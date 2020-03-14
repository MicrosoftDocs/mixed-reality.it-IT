---
title: Sguardo e commit
description: Panoramica generale del modello di input "sguardo e commit", che usa l'input occhio o Head.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, targeting, interazione, progettazione, rilevamento degli sguardi, rilevamento Head
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375848"
---
# <a name="gaze-and-commit"></a>Sguardo e commit

_Sguardi e commit_ sono un modello di input fondamentale che è strettamente correlato al modo in cui si interagisce con i computer usando il mouse: _Point & fare clic su_.
In questa pagina vengono introdotti due tipi di input di sguardi (occhio e sguardo) e diversi tipi di azioni di commit. 
_Sguardi e commit_ sono considerati un modello di input molto lungo con manipolazione indiretta.
Ciò significa che è preferibile usare per interagire con contenuto olografico non raggiunto.

Gli auricolari per la realtà mista possono usare la posizione e l'orientamento dell'intestazione dell'utente per determinare il vettore di direzione della direzione. Per comprendere questo concetto, pensa a un laser che punti dritto davanti partendo direttamente tra gli occhi dell'utente. Questa è una grossolana approssimazione del punto guardato dall'utente. L'applicazione può intersecare questo raggio con oggetti virtuali o reali e creare un cursore in tale posizione per consentire all'utente di conoscere gli elementi attualmente destinati.

Oltre al controllo, alcuni auricolari con realtà mista, ad esempio HoloLens 2, includono sistemi di rilevamento degli occhi che producono un vettore di sguardi oculari. In questo modo si ottiene una misurazione precisa di dove sta guardando l'utente. In entrambi i casi, lo sguardo rappresenta un segnale importante per lo scopo dell'utente. Maggiore è il sistema in grado di interpretare e prevedere le azioni previste dall'utente, gli aumenti di soddisfazione degli utenti e migliorare le prestazioni.

Di seguito sono riportati alcuni esempi di come uno sviluppatore di realtà mista può trarre vantaggio da un occhio d'occhio:
* L'app può intersecare sguardi con gli ologrammi nella scena per determinare il punto in cui l'attenzione dell'utente è (più precisa con occhio).
* L'app può effettuare il canale di movimenti e pressioni del controller in base allo sguardo dell'utente, consentendo all'utente di selezionare, attivare, acquisire, scorrere o interagire in altro modo con i propri ologrammi.
* L'app può consentire all'utente di posizionare gli ologrammi su superfici reali intersecando il raggio di sguardi con la mesh di mapping spaziale.
* L'app può sapere quando l'utente *non* sta osservando la direzione di un oggetto importante, che può portare l'app a fornire suggerimenti visivi e audio per la rotazione verso tale oggetto.

<br>


## <a name="device-support"></a>Supporto per i dispositivi

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e commit</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</td>
        <td>➕ Opzione alternativa</td>
    </tr>
         <tr>
        <td>Sguardo fisso e commit</td>
        <td>❌ non disponibile</td>
        <td>✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</td>
        <td>❌ non disponibile</td>
    </tr>
</table>


## <a name="gaze"></a>Sguardo fisso

