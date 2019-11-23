---
title: Controller di movimento
description: Dettagli sui controller di movimento della realtà mista.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: controller 6DOF, controller di movimento
ms.openlocfilehash: 84ebc6c0d7c63e58346b6ee9e565811bc40571b5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437847"
---
# <a name="motion-controllers"></a>Controller di movimento

:::row:::
    :::column:::
        I controller di movimento sono [Accessori hardware](hardware-accessories.md) che consentono agli utenti di intervenire in realtà mista. Un vantaggio dei controller di movimento rispetto ai [movimenti](gaze-and-commit.md#composite-gestures) è che i controller hanno una posizione precisa nello spazio, consentendo un'interazione con granularità fine con gli oggetti digitali. Per gli auricolari a realtà mista di Windows, i controller di movimento sono il modo principale in cui gli utenti interverranno in tutto il mondo.<br>
        <br>
        *Image: controller di movimento per realtà mista di Windows*
    :::column-end:::
        :::column:::
       ![Controller di movimento per la realtà mista di Windows](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a>Supporto di dispositivi

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funzionalità</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
</tr>
<tr>
     <td>Controller di movimento</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Dettagli hardware

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

I controller di movimento per la realtà mista di Windows offrono un tracking preciso e reattivo del movimento nel campo della visualizzazione usando i sensori nell'auricolare immersiva, ovvero non è necessario installare hardware nei muri dello spazio. Questi controller di movimento offriranno la stessa facilità di installazione e portabilità come gli auricolari immersivi a realtà mista di Windows. I nostri partner per i dispositivi pianificano di commercializzare e vendere questi controller ai piani di vendita al dettaglio.

![ottenere informazioni sul controller](images/controllerimage-750px.png)<br>
*Scopri il controller*

**Funzionalità**
* Rilevamento ottico
* Trigger
* Pulsante di cattura
* Levetta
* Touchpad

## <a name="setup"></a>Installazione

### <a name="before-you-begin"></a>Prima di iniziare

**Sono necessari:**
* Set di due controller di movimento.
* Quattro batterie AA.
* Un PC in grado di Bluetooth 4,0.

**Verificare la disponibilità di Windows, Unity e gli aggiornamenti dei driver**
* Visitare [installare gli strumenti](install-the-tools.md) per le versioni preferite di Windows, Unity e così via per lo sviluppo di realtà miste.
* Assicurarsi di disporre dei driver più aggiornati per l' [auricolare e il controller di movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software).

### <a name="pairing-controllers"></a>Associazione di controller

I controller di movimento possono essere legati a computer host usando le impostazioni di Windows come qualsiasi altro dispositivo Bluetooth.

1. Inserire 2 batterie AA nella parte posteriore del controller. Lasciare il coperchio della batteria per il momento.
2. Se si usa una scheda Bluetooth USB esterna anziché una radio Bluetooth incorporata, verificare le procedure consigliate [Bluetooth](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) prima di procedere. Per la configurazione del desktop con la radio predefinita, assicurarsi che l'antenna sia connessa.
3. Aprire **impostazioni di Windows** -> **dispositivi** -> **aggiungere Bluetooth o altro dispositivo** -> **Bluetooth** e rimuovere le istanze precedenti di "motion controller – Right" e "motion controller – left". Controllare anche la categoria altri dispositivi nella parte inferiore dell'elenco.
4. Selezionare **Aggiungi Bluetooth o altro dispositivo** e vedere avvio per individuare i dispositivi Bluetooth.
5. Premere e tenere premuto il pulsante Windows del controller per accendere il controller, quindi rilasciarlo dopo il ronzio.
6. Premere e tenere premuto il pulsante di associazione (scheda nel compartimento della batteria) fino a quando i LED non iniziano a pulsare.

:::row:::
    :::column:::
7. Attendere "motion controller-left" o "motion controller-Right" per visualizzare la parte inferiore dell'elenco. Selezionare l'associazione. Il controller vibra una volta quando si è connessi.<br>
        <br>
        *Image: selezionare "motion controller" da associare. Se sono presenti più istanze, selezionarne una nella parte inferiore dell'elenco*
    :::column-end:::
        :::column:::
       ![Selezionare il controller di movimento da abbinare, se più istanze ne selezionano una da visualizzare nella parte inferiore dell'elenco](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. Il controller verrà visualizzato nelle impostazioni Bluetooth nella **categoria "mouse, tastiera, & Pen"** come **connesso**. A questo punto, è possibile ottenere un aggiornamento del firmware: vedere la [sezione successiva](motion-controllers.md#updating-controller-firmware).
9. Alleghi il coperchio della batteria.
10. Ripetere i passaggi 1-9 per il secondo controller.

<br>

:::row:::
    :::column:::
        Una volta abbinati entrambi i controller, le impostazioni dovrebbero essere simili a quelle della **categoria "mouse, tastiera, & Pen"** <br>
        <br>
        *Immagine: controller di movimento connessi*
    :::column-end:::
        :::column:::
       ![Controller di movimento connessi](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

Se i controller sono spenti dopo l'associazione, lo stato verrà visualizzato come abbinato. Se i controller vengono mantenuti in modo permanente nell'associazione di categoria "altri dispositivi", potrebbe essere stato completato solo parzialmente e deve essere eseguito di nuovo per ottenere la funzionalità del controller.

### <a name="updating-controller-firmware"></a>Aggiornamento del firmware del controller

* Se un headset immersivo è connesso al PC ed è disponibile un nuovo firmware del controller, il firmware verrà inserito automaticamente nei controller di movimento alla successiva accensione. Gli aggiornamenti del firmware del controller sono indicati da un modello di illuminazione del quadrante dei LED in movimento circolare e da richiedere 1-2 minuti.


:::row:::
    :::column:::
* Al termine dell'aggiornamento del firmware, i controller vengono riavviati e riconnessi. Entrambi i controller devono essere connessi adesso. <br>
        <br>
        *Immagine: controller connessi nelle impostazioni Bluetooth*
    :::column-end:::
        :::column:::
       ![Controller connessi](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* Verificare che i controller funzionino correttamente:
    1. Avviare il **portale di realtà mista** e immettere la Home realtà mista.
    2. Spostare i controller e verificare il rilevamento, i pulsanti di test e verificare il funzionamento della [teleportazione](navigating-the-windows-mixed-reality-home.md#getting-around-your-home). In caso contrario, consultare la sezione relativa alla [risoluzione dei problemi del controller di movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).

## <a name="gazing-and-pointing"></a>Osservazione e puntamento

La realtà mista di Windows supporta due modelli chiave per interazione, **sguardo e commit** , **punto e commit**:
* Con lo **sguardo e il commit**, gli utenti hanno come destinazione un oggetto con il proprio [sguardo](gaze-and-commit.md) , quindi selezionano gli oggetti con rubinetti d'aria, un gamepad, un clic o la loro voce.
* Con **Point e commit**, un utente può puntare a un controller di movimento in grado di puntare all'oggetto di destinazione e quindi selezionare oggetti con il trigger del controller.

Le app che supportano l'indirizzamento con i controller di movimento devono anche abilitare le interazioni basate su sguardi laddove possibile, per offrire agli utenti la possibilità di scegliere i dispositivi di input utilizzati.

### <a name="managing-recoil-when-pointing"></a>Gestione della ribobina quando si punta

Quando si usano i controller di movimento per puntare ed eseguire il commit, gli utenti utilizzeranno il controller per individuare e quindi intervenire eseguendo il pull del trigger. Gli utenti che tirano il trigger vigorosamente potrebbero finire a puntare il controller in un livello superiore alla fine del pull del trigger rispetto a quello previsto.

Per gestire un eventuale rinculo che può verificarsi quando gli utenti effettuano il pull del trigger, l'app può bloccare il raggio di destinazione quando il valore dell'asse analogico del trigger supera 0,0. È quindi possibile eseguire un'azione con la definizione di un numero limitato di frame in un secondo momento quando il valore del trigger raggiunge 1,0, purché la pressione finale venga eseguita in un intervallo di tempo breve. Quando si usa il gesto di [tocco composito](gaze-and-commit.md#composite-gestures)di livello superiore, Windows gestirà l'acquisizione e il timeout dei raggi di destinazione.

## <a name="grip-pose-vs-pointing-pose"></a>Posa del grip e puntamento

La realtà mista di Windows supporta i controller di movimento in diversi fattori di forma, con la progettazione di ogni controller diversa nella relazione tra la posizione della mano dell'utente e la direzione naturale "Avanti" che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, esistono due tipi di pose che è possibile esaminare per ogni origine interazione, la **posizione del grip** e la **posizione del puntatore**.

### <a name="grip-pose"></a>Pose di grip

La posizione del **grip** rappresenta la posizione della Palma di una mano rilevata da un HoloLens o della palma che contiene un controller di movimento.

Negli auricolari immersivi, la disposizione dei grip è la scelta migliore per eseguire **il rendering della mano dell'utente** o di **un oggetto contenuto nella mano**, ad esempio una spada o una pistola. La posizione del grip viene usata anche durante la visualizzazione di un controller di movimento, perché il **modello di rendering** fornito da Windows per un controller di movimento usa la posizione del grip come origine e centro di rotazione.

Il grip viene definito in modo specifico come segue:
* **Posizione del grip**: il centro della palma quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del grip. Sul controller di movimento per la realtà mista di Windows, questa posizione viene in genere allineata con il pulsante afferra.
* L' **asse destro dell'orientamento del grip**: quando si apre completamente la mano per formare una formula a 5 dita piatta, il raggio normale per la Palma (in avanti dal palmo sinistro e viceversa)
* **Asse di avanzamento dell'orientamento del grip**: quando si chiude parzialmente la mano (come se si utilizzasse il controller), il raggio che punta "in poi" attraverso il tubo formato dalle dita non Thumb.
* **Asse verticale dell'orientamento del grip**: l'asse verso l'alto implicato dalle definizioni di destra e di avanzamento.

### <a name="pointer-pose"></a>Posa puntatore

Il **puntatore** posizionato rappresenta il suggerimento del controller che punta in futuro.

La disposizione del puntatore fornita dal sistema è ideale per Raycast quando si esegue **il rendering del modello di controller**. Se si esegue il rendering di un altro oggetto virtuale al posto del controller, ad esempio una pistola virtuale, è necessario puntare con un raggio più naturale per tale oggetto virtuale, ad esempio un raggio che viaggia lungo il barilotto del modello Gun definito dall'app. Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, puntare con l'oggetto virtuale sarà probabilmente più naturale per quelli che usano l'app.

## <a name="controller-tracking-state"></a>Stato di rilevamento del controller

Come gli auricolari, il controller di movimento di realtà mista di Windows non richiede l'installazione di sensori di rilevamento esterni. Il controller viene invece rilevato dai sensori nell'auricolare.

Se l'utente sposta i controller fuori dal campo di visualizzazione dell'auricolare, nella maggior parte dei casi Windows continuerà a dedurre le posizioni del controller e le fornirà all'app. Quando il controller ha perso il rilevamento visivo per un periodo di tempo sufficiente, le posizioni del controller vengono rilasciate a posizioni di accuratezza approssimativa.

A questo punto, il sistema bloccherà il controller all'utente, tenendo traccia della posizione dell'utente mentre si spostano, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano i controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con una precisione approssimativa senza che l'utente abbia notato.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>Ragionamento sullo stato di rilevamento in modo esplicito

Le app che desiderano gestire le posizioni in modo diverso in base allo stato di rilevamento possono andare oltre e controllare le proprietà nello stato del controller, ad esempio SourceLossRisk e PositionAccuracy:

<table>
<tr>
<th> Stato di rilevamento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td>   di <b>accuratezza elevata</b></td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza elevata (a rischio di perdita)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza approssimativa</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Nessuna posizione</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: orange"> false</td>
</tr>
</table>



Questi stati di rilevamento del controller di movimento sono definiti come segue:
* **Accuratezza elevata:** Mentre il controller di movimento si trova all'interno del campo di visualizzazione dell'auricolare, in genere fornisce posizioni con accuratezza elevata, in base al rilevamento visivo. Si noti che un controller che sposta temporaneamente il campo di visualizzazione o è temporaneamente nascosto dai sensori dell'auricolare (ad esempio, da parte dell'utente) continuerà a restituire le pose con precisione elevata per un breve periodo di tempo, in base al rilevamento inerziale del controller. stesso.
* **Accuratezza elevata (a rischio di perdita):** Quando l'utente sposta il controller di movimento oltre il bordo del campo di visualizzazione dell'auricolare, l'auricolare non sarà presto in grado di rilevare visivamente la posizione del controller. L'app sa quando il controller ha raggiunto questo limite FOV visualizzando il **SourceLossRisk** REACH 1,0. A questo punto, l'app può scegliere di sospendere i movimenti del controller che richiedono un flusso costante di pose di qualità molto elevata.
* **Accuratezza approssimativa:** Quando il controller ha perso il rilevamento visivo per un periodo di tempo sufficiente, le posizioni del controller vengono rilasciate a posizioni di accuratezza approssimativa. A questo punto, il sistema bloccherà il controller all'utente, tenendo traccia della posizione dell'utente mentre si spostano, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano i controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con una precisione approssimativa senza che l'utente ne abbia notato. Le app con requisiti di input più pesanti possono scegliere di comprendere questo calo dall'accuratezza **elevata** all'accuratezza **approssimativa** controllando la proprietà **PositionAccuracy** , ad esempio per dare all'utente un hitbox più generoso sulle destinazioni fuori schermo durante questo periodo di tempo.
* **Nessuna posizione:** Mentre il controller può funzionare con una precisione approssimativa per molto tempo, a volte il sistema sa che anche una posizione bloccata dal corpo non è al momento significativa. Ad esempio, un controller appena attivato potrebbe non essere mai stato osservato visivamente oppure un utente può arrestare un controller che viene quindi prelevato da qualcun altro. In questi casi, il sistema non fornirà alcuna posizione all'app e **TryGetPosition** restituirà false.

## <a name="interactions-low-level-spatial-input"></a>Interazioni: input spaziale di basso livello

Le interazioni di base tra i controller hands e Motion sono **Select**, **menu**, **afferrare**, **touchpad**, **levetta**e **Home**.
* **Select** è l'interazione principale per attivare un ologramma, costituito da una pressione seguita da una versione. Per i controller di movimento, eseguire una selezione premere usando il trigger del controller. Altri modi per eseguire un'impostazione Select sono pronunciando il [comando vocale](voice-input.md) "Select". La stessa interazione SELECT può essere usata in qualsiasi app. Si pensi a SELECT come all'equivalente di un clic del mouse, un'azione universale che si apprende una volta e quindi si applica a tutte le app.
* **Menu** è l'interazione secondaria per agire su un oggetto, usato per eseguire il pull di un menu di scelta rapida o eseguire altre azioni secondarie. Con i controller di movimento è possibile eseguire un'azione di menu usando il pulsante di *menu* del controller. (ovvero il pulsante con l'icona "menu" di hamburger)
* La **comprensione** è il modo in cui gli utenti possono agire direttamente sugli oggetti a loro disposizione per manipolarli. Con i controller di movimento, è possibile eseguire un'azione di comprensione inserendo il pugno. Un controller di movimento può rilevare una stretta con un pulsante di cattura, un trigger di Palma o un altro sensore.
* **Touchpad** consente all'utente di modificare un'azione in due dimensioni lungo la superficie del touchpad del controller di movimento, eseguendo il commit dell'azione facendo clic sul touchpad. I touchpad forniscono lo stato premuto, lo stato di contatto e le coordinate XY normalizzate. X e Y sono compresi tra-1 e 1 nell'intervallo del touchpad circolare, con un centro in corrispondenza di (0, 0). Per X,-1 si trova a sinistra e 1 si trova a destra. Per Y,-1 si trova nella parte inferiore e 1 si trova nella parte superiore.
* **Levetta** consente all'utente di modificare un'azione in due dimensioni spostando il levetta del controller di movimento nell'intervallo circolare, eseguendo il commit dell'azione facendo clic sul levetta. ThumbSticks inoltre fornire uno stato premuto e le coordinate XY normalizzate. X e Y sono compresi tra-1 e 1 nell'intervallo del touchpad circolare, con un centro in corrispondenza di (0, 0). Per X,-1 si trova a sinistra e 1 si trova a destra. Per Y,-1 si trova nella parte inferiore e 1 si trova nella parte superiore.
* **Home** è un'azione speciale di sistema che viene utilizzata per tornare al menu Start. È simile a premere il tasto Windows su una tastiera o il pulsante Xbox in un controller Xbox. È possibile passare a casa premendo il pulsante Windows in un controller di movimento. Si noti anche che è sempre possibile tornare all'inizio dicendo "Hey Cortana, Go Home". Le app non possono rispondere in modo specifico alle azioni domestiche, perché vengono gestite dal sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Movimenti compositi: input spaziale di alto livello

Per rilevare un set comune di **[movimenti compositi](gaze-and-commit.md#composite-gestures)** di alto livello, è possibile tenere traccia dei [movimenti di mano](gaze-and-commit.md#composite-gestures) e dei controller di movimento nel tempo. Ciò consente all'app di rilevare movimenti di **tocco**, **attesa**, **manipolazione** e **spostamento** di alto livello, indipendentemente dal fatto che gli utenti finiscano con le mani o i controller.

## <a name="rendering-the-motion-controller-model"></a>Rendering del modello del controller di movimento

**modelli di controller 3D** Windows rende disponibile per le app un modello di rendering di ogni controller di movimento attualmente attivo nel sistema. Grazie alla possibilità di caricare e articolare dinamicamente i modelli di controller forniti dal sistema in fase di esecuzione, l'app è in grado di garantire la compatibilità con le versioni future per qualsiasi futura progettazione del controller.

È necessario eseguire il rendering di questi modelli di cui è possibile eseguire il rendering in corrispondenza della **posizione** del controller, perché l'origine del modello è allineata a questo punto nel mondo fisico. Se si esegue il rendering dei modelli di controller, è possibile che si desideri Raycast nella scena dalla **posizione dell'indicatore**di misura, che rappresenta il raggio lungo il quale gli utenti si aspettano naturalmente di puntare, data la progettazione fisica del controller.

Per altre informazioni su come caricare dinamicamente i modelli di controller in Unity, vedere la sezione [rendering del modello di controller di movimento in Unity](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) .

**linea grafica controller 2D** Sebbene sia consigliabile aggiungere comandi e suggerimenti del controller in-app ai modelli di controller in-app, è possibile che alcuni sviluppatori vogliano usare rappresentazioni linea 2D dei controller di movimento nell'interfaccia utente "esercitazione" o "procedura" flat. Per gli sviluppatori, sono stati resi disponibili i file con estensione png per la linea del controller di movimento.

![Anteprima dei controller di movimento line art](images/motioncontrollers-black-preview-300px.png)

[Linea d'arte dei controller di movimento a risoluzione completa in ''' White ''](images/motioncontrollers-white.png)
 
[Controller di movimento a risoluzione completa line art in ''' Black ''](images/motioncontrollers-black.png)

## <a name="faq"></a>Domande frequenti

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>È possibile associare I controller di movimento a più PC?

I controller di movimento supportano l'associazione a un singolo computer. Per associare i controller, seguire le istruzioni sul [programma di installazione del controller di movimento](motion-controllers.md#setup) .

### <a name="how-do-i-update-motion-controller-firmware"></a>Ricerca per categorie aggiornare il firmware del controller di movimento?

Il firmware del controller di movimento fa parte del driver della cuffia e verrà aggiornato automaticamente in caso di connessione, se necessario. Gli aggiornamenti del firmware in genere importano 1-2 minuti a seconda della qualità del collegamento e della radio Bluetooth. In rari casi, gli aggiornamenti del firmware del controller possono richiedere fino a 10 minuti, che possono indicare una scarsa connettività Bluetooth o interferenze radio. Per risolvere i problemi di connettività, vedere [procedure consigliate Bluetooth nella Guida per gli appassionati](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) . Dopo un aggiornamento del firmware, i controller verranno riavviati e riconnessi al PC host. è possibile notare che i LED sono luminosi per il rilevamento. Se un aggiornamento del firmware viene interrotto (ad esempio, i controller perdono energia), verrà ritentata la volta successiva che i controller saranno accesi.

### <a name="how-i-can-check-battery-level"></a>Come posso controllare il livello della batteria?

Nella [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md), è possibile attivare il controller per visualizzare il relativo livello di batteria sul lato inverso del modello virtuale. Nessun indicatore del livello di batteria fisico.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>È possibile usare questi controller senza cuffie? Solo per l'input joystick/trigger/etc?

Non per le applicazioni Windows universali.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Vedere la pagina relativa alla [risoluzione dei problemi di motion controller](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) nella Guida per gli appassionati.

## <a name="filing-motion-controller-feedbackbugs"></a>Suggerimenti/bug del controller di movimento di archiviazione

[Inviare commenti e suggerimenti](give-us-feedback.md) nell'hub feedback, usando la categoria "Mixed Reality-> input".

## <a name="see-also"></a>Vedi anche
* [Movimenti e controller del movimento in Unity](gestures-and-motion-controllers-in-unity.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Movimenti](gaze-and-commit.md#composite-gestures)
* [Input MR 213: controller di movimento](mixed-reality-213.md)
* [Guida per gli appassionati: Home page della realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guida per gli appassionati: uso di giochi & app in realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Funzionamento del rilevamento interno](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
