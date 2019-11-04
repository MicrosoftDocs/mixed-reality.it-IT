---
title: MR e Azure 306-video di streaming
description: Completare questo corso per apprendere come implementare servizi multimediali di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, servizi multimediali, streaming video, 360, immersiva, VR
ms.openlocfilehash: 6585aa731ff7ebb89beae67ab0b61ac5ef026e47
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438568"
---
>[!NOTE]
><span data-ttu-id="4c8bb-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="4c8bb-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="4c8bb-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="4c8bb-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="4c8bb-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="4c8bb-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="4c8bb-110">MR e Azure 306: video di streaming</span><span class="sxs-lookup"><span data-stu-id="4c8bb-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="4c8bb-111">![prodotto finale](images/AzureLabs-Lab6-00.png)
![inizio](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="4c8bb-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="4c8bb-112">In questo corso si apprenderà come connettere i servizi multimediali di Azure a un'esperienza di VR per la realtà mista di Windows per consentire la riproduzione video in streaming di 360 gradi su cuffie immersive.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="4c8bb-113">**Servizi multimediali di Azure** è una raccolta di servizi che offre servizi di streaming video di qualità broadcast per raggiungere un numero elevato di destinatari sui dispositivi mobili attualmente più diffusi.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="4c8bb-114">Per altre informazioni, visitare la [pagina servizi multimediali di Azure](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="4c8bb-115">Dopo aver completato questo corso, si disporrà di un'applicazione per cuffie immersiva mista, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="4c8bb-116">Recuperare un video di 360 Degree da un' **archiviazione di Azure**tramite il **servizio multimediale di Azure**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="4c8bb-117">Visualizza il video recuperato di 360 Degree in una scena Unity.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="4c8bb-118">Spostarsi tra due scene, con due video diversi.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="4c8bb-119">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="4c8bb-120">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="4c8bb-121">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="4c8bb-122">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="4c8bb-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4c8bb-123">Corso</span><span class="sxs-lookup"><span data-stu-id="4c8bb-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="4c8bb-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4c8bb-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4c8bb-125"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="4c8bb-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4c8bb-126">MR e Azure 306: video di streaming</span><span class="sxs-lookup"><span data-stu-id="4c8bb-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="4c8bb-127">✔️</span><span class="sxs-lookup"><span data-stu-id="4c8bb-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="4c8bb-128">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="4c8bb-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="4c8bb-129">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="4c8bb-130">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="4c8bb-131">È possibile utilizzare il software più recente, come indicato nell' [articolo installare gli strumenti](install-the-tools.md), ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="4c8bb-132">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="4c8bb-133">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="4c8bb-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="4c8bb-134">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="4c8bb-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4c8bb-135">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="4c8bb-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4c8bb-136">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="4c8bb-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4c8bb-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4c8bb-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="4c8bb-138">[Cuffia A realtà mista (VR) di Windows](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="4c8bb-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="4c8bb-139">Accesso a Internet per l'installazione di Azure e il recupero dei dati</span><span class="sxs-lookup"><span data-stu-id="4c8bb-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="4c8bb-140">Video di 2 360 gradi in formato MP4 (è possibile trovare alcuni video senza diritti d'autore [in questa pagina di download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="4c8bb-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="4c8bb-141">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="4c8bb-141">Before you start</span></span>

1.  <span data-ttu-id="4c8bb-142">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="4c8bb-143">Configurare e testare l'auricolare immersiva della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4c8bb-144">**Non** sarà necessario alcun controller di movimento per questo corso.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="4c8bb-145">Se è necessario supportare la configurazione dell'auricolare immersivo, fare clic [sul collegamento per configurare la realtà mista di Windows](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="4c8bb-146">Capitolo 1-portale di Azure: creazione dell'account di archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="4c8bb-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="4c8bb-147">Per usare il **servizio di archiviazione di Azure**, è necessario creare e configurare un **account di archiviazione** nell'portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="4c8bb-148">Accedere al portale di [Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="4c8bb-149">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="4c8bb-150">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="4c8bb-151">Una volta effettuato l'accesso, fare clic su **account di archiviazione** nel menu a sinistra.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="4c8bb-153">Nella scheda **account di archiviazione** fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="4c8bb-155">Nella scheda **Crea account di archiviazione** :</span><span class="sxs-lookup"><span data-stu-id="4c8bb-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="4c8bb-156">Inserire un **nome** per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="4c8bb-157">Per **modello di distribuzione** selezionare **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="4c8bb-158">Per **tipo di account**selezionare **archiviazione (utilizzo generico V1)** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="4c8bb-159">Per **prestazioni**, selezionare \**standard *.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="4c8bb-160">Per la **replica** selezionare **archiviazione con ridondanza locale (con ridondanza locale)** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="4c8bb-161">Lasciare il **trasferimento sicuro necessario** come **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="4c8bb-162">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="4c8bb-163">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="4c8bb-164">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="4c8bb-165">Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="4c8bb-166">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="4c8bb-167">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="4c8bb-168">È necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="4c8bb-170">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="4c8bb-171">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="4c8bb-173">A questo punto non è necessario seguire la risorsa, ma è sufficiente passare al capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="4c8bb-174">Capitolo 2-portale di Azure: creazione del servizio multimediale</span><span class="sxs-lookup"><span data-stu-id="4c8bb-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="4c8bb-175">Per usare il servizio multimediale di Azure, è necessario configurare un'istanza del servizio da rendere disponibile all'applicazione (dove il titolare dell'account deve essere un amministratore).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="4c8bb-176">Nel portale di Azure fare clic su **Crea una risorsa** nell'angolo in alto a sinistra e cercare **servizio multimediale,** quindi premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="4c8bb-177">La risorsa desiderata dispone attualmente di un'icona rosa; fare clic su questo pulsante per visualizzare una nuova pagina.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="4c8bb-179">La nuova pagina fornirà una descrizione del **servizio multimediale**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="4c8bb-180">Nella parte inferiore sinistra del prompt, fare clic sul pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="4c8bb-182">Una volta fatto clic su **Crea** , verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli sul nuovo servizio multimediale:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="4c8bb-183">Inserire il **nome dell'account** desiderato per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="4c8bb-184">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="4c8bb-185">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="4c8bb-186">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="4c8bb-187">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="4c8bb-188">Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire i gruppi di risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="4c8bb-189">Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="4c8bb-190">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="4c8bb-191">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="4c8bb-192">Per la sezione **account di archiviazione** , fare clic sulla sezione **selezionare...** , quindi fare clic sull'account di **archiviazione** creato nell'ultimo capitolo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="4c8bb-193">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="4c8bb-194">Fai clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-194">Click **Create**.</span></span>

        ![Portale di Azure](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="4c8bb-196">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="4c8bb-197">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="4c8bb-199">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-199">Click on the notification to explore your new Service instance.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="4c8bb-201">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="4c8bb-202">Nella pagina nuovo servizio multimediale, all'interno del pannello a sinistra, fare clic sul collegamento **Asset** , che è circa a metà.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="4c8bb-203">Nella pagina successiva, nell'angolo in alto a sinistra della pagina, fare clic su **carica**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="4c8bb-205">Fare clic sull'icona della **cartella** per sfogliare i file e selezionare il primo video 360 che si desidera trasmettere in streaming.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="4c8bb-206">È possibile seguire questo [collegamento per scaricare un video di esempio](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="4c8bb-208">I nomi di file lunghi possono causare un problema con il codificatore: pertanto, per assicurarsi che i video non richiedano problemi, è consigliabile abbreviare la lunghezza dei nomi dei file video.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="4c8bb-209">L'indicatore di stato diventerà verde al termine del caricamento del video.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="4c8bb-211">Fai clic sul testo precedente (**yourservicename-assets**) per tornare alla pagina **Asset** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="4c8bb-212">Si noterà che il video è stato caricato correttamente.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="4c8bb-213">Fare clic su di essa.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-213">Click on it.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="4c8bb-215">Nella pagina a cui si è reindirizzati verranno visualizzate informazioni dettagliate sul video.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="4c8bb-216">Per poter usare il video, è necessario codificarlo facendo clic sul pulsante Encode ( **codifica** ) nella parte superiore sinistra della pagina.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="4c8bb-218">Verrà visualizzato un nuovo pannello a destra, in cui sarà possibile impostare le opzioni di codifica per il file.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="4c8bb-219">Impostare le proprietà seguenti (alcune saranno già impostate per impostazione predefinita):</span><span class="sxs-lookup"><span data-stu-id="4c8bb-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="4c8bb-220">**Nome codificatore multimediale *Media Encoder standard***</span><span class="sxs-lookup"><span data-stu-id="4c8bb-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="4c8bb-221">**Codifica del contenuto preimpostato *contenuto MP4 a più velocità in bit***</span><span class="sxs-lookup"><span data-stu-id="4c8bb-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="4c8bb-222">**Nome processo *Media Encoder standard l'elaborazione di video1. mp4***</span><span class="sxs-lookup"><span data-stu-id="4c8bb-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="4c8bb-223">**Nome asset del supporto *di output video1. MP4--Media Encoder standard codificato***</span><span class="sxs-lookup"><span data-stu-id="4c8bb-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Portale di Azure](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="4c8bb-225">Fare clic sul pulsante **Crea**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="4c8bb-226">Si noterà una barra con il **processo di codifica aggiunto**, si fa clic su tale barra e viene visualizzato un pannello con lo stato di codifica visualizzato.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-17.png)

    ![Portale di Azure](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="4c8bb-229">Attendere il completamento del processo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="4c8bb-230">Al termine, è possibile chiudere il pannello con ' X ' nella parte superiore destra del pannello.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-19.png)

    ![Portale di Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="4c8bb-233">Il tempo necessario dipende dalla dimensione del file del video.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="4c8bb-234">Questo processo può richiedere molto tempo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="4c8bb-235">Ora che è stata creata la versione codificata del video, è possibile pubblicarla per renderla accessibile.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="4c8bb-236">A tale scopo, fare clic sulle **risorse** dei collegamenti blu per tornare alla pagina asset.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="4c8bb-238">Il video verrà visualizzato insieme a un altro, che è di **tipo asset con _MP4 a bitrate multipli_** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="4c8bb-240">È possibile notare che il nuovo asset, insieme al video iniziale, è *sconosciuto*e contiene ' 0' byte per la **dimensione**, ma è sufficiente aggiornare la finestra affinché venga aggiornata.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="4c8bb-241">Fare clic su questo nuovo asset.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-241">Click this new asset.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="4c8bb-243">Verrà visualizzato un pannello simile a quello usato in precedenza, ma si tratta di un asset diverso.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="4c8bb-244">Fare clic sul pulsante **pubblica** nella parte superiore del centro della pagina.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="4c8bb-246">Verrà richiesto di impostare un **localizzatore**, ovvero il punto di ingresso, per file/s negli asset.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="4c8bb-247">Per lo scenario, impostare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="4c8bb-248">**Tipo di localizzatore** > **progressive**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="4c8bb-249">La **Data** e l' **ora** verranno impostate per l'utente, dalla data corrente, a un'ora futura (100 anni in questo caso).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="4c8bb-250">Lasciarlo invariato o modificarlo in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4c8bb-251">Per altre informazioni sui localizzatori e sulle opzioni che è possibile scegliere, vedere la [documentazione di servizi multimediali di Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="4c8bb-252">Nella parte inferiore del pannello fare clic sul pulsante **Aggiungi** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="4c8bb-254">Il video è ora pubblicato e può essere trasmesso tramite il relativo endpoint.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="4c8bb-255">La pagina è una sezione di **file** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="4c8bb-256">Questo è il punto in cui saranno le diverse versioni codificate del video.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="4c8bb-257">Selezionare la risoluzione più alta possibile (nell'immagine seguente è il file 1920x960) e quindi verrà visualizzato un pannello a destra.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="4c8bb-258">Qui sarà disponibile un **URL di download**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="4c8bb-259">Copiare questo **endpoint** come verrà usato in un secondo momento nel codice.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-26.png)    

    ![Portale di Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="4c8bb-262">È anche possibile premere il pulsante **Riproduci** per riprodurre il video e testarlo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="4c8bb-263">È ora necessario caricare il secondo video che verrà usato in questo Lab.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="4c8bb-264">Seguire i passaggi precedenti, ripetendo lo stesso processo per il secondo video.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="4c8bb-265">Assicurarsi di copiare anche il secondo **endpoint** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="4c8bb-266">Usare il [collegamento seguente per scaricare un secondo video](https://vimeo.com/214402865).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="4c8bb-267">Dopo la pubblicazione di entrambi i video, è possibile passare al capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="4c8bb-268">Capitolo 3-configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="4c8bb-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="4c8bb-269">Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="4c8bb-270">Aprire **Unity** e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-270">Open **Unity** and click **New**.</span></span> 

    ![Portale di Azure](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="4c8bb-272">A questo punto sarà necessario specificare un nome di progetto Unity, inserire **MR\_360VideoStreaming.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="4c8bb-273">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="4c8bb-274">Impostare il percorso su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="4c8bb-275">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-275">Then, click **Create project**.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="4c8bb-277">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="4c8bb-278">Passare a ***modifica* *Preferenze*** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="4c8bb-279">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="4c8bb-280">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-280">Close the **Preferences** window.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="4c8bb-282">Passare quindi a  ***impostazioni di compilazione* File** e passare alla piattaforma **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="4c8bb-283">Assicurarsi inoltre che:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-283">Also make sure that:</span></span>

    1. <span data-ttu-id="4c8bb-284">Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="4c8bb-285">Il **tipo di compilazione** è impostato su **D3D.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="4c8bb-286">**SDK** è impostato sull' **ultima versione installata.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="4c8bb-287">La **versione di Visual Studio** è impostata su **installazione più recente.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="4c8bb-288">**Compilazione ed esecuzione** è impostato su **computer locale.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="4c8bb-289">Non preoccuparti di configurare le **scene** in questo momento, perché verranno impostate in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="4c8bb-290">Per il momento le impostazioni rimanenti devono essere lasciate come predefinite.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-290">The remaining settings should be left as default for now.</span></span>

        ![Configurazione del progetto Unity](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="4c8bb-292">Nella finestra **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="4c8bb-293">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="4c8bb-294">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="4c8bb-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="4c8bb-295">La **versione di runtime** di **Scripting** deve essere **stabile** (equivalente a .NET 3,5).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="4c8bb-296">Il **back-end di scripting** deve essere **.NET.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="4c8bb-297">Il **livello di compatibilità API** deve essere **.NET 4,6.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Configurazione del progetto Unity](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="4c8bb-299">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurazione del progetto Unity](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="4c8bb-301">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="4c8bb-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-302">**InternetClient**</span></span>

            ![Configurazione del progetto Unity](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="4c8bb-304">Dopo aver apportato queste modifiche, chiudere la finestra **impostazioni di compilazione** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="4c8bb-305">Salvare il progetto \**file* \* Salva progetto \* \*.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="4c8bb-306">Capitolo 4-importazione del pacchetto InsideOutSphere Unity</span><span class="sxs-lookup"><span data-stu-id="4c8bb-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c8bb-307">Se si desidera ignorare il componente di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile scaricarlo [. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal **capitolo 5**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="4c8bb-308">Sarà comunque necessario creare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="4c8bb-309">Per questo corso sarà necessario scaricare un pacchetto di asset Unity denominato [**InsideOutSphere. file unitypackage Tools**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="4c8bb-310">Procedura: importare il **file unitypackage Tools**:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="4c8bb-311">Con il dashboard Unity, fare clic su **Asset** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto > pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="4c8bb-313">Usare il selettore file per selezionare il pacchetto **InsideOutSphere. file unitypackage Tools** e fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="4c8bb-314">Verrà visualizzato un elenco di componenti per questo asset.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="4c8bb-315">Confermare l'importazione facendo clic su **Importa**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-315">Confirm the import by clicking **Import**.</span></span>

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="4c8bb-317">Una volta completata l'importazione, si noterà che nella cartella **assets** sono state aggiunte tre nuove cartelle, **materiali**, **modelli**e **prefabbricati**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="4c8bb-318">Questo tipo di struttura di cartelle è tipico per un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="4c8bb-320">Aprire la cartella **Models (modelli** ). si noterà che il modello **InsideOutSphere** è stato importato.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="4c8bb-321">All'interno della cartella **Materials (materiali** ) troverete il materiale **InsideOutSpheres** *lambert1*, insieme a un materiale denominato *ButtonMaterial*, che viene usato da GazeButton, che verrà visualizzato a breve.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="4c8bb-322">La cartella **Prefabbricates** contiene la prefabbricazione **InsideOutSphere** che contiene il *modello* **InsideOutSphere** e *GazeButton*.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="4c8bb-323">**Non è incluso alcun codice**, il codice verrà scritto seguendo questo corso.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="4c8bb-324">All'interno della **gerarchia**selezionare l'oggetto **principale della fotocamera** e aggiornare i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="4c8bb-325">**Trasformazione**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-325">**Transform**</span></span>

        1.  <span data-ttu-id="4c8bb-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="4c8bb-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="4c8bb-328">Scala **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="4c8bb-329">**Fotocamera**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-329">**Camera**</span></span>

        1. <span data-ttu-id="4c8bb-330">**Cancella flag**: colore a tinta unita.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="4c8bb-331">**Piani di ritaglio**: Near: 0,1, lontano: 6.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="4c8bb-333">Passare alla cartella **prefabbricata** , quindi trascinare la prefabbricata **InsideOutSphere** nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="4c8bb-335">Espandere l'oggetto **InsideOutSphere** all'interno della **gerarchia** facendo clic sulla piccola freccia accanto.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="4c8bb-336">Verrà visualizzato un oggetto **figlio** sotto il nome **GazeButton**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="4c8bb-337">Questa operazione verrà usata per modificare le scene e quindi i video.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-337">This will be used to change scenes and thus videos.</span></span>

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="4c8bb-339">Nella finestra di controllo fare clic sul componente di trasformazione di **InsideOutSphere**, verificare che siano impostate le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="4c8bb-340">TRASFORMAZIONE-POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="4c8bb-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4c8bb-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-341">**X** 0</span></span>  |          <span data-ttu-id="4c8bb-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-342">**Y** 0</span></span>          |  <span data-ttu-id="4c8bb-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="4c8bb-344">TRASFORMAZIONE-ROTAZIONE</span><span class="sxs-lookup"><span data-stu-id="4c8bb-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4c8bb-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-345">**X** 0</span></span>  |          <span data-ttu-id="4c8bb-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="4c8bb-346">**Y** -50</span></span>        |  <span data-ttu-id="4c8bb-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="4c8bb-348">TRASFORMAZIONE-RIDIMENSIONA</span><span class="sxs-lookup"><span data-stu-id="4c8bb-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="4c8bb-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-349">**X** 1</span></span>   |          <span data-ttu-id="4c8bb-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-350">**Y** 1</span></span>          |  <span data-ttu-id="4c8bb-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-351">**Z** 1</span></span>  |

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="4c8bb-353">Fare clic sull'oggetto figlio **GazeButton** e impostare la relativa **trasformazione** come segue:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="4c8bb-354">TRASFORMAZIONE-POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="4c8bb-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4c8bb-355">**X** 3,6</span><span class="sxs-lookup"><span data-stu-id="4c8bb-355">**X** 3.6</span></span>|          <span data-ttu-id="4c8bb-356">**Y** 1,3</span><span class="sxs-lookup"><span data-stu-id="4c8bb-356">**Y** 1.3</span></span>        |  <span data-ttu-id="4c8bb-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="4c8bb-358">TRASFORMAZIONE-ROTAZIONE</span><span class="sxs-lookup"><span data-stu-id="4c8bb-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4c8bb-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-359">**X** 0</span></span>  |          <span data-ttu-id="4c8bb-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-360">**Y** 0</span></span>          |  <span data-ttu-id="4c8bb-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="4c8bb-362">TRASFORMAZIONE-RIDIMENSIONA</span><span class="sxs-lookup"><span data-stu-id="4c8bb-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="4c8bb-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-363">**X** 1</span></span>   |          <span data-ttu-id="4c8bb-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-364">**Y** 1</span></span>          |  <span data-ttu-id="4c8bb-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-365">**Z** 1</span></span>  |

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="4c8bb-367">Capitolo 5: creare la classe VideoController</span><span class="sxs-lookup"><span data-stu-id="4c8bb-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="4c8bb-368">La classe **VideoController** ospita i due endpoint video che verranno usati per lo streaming del contenuto da servizi multimediali di Azure.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="4c8bb-369">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-369">To create this class:</span></span>

1.  <span data-ttu-id="4c8bb-370">Fare clic con il pulsante destro del mouse nella **cartella Asset**, che si trova nel pannello **progetto** , quindi fare clic su **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="4c8bb-371">Denominare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-371">Name the folder **Scripts**.</span></span>

    ![Creazione della classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Creazione della classe VideoController](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="4c8bb-374">Fare doppio clic sulla cartella **script** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="4c8bb-375">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi fare clic su **crea > C\# script**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="4c8bb-376">Denominare lo script **VideoController**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-376">Name the script **VideoController**.</span></span>

    ![Creazione della classe VideoController](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="4c8bb-378">Fare doppio clic sul nuovo script **VideoController** per aprirlo con **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Creazione della classe VideoController](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="4c8bb-380">Aggiornare gli spazi dei nomi all'inizio del file di codice nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="4c8bb-381">Immettere le variabili seguenti nella classe **VideoController** insieme al metodo **svegli ()** :</span><span class="sxs-lookup"><span data-stu-id="4c8bb-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

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

7.  <span data-ttu-id="4c8bb-382">A questo punto è possibile immettere gli endpoint dai video di servizi multimediali di Azure:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="4c8bb-383">Primo oggetto nella variabile *video1endpoint* .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="4c8bb-384">Il secondo oggetto nella variabile *video2endpoint* .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="4c8bb-385">Si è verificato un problema noto relativo all'uso di *https* in Unity, con la versione 2017.4.1 F1.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="4c8bb-386">Se i video forniscono un errore di riproduzione, provare a usare "http".</span><span class="sxs-lookup"><span data-stu-id="4c8bb-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="4c8bb-387">Successivamente, è necessario modificare il metodo **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="4c8bb-388">Questo metodo verrà attivato ogni volta che l'utente passa dalla scena (quindi passa il video) esaminando il pulsante con lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="4c8bb-389">Dopo il metodo **Start ()** , inserire il metodo **PlayVideo ()** *IEnumerator* , che verrà usato per avviare i video senza interruzioni (pertanto non viene visualizzata alcuna balbuzie).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

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

10. <span data-ttu-id="4c8bb-390">L'ultimo metodo necessario per questa classe è il metodo **ChangeScene ()** , che verrà usato per scambiare tra le scene.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="4c8bb-391">Il metodo **ChangeScene ()** usa una funzionalità di\# C utile chiamata *operatore condizionale*.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="4c8bb-392">In questo modo è possibile controllare le condizioni e i valori restituiti in base al risultato del controllo, il tutto all'interno di un'unica istruzione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="4c8bb-393">Seguire questo [collegamento per altre informazioni sull'operatore condizionale](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="4c8bb-394">Salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="4c8bb-395">Nell'editor di Unity fare clic e trascinare la classe **VideoController** [from] {. Underline} la cartella **Scripts** nell'oggetto **principale della fotocamera** nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="4c8bb-396">Fare clic sulla **fotocamera principale** ed esaminare il **pannello Inspector**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="4c8bb-397">Si noterà che all'interno del componente script appena aggiunto è presente un campo con un valore vuoto.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="4c8bb-398">Si tratta di un campo di riferimento, che ha come destinazione le variabili pubbliche all'interno del codice.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="4c8bb-399">Trascinare l'oggetto **InsideOutSphere** dal **Pannello gerarchia** allo slot **Sphere** , come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="4c8bb-400">![creare la classe VideoController](images/AzureLabs-Lab6-47.png)
    ![creare la classe VideoController](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="4c8bb-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="4c8bb-401">Capitolo 6: creare la classe sguardi</span><span class="sxs-lookup"><span data-stu-id="4c8bb-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="4c8bb-402">Questa classe è responsabile della creazione di un **Raycast** che verrà proiettato in futuro dalla **fotocamera principale**, per individuare l'oggetto analizzato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="4c8bb-403">In questo caso, **Raycast** dovrà identificare se l'utente sta esaminando l'oggetto **GazeButton** nella scena e attivare un comportamento.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="4c8bb-404">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-404">To create this Class:</span></span>

1.  <span data-ttu-id="4c8bb-405">Passare alla cartella **Scripts** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="4c8bb-406">Fare clic con il pulsante destro del mouse nel pannello del **progetto** , \**crea* \* C\# script \* \*.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="4c8bb-407">Denominare **lo script.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="4c8bb-408">Fare doppio clic ***sul nuovo script*** per aprirlo con **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="4c8bb-409">Verificare che lo spazio dei nomi seguente si trovi nella parte superiore dello script e rimuovere gli altri:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="4c8bb-410">Aggiungere quindi le variabili seguenti all'interno della classe **sguardi** :</span><span class="sxs-lookup"><span data-stu-id="4c8bb-410">Then add the following variables inside the **Gaze** class:</span></span>

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

6.  <span data-ttu-id="4c8bb-411">È ora necessario aggiungere il codice per i metodi **svegli ()** e **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="4c8bb-412">Aggiungere il codice seguente nel metodo **Update ()** per proiettare un Raycast e rilevare il raggiungimento della destinazione:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

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

8.  <span data-ttu-id="4c8bb-413">Salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="4c8bb-414">Fare clic e trascinare la classe **sguardi** dalla cartella Scripts all'oggetto principale della fotocamera nel pannello **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="4c8bb-415">Capitolo 7: configurare le due scene Unity</span><span class="sxs-lookup"><span data-stu-id="4c8bb-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="4c8bb-416">Lo scopo di questo capitolo è quello di configurare le due scene, ciascuna delle quali ospita un video da trasmettere.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="4c8bb-417">Si duplica la scena che è già stata creata, in modo che non sia necessario configurarla di nuovo, anche se si modifica la nuova scena, in modo che l'oggetto *GazeButton* si trovi in una posizione diversa e abbia un aspetto diverso.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="4c8bb-418">In questo modo viene illustrato come passare da una scena all'altra.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="4c8bb-419">A tale scopo, passare a **File > Salva scena con nome...** . Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="4c8bb-420">Fare clic sul pulsante **nuova cartella** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-420">Click the **New folder** button.</span></span>

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="4c8bb-422">Denominare la cartella **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="4c8bb-423">La finestra **Salva scena** sarà ancora aperta.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="4c8bb-424">Aprire la cartella **scene** appena create.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="4c8bb-425">Nel campo **nome file:** testo digitare **VideoScene1**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="4c8bb-426">Tornare in Unity, aprire la cartella **Scenes** e fare clic sul file **VideoScene1** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="4c8bb-427">Utilizzare la tastiera e premere **CTRL + D** per duplicare la scena</span><span class="sxs-lookup"><span data-stu-id="4c8bb-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="4c8bb-428">Il comando **duplicato** può essere eseguito anche passando a **Modifica > duplicato**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="4c8bb-429">Unity incrementerà automaticamente il numero di nomi di scena, ma ne verificherà comunque il numero per assicurarsi che corrisponda al codice inserito in precedenza.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="4c8bb-430">Sono presenti **VideoScene1** e **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="4c8bb-431">Con le due scene, passare a **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="4c8bb-432">Con la finestra **impostazioni di compilazione** aperta, trascinare le scene nella sezione **scene della compilazione** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="4c8bb-434">È possibile selezionare entrambe le scene dalla cartella **Scenes** tenendo premuto il pulsante **CTRL** , quindi fare clic su ciascuna scena e infine trascinare entrambe le scene.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="4c8bb-435">Chiudere la finestra **impostazioni di compilazione** e fare doppio clic su **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="4c8bb-436">Con la seconda scena aperta, fare clic sull'oggetto figlio **GazeButton** di **InsideOutSphere**e impostare la relativa trasformazione come segue:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="4c8bb-437">TRASFORMAZIONE-POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="4c8bb-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4c8bb-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-438">**X** 0</span></span>  |         <span data-ttu-id="4c8bb-439">**Y** 1,3</span><span class="sxs-lookup"><span data-stu-id="4c8bb-439">**Y** 1.3</span></span>         | <span data-ttu-id="4c8bb-440">**Z** 3,6</span><span class="sxs-lookup"><span data-stu-id="4c8bb-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="4c8bb-441">TRASFORMAZIONE-ROTAZIONE</span><span class="sxs-lookup"><span data-stu-id="4c8bb-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="4c8bb-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-442">**X** 0</span></span>  |          <span data-ttu-id="4c8bb-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-443">**Y** 0</span></span>          |  <span data-ttu-id="4c8bb-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="4c8bb-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="4c8bb-445">TRASFORMAZIONE-RIDIMENSIONA</span><span class="sxs-lookup"><span data-stu-id="4c8bb-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="4c8bb-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-446">**X** 1</span></span>   |          <span data-ttu-id="4c8bb-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-447">**Y** 1</span></span>          |  <span data-ttu-id="4c8bb-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="4c8bb-448">**Z** 1</span></span>  |

10. <span data-ttu-id="4c8bb-449">Con l'elemento figlio **GazeButton** ancora selezionato, esaminare il **controllo** e il **Filtro Mesh**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="4c8bb-450">Fare clic sulla piccola destinazione accanto al campo riferimento **mesh** :</span><span class="sxs-lookup"><span data-stu-id="4c8bb-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="4c8bb-452">Verrà visualizzata una finestra popup **Seleziona mesh** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="4c8bb-453">Fare doppio clic sulla mesh del **cubo** dall'elenco degli **Asset**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="4c8bb-455">Il **Filtro Mesh** verrà aggiornato ed è ora costituito da un **cubo**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="4c8bb-456">A questo punto, fare clic sull'icona a forma di **ingranaggio** accanto a **Sphere Collider** , quindi fare clic su **Rimuovi componente**per eliminare il Collider da questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="4c8bb-458">Con il **GazeButton** ancora selezionato, fare clic sul pulsante **Aggiungi componente** nella parte inferiore del **controllo**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="4c8bb-459">Nel campo di ricerca digitare **Box**e **Box Collider** sarà un'opzione: fare clic su di essa per aggiungere un **Collider di box** all'oggetto **GazeButton** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="4c8bb-461">Il **GazeButton** è stato aggiornato parzialmente, per un aspetto diverso, tuttavia, verrà creato un nuovo **materiale**, in modo che appaia completamente diverso ed è più facile da riconoscere come oggetto diverso rispetto all'oggetto nella prima scena.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="4c8bb-462">Passare alla cartella **Materials** , all'interno del **Pannello Project**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="4c8bb-463">Duplicare il materiale **ButtonMaterial** (premere **CTRL** + **D** sulla tastiera o fare clic con il pulsante destro del mouse sul **materiale**, quindi scegliere **duplicato**dall'opzione di menu **modifica** file).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="4c8bb-464">![capitolo 7--configurare le due scene Unity](images/AzureLabs-Lab6-55.png)
    ![capitolo 7--configurare le due scene Unity](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="4c8bb-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="4c8bb-465">Selezionare il nuovo materiale **ButtonMaterial** (qui denominato **ButtonMaterial 1**) e, all'interno del **controllo**, fare clic sulla finestra del colore **albedo** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="4c8bb-466">Verrà visualizzata una finestra popup in cui è possibile selezionare un altro colore (scegliere il tipo desiderato), quindi chiudere il popup.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="4c8bb-467">Il materiale sarà una propria istanza e diverso dall'originale.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-467">The Material will be its own instance, and different to the original.</span></span>

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="4c8bb-469">Trascinare il nuovo **materiale** nell'elemento figlio **GazeButton** , per aggiornare completamente l'aspetto, in modo che sia facilmente distinguibile dal pulsante First Scenes.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="4c8bb-471">A questo punto è possibile testare il progetto nell'editor prima di compilare il progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="4c8bb-472">Premere il pulsante **Riproduci** nell' **Editor** e utilizzare l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="4c8bb-474">Esaminare i due oggetti **GazeButton** per passare tra il primo e il secondo video.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="4c8bb-475">Capitolo 8: compilare la soluzione UWP</span><span class="sxs-lookup"><span data-stu-id="4c8bb-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="4c8bb-476">Dopo aver verificato che l'editor non abbia errori, è possibile procedere alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="4c8bb-477">Per compilare:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-477">To Build:</span></span>

1.  <span data-ttu-id="4c8bb-478">Salvare la scena corrente facendo clic su **File > Salva**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="4c8bb-479">Selezionare la casella denominata **Unity C\# Projects** (questo è importante perché consente di modificare le classi al termine della compilazione).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="4c8bb-480">Passare a **File > impostazioni di compilazione**, fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="4c8bb-481">Verrà richiesto di selezionare la cartella in cui si vuole buildthe la soluzione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="4c8bb-482">Creare una cartella **compilazioni** e all'interno di tale cartella creare un'altra cartella con un nome appropriato.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="4c8bb-483">Fare clic sulla nuova cartella e quindi fare clic su **Seleziona cartella**, quindi scegliere la cartella per iniziare la compilazione in quel percorso.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="4c8bb-484">![capitolo 8: compilare la soluzione UWP](images/AzureLabs-Lab6-60.png)
    ![capitolo 8: compilare la soluzione UWP](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="4c8bb-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="4c8bb-485">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nel percorso della compilazione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="4c8bb-486">Capitolo 9: eseguire la distribuzione nel computer locale</span><span class="sxs-lookup"><span data-stu-id="4c8bb-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="4c8bb-487">Una volta completata la compilazione, nella posizione della compilazione verrà visualizzata una finestra **Esplora file** .</span><span class="sxs-lookup"><span data-stu-id="4c8bb-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="4c8bb-488">Aprire la cartella denominata e compilata, quindi fare doppio clic sul file di soluzione (con estensione sln) all'interno della cartella per aprire la soluzione con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="4c8bb-489">L'unica cosa che rimane da fare è distribuire l'app nel computer (o nel computer *locale*).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="4c8bb-490">Per eseguire la distribuzione nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="4c8bb-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="4c8bb-491">In **Visual Studio 2017**aprire il file di soluzione appena creato.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="4c8bb-492">Nella **piattaforma soluzione**selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="4c8bb-493">Nella **configurazione della soluzione** selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Capitolo 9-distribuzione nel computer locale](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="4c8bb-495">A questo punto sarà necessario ripristinare tutti i pacchetti nella soluzione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="4c8bb-496">Fare clic con il pulsante destro del mouse sulla **soluzione**e scegliere **Ripristina pacchetti NuGet per la soluzione...**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="4c8bb-497">Questa operazione viene eseguita perché i pacchetti compilati da Unity devono essere destinati a funzionare con i riferimenti dei computer locali.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="4c8bb-498">Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="4c8bb-499">Visual Studio compilerà prima di tutto e distribuirà l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="4c8bb-500">L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Capitolo 9-distribuzione nel computer locale](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="4c8bb-502">Quando si esegue l'applicazione di realtà mista, si sarà all'interno del modello **InsideOutSphere** usato nell'app.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="4c8bb-503">Questa sfera è la posizione in cui verrà trasmesso il video, fornendo una visualizzazione di 360 gradi, del video in arrivo (filmato per questo tipo di prospettiva).</span><span class="sxs-lookup"><span data-stu-id="4c8bb-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="4c8bb-504">Non sorprendere se il video richiede un paio di secondi per il caricamento, l'app è soggetta alla velocità Internet disponibile, perché il video deve essere recuperato e quindi scaricato, quindi per eseguire lo streaming nell'app.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="4c8bb-505">Quando si è pronti, modificare le scene e aprire il secondo video, guardando la sfera rossa.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="4c8bb-506">Quindi, è possibile tornare indietro, usando il cubo blu nella seconda scena.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="4c8bb-507">Applicazione di servizi multimediali di Azure completata</span><span class="sxs-lookup"><span data-stu-id="4c8bb-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="4c8bb-508">Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio multimediale di Azure per lo streaming di video di 360.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![risultato Lab](images/AzureLabs-Lab6-00.png)

![risultato Lab](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="4c8bb-511">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="4c8bb-511">Bonus Exercises</span></span>

<span data-ttu-id="4c8bb-512">**Esercizio 1**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-512">**Exercise 1**</span></span>

<span data-ttu-id="4c8bb-513">Per modificare i video in questa esercitazione è possibile usare solo una singola scena.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="4c8bb-514">Prova la tua applicazione e creala in un'unica scena.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="4c8bb-515">Forse anche aggiungere un altro video alla combinazione.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="4c8bb-516">**Esercizio 2**</span><span class="sxs-lookup"><span data-stu-id="4c8bb-516">**Exercise 2**</span></span>

<span data-ttu-id="4c8bb-517">Sperimentare Azure e Unity e provare a implementare la possibilità per l'app di selezionare automaticamente un video con dimensioni di file diverse, a seconda del livello di attendibilità di una connessione Internet.</span><span class="sxs-lookup"><span data-stu-id="4c8bb-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


