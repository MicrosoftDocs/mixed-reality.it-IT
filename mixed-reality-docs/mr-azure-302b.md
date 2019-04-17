---
title: MR e 302b Azure - visione artificiale personalizzato
description: Completare questo corso per informazioni su come eseguire il training di un modello di machine learning e quindi usare il modello con training per riconoscere gli oggetti simili all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, visione artificiale personalizzato, hololens, coinvolgenti, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600002"
---
>[!NOTE]
><span data-ttu-id="74999-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="74999-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="74999-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="74999-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="74999-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="74999-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="74999-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="74999-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="74999-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="74999-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="74999-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="74999-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="74999-110">MR e 302b Azure: Servizio visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="74999-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="74999-111">In questo corso, si apprenderà come riconoscere personalizzato contenuto visivo all'interno di un'immagine fornita, usando le funzionalità di visione artificiale personalizzato di Azure in un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="74999-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="74999-112">Questo servizio consentirà di eseguire il training di un modello di machine learning usando immagini di oggetto.</span><span class="sxs-lookup"><span data-stu-id="74999-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="74999-113">Si utilizzerà il modello con training per riconoscere gli oggetti simili, come specificato dall'acquisizione della fotocamera del Microsoft HoloLens o una fotocamera connesso al PC per immersive auricolari (VR).</span><span class="sxs-lookup"><span data-stu-id="74999-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![risultato del corso](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="74999-115">Visione artificiale personalizzato di Azure è un servizio cognitivi di Microsoft che consente agli sviluppatori di compilare classificatori di immagini personalizzate.</span><span class="sxs-lookup"><span data-stu-id="74999-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="74999-116">Questi due classificatori sono quindi utilizzabile con nuove immagini per riconoscere o classificare, gli oggetti all'interno che la nuova immagine.</span><span class="sxs-lookup"><span data-stu-id="74999-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="74999-117">Il servizio offre un portale semplice, facile da usare, in linea per semplificare il processo.</span><span class="sxs-lookup"><span data-stu-id="74999-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="74999-118">Per altre informazioni, visitare il [pagina servizio visione artificiale personalizzato di Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="74999-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="74999-119">Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di funzionare in due modalità:</span><span class="sxs-lookup"><span data-stu-id="74999-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="74999-120">**Modalità analisi**: configurare il servizio visione artificiale personalizzato manualmente dal caricamento di immagini, la creazione di tag e il servizio di training per riconoscere i diversi oggetti (in questo caso mouse e tastiera).</span><span class="sxs-lookup"><span data-stu-id="74999-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="74999-121">Quindi si creerà un'app di HoloLens che acquisire immagini di uso della fotocamera e tenta di riconoscere tali oggetti nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="74999-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="74999-122">**Training modello**: si implementerà codice che consentirà una modalità"Training" nell'app.</span><span class="sxs-lookup"><span data-stu-id="74999-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="74999-123">La modalità di training consentirà di acquisire immagini di uso della fotocamera degli HoloLens, caricare le immagini acquisite nel servizio e il training del modello di visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="74999-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="74999-124">Questo corso ti spiegherà come ottenere i risultati dal servizio visione artificiale personalizzato in un'applicazione di esempio basate su Unity.</span><span class="sxs-lookup"><span data-stu-id="74999-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="74999-125">Sarà quindi compito è possibile applicare questi concetti a un'applicazione personalizzata, che potrebbe voler costruire.</span><span class="sxs-lookup"><span data-stu-id="74999-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="74999-126">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="74999-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="74999-127">Corso</span><span class="sxs-lookup"><span data-stu-id="74999-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="74999-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="74999-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="74999-129"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="74999-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="74999-130">MR e 302b Azure: Servizio visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="74999-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="74999-131">✔️</span><span class="sxs-lookup"><span data-stu-id="74999-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="74999-132">✔️</span><span class="sxs-lookup"><span data-stu-id="74999-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="74999-133">Questo corso è incentrato principalmente sulla HoloLens, è inoltre possibile applicare informazioni in questo corso per auricolari (VR) coinvolgenti di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="74999-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="74999-134">Poiché immersive auricolari (VR) non è accessibile fotocamere, sarà necessario una fotocamera esterna connessa al PC.</span><span class="sxs-lookup"><span data-stu-id="74999-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="74999-135">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare immersive auricolari (VR).</span><span class="sxs-lookup"><span data-stu-id="74999-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74999-136">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="74999-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="74999-137">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="74999-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="74999-138">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="74999-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="74999-139">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quanto elencato di seguito.</span><span class="sxs-lookup"><span data-stu-id="74999-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="74999-140">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="74999-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="74999-141">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="74999-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="74999-142">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="74999-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="74999-143">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="74999-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="74999-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="74999-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="74999-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="74999-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="74999-146">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="74999-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="74999-147">Una fotocamera connessa al PC (per lo sviluppo visore VR immersivi)</span><span class="sxs-lookup"><span data-stu-id="74999-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="74999-148">Accesso a Internet per la configurazione di Azure e il recupero delle API visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="74999-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="74999-149">Una serie di almeno cinque (5) immagini (dieci (10) consigliati) per ogni oggetto che si desidera venga riconosciuta dal servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="74999-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="74999-150">Se si desidera, è possibile usare [le immagini già fornite con questo corso (un mouse e tastiera) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="74999-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="74999-151">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="74999-151">Before you start</span></span>

1.  <span data-ttu-id="74999-152">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="74999-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="74999-153">Configurare e testare l'HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74999-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="74999-154">Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="74999-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="74999-155">È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova app per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente).</span><span class="sxs-lookup"><span data-stu-id="74999-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="74999-156">Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="74999-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="74999-157">Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="74999-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="74999-158">Capitolo 1 - portale del servizio visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="74999-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="74999-159">Usare la *servizio visione artificiale personalizzato* in Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="74999-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="74999-160">Prima di tutto [passare al *servizio visione artificiale personalizzato* pagina principale](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="74999-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="74999-161">Fare clic sui **iniziare a usare** pulsante.</span><span class="sxs-lookup"><span data-stu-id="74999-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="74999-162">Accedi per il *servizio visione artificiale personalizzato* portale.</span><span class="sxs-lookup"><span data-stu-id="74999-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="74999-163">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="74999-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="74999-164">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="74999-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="74999-165">Una volta che si sono connessi per la prima volta, verrà richiesto con la *Terms of Service* pannello.</span><span class="sxs-lookup"><span data-stu-id="74999-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="74999-166">Fare clic sulla casella di controllo per accettare le condizioni.</span><span class="sxs-lookup"><span data-stu-id="74999-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="74999-167">Quindi fare clic su **accetto**.</span><span class="sxs-lookup"><span data-stu-id="74999-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="74999-168">Avere accettato le condizioni, verrà reindirizzato il *progetti* sezione del portale.</span><span class="sxs-lookup"><span data-stu-id="74999-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="74999-169">Fare clic su **nuovo progetto**.</span><span class="sxs-lookup"><span data-stu-id="74999-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="74999-170">Verrà visualizzata una scheda sul lato destro, che verrà richiesto di specificare alcuni campi per il progetto.</span><span class="sxs-lookup"><span data-stu-id="74999-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="74999-171">Inserire un *nome* per il progetto.</span><span class="sxs-lookup"><span data-stu-id="74999-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="74999-172">Inserire un *Description* per il progetto (*facoltativo*).</span><span class="sxs-lookup"><span data-stu-id="74999-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="74999-173">Scegliere una *gruppo di risorse* o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="74999-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="74999-174">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="74999-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="74999-175">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="74999-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="74999-176">Impostare il *tipi di progetto* a **classificazione**</span><span class="sxs-lookup"><span data-stu-id="74999-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="74999-177">Impostare il *domini* come **generali**.</span><span class="sxs-lookup"><span data-stu-id="74999-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="74999-178">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="74999-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="74999-179">Dopo aver completato, fare clic su **Crea progetto**, si verrà reindirizzati al servizio visione artificiale personalizzato, pagina del progetto.</span><span class="sxs-lookup"><span data-stu-id="74999-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="74999-180">Capitolo 2 - Training il progetto di Custom Vision</span><span class="sxs-lookup"><span data-stu-id="74999-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="74999-181">Una volta nel portale di visione artificiale personalizzato, l'obiettivo principale è eseguire il training di progetto per riconoscere gli oggetti specifici nelle immagini.</span><span class="sxs-lookup"><span data-stu-id="74999-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="74999-182">È necessario almeno cinque (5) le immagini, anche se dieci (10) preferito, per ogni oggetto che si desidera riconoscere l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="74999-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="74999-183">[È possibile usare le immagini fornite con questo corso (un mouse e tastiera)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="74999-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="74999-184">Per eseguire il training il progetto di servizio visione artificiale personalizzato:</span><span class="sxs-lookup"><span data-stu-id="74999-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="74999-185">Fare clic sui **+** accanto alla **tag.**</span><span class="sxs-lookup"><span data-stu-id="74999-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="74999-186">Aggiungere il **nome** dell'oggetto da riconoscere.</span><span class="sxs-lookup"><span data-stu-id="74999-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="74999-187">Fare clic su **salvare**.</span><span class="sxs-lookup"><span data-stu-id="74999-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="74999-188">Si noterà il **Tag** è stato aggiunto (potrebbe essere necessario ricaricare la pagina affinché venga visualizzata).</span><span class="sxs-lookup"><span data-stu-id="74999-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="74999-189">Se non è già selezionata, fare clic con il nuovo tag, la casella di controllo.</span><span class="sxs-lookup"><span data-stu-id="74999-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="74999-190">Fare clic su **aggiungere immagini** al centro della pagina.</span><span class="sxs-lookup"><span data-stu-id="74999-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="74999-191">Fare clic su **Esplora file locali**e di ricerca, quindi selezionare, le immagini da caricare, dove il minimo è cinque (5).</span><span class="sxs-lookup"><span data-stu-id="74999-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="74999-192">Tenere presente che tutte queste immagini deve contenere l'oggetto che è set di training.</span><span class="sxs-lookup"><span data-stu-id="74999-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="74999-193">È possibile selezionare numerose immagini alla volta, da caricare.</span><span class="sxs-lookup"><span data-stu-id="74999-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="74999-194">Dopo che è possibile visualizzare le immagini nella scheda, selezionare i tag appropriati nel **contrassegni** casella.</span><span class="sxs-lookup"><span data-stu-id="74999-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="74999-195">Fare clic su **caricare i file**.</span><span class="sxs-lookup"><span data-stu-id="74999-195">Click on **Upload files**.</span></span> <span data-ttu-id="74999-196">I file verranno avviato il caricamento.</span><span class="sxs-lookup"><span data-stu-id="74999-196">The files will begin uploading.</span></span> <span data-ttu-id="74999-197">Dopo aver conferma del caricamento, fare clic su **fatto**</span><span class="sxs-lookup"><span data-stu-id="74999-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="74999-198">Ripetere lo stesso processo per creare una nuova **Tag** denominate **tastiera** e caricare le foto appropriate per tale.</span><span class="sxs-lookup"><span data-stu-id="74999-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="74999-199">Verificare di aver **deselezionare l'opzione** *Mouse* dopo aver creato i nuovi tag, pertanto, per visualizzare il *aggiungere immagini* finestra.</span><span class="sxs-lookup"><span data-stu-id="74999-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="74999-200">Dopo aver creato entrambe tag configurato, fare clic su **Train**, e avvierà la compilazione della prima iterazione di training.</span><span class="sxs-lookup"><span data-stu-id="74999-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="74999-201">Una volta creato, sarà possibile visualizzare due pulsanti chiamati **predefinito** e **stima URL**.</span><span class="sxs-lookup"><span data-stu-id="74999-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="74999-202">Fare clic su **predefinito** prima di tutto, quindi fare clic su **stima URL**.</span><span class="sxs-lookup"><span data-stu-id="74999-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="74999-203">L'URL dell'endpoint che viene fornito da questo, è impostato su qualunque *iterazione* è stata contrassegnata come predefinita.</span><span class="sxs-lookup"><span data-stu-id="74999-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="74999-204">Pertanto, se si apportata in un secondo momento una nuova *iterazione* e aggiornarlo come impostazione predefinita, non è necessario modificare il codice.</span><span class="sxs-lookup"><span data-stu-id="74999-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="74999-205">Dopo avere fatto clic su *URL di stima*, aprire *blocco note*e copiare e incollare il **URL** e il **stima-Key**, in modo che sia possibile recuperarlo quando ti serve in un secondo momento nel codice.</span><span class="sxs-lookup"><span data-stu-id="74999-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="74999-206">Fare clic sui **rappresenta dalla ruota dentata** nella parte superiore destra della schermata.</span><span class="sxs-lookup"><span data-stu-id="74999-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="74999-207">Copia il **chiave di formazione** e incollarlo in una *Notepad*, per un uso successivo.</span><span class="sxs-lookup"><span data-stu-id="74999-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="74999-208">Copiare anche il **Id progetto**e anche incollarlo nel *Notepad* file, per un uso successivo.</span><span class="sxs-lookup"><span data-stu-id="74999-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="74999-209">Capitolo 3 - configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="74999-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="74999-210">Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="74999-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="74999-211">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="74999-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="74999-212">A questo punto, è necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="74999-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="74999-213">Inserisci **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="74999-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="74999-214">Verificare che il modello di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="74999-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="74999-215">Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="74999-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="74999-216">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="74999-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="74999-217">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74999-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="74999-218">Passare a **modificare* > *preferenze** e quindi dalla nuova finestra, passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="74999-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="74999-219">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="74999-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="74999-220">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="74999-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="74999-221">Passare quindi ad **File > Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sui **commutatore piattaforma** pulsante per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="74999-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="74999-222">Mentre si trovano ancora nella **File > Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="74999-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="74999-223">**Dispositivo di destinazione** è impostata su **Hololens**</span><span class="sxs-lookup"><span data-stu-id="74999-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="74999-224">Per le cuffie coinvolgenti, impostare **dispositivo di destinazione** al *qualsiasi dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="74999-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="74999-225">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="74999-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="74999-226">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="74999-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="74999-227">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="74999-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="74999-228">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="74999-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="74999-229">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="74999-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="74999-230">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="74999-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="74999-231">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="74999-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="74999-232">Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="74999-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="74999-233">Aprire appena creato **scene** cartella e quindi il *nome File:* campo di testo, digitare **CustomVisionScene**, quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="74999-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="74999-234">Tenere presente, è necessario salvare le scene di Unity all'interno di *asset* cartella, come devono essere associate al progetto di Unity.</span><span class="sxs-lookup"><span data-stu-id="74999-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="74999-235">Creare la cartella scene (e altre simili) è un modo tipico strutturare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="74999-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="74999-236">Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="74999-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="74999-237">Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.</span><span class="sxs-lookup"><span data-stu-id="74999-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="74999-238">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="74999-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="74999-239">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="74999-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="74999-240">**Versione del Runtime di scripting** deve essere **Experimental (.NET 4.6 equivalente)**, che attiverà una necessità di riavviare l'Editor.</span><span class="sxs-lookup"><span data-stu-id="74999-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="74999-241">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="74999-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="74999-242">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="74999-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="74999-243">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="74999-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="74999-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="74999-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="74999-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="74999-245">**Webcam**</span></span>

        3. <span data-ttu-id="74999-246">**Microfono**</span><span class="sxs-lookup"><span data-stu-id="74999-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="74999-247">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="74999-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="74999-248">Nuovamente in *Build Settings* *Unity C\# progetti* non è non è più in grigio, selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="74999-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="74999-249">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="74999-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="74999-250">Salvare la scena e il progetto (**FILE > Salva scena / FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="74999-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="74999-251">Capitolo 4 - importare la DLL Newtonsoft in Unity</span><span class="sxs-lookup"><span data-stu-id="74999-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74999-252">Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [MR-Azure-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importarlo nel progetto come un [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 6](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="74999-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="74999-253">Questo corso è necessario utilizzare il **Newtonsoft** libreria, che è possibile aggiungere come una DLL agli asset.</span><span class="sxs-lookup"><span data-stu-id="74999-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="74999-254">Il pacchetto che contiene [questa libreria può essere scaricata da questo collegamento](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="74999-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="74999-255">Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornita con questo corso.</span><span class="sxs-lookup"><span data-stu-id="74999-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="74999-256">Aggiungere il *.unitypackage* Unity tramite il **asset* > *importazione* *pacchetto*  >  *Custom* *pacchetto** l'opzione di menu.</span><span class="sxs-lookup"><span data-stu-id="74999-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="74999-257">Nel **Importa pacchetto Unity** scatola viene, assicurarsi che tutto ciò che in (e tra cui) **plug-in** sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="74999-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="74999-258">Scegliere il **importazione** pulsante per aggiungere elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="74999-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="74999-259">Andare alla **Newtonsoft** cartella sotto **plug-in** nella visualizzazione del progetto e selezionare il *plug-in di newtonsoft. JSON*.</span><span class="sxs-lookup"><span data-stu-id="74999-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="74999-260">Con il *plug-in di newtonsoft. JSON* selezionato, assicurarsi che **Any Platform** viene **unchecked**, quindi verificare che **WSAPlayer** è anche **unchecked**, quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="74999-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="74999-261">Si tratta semplicemente di confermare che i file siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="74999-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="74999-262">Contrassegnare questi plug-in Configura perché possano essere usati solo nell'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="74999-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="74999-263">Sono presenti un set diverso di esse nella cartella WSA che verrà usato dopo che il progetto viene esportato da Unity.</span><span class="sxs-lookup"><span data-stu-id="74999-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="74999-264">Successivamente, è necessario aprire la **WSA** cartella, all'interno di **Newtonsoft** cartella.</span><span class="sxs-lookup"><span data-stu-id="74999-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="74999-265">Si noterà una copia dello stesso file che appena configurato.</span><span class="sxs-lookup"><span data-stu-id="74999-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="74999-266">Selezionare il file e quindi nella finestra di ispezione, assicurarsi che</span><span class="sxs-lookup"><span data-stu-id="74999-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="74999-267">**Qualsiasi piattaforma** è **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="74999-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="74999-268">**solo** **WSAPlayer** è **selezionata**</span><span class="sxs-lookup"><span data-stu-id="74999-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="74999-269">**Non elaborare** è **selezionata**</span><span class="sxs-lookup"><span data-stu-id="74999-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="74999-270">Capitolo 5 - impostazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="74999-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="74999-271">Nel Pannello di gerarchia, selezionare la *Main Camera*.</span><span class="sxs-lookup"><span data-stu-id="74999-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="74999-272">Una volta selezionata, sarà possibile visualizzare tutti i componenti del *Main Camera* nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="74999-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="74999-273">Il *fotocamera* nome oggetto deve essere **Main Camera** (si noti l'ortografici!)</span><span class="sxs-lookup"><span data-stu-id="74999-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="74999-274">Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici!)</span><span class="sxs-lookup"><span data-stu-id="74999-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="74999-275">Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="74999-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="74999-276">Impostare **Cancella flag** al **colore a tinta unita** (ignorare questo visore VR immersivi).</span><span class="sxs-lookup"><span data-stu-id="74999-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="74999-277">Impostare il **sfondo** colore della fotocamera componente **nero, Alpha 0 (codice esadecimale: #00000000)** (ignorare questo visore VR immersivi).</span><span class="sxs-lookup"><span data-stu-id="74999-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="74999-278">Capitolo 6: creare la classe CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="74999-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="74999-279">A questo punto si è pronti a scrivere codice.</span><span class="sxs-lookup"><span data-stu-id="74999-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="74999-280">Inizierà con la *CustomVisionAnalyser* classe.</span><span class="sxs-lookup"><span data-stu-id="74999-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="74999-281">Le chiamate per il **servizio visione artificiale personalizzato** apportate al codice illustrato di seguito vengono effettuate tramite il **API REST di Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="74999-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="74999-282">Tramite l'utilizzo, verrà visualizzato come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile per conto proprio).</span><span class="sxs-lookup"><span data-stu-id="74999-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="74999-283">Tenere presente, che Microsoft mette a disposizione un **SDK del servizio visione artificiale personalizzato** che può essere utilizzato anche per effettuare chiamate al servizio.</span><span class="sxs-lookup"><span data-stu-id="74999-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="74999-284">Per altre informazioni, vedere la [SDK del servizio visione artificiale personalizzato](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) articolo.</span><span class="sxs-lookup"><span data-stu-id="74999-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="74999-285">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="74999-285">This class is responsible for:</span></span>

