---
title: MR e Azure 302 - visione artificiale
description: Completa questo corso per imparare a riconoscere contenuti visivi all'interno di un'immagine fornita, l'utilizzo di visione artificiale di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, visione artificiale, hololens, coinvolgenti, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597892"
---
>[!NOTE]
><span data-ttu-id="85443-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="85443-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="85443-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="85443-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="85443-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="85443-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="85443-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="85443-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="85443-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="85443-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="85443-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="85443-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="85443-110">MR e Azure 302: Visione artificiale</span><span class="sxs-lookup"><span data-stu-id="85443-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="85443-111">In questo corso, si apprenderà come riconoscere contenuto visivo all'interno di un'immagine specificato, usando le funzionalità di visione artificiale di Azure in un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="85443-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="85443-112">Risultati di riconoscimento verranno visualizzati come tag descrittivi.</span><span class="sxs-lookup"><span data-stu-id="85443-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="85443-113">È possibile utilizzare questo servizio senza la necessità di eseguire il training di un modello di machine learning.</span><span class="sxs-lookup"><span data-stu-id="85443-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="85443-114">Se l'implementazione richieda training modello di machine learning, vedere [MR e 302b Azure](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="85443-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![risultato di Lab](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="85443-116">La visione artificiale Microsoft è un set di API progettato per offrire agli sviluppatori con l'elaborazione di immagini e analisi (con restituiscono informazioni), utilizzando algoritmi avanzati, tutto dal cloud.</span><span class="sxs-lookup"><span data-stu-id="85443-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="85443-117">Gli sviluppatori di caricare un'immagine o URL dell'immagine e gli algoritmi di API visione artificiale Microsoft analizzano il contenuto visivo, basato su input scelte utente, che quindi può restituire le informazioni, inclusi, che identifica il tipo e la qualità di un'immagine, rileva i visi umani ( Restituisce le coordinate) e l'assegnazione di tag, o classificazione di immagini.</span><span class="sxs-lookup"><span data-stu-id="85443-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="85443-118">Per altre informazioni, visitare il [pagina API visione artificiale di Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="85443-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="85443-119">Dopo aver completato il corso, si avrà una realtà mista applicazione HoloLens, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="85443-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="85443-120">Usa il gesto tocco, la camera e il HoloLens consente di acquisire un'immagine.</span><span class="sxs-lookup"><span data-stu-id="85443-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="85443-121">L'immagine verrà inviato il Computer Vision API nel servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="85443-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="85443-122">Gli oggetti riconosciuti verranno elencati in un gruppo dell'interfaccia utente semplice posizionato nella scena Unity.</span><span class="sxs-lookup"><span data-stu-id="85443-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="85443-123">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="85443-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="85443-124">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="85443-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="85443-125">È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="85443-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="85443-126">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="85443-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="85443-127">Corso</span><span class="sxs-lookup"><span data-stu-id="85443-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="85443-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="85443-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="85443-129"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="85443-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="85443-130">MR e Azure 302: Visione artificiale</span><span class="sxs-lookup"><span data-stu-id="85443-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="85443-131">✔️</span><span class="sxs-lookup"><span data-stu-id="85443-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="85443-132">✔️</span><span class="sxs-lookup"><span data-stu-id="85443-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="85443-133">Questo corso è incentrato principalmente sulla HoloLens, è inoltre possibile applicare informazioni in questo corso per auricolari (VR) coinvolgenti di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="85443-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="85443-134">Poiché immersive auricolari (VR) non è accessibile fotocamere, sarà necessario una fotocamera esterna connessa al PC.</span><span class="sxs-lookup"><span data-stu-id="85443-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="85443-135">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare immersive auricolari (VR).</span><span class="sxs-lookup"><span data-stu-id="85443-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="85443-136">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="85443-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="85443-137">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="85443-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="85443-138">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="85443-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="85443-139">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .</span><span class="sxs-lookup"><span data-stu-id="85443-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="85443-140">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="85443-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="85443-141">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="85443-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="85443-142">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="85443-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="85443-143">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="85443-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="85443-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="85443-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="85443-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="85443-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="85443-146">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="85443-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="85443-147">Una fotocamera connessa al PC (per lo sviluppo visore VR immersivi)</span><span class="sxs-lookup"><span data-stu-id="85443-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="85443-148">Accesso a Internet per la configurazione di Azure e il recupero delle API visione artificiale</span><span class="sxs-lookup"><span data-stu-id="85443-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="85443-149">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="85443-149">Before you start</span></span>

1.  <span data-ttu-id="85443-150">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="85443-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="85443-151">Configurare e testare l'HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85443-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="85443-152">Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="85443-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="85443-153">È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova App per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente).</span><span class="sxs-lookup"><span data-stu-id="85443-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="85443-154">Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="85443-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="85443-155">Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="85443-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="85443-156">Capitolo 1: il portale di Azure</span><span class="sxs-lookup"><span data-stu-id="85443-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="85443-157">Usare la *API visione artificiale* servizio in Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="85443-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="85443-158">Accedere prima di tutto per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="85443-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="85443-159">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="85443-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="85443-160">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="85443-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="85443-161">Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *API visione artificiale*, fare clic su **invio**.</span><span class="sxs-lookup"><span data-stu-id="85443-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Creare una nuova risorsa in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="85443-163">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="85443-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="85443-164">La nuova pagina fornirà una descrizione del *API visione artificiale* servizio.</span><span class="sxs-lookup"><span data-stu-id="85443-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="85443-165">AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="85443-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Informazioni sul servizio di computer vision api](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="85443-167">Dopo avere fatto clic su **Create**:</span><span class="sxs-lookup"><span data-stu-id="85443-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="85443-168">Inserire la posizione desiderata **nome** per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="85443-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="85443-169">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="85443-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="85443-170">Selezionare il **piano tariffario** appropriati per l'utente, se questo è il primo tempo nella creazione una *API visione artificiale* servizio, un livello gratuito (denominato F0) deve essere disponibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="85443-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="85443-171">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="85443-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="85443-172">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="85443-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="85443-173">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="85443-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="85443-174">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="85443-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="85443-175">Determinare il percorso per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="85443-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="85443-176">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="85443-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="85443-177">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="85443-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="85443-178">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="85443-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="85443-179">Fare clic su Crea.</span><span class="sxs-lookup"><span data-stu-id="85443-179">Click Create.</span></span>

        ![Informazioni sulla creazione del servizio](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="85443-181">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="85443-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="85443-182">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="85443-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Vedere la nuova notifica per il nuovo servizio](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="85443-184">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="85443-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Selezionare il pulsante di passare alla risorsa.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="85443-186">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="85443-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="85443-187">Verrà visualizzata per la nuova istanza del servizio API visione artificiale.</span><span class="sxs-lookup"><span data-stu-id="85443-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![Il nuovo servizio API visione artificiale](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="85443-189">All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, questa operazione viene eseguita tramite chiave di sottoscrizione del servizio.</span><span class="sxs-lookup"><span data-stu-id="85443-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="85443-190">Dal *avvio rapido* pagina, delle *API visione artificiale* del servizio, passare al primo passaggio *individuare le chiavi*e fare clic su **chiavi** ( è possibile anche ottenere ciò scegliendo il collegamento blu chiavi, che si trova nel menu di spostamento dei servizi, indicato dall'icona della chiave).</span><span class="sxs-lookup"><span data-stu-id="85443-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="85443-191">Il servizio verrà visualizzata *chiavi*.</span><span class="sxs-lookup"><span data-stu-id="85443-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="85443-192">Richiedere una copia di una delle chiavi visualizzate, in quanto sarà necessaria in un secondo momento nel progetto.</span><span class="sxs-lookup"><span data-stu-id="85443-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="85443-193">Tornare al *introduttiva* pagina e da lì, recuperare l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="85443-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="85443-194">Tenere presente quelle in uso potrebbe essere diverso, in base al paese (che se si tratta, sarà necessario apportare una modifica al codice in un secondo momento).</span><span class="sxs-lookup"><span data-stu-id="85443-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="85443-195">Eseguire una copia di questo endpoint per l'uso in un secondo momento:</span><span class="sxs-lookup"><span data-stu-id="85443-195">Take a copy of this endpoint for use later:</span></span>

    ![Il nuovo servizio API visione artificiale](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="85443-197">È possibile controllare quali sono i diversi endpoint [qui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="85443-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="85443-198">Capitolo 2: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="85443-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="85443-199">Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="85443-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="85443-200">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="85443-200">Open *Unity* and click **New**.</span></span> 

    ![Avvio nuovo progetto Unity.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="85443-202">A questo punto, è necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="85443-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="85443-203">Inserire **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="85443-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="85443-204">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="85443-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="85443-205">Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="85443-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="85443-206">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="85443-206">Then, click **Create project**.</span></span>

    ![Fornire i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="85443-208">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="85443-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="85443-209">Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="85443-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="85443-210">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="85443-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="85443-211">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="85443-211">Close the **Preferences** window.</span></span>

    ![Aggiornamento delle preferenze dell'editor di script.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="85443-213">Passare quindi ad **File > Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sui **commutatore piattaforma** pulsante per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="85443-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Crea finestra delle impostazioni, la piattaforma del commutatore alla piattaforma UWP.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="85443-215">Mentre si trovano ancora nella **File > Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="85443-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="85443-216">**Dispositivo di destinazione** è impostata su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="85443-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="85443-217">Per le cuffie coinvolgenti, impostare **dispositivo di destinazione** al *qualsiasi dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="85443-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="85443-218">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="85443-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="85443-219">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="85443-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="85443-220">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="85443-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="85443-221">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="85443-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="85443-222">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="85443-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="85443-223">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="85443-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="85443-224">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="85443-224">A save window will appear.</span></span>
        
            ![Fare clic su Aggiungi pulsante Apri scene](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="85443-226">Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="85443-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crea nuova cartella scripts](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="85443-228">Aprire appena creato **scene** cartella e quindi la *nome File*: campo di testo, digitare **MR_ComputerVisionScene**, quindi fare clic su **Salva** .</span><span class="sxs-lookup"><span data-stu-id="85443-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Assegnare un nome nuova scena.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="85443-230">Tenere presente, è necessario salvare le scene di Unity all'interno di *asset* cartella, come devono essere associate al progetto di Unity.</span><span class="sxs-lookup"><span data-stu-id="85443-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="85443-231">Creare la cartella scene (e altre simili) è un modo tipico strutturare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="85443-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="85443-232">Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="85443-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="85443-233">Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.</span><span class="sxs-lookup"><span data-stu-id="85443-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Aprire le impostazioni del giocatore.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="85443-235">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="85443-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="85443-236">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="85443-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="85443-237">**Versione del Runtime di scripting** deve essere **stabile** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="85443-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="85443-238">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="85443-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="85443-239">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="85443-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aggiornare le altre impostazioni.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="85443-241">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="85443-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="85443-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="85443-242">**InternetClient**</span></span>
        2. <span data-ttu-id="85443-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="85443-243">**Webcam**</span></span>

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="85443-245">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="85443-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aggiornare le impostazioni di R X.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="85443-247">Nuovamente in *Build Settings* _Unity C#_  progetti non sono più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="85443-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="85443-248">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="85443-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="85443-249">Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="85443-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="85443-250">Capitolo 3: impostazione della fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="85443-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85443-251">Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importarlo nel progetto come un [pacchetto personalizzato ](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="85443-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="85443-252">Nel *Pannello di gerarchia*, selezionare la **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="85443-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="85443-253">Una volta selezionata, sarà possibile visualizzare tutti i componenti del **Main Camera** nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="85443-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="85443-254">Il **oggetto della fotocamera** devono essere denominati **Main Camera** (si noti l'ortografici!)</span><span class="sxs-lookup"><span data-stu-id="85443-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="85443-255">Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici!)</span><span class="sxs-lookup"><span data-stu-id="85443-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="85443-256">Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="85443-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="85443-257">Impostare **Cancella flag** al **colore a tinta unita** (ignorare questo visore VR immersivi).</span><span class="sxs-lookup"><span data-stu-id="85443-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="85443-258">Impostare il **sfondo** colore del componente della fotocamera **nero, Alpha 0 (codice esadecimale: #00000000)** (ignorare questo visore VR immersivi).</span><span class="sxs-lookup"><span data-stu-id="85443-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Aggiornare i componenti della fotocamera.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="85443-260">Successivamente, sarà necessario creare un oggetto semplice "Cursor" collegato al **Main Camera**, che aiutano a posizionare l'analisi delle immagini restituirà quando l'applicazione è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="85443-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="85443-261">Questo cursore determinerà il punto centrale dello stato attivo della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="85443-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="85443-262">Per creare il cursore:</span><span class="sxs-lookup"><span data-stu-id="85443-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="85443-263">Nel *Pannello di gerarchia*, fare clic sui **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="85443-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="85443-264">Sotto **oggetto 3D**, fare clic su **sfera**.</span><span class="sxs-lookup"><span data-stu-id="85443-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Selezionare l'oggetto cursore.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="85443-266">Rinominare il **sfera** al **cursore** fare doppio clic sull'oggetto cursore o premere il tasto 'F2' con l'oggetto selezionato e assicurarsi che sia disponibile come elemento figlio del **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="85443-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="85443-267">Nel *pannello gerarchia*, fare clic sulla **cursore**.</span><span class="sxs-lookup"><span data-stu-id="85443-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="85443-268">Con il cursore selezionato, modificare le variabili seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="85443-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="85443-269">Impostare il *trasformare posizione* a **0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="85443-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="85443-270">Impostare il *scalabilità* a **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="85443-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Aggiornare la posizione di trasformazione e la scala.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="85443-272">Capitolo 4 – programma di installazione il sistema di etichetta</span><span class="sxs-lookup"><span data-stu-id="85443-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="85443-273">Dopo aver acquisito un'immagine con fotocamera degli HoloLens, tale immagine verrà inviato per il *API visione artificiale di Azure* istanza del servizio per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="85443-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="85443-274">I risultati dell'analisi sarà un elenco di oggetti riconosciuti denominati **tag**.</span><span class="sxs-lookup"><span data-stu-id="85443-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="85443-275">Si userà le etichette (come un testo 3D nello spazio globale) per visualizzare questi tag in corrispondenza della posizione che è stata eseguita la foto.</span><span class="sxs-lookup"><span data-stu-id="85443-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="85443-276">I passaggi seguenti illustrano come configurare il **etichetta** oggetto.</span><span class="sxs-lookup"><span data-stu-id="85443-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="85443-277">Fare doppio clic in un punto qualsiasi nella gerarchia di sezione del pannello (il percorso non è rilevante a questo punto), **oggetto 3D**, aggiungere un **testo 3D**.</span><span class="sxs-lookup"><span data-stu-id="85443-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="85443-278">Denominarlo **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="85443-278">Name it **LabelText**.</span></span>

    ![Creare l'oggetto testo 3D.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="85443-280">Nel *pannello gerarchia*, fare clic sulla **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="85443-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="85443-281">Con il **LabelText** selezionato, modificare le variabili seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="85443-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="85443-282">Impostare il **posizione** a **0, 0,0**</span><span class="sxs-lookup"><span data-stu-id="85443-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="85443-283">Impostare il **scalabilità** a **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="85443-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="85443-284">Nel componente **testo Mesh**:</span><span class="sxs-lookup"><span data-stu-id="85443-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="85443-285">Sostituire tutto il testo all'interno **testo**, con "..."</span><span class="sxs-lookup"><span data-stu-id="85443-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="85443-286">Impostare il **ancoraggio** a **in mezzo al centro**</span><span class="sxs-lookup"><span data-stu-id="85443-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="85443-287">Impostare il **allineamento** a **Center**</span><span class="sxs-lookup"><span data-stu-id="85443-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="85443-288">Impostare il **Dimensione tabulazione** a **4**</span><span class="sxs-lookup"><span data-stu-id="85443-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="85443-289">Impostare il **Font Size** a **50**</span><span class="sxs-lookup"><span data-stu-id="85443-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="85443-290">Impostare il **colore** a **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="85443-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Componente di testo](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="85443-292">Trascinare il **LabelText** dal *pannello gerarchia*, nel *cartella Asset*all'interno nel *progetto pannello*.</span><span class="sxs-lookup"><span data-stu-id="85443-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="85443-293">In questo modo il **LabelText** un Prefab, in modo che non è possibile creare istanze nel codice.</span><span class="sxs-lookup"><span data-stu-id="85443-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Crea un prefab dell'oggetto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="85443-295">È consigliabile eliminare il **LabelText** dalle *gerarchia pannello*, in modo che non verrà visualizzato nella scena apertura.</span><span class="sxs-lookup"><span data-stu-id="85443-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="85443-296">Quanto è diventato un prefab, che si chiamerà per le singole istanze dalla cartella Assets, non è necessario per contenerlo entro la scena.</span><span class="sxs-lookup"><span data-stu-id="85443-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="85443-297">La struttura dell'oggetto finale nel *gerarchia pannello* dovrebbe essere simile a quello illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="85443-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Struttura finale del Pannello di gerarchia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="85443-299">Capitolo 5: creare la classe ResultsLabel</span><span class="sxs-lookup"><span data-stu-id="85443-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="85443-300">È il primo script è necessario creare il *ResultsLabel* (classe), che è responsabile per le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="85443-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="85443-301">Creazione di etichette nello spazio complessivo appropriato, rispetto alla posizione della Camera.</span><span class="sxs-lookup"><span data-stu-id="85443-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="85443-302">Visualizzare i tag da onerosa l'immagine.</span><span class="sxs-lookup"><span data-stu-id="85443-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="85443-303">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="85443-303">To create this class:</span></span> 

1.  <span data-ttu-id="85443-304">Fare doppio clic nella *Pannello di progetto*, quindi **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="85443-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="85443-305">Denominare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="85443-305">Name the folder **Scripts**.</span></span> 

    ![Crea cartella scripts.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="85443-307">Con il **script** cartella creare, fare doppio clic sopra per avviarlo.</span><span class="sxs-lookup"><span data-stu-id="85443-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="85443-308">Quindi all'interno di tale cartella, pulsante destro del mouse e scegliere **Crea >** quindi  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="85443-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="85443-309">Denominare lo script *ResultsLabel*.</span><span class="sxs-lookup"><span data-stu-id="85443-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="85443-310">Fare doppio clic su nuova *ResultsLabel* script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="85443-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="85443-311">All'interno della classe inserire il codice seguente nel *ResultsLabel* classe:</span><span class="sxs-lookup"><span data-stu-id="85443-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

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

6.  <span data-ttu-id="85443-312">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="85443-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="85443-313">Nel *Editor di Unity*, fare clic e trascinare il *ResultsLabel* classe la **script** cartella in cui la **Main Camera** oggetto nel  *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="85443-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="85443-314">Fare clic sui **Main Camera** ed esaminare le *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="85443-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="85443-315">Si noterà dallo script che è stato appena trascinato nella fotocamera, sono presenti due campi: **Cursore** e **etichettare Prefab**.</span><span class="sxs-lookup"><span data-stu-id="85443-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="85443-316">Trascinare l'oggetto chiamato **cursore** dalle *Pannello di gerarchia* allo slot denominato **cursore**, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="85443-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="85443-317">Trascinare l'oggetto chiamato **LabelText** dal *cartella Assets* nel *pannello progetto* allo slot denominato **etichetta Prefab**, come illustrato di immagine riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="85443-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Impostare gli obiettivi di riferimento all'interno di Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="85443-319">Capitolo 6: creare la classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="85443-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="85443-320">La classe successiva si intende creare è il *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="85443-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="85443-321">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="85443-321">This class is responsible for:</span></span>

-   <span data-ttu-id="85443-322">Acquisizione di un'immagine usando la fotocamera di HoloLens e archiviarlo nella cartella dell'App.</span><span class="sxs-lookup"><span data-stu-id="85443-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="85443-323">Movimenti tocco di acquisizione da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="85443-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="85443-324">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="85443-324">To create this class:</span></span> 

1.  <span data-ttu-id="85443-325">Andare alla **script** cartella creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="85443-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="85443-326">Pulsante destro del mouse all'interno della cartella **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="85443-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="85443-327">Chiamare lo script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="85443-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="85443-328">Fare doppio clic su nuova *ImageCapture* script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="85443-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="85443-329">Aggiungere spazi dei nomi seguenti all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="85443-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="85443-330">Quindi aggiungere le variabili seguenti all'interno di *ImageCapture* classe sopra il *Start ()* metodo:</span><span class="sxs-lookup"><span data-stu-id="85443-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="85443-331">Il **tapsCount** variabile archivieranno il numero di movimenti di tocco acquisiti da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="85443-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="85443-332">Questo numero viene usato nella denominazione delle immagini acquisite.</span><span class="sxs-lookup"><span data-stu-id="85443-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="85443-333">Codice per un *Awake()* e *Start ()* metodi deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="85443-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="85443-334">Questi verranno chiamati quando inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="85443-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="85443-335">Implementare un gestore che verrà chiamato quando si verifica un gesto tocco.</span><span class="sxs-lookup"><span data-stu-id="85443-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

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
 
<span data-ttu-id="85443-336">Il *TapHandler()* metodo incrementa il numero di elementi di ritardo acquisiti da parte dell'utente e utilizza la posizione del cursore corrente per determinare dove posizionare una nuova etichetta.</span><span class="sxs-lookup"><span data-stu-id="85443-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="85443-337">Questo metodo chiama quindi il *ExecuteImageCaptureAndAnalysis()* metodo per avviare le funzionalità principali di questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="85443-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="85443-338">Dopo aver acquisita un'immagine ed archiviata, i seguenti gestori verranno chiamati.</span><span class="sxs-lookup"><span data-stu-id="85443-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="85443-339">Se il processo ha esito positivo, il risultato viene passato per il *VisionManager* (che sono ancora da creare) per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="85443-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

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
 
9.  <span data-ttu-id="85443-340">Aggiungere quindi il metodo che l'applicazione usa per avviare il processo di acquisizione di immagini e archiviare l'immagine.</span><span class="sxs-lookup"><span data-stu-id="85443-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

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
> <span data-ttu-id="85443-341">A questo punto si noterà un errore dei *pannello della Console dell'Editor Unity*.</span><span class="sxs-lookup"><span data-stu-id="85443-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="85443-342">Infatti, il codice fa riferimento il *VisionManager* classe che verrà creato nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="85443-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="85443-343">Capitolo 7: chiamata ad Azure e analisi delle immagini</span><span class="sxs-lookup"><span data-stu-id="85443-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="85443-344">È l'ultimo script è necessario creare il *VisionManager* classe.</span><span class="sxs-lookup"><span data-stu-id="85443-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="85443-345">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="85443-345">This class is responsible for:</span></span>

-   <span data-ttu-id="85443-346">Il caricamento dell'immagine più recente acquisito come una matrice di byte.</span><span class="sxs-lookup"><span data-stu-id="85443-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="85443-347">Matrice di byte da inviare le *API visione artificiale di Azure* istanza del servizio per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="85443-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="85443-348">Ricezione della risposta come stringa JSON.</span><span class="sxs-lookup"><span data-stu-id="85443-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="85443-349">La deserializzazione della risposta e passando il tag risultante per il *ResultsLabel* classe.</span><span class="sxs-lookup"><span data-stu-id="85443-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="85443-350">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="85443-350">To create this class:</span></span>

1.  <span data-ttu-id="85443-351">Fare doppio clic sui **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="85443-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="85443-352">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="85443-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="85443-353">Denominare lo script *VisionManager*.</span><span class="sxs-lookup"><span data-stu-id="85443-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="85443-354">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85443-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="85443-355">Aggiornare gli spazi dei nomi affinché corrisponda al seguente, in cima il *VisionManager* classe:</span><span class="sxs-lookup"><span data-stu-id="85443-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="85443-356">Nella parte superiore dello script, *all'interno* le *VisionManager* classe (sopra il *Start ()* metodo), è ora necessario creare due *classi* che rappresenta la risposta JSON deserializzata da Azure:</span><span class="sxs-lookup"><span data-stu-id="85443-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

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
    > <span data-ttu-id="85443-357">Il *TagData* e *AnalysedObject* classi devono avere la *[System.Serializable]* attributo aggiunto prima della dichiarazione per poter essere deserializzati con Unity librerie.</span><span class="sxs-lookup"><span data-stu-id="85443-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="85443-358">Nella classe VisionManager, è necessario aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="85443-358">In the VisionManager class, you should add the following variables:</span></span>

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
    > <span data-ttu-id="85443-359">Assicurarsi di inserire le **Authentication Key** nel **authorizationKey** variabile.</span><span class="sxs-lookup"><span data-stu-id="85443-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="85443-360">Verrà annotati i **Authentication Key** all'inizio di questo corso [capitolo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="85443-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="85443-361">Il **visionAnalysisEndpoint** variabile potrebbe essere diverso da quello specificato in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="85443-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="85443-362">Il **west-us** rigorosamente fa riferimento alle istanze del servizio create per l'area Stati Uniti occidentali.</span><span class="sxs-lookup"><span data-stu-id="85443-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="85443-363">Aggiornarlo con il [URL dell'endpoint](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); di seguito sono riportati alcuni esempi di come potrebbe essere simile:</span><span class="sxs-lookup"><span data-stu-id="85443-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="85443-364">Europa occidentale: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="85443-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="85443-365">Asia sud-orientale: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="85443-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="85443-366">Australia orientale: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="85443-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="85443-367">Codice per Awake deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="85443-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="85443-368">Successivamente, aggiungere le coroutine (con il metodo statico flusso sotto di essa), che otterrà i risultati dell'analisi dell'immagine acquisita dal *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="85443-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

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

9.  <span data-ttu-id="85443-369">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="85443-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="85443-370">Indietro nell'Editor di Unity, fare clic e trascinare il *VisionManager* e *ImageCapture* classi il **script** cartella in cui il **Main Camera**dell'oggetto nel *Pannello di gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="85443-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="85443-371">Capitolo 8 – prima della compilazione</span><span class="sxs-lookup"><span data-stu-id="85443-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="85443-372">Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85443-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="85443-373">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="85443-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="85443-374">Tutte le impostazioni indicate nella [capitolo 2](#chapter-2--set-up-the-unity-project) siano impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="85443-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="85443-375">Tutti gli script associati per il **Main Camera** oggetto.</span><span class="sxs-lookup"><span data-stu-id="85443-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="85443-376">Tutti i campi di *Pannello controllo fotocamera principale* vengono assegnati in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="85443-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="85443-377">Assicurarsi di inserire le **Authentication Key** nel **authorizationKey** variabile.</span><span class="sxs-lookup"><span data-stu-id="85443-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="85443-378">Assicurarsi di aver anche selezionato l'endpoint *VisionManager* script e che si allinei alla *il* area (questo documento usa *west-us* per impostazione predefinita).</span><span class="sxs-lookup"><span data-stu-id="85443-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="85443-379">Capitolo 9: compilare la soluzione di piattaforma UWP e trasferire localmente l'applicazione</span><span class="sxs-lookup"><span data-stu-id="85443-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="85443-380">Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.</span><span class="sxs-lookup"><span data-stu-id="85443-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="85443-381">Passare a *impostazioni di compilazione* - **File > Impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="85443-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="85443-382">Dal *Build Settings* finestra, fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="85443-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="85443-384">Se non è già, graduazione **Unity C# progetti**.</span><span class="sxs-lookup"><span data-stu-id="85443-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="85443-385">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="85443-385">Click **Build**.</span></span> <span data-ttu-id="85443-386">Unity avvierà una *Esplora File* finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in.</span><span class="sxs-lookup"><span data-stu-id="85443-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="85443-387">Creare ora tale cartella e denominarlo *App*.</span><span class="sxs-lookup"><span data-stu-id="85443-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="85443-388">Quindi con il *App* cartella selezionata, premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="85443-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="85443-389">Unity verrà avviata la compilazione del progetto per la *App* cartella.</span><span class="sxs-lookup"><span data-stu-id="85443-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="85443-390">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un *Esplora File* finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).</span><span class="sxs-lookup"><span data-stu-id="85443-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="85443-391">Il capitolo 10-distribuire a HoloLens</span><span class="sxs-lookup"><span data-stu-id="85443-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="85443-392">Per distribuire in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="85443-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="85443-393">È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="85443-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="85443-394">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="85443-394">To do this:</span></span>

    1. <span data-ttu-id="85443-395">Durante l'uso di HoloLens, aprire il **impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="85443-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="85443-396">Passare a **rete e Internet > Wi-Fi > Opzioni avanzate**</span><span class="sxs-lookup"><span data-stu-id="85443-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="85443-397">Si noti il **IPv4** indirizzo.</span><span class="sxs-lookup"><span data-stu-id="85443-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="85443-398">Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza > per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="85443-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="85443-399">Attivare la modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="85443-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="85443-400">Passare alla nuova build Unity (le *App* cartella) e aprire il file di soluzione con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="85443-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="85443-401">Selezione configurazione di soluzione **Debug**.</span><span class="sxs-lookup"><span data-stu-id="85443-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="85443-402">La piattaforma della soluzione, selezionare **x86**, **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="85443-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="85443-404">Andare alla **dal menu Compila** e fare clic su **Distribuisci soluzione**, trasferire localmente l'applicazione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85443-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="85443-405">L'App deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="85443-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="85443-406">Per distribuire visore VR immersivi, impostare il **piattaforma soluzione** al *computer locale*e impostare il **configurazione** a *Debug*, con *x86* come la **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="85443-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="85443-407">Quindi distribuire in locale del computer, utilizzando il **dal menu Compila**, selezionando *Distribuisci soluzione*.</span><span class="sxs-lookup"><span data-stu-id="85443-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="85443-408">L'applicazione API visione artificiale completata</span><span class="sxs-lookup"><span data-stu-id="85443-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="85443-409">Complimenti, è stata compilata un'app per realtà mista che sfrutta l'API visione artificiale di Azure per riconoscere gli oggetti reali e visualizzare la fiducia di ciò che è stato individuato.</span><span class="sxs-lookup"><span data-stu-id="85443-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![risultato di Lab](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="85443-411">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="85443-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="85443-412">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="85443-412">Exercise 1</span></span>

<span data-ttu-id="85443-413">Esattamente come è stato usato il *tag* parametro (come evidenziato all'interno del *endpoint* utilizzati all'interno di *VisionManager*), estendere l'app per rilevare altre informazioni, esaminare quali altri parametri che è possibile utilizzare [qui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="85443-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="85443-414">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="85443-414">Exercise 2</span></span>

<span data-ttu-id="85443-415">Visualizzare i dati di Azure restituiti, in modo più colloquiale e leggibile, ad esempio nascondendo i numeri.</span><span class="sxs-lookup"><span data-stu-id="85443-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="85443-416">Come se un bot potrebbe essere riprodotta la voce all'utente.</span><span class="sxs-lookup"><span data-stu-id="85443-416">As though a bot might be speaking to the user.</span></span>
