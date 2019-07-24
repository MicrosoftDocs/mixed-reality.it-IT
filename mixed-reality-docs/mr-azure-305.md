---
title: MR e Azure 305-funzioni e archiviazione
description: Completare questo corso per apprendere come implementare archiviazione e funzioni di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, funzioni, archiviazione, hololens, immersiva, VR
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694553"
---
>[!NOTE]
><span data-ttu-id="aebbc-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="aebbc-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="aebbc-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="aebbc-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="aebbc-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="aebbc-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="aebbc-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="aebbc-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="aebbc-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="aebbc-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="aebbc-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="aebbc-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="aebbc-110">MR e Azure 305: Funzioni e archiviazione</span><span class="sxs-lookup"><span data-stu-id="aebbc-110">MR and Azure 305: Functions and storage</span></span>

![prodotto finale-inizio](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="aebbc-112">In questo corso si apprenderà come creare e usare funzioni di Azure e come archiviare i dati con una risorsa di archiviazione di Azure, all'interno di un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="aebbc-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="aebbc-113">*Funzioni di Azure* è un servizio Microsoft che consente agli sviluppatori di eseguire piccole porzioni di codice, "funzioni", in Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="aebbc-114">Questo consente di delegare il lavoro al cloud, anziché l'applicazione locale, che può avere molti vantaggi.</span><span class="sxs-lookup"><span data-stu-id="aebbc-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="aebbc-115">*Funzioni di Azure* supporta diversi linguaggi di sviluppo,\#tra cui\#C, F, node. js, Java e php.</span><span class="sxs-lookup"><span data-stu-id="aebbc-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="aebbc-116">Per altre informazioni, vedere l' [articolo funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="aebbc-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="aebbc-117">*Archiviazione di Azure* è un servizio cloud Microsoft che consente agli sviluppatori di archiviare i dati, con l'assicurazione che saranno a disponibilità elevata, protezione, durabilità, scalabilità e ridondanza.</span><span class="sxs-lookup"><span data-stu-id="aebbc-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="aebbc-118">Ciò significa che Microsoft gestirà tutta la manutenzione e i problemi critici.</span><span class="sxs-lookup"><span data-stu-id="aebbc-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="aebbc-119">Per altre informazioni, vedere l' [articolo archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="aebbc-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="aebbc-120">Dopo aver completato questo corso, si disporrà di un'applicazione con un auricolare immersiva a realtà mista che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="aebbc-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="aebbc-121">Consente all'utente di guardare una scena.</span><span class="sxs-lookup"><span data-stu-id="aebbc-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="aebbc-122">Attiva la generazione di oggetti quando l'utente guarda un "pulsante" 3D.</span><span class="sxs-lookup"><span data-stu-id="aebbc-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="aebbc-123">Gli oggetti generati verranno scelti da una funzione di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="aebbc-124">Quando viene generato ogni oggetto, l'applicazione archivia il tipo di oggetto in un *file di Azure*, che si trova in *archiviazione di Azure*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="aebbc-125">Al caricamento di una seconda volta, i dati dei *file di Azure* verranno recuperati e usati per riprodurre le azioni di generazione dall'istanza precedente dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="aebbc-126">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="aebbc-127">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="aebbc-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="aebbc-128">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="aebbc-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="aebbc-129">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="aebbc-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="aebbc-130">Corso</span><span class="sxs-lookup"><span data-stu-id="aebbc-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="aebbc-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="aebbc-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="aebbc-132"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="aebbc-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="aebbc-133">MR e Azure 305: Funzioni e archiviazione</span><span class="sxs-lookup"><span data-stu-id="aebbc-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="aebbc-134">✔️</span><span class="sxs-lookup"><span data-stu-id="aebbc-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="aebbc-135">✔️</span><span class="sxs-lookup"><span data-stu-id="aebbc-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="aebbc-136">Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aebbc-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="aebbc-137">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aebbc-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aebbc-138">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="aebbc-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="aebbc-139">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="aebbc-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="aebbc-140">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="aebbc-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="aebbc-141">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="aebbc-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="aebbc-142">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="aebbc-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="aebbc-143">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="aebbc-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="aebbc-144">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="aebbc-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="aebbc-145">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="aebbc-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="aebbc-146">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="aebbc-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="aebbc-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="aebbc-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="aebbc-148">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="aebbc-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="aebbc-149">Una sottoscrizione di un account Azure per la creazione di risorse di Azure</span><span class="sxs-lookup"><span data-stu-id="aebbc-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="aebbc-150">Accesso a Internet per l'installazione di Azure e il recupero dei dati</span><span class="sxs-lookup"><span data-stu-id="aebbc-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="aebbc-151">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="aebbc-151">Before you start</span></span>

<span data-ttu-id="aebbc-152">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="aebbc-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="aebbc-153">Capitolo 1-portale di Azure</span><span class="sxs-lookup"><span data-stu-id="aebbc-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="aebbc-154">Per usare il **servizio di archiviazione di Azure**, è necessario creare e configurare un **account di archiviazione** nell'portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="aebbc-155">Accedere al portale di [Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="aebbc-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="aebbc-156">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="aebbc-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="aebbc-157">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="aebbc-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="aebbc-158">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *account di archiviazione*e premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![ricerca di archiviazione di Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="aebbc-160">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="aebbc-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="aebbc-161">La nuova pagina fornirà una descrizione del servizio *account di archiviazione di Azure* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="aebbc-162">Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="aebbc-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Crea servizio](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="aebbc-164">Una volta fatto clic su **Crea**:</span><span class="sxs-lookup"><span data-stu-id="aebbc-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="aebbc-165">Inserire un *nome* per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.</span><span class="sxs-lookup"><span data-stu-id="aebbc-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="aebbc-166">Per *modello di distribuzione*selezionare **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="aebbc-167">Per *tipo di account*selezionare **archiviazione (utilizzo generico V1)** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="aebbc-168">Determinare il *percorso* del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="aebbc-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="aebbc-169">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="aebbc-170">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="aebbc-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="aebbc-171">Per la *replica* selezionare **l'archiviazione con ridondanza geografica e accesso in lettura (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="aebbc-172">Per *prestazioni*, selezionare **standard**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="aebbc-173">Lasciare il *trasferimento sicuro necessario* come **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="aebbc-174">Selezionare una *sottoscrizione*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="aebbc-175">Scegliere un *gruppo di risorse* o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="aebbc-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="aebbc-176">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="aebbc-177">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="aebbc-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="aebbc-178">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="aebbc-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="aebbc-179">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="aebbc-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="aebbc-180">Selezionare **Create**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-180">Select **Create**.</span></span>

        ![informazioni sul servizio di input](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="aebbc-182">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="aebbc-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="aebbc-183">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="aebbc-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nuova notifica nel portale di Azure](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="aebbc-185">Fare clic sulle notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="aebbc-185">Click on the notifications to explore your new Service instance.</span></span>

    ![Vai alla risorsa](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="aebbc-187">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="aebbc-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="aebbc-188">Si verrà portati alla nuova istanza del servizio dell' *account di archiviazione* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![chiavi di accesso](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="aebbc-190">Fare clic su *chiavi di accesso*per visualizzare gli endpoint per il servizio cloud.</span><span class="sxs-lookup"><span data-stu-id="aebbc-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="aebbc-191">Usare *blocco note* o simile per copiare una delle chiavi da usare in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="aebbc-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="aebbc-192">Prendere nota anche del valore della *stringa di connessione* , che verrà usato nella classe *Servizi* , che verrà creata in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="aebbc-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![copia stringa di connessione](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="aebbc-194">Capitolo 2-configurazione di una funzione di Azure</span><span class="sxs-lookup"><span data-stu-id="aebbc-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="aebbc-195">Verrà ora scritta una **funzione** di **Azure** nel servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="aebbc-196">È possibile usare una **funzione di Azure** per eseguire quasi tutte le operazioni eseguite con una funzione classica nel codice. la differenza è che questa funzione è accessibile da qualsiasi applicazione con credenziali per accedere all'account di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="aebbc-197">Per creare una funzione di Azure:</span><span class="sxs-lookup"><span data-stu-id="aebbc-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="aebbc-198">Dal *portale di Azure*fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *app per le funzioni*e premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Crea app per le funzioni](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="aebbc-200">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="aebbc-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="aebbc-201">La nuova pagina fornirà una descrizione del servizio *app per le funzioni di Azure* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="aebbc-202">Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="aebbc-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![informazioni sull'app per le funzioni](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="aebbc-204">Una volta fatto clic su **Crea**:</span><span class="sxs-lookup"><span data-stu-id="aebbc-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="aebbc-205">Specificare un *nome*per l'app.</span><span class="sxs-lookup"><span data-stu-id="aebbc-205">Provide an *App name*.</span></span> <span data-ttu-id="aebbc-206">Qui è possibile usare solo lettere e numeri (maiuscole o minuscole).</span><span class="sxs-lookup"><span data-stu-id="aebbc-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="aebbc-207">Selezionare la *sottoscrizione*preferita.</span><span class="sxs-lookup"><span data-stu-id="aebbc-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="aebbc-208">Scegliere un *gruppo di risorse* o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="aebbc-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="aebbc-209">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="aebbc-210">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="aebbc-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="aebbc-211">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="aebbc-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="aebbc-212">Per questo esercizio, selezionare *Windows* come **sistema operativo**scelto.</span><span class="sxs-lookup"><span data-stu-id="aebbc-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="aebbc-213">Selezionare il *piano a consumo* per il piano di **hosting**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="aebbc-214">Determinare il *percorso* del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="aebbc-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="aebbc-215">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="aebbc-216">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="aebbc-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="aebbc-217">Per prestazioni ottimali, selezionare la stessa area dell'account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="aebbc-218">Per *archiviazione*, selezionare **Usa esistente**e quindi usare il menu a discesa per individuare l'archiviazione creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="aebbc-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="aebbc-219">Uscire da *Application Insights* per questo esercizio.</span><span class="sxs-lookup"><span data-stu-id="aebbc-219">Leave *Application Insights* off for this exercise.</span></span>

        ![dettagli dell'app per le funzioni di input](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="aebbc-221">Fare clic sul pulsante **Crea**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="aebbc-222">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="aebbc-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="aebbc-223">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="aebbc-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notifica del nuovo portale di Azure](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="aebbc-225">Fare clic sulle notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="aebbc-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![passa all'app per le funzioni delle risorse](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="aebbc-227">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="aebbc-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="aebbc-228">Si verrà portati alla nuova istanza del servizio *app per le funzioni* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="aebbc-229">Nel dashboard *app per le funzioni* , posizionare il puntatore del mouse sulle *funzioni*, disponibili all'interno del pannello a sinistra, quindi fare clic sul simbolo **+ (segno più)** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![Crea nuova funzione](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="aebbc-231">Nella pagina successiva assicurarsi che webhook e l' **API** siano selezionati e per *scegliere una lingua* Selezionare **CSharp**, in quanto si tratta della lingua usata per questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="aebbc-232">Infine, fare clic sul pulsante **Crea funzione** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-232">Lastly, click the **Create this function** button.</span></span>

    ![Seleziona CSharp Web Hook](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="aebbc-234">È necessario passare alla tabella codici (Run. CSX), se non è possibile fare clic sulla funzione appena creata nell'elenco funzioni all'interno del pannello a sinistra.</span><span class="sxs-lookup"><span data-stu-id="aebbc-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![Apri nuova funzione](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="aebbc-236">Copiare il codice seguente nella funzione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-236">Copy the following code into your function.</span></span> <span data-ttu-id="aebbc-237">Questa funzione restituirà semplicemente un intero casuale compreso tra 0 e 2 quando viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="aebbc-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="aebbc-238">Non preoccuparti del codice esistente, è possibile incollarlo nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="aebbc-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="aebbc-239">Selezionare **Salva**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-239">Select **Save**.</span></span>

14. <span data-ttu-id="aebbc-240">Il risultato dovrebbe essere simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="aebbc-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="aebbc-241">Fare clic su **Ottieni URL funzione** e prendere nota dell' *endpoint* visualizzato.</span><span class="sxs-lookup"><span data-stu-id="aebbc-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="aebbc-242">Sarà necessario inserirlo nella classe *Servizi* che verrà creata più avanti in questo corso.</span><span class="sxs-lookup"><span data-stu-id="aebbc-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![Ottieni endpoint funzione](images/AzureLabs-Lab5-16.png)

    ![Ottieni endpoint funzione](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="aebbc-245">Capitolo 3-configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="aebbc-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="aebbc-246">Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="aebbc-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="aebbc-247">Configurare e testare l'auricolare immersiva della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="aebbc-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="aebbc-248">**Non** sarà necessario alcun controller di movimento per questo corso.</span><span class="sxs-lookup"><span data-stu-id="aebbc-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="aebbc-249">Se è necessario supporto per la configurazione dell'auricolare immersivo, [vedere l'articolo relativo alla configurazione della realtà mista](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="aebbc-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="aebbc-250">Aprire Unity e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-250">Open Unity and click **New**.</span></span>

    ![Crea nuovo progetto Unity](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="aebbc-252">A questo punto sarà necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="aebbc-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="aebbc-253">Inserire **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="aebbc-254">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="aebbc-255">Impostare il *percorso* su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="aebbc-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="aebbc-256">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-256">Then, click **Create project**.</span></span>

    ![assegnare un nome al nuovo progetto Unity](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="aebbc-258">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="aebbc-259">Passare a **modifica** > **Preferenze** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="aebbc-260">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="aebbc-261">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-261">Close the **Preferences** window.</span></span>

    ![imposta Visual Studio come editor di script](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="aebbc-263">Passare quindi a**impostazioni di compilazione** **file** > e passare alla piattaforma **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![passa alla piattaforma UWP](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="aebbc-265">Passare a**impostazioni di compilazione** **file** > e verificare che:</span><span class="sxs-lookup"><span data-stu-id="aebbc-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="aebbc-266">Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="aebbc-267">Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="aebbc-268">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="aebbc-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="aebbc-269">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="aebbc-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="aebbc-270">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="aebbc-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="aebbc-271">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="aebbc-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="aebbc-272">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="aebbc-273">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="aebbc-274">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="aebbc-274">A save window will appear.</span></span>

            ![Aggiungi scene aperte](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="aebbc-276">Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.</span><span class="sxs-lookup"><span data-stu-id="aebbc-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![cartella crea scene](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="aebbc-278">Aprire la cartella **Scenes** appena creata e quindi nel campo **nome file:** testo digitare **FunctionsScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![scena Salva funzioni](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="aebbc-280">Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="aebbc-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![scena Salva funzioni](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="aebbc-282">Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![impostazioni del lettore in Inspector](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="aebbc-284">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="aebbc-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="aebbc-285">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="aebbc-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="aebbc-286">La **versione di runtime** di scripting deve essere **sperimentale** (equivalente a .NET 4,6), che attiverà la necessità di riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="aebbc-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="aebbc-287">Il **back-end** di scripting deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="aebbc-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="aebbc-288">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="aebbc-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="aebbc-289">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="aebbc-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="aebbc-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="aebbc-290">**InternetClient**</span></span>

            ![impostare le funzionalità](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="aebbc-292">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![impostare le impostazioni di XR](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="aebbc-294">Nelle *impostazioni di compilazione* *i C# progetti Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="aebbc-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![Seleziona progetti c#](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="aebbc-296">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="aebbc-297">Salva la scena e il progetto **(**  > **progetto**Salva**scena/Salva file** > ).</span><span class="sxs-lookup"><span data-stu-id="aebbc-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="aebbc-298">Capitolo 4-installazione della fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="aebbc-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aebbc-299">Se si vuole ignorare i componenti di *configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile [scaricare questo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo nel progetto come [pacchetto personalizzato](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="aebbc-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="aebbc-300">Questo conterrà anche le dll del capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="aebbc-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="aebbc-301">Dopo l'importazione, continuare con il [capitolo 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="aebbc-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="aebbc-302">Nel *Pannello gerarchia*è presente un oggetto denominato **Main camera**, che rappresenta il punto di visualizzazione "Head" dopo che l'applicazione è stata "interna".</span><span class="sxs-lookup"><span data-stu-id="aebbc-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="aebbc-303">Con il dashboard Unity in primo piano, selezionare la **fotocamera principale GameObject**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="aebbc-304">Si noterà che il *pannello Inspector* , disponibile in genere a destra, all'interno del dashboard, visualizzerà i vari componenti di tale *GameObject*, con la *trasformazione* nella parte superiore, seguita dalla *fotocamera*e da altri componenti.</span><span class="sxs-lookup"><span data-stu-id="aebbc-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="aebbc-305">Sarà necessario reimpostare la trasformazione della fotocamera principale, in modo che venga posizionata correttamente.</span><span class="sxs-lookup"><span data-stu-id="aebbc-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="aebbc-306">A tale scopo, selezionare l'  icona dell'ingranaggio accanto al componente *trasformazione* della fotocamera e selezionare **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![Reimposta trasformazione](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="aebbc-308">Aggiornare quindi il componente **Transform** in modo simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="aebbc-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="aebbc-309">TRASFORMAZIONE-POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="aebbc-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="aebbc-310">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-310">**X**</span></span>   | <span data-ttu-id="aebbc-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-311">**Y**</span></span>                     | <span data-ttu-id="aebbc-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-312">**Z**</span></span> |
    | <span data-ttu-id="aebbc-313">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-313">0</span></span>       | <span data-ttu-id="aebbc-314">1</span><span class="sxs-lookup"><span data-stu-id="aebbc-314">1</span></span>                         | <span data-ttu-id="aebbc-315">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-315">0</span></span>     |    

    |       | <span data-ttu-id="aebbc-316">TRASFORMAZIONE-ROTAZIONE</span><span class="sxs-lookup"><span data-stu-id="aebbc-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="aebbc-317">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-317">**X**</span></span> | <span data-ttu-id="aebbc-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-318">**Y**</span></span>                | <span data-ttu-id="aebbc-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-319">**Z**</span></span> |
    | <span data-ttu-id="aebbc-320">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-320">0</span></span>     | <span data-ttu-id="aebbc-321">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-321">0</span></span>                    | <span data-ttu-id="aebbc-322">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-322">0</span></span>     |

    |       | <span data-ttu-id="aebbc-323">TRASFORMAZIONE-RIDIMENSIONA</span><span class="sxs-lookup"><span data-stu-id="aebbc-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="aebbc-324">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-324">**X**</span></span> | <span data-ttu-id="aebbc-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-325">**Y**</span></span>             | <span data-ttu-id="aebbc-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-326">**Z**</span></span> |
    | <span data-ttu-id="aebbc-327">1</span><span class="sxs-lookup"><span data-stu-id="aebbc-327">1</span></span>     | <span data-ttu-id="aebbc-328">1</span><span class="sxs-lookup"><span data-stu-id="aebbc-328">1</span></span>                 | <span data-ttu-id="aebbc-329">1</span><span class="sxs-lookup"><span data-stu-id="aebbc-329">1</span></span>     |

    ![imposta trasformazione fotocamera](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="aebbc-331">Capitolo 5-configurazione della scena Unity</span><span class="sxs-lookup"><span data-stu-id="aebbc-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="aebbc-332">Fare clic con il pulsante destro del mouse in un'area vuota del *Pannello gerarchia*, sotto **oggetto 3D**, Aggiungi un **piano**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![Crea nuovo piano](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="aebbc-334">Con l'oggetto **piano** selezionato, modificare i parametri seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="aebbc-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="aebbc-335">TRASFORMAZIONE-POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="aebbc-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="aebbc-336">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-336">**X**</span></span> | <span data-ttu-id="aebbc-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-337">**Y**</span></span>                | <span data-ttu-id="aebbc-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-338">**Z**</span></span> |
    | <span data-ttu-id="aebbc-339">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-339">0</span></span>     | <span data-ttu-id="aebbc-340">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-340">0</span></span>                    | <span data-ttu-id="aebbc-341">4</span><span class="sxs-lookup"><span data-stu-id="aebbc-341">4</span></span>     |

    |       | <span data-ttu-id="aebbc-342">TRASFORMAZIONE-RIDIMENSIONA</span><span class="sxs-lookup"><span data-stu-id="aebbc-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="aebbc-343">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-343">**X**</span></span> | <span data-ttu-id="aebbc-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-344">**Y**</span></span>             | <span data-ttu-id="aebbc-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-345">**Z**</span></span> |
    | <span data-ttu-id="aebbc-346">10</span><span class="sxs-lookup"><span data-stu-id="aebbc-346">10</span></span>    | <span data-ttu-id="aebbc-347">1</span><span class="sxs-lookup"><span data-stu-id="aebbc-347">1</span></span>                 | <span data-ttu-id="aebbc-348">10</span><span class="sxs-lookup"><span data-stu-id="aebbc-348">10</span></span>    |

    ![Imposta posizione e scala del piano](images/AzureLabs-Lab5-32.png)

    ![visualizzazione scena del piano](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="aebbc-351">Fare clic con il pulsante destro del mouse in un'area vuota del *Pannello gerarchia*, sotto **oggetto 3D**, Aggiungi un **cubo**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="aebbc-352">Rinominare il cubo in **GazeButton** (con il cubo selezionato, premere ' F2').</span><span class="sxs-lookup"><span data-stu-id="aebbc-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="aebbc-353">Modificare i parametri seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="aebbc-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="aebbc-354">TRASFORMAZIONE-POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="aebbc-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="aebbc-355">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-355">**X**</span></span> | <span data-ttu-id="aebbc-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-356">**Y**</span></span>                | <span data-ttu-id="aebbc-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-357">**Z**</span></span> |
        | <span data-ttu-id="aebbc-358">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-358">0</span></span>     | <span data-ttu-id="aebbc-359">3</span><span class="sxs-lookup"><span data-stu-id="aebbc-359">3</span></span>                    | <span data-ttu-id="aebbc-360">5</span><span class="sxs-lookup"><span data-stu-id="aebbc-360">5</span></span>     |


        ![imposta la trasformazione del pulsante di sguardo](images/AzureLabs-Lab5-34.png)

        ![visualizzazione della scena del pulsante Guarda](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="aebbc-363">Fare clic sul pulsante a discesa **tag** e fare clic su **Aggiungi tag** per aprire il *riquadro Tag & livelli*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Aggiungi nuovo tag](images/AzureLabs-Lab5-36.png)

        ![Seleziona più](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="aebbc-366">Selezionare il pulsante **+ (segno più)** e nel campo *nuovo nome tag* immettere **GazeButton**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![nome nuovo tag](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="aebbc-368">Fare clic sull'oggetto **GazeButton** nel *Pannello gerarchia*e nel *pannello Inspector*assegnare il tag **GazeButton** appena creato.</span><span class="sxs-lookup"><span data-stu-id="aebbc-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![pulsante assegna sguardo al nuovo tag](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="aebbc-370">Fare clic con il pulsante destro del mouse sull'oggetto **GazeButton** , nel *Pannello gerarchia*e aggiungere un **GameObject vuoto** (che verrà aggiunto come oggetto *figlio* ).</span><span class="sxs-lookup"><span data-stu-id="aebbc-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="aebbc-371">Selezionare il nuovo oggetto e rinominarlo **ShapeSpawnPoint**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="aebbc-372">Modificare i parametri seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="aebbc-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="aebbc-373">TRASFORMAZIONE-POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="aebbc-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="aebbc-374">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-374">**X**</span></span> |<span data-ttu-id="aebbc-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-375">**Y**</span></span>                 | <span data-ttu-id="aebbc-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-376">**Z**</span></span> |
        | <span data-ttu-id="aebbc-377">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-377">0</span></span>     | <span data-ttu-id="aebbc-378">-1</span><span class="sxs-lookup"><span data-stu-id="aebbc-378">-1</span></span>                   | <span data-ttu-id="aebbc-379">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-379">0</span></span>     |

        ![Aggiorna trasformazione punto di generazione forma](images/AzureLabs-Lab5-40.png)

        ![visualizzazione scena punto di generazione forma](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="aebbc-382">Successivamente verrà creato un oggetto **testo 3D** per fornire commenti e suggerimenti sullo stato del servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="aebbc-383">Fare di nuovo clic con il pulsante destro del mouse su **GazeButton** nel pannello gerarchia e aggiungere un oggetto **3D oggetto** > **testo 3D** come *elemento figlio*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![Crea nuovo oggetto testo 3D](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="aebbc-385">Rinominare l'oggetto **testo 3D** in **AzureStatusText**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="aebbc-386">Modificare la trasformazione dell'oggetto **AzureStatusText** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="aebbc-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="aebbc-387">TRASFORMAZIONE-POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="aebbc-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="aebbc-388">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-388">**X**</span></span> | <span data-ttu-id="aebbc-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-389">**Y**</span></span>                | <span data-ttu-id="aebbc-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-390">**Z**</span></span> |
    | <span data-ttu-id="aebbc-391">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-391">0</span></span>     | <span data-ttu-id="aebbc-392">0</span><span class="sxs-lookup"><span data-stu-id="aebbc-392">0</span></span>                    | <span data-ttu-id="aebbc-393">-0,6</span><span class="sxs-lookup"><span data-stu-id="aebbc-393">-0.6</span></span>  |

    |       | <span data-ttu-id="aebbc-394">TRASFORMAZIONE-RIDIMENSIONA</span><span class="sxs-lookup"><span data-stu-id="aebbc-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="aebbc-395">**X**</span><span class="sxs-lookup"><span data-stu-id="aebbc-395">**X**</span></span> | <span data-ttu-id="aebbc-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="aebbc-396">**Y**</span></span>             | <span data-ttu-id="aebbc-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="aebbc-397">**Z**</span></span> |
    | <span data-ttu-id="aebbc-398">0,1</span><span class="sxs-lookup"><span data-stu-id="aebbc-398">0.1</span></span>   | <span data-ttu-id="aebbc-399">0,1</span><span class="sxs-lookup"><span data-stu-id="aebbc-399">0.1</span></span>               | <span data-ttu-id="aebbc-400">0,1</span><span class="sxs-lookup"><span data-stu-id="aebbc-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="aebbc-401">Non preoccuparti se sembra essere fuori sede, perché verrà corretto quando il componente mesh del testo seguente viene aggiornato.</span><span class="sxs-lookup"><span data-stu-id="aebbc-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="aebbc-402">Modificare il componente **mesh di testo** in modo che corrisponda a quanto segue:</span><span class="sxs-lookup"><span data-stu-id="aebbc-402">Change the **Text Mesh** component to match the below:</span></span>

    ![imposta componente mesh testo](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="aebbc-404">Il colore selezionato è il colore esadecimale: **000000FF**, sebbene sia possibile sceglierne una propria, è sufficiente assicurarsi che sia leggibile.</span><span class="sxs-lookup"><span data-stu-id="aebbc-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="aebbc-405">La struttura del pannello della gerarchia dovrebbe ora essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="aebbc-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![mesh di testo in visualizzazione scena](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="aebbc-407">La scena dovrebbe ora essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="aebbc-407">Your scene should now look like this:</span></span>

    ![mesh di testo in visualizzazione scena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="aebbc-409">Capitolo 6: importare archiviazione di Azure per Unity</span><span class="sxs-lookup"><span data-stu-id="aebbc-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="aebbc-410">Si utilizzerà archiviazione di Azure per Unity (che a sua volta USA .NET SDK per Azure).</span><span class="sxs-lookup"><span data-stu-id="aebbc-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="aebbc-411">Per altre informazioni, vedere l' [articolo archiviazione di Azure per Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="aebbc-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="aebbc-412">Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="aebbc-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="aebbc-413">Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.</span><span class="sxs-lookup"><span data-stu-id="aebbc-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="aebbc-414">Per importare l'SDK nel progetto, assicurarsi di aver scaricato la versione più recente [di ". file unitypackage Tools" da GitHub](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="aebbc-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="aebbc-415">Eseguire quindi le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="aebbc-415">Then, do the following:</span></span>

1.  <span data-ttu-id="aebbc-416">Aggiungere il file con **estensione file unitypackage Tools** a Unity usando l'opzione di menu **Asset** > **Import Package** > **Custom Package** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="aebbc-417">Nella casella **Importa pacchetto Unity** visualizzata è possibile selezionare tutti gli elementi in**archiviazione** **plug** > -in.</span><span class="sxs-lookup"><span data-stu-id="aebbc-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="aebbc-418">Deselezionare tutti gli altri elementi, perché non sono necessari per questo corso.</span><span class="sxs-lookup"><span data-stu-id="aebbc-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Importa nel pacchetto](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="aebbc-420">Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="aebbc-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="aebbc-421">Passare alla cartella *archiviazione* in *plug*-in, nella visualizzazione del progetto e selezionare *solo*i plug-in seguenti:</span><span class="sxs-lookup"><span data-stu-id="aebbc-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="aebbc-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="aebbc-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="aebbc-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="aebbc-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="aebbc-424">Microsoft. WindowsAzure. storage</span><span class="sxs-lookup"><span data-stu-id="aebbc-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="aebbc-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="aebbc-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="aebbc-426">System. Spatial</span><span class="sxs-lookup"><span data-stu-id="aebbc-426">System.Spatial</span></span>

        ![deseleziona qualsiasi piattaforma](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="aebbc-428">Con *questi plug* -in specifici selezionati, **deselezionare** *qualsiasi piattaforma* e **deselezionare** *WSAPlayer* , quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![applica dll della piattaforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="aebbc-430">Questi specifici plug-in vengono contrassegnati per essere usati solo nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="aebbc-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="aebbc-431">Questo è dovuto al fatto che esistono versioni diverse degli stessi plug-in nella cartella WSA che verranno usate dopo l'esportazione del progetto da Unity.</span><span class="sxs-lookup"><span data-stu-id="aebbc-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="aebbc-432">Nella cartella plugin di *archiviazione* selezionare solo:</span><span class="sxs-lookup"><span data-stu-id="aebbc-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="aebbc-433">Microsoft. Data. Services. client</span><span class="sxs-lookup"><span data-stu-id="aebbc-433">Microsoft.Data.Services.Client</span></span>

        ![impostazione non elabora per le dll](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="aebbc-435">Selezionare la casella **non elaborare** in *Impostazioni piattaforma* e fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="aebbc-437">Si sta contrassegnando questo plug-in "non elaborare" perché il plug-in assembly Unity ha difficoltà nell'elaborare questo plug-in.</span><span class="sxs-lookup"><span data-stu-id="aebbc-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="aebbc-438">Il plug-in continuerà a funzionare anche se non viene elaborato.</span><span class="sxs-lookup"><span data-stu-id="aebbc-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="aebbc-439">Capitolo 7: creare la classe servizi</span><span class="sxs-lookup"><span data-stu-id="aebbc-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="aebbc-440">La prima classe che si intende creare è la classe *Servizi* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="aebbc-441">La classe *Servizi* sarà responsabile di:</span><span class="sxs-lookup"><span data-stu-id="aebbc-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="aebbc-442">Archiviazione delle credenziali dell'account Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="aebbc-443">Chiamata della funzione app Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="aebbc-444">Caricare e scaricare il file di dati nella risorsa di archiviazione cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="aebbc-445">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="aebbc-445">To create this Class:</span></span>

1.  <span data-ttu-id="aebbc-446">Fare clic con il pulsante destro del mouse nella cartella *Asset* , che si trova nel pannello progetto, **Crea** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="aebbc-447">Denominare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="aebbc-447">Name the folder **Scripts**.</span></span>

    ![Crea nuova cartella](images/AzureLabs-Lab5-50.png)

    ![cartella di chiamata-script](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="aebbc-450">Fare doppio clic sulla cartella appena creata per aprirla.</span><span class="sxs-lookup"><span data-stu-id="aebbc-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="aebbc-451">Fare clic con il pulsante destro del mouse all'interno della cartella **Crea**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="aebbc-452">Chiamare lo script *Servizi*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="aebbc-453">Fare doppio clic sulla nuova classe *Servizi* per aprirla con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="aebbc-454">Aggiungere gli spazi dei nomi seguenti all'inizio di *Servizi*:</span><span class="sxs-lookup"><span data-stu-id="aebbc-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="aebbc-455">Aggiungere i campi Inspector seguenti all'interno della classe *Servizi* :</span><span class="sxs-lookup"><span data-stu-id="aebbc-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="aebbc-456">Aggiungere quindi le variabili membro seguenti all'interno della classe *Servizi* :</span><span class="sxs-lookup"><span data-stu-id="aebbc-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="aebbc-457">Assicurarsi di sostituire i valori della *stringa di connessione* e dell' *endpoint* con i valori di archiviazione di Azure, disponibili nel portale di Azure</span><span class="sxs-lookup"><span data-stu-id="aebbc-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="aebbc-458">È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="aebbc-459">Questi metodi verranno chiamati quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="aebbc-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="aebbc-460">Il codice per *CallAzureFunctionForNextShape ()* viene compilato in un [capitolo futuro](#chapter-10---completing-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="aebbc-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="aebbc-461">Eliminare il metodo *Update ()* perché non verrà utilizzato da questa classe.</span><span class="sxs-lookup"><span data-stu-id="aebbc-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="aebbc-462">Salvare le modifiche in Visual Studio e quindi tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="aebbc-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="aebbc-463">Fare clic e trascinare la classe *Servizi* dalla cartella Scripts all'oggetto principale della fotocamera nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="aebbc-464">Selezionare la fotocamera principale, quindi estrarre l'oggetto figlio **AzureStatusText** dall'oggetto **GazeButton** e inserirlo nel campo destinazione riferimento **AzureStatusText** , nel *controllo*, per fornire il riferimento al  *Script Servizi* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![assegnare la destinazione di riferimento del testo di stato di Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="aebbc-466">Capitolo 8: creare la classe ShapeFactory</span><span class="sxs-lookup"><span data-stu-id="aebbc-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="aebbc-467">Lo script successivo da creare è la classe *ShapeFactory* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="aebbc-468">Il ruolo di questa classe è creare una nuova forma, quando richiesto, e conservarne una cronologia delle forme create in un *elenco della cronologia delle forme*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="aebbc-469">Ogni volta che viene creata una forma, l' *elenco della cronologia delle forme* viene aggiornato nella classe *AzureService* e quindi archiviato in *archiviazione di Azure*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="aebbc-470">All'avvio dell'applicazione, se viene trovato un file archiviato in *archiviazione di Azure*, l' *elenco della cronologia delle forme* viene recuperato e riprodotto, con l'oggetto **testo 3D** che indica se la forma generata è di archiviazione o una nuova.</span><span class="sxs-lookup"><span data-stu-id="aebbc-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="aebbc-471">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="aebbc-471">To create this class:</span></span>

1.  <span data-ttu-id="aebbc-472">Passare alla cartella **Scripts** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="aebbc-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="aebbc-473">Fare clic con il pulsante destro del mouse all'interno della cartella **Crea**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="aebbc-474">Chiamare lo script *ShapeFactory*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="aebbc-475">Fare doppio clic sul nuovo script *ShapeFactory* per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="aebbc-476">Verificare che la classe *ShapeFactory* includa gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="aebbc-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="aebbc-477">Aggiungere le variabili illustrate di seguito alla classe *ShapeFactory* e sostituire le funzioni *Start ()* e *svegli ()* con quelle riportate di seguito:</span><span class="sxs-lookup"><span data-stu-id="aebbc-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="aebbc-478">Il metodo *createShape ()* genera le forme primitive, in base al parametro *Integer* fornito.</span><span class="sxs-lookup"><span data-stu-id="aebbc-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="aebbc-479">Il parametro booleano viene usato per specificare se la forma attualmente creata è di archiviazione o nuova.</span><span class="sxs-lookup"><span data-stu-id="aebbc-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="aebbc-480">Inserire il codice seguente nella classe *ShapeFactory* , sotto i metodi precedenti:</span><span class="sxs-lookup"><span data-stu-id="aebbc-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="aebbc-481">Assicurarsi di salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="aebbc-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="aebbc-482">Nell'editor di Unity fare clic e trascinare la classe *ShapeFactory* dalla cartella **Scripts** all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="aebbc-483">Con la fotocamera principale selezionata, si noterà che nel componente di script *ShapeFactory* manca il riferimento al *punto di generazione* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="aebbc-484">Per risolvere il problema, trascinare l'oggetto **ShapeSpawnPoint** dal *Pannello gerarchia* alla destinazione di riferimento del **punto di generazione** .</span><span class="sxs-lookup"><span data-stu-id="aebbc-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![imposta la destinazione del riferimento alla Factory della forma](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="aebbc-486">Capitolo 9: creare la classe sguardi</span><span class="sxs-lookup"><span data-stu-id="aebbc-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="aebbc-487">L'ultimo script che è necessario creare è la classe *sguardi* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="aebbc-488">Questa classe è responsabile della creazione di un **Raycast** che verrà proiettato in futuro dalla fotocamera principale, per individuare l'oggetto analizzato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="aebbc-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="aebbc-489">In questo caso, Raycast dovrà identificare se l'utente sta esaminando l'oggetto **GazeButton** nella scena e attivare un comportamento.</span><span class="sxs-lookup"><span data-stu-id="aebbc-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="aebbc-490">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="aebbc-490">To create this Class:</span></span>

1.  <span data-ttu-id="aebbc-491">Passare alla cartella **Scripts** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="aebbc-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="aebbc-492">Fare clic con il pulsante destro del mouse sul pannello del progetto, quindi scegliere **Crea**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="aebbc-493">Chiamare lo *sguardo*dello script.</span><span class="sxs-lookup"><span data-stu-id="aebbc-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="aebbc-494">Fare doppio clic *sul nuovo script* per aprirlo con *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="aebbc-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="aebbc-495">Verificare che nella parte superiore dello script sia incluso lo spazio dei nomi seguente:</span><span class="sxs-lookup"><span data-stu-id="aebbc-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="aebbc-496">Aggiungere quindi le variabili seguenti all'interno della classe *sguardi* :</span><span class="sxs-lookup"><span data-stu-id="aebbc-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="aebbc-497">Alcune di queste variabili possono essere modificate nell' *Editor*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="aebbc-498">È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="aebbc-499">Aggiungere il codice seguente, in cui verrà creato un oggetto cursore all'inizio, insieme al metodo *Update ()* , che eseguirà il metodo Raycast, insieme alla posizione in cui viene attivato il valore booleano GazeEnabled:</span><span class="sxs-lookup"><span data-stu-id="aebbc-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="aebbc-500">Aggiungere quindi il metodo *UpdateRaycast ()* che proietta un Raycast e rileva la destinazione dell'hit.</span><span class="sxs-lookup"><span data-stu-id="aebbc-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="aebbc-501">Infine, aggiungere il metodo *ResetFocusedObject ()* , che consente di impostare il colore corrente per gli oggetti GazeButton, che indica se sta creando una nuova forma.</span><span class="sxs-lookup"><span data-stu-id="aebbc-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="aebbc-502">Salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="aebbc-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="aebbc-503">Fare clic e trascinare la classe *sguardi* dalla cartella Scripts all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="aebbc-504">Capitolo 10-completamento della classe servizi</span><span class="sxs-lookup"><span data-stu-id="aebbc-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="aebbc-505">Con gli altri script sul posto, è ora possibile *completare* la classe *Servizi* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="aebbc-506">Questa operazione verrà eseguita tramite:</span><span class="sxs-lookup"><span data-stu-id="aebbc-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="aebbc-507">Aggiunta di un nuovo metodo denominato *CreateCloudIdentityAsync ()* per configurare le variabili di autenticazione necessarie per la comunicazione con Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="aebbc-508">Questo metodo verificherà anche l'esistenza di un file archiviato in precedenza contenente l'elenco di forme.</span><span class="sxs-lookup"><span data-stu-id="aebbc-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="aebbc-509">**Se il file viene trovato**, lo *sguardo*dell'utente viene disabilitato e viene attivata la creazione della forma, in base al modello di forme, come archiviato nel **file di archiviazione di Azure**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="aebbc-510">L'utente può visualizzarlo, perché la **mesh di testo** fornirà la visualizzazione ' storage ' o ' New ', a seconda delle forme Origin.</span><span class="sxs-lookup"><span data-stu-id="aebbc-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="aebbc-511">**Se non viene trovato alcun file**, verrà abilitato lo *sguardo*, consentendo all'utente di creare forme quando si esamina l'oggetto **GazeButton** nella scena.</span><span class="sxs-lookup"><span data-stu-id="aebbc-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="aebbc-512">Il frammento di codice successivo si trova all'interno del metodo *Start ()* ; dove verrà effettuata una chiamata al metodo *CreateCloudIdentityAsync ()* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="aebbc-513">È possibile copiare il metodo *Start ()* corrente con il seguente:</span><span class="sxs-lookup"><span data-stu-id="aebbc-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="aebbc-514">Compilare il codice per il metodo *CallAzureFunctionForNextShape ()* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="aebbc-515">Si userà la *app per le funzioni di Azure* creata in precedenza per richiedere un indice delle forme.</span><span class="sxs-lookup"><span data-stu-id="aebbc-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="aebbc-516">Una volta ricevuta la nuova forma, questo metodo invierà la forma alla classe *ShapeFactory* per creare la nuova forma nella scena.</span><span class="sxs-lookup"><span data-stu-id="aebbc-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="aebbc-517">Usare il codice seguente per completare il corpo di *CallAzureFunctionForNextShape ()* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="aebbc-518">Aggiungere un metodo per creare una stringa concatenando gli Integer archiviati nell'elenco della cronologia delle forme e salvarli nel *file di archiviazione di Azure*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="aebbc-519">Aggiungere un metodo per recuperare il testo archiviato nel file che si trova nel *file di archiviazione di Azure* e deserializzarlo in un elenco.</span><span class="sxs-lookup"><span data-stu-id="aebbc-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="aebbc-520">Una volta completato il processo, il metodo abilita nuovamente lo sguardo in modo che l'utente possa aggiungere altre forme alla scena.</span><span class="sxs-lookup"><span data-stu-id="aebbc-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="aebbc-521">Salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="aebbc-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="aebbc-522">Capitolo 11: compilare la soluzione UWP</span><span class="sxs-lookup"><span data-stu-id="aebbc-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="aebbc-523">Per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="aebbc-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="aebbc-524">Passare a **file** > **impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-524">Go to **File** > **Build Settings**.</span></span>

    ![compilare l'app](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="aebbc-526">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-526">Click **Build**.</span></span> <span data-ttu-id="aebbc-527">Unity avvierà una finestra di *Esplora file* , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="aebbc-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="aebbc-528">Creare la cartella adesso e denominarla *app*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="aebbc-529">Quindi, con la cartella dell' *app* selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="aebbc-530">Unity inizierà a compilare il progetto nella cartella dell' *app* .</span><span class="sxs-lookup"><span data-stu-id="aebbc-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="aebbc-531">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra *Esplora file* nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).</span><span class="sxs-lookup"><span data-stu-id="aebbc-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="aebbc-532">Capitolo 12-distribuzione dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="aebbc-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="aebbc-533">Per distribuire l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="aebbc-533">To deploy your application:</span></span>

1.  <span data-ttu-id="aebbc-534">Passare alla cartella dell' *app* creata nell' [ultimo capitolo](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="aebbc-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="aebbc-535">Verrà visualizzato un file con il nome delle app, con l'estensione ' sln ', che è necessario fare doppio clic, per aprirlo in *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="aebbc-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="aebbc-536">Nella **piattaforma soluzione**selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="aebbc-537">Nella **configurazione della soluzione** selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="aebbc-538">Per Microsoft HoloLens, può risultare più semplice impostare questa impostazione su *computer remoto*, in modo da non essere collegati al computer.</span><span class="sxs-lookup"><span data-stu-id="aebbc-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="aebbc-539">Tuttavia, sarà necessario eseguire anche le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="aebbc-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="aebbc-540">Individuare l' **indirizzo IP** della HoloLens, che si trova all'interno della rete **Impostazioni** >  **&**  > **Opzioni avanzate** **Wi-Fi** > . l'indirizzo IPv4 è quello da usare.</span><span class="sxs-lookup"><span data-stu-id="aebbc-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="aebbc-541">Verificare che la **modalità sviluppatore** sia **attiva**; disponibile in **Impostazioni** > **aggiornare & sicurezza** > **per gli sviluppatori**.</span><span class="sxs-lookup"><span data-stu-id="aebbc-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![Distribuisci soluzione](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="aebbc-543">Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.</span><span class="sxs-lookup"><span data-stu-id="aebbc-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="aebbc-544">L'app verrà visualizzata nell'elenco delle app installate, pronta per essere avviata e testata.</span><span class="sxs-lookup"><span data-stu-id="aebbc-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="aebbc-545">Le funzioni di Azure e l'applicazione di archiviazione completate</span><span class="sxs-lookup"><span data-stu-id="aebbc-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="aebbc-546">Congratulazioni, è stata creata un'app per realtà mista che sfrutta sia le funzioni di Azure che i servizi di archiviazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="aebbc-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="aebbc-547">L'app sarà in grado di creare dati archiviati e fornirà un'azione in base a tali dati.</span><span class="sxs-lookup"><span data-stu-id="aebbc-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![fine prodotto finale](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="aebbc-549">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="aebbc-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="aebbc-550">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="aebbc-550">Exercise 1</span></span>

<span data-ttu-id="aebbc-551">Creare un secondo punto di spawn e registrare il punto di generazione da cui è stato creato un oggetto.</span><span class="sxs-lookup"><span data-stu-id="aebbc-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="aebbc-552">Quando si carica il file di dati, riprodurre le forme generate dalla posizione in cui sono state create originariamente.</span><span class="sxs-lookup"><span data-stu-id="aebbc-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="aebbc-553">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="aebbc-553">Exercise 2</span></span>

<span data-ttu-id="aebbc-554">Creare un modo per riavviare l'app, anziché riaprirla ogni volta.</span><span class="sxs-lookup"><span data-stu-id="aebbc-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="aebbc-555">Il **caricamento di scene** è un punto di partenza valido.</span><span class="sxs-lookup"><span data-stu-id="aebbc-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="aebbc-556">Al termine di questa operazione, creare un modo per cancellare l'elenco Archiviato in *archiviazione di Azure*, in modo che possa essere facilmente reimpostato dall'app.</span><span class="sxs-lookup"><span data-stu-id="aebbc-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
