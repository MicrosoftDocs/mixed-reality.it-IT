---
title: OpenXR
description: È possibile creare un motore usando lo standard dell'API OpenXR portatile e distribuirlo in una realtà mista di Windows e in HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware
ms.openlocfilehash: 04b2404889dc74f191543466beb7ae1e516d0d42
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549381"
---
# <a name="openxr"></a>OpenXR

OpenXR è uno standard API senza diritti d'autore aperto da <a href="https://www.khronos.org/" target="_blank">Khronos</a> che fornisce ai motori l'accesso nativo a un'ampia gamma di dispositivi di molti fornitori che si estendono nello [spettro della realtà mista](mixed-reality.md).

È possibile sviluppare usando OpenXR in un headset HoloLens 2 o Windows Mixed Reality immersive sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

## <a name="why-openxr"></a>Perché OpenXR?

Con OpenXR, è possibile creare motori destinati a entrambi i dispositivi olografici (ad esempio HoloLens 2) che collocano contenuti digitali nel mondo reale come se fossero effettivamente presenti, nonché dispositivi immersivi, come le cuffie di realtà mista di Windows per PC desktop, che nascondono il fisico e sostituirla con un'esperienza digitale.  OpenXR consente di scrivere codice una volta trasportabile in un'ampia gamma di piattaforme hardware.

L'API OpenXR usa un caricatore che connette l'applicazione direttamente al supporto della piattaforma nativa dell'auricolare.  Questo consente agli utenti finali di ottenere le massime prestazioni e la latenza minima, sia che usino un auricolare di realtà mista di Windows o qualsiasi altro auricolare.

## <a name="what-is-openxr"></a>Che cos'è OpenXR?

L'API OpenXR fornisce le funzionalità di base per la stima, la tempistica dei frame e l'input spaziale necessari per compilare un motore che può essere destinato a entrambi i dispositivi olografici come HoloLens 2 e dispositivi immersivi come gli auricolari di realtà mista di Windows.

Per informazioni sull'API OpenXR, vedere la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica</a>OpenXR 1,0, informazioni di <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">riferimento sulle API</a> e <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guida di riferimento rapido</a>.  Per ulteriori informazioni, vedere la <a href="https://www.khronos.org/openxr/" target="_blank">pagina Khronos OpenXR</a>.

