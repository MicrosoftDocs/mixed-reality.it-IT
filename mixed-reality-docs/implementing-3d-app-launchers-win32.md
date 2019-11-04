---
title: Implementare i lanci di app 3D (app Win32)
description: Come creare lanci di app 3D e logo per app e giochi Win32 VR (distribuiti al di fuori di Steam) in modo che vengano visualizzati nel menu Start della realtà mista di Windows e nell'ambiente Home.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icona, modellazione, avvio, avvio 3D, riquadro, cubo attivo, Win32
ms.openlocfilehash: 87eadfb5184f9fb5f8d513ab00a2a954e71df376
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438581"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementare i lanci di app 3D (app Win32)

> [!NOTE]
> Questa funzionalità è disponibile solo per i PC che eseguono i più recenti voli di [Windows Insider](https://insider.windows.com) (RS5), Build 17704 e versioni successive.

La [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) è il punto di partenza in cui gli utenti atterrano prima di avviare le applicazioni. Per impostazione predefinita, i giochi e le app VR Win32 immersive devono essere avviati dall'esterno dell'auricolare e non vengono visualizzati nell'elenco "tutte le app" nel menu Start della realtà mista di Windows. Tuttavia, seguendo le istruzioni riportate in questo articolo per implementare un'utilità di avvio delle app 3D, è possibile avviare l'esperienza immersiva Win32 VR dal menu Start della realtà mista di Windows e dall'ambiente domestico.

Questa operazione è valida solo per le esperienze di Win32 VR immersive distributied al di fuori del vapore. Per le esperienze VR [distribuite tramite Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), abbiamo [aggiornato la realtà mista di Windows per SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) insieme ai più recenti voli RS5 di Windows Insider, in modo che i titoli SteamVR siano visualizzati nel menu Start della realtà mista di Windows nell'elenco "tutte le app" utilizzando automaticamente un'utilità di avvio predefinita. In altre parole, il metodo descritto in questo articolo non è necessario per i titoli SteamVR e verrà sostituito dalla realtà mista di Windows per la funzionalità beta di SteamVR.

## <a name="3d-app-launcher-creation-process"></a>processo di creazione dell'utilità di avvio delle app 3D

Per la creazione di un avvio di app 3D sono necessari tre passaggi:
1. [Progettazione e concezione](3d-app-launcher-design-guidance.md)
2. [Modellazione ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrazione nell'applicazione (questo articolo)

gli asset 3D da usare come avvii per l'applicazione devono essere creati usando le [linee guida per la creazione di realtà miste di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per garantire la compatibilità. Gli asset che non soddisfano questa specifica di authoring non verranno sottoposti a rendering nella Home della realtà mista di Windows.

## <a name="configuring-the-3d-launcher"></a>Configurazione dell'utilità di avvio 3D

Le applicazioni Win32 verranno visualizzate nell'elenco "tutte le app" nel menu di avvio della realtà mista di Windows se si crea un Launcher di app 3D. A tale scopo, creare un file XML del [manifesto degli elementi visivi](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) che fa riferimento all'utilità di avvio delle app 3D attenendosi alla procedura seguente:

1. Creare un **file GLB asset di avvio app 3D** (vedere [modellazione ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Creare un **[manifesto degli elementi visivi](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** per l'applicazione.
    1. È possibile iniziare con l' [esempio riportato di seguito](#sample-visual-elements-manifest).  Per altri dettagli, vedere la documentazione completa del [manifesto degli elementi visivi](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) .
    2. Aggiornare **Square150x150Logo** e **SQUARE70X70LOGO** con un png/jpg/gif per l'app.
        * Questi verranno usati per il logo 2D dell'app nell'elenco di tutte le app della realtà mista di Windows e per il menu Start sul desktop.
        * Il percorso del file è relativo alla cartella che contiene il manifesto degli elementi visivi.
        * È comunque necessario fornire un'icona del menu Start Desktop per l'app attraverso i meccanismi standard. Questo può essere direttamente nell'eseguibile o nel collegamento creato, ad esempio tramite IShellLink:: SetIconLocation.
        * *Facoltativo:* È possibile usare un file resources. pri se si vuole che MRT fornisca più dimensioni di asset per diverse scale di risoluzione e temi a contrasto elevato.
    3. Aggiornare il **percorso di MixedRealityModel** in modo che punti al GLB per l'utilità di avvio dell'app 3D
    4. Salvare il file con lo stesso nome del file eseguibile, con estensione ". VisualElementsManifest. xml "e salvarlo nella stessa directory. Per il file eseguibile "contoso. exe", ad esempio, il file XML associato è denominato "contoso. visualelementsmanifest. xml".
3. **Aggiungere un collegamento** all'applicazione nel menu Start di Windows desktop. Per un'implementazione di esempio C++ , vedere l' [esempio seguente](#sample-app-launcher-shortcut-creation) . 
    * Crearlo in%ALLUSERSPROFILE%\Microsoft\Windows\Start Avvio\programmi (Machine) o%APPDATA%\Microsoft\Windows\Start Avvio\programmi (User)
    * Se un aggiornamento modifica il manifesto degli elementi visivi o gli asset a cui fa riferimento, il programma di aggiornamento o il programma di installazione dovrebbe aggiornare il collegamento in modo che il manifesto venga analizzato e aggiornato gli asset memorizzati nella cache.
4. *Facoltativo:* Se il collegamento sul desktop non punta direttamente al file EXE dell'applicazione (ad esempio, se richiama un gestore di protocollo personalizzato come "myapp://"), il menu Start non troverà automaticamente il file VisualElementsManifest. XML dell'app. Per risolvere il problema, è necessario che il collegamento specifichi il percorso del file del manifesto degli elementi visivi utilizzando System. AppUserModel. VisualElementsManifestHintPath (). Questa impostazione può essere configurata nel collegamento utilizzando le stesse tecniche di System.AppUserModel.ID. Non è necessario utilizzare System.AppUserModel.ID, ma è possibile eseguire questa operazione se si desidera che il collegamento corrisponda all'ID del modello utente dell'applicazione esplicita se ne viene utilizzato uno.  Per un C++ esempio, vedere la sezione relativa alla [creazione del collegamento di avvio dell'app di esempio](#sample-app-launcher-shortcut-creation) .

### <a name="sample-visual-elements-manifest"></a>Manifesto degli elementi visivi di esempio

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>Creazione di un collegamento dell'utilità di avvio app di esempio

Il codice di esempio seguente illustra come creare un collegamento in C++, inclusa l'override del percorso del file XML del manifesto degli elementi visivi. Si noti che l'override è necessario solo nei casi in cui il collegamento non punti direttamente al file EXE associato al manifesto (ad esempio, il collegamento usa un gestore di protocollo personalizzato come "myapp://".

#### <a name="sample-lnk-shortcut-creation-c"></a>Esempio. Creazione di collegamenti LNKC++()

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>Esempio. Collegamento all'utilità di avvio URL 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>Vedi anche

* [Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un utilità di avvio delle app 3D.
* [Linee guida per la progettazione di utilità di avvio di app 3D](3d-app-launcher-design-guidance.md)
* [Creazione di modelli 3D per l'utilizzo nella Home realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementazione di lanci di app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
