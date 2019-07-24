---
title: Puntamento con la testa e commit
description: Panoramica del modello di input puntamento con la testa e commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: realtà mista, sguardo fisso, selezione della destinazione con lo sguardo fisso, interazione, progettazione
ms.openlocfilehash: aeca5ceacf5ae350aa06cb58cc68162f885f6d78
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387675"
---
# <a name="head-gaze-and-commit"></a>Puntamento con la testa e commit
Head-sguardi e commit è un modello di input che prevede la destinazione di un oggetto con la direzione della testa che punta verso l'alto (direzione), quindi agisce su di esso con un input secondario, ad esempio il gesto d'aria della mano o il comando Voice Select. Viene considerato un modello di input molto lungo con manipolazione indiretta, vale a dire che è consigliabile usarlo per interagire con il contenuto che supera le armi.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modello di input</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e commit</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</td>
        <td>➕ Opzione alternativa</td>
    </tr>
</table>

## <a name="head-gaze"></a>Puntamento con la testa
I visori VR realtà mista usano la posizione e l'orientamento della testa dell'utente per determinare il vettore di direzione della testa. Per comprendere questo concetto, pensa a un laser che punti dritto davanti partendo direttamente tra gli occhi dell'utente. Questa è una grossolana approssimazione del punto guardato dall'utente. L'applicazione può intersecare questo raggio con oggetti virtuali o reali e creare un cursore in tale posizione per consentire all'utente di conoscere gli elementi attualmente destinati.

Oltre al controllo, alcuni auricolari con realtà mista, come HoloLens 2, includono sistemi di rilevamento degli occhi che producono un vettore di sguardi oculari. In questo modo si ottiene una misurazione precisa di dove sta guardando l'utente. È possibile compilare le interazioni con lo sguardo e il commit usando gli sguardi. Questa operazione viene tuttavia fornita con un set di vincoli di progettazione molto diverso, che verrà trattato separatamente nell'articolo relativo agli [sguardi](eye-tracking.md).

## <a name="commit"></a>Commit
Dopo la destinazione di un oggetto o di un elemento dell'interfaccia utente, l'utente può interagire o fare clic su di esso usando un input secondario. Questo è il cosiddetto passaggio di commit del modello. Sono supportati i metodi di commit seguenti:

