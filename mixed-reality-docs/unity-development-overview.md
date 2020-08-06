---
title: Panoramica dello sviluppo con Unity
description: Guida introduttiva alla creazione di app di realtà mista in Unity.
author: thetuvix
ms.author: kurtie
ms.date: 07/29/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realtà mista, sviluppo, guida introduttiva, nuovo progetto, conversione, funzionalità, fotocamera, simulazione, emulazione, documentazione
ms.openlocfilehash: 4679e1a2b58a7e0d77e6b295803624a4de1fac19
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476713"
---
# <a name="unity-development-overview"></a>Panoramica dello sviluppo con Unity

[Unity](https://unity.com) offre la soluzione più veloce per creare un'[app di realtà mista](app-views.md). Ti consigliamo di dedicare un po' di tempo a esplorare le esercitazioni di [Unity](https://unity3d.com/learn/tutorials). Se hai bisogno di asset, Unity offre un [Asset Store](https://www.assetstore.unity3d.com/) ben fornito. Dopo avere acquisito una conoscenza di base di Unity, potrai eseguire le [esercitazioni](tutorials.md) per apprendere le specifiche dello sviluppo di app di realtà mista con Unity. Visita i [forum di Unity relativi alla realtà mista](https://forum.unity3d.com/forums/hololens.102/) per collaborare con i membri della community impegnati a creare app di realtà mista in Unity. Ti aiuteranno a trovare le soluzioni ai problemi che potresti incontrare.

Per iniziare a creare app di realtà mista con Unity, devi prima [installare gli strumenti](install-the-tools.md).

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Nuovo progetto Unity con Mixed Reality Toolkit 

Il modo più semplice per sviluppare app in Unity è quello di usare Mixed Reality Toolkit, che consentirà di impostare il progetto automaticamente e fornirà un set di funzionalità per la realtà mista utili per accelerare le attività di sviluppo. Per altre informazioni e per iniziare, vedere [Mixed Reality Toolkit v2](mrtk-getting-started.md). 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Conversione di un'app Unity esistente in Windows Mixed Reality

Se disponi di un progetto Unity esistente che prevedi di convertire in Windows Mixed Reality, inizia seguendo le istruzioni della [guida alla conversione di Unity](porting-guides.md).

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Configurazione del nuovo progetto Unity per Windows Mixed Reality

Se si crea un nuovo progetto Unity senza importare Mixed Reality Toolkit, è necessario modificare un set ridotto di impostazioni di Unity per Windows Mixed Reality. Queste impostazioni sono suddivise in due categorie: per progetto e per scena. Per istruzioni dettagliate, vedere [Configurare un nuovo progetto Unity per Windows Mixed Reality](Configure-Unity-Project.md).

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Aggiunta di input e funzionalità per la realtà mista

Dopo aver impostato MRTK V2 con il progetto o aver configurato il progetto come descritto in precedenza, gli oggetti di gioco Unity standard, ad esempio la fotocamera, si illumineranno immediatamente per un'**esperienza da seduti** in cui la posizione della fotocamera viene aggiornata automaticamente mentre l'utente sposta la testa nel mondo.

L'aggiunta del supporto per le funzionalità di Windows Mixed Reality, ad esempio [fasi spaziali](coordinate-systems.md#spatial-coordinate-systems), [movimenti, controller del movimento](gestures-and-motion-controllers-in-unity.md) o [input vocale](voice-input-in-unity.md), avviene tramite le API integrate direttamente in Unity. 

Esamina prima di tutto le [scale di esperienza](coordinate-systems.md) a cui può essere destinata l'applicazione:
* Se vuoi creare un'esperienza di **solo orientamento** o **da seduti**, devi impostare il tipo di spazio di tracciamento di Unity su [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se vuoi creare un'esperienza **in piedi** o **a livello di stanza**, devi assicurarti che il tipo di spazio di tracciamento di Unity sia impostato correttamente su [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se vuoi creare in HoloLens un'esperienza **su scala globale** che consenta agli utenti di spostarsi oltre 5 metri, dovrai usare il componente [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience).

Tutti i componenti di base per le applicazioni di realtà mista sono esposti in modo coerente con altre API di Unity e sono disponibili anche tramite Mixed Reality Toolkit.
* [Fotocamera](camera-in-unity.md)
* [Sistemi di coordinate](coordinate-systems-in-unity.md)
* [Sguardo fisso](gaze-in-unity.md)
* [Movimenti e controller del movimento](gestures-and-motion-controllers-in-unity.md)
* [Input vocale](voice-input-in-unity.md)
* [Persistenza](persistence-in-unity.md)
* [Audio spaziale](spatial-sound-in-unity.md)
* [Mapping spaziale](spatial-mapping-in-unity.md)

Esistono altre funzionalità importanti che sono richieste in molte applicazioni di realtà mista e sono esposte anche alle app Unity:
* [Esperienze condivise](shared-experiences-in-unity.md)
* [Fotocamera individuabile](locatable-camera-in-unity.md)
* [Punto di interesse](focus-point-in-unity.md)
* [Perdita del tracciamento](tracking-loss-in-unity.md)
* [Tastiera](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Esecuzione del progetto Unity in un dispositivo reale o simulato

Non appena il progetto Unity olografico è pronto per il test, il passaggio successivo è quello di [esportare e compilare una soluzione Unity di Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md).

Con questa soluzione di Visual Studio, potrai eseguire l'applicazione in uno dei tre modi seguenti, usando un dispositivo reale o simulato:
* [Distribuire l'applicazione in un visore VR immersive di HoloLens o Windows Mixed Reality](using-visual-studio.md)
* [Distribuire l'applicazione nell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Distribuire l'applicazione nel simulatore del visore VR immersive di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentazione di Unity

Oltre a questa documentazione disponibile in docs.microsoft.com, è disponibile la documentazione di Unity relativa alle funzionalità di Windows Mixed Reality, che viene installata insieme all'editor di Unity. La documentazione fornita da Unity include due sezioni separate:
1. **Informazioni di riferimento sullo scripting di Unity**
    * Questa sezione contiene i dettagli dell'API di scripting fornita da Unity.
    * È accessibile dall'editor di Unity tramite **Help > Scripting Reference** (Guida > Riferimento scripting)
2. **Manuale di Unity**
    * Questo manuale è stato progettato per facilitare l'utente nel processo di apprendimento di Unity, dalle tecniche di base a quelle più avanzate.
    * È accessibile dall'editor di Unity tramite **Help > Manual** (Guida > Manuale)

## <a name="see-also"></a>Vedere anche
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Nozioni di base MR 100: Introduzione a Unity](holograms-100.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Uso dello spazio dei nomi Windows con le app Unity per HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedure consigliate per l'uso con Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modalità di gioco Unity](unity-play-mode.md)
* [Guide alla conversione](porting-guides.md)
