---
title: Modulo MR Learning sharing per HoloLens 2
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: e40cd50f75ca509c601d215cb865161ea3596565
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293648"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="23224-104">Configurazione della rete di Photon Unity</span><span class="sxs-lookup"><span data-stu-id="23224-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="23224-105">Questa esercitazione illustra come prepararsi per la creazione di un'esperienza condivisa importando la rete di Photon Unity (PUN) nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="23224-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="23224-106">Photon è una delle diverse opzioni di rete disponibili agli sviluppatori di realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="23224-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="23224-107">Si apprenderà come creare un account Photon, importare un fotone e creare un server locale facoltativo</span><span class="sxs-lookup"><span data-stu-id="23224-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="23224-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="23224-108">Objectives:</span></span>

* <span data-ttu-id="23224-109">Informazioni su come creare un account Photon</span><span class="sxs-lookup"><span data-stu-id="23224-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="23224-110">Informazioni su come trovare e importare la rete di Photon Unity</span><span class="sxs-lookup"><span data-stu-id="23224-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="23224-111">Configurare un server Photon locale</span><span class="sxs-lookup"><span data-stu-id="23224-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="23224-112">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="23224-112">Setting up Photon</span></span>

1. <span data-ttu-id="23224-113">Configurare un account [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="23224-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="23224-114">Passare alla pagina di iscrizione a Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="23224-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="23224-115">Seguire le istruzioni nella pagina di iscrizione per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="23224-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="23224-118">Creare un ID applicazione facendo clic sul pulsante Crea una nuova app.</span><span class="sxs-lookup"><span data-stu-id="23224-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="23224-120">Selezionare Photon PUN dal menu a discesa in tipo di fotone.</span><span class="sxs-lookup"><span data-stu-id="23224-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="23224-121">Assegnare quindi un nome.</span><span class="sxs-lookup"><span data-stu-id="23224-121">Then give it a name.</span></span> <span data-ttu-id="23224-122">In questo esempio, il nome è HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="23224-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="23224-123">Al termine, fare clic sul pulsante Crea.</span><span class="sxs-lookup"><span data-stu-id="23224-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="23224-125">Al termine, tornare alla pagina delle applicazioni. verrà visualizzata una schermata simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="23224-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="23224-126">Fare clic sull'ID applicazione e copiarlo.</span><span class="sxs-lookup"><span data-stu-id="23224-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="23224-127">Incollarlo in un'altra posizione a cui è possibile accedere facilmente.</span><span class="sxs-lookup"><span data-stu-id="23224-127">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="23224-129">Creare un nuovo progetto Unity e denominarlo HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="23224-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="23224-130">Per istruzioni su come creare un nuovo progetto Unity, vedere [la sezione "creare un progetto Unity" del modulo di base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="23224-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="23224-131">Una volta caricato il progetto, fare clic sulla scheda Archivio risorse, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="23224-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="23224-132">Quindi, nella casella di ricerca evidenziata nell'immagine riportata di seguito, digitare PUN e selezionare l'asset Photon PUN 2-FREE "dai risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="23224-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="23224-134">Scaricare e importare questo asset premendo i pulsanti Scarica e importa.</span><span class="sxs-lookup"><span data-stu-id="23224-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="23224-136">Dopo che il fotone ha completato il processo di importazione, viene visualizzata la procedura guidata di pun.</span><span class="sxs-lookup"><span data-stu-id="23224-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="23224-137">Prendere l'ID applicazione, che dovrebbe trovarsi negli Appunti, dal passaggio 4 e incollarlo nella casella AppID e premere il pulsante Imposta progetto.</span><span class="sxs-lookup"><span data-stu-id="23224-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="23224-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="23224-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="23224-139">Dopo aver aggiunto l'AppID, passare a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets.</span><span class="sxs-lookup"><span data-stu-id="23224-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="23224-140">Selezionare l'opzione Usa il server dei nomi e impostare l'area fissa su US o l'area del servizio Photon.</span><span class="sxs-lookup"><span data-stu-id="23224-140">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="23224-142">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="23224-142">Congratulations</span></span>

<span data-ttu-id="23224-143">È stato creato un account Photon, configurato un server Photon locale e il PUN è stato importato in Unity.</span><span class="sxs-lookup"><span data-stu-id="23224-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="23224-144">Il passaggio successivo consiste nell'impostare il progetto e quindi consentire le connessioni con altri utenti in modo che più utenti possano visualizzare il lavoro.</span><span class="sxs-lookup"><span data-stu-id="23224-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="23224-145">[Esercitazione successiva: Preparazione di Unity per lo sviluppo](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="23224-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

