---
title: Puntamento con la testa e commit
description: Panoramica del modello di input puntamento con la testa e commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, sguardo fisso, selezione della destinazione con lo sguardo fisso, interazione, progettazione
ms.openlocfilehash: d9eae3c0cfceba7c2c31425941dfce865f3aa609
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692308"
---
# <a name="head-gaze-and-commit"></a>Puntamento con la testa e commit
Puntamento con la testa e commit è un modello di input che prevede la selezione di un oggetto come destinazione puntando avanti con la testa (direzione della testa) e agendo su di esso con un input secondario quale il movimento della mano per la simulazione del tocco o il comando vocale "Seleziona". Viene considerato un modello di input "da lontano" con manipolazione indiretta, in quanto è consigliabile usarlo per interagire con contenuto non raggiungibile nemmeno stendendo le braccia.

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
I visori VR realtà mista usano la posizione e l'orientamento della testa dell'utente per determinare il vettore di direzione della testa. Per comprendere questo concetto, pensa a un laser che punti dritto davanti partendo direttamente tra gli occhi dell'utente. Questa è una grossolana approssimazione del punto guardato dall'utente. L'applicazione è in grado di intersecare questo raggio con oggetti virtuali o del mondo reale e di disegnare un cursore in quella posizione per consentire all'utente di capire cosa sta puntando in quel momento.

Oltre al puntamento con la testa, alcuni visori VR realtà mista come HoloLens 2 includono sistemi di tracciamento oculare che producono un vettore di sguardo fisso. In questo modo si ottiene una misurazione precisa di dove sta guardando l'utente. Usando lo sguardo fisso è possibile creare interazioni basate sullo sguardo fisso e sul commit, ma in questo caso è necessario tenere conto di una serie molto diversa di vincoli di progettazione che verranno trattati separatamente nell'[articolo relativo al tracciamento oculare](eye-tracking.md).

## <a name="commit"></a>Commit
Dopo aver selezionato come destinazione un elemento dell'interfaccia utente o un oggetto, l'utente può interagire con esso o "farvi clic" usando un input secondario. Questo è il cosiddetto passaggio di commit del modello. Sono supportati i metodi di commit seguenti:

