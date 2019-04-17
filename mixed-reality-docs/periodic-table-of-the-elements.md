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
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="6999a-104">Tabella periodico degli elementi</span><span class="sxs-lookup"><span data-stu-id="6999a-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="6999a-105">Questo articolo illustra un esempio di analisi esplorativo è stata creata nel [laboratori di progettazione di realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), una posizione in cui si condivide quanto appreso sulle e per suggerimenti su mista lo sviluppo di app di realtà.</span><span class="sxs-lookup"><span data-stu-id="6999a-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="6999a-106">Nostri articoli correlati alla progettazione e il codice si evolverà come si ottengono nuove informazioni.</span><span class="sxs-lookup"><span data-stu-id="6999a-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="6999a-107">[Tabella periodico degli elementi](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) è un'app di esempio open source di laboratori di progettazione realtà mista di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6999a-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="6999a-108">Con questo progetto, è possibile imparare a layout di una matrice di oggetti nello spazio 3D con vari tipi di area con un  **[raccolta di oggetti](object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="6999a-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="6999a-109">Anche imparare a creare oggetti si che rispondono a input standard da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6999a-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="6999a-110">È possibile utilizzare i componenti del progetto per creare la propria esperienza di app di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="6999a-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Periodo nella tabella dell'app elementi](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="6999a-112">Sull'app</span><span class="sxs-lookup"><span data-stu-id="6999a-112">About the app</span></span>

<span data-ttu-id="6999a-113">Tabella periodico degli elementi Visualizza gli elementi prodotti chimici e ognuna delle proprietà nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="6999a-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="6999a-114">Incorpora le interazioni di base di HoloLens, ad esempio toccare sguardo e aria.</span><span class="sxs-lookup"><span data-stu-id="6999a-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="6999a-115">Gli utenti possono informazioni sugli elementi con modelli 3D animati.</span><span class="sxs-lookup"><span data-stu-id="6999a-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="6999a-116">È possibile comprendere visivamente shell electron di un elemento e il nucleo - composto da protons e neutrons.</span><span class="sxs-lookup"><span data-stu-id="6999a-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="6999a-117">Informazioni</span><span class="sxs-lookup"><span data-stu-id="6999a-117">Background</span></span>

<span data-ttu-id="6999a-118">Dopo aver visto prima HoloLens, un'app table periodica è stata un'idea che sapevo che volevo possano sperimentarlo in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="6999a-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="6999a-119">Poiché ogni elemento dispone di numerosi punti dati che vengono visualizzati con testo, pensato che sarebbe ideale in materia di analisi composizione tipografica nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="6999a-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="6999a-120">La possibilità di visualizzare il modello dell'elemento electron era un'altra parte interessante di questo progetto.</span><span class="sxs-lookup"><span data-stu-id="6999a-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="6999a-121">Progettazione</span><span class="sxs-lookup"><span data-stu-id="6999a-121">Design</span></span>

<span data-ttu-id="6999a-122">Per la visualizzazione predefinita della tabella periodico, immaginato in precedenza caselle tridimensionale che contengono il modello di electron di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="6999a-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="6999a-123">L'area di ogni casella sarebbe semitrasparente in modo che l'utente è stato possibile ottenere un'idea approssimativa del volume dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="6999a-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="6999a-124">Con il tocco sguardo e aria, l'utente è stato possibile aprire una visualizzazione dettagliata di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="6999a-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="6999a-125">Per rendere la transizione tra la visualizzazione di tabella e vista dettagliata semplice e naturale, reso simile all'interazione fisica di una casella di apertura in uno scenario reale.</span><span class="sxs-lookup"><span data-stu-id="6999a-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="6999a-126">![Sketch di progettazione](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="6999a-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="6999a-127">*Disegni di progettazione*</span><span class="sxs-lookup"><span data-stu-id="6999a-127">*Design sketches*</span></span>

