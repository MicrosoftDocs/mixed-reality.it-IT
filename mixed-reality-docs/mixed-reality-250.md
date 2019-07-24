---
title: MR sharing 250-HoloLens e auricolari immersivi
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio, HoloLens e gli auricolari per la realtà mista di Windows per apprendere i dettagli della condivisione degli ologrammi tra i dispositivi a realtà mista.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, immersive, Motion controller, condivisione, Xbox Controller, rete, dispositivo incrociato
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63506110"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR sharing 250: HoloLens e auricolari immersivi

Con la flessibilità di piattaforma UWP (Universal Windows Platform) (UWP), è facile creare un'applicazione che si estende su più dispositivi. Grazie a questa flessibilità, possiamo creare esperienze che sfruttano i punti di forza di ogni dispositivo. In questa esercitazione verrà illustrata un'esperienza condivisa di base che viene eseguita sia in HoloLens che in modalità mista di Windows. Questo contenuto è stato originariamente fornito alla conferenza Microsoft Build 2017 a Seattle, WA.

**In questa esercitazione verrà:**

* Configurare una rete usando UNET.
* Condividere gli ologrammi tra i dispositivi a realtà mista.
* Definire una visualizzazione diversa dell'applicazione a seconda del dispositivo di realtà mista utilizzato.
* Crea un'esperienza condivisa in cui gli utenti di HoloLens guidano gli utenti con auricolari immersivi attraverso alcuni semplici puzzle.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>MR sharing 250: HoloLens e auricolari immersivi</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 con gli [strumenti di sviluppo necessari](install-the-tools.md) e [configurato per il supporto di una cuffia a realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Controller Xbox che funziona con il PC.
* Almeno un dispositivo HoloLens e un headset immersivo.
* Rete che consente la trasmissione UDP per l'individuazione.

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/MixedReality250/archive/master.zip) richiesti dal progetto. Estrarre i file in un percorso facile da ricordare.
* Questo progetto richiede [una versione consigliata di Unity con supporto della realtà mista di Windows](install-the-tools.md).

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capitolo 1-Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Obiettivi

Assicurarsi che l'ambiente di sviluppo sia pronto per l'uso con un progetto semplice.

### <a name="what-we-will-build"></a>Elementi da compilare

Un'applicazione che mostra un ologramma in HoloLens o in un headset a realtà mista di Windows.

### <a name="steps"></a>Passaggi
* Aprire Unity.
    * Selezionare **Apri**.
    * Passare alla posizione in cui sono stati estratti i file di progetto.
    * Fare clic su **Seleziona cartella**.
    * *L'elaborazione del progetto da parte di Unity verrà eseguita per la prima volta.*
* Verificare che la realtà mista sia abilitata in Unity.
    * Aprire la finestra di dialogo Impostazioni di compilazione (**CTRL + MAIUSC + B** o **file > impostazioni di compilazione...** ).
    * Selezionare **piattaforma UWP (Universal Windows Platform)** quindi fare clic su **Cambia piattaforma**.
    * Selezionare **Modifica impostazioni lettore >** .
    * Nel pannello **Inspector** sul lato destro, espandere **XR Settings**.
    * Controllare la casella **Virtual Reality supported** .
    * *La realtà mista di Windows dovrebbe essere Virtual Reality SDK.*
* Creare una scena.
    * Nella **gerarchia** fare clic su **fotocamera principale** Selezionare **Elimina**.
    * Da **HoloToolkit > Input >** i prefabbricati trascinano **MixedRealityCameraParent** nella **gerarchia**.
* Aggiungere ologrammi alla scena
    * Da **AppPrefabs** trascinare **SKYBOX** nella **visualizzazione scena**.
    * Da **AppPrefabs** trascinare i **Manager** alla **gerarchia**.
    * Da **AppPrefabs** trascinare l' **isola** nella **gerarchia**.
* Salva e compila
    * Salva ( **CTRL + S** o **file > Salva scena**)
    * Poiché si tratta di una nuova scena, è necessario assegnarle un nome. Il nome non è rilevante, ma viene usato SharedMixedReality.
