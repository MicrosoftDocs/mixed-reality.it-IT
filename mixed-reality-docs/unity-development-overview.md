---
title: Panoramica sullo sviluppo Unity
description: Guida introduttiva alla creazione di app per realtà mista in Unity.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto, porting, funzionalità, fotocamera, simulazione, emulazione, documentazione
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414517"
---
# <a name="unity-development-overview"></a>Panoramica sullo sviluppo Unity

Il percorso più veloce per la creazione di un' [app per realtà mista](app-views.md) è con [Unity](http://aka.ms/HoloLensUnity). Si consiglia di prendere tempo per esplorare le esercitazioni su [Unity](https://unity3d.com/learn/tutorials). Se sono necessarie risorse, Unity dispone di un [Archivio asset](https://www.assetstore.unity3d.com/)completo. Una volta creata una conoscenza di base di Unity, è possibile visitare le [esercitazioni](tutorials.md) per apprendere le specifiche dello sviluppo di realtà miste con Unity. Visitare i [forum in realtà mista](http://forum.unity3d.com/forums/hololens.102/) di Unity per coinvolgere il resto della community sulla creazione di app per realtà mista in Unity e trovare soluzioni ai problemi che potrebbero verificarsi.


Per iniziare a creare app per realtà miste con Unity, [installare prima gli strumenti](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Nuovo progetto Unity con il Toolkit di realtà misto 

Il modo più semplice per sviluppare in Unity è costituito dal supporto di Mixed Reality Toolkit. Consente di configurare automaticamente con Project e di fornire un set di funzionalità di realtà mista per accelerare lo sviluppo. Per altre informazioni e per iniziare, vedere il [Toolkit di realtà misto V2](mrtk-getting-started.md) . 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Porting di un'app Unity esistente a realtà mista di Windows

Se si dispone di un progetto Unity esistente che si sta trasportando a realtà mista di Windows, seguire la [Guida](porting-guides.md) per il porting di Unity per iniziare.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Configurazione del nuovo progetto Unity per la realtà mista di Windows

Se si vuole creare un nuovo progetto Unity senza importare il Toolkit di realtà mista, è necessario modificare manualmente le impostazioni di Unity per la realtà mista di Windows. Questi sono suddivisi in due categorie: per progetto e per scena. Vedere qui per la guida dettagliata alla [configurazione del nuovo progetto Unity per la realtà mista di Windows](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Aggiunta di input e funzionalità di realtà mista

Dopo aver configurato MRTK V2 con il progetto o aver configurato il progetto come descritto in precedenza, gli oggetti di gioco Unity standard (ad esempio la fotocamera) si illumineranno immediatamente per un' **esperienza**a scalabilità, con la posizione della fotocamera aggiornata automaticamente come l'utente sposta l'intestazione nel mondo.

L'aggiunta del supporto per le funzionalità di realtà mista di Windows, ad esempio [fasi spaziali](coordinate-systems.md#spatial-coordinate-systems), [movimenti, controller di movimento](gestures-and-motion-controllers-in-unity.md) o [input vocale](voice-input-in-unity.md) , viene ottenuta usando le API compilate direttamente in Unity. 

Esaminare prima di tutto le [scale di esperienza](coordinate-systems.md) che possono essere destinate alla Applicatioin:
* Se si sta cercando di creare un' **esperienza**di **solo orientamento** o di scalabilità verticale, è necessario impostare il tipo di spazio di rilevamento di Unity su [stazionari](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se si sta cercando di creare un'  esperienza di scalabilità o scalabilità, è necessario assicurarsi che il tipo di spazio di rilevamento di Unity sia impostato correttamente su [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se si vuole creare un'esperienza **globale** su HoloLens che consente agli utenti di spostarsi oltre 5 metri, è necessario usare il componente [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) .

Tutti i componenti di base per le applicazioni di realtà miste sono esposti in modo coerente con altre API Unity. Sono disponibili anche tramite il Toolkit di realtà mista.
* [Fotocamera](camera-in-unity.md)
* [Sistemi di coordinate](coordinate-systems-in-unity.md)
* [Sguardo fisso](gaze-in-unity.md)
* [Movimenti e controller di movimento](gestures-and-motion-controllers-in-unity.md)
* [Input vocale](voice-input-in-unity.md)
* [Persistenza](persistence-in-unity.md)
* [Audio spaziale](spatial-sound-in-unity.md)
* [Mapping spaziale](spatial-mapping-in-unity.md)

Sono disponibili altre funzionalità chiave che molte applicazioni di realtà miste vorranno usare che sono esposte anche alle app Unity:
* [Esperienze condivise](shared-experiences-in-unity.md)
* [Fotocamera individuabile](locatable-camera-in-unity.md)
* [Punto di interesse](focus-point-in-unity.md)
* [Perdita di rilevamento](tracking-loss-in-unity.md)
* [Tastiera](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Esecuzione del progetto Unity in un dispositivo reale o simulato

Una volta che il progetto di Unity olografico è pronto per il test, il passaggio successivo consiste nell' [esportare e compilare una soluzione Unity di Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md).

Con questa soluzione di Visual Studio, è possibile eseguire l'applicazione in uno dei tre modi seguenti, usando un dispositivo reale o simulato:
* [Eseguire la distribuzione in un HoloLens reale o in una serie di realtà mista di Windows](using-visual-studio.md)
* [Eseguire la distribuzione nell'emulatore di HoloLens](using-the-hololens-emulator.md)
* [Eseguire la distribuzione nel simulatore di Windows misto realismo per cuffie](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentazione di Unity

Oltre a questa documentazione disponibile in Windows Dev Center, Unity installa la documentazione per la funzionalità di realtà mista di Windows insieme all'editor di Unity. La documentazione fornita da Unity include due sezioni separate:
1. **Informazioni di riferimento sullo scripting Unity**
    * Questa sezione della documentazione contiene i dettagli dell'API di scripting fornita da Unity.
    * Accessibile dall'editor di Unity tramite **guida > riferimento di script**
2. **Unity manuale**
    * Questo manuale è stato progettato per aiutare l'utente a imparare a usare Unity, dalle tecniche di base a quelle avanzate.
    * Accessibile dall'editor di Unity tramite **guida > manuale**

## <a name="see-also"></a>Vedere anche
* [Toolkit di realtà mista V2](mrtk-getting-started.md)
* [Nozioni di base MR 100: Introduzione a Unity](holograms-100.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Uso dello spazio dei nomi Windows con le app Unity per HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedure consigliate per l'uso con Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modalità di gioco Unity](unity-play-mode.md)
* [Guide al porting](porting-guides.md)
