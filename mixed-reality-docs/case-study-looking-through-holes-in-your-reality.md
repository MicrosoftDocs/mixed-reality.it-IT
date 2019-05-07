---
title: 'Case study: ricerca sui difetti nella realtà'
description: Questo case study viene illustrato come implementare l'effetto della "finestra magic" su HoloLens, consentendo all'utente di vedere dietro i muri sotto il pavimento e in aperture virtuale nell'ambiente effettivo.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, finestra magic, parallasse
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873933"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Case study: ricerca sui difetti nella realtà

Quando le persone pensano realtà mista e ciò che è possibile eseguire con Microsoft HoloLens, vengono in genere adattarsi a domande quali "Quali oggetti è possibile aggiungere per la mia camera"? oppure "Cosa è possibile layer sopra spazio personale?" Desidero evidenziare un'altra area è possibile prendere in considerazione, essenzialmente un espediente magic, ovvero con la stessa tecnologia per la ricerca all'interno o attraverso gli oggetti fisici reali si.

## <a name="the-tech"></a>Le tecnologie innovative

Se è stata ritenuta gli alieni come interrompano mediante le bacheche nelle  **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, sbloccato una parete sicura nei  **[frammenti](case-study-creating-an-immersive-experience-in-fragments.md)**, o sono stati abbastanza fortunato Per visualizzare il hangar UNSC infinito nel  **[esperienza Halo 5 E3 nel 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, si conosce già cosa sto parlando. In base alla propria immaginazione, questo espediente visual è utilizzabile per inserire aree libere temporanei nei muri a secco o nascondere i mondi sotto un floorboard loose.

![RoboRaid aggiunge pipe tridimensionale e altre strutture dietro le bacheche, visibile solo tramite aree libere creati come vincere la invaders.](images/roboraid-640px.png)

RoboRaid aggiunge pipe tridimensionale e altre strutture dietro le bacheche, visibile solo tramite aree libere creati come vincere la invaders.

Utilizza uno di questi vntana univoco su HoloLens, un'app può conferire un effetto ottico di contenuto protetto da affisse o tramite il piano nello stesso modo che realtà si manifesta tramite una finestra effettiva. Spostare manualmente a sinistra e si può vedere tutti gli elementi sul lato destro. Ottenere più da vicino e noterete un po' più di tutti gli elementi. La differenza principale è che fori reali permettono di tramite, mentre la parte intera parallelizzate non consentirà di salire tramite tale contenuto holographic magiche presenti. (Aggiungere un'attività al backlog.)

## <a name="behind-the-scenes"></a>Dietro le quinte

Il trucco è una combinazione di due effetti. In primo luogo, holographic contenuto sia stato aggiunto al mondo usando "spaziali anchor". L'uso di punti di ancoraggio per assicurarsi che il contenuto di "world-bloccato" significa che cosa si sta cercando in non in modo visivo dello sfasamento lontano da oggetti fisici vicino al telefono, anche quando si sposta o il sistema di mapping spaziale sottostante aggiorna il modello 3D della chat.

In secondo luogo, che il contenuto holographic è visivamente limitato a uno spazio molto specifico, in modo che è possibile vedere solo attraverso il foro nella realtà. Tale occlusione è necessario richiedere capacità attraverso un foro logica, nella finestra o trampolino, che vende il trucco. Senza qualcosa blocca la maggior parte della vista, un'abbreviazione nello spazio a una dimensione Jurassic segreto potrebbe essere semplicemente simile un divorasse posizionato in modo inadeguato.

![Ciò non è una schermata effettiva, ma un'illustrazione di come il segreto underworld da 101 nozioni di base di MR appare in HoloLens. L'enclosure nero non viene visualizzata, ma è possibile visualizzare il contenuto di un foro virtuale. (Quando la ricerca tramite un dispositivo reale, la parte intera sembrerebbe scompaiono ancora più perché gli occhi lo stato attivo a una distanza ulteriore come se non è ancora presente.)](images/origamiholecomposited-640px.png)

Ciò non è una schermata effettiva, ma un'illustrazione di come il segreto underworld dal [MR nozioni di base 101](holograms-101.md) Cerca su HoloLens. L'enclosure nero non viene visualizzata, ma è possibile visualizzare il contenuto di un foro virtuale. (Quando la ricerca tramite un dispositivo reale, la parte intera sembrerebbe scompaiono ancora più perché gli occhi lo stato attivo a una distanza ulteriore come se non è ancora presente.)

### <a name="world-locking-holographic-content"></a>Blocco a livello mondiale holographic contenuto

In Unity, è facile come aggiungere un componente WorldAnchor causando holographic contenuto rimanga bloccato world:

```
myObject.AddComponent<WorldAnchor>();
```

Il componente WorldAnchor costante regolerà la posizione e la rotazione del relativo GameObject (e pertanto altri in tale oggetto nella gerarchia di elementi) per mantenerla stabile rispetto agli oggetti fisici vicini. Durante la creazione del contenuto, è possibile crearlo in modo che il pivot radice dell'oggetto viene centrato in questo spazio virtuale vuoto. (Se pivot dell'oggetto si trova approfondita in muro, saranno molto più evidenti relativo piccoli aggiustamenti posizione e la rotazione e foro potrebbe non avere un aspetto molto stabile.)

### <a name="occluding-everything-but-the-virtual-hole"></a>Tutti gli elementi tranne il foro virtuale occluding

Esistono diversi modi per bloccare selettivamente la visualizzazione a ciò che è nascosto nell'affisse. La più semplice consente di sfruttare il fatto che HoloLens Usa una visualizzazione di addizione, il che significa che gli oggetti neri completamente invisibile. È possibile farlo in Unity non esegue qualsiasi shader speciali o materiale consigli, è sufficiente creare un materiale nero e assegnarla a un oggetto che le finestre nel contenuto. Se si ritiene che questo di modellazione 3D, è sufficiente usare un numero limitato di oggetti Quad predefiniti e sovrapporle leggermente. Esistono una serie di svantaggi di questo approccio, ma è il modo più rapido per ottenere qualcosa di utilizzo e ottenere una bassa fedeltà e prova del lavoro concetto è molto utile, anche se si sospetta che è possibile eseguire il refactoring in un secondo momento.

Uno degli svantaggi principali l'approccio "black box" precedente è che non fotografare bene. Mentre l'effetto potrebbe essere perfetto tramite la visualizzazione di HoloLens, qualsiasi schermate che scelto verranno visualizzato un oggetto grande nero invece di ciò che rimanga della parete o floor. Il motivo è che la fisica vntana composito hardware e le schermate e realtà in modo diverso. Verrà ora deviazione per un istante nel alcuni calcoli matematici fittizio...

*Avviso fittizio matematico. Questi numeri e le formule sono lo scopo di illustrare un punto, non deve essere di qualsiasi tipo di metrica accurata.*

Ciò che viene visualizzato tramite HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

Quanto visualizzato nelle schermate e video:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

IN INGLESE: Ciò che viene visualizzato tramite HoloLens è una semplice combinazione di più scura realtà (ad esempio tramite occhiali da sole) e tutti i valori vntana vuole visualizzare l'app. Tuttavia, quando si acquisisce uno screenshot, l'immagine della fotocamera viene sfumato con vntana dell'app in base al valore di trasparenza per pixel.

Un modo per risolvere questo problema consiste nel modificare il materiale "black box" per solo scrivere nel buffer di profondità e ordinare con l'altro materiale opaco. Per un esempio di ciò, consultare il [WindowOcclusion.shader file nei MixedRealityToolkit su GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). Le righe pertinenti vengono copiate qui:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Si noti "Offset 50, 100" riga è per risolvere problemi non correlati, in modo che probabilmente avrebbe senso di tralasciare che.)

Implementazione di un oggetto material occlusione invisibile simili consentirà all'app Disegna una casella che risulta corretta nella visualizzazione e nelle schermate di realtà mista. Per i punti in bonus, è possibile provare a migliorare le prestazioni di tale casella ulteriormente effettuando operazioni clever per disegnare anche un minor numero di pixel invisibile, ma che effettivamente può assumere le erbacce e in genere non è richiesto.

![Ecco il segreto underworld da 101 nozioni di base di MR Unity lo disegna, fatta eccezione per le parti della finestra di occluding esterne. Si noti che il pivot per il underworld al centro della finestra, che consente di mantenere l'area libera più stabile possibile relativo del piano effettivo.](images/underworld-occluded-640px.png)

Di seguito è riportato il segreto underworld dal [MR nozioni di base 101](holograms-101.md) come Unity lo disegna, fatta eccezione per le parti della finestra di occluding esterne. Si noti che il pivot per il underworld al centro della finestra, che consente di mantenere l'area libera più stabile possibile relativo del piano effettivo.

## <a name="do-it-yourself"></a>Eseguire tale operazione manualmente

Dispone un HoloLens e si desidera provare l'effetto personali? La cosa più semplice è (Nessuna esigenza) consiste nell'installare l'app Visualizzatore 3D gratuita e quindi caricare il [scaricare il file the.fbx ho fornito su GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) per visualizzare un modello di Teapot fiore stanza. Caricarlo in HoloLens ed è possibile visualizzare l'illusione al lavoro. Quando si è davanti il modello, è possibile vedere solo negli hole di piccole dimensioni, ovvero tutto il resto è invisibile. Esaminare il modello da qualsiasi altro lato e scomparire completamente. Usare il movimento, rotazione e scalabilità controlli del Visualizzatore 3D per posizionare il foro virtuale in qualsiasi area verticale che è possibile pensare a generare alcune idee!

![Visualizzazione di questo modello nell'editor di Unity mostrerà una scatola nera grande tutto il flowerpot. Su HoloLens, la finestra scomparirà, modo un effetto di finestra magic.](images/magicwindowflowerpotineditor.png)

Visualizzazione di questo modello nell'editor di Unity mostrerà una scatola nera grande tutto il flowerpot. Su HoloLens, la finestra scomparirà, modo un effetto di finestra magic.

Se si desidera compilare un'app che usa questa tecnica, consultare il [esercitazione MR nozioni di base 101](holograms-101.md) nel [esercitazioni di realtà mista](tutorials.md). Capitolo 7 termina con un'esplosione del piano che rivela un underworld nascosti (come illustrato nella figura sopra). Chi ha detto esercitazioni dovevano essere noioso?

Di seguito sono riportate alcune idee di in cui è possibile eseguire questa idea Avanti:
* Pensare al modo per rendere il contenuto all'interno del foro virtuale interattive. Consentire agli utenti di influire oltre le pareti può migliorare effettivamente le assimilata sorprende che può fornire il trucco.
* Pensare al modo attraverso gli oggetti ai aree note. Ad esempio, come può inserire un foro holographic nella tabella di caffè e vedere la parte intera sotto tale?

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Senior Software Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche
* [Nozioni di base MR 101: Progetto completo con dispositivo](holograms-101.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Ancoraggi nello spazio](spatial-anchors.md)
* [Mapping spaziale](spatial-mapping.md)
