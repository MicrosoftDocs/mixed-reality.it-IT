---
title: MR e Azure 304 - riconoscimento facciale
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, misto realtà, academy, unity, esercitazione, api, riconoscimento, hololens, vr immersivi, facciale
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603811"
---
>[!NOTE]
><span data-ttu-id="c3e4e-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c3e4e-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c3e4e-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c3e4e-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c3e4e-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c3e4e-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="c3e4e-110">MR e Azure 304: Rilevamento viso</span><span class="sxs-lookup"><span data-stu-id="c3e4e-110">MR and Azure 304: Face recognition</span></span>

![risultato del completamento di questo corso](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="c3e4e-112">In questo corso si apprenderà come aggiungere funzionalità di riconoscimento del volto a un'applicazione di realtà mista, uso di servizi cognitivi di Azure, con l'API viso di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="c3e4e-113">*API viso Azure* è un servizio Microsoft, che offre agli sviluppatori di algoritmi estremamente avanzati, faccia tutto nel cloud.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="c3e4e-114">Il *API viso* ha due funzioni principali: con gli attributi di rilevamento viso e riconoscimento facciale.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="c3e4e-115">Ciò consente agli sviluppatori di è sufficiente impostare un set di gruppi per i visi e quindi inviare query immagini al servizio in un secondo momento, per determinare a cui appartiene un viso.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="c3e4e-116">Per altre informazioni, visitare il [pagina di riconoscimento facciale Azure](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="c3e4e-117">Dopo aver completato il corso, si avrà una realtà mista applicazione HoloLens, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="c3e4e-118">Usare un **movimento toccare** per avviare l'acquisizione di un'immagine usando la fotocamera di HoloLens integrata.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="c3e4e-119">Inviare l'immagine acquisita per il *l'API viso Azure* servizio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="c3e4e-120">Ricevere i risultati del *API viso* algoritmo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="c3e4e-121">Usare una semplice interfaccia utente, per visualizzare il nome delle persone corrispondente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="c3e4e-122">Ciò viene illustrato come ottenere i risultati dal servizio API viso in un'applicazione basata su Unity realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="c3e4e-123">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c3e4e-124">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="c3e4e-125">È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="c3e4e-126">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="c3e4e-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c3e4e-127">Corso</span><span class="sxs-lookup"><span data-stu-id="c3e4e-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c3e4e-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c3e4e-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c3e4e-129"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="c3e4e-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c3e4e-130">MR e Azure 304: Rilevamento viso</span><span class="sxs-lookup"><span data-stu-id="c3e4e-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3e4e-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c3e4e-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3e4e-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c3e4e-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c3e4e-133">Questo corso è incentrato principalmente sulla HoloLens, è inoltre possibile applicare informazioni in questo corso per auricolari (VR) coinvolgenti di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="c3e4e-134">Poiché immersive auricolari (VR) non è accessibile fotocamere, sarà necessario una fotocamera esterna connessa al PC.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="c3e4e-135">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare immersive auricolari (VR).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3e4e-136">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="c3e4e-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c3e4e-137">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c3e4e-138">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c3e4e-139">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .</span><span class="sxs-lookup"><span data-stu-id="c3e4e-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c3e4e-140">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c3e4e-141">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="c3e4e-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c3e4e-142">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="c3e4e-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="c3e4e-143">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c3e4e-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="c3e4e-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="c3e4e-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="c3e4e-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c3e4e-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="c3e4e-146">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="c3e4e-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c3e4e-147">Una fotocamera connessa al PC (per lo sviluppo visore VR immersivi)</span><span class="sxs-lookup"><span data-stu-id="c3e4e-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="c3e4e-148">Accesso a Internet per la configurazione di Azure e il recupero di API viso</span><span class="sxs-lookup"><span data-stu-id="c3e4e-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c3e4e-149">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="c3e4e-149">Before you start</span></span>

1.  <span data-ttu-id="c3e4e-150">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c3e4e-151">Configurare e testare l'HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="c3e4e-152">Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="c3e4e-153">È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova App per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="c3e4e-154">Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="c3e4e-155">Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="c3e4e-156">Capitolo 1 - portale di Azure</span><span class="sxs-lookup"><span data-stu-id="c3e4e-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="c3e4e-157">Usare la *API viso* servizio in Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="c3e4e-158">Accedere prima di tutto per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="c3e4e-159">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c3e4e-160">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c3e4e-161">Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *API viso*, premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![eseguire la ricerca di api viso](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="c3e4e-163">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="c3e4e-164">La nuova pagina fornirà una descrizione del *API viso* servizio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="c3e4e-165">AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![informazioni sull'api viso](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="c3e4e-167">Dopo avere fatto clic su **Create**:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="c3e4e-168">Inserire il nome desiderato per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="c3e4e-169">Selezionare una sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-169">Select a subscription.</span></span>

    3. <span data-ttu-id="c3e4e-170">Selezionare il piano tariffario appropriato per l'utente, se questa è la prima volta che la creazione di un *Face API servizio*, un livello gratuito, denominato F0, debba essere disponibile.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="c3e4e-171">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c3e4e-172">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c3e4e-173">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="c3e4e-174">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="c3e4e-175">L'app UWP **persona Maker**, che viene usato in seguito, richiede l'uso di 'Stati Uniti occidentali' per il percorso.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="c3e4e-176">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="c3e4e-177">Selezionare \**creare *.**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-177">Select **Create\*.**</span></span>

        ![Crea servizio api viso](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="c3e4e-179">Dopo avere fatto clic su \**crea *,** si dovrà attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="c3e4e-180">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notifica di creazione del servizio](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="c3e4e-182">Fare clic su notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-182">Click on the notifications to explore your new Service instance.</span></span>

    ![Passare alla notifica relativa alle risorse](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="c3e4e-184">Quando si è pronti, fare clic su **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![accesso affrontano le chiavi api](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="c3e4e-186">All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, questa operazione viene eseguita tramite la sottoscrizione del servizio 'key'.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="c3e4e-187">Dal *avvio rapido* pagina, del *API viso* del servizio, il primo punto è numero 1, a *individuare le chiavi.*</span><span class="sxs-lookup"><span data-stu-id="c3e4e-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="c3e4e-188">Nel *Service* pagina selezionare entrambe di blue **chiavi** hyperlink (se nella pagina avvio rapido), o la **chiavi** collegamento nel menu di spostamento di servizi (a sinistra, identificata dal ' chiave ' icona), per visualizzare le chiavi.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="c3e4e-189">Prendere nota di uno delle chiavi e proteggerlo, perché sarà necessaria in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="c3e4e-190">Capitolo 2 - uso dell'applicazione UWP 'Person Maker'</span><span class="sxs-lookup"><span data-stu-id="c3e4e-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="c3e4e-191">Assicurarsi di scaricare l'applicazione UWP predefiniti chiamati [persona Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="c3e4e-192">Questa app non è il prodotto finale per questo corso, di un semplice strumento per creare le voci di Azure, il progetto più avanti si baseranno su.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="c3e4e-193">**Persona Maker** consente di creare voci di Azure, che sono associate utenti e gruppi di utenti.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="c3e4e-194">L'applicazione inseriranno tutte le informazioni necessarie in un formato che è quindi in un secondo momento utilizzabile da FaceAPI, per poterlo riconoscere i visi di persone che sono stati aggiunti.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="c3e4e-195">[IMPORTANTE] **Persona Maker** utilizza una base limitazione delle richieste, al fine di garantire di non superare il numero di chiamate al servizio al minuto per il **livello di sottoscrizione gratuita**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="c3e4e-196">Il testo in verde nella parte superiore verrà cambia in rosso e aggiornare 'Attivo' quando viene applicata la limitazione; In questo caso, attendere semplicemente che l'applicazione (attenderà fino a quando non può continuare quindi l'accesso al servizio viso, l'aggiornamento come 'Attivo IN' quando è possibile utilizzare anche in questo caso).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="c3e4e-197">Questa applicazione usa la *Microsoft.ProjectOxford.Face* usano librerie, quale sarà possibile apportare completa dell'API viso.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="c3e4e-198">Questa libreria è disponibile gratuitamente come pacchetto NuGet.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="c3e4e-199">Per altre informazioni su questo e così via, le API [assicurarsi di passare all'articolo di riferimento API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="c3e4e-200">Questi sono solo i passaggi necessari, le istruzioni su come eseguire queste operazioni è più in basso il documento.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="c3e4e-201">Il **persona Maker** app consentirà di:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="c3e4e-202">Creare un *gruppo di persone*, che è costituito da un gruppo di più persone che si desidera associare.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="c3e4e-203">Con l'account di Azure Puoi ospitare più gruppi di persone.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="c3e4e-204">Creare un *persona*, che è un membro di un gruppo di persone.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="c3e4e-205">Ogni persona dispone di numerose *viso* immagini associate.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="c3e4e-206">Assegnare *affrontano le immagini* a un *persona*, per consentire al servizio di API viso di Azure di riconoscere un *persona* dal corrispondente *viso*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="c3e4e-207">*Train* le *Azure affrontano servizio API*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="c3e4e-208">Si noti, pertanto per eseguire il training di questa app di riconoscere le persone, sarà necessario foto ravvicinate dieci (10) di ogni persona che si desidera aggiungere al gruppo di persone.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="c3e4e-209">L'App di Windows 10 Cam possono aiutare a sfruttare questi.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="c3e4e-210">È necessario assicurarsi che ogni foto è chiaro (evitare sfocatura, oscurare o in corso troppo lontano dal soggetto), avere la foto in formato di file jpg o png, con le dimensioni del file di immagine in corso non superiore **4MB**e non inferiore a **1KB**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="c3e4e-211">Se si segue questa esercitazione, non usare il proprio viso per il training, come quando si inserisce il HoloLens, è Impossibile esaminare manualmente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="c3e4e-212">Usare la faccia di un collega o fellow studente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="c3e4e-213">In esecuzione **persona Maker**:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="c3e4e-214">Aprire il **PersonMaker** cartella e fare doppio clic sui *soluzione PersonMaker* aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="c3e4e-215">Una volta il *PersonMaker soluzione* è aperto, assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="c3e4e-216">Il *configurazione della soluzione* è impostata su **Debug**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="c3e4e-217">Il *piattaforma soluzione* è impostata su **x86**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="c3e4e-218">Il *piattaforma di destinazione* viene **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="c3e4e-219">Inoltre potrebbe essere necessario *Ripristina pacchetti NuGet* (pulsante destro del mouse il *soluzione* e selezionare **Ripristina pacchetti NuGet**).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="c3e4e-220">Fare clic su *computer locale* e verrà avviata l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="c3e4e-221">Tenere presente, a su schermi più piccoli, tutto il contenuto potrebbe non essere visibile, anche se è possibile scorrere ulteriormente verso il basso per visualizzarlo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![interfaccia utente di persona maker](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="c3e4e-223">Inserire le **chiave di autenticazione di Azure**, che è necessario, dalle *API viso* servizio all'interno di Azure.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="c3e4e-224">Inserire:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-224">Insert:</span></span>

    1. <span data-ttu-id="c3e4e-225">Il *ID* da assegnare per il *gruppo di persone*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="c3e4e-226">L'ID deve essere in lettere minuscole, senza spazi.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="c3e4e-227">Prendere nota di questo ID, sarà necessaria in un secondo momento nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="c3e4e-228">Il *Name* da assegnare al *gruppo di persone* (può avere spazi).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="c3e4e-229">Premere **Crea gruppo di persone** pulsante.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="c3e4e-230">Sotto il pulsante verrà visualizzato il messaggio di conferma.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="c3e4e-231">Se si dispone di un errore "Accesso negato", controllare il percorso impostato per il servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="c3e4e-232">Come indicato in precedenza, questa app è stata progettata per "Stati Uniti occidentali".</span><span class="sxs-lookup"><span data-stu-id="c3e4e-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3e4e-233">Si noterà che è anche possibile scegliere il **recuperare un gruppo noto** pulsante: si tratta di per se è stato già creato un utente a gruppo e preferenze per usarlo, anziché crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="c3e4e-234">Tenere presente, se si sceglie *creare un gruppo di persone* con un gruppo noto, verrà recuperata anche un gruppo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="c3e4e-235">Inserire il *Name* del *persona* si desidera creare.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="c3e4e-236">Scegliere il **persona che crea** pulsante.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="c3e4e-237">Sotto il pulsante verrà visualizzato il messaggio di conferma.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="c3e4e-238">Se si desidera eliminare una persona hanno creato in precedenza, è possibile scrivere il nome nella casella di testo e premere **Elimina utente**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="c3e4e-239">Assicurarsi che si conosce il percorso di dieci (10) foto della persona che si desidera aggiungere al gruppo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="c3e4e-240">Premere **crea e Apri cartella** per aprire l'Explorer di Windows per la cartella associata alla persona.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="c3e4e-241">Aggiungere le immagini di dieci (10) nella cartella.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="c3e4e-242">Tali dispositivi devono presentare *JPG* oppure *PNG* formato di file.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="c3e4e-243">Fare clic su **inviare ad Azure**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="c3e4e-244">Un contatore visualizzerà lo stato dell'inoltro, seguito da un messaggio quando è stata completata.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="c3e4e-245">Dopo il contatore è stata completata ed è stato visualizzato un messaggio di conferma fare clic su **Train** per eseguire il training del servizio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="c3e4e-246">Una volta completato il processo, si è pronti a spostare in Unity.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="c3e4e-247">Capitolo 3 - configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="c3e4e-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="c3e4e-248">Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c3e4e-249">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-249">Open *Unity* and click **New**.</span></span> 

    ![Avvio nuovo progetto Unity.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="c3e4e-251">A questo punto, è necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="c3e4e-252">Inserire **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="c3e4e-253">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="c3e4e-254">Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c3e4e-255">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-255">Then, click **Create project**.</span></span>

    ![Fornire i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="c3e4e-257">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c3e4e-258">Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c3e4e-259">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c3e4e-260">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-260">Close the **Preferences** window.</span></span>

    ![Aggiornamento delle preferenze dell'editor di script.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="c3e4e-262">Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crea finestra delle impostazioni, la piattaforma del commutatore alla piattaforma UWP.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="c3e4e-264">Passare a **File > Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="c3e4e-265">**Dispositivo di destinazione** è impostata su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="c3e4e-266">Per le cuffie coinvolgenti, impostare **dispositivo di destinazione** al *qualsiasi dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="c3e4e-267">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="c3e4e-268">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="c3e4e-269">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="c3e4e-270">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="c3e4e-271">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="c3e4e-272">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c3e4e-273">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-273">A save window will appear.</span></span>

            ![Fare clic su Aggiungi pulsante Apri scene](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="c3e4e-275">Selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crea nuova cartella scripts](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="c3e4e-277">Aprire appena creato **scene** cartella e quindi il **nome File**: campo di testo, digitare **FaceRecScene**, quindi premere **Salva**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Assegnare un nome nuova scena.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="c3e4e-279">Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="c3e4e-280">Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Aprire le impostazioni del giocatore.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="c3e4e-282">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="c3e4e-283">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="c3e4e-284">**Scripting** **versione Runtime** deve essere **sperimentale** (.NET 4.6 equivalente).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="c3e4e-285">Modificare questo elemento attiverà la necessità di riavviare l'Editor.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="c3e4e-286">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="c3e4e-287">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aggiornare le altre impostazioni.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="c3e4e-289">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="c3e4e-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-290">**InternetClient**</span></span>
        - <span data-ttu-id="c3e4e-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-291">**Webcam**</span></span>

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="c3e4e-293">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aggiornare le impostazioni di R X.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="c3e4e-295">Nuovamente in *Build Settings*, **Unity C# progetti** non è più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="c3e4e-296">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="c3e4e-297">Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="c3e4e-298">Capitolo 4 - impostazione della fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="c3e4e-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3e4e-299">Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo nel progetto come un [personalizzato Pacchetto](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="c3e4e-300">Tenere presente che questo pacchetto include inoltre l'importazione del *DLL Newtonsoft*, descritta in [capitolo 5](#chapter-5--import-the-newtonsoft.json-library).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoft.json-library).</span></span> <span data-ttu-id="c3e4e-301">A questo punto importato, è possibile continuare dal [capitolo 6](#chapter-6-create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-301">With this imported, you can continue from [Chapter 6](#chapter-6-create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="c3e4e-302">Nel *gerarchia* riquadro, selezionare la **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="c3e4e-303">Una volta selezionata, sarà possibile visualizzare tutti i componenti del **Main Camera** nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="c3e4e-304">Il **oggetto della fotocamera** devono essere denominati **Main Camera** (si noti l'ortografici!)</span><span class="sxs-lookup"><span data-stu-id="c3e4e-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="c3e4e-305">Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici!)</span><span class="sxs-lookup"><span data-stu-id="c3e4e-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="c3e4e-306">Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="c3e4e-307">Impostare **cancellare i flag** a **colore a tinta unita**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="c3e4e-308">Impostare il **sfondo** colore del componente della fotocamera su **nero, Alpha 0 (Hex codice: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![configurare i componenti della fotocamera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="c3e4e-310">Capitolo 5: importazione della libreria newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="c3e4e-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3e4e-311">Se è stata importata '.unitypackage' nella [ultimo capitolo](#chapter-4--main-camera-setup), è possibile ignorare questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4--main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="c3e4e-312">Che consentono di deserializzano e serializzano oggetti ricevuti e inviati al servizio Bot è necessario scaricare il *newtonsoft. JSON* libreria.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="c3e4e-313">Si noterà una versione compatibile già organizzata con la struttura di cartelle di Unity corretta in questo [file di pacchetto Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="c3e4e-314">Per importare la libreria:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-314">To import the library:</span></span>

1.  <span data-ttu-id="c3e4e-315">Scaricare il pacchetto Unity.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="c3e4e-316">Fare clic su **Assets**, **Importa pacchetto**, **pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Importazione della libreria newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="c3e4e-318">Cercare il pacchetto Unity è stato scaricato e fare clic su Apri.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="c3e4e-319">Assicurarsi che tutti i componenti del pacchetto sono selezionati e fare clic su **importazione**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Importazione della libreria newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="c3e4e-321">Capitolo 6: creare la classe FaceAnalysis</span><span class="sxs-lookup"><span data-stu-id="c3e4e-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="c3e4e-322">Lo scopo della classe FaceAnalysis deve ospitare i metodi necessari per comunicare con il servizio di riconoscimento di volti di Azure.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="c3e4e-323">Dopo l'invio di un'immagine di acquisizione del servizio, verrà analizzare lo e identificare i volti all'interno e determinare se eventuali appartengono a un utente noto.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="c3e4e-324">Se viene trovata una persona nota, questa classe relativo nome verrà visualizzato come testo dell'interfaccia utente nella scena.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="c3e4e-325">Per creare il *FaceAnalysis* classe:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="c3e4e-326">Fare doppio clic nella *cartella Assets* si trova nel Pannello di progetto, quindi fare clic su **Create** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="c3e4e-327">Chiamare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-327">Call the folder **Scripts**.</span></span> 

    ![Creare la classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="c3e4e-329">Fare doppio clic sulla cartella appena creata, per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="c3e4e-330">Fare doppio clic all'interno della cartella, quindi fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="c3e4e-331">Chiamare lo script *FaceAnalysis*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="c3e4e-332">Fare doppio clic su nuova *FaceAnalysis* script per aprirlo con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="c3e4e-333">Immettere gli spazi dei nomi seguenti sopra la *FaceAnalysis* classe:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="c3e4e-334">È ora necessario aggiungere tutti gli oggetti che vengono usati per deserialising.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="c3e4e-335">Questi oggetti devono essere aggiunti **fuori** del *FaceAnalysis* script (sotto la parentesi graffa in basso).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

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
7. <span data-ttu-id="c3e4e-336">Il *Start ()* e *Update ()* metodi non verranno utilizzati, quindi eliminarli ora.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="c3e4e-337">All'interno di *FaceAnalysis* classe, aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

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
    > <span data-ttu-id="c3e4e-338">Sostituire il **key** e il **personGroupId** con la chiave di servizio e l'Id del gruppo creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="c3e4e-339">Aggiungere il *Awake()* metodo, che initialises la classe, aggiungendo il *ImageCapture* classe alla fotocamera principale e chiama il metodo di creazione di etichette:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

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

10. <span data-ttu-id="c3e4e-340">Aggiungere il *CreateLabel()* metodo, che crea il *etichetta* oggetto per visualizzare il risultato dell'analisi:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

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

11. <span data-ttu-id="c3e4e-341">Aggiungere il *DetectFacesFromImage()* e *GetImageAsByteArray()* (metodo).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="c3e4e-342">Il primo richiederà il servizio di riconoscimento del viso per rilevare eventuali possibili viso nell'immagine inviata, mentre nel secondo caso è necessario convertire l'immagine acquisita in una matrice di byte:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

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

12. <span data-ttu-id="c3e4e-343">Aggiungere il *IdentifyFaces()* metodo, che richiede il *servizio di riconoscimento volto* per identificare eventuali noti volti rilevati in precedenza nell'immagine inviato.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="c3e4e-344">La richiesta restituisce un id dell'utente identificato ma non il nome:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-344">The request will return an id of the identified person but not the name:</span></span>

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

13. <span data-ttu-id="c3e4e-345">Aggiungere il *GetPerson()* (metodo).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="c3e4e-346">Fornendo la persona id, questo metodo e le richieste per il *servizio di riconoscimento volto* per restituire il nome della persona identificato:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

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

14.  <span data-ttu-id="c3e4e-347">Ricordarsi di **salvare** le modifiche prima di tornare all'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="c3e4e-348">Nell'Editor di Unity, trascinare lo script FaceAnalysis dalla cartella Scripts nel Pannello di progetto per l'oggetto Main Camera nel *pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="c3e4e-349">Il nuovo componente script verrà quindi aggiunto alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-349">The new script component will be so added to the Main Camera.</span></span> 

![Posizionare FaceAnalysis nella fotocamera principale](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="c3e4e-351">Capitolo 7 - creare la classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="c3e4e-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="c3e4e-352">Lo scopo del *ImageCapture* classe consiste nell'ospitare i metodi necessari per comunicare con i *servizio di riconoscimento volto Azure* per analizzare l'immagine verrà acquisita, che identifica i visi in esso e determinare se appartiene a un utente noto.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="c3e4e-353">Se viene trovata una persona nota, questa classe relativo nome verrà visualizzato come testo dell'interfaccia utente nella scena.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="c3e4e-354">Per creare il *ImageCapture* classe:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="c3e4e-355">Pulsante destro del mouse all'interno di **script** cartella hanno creato in precedenza e quindi fare clic su **Create**,  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="c3e4e-356">Chiamare lo script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="c3e4e-357">Fare doppio clic su nuova *ImageCapture* script per aprirlo con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="c3e4e-358">Immettere gli spazi dei nomi seguenti sopra la classe ImageCapture:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="c3e4e-359">All'interno di *ImageCapture* classe, aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-359">Inside the *ImageCapture* class, add the following variables:</span></span>

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

5.  <span data-ttu-id="c3e4e-360">Aggiungere il *Awake()* e *Start ()* metodi necessari per inizializzare la classe e consentire di HoloLens acquisire i movimenti dell'utente:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

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

6.  <span data-ttu-id="c3e4e-361">Aggiungere il *TapHandler()* che viene chiamato quando l'utente esegue un' *toccare* movimenti:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

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

7.  <span data-ttu-id="c3e4e-362">Aggiungere il *ExecuteImageCaptureAndAnalysis()* metodo, che inizierà il processo di acquisizione immagine:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

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

8.  <span data-ttu-id="c3e4e-363">Aggiungere i gestori eventi vengono chiamati quando il processo di acquisizione di foto è stato completato:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

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

9. <span data-ttu-id="c3e4e-364">Ricordarsi di **salvare** le modifiche prima di tornare all'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="c3e4e-365">Capitolo 8 - la compilazione della soluzione</span><span class="sxs-lookup"><span data-stu-id="c3e4e-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="c3e4e-366">Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="c3e4e-367">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="c3e4e-368">Tutte le impostazioni indicate nel capitolo 3 siano impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="c3e4e-369">Lo script *FaceAnalysis* è collegato all'oggetto Main Camera.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="c3e4e-370">Entrambi il **Authentication Key** e **Id gruppo** sono state impostate all'interno di *FaceAnalysis* script.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="c3e4e-371">R questo punto si è pronti a compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="c3e4e-372">Dopo aver compilata la soluzione, sarà possibile distribuire l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="c3e4e-373">Per iniziare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="c3e4e-374">Facendo clic sul File, salvare, salvare nella scena corrente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="c3e4e-375">Vai a File, impostazioni di compilazione, fare clic su Aggiungi scene Open.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="c3e4e-376">Assicurarsi di segni di graduazione Unity C# progetti.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-376">Make sure to tick Unity C# Projects.</span></span>

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="c3e4e-378">Premere compilazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-378">Press Build.</span></span> <span data-ttu-id="c3e4e-379">In questo modo, Unity avvierà una finestra di Esplora File, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c3e4e-380">Creare a questo punto, tale cartella all'interno del progetto Unity e App.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="c3e4e-381">Premere quindi con la cartella dell'App selezionata, selezionare la cartella.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="c3e4e-382">Unity verrà avviata la creazione del progetto, per la cartella dell'App.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="c3e4e-383">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà una finestra di Esplora File nel percorso della compilazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="c3e4e-385">Aprire la cartella dell'App e quindi aprire la nuova soluzione di progetto (come nell'esempio precedente, MR_FaceRecognition.sln).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="c3e4e-386">Capitolo 9 - distribuzione dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="c3e4e-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="c3e4e-387">Per distribuire in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="c3e4e-388">È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="c3e4e-389">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-389">To do this:</span></span>

    1. <span data-ttu-id="c3e4e-390">Durante l'uso di HoloLens, aprire il **impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="c3e4e-391">Passare a **rete e Internet > Wi-Fi > Opzioni avanzate**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="c3e4e-392">Si noti il **IPv4** indirizzo.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="c3e4e-393">Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza > per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="c3e4e-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="c3e4e-394">Attivare la modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="c3e4e-395">Passare alla nuova build Unity (le *App* cartella) e aprire il file di soluzione con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="c3e4e-396">Selezione configurazione di soluzione **Debug**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="c3e4e-397">La piattaforma della soluzione, selezionare **x86**, **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="c3e4e-399">Andare alla **dal menu Compila** e fare clic su **Distribuisci soluzione**, trasferire localmente l'applicazione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="c3e4e-400">L'App deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="c3e4e-401">Per distribuire visore VR immersivi, impostare il **piattaforma soluzione** al *computer locale*e impostare il **configurazione** a *Debug*, con *x86* come la **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="c3e4e-402">Quindi distribuire in locale del computer, utilizzando il **dal menu Compila**, selezionando *Distribuisci soluzione*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="c3e4e-403">Capitolo 10 - uso dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="c3e4e-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="c3e4e-404">Uso di HoloLens, avviare l'app.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="c3e4e-405">Esaminare la persona che è registrati con il *API viso*.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="c3e4e-406">Verificare che:</span><span class="sxs-lookup"><span data-stu-id="c3e4e-406">Make sure that:</span></span>

    -  <span data-ttu-id="c3e4e-407">Viso della persona non è troppo distante e chiaramente visibili</span><span class="sxs-lookup"><span data-stu-id="c3e4e-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="c3e4e-408">L'illuminazione di ambiente non è troppo scuro</span><span class="sxs-lookup"><span data-stu-id="c3e4e-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="c3e4e-409">Usare i movimenti di tocco per acquisire l'immagine di una persona.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="c3e4e-410">Attendere che l'App per la richiesta di analisi di inviare e ricevere una risposta.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="c3e4e-411">Se la persona che è stata riconosciuta correttamente, verrà visualizzato il nome della persona come testo dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="c3e4e-412">È possibile ripetere il processo di acquisizione mediante i movimenti tocco di intervalli di pochi secondi.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="c3e4e-413">Azure Face API dell'applicazione completata</span><span class="sxs-lookup"><span data-stu-id="c3e4e-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="c3e4e-414">Complimenti, è stata compilata un'app per realtà mista che usa il servizio di riconoscimento facciale di Azure per rilevare volti all'interno di un'immagine e identificare eventuali visi noti.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![risultato del completamento di questo corso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c3e4e-416">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="c3e4e-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c3e4e-417">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="c3e4e-417">Exercise 1</span></span>

<span data-ttu-id="c3e4e-418">Il **l'API viso Azure** è sufficientemente potente per rilevare fino a 64 visi in un'unica immagine.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="c3e4e-419">Estendere l'applicazione, in modo che Impossibile riconoscere i visi due o tre, tra le molte altre persone.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c3e4e-420">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="c3e4e-420">Exercise 2</span></span>

<span data-ttu-id="c3e4e-421">Il **l'API viso Azure** è anche in grado di fornire nuovamente tutti i tipi di informazioni sugli attributi.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="c3e4e-422">Integrare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c3e4e-422">Integrate this into the application.</span></span> <span data-ttu-id="c3e4e-423">Ciò potrebbe essere ancora più interessante, in combinazione con il [API emozioni](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="c3e4e-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