-   <span data-ttu-id="74999-286">Il caricamento dell'immagine più recente acquisito come una matrice di byte.</span><span class="sxs-lookup"><span data-stu-id="74999-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="74999-287">Invia la matrice di byte per Azure *servizio visione artificiale personalizzato* istanza per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="74999-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="74999-288">Ricezione della risposta come stringa JSON.</span><span class="sxs-lookup"><span data-stu-id="74999-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="74999-289">La deserializzazione della risposta e passando l'oggetto risultante *Prediction* per il *SceneOrganiser* classe, che si occuperà di modalità di visualizzazione nella risposta.</span><span class="sxs-lookup"><span data-stu-id="74999-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="74999-290">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74999-290">To create this class:</span></span>

1.  <span data-ttu-id="74999-291">Fare doppio clic nella *cartella Asset* che si trova nel *pannello progetto*, quindi fare clic su **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="74999-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="74999-292">Chiamare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="74999-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="74999-293">Fare doppio clic sulla cartella appena creata, per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="74999-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="74999-294">Fare doppio clic all'interno della cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="74999-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="74999-295">Denominare lo script *CustomVisionAnalyser*.</span><span class="sxs-lookup"><span data-stu-id="74999-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="74999-296">Fare doppio clic su nuova *CustomVisionAnalyser* script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74999-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="74999-297">Aggiornare gli spazi dei nomi nella parte superiore del file per corrispondere a quanto segue:</span><span class="sxs-lookup"><span data-stu-id="74999-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="74999-298">Nel *CustomVisionAnalyser* classe, aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="74999-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

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
    > <span data-ttu-id="74999-299">Assicurarsi di inserire le **chiave stima** nel **predictionKey** variabile e il **stima Endpoint** nel **predictionEndpoint** variabile.</span><span class="sxs-lookup"><span data-stu-id="74999-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="74999-300">È stato copiato al *Notepad* più indietro in corso.</span><span class="sxs-lookup"><span data-stu-id="74999-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="74999-301">Codice per un **Awake()** deve ora essere aggiunto per inizializzare la variabile di istanza:</span><span class="sxs-lookup"><span data-stu-id="74999-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="74999-302">Eliminare i metodi **Start ()** e **Update ()**.</span><span class="sxs-lookup"><span data-stu-id="74999-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="74999-303">Successivamente, aggiungere le coroutine (con il metodo statico **GetImageAsByteArray()** metodo sotto di essa), che otterranno i risultati dell'analisi dell'immagine acquisita dalle *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="74999-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="74999-304">Nel **AnalyseImageCapture** coroutine, viene eseguita una chiamata ai *SceneOrganiser* classe che è ancora da creare.</span><span class="sxs-lookup"><span data-stu-id="74999-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="74999-305">Pertanto **lasciarli impostata come commento le righe per il momento**.</span><span class="sxs-lookup"><span data-stu-id="74999-305">Therefore, **leave those lines commented for now**.</span></span>

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