* Esporta in Visual Studio
    * Aprire il menu Compila (**CTRL + MAIUSC + B** o **file > impostazioni di compilazione**)
    * Fare clic su **Aggiungi scene aperte.**
    * Verifica **progetti C# Unity**
    * Fai clic su **Compila**.
    * Nella finestra Esplora file visualizzata creare una nuova cartella denominata **app**.
    * Fare clic sulla cartella dell' **app** .
    * Premere **Seleziona cartella.**
    * **Attendi il completamento della compilazione**
    * Nella finestra Esplora file visualizzata passare alla cartella **app** .
    * Fare doppio clic su **SharedMixedReality. sln** per avviare Visual Studio
* Compilazione da Visual Studio
    * Utilizzando la barra degli strumenti superiore modificare destinazione per **rilasciare** e **x86**.
    * Fare clic sulla freccia accanto a **computer locale** e selezionare il **dispositivo** da distribuire in HoloLens
    * Fare clic sulla freccia accanto a **dispositivo** e selezionare **computer locale** per eseguire la distribuzione per l'auricolare della realtà mista.
    * Fare clic su **debug-> avvia senza eseguire debug** o **CTRL + F5** per avviare l'applicazione.

### <a name="digging-into-the-code"></a>Ricerche nel codice

Nel pannello del progetto passare a **Assets\HoloToolkit\Input\Scripts\Utilities** e fare doppio clic su **MixedRealityCameraManager.cs** per aprirlo.

**Panoramica** MixedRealityCameraManager.cs è un semplice script che regola il livello di qualità e le impostazioni di sfondo in base al dispositivo. La chiave è HolographicSettings. IsDisplayOpaque, che consente a uno script di rilevare se il dispositivo è un HoloLens (IsDisplayOpaque restituisce false) o un auricolare immersivo (IsDisplayOpaque restituisce true).

### <a name="enjoy-your-progress"></a>Scopri lo stato di avanzamento

A questo punto, l'applicazione eseguirà semplicemente il rendering di un ologramma. L'interazione con l'ologramma viene aggiunta in un secondo momento. Entrambi i dispositivi eseguiranno il rendering dell'ologramma. L'auricolare immersivo eseguirà anche il rendering di un cielo blu e di uno sfondo cloud.

## <a name="chapter-2---interaction"></a>Capitolo 2-interazione

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Obiettivi

Mostra come gestire l'input per un'applicazione di realtà mista di Windows.

### <a name="what-we-will-build"></a>Elementi da compilare

Basandosi sull'applicazione del capitolo 1, si aggiungeranno funzionalità per consentire all'utente di prelevare l'ologramma e posizionarlo in una superficie reale in HoloLens o in una tabella virtuale in un auricolare immersivo.

**Aggiornamento dell'input:** In HoloLens il gesto di selezione è il **tocco d'aria**. Negli auricolari immersivi viene usato il pulsante **a** del controller Xbox. Per ulteriori informazioni sull'input, [iniziare da qui](gestures.md).

### <a name="steps"></a>Passaggi
* Aggiunta di gestione input
    * Da **HoloToolkit > Input >** i prefabbricati trascinano **InputManager** nella **gerarchia** come figlio dei **responsabili**.
    * Da **HoloToolkit > Input > Prefabbricati >** cursore **di** trascinamento cursore alla **gerarchia**.
* Aggiungi mapping spaziale
    * Da **HoloToolkit > SpatialMapping >** i prefabbricati trascinano **SpatialMapping** nella **gerarchia**.
* Aggiungi playspace virtuale
    * In **gerarchia** Espandi **MixedRealityCameraParent** Selezionare **limite**
    * Nel pannello **Inspector** selezionare la casella per abilitare il **limite**
    * Da **AppPrefabs** trascinare **VRRoom** in **gerarchia**.
* Aggiungi WorldAnchorManager
    * In **gerarchia**selezionare **Manager**.
    * In **Inspector**fare clic su **Add Component**.
    * Digitare **World Anchor Manager**.
    * Selezionare **World Anchor Manager** per aggiungerlo.
* Aggiungere TapToPlace all'isola
    * In **gerarchia**espandere **isola**.
    * Selezionare **MixedRealityLand**.
    * In **Inspector**fare clic su **Add Component**.
    * Digitare **Tap per posizionarlo** e selezionarlo.
    * Controllare la **posizione dell'elemento padre al tocco**.
    * Imposta **offset selezione host** su **(0, 0,1, 0)** .
* Salva e compila come prima

### <a name="digging-into-the-code"></a>Ricerche nel codice

**Script 1-GamepadInput.cs**

