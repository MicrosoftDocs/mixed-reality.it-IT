---
title: MR e 310 Azure - rilevamento di oggetti
description: Completare questo corso per informazioni su come eseguire il training di un modello di machine learning e quindi usare il modello con training per riconoscere gli oggetti simili e la posizione nel mondo reale dall'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, servizio visione artificiale personalizzato, dell'oggetto rilevamento, mista realtà, academy, unity, esercitazione, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597652"
---
>[!NOTE]
><span data-ttu-id="d229d-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="d229d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d229d-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="d229d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d229d-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="d229d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d229d-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="d229d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d229d-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d229d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d229d-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="d229d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="d229d-110">MR e Azure 310: Rilevamento di oggetti</span><span class="sxs-lookup"><span data-stu-id="d229d-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="d229d-111">In questo corso, si apprenderà come riconoscere contenuto visivo personalizzato e la sua posizione spaziale all'interno di un'immagine fornita, visione artificiale personalizzato di Azure usando le funzionalità di "Rilevamento di oggetti" in un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d229d-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="d229d-112">Questo servizio consentirà di eseguire il training di un modello di machine learning usando immagini di oggetto.</span><span class="sxs-lookup"><span data-stu-id="d229d-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="d229d-113">Si utilizzerà quindi il modello con training per riconoscere gli oggetti simili e approssimare la relativa posizione nel mondo reale, come specificato dall'acquisizione della fotocamera del Microsoft HoloLens o una videocamera di connettersi a un PC per immersive auricolari (VR).</span><span class="sxs-lookup"><span data-stu-id="d229d-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![risultato del corso](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="d229d-115">**Visione artificiale personalizzato di Azure, rilevamento di oggetti** è un Service Microsoft che consente agli sviluppatori di compilare classificatori di immagini personalizzate.</span><span class="sxs-lookup"><span data-stu-id="d229d-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="d229d-116">Questi due classificatori sono quindi utilizzabile con le immagini nuove per rilevare gli oggetti all'interno di tale immagine nuova, fornendo **limiti di finestra** all'interno dell'immagine stessa.</span><span class="sxs-lookup"><span data-stu-id="d229d-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="d229d-117">Il servizio offre un portale semplice, facile da usare, in linea per semplificare questo processo.</span><span class="sxs-lookup"><span data-stu-id="d229d-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="d229d-118">Per altre informazioni, visitare i collegamenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d229d-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="d229d-119">Pagina di visione artificiale personalizzato di Azure</span><span class="sxs-lookup"><span data-stu-id="d229d-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="d229d-120">Limiti e quote</span><span class="sxs-lookup"><span data-stu-id="d229d-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="d229d-121">Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d229d-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="d229d-122">L'utente sarà in grado *estasiati* in un oggetto che si è sottoposti a training usando il servizio di visione artificiale personalizzato di Azure, rilevamento di oggetti.</span><span class="sxs-lookup"><span data-stu-id="d229d-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="d229d-123">L'utente userà il *toccare* movimento per acquisire un'immagine di ciò che si sta esaminando.</span><span class="sxs-lookup"><span data-stu-id="d229d-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="d229d-124">L'app invia l'immagine per il servizio visione artificiale personalizzato di Azure.</span><span class="sxs-lookup"><span data-stu-id="d229d-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="d229d-125">Sarà presente una risposta dal servizio che verrà visualizzato il risultato del riconoscimento come testo spazio globale.</span><span class="sxs-lookup"><span data-stu-id="d229d-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="d229d-126">A tale scopo tramite l'utilizzo spaziale di rilevamento degli Microsoft HoloLens, allo scopo di comprendere la posizione globale dell'oggetto riconosciuta e quindi usando il *Tag* associata a ciò che viene rilevato nell'immagine, a fornire il testo dell'etichetta.</span><span class="sxs-lookup"><span data-stu-id="d229d-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="d229d-127">Il corso si occuperà anche caricare manualmente le immagini, la creazione di tag, e il servizio, per riconoscere diversi training oggetti (nell'esempio fornito una tazza), da impostando il *limite casella* all'interno dell'immagine è inviare.</span><span class="sxs-lookup"><span data-stu-id="d229d-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="d229d-128">Dopo la creazione e uso dell'app, lo sviluppatore deve passare al servizio visione artificiale personalizzato, Azure e identificare le stime eseguite dal servizio e verificare se è corretti o non (tramite l'assegnazione di tag alcuna operazione del servizio mancante, e modificando la *riquadri*).</span><span class="sxs-lookup"><span data-stu-id="d229d-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="d229d-129">Il servizio può quindi eseguire nuovamente il training, che aumenta il livello di probabilità di riconoscere gli oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="d229d-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="d229d-130">Questo corso ti spiegherà come ottenere i risultati dal servizio visione artificiale personalizzato di Azure, il rilevamento di oggetti, in un'applicazione di esempio basate su Unity.</span><span class="sxs-lookup"><span data-stu-id="d229d-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="d229d-131">Sarà quindi compito è possibile applicare questi concetti a un'applicazione personalizzata, che potrebbe voler costruire.</span><span class="sxs-lookup"><span data-stu-id="d229d-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="d229d-132">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="d229d-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d229d-133">Corso</span><span class="sxs-lookup"><span data-stu-id="d229d-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d229d-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d229d-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d229d-135"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="d229d-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d229d-136">MR e Azure 310: Rilevamento di oggetti</span><span class="sxs-lookup"><span data-stu-id="d229d-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="d229d-137">✔️</span><span class="sxs-lookup"><span data-stu-id="d229d-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="d229d-138">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="d229d-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="d229d-139">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="d229d-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="d229d-140">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="d229d-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="d229d-141">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quanto elencato di seguito.</span><span class="sxs-lookup"><span data-stu-id="d229d-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="d229d-142">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="d229d-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="d229d-143">Un computer di sviluppo</span><span class="sxs-lookup"><span data-stu-id="d229d-143">A development PC</span></span>
- [<span data-ttu-id="d229d-144">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="d229d-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="d229d-145">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="d229d-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="d229d-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="d229d-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="d229d-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d229d-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="d229d-148">Oggetto [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="d229d-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="d229d-149">Accesso a Internet per la configurazione di Azure e il recupero servizio visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="d229d-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="d229d-150">Una serie di immagini almeno quindici (15) sono necessarie) per ogni oggetto che si desidera la visione artificiale personalizzato per riconoscere.</span><span class="sxs-lookup"><span data-stu-id="d229d-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="d229d-151">Se si desidera, è possibile usare le immagini già fornite con questo corso [una serie di criteri utente personalizzati](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="d229d-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="d229d-152">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="d229d-152">Before you start</span></span>

1.  <span data-ttu-id="d229d-153">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="d229d-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="d229d-154">Configurare e testare l'HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d229d-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="d229d-155">Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="d229d-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="d229d-156">È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova App per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente).</span><span class="sxs-lookup"><span data-stu-id="d229d-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="d229d-157">Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="d229d-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="d229d-158">Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="d229d-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="d229d-159">Capitolo 1 - portale di visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="d229d-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="d229d-160">Usare la **servizio visione artificiale personalizzato di Azure**, sarà necessario configurare un'istanza di tale da rendere disponibili all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d229d-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="d229d-161">Spostarsi [per il **servizio visione artificiale personalizzato** pagina principale](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="d229d-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="d229d-162">Fare clic su **introduttiva**.</span><span class="sxs-lookup"><span data-stu-id="d229d-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="d229d-163">Accedere al portale del servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d229d-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="d229d-164">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="d229d-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="d229d-165">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="d229d-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="d229d-166">Una volta che si sono connessi per la prima volta, verrà richiesto con la *Terms of Service* pannello.</span><span class="sxs-lookup"><span data-stu-id="d229d-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="d229d-167">Selezionare la casella di controllo *accettare le condizioni*.</span><span class="sxs-lookup"><span data-stu-id="d229d-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="d229d-168">Quindi fare clic su **accetto**.</span><span class="sxs-lookup"><span data-stu-id="d229d-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="d229d-169">Avere accettato le condizioni, ci si trova nel *progetti* sezione.</span><span class="sxs-lookup"><span data-stu-id="d229d-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="d229d-170">Fare clic su **nuovo progetto**.</span><span class="sxs-lookup"><span data-stu-id="d229d-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="d229d-171">Verrà visualizzata una scheda sul lato destro, che verrà richiesto di specificare alcuni campi per il progetto.</span><span class="sxs-lookup"><span data-stu-id="d229d-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="d229d-172">Inserire un nome per il progetto</span><span class="sxs-lookup"><span data-stu-id="d229d-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="d229d-173">Inserire una descrizione per il progetto (**facoltativo**)</span><span class="sxs-lookup"><span data-stu-id="d229d-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="d229d-174">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="d229d-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="d229d-175">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="d229d-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d229d-176">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="d229d-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="d229d-177">Se si vuole [altre informazioni sui gruppi di risorse di Azure, passare alla documentazione associata](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="d229d-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="d229d-178">Impostare il **tipi di progetto** come **rilevamento di oggetti (anteprima)**.</span><span class="sxs-lookup"><span data-stu-id="d229d-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="d229d-179">Dopo aver completato, fare clic su **Crea progetto**, e si verrà reindirizzati alla pagina progetto servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d229d-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="d229d-180">Capitolo 2 - Training il progetto di Custom Vision</span><span class="sxs-lookup"><span data-stu-id="d229d-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="d229d-181">Una volta nel portale di visione artificiale personalizzato, l'obiettivo principale è eseguire il training di progetto per riconoscere gli oggetti specifici nelle immagini.</span><span class="sxs-lookup"><span data-stu-id="d229d-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="d229d-182">È necessario almeno quindici (15) le immagini per ogni oggetto che si desidera riconoscere l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d229d-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="d229d-183">È possibile usare le immagini fornite con questo corso ([una serie di criteri utente personalizzati](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="d229d-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="d229d-184">Per eseguire il training del progetto di visione artificiale personalizzato:</span><span class="sxs-lookup"><span data-stu-id="d229d-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="d229d-185">Fare clic sui **+** accanto alla **tag**.</span><span class="sxs-lookup"><span data-stu-id="d229d-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="d229d-186">Aggiungere un **nome** per il tag che verrà usato per associare le immagini con.</span><span class="sxs-lookup"><span data-stu-id="d229d-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="d229d-187">In questo esempio le immagini dei criteri utente personalizzati per il riconoscimento, pertanto ha assegnato un nome al tag a tale scopo, utilizziamo **Cup**.</span><span class="sxs-lookup"><span data-stu-id="d229d-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="d229d-188">Fare clic su **salvare** una volta terminato.</span><span class="sxs-lookup"><span data-stu-id="d229d-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="d229d-189">Si noterà il **Tag** è stato aggiunto (potrebbe essere necessario ricaricare la pagina affinché venga visualizzata).</span><span class="sxs-lookup"><span data-stu-id="d229d-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="d229d-190">Fare clic su **aggiungere immagini** al centro della pagina.</span><span class="sxs-lookup"><span data-stu-id="d229d-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="d229d-191">Fare clic su **Esplora file locali**e passare alle immagini di cui si vuole caricare un oggetto, con il minimo being quindici (15).</span><span class="sxs-lookup"><span data-stu-id="d229d-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="d229d-192">È possibile selezionare numerose immagini alla volta, da caricare.</span><span class="sxs-lookup"><span data-stu-id="d229d-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="d229d-193">Premere **caricare i file** dopo aver selezionato tutte le immagini che si desidera eseguire il training con il progetto.</span><span class="sxs-lookup"><span data-stu-id="d229d-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="d229d-194">I file verranno avviato il caricamento.</span><span class="sxs-lookup"><span data-stu-id="d229d-194">The files will begin uploading.</span></span> <span data-ttu-id="d229d-195">Dopo aver conferma del caricamento, fare **clic** su </span><span class="sxs-lookup"><span data-stu-id="d229d-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="d229d-196">A questo punto le immagini vengono caricate, ma non contrassegnate.</span><span class="sxs-lookup"><span data-stu-id="d229d-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="d229d-197">Per applicare un tag delle immagini, utilizzare il mouse.</span><span class="sxs-lookup"><span data-stu-id="d229d-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="d229d-198">Come passa il mouse sopra l'immagine, che risulteranno utili per un'evidenziazione della selezione creando automaticamente una selezione attorno all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="d229d-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="d229d-199">Se non è accurato, è possibile creare il proprio.</span><span class="sxs-lookup"><span data-stu-id="d229d-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="d229d-200">Questa operazione viene eseguita contenente il pulsante sinistro del mouse, e trascinando l'area di selezione per includere l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="d229d-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="d229d-201">Dopo la selezione dell'oggetto all'interno dell'immagine, verrà richiesto un prompt dei comandi di piccole dimensioni per poter *aggiungere Tag Region*.</span><span class="sxs-lookup"><span data-stu-id="d229d-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="d229d-202">Selezionare il tag creato in precedenza ('Cup', nell'esempio precedente) o se si desidera aggiungere altri tag, digitare in, fare clic sui **+ (segno più)** pulsante.</span><span class="sxs-lookup"><span data-stu-id="d229d-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="d229d-203">Per contrassegnare l'immagine successiva, è possibile fare clic sulla freccia a destra del pannello o chiudere il pannello tag (facendo il **X** nell'angolo in alto a destra del pannello) e quindi fare clic sull'immagine successiva.</span><span class="sxs-lookup"><span data-stu-id="d229d-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="d229d-204">Dopo aver creato l'immagine successiva pronto, ripetere la stessa procedura.</span><span class="sxs-lookup"><span data-stu-id="d229d-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="d229d-205">Eseguire questa operazione per tutte le immagini di che aver caricato, fino a quando non sono tutte contrassegnate.</span><span class="sxs-lookup"><span data-stu-id="d229d-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="d229d-206">È possibile selezionare diversi oggetti della stessa immagine, simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="d229d-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="d229d-207">Dopo avere tutti i tag, fare clic sui **tagged** pulsante a sinistra della schermata per visualizzare le immagini con tag.</span><span class="sxs-lookup"><span data-stu-id="d229d-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="d229d-208">A questo punto si è pronti eseguire il training del servizio.</span><span class="sxs-lookup"><span data-stu-id="d229d-208">You are now ready to train your Service.</span></span> <span data-ttu-id="d229d-209">Scegliere il **Train** pulsante e la prima iterazione training inizierà.</span><span class="sxs-lookup"><span data-stu-id="d229d-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="d229d-210">Una volta creato, sarà possibile visualizzare due pulsanti chiamati **predefinito** e **stima URL**.</span><span class="sxs-lookup"><span data-stu-id="d229d-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="d229d-211">Fare clic su **predefinito** prima di tutto, quindi fare clic su **stima URL**.</span><span class="sxs-lookup"><span data-stu-id="d229d-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="d229d-212">L'endpoint che viene fornito da questo, è impostato su qualunque *iterazione* è stata contrassegnata come predefinita.</span><span class="sxs-lookup"><span data-stu-id="d229d-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="d229d-213">Pertanto, se si apportata in un secondo momento una nuova *iterazione* e aggiornarlo come impostazione predefinita, non è necessario modificare il codice.</span><span class="sxs-lookup"><span data-stu-id="d229d-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="d229d-214">Dopo avere fatto clic su **URL di stima**, aprire *blocco note*e copiare e incollare il **URL** (chiamato anche il **stima-Endpoint**) e il **stima-chiave servizio**, in modo che è possibile recuperarlo quando ti serve in un secondo momento nel codice.</span><span class="sxs-lookup"><span data-stu-id="d229d-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="d229d-215">Capitolo 3 - configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d229d-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="d229d-216">Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="d229d-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="d229d-217">Aprire **Unity** e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="d229d-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="d229d-218">A questo punto, è necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="d229d-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="d229d-219">Inserire **CustomVisionObjDetection**.</span><span class="sxs-lookup"><span data-stu-id="d229d-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="d229d-220">Verificare che il tipo di progetto è impostato su **3D**e impostare le **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="d229d-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d229d-221">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="d229d-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="d229d-222">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d229d-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d229d-223">Passare a **modificare* > *preferenze** e quindi dalla nuova finestra, passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="d229d-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d229d-224">Change **External Script Editor** al **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d229d-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="d229d-225">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="d229d-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="d229d-226">Passare quindi ad **File > Build Settings** e passare la **piattaforma** a *Universal Windows Platform*e fare clic su di **Switch Platform** pulsante.</span><span class="sxs-lookup"><span data-stu-id="d229d-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="d229d-227">Nella stessa **Build Settings** finestra, assicurarsi che siano impostate le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d229d-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="d229d-228">**Dispositivo di destinazione** è impostata su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="d229d-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="d229d-229">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="d229d-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="d229d-230">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="d229d-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="d229d-231">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="d229d-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="d229d-232">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="d229d-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="d229d-233">Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="d229d-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="d229d-234">Nella stessa **Build Settings** finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il **Inspector** si trova.</span><span class="sxs-lookup"><span data-stu-id="d229d-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="d229d-235">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="d229d-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="d229d-236">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="d229d-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="d229d-237">**Versione del Runtime di scripting** deve essere **sperimentale** (.NET 4.6 equivalente), che attiverà una necessità di riavviare l'Editor.</span><span class="sxs-lookup"><span data-stu-id="d229d-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="d229d-238">**Back-end di scripting** deve essere **.NET**.</span><span class="sxs-lookup"><span data-stu-id="d229d-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="d229d-239">**Livello di compatibilità delle API** deve essere **.NET 4.6**.</span><span class="sxs-lookup"><span data-stu-id="d229d-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="d229d-240">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="d229d-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="d229d-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d229d-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="d229d-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="d229d-242">**Webcam**</span></span>

        3. <span data-ttu-id="d229d-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="d229d-243">**SpatialPerception**</span></span>

            <span data-ttu-id="d229d-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="d229d-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="d229d-245">Ulteriormente verso il basso il pannello, in **impostazioni XR** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, quindi assicurarsi che il **Windows misti Realtà SDK** viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="d229d-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="d229d-246">Nuovamente in **Build Settings**, *Unity C\# progetti* non è non è più in grigio: selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="d229d-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="d229d-247">Chiudi il **Build Settings** finestra.</span><span class="sxs-lookup"><span data-stu-id="d229d-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="d229d-248">Nel **Editor**, fare clic su **Edit** > **impostazioni progetto** > **grafica**.</span><span class="sxs-lookup"><span data-stu-id="d229d-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="d229d-249">Nel **Pannello di controllo** le *grafica impostazioni* saranno aperte.</span><span class="sxs-lookup"><span data-stu-id="d229d-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="d229d-250">Scorrere verso il basso finché non viene visualizzata una matrice denominata **includono sempre gli shader**.</span><span class="sxs-lookup"><span data-stu-id="d229d-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="d229d-251">Aggiungere uno slot, aumentando la **dimensioni** variabile da uno (in questo esempio, era 8 in modo che l'abbiamo fatto 9).</span><span class="sxs-lookup"><span data-stu-id="d229d-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="d229d-252">Un nuovo slot apparirà l'ultima posizione della matrice, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d229d-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="d229d-253">Nello slot, fare clic sul cerchio accanto slot per aprire un elenco di shader di destinazione di dimensioni ridotte.</span><span class="sxs-lookup"><span data-stu-id="d229d-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="d229d-254">Cercare il **Legacy shader o trasparente/diffuso** shader e fare doppio clic.</span><span class="sxs-lookup"><span data-stu-id="d229d-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="d229d-255">Capitolo 4 - importazione del pacchetto CustomVisionObjDetection Unity</span><span class="sxs-lookup"><span data-stu-id="d229d-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="d229d-256">Per questo corso viene fornito un pacchetto di Asset Unity denominati **Azure-SIG-310.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="d229d-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="d229d-257">[SUGGERIMENTO] Qualsiasi oggetto supportato da Unity, incluse intere scene, può essere compresse in un **.unitypackage** file ed esportato o importato in altri progetti.</span><span class="sxs-lookup"><span data-stu-id="d229d-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="d229d-258">È il modo più efficiente e sicuro per spostare risorse tra diverse **i progetti Unity**.</span><span class="sxs-lookup"><span data-stu-id="d229d-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="d229d-259">È possibile trovare il [pacchetto Azure-SIG-310 che è necessario scaricare qui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="d229d-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="d229d-260">Con il dashboard di Unity fronte, fare clic su **Assets** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto > pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="d229d-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="d229d-261">Usare il selettore file per selezionare i **Azure-SIG-310.unitypackage** del pacchetto e fare clic su **Open**.</span><span class="sxs-lookup"><span data-stu-id="d229d-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="d229d-262">Verrà visualizzato un elenco di componenti per questo asset all'utente.</span><span class="sxs-lookup"><span data-stu-id="d229d-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="d229d-263">Confermare l'importazione facendo il **importare** pulsante.</span><span class="sxs-lookup"><span data-stu-id="d229d-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="d229d-264">Una volta completato l'importazione, si noterà che le cartelle del pacchetto sono stato aggiunto per le **asset** cartella.</span><span class="sxs-lookup"><span data-stu-id="d229d-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="d229d-265">Questo tipo di struttura di cartelle è tipico per i progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="d229d-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="d229d-266">Il **materiali** cartella contiene il materiale usato dalle **estasiati cursore**.</span><span class="sxs-lookup"><span data-stu-id="d229d-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="d229d-267">Il **Plugins** contiene la DLL Newtonsoft utilizzato dal codice per deserializzare la risposta del servizio web.</span><span class="sxs-lookup"><span data-stu-id="d229d-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="d229d-268">Due (2) diverse versioni contenute nella cartella e sotto-cartella, sono necessari per consentire la libreria da utilizzare ed compilati da Editor di Unity e la compilazione della piattaforma UWP.</span><span class="sxs-lookup"><span data-stu-id="d229d-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="d229d-269">Il **Prefabs** cartella contiene il prefabs contenute nella scena.</span><span class="sxs-lookup"><span data-stu-id="d229d-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="d229d-270">Questi sono:</span><span class="sxs-lookup"><span data-stu-id="d229d-270">Those are:</span></span>

        1.  <span data-ttu-id="d229d-271">Il **GazeCursor**, il cursore utilizzato nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d229d-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="d229d-272">Funzionerà con il prefab SpatialMapping per poter essere inseriti nella scena in oggetti fisici.</span><span class="sxs-lookup"><span data-stu-id="d229d-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="d229d-273">Il **etichetta**, ovvero l'oggetto dell'interfaccia utente utilizzato per visualizzare il tag di oggetti nella scena quando necessario.</span><span class="sxs-lookup"><span data-stu-id="d229d-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="d229d-274">Il **SpatialMapping**, che è l'oggetto che consente di usare l'applicazione creare una mappa virtuale, usando il rilevamento spaziale degli Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d229d-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="d229d-275">Il **scene** cartella che contiene attualmente preesistente scena a questo corso.</span><span class="sxs-lookup"><span data-stu-id="d229d-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="d229d-276">Aprire il **scene** cartella, nella **pannello progetto**e fare doppio clic sul **ObjDetectionScene**, caricare la scena che si utilizzerà questo corso di.</span><span class="sxs-lookup"><span data-stu-id="d229d-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="d229d-277">**Non è incluso alcun codice**, si scriverà il codice seguendo questo corso.</span><span class="sxs-lookup"><span data-stu-id="d229d-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="d229d-278">Capitolo 5 - creare la classe CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="d229d-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="d229d-279">A questo punto si è pronti a scrivere codice.</span><span class="sxs-lookup"><span data-stu-id="d229d-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="d229d-280">Inizierà con la **CustomVisionAnalyser** classe.</span><span class="sxs-lookup"><span data-stu-id="d229d-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="d229d-281">Le chiamate per il **servizio visione artificiale personalizzato**, apportate al codice illustrato di seguito, vengono effettuate tramite il **API REST di Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="d229d-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="d229d-282">Tramite l'utilizzo, verrà visualizzato come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile per conto proprio).</span><span class="sxs-lookup"><span data-stu-id="d229d-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="d229d-283">Tenere presente, che Microsoft mette a disposizione un **SDK di Custom Vision** che può essere utilizzato anche per effettuare chiamate al servizio.</span><span class="sxs-lookup"><span data-stu-id="d229d-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="d229d-284">Per altre informazioni, vedere la [articolo SDK di Custom Vision](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="d229d-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="d229d-285">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="d229d-285">This class is responsible for:</span></span>

- <span data-ttu-id="d229d-286">Il caricamento dell'immagine più recente acquisito come una matrice di byte.</span><span class="sxs-lookup"><span data-stu-id="d229d-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="d229d-287">Invia la matrice di byte per Azure **servizio visione artificiale personalizzato** istanza per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="d229d-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="d229d-288">Ricezione della risposta come stringa JSON.</span><span class="sxs-lookup"><span data-stu-id="d229d-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="d229d-289">La deserializzazione della risposta e passando l'oggetto risultante **Prediction** per il **SceneOrganiser** classe, che si occuperà di modalità di visualizzazione nella risposta.</span><span class="sxs-lookup"><span data-stu-id="d229d-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="d229d-290">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-290">To create this class:</span></span>

1.  <span data-ttu-id="d229d-291">Fare doppio clic nella **cartella Asset**che si trova nel **pannello progetto**, quindi fare clic su **Create** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="d229d-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="d229d-292">Chiamare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="d229d-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="d229d-293">Fare doppio clic sulla cartella appena creata, per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="d229d-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="d229d-294">Fare doppio clic all'interno della cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="d229d-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="d229d-295">Denominare lo script **CustomVisionAnalyser.**</span><span class="sxs-lookup"><span data-stu-id="d229d-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="d229d-296">Fare doppio clic su nuova **CustomVisionAnalyser** script per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="d229d-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="d229d-297">Assicurarsi di avere i seguenti spazi dei nomi cui viene fatto riferimento nella parte superiore del file:</span><span class="sxs-lookup"><span data-stu-id="d229d-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="d229d-298">Nel **CustomVisionAnalyser** classe, aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="d229d-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

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
    > <span data-ttu-id="d229d-299">Assicurarsi di inserire le **stima-chiave di servizio** nel **predictionKey** variabile e il **stima-Endpoint** nel **predictionEndpoint**  variabile.</span><span class="sxs-lookup"><span data-stu-id="d229d-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="d229d-300">È stato copiato al [blocco note in precedenza, nel capitolo 2, passaggio 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="d229d-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="d229d-301">Codice per un **Awake()** deve ora essere aggiunto per inizializzare la variabile di istanza:</span><span class="sxs-lookup"><span data-stu-id="d229d-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="d229d-302">Aggiungere le coroutine (con il metodo statico **GetImageAsByteArray()** metodo sotto di essa), che otterranno i risultati dell'analisi dell'immagine, acquisito dalle **ImageCapture** classe.</span><span class="sxs-lookup"><span data-stu-id="d229d-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d229d-303">Nel **AnalyseImageCapture** coroutine, viene eseguita una chiamata ai **SceneOrganiser** classe che è ancora da creare.</span><span class="sxs-lookup"><span data-stu-id="d229d-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="d229d-304">Pertanto **lasciarli impostata come commento le righe per il momento**.</span><span class="sxs-lookup"><span data-stu-id="d229d-304">Therefore, **leave those lines commented for now**.</span></span>

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

9. <span data-ttu-id="d229d-305">Eliminare il **Start ()** e **Update ()** metodi, poiché essi non verrà utilizzati.</span><span class="sxs-lookup"><span data-stu-id="d229d-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="d229d-306">Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="d229d-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d229d-307">Come accennato in precedenza, non preoccuparsi di codice che può sembrare un errore, come si fornirà ulteriori classi presto, risolvere questi.</span><span class="sxs-lookup"><span data-stu-id="d229d-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="d229d-308">Capitolo 6: creare la classe CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="d229d-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="d229d-309">La classe si creerà ora è il **CustomVisionObjects** classe.</span><span class="sxs-lookup"><span data-stu-id="d229d-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="d229d-310">Questo script contiene un numero di oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate al servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d229d-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="d229d-311">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-311">To create this class:</span></span>

1.  <span data-ttu-id="d229d-312">Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="d229d-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="d229d-313">Chiamare lo script **CustomVisionObjects.**</span><span class="sxs-lookup"><span data-stu-id="d229d-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="d229d-314">Fare doppio clic su nuova **CustomVisionObjects** script per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="d229d-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="d229d-315">Assicurarsi di avere i seguenti spazi dei nomi cui viene fatto riferimento nella parte superiore del file:</span><span class="sxs-lookup"><span data-stu-id="d229d-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="d229d-316">Eliminare il **Start ()** e **Update ()** metodi all'interno di **CustomVisionObjects** (classe), questa classe ora deve essere vuota.</span><span class="sxs-lookup"><span data-stu-id="d229d-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="d229d-317">È importante che seguire attentamente l'istruzione successiva.</span><span class="sxs-lookup"><span data-stu-id="d229d-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="d229d-318">Se si inseriscono le nuove dichiarazioni di classe all'interno di **CustomVisionObjects** (classe), puoi accedere a errori di compilazione [capitolo 10](#chapter-10---create-the-imagecapture-class), che segnala che **AnalysisRootObject** e **BoundingBox** non sono stati trovati.</span><span class="sxs-lookup"><span data-stu-id="d229d-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="d229d-319">Aggiungere le classi seguenti *fuori* le **CustomVisionObjects** classe.</span><span class="sxs-lookup"><span data-stu-id="d229d-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="d229d-320">Questi oggetti vengono utilizzati per il **Newtonsoft** libreria per serializzare e deserializzare i dati di risposta:</span><span class="sxs-lookup"><span data-stu-id="d229d-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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

6.  <span data-ttu-id="d229d-321">Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="d229d-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="d229d-322">Capitolo 7 - creare la classe SpatialMapping</span><span class="sxs-lookup"><span data-stu-id="d229d-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="d229d-323">Questa classe verrà impostato il **Collider Mapping spaziale** della scena in modo da essere in grado di rilevare le collisioni tra oggetti virtuali e oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="d229d-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="d229d-324">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-324">To create this class:</span></span>

1.  <span data-ttu-id="d229d-325">Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="d229d-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="d229d-326">Chiamare lo script **SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="d229d-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="d229d-327">Fare doppio clic su nuova **SpatialMapping** script per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="d229d-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="d229d-328">Assicurarsi di avere i seguenti spazi dei nomi citati in precedenza il **SpatialMapping** classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="d229d-329">Quindi, aggiungere le variabili seguenti all'interno di **SpatialMapping** classe, sopra il **Start ()** (metodo):</span><span class="sxs-lookup"><span data-stu-id="d229d-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="d229d-330">Aggiungere il **Awake()** e **Start ()**:</span><span class="sxs-lookup"><span data-stu-id="d229d-330">Add the **Awake()** and **Start()**:</span></span>

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

6.  <span data-ttu-id="d229d-331">Eliminare il **Update ()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="d229d-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="d229d-332">Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="d229d-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="d229d-333">Capitolo 8 - creare la classe GazeCursor</span><span class="sxs-lookup"><span data-stu-id="d229d-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="d229d-334">Questa classe è responsabile della configurazione del cursore nella posizione corretta nell'area reale, mediante l'utilizzo dei **SpatialMappingCollider**, creato nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="d229d-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="d229d-335">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-335">To create this class:</span></span>

1.  <span data-ttu-id="d229d-336">Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="d229d-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="d229d-337">Chiamare lo script **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="d229d-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="d229d-338">Fare doppio clic su nuova **GazeCursor** script per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="d229d-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="d229d-339">Assicurarsi di avere il seguente spazio dei nomi citato in precedenza il **GazeCursor** classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="d229d-340">Quindi aggiungere la variabile seguente all'interno di **GazeCursor** classe, sopra la **Start ()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="d229d-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="d229d-341">Aggiorna il **Start ()** metodo con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="d229d-341">Update the **Start()** method with the following code:</span></span>

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

6.  <span data-ttu-id="d229d-342">Aggiorna il **Update ()** metodo con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="d229d-342">Update the **Update()** method with the following code:</span></span>

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
    > <span data-ttu-id="d229d-343">Senza doversi preoccupare di errore per il **SceneOrganiser** classe non viene trovato, verrà creato nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="d229d-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="d229d-344">Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="d229d-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="d229d-345">Capitolo 9 - creare la classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="d229d-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="d229d-346">Questa classe sarà:</span><span class="sxs-lookup"><span data-stu-id="d229d-346">This class will:</span></span>

-   <span data-ttu-id="d229d-347">Configurare il *Main Camera* collegando i componenti appropriati a esso.</span><span class="sxs-lookup"><span data-stu-id="d229d-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="d229d-348">Quando viene rilevato un oggetto, sarà responsabile del calcolo relativa posizione nel mondo reale e sul posto un **Tag Label** vicino, con l'appropriato **nome del Tag**.</span><span class="sxs-lookup"><span data-stu-id="d229d-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="d229d-349">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-349">To create this class:</span></span>

1.  <span data-ttu-id="d229d-350">Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="d229d-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="d229d-351">Denominare lo script **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="d229d-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="d229d-352">Fare doppio clic su nuova **SceneOrganiser** script per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="d229d-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="d229d-353">Assicurarsi di avere i seguenti spazi dei nomi citati in precedenza il **SceneOrganiser** classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="d229d-354">Quindi aggiungere le variabili seguenti all'interno di **SceneOrganiser** classe sopra il **Start ()** metodo:</span><span class="sxs-lookup"><span data-stu-id="d229d-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="d229d-355">Eliminare il **Start ()** e **Update ()** metodi.</span><span class="sxs-lookup"><span data-stu-id="d229d-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="d229d-356">Sotto le variabili, aggiungere il **Awake()** (metodo), che consente di inizializzare la classe e impostare la scena.</span><span class="sxs-lookup"><span data-stu-id="d229d-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="d229d-357">Aggiungere il **PlaceAnalysisLabel()** metodo, che verrà *Instantiate* l'etichetta nella scena (che a questo punto è invisibile all'utente).</span><span class="sxs-lookup"><span data-stu-id="d229d-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="d229d-358">Inserisce inoltre quad (anche invisibili) in cui viene inserito l'immagine e si sovrappone al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="d229d-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="d229d-359">Questo è importante perché le coordinate della finestra recuperati dal servizio dopo l'analisi vengono risalire in questa quad determinata la posizione approssimativa dell'oggetto nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="d229d-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

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

8.  <span data-ttu-id="d229d-360">Aggiungere il **FinaliseLabel()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="d229d-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="d229d-361">È responsabile per:</span><span class="sxs-lookup"><span data-stu-id="d229d-361">It is responsible for:</span></span>

    *   <span data-ttu-id="d229d-362">Impostando il *Label* testo con il *Tag* la stima con il livello di confidenza più elevato.</span><span class="sxs-lookup"><span data-stu-id="d229d-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="d229d-363">Chiamare il calcolo del *rettangolo di selezione* sull'oggetto quad, posizionato in precedenza e posizionare l'etichetta nella scena.</span><span class="sxs-lookup"><span data-stu-id="d229d-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="d229d-364">Regolare la profondità di etichetta usando un Raycast verso la *rettangolo di selezione*, quali dovrebbe entri in conflitto con l'oggetto nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="d229d-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="d229d-365">Reimpostare il processo di acquisizione per consentire all'utente di acquisire un'altra immagine.</span><span class="sxs-lookup"><span data-stu-id="d229d-365">Resetting the capture process to allow the user to capture another image.</span></span>

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

9.  <span data-ttu-id="d229d-366">Aggiungere il **CalculateBoundingBoxPosition()** metodo, che ospita un numero di calcoli necessari per convertire le *rettangolo di selezione* coordinate recuperati dal servizio e crearli di nuovo in modo proporzionale su quad.</span><span class="sxs-lookup"><span data-stu-id="d229d-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

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

10. <span data-ttu-id="d229d-367">Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="d229d-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d229d-368">Prima di continuare, aprire il **CustomVisionAnalyser** (classe) e all'interno di **AnalyseLastImageCaptured()** metodo *rimuovere il commento* le righe seguenti:</span><span class="sxs-lookup"><span data-stu-id="d229d-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
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
> <span data-ttu-id="d229d-369">Senza doversi preoccupare di **ImageCapture** classe messaggio 'non è stato possibile trovare', si creerà nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="d229d-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="d229d-370">Capitolo 10 - creare la classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="d229d-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="d229d-371">La classe successiva si intende creare è il **ImageCapture** classe.</span><span class="sxs-lookup"><span data-stu-id="d229d-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="d229d-372">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="d229d-372">This class is responsible for:</span></span>

*   <span data-ttu-id="d229d-373">Acquisizione di un'immagine usando la fotocamera di HoloLens e archiviandolo nel *App* cartella.</span><span class="sxs-lookup"><span data-stu-id="d229d-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="d229d-374">Gestisce *toccare* movimenti da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="d229d-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="d229d-375">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d229d-375">To create this class:</span></span>

1.  <span data-ttu-id="d229d-376">Andare alla **script** cartella creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d229d-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="d229d-377">Fare doppio clic all'interno della cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="d229d-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="d229d-378">Denominare lo script **ImageCapture**.</span><span class="sxs-lookup"><span data-stu-id="d229d-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="d229d-379">Fare doppio clic su nuova **ImageCapture** script per aprirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="d229d-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="d229d-380">Sostituire gli spazi dei nomi nella parte superiore del file con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="d229d-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="d229d-381">Quindi aggiungere le variabili seguenti all'interno di **ImageCapture** classe sopra il **Start ()** metodo:</span><span class="sxs-lookup"><span data-stu-id="d229d-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="d229d-382">Codice per un **Awake()** e **Start ()** metodi deve ora essere aggiunto:</span><span class="sxs-lookup"><span data-stu-id="d229d-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="d229d-383">Implementare un gestore che verrà chiamato quando si verifica un gesto tocco:</span><span class="sxs-lookup"><span data-stu-id="d229d-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

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
    > <span data-ttu-id="d229d-384">Quando il cursore si trova **verde**, significa che la fotocamera è disponibile per acquisire l'immagine.</span><span class="sxs-lookup"><span data-stu-id="d229d-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="d229d-385">Quando il cursore si trova **rosso**, significa che la fotocamera è occupata.</span><span class="sxs-lookup"><span data-stu-id="d229d-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="d229d-386">Aggiungere il metodo che l'applicazione usa per avviare il processo di acquisizione di immagini e archiviare l'immagine:</span><span class="sxs-lookup"><span data-stu-id="d229d-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

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

9.  <span data-ttu-id="d229d-387">Aggiungere i gestori che verranno chiamati quando è stata acquisita la foto e quando è pronto per essere analizzati.</span><span class="sxs-lookup"><span data-stu-id="d229d-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="d229d-388">Il risultato viene quindi passato per il **CustomVisionAnalyser** per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="d229d-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

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

10. <span data-ttu-id="d229d-389">Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="d229d-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="d229d-390">Capitolo 11 - configurazione gli script nella scena</span><span class="sxs-lookup"><span data-stu-id="d229d-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="d229d-391">Ora che è necessario scrivere tutto il codice necessario per questo progetto, è ora possibile configurare gli script nella scena e su prefabs, per essi funzionino correttamente.</span><span class="sxs-lookup"><span data-stu-id="d229d-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="d229d-392">All'interno di **Editor di Unity**, nel **pannello gerarchia**, selezionare il **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="d229d-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="d229d-393">Nel **Pannello di controllo**, con la **Main Camera** selezionato, fare clic su **Add Component**, quindi cercare **SceneOrganiser** script e Fare doppio clic, per aggiungerlo.</span><span class="sxs-lookup"><span data-stu-id="d229d-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="d229d-394">Nel **pannello progetto**, aprire il **cartella Prefabs**, trascinare il **etichetta** prefab nel *etichetta* area di input destinazione del riferimento vuoto nel **SceneOrganiser** che appena aggiunti allo script il *Main Camera*, come illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="d229d-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="d229d-395">Nel **Pannello di gerarchia**, selezionare la **GazeCursor** figlio del **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="d229d-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="d229d-396">Nel **Pannello di controllo**, con la **GazeCursor** selezionato, fare clic su **Add Component**, quindi cercare **GazeCursor** script e Fare doppio clic, per aggiungerlo.</span><span class="sxs-lookup"><span data-stu-id="d229d-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="d229d-397">Ripetere l'operazione, il **pannello gerarchia**, selezionare il **SpatialMapping** figlio del **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="d229d-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="d229d-398">Nel **Pannello di controllo**, con la **SpatialMapping** selezionato, fare clic su **Add Component**, quindi cercare **SpatialMapping** script e fare doppio clic, per aggiungerlo.</span><span class="sxs-lookup"><span data-stu-id="d229d-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="d229d-399">Gli script rimanenti che si hanno non verrà aggiunti dal codice nel set il **SceneOrganiser** script, in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d229d-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="d229d-400">Capitolo 12 - prima della compilazione</span><span class="sxs-lookup"><span data-stu-id="d229d-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="d229d-401">Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload in di Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d229d-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="d229d-402">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="d229d-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="d229d-403">Tutte le impostazioni indicate nella [capitolo 3](#chapter-3---set-up-the-unity-project) siano impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="d229d-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="d229d-404">Lo script **SceneOrganiser** è collegato il **Main Camera** oggetto.</span><span class="sxs-lookup"><span data-stu-id="d229d-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="d229d-405">Lo script **GazeCursor** è collegato il **GazeCursor** oggetto.</span><span class="sxs-lookup"><span data-stu-id="d229d-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="d229d-406">Lo script **SpatialMapping** è collegato il **SpatialMapping** oggetto.</span><span class="sxs-lookup"><span data-stu-id="d229d-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="d229d-407">Nelle [capitolo 5](#chapter-5---create-the-customvisionanalyser-class), passaggio 6:</span><span class="sxs-lookup"><span data-stu-id="d229d-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="d229d-408">Assicurarsi di inserire le **chiave del servizio stima** nel **predictionKey** variabile.</span><span class="sxs-lookup"><span data-stu-id="d229d-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="d229d-409">Sono stati inseriti i **Endpoint di stima** nel **predictionEndpoint** classe.</span><span class="sxs-lookup"><span data-stu-id="d229d-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="d229d-410">Capitolo 13 - compila la soluzione di piattaforma UWP e trasferire localmente l'applicazione</span><span class="sxs-lookup"><span data-stu-id="d229d-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="d229d-411">A questo punto si è pronti a compilare l'applicazione come una soluzione di piattaforma UWP potrai distribuire con il Microsoft HoloLens è.</span><span class="sxs-lookup"><span data-stu-id="d229d-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="d229d-412">Per iniziare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="d229d-412">To begin the build process:</span></span>

1.  <span data-ttu-id="d229d-413">Passare a **File > Impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="d229d-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="d229d-414">Segni di graduazione **Unity C\# progetti**.</span><span class="sxs-lookup"><span data-stu-id="d229d-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="d229d-415">Fare clic su **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="d229d-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="d229d-416">Verrà aggiunta la scena attualmente aperta per la compilazione.</span><span class="sxs-lookup"><span data-stu-id="d229d-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="d229d-417">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="d229d-417">Click **Build**.</span></span> <span data-ttu-id="d229d-418">Unity avvierà una *Esplora File* finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in.</span><span class="sxs-lookup"><span data-stu-id="d229d-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="d229d-419">Creare ora tale cartella e denominarlo **App**.</span><span class="sxs-lookup"><span data-stu-id="d229d-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="d229d-420">Quindi con il **App** cartella selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="d229d-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="d229d-421">Unity verrà avviata la compilazione del progetto per la **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="d229d-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="d229d-422">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).</span><span class="sxs-lookup"><span data-stu-id="d229d-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="d229d-423">Per distribuire al Microsoft HoloLens, è necessario l'indirizzo IP del dispositivo (per la distribuzione remota), e per verificare che siano anche dispone **modalità sviluppatore** impostato.</span><span class="sxs-lookup"><span data-stu-id="d229d-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="d229d-424">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="d229d-424">To do this:</span></span>

    1.  <span data-ttu-id="d229d-425">Durante l'uso di HoloLens, aprire il **impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="d229d-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="d229d-426">Passare a **rete e Internet** > **Wi-Fi** > **opzioni avanzate**</span><span class="sxs-lookup"><span data-stu-id="d229d-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="d229d-427">Si noti il **IPv4** indirizzo.</span><span class="sxs-lookup"><span data-stu-id="d229d-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="d229d-428">Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza** > **per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="d229d-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="d229d-429">Impostare **modalità sviluppatore** *su*.</span><span class="sxs-lookup"><span data-stu-id="d229d-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="d229d-430">Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d229d-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="d229d-431">Selezione configurazione di soluzione **Debug**.</span><span class="sxs-lookup"><span data-stu-id="d229d-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="d229d-432">La piattaforma della soluzione, selezionare **x86, computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="d229d-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="d229d-433">Verrà richiesto di inserire le **indirizzo IP** di un dispositivo remoto (di Microsoft HoloLens, in questo caso, che si è preso nota).</span><span class="sxs-lookup"><span data-stu-id="d229d-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="d229d-434">Andare alla **compilare** dal menu e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d229d-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="d229d-435">L'app deve vengono ora visualizzati nell'elenco delle App installate in di Microsoft HoloLens, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="d229d-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="d229d-436">Per usare l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="d229d-436">To use the application:</span></span>

