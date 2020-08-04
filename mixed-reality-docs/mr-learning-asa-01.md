---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 1. Introduzione
description: Completare questo corso per imparare a implementare Ancoraggi nello spazio di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: f273c573d40b1e65e325bd31b5dd9e14c1ee66ec
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376553"
---
# <a name="1-introduction"></a>1. Introduzione

## <a name="overview"></a>Panoramica

Esercitazioni su Ancoraggi nello spazio di Azure Con questa serie di esercitazioni si apprenderanno le nozioni di base di <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a> (ASA) e le procedure per ancorare un'esperienza di realtà mista completa al mondo reale. Si apprenderà anche come distribuire il progetto in Android e iOS.

Esercitazioni di questa serie:

1. [Introduzione](mr-learning-asa-01.md)
2. [Introduzione ad Ancoraggi nello spazio di Azure](mr-learning-asa-02.md)
3. [Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure](mr-learning-asa-03.md)
4. [Visualizzazione del feedback su Ancoraggi nello spazio di Azure](mr-learning-asa-04.md)
5. [Ancoraggi nello spazio di Azure per Android e iOS](mr-learning-asa-05.md)

## <a name="objectives"></a>Obiettivi

* Imparare a creare ancoraggi nello spazio e recuperarli da Azure
* Imparare a ottenere l'allineamento spaziale tra le sessioni dell'app
* Imparare a ottenere l'allineamento spaziale tra più dispositivi
* Imparare a preparare, creare e distribuire il progetto in Android e iOS

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

[Esercitazione successiva: 2. Introduzione ad Ancoraggi nello spazio di Azure](mr-learning-asa-02.md)
