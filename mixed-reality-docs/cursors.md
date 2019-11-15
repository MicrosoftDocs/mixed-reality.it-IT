---
title: Cursori
description: Un cursore, o un indicatore del vettore di destinazione, fornisce un feedback continuo all'utente per comprendere quali sono le intenzioni di HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1a generazione), HoloLens 2, realtà mista, cursori, targeting, sguardi, movimenti
ms.openlocfilehash: 719e7a573e8c8bc682ec0f960d9f3c8f8c8e5a4a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105746"
---
# <a name="cursors"></a><span data-ttu-id="a6570-104">Cursori</span><span class="sxs-lookup"><span data-stu-id="a6570-104">Cursors</span></span>

![Cursori](images/UX/UX_Hero_Cursor.jpg)

<span data-ttu-id="a6570-106">Un cursore, o un indicatore del vettore di destinazione corrente, fornisce un feedback continuo all'utente per comprendere la posizione in cui l'auricolare ritiene che lo stato attivo corrente sia in quel momento.</span><span class="sxs-lookup"><span data-stu-id="a6570-106">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="a6570-107">Il cursore consente all'utente di comprendere il punto di destinazione corrente e funge da feedback per indicare quale area, ologramma o punto risponderà all'input.</span><span class="sxs-lookup"><span data-stu-id="a6570-107">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="a6570-108">Si tratta della rappresentazione digitale del punto in cui il dispositivo è in grado di comprendere l'attenzione dell'utente (anche se ciò potrebbe non essere uguale a quello di determinare le proprie intenzioni).</span><span class="sxs-lookup"><span data-stu-id="a6570-108">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="a6570-109">Il feedback fornito dal cursore offre agli utenti la possibilità di prevedere il modo in cui il sistema risponderà, utilizzare tale segnale come feedback per comunicare meglio la loro intenzione al dispositivo e, infine, avere maggiore fiducia sulle interazioni.</span><span class="sxs-lookup"><span data-stu-id="a6570-109">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="a6570-110">Sono disponibili tre tipi di cursori: **Finger, Ray**e **Head-sguardi**.</span><span class="sxs-lookup"><span data-stu-id="a6570-110">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="a6570-111">Questi puntatori funzionano con diverse modalità di input in HoloLens, HoloLens 2 e auricolari immersivi.</span><span class="sxs-lookup"><span data-stu-id="a6570-111">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="a6570-112">Di seguito sono riportate informazioni aggiuntive sul tipo di cursore da usare per ogni tipo di modello di auricolare e interazione.</span><span class="sxs-lookup"><span data-stu-id="a6570-112">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="a6570-113">Nel Toolkit di realtà mista (MRTK) sono stati creati moduli per i cursori con trascinamento della selezione che consentono di creare l'esperienza di puntamento corretta.</span><span class="sxs-lookup"><span data-stu-id="a6570-113">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="a6570-114">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a6570-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a6570-115"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="a6570-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a6570-116"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a6570-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a6570-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a6570-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a6570-118"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="a6570-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a6570-119">Cursore dito</span><span class="sxs-lookup"><span data-stu-id="a6570-119">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a6570-120">✔️</span><span class="sxs-lookup"><span data-stu-id="a6570-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="a6570-121">Cursore Ray</span><span class="sxs-lookup"><span data-stu-id="a6570-121">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="a6570-122">✔️</span><span class="sxs-lookup"><span data-stu-id="a6570-122">✔️</span></span></td>
        <td><span data-ttu-id="a6570-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a6570-123">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="a6570-124">Cursore Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="a6570-124">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="a6570-125">✔️</span><span class="sxs-lookup"><span data-stu-id="a6570-125">✔️</span></span></td>
        <td><span data-ttu-id="a6570-126">✔️</span><span class="sxs-lookup"><span data-stu-id="a6570-126">✔️</span></span></td>
        <td><span data-ttu-id="a6570-127">✔️</span><span class="sxs-lookup"><span data-stu-id="a6570-127">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="a6570-128">Cursore dito</span><span class="sxs-lookup"><span data-stu-id="a6570-128">Finger cursor</span></span>