Per avere come destinazione il set completo di funzionalità di HoloLens 2, si useranno anche estensioni OpenXR specifiche del fornitore e dei fornitori che consentono funzionalità aggiuntive oltre al core OpenXR 1,0, ad esempio il rilevamento a mano articolato, il monitoraggio degli occhi, il mapping spaziale e i ancoraggi spaziali.  Vedere la [sezione roadmap](#roadmap) riportata di seguito per altre informazioni sulle estensioni riportate più avanti in questo anno.

Si noti che OpenXR non è a sua volta un motore di realtà mista.  OpenXR consente invece ai motori come Unity e Unreal di scrivere codice portatile una volta che può accedere alle funzionalità della piattaforma nativa del dispositivo olografico o immersivo dell'utente, indipendentemente dal fornitore che ha creato tale piattaforma.

## <a name="roadmap"></a>Guida di orientamento

La specifica OpenXR definisce un meccanismo di estensione che consente agli implementatori del runtime di esporre funzionalità aggiuntive oltre le [funzionalità](#what-is-openxr) di <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">base definite nella specifica OpenXR 1,0 di base</a>.

Sono disponibili tre tipi di estensioni OpenXR:
* **Estensioni Fornitore (ad esempio `MSFT`):** Consente l'innovazione per fornitore in funzionalità hardware o software.  Qualsiasi fornitore di runtime può introdurre e distribuire un'estensione del fornitore in qualsiasi momento.
  * **Estensioni del fornitore sperimentale (ad esempio `MSFT_preview`):** Estensioni del fornitore sperimentali visualizzate in anteprima per raccogliere commenti e suggerimenti.  le estensioni `MSFT_preview` sono destinate solo ai dispositivi per sviluppatori e verranno rimosse quando l'estensione reale viene fornita.  Per sperimentarli, è possibile [abilitare le estensioni di anteprima nel dispositivo per sviluppatori](openxr-getting-started.md#using-preview-extensions).
* **Estensioni `EXT` tra fornitori:** Estensioni tra fornitori che vengono definite e implementate da più aziende.  I gruppi di società interessate possono introdurre estensioni EXT in qualsiasi momento.
* **Estensioni `KHR` ufficiale:** Estensioni Khronos ufficiali ratificate come parte di una versione di base delle specifiche.  Le estensioni KHR sono coperte dalla stessa licenza della specifica principale.

Entro il 2020 luglio, il runtime di OpenXR per la realtà mista di Windows supporterà un set di `MSFT` e `EXT` estensioni che portano il set completo di funzionalità HoloLens 2 alle applicazioni OpenXR:

| Area funzionale | Disponibilità dell'estensione |
|--------------|------------------------|
| Sistemi e sessioni | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Spazi di riferimento (visualizzazione, locale, fase)](coordinate-systems.md) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Visualizza configurazioni (mono, stereo) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Le catene](rendering.md) [intervallo frame](understanding-performance-for-mixed-reality.md) +  | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Livelli di composizione<br />(proiezione, quad) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Input e haptics](interaction-fundamentals.md) | **OpenXR 1,0-spec Core:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integrazione di Direct3D 11 | **Estensione `KHR` ufficiale rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code><br /> |
| Integrazione con Direct3D 12 | **Estensione `KHR` ufficiale definita:** *(non ancora supportata)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code><br /><p>**Supporto in anteprima**: aprile 2020 *(pianificato)*</p><p>**Supporto completo**: 2020 maggio *(pianificato)*</p> |
| [Spazio di riferimento senza limiti<br />(esperienze su scala mondiale)](coordinate-systems.md#building-a-world-scale-experience) | **estensione `MSFT` rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Ancoraggi nello spazio](spatial-anchors.md) | **estensione `MSFT` rilasciata:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [<br />interazione della mano (grip/AIM, tocco, presa)](hands-and-tools.md) | **`MSFT_preview` estensione disponibile:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_interaction_preview">XR_MSFT_hand_interaction_preview</a></code><p>**`MSFT` versione**: aprile 2020 *(pianificato)*</p> |
| [Articolazione manuale + mesh mano](hands-and-tools.md) | **`MSFT_preview` estensione disponibile:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_preview">XR_MSFT_hand_tracking_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_mesh_preview">XR_MSFT_hand_tracking_mesh_preview</a></code><p>**`MSFT` versione**: 2020 maggio *(pianificato)*</p> |
| Interoperabilità con altri SDK di HoloLens (ad esempio, [QR](qr-code-tracking.md)) | **`MSFT_preview` estensione disponibile:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_graph_bridge_preview">XR_MSFT_spatial_graph_bridge_preview</a></code><p>**`MSFT` versione**: 2020 maggio *(pianificato)*</p> |
| [Tracciamento oculare](eye-tracking.md) | <p>**estensione`EXT` definita**: *(non ancora supportata)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code><p>**Supporto in anteprima**: aprile 2020 *(pianificato)*</p><p>**Supporto completo**: 2020 maggio *(pianificato)*</p> |
| [<br />di acquisizione realtà mista (terzo rendering dalla fotocamera PV)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) | **`MSFT_preview` estensione disponibile:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_secondary_view_configuration_preview">XR_MSFT_secondary_view_configuration_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_first_person_observer_preview">XR_MSFT_first_person_observer_preview</a></code><br /><p>**`MSFT` versione**: 2020 giugno *(pianificato)*</p> |
| [Modelli di rendering del controller di movimento](motion-controllers.md#rendering-the-motion-controller-model) | <p>**`MSFT_preview`** : aprile 2020 *(pianificato)*</p><p>**`MSFT` versione**: 2020 luglio *(pianificato)*</p> |
| [Comprensione della scena (piani, mesh)](scene-understanding.md) | <p>**`MSFT_preview`** : 2020 maggio *(pianificato)*</p><p>**`MSFT` versione**: 2020 luglio *(pianificato)*</p> |

Sebbene alcune di queste estensioni possano iniziare come estensioni di `MSFT` specifiche del fornitore, Microsoft e altri fornitori di runtime di OpenXR collaborano per progettare `EXT` o `KHR` estensioni di un fornitore per molte di queste aree di funzionalità.  In questo modo il codice scritto per le funzionalità sarà portabile tra i fornitori di runtime, come per la specifica di base.

## <a name="get-started-with-openxr"></a>Introduzione a OpenXR

È possibile sviluppare usando OpenXR in un headset HoloLens 2 o Windows Mixed Reality immersive sul desktop.  Se non si ha accesso a una cuffia, è invece possibile usare l'emulatore HoloLens 2 o il simulatore di realtà mista di Windows.

Per iniziare a sviluppare applicazioni OpenXR per HoloLens 2 o cuffie di realtà miste Windows immersive, vedere [come iniziare a usare lo sviluppo OpenXR](openxr-getting-started.md).

## <a name="see-also"></a>Vedere anche

* <a href="https://www.khronos.org/openxr/" target="_blank">Altre informazioni su OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Specifica OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Informazioni di riferimento sull'API OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guida di riferimento rapido per OpenXR 1,0</a>