<span data-ttu-id="6999a-128">Nel riquadro dettagli, vorrei visualizzare le informazioni di ogni elemento con il testo sofisticato nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="6999a-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="6999a-129">Il modello di electron 3D animate viene visualizzato nell'area centrale e può essere visualizzato da diverse angolazioni.</span><span class="sxs-lookup"><span data-stu-id="6999a-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interazione](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="6999a-131">![Prototipi](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="6999a-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="6999a-132">*Prototipi di interazione*</span><span class="sxs-lookup"><span data-stu-id="6999a-132">*Interaction prototypes*</span></span>

<span data-ttu-id="6999a-133">L'utente può modificare il tipo di area per via aerea toccando i pulsanti nella parte inferiore della tabella, possono passare tra piano, cilindro, sphere e a dispersione.</span><span class="sxs-lookup"><span data-stu-id="6999a-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="6999a-134">I modelli usati in questa app e i controlli comuni</span><span class="sxs-lookup"><span data-stu-id="6999a-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="6999a-135">Oggetto si (pulsante)</span><span class="sxs-lookup"><span data-stu-id="6999a-135">Interactable object (button)</span></span>

<span data-ttu-id="6999a-136">[Oggetto si](interactable-object.md) è un oggetto che può rispondere all'input di base HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6999a-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="6999a-137">Viene fornito come un prefab/script che è possibile applicare facilmente a qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="6999a-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="6999a-138">Ad esempio, è possibile rendere una tazza di caffè nella scena si e rispondere agli input, ad esempio sguardo, gesti di navigazione e modifica e indice puntato.</span><span class="sxs-lookup"><span data-stu-id="6999a-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="6999a-139">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="6999a-139">Learn more</span></span>](interactable-object.md)

![oggetto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="6999a-141">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="6999a-141">Object collection</span></span>

<span data-ttu-id="6999a-142">[Raccolta di oggetti](object-collection.md) è un oggetto che consente definire il layout più oggetti in varie forme.</span><span class="sxs-lookup"><span data-stu-id="6999a-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="6999a-143">Supporta piano, cilindro, sphere e a dispersione.</span><span class="sxs-lookup"><span data-stu-id="6999a-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="6999a-144">È possibile configurare proprietà aggiuntive, ad esempio radius, il numero di righe e la spaziatura.</span><span class="sxs-lookup"><span data-stu-id="6999a-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="6999a-145">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="6999a-145">Learn more</span></span>](object-collection.md)

![Raccolta di oggetti](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="6999a-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="6999a-147">Fitbox</span></span>

<span data-ttu-id="6999a-148">Per impostazione predefinita, verrà inseriti nella posizione in cui l'utente è gazing vntana nel momento in cui viene avviata l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6999a-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="6999a-149">Ciò comporta in alcuni casi un risultato indesiderato, ad esempio vntana inserito dietro una parete o all'interno di una tabella.</span><span class="sxs-lookup"><span data-stu-id="6999a-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="6999a-150">Un fitbox consente a un utente da utilizzare sguardo per determinare la posizione in cui verrà inserito gli ologramma.</span><span class="sxs-lookup"><span data-stu-id="6999a-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="6999a-151">Viene reso con una trama di immagine PNG semplice che può essere personalizzata facilmente con le immagini o oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="6999a-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="6999a-153">Dettagli tecnici</span><span class="sxs-lookup"><span data-stu-id="6999a-153">Technical details</span></span>

<span data-ttu-id="6999a-154">È possibile trovare prefabs e script per la tabella periodico dell'app elementi sul [mista realtà progettazione Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="6999a-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="6999a-155">Esempi di applicazioni</span><span class="sxs-lookup"><span data-stu-id="6999a-155">Application examples</span></span>

<span data-ttu-id="6999a-156">Di seguito sono riportate alcune idee per ciò che è possibile creare, sfruttando i componenti di questo progetto.</span><span class="sxs-lookup"><span data-stu-id="6999a-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="6999a-157">App di visualizzazione dati azionari</span><span class="sxs-lookup"><span data-stu-id="6999a-157">Stock data visualization app</span></span>

<span data-ttu-id="6999a-158">Usa i controlli stesso e un modello di interazione della tabella periodico dell'esempio di elementi, è possibile creare un'app che visualizza dati di mercato azionario.</span><span class="sxs-lookup"><span data-stu-id="6999a-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="6999a-159">Questo esempio Usa il controllo di raccolta di oggetti per il layout dei dati predefiniti in una forma sferica.</span><span class="sxs-lookup"><span data-stu-id="6999a-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="6999a-160">È possibile immaginare una visualizzazione dettagli in cui è stato possibile visualizzare informazioni aggiuntive su ogni titolo in modo interessante.</span><span class="sxs-lookup"><span data-stu-id="6999a-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Esempio di applicazione: Finanziari (1 di 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Esempio di applicazione: Finanziari (2 di 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="6999a-163">![Esempio di applicazione: Finanziari (3 di 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="6999a-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="6999a-164">*Un esempio di come usare la raccolta di oggetti utilizzata nella tabella periodico dell'app di esempio di elementi in un'app finance*</span><span class="sxs-lookup"><span data-stu-id="6999a-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="6999a-165">App di sport</span><span class="sxs-lookup"><span data-stu-id="6999a-165">Sports app</span></span>

<span data-ttu-id="6999a-166">Questo è un esempio di visualizzazione dei dati sportivi con raccolta di oggetti e degli altri componenti dalla tabella periodico dell'app di esempio di elementi.</span><span class="sxs-lookup"><span data-stu-id="6999a-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Esempio di applicazione: Sport (1 di 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Esempio di applicazione: Sport (2 di 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="6999a-169">![Esempio di applicazione: Sport (3 di 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="6999a-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="6999a-170">*Un esempio di come la raccolta di oggetti utilizzati nella tabella periodico di appcould l'esempio elementi utilizzabile in un'app di sport*</span><span class="sxs-lookup"><span data-stu-id="6999a-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="6999a-171">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="6999a-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="6999a-172"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="6999a-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="6999a-173">UX Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="6999a-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="6999a-174">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6999a-174">See also</span></span>

* [<span data-ttu-id="6999a-175">Oggetto si</span><span class="sxs-lookup"><span data-stu-id="6999a-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6999a-176">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="6999a-176">Object collection</span></span>](object-collection.md)
