---
title: Input da tastiera in Unity
description: Unity fornisce la classe TouchScreenKeyboard per accettare l'input da tastiera quando non è disponibile una tastiera fisica.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: tastiera, input, Unity, touchscreenkeyboard
ms.openlocfilehash: f506415f9658d9723bf31b339d63fe4569100ace
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438557"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="11da3-104">Input da tastiera in Unity</span><span class="sxs-lookup"><span data-stu-id="11da3-104">Keyboard input in Unity</span></span>

<span data-ttu-id="11da3-105">**Spazio dei nomi:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="11da3-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="11da3-106">**Tipo**:  *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="11da3-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="11da3-107">Sebbene HoloLens supporti molte forme di input, incluse le tastiere Bluetooth, la maggior parte delle applicazioni non può presupporre che tutti gli utenti dispongano di una tastiera fisica disponibile.</span><span class="sxs-lookup"><span data-stu-id="11da3-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="11da3-108">Se l'applicazione richiede un input di testo, è necessario specificare una qualsiasi forma di tastiera sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="11da3-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="11da3-109">Unity fornisce la classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* per accettare l'input da tastiera quando non è disponibile una tastiera fisica.</span><span class="sxs-lookup"><span data-stu-id="11da3-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="11da3-110">Comportamento della tastiera di sistema HoloLens in Unity</span><span class="sxs-lookup"><span data-stu-id="11da3-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="11da3-111">In HoloLens, *TouchScreenKeyboard* sfrutta la tastiera sullo schermo del sistema.</span><span class="sxs-lookup"><span data-stu-id="11da3-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="11da3-112">La tastiera sullo schermo del sistema non è in grado di sovrapporsi a una visualizzazione volumetrica, in modo che Unity debba creare una visualizzazione XAML 2D secondaria per mostrare la tastiera e tornare alla visualizzazione volumetrica una volta inviato l'input.</span><span class="sxs-lookup"><span data-stu-id="11da3-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="11da3-113">Il flusso utente sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="11da3-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="11da3-114">L'utente esegue un'azione che causa il codice dell'app per chiamare *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="11da3-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="11da3-115">L'app è responsabile della sospensione dello stato dell'app prima della chiamata a *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="11da3-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="11da3-116">L'app può terminare prima di tornare alla visualizzazione volumetrica</span><span class="sxs-lookup"><span data-stu-id="11da3-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="11da3-117">Unity passa a una visualizzazione XAML 2D, che viene inserita automaticamente nel mondo</span><span class="sxs-lookup"><span data-stu-id="11da3-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="11da3-118">L'utente immette il testo usando la tastiera di sistema e invia o Annulla</span><span class="sxs-lookup"><span data-stu-id="11da3-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="11da3-119">Unity ritorna alla visualizzazione volumetrica</span><span class="sxs-lookup"><span data-stu-id="11da3-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="11da3-120">L'app è responsabile della ripresa dello stato dell'app al termine della *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="11da3-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="11da3-121">Il testo inviato è disponibile in *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="11da3-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="11da3-122">Visualizzazioni tastiera disponibili</span><span class="sxs-lookup"><span data-stu-id="11da3-122">Available keyboard views</span></span>

