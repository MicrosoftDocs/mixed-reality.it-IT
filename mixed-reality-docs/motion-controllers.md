---
title: Controller di movimento
description: Informazioni dettagliate sui controller di movimento di realtà mista.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6DOF controller, controller di movimento
ms.openlocfilehash: 7db1c16f8243081dc8f53e8722391f102c38e0d3
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629116"
---
# <a name="motion-controllers"></a>Controller di movimento

I controller di movimento sono [accessori hardware](hardware-accessories.md) che consentono agli utenti di eseguire un'azione in realtà mista. Un vantaggio dei controller di movimento tramite [movimenti](gestures.md) è che i controller hanno una precisa posizione nello spazio, consentendo di criterio granulare per le interazioni con oggetti digitali. Per le cuffie coinvolgenti di realtà mista di Windows, i controller di movimento sono il modo principale che gli utenti eseguirà l'azione nel proprio mondo.

![Controller del movimento di realtà mista di Windows](images/winmr-ck-1080x1080-350px.jpg)


## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Controller di movimento</td><td style="text-align: center;"></td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Dettagli sull'hardware

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

I controller del movimento di realtà mista di Windows offrono preciso e reattivo rilevamento del movimento nel campo visivo usando i sensori nel visore VR immersivi, ovvero non vi è alcuna necessità di installare hardware sulle pareti nello spazio di. Questi controller di movimento offrono la stessa facilità di installazione e la portabilità come auricolari coinvolgenti di realtà mista di Windows. I nostri partner dispositivo prevede di commercializzare e vendere questi controller sugli scaffali delle vendite al dettaglio in questo giorno festivo.

![Scopri il controller](images/controllerimage-750px.png)<br>
*Scopri il controller*

**Funzionalità:**
* Rilevamento ottico
* Trigger
* Pulsante di quadratini di ridimensionamento
* Thumbstick
* Touchpad

## <a name="setup"></a>Configurazione

### <a name="before-you-begin"></a>Prima di iniziare

**È necessario:**
* Un set di due controller di movimento.
* Quattro batterie AA.
* Un PC in grado di Bluetooth 4.0.

**Cercare gli aggiornamenti di Windows, Unity e driver**
* Visita [installare gli strumenti](install-the-tools.md) per le versioni di Windows, Unity, preferite e così via per lo sviluppo della realtà mista.
* Assicurarsi di avere più aggiornate [driver del controller visore VR e movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software).

### <a name="pairing-controllers"></a>Associazione di controller

I controller di movimento possono essere collegati con PC host usando le impostazioni di Windows, ad esempio eventuali altri dispositivi Bluetooth.

