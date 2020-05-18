---
title: Codici a matrice in Unreal
description: Guida all'uso dei codici a matrice in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, codici a matrice
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342659"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="9d9d4-104">Codici a matrice in Unreal</span><span class="sxs-lookup"><span data-stu-id="9d9d4-104">QR codes in Unreal</span></span>

<span data-ttu-id="9d9d4-105">HoloLens può individuare i codici a matrice in uno spazio del mondo reale per il rendering degli ologrammi in posizioni note del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-105">HoloLens can locate QR codes in world space to render holograms at known positions in the real world.</span></span>  <span data-ttu-id="9d9d4-106">Questi codici possono essere usati anche per eseguire il rendering degli ologrammi su più dispositivi nella stessa posizione, in modo da creare un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-106">This can also be used to render holograms on multiple devices in the same location to create a shared experience.</span></span> 

<span data-ttu-id="9d9d4-107">Per abilitare il rilevamento a matrice in HoloLens, verifica che la funzionalità Webcam sia selezionata nell'editor di Unreal in Project Settings > Platform > HoloLens > Capabilities (Impostazioni progetto > Piattaforma > HoloLens > Funzionalità).</span><span class="sxs-lookup"><span data-stu-id="9d9d4-107">To enable QR detection on HoloLens, ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="9d9d4-108">Puoi acconsentire esplicitamente all'uso del rilevamento dei codici a matrice in Unreal avviando ARSession con la funzione StartARSession.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-108">Opt into using QR code tracking in Unreal by starting an ARSession with the StartARSession function.</span></span> 

<span data-ttu-id="9d9d4-109">I codici a matrice vengono esposti tramite il sistema di geometria rilevata AR di Unreal come immagine rilevata.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-109">QR Codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span>  <span data-ttu-id="9d9d4-110">Per usare questo sistema, aggiungi un componente AR Trackable Notify a un attore del progetto:</span><span class="sxs-lookup"><span data-stu-id="9d9d4-110">To use this, add an AR Trackable Notify component to a Blueprint actor:</span></span> 

![Codice a matrice - AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="9d9d4-112">Passa quindi ai dettagli del componente e fai clic sul pulsante verde "+" per selezionare gli eventi da monitorare.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-112">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span>  

![Eventi dei codici a matrice](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="9d9d4-114">In questo esempio, abbiamo effettuato la sottoscrizione a OnUpdateTrackedImage per eseguire il rendering di un punto al centro di un codice a matrice e stampare i dati codificati del codice a matrice.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-114">Here, we have subscribed to OnUpdateTrackedImage to render a point in the center of a QR Code and print the QR code’s encoded data.</span></span> 

![Esempio di rendering dei codici a matrice](images/unreal-qr-render.PNG)

<span data-ttu-id="9d9d4-116">Esegui innanzitutto il cast dell'immagine rilevata in un codice ARTrackedQRCode, per verificare che l'immagine aggiornata corrente sia un codice a matrice.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-116">First cast the tracked image to an ARTrackedQRCode to verify that the current updated image is a QR code.</span></span>  <span data-ttu-id="9d9d4-117">I dati codificati possono quindi essere recuperati con la variabile QRCode.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-117">Then the encoded data can be retrieved with the QRCode variable.</span></span>  <span data-ttu-id="9d9d4-118">La parte superiore sinistra del codice a matrice può essere recuperata dalla posizione di GetLocalToWorldTransform.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-118">The top-left of the QR code can be retrieved from the location of GetLocalToWorldTransform.</span></span>  <span data-ttu-id="9d9d4-119">Le dimensioni possono essere recuperate con GetEstimateSize.</span><span class="sxs-lookup"><span data-stu-id="9d9d4-119">The dimensions can be retrieved with GetEstimateSize.</span></span> 

<span data-ttu-id="9d9d4-120">Ogni codice a matrice ha anche un ID GUID univoco:</span><span class="sxs-lookup"><span data-stu-id="9d9d4-120">Every QR code also has a unique guid ID:</span></span> 

![GUID dei codici a matrice](images/unreal-qr-guid.PNG)

## <a name="see-also"></a><span data-ttu-id="9d9d4-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9d9d4-122">See also</span></span>
* [<span data-ttu-id="9d9d4-123">Rilevamento di codici a matrice</span><span class="sxs-lookup"><span data-stu-id="9d9d4-123">QR code tracking</span></span>](qr-code-tracking.md)
