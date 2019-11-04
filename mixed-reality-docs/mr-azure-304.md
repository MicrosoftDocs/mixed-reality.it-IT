---
title: MR e Azure 304-riconoscimento facciale
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, riconoscimento viso, hololens, immersive, VR
ms.openlocfilehash: ef75be5485f85538eb8b3db3eebec63b166f7aa3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438500"
---
>[!NOTE]
><span data-ttu-id="9a791-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="9a791-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9a791-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="9a791-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9a791-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9a791-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9a791-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="9a791-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9a791-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9a791-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9a791-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="9a791-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="9a791-110">MR e Azure 304: riconoscimento viso</span><span class="sxs-lookup"><span data-stu-id="9a791-110">MR and Azure 304: Face recognition</span></span>

![risultato del completamento del corso](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="9a791-112">In questo corso si apprenderà come aggiungere funzionalità di riconoscimento viso a un'applicazione di realtà mista usando servizi cognitivi di Azure con Microsoft API Viso.</span><span class="sxs-lookup"><span data-stu-id="9a791-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="9a791-113">*Azure API viso* è un servizio Microsoft, che fornisce agli sviluppatori gli algoritmi volti più avanzati, tutto nel cloud.</span><span class="sxs-lookup"><span data-stu-id="9a791-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="9a791-114">Il *API viso* dispone di due funzioni principali: il rilevamento viso con attributi e il riconoscimento viso.</span><span class="sxs-lookup"><span data-stu-id="9a791-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="9a791-115">In questo modo gli sviluppatori possono semplicemente impostare un set di gruppi per i visi e quindi inviare immagini di query al servizio in un secondo momento, per determinare a chi appartiene un viso.</span><span class="sxs-lookup"><span data-stu-id="9a791-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="9a791-116">Per ulteriori informazioni, visitare la [pagina Azure Face Recognition](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="9a791-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="9a791-117">Dopo aver completato questo corso, si disporrà di un'applicazione HoloLens in realtà mista, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="9a791-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="9a791-118">Usare un **movimento Tap** per avviare l'acquisizione di un'immagine usando la fotocamera HoloLens a bordo.</span><span class="sxs-lookup"><span data-stu-id="9a791-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="9a791-119">Inviare l'immagine acquisita al servizio *API viso di Azure* .</span><span class="sxs-lookup"><span data-stu-id="9a791-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="9a791-120">Ricevere i risultati dell'algoritmo di *API viso* .</span><span class="sxs-lookup"><span data-stu-id="9a791-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="9a791-121">Utilizzare un'interfaccia utente semplice per visualizzare il nome delle persone corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="9a791-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="9a791-122">In questo modo verrà illustrato come ottenere i risultati dal servizio API Viso nell'applicazione di realtà mista basata su Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="9a791-123">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="9a791-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="9a791-124">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="9a791-125">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="9a791-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="9a791-126">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="9a791-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9a791-127">Corso</span><span class="sxs-lookup"><span data-stu-id="9a791-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9a791-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9a791-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9a791-129"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="9a791-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="9a791-130">MR e Azure 304: riconoscimento viso</span><span class="sxs-lookup"><span data-stu-id="9a791-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="9a791-131">✔️</span><span class="sxs-lookup"><span data-stu-id="9a791-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9a791-132">✔️</span><span class="sxs-lookup"><span data-stu-id="9a791-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="9a791-133">Sebbene questo corso sia incentrato principalmente su HoloLens, è anche possibile applicare le informazioni apprese in questo corso agli auricolari per la realtà mista (VR) di Windows.</span><span class="sxs-lookup"><span data-stu-id="9a791-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="9a791-134">Poiché le cuffie immersive (VR) non hanno fotocamere accessibili, sarà necessaria una fotocamera esterna connessa al PC.</span><span class="sxs-lookup"><span data-stu-id="9a791-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="9a791-135">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare gli auricolari immersivi (VR).</span><span class="sxs-lookup"><span data-stu-id="9a791-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9a791-136">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="9a791-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="9a791-137">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="9a791-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="9a791-138">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="9a791-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="9a791-139">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="9a791-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="9a791-140">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="9a791-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="9a791-141">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="9a791-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="9a791-142">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="9a791-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="9a791-143">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="9a791-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="9a791-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="9a791-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="9a791-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9a791-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="9a791-146">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="9a791-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="9a791-147">Una fotocamera connessa al PC (per lo sviluppo di auricolari immersivi)</span><span class="sxs-lookup"><span data-stu-id="9a791-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="9a791-148">Accesso a Internet per il programma di installazione di Azure e il recupero API Viso</span><span class="sxs-lookup"><span data-stu-id="9a791-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="9a791-149">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="9a791-149">Before you start</span></span>

1.  <span data-ttu-id="9a791-150">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="9a791-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="9a791-151">Configurare e testare il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9a791-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="9a791-152">Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="9a791-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="9a791-153">Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="9a791-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="9a791-154">Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="9a791-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="9a791-155">Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="9a791-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="9a791-156">Capitolo 1-portale di Azure</span><span class="sxs-lookup"><span data-stu-id="9a791-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="9a791-157">Per usare il servizio *API viso* in Azure, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9a791-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="9a791-158">Per prima cosa, accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9a791-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="9a791-159">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="9a791-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="9a791-160">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="9a791-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="9a791-161">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *API viso*, quindi premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="9a791-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![Cerca API viso](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="9a791-163">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="9a791-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="9a791-164">La nuova pagina fornirà una descrizione del servizio *API viso* .</span><span class="sxs-lookup"><span data-stu-id="9a791-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="9a791-165">Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="9a791-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![informazioni sull'API viso](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="9a791-167">Una volta fatto clic su **Crea**:</span><span class="sxs-lookup"><span data-stu-id="9a791-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="9a791-168">Inserire il nome desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="9a791-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="9a791-169">Selezionare una sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="9a791-169">Select a subscription.</span></span>

    3. <span data-ttu-id="9a791-170">Selezionare il piano tariffario appropriato. se è la prima volta che si crea un *servizio di API viso*, è necessario che sia disponibile un livello gratuito (denominato F0).</span><span class="sxs-lookup"><span data-stu-id="9a791-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="9a791-171">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="9a791-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="9a791-172">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="9a791-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="9a791-173">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="9a791-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="9a791-174">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="9a791-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="9a791-175">L'app UWP, **persona Maker**, che viene usata in un secondo momento, richiede l'uso di "Stati Uniti occidentali" per la località.</span><span class="sxs-lookup"><span data-stu-id="9a791-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="9a791-176">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="9a791-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="9a791-177">Selezionare \**Crea *.**</span><span class="sxs-lookup"><span data-stu-id="9a791-177">Select **Create\*.**</span></span>

        ![Crea servizio API viso](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="9a791-179">Una volta fatto clic su \**Crea *,** sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="9a791-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="9a791-180">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="9a791-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notifica di creazione del servizio](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="9a791-182">Fare clic sulle notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="9a791-182">Click on the notifications to explore your new Service instance.</span></span>

    ![passa a notifica risorse](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="9a791-184">Quando si è pronti, fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="9a791-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![chiavi API della faccia di accesso](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="9a791-186">All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione che viene eseguita tramite l'uso della sottoscrizione ' Key ' del servizio.</span><span class="sxs-lookup"><span data-stu-id="9a791-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="9a791-187">Dalla pagina *avvio rapido* del servizio *API viso* , il primo punto è il numero 1, per recuperare *le chiavi.*</span><span class="sxs-lookup"><span data-stu-id="9a791-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="9a791-188">Nella pagina del *servizio* selezionare il collegamento ipertestuale **chiavi** blu (se nella pagina avvio rapido) o il collegamento **chiavi** nel menu di navigazione servizi (a sinistra, indicato dall'icona "chiave"), per rivelare le chiavi.</span><span class="sxs-lookup"><span data-stu-id="9a791-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="9a791-189">Prendere nota di una delle chiavi e proteggerla, perché sarà necessaria in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="9a791-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="9a791-190">Capitolo 2-uso dell'applicazione UWP ' person Maker '</span><span class="sxs-lookup"><span data-stu-id="9a791-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="9a791-191">Assicurarsi di scaricare l'applicazione UWP predefinita denominata [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="9a791-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="9a791-192">Questa app non è il prodotto finale per questo corso, ma solo uno strumento che consente di creare le voci di Azure su cui si basa il progetto successivo.</span><span class="sxs-lookup"><span data-stu-id="9a791-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="9a791-193">**Persona Maker** consente di creare voci di Azure, associate a utenti e gruppi di utenti.</span><span class="sxs-lookup"><span data-stu-id="9a791-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="9a791-194">L'applicazione inserisce tutte le informazioni necessarie in un formato che può essere usato in un secondo momento da FaceAPI, in modo da riconoscere i visi degli utenti che sono stati aggiunti.</span><span class="sxs-lookup"><span data-stu-id="9a791-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="9a791-195">IMPORTANTE La **persona Maker** usa alcune limitazioni di base per garantire che il numero di chiamate al servizio al minuto per il **livello di abbonamento gratuito**non venga superato.</span><span class="sxs-lookup"><span data-stu-id="9a791-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="9a791-196">Il testo verde nella parte superiore verrà modificato in rosso e verrà aggiornato come ' ACTIVE ' quando si verifica la limitazione; in tal caso, è sufficiente attendere che l'applicazione continui ad accedere al servizio face, aggiornando come ' IN-ACTIVE ' quando è possibile riutilizzarla.</span><span class="sxs-lookup"><span data-stu-id="9a791-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="9a791-197">Questa applicazione usa le librerie *Microsoft. ProjectOxford. Face* che consentono di sfruttare al meglio le API viso.</span><span class="sxs-lookup"><span data-stu-id="9a791-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="9a791-198">Questa libreria è disponibile gratuitamente come pacchetto NuGet.</span><span class="sxs-lookup"><span data-stu-id="9a791-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="9a791-199">Per altre informazioni su questo e sulle API simili, vedere [l'articolo di riferimento sulle API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="9a791-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="9a791-200">Questi sono solo i passaggi necessari. le istruzioni su come eseguire queste operazioni sono più avanti nel documento.</span><span class="sxs-lookup"><span data-stu-id="9a791-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="9a791-201">L'app **Person Maker** consentirà di:</span><span class="sxs-lookup"><span data-stu-id="9a791-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="9a791-202">Creare un *gruppo*di persone, ovvero un gruppo composto da più persone a cui si desidera associarlo.</span><span class="sxs-lookup"><span data-stu-id="9a791-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="9a791-203">Con l'account Azure è possibile ospitare più gruppi di persone.</span><span class="sxs-lookup"><span data-stu-id="9a791-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="9a791-204">Creare una *persona*, che è un membro di un gruppo di persone.</span><span class="sxs-lookup"><span data-stu-id="9a791-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="9a791-205">Ogni persona ha un certo numero di immagini *facciali* associate.</span><span class="sxs-lookup"><span data-stu-id="9a791-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="9a791-206">Assegnare le *Immagini facciali* a una *persona*per consentire al servizio API viso di Azure di riconoscere una *persona* con la *faccia*corrispondente.</span><span class="sxs-lookup"><span data-stu-id="9a791-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="9a791-207">Eseguire il *Training* del *servizio API viso di Azure*.</span><span class="sxs-lookup"><span data-stu-id="9a791-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="9a791-208">Tenere presente che, per eseguire il training dell'app in modo che riconosca le persone, saranno necessarie dieci (10) foto di primo piano di ogni persona che si desidera aggiungere al gruppo di persone.</span><span class="sxs-lookup"><span data-stu-id="9a791-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="9a791-209">L'app di Windows 10 CAM può aiutarti a eseguire queste app.</span><span class="sxs-lookup"><span data-stu-id="9a791-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="9a791-210">È necessario assicurarsi che ogni foto sia chiara (evitare la sfocatura, l'oscuramento o la distanza dal soggetto), avere la foto in formato di file jpg o PNG, con le dimensioni del file di immagine non maggiori di **4 MB**e non inferiori a **1 KB**.</span><span class="sxs-lookup"><span data-stu-id="9a791-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="9a791-211">Se si segue questa esercitazione, non usare il proprio viso per il training, come quando si inserisce il HoloLens, non è possibile esaminare se stessi.</span><span class="sxs-lookup"><span data-stu-id="9a791-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="9a791-212">Usare la faccia di un collega o di un altro studente.</span><span class="sxs-lookup"><span data-stu-id="9a791-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="9a791-213">**Autore della persona**che esegue:</span><span class="sxs-lookup"><span data-stu-id="9a791-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="9a791-214">Aprire la cartella **PersonMaker** e fare doppio clic sulla *soluzione PersonMaker* per aprirla con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="9a791-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="9a791-215">Dopo aver aperto la *soluzione PersonMaker* , verificare che:</span><span class="sxs-lookup"><span data-stu-id="9a791-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="9a791-216">La *configurazione della soluzione* è impostata su **debug**.</span><span class="sxs-lookup"><span data-stu-id="9a791-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="9a791-217">La *piattaforma della soluzione* è impostata su **x86**</span><span class="sxs-lookup"><span data-stu-id="9a791-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="9a791-218">La *piattaforma di destinazione* è il **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="9a791-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="9a791-219">Potrebbe anche essere necessario *ripristinare i pacchetti NuGet* facendo clic con il pulsante destro del mouse sulla *soluzione* e selezionando **Ripristina pacchetti NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9a791-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="9a791-220">Fare clic su *computer locale* e l'applicazione viene avviata.</span><span class="sxs-lookup"><span data-stu-id="9a791-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="9a791-221">Tenere presente che, su schermi più piccoli, tutto il contenuto potrebbe non essere visibile, anche se è possibile scorrere ulteriormente verso il basso per visualizzarlo.</span><span class="sxs-lookup"><span data-stu-id="9a791-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![interfaccia utente di PERSON Maker](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="9a791-223">Inserire la **chiave di autenticazione di Azure**, che dovrebbe essere disponibile, dal servizio *API viso* in Azure.</span><span class="sxs-lookup"><span data-stu-id="9a791-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="9a791-224">Inserire</span><span class="sxs-lookup"><span data-stu-id="9a791-224">Insert:</span></span>

    1. <span data-ttu-id="9a791-225">*ID* da assegnare al *gruppo person*.</span><span class="sxs-lookup"><span data-stu-id="9a791-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="9a791-226">L'ID deve essere minuscolo, senza spazi.</span><span class="sxs-lookup"><span data-stu-id="9a791-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="9a791-227">Prendere nota di questo ID, perché sarà necessario in un secondo momento nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="9a791-228">*Nome* che si desidera assegnare al *gruppo person* (può contenere spazi).</span><span class="sxs-lookup"><span data-stu-id="9a791-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="9a791-229">Premere il pulsante **Crea gruppo di persone** .</span><span class="sxs-lookup"><span data-stu-id="9a791-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="9a791-230">Sotto il pulsante verrà visualizzato un messaggio di conferma.</span><span class="sxs-lookup"><span data-stu-id="9a791-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="9a791-231">Se si verifica un errore di accesso negato, controllare il percorso impostato per il servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="9a791-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="9a791-232">Come indicato in precedenza, questa app è progettata per "Stati Uniti occidentali".</span><span class="sxs-lookup"><span data-stu-id="9a791-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a791-233">Si noterà che è possibile anche fare clic sul pulsante **Recupera un gruppo noto** , ovvero se è già stato creato un gruppo di persone e si desidera utilizzarlo, anziché crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="9a791-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="9a791-234">Tenere presente che, se si fa clic su *Crea un gruppo di persone* con un gruppo noto, viene recuperato anche un gruppo.</span><span class="sxs-lookup"><span data-stu-id="9a791-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="9a791-235">Inserire il *nome* della *persona* che si desidera creare.</span><span class="sxs-lookup"><span data-stu-id="9a791-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="9a791-236">Fare clic sul pulsante **Crea persona** .</span><span class="sxs-lookup"><span data-stu-id="9a791-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="9a791-237">Sotto il pulsante verrà visualizzato un messaggio di conferma.</span><span class="sxs-lookup"><span data-stu-id="9a791-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="9a791-238">Se si desidera eliminare una persona creata in precedenza, è possibile scrivere il nome nella casella di testo e premere **Canc person** .</span><span class="sxs-lookup"><span data-stu-id="9a791-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="9a791-239">Assicurarsi di avere la posizione di dieci (10) foto della persona che si vuole aggiungere al gruppo.</span><span class="sxs-lookup"><span data-stu-id="9a791-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="9a791-240">Premere **Crea e Apri cartella** per aprire Esplora risorse e la cartella associata alla persona.</span><span class="sxs-lookup"><span data-stu-id="9a791-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="9a791-241">Aggiungere le dieci (10) immagini nella cartella.</span><span class="sxs-lookup"><span data-stu-id="9a791-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="9a791-242">Il formato del file deve essere *jpg* o *png* .</span><span class="sxs-lookup"><span data-stu-id="9a791-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="9a791-243">Fare clic su **Invia ad Azure**.</span><span class="sxs-lookup"><span data-stu-id="9a791-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="9a791-244">Un contatore indicherà lo stato dell'invio, seguito da un messaggio al termine dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="9a791-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="9a791-245">Una volta completato il contatore e visualizzato un messaggio di conferma, fare clic su **Training** per eseguire il training del servizio.</span><span class="sxs-lookup"><span data-stu-id="9a791-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="9a791-246">Al termine del processo, si è pronti per passare a Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="9a791-247">Capitolo 3: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="9a791-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="9a791-248">Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="9a791-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="9a791-249">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="9a791-249">Open *Unity* and click **New**.</span></span> 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="9a791-251">A questo punto sarà necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="9a791-252">Inserire **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="9a791-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="9a791-253">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="9a791-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="9a791-254">Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="9a791-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="9a791-255">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="9a791-255">Then, click **Create project**.</span></span>

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="9a791-257">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9a791-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="9a791-258">Passare a **Modifica preferenze >** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="9a791-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="9a791-259">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="9a791-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="9a791-260">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="9a791-260">Close the **Preferences** window.</span></span>

    ![Aggiornare la preferenza dell'editor di script.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="9a791-262">Passare quindi a **File > impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="9a791-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Finestra impostazioni di compilazione, passa alla piattaforma UWP.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="9a791-264">Passare a **File > impostazioni di compilazione** e verificare che:</span><span class="sxs-lookup"><span data-stu-id="9a791-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="9a791-265">Il **dispositivo di destinazione** è impostato su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="9a791-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="9a791-266">Per gli auricolari immersivi, impostare **dispositivo di destinazione** su *qualsiasi dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="9a791-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="9a791-267">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="9a791-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="9a791-268">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="9a791-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="9a791-269">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="9a791-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="9a791-270">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="9a791-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="9a791-271">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="9a791-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="9a791-272">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="9a791-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="9a791-273">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="9a791-273">A save window will appear.</span></span>

            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="9a791-275">Selezionare il pulsante **nuova cartella** per creare una nuova cartella, denominarla **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="9a791-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crea nuova cartella script](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="9a791-277">Aprire la cartella **Scenes** appena creata e quindi nel campo **nome file**: testo digitare **FaceRecScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="9a791-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="9a791-279">Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="9a791-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="9a791-280">Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .</span><span class="sxs-lookup"><span data-stu-id="9a791-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="9a791-282">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="9a791-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="9a791-283">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="9a791-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="9a791-284">La **versione di runtime** di **Scripting** deve essere **sperimentale** (equivalente a .NET 4,6).</span><span class="sxs-lookup"><span data-stu-id="9a791-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="9a791-285">Se si modifica questa impostazione, è necessario riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="9a791-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="9a791-286">Il **back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="9a791-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="9a791-287">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="9a791-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="9a791-289">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="9a791-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="9a791-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="9a791-290">**InternetClient**</span></span>
        - <span data-ttu-id="9a791-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="9a791-291">**Webcam**</span></span>

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="9a791-293">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="9a791-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aggiornare le impostazioni X R.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="9a791-295">Nelle *impostazioni di compilazione*, **i C# progetti Unity** non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="9a791-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="9a791-296">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="9a791-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="9a791-297">Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="9a791-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="9a791-298">Capitolo 4-configurazione della fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="9a791-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a791-299">Se si desidera ignorare il componente di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile [scaricare questo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo nel progetto come [pacchetto personalizzato](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="9a791-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="9a791-300">Tenere presente che questo pacchetto include anche l'importazione della *dll Newtonsoft*, illustrata nel [capitolo 5](#chapter-5--import-the-newtonsoftjson-library).</span><span class="sxs-lookup"><span data-stu-id="9a791-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="9a791-301">Con questa importazione, è possibile continuare dal [capitolo 6](#chapter-6---create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="9a791-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="9a791-302">Nel pannello *gerarchia* selezionare la **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="9a791-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="9a791-303">Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="9a791-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="9a791-304">L' **oggetto fotocamera** deve essere denominato **Main camera** (nota l'ortografia).</span><span class="sxs-lookup"><span data-stu-id="9a791-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="9a791-305">Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (si noti l'ortografia).</span><span class="sxs-lookup"><span data-stu-id="9a791-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="9a791-306">Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="9a791-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="9a791-307">Imposta **Cancella flag** su **colore a tinta unita**</span><span class="sxs-lookup"><span data-stu-id="9a791-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="9a791-308">Imposta il colore di **sfondo** del componente della fotocamera su **nero, alfa 0 (codice esadecimale: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="9a791-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![configurare i componenti della fotocamera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="9a791-310">Capitolo 5: importare la libreria Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="9a791-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a791-311">Se il ". file unitypackage Tools" è stato importato nell' [ultimo capitolo](#chapter-4---main-camera-setup), è possibile ignorare questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="9a791-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="9a791-312">Per semplificare la deserializzazione e la serializzazione degli oggetti ricevuti e inviati al servizio bot, è necessario scaricare la libreria *Newtonsoft. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a791-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="9a791-313">È presente una versione compatibile già organizzata con la struttura di cartelle Unity corretta in questo [file di pacchetto Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="9a791-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="9a791-314">Per importare la libreria:</span><span class="sxs-lookup"><span data-stu-id="9a791-314">To import the library:</span></span>

1.  <span data-ttu-id="9a791-315">Scaricare il pacchetto Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="9a791-316">Fare clic su **Asset**, **Importa pacchetto**, **pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="9a791-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Importare la libreria Newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="9a791-318">Cercare il pacchetto Unity scaricato e fare clic su Apri.</span><span class="sxs-lookup"><span data-stu-id="9a791-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="9a791-319">Verificare che tutti i componenti del pacchetto siano stati sottoselezionati e fare clic su **Importa**.</span><span class="sxs-lookup"><span data-stu-id="9a791-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Importare la libreria Newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="9a791-321">Capitolo 6: creare la classe FaceAnalysis</span><span class="sxs-lookup"><span data-stu-id="9a791-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="9a791-322">Lo scopo della classe FaceAnalysis è di ospitare i metodi necessari per comunicare con il servizio Azure Face Cognition.</span><span class="sxs-lookup"><span data-stu-id="9a791-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="9a791-323">Dopo aver inviato il servizio a un'immagine di acquisizione, lo analizzerà e identificherà i visi in e ne determinerà l'eventuale appartenenza a una persona nota.</span><span class="sxs-lookup"><span data-stu-id="9a791-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="9a791-324">Se viene trovata una persona nota, questa classe ne visualizzerà il nome come testo dell'interfaccia utente nella scena.</span><span class="sxs-lookup"><span data-stu-id="9a791-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="9a791-325">Per creare la classe *FaceAnalysis* :</span><span class="sxs-lookup"><span data-stu-id="9a791-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="9a791-326">Fare clic con il pulsante destro del mouse sulla *cartella assets* nel pannello Project, quindi scegliere **Crea** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="9a791-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="9a791-327">Chiamare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="9a791-327">Call the folder **Scripts**.</span></span> 

    ![Creare la classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="9a791-329">Fare doppio clic sulla cartella appena creata per aprirla.</span><span class="sxs-lookup"><span data-stu-id="9a791-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="9a791-330">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi fare clic su **Crea** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="9a791-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="9a791-331">Chiamare lo script *FaceAnalysis*.</span><span class="sxs-lookup"><span data-stu-id="9a791-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="9a791-332">Fare doppio clic sul nuovo script *FaceAnalysis* per aprirlo con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9a791-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="9a791-333">Immettere gli spazi dei nomi seguenti sopra la classe *FaceAnalysis* :</span><span class="sxs-lookup"><span data-stu-id="9a791-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="9a791-334">È ora necessario aggiungere tutti gli oggetti utilizzati per deserialising.</span><span class="sxs-lookup"><span data-stu-id="9a791-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="9a791-335">Questi oggetti devono essere aggiunti **all'esterno** dello script *FaceAnalysis* (sotto la parentesi graffa inferiore).</span><span class="sxs-lookup"><span data-stu-id="9a791-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="9a791-336">I metodi *Start ()* e *Update ()* non verranno usati, quindi eliminarli ora.</span><span class="sxs-lookup"><span data-stu-id="9a791-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="9a791-337">All'interno della classe *FaceAnalysis* aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="9a791-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="9a791-338">Sostituire la **chiave** e il **PersonGroupId** con la chiave del servizio e l'ID del gruppo creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="9a791-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="9a791-339">Aggiungere il metodo *sveglie ()* , che inizializza la classe, aggiungendo la classe *ImageCapture* alla fotocamera principale e chiama il metodo di creazione dell'etichetta:</span><span class="sxs-lookup"><span data-stu-id="9a791-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="9a791-340">Aggiungere il metodo *CreateLabel ()* , che crea l'oggetto *Label* per visualizzare il risultato dell'analisi:</span><span class="sxs-lookup"><span data-stu-id="9a791-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="9a791-341">Aggiungere il metodo *DetectFacesFromImage ()* e *GetImageAsByteArray ()* .</span><span class="sxs-lookup"><span data-stu-id="9a791-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="9a791-342">Il primo richiederà al servizio di riconoscimento delle facce di rilevare qualsiasi possibile aspetto nell'immagine inviata, mentre quest'ultimo è necessario per convertire l'immagine acquisita in una matrice di byte:</span><span class="sxs-lookup"><span data-stu-id="9a791-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="9a791-343">Aggiungere il metodo *IdentifyFaces ()* che richiede al *servizio di riconoscimento delle facce* di identificare qualsiasi volto noto rilevato in precedenza nell'immagine inviata.</span><span class="sxs-lookup"><span data-stu-id="9a791-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="9a791-344">La richiesta restituirà un ID della persona identificata, ma non il nome:</span><span class="sxs-lookup"><span data-stu-id="9a791-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="9a791-345">Aggiungere il metodo *GetPerson ()* .</span><span class="sxs-lookup"><span data-stu-id="9a791-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="9a791-346">Se si specifica l'ID persona, questo metodo richiede al *servizio di riconoscimento delle facce* di restituire il nome della persona identificata:</span><span class="sxs-lookup"><span data-stu-id="9a791-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="9a791-347">Ricordarsi di **salvare** le modifiche prima di tornare all'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="9a791-348">Nell'editor di Unity trascinare lo script FaceAnalysis dalla cartella Scripts nel pannello del progetto all'oggetto fotocamera principale nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="9a791-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="9a791-349">Il nuovo componente script verrà aggiunto alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="9a791-349">The new script component will be so added to the Main Camera.</span></span> 

![Inserire FaceAnalysis nella fotocamera principale](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="9a791-351">Capitolo 7: creare la classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="9a791-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="9a791-352">Lo scopo della classe *ImageCapture* è di ospitare i metodi necessari per comunicare con il *servizio Azure Face Recognition* per analizzare l'immagine che verrà acquisita, identificando i visi al suo interno e determinando se appartiene a una persona nota.</span><span class="sxs-lookup"><span data-stu-id="9a791-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="9a791-353">Se viene trovata una persona nota, questa classe ne visualizzerà il nome come testo dell'interfaccia utente nella scena.</span><span class="sxs-lookup"><span data-stu-id="9a791-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="9a791-354">Per creare la classe *ImageCapture* :</span><span class="sxs-lookup"><span data-stu-id="9a791-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="9a791-355">Fare clic con il pulsante destro del mouse all'interno della cartella **script** creata in precedenza, quindi fare clic su **Crea**,  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="9a791-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="9a791-356">Chiamare lo script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="9a791-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="9a791-357">Fare doppio clic sul nuovo script *ImageCapture* per aprirlo con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9a791-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="9a791-358">Immettere gli spazi dei nomi seguenti sopra la classe ImageCapture:</span><span class="sxs-lookup"><span data-stu-id="9a791-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="9a791-359">All'interno della classe *ImageCapture* aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="9a791-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="9a791-360">Aggiungere i metodi *svegli ()* e *Start ()* necessari per inizializzare la classe e consentire al HoloLens di acquisire i movimenti dell'utente:</span><span class="sxs-lookup"><span data-stu-id="9a791-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="9a791-361">Aggiungere *TapHandler ()* che viene chiamato quando l'utente esegue un gesto *Tap* :</span><span class="sxs-lookup"><span data-stu-id="9a791-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="9a791-362">Aggiungere il metodo *ExecuteImageCaptureAndAnalysis ()* che inizierà il processo di acquisizione dell'immagine:</span><span class="sxs-lookup"><span data-stu-id="9a791-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="9a791-363">Aggiungere i gestori che vengono chiamati quando il processo di acquisizione foto è stato completato:</span><span class="sxs-lookup"><span data-stu-id="9a791-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="9a791-364">Ricordarsi di **salvare** le modifiche prima di tornare all'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="9a791-365">Capitolo 8-compilazione della soluzione</span><span class="sxs-lookup"><span data-stu-id="9a791-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="9a791-366">Per eseguire un test completo dell'applicazione, è necessario sideload nel HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9a791-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="9a791-367">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="9a791-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="9a791-368">Tutte le impostazioni indicate nel capitolo 3 sono impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="9a791-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="9a791-369">Lo script *FaceAnalysis* è associato all'oggetto principale della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="9a791-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="9a791-370">All'interno dello script *FaceAnalysis* sono stati impostati sia la **chiave di autenticazione** che l' **ID gruppo** .</span><span class="sxs-lookup"><span data-stu-id="9a791-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="9a791-371">A questo punto si è pronti per compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="9a791-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="9a791-372">Una volta compilata la soluzione, si sarà pronti per distribuire l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9a791-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="9a791-373">Per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="9a791-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="9a791-374">Salvare la scena corrente facendo clic su file, Salva.</span><span class="sxs-lookup"><span data-stu-id="9a791-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="9a791-375">Passare a file, impostazioni di compilazione, fare clic su Aggiungi scene aperte.</span><span class="sxs-lookup"><span data-stu-id="9a791-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="9a791-376">Verificare di aver selezionato i C# progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="9a791-376">Make sure to tick Unity C# Projects.</span></span>

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="9a791-378">Premere compila.</span><span class="sxs-lookup"><span data-stu-id="9a791-378">Press Build.</span></span> <span data-ttu-id="9a791-379">Quando si esegue questa operazione, Unity avvierà una finestra di Esplora file, in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="9a791-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="9a791-380">Creare la cartella adesso, all'interno del progetto Unity, e chiamarla app.</span><span class="sxs-lookup"><span data-stu-id="9a791-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="9a791-381">Quindi, con la cartella dell'app selezionata, fare clic su Seleziona cartella.</span><span class="sxs-lookup"><span data-stu-id="9a791-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="9a791-382">Unity inizierà a compilare il progetto, fino alla cartella dell'app.</span><span class="sxs-lookup"><span data-stu-id="9a791-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="9a791-383">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra Esplora file nel percorso della compilazione.</span><span class="sxs-lookup"><span data-stu-id="9a791-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="9a791-385">Aprire la cartella dell'app e quindi aprire la nuova soluzione del progetto (come illustrato in precedenza, MR_FaceRecognition. sln).</span><span class="sxs-lookup"><span data-stu-id="9a791-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="9a791-386">Capitolo 9-distribuzione dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="9a791-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="9a791-387">Per eseguire la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="9a791-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="9a791-388">È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="9a791-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="9a791-389">A tale scopo, effettua le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="9a791-389">To do this:</span></span>

    1. <span data-ttu-id="9a791-390">Quando si indossa il HoloLens, aprire le **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="9a791-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="9a791-391">Passare a **rete & Internet > opzioni avanzate Wi-Fi >**</span><span class="sxs-lookup"><span data-stu-id="9a791-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="9a791-392">Prendere nota dell'indirizzo **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="9a791-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="9a791-393">Quindi, tornare a **Settings (impostazioni**) e quindi **aggiornare & Security > per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="9a791-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="9a791-394">Impostare la modalità di sviluppo su.</span><span class="sxs-lookup"><span data-stu-id="9a791-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="9a791-395">Passare alla nuova compilazione Unity (cartella *app* ) e aprire il file della soluzione con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="9a791-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="9a791-396">Nella configurazione della soluzione selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="9a791-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="9a791-397">Nella piattaforma soluzione selezionare **x86**, **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="9a791-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="9a791-399">Passare al **menu Compila** e fare clic su **Distribuisci soluzione**per sideload l'applicazione in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9a791-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="9a791-400">L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="9a791-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="9a791-401">Per eseguire la distribuzione in un dispositivo headset immersivo, impostare la **piattaforma della soluzione** su *computer locale*e impostare la **configurazione** su *debug*, con *x86* come **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="9a791-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="9a791-402">Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*.</span><span class="sxs-lookup"><span data-stu-id="9a791-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="9a791-403">Capitolo 10-uso dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="9a791-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="9a791-404">Quando si usa il HoloLens, avviare l'app.</span><span class="sxs-lookup"><span data-stu-id="9a791-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="9a791-405">Esaminare la persona registrata con il *API viso*.</span><span class="sxs-lookup"><span data-stu-id="9a791-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="9a791-406">Verificare che:</span><span class="sxs-lookup"><span data-stu-id="9a791-406">Make sure that:</span></span>

    -  <span data-ttu-id="9a791-407">Il volto della persona non è troppo distante e chiaramente visibile</span><span class="sxs-lookup"><span data-stu-id="9a791-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="9a791-408">L'illuminazione dell'ambiente non è troppo scura</span><span class="sxs-lookup"><span data-stu-id="9a791-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="9a791-409">Usare il gesto Tap per acquisire l'immagine della persona.</span><span class="sxs-lookup"><span data-stu-id="9a791-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="9a791-410">Attendere l'invio della richiesta di analisi da parte dell'app e la ricezione di una risposta.</span><span class="sxs-lookup"><span data-stu-id="9a791-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="9a791-411">Se la persona è stata riconosciuta correttamente, il nome della persona verrà visualizzato come testo dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="9a791-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="9a791-412">È possibile ripetere il processo di acquisizione usando il gesto Tap a intervalli di pochi secondi.</span><span class="sxs-lookup"><span data-stu-id="9a791-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="9a791-413">Applicazione API Viso di Azure completa</span><span class="sxs-lookup"><span data-stu-id="9a791-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="9a791-414">Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio Azure Face Cognition per rilevare i visi in un'immagine e identificare eventuali visi noti.</span><span class="sxs-lookup"><span data-stu-id="9a791-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![risultato del completamento del corso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="9a791-416">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="9a791-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="9a791-417">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="9a791-417">Exercise 1</span></span>

<span data-ttu-id="9a791-418">Il **API viso di Azure** è sufficientemente potente da rilevare fino a 64 visi in un'unica immagine.</span><span class="sxs-lookup"><span data-stu-id="9a791-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="9a791-419">Estendere l'applicazione in modo che riconosca due o tre visi, tra le molte altre persone.</span><span class="sxs-lookup"><span data-stu-id="9a791-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="9a791-420">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="9a791-420">Exercise 2</span></span>

<span data-ttu-id="9a791-421">Il **API viso di Azure** è inoltre in grado di fornire tutti i tipi di informazioni sugli attributi.</span><span class="sxs-lookup"><span data-stu-id="9a791-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="9a791-422">Integrarlo nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9a791-422">Integrate this into the application.</span></span> <span data-ttu-id="9a791-423">Questo potrebbe essere ancora più interessante, se combinato con il [API emozioni](https://azure.microsoft.com/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="9a791-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/).</span></span>
