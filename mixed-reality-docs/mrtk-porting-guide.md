---
title: Preparare un'app per HoloLens 2
description: Questo articolo è destinato agli sviluppatori che dispongono di un'app esistente su HoloLens (prima generazione) e/o della versione precedente del toolkit MRTK e che vogliono eseguire la conversione a MRTK versione 2 e HoloLens 2.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, testare, MRTK, MRTK versione 2, HoloLens 2
ms.openlocfilehash: 02dabd21b7a6add2ce53fe291a447e49057184d0
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270388"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>Preparare un'app esistente per HoloLens 2

Questa guida è progettata appositamente per aiutare gli sviluppatori che dispongono di un'app Unity esistente per HoloLens (prima generazione) a convertire la propria applicazione per il nuovo dispositivo HoloLens 2. Esistono quattro passaggi principali per la conversione di un'app Unity per HoloLens (prima generazione) a HoloLens 2. Le sezioni seguenti forniscono informazioni dettagliate per ogni fase. 

| Passaggio 1 | Passaggio 2 | Passaggio 3 | Passaggio 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logo di Visual Studio](images/visualstudio_logo.png) | ![Logo di Unity](images/unity_logo.png)| ![Icona di Unity](images/hololens2_icon.jpg) | ![Logo di MRTK](images/MRTKIcon.jpg) |
| Scaricare gli strumenti più recenti | Aggiornare un progetto Unity | Eseguire la compilazione per ARM | Eseguire la migrazione a MRTK v2

Prima di iniziare il processo di conversione, è **altamente consigliato** che gli sviluppatori usino il controllo del codice sorgente per salvare uno snapshot dello stato originale della propria app. Inoltre, è consigliabile *salvare* gli stati dei checkpoint in vari momenti durante il processo. Può anche essere molto utile disporre di un'altra istanza Unity dell'app originale per consentire il confronto side-by-side durante il processo di conversione. 

> [!NOTE]
> Prima della conversione, assicurati che siano installati gli strumenti più recenti per lo sviluppo con Windows Mixed Reality. Per la maggior parte degli sviluppatori HoloLens esistenti, questo passaggio comporterà principalmente l'aggiornamento alla versione Visual Studio 2017 più recente e all'installazione dell'SDK di Windows appropriato. Di seguito verranno analizzate in dettaglio diverse versioni di Unity e Mixed Reality Toolkit versione 2.
>
> Per altre informazioni, vedi [Installare gli strumenti](install-the-tools.md).

## <a name="migrate-project-to-latest-version-of-unity"></a>Eseguire la migrazione alla versione di Unity più recente

Se usi MRTK 2, Unity 2018 LTS sarà il percorso di supporto a lungo termine migliore senza modifiche di rilievo in Unity o in MRTK.  La build di Unity consigliata, secondo quanto indicato nell'argomento sopra menzionato "Installare gli strumenti", è Unity 2018.3, che diventerà la versione LTS per Unity 2018.  Inoltre, MRTK v2 garantirà sempre il supporto per Unity 2018 LTS, ma non necessariamente per ogni iterazione di Unity 2019.x. 

Per chiarire le altre differenze tra Unity 2018.3.x e Unity 2019.1.x, di seguito sono riportati i compromessi tra queste due versioni, in cui la differenza più significativa risulta essere la capacità di compilare per ARM64 in Unity 2019. 

