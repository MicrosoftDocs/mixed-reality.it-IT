---
title: Operazioni preliminari per HoloLens 2 all'app
description: Rivolto agli sviluppatori che hanno un'app esistente per HoloLens (dal 1 ° generazione) e/o meno recenti MRTK e cercando alla porta al MRTK versione 2 e HoloLens 2.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista di Windows, testare, MRTK, MRTK versione 2, 2 HoloLens
ms.openlocfilehash: 02dabd21b7a6add2ce53fe291a447e49057184d0
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270388"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>Operazioni preliminari per HoloLens 2 l'app esistente

Questa guida è progettata appositamente per aiutare gli sviluppatori che dispongono di un'app esistente di Unity per HoloLens (dal 1 ° generazione) alla propria applicazione per il nuovo dispositivo HoloLens 2 di porta. Esistono quattro passaggi principali per il porting di un HoloLens (dal 1 ° generazione) dell'app Unity HoloLens 2. Le sezioni seguenti in modo dettagliato le informazioni per ogni fase. 

| Passaggio 1 | Passaggio 2 | Passaggio 3 | Passaggio 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logo di Visual Studio](images/visualstudio_logo.png) | ![Logo di Unity](images/unity_logo.png)| ![Icona di Unity](images/hololens2_icon.jpg) | ![Logo MRTK](images/MRTKIcon.jpg) |
| Scarica gli strumenti più recenti | Aggiornare un progetto Unity | Compilare il codice per ARM | Eseguire la migrazione a MRTK v2

Si tratta **altamente consigliato** che, prima di iniziare il processo di porting, gli sviluppatori di usare il codice sorgente per salvare uno snapshot dello stato originale della propria app. Inoltre, è consigliabile *salvare* gli stati di checkpoint in vari momenti durante il processo. Può anche essere molto utile avere un'altra istanza di Unity dell'app originale per consentire il confronto side-by-side durante il processo di porta. 

> [!NOTE]
> Prima della conversione, assicurarsi di che avere gli strumenti più recenti per lo sviluppo della realtà mista di Windows installati. Per la maggior parte degli sviluppatori di HoloLens esistente, questo passaggio comporterà principalmente l'aggiornamento per la versione più recente di Visual Studio 2017 e installare il SDK di Windows appropriato. Il contenuto seguente verrà approfondire ulteriormente in diverse versioni di Unity e il Toolkit di realtà mista versione 2.
>
> Per altre informazioni, vedi [installare gli strumenti](install-the-tools.md).

## <a name="migrate-project-to-latest-version-of-unity"></a>Eseguire la migrazione di progetti alla versione più recente di Unity

Se si usa la versione 2 MRTK, Unity 2018 LTS sarà il percorso di supporto migliore a lungo termine senza modifiche di rilievo in Unity o in MRTK.  La compilazione di Unity consigliata, per il precedente "Installa gli strumenti" è 2018.3 Unity, che diventerà la versione LTS di Unity 2018.  Inoltre, la v2 MRTK verrà sempre garantire il supporto per Unity 2018 LTS ma non necessariamente garantisce il supporto per ogni iterazione di Unity 2019.x. 

Per aiutare a chiarire le differenze aggiuntive tra Unity 2018.3.x o Unity 2019.1.x, seguente sono riportati i compromessi tra queste due versioni, con la differenza principale consiste nel significativo è la possibilità di compilare il codice per ARM64 in Unity 2019. 

