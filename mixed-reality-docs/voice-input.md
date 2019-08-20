---
title: Input vocale
description: L'input vocale è un input di base per HoloLens e per le cuffie immersive in realtà mista di Windows. La voce può essere usata per i comandi, la dettatura, il Cortana e altro ancora.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, input
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829956"
---
# <a name="voice-input"></a><span data-ttu-id="b4b46-105">Input vocale</span><span class="sxs-lookup"><span data-stu-id="b4b46-105">Voice input</span></span>

<span data-ttu-id="b4b46-106">Voice è una delle tre forme chiave di input per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b4b46-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="b4b46-107">Consente di eseguire direttamente il comando di un ologramma senza dover usare i [movimenti](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="b4b46-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="b4b46-108">È sufficiente [guardare](gaze.md) un ologramma e pronunciare il comando.</span><span class="sxs-lookup"><span data-stu-id="b4b46-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="b4b46-109">L'input vocale può essere un metodo naturale per comunicare lo scopo.</span><span class="sxs-lookup"><span data-stu-id="b4b46-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="b4b46-110">La voce è particolarmente utile per attraversare interfacce complesse perché consente agli utenti di tagliare i menu nidificati con un unico comando.</span><span class="sxs-lookup"><span data-stu-id="b4b46-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="b4b46-111">L'input vocale è alimentato dallo [stesso motore](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) che supporta la sintesi vocale in tutte le altre app di Windows universale.</span><span class="sxs-lookup"><span data-stu-id="b4b46-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="b4b46-112">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="b4b46-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4b46-113"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="b4b46-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b4b46-114"><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4b46-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b4b46-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b4b46-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b4b46-116"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4b46-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4b46-117">Input vocale</span><span class="sxs-lookup"><span data-stu-id="b4b46-117">Voice input</span></span></td>
        <td><span data-ttu-id="b4b46-118">✔️</span><span class="sxs-lookup"><span data-stu-id="b4b46-118">✔️</span></span></td>
        <td><span data-ttu-id="b4b46-119">✔️</span><span class="sxs-lookup"><span data-stu-id="b4b46-119">✔️</span></span></td>
        <td><span data-ttu-id="b4b46-120">✔️ (con microfono)</span><span class="sxs-lookup"><span data-stu-id="b4b46-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="b4b46-121">Comando "Select"</span><span class="sxs-lookup"><span data-stu-id="b4b46-121">The "select" command</span></span>

<span data-ttu-id="b4b46-122">Anche senza aggiungere esplicitamente il supporto vocale all'app, gli utenti possono attivare gli ologrammi semplicemente dicendo "Select".</span><span class="sxs-lookup"><span data-stu-id="b4b46-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="b4b46-123">Questo comportamento è identico a quello di un [rubinetto d'aria](gestures.md#air-tap) su HoloLens, facendo clic sul pulsante Seleziona nel [HoloLens clic](hardware-accessories.md#hololens-clicker)oppure premendo il trigger in un [controller di movimento della realtà mista di Windows](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="b4b46-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="b4b46-124">Verrà visualizzato un suono e verrà visualizzata una descrizione comando con "Select" come conferma.</span><span class="sxs-lookup"><span data-stu-id="b4b46-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="b4b46-125">"Select" è abilitato da un algoritmo di rilevamento di parole chiave a basso consumo, in modo che sia sempre disponibile per l'utente in qualsiasi momento con un minimo di durata della batteria, anche con le tue mani.</span><span class="sxs-lookup"><span data-stu-id="b4b46-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="b4b46-126">Altre indicazioni specifiche per HoloLens 2 [saranno presto](index.md#news-and-notes)disponibili.</span><span class="sxs-lookup"><span data-stu-id="b4b46-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="b4b46-127">![Pronunciare "Select" per utilizzare il comando Voice per la selezione](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="b4b46-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="b4b46-128">*Pronunciare "Select" per utilizzare il comando Voice per la selezione*</span><span class="sxs-lookup"><span data-stu-id="b4b46-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="b4b46-129">Ehi Cortana</span><span class="sxs-lookup"><span data-stu-id="b4b46-129">Hey Cortana</span></span>

<span data-ttu-id="b4b46-130">È anche possibile pronunciare "Hey Cortana" per visualizzare Cortana in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="b4b46-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="b4b46-131">Non è necessario attendere che venga visualizzata per continuare a porre una domanda o fornire un'istruzione, ad esempio, provare a pronunciare "Hey Cortana qual è il meteo?"</span><span class="sxs-lookup"><span data-stu-id="b4b46-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="b4b46-132">come singola frase.</span><span class="sxs-lookup"><span data-stu-id="b4b46-132">as a single sentence.</span></span> <span data-ttu-id="b4b46-133">Per ulteriori informazioni su Cortana e sulle operazioni che è possibile eseguire, è sufficiente chiederle!</span><span class="sxs-lookup"><span data-stu-id="b4b46-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="b4b46-134">Pronunciare "Hey Cortana cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="b4b46-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="b4b46-135">verrà quindi eseguito il pull di un elenco di comandi funzionanti e consigliati.</span><span class="sxs-lookup"><span data-stu-id="b4b46-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="b4b46-136">Se si è già nell'app Cortana, è anche possibile fare clic sul pulsante **?**</span><span class="sxs-lookup"><span data-stu-id="b4b46-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="b4b46-137">icona sulla barra laterale per estrarre lo stesso menu.</span><span class="sxs-lookup"><span data-stu-id="b4b46-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="b4b46-138">**Comandi specifici di HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b4b46-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="b4b46-139">"Cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="b4b46-139">"What can I say?"</span></span>
* <span data-ttu-id="b4b46-140">"Vai a casa" o "Vai a avvio"-anziché [Bloom](gestures.md#bloom) per visualizzare il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="b4b46-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="b4b46-141">"Avvia <app>"</span><span class="sxs-lookup"><span data-stu-id="b4b46-141">"Launch <app>"</span></span>
* <span data-ttu-id="b4b46-142">"Sposta <app> qui"</span><span class="sxs-lookup"><span data-stu-id="b4b46-142">"Move <app> here"</span></span>
* <span data-ttu-id="b4b46-143">"Scattare un'immagine"</span><span class="sxs-lookup"><span data-stu-id="b4b46-143">"Take a picture"</span></span>
* <span data-ttu-id="b4b46-144">"Avvia registrazione"</span><span class="sxs-lookup"><span data-stu-id="b4b46-144">"Start recording"</span></span>
* <span data-ttu-id="b4b46-145">"Arresta registrazione"</span><span class="sxs-lookup"><span data-stu-id="b4b46-145">"Stop recording"</span></span>
* <span data-ttu-id="b4b46-146">"Aumentare la luminosità"</span><span class="sxs-lookup"><span data-stu-id="b4b46-146">"Increase the brightness"</span></span>
* <span data-ttu-id="b4b46-147">"Riduzione della luminosità"</span><span class="sxs-lookup"><span data-stu-id="b4b46-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="b4b46-148">"Aumento del volume"</span><span class="sxs-lookup"><span data-stu-id="b4b46-148">"Increase the volume"</span></span>
* <span data-ttu-id="b4b46-149">"Diminuisci volume"</span><span class="sxs-lookup"><span data-stu-id="b4b46-149">"Decrease the volume"</span></span>
* <span data-ttu-id="b4b46-150">"Mute" o "unmute"</span><span class="sxs-lookup"><span data-stu-id="b4b46-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="b4b46-151">"Arresta il dispositivo"</span><span class="sxs-lookup"><span data-stu-id="b4b46-151">"Shut down the device"</span></span>
* <span data-ttu-id="b4b46-152">"Riavvia il dispositivo"</span><span class="sxs-lookup"><span data-stu-id="b4b46-152">"Restart the device"</span></span>
* <span data-ttu-id="b4b46-153">"Vai a sospensione"</span><span class="sxs-lookup"><span data-stu-id="b4b46-153">"Go to sleep"</span></span>
* <span data-ttu-id="b4b46-154">"Qual è il tempo?"</span><span class="sxs-lookup"><span data-stu-id="b4b46-154">"What time is it?"</span></span>
* <span data-ttu-id="b4b46-155">"Quanta batteria è rimasta?"</span><span class="sxs-lookup"><span data-stu-id="b4b46-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="b4b46-156">"Call <contact>" (richiede Skype per HoloLens)</span><span class="sxs-lookup"><span data-stu-id="b4b46-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="b4b46-157">"Vedere la voce"</span><span class="sxs-lookup"><span data-stu-id="b4b46-157">"See It, Say It"</span></span>

<span data-ttu-id="b4b46-158">HoloLens dispone di un modello "See it, Say it" per l'input vocale, in cui le etichette sui pulsanti indicano agli utenti i comandi vocali che possono dire.</span><span class="sxs-lookup"><span data-stu-id="b4b46-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="b4b46-159">Ad esempio, quando si esamina un'app 2D, un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app nel mondo.</span><span class="sxs-lookup"><span data-stu-id="b4b46-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![Quando si esamina un'app 2D o un ologramma, un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app nel mondo](images/microphone-600px.png)

<span data-ttu-id="b4b46-161">Quando le app seguono questa regola, gli utenti possono comprendere facilmente cosa dire per controllare il sistema.</span><span class="sxs-lookup"><span data-stu-id="b4b46-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="b4b46-162">Per rinforzare questo problema, guardando un pulsante, viene visualizzata una descrizione comando "Voice Rest" che viene visualizzata dopo un secondo se il pulsante è abilitato per la voce e visualizza il comando per "premere".</span><span class="sxs-lookup"><span data-stu-id="b4b46-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="b4b46-163">![Vedere i comandi visualizzati sotto i pulsanti](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="b4b46-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="b4b46-164">*I comandi "See it, Say it" appaiono sotto i pulsanti*</span><span class="sxs-lookup"><span data-stu-id="b4b46-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="b4b46-165">Comandi vocali per la manipolazione rapida degli ologrammi</span><span class="sxs-lookup"><span data-stu-id="b4b46-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="b4b46-166">Sono inoltre disponibili numerosi comandi vocali che è possibile osservare guardando un ologramma per eseguire rapidamente le attività di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="b4b46-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="b4b46-167">Questi comandi vocali funzionano in app 2D e in oggetti 3D che sono stati inseriti nel mondo.</span><span class="sxs-lookup"><span data-stu-id="b4b46-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="b4b46-168">**Comandi di manipolazione ologramma**</span><span class="sxs-lookup"><span data-stu-id="b4b46-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="b4b46-169">Mi faccia</span><span class="sxs-lookup"><span data-stu-id="b4b46-169">Face me</span></span>
* <span data-ttu-id="b4b46-170">Più grande | Migliorare</span><span class="sxs-lookup"><span data-stu-id="b4b46-170">Bigger | Enhance</span></span>
* <span data-ttu-id="b4b46-171">Più piccoli</span><span class="sxs-lookup"><span data-stu-id="b4b46-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="b4b46-172">Dettatura</span><span class="sxs-lookup"><span data-stu-id="b4b46-172">Dictation</span></span>

<span data-ttu-id="b4b46-173">Invece di digitare con le [scelte aeree](gestures.md#air-tap), la dettatura vocale può essere più efficiente per inserire il testo in un'app.</span><span class="sxs-lookup"><span data-stu-id="b4b46-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="b4b46-174">Questo può accelerare significativamente l'input con minore impegno per l'utente.</span><span class="sxs-lookup"><span data-stu-id="b4b46-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="b4b46-175">![La dettatura vocale inizia selezionando il pulsante del microfono](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="b4b46-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="b4b46-176">*La dettatura vocale inizia selezionando il pulsante del microfono sulla tastiera*</span><span class="sxs-lookup"><span data-stu-id="b4b46-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="b4b46-177">Ogni volta che la tastiera olografica è attiva, è possibile passare alla modalità di dettatura anziché alla digitazione.</span><span class="sxs-lookup"><span data-stu-id="b4b46-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="b4b46-178">Per iniziare, selezionare il microfono sul lato della casella input di testo.</span><span class="sxs-lookup"><span data-stu-id="b4b46-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="b4b46-179">Comunicazione</span><span class="sxs-lookup"><span data-stu-id="b4b46-179">Communication</span></span>

<span data-ttu-id="b4b46-180">Per le applicazioni che vogliono sfruttare le opzioni di elaborazione dell'input audio personalizzato fornite da HoloLens, è importante comprendere le diverse categorie di [flussi audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) che l'app può utilizzare.</span><span class="sxs-lookup"><span data-stu-id="b4b46-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="b4b46-181">Windows 10 supporta diverse categorie di flusso e HoloLens ne usa tre per consentire l'elaborazione personalizzata per ottimizzare la qualità audio del microfono personalizzata per la comunicazione vocale, la comunicazione e altro che può essere usata per l'audio dell'ambiente di ambiente scenari di acquisizione, ad esempio "videocamera".</span><span class="sxs-lookup"><span data-stu-id="b4b46-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="b4b46-182">La categoria del flusso AudioCategory_Communications è personalizzata per gli scenari di qualità della chiamata e di narrazione e fornisce al client un flusso audio 16kHz 24bit mono della voce dell'utente</span><span class="sxs-lookup"><span data-stu-id="b4b46-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="b4b46-183">La categoria del flusso AudioCategory_Speech è personalizzata per il motore vocale HoloLens (Windows) e fornisce un flusso 16kHz 24bit mono della voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="b4b46-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="b4b46-184">Questa categoria può essere usata dai motori di sintesi vocale di terze parti, se necessario.</span><span class="sxs-lookup"><span data-stu-id="b4b46-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="b4b46-185">La categoria del flusso AudioCategory_Other è personalizzata per la registrazione audio dell'ambiente di ambiente e fornisce al client un flusso audio stereo a 24 bit a 48 bit.</span><span class="sxs-lookup"><span data-stu-id="b4b46-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="b4b46-186">Questa elaborazione audio è accelerata dall'hardware, il che significa che le funzionalità svuotano molto meno energia rispetto a quando la stessa elaborazione è stata eseguita sulla CPU HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b4b46-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="b4b46-187">Evitare di eseguire altre elaborazioni di input audio sulla CPU per ottimizzare la durata della batteria del sistema e sfruttare i vantaggi dell'elaborazione dell'input audio con offload incorporato.</span><span class="sxs-lookup"><span data-stu-id="b4b46-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="b4b46-188">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="b4b46-188">Troubleshooting</span></span>

<span data-ttu-id="b4b46-189">Se si verificano problemi con "Select" e "Hey Cortana", provare a passare a uno spazio più silenzioso, a disattivarsi dall'origine del rumore o a una voce più forte.</span><span class="sxs-lookup"><span data-stu-id="b4b46-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="b4b46-190">A questo punto, tutto il riconoscimento vocale in HoloLens viene ottimizzato e ottimizzato in modo specifico per gli altoparlanti nativi di Stati Uniti inglese.</span><span class="sxs-lookup"><span data-stu-id="b4b46-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="b4b46-191">Per la versione 2017 di Windows Mixed Reality Developer Edition, la logica di gestione degli endpoint audio funzionerà correttamente (per sempre) dopo la disconnessione e l'accesso al desktop del PC dopo la connessione iniziale di HMD.</span><span class="sxs-lookup"><span data-stu-id="b4b46-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="b4b46-192">Prima della prima disconnessione o dell'evento, dopo aver attraversato la configurazione guidata di WMR, l'utente poteva riscontrare diversi problemi di funzionalità audio, tra cui l'assenza di audio e nessun cambio audio, a seconda della configurazione del sistema prima di connettere il HMD per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="b4b46-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4b46-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b4b46-193">See also</span></span>
* [<span data-ttu-id="b4b46-194">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="b4b46-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="b4b46-195">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="b4b46-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="b4b46-196">Input MR 212: Voce</span><span class="sxs-lookup"><span data-stu-id="b4b46-196">MR Input 212: Voice</span></span>](holograms-212.md)