<span data-ttu-id="a6570-129">Il cursore Finger è disponibile solo in HoloLens 2 per migliorare la modalità di interazione "[manipolazione diretta con mani](direct-manipulation.md)".</span><span class="sxs-lookup"><span data-stu-id="a6570-129">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="a6570-130">Per comprendere meglio la posizione del dito, sono stati collegati anelli ai suggerimenti di entrambe le dita degli indici.</span><span class="sxs-lookup"><span data-stu-id="a6570-130">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="a6570-131">Le dimensioni della suoneria si basano sulla prossimità del dito alla superficie dell'interfaccia utente (più vicino al dito, minore è l'anello) e si ridurrà a una forma punto quando il dito si mette in contatto con l'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="a6570-131">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="a6570-132">](images/finger-cursor.png) cursore dito ![</span><span class="sxs-lookup"><span data-stu-id="a6570-132">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="a6570-133">**Stati feedback visivi del cursore dito** 1: l'anello si riduce a un punto.</span><span class="sxs-lookup"><span data-stu-id="a6570-133">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="a6570-134">2: l'anello è allineato alla superficie.</span><span class="sxs-lookup"><span data-stu-id="a6570-134">2: The ring aligns with surface.</span></span> <span data-ttu-id="a6570-135">3: l'anello è perpendicolare al vettore del dito.</span><span class="sxs-lookup"><span data-stu-id="a6570-135">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="a6570-136">4: nessun anello.</span><span class="sxs-lookup"><span data-stu-id="a6570-136">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="a6570-137">Cursore Ray</span><span class="sxs-lookup"><span data-stu-id="a6570-137">Ray cursor</span></span>
<span data-ttu-id="a6570-138">I cursori raggio si allineano alla fine dei raggi di puntamento per consentire la manipolazione di oggetti fuori dalla portata di mano.</span><span class="sxs-lookup"><span data-stu-id="a6570-138">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="a6570-139">Negli auricolari immersivi, i raggi vengono ritirati dai controller di movimento e terminano con i cursori a punti.</span><span class="sxs-lookup"><span data-stu-id="a6570-139">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="a6570-140">In HoloLens 2 viene usato il modello mentale di questi raggi del controller di movimento e i raggi mano progettati che hanno origine dalle palme e terminano con cursori a forma di anello coerenti con i cursori con dito usati nella manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="a6570-140">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="a6570-141">![controller del cursore a raggi](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="a6570-141">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="a6570-142">**Cursori Ray dei controller di movimento**</span><span class="sxs-lookup"><span data-stu-id="a6570-142">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a6570-143">](images/ray-cursor-hand.png) mano del cursore ![raggio</span><span class="sxs-lookup"><span data-stu-id="a6570-143">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="a6570-144">**Cursori raggio delle mani**</span><span class="sxs-lookup"><span data-stu-id="a6570-144">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="a6570-145">Cursore Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="a6570-145">Head-gaze cursor</span></span>
<span data-ttu-id="a6570-146">Il cursore Head-sguardi è un punto che si connette alla fine di un vettore di sguardi invisibili che usa la posizione e la rotazione dell'intestazione verso il punto.</span><span class="sxs-lookup"><span data-stu-id="a6570-146">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="a6570-147">Per eseguire le azioni, questo cursore di puntamento è associato a diversi input di commit, ad esempio il tocco aereo, i comandi vocali, l'abitazione e la pressione del pulsante.</span><span class="sxs-lookup"><span data-stu-id="a6570-147">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="a6570-148">In HoloLens 2, il punto di partenza è meglio abbinato a qualsiasi input di commit che non sia il rubinetto aereo, in quanto si verifica un conflitto di interazione tra il tocco aereo e i raggi di mano.</span><span class="sxs-lookup"><span data-stu-id="a6570-148">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="a6570-149">![la mano del cursore](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="a6570-149">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="a6570-150">**Cursore Head-sguardi con movimento mano**</span><span class="sxs-lookup"><span data-stu-id="a6570-150">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="a6570-151">](images/head-gaze-cursor-voice.png) voce cursore ![sguardo a capo</span><span class="sxs-lookup"><span data-stu-id="a6570-151">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="a6570-152">**Cursore Head-sguardi con comando Voice**</span><span class="sxs-lookup"><span data-stu-id="a6570-152">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="a6570-153">Suggerimenti sulla personalizzazione del cursore</span><span class="sxs-lookup"><span data-stu-id="a6570-153">Cursor customization recommendations</span></span>
<span data-ttu-id="a6570-154">Se si desidera personalizzare i comportamenti e le caratteristiche di feedback del cursore, di seguito sono riportate alcune indicazioni sulla progettazione:</span><span class="sxs-lookup"><span data-stu-id="a6570-154">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="a6570-155">Scala del cursore</span><span class="sxs-lookup"><span data-stu-id="a6570-155">Cursor scale</span></span>
* <span data-ttu-id="a6570-156">Il cursore non deve essere più grande delle destinazioni disponibili, consentendo agli utenti di interagire con facilità e di visualizzare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="a6570-156">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="a6570-157">A seconda dell'esperienza creata, il ridimensionamento del cursore mentre l'utente si trova è anche una considerazione importante.</span><span class="sxs-lookup"><span data-stu-id="a6570-157">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="a6570-158">Se, ad esempio, l'utente ha una maggiore familiarità con l'esperienza, il cursore non dovrebbe diventare troppo piccolo in modo che vada perduto.</span><span class="sxs-lookup"><span data-stu-id="a6570-158">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="a6570-159">Quando si ridimensiona il cursore, prendere in considerazione l'applicazione di un'animazione soft mentre viene ridimensionata in modo da ottenere un senso organico.</span><span class="sxs-lookup"><span data-stu-id="a6570-159">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="a6570-160">Evitare di ostacolare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="a6570-160">Avoid obstructing content.</span></span> <span data-ttu-id="a6570-161">Gli ologrammi sono gli elementi che rendono memorabile l'esperienza e il cursore non dovrebbe allontanarsi da essi.</span><span class="sxs-lookup"><span data-stu-id="a6570-161">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="a6570-162">Forma cursore direzionale</span><span class="sxs-lookup"><span data-stu-id="a6570-162">Directionless cursor shape</span></span>
* <span data-ttu-id="a6570-163">Sebbene non esista una forma di cursore a destra, è consigliabile usare una forma senza direzione come un torus.</span><span class="sxs-lookup"><span data-stu-id="a6570-163">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="a6570-164">Un cursore che punta in una direzione, ad esempio un cursore a freccia tradizionale, potrebbe confondere l'utente in modo che sia sempre simile.</span><span class="sxs-lookup"><span data-stu-id="a6570-164">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="a6570-165">Un'eccezione è rappresentata dall'utilizzo del cursore per la comunicazione dell'istruzione di interazione con l'utente.</span><span class="sxs-lookup"><span data-stu-id="a6570-165">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="a6570-166">Ad esempio, quando si ridimensionano gli ologrammi nel sistema operativo di realtà mista, il cursore include temporaneamente frecce che indicano all'utente come spostare la mano per ridimensionare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="a6570-166">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="a6570-167">Aspetto</span><span class="sxs-lookup"><span data-stu-id="a6570-167">Look and feel</span></span>
* <span data-ttu-id="a6570-168">Un cursore a forma di ciambella o Toro è adatto a una grande quantità di applicazioni.</span><span class="sxs-lookup"><span data-stu-id="a6570-168">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="a6570-169">Selezionare un colore e una forma che rappresenti al meglio l'esperienza che si sta creando.</span><span class="sxs-lookup"><span data-stu-id="a6570-169">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="a6570-170">I cursori sono particolarmente soggetti alla [separazione dei colori](hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="a6570-170">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="a6570-171">Un piccolo cursore con opacità bilanciata mantiene informativo senza dominare la gerarchia visiva.</span><span class="sxs-lookup"><span data-stu-id="a6570-171">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="a6570-172">Tenere presente che l'uso di ombre o evidenziazioni dietro il cursore potrebbe ostacolare il contenuto e distrarre dall'attività.</span><span class="sxs-lookup"><span data-stu-id="a6570-172">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="a6570-173">I cursori devono essere allineati e abbracciare le superfici nell'app, in modo da dare all'utente la sensazione che il sistema sia in grado di individuare il punto in cui stanno cercando, ma anche che il sistema sia in grado di riconoscere l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="a6570-173">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="a6570-174">Nel sistema operativo di realtà mista, ad esempio, il cursore è allineato alle superfici del mondo dell'utente, creando una sensazione di consapevolezza del mondo anche quando l'utente non guarda direttamente un ologramma.</span><span class="sxs-lookup"><span data-stu-id="a6570-174">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="a6570-175">Il blocco magnetico del cursore a un elemento interattivo quando si trova in prossimità può contribuire a migliorare la fiducia che l'utente interagirà con tale elemento quando eseguirà un'azione di selezione.</span><span class="sxs-lookup"><span data-stu-id="a6570-175">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="a6570-176">Segnali visivi</span><span class="sxs-lookup"><span data-stu-id="a6570-176">Visual cues</span></span>
* <span data-ttu-id="a6570-177">Se l'esperienza è incentrata su un solo ologramma, il cursore dovrebbe allinearsi e abbracciare solo tale ologramma e modificare la forma quando si è lontani dall'ologramma.</span><span class="sxs-lookup"><span data-stu-id="a6570-177">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="a6570-178">Ciò può comportare all'utente che l'ologramma è interoperabile e può interagire con esso.</span><span class="sxs-lookup"><span data-stu-id="a6570-178">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="a6570-179">Se l'applicazione usa il mapping spaziale, il cursore potrebbe allinearsi e abbracciare ogni superficie che vede.</span><span class="sxs-lookup"><span data-stu-id="a6570-179">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="a6570-180">In questo modo viene fornito un feedback agli utenti che HoloLens e l'applicazione possono visualizzare il proprio spazio.</span><span class="sxs-lookup"><span data-stu-id="a6570-180">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="a6570-181">Questo rafforza il fatto che gli ologrammi sono reali e in questo mondo e contribuiscono a colmare il divario tra il reale e il virtuale.</span><span class="sxs-lookup"><span data-stu-id="a6570-181">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="a6570-182">Avere un'idea di cosa deve fare il cursore quando non sono presenti ologrammi o superfici in visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a6570-182">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="a6570-183">Il posizionamento a una distanza predeterminata davanti all'utente è un'opzione.</span><span class="sxs-lookup"><span data-stu-id="a6570-183">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="a6570-184">Azioni possibili</span><span class="sxs-lookup"><span data-stu-id="a6570-184">Possible actions</span></span>
* <span data-ttu-id="a6570-185">Il cursore può essere rappresentato da icone diverse per indicare le possibili azioni che possono essere eseguite da un ologramma, ad esempio il ridimensionamento o la rotazione.</span><span class="sxs-lookup"><span data-stu-id="a6570-185">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="a6570-186">Aggiungere al cursore informazioni aggiuntive solo se significa qualcosa per l'utente.</span><span class="sxs-lookup"><span data-stu-id="a6570-186">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="a6570-187">In caso contrario, gli utenti potrebbero non osservare le modifiche dello stato o essere confuse dal cursore.</span><span class="sxs-lookup"><span data-stu-id="a6570-187">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="a6570-188">Stato input</span><span class="sxs-lookup"><span data-stu-id="a6570-188">Input state</span></span>
* <span data-ttu-id="a6570-189">È possibile utilizzare il cursore per visualizzare lo stato o la finalità di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a6570-189">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="a6570-190">Ad esempio, è possibile visualizzare un'icona che informa l'utente che il sistema rileva lo stato della mano e che l'applicazione sa che è pronto a intervenire.</span><span class="sxs-lookup"><span data-stu-id="a6570-190">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="a6570-191">È anche possibile usare il cursore per mostrare agli utenti che i comandi vocali sono stati uditi dal sistema tramite un colore momentaneo Chang</span><span class="sxs-lookup"><span data-stu-id="a6570-191">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="a6570-192">Gli Stati del cursore seguenti possono essere implementati in modi diversi.</span><span class="sxs-lookup"><span data-stu-id="a6570-192">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="a6570-193">È possibile implementare questi stati diversi modellando il cursore come una macchina a Stati.</span><span class="sxs-lookup"><span data-stu-id="a6570-193">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="a6570-194">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="a6570-194">For example:</span></span>
    * <span data-ttu-id="a6570-195">Lo stato di inattività è il punto in cui viene visualizzato il cursore predefinito.</span><span class="sxs-lookup"><span data-stu-id="a6570-195">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="a6570-196">Lo stato pronto è quando è stata rilevata la mano dell'utente nella posizione pronta.</span><span class="sxs-lookup"><span data-stu-id="a6570-196">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="a6570-197">Lo stato di interazione è quando l'utente sta eseguendo una particolare interazione.</span><span class="sxs-lookup"><span data-stu-id="a6570-197">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="a6570-198">Lo stato delle azioni possibili o il passaggio del mouse è quando si conferiscono azioni possibili che possono essere eseguite su un ologramma.</span><span class="sxs-lookup"><span data-stu-id="a6570-198">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="a6570-199">È anche possibile implementare questi stati in modo che sia possibile visualizzare risorse dell'arte diverse quando vengono rilevati stati diversi.</span><span class="sxs-lookup"><span data-stu-id="a6570-199">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="a6570-200">"Senza cursore"</span><span class="sxs-lookup"><span data-stu-id="a6570-200">Going "cursor-free"</span></span>
<span data-ttu-id="a6570-201">La progettazione senza cursore è consigliata quando il senso di immersione è un componente chiave di un'esperienza e quando si puntano interazioni (tramite sguardo e movimento) non è necessaria una precisione notevole.</span><span class="sxs-lookup"><span data-stu-id="a6570-201">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="a6570-202">Il sistema deve comunque soddisfare le esigenze normalmente soddisfatte da un cursore fornendo agli utenti un feedback continuo sulla comprensione del sistema e aiutandoli a comunicare in modo sicuro le proprie intenzioni al sistema.</span><span class="sxs-lookup"><span data-stu-id="a6570-202">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="a6570-203">Questo può essere raggiungibile attraverso altre modifiche di stato evidenti.</span><span class="sxs-lookup"><span data-stu-id="a6570-203">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="a6570-204">Cursore in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="a6570-204">Cursor in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="a6570-205">Per impostazione predefinita, **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce una precostruzione del cursore ([DefaultCursor. prefabbricate](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) che ha lo stesso stato di visualizzazione del cursore di sistema della shell.</span><span class="sxs-lookup"><span data-stu-id="a6570-205">By default, **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="a6570-206">Viene assegnato nel profilo di input di MRTK in puntatori.</span><span class="sxs-lookup"><span data-stu-id="a6570-206">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="a6570-207">È possibile sostituire o personalizzare questo cursore per la propria esperienza.</span><span class="sxs-lookup"><span data-stu-id="a6570-207">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="a6570-208">Per l'esperienza con l'input di rilevamento degli occhi, MRTK fornisce anche EyeGazeCursor con un oggetto visivo sottile per ridurre al minimo la distrazione.</span><span class="sxs-lookup"><span data-stu-id="a6570-208">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="a6570-209">MRTK-profilo puntatore</span><span class="sxs-lookup"><span data-stu-id="a6570-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="a6570-210">MRTK-sistema di input</span><span class="sxs-lookup"><span data-stu-id="a6570-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="a6570-211">MRTK-puntatori</span><span class="sxs-lookup"><span data-stu-id="a6570-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="a6570-212">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a6570-212">See also</span></span>
* [<span data-ttu-id="a6570-213">Movimenti</span><span class="sxs-lookup"><span data-stu-id="a6570-213">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a6570-214">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="a6570-214">Head-gaze and commit</span></span>](gaze-and-commit.md)
