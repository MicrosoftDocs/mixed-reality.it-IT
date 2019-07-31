---
title: OpenXR
description: È possibile creare un motore usando lo standard dell'API OpenXR portatile e distribuirlo in una realtà mista di Windows e in HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, realtà mista OpenXR portale per sviluppatori, DirectX, nativo, motore personalizzato app native, middleware
ms.openlocfilehash: efad0809356f969c825ef7285885fdb9431c7fce
ms.sourcegitcommit: c0d5c19b756b8e6ff95ea26a4d8d2b3a53878c2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671952"
---
# <a name="openxr"></a>OpenXR

OpenXR è uno standard API senza diritti d'autore aperto da [Khronos](https://www.khronos.org/) che fornisce ai motori l'accesso nativo a un'ampia gamma di dispositivi di molti fornitori che si estendono nello spettro della [realtà mista](mixed-reality.md).

È possibile sviluppare usando OpenXR in un headset HoloLens 2 o Windows Mixed Reality immersive sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

## <a name="why-openxr"></a>Perché OpenXR?

Con OpenXR, è possibile creare motori destinati a entrambi i dispositivi olografici (ad esempio HoloLens 2) che collocano contenuti digitali nel mondo reale come se fossero effettivamente presenti, nonché dispositivi immersivi, come le cuffie di realtà mista di Windows per PC desktop, che nascondono il fisico e sostituirla con un'esperienza digitale.  OpenXR consente di scrivere codice una volta trasportabile in un'ampia gamma di piattaforme hardware.

L'API OpenXR usa un caricatore che connette l'applicazione direttamente al supporto della piattaforma nativa dell'auricolare.  Questo consente agli utenti finali di ottenere le massime prestazioni e la latenza minima, sia che usino un auricolare di realtà mista di Windows o qualsiasi altro auricolare.

## <a name="what-is-openxr"></a>Che cos'è OpenXR?

L'API OpenXR 1,0 principale fornisce le funzionalità di base necessarie per creare un motore che può essere destinato a dispositivi olografici come HoloLens 2 e dispositivi immersivi come gli auricolari per la realtà mista di Windows:
* Sistemi e sessioni
* Spazi di riferimento (visualizzazione, locale, fase)
* Visualizza configurazioni (mono, stereo)
* Le catene + intervallo frame
* Livelli di composizione
* Input e haptics
* API grafica + integrazione della piattaforma

Per informazioni sull'API OpenXR, vedere la [specifica OpenXR 1,0](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html) e le informazioni di [riferimento sulle API OpenXR 1,0](https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html).  Per ulteriori informazioni, vedere la [pagina Khronos OpenXR](https://www.khronos.org/openxr/).

