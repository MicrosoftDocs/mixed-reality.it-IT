---
title: 'Case study: Building HoloSketch, un layout spaziali e UX sketch di app per HoloLens'
description: HoloSketch è un layout spaziali sul dispositivo e dell'esperienza utente sketch strumento per HoloLens per la creazione di esperienze holographic.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, realtà mista di Windows, tracciare, app
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600133"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="45f6c-104">Case study: Building HoloSketch, un layout spaziali e UX sketch di app per HoloLens</span><span class="sxs-lookup"><span data-stu-id="45f6c-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="45f6c-105">HoloSketch è un layout spaziali sul dispositivo e dell'esperienza utente sketch strumento per HoloLens per la creazione di esperienze holographic.</span><span class="sxs-lookup"><span data-stu-id="45f6c-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="45f6c-106">HoloSketch funziona con un comandi da tastiera e mouse, nonché gesti e voce Bluetooth abbinata.</span><span class="sxs-lookup"><span data-stu-id="45f6c-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="45f6c-107">Lo scopo di HoloSketch è fornire uno strumento di layout dell'esperienza utente semplice per la visualizzazione rapida e di iterazione.</span><span class="sxs-lookup"><span data-stu-id="45f6c-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="45f6c-108">![HoloSketch: Un layout spaziali e UX sketch di app per HoloLens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="45f6c-109">*HoloSketch: layout spaziali e UX sketch di app per HoloLens*</span><span class="sxs-lookup"><span data-stu-id="45f6c-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="45f6c-110">![Uno strumento di layout dell'esperienza utente semplice per la visualizzazione rapida e di iterazione.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="45f6c-111">*Uno strumento di layout dell'esperienza utente semplice per la visualizzazione rapida e di iterazione*</span><span class="sxs-lookup"><span data-stu-id="45f6c-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="45f6c-112">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="45f6c-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="45f6c-113">Primitive per study rapido e scalabilità-creazione di prototipi</span><span class="sxs-lookup"><span data-stu-id="45f6c-113">Primitives for quick studies and scale-prototyping</span></span>

![Utilizzo delle forme primitive](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="45f6c-115">Usare le forme primitive per study massing rapido e scalabilità-creazione di prototipi.</span><span class="sxs-lookup"><span data-stu-id="45f6c-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="45f6c-116">Oggetti di importazione tramite OneDrive</span><span class="sxs-lookup"><span data-stu-id="45f6c-116">Import objects through OneDrive</span></span>

![importazione di oggetti](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="45f6c-118">Importare immagini PNG o JPG o oggetti FBX 3D (richiede la creazione di pacchetti in Unity) nello spazio di realtà mista tramite OneDrive.</span><span class="sxs-lookup"><span data-stu-id="45f6c-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="45f6c-119">Modificare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="45f6c-119">Manipulate objects</span></span>

![la modifica degli oggetti](images/manipulate-objects-640px.jpg)

<span data-ttu-id="45f6c-121">Modificare gli oggetti (spostamento/ruotare/scala) con un'interfaccia familiare oggetto 3D.</span><span class="sxs-lookup"><span data-stu-id="45f6c-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="45f6c-122">Bluetooth, mouse e tastiera, movimenti e i comandi vocali</span><span class="sxs-lookup"><span data-stu-id="45f6c-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![supporta Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="45f6c-124">HoloSketch supporta mouse e tastiera Bluetooth, movimenti e comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="45f6c-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="45f6c-125">Informazioni</span><span class="sxs-lookup"><span data-stu-id="45f6c-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="45f6c-126">Importanza della verifica della progettazione del dispositivo</span><span class="sxs-lookup"><span data-stu-id="45f6c-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="45f6c-127">Quando si progetta qualcosa per HoloLens, è importante sperimentare la progettazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="45f6c-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="45f6c-128">Una delle principali sfide nella progettazione delle app di realtà mista è che è difficile ottenere il senso di scalabilità, posizione e profondità, in particolare nelle tradizionali schizzi 2D.</span><span class="sxs-lookup"><span data-stu-id="45f6c-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="45f6c-129">Comunicazione basato sui costi di 2D</span><span class="sxs-lookup"><span data-stu-id="45f6c-129">Cost of 2D based communication</span></span>

<span data-ttu-id="45f6c-130">Per comunicare in modo efficace i flussi dell'esperienza utente e gli scenari ad altri utenti, una finestra di progettazione potrebbe avere un notevole dispendio di tempo di creazione di asset mediante gli strumenti tradizionali 2D, come Illustrator, Photoshop e PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="45f6c-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="45f6c-131">Questi progetti 2D spesso richiedono un impegno aggiuntivo per convertirli in 3D.</span><span class="sxs-lookup"><span data-stu-id="45f6c-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="45f6c-132">Alcune informazioni vengono perse in questa conversione da 2D a 3D.</span><span class="sxs-lookup"><span data-stu-id="45f6c-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="45f6c-133">Processo di distribuzione complesse</span><span class="sxs-lookup"><span data-stu-id="45f6c-133">Complex deployment process</span></span>

<span data-ttu-id="45f6c-134">Poiché realtà mista è una nuova area di disegno per noi, comporta molti tentativi ed errori e iterazione di progettazione per sua natura.</span><span class="sxs-lookup"><span data-stu-id="45f6c-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="45f6c-135">Finestra di progettazione che non hanno familiarità con gli strumenti, ad esempio Unity e Visual Studio, non è facile inserire un elemento tra loro in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="45f6c-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="45f6c-136">In genere è necessario seguire la procedura seguente per visualizzare la grafica 2D e 3D nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="45f6c-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="45f6c-137">Si tratta di una barriera di big data per i progettisti rapidamente l'iterazione sugli scenari e le idee.</span><span class="sxs-lookup"><span data-stu-id="45f6c-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="45f6c-138">![Processo di distribuzione complesse](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="45f6c-139">*Processo di distribuzione*</span><span class="sxs-lookup"><span data-stu-id="45f6c-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="45f6c-140">Processo semplificato con HoloSketch</span><span class="sxs-lookup"><span data-stu-id="45f6c-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="45f6c-141">Con HoloSketch, volevamo semplificare il processo senza coinvolgere gli strumenti di sviluppo e associazione del portale di dispositivo.</span><span class="sxs-lookup"><span data-stu-id="45f6c-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="45f6c-142">Uso di OneDrive, gli utenti possono facilmente attivare gli asset 2D e 3D HoloLens.</span><span class="sxs-lookup"><span data-stu-id="45f6c-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="45f6c-143">![Processo semplificato con HoloSketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="45f6c-144">*Processo semplificato con HoloSketch*</span><span class="sxs-lookup"><span data-stu-id="45f6c-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="45f6c-145">Incoraggiando la mentalità progettazione tridimensionale e soluzioni</span><span class="sxs-lookup"><span data-stu-id="45f6c-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="45f6c-146">Abbiamo pensato di che questo strumento darebbe finestre di progettazione un'opportunità di Esplora soluzioni in uno spazio tridimensionale realmente e non essere bloccato in 2D.</span><span class="sxs-lookup"><span data-stu-id="45f6c-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="45f6c-147">Non dovranno considerare creando un background 3D per l'interfaccia utente, poiché lo sfondo è di mondo reale in caso di Hololens.</span><span class="sxs-lookup"><span data-stu-id="45f6c-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="45f6c-148">HoloSketch offre un modo per i progettisti di esplorare facilmente progettazione 3D in Hololens.</span><span class="sxs-lookup"><span data-stu-id="45f6c-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="45f6c-149">Introduzione</span><span class="sxs-lookup"><span data-stu-id="45f6c-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="45f6c-150">Come importare immagini 2D JPG/PNG () in HoloSketch</span><span class="sxs-lookup"><span data-stu-id="45f6c-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="45f6c-151">Caricare immagini JPG/PNG per la cartella di OneDrive ' Documenti/HoloSketch'.</span><span class="sxs-lookup"><span data-stu-id="45f6c-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="45f6c-152">Dal menu di OneDrive nel HoloSketch, sarà possibile selezionare e copiare l'immagine nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="45f6c-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="45f6c-153">![L'importazione di immagini 2D](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="45f6c-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="45f6c-154">*Importazione di immagini e oggetti 3D tramite OneDrive*</span><span class="sxs-lookup"><span data-stu-id="45f6c-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="45f6c-155">Come importare oggetti 3D in HoloSketch</span><span class="sxs-lookup"><span data-stu-id="45f6c-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="45f6c-156">Prima di caricare la cartella di OneDrive, attenersi alla procedura seguente per creare un pacchetto di oggetti 3D in un bundle di asset di Unity.</span><span class="sxs-lookup"><span data-stu-id="45f6c-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="45f6c-157">Utilizzo di questo processo è possibile importare i file FBX/OBJ da software 3D come Maya, Cinema 4D e Microsoft Paint 3D.</span><span class="sxs-lookup"><span data-stu-id="45f6c-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="45f6c-158">Attualmente, la creazione di bundle di asset è supportata con Unity versione 5.4.5f1.</span><span class="sxs-lookup"><span data-stu-id="45f6c-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="45f6c-159">Scaricare e aprire il progetto di Unity ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="45f6c-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="45f6c-160">Questo progetto di Unity include lo script per la generazione di asset di bundle.</span><span class="sxs-lookup"><span data-stu-id="45f6c-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="45f6c-161">Creare un GameObject nuovo.</span><span class="sxs-lookup"><span data-stu-id="45f6c-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="45f6c-162">Denominare il GameObject basato sul contenuto.</span><span class="sxs-lookup"><span data-stu-id="45f6c-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="45f6c-163">Nel Pannello di controllo, fare clic su 'Aggiungi componente' e aggiungere 'Casella Collider'.</span><span class="sxs-lookup"><span data-stu-id="45f6c-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![Nel Pannello di controllo, fare clic su 'Aggiungi componente' e aggiungere 'Casella Collider'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Nel Pannello di controllo, fare clic su 'Aggiungi componente' e aggiungere 'Casella Collider' #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="45f6c-166">Importare il file FBX 3D trascinandolo nel Pannello di progetto.</span><span class="sxs-lookup"><span data-stu-id="45f6c-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="45f6c-167">Trascinare l'oggetto nel Pannello di gerarchia **sotto il nuovo GameObject**.</span><span class="sxs-lookup"><span data-stu-id="45f6c-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Trascinare l'oggetto nel Pannello di gerarchia sotto il nuovo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="45f6c-169">Regolare la dimensione collider se non corrisponde l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="45f6c-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="45f6c-170">Ruotare l'oggetto per affrontare **asse z**.</span><span class="sxs-lookup"><span data-stu-id="45f6c-170">Rotate the object to face **Z-axis**.</span></span>

   ![Regolare la dimensione collider se non corrisponde l'oggetto.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="45f6c-172">Trascinare l'oggetto dal Pannello di gerarchia al pannello di progetto per **renderlo prefab**.</span><span class="sxs-lookup"><span data-stu-id="45f6c-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="45f6c-173">Nella parte inferiore del Pannello di controllo, fare clic sul menu a discesa, creare e assegnare un nome univoco.</span><span class="sxs-lookup"><span data-stu-id="45f6c-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="45f6c-174">Esempio seguente illustra l'aggiunta e l'assegnazione 'brownchair' per il nome AssetBundle.</span><span class="sxs-lookup"><span data-stu-id="45f6c-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![Nella parte inferiore del Pannello di controllo, fare clic sul menu a discesa e assegnare un nuovo nome univoco.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="45f6c-176">Preparare un'immagine di anteprima per l'oggetto modello.</span><span class="sxs-lookup"><span data-stu-id="45f6c-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="45f6c-177">![Trascinare un'immagine nel Pannello di progetto e assegnare il nome utilizzato per l'oggetto.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="45f6c-178">Creare una cartella denominata 'Assetbundles' nella cartella 'Asset' del progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="45f6c-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="45f6c-179">Nel menu di asset, selezionare 'Build AssetBundles' per generare file.</span><span class="sxs-lookup"><span data-stu-id="45f6c-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="45f6c-180">![Nel menu di asset, selezionare 'Build AssetBundles' per generare file.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="45f6c-181">**Caricare il file generato nella cartella /Files/Documents/HoloSketch in OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="45f6c-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="45f6c-182">Caricare il file asset_unique_name solo.</span><span class="sxs-lookup"><span data-stu-id="45f6c-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="45f6c-183">Non si dovranno caricare file AssetBundles o i file manifesto.</span><span class="sxs-lookup"><span data-stu-id="45f6c-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="45f6c-184">![Aggiungere file al file/documenti/HoloSketch/cartella](images/holosketch-onedriveupload-1000px.png)
![verrà visualizzato un oggetto 3D aggiunto nel menu di OneDrive del HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="45f6c-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="45f6c-185">Come modificare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="45f6c-185">How to manipulate the objects</span></span>

<span data-ttu-id="45f6c-186">HoloSketch supporta l'interfaccia tradizionali che è ampiamente usato in 3D software.</span><span class="sxs-lookup"><span data-stu-id="45f6c-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="45f6c-187">È possibile utilizzare per spostare, ruotare, ridimensionare gli oggetti con i movimenti e un mouse.</span><span class="sxs-lookup"><span data-stu-id="45f6c-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="45f6c-188">È possibile passare rapidamente tra modalità diverse con vocali o della tastiera.</span><span class="sxs-lookup"><span data-stu-id="45f6c-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="45f6c-189">Modalità di manipolazione di oggetti</span><span class="sxs-lookup"><span data-stu-id="45f6c-189">Object manipulation modes</span></span>

<span data-ttu-id="45f6c-190">![Come modificare gli oggetti](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="45f6c-191">*Come modificare gli oggetti*</span><span class="sxs-lookup"><span data-stu-id="45f6c-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="45f6c-192">Menu contestuali e Tool Belt</span><span class="sxs-lookup"><span data-stu-id="45f6c-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="45f6c-193">**Tramite il menu di scelta rapida**</span><span class="sxs-lookup"><span data-stu-id="45f6c-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="45f6c-194">Indice puntato Double per aprire il menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="45f6c-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="45f6c-195">Voci di menu:</span><span class="sxs-lookup"><span data-stu-id="45f6c-195">Menu items:</span></span>
* <span data-ttu-id="45f6c-196">**Nell'area di layout:** Questo è un sistema di griglie 3D in cui è possibile modificare il layout più oggetti e gestirli come gruppo.</span><span class="sxs-lookup"><span data-stu-id="45f6c-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="45f6c-197">Double-indice puntato nell'area di Layout per aggiungervi gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="45f6c-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="45f6c-198">**Primitive:** Usare i cubi, sfere, cilindri e coni per massing studi.</span><span class="sxs-lookup"><span data-stu-id="45f6c-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="45f6c-199">**OneDrive:** Aprire il menu di OneDrive per importare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="45f6c-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="45f6c-200">**aiuto:** Visualizza la Guida dello schermo.</span><span class="sxs-lookup"><span data-stu-id="45f6c-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="45f6c-201">![Menu di scelta rapida](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="45f6c-202">*Menu di scelta rapida*</span><span class="sxs-lookup"><span data-stu-id="45f6c-202">*Contextual menu*</span></span>

<span data-ttu-id="45f6c-203">**Usando il Menu di Tool Belt**</span><span class="sxs-lookup"><span data-stu-id="45f6c-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="45f6c-204">Spostare, ruota, scalabilità, salvataggio e caricamento scena sono disponibili dal Menu Tool Belt.</span><span class="sxs-lookup"><span data-stu-id="45f6c-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="45f6c-205">Usando la tastiera, movimenti e comandi vocali</span><span class="sxs-lookup"><span data-stu-id="45f6c-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="45f6c-206">![Tastiera, movimenti e comandi vocali](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="45f6c-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="45f6c-207">*Tastiera, movimenti e comandi vocali*</span><span class="sxs-lookup"><span data-stu-id="45f6c-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="45f6c-208">Scarica l'app</span><span class="sxs-lookup"><span data-stu-id="45f6c-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="45f6c-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Scaricare e installare l'app HoloSketch gratuitamente da di Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="45f6c-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="45f6c-210">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="45f6c-210">Known issues</span></span>
* <span data-ttu-id="45f6c-211">Attualmente è supportata la creazione di bundle di asset con **5.4.5f1 versione di Unity.**</span><span class="sxs-lookup"><span data-stu-id="45f6c-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="45f6c-212">A seconda della quantità di dati in OneDrive, l'app potrebbe essere visualizzato come se è stato arrestato durante il caricamento del contenuto di OneDrive</span><span class="sxs-lookup"><span data-stu-id="45f6c-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="45f6c-213">Attualmente, salvare e caricare oggetti primitivi supporta solo funzionalità</span><span class="sxs-lookup"><span data-stu-id="45f6c-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="45f6c-214">Menu di testo, audio, Video e foto sono disabilitati nel menu di scelta rapida</span><span class="sxs-lookup"><span data-stu-id="45f6c-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="45f6c-215">Il pulsante Play del menu Tool Belt Cancella il gizmo manipulation</span><span class="sxs-lookup"><span data-stu-id="45f6c-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="45f6c-216">Le bozze di condivisione</span><span class="sxs-lookup"><span data-stu-id="45f6c-216">Sharing your sketches</span></span>

<span data-ttu-id="45f6c-217">È possibile usare la funzionalità di registrazione video in HoloLens, pronunciare "Ehi Cortana, la registrazione di Start/Stop '.</span><span class="sxs-lookup"><span data-stu-id="45f6c-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="45f6c-218">Premere il volume su/giù chiave insieme a scattare una foto dello sketch.</span><span class="sxs-lookup"><span data-stu-id="45f6c-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="45f6c-219">Informazioni sugli autori</span><span class="sxs-lookup"><span data-stu-id="45f6c-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="45f6c-220"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="45f6c-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="45f6c-221">UX Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="45f6c-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="45f6c-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="45f6c-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="45f6c-223">Per gli sviluppatori @Microsoft</span><span class="sxs-lookup"><span data-stu-id="45f6c-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