- Movimento tocco aereo
- Pronunciare il comando Voice, SELECT o uno dei comandi Voice di destinazione
- Premere un solo pulsante su un [clic del HoloLens](hardware-accessories.md#hololens-clicker)
- Premere il pulsante ' A ' in un gamepad Xbox
- Premere il pulsante "A" in un controller adattivo Xbox

### <a name="head-gaze-and-air-tap-gesture"></a>Puntamento con la testa e simulazione del tocco
Per simulazione del tocco si intende un gesto tocco fatto con la mano mantenuta in verticale. Per eseguire un rubinetto aereo, aumentare il dito dell'indice nella posizione pronta, quindi pizzicare il cursore e aumentare il dito dell'indice fino al rilascio. In HoloLens (1a generazione), il rubinetto aereo è l'input secondario più comune.

![Dito in posizione di pronto e quindi un movimento di tocco o di clic](images/readyandpress.jpg)<br>

Il rubinetto aereo è disponibile anche in HoloLens 2. È stato rilassato dalla versione originale. Quasi tutti i tipi di Pinch sono ora supportati finché la mano è eretta e mantiene ancora. Ciò consente agli utenti di apprendere ed eseguire più facilmente il movimento. Questo nuovo tocco sostituisce quello precedente tramite la stessa API, in modo che le applicazioni esistenti avranno automaticamente il nuovo comportamento dopo la ricompilazione per HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Puntamento con la testa e comando vocale "Seleziona"
Il comando Voice è uno dei metodi di interazione principali in realtà mista. Fornisce un meccanismo senza intervento pratico per controllare il sistema. Sono disponibili diversi tipi di modelli di interazione vocale:

- Il comando generico SELECT che esegue l'attivazione di un clic o il commit come input secondario.
- I comandi dell'oggetto come Close o rendono più grande l'esecuzione e il commit in un'azione come input secondario.
- La comandi globale come go to Start non richiede una destinazione.
- Le interfacce utente di conversazione o entità come Cortana hanno una funzionalità del linguaggio di intelligenza artificiale.
- Comandi personalizzati.

Per ulteriori dettagli, oltre a un elenco comprenhesive di comandi disponibili e a come utilizzarli, consultare le linee guida per i comandi [vocali](voice-design.md) .


### <a name="head-gaze-and-hololens-clicker"></a>Puntamento con la testa e dispositivo Clicker HoloLens
Il HoloLens clic è il primo dispositivo periferico creato in modo specifico per HoloLens. È incluso in HoloLens (1st Gen) Development Edition. Il clicker HoloLens consente a un utente di fare clic con movimento minimo e di eseguire il commit come input secondario. Il HoloLens Clicker si connette a HoloLens (1st Gen) o HoloLens 2 usando Bluetooth Low Energy (BTLE).

![Dispositivo Clicker HoloLens](images/hololens-clicker-500px.jpg)<br>
*Dispositivo Clicker HoloLens*

Per altre informazioni e istruzioni su come associare il dispositivo, fai clic [qui](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Puntamento con la testa e controller wireless Xbox
Il controller wireless Xbox esegue l'attivazione tramite clic come input secondario usando il pulsante "A". Il dispositivo viene mappato a un set predefinito di azioni che facilitano la navigazione all'interno del sistema e il controllo del sistema stesso. Se si vuole personalizzare il controller, usare l'applicazione Xbox Accessori per configurare il controller wireless Xbox.

![Controller wireless Xbox](images/xboxcontroller.jpg)<br>
*Controller wireless Xbox*

[Associazione di un controller Xbox al PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Puntamento con la testa e controller adattivo Xbox
Progettato principalmente per soddisfare le esigenze dei giocatori con mobilità limitata, il controller adattivo Xbox è un hub unificato per i dispositivi che semplificano l'accessibilità della realtà mista.

Il controller adattivo Xbox esegue l'attivazione di un clic come input secondario usando il pulsante "A". Il dispositivo è mappato a un set predefinito di azioni che facilitano la navigazione e il controllo del sistema. Se si vuole personalizzare il controller, usare l'applicazione Xbox Accessori per configurare il controller adattivo Xbox.

![Controller adattivo Xbox](images/xbox-adaptive-controller-devices.jpg)<br>
*Controller adattivo Xbox*

Connetti dispositivi esterni, ad esempio commutatori, pulsanti, montaggi e joystick, per creare un'esperienza di controller personalizzata univoca. Gli input Button, levetta e trigger sono controllati con dispositivi per l'accesso facilitato connessi tramite jack da 3,5 mm e porte USB.

![Porte del controller adattivo Xbox](images/xbox-adaptive-controller-ports.jpg)<br>
*Porte del controller adattivo Xbox*

[Istruzioni per associare il dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Altre informazioni disponibili sul sito Xbox</a>


## <a name="design-guidelines"></a>Linee guida per la progettazione
> [!NOTE]
> Saranno [presto disponibili](index.md) altre istruzioni di progettazione specifiche per lo sguardo fisso.

## <a name="head-gaze-targeting"></a>Selezione della destinazione mediante puntamento con la testa
Tutte le interazioni si basano sulla capacità di un utente di selezionare come destinazione l'elemento con cui vuole interagire, indipendentemente dalla modalità di input. In Windows Mixed Reality questo avviene in genere mediante lo sguardo dell'utente.
Per consentire a un utente di lavorare correttamente con un'esperienza, la conoscenza calcolata del sistema delle finalità di un utente e l'intento effettivo dell'utente devono essere allineati il più vicino possibile. Più il sistema interpreta correttamente le azioni che l'utente intende compiere, più aumenta la soddisfazione e migliorano le prestazioni.


## <a name="target-sizing-and-feedback"></a>Dimensioni della destinazione e feedback
Il vettore di sguardi è stato visualizzato ripetutamente per poter essere usato per finalità mirate, ma spesso funziona meglio per il targeting lordo, acquisendo obiettivi di dimensioni più grandi. Le dimensioni minime di destinazione da 1 a 1,5 gradi consentono azioni utente di successo nella maggior parte degli scenari, sebbene le destinazioni di 3 gradi consentano spesso una maggiore velocità. Le dimensioni che l'utente punta come destinazione corrispondono in effetti a un'area 2D persino per gli elementi 3D: qualunque proiezione vi sia di fronte deve essere l'area selezionabile come destinazione. Fornire un segnale saliente che un elemento è "attivo" (che l'utente lo sta indirizzando) è estremamente utile. Questo può includere trattamenti quali effetti "hover" visibili, evidenziazioni audio o clic oppure un chiaro allineamento di un cursore con un elemento.

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni ottimali della destinazione a una distanza di 2 metri*

![Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso](images/gazetargeting-highlighting-640px.jpg)<br>
*Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso*

## <a name="target-placement"></a>Posizionamento della destinazione
Spesso gli utenti non riescono a trovare gli elementi dell'interfaccia utente posizionati in modo molto elevato o molto basso nel proprio campo di visualizzazione, concentrando la maggior parte delle loro attenzioni sulle aree attorno al suo interesse principale, che è approssimativamente a livello di occhio. Può pertanto rivelarsi utile posizionare la maggior parte delle destinazioni in una fascia ragionevole attorno al livello degli occhi. Data la tendenza degli utenti a concentrarsi su un'area visiva relativamente limitata in un determinato momento (il cono attenzionale della visione è all'incirca di 10 gradi), il fatto di raggruppare gli elementi dell'interfaccia utente in base a come sono correlati concettualmente può dare luogo a comportamenti di concatenamento dell'attenzione da un elemento all'altro man mano che l'utente sposta lo sguardo all'interno di un'area. Quando progetti l'interfaccia utente, tieni presente la grande differenza potenziale di campo visivo tra i visori HoloLens e i visori VR immersive.

![Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Miglioramento dei comportamenti di selezione della destinazione
Se è possibile determinare o approssimarsi attentamente gli obiettivi dell'utente per la destinazione di un elemento, può essere molto utile accettare i tentativi vicini di interazione come se fossero destinati correttamente. Ecco alcuni metodi efficaci che possono essere incorporati in esperienze di realtà mista:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilizzazione del puntamento con la testa ("pozzi di gravità")
Questa operazione deve essere attivata la maggior parte o tutto il tempo. Questa tecnica elimina la natura naturale e le jittere del collo che possono essere spostate dagli utenti anche a causa di comportamenti di ricerca e di conversazione.

### <a name="closest-link-algorithms"></a>Algoritmi di collegamento più vicino
Funzionano al meglio nelle aree con contenuto interattivo sparso. Se c'è una probabilità elevata che è possibile determinare ciò che un utente ha tentato di interagire, è possibile integrare le proprie capacità di destinazione supponendo un certo livello di INTENTITà.

### <a name="backdating-and-postdating-actions"></a>Azioni di Ridata e di backdating
Questo meccanismo è utile per le attività che richiedono velocità. Quando un utente si sposta in una serie di manovre di targeting e attivazione alla velocità, è utile presupporre un certo scopo e consentire la mancata corrispondenza delle destinazioni in cui l'utente si è concentrato leggermente prima o leggermente dopo il tocco (50 ms before/after era efficace in EA test di rly).

### <a name="smoothing"></a>Definizione di movimenti uniformi
Questo meccanismo è utile per i movimenti di percorso, riducendo il lieve tremolio e le oscillazioni dovute alle caratteristiche di movimento Head naturale. Quando si smussano i movimenti del tracciato, è necessario arrotondare le dimensioni e la distanza dei movimenti anziché nel tempo.

### <a name="magnetism"></a>Magnetismo
Questo meccanismo può essere considerato come una versione più generale degli algoritmi di collegamento più vicini, ovvero disegnare un cursore verso una destinazione o semplicemente aumentare hitboxes, in modo visibile o meno, perché gli utenti si avvicinano a destinazioni potenziali utilizzando una conoscenza del layout interattivo per migliorare finalità utente di approccio. Questa soluzione può risultare particolarmente efficace per le destinazioni di piccole dimensioni.

### <a name="focus-stickiness"></a>Spostamento dello stato attivo in base all'elemento di interesse corrente
Quando si determinano gli elementi interattivi adiacenti a cui dare lo stato attivo, la viscosità dello stato attivo fornisce una distorsione all'elemento attualmente attivo. Questo consente di ridurre i comportamenti di cambio dello stato attivo quando si esegue il mobile a un punto medio tra due elementi con rumore naturale.


## <a name="composite-gestures"></a>Movimenti compositi

### <a name="air-tap"></a>Simulazione del tocco
Il gesto del rubinetto d'aria, così come gli altri movimenti riportati di seguito, reagirà solo a un tap specifico. Per rilevare altri rubinetti, ad esempio menu o afferra, l'applicazione deve usare direttamente le interazioni di livello inferiore descritte nella precedente sezione due movimenti dei componenti principali.

### <a name="tap-and-hold"></a>Tocco e pressione prolungata
La pressione prolungata consiste nel mantenere la posizione del dito abbassato della simulazione del tocco. La combinazione di tocco e mantenimento dell'aria permette una serie di interazioni di tipo "clic e trascinamento" più complesse in combinazione con lo spostamento ARM, ad esempio la selezione di un oggetto anziché l'attivazione di interazioni secondarie MouseDown, ad esempio la visualizzazione di un menu di scelta rapida.
È tuttavia consigliabile prestare attenzione durante la progettazione di questo movimento perché gli utenti possono avere la tendenza ad allentare la posizione della mano durante l'esecuzione di un movimento esteso.

### <a name="manipulation"></a>Manipolazione
I movimenti di manipolazione possono essere usati per spostare, ridimensionare o ruotare un ologramma quando si vuole che l'ologramma reagisca 1:1 ai movimenti della mano dell'utente. Uno degli usi possibili di tali movimenti 1:1 è quello di consentire all'utente di disegnare o dipingere nel mondo.
La selezione iniziale della destinazione per un movimento di manipolazione dovrebbe avvenire mediante sguardo fisso o puntamento. Una volta avviato il tocco e l'attesa, qualsiasi modifica dell'oggetto viene gestita da movimenti mano, liberando l'utente per l'aspetto durante la modifica.

### <a name="navigation"></a>Navigazione
I movimenti di navigazione funzionano come un joystick virtuale e possono essere usati per spostarsi nei widget dell'interfaccia utente, ad esempio nei menu radiali. Tocca e tieni premuto per avviare il movimento, quindi sposta la mano all'interno di un cubo 3D normalizzato, centrato attorno al punto di pressione iniziale. Puoi spostare la mano lungo l'asse X, Y o Z da un valore -1 a 1, essendo lo 0 il punto di partenza.
La navigazione può essere usata per creare movimenti continui di scorrimento o zoom basati sulla velocità, analoghi allo scorrimento di un'interfaccia utente 2D mediante il clic sul pulsante centrale del mouse e il successivo spostamento del mouse verso l'alto o il basso.

La navigazione con Rails si riferisce alla capacità di riconoscere i movimenti in determinati assi fino a quando non viene raggiunta una determinata soglia sull'asse. Questa operazione è utile solo quando lo sviluppatore sposta in più assi è abilitato in un'applicazione, ad esempio se un'applicazione è configurata in modo da riconoscere i movimenti di navigazione tra l'asse X, l'asse Y ma anche l'asse X specificato con Rails. In questo caso, il sistema rileverà i movimenti di mano sull'asse X, purché rimangano all'interno di una guida immaginaria (Guida) sull'asse X, se lo spostamento della mano si verifica anche sull'asse Y.

Nelle app 2D gli utenti possono usare movimenti di navigazione verticali per scorrere, eseguire lo zoom o trascinare all'interno dell'app. In questo modo vengono inseriti nell'app tocchi delle dita virtuali per simulare tocchi dello stesso tipo. Gli utenti possono selezionare quali di queste azioni si verificano alternando gli strumenti sulla barra sopra l'applicazione, selezionando il pulsante o dicendo "< Scroll/drag/zoom > Tool".

[Altre informazioni sui movimenti compositi](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Strumenti di riconoscimento dei movimenti

Un vantaggio dell'uso del riconoscimento dei movimenti è che è possibile configurare un riconoscimento di movimento solo per i movimenti che l'ologramma attualmente interessato può accettare. La piattaforma esegue solo la risoluzione di ambiguità, se necessario, per distinguere questi movimenti specifici supportati. In questo modo, un ologramma che supporta solo il tocco aereo può accettare qualsiasi periodo di tempo tra la pressione e il rilascio, mentre un ologramma che supporta sia tap che tenere premuto può alzare di livello il tocco a una presa dopo la soglia del tempo di attesa.

## <a name="hand-recognition"></a>Riconoscimento della mano
HoloLens riconosce i movimenti della mano tenendo traccia della posizione di una o di entrambe le mani visibili al dispositivo. HoloLens vede le mani quando sono in stato pronto (dorso della mano rivolto verso di te con il dito indice alzato) o in stato premuto (dorso della mano rivolto verso di te con il dito indice abbassato). Quando le mani si trovano in altre pose, HoloLens ignora themz.
Per ogni mano rilevato da HoloLens, è possibile accedere alla propria posizione senza orientamento e lo stato premuto. Non appena la mano si avvicina al bordo della cornice di movimento, viene fornito anche un vettore direzionale che puoi decidere di mostrare all'utente in modo che sappia come muovere la mano per riportarla dove può essere vista da HoloLens.

## <a name="gesture-frame"></a>Cornice di movimento
Per i movimenti in HoloLens, è necessario che la mano si trovi all'interno di un frame di movimento, in un intervallo che può essere visualizzato in modo appropriato dalle fotocamere con rilevamento dei movimenti, dal naso alla vita e tra le spalle. Gli utenti devono essere sottoposti a training in questa area di riconoscimento sia per l'esito positivo dell'azione sia per la loro comodità. Molti utenti presumono inizialmente che il frame di movimento debba trovarsi all'interno della propria visualizzazione tramite HoloLens e tenere le braccia invariate per interagire. Quando si usa il clicker HoloLens, non è necessario che le mani si trovino all'interno del frame di movimento.

Nel caso di movimenti continui in particolare, c'è il rischio che gli utenti sposti le loro mani al di fuori del frame di movimento mentre si trova a metà movimento quando si trasferisce un oggetto olografico, ad esempio, e si perde il risultato previsto.

Sono tre gli aspetti da considerare:

- Formazione dell'utente sull'esistenza e sui limiti approssimativi del frame di movimento. Questa operazione viene insegnata durante l'installazione di HoloLens.

- Notificare agli utenti quando i movimenti si avvicinano o interferiscono con i limiti del frame di movimento all'interno di un'applicazione fino a quando un movimento perso conduce a risultati indesiderati. La ricerca ha illustrato le qualità principali di un sistema di notifica. La shell HoloLens fornisce un esempio di questo tipo di notifica, ovvero un oggetto visivo, sul cursore centrale, che indica la direzione in cui si verifica l'attraversamento del limite.

- Necessità di ridurre al minimo le conseguenze del superamento dei limiti della cornice di movimento. In generale, ciò significa che il risultato di un movimento deve essere interrotto al limite e non invertito. Se, ad esempio, un utente sposta un oggetto olografico in una stanza, lo spostamento dovrebbe arrestarsi quando il frame del movimento viene violato e non viene restituito al punto iniziale. L'utente può riscontrare qualche frustrazione, ma potrebbe comprendere più rapidamente i limiti e non deve riavviare ogni volta le azioni desiderate.


## <a name="see-also"></a>Vedere anche
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Esecuzione di comandi vocali](voice-design.md)





