---
title: Movimenti
description: I movimenti della mano consentono agli utenti di agire in realtà mista.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, movimenti, interazione, progettazione
ms.openlocfilehash: ae8af8fdb0bd224d127092c6636d473f383ab6f9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435205"
---
# <a name="gestures"></a>Movimenti

I movimenti della mano consentono agli utenti di agire in realtà mista. L'interazione si basa su **sguardi** , **movimenti** o **voce** , per agire su qualsiasi elemento di destinazione. I movimenti della mano non forniscono una posizione precisa nello spazio, ma la semplicità di inserimento di un HoloLens e l'interazione immediata con il contenuto consentono agli utenti di lavorare senza altri accessori.

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

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
        <td>Movimenti</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Mano articolata</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Altre indicazioni specifiche per HoloLens 2 [saranno presto](news.md)disponibili.

## <a name="gaze-and-commit"></a>Sguardo e commit

Per intraprendere azioni, i movimenti della mano usano lo [sguardo a capo](gaze-and-commit.md) come meccanismo di destinazione. La combinazione di **sguardo** e movimento del **tocco di aria** comporta un'interazione con lo **sguardo e il commit** . Un'alternativa a sguardi e commit è il **punto e il commit**, abilitati dai [controller di movimento](motion-controllers.md). Le app eseguite in HoloLens devono supportare solo lo sguardo e il commit poiché HoloLens non supporta i controller di movimento. Le app in esecuzione su HoloLens e auricolari immersivi devono supportare sia le interazioni basate su sguardi che quelle basate su punti, per offrire agli utenti la possibilità di scegliere il dispositivo di input che usano.

## <a name="the-two-core-gestures-of-hololens"></a>I due movimenti principali di HoloLens

HoloLens riconosce attualmente due movimenti principali per i componenti, il **tocco aereo** e la **fioritura**. Queste due interazioni principali sono il livello più basso di dati di input spaziali a cui uno sviluppatore può accedere. Costituiscono la base per un'ampia gamma di possibili azioni da parte degli utenti.

### <a name="air-tap"></a>Simulazione del tocco

Il rubinetto aereo è un gesto di tocco con la mano verticale, simile a un clic del mouse o a una selezione. Viene usato nella maggior parte delle esperienze HoloLens per l'equivalente di un "clic" su un elemento dell'interfaccia utente dopo che è stato indirizzato con lo [sguardo](gaze-and-commit.md). Si tratta di un'azione universale che si apprende una volta e quindi si applica a tutte le app. Altri modi per eseguire SELECT sono premere il pulsante singolo in un [clic del mouse HoloLens](hardware-accessories.md#hololens-clicker) o pronunciare il comando vocale "Select".

![stato pronto per i movimenti della mano in HoloLens](images/image9.png)<br>
*Stato pronto per il rubinetto aria su HoloLens.*

Il rubinetto aereo è un gesto discreto. Una selezione è stata completata o non è, un'azione è o non viene rilevata in un'esperienza. È possibile, sebbene non consigliato, senza alcuno scopo specifico, creare altri movimenti discreti dalle combinazioni dei componenti principali, ad esempio un gesto di doppio tocco, per indicare qualcosa di diverso da un singolo tocco.

![dito nella posizione pronta, quindi toccare o fare clic su movimento](images/readyandpress.jpg)<br>
*Come eseguire un rubinetto aria: alzare il dito dell'indice nella posizione pronta, premere il dito per toccare o selezionare e quindi eseguire il backup fino a rilasciare.*

### <a name="bloom"></a>Bloom

Bloom è il movimento "Home" ed è riservato solo a questo. Si tratta di un'azione speciale di sistema che viene utilizzata per tornare al menu Start. Equivale a premere il tasto Windows su una tastiera o il pulsante Xbox in un controller Xbox. L'utente può utilizzare una mano.

![Movimento Bloom su HoloLens](images/image10-640px.png)

Per eseguire il gesto di Bloom su HoloLens, è possibile fare una mano, Palm up, insieme a tutte le dita. Aprire quindi la mano. Si noti anche che è sempre possibile tornare all'inizio dicendo "Hey Cortana, Go Home". Le app non possono rispondere in modo specifico a un'azione Home, perché vengono gestite dal sistema.

