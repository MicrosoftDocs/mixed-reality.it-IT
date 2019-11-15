---
title: Input vocale
description: L'input vocale è un input di base per HoloLens e per le cuffie immersive in realtà mista di Windows. La voce può essere usata per i comandi, la dettatura, il Cortana e altro ancora.
author: Hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, input
ms.openlocfilehash: 7264b0b8882928f64860bc5a30b97683306cb19c
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105775"
---
# <a name="voice-input"></a><span data-ttu-id="68c95-105">Input vocale</span><span class="sxs-lookup"><span data-stu-id="68c95-105">Voice input</span></span>

![Input vocale](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="68c95-107">La voce è una delle forme di input chiave per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="68c95-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="68c95-108">Consente di eseguire direttamente il comando di un ologramma senza dover usare i [movimenti di mano](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="68c95-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="68c95-109">L'input vocale può essere un modo naturale di comunicare le intenzioni.</span><span class="sxs-lookup"><span data-stu-id="68c95-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="68c95-110">La voce è particolarmente utile per attraversare interfacce complesse, perché consente agli utenti di tagliare i menu nidificati con un unico comando.</span><span class="sxs-lookup"><span data-stu-id="68c95-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="68c95-111">L'input vocale è alimentato dallo [stesso motore](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) che supporta la sintesi vocale in tutte le altre _app di Windows universale_.</span><span class="sxs-lookup"><span data-stu-id="68c95-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="68c95-112">In HoloLens il riconoscimento vocale funzionerà sempre nella lingua di visualizzazione di Windows configurata in impostazioni.</span><span class="sxs-lookup"><span data-stu-id="68c95-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="68c95-113">Voice and sguardi</span><span class="sxs-lookup"><span data-stu-id="68c95-113">Voice and gaze</span></span>

<span data-ttu-id="68c95-114">Quando si usano i comandi vocali, lo sguardo (Head o Eye) viene in genere usato come meccanismo di destinazione, con un cursore ("Select") o con il canale implicito del comando a un'applicazione che si sta esaminando.</span><span class="sxs-lookup"><span data-stu-id="68c95-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="68c95-115">A tale proposito, potrebbe non essere necessario visualizzare alcun cursore _("vedere, pronunciare")_ .</span><span class="sxs-lookup"><span data-stu-id="68c95-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="68c95-116">Naturalmente, alcuni comandi vocali non richiedono una destinazione, ad esempio "go to Start" o "Hey Cortana".</span><span class="sxs-lookup"><span data-stu-id="68c95-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="68c95-117">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="68c95-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="68c95-118"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="68c95-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="68c95-119"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="68c95-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="68c95-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="68c95-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="68c95-121"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="68c95-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="68c95-122">Input vocale</span><span class="sxs-lookup"><span data-stu-id="68c95-122">Voice input</span></span></td>
        <td><span data-ttu-id="68c95-123">✔️</span><span class="sxs-lookup"><span data-stu-id="68c95-123">✔️</span></span></td>
        <td><span data-ttu-id="68c95-124">✔️</span><span class="sxs-lookup"><span data-stu-id="68c95-124">✔️</span></span></td>
        <td><span data-ttu-id="68c95-125">✔️ (con microfono)</span><span class="sxs-lookup"><span data-stu-id="68c95-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="68c95-126">Comando "Select"</span><span class="sxs-lookup"><span data-stu-id="68c95-126">The "select" command</span></span>

<span data-ttu-id="68c95-127">**HoloLens (prima generazione)**</span><span class="sxs-lookup"><span data-stu-id="68c95-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="68c95-128">Anche senza aggiungere in modo specifico il supporto vocale all'app, gli utenti possono attivare gli ologrammi semplicemente pronunciando il comando "Select" del comando "System Voice".</span><span class="sxs-lookup"><span data-stu-id="68c95-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="68c95-129">Questo comportamento è identico a quello di un [rubinetto d'aria](gaze-and-commit.md#composite-gestures) su HoloLens, facendo clic sul pulsante Seleziona nel [HoloLens clic](hardware-accessories.md#hololens-clicker)oppure premendo il trigger in un [controller di movimento della realtà mista di Windows](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="68c95-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="68c95-130">Verrà visualizzato un suono e verrà visualizzata una descrizione comando con "Select" come conferma.</span><span class="sxs-lookup"><span data-stu-id="68c95-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="68c95-131">"Select" è abilitato da un algoritmo di rilevamento di parole chiave a basso consumo, in modo che sia sempre disponibile per l'utente in qualsiasi momento con un minimo di durata della batteria, anche con le tue mani.</span><span class="sxs-lookup"><span data-stu-id="68c95-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="68c95-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="68c95-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="68c95-133">Per usare il comando voce "Select" in HoloLens 2, è necessario prima di tutto visualizzare il cursore di sguardi da usare come puntatore.</span><span class="sxs-lookup"><span data-stu-id="68c95-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="68c95-134">Il comando per riportarlo è facile da ricordare, ovvero "Select".</span><span class="sxs-lookup"><span data-stu-id="68c95-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="68c95-135">Per uscire dalla modalità, è sufficiente usare di nuovo le mani per toccare l'aria, avvicinarsi a un pulsante con le dita o usare il gesto del sistema.</span><span class="sxs-lookup"><span data-stu-id="68c95-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="68c95-136">*Image: pronunciare "Select" per utilizzare il comando Voice per la selezione*</span><span class="sxs-lookup"><span data-stu-id="68c95-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Un utente può pronunciare "Select" per usare il comando Voice per una selezione.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="68c95-138">Ehi Cortana</span><span class="sxs-lookup"><span data-stu-id="68c95-138">Hey Cortana</span></span>

<span data-ttu-id="68c95-139">È anche possibile pronunciare "Hey Cortana" per visualizzare Cortana in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="68c95-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="68c95-140">Non è necessario attendere che venga visualizzata per continuare a porre una domanda o fornire un'istruzione, ad esempio, provare a pronunciare "Hey Cortana, qual è il meteo?"</span><span class="sxs-lookup"><span data-stu-id="68c95-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="68c95-141">come singola frase.</span><span class="sxs-lookup"><span data-stu-id="68c95-141">as a single sentence.</span></span> <span data-ttu-id="68c95-142">Per ulteriori informazioni su Cortana e sulle operazioni che è possibile eseguire, è sufficiente chiederle!</span><span class="sxs-lookup"><span data-stu-id="68c95-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="68c95-143">Pronunciare "Hey Cortana, cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="68c95-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="68c95-144">verrà quindi eseguito il pull di un elenco di comandi funzionanti e consigliati.</span><span class="sxs-lookup"><span data-stu-id="68c95-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="68c95-145">Se si è già nell'app Cortana, è anche possibile fare clic sul pulsante **?**</span><span class="sxs-lookup"><span data-stu-id="68c95-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="68c95-146">icona sulla barra laterale per estrarre lo stesso menu.</span><span class="sxs-lookup"><span data-stu-id="68c95-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="68c95-147">**Comandi specifici di HoloLens**</span><span class="sxs-lookup"><span data-stu-id="68c95-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="68c95-148">"Cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="68c95-148">"What can I say?"</span></span>
* <span data-ttu-id="68c95-149">"Vai a avvio"-anziché [Bloom](system-gesture.md#bloom) per visualizzare il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="68c95-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="68c95-150">"Avvia <app>"</span><span class="sxs-lookup"><span data-stu-id="68c95-150">"Launch <app>"</span></span>
* <span data-ttu-id="68c95-151">"Sposta <app> qui"</span><span class="sxs-lookup"><span data-stu-id="68c95-151">"Move <app> here"</span></span>
* <span data-ttu-id="68c95-152">"Scattare un'immagine"</span><span class="sxs-lookup"><span data-stu-id="68c95-152">"Take a picture"</span></span>
* <span data-ttu-id="68c95-153">"Avvia registrazione"</span><span class="sxs-lookup"><span data-stu-id="68c95-153">"Start recording"</span></span>
* <span data-ttu-id="68c95-154">"Arresta registrazione"</span><span class="sxs-lookup"><span data-stu-id="68c95-154">"Stop recording"</span></span>
* <span data-ttu-id="68c95-155">"Aumentare la luminosità"</span><span class="sxs-lookup"><span data-stu-id="68c95-155">"Increase the brightness"</span></span>
* <span data-ttu-id="68c95-156">"Riduzione della luminosità"</span><span class="sxs-lookup"><span data-stu-id="68c95-156">"Decrease the brightness"</span></span>
* <span data-ttu-id="68c95-157">"Aumento del volume"</span><span class="sxs-lookup"><span data-stu-id="68c95-157">"Increase the volume"</span></span>
* <span data-ttu-id="68c95-158">"Diminuisci volume"</span><span class="sxs-lookup"><span data-stu-id="68c95-158">"Decrease the volume"</span></span>
* <span data-ttu-id="68c95-159">"Mute" o "unmute"</span><span class="sxs-lookup"><span data-stu-id="68c95-159">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="68c95-160">"Arresta il dispositivo"</span><span class="sxs-lookup"><span data-stu-id="68c95-160">"Shut down the device"</span></span>
* <span data-ttu-id="68c95-161">"Riavvia il dispositivo"</span><span class="sxs-lookup"><span data-stu-id="68c95-161">"Restart the device"</span></span>
* <span data-ttu-id="68c95-162">"Vai a sospensione"</span><span class="sxs-lookup"><span data-stu-id="68c95-162">"Go to sleep"</span></span>
* <span data-ttu-id="68c95-163">"Qual è il tempo?"</span><span class="sxs-lookup"><span data-stu-id="68c95-163">"What time is it?"</span></span>
* <span data-ttu-id="68c95-164">"Quanta batteria è rimasta?"</span><span class="sxs-lookup"><span data-stu-id="68c95-164">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="68c95-165">"Vedere la voce"</span><span class="sxs-lookup"><span data-stu-id="68c95-165">"See It, Say It"</span></span><br>
        <span data-ttu-id="68c95-166">HoloLens dispone di un modello "See it, Say it" per l'input vocale, in cui le etichette sui pulsanti indicano agli utenti i comandi vocali che possono dire.</span><span class="sxs-lookup"><span data-stu-id="68c95-166">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="68c95-167">Ad esempio, quando si esamina una finestra dell'app in HoloLens (1st Gen), un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app nel mondo.</span><span class="sxs-lookup"><span data-stu-id="68c95-167">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="68c95-168">*Image: un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app*</span><span class="sxs-lookup"><span data-stu-id="68c95-168">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68c95-169">spazio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68c95-169">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="68c95-170">![quando si esamina una finestra o un ologramma dell'app, un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app nel mondo](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="68c95-170">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="68c95-171">Quando le app seguono questa regola, gli utenti possono comprendere facilmente cosa dire per controllare il sistema.</span><span class="sxs-lookup"><span data-stu-id="68c95-171">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="68c95-172">Per rinforzare questo problema, guardando un pulsante in HoloLens (1st Gen), viene visualizzata una descrizione comando "Voice Rest" che viene visualizzata dopo un secondo se il pulsante è abilitato per la voce e visualizza il comando per parlare con "premere".</span><span class="sxs-lookup"><span data-stu-id="68c95-172">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="68c95-173">Per rivelare le descrizioni comandi vocali in HoloLens 2, visualizzare il cursore vocale digitando "Select" o "What Can Say" (vedere l'immagine).</span><span class="sxs-lookup"><span data-stu-id="68c95-173">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="68c95-174">*Image: i comandi "See it, Say it" vengono visualizzati sotto i pulsanti*</span><span class="sxs-lookup"><span data-stu-id="68c95-174">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Vedere i comandi visualizzati sotto i pulsanti](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="68c95-176">Comandi vocali per la manipolazione rapida degli ologrammi</span><span class="sxs-lookup"><span data-stu-id="68c95-176">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="68c95-177">Per eseguire rapidamente le attività di manipolazione, è possibile pronunciare un certo numero di comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="68c95-177">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="68c95-178">Questi comandi vocali funzionano nelle finestre delle app e negli oggetti 3D che sono stati inseriti nel mondo.</span><span class="sxs-lookup"><span data-stu-id="68c95-178">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="68c95-179">**Comandi di manipolazione ologramma**</span><span class="sxs-lookup"><span data-stu-id="68c95-179">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="68c95-180">Mi faccia</span><span class="sxs-lookup"><span data-stu-id="68c95-180">Face me</span></span>
* <span data-ttu-id="68c95-181">Più grande | Migliorare</span><span class="sxs-lookup"><span data-stu-id="68c95-181">Bigger | Enhance</span></span>
* <span data-ttu-id="68c95-182">Più piccoli</span><span class="sxs-lookup"><span data-stu-id="68c95-182">Smaller</span></span>

<span data-ttu-id="68c95-183">In HoloLens 2 è anche possibile creare interazioni più naturali insieme a Eye-sguardi che fornisce in modo implicito informazioni contestuali sugli elementi a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="68c95-183">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="68c95-184">Ad esempio, è possibile esaminare semplicemente un ologramma e pronunciare _il_punto in cui si vuole posizionarlo e pronunciare " _qui_".</span><span class="sxs-lookup"><span data-stu-id="68c95-184">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="68c95-185">In alternativa, è possibile esaminare una parte olografica in un computer complesso e pronunciare: "fornire ulteriori informazioni su _questo_".</span><span class="sxs-lookup"><span data-stu-id="68c95-185">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="68c95-186">Individuazione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="68c95-186">Discovering voice commands</span></span>

<span data-ttu-id="68c95-187">Alcuni comandi, ad esempio i comandi per una manipolazione rapida precedente, possono essere nascosti.</span><span class="sxs-lookup"><span data-stu-id="68c95-187">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="68c95-188">Per informazioni sui comandi che è possibile usare, osservare un oggetto e pronunciare "cosa si può dire?".</span><span class="sxs-lookup"><span data-stu-id="68c95-188">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="68c95-189">Viene visualizzato un elenco di comandi possibili.</span><span class="sxs-lookup"><span data-stu-id="68c95-189">A list of possible commands pops up.</span></span> <span data-ttu-id="68c95-190">È anche possibile usare il cursore Head sguardi per individuare e visualizzare le descrizioni comandi vocali per ogni pulsante davanti all'utente.</span><span class="sxs-lookup"><span data-stu-id="68c95-190">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="68c95-191">Se si desidera un elenco completo, è sufficiente indicare "Mostra tutti i comandi" in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="68c95-191">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="68c95-192">Dettatura</span><span class="sxs-lookup"><span data-stu-id="68c95-192">Dictation</span></span>

<span data-ttu-id="68c95-193">Invece di digitare con le scelte [aeree](gaze-and-commit.md#composite-gestures), la dettatura vocale può essere più efficiente per inserire il testo in un'app.</span><span class="sxs-lookup"><span data-stu-id="68c95-193">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="68c95-194">Questo può accelerare significativamente l'input con minore impegno per l'utente.</span><span class="sxs-lookup"><span data-stu-id="68c95-194">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="68c95-195">![la dettatura vocale inizia selezionando il pulsante del microfono](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="68c95-195">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="68c95-196">*La dettatura vocale inizia selezionando il pulsante del microfono sulla tastiera*</span><span class="sxs-lookup"><span data-stu-id="68c95-196">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="68c95-197">Ogni volta che la tastiera olografica è attiva, è possibile passare alla modalità di dettatura anziché alla digitazione.</span><span class="sxs-lookup"><span data-stu-id="68c95-197">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="68c95-198">Per iniziare, selezionare il microfono sul lato della casella input di testo.</span><span class="sxs-lookup"><span data-stu-id="68c95-198">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="68c95-199">Aggiunta di comandi vocali all'app</span><span class="sxs-lookup"><span data-stu-id="68c95-199">Adding voice commands to your app</span></span>

<span data-ttu-id="68c95-200">Valuta l'opportunità di aggiungere comandi vocali a un'esperienza che stai creando.</span><span class="sxs-lookup"><span data-stu-id="68c95-200">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="68c95-201">La voce è un modo pratico e potente di controllare il sistema e le app.</span><span class="sxs-lookup"><span data-stu-id="68c95-201">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="68c95-202">Poiché gli utenti parlano con un'ampia gamma di dialetti e accenti, la scelta appropriata delle parole chiave di contenuti vocali garantirà un'interpretazione non ambigua dei comandi degli utenti.</span><span class="sxs-lookup"><span data-stu-id="68c95-202">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="68c95-203">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="68c95-203">Best practices</span></span>

<span data-ttu-id="68c95-204">Di seguito vengono illustrate alcune procedure che semplificheranno il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="68c95-204">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="68c95-205">**Usa comandi concisi**. Quando possibile, scegli parole chiave di due o più sillabe.</span><span class="sxs-lookup"><span data-stu-id="68c95-205">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="68c95-206">Le parole di una sillaba tendono a usare suoni di vocali differenti se pronunciate da persone con accenti diversi.</span><span class="sxs-lookup"><span data-stu-id="68c95-206">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="68c95-207">Esempio: "riprodurre video" è migliore di "riprodurre il video attualmente selezionato"</span><span class="sxs-lookup"><span data-stu-id="68c95-207">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="68c95-208">**Usare un vocabolario semplice** , ad esempio: "show note" è migliore di "Show manifest"</span><span class="sxs-lookup"><span data-stu-id="68c95-208">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="68c95-209">**Assicurati che i comandi non siano distruttivi**. Verifica che tutte le azioni eseguibili con un comando vocale siano di tipo non distruttivo e possano essere annullate facilmente qualora un'altra persona che parla vicino all'utente attivi accidentalmente un comando.</span><span class="sxs-lookup"><span data-stu-id="68c95-209">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="68c95-210">**Evita comandi con suoni simili**. Non registrare più comandi vocali con suoni molto simili.</span><span class="sxs-lookup"><span data-stu-id="68c95-210">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="68c95-211">Esempio: "Mostra più" e "Mostra archivio" può essere un suono molto simile.</span><span class="sxs-lookup"><span data-stu-id="68c95-211">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="68c95-212">**Annulla la registrazione dell'app quando non è in uso**. Quando l'app non è in uno stato in cui sia valido un comando vocale specifico, è consigliabile annullarne la registrazione in modo da evitare confusione tra i comandi.</span><span class="sxs-lookup"><span data-stu-id="68c95-212">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="68c95-213">**Esegui test con accenti diversi**. Testa l'app con utenti con accenti diversi.</span><span class="sxs-lookup"><span data-stu-id="68c95-213">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="68c95-214">**Mantieni la coerenza dei comandi vocali**. Se "Indietro" porta alla pagina precedente, mantieni questo comportamento nelle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="68c95-214">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="68c95-215">**Evita di usare i comandi di sistema**. I comandi vocali seguenti sono riservati per il sistema.</span><span class="sxs-lookup"><span data-stu-id="68c95-215">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="68c95-216">Non devono essere usati dalle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="68c95-216">These should not be used by applications.</span></span>
   * <span data-ttu-id="68c95-217">"Ehi Cortana"</span><span class="sxs-lookup"><span data-stu-id="68c95-217">"Hey Cortana"</span></span>
   * <span data-ttu-id="68c95-218">"Seleziona"</span><span class="sxs-lookup"><span data-stu-id="68c95-218">"Select"</span></span>
   * <span data-ttu-id="68c95-219">"Vai all'avvio"</span><span class="sxs-lookup"><span data-stu-id="68c95-219">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="68c95-220">Vantaggi dell'input vocale</span><span class="sxs-lookup"><span data-stu-id="68c95-220">Advantages of voice input</span></span>

<span data-ttu-id="68c95-221">L'input vocale è un modo naturale di comunicare le intenzioni.</span><span class="sxs-lookup"><span data-stu-id="68c95-221">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="68c95-222">La voce è particolarmente utile negli **attraversamenti** dell'interfaccia perché può aiutare gli utenti a tagliare più passaggi di un'interfaccia (un utente potrebbe "tornare indietro" guardando una pagina Web, anziché dover passare al pulsante indietro nell'app).</span><span class="sxs-lookup"><span data-stu-id="68c95-222">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="68c95-223">Questo piccolo risparmio di tempo ha un forte **effetto emotivo** sulla percezione dell'esperienza dell'utente e offre una piccola superpotenza.</span><span class="sxs-lookup"><span data-stu-id="68c95-223">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="68c95-224">I comandi vocali rappresentano anche un pratico metodo di input quando hai le mani occupate oppure quando sei in modalità **multitasking**.</span><span class="sxs-lookup"><span data-stu-id="68c95-224">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="68c95-225">Nei dispositivi in cui la digitazione su una tastiera è difficile, la **Dettatura vocale** può essere un metodo alternativo efficace per inserire il testo.</span><span class="sxs-lookup"><span data-stu-id="68c95-225">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="68c95-226">Infine, in alcuni casi, quando l' **intervallo di accuratezza** per lo sguardo e il movimento sono limitati, Voice può contribuire a evitare ambiguità tra le finalità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="68c95-226">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="68c95-227">**In che modo i comandi vocali possono rivelarsi utili per l'utente**</span><span class="sxs-lookup"><span data-stu-id="68c95-227">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="68c95-228">Riducono i tempi: devono rendere l'obiettivo finale più efficiente.</span><span class="sxs-lookup"><span data-stu-id="68c95-228">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="68c95-229">Riducono al minimo lo sforzo: devono rendere le attività più fluide e semplici.</span><span class="sxs-lookup"><span data-stu-id="68c95-229">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="68c95-230">Riducono il carico cognitivo: sono intuitivi e facili da imparare e ricordare.</span><span class="sxs-lookup"><span data-stu-id="68c95-230">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="68c95-231">Sono socialmente accettabili: devono essere conformi alle regole della società in termini di comportamento.</span><span class="sxs-lookup"><span data-stu-id="68c95-231">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="68c95-232">Rappresentano la routine: i comandi vocali possono facilmente diventare un comportamento abituale.</span><span class="sxs-lookup"><span data-stu-id="68c95-232">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="68c95-233">Problemi per l'input vocale</span><span class="sxs-lookup"><span data-stu-id="68c95-233">Challenges for voice input</span></span>

<span data-ttu-id="68c95-234">Anche se l'input vocale è ideale per molte applicazioni diverse, presenta anche diverse problemi.</span><span class="sxs-lookup"><span data-stu-id="68c95-234">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="68c95-235">Comprendere i vantaggi e le esigenze per l'input vocale consente agli sviluppatori di app di prendere scelte più intelligenti per sapere come e quando usare l'input vocale e per creare un'esperienza ottimale per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="68c95-235">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="68c95-236">**Input vocale per il controllo di input continuo** Il controllo con granularità fine è uno di essi.</span><span class="sxs-lookup"><span data-stu-id="68c95-236">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="68c95-237">Ad esempio, un utente potrebbe voler modificare il volume nella propria app musicale.</span><span class="sxs-lookup"><span data-stu-id="68c95-237">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="68c95-238">Può semplicemente dire "più forte", ma non è chiaro quanto sia forte il sistema a creare il volume.</span><span class="sxs-lookup"><span data-stu-id="68c95-238">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="68c95-239">L'utente può affermare: "renderlo un po' più forte", ma è difficile quantificare "un po'".</span><span class="sxs-lookup"><span data-stu-id="68c95-239">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="68c95-240">Lo stato di scalabilità o di ridimensionamento degli ologrammi con la voce è simile.</span><span class="sxs-lookup"><span data-stu-id="68c95-240">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="68c95-241">**Affidabilità del rilevamento dell'input vocale** Sebbene i sistemi di input vocali siano migliori e migliori, a volte potrebbero non essere in grado di ascoltare e interpretare un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="68c95-241">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="68c95-242">La chiave consiste nel risolvere questo problema nell'applicazione fornendo commenti e suggerimenti all'utente quando il sistema è in ascolto e ciò che il sistema ha compreso per creare chiarezza sui potenziali problemi nella comprensione corretta dell'utente.</span><span class="sxs-lookup"><span data-stu-id="68c95-242">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="68c95-243">**Input vocale negli spazi condivisi** La voce potrebbe non essere socialmente accettabile negli spazi condivisi con altri utenti.</span><span class="sxs-lookup"><span data-stu-id="68c95-243">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="68c95-244">Ecco alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="68c95-244">Here are a few examples:</span></span>
* <span data-ttu-id="68c95-245">L'utente potrebbe non voler disturbare altri, ad esempio in una libreria interattiva o in una sede condivisa</span><span class="sxs-lookup"><span data-stu-id="68c95-245">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="68c95-246">Gli utenti potrebbero sembrare imbarazzanti,</span><span class="sxs-lookup"><span data-stu-id="68c95-246">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="68c95-247">Un utente potrebbe non essere scomodo a indicare un messaggio personale o riservato (incluse le password) mentre altri sono in ascolto</span><span class="sxs-lookup"><span data-stu-id="68c95-247">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="68c95-248">**Input vocale di parole univoche o sconosciute** Le difficoltà per l'input vocale si verificano anche quando gli utenti definiscono parole che potrebbero essere sconosciute al sistema, ad esempio i nomi alternativi, alcune parole o abbreviazioni gergali.</span><span class="sxs-lookup"><span data-stu-id="68c95-248">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="68c95-249">**Apprendimento di comandi vocali** Anche se l'obiettivo finale è quello di comunicare naturalmente con il sistema, spesso le app si basano su comandi vocali predefiniti specifici.</span><span class="sxs-lookup"><span data-stu-id="68c95-249">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="68c95-250">Un problema associato a una grande serie di comandi vocali è come insegnarli senza sovraccaricare l'utente e come aiutarli a conservarli.</span><span class="sxs-lookup"><span data-stu-id="68c95-250">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="68c95-251">Stati di feedback dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="68c95-251">Voice feedback states</span></span>

<span data-ttu-id="68c95-252">Quando i comandi vocali vengono applicati in modo corretto, l'utente capisce **cosa può dire e ottiene un feedback chiaro** a indicare che il sistema ha **recepito correttamente i comandi**.</span><span class="sxs-lookup"><span data-stu-id="68c95-252">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="68c95-253">Questi due segnali fanno sì che l'utente si senta sicuro di usare i comandi vocali come input principale.</span><span class="sxs-lookup"><span data-stu-id="68c95-253">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="68c95-254">Di seguito è riportato un diagramma che illustra che cosa accade al cursore quando l'input vocale viene riconosciuto e come tale risultato viene comunicato all'utente.</span><span class="sxs-lookup"><span data-stu-id="68c95-254">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="68c95-255">![1.](images/voicefeedbackstates-regular.jpg) dello stato del cursore regolare</span><span class="sxs-lookup"><span data-stu-id="68c95-255">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="68c95-256">**1. stato del cursore normale**</span><span class="sxs-lookup"><span data-stu-id="68c95-256">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="68c95-257">![2. Comunica il feedback vocale e scompare](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="68c95-257">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="68c95-258">**2. comunica il feedback vocale e scompare**</span><span class="sxs-lookup"><span data-stu-id="68c95-258">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="68c95-259">![\* 3.</span><span class="sxs-lookup"><span data-stu-id="68c95-259">![\*3.</span></span> <span data-ttu-id="68c95-260">](images/voicefeedbackstates-regular.jpg) dello stato del cursore regolare</span><span class="sxs-lookup"><span data-stu-id="68c95-260">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="68c95-261">**3. torna allo stato normale del cursore**</span><span class="sxs-lookup"><span data-stu-id="68c95-261">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="68c95-262">Nozioni di base sui comandi vocali che gli utenti devono conoscere per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="68c95-262">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="68c95-263">Pronuncia **"Seleziona"** quando la destinazione è un pulsante. Puoi usare questo comando ovunque per fare clic su un pulsante.</span><span class="sxs-lookup"><span data-stu-id="68c95-263">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="68c95-264">Puoi pronunciare il **nome dell'etichetta di un pulsante della barra dell'app** in alcune app per eseguire un'azione.</span><span class="sxs-lookup"><span data-stu-id="68c95-264">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="68c95-265">Mentre guarda un'app, ad esempio, un utente può pronunciare il comando "Rimuovi" per rimuovere definitivamente l'app, senza dover fare clic su di essa con la mano e risparmiando così tempo.</span><span class="sxs-lookup"><span data-stu-id="68c95-265">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="68c95-266">Puoi avviare l'ascolto da parte di Cortana dicendo **"Ehi Cortana"** .</span><span class="sxs-lookup"><span data-stu-id="68c95-266">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="68c95-267">Puoi porre domande ("Ehi Cortana, quanto è alta la Torre Eiffel?"), chiedere di aprire un'app ("Ehi Cortana, apri Netflix") o chiedere di visualizzare il menu di avvio ("Ehi Cortana, portami all'inizio") e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="68c95-267">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="68c95-268">Domande e dubbi comuni degli utenti sui comandi vocali</span><span class="sxs-lookup"><span data-stu-id="68c95-268">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="68c95-269">Cosa posso dire?</span><span class="sxs-lookup"><span data-stu-id="68c95-269">What can I say?</span></span>
* <span data-ttu-id="68c95-270">Come posso sapere se il sistema mi ha capito correttamente?</span><span class="sxs-lookup"><span data-stu-id="68c95-270">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="68c95-271">Il sistema continua a interpretare i miei comandi vocali in modo errato.</span><span class="sxs-lookup"><span data-stu-id="68c95-271">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="68c95-272">Non reagisce quando pronuncio un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="68c95-272">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="68c95-273">Reagisce in modo non corretto quando pronuncio un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="68c95-273">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="68c95-274">Come posso indirizzare un comando vocale a una specifica app o un comando di app?</span><span class="sxs-lookup"><span data-stu-id="68c95-274">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="68c95-275">Posso usare i comandi vocali per operazioni all'esterno del fotogramma olografico di HoloLens?</span><span class="sxs-lookup"><span data-stu-id="68c95-275">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="68c95-276">Comunicazione</span><span class="sxs-lookup"><span data-stu-id="68c95-276">Communication</span></span>

<span data-ttu-id="68c95-277">Per le applicazioni che vogliono sfruttare le opzioni di elaborazione dell'input audio personalizzato fornite da HoloLens, è importante comprendere le diverse categorie di [flussi audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) che l'app può utilizzare.</span><span class="sxs-lookup"><span data-stu-id="68c95-277">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="68c95-278">Windows 10 supporta diverse categorie di flusso e HoloLens ne usa tre per consentire l'elaborazione personalizzata per ottimizzare la qualità audio del microfono personalizzata per la comunicazione vocale, la comunicazione e altro che può essere usata per l'audio dell'ambiente di ambiente scenari di acquisizione, ad esempio "videocamera".</span><span class="sxs-lookup"><span data-stu-id="68c95-278">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="68c95-279">La categoria AudioCategory_Communications Stream è personalizzata per gli scenari di qualità della chiamata e di narrazione e fornisce al client un flusso audio mono 16kHz 24bit della voce dell'utente</span><span class="sxs-lookup"><span data-stu-id="68c95-279">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="68c95-280">La categoria AudioCategory_Speech Stream è personalizzata per il motore di riconoscimento vocale HoloLens (Windows) e fornisce un flusso di 16kHz 24bit mono della voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="68c95-280">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="68c95-281">Questa categoria può essere usata dai motori di sintesi vocale di terze parti, se necessario.</span><span class="sxs-lookup"><span data-stu-id="68c95-281">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="68c95-282">La categoria AudioCategory_Other Stream è personalizzata per la registrazione audio dell'ambiente di ambiente e fornisce al client un flusso audio stereo a 24 bit a 48 bit.</span><span class="sxs-lookup"><span data-stu-id="68c95-282">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="68c95-283">Questa elaborazione audio è accelerata dall'hardware, il che significa che le funzionalità svuotano molto meno energia rispetto a quando la stessa elaborazione è stata eseguita sulla CPU HoloLens.</span><span class="sxs-lookup"><span data-stu-id="68c95-283">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="68c95-284">Evitare di eseguire altre elaborazioni di input audio sulla CPU per ottimizzare la durata della batteria del sistema e sfruttare i vantaggi dell'elaborazione dell'input audio con offload incorporato.</span><span class="sxs-lookup"><span data-stu-id="68c95-284">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="68c95-285">Lingue</span><span class="sxs-lookup"><span data-stu-id="68c95-285">Languages</span></span>

<span data-ttu-id="68c95-286">HoloLens 2 supporta inoltre lingue aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="68c95-286">HoloLens 2 also supports additional languages.</span></span> <span data-ttu-id="68c95-287">Tenere presente che i comandi vocali verranno sempre eseguiti nella lingua di visualizzazione del sistema anche se sono installate più tastiere o se le app tentano di creare un riconoscimento vocale in una lingua diversa.</span><span class="sxs-lookup"><span data-stu-id="68c95-287">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="68c95-288">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="68c95-288">Troubleshooting</span></span>

<span data-ttu-id="68c95-289">Se si verificano problemi con "Select" e "Hey Cortana", provare a passare a uno spazio più silenzioso, a disattivarsi dall'origine del rumore o a una voce più forte.</span><span class="sxs-lookup"><span data-stu-id="68c95-289">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="68c95-290">A questo punto, tutto il riconoscimento vocale in HoloLens viene ottimizzato e ottimizzato in modo specifico per gli altoparlanti nativi di Stati Uniti inglese.</span><span class="sxs-lookup"><span data-stu-id="68c95-290">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="68c95-291">Per la versione 2017 di Windows Mixed Reality Developer Edition, la logica di gestione degli endpoint audio funzionerà correttamente (per sempre) dopo la disconnessione e l'accesso al desktop del PC dopo la connessione iniziale di HMD.</span><span class="sxs-lookup"><span data-stu-id="68c95-291">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="68c95-292">Prima della prima disconnessione o dell'evento, dopo aver attraversato la configurazione guidata di WMR, l'utente poteva riscontrare diversi problemi di funzionalità audio, tra cui l'assenza di audio e nessun cambio audio, a seconda della configurazione del sistema prima di connettere il HMD per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="68c95-292">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="68c95-293">Input vocale in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="68c95-293">Voice input in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="68c95-294">Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , è possibile assegnare facilmente il comando Voice a tutti gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="68c95-294">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="68c95-295">Usare **il profilo di input vocale** di MRTK per definire le parole chiave.</span><span class="sxs-lookup"><span data-stu-id="68c95-295">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="68c95-296">Assegnando lo script **SpeechInputHandler** , è possibile fare in modo che qualsiasi oggetto risponda alle parole chiave definite nel profilo di input vocale.</span><span class="sxs-lookup"><span data-stu-id="68c95-296">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="68c95-297">SpeechInputHandler fornisce anche un'etichetta di conferma vocale per migliorare la confidenza dell'utente.</span><span class="sxs-lookup"><span data-stu-id="68c95-297">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="68c95-298">Comando MRTK-Voice</span><span class="sxs-lookup"><span data-stu-id="68c95-298">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="68c95-299">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="68c95-299">See also</span></span>
* [<span data-ttu-id="68c95-300">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="68c95-300">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="68c95-301">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="68c95-301">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="68c95-302">Input di MR 212: Voice</span><span class="sxs-lookup"><span data-stu-id="68c95-302">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="68c95-303">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="68c95-303">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="68c95-304">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="68c95-304">Voice input in Unity</span></span>](voice-input-in-unity.md)
