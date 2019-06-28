---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416122"
---
# <a name="setting-up-photon"></a><span data-ttu-id="51f0b-104">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="51f0b-104">Setting Up Photon</span></span>

<span data-ttu-id="51f0b-105">In questa lezione si apprenderà come prepararsi per la creazione di un'esperienza condivisa tramite l'importazione di Networking Unity Photon (stato) nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="51f0b-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="51f0b-106">Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="51f0b-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="51f0b-107">Si si apprenderà come creare un account Photon, importare Photon e creare un server locale facoltativo</span><span class="sxs-lookup"><span data-stu-id="51f0b-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="51f0b-108">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="51f0b-108">Objectives:</span></span>

* <span data-ttu-id="51f0b-109">Informazioni su come creare account Photon</span><span class="sxs-lookup"><span data-stu-id="51f0b-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="51f0b-110">Informazioni su come individuare e importare Networking Unity Photon</span><span class="sxs-lookup"><span data-stu-id="51f0b-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="51f0b-111">Configurare un server locale Photon</span><span class="sxs-lookup"><span data-stu-id="51f0b-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="51f0b-112">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="51f0b-112">Setting Up Photon</span></span>

1. <span data-ttu-id="51f0b-113">Configurare un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span><span class="sxs-lookup"><span data-stu-id="51f0b-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="51f0b-114">Passare alla pagina di iscrizione Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="51f0b-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="51f0b-115">Seguire le istruzioni nella pagina di iscrizione per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="51f0b-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="51f0b-118">Creare un ID applicazione facendo clic sul pulsante "Crea una nuova app".</span><span class="sxs-lookup"><span data-stu-id="51f0b-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="51f0b-120">Selezionare "Photon considerato" nel menu a discesa in "tipo photon".</span><span class="sxs-lookup"><span data-stu-id="51f0b-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="51f0b-121">Assegnargli un nome, in questo esempio, è denominato "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="51f0b-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="51f0b-122">Al termine, fare clic sul pulsante "Crea".</span><span class="sxs-lookup"><span data-stu-id="51f0b-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="51f0b-124">Al termine dell'operazione, tornare alla pagina delle applicazioni e verrà visualizzato qualcosa di simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="51f0b-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="51f0b-125">Fare clic sull'ID dell'app e copiarlo.</span><span class="sxs-lookup"><span data-stu-id="51f0b-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="51f0b-126">Incolla è in una posizione che facilmente accessibile.</span><span class="sxs-lookup"><span data-stu-id="51f0b-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="51f0b-128">Creare un nuovo progetto unity e denominarla "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="51f0b-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="51f0b-129">Per istruzioni su come creare un nuovo progetto Unity, consultare [sezione "Creare progetto Unity" del modulo Base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="51f0b-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="51f0b-130">Una volta che il progetto viene caricato, fare clic sulla scheda "asset store", come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="51f0b-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="51f0b-131">Quindi, nella casella di ricerca evidenziata nell'immagine seguente, digitare "Stato" e selezionare l'asset "Photon stato 2 - gratuito" dai risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="51f0b-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="51f0b-133">Scaricare e importare questo asset facendo clic sul pulsante "Download" e "Import".</span><span class="sxs-lookup"><span data-stu-id="51f0b-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="51f0b-135">Una volta Photon completato il processo di importazione, verrà visualizzata la procedura guidata in poi.</span><span class="sxs-lookup"><span data-stu-id="51f0b-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="51f0b-136">Richiedere l'ID dell'applicazione (che deve essere copiata negli Appunti) del passaggio 4 e incollarlo nella casella di AppID e fare clic sul pulsante "Progetto di installazione".</span><span class="sxs-lookup"><span data-stu-id="51f0b-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="51f0b-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="51f0b-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="51f0b-138">Dopo aver aggiunto l'AppID, passare a "Photon"->"PhotonUnityNetworking" -> "Risorse" -> "PhotonServerSettings" negli asset.</span><span class="sxs-lookup"><span data-stu-id="51f0b-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="51f0b-139">Selezionare l'opzione "Usa nome Server" e impostare l'area fisso in "us" o l'area di servizio photon.</span><span class="sxs-lookup"><span data-stu-id="51f0b-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="51f0b-141">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="51f0b-141">Congratulations</span></span>

<span data-ttu-id="51f0b-142">Si hanno correttamente creato un account Photon configurare un server Photon locale e importato in poi in Unity.</span><span class="sxs-lookup"><span data-stu-id="51f0b-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="51f0b-143">Il passaggio successivo è impostare il progetto e quindi consentire le connessioni con altri utenti in modo che più utenti possono visualizzare il proprio lavoro.</span><span class="sxs-lookup"><span data-stu-id="51f0b-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="51f0b-144">[Lezione successiva: Sharing(photon) lezione 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="51f0b-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