10.  <span data-ttu-id="74999-306">Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="74999-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="74999-307">Capitolo 7 - creare la classe CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="74999-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="74999-308">La classe si creerà ora è il *CustomVisionObjects* classe.</span><span class="sxs-lookup"><span data-stu-id="74999-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="74999-309">Questo script contiene un numero di oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate per la *servizio visione artificiale personalizzato*.</span><span class="sxs-lookup"><span data-stu-id="74999-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="74999-310">È importante che prendere nota dell'endpoint a cui il servizio visione artificiale personalizzato fornisce, come il codice JSON seguente struttura è stata configurata per lavorare con [ *v2.0 di Custom Vision stima*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="74999-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="74999-311">Se si dispone di una versione diversa, si potrebbe essere necessario aggiornare la seguente struttura.</span><span class="sxs-lookup"><span data-stu-id="74999-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="74999-312">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74999-312">To create this class:</span></span>

1.  <span data-ttu-id="74999-313">Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="74999-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="74999-314">Chiamare lo script *CustomVisionObjects*.</span><span class="sxs-lookup"><span data-stu-id="74999-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="74999-315">Fare doppio clic su nuova **CustomVisionObjects** script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74999-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="74999-316">Aggiungere spazi dei nomi seguenti all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="74999-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="74999-317">Eliminare il **Start ()** e **Update ()** metodi all'interno di *CustomVisionObjects* classe; questa classe dovrebbe ora essere vuota.</span><span class="sxs-lookup"><span data-stu-id="74999-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="74999-318">Aggiungere le classi seguenti **fuori** le *CustomVisionObjects* classe.</span><span class="sxs-lookup"><span data-stu-id="74999-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="74999-319">Questi oggetti vengono utilizzati per il *Newtonsoft* libreria per serializzare e deserializzare i dati di risposta:</span><span class="sxs-lookup"><span data-stu-id="74999-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="74999-320">Capitolo 8 - creare la classe VoiceRecognizer</span><span class="sxs-lookup"><span data-stu-id="74999-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="74999-321">Questa classe riconosceranno l'input vocale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="74999-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="74999-322">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74999-322">To create this class:</span></span>

