---
title: MR e Azure 302B-visione personalizzata
description: Completare questo corso per apprendere come eseguire il training di un modello di apprendimento automatico e quindi usare il modello sottoposto a training per riconoscere oggetti simili in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, visione personalizzata, hololens, immersiva, VR
ms.openlocfilehash: 2c8bd31958cca3b0e27fb0e97839d75fcdebe8c5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438514"
---
>[!NOTE]
><span data-ttu-id="25a3c-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="25a3c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="25a3c-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="25a3c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="25a3c-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="25a3c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="25a3c-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="25a3c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="25a3c-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="25a3c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="25a3c-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="25a3c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="25a3c-110">MR e Azure 302B: visione personalizzata</span><span class="sxs-lookup"><span data-stu-id="25a3c-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="25a3c-111">In questo corso si apprenderà come riconoscere contenuto visivo personalizzato in un'immagine fornita, usando le funzionalità di Visione personalizzata di Azure in un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="25a3c-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="25a3c-112">Questo servizio consentirà di eseguire il training di un modello di apprendimento automatico usando immagini oggetto.</span><span class="sxs-lookup"><span data-stu-id="25a3c-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="25a3c-113">Si userà quindi il modello sottoposto a training per riconoscere oggetti simili, come fornito dall'acquisizione della fotocamera di Microsoft HoloLens o da una fotocamera connessa al PC per auricolari immersivi (VR).</span><span class="sxs-lookup"><span data-stu-id="25a3c-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![risultato del corso](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="25a3c-115">Azure Visione personalizzata è un servizio cognitivo Microsoft che consente agli sviluppatori di creare classificatori di immagini personalizzate.</span><span class="sxs-lookup"><span data-stu-id="25a3c-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="25a3c-116">Questi classificatori possono quindi essere utilizzati con nuove immagini per riconoscere, o classificare, gli oggetti all'interno di tale nuova immagine.</span><span class="sxs-lookup"><span data-stu-id="25a3c-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="25a3c-117">Il servizio fornisce un portale online semplice e facile da usare per semplificare il processo.</span><span class="sxs-lookup"><span data-stu-id="25a3c-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="25a3c-118">Per ulteriori informazioni, visitare la [pagina servizio visione artificiale personalizzato di Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="25a3c-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="25a3c-119">Al termine di questo corso, sarà disponibile un'applicazione di realtà mista che sarà in grado di funzionare in due modalità:</span><span class="sxs-lookup"><span data-stu-id="25a3c-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="25a3c-120">**Modalità di analisi**: configurazione manuale del servizio visione artificiale personalizzato tramite il caricamento di immagini, creazione di tag e training del servizio per riconoscere oggetti diversi (in questo caso mouse e tastiera).</span><span class="sxs-lookup"><span data-stu-id="25a3c-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="25a3c-121">Si creerà quindi un'app HoloLens che acquisisce immagini con la fotocamera e si tenterà di riconoscere tali oggetti nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="25a3c-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="25a3c-122">**Modalità di training**: viene implementato il codice che Abilita una "modalità di training" nell'app.</span><span class="sxs-lookup"><span data-stu-id="25a3c-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="25a3c-123">La modalità di training consentirà di acquisire immagini usando la fotocamera HoloLens, caricare le immagini acquisite nel servizio ed eseguire il training del modello di visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="25a3c-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="25a3c-124">Questo corso spiegherà come ottenere i risultati dal Servizio visione artificiale personalizzato in un'applicazione di esempio basata su Unity.</span><span class="sxs-lookup"><span data-stu-id="25a3c-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="25a3c-125">Sarà necessario applicare questi concetti a un'applicazione personalizzata che è possibile creare.</span><span class="sxs-lookup"><span data-stu-id="25a3c-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="25a3c-126">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="25a3c-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="25a3c-127">Corso</span><span class="sxs-lookup"><span data-stu-id="25a3c-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="25a3c-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="25a3c-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="25a3c-129"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="25a3c-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="25a3c-130">MR e Azure 302B: visione personalizzata</span><span class="sxs-lookup"><span data-stu-id="25a3c-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="25a3c-131">✔️</span><span class="sxs-lookup"><span data-stu-id="25a3c-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="25a3c-132">✔️</span><span class="sxs-lookup"><span data-stu-id="25a3c-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="25a3c-133">Sebbene questo corso sia incentrato principalmente su HoloLens, è anche possibile applicare le informazioni apprese in questo corso agli auricolari per la realtà mista (VR) di Windows.</span><span class="sxs-lookup"><span data-stu-id="25a3c-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="25a3c-134">Poiché le cuffie immersive (VR) non hanno fotocamere accessibili, sarà necessaria una fotocamera esterna connessa al PC.</span><span class="sxs-lookup"><span data-stu-id="25a3c-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="25a3c-135">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare gli auricolari immersivi (VR).</span><span class="sxs-lookup"><span data-stu-id="25a3c-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="25a3c-136">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="25a3c-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="25a3c-137">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="25a3c-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="25a3c-138">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="25a3c-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="25a3c-139">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="25a3c-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="25a3c-140">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="25a3c-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="25a3c-141">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="25a3c-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="25a3c-142">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="25a3c-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="25a3c-143">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="25a3c-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="25a3c-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="25a3c-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="25a3c-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="25a3c-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="25a3c-146">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="25a3c-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="25a3c-147">Una fotocamera connessa al PC (per lo sviluppo di auricolari immersivi)</span><span class="sxs-lookup"><span data-stu-id="25a3c-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="25a3c-148">Accesso a Internet per il programma di installazione di Azure e il recupero Visione personalizzata API</span><span class="sxs-lookup"><span data-stu-id="25a3c-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="25a3c-149">Una serie di almeno cinque immagini (5) (dieci (10) consigliate) per ogni oggetto che si desidera venga riconosciuto dal Servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="25a3c-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="25a3c-150">Se si desidera, è possibile utilizzare [le immagini già disponibili in questo corso (un mouse del computer e una tastiera) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="25a3c-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="25a3c-151">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="25a3c-151">Before you start</span></span>

1.  <span data-ttu-id="25a3c-152">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="25a3c-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="25a3c-153">Configurare e testare il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="25a3c-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="25a3c-154">Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="25a3c-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="25a3c-155">Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="25a3c-156">Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="25a3c-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="25a3c-157">Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="25a3c-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="25a3c-158">Capitolo 1-portale di Servizio visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="25a3c-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="25a3c-159">Per usare il *servizio visione artificiale personalizzato* in Azure, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="25a3c-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="25a3c-160">Per prima cosa, [passare alla pagina principale *servizio visione artificiale personalizzato* ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="25a3c-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="25a3c-161">Fare clic sul pulsante **Get Started** (attività iniziali).</span><span class="sxs-lookup"><span data-stu-id="25a3c-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="25a3c-162">Accedere al portale di *servizio visione artificiale personalizzato* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="25a3c-163">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="25a3c-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="25a3c-164">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="25a3c-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="25a3c-165">Una volta effettuato l'accesso per la prima volta, verrà visualizzato il pannello *condizioni del servizio* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="25a3c-166">Fare clic sulla casella di controllo per accettare le condizioni.</span><span class="sxs-lookup"><span data-stu-id="25a3c-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="25a3c-167">Quindi **, fare clic su Accetto.**</span><span class="sxs-lookup"><span data-stu-id="25a3c-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="25a3c-168">Accettando le condizioni, si passerà alla sezione *Projects (progetti* ) del portale.</span><span class="sxs-lookup"><span data-stu-id="25a3c-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="25a3c-169">Fare clic su **nuovo progetto**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="25a3c-170">Verrà visualizzata una scheda sul lato destro, che richiederà di specificare alcuni campi per il progetto.</span><span class="sxs-lookup"><span data-stu-id="25a3c-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="25a3c-171">Inserire un *nome* per il progetto.</span><span class="sxs-lookup"><span data-stu-id="25a3c-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="25a3c-172">Inserire una *Descrizione* per il progetto (*facoltativo*).</span><span class="sxs-lookup"><span data-stu-id="25a3c-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="25a3c-173">Scegliere un *gruppo di risorse* o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="25a3c-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="25a3c-174">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="25a3c-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="25a3c-175">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="25a3c-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="25a3c-176">Impostare i *tipi di progetto* sulla **classificazione**</span><span class="sxs-lookup"><span data-stu-id="25a3c-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="25a3c-177">Impostare i *domini* come **generali**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="25a3c-178">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="25a3c-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="25a3c-179">Al termine, fare clic su **Crea progetto**. si verrà reindirizzati alla pagina servizio visione artificiale personalizzato, progetto.</span><span class="sxs-lookup"><span data-stu-id="25a3c-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="25a3c-180">Capitolo 2-training del progetto di Visione personalizzata</span><span class="sxs-lookup"><span data-stu-id="25a3c-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="25a3c-181">Una volta nel portale di Visione personalizzata, l'obiettivo principale è quello di eseguire il training del progetto per riconoscere oggetti specifici nelle immagini.</span><span class="sxs-lookup"><span data-stu-id="25a3c-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="25a3c-182">Sono necessarie almeno cinque immagini (5), sebbene sia preferibile dieci (10), per ogni oggetto che si desidera che l'applicazione riconosca.</span><span class="sxs-lookup"><span data-stu-id="25a3c-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="25a3c-183">[È possibile utilizzare le immagini fornite con questo corso (un mouse del computer e una tastiera)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="25a3c-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="25a3c-184">Per eseguire il training del progetto Servizio visione artificiale personalizzato:</span><span class="sxs-lookup"><span data-stu-id="25a3c-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="25a3c-185">Fare clic sul pulsante **+** accanto ai **tag.**</span><span class="sxs-lookup"><span data-stu-id="25a3c-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="25a3c-186">Aggiungere il **nome** dell'oggetto che si desidera riconoscere.</span><span class="sxs-lookup"><span data-stu-id="25a3c-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="25a3c-187">Fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="25a3c-188">Si noterà che il **tag** è stato aggiunto. potrebbe essere necessario ricaricare la pagina affinché venga visualizzata.</span><span class="sxs-lookup"><span data-stu-id="25a3c-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="25a3c-189">Fare clic sulla casella di controllo accanto al nuovo tag, se non è già selezionato.</span><span class="sxs-lookup"><span data-stu-id="25a3c-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="25a3c-190">Fare clic su **Aggiungi immagini** al centro della pagina.</span><span class="sxs-lookup"><span data-stu-id="25a3c-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="25a3c-191">Fare clic su **Sfoglia file locali**e cercare, quindi selezionare le immagini che si desidera caricare, almeno cinque (5).</span><span class="sxs-lookup"><span data-stu-id="25a3c-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="25a3c-192">Tenere presente che tutte le immagini devono contenere l'oggetto di cui si esegue il training.</span><span class="sxs-lookup"><span data-stu-id="25a3c-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="25a3c-193">È possibile selezionare più immagini alla volta per caricare.</span><span class="sxs-lookup"><span data-stu-id="25a3c-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="25a3c-194">Una volta visualizzate le immagini nella scheda, selezionare il tag appropriato nella casella **tag personali** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="25a3c-195">Fare clic su **Carica file**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-195">Click on **Upload files**.</span></span> <span data-ttu-id="25a3c-196">Il caricamento dei file inizierà.</span><span class="sxs-lookup"><span data-stu-id="25a3c-196">The files will begin uploading.</span></span> <span data-ttu-id="25a3c-197">Una volta confermata la richiesta di caricamento, fare clic su **fine**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="25a3c-198">Ripetere lo stesso processo per creare un nuovo **tag** denominato **Keyboard** e caricare le foto appropriate.</span><span class="sxs-lookup"><span data-stu-id="25a3c-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="25a3c-199">Assicurarsi di **deselezionare** il *mouse* dopo aver creato i nuovi tag, in modo da visualizzare la finestra *Aggiungi immagini* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="25a3c-200">Una volta impostati entrambi i tag, fare clic su **Training**per avviare la creazione della prima iterazione di training.</span><span class="sxs-lookup"><span data-stu-id="25a3c-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="25a3c-201">Una volta compilato, sarà possibile visualizzare due pulsanti denominati **Make default** and **PREDICTION URL**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="25a3c-202">Fare clic su **Imposta come predefinito** per primo, quindi fare clic su **URL stima**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="25a3c-203">L'URL dell'endpoint fornito da questo oggetto è impostato su qualsiasi *iterazione* contrassegnata come predefinita.</span><span class="sxs-lookup"><span data-stu-id="25a3c-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="25a3c-204">Di conseguenza, se in un secondo momento si crea una nuova *iterazione* e la si aggiorna come predefinita, non sarà necessario modificare il codice.</span><span class="sxs-lookup"><span data-stu-id="25a3c-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="25a3c-205">Una volta fatto clic su *URL stima*, aprire *blocco note*e copiare e incollare l' **URL** e la chiave di **stima**, in modo da poterlo recuperare quando necessario in un secondo momento nel codice.</span><span class="sxs-lookup"><span data-stu-id="25a3c-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="25a3c-206">Fare clic sull' **ingranaggio** nella parte superiore destra della schermata.</span><span class="sxs-lookup"><span data-stu-id="25a3c-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="25a3c-207">Copiare la **chiave di training** e incollarla in un *blocco note*, per un uso successivo.</span><span class="sxs-lookup"><span data-stu-id="25a3c-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="25a3c-208">Copiare anche l' **ID del progetto**e incollarlo nel file del *blocco note* , per usarlo in seguito.</span><span class="sxs-lookup"><span data-stu-id="25a3c-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="25a3c-209">Capitolo 3: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="25a3c-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="25a3c-210">Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="25a3c-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="25a3c-211">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="25a3c-212">A questo punto sarà necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="25a3c-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="25a3c-213">Inserire **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="25a3c-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="25a3c-214">Verificare che il modello di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="25a3c-215">Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="25a3c-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="25a3c-216">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="25a3c-217">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="25a3c-218">Passare a  \**modifica* *Preferenze* > \* e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="25a3c-219">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="25a3c-220">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="25a3c-221">Passare quindi a **File > impostazioni di compilazione** e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="25a3c-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="25a3c-222">Sempre in **File > impostazioni di compilazione** e verificare che:</span><span class="sxs-lookup"><span data-stu-id="25a3c-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="25a3c-223">Il **dispositivo di destinazione** è impostato su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="25a3c-223">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="25a3c-224">Per gli auricolari immersivi, impostare **dispositivo di destinazione** su *qualsiasi dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="25a3c-225">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="25a3c-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="25a3c-226">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="25a3c-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="25a3c-227">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="25a3c-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="25a3c-228">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="25a3c-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="25a3c-229">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="25a3c-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="25a3c-230">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="25a3c-231">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="25a3c-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="25a3c-232">Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.</span><span class="sxs-lookup"><span data-stu-id="25a3c-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="25a3c-233">Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file:* testo digitare **CustomVisionScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="25a3c-234">Tenere presente che è necessario salvare le scene Unity all'interno della cartella *assets* , in quanto devono essere associate al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="25a3c-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="25a3c-235">La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="25a3c-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="25a3c-236">Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="25a3c-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="25a3c-237">Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="25a3c-238">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="25a3c-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="25a3c-239">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="25a3c-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="25a3c-240">La **versione di runtime di scripting** deve essere **sperimentale (equivalente a .NET 4,6)** , che attiverà la necessità di riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="25a3c-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="25a3c-241">Il **back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="25a3c-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="25a3c-242">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="25a3c-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="25a3c-243">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="25a3c-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="25a3c-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="25a3c-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="25a3c-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="25a3c-245">**Webcam**</span></span>

        3. <span data-ttu-id="25a3c-246">**Microfono**</span><span class="sxs-lookup"><span data-stu-id="25a3c-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="25a3c-247">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="25a3c-248">Nelle *impostazioni di compilazione* i *progetti di unity C\#* non sono più in grigio; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="25a3c-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="25a3c-249">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="25a3c-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="25a3c-250">Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="25a3c-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="25a3c-251">Capitolo 4-importazione della DLL di Newtonsoft in Unity</span><span class="sxs-lookup"><span data-stu-id="25a3c-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25a3c-252">Se si vuole ignorare il componente di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile scaricare questo [Azure-Mr-302B. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 6 ](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="25a3c-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="25a3c-253">Questo corso richiede l'uso della libreria **Newtonsoft** , che è possibile aggiungere come dll agli asset.</span><span class="sxs-lookup"><span data-stu-id="25a3c-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="25a3c-254">Il pacchetto contenente [questa libreria può essere scaricato da questo collegamento](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="25a3c-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="25a3c-255">Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornito con questo corso.</span><span class="sxs-lookup"><span data-stu-id="25a3c-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="25a3c-256">Aggiungere il *file unitypackage Tools* a Unity usando l'opzione di menu **asset* > *Importa* *pacchetto* > *pacchetto* *personalizzato** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="25a3c-257">Nella casella **Importa pacchetto Unity** visualizzata verificare che siano selezionati tutti gli elementi in (e inclusi) **plug** -in.</span><span class="sxs-lookup"><span data-stu-id="25a3c-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="25a3c-258">Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="25a3c-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="25a3c-259">Passare alla cartella **Newtonsoft** in **plug** -in nella visualizzazione del progetto e selezionare il plug-in *Newtonsoft. JSON*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="25a3c-260">Con il *plug-in Newtonsoft. JSON* selezionato, verificare che **qualsiasi piattaforma** sia **deselezionata**, quindi verificare che **WSAPlayer** sia **deselezionata**, quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="25a3c-261">Questa operazione è sufficiente per verificare che i file siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="25a3c-262">Contrassegnando questi plug-in, questi vengono configurati per essere usati solo nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="25a3c-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="25a3c-263">Nella cartella WSA è presente un set diverso che verrà usato dopo l'esportazione del progetto da Unity.</span><span class="sxs-lookup"><span data-stu-id="25a3c-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="25a3c-264">Successivamente, è necessario aprire la cartella **WSA** , all'interno della cartella **Newtonsoft** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="25a3c-265">Viene visualizzata una copia dello stesso file appena configurato.</span><span class="sxs-lookup"><span data-stu-id="25a3c-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="25a3c-266">Selezionare il file e quindi nel controllo verificare che</span><span class="sxs-lookup"><span data-stu-id="25a3c-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="25a3c-267">**Qualsiasi piattaforma** è **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="25a3c-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="25a3c-268">**Verifica** **solo** **WSAPlayer**</span><span class="sxs-lookup"><span data-stu-id="25a3c-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="25a3c-269">Il **processo** non è **selezionato**</span><span class="sxs-lookup"><span data-stu-id="25a3c-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="25a3c-270">Capitolo 5-configurazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="25a3c-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="25a3c-271">Nel pannello gerarchia selezionare la *fotocamera principale*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="25a3c-272">Una volta selezionato, sarà possibile visualizzare tutti i componenti della *fotocamera principale* nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="25a3c-273">L'oggetto *fotocamera* deve essere denominato **Main camera** (nota l'ortografia).</span><span class="sxs-lookup"><span data-stu-id="25a3c-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="25a3c-274">Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (si noti l'ortografia).</span><span class="sxs-lookup"><span data-stu-id="25a3c-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="25a3c-275">Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="25a3c-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="25a3c-276">Impostare **Cancella flag** su **colore a tinta unita** (ignorarlo per l'auricolare immersivo).</span><span class="sxs-lookup"><span data-stu-id="25a3c-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="25a3c-277">Imposta il colore di **sfondo** del componente della fotocamera su **nero, alfa 0 (codice esadecimale: #00000000)** (ignorarlo per l'auricolare immersivo).</span><span class="sxs-lookup"><span data-stu-id="25a3c-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="25a3c-278">Capitolo 6: creare la classe CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="25a3c-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="25a3c-279">A questo punto si è pronti per scrivere il codice.</span><span class="sxs-lookup"><span data-stu-id="25a3c-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="25a3c-280">Si inizierà con la classe *CustomVisionAnalyser* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="25a3c-281">Le chiamate al **servizio visione artificiale personalizzato** effettuate nel codice riportato di seguito vengono effettuate usando l' **API REST di visione personalizzata**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="25a3c-282">Con l'uso di questa API, si vedrà come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile).</span><span class="sxs-lookup"><span data-stu-id="25a3c-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="25a3c-283">Tenere presente che Microsoft offre un **servizio visione artificiale personalizzato SDK** che può essere usato anche per effettuare chiamate al servizio.</span><span class="sxs-lookup"><span data-stu-id="25a3c-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="25a3c-284">Per altre informazioni, vedere l'articolo [servizio visione artificiale personalizzato SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) .</span><span class="sxs-lookup"><span data-stu-id="25a3c-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="25a3c-285">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="25a3c-285">This class is responsible for:</span></span>

-   <span data-ttu-id="25a3c-286">Caricamento dell'immagine più recente acquisita come matrice di byte.</span><span class="sxs-lookup"><span data-stu-id="25a3c-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="25a3c-287">Invio della matrice di byte all'istanza di Azure *servizio visione artificiale personalizzato* per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="25a3c-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="25a3c-288">Ricezione della risposta come stringa JSON.</span><span class="sxs-lookup"><span data-stu-id="25a3c-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="25a3c-289">Deserializzare la risposta e passare la *stima* risultante alla classe *SceneOrganiser* , che si occuperà della modalità di visualizzazione della risposta.</span><span class="sxs-lookup"><span data-stu-id="25a3c-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="25a3c-290">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="25a3c-290">To create this class:</span></span>

1.  <span data-ttu-id="25a3c-291">Fare clic con il pulsante destro del mouse nella *cartella Asset* che si trova nel *pannello progetto*, quindi fare clic su **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="25a3c-292">Chiamare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="25a3c-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="25a3c-293">Fare doppio clic sulla cartella appena creata per aprirla.</span><span class="sxs-lookup"><span data-stu-id="25a3c-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="25a3c-294">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi fare clic su **crea** > **C\# script**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="25a3c-295">Denominare lo script *CustomVisionAnalyser*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="25a3c-296">Fare doppio clic sul nuovo script *CustomVisionAnalyser* per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="25a3c-297">Aggiornare gli spazi dei nomi all'inizio del file in modo che corrispondano a quanto segue:</span><span class="sxs-lookup"><span data-stu-id="25a3c-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="25a3c-298">Nella classe *CustomVisionAnalyser* aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="25a3c-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="25a3c-299">Assicurarsi di inserire la **chiave di stima** nella variabile **PredictionKey** e l'endpoint di **stima** nella variabile **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="25a3c-300">Questi sono stati copiati nel *blocco note* in precedenza nel corso.</span><span class="sxs-lookup"><span data-stu-id="25a3c-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="25a3c-301">Per inizializzare la variabile di istanza, è necessario aggiungere il codice per il punto di riattivazione **()** :</span><span class="sxs-lookup"><span data-stu-id="25a3c-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="25a3c-302">Eliminare i metodi **Start ()** e **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="25a3c-303">Aggiungere quindi la coroutine (con il metodo statico **GetImageAsByteArray ()** sottostante), che otterrà i risultati dell'analisi dell'immagine acquisita dalla classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="25a3c-304">Nella coroutine di **AnalyseImageCapture** è presente una chiamata alla classe *SceneOrganiser* che è ancora necessario creare.</span><span class="sxs-lookup"><span data-stu-id="25a3c-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="25a3c-305">Lasciare quindi **le righe impostate come commento per il momento**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="25a3c-306">Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="25a3c-307">Capitolo 7: creare la classe CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="25a3c-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="25a3c-308">La classe che verrà creata ora è la classe *CustomVisionObjects* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="25a3c-309">Questo script contiene una serie di oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate all' *servizio visione artificiale personalizzato*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="25a3c-310">È importante prendere nota dell'endpoint fornito dal Servizio visione artificiale personalizzato, perché la struttura JSON seguente è stata configurata per funzionare con [*visione personalizzata Prediction v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="25a3c-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="25a3c-311">Se si dispone di una versione diversa, potrebbe essere necessario aggiornare la struttura seguente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="25a3c-312">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="25a3c-312">To create this class:</span></span>

1.  <span data-ttu-id="25a3c-313">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi fare clic su **crea** > **C\# script**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="25a3c-314">Chiamare lo script *CustomVisionObjects*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="25a3c-315">Fare doppio clic sul nuovo script **CustomVisionObjects** per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="25a3c-316">Aggiungere i seguenti spazi dei nomi all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="25a3c-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="25a3c-317">Eliminare i metodi **Start ()** e **Update ()** all'interno della classe *CustomVisionObjects* . Questa classe dovrebbe ora essere vuota.</span><span class="sxs-lookup"><span data-stu-id="25a3c-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="25a3c-318">Aggiungere le classi seguenti al di **fuori** della classe *CustomVisionObjects* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="25a3c-319">Questi oggetti vengono usati dalla libreria *Newtonsoft* per serializzare e deserializzare i dati di risposta:</span><span class="sxs-lookup"><span data-stu-id="25a3c-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="25a3c-320">Capitolo 8: creare la classe VoiceRecognizer</span><span class="sxs-lookup"><span data-stu-id="25a3c-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="25a3c-321">Questa classe riconoscerà l'input vocale dall'utente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="25a3c-322">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="25a3c-322">To create this class:</span></span>

1.  <span data-ttu-id="25a3c-323">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi fare clic su **crea** > **C\# script**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="25a3c-324">Chiamare lo script *VoiceRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="25a3c-325">Fare doppio clic sul nuovo script **VoiceRecognizer** per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="25a3c-326">Aggiungere gli spazi dei nomi seguenti sopra la classe *VoiceRecognizer* :</span><span class="sxs-lookup"><span data-stu-id="25a3c-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="25a3c-327">Aggiungere quindi le variabili seguenti all'interno della classe *VoiceRecognizer* , sopra il metodo *Start ()* :</span><span class="sxs-lookup"><span data-stu-id="25a3c-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="25a3c-328">Aggiungere i metodi **svegli ()** e **Start ()** , il secondo dei quali configurerà le *parole chiave* utente da riconoscere quando si associa un tag a un'immagine:</span><span class="sxs-lookup"><span data-stu-id="25a3c-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="25a3c-329">Eliminare il metodo **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="25a3c-330">Aggiungere il seguente gestore, che viene chiamato ogni volta che viene riconosciuto l'input vocale:</span><span class="sxs-lookup"><span data-stu-id="25a3c-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="25a3c-331">Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="25a3c-332">Non è necessario preoccuparsi del codice che potrebbe sembrare avere un errore, in quanto verranno presto fornite ulteriori classi, per risolvere il problema.</span><span class="sxs-lookup"><span data-stu-id="25a3c-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="25a3c-333">Capitolo 9: creare la classe CustomVisionTrainer</span><span class="sxs-lookup"><span data-stu-id="25a3c-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="25a3c-334">Questa classe condurrà una serie di chiamate web per il training del *servizio visione artificiale personalizzato*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="25a3c-335">Ogni chiamata verrà illustrata in dettaglio immediatamente sopra il codice.</span><span class="sxs-lookup"><span data-stu-id="25a3c-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="25a3c-336">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="25a3c-336">To create this class:</span></span>

1.  <span data-ttu-id="25a3c-337">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi fare clic su **crea** > **C\# script**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="25a3c-338">Chiamare lo script *CustomVisionTrainer*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="25a3c-339">Fare doppio clic sul nuovo script *CustomVisionTrainer* per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="25a3c-340">Aggiungere gli spazi dei nomi seguenti sopra la classe *CustomVisionTrainer* :</span><span class="sxs-lookup"><span data-stu-id="25a3c-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="25a3c-341">Aggiungere quindi le variabili seguenti all'interno della classe *CustomVisionTrainer* , sopra il metodo **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="25a3c-342">L'URL di training usato in questo articolo è disponibile all'interno della documentazione di *visione personalizzata training 1,2* e presenta una struttura di: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="25a3c-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="25a3c-343">Per ulteriori informazioni, visitare l' [*API di riferimento visione personalizzata Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="25a3c-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="25a3c-344">È importante prendere nota dell'endpoint che la Servizio visione artificiale personalizzato fornisce per la modalità di training, perché la struttura JSON usata (all'interno della classe **CustomVisionObjects** ) è stata configurata per funzionare con [*visione personalizzata Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="25a3c-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="25a3c-345">Se si dispone di una versione diversa, potrebbe essere necessario aggiornare la struttura *degli oggetti* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="25a3c-346">Assicurarsi di aggiungere il valore della **chiave del servizio** (chiave di training) e il valore dell' **ID progetto** , annotato in precedenza; Questi sono i valori [raccolti dal portale in precedenza nel corso (capitolo 2, passaggio 10 e versioni successive)](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="25a3c-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-project).</span></span>

5.  <span data-ttu-id="25a3c-347">Aggiungere i seguenti metodi **Start ()** e **sveglie ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="25a3c-348">Questi metodi vengono chiamati all'inizializzazione e contengono la chiamata per configurare l'interfaccia utente:</span><span class="sxs-lookup"><span data-stu-id="25a3c-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="25a3c-349">Eliminare il metodo **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-349">Delete the **Update()** method.</span></span> <span data-ttu-id="25a3c-350">Questa classe non sarà necessaria.</span><span class="sxs-lookup"><span data-stu-id="25a3c-350">This class will not need it.</span></span>

7.  <span data-ttu-id="25a3c-351">Aggiungere il metodo **RequestTagSelection ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="25a3c-352">Questo metodo è il primo a essere chiamato quando un'immagine viene acquisita e archiviata nel dispositivo ed è ora pronta per essere inviata alla *servizio visione artificiale personalizzato*per eseguirne il training.</span><span class="sxs-lookup"><span data-stu-id="25a3c-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="25a3c-353">Questo metodo Visualizza, nell'interfaccia utente di training, un set di parole chiave che l'utente può usare per contrassegnare l'immagine che è stata acquisita.</span><span class="sxs-lookup"><span data-stu-id="25a3c-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="25a3c-354">Avvisa inoltre la classe *VoiceRecognizer* per iniziare l'ascolto dell'input vocale da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="25a3c-355">Aggiungere il metodo **VerifyTag ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="25a3c-356">Questo metodo riceverà l'input vocale riconosciuto dalla classe **VoiceRecognizer** e ne verificherà la validità, quindi avvierà il processo di training.</span><span class="sxs-lookup"><span data-stu-id="25a3c-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="25a3c-357">Aggiungere il metodo **SubmitImageForTraining ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="25a3c-358">Questo metodo inizierà il processo di training Servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="25a3c-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="25a3c-359">Il primo passaggio consiste nel recuperare l' **ID del tag** dal servizio associato all'input vocale convalidato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="25a3c-360">L' **ID Tag** verrà quindi caricato insieme all'immagine.</span><span class="sxs-lookup"><span data-stu-id="25a3c-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="25a3c-361">Aggiungere il metodo **TrainCustomVisionProject ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="25a3c-362">Una volta che l'immagine è stata inviata e contrassegnata, questo metodo verrà chiamato.</span><span class="sxs-lookup"><span data-stu-id="25a3c-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="25a3c-363">Verrà creata una nuova iterazione che verrà sottoposta a training con tutte le immagini precedenti inviate al servizio più l'immagine appena caricata.</span><span class="sxs-lookup"><span data-stu-id="25a3c-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="25a3c-364">Una volta completato il training, questo metodo chiamerà un metodo per impostare l' **iterazione** appena creata come **predefinita**, in modo che l'endpoint usato per l'analisi sia l'iterazione con training più recente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="25a3c-365">Aggiungere il metodo **SetDefaultIteration ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="25a3c-366">Questo metodo imposterà l'iterazione precedentemente creata e sottoposta a training come *predefinita*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="25a3c-367">Al termine, questo metodo dovrà eliminare l'iterazione precedente esistente nel servizio.</span><span class="sxs-lookup"><span data-stu-id="25a3c-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="25a3c-368">Al momento della stesura di questo corso, è previsto un limite di un massimo di dieci (10) iterazioni che possono esistere nello stesso momento nel servizio.</span><span class="sxs-lookup"><span data-stu-id="25a3c-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="25a3c-369">Aggiungere il metodo **DeletePreviousIteration ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="25a3c-370">Questo metodo troverà ed eliminerà l'iterazione non predefinita precedente:</span><span class="sxs-lookup"><span data-stu-id="25a3c-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="25a3c-371">L'ultimo metodo da aggiungere in questa classe è il metodo **GetImageAsByteArray ()** usato nelle chiamate web per convertire l'immagine acquisita in una matrice di byte.</span><span class="sxs-lookup"><span data-stu-id="25a3c-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="25a3c-372">Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="25a3c-373">Capitolo 10: creare la classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="25a3c-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="25a3c-374">Questa classe:</span><span class="sxs-lookup"><span data-stu-id="25a3c-374">This class will:</span></span>

-   <span data-ttu-id="25a3c-375">Creare un oggetto **cursore** per la connessione alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="25a3c-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="25a3c-376">Creare un oggetto **Label** che verrà visualizzato quando il servizio riconosce gli oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="25a3c-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="25a3c-377">Configurare la fotocamera principale collegando i componenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="25a3c-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="25a3c-378">In **modalità di analisi**, generare le etichette in fase di esecuzione, nello spazio globale appropriato rispetto alla posizione della fotocamera principale e visualizzare i dati ricevuti dal servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="25a3c-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="25a3c-379">In **modalità di training**, generare l'interfaccia utente che visualizzerà le varie fasi del processo di training.</span><span class="sxs-lookup"><span data-stu-id="25a3c-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="25a3c-380">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="25a3c-380">To create this class:</span></span>

1.  <span data-ttu-id="25a3c-381">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi fare clic su **crea** > **C\# script**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="25a3c-382">Denominare lo script *SceneOrganiser*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="25a3c-383">Fare doppio clic sul nuovo script *SceneOrganiser* per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="25a3c-384">Sarà necessario solo uno spazio dei nomi, rimuovere gli altri dalla classe *SceneOrganiser* :</span><span class="sxs-lookup"><span data-stu-id="25a3c-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="25a3c-385">Aggiungere quindi le variabili seguenti all'interno della classe *SceneOrganiser* , sopra il metodo **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="25a3c-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="25a3c-386">Eliminare i metodi **Start ()** e **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="25a3c-387">Direttamente sotto le variabili aggiungere il metodo **sveglie ()** che inizializza la classe e imposta la scena.</span><span class="sxs-lookup"><span data-stu-id="25a3c-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="25a3c-388">A questo punto aggiungere il metodo **CreateCameraCursor ()** che crea e posiziona il cursore della fotocamera principale e il metodo **CreateLabel ()** , che crea l'oggetto **Label di analisi** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="25a3c-389">Aggiungere il metodo **SetCameraStatus ()** , che gestirà i messaggi destinati alla rete di testo che forniscono lo stato della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="25a3c-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="25a3c-390">Aggiungere i metodi **PlaceAnalysisLabel ()** e **SetTagsToLastLabel ()** , che generano e visualizzano i dati dal servizio visione artificiale personalizzato alla scena.</span><span class="sxs-lookup"><span data-stu-id="25a3c-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="25a3c-391">Infine, aggiungere il metodo **CreateTrainingUI ()** , che genera l'interfaccia utente che visualizza le varie fasi del processo di training quando l'applicazione è in modalità di training.</span><span class="sxs-lookup"><span data-stu-id="25a3c-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="25a3c-392">Questo metodo verrà inoltre sfruttato per creare l'oggetto stato della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="25a3c-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="25a3c-393">Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25a3c-394">Prima di continuare, aprire la classe **CustomVisionAnalyser** e, all'interno del metodo **AnalyseLastImageCaptured ()** , *rimuovere il commento* dalle righe seguenti:</span><span class="sxs-lookup"><span data-stu-id="25a3c-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="25a3c-395">Capitolo 11: creare la classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="25a3c-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="25a3c-396">La classe successiva che si intende creare è la classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="25a3c-397">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="25a3c-397">This class is responsible for:</span></span>

-   <span data-ttu-id="25a3c-398">Acquisizione di un'immagine con la fotocamera HoloLens e relativa archiviazione nella cartella dell' *app* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="25a3c-399">Gestione dei movimenti Tap dall'utente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="25a3c-400">Gestione del valore *enum* che determina se l'applicazione viene eseguita in modalità di *analisi* o di *Training* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="25a3c-401">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="25a3c-401">To create this class:</span></span>

1.  <span data-ttu-id="25a3c-402">Passare alla cartella **Scripts** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="25a3c-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="25a3c-403">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi fare clic su **crea > C\# script**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="25a3c-404">Denominare lo script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="25a3c-405">Fare doppio clic sul nuovo script **ImageCapture** per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="25a3c-406">Sostituire gli spazi dei nomi all'inizio del file con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="25a3c-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="25a3c-407">Aggiungere quindi le variabili seguenti all'interno della classe *ImageCapture* , sopra il metodo **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="25a3c-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="25a3c-408">È ora necessario aggiungere il codice per i metodi **svegli ()** e **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="25a3c-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="25a3c-409">Implementare un gestore che verrà chiamato quando si verifica un movimento tap.</span><span class="sxs-lookup"><span data-stu-id="25a3c-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="25a3c-410">In modalità *analisi* il metodo **TapHandler** funge da opzione per avviare o arrestare il ciclo di acquisizione foto.</span><span class="sxs-lookup"><span data-stu-id="25a3c-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="25a3c-411">In modalità di *Training* , acquisisce un'immagine dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="25a3c-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="25a3c-412">Quando il cursore è verde, significa che la fotocamera è disponibile per l'immagine.</span><span class="sxs-lookup"><span data-stu-id="25a3c-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="25a3c-413">Quando il cursore è rosso, significa che la fotocamera è occupata.</span><span class="sxs-lookup"><span data-stu-id="25a3c-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="25a3c-414">Aggiungere il metodo usato dall'applicazione per avviare il processo di acquisizione dell'immagine e archiviare l'immagine.</span><span class="sxs-lookup"><span data-stu-id="25a3c-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="25a3c-415">Aggiungere i gestori che verranno chiamati quando la foto è stata acquisita e quando è pronta per essere analizzata.</span><span class="sxs-lookup"><span data-stu-id="25a3c-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="25a3c-416">Il risultato viene quindi passato a *CustomVisionAnalyser* o *CustomVisionTrainer* a seconda della modalità in cui è impostato il codice.</span><span class="sxs-lookup"><span data-stu-id="25a3c-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="25a3c-417">Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="25a3c-418">Ora che tutti gli script sono stati completati, tornare nell'editor di Unity, quindi fare clic e trascinare la classe **SceneOrganiser** dalla cartella **Scripts** all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="25a3c-419">Capitolo 12-prima della compilazione</span><span class="sxs-lookup"><span data-stu-id="25a3c-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="25a3c-420">Per eseguire un test completo dell'applicazione, è necessario sideload nel HoloLens.</span><span class="sxs-lookup"><span data-stu-id="25a3c-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="25a3c-421">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="25a3c-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="25a3c-422">Tutte le impostazioni indicate nel [capitolo 2](#chapter-2---training-your-custom-vision-project) sono impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="25a3c-423">Tutti i campi della **fotocamera principale**, il pannello di controllo, sono assegnati correttamente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="25a3c-424">Lo script **SceneOrganiser** è associato all'oggetto **principale della fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="25a3c-425">Assicurarsi di inserire la **chiave di stima** nella variabile **predictionKey** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="25a3c-426">L' **endpoint di stima** è stato inserito nella variabile **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="25a3c-427">La **chiave di training** è stata inserita nella variabile **TrainingKey** della classe *CustomVisionTrainer* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="25a3c-428">L' **ID progetto** è stato inserito nella variabile **projectId** della classe *CustomVisionTrainer* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="25a3c-429">Capitolo 13: creare e sideload l'applicazione</span><span class="sxs-lookup"><span data-stu-id="25a3c-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="25a3c-430">Per avviare il processo di *compilazione* :</span><span class="sxs-lookup"><span data-stu-id="25a3c-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="25a3c-431">Passare a **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="25a3c-432">Seleziona i **progetti di Unity C\#** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="25a3c-433">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-433">Click **Build**.</span></span> <span data-ttu-id="25a3c-434">Unity avvierà una finestra di **Esplora file** , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="25a3c-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="25a3c-435">Creare la cartella adesso e denominarla **app**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="25a3c-436">Quindi, con la cartella **app** selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="25a3c-437">Unity inizierà a compilare il progetto nella cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="25a3c-438">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).</span><span class="sxs-lookup"><span data-stu-id="25a3c-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="25a3c-439">Per eseguire la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="25a3c-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="25a3c-440">È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="25a3c-441">A tale scopo, effettua le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="25a3c-441">To do this:</span></span>

    1.  <span data-ttu-id="25a3c-442">Quando si indossa il HoloLens, aprire le **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="25a3c-443">Passare a **rete & Internet** > **Opzioni avanzate** **Wi-Fi** > </span><span class="sxs-lookup"><span data-stu-id="25a3c-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="25a3c-444">Prendere nota dell'indirizzo **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="25a3c-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="25a3c-445">Quindi, tornare a **Settings (impostazioni**) e quindi **aggiornare & Security** > **per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="25a3c-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="25a3c-446">Impostare la **modalità di sviluppo su**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="25a3c-447">Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="25a3c-448">Nella *configurazione della soluzione* selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="25a3c-449">Nella *piattaforma soluzione*selezionare **x86, computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="25a3c-450">Verrà richiesto di inserire l' **indirizzo IP** di un dispositivo remoto (HoloLens, in questo caso, annotato).</span><span class="sxs-lookup"><span data-stu-id="25a3c-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="25a3c-451">Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="25a3c-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="25a3c-452">L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="25a3c-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="25a3c-453">Per eseguire la distribuzione in un dispositivo headset immersivo, impostare la **piattaforma della soluzione** su *computer locale*e impostare la **configurazione** su *debug*, con *x86* come **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="25a3c-454">Quindi eseguire la distribuzione nel computer locale, usando la voce di menu **Compila** , selezionando *Distribuisci soluzione*.</span><span class="sxs-lookup"><span data-stu-id="25a3c-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="25a3c-455">Per utilizzare l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="25a3c-455">To use the application:</span></span>

<span data-ttu-id="25a3c-456">Per cambiare la funzionalità dell'app tra la modalità di *Training* e la modalità di *stima* è necessario aggiornare la variabile **AppMode** , che si trova nel metodo **sveglie ()** che si trova all'interno della classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="25a3c-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="25a3c-457">o</span><span class="sxs-lookup"><span data-stu-id="25a3c-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="25a3c-458">In modalità di *Training* :</span><span class="sxs-lookup"><span data-stu-id="25a3c-458">In *Training* mode:</span></span>

- <span data-ttu-id="25a3c-459">Esaminare il **mouse** o la **tastiera** e usare il **gesto Tap**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="25a3c-460">Verrà quindi visualizzato un messaggio in cui viene chiesto di specificare un tag.</span><span class="sxs-lookup"><span data-stu-id="25a3c-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="25a3c-461">Pronunciare il **mouse** o la **tastiera**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="25a3c-462">In modalità di *stima* :</span><span class="sxs-lookup"><span data-stu-id="25a3c-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="25a3c-463">Esaminare un oggetto e usare il **gesto Tap**.</span><span class="sxs-lookup"><span data-stu-id="25a3c-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="25a3c-464">Verrà visualizzato il testo che fornisce l'oggetto rilevato, con la probabilità più elevata (normalizzata).</span><span class="sxs-lookup"><span data-stu-id="25a3c-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="25a3c-465">Capitolo 14: valutare e migliorare il modello di Visione personalizzata</span><span class="sxs-lookup"><span data-stu-id="25a3c-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="25a3c-466">Per rendere più accurato il servizio, sarà necessario continuare a eseguire il training del modello utilizzato per la stima.</span><span class="sxs-lookup"><span data-stu-id="25a3c-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="25a3c-467">Questa operazione viene eseguita tramite l'uso della nuova applicazione, con le modalità di *Training* e di *previsione* , con la seconda richiesta di visitare il portale, che è il contenuto di questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="25a3c-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="25a3c-468">Prepararsi a rivisitare il portale più volte, per migliorare continuamente il modello.</span><span class="sxs-lookup"><span data-stu-id="25a3c-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="25a3c-469">Tornare al portale di Visione personalizzata di Azure e, una volta nel progetto, selezionare la scheda *stime* (dal centro superiore della pagina):</span><span class="sxs-lookup"><span data-stu-id="25a3c-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="25a3c-470">Vengono visualizzate tutte le immagini che sono state inviate al servizio mentre l'applicazione era in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="25a3c-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="25a3c-471">Se si passa il mouse sulle immagini, verranno fornite le stime effettuate per l'immagine:</span><span class="sxs-lookup"><span data-stu-id="25a3c-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="25a3c-472">Selezionare una delle immagini per aprirla.</span><span class="sxs-lookup"><span data-stu-id="25a3c-472">Select one of your images to open it.</span></span> <span data-ttu-id="25a3c-473">Una volta aperta, le stime effettuate per l'immagine vengono visualizzate a destra.</span><span class="sxs-lookup"><span data-stu-id="25a3c-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="25a3c-474">Se le stime sono corrette e si desidera aggiungere questa immagine al modello di training del servizio, fare clic sulla casella di input *Tags* e selezionare il tag che si desidera associare.</span><span class="sxs-lookup"><span data-stu-id="25a3c-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="25a3c-475">Al termine, fare clic sul pulsante *Salva e Chiudi* in basso a destra e continuare con l'immagine successiva.</span><span class="sxs-lookup"><span data-stu-id="25a3c-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="25a3c-476">Quando si torna alla griglia delle immagini, si noterà che le immagini a cui sono stati aggiunti i tag (e salvate) verranno rimosse.</span><span class="sxs-lookup"><span data-stu-id="25a3c-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="25a3c-477">Se si rilevano immagini a cui non è associato alcun elemento con tag, è possibile eliminarle facendo clic sul segno di ingrandimento dell'immagine (può eseguire questa operazione per diverse immagini) e quindi facendo clic su *Elimina* nell'angolo superiore destro della pagina della griglia.</span><span class="sxs-lookup"><span data-stu-id="25a3c-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="25a3c-478">Nella finestra popup riportata di seguito è possibile fare clic su *Sì, Elimina* o *No*per confermare l'eliminazione o annullarla, rispettivamente.</span><span class="sxs-lookup"><span data-stu-id="25a3c-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="25a3c-479">Quando si è pronti per continuare, fare clic sul pulsante di *Train* verde in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="25a3c-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="25a3c-480">Il modello di servizio verrà sottoposto a training con tutte le immagini fornite a questo punto (per renderlo più accurato).</span><span class="sxs-lookup"><span data-stu-id="25a3c-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="25a3c-481">Al termine del training, assicurarsi di fare clic sul pulsante *Rendi predefinito* ancora una volta, in modo che l' *URL di stima* continui a usare l'iterazione più aggiornata del servizio.</span><span class="sxs-lookup"><span data-stu-id="25a3c-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="25a3c-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="25a3c-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="25a3c-483">Applicazione API Visione personalizzata completata</span><span class="sxs-lookup"><span data-stu-id="25a3c-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="25a3c-484">Congratulazioni, è stata creata un'app per realtà mista che sfrutta l'API Visione personalizzata di Azure per riconoscere oggetti reali, eseguire il training del modello del servizio e visualizzare la confidenza di ciò che è stato visto.</span><span class="sxs-lookup"><span data-stu-id="25a3c-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="25a3c-485">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="25a3c-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="25a3c-486">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="25a3c-486">Exercise 1</span></span>

<span data-ttu-id="25a3c-487">Eseguire il training del **servizio visione artificiale personalizzato** per riconoscere più oggetti.</span><span class="sxs-lookup"><span data-stu-id="25a3c-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="25a3c-488">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="25a3c-488">Exercise 2</span></span>

<span data-ttu-id="25a3c-489">Per ampliare i concetti appresi, completare gli esercizi seguenti:</span><span class="sxs-lookup"><span data-stu-id="25a3c-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="25a3c-490">Riprodurre un suono quando viene riconosciuto un oggetto.</span><span class="sxs-lookup"><span data-stu-id="25a3c-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="25a3c-491">Esercizio 3</span><span class="sxs-lookup"><span data-stu-id="25a3c-491">Exercise 3</span></span>

<span data-ttu-id="25a3c-492">Usare l'API per eseguire nuovamente il training del servizio con le stesse immagini analizzate dall'app, in modo da rendere più accurato il servizio (eseguire contemporaneamente la stima e la formazione).</span><span class="sxs-lookup"><span data-stu-id="25a3c-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
