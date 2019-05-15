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
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="5e366-104">Case study: ricerca sui difetti nella realtà</span><span class="sxs-lookup"><span data-stu-id="5e366-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="5e366-105">Quando le persone pensano realtà mista e ciò che è possibile eseguire con Microsoft HoloLens, vengono in genere adattarsi a domande quali "Quali oggetti è possibile aggiungere per la mia camera"?</span><span class="sxs-lookup"><span data-stu-id="5e366-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="5e366-106">oppure "Cosa è possibile layer sopra spazio personale?"</span><span class="sxs-lookup"><span data-stu-id="5e366-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="5e366-107">Desidero evidenziare un'altra area è possibile prendere in considerazione, essenzialmente un espediente magic, ovvero con la stessa tecnologia per la ricerca all'interno o attraverso gli oggetti fisici reali si.</span><span class="sxs-lookup"><span data-stu-id="5e366-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="5e366-108">Le tecnologie innovative</span><span class="sxs-lookup"><span data-stu-id="5e366-108">The tech</span></span>

<span data-ttu-id="5e366-109">Se è stata ritenuta gli alieni come interrompano mediante le bacheche nelle  **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, sbloccato una parete sicura nei  **[frammenti](case-study-creating-an-immersive-experience-in-fragments.md)**, o sono stati abbastanza fortunato Per visualizzare il hangar UNSC infinito nel  **[esperienza Halo 5 E3 nel 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, si conosce già cosa sto parlando.</span><span class="sxs-lookup"><span data-stu-id="5e366-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="5e366-110">In base alla propria immaginazione, questo espediente visual è utilizzabile per inserire aree libere temporanei nei muri a secco o nascondere i mondi sotto un floorboard loose.</span><span class="sxs-lookup"><span data-stu-id="5e366-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid aggiunge pipe tridimensionale e altre strutture dietro le bacheche, visibile solo tramite aree libere creati come vincere la invaders.](images/roboraid-640px.png)

<span data-ttu-id="5e366-112">RoboRaid aggiunge pipe tridimensionale e altre strutture dietro le bacheche, visibile solo tramite aree libere creati come vincere la invaders.</span><span class="sxs-lookup"><span data-stu-id="5e366-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="5e366-113">Utilizza uno di questi vntana univoco su HoloLens, un'app può conferire un effetto ottico di contenuto protetto da affisse o tramite il piano nello stesso modo che realtà si manifesta tramite una finestra effettiva.</span><span class="sxs-lookup"><span data-stu-id="5e366-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="5e366-114">Spostare manualmente a sinistra e si può vedere tutti gli elementi sul lato destro.</span><span class="sxs-lookup"><span data-stu-id="5e366-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="5e366-115">Ottenere più da vicino e noterete un po' più di tutti gli elementi.</span><span class="sxs-lookup"><span data-stu-id="5e366-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="5e366-116">La differenza principale è che fori reali permettono di tramite, mentre la parte intera parallelizzate non consentirà di salire tramite tale contenuto holographic magiche presenti.</span><span class="sxs-lookup"><span data-stu-id="5e366-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="5e366-117">(Aggiungere un'attività al backlog.)</span><span class="sxs-lookup"><span data-stu-id="5e366-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="5e366-118">Dietro le quinte</span><span class="sxs-lookup"><span data-stu-id="5e366-118">Behind the scenes</span></span>