- Eseguire una simulazione del tocco
- Pronunciare il comando vocale "Seleziona" o uno dei comandi vocali specifici per la situazione
- Premere il pulsante singolo su un [dispositivo Clicker HoloLens](hardware-accessories.md#hololens-clicker)
- Premere il pulsante 'A' su un game pad Xbox
- Premere il pulsante 'A' su un controller adattivo Xbox

### <a name="head-gaze-and-air-tap-gesture"></a>Puntamento con la testa e simulazione del tocco
Per simulazione del tocco si intende un gesto tocco fatto con la mano mantenuta in verticale. Per simulare il tocco, alza il dito indice in posizione di pronto e poi avvicinalo al pollice, quindi alza di nuovo l'indice per rilasciare. In HoloLens 1 la simulazione del tocco è l'input secondario più comune.

![Dito in posizione di pronto e quindi un movimento di tocco o di clic](images/readyandpress.jpg)<br>

La simulazione del tocco è disponibile anche in HoloLens 2 e viene riconosciuta con maggiore flessibilità rispetto alla versione originaria. Ora sono supportati quasi tutti i tipi di avvicinamento delle dita, purché la mano venga mantenuta in verticale e ferma. Ciò consente agli utenti di apprendere ed eseguire più facilmente il movimento.  Questa nuova simulazione del tocco sostituisce quella precedente tramite la stessa API, pertanto le applicazioni esistenti avranno automaticamente il nuovo comportamento dopo la ricompilazione per HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Puntamento con la testa e comando vocale "Seleziona"
L'uso di comandi vocali è uno dei principali metodi di interazione nella realtà mista e offre un potente meccanismo per controllare il sistema "senza usare le mani". Sono disponibili diversi tipi di modelli di interazione vocale:

- Il comando generico "Seleziona" che consente di eseguire un "clic" oppure un commit come input secondario.
- I comandi oggetto come "Chiudi" o "Più grande" che consentono di eseguire un'azione e di effettuarne il commit come input secondario.
- I comandi globali come "Vai a Start" che non richiedono una destinazione.
- Le interfacce utente di conversazione o le entità come Cortana che hanno la capacità di usare un linguaggio naturale IA.
- Comandi personalizzati.

Per altri dettagli e un elenco completo dei comandi disponibili e di come usarli, vedi le istruzioni relative all'[esecuzione dei comandi vocali](voice-design.md).


### <a name="head-gaze-and-hololens-clicker"></a>Puntamento con la testa e dispositivo Clicker HoloLens
Il dispositivo Clicker HoloLens è la prima periferica realizzata specificamente per HoloLens e viene fornito con HoloLens 1 Development Edition. Tale dispositivo consente a un utente di fare clic con un movimento minimo della mano e di eseguire il commit come input secondario. Il dispositivo Clicker HoloLens può essere collegato a HoloLens 1 o 2 tramite Bluetooth Low Energy (BTLE).

![Dispositivo Clicker HoloLens](images/hololens-clicker-500px.jpg)<br>
*Dispositivo Clicker HoloLens*

Per altre informazioni e istruzioni su come associare il dispositivo, fai clic [qui](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Puntamento con la testa e controller wireless Xbox
Il controller wireless Xbox consente di eseguire un "clic" come input secondario mediante il pulsante A. Il dispositivo viene mappato a un set predefinito di azioni che facilitano la navigazione all'interno del sistema e il controllo del sistema stesso. Se vuoi personalizzare il controller wireless Xbox, configuralo usando l'app Accessori Xbox.

![Controller wireless Xbox](images/xboxcontroller.jpg)<br>
*Controller wireless Xbox*

[Associazione di un controller Xbox al PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Puntamento con la testa e controller adattivo Xbox
Progettato principalmente per soddisfare le esigenze dei giocatori con mobilità ridotta, il controller adattivo Xbox è un hub unificato per i dispositivi che contribuisce a rendere più accessibile la realtà mista.

Il controller adattivo Xbox consente di eseguire un "clic" come input secondario mediante il pulsante A. Il dispositivo viene mappato a un set predefinito di azioni che facilitano la navigazione all'interno del sistema e il controllo del sistema stesso. Se vuoi personalizzare il controller adattivo Xbox, configuralo usando l'app Accessori Xbox.

![Controller adattivo Xbox](images/xbox-adaptive-controller-devices.jpg)<br>
*Controller adattivo Xbox*

Collega dispositivi esterni come interruttori, pulsanti, montaggi e joystick per personalizzare l'utilizzo del controller e creare un'esperienza unicamente tua. Gli input di pulsanti, levette e grilletti sono controllati tramite dispositivi assistivi collegati tramite connettori jack da 3,5 mm e porte USB.

![Porte del controller adattivo Xbox](images/xbox-adaptive-controller-ports.jpg)<br>
*Porte del controller adattivo Xbox*

[Istruzioni per associare il dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Altre informazioni disponibili sul sito Xbox</a>


## <a name="design-guidelines"></a>Linee guida per la progettazione
> [!NOTE]
> Saranno [presto disponibili](index.md) altre istruzioni di progettazione specifiche per lo sguardo fisso.

## <a name="head-gaze-targeting"></a>Selezione della destinazione mediante puntamento con la testa
Tutte le interazioni si basano sulla capacità di un utente di selezionare come destinazione l'elemento con cui vuole interagire, indipendentemente dalla modalità di input. In Windows Mixed Reality questo avviene in genere mediante lo sguardo dell'utente.
Per consentire a un utente di usufruire con successo di un'esperienza, la comprensione dell'intenzione dell'utente calcolata dal sistema e l'effettiva intenzione dell'utente devono essere allineate il più possibile. Più il sistema interpreta correttamente le azioni che l'utente intende compiere, più aumenta la soddisfazione e migliorano le prestazioni.


## <a name="target-sizing-and-feedback"></a>Dimensioni della destinazione e feedback
In più occasioni è stato dimostrato come il vettore di sguardo fisso sia utilizzabile per selezionare con precisione la destinazione, ma spesso tale vettore funziona in modo ottimale per selezionare la destinazione con minore precisione, ovvero quando sia necessario acquisire destinazioni di dimensioni più grandi. Dimensioni minime della destinazione da 1 a 1,5 gradi dovrebbero garantire una corretta esecuzione delle azioni dell'utente nella maggior parte degli scenari, benché destinazioni di 3 gradi spesso consentano una velocità superiore. Le dimensioni che l'utente punta come destinazione corrispondono in effetti a un'area 2D persino per gli elementi 3D: qualunque proiezione vi sia di fronte deve essere l'area selezionabile come destinazione. È estremamente utile fornire un segnale che indichi quando un elemento è "attivo", ossia quando l'utente lo sta puntando come destinazione. A tale scopo, possono essere usati effetti visibili "al passaggio del puntatore", clic o evidenziazioni audio oppure il chiaro allineamento di un cursore a un elemento.

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni ottimali della destinazione a una distanza di 2 metri*

![Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso](images/gazetargeting-highlighting-640px.jpg)<br>
*Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso*

## <a name="target-placement"></a>Posizionamento della destinazione
Gli utenti spesso non riescono a trovare gli elementi dell'interfaccia utente posizionati molto in alto o molto in basso nel loro campo visivo, in quanto tendono a concentrare l'attenzione sulle aree intorno al punto focale principale, che in genere si trova approssimativamente al livello degli occhi. Può pertanto rivelarsi utile posizionare la maggior parte delle destinazioni in una fascia ragionevole attorno al livello degli occhi. Data la tendenza degli utenti a concentrarsi su un'area visiva relativamente limitata in un determinato momento (il cono attenzionale della visione è all'incirca di 10 gradi), il fatto di raggruppare gli elementi dell'interfaccia utente in base a come sono correlati concettualmente può dare luogo a comportamenti di concatenamento dell'attenzione da un elemento all'altro man mano che l'utente sposta lo sguardo all'interno di un'area. Quando progetti l'interfaccia utente, tieni presente la grande differenza potenziale di campo visivo tra i visori HoloLens e i visori VR immersive.

![Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Miglioramento dei comportamenti di selezione della destinazione
Se è possibile determinare (o approssimare con una certa precisione) l'intenzione dell'utente di selezionare un elemento come destinazione, può essere molto utile accettare i tentativi di interazione "quasi riusciti" come se avessero avuto esito positivo. Sono disponibili alcuni metodi validi che possono essere incorporati nelle esperienze di realtà mista:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilizzazione del puntamento con la testa ("pozzi di gravità")
Deve essere attivata per tutto o per la maggior parte del tempo. Questa tecnica consente di eliminare i tremolii naturali della testa o del collo che possono avere gli utenti, nonché il movimento che si produce guardando o parlando.

### <a name="closest-link-algorithms"></a>Algoritmi di collegamento più vicino
Funzionano al meglio nelle aree con contenuto interattivo sparso. Se vi è un'alta probabilità di determinare l'elemento con cui un utente stava tentando di interagire, puoi integrare le sue capacità di selezione della destinazione semplicemente presupponendo un certo livello di intenzione.

### <a name="backdatingpostdating-actions"></a>Retrodatazione o postdatazione delle azioni
Questo meccanismo è utile per le attività che richiedono velocità. Quando un utente esegue rapidamente una serie di operazioni di selezione della destinazione o di attivazione, può essere utile presupporre una certa intenzione e consentire che i passaggi mancati agiscano sulle destinazioni che l'utente aveva come obiettivo leggermente prima o dopo il tocco (50 millisecondi è stato un intervallo efficace nei primi test).

### <a name="smoothing"></a>Definizione di movimenti uniformi
Questo meccanismo è utile per i movimenti che consentono di disegnare un percorso, in quanto riduce il leggero tremolio o la lieve oscillazione dovuta alle naturali caratteristiche del movimento della testa. Quando decidi di rendere uniformi i movimenti che disegnano un percorso, uniformali in base alla loro entità o distanza anziché in base al tempo.

### <a name="magnetism"></a>Magnetismo
Questo meccanismo può essere considerato come una versione più generale degli algoritmi di "collegamento più vicino"; è possibile disegnare un cursore verso una destinazione o semplicemente aumentare le hitbox (in modo visibile o meno) man mano che gli utenti si avvicinano a probabili destinazioni, avvalendosi di una certa conoscenza del layout interattivo per avvicinarsi con maggior accuratezza all'intenzione dell'utente. Questa soluzione può risultare particolarmente efficace per le destinazioni di piccole dimensioni.

### <a name="focus-stickiness"></a>Spostamento dello stato attivo in base all'elemento di interesse corrente
Quando determini gli elementi interattivi vicini su cui spostare lo stato attivo, prediligi l'elemento su cui è attualmente concentrata l'attenzione. Ciò consentirà di ridurre i passaggi imprevedibili da un'area di interesse all'altra quando ci si trova in un punto intermedio tra due elementi con disturbi naturali.


## <a name="composite-gestures"></a>Movimenti compositi
Le app sono in grado di riconoscere molto più dei singoli tocchi. Combinando il tocco, la pressione prolungata e il rilascio con il movimento della mano, possono essere eseguiti movimenti compositi più complessi. Questi movimenti compositi o di alto livello si basano sui dati di input spaziali di basso livello (provenienti dalla simulazione del tocco e dall'apertura della mano a fiore) a cui hanno accesso gli sviluppatori.

### <a name="air-tap"></a>Simulazione del tocco
La simulazione del tocco (come gli altri movimenti descritti di seguito) reagisce solo a un tocco specifico. Per rilevare altri tocchi, come Menu o Afferra, l'app deve usare direttamente le interazioni di livello più basso descritte nella sezione precedente relativa ai due movimenti componente chiave.

### <a name="tap-and-hold"></a>Tocco e pressione prolungata
La pressione prolungata consiste nel mantenere la posizione del dito abbassato della simulazione del tocco. La combinazione della simulazione del tocco e della pressione prolungata rende possibile una serie di interazioni più complesse di tipo "fare clic e trascinare" se usata insieme al movimento del braccio (ad esempio, per raccogliere un oggetto invece di attivarlo) oppure consente interazioni secondarie di tipo "premere il pulsante del mouse" (ad esempio, per visualizzare un menu di scelta rapida).
È tuttavia consigliabile prestare attenzione durante la progettazione di questo movimento perché gli utenti possono avere la tendenza ad allentare la posizione della mano durante l'esecuzione di un movimento esteso.

### <a name="manipulation"></a>Manipolazione
I movimenti di manipolazione possono essere usati per spostare, ridimensionare o ruotare un ologramma quando vuoi che quest'ultimo reagisca con un rapporto 1:1 ai movimenti della mano dell'utente. Uno degli usi possibili di tali movimenti 1:1 è quello di consentire all'utente di disegnare o dipingere nel mondo.
La selezione iniziale della destinazione per un movimento di manipolazione dovrebbe avvenire mediante sguardo fisso o puntamento. Quando inizia la sequenza tocco e pressione prolungata, qualunque manipolazione dell'oggetto viene gestita dai movimenti della mano, consentendo all'utente di guardarsi intorno mentre esegue la manipolazione.

### <a name="navigation"></a>Navigazione
I movimenti di navigazione funzionano come un joystick virtuale e possono essere usati per spostarsi nei widget dell'interfaccia utente, ad esempio nei menu radiali. Tocca e tieni premuto per avviare il movimento, quindi sposta la mano all'interno di un cubo 3D normalizzato, centrato attorno al punto di pressione iniziale. Puoi spostare la mano lungo l'asse X, Y o Z da un valore -1 a 1, essendo lo 0 il punto di partenza.
La navigazione può essere usata per creare movimenti continui di scorrimento o zoom basati sulla velocità, analoghi allo scorrimento di un'interfaccia utente 2D mediante il clic sul pulsante centrale del mouse e il successivo spostamento del mouse verso l'alto o il basso.

Per navigazione con binari si intende la capacità di riconoscere i movimenti su un determinato asse fino al raggiungimento di una certa soglia sullo stesso asse. Ciò è utile quando lo sviluppatore abilita lo spostamento su più di un asse in un'applicazione, ad esempio se l'applicazione è configurata per riconoscere i movimenti di navigazione sugli assi X e Y, ma viene specificato anche l'asse X con binari. In questo caso il sistema riconoscerà i movimenti della mano sull'asse X finché rimangono entro binari (guida) immaginari sull'asse X, se il movimento della mano ha luogo anche sull'asse Y.

Nelle app 2D gli utenti possono usare movimenti di navigazione verticali per scorrere, eseguire lo zoom o trascinare all'interno dell'app. In questo modo vengono inseriti nell'app tocchi delle dita virtuali per simulare tocchi dello stesso tipo. Gli utenti possono selezionare quali di queste azioni eseguire muovendosi tra gli strumenti sulla barra al di sopra dell'app, facendo clic sul pulsante o dicendo "Strumento <Scorri/Trascina/Zoom>".

[Altre informazioni sui movimenti compositi](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Strumenti di riconoscimento dei movimenti

Uno dei vantaggi derivanti dall'uso del riconoscimento dei movimenti è poter configurare uno strumento di riconoscimento solo per i movimenti che l'ologramma attualmente selezionato come destinazione può accettare. La piattaforma eseguirà esclusivamente la disambiguazione necessaria per distinguere i movimenti supportati specifici. In questo modo, un ologramma che supporta solo la simulazione del tocco può accettare che trascorra un intervallo di tempo di qualunque durata tra la pressione e il rilascio, mentre un ologramma che supporta sia il tocco che la pressione prolungata può trasformare il tocco in pressione prolungata dopo il superamento della soglia temporale per la pressione prolungata.

## <a name="hand-recognition"></a>Riconoscimento della mano
HoloLens riconosce i movimenti della mano tenendo traccia della posizione di una o di entrambe le mani visibili al dispositivo. HoloLens vede le mani quando sono in stato pronto (dorso della mano rivolto verso di te con il dito indice alzato) o in stato premuto (dorso della mano rivolto verso di te con il dito indice abbassato). Quando le mani sono in altre posizioni, vengono ignorate da HoloLens.
Per ogni mano rilevata da HoloLens, puoi accedere alla sua posizione (senza orientamento) e allo stato premuto. Non appena la mano si avvicina al bordo della cornice di movimento, viene fornito anche un vettore direzionale che puoi decidere di mostrare all'utente in modo che sappia come muovere la mano per riportarla dove può essere vista da HoloLens.

## <a name="gesture-frame"></a>Cornice di movimento
Per i movimenti in HoloLens, la mano deve trovarsi all'interno di una "cornice di movimento", in un'area che possa essere vista adeguatamente dalle videocamere di rilevamento dei movimenti (approssimativamente un'area che va dal naso alla vita e che si estende tra le spalle). Gli utenti devono essere addestrati a usare quest'area di riconoscimento sia per la corretta esecuzione delle operazioni sia per il loro comfort (molti di essi inizialmente presumeranno che la cornice di movimento debba essere all'interno della visualizzazione attraverso HoloLens e terranno scomodamente le braccia alzate per interagire). Quando usi il dispositivo Clicker HoloLens, non è necessario che le tue mani si trovino all'interno della cornice di movimento.

Soprattutto nel caso di movimenti che continuano, vi è il rischio che gli utenti portino le mani al di fuori della cornice di movimento quando l'operazione non è ancora completata (ad esempio, mentre spostano un oggetto olografico), non riuscendo quindi a ottenere il risultato desiderato.

Sono tre gli aspetti da considerare:

- Necessità di formare l'utente in merito all'esistenza della cornice di movimento e ai relativi limiti approssimativi (formazione tenuta durante l'installazione di HoloLens).

- Necessità di notificare agli utenti quando con i loro movimenti si stanno avvicinando o stanno superando i limiti della cornice di movimento all'interno di un'applicazione, in quanto un movimento andato perduto può generare risultati indesiderati. Le ricerche svolte hanno mostrato i principali vantaggi di un tale sistema di notifica e la shell HoloLens ne costituisce un buon esempio (notifica visiva, sul cursore centrale, che indica la direzione in cui si sta oltrepassando il limite).

- Necessità di ridurre al minimo le conseguenze del superamento dei limiti della cornice di movimento. Questo, in generale, significa che il risultato di un movimento deve arrestarsi in corrispondenza del limite, ma non essere annullato. Ad esempio, se un utente sta spostando un oggetto olografico all'interno di una stanza, lo spostamento deve essere arrestato quando la cornice di movimento viene oltrepassata, ma l'oggetto non deve essere riportato al punto di partenza. L'utente può sentirsi frustrato in questo caso, ma può rendersi conto più rapidamente dei limiti senza dover ricominciare ogni volta a eseguire per intero le azioni desiderate.


## <a name="see-also"></a>Vedi anche
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Esecuzione di comandi vocali](voice-design.md)





