---
title: Audio in realtà mista
description: L'audio in realtà mista può aumentare la confidenza degli utenti nelle interazioni dell'interfaccia utente e immergere gli utenti nell'esperienza.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Audio spaziale, audio surround, audio 3D, audio 3D, audio spaziale
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641113"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="b4856-104">Audio in realtà mista</span><span class="sxs-lookup"><span data-stu-id="b4856-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="b4856-105">L'audio è una parte essenziale della progettazione e della produttività in realtà mista e può:</span><span class="sxs-lookup"><span data-stu-id="b4856-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="b4856-106">Aumentare la confidenza degli utenti nelle interazioni basate su movimento e voce</span><span class="sxs-lookup"><span data-stu-id="b4856-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="b4856-107">Guida per gli utenti ai passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b4856-107">Guide users to next steps</span></span>
* <span data-ttu-id="b4856-108">Combinare efficacemente oggetti virtuali con il mondo reale</span><span class="sxs-lookup"><span data-stu-id="b4856-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="b4856-109">Il rilevamento Head a bassa latenza degli auricolari per la realtà mista, incluso HoloLens, consente l'uso della spazializzazione basata su HRTF di alta qualità.</span><span class="sxs-lookup"><span data-stu-id="b4856-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="b4856-110">Spatializing audio nell'applicazione può:</span><span class="sxs-lookup"><span data-stu-id="b4856-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="b4856-111">Richiama l'attenzione sugli elementi visivi</span><span class="sxs-lookup"><span data-stu-id="b4856-111">Call attention to visual elements</span></span>
* <span data-ttu-id="b4856-112">Consentire agli utenti di mantenere la consapevolezza degli ambienti reali</span><span class="sxs-lookup"><span data-stu-id="b4856-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="b4856-113">L'aggiunta di acustica in modo più approfondito connette gli ologrammi al mondo misto e può fornire indicazioni sull'ambiente e sullo stato dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="b4856-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="b4856-114">Per esempi più dettagliati di progettazione tramite audio, vedere la pagina relativa alla [progettazione del suono](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="b4856-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="b4856-115">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="b4856-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4856-116"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="b4856-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b4856-117"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4856-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b4856-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b4856-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b4856-119"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4856-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4856-120">Spazializzazione</span><span class="sxs-lookup"><span data-stu-id="b4856-120">Spatialization</span></span></td>
        <td><span data-ttu-id="b4856-121">✔️</span><span class="sxs-lookup"><span data-stu-id="b4856-121">✔️</span></span></td>
        <td><span data-ttu-id="b4856-122">✔️</span><span class="sxs-lookup"><span data-stu-id="b4856-122">✔️</span></span></td>
        <td><span data-ttu-id="b4856-123">✔️</span><span class="sxs-lookup"><span data-stu-id="b4856-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4856-124">Accelerazione hardware di spazializzazione</span><span class="sxs-lookup"><span data-stu-id="b4856-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b4856-125">✔️</span><span class="sxs-lookup"><span data-stu-id="b4856-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="b4856-126">Uso di suoni in realtà mista</span><span class="sxs-lookup"><span data-stu-id="b4856-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="b4856-127">L' [uso di suoni in realtà mista](spatial-sound-design.md) può richiedere un approccio diverso rispetto alle applicazioni touch e tastiera e mouse.</span><span class="sxs-lookup"><span data-stu-id="b4856-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="b4856-128">Le decisioni principali relative alla progettazione sono i suoni da spatialize e le interazioni con Sonify.</span><span class="sxs-lookup"><span data-stu-id="b4856-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="b4856-129">Queste decisioni possono avere un effetto forte sulla confidenza degli utenti, sulla produttività e sulla curva di apprendimento.</span><span class="sxs-lookup"><span data-stu-id="b4856-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="b4856-130">Case study</span><span class="sxs-lookup"><span data-stu-id="b4856-130">Case studies</span></span>
<span data-ttu-id="b4856-131">HoloTour virtualmente gli utenti a siti turistici e cronologici in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="b4856-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="b4856-132">Il case study seguente descrive la progettazione del suono per HoloTour: [Sound Design per HoloTour](case-study-spatial-sound-design-for-holotour.md).</span><span class="sxs-lookup"><span data-stu-id="b4856-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="b4856-133">Per acquisire gli spazi oggetto sono stati usati un microfono speciale e una configurazione per il rendering.</span><span class="sxs-lookup"><span data-stu-id="b4856-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="b4856-134">RoboRaid è uno sparatutto ad alta energia per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b4856-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="b4856-135">Il case study seguente descrive le scelte di progettazione effettuate per garantire che l'audio spaziale sia stato usato per un effetto drammatico più completo: [progettazione sonora per RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span><span class="sxs-lookup"><span data-stu-id="b4856-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="b4856-136">Spazializzazione</span><span class="sxs-lookup"><span data-stu-id="b4856-136">Spatialization</span></span>
<span data-ttu-id="b4856-137">La spazializzazione è il componente direzionale dell'audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="b4856-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="b4856-138">Quando si usa una configurazione di 7,1 Home Theater, la spazializzazione è semplice come la panoramica tra altoparlanti più potenti.</span><span class="sxs-lookup"><span data-stu-id="b4856-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="b4856-139">Ma con le cuffie in realtà mista è essenziale usare una tecnologia basata su HRTF per l'accuratezza e la comodità.</span><span class="sxs-lookup"><span data-stu-id="b4856-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="b4856-140">Windows offre la spazializzazione basata su HRTF e questo supporto è con accelerazione hardware in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b4856-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="b4856-141">Devo spatialize?</span><span class="sxs-lookup"><span data-stu-id="b4856-141">Should I spatialize?</span></span>
<span data-ttu-id="b4856-142">Molti suoni nelle applicazioni di realtà mista traggono vantaggio dalla spazializzazione, che estrae un suono dal capo del listener e lo inserisce nel mondo.</span><span class="sxs-lookup"><span data-stu-id="b4856-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="b4856-143">Per suggerimenti sugli usi più efficaci della spazializzazione nell'applicazione, vedere [progettazione di suoni spaziali](spatial-sound-design.md) .</span><span class="sxs-lookup"><span data-stu-id="b4856-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="b4856-144">Personalizzazione di Spatializer</span><span class="sxs-lookup"><span data-stu-id="b4856-144">Spatializer personalization</span></span>
<span data-ttu-id="b4856-145">HRTFs manipola le differenze di livello e fase tra le orecchie nello spettro di frequenza.</span><span class="sxs-lookup"><span data-stu-id="b4856-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="b4856-146">Sono basati su modelli fisici e misurazioni delle forme Head, torso e ear (pinna).</span><span class="sxs-lookup"><span data-stu-id="b4856-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="b4856-147">I nostri cervelli rispondono a queste differenze per dare luogo a una percezione della direzione del suono.</span><span class="sxs-lookup"><span data-stu-id="b4856-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="b4856-148">Ogni persona ha una forma Ear univoca, una dimensione della testa e una posizione dell'orecchio, quindi i HRTFs migliori sono conformi all'utente.</span><span class="sxs-lookup"><span data-stu-id="b4856-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="b4856-149">HoloLens consente di aumentare l'accuratezza della spazialità usando la distanza tra gli alunni (dpi) dalle cuffie per modificare il HRTFs per le dimensioni della testa.</span><span class="sxs-lookup"><span data-stu-id="b4856-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="b4856-150">Supporto della piattaforma Spatializer</span><span class="sxs-lookup"><span data-stu-id="b4856-150">Spatializer platform support</span></span>
<span data-ttu-id="b4856-151">Windows offre la spazializzazione, tra cui HRTFs, tramite l' [API ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span><span class="sxs-lookup"><span data-stu-id="b4856-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="b4856-152">Questa API espone l'accelerazione hardware HoloLens 2 HRTF alle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="b4856-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="b4856-153">Supporto del middleware Spatializer</span><span class="sxs-lookup"><span data-stu-id="b4856-153">Spatializer middleware support</span></span>
<span data-ttu-id="b4856-154">Il supporto per HRTFs di Windows è disponibile per alcuni motori audio di terze parti:</span><span class="sxs-lookup"><span data-stu-id="b4856-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="b4856-155">Un plug-in del [motore audio Unity](spatial-sound-in-unity.md) chiama il XAPO HRTF</span><span class="sxs-lookup"><span data-stu-id="b4856-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="b4856-156">Un plug-in del [motore audio Wwise](https://www.audiokinetic.com/products/plug-ins/msspatial/) chiama l'API ISpatialAudioClient</span><span class="sxs-lookup"><span data-stu-id="b4856-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="b4856-157">Acustica</span><span class="sxs-lookup"><span data-stu-id="b4856-157">Acoustics</span></span>
<span data-ttu-id="b4856-158">L'audio spaziale può essere più di una direzione.</span><span class="sxs-lookup"><span data-stu-id="b4856-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="b4856-159">Altre dimensioni, tra cui l'occlusione, l'ostruzione, il riverbero, il portale e la modellazione di origine, sono definite collettivamente "acustica".</span><span class="sxs-lookup"><span data-stu-id="b4856-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="b4856-160">Senza acustica, i suoni spaziali non hanno una distanza percepita.</span><span class="sxs-lookup"><span data-stu-id="b4856-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="b4856-161">Il trattamento acustico può variare da semplice a molto complesso.</span><span class="sxs-lookup"><span data-stu-id="b4856-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="b4856-162">Utilizzando un semplice riverbero, ad esempio quello supportato da qualsiasi motore audio, è possibile eseguire il push di suoni spaziali nell'ambiente che circonda il listener.</span><span class="sxs-lookup"><span data-stu-id="b4856-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="b4856-163">Il trattamento acustico più completo e accattivante è disponibile da sistemi acustici come l' [acustica del progetto](https://aka.ms/acoustics).</span><span class="sxs-lookup"><span data-stu-id="b4856-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="b4856-164">I progetti acustici possono modellare l'effetto di muri, porte e altre geometrie in un suono ed è un'opzione efficace nei casi in cui la geometria della scena pertinente è nota in fase di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="b4856-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>

