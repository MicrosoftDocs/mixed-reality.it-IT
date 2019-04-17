---
title: Nozioni fondamentali MR 101 - progetto completo con dispositivo
description: Seguire questa procedura dettagliata di scrittura del codice grazie a Unity, Visual Studio e HoloLens per apprendere le nozioni fondamentali di realtà mista di Windows.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, realtà mista ologrammi, academy, esercitazione
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599362"
---
>[!NOTE]
><span data-ttu-id="f5ea4-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f5ea4-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f5ea4-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f5ea4-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f5ea4-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f5ea4-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="f5ea4-110">Nozioni fondamentali di MR 101: Progetto completo con dispositivo</span><span class="sxs-lookup"><span data-stu-id="f5ea4-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="f5ea4-111">Questa esercitazione illustrerà un progetto completo, compilato in Unity, che illustra le funzionalità di realtà mista di Windows di core per HoloLens, incluse [estasiati](gaze.md), [movimenti](gestures.md), [inputvocale](voice-input.md), [spaziale audio](spatial-sound.md) e [mapping spaziale](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="f5ea4-112">L'esercitazione saranno necessari circa 1 ora.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="f5ea4-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="f5ea4-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f5ea4-114">Corso</span><span class="sxs-lookup"><span data-stu-id="f5ea4-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f5ea4-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f5ea4-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f5ea4-116"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="f5ea4-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="f5ea4-117">Nozioni fondamentali di MR 101: Progetto completo con dispositivo</span><span class="sxs-lookup"><span data-stu-id="f5ea4-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="f5ea4-118">✔️</span><span class="sxs-lookup"><span data-stu-id="f5ea4-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="f5ea4-119">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="f5ea4-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f5ea4-120">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="f5ea4-120">Prerequisites</span></span>

* <span data-ttu-id="f5ea4-121">Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="f5ea4-122">Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="f5ea4-123">File di progetto</span><span class="sxs-lookup"><span data-stu-id="f5ea4-123">Project files</span></span>

* <span data-ttu-id="f5ea4-124">Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) necessarie per il progetto.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="f5ea4-125"> Richiede Unity 2017.2 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="f5ea4-126">Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="f5ea4-127">Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="f5ea4-128">Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="f5ea4-129">Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="f5ea4-130">Mantenere il nome di cartella **Origami**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="f5ea4-131">Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="f5ea4-132">Capitolo 1 - world "Holo"</span><span class="sxs-lookup"><span data-stu-id="f5ea4-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="f5ea4-133">In questo capitolo verranno configurare il primo progetto Unity e procedere con la compilazione e processo di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="f5ea4-134">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f5ea4-134">Objectives</span></span>

* <span data-ttu-id="f5ea4-135">Configurare Unity per lo sviluppo holographic.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="f5ea4-136">Rendere ologramma.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-136">Make a hologram.</span></span>
* <span data-ttu-id="f5ea4-137">Vedere ologramma apportate.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="f5ea4-138">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f5ea4-138">Instructions</span></span>

* <span data-ttu-id="f5ea4-139">Avviare Unity.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-139">Start Unity.</span></span>
* <span data-ttu-id="f5ea4-140">Selezionare **aperto**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-140">Select **Open**.</span></span>
* <span data-ttu-id="f5ea4-141">Immettere il percorso come il **Origami** cartella è archiviato in precedenza di annullamento.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="f5ea4-142">Selezionare **Origami** e fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="f5ea4-143">Poiché il **Origami** progetto non contiene una scena, salvare la scena predefinita vuoto in un nuovo file usando: **File** / **Salva scena come**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="f5ea4-144">Denominare la nuova scena **Origami** e premere il **salvare** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="f5ea4-145">Programma di installazione la fotocamera virtuale principale</span><span class="sxs-lookup"><span data-stu-id="f5ea4-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="f5ea4-146">Nel **Pannello di gerarchia**, selezionare **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="f5ea4-147">Nel **Inspector** impostare la posizione di trasformazione **0, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="f5ea4-148">Trovare il **Cancella flag** proprietà e modificare l'elenco a discesa dal **Skybox** al **colore a tinta unita**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="f5ea4-149">Fare clic sui **sfondo** campo per aprire una selezione colori.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="f5ea4-150">Impostare **R, G, B e A** al **0**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="f5ea4-151">Programma di installazione della scena</span><span class="sxs-lookup"><span data-stu-id="f5ea4-151">Setup the scene</span></span>

