---
title: Preparare un'app esistente per HoloLens 2
description: Queste informazioni sono destinate agli sviluppatori che hanno un'app esistente in HoloLens (prima generazione) e/o una versione precedente di MRTK e vogliono eseguire la conversione a MRTK versione 2 e HoloLens 2.
author: grbury
ms.author: grbury
ms.date: 07/29/2020
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, testare, MRTK, MRTK versione 2, HoloLens 2
ms.openlocfilehash: a6d6c4ad2b9ec0de2663536f2299f31f7d79571a
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476993"
---
# <a name="get-your-existing-app-ready-for-hololens-2"></a>Preparare un'app esistente per HoloLens 2

## <a name="overview"></a>Panoramica

Questa guida è progettata appositamente per aiutare gli sviluppatori con un'applicazione Unity per HoloLens (prima generazione) a convertirla per il dispositivo HoloLens 2. Per la conversione di un'applicazione Unity da HoloLens (prima generazione) a HoloLens 2, è necessario completare quattro passaggi. 

Le sezioni seguenti forniscono informazioni dettagliate per ogni fase:

| Passaggio 1 | Passaggio 2 | Passaggio 3 | Passaggio 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logo di Visual Studio](images/visualstudio_logo.png) | ![Logo di Unity](images/final_unity_logo.png)| ![Icona di Unity](images/hololens2_icon.jpg) | ![Logo di MRTK](images/final_mrtk-small_logo.png) |
| Scaricare gli strumenti più recenti | Aggiornare un progetto Unity | Eseguire la compilazione per ARM | Eseguire la migrazione a MRTK v2

Prerequisiti:

Prima di iniziare il processo di conversione, è **consigliabile** usare il controllo del codice sorgente per salvare uno snapshot dello stato originale dell'applicazione. Inoltre, è consigliabile *salvare* gli stati dei checkpoint in vari momenti durante il processo. Può anche essere utile avere un'altra istanza Unity dell'applicazione originale per eseguire il confronto affiancato durante il processo di conversione. 

> [!NOTE]
> Prima della conversione, assicurati che siano installati gli strumenti più recenti per lo sviluppo con Windows Mixed Reality. Per la maggior parte degli attuali sviluppatori HoloLens, questo passaggio comporta l'aggiornamento all'ultima versione di Visual Studio 2019 e l'installazione dell'istanza appropriata di Windows SDK. Di seguito verranno analizzate in dettaglio diverse versioni di Unity e Mixed Reality Toolkit (MRTK) versione 2.
>
> Per altre informazioni, vedi [Installare gli strumenti](install-the-tools.md).

## <a name="migrate-project-to-the-latest-version-of-unity"></a>Eseguire la migrazione del progetto all'ultima versione di Unity

