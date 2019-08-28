---
title: Rilevamento del codice a matrice
description: Informazioni su come rilevare i codici a matrice in HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, location based Entertainment, VR Arcade, Arcade, immersive, QR, QR code, hololens2
ms.openlocfilehash: 736ab265db2145dd784c435e525059ed3a2fcbbb
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047162"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="ca266-104">Rilevamento del codice a matrice</span><span class="sxs-lookup"><span data-stu-id="ca266-104">QR code tracking</span></span>

<span data-ttu-id="ca266-105">HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente intorno all'auricolare, stabilendo un sistema di coordinate in base alla posizione reale del codice.</span><span class="sxs-lookup"><span data-stu-id="ca266-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="ca266-106">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="ca266-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ca266-107">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="ca266-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="ca266-108"><a href="hololens-hardware-details.md">HoloLens (prima generazione)</a></span><span class="sxs-lookup"><span data-stu-id="ca266-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="ca266-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ca266-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="ca266-110"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="ca266-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ca266-111">Rilevamento del codice a matrice</span><span class="sxs-lookup"><span data-stu-id="ca266-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="ca266-112">️</span><span class="sxs-lookup"><span data-stu-id="ca266-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ca266-113">✔️</span><span class="sxs-lookup"><span data-stu-id="ca266-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ca266-114">Vedere la nota</span><span class="sxs-lookup"><span data-stu-id="ca266-114">See note</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="ca266-115">Il supporto per le cuffie di realtà miste Windows immersive nei PC desktop non è attualmente supportato con il pacchetto NuGet riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="ca266-115">Support for immersive Windows Mixed Reality headsets on desktop PCs is not currently supported with the NuGet package below.</span></span>  <span data-ttu-id="ca266-116">Rimanere sintonizzati per ulteriori aggiornamenti sul supporto per desktop.</span><span class="sxs-lookup"><span data-stu-id="ca266-116">Stay tuned for further updates on desktop support.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="ca266-117">Recupero del pacchetto QR</span><span class="sxs-lookup"><span data-stu-id="ca266-117">Getting the QR package</span></span>
<span data-ttu-id="ca266-118">È possibile scaricare un pacchetto NuGet per il rilevamento del codice QR [qui](https://github.com/dorreneb/mixed-reality/releases).</span><span class="sxs-lookup"><span data-stu-id="ca266-118">You can download a NuGet package for QR code detection [here](https://github.com/dorreneb/mixed-reality/releases).</span></span>

<span data-ttu-id="ca266-119">Le versioni future di questo pacchetto saranno disponibili tramite il repository di pacchetti NuGet pubblico.</span><span class="sxs-lookup"><span data-stu-id="ca266-119">Future versions of this package will be available through the public NuGet package repository.</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="ca266-120">Rilevamento di codici QR</span><span class="sxs-lookup"><span data-stu-id="ca266-120">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="ca266-121">Aggiunta della funzionalità webcam</span><span class="sxs-lookup"><span data-stu-id="ca266-121">Adding the webcam capability</span></span>
<span data-ttu-id="ca266-122">Per rilevare i codici QR, è `webcam` necessario aggiungere la funzionalità al manifesto.</span><span class="sxs-lookup"><span data-stu-id="ca266-122">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="ca266-123">Questa funzionalità è necessaria perché i dati nei codici rilevati nell'ambiente dell'utente possono contenere informazioni riservate.</span><span class="sxs-lookup"><span data-stu-id="ca266-123">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="ca266-124">È possibile richiedere l'autorizzazione chiamando `QRCodeWatcher.RequestAccessAsync()`:</span><span class="sxs-lookup"><span data-stu-id="ca266-124">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="ca266-125">_C#:_</span><span class="sxs-lookup"><span data-stu-id="ca266-125">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="ca266-126">_C++:_</span><span class="sxs-lookup"><span data-stu-id="ca266-126">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="ca266-127">Prima di creare un oggetto QRCodeWatcher, è necessario richiedere l'autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="ca266-127">Permission should be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="ca266-128">Sebbene il rilevamento del codice a `webcam` matrice richieda la funzionalità, il rilevamento si verifica usando le fotocamere di rilevamento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ca266-128">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="ca266-129">Questo fornisce un rilevamento più ampio FOV e una migliore durata della batteria rispetto al rilevamento con la fotocamera Photo/video (PV) del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ca266-129">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="ca266-130">Rilevamento di codici QR in Unity</span><span class="sxs-lookup"><span data-stu-id="ca266-130">Detecting QR codes in Unity</span></span>

<span data-ttu-id="ca266-131">È possibile usare l'API di rilevamento del codice a matrice in Unity senza dipendere da MRTK.</span><span class="sxs-lookup"><span data-stu-id="ca266-131">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="ca266-132">A tale scopo, è necessario:</span><span class="sxs-lookup"><span data-stu-id="ca266-132">To do so, you must:</span></span>

1. <span data-ttu-id="ca266-133">Creare una nuova cartella nella cartella assets del progetto Unity con il nome *plug*-in.</span><span class="sxs-lookup"><span data-stu-id="ca266-133">Create a new folder in the assets folder of your unity project with the name *Plugins*.</span></span>
2. <span data-ttu-id="ca266-134">Copiare tutti i file necessari da questa cartella nella cartella "plugins" locale appena creata.</span><span class="sxs-lookup"><span data-stu-id="ca266-134">Copy all the required files from this folder into the local "Plugins" folder you just created.</span></span>

<span data-ttu-id="ca266-135">È disponibile un'app Unity di esempio che visualizza un quadrato olografico su codici a matrice, insieme ai dati associati, ad esempio GUID, dimensioni fisiche, timestamp e dati decodificati.</span><span class="sxs-lookup"><span data-stu-id="ca266-135">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="ca266-136">Questa app si trova in https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span><span class="sxs-lookup"><span data-stu-id="ca266-136">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="ca266-137">Rilevamento di codici QR inC++</span><span class="sxs-lookup"><span data-stu-id="ca266-137">Detecting QR codes in C++</span></span>

>[!NOTE]
><span data-ttu-id="ca266-138">I C++ frammenti di codice in questo articolo illustrano attualmente l'uso C++di/CX, invece di/WinRT conformi C++a C + 17 come usato nel [ C++ modello di progetto olografico](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="ca266-138">The C++ code snippets in this article currently demonstrate the use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="ca266-139">I concetti sono equivalenti per C++un progetto/WinRT, anche se è necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="ca266-139">The concepts are equivalent for a C++/WinRT project, though you need to translate the code.</span></span>

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="ca266-140">Recupero del sistema di coordinate per un codice a matrice</span><span class="sxs-lookup"><span data-stu-id="ca266-140">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="ca266-141">Ogni codice a matrice rilevato espone un [sistema di coordinate spaziali](coordinate-systems.md) allineato al codice a matrice nell'angolo superiore sinistro del quadrato di rilevamento rapido in alto a sinistra, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="ca266-141">Each detected QR code exposes a [spatial coordinate system](coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="ca266-142">Quando si usa direttamente il QR SDK, l'asse Z punta alla carta (non mostrata): quando viene convertito in coordinate Unity, l'asse Z punta all'esterno della carta ed è a sinistra.</span><span class="sxs-lookup"><span data-stu-id="ca266-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="ca266-143">Il SpatialCoordinateSystem del codice A matrice viene allineato.</span><span class="sxs-lookup"><span data-stu-id="ca266-143">A QR code's SpatialCoordinateSystem aligns shown.</span></span> <span data-ttu-id="ca266-144">Questo sistema di coordinate può essere ottenuto dalla piattaforma chiamando <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> e passando il SpatialGraphNodeId del codice.</span><span class="sxs-lookup"><span data-stu-id="ca266-144">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![Sistema di coordinate del codice a matrice](images/Qr-coordinatesystem.png) 

<span data-ttu-id="ca266-146">Per un oggetto QRCode, il codice C++/CX seguente illustra come creare un rettangolo e posizionarlo usando il sistema di coordinate del codice a matrice:</span><span class="sxs-lookup"><span data-stu-id="ca266-146">For a QRCode object, the following C++/CX code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="ca266-147">È possibile utilizzare le dimensioni fisiche per creare il rettangolo QR:</span><span class="sxs-lookup"><span data-stu-id="ca266-147">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="ca266-148">Il sistema di coordinate può essere usato per creare il codice a matrice o per alleghire gli ologrammi al percorso:</span><span class="sxs-lookup"><span data-stu-id="ca266-148">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

<span data-ttu-id="ca266-149">Il valore di *QRCodeWatcher:: QRCodeAddedHandler* potrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="ca266-149">Altogether, your *QRCodeWatcher::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="ca266-150">Procedure consigliate per il rilevamento del codice a matrice</span><span class="sxs-lookup"><span data-stu-id="ca266-150">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="ca266-151">Zone tranquille intorno ai codici QR</span><span class="sxs-lookup"><span data-stu-id="ca266-151">Quiet zones around QR Codes</span></span>

<span data-ttu-id="ca266-152">Per la lettura corretta, i codici a matrice richiedono un margine intorno a tutti i lati del codice.</span><span class="sxs-lookup"><span data-stu-id="ca266-152">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="ca266-153">Questo margine non deve contenere contenuto stampato e deve essere costituito da quattro moduli (un singolo quadrato nero nel codice).</span><span class="sxs-lookup"><span data-stu-id="ca266-153">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="ca266-154">La [specifica QR](https://www.qrcode.com/en/howto/code.html) contiene altre informazioni sulle zone tranquile.</span><span class="sxs-lookup"><span data-stu-id="ca266-154">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="ca266-155">Illuminazione e sfondo</span><span class="sxs-lookup"><span data-stu-id="ca266-155">Lighting and backdrop</span></span>
<span data-ttu-id="ca266-156">La qualità del rilevamento del codice a matrice è soggetta a variazioni di illuminazione e sfondo.</span><span class="sxs-lookup"><span data-stu-id="ca266-156">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="ca266-157">In una scena con illuminazione particolarmente luminosa, stampare un codice nero su uno sfondo grigio.</span><span class="sxs-lookup"><span data-stu-id="ca266-157">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="ca266-158">In caso contrario, stampare un codice a matrice nero su uno sfondo bianco.</span><span class="sxs-lookup"><span data-stu-id="ca266-158">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="ca266-159">Se lo sfondo del codice è particolarmente scuro, provare a usare un codice nero in grigio se la frequenza di rilevamento è bassa.</span><span class="sxs-lookup"><span data-stu-id="ca266-159">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="ca266-160">Se lo sfondo è relativamente chiaro, un codice normale dovrebbe funzionare correttamente.</span><span class="sxs-lookup"><span data-stu-id="ca266-160">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="ca266-161">Dimensioni dei codici QR</span><span class="sxs-lookup"><span data-stu-id="ca266-161">Size of QR codes</span></span>
<span data-ttu-id="ca266-162">I dispositivi di realtà mista di Windows non funzionano con codici a matrice con lati inferiori a 5 cm.</span><span class="sxs-lookup"><span data-stu-id="ca266-162">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="ca266-163">Per i codici a matrice con lunghezza compresa tra 5 e 10 cm, è necessario essere abbastanza vicini per rilevare il codice.</span><span class="sxs-lookup"><span data-stu-id="ca266-163">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="ca266-164">Sarà inoltre necessario più tempo per rilevare i codici in questa dimensione.</span><span class="sxs-lookup"><span data-stu-id="ca266-164">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="ca266-165">Il tempo esatto per rilevare i codici dipende non solo dalle dimensioni dei codici a matrice, ma dalla distanza del codice.</span><span class="sxs-lookup"><span data-stu-id="ca266-165">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="ca266-166">Lo spostamento più vicino al codice consente di compensare i problemi con le dimensioni.</span><span class="sxs-lookup"><span data-stu-id="ca266-166">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="ca266-167">Posizione angolare e distanza dal codice a matrice</span><span class="sxs-lookup"><span data-stu-id="ca266-167">Distance and angular position from the QR code</span></span>
<span data-ttu-id="ca266-168">Le videocamere di rilevamento possono rilevare solo un certo livello di dettaglio.</span><span class="sxs-lookup"><span data-stu-id="ca266-168">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="ca266-169">Per i codici molto piccoli, < 10cm lungo i lati, è necessario essere abbastanza vicini.</span><span class="sxs-lookup"><span data-stu-id="ca266-169">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="ca266-170">Per un codice a matrice di versione 1 variabile da 10 a 25 cm di larghezza, la distanza di rilevamento minima varia da 0,15 metri a 0,5 metri.</span><span class="sxs-lookup"><span data-stu-id="ca266-170">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="ca266-171">La distanza di rilevamento per le dimensioni aumenta in modo lineare.</span><span class="sxs-lookup"><span data-stu-id="ca266-171">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="ca266-172">Il rilevamento a matrice funziona con un intervallo di angoli + = 45deg.</span><span class="sxs-lookup"><span data-stu-id="ca266-172">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="ca266-173">Ciò consente di verificare la corretta risoluzione per il rilevamento del codice.</span><span class="sxs-lookup"><span data-stu-id="ca266-173">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="ca266-174">Codici QR con logo</span><span class="sxs-lookup"><span data-stu-id="ca266-174">QR codes with logos</span></span>
<span data-ttu-id="ca266-175">I codici QR con logo non sono stati testati e non sono attualmente supportati.</span><span class="sxs-lookup"><span data-stu-id="ca266-175">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="ca266-176">Gestione dei dati del codice QR</span><span class="sxs-lookup"><span data-stu-id="ca266-176">Managing QR code data</span></span>
<span data-ttu-id="ca266-177">I dispositivi di realtà mista Windows rilevano codici QR a livello di sistema nel driver.</span><span class="sxs-lookup"><span data-stu-id="ca266-177">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="ca266-178">Quando il dispositivo viene riavviato, i codici QR rilevati vengono eliminati e verranno rilevati nuovamente come nuovi oggetti la volta successiva.</span><span class="sxs-lookup"><span data-stu-id="ca266-178">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="ca266-179">Si consiglia di configurare l'app in modo da ignorare i codici QR precedenti a un timestamp specifico.</span><span class="sxs-lookup"><span data-stu-id="ca266-179">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="ca266-180">Attualmente, l'API non supporta la cancellazione della cronologia del codice QR.</span><span class="sxs-lookup"><span data-stu-id="ca266-180">Currently, the API does not support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="ca266-181">Posizionamento del codice a matrice in uno spazio</span><span class="sxs-lookup"><span data-stu-id="ca266-181">QR code placement in a space</span></span>
<span data-ttu-id="ca266-182">Per consigli su dove e come collocare i codici QR, vedere Considerazioni sull' [ambiente per HoloLens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="ca266-182">For recommendations on where and how to place QR codes, please refer to [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="ca266-183">Riferimento all'API QR</span><span class="sxs-lookup"><span data-stu-id="ca266-183">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="ca266-184">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ca266-184">See also</span></span>
* [<span data-ttu-id="ca266-185">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="ca266-185">Coordinate systems</span></span>](coordinate-systems.md)
* <span data-ttu-id="ca266-186"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="ca266-186"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>