Gli sviluppatori devono valutare eventuali [dipendenze di plug-in](https://docs.unity3d.com/Manual/Plugins.html) che attualmente esistenti nel progetto e se queste DLL possono essere compilate per ARM64. Se non è possibile creare un plug-in di dipendenza rigida per ARM64 uno sarà necessario usare Unity 2018 LTS.


| Unity 2018.3.x | Unity 2019.1 + |
|----------|-------------------|
| Supporto per build ARM32 | ARM64 e ARM32 supporto per la compilazione |
| LTS stabile build di rilascio | Stabilità Beta |
| [Back-end .NET di scripting](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *deprecato* | [Back-end .NET di scripting](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *rimosso* |
| Rete UNET *deprecato* | Rete UNET *rimosso* |

## <a name="update-sceneproject-settings-in-unity"></a>Aggiornare le impostazioni di scena o di un progetto in Unity

Dopo l'aggiornamento a Unity 2018.3.x o Unity 2019 +, è consigliabile aggiornare le impostazioni particolare in Unity per risultati ottimali nel dispositivo. Queste impostazioni sono descritte dettagliatamente nella sezione  **[le impostazioni consigliate per Unity](Recommended-settings-for-Unity.md)** .

Deve essere nuovamente iterato che il [back-end .NET di Scripting](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) deprecato in Unity 2018 e *rimosso* in Unity 2019 e di conseguenza, gli sviluppatori devono decisamente considerare di passando il progetto a [ IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). 

> [!NOTE]
> Scripting IL2CPP back-end può causare tempi di compilazione da Unity a Visual Studio e pertanto gli sviluppatori devono configurare i computer di sviluppo per [ottimizzazione dei tempi di compilazione IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> Inoltre, potrebbe essere utile per l'installazione una [Server di Cache](https://docs.unity3d.com/Manual/CacheServer.html), soprattutto per i progetti Unity con una grande quantità di risorse (esclusi i file di script) o costantemente modifica assets/scenes. Quando si apre un progetto, Unity idonei gli asset vengono archiviati in un formato della cache interna sul computer per lo sviluppo. Elementi devono essere nuovamente importati e quindi elaborati nuovamente quando modificare. Questo processo può essere eseguito una volta e salvato in un Server Cache e, di conseguenza, condivisi con altri sviluppatori di risparmiare tempo, invece di tutti gli sviluppatori di importare di nuovo di nuove modifiche in locale di elaborazione.

Dopo aver risolto eventuali modifiche di rilievo dopo lo spostamento alla versione aggiornata di Unity, gli sviluppatori devono compilare e testare le proprie App in HoloLens corrente (dal 1 ° generazione). Inoltre, questo è un buon punto per creare e salvare un commit per il controllo del codice sorgente. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilare le dipendenze/plug-in per il processore ARM

HoloLens (dal 1 ° generazione) eseguite applicazioni su x86 processore mentre il nuovo dispositivo HoloLens 2 Usa un processore ARM. Di conseguenza, le applicazioni esistenti devono essere trasferita in per il supporto ARM. Come indicato in precedenza, 2018 Unity supporta la compilazione per le app ARM32 mentre Unity 2019 + supporta la compilazione per le app ARM64. Lo sviluppo per le applicazioni ARM64 è in genere preferibile in quanto non esiste una differenza nelle prestazioni sostanziale. Tuttavia, ciò richiede che tutti i [dipendenze di plug-in](https://docs.unity3d.com/Manual/Plugins.html) anche da compilare per ARM64. 

Attualmente, esaminare tutte le dipendenze DLL dell'applicazione. Se una dipendenza non è più necessario, è consigliabile rimuoverlo dal progetto. I plug-in rimanenti che sono necessari, inserire i rispettivi file binari ARM32 o ARM64 nel progetto Unity. 

Dopo aver inserito le DLL pertinenti, compilare una soluzione di Visual Studio da Unity e quindi compilare un AppX per ARM in Visual Studio per verificare che l'applicazione può essere compilata per processori ARM. Questo altro punto in cui si consiglia di salvare un commit all'interno della soluzione di controllo di origine. 

## <a name="update-to-mrtk-version-2"></a>Aggiornamento alla versione 2 MRTK

MRTK versione 2 è il nuovo toolkit nella parte superiore di Unity che supportano entrambi HoloLens (dal 1 ° generazione) e 2 di HoloLens, e in cui tutte le nuove funzionalità di HoloLens 2 sono state aggiunte, ad esempio fornire interazioni e dell'occhio rilevamento.

### <a name="prepare-for-the-migration"></a>Preparare la migrazione

Prima dell'inserimento di nuove [*.unitypackage file per la versione v2 MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), è consigliabile eseguire un inventario di **1) qualsiasi codice personalizzato che si integra con MRTK v1** e **2) qualsiasi codice personalizzato per le interazioni di input o i componenti dell'esperienza utente**. Conflitto più diffuso e comune per uno sviluppatore di realtà mista l'inserimento di nuovo v2 MRTK comporterà input e le interazioni. In questo modo, si consiglia di iniziare la lettura e la comprensione di [modello di input v2 MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Infine, la nuova v2 MRTK è passata da un modello di script e gli oggetti nella scena manager a una configurazione e l'architettura del provider di servizi. Ciò comporta un modello di gerarchia e l'architettura scene più chiaro ma richiede una curva di apprendimento per comprendere i nuovi profili di configurazione. In questo modo, leggere il [Guida alla configurazione di Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) opportuno acquisire familiarità con le impostazioni importanti e i profili per adattarti alle esigenze dell'applicazione. 

### <a name="perform-the-migration"></a>Eseguire la migrazione

Dopo aver importato MRTK v2, di un progetto Unity avrà probabilmente molti errori relativi al compilatore. Si tratta in genere a causa la nuova struttura di spazio dei nomi e i nuovi nomi di componente. Procedere a risolvere questi errori modificando gli script per i nuovi spazi dei nomi e i componenti. 

Per altre informazioni sulle differenze tra HTK/MRTK e MRTK versione 2 la specifiche API, vedere la Guida al porting sul [MRTK versione 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Procedure consigliate

- Preferisce l'uso dello shader MRTK Standard
- Operazioni su una sostanziale comportano la modifica tipo alla volta (ad esempio: IFocusable a IMixedRealityFocusHandler)
- Test dopo ogni modifica e usare il codice sorgente
- Utilizza impostazioni predefinite MRTK UX (pulsanti, Slate e così via) quando possibile
- Provare a evitare di modificare direttamente i file MRTK, invece di creare wrapper che racchiudono i componenti MRTK
    - Ciò costituisce una protezione contro gli aggiornamenti e ingestions MRTK future
- Esaminare ed esplorare le scene di esempio fornite in MRTK (soprattutto *HandInteractionExamples.scene*)
- Ricompilare invece dell'interfaccia utente basata su canvas con quadrati, colliders e testo TextMeshPro

### <a name="testing-your-application"></a>Test dell'applicazione

Ora che HoloLens 2 componenti e le funzionalità sono disponibili nella versione 2, MRTK partire [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1), è possibile simulare le interazioni disponibili direttamente in Unity e sviluppare in base a nuove API per le interazioni di mano e sotto controllo di rilevamento.  Il dispositivo HoloLens 2 è necessario per creare un'esperienza ottimale, ma almeno uno è stato possibile avviare learning negli strumenti e documentazione. Inoltre, MRTK v2 supporta lo sviluppo in HoloLens (dal 1 ° generazione) e di conseguenza, i modelli di input tradizionali, ad esempio select tramite indice puntato possono comunque essere testate nel HoloLens (dal 1 ° generazione) i dispositivi. 

## <a name="updating-interaction-model-for-hololens-2"></a>L'aggiornamento del modello di interazione per HoloLens 2

Dopo aver creato l'app trasferite e averla preparata per HoloLens 2, si è pronti a prendere in considerazione l'interazione tra modello ologrammi progettazioni/il posizionamento e di aggiornamento.
Provenienti da HoloLens (dal 1 ° generazione), probabile che l'app ha un modello di interazione sguardo ed eseguire il commit, con vntana relativamente a portata di mano per rientrare nel campo di visualizzazione.

Passaggi per aggiornare la progettazione di app per costituire la scelta migliore per HoloLens 2:
1.  Componenti MRTK: Per le operazioni preliminari, se è stato aggiunto MRTK v2, sono disponibili vari componenti/script per sfruttare che sono stati progettati e ottimizzati per HoloLens 2.

2.  Modello di interazione: È consigliabile aggiornare il modello di interazione.  Per la maggior parte degli scenari, è consigliabile passare da sguardo ed eseguire il commit per mani.  Con la vntana esaurita in genere arms raggiungere, passando al mani verrà comportare rays puntamento interazione estrema e scarica i movimenti.
Nota: esistono scenari in cui un modello di interazione invisibile all'utente viene richiesto, ad esempio un ruolo di lavoro di attività che contiene gli strumenti e indicazioni di progettazione specifiche per questi casi è. 

3.  Posizionamento di ologramma: Dopo il passaggio a un modello di interazione tra le mani, provare a spostare alcuni vntana più vicini per interagire direttamente con il vntana con le mani, usando in prossimità di movimenti di quadratini di ridimensionamento di interazione.  I tipi di vntana consigliata spostare più vicino ottenere direttamente o interagire sono i menu di destinazione di dimensioni ridotte, controlli, i pulsanti e vntana più piccoli che rientrano in 2 HoloLens campo visivo quando selezionandola e controllando l'ologramma.
<br>
Ogni scenario e l'app è diverso e continueremo a perfezionare e registrare progettazione indicazioni in base al feedback e continuato procedurali.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>Informazioni aggiuntive ottenute dallo spostamento delle app da x86 a ARM

- Le app Unity semplici sono semplici come è possibile generare un bundle appx ARM o distribuire direttamente nel dispositivo ed è in esecuzione.
Il problema si verifica quando l'app Unity Usa plug-in nativi.  Tutti i plug-in native devono essere aggiornati a Visual Studio 2017 e ricompilati per ARM e con Unity 2019, ARM64.

- Un'app, utilizzare il plug-in AudioKinetic Wwise per Unity e la versione usata non è stata un plug-in UWP ARM. Sono necessari diversi giorni per funzionare nuovamente il suono nell'applicazione per lavorare su ARM.

- In altri casi, un plug-in UWP/ARM può non esistere per plug-in è necessaria un'app, che impediscono la porta ed eseguire in 2 HoloLens.  Coinvolgimento con il provider di plug-in può essere necessario per sbloccare e supporto ARM.

- Lo minfloat (varianti, ad esempio min16float minint, e così via) in e gli shader possono comportarsi in modo diverso in 2 HoloLen rispetto a su HoloLens (dal 1 ° generazione). In particolare, si garantisce che per "almeno il numero di bit verrà usato". In Intel/GPU NVIDIA, tali valori vengono considerati in larga misura solo 32 bit. In ARM, il numero di bit specificato in realtà viene rispettato. Che significa che in pratica, questi numeri possono avere minore precisione o di un intervallo in 2 HoloLens rispetto a quanto succede HoloLens (dal 1 ° generazione).

- Le istruzioni di ASM non sembrano funzionare su ARM, pertanto qualsiasi codice con istruzioni ASM dovrà essere riscritta.

- Il set di istruzioni SIMD non è supportato su ARM. Ciò significa varie intestazioni, ad esempio xmmintrin, emmintrin, tmmintrin.h e immintrin. h non sono disponibili su ARM.

- Il compilatore dello shader in ARM viene eseguito durante la prima chiamata di disegno dopo lo shader è stato caricato o qualcosa di shader si basa su è cambiato, non in fase di caricamento dello shader. L'impatto sulla frequenza dei fotogrammi può essere notevole, a seconda del modo in cui molti shader devono essere compilate. Ciò ha diverse implicazioni per come shader devono essere gestite o incluso nel pacchetto/aggiornato in modo diverso in Visual Studio 2 HoloLens HoloLens (dal 1 ° generazione).

## <a name="see-also"></a>Vedere anche
* [Guida introduttiva a MRTK versione 2](mrtk-getting-started.md)
* [MRTK versione 2 HowTo](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [Installare gli strumenti](install-the-tools.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md)

