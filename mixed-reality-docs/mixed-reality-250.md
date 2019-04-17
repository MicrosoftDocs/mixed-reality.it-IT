---
title: MR 250 - HoloLens e auricolari coinvolgenti di condivisione
description: Seguire questa procedura dettagliata sull'uso delle cuffie per Unity, Visual Studio, HoloLens e realtà mista di Windows per acquisire i dettagli di condivisione vntana tra dispositivi per realtà mista di codifica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, coinvolgenti, movimento controller, condivisione, controller xbox, reti, più dispositivi
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598043"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR Sharing 250: HoloLens e auricolari coinvolgenti

Con la flessibilità di Universal Windows Platform (UWP), è facile creare un'applicazione che si estende su più dispositivi. Con questa flessibilità, possiamo creare esperienze in grado di sfruttano le potenzialità di ogni dispositivo. Questa esercitazione verrà descritta una base condividere esperienze in esecuzione su auricolari coinvolgenti di HoloLens e realtà mista di Windows. Questo contenuto è stato originariamente fornito in occasione della conferenza Microsoft Build 2017 a Seattle, WA.

**In questa esercitazione si apprenderà come:**

* Configurare una rete usando UNET.
* Condividere vntana tra dispositivi per realtà mista.
* Stabilire una visualizzazione diversa dell'applicazione in base alla quale viene utilizzato il dispositivo di realtà mista.
* Creare un'esperienza condivisa in cui gli utenti di HoloLens guidano gli utenti auricolari immersive avvantaggiarsene semplice.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>MR Sharing 250: HoloLens e auricolari coinvolgenti</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 con il [strumenti di sviluppo necessari](install-the-tools.md) e [configurato per supportare un visore VR immersivi di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Un controller Xbox che funziona con il PC.
* Almeno un dispositivo HoloLens e uno visore VR immersivi.
* Una rete che consente di Broadcast di UDP per l'individuazione.

### <a name="project-files"></a>File di progetto

