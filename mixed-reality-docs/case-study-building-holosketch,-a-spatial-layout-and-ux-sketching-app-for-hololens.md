---
title: Case Study-compilazione di HoloSketch, un layout spaziale e un'app per lo sketch di UX per HoloLens
description: HoloSketch è un layout spaziale su dispositivo e uno strumento di schizzo UX per HoloLens per aiutare a creare esperienze olografiche.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, realtà mista di Windows, sketching, app
ms.openlocfilehash: d6d22aae7709bcc1a33b142a100d1a0f9645d3cc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436951"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="89a9c-104">Case Study-compilazione di HoloSketch, un layout spaziale e un'app per lo sketch di UX per HoloLens</span><span class="sxs-lookup"><span data-stu-id="89a9c-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="89a9c-105">HoloSketch è un layout spaziale su dispositivo e uno strumento di schizzo UX per HoloLens per aiutare a creare esperienze olografiche.</span><span class="sxs-lookup"><span data-stu-id="89a9c-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="89a9c-106">HoloSketch funziona con una tastiera e un mouse Bluetooth abbinati, nonché comandi di movimento e voce.</span><span class="sxs-lookup"><span data-stu-id="89a9c-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="89a9c-107">Lo scopo di HoloSketch è fornire un semplice strumento di layout UX per la visualizzazione e l'iterazione rapide.</span><span class="sxs-lookup"><span data-stu-id="89a9c-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="89a9c-108">![HoloSketch: un layout spaziale e un'app di sketch di UX per HoloLens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="89a9c-109">*HoloSketch: layout spaziale e app di sketch di UX per HoloLens*</span><span class="sxs-lookup"><span data-stu-id="89a9c-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="89a9c-110">![un semplice strumento di layout UX per la visualizzazione e l'iterazione rapide.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="89a9c-111">*Semplice strumento di layout UX per la visualizzazione e l'iterazione rapide*</span><span class="sxs-lookup"><span data-stu-id="89a9c-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="89a9c-112">Caratteristiche</span><span class="sxs-lookup"><span data-stu-id="89a9c-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="89a9c-113">Primitive per gli studi rapidi e la creazione di prototipi di scalabilità</span><span class="sxs-lookup"><span data-stu-id="89a9c-113">Primitives for quick studies and scale-prototyping</span></span>