1.  <span data-ttu-id="74999-323">Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="74999-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="74999-324">Chiamare lo script *VoiceRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="74999-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="74999-325">Fare doppio clic su nuova **VoiceRecognizer** script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74999-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="74999-326">Aggiungere gli spazi dei nomi seguenti sopra la *VoiceRecognizer* classe:</span><span class="sxs-lookup"><span data-stu-id="74999-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="74999-327">Quindi aggiungere le variabili seguenti all'interno di *VoiceRecognizer* classe sopra il *Start ()* metodo:</span><span class="sxs-lookup"><span data-stu-id="74999-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

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

5.  <span data-ttu-id="74999-328">Aggiungere il **Awake()** e **Start ()** metodi, l'utente verrà impostato il secondo dei quali *parole chiave* per essere riconosciuti durante l'associazione di un tag di un'immagine:</span><span class="sxs-lookup"><span data-stu-id="74999-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

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

6.  <span data-ttu-id="74999-329">Eliminare il **Update ()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="74999-330">Aggiungere il gestore seguente, che viene chiamato ogni volta che viene riconosciuto input vocale:</span><span class="sxs-lookup"><span data-stu-id="74999-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

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

8.  <span data-ttu-id="74999-331">Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="74999-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="74999-332">Non preoccuparsi di codice che può sembrare un errore, come si fornirà ulteriori classi presto, risolvere questi.</span><span class="sxs-lookup"><span data-stu-id="74999-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="74999-333">Capitolo 9 - creare la classe CustomVisionTrainer</span><span class="sxs-lookup"><span data-stu-id="74999-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="74999-334">Questa classe verrà concatenare una serie di chiamate web per eseguire il training di *servizio visione artificiale personalizzato*.</span><span class="sxs-lookup"><span data-stu-id="74999-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="74999-335">Ogni chiamata verrà descritta in dettaglio immediatamente sopra il codice.</span><span class="sxs-lookup"><span data-stu-id="74999-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="74999-336">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74999-336">To create this class:</span></span>

