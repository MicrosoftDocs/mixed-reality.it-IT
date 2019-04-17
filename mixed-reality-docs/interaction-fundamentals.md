---
title: Nozioni fondamentali di interazione
description: Come abbiamo creato esperienze tra HoloLens (dal 1 ° generazione), 2 HoloLens e auricolari coinvolgenti, abbiamo iniziato a scrivere verso il basso alcuni elementi sono stati trovati utile condividere.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Progettare l'interazione, realtà mista
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597552"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="2eafe-104">Nozioni fondamentali di interazione</span><span class="sxs-lookup"><span data-stu-id="2eafe-104">Interaction fundamentals</span></span>

<span data-ttu-id="2eafe-105">Come abbiamo creato esperienze in HoloLens e auricolari coinvolgenti, abbiamo iniziato a scrivere verso il basso alcuni elementi che sono stati trovati utile condividere.</span><span class="sxs-lookup"><span data-stu-id="2eafe-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="2eafe-106">Pensare a queste informazioni come i blocchi predefiniti fondamentali per la progettazione di interazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="2eafe-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="2eafe-107">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="2eafe-107">Device support</span></span>

<span data-ttu-id="2eafe-108">Di seguito è una struttura degli articoli di progettazione di interazione disponibili e il tipo di dispositivo o dei tipi sono applicabili ai.</span><span class="sxs-lookup"><span data-stu-id="2eafe-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="2eafe-109"><strong>Input</strong></span><span class="sxs-lookup"><span data-stu-id="2eafe-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="2eafe-110"><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2eafe-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="2eafe-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2eafe-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="2eafe-112"><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></span><span class="sxs-lookup"><span data-stu-id="2eafe-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="2eafe-113"><a href="gestures.md">Articolati e mani</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="2eafe-114">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="2eafe-115"><a href="gaze-targeting.md">Destinazione rossi</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="2eafe-116">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="2eafe-117"><a href="gaze-targeting.md">Sguardo targeting</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-118">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-119">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-120">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2eafe-121"><a href="gestures.md">Movimenti</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-122">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="2eafe-124"><a href="voice-design.md">Progettazione vocale</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-125">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-126">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2eafe-128">Game pad</span><span class="sxs-lookup"><span data-stu-id="2eafe-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-129">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-130">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-131">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="2eafe-132"><a href="motion-controllers.md">Controller di movimento</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="2eafe-133">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="2eafe-134"><strong>Percezione e nuove funzionalità spaziali</strong></span><span class="sxs-lookup"><span data-stu-id="2eafe-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="2eafe-135"><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2eafe-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="2eafe-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2eafe-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="2eafe-137"><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></span><span class="sxs-lookup"><span data-stu-id="2eafe-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="2eafe-138"><a href="spatial-sound-design.md">Progettazione spaziale</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-139">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-140">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-141">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2eafe-142"><a href="spatial-mapping-design.md">Progettazione di mapping spaziale</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-143">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-144">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="2eafe-145"><a href="hologram.md">Ologrammi</a></span><span class="sxs-lookup"><span data-stu-id="2eafe-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-146">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="2eafe-147">✔️</span><span class="sxs-lookup"><span data-stu-id="2eafe-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="2eafe-148">L'utente è la fotocamera</span><span class="sxs-lookup"><span data-stu-id="2eafe-148">The user is the camera</span></span>