Nel pannello del progetto passare a **Assets\HoloToolkit\Input\Scripts\InputSources** e fare doppio clic su **GamepadInput.cs** per aprirlo. Dallo stesso percorso nel pannello del progetto, fare doppio clic su **InteractionSourceInputSource.cs**.

Si noti che entrambi gli script hanno una classe base comune, BaseInputSource.

BaseInputSource mantiene un riferimento a un InputManager, che consente a uno script di attivare gli eventi. In questo caso, l'evento InputClicked è pertinente. Questo aspetto è importante da ricordare quando si arriva allo script 2, TapToPlace. Nel caso di GamePadInput, viene eseguito il polling del pulsante a del controller da premere, quindi viene generato l'evento InputClicked. Nel caso di InteractionSourceInputSource, viene generato l'evento InputClicked in risposta a TappedEvent.

**Script 2-TapToPlace.cs**

Nel pannello del progetto passare a **Assets\HoloToolkit\SpatialMapping\Scripts** e fare doppio clic su **TapToPlace.cs** per aprirlo.

La prima cosa che molti sviluppatori vogliono implementare quando si crea un'applicazione olografica consiste nello trasferire gli ologrammi con input di movimento. Di conseguenza, abbiamo cercato di commentare questo script in modo approfondito. Per questa esercitazione è opportuno evidenziare alcuni aspetti.

Si noti prima di tutto che TapToPlace implementa IInputClickHandler. IInputClickHandler espone le funzioni che gestiscono l'evento InputClicked generato da GamePadInput.cs o InteractionSourceInputSource.cs. OnInputClicked viene chiamato quando un BaseInputSource rileva un clic mentre l'oggetto con TapToPlace si trova nello stato attivo. L'evento viene attivato in HoloLens o premendo il pulsante a del controller Xbox.

In secondo luogo, il codice deve essere eseguito in Update per verificare se è in corso l'aspetto di una superficie, in modo da poter posizionare l'oggetto gioco su una superficie, ad esempio una tabella. L'auricolare immersivo non ha un concetto di superficie reale, quindi l'oggetto che rappresenta la tabella Top (Vroom > TableThingy > Cube) è stato contrassegnato con il livello di fisica SpatialMapping, quindi il cast del raggio in Update entrerà in conflitto con la tabella virtuale top.

### <a name="enjoy-your-progress"></a>Scopri lo stato di avanzamento

Questa volta è possibile selezionare l'isola per spostarla. In HoloLens è possibile spostare l'isola in una superficie reale. Nel dispositivo headset immersivo è possibile spostare l'isola nella tabella virtuale aggiunta.

## <a name="chapter-3---sharing"></a>Capitolo 3-condivisione

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Obiettivi

Verificare che la rete sia configurata correttamente e detaili la modalità di condivisione degli ancoraggi spaziali tra i dispositivi.

### <a name="what-we-will-build"></a>Elementi da compilare

Il progetto viene convertito in un progetto multiplayer. Si aggiungeranno l'interfaccia utente e la logica alle sessioni host o join. Gli utenti di HoloLens si vedranno reciprocamente nella sessione con i cloud sulle rispettive e gli utenti di auricolari immersivi hanno un cloud vicino a quello in cui si trova l'ancoraggio. Gli utenti degli auricolari immersivi vedranno gli utenti di HoloLens relativi all'origine della scena. Gli utenti di HoloLens vedranno l'ologramma dell'isola nella stessa posizione. Si noti che gli utenti negli auricolari immersivi non si troveranno nell'isola durante questo capitolo, ma si comporteranno in modo molto simile a HoloLens, con una vista degli uccelli dell'isola.

### <a name="steps"></a>Passaggi
* Rimuovi isola e VRRoom
    * In **gerarchia** fare clic con il pulsante destro del mouse su **isola** Selezionare **Elimina**
    * In **gerarchia** fare clic con il pulsante destro del mouse su **VRRoom** Selezionare **Elimina**
* Aggiungi usland
    * Da **AppPrefabs** trascinare **usland** in **gerarchia**.
* Da **AppPrefabs** trascinare ognuno dei seguenti elementi nella **gerarchia**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Salva e compila come prima

### <a name="digging-into-the-code"></a>Ricerche nel codice

Nel pannello del progetto passare a **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** e fare doppio clic su **UnetAnchorManager.cs**. La possibilità per un HoloLens di condividere le informazioni di rilevamento con un altro HoloLens, in modo che entrambi i dispositivi possano condividere lo stesso spazio è quasi magico. La potenza della realtà mista è attiva quando due o più persone possono collaborare usando gli stessi dati digitali.

