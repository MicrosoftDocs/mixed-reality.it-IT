---
title: Input vocale
description: Input vocale è un input di core per HoloLens e realtà mista di Windows auricolari coinvolgente e concreto. Vocale è utilizzabile per i comandi, dettatura, Cortana e altro ancora.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, voce, cortana, il riconoscimento vocale, di input
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829956"
---
# <a name="voice-input"></a><span data-ttu-id="38460-105">Input vocale</span><span class="sxs-lookup"><span data-stu-id="38460-105">Voice input</span></span>

<span data-ttu-id="38460-106">Vocale è uno dei tre formati principali di input su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38460-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="38460-107">Consente al comando direttamente ologramma senza dover usare [movimenti](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="38460-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="38460-108">È semplicemente [estasiati](gaze.md) in ologramma e si parla del comando.</span><span class="sxs-lookup"><span data-stu-id="38460-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="38460-109">Input vocale può essere un modo semplice per comunicare lo scopo previsto.</span><span class="sxs-lookup"><span data-stu-id="38460-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="38460-110">Vocale è particolarmente efficaci per attraversare complesse interfacce perché consente agli utenti di Taglia tramite i menu annidati con un solo comando.</span><span class="sxs-lookup"><span data-stu-id="38460-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="38460-111">Input vocale è una tecnologia di [stesso motore](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) che supporta la sintesi vocale in tutte le altre app di Windows universale.</span><span class="sxs-lookup"><span data-stu-id="38460-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="38460-112">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="38460-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="38460-113"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="38460-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="38460-114"><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="38460-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="38460-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="38460-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="38460-116"><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></span><span class="sxs-lookup"><span data-stu-id="38460-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="38460-117">Input vocale</span><span class="sxs-lookup"><span data-stu-id="38460-117">Voice input</span></span></td>
        <td><span data-ttu-id="38460-118">✔️</span><span class="sxs-lookup"><span data-stu-id="38460-118">✔️</span></span></td>
        <td><span data-ttu-id="38460-119">✔️</span><span class="sxs-lookup"><span data-stu-id="38460-119">✔️</span></span></td>
        <td><span data-ttu-id="38460-120">✔️ (con microfono)</span><span class="sxs-lookup"><span data-stu-id="38460-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="38460-121">Il comando "select"</span><span class="sxs-lookup"><span data-stu-id="38460-121">The "select" command</span></span>

<span data-ttu-id="38460-122">Anche senza specificamente aggiunta del supporto vocali all'App, gli utenti possono attivare vntana semplicemente specificando "select".</span><span class="sxs-lookup"><span data-stu-id="38460-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="38460-123">Si comporta come un [puntato](gestures.md#air-tap) su HoloLens, premendo il pulsante di selezione per il [HoloLens clicker](hardware-accessories.md#hololens-clicker), o premendo il trigger per un [controller movimento di realtà mista di Windows](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="38460-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="38460-124">Si verrà riprodotto un suono e una descrizione comando con l'istruzione "select" vengono visualizzati come conferma.</span><span class="sxs-lookup"><span data-stu-id="38460-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="38460-125">"Select" è abilitata per un algoritmo di rilevamento di basso consumo (parola chiave) in modo che è sempre disponibile per poter affermare in qualsiasi momento con un impatto minimo batteria vita, anche con le mani al lato dell'utente.</span><span class="sxs-lookup"><span data-stu-id="38460-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="38460-126">Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="38460-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="38460-127">![Ad esempio "select" per usare i comandi vocali per la selezione](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="38460-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="38460-128">*Ad esempio "select" per usare i comandi vocali per la selezione*</span><span class="sxs-lookup"><span data-stu-id="38460-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="38460-129">Ehi Cortana</span><span class="sxs-lookup"><span data-stu-id="38460-129">Hey Cortana</span></span>

<span data-ttu-id="38460-130">È inoltre possibile pronunciare "Ehi Cortana" per visualizzare Cortana in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="38460-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="38460-131">Non devi attendere di sembrano continuare chiede la domanda o relativa fornendo un'istruzione, ad esempio, provare ottimizzazioni "Ehi Cortana che cos'è il meteo?"</span><span class="sxs-lookup"><span data-stu-id="38460-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="38460-132">come una singola frase.</span><span class="sxs-lookup"><span data-stu-id="38460-132">as a single sentence.</span></span> <span data-ttu-id="38460-133">Per altre informazioni su Cortana e cosa può fare, è sufficiente richiedere copie!</span><span class="sxs-lookup"><span data-stu-id="38460-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="38460-134">Pronunciare "Ehi Cortana in che modo è dico?"</span><span class="sxs-lookup"><span data-stu-id="38460-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="38460-135">e Lei esegue pull un elenco di comandi funziona correttamente ed è consigliati.</span><span class="sxs-lookup"><span data-stu-id="38460-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="38460-136">Se si ha già nell'app di Cortana è anche possibile scegliere di **?**</span><span class="sxs-lookup"><span data-stu-id="38460-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="38460-137">icona sulla barra laterale per eseguire il pull questo stesso menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="38460-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="38460-138">**Comandi specifici HoloLens**</span><span class="sxs-lookup"><span data-stu-id="38460-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="38460-139">"Cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="38460-139">"What can I say?"</span></span>
* <span data-ttu-id="38460-140">"Go home" o "andare a Start" - anziché [bloom](gestures.md#bloom) per ottenere [Menu Start](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="38460-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="38460-141">"Avvio <app>"</span><span class="sxs-lookup"><span data-stu-id="38460-141">"Launch <app>"</span></span>
* <span data-ttu-id="38460-142">"Sposta <app> qui"</span><span class="sxs-lookup"><span data-stu-id="38460-142">"Move <app> here"</span></span>
* <span data-ttu-id="38460-143">"Scattare una foto"</span><span class="sxs-lookup"><span data-stu-id="38460-143">"Take a picture"</span></span>
* <span data-ttu-id="38460-144">"Avvia registrazione"</span><span class="sxs-lookup"><span data-stu-id="38460-144">"Start recording"</span></span>
* <span data-ttu-id="38460-145">"Arrestare la registrazione"</span><span class="sxs-lookup"><span data-stu-id="38460-145">"Stop recording"</span></span>
* <span data-ttu-id="38460-146">"Increase luminosità"</span><span class="sxs-lookup"><span data-stu-id="38460-146">"Increase the brightness"</span></span>
* <span data-ttu-id="38460-147">"Riduzione della luminosità"</span><span class="sxs-lookup"><span data-stu-id="38460-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="38460-148">"Increase il volume"</span><span class="sxs-lookup"><span data-stu-id="38460-148">"Increase the volume"</span></span>
* <span data-ttu-id="38460-149">"Diminuire il volume"</span><span class="sxs-lookup"><span data-stu-id="38460-149">"Decrease the volume"</span></span>
* <span data-ttu-id="38460-150">"Disattivare" o "Ripristinare"</span><span class="sxs-lookup"><span data-stu-id="38460-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="38460-151">"Arrestare il dispositivo"</span><span class="sxs-lookup"><span data-stu-id="38460-151">"Shut down the device"</span></span>
* <span data-ttu-id="38460-152">"Riavvia il dispositivo"</span><span class="sxs-lookup"><span data-stu-id="38460-152">"Restart the device"</span></span>
* <span data-ttu-id="38460-153">"Vai allo stato di sospensione"</span><span class="sxs-lookup"><span data-stu-id="38460-153">"Go to sleep"</span></span>
* <span data-ttu-id="38460-154">"Che ora è?"</span><span class="sxs-lookup"><span data-stu-id="38460-154">"What time is it?"</span></span>
* <span data-ttu-id="38460-155">"Quanti batteria rimasti?"</span><span class="sxs-lookup"><span data-stu-id="38460-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="38460-156">"Chiamare <contact>" (richiede Skype per HoloLens)</span><span class="sxs-lookup"><span data-stu-id="38460-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="38460-157">"Visualizzarlo, dice"</span><span class="sxs-lookup"><span data-stu-id="38460-157">"See It, Say It"</span></span>

<span data-ttu-id="38460-158">HoloLens dispone di un modello "visualizzarlo, dice" per l'input vocale, in cui le etichette nei pulsanti indicano agli utenti quali comandi vocali dice anche.</span><span class="sxs-lookup"><span data-stu-id="38460-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="38460-159">Ad esempio, quando si esamina un'app 2D, un utente può pronunciare il comando "Regolare" che viene visualizzato nella barra dell'App per regolare la posizione dell'app nel mondo.</span><span class="sxs-lookup"><span data-stu-id="38460-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![Quando si esamina un'ologrammi o un'app 2D, un utente può pronunciare il comando "Regolare" che viene visualizzato nella barra dell'App per regolare la posizione dell'app nel mondo](images/microphone-600px.png)

<span data-ttu-id="38460-161">Quando le app seguono questa regola, possono comprenderne facilmente agli utenti cosa significa controllare il sistema.</span><span class="sxs-lookup"><span data-stu-id="38460-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="38460-162">Per ribadire, mentre gazing a un pulsante, si noterà una descrizione comando "permanenza della voce" che viene visualizzato dopo un secondo se il pulsante è abilitato per la voce e viene visualizzato il comando da leggere a voce per "premerlo".</span><span class="sxs-lookup"><span data-stu-id="38460-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="38460-163">![Visualizzarlo, ad esempio, i comandi vengono visualizzate sotto i pulsanti](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="38460-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="38460-164">*"A vederla, dice" i comandi vengono visualizzate sotto i pulsanti*</span><span class="sxs-lookup"><span data-stu-id="38460-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="38460-165">Comandi vocali per la manipolazione di ologramma veloce</span><span class="sxs-lookup"><span data-stu-id="38460-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="38460-166">Esistono anche numerose vocale comandi è possibile dire durante gazing in ologramma per eseguire rapidamente attività di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="38460-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="38460-167">Questi comandi vocali si cimentano App 2D nonché oggetti 3D che è stato inserito nel mondo.</span><span class="sxs-lookup"><span data-stu-id="38460-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="38460-168">**Comandi di manipolazione ologrammi**</span><span class="sxs-lookup"><span data-stu-id="38460-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="38460-169">Viso me</span><span class="sxs-lookup"><span data-stu-id="38460-169">Face me</span></span>
* <span data-ttu-id="38460-170">Più grande | Migliorare</span><span class="sxs-lookup"><span data-stu-id="38460-170">Bigger | Enhance</span></span>
* <span data-ttu-id="38460-171">Più piccolo</span><span class="sxs-lookup"><span data-stu-id="38460-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="38460-172">Dettatura</span><span class="sxs-lookup"><span data-stu-id="38460-172">Dictation</span></span>

<span data-ttu-id="38460-173">Invece di digitare con [aria scelte](gestures.md#air-tap), dettatura può essere più efficiente di immettere testo in un'app.</span><span class="sxs-lookup"><span data-stu-id="38460-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="38460-174">Ciò consente di accelerare notevolmente input con meno sforzi per l'utente.</span><span class="sxs-lookup"><span data-stu-id="38460-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="38460-175">![Dettatura inizia selezionando il pulsante del microfono](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="38460-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="38460-176">*Dettatura inizia selezionando il pulsante del microfono sulla tastiera*</span><span class="sxs-lookup"><span data-stu-id="38460-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="38460-177">Ogni volta che la tastiera holographic è attiva, è possibile passare alla modalità di dettatura anziché digitare.</span><span class="sxs-lookup"><span data-stu-id="38460-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="38460-178">Selezionare il microfono sul lato di casella di input di testo per iniziare.</span><span class="sxs-lookup"><span data-stu-id="38460-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="38460-179">Comunicazione</span><span class="sxs-lookup"><span data-stu-id="38460-179">Communication</span></span>

<span data-ttu-id="38460-180">Per le applicazioni che vogliono sfruttare i vantaggi dell'input audio personalizzato fornite da HoloLens opzioni di elaborazione, è importante comprendere i vari [categorie flusso audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) può usare l'app.</span><span class="sxs-lookup"><span data-stu-id="38460-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="38460-181">Windows 10 supporta diverse categorie di flusso diverso e HoloLens rende l'utilizzo di tre di questi per consentire l'elaborazione personalizzata ottimizzare la qualità audio microfono su misura per la sintesi vocale, la comunicazione e altri che può essere usato per audio ambiente ambiente scenari di acquisizione (vale a dire "cineprese").</span><span class="sxs-lookup"><span data-stu-id="38460-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="38460-182">La categoria di flusso AudioCategory_Communications personalizzata per la chiamata di qualità e un testo descrittivo scenari e fornisce al client con un flusso audio mono a 24 kHz 16 bit della voce dell'utente</span><span class="sxs-lookup"><span data-stu-id="38460-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="38460-183">La categoria di flusso AudioCategory_Speech personalizzata per il motore di sintesi vocale HoloLens (Windows) e fornisce un flusso di mono a 24 kHz 16 bit della voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="38460-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="38460-184">Questa categoria può essere utilizzata dai motori di sintesi vocale 3rd party se necessario.</span><span class="sxs-lookup"><span data-stu-id="38460-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="38460-185">La categoria di flusso AudioCategory_Other personalizzata per la registrazione audio ambiente ambiente e fornisce al client con un flusso audio stereo a 48 bit 24 kHz.</span><span class="sxs-lookup"><span data-stu-id="38460-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="38460-186">Tutti i questa elaborazione audio è con accelerazione hardware che indica che le funzionalità di svuotare molto meno energia rispetto a se stessa elaborazione è stata eseguita sulla CPU HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38460-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="38460-187">Evitare di eseguire altri input audio di elaborazione sulla CPU per ottimizzare la durata della batteria del sistema e sfruttare i vantaggi di incorporato, l'offload l'elaborazione dell'input audio.</span><span class="sxs-lookup"><span data-stu-id="38460-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="38460-188">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="38460-188">Troubleshooting</span></span>

<span data-ttu-id="38460-189">Se si verificano eventuali problemi tramite "selezionare" e "Ehi Cortana", provare a spostare in uno spazio risulteranno meno intensi, l'attivazione verso la sorgente di disturbo o parlando più alto.</span><span class="sxs-lookup"><span data-stu-id="38460-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="38460-190">A questo punto, tutti di riconoscimento vocale in HoloLens è ottimizzato e ottimizzato in modo specifico per madrelingua dell'inglese degli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="38460-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="38460-191">Per la versione di Windows misti realtà Developer Edition 2017, la logica di gestione endpoint audio funziona correttamente (per sempre) dopo la registrazione e al desktop del computer dopo la connessione HMD iniziale.</span><span class="sxs-lookup"><span data-stu-id="38460-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="38460-192">Prima di tale prima sign out/in eventi dopo il passaggio attraverso WMR OOBE, l'utente potrebbe subire vari problemi di funzionalità audio compreso senza audio e nessun audio di commutazione a seconda del modo in cui è stato configurato il sistema prima di connettere il HMD per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="38460-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="38460-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="38460-193">See also</span></span>
* [<span data-ttu-id="38460-194">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="38460-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="38460-195">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="38460-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="38460-196">Input MR 212: Voce</span><span class="sxs-lookup"><span data-stu-id="38460-196">MR Input 212: Voice</span></span>](holograms-212.md)