* <span data-ttu-id="f5ea4-152">Nel **Pannello di gerarchia**, fare clic su **Create** e **Crea vuoto**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="f5ea4-153">Fare doppio clic su nuova **GameObject** e scegliere Rinomina.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="f5ea4-154">Rinominare gli elementi GameObject al **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="f5ea4-155">Dal **Vntana** cartella nel Pannello di progetto (espandere gli asset e selezionare Vntana o fare doppio clic sulla cartella Vntana nel Pannello di progetto):</span><span class="sxs-lookup"><span data-stu-id="f5ea4-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="f5ea4-156">Trascinare **Stage** nella gerarchia di un elemento figlio di **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="f5ea4-157">Trascinare **Sphere1** nella gerarchia di un elemento figlio di **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="f5ea4-158">Trascinare **Sphere2** nella gerarchia di un elemento figlio di **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="f5ea4-159">Fare doppio clic sul **luce direzionale** dell'oggetto nel **Pannello di gerarchia** e selezionare **Elimina**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="f5ea4-160">Dal **Vntana** cartella, trascinare **luci** nella radice del **gerarchia pannello**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="f5ea4-161">Nel **gerarchia**, selezionare la **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="f5ea4-162">Nel **Inspector**, impostare la posizione di trasformazione **0, -0,5, 2.0**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="f5ea4-163">Premere il **riprodurre** pulsante in Unity per visualizzare in anteprima il vntana.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="f5ea4-164">Si dovrebbero vedere gli oggetti di Origami nella finestra di anteprima.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="f5ea4-165">Premere **riprodurre** una seconda volta per arrestare la modalità di anteprima.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="f5ea4-166">Esporta il progetto di Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5ea4-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="f5ea4-167">Nella finestra Seleziona Unity **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="f5ea4-168">Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="f5ea4-169">Impostare **SDK** al **10 Universal** e **tipo di compilazione** al **D3D**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="f5ea4-170">Controllare **Unity C# progetti**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="f5ea4-171">Fare clic su **aggiungere scene Open** per aggiungere la scena.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="f5ea4-172">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-172">Click **Build**.</span></span>
* <span data-ttu-id="f5ea4-173">Nella finestra di Esplora file che viene visualizzato, creare un **nuova cartella** denominato "App".</span><span class="sxs-lookup"><span data-stu-id="f5ea4-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="f5ea4-174">Solo clic i **cartella App**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="f5ea4-175">Premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="f5ea4-176">Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="f5ea4-177">Aprire il **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-177">Open the **App** folder.</span></span>
* <span data-ttu-id="f5ea4-178">(Fare doppio clic) di Open **Origami.sln**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="f5ea4-179">Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **X86**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="f5ea4-180">Fare clic sulla freccia accanto al pulsante di dispositivo e selezionare **computer remoto** distribuire tramite Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="f5ea4-181">Impostare il **indirizzo** al nome o indirizzo IP di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="f5ea4-182">Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate** o chiedere a Cortana **"Ehi Cortana, qual è l'indirizzo IP?"**</span><span class="sxs-lookup"><span data-stu-id="f5ea4-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="f5ea4-183">Se il HoloLens è connesso tramite USB, è possibile selezionare invece **dispositivo** distribuire tramite USB.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="f5ea4-184">Lasciare il **modalità di autenticazione** impostata su **universale**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="f5ea4-185">Fare clic su **selezionare**</span><span class="sxs-lookup"><span data-stu-id="f5ea4-185">Click **Select**</span></span>

* <span data-ttu-id="f5ea4-186">Fare clic su **Debug > Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="f5ea4-187">Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="f5ea4-188">Il progetto di Origami sarà a questo punto compilare, distribuire di HoloLens e quindi eseguire.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="f5ea4-189">Inserire nella finestra di HoloLens e Guardatevi intorno per visualizzare il nuovo vntana.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="f5ea4-190">Capitolo 2 - sguardo</span><span class="sxs-lookup"><span data-stu-id="f5ea4-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="f5ea4-191">In questo capitolo verrà per introdurre il primo di tre modi di interagire con i vntana: [estasiati](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="f5ea4-192">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f5ea4-192">Objectives</span></span>

* <span data-ttu-id="f5ea4-193">Visualizzare lo sguardo utilizzando un cursore bloccato al mondo.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="f5ea4-194">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f5ea4-194">Instructions</span></span>

