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
# <a name="1-introduction"></a><span data-ttu-id="f7eea-105">1. Introduzione</span><span class="sxs-lookup"><span data-stu-id="f7eea-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="f7eea-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="f7eea-106">Overview</span></span>

<span data-ttu-id="f7eea-107">Esercitazioni su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="f7eea-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="f7eea-108">Con questa serie di esercitazioni si apprenderanno le nozioni di base di <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a> (ASA) e le procedure per ancorare un'esperienza di realtà mista completa al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="f7eea-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="f7eea-109">Si apprenderà anche come distribuire il progetto in Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="f7eea-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="f7eea-110">Esercitazioni di questa serie:</span><span class="sxs-lookup"><span data-stu-id="f7eea-110">Tutorials in this series:</span></span>

1. [<span data-ttu-id="f7eea-111">Introduzione</span><span class="sxs-lookup"><span data-stu-id="f7eea-111">Introduction</span></span>](mr-learning-asa-01.md)
2. [<span data-ttu-id="f7eea-112">Introduzione ad Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="f7eea-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="f7eea-113">Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="f7eea-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="f7eea-114">Visualizzazione del feedback su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="f7eea-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="f7eea-115">Ancoraggi nello spazio di Azure per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="f7eea-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="f7eea-116">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f7eea-116">Objectives</span></span>

* <span data-ttu-id="f7eea-117">Imparare a creare ancoraggi nello spazio e recuperarli da Azure</span><span class="sxs-lookup"><span data-stu-id="f7eea-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="f7eea-118">Imparare a ottenere l'allineamento spaziale tra le sessioni dell'app</span><span class="sxs-lookup"><span data-stu-id="f7eea-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="f7eea-119">Imparare a ottenere l'allineamento spaziale tra più dispositivi</span><span class="sxs-lookup"><span data-stu-id="f7eea-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="f7eea-120">Imparare a preparare, creare e distribuire il progetto in Android e iOS</span><span class="sxs-lookup"><span data-stu-id="f7eea-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7eea-121">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="f7eea-121">Prerequisites</span></span>

* <span data-ttu-id="f7eea-122">Un computer Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="f7eea-122">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="f7eea-123">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="f7eea-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="f7eea-124">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="f7eea-124">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="f7eea-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo Universal Windows Platform Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="f7eea-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="f7eea-126">Completamento della sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="f7eea-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="f7eea-127">Completamento della serie di [esercitazioni introduttive](mr-learning-base-01.md) o di esperienze di base precedenti con Unity e MRTK</span><span class="sxs-lookup"><span data-stu-id="f7eea-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="f7eea-128">Completamento della serie di [esercitazioni sugli Ancoraggi nello spazio di Azure](mr-learning-asa-01.md) o di esperienze precedenti sulla creazione di un account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="f7eea-128">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or previous experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="f7eea-129">Se è prevista la distribuzione in Android e HoloLens</span><span class="sxs-lookup"><span data-stu-id="f7eea-129">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="f7eea-130">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">con le opzioni di sviluppo abilitate</a> e <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">supportato da ARCore</a> con connessione USB a un computer con Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="f7eea-130">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="f7eea-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo Android Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="f7eea-131"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="f7eea-132">Se è prevista la distribuzione in iOS e HoloLens</span><span class="sxs-lookup"><span data-stu-id="f7eea-132">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="f7eea-133">Un computer macOS con la versione più recente di <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installata</span><span class="sxs-lookup"><span data-stu-id="f7eea-133">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="f7eea-134">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatibile con ARKit</a> con connessione USB al computer macOS</span><span class="sxs-lookup"><span data-stu-id="f7eea-134">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="f7eea-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 installato e il modulo iOS Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="f7eea-135"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="f7eea-136">La versione di Mixed Reality Toolkit consigliata per questa serie di esercitazioni è MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="f7eea-136">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="f7eea-137">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="f7eea-137">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="f7eea-138">Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="f7eea-138">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="f7eea-139">Esercitazione successiva: 2. Introduzione ad Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="f7eea-139">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
