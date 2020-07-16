---
title: WinRT in Unreal
description: Panoramica del plug-in di audio spaziale per Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, streaming, comunicazione remota, realtà mista, sviluppo, guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, caratteristiche, ologrammi, sviluppo di giochi
ms.openlocfilehash: 7a64002a5fa48bb589ab113f0a8dc1bfcb92d535
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408219"
---
# <a name="winrt-in-unreal"></a>WinRT in Unreal

## <a name="overview"></a>Panoramica

Nel corso dello sviluppo di HoloLens potrebbe essere necessario scrivere una funzionalità usando WinRT. Se ad esempio si apre una finestra di dialogo di file in un'applicazione HoloLens, è necessario FileSavePicker nel file di intestazione WinRT/Windows. storage. Pickers. h.  Poiché Unreal non compila in modo nativo il codice WinRT, è il processo di compilare un file binario separato che può essere utilizzato dal sistema di compilazione di Unreal. In questa esercitazione verrà illustrata una situazione di questo tipo.

## <a name="objectives"></a>Obiettivi
- Crea una DLL di Windows universale che apre un FileSaveDialogue
- Collegare la DLL a un progetto di gioco Unreal
- Salvare un file in HoloLens da un progetto Unreal usando la nuova DLL

## <a name="getting-started"></a>Introduzione
1. Verificare che siano installati tutti [gli strumenti necessari](unreal-uxt-ch1.md)
2. [Creare un nuovo progetto irreale](unreal-uxt-ch2.md#creating-a-new-unreal-project) e denominarlo **Consumewinrt**
3. Abilitare i [plug](unreal-uxt-ch2.md#enabling-required-plugins) -in richiesti per lo sviluppo di HoloLens
4. [Installazione per la distribuzione](unreal-uxt-ch6.md) in un dispositivo o in un emulatore

## <a name="creating-a-winrt-dll"></a>Creazione di una DLL WinRT 
1. Aprire un nuovo progetto di Visual Studio e creare un progetto **dll (Windows universale)** nella stessa directory del file **uproject** del gioco Unreal. 

![Creazione di una DLL](images/unreal-winrt-img-01.png)

2. Denominare il progetto **HoloLensWinrtDLL** e impostare il percorso come sottodirectory **thirdparty** sul file uproject del gioco Unreal. 
    * Selezionare **posiziona soluzione e progetto nella stessa directory** per semplificare la ricerca dei percorsi in un secondo momento. 

![Configurazione della DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Al termine della compilazione del nuovo progetto, è opportuno prestare particolare attenzione ai file di intestazione e cpp vuoti, denominati rispettivamente **HoloLensWinrtDLL. cpp** e **HoloLensWinrtDLL. h** . L'intestazione è il file di inclusione che usa la DLL in Unreal, mentre la CPP conserva il corpo di tutte le funzioni esportate e include il codice WinRT che Unreal non sarebbe altrimenti in grado di compilare. 

3. Prima di aggiungere il codice, è necessario aggiornare le proprietà del progetto per assicurarsi che il codice WinRT necessario possa essere compilato: 
    * Fare clic con il pulsante destro del mouse sul progetto HoloLensWinrtDLL e scegliere **Proprietà** .  
    * Modificare l'elenco a discesa **configurazione** in **tutte le configurazioni** e l'elenco a discesa **piattaforma** su **tutte le piattaforme**  
    * In **proprietà di configurazione> C/C++> tutte le opzioni**:
        * Aggiungere **await** a **Opzioni aggiuntive** per assicurarsi che sia possibile attendere le attività asincrone  
        * Modificare lo standard del **linguaggio c++** allo **standard ISO c++ 17 (/STD: c++ 17)** per includere qualsiasi codice WinRT

![Configurazione della DLL](images/unreal-winrt-img-03.png)

Il progetto è pronto per aggiornare l'origine della DLL con il codice WinRT che apre una finestra di dialogo di file e salva un file nel disco HoloLens.  

## <a name="adding-the-dll-code"></a>Aggiunta del codice DLL
1. Aprire **HoloLensWinrtDLL. h** e aggiungere una funzione di DLL esportata per l'utilizzo di Unreal: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Aprire **HoloLensWinrtDLL. cpp** e aggiungere tutte le intestazioni che la classe utilizzerà:  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> Tutto il codice WinRT viene archiviato in **HoloLensWinrtDLL. cpp,** quindi Unreal non tenta di includere codice WinRT quando fa riferimento all'intestazione. 

3. Sempre in **HoloLensWinrtDLL. cpp**aggiungere un corpo della funzione per OpenFileDialogue () e tutto il codice supportato: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Aggiungere una classe SaveGameManager a **HoloLensWinrtDLL. cpp** per gestire la finestra di dialogo del file e salvare il file: 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullprt);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. Compilare la soluzione per la **versione > arm64** per compilare la dll nella directory figlio arm64/Release/HoloLensWinrtDLL dalla soluzione dll. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Aggiunta del file binario WinRT a Unreal 
Per il collegamento e l'uso di una DLL in Unreal è necessario un progetto C++. Se si usa un progetto Blueprint, è possibile convertirlo facilmente in un progetto C++ aggiungendo una classe C++:  

1. Nell'editor Unreal aprire **File > nuova classe C++...** e creare un nuovo **attore** denominato **WinrtActor** per eseguire il codice nella dll: 

![Configurazione della DLL](images/unreal-winrt-img-04.png)

> [!NOTE]
> È stata ora creata una soluzione nella stessa directory del file uproject insieme a un nuovo script di compilazione denominato source/ConsumeWinRT/ConsumerWinRT. Build. cs.

2. Aprire la soluzione, cercare la cartella **Games/ConsumeWinRT/source/ConsumeWinRT** e aprire **ConsumeWinRT.Build.cs**:

![Configurazione della DLL](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Collegamento della DLL
1. In **ConsumeWinRT.Build.cs**aggiungere una proprietà per trovare il percorso di inclusione per la dll (la directory contenente HoloLensWinrtDLL. h). La DLL si trova in una directory figlio del percorso di inclusione, quindi questa proprietà verrà usata come dir radice binaria:

```cs
public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirddParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. Nel costruttore della classe aggiungere il codice seguente per aggiornare il percorso di inclusione, collegare il nuovo lib e ritardare il caricamento e copiare la DLL nel percorso appx in pacchetto:

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. Aprire **WinrtActor. h** e aggiungere due definizioni di funzione, una che può essere usata da un progetto e un'altra che usa il codice dll: 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. Aprire **WinrtActor. cpp** e caricare la dll in BeginPlay: 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> Prima di chiamare le funzioni, è necessario caricare la DLL.

### <a name="building-the-game"></a>Compilazione del gioco
1. Compilare la soluzione di gioco per avviare l'editor non reale aperto al progetto di gioco: 
    * Nella scheda **posiziona gli attori** cercare il nuovo **WinrtActor** e trascinarlo nella scena 
    * Aprire il progetto level per eseguire la funzione Blueprint Callable nella **WinrtActor** 

![Configurazione della DLL](images/unreal-winrt-img-06.png)

2. Nel **mondo**, trovare i **WindrtActor** precedentemente rilasciati nella scena e trascinarli nel progetto di livello: 

![Configurazione della DLL](images/unreal-winrt-img-07.png)

3. Nel progetto Level trascinare il nodo output da WinrtActor, cercare **Apri file Dialog**, quindi indirizzare il nodo da qualsiasi input utente.  In questo caso, la finestra di dialogo Apri file viene chiamata da un evento vocale: 

![Configurazione della DLL](images/unreal-winrt-img-08.png)

4. Creare [il pacchetto del gioco per HoloLens](unreal-uxt-ch6.md), distribuirlo ed eseguirlo.  

Quando Unreal chiama OpenFileDialogue, viene aperta una finestra di dialogo di file nella richiesta di HoloLens di un nome di file con estensione txt.  Dopo aver salvato il file, passare alla scheda **Esplora file** nel portale del dispositivo per visualizzare il contenuto "Hello WinRT". 

## <a name="summary"></a>Riepilogo 

Si consiglia di usare il codice in questa esercitazione come punto di partenza per l'utilizzo del codice WinRT in Unreal.  Consente agli utenti di salvare i file nel disco HoloLens usando la stessa finestra di dialogo del file di Windows.  Seguire lo stesso processo per esportare eventuali funzioni aggiuntive dall'intestazione HoloLensWinrtDLL e usate in Unreal.  Si noti il codice DLL che attende il codice WinRT asincrono in un thread in background MTA, che evita il deadlock del thread del gioco non reale. 

## <a name="see-also"></a>Vedere anche
* [API C++/WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [Classe FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Librerie di terze parti non reali](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
