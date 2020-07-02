---
title: Codici a matrice in Unreal
description: Guida all'uso dei codici a matrice in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, codici a matrice
ms.openlocfilehash: cf6c113f6bf4a13a96f46d6420a3093966455c3b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720387"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="38271-104">Codici a matrice in Unreal</span><span class="sxs-lookup"><span data-stu-id="38271-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="38271-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="38271-105">Overview</span></span>

<span data-ttu-id="38271-106">HoloLens 2 può individuare i codici a matrice in uno spazio del mondo reale usando la webcam, eseguendone il rendering come ologrammi mediante un sistema di coordinate nella posizione reale di ciascun nodo.</span><span class="sxs-lookup"><span data-stu-id="38271-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="38271-107">Oltre ai singoli codici a matrice, HoloLens 2 è in grado di eseguire il rendering degli ologrammi nella stessa posizione su più dispositivi per creare un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="38271-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="38271-108">Assicurati di seguire le procedure consigliate per l'aggiunta di codici a matrice alle tue applicazioni:</span><span class="sxs-lookup"><span data-stu-id="38271-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="38271-109">Zone silenziose</span><span class="sxs-lookup"><span data-stu-id="38271-109">Quiet zones</span></span>
- <span data-ttu-id="38271-110">Illuminazione e sfondo</span><span class="sxs-lookup"><span data-stu-id="38271-110">Lighting and backdrop</span></span>
- <span data-ttu-id="38271-111">Dimensione, distanza e posizione angolare</span><span class="sxs-lookup"><span data-stu-id="38271-111">Size, distance, and angular position</span></span>

<span data-ttu-id="38271-112">Presta particolare attenzione alle [considerazioni sull'ambiente](environment-considerations-for-hololens.md) quando vengono inseriti codici a matrice nell'app.</span><span class="sxs-lookup"><span data-stu-id="38271-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="38271-113">Per altre informazioni su questi argomenti e per istruzioni su come scaricare il pacchetto NuGet necessario, vedi il documento principale [Rilevamento di codici a matrice](qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="38271-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="38271-114">Abilitazione del rilevamento di codici a matrice</span><span class="sxs-lookup"><span data-stu-id="38271-114">Enabling QR detection</span></span>
<span data-ttu-id="38271-115">Dato che HoloLens 2 deve usare la webcam per visualizzare i codici a matrice, è necessario abilitarla nelle impostazioni del progetto:</span><span class="sxs-lookup"><span data-stu-id="38271-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="38271-116">Apri **Edit > Project Settings** (Modifica > Impostazioni progetto), scorri fino alla sezione **Platforms** (Piattaforme) e fai clic su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="38271-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="38271-117">Espandi la sezione **Capabilities** (Funzionalità) e seleziona **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="38271-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="38271-118">Devi anche acconsentire esplicitamente al rilevamento dei codici a matrice [aggiungendo un asset ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="38271-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="38271-119">Configurazione di un'immagine rilevata</span><span class="sxs-lookup"><span data-stu-id="38271-119">Setting up a tracked image</span></span>

<span data-ttu-id="38271-120">I codici a matrice vengono esposti tramite il sistema di geometria rilevata AR di Unreal come immagine rilevata.</span><span class="sxs-lookup"><span data-stu-id="38271-120">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="38271-121">Per procedere, è necessario:</span><span class="sxs-lookup"><span data-stu-id="38271-121">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="38271-122">Creare un progetto e aggiungere un componente **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="38271-122">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![Codice a matrice - AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="38271-124">Selezionare **ARTrackableNotify** ed espandere la sezione **Events** (Eventi) nel pannello **Details** (Dettagli).</span><span class="sxs-lookup"><span data-stu-id="38271-124">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![Eventi dei codici a matrice](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="38271-126">Fare clic su **+** accanto a **On Add Tracked Geometry** (All'aggiunta della geometria rilevata) per aggiungere il nodo in Event Graph (Grafico eventi).</span><span class="sxs-lookup"><span data-stu-id="38271-126">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="38271-127">L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="38271-127">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![Esempio di rendering dei codici a matrice](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="38271-129">Uso di un'immagine rilevata</span><span class="sxs-lookup"><span data-stu-id="38271-129">Using a tracked image</span></span>
<span data-ttu-id="38271-130">Il grafico degli eventi nell'immagine seguente mostra l'evento **OnUpdateTrackedImage** usato per eseguire il rendering di un punto al centro di un codice a matrice e stamparne i dati.</span><span class="sxs-lookup"><span data-stu-id="38271-130">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![Esempio di rendering dei codici a matrice](images/unreal-qr-render.PNG)

<span data-ttu-id="38271-132">Ecco cosa accade:</span><span class="sxs-lookup"><span data-stu-id="38271-132">Here's what's going on:</span></span>
1. <span data-ttu-id="38271-133">Prima di tutto, viene eseguito il cast dell'immagine rilevata in un codice **ARTrackedQRCode** per verificare che l'immagine aggiornata corrente sia un codice a matrice.</span><span class="sxs-lookup"><span data-stu-id="38271-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="38271-134">I dati codificati vengono recuperati dalla variabile **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="38271-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="38271-135">È possibile ottenere la parte superiore sinistra del codice a matrice dalla posizione di **GetLocalToWorldTransform** e le dimensioni con **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="38271-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="38271-136">È anche possibile [ottenere il sistema di coordinate per un codice a matrice](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) nel codice.</span><span class="sxs-lookup"><span data-stu-id="38271-136">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="38271-137">Ricerca dell'ID univoco</span><span class="sxs-lookup"><span data-stu-id="38271-137">Finding the unique ID</span></span>
<span data-ttu-id="38271-138">Ogni codice a matrice ha un ID GUID univoco. Per trovarlo:</span><span class="sxs-lookup"><span data-stu-id="38271-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="38271-139">Trascina e rilascia il segnaposto **As ARTracked QRCode** e cerca **Get Unique ID** (Ottieni ID univoco).</span><span class="sxs-lookup"><span data-stu-id="38271-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID dei codici a matrice](images/unreal-qr-guid.PNG)

<span data-ttu-id="38271-141">Le operazioni sui codici a matrice sono piuttosto complesse, quindi ci sono diversi aspetti da approfondire.</span><span class="sxs-lookup"><span data-stu-id="38271-141">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="38271-142">I collegamenti riportati di seguito consentono di accedere a informazioni più dettagliate a questo proposito.</span><span class="sxs-lookup"><span data-stu-id="38271-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="38271-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="38271-143">See also</span></span>
* [<span data-ttu-id="38271-144">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="38271-144">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="38271-145">Ologrammi</span><span class="sxs-lookup"><span data-stu-id="38271-145">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="38271-146">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="38271-146">Coordinate systems</span></span>](coordinate-systems.md)