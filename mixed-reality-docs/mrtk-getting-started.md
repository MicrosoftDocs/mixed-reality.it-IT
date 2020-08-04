---
title: Guida introduttiva a MRTK versione 2
description: Per i nuovi sviluppatori interessati a usufruire dei vantaggi offerti da MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 64f5925154a2987cd04293fd4c04bbd9f48bacbf
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "87477013"
---
# <a name="getting-started-with-mrtk-for-unity"></a>Introduzione a MRTK per Unity
![MRTK](images/UX/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Che cos'è Mixed Reality Toolkit (MRTK)?
MRTK è un toolkit open source eccezionale, disponibile da quando il dispositivo HoloLens è stato rilasciato per la prima volta, ma che oggi non sarebbe così efficace senza i preziosi contributi della nostra community di sviluppatori. Negli ultimi tre anni abbiamo acquisito feedback dalla nostra community di sviluppatori e abbiamo creato MRTK v2 tenendo conto delle loro principali esigenze e segnalazioni.  

MRTK per Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali. MRTK versione 2 permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, di visori VR immersive di Windows Mixed Reality e della piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

Per altre informazioni, vedere la [documentazione di MRTK in GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="new-with-mrtk-v2"></a>Novità di MRTK v2
È importante sottolineare l'impegno che abbiamo dedicato a questi strumenti della piattaforma.  In realtà, abbiamo usato proprio MRTK versione 2 per sviluppare le nostre esperienze integrate, come l'esperienza di installazione (OOBE) e l'applicazione per l'apprendimento basato sulla realtà mista.  Probabilmente avrai l'occasione anche di vedere nuove funzionalità di HoloLens 2 esposte tramite MRTK prima del rilascio, perché crediamo che questo sia il modo migliore per sviluppare sulla nostra piattaforma. 

### <a name="modular"></a>Modularità
Il toolkit è stato creato in modo modulare, quindi non è necessario includerlo per intero nel progetto.  Questa caratteristica presenta alcuni vantaggi.  Consente di limitare le dimensioni del progetto e ne semplifica la gestione.  Inoltre, poiché il toolkit è stato creato con oggetti gestibili tramite script ed è dotato di interfaccia, puoi anche sostituire i componenti inclusi nel toolkit con componenti personalizzati, per supportare altri servizi, sistemi e piattaforme.

### <a name="cross-platform"></a>Multipiattaforma
Il toolkit include il supporto per più piattaforme.  Anche se questo non significa che ogni singola piattaforma è supportata in modo predefinito, abbiamo fatto in modo che nessuna parte del codice del toolkit smetta di funzionare nel caso in cui tu scelga di configurare altre piattaforme di destinazione per la tua build.  L'affidabilità e l'estendibilità che caratterizzano la progettazione modulare ti aiuteranno a seguire la strada giusta per supportare più piattaforme, come ARCore, ARKit e OpenVR.

### <a name="performant"></a>Ottime prestazioni
Dovendo lavorare con piattaforme mobili, abbiamo realizzato il toolkit tenendo sempre ben presenti le prestazioni.  Questo è un aspetto molto importante e volevamo essere sicuri che gli strumenti funzionassero nel modo giusto.

## <a name="see-also"></a>Vedere anche
* [Guida introduttiva a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Home page della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Installare gli strumenti](install-the-tools.md)
* [Conversione da HTK/MRTK a MRTK versione 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