![Uso di forme primitive](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="89a9c-115">Usare forme primitive per gli studi di massa rapida e la creazione di prototipi di scalabilità.</span><span class="sxs-lookup"><span data-stu-id="89a9c-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="89a9c-116">Importare oggetti tramite OneDrive</span><span class="sxs-lookup"><span data-stu-id="89a9c-116">Import objects through OneDrive</span></span>

![importazione di oggetti](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="89a9c-118">Importa le immagini PNG/JPG o gli oggetti FBX 3D (richiede la creazione di pacchetti in Unity) nello spazio di realtà misto attraverso OneDrive.</span><span class="sxs-lookup"><span data-stu-id="89a9c-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="89a9c-119">Modificare oggetti</span><span class="sxs-lookup"><span data-stu-id="89a9c-119">Manipulate objects</span></span>

![manipolazione di oggetti](images/manipulate-objects-640px.jpg)

<span data-ttu-id="89a9c-121">Modificare gli oggetti (spostamento/rotazione/ridimensionamento) con una nota interfaccia oggetto 3D.</span><span class="sxs-lookup"><span data-stu-id="89a9c-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="89a9c-122">Bluetooth, mouse/tastiera, movimenti e comandi vocali</span><span class="sxs-lookup"><span data-stu-id="89a9c-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![supporta Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="89a9c-124">HoloSketch supporta mouse/tastiera, movimenti e comandi vocali Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="89a9c-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="89a9c-125">Informazioni</span><span class="sxs-lookup"><span data-stu-id="89a9c-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="89a9c-126">Importanza dell'esperienza di progettazione nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="89a9c-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="89a9c-127">Quando si progetta un elemento per HoloLens, è importante sperimentare la progettazione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="89a9c-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="89a9c-128">Una delle principali difficoltà nella progettazione di app in realtà mista è che è difficile ottenere la scalabilità, la posizione e la profondità, soprattutto tramite gli schizzi 2D tradizionali.</span><span class="sxs-lookup"><span data-stu-id="89a9c-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="89a9c-129">Costo della comunicazione basata su 2D</span><span class="sxs-lookup"><span data-stu-id="89a9c-129">Cost of 2D based communication</span></span>

<span data-ttu-id="89a9c-130">Per comunicare efficacemente flussi e scenari UX ad altri, una finestra di progettazione può dedicare molto tempo alla creazione di asset usando strumenti 2D tradizionali come Illustrator, Photoshop e PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="89a9c-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="89a9c-131">Queste progettazioni 2D richiedono spesso ulteriori sforzi per convertirle in 3D.</span><span class="sxs-lookup"><span data-stu-id="89a9c-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="89a9c-132">Alcune idee vengono perse in questa conversione da 2D a 3D.</span><span class="sxs-lookup"><span data-stu-id="89a9c-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="89a9c-133">Processo di distribuzione complesso</span><span class="sxs-lookup"><span data-stu-id="89a9c-133">Complex deployment process</span></span>

<span data-ttu-id="89a9c-134">Poiché la realtà mista è una nuova area di disegno, comporta una grande quantità di iterazioni di progettazione e di prova ed errori per natura.</span><span class="sxs-lookup"><span data-stu-id="89a9c-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="89a9c-135">Per le finestre di progettazione che non hanno familiarità con strumenti quali Unity e Visual Studio, non è facile inserire un elemento in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89a9c-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="89a9c-136">In genere è necessario eseguire il processo seguente per visualizzare le immagini 2D/3D nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="89a9c-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="89a9c-137">Si tratta di un grande ostacolo per i progettisti che scorrono rapidamente idee e scenari.</span><span class="sxs-lookup"><span data-stu-id="89a9c-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="89a9c-138">![processo di distribuzione complesso](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="89a9c-139">*Processo di distribuzione*</span><span class="sxs-lookup"><span data-stu-id="89a9c-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="89a9c-140">Processo semplificato con HoloSketch</span><span class="sxs-lookup"><span data-stu-id="89a9c-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="89a9c-141">Con HoloSketch è stato voluto semplificare questo processo senza coinvolgere gli strumenti di sviluppo e l'associazione del portale per i dispositivi.</span><span class="sxs-lookup"><span data-stu-id="89a9c-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="89a9c-142">Con OneDrive, gli utenti possono inserire facilmente risorse 2D/3D in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89a9c-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="89a9c-143">![processo semplificato con HoloSketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="89a9c-144">*Processo semplificato con HoloSketch*</span><span class="sxs-lookup"><span data-stu-id="89a9c-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="89a9c-145">Incoraggiare le soluzioni e i Thinking di progettazione tridimensionali</span><span class="sxs-lookup"><span data-stu-id="89a9c-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="89a9c-146">Abbiamo pensato che questo strumento darebbe ai progettisti la possibilità di esplorare le soluzioni in uno spazio effettivamente tridimensionale e di non rimanere bloccati in 2D.</span><span class="sxs-lookup"><span data-stu-id="89a9c-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="89a9c-147">Non è necessario considerare la creazione di uno sfondo 3D per la propria interfaccia utente, poiché lo sfondo è il mondo reale nel caso di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89a9c-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of HoloLens.</span></span> <span data-ttu-id="89a9c-148">HoloSketch apre una soluzione che consente ai progettisti di esplorare facilmente la progettazione 3D in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89a9c-148">HoloSketch opens up a way for designers to easily explore 3D design on HoloLens.</span></span>

## <a name="get-started"></a><span data-ttu-id="89a9c-149">Inizia subito</span><span class="sxs-lookup"><span data-stu-id="89a9c-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="89a9c-150">Come importare immagini 2D (JPG/PNG) in HoloSketch</span><span class="sxs-lookup"><span data-stu-id="89a9c-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="89a9c-151">Caricare le immagini JPG/PNG nella cartella OneDrive "Documents/HoloSketch".</span><span class="sxs-lookup"><span data-stu-id="89a9c-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="89a9c-152">Dal menu OneDrive in HoloSketch sarà possibile selezionare e inserire l'immagine nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="89a9c-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="89a9c-153">![importazione di immagini 2D](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="89a9c-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="89a9c-154">*Importazione di immagini e oggetti 3D tramite OneDrive*</span><span class="sxs-lookup"><span data-stu-id="89a9c-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="89a9c-155">Come importare oggetti 3D in HoloSketch</span><span class="sxs-lookup"><span data-stu-id="89a9c-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="89a9c-156">Prima di caricare nella cartella OneDrive, attenersi alla procedura seguente per creare un pacchetto degli oggetti 3D in un bundle di asset Unity.</span><span class="sxs-lookup"><span data-stu-id="89a9c-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="89a9c-157">Con questo processo è possibile importare i file FBX/OBJ dal software 3D, ad esempio Maya, cinema 4D e Microsoft Paint 3D.</span><span class="sxs-lookup"><span data-stu-id="89a9c-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="89a9c-158">Attualmente la creazione di bundle di asset è supportata con Unity Version 5.4.5 F1.</span><span class="sxs-lookup"><span data-stu-id="89a9c-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="89a9c-159">Scaricare e aprire il progetto Unity [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="89a9c-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="89a9c-160">Questo progetto Unity include lo script per la generazione di asset bundle.</span><span class="sxs-lookup"><span data-stu-id="89a9c-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="89a9c-161">Creare un nuovo GameObject.</span><span class="sxs-lookup"><span data-stu-id="89a9c-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="89a9c-162">Denominare il GameObject in base al contenuto.</span><span class="sxs-lookup"><span data-stu-id="89a9c-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="89a9c-163">Nel pannello di controllo fare clic su' Aggiungi componente ' e aggiungere ' box Collider '.</span><span class="sxs-lookup"><span data-stu-id="89a9c-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![Nel pannello di controllo fare clic su' Aggiungi componente ' e aggiungere ' box Collider '](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Nel pannello di controllo fare clic su' Aggiungi componente ' e aggiungere ' box Collider ' #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="89a9c-166">Importare il file FBX 3D trascinandolo nel pannello del progetto.</span><span class="sxs-lookup"><span data-stu-id="89a9c-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="89a9c-167">Trascinare l'oggetto nel pannello gerarchia **sotto il nuovo GameObject**.</span><span class="sxs-lookup"><span data-stu-id="89a9c-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Trascinare l'oggetto nel pannello gerarchia sotto il nuovo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="89a9c-169">Modificare la dimensione del Collider se non corrisponde all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="89a9c-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="89a9c-170">Ruotare l'oggetto sull' **asse Z**.</span><span class="sxs-lookup"><span data-stu-id="89a9c-170">Rotate the object to face **Z-axis**.</span></span>

   ![Modificare la dimensione del Collider se non corrisponde all'oggetto.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="89a9c-172">Trascinare l'oggetto dal pannello gerarchia al pannello del progetto per **renderlo prefabbricato**.</span><span class="sxs-lookup"><span data-stu-id="89a9c-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="89a9c-173">Nella parte inferiore del pannello Inspector fare clic sull'elenco a discesa, creare e assegnare un nuovo nome univoco.</span><span class="sxs-lookup"><span data-stu-id="89a9c-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="89a9c-174">Nell'esempio seguente viene illustrato come aggiungere e assegnare "brownchair" per il nome AssetBundle.</span><span class="sxs-lookup"><span data-stu-id="89a9c-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![Nella parte inferiore del pannello Inspector fare clic sull'elenco a discesa e assegnare un nuovo nome univoco.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="89a9c-176">Preparare un'immagine di anteprima per l'oggetto modello.</span><span class="sxs-lookup"><span data-stu-id="89a9c-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="89a9c-177">![trascinare un'immagine nel pannello del progetto e assegnare il nome usato per l'oggetto.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="89a9c-178">Creare una cartella denominata "Assetbundles" nella cartella "asset" del progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="89a9c-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="89a9c-179">Dal menu Asset selezionare ' compila AssetBundles ' per generare il file.</span><span class="sxs-lookup"><span data-stu-id="89a9c-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="89a9c-180">![dal menu asset, selezionare ' compila AssetBundles ' per generare il file.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="89a9c-181">**Caricare il file generato nella cartella/Files/Documents/HoloSketch in OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="89a9c-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="89a9c-182">Caricare solo il file di asset_unique_name.</span><span class="sxs-lookup"><span data-stu-id="89a9c-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="89a9c-183">Non è necessario caricare file manifesto o file AssetBundles.</span><span class="sxs-lookup"><span data-stu-id="89a9c-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="89a9c-184">![aggiungere file a file/documenti/HoloSketch/cartella](images/holosketch-onedriveupload-1000px.png)
![viene visualizzato un oggetto 3D aggiunto nel menu OneDrive di HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="89a9c-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="89a9c-185">Come modificare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="89a9c-185">How to manipulate the objects</span></span>

<span data-ttu-id="89a9c-186">HoloSketch supporta l'interfaccia tradizionale ampiamente utilizzata nel software 3D.</span><span class="sxs-lookup"><span data-stu-id="89a9c-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="89a9c-187">È possibile utilizzare Sposta, ruota, ridimensionare gli oggetti con movimenti e mouse.</span><span class="sxs-lookup"><span data-stu-id="89a9c-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="89a9c-188">È possibile passare rapidamente da una modalità all'altra con la voce o la tastiera.</span><span class="sxs-lookup"><span data-stu-id="89a9c-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="89a9c-189">Modalità di manipolazione degli oggetti</span><span class="sxs-lookup"><span data-stu-id="89a9c-189">Object manipulation modes</span></span>

<span data-ttu-id="89a9c-190">![come modificare gli oggetti](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="89a9c-191">*Come modificare gli oggetti*</span><span class="sxs-lookup"><span data-stu-id="89a9c-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="89a9c-192">Menu contestuale e barra degli strumenti</span><span class="sxs-lookup"><span data-stu-id="89a9c-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="89a9c-193">**Uso del menu contestuale**</span><span class="sxs-lookup"><span data-stu-id="89a9c-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="89a9c-194">Toccare aria doppia per aprire il menu contestuale.</span><span class="sxs-lookup"><span data-stu-id="89a9c-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="89a9c-195">Voci di menu:</span><span class="sxs-lookup"><span data-stu-id="89a9c-195">Menu items:</span></span>
* <span data-ttu-id="89a9c-196">**Superficie layout:** Si tratta di un sistema Grid 3D in cui è possibile disporre più oggetti e gestirli come un gruppo.</span><span class="sxs-lookup"><span data-stu-id="89a9c-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="89a9c-197">Toccare aria doppia sull'area del layout per aggiungere oggetti.</span><span class="sxs-lookup"><span data-stu-id="89a9c-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="89a9c-198">**Primitive:** Usare cubi, sfere, cilindri e coni per gli studi di massa.</span><span class="sxs-lookup"><span data-stu-id="89a9c-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="89a9c-199">**OneDrive:** Aprire il menu OneDrive per importare gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="89a9c-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="89a9c-200">**Guida:** Visualizza la schermata della guida.</span><span class="sxs-lookup"><span data-stu-id="89a9c-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="89a9c-201">![menu contestuale](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="89a9c-202">*Menu contestuale*</span><span class="sxs-lookup"><span data-stu-id="89a9c-202">*Contextual menu*</span></span>

<span data-ttu-id="89a9c-203">**Uso del menu della barra degli strumenti**</span><span class="sxs-lookup"><span data-stu-id="89a9c-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="89a9c-204">Spostare, ruotare, ridimensionare, salvare e caricare la scena sono disponibili dal menu della barra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="89a9c-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="89a9c-205">Uso di tasti di scelta rapida, movimenti e comandi vocali</span><span class="sxs-lookup"><span data-stu-id="89a9c-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="89a9c-206">![tastiera, movimenti e comandi vocali](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="89a9c-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="89a9c-207">*Tastiera, movimenti e comandi vocali*</span><span class="sxs-lookup"><span data-stu-id="89a9c-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="89a9c-208">Scarica l'app</span><span class="sxs-lookup"><span data-stu-id="89a9c-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="89a9c-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Scaricare e installare gratuitamente l'app HoloSketch dalla Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="89a9c-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="89a9c-210">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="89a9c-210">Known issues</span></span>
* <span data-ttu-id="89a9c-211">La creazione del bundle di asset è attualmente supportata con **Unity Version 5.4.5 F1.**</span><span class="sxs-lookup"><span data-stu-id="89a9c-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="89a9c-212">A seconda della quantità di dati nel OneDrive, l'app potrebbe apparire come se fosse stata arrestata durante il caricamento del contenuto di OneDrive</span><span class="sxs-lookup"><span data-stu-id="89a9c-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="89a9c-213">Attualmente, la funzionalità Salva e carica supporta solo oggetti primitivi</span><span class="sxs-lookup"><span data-stu-id="89a9c-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="89a9c-214">Menu di testo, audio, video e foto sono disabilitati nel menu contestuale</span><span class="sxs-lookup"><span data-stu-id="89a9c-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="89a9c-215">Il pulsante Riproduci nel menu della barra degli strumenti Cancella i gizmo di manipolazione</span><span class="sxs-lookup"><span data-stu-id="89a9c-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="89a9c-216">Condivisione degli sketch</span><span class="sxs-lookup"><span data-stu-id="89a9c-216">Sharing your sketches</span></span>

<span data-ttu-id="89a9c-217">È possibile usare la funzionalità di registrazione video in HoloLens dicendo ' Hey Cortana, Start/Stop Registration '.</span><span class="sxs-lookup"><span data-stu-id="89a9c-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="89a9c-218">Premere il tasto di scorrimento/discesa del volume per scattare un'immagine dello schizzo.</span><span class="sxs-lookup"><span data-stu-id="89a9c-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="89a9c-219">Informazioni sugli autori</span><span class="sxs-lookup"><span data-stu-id="89a9c-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="89a9c-220"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="89a9c-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="89a9c-221">Progettazione UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="89a9c-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="89a9c-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="89a9c-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="89a9c-223">@Microsoft per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="89a9c-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