* <span data-ttu-id="f5ea4-195">Tornare al progetto Unity e chiudere la finestra Impostazioni di compilazione se è ancora aperto.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="f5ea4-196">Selezionare il **Vntana** cartella le **pannello progetto**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="f5ea4-197">Trascinare il **cursore** all'oggetto il **Pannello di gerarchia** a livello di radice.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="f5ea4-198">Fare doppio clic sulla **cursore** oggetto da ottenere un quadro più da vicino.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="f5ea4-199">Fare clic sui **script** cartella nel Pannello di progetto.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="f5ea4-200">Scegliere il **Create** sottomenu.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="f5ea4-201">Selezionare  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-201">Select **C# Script**.</span></span>
* <span data-ttu-id="f5ea4-202">Denominare lo script **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="f5ea4-203">Nota: Per il nome viene fatta distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="f5ea4-204">Non devi aggiungere l'estensione. cs.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="f5ea4-205">Selezionare il **cursore** dell'oggetto nel **Pannello di gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="f5ea4-206">Trascinare e rilasciare il **WorldCursor** basano gli script delle **Pannello di controllo**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="f5ea4-207">Fare doppio clic il **WorldCursor** script per aprirlo in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="f5ea4-208">Copiare e incollare questo codice nel **WorldCursor.cs** e **Salva tutto**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="f5ea4-209">Ricompilare l'app dalla **File > Impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="f5ea4-210">Tornare alla soluzione di Visual Studio usata in precedenza per distribuire il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="f5ea4-211">Selezionare "Ricarica tutto" quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="f5ea4-212">Fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="f5ea4-213">A questo punto Guardatevi intorno scena e notare come il cursore interagisce con la forma degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="f5ea4-214">Capitolo 3 - movimenti</span><span class="sxs-lookup"><span data-stu-id="f5ea4-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="f5ea4-215">In questo capitolo verrà aggiunto il supporto per [movimenti](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="f5ea4-216">Quando l'utente seleziona una sfera paper, ci assicureremo sfera rientrano attivando la gravità usando il motore di fisica di Unity.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="f5ea4-217">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f5ea4-217">Objectives</span></span>

* <span data-ttu-id="f5ea4-218">Controllare il vntana con il movimento di Select.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="f5ea4-219">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f5ea4-219">Instructions</span></span>

<span data-ttu-id="f5ea4-220">Si inizierà creando uno script, quindi in grado di rilevare il movimento di Select.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="f5ea4-221">Nel **gli script** cartella, creare uno script denominato **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="f5ea4-222">Trascinare il **GazeGestureManager** lo script nel **OrigamiCollection** oggetto nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="f5ea4-223">Aprire il **GazeGestureManager** genera script in Visual Studio e aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="f5ea4-224">Creare un altro script nella cartella Scripts, questa volta denominata **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="f5ea4-225">Espandere la **OrigamiCollection** oggetto nella visualizzazione gerarchica.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="f5ea4-226">Trascinare il **SphereCommands** nello script le **Sphere1** oggetto nel Pannello di gerarchia.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="f5ea4-227">Trascinare il **SphereCommands** nello script le **Sphere2** oggetto nel Pannello di gerarchia.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="f5ea4-228">Aprire lo script in Visual Studio per la modifica e sostituire il codice predefinito con questo:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="f5ea4-229">Esportare, compilare e distribuire l'app di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="f5ea4-230">Esaminare uno dei settori.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="f5ea4-231">Eseguire il movimento di seleziona e controllare la sfera rilasciarla sotto l'area.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="f5ea4-232">Capitolo 4 - voce</span><span class="sxs-lookup"><span data-stu-id="f5ea4-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="f5ea4-233">In questo capitolo verrà aggiunto il supporto per due [comandi vocali](voice-input.md): "Reimposta world" per restituire le sfere eliminate nel percorso originale, "Drop sphere" per rendere la sfera di fallback.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="f5ea4-234">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f5ea4-234">Objectives</span></span>

* <span data-ttu-id="f5ea4-235">Aggiungere comandi vocali sempre in ascolto in background.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="f5ea4-236">Creare un ologrammi che reagisce a un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="f5ea4-237">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f5ea4-237">Instructions</span></span>

* <span data-ttu-id="f5ea4-238">Nel **gli script** cartella, creare uno script denominato **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="f5ea4-239">Trascinare il **SpeechManager** nello script le **OrigamiCollection** oggetto nella gerarchia di</span><span class="sxs-lookup"><span data-stu-id="f5ea4-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="f5ea4-240">Aprire il **SpeechManager** script in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="f5ea4-241">Copiare e incollare questo codice nel **SpeechManager.cs** e **Salva tutto**:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="f5ea4-242">Aprire il **SphereCommands** script in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="f5ea4-243">Aggiornare lo script come segue:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-243">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="f5ea4-244">Esportare, compilare e distribuire l'app di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="f5ea4-245">Esaminare una delle seguenti settori e scelgo "**sfera Drop**".</span><span class="sxs-lookup"><span data-stu-id="f5ea4-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="f5ea4-246">Ad esempio "**reimpostare World**" per riportarle posizioni iniziali.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="f5ea4-247">Capitolo 5 - spaziale audio</span><span class="sxs-lookup"><span data-stu-id="f5ea4-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="f5ea4-248">In questo capitolo, si sarà aggiungere musica all'app e quindi attivare effetti sonori su determinate azioni.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="f5ea4-249">Utilizzeremo [spaziale audio](spatial-sound.md) per fornire un percorso specifico nello spazio 3D suoni.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="f5ea4-250">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f5ea4-250">Objectives</span></span>

