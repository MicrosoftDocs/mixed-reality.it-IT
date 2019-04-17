---
title: Fotocamera individuabile in DirectX
description: Viene illustrato come usare la fotocamera (immagini) punto di vista in un'app di HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, fotocamera individuabile, punto di vista, immagini, unporoject, media foundation, MF, sink personalizzati, procedura dettagliata, codice di esempio
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602083"
---
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="a75cd-104">Fotocamera individuabile in DirectX</span><span class="sxs-lookup"><span data-stu-id="a75cd-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="a75cd-105">In questo argomento descrive come configurare un [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) della pipeline per l'accesso di [fotocamera](locatable-camera.md) in un'app DirectX, inclusi i metadati di frame che sono possibile individuare le immagini del prodotto nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="a75cd-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="a75cd-106">Acquisizione di Windows Media e Media Foundation sviluppo: IMFAttributes</span><span class="sxs-lookup"><span data-stu-id="a75cd-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="a75cd-107">Ogni frame di immagini [include un sistema di coordinate](locatable-camera.md#images-with-coordinate-systems) , nonché due trasformazioni importanti.</span><span class="sxs-lookup"><span data-stu-id="a75cd-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="a75cd-108">La "visualizzazione" Trasforma mappe dal sistema di coordinate specificato per la fotocamera e le mappe "proiezione" dalla fotocamera ai pixel nell'immagine.</span><span class="sxs-lookup"><span data-stu-id="a75cd-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="a75cd-109">Il sistema di coordinate e 2 trasformazioni incorporate come metadati in ogni frame di immagini tramite Media Foundation [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a75cd-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="a75cd-110">Esempio di utilizzo di lettura di attributi con sink personalizzati MF e l'esecuzione di proiezione</span><span class="sxs-lookup"><span data-stu-id="a75cd-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="a75cd-111">Il flusso MF Sink personalizzati ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), si otterrà [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) con gli attributi di esempio:</span><span class="sxs-lookup"><span data-stu-id="a75cd-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="a75cd-112">Il seguente MediaExtensions devono essere definiti per il codice basato su WinRT:</span><span class="sxs-lookup"><span data-stu-id="a75cd-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="a75cd-113">È possibile accedere a questi attributi dalla APIs WinRT, ma richiede l'implementazione dell'estensione di supporti [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (per effetto) o [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) e [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) ( per il Sink personalizzati).</span><span class="sxs-lookup"><span data-stu-id="a75cd-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="a75cd-114">Quando si elabora l'esempio in questa estensione sia nel [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) o [IMFStreamSink::ProcessSample() ](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), è possibile eseguire una query degli attributi, ad esempio in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="a75cd-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

<span data-ttu-id="a75cd-115">Per accedere a trama dalla fotocamera, è necessario stesso dispositivo D3D che consente di creare la trama frame della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="a75cd-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="a75cd-116">Questo dispositivo D3D è nel [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) nella pipeline di acquisizione.</span><span class="sxs-lookup"><span data-stu-id="a75cd-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="a75cd-117">Per ottenere la gestione di dispositivi DXGI da supporti di acquisizione è possibile usare [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) e [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfacce.</span><span class="sxs-lookup"><span data-stu-id="a75cd-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

<span data-ttu-id="a75cd-118">È anche possibile abilitare input come metodi di input facoltativi per l'app di realtà mista di Windows della tastiera e mouse.</span><span class="sxs-lookup"><span data-stu-id="a75cd-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="a75cd-119">Ciò può anche essere un'ottima funzionalità di debug per i dispositivi, ad esempio HoloLens e potrebbe essere utile per l'input utente nelle app di realtà mista in esecuzione in coinvolgenti auricolari collegati al PC.</span><span class="sxs-lookup"><span data-stu-id="a75cd-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
