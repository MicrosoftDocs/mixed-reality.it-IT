---
title: Introduzione a MRTK versione 2
description: Per i nuovi sviluppatori interessati a sfruttare MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
keywords: Realtà mista di Windows, test, Toolkit per realtà mista, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: bb958543aa68586dd689a2048665b233d6be7064
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913133"
---
# <a name="getting-started-with-mrtk-v2"></a>Introduzione a MRTK V2

## <a name="mrtk-getting-started-guide"></a>Guida Introduzione MRTK
Per informazioni dettagliate su come iniziare a usare MRTK V2, vedere la Guida introduttiva a [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) .

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Che cos'è il Toolkit di realtà mista (MRTK)?
MRTK è un toolkit open source straordinario, che è stato girato da quando il HoloLens è stato rilasciato per la prima volta e non può essere usato oggi senza il lavoro svolto dalla nostra community di sviluppatori che ha contribuito. Negli ultimi tre anni abbiamo ascoltato i commenti e i suggerimenti della nostra community di sviluppatori e abbiamo creato MRTK V2 per tenere conto dei principali problemi.  

MRTK v2 con Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista.  MRTK versione 2 consente di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, ai visori VR immersive di Windows Mixed Reality e alla piattaforma OpenVR. Il progetto ha lo scopo di ridurre le barriere all'ingresso, creare applicazioni di realtà miste e contribuire alla community Man mano che crescono. 

Per altre informazioni, vedere il [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) .

## <a name="new-with-mrtk-v2"></a>Novità con MRTK V2
Vogliamo sottolineare l'impegno a questi strumenti della piattaforma.  In realtà, abbiamo sfruttato MRTK versione 2 per sviluppare le nostre esperienze di posta in arrivo, ad esempio l'esperienza di installazione (OOBE) e l'applicazione di apprendimento in realtà mista.  Puoi anche aspettarti che le nuove funzionalità di HoloLens 2 siano esposte prima di tutto tramite MRTK, perché crediamo che sia il modo migliore per sviluppare sulla nostra piattaforma. 

### <a name="modular"></a>Modulare
La compilazione è stata compilata in modo modulare, quindi non è necessario eseguire ogni bit del Toolkit nel progetto.  Questa operazione è in realtà costituita da alcuni vantaggi.  Mantiene le dimensioni del progetto minori e ne semplifica la gestione.  Inoltre, poiché è stato creato con oggetti gestibili tramite script ed è basato sull'interfaccia, è anche possibile sostituire i componenti inclusi nel proprio, per supportare altri servizi, sistemi e piattaforme.

### <a name="cross-platform"></a>Multipiattaforma
Parlando di altre piattaforme, ha un supporto multipiattaforma.  Anche se questo non significa che ogni singola piattaforma è supportata in modo predefinito, è stato verificato che nessuno del codice del Toolkit si interrompe quando si passa alla destinazione di compilazione ad altre piattaforme.  L'affidabilità e l'estendibilità con la progettazione modulare consentiranno di ottenere un percorso valido per supportare più piattaforme, ad esempio ARCore, ARKit e OpenVR.

### <a name="performant"></a>Performante
Con le piattaforme mobili è stato costruito con le prestazioni.  Si tratta di un aspetto molto importante e si vuole assicurare che gli strumenti non funzionino correttamente.

## <a name="see-also"></a>Vedi anche
* [Guida introduttiva a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Home page della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Installare gli strumenti](install-the-tools.md)
* [Porting da HTK/MRTK a MRTK versione 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