<span data-ttu-id="11da3-123">Sono disponibili sei diverse visualizzazioni tastiera:</span><span class="sxs-lookup"><span data-stu-id="11da3-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="11da3-124">Casella di testo a riga singola</span><span class="sxs-lookup"><span data-stu-id="11da3-124">Single-line textbox</span></span>
* <span data-ttu-id="11da3-125">Casella di testo a riga singola con titolo</span><span class="sxs-lookup"><span data-stu-id="11da3-125">Single-line textbox with title</span></span>
* <span data-ttu-id="11da3-126">Casella di testo a più righe</span><span class="sxs-lookup"><span data-stu-id="11da3-126">Multi-line textbox</span></span>
* <span data-ttu-id="11da3-127">Casella di testo a più righe con titolo</span><span class="sxs-lookup"><span data-stu-id="11da3-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="11da3-128">Casella password a riga singola</span><span class="sxs-lookup"><span data-stu-id="11da3-128">Single-line password box</span></span>
* <span data-ttu-id="11da3-129">Casella password a riga singola con titolo</span><span class="sxs-lookup"><span data-stu-id="11da3-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="11da3-130">Come abilitare la tastiera di sistema in Unity</span><span class="sxs-lookup"><span data-stu-id="11da3-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="11da3-131">La tastiera di sistema HoloLens è disponibile solo per le applicazioni Unity esportate con il "tipo di compilazione UWP" impostato su "XAML".</span><span class="sxs-lookup"><span data-stu-id="11da3-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="11da3-132">Quando si sceglie "XAML" come "tipo di compilazione UWP" su "D3D", si verificano compromessi.</span><span class="sxs-lookup"><span data-stu-id="11da3-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="11da3-133">Se non si ha familiarità con questi compromessi, può essere utile esplorare una [soluzione di input alternativa](#alternative-keyboard-options) alla tastiera di sistema.</span><span class="sxs-lookup"><span data-stu-id="11da3-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="11da3-134">Aprire il menu **file** e selezionare **impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="11da3-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="11da3-135">Verificare che **la piattaforma** sia impostata su **Windows Store**, che l' **SDK** sia impostato su **Universal 10**e impostare il **tipo di compilazione UWP** su **XAML**.</span><span class="sxs-lookup"><span data-stu-id="11da3-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="11da3-136">Nella finestra di dialogo **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore...**</span><span class="sxs-lookup"><span data-stu-id="11da3-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="11da3-137">Selezionare la scheda **impostazioni per Windows Store**</span><span class="sxs-lookup"><span data-stu-id="11da3-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="11da3-138">Espandi il gruppo **altre impostazioni**</span><span class="sxs-lookup"><span data-stu-id="11da3-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="11da3-139">Nella sezione **rendering** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco **dispositivi di realtà virtuale**</span><span class="sxs-lookup"><span data-stu-id="11da3-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="11da3-140">Assicurarsi che **Windows olografico** sia visualizzato nell'elenco degli SDK di realtà virtuale</span><span class="sxs-lookup"><span data-stu-id="11da3-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="11da3-141">Se la compilazione non viene contrassegnata come realtà virtuale supportata con il dispositivo HoloLens, il progetto viene esportato come app XAML 2D.</span><span class="sxs-lookup"><span data-stu-id="11da3-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="11da3-142">Uso della tastiera di sistema nell'app Unity</span><span class="sxs-lookup"><span data-stu-id="11da3-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="11da3-143">Dichiarare la tastiera</span><span class="sxs-lookup"><span data-stu-id="11da3-143">Declare the keyboard</span></span>

<span data-ttu-id="11da3-144">Nella classe dichiarare una variabile per archiviare *TouchScreenKeyboard* e una variabile per contenere la stringa restituita dalla tastiera.</span><span class="sxs-lookup"><span data-stu-id="11da3-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="11da3-145">Richiama la tastiera</span><span class="sxs-lookup"><span data-stu-id="11da3-145">Invoke the keyboard</span></span>

<span data-ttu-id="11da3-146">Quando si verifica un evento che richiede l'input da tastiera, chiamare una di queste funzioni a seconda del tipo di input desiderato.</span><span class="sxs-lookup"><span data-stu-id="11da3-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="11da3-147">Si noti che il titolo viene specificato nel parametro textPlaceholder.</span><span class="sxs-lookup"><span data-stu-id="11da3-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

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

### <a name="retrieve-typed-contents"></a><span data-ttu-id="11da3-148">Recupera contenuto tipizzato</span><span class="sxs-lookup"><span data-stu-id="11da3-148">Retrieve typed contents</span></span>

<span data-ttu-id="11da3-149">Nel ciclo di aggiornamento controllare se la tastiera ha ricevuto il nuovo input e archiviarlo per l'uso altrove.</span><span class="sxs-lookup"><span data-stu-id="11da3-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

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

## <a name="alternative-keyboard-options"></a><span data-ttu-id="11da3-150">Opzioni di tastiera alternative</span><span class="sxs-lookup"><span data-stu-id="11da3-150">Alternative keyboard options</span></span>

<span data-ttu-id="11da3-151">Si comprende che la disattivazione di una visualizzazione volumetrica in una visualizzazione 2D non è il modo ideale per ottenere l'input di testo dall'utente.</span><span class="sxs-lookup"><span data-stu-id="11da3-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="11da3-152">Le alternative attuali per sfruttare la tastiera di sistema tramite Unity includono:</span><span class="sxs-lookup"><span data-stu-id="11da3-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="11da3-153">Uso della dettatura vocale per l'input (<b>Nota:</b> si tratta spesso di un errore soggetto a parole non trovate nel dizionario e non è adatto per l'immissione della password)</span><span class="sxs-lookup"><span data-stu-id="11da3-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="11da3-154">Creare una tastiera che funzioni nella visualizzazione esclusiva delle applicazioni</span><span class="sxs-lookup"><span data-stu-id="11da3-154">Create a keyboard that works in your applications exclusive view</span></span>
