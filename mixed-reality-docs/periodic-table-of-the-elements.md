---
title: Tabella periodico degli elementi
description: Tabella periodico degli elementi è un'app di esempio open source di Microsoft misto realtà progettazione Labs in cui è possibile imparare a creare il layout una matrice di oggetti nello spazio 3D con vari tipi di area con una raccolta di oggetti.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, app di esempio, i controlli
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604115"
---
# <a name="periodic-table-of-the-elements"></a>Tabella periodico degli elementi

>[!NOTE]
>Questo articolo illustra un esempio di analisi esplorativo è stata creata nel [laboratori di progettazione di realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), una posizione in cui si condivide quanto appreso sulle e per suggerimenti su mista lo sviluppo di app di realtà. Nostri articoli correlati alla progettazione e il codice si evolverà come si ottengono nuove informazioni.

[Tabella periodico degli elementi](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) è un'app di esempio open source di laboratori di progettazione realtà mista di Microsoft. Con questo progetto, è possibile imparare a layout di una matrice di oggetti nello spazio 3D con vari tipi di area con un  **[raccolta di oggetti](object-collection.md)**. Anche imparare a creare oggetti si che rispondono a input standard da HoloLens. È possibile utilizzare i componenti del progetto per creare la propria esperienza di app di realtà mista.

![Periodo nella tabella dell'app elementi](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>Sull'app

Tabella periodico degli elementi Visualizza gli elementi prodotti chimici e ognuna delle proprietà nello spazio 3D. Incorpora le interazioni di base di HoloLens, ad esempio toccare sguardo e aria. Gli utenti possono informazioni sugli elementi con modelli 3D animati. È possibile comprendere visivamente shell electron di un elemento e il nucleo - composto da protons e neutrons.

## <a name="background"></a>Informazioni

Dopo aver visto prima HoloLens, un'app table periodica è stata un'idea che sapevo che volevo possano sperimentarlo in realtà mista. Poiché ogni elemento dispone di numerosi punti dati che vengono visualizzati con testo, pensato che sarebbe ideale in materia di analisi composizione tipografica nello spazio 3D. La possibilità di visualizzare il modello dell'elemento electron era un'altra parte interessante di questo progetto.

## <a name="design"></a>Progettazione

Per la visualizzazione predefinita della tabella periodico, immaginato in precedenza caselle tridimensionale che contengono il modello di electron di ogni elemento. L'area di ogni casella sarebbe semitrasparente in modo che l'utente è stato possibile ottenere un'idea approssimativa del volume dell'elemento. Con il tocco sguardo e aria, l'utente è stato possibile aprire una visualizzazione dettagliata di ogni elemento. Per rendere la transizione tra la visualizzazione di tabella e vista dettagliata semplice e naturale, reso simile all'interazione fisica di una casella di apertura in uno scenario reale.

![Sketch di progettazione](images/640px-sketch20170406.jpg)<br>
*Disegni di progettazione*

Nel riquadro dettagli, vorrei visualizzare le informazioni di ogni elemento con il testo sofisticato nello spazio 3D. Il modello di electron 3D animate viene visualizzato nell'area centrale e può essere visualizzato da diverse angolazioni.

![Interazione](images/640px-periodictable-interaction.jpg)

![Prototipi](images/640px-periodictable-prototypes.jpg)<br>
*Prototipi di interazione*

L'utente può modificare il tipo di area per via aerea toccando i pulsanti nella parte inferiore della tabella, possono passare tra piano, cilindro, sphere e a dispersione.

## <a name="common-controls-and-patterns-used-in-this-app"></a>I modelli usati in questa app e i controlli comuni

### <a name="interactable-object-button"></a>Oggetto si (pulsante)

[Oggetto si](interactable-object.md) è un oggetto che può rispondere all'input di base HoloLens. Viene fornito come un prefab/script che è possibile applicare facilmente a qualsiasi oggetto. Ad esempio, è possibile rendere una tazza di caffè nella scena si e rispondere agli input, ad esempio sguardo, gesti di navigazione e modifica e indice puntato. [Altre informazioni](interactable-object.md)

![oggetto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Raccolta di oggetti

[Raccolta di oggetti](object-collection.md) è un oggetto che consente definire il layout più oggetti in varie forme. Supporta piano, cilindro, sphere e a dispersione. È possibile configurare proprietà aggiuntive, ad esempio radius, il numero di righe e la spaziatura. [Altre informazioni](object-collection.md)

![Raccolta di oggetti](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

Per impostazione predefinita, verrà inseriti nella posizione in cui l'utente è gazing vntana nel momento in cui viene avviata l'applicazione. Ciò comporta in alcuni casi un risultato indesiderato, ad esempio vntana inserito dietro una parete o all'interno di una tabella. Un fitbox consente a un utente da utilizzare sguardo per determinare la posizione in cui verrà inserito gli ologramma. Viene reso con una trama di immagine PNG semplice che può essere personalizzata facilmente con le immagini o oggetti 3D.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>Dettagli tecnici

È possibile trovare prefabs e script per la tabella periodico dell'app elementi sul [mista realtà progettazione Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="application-examples"></a>Esempi di applicazioni

Di seguito sono riportate alcune idee per ciò che è possibile creare, sfruttando i componenti di questo progetto.

### <a name="stock-data-visualization-app"></a>App di visualizzazione dati azionari

Usa i controlli stesso e un modello di interazione della tabella periodico dell'esempio di elementi, è possibile creare un'app che visualizza dati di mercato azionario. Questo esempio Usa il controllo di raccolta di oggetti per il layout dei dati predefiniti in una forma sferica. È possibile immaginare una visualizzazione dettagli in cui è stato possibile visualizzare informazioni aggiuntive su ogni titolo in modo interessante.

![Esempio di applicazione: Finanziari (1 di 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Esempio di applicazione: Finanziari (2 di 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![Esempio di applicazione: Finanziari (3 di 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*Un esempio di come usare la raccolta di oggetti utilizzata nella tabella periodico dell'app di esempio di elementi in un'app finance*

### <a name="sports-app"></a>App di sport

Questo è un esempio di visualizzazione dei dati sportivi con raccolta di oggetti e degli altri componenti dalla tabella periodico dell'app di esempio di elementi.

![Esempio di applicazione: Sport (1 di 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Esempio di applicazione: Sport (2 di 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![Esempio di applicazione: Sport (3 di 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*Un esempio di come la raccolta di oggetti utilizzati nella tabella periodico di appcould l'esempio elementi utilizzabile in un'app di sport*

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche

* [Oggetto si](interactable-object.md)
* [Raccolta di oggetti](object-collection.md)