1. Inserire 2 batterie AA retro del controller. Per il momento, lasciare il coperchio della batteria.
2. Se si usa un Adapter di Bluetooth USB esterno invece di una periferica Bluetooth predefiniti, vedere la [Bluetooth le procedure consigliate](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) prima di procedere. Per la configurazione dei desktop con l'opzione predefinito, assicurarsi che sia connesso antenna.
3. Aprire **delle impostazioni di Windows** -> **dispositivi** -> **aggiungere Bluetooth o un altro dispositivo** -> **Bluetooth** e rimuovere tutte le istanze precedenti di "movimento controller, a destra" e "movimento controller – a sinistra". Controllare anche l'altra categoria di dispositivi nella parte inferiore dell'elenco.
4. Selezionare **Bluetooth aggiungere o un altro dispositivo** e scopri subito come iniziare a individuare i dispositivi Bluetooth.
5. Premere e tenere premuto il pulsante di Windows del controller per accendere il controller, rilasciarlo una volta buzzes.
6. Tenere premuto il pulsante di associazione (scheda nel raggruppamento della batteria) finché i LED di iniziare l'attivazione.
7. In attesa "Movimento controller - sinistra" o "movimento - Right" venga visualizzato nella parte inferiore dell'elenco. Selezionare questa opzione per coppia. Controller verrà vibrazione una sola volta quando si è connessi.

   ![Selezionare il controller di movimento in coppia, se più istanze di selezionarne uno dal vengono visualizzati nella parte inferiore dell'elenco](images/450px-bluetooth-add-a-device-300px.png)<br>
   *Selezionare "il movimento" controller alla coppia. Se sono presenti più istanze, selezionare uno tra la fine dell'elenco*
   
8. Verrà visualizzato il controller nelle impostazioni di Bluetooth sotto **"Mouse, tastiera e penna" categoria** come **connesso**. A questo punto, è possibile che venga visualizzato un aggiornamento del firmware, vedere [nella sezione successiva](motion-controllers.md#updating-controller-firmware).
9. Ricollega il coperchio della batteria.
10. Ripetere i passaggi da 1 a 9 per il secondo controller.

Dopo l'associazione è stata entrambi i controller, le impostazioni dovrebbero essere simile al seguente in **"Mouse, tastiera e penna" categoria** 

   ![Controller di movimento connessi](images/450px-motion-controller-connected-300px.png)<br>
   *Controller di movimento connessi*

Se i controller sono stati disabilitate dopo l'associazione, il relativo stato verrà visualizzata come appaiati. Se i controller di rimangono in modo permanente in "Altri dispositivi di" categoria associazione sia stata parzialmente completata ed è necessario essere nuovamente eseguito per ottenere funzionalità controller.

### <a name="updating-controller-firmware"></a>L'aggiornamento firmware del controller

* Se un visore VR immersivi è connesso al computer e nuovo firmware del controller è disponibile, il firmware avverranno ai controller di movimento automaticamente la volta successiva che siano attivati. Aggiornamenti del firmware del controller sono indicati da un modello di illuminazione quadranti LED un movimento circolare e richiedere 1-2 minuti.
* Dopo aver completato l'aggiornamento del firmware, i controller verranno riavviato e riconnettersi. Entrambi i controller devono essere connesse a questo punto. 
    
    ![Controller connessi](images/cyk-connected-300px.jpg)<br>
    *Controller connessi in impostazioni Bluetooth*

* Verificare il proprio lavoro controller correttamente:
    1. Avvio veloce **portale di realtà mista** e immettere la home page realtà mista.
    2. Spostare i controller e verificare di rilevamento, i pulsanti di test e verificare [teletrasporto](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) funziona. Se non, quindi estrae [risoluzione dei problemi controller di movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).

## <a name="gazing-and-pointing"></a>Gazing e scegliendo

Realtà mista di Windows supporta due modelli principali per l'interazione **estasiati ed eseguire il commit** e **scegliere ed eseguire il commit**:
* Con **estasiati ed eseguire il commit**, gli utenti di destinazione un oggetto con loro [estasiati](gaze.md) e quindi selezionare gli oggetti con mano aria-scelte, una su gamepad, un clicker o comandi vocali.
* Con **punto ed eseguire il commit**, un utente può puntare a un controller di movimento che punta in grado di supportare l'oggetto di destinazione e quindi selezionare gli oggetti con trigger del controller.

Le app che supporto puntando con i controller di movimento dovrebbe inoltre consentono le interazioni basate su sguardo laddove possibile, per concedere agli utenti di scegliere in che cosa input dispositivi che egli utilizza.

### <a name="managing-recoil-when-pointing"></a>La gestione recoil quando punta

Quando si usano controller di movimento scegliere ed eseguire il commit, gli utenti utilizzeranno il controller di destinazione e quindi eseguire un'azione spostando il trigger. Gli utenti che eseguire il pull del trigger vigorosamente rischia di mira il controller superiore alla fine della loro pull trigger rispetto a quello che era previsto.

Per gestire qualsiasi tali recoil che possono verificarsi quando gli utenti pull il trigger, l'app può collegarsi relativo ray targeting quando supera il valore dell'asse analogico del trigger 0,0. È quindi possibile intraprendere azioni tramite tale destinazione ray alcuni fotogrammi in un secondo momento quando il valore trigger raggiunga 1.0, purché la stampa viene eseguito entro un intervallo di tempo breve. Quando si usa il livello superiore [composito gesto tocco](gestures.md#composite-gestures), Windows gestiranno questa destinazione ray acquisizione e il timeout per l'utente.

## <a name="grip-pose-vs-pointing-pose"></a>Triangolo di ridimensionamento posa confronto posa puntamento

Realtà mista di Windows supporta controller di movimento in un'ampia gamma di fattori di forma, con la progettazione del ogni controller che differiscono per la relazione tra la posizione dell'utente mano e naturale "inoltro" direzione tale app deve usare per fare riferimento durante il rendering di controller.

Per rappresentare meglio questi controller, esistono due tipi di può causare per ogni origine di interazione, è possibile esaminare i **posa triangolo** e il **posa puntatore**.

### <a name="grip-pose"></a>Triangolo di ridimensionamento posa

Il **triangolo posa** rappresenta la posizione di palmo di una mano rilevata da un HoloLens o palmo che contiene un controller di movimento.

In coinvolgenti auricolari, posa il triangolo di ridimensionamento è particolarmente utile per eseguire il rendering **manuale dell'utente** oppure **mantenuto un oggetto a disposizione dell'utente**, ad esempio un doppio taglio o gun. Posa il triangolo di ridimensionamento viene usata anche quando la visualizzazione di un controller di movimento, come le **renderizzabili modello** fornite da Windows per un movimento controller utilizza posa il triangolo di ridimensionamento come origine e il centro di rotazione.

Posa il triangolo di ridimensionamento è definita in modo specifico come indicato di seguito:
* Il **afferrare posizione**: Il centroide palm quando tenendo naturalmente, il controller è regolato sinistro o destro da allineare al centro la posizione all'interno del triangolo di ridimensionamento. Nel controller di movimento di realtà mista di Windows, questa posizione viene allineato a livello generale con il pulsante. é quindi.
* Il **afferrare asse a destra dell'orientamento**: Quando si apre completamente la mano per formare una posa flat con un dito di 5, il raggio è normale che palm (in avanti dal palmo a sinistra, con le versioni precedenti dal palmo a destra)
* Il **afferrare asse diretta dell'orientamento**: Quando si chiude la mano parzialmente (come se che contiene il controller), il raggio che punta "forward" tramite il tubo costituita dalle dita non thumb.
* Il **afferrare orientamento di asse**: L'asse verticale in cui è inclusa per le definizioni di destra e l'inoltro.

### <a name="pointer-pose"></a>Puntatore posa

Il **posa puntatore** rappresenta la punta del controller in avanti che punta.

Il puntatore fornito dal sistema posa è particolarmente utile per raycast quando sei **il modello controller stesso per il rendering**. Se si esegue il rendering di un altro oggetto virtuale al posto di controller, ad esempio un gun virtuale, è necessario puntare con un raggio che risulta più naturale per l'oggetto virtuale, ad esempio un raggio che percorre cilindro del modello gun definito dall'app. Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, che punta all'oggetto virtuale sarà probabilmente più naturale per chi usa l'app.

## <a name="controller-tracking-state"></a>Stato di rilevamento del controller

Ad esempio le cuffie, il controller di movimento di realtà mista di Windows non richiede alcuna configurazione dei sensori esterna tracciamento. Al contrario, i controller vengono rilevati da sensori in auricolare stesso.

Se l'utente sposta il controller all'esterno il della cuffia campo visivo, nella maggior parte dei casi Windows continuerà a dedurre le posizioni di controller e fornire all'app. Quando il controller ha perso visual rilevamento per tempo sufficiente, eliminerà le posizioni del controller nelle posizioni di accuratezza approssimativo.

A questo punto, il sistema eseguirà il corpo del blocco il controller per l'utente e la posizione dell'utente di rilevamento durante lo spostamento, quando si espongono ancora orientamento true del controller tramite sensori relativo orientamento interno. Molte App che usano i controller per puntare alla e attivare gli elementi dell'interfaccia utente può funzionare normalmente anche se in accuratezza approssimativo senza che l'utente vengano rilevate.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>Ha a che fare in modo esplicito lo stato di rilevamento

Le app che si desiderano considerare le posizioni in base alle tiene traccia dello stato potrebbero andare oltre e controllare le proprietà sullo stato del controller, ad esempio SourceLossRisk e PositionAccuracy:

<table>
<tr>
<th> Tenere traccia dello stato </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Accuratezza elevata</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Elevata precisione per (a rischio di perdita)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza approssimativo</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Nessuna posizione</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: orange"> false</td>
</tr>
</table>



Questi stati di rilevamento movimento controller sono definiti come segue:
* **Alta precisione:** Anche se il controller di movimento è all'interno il della cuffia campo visivo, in genere fornirà le posizioni di elevata precisione, basate sul rilevamento visual. Si noti che un controller di spostamento che momentaneamente lascia il campo visivo o momentaneamente è nascosto dai sensori visore VR (ad esempio, da altra parte dell'utente) continuerà a restituire pose elevata precisione per un breve periodo di tempo, basato sul rilevamento movimento inerziale del controller di sé stesso.
* **Elevata precisione (a rischio di perdita):** Quando l'utente sposta il controller di movimento oltre il bordo del campo visivo della cuffia, le cuffie saranno presto possibile tenere traccia visivamente della posizione del controller. L'app conosce quando il controller ha raggiunto il limite del campo di visualizzazione, vedere l'articolo di **SourceLossRisk** raggiungere 1.0. A questo punto, l'app può scegliere di sospendere i movimenti di controller che richiedono un flusso costante di altissima qualità creeranno.
* **Accuratezza approssimativo:** Quando il controller ha perso visual rilevamento per tempo sufficiente, eliminerà le posizioni del controller nelle posizioni di accuratezza approssimativo. A questo punto, il sistema eseguirà il corpo del blocco il controller per l'utente e la posizione dell'utente di rilevamento durante lo spostamento, quando si espongono ancora orientamento true del controller tramite sensori relativo orientamento interno. Molte App che usano i controller per puntare alla e attivare gli elementi dell'interfaccia utente possono operare come normale periodo di tempo accuratezza approssimativo senza che l'utente vengano rilevate. Le app con più intensi i requisiti di input possono scegliere di questo elenco da rilevare **elevata** approssimazione pari a **approssimato** accuratezza controllando il **PositionAccuracy** proprietà, per esempio per consentire all'utente un hitbox maggiori nelle destinazioni fuori dello schermo durante questo periodo.
* **Nessuna posizione:** Mentre il controller può operare accuratezza approssimativo per molto tempo, in alcuni casi il sistema sa che anche una posizione bloccata corpo non è significativa al momento. Ad esempio, un controller che è stato appena abilitato non può sono mai stato osservato visivamente o un utente può inserire verso il basso un controller che viene quindi prelevato da un altro utente. In tali casi, il sistema non fornirà a qualsiasi posizione all'app, e **TryGetPosition** restituirà false.

## <a name="interactions-low-level-spatial-input"></a>Interazioni tra: Input spaziale a basso livello

Sono le interazioni principali tra le mani e controller di movimento **selezionate**, **dal Menu**, **afferrare**, **Touchpad**,  **Thumbstick**, e **Home**.
* **Selezionare** è l'interazione principale per attivare un ologrammi, costituito da una pressione seguita da una versione. Per i controller di movimento, è eseguire Select pressione di un utilizzo di trigger del controller. Altri modi per eseguire un'istruzione Select sono parlando la [vocali comando](voice-input.md) "Select". L'interazione seleziona stesso può essere utilizzato all'interno di qualsiasi app. Pensare a selezionare l'equivalente di un topo clic, un'azione di universal informazioni su una sola volta e applicarne tra tutte le app.
* **Menu** è rappresentato dall'interazione secondario per eseguire operazioni su un oggetto usato per eseguire il pull di un menu di scelta rapida o eseguire altre azioni secondarie. Con i controller di movimento, è possibile eseguire un'azione di menu usando il controller *menu* pulsante. (ad esempio il pulsante con l'icona "menu" hamburger su di esso)
* **Afferrare** è come gli utenti direttamente possono eseguire azioni sugli oggetti a loro portata di mano per la manipolazione. Per eseguire un'azione. é quindi con i controller di movimento, stesso come strettamente concentrare la prima. Un controller di movimento rilevi. é quindi con un pulsante di quadratini di ridimensionamento, palm trigger o altro sensore.
* **Touchpad** consente all'utente di modificare un'azione in due dimensioni lungo la superficie del touchpad del controller un movimento, eseguire il commit dell'azione facendo verso il basso il touchpad. Dotati di touchpad forniscono premuto, lo stato aggiornato e normalizzata delle coordinate XY. X e Y compreso tra -1 e 1 tutta la gamma del touchpad circolare, con un centro a (0, 0). Per l'asse X -1 è a sinistra e 1 è a destra. Per l'asse Y, -1 è nella parte inferiore e 1 è nella parte superiore.
* **Thumbstick** consente all'utente di modificare un'azione in due dimensioni spostando thumbstick del controller un movimento entro l'intervallo circolare, eseguire il commit dell'azione facendo verso il basso il thumbstick. Levette anche fornire uno stato di premuto e normalizzati coordinate XY. X e Y compreso tra -1 e 1 tutta la gamma del touchpad circolare, con un centro a (0, 0). Per l'asse X -1 è a sinistra e 1 è a destra. Per l'asse Y, -1 è nella parte inferiore e 1 è nella parte superiore.
* **Home** è un'azione di sistema speciale che consente di tornare al menu Start. È simile alla pressione del tasto Windows sulla tastiera o il tasto Xbox in un controller Xbox. È possibile passare home premendo il pulsante di Windows in un controller di movimento. Si noti che è anche sempre possibile tornare a Start pronunciare "Ehi Cortana, Go Home". Le app non è possibile reagire in modo specifico alle azioni principali, come vengono gestiti dal sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Movimenti compositi: Input spaziali ad alto livello

Entrambe [mano i movimenti](gestures.md) e i controller di movimento possono essere monitorati nel corso del tempo per rilevare un set comune di alto livello  **[movimenti compositi](gestures.md#composite-gestures)**. Questo consente all'app per il rilevamento di alto livello **toccare**, **contenere**, **manipolazione** e **navigazione** movimenti, se gli utenti comporta l'utilizzo di le mani o controller.

## <a name="rendering-the-motion-controller-model"></a>Il modello di controller di movimento per il rendering

**I modelli 3D controller** Windows rende disponibili per App di un modello di ogni controller di movimento renderizzabili attualmente attivi nel sistema. Facendo in modo che l'app in modo dinamico, caricare e l'obiettivo di questi modelli di controller fornite dal sistema in fase di esecuzione, è possibile garantire che l'app è progettazioni compatibile per eventuali, prossimi controller.

Questi modelli renderizzabili devono eseguire il rendering nel **triangolo posa** del controller, come l'origine del modello è allineata con questo punto nel mondo fisico. Se si esegue il rendering di modelli di controller, è quindi possibile raycast in scena dal **posa puntatore**, che rappresenta il raggio lungo cui naturalmente probabile che gli utenti in modo da puntare, progettazione fisica del controller specificato.

Per altre informazioni su come caricare modelli di controller in modo dinamico in Unity, vedere la [il modello di controller di movimento in Unity per il Rendering](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) sezione.

**Grafica 2D controller** Sebbene sia consigliabile associare suggerimenti in-app controller e i comandi per i modelli in-app controller stessi, alcuni sviluppatori potrebbe essere necessario usare rappresentazioni di grafica 2D riga dei controller di movimento in esercitazione di flat"" o "procedure" INTERFACCIA UTENTE. Per gli sviluppatori, abbiamo apportato movimento controller line art file PNG disponibili in entrambi bianco e nero riportato di seguito (pulsante destro del mouse per salvare).

![Anteprima del tratto i controller di movimento](images/motioncontrollers-black-preview-300px.png)

 [I controller di movimento ad alta risoluzione grafica in ' ' vuoti ' '](images/motioncontrollers-white.png)
 
 [I controller di movimento ad alta risoluzione grafica in ' ' nero ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>Domande frequenti

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>È possibile si coppia di movimento controller per più PC?

Movimento controller supportano l'associazione con un unico PC. Seguire le istruzioni sullo [installazione del controller di movimento](motion-controllers.md#setup) per abbinare i controller.

### <a name="how-do-i-update-motion-controller-firmware"></a>Come esegue l'aggiornamento firmware del controller di movimento?

Firmware del controller di movimento fa parte del driver visore VR e verrà aggiornato automaticamente nella connessione se necessario. Gli aggiornamenti del firmware in genere richiedere 1-2 minuti a seconda della qualità di pulsanti di opzione e collegamenti Bluetooth. In rari casi, aggiornamenti del firmware del controller potrebbero richiedere fino a 10 minuti, che può indicare la scarsa connettività Bluetooth o radio interferenze. Vedi [Bluetooth le procedure consigliate nella Guida alla appassionato](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) per risolvere i problemi di connettività. Dopo un aggiornamento del firmware, controller verrà riavviato e ristabilire la connessione all'host del computer (è possibile notare i LED passare chiaro per il rilevamento). Se un aggiornamento del firmware viene interrotta (ad esempio, i controller di interruzione dell'alimentazione), verrà tentata nuovamente la volta successiva i controller siano accesi.

### <a name="how-i-can-check-battery-level"></a>In che modo è possibile controllare a livello di batteria?

Nel [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md), è possibile attivare il controller di per visualizzare il livello di batteria sul lato opposto del modello virtuale. Non vi è alcun indicatore del livello di batteria fisico.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>È possibile usare questi controller senza un auricolare? Solo per l'input di joystick/trigger/e così via?

Non per le applicazioni di Windows universale.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Visualizzare [risoluzione dei problemi controller di movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) nella Guida alla imprenditore.

## <a name="filing-motion-controller-feedbackbugs"></a>Registrare i commenti e suggerimenti di movimento controller/i bug

[Invia commenti e suggerimenti](give-us-feedback.md) nell'Hub di commenti e suggerimenti, utilizzando la categoria "Input realtà mista ->".

## <a name="see-also"></a>Vedere anche
* [Movimenti e controller del movimento in Unity](gestures-and-motion-controllers-in-unity.md)
* [Le mani e i controller di movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Movimenti](gestures.md)
* [Input MR 213: Controller del movimento](mixed-reality-213.md)
* [Guida della appassionato: La realtà mista di Windows home](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guida della appassionato: Uso di App e giochi in realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Funzionamento del rilevamento interno a esterno](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
