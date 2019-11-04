---
title: MR e Azure 302-visione artificiale
description: Completare questo corso per apprendere come riconoscere il contenuto visivo in un'immagine fornita, usando Azure Visione artificiale in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, visione artificiale, hololens, immersiva, VR
ms.openlocfilehash: d6f792a67adfd1038ca4cdbc44b2ef1bf12a1173
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437949"
---
>[!NOTE]
><span data-ttu-id="74cd6-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="74cd6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="74cd6-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="74cd6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="74cd6-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="74cd6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="74cd6-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="74cd6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="74cd6-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="74cd6-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="74cd6-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="74cd6-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="74cd6-110">MR e Azure 302: visione artificiale</span><span class="sxs-lookup"><span data-stu-id="74cd6-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="74cd6-111">In questo corso si apprenderà come riconoscere il contenuto visivo in un'immagine fornita, usando le funzionalità di Visione artificiale di Azure in un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="74cd6-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="74cd6-112">I risultati del riconoscimento verranno visualizzati come tag descrittivi.</span><span class="sxs-lookup"><span data-stu-id="74cd6-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="74cd6-113">È possibile usare questo servizio senza dover eseguire il training di un modello di machine learning.</span><span class="sxs-lookup"><span data-stu-id="74cd6-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="74cd6-114">Se l'implementazione richiede il training di un modello di apprendimento automatico, vedere [Mr e Azure 302B](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="74cd6-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![risultato Lab](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="74cd6-116">Microsoft Visione artificiale è un set di API progettate per fornire agli sviluppatori l'elaborazione e l'analisi delle immagini (con informazioni di ritorno), usando algoritmi avanzati, dal cloud.</span><span class="sxs-lookup"><span data-stu-id="74cd6-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="74cd6-117">Gli sviluppatori caricano un URL di immagine o immagine e gli algoritmi di Microsoft API Visione artificiale analizzano il contenuto visivo, in base agli input scelti dall'utente, che possono quindi restituire informazioni, tra cui l'identificazione del tipo e della qualità di un'immagine, il rilevamento dei visi umani ( la restituzione delle coordinate), l'assegnazione di tag o la categorizzazione di immagini.</span><span class="sxs-lookup"><span data-stu-id="74cd6-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="74cd6-118">Per ulteriori informazioni, visitare la [pagina API visione artificiale di Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="74cd6-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="74cd6-119">Dopo aver completato questo corso, si disporrà di un'applicazione HoloLens in realtà mista, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="74cd6-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="74cd6-120">Usando il gesto Tap, la fotocamera del HoloLens acquisirà un'immagine.</span><span class="sxs-lookup"><span data-stu-id="74cd6-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="74cd6-121">L'immagine verrà inviata al servizio API Visione artificiale di Azure.</span><span class="sxs-lookup"><span data-stu-id="74cd6-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="74cd6-122">Gli oggetti riconosciuti saranno elencati in un gruppo di interfaccia utente semplice posizionato nella scena Unity.</span><span class="sxs-lookup"><span data-stu-id="74cd6-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="74cd6-123">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="74cd6-124">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="74cd6-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="74cd6-125">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="74cd6-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="74cd6-126">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="74cd6-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="74cd6-127">Corso</span><span class="sxs-lookup"><span data-stu-id="74cd6-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="74cd6-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="74cd6-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="74cd6-129"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="74cd6-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="74cd6-130">MR e Azure 302: visione artificiale</span><span class="sxs-lookup"><span data-stu-id="74cd6-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="74cd6-131">✔️</span><span class="sxs-lookup"><span data-stu-id="74cd6-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="74cd6-132">✔️</span><span class="sxs-lookup"><span data-stu-id="74cd6-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="74cd6-133">Sebbene questo corso sia incentrato principalmente su HoloLens, è anche possibile applicare le informazioni apprese in questo corso agli auricolari per la realtà mista (VR) di Windows.</span><span class="sxs-lookup"><span data-stu-id="74cd6-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="74cd6-134">Poiché le cuffie immersive (VR) non hanno fotocamere accessibili, sarà necessaria una fotocamera esterna connessa al PC.</span><span class="sxs-lookup"><span data-stu-id="74cd6-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="74cd6-135">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare gli auricolari immersivi (VR).</span><span class="sxs-lookup"><span data-stu-id="74cd6-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74cd6-136">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="74cd6-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="74cd6-137">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="74cd6-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="74cd6-138">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="74cd6-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="74cd6-139">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="74cd6-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="74cd6-140">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="74cd6-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="74cd6-141">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="74cd6-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="74cd6-142">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="74cd6-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="74cd6-143">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="74cd6-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="74cd6-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="74cd6-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="74cd6-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="74cd6-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="74cd6-146">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="74cd6-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="74cd6-147">Una fotocamera connessa al PC (per lo sviluppo di auricolari immersivi)</span><span class="sxs-lookup"><span data-stu-id="74cd6-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="74cd6-148">Accesso a Internet per il programma di installazione di Azure e il recupero API Visione artificiale</span><span class="sxs-lookup"><span data-stu-id="74cd6-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="74cd6-149">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="74cd6-149">Before you start</span></span>