<span data-ttu-id="5e366-119">Il trucco è una combinazione di due effetti.</span><span class="sxs-lookup"><span data-stu-id="5e366-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="5e366-120">In primo luogo, holographic contenuto sia stato aggiunto al mondo usando "spaziali anchor".</span><span class="sxs-lookup"><span data-stu-id="5e366-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="5e366-121">L'uso di punti di ancoraggio per assicurarsi che il contenuto di "world-bloccato" significa che cosa si sta cercando in non in modo visivo dello sfasamento lontano da oggetti fisici vicino al telefono, anche quando si sposta o il sistema di mapping spaziale sottostante aggiorna il modello 3D della chat.</span><span class="sxs-lookup"><span data-stu-id="5e366-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="5e366-122">In secondo luogo, che il contenuto holographic è visivamente limitato a uno spazio molto specifico, in modo che è possibile vedere solo attraverso il foro nella realtà.</span><span class="sxs-lookup"><span data-stu-id="5e366-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="5e366-123">Tale occlusione è necessario richiedere capacità attraverso un foro logica, nella finestra o trampolino, che vende il trucco.</span><span class="sxs-lookup"><span data-stu-id="5e366-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="5e366-124">Senza qualcosa blocca la maggior parte della vista, un'abbreviazione nello spazio a una dimensione Jurassic segreto potrebbe essere semplicemente simile un divorasse posizionato in modo inadeguato.</span><span class="sxs-lookup"><span data-stu-id="5e366-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![Ciò non è una schermata effettiva, ma un'illustrazione di come il segreto underworld da 101 nozioni di base di MR appare in HoloLens.](images/origamiholecomposited-640px.png)

<span data-ttu-id="5e366-128">Ciò non è una schermata effettiva, ma un'illustrazione di come il segreto underworld dal [MR nozioni di base 101](holograms-101.md) Cerca su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5e366-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="5e366-129">L'enclosure nero non viene visualizzata, ma è possibile visualizzare il contenuto di un foro virtuale.</span><span class="sxs-lookup"><span data-stu-id="5e366-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="5e366-130">(Quando la ricerca tramite un dispositivo reale, la parte intera sembrerebbe scompaiono ancora più perché gli occhi lo stato attivo a una distanza ulteriore come se non è ancora presente.)</span><span class="sxs-lookup"><span data-stu-id="5e366-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="5e366-131">Blocco a livello mondiale holographic contenuto</span><span class="sxs-lookup"><span data-stu-id="5e366-131">World-locking holographic content</span></span>

