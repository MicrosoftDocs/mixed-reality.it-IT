---
title: Audio in realtà mista
description: L'audio in realtà mista può aumentare la confidenza degli utenti nelle interazioni dell'interfaccia utente e immergere gli utenti nell'esperienza.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Audio spaziale, audio surround, audio 3D, audio 3D, audio spaziale
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181981"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="f0c9f-104">Audio in realtà mista</span><span class="sxs-lookup"><span data-stu-id="f0c9f-104">Audio in mixed reality</span></span>
<span data-ttu-id="f0c9f-105">L'audio è una parte essenziale della progettazione e della produttività in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="f0c9f-106">Il suono può:</span><span class="sxs-lookup"><span data-stu-id="f0c9f-106">Sound can:</span></span>
* <span data-ttu-id="f0c9f-107">Aumentare la confidenza degli utenti nelle interazioni con movimento e voce.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="f0c9f-108">Guida gli utenti ai passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-108">Guide users to next steps.</span></span>
* <span data-ttu-id="f0c9f-109">Combinare efficacemente gli oggetti virtuali con il mondo reale.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="f0c9f-110">Il rilevamento Head a bassa latenza degli auricolari per la realtà mista, tra cui HoloLens, supporta la spazializzazione basata su HRTF di alta qualità.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="f0c9f-111">È possibile spatialize audio nell'applicazione per:</span><span class="sxs-lookup"><span data-stu-id="f0c9f-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="f0c9f-112">Richiama l'attenzione sugli elementi visivi.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="f0c9f-113">Consentire agli utenti di mantenere la consapevolezza degli ambienti reali.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="f0c9f-114">I componenti acustici connettono gli ologrammi al mondo della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="f0c9f-115">Fornisce indicazioni sull'ambiente e sullo stato dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="f0c9f-116">Vedere esempi dettagliati [di progettazione che usa audio](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="f0c9f-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="f0c9f-117">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="f0c9f-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f0c9f-118"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="f0c9f-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f0c9f-119"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0c9f-119"><a href="hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f0c9f-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f0c9f-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f0c9f-121"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0c9f-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f0c9f-122">Spazializzazione</span><span class="sxs-lookup"><span data-stu-id="f0c9f-122">Spatialization</span></span></td>
        <td><span data-ttu-id="f0c9f-123">✔️</span><span class="sxs-lookup"><span data-stu-id="f0c9f-123">✔️</span></span></td>
        <td><span data-ttu-id="f0c9f-124">✔️</span><span class="sxs-lookup"><span data-stu-id="f0c9f-124">✔️</span></span></td>
        <td><span data-ttu-id="f0c9f-125">✔️</span><span class="sxs-lookup"><span data-stu-id="f0c9f-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f0c9f-126">Accelerazione hardware di spazializzazione</span><span class="sxs-lookup"><span data-stu-id="f0c9f-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f0c9f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="f0c9f-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="f0c9f-128">Uso di suoni in realtà mista</span><span class="sxs-lookup"><span data-stu-id="f0c9f-128">Use of sounds in mixed reality</span></span>
