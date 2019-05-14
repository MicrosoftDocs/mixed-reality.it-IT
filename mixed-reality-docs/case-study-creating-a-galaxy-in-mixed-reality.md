---
title: 'Case study: creazione di un galaxy in realtà mista'
description: Prima di spedizione Microsoft HoloLens, abbiamo chiesto la nostra community di sviluppatori il tipo di app vorrebbero vedere un team interno di esperti di compilazione per il nuovo dispositivo. Sono stati condivisi più di 5000 idee e dopo un poll di Twitter di 24 ore, il vincitore è stata un'idea denominata "Galaxy Explorer".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Esplora Galaxy, HoloLens, realtà mista di Windows, Condividi la tua idea, case study
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604830"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="25c57-105">Case study: creazione di un galaxy in realtà mista</span><span class="sxs-lookup"><span data-stu-id="25c57-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="25c57-106">Prima di spedizione Microsoft HoloLens, abbiamo chiesto la nostra community di sviluppatori il tipo di app vorrebbero vedere un team interno di esperti di compilazione per il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="25c57-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="25c57-107">Sono stati condivisi più di 5000 idee e dopo un poll di Twitter di 24 ore, il vincitore è stata un'idea chiamata [Galaxy Esplora](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="25c57-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="25c57-108">Andy Zibits, il lead art sul progetto e Karim Luccin, tecnico del grafico del team, parlano la collaborazione tra l'arte e sviluppo che ha portato alla creazione di una rappresentazione accurata e interattiva di galaxy le missioni nello Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="25c57-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="25c57-109">Le tecnologie innovative</span><span class="sxs-lookup"><span data-stu-id="25c57-109">The Tech</span></span>

