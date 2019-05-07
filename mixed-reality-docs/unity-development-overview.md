---
title: Panoramica sullo sviluppo per Unity
description: Recupero di iniziare a compilare mista le App per realtà in Unity.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mista realtà, sviluppo, Guida introduttiva, nuovo progetto, portabilità, funzionalità, fotocamera, simulazione, emulazione, documentazione
ms.openlocfilehash: 2cdcd5e997ab7e3f6d340377464e453a8e7c025c
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64874006"
---
# <a name="unity-development-overview"></a>Panoramica sullo sviluppo per Unity

Il percorso più veloce alla compilazione un' [app per realtà mista](app-views.md) riguarda [Unity](http://aka.ms/HoloLensUnity). È consigliabile eseguire il tempo necessario per esplorare le [esercitazioni di Unity](https://unity3d.com/learn/tutorials). Se è necessario asset, Unity ha una serie completa [Asset Store](https://www.assetstore.unity3d.com/). Dopo aver creato una conoscenza di base di Unity, è possibile visitare il [esercitazioni](tutorials.md) conoscere le specifiche di sviluppo di applicazioni di realtà mista con Unity. Assicurarsi di visitare il [forum di realtà mista di Unity](http://forum.unity3d.com/forums/hololens.102/) di interagire con il resto della community di creazione di App di realtà mista in Unity e trovare soluzioni ai problemi si verificano.


Per iniziare a compilare le App per realtà mista con Unity, innanzitutto [installare gli strumenti](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Nuovo progetto Unity con il Toolkit di realtà mista 

Il modo più semplice per sviluppare in Unity è con l'aiuto del Toolkit di realtà mista. Verrà consentono automaticamente si programma di installazione con project e forniscono un set di funzionalità di realtà mista per accelerare lo sviluppo. Consulta [Toolkit di realtà mista v2](mrtk-getting-started.md) per altre informazioni e iniziare a usare. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Porting di un'app esistente di Unity in Windows Mixed Reality

Se si dispone di un progetto Unity esistente che sta eseguendo il porting in Windows Mixed Reality, seguire le [Guida al porting di Unity](porting-guides.md) per iniziare.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Configurazione di nuovo progetto Unity per realtà mista di Windows

Se si vuole creare un nuovo progetto Unity senza importare Toolkit di realtà mista, sono disponibili un piccolo set di impostazioni di Unity, è necessario modificare manualmente per realtà mista di Windows, suddivise in due categorie: al progetto e per ogni scena. Vedere di seguito per istruzioni passo per passo per [configurare nuovi Unity Project per realtà mista di Windows](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Aggiunta di input e le funzionalità di realtà mista

Dopo che è stata configurata MRTK V2 con il progetto o configurato il progetto come descritto in precedenza, oggetti di gioco Unity standard (ad esempio la fotocamera) verranno visualizzati immediatamente per un **esperienza su scala seduto**, con la posizione della fotocamera aggiornata come l'utente si sposta automaticamente propria testa attraverso il mondo.

Aggiunta del supporto per le funzionalità di realtà mista di Windows, ad esempio [fasi spaziali](coordinate-systems.md#spatial-coordinate-systems), [movimenti, i controller di movimento](gestures-and-motion-controllers-in-unity.md) oppure [input vocale](voice-input-in-unity.md) avviene tramite le API incorporate direttamente in Unity. 

Il primo passaggio necessario per rivedere le [esperienza Scale](coordinate-systems.md) che può avere come destinazione l'app:
* Se si sta cercando di creare un **orientamento sola** o **scalabilità seduto esperienza**, è necessario impostare Unity del rilevamento tipo dello spazio a [fermo](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se si sta cercando di creare un **permanente-scale** o **esperienza su scala chat room**, è necessario assicurarsi di Unity spazio tipo di rilevamento è stata impostata su [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se si sta cercando di creare un **su scala mondiale** esperienza in HoloLens, consentire agli utenti di effettuare il roaming oltre i contatori di 5, è necessario utilizzare il [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) componente.

Tutti i componenti fondamentali per le app di realtà mista sono esposti in modo coerente con altre API di Unity. Sono anche disponibili tramite il Toolkit di realtà mista.
* [Fotocamera](camera-in-unity.md)
* [Sistemi di coordinate](coordinate-systems-in-unity.md)
* [Sguardo fisso](gaze-in-unity.md)
* [I movimenti e controller di movimento](gestures-and-motion-controllers-in-unity.md)
* [Input vocale](voice-input-in-unity.md)
* [Persistenza](persistence-in-unity.md)
* [Audio spaziale](spatial-sound-in-unity.md)
* [Mapping spaziale](spatial-mapping-in-unity.md)

Sono disponibili altre funzionalità chiave che molte app di realtà mista desidera usare, che sono visualizzate anche per le app Unity:
* [Esperienze condivise](shared-experiences-in-unity.md)
* [Fotocamera individuabile](locatable-camera-in-unity.md)
* [Punto di stato attivo](focus-point-in-unity.md)
* [Perdita di rilevamento](tracking-loss-in-unity.md)
* [Tastiera](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Esecuzione del progetto Unity in un dispositivo reale o simulato

Una volta il progetto Unity holographic pronti per eseguire il test, il passaggio successivo consiste [esportare e compilare una soluzione di Visual Studio a Unity](exporting-and-building-a-unity-visual-studio-solution.md).

Con tale soluzione di Visual Studio a disposizione, è possibile quindi eseguire l'app in uno dei tre modi, usando un dispositivo reale o simulato:
* [Distribuire un auricolare immersiva reale, HoloLens o realtà mista di Windows](using-visual-studio.md)
* [Distribuire l'emulatore di HoloLens](using-the-hololens-emulator.md)
* [Distribuire il simulatore immersive visore VR realtà mista di Windows](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentazione di Unity

Oltre a questa documentazione disponibile in Windows Dev Center, Unity installa la documentazione per la funzionalità di realtà mista di Windows con l'Editor di Unity. Unity fornita documentazione include due sezioni separate:
1. **Riferimento di scripting di Unity**
    * In questa sezione della documentazione contiene i dettagli dell'API di scripting che consente di Unity.
    * Accessibile dall'Editor di Unity tramite **Guida > riferimento agli script**
2. **Manuale di Unity**
    * Questo manuale è progettato per scoprire come usare Unity, dalle tecniche di base fino ad avanzate.
    * Accessibile dall'Editor di Unity tramite **Guida > manuale**

## <a name="see-also"></a>Vedere anche
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Nozioni di base MR 100: Introduzione a Unity](holograms-100.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Uso dello spazio dei nomi Windows con le app Unity per HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedure consigliate per l'uso con Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modalità di gioco Unity](unity-play-mode.md)
* [Porting di guide](porting-guides.md)
