---
title: OpenXR
description: Provare l'API OpenXR 0,90 provvisoria con la realtà mista OpenXR Developer Preview.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Realtà mista OpenXR Developer Preview
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039176"
---
# <a name="openxr"></a>OpenXR

OpenXR è uno standard aperto senza diritti d'autore di [Khronos](https://www.khronos.org/) che fornisce l'accesso nativo a un'ampia gamma di dispositivi di molti fornitori che si estendono nello spettro della [realtà mista](mixed-reality.md).

Con OpenXR, è possibile creare applicazioni destinate a entrambi i dispositivi olografici (ad esempio HoloLens 2) che collocano contenuti digitali nel mondo reale come se fossero effettivamente presenti, nonché dispositivi immersivi, come le cuffie di realtà mista di Windows per PC desktop, che nascondono il mondo fisico e sostituirlo con un'esperienza digitale.  OpenXR consente di scrivere codice una volta trasportabile in un'ampia gamma di piattaforme hardware.

Lo standard OpenXR si trova attualmente in una fase provvisoria, con una specifica iniziale OpenXR 0,90 rilasciata per il feedback.  Per altre informazioni su OpenXR, incluso l'accesso alla specifica e alle [intestazioni](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)di [0,90 provvisorio](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) , vedere la [pagina Khronos OpenXR](https://www.khronos.org/openxr/). 

È possibile provare l'API OpenXR 0,90 provvisoria in un HoloLens 2 o un PC desktop usando la realtà mista OpenXR Developer Preview.  Questo runtime iniziale consente alle applicazioni destinate all'API OpenXR 0,90 di usare gli auricolari HoloLens 2 o Windows a realtà mista sul desktop.

Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>Configurazione della realtà mista OpenXR Developer Preview per HoloLens 2

Per iniziare a usare la realtà mista OpenXR Developer Preview in HoloLens 2:

1. Configurare un HoloLens 2 o seguire le istruzioni per [installare l'emulatore HoloLens 2](using-the-hololens-emulator.md).
1. Avviare l'App Store dall'interno del dispositivo o dell'emulatore e assicurarsi che tutte le app vengano aggiornate.  Verrà installata la realtà mista OpenXR Developer Preview per l'uso con le app in tale dispositivo.  Se si usa l'emulatore, è consigliabile consultare le [istruzioni di input](using-the-hololens-emulator.md#basic-emulator-input) dell'emulatore per usare l'app dello Store all'interno dell'emulatore.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>Configurazione della realtà mista OpenXR Developer Preview per cuffie Desktop immersive

Per iniziare a usare la realtà mista OpenXR Developer Preview in un computer desktop:

1. Assicurarsi di eseguire l'aggiornamento di Windows 10 ottobre 2018 (1809) o l'aggiornamento di Windows 10 di maggio 2019 (1903).  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento all'aggiornamento di maggio 2019 usando [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).
1. Configurare un auricolare di realtà mista di Windows o seguire le istruzioni per [abilitare il simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md).
1. Installare l' [app OpenXR Developer Preview di realtà mista](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Questa app viene configurata con l'anteprima di OpenXR Runtime in Windows 10 ottobre 2018 aggiornamento (1809) o versione successiva.  Dopo l'installazione di questa app, Windows Store manterrà aggiornato il Runtime.
1. Eseguire l'app OpenXR Developer Preview per la realtà mista dal menu Start e seguire le istruzioni per rendere attivo il Runtime.  A breve, questa app consente di esplorare anche altre informazioni di debug di OpenXR.

![App OpenXR Developer Preview in realtà mista](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Supporto per l'aggiornamento di Windows 10 ottobre 2018

Se si esegue l'aggiornamento di Windows 10 May 2019 (1903) e si sono seguiti i passaggi precedenti, è necessario essere pronti per usare la realtà mista OpenXR Developer Preview.

Se non si è pronti ad [aggiornare il PC desktop all'aggiornamento di maggio 2019](https://www.microsoft.com/en-us/software-download/windows10), è possibile procedere con l'aggiornamento di Windows 10 ottobre 2018 (1809) seguendo un altro passaggio:

1. Seguire questa procedura per installare la realtà mista OpenXR Developer Preview.
1. Per impostare la realtà mista OpenXR Developer Preview come il runtime OpenXR attivo del sistema, installare il [pacchetto di compatibilità OpenXR Developer Preview](https://aka.ms/openxr-compat)per la realtà mista.

## <a name="building-a-sample-openxr-app"></a>Compilazione di un'app OpenXR di esempio

Il progetto [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) illustra un semplice esempio di OpenXR con due file di progetto di Visual Studio, uno per un'app desktop Win32 e uno per un'app UWP HoloLens 2.  Poiché la soluzione contiene un progetto HoloLens UWP, è necessario che il [carico di lavoro di sviluppo piattaforma UWP (Universal Windows Platform)](install-the-tools.md#installation-checklist) installato in Visual Studio per aprirlo completamente.

Si noti che, mentre i file di progetto Win32 e UWP sono separati a causa delle differenze nella creazione di pacchetti e distribuzione, il codice dell'app all'interno di ogni progetto è uguale al 100%.

## <a name="feedback"></a>Commenti e suggerimenti

Per inviare commenti e suggerimenti sulla [specifica OpenXR 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), visitare i [Forum di Khronos OpenXR](https://community.khronos.org/c/openxr), [Slack #openxr Channel](https://khr.io/slack) e lo strumento di [rilevamento dei problemi delle specifiche](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Risoluzione dei problemi

Ecco alcuni suggerimenti per la risoluzione dei problemi per la realtà mista OpenXR Developer Preview.  Se si verificano altri problemi, visitare il canale [Khronos OpenXR Forums](https://community.khronos.org/c/openxr) o [Slack #openxr Channel](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>App OpenXR che non avvia la realtà mista di Windows

Se l'app OpenXR non avvia la realtà mista di Windows quando viene eseguita, la realtà mista OpenXR Developer Preview potrebbe non essere impostata come runtime attivo.  Assicurarsi di eseguire l'app OpenXR Developer Preview per la realtà mista e seguire le istruzioni per rendere attiva la fase di esecuzione.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Non è possibile installare l'app OpenXR Developer Preview in realtà mista 

Assicurarsi di eseguire almeno l'aggiornamento di Windows 10 ottobre 2018 (1809).  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento all'aggiornamento 2019 di maggio (1903) con [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).

Se il pulsante Installa nell'app OpenXR Developer Preview per la realtà mista non esegue alcuna operazione nell'aggiornamento di Windows 10 ottobre 2018, il sistema potrebbe avere memorizzato nella cache i requisiti di sistema non aggiornati per l'app.  È possibile eseguire il comando `wsreset.exe` da un prompt dei comandi per cancellare la cache.

## <a name="see-also"></a>Vedere anche

* [Altre informazioni su OpenXR](https://www.khronos.org/openxr/)
* [Specifica OpenXR 0,90 provvisoria](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Informazioni di riferimento sull'API Provisional 0,90 di OpenXR](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR le intestazioni 0,90 provvisorie](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [Guida di riferimento rapido a OpenXR Provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