Ecco alcuni aspetti da evidenziare in questo script:

Nella funzione Start si noti il controllo **IsDisplayOpaque**. In questo caso, si Finge che l'ancoraggio venga stabilito. Questo perché gli auricolari immersivi non espongono un modo per importare o esportare ancoraggi. Se viene eseguito in un HoloLens, tuttavia, questo script implementa gli ancoraggi di condivisione tra i dispositivi. Il dispositivo che avvia la sessione creerà un ancoraggio per l'esportazione. Il dispositivo che partecipa a una sessione richiede l'ancoraggio dal dispositivo che ha avviato la sessione.

**Esportazione**

Quando un utente crea una sessione, NetworkDiscoveryWithAnchors chiamerà la funzione UNETAnchorManagers CreateAnchor. Seguiamo il flusso CreateAnchor.

Si inizia con alcune pulizie, cancellando tutti i dati che potrebbero essere stati raccolti per gli ancoraggi precedenti. Viene quindi verificato se è presente un ancoraggio memorizzato nella cache da caricare. I dati di ancoraggio tendono a essere compresi tra 5 e 20 MB, quindi il riutilizzo degli ancoraggi memorizzati nella cache può ridurre la quantità di dati necessari per il trasferimento in rete. Vedremo come funziona un po' più tardi. Anche se si sta riutilizzando l'ancoraggio, è necessario che i dati di ancoraggio siano pronti nel caso in cui un nuovo client si unisca senza l'ancoraggio.

Parlando di ottenere i dati di ancoraggio pronti, la classe WorldAnchorTransferBatch espone la funzionalità per preparare i dati di ancoraggio per l'invio a un altro dispositivo o applicazione e la funzionalità per importare i dati di ancoraggio. Poiché il percorso di esportazione è in corso, si aggiungerà l'ancoraggio a WorldAnchorTransferBatch e si chiamerà la funzione ExportAsync. ExportAsync chiamerà quindi il callback WriteBuffer mentre genera i dati per l'esportazione. Quando tutti i dati sono stati esportati, viene chiamato ExportComplete. In WriteBuffer il blocco di dati viene aggiunto a un elenco che viene mantenuto per l'esportazione. In ExportComplete l'elenco viene convertito in una matrice. Viene anche impostata la variabile anchorName, che attiverà altri dispositivi per richiedere l'ancoraggio se non è disponibile.

In alcuni casi l'ancoraggio non viene esportato o creerà così pochi dati che verranno riprovati. Qui è sufficiente chiamare di nuovo CreateAnchor.

Una funzione finale nel percorso di esportazione è AnchorFoundRemotely. Quando un altro dispositivo trova l'ancoraggio, il dispositivo lo dirà all'host e l'host lo userà come segnale che l'ancoraggio è un "ancoraggio positivo" e può essere memorizzato nella cache.

**Importazione**

Quando un HoloLens viene unito a una sessione, deve importare un ancoraggio. Nella funzione Update di UNETAnchorManager viene eseguito il polling di anchorName. Quando il nome dell'ancoraggio viene modificato, inizia il processo di importazione. Prima di tutto, si tenta di caricare l'ancoraggio con il nome specificato dall'archivio di ancoraggio locale. Se è già presente, è possibile usarlo senza scaricare di nuovo i dati. Se non è disponibile, viene chiamato WaitForAnchor che avvierà il download.

Al termine del download, viene chiamato NetworkTransmitter_dataReadyEvent. Il ciclo di aggiornamento verrà segnalato per chiamare ImportAsync con i dati scaricati. ImportAsync chiamerà ImportComplete al termine del processo di importazione. Se l'importazione ha esito positivo, l'ancoraggio verrà salvato nell'archivio locale del lettore. PlayerController.cs esegue effettivamente la chiamata a AnchorFoundRemotely per consentire all'host di sapere che è stato stabilito un ancoraggio valido.

### <a name="enjoy-your-progress"></a>Scopri lo stato di avanzamento

Questa volta un utente con un HoloLens ospiterà una sessione usando il pulsante **Avvia sessione** nell'interfaccia utente. Gli altri utenti, sia su HoloLens che su un headset immersivo, selezionano la sessione e quindi selezionano il pulsante **Unisci sessione** nell'interfaccia utente. Se sono presenti più persone con dispositivi HoloLens, avranno i cloud rossi sulle rispettive teste. Ci sarà anche un cloud blu per ogni auricolare immersiva, ma i cloud blu non saranno sopra gli auricolari, perché gli auricolari non tentano di trovare lo stesso spazio delle coordinate globali dei dispositivi HoloLens.