1.  <span data-ttu-id="74999-337">Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="74999-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="74999-338">Chiamare lo script *CustomVisionTrainer*.</span><span class="sxs-lookup"><span data-stu-id="74999-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="74999-339">Fare doppio clic su nuova *CustomVisionTrainer* script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74999-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="74999-340">Aggiungere gli spazi dei nomi seguenti sopra la *CustomVisionTrainer* classe:</span><span class="sxs-lookup"><span data-stu-id="74999-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="74999-341">Quindi aggiungere le variabili seguenti all'interno di *CustomVisionTrainer* classe, sopra la **Start ()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="74999-342">L'URL di training usata in questo esempio viene fornito all'interno di *1.2 di Custom Vision Training* documentazione, e ha una struttura di: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="74999-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="74999-343">Per altre informazioni, visitare il [ *API di riferimento di Training di Custom Vision v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="74999-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="74999-344">È importante che prendere nota dell'endpoint a cui il servizio visione artificiale personalizzato offre la modalità di training, come la struttura JSON usata (all'interno di **CustomVisionObjects** classe) è stato configurato per lavorare con [  *Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="74999-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="74999-345">Se si dispone di una versione diversa, si potrebbe essere necessario aggiornare il *oggetti* struttura.</span><span class="sxs-lookup"><span data-stu-id="74999-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

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
    > <span data-ttu-id="74999-346">Assicurarsi di aggiungere il **chiave di servizio** valore (chiave di Training) e **Id progetto** valore, che si è preso nota precedente; questi sono i valori si [raccolti dal portale in precedenza nel corso ( Capitolo 2, vedere il passaggio 10 e versioni successive)](#chapter-2---training-your-custom-vision-oroject).</span><span class="sxs-lookup"><span data-stu-id="74999-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="74999-347">Aggiungere il codice seguente **Start ()** e **Awake()** metodi.</span><span class="sxs-lookup"><span data-stu-id="74999-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="74999-348">Questi metodi vengono chiamati durante l'inizializzazione e contengono la chiamata per impostare l'interfaccia utente:</span><span class="sxs-lookup"><span data-stu-id="74999-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

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

6.  <span data-ttu-id="74999-349">Eliminare il **Update ()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-349">Delete the **Update()** method.</span></span> <span data-ttu-id="74999-350">Questa classe sarà non necessario.</span><span class="sxs-lookup"><span data-stu-id="74999-350">This class will not need it.</span></span>

7.  <span data-ttu-id="74999-351">Aggiungere il **RequestTagSelection()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="74999-352">Questo metodo è il primo a essere chiamato quando un'immagine acquisita e archiviata nel dispositivo ed è ora pronto per essere inviato per la *servizio visione artificiale personalizzato*per sottoporlo a training.</span><span class="sxs-lookup"><span data-stu-id="74999-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="74999-353">Questo metodo visualizza i corsi di formazione dell'interfaccia utente, un set di parole chiave che l'utente può usare per contrassegnare l'immagine acquisita.</span><span class="sxs-lookup"><span data-stu-id="74999-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="74999-354">Avvisa anche il *VoiceRecognizer* classe per iniziare l'ascolto per l'utente per l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="74999-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="74999-355">Aggiungere il **VerifyTag()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="74999-356">Questo metodo riceverà l'input vocale riconosciuto dal **VoiceRecognizer** classe e verificare la validità e quindi avviare il processo di training.</span><span class="sxs-lookup"><span data-stu-id="74999-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

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

9.  <span data-ttu-id="74999-357">Aggiungere il **SubmitImageForTraining()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="74999-358">Questo metodo inizierà il processo di training del servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="74999-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="74999-359">Il primo passaggio consiste nel recuperare la **l'Id di Tag** dal servizio di cui è associato l'input vocale convalidato da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="74999-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="74999-360">Il **l'Id di Tag** verrà quindi caricato insieme all'immagine.</span><span class="sxs-lookup"><span data-stu-id="74999-360">The **Tag Id** will then be uploaded along with the image.</span></span>

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

10. <span data-ttu-id="74999-361">Aggiungere il **TrainCustomVisionProject()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="74999-362">Una volta che l'immagine ha inviato e contrassegnata, questo metodo verrà chiamato.</span><span class="sxs-lookup"><span data-stu-id="74999-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="74999-363">Verrà creata una nuova iterazione che verrà eseguito il training con tutte le immagini precedente inviate al servizio più l'immagine appena caricato.</span><span class="sxs-lookup"><span data-stu-id="74999-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="74999-364">Dopo aver completato il training, questo metodo chiamerà un metodo per impostare l'oggetto appena creato **iterazione** come **predefinito**, in modo che l'endpoint si usa per l'analisi è l'ultima iterazione sottoposto a training.</span><span class="sxs-lookup"><span data-stu-id="74999-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

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

11. <span data-ttu-id="74999-365">Aggiungere il **SetDefaultIteration()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="74999-366">Questo metodo verrà impostato l'iterazione precedentemente creato e sottoposto a training come *predefinito*.</span><span class="sxs-lookup"><span data-stu-id="74999-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="74999-367">Al termine, questo metodo dovrà eliminare iterazione precedente esistente nel servizio.</span><span class="sxs-lookup"><span data-stu-id="74999-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="74999-368">Al momento della stesura di questo corso, è previsto un limite di un numero massimo dieci (10) di iterazioni possono esistere contemporaneamente nel servizio.</span><span class="sxs-lookup"><span data-stu-id="74999-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

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

12. <span data-ttu-id="74999-369">Aggiungere il **DeletePreviousIteration()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="74999-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="74999-370">Questo metodo verrà trovare ed eliminare iterazione precedente non predefinita:</span><span class="sxs-lookup"><span data-stu-id="74999-370">This method will find and delete the previous non-default iteration:</span></span>

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

13. <span data-ttu-id="74999-371">L'ultimo metodo da aggiungere in questa classe è il **GetImageAsByteArray()** metodo, utilizzata per il web le chiamate per convertire l'immagine acquisita in una matrice di byte.</span><span class="sxs-lookup"><span data-stu-id="74999-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

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

14. <span data-ttu-id="74999-372">Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="74999-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="74999-373">Capitolo 10 - creare la classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="74999-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="74999-374">Questa classe sarà:</span><span class="sxs-lookup"><span data-stu-id="74999-374">This class will:</span></span>

-   <span data-ttu-id="74999-375">Creare un **cursore** oggetto da connettere alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="74999-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="74999-376">Creare un **etichetta** oggetto che verrà visualizzato quando il servizio riconosca gli oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="74999-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="74999-377">Configurare la fotocamera principale collegando i componenti appropriati a esso.</span><span class="sxs-lookup"><span data-stu-id="74999-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="74999-378">Se si **modalità analisi**, le etichette in fase di esecuzione nello spazio complessivo appropriato rispetto alla posizione della fotocamera principale, generare e visualizzare i dati ricevuti dal servizio visione artificiale personalizzato.</span><span class="sxs-lookup"><span data-stu-id="74999-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="74999-379">Se si **modalità di Training**, generare l'interfaccia utente che visualizzerà le diverse fasi del processo di training.</span><span class="sxs-lookup"><span data-stu-id="74999-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="74999-380">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74999-380">To create this class:</span></span>

1.  <span data-ttu-id="74999-381">Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="74999-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="74999-382">Denominare lo script *SceneOrganiser*.</span><span class="sxs-lookup"><span data-stu-id="74999-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="74999-383">Fare doppio clic su nuova *SceneOrganiser* script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74999-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="74999-384">È sufficiente uno spazio dei nomi, rimuovere gli altri dall'esempio precedente il *SceneOrganiser* classe:</span><span class="sxs-lookup"><span data-stu-id="74999-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="74999-385">Quindi aggiungere le variabili seguenti all'interno di *SceneOrganiser* classe sopra il **Start ()** metodo:</span><span class="sxs-lookup"><span data-stu-id="74999-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="74999-386">Eliminare il **Start ()** e **Update ()** metodi.</span><span class="sxs-lookup"><span data-stu-id="74999-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="74999-387">A destra sotto le variabili, aggiungere il **Awake()** (metodo), che consente di inizializzare la classe e impostare la scena.</span><span class="sxs-lookup"><span data-stu-id="74999-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="74999-388">A questo punto aggiungere il **CreateCameraCursor()** metodo che crea e posiziona il cursore Main Camera, e il **CreateLabel()** metodo, che consente di creare la **etichetta analisi** oggetto .</span><span class="sxs-lookup"><span data-stu-id="74999-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

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

8. <span data-ttu-id="74999-389">Aggiungere il **SetCameraStatus()** metodo che gestirà i messaggi destinati per la rete mesh di testo che fornisce lo stato della camera.</span><span class="sxs-lookup"><span data-stu-id="74999-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

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

9. <span data-ttu-id="74999-390">Aggiungere il **PlaceAnalysisLabel()** e **SetTagsToLastLabel()** metodi, che consente di generare e visualizzare i dati dal servizio visione artificiale personalizzato nella scena.</span><span class="sxs-lookup"><span data-stu-id="74999-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

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

10. <span data-ttu-id="74999-391">Infine, aggiungere il **CreateTrainingUI()** metodo, che distribuirà l'interfaccia utente di visualizzare le fasi del processo di training più quando l'applicazione è in modalità di Training.</span><span class="sxs-lookup"><span data-stu-id="74999-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="74999-392">Questo metodo verrà inoltre essere sfruttato per creare l'oggetto di stato della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="74999-392">This method will also be harnessed to create the camera status object.</span></span>

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

11. <span data-ttu-id="74999-393">Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="74999-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74999-394">Prima di continuare, aprire il **CustomVisionAnalyser** (classe) e all'interno di **AnalyseLastImageCaptured()** metodo *rimuovere il commento* le righe seguenti:</span><span class="sxs-lookup"><span data-stu-id="74999-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="74999-395">Capitolo 11 - creare la classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="74999-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="74999-396">La classe successiva si intende creare è il *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="74999-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="74999-397">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="74999-397">This class is responsible for:</span></span>

-   <span data-ttu-id="74999-398">Acquisizione di un'immagine usando la fotocamera di HoloLens e archiviandolo nel *App* cartella.</span><span class="sxs-lookup"><span data-stu-id="74999-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="74999-399">Gestione di movimenti di tocco da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="74999-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="74999-400">Mantenendo il *Enum* valore che determina se l'applicazione verrà eseguita *Analysis* modalità oppure *Training* modalità.</span><span class="sxs-lookup"><span data-stu-id="74999-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="74999-401">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="74999-401">To create this class:</span></span>

1.  <span data-ttu-id="74999-402">Andare alla **script** cartella creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="74999-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="74999-403">Fare doppio clic all'interno della cartella, quindi fare clic su **Crea > C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="74999-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="74999-404">Denominare lo script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="74999-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="74999-405">Fare doppio clic su nuova **ImageCapture** script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74999-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="74999-406">Sostituire gli spazi dei nomi nella parte superiore del file con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="74999-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="74999-407">Quindi aggiungere le variabili seguenti all'interno di *ImageCapture* classe sopra il **Start ()** metodo:</span><span class="sxs-lookup"><span data-stu-id="74999-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="74999-408">Codice per un **Awake()** e **Start ()** metodi deve ora essere aggiunto:</span><span class="sxs-lookup"><span data-stu-id="74999-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="74999-409">Implementare un gestore che verrà chiamato quando si verifica un gesto tocco.</span><span class="sxs-lookup"><span data-stu-id="74999-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

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
    > <span data-ttu-id="74999-410">Nelle *Analysis* modalità, il **TapHandler** metodo funge da opzione per avviare o interrompere il ciclo di acquisizione di foto.</span><span class="sxs-lookup"><span data-stu-id="74999-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="74999-411">Nelle *Training* modalità, consente di acquisire un'immagine dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="74999-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="74999-412">Quando il cursore è verde, significa che la fotocamera è disponibile per acquisire l'immagine.</span><span class="sxs-lookup"><span data-stu-id="74999-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="74999-413">Quando il cursore è rosso, significa che la fotocamera è occupata.</span><span class="sxs-lookup"><span data-stu-id="74999-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="74999-414">Aggiungere il metodo che l'applicazione usa per avviare il processo di acquisizione di immagini e archiviare l'immagine.</span><span class="sxs-lookup"><span data-stu-id="74999-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

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

9.  <span data-ttu-id="74999-415">Aggiungere i gestori che verranno chiamati quando è stata acquisita la foto e quando è pronto per essere analizzati.</span><span class="sxs-lookup"><span data-stu-id="74999-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="74999-416">Il risultato viene quindi passato per il *CustomVisionAnalyser* o il *CustomVisionTrainer* a seconda di quale modalità è nastavit il codice.</span><span class="sxs-lookup"><span data-stu-id="74999-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

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

10. <span data-ttu-id="74999-417">Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="74999-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="74999-418">Ora che sono stati completati tutti gli script, tornare indietro nell'Editor di Unity, quindi fare clic e trascinare il **SceneOrganiser** classe la **script** cartella per il **Main Camera** oggetto di *gerarchia pannello*.</span><span class="sxs-lookup"><span data-stu-id="74999-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="74999-419">Capitolo 12 - prima della compilazione</span><span class="sxs-lookup"><span data-stu-id="74999-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="74999-420">Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74999-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="74999-421">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="74999-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="74999-422">Tutte le impostazioni indicate nella [capitolo 2](#chapter-2---training-your-custom-vision-project) siano impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="74999-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="74999-423">Tutti i campi di **Main Camera**, pannello di controllo, vengono assegnate in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="74999-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="74999-424">Lo script **SceneOrganiser** è collegato il **Main Camera** oggetto.</span><span class="sxs-lookup"><span data-stu-id="74999-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="74999-425">Assicurarsi di inserire le **chiave di stima** nel **predictionKey** variabile.</span><span class="sxs-lookup"><span data-stu-id="74999-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="74999-426">Sono stati inseriti i **Endpoint di stima** nel **predictionEndpoint** variabile.</span><span class="sxs-lookup"><span data-stu-id="74999-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="74999-427">Sono stati inseriti i **chiave di formazione** nel **trainingKey** variabile, del *CustomVisionTrainer* classe.</span><span class="sxs-lookup"><span data-stu-id="74999-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="74999-428">Sono stati inseriti i **ID progetto** nel **projectId** variabile, del *CustomVisionTrainer* classe.</span><span class="sxs-lookup"><span data-stu-id="74999-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="74999-429">Capitolo 13 - compilazione e trasferire localmente l'applicazione</span><span class="sxs-lookup"><span data-stu-id="74999-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="74999-430">Per avviare il *compilazione* processo:</span><span class="sxs-lookup"><span data-stu-id="74999-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="74999-431">Passare a **File > Impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="74999-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="74999-432">Segni di graduazione **Unity C\# progetti**.</span><span class="sxs-lookup"><span data-stu-id="74999-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="74999-433">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="74999-433">Click **Build**.</span></span> <span data-ttu-id="74999-434">Unity avvierà una **Esplora File** finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in.</span><span class="sxs-lookup"><span data-stu-id="74999-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="74999-435">Creare ora tale cartella e denominarlo **App**.</span><span class="sxs-lookup"><span data-stu-id="74999-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="74999-436">Quindi con il **App** cartella selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="74999-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="74999-437">Unity verrà avviata la compilazione del progetto per la **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="74999-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="74999-438">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).</span><span class="sxs-lookup"><span data-stu-id="74999-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="74999-439">Per distribuire in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="74999-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="74999-440">È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="74999-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="74999-441">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="74999-441">To do this:</span></span>

    1.  <span data-ttu-id="74999-442">Durante l'uso di HoloLens, aprire il **impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="74999-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="74999-443">Passare a **rete e Internet** > **Wi-Fi** > **opzioni avanzate**</span><span class="sxs-lookup"><span data-stu-id="74999-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="74999-444">Si noti il **IPv4** indirizzo.</span><span class="sxs-lookup"><span data-stu-id="74999-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="74999-445">Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza** > **per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="74999-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="74999-446">Impostare **modalità sviluppatore su**.</span><span class="sxs-lookup"><span data-stu-id="74999-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="74999-447">Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="74999-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="74999-448">Nel *configurazione della soluzione* selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="74999-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="74999-449">Nel *piattaforma soluzione*, selezionare **x86, computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="74999-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="74999-450">Verrà richiesto di inserire le **indirizzo IP** di un dispositivo remoto (il HoloLens, in questo caso, che si è preso nota).</span><span class="sxs-lookup"><span data-stu-id="74999-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="74999-451">Passare a **compilare** dal menu e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="74999-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="74999-452">L'app deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="74999-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="74999-453">Per distribuire visore VR immersivi, impostare il **piattaforma soluzione** al *computer locale*e impostare il **configurazione** a *Debug*, con *x86* come la **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="74999-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="74999-454">Quindi distribuire in locale del computer, utilizzando il **compilare** voce di menu, selezionando *Distribuisci soluzione*.</span><span class="sxs-lookup"><span data-stu-id="74999-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="74999-455">Per usare l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="74999-455">To use the application:</span></span>

<span data-ttu-id="74999-456">Per cambiare le funzionalità di app tra *Training* modalità e *stima* modalità è necessario aggiornare il **AppMode** variabile, che si trova nel **Awake()** metodo all'interno di *ImageCapture* classe.</span><span class="sxs-lookup"><span data-stu-id="74999-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="74999-457">oppure</span><span class="sxs-lookup"><span data-stu-id="74999-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="74999-458">Nelle *Training* modalità:</span><span class="sxs-lookup"><span data-stu-id="74999-458">In *Training* mode:</span></span>

- <span data-ttu-id="74999-459">Esaminare **Mouse** oppure **tastiera** e usare il **gesto tocco**.</span><span class="sxs-lookup"><span data-stu-id="74999-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="74999-460">Successivamente, il testo verrà visualizzato che richiede di specificare un tag.</span><span class="sxs-lookup"><span data-stu-id="74999-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="74999-461">Indicato **Mouse** oppure **tastiera**.</span><span class="sxs-lookup"><span data-stu-id="74999-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="74999-462">Nelle *stima* modalità:</span><span class="sxs-lookup"><span data-stu-id="74999-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="74999-463">Esaminare un oggetto e usare la **gesto tocco**.</span><span class="sxs-lookup"><span data-stu-id="74999-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="74999-464">Verrà visualizzato il testo che fornisce l'oggetto rilevato, con la probabilità più alta (ciò viene normalizzato).</span><span class="sxs-lookup"><span data-stu-id="74999-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="74999-465">Capitolo 14 - valutare e migliorare il modello di visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="74999-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="74999-466">Per rendere il server più accurato, dovrai continuare per il training del modello utilizzato per la stima.</span><span class="sxs-lookup"><span data-stu-id="74999-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="74999-467">Questa operazione viene eseguita tramite la nuova applicazione, sia con il *training* e *stima* modalità, richiedendo quest'ultimo è possibile visitare il portale, ovvero quelle illustrate in questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="74999-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="74999-468">Essere preparati a visitare di nuovo il portale del numero di volte, per migliorare costantemente il modello.</span><span class="sxs-lookup"><span data-stu-id="74999-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="74999-469">Passare al portale di visione artificiale personalizzato di Azure anche in questo caso e una volta nel progetto, selezionare la *stime* della scheda (dall'alto al centro della pagina):</span><span class="sxs-lookup"><span data-stu-id="74999-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="74999-470">Si noterà che tutte le immagini che sono state inviate al servizio mentre era in esecuzione l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="74999-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="74999-471">Se si posiziona le immagini, si fornirà all'utente le stime che sono state apportate per quell'immagine:</span><span class="sxs-lookup"><span data-stu-id="74999-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="74999-472">Selezionare una delle immagini per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="74999-472">Select one of your images to open it.</span></span> <span data-ttu-id="74999-473">Una volta aperto, si visualizzeranno le stime eseguite per quell'immagine a destra.</span><span class="sxs-lookup"><span data-stu-id="74999-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="74999-474">Se si delle stime corrette e si vuole aggiungere questa immagine modello di training del servizio, fare clic sui *contrassegni* casella di input e selezionare il tag che si desidera associare.</span><span class="sxs-lookup"><span data-stu-id="74999-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="74999-475">Al termine, scegliere il *salvare e chiudere* pulsante nella parte inferiore destra e continuare con l'immagine successiva.</span><span class="sxs-lookup"><span data-stu-id="74999-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="74999-476">Dopo aver nuovamente alla griglia delle immagini, è possibile notare le immagini di che aver aggiunto i tag per (e salvato), verranno rimossi.</span><span class="sxs-lookup"><span data-stu-id="74999-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="74999-477">Se si trova tutte le immagini che si ritiene che non è l'elemento con tag al loro interno, è possibile eliminarle, facendo clic sui segni di graduazione sull'immagine specificata (questa operazione può essere numerose immagini) e quindi scegliendo *eliminare* nell'angolo superiore destro della pagina della griglia.</span><span class="sxs-lookup"><span data-stu-id="74999-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="74999-478">Nella finestra popup che segue, è possibile fare clic su *Sì, è possibile eliminare* oppure *No*, per confermare l'eliminazione o annullare l'operazione, rispettivamente.</span><span class="sxs-lookup"><span data-stu-id="74999-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="74999-479">Quando si è pronti per procedere, fare clic su verde *Train* pulsante in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="74999-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="74999-480">Il modello del servizio verrà eseguito il training con tutte le immagini sono ora fornite (che rendono più accurati).</span><span class="sxs-lookup"><span data-stu-id="74999-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="74999-481">Una volta completato il training, assicurarsi di fare clic sui *predefinito* pulsante ancora una volta, in modo che le *stima URL* continua a usare l'iterazione aggiornata del servizio.</span><span class="sxs-lookup"><span data-stu-id="74999-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="74999-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="74999-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="74999-483">L'applicazione API visione artificiale personalizzato completato</span><span class="sxs-lookup"><span data-stu-id="74999-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="74999-484">Complimenti, è stata compilata un'app per realtà mista che sfrutta l'API di visione artificiale personalizzato di Azure per riconoscere gli oggetti reali, il training del modello di servizio e visualizzare la fiducia di ciò che è stato individuato.</span><span class="sxs-lookup"><span data-stu-id="74999-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="74999-485">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="74999-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="74999-486">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="74999-486">Exercise 1</span></span>

<span data-ttu-id="74999-487">Eseguire il training del **servizio visione artificiale personalizzato** riconoscere più oggetti.</span><span class="sxs-lookup"><span data-stu-id="74999-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="74999-488">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="74999-488">Exercise 2</span></span>

<span data-ttu-id="74999-489">Che consente di espandere in quanto si è appreso, eseguire gli esercizi seguenti:</span><span class="sxs-lookup"><span data-stu-id="74999-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="74999-490">Riprodurre un suono quando un oggetto viene riconosciuto.</span><span class="sxs-lookup"><span data-stu-id="74999-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="74999-491">Esercizio 3</span><span class="sxs-lookup"><span data-stu-id="74999-491">Exercise 3</span></span>

<span data-ttu-id="74999-492">Usare l'API di eseguire nuovamente il training del servizio con le stesse immagini all'app è l'analisi, pertanto, per rendere il più accurati (eseguire stime e contemporaneamente di training).</span><span class="sxs-lookup"><span data-stu-id="74999-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
