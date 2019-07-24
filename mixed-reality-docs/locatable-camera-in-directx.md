---
title: Fotocamera locatable in DirectX
description: Viene illustrato come usare la fotocamera punto di visualizzazione (POV) in un'app HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, locatable, videocamera, punto di vista, POV, unporoject, Media Foundation, MF, sink personalizzato, procedura dettagliata, codice di esempio
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516860"
---
# <a name="locatable-camera-in-directx"></a>Fotocamera locatable in DirectX

Questo argomento descrive come configurare una pipeline di [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) per accedere alla [fotocamera](locatable-camera.md) in un'app DirectX, inclusi i metadati del frame che consentono di individuare le immagini prodotte nel mondo reale.

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows Media Capture e Media Foundation sviluppo: IMFAttributes

Ogni frame di immagine [include un sistema di coordinate](locatable-camera.md#images-with-coordinate-systems) , nonché due trasformazioni importanti. La trasformazione "View" esegue il mapping dal sistema di coordinate fornito alla fotocamera e la "proiezione" esegue il mapping dalla fotocamera ai pixel nell'immagine. Il sistema di coordinate e le due trasformazioni sono incorporati come metadati in ogni fotogramma immagine tramite [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)di Media Foundation.

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>Esempio di utilizzo della lettura degli attributi con il sink personalizzato MF e la proiezione

Nel flusso di sink MF personalizzato ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) si otterrà [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) con gli attributi di esempio:

Per il codice basato su WinRT è necessario definire i seguenti MediaExtensions:

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

Non è possibile accedere a questi attributi dalle API WinRT, ma è necessaria l'implementazione dell'estensione multimediale di [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (per effetto) o [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) e [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (per il sink personalizzato). Quando si elabora l'esempio in questa estensione in [IMFTransform::P rocessinput ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::P rocessoutput ()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) o [IMFStreamSink::P rocesssample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), è possibile eseguire una query sugli attributi come questo esempio.

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

Per accedere alla trama dalla fotocamera, è necessario lo stesso dispositivo D3D che crea la trama del fotogramma della fotocamera. Questo dispositivo D3D si trova in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) nella pipeline di acquisizione. Per ottenere gestione dispositivi DXGI da Media Capture, è possibile usare le interfacce [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) e [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) .

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

È anche possibile abilitare l'input da mouse e tastiera come metodi di input facoltativi per l'app di realtà mista Windows. Può anche trattarsi di un'ottima funzionalità di debug per i dispositivi, ad esempio HoloLens, e può essere utile per l'input dell'utente in app realtà miste in esecuzione in auricolari immersivi collegati ai PC.
