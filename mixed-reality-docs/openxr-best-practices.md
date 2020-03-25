---
title: Procedure consigliate per OpenXR
description: Informazioni sulle procedure consigliate per la qualità visiva, la stabilità e le prestazioni delle applicazioni OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware, procedure consigliate, prestazioni, qualità, stabilità
ms.openlocfilehash: 01ce2ac0a69ffdf5dd1f00b92f37f54964f4c30c
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163355"
---
# <a name="openxr-app-best-practices"></a>Procedure consigliate per le app OpenXR

È possibile vedere un esempio delle procedure consigliate riportate di seguito nel file [OpenXRProgram. cpp](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp) di BasicXrApp. La funzione Run () all'inizio acquisisce un flusso di codice dell'app OpenXR tipico dall'inizializzazione all'evento e al ciclo di rendering.

## <a name="best-practices-for-visual-quality-and-stability"></a>Procedure consigliate per la qualità e la stabilità visive

Le procedure consigliate in questa sezione descrivono come ottenere la qualità visiva e la stabilità migliori in qualsiasi applicazione OpenXR.

Per ulteriori raccomandazioni sulle prestazioni specifiche per HoloLens 2, vedere la sezione procedure consigliate [per le prestazioni in HoloLens 2](#best-practices-for-performance-on-hololens-2) .

### <a name="gamma-correct-rendering"></a>Rendering con correzione gamma

È necessario prestare attenzione per assicurarsi che la pipeline di rendering sia corretta da gamma. Quando si esegue il rendering in un presentazione catena, il formato di visualizzazione della destinazione di rendering deve corrispondere al formato presentazione catena (ad esempio DXGI_FORMAT_B8G8R8A8_UNORM_SRGB sia per il formato presentazione catena che per la visualizzazione destinazione rendering).
L'eccezione è rappresentata dal caso in cui la pipeline di rendering dell'app esegua una conversione manuale di sRGB nel codice dello shader, nel qual caso l'app deve richiedere un formato presentazione catena di sRGB, ma usare il formato lineare per la visualizzazione di destinazione di rendering (ad esempio, la richiesta DXGI_FORMAT_B8G8R8A8_UNORM_SRGB come presentazione catena, ma usa DXGI_FORMAT_B8G8R8A8_UNORM come visualizzazione di destinazione di rendering) per impedire che il contenuto venga corretto a seconda della gamma.

### <a name="submit-depth-buffer-for-projection-layers"></a>Invia buffer di profondità per i livelli di proiezione

Usare sempre `XR_KHR_composition_layer_depth` estensione e inviare il buffer di profondità insieme al livello di proiezione quando si invia un frame al `xrEndFrame`.
Ciò migliora la stabilità dell'ologramma abilitando la riproiezione hardware depth in HoloLens 2.

### <a name="choose-a-reasonable-depth-range"></a>Scegliere un intervallo di profondità ragionevole

Preferire un intervallo di profondità più ristretto per definire l'ambito del contenuto virtuale per aiutare la stabilità degli ologrammi in HoloLens.
Ad esempio, l'esempio OpenXrProgram. cpp utilizza 0,1 a 20 metri.
Utilizzare [invertito-Z](https://developer.nvidia.com/content/depth-precision-visualized) per una risoluzione più uniforme della profondità.
Si noti che, in HoloLens 2, l'uso del formato di profondità `DXGI_FORMAT_D16_UNORM` preferito consentirà di ottimizzare la frequenza dei fotogrammi e le prestazioni, sebbene i buffer di profondità a 16 bit forniscano una risoluzione meno approfondita rispetto ai buffer di profondità a 24 bit.
Quindi, seguendo queste procedure consigliate per sfruttare al meglio la risoluzione di profondità diventa più importante.

### <a name="prepare-for-different-environment-blend-modes"></a>Preparare le diverse modalità di Blend dell'ambiente

Se l'applicazione verrà eseguita anche su auricolari immersivi che bloccano completamente il mondo, assicurarsi di enumerare le modalità di Blend dell'ambiente supportate usando `xrEnumerateEnvironmentBlendModes` API e di preparare il contenuto di rendering di conseguenza.
Ad esempio, per un sistema con `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` come HoloLens, l'app deve usare trasparente come colore chiaro, mentre per un sistema con `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`, l'app deve eseguire il rendering di un colore opaco o di una stanza virtuale in background.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Scegliere lo spazio di riferimento senza limiti come spazio radice dell'applicazione

In genere, le applicazioni stabiliscono uno spazio delle coordinate del mondo radice per connettere viste, azioni e ologrammi.
Usare `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` quando l'estensione è supportata per stabilire un [sistema di coordinate su scala globale](coordinate-systems.md#building-a-world-scale-experience), consentendo all'app di evitare la tendenza olografica indesiderata quando l'utente si sposta lontano (ad esempio, 5 metri di distanza) da dove viene avviata l'app.
Usare `XR_REFERENCE_SPACE_TYPE_LOCAL` come fallback se l'estensione dello spazio non associato non esiste.

### <a name="associate-hologram-with-spatial-anchor"></a>Associa ologramma a ancoraggio spaziale

Quando si usa uno spazio di riferimento non vincolato, gli ologrammi posizionati direttamente nello spazio di riferimento [potrebbero andare alla deriva quando l'utente passa a una stanza lontana e quindi](coordinate-systems.md#building-a-world-scale-experience)torna.
Per gli utenti olografici posizionati in una posizione discreta nel mondo, [creare un ancoraggio spaziale](spatial-anchors.md#best-practices) usando la funzione di estensione `xrCreateSpatialAnchorSpaceMSFT` e posizionare l'ologramma all'origine.
In questo modo l'ologramma viene mantenuto indipendentemente stabile nel tempo.

### <a name="support-mixed-reality-capture"></a>Supportare l'acquisizione di realtà mista

Sebbene la visualizzazione principale di HoloLens 2 usi la fusione dell'ambiente additiva, quando l'utente avvia l' [acquisizione della realtà mista](mixed-reality-capture-for-developers.md), il contenuto di rendering dell'app verrà sottoposto ad Alpha blending con il flusso video dell'ambiente.
Per ottenere la migliore qualità visiva nei video di acquisizione di realtà mista, è preferibile impostare il `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` nel `layerFlags`del livello di proiezione.

## <a name="best-practices-for-performance-on-hololens-2"></a>Procedure consigliate per le prestazioni in HoloLens 2

Come dispositivo mobile con supporto per la riproiezione dell'hardware, HoloLens 2 presenta requisiti più restrittivi per ottenere prestazioni ottimali.  Esistono diversi modi per inviare i dati di composizione tramite `xrEndFrame` che comporteranno una successiva elaborazione che avrà una notevole riduzione delle prestazioni.

### <a name="select-a-swapchain-format"></a>Selezionare un formato presentazione catena

Enumerare sempre i formati pixel supportati usando `xrEnumerateSwapchainFormats`e scegliere il primo formato pixel di colore e profondità dal runtime supportato dall'app, perché questo è quello che il runtime preferisce per ottenere prestazioni ottimali. Si noti che, in HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` e `DXGI_FORMAT_D16_UNORM` sono in genere la prima scelta per ottenere prestazioni di rendering migliori. Questa preferenza può essere diversa negli auricolari VR in esecuzione su un PC desktop, in cui i buffer di profondità a 24 bit hanno un minore effetto sulle prestazioni.
  
**Avviso di prestazioni:** Se si usa un formato diverso dal formato di colore presentazione catena primario, la post-elaborazione del runtime comporterà una riduzione significativa delle prestazioni.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Rendering con i parametri di rendering consigliati e la tempistica dei frame

Eseguire sempre il rendering con la larghezza/altezza della configurazione di visualizzazione consigliata (`recommendedImageRectWidth` e `recommendedImageRectHeight` da `XrViewConfigurationView`) e usare sempre `xrLocateViews` API per eseguire una query per la visualizzazione consigliata, FOV e altri parametri di rendering prima del rendering.
Usare sempre il `XrFrameEndInfo.predictedDisplayTime` dalla chiamata `xrWaitFrame` più recente quando si eseguono query per pose e viste.
Ciò consente a HoloLens di modificare il rendering e ottimizzare la qualità visiva per la persona che sta indossando la HoloLens.

### <a name="use-a-single-projection-layer"></a>Usa un solo livello di proiezione

HoloLens 2 ha una potenza GPU limitata per le applicazioni per il rendering del contenuto e un compositor hardware ottimizzato per un singolo livello di proiezione.
Usare sempre un solo livello di proiezione può aiutare a framerate, stabilità olografica e qualità visiva dell'applicazione.  
  
**Avviso di prestazioni:** L'invio di un singolo livello di protezione comporta un conseguente calo delle prestazioni in fase di elaborazione.

### <a name="render-with-texture-array-and-vprt"></a>Rendering con matrice di trame e VPRT

Creare una `xrSwapchain` sia per l'occhio sinistro che quello destro usando `arraySize=2` per il colore presentazione catena e una per la profondità.
Eseguire il rendering dell'occhio sinistro nella sezione 0 e l'occhio destro nella sezione 1.
Usare uno shader con VPRT e le chiamate di progetto con istanza per il rendering stereoscopico per ridurre al minimo il carico della GPU.
Questo consente anche l'ottimizzazione del runtime per ottenere prestazioni ottimali in HoloLens 2.
Le alternative all'uso di una matrice di trame, ad esempio il rendering a doppio livello o un presentazione catena separato per occhio, comporteranno una successiva elaborazione del runtime che comporta una riduzione significativa delle prestazioni.

### <a name="avoid-quad-layers"></a>Evitare i livelli quad

Anziché inviare livelli quad come livelli di composizione con `XrCompositionLayerQuad`, eseguire il rendering del contenuto Quad direttamente nella proiezione presentazione catena.

**Avviso di prestazioni:** Fornire livelli aggiuntivi oltre un singolo livello di proiezione, ad esempio i livelli quad, comporterà la post-elaborazione in fase di esecuzione, che comporta una riduzione significativa delle prestazioni.