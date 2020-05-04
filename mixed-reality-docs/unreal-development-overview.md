---
title: Panoramica dello sviluppo con Unreal
description: Guida introduttiva alla creazione di app di realtà mista in Unreal.
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, streaming, controllo remoto, realtà mista, sviluppo, guida introduttiva, nuovo progetto, emulatore, documentazione
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491178"
---
# <a name="unreal-development-overview"></a>Panoramica dello sviluppo con Unreal

Il supporto della realtà mista per Unreal Engine 4 è ora disponibile in versione beta. Se non hai familiarità con lo sviluppo in Unreal, l'<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">introduzione a Unreal Engine 4</a> è un ottimo articolo da cui iniziare. Se hai bisogno di asset, Unreal offre un <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a> completo. 

Una volta acquisita la conoscenza di base di Unreal Engine 4, puoi visitare la pagina relativa allo <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">sviluppo per Microsoft HoloLens</a> nel sito della documentazione di Unreal Engine per imparare a compilare ed eseguire le app in HoloLens. Visita i <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">forum di Unreal relativi alla realtà mista</a> per collaborare con i membri della community impegnati a creare app di realtà mista in Unreal. È il luogo ideale in cui trovare le soluzioni ai problemi che potresti incontrare.

## <a name="installing-the-prerequisites"></a>Installazione dei prerequisiti

Per iniziare a creare un'app HoloLens 2 in Unreal, devi disporre dell'[emulatore HoloLens 2](using-the-hololens-emulator.md) o di un visore VR HoloLens. Devi inoltre installare l'ultima versione di Visual Studio con i carichi di lavoro e i componenti elencati in <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">HoloLens 2 Prerequisites for Unreal</a> (Prerequisiti di HoloLens 2 per Unreal).

## <a name="building-and-running-your-unreal-app"></a>Compilazione ed esecuzione dell'app Unreal

Prima di tutto, <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">crea un pacchetto dell'app per HoloLens 2</a>. Scegli quindi dove vuoi distribuire il pacchetto:
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">Distribuire nell'emulatore HoloLens 2</a>
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">Distribuire in un visore VR di HoloLens 2</a>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a>Trasmetti in streaming l'app a un visore VR tramite Holographic Remoting Player

La trasmissione in streaming dell'app dal desktop all'app Holographic Remoting Player su un visore VR di HoloLens presenta due vantaggi principali: 
* Accelera le attività di sviluppo, evitando di dover creare ogni volta un nuovo pacchetto e caricare l'app ogni volta che vengono apportate modifiche
* Sfrutta la potenza del desktop, in modo da poter eseguire il rendering di tutti i poligoni consentiti dalla GPU del desktop, senza essere limitati dalla capacità del computer disponibile nel visore VR

Per acquisire familiarità con lo streaming, vedi <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 Streaming Quick Start</a>[]() (Avvio rapido allo streaming in HoloLens 2).

## <a name="see-also"></a>Vedere anche
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a> (Linee guida sulle prestazioni di Unreal per i dispositivi mobili)