### <a name="eye--or-head-gaze"></a>Occhio o Head-sguardi?
Ci sono diverse considerazioni da tenere in considerazione quando si affronta la domanda se è necessario usare il modello di input "sguardo e commit" o "Head-sguardi e commit". Se si sta sviluppando per un auricolare immersivo o HoloLens (1st Gen), la scelta è semplice: Head-sguardi e commit. Se si sta sviluppando per HoloLens 2, la scelta diventa leggermente più difficile ed è per questo motivo che è importante comprendere i vantaggi e le difficoltà che derivano da ognuno di essi.
Nella tabella riportata di seguito sono stati compilati alcuni Pro e con le versioni precedenti per confrontare Head-vs. Eye-sguardi targeting. Questo è molto più completo e si consiglia di saperne di più sugli sguardi mirati in realtà mista:
* [Eye tracking on HoloLens 2](eye-tracking.md): introduzione generale della nuova funzionalità di rilevamento degli occhi in HoloLens 2, incluse alcune istruzioni per gli sviluppatori. 
* [Interazione con gli sguardi oculari](eye-gaze-interaction.md): considerazioni sulla progettazione e consigli per la pianificazione dell'uso del rilevamento degli occhi come input.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>Targeting degli sguardi</strong></td>
        <td><strong>Targeting mirato</strong></td>
    </tr>
    <tr>
        <td>Veloce!</td>
        <td>Più lento</td>
    </tr>
    <tr>
        <td>Impegno minimo (a malapena tutti i movimenti del corpo necessari)</td>
        <td>Può essere faticoso, possibile disagio (ad esempio, Strain Neck)</td>
    </tr>
    <tr>
        <td>Non richiede un cursore, ma è consigliabile un feedback sottile</td>
        <td>Richiede che mostri un cursore</td>
    </tr>
    <tr>
        <td>Nessun movimento degli occhi, ad esempio, non adatto per il disegno</td>
        <td>Maggiore controllo ed esplicito</td>
    </tr>
    <tr>
        <td>Difficile per gli obiettivi molto piccoli (ad esempio, piccoli pulsanti o collegamenti weblink)</td>
        <td>Affidabile! Ottimo fallback.</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

Indipendentemente dal fatto che il modello di input con sguardo e commit venga usato per il modello di input con sguardo e commit, viene usato con diversi insiemi di vincoli di progettazione, che verranno trattati separatamente negli articoli sugli sguardi [e sui commit](gaze-and-commit-eyes.md) e sugli sguardi e sui [commit](gaze-and-commit-head.md) .

<br>

---

### <a name="cursor"></a>Cursore

