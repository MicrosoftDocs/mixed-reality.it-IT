---
title: Esercitazioni sulle funzionalità multiutente-1. Configurazione della rete di Photon Unity
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: c6a2bea3d50669000e81cad7c83ae6a69b8a847f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437743"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="704bf-105">1. configurazione della rete di Photon Unity</span><span class="sxs-lookup"><span data-stu-id="704bf-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="704bf-106">In questa esercitazione si apprenderà come preparare la creazione di un'esperienza condivisa importando la rete di Photon Unity (PUN) nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="704bf-106">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="704bf-107">Photon è una delle diverse opzioni di rete disponibili agli sviluppatori di realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="704bf-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="704bf-108">Si apprenderà come creare un account Photon, importare un fotone e creare un server locale facoltativo</span><span class="sxs-lookup"><span data-stu-id="704bf-108">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="704bf-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="704bf-109">Objectives</span></span>

* <span data-ttu-id="704bf-110">Informazioni su come creare un account Photon</span><span class="sxs-lookup"><span data-stu-id="704bf-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="704bf-111">Informazioni su come trovare e importare la rete di Photon Unity</span><span class="sxs-lookup"><span data-stu-id="704bf-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="704bf-112">Configurare un server Photon locale</span><span class="sxs-lookup"><span data-stu-id="704bf-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="704bf-113">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="704bf-113">Setting up Photon</span></span>

1. <span data-ttu-id="704bf-114">Configurare un account [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="704bf-114">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="704bf-115">Passare alla pagina di iscrizione a Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="704bf-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="704bf-116">Seguire le istruzioni nella pagina di iscrizione per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="704bf-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="704bf-119">Creare un ID applicazione facendo clic sul pulsante Crea una nuova app.</span><span class="sxs-lookup"><span data-stu-id="704bf-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="704bf-121">Selezionare Photon PUN dal menu a discesa in tipo di fotone.</span><span class="sxs-lookup"><span data-stu-id="704bf-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="704bf-122">Assegnare quindi un nome.</span><span class="sxs-lookup"><span data-stu-id="704bf-122">Then give it a name.</span></span> <span data-ttu-id="704bf-123">In questo esempio, il nome è HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="704bf-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="704bf-124">Al termine, fare clic sul pulsante Crea.</span><span class="sxs-lookup"><span data-stu-id="704bf-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="704bf-126">Tornare alla pagina delle applicazioni. verrà visualizzata una schermata simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="704bf-126">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="704bf-127">Fare clic sull'ID applicazione e copiarlo.</span><span class="sxs-lookup"><span data-stu-id="704bf-127">Click the application ID and copy it.</span></span> <span data-ttu-id="704bf-128">Incollarlo in un'altra posizione a cui è possibile accedere facilmente.</span><span class="sxs-lookup"><span data-stu-id="704bf-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="704bf-130">Creare un nuovo progetto Unity e denominarlo HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="704bf-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="704bf-131">Per istruzioni su come creare un nuovo progetto Unity, vedere [la sezione "creare un progetto Unity" del modulo di base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="704bf-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="704bf-132">Una volta caricato il progetto, fare clic sulla scheda Archivio risorse, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="704bf-132">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="704bf-133">Quindi, nella casella di ricerca evidenziata nell'immagine riportata di seguito, digitare PUN e selezionare l'asset Photon PUN 2-FREE "dai risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="704bf-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="704bf-135">Scaricare e importare questo asset premendo i pulsanti Scarica e importa.</span><span class="sxs-lookup"><span data-stu-id="704bf-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="704bf-137">Dopo che il fotone ha completato il processo di importazione, viene visualizzata la procedura guidata di pun.</span><span class="sxs-lookup"><span data-stu-id="704bf-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="704bf-138">Prendere l'ID applicazione, che dovrebbe trovarsi negli Appunti, dal passaggio 4, incollarlo nella casella AppID e premere il pulsante Imposta progetto.</span><span class="sxs-lookup"><span data-stu-id="704bf-138">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="704bf-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="704bf-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="704bf-140">Dopo aver aggiunto l'AppID, passare a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets.</span><span class="sxs-lookup"><span data-stu-id="704bf-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="704bf-141">Selezionare l'opzione Usa il server dei nomi e impostare l'area fissa su US o l'area del servizio Photon.</span><span class="sxs-lookup"><span data-stu-id="704bf-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="704bf-143">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="704bf-143">Congratulations</span></span>

<span data-ttu-id="704bf-144">È stato creato un account Photon, configurato un server Photon locale e il PUN è stato importato in Unity.</span><span class="sxs-lookup"><span data-stu-id="704bf-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="704bf-145">Il passaggio successivo consiste nell'impostare il progetto e consentire le connessioni con altri utenti in modo che più utenti possano visualizzare il lavoro.</span><span class="sxs-lookup"><span data-stu-id="704bf-145">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="704bf-146">[Esercitazione successiva: 2. preparazione di Unity per lo sviluppo](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="704bf-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