Questo punto del progetto è un'applicazione di condivisione contenuta; non esegue molte operazioni e può fungere da baseline. Nei prossimi capitoli si inizierà a creare un'esperienza per gli utenti. Per altre indicazioni sulla progettazione dell'esperienza condivisa, vedere qui.

## <a name="chapter-4---immersion-and-teleporting"></a>Capitolo 4-immersione e Teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Obiettivi

Adatta l'esperienza a ogni tipo di dispositivo di realtà mista.

### <a name="what-we-will-build"></a>Elementi da compilare

L'applicazione viene aggiornata in modo da inserire utenti di auricolari immersivi nell'isola con una visualizzazione immersiva. Gli utenti di HoloLens avranno ancora la vista d'occhio dell'isola. Gli utenti di ogni tipo di dispositivo possono visualizzare altri utenti così come appaiono nel mondo. Ad esempio, gli utenti con auricolari immersivi possono visualizzare gli altri avatar su altri percorsi nell'isola e vedono gli utenti di HoloLens come cloud giganti sopra l'isola. Gli utenti di auricolari immersivi vedranno anche il cursore del raggio di sguardi dell'utente HoloLens se l'utente HoloLens sta esaminando l'isola. Gli utenti di HoloLens visualizzeranno un avatar nell'isola per rappresentare ogni utente di un headset immersivo.

**Input aggiornato per il dispositivo immersivo:**
* I pulsanti sinistro e destro del mouse sul controller Xbox ruotano il lettore
* Se si tiene premuto il pulsante Y sul controller Xbox, viene abilitato un cursore [Teleport](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) . Se il cursore ha un indicatore della freccia rotante quando si rilascia il pulsante Y, verrà avviata la teleportazione nella posizione del cursore.

### <a name="steps"></a>Passaggi
* Aggiungere MixedRealityTeleport a MixedRealityCameraParent
    * In **gerarchia**selezionare **usland**.
    * In **Inspector**, abilitare il **controllo del livello**.
    * In **gerarchia**selezionare **MixedRealityCameraParent**.
    * In **Inspector**fare clic su **Add Component**.
    * Digitare la **realtà mista Teleport** e selezionarla.

### <a name="digging-into-the-code"></a>Ricerche nel codice

Gli utenti con auricolari immersivi saranno collegati ai PC con un cavo, ma l'isola è più grande del cavo. Per compensare, è necessario avere la possibilità di spostare la fotocamera in modo indipendente dal movimento dell'utente. Per altre informazioni sulla progettazione di un'applicazione di realtà mista (in particolare movimento autonomo e locomozione), vedere la pagina relativa alla [comodità](comfort.md) .

Per descrivere questo processo, sarà utile definire due termini. Per prima  cosa, Dolly sarà l'oggetto che sposta la fotocamera in modo indipendente dall'utente. Un oggetto gioco figlio della **bambola** sarà la **fotocamera principale**. La videocamera principale è collegata alla testa dell'utente.

Nel pannello del progetto passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **MixedRealityTeleport.cs**.

MixedRealityTeleport ha due processi. In primo luogo, gestisce la rotazione usando i paraurti. Nella funzione Update viene eseguito il polling di ' ButtonUp ' in LeftBumper e RightBumper. GetButtonUp restituisce true solo sul primo frame un pulsante è attivo dopo essere stato disattivato. Se uno dei pulsanti è stato generato, è necessario che l'utente ruoti.

Quando si ruota, si esegue una dissolvenza e si dissolve l'uso di uno script semplice denominato "Fade Control". Questa operazione viene eseguita per impedire all'utente di vedere un movimento non naturale che può causare disagio. L'effetto di dissolvenza in entrata e in uscita è piuttosto semplice. Il quadrato nero è appeso davanti alla **fotocamera principale**. In caso di dissolvenza, il valore alfa viene sottoposto a transizione da 0 a 1. Questa operazione determina gradualmente il rendering dei pixel neri del quad e la relativa oscurità. Quando si esegue la dissolvenza, il valore alfa viene passato a zero.

