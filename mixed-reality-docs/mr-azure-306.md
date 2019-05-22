---
title: MR e 306 Azure - video in Streaming
description: Completare questo corso di informazioni su come implementare servizi multimediali di Azure all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, servizi multimediali, lo streaming di video, 360, coinvolgenti, vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599483"
---
>[!NOTE]
><span data-ttu-id="5c8a4-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5c8a4-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5c8a4-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5c8a4-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5c8a4-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5c8a4-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="5c8a4-110">MR e Azure 306: Lo streaming di video</span><span class="sxs-lookup"><span data-stu-id="5c8a4-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="5c8a4-111">![versione finale del prodotto-avviare](images/AzureLabs-Lab6-00.png)
![prodotto finale-avvio](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="5c8a4-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="5c8a4-112">In questo corso scoprirai come connettere i servizi multimediali di Azure a un'esperienza VR realtà mista di Windows per consentire la riproduzione di video a 360 gradi in auricolari coinvolgenti di streaming.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="5c8a4-113">**Servizi multimediali di Azure** sono una raccolta di servizi che ti offre servizi streaming video di alta qualità per raggiungere un pubblico più ampio sui dispositivi mobili più diffusi di oggi.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="5c8a4-114">Per altre informazioni, visitare il [pagina di servizi multimediali di Azure](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="5c8a4-115">Dopo aver completato il corso, si avrà un'applicazione visore VR immersivi realtà mista, in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="5c8a4-116">Recuperare un video a 360 gradi da un' **archiviazione di Azure**, tramite il **servizi multimediali di Azure**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="5c8a4-117">Visualizzare il video a 360 gradi recuperato all'interno di una scena Unity.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="5c8a4-118">Spostarsi tra le due scene, con due diversi video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="5c8a4-119">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="5c8a4-120">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="5c8a4-121">È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="5c8a4-122">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="5c8a4-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5c8a4-123">Corso</span><span class="sxs-lookup"><span data-stu-id="5c8a4-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5c8a4-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5c8a4-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5c8a4-125"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="5c8a4-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="5c8a4-126">MR e Azure 306: Lo streaming di video</span><span class="sxs-lookup"><span data-stu-id="5c8a4-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="5c8a4-127">✔️</span><span class="sxs-lookup"><span data-stu-id="5c8a4-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="5c8a4-128">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5c8a4-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="5c8a4-129">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="5c8a4-130">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="5c8a4-131">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare l'articolo strumenti](install-the-tools.md), anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .</span><span class="sxs-lookup"><span data-stu-id="5c8a4-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="5c8a4-132">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="5c8a4-133">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="5c8a4-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="5c8a4-134">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="5c8a4-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5c8a4-135">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="5c8a4-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5c8a4-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="5c8a4-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5c8a4-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5c8a4-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="5c8a4-138">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="5c8a4-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="5c8a4-139">Accesso a Internet per il recupero di dati e il programma di installazione di Azure</span><span class="sxs-lookup"><span data-stu-id="5c8a4-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="5c8a4-140">Due video a 360 gradi in formato mp4 (è possibile trovare alcuni video gratuite [nella pagina di download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="5c8a4-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="5c8a4-141">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="5c8a4-141">Before you start</span></span>

1.  <span data-ttu-id="5c8a4-142">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="5c8a4-143">Configurare e testare il visore VR Immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5c8a4-144">Verrà **non** richiedono controller di movimento a questo corso.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="5c8a4-145">Se è necessario il supporto di configurazione di visore VR Immersivi, fai clic [collegamento su come impostare la realtà mista di Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="5c8a4-146">Capitolo 1 - portale di Azure: creare l'Account di archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="5c8a4-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="5c8a4-147">Usare la **servizio di archiviazione di Azure**, sarà necessario creare e configurare un **Account di archiviazione** nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="5c8a4-148">Accedi per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5c8a4-149">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="5c8a4-150">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="5c8a4-151">Una volta connessi, fare clic su **gli account di archiviazione** nel menu a sinistra.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="5c8a4-153">Nel **gli account di archiviazione** scheda, fare clic su **Add**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="5c8a4-155">Nel **creare account di archiviazione** scheda:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="5c8a4-156">Inserire un **nome** per l'account, tenere presente questo campo accetta solo numeri e lettere minuscole.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="5c8a4-157">Per la **modello di distribuzione** selezionate **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="5c8a4-158">Per la **tipologia Account**, selezionare **archiviazione (utilizzo generico v1)**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="5c8a4-159">Per la **Performance**, selezionare **Standard\*.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="5c8a4-160">Per la **replica** selezionate **l'archiviazione con ridondanza locale (LRS)**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="5c8a4-161">Lasciare **trasferimento sicuro obbligatorio** come **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="5c8a4-162">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="5c8a4-163">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="5c8a4-164">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="5c8a4-165">Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5c8a4-166">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5c8a4-167">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="5c8a4-168">È necessario confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="5c8a4-170">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="5c8a4-171">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="5c8a4-173">A questo punto non è necessario seguire la risorsa, è sufficiente spostare il capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="5c8a4-174">Capitolo 2 - portale di Azure: creazione del servizio multimediale</span><span class="sxs-lookup"><span data-stu-id="5c8a4-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="5c8a4-175">Per usare il servizio di supporto di Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione (in cui il titolare dell'account deve essere un amministratore).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="5c8a4-176">Nel portale di Azure, fare clic su **crea una risorsa** nell'angolo in alto a sinistra e cercare **servizio multimediale** premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="5c8a4-177">La risorsa desiderata attualmente dispone di un'icona di colore rosa; Fare clic sul collegamento, in modo da visualizzare una nuova pagina.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="5c8a4-179">La nuova pagina fornirà una descrizione del **servizio multimediale**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="5c8a4-180">AT nella parte inferiore sinistra di questo prompt, fare clic sui **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="5c8a4-182">Dopo avere fatto clic su **Create** verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli relativi al nuovo servizio di supporto:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="5c8a4-183">Inserire la posizione desiderata **nome dell'Account** per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="5c8a4-184">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="5c8a4-185">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5c8a4-186">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5c8a4-187">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="5c8a4-188">Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire i gruppi di risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="5c8a4-189">Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5c8a4-190">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5c8a4-191">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="5c8a4-192">Per il **Account di archiviazione** fare clic su di **Seleziona...**  sezione e quindi scegliere il **Account di archiviazione** creato nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="5c8a4-193">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="5c8a4-194">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-194">Click **Create**.</span></span>

        ![Il portale di Azure](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="5c8a4-196">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="5c8a4-197">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="5c8a4-199">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-199">Click on the notification to explore your new Service instance.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="5c8a4-201">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="5c8a4-202">Entro la nuova pagina di servizi multimediali, all'interno del pannello a sinistra, fare clic sui **asset** collegamento, che si riferisce a metà inferiore.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="5c8a4-203">Nella pagina successiva, nell'angolo superiore sinistro della pagina, fare clic su **caricare**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="5c8a4-205">Fare clic sui **cartella** icona per esplorare i file e selezionare il Video 360 prima che si desidera eseguire lo streaming.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="5c8a4-206">È possibile seguire questo [collegamento per scaricare un video di esempio](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="5c8a4-208">Nomi file lunghi possono causare un problema con il codificatore: pertanto, per garantire i video non sono presenti problemi, è consigliabile ridurre la lunghezza dei nomi di file video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="5c8a4-209">L'indicatore di stato verrà diventi verde quando ha terminato il caricamento di video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="5c8a4-211">Fare clic sul testo precedente (**yourservicename - asset**) per tornare alle **asset** pagina.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="5c8a4-212">Si noterà che il video sia stato caricato correttamente.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="5c8a4-213">Fare clic su di esso.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-213">Click on it.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="5c8a4-215">Si verrà reindirizzati alla pagina mostrerà che vengono fornite informazioni dettagliate relative al video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="5c8a4-216">Per poter utilizzare il video è necessario codificarli, facendo i **Encode** pulsante in alto a sinistra della pagina.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="5c8a4-218">Un nuovo pannello verrà visualizzato a destra, in cui sarà in grado di impostare le opzioni per il file di codifica.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="5c8a4-219">Impostare le proprietà seguenti (alcuni sarà già impostato per impostazione predefinita):</span><span class="sxs-lookup"><span data-stu-id="5c8a4-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="5c8a4-220">**Nome del codificatore multimediale *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="5c8a4-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="5c8a4-221">**Set di impostazioni di codifica *Content Adaptive Multiple Bitrate MP4***</span><span class="sxs-lookup"><span data-stu-id="5c8a4-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="5c8a4-222">**Nome del processo *elaborazione Media Encoder Standard di Video1.mp4***</span><span class="sxs-lookup"><span data-stu-id="5c8a4-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="5c8a4-223">**Nome dell'asset multimediali output *Video1.mp4 - Media Encoder Standard con codifica***</span><span class="sxs-lookup"><span data-stu-id="5c8a4-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Il portale di Azure](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="5c8a4-225">Fare clic sul pulsante **Crea**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="5c8a4-226">Si noterà una barra con **processo di codifica aggiunta**, fare clic su tale barra e verrà visualizzato un pannello con lo stato di avanzamento di codifica in esso visualizzato.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-17.png)

    ![Il portale di Azure](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="5c8a4-229">Attendere il completamento del processo.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="5c8a4-230">Al termine, è possibile chiudere il pannello con la "X" in alto a destra del pannello.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-19.png)

    ![Il portale di Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="5c8a4-233">Il tempo che richiesto, dipende dalla dimensione file del video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="5c8a4-234">Questo processo può richiedere molto tempo.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="5c8a4-235">Ora che la versione codificata del video è stata creata, è possibile pubblicare in modo che sia accessibile.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="5c8a4-236">A tale scopo, fare clic sul collegamento blu **asset** per tornare alla pagina di asset.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="5c8a4-238">Si noterà un video insieme a un altro, che è impostato su \*\*Asset di tipo \*a più Bitrate MP4\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="5c8a4-240">È possibile notare che il nuovo asset, insieme ai video iniziale, è *sconosciuto*, e ha '0' byte, in quanto **dimensioni**, aggiornare semplicemente la finestra per consentirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="5c8a4-241">Fare clic su questo nuovo asset.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-241">Click this new asset.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="5c8a4-243">Verrà visualizzato un pannello simile a quello usato prima, proprio questa è una risorsa diversa.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="5c8a4-244">Scegliere il **pubblica** pulsante che si trova in centrale superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="5c8a4-246">Verrà richiesto di impostare una **localizzatore**, ovvero il punto di ingresso, file/sec negli asset.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="5c8a4-247">Per lo scenario di imposta le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="5c8a4-248">**Tipo di localizzatore** > **progressivo**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="5c8a4-249">Il **data** e **ora** verrà automaticamente impostato per l'utente, la data corrente, un momento nel futuro (100 anni in questo caso).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="5c8a4-250">Lasciare invariata o modificandola in base alle proprie.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5c8a4-251">Per altre informazioni sui localizzatori e ciò che è possibile scegliere, visitare il [documentazione di servizi multimediali di Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="5c8a4-252">Nella parte inferiore del pannello, fare clic sui **Add** pulsante.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="5c8a4-254">Il video viene pubblicato e può essere trasmessi tramite il relativo endpoint.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="5c8a4-255">Ulteriormente verso il basso la pagina è una **file** sezione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="5c8a4-256">Si tratta in cui saranno le diverse versioni di codificate del video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="5c8a4-257">Selezionare il più alto possibile risoluzione uno (nell'immagine seguente è il file di 1920 x 960), e quindi verrà visualizzato un pannello a destra.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="5c8a4-258">Qui troverai una **URL di Download**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="5c8a4-259">Copiare questa **Endpoint** perché verrà usato successivamente nel codice.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-26.png)    

    ![Il portale di Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="5c8a4-262">È anche possibile premere il **riprodurre** per riprodurre il video e testarlo.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="5c8a4-263">È ora necessario caricare il secondo video che si userà in questo laboratorio.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="5c8a4-264">Seguire i passaggi precedenti, ripetere lo stesso processo per il secondo video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="5c8a4-265">Assicurarsi copiare il secondo **Endpoint** anche.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="5c8a4-266">Usare il comando seguente [collegamento per scaricare un video secondo](https://vimeo.com/214402865).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="5c8a4-267">Dopo che entrambi i video sono stati pubblicati, si è pronti per passare al capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="5c8a4-268">Capitolo 3 - configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="5c8a4-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="5c8a4-269">Di seguito è una tipica configurato per lo sviluppo con la realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="5c8a4-270">Aprire **Unity** e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-270">Open **Unity** and click **New**.</span></span> 

    ![Il portale di Azure](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="5c8a4-272">A questo punto si dovrà fornire un nome di progetto Unity, inserire **MR\_360VideoStreaming.**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="5c8a4-273">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="5c8a4-274">Impostare il percorso a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="5c8a4-275">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-275">Then, click **Create project**.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="5c8a4-277">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="5c8a4-278">Passare a ***modificare* *preferenze*** e quindi dalla nuova finestra, passare al **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="5c8a4-279">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="5c8a4-280">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-280">Close the **Preferences** window.</span></span>

    ![Il portale di Azure](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="5c8a4-282">Passare quindi ad ***File* *Build Settings*** e passare alla piattaforma di **Universal Windows Platform**, facendo clic su di **Commutatore piattaforma** pulsante.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="5c8a4-283">Assicurarsi anche che:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-283">Also make sure that:</span></span>

    1. <span data-ttu-id="5c8a4-284">**Dispositivo di destinazione** è impostata su **qualsiasi dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="5c8a4-285">**Tipo di compilazione** è impostata su **D3D.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="5c8a4-286">**SDK** è impostata su **installata più recente.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="5c8a4-287">**Versione di Visual Studio** è impostata su **installata più recente.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="5c8a4-288">**Compilare ed eseguire** è impostata su **computer locale.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="5c8a4-289">Non è necessario configurare **scene** subito, perché questi valori verranno impostati in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="5c8a4-290">Le impostazioni rimanenti devono essere lasciate come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-290">The remaining settings should be left as default for now.</span></span>

        ![Impostazione del progetto Unity](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="5c8a4-292">Nel **Build Settings** finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il **Inspector** si trova.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="5c8a4-293">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="5c8a4-294">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="5c8a4-295">**Scripting** **versione Runtime** deve essere **stabile** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="5c8a4-296">**Back-end di scripting** deve essere **.NET.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="5c8a4-297">**Livello di compatibilità delle API** deve essere **.NET 4.6.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Impostazione del progetto Unity](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="5c8a4-299">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Impostazione del progetto Unity](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="5c8a4-301">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="5c8a4-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-302">**InternetClient**</span></span>

            ![Impostazione del progetto Unity](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="5c8a4-304">Una volta apportate queste modifiche, chiudere la **Build Settings** finestra.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="5c8a4-305">Salvare il progetto \**File* \*Salva progetto\*\*.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="5c8a4-306">Capitolo 4 - importazione del pacchetto InsideOutSphere Unity</span><span class="sxs-lookup"><span data-stu-id="5c8a4-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5c8a4-307">Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importarlo nel progetto come un [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione **capitolo 5**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="5c8a4-308">È comunque necessario creare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="5c8a4-309">Per questo corso si sarà necessario scaricare un pacchetto di Asset Unity denominati [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="5c8a4-310">Importazione sulle procedure di **file unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="5c8a4-311">Con il dashboard di Unity fronte, fare clic su **Assets** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto > pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="5c8a4-313">Usare il selettore file per selezionare i **InsideOutSphere.unitypackage** del pacchetto e fare clic su **Open**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="5c8a4-314">Verrà visualizzato un elenco di componenti per questo asset all'utente.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="5c8a4-315">Confermare l'importazione facendo **importare**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-315">Confirm the import by clicking **Import**.</span></span>

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="5c8a4-317">Una volta completato l'importazione, si noteranno tre nuove cartelle, **materiali**, **modelli**, e **Prefabs**, sono state aggiunte ad il **asset**cartella.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="5c8a4-318">Questo tipo di struttura di cartelle è tipico per i progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="5c8a4-320">Aprire il **modelli** cartella e si noterà che il **InsideOutSphere** modello è stato importato.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="5c8a4-321">All'interno di **materiali** cartella troveranno le **InsideOutSpheres** materiale *lambert1*, insieme a un materiale chiamato *ButtonMaterial*, che viene usato per il GazeButton, che viene visualizzata a breve.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="5c8a4-322">Il **Prefabs** cartella contiene le **InsideOutSphere** prefab che contiene sia il **InsideOutSphere** *modello* e la  *GazeButton*.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="5c8a4-323">**Non è incluso alcun codice**, si scriverà il codice seguendo questo corso.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="5c8a4-324">All'interno di **gerarchia**, selezionare la **Main Camera** dell'oggetto e aggiornare i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="5c8a4-325">**Transform**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-325">**Transform**</span></span>

        1.  <span data-ttu-id="5c8a4-326">Posizione = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="5c8a4-327">Rotazione = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="5c8a4-328">Scala **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="5c8a4-329">**Fotocamera**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-329">**Camera**</span></span>

        1. <span data-ttu-id="5c8a4-330">**Cancellare i flag**: Colore a tinta unita.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="5c8a4-331">**I piani di ritaglio**: In prossimità di: 0,1, a questo momento: 6.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="5c8a4-333">Passare al **Prefab** cartella e quindi trascinare il **InsideOutSphere** prefab nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="5c8a4-335">Espandere la **InsideOutSphere** dell'oggetto all'interno di **gerarchia** facendo clic sulla piccola freccia accanto a esso.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="5c8a4-336">Si noterà una **figlio** oggetto sotto il chiamato **GazeButton**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="5c8a4-337">Questo verrà utilizzato per modificare le scene e pertanto i video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-337">This will be used to change scenes and thus videos.</span></span>

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="5c8a4-339">Nella finestra di controllo fare clic sui **InsideOutSphere**del componente di trasformazione, assicurarsi che siano impostate le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="5c8a4-340">TRASFORMAZIONE - POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="5c8a4-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-341">**X** 0</span></span>  |          <span data-ttu-id="5c8a4-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-342">**Y** 0</span></span>          |  <span data-ttu-id="5c8a4-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="5c8a4-344">TRASFORMAZIONE - ROTAZIONE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="5c8a4-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-345">**X** 0</span></span>  |          <span data-ttu-id="5c8a4-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="5c8a4-346">**Y** -50</span></span>        |  <span data-ttu-id="5c8a4-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="5c8a4-348">TRANSFORM - SCALE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="5c8a4-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-349">**X** 1</span></span>   |          <span data-ttu-id="5c8a4-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-350">**Y** 1</span></span>          |  <span data-ttu-id="5c8a4-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-351">**Z** 1</span></span>  |

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="5c8a4-353">Fare clic sui **GazeButton** oggetto figlio e set relativo **trasformare** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="5c8a4-354">TRASFORMAZIONE - POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="5c8a4-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="5c8a4-355">**X** 3.6</span></span>|          <span data-ttu-id="5c8a4-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="5c8a4-356">**Y** 1.3</span></span>        |  <span data-ttu-id="5c8a4-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="5c8a4-358">TRASFORMAZIONE - ROTAZIONE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="5c8a4-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-359">**X** 0</span></span>  |          <span data-ttu-id="5c8a4-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-360">**Y** 0</span></span>          |  <span data-ttu-id="5c8a4-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="5c8a4-362">TRANSFORM - SCALE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="5c8a4-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-363">**X** 1</span></span>   |          <span data-ttu-id="5c8a4-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-364">**Y** 1</span></span>          |  <span data-ttu-id="5c8a4-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-365">**Z** 1</span></span>  |

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="5c8a4-367">Capitolo 5 - creare la classe VideoController</span><span class="sxs-lookup"><span data-stu-id="5c8a4-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="5c8a4-368">Il **VideoController** classe ne ospita i due endpoint di video che verrà usato per trasmettere il contenuto dal servizio multimediale di Azure.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="5c8a4-369">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-369">To create this class:</span></span>

1.  <span data-ttu-id="5c8a4-370">Fare doppio clic nella **cartella Asset**che si trova nel **Project** pannello e fare clic su **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="5c8a4-371">Denominare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-371">Name the folder **Scripts**.</span></span>

    ![Creare la classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Creare la classe VideoController](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="5c8a4-374">Fare doppio clic sui **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="5c8a4-375">Fare doppio clic all'interno della cartella, quindi fare clic su **Crea > C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="5c8a4-376">Denominare lo script **VideoController**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-376">Name the script **VideoController**.</span></span>

    ![Creare la classe VideoController](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="5c8a4-378">Fare doppio clic su nuova **VideoController** script per aprirlo con **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Creare la classe VideoController](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="5c8a4-380">Aggiornare gli spazi dei nomi nella parte superiore del file di codice come segue:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="5c8a4-381">Immettere le seguenti variabili nel **VideoController** classe, insieme con la **Awake()** metodo:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="5c8a4-382">È arrivato il momento di immettere gli endpoint dai tuoi video di servizi multimediali di Azure:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="5c8a4-383">Il primo nel *video1endpoint* variabile.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="5c8a4-384">La seconda nel *video2endpoint* variabile.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="5c8a4-385">Si verifica un problema noto con usando *https* in Unity, con versione 2017.4.1f1.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="5c8a4-386">Se i video di forniscono un errore in play, provare a utilizzare 'http'.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="5c8a4-387">Successivamente, il **Start ()** metodo deve essere modificato.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="5c8a4-388">Questo metodo verrà attivato ogni volta che l'utente passa scena (cambio, di conseguenza, il video) esaminando il pulsante estasiati.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="5c8a4-389">Seguendo la **Start ()** metodo, inserire il **playVideo ()** *IEnumerator* metodo, che verrà usato per avviare i video facilmente (in modo che non si verifica alcuna segnalazione).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="5c8a4-390">Quest'ultimo metodo è necessario per questa classe è il **ChangeScene()** metodo, che verrà usato per scambiare tra le scene.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="5c8a4-391">Il **ChangeScene()** metodo utilizza un comodo C\# funzionalità denominata di *operatore condizionale*.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="5c8a4-392">In questo modo le condizioni da controllare e quindi i valori restituiti in base il risultato della verifica, tutto all'interno di una singola istruzione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="5c8a4-393">Seguire questo [collegamento per altre informazioni sull'operatore condizionale](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="5c8a4-394">Salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="5c8a4-395">Indietro nell'Editor di Unity, fare clic e trascinare il **VideoController** classe [da] {.underline} il **script** cartella per il **Main Camera** dell'oggetto nel  **Gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="5c8a4-396">Fare clic sui **Main Camera** ed esaminare le **Pannello di controllo**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="5c8a4-397">Si noterà che all'interno del componente di Script appena aggiunto, vi è un campo con un valore vuoto.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="5c8a4-398">Si tratta di un campo di riferimento, fa riferimento a variabili pubbliche all'interno del codice.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="5c8a4-399">Trascinare il **InsideOutSphere** dall'oggetto il **Pannello di gerarchia** per il **sfera** slot, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="5c8a4-400">![Creare la classe VideoController](images/AzureLabs-Lab6-47.png)
    ![creare la classe VideoController](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="5c8a4-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="5c8a4-401">Capitolo 6: creare la classe sguardo</span><span class="sxs-lookup"><span data-stu-id="5c8a4-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="5c8a4-402">Questa classe è responsabile per la creazione di un **Raycast** che beprojected inoltrerà dalle **Main Camera**, per rilevare l'oggetto sta guardando l'utente.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="5c8a4-403">In questo caso, il **Raycast** sarà necessario identificare se l'utente sta guardando il **GazeButton** oggetti nella scena e attivare un comportamento.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="5c8a4-404">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-404">To create this Class:</span></span>

1.  <span data-ttu-id="5c8a4-405">Andare alla **script** cartella creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="5c8a4-406">Fare doppio clic nella **Project** Pannello di \**creare* \*C\# Script\*\*.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="5c8a4-407">Denominare lo script **estasiati**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="5c8a4-408">Fare doppio clic su nuova ***estasiati*** script per aprirlo con **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="5c8a4-409">Verificare che sia lo spazio dei nomi seguente all'inizio dello script e rimuovere tutte le altre:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="5c8a4-410">Quindi aggiungere le variabili seguenti all'interno di **estasiati** classe:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="5c8a4-411">Il codice per il **Awake()** e **Start ()** metodi deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="5c8a4-412">Aggiungere il codice seguente nel **Update ()** metodo per proiettare un Raycast e rilevare il calo di destinazione:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="5c8a4-413">Salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="5c8a4-414">Fare clic e trascinare il **estasiati** classe dalla cartella degli script per l'oggetto Main Camera nel **gerarchia** pannello.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="5c8a4-415">Capitolo 7 - installazione le due scene di Unity</span><span class="sxs-lookup"><span data-stu-id="5c8a4-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="5c8a4-416">Lo scopo di questo capitolo è per configurare le due scene, ognuno dei quali ospita un video in stream.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="5c8a4-417">Verranno duplicati della scena è già stato creato, in modo che non devi reimpostarlo, anche se si modificherà quindi la nuova scena, in modo che il *GazeButton* oggetto è in una posizione diversa e ha un aspetto diverso.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="5c8a4-418">Ciò sta a indicare come cambiare tra le scene.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="5c8a4-419">Eseguire questa operazione passando a **File > Salva scena come...** . Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="5c8a4-420">Scegliere il **nuova cartella** pulsante.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-420">Click the **New folder** button.</span></span>

    ![Capitolo 7 - installazione le due scene di Unity](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="5c8a4-422">Denominare la cartella **scene**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="5c8a4-423">Il **Salva scena** finestra saranno ancora aperta.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="5c8a4-424">Aprire l'appena creato **scene** cartella.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="5c8a4-425">Nel **nome File:** campo di testo, digitare **VideoScene1**, quindi premere **Salva**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="5c8a4-426">In Unity, aprire il **scene** la cartella e quindi fare clic sui **VideoScene1** file.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="5c8a4-427">Utilizzare la tastiera, premere **Ctrl + D** verranno duplicati tale scena</span><span class="sxs-lookup"><span data-stu-id="5c8a4-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="5c8a4-428">Il **duplicato** comandi possono essere eseguiti anche passando a **Modifica > duplicato**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="5c8a4-429">Unity automaticamente incrementare il numero di nomi di scena, ma verificare, in modo che corrisponda il codice inserito in precedenza.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="5c8a4-430">È necessario disporre **VideoScene1** e **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="5c8a4-431">Con le due scene, andare al **File > Build Settings**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="5c8a4-432">Con il **Build Settings** finestra aperta, trascinare gli in modo invisibile per il **scene nella compilazione** sezione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="5c8a4-434">È possibile selezionare entrambe le scene le **scene** cartella tramite azienda il **Ctrl** pulsante, quindi mouse ogni scena e infine trascinare entrambi in.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="5c8a4-435">Chiudi il **Build Settings** finestra e fare doppio clic sul **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="5c8a4-436">Con il secondo scena aperta, fare clic sul **GazeButton** oggetto figlio del **InsideOutSphere**e impostare la trasformazione corrispondente come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="5c8a4-437">TRASFORMAZIONE - POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="5c8a4-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-438">**X** 0</span></span>  |         <span data-ttu-id="5c8a4-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="5c8a4-439">**Y** 1.3</span></span>         | <span data-ttu-id="5c8a4-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="5c8a4-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="5c8a4-441">TRASFORMAZIONE - ROTAZIONE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="5c8a4-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-442">**X** 0</span></span>  |          <span data-ttu-id="5c8a4-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-443">**Y** 0</span></span>          |  <span data-ttu-id="5c8a4-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="5c8a4-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="5c8a4-445">TRANSFORM - SCALE</span><span class="sxs-lookup"><span data-stu-id="5c8a4-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="5c8a4-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-446">**X** 1</span></span>   |          <span data-ttu-id="5c8a4-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-447">**Y** 1</span></span>          |  <span data-ttu-id="5c8a4-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="5c8a4-448">**Z** 1</span></span>  |

10. <span data-ttu-id="5c8a4-449">Con il **GazeButton** figlio ancora selezionato, cercare nel **Inspector** e il **Mesh filtro**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="5c8a4-450">Fare clic accanto alla destinazione little il **Mesh** campo di riferimento:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="5c8a4-452">Oggetto **Mesh selezionare** verrà visualizzata la finestra popup.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="5c8a4-453">Fare doppio clic il **cubo** mesh dall'elenco dei **asset**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="5c8a4-455">Il **filtro Mesh** consente di aggiornare e ora da un **cubo**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="5c8a4-456">A questo punto, fare clic sui **a forma di ingranaggio** icona accanto a **sfera Collider** e fare clic su **Rimuovi componente**, eliminare l'oggetto collider da questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="5c8a4-458">Con il **GazeButton** ancora selezionato, fare clic sul **Add Component** nella parte inferiore del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="5c8a4-459">Nel campo di ricerca, digitare **finestra**, e **casella Collider** sarà un'opzione: fare clic per aggiungere un **casella Collider** per il **GazeButton** oggetto .</span><span class="sxs-lookup"><span data-stu-id="5c8a4-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="5c8a4-461">Il **GazeButton** è ora aggiornata parzialmente, per un aspetto diverso, tuttavia, ora si creerà un nuovo **materiale**, in modo che il servizio ha un aspetto completamente diverso ed è più facile da riconoscere come un oggetto diverso, rispetto al oggetto in prima scena.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="5c8a4-462">Passare alle **materiali** cartella, all'interno di **pannello progetto**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="5c8a4-463">Duplica il **ButtonMaterial** materiale (premere **Ctrl** + **1!d** sulla tastiera o fare clic sul **materiale**, quindi dal **Edit** opzione di menu, selezionare file **duplicato**).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="5c8a4-464">![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-55.png)
    ![capitolo 7: configurare le due scene di Unity](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="5c8a4-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="5c8a4-465">Selezionare la nuova **ButtonMaterial** materiale (qui denominata **1 ButtonMaterial**) e all'interno di **Inspector**, fare clic sul **Albedo** colore finestra.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="5c8a4-466">Verrà visualizzata una finestra popup, in cui è possibile selezionare un altro colore (scegliere a seconda di quale si desidera), quindi chiudere la finestra popup.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="5c8a4-467">Il materiale sarà una propria istanza e diversi con la versione originale.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-467">The Material will be its own instance, and different to the original.</span></span>

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="5c8a4-469">Trascinare la nuova **materiale** nel **GazeButton** figlio, a questo punto aggiornare completamente aspetto, in modo che risulti facilmente distinguibile dal primo pulsante in background.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="5c8a4-471">A questo punto è possibile testare il progetto nell'Editor prima di compilare il progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="5c8a4-472">Premere il **riprodurre** pulsante il **Editor** e wear le cuffie.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="5c8a4-474">Esaminare i due **GazeButton** oggetti da passare tra il primo e il secondo video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="5c8a4-475">Capitolo 8 - compilare la soluzione di piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="5c8a4-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="5c8a4-476">Dopo aver verificato che l'editor non dispone di alcun errore, sei pronto per la compilazione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="5c8a4-477">Per compilare:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-477">To Build:</span></span>

1.  <span data-ttu-id="5c8a4-478">Salvare nella scena corrente facendo clic su **File > Salva**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="5c8a4-479">Selezionare la casella denominata **C Unity\# progetti** (questo è importante poiché ciò permette di modificare le classi dopo la compilazione è stata completata).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="5c8a4-480">Passare a **File > Build Settings**, fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="5c8a4-481">Viene chiesto di selezionare la cartella in cui si desidera buildthe soluzione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="5c8a4-482">Creare un **COMPILAZIONI** cartella e all'interno della cartella creare un'altra cartella con un nome appropriato di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="5c8a4-483">Fare clic sulla nuova cartella e quindi fare clic su **selezionare la cartella**, pertanto, per scegliere quella cartella, per avviare la compilazione nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="5c8a4-484">![Capitolo 8 - Compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab6-60.png)
    ![capitolo 8 - compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="5c8a4-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="5c8a4-485">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="5c8a4-486">Capitolo 9 - distribuire nel computer locale</span><span class="sxs-lookup"><span data-stu-id="5c8a4-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="5c8a4-487">Dopo aver completata la compilazione, un **Esplora File** verrà visualizzata la finestra in corrispondenza della posizione della compilazione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="5c8a4-488">Aprire la cartella è denominata e compilata per, quindi fare doppio clic sul file di soluzione (sln) da quella cartella, aprire la soluzione con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="5c8a4-489">L'unico a sinistra è distribuire l'app nel computer (o *computer locale*).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="5c8a4-490">Per distribuire nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="5c8a4-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="5c8a4-491">Nelle **Visual Studio 2017**, aprire il file di soluzione che è stato appena creato.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="5c8a4-492">Nel **piattaforma soluzione**, selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="5c8a4-493">Nel **configurazione della soluzione** selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Capitolo 9 - Distribuire nel computer locale](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="5c8a4-495">A questo punto, è necessario ripristinare tutti i pacchetti della soluzione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="5c8a4-496">Fare clic sui **soluzione**, fare clic su **Ripristina pacchetti NuGet per la soluzione...**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="5c8a4-497">Ciò avviene perché i pacchetti che Unity compilate necessarie da impostare come destinazione per l'uso con i riferimenti del computer locale.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="5c8a4-498">Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="5c8a4-499">Visual Studio verrà innanzitutto compilare e distribuire l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="5c8a4-500">L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Capitolo 9 - Distribuire nel computer locale](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="5c8a4-502">Quando si esegue l'applicazione di realtà mista, saranno è essere all'interno di **InsideOutSphere** modello che è stato utilizzato all'interno dell'app.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="5c8a4-503">Questo sfera saranno in cui il video verrà trasmesso, fornendo una visualizzazione a 360 gradi, di video in ingresso (che per questo tipo di punto di vista è stato filmato).</span><span class="sxs-lookup"><span data-stu-id="5c8a4-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="5c8a4-504">Non sorprendere che se il video richiede un paio di secondi per caricare, l'app è soggetto alle velocità di Internet disponibile, come il video deve essere recuperate e quindi scaricati, pertanto per lo streaming nell'app.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="5c8a4-505">Quando si è pronti, modificare le scene e aprire il secondo video, gazing alla sfera rossa!</span><span class="sxs-lookup"><span data-stu-id="5c8a4-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="5c8a4-506">Quindi è possibile tornare indietro, mediante il cubo blu nella scena secondo!</span><span class="sxs-lookup"><span data-stu-id="5c8a4-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="5c8a4-507">L'applicazione di servizi multimediali di Azure completata</span><span class="sxs-lookup"><span data-stu-id="5c8a4-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="5c8a4-508">Complimenti, è stata compilata un'app per realtà mista che si avvale di servizi multimediali di Azure per trasmettere in streaming 360 video.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![risultato di Lab](images/AzureLabs-Lab6-00.png)

![risultato di Lab](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="5c8a4-511">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="5c8a4-511">Bonus Exercises</span></span>

<span data-ttu-id="5c8a4-512">**Esercizio 1**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-512">**Exercise 1**</span></span>

<span data-ttu-id="5c8a4-513">È assolutamente possibile utilizzare solo un'unica scena per modificare i video all'interno di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="5c8a4-514">Provare a usare l'applicazione e trasformarlo in un'unica scena.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="5c8a4-515">Aggiungere anche un altro video alla combinazione.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="5c8a4-516">**Esercizio 2**</span><span class="sxs-lookup"><span data-stu-id="5c8a4-516">**Exercise 2**</span></span>

<span data-ttu-id="5c8a4-517">Sperimentare con Unity e Azure e provare a implementare la possibilità per l'app selezionare automaticamente un video con una dimensione di file diverso, a seconda della complessità di una connessione a Internet.</span><span class="sxs-lookup"><span data-stu-id="5c8a4-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