1.  <span data-ttu-id="74cd6-150">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="74cd6-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="74cd6-151">Configurare e testare il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74cd6-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="74cd6-152">Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="74cd6-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="74cd6-153">Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="74cd6-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="74cd6-154">Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="74cd6-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="74cd6-155">Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="74cd6-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="74cd6-156">Capitolo 1: portale di Azure</span><span class="sxs-lookup"><span data-stu-id="74cd6-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="74cd6-157">Per usare il servizio *API visione artificiale* in Azure, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="74cd6-158">Per prima cosa, accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="74cd6-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="74cd6-159">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="74cd6-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="74cd6-160">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="74cd6-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="74cd6-161">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *API visione artificiale*e premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Creare una nuova risorsa in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="74cd6-163">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="74cd6-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="74cd6-164">La nuova pagina fornirà una descrizione del servizio *API visione artificiale* .</span><span class="sxs-lookup"><span data-stu-id="74cd6-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="74cd6-165">Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Informazioni sul servizio API visione artificiale](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="74cd6-167">Una volta fatto clic su **Crea**:</span><span class="sxs-lookup"><span data-stu-id="74cd6-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="74cd6-168">Inserire il **nome** desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="74cd6-169">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="74cd6-170">Selezionare il piano **tariffario** appropriato. se è la prima volta che si crea un servizio di *API visione artificiale* , è necessario che sia disponibile un livello gratuito (denominato F0).</span><span class="sxs-lookup"><span data-stu-id="74cd6-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="74cd6-171">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="74cd6-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="74cd6-172">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="74cd6-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="74cd6-173">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="74cd6-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="74cd6-174">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="74cd6-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="74cd6-175">Determinare il percorso del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="74cd6-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="74cd6-176">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="74cd6-177">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="74cd6-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="74cd6-178">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="74cd6-179">Fare clic su Crea.</span><span class="sxs-lookup"><span data-stu-id="74cd6-179">Click Create.</span></span>

        ![Informazioni sulla creazione del servizio](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="74cd6-181">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="74cd6-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="74cd6-182">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="74cd6-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Visualizza la nuova notifica per il nuovo servizio](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="74cd6-184">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Selezionare il pulsante Vai alla risorsa.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="74cd6-186">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="74cd6-187">Si verrà portati alla nuova istanza del servizio API Visione artificiale.</span><span class="sxs-lookup"><span data-stu-id="74cd6-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![Il nuovo servizio API Visione artificiale](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="74cd6-189">All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita usando la chiave di sottoscrizione del servizio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="74cd6-190">Dalla pagina *avvio rapido* del servizio *API visione artificiale* , passare al primo passaggio, selezionare le *chiavi*e fare clic su **chiavi** . a tale scopo, fare clic sui tasti di collegamento ipertestuale blu disponibili nel menu di navigazione servizi, indicato dall'icona della chiave).</span><span class="sxs-lookup"><span data-stu-id="74cd6-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="74cd6-191">Le *chiavi*del servizio vengono rivelate.</span><span class="sxs-lookup"><span data-stu-id="74cd6-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="74cd6-192">Eseguire una copia di una delle chiavi visualizzate, perché sarà necessario in un secondo momento nel progetto.</span><span class="sxs-lookup"><span data-stu-id="74cd6-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="74cd6-193">Tornare alla pagina *avvio rapido* e, da qui, recuperare l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="74cd6-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="74cd6-194">Tenere presente che l'utente può essere diverso, a seconda dell'area geografica (in questo caso, sarà necessario apportare una modifica al codice in un secondo momento).</span><span class="sxs-lookup"><span data-stu-id="74cd6-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="74cd6-195">Eseguire una copia di questo endpoint per usarlo in seguito:</span><span class="sxs-lookup"><span data-stu-id="74cd6-195">Take a copy of this endpoint for use later:</span></span>

    ![Il nuovo servizio API Visione artificiale](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="74cd6-197">È possibile controllare quali sono i vari [endpoint.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)</span><span class="sxs-lookup"><span data-stu-id="74cd6-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="74cd6-198">Capitolo 2: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="74cd6-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="74cd6-199">Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="74cd6-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="74cd6-200">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-200">Open *Unity* and click **New**.</span></span> 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="74cd6-202">A questo punto sarà necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="74cd6-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="74cd6-203">Inserire **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="74cd6-204">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="74cd6-205">Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="74cd6-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="74cd6-206">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-206">Then, click **Create project**.</span></span>

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="74cd6-208">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="74cd6-209">Passare a **Modifica preferenze >** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="74cd6-210">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="74cd6-211">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="74cd6-211">Close the **Preferences** window.</span></span>

    ![Aggiornare la preferenza dell'editor di script.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="74cd6-213">Passare quindi a **File > impostazioni di compilazione** e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Finestra impostazioni di compilazione, passa alla piattaforma UWP.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="74cd6-215">Sempre in **File > impostazioni di compilazione** e verificare che:</span><span class="sxs-lookup"><span data-stu-id="74cd6-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="74cd6-216">Il **dispositivo di destinazione** è impostato su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="74cd6-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="74cd6-217">Per gli auricolari immersivi, impostare **dispositivo di destinazione** su *qualsiasi dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="74cd6-218">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="74cd6-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="74cd6-219">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="74cd6-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="74cd6-220">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="74cd6-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="74cd6-221">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="74cd6-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="74cd6-222">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="74cd6-223">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="74cd6-224">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="74cd6-224">A save window will appear.</span></span>
        
            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="74cd6-226">Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.</span><span class="sxs-lookup"><span data-stu-id="74cd6-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crea nuova cartella script](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="74cd6-228">Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **MR_ComputerVisionScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="74cd6-230">Tenere presente che è necessario salvare le scene Unity all'interno della cartella *assets* , in quanto devono essere associate al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="74cd6-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="74cd6-231">La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="74cd6-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="74cd6-232">Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="74cd6-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="74cd6-233">Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .</span><span class="sxs-lookup"><span data-stu-id="74cd6-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="74cd6-235">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="74cd6-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="74cd6-236">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="74cd6-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="74cd6-237">La **versione di runtime di scripting** deve essere **stabile** (equivalente a .NET 3,5).</span><span class="sxs-lookup"><span data-stu-id="74cd6-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="74cd6-238">Il **back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="74cd6-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="74cd6-239">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="74cd6-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="74cd6-241">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="74cd6-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="74cd6-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="74cd6-242">**InternetClient**</span></span>
        2. <span data-ttu-id="74cd6-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="74cd6-243">**Webcam**</span></span>

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="74cd6-245">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="74cd6-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aggiornare le impostazioni X R.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="74cd6-247">Nelle *impostazioni di compilazione* i progetti _Unity C#_  non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="74cd6-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="74cd6-248">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="74cd6-249">Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="74cd6-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="74cd6-250">Capitolo 3-configurazione della fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="74cd6-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74cd6-251">Se si desidera ignorare il componente di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile scaricarlo [. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importarlo nel progetto come [pacchetto personalizzato](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="74cd6-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="74cd6-252">Nel *Pannello gerarchia*selezionare la **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="74cd6-253">Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="74cd6-254">L' **oggetto fotocamera** deve essere denominato **Main camera** (nota l'ortografia).</span><span class="sxs-lookup"><span data-stu-id="74cd6-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="74cd6-255">Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (si noti l'ortografia).</span><span class="sxs-lookup"><span data-stu-id="74cd6-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="74cd6-256">Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="74cd6-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="74cd6-257">Impostare **Cancella flag** su **colore a tinta unita** (ignorarlo per l'auricolare immersivo).</span><span class="sxs-lookup"><span data-stu-id="74cd6-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="74cd6-258">Imposta il colore di **sfondo** del componente della fotocamera su **nero, alfa 0 (codice esadecimale: #00000000)** (ignorarlo per l'auricolare immersivo).</span><span class="sxs-lookup"><span data-stu-id="74cd6-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Aggiornare i componenti della fotocamera.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="74cd6-260">Sarà quindi necessario creare un oggetto "Cursor" semplice collegato alla **fotocamera principale**, che consentirà di posizionare l'output dell'analisi dell'immagine quando l'applicazione è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="74cd6-261">Questo cursore determina il punto centrale dello stato attivo della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="74cd6-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="74cd6-262">Per creare il cursore:</span><span class="sxs-lookup"><span data-stu-id="74cd6-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="74cd6-263">Nel *Pannello gerarchia*, fare clic con il pulsante destro del mouse sulla **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="74cd6-264">In **oggetto 3D**fare clic su **sfera**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Selezionare l'oggetto cursore.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="74cd6-266">Rinominare la **sfera** in **cursore** (fare doppio clic sull'oggetto cursore o premere il pulsante della tastiera "F2" con l'oggetto selezionato) e verificare che sia posizionato come figlio della **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="74cd6-267">Nel *Pannello gerarchia*, fare clic sul **cursore**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="74cd6-268">Con il cursore selezionato, modificare le variabili seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="74cd6-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="74cd6-269">Impostare la *posizione di trasformazione* su **0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="74cd6-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="74cd6-270">Impostare la *scala* su **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="74cd6-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Aggiornare la posizione e la scala della trasformazione.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="74cd6-272">Capitolo 4: configurare il sistema di etichette</span><span class="sxs-lookup"><span data-stu-id="74cd6-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="74cd6-273">Una volta acquisita un'immagine con la fotocamera HoloLens, tale immagine verrà inviata all'istanza del servizio *API visione artificiale di Azure* per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="74cd6-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="74cd6-274">I risultati di tale analisi saranno un elenco di oggetti riconosciuti chiamati **tag**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="74cd6-275">Si useranno le etichette (come testo 3D nello spazio globale) per visualizzare questi tag nella posizione in cui è stata eseguita la foto.</span><span class="sxs-lookup"><span data-stu-id="74cd6-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="74cd6-276">Nei passaggi seguenti viene illustrato come configurare l'oggetto **Label** .</span><span class="sxs-lookup"><span data-stu-id="74cd6-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="74cd6-277">Fare clic con il pulsante destro del mouse in un punto qualsiasi del pannello gerarchia (il percorso non è rilevante a questo punto), in **oggetto 3D**, aggiungere un **testo 3D**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="74cd6-278">Denominarlo **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-278">Name it **LabelText**.</span></span>

    ![Crea oggetto testo 3D.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="74cd6-280">Nel *Pannello gerarchia*fare clic su **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="74cd6-281">Con **LabelText** selezionato, modificare le variabili seguenti nel pannello di *controllo*:</span><span class="sxs-lookup"><span data-stu-id="74cd6-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="74cd6-282">Imposta la **posizione** su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="74cd6-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="74cd6-283">Impostare la **scala** su **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="74cd6-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="74cd6-284">Nella mesh del **testo**del componente:</span><span class="sxs-lookup"><span data-stu-id="74cd6-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="74cd6-285">Sostituire tutto il testo all'interno del **testo**con "..."</span><span class="sxs-lookup"><span data-stu-id="74cd6-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="74cd6-286">Imposta l' **ancoraggio** sul **centro centrale**</span><span class="sxs-lookup"><span data-stu-id="74cd6-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="74cd6-287">Impostare l' **allineamento** al **centro**</span><span class="sxs-lookup"><span data-stu-id="74cd6-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="74cd6-288">Imposta la **dimensione della tabulazione** su **4**</span><span class="sxs-lookup"><span data-stu-id="74cd6-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="74cd6-289">Imposta la **dimensione del carattere** su **50**</span><span class="sxs-lookup"><span data-stu-id="74cd6-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="74cd6-290">Imposta il **colore** su **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="74cd6-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Componente testo](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="74cd6-292">Trascinare **LabelText** dal *Pannello gerarchia*, nella *cartella Asset*, all'interno del *Pannello Project*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="74cd6-293">In questo modo, **LabelText** viene creato un prefabbricato, in modo che sia possibile crearne un'istanza nel codice.</span><span class="sxs-lookup"><span data-stu-id="74cd6-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Creare una prefabbricata dell'oggetto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="74cd6-295">È necessario eliminare il **LabelText** dal *Pannello gerarchia*, in modo che non venga visualizzato nella scena di apertura.</span><span class="sxs-lookup"><span data-stu-id="74cd6-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="74cd6-296">Poiché è ora un prefabbricato, che verrà chiamato per le singole istanze dalla cartella assets, non è necessario mantenerlo all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="74cd6-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="74cd6-297">La struttura dell'oggetto finale nel *Pannello gerarchia* deve essere simile a quella illustrata nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="74cd6-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Struttura finale del pannello gerarchia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="74cd6-299">Capitolo 5: creare la classe ResultsLabel</span><span class="sxs-lookup"><span data-stu-id="74cd6-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="74cd6-300">Il primo script che è necessario creare è la classe *ResultsLabel* , responsabile delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="74cd6-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="74cd6-301">Creazione delle etichette nello spazio globale appropriato rispetto alla posizione della camera.</span><span class="sxs-lookup"><span data-stu-id="74cd6-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="74cd6-302">Visualizzazione dei tag dall'immagine onerosa.</span><span class="sxs-lookup"><span data-stu-id="74cd6-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="74cd6-303">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74cd6-303">To create this class:</span></span> 

1.  <span data-ttu-id="74cd6-304">Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare > cartella**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="74cd6-305">Denominare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="74cd6-305">Name the folder **Scripts**.</span></span> 

    ![Crea cartella script.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="74cd6-307">Con la cartella **Scripts** create, fare doppio clic su di essa per aprirla.</span><span class="sxs-lookup"><span data-stu-id="74cd6-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="74cd6-308">Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse e selezionare **Crea >** quindi  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="74cd6-309">Denominare lo script *ResultsLabel*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="74cd6-310">Fare doppio clic sul nuovo script *ResultsLabel* per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="74cd6-311">All'interno della classe, inserire il codice seguente nella classe *ResultsLabel* :</span><span class="sxs-lookup"><span data-stu-id="74cd6-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="74cd6-312">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="74cd6-313">Nell'editor di *Unity*fare clic e trascinare la classe *ResultsLabel* dalla cartella **Scripts** all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="74cd6-314">Fare clic sulla **fotocamera principale** ed esaminare il *pannello Inspector*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="74cd6-315">Si noterà che dallo script appena trascinato nella fotocamera sono presenti due campi: **cursore** ed **etichetta prefabbricata**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="74cd6-316">Trascinare l'oggetto denominato **cursore** dal *Pannello gerarchia* nello slot denominato **Cursor**, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="74cd6-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="74cd6-317">Trascinare l'oggetto denominato **LabelText** dalla *cartella assets* nel *Pannello Project* allo slot denominato **Label prefabric**, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="74cd6-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Impostare le destinazioni di riferimento all'interno di Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="74cd6-319">Capitolo 6: creare la classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="74cd6-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="74cd6-320">La classe successiva che si intende creare è la classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="74cd6-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="74cd6-321">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="74cd6-321">This class is responsible for:</span></span>

-   <span data-ttu-id="74cd6-322">Acquisizione di un'immagine con la fotocamera HoloLens e relativa archiviazione nella cartella dell'app.</span><span class="sxs-lookup"><span data-stu-id="74cd6-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="74cd6-323">Acquisizione dei movimenti Tap dall'utente.</span><span class="sxs-lookup"><span data-stu-id="74cd6-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="74cd6-324">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74cd6-324">To create this class:</span></span> 

1.  <span data-ttu-id="74cd6-325">Passare alla cartella **Scripts** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="74cd6-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="74cd6-326">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi **creare > C# script**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="74cd6-327">Chiamare lo script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="74cd6-328">Fare doppio clic sul nuovo script *ImageCapture* per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="74cd6-329">Aggiungere i seguenti spazi dei nomi all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="74cd6-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="74cd6-330">Aggiungere quindi le variabili seguenti all'interno della classe *ImageCapture* , sopra il metodo *Start ()* :</span><span class="sxs-lookup"><span data-stu-id="74cd6-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="74cd6-331">Nella variabile **tapsCount** viene archiviato il numero di movimenti Tap acquisiti dall'utente.</span><span class="sxs-lookup"><span data-stu-id="74cd6-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="74cd6-332">Questo numero viene usato per la denominazione delle immagini acquisite.</span><span class="sxs-lookup"><span data-stu-id="74cd6-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="74cd6-333">È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="74cd6-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="74cd6-334">Questi verranno chiamati quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="74cd6-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="74cd6-335">Implementare un gestore che verrà chiamato quando si verifica un movimento tap.</span><span class="sxs-lookup"><span data-stu-id="74cd6-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="74cd6-336">Il metodo *TapHandler ()* incrementa il numero di rubinetti acquisiti dall'utente e utilizza la posizione corrente del cursore per determinare la posizione in cui posizionare una nuova etichetta.</span><span class="sxs-lookup"><span data-stu-id="74cd6-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="74cd6-337">Questo metodo chiama quindi il metodo *ExecuteImageCaptureAndAnalysis ()* per avviare la funzionalità di base di questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="74cd6-338">Una volta acquisita e archiviata un'immagine, verranno chiamati i gestori seguenti.</span><span class="sxs-lookup"><span data-stu-id="74cd6-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="74cd6-339">Se il processo ha esito positivo, il risultato viene passato a *VisionManager* (che è ancora necessario creare) per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="74cd6-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="74cd6-340">Aggiungere quindi il metodo usato dall'applicazione per avviare il processo di acquisizione dell'immagine e archiviare l'immagine.</span><span class="sxs-lookup"><span data-stu-id="74cd6-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="74cd6-341">A questo punto si noterà un errore nel *Pannello console dell'editor di Unity*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="74cd6-342">Questo perché il codice fa riferimento alla classe *VisionManager* che verrà creata nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="74cd6-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="74cd6-343">Capitolo 7-chiamata ad Azure e analisi delle immagini</span><span class="sxs-lookup"><span data-stu-id="74cd6-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="74cd6-344">L'ultimo script che è necessario creare è la classe *VisionManager* .</span><span class="sxs-lookup"><span data-stu-id="74cd6-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="74cd6-345">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="74cd6-345">This class is responsible for:</span></span>

-   <span data-ttu-id="74cd6-346">Caricamento dell'immagine più recente acquisita come matrice di byte.</span><span class="sxs-lookup"><span data-stu-id="74cd6-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="74cd6-347">Invio della matrice di byte all'istanza del servizio *API visione artificiale di Azure* per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="74cd6-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="74cd6-348">Ricezione della risposta come stringa JSON.</span><span class="sxs-lookup"><span data-stu-id="74cd6-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="74cd6-349">Deserializzazione della risposta e passaggio dei tag risultanti alla classe *ResultsLabel* .</span><span class="sxs-lookup"><span data-stu-id="74cd6-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="74cd6-350">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74cd6-350">To create this class:</span></span>

1.  <span data-ttu-id="74cd6-351">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="74cd6-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="74cd6-352">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="74cd6-353">Denominare lo script *VisionManager*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="74cd6-354">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="74cd6-355">Aggiornare gli spazi dei nomi in modo che corrispondano a quelli riportati di seguito, all'inizio della classe *VisionManager* :</span><span class="sxs-lookup"><span data-stu-id="74cd6-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="74cd6-356">All'inizio dello script, *all'interno* della classe *VisionManager* (sopra il metodo *Start ()* ), è ora necessario creare due *classi* che rappresenteranno la risposta JSON deserializzata da Azure:</span><span class="sxs-lookup"><span data-stu-id="74cd6-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="74cd6-357">Le classi *TagData* e *AnalysedObject* devono avere l'attributo *[System. Serializable]* aggiunto prima della dichiarazione per poter essere deserializzato con le librerie di Unity.</span><span class="sxs-lookup"><span data-stu-id="74cd6-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="74cd6-358">Nella classe VisionManager è necessario aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="74cd6-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="74cd6-359">Assicurarsi di inserire la **chiave di autenticazione** nella variabile **authorizationKey** .</span><span class="sxs-lookup"><span data-stu-id="74cd6-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="74cd6-360">Si noterà che la **chiave di autenticazione** è stata annotata all'inizio di questo corso, [capitolo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="74cd6-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="74cd6-361">La variabile **visionAnalysisEndpoint** potrebbe essere diversa da quella specificata in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="74cd6-362">Gli **Stati Uniti occidentali** si riferiscono esclusivamente alle istanze del servizio create per l'area Stati Uniti occidentali.</span><span class="sxs-lookup"><span data-stu-id="74cd6-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="74cd6-363">Aggiornarlo con l' [URL dell'endpoint](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). di seguito sono riportati alcuni esempi di ciò che potrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="74cd6-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="74cd6-364">Europa occidentale: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="74cd6-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="74cd6-365">Asia sudorientale: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="74cd6-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="74cd6-366">Australia orientale: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="74cd6-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="74cd6-367">È necessario aggiungere il codice per l'ora di riattivazione.</span><span class="sxs-lookup"><span data-stu-id="74cd6-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="74cd6-368">Aggiungere quindi la coroutine (con il metodo del flusso statico sotto di essa), che otterrà i risultati dell'analisi dell'immagine acquisita dalla classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="74cd6-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="74cd6-369">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="74cd6-370">Nell'editor di Unity fare clic e trascinare le classi *VisionManager* e *ImageCapture* dalla cartella **Scripts** all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="74cd6-371">Capitolo 8-prima della compilazione</span><span class="sxs-lookup"><span data-stu-id="74cd6-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="74cd6-372">Per eseguire un test completo dell'applicazione, è necessario sideload nel HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74cd6-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="74cd6-373">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="74cd6-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="74cd6-374">Tutte le impostazioni indicate nel [capitolo 2](#chapter-2--set-up-the-unity-project) sono impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="74cd6-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="74cd6-375">Tutti gli script sono collegati all'oggetto **principale della fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="74cd6-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="74cd6-376">Tutti i campi nel *pannello principale di controllo della fotocamera* sono assegnati correttamente.</span><span class="sxs-lookup"><span data-stu-id="74cd6-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="74cd6-377">Assicurarsi di inserire la **chiave di autenticazione** nella variabile **authorizationKey** .</span><span class="sxs-lookup"><span data-stu-id="74cd6-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="74cd6-378">Assicurarsi di aver controllato anche l'endpoint nello script *VisionManager* e che sia allineato all'area geografica (in questo documento vengono usati *Stati Uniti occidentali* *per impostazione* predefinita).</span><span class="sxs-lookup"><span data-stu-id="74cd6-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="74cd6-379">Capitolo 9: compilare la soluzione UWP e sideload l'applicazione</span><span class="sxs-lookup"><span data-stu-id="74cd6-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="74cd6-380">Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.</span><span class="sxs-lookup"><span data-stu-id="74cd6-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="74cd6-381">Passare a *Impostazioni compilazione* - **file > impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="74cd6-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="74cd6-382">Nella finestra *impostazioni di compilazione* fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="74cd6-384">Se non è già stato fatto, è necessario che i **progetti Unity C#**</span><span class="sxs-lookup"><span data-stu-id="74cd6-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="74cd6-385">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-385">Click **Build**.</span></span> <span data-ttu-id="74cd6-386">Unity avvierà una finestra di *Esplora file* , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="74cd6-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="74cd6-387">Creare la cartella adesso e denominarla *app*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="74cd6-388">Quindi, con la cartella dell' *app* selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="74cd6-389">Unity inizierà a compilare il progetto nella cartella dell' *app* .</span><span class="sxs-lookup"><span data-stu-id="74cd6-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="74cd6-390">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra *Esplora file* nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).</span><span class="sxs-lookup"><span data-stu-id="74cd6-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="74cd6-391">Capitolo 10: eseguire la distribuzione in HoloLens</span><span class="sxs-lookup"><span data-stu-id="74cd6-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="74cd6-392">Per eseguire la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="74cd6-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="74cd6-393">È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="74cd6-394">A tale scopo, effettua le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="74cd6-394">To do this:</span></span>

    1. <span data-ttu-id="74cd6-395">Quando si indossa il HoloLens, aprire le **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="74cd6-396">Passare a **rete & Internet > opzioni avanzate Wi-Fi >**</span><span class="sxs-lookup"><span data-stu-id="74cd6-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="74cd6-397">Prendere nota dell'indirizzo **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="74cd6-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="74cd6-398">Quindi, tornare a **Settings (impostazioni**) e quindi **aggiornare & Security > per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="74cd6-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="74cd6-399">Impostare la modalità di sviluppo su.</span><span class="sxs-lookup"><span data-stu-id="74cd6-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="74cd6-400">Passare alla nuova compilazione Unity (cartella *app* ) e aprire il file della soluzione con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="74cd6-401">Nella configurazione della soluzione selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="74cd6-402">Nella piattaforma soluzione selezionare **x86**, **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="74cd6-404">Passare al **menu Compila** e fare clic su **Distribuisci soluzione**per sideload l'applicazione in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74cd6-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="74cd6-405">L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="74cd6-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="74cd6-406">Per eseguire la distribuzione in un dispositivo headset immersivo, impostare la **piattaforma della soluzione** su *computer locale*e impostare la **configurazione** su *debug*, con *x86* come **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="74cd6-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="74cd6-407">Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*.</span><span class="sxs-lookup"><span data-stu-id="74cd6-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="74cd6-408">Applicazione API Visione artificiale completata</span><span class="sxs-lookup"><span data-stu-id="74cd6-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="74cd6-409">Congratulazioni, è stata creata un'app per realtà mista che sfrutta la API Visione artificiale di Azure per riconoscere gli oggetti reali e visualizzare la confidenza di ciò che è stato visto.</span><span class="sxs-lookup"><span data-stu-id="74cd6-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![risultato Lab](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="74cd6-411">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="74cd6-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="74cd6-412">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="74cd6-412">Exercise 1</span></span>

<span data-ttu-id="74cd6-413">Così come è stato usato il parametro *Tags* (come evidenziato all'interno dell' *endpoint* usato in *VisionManager*), estendere l'app per rilevare altre informazioni; esaminare gli altri parametri [a cui si ha accesso.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)</span><span class="sxs-lookup"><span data-stu-id="74cd6-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="74cd6-414">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="74cd6-414">Exercise 2</span></span>

<span data-ttu-id="74cd6-415">Visualizza i dati di Azure restituiti, in modo più colloquiale e leggibile, forse nascondendo i numeri.</span><span class="sxs-lookup"><span data-stu-id="74cd6-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="74cd6-416">Come se un bot potesse parlare con l'utente.</span><span class="sxs-lookup"><span data-stu-id="74cd6-416">As though a bot might be speaking to the user.</span></span>
