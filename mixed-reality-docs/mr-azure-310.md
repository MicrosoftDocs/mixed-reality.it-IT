---
title: MR e Azure 310-rilevamento di oggetti
description: Completare questo corso per apprendere come eseguire il training di un modello di apprendimento automatico e quindi usare il modello sottoposto a training per riconoscere oggetti simili e la relativa posizione nel mondo reale dall'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, visione personalizzata, rilevamento di oggetti, realtà mista, Accademia, Unity, esercitazione, API, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544413"
---
>[!NOTE]
><span data-ttu-id="7fd3c-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7fd3c-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7fd3c-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7fd3c-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7fd3c-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7fd3c-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="7fd3c-110">Mr e Azure 310: Rilevamento oggetti</span><span class="sxs-lookup"><span data-stu-id="7fd3c-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="7fd3c-111">In questo corso si apprenderà come riconoscere il contenuto visivo personalizzato e la relativa posizione spaziale all'interno di un'immagine fornita, usando le funzionalità di Azure Visione personalizzata "rilevamento oggetti" in un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="7fd3c-112">Questo servizio consentirà di eseguire il training di un modello di apprendimento automatico usando immagini oggetto.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="7fd3c-113">Si userà quindi il modello sottoposto a training per riconoscere oggetti simili e approssimarne la posizione nel mondo reale, come fornito dall'acquisizione della fotocamera di Microsoft HoloLens o da una fotocamera che si connette a un PC per auricolari immersivi (VR).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![risultato del corso](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="7fd3c-115">**Azure visione personalizzata, rilevamento oggetti** è un servizio Microsoft che consente agli sviluppatori di creare classificatori di immagini personalizzate.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="7fd3c-116">Questi classificatori possono quindi essere utilizzati con nuove immagini per rilevare gli oggetti all'interno di tale nuova immagine, fornendo **limiti di box** all'interno dell'immagine stessa.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="7fd3c-117">Il servizio fornisce un portale online semplice e facile da usare per semplificare questo processo.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="7fd3c-118">Per ulteriori informazioni, visitare i collegamenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="7fd3c-119">Pagina Visione personalizzata di Azure</span><span class="sxs-lookup"><span data-stu-id="7fd3c-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="7fd3c-120">Limiti e quote</span><span class="sxs-lookup"><span data-stu-id="7fd3c-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="7fd3c-121">Al termine di questo corso, sarà disponibile un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="7fd3c-122">L'utente sarà in grado di *osservare un* oggetto, di cui è stato eseguito il training tramite il servizio visione artificiale personalizzato di Azure e il rilevamento degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="7fd3c-123">L'utente userà il gesto *Tap* per acquisire un'immagine di ciò che sta esaminando.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="7fd3c-124">L'app invierà l'immagine alla Servizio visione artificiale personalizzato di Azure.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="7fd3c-125">Verrà restituita una risposta dal servizio che visualizzerà il risultato del riconoscimento come testo dello spazio globale.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="7fd3c-126">Questa operazione viene eseguita tramite l'uso del rilevamento spaziale di Microsoft HoloLens, per comprendere la posizione globale dell'oggetto riconosciuto e quindi usare il *tag* associato a quello rilevato nell'immagine, per fornire il testo dell'etichetta.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="7fd3c-127">Il corso illustra anche il caricamento manuale delle immagini, la creazione di tag e il training del servizio per riconoscere oggetti diversi (nell'esempio specificato, una Coppa), impostando la *casella limite* all'interno dell'immagine inviata.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="7fd3c-128">Dopo la creazione e l'uso dell'app, lo sviluppatore deve tornare al Servizio visione artificiale personalizzato di Azure e identificare le stime effettuate dal servizio e determinare se sono corrette o meno (tramite l'assegnazione di tag a qualsiasi elemento del servizio e regolazione dei *rettangoli*di delimitazione).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="7fd3c-129">Il servizio può quindi essere nuovamente sottoposto a training, che aumenterà la probabilità che riconosca gli oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="7fd3c-130">Questo corso spiegherà come ottenere i risultati dal Servizio visione artificiale personalizzato di Azure, il rilevamento degli oggetti, in un'applicazione di esempio basata su Unity.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="7fd3c-131">Sarà necessario applicare questi concetti a un'applicazione personalizzata che è possibile creare.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="7fd3c-132">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="7fd3c-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7fd3c-133">Corso</span><span class="sxs-lookup"><span data-stu-id="7fd3c-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7fd3c-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7fd3c-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7fd3c-135"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="7fd3c-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="7fd3c-136">MR e Azure 310: Rilevamento oggetti</span><span class="sxs-lookup"><span data-stu-id="7fd3c-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="7fd3c-137">✔️</span><span class="sxs-lookup"><span data-stu-id="7fd3c-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="7fd3c-138">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="7fd3c-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="7fd3c-139">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="7fd3c-140">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="7fd3c-141">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="7fd3c-142">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="7fd3c-143">Un computer di sviluppo</span><span class="sxs-lookup"><span data-stu-id="7fd3c-143">A development PC</span></span>
- [<span data-ttu-id="7fd3c-144">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="7fd3c-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="7fd3c-145">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="7fd3c-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="7fd3c-146">Unity 2017,4 LTS</span><span class="sxs-lookup"><span data-stu-id="7fd3c-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="7fd3c-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7fd3c-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="7fd3c-148">[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="7fd3c-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="7fd3c-149">Accesso a Internet per il programma di installazione di Azure e il recupero Servizio visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="7fd3c-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="7fd3c-150">È necessaria una serie di almeno quindici (15) immagini) per ogni oggetto che si desidera venga riconosciuto dal Visione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="7fd3c-151">Se lo si desidera, è possibile utilizzare le immagini già disponibili in questo corso, [una serie di CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="7fd3c-152">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="7fd3c-152">Before you start</span></span>

1.  <span data-ttu-id="7fd3c-153">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="7fd3c-154">Configurare e testare il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="7fd3c-155">Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="7fd3c-156">Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="7fd3c-157">Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="7fd3c-158">Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="7fd3c-159">Capitolo 1-portale di Visione personalizzata</span><span class="sxs-lookup"><span data-stu-id="7fd3c-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="7fd3c-160">Per usare il **servizio visione artificiale personalizzato di Azure**, è necessario configurare un'istanza di tale istanza per renderla disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="7fd3c-161">Passare [alla pagina principale **servizio visione artificiale personalizzato** ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="7fd3c-162">Fare clic su **Introduzione**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="7fd3c-163">Accedere al portale di Visione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="7fd3c-164">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="7fd3c-165">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="7fd3c-166">Una volta effettuato l'accesso per la prima volta, verrà visualizzato il pannello *condizioni del servizio* .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="7fd3c-167">Fare clic sulla casella di controllo per *accettare le condizioni*.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="7fd3c-168">Quindi fare **clic**su Accetto.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="7fd3c-169">Accettando le condizioni, si è ora nella sezione *progetti personali* .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="7fd3c-170">Fare clic su **nuovo progetto**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="7fd3c-171">Verrà visualizzata una scheda sul lato destro, che richiederà di specificare alcuni campi per il progetto.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="7fd3c-172">Inserire un nome per il progetto</span><span class="sxs-lookup"><span data-stu-id="7fd3c-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="7fd3c-173">Inserire una descrizione per il progetto (**facoltativo**)</span><span class="sxs-lookup"><span data-stu-id="7fd3c-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="7fd3c-174">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7fd3c-175">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="7fd3c-176">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="7fd3c-177">Per [altre informazioni sui gruppi di risorse di Azure, passare alla documentazione associata](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="7fd3c-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="7fd3c-178">Impostare i **tipi di progetto** come **rilevamento oggetti (anteprima)** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="7fd3c-179">Al termine, fare clic su **Crea progetto**e si verrà reindirizzati alla pagina servizio visione artificiale personalizzato progetto.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="7fd3c-180">Capitolo 2-training del progetto di Visione personalizzata</span><span class="sxs-lookup"><span data-stu-id="7fd3c-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="7fd3c-181">Una volta nel portale di Visione personalizzata, l'obiettivo principale è quello di eseguire il training del progetto per riconoscere oggetti specifici nelle immagini.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="7fd3c-182">Sono necessarie almeno 15 immagini per ogni oggetto che si desidera che l'applicazione riconosca.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="7fd3c-183">È possibile usare le immagini fornite con questo corso ([una serie di CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="7fd3c-184">Per eseguire il training del progetto Visione personalizzata:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="7fd3c-185">Fare clic sul **+** pulsante accanto ai **tag**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="7fd3c-186">Aggiungere un **nome** per il tag che verrà usato per associare le immagini a.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="7fd3c-187">In questo esempio vengono utilizzate immagini di CUPS per il riconoscimento, quindi è stato denominato il tag per questo, **Cup**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="7fd3c-188">Al termine, fare clic su **Salva** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="7fd3c-189">Si noterà che il **tag** è stato aggiunto. potrebbe essere necessario ricaricare la pagina affinché venga visualizzata.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="7fd3c-190">Fare clic su **Aggiungi immagini** al centro della pagina.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="7fd3c-191">Fare clic su **Sfoglia file locali**e selezionare le immagini che si desidera caricare per un oggetto, con un minimo di quindici (15).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="7fd3c-192">È possibile selezionare più immagini alla volta per caricare.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="7fd3c-193">Quando si selezionano tutte le immagini con cui si vuole eseguire il training del progetto, fare clic su **Carica file** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="7fd3c-194">Il caricamento dei file inizierà.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-194">The files will begin uploading.</span></span> <span data-ttu-id="7fd3c-195">Dopo aver conferma del caricamento, fare **clic** su</span><span class="sxs-lookup"><span data-stu-id="7fd3c-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="7fd3c-196">A questo punto le immagini vengono caricate, ma non contrassegnate.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="7fd3c-197">Per contrassegnare le immagini, usare il mouse.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="7fd3c-198">Quando si passa il mouse sull'immagine, un'evidenziazione della selezione consente di disegnare automaticamente una selezione intorno all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="7fd3c-199">Se non è accurato, è possibile creare un proprio.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="7fd3c-200">Questa operazione viene eseguita tenendo premuto il pulsante sinistro del mouse e trascinando l'area di selezione per includere l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="7fd3c-201">Dopo la selezione dell'oggetto all'interno dell'immagine, verrà richiesto di *aggiungere un tag Region*.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="7fd3c-202">Selezionare il tag creato in precedenza (' Cup ' nell'esempio precedente) oppure, se si aggiungono altri tag, digitarlo in e fare clic sul pulsante **+ (segno più)** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="7fd3c-203">Per contrassegnare l'immagine successiva, è possibile fare clic sulla freccia a destra del pannello oppure chiudere il pannello Tag facendo clic sulla **X** nell'angolo superiore destro del pannello, quindi fare clic sull'immagine successiva.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="7fd3c-204">Una volta preparata l'immagine successiva, ripetere la stessa procedura.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="7fd3c-205">Eseguire questa operazione per tutte le immagini caricate fino a quando non vengono contrassegnate tutte con tag.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="7fd3c-206">È possibile selezionare più oggetti nella stessa immagine, come nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="7fd3c-207">Una volta contrassegnati tutti, fare clic sul pulsante **con tag** , a sinistra della schermata, per visualizzare le immagini con tag.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="7fd3c-208">A questo punto è possibile eseguire il training del servizio.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-208">You are now ready to train your Service.</span></span> <span data-ttu-id="7fd3c-209">Fare clic sul pulsante **Train (Train** ) per avviare la prima iterazione di training.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="7fd3c-210">Una volta compilato, sarà possibile visualizzare due pulsanti denominati **Make default** and prediction **URL**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="7fd3c-211">Fare clic su **Imposta come predefinito** per primo, quindi fare clic su **URL stima**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="7fd3c-212">L'endpoint fornito da questo oggetto è impostato su qualsiasi iterazione  contrassegnata come predefinita.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="7fd3c-213">Di conseguenza, se in un secondo momento si  crea una nuova iterazione e la si aggiorna come predefinita, non sarà necessario modificare il codice.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="7fd3c-214">Dopo aver fatto clic su **URL di stima**, aprire il *blocco note*e copiare e incollare l' **URL** (detto anche endpoint di **stima**) e la chiave di **stima del servizio**, in modo da poterlo recuperare quando necessario in un secondo momento nel codice.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="7fd3c-215">Capitolo 3: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="7fd3c-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="7fd3c-216">Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="7fd3c-217">Aprire **Unity** e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="7fd3c-218">A questo punto sarà necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="7fd3c-219">Inserire **CustomVisionObjDetection**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="7fd3c-220">Verificare che il tipo di progetto sia impostato su **3D**e impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="7fd3c-221">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="7fd3c-222">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="7fd3c-223">Passare a **modifica* > *Preferenze** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="7fd3c-224">Modificare l' **editor di script esterno** in **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="7fd3c-225">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="7fd3c-226">Passare quindi a **File > impostazioni di compilazione** e impostare la **piattaforma** su *piattaforma UWP (Universal Windows Platform)* , quindi fare clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="7fd3c-227">Nella stessa finestra **impostazioni di compilazione** verificare che siano impostati i seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="7fd3c-228">Il **dispositivo di destinazione** è impostato su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="7fd3c-229">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="7fd3c-230">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="7fd3c-231">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="7fd3c-232">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="7fd3c-233">Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="7fd3c-234">Nella stessa finestra **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="7fd3c-235">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="7fd3c-236">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="7fd3c-237">La **versione di runtime** di scripting deve essere **sperimentale** (equivalente a .NET 4,6), che attiverà la necessità di riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="7fd3c-238">Il **back-end** di scripting deve essere **.NET**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="7fd3c-239">Il **livello di compatibilità API** deve essere **.NET 4,6**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="7fd3c-240">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="7fd3c-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="7fd3c-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-242">**Webcam**</span></span>

        3. <span data-ttu-id="7fd3c-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-243">**SpatialPerception**</span></span>

            <span data-ttu-id="7fd3c-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="7fd3c-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="7fd3c-245">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, quindi assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="7fd3c-246">Nelle **impostazioni di compilazione**, i *progetti\# Unity C* non sono più in grigio: selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="7fd3c-247">Chiudere la finestra **impostazioni di compilazione** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="7fd3c-248">Nell' **Editor**fare clic su **modifica** > **Impostazioni** > progetto**grafica**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="7fd3c-249">Nel **pannello Inspector** verranno aperte le *impostazioni grafiche* .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="7fd3c-250">Scorrere verso il basso fino a quando non viene visualizzata una matrice denominata **Includi sempre gli shader**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="7fd3c-251">Aggiungere uno slot aumentando la variabile di **dimensione** di uno (in questo esempio, è stato 8, quindi è stato creato 9).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="7fd3c-252">Verrà visualizzato un nuovo slot nell'ultima posizione della matrice, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="7fd3c-253">Nello slot fare clic sul cerchio di destinazione piccolo accanto allo slot per aprire un elenco di shader.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="7fd3c-254">Cercare il Legacy shaders **/Transparent/Diffusion** shader e fare doppio clic su di esso.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="7fd3c-255">Capitolo 4-importazione del pacchetto CustomVisionObjDetection Unity</span><span class="sxs-lookup"><span data-stu-id="7fd3c-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="7fd3c-256">Per questo corso viene fornito un pacchetto di asset Unity denominato **Azure-Mr-310. file unitypackage Tools**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="7fd3c-257">Punta Tutti gli oggetti supportati da Unity, incluse le intere scene, possono essere inseriti in un file con **estensione file unitypackage Tools** e esportati o importati in altri progetti.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="7fd3c-258">Si tratta del modo più sicuro e più efficiente per spostare le risorse tra diversi **progetti Unity**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="7fd3c-259">È possibile trovare il [pacchetto Azure-Mr-310 che è necessario scaricare qui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="7fd3c-260">Con il dashboard Unity, fare clic su **Asset** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto > pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="7fd3c-261">Usare il selettore file per selezionare il pacchetto **Azure-Mr-310. file unitypackage Tools** e fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="7fd3c-262">Verrà visualizzato un elenco di componenti per questo asset.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="7fd3c-263">Confermare l'importazione facendo clic sul pulsante **Importa** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="7fd3c-264">Una volta completata l'importazione, si noterà che le cartelle del pacchetto sono state aggiunte alla cartella assets  .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="7fd3c-265">Questo tipo di struttura di cartelle è tipico per un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="7fd3c-266">La  cartella Materials contiene il materiale utilizzato dal **cursore sguardo**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="7fd3c-267">La  cartella plugins contiene la dll Newtonsoft usata dal codice per deserializzare la risposta Web del servizio.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="7fd3c-268">Le due (2) versioni diverse contenute nella cartella e nella sottocartella sono necessarie per consentire l'uso e la compilazione della libreria sia dall'editor di Unity che dalla compilazione UWP.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="7fd3c-269">La  cartella prefabbricates contiene le prefabbricati contenute nella scena.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="7fd3c-270">Sono:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-270">Those are:</span></span>

        1.  <span data-ttu-id="7fd3c-271">**GazeCursor**, il cursore utilizzato nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="7fd3c-272">Collaborerà con la prefabbricata SpatialMapping per poter essere posizionata nella scena sopra gli oggetti fisici.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="7fd3c-273">**Etichetta**, ovvero l'oggetto dell'interfaccia utente usato per visualizzare il tag oggetto nella scena quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="7fd3c-274">**SpatialMapping**, che è l'oggetto che consente all'applicazione di usare la creazione di una mappa virtuale usando il rilevamento spaziale di Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="7fd3c-275">La cartella **Scenes** che attualmente contiene la scena predefinita per questo corso.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="7fd3c-276">Aprire la cartella **Scenes** , nel **Pannello Project**e fare doppio clic su **ObjDetectionScene**per caricare la scena che verrà usata per questo corso.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="7fd3c-277">**Non è incluso alcun codice**, il codice verrà scritto seguendo questo corso.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="7fd3c-278">Capitolo 5: creare la classe CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="7fd3c-279">A questo punto si è pronti per scrivere il codice.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="7fd3c-280">Si inizierà con la classe **CustomVisionAnalyser** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="7fd3c-281">Le chiamate al **servizio visione artificiale personalizzato**, effettuate nel codice riportato di seguito, vengono effettuate usando l' **API REST di visione personalizzata**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="7fd3c-282">Con l'uso di questa API, si vedrà come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="7fd3c-283">Tenere presente che Microsoft offre un **visione personalizzata SDK** che può essere usato anche per effettuare chiamate al servizio.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="7fd3c-284">Per altre informazioni, vedere l' [articolo visione personalizzata SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="7fd3c-285">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-285">This class is responsible for:</span></span>

- <span data-ttu-id="7fd3c-286">Caricamento dell'immagine più recente acquisita come matrice di byte.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="7fd3c-287">Invio della matrice di byte all'istanza di Azure **servizio visione artificiale personalizzato** per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="7fd3c-288">Ricezione della risposta come stringa JSON.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="7fd3c-289">Deserializzare la risposta e passare la **stima** risultante alla classe **SceneOrganiser** , che si occuperà della modalità di visualizzazione della risposta.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="7fd3c-290">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-290">To create this class:</span></span>

1.  <span data-ttu-id="7fd3c-291">Fare clic con il pulsante destro del mouse nella **cartella Asset**, che si trova nel **pannello progetto**, quindi fare clic su **Crea** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="7fd3c-292">Chiamare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="7fd3c-293">Fare doppio clic sulla cartella appena creata per aprirla.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="7fd3c-294">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi scegliere **Crea** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7fd3c-295">Denominare lo script **CustomVisionAnalyser.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="7fd3c-296">Fare doppio clic sul nuovo script **CustomVisionAnalyser** per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="7fd3c-297">Verificare che siano presenti gli spazi dei nomi seguenti a cui si fa riferimento all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="7fd3c-298">Nella classe **CustomVisionAnalyser** aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="7fd3c-299">Assicurarsi di inserire la **chiave di stima del servizio** nella variabile **PredictionKey** e l'endpoint di **stima** nella variabile **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="7fd3c-300">Questi sono stati copiati [nel blocco note in precedenza, nel capitolo 2, passaggio 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="7fd3c-301">Per inizializzare la variabile di istanza, è necessario aggiungere il codice per il punto di riattivazione **()** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="7fd3c-302">Aggiungere la coroutine (con il metodo statico **GetImageAsByteArray ()** sottostante), che otterrà i risultati dell'analisi dell'immagine, acquisita dalla classe **ImageCapture** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7fd3c-303">Nella coroutine di **AnalyseImageCapture** è presente una chiamata alla classe **SceneOrganiser** che è ancora necessario creare.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="7fd3c-304">Lasciare quindi **le righe impostate come commento per il momento**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. <span data-ttu-id="7fd3c-305">Eliminare i metodi **Start ()** e **Update ()** perché non verranno usati.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="7fd3c-306">Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7fd3c-307">Come indicato in precedenza, non è necessario preoccuparsi del codice che potrebbe sembrare un errore, in quanto le altre classi saranno presto disponibili, che verranno risolte.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="7fd3c-308">Capitolo 6: creare la classe CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="7fd3c-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="7fd3c-309">La classe che verrà creata ora è la classe **CustomVisionObjects** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="7fd3c-310">Questo script contiene una serie di oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate all'Servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="7fd3c-311">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-311">To create this class:</span></span>

1.  <span data-ttu-id="7fd3c-312">Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7fd3c-313">Chiamare lo script **CustomVisionObjects.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="7fd3c-314">Fare doppio clic sul nuovo script **CustomVisionObjects** per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="7fd3c-315">Verificare che siano presenti gli spazi dei nomi seguenti a cui si fa riferimento all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="7fd3c-316">Eliminare i metodi **Start ()** e **Update ()** all'interno della classe **CustomVisionObjects** . questa classe ora dovrebbe essere vuota.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="7fd3c-317">È importante seguire con attenzione l'istruzione successiva.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="7fd3c-318">Se si inseriscono le nuove dichiarazioni di classe all'interno della classe **CustomVisionObjects** , si otterranno errori di compilazione nel [capitolo 10](#chapter-10---create-the-imagecapture-class), indicando che **AnalysisRootObject** e **BoundingBox** non sono stati trovati.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="7fd3c-319">Aggiungere le classi seguenti al di *fuori* della classe **CustomVisionObjects** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="7fd3c-320">Questi oggetti vengono usati dalla libreria **Newtonsoft** per serializzare e deserializzare i dati di risposta:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="7fd3c-321">Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="7fd3c-322">Capitolo 7: creare la classe SpatialMapping</span><span class="sxs-lookup"><span data-stu-id="7fd3c-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="7fd3c-323">Questa classe imposterà il **conflitto di mapping spaziale** nella scena in modo da essere in grado di rilevare conflitti tra oggetti virtuali e oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="7fd3c-324">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-324">To create this class:</span></span>

1.  <span data-ttu-id="7fd3c-325">Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7fd3c-326">Chiamare lo script **SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="7fd3c-327">Fare doppio clic sul nuovo script **SpatialMapping** per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="7fd3c-328">Verificare che siano presenti gli spazi dei nomi seguenti a cui si fa riferimento sopra la classe **SpatialMapping** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="7fd3c-329">Aggiungere quindi le variabili seguenti all'interno della classe **SpatialMapping** , sopra il metodo **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="7fd3c-330">Aggiungere i **risvegli ()** e **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="7fd3c-331">Eliminare il metodo **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="7fd3c-332">Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="7fd3c-333">Capitolo 8: creare la classe GazeCursor</span><span class="sxs-lookup"><span data-stu-id="7fd3c-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="7fd3c-334">Questa classe è responsabile della configurazione del cursore nella posizione corretta nello spazio reale, mediante l'utilizzo di **SpatialMappingCollider**, creato nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="7fd3c-335">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-335">To create this class:</span></span>

1.  <span data-ttu-id="7fd3c-336">Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7fd3c-337">Chiamare lo script **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="7fd3c-338">Fare doppio clic sul nuovo script **GazeCursor** per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="7fd3c-339">Verificare che sia presente lo spazio dei nomi seguente a cui si fa riferimento sopra la classe **GazeCursor** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="7fd3c-340">Aggiungere quindi la variabile seguente all'interno della classe **GazeCursor** , sopra il metodo **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="7fd3c-341">Aggiornare il metodo **Start ()** con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="7fd3c-342">Aggiornare il metodo **Update ()** con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="7fd3c-343">Non preoccuparsi dell'errore per la classe **SceneOrganiser** non trovata, che verrà creata nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="7fd3c-344">Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="7fd3c-345">Capitolo 9: creare la classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="7fd3c-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="7fd3c-346">Questa classe:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-346">This class will:</span></span>

-   <span data-ttu-id="7fd3c-347">Configurare la *fotocamera principale* collegando i componenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="7fd3c-348">Quando viene rilevato un oggetto, questo sarà responsabile per il calcolo della posizione nel mondo reale e per inserire un' **etichetta tag** accanto al **nome del tag**appropriato.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="7fd3c-349">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-349">To create this class:</span></span>

1.  <span data-ttu-id="7fd3c-350">Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7fd3c-351">Denominare lo script **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="7fd3c-352">Fare doppio clic sul nuovo script **SceneOrganiser** per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="7fd3c-353">Verificare che siano presenti gli spazi dei nomi seguenti a cui si fa riferimento sopra la classe **SceneOrganiser** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="7fd3c-354">Aggiungere quindi le variabili seguenti all'interno della classe **SceneOrganiser** , sopra il metodo **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="7fd3c-355">Eliminare i metodi **Start ()** e **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="7fd3c-356">Sotto le variabili aggiungere il metodo **sveglie ()** che inizializza la classe e imposta la scena.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="7fd3c-357">Aggiungere il metodo **PlaceAnalysisLabel ()** che creerà *un'istanza* dell'etichetta nella scena, che a questo punto non è visibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="7fd3c-358">Inserisce anche il quad (anche invisibile) in cui si trova l'immagine e si sovrappone al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="7fd3c-359">Questo è importante perché le coordinate della casella recuperate dal servizio dopo l'analisi vengono riportate in questo quad per determinare la posizione approssimativa dell'oggetto nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="7fd3c-360">Aggiungere il metodo **FinaliseLabel ()** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="7fd3c-361">È responsabile di:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-361">It is responsible for:</span></span>

    *   <span data-ttu-id="7fd3c-362">Impostazione del testo dell' *etichetta* con il *tag* della stima con la massima confidenza.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="7fd3c-363">Chiamata del calcolo del rettangolo  di delimitazione dell'oggetto Quad, posizionato in precedenza e posizionamento dell'etichetta nella scena.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="7fd3c-364">Regolazione della profondità dell'etichetta usando un Raycast verso il rettangolo di delimitazione, che deve essere in conflitto con l'oggetto nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="7fd3c-365">Reimpostazione del processo di acquisizione per consentire all'utente di acquisire un'altra immagine.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="7fd3c-366">Aggiungere il metodo **CalculateBoundingBoxPosition ()** che ospita una serie di calcoli necessari per tradurre le coordinate  del rettangolo di delimitazione recuperate dal servizio e ricrearle proporzionalmente sul quad.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="7fd3c-367">Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7fd3c-368">Prima di continuare, aprire la classe **CustomVisionAnalyser** e, all'interno del metodo **AnalyseLastImageCaptured ()** , *rimuovere il commento* dalle righe seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="7fd3c-369">Non preoccuparsi del messaggio "Impossibile trovare la classe **ImageCapture** ", che verrà creata nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="7fd3c-370">Capitolo 10: creare la classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="7fd3c-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="7fd3c-371">La classe successiva che si intende creare è la classe **ImageCapture** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="7fd3c-372">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-372">This class is responsible for:</span></span>

*   <span data-ttu-id="7fd3c-373">Acquisizione di un'immagine con la fotocamera HoloLens e relativa archiviazione nella cartella dell' *app* .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="7fd3c-374">Gestione dei movimenti *Tap* dall'utente.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="7fd3c-375">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-375">To create this class:</span></span>

1.  <span data-ttu-id="7fd3c-376">Passare alla cartella **Scripts** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="7fd3c-377">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi scegliere **Crea** > **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7fd3c-378">Denominare lo script **ImageCapture**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="7fd3c-379">Fare doppio clic sul nuovo script **ImageCapture** per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="7fd3c-380">Sostituire gli spazi dei nomi all'inizio del file con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="7fd3c-381">Aggiungere quindi le variabili seguenti all'interno della classe **ImageCapture** , sopra il metodo **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="7fd3c-382">È ora necessario aggiungere il codice per i metodi **svegli ()** e **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="7fd3c-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="7fd3c-383">Implementare un gestore che verrà chiamato quando si verifica un movimento TAP:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="7fd3c-384">Quando il cursore è **verde**, significa che la fotocamera è disponibile per l'immagine.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="7fd3c-385">Quando il cursore è **rosso**, significa che la fotocamera è occupata.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="7fd3c-386">Aggiungere il metodo usato dall'applicazione per avviare il processo di acquisizione dell'immagine e archiviare l'immagine:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  <span data-ttu-id="7fd3c-387">Aggiungere i gestori che verranno chiamati quando la foto è stata acquisita e quando è pronta per essere analizzata.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="7fd3c-388">Il risultato viene quindi passato a **CustomVisionAnalyser** per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="7fd3c-389">Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="7fd3c-390">Capitolo 11-Configurazione degli script nella scena</span><span class="sxs-lookup"><span data-stu-id="7fd3c-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="7fd3c-391">Ora che è stato scritto tutto il codice necessario per questo progetto, è il momento di configurare gli script nella scena e sui prefabbricati per comportarsi correttamente.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="7fd3c-392">Nell' **Editor**di Unity selezionare la **fotocamera principale**nel **Pannello gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="7fd3c-393">Nel **pannello Inspector**, con la **fotocamera principale** selezionata, fare clic su **Add Component**, quindi cercare lo script **SceneOrganiser** e fare doppio clic su per aggiungerlo.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="7fd3c-394">Nel **Pannello del progetto**aprire la cartella prefabbricati, trascinare l' **etichetta** prefabbricato nell'area di input di destinazione di riferimento vuota dell' *etichetta* , nello script **SceneOrganiser** appena aggiunto alla *fotocamera principale*, come illustrato in  l'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="7fd3c-395">Nel **Pannello gerarchia**selezionare l'elemento figlio **GazeCursor** della **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="7fd3c-396">Nel **pannello Inspector**, con **GazeCursor** selezionato, fare clic su **Add Component**, quindi cercare **GazeCursor** script e fare doppio clic su per aggiungerlo.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="7fd3c-397">Anche in questo caso, nel **Pannello gerarchia**selezionare l'elemento figlio **SpatialMapping** della **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="7fd3c-398">Nel **pannello Inspector**, con **SpatialMapping** selezionato, fare clic su **Add Component**, quindi cercare **SpatialMapping** script e fare doppio clic su per aggiungerlo.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="7fd3c-399">Gli script rimanenti non impostati verranno aggiunti dal codice nello script **SceneOrganiser** , durante la fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="7fd3c-400">Capitolo 12-prima della compilazione</span><span class="sxs-lookup"><span data-stu-id="7fd3c-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="7fd3c-401">Per eseguire un test completo dell'applicazione, è necessario sideload in Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="7fd3c-402">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="7fd3c-403">Tutte le impostazioni indicate nel [capitolo 3](#chapter-3---set-up-the-unity-project) sono impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="7fd3c-404">Lo script **SceneOrganiser** è associato all'oggetto **principale della fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="7fd3c-405">Lo script **GazeCursor** è associato all'oggetto **GazeCursor** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="7fd3c-406">Lo script **SpatialMapping** è associato all'oggetto **SpatialMapping** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="7fd3c-407">Nel [capitolo 5](#chapter-5---create-the-customvisionanalyser-class), passaggio 6:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="7fd3c-408">Assicurarsi di inserire la **chiave di stima del servizio** nella variabile **predictionKey** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="7fd3c-409">L' **endpoint di stima** è stato inserito nella classe **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="7fd3c-410">Capitolo 13: compilare la soluzione UWP e sideload l'applicazione</span><span class="sxs-lookup"><span data-stu-id="7fd3c-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="7fd3c-411">A questo punto si è pronti per compilare l'applicazione come soluzione UWP che sarà possibile distribuire in Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="7fd3c-412">Per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-412">To begin the build process:</span></span>

1.  <span data-ttu-id="7fd3c-413">Passare a **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="7fd3c-414">Seleziona i **progetti\# Unity C**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="7fd3c-415">Fare clic su **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="7fd3c-416">Verrà aggiunta la scena attualmente aperta alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="7fd3c-417">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-417">Click **Build**.</span></span> <span data-ttu-id="7fd3c-418">Unity avvierà una finestra di *Esplora file* , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="7fd3c-419">Creare la cartella adesso e denominarla **app**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="7fd3c-420">Quindi, con la cartella dell' **app** selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="7fd3c-421">Unity inizierà a compilare il progetto nella cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="7fd3c-422">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="7fd3c-423">Per eseguire la distribuzione in Microsoft HoloLens, è necessario l'indirizzo IP del dispositivo (per la distribuzione remota) e per assicurarsi che abbia anche la **modalità di sviluppo** impostata.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="7fd3c-424">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-424">To do this:</span></span>

    1.  <span data-ttu-id="7fd3c-425">Quando si indossa il HoloLens, aprire le **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="7fd3c-426">Passa a **rete &**  > **Opzioni avanzate** **Wi-Fi** > Internet</span><span class="sxs-lookup"><span data-stu-id="7fd3c-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="7fd3c-427">Prendere nota dell'indirizzo **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="7fd3c-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="7fd3c-428">Tornare quindi a Settings ( **Impostazioni**) e quindi **aggiornare & Security** > **per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="7fd3c-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="7fd3c-429">Impostare la **modalità di sviluppo** *su*.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="7fd3c-430">Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="7fd3c-431">Nella configurazione della soluzione selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="7fd3c-432">Nella piattaforma soluzione selezionare **x86, computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="7fd3c-433">Verrà richiesto di inserire l' **indirizzo IP** di un dispositivo remoto (Microsoft HoloLens, in questo caso, annotato).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="7fd3c-434">Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="7fd3c-435">L'app verrà ora visualizzata nell'elenco delle app installate in Microsoft HoloLens, pronto per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="7fd3c-436">Per utilizzare l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="7fd3c-436">To use the application:</span></span>

* <span data-ttu-id="7fd3c-437">Esaminare un oggetto, che è stato sottoposto a training con la **servizio visione artificiale personalizzato di Azure, il rilevamento degli oggetti**e usare il **gesto Tap**.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="7fd3c-438">Se l'oggetto viene rilevato correttamente, verrà visualizzato un *testo dell'etichetta* con spazio globale con il nome del tag.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7fd3c-439">Ogni volta che si acquisisce una foto e la si invia al servizio, è possibile tornare alla pagina del servizio e ripetere il training del servizio con le immagini appena acquisite.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="7fd3c-440">All'inizio, probabilmente sarà anche necessario correggere i *riquadri* delimitativi in modo da essere più accurati e ripetere il training del servizio.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="7fd3c-441">Il testo dell'etichetta inserito potrebbe non essere visualizzato vicino all'oggetto quando i sensori Microsoft HoloLens e/o SpatialTrackingComponent in Unity non riescono a collocare i Collider appropriati, relativi agli oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="7fd3c-442">Se questo è il caso, provare a usare l'applicazione in un'area diversa.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="7fd3c-443">Applicazione di rilevamento oggetti Visione personalizzata</span><span class="sxs-lookup"><span data-stu-id="7fd3c-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="7fd3c-444">Congratulazioni, è stata creata un'app per realtà mista che sfrutta il Visione personalizzata di Azure, l'API di rilevamento oggetti, che può riconoscere un oggetto da un'immagine, quindi fornire una posizione approssimativa per tale oggetto nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7fd3c-445">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="7fd3c-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7fd3c-446">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="7fd3c-446">Exercise 1</span></span>

<span data-ttu-id="7fd3c-447">Aggiungendo all'etichetta di testo, utilizzare un cubo semi-trasparente per eseguire il wrapping dell'oggetto reale in un rettangolo di delimitazione 3D.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="7fd3c-448">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="7fd3c-448">Exercise 2</span></span>

<span data-ttu-id="7fd3c-449">Eseguire il training del Servizio visione artificiale personalizzato per riconoscere più oggetti.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="7fd3c-450">Esercizio 3</span><span class="sxs-lookup"><span data-stu-id="7fd3c-450">Exercise 3</span></span>

<span data-ttu-id="7fd3c-451">Riprodurre un suono quando viene riconosciuto un oggetto.</span><span class="sxs-lookup"><span data-stu-id="7fd3c-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="7fd3c-452">Esercizio 4</span><span class="sxs-lookup"><span data-stu-id="7fd3c-452">Exercise 4</span></span>

<span data-ttu-id="7fd3c-453">Usare l'API per eseguire nuovamente il training del servizio con le stesse immagini analizzate dall'app, in modo da rendere più accurato il servizio (eseguire contemporaneamente la stima e la formazione).</span><span class="sxs-lookup"><span data-stu-id="7fd3c-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