* <span data-ttu-id="d229d-437">Esaminare un oggetto che aver eseguito il training con il **servizio visione artificiale personalizzato di Azure, rilevamento di oggetti**e utilizzare il **gesto tocco**.</span><span class="sxs-lookup"><span data-stu-id="d229d-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="d229d-438">Se l'oggetto è stato rilevato, un spazio globale *testo dell'etichetta* verranno visualizzate con il nome del tag.</span><span class="sxs-lookup"><span data-stu-id="d229d-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d229d-439">Ogni volta che è acquisire una foto e inviarlo al servizio, è possibile tornare alla pagina del servizio e ripetere il training del servizio con le immagini appena acquisite.</span><span class="sxs-lookup"><span data-stu-id="d229d-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="d229d-440">All'inizio, sarà probabilmente anche essere necessario correggere il *riquadri* per ottenere una maggiore precisione e ripetere il training del servizio.</span><span class="sxs-lookup"><span data-stu-id="d229d-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="d229d-441">Il testo dell'etichetta inseriti potrebbe non essere visualizzato in prossimità dell'oggetto quando i sensori Microsoft HoloLens e/o SpatialTrackingComponent in Unity non è possibile posizionare il colliders appropriato, rispetto all'oggetto reale.</span><span class="sxs-lookup"><span data-stu-id="d229d-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="d229d-442">Provare a usare l'applicazione in un'area diversa, se in questo caso.</span><span class="sxs-lookup"><span data-stu-id="d229d-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="d229d-443">La visione artificiale personalizzato, applicazione di rilevamento di oggetti</span><span class="sxs-lookup"><span data-stu-id="d229d-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="d229d-444">Complimenti, è stata compilata un'app per realtà mista che sfrutta la visione personalizzata di Azure, API di rilevamento di oggetti, che può riconoscere un oggetto da un'immagine e quindi specificare una posizione approssimativa per quell'oggetto nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="d229d-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="d229d-445">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="d229d-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d229d-446">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="d229d-446">Exercise 1</span></span>

