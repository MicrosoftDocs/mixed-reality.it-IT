---
title: Cursori
description: Un cursore, o un indicatore del vettore di destinazione, fornisce un feedback continuo all'utente per comprendere quali sono le intenzioni di HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1a generazione), HoloLens 2, realtà mista, cursori, targeting, sguardi, movimenti
ms.openlocfilehash: 719e7a573e8c8bc682ec0f960d9f3c8f8c8e5a4a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105746"
---
# <a name="cursors"></a>Cursori

![Cursori](images/UX/UX_Hero_Cursor.jpg)

Un cursore, o un indicatore del vettore di destinazione corrente, fornisce un feedback continuo all'utente per comprendere la posizione in cui l'auricolare ritiene che lo stato attivo corrente sia in quel momento. Il cursore consente all'utente di comprendere il punto di destinazione corrente e funge da feedback per indicare quale area, ologramma o punto risponderà all'input. Si tratta della rappresentazione digitale del punto in cui il dispositivo è in grado di comprendere l'attenzione dell'utente (anche se ciò potrebbe non essere uguale a quello di determinare le proprie intenzioni).

Il feedback fornito dal cursore offre agli utenti la possibilità di prevedere il modo in cui il sistema risponderà, utilizzare tale segnale come feedback per comunicare meglio la loro intenzione al dispositivo e, infine, avere maggiore fiducia sulle interazioni.

Sono disponibili tre tipi di cursori: **Finger, Ray**e **Head-sguardi**. Questi puntatori funzionano con diverse modalità di input in HoloLens, HoloLens 2 e auricolari immersivi. Di seguito sono riportate informazioni aggiuntive sul tipo di cursore da usare per ogni tipo di modello di auricolare e interazione. Nel Toolkit di realtà mista (MRTK) sono stati creati moduli per i cursori con trascinamento della selezione che consentono di creare l'esperienza di puntamento corretta.


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
        <td>Cursore dito</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Cursore Ray</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursore Head-sguardi</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Cursore dito
