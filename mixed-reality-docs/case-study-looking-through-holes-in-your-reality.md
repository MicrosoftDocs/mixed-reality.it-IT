---
title: 'Case Study: ricerca nei buchi della realtà'
description: In questo case study viene illustrato come implementare l'effetto "finestra magica" in HoloLens, che consente all'utente di vedere dietro le pareti, sotto il pavimento e in aperture virtuali all'interno dell'ambiente effettivo.
author: EricRehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, Magic Window, parallasse
ms.openlocfilehash: a1b9f0b2e576379846a867f3d3bffef7d8ec277e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436662"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Case Study: ricerca nei buchi della realtà

Quando le persone pensano alla realtà mista e a cosa possono fare con Microsoft HoloLens, in genere si limitano a domande come "quali oggetti è possibile aggiungere alla mia stanza?" o "quali sono I livelli in cima allo spazio?" Desidero evidenziare un'altra area che è possibile prendere in considerazione, essenzialmente un trucco magico, che usa la stessa tecnologia per esaminare o attraverso oggetti fisici reali.

## <a name="the-tech"></a>Il Tech

Se si hanno combattuto gli stranieri durante l'attraversamento dei muri in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** , è stato sbloccato un muro sicuro nei **[frammenti](case-study-creating-an-immersive-experience-in-fragments.md)** oppure è stato abbastanza fortunato per vedere il UNSC Infinity hangar nell' **[esperienza di Halo 5 all'E3 nel 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)** , si è visto che cosa sto parlando. A seconda dell'immaginazione, questo espediente visivo può essere usato per inserire buchi temporanei nel muro a secco o per nascondere i mondi in un listello separato.

![RoboRaid aggiunge le pipe tridimensionali e altre strutture dietro le pareti, visibili solo attraverso buchi creati come interruzioni degli invasori.](images/roboraid-640px.png)

RoboRaid aggiunge le pipe tridimensionali e altre strutture dietro le pareti, visibili solo attraverso buchi creati come interruzioni degli invasori.

Usando uno di questi ologrammi univoci in HoloLens, un'app può fornire l'illusione di contenuti protetti da muri o attraverso la propria pavimentazione in modo analogo alla realtà. Spostarsi a sinistra ed è possibile vedere qualunque sia il lato destro. È possibile avvicinarsi a un po' di tutto. La differenza principale consiste nel fatto che i buchi reali consentono di raggiungere il contenuto olografico, mentre il suo piano non consente di passare a tale contenuto. Aggiungo un'attività al backlog.

## <a name="behind-the-scenes"></a>Dietro le quinte

Questo trucco è costituito da una combinazione di due effetti. Per prima cosa, il contenuto olografico viene aggiunto al mondo con "ancoraggi spaziali". L'uso di ancoraggi per rendere il contenuto "con blocco universale" significa che ciò che si sta osservando non deriva visivamente dagli oggetti fisici vicini, anche quando si sposta o il sistema di mapping spaziale sottostante aggiorna il proprio modello 3D della chat room.

In secondo luogo, il contenuto olografico è limitato visivamente a uno spazio molto specifico, quindi è possibile vedere solo il foro della realtà. Tale occlusione è necessaria per richiedere la ricerca in un foro logico, una finestra o una porta, che vende il trucco. Senza bloccare la maggior parte della visualizzazione, un crack nello spazio a una dimensione Jurassic segreta potrebbe essere simile a un dinosauro mal inserito.

![Non si tratta di uno screenshot effettivo, ma viene illustrato il modo in cui il segreto Sottomondo di MR nozioni di base 101 esamina HoloLens. L'enclosure nera non viene visualizzata, ma è possibile visualizzare il contenuto tramite un foro virtuale. Quando si esamina un dispositivo reale, il piano sembrerebbe scomparire ulteriormente perché gli occhi si concentrano su un ulteriore distanza, come se non fosse neanche presente.](images/origamiholecomposited-640px.png)

Non si tratta di uno screenshot effettivo, ma viene illustrato il modo in cui il segreto Sottomondo di [Mr nozioni di base 101](holograms-101.md) esamina HoloLens. L'enclosure nera non viene visualizzata, ma è possibile visualizzare il contenuto tramite un foro virtuale. Quando si esamina un dispositivo reale, il piano sembrerebbe scomparire ulteriormente perché gli occhi si concentrano su un ulteriore distanza, come se non fosse neanche presente.

### <a name="world-locking-holographic-content"></a>Contenuto olografico con blocco globale

In Unity, causando il blocco del contenuto olografico è facile aggiungere un componente WorldAnchor:

```
myObject.AddComponent<WorldAnchor>();
```

Il componente WorldAnchor regola costantemente la posizione e la rotazione dei relativi GameObject (e quindi qualsiasi altro elemento sotto tale oggetto nella gerarchia) per mantenerlo stabile rispetto agli oggetti fisici adiacenti. Quando si crea il contenuto, crearlo in modo che il pivot radice dell'oggetto sia centrato su questo foro virtuale. Se il pivot dell'oggetto è profondo nella parete, le piccole modifiche apportate alla posizione e alla rotazione saranno molto più evidenti e il foro potrebbe non sembrare molto stabile.

### <a name="occluding-everything-but-the-virtual-hole"></a>Occlusione tutto tranne il foro virtuale

Esistono diversi modi per bloccare selettivamente la visualizzazione a ciò che è nascosto nei muri. Il più semplice sfrutta il fatto che HoloLens utilizza una visualizzazione additiva, il che significa che gli oggetti completamente neri appaiono invisibili. Questa operazione può essere eseguita in Unity senza eseguire particolari operazioni di shader o materiali, ma è sufficiente creare un materiale nero e assegnarlo a un oggetto che riquadri il contenuto. Se non si ha familiarità con la modellazione 3D, è sufficiente usare alcuni oggetti Quad predefiniti e sovrapporli leggermente. Questo approccio presenta diversi svantaggi, ma è il modo più rapido per lavorare e ottenere un modello di verifica a bassa fedeltà funzionante, anche se si sospetta che sia necessario effettuare il refactoring in un secondo momento.

Uno dei principali svantaggi dell'approccio "black box" precedente è la mancata fotografia. Anche se l'effetto potrebbe sembrare perfetto attraverso la visualizzazione di HoloLens, le schermate che verranno visualizzate mostreranno un oggetto nero di grandi dimensioni anziché quello che rimane della parete o del pavimento. Questo è il motivo per cui l'hardware fisico e le schermate degli ologrammi e della realtà compositi sono diversi. Devi dedicare qualche istante a una matematica falsa...

*Avviso matematico falso. Questi numeri e formule hanno lo scopo di illustrare un punto, non come una metrica accurata.*

Cosa si vede con HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

Cosa viene visualizzato in screenshot e video:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

In inglese: ciò che viene visualizzato tramite HoloLens è una semplice combinazione di realtà offuscata (ad esempio tramite occhiali) e qualsiasi ologramma che l'app vuole visualizzare. Tuttavia, quando si acquisisce una schermata, l'immagine della fotocamera viene fusa con gli ologrammi dell'app in base al valore di trasparenza per pixel.

Un modo per aggirare questo problema consiste nel modificare il materiale "black box" per scrivere solo nel buffer di profondità e ordinarlo con tutti gli altri materiali opachi. Per un esempio, vedere il [file WindowOcclusion. shader in MixedRealityToolkit su GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). Le righe rilevanti vengono copiate qui:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

Si noti che la linea "offset 50, 100" consiste nel risolvere i problemi non correlati, quindi potrebbe essere opportuno lasciarlo invariato.

Implementando un materiale di occlusione invisibile come che consente all'app di creare una casella che sembra corretta nella visualizzazione e negli screenshot di realtà mista. Per i punti di bonus, è possibile provare a migliorare ulteriormente le prestazioni di tale box eseguendo operazioni intelligenti per creare un numero ancora inferiore di pixel invisibili, ma che possono entrare nelle erbacce e, in genere, non sono necessarie.

![Di seguito è riportato il segreto sotterraneo di MR nozioni di base 101 As Unity lo disegna, eccetto le parti esterne della casella occlusione. Si noti che il perno per il Sottomondo è al centro della casella, che consente di tenere il foro il più possibile stabile rispetto al piano effettivo.](images/underworld-occluded-640px.png)

Di seguito è riportato il segreto sotterraneo di [Mr nozioni di base 101](holograms-101.md) As Unity lo disegna, eccetto le parti esterne della casella occlusione. Si noti che il perno per il Sottomondo è al centro della casella, che consente di tenere il foro il più possibile stabile rispetto al piano effettivo.

## <a name="do-it-yourself"></a>Fai da te

Si ha un HoloLens e si vuole provare l'effetto per se stessi? La cosa più semplice da fare (non è necessario scrivere codice) consiste nell'installare l'app visualizzatore 3D gratuita e quindi caricare il [file con estensione FBX fornito in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) per visualizzare un modello di Flower Pot nella propria stanza. Caricarla in HoloLens. è possibile osservare l'illusione al lavoro. Quando ci si trova davanti al modello, è possibile vedere solo nel piccolo foro, tutto il resto è invisibile. Esaminare il modello da qualsiasi altro lato e scomparire completamente. Usare i controlli di spostamento, rotazione e scalabilità del visualizzatore 3D per posizionare il foro virtuale su qualsiasi superficie verticale che è possibile considerare per generare alcune idee.

![La visualizzazione di questo modello nell'editor di Unity mostrerà un black box di grandi dimensioni intorno al vaso. In HoloLens, la casella scompare, consentendo un effetto della finestra magica.](images/magicwindowflowerpotineditor.png)

La visualizzazione di questo modello nell'editor di Unity mostrerà un black box di grandi dimensioni intorno al vaso. In HoloLens, la casella scompare, consentendo un effetto della finestra magica.

Se si vuole compilare un'app che usa questa tecnica, vedere l' [esercitazione nozioni di base su 101](holograms-101.md) nelle [esercitazioni sulla realtà mista](tutorials.md). Il capitolo 7 termina con un'esplosione al pavimento che rivela un Sottomondo nascosto (come illustrato in precedenza). Chi ha detto che le esercitazioni erano noiose?

Di seguito sono riportate alcune idee in cui è possibile adottare questa idea:
* Si pensi ai modi per rendere il contenuto all'interno del foro virtuale interattivo. Consentire agli utenti di avere un certo effetto oltre i muri può migliorare il senso di stupore che questo trick può offrire.
* Si pensi ai modi per visualizzare gli oggetti attraverso le aree note. Come è possibile, ad esempio, inserire un foro olografico nella tabella del caffè per visualizzare il piano sottostante?

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Senior Software Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche
* [Nozioni fondamentali 101: completare il progetto con il dispositivo](holograms-101.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Ancoraggi nello spazio](spatial-anchors.md)
* [Mapping spaziale](spatial-mapping.md)
