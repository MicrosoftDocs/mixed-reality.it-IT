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
# <a name="locatable-camera-in-directx"></a>Fotocamera individuabile in DirectX

In questo argomento descrive come configurare un [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) della pipeline per l'accesso di [fotocamera](locatable-camera.md) in un'app DirectX, inclusi i metadati di frame che sono possibile individuare le immagini del prodotto nel mondo reale.

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Acquisizione di Windows Media e Media Foundation sviluppo: IMFAttributes

Ogni frame di immagini [include un sistema di coordinate](locatable-camera.md#images-with-coordinate-systems) , nonché due trasformazioni importanti. La "visualizzazione" Trasforma mappe dal sistema di coordinate specificato per la fotocamera e le mappe "proiezione" dalla fotocamera ai pixel nell'immagine. Il sistema di coordinate e 2 trasformazioni incorporate come metadati in ogni frame di immagini tramite Media Foundation [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>Esempio di utilizzo di lettura di attributi con sink personalizzati MF e l'esecuzione di proiezione

Il flusso MF Sink personalizzati ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), si otterrà [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) con gli attributi di esempio:

Il seguente MediaExtensions devono essere definiti per il codice basato su WinRT:

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

È possibile accedere a questi attributi dalla APIs WinRT, ma richiede l'implementazione dell'estensione di supporti [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (per effetto) o [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) e [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) ( per il Sink personalizzati). Quando si elabora l'esempio in questa estensione sia nel [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) o [IMFStreamSink::ProcessSample() ](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), è possibile eseguire una query degli attributi, ad esempio in questo esempio.

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

Per accedere a trama dalla fotocamera, è necessario stesso dispositivo D3D che consente di creare la trama frame della fotocamera. Questo dispositivo D3D è nel [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) nella pipeline di acquisizione. Per ottenere la gestione di dispositivi DXGI da supporti di acquisizione è possibile usare [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) e [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfacce.

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

È anche possibile abilitare input come metodi di input facoltativi per l'app di realtà mista di Windows della tastiera e mouse. Ciò può anche essere un'ottima funzionalità di debug per i dispositivi, ad esempio HoloLens e potrebbe essere utile per l'input utente nelle app di realtà mista in esecuzione in coinvolgenti auricolari collegati al PC.