* <span data-ttu-id="f5ea4-251">Ascolta vntana in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="f5ea4-252">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f5ea4-252">Instructions</span></span>

* <span data-ttu-id="f5ea4-253">Nella finestra Seleziona Unity dal menu in alto **Modifica > Impostazioni di progetto > Audio**</span><span class="sxs-lookup"><span data-stu-id="f5ea4-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="f5ea4-254">Nel Pannello di controllo a destra, trovare il **plug-in spaziale** impostazione e selezionare **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="f5ea4-255">Dal **Vntana** cartella nel Pannello di progetto, trascinare le **atmosfera** dell'oggetto nel **OrigamiCollection** oggetto nel Pannello di gerarchia.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="f5ea4-256">Selezionare **OrigamiCollection** e trovare il **origine Audio** componente nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="f5ea4-257">Modificare queste proprietà:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-257">Change these properties:</span></span>
  * <span data-ttu-id="f5ea4-258">Verificare i **Spatialize** proprietà.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="f5ea4-259">Verificare i **Ascolta al attivi**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="f5ea4-260">Change **Blend spaziali** al **3D** trascinando il dispositivo di scorrimento fino a destra.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="f5ea4-261">Il valore deve cambiare da 0 a 1 quando si sposta il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="f5ea4-262">Verificare i **ciclo** proprietà.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="f5ea4-263">Espandere **impostazioni 3D suono**e immettere **0,1** per **livello Doppler**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="f5ea4-264">Impostare **Volume attenuazione** al **attenuazione logaritmica**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="f5ea4-265">Impostare **distanza massima** al **20**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="f5ea4-266">Nel **gli script** cartella, creare uno script denominato **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="f5ea4-267">Trascinare e rilasciare **SphereSounds** per il **Sphere1** e **Sphere2** gli oggetti nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="f5ea4-268">Aprire **SphereSounds** in Visual Studio, aggiornare il codice seguente e **Salva tutto**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="f5ea4-269">Salvare lo script e tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="f5ea4-270">Esportare, compilare e distribuire l'app di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="f5ea4-271">Spostare più vicino e lontano dalla fase e attivare per affiancata lieti di ricevere i suoni modificare.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="f5ea4-272">Capitolo 6 - spaziali mapping</span><span class="sxs-lookup"><span data-stu-id="f5ea4-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="f5ea4-273">A questo punto si userà [mapping spaziale](spatial-mapping.md) per inserire la tavola da gioco in un oggetto reale nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="f5ea4-274">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f5ea4-274">Objectives</span></span>

* <span data-ttu-id="f5ea4-275">Rendere il mondo reale del mondo virtuale.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="f5ea4-276">Posizionare il vntana dove sono più importanti.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="f5ea4-277">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f5ea4-277">Instructions</span></span>

* <span data-ttu-id="f5ea4-278">In Unity, fare clic sui **Vntana** cartella nel Pannello di progetto.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="f5ea4-279">Trascinare il **Mapping spaziale** asset nella radice della **gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="f5ea4-280">Fare clic sui **Mapping spaziale** oggetto nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="f5ea4-281">Nel **Pannello di controllo**, modificare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="f5ea4-282">Verificare i **disegnare Visual trame** casella.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="f5ea4-283">Individuare **disegnare materiale** e fare clic sul cerchio nella parte destra.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="f5ea4-284">Tipo "**wireframe**" nel campo di ricerca nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="f5ea4-285">Fare clic sul risultato e quindi chiudere la finestra.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-285">Click on the result and then close the window.</span></span> <span data-ttu-id="f5ea4-286">Quando si esegue questa operazione, il valore per disegnare materiale deve ottenere impostato su Wireframe.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="f5ea4-287">Esportare, compilare e distribuire l'app di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="f5ea4-288">Quando si esegue l'app, una rete mesh di wireframe sovrapporrà del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="f5ea4-289">Guarda come una sfera in sequenza rientrerà il palco e al tetto minimo.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="f5ea4-290">A questo punto vi mostreremo come spostare il OrigamiCollection in una nuova posizione:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="f5ea4-291">Nel **gli script** cartella, creare uno script denominato **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="f5ea4-292">Nel **gerarchia**, espandere il **OrigamiCollection** e selezionare il **fase** oggetto.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="f5ea4-293">Trascinare il **TapToPlaceParent** script l'oggetto di fase.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="f5ea4-294">Aprire il **TapToPlaceParent** script in Visual Studio e aggiornarlo in modo da essere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="f5ea4-295">Esportare, compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="f5ea4-296">Ora sarà ora possibile posizionare il gioco in una posizione specifica, gazing analizzarlo, tramite il movimento di seleziona e quindi lo spostamento in una nuova posizione e utilizzando il movimento seleziona di nuovo.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="f5ea4-297">Capitolo 7 - divertente Holographic</span><span class="sxs-lookup"><span data-stu-id="f5ea4-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="f5ea4-298">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f5ea4-298">Objectives</span></span>

