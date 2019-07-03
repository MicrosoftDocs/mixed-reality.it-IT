---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523296"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="fbf05-104">Configurazione di rete di Unity Photon</span><span class="sxs-lookup"><span data-stu-id="fbf05-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="fbf05-105">In questa esercitazione, è informazioni su come prepararsi per la creazione di un'esperienza condivisa tramite l'importazione di Networking Unity Photon (stato) nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="fbf05-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="fbf05-106">Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="fbf05-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="fbf05-107">Si si apprenderà come creare un account Photon, importare Photon e creare un server locale facoltativo</span><span class="sxs-lookup"><span data-stu-id="fbf05-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="fbf05-108">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="fbf05-108">Objectives:</span></span>

* <span data-ttu-id="fbf05-109">Informazioni su come creare un account Photon</span><span class="sxs-lookup"><span data-stu-id="fbf05-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="fbf05-110">Informazioni su come individuare e importare Networking Unity Photon</span><span class="sxs-lookup"><span data-stu-id="fbf05-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="fbf05-111">Configurare un server locale Photon</span><span class="sxs-lookup"><span data-stu-id="fbf05-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="fbf05-112">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="fbf05-112">Setting up Photon</span></span>

1. <span data-ttu-id="fbf05-113">Configurare un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span><span class="sxs-lookup"><span data-stu-id="fbf05-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="fbf05-114">Passare alla pagina di iscrizione Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="fbf05-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="fbf05-115">Seguire le istruzioni nella pagina di iscrizione per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="fbf05-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="fbf05-118">Creare un ID applicazione, fare clic su Crea un pulsante Nuova App.</span><span class="sxs-lookup"><span data-stu-id="fbf05-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="fbf05-120">Selezionare poi Photon nel menu a discesa sotto Photon tipo.</span><span class="sxs-lookup"><span data-stu-id="fbf05-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="fbf05-121">Assegnargli un nome.</span><span class="sxs-lookup"><span data-stu-id="fbf05-121">Then give it a name.</span></span> <span data-ttu-id="fbf05-122">In questo esempio è denominato HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="fbf05-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="fbf05-123">Al termine, fare clic sul pulsante Crea.</span><span class="sxs-lookup"><span data-stu-id="fbf05-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="fbf05-125">Al termine dell'operazione, tornare alla pagina delle applicazioni e verrà visualizzato qualcosa di simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="fbf05-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="fbf05-126">Fare clic sull'ID applicazione e copiarlo.</span><span class="sxs-lookup"><span data-stu-id="fbf05-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="fbf05-127">Incolla è in una posizione che facilmente accessibile.</span><span class="sxs-lookup"><span data-stu-id="fbf05-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="fbf05-129">Creare un nuovo progetto unity e denominarla HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="fbf05-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="fbf05-130">Per istruzioni su come creare un nuovo progetto Unity, consultare [sezione "Creare progetto Unity" del modulo Base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="fbf05-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="fbf05-131">Una volta che il progetto viene caricato, fare clic sulla scheda Asset Store, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="fbf05-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="fbf05-132">Quindi, nella casella di ricerca evidenziata nell'immagine seguente, digitare in poi e selezionare il 2 in poi Photon - da FRE"asset dai risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="fbf05-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="fbf05-134">Scaricare e importare questo asset facendo clic sul pulsante Download e importazione.</span><span class="sxs-lookup"><span data-stu-id="fbf05-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="fbf05-136">Una volta Photon completato il processo di importazione, verrà visualizzata la procedura guidata in poi.</span><span class="sxs-lookup"><span data-stu-id="fbf05-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="fbf05-137">Richiedere l'ID dell'applicazione (che deve essere copiata negli Appunti) nel passaggio 4, incollarlo nella casella di AppID e premere il pulsante di progetto di installazione.</span><span class="sxs-lookup"><span data-stu-id="fbf05-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="fbf05-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="fbf05-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="fbf05-139">Dopo aver aggiunto l'AppID, passare a Photon -> PhotonUnityNetworking -> risorse -> PhotonServerSettings negli asset.</span><span class="sxs-lookup"><span data-stu-id="fbf05-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="fbf05-140">Selezionare l'opzione utilizza un nome Server e impostare il fisso area Stati Uniti o l'area di servizio yourPphoton.</span><span class="sxs-lookup"><span data-stu-id="fbf05-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="fbf05-142">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="fbf05-142">Congratulations</span></span>

<span data-ttu-id="fbf05-143">Si hanno correttamente creato un account Photon configurare un server Photon locale e importato in poi in Unity.</span><span class="sxs-lookup"><span data-stu-id="fbf05-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="fbf05-144">Il passaggio successivo è impostare il progetto e quindi consentire le connessioni con altri utenti in modo che più utenti possono visualizzare il proprio lavoro.</span><span class="sxs-lookup"><span data-stu-id="fbf05-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="fbf05-145">[Esercitazione successiva: Operazioni preliminari per lo sviluppo di Unity](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="fbf05-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

