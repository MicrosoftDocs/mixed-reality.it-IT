---
title: Head-sguardo ed eseguire il commit
description: Panoramica del modello di input sguardo di inizio e commit
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: Progettare sguardo, sguardo targeting, interazione, realtà mista
ms.openlocfilehash: a84465de3479bf3da2131b94dd522539cd7de6e9
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974871"
---
# <a name="head-gaze-and-commit"></a>Head-sguardo ed eseguire il commit
Head-sguardo ed eseguire il commit è un modello di input che coinvolge destinato a un oggetto con direzione di inizio in avanti che punta (head-direction) e quindi agisce su di esso con una replica secondaria di input, ad il movimento mano Air toccare o voce di comando "Select". Viene considerato un modello di input "molto" con manipolazione indiretta, ovvero che viene utilizzato meglio per l'interazione con contenuto che è di là arms raggiungere.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Head-sguardo ed eseguire il commit</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato (in terza scelta - <a href="interaction-fundamentals.md">vedere le altre opzioni</a>)</td>
        <td>Opzione alternativa ➕</td>
    </tr>
</table>

## <a name="head-gaze"></a>Head-sguardo
Realtà mista auricolari usano la posizione e l'orientamento della testina dell'utente per determinare il vettore di direzione head. È possibile considerare questo come il laser che faccia riferimento dritto dal direttamente tra gli occhi dell'utente. Si tratta di un piuttosto grossolana approssimazione di dove sta guardando l'utente. L'applicazione possa interseca il raggio con oggetti reali o virtuali e creare un cursore in tale posizione per consentire all'utente di sapere che cosa sono in uso.

Oltre a head sguardo, alcuni auricolari realtà mista, ad esempio le 2 HoloLens includono sotto controllo i sistemi che producono un vettore visiva di rilevamento. Ciò fornisce una misura con granularità fine del dove sta guardando l'utente. È possibile compilare sguardo ed eseguire il commit le interazioni tramite sguardo sotto controllo, ma ciò comporta un set di vincoli di progettazione, che verranno trattati separatamente in molto diverso il [occhio rilevamento articolo](eye-tracking.md).

## <a name="commit"></a>Eseguire il commit
Dopo la destinazione è un oggetto o un elemento dell'interfaccia utente, l'utente può interagire o "click" su di essa utilizzando input secondari. Questo è noto come il passaggio di commit del modello. Sono supportati i seguenti metodi di commit:

- Movimento dell'indice puntato
- Pronunciare il comando vocale "Select" o uno dei comandi vocali destinazione
- Fare clic sul pulsante singolo un [HoloLens Clicker](hardware-accessories.md#hololens-clicker)
- Fare clic sul pulsante 'A' su un Xbox Gamepad
- Fare clic sul pulsante 'A' in un Controller adattivo Xbox

### <a name="head-gaze-and-air-tap-gesture"></a>Head-sguardo e aria gesto tocco
Indice puntato è un gesto tocco con l'icona della mano mantenuto in verticale. Per eseguire l'indice puntato, generare il dito indice nella posizione pronto, quindi avvicinare le dita con il controllo thumb e generare il dito indice eseguire il backup per rilasciare. In 1 HoloLens, indice puntato è l'input secondario più comune.

![Con un dito nella posizione pronta e quindi un movimento toccare o fare clic su](images/readyandpress.jpg)<br>

Indice puntato è disponibile anche su HoloLens 2 e è stato aumentato dalla versione originale. Quasi tutti i tipi di pinches sono ora supportati, fino a quando l'icona della mano è verticale e ha ancora. Questo rende molto più semplice per gli utenti apprendere e di eseguire il movimento.  Questo nuovo indice puntato sostituisca il precedente tramite l'API stessa, in modo che le applicazioni esistenti otterranno automaticamente il nuovo comportamento dopo la ricompilazione per HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Head-sguardo e "Selezionare" vocali comando
L'esecuzione di comandi vocali è uno dei metodi di interazione principale nella realtà mista. Fornisce un meccanismo molto potente "Mani libero" per controllare il sistema. Sono disponibili tipi differente di modelli di interazione vocale:

- Il comando generico "Select" che consente di eseguire un "fare clic su" azionamento o commit come input secondari.
- Comandi dell'oggetto, ad esempio "Chiudi" o "Ingrandirlo" che consente di eseguire ed eseguire il commit a un'azione come input secondari.
- File globali, ad esempio "Torna all'inizio" che non richiedono una destinazione.
- Interfacce utente conversazione o entità, come Cortana dotati di una funzionalità del linguaggio naturale per intelligenza artificiale.
- File personalizzato

Per trovare altri dettagli e un elenco di comprenhesive di comandi disponibili e sul relativo utilizzo, consultare il [l'esecuzione di comandi vocali](voice-design.md) indicazioni.


### <a name="head-gaze-and-hololens-clicker"></a>Head-sguardo e HoloLens Clicker
Il HoloLens Clicker è il primo dispositivo periferico creato appositamente per HoloLens e viene fornita con la versione di sviluppo di HoloLens 1. Il HoloLens Clicker consente all'utente di fare clic su con movimento manuale minimo ed eseguire il commit come input secondari. Il clicker HoloLens si connette a HoloLens 1 o 2 tramite Bluetooth Low Energy (BTLE).

![](images/hololens-clicker-500px.jpg)<br>
HoloLens Clicker

Sono disponibili altre informazioni e istruzioni per associare il dispositivo [qui](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Head-sguardo e Controller Xbox Wireless
Il Controller Wireless Xbox consente l'esecuzione di un azionamento "fare clic su" come database secondario con il pulsante di input. Il dispositivo viene mappato a un set predefinito di azioni che consentono di esplorare e controllo del sistema. Se si desidera personalizzare il controller, usare l'App di Accesories Xbox per configurare il Controller Wireless Xbox.

![](images/xboxcontroller.jpg)<br>
Controller Xbox Wireless

[Associazione di un controller Xbox con il PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Controller adattivo head sguardo e Xbox
Progettato principalmente per soddisfare le esigenze dei giocatori con difficoltà, il Controller di Adaptive Xbox è un hub unificato per i dispositivi che consente di rendere più accessibile realtà mista.

Il Controller adattivo Xbox consente l'esecuzione di un azionamento "fare clic su" come un database secondario con il pulsante di input. Il dispositivo viene mappato a un set predefinito di azioni che consentono di esplorare e controllo del sistema. Se si desidera personalizzare il controller, usare l'App di Accesories Xbox per configurare il Controller adattivo Xbox.

![](images/xbox-adaptive-controller-devices.jpg)<br>
Controller adattivo Xbox

Connetti i dispositivi esterni, ad esempio commutatori, pulsanti, punti di montaggio e joystick per creare un'esperienza personalizzata controller che ricade sul cliente in modo univoco. Pulsante, thumbstick e trigger di input vengono controllate con tecnologie e dispositivi connessi tramite jack mm 3.5 e le porte USB.

![](images/xbox-adaptive-controller-ports.jpg)<br>
Porta Controller adattivo Xbox

[Istruzioni per associare il dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Altre informazioni disponibili sul sito Xbox</a>


# <a name="head-gaze-design-guidelines"></a>Linee guida di progettazione head sguardo
> [!NOTE]
> Informazioni aggiuntive specifiche di progettazione estasiati [presto](index.md).

## <a name="head-gaze-targeting"></a>Head-sguardo targeting
Tutte le interazioni vengono compilate al momento la possibilità di un utente di destinazione l'elemento a cui che si desidera interagire, indipendentemente dalla modalità di input. Realtà mista di Windows, questa operazione viene in genere eseguita usando sguardo dell'utente.
Per consentire agli utenti un'esperienza di corretto funzionamento, comprensione calcolata del sistema della finalità dell'utente e l'intenzione dell'utente effettivo, deve essere allineati quanto più vicina. Al grado che il sistema interpreta le azioni dell'utente desiderato correttamente, le prestazioni e aumenta la soddisfazione migliora.


## <a name="target-sizing-and-feedback"></a>Commenti e suggerimenti e le dimensioni di destinazione
Il vettore sguardo è stato dimostrato ripetutamente per poter essere usato per specificare come destinazione bene, ma spesso è adatto per gross targeting (acquisizione leggermente maggiori destinazioni). Le dimensioni di destinazione minimo di 1 a 1.5 gradi devono consentire le azioni dell'utente ha esito positivo nella maggior parte degli scenari, anche se le destinazioni di gradi 3 spesso consentono maggiore velocità. Si noti che le dimensioni che le destinazioni degli utenti in modo efficace è un'area 2D anche per gli elementi 3D, qualunque proiezione è rivolta essi devono essere l'area definibili come destinazione. Fornendo alcune salienti della segnalazione che un elemento è "active" (che l'utente è destinato a si) è molto utile: può trattarsi di trattamenti come effetti visibili "mouse", evidenzia audio o fa clic su, o cancellare l'allineamento di un cursore con un elemento.

![Dimensioni di destinazione ottimale a distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni di destinazione ottimale a distanza di 2 metri*

![Un esempio di evidenziazione di un oggetto di destinazione sguardo](images/gazetargeting-highlighting-640px.jpg)<br>
*Un esempio di evidenziazione di un oggetto di destinazione sguardo*

## <a name="target-placement"></a>Selezione host di destinazione
Gli utenti spesso riuscirà a trovare gli elementi dell'interfaccia utente che vengono posizionati in modo molto elevato o molto bassa nel loro campo visivo, concentrandosi la maggior parte dei loro attenzione sulle aree intorno a loro lo stato attivo principale (in genere circa livello rossi). Consente l'inserimento di quasi tutte le destinazioni in alcune fuori banda ragionevole intorno a livello di attenzione. Data la tendenza per gli utenti per concentrarsi su un'area visual relativamente piccola in qualsiasi momento (cono attentional della visione è all'incirca 10 gradi), raggruppare gli elementi dell'interfaccia utente per il livello che sono correlati a livello concettuale possono sfruttare i comportamenti di concatenamento dell'attenzione da elemento a un elemento con un account utente viene spostata loro sguardo all'interno di un'area. Durante la progettazione dell'interfaccia utente, tenere presenti le variazioni di grandi dimensioni potenziali nel campo visivo tra HoloLens e auricolari coinvolgente e concreto.

![Un esempio di elementi dell'interfaccia utente raggruppati per più semplice sguardo targeting in Esplora Galaxy](images/gazetargeting-grouping-1000px.jpg)<br>
*Un esempio di elementi dell'interfaccia utente raggruppati per più semplice sguardo targeting in Esplora Galaxy*

## <a name="improving-targeting-behaviors"></a>Miglioramento della destinazione dei comportamenti
Se l'intenzione dell'utente a un elemento di destinazione può essere determinato o approssimati a stretto contatto, può essere molto utile accettare "near miss" tentativi di interazione come se esse sono destinate in modo corretto. Esistono un numero limitato di metodi corretta che può essere incorporato nelle esperienze di realtà mista:

### <a name="head-gaze-stabilization-gravity-wells"></a>Head-sguardo stabilizzazione ("aree di gravità")
Questa deve essere attiva per la maggior parte/all del tempo. Questa tecnica consente di rimuovere l'instabilità head/collo naturale che gli utenti possono avere. Anche lo spostamento a causa dei comportamenti di ricerca/parlando.

### <a name="closest-link-algorithms"></a>Algoritmi di collegamento più vicino
Queste funzionano meglio in aree con sparse contenuti interattivi. Se è presente un'elevata probabilità che è possibile determinare quali un utente ha tentato di interagire con, è possibile integrare la capacità targeting semplicemente assumendo un certo livello di intent.

### <a name="backdatingpostdating-actions"></a>Azioni backdating/postdating
Questo meccanismo è utile per le attività che richiedono velocità. Quando un utente è in movimento attraverso una serie di targeting/attivazione evasive alla velocità, può essere utile per presuppone alcune finalità e consentire mancati passaggi su cui intervenire destinazioni che l'utente ha lo stato attivo leggermente prima o leggermente dopo il tocco (50 ms prima/dopo è rimasto in vigore in test preliminare).

### <a name="smoothing"></a>Anti-aliasing
Questo meccanismo è utile per gli spostamenti di ricerca del percorso, riducendo l'instabilità/oscillazione leggero a causa di caratteristiche naturale movimento della testina. Quando l'anti-aliasing tramite i movimenti di ricerca del percorso, arrotondare di dimensioni/distanza di spostamenti di tipo invece che nel corso del tempo

### <a name="magnetism"></a>Campi magnetici
Questo meccanismo può essere considerato come una versione più generale degli algoritmi "Più vicino link" - Creazione di un cursore verso una destinazione o aumentare semplicemente hitboxes (se visibilmente o No) quando gli utenti si avvicinano probabilmente destinazioni, tramite una certa conoscenza del layout interattiva per intenzione dell'utente approccio migliore. Ciò risulta particolarmente utile per le destinazioni di piccole dimensioni.

### <a name="focus-stickiness"></a>Persistenza dello stato attivo
Quando si determina quale vicino agli elementi interattivi per attivare, fornire un valore di bias all'elemento che è attualmente attivo. Ciò consentirà di ridurre lo stato attivo imprevedibile cambio comportamenti quando mobile in un punto intermedio tra due elementi con rumore naturale.


## <a name="composite-gestures"></a>Movimenti compositi
Le App in grado di riconoscere le scelte più di solo i singoli. Dalla combinazione scelta, tenere premuto e rilasciare con lo spostamento della mano, movimenti compositi più complessi possono essere eseguiti. Questi gesti compositi o ad alto livello si basano su di basso livello inpui dati spaziali (da indice puntato e Bloom) che gli sviluppatori hanno accesso a.

### <a name="air-tap"></a>Indice puntato
Il movimento dell'indice puntato (nonché i movimenti seguenti) reagisce solo a un tocco specifico. Per rilevare altre scelte, ad esempio Menu o. é quindi, l'app deve usare direttamente le interazioni di basso livello descritte due componenti chiave movimenti in precedenza nella sezione.

### <a name="tap-and-hold"></a>Toccare e tenere premuto
Tenere premuto è mantenere semplicemente la posizione di un dito verso il basso dell'indice puntato. La combinazione di aria toccare e tenere premuto consente un'ampia gamma di interazioni più complesse "fare clic e trascinare" in combinazione con lo spostamento di gestione risorse di Azure, ad esempio esegue la scelta di un oggetto anziché attivarlo o interazioni secondario "mousedown", ad esempio che mostra un menu di scelta rapida.
Prestare attenzione quando si progetta per questa azione, tuttavia, come gli utenti può essere soggetta a si rilassa loro maneggevolezza manualmente nel corso di un'operazione estesa.

### <a name="manipulation"></a>Manipolazione
I movimenti di manipolazione sono utilizzabile per spostare, ridimensionare o ruotare ologramma quando si desidera che l'ologrammi reagire 1:1 per gli spostamenti manuale dell'utente. Un utilizzo di tali spostamenti di tipo 1:1 consiste nel consentire all'utente di disegnare o disegnare nel mondo.
La selezione di destinazioni iniziali per un movimento di manipolazione deve essere eseguita da sguardo o fa riferimento. Una volta avviata la toccare e tenere premuto, qualsiasi modifica dell'oggetto viene quindi gestita manualmente gli spostamenti, liberando Guardatevi intorno mentre che modificano, all'utente.

### <a name="navigation"></a>Navigazione
Movimenti di esplorazione operano come un joystick virtuale e possono essere utilizzati per spostarsi di widget dell'interfaccia utente, ad esempio menu radiali. Toccare e tenere premuto per avviare il movimento e quindi spostare la mano all'interno di un cubo 3D normalizzato, incentrata sulla stampa iniziale. È possibile spostare la mano lungo l'asse X, Y o Z da un valore pari a -1 a 1, dove 0 è il punto di partenza.
Navigazione utilizzabile per compilare in base al relativo alla velocità lo scorrimento continuo o i movimenti zoom, simili alla visualizzazione a scorrimento un'interfaccia utente 2D facendo clic sul pulsante centrale del mouse e quindi spostando il puntatore del mouse su e giù.

Navigazione con rails si riferisce alla capacità di riconoscere gli spostamenti in determinati asse fino al raggiungimento di determinate soglia su quell'asse. Ciò è utile, solo quando lo spostamento in più di un asse è abilitato in un'applicazione dallo sviluppatore, ad esempio, se un'applicazione è configurata per riconoscere i movimenti di navigazione tra asse Y X, ma anche specificata con rails asse X. In questo caso sistema riconoscerà mano gli spostamenti tra asse X fino a quando rimangono all'interno di un immaginario Guide (Guida) dell'asse X se lo spostamento di disponibilità si verifica anche asse Y.

All'interno delle App 2D, gli utenti possono usare i movimenti di spostamento verticale a scorrere, eseguire lo zoom avanti o trascinare all'interno dell'app. Questo viene inserito virtuale con un dito tocca all'app per simulare i movimenti tocco dello stesso tipo. Gli utenti possono selezionare le azioni avvengono attivando e disattivando tra gli strumenti della barra di sopra dell'app, selezionando il pulsante o indicante che '< scorrimento/trascinare/> dello zoom'.

[Altre informazioni sui movimenti compositi](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Riconoscitori di movimento

Un vantaggio dell'utilizzo di riconoscimento del movimento è che è possibile configurare un riconoscitore di movimento solo per i movimenti che di destinazione corrente ologrammi possono accettare. La piattaforma verrà eseguita solo la risoluzione dell'ambiguità necessarie per distinguere questi gesti supportati particolari. In questo modo, ologramma che supporta solo l'indice puntato può accettare qualsiasi periodo di tempo tra pressione e rilascio, mentre un ologrammi che supporta sia toccare e tenere premuto possibile alzare di livello il tocco per l'attesa dopo la soglia di tempo di attesa.

## <a name="hand-recognition"></a>Riconoscimento di mano
HoloLens riconosce i movimenti della mano per rilevare la posizione di una o entrambe le mani visibili al dispositivo. HoloLens vede le mani quando sono in stato ready (parte posteriore l'icona della mano è rivolta con dito indice) o lo stato di premuto (parte posteriore l'icona della mano rivolta verso il basso è il dito indice). Quando sono in altri può causare, di HoloLens tali file verranno ignorati.
Per ogni indicatore rileva tale HoloLens, è possibile accedere alla posizione (senza l'orientamento) e il relativo stato premuto. Quando l'icona della mano si avvicina il bordo della cornice di movimento, ha anche fornito con un vettore di direzione, è possibile mostrare all'utente in modo che sappia come spostare le mani per ottenerlo di nuovo in cui HoloLens può visualizzarlo.

## <a name="gesture-frame"></a>Frame di movimento
Per movimenti su HoloLens, l'icona della mano deve essere all'interno di un"movimento", in un intervallo che il rilevamento del movimento fotocamere possono visualizzare in modo appropriato (molto più o meno da naso vita e tra ricade). Gli utenti devono essere sottoposti a training su un'area del riconoscimento per l'esito positivo dell'azione e per i propri comfort (molti utenti inizialmente presupporrà che il frame di movimento deve essere entro la visualizzazione tramite HoloLens e contenere le armi uncomfortably per interagire). Quando si usa il HoloLens Clicker, subito a usare non è necessario essere all'interno della cornice di movimento.

Nel caso di movimenti continuati, in particolare, vi è alcuni rischi correlati agli utenti lo spostamento le mani fuori dalla cornice movimenti mentre è in movimento a metà (durante lo spostamento di un determinato oggetto holographic, ad esempio) e la perdita di base al risultato desiderato.

Esistono tre aspetti da considerare:

- Formazione dell'utente del movimento frame esistenza e limiti approssimativi (tenuto durante l'installazione di HoloLens).

- Informare gli utenti quando i movimenti sono prossime alla/sostanziale i limiti di intervallo movimento all'interno di un'applicazione, come accade in un movimento perso porterà a risultati indesiderati. Research ha illustrato le qualità di chiave di un sistema di notifica e la shell di HoloLens fornisce un buon esempio di questo tipo di notifica (visual, sul cursore centrale, che indica la direzione nella quale limite attraversamento è in corso).

- Conseguenze di compromettere il funzionamento i limiti di frame di movimento dovrebbero essere ridotta a icona. In genere, ciò significa che il risultato di un movimento deve essere arrestato in corrispondenza del limite, ma non invertito. Ad esempio, se un utente sta spostando un oggetto holographic attraverso una chat room, lo spostamento deve essere interrotta quando viene superata la cornice di movimento, ma non verranno restituita al punto di partenza. L'utente potrebbe esperienza alcuni frustrazione, ma può comprendere più rapidamente i limiti e non è necessario riavviare le azioni desiderate complete ogni volta che.


## <a name="see-also"></a>Vedere anche
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Esecuzione di comandi vocali](voice-design.md)





