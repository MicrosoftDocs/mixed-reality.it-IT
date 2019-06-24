---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327928"
---
# <a name="setting-up-photon"></a><span data-ttu-id="9bb39-104">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="9bb39-104">Setting Up Photon</span></span>

<span data-ttu-id="9bb39-105">In questa lezione si apprenderà come prepararsi per la creazione di un'esperienza condivisa tramite l'importazione di Networking Unity Photon (stato) nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="9bb39-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="9bb39-106">Photon è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise.</span><span class="sxs-lookup"><span data-stu-id="9bb39-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="9bb39-107">Si si apprenderà come creare un account Photon, importare Photon e creare un server locale facoltativo</span><span class="sxs-lookup"><span data-stu-id="9bb39-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="9bb39-108">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="9bb39-108">Objectives:</span></span>

* <span data-ttu-id="9bb39-109">Informazioni su come creare account Photon</span><span class="sxs-lookup"><span data-stu-id="9bb39-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="9bb39-110">Informazioni su come individuare e importare Networking Unity Photon</span><span class="sxs-lookup"><span data-stu-id="9bb39-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="9bb39-111">Configurare un server locale Photon</span><span class="sxs-lookup"><span data-stu-id="9bb39-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="9bb39-112">Configurazione di Photon</span><span class="sxs-lookup"><span data-stu-id="9bb39-112">Setting Up Photon</span></span>

1. <span data-ttu-id="9bb39-113">Configurare un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span><span class="sxs-lookup"><span data-stu-id="9bb39-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="9bb39-114">Passare alla pagina di iscrizione Photon facendo clic su [questo collegamento](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="9bb39-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="9bb39-115">Seguire le istruzioni nella pagina di iscrizione per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="9bb39-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="9bb39-117">Dopo che è stata effettuata l'iscrizione, fare clic su SDK.</span><span class="sxs-lookup"><span data-stu-id="9bb39-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="9bb39-118">Una volta in tale pagina, fare clic su "server" e assicurarsi che lo stato, "self-hosted."</span><span class="sxs-lookup"><span data-stu-id="9bb39-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="9bb39-119">Scorrere verso il basso e fare clic su "server", come illustrato nell'immagine secondo seguente.</span><span class="sxs-lookup"><span data-stu-id="9bb39-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="9bb39-122">In tal modo una casella di testo da visualizzare con etichette, "Leggi me."</span><span class="sxs-lookup"><span data-stu-id="9bb39-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="9bb39-123">Proseguo e leggerlo.</span><span class="sxs-lookup"><span data-stu-id="9bb39-123">Go ahead and read it.</span></span> <span data-ttu-id="9bb39-124">Al termine, fare clic sul collegamento accanto a "downloadSDK" per scaricarlo.</span><span class="sxs-lookup"><span data-stu-id="9bb39-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="9bb39-126">Fare doppio clic sulla cartella termine di download.</span><span class="sxs-lookup"><span data-stu-id="9bb39-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="9bb39-127">Una volta Esplora file viene aperto rivelando la cartella del SDK, copiare la cartella del SDK.</span><span class="sxs-lookup"><span data-stu-id="9bb39-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="9bb39-128">Il passaggio successivo, è possibile passare nell'unità c: windows e creare una nuova cartella denominata "server".</span><span class="sxs-lookup"><span data-stu-id="9bb39-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="9bb39-130">A questo punto aprire la cartella e incollare la cartella SDK copiato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="9bb39-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="9bb39-132">Una volta che viene completato, aprire la cartella SDK e passare a "Distribuisci", quindi "bin_Win64", quindi fare doppio clic su "controllo photon".</span><span class="sxs-lookup"><span data-stu-id="9bb39-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="9bb39-134">Nota: Se hai domande sull'indirizzo IP o eventuali altre domande simili, è possibile trovare la maggior parte delle informazioni sulla barra degli strumenti (come illustrato nell'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="9bb39-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="9bb39-136">Ora che il server è configurato e avviato, tornare al sito Web Photon e assicurarsi che è ancora connessi (o accedere nuovamente, se non si.) Fare clic sull'icona del profilo (boxed in alto a destra dell'immagine riportata di seguito) e selezionare "applicazioni".</span><span class="sxs-lookup"><span data-stu-id="9bb39-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="9bb39-138">Creare un ID applicazione facendo clic sul pulsante "Crea una nuova app".</span><span class="sxs-lookup"><span data-stu-id="9bb39-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="9bb39-140">Selezionare "Photon considerato" nel menu a discesa in "tipo photon".</span><span class="sxs-lookup"><span data-stu-id="9bb39-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="9bb39-141">Assegnargli un nome, in questo esempio, è denominato "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="9bb39-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="9bb39-142">Al termine, fare clic sul pulsante "Crea".</span><span class="sxs-lookup"><span data-stu-id="9bb39-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="9bb39-144">Al termine dell'operazione, tornare alla pagina delle applicazioni e verrà visualizzato qualcosa di simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="9bb39-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="9bb39-145">Fare clic sull'ID dell'app e copiarlo.</span><span class="sxs-lookup"><span data-stu-id="9bb39-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="9bb39-146">Incolla è in una posizione che facilmente accessibile.</span><span class="sxs-lookup"><span data-stu-id="9bb39-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="9bb39-148">Creare un nuovo progetto unity e denominarla "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="9bb39-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="9bb39-149">Per istruzioni su come creare un nuovo progetto Unity, consultare [sezione "Creare progetto Unity" del modulo Base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="9bb39-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="9bb39-150">Una volta che il progetto viene caricato, fare clic sulla scheda "asset store", come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="9bb39-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="9bb39-151">Quindi, nella casella di ricerca evidenziata nell'immagine seguente, digitare "Stato" e selezionare l'asset "Photon 2 in poi" gratuiti"dai risultati della ricerca.</span><span class="sxs-lookup"><span data-stu-id="9bb39-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="9bb39-153">Scaricare e importare questo asset facendo clic sul pulsante "Download" e "Import".</span><span class="sxs-lookup"><span data-stu-id="9bb39-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="9bb39-155">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="9bb39-155">Congratulations</span></span>

<span data-ttu-id="9bb39-156">Si hanno correttamente creato un account Photon configurare un server Photon locale e importato in poi in Unity.</span><span class="sxs-lookup"><span data-stu-id="9bb39-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="9bb39-157">Il passaggio successivo è impostare il progetto e quindi consentire le connessioni con altri utenti in modo che più utenti possono visualizzare il proprio lavoro.</span><span class="sxs-lookup"><span data-stu-id="9bb39-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="9bb39-158">[Lezione successiva: Sharing(photon) lezione 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="9bb39-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

