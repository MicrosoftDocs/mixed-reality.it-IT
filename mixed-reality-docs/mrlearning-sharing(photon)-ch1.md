---
title: Esercitazioni sulle funzionalità multiutente - 1. Configurazione di Photon Unity Networking
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031334"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="e1de7-105">1. Configurazione di Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="e1de7-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="e1de7-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="e1de7-106">Overview</span></span>

<span data-ttu-id="e1de7-107">In questa esercitazione imparerai a prepararti per la creazione di un'esperienza condivisa tramite l'importazione di Photon Unity Networking (PUN) nel tuo progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="e1de7-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="e1de7-108">Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di Realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="e1de7-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="e1de7-109">Imparerai a creare un account Photon, importare Photon e creare un server locale facoltativo.</span><span class="sxs-lookup"><span data-stu-id="e1de7-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="e1de7-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="e1de7-110">Objectives</span></span>

* <span data-ttu-id="e1de7-111">Imparare a creare un account Photon</span><span class="sxs-lookup"><span data-stu-id="e1de7-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="e1de7-112">Sapere come trovare e importare Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="e1de7-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="e1de7-113">Configurare un server Photon locale</span><span class="sxs-lookup"><span data-stu-id="e1de7-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e1de7-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="e1de7-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="e1de7-115">Se non hai ancora completato le serie di [Esercitazioni introduttive](mrlearning-base.md) ed [Esercitazioni introduttive ad Ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md), è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="e1de7-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="e1de7-116">Un PC Windows 10 configurato in cui siano [installati gli strumenti](install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="e1de7-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="e1de7-117">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="e1de7-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e1de7-118">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="e1de7-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="e1de7-119">Un dispositivo HoloLens 2 [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="e1de7-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="e1de7-120">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="e1de7-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="e1de7-121">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="e1de7-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="e1de7-122">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="e1de7-122">Setting up Photon</span></span>

1. <span data-ttu-id="e1de7-123">Configura un account [Photon](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="e1de7-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="e1de7-124">Passa alla pagina dell'iscrizione a Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="e1de7-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="e1de7-125">Segui le istruzioni visualizzate nella pagina dell'iscrizione per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="e1de7-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="e1de7-128">Crea un ID applicazione facendo clic sul pulsante Create a New App (Crea una nuova app).</span><span class="sxs-lookup"><span data-stu-id="e1de7-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="e1de7-130">Seleziona Photon PUN dal menu a discesa in Photon Type (Tipo Photon).</span><span class="sxs-lookup"><span data-stu-id="e1de7-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="e1de7-131">Assegna quindi un nome al tipo.</span><span class="sxs-lookup"><span data-stu-id="e1de7-131">Then give it a name.</span></span> <span data-ttu-id="e1de7-132">In questo esempio il nome assegnato è HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="e1de7-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="e1de7-133">Al termine, fai clic sul pulsante Create (Crea).</span><span class="sxs-lookup"><span data-stu-id="e1de7-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="e1de7-135">Torna alla pagina delle tue applicazioni. Verrà visualizzata una schermata simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="e1de7-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="e1de7-136">Fai clic sull'ID applicazione e copialo.</span><span class="sxs-lookup"><span data-stu-id="e1de7-136">Click the application ID and copy it.</span></span> <span data-ttu-id="e1de7-137">Incollalo in una posizione a cui puoi accedere facilmente.</span><span class="sxs-lookup"><span data-stu-id="e1de7-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="e1de7-139">Crea un nuovo progetto Unity con il nome HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="e1de7-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="e1de7-140">Per istruzioni su come creare un nuovo progetto Unity, vedi [la sezione "Crea un nuovo progetto Unity" del modulo di base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="e1de7-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="e1de7-141">Dopo aver caricato il progetto, fai clic sulla scheda Assets Store (Archivio asset), come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="e1de7-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="e1de7-142">Nella casella di ricerca evidenziata nell'immagine seguente digita quindi PUN e seleziona l'asset "Photon PUN 2 - FREE" (Photon PUN 2 - GRATUITO) dai risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="e1de7-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="e1de7-144">Scarica e importa questo asset premendo i pulsanti Download (Scarica) e Import (Importa).</span><span class="sxs-lookup"><span data-stu-id="e1de7-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="e1de7-146">Dopo che Photon ha completato il processo di importazione, viene visualizzato Pun Wizard (Configurazione guidata PUN).</span><span class="sxs-lookup"><span data-stu-id="e1de7-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="e1de7-147">Prendi l'ID applicazione, che deve trovarsi negli Appunti, nel passaggio 4, incollalo nella casella AppID e premi il pulsante Setup Project (Configura progetto).</span><span class="sxs-lookup"><span data-stu-id="e1de7-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="e1de7-149">Dopo aver aggiunto AppID, passa a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings (Photon-> PhotonUnityNetworking-> Risorse-> ImpostazioniServerPhoton) in Assets (Asset).</span><span class="sxs-lookup"><span data-stu-id="e1de7-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="e1de7-150">Seleziona l'opzione Use Name Server (Usa server dei nomi) e imposta l'area geografica fissa su US (Stati Uniti) o sull'area geografica del servizio Photon.</span><span class="sxs-lookup"><span data-stu-id="e1de7-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="e1de7-152">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="e1de7-152">Congratulations</span></span>

<span data-ttu-id="e1de7-153">Hai creato un account Photon, configurato un server Photon locale e importato PUN in Unity.</span><span class="sxs-lookup"><span data-stu-id="e1de7-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="e1de7-154">Il passaggio successivo consiste nel configurare il progetto e consentire connessioni con altri utenti, in modo che più utenti possano visualizzare il lavoro che hai svolto.</span><span class="sxs-lookup"><span data-stu-id="e1de7-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="e1de7-155">[Esercitazione successiva: 2. Preparazione di Unity per lo sviluppo](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="e1de7-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