Quando si calcola la rotazione, si noti che viene ruotata la nostra **bambola** , ma il calcolo della rotazione intorno alla **fotocamera principale**. Questo è importante perché la **fotocamera principale** è più lontana da 0, 0, 0, minore è la precisione di una rotazione intorno alla bambola, dal punto di vista dell'utente. Infatti, se non si ruota attorno alla posizione della fotocamera, l'utente si sposterà su un arco intorno alla **bambola** invece che sulla rotazione.

Il secondo processo per MixedRealityTeleport consiste nel gestire lo stato di **bambola**. Questa operazione viene eseguita in SetWorldPosition. SetWorldPosition prende la posizione del mondo desiderata, ovvero la posizione in cui l'utente desidera percepire che abitano. Dobbiamo inserire la nostra **bambola** in quella posizione, meno la posizione locale della **fotocamera principale**, in quanto tale offset verrà aggiunto a ogni frame.

Un secondo script chiama SetWorldPosition. Viene ora esaminato lo script. Nel pannello del progetto passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **TeleportScript.cs**.

Questo script è un po' più impegnativo rispetto a MixedRealityTeleport. Lo script sta controllando che il pulsante Y del controller Xbox venga mantenuto attivo. Mentre il pulsante è premuto, viene eseguito il rendering di un cursore Teleport e lo script esegue il cast di un raggio dalla posizione dello sguardo dell'utente. Se il raggio si scontra con una superficie che è più o meno rivolta verso l'alto, la superficie verrà considerata una superficie corretta per il teletrasporto e l'animazione sul cursore Teleport verrà abilitata. Se il raggio non entra in conflitto con una superficie più o meno rivolta verso l'alto, l'animazione sul cursore verrà disabilitata. Quando il pulsante Y viene rilasciato e il punto calcolato del raggio è una posizione valida, lo script chiama SetWorldPosition con la posizione in cui è intersecato il raggio.

### <a name="enjoy-your-progress"></a>Scopri lo stato di avanzamento

Questa volta è necessario trovare un amico.

Ancora una volta, un utente con il HoloLens ospiterà una sessione. Altri utenti faranno parte della sessione. L'applicazione inserisce i primi tre utenti in join da un auricolare immersivo in uno dei tre percorsi dell'isola. È possibile esplorare l'isola in questa sezione.

Dettagli da notare:
1. È possibile visualizzare i visi nei cloud, che consentono a un utente immerso di vedere quale direzione sta cercando un utente HoloLens.
2. Gli avatar nell'isola hanno colli che ruotano. Non seguiranno le operazioni che l'utente sta eseguendo è la realtà reale (queste informazioni non sono disponibili), ma è un'esperienza interessante.
3. Se l'utente HoloLens sta esaminando l'isola, gli utenti immersi possono visualizzarne il cursore.
4. I cloud che rappresentano gli utenti HoloLens hanno eseguito il cast delle ombreggiature.

## <a name="chapter-5---finale"></a>Capitolo 5-finali

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Obiettivi

Creare un'esperienza interattiva collaborativa tra i due tipi di dispositivi.

### <a name="what-we-will-build"></a>Elementi da compilare

Basandosi sul capitolo 4, quando un utente con una cuffia coinvolgente si avvicina a un rompicapo nell'isola, gli utenti di HoloLens otterranno una descrizione comando con un indizio sul puzzle. Una volta che tutti gli utenti di auricolari immersivi hanno superato i loro rompicapo e il "pad pronto" nella sala Rocket, il Rocket si avvierà.

### <a name="steps"></a>Passaggi
* In **gerarchia**selezionare **usland**.
* In controllo, in **controllo livello**, selezionare **Abilita collaborazione**.

### <a name="digging-into-the-code"></a>Ricerche nel codice

Esaminiamo ora LevelControl.cs. Questo script è il nucleo della logica del gioco e mantiene lo stato del gioco. Poiché si tratta di un gioco multiplayer che usa UNET è necessario comprendere in che modo i flussi di dati, almeno abbastanza bene per modificare questa esercitazione. Per una panoramica più completa di UNET, vedere la documentazione di Unity.

Nel pannello del progetto passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **LevelControl.cs**.

Viene ora illustrato come una cuffia immersiva indica che sono pronte per il lancio del Rocket. La preparazione del lancio Rocket viene comunicata impostando uno dei tre bool in un elenco di bool che corrispondono ai tre percorsi nell'isola. Il valore bool di un percorso verrà impostato quando l'utente assegnato al percorso si trova sopra il riquadro marrone all'interno della sala Rocket. Bene. ora i dettagli.