:::row:::
    :::column:::
        Per lo sguardo a capo, la maggior parte delle app deve usare un [cursore](cursors.md) (o altre indicazioni visive/visive) per fornire all'utente la confidenza con cui si sta per interagire. In genere, il cursore viene posizionato in tutto il mondo in cui il raggio di sguardo principale interseca un oggetto, che può essere un ologramma o una superficie reale.<br>
        <br>
        Per gli occhi, in genere è consigliabile *non* mostrare un cursore, in quanto questa operazione può diventare rapidamente distrazione e fastidioso per l'utente. È invece possibile evidenziare leggermente le destinazioni visive o usare un cursore occhio molto debole per fornire informazioni su ciò che l'utente sta per interagire. Per altre informazioni, vedere le [linee guida di progettazione per l'input basato su occhi](eye-tracking.md) su HoloLens 2.
    :::column-end:::
        :::column:::
       ![un cursore visivo di esempio per mostrare lo sguardo](images/cursor.jpg)<br>
       *Image: un cursore visivo di esempio per mostrare lo sguardo*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
Quando _si parla di diversi_ modi per esaminare una destinazione, è possibile approfondire la parte relativa al _commit_ nello _sguardo e nel commit_.
Dopo la destinazione di un oggetto o di un elemento dell'interfaccia utente, l'utente può interagire o fare clic su di esso usando un input secondario. Questa operazione è nota come passaggio di commit del modello di input. 

Sono supportati i metodi di commit seguenti:
- Gesto della mano del rubinetto d'aria (ad esempio, alzare la mano davanti all'utente e riunire il dito e il pollice dell'indice)
- Pronunciare _"Select"_ o uno dei comandi vocali di destinazione
- Premere un solo pulsante su un [clic del HoloLens](hardware-accessories.md#hololens-clicker)
- Premere il pulsante ' A ' in un gamepad Xbox
- Premere il pulsante "A" in un controller adattivo Xbox

### <a name="gaze-and-air-tap-gesture"></a>Gesto dello sguardo e del tocco aereo
Per simulazione del tocco si intende un gesto tocco fatto con la mano mantenuta in verticale. Per eseguire un rubinetto aereo, aumentare il dito dell'indice nella posizione pronta, quindi pizzicare il cursore e aumentare il dito dell'indice fino al rilascio. In HoloLens (1a generazione), il rubinetto aereo è l'input secondario più comune.


:::row:::
    :::column:::
       ![dito nella posizione pronta](images/readyandpress-ready.jpg)<br>
       **Dito nella posizione pronta**<br>
    :::column-end:::
    :::column:::
       ![premere il dito per toccare o fare clic su](images/readyandpress-press.jpg)<br>
        **Premere il tasto dito per toccare o fare clic su**<br>
    :::column-end:::
:::row-end:::


Il rubinetto aereo è disponibile anche in HoloLens 2. È stato rilassato dalla versione originale. Quasi tutti i tipi di Pinch sono ora supportati finché la mano è eretta e mantiene ancora. Ciò consente agli utenti di apprendere ed eseguire più facilmente il movimento. Questo nuovo tocco sostituisce quello precedente tramite la stessa API, in modo che le applicazioni esistenti avranno automaticamente il nuovo comportamento dopo la ricompilazione per HoloLens 2.

<br>

---

### <a name="gaze-and-select-voice-command"></a>Sguardo e "Select" (comando vocale)
Il comando Voice è uno dei metodi di interazione principali in realtà mista. Fornisce un meccanismo senza intervento pratico per controllare il sistema. Esistono diversi tipi di modelli di interazione vocale:

- Comando "Select" generico che esegue l'attivazione di un clic o il commit come input secondario.
- I comandi dell'oggetto, ad esempio "close" o "make it Bigger", eseguono ed eseguono il commit in un'azione come input secondario.
- I comandi globali (ad esempio, "go to Start") non richiedono una destinazione.
- Le interfacce utente di conversazione o entità come Cortana hanno una funzionalità del linguaggio di intelligenza artificiale.
- Comandi vocali personalizzati

Per altre informazioni e per un elenco completo dei comandi vocali disponibili e per informazioni su come usarli, vedere la guida per i comandi [vocali](voice-design.md) .

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Clicker sguardi e HoloLens

:::row:::
    :::column:::
        Il HoloLens clic è il primo dispositivo periferico creato in modo specifico per HoloLens. È incluso in HoloLens (1st Gen) Development Edition. Il clicker HoloLens consente a un utente di fare clic con movimento minimo e di eseguire il commit come input secondario. Il HoloLens Clicker si connette a HoloLens (1st Gen) o HoloLens 2 usando Bluetooth Low Energy (BTLE).<br>
        <br>
        [Altre informazioni e istruzioni per associare il dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Immagine: HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens clic](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>Guarda e controller wireless Xbox

:::row:::
    :::column:::
        Il controller wireless Xbox esegue l'attivazione tramite clic come input secondario usando il pulsante "A". Il dispositivo è mappato a un set predefinito di azioni che facilitano la navigazione e il controllo del sistema. Se si vuole personalizzare il controller, usare l'applicazione Xbox Accessori per configurare il controller wireless Xbox.<br>
        <br>
        [Come associare un controller Xbox al PC](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Immagine: controller wireless Xbox*
    :::column-end:::
        :::column:::
       ![Controller wireless Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>Sguardo e controller adattivo Xbox
Progettato principalmente per soddisfare le esigenze dei giocatori con mobilità limitata, il controller adattivo Xbox è un hub unificato per i dispositivi che semplificano l'accessibilità della realtà mista.

Il controller adattivo Xbox esegue l'attivazione di un clic come input secondario usando il pulsante "A". Il dispositivo è mappato a un set predefinito di azioni che facilitano la navigazione e il controllo del sistema. Se si vuole personalizzare il controller, usare l'applicazione Xbox Accessori per configurare il controller adattivo Xbox.

![Controller adattivo Xbox](images/xbox-adaptive-controller-devices.jpg)<br>
*Controller adattivo Xbox*

Connetti dispositivi esterni, ad esempio commutatori, pulsanti, montaggi e joystick, per creare un'esperienza di controller personalizzata univoca. Gli input Button, levetta e trigger sono controllati con dispositivi per l'accesso facilitato connessi tramite jack da 3,5 mm e porte USB.

![Porte del controller adattivo Xbox](images/xbox-adaptive-controller-ports.jpg)<br>
*Porte del controller adattivo Xbox*

[Istruzioni per associare il dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Altre informazioni disponibili sul sito Xbox</a>

<br>

---

## <a name="composite-gestures"></a>Movimenti compositi

### <a name="air-tap"></a>Simulazione del tocco
Il gesto del rubinetto d'aria, così come gli altri movimenti riportati di seguito, reagirà solo a un tap specifico. Per rilevare altri rubinetti, ad esempio menu o afferra, l'applicazione deve usare direttamente le interazioni di livello inferiore descritte nella precedente sezione due movimenti dei componenti principali.

### <a name="tap-and-hold"></a>Tocco e pressione prolungata
La pressione prolungata consiste nel mantenere la posizione del dito abbassato della simulazione del tocco. La combinazione di tocco e mantenimento dell'aria permette una serie di interazioni di tipo "clic e trascinamento" più complesse in combinazione con lo spostamento ARM, ad esempio la selezione di un oggetto anziché l'attivazione di interazioni secondarie MouseDown, ad esempio la visualizzazione di un menu di scelta rapida.
È tuttavia consigliabile prestare attenzione durante la progettazione di questo movimento perché gli utenti possono avere la tendenza ad allentare la posizione della mano durante l'esecuzione di un movimento esteso.

### <a name="manipulation"></a>Manipulation
I movimenti di manipolazione possono essere usati per spostare, ridimensionare o ruotare un ologramma quando si vuole che l'ologramma reagisca 1:1 ai movimenti della mano dell'utente. Uno degli usi possibili di tali movimenti 1:1 è quello di consentire all'utente di disegnare o dipingere nel mondo.
La selezione iniziale della destinazione per un movimento di manipolazione dovrebbe avvenire mediante sguardo fisso o puntamento. Una volta avviato il tocco e l'attesa, qualsiasi modifica dell'oggetto viene gestita da movimenti mano, liberando l'utente per l'aspetto durante la modifica.

### <a name="navigation"></a>Navigazione
I movimenti di navigazione funzionano come un joystick virtuale e possono essere usati per spostarsi nei widget dell'interfaccia utente, ad esempio nei menu radiali. Tocca e tieni premuto per avviare il movimento, quindi sposta la mano all'interno di un cubo 3D normalizzato, centrato attorno al punto di pressione iniziale. Puoi spostare la mano lungo l'asse X, Y o Z da un valore -1 a 1, essendo lo 0 il punto di partenza.
La navigazione può essere usata per creare movimenti continui di scorrimento o zoom basati sulla velocità, analoghi allo scorrimento di un'interfaccia utente 2D mediante il clic sul pulsante centrale del mouse e il successivo spostamento del mouse verso l'alto o il basso.

La navigazione con Rails si riferisce alla capacità di riconoscere i movimenti in determinati assi fino a quando non viene raggiunta una determinata soglia sull'asse. Questa operazione è utile solo quando lo sviluppatore sposta in più assi è abilitato in un'applicazione, ad esempio se un'applicazione è configurata in modo da riconoscere i movimenti di navigazione tra l'asse X, l'asse Y ma anche l'asse X specificato con Rails. In questo caso, il sistema rileverà i movimenti di mano sull'asse X, purché rimangano all'interno di una guida immaginaria (Guida) sull'asse X, se lo spostamento della mano si verifica anche sull'asse Y.

Nelle app 2D gli utenti possono usare movimenti di navigazione verticali per scorrere, eseguire lo zoom o trascinare all'interno dell'app. In questo modo vengono inseriti nell'app tocchi delle dita virtuali per simulare tocchi dello stesso tipo. Gli utenti possono selezionare quali di queste azioni si verificano alternando gli strumenti sulla barra sopra l'applicazione, selezionando il pulsante o dicendo "< Scroll/drag/zoom > Tool".

[Altre informazioni sui movimenti compositi](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>Strumenti di riconoscimento dei movimenti

Un vantaggio dell'uso del riconoscimento dei movimenti è che è possibile configurare un riconoscimento di movimento solo per i movimenti che l'ologramma attualmente interessato può accettare. La piattaforma esegue solo la risoluzione di ambiguità, se necessario, per distinguere questi movimenti specifici supportati. In questo modo, un ologramma che supporta solo il tocco aereo può accettare qualsiasi periodo di tempo tra la pressione e il rilascio, mentre un ologramma che supporta sia tap che tenere premuto può alzare di livello il tocco a una presa dopo la soglia del tempo di attesa.

## <a name="hand-recognition"></a>Riconoscimento della mano
HoloLens riconosce i movimenti della mano tenendo traccia della posizione di una o di entrambe le mani visibili al dispositivo. HoloLens vede le mani quando sono in stato pronto (dorso della mano rivolto verso di te con il dito indice alzato) o in stato premuto (dorso della mano rivolto verso di te con il dito indice abbassato). Quando le mani si trovano in altre pose, HoloLens le ignora.
Per ogni mano rilevato da HoloLens, è possibile accedere alla propria posizione senza orientamento e lo stato premuto. Non appena la mano si avvicina al bordo della cornice di movimento, viene fornito anche un vettore direzionale che puoi decidere di mostrare all'utente in modo che sappia come muovere la mano per riportarla dove può essere vista da HoloLens.

## <a name="gesture-frame"></a>Cornice di movimento
Per i movimenti in HoloLens, è necessario che la mano si trovi all'interno di un frame di movimento, in un intervallo che può essere visualizzato in modo appropriato dalle fotocamere con rilevamento dei movimenti, dal naso alla vita e tra le spalle. Gli utenti devono essere sottoposti a training in questa area di riconoscimento sia per l'esito positivo dell'azione sia per la loro comodità. Molti utenti presumono inizialmente che il frame di movimento debba trovarsi all'interno della propria visualizzazione tramite HoloLens e tenere le braccia invariate per interagire. Quando si usa il clicker HoloLens, non è necessario che le mani si trovino all'interno del frame di movimento.

Nel caso di movimenti continui in particolare, c'è il rischio che gli utenti sposti le loro mani al di fuori del frame di movimento mentre si trova a metà movimento quando si trasferisce un oggetto olografico, ad esempio, e si perde il risultato previsto.

Sono tre gli aspetti da considerare:

- Formazione dell'utente sull'esistenza e sui limiti approssimativi del frame di movimento. Questa operazione viene insegnata durante l'installazione di HoloLens.

- Notificare agli utenti quando i movimenti si avvicinano o interferiscono con i limiti del frame di movimento all'interno di un'applicazione fino a quando un movimento perso conduce a risultati indesiderati. La ricerca ha illustrato le qualità principali di un sistema di notifica. La shell HoloLens fornisce un esempio di questo tipo di notifica, ovvero un oggetto visivo, sul cursore centrale, che indica la direzione in cui si verifica l'attraversamento del limite.

- Necessità di ridurre al minimo le conseguenze del superamento dei limiti della cornice di movimento. In generale, ciò significa che il risultato di un movimento deve essere interrotto al limite e non invertito. Se, ad esempio, un utente sposta un oggetto olografico in una stanza, lo spostamento dovrebbe arrestarsi quando il frame del movimento viene violato e non viene restituito al punto iniziale. L'utente può riscontrare qualche frustrazione, ma potrebbe comprendere più rapidamente i limiti e non deve riavviare ogni volta le azioni desiderate.



## <a name="see-also"></a>Vedere anche
* [Interazione basata sullo sguardo](eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)