<span data-ttu-id="25c57-110">[Il nostro team](galaxy-explorer.md#meet-the-team) - effettuata backup di due finestre di progettazione, tre sviluppatori, quattro alle creazioni degli artisti, un producer e un tester, aveva sei settimane per creare un'app completamente funzionale che consente agli utenti di apprendere ed esplorare il vastness e bellezza del nostro Galaxy missioni nello spazio.</span><span class="sxs-lookup"><span data-stu-id="25c57-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="25c57-111">Volevamo sfruttare appieno la capacità di eseguire il rendering di oggetti 3D direttamente nello spazio di vita, in modo che abbiamo deciso di che voler creare un realistico galaxy dall'aspetto professionale in cui le persone sarebbe in grado di eseguire lo zoom avanti nella chiusura e vedere i singoli stelle, ognuno nella propria traiettorie HoloLens .</span><span class="sxs-lookup"><span data-stu-id="25c57-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="25c57-112">La prima settimana di sviluppo, ci siamo inventati alcuni obiettivi per la rappresentazione di Galaxy le missioni nello spazio: È necessario avere profondità, lo spostamento e l'aspetto volumetrico, completa di stelle che risulterebbe d'aiuto creano la forma del galaxy.</span><span class="sxs-lookup"><span data-stu-id="25c57-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="25c57-113">Il problema con la creazione di un'animazione galaxy con miliardi di stelle era che il numero di elementi singoli che necessitano di aggiornamento potrebbe risultare troppo grande per ogni fotogramma per HoloLens animare l'utilizzo della CPU.</span><span class="sxs-lookup"><span data-stu-id="25c57-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="25c57-114">La nostra soluzione coinvolta una combinazione complessa di arte e scienza.</span><span class="sxs-lookup"><span data-stu-id="25c57-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="25c57-115">Dietro le quinte</span><span class="sxs-lookup"><span data-stu-id="25c57-115">Behind the scenes</span></span>

<span data-ttu-id="25c57-116">Per consentire agli utenti di esplorare i singoli stelle, è stato il primo passaggio per scoprire quanti particelle è stato possibile eseguire il rendering in una sola volta.</span><span class="sxs-lookup"><span data-stu-id="25c57-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="25c57-117">Il rendering di particelle</span><span class="sxs-lookup"><span data-stu-id="25c57-117">Rendering particles</span></span>

<span data-ttu-id="25c57-118">CPU corrente sono ideali per l'elaborazione di attività seriali e fino a qualche attività in parallelo in una sola volta (a seconda del numero di core hanno), ma le GPU sono molto più efficaci per l'elaborazione di migliaia di operazioni in parallelo.</span><span class="sxs-lookup"><span data-stu-id="25c57-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="25c57-119">Tuttavia, perché in genere non condividono la stessa memoria CPU, lo scambio di dati tra CPU <> GPU può diventare rapidamente un collo di bottiglia.</span><span class="sxs-lookup"><span data-stu-id="25c57-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="25c57-120">La soluzione consisteva nel rendere un galaxy sulla GPU e avesse durata (TTL) completamente nella GPU.</span><span class="sxs-lookup"><span data-stu-id="25c57-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="25c57-121">Test di stress abbiamo iniziato con migliaia di particelle punto in vari modelli.</span><span class="sxs-lookup"><span data-stu-id="25c57-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="25c57-122">Ciò ha permesso di ottenere il galaxy su HoloLens per vedere cosa ha funzionato e cosa non è stato.</span><span class="sxs-lookup"><span data-stu-id="25c57-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="25c57-123">Creazione di posizione delle stelle</span><span class="sxs-lookup"><span data-stu-id="25c57-123">Creating the position of the stars</span></span>

<span data-ttu-id="25c57-124">Uno dei membri del nostro team aveva già scritto la C# codice generato da stelle la loro posizione iniziale.</span><span class="sxs-lookup"><span data-stu-id="25c57-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="25c57-125">Le stelle si trovano in un'ellisse e la loro posizione può essere descritto da (**curveOffset**, **ellipseSize**, **elevazione**) in cui **curveOffset**è l'angolo della stella lungo l'ellisse **ellipseSize** è la dimensione dell'ellisse lungo X e Z e l'elevazione appropriata della stella all'interno di galaxy l'elevazione dei privilegi.</span><span class="sxs-lookup"><span data-stu-id="25c57-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="25c57-126">Di conseguenza, possiamo creare un buffer ([ComputeBuffer di Unity](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) che verrebbe inizializzata con ogni attributo star e inviarlo nella GPU in cui attivarlo per il resto dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="25c57-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="25c57-127">Per disegnare il buffer, usiamo [DrawProcedural di Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) che consente di eseguire uno shader (codice di una GPU) in un set arbitrario di punti senza la necessità di una mesh effettiva che rappresenta il galaxy:</span><span class="sxs-lookup"><span data-stu-id="25c57-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="25c57-128">**CPU:**</span><span class="sxs-lookup"><span data-stu-id="25c57-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="25c57-129">**GPU:**</span><span class="sxs-lookup"><span data-stu-id="25c57-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="25c57-130">Abbiamo iniziato con modelli circolari non elaborati con migliaia di particelle.</span><span class="sxs-lookup"><span data-stu-id="25c57-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="25c57-131">Questo ci ha offerto l'avevamo bisogno che è stato possibile gestire molti particelle ed eseguirlo alle velocità del ad alte prestazioni, ma non è stato soddisfatti con la forma complessiva di galaxy della prova.</span><span class="sxs-lookup"><span data-stu-id="25c57-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="25c57-132">Per migliorare la forma, abbiamo provato diversi modelli e i sistemi particellari con rotazione.</span><span class="sxs-lookup"><span data-stu-id="25c57-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="25c57-133">Questi sono stati inizialmente promettenti perché il numero di particelle e delle prestazioni è rimasto coerenza, ma la forma ha funzionato in prossimità del centro e le stelle emettesse una verso l'esterno che non era realistico.</span><span class="sxs-lookup"><span data-stu-id="25c57-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="25c57-134">Ci serviva un'emissione che consente di modificare l'ora e hanno le particelle spostare realisticamente, ciclo mai più da vicino al centro della finestra di galaxy.</span><span class="sxs-lookup"><span data-stu-id="25c57-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Abbiamo provato diversi modelli e i sistemi particellari ruotato, simili ai seguenti.](images/galaxy-patterns-500px.png)

<span data-ttu-id="25c57-136">Abbiamo provato diversi modelli e i sistemi particellari ruotato, simili ai seguenti.</span><span class="sxs-lookup"><span data-stu-id="25c57-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="25c57-137">Il nostro team ha qualche ricerca sulla funzione galassie modo e abbiamo effettuato un sistema particellare personalizzato in modo specifico per il galaxy in modo che è stato possibile spostare le particelle sui puntini di sospensione in base "[teoria wave densità](https://en.wikipedia.org/wiki/Density_wave_theory)," quale theorizes che i rami di un Galaxy sono aree di un aumento della densità ma in continuo mutamento, costante, ad esempio un blocco del traffico.</span><span class="sxs-lookup"><span data-stu-id="25c57-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="25c57-138">Risulta stabile e affidabile, ma gli asterischi vengono effettivamente spostati da e verso i rami durante lo spostamento lungo i rispettivi puntini di sospensione.</span><span class="sxs-lookup"><span data-stu-id="25c57-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="25c57-139">Nel nostro sistema, le particelle mai presenti sulla CPU, ovvero si generano le schede e orientare tutto su GPU, in modo che l'intero sistema è stato semplicemente iniziale + tempo.</span><span class="sxs-lookup"><span data-stu-id="25c57-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="25c57-140">Avanzata simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="25c57-140">It progressed like this:</span></span>

![Progressione di sistema di particelle con rendering GPU](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="25c57-142">Progressione di sistema di particelle con rendering GPU</span><span class="sxs-lookup"><span data-stu-id="25c57-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="25c57-143">Una volta sufficiente puntini di sospensione vengono aggiunti e configurati per ruotare, i galassie ha iniziato a form "tratti" in cui eseguire la convergenza lo spostamento di stelle.</span><span class="sxs-lookup"><span data-stu-id="25c57-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="25c57-144">La spaziatura delle stelle lungo ogni percorso ellittico sono stata assegnata casualità e ogni stella ha ottenuto un po' di casualità posizionali aggiunto.</span><span class="sxs-lookup"><span data-stu-id="25c57-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="25c57-145">Ciò creato una distribuzione professionale molto più naturale della forma a stella di spostamento e la gestione risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="25c57-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="25c57-146">Infine, è stata aggiunta la possibilità colore unità in base alla distanza dal centro.</span><span class="sxs-lookup"><span data-stu-id="25c57-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="25c57-147">Creare il movimento delle stelle</span><span class="sxs-lookup"><span data-stu-id="25c57-147">Creating the motion of the stars</span></span>

<span data-ttu-id="25c57-148">Per animare il movimento a stella generale, è necessario per aggiungere un angolo di costante per ogni fotogramma e ottenere lo spostamento lungo i puntini di sospensione in modo costante radiale stelle.</span><span class="sxs-lookup"><span data-stu-id="25c57-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="25c57-149">Questo è il motivo principale per l'utilizzo **curveOffset**.</span><span class="sxs-lookup"><span data-stu-id="25c57-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="25c57-150">Non è tecnicamente corretto come stelle verranno migrate più rapidamente ai lati lungo dei puntini di sospensione, ma il movimento generale ritenuto valido.</span><span class="sxs-lookup"><span data-stu-id="25c57-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Stelle passare più rapidamente l'arco di tempo, più lento sui bordi.](images/ellipse-movement.jpg)

<span data-ttu-id="25c57-152">Stelle passare più rapidamente l'arco di tempo, più lento sui bordi.</span><span class="sxs-lookup"><span data-stu-id="25c57-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="25c57-153">Con questo, ogni star è completamente descritto da (**curveOffset**, **ellipseSize**, **l'elevazione dei privilegi**, **Age**) in cui **Age** è un accumulo del tempo totale trascorso dal momento che è stata caricata la scena.</span><span class="sxs-lookup"><span data-stu-id="25c57-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="25c57-154">Ciò ha permesso di generare decine di migliaia di stelle una sola volta all'inizio dell'applicazione, quindi viene aggiunta un'animazione di un set di stelle lungo le curve stabilite un.</span><span class="sxs-lookup"><span data-stu-id="25c57-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="25c57-155">Poiché tutti gli elementi nella GPU, il sistema è possibile aggiungere un'animazione di tutte le stelle in parallelo senza costi aggiuntivi per la CPU.</span><span class="sxs-lookup"><span data-stu-id="25c57-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Ecco l'aspetto quando disegnare quadrati vuoti.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="25c57-157">Ecco l'aspetto quando disegnare quadrati vuoti.</span><span class="sxs-lookup"><span data-stu-id="25c57-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="25c57-158">Per rendere ogni viso quad-la fotocamera, abbiamo utilizzato un geometry shader per trasformare ogni posizione a stella a un rettangolo sullo schermo che conterrà la stella trama 2D.</span><span class="sxs-lookup"><span data-stu-id="25c57-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![A forma di rombo anziché quadrati.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="25c57-160">A forma di rombo anziché quadrati.</span><span class="sxs-lookup"><span data-stu-id="25c57-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="25c57-161">Perché volevamo limitare il caricamento (numero di volte in cui verrà elaborato un pixel), per quanto possibile, viene ruotata i quadrati in modo che hanno meno si sovrappongono.</span><span class="sxs-lookup"><span data-stu-id="25c57-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="25c57-162">Aggiunta di cloud</span><span class="sxs-lookup"><span data-stu-id="25c57-162">Adding clouds</span></span>

<span data-ttu-id="25c57-163">Esistono diversi modi per ottenere una visione volumetrica con particelle, ovvero dal raggio marching all'interno di un volume al disegno di particelle tanti possibili per simulare un cloud.</span><span class="sxs-lookup"><span data-stu-id="25c57-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="25c57-164">Raggio in tempo reale marching stava per essere troppo costoso e complesso all'autore, quindi è un primo tentativo di creazione di un sistema di computer impostore usando un metodo per le foreste per il rendering nei giochi, con molte immagini 2D di alberi rivolta alla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="25c57-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="25c57-165">Quando si esegue questa operazione in un gioco, è possibile disporre le trame di alberi viene eseguito il rendering da una fotocamera che ruota intorno a salvare tutte le immagini e in fase di esecuzione per ogni scheda billboard, selezionare l'immagine che corrisponde alla direzione di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="25c57-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="25c57-166">Questo non funziona anche quando le immagini sono vntana.</span><span class="sxs-lookup"><span data-stu-id="25c57-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="25c57-167">La differenza tra l'occhio del lettore a sinistra e l'occhio del lettore a destra fare in modo che è necessario un risoluzione più alta, altrimenti solo sembra semplice, un alias, o ripetitivi.</span><span class="sxs-lookup"><span data-stu-id="25c57-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="25c57-168">Il secondo tentativo, abbiamo provato con particelle tanti possibili.</span><span class="sxs-lookup"><span data-stu-id="25c57-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="25c57-169">Gli oggetti visivi migliori sono stati raggiunti quando si modo additivo disegnata particelle e li sfocata prima di aggiungerli alla scena.</span><span class="sxs-lookup"><span data-stu-id="25c57-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="25c57-170">I tipici problemi con l'approccio erano correlati a quanti particelle è stato possibile disegnare in una sola volta e area si occupava mantenendo al tempo stesso 60fps quanto dello schermo.</span><span class="sxs-lookup"><span data-stu-id="25c57-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="25c57-171">L'immagine risultante per ottenere questo cloud sente sfocatura è in genere un'operazione molto costosa.</span><span class="sxs-lookup"><span data-stu-id="25c57-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Senza la trama, questo è ciò che si presenta come il cloud con opacità % 2.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="25c57-173">Senza la trama, questo è ciò che si presenta come il cloud con opacità % 2.</span><span class="sxs-lookup"><span data-stu-id="25c57-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="25c57-174">Additive in corso e una quantità elevata di essi significa che avremmo diversi quadrati uno sopra l'altro, ombreggiatura ripetutamente lo stesso pixel.</span><span class="sxs-lookup"><span data-stu-id="25c57-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="25c57-175">Al centro della finestra di galaxy, lo stesso pixel contiene centinaia di quadrati sopra l'altra e ciò ha un costo elevato quando viene eseguita a schermo intero.</span><span class="sxs-lookup"><span data-stu-id="25c57-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="25c57-176">In questo cloud schermo intero e il tentativo di sfocatura li sarebbe stata una cattiva idea, ma che si è deciso di lasciare l'hardware il lavoro per noi.</span><span class="sxs-lookup"><span data-stu-id="25c57-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="25c57-177">Prima di tutto un bit del contesto</span><span class="sxs-lookup"><span data-stu-id="25c57-177">A bit of context first</span></span>

<span data-ttu-id="25c57-178">Quando si usano le trame in un gioco per le dimensioni della trama corrisponderanno raramente l'area in cui si vuole usarlo in, ma è possibile usare un tipo diverso di filtro per ottenere la scheda grafica per interpolare il colore dai pixel della trama della trama ([filtraggio della trama<C3/>).](https://msdn.microsoft.com/library/dn642451.aspx)</span><span class="sxs-lookup"><span data-stu-id="25c57-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="25c57-179">Il filtro che ci interessa sia [bilineare](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) che calcola il valore di qualsiasi pixel usando il 4 vicini più prossimi.</span><span class="sxs-lookup"><span data-stu-id="25c57-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Originale prima dell'applicazione di filtri](images/texture-1.png)

![Risultato dopo il filtro](images/texture-2.png)

<span data-ttu-id="25c57-182">Utilizzo di questa proprietà, noteremo che ogni volta che si tenta di disegnare una trama in un'area raddoppiata big data, consente di sfocare il risultato.</span><span class="sxs-lookup"><span data-stu-id="25c57-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="25c57-183">Invece di rendering in modalità schermo intero e perdere tali millisecondi preziosi che è stato possibile impiegare una notevole per qualcos'altro, si esegue il rendering di una versione di piccole dimensioni dello schermo.</span><span class="sxs-lookup"><span data-stu-id="25c57-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="25c57-184">Quindi, copiare questa trama e estendendolo in base a un fattore pari a 2 diverse volte, otteniamo a schermo intero durante la sfocatura il contenuto del processo.</span><span class="sxs-lookup"><span data-stu-id="25c57-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 ingrandire indietro a risoluzione completa.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="25c57-186">x3 ingrandire indietro a risoluzione completa.</span><span class="sxs-lookup"><span data-stu-id="25c57-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="25c57-187">Ciò ha permesso di ottenere la parte cloud con solo una frazione del costo originale.</span><span class="sxs-lookup"><span data-stu-id="25c57-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="25c57-188">Anziché aggiungere cloud nella risoluzione massima, abbiamo solo paint 1/64th dei pixel e semplicemente allungare la trama al ad alta risoluzione.</span><span class="sxs-lookup"><span data-stu-id="25c57-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![A sinistra, con una fascia alta parlino da 1/l'8 a risoluzione completa. e a destra, con 3 aumentare con potenza di 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="25c57-190">A sinistra, con una fascia alta parlino da 1/l'8 a risoluzione completa. e a destra, con 3 aumentare con potenza di 2.</span><span class="sxs-lookup"><span data-stu-id="25c57-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="25c57-191">Si noti che il tentativo di passare dal 1/64th le dimensioni per la versione completa delle dimensioni in un'unica operazione risulterebbe completamente diverse, come la scheda grafica sarebbe comunque di usare 4 pixel nel nostro programma di installazione per evidenziare un'area più grande e avviare gli elementi da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="25c57-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="25c57-192">Quindi, se si aggiungono stelle risoluzione completa con schede più piccole, otteniamo il completo galaxy:</span><span class="sxs-lookup"><span data-stu-id="25c57-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Quasi il risultato finale del rendering galaxy utilizzando stelle ad alta risoluzione](images/full-galaxy-500px.png)