![L'utente che corrisponde alla fotocamera](images/useriscamera-640px.jpg)

<span data-ttu-id="2eafe-150">Considerare sempre sulla progettazione per il punto di vista dell'utente quando vengono spostati sui loro ambienti reali e virtuali.</span><span class="sxs-lookup"><span data-stu-id="2eafe-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="2eafe-151">**Alcune domande da chiedere**</span><span class="sxs-lookup"><span data-stu-id="2eafe-151">**Some questions to ask**</span></span>
* <span data-ttu-id="2eafe-152">È l'utente che si trova, schienale, permanente o walking quando si usa l'esperienza?</span><span class="sxs-lookup"><span data-stu-id="2eafe-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="2eafe-153">La modalità modificare i contenuti in posizioni diverse?</span><span class="sxs-lookup"><span data-stu-id="2eafe-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="2eafe-154">L'utente può regolare lo?</span><span class="sxs-lookup"><span data-stu-id="2eafe-154">Can the user adjust it?</span></span>
* <span data-ttu-id="2eafe-155">L'utente è a proprio agio usando l'app?</span><span class="sxs-lookup"><span data-stu-id="2eafe-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="2eafe-156">**Procedure consigliate**</span><span class="sxs-lookup"><span data-stu-id="2eafe-156">**Best practices**</span></span>
* <span data-ttu-id="2eafe-157">L'utente è la fotocamera e controllano lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="2eafe-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="2eafe-158">"Let" tali unità.</span><span class="sxs-lookup"><span data-stu-id="2eafe-158">Let them drive.</span></span>
* <span data-ttu-id="2eafe-159">Se è necessario per il trasporto praticamente l'utente, essere sensibili a problemi riguardanti il disturbo vestibular.</span><span class="sxs-lookup"><span data-stu-id="2eafe-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="2eafe-160">Usare le animazioni più breve</span><span class="sxs-lookup"><span data-stu-id="2eafe-160">Use shorter animations</span></span>
* <span data-ttu-id="2eafe-161">Aggiungere un'animazione da verso il basso/a sinistra/destra o la dissolvenza in entrata invece di Z</span><span class="sxs-lookup"><span data-stu-id="2eafe-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="2eafe-162">Rallentare temporizzazione</span><span class="sxs-lookup"><span data-stu-id="2eafe-162">Slow down timing</span></span>
* <span data-ttu-id="2eafe-163">Consente di visualizzare il mondo in background</span><span class="sxs-lookup"><span data-stu-id="2eafe-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="2eafe-164">**Cosa evitare**</span><span class="sxs-lookup"><span data-stu-id="2eafe-164">**What to avoid**</span></span>
* <span data-ttu-id="2eafe-165">Non shake della fotocamera o intenzionalmente bloccato a 3DOF (solo l'orientamento, senza conversione), è possibile rendere gli utenti preferisce.</span><span class="sxs-lookup"><span data-stu-id="2eafe-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="2eafe-166">Nessun movimento improvvisa.</span><span class="sxs-lookup"><span data-stu-id="2eafe-166">No abrupt movement.</span></span> <span data-ttu-id="2eafe-167">Se devi trasferire contenuto da o verso l'utente, spostarlo lentamente e senza problemi verso di loro per la massima comodità.</span><span class="sxs-lookup"><span data-stu-id="2eafe-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="2eafe-168">Gli utenti reagirà ai menu di grandi dimensioni presto a tali file.</span><span class="sxs-lookup"><span data-stu-id="2eafe-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="2eafe-169">Non accelerare o attivare fotocamera dell'utente.</span><span class="sxs-lookup"><span data-stu-id="2eafe-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="2eafe-170">Gli utenti sono riservati per l'accelerazione (angular e traslazione).</span><span class="sxs-lookup"><span data-stu-id="2eafe-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="2eafe-171">Sfruttare prospettiva dell'utente</span><span class="sxs-lookup"><span data-stu-id="2eafe-171">Leverage the user's perspective</span></span>

<span data-ttu-id="2eafe-172">Gli utenti vedono il mondo delle realtà mista tramite consente di visualizzare nei dispositivi coinvolgenti e holographic.</span><span class="sxs-lookup"><span data-stu-id="2eafe-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="2eafe-173">Nella finestra di HoloLens, questa visualizzazione viene chiamata la [frame holographic](holographic-frame.md).</span><span class="sxs-lookup"><span data-stu-id="2eafe-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="2eafe-174">Nell'ambiente di sviluppo 2D contenuto a cui si accede di frequente e delle impostazioni possono essere inserite negli angoli di una schermata per renderli facilmente accessibili.</span><span class="sxs-lookup"><span data-stu-id="2eafe-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="2eafe-175">Tuttavia, holographic le app, il contenuto negli angoli della visualizzazione dell'utente potrà essere prepararli per l'accesso.</span><span class="sxs-lookup"><span data-stu-id="2eafe-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="2eafe-176">In questo caso, il centro del frame holographic è il percorso principale per il contenuto.</span><span class="sxs-lookup"><span data-stu-id="2eafe-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="2eafe-177">L'utente potrebbe essere necessario tener conto per agevolare l'individuazione oggetti oltre la visualizzazione immediata o eventi importanti.</span><span class="sxs-lookup"><span data-stu-id="2eafe-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="2eafe-178">È possibile utilizzare le frecce, gli itinerari di luce, movimento della testina del carattere, fumetti, puntatori, spaziale audio e istruzioni vocali guideranno l'utente al contenuto importante nell'app.</span><span class="sxs-lookup"><span data-stu-id="2eafe-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="2eafe-179">È consigliabile non blocco contenuto sullo schermo per comodità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="2eafe-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="2eafe-180">Se si desidera mantenere il contenuto nella visualizzazione, inserire in tutto il mondo e rendere il contenuto "tag-along", ad esempio il menu Start.</span><span class="sxs-lookup"><span data-stu-id="2eafe-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="2eafe-181">Si sentiranno più naturale nell'ambiente di contenuto che viene inserito insieme a prospettiva dell'utente.</span><span class="sxs-lookup"><span data-stu-id="2eafe-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="2eafe-182">![Nel menu start segue la visualizzazione dell'utente quando viene raggiunto il bordo del frame](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2eafe-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="2eafe-183">*Nel menu Start segue la visualizzazione dell'utente quando viene raggiunto il bordo del frame*</span><span class="sxs-lookup"><span data-stu-id="2eafe-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="2eafe-184">Su HoloLens, vntana sentirsi reale quando rientrano all'interno della cornice holographic poiché essi non tagliate.</span><span class="sxs-lookup"><span data-stu-id="2eafe-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="2eafe-185">Gli utenti verranno spostato al fine di determinare i limiti di ologramma all'interno del frame.</span><span class="sxs-lookup"><span data-stu-id="2eafe-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="2eafe-186">Su HoloLens, è importante semplificare l'interfaccia utente per rientri in vista dell'utente e mantenere l'attenzione sull'azione principale.</span><span class="sxs-lookup"><span data-stu-id="2eafe-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="2eafe-187">Per le cuffie coinvolgenti, è importante mantenere l'illusione di un mondo virtuale persistente all'interno il del dispositivo campo visivo.</span><span class="sxs-lookup"><span data-stu-id="2eafe-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="2eafe-188">Fattore di comfort utente</span><span class="sxs-lookup"><span data-stu-id="2eafe-188">User comfort</span></span>

<span data-ttu-id="2eafe-189">Per garantire la massima [fattore di comfort](comfort.md) sugli schermi montato head, è importante per progettisti e sviluppatori di creare e presentare il contenuto in modo che simuli come esseri umani interpretano le forme 3D e la posizione relativa degli oggetti in naturale World.</span><span class="sxs-lookup"><span data-stu-id="2eafe-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="2eafe-190">Dal punto di vista fisico, è anche importante progettare il contenuto che non richiede difficoltoso i movimenti del collo o agli armamenti.</span><span class="sxs-lookup"><span data-stu-id="2eafe-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="2eafe-191">Se lo sviluppo per HoloLens o auricolari coinvolgenti, è importante eseguire il rendering degli oggetti visivi per entrambi gli occhi.</span><span class="sxs-lookup"><span data-stu-id="2eafe-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="2eafe-192">Il rendering di una visualizzazione hud un occhio può apportare solo un'interfaccia difficili da comprendere, nonché causare uneasiness occhio e cervello dell'utente.</span><span class="sxs-lookup"><span data-stu-id="2eafe-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="2eafe-193">Condividere la propria esperienza</span><span class="sxs-lookup"><span data-stu-id="2eafe-193">Share your experience</span></span>

<span data-ttu-id="2eafe-194">Usando [acquisizione di realtà mista](mixed-reality-capture.md), gli utenti possono acquisire una foto o video della propria esperienza in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="2eafe-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="2eafe-195">Prendere in considerazione esperienze nell'app in cui si desidera incoraggiare gli snapshot o video.</span><span class="sxs-lookup"><span data-stu-id="2eafe-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="2eafe-196">Usare elementi di base dell'interfaccia utente di casa la realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="2eafe-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="2eafe-197">Esattamente come viene avviata l'esperienza di PC Windows con il desktop, realtà mista di Windows viene avviata con la home page.</span><span class="sxs-lookup"><span data-stu-id="2eafe-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="2eafe-198">Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) sfrutta la nostra capacità innata per comprendere e spostarsi tra punti 3D.</span><span class="sxs-lookup"><span data-stu-id="2eafe-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="2eafe-199">Con HoloLens, la home page è lo spazio fisico.</span><span class="sxs-lookup"><span data-stu-id="2eafe-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="2eafe-200">Con immersive auricolari, la home page è un punto virtuale.</span><span class="sxs-lookup"><span data-stu-id="2eafe-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="2eafe-201">La home page è anche in cui si userà il menu Start aprire e inserire le App e il contenuto.</span><span class="sxs-lookup"><span data-stu-id="2eafe-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="2eafe-202">È possibile compilare la home page con contenuto di realtà mista e multitasking con più App contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="2eafe-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="2eafe-203">Le operazioni posizionate in casa rimangono non esiste, anche se si riavvia il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2eafe-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="2eafe-204">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2eafe-204">See also</span></span>
* [<span data-ttu-id="2eafe-205">Sguardo targeting</span><span class="sxs-lookup"><span data-stu-id="2eafe-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="2eafe-206">Movimenti</span><span class="sxs-lookup"><span data-stu-id="2eafe-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="2eafe-207">Progettazione vocale</span><span class="sxs-lookup"><span data-stu-id="2eafe-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="2eafe-208">Controller di movimento</span><span class="sxs-lookup"><span data-stu-id="2eafe-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="2eafe-209">Progettazione spaziale</span><span class="sxs-lookup"><span data-stu-id="2eafe-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="2eafe-210">Progettazione di mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="2eafe-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="2eafe-211">Comfort</span><span class="sxs-lookup"><span data-stu-id="2eafe-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="2eafe-212">Esplorazione di realtà mista di Windows home</span><span class="sxs-lookup"><span data-stu-id="2eafe-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
