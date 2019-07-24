---
title: Tavola periodica degli elementi
description: La tabella periodica degli elementi è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs, in cui è possibile apprendere come disporre una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una raccolta di oggetti.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, app di esempio, controlli
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525307"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="ffa90-104">Tavola periodica degli elementi</span><span class="sxs-lookup"><span data-stu-id="ffa90-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="ffa90-105">Questo articolo illustra un esempio esplorativo creato nei [laboratori di progettazione della realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), un posto in cui si condividono le informazioni e suggerimenti per lo sviluppo di app di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="ffa90-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="ffa90-106">Gli articoli e il codice correlati alla progettazione si evolveranno Man mano che si effettuano nuove individuazioni.</span><span class="sxs-lookup"><span data-stu-id="ffa90-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="ffa90-107">[La tabella periodica degli elementi](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs.</span><span class="sxs-lookup"><span data-stu-id="ffa90-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="ffa90-108">Con questo progetto è possibile apprendere come disporre una matrice di oggetti nello spazio 3D con vari tipi di superficie usando una **[raccolta di oggetti](object-collection.md)** .</span><span class="sxs-lookup"><span data-stu-id="ffa90-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="ffa90-109">Viene inoltre illustrato come creare oggetti interagibili che rispondono agli input standard da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ffa90-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="ffa90-110">È possibile usare i componenti di questo progetto per creare un'esperienza di app per realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ffa90-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabella del periodo dell'app elementi](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="ffa90-112">Informazioni sull'app</span><span class="sxs-lookup"><span data-stu-id="ffa90-112">About the app</span></span>

<span data-ttu-id="ffa90-113">La tabella periodica degli elementi Visualizza gli elementi chimici e ognuna delle relative proprietà in uno spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="ffa90-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="ffa90-114">Incorpora le interazioni di base di HoloLens, ad esempio lo sguardo e il tocco aereo.</span><span class="sxs-lookup"><span data-stu-id="ffa90-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="ffa90-115">Gli utenti possono ottenere informazioni sugli elementi con i modelli 3D animati.</span><span class="sxs-lookup"><span data-stu-id="ffa90-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="ffa90-116">Possono comprendere visivamente la Shell degli elettroni di un elemento e il suo nucleo, composto da protoni e neutroni.</span><span class="sxs-lookup"><span data-stu-id="ffa90-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="ffa90-117">Sfondo</span><span class="sxs-lookup"><span data-stu-id="ffa90-117">Background</span></span>

<span data-ttu-id="ffa90-118">Dopo la prima volta che ho sperimentato HoloLens, un'app di tabella periodica era un'idea che ho voluto sperimentare in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ffa90-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="ffa90-119">Poiché ogni elemento dispone di molti punti dati visualizzati con testo, ho pensato che sarebbe stato molto soggetto per l'esplorazione della composizione tipografica in uno spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="ffa90-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="ffa90-120">La possibilità di visualizzare il modello Electron dell'elemento era un'altra parte interessante di questo progetto.</span><span class="sxs-lookup"><span data-stu-id="ffa90-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="ffa90-121">Progettazione</span><span class="sxs-lookup"><span data-stu-id="ffa90-121">Design</span></span>

<span data-ttu-id="ffa90-122">Per la visualizzazione predefinita della tabella periodica, ho immaginato le caselle tridimensionali che contenevano il modello Electron di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="ffa90-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="ffa90-123">La superficie di ogni casella sarà translucida, in modo che l'utente possa ottenere un'idea approssimativa del volume dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="ffa90-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="ffa90-124">Con lo sguardo e il tocco aereo, l'utente può aprire una visualizzazione dettagliata di ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="ffa90-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="ffa90-125">Per fare in modo che la transizione tra la visualizzazione tabella e la visualizzazione dei dettagli sia uniforme e naturale, è stata creata in modo analogo all'interazione fisica di una scatola aperta in vita reale.</span><span class="sxs-lookup"><span data-stu-id="ffa90-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="ffa90-126">![Schizzo di progettazione](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="ffa90-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="ffa90-127">*Schizzi di progettazione*</span><span class="sxs-lookup"><span data-stu-id="ffa90-127">*Design sketches*</span></span>

<span data-ttu-id="ffa90-128">In visualizzazione dettagli, ho voluto visualizzare le informazioni di ogni elemento con un testo con rendering bello nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="ffa90-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="ffa90-129">Il modello di elettroni 3D animato viene visualizzato nell'area centrale e può essere visualizzato da diverse angolazioni.</span><span class="sxs-lookup"><span data-stu-id="ffa90-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interazione](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="ffa90-131">![Prototipi](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="ffa90-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="ffa90-132">*Prototipi di interazione*</span><span class="sxs-lookup"><span data-stu-id="ffa90-132">*Interaction prototypes*</span></span>

<span data-ttu-id="ffa90-133">L'utente può modificare il tipo di superficie per aria toccando i pulsanti nella parte inferiore della tabella, che possono spostarsi tra il piano, il cilindro, la sfera e la dispersione.</span><span class="sxs-lookup"><span data-stu-id="ffa90-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="ffa90-134">Controlli e modelli comuni usati in questa app</span><span class="sxs-lookup"><span data-stu-id="ffa90-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="ffa90-135">Oggetto interagibile (pulsante)</span><span class="sxs-lookup"><span data-stu-id="ffa90-135">Interactable object (button)</span></span>

<span data-ttu-id="ffa90-136">L' [oggetto interagibile](interactable-object.md) è un oggetto che può rispondere agli input HoloLens di base.</span><span class="sxs-lookup"><span data-stu-id="ffa90-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="ffa90-137">Viene fornito come prefabbricato/script che è possibile applicare facilmente a qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="ffa90-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="ffa90-138">Ad esempio, è possibile rendere interattivo un caffè nella scena e rispondere a input come lo sguardo, il tocco aereo, i movimenti di spostamento e manipolazione.</span><span class="sxs-lookup"><span data-stu-id="ffa90-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="ffa90-139">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="ffa90-139">Learn more</span></span>](interactable-object.md)

![oggetto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="ffa90-141">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="ffa90-141">Object collection</span></span>

<span data-ttu-id="ffa90-142">La [raccolta](object-collection.md) di oggetti è un oggetto che consente di disporre più oggetti in varie forme.</span><span class="sxs-lookup"><span data-stu-id="ffa90-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="ffa90-143">Supporta piani, cilindri, sfere e dispersione.</span><span class="sxs-lookup"><span data-stu-id="ffa90-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="ffa90-144">È possibile configurare proprietà aggiuntive, ad esempio raggio, numero di righe e spaziatura.</span><span class="sxs-lookup"><span data-stu-id="ffa90-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="ffa90-145">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="ffa90-145">Learn more</span></span>](object-collection.md)

![Raccolta di oggetti](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="ffa90-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="ffa90-147">Fitbox</span></span>

<span data-ttu-id="ffa90-148">Per impostazione predefinita, gli ologrammi verranno posizionati nella posizione in cui l'utente sta guardando nel momento in cui viene avviata l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="ffa90-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="ffa90-149">Questo comporta talvolta un risultato indesiderato, ad esempio gli ologrammi posizionati dietro una parete o al centro di una tabella.</span><span class="sxs-lookup"><span data-stu-id="ffa90-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="ffa90-150">Un fitbox consente all'utente di usare lo sguardo per determinare la posizione in cui verrà inserito l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="ffa90-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="ffa90-151">Viene eseguita con una semplice trama di immagini PNG, che può essere facilmente personalizzata con le immagini o gli oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="ffa90-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="ffa90-153">Dettagli tecnici</span><span class="sxs-lookup"><span data-stu-id="ffa90-153">Technical details</span></span>

<span data-ttu-id="ffa90-154">È possibile trovare gli script e i prefabbricati per la tabella periodica dell'app elementi nel [progetto Mixed Reality Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="ffa90-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="ffa90-155">Esempi di applicazioni</span><span class="sxs-lookup"><span data-stu-id="ffa90-155">Application examples</span></span>

<span data-ttu-id="ffa90-156">Di seguito sono riportate alcune idee per le operazioni che è possibile creare sfruttando i componenti di questo progetto.</span><span class="sxs-lookup"><span data-stu-id="ffa90-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="ffa90-157">App visualizzazione dati azionari</span><span class="sxs-lookup"><span data-stu-id="ffa90-157">Stock data visualization app</span></span>

<span data-ttu-id="ffa90-158">Usando gli stessi controlli e il modello di interazione della tabella periodica dell'esempio Elements, è possibile creare un'app che visualizzi i dati del mercato azionario.</span><span class="sxs-lookup"><span data-stu-id="ffa90-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="ffa90-159">In questo esempio viene utilizzato il controllo della raccolta di oggetti per disporre i dati azionari in una forma sferica.</span><span class="sxs-lookup"><span data-stu-id="ffa90-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="ffa90-160">È possibile immaginare una visualizzazione dettagli in cui è possibile visualizzare informazioni aggiuntive su ogni titolo in modo interessante.</span><span class="sxs-lookup"><span data-stu-id="ffa90-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Esempio di applicazione: Finanza (1 di 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Esempio di applicazione: Finanza (2 di 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="ffa90-163">![Esempio di applicazione: Finanza (3 di 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="ffa90-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="ffa90-164">*Un esempio di come la raccolta di oggetti usata nella tabella periodica dell'app di esempio Elements può essere usata in un'app Finance*</span><span class="sxs-lookup"><span data-stu-id="ffa90-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="ffa90-165">App per sportivi</span><span class="sxs-lookup"><span data-stu-id="ffa90-165">Sports app</span></span>

<span data-ttu-id="ffa90-166">Questo è un esempio di visualizzazione dei dati sportivi tramite la raccolta di oggetti e altri componenti dalla tabella periodica dell'app di esempio Elements.</span><span class="sxs-lookup"><span data-stu-id="ffa90-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Esempio di applicazione: Sport (1 di 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Esempio di applicazione: Sport (2 di 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="ffa90-169">![Esempio di applicazione: Sport (3 di 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="ffa90-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="ffa90-170">*Un esempio di come usare la raccolta di oggetti nella tabella periodica degli elementi di esempio appcould in un'app sportiva*</span><span class="sxs-lookup"><span data-stu-id="ffa90-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="ffa90-171">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="ffa90-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ffa90-172"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="ffa90-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="ffa90-173">Progettazione UX@Microsoft</span><span class="sxs-lookup"><span data-stu-id="ffa90-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="ffa90-174">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ffa90-174">See also</span></span>

* [<span data-ttu-id="ffa90-175">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="ffa90-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ffa90-176">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="ffa90-176">Object collection</span></span>](object-collection.md)
