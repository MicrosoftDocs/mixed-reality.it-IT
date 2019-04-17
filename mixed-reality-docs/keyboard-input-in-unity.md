---
title: Input da tastiera in Unity
description: Unity offre la classe TouchScreenKeyboard per accettare input da tastiera quando non è disponibile alcuna tastiera fisica.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: unity input, dalla tastiera del computer, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604889"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="a2aba-104">Input da tastiera in Unity</span><span class="sxs-lookup"><span data-stu-id="a2aba-104">Keyboard input in Unity</span></span>

<span data-ttu-id="a2aba-105">**Namespace:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="a2aba-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="a2aba-106">**Tipo**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="a2aba-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="a2aba-107">Mentre HoloLens supporta molti formati di input, tra cui Bluetooth tastiere, la maggior parte delle applicazioni non possono presupporre che tutti gli utenti avranno una tastiera fisica disponibile.</span><span class="sxs-lookup"><span data-stu-id="a2aba-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="a2aba-108">Se l'applicazione richiede l'input di testo, è necessario specificare una forma di tastiera su schermo.</span><span class="sxs-lookup"><span data-stu-id="a2aba-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="a2aba-109">Unity offre il *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* classe per accettare input da tastiera quando non è disponibile alcuna tastiera fisica.</span><span class="sxs-lookup"><span data-stu-id="a2aba-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="a2aba-110">Comportamento della tastiera sistema HoloLens in Unity</span><span class="sxs-lookup"><span data-stu-id="a2aba-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="a2aba-111">Su HoloLens, la *TouchScreenKeyboard* sfrutta la tastiera su schermo del sistema.</span><span class="sxs-lookup"><span data-stu-id="a2aba-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="a2aba-112">Tastiera su schermo del sistema non riesce a sovrapporre all'inizio di una vista volumetrica in modo che dispone di Unity creare una visualizzazione XAML 2D secondaria per mostrare la tastiera quindi tornare alla visualizzazione volumetrica dopo che l'input è stato inviato.</span><span class="sxs-lookup"><span data-stu-id="a2aba-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="a2aba-113">Il flusso utente è il seguente:</span><span class="sxs-lookup"><span data-stu-id="a2aba-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="a2aba-114">L'utente esegue un'azione che ha causato il codice di app di chiamare *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="a2aba-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="a2aba-115">L'app è responsabile per lo stato di sospensione app prima di chiamare *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="a2aba-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="a2aba-116">L'app può terminare prima del passaggio che mai tornare alla visualizzazione volumetrica</span><span class="sxs-lookup"><span data-stu-id="a2aba-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="a2aba-117">Unity passa a una visualizzazione XAML 2D disponibile posizionati automaticamente in tutto il mondo</span><span class="sxs-lookup"><span data-stu-id="a2aba-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="a2aba-118">L'utente immette testo mediante la tastiera del sistema e invia o Annulla</span><span class="sxs-lookup"><span data-stu-id="a2aba-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="a2aba-119">Unity passa nuovamente alla visualizzazione volumetrica</span><span class="sxs-lookup"><span data-stu-id="a2aba-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="a2aba-120">L'app è responsabile della ripresa dell'app stato quando la *TouchScreenKeyboard* avviene</span><span class="sxs-lookup"><span data-stu-id="a2aba-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="a2aba-121">È disponibile in testo inviati il *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="a2aba-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="a2aba-122">Viste da tastiera disponibili</span><span class="sxs-lookup"><span data-stu-id="a2aba-122">Available keyboard views</span></span>

