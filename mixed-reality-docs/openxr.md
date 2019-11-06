---
title: OpenXR
description: È possibile creare un motore usando lo standard dell'API OpenXR portatile e distribuirlo in una realtà mista di Windows e in HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, realtà mista OpenXR portale per sviluppatori, DirectX, nativo, motore personalizzato app native, middleware
ms.openlocfilehash: d29b59d7dec19e5423c83ea6e61bb5625c8981dd
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641136"
---
# <a name="openxr"></a>OpenXR

OpenXR è uno standard API senza diritti d'autore aperto da <a href="https://www.khronos.org/" target="_blank">Khronos</a> che fornisce ai motori l'accesso nativo a un'ampia gamma di dispositivi di molti fornitori che si estendono nello [spettro della realtà mista](mixed-reality.md).

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

Per informazioni sull'API OpenXR, vedere la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica</a>OpenXR 1,0, informazioni di <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">riferimento sulle API</a> e <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guida di riferimento rapido</a>.  Per ulteriori informazioni, vedere la <a href="https://www.khronos.org/openxr/" target="_blank">pagina Khronos OpenXR</a>.

Per avere come destinazione il set completo di funzionalità di HoloLens 2, si useranno anche estensioni OpenXR specifiche del fornitore e dei fornitori che consentono funzionalità aggiuntive oltre al core OpenXR 1,0, ad esempio il rilevamento a mano articolato, il monitoraggio degli occhi, il mapping spaziale e i ancoraggi spaziali.  Vedere la sezione della Guida di [orientamento](openxr.md#roadmap) riportata di seguito per altre informazioni sulle estensioni riportate più avanti in questo anno.

Si noti che OpenXR non è a sua volta un motore di realtà mista.  OpenXR consente invece ai motori come Unity e Unreal di scrivere codice portatile una volta che può accedere alle funzionalità della piattaforma nativa del dispositivo olografico o immersivo dell'utente, indipendentemente dal fornitore che ha creato tale piattaforma.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introduzione a OpenXR per HoloLens 2

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2:

1. Configurare un HoloLens 2 o seguire le istruzioni per [installare l'emulatore HoloLens 2](using-the-hololens-emulator.md).
1. Avviare l'App Store dall'interno del dispositivo o dell'emulatore e assicurarsi che tutte le app vengano aggiornate.  In questo modo si garantisce che il runtime di OpenXR in HoloLens venga aggiornato a OpenXR 1,0.  Se si usa l'emulatore, è consigliabile consultare le [istruzioni di input dell'emulatore](using-the-hololens-emulator.md#basic-emulator-input) per usare l'app dello Store all'interno dell'emulatore.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introduzione a OpenXR per le cuffie con la realtà mista di Windows

Per iniziare a sviluppare applicazioni OpenXR per cuffie di realtà miste di Windows Immersive:

1. Assicurarsi di eseguire l'aggiornamento di Windows 10 2019 (1903), che è il requisito minimo per gli utenti finali di Windows Mixed Reality per l'esecuzione di applicazioni OpenXR.  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento all'aggiornamento di maggio 2019 usando <a href="https://www.microsoft.com//software-download/windows10" target="_blank">Windows 10 Update Assistant</a>.  Se non si è in grado di aggiornare il PC, è anche possibile [sviluppare l'app OpenXR usando l'aggiornamento di Windows 10 ottobre 2018 (1809)](openxr.md#developing-on-windows-10-october-2018-update), sebbene sia possibile riscontrare prestazioni ridotte o altri problemi.
2. Configurare un auricolare di realtà mista di Windows o seguire le istruzioni per [abilitare il simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md).  Dopo aver configurato la realtà mista di Windows, il portale di realtà mista installerà automaticamente il runtime di OpenXR di realtà mista di Windows.  Il Microsoft Store manterrà aggiornato il Runtime.
3. Rendere attiva la realtà mista di Windows OpenXR runtime avviando il portale di realtà mista dal menu Start, facendo clic sul pulsante... menu in basso a sinistra e selezionando "Configura OpenXR".<br>
![la configurazione di OpenXR nel portale per la realtà mista](images/mixed-reality-portal-set-up-openxr.png)

Se è necessario riattivare la realtà mista di Windows OpenXR Runtime, ripetere il passaggio 3.

> [!NOTE]
> Il runtime di OpenXR per la realtà mista di Windows verrà presto configurato automaticamente per tutti gli utenti finali di Windows Mixed Reality.

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>Ottenere il portale per sviluppatori OpenXR realtà mista

Per provare il runtime di OpenXR per la realtà mista di Windows, è possibile installare l' <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">app del portale per sviluppatori OpenXR per la realtà mista</a>.  Questa app fornisce una scena demo che esercita varie funzionalità di OpenXR, insieme a una pagina di stato del sistema che fornisce informazioni chiave sul runtime attivo e sull'auricolare corrente.

![App del portale per sviluppatori della realtà mista OpenXR](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>Compilazione di un'app OpenXR di esempio

Il progetto <a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> illustra un semplice esempio di OpenXR con due file di progetto di Visual Studio, uno per un'app desktop Win32 e uno per un'app UWP HoloLens 2.  Poiché la soluzione contiene un progetto HoloLens UWP, è necessario che il [carico di lavoro di sviluppo piattaforma UWP (Universal Windows Platform)](install-the-tools.md#installation-checklist) installato in Visual Studio per aprirlo completamente.

Si noti che, mentre i file di progetto Win32 e UWP sono separati a causa delle differenze nella creazione di pacchetti e distribuzione, il codice dell'app all'interno di ogni progetto è uguale al 100%.

## <a name="roadmap"></a>Roadmap

La specifica OpenXR definisce un meccanismo di estensione che consente agli implementatori del runtime di esporre funzionalità aggiuntive oltre le [funzionalità](openxr.md#what-is-openxr) di <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">base definite nella specifica OpenXR 1,0 di base</a>.

Sono disponibili tre tipi di estensioni OpenXR:
* **Estensioni Fornitore (ad esempio, MSFT):** Consente l'innovazione per fornitore in funzionalità hardware o software.  Qualsiasi fornitore di runtime può introdurre e distribuire un'estensione del fornitore in qualsiasi momento.
* **Estensioni ext:** Estensioni tra fornitori che vengono definite e implementate da più aziende.  I gruppi di società interessate possono introdurre estensioni EXT in qualsiasi momento.
* **Estensioni KHR:** Estensioni Khronos ufficiali ratificate come parte di una versione di base delle specifiche.  Le estensioni KHR sono coperte dalla stessa licenza della specifica principale.

Entro la fine dell'anno, il runtime di OpenXR per la realtà mista di Windows supporterà un set di estensioni MSFT ed EXT che porteranno il set completo di funzionalità HoloLens 2 alle applicazioni OpenXR:
* [Spazio di riferimento senza limiti (esperienze su scala mondiale)](coordinate-systems.md#building-a-world-scale-experience)
* [Ancoraggi spaziali e archiviazione](spatial-anchors.md)
* [Articolazione manuale + mesh mano](hands-and-tools.md)
* [Tracciamento oculare](eye-tracking.md)
* [Configurazioni di viste secondarie (acquisizione di realtà mista)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [Informazioni sulle scene](scene-understanding.md)
* Interoperabilità con API Windows SDK

Sebbene alcune di queste estensioni possano iniziare come estensioni MSFT specifiche del fornitore, Microsoft e altri fornitori di runtime di OpenXR collaborano per progettare estensioni EXT o KHR tra fornitori per molte di queste aree di funzionalità.  In questo modo il codice scritto per le funzionalità sarà portabile tra i fornitori di runtime, come per la specifica di base.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Ecco alcuni suggerimenti per la risoluzione dei problemi relativi al runtime di OpenXR per la realtà mista di Windows.  Per eventuali altre domande sulla <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica OpenXR 1,0</a>, visitare il <a href="https://community.khronos.org/c/openxr" target="_blank">Forum Khronos OpenXR</a> o il <a href="https://khr.io/slack" target="_blank">canale Slack #openxr</a>.

### <a name="developing-on-windows-10-october-2018-update"></a>Sviluppo in Windows 10 ottobre 2018 aggiornamento

Se non si è in grado di [aggiornare il computer di sviluppo all'aggiornamento di maggio 2019](https://www.microsoft.com//software-download/windows10), è possibile configurare il PC Windows 10 ottobre 2018 update (1809) per lo sviluppo attenendosi a un altro passaggio:

1. Attenersi alla procedura descritta in precedenza per iniziare a usare OpenXR nel PC desktop.
1. Per impostare il runtime di OpenXR per la realtà mista di Windows come runtime OpenXR attivo del sistema, installare la [realtà mista di Windows OpenXR Developer Compatibility Pack](https://aka.ms/openxr-compat).

> [!NOTE]
> Sebbene sia possibile usare l'aggiornamento di Windows 10 ottobre 2018 (1809) quando si sviluppano le applicazioni OpenXR, l'aggiornamento di Windows 10 2019 (1903) è il requisito minimo per consentire agli utenti finali di usare OpenXR con la realtà mista di Windows.  È possibile che si verifichino minori prestazioni o altri problemi durante l'esecuzione dell'app OpenXR nell'aggiornamento del 2018 ottobre.  Si consiglia vivamente di aggiornare il computer di sviluppo all'aggiornamento 2019 di Windows 10 (1903).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>App OpenXR che non avvia la realtà mista di Windows

Se l'app OpenXR non avvia la realtà mista di Windows quando viene eseguita, il runtime di OpenXR per la realtà mista di Windows non può essere impostato come runtime attivo.  Assicurarsi di seguire le istruzioni riportate sopra per iniziare a usare [OpenXR per le cuffie di realtà miste di Windows](#getting-started-with-openxr-for-windows-mixed-reality-headsets) in modo che il Runtime sia attivo.

È anche possibile eseguire la [realtà mista OpenXR Developer Portal](#getting-the-mixed-reality-openxr-developer-portal) per informazioni aggiuntive sulla risoluzione dei problemi relativi allo stato del runtime di OpenXR per la realtà mista di Windows nel sistema.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Il portale per la realtà mista non Mostra la voce di menu "Configura OpenXR"

Assicurarsi di eseguire almeno l'aggiornamento di Windows 10 ottobre 2018 (1809).  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento all'aggiornamento 2019 di maggio (1903) con [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10).

La voce di menu "Configura OpenXR" potrebbe non essere disponibile se si dispone di una versione precedente dell'app del portale per la realtà mista.  Verificare la presenza di un [aggiornamento dell'app portale per realtà mista](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) per assicurarsi di avere la versione più recente.

Si noti che la voce di menu "Configura OpenXR" non verrà visualizzata se il runtime OpenXR di Windows Mixed Reality è già installato e attivo.  È possibile installare la [realtà mista OpenXR Developer Portal](#getting-the-mixed-reality-openxr-developer-portal) per determinare lo stato corrente del runtime di OpenXR nel sistema.

## <a name="see-also"></a>Vedi anche

* <a href="https://www.khronos.org/openxr/" target="_blank">Altre informazioni su OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Specifica OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Informazioni di riferimento sull'API OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guida di riferimento rapido per OpenXR 1,0</a>