Il cursore Finger è disponibile solo in HoloLens 2 per migliorare la modalità di interazione "[manipolazione diretta con mani](direct-manipulation.md)". Per comprendere meglio la posizione del dito, sono stati collegati anelli ai suggerimenti di entrambe le dita degli indici. Le dimensioni della suoneria si basano sulla prossimità del dito alla superficie dell'interfaccia utente (più vicino al dito, minore è l'anello) e si ridurrà a una forma punto quando il dito si mette in contatto con l'interfaccia utente. <br>

](images/finger-cursor.png) cursore dito ![<br>
**Stati feedback visivi del cursore dito** 1: l'anello si riduce a un punto. 2: l'anello è allineato alla superficie. 3: l'anello è perpendicolare al vettore del dito. 4: nessun anello.

## <a name="ray-cursor"></a>Cursore Ray
I cursori raggio si allineano alla fine dei raggi di puntamento per consentire la manipolazione di oggetti fuori dalla portata di mano. Negli auricolari immersivi, i raggi vengono ritirati dai controller di movimento e terminano con i cursori a punti. In HoloLens 2 viene usato il modello mentale di questi raggi del controller di movimento e i raggi mano progettati che hanno origine dalle palme e terminano con cursori a forma di anello coerenti con i cursori con dito usati nella manipolazione diretta. <br>
:::row:::
    :::column:::
        ![controller del cursore a raggi](images/ray-cursor-controller.png)<br>
        **Cursori Ray dei controller di movimento**<br>
    :::column-end:::
    :::column:::
        ](images/ray-cursor-hand.png) mano del cursore ![raggio<br>
        **Cursori raggio delle mani**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a>Cursore Head-sguardi
Il cursore Head-sguardi è un punto che si connette alla fine di un vettore di sguardi invisibili che usa la posizione e la rotazione dell'intestazione verso il punto. Per eseguire le azioni, questo cursore di puntamento è associato a diversi input di commit, ad esempio il tocco aereo, i comandi vocali, l'abitazione e la pressione del pulsante. In HoloLens 2, il punto di partenza è meglio abbinato a qualsiasi input di commit che non sia il rubinetto aereo, in quanto si verifica un conflitto di interazione tra il tocco aereo e i raggi di mano. <br>
:::row:::
    :::column:::
        ![la mano del cursore](images/head-gaze-cursor-hand.png)<br>
        **Cursore Head-sguardi con movimento mano**<br>
    :::column-end:::
    :::column:::
        ](images/head-gaze-cursor-voice.png) voce cursore ![sguardo a capo<br>
        **Cursore Head-sguardi con comando Voice**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a>Suggerimenti sulla personalizzazione del cursore
Se si desidera personalizzare i comportamenti e le caratteristiche di feedback del cursore, di seguito sono riportate alcune indicazioni sulla progettazione:

### <a name="cursor-scale"></a>Scala del cursore
* Il cursore non deve essere più grande delle destinazioni disponibili, consentendo agli utenti di interagire con facilità e di visualizzare il contenuto.
* A seconda dell'esperienza creata, il ridimensionamento del cursore mentre l'utente si trova è anche una considerazione importante. Se, ad esempio, l'utente ha una maggiore familiarità con l'esperienza, il cursore non dovrebbe diventare troppo piccolo in modo che vada perduto.
* Quando si ridimensiona il cursore, prendere in considerazione l'applicazione di un'animazione soft mentre viene ridimensionata in modo da ottenere un senso organico.
* Evitare di ostacolare il contenuto. Gli ologrammi sono gli elementi che rendono memorabile l'esperienza e il cursore non dovrebbe allontanarsi da essi.

### <a name="directionless-cursor-shape"></a>Forma cursore direzionale
* Sebbene non esista una forma di cursore a destra, è consigliabile usare una forma senza direzione come un torus. Un cursore che punta in una direzione, ad esempio un cursore a freccia tradizionale, potrebbe confondere l'utente in modo che sia sempre simile.
* Un'eccezione è rappresentata dall'utilizzo del cursore per la comunicazione dell'istruzione di interazione con l'utente. Ad esempio, quando si ridimensionano gli ologrammi nel sistema operativo di realtà mista, il cursore include temporaneamente frecce che indicano all'utente come spostare la mano per ridimensionare l'ologramma.

### <a name="look-and-feel"></a>Aspetto
* Un cursore a forma di ciambella o Toro è adatto a una grande quantità di applicazioni.
* Selezionare un colore e una forma che rappresenti al meglio l'esperienza che si sta creando.
* I cursori sono particolarmente soggetti alla [separazione dei colori](hologram-stability.md#color-separation).
* Un piccolo cursore con opacità bilanciata mantiene informativo senza dominare la gerarchia visiva.
* Tenere presente che l'uso di ombre o evidenziazioni dietro il cursore potrebbe ostacolare il contenuto e distrarre dall'attività.
* I cursori devono essere allineati e abbracciare le superfici nell'app, in modo da dare all'utente la sensazione che il sistema sia in grado di individuare il punto in cui stanno cercando, ma anche che il sistema sia in grado di riconoscere l'ambiente. Nel sistema operativo di realtà mista, ad esempio, il cursore è allineato alle superfici del mondo dell'utente, creando una sensazione di consapevolezza del mondo anche quando l'utente non guarda direttamente un ologramma.
* Il blocco magnetico del cursore a un elemento interattivo quando si trova in prossimità può contribuire a migliorare la fiducia che l'utente interagirà con tale elemento quando eseguirà un'azione di selezione.

### <a name="visual-cues"></a>Segnali visivi
* Se l'esperienza è incentrata su un solo ologramma, il cursore dovrebbe allinearsi e abbracciare solo tale ologramma e modificare la forma quando si è lontani dall'ologramma. Ciò può comportare all'utente che l'ologramma è interoperabile e può interagire con esso.
* Se l'applicazione usa il mapping spaziale, il cursore potrebbe allinearsi e abbracciare ogni superficie che vede. In questo modo viene fornito un feedback agli utenti che HoloLens e l'applicazione possono visualizzare il proprio spazio. Questo rafforza il fatto che gli ologrammi sono reali e in questo mondo e contribuiscono a colmare il divario tra il reale e il virtuale.
* Avere un'idea di cosa deve fare il cursore quando non sono presenti ologrammi o superfici in visualizzazione. Il posizionamento a una distanza predeterminata davanti all'utente è un'opzione.

### <a name="possible-actions"></a>Azioni possibili
* Il cursore può essere rappresentato da icone diverse per indicare le possibili azioni che possono essere eseguite da un ologramma, ad esempio il ridimensionamento o la rotazione.
* Aggiungere al cursore informazioni aggiuntive solo se significa qualcosa per l'utente. In caso contrario, gli utenti potrebbero non osservare le modifiche dello stato o essere confuse dal cursore.

### <a name="input-state"></a>Stato input
* È possibile utilizzare il cursore per visualizzare lo stato o la finalità di input dell'utente. Ad esempio, è possibile visualizzare un'icona che informa l'utente che il sistema rileva lo stato della mano e che l'applicazione sa che è pronto a intervenire.
* È anche possibile usare il cursore per mostrare agli utenti che i comandi vocali sono stati uditi dal sistema tramite un colore momentaneo Chang

* Gli Stati del cursore seguenti possono essere implementati in modi diversi. È possibile implementare questi stati diversi modellando il cursore come una macchina a Stati. Ad esempio:
    * Lo stato di inattività è il punto in cui viene visualizzato il cursore predefinito.
    * Lo stato pronto è quando è stata rilevata la mano dell'utente nella posizione pronta.
    * Lo stato di interazione è quando l'utente sta eseguendo una particolare interazione.
    * Lo stato delle azioni possibili o il passaggio del mouse è quando si conferiscono azioni possibili che possono essere eseguite su un ologramma.

È anche possibile implementare questi stati in modo che sia possibile visualizzare risorse dell'arte diverse quando vengono rilevati stati diversi.

<br>

---


## <a name="going-cursor-free"></a>"Senza cursore"
La progettazione senza cursore è consigliata quando il senso di immersione è un componente chiave di un'esperienza e quando si puntano interazioni (tramite sguardo e movimento) non è necessaria una precisione notevole. Il sistema deve comunque soddisfare le esigenze normalmente soddisfatte da un cursore fornendo agli utenti un feedback continuo sulla comprensione del sistema e aiutandoli a comunicare in modo sicuro le proprie intenzioni al sistema. Questo può essere raggiungibile attraverso altre modifiche di stato evidenti.

<br>

---

## <a name="cursor-in-mrtkmixed-reality-toolkit-for-unity"></a>Cursore in MRTK (Mixed Reality Toolkit) per Unity
Per impostazione predefinita, **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce una precostruzione del cursore ([DefaultCursor. prefabbricate](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) che ha lo stesso stato di visualizzazione del cursore di sistema della shell. Viene assegnato nel profilo di input di MRTK in puntatori. È possibile sostituire o personalizzare questo cursore per la propria esperienza. Per l'esperienza con l'input di rilevamento degli occhi, MRTK fornisce anche EyeGazeCursor con un oggetto visivo sottile per ridurre al minimo la distrazione.

* [MRTK-profilo puntatore](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK-sistema di input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK-puntatori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a>Vedi anche
* [Movimenti](gaze-and-commit.md#composite-gestures)
* [Puntamento con la testa e commit](gaze-and-commit.md)
