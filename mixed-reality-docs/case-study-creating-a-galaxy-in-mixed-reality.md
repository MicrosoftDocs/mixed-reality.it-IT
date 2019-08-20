---
title: Case Study-creazione di una galassia in realtà mista
description: Prima che Microsoft HoloLens spedito, abbiamo chiesto al nostro community di sviluppatori quale tipo di app vorrebbero vedere un'esperienza di Team Build interna per il nuovo dispositivo. Sono state condivise più di 5000 idee e dopo un sondaggio Twitter di 24 ore, il vincitore era un'idea denominata "Galaxy Explorer".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, realtà mista di Windows, Condividi la tua idea case study
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523845"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="48c5e-105">Case Study-creazione di una galassia in realtà mista</span><span class="sxs-lookup"><span data-stu-id="48c5e-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="48c5e-106">Prima che Microsoft HoloLens spedito, abbiamo chiesto al nostro community di sviluppatori quale tipo di app vorrebbero vedere un'esperienza di Team Build interna per il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="48c5e-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="48c5e-107">Sono state condivise più di 5000 idee e dopo un sondaggio Twitter di 24 ore, il vincitore era un'idea denominata [Galaxy Explorer](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="48c5e-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="48c5e-108">Andy Zibits, il responsabile dell'arte del progetto e Karim Luccin, il tecnico di grafica del team, illustrano il lavoro di collaborazione tra l'arte e la progettazione, che hanno portato alla creazione di una rappresentazione accurata e interattiva della galassia del modo lattiginoso in Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="48c5e-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="48c5e-109">Il Tech</span><span class="sxs-lookup"><span data-stu-id="48c5e-109">The Tech</span></span>

<span data-ttu-id="48c5e-110">Il [nostro team](galaxy-explorer.md#meet-the-team) , composto da due progettisti, tre sviluppatori, quattro artisti, un produttore e un tester, aveva sei settimane per creare un'app completamente funzionante che consentiva agli utenti di apprendere ed esplorare la vastità e la bellezza della nostra galassia lattiginosa.</span><span class="sxs-lookup"><span data-stu-id="48c5e-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="48c5e-111">Volevamo sfruttare appieno la capacità di HoloLens di eseguire il rendering degli oggetti 3D direttamente nello spazio di lavoro, quindi abbiamo deciso di voler creare una galassia realistica in cui le persone sarebbero in grado di eseguire lo zoom avanti e visualizzare le singole stelle, ognuna sulle proprie traiettorie .</span><span class="sxs-lookup"><span data-stu-id="48c5e-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="48c5e-112">Nella prima settimana dello sviluppo sono stati introdotti alcuni obiettivi per la rappresentazione della galassia Milky Way: Doveva avere un livello di profondità, spostamento e sensazione volumetrica, pieno di stelle che facilitavano la creazione della forma della galassia.</span><span class="sxs-lookup"><span data-stu-id="48c5e-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="48c5e-113">Il problema della creazione di una galassia animata con miliardi di stelle consisteva nel fatto che il numero di singoli elementi che necessitano di aggiornamento sarebbe troppo grande per ogni fotogramma per HoloLens per l'animazione con la CPU.</span><span class="sxs-lookup"><span data-stu-id="48c5e-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="48c5e-114">La nostra soluzione comprendeva una complessa combinazione di arte e scienza.</span><span class="sxs-lookup"><span data-stu-id="48c5e-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="48c5e-115">Dietro le quinte</span><span class="sxs-lookup"><span data-stu-id="48c5e-115">Behind the scenes</span></span>

<span data-ttu-id="48c5e-116">Per consentire agli utenti di esplorare le singole stelle, il primo passaggio consiste nel determinare il numero di particelle di cui è possibile eseguire il rendering in una sola volta.</span><span class="sxs-lookup"><span data-stu-id="48c5e-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="48c5e-117">Rendering di particelle</span><span class="sxs-lookup"><span data-stu-id="48c5e-117">Rendering particles</span></span>

<span data-ttu-id="48c5e-118">Le CPU correnti sono molto utili per l'elaborazione di attività seriali e fino ad alcune attività parallele contemporaneamente (a seconda del numero di core presenti), ma le GPU sono molto più efficienti nell'elaborazione di migliaia di operazioni in parallelo.</span><span class="sxs-lookup"><span data-stu-id="48c5e-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="48c5e-119">Tuttavia, poiché in genere non condividono la stessa memoria della CPU, lo scambio di dati tra CPU < > GPU può diventare rapidamente un collo di bottiglia.</span><span class="sxs-lookup"><span data-stu-id="48c5e-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="48c5e-120">La soluzione è stata quella di creare una galassia sulla GPU, che doveva vivere completamente sulla GPU.</span><span class="sxs-lookup"><span data-stu-id="48c5e-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="48c5e-121">Sono stati avviati test di stress con migliaia di particelle puntiformi in vari modelli.</span><span class="sxs-lookup"><span data-stu-id="48c5e-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="48c5e-122">Questo ci ha consentito di ottenere la galassia in HoloLens per vedere cosa ha funzionato e cosa non è stato fatto.</span><span class="sxs-lookup"><span data-stu-id="48c5e-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="48c5e-123">Creazione della posizione delle stelle</span><span class="sxs-lookup"><span data-stu-id="48c5e-123">Creating the position of the stars</span></span>

<span data-ttu-id="48c5e-124">Uno dei membri del team ha già scritto il C# codice che genera stelle nella posizione iniziale.</span><span class="sxs-lookup"><span data-stu-id="48c5e-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="48c5e-125">Le stelle si trovano su un'ellisse e la loro posizione può essere descritta da (**curveOffset**, **ellipseSize**, **elevazione**) dove **curveOffset** è l'angolo della stella lungo l'ellisse, **ellipseSize** è la dimensione dell'ellisse. lungo X e Z e elevazione dell'elevazione corretta della stella all'interno della galassia.</span><span class="sxs-lookup"><span data-stu-id="48c5e-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="48c5e-126">In questo modo, è possibile creare un buffer ([ComputeBuffer di Unity](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) che verrebbe inizializzato con ogni attributo Star e lo invierà alla GPU in cui risiederà per il resto dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="48c5e-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="48c5e-127">Per creare questo buffer, viene usato [DrawProcedural di Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) che consente l'esecuzione di uno shader (codice su una GPU) in un set arbitrario di punti senza avere una mesh effettiva che rappresenti la galassia:</span><span class="sxs-lookup"><span data-stu-id="48c5e-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="48c5e-128">**CPU**</span><span class="sxs-lookup"><span data-stu-id="48c5e-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="48c5e-129">**GPU**</span><span class="sxs-lookup"><span data-stu-id="48c5e-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="48c5e-130">Abbiamo iniziato con modelli circolari non elaborati con migliaia di particelle.</span><span class="sxs-lookup"><span data-stu-id="48c5e-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="48c5e-131">Questo ci ha permesso di provare a gestire molte particelle ed eseguirle a velocità elevate, ma non è stata soddisfatta la forma complessiva della galassia.</span><span class="sxs-lookup"><span data-stu-id="48c5e-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="48c5e-132">Per migliorare la forma, abbiamo provato a usare diversi modelli e sistemi particellari con rotazione.</span><span class="sxs-lookup"><span data-stu-id="48c5e-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="48c5e-133">Inizialmente provenivano promesse, perché il numero di particelle e le prestazioni rimanevano coerenti, ma la forma si è interrotta in prossimità del centro e le stelle venivano emesse in modo esterno e non realistico.</span><span class="sxs-lookup"><span data-stu-id="48c5e-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="48c5e-134">Avevamo bisogno di una trasmissione che ci consentisse di manipolare il tempo e far muovere le particelle in modo realistico, scorrendo sempre più vicino al centro della galassia.</span><span class="sxs-lookup"><span data-stu-id="48c5e-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Sono stati tentati diversi modelli e sistemi particellari ruotati, come questi.](images/galaxy-patterns-500px.png)

<span data-ttu-id="48c5e-136">Sono stati tentati diversi modelli e sistemi particellari ruotati, come questi.</span><span class="sxs-lookup"><span data-stu-id="48c5e-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="48c5e-137">Il nostro team ha eseguito alcune ricerche sul funzionamento delle galassie ed è stato creato un sistema particellare personalizzato appositamente per la galassia, in modo da poter spostare le particelle sui puntini di sospensione in base alla "[teoria delle onde di densità](https://en.wikipedia.org/wiki/Density_wave_theory)", che ipotizza che le braccia di una galassia siano aree di densità più elevata ma in flusso costante, ad esempio un ingorgo del traffico.</span><span class="sxs-lookup"><span data-stu-id="48c5e-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="48c5e-138">Sembra stabile e uniforme, ma le stelle sono in realtà spostate in e fuori dalle braccia mentre si spostano lungo i rispettivi ellissi.</span><span class="sxs-lookup"><span data-stu-id="48c5e-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="48c5e-139">Nel nostro sistema, le particelle non sono mai presenti sulla CPU: le schede vengono generate e ne vengono orientate tutte sulla GPU, quindi l'intero sistema è semplicemente stato iniziale + tempo.</span><span class="sxs-lookup"><span data-stu-id="48c5e-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="48c5e-140">Questa operazione è stata avanzata in questo modo:</span><span class="sxs-lookup"><span data-stu-id="48c5e-140">It progressed like this:</span></span>

![Progressione del sistema particellare con rendering GPU](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="48c5e-142">Progressione del sistema particellare con rendering GPU</span><span class="sxs-lookup"><span data-stu-id="48c5e-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="48c5e-143">Una volta aggiunti i puntini di sospensione sufficienti e impostati per la rotazione, le galassie iniziano a formare "braccia" dove lo spostamento delle stelle converge.</span><span class="sxs-lookup"><span data-stu-id="48c5e-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="48c5e-144">Alla spaziatura delle stelle lungo ogni percorso ellittico è stato assegnato un certo grado di casualità e ogni stella ha aggiunto un bit di casualità posizionale.</span><span class="sxs-lookup"><span data-stu-id="48c5e-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="48c5e-145">Questo ha creato una distribuzione di aspetto molto più naturale del movimento a stella e della forma ARM.</span><span class="sxs-lookup"><span data-stu-id="48c5e-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="48c5e-146">Infine, è stata aggiunta la possibilità di guidare il colore in base alla distanza dal centro.</span><span class="sxs-lookup"><span data-stu-id="48c5e-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="48c5e-147">Creazione del movimento delle stelle</span><span class="sxs-lookup"><span data-stu-id="48c5e-147">Creating the motion of the stars</span></span>

<span data-ttu-id="48c5e-148">Per animare il movimento a stella generale, è necessario aggiungere un angolo costante per ogni fotogramma e ottenere le stelle che si spostano lungo i puntini di sospensione a una velocità radiale costante.</span><span class="sxs-lookup"><span data-stu-id="48c5e-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="48c5e-149">Questo è il motivo principale per l'uso di **curveOffset**.</span><span class="sxs-lookup"><span data-stu-id="48c5e-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="48c5e-150">Questa operazione non è tecnicamente corretta perché le stelle si muovono più velocemente lungo i lati lunghi dei puntini di sospensione, ma il movimento generale si è ritenuto positivo.</span><span class="sxs-lookup"><span data-stu-id="48c5e-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Le stelle si muovono più velocemente nell'arco lungo, più lentamente sui bordi.](images/ellipse-movement.jpg)

<span data-ttu-id="48c5e-152">Le stelle si muovono più velocemente nell'arco lungo, più lentamente sui bordi.</span><span class="sxs-lookup"><span data-stu-id="48c5e-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="48c5e-153">A tale scopo, ogni stella viene descritta in modo completo da (**curveOffset**, **ellipseSize**, **Elevation**, **Age**) in cui **Age** è un accumulo del tempo totale trascorso dal momento in cui la scena è stata caricata.</span><span class="sxs-lookup"><span data-stu-id="48c5e-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="48c5e-154">Questo ci ha permesso di generare decine di migliaia di stelle una volta all'inizio dell'applicazione, quindi abbiamo animato un set di stelle a un unico lungo le curve stabilite.</span><span class="sxs-lookup"><span data-stu-id="48c5e-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="48c5e-155">Poiché tutti gli elementi sono sulla GPU, il sistema può animare tutte le stelle in parallelo senza costi aggiuntivi per la CPU.</span><span class="sxs-lookup"><span data-stu-id="48c5e-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Ecco come appare quando si disegnano i quad bianchi.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="48c5e-157">Ecco come appare quando si disegnano i quad bianchi.</span><span class="sxs-lookup"><span data-stu-id="48c5e-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="48c5e-158">Per fare in modo che ogni Quad faccia la fotocamera, abbiamo usato un geometry shader per trasformare ogni posizione a stella in un rettangolo 2D sullo schermo che conterrà la trama a stella.</span><span class="sxs-lookup"><span data-stu-id="48c5e-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Diamanti anziché quad.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="48c5e-160">Diamanti anziché quad.</span><span class="sxs-lookup"><span data-stu-id="48c5e-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="48c5e-161">Poiché si desiderava limitare il numero di volte in cui un pixel verrà elaborato, il più possibile è stato ruotato in modo da ottenere una minore sovrapposizione.</span><span class="sxs-lookup"><span data-stu-id="48c5e-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="48c5e-162">Aggiunta di cloud</span><span class="sxs-lookup"><span data-stu-id="48c5e-162">Adding clouds</span></span>

<span data-ttu-id="48c5e-163">Esistono diversi modi per ottenere un senso volumetrico con le particelle, da Ray che si trova all'interno di un volume per disegnare il maggior numero possibile di particelle per simulare un cloud.</span><span class="sxs-lookup"><span data-stu-id="48c5e-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="48c5e-164">La marcia in tempo reale di un raggio era troppo costosa e difficile da creare, quindi abbiamo prima provato a creare un sistema impostore usando un metodo per il rendering delle foreste nei giochi, con numerose immagini 2D di alberi rivolte alla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="48c5e-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="48c5e-165">Quando si esegue questa operazione in un gioco, è possibile eseguire il rendering di trame di alberi da una fotocamera che ruota, salvare tutte le immagini e in fase di esecuzione per ogni scheda del tabellone, selezionare l'immagine che corrisponde alla direzione di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="48c5e-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="48c5e-166">Questa operazione non funziona anche quando le immagini sono ologrammi.</span><span class="sxs-lookup"><span data-stu-id="48c5e-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="48c5e-167">La differenza tra l'occhio sinistro e l'occhio destro lo rende, in modo che sia necessaria una risoluzione molto più elevata, in caso contrario si tratta semplicemente di un aspetto Flat, con alias o ripetitivo.</span><span class="sxs-lookup"><span data-stu-id="48c5e-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="48c5e-168">Al secondo tentativo, abbiamo provato a ottenere il maggior numero possibile di particelle.</span><span class="sxs-lookup"><span data-stu-id="48c5e-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="48c5e-169">Gli oggetti visivi migliori sono stati realizzati quando sono state apportate in modo additivo le particelle e sono state sfocate prima di aggiungerle alla scena.</span><span class="sxs-lookup"><span data-stu-id="48c5e-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="48c5e-170">I problemi tipici di questo approccio sono correlati al numero di particelle che è possibile creare in una sola volta e alla quantità di spazio dello schermo analizzate mantenendo comunque 60fps.</span><span class="sxs-lookup"><span data-stu-id="48c5e-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="48c5e-171">La sfocatura dell'immagine risultante per ottenere questa sensazione di cloud era in genere un'operazione molto costosa.</span><span class="sxs-lookup"><span data-stu-id="48c5e-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Senza texture, questo è l'aspetto dei cloud con opacità del 2%.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="48c5e-173">Senza texture, questo è l'aspetto dei cloud con opacità del 2%.</span><span class="sxs-lookup"><span data-stu-id="48c5e-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="48c5e-174">Il fatto di essere additivi e avere molti di essi significa che ci saranno più quadre tra loro, ombreggiando ripetutamente lo stesso pixel.</span><span class="sxs-lookup"><span data-stu-id="48c5e-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="48c5e-175">Al centro della galassia, lo stesso pixel presenta centinaia di quadre tra loro e questo ha comportato un costo enorme quando viene eseguito a schermo intero.</span><span class="sxs-lookup"><span data-stu-id="48c5e-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="48c5e-176">L'esecuzione di cloud a schermo intero e il tentativo di sfocarli sarebbe stata una pessima idea, quindi abbiamo deciso di lasciare che l'hardware eseguisse il lavoro per noi.</span><span class="sxs-lookup"><span data-stu-id="48c5e-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="48c5e-177">Prima un po' di contesto</span><span class="sxs-lookup"><span data-stu-id="48c5e-177">A bit of context first</span></span>

<span data-ttu-id="48c5e-178">Quando si usano le trame in un gioco per le dimensioni della trama corrisponderanno raramente l'area in cui si vuole usarlo in, ma è possibile usare un tipo diverso di filtro per ottenere la scheda grafica per interpolare il colore dai pixel della trama della trama ([filtraggio della trama<C3/>).](https://msdn.microsoft.com/library/dn642451.aspx)</span><span class="sxs-lookup"><span data-stu-id="48c5e-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="48c5e-179">Il filtraggio che interessa è il [filtraggio bilineare](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) che consente di calcolare il valore di qualsiasi pixel usando i 4 adiacenti più vicini.</span><span class="sxs-lookup"><span data-stu-id="48c5e-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Originale prima del filtro](images/texture-1.png)

![Risultato dopo il filtro](images/texture-2.png)

<span data-ttu-id="48c5e-182">Utilizzando questa proprietà, si noterà che ogni volta che si tenta di creare una trama in un'area con una dimensione doppia, il risultato viene offuscato.</span><span class="sxs-lookup"><span data-stu-id="48c5e-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="48c5e-183">Anziché eseguire il rendering a schermo intero e perdere questi preziosi millisecondi, possiamo passare a un'altra versione dello schermo.</span><span class="sxs-lookup"><span data-stu-id="48c5e-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="48c5e-184">Quindi, copiando questa trama e inserendola per un fattore di due volte, viene visualizzata una schermata a schermo intero, mentre il contenuto del processo viene offuscato.</span><span class="sxs-lookup"><span data-stu-id="48c5e-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![la scalabilità di X3 torna alla risoluzione completa.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="48c5e-186">la scalabilità di X3 torna alla risoluzione completa.</span><span class="sxs-lookup"><span data-stu-id="48c5e-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="48c5e-187">Questo ci ha consentito di ottenere la parte cloud con solo una frazione del costo originale.</span><span class="sxs-lookup"><span data-stu-id="48c5e-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="48c5e-188">Anziché aggiungere i cloud alla risoluzione completa, si dipinge solo 1/64 dei pixel e si limita a riportare la trama alla risoluzione completa.</span><span class="sxs-lookup"><span data-stu-id="48c5e-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Left, con scalabilità da 1/8 a risoluzione completa; e a destra, con 3 scalabilità usando la potenza di 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="48c5e-190">Left, con scalabilità da 1/8 a risoluzione completa; e a destra, con 3 scalabilità usando la potenza di 2.</span><span class="sxs-lookup"><span data-stu-id="48c5e-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="48c5e-191">Si noti che il tentativo di passare da 1/64 dimensioni a tutte le dimensioni in un solo passaggio avrebbe un aspetto completamente diverso, in quanto la scheda grafica utilizzerebbe comunque 4 pixel nella configurazione per ombreggiare un'area più grande e iniziare a visualizzare gli artefatti.</span><span class="sxs-lookup"><span data-stu-id="48c5e-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="48c5e-192">Quindi, se si aggiungono stelle a risoluzione completa con schede più piccole, si ottiene la galassia completa:</span><span class="sxs-lookup"><span data-stu-id="48c5e-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Risultato finale del rendering Galaxy con le stelle a risoluzione completa](images/full-galaxy-500px.png)

<span data-ttu-id="48c5e-194">Una volta completata la forma, abbiamo aggiunto un livello di cloud, abbiamo scambiato i punti temporanei con quelli che abbiamo disegnato in Photoshop e abbiamo aggiunto altro colore.</span><span class="sxs-lookup"><span data-stu-id="48c5e-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="48c5e-195">Il risultato è un metodo lattiginoso, che i nostri team di progettazione e di ingegneria si sono ritenuti bravi a raggiungere i nostri obiettivi, senza sovraccaricare la CPU.</span><span class="sxs-lookup"><span data-stu-id="48c5e-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Il nostro finale della galassia per la mungitura in 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="48c5e-197">Il nostro finale della galassia per la mungitura in 3D.</span><span class="sxs-lookup"><span data-stu-id="48c5e-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="48c5e-198">Altre informazioni da esplorare</span><span class="sxs-lookup"><span data-stu-id="48c5e-198">More to explore</span></span>

<span data-ttu-id="48c5e-199">Il codice per l'app Galaxy Explorer è stato aperto e reso disponibile su [GitHub](https://github.com/Microsoft/GalaxyExplorer) per consentire agli sviluppatori di eseguire la compilazione.</span><span class="sxs-lookup"><span data-stu-id="48c5e-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="48c5e-200">Si è interessati a trovare altre informazioni sul processo di sviluppo per Galaxy Explorer?</span><span class="sxs-lookup"><span data-stu-id="48c5e-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="48c5e-201">Scopri tutti gli aggiornamenti del progetto precedenti sul [canale Microsoft HoloLens YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="48c5e-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="48c5e-202">Informazioni sugli autori</span><span class="sxs-lookup"><span data-stu-id="48c5e-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="48c5e-203"><b>Karim Luccin</b> è un tecnico di software e appassionato di oggetti visivi.</span><span class="sxs-lookup"><span data-stu-id="48c5e-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="48c5e-204">Era il tecnico di grafica per Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="48c5e-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="48c5e-205"><b>Andy Zibits</b> è un responsabile artistico e un appassionato di spazio che ha gestito il team di modellazione 3D per Galaxy Explorer e ha combattuto un numero ancora maggiore di particelle.</span><span class="sxs-lookup"><span data-stu-id="48c5e-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="48c5e-206">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="48c5e-206">See also</span></span>
* [<span data-ttu-id="48c5e-207">Galaxy Explorer su GitHub</span><span class="sxs-lookup"><span data-stu-id="48c5e-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="48c5e-208">Aggiornamenti del progetto di Galaxy Explorer in YouTube</span><span class="sxs-lookup"><span data-stu-id="48c5e-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
