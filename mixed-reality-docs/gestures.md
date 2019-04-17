---
title: Movimenti
description: Movimenti della mano consentono agli utenti di eseguire un'azione in realtà mista.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, movimenti, interazione, progettazione
ms.openlocfilehash: afebefddfd620b4697b86616e8ecc930b271dca2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597563"
---
# <a name="gestures"></a>Movimenti

Movimenti della mano consentono agli utenti intraprendere l'azione nella realtà mista. Interazione si basa **estasiati** di destinazione e **movimento** o **vocale** per agire su qualsiasi elemento sia stato definito. Movimenti della mano non si specifica un percorso preciso in uno spazio, ma la semplicità di inserimento in un HoloLens e immediatamente l'interazione con contenuto consente agli utenti di iniziare a lavorare senza altri accessori.

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Movimenti</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
<tr>
<td> Articolati e mani</td><td></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

## <a name="gaze-and-commit"></a>Gaze-and-commit

Per eseguire azioni, di usare i movimenti [sguardo head](gaze.md) come meccanismo di destinazione. La combinazione di **estasiati** e il **indice puntato** movimenti i risultati in un **sguardo e commit** interazione. È un'alternativa al sguardo e commit **punto di commit**, sono abilitate per [movimento controller](motion-controllers.md). App eseguibili su HoloLens sufficiente supportare sguardo e commit poiché HoloLens non supporta i controller di movimento. Le app eseguite su HoloLens e auricolari immersive devono supportare le interazioni basate su sguardo sia basate su sta puntando, per consentire agli utenti che usano il dispositivo di input.

## <a name="the-two-core-gestures-of-hololens"></a>I due principali i movimenti di HoloLens

HoloLens riconosce attualmente due principali movimenti di componenti - **puntato** e **Bloom**. Tali interazioni di due core sono il livello più basso di dati spaziali di input che uno sviluppatore possa accedere. Formano le basi per un'ampia gamma di possibili azioni dell'utente.

### <a name="air-tap"></a>Indice puntato