Se si usa [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), [Unity 2019 LTS](https://unity3d.com/unity/qa/lts-releases) è il percorso di supporto a lungo termine ottimale senza modifiche di rilievo in Unity o in MRTK. È necessario valutare tutte le [dipendenze da plug-in](https://docs.unity3d.com/Manual/Plugins.html) attualmente esistenti nel progetto e stabilire se è possibile creare le DLL per ARM64. Se non è possibile compilare un plug-in con dipendenza rigida per ARM64, potrebbe essere necessario continuare a compilare l'app per ARM.

<!-- MRTK v2 always guarantees support for Unity 2018 LTS, but does not necessarily guarantee support for every iteration of Unity 2019.x.

To help clarify additional differences between [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) and Unity 2019.x, the following table outlines the trade-offs between the two versions. The primary difference between the two is the ability to compile for ARM64 in Unity 2019.

| Unity 2018 LTS | Unity 2019.x |
|----------|-------------------|
| ARM32 build support | ARM32 and ARM64 build support |
| Stable LTS build release | Beta stability |
| [.NET Scripting back-end](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *deprecated* | [.NET Scripting back-end](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *removed* |
| UNET Networking *deprecated* | UNET Networking *deprecated* |

-->

## <a name="update-sceneproject-settings-in-unity"></a>Aggiornare le impostazioni di scena o progetto in Unity

Dopo l'aggiornamento a [Unity 2019 LTS](https://unity3d.com/unity/qa/lts-releases), è consigliabile aggiornare specifiche impostazioni di Unity per ottenere risultati ottimali nel dispositivo. Queste impostazioni sono descritte in dettaglio nella sezione [Impostazioni consigliate per Unity](Recommended-settings-for-Unity.md).

È opportuno ripetere che il [back-end di scripting .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) è stato deprecato in Unity 2018 e *rimosso* in Unity 2019. Per gli sviluppatori è consigliabile passare a [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html) per il loro progetto.

> [!NOTE]
> Il back-end di scripting IL2CPP può comportare tempi di compilazione da Unity a Visual Studio più lunghi, quindi gli sviluppatori devono configurare i computer di sviluppo in modo da [ottimizzare i tempi di compilazione di IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> Inoltre, potrebbe essere utile configurare un [server di cache](https://docs.unity3d.com/Manual/CacheServer.html), soprattutto per i progetti Unity con una grande quantità di asset (esclusi i file di script) o con asset e scene che cambiano continuamente. All'apertura di un progetto, Unity archivia gli asset validi in un formato della cache interna nel computer di sviluppo. Gli elementi devono essere reimportati e rielaborati in caso di modifica. Questo processo può essere eseguito una volta sola, salvato in un server di cache e quindi condiviso con altri sviluppatori in modo da risparmiare tempo, evitando a ciascuno sviluppatore di elaborare la reimportazione di nuove modifiche in locale.

Dopo aver gestito tutte le modifiche di rilievo derivanti dal passaggio alla versione aggiornata di Unity, è necessario creare e testare le applicazioni correnti in HoloLens (prima generazione). In questa fase è anche opportuno creare e salvare un commit per il controllo del codice sorgente.

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilare dipendenze/plug-in per il processore ARM

HoloLens (prima generazione) esegue le applicazioni su un processore x86, mentre HoloLens 2 si basa su un processore ARM. Di conseguenza, le applicazioni HoloLens esistenti devono essere convertite per supportare ARM. Come indicato in precedenza, Unity 2018 LST supporta la compilazione per app ARM32, mentre Unity 2019.x supporta la compilazione per app ARM32 e ARM64. Lo sviluppo per le applicazioni ARM64 è preferibile in quanto esiste una differenza sostanziale nelle prestazioni. Tuttavia, in questo modo è necessario creare tutte le [dipendenze da plug-in](https://docs.unity3d.com/Manual/Plugins.html) anche per ARM64.

Esamina tutte le dipendenze da DLL dell'applicazione. Se una dipendenza non è più necessaria, è consigliabile rimuoverla dal progetto. Per i plug-in rimanenti che sono necessari, inserisci i rispettivi file binari ARM32 o ARM64 nel progetto Unity.

Dopo aver inserito le DLL pertinenti, crea una soluzione Visual Studio da Unity e quindi compila AppX per ARM in Visual Studio per verificare che l'applicazione possa essere creata per processori ARM. È consigliabile salvare l'applicazione come commit nella soluzione di controllo del codice sorgente.

> [!IMPORTANT]
> Le applicazioni che usano MRTK v1 possono essere eseguite in HoloLens 2 dopo aver impostato la destinazione di compilazione su ARM, presupponendo che tutti gli altri requisiti siano soddisfatti, inclusa la presenza di versioni ARM di tutti i plug-in. L'app, tuttavia, non potrà accedere alle funzioni specifiche di HoloLens 2, ad esempio il tracciamento della mano e il tracciamento oculare articolati. MRTK v1 e MRTK v2 hanno spazi dei nomi diversi che consentono di mantenere entrambe le versioni nello stesso progetto, meccanismo utile per la transizione da una versione all'altra.

## <a name="update-to-mrtk-version-2"></a>Eseguire l'aggiornamento a MRTK versione 2

[MRTK versione 2](https://github.com/microsoft/MixedRealityToolkit-Unity) è il nuovo toolkit che controlla Unity e che supporta sia HoloLens (prima generazione) che HoloLens 2. In questo toolkit sono state aggiunte tutte le nuove funzionalità di HoloLens 2, ad esempio le interazioni con le mani e il tracciamento oculare.

Per altre informazioni sull'uso di MRTK versione 2, vedere le risorse seguenti:

- [Pagina di destinazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
- [Introduzione a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
- [Interazioni con le mani in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
- [Tracciamento oculare in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

### <a name="prepare-for-the-migration"></a>Prepararsi per la migrazione

Prima dell'inserimento di nuovi [file *.unitypackage per MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), è consigliabile eseguire un inventario di **1) tutto il codice personalizzato che si integra con MRTK v1** e di **2) tutto il codice personalizzato per le interazioni di input o i componenti dell'esperienza utente**. L'impegno maggiore per uno sviluppatore di realtà mista che inserisce il toolkit MRTK v2 è relativo all'input e alle interazioni. È consigliabile pertanto leggere e comprendere il [modello di input di MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Infine, il nuovo toolkit [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) è passato da un modello di script e di oggetti di gestione in scena a un'architettura di provider di servizi e configurazione. Ne deriva un modello di architettura e gerarchia di scene più chiaro, ma anche l'esigenza di una curva di apprendimento per comprendere i nuovi profili di configurazione. Leggi pertanto [Guida alla configurazione di Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) per acquisire familiarità con le impostazioni e i profili importanti per soddisfare i requisiti dell'applicazione.

### <a name="perform-the-migration"></a>Eseguire la migrazione

Dopo l'importazione di [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), il progetto Unity conterrà probabilmente molti errori relativi al compilatore. Si tratta in genere di errori dovuti alla struttura dei nuovi spazi dei nomi e ai nomi dei nuovi componenti. Per risolvere questi errori, inserisci negli script i nuovi spazi dei nomi e componenti.

Per informazioni sulle differenze di API specifiche tra HTK/MRTK e MRTK v2, vedi la guida di conversione nella [wiki di MRTK versione 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Procedure consigliate

- Prediligi l'uso dello [shader MRTK Standard](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html).
- Lavora su un tipo di modifica sostanziale per volta (ad esempio: da IFocusable a [IMixedRealityFocusHandler](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler.html)).
- Esegui il test dopo ogni modifica e usa il controllo del codice sorgente.
- Quando possibile, usare l'esperienza utente MRTK predefinita (pulsanti, slate e così via).
- Evita di modificare direttamente i file MRTK e crea invece wrapper intorno ai componenti MRTK.
    - Questa azione semplifica inserimenti e aggiornamenti MRTK futuri.
- Esamina ed esplora le scene di esempio fornite in MRTK (soprattutto *HandInteractionExamples.scene*).
- Ricrea l'interfaccia utente basata su aree di disegno con quadrilateri, collisori e testo TextMeshPro.
- Abilita la [condivisione dei buffer di intensità](camera-in-unity.md#sharing-your-depth-buffers-with-windows) o [imposta il punto di messa a fuoco](focus-point-in-unity.md); usa un buffer di intensità di 16 bit per prestazioni migliori. Quando esegui il rendering del colore, assicurati di farlo anche per la profondità. Unity in genere non scrive la profondità per oggetti gioco trasparenti e di testo. 
- Imposta il percorso di rendering con istanze a singolo passaggio.
- Usa il [profilo di configurazione di HoloLens 2 per MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html#hololens-2-profile).

### <a name="testing-your-application"></a>Test dell'applicazione

In MRTK versione 2 puoi simulare le interazioni con le mani disponibili direttamente in Unity e sviluppare con le nuove API per le interazioni con le mani e il tracciamento oculare. Il dispositivo HoloLens 2 è necessario per creare un'esperienza utente soddisfacente. È consigliabile iniziare a studiare la documentazione e gli strumenti per acquisire una maggiore familiarità. [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) supporta lo sviluppo in HoloLens (prima generazione) e i modelli di input tradizionali, come la selezione tramite simulazione del tocco, possono essere testati in questa generazione di dispositivi. 

## <a name="updating-your-interaction-model-for-hololens-2"></a>Aggiornamento del modello di interazione per HoloLens 2

Dopo aver convertito e preparato l'applicazione per HoloLens 2, puoi iniziare a prendere in considerazione l'aggiornamento del modello di interazione del posizionamento degli ologrammi.
In HoloLens (prima generazione) è probabile che l'applicazione abbia un modello di interazione basato sullo sguardo fisso e il commit, con ologrammi relativamente lontani per rientrare nel campo di visualizzazione.

Passaggi per aggiornare la progettazione dell'applicazione in modo ottimale per HoloLens 2:
1.  Componenti MRTK: per le operazioni preliminari, se hai aggiunto [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), sono disponibili diversi componenti/script progettati e ottimizzati per HoloLens 2.

2.  Modello di interazione: valuta l'opportunità di aggiornare il modello di interazione. Per la maggior parte degli scenari, è consigliabile passare da sguardo fisso e commit alle mani. Con gli ologrammi che in genere non sono raggiungibili stendendo le braccia, il passaggio all'uso delle mani consente di sfruttare raggi di puntamento e movimenti di cattura per l'interazione da lontano.

3.  Posizionamento dell'ologramma: dopo il passaggio a un modello di interazione con le mani, valuta la possibilità di avvicinare alcuni ologrammi per interagire direttamente usando movimenti di cattura per l'interazione da vicino con le mani. I tipi di ologrammi consigliati per avvicinarsi e afferrare o interagire direttamente sono menu, controlli e pulsanti di destinazione di dimensioni ridotte e ologrammi più piccoli che rientrano nel campo visivo di HoloLens 2 quando si afferra e si esamina l'ologramma.
<br>
Ogni applicazione e ogni scenario hanno caratteristiche diverse e si proseguirà con il perfezionamento e la pubblicazione di indicazioni di progettazione in base al feedback e alle nuove informazioni.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>Avvertenze e informazioni aggiuntive sullo spostamento di applicazioni da x86 ad ARM

- Le applicazioni Unity lineari sono semplici perché è possibile creare un bundle di applicazioni ARM o distribuirle direttamente nel dispositivo per l'esecuzione del bundle. Alcuni plug-in nativi di Unity possono presentare specifici problemi di sviluppo. Per questo motivo, è necessario aggiornare tutti i plug-in nativi di Unity a Visual Studio 2019 e quindi rieseguire la compilazione per ARM.

- Per un'applicazione è stato usato il plug-in AudioKinetic Wwise di Unity e tale versione di Unity non include un plug-in ARM UWP, quindi è stato necessario un notevole sforzo per rielaborare le funzionalità audio nell'applicazione in questione per l'esecuzione in ARM. Assicurati che tutti i plug-in necessari per i tuoi piani di sviluppo siano installati e disponibili in Unity.

- In alcuni casi, tra i plug-in richiesti dall'applicazione potrebbe non esistere un plug-in ARM/UWP, il che impedisce la possibilità di convertirla ed eseguirla in HoloLens 2. Contatta il provider di plug-in per risolvere il problema e fornire il supporto per ARM.

- I valori minfloat (e varianti come min16float, minint e così via) negli shader possono avere un comportamento diverso in HoloLens 2 rispetto a HoloLens (prima generazione). In particolare, garantiscono che venga usato almeno il numero specificato di bit. Nelle GPU Intel/Nvidia vengono considerati in larga misura come 32 bit. In ARM il numero di bit specificato viene effettivamente rispettato. Ciò significa che in pratica questi numeri possono avere una portata o una precisione minore in HoloLens 2 rispetto a quanto accade in HoloLens (prima generazione).

- Le istruzioni _asm non sembrano funzionare in ARM, pertanto il codice con istruzioni _asm deve essere riscritto.

- Il set di istruzioni SIMD non è supportato in ARM perché varie intestazioni, come xmmintrin.h, emmintrin.h, tmmintrin.h e immintrin.h, non sono disponibili in ARM.

- Il compilatore dello shader in ARM viene eseguito durante la prima chiamata di disegno dopo il caricamento dello shader o dopo che è cambiato qualcosa su cui si basa lo shader, non in fase di caricamento dello shader. L'impatto sulla frequenza dei fotogrammi può essere notevole, a seconda del numero di shader da compilare. Questo comporta diverse implicazioni perché gli shader devono essere gestiti, inclusi in pacchetti o aggiornati in modo diverso in HoloLens 2 rispetto a HoloLens (prima generazione).

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* [Guida introduttiva a MRTK versione 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Aggiornamento dalle API HTK alle API MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)