Si inizierà con la funzione Update (). Si noterà che è presente una funzione "cheat". Questa operazione è stata usata in fase di sviluppo per testare la sequenza di avvio e reimpostazione del Rocket. Non funzionerà nell'esperienza multiutente. Si spera che nel momento in cui si interiorizzano gli indici seguenti è possibile farlo funzionare. Dopo aver verificato se è necessario imbrogliare, viene verificato se il lettore locale è immerso. Vogliamo concentrarci sul modo in cui siamo in grado di raggiungere l'obiettivo. All'interno del controllo if (immerso) è presente una chiamata a CheckGoal nascosta dietro **EnableCollaboration** bool. Corrisponde alla casella di controllo selezionata durante il completamento dei passaggi per questo capitolo. All'interno di EnableCollaboration viene visualizzata una chiamata a CheckGoal ().

CheckGoal esegue alcuni calcoli matematici per verificare se il pad è più o meno in piedi. Quando ci troviamo, eseguiamo il debug. log "arrivato all'obiettivo" e chiamiamo "SendAtGoalMessage ()". In SendAtGoalMessage viene chiamato playerController. SendAtGoal. Per risparmiare tempo, ecco il codice seguente:

```cs
private void CmdSendAtGoal(int GoalIndex)
       {
           levelState.SetGoalIndex(GoalIndex);
       }
```

```cs
public void SendAtGoal(int GoalIndex)
       {
           if (isLocalPlayer)
           {
               Debug.Log("sending at goal " + GoalIndex);
               CmdSendAtGoal(GoalIndex);
           }
       }
```

Si noti che SendAtGoalMessage chiama CmdSendAtGoal, che chiama levelState. SetGoalIndex, che è di nuovo in LevelControl.cs. A prima vista, sembra strano. Perché non è sufficiente chiamare SetGoalIndex anziché questo strano routing tramite il controller del lettore? Il motivo è che è conforme al modello di dati usato da UNET per la sincronizzazione dei dati. Per evitare frodi e thrashing, UNET richiede che ogni oggetto disponga di un utente con l'autorità di modificare le variabili sincronizzate. Inoltre, solo l'host (l'utente che ha avviato la sessione) può modificare direttamente i dati. Gli utenti che non sono host, ma hanno l'autorità necessaria per inviare un "comando" all'host che modificherà la variabile. Per impostazione predefinita, l'host dispone di autorità su tutti gli oggetti, ad eccezione dell'oggetto generato per rappresentare l'utente. In questo caso l'oggetto ha lo script PlayerController. Esiste un modo per richiedere un'autorità per un oggetto e quindi apportare le modifiche, ma si sceglie di sfruttare il fatto che il controller del lettore dispone di autoauthority e indirizzare i comandi attraverso il controller del lettore.

Detto un altro modo, quando ci siamo trovati al nostro obiettivo, il giocatore deve indicare all'host che l'host ne dirà tutti gli altri.

Tornando a LevelControl.cs, vedere SetGoalIndex. Qui viene impostato il valore di un valore in un elenco di sincronizzazione (AtGoal). Si tenga presente che il contesto dell'host è in esecuzione. Analogamente a un comando, una RPC è un elemento che può essere emesso dall'host che farà sì che tutti i client eseguano il codice. Qui chiamiamo ' RpcCheckAllGoals '. Ogni client verificherà singolarmente se sono state impostate tutte e tre le AtGoals e, in caso affermativo, avvierà il Rocket.

### <a name="enjoy-your-progress"></a>Scopri lo stato di avanzamento

Per la compilazione nel capitolo precedente, la sessione viene avviata come prima. Questa volta, quando gli utenti nell'auricolare immersiva entrano nello "sportello" sul percorso, viene visualizzata una descrizione comando che solo gli utenti HoloLens possono vedere. Gli utenti di HoloLens sono responsabili della comunicazione di questo indizio agli utenti nell'auricolare immersiva. Il Rocket si avvierà allo spazio quando ogni avatar ha risalendo al Pad marrone corrispondente all'interno del vulcano. La scena viene reimpostata dopo 60 secondi, quindi è possibile eseguirla di nuovo.

## <a name="see-also"></a>Vedere anche
* [Input MR 213: Controller del movimento](mixed-reality-213.md)