<span data-ttu-id="a2aba-123">Sono disponibili sei viste della tastiera a altro:</span><span class="sxs-lookup"><span data-stu-id="a2aba-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="a2aba-124">Nella casella di testo a riga singola</span><span class="sxs-lookup"><span data-stu-id="a2aba-124">Single-line textbox</span></span>
* <span data-ttu-id="a2aba-125">Nella casella di testo a riga singola con titolo</span><span class="sxs-lookup"><span data-stu-id="a2aba-125">Single-line textbox with title</span></span>
* <span data-ttu-id="a2aba-126">Nella casella di testo multilinea</span><span class="sxs-lookup"><span data-stu-id="a2aba-126">Multi-line textbox</span></span>
* <span data-ttu-id="a2aba-127">Nella casella di testo multilinea con titolo</span><span class="sxs-lookup"><span data-stu-id="a2aba-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="a2aba-128">Casella della password a riga singola</span><span class="sxs-lookup"><span data-stu-id="a2aba-128">Single-line password box</span></span>
* <span data-ttu-id="a2aba-129">Casella della password a riga singola con titolo</span><span class="sxs-lookup"><span data-stu-id="a2aba-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="a2aba-130">Come abilitare la tastiera del sistema in Unity</span><span class="sxs-lookup"><span data-stu-id="a2aba-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="a2aba-131">I tasti di sistema HoloLens sono disponibili solo per le applicazioni di Unity che vengono esportate con il "UWP tipo Build" impostato su "XAML".</span><span class="sxs-lookup"><span data-stu-id="a2aba-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="a2aba-132">Sussistono compromessi apportate quando si sceglie "XAML" come "UWP BuildType" su "D3D".</span><span class="sxs-lookup"><span data-stu-id="a2aba-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="a2aba-133">Se non si ha familiarità con questi compromessi, è consigliabile consultare un [soluzione di input alternativi](#alternative-keyboard-options) alla tastiera di sistema.</span><span class="sxs-lookup"><span data-stu-id="a2aba-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="a2aba-134">Aprire il **File** dal menu **Build Settings...**</span><span class="sxs-lookup"><span data-stu-id="a2aba-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="a2aba-135">Verificare che il **piattaforma** è impostata su **Windows Store**, il **SDK** è impostata su **10 universale**e impostare il **tipo Build UWP**  al **XAML**.</span><span class="sxs-lookup"><span data-stu-id="a2aba-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="a2aba-136">Nel **Build Settings** finestra di dialogo, fare clic sui **le impostazioni del giocatore...**  pulsante</span><span class="sxs-lookup"><span data-stu-id="a2aba-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="a2aba-137">Selezionare il **le impostazioni per Windows Store** scheda</span><span class="sxs-lookup"><span data-stu-id="a2aba-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="a2aba-138">Espandere la **altre impostazioni** gruppo</span><span class="sxs-lookup"><span data-stu-id="a2aba-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="a2aba-139">Nel **Rendering** sezione, verificare il **realtà virtuale supportato** casella di controllo per aggiungere un nuovo **dispositivi per realtà virtuale** elenco</span><span class="sxs-lookup"><span data-stu-id="a2aba-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="a2aba-140">Assicurarsi **Windows Holographic** visualizzato nell'elenco degli SDK di realtà virtuale</span><span class="sxs-lookup"><span data-stu-id="a2aba-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="a2aba-141">Se non si contrassegna la compilazione come realtà virtuale supportata con il dispositivo HoloLens, il progetto verrà esportati come un'app XAML 2D.</span><span class="sxs-lookup"><span data-stu-id="a2aba-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="a2aba-142">Uso della tastiera di sistema nell'app Unity</span><span class="sxs-lookup"><span data-stu-id="a2aba-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="a2aba-143">Dichiarare la tastiera</span><span class="sxs-lookup"><span data-stu-id="a2aba-143">Declare the keyboard</span></span>

<span data-ttu-id="a2aba-144">Nella classe, dichiarare una variabile per archiviare le *TouchScreenKeyboard* e restituisce una variabile per contenere la stringa della tastiera.</span><span class="sxs-lookup"><span data-stu-id="a2aba-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="a2aba-145">Richiamare la tastiera</span><span class="sxs-lookup"><span data-stu-id="a2aba-145">Invoke the keyboard</span></span>

<span data-ttu-id="a2aba-146">Quando si verifica un evento che richiede input da tastiera, chiamare una di queste funzioni in base al tipo di input desiderato.</span><span class="sxs-lookup"><span data-stu-id="a2aba-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="a2aba-147">Si noti che il titolo è specificato nel parametro textPlaceholder.</span><span class="sxs-lookup"><span data-stu-id="a2aba-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="a2aba-148">Recuperare contenuto tipizzato</span><span class="sxs-lookup"><span data-stu-id="a2aba-148">Retrieve typed contents</span></span>

<span data-ttu-id="a2aba-149">Nel ciclo di aggiornamento, controllare se la tastiera ricevuto nuovo input e archiviarlo per l'uso in un' posizione.</span><span class="sxs-lookup"><span data-stu-id="a2aba-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="a2aba-150">Opzioni della tastiera alternativo</span><span class="sxs-lookup"><span data-stu-id="a2aba-150">Alternative keyboard options</span></span>

<span data-ttu-id="a2aba-151">Siamo consapevoli che il passaggio all'esterno di una vista in una visualizzazione 2D volumetrica non è il modo ideale per ottenere l'input di testo da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a2aba-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="a2aba-152">Le alternative corrente per l'uso della tastiera di sistema tramite Unity includono:</span><span class="sxs-lookup"><span data-stu-id="a2aba-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="a2aba-153">Utilizzando la dettatura di riconoscimento vocale per l'input (<b>Nota:</b> ciò spesso è soggetta a errori per le parole non trovate nel dizionario e non è adatto per l'immissione della password)</span><span class="sxs-lookup"><span data-stu-id="a2aba-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="a2aba-154">Creare una tastiera che funziona nella propria vista esclusivo di applicazioni</span><span class="sxs-lookup"><span data-stu-id="a2aba-154">Create a keyboard that works in your applications exclusive view</span></span>