Per avere come destinazione il set completo di funzionalità di HoloLens 2, si useranno anche estensioni OpenXR specifiche del fornitore e dei fornitori che consentono funzionalità aggiuntive oltre al core OpenXR 1,0, ad esempio il rilevamento a mano articolato, il monitoraggio degli occhi, il mapping spaziale e i ancoraggi spaziali.  Vedere la sezione della Guida di [orientamento](openxr.md#roadmap) riportata di seguito per altre informazioni sulle estensioni riportate più avanti in questo anno.

Si noti che OpenXR non è a sua volta un motore di realtà mista.  OpenXR consente invece ai motori come Unity e Unreal di scrivere codice portatile una volta che può accedere alle funzionalità della piattaforma nativa del dispositivo olografico o immersivo dell'utente, indipendentemente dal fornitore che ha creato tale piattaforma.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introduzione a OpenXR per HoloLens 2

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2:

1. Configurare un HoloLens 2 o seguire le istruzioni per [installare l'emulatore HoloLens 2](using-the-hololens-emulator.md).
1. Avviare l'App Store dall'interno del dispositivo o dell'emulatore e assicurarsi che tutte le app vengano aggiornate.  In questo modo si garantisce che il runtime di OpenXR in HoloLens venga aggiornato a OpenXR 1,0.  Se si usa l'emulatore, è consigliabile consultare le [istruzioni di input](using-the-hololens-emulator.md#basic-emulator-input) dell'emulatore per usare l'app dello Store all'interno dell'emulatore.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introduzione a OpenXR per le cuffie con la realtà mista di Windows

Per iniziare a sviluppare applicazioni OpenXR per cuffie di realtà miste di Windows Immersive:

1. Assicurarsi di eseguire l'aggiornamento di Windows 10 2019 (1903), che è il requisito minimo per gli utenti finali di Windows Mixed Reality per l'esecuzione di applicazioni OpenXR.  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento all'aggiornamento di maggio 2019 usando [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).  Se non si è in grado di aggiornare il PC, è anche possibile [sviluppare l'app OpenXR usando l'aggiornamento di Windows 10 ottobre 2018 (1809)](openxr.md#developing-on-windows-10-october-2018-update), sebbene sia possibile riscontrare prestazioni ridotte o altri problemi.
1. Configurare un auricolare di realtà mista di Windows o seguire le istruzioni per [abilitare il simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md).
1. Installare l' [app del portale per sviluppatori OpenXR](https://www.microsoft.com/store/productId/9n5cvvl23qbt)per la realtà mista.  L'installazione di questa app installerà automaticamente la realtà mista OpenXR Runtime.  Al termine dell'installazione del runtime di OpenXR, il Microsoft Store manterrà aggiornato il Runtime.
1. Eseguire l'app del portale per sviluppatori OpenXR di realtà mista dal menu Start e seguire le istruzioni per rendere attivo il Runtime.

![App del portale per sviluppatori della realtà mista OpenXR](images/mixed-reality-openxr-developer-portal.png)

> [!NOTE]
> La realtà mista OpenXR runtime sarà presto disponibile per tutti gli utenti finali di Windows Mixed Reality tramite l'app del portale per la realtà mista.

## <a name="building-a-sample-openxr-app"></a>Compilazione di un'app OpenXR di esempio

Il progetto [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) illustra un semplice esempio di OpenXR con due file di progetto di Visual Studio, uno per un'app desktop Win32 e uno per un'app UWP HoloLens 2.  Poiché la soluzione contiene un progetto HoloLens UWP, è necessario che il [carico di lavoro di sviluppo piattaforma UWP (Universal Windows Platform)](install-the-tools.md#installation-checklist) installato in Visual Studio per aprirlo completamente.

Si noti che, mentre i file di progetto Win32 e UWP sono separati a causa delle differenze nella creazione di pacchetti e distribuzione, il codice dell'app all'interno di ogni progetto è uguale al 100%.

## <a name="roadmap"></a>Guida di orientamento

La specifica OpenXR definisce un meccanismo di estensione che consente agli implementatori del runtime di esporre funzionalità aggiuntive oltre le [funzionalità](openxr.md#what-is-openxr) di [base definite nella specifica OpenXR 1,0 di base](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html).

Sono disponibili tre tipi di estensioni OpenXR:
* **Estensioni Fornitore (ad esempio, MSFT):** Consente l'innovazione per fornitore in funzionalità hardware o software.  Qualsiasi fornitore di runtime può introdurre e distribuire un'estensione del fornitore in qualsiasi momento.
* **Estensioni EXT:** Estensioni tra fornitori che vengono definite e implementate da più aziende.  I gruppi di società interessate possono introdurre estensioni EXT in qualsiasi momento.
* **Estensioni KHR:** Estensioni Khronos ufficiali ratificate come parte di una versione di base delle specifiche.  Le estensioni KHR sono coperte dalla stessa licenza della specifica principale.

Entro la fine dell'anno, la realtà mista OpenXR Runtime supporterà un set di estensioni MSFT ed EXT che porteranno il set completo di funzionalità HoloLens 2 alle applicazioni OpenXR:
* [Spazio di riferimento senza limiti (esperienze su scala mondiale)](coordinate-systems.md#building-a-world-scale-experience)
* [Ancoraggi spaziali e archiviazione](spatial-anchors.md)
* [Articolazione manuale + mesh mano](hands-and-tools.md)
* [Tracciamento oculare](eye-tracking.md)
* [Configurazioni di viste secondarie (acquisizione di realtà mista)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [Mapping spaziale](spatial-mapping.md)
* Interoperabilità con API Windows SDK

Sebbene alcune di queste estensioni possano iniziare come estensioni MSFT specifiche del fornitore, Microsoft e altri fornitori di runtime di OpenXR collaborano per progettare estensioni EXT o KHR tra fornitori per molte di queste aree di funzionalità.  In questo modo il codice scritto per le funzionalità sarà portabile tra i fornitori di runtime, come per la specifica di base.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Di seguito sono riportati alcuni suggerimenti per la risoluzione dei problemi per la realtà mista OpenXR Runtime.  Per eventuali altre domande sulla [specifica OpenXR 1,0](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html), visitare il [Forum Khronos OpenXR](https://community.khronos.org/c/openxr) o il [canale Slack #openxr](https://khr.io/slack).

### <a name="developing-on-windows-10-october-2018-update"></a>Sviluppo in Windows 10 ottobre 2018 aggiornamento

Se non si è in grado di [aggiornare il computer di sviluppo all'aggiornamento di maggio 2019](https://www.microsoft.com/en-us/software-download/windows10), è possibile configurare il PC Windows 10 ottobre 2018 update (1809) per lo sviluppo attenendosi a un altro passaggio:

1. Attenersi alla procedura descritta in precedenza per iniziare a usare OpenXR nel PC desktop.
1. Per impostare la realtà mista OpenXR runtime come runtime OpenXR attivo del sistema, installare la [realtà mista OpenXR Developer Compatibility Pack](https://aka.ms/openxr-compat).

> [!NOTE]
> Sebbene sia possibile usare l'aggiornamento di Windows 10 ottobre 2018 (1809) quando si sviluppano le applicazioni OpenXR, l'aggiornamento di Windows 10 2019 (1903) è il requisito minimo per consentire agli utenti finali di usare OpenXR con la realtà mista di Windows.  È possibile che si verifichino minori prestazioni o altri problemi durante l'esecuzione dell'app OpenXR nell'aggiornamento del 2018 ottobre.  Si consiglia vivamente di aggiornare il computer di sviluppo all'aggiornamento 2019 di Windows 10 (1903).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>App OpenXR che non avvia la realtà mista di Windows

Se l'app OpenXR non avvia la realtà mista di Windows quando viene eseguita, il runtime OpenXR di realtà mista potrebbe non essere impostato come runtime attivo.  Assicurarsi di eseguire l'app del portale per sviluppatori OpenXR di realtà mista e seguire le istruzioni per rendere attivo il Runtime.

### <a name="mixed-reality-openxr-developer-portal-app-cannot-be-installed"></a>Non è possibile installare l'app del portale per sviluppatori OpenXR per la realtà mista 

Assicurarsi di eseguire almeno l'aggiornamento di Windows 10 ottobre 2018 (1809).  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento all'aggiornamento 2019 di maggio (1903) con [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).

Se il pulsante Installa nell'app del portale per sviluppatori della realtà mista OpenXR non esegue alcuna operazione nell'aggiornamento di Windows 10 ottobre 2018, il sistema potrebbe avere memorizzato nella cache i requisiti di sistema non aggiornati per l'app.  È possibile eseguire il comando `wsreset.exe` da un prompt dei comandi per cancellare la cache.

## <a name="see-also"></a>Vedere anche

* [Altre informazioni su OpenXR](https://www.khronos.org/openxr/)
* [Specifica OpenXR 1,0](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html)
* [Informazioni di riferimento sull'API OpenXR 1,0](https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html)
* [Guida di riferimento rapido per OpenXR 1,0](https://www.khronos.org/registry/OpenXR/specs/1.0/refguide/OpenXR-1.0-web.pdf)