Indice puntato è un gesto tocco con l'icona della mano mantenuto in verticale, in modo analogo a un clic del mouse o selezionare. Viene utilizzato nella maggior parte delle esperienze di HoloLens per l'equivalente di un "clic" su un elemento dell'interfaccia utente dopo con targeting [estasiati](gaze.md). È un'azione di universal informazioni su una sola volta e applicarne tra tutte le app. Altri modi per eseguire select sono facendo clic sul pulsante singolo un [HoloLens Clicker](hardware-accessories.md#hololens-clicker) o parlando della voce di comando "Select".

![Stato pronto per movimenti della mano su HoloLens](images/image9.png)<br>
*Stato pronto per l'indice puntato in HoloLens.*

Indice puntato è un movimento discreto. Una selezione viene completata o non è, un'azione è o non viene eseguita all'interno di un'esperienza. È possibile, sebbene non consigliabile senza uno scopo specifico, per creare altri movimenti discreti da combinazioni di componenti principali (ad esempio, un movimento di un doppio tocco per indicare qualcosa di diverso da un singolo tocco).

![Con un dito nella posizione pronta e quindi un movimento toccare o fare clic su](images/readyandpress.jpg)<br>
*Come eseguire l'indice puntato: Generare il dito indice nella posizione pronti, premere il dito toccare o selezionare e quindi eseguire il backup di rilascio.*

### <a name="bloom"></a>Bloom

Bloom è il movimento "home" ed è riservata per questo da solo. È un'azione di sistema speciale che consente di tornare al menu Start. È equivalente alla pressione del tasto Windows sulla tastiera o il tasto Xbox in un controller Xbox. L'utente può usare entrambe le mani.

![Movimento Bloom su HoloLens](images/image10-640px.png)

Per eseguire il movimento bloom su HoloLens, riservare la mano, palm, insieme con portata. Aprire quindi la mano. Si noti che è anche sempre possibile tornare a Start pronunciare "Ehi Cortana, Go Home". Le app non è possibile reagire in modo specifico a un'azione home, come vengono gestiti dal sistema.

![Movimento Bloom](images/bloom-giphy.gif)<br>
*Come eseguire il movimento bloom su HoloLens.*

## <a name="composite-gestures"></a>Movimenti compositi

Le App in grado di riconoscere le scelte più di solo i singoli. Dalla combinazione scelta, tenere premuto e rilasciare con lo spostamento della mano, movimenti compositi più complessi possono essere eseguiti. Questi gesti compositi o ad alto livello si basano su di basso livello inpui dati spaziali (da indice puntato e Bloom) che gli sviluppatori hanno accesso a.

<table>
<tr>
<th> Movimento composito</th><th> Come applicare</th>
</tr><tr>
<td>Indice puntato</td><td>Il movimento dell'indice puntato (nonché i movimenti seguenti) reagisce solo a un tocco specifico. Per rilevare altre scelte, ad esempio Menu o. é quindi, l'app deve usare direttamente le interazioni di basso livello descritte due componenti chiave movimenti in precedenza nella sezione.</td>
</tr><tr>
<td>Toccare e tenere premuto</td><td><p>Tenere premuto è mantenere semplicemente la posizione di un dito verso il basso dell'indice puntato. La combinazione di aria toccare e tenere premuto consente un'ampia gamma di più complessa &quot;fare clic e trascinare&quot; interazioni in combinazione con arm lo spostamento dei quali esegue la scelta di un oggetto anziché averlo attivato oppure &quot;mousedown&quot; interazioni secondarie, ad esempio che mostra un menu di scelta rapida.</p><p>Prestare attenzione quando si progetta per questa azione, tuttavia, come gli utenti può essere soggetta a si rilassa loro maneggevolezza manualmente nel corso di un'operazione estesa.</p></td>
</tr><tr>
<td>Manipolazione</td><td><p>I movimenti di manipolazione possono essere utilizzati per spostare, ridimensionare o ruotare ologramma quando si desidera che l'ologrammi reagire 1:1 all'utente&#39;movimenti mano s. Un utilizzo di tali spostamenti di tipo 1:1 consiste nel consentire all'utente di disegnare o disegnare nel mondo.</p><p>La selezione di destinazioni iniziali per un movimento di manipolazione deve essere eseguita da sguardo o fa riferimento. Una volta avviata la toccare e tenere premuto, qualsiasi modifica dell'oggetto viene quindi gestita manualmente gli spostamenti, liberando Guardatevi intorno mentre che modificano, all'utente.</p></td>
</tr><tr>
<td>Navigazione</td><td><p>Movimenti di esplorazione operano come un joystick virtuale e possono essere utilizzati per spostarsi di widget dell'interfaccia utente, ad esempio menu radiali. Toccare e tenere premuto per avviare il movimento e quindi spostare la mano all'interno di un cubo 3D normalizzato, incentrata sulla stampa iniziale. È possibile spostare la mano lungo l'asse X, Y o Z da un valore pari a -1 a 1, dove 0 è il punto di partenza.</p><p>Navigazione utilizzabile per compilare in base al relativo alla velocità lo scorrimento continuo o i movimenti zoom, simili alla visualizzazione a scorrimento un'interfaccia utente 2D facendo clic sul pulsante centrale del mouse e quindi spostando il puntatore del mouse su e giù.</p><p>Navigazione con rails si riferisce alla capacità di riconoscere gli spostamenti in determinati asse fino al raggiungimento di determinate soglia su quell'asse. Ciò è utile, solo quando lo spostamento in più di un asse è abilitato in un'applicazione dallo sviluppatore, ad esempio, se un'applicazione è configurata per riconoscere i movimenti di navigazione tra asse Y X, ma anche specificata con rails asse X. In questo caso sistema riconoscerà mano gli spostamenti tra asse X fino a quando rimangono all'interno di un immaginario Guide (Guida) dell'asse X se lo spostamento di disponibilità si verifica anche asse Y.</p><p>All'interno delle App 2D, gli utenti possono usare i movimenti di spostamento verticale a scorrere, eseguire lo zoom avanti o trascinare all'interno dell'app. Questo viene inserito virtuale con un dito tocca all'app per simulare i movimenti tocco dello stesso tipo. Gli utenti possono selezionare le azioni avvengono attivando e disattivando tra gli strumenti della barra di sopra dell'app, selezionando il pulsante o che informa che &#39; &lt;trascinamento/Zoom e scorrimento&gt; strumento&#39;.</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>Riconoscitori di movimento

Un vantaggio dell'utilizzo di riconoscimento del movimento è che è possibile configurare un riconoscitore di movimento solo per i movimenti che di destinazione corrente ologrammi possono accettare. La piattaforma verrà eseguita solo la risoluzione dell'ambiguità necessarie per distinguere questi gesti supportati particolari. In questo modo, ologramma che supporta solo l'indice puntato può accettare qualsiasi periodo di tempo tra pressione e rilascio, mentre un ologrammi che supporta sia toccare e tenere premuto possibile alzare di livello il tocco per l'attesa dopo la soglia di tempo di attesa.

## <a name="hand-recognition"></a>Riconoscimento di mano

HoloLens riconosce i movimenti della mano per rilevare la posizione di una o entrambe le mani visibili al dispositivo. HoloLens vede le mani quando sono in uno il **lo stato di pronto** (parte posteriore l'icona della mano è rivolta con dito indice) o il **premuto stato** (parte posteriore l'icona della mano rivolta verso il basso è il dito indice). Quando sono in altri può causare, di HoloLens tali file verranno ignorati.

Per ogni indicatore rileva tale HoloLens, è possibile accedere alla posizione (senza l'orientamento) e il relativo stato premuto. Quando l'icona della mano si avvicina il bordo della cornice di movimento, ha anche fornito con un vettore di direzione, è possibile mostrare all'utente in modo che sappia come spostare le mani per ottenerlo di nuovo in cui HoloLens può visualizzarlo.

## <a name="gesture-frame"></a>Frame di movimento

Per movimenti su HoloLens, l'icona della mano deve essere all'interno di un"movimento", in un intervallo che il rilevamento del movimento fotocamere possono visualizzare in modo appropriato (molto più o meno da naso vita e tra ricade). Gli utenti devono essere sottoposti a training su un'area del riconoscimento per l'esito positivo dell'azione e per i propri comfort (molti utenti inizialmente presupporrà che il frame di movimento deve essere entro la visualizzazione tramite HoloLens e contenere le armi uncomfortably per interagire). Quando si usa il HoloLens Clicker, subito a usare non è necessario essere all'interno della cornice di movimento.

Nel caso di movimenti continuati, in particolare, vi è alcuni rischi correlati agli utenti lo spostamento le mani fuori dalla cornice movimenti mentre è in movimento a metà (durante lo spostamento di un determinato oggetto holographic, ad esempio) e la perdita di base al risultato desiderato.

Esistono tre aspetti da considerare:
* Formazione dell'utente del movimento frame esistenza e limiti approssimativi (tenuto durante l'installazione di HoloLens).
* Informare gli utenti quando i movimenti sono prossime alla/sostanziale i limiti di intervallo movimento all'interno di un'applicazione, come accade in un movimento perso porterà a risultati indesiderati. Research ha illustrato le qualità di chiave di un sistema di notifica e la shell di HoloLens fornisce un buon esempio di questo tipo di notifica (visual, sul cursore centrale, che indica la direzione nella quale limite attraversamento è in corso).
* Conseguenze di compromettere il funzionamento i limiti di frame di movimento dovrebbero essere ridotta a icona. In genere, ciò significa che il risultato di un movimento deve essere arrestato in corrispondenza del limite, ma non invertito. Ad esempio, se un utente sta spostando un oggetto holographic attraverso una chat room, lo spostamento deve essere interrotta quando viene superata la cornice di movimento, ma **non** da restituire per il punto di partenza. L'utente potrebbe esperienza alcuni frustrazione, ma può comprendere più rapidamente i limiti e non è necessario riavviare le azioni desiderate complete ogni volta che.

## <a name="see-also"></a>Vedere anche
* [Sguardo targeting](gaze-targeting.md)
* [Progettazione vocale](voice-design.md)
* [Input di MR 211: Movimento](holograms-211.md)
* [I movimenti e i controller di movimento in Unity](gestures-and-motion-controllers-in-unity.md)
* [Sguardo, gesti e controller di movimento in DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Controller di movimento](motion-controllers.md)
