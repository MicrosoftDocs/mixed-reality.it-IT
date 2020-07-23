---
title: Esercitazioni sulle funzionalità multiutente - 1. Introduzione
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: eff600ba6388732ab9aa200ce41494cac1dddf35
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305827"
---
# <a name="1-introduction"></a>1. Introduzione

## <a name="overview"></a>Panoramica

Esercitazioni sulle funzionalità multiutente Con questa serie di esercitazioni si apprenderanno le nozioni di base per la creazione di un'esperienza multiutente usando <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN). PUN è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise.

Esercitazioni di questa serie:

* [Configurazione di Photon Unity Networking](mr-learning-sharing-02.md)
* [Connessione di più utenti](mr-learning-sharing-03.md)
* [Condivisione dei movimenti di oggetti con più utenti](mr-learning-sharing-04.md)
* [Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa](mr-learning-sharing-05.md)

## <a name="objectives"></a>Obiettivi

* Imparare a creare un'app PUN e a connettere il progetto Unity all'app
* Imparare a connettere più utenti in un'esperienza condivisa
* Imparare a condividere i movimenti degli oggetti con altri utenti
* Imparare a ottenere l'allineamento spaziale tra più dispositivi

## <a name="prerequisites"></a>Prerequisiti

* Un computer Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo Universal Windows Platform Build Support aggiunto
* Completamento della sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* Completamento della serie di [esercitazioni introduttive](mr-learning-base-01.md) o di esperienze di base precedenti con Unity e MRTK
* Completamento della serie di [esercitazioni sugli Ancoraggi nello spazio di Azure](mr-learning-asa-01.md) o di esperienze precedenti sulla creazione di un account di Ancoraggi nello spazio di Azure
* Se è prevista la distribuzione in Android e HoloLens
  * Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">con le opzioni di sviluppo abilitate</a> e <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">supportato da ARCore</a> con connessione USB a un computer con Windows o macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo Android Build Support aggiunto
* Se è prevista la distribuzione in iOS e HoloLens
  * Un computer macOS con la versione più recente di <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installata
  * Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatibile con ARKit</a> con connessione USB al computer macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo iOS Build Support aggiunto

> [!CAUTION]
> La versione di Mixed Reality Toolkit consigliata per questa serie di esercitazioni è MRTK 2.4.0.

> [!CAUTION]
> La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.3.15. Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.

[Esercitazione successiva: 2. Configurazione di Photon Unity Networking](mr-learning-sharing-02.md)