Gli sviluppatori devono valutare eventuali [dipendenze da plug-in](https://docs.unity3d.com/Manual/Plugins.html) attualmente esistenti nel progetto e se queste DLL possono essere create per ARM64. Se non è possibile creare un plug-in con dipendenza rigida per ARM64, sarà necessario usare Unity 2018 LTS.


| Unity 2018.3.x | Unity 2019.1+ |
|----------|-------------------|
| Supporto per creazione per ARM32 | Supporto per creazione per ARM64 e ARM32 |
| Versione build LTS stabile | Stabilità beta |
| [Back-end di scripting .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *deprecato* | [Back-end di scripting .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *rimosso* |
| Rete UNET *deprecata* | Rete UNET *rimossa* |

## <a name="update-sceneproject-settings-in-unity"></a>Aggiornare le impostazioni di scena o progetto in Unity

Dopo l'aggiornamento a Unity 2018.3.x o Unity 2019+, è consigliabile aggiornare impostazioni specifiche in Unity per ottenere risultati ottimali nel dispositivo. Queste impostazioni sono descritte dettagliatamente nella sezione **[Impostazioni consigliate per Unity](Recommended-settings-for-Unity.md)** .

È opportuno ripetere che il [back-end di scripting .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) è deprecato in Unity 2018 e *rimosso* in Unity 2019 ed è pertanto consigliabile che gli sviluppatori valutino l'opportunità di passare il proprio progetto a [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). 

> [!NOTE]
> Poiché il back-end di scripting IL2CPP può comportare tempi di compilazione da Unity a Visual Studio più lunghi, gli sviluppatori devono configurare i computer di sviluppo in modo da [ottimizzare i tempi di compilazione IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> Inoltre, potrebbe essere utile configurare un [server di cache](https://docs.unity3d.com/Manual/CacheServer.html), soprattutto per i progetti Unity con una grande quantità di asset (esclusi i file di script) o con asset/scene in continua evoluzione. All'apertura di un progetto, Unity archivia gli asset validi in un formato della cache interna nel computer di sviluppo. Gli elementi devono essere reimportati e quindi rielaborati in caso di modifica. Questo processo può essere eseguito una volta, salvato in un server di cache e quindi condiviso con altri sviluppatori in modo da risparmiare tempo, evitando a ciascuno sviluppatore di elaborare la reimportazione di nuove modifiche in locale.

Una volta gestite eventuali modifiche di rilievo dopo il passaggio alla versione aggiornata di Unity, gli sviluppatori devono creare e testare le proprie app correnti su HoloLens (prima generazione). Questo è anche un buon momento per creare e salvare un commit per il controllo del codice sorgente. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilare dipendenze/plug-in per il processore ARM

HoloLens (prima generazione) esegue le applicazioni su un processore x86, mentre il nuovo dispositivo HoloLens 2 usa un processore ARM. Di conseguenza, le applicazioni esistenti devono essere convertite per supportare ARM. Come indicato in precedenza, Unity 2018 supporta la compilazione per le app ARM32, mentre Unity 2019+ supporta la compilazione per le app ARM64. Lo sviluppo per le applicazioni ARM64 è in genere preferibile in quanto esiste una differenza sostanziale nelle prestazioni. Tuttavia, in questo modo è necessario creare tutte le [dipendenze da plug-in](https://docs.unity3d.com/Manual/Plugins.html) anche per ARM64. 

Esamina tutte le dipendenze da DLL correnti dell'applicazione. Se una dipendenza non è più necessaria, è consigliabile rimuoverla dal progetto. Per i plug-in rimanenti che sono necessari, inserisci i rispettivi file binari ARM32 o ARM64 nel progetto Unity. 

Dopo aver inserito le DLL pertinenti, crea una soluzione Visual Studio da Unity e quindi compila AppX per ARM in Visual Studio per verificare che l'applicazione possa essere creata per processori ARM. Questo è un altro momento in cui è consigliabile salvare un commit nella soluzione di controllo del codice sorgente. 

## <a name="update-to-mrtk-version-2"></a>Eseguire l'aggiornamento a MRTK versione 2

MRTK versione 2 è il nuovo toolkit che controlla Unity e che supporta sia HoloLens (prima generazione) che HoloLens 2 e in cui sono state aggiunte tutte le nuove funzionalità di HoloLens 2, ad esempio le interazioni con le mani e il tracciamento oculare.

### <a name="prepare-for-the-migration"></a>Prepararsi per la migrazione

Prima dell'inserimento di nuovi [file *.unitypackage per MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), è consigliabile eseguire un inventario di **1) tutto il codice personalizzato che si integra con MRTK v1** e di **2) tutto il codice personalizzato per le interazioni di input o i componenti dell'esperienza utente**. L'impegno maggiore per uno sviluppatore di realtà mista che inserisce il nuovo toolkit MRTK v2 è relativo all'input e alle interazioni. È consigliabile pertanto leggere e comprendere il [modello di input di MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Infine, il nuovo toolkit MRTK v2 è passato da un modello di script e di oggetti di gestione in scena a un'architettura di provider di servizi e configurazione. Ne deriva un modello di architettura e gerarchia di scene più chiaro, ma anche l'esigenza di una curva di apprendimento per comprendere i nuovi profili di configurazione. Leggi pertanto [Guida alla configurazione di Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) per acquisire familiarità con le impostazioni e i profili importanti per soddisfare i requisiti dell'applicazione. 

### <a name="perform-the-migration"></a>Eseguire la migrazione

Dopo l'importazione di MRTK v2, un progetto Unity conterrà probabilmente molti errori relativi al compilatore. Questi errori in genere sono dovuti alla struttura dei nuovi spazi dei nomi e ai nomi dei nuovi componenti. Per risolvere questi errori, inserisci negli script i nuovi spazi dei nomi e componenti. 

Per altre informazioni sulle differenze di API specifiche tra HTK/MRTK e MRTK versione 2, vedi la guida di conversione nella [wiki di MRTK versione 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Procedure consigliate

- Prediligi l'uso dello shader MRTK Standard
- Lavora su un tipo di modifica sostanziale per volta (ad esempio: passaggio da IFocusable a IMixedRealityFocusHandler)
- Esegui il test dopo ogni modifica e usa il controllo del codice sorgente
- Usa l'esperienza utente MRTK predefinita (pulsanti, slate e così via) quando possibile
- Prova a evitare di modificare direttamente i file MRTK e crea invece wrapper intorno ai componenti MRTK
    - In questo modo sarai protetto in caso di inserimenti e aggiornamenti MRTK futuri
- Esamina ed esplora le scene di esempio fornite in MRTK (soprattutto *HandInteractionExamples.scene*)
- Ricrea invece l'interfaccia utente basata su aree di disegno con quadrilateri, collisori e testo TextMeshPro

### <a name="testing-your-application"></a>Test dell'applicazione

Ora che i componenti e le funzionalità di HoloLens 2 sono disponibili in MRTK versione 2, a partire da [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1) puoi simulare le interazioni con le mani disponibili direttamente in Unity e sviluppare con le nuove API per le interazioni con le mani e il tracciamento oculare.  Il dispositivo HoloLens 2 è necessario per creare un'esperienza ottimale, ma è almeno possibile iniziare ad acquisire familiarità con gli strumenti e la documentazione. Inoltre, MRTK v2 supporta lo sviluppo in HoloLens (prima generazione) e di conseguenza i modelli di input tradizionali come la selezione tramite simulazione del tocco possono comunque essere testati sui dispositivi HoloLens (prima generazione). 

## <a name="updating-interaction-model-for-hololens-2"></a>Aggiornamento del modello di interazione per HoloLens 2

Dopo aver convertito e preparato l'app per HoloLens 2, sei pronto per prendere in considerazione l'aggiornamento del modello di interazione e della progettazione o del posizionamento dell'ologramma.
Dal momento che proviene da HoloLens (prima generazione), è probabile che l'app disponga di un modello di interazione basato sullo sguardo fisso e il commit, con ologrammi relativamente lontani per rientrare nel campo di visualizzazione.

Passaggi per aggiornare la progettazione dell'app in modo ottimale per HoloLens 2:
1.  Componenti MRTK: per le operazioni preliminari, se hai aggiunto MRTK v2, sono disponibili diversi componenti/script progettati e ottimizzati per HoloLens 2.

2.  Modello di interazione: valuta l'opportunità di aggiornare il modello di interazione.  Per la maggior parte degli scenari, è consigliabile passare da sguardo fisso e commit alle mani.  Con gli ologrammi che in genere non sono raggiungibili stendendo le braccia, il passaggio all'uso delle mani consentirà di sfruttare raggi di puntamento e movimenti di cattura per l'interazione da lontano.
Nota: esistono scenari in cui è necessario un modello di interazione a mani libere, ad esempio per un operaio che maneggia strumenti. In questo caso sono disponibili indicazioni di progettazione specifiche. 

3.  Posizionamento dell'ologramma: dopo il passaggio a un modello di interazione con le mani, valuta la possibilità di avvicinare alcuni ologrammi per interagire direttamente con le mani, usando movimenti di cattura per l'interazione da vicino.  I tipi di ologrammi consigliati per avvicinarsi e afferrare o interagire direttamente sono menu, controlli e pulsanti di destinazione di dimensioni ridotte e ologrammi più piccoli che rientrano nel campo visivo di HoloLens 2 quando si afferra e si esamina l'ologramma.
<br>
Ogni app e ogni scenario hanno caratteristiche diverse e continueremo a perfezionare e pubblicare indicazioni di progettazione in base al feedback e alle nuove informazioni.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>Informazioni aggiuntive sul passaggio delle app da x86 ad ARM

- Le normali app Unity sono semplici perché permettono di creare un bundle di appx ARM o di eseguire la distribuzione direttamente sul dispositivo e procedere con l'esecuzione.
Il problema si verifica quando l'app Unity usa plug-in nativi.  Tutti i plug-in nativi devono essere aggiornati a VS2017 e ricreati per ARM e, con Unity 2019, per ARM64.

- Un'app usava il plug-in AudioKinetic Wwise per Unity e la versione usata non disponeva di un plug-in UWP ARM. Sono stati necessari diversi giorni per rimaneggiare il suono nell'applicazione in modo che funzionasse su ARM.

- In altri casi, è possibile che non esista un plug-in UWP/ARM per i plug-in necessari per l'app, impedendo la conversione e l'esecuzione su HoloLens 2.  Potrebbe essere necessario contattare il provider del plug-in per lo sblocco e per il supporto di ARM.

- Il minfloat (e varianti quali min16float e minint e così via) in shader possono comportarsi in modo diverso in HoloLen 2 rispetto a HoloLens (prima generazione). In particolare, in questo modo viene garantito che "venga usato almeno il numero specificato di bit". Nelle GPU Intel/Nvidia vengono considerati in larga misura come 32 bit. In ARM il numero di bit specificato viene effettivamente rispettato. Ciò significa che in pratica questi numeri possono avere una portata con una precisione minore in HoloLens 2 rispetto a quanto accade in HoloLens (prima generazione).

- Le istruzioni _asm non sembrano funzionare in ARM, pertanto il codice con istruzioni _asm dovrà essere riscritto.

- Il set di istruzioni SIMD non è supportato in ARM. Ciò significa che varie intestazioni, ad esempio xmmintrin.h, emmintrin.h, tmmintrin.h e immintrin.h non sono disponibili in ARM.

- Il compilatore dello shader in ARM viene eseguito durante la prima chiamata di disegno dopo il caricamento dello shader o dopo che è cambiato qualcosa su cui si basa lo shader, non in fase di caricamento dello shader. L'impatto sulla frequenza dei fotogrammi può essere notevole, a seconda di quanti shader devono essere compilati. Questo comporta diverse implicazioni per come devono essere gestiti/inclusi in pacchetti/aggiornati gli shader in modo diverso in HoloLens 2 rispetto a HoloLens (prima generazione).

## <a name="see-also"></a>Vedi anche
* [Guida introduttiva a MRTK versione 2](mrtk-getting-started.md)
* [Procedure relative a MRTK versione 2](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [Installare gli strumenti](install-the-tools.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)