<span data-ttu-id="5e366-132">In Unity, è facile come aggiungere un componente WorldAnchor causando holographic contenuto rimanga bloccato world:</span><span class="sxs-lookup"><span data-stu-id="5e366-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="5e366-133">Il componente WorldAnchor costante regolerà la posizione e la rotazione del relativo GameObject (e pertanto altri in tale oggetto nella gerarchia di elementi) per mantenerla stabile rispetto agli oggetti fisici vicini.</span><span class="sxs-lookup"><span data-stu-id="5e366-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="5e366-134">Durante la creazione del contenuto, è possibile crearlo in modo che il pivot radice dell'oggetto viene centrato in questo spazio virtuale vuoto.</span><span class="sxs-lookup"><span data-stu-id="5e366-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="5e366-135">(Se pivot dell'oggetto si trova approfondita in muro, saranno molto più evidenti relativo piccoli aggiustamenti posizione e la rotazione e foro potrebbe non avere un aspetto molto stabile.)</span><span class="sxs-lookup"><span data-stu-id="5e366-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="5e366-136">Tutti gli elementi tranne il foro virtuale occluding</span><span class="sxs-lookup"><span data-stu-id="5e366-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="5e366-137">Esistono diversi modi per bloccare selettivamente la visualizzazione a ciò che è nascosto nell'affisse.</span><span class="sxs-lookup"><span data-stu-id="5e366-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="5e366-138">La più semplice consente di sfruttare il fatto che HoloLens Usa una visualizzazione di addizione, il che significa che gli oggetti neri completamente invisibile.</span><span class="sxs-lookup"><span data-stu-id="5e366-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="5e366-139">È possibile farlo in Unity non esegue qualsiasi shader speciali o materiale consigli, è sufficiente creare un materiale nero e assegnarla a un oggetto che le finestre nel contenuto.</span><span class="sxs-lookup"><span data-stu-id="5e366-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="5e366-140">Se si ritiene che questo di modellazione 3D, è sufficiente usare un numero limitato di oggetti Quad predefiniti e sovrapporle leggermente.</span><span class="sxs-lookup"><span data-stu-id="5e366-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="5e366-141">Esistono una serie di svantaggi di questo approccio, ma è il modo più rapido per ottenere qualcosa di utilizzo e ottenere una bassa fedeltà e prova del lavoro concetto è molto utile, anche se si sospetta che è possibile eseguire il refactoring in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="5e366-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="5e366-142">Uno degli svantaggi principali l'approccio "black box" precedente è che non fotografare bene.</span><span class="sxs-lookup"><span data-stu-id="5e366-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="5e366-143">Mentre l'effetto potrebbe essere perfetto tramite la visualizzazione di HoloLens, qualsiasi schermate che scelto verranno visualizzato un oggetto grande nero invece di ciò che rimanga della parete o floor.</span><span class="sxs-lookup"><span data-stu-id="5e366-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="5e366-144">Il motivo è che la fisica vntana composito hardware e le schermate e realtà in modo diverso.</span><span class="sxs-lookup"><span data-stu-id="5e366-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="5e366-145">Verrà ora deviazione per un istante nel alcuni calcoli matematici fittizio...</span><span class="sxs-lookup"><span data-stu-id="5e366-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="5e366-146">*Avviso fittizio matematico. Questi numeri e le formule sono lo scopo di illustrare un punto, non deve essere di qualsiasi tipo di metrica accurata.*</span><span class="sxs-lookup"><span data-stu-id="5e366-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="5e366-147">Ciò che viene visualizzato tramite HoloLens:</span><span class="sxs-lookup"><span data-stu-id="5e366-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="5e366-148">Quanto visualizzato nelle schermate e video:</span><span class="sxs-lookup"><span data-stu-id="5e366-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="5e366-149">IN INGLESE: Ciò che viene visualizzato tramite HoloLens è una semplice combinazione di più scura realtà (ad esempio tramite occhiali da sole) e tutti i valori vntana vuole visualizzare l'app.</span><span class="sxs-lookup"><span data-stu-id="5e366-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="5e366-150">Tuttavia, quando si acquisisce uno screenshot, l'immagine della fotocamera viene sfumato con vntana dell'app in base al valore di trasparenza per pixel.</span><span class="sxs-lookup"><span data-stu-id="5e366-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="5e366-151">Un modo per risolvere questo problema consiste nel modificare il materiale "black box" per solo scrivere nel buffer di profondità e ordinare con l'altro materiale opaco.</span><span class="sxs-lookup"><span data-stu-id="5e366-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="5e366-152">Per un esempio di ciò, consultare il [WindowOcclusion.shader file nei MixedRealityToolkit su GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span><span class="sxs-lookup"><span data-stu-id="5e366-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="5e366-153">Le righe pertinenti vengono copiate qui:</span><span class="sxs-lookup"><span data-stu-id="5e366-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="5e366-154">(Si noti "Offset 50, 100" riga è per risolvere problemi non correlati, in modo che probabilmente avrebbe senso di tralasciare che.)</span><span class="sxs-lookup"><span data-stu-id="5e366-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="5e366-155">Implementazione di un oggetto material occlusione invisibile simili consentirà all'app Disegna una casella che risulta corretta nella visualizzazione e nelle schermate di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5e366-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="5e366-156">Per i punti in bonus, è possibile provare a migliorare le prestazioni di tale casella ulteriormente effettuando operazioni clever per disegnare anche un minor numero di pixel invisibile, ma che effettivamente può assumere le erbacce e in genere non è richiesto.</span><span class="sxs-lookup"><span data-stu-id="5e366-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![Ecco il segreto underworld da 101 nozioni di base di MR Unity lo disegna, fatta eccezione per le parti della finestra di occluding esterne.](images/underworld-occluded-640px.png)

<span data-ttu-id="5e366-159">Di seguito è riportato il segreto underworld dal [MR nozioni di base 101](holograms-101.md) come Unity lo disegna, fatta eccezione per le parti della finestra di occluding esterne.</span><span class="sxs-lookup"><span data-stu-id="5e366-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="5e366-160">Si noti che il pivot per il underworld al centro della finestra, che consente di mantenere l'area libera più stabile possibile relativo del piano effettivo.</span><span class="sxs-lookup"><span data-stu-id="5e366-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="5e366-161">Eseguire tale operazione manualmente</span><span class="sxs-lookup"><span data-stu-id="5e366-161">Do it yourself</span></span>

<span data-ttu-id="5e366-162">Dispone un HoloLens e si desidera provare l'effetto personali?</span><span class="sxs-lookup"><span data-stu-id="5e366-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="5e366-163">La cosa più semplice è (Nessuna esigenza) consiste nell'installare l'app Visualizzatore 3D gratuita e quindi caricare il [scaricare il file the.fbx ho fornito su GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) per visualizzare un modello di Teapot fiore stanza.</span><span class="sxs-lookup"><span data-stu-id="5e366-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="5e366-164">Caricarlo in HoloLens ed è possibile visualizzare l'illusione al lavoro.</span><span class="sxs-lookup"><span data-stu-id="5e366-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="5e366-165">Quando si è davanti il modello, è possibile vedere solo negli hole di piccole dimensioni, ovvero tutto il resto è invisibile.</span><span class="sxs-lookup"><span data-stu-id="5e366-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="5e366-166">Esaminare il modello da qualsiasi altro lato e scomparire completamente.</span><span class="sxs-lookup"><span data-stu-id="5e366-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="5e366-167">Usare il movimento, rotazione e scalabilità controlli del Visualizzatore 3D per posizionare il foro virtuale in qualsiasi area verticale che è possibile pensare a generare alcune idee!</span><span class="sxs-lookup"><span data-stu-id="5e366-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![Visualizzazione di questo modello nell'editor di Unity mostrerà una scatola nera grande tutto il flowerpot.](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="5e366-170">Visualizzazione di questo modello nell'editor di Unity mostrerà una scatola nera grande tutto il flowerpot.</span><span class="sxs-lookup"><span data-stu-id="5e366-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="5e366-171">Su HoloLens, la finestra scomparirà, modo un effetto di finestra magic.</span><span class="sxs-lookup"><span data-stu-id="5e366-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="5e366-172">Se si desidera compilare un'app che usa questa tecnica, consultare il [esercitazione MR nozioni di base 101](holograms-101.md) nel [esercitazioni di realtà mista](tutorials.md).</span><span class="sxs-lookup"><span data-stu-id="5e366-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="5e366-173">Capitolo 7 termina con un'esplosione del piano che rivela un underworld nascosti (come illustrato nella figura sopra).</span><span class="sxs-lookup"><span data-stu-id="5e366-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="5e366-174">Chi ha detto esercitazioni dovevano essere noioso?</span><span class="sxs-lookup"><span data-stu-id="5e366-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="5e366-175">Di seguito sono riportate alcune idee di in cui è possibile eseguire questa idea Avanti:</span><span class="sxs-lookup"><span data-stu-id="5e366-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="5e366-176">Pensare al modo per rendere il contenuto all'interno del foro virtuale interattive.</span><span class="sxs-lookup"><span data-stu-id="5e366-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="5e366-177">Consentire agli utenti di influire oltre le pareti può migliorare effettivamente le assimilata sorprende che può fornire il trucco.</span><span class="sxs-lookup"><span data-stu-id="5e366-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="5e366-178">Pensare al modo attraverso gli oggetti ai aree note.</span><span class="sxs-lookup"><span data-stu-id="5e366-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="5e366-179">Ad esempio, come può inserire un foro holographic nella tabella di caffè e vedere la parte intera sotto tale?</span><span class="sxs-lookup"><span data-stu-id="5e366-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="5e366-180">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="5e366-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="5e366-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="5e366-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="5e366-182">Senior Software Engineer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="5e366-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="5e366-183">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5e366-183">See also</span></span>
* [<span data-ttu-id="5e366-184">Nozioni di base MR 101: Progetto completo con dispositivo</span><span class="sxs-lookup"><span data-stu-id="5e366-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="5e366-185">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="5e366-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="5e366-186">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="5e366-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="5e366-187">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="5e366-187">Spatial mapping</span></span>](spatial-mapping.md)