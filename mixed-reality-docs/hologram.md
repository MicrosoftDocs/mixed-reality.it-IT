---
title: Che cos'è un ologramma?
description: HoloLens consente di visualizzare e interagire con ologrammi tridimensionali, oggetti di luce e suoni presenti in tutto il mondo.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, ologrammi, progettazione, interazione
ms.openlocfilehash: 5fb3aff3f59d0999676356d257b72f286a8d7adf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435104"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="b7c44-104">Che cos'è un ologramma?</span><span class="sxs-lookup"><span data-stu-id="b7c44-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="b7c44-105">HoloLens consente di creare **ologrammi**, oggetti costituiti da luce e suoni presenti in tutto il mondo, proprio come se fossero oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="b7c44-105">HoloLens lets you create **holograms**, objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="b7c44-106">Gli ologrammi rispondono a [sguardi](gaze-and-commit.md), [movimenti](gaze-and-commit.md#composite-gestures) e [comandi vocali](voice-input.md)e possono interagire con le [aree reali](spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="b7c44-106">Holograms respond to your [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures) and [voice commands](voice-input.md), and can interact with [real-world surfaces](spatial-mapping.md) around you.</span></span> <span data-ttu-id="b7c44-107">Con gli ologrammi puoi creare oggetti digitali che fanno parte del tuo mondo.</span><span class="sxs-lookup"><span data-stu-id="b7c44-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="b7c44-108">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="b7c44-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b7c44-109"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="b7c44-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b7c44-110"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b7c44-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b7c44-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b7c44-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b7c44-112"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="b7c44-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b7c44-113">Ologrammi</span><span class="sxs-lookup"><span data-stu-id="b7c44-113">Holograms</span></span></td>
        <td><span data-ttu-id="b7c44-114">✔️</span><span class="sxs-lookup"><span data-stu-id="b7c44-114">✔️</span></span></td>
        <td><span data-ttu-id="b7c44-115">✔️</span><span class="sxs-lookup"><span data-stu-id="b7c44-115">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="b7c44-116">Un ologramma è costituito da luce e suoni</span><span class="sxs-lookup"><span data-stu-id="b7c44-116">A hologram is made of light and sound</span></span>

<span data-ttu-id="b7c44-117">Gli ologrammi che HoloLens [esegue il rendering](rendering.md) vengono visualizzati nel frame olografico direttamente davanti agli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="b7c44-117">The holograms that HoloLens [renders](rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="b7c44-118">Gli ologrammi aggiungono luce al mondo, il che significa che è possibile visualizzare sia la luce dallo schermo che la luce dall'ambiente circostante.</span><span class="sxs-lookup"><span data-stu-id="b7c44-118">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="b7c44-119">HoloLens non rimuove la luce dagli occhi, quindi gli ologrammi non possono essere sottoposti a rendering con il colore nero.</span><span class="sxs-lookup"><span data-stu-id="b7c44-119">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="b7c44-120">Il contenuto nero viene invece visualizzato come trasparente.</span><span class="sxs-lookup"><span data-stu-id="b7c44-120">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="b7c44-121">Gli ologrammi possono avere diversi aspetti e comportamenti.</span><span class="sxs-lookup"><span data-stu-id="b7c44-121">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="b7c44-122">Alcune sono realistiche e solide e altre sono animate ed etereo.</span><span class="sxs-lookup"><span data-stu-id="b7c44-122">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="b7c44-123">Gli ologrammi possono evidenziare le funzionalità nell'ambiente in uso e possono essere elementi nell'interfaccia utente dell'app.</span><span class="sxs-lookup"><span data-stu-id="b7c44-123">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![Mano che manipola un ologramma](images/hologram-hands-940px.jpg)

<span data-ttu-id="b7c44-125">Gli ologrammi possono anche creare [suoni](spatial-sound.md), che sembrano provenire da una posizione specifica nell'ambiente in cui si trovano.</span><span class="sxs-lookup"><span data-stu-id="b7c44-125">Holograms can also make [sounds](spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="b7c44-126">In HoloLens, il suono deriva da due altoparlanti che si trovano direttamente sopra le orecchie, senza coprirli.</span><span class="sxs-lookup"><span data-stu-id="b7c44-126">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="b7c44-127">Analogamente agli schermi, i relatori sono additivi, introducendo nuovi suoni senza bloccare i suoni dall'ambiente.</span><span class="sxs-lookup"><span data-stu-id="b7c44-127">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="b7c44-128">Un ologramma può essere inserito nel mondo o nel tag insieme all'utente</span><span class="sxs-lookup"><span data-stu-id="b7c44-128">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="b7c44-129">Quando si dispone di una posizione specifica in cui si desidera un ologramma, è possibile [inserirla](coordinate-systems.md) esattamente nel mondo.</span><span class="sxs-lookup"><span data-stu-id="b7c44-129">When you have a particular location where you want a hologram, you can [place](coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="b7c44-130">Quando si tratta di un ologramma, viene visualizzato un aspetto stabile rispetto al mondo.</span><span class="sxs-lookup"><span data-stu-id="b7c44-130">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="b7c44-131">Se si usa un [ancoraggio spaziale](coordinate-systems.md#spatial-anchors) per aggiungere l'oggetto in modo consolidato al mondo, il sistema può persino ricordare dove è stato lasciato quando si torna più tardi.</span><span class="sxs-lookup"><span data-stu-id="b7c44-131">If you use a [spatial anchor](coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![Due uomini che usano il layout di Microsoft Dynamics 365 in uno spazio al dettaglio](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="b7c44-133">Alcuni ologrammi seguono invece l'utente.</span><span class="sxs-lookup"><span data-stu-id="b7c44-133">Some holograms follow the user instead.</span></span> <span data-ttu-id="b7c44-134">Gli ologrammi con tag vengono posizionati in relazione all'utente, indipendentemente dalla loro posizione.</span><span class="sxs-lookup"><span data-stu-id="b7c44-134">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="b7c44-135">È anche possibile scegliere di portare un ologramma per un po' di tempo e quindi posizionarlo sul muro quando si accede a un'altra stanza.</span><span class="sxs-lookup"><span data-stu-id="b7c44-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="b7c44-136">**Procedure consigliate**</span><span class="sxs-lookup"><span data-stu-id="b7c44-136">**Best practices**</span></span>
* <span data-ttu-id="b7c44-137">Alcuni scenari possono richiedere che gli ologrammi rimangano facilmente individuabili o visibili nell'intera esperienza.</span><span class="sxs-lookup"><span data-stu-id="b7c44-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="b7c44-138">Questo tipo di posizionamento è costituito da due approcci di alto livello.</span><span class="sxs-lookup"><span data-stu-id="b7c44-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="b7c44-139">Chiameremo **"display-locked"** e **"Body-locked"** .</span><span class="sxs-lookup"><span data-stu-id="b7c44-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="b7c44-140">Il contenuto con blocco visualizzato è posizionato "bloccato" sullo schermo del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b7c44-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="b7c44-141">Si tratta di un'operazione complessa per diversi motivi, tra cui una sensazione insensata di "clingyness" che rende molti utenti frustrati e che desiderano "eliminarli".</span><span class="sxs-lookup"><span data-stu-id="b7c44-141">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="b7c44-142">In generale, molti designer hanno ritenuto migliore di evitare il contenuto del blocco visualizzato.</span><span class="sxs-lookup"><span data-stu-id="b7c44-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="b7c44-143">L'approccio con blocco del corpo è molto più perdonabile.</span><span class="sxs-lookup"><span data-stu-id="b7c44-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="b7c44-144">Il blocco del corpo si verifica quando un ologramma è vincolato al corpo dell'utente o al vettore dello sguardo, ma è posizionato nello spazio 3D intorno all'utente.</span><span class="sxs-lookup"><span data-stu-id="b7c44-144">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="b7c44-145">Molte esperienze hanno adottato un comportamento di blocco del corpo in cui l'ologramma "segue" lo sguardo degli utenti, che consente all'utente di ruotare il corpo e spostarsi nello spazio senza perdere l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="b7c44-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="b7c44-146">L'integrazione di un ritardo aiuta il movimento dell'ologramma a essere più naturale.</span><span class="sxs-lookup"><span data-stu-id="b7c44-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="b7c44-147">Ad esempio, un'interfaccia utente di base del sistema operativo Windows olografico usa una variante del blocco del corpo che segue lo sguardo dell'utente con un ritardo di tipo elastico e elastico mentre l'utente si attiva.</span><span class="sxs-lookup"><span data-stu-id="b7c44-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="b7c44-148">Posizionare l'ologramma a una distanza di visualizzazione comoda in genere a circa 1-2 metri di distanza dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="b7c44-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="b7c44-149">Fornire una certa tendenza per gli elementi che devono essere continuamente nel frame olografico oppure provare ad animare il contenuto su un lato dello schermo quando l'utente modifica il proprio punto di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b7c44-149">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="b7c44-150">**Posizionare gli ologrammi nell'area ottimale, tra 1.25 m e 5m**</span><span class="sxs-lookup"><span data-stu-id="b7c44-150">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="b7c44-151">Due contatori sono i più ottimali e l'esperienza ridurrà il più vicino possibile da un contatore.</span><span class="sxs-lookup"><span data-stu-id="b7c44-151">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="b7c44-152">A distanze più vicine a un metro, gli ologrammi che si spostano regolarmente in profondità sono più probabilmente problematici degli ologrammi stazionari.</span><span class="sxs-lookup"><span data-stu-id="b7c44-152">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="b7c44-153">Prendere in considerazione la possibilità di ritagliare o dissolvere il contenuto quando diventa troppo vicino, in modo da non inserirlo in un'esperienza imprevista.</span><span class="sxs-lookup"><span data-stu-id="b7c44-153">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![Distanza ottimale per inserire gli ologrammi dall'utente.](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="b7c44-155">Un ologramma interagisce con l'utente e il mondo</span><span class="sxs-lookup"><span data-stu-id="b7c44-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="b7c44-156">Gli ologrammi non hanno solo la luce e il suono; sono anche una parte attiva del mondo.</span><span class="sxs-lookup"><span data-stu-id="b7c44-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="b7c44-157">Osservando un ologramma e un gesto con la mano, un ologramma può iniziare a seguire l'utente.</span><span class="sxs-lookup"><span data-stu-id="b7c44-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="b7c44-158">Fornire un comando Voice a un ologramma, che può rispondere.</span><span class="sxs-lookup"><span data-stu-id="b7c44-158">Give a voice command to a hologram, and it can reply.</span></span>

![Gruppo di utenti governativi che usano Microsoft HoloLens 2 per collaborare a un progetto di sviluppo di una farm eolica](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="b7c44-160">Gli ologrammi consentono interazioni personali che non sono possibili altrove.</span><span class="sxs-lookup"><span data-stu-id="b7c44-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="b7c44-161">Poiché il HoloLens sa dove si trova nel mondo, un carattere olografico può esaminarlo direttamente quando si cammina intorno alla stanza.</span><span class="sxs-lookup"><span data-stu-id="b7c44-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="b7c44-162">Un ologramma può interagire anche con l'ambiente in uso.</span><span class="sxs-lookup"><span data-stu-id="b7c44-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="b7c44-163">Ad esempio, è possibile inserire una palla da rimbalzo olografica sopra una tabella.</span><span class="sxs-lookup"><span data-stu-id="b7c44-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="b7c44-164">Quindi, con un [Rubinetto aria](gaze-and-commit.md#composite-gestures), guardare il rimbalzo della palla e creare un suono quando si raggiunge la tabella.</span><span class="sxs-lookup"><span data-stu-id="b7c44-164">Then, with an [air tap](gaze-and-commit.md#composite-gestures), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="b7c44-165">Gli ologrammi possono anche essere bloccati da oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="b7c44-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="b7c44-166">Un carattere olografico, ad esempio, può spostarsi tra una porta e un muro, fuori dalla propria visione.</span><span class="sxs-lookup"><span data-stu-id="b7c44-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="b7c44-167">**Suggerimenti per l'integrazione di ologrammi e il mondo reale**</span><span class="sxs-lookup"><span data-stu-id="b7c44-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="b7c44-168">L'allineamento alle regole gravitazionali rende gli ologrammi più semplici da correlare e più credibili.</span><span class="sxs-lookup"><span data-stu-id="b7c44-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="b7c44-169">ad esempio: posizionare un cane olografico & un vaso sulla tabella anziché inserirli nello spazio.</span><span class="sxs-lookup"><span data-stu-id="b7c44-169">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="b7c44-170">Molti designer hanno scoperto che possono integrare gli ologrammi in modo ancora più credibile creando un'ombreggiatura negativa sulla superficie in cui si trova l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="b7c44-170">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="b7c44-171">A tale scopo, è possibile creare un alone di luce intorno all'ologramma e quindi sottrarre l'ombreggiatura dal bagliore.</span><span class="sxs-lookup"><span data-stu-id="b7c44-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="b7c44-172">Il Soft Glow si integra con la luce del mondo reale e con i motivi dell'ombreggiatura dell'ologramma nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="b7c44-172">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="b7c44-173">Un ologramma è qualsiasi</span><span class="sxs-lookup"><span data-stu-id="b7c44-173">A hologram is whatever</span></span> <br><span data-ttu-id="b7c44-174">è possibile sognare</span><span class="sxs-lookup"><span data-stu-id="b7c44-174">you can dream up</span></span><br>
        <span data-ttu-id="b7c44-175">Gli sviluppatori olografici hanno la possibilità di suddividere la creatività dalle schermate 2D e in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="b7c44-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="b7c44-176">*Che cosa compilerai* ?</span><span class="sxs-lookup"><span data-stu-id="b7c44-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b7c44-177">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b7c44-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b7c44-178">![mondo immaginario olografico in una stanza vivente](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="b7c44-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a><span data-ttu-id="b7c44-179">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b7c44-179">See also</span></span>
* [<span data-ttu-id="b7c44-180">Espandi il processo di progettazione</span><span class="sxs-lookup"><span data-stu-id="b7c44-180">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)
* [<span data-ttu-id="b7c44-181">Audio spaziale</span><span class="sxs-lookup"><span data-stu-id="b7c44-181">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b7c44-182">Colore, luce e materiali</span><span class="sxs-lookup"><span data-stu-id="b7c44-182">Color, light and materials</span></span>](color,-light-and-materials.md)