<span data-ttu-id="25c57-194">Dopo che è stato sulla strada giusta con la forma, è stato aggiunto un livello di cloud, eseguire lo swapping dei punti temporanei con quelli abbiamo disegnato Photoshop e aggiungere alcuni colori aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="25c57-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="25c57-195">Il risultato è un Galaxy missioni nell'arte ed entrambi i team di tecnici ritenevano bene e soddisfa gli obiettivi di profondità, volume e di movimento, tutto senza sovraccaricare la CPU.</span><span class="sxs-lookup"><span data-stu-id="25c57-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Il finale Galaxy missioni nello spazio 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="25c57-197">Il finale Galaxy missioni nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="25c57-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="25c57-198">Informazioni di esplorazione</span><span class="sxs-lookup"><span data-stu-id="25c57-198">More to explore</span></span>

<span data-ttu-id="25c57-199">Abbiamo reso open-source il codice per l'app Esplora Galaxy e averlo reso disponibile nel [GitHub](https://github.com/Microsoft/GalaxyExplorer) agli sviluppatori di compilare.</span><span class="sxs-lookup"><span data-stu-id="25c57-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="25c57-200">Vuoi ottenere informazioni più dettagliate del processo di sviluppo per Galaxy Explorer?</span><span class="sxs-lookup"><span data-stu-id="25c57-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="25c57-201">Estrae tutti gli aggiornamenti di progetto precedenti sul [canale YouTube di Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="25c57-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="25c57-202">Informazioni sugli autori</span><span class="sxs-lookup"><span data-stu-id="25c57-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="25c57-203"><b>Karim Luccin</b> è un Software Engineer e un appassionato di oggetti visivi fantasiosi.</span><span class="sxs-lookup"><span data-stu-id="25c57-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="25c57-204">È stato il tecnico della grafica per Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="25c57-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="25c57-205"><b>Andy Zibits</b> è un appassionato di Lead arte e lo spazio che ha gestito il team di modellazione 3D per Galaxy Explorer e ritenuta per particelle ancora più.</span><span class="sxs-lookup"><span data-stu-id="25c57-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="25c57-206">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25c57-206">See also</span></span>
* [<span data-ttu-id="25c57-207">Esplora Galaxy su GitHub</span><span class="sxs-lookup"><span data-stu-id="25c57-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="25c57-208">Aggiornamenti di progetto Galaxy Explorer su YouTube</span><span class="sxs-lookup"><span data-stu-id="25c57-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
