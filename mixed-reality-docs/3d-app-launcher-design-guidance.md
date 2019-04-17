---
title: Linee guida di progettazione di app 3D dell'utilità di avvio
description: Un'utilità di avvio app 3D è un oggetto "physical" in casa di realtà mista dell'utente che è possibile scegliere di avviare un'app.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, utilità di avvio app 3D, visore VR immersivi, il cubo in tempo reale
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598552"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="c7db8-104">Linee guida di progettazione di app 3D dell'utilità di avvio</span><span class="sxs-lookup"><span data-stu-id="c7db8-104">3D app launcher design guidance</span></span>

<span data-ttu-id="c7db8-105">Quando si inserisce in un auricolare (VR) coinvolgente di realtà mista di Windows, si immette la realtà mista di Windows home, visualizzato come una casa in un precipizio racchiuso tra le montagne e acqua (anche se è possibile [scegliere altri ambienti e persino crearne di propri](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="c7db8-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="c7db8-106">Nello spazio di questo home, un utente è libero di gestire e organizzare gli oggetti 3D e le app che si preoccupi di qualsiasi modalità che preferiscono.</span><span class="sxs-lookup"><span data-stu-id="c7db8-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="c7db8-107">Oggetto **utilità di avvio app 3D** è casa realtà che è possibile scegliere di avviare un'app mista di un oggetto "physical" dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c7db8-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="c7db8-108">![Esempio: Utilità di avvio di Mobile Bird app 3D](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7db8-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="c7db8-109">*Esempio di utilità di avvio di Mobile Bird app 3D (fittizia app)*</span><span class="sxs-lookup"><span data-stu-id="c7db8-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="c7db8-110">Processo di creazione dell'utilità di avvio app 3D</span><span class="sxs-lookup"><span data-stu-id="c7db8-110">3D app launcher creation process</span></span>

<span data-ttu-id="c7db8-111">Sono previsti 3 passaggi per la creazione di un'utilità di avvio app 3D:</span><span class="sxs-lookup"><span data-stu-id="c7db8-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="c7db8-112">Progettazione e concepting (questo articolo)</span><span class="sxs-lookup"><span data-stu-id="c7db8-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="c7db8-113">Modellazione e l'esportazione</span><span class="sxs-lookup"><span data-stu-id="c7db8-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="c7db8-114">L'integrazione nell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="c7db8-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="c7db8-115">App UWP</span><span class="sxs-lookup"><span data-stu-id="c7db8-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="c7db8-116">App Win32</span><span class="sxs-lookup"><span data-stu-id="c7db8-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="c7db8-117">Concetti relativi alla progettazione</span><span class="sxs-lookup"><span data-stu-id="c7db8-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="c7db8-118">Fantastico ancora familiare</span><span class="sxs-lookup"><span data-stu-id="c7db8-118">Fantastic yet familiar</span></span>

<span data-ttu-id="c7db8-119">L'ambiente di realtà mista di Windows in che si trova l'icona di avvio delle app è parte familiare, parte eroi sempre/sci-fi.</span><span class="sxs-lookup"><span data-stu-id="c7db8-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="c7db8-120">L'utilità di avvio migliore seguono le regole di questo mondo.</span><span class="sxs-lookup"><span data-stu-id="c7db8-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="c7db8-121">Pensare a come è possibile accettare un oggetto familiare e rappresentativo dall'app, ma piegare alcune delle regole di realtà effettivo.</span><span class="sxs-lookup"><span data-stu-id="c7db8-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="c7db8-122">Magic verrà generato.</span><span class="sxs-lookup"><span data-stu-id="c7db8-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="c7db8-123">intuitivo</span><span class="sxs-lookup"><span data-stu-id="c7db8-123">Intuitive</span></span>

<span data-ttu-id="c7db8-124">Quando si esamina l'utilità di avvio di app, lo scopo - per avviare l'app - dovrebbe essere evidente e non dovrebbe causare confusione.</span><span class="sxs-lookup"><span data-stu-id="c7db8-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="c7db8-125">Assicurarsi, ad esempio, che l'utilità di avvio è un ovvio sufficientemente rappresentativo dell'app che non verranno confusi per un dato decor in House di Cliff.</span><span class="sxs-lookup"><span data-stu-id="c7db8-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="c7db8-126">L'utilità di avvio di app deve invitare persone a tocco/select si.</span><span class="sxs-lookup"><span data-stu-id="c7db8-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="c7db8-127">![Esempio: Nuova utilità di avvio nota app 3D](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7db8-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="c7db8-128">*Nuova nota 3D app dell'utilità di avvio di esempio (fittizio app)*</span><span class="sxs-lookup"><span data-stu-id="c7db8-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="c7db8-129">Scalabilità home</span><span class="sxs-lookup"><span data-stu-id="c7db8-129">Home scale</span></span>

<span data-ttu-id="c7db8-130">Nelle schermate di avvio app 3D in tempo reale in House di Cliff e le dimensioni predefinite devono essere usati con gli altri oggetti "physical" nello spazio.</span><span class="sxs-lookup"><span data-stu-id="c7db8-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="c7db8-131">Se si inseriscono le utilità di avvio-beside, ad esempio, un impianto di casa o alcuni mobili, dovrebbe risultare a casa, size-wise.</span><span class="sxs-lookup"><span data-stu-id="c7db8-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="c7db8-132">Un buon punto di partenza consiste nel verificarne l'aspetto in centimetri cubiche 30, tenere presente che gli utenti possono scalare verso l'alto o verso il basso se desiderano.</span><span class="sxs-lookup"><span data-stu-id="c7db8-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="c7db8-133">Il proprietario da dispositivo</span><span class="sxs-lookup"><span data-stu-id="c7db8-133">Own-able</span></span>

<span data-ttu-id="c7db8-134">L'icona di avvio dovrebbe risultare simile a un oggetto persona sarebbe entusiasti di avere nel proprio spazio.</span><span class="sxs-lookup"><span data-stu-id="c7db8-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="c7db8-135">Si sarà essere praticamente circostante autonomamente con queste cose, in modo che l'utilità di avvio dovrebbe risultare simile al pensiero di utente è stata abbastanza utile cercare e mantenere vicini.</span><span class="sxs-lookup"><span data-stu-id="c7db8-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="c7db8-136">![Esempio: Utilità di avvio app 3D atomi Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7db8-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="c7db8-137">*Esempio di utilità di avvio app 3D atomi Warp (fittizia app)*</span><span class="sxs-lookup"><span data-stu-id="c7db8-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="c7db8-138">Riconoscibile</span><span class="sxs-lookup"><span data-stu-id="c7db8-138">Recognizable</span></span>

<span data-ttu-id="c7db8-139">L'utilità di avvio app 3D debba esprimere istantaneamente "marchio dell'app" a chi visualizzarlo.</span><span class="sxs-lookup"><span data-stu-id="c7db8-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="c7db8-140">Se si dispone di un carattere a stella o a un oggetto soprattutto personali nell'app, è consigliabile usarlo come gran parte della progettazione.</span><span class="sxs-lookup"><span data-stu-id="c7db8-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="c7db8-141">In un mondo di realtà mista, un oggetto verrà suscitare l'interesse più utenti rispetto a semplicemente un logo da solo.</span><span class="sxs-lookup"><span data-stu-id="c7db8-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="c7db8-142">Oggetti riconoscibili comunicano marchio semplice e rapido.</span><span class="sxs-lookup"><span data-stu-id="c7db8-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="c7db8-143">Volumetrici</span><span class="sxs-lookup"><span data-stu-id="c7db8-143">Volumetric</span></span>

<span data-ttu-id="c7db8-144">L'applicazione merita i più della semplice inserendo il logo personalizzato su un piano flat e la chiamata a tutto il giorno.</span><span class="sxs-lookup"><span data-stu-id="c7db8-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="c7db8-145">L'utilità di avvio dovrebbe risultare, ad esempio un oggetto interessante, 3D, fisico nello spazio dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c7db8-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="c7db8-146">Un buon approccio è immaginare che l'app stava per avere una bolla nel giorno del ringraziamento YCbCr di Macy.</span><span class="sxs-lookup"><span data-stu-id="c7db8-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="c7db8-147">Chiedersi che cosa sarebbe stupire persone come proviene strada?</span><span class="sxs-lookup"><span data-stu-id="c7db8-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="c7db8-148">Aspetto eccezionale da tutti gli angoli di visualizzazione?</span><span class="sxs-lookup"><span data-stu-id="c7db8-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="c7db8-149">Suggerimenti per la buona modelli 3D</span><span class="sxs-lookup"><span data-stu-id="c7db8-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="c7db8-150">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="c7db8-150">Best practices</span></span>
* <span data-ttu-id="c7db8-151">Quando si pianificano le quote dell'utilità di avvio di app, riprese per circa un cubo 30cm.</span><span class="sxs-lookup"><span data-stu-id="c7db8-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="c7db8-152">Pertanto, un valore 1: proporzioni 1:1.</span><span class="sxs-lookup"><span data-stu-id="c7db8-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="c7db8-153">I modelli devono essere meno di 10.000 poligoni.</span><span class="sxs-lookup"><span data-stu-id="c7db8-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="c7db8-154">Altre informazioni sui livelli dei dettagli (LOD) e i conteggi di triangolo</span><span class="sxs-lookup"><span data-stu-id="c7db8-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="c7db8-155">Test su un visore VR immersivi quando possibile.</span><span class="sxs-lookup"><span data-stu-id="c7db8-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="c7db8-156">Dettagli di compilazione nella geometria del modello dove possibile, non si basano su trame per informazioni dettagliate.</span><span class="sxs-lookup"><span data-stu-id="c7db8-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="c7db8-157">Compilare la geometria "acqua stretta" chiusa.</span><span class="sxs-lookup"><span data-stu-id="c7db8-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="c7db8-158">Nessun buchi che non sono modellate in.</span><span class="sxs-lookup"><span data-stu-id="c7db8-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="c7db8-159">Utilizzare materiali naturale nell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c7db8-159">Use natural materials in your object.</span></span> <span data-ttu-id="c7db8-160">Si supponga alla creazione nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="c7db8-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="c7db8-161">Assicurarsi che il modello legge correttamente alle dimensioni e le distanze diverse.</span><span class="sxs-lookup"><span data-stu-id="c7db8-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="c7db8-162">Quando il modello è pronto per iniziare, leggere il [esportazione di linee guida per gli asset](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="c7db8-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="c7db8-163">![Modello con dettagli nella trama](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7db8-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="c7db8-164">*Modello con dettagli nella trama*</span><span class="sxs-lookup"><span data-stu-id="c7db8-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="c7db8-165">Cosa evitare</span><span class="sxs-lookup"><span data-stu-id="c7db8-165">What to avoid</span></span>
* <span data-ttu-id="c7db8-166">Non usare i dettagli a contrasto elevato o modelli di piccole dimensioni, occupati e trame.</span><span class="sxs-lookup"><span data-stu-id="c7db8-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="c7db8-167">Non usare geometry thin: non funzionare bene a una distanza, alias in modo errato.</span><span class="sxs-lookup"><span data-stu-id="c7db8-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="c7db8-168">Non lasciare che le parti del modello di estendere troppo oltre il 1: proporzioni 1:1.</span><span class="sxs-lookup"><span data-stu-id="c7db8-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="c7db8-169">Problemi di scalabilità verrà creato.</span><span class="sxs-lookup"><span data-stu-id="c7db8-169">It will create scaling problems.</span></span>

<span data-ttu-id="c7db8-170">![Evitare i modelli di occupato a contrasto elevato di piccole dimensioni](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7db8-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="c7db8-171">*Evitare i modelli a contrasto elevato, piccoli, occupati*</span><span class="sxs-lookup"><span data-stu-id="c7db8-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="c7db8-172">Come tipo di handle</span><span class="sxs-lookup"><span data-stu-id="c7db8-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="c7db8-173">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="c7db8-173">Best practices</span></span>
* <span data-ttu-id="c7db8-174">È consigliabile il tipo è costituito da circa 1/3 di utilità di avvio di app (o più).</span><span class="sxs-lookup"><span data-stu-id="c7db8-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="c7db8-175">Il tipo è la cosa principale che offre agli utenti un'idea che è l'utilità di avvio, infatti, un'utilità di avvio in modo che se non si verificano se è piuttosto notevole.</span><span class="sxs-lookup"><span data-stu-id="c7db8-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="c7db8-176">Evitare l'esecuzione di tipo wide super: provare per contenerlo entro i confini dell'utilità di avvio di app le quote di core (più o meno).</span><span class="sxs-lookup"><span data-stu-id="c7db8-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="c7db8-177">Tipo flat può funzionare, ma tenere presente che può essere difficile da visualizzare da alcuni punti di vista e in alcuni ambienti.</span><span class="sxs-lookup"><span data-stu-id="c7db8-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="c7db8-178">È possibile applicarlo a un oggetto solid o dello sfondo dietro di essa per facilitare questa operazione.</span><span class="sxs-lookup"><span data-stu-id="c7db8-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="c7db8-179">Dimensione aggiunta al tipo ritiene interessante in 3D.</span><span class="sxs-lookup"><span data-stu-id="c7db8-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="c7db8-180">Ombreggiatura i lati del tipo di un colore diverso e più scuro utili per migliorare la leggibilità.</span><span class="sxs-lookup"><span data-stu-id="c7db8-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="c7db8-181">**Colori di tipo che funzionano**</span><span class="sxs-lookup"><span data-stu-id="c7db8-181">**Type colors that work**</span></span>
* <span data-ttu-id="c7db8-182">Bianco</span><span class="sxs-lookup"><span data-stu-id="c7db8-182">White</span></span>
* <span data-ttu-id="c7db8-183">Nero</span><span class="sxs-lookup"><span data-stu-id="c7db8-183">Black</span></span>
* <span data-ttu-id="c7db8-184">Brillante semi-saturazione colore</span><span class="sxs-lookup"><span data-stu-id="c7db8-184">Bright semi-saturated color</span></span>

<span data-ttu-id="c7db8-185">![Digitare i colori che funzionano.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7db8-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="c7db8-186">*Colori di tipo che funzionano*</span><span class="sxs-lookup"><span data-stu-id="c7db8-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="c7db8-187">Cosa evitare</span><span class="sxs-lookup"><span data-stu-id="c7db8-187">What to avoid</span></span>

<span data-ttu-id="c7db8-188">**Colori di tipo che causano problemi**</span><span class="sxs-lookup"><span data-stu-id="c7db8-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="c7db8-189">Tonalità medie</span><span class="sxs-lookup"><span data-stu-id="c7db8-189">Mid-tones</span></span>
* <span data-ttu-id="c7db8-190">Grigio</span><span class="sxs-lookup"><span data-stu-id="c7db8-190">Gray</span></span>
* <span data-ttu-id="c7db8-191">Overcommit saturazione dei colori o colori desaturati</span><span class="sxs-lookup"><span data-stu-id="c7db8-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="c7db8-192">![Digitare i colori che causano problemi.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7db8-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="c7db8-193">*Colori di tipo che causano problemi*</span><span class="sxs-lookup"><span data-stu-id="c7db8-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="c7db8-194">Luce</span><span class="sxs-lookup"><span data-stu-id="c7db8-194">Lighting</span></span>

<span data-ttu-id="c7db8-195">L'illuminazione per l'utilità di avvio app provenienti dall'ambiente Cliff House.</span><span class="sxs-lookup"><span data-stu-id="c7db8-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="c7db8-196">Assicurarsi di testare l'utilità di avvio in diverse posizioni in tutta la casa, in modo esito positivo in chiaro e ombreggiature.</span><span class="sxs-lookup"><span data-stu-id="c7db8-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="c7db8-197">La buona notizia è, se sono stati eseguiti altri linee guida di progettazione in questo documento, l'utilità di avvio deve essere abbastanza corrette per la maggior parte delle illuminazione in House di Cliff.</span><span class="sxs-lookup"><span data-stu-id="c7db8-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="c7db8-198">Ottimo strumento per testare come l'utilità di avvio appare in varie luci nell'ambiente è di Studio, chat Room Media, in qualsiasi punto esterno e terrazzo indietro (l'area concreto con le Prato).</span><span class="sxs-lookup"><span data-stu-id="c7db8-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="c7db8-199">Un altro, è possibile inserirlo nella metà e ombre metà e vedere l'effetto.</span><span class="sxs-lookup"><span data-stu-id="c7db8-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="c7db8-200">![Assicurarsi che l'utilità di avvio sono corrette in chiaro e ombreggiature.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c7db8-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="c7db8-201">*Assicurarsi che l'utilità di avvio sono corrette in chiaro e ombreggiature*</span><span class="sxs-lookup"><span data-stu-id="c7db8-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="c7db8-202">La trama</span><span class="sxs-lookup"><span data-stu-id="c7db8-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="c7db8-203">Le trame di creazione</span><span class="sxs-lookup"><span data-stu-id="c7db8-203">Authoring your textures</span></span>

<span data-ttu-id="c7db8-204">Il formato finale dell'utilità di avvio app 3D sarà un file .glb, che viene eseguito tramite la pipeline PBR (Rendering fisicamente base).</span><span class="sxs-lookup"><span data-stu-id="c7db8-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="c7db8-205">Può trattarsi di un processo difficile, ora è un buon momento per impiegare un artista tecnico se già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="c7db8-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="c7db8-206">Se si ha un coraggioso fai da te-UT, avere inviato [ricerche e informazioni sulla terminologia PBR](http://wiki.polycount.com/wiki/PBR) e ciò che accade dietro le quinte prima di iniziare per evitare gli errori più comuni.</span><span class="sxs-lookup"><span data-stu-id="c7db8-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="c7db8-207">![Esempio: App nuova nota](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="c7db8-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="c7db8-208">*Nuova nota 3D app dell'utilità di avvio di esempio (fittizio app)*</span><span class="sxs-lookup"><span data-stu-id="c7db8-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="c7db8-209">**Strumento di creazione e modifica consigliato**</span><span class="sxs-lookup"><span data-stu-id="c7db8-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="c7db8-210">È consigliabile usare [sostanza pittore](https://www.allegorithmic.com/products/substance-painter) da Allegorithmic per creare il file finale.</span><span class="sxs-lookup"><span data-stu-id="c7db8-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="c7db8-211">Se non si ha familiarità con la creazione di shader PBR in sostanza, del pittore una [esercitazione](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="c7db8-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="c7db8-212">(In alternativa [3D Coat](https://3dcoat.com/home/), [Suite Quixel 2](https://quixel.se/suite2/), o [Marmoset Toolbag](https://www.marmoset.co/toolbag/) funzionerebbe anche se non ha maggiore familiarità con uno di questi.)</span><span class="sxs-lookup"><span data-stu-id="c7db8-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="c7db8-213">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="c7db8-213">Best practices</span></span>

* <span data-ttu-id="c7db8-214">Se l'oggetto dell'utilità di avvio di app è stata creata per PBR, dovrebbe essere piuttosto semplice per convertirlo per l'ambiente di Cliff House.</span><span class="sxs-lookup"><span data-stu-id="c7db8-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="c7db8-215">Il shader si aspetta un flusso di lavoro Metal/asperità: The PBR Unreal shader è un facsimile chiude.</span><span class="sxs-lookup"><span data-stu-id="c7db8-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="c7db8-216">Quando l'esportazione le trame di mantenere la [consiglia le dimensioni della trama](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) presente.</span><span class="sxs-lookup"><span data-stu-id="c7db8-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="c7db8-217">Assicurarsi di compilare gli oggetti per l'illuminazione in tempo reale: ciò significa che:</span><span class="sxs-lookup"><span data-stu-id="c7db8-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="c7db8-218">Evitare virtuali create con bake shadows – o ombreggiature disegnate</span><span class="sxs-lookup"><span data-stu-id="c7db8-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="c7db8-219">Evitare di illuminazione virtuali create con bake nelle trame</span><span class="sxs-lookup"><span data-stu-id="c7db8-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="c7db8-220">Usare uno dei materiali PBR creazione di pacchetti per le mappe a destra generate per il shader</span><span class="sxs-lookup"><span data-stu-id="c7db8-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="c7db8-221">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c7db8-221">See also</span></span>

* [<span data-ttu-id="c7db8-222">Creare modelli 3D per l'utilizzo in realtà mista home</span><span class="sxs-lookup"><span data-stu-id="c7db8-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="c7db8-223">Implementare nelle schermate di avvio app 3D (app UWP)</span><span class="sxs-lookup"><span data-stu-id="c7db8-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="c7db8-224">Implementare nelle schermate di avvio app 3D (app Win32)</span><span class="sxs-lookup"><span data-stu-id="c7db8-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