* Scaricare il [file](https://github.com/Microsoft/MixedReality250/archive/master.zip) necessarie per il progetto. Estrarre i file in un facile da ricordare di percorso.
* Questo progetto richiede la [una versione consigliata di Unity con il supporto di realtà mista di Windows](install-the-tools.md).

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capitolo 1 - Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Obiettivi

Assicurarsi che l'ambiente di sviluppo sia pronto per iniziare con un progetto semplice.

### <a name="what-we-will-build"></a>Che cosa verrà compilata

Un'applicazione che mostra un ologrammi su HoloLens o un visore VR immersivi di realtà mista di Windows.

### <a name="steps"></a>Passaggi
* Aprire Unity.
    * Selezionare **aperto**.
    * Passare a dove sono stati estratti i file di progetto.
    * Fare clic su **Seleziona cartella**.
    * *Richiederà un po' mentre per Unity elaborare la prima volta che il progetto.*
* Verificare che in Unity sia abilitato realtà mista.
    * Aprire la finestra di dialogo Impostazioni di compilazione (**CTRL + MAIUSC + B** o **File > Build Settings...** ).
    * Selezionare **Universal Windows Platform** quindi fare clic su **commutatore piattaforma**.
    * Selezionare **Modifica > impostazioni del lettore**.
    * Nel **Inspector** pannello sul lato destro, quindi espandere **XR impostazioni**.
    * Verificare i **supportato di realtà virtuale** casella.
    * *Realtà mista di Windows deve essere il SDK di realtà virtuale.*
* Creare una scena.
    * Nel **gerarchia** con il pulsante destro fare clic su **Main Camera** seleziona **Elimina**.
    * Dal **HoloToolkit > Input > Prefabs** trascinare **MixedRealityCameraParent** per il **gerarchia**.
* Aggiungere Vntana alla scena
    * Dal **AppPrefabs** trascinare **Skybox** per il **visualizzazione scena**.
    * Dal **AppPrefabs** trascinare **responsabili** per il **gerarchia**.
    * Dal **AppPrefabs** trascinare **isola** per il **gerarchia**.
* Salvare e compilare
    * Salvare (entrambe **controllo + S** oppure **File > Salva scena**)
    * Poiché si tratta di una nuova scena, è necessario assegnargli il nome. Nome non è rilevante, ma si utilizza SharedMixedReality.
* Esportare in Visual Studio
    * Aprire il menu di compilazione (**CTRL + MAIUSC + B** oppure **File > Build Settings**)
    * Fare clic su **aggiungere scene Open.**
    * Controllare **Unity C# progetti**
    * Fai clic su **Compila**.
    * Nella finestra di Esplora file che viene visualizzato, creare una nuova cartella denominata **App**.
    * Solo clic i **App** cartella.
    * Premere **Seleziona cartella.**
    * **Attendere il completamento della compilazione**
    * Nella finestra di Esplora file che viene visualizzato, esplorare il **App** cartella.
    * Fare doppio clic su **SharedMixedReality.sln** per avviare Visual Studio
* Compilazione da Visual Studio
    * La barra degli strumenti superiore Cambia destinazione per **Release** e **x86**.
    * Fare clic sulla freccia accanto a **computer locale** e selezionare **dispositivo** distribuire a HoloLens
    * Fare clic sulla freccia accanto a **periferica** e selezionare **computer locale** da distribuire per il visore VR realtà mista.
    * Fare clic su **Debug -> Avvia senza eseguire debug** oppure **CTRL + F5** per avviare l'applicazione.

### <a name="digging-into-the-code"></a>Il codice nei dettagli

Nel Pannello di progetto, passare a **Assets\HoloToolkit\Input\Scripts\Utilities** e fare doppio clic **MixedRealityCameraManager.cs** per aprirlo.

**Panoramica:** MixedRealityCameraManager.cs è uno script semplice che consente di regolare le impostazioni di sfondo e a livello di qualità in base al dispositivo. Chiave di seguito è riportato HolographicSettings.IsDisplayOpaque, che consente a uno script per rilevare se il dispositivo è un HoloLens (IsDisplayOpaque restituisce false) o un visore VR immersivi (IsDisplayOpaque restituisce true).

### <a name="enjoy-your-progress"></a>Sfrutta i vantaggi dello stato di avanzamento

A questo punto l'applicazione verrà semplicemente eseguito il rendering ologramma. In un secondo momento si aggiungerà l'interazione a di ologramma. Entrambi i dispositivi verranno eseguito il rendering di ologramma lo stesso. Il visore VR immersivi inoltre il rendering di uno sfondo blu sky e cloud.

## <a name="chapter-2---interaction"></a>Capitolo 2: interazione

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Obiettivi

Viene illustrato come gestire gli input per un'applicazione di realtà mista di Windows.

### <a name="what-we-will-build"></a>Che cosa verrà compilata

Compila l'applicazione dal capitolo 1, si aggiungeranno funzionalità per consentire all'utente di prelevare l'ologrammi e inserirlo in un'area del mondo reale in HoloLens o in una tabella virtuale in un visore VR immersivi.

**Input processo di aggiornamento:** Su HoloLens è il movimento di seleziona il **puntato**. In coinvolgenti auricolari, si userà il **oggetto** pulsante sul controller Xbox. Per altre informazioni sull'input [iniziare da qui](gestures.md).

### <a name="steps"></a>Passaggi
* Aggiungi il gestore di Input
    * Dal **HoloToolkit > Input > Prefabs** trascinare **InputManager** al **gerarchia** come elemento figlio **responsabili**.
    * Dal **HoloToolkit > Input > Prefabs > cursore** trascinare **cursore** al **gerarchia**.
* Aggiungi Mapping spaziale
    * Dal **HoloToolkit > SpatialMapping > Prefabs** trascinare **SpatialMapping** al **gerarchia**.
* Aggiungere Playspace virtuale
    * Nelle **gerarchia** espandere **MixedRealityCameraParent** selezionare **limite**
    * Nelle **Inspector** pannello selezionare la casella per abilitare **limite**
    * Dal **AppPrefabs** trascinare **VRRoom** al **gerarchia**.
* Add WorldAnchorManager
    * Nelle **gerarchia**, selezionare **responsabili**.
    * Nelle **Inspector**, fare clic su **Add Component**.
    * Tipo di **World ancoraggio Manager**.
    * Selezionare **World ancoraggio Manager** per aggiungerlo.
* Aggiungere TapToPlace all'isola di
    * Nelle **gerarchia**, espandere **isola**.
    * Selezionare **MixedRealityLand**.
    * Nelle **Inspector**, fare clic su **Add Component**.
    * Tipo di **toccare per posizione** e selezionarlo.
    * Controllare **posizionare padre al tocco**.
    * Impostare **Offset di posizionamento** al **(0, 0, 0,1)**.
* Salvare e compilare come indicato in precedenza

### <a name="digging-into-the-code"></a>Il codice nei dettagli

**1 - GamepadInput.cs lo script**

Nel pannello Progetto spostarsi **Assets\HoloToolkit\Input\Scripts\InputSources** e fare doppio clic **GamepadInput.cs** per aprirlo. Dallo stesso percorso nel Pannello di progetto, anche fare doppio clic **InteractionSourceInputSource.cs**.

Si noti che entrambi gli script hanno una classe di base comune, BaseInputSource.

BaseInputSource mantiene un riferimento a un InputManager, che consente a uno script per attivare gli eventi. In questo caso, l'evento InputClicked è rilevante. Questo è importante da ricordare quando si arriva alla script 2, TapToPlace. Nel caso di GamePadInput, si esegue il polling per il pulsante sul controller per la pressione, quindi viene generato l'evento InputClicked. Nel caso di InteractionSourceInputSource, generare l'evento InputClicked in risposta al TappedEvent.

**Script 2: TapToPlace.cs**

Nel pannello Progetto spostarsi **Assets\HoloToolkit\SpatialMapping\Scripts** e fare doppio clic **TapToPlace.cs** per aprirlo.

La prima cosa da molti sviluppatori di implementare quando si crea un'applicazione Holographic passerà Vntana con input di movimento. Di conseguenza, è stata endeavored commentare attentamente questo script. Alcune operazioni sono opportuno evidenziare per questa esercitazione.

In primo luogo, si noti che TapToPlace implementa IInputClickHandler. IInputClickHandler espone le funzioni che gestiscono l'evento InputClicked generato GamePadInput.cs o InteractionSourceInputSource.cs. OnInputClicked viene chiamato quando un BaseInputSource rileva un clic, mentre l'oggetto con TapToPlace è in stato attivo. Airtapping su HoloLens o premendo il pulsante sul controller Xbox attiverà l'evento.

In secondo luogo, se il codice verrà eseguito in update per verificare se un'area viene analizzata in modo che è possibile inserire l'oggetto gioco su una superficie, ad esempio una tabella. Il visore VR immersivi non hanno un concetto di superfici reali, pertanto, l'oggetto che rappresenta l'inizio di tabella (Vroom > TableThingy > cubo) è stato contrassegnato con il livello di fisica SpatialMapping, pertanto il raggio di eseguire il cast in aggiornamento entrerà in conflitto con la parte superiore di tabella virtuale.

### <a name="enjoy-your-progress"></a>Sfrutta i vantaggi dello stato di avanzamento

Questa volta è possibile selezionare l'isola per spostarlo. HoloLens è possibile spostare l'isola di in una superficie reale. Nel visore VR immersivi è possibile spostare l'isola per la tabella virtuale che è stata aggiunta.

## <a name="chapter-3---sharing"></a>Capitolo 3 - condivisione

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Obiettivi

Assicurarsi che la rete sia configurata correttamente e in dettaglio come ancoraggi spaziali vengono condivise tra i dispositivi.

### <a name="what-we-will-build"></a>Che cosa verrà compilata

Si convertirà il progetto a un progetto per più giocatori. Si aggiungerà dell'interfaccia utente e per la logica per le sessioni di host o join. HoloLens gli utenti vedranno tra loro nella sessione con cloud su mentalmente, e gli utenti visore VR immersivi nelle vicinanze in cui è il punto di ancoraggio cloud. Gli utenti di auricolari immersive visualizzeranno gli utenti di HoloLens relative all'origine della scena. Gli utenti di HoloLens verranno visualizzato l'ologrammi dell'isola di nella stessa posizione. È importante notare che gli utenti delle cuffie immersive potrebbe non essere isola durante questo capitolo, ma si comporterà in modo molto simile a HoloLens, con una visualizzazione aerea dell'isola di.

### <a name="steps"></a>Passaggi
* Rimuovi isola e VRRoom
    * Nelle **gerarchia** fare doppio clic su **isola** selezionare **Delete**
    * Nella **gerarchia** destro **VRRoom** selezionare **Delete**
* Aggiungere Usland
    * Dal **AppPrefabs** trascinare **Usland** al **gerarchia**.
* Dal **AppPrefabs** ognuna delle seguenti operazioni per trascinare **gerarchia**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Salvare e compilare come indicato in precedenza

### <a name="digging-into-the-code"></a>Il codice nei dettagli

Nel Pannello di progetto, passare a **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** e fare doppio clic su **UnetAnchorManager.cs**. La possibilità per uno HoloLens condividere le informazioni di rilevamento con HoloLens un altro modo che entrambi i dispositivi possono condividere lo stesso spazio è quasi magiche presenti. La potenza di realtà mista deriva attiva quando due o più persone possono collaborare con gli stessi dati digitali.

Alcuni aspetti da notare in questo script:

Nella funzione di avvio, si noti che la verifica della presenza **IsDisplayOpaque**. In questo caso, abbiamo fingendo che il punto di ancoraggio è stata stabilita. Questo avviene perché le cuffie coinvolgenti per non esporre un modo per importare o esportare gli ancoraggi. Se in esecuzione un HoloLens, tuttavia, questo script implementa gli ancoraggi condivisione tra i dispositivi. Il dispositivo che avvia la sessione verrà creato un ancoraggio per l'esportazione. Il dispositivo che partecipa a una sessione richiederà l'ancoraggio dal dispositivo che ha avviato la sessione.

**L'esportazione:**

Quando un utente crea una sessione, NetworkDiscoveryWithAnchors chiamerà UNETAnchorManagers CreateAnchor (funzione). È possibile seguire CreateAnchor flusso.

È innanzitutto necessario effettuare alcune attività di manutenzione, cancellare tutti i dati che si potrà avere raccolti i punti di ancoraggio precedente. Controlliamo quindi se non c'è un ancoraggio memorizzati nella cache da caricare. I dati di ancoraggio tendono a essere compreso tra 5 e 20 MB, in modo da riutilizzare gli ancoraggi memorizzato nella cache è possibile salvare sulla quantità di dati che ci servono per il trasferimento in rete. Si vedrà come funziona un po' più avanti. Anche se si sta riutilizzando il punto di ancoraggio, è necessario ottenere dati pronti nel caso in cui viene aggiunto un nuovo client che non hanno il punto di ancoraggio l'ancoraggio.

Parlando di preparazione dei dati di ancoraggio, la classe WorldAnchorTransferBatch espone la funzionalità per preparare i dati di ancoraggio per l'invio a un altro dispositivo o dell'applicazione e la funzionalità per importare i dati di ancoraggio. Poiché si usa il percorso di esportazione, verrà aggiunto il nostro ancoraggio per il WorldAnchorTransferBatch e chiamare la funzione ExportAsync. ExportAsync verrà quindi chiamato il callback WriteBuffer, in quanto genera i dati da esportare. Quando tutti i dati sono state esportate ExportComplete verrà chiamato. In WriteBuffer il blocco di dati viene aggiunto a un elenco che richiedono la conservazione per l'esportazione. In ExportComplete convertiamo l'elenco in una matrice. La variabile AnchorName è impostata per richiedere l'ancoraggio, se non si hanno che attivano altri dispositivi anche.

In alcuni casi il punto di ancoraggio non esporta o creerà così pochi dati che si eseguirà un nuovo tentativo. In questo caso è sufficiente chiamare CreateAnchor nuovamente.

Una funzione finale nel percorso di esportazione è AnchorFoundRemotely. Quando un altro dispositivo consente di trovare il punto di ancoraggio, tale dispositivo indicherà l'host e l'host che verrà utilizzato come un segnale che il punto di ancoraggio è un punto di ancoraggio valido"" e può essere memorizzati nella cache.

**L'importazione:**

Quando un HoloLens partecipa a una sessione, è necessario importare un ancoraggio. Nella funzione di aggiornamento del UNETAnchorManager, viene eseguito il polling di AnchorName. Quando viene modificato il nome dell'ancoraggio, inizia il processo di importazione. In primo luogo, si tenta di caricare il punto di ancoraggio con il nome specificato dall'archivio locale di ancoraggio. Se è già stato fatto, è possibile usarlo senza scaricare nuovamente i dati. Se è non disponibile, chiamiamo il metodo WaitForAnchor che avvierà il download.

Quando viene completato il download, viene chiamato NetworkTransmitter_dataReadyEvent. Ciò segnalerà il ciclo di aggiornamento per chiamare ImportAsync con i dati scaricati. ImportAsync chiamerà ImportComplete durante il processo di importazione è stato completato. Se l'importazione ha esito positivo, il punto di ancoraggio verrà salvato nell'archivio locale di Windows Media player. PlayerController.cs rende effettivamente la chiamata a AnchorFoundRemotely per informare l'host che un buon punto di ancoraggio è stata stabilita.

### <a name="enjoy-your-progress"></a>Sfrutta i vantaggi dello stato di avanzamento

Questa volta un utente con un HoloLens ospiterà una sessione utilizzando il **avviare la sessione** pulsante nell'interfaccia utente. Gli altri utenti, sia su HoloLens o un visore VR immersivi, verranno selezionare la sessione e quindi selezionare il **partecipare sessione** pulsante nell'interfaccia utente. Se si dispone di più utenti con dispositivi HoloLens, hanno cloud rosso su mentalmente. Ci sarà un cloud blu per ogni visore VR immersivi, ma i cloud blu non sarà sopra le cuffie, come le cuffie non siano tentando di trovare lo spazio delle coordinate world dei dispositivi HoloLens.

Questo punto il progetto è un'applicazione di condivisione indipendente; non esegue molte operazioni e potrebbe essere utilizzato come una linea di base. Nei capitoli successivi, si inizierà la creazione di un'esperienza per le persone a guardare. Per ottenere un'ulteriore materiale sussidiario sulla progettazione di condividere esperienze, fare clic qui.

## <a name="chapter-4---immersion-and-teleporting"></a>Capitolo 4 - full Immersion e teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Obiettivi

Soddisfa le esigenze dell'esperienza per ogni tipo di dispositivo di realtà mista.

### <a name="what-we-will-build"></a>Che cosa verrà compilata

Si aggiornerà l'applicazione per inserire gli utenti visore VR immersivi isola con una visualizzazione coinvolgente e concreto. HoloLens continueranno ad avere la vista aerea dell'isola. Gli utenti di ogni tipo di dispositivo possono visualizzare gli altri utenti come appaiono in tutto il mondo. Ad esempio, gli utenti visore VR immersivi possono vedere l'altro avatar in altri percorsi isola e vedono gli utenti di HoloLens come cloud di grandi dimensioni di sopra dell'isola. Visore VR immersivi il cursore di ray sguardo dell'utente HoloLens verrà inoltre visualizzato se l'utente di HoloLens sta guardando l'isola. Gli utenti di HoloLens visualizzeranno un avatar dell'isola per rappresentare ogni utente visore VR immersivi.

**Aggiornato Input per il dispositivo Immersive:**
* I pulsanti di chiusura e respingenti a destra a sinistra nel controller Xbox ruotare Windows Media player
* Tenendo premuto il pulsante Y sul controller Xbox consentirà una [teleport](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) cursore. Se il cursore è un indicatore rotante quando si rilascia il pulsante Y, si sarà teleported alla posizione del cursore.

### <a name="steps"></a>Passaggi
* Add MixedRealityTeleport to MixedRealityCameraParent
    * Nelle **gerarchia**, selezionare **Usland**.
    * Nelle **Inspector**, abilitare **a livello di controllo**.
    * Nelle **gerarchia**, selezionare **MixedRealityCameraParent**.
    * Nelle **Inspector**, fare clic su **Add Component**.
    * Tipo di **Teleport realtà mista** e selezionarlo.

### <a name="digging-into-the-code"></a>Il codice nei dettagli

Gli utenti visore VR immersivi sarà possibile con tethering i PC con un cavo, ma l'isola è maggiore di quanto è lungo il cavo. Per compensare la modifica, è necessario avere la possibilità di spostare la camera indipendentemente dal movimento dell'utente. Vedere le [pagina comfort](comfort.md) per altre informazioni sulla progettazione dell'applicazione di realtà mista (in particolare self movimento e locomotion).

Per descrivere questo processo sarà utile definire due termini. Prima di tutto **carrello** sarà l'oggetto che consente di spostare la fotocamera in modo indipendente da parte dell'utente. Un oggetto gioco figlio del **carrello** sarà il **fotocamera principale**. La fotocamera principale è collegata all'inizio dell'utente.

Nel Pannello di progetto, passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **MixedRealityTeleport.cs**.

MixedRealityTeleport ha due compiti. In primo luogo, che gestisce la rotazione usando paraurti. Nella funzione di aggiornamento è eseguire il polling per 'ButtonUp' LeftBumper e RightBumper. GetButtonUp restituisce true solo sul primo frame di che un pulsante è rilasciato dopo essere stata verso il basso. Se dei pulsanti fosse stato generato, quindi sappiamo che l'utente deve eseguire la rotazione.

Quando si ruota Microsoft un effetto di dissolvenza e usando uno script semplice denominato 'di dissolvenza controllo' di dissolvenza. È utile per impedire all'utente di visualizzare un movimento non naturale che potrebbe causare disturbo. L'effetto di dissolvenza in entrata e in uscita effetto è piuttosto semplice. Abbiamo un quadrato nero sporgenti davanti il **fotocamera principale**. Quando dissolvenza in uscita è passare il valore alfa da 0 a 1. In questo modo gradualmente i pixel neri del quadrato per eseguire il rendering e nascondere qualsiasi elemento su cui si basano. Quando a dissolvenza nella transizione il valore alfa su zero.

Quando si calcola la rotazione, tenere presente che si sta rotazione nostri **carrello** ma calcolando la rotazione intorno al **fotocamera principale**. Questo aspetto è importante come quanto più il **fotocamera principale** è lontano da 0, 0,0, meno precisa una rotazione intorno al carrello diventerebbe dal punto di vista dell'utente. In effetti, se non esegue alcuna rotazione intorno alla posizione della camera, l'utente passerà in un arco tutto il **carrello** anziché la rotazione.

Il secondo processo per MixedRealityTeleport consiste nel gestire lo spostamento di **carrello**. Questa operazione viene eseguita in SetWorldPosition. SetWorldPosition accetta la posizione globale desiderato, la posizione in cui l'utente desidera percieve che si occupino. È necessario inserire nostri **carrello** in tale posizione meno alla posizione locale del **fotocamera principale**, come offset verrà aggiunti ogni fotogramma.

Un secondo script chiama SetWorldPosition. Esaminiamo lo script. Nel Pannello di progetto, passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **TeleportScript.cs**.

Questo script è un po' più complesso del MixedRealityTeleport. Lo script controlla per il pulsante di Y sul controller Xbox venga mantenuto. Mentre è attivo il pulsante verso il basso un teleport viene eseguito il rendering di cursore e lo script esegue il cast di un raggio da posizione sguardo dell'utente. Se tale ray è in conflitto con un'area che è più o meno verso l'alto, l'area viene considerato una superficie di buon teleport a e l'animazione sul cursore teleport verrà abilitata. Se il raggio non entri in conflitto con una superficie maggiore o minore puntamento verso l'alto, quindi verrà disabilitata l'animazione sul cursore. Quando viene rilasciato il pulsante Y e il punto del raggio calcolato è una posizione valida, lo script chiama SetWorldPosition con la posizione del raggio intersecato.

### <a name="enjoy-your-progress"></a>Sfrutta i vantaggi dello stato di avanzamento

Questa volta è necessario trovare un amico.

Ancora una volta, un utente con il HoloLens ospiterà una sessione. Gli altri utenti verranno partecipare alla sessione. L'applicazione verrà posizionati i primi tre agli utenti di accedere da un visore VR immersivi su uno dei tre percorsi dell'isola. È possibile esplorare l'isola di questa sezione.

Dettagli da notare:
1. È possibile visualizzare i volti nel cloud, consentendo di un utente immerso vedere direzione in cui un utente di HoloLens è alla ricerca.
2. L'avatar dell'isola hanno necks che ruotano. Non seguono svolte l'utente è realtà reale (non abbiamo informazioni), ma rende un'interessante esperienza.
3. Se l'utente di HoloLens è esaminando l'isola, gli utenti immerso possono vedere il cursore.
4. I cloud che rappresentano gli utenti di HoloLens ombre.

## <a name="chapter-5---finale"></a>Capitolo 5 - Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Obiettivi

Creare un'esperienza interattiva di collaborazione tra i tipi di due dispositivi.

### <a name="what-we-will-build"></a>Che cosa verrà compilata

Compila il capitolo 4, quando un utente con un visore VR immersivi Ottiene quasi un puzzle isola, gli utenti di HoloLens otterrà una descrizione comando con un'indicazione del puzzle. Una volta nella chat room rocket tutti gli utenti visore VR immersivi ottenere oltre i quesiti e sul riquadro"pronto", verrà avviata la rocket.

### <a name="steps"></a>Passaggi
* Nelle **gerarchia**, selezionare **Usland**.
* Nella **Inspector**, nel **a livello di controllo**, controllare **abilitare collaborazione**.

### <a name="digging-into-the-code"></a>Il codice nei dettagli

Ora esaminiamo LevelControl.cs. Questo script costituisce il nucleo della logica del gioco e mantiene lo stato del gioco. Poiché si tratta di un gioco multiplayer con UNET dobbiamo comprendere il flusso dei dati, almeno così ben per modificare questa esercitazione. Per una panoramica più completa di UNET, consultare la documentazione di Unity.

Nel Pannello di progetto, passare a **Assets\AppPrefabs\Support\Scripts\GameLogic** e fare doppio clic su **LevelControl.cs**.

Ecco come un visore VR immersivi indica che essi sono pronti per il lancio di rocket. Preparazione avvio Rocket viene comunicato impostando uno dei tre bool in un elenco di bool che corrispondono ai tre percorsi dell'isola. Quando l'utente assegnato al percorso si trova sopra il riquadro marrone all'interno di chat room rocket verrà impostato bool del percorso. OK, ora per i dettagli.

Si inizierà nella funzione Update (). Si noti che vi sia una funzione 'cheat'. Abbiamo utilizzato questo nello sviluppo per testare il lancio di rocket e reimpostazione della sequenza. Non funzionerà nell'esperienza dell'utente con più. Si spera nel momento in cui che si acquisisce le informazioni seguenti è possibile utilizzarlo. Dopo che è possibile controllare se è opportuno cheat, controlliamo per vedere se è si è immersi il giocatore locale. Si vuole concentrare sul modo in cui troviamo che ci troviamo qui l'obiettivo. All'interno di if (si è immersi) controllare, è presente una chiamata a CheckGoal nascoste dietro la **EnableCollaboration** bool. Corrisponde alla casella di controllo che è stata selezionata durante il completamento dei passaggi di questo capitolo. All'interno di EnableCollaboration notiamo una chiamata a CheckGoal().

CheckGoal esegue alcuni calcoli matematici per vedere se siamo più o meno la condizione nel blocco note. Quando si sono, è debug. log "Arrivata all'obiettivo" e quindi chiamare 'SendAtGoalMessage()'. In SendAtGoalMessage chiamiamo playerController.SendAtGoal. Per risparmiare tempo, ecco il codice:

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

Si noti che SendAtGoalMessage chiama CmdSendAtGoal, quali levelState.SetGoalIndex chiamate, che viene ripristinato LevelControl.cs. A prima vista questa apparentemente anomalo. Perché non semplicemente chiamare SetGoalIndex anziché questo strano routing tramite il controller player? Il motivo è che si sta conforme al modello dati che UNET viene utilizzato per mantenere sincronizzati i dati. Per evitare comportamenti scorretti e thrashing, UNET richiede che ogni oggetto dispone di un utente che dispone dell'autorità di modificare le variabili sincronizzate. Inoltre, solo l'host (l'utente che ha avviato la sessione) può modificare i dati direttamente. Gli utenti che non sono host, ma dispongono di autorità, è necessario inviare un 'command' nell'host e modificare la variabile. Per impostazione predefinita l'host ha autorità su tutti gli oggetti, a eccezione dell'oggetto generato per rappresentare l'utente. In questo caso l'oggetto con lo script playercontroller. È possibile richiedere l'autorità per un oggetto e quindi apportare le modifiche, ma si sceglie di sfruttare il fatto che il controller player è Self-comandi autorità e route tramite il controller player.

In altri termini, quando abbiamo scoperto noi stessi al nostro obiettivo, il giocatore deve riuscire ad indicare all'host e host indicherà tutti gli altri utenti.

Tornare in LevelControl.cs SetGoalIndex sguardo. Qui viene impostato il valore di un valore in un synclist (AtGoal). Tenere presente che si sono nel contesto dell'host mentre questa operazione viene eseguita. Analogamente a un comando, una chiamata RPC è qualcosa può emettere l'host che faranno Sì tutti i client di eseguire il codice. Qui definiamo 'RpcCheckAllGoals'. Ogni client singolarmente verificare se tutti i tre AtGoals sono impostate e in questo caso, avviare il rocket.

### <a name="enjoy-your-progress"></a>Sfrutta i vantaggi dello stato di avanzamento

Compila nel capitolo precedente, si inizierà la sessione come prima. Questa volta, gli utenti in get visore VR immersivi da "porta" nel loro percorso, verrà visualizzata una descrizione comando che è possono visualizzare solo gli utenti di HoloLens. Gli utenti di HoloLens sono responsabili per la comunicazione questa indicazione per gli utenti nel visore VR immersivi. Il rocket avvierà nello spazio dopo ogni avatar ha allontanato il tastierino marrone corrispondente all'interno di Vulcano. La scena verrà reimpostato dopo 60 secondi in modo che è possibile farlo anche in questo caso.

## <a name="see-also"></a>Vedere anche
* [Input di MR 213: Controller di movimento](mixed-reality-213.md)