<span data-ttu-id="f0c9f-129">L' [uso di suoni in realtà mista](spatial-sound-design.md) richiede un approccio diverso rispetto alle applicazioni touch e Keyboard-and-mouse.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="f0c9f-130">Le decisioni principali relative alla progettazione sono i suoni da spatialize e le interazioni con Sonify.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="f0c9f-131">Queste decisioni influiscono fortemente sulla confidenza degli utenti, sulla produttività e sulla curva di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="f0c9f-132">Case study</span><span class="sxs-lookup"><span data-stu-id="f0c9f-132">Case studies</span></span>
<span data-ttu-id="f0c9f-133">HoloTour virtualmente gli utenti a siti turistici e cronologici in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="f0c9f-134">Vedere la [progettazione audio per HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="f0c9f-135">Per acquisire gli spazi oggetto sono stati usati un microfono speciale e una configurazione per il rendering.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="f0c9f-136">RoboRaid è uno sparatutto ad alta energia per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="f0c9f-137">La [progettazione audio per RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study descrive le scelte di progettazione effettuate per garantire che l'audio spaziale sia stato usato per l'effetto drammatico più completo.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="f0c9f-138">Spazializzazione</span><span class="sxs-lookup"><span data-stu-id="f0c9f-138">Spatialization</span></span>
<span data-ttu-id="f0c9f-139">La spazializzazione è il componente direzionale dell'audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="f0c9f-140">Per una configurazione di 7,1 Home Theater, la spazializzazione è semplice come la panoramica tra gli altoparlanti.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="f0c9f-141">Tuttavia, per le cuffie in realtà mista, è essenziale usare una tecnologia basata su HRTF per l'accuratezza e la comodità.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="f0c9f-142">Windows offre la spazializzazione basata su HRTF e questo supporto è con accelerazione hardware in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="f0c9f-143">Devo spatialize?</span><span class="sxs-lookup"><span data-stu-id="f0c9f-143">Should I spatialize?</span></span>
<span data-ttu-id="f0c9f-144">La spazializzazione può migliorare molti suoni nelle applicazioni a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="f0c9f-145">La spazializzazione estrae un suono dal capo del listener e lo inserisce nel mondo.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="f0c9f-146">Per suggerimenti sull'utilizzo efficace della spazializzazione nell'applicazione, vedere [progettazione di suoni spaziali](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="f0c9f-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="f0c9f-147">Personalizzazione di Spatializer</span><span class="sxs-lookup"><span data-stu-id="f0c9f-147">Spatializer personalization</span></span>
<span data-ttu-id="f0c9f-148">HRTFs manipola le differenze di livello e fase tra le orecchie nello spettro di frequenza.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="f0c9f-149">Sono basati su modelli fisici e misurazioni delle forme Head, torso e ear (pinna).</span><span class="sxs-lookup"><span data-stu-id="f0c9f-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="f0c9f-150">I nostri cervelli rispondono a queste differenze per fornire una direzione percepita nel suono.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="f0c9f-151">Ogni persona ha una forma orecchio, una dimensione della testa e una posizione dell'orecchio univoche.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="f0c9f-152">Il HRTFs migliore è quindi conforme all'utente.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="f0c9f-153">Per aumentare l'accuratezza della spazialità, HoloLens usa la distanza tra gli alunni (dpi) dalle schermate dell'auricolare per modificare il HRTFs per le dimensioni della testa.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="f0c9f-154">Supporto della piattaforma Spatializer</span><span class="sxs-lookup"><span data-stu-id="f0c9f-154">Spatializer platform support</span></span>
<span data-ttu-id="f0c9f-155">Windows offre la spazializzazione, tra cui HRTFs, tramite l' [API ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span><span class="sxs-lookup"><span data-stu-id="f0c9f-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="f0c9f-156">Questa API espone l'accelerazione hardware HoloLens 2 HRTF alle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="f0c9f-157">Supporto del middleware Spatializer</span><span class="sxs-lookup"><span data-stu-id="f0c9f-157">Spatializer middleware support</span></span>
<span data-ttu-id="f0c9f-158">Il supporto per HRTFs di Windows è disponibile per i motori audio di terze parti seguenti.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="f0c9f-159">Plug-in del [motore audio Unity](spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="f0c9f-159">A [Unity audio engine plugin](spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="f0c9f-160">Plug-in del [motore audio Wwise](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="f0c9f-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="f0c9f-161">Acustica</span><span class="sxs-lookup"><span data-stu-id="f0c9f-161">Acoustics</span></span>
<span data-ttu-id="f0c9f-162">L'audio spaziale è più di una direzione.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="f0c9f-163">Altre dimensioni includono l'occlusione, l'ostruzione, il riverbero, il portale e la modellazione dell'origine.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-163">Other dimensions include occlusion, obstruction, reverb, portalling, and source modeling.</span></span> <span data-ttu-id="f0c9f-164">Complessivamente, queste dimensioni vengono definite *acustiche*.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="f0c9f-165">Senza acustica, i suoni spaziali non hanno una distanza percepita.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="f0c9f-166">I trattamenti acustici variano da semplice a molto complesso.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-166">Acoustics treatments range from simple to very complex.</span></span> <span data-ttu-id="f0c9f-167">È possibile usare un semplice riverbero supportato da qualsiasi motore audio per eseguire il push di suoni spaziali nell'ambiente del listener.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-167">You can use a simple reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="f0c9f-168">I sistemi acustici come l' [acustica del progetto](https://aka.ms/acoustics) offrono un trattamento acustico più completo e accattivante.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-168">Acoustics systems such as [Project Acoustics](https://aka.ms/acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="f0c9f-169">I progetti acustici possono modellare l'effetto di muri, porte e altra geometria della scena su un suono.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="f0c9f-170">Si tratta di un'opzione valida nei casi in cui la geometria della scena pertinente è nota in fase di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="f0c9f-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f0c9f-171">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="f0c9f-171">Next steps</span></span>
- [<span data-ttu-id="f0c9f-172">Audio spaziale in Unity</span><span class="sxs-lookup"><span data-stu-id="f0c9f-172">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
- [<span data-ttu-id="f0c9f-173">Come usare un suono in applicazioni in realtà mista</span><span class="sxs-lookup"><span data-stu-id="f0c9f-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)