<span data-ttu-id="d229d-447">Aggiunta all'etichetta di testo, utilizzare un cubo semi-trasparente per eseguire il wrapping dell'oggetto reale in una 3D *rettangolo di selezione*.</span><span class="sxs-lookup"><span data-stu-id="d229d-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="d229d-448">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="d229d-448">Exercise 2</span></span>

<span data-ttu-id="d229d-449">Eseguire il training del servizio visione artificiale personalizzato per riconoscere più oggetti.</span><span class="sxs-lookup"><span data-stu-id="d229d-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="d229d-450">Esercizio 3</span><span class="sxs-lookup"><span data-stu-id="d229d-450">Exercise 3</span></span>

<span data-ttu-id="d229d-451">Riprodurre un suono quando un oggetto viene riconosciuto.</span><span class="sxs-lookup"><span data-stu-id="d229d-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="d229d-452">Esercizio 4</span><span class="sxs-lookup"><span data-stu-id="d229d-452">Exercise 4</span></span>

<span data-ttu-id="d229d-453">Usare l'API di eseguire nuovamente il training del servizio con le stesse immagini all'app è l'analisi, pertanto, per rendere il più accurati (eseguire stime e contemporaneamente di training).</span><span class="sxs-lookup"><span data-stu-id="d229d-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
