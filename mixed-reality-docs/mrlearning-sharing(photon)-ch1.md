---
title: Esercitazioni sulle funzionalità multiutente-1. Configurazione della rete di Photon Unity
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 57a23e34404e4bff653d74b7f6afc65adff8b19c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334338"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="56e22-105">1. configurazione della rete di Photon Unity</span><span class="sxs-lookup"><span data-stu-id="56e22-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="56e22-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="56e22-106">Overview</span></span>

<span data-ttu-id="56e22-107">In questa esercitazione si apprenderà come preparare la creazione di un'esperienza condivisa importando la rete di Photon Unity (PUN) nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="56e22-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="56e22-108">Photon è una delle diverse opzioni di rete disponibili agli sviluppatori di realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="56e22-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="56e22-109">Si apprenderà come creare un account Photon, importare un fotone e creare un server locale facoltativo</span><span class="sxs-lookup"><span data-stu-id="56e22-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="56e22-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="56e22-110">Objectives</span></span>

* <span data-ttu-id="56e22-111">Informazioni su come creare un account Photon</span><span class="sxs-lookup"><span data-stu-id="56e22-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="56e22-112">Informazioni su come trovare e importare la rete di Photon Unity</span><span class="sxs-lookup"><span data-stu-id="56e22-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="56e22-113">Configurare un server Photon locale</span><span class="sxs-lookup"><span data-stu-id="56e22-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56e22-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="56e22-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="56e22-115">Se non è ancora stata completata la serie di [esercitazioni introduttive](mrlearning-base.md) , è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="56e22-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="56e22-116">Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="56e22-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="56e22-117">Windows 10 SDK 10.0.18362.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="56e22-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="56e22-118">Funzionalità di C# programmazione di base</span><span class="sxs-lookup"><span data-stu-id="56e22-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="56e22-119">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="56e22-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="56e22-120">Questa serie di esercitazioni richiede <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> e la versione consigliata è Unity 2019.1.14.</span><span class="sxs-lookup"><span data-stu-id="56e22-120">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="56e22-121">Questa operazione sostituisce i requisiti di versione di Unity o i consigli indicati nei prerequisiti collegati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="56e22-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="56e22-122">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="56e22-122">Setting up Photon</span></span>

1. <span data-ttu-id="56e22-123">Configurare un account [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="56e22-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="56e22-124">Passare alla pagina di iscrizione a Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="56e22-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="56e22-125">Seguire le istruzioni nella pagina di iscrizione per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="56e22-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="56e22-128">Creare un ID applicazione facendo clic sul pulsante Crea una nuova app.</span><span class="sxs-lookup"><span data-stu-id="56e22-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="56e22-130">Selezionare Photon PUN dal menu a discesa in tipo di fotone.</span><span class="sxs-lookup"><span data-stu-id="56e22-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="56e22-131">Assegnare quindi un nome.</span><span class="sxs-lookup"><span data-stu-id="56e22-131">Then give it a name.</span></span> <span data-ttu-id="56e22-132">In questo esempio, il nome è HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="56e22-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="56e22-133">Al termine, fare clic sul pulsante Crea.</span><span class="sxs-lookup"><span data-stu-id="56e22-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="56e22-135">Tornare alla pagina delle applicazioni. verrà visualizzata una schermata simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="56e22-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="56e22-136">Fare clic sull'ID applicazione e copiarlo.</span><span class="sxs-lookup"><span data-stu-id="56e22-136">Click the application ID and copy it.</span></span> <span data-ttu-id="56e22-137">Incollarlo in un'altra posizione a cui è possibile accedere facilmente.</span><span class="sxs-lookup"><span data-stu-id="56e22-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="56e22-139">Creare un nuovo progetto Unity e denominarlo HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="56e22-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="56e22-140">Per istruzioni su come creare un nuovo progetto Unity, vedere [la sezione "creare un progetto Unity" del modulo di base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="56e22-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="56e22-141">Una volta caricato il progetto, fare clic sulla scheda Archivio risorse, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="56e22-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="56e22-142">Quindi, nella casella di ricerca evidenziata nell'immagine riportata di seguito, digitare PUN e selezionare l'asset Photon PUN 2-FREE "dai risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="56e22-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="56e22-144">Scaricare e importare questo asset premendo i pulsanti Scarica e importa.</span><span class="sxs-lookup"><span data-stu-id="56e22-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="56e22-146">Dopo che il fotone ha completato il processo di importazione, viene visualizzata la procedura guidata di pun.</span><span class="sxs-lookup"><span data-stu-id="56e22-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="56e22-147">Prendere l'ID applicazione, che dovrebbe trovarsi negli Appunti, dal passaggio 4, incollarlo nella casella AppID e premere il pulsante Imposta progetto.</span><span class="sxs-lookup"><span data-stu-id="56e22-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="56e22-149">Dopo aver aggiunto l'AppID, passare a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets.</span><span class="sxs-lookup"><span data-stu-id="56e22-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="56e22-150">Selezionare l'opzione Usa il server dei nomi e impostare l'area fissa su US o l'area del servizio Photon.</span><span class="sxs-lookup"><span data-stu-id="56e22-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="56e22-152">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="56e22-152">Congratulations</span></span>

<span data-ttu-id="56e22-153">È stato creato un account Photon, configurato un server Photon locale e il PUN è stato importato in Unity.</span><span class="sxs-lookup"><span data-stu-id="56e22-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="56e22-154">Il passaggio successivo consiste nell'impostare il progetto e consentire le connessioni con altri utenti in modo che più utenti possano visualizzare il lavoro.</span><span class="sxs-lookup"><span data-stu-id="56e22-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="56e22-155">[Esercitazione successiva: 2. preparazione di Unity per lo sviluppo](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="56e22-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
