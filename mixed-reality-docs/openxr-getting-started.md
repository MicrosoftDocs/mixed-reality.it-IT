---
title: Introduzione a OpenXR
description: Inizia a usare l'API OpenXR portatile standard in realtà mista di Windows e gli auricolari HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality OpenXR Developer Portal, DirectX, native, Native App, Custom Engine, middleware, Getting Started, 101, Preview Extensions
ms.openlocfilehash: db45308834f920413420f080a35b378f6a55fa49
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362025"
---
# <a name="getting-started-with-openxr"></a>Introduzione a OpenXR

È possibile sviluppare usando OpenXR in un headset HoloLens 2 o Windows Mixed Reality immersive sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introduzione a OpenXR per HoloLens 2

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2:

1. Configurare un HoloLens 2 o seguire le istruzioni per [installare una versione recente dell'emulatore di HoloLens 2](using-the-hololens-emulator.md).  Se il dispositivo ha aggiornato di recente il sistema operativo o se si sta usando un'immagine dell'emulatore recente, è necessario che OpenXR 1,0 sia già pronto per iniziare.
1. Per assicurarsi di avere la versione più recente del runtime di OpenXR con tutte le [estensioni](openxr.md#roadmap) presenti, avviare l'app dello Store dall'interno del dispositivo o dell'emulatore, aprire il menu in alto a destra, fare clic su **download e aggiornamenti** e fare clic su **Ottieni aggiornamenti**.  In questo modo si garantisce che il runtime di OpenXR in HoloLens sia aggiornato.  Si noti che se si usa l'emulatore, l'immagine dell'emulatore verrà reimpostata ogni volta che viene avviata, quindi la scommessa migliore consiste nel verificare di disporre [della versione più recente dell'immagine dell'emulatore HoloLens 2](using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introduzione a OpenXR per le cuffie con la realtà mista di Windows

Per iniziare a sviluppare applicazioni OpenXR per cuffie di realtà miste di Windows Immersive:

1. Assicurarsi di eseguire almeno l'aggiornamento 2019 di Windows 10 (1903), che è il requisito minimo per gli utenti finali di Windows Mixed Reality per l'esecuzione di applicazioni OpenXR.  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento con <a href="https://www.microsoft.com/software-download/windows10" target="_blank">Windows 10 Update Assistant</a>.
2. Configurare un auricolare di realtà mista di Windows o seguire le istruzioni per [abilitare il simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md).  Quando si configura la realtà mista di Windows, il portale di realtà mista installerà automaticamente il runtime di OpenXR di realtà mista di Windows.  Il Microsoft Store manterrà aggiornato il Runtime.
3. Rendere attiva la realtà mista di Windows OpenXR runtime avviando il portale di realtà mista dal menu Start, facendo clic sul pulsante... menu in basso a sinistra e selezionando "Configura OpenXR".<br>
![la configurazione di OpenXR nel portale per la realtà mista](images/mixed-reality-portal-set-up-openxr.png)

Se è necessario riattivare la realtà mista di Windows OpenXR Runtime, ripetere il passaggio 3.

> [!NOTE]
> Il runtime di OpenXR per la realtà mista di Windows verrà presto reso attivo automaticamente per tutti gli utenti finali della realtà mista di Windows.

## <a name="getting-the-windows-mixed-reality-openxr-developer-portal"></a>Recupero del portale per sviluppatori di OpenXR per la realtà mista di Windows

Per provare il runtime di OpenXR per la realtà mista di Windows, è possibile installare l' <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">app del portale per sviluppatori OpenXR per la realtà mista</a>.  Questa app fornisce una scena demo che esercita varie funzionalità di OpenXR, insieme a una pagina di stato del sistema che fornisce informazioni chiave sul runtime attivo e sull'auricolare corrente.

Se si usa l'emulatore, il modo più semplice per installare il portale per sviluppatori OpenXR per la realtà mista è usare il [portale per dispositivi Windows](using-the-windows-device-portal.md), passando alla pagina "OpenXR" e quindi facendo clic sul pulsante "Installa" in "funzionalità per sviluppatori". (funziona anche su un dispositivo HoloLens 2 fisico)

![App del portale per sviluppatori della realtà mista OpenXR](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>Compilazione di un'app OpenXR di esempio

Assicurarsi di [installare gli strumenti](install-the-tools.md) necessari per lo sviluppo di OpenXR, se non è già stato fatto.

Il progetto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> illustra un semplice esempio di OpenXR con due file di progetto di Visual Studio, uno per un'app desktop Win32 e uno per un'app UWP HoloLens 2.  Poiché la soluzione contiene un progetto HoloLens UWP, è necessario che il [carico di lavoro di sviluppo piattaforma UWP (Universal Windows Platform)](install-the-tools.md#installation-checklist) installato in Visual Studio per aprirlo completamente.

Si noti che, mentre i file di progetto Win32 e UWP sono separati a causa delle differenze nella creazione di pacchetti e distribuzione, il codice dell'app all'interno di ogni progetto è uguale al 100%.

Dopo la compilazione di un desktop Win32 OpenXR. EXE, è possibile usarlo con una cuffia VR su qualsiasi piattaforma desktop VR che supporta OpenXR, sia che si tratti di un auricolare a realtà mista di Windows o di qualsiasi altro auricolare.

Dopo aver compilato un pacchetto dell'app OpenXR UWP, è possibile [distribuire il pacchetto](using-visual-studio.md) in un dispositivo HoloLens 2 o nell'emulatore HoloLens 2.

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrare il caricatore OpenXR in un progetto

Per iniziare a usare OpenXR in un progetto esistente, è necessario includere il caricatore OpenXR.  Il caricatore rileva il runtime OpenXR attivo sul dispositivo e fornisce l'accesso alle funzioni di base e alle funzioni di estensione che implementa.

È possibile [fare riferimento al pacchetto NuGet OpenXR ufficiale](#reference-official-openxr-nuget-package) dal progetto di Visual Studio o [includere l'origine del caricatore OpenXR ufficiale](#include-official-openxr-loader-source) dal repository GitHub Khronos.  Entrambi gli approcci consentono di accedere alle funzionalità di base di OpenXR 1,0, oltre a `KHR`pubblicate, `EXT` e `MSFT` estensioni.

Se si è interessati a provare a usare `MSFT_preview` Extensions, è possibile [copiare le intestazioni OpenXR in anteprima](#using-preview-extensions) dal repository GitHub della realtà mista.

### <a name="reference-official-openxr-nuget-package"></a>Pacchetto NuGet OpenXR ufficiale di riferimento

Il <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">pacchetto NuGet **OpenXR. loader** </a> è il modo più semplice per fare riferimento a un caricatore OpenXR predefinito. DLL nella soluzione di Visual C++ Studio.  In questo modo sarà possibile accedere alle funzionalità di base di OpenXR 1,0, oltre alle estensioni `KHR`, `EXT` ed `MSFT` pubblicate.

Per aggiungere un riferimento al pacchetto NuGet OpenXR. loader alla soluzione di C++ Visual Studio:
1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto che userà OpenXR e selezionare **Gestisci pacchetti NuGet...** .
1. Passare alla scheda **Sfoglia** e cercare **OpenXR. loader**.
1. Selezionare il pacchetto **OpenXR. loader** e fare clic su installa nel riquadro dei dettagli a destra.
1. Fare clic su OK per accettare le modifiche apportate al progetto.
1. Aggiungere `#include <openxr/openxr.h>` a un file di origine per iniziare a usare l'API OpenXR.

Per un esempio dell'API OpenXR in azione, vedere l'app di esempio <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Includi origine del caricatore OpenXR ufficiale

Se si vuole creare il caricatore manualmente, ad esempio per evitare il caricatore aggiuntivo. DLL, è possibile effettuare il pull delle origini ufficiali del caricatore OpenXR di Khronos nel progetto.  In questo modo sarà possibile accedere alle funzionalità di base di OpenXR 1,0, oltre alle estensioni `KHR`, `EXT` ed `MSFT` pubblicate.

Per iniziare, seguire le istruzioni riportate nel <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">repository Khronos OpenXR-SDK su GitHub</a>.  Il progetto è configurato per la compilazione con CMake. Se si usa MSBuild, sarà necessario copiare il codice nel progetto.

## <a name="using-preview-extensions"></a>Uso delle estensioni di anteprima

Le estensioni `MSFT_preview` elencate nella [Roadmap di estensione](openxr.md#roadmap) sono le estensioni del fornitore sperimentali visualizzate come anteprima per raccogliere commenti e suggerimenti.  Queste estensioni sono destinate solo ai dispositivi per sviluppatori e verranno rimosse quando l'estensione reale viene fornita.

Se si è interessati a provare le estensioni `MSFT_preview` disponibili, seguire questa procedura per aggiornare il progetto:
1. Seguire uno degli approcci precedenti per integrare un caricatore OpenXR nel progetto.
1. Sostituire le intestazioni OpenXR standard nel progetto con le <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">intestazioni di anteprima del repository OpenXR realtà mista su GitHub</a>.

Per attivare quindi le estensioni di anteprima sulla destinazione HoloLens 2 o sul PC desktop:
  1. Abilitare il portale per dispositivi Windows sul dispositivo di destinazione:
     * Se il dispositivo di destinazione è un dispositivo HoloLens 2, [seguire queste istruzioni](using-the-windows-device-portal.md) sul dispositivo di destinazione.  Si noti che questa operazione richiede una cuffia fisica, perché un problema noto nell'emulatore HoloLens 2 impedisce che l'interfaccia utente nel passaggio successivo venga visualizzata nell'emulatore.
     * Se il dispositivo di destinazione è un PC desktop con una periferica di auricolare immersiva collegata, <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop#set-up-device-portal-on-windows-desktop" target="_blank">seguire queste istruzioni</a> sul PC desktop di destinazione.
  1. Passare alla scheda **OpenXR** nel riquadro sinistro e abilitare l' **uso dell'ultima versione di anteprima OpenXR Runtime**.  In questo modo viene abilitato il runtime di anteprima nel dispositivo, in cui sono attivate le estensioni di anteprima.

Vedere il <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">repository di OpenXR per la realtà mista</a> per la documentazione di queste estensioni di anteprima ed esempi su come usarle.

## <a name="troubleshooting"></a>Risoluzione dei problemi

In caso di problemi con lo sviluppo OpenXR, vedere i suggerimenti per la [risoluzione dei problemi](openxr-troubleshooting.md).