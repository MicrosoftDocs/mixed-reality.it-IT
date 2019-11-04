---
title: Che cos'è un ologramma?
description: HoloLens consente di visualizzare e interagire con ologrammi tridimensionali, oggetti di luce e suoni presenti in tutto il mondo.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, ologrammi, progettazione, interazione
ms.openlocfilehash: 5fb3aff3f59d0999676356d257b72f286a8d7adf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435104"
---
# <a name="what-is-a-hologram"></a>Che cos'è un ologramma?

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


HoloLens consente di creare **ologrammi**, oggetti costituiti da luce e suoni presenti in tutto il mondo, proprio come se fossero oggetti reali. Gli ologrammi rispondono a [sguardi](gaze-and-commit.md), [movimenti](gaze-and-commit.md#composite-gestures) e [comandi vocali](voice-input.md)e possono interagire con le [aree reali](spatial-mapping.md) . Con gli ologrammi puoi creare oggetti digitali che fanno parte del tuo mondo.

<br>


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
        <td>Ologrammi</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>Un ologramma è costituito da luce e suoni

Gli ologrammi che HoloLens [esegue il rendering](rendering.md) vengono visualizzati nel frame olografico direttamente davanti agli occhi dell'utente. Gli ologrammi aggiungono luce al mondo, il che significa che è possibile visualizzare sia la luce dallo schermo che la luce dall'ambiente circostante. HoloLens non rimuove la luce dagli occhi, quindi gli ologrammi non possono essere sottoposti a rendering con il colore nero. Il contenuto nero viene invece visualizzato come trasparente.

Gli ologrammi possono avere diversi aspetti e comportamenti. Alcune sono realistiche e solide e altre sono animate ed etereo. Gli ologrammi possono evidenziare le funzionalità nell'ambiente in uso e possono essere elementi nell'interfaccia utente dell'app.

![Mano che manipola un ologramma](images/hologram-hands-940px.jpg)

Gli ologrammi possono anche creare [suoni](spatial-sound.md), che sembrano provenire da una posizione specifica nell'ambiente in cui si trovano. In HoloLens, il suono deriva da due altoparlanti che si trovano direttamente sopra le orecchie, senza coprirli. Analogamente agli schermi, i relatori sono additivi, introducendo nuovi suoni senza bloccare i suoni dall'ambiente.

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Un ologramma può essere inserito nel mondo o nel tag insieme all'utente

Quando si dispone di una posizione specifica in cui si desidera un ologramma, è possibile [inserirla](coordinate-systems.md) esattamente nel mondo. Quando si tratta di un ologramma, viene visualizzato un aspetto stabile rispetto al mondo. Se si usa un [ancoraggio spaziale](coordinate-systems.md#spatial-anchors) per aggiungere l'oggetto in modo consolidato al mondo, il sistema può persino ricordare dove è stato lasciato quando si torna più tardi.

![Due uomini che usano il layout di Microsoft Dynamics 365 in uno spazio al dettaglio](images/HLS19_retailLayoutHologram_001-940px.jpg)

Alcuni ologrammi seguono invece l'utente. Gli ologrammi con tag vengono posizionati in relazione all'utente, indipendentemente dalla loro posizione. È anche possibile scegliere di portare un ologramma per un po' di tempo e quindi posizionarlo sul muro quando si accede a un'altra stanza.

**Procedure consigliate**
* Alcuni scenari possono richiedere che gli ologrammi rimangano facilmente individuabili o visibili nell'intera esperienza. Questo tipo di posizionamento è costituito da due approcci di alto livello. Chiameremo **"display-locked"** e **"Body-locked"** .
   * Il contenuto con blocco visualizzato è posizionato "bloccato" sullo schermo del dispositivo. Si tratta di un'operazione complessa per diversi motivi, tra cui una sensazione insensata di "clingyness" che rende molti utenti frustrati e che desiderano "eliminarli". In generale, molti designer hanno ritenuto migliore di evitare il contenuto del blocco visualizzato.
   * L'approccio con blocco del corpo è molto più perdonabile. Il blocco del corpo si verifica quando un ologramma è vincolato al corpo dell'utente o al vettore dello sguardo, ma è posizionato nello spazio 3D intorno all'utente. Molte esperienze hanno adottato un comportamento di blocco del corpo in cui l'ologramma "segue" lo sguardo degli utenti, che consente all'utente di ruotare il corpo e spostarsi nello spazio senza perdere l'ologramma. L'integrazione di un ritardo aiuta il movimento dell'ologramma a essere più naturale. Ad esempio, un'interfaccia utente di base del sistema operativo Windows olografico usa una variante del blocco del corpo che segue lo sguardo dell'utente con un ritardo di tipo elastico e elastico mentre l'utente si attiva.
* Posizionare l'ologramma a una distanza di visualizzazione comoda in genere a circa 1-2 metri di distanza dall'inizio.
* Fornire una certa tendenza per gli elementi che devono essere continuamente nel frame olografico oppure provare ad animare il contenuto su un lato dello schermo quando l'utente modifica il proprio punto di visualizzazione.

**Posizionare gli ologrammi nell'area ottimale, tra 1.25 m e 5m**

Due contatori sono i più ottimali e l'esperienza ridurrà il più vicino possibile da un contatore. A distanze più vicine a un metro, gli ologrammi che si spostano regolarmente in profondità sono più probabilmente problematici degli ologrammi stazionari. Prendere in considerazione la possibilità di ritagliare o dissolvere il contenuto quando diventa troppo vicino, in modo da non inserirlo in un'esperienza imprevista.

![Distanza ottimale per inserire gli ologrammi dall'utente.](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a>Un ologramma interagisce con l'utente e il mondo

Gli ologrammi non hanno solo la luce e il suono; sono anche una parte attiva del mondo. Osservando un ologramma e un gesto con la mano, un ologramma può iniziare a seguire l'utente. Fornire un comando Voice a un ologramma, che può rispondere.

![Gruppo di utenti governativi che usano Microsoft HoloLens 2 per collaborare a un progetto di sviluppo di una farm eolica](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Gli ologrammi consentono interazioni personali che non sono possibili altrove. Poiché il HoloLens sa dove si trova nel mondo, un carattere olografico può esaminarlo direttamente quando si cammina intorno alla stanza.

Un ologramma può interagire anche con l'ambiente in uso. Ad esempio, è possibile inserire una palla da rimbalzo olografica sopra una tabella. Quindi, con un [Rubinetto aria](gaze-and-commit.md#composite-gestures), guardare il rimbalzo della palla e creare un suono quando si raggiunge la tabella.

Gli ologrammi possono anche essere bloccati da oggetti reali. Un carattere olografico, ad esempio, può spostarsi tra una porta e un muro, fuori dalla propria visione.

**Suggerimenti per l'integrazione di ologrammi e il mondo reale**
* L'allineamento alle regole gravitazionali rende gli ologrammi più semplici da correlare e più credibili. ad esempio: posizionare un cane olografico & un vaso sulla tabella anziché inserirli nello spazio.
* Molti designer hanno scoperto che possono integrare gli ologrammi in modo ancora più credibile creando un'ombreggiatura negativa sulla superficie in cui si trova l'ologramma. A tale scopo, è possibile creare un alone di luce intorno all'ologramma e quindi sottrarre l'ombreggiatura dal bagliore. Il Soft Glow si integra con la luce del mondo reale e con i motivi dell'ombreggiatura dell'ologramma nell'ambiente.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a>Un ologramma è qualsiasi <br>è possibile sognare<br>
        Gli sviluppatori olografici hanno la possibilità di suddividere la creatività dalle schermate 2D e in tutto il mondo.<br><br>
        *Che cosa compilerai* ?
    :::column-end:::
        :::column:::
        spazio ![](images/spacer-20x582.png)<br>
       ![mondo immaginario olografico in una stanza vivente](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a>Vedi anche
* [Espandi il processo di progettazione](case-study-expanding-the-design-process-for-mixed-reality.md)
* [Audio spaziale](spatial-sound.md)
* [Colore, luce e materiali](color,-light-and-materials.md)
