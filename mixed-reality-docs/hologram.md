---
title: Che cos'è un ologramma?
description: Consente di HoloLens visualizzare e interagire con vntana tridimensionale, gli oggetti di luce e audio che vengono visualizzati in tutto il mondo si.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, vntana, progettazione, l'interazione
ms.openlocfilehash: 5a6cc4df764b1f92f6bea2d7d6e6effe2164e4d6
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597833"
---
# <a name="what-is-a-hologram"></a>Che cos'è un ologramma?

HoloLens è possibile creare **vntana**, oggetti apportate della luce e audio che vengono visualizzati in ambiente circostante, proprio come se fossero oggetti reali. Vntana risposta al [estasiati](gaze.md), [movimenti](gestures.md) e [comandi vocali](voice-input.md)e possono interagire con [superfici reali](spatial-mapping.md) si. Con vntana, è possibile creare oggetti digitali che fanno parte del mondo.

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Ologrammi</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>Ologramma è costituita da luce e suono

Il vntana tale HoloLens [esegue il rendering](rendering.md) visualizzati nel frame holographic presentare direttamente gli occhi dell'utente. Ologrammi aggiungono light nel mondo, ciò significa che viene visualizzata sia la luce dalla visualizzazione e la luce dall'ambiente circostante. HoloLens non rimuove luce dagli occhi, in modo vntana non è possibile eseguire il rendering con il colore nero. Al contrario, nero contenuto viene visualizzato come trasparente.

Ologrammi possono avere molti aspetti diversi e comportamenti. Alcuni sono realistici e continue e altri sono cartoonish ed ethereal. Ologrammi possono evidenziare le funzionalità di ambiente circostante e possono essere elementi dell'interfaccia utente dell'app.

![Cane holographic walking sul pavimento](images/fang3-640px.jpg)

Può anche rendere vntana [suoni](spatial-sound.md), che sembrerà provenire da un punto specifico l'ambiente circostante. Su HoloLens, suoni provengono da due relatori che si trovano direttamente sopra dare l'impressione, senza che li. Come per le visualizzazioni, i relatori principali sono additive, introdurre nuovi suoni senza bloccare i suoni dall'ambiente in uso.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Ologramma può essere inserito nel mondo o tag alle

