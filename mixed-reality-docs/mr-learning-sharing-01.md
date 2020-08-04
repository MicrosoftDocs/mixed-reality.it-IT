---
title: Esercitazioni sulle funzionalità multiutente - 1. Introduzione
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: ebdef9818aace28b32e91384cd9d3278da2733b4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376343"
---
# <a name="1-introduction"></a><span data-ttu-id="fc151-105">1. Introduzione</span><span class="sxs-lookup"><span data-stu-id="fc151-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="fc151-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="fc151-106">Overview</span></span>

<span data-ttu-id="fc151-107">Esercitazioni sulle funzionalità multiutente</span><span class="sxs-lookup"><span data-stu-id="fc151-107">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="fc151-108">Con questa serie di esercitazioni si apprenderanno le nozioni di base per la creazione di un'esperienza multiutente usando <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span><span class="sxs-lookup"><span data-stu-id="fc151-108">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="fc151-109">PUN è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="fc151-109">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="fc151-110">Esercitazioni di questa serie:</span><span class="sxs-lookup"><span data-stu-id="fc151-110">Tutorials in this series:</span></span>

* [<span data-ttu-id="fc151-111">Configurazione di Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="fc151-111">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="fc151-112">Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="fc151-112">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="fc151-113">Condivisione dei movimenti di oggetti con più utenti</span><span class="sxs-lookup"><span data-stu-id="fc151-113">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="fc151-114">Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="fc151-114">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="fc151-115">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="fc151-115">Objectives</span></span>

* <span data-ttu-id="fc151-116">Imparare a creare un'app PUN e a connettere il progetto Unity all'app</span><span class="sxs-lookup"><span data-stu-id="fc151-116">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="fc151-117">Imparare a connettere più utenti in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="fc151-117">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="fc151-118">Imparare a condividere i movimenti degli oggetti con altri utenti</span><span class="sxs-lookup"><span data-stu-id="fc151-118">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="fc151-119">Imparare a ottenere l'allineamento spaziale tra più dispositivi</span><span class="sxs-lookup"><span data-stu-id="fc151-119">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc151-120">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="fc151-120">Prerequisites</span></span>

* <span data-ttu-id="fc151-121">Un computer Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="fc151-121">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="fc151-122">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="fc151-122">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="fc151-123">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="fc151-123">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="fc151-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo Universal Windows Platform Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="fc151-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="fc151-125">Completamento della sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="fc151-125">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="fc151-126">Completamento della serie di [esercitazioni introduttive](mr-learning-base-01.md) o di esperienze di base precedenti con Unity e MRTK</span><span class="sxs-lookup"><span data-stu-id="fc151-126">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="fc151-127">Completamento della serie di [esercitazioni sugli Ancoraggi nello spazio di Azure](mr-learning-asa-01.md) o di esperienze precedenti sulla creazione di un account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="fc151-127">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="fc151-128">Se è prevista la distribuzione in Android e HoloLens</span><span class="sxs-lookup"><span data-stu-id="fc151-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="fc151-129">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">con le opzioni di sviluppo abilitate</a> e <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">supportato da ARCore</a> con connessione USB a un computer con Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="fc151-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="fc151-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo Android Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="fc151-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="fc151-131">Se è prevista la distribuzione in iOS e HoloLens</span><span class="sxs-lookup"><span data-stu-id="fc151-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="fc151-132">Un computer macOS con la versione più recente di <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installata</span><span class="sxs-lookup"><span data-stu-id="fc151-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="fc151-133">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatibile con ARKit</a> con connessione USB al computer macOS</span><span class="sxs-lookup"><span data-stu-id="fc151-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="fc151-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo iOS Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="fc151-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="fc151-135">La versione di Mixed Reality Toolkit consigliata per questa serie di esercitazioni è MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="fc151-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="fc151-136">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="fc151-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="fc151-137">Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="fc151-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="fc151-138">Esercitazione successiva: 2. Configurazione di Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="fc151-138">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
