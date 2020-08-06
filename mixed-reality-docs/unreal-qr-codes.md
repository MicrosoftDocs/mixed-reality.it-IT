---
title: Codici a matrice in Unreal
description: Guida all'uso dei codici a matrice in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, codici a matrice
ms.openlocfilehash: a53fad14ab76136f1da419379dd39eca3a29701a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376103"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="91581-104">Codici a matrice in Unreal</span><span class="sxs-lookup"><span data-stu-id="91581-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="91581-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="91581-105">Overview</span></span>

<span data-ttu-id="91581-106">HoloLens 2 può individuare i codici a matrice in uno spazio del mondo reale usando la webcam, eseguendone il rendering come ologrammi mediante un sistema di coordinate nella posizione reale di ciascun nodo.</span><span class="sxs-lookup"><span data-stu-id="91581-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="91581-107">Oltre ai singoli codici a matrice, HoloLens 2 è in grado di eseguire il rendering degli ologrammi nella stessa posizione su più dispositivi per creare un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="91581-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="91581-108">Assicurati di seguire le procedure consigliate per l'aggiunta di codici a matrice alle tue applicazioni:</span><span class="sxs-lookup"><span data-stu-id="91581-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="91581-109">Zone silenziose</span><span class="sxs-lookup"><span data-stu-id="91581-109">Quiet zones</span></span>
- <span data-ttu-id="91581-110">Illuminazione e sfondo</span><span class="sxs-lookup"><span data-stu-id="91581-110">Lighting and backdrop</span></span>
- <span data-ttu-id="91581-111">Dimensione, distanza e posizione angolare</span><span class="sxs-lookup"><span data-stu-id="91581-111">Size, distance, and angular position</span></span>

<span data-ttu-id="91581-112">Presta particolare attenzione alle [considerazioni sull'ambiente](environment-considerations-for-hololens.md) quando vengono inseriti codici a matrice nell'app.</span><span class="sxs-lookup"><span data-stu-id="91581-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="91581-113">Per altre informazioni su questi argomenti e per istruzioni su come scaricare il pacchetto NuGet necessario, vedi il documento principale [Rilevamento di codici a matrice](qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="91581-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="91581-114">Abilitazione del rilevamento di codici a matrice</span><span class="sxs-lookup"><span data-stu-id="91581-114">Enabling QR detection</span></span>
<span data-ttu-id="91581-115">Dato che HoloLens 2 deve usare la webcam per visualizzare i codici a matrice, è necessario abilitarla nelle impostazioni del progetto:</span><span class="sxs-lookup"><span data-stu-id="91581-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="91581-116">Apri **Edit > Project Settings** (Modifica > Impostazioni progetto), scorri fino alla sezione **Platforms** (Piattaforme) e fai clic su **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="91581-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="91581-117">Espandi la sezione **Capabilities** (Funzionalità) e seleziona **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="91581-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="91581-118">Devi anche acconsentire esplicitamente al rilevamento dei codici a matrice [aggiungendo un asset ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="91581-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="91581-119">Prima dell'utilizzo è necessario abilitare manualmente il rilevamento chiamando `UHoloLensARFunctionLibrary::StartQRCodeCapture()`.</span><span class="sxs-lookup"><span data-stu-id="91581-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartQRCodeCapture()`.</span></span> <span data-ttu-id="91581-120">Dopo aver terminato il rilevamento dei codici a matrice, è necessario disabilitarlo tramite `UHoloLensARFunctionLibrary::StopCameraCapture()` per salvare le risorse del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="91581-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span> 

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="91581-121">Configurazione di un'immagine rilevata</span><span class="sxs-lookup"><span data-stu-id="91581-121">Setting up a tracked image</span></span>

<span data-ttu-id="91581-122">I codici a matrice vengono esposti tramite il sistema di geometria rilevata AR di Unreal come immagine rilevata.</span><span class="sxs-lookup"><span data-stu-id="91581-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="91581-123">Per procedere, è necessario:</span><span class="sxs-lookup"><span data-stu-id="91581-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="91581-124">Creare un progetto e aggiungere un componente **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="91581-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![Codice a matrice - AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="91581-126">Selezionare **ARTrackableNotify** ed espandere la sezione **Events** (Eventi) nel pannello **Details** (Dettagli).</span><span class="sxs-lookup"><span data-stu-id="91581-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![Eventi dei codici a matrice](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="91581-128">Fare clic su **+** accanto a **On Add Tracked Geometry** (All'aggiunta della geometria rilevata) per aggiungere il nodo in Event Graph (Grafico eventi).</span><span class="sxs-lookup"><span data-stu-id="91581-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="91581-129">L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="91581-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![Esempio di rendering dei codici a matrice](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="91581-131">Uso di un'immagine rilevata</span><span class="sxs-lookup"><span data-stu-id="91581-131">Using a tracked image</span></span>
<span data-ttu-id="91581-132">Il grafico degli eventi nell'immagine seguente mostra l'evento **OnUpdateTrackedImage** usato per eseguire il rendering di un punto al centro di un codice a matrice e stamparne i dati.</span><span class="sxs-lookup"><span data-stu-id="91581-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![Esempio di rendering dei codici a matrice](images/unreal-qr-render.PNG)

<span data-ttu-id="91581-134">Ecco cosa accade:</span><span class="sxs-lookup"><span data-stu-id="91581-134">Here's what's going on:</span></span>
1. <span data-ttu-id="91581-135">Prima di tutto, viene eseguito il cast dell'immagine rilevata in un codice **ARTrackedQRCode** per verificare che l'immagine aggiornata corrente sia un codice a matrice.</span><span class="sxs-lookup"><span data-stu-id="91581-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="91581-136">I dati codificati vengono recuperati dalla variabile **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="91581-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="91581-137">È possibile ottenere la parte superiore sinistra del codice a matrice dalla posizione di **GetLocalToWorldTransform** e le dimensioni con **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="91581-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="91581-138">È anche possibile [ottenere il sistema di coordinate per un codice a matrice](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) nel codice.</span><span class="sxs-lookup"><span data-stu-id="91581-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="91581-139">Ricerca dell'ID univoco</span><span class="sxs-lookup"><span data-stu-id="91581-139">Finding the unique ID</span></span>
<span data-ttu-id="91581-140">Ogni codice a matrice ha un ID GUID univoco. Per trovarlo:</span><span class="sxs-lookup"><span data-stu-id="91581-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="91581-141">Trascina e rilascia il segnaposto **As ARTracked QRCode** e cerca **Get Unique ID** (Ottieni ID univoco).</span><span class="sxs-lookup"><span data-stu-id="91581-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID dei codici a matrice](images/unreal-qr-guid.PNG)

<span data-ttu-id="91581-143">Le operazioni sui codici a matrice sono piuttosto complesse, quindi ci sono diversi aspetti da approfondire.</span><span class="sxs-lookup"><span data-stu-id="91581-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="91581-144">I collegamenti riportati di seguito consentono di accedere a informazioni più dettagliate a questo proposito.</span><span class="sxs-lookup"><span data-stu-id="91581-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="91581-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="91581-145">See also</span></span>
* [<span data-ttu-id="91581-146">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="91581-146">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="91581-147">Ologrammi</span><span class="sxs-lookup"><span data-stu-id="91581-147">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="91581-148">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="91581-148">Coordinate systems</span></span>](coordinate-systems.md)