Quando si dispone di una determinata posizione in cui si desidera ologramma, è possibile [posizionare](coordinate-systems.md) è precisamente presenti nel mondo. Nel corso di tutto tali ologrammi, verrà visualizzato stabile rispetto all'ambiente circostante è. Se si usa un' [ancoraggio spaziale](coordinate-systems.md#spatial-anchors) per bloccare tale oggetto saldamente al mondo, il sistema può anche ricordare in cui si trovava quando torna online in un secondo momento.

![Maquette holographic predefiniti che si trova in una tabella](images/image5-640px.png)

Alcuni vntana seguire invece l'utente. Questi vntana tag-along posiziona in base all'utente, indipendentemente da dove che illustrano in modo. È anche possibile portare ologramma con l'utente per un periodo di tempo e posizionarlo sul muro dopo aver ottenuto da un'altra chat room.

**Procedure consigliate**
* Alcuni scenari potrebbero richiedere che vntana rimanga visibili in tutto l'esperienza o facilmente individuabile. Esistono due approcci generali per questo tipo di posizionamento. È possibile chiamarli **"bloccata alla visualizzazione"** e **"bloccato corpo"**.
   * Blocco di visualizzazione contenuto viene Formed "bloccato" per la visualizzazione del dispositivo. Questo è difficile per diversi motivi, tra cui un sentimento innaturale di "clingyness" che rende frustrato molti utenti e che si voglia "disfarci lo." In generale, molti progettisti riscontrato che è preferibile evitare il blocco a livello di visualizzazione contenuto.
   * L'approccio bloccato corpo è molto più forgivable. Blocca il thread del corpo è quando ologramma è Windows con tethering al corpo dell'utente o il vettore sguardo, ma viene posizionato nello spazio 3d intorno all'utente. Numerose esperienze hanno adottato un comportamento di blocco a livello di corpo dove ologrammi il "segue" lo sguardo agli utenti, che consente all'utente ruota il corpo e spostarsi all'interno dello spazio senza perdere l'ologrammi. Incorporare un ritardo consente lo spostamento di ologramma sembrano più naturali. Ad esempio, alcuni core dell'interfaccia utente del sistema operativo Windows Holographic Usa una variante nel corpo di blocco che segue sguardo dell'utente con un ritardo gentle, simile a elastic mentre l'utente attiva propria testa.
* Posizionare l'ologrammi a una distanza di visualizzazione più comoda in genere circa 1-2 contatori dall'inizio.
* Fornire una quantità di deviazione per gli elementi che devono essere continuamente nel frame holographic oppure prendere in considerazione l'animazione di contenuto da un lato dello schermo quando l'utente sposta il punto di vista.

**Posizionare vntana nella zona ottimale - tra m 1,25 e 5 minuti**

Due contatori è la soluzione ottimale e l'esperienza diminuirà si avvicina di un misuratore. Alle distanze più vicini a un misuratore, è maggiori probabilità di essere problematico rispetto fermo ologrammi vntana che sposta regolarmente in modo approfondito. Prendere in considerazione normalmente il taglio o dissolvenza in uscita del contenuto quando le dimensioni diventano troppo vicino ai come non jar l'utente in un'esperienza di imprevista.

![Distanza ottima per il posizionamento vntana da parte dell'utente.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Ologramma interagisce con il mondo

Ologrammi non solo sulla luce e suoni; si tratta inoltre di una parte attiva del tuo mondo. Sguardo ologrammi e movimento con la mano ologramma possibile iniziare a seguire l'utente. Consentire a un comando vocale ologramma e può rispondere.

![Progettazione motorcycle holographic montati nel corpo di una motocicletta reali](images/image8-640px.png)

Ologrammi abilitare interazioni personale che non sono possibili in un' posizione. Perché nel mondo in cui è in grado di HoloLens, un carattere holographic può esaminare è direttamente gli occhi nel corso nella stanza.

Ologramma può interagire anche con l'ambiente circostante. Ad esempio, è possibile inserire una palla holographic sopra una tabella. Quindi, con un [puntato](gestures.md#air-tap), guardare la palla rimbalzante e rendere suono quando raggiunge la tabella.

Ologrammi possono anche essere bloccati da oggetti reali. Ad esempio, un carattere holographic potrebbe essere illustrato tramite una porta e dietro una parete, non è il più visualizzata.

**Suggerimenti per l'integrazione ologrammi e del mondo reale**
* Allineamento alle regole gravitazionale rende vntana più facile correlare alla e credibili più. eg: Inserisci un cane holographic su sin & un vaso sulla tabella, anziché lasciare che mobile nello spazio.
* Molti progettisti hanno riscontrato la possibilità di integrare ulteriormente believably vntana creando un'ombreggiatura"negativa" nell'area di cui si trova l'ologrammi in. Ciò avviene creando un alone soft terra tutto l'ologrammi e quindi sottraendo "ombra" dall'alone. L'alone temporanea si integra con la luce dal mondo reale e l'ombreggiatura motivi di ologramma nell'ambiente.

## <a name="a-hologram-is-whatever-you-dream-up"></a>Ologramma è qualsiasi elemento sogna

Gli sviluppatori holographic hai la possibilità di interrompere la tua creatività all'esterno di schermate 2D e in ambiente circostante è. Che cosa verrà *si* compilazione?

![World immaginaria holographic in domestico](images/designoverview.jpg)

## <a name="see-also"></a>Vedere anche
* [Spaziale audio](spatial-sound.md)
* [Colore, chiaro e materiali](color,-light-and-materials.md)