![movimento Bloom](images/bloom-giphy.gif)<br>
*Come eseguire il movimento Bloom in HoloLens.*

## <a name="composite-gestures"></a>Movimenti compositi

Le app sono in grado di riconoscere molto più dei singoli tocchi. Combinando il tocco, la pressione prolungata e il rilascio con il movimento della mano, possono essere eseguiti movimenti compositi più complessi. Questi movimenti compositi o di alto livello si basano sui dati di input spaziali di basso livello (provenienti dalla simulazione del tocco e dall'apertura della mano a fiore) a cui hanno accesso gli sviluppatori.

<table>
<tr>
<th> Gesto composito</th><th> Come applicare</th>
</tr><tr>
<td>Simulazione del tocco</td><td>La simulazione del tocco (come gli altri movimenti descritti di seguito) reagisce solo a un tocco specifico. Per rilevare altri tocchi, come Menu o Afferra, l'app deve usare direttamente le interazioni di livello più basso descritte nella sezione precedente relativa ai due movimenti componente chiave.</td>
</tr><tr>
<td>Tocco e pressione prolungata</td><td><p>La pressione prolungata consiste nel mantenere la posizione del dito abbassato della simulazione del tocco. La combinazione di tocco e mantenimento dell'aria permette una serie di più complesse &quot;fare clic e trascinare&quot; interazioni in combinazione con lo spostamento ARM, ad esempio la selezione di un oggetto anziché l'attivazione o l'&quot;MouseDown&quot; interazioni secondarie come la visualizzazione di un menu di scelta rapida.</p><p>È tuttavia consigliabile prestare attenzione durante la progettazione di questo movimento perché gli utenti possono avere la tendenza ad allentare la posizione della mano durante l'esecuzione di un movimento esteso.</p></td>
</tr><tr>
<td>Manipolazione</td><td><p>I movimenti di manipolazione possono essere usati per spostare, ridimensionare o ruotare un ologramma quando si vuole che l'ologramma reagisca 1:1 ai movimenti della mano dell'utente&#39;. Uno degli usi possibili di tali movimenti 1:1 è quello di consentire all'utente di disegnare o dipingere nel mondo.</p><p>La selezione iniziale della destinazione per un movimento di manipolazione dovrebbe avvenire mediante sguardo fisso o puntamento. Quando inizia la sequenza tocco e pressione prolungata, qualunque manipolazione dell'oggetto viene gestita dai movimenti della mano, consentendo all'utente di guardarsi intorno mentre esegue la manipolazione.</p></td>
</tr><tr>
<td>Navigazione</td><td><p>I movimenti di navigazione funzionano come un joystick virtuale e possono essere usati per spostarsi nei widget dell'interfaccia utente, ad esempio nei menu radiali. Tocca e tieni premuto per avviare il movimento, quindi sposta la mano all'interno di un cubo 3D normalizzato, centrato attorno al punto di pressione iniziale. Puoi spostare la mano lungo l'asse X, Y o Z da un valore -1 a 1, essendo lo 0 il punto di partenza.</p><p>La navigazione può essere usata per creare movimenti continui di scorrimento o zoom basati sulla velocità, analoghi allo scorrimento di un'interfaccia utente 2D mediante il clic sul pulsante centrale del mouse e il successivo spostamento del mouse verso l'alto o il basso.</p><p>Per navigazione con binari si intende la capacità di riconoscere i movimenti su un determinato asse fino al raggiungimento di una certa soglia sullo stesso asse. Ciò è utile quando lo sviluppatore abilita lo spostamento su più di un asse in un'applicazione, ad esempio se l'applicazione è configurata per riconoscere i movimenti di navigazione sugli assi X e Y, ma viene specificato anche l'asse X con binari. In questo caso il sistema riconoscerà i movimenti della mano sull'asse X finché rimangono entro binari (guida) immaginari sull'asse X, se il movimento della mano ha luogo anche sull'asse Y.</p><p>Nelle app 2D gli utenti possono usare movimenti di navigazione verticali per scorrere, eseguire lo zoom o trascinare all'interno dell'app. In questo modo vengono inseriti nell'app tocchi delle dita virtuali per simulare tocchi dello stesso tipo. Gli utenti possono selezionare quali di queste azioni vengono eseguite alternando gli strumenti sulla barra sopra l'app, selezionando il pulsante o dicendo &#39;&lt;strumento&#39;di scorrimento/trascinamento/zoom&gt;.</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>Strumenti di riconoscimento dei movimenti

Uno dei vantaggi derivanti dall'uso del riconoscimento dei movimenti è poter configurare uno strumento di riconoscimento solo per i movimenti che l'ologramma attualmente selezionato come destinazione può accettare. La piattaforma eseguirà esclusivamente la disambiguazione necessaria per distinguere i movimenti supportati specifici. In questo modo, un ologramma che supporta solo la simulazione del tocco può accettare che trascorra un intervallo di tempo di qualunque durata tra la pressione e il rilascio, mentre un ologramma che supporta sia il tocco che la pressione prolungata può trasformare il tocco in pressione prolungata dopo il superamento della soglia temporale per la pressione prolungata.

## <a name="hand-recognition"></a>Riconoscimento della mano

HoloLens riconosce i movimenti della mano tenendo traccia della posizione di una o di entrambe le mani visibili al dispositivo. HoloLens considera le mani quando sono nello **stato pronto** (parte posteriore della mano con indice) o lo **stato premuto** (indietro della mano con il dito indice verso il basso). Quando le mani sono in altre posizioni, vengono ignorate da HoloLens.

Per ogni mano rilevata da HoloLens, puoi accedere alla sua posizione (senza orientamento) e allo stato premuto. Non appena la mano si avvicina al bordo della cornice di movimento, viene fornito anche un vettore direzionale che puoi decidere di mostrare all'utente in modo che sappia come muovere la mano per riportarla dove può essere vista da HoloLens.

## <a name="gesture-frame"></a>Cornice di movimento

Per i movimenti in HoloLens, la mano deve trovarsi all'interno di una "cornice di movimento", in un'area che possa essere vista adeguatamente dalle videocamere di rilevamento dei movimenti (approssimativamente un'area che va dal naso alla vita e che si estende tra le spalle). Gli utenti devono essere addestrati a usare quest'area di riconoscimento sia per la corretta esecuzione delle operazioni sia per il loro comfort (molti di essi inizialmente presumeranno che la cornice di movimento debba essere all'interno della visualizzazione attraverso HoloLens e terranno scomodamente le braccia alzate per interagire). Quando usi il dispositivo Clicker HoloLens, non è necessario che le tue mani si trovino all'interno della cornice di movimento.

Soprattutto nel caso di movimenti che continuano, vi è il rischio che gli utenti portino le mani al di fuori della cornice di movimento quando l'operazione non è ancora completata (ad esempio, mentre spostano un oggetto olografico), non riuscendo quindi a ottenere il risultato desiderato.

Sono tre gli aspetti da considerare:
* Necessità di formare l'utente in merito all'esistenza della cornice di movimento e ai relativi limiti approssimativi (formazione tenuta durante l'installazione di HoloLens).
* Necessità di notificare agli utenti quando con i loro movimenti si stanno avvicinando o stanno superando i limiti della cornice di movimento all'interno di un'applicazione, in quanto un movimento andato perduto può generare risultati indesiderati. Le ricerche svolte hanno mostrato i principali vantaggi di un tale sistema di notifica e la shell HoloLens ne costituisce un buon esempio (notifica visiva, sul cursore centrale, che indica la direzione in cui si sta oltrepassando il limite).
* Necessità di ridurre al minimo le conseguenze del superamento dei limiti della cornice di movimento. Questo, in generale, significa che il risultato di un movimento deve arrestarsi in corrispondenza del limite, ma non essere annullato. Se, ad esempio, un utente sposta un oggetto olografico in una stanza, lo spostamento dovrebbe arrestarsi quando viene violato il frame di movimento, ma **non** deve essere restituito al punto iniziale. L'utente può sentirsi frustrato in questo caso, ma può rendersi conto più rapidamente dei limiti senza dover ricominciare ogni volta a eseguire per intero le azioni desiderate.

## <a name="see-also"></a>Vedi anche
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Progettazione delle interazioni vocali](voice-design.md)
* [Input MR 211: movimento](holograms-211.md)
* [Movimenti e controller del movimento in Unity](gestures-and-motion-controllers-in-unity.md)
* [Mani e controller del movimento in DirectX](hands-and-motion-controllers-in-directx.md)
* [Controller del movimento](motion-controllers.md)