* <span data-ttu-id="f5ea4-299">Rivelare all'ingresso di un underworld holographic.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="f5ea4-300">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="f5ea4-300">Instructions</span></span>

<span data-ttu-id="f5ea4-301">A questo punto vi mostreremo come scoprire i underworld holographic:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="f5ea4-302">Dal **Vntana** cartella nel Pannello di progetto:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="f5ea4-303">Trascinare **Underworld** nella gerarchia di un elemento figlio di **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="f5ea4-304">Nel **gli script** cartella, creare uno script denominato **HitTarget**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="f5ea4-305">Nel **gerarchia**, espandere il **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="f5ea4-306">Espandere la **Stage** dell'oggetto e selezionare il **destinazione** oggetto (ventola blue).</span><span class="sxs-lookup"><span data-stu-id="f5ea4-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="f5ea4-307">Trascinare il **HitTarget** nello script le **destinazione** oggetto.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="f5ea4-308">Aprire il **HitTarget** script in Visual Studio e aggiornarlo in modo da essere quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="f5ea4-309">In Unity, selezionare la **destinazione** oggetto.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="f5ea4-310">Ora sono visibili in due proprietà pubbliche il **destinazione riscontri** componente ed è necessario per gli oggetti di riferimento nel nostro scena:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="f5ea4-311">Trascinare **Underworld** dal **gerarchia** pannello per il **Underworld** proprietà il **destinazione riscontri** componente.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="f5ea4-312">Trascinare **fase** dal **gerarchia** pannello per il **oggetto da nascondere** proprietà il **destinazione riscontri** componente.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="f5ea4-313">Esportare, compilare e distribuire l'app.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="f5ea4-314">Inserire l'insieme di Origami sul pavimento e quindi utilizzare il movimento di Select per eseguire una sfera drop.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="f5ea4-315">Quando la sfera raggiunge la destinazione (ventola blue), si verificherà un'esplosione.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="f5ea4-316">La raccolta verrà nascosto e verrà visualizzato un problema per il underworld.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="f5ea4-317">La fine</span><span class="sxs-lookup"><span data-stu-id="f5ea4-317">The end</span></span>

<span data-ttu-id="f5ea4-318">E questo è il termine di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="f5ea4-319">Si è appreso:</span><span class="sxs-lookup"><span data-stu-id="f5ea4-319">You learned:</span></span>

* <span data-ttu-id="f5ea4-320">Come creare un'app holographic in Unity.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="f5ea4-321">Come rendere utilizzare sguardo, movimento, vocali, audio e mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="f5ea4-322">Come compilare e distribuire un'app usando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="f5ea4-323">Si è ora pronti per iniziare a creare un'esperienza olografica.</span><span class="sxs-lookup"><span data-stu-id="f5ea4-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="f5ea4-324">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f5ea4-324">See also</span></span>

* [<span data-ttu-id="f5ea4-325">MR Basics 101E: Progetto completo con emulatore</span><span class="sxs-lookup"><span data-stu-id="f5ea4-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="f5ea4-326">Sguardo</span><span class="sxs-lookup"><span data-stu-id="f5ea4-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="f5ea4-327">Movimenti</span><span class="sxs-lookup"><span data-stu-id="f5ea4-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="f5ea4-328">Input vocale</span><span class="sxs-lookup"><span data-stu-id="f5ea4-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="f5ea4-329">Spaziale audio</span><span class="sxs-lookup"><span data-stu-id="f5ea4-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="f5ea4-330">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="f5ea4-330">Spatial mapping</span></span>](spatial-mapping.md)
