---
title: MR e 305 Azure - funzioni e archiviazione
description: Completare questo corso di informazioni su come implementare l'archiviazione di Azure e le funzioni all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, funzioni, archiviazione, hololens, vr immersivi,
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598302"
---
>[!NOTE]
><span data-ttu-id="d0407-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="d0407-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d0407-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="d0407-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d0407-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="d0407-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d0407-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="d0407-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d0407-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d0407-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d0407-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="d0407-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="d0407-110">MR e Azure 305: Funzioni e archiviazione</span><span class="sxs-lookup"><span data-stu-id="d0407-110">MR and Azure 305: Functions and storage</span></span>

![versione finale del prodotto-avvio](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="d0407-112">In questo corso, si apprenderà come creare e usare funzioni di Azure e archiviare i dati con una risorsa di archiviazione di Azure, all'interno di un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d0407-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="d0407-113">*Funzioni di Azure* è un servizio Microsoft, che consente agli sviluppatori di eseguire piccole porzioni di codice, 'le funzioni', in Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="d0407-114">Ciò consente di delegare lavoro nel cloud, anziché l'applicazione locale, che può avere molti vantaggi.</span><span class="sxs-lookup"><span data-stu-id="d0407-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="d0407-115">*Funzioni di Azure* supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, Node. js, Java e PHP.</span><span class="sxs-lookup"><span data-stu-id="d0407-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="d0407-116">Per altre informazioni, visitare il [articolo funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="d0407-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="d0407-117">*Archiviazione di Azure* è un servizio cloud Microsoft, che consente agli sviluppatori di archiviare i dati, con l'assicurazione che sarà altamente disponibile, sicuro, durevole, scalabile e ridondante.</span><span class="sxs-lookup"><span data-stu-id="d0407-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="d0407-118">Ciò significa che Microsoft gestirà tutti manutenzione e i problemi critici per l'utente.</span><span class="sxs-lookup"><span data-stu-id="d0407-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="d0407-119">Per altre informazioni, visitare il [articolo di archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="d0407-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="d0407-120">Dopo aver completato il corso, si avrà un'applicazione di realtà mista visore VR immersivi che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0407-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="d0407-121">Consentire all'utente di estasiati intorno a una scena.</span><span class="sxs-lookup"><span data-stu-id="d0407-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="d0407-122">Attivare la generazione di oggetti, quando l'utente gazes in un 'button' 3D.</span><span class="sxs-lookup"><span data-stu-id="d0407-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="d0407-123">Gli oggetti generati verranno scelto da una funzione di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="d0407-124">Poiché ogni oggetto viene generato, l'applicazione archivierà il tipo di oggetto in un *File di Azure*che si trova in *archiviazione di Azure*.</span><span class="sxs-lookup"><span data-stu-id="d0407-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="d0407-125">Durante il caricamento di una seconda volta, il *File di Azure* dati verranno recuperati e utilizzati per riprodurre le azioni di generazione dell'istanza precedente dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d0407-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="d0407-126">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="d0407-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="d0407-127">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="d0407-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="d0407-128">È il compito di utilizzare le competenze acquisite in questo corso per migliorare le applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d0407-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="d0407-129">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="d0407-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d0407-130">Corso</span><span class="sxs-lookup"><span data-stu-id="d0407-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d0407-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d0407-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d0407-132"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="d0407-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d0407-133">MR e Azure 305: Funzioni e archiviazione</span><span class="sxs-lookup"><span data-stu-id="d0407-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="d0407-134">✔️</span><span class="sxs-lookup"><span data-stu-id="d0407-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d0407-135">✔️</span><span class="sxs-lookup"><span data-stu-id="d0407-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="d0407-136">Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d0407-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="d0407-137">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d0407-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d0407-138">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="d0407-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="d0407-139">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="d0407-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="d0407-140">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="d0407-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="d0407-141">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .</span><span class="sxs-lookup"><span data-stu-id="d0407-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="d0407-142">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="d0407-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="d0407-143">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="d0407-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="d0407-144">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="d0407-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d0407-145">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="d0407-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d0407-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="d0407-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d0407-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d0407-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="d0407-148">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="d0407-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="d0407-149">Una sottoscrizione a un account Azure per la creazione di risorse di Azure</span><span class="sxs-lookup"><span data-stu-id="d0407-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="d0407-150">Accesso a Internet per il recupero di dati e il programma di installazione di Azure</span><span class="sxs-lookup"><span data-stu-id="d0407-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="d0407-151">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="d0407-151">Before you start</span></span>

<span data-ttu-id="d0407-152">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="d0407-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="d0407-153">Capitolo 1 - portale di Azure</span><span class="sxs-lookup"><span data-stu-id="d0407-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="d0407-154">Usare la **servizio di archiviazione di Azure**, sarà necessario creare e configurare un **Account di archiviazione** nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="d0407-155">Accedi per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="d0407-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="d0407-156">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="d0407-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="d0407-157">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="d0407-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="d0407-158">Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *account di archiviazione*, fare clic su **invio**.</span><span class="sxs-lookup"><span data-stu-id="d0407-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![ricerca di archiviazione di Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="d0407-160">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="d0407-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="d0407-161">La nuova pagina fornirà una descrizione del *account di archiviazione Azure* servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="d0407-162">AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Crea servizio](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="d0407-164">Dopo avere fatto clic su **Create**:</span><span class="sxs-lookup"><span data-stu-id="d0407-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="d0407-165">Inserire un *nome* per l'account, tenere presente questo campo accetta solo numeri e lettere minuscole.</span><span class="sxs-lookup"><span data-stu-id="d0407-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="d0407-166">Per la *modello di distribuzione*, selezionare **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="d0407-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="d0407-167">Per la *tipologia Account*, selezionare **archiviazione (utilizzo generico v1)**.</span><span class="sxs-lookup"><span data-stu-id="d0407-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="d0407-168">Determinare il *posizione* per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="d0407-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="d0407-169">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="d0407-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="d0407-170">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="d0407-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="d0407-171">Per la *replica* selezionate **Read-access-archiviazione geograficamente ridondante (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="d0407-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="d0407-172">Per la *Performance*, selezionare **Standard**.</span><span class="sxs-lookup"><span data-stu-id="d0407-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="d0407-173">Lasciare *trasferimento sicuro obbligatorio* come **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="d0407-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="d0407-174">Selezionare una *sottoscrizione*.</span><span class="sxs-lookup"><span data-stu-id="d0407-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="d0407-175">Scegliere una *gruppo di risorse* o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="d0407-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="d0407-176">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d0407-177">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="d0407-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="d0407-178">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="d0407-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="d0407-179">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="d0407-180">Selezionare **Create**.</span><span class="sxs-lookup"><span data-stu-id="d0407-180">Select **Create**.</span></span>

        ![informazioni di input del servizio](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="d0407-182">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="d0407-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="d0407-183">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="d0407-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nuova notifica nel portale di azure](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="d0407-185">Fare clic su notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-185">Click on the notifications to explore your new Service instance.</span></span>

    ![Vai alla risorsa](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="d0407-187">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="d0407-188">Si verrà indirizzati alla nuova *account di archiviazione* l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![tasti di scelta](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="d0407-190">Fare clic su *chiavi di accesso*, per visualizzare gli endpoint per questo servizio cloud.</span><span class="sxs-lookup"><span data-stu-id="d0407-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="d0407-191">Usare *Notepad* o simile, per copiare una delle chiavi per un uso successivo.</span><span class="sxs-lookup"><span data-stu-id="d0407-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="d0407-192">Si noti anche il *stringa di connessione* valore, perché verrà usato nel *servizi di Azure* (classe), che verrà creato in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="d0407-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![Copiare la stringa di connessione](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="d0407-194">Capitolo 2: configurazione di una funzione di Azure</span><span class="sxs-lookup"><span data-stu-id="d0407-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="d0407-195">Ora si scriverà un' **Azure** **funzione** nel servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="d0407-196">È possibile usare un **funzione di Azure** per eseguire praticamente qualsiasi operazione che si farebbe con una funzione classica nel codice, la differenza è che questa funzione è accessibile da qualsiasi applicazione che dispone delle credenziali per accedere all'Account Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="d0407-197">Per creare una funzione di Azure:</span><span class="sxs-lookup"><span data-stu-id="d0407-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="d0407-198">Dalle *portale di Azure*, fare clic su **New** nell'angolo in alto a sinistra e cercare *App per le funzioni*, fare clic su **invio**.</span><span class="sxs-lookup"><span data-stu-id="d0407-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Creare app per le funzioni](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="d0407-200">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="d0407-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="d0407-201">La nuova pagina fornirà una descrizione del *App per le funzioni* servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="d0407-202">AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![informazioni sull'app (funzione)](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="d0407-204">Dopo avere fatto clic su **Create**:</span><span class="sxs-lookup"><span data-stu-id="d0407-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="d0407-205">Fornire un' *nome App*.</span><span class="sxs-lookup"><span data-stu-id="d0407-205">Provide an *App name*.</span></span> <span data-ttu-id="d0407-206">Solo lettere e numeri possono essere usati di seguito (è consentito sia maiuscole o minuscole).</span><span class="sxs-lookup"><span data-stu-id="d0407-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="d0407-207">Selezionare la voce preferita *sottoscrizione*.</span><span class="sxs-lookup"><span data-stu-id="d0407-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="d0407-208">Scegliere una *gruppo di risorse* o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="d0407-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="d0407-209">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d0407-210">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="d0407-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="d0407-211">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="d0407-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="d0407-212">Per questo esercizio, selezionare *Windows* come la scelta **OS**.</span><span class="sxs-lookup"><span data-stu-id="d0407-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="d0407-213">Selezionare *piano a consumo* per il **piano di Hosting**.</span><span class="sxs-lookup"><span data-stu-id="d0407-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="d0407-214">Determinare il *posizione* per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="d0407-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="d0407-215">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="d0407-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="d0407-216">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="d0407-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="d0407-217">Per ottenere prestazioni ottimali, selezionare la stessa area dell'account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="d0407-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="d0407-218">Per la *memorizzazione*, selezionare **Usa esistente**, e quindi utilizzando il menu a discesa, individuare lo spazio di archiviazione creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d0407-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="d0407-219">Lasciare *Application Insights* disattivata per questo esercizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-219">Leave *Application Insights* off for this exercise.</span></span>

        ![dettagli dell'app input (funzione)](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="d0407-221">Fare clic sul pulsante **Crea**.</span><span class="sxs-lookup"><span data-stu-id="d0407-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="d0407-222">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="d0407-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="d0407-223">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="d0407-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nuove notifiche del portale di azure](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="d0407-225">Fare clic su notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![Passare alla risorsa app per le funzioni](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="d0407-227">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="d0407-228">Si verrà indirizzati alla nuova *App per le funzioni* l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="d0407-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="d0407-229">Nel *App per le funzioni* dashboard, posizionare il mouse sopra *funzioni*trovato all'interno del pannello a sinistra e quindi fare clic sui **+ (segno più)** simbolo.</span><span class="sxs-lookup"><span data-stu-id="d0407-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![Creare una nuova funzione](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="d0407-231">Nella pagina successiva, assicurarsi **Webhook e API** è selezionata e per *scegliere una lingua* seleziona **CSharp**, come sarà la lingua utilizzata per questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="d0407-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="d0407-232">Infine, fare clic il **consente di creare questa funzione** pulsante.</span><span class="sxs-lookup"><span data-stu-id="d0407-232">Lastly, click the **Create this function** button.</span></span>

    ![Selezionare web hook csharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="d0407-234">Si verrà reindirizzati al codice di pagina (Run. csx), in caso contrario, fare clic sulla funzione appena creata nell'elenco le funzioni all'interno del pannello a sinistra.</span><span class="sxs-lookup"><span data-stu-id="d0407-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![Aprire una nuova funzione](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="d0407-236">Copiare il codice seguente alla funzione.</span><span class="sxs-lookup"><span data-stu-id="d0407-236">Copy the following code into your function.</span></span> <span data-ttu-id="d0407-237">Questa funzione restituirà semplicemente un numero intero casuale compreso tra 0 e 2 quando viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="d0407-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="d0407-238">Non preoccuparti del codice esistente, è possibile incollare nella parte superiore di esso.</span><span class="sxs-lookup"><span data-stu-id="d0407-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

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

13. <span data-ttu-id="d0407-239">Selezionare **Salva**.</span><span class="sxs-lookup"><span data-stu-id="d0407-239">Select **Save**.</span></span>

14. <span data-ttu-id="d0407-240">Il risultato dovrebbe essere simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="d0407-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="d0407-241">Fare clic su **recupera URL della funzione** e prendere nota del *endpoint* visualizzato.</span><span class="sxs-lookup"><span data-stu-id="d0407-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="d0407-242">È necessario inserirla nel *servizi di Azure* classe che verrà creato più avanti in questo corso.</span><span class="sxs-lookup"><span data-stu-id="d0407-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![ottenere l'endpoint (funzione)](images/AzureLabs-Lab5-16.png)

    ![ottenere l'endpoint (funzione)](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="d0407-245">Capitolo 3 - configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d0407-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="d0407-246">Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="d0407-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="d0407-247">Configurare e testare il visore VR immersivi di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d0407-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="d0407-248">Verrà **non** richiedono controller di movimento a questo corso.</span><span class="sxs-lookup"><span data-stu-id="d0407-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="d0407-249">Se è necessario il supporto di configurazione di visore VR immersivi, please [visitare la realtà mista configurare articolo](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="d0407-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="d0407-250">Aprire Unity e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="d0407-250">Open Unity and click **New**.</span></span>

    ![creare nuovo progetto unity](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="d0407-252">A questo punto, è necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="d0407-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="d0407-253">Inserire **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="d0407-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="d0407-254">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="d0407-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="d0407-255">Impostare il *posizione* a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="d0407-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d0407-256">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="d0407-256">Then, click **Create project**.</span></span>

    ![assegnare un nome nuovo progetto unity](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="d0407-258">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d0407-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d0407-259">Passare a **modificare* > *preferenze** e quindi dalla nuova finestra, passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="d0407-259">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d0407-260">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="d0407-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="d0407-261">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="d0407-261">Close the **Preferences** window.</span></span>

    ![set di visual studio come editor di script](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="d0407-263">Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.</span><span class="sxs-lookup"><span data-stu-id="d0407-263">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![piattaforma del commutatore alla piattaforma uwp](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="d0407-265">Passare a **File > Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="d0407-265">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="d0407-266">**Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="d0407-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="d0407-267">Per Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="d0407-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="d0407-268">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="d0407-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="d0407-269">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="d0407-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="d0407-270">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="d0407-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="d0407-271">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="d0407-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="d0407-272">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="d0407-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="d0407-273">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="d0407-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="d0407-274">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="d0407-274">A save window will appear.</span></span>

            ![aggiungere scene open](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="d0407-276">Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="d0407-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![creare la cartella in background](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="d0407-278">Aprire appena creato **scene** cartella e quindi il **nome File:** campo di testo, digitare **FunctionsScene**, quindi premere **Salva**.</span><span class="sxs-lookup"><span data-stu-id="d0407-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![Salva scena le funzioni](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="d0407-280">Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="d0407-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![Salva scena le funzioni](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="d0407-282">Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.</span><span class="sxs-lookup"><span data-stu-id="d0407-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![impostazioni del lettore di controllo](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="d0407-284">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="d0407-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="d0407-285">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="d0407-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="d0407-286">**Versione del Runtime di scripting** deve essere **sperimentale** (.NET 4.6 equivalente), che attiverà una necessità di riavviare l'Editor.</span><span class="sxs-lookup"><span data-stu-id="d0407-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="d0407-287">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="d0407-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="d0407-288">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="d0407-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="d0407-289">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="d0407-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="d0407-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d0407-290">**InternetClient**</span></span>

            ![set di funzionalità](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="d0407-292">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **le impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **realtà mista di Windows SDK** viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="d0407-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![XR le impostazioni](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="d0407-294">Nuovamente in *Build Settings* *Unity C# progetti* non è più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="d0407-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![progetti c# segni di graduazione](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="d0407-296">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="d0407-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="d0407-297">Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="d0407-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="d0407-298">Capitolo 4 - la fotocamera principale di installazione</span><span class="sxs-lookup"><span data-stu-id="d0407-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0407-299">Se si vuole ignorare la *configurare Unity* componenti di questo corso e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo nel progetto come un [personalizzato Pacchetto](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="d0407-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="d0407-300">Questa conterrà anche la DLL del capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="d0407-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="d0407-301">Al termine dell'importazione, sono la prosecuzione [capitolo 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="d0407-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="d0407-302">Nel *Pannello di gerarchia*, si noterà un oggetto denominato **Main Camera**, questo oggetto rappresenta il punto di vista della "head" quando si è "l'applicazione interni".</span><span class="sxs-lookup"><span data-stu-id="d0407-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="d0407-303">Con il Dashboard di Unity fronte, selezionare la **Main Camera GameObject**.</span><span class="sxs-lookup"><span data-stu-id="d0407-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="d0407-304">Si noterà che il *Pannello di controllo* (in genere trovato a destra, all'interno del Dashboard) mostrerà i vari componenti di tale *GameObject*, con *trasformare* nella parte superiore, seguita da *fotocamera*e alcuni altri componenti.</span><span class="sxs-lookup"><span data-stu-id="d0407-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="d0407-305">È necessario reimpostare la trasformazione della fotocamera principale, in modo che sia posizionato correttamente.</span><span class="sxs-lookup"><span data-stu-id="d0407-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="d0407-306">A questo scopo, selezionare la **a forma di ingranaggio** icona accanto della fotocamera *trasformare* componente e selezionare **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="d0407-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![reimpostazione della trasformazione](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="d0407-308">Aggiornare quindi il **trasformare** componente come illustrato:</span><span class="sxs-lookup"><span data-stu-id="d0407-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="d0407-309">TRASFORMAZIONE - POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="d0407-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="d0407-310">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-310">**X**</span></span>   | <span data-ttu-id="d0407-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-311">**Y**</span></span>                     | <span data-ttu-id="d0407-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-312">**Z**</span></span> |
    | <span data-ttu-id="d0407-313">0</span><span class="sxs-lookup"><span data-stu-id="d0407-313">0</span></span>       | <span data-ttu-id="d0407-314">1</span><span class="sxs-lookup"><span data-stu-id="d0407-314">1</span></span>                         | <span data-ttu-id="d0407-315">0</span><span class="sxs-lookup"><span data-stu-id="d0407-315">0</span></span>     |    

    |       | <span data-ttu-id="d0407-316">TRASFORMAZIONE - ROTAZIONE</span><span class="sxs-lookup"><span data-stu-id="d0407-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="d0407-317">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-317">**X**</span></span> | <span data-ttu-id="d0407-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-318">**Y**</span></span>                | <span data-ttu-id="d0407-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-319">**Z**</span></span> |
    | <span data-ttu-id="d0407-320">0</span><span class="sxs-lookup"><span data-stu-id="d0407-320">0</span></span>     | <span data-ttu-id="d0407-321">0</span><span class="sxs-lookup"><span data-stu-id="d0407-321">0</span></span>                    | <span data-ttu-id="d0407-322">0</span><span class="sxs-lookup"><span data-stu-id="d0407-322">0</span></span>     |

    |       | <span data-ttu-id="d0407-323">TRANSFORM - SCALE</span><span class="sxs-lookup"><span data-stu-id="d0407-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="d0407-324">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-324">**X**</span></span> | <span data-ttu-id="d0407-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-325">**Y**</span></span>             | <span data-ttu-id="d0407-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-326">**Z**</span></span> |
    | <span data-ttu-id="d0407-327">1</span><span class="sxs-lookup"><span data-stu-id="d0407-327">1</span></span>     | <span data-ttu-id="d0407-328">1</span><span class="sxs-lookup"><span data-stu-id="d0407-328">1</span></span>                 | <span data-ttu-id="d0407-329">1</span><span class="sxs-lookup"><span data-stu-id="d0407-329">1</span></span>     |

    ![trasformazione della fotocamera set](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="d0407-331">Capitolo 5 - configurare la scena Unity</span><span class="sxs-lookup"><span data-stu-id="d0407-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="d0407-332">Pulsante destro del mouse in un'area vuota del *Pannello di gerarchia*, in **oggetto 3D**, aggiungere un **piano**.</span><span class="sxs-lookup"><span data-stu-id="d0407-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![Crea nuovo piano](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="d0407-334">Con il **piano** dell'oggetto selezionato, modificare i parametri seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="d0407-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="d0407-335">TRASFORMAZIONE - POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="d0407-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="d0407-336">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-336">**X**</span></span> | <span data-ttu-id="d0407-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-337">**Y**</span></span>                | <span data-ttu-id="d0407-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-338">**Z**</span></span> |
    | <span data-ttu-id="d0407-339">0</span><span class="sxs-lookup"><span data-stu-id="d0407-339">0</span></span>     | <span data-ttu-id="d0407-340">0</span><span class="sxs-lookup"><span data-stu-id="d0407-340">0</span></span>                    | <span data-ttu-id="d0407-341">4</span><span class="sxs-lookup"><span data-stu-id="d0407-341">4</span></span>     |

    |       | <span data-ttu-id="d0407-342">TRANSFORM - SCALE</span><span class="sxs-lookup"><span data-stu-id="d0407-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="d0407-343">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-343">**X**</span></span> | <span data-ttu-id="d0407-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-344">**Y**</span></span>             | <span data-ttu-id="d0407-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-345">**Z**</span></span> |
    | <span data-ttu-id="d0407-346">10</span><span class="sxs-lookup"><span data-stu-id="d0407-346">10</span></span>    | <span data-ttu-id="d0407-347">1</span><span class="sxs-lookup"><span data-stu-id="d0407-347">1</span></span>                 | <span data-ttu-id="d0407-348">10</span><span class="sxs-lookup"><span data-stu-id="d0407-348">10</span></span>    |

    ![Imposta piano posizione e scala](images/AzureLabs-Lab5-32.png)

    ![visualizzazione scena del piano](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="d0407-351">Pulsante destro del mouse in un'area vuota del *Pannello di gerarchia*, in **oggetto 3D**, aggiungere un **cubo**.</span><span class="sxs-lookup"><span data-stu-id="d0407-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="d0407-352">Rinominare il cubo **GazeButton** (con il cubo selezionato, premere 'F2').</span><span class="sxs-lookup"><span data-stu-id="d0407-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="d0407-353">Modificare i parametri seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="d0407-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="d0407-354">TRASFORMAZIONE - POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="d0407-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="d0407-355">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-355">**X**</span></span> | <span data-ttu-id="d0407-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-356">**Y**</span></span>                | <span data-ttu-id="d0407-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-357">**Z**</span></span> |
        | <span data-ttu-id="d0407-358">0</span><span class="sxs-lookup"><span data-stu-id="d0407-358">0</span></span>     | <span data-ttu-id="d0407-359">3</span><span class="sxs-lookup"><span data-stu-id="d0407-359">3</span></span>                    | <span data-ttu-id="d0407-360">5</span><span class="sxs-lookup"><span data-stu-id="d0407-360">5</span></span>     |


        ![set sguardo pulsante trasformazione](images/AzureLabs-Lab5-34.png)

        ![estasiati visualizzazione scena pulsante](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="d0407-363">Fare clic sui **Tag** pulsante a discesa e fare clic su **aggiungere Tag** per aprire il *tag & riquadro livelli*.</span><span class="sxs-lookup"><span data-stu-id="d0407-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Aggiungi nuovo tag](images/AzureLabs-Lab5-36.png)

        ![Select plus](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="d0407-366">Selezionare il **+ (segno più)** pulsante e il *nuovo nome del Tag* immettere **GazeButton**e premere **Salva**.</span><span class="sxs-lookup"><span data-stu-id="d0407-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![nuovo tag di nome](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="d0407-368">Fare clic sul **GazeButton** dell'oggetto nel *pannello gerarchia*e nel *Pannello di controllo*, assegnare l'oggetto appena creato **GazeButton** tag.</span><span class="sxs-lookup"><span data-stu-id="d0407-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![pulsante di sguardo assegna il nuovo tag](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="d0407-370">Fare clic sul **GazeButton** dell'oggetto, nelle *pannello gerarchia*e aggiungere un **GameObject vuoto** (che verrà aggiunto come un *figlio* oggetto).</span><span class="sxs-lookup"><span data-stu-id="d0407-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="d0407-371">Selezionare il nuovo oggetto e rinominarlo **ShapeSpawnPoint**.</span><span class="sxs-lookup"><span data-stu-id="d0407-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="d0407-372">Modificare i parametri seguenti nel *Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="d0407-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="d0407-373">TRASFORMAZIONE - POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="d0407-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="d0407-374">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-374">**X**</span></span> |<span data-ttu-id="d0407-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-375">**Y**</span></span>                 | <span data-ttu-id="d0407-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-376">**Z**</span></span> |
        | <span data-ttu-id="d0407-377">0</span><span class="sxs-lookup"><span data-stu-id="d0407-377">0</span></span>     | <span data-ttu-id="d0407-378">-1</span><span class="sxs-lookup"><span data-stu-id="d0407-378">-1</span></span>                   | <span data-ttu-id="d0407-379">0</span><span class="sxs-lookup"><span data-stu-id="d0407-379">0</span></span>     |

        ![trasformazione di punto di aggiornamento forma spawn](images/AzureLabs-Lab5-40.png)

        ![vista forma spawn punto della scena](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="d0407-382">Successivamente verrà creato un **testo 3D** oggetto da fornire commenti e suggerimenti sullo stato del servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="d0407-383">Fare clic con il pulsante destro sul **GazeButton** nella gerarchia del pannello nuovo e aggiungere un **oggetto 3D > testo 3D** dell'oggetto come un *figlio*.</span><span class="sxs-lookup"><span data-stu-id="d0407-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object > 3D Text** object as a *child*.</span></span>

    ![creare nuovi oggetti di testo 3D](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="d0407-385">Rinominare il **testo 3D** obiettare **AzureStatusText**.</span><span class="sxs-lookup"><span data-stu-id="d0407-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="d0407-386">Modifica il **AzureStatusText** trasformazione dell'oggetto come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d0407-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="d0407-387">TRASFORMAZIONE - POSIZIONE</span><span class="sxs-lookup"><span data-stu-id="d0407-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="d0407-388">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-388">**X**</span></span> | <span data-ttu-id="d0407-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-389">**Y**</span></span>                | <span data-ttu-id="d0407-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-390">**Z**</span></span> |
    | <span data-ttu-id="d0407-391">0</span><span class="sxs-lookup"><span data-stu-id="d0407-391">0</span></span>     | <span data-ttu-id="d0407-392">0</span><span class="sxs-lookup"><span data-stu-id="d0407-392">0</span></span>                    | <span data-ttu-id="d0407-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="d0407-393">-0.6</span></span>  |

    |       | <span data-ttu-id="d0407-394">TRANSFORM - SCALE</span><span class="sxs-lookup"><span data-stu-id="d0407-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="d0407-395">**X**</span><span class="sxs-lookup"><span data-stu-id="d0407-395">**X**</span></span> | <span data-ttu-id="d0407-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="d0407-396">**Y**</span></span>             | <span data-ttu-id="d0407-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="d0407-397">**Z**</span></span> |
    | <span data-ttu-id="d0407-398">0.1</span><span class="sxs-lookup"><span data-stu-id="d0407-398">0.1</span></span>   | <span data-ttu-id="d0407-399">0.1</span><span class="sxs-lookup"><span data-stu-id="d0407-399">0.1</span></span>               | <span data-ttu-id="d0407-400">0.1</span><span class="sxs-lookup"><span data-stu-id="d0407-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="d0407-401">Non occorre preoccuparsi se sembrano essere disattivato centre, come questo problema verrà risolto quando il seguente testo Mesh componente viene aggiornato.</span><span class="sxs-lookup"><span data-stu-id="d0407-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="d0407-402">Modifica il **Mesh testo** componente in modo che corrisponda di seguito:</span><span class="sxs-lookup"><span data-stu-id="d0407-402">Change the **Text Mesh** component to match the below:</span></span>

    ![componente mesh testo set](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="d0407-404">Colore selezionato qui è di colore esadecimale: **000000FF**, tuttavia è possibile scegliere il proprio, assicurarsi sia leggibile.</span><span class="sxs-lookup"><span data-stu-id="d0407-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="d0407-405">La struttura di gerarchia pannello sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="d0407-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![testo mesh nella visualizzazione scena](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="d0407-407">La scena a questo punto dovrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="d0407-407">Your scene should now look like this:</span></span>

    ![testo mesh nella visualizzazione scena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="d0407-409">Capitolo 6: importare l'archiviazione di Azure per Unity</span><span class="sxs-lookup"><span data-stu-id="d0407-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="d0407-410">Si userà archiviazione di Azure per Unity (che a sua volta si basa su .net SDK per Azure).</span><span class="sxs-lookup"><span data-stu-id="d0407-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="d0407-411">È possibile leggere altre informazioni, vedere la [archiviazione di Azure per l'articolo di Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="d0407-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="d0407-412">È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="d0407-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="d0407-413">Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.</span><span class="sxs-lookup"><span data-stu-id="d0407-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="d0407-414">Per importare il SDK in un progetto, assicurarsi di aver scaricato la versione più recente ['.unitypackage' da GitHub](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="d0407-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="d0407-415">Quindi, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0407-415">Then, do the following:</span></span>

1.  <span data-ttu-id="d0407-416">Aggiungere il **.unitypackage** file da Unity tramite il **asset > Importa pacchetto > pacchetto personalizzato** l'opzione di menu.</span><span class="sxs-lookup"><span data-stu-id="d0407-416">Add the **.unitypackage** file to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="d0407-417">Nel **Importa pacchetto Unity** casella visualizzata, è possibile selezionare tutti gli elementi in \**plug-in* > \* archiviazione \* \*.</span><span class="sxs-lookup"><span data-stu-id="d0407-417">In the **Import Unity Package** box that pops up, you can select everything under \**Plugin* > \*Storage\*\*.</span></span> <span data-ttu-id="d0407-418">Deseleziona tutto il resto, perché non è necessaria per questo corso.</span><span class="sxs-lookup"><span data-stu-id="d0407-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Importa pacchetto](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="d0407-420">Scegliere il **importazione** pulsante per aggiungere elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="d0407-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="d0407-421">Passare al *archiviazione* cartella sotto *Plugins*, nella visualizzazione del progetto e selezionare il plug-in seguenti *solo*:</span><span class="sxs-lookup"><span data-stu-id="d0407-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="d0407-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="d0407-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="d0407-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="d0407-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="d0407-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="d0407-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="d0407-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="d0407-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="d0407-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="d0407-426">System.Spatial</span></span>

        ![Deselezionare qualsiasi piattaforma](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="d0407-428">Con *questi plug-in specifici* è selezionata, **deselezionare** *Any Platform* e **deselezionare** *WSAPlayer* quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="d0407-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![applicare le DLL di piattaforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="d0407-430">Vengono contrassegnati questi plug-in particolare per essere usato solo nell'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="d0407-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="d0407-431">Questo avviene perché sono presenti versioni diverse dello stesso plug-nella cartella WSA che verrà utilizzata dopo che il progetto viene esportato da Unity.</span><span class="sxs-lookup"><span data-stu-id="d0407-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="d0407-432">Nel *archiviazione* cartella plug-in, selezionare solo:</span><span class="sxs-lookup"><span data-stu-id="d0407-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="d0407-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="d0407-433">Microsoft.Data.Services.Client</span></span>

        ![non elabora set di DLL](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="d0407-435">Verificare i **processo non** nella casella *impostazioni piattaforma* e fare clic su **Apply**.</span><span class="sxs-lookup"><span data-stu-id="d0407-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="d0407-437">Vengono contrassegnati questo plug-in "Non elabora" perché il patcher assembly di Unity ha difficoltà a questo plug-in di elaborazione.</span><span class="sxs-lookup"><span data-stu-id="d0407-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="d0407-438">Il plug-in continuerà a funzionare anche se non è stato elaborato.</span><span class="sxs-lookup"><span data-stu-id="d0407-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="d0407-439">Capitolo 7 - creare la classe di servizi di Azure</span><span class="sxs-lookup"><span data-stu-id="d0407-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="d0407-440">La prima classe si intende creare è il *servizi di Azure* classe.</span><span class="sxs-lookup"><span data-stu-id="d0407-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="d0407-441">Il *servizi di Azure* classe sarà responsabile per:</span><span class="sxs-lookup"><span data-stu-id="d0407-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="d0407-442">Archiviare le credenziali dell'Account di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="d0407-443">Chiamare la funzione di App di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="d0407-444">Il caricamento e il download del file di dati nell'archiviazione Cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="d0407-445">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d0407-445">To create this Class:</span></span>

1.  <span data-ttu-id="d0407-446">Fare doppio clic nella *bene* cartella, che si trova nel pannello dei progetti **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="d0407-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="d0407-447">Denominare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="d0407-447">Name the folder **Scripts**.</span></span>

    ![Crea nuova cartella](images/AzureLabs-Lab5-50.png)

    ![cartella chiamata - script](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="d0407-450">Fare doppio clic sulla cartella appena creata, per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="d0407-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="d0407-451">Pulsante destro del mouse all'interno della cartella **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d0407-451">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="d0407-452">Chiamare lo script *servizi di Azure*.</span><span class="sxs-lookup"><span data-stu-id="d0407-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="d0407-453">Fare doppio clic su nuova *servizi di Azure* classe per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="d0407-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="d0407-454">Aggiungere spazi dei nomi seguenti all'inizio del *servizi di Azure*:</span><span class="sxs-lookup"><span data-stu-id="d0407-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="d0407-455">Aggiungere i seguenti campi di controllo all'interno di *servizi di Azure* classe:</span><span class="sxs-lookup"><span data-stu-id="d0407-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

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

7.  <span data-ttu-id="d0407-456">Quindi aggiungere le seguenti variabili membro all'interno di *servizi di Azure* classe:</span><span class="sxs-lookup"><span data-stu-id="d0407-456">Then add the following member variables inside the *AzureServices* class:</span></span>

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
    > <span data-ttu-id="d0407-457">Assicurarsi di sostituire il *endpoint* e *stringa di connessione* valori con i valori da archiviazione di Azure, disponibile nel portale di Azure</span><span class="sxs-lookup"><span data-stu-id="d0407-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="d0407-458">Codice per un *Awake()* e *Start ()* metodi deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="d0407-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="d0407-459">Questi metodi verranno chiamati quando si inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="d0407-459">These methods will be called when the class initializes:</span></span>

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
    > <span data-ttu-id="d0407-460">Si compilerà il codice per *CallAzureFunctionForNextShape()* in un [capitolo future](#chapter-10---completing-the-AzureServices-class).</span><span class="sxs-lookup"><span data-stu-id="d0407-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-AzureServices-class).</span></span>

9.  <span data-ttu-id="d0407-461">Eliminare il *Update ()* metodo poiché questa classe non verrà utilizzate.</span><span class="sxs-lookup"><span data-stu-id="d0407-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="d0407-462">Salvare le modifiche in Visual Studio e quindi tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="d0407-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="d0407-463">Fare clic e trascinare il *servizi di Azure* classe dalla cartella degli script per l'oggetto Main Camera nel *gerarchia pannello*.</span><span class="sxs-lookup"><span data-stu-id="d0407-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="d0407-464">Selezionare la fotocamera principale, quindi selezionare il **AzureStatusText** oggetto figlio da sotto il **GazeButton** dell'oggetto e inserirla all'interno di **AzureStatusText** target di riferimento nel campo la *Inspector*, per fornire il riferimento al *servizi di Azure* script.</span><span class="sxs-lookup"><span data-stu-id="d0407-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![assegnare una destinazione del riferimento di testo dello stato di azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="d0407-466">Capitolo 8 - creare la classe ShapeFactory</span><span class="sxs-lookup"><span data-stu-id="d0407-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="d0407-467">Lo script successivo per la creazione, è il *ShapeFactory* classe.</span><span class="sxs-lookup"><span data-stu-id="d0407-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="d0407-468">Il ruolo di questa classe consiste nel creare una nuova forma, quando richiesto e conservare una cronologia delle forme creato in una *elenco di cronologia forma*.</span><span class="sxs-lookup"><span data-stu-id="d0407-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="d0407-469">Ogni volta che viene creata una forma, il *elenco cronologia forma* viene aggiornato nel *AzureService* classe e quindi archiviati nel *archiviazione di Azure*.</span><span class="sxs-lookup"><span data-stu-id="d0407-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="d0407-470">Quando viene avviata l'applicazione, se viene trovato un file archiviato nel *archiviazione di Azure*, il *elenco cronologia forma* viene recuperato e riprodotti, con il **testo 3D** oggetto fornendo indica se il generato shape è dall'archiviazione o i nuovi.</span><span class="sxs-lookup"><span data-stu-id="d0407-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="d0407-471">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d0407-471">To create this class:</span></span>

1.  <span data-ttu-id="d0407-472">Andare alla **script** cartella creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d0407-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="d0407-473">Pulsante destro del mouse all'interno della cartella **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d0407-473">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="d0407-474">Chiamare lo script *ShapeFactory*.</span><span class="sxs-lookup"><span data-stu-id="d0407-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="d0407-475">Fare doppio clic su nuova *ShapeFactory* script per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="d0407-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="d0407-476">Verificare che il *ShapeFactory* classe include spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0407-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="d0407-477">Aggiungere le variabili mostrate di seguito per il *ShapeFactory* e sostituire il *Start ()* e *Awake()* funzioni con quelli seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0407-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

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

6.  <span data-ttu-id="d0407-478">Il *createShape ()* metodo genera le forme di primitive, in base al fornito *integer* parametro.</span><span class="sxs-lookup"><span data-stu-id="d0407-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="d0407-479">Il parametro booleano viene usato per specificare se la forma attualmente creata da un archivio o nuovo.</span><span class="sxs-lookup"><span data-stu-id="d0407-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="d0407-480">Inserire il codice seguente nel *ShapeFactory* (classe), i metodi sopra riportati di seguito:</span><span class="sxs-lookup"><span data-stu-id="d0407-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

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

7.  <span data-ttu-id="d0407-481">Assicurarsi di salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="d0407-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="d0407-482">Indietro nell'Editor di Unity, fare clic e trascinare il *ShapeFactory* classe il **script** cartella per il **Main Camera** dell'oggetto nel *gerarchia pannello*.</span><span class="sxs-lookup"><span data-stu-id="d0407-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="d0407-483">Con la fotocamera principale selezionato si noterà il *ShapeFactory* componente script non è presente il *Spawn punto* riferimento.</span><span class="sxs-lookup"><span data-stu-id="d0407-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="d0407-484">Per risolvere il problema, trascinare il **ShapeSpawnPoint** dall'oggetto il *pannello gerarchia* per il **Spawn punto** target di riferimento.</span><span class="sxs-lookup"><span data-stu-id="d0407-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![destinazione del riferimento di set di forma factory](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="d0407-486">Capitolo 9 - creare la classe sguardo</span><span class="sxs-lookup"><span data-stu-id="d0407-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="d0407-487">È l'ultimo script è necessario creare il *estasiati* classe.</span><span class="sxs-lookup"><span data-stu-id="d0407-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="d0407-488">Questa classe è responsabile per la creazione di un **Raycast** che sarà proiettato in avanti dalla fotocamera principale, per rilevare l'oggetto sta guardando l'utente.</span><span class="sxs-lookup"><span data-stu-id="d0407-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="d0407-489">In questo caso, sarà necessario il Raycast identificare se l'utente sta guardando il **GazeButton** oggetti nella scena e attivare un comportamento.</span><span class="sxs-lookup"><span data-stu-id="d0407-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="d0407-490">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="d0407-490">To create this Class:</span></span>

1.  <span data-ttu-id="d0407-491">Andare alla **script** cartella creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d0407-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="d0407-492">Pulsante destro del mouse nel pannello dei progetti **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d0407-492">Right-click in the Project Panel, **Create > C# Script**.</span></span> <span data-ttu-id="d0407-493">Chiamare lo script *estasiati*.</span><span class="sxs-lookup"><span data-stu-id="d0407-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="d0407-494">Fare doppio clic su nuova *estasiati* script per aprirlo con *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="d0407-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="d0407-495">Assicurarsi che lo spazio dei nomi seguente è incluso nella parte superiore dello script:</span><span class="sxs-lookup"><span data-stu-id="d0407-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="d0407-496">Quindi aggiungere le variabili seguenti all'interno di *estasiati* classe:</span><span class="sxs-lookup"><span data-stu-id="d0407-496">Then add the following variables inside the *Gaze* class:</span></span>

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
> <span data-ttu-id="d0407-497">Alcune di queste variabili potranno essere modificati nel *Editor*.</span><span class="sxs-lookup"><span data-stu-id="d0407-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="d0407-498">Il codice per il *Awake()* e *Start ()* metodi deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="d0407-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="d0407-499">Aggiungere il codice seguente, che verrà creato un oggetto cursore all'inizio, con la *Update ()* metodo, che verrà eseguito il metodo Raycast, oltre a essere in cui è attivato o disattivato il valore booleano GazeEnabled:</span><span class="sxs-lookup"><span data-stu-id="d0407-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

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

8. <span data-ttu-id="d0407-500">Successivamente aggiungere il *UpdateRaycast()* metodo, che sarà un Raycast del progetto e rilevare la destinazione di hit.</span><span class="sxs-lookup"><span data-stu-id="d0407-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

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

9. <span data-ttu-id="d0407-501">Infine, aggiungere il *ResetFocusedObject()* metodo, che si attiva o disattiva il colore corrente oggetti GazeButton, che indica se che si sta creando una nuova forma o No.</span><span class="sxs-lookup"><span data-stu-id="d0407-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

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

10.  <span data-ttu-id="d0407-502">Salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="d0407-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="d0407-503">Fare clic e trascinare il *estasiati* classe dalla cartella degli script per il **Main Camera** dell'oggetto nel *gerarchia pannello*.</span><span class="sxs-lookup"><span data-stu-id="d0407-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="d0407-504">Capitolo 10 - completamento della classe di servizi di Azure</span><span class="sxs-lookup"><span data-stu-id="d0407-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="d0407-505">Con gli altri script posto, è ora possibile *completa* le *servizi di Azure* classe.</span><span class="sxs-lookup"><span data-stu-id="d0407-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="d0407-506">Questo verrà ottenuto tramite:</span><span class="sxs-lookup"><span data-stu-id="d0407-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="d0407-507">Aggiunta di un nuovo metodo denominato *CreateCloudIdentityAsync()* per impostare le variabili di autenticazione necessarie per la comunicazione con Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="d0407-508">Questo metodo inoltre verifica l'esistenza di un File archiviato in precedenza che contiene l'elenco di forma.</span><span class="sxs-lookup"><span data-stu-id="d0407-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="d0407-509">**Se il file si trova**, disabilita l'utente *estasiati*e attivare la creazione di forma, in base al modello di forme, archiviato nel **file di archiviazione di Azure**.</span><span class="sxs-lookup"><span data-stu-id="d0407-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="d0407-510">L'utente può visualizzare, come le **Mesh testo** fornirà display 'Storage' o 'New', a seconda dell'origine di forme.</span><span class="sxs-lookup"><span data-stu-id="d0407-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="d0407-511">**Se viene trovato alcun file**, abiliterà il *estasiati*, consentendo all'utente di creare forme quando si esaminano le **GazeButton** oggetti nella scena.</span><span class="sxs-lookup"><span data-stu-id="d0407-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

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

2.  <span data-ttu-id="d0407-512">Il frammento di codice successivo viene dall'interno di *Start ()* metodo; in cui verrà eseguita una chiamata per il *CreateCloudIdentityAsync()* (metodo).</span><span class="sxs-lookup"><span data-stu-id="d0407-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="d0407-513">È possibile copiare correnti *Start ()* (metodo), con il seguito:</span><span class="sxs-lookup"><span data-stu-id="d0407-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

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

3.  <span data-ttu-id="d0407-514">Compilare il codice per il metodo *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="d0407-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="d0407-515">Si userà creato in precedenza *App per le funzioni* per richiedere un indice di forma.</span><span class="sxs-lookup"><span data-stu-id="d0407-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="d0407-516">Dopo aver ricevuta la nuova forma, questo metodo invia la forma per il *ShapeFactory* classe per creare la nuova forma nella scena.</span><span class="sxs-lookup"><span data-stu-id="d0407-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="d0407-517">Usare il codice seguente per completare il corpo della *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="d0407-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

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

4.  <span data-ttu-id="d0407-518">Aggiungere un metodo per creare una stringa, concatenando i numeri interi archiviati nell'elenco della cronologia di forma e salvarli nel *File di archiviazione di Azure*.</span><span class="sxs-lookup"><span data-stu-id="d0407-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

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

5.  <span data-ttu-id="d0407-519">Aggiungere un metodo per recuperare il testo archiviato nel file che si trova nel *File di archiviazione di Azure* e *deserializzare* in un elenco.</span><span class="sxs-lookup"><span data-stu-id="d0407-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="d0407-520">Una volta completato questo processo, il metodo riabilita lo sguardo in modo che l'utente può aggiungere più forme nella scena.</span><span class="sxs-lookup"><span data-stu-id="d0407-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

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

7.  <span data-ttu-id="d0407-521">Salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="d0407-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="d0407-522">Capitolo 11 - compilare la soluzione di piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="d0407-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="d0407-523">Per iniziare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="d0407-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="d0407-524">Passare a **File > Impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="d0407-524">Go to **File > Build Settings**.</span></span>

    ![Compilare l'app](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="d0407-526">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="d0407-526">Click **Build**.</span></span> <span data-ttu-id="d0407-527">Unity avvierà una *Esplora File* finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in.</span><span class="sxs-lookup"><span data-stu-id="d0407-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="d0407-528">Creare ora tale cartella e denominarlo *App*.</span><span class="sxs-lookup"><span data-stu-id="d0407-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="d0407-529">Quindi con il *App* cartella selezionata, premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="d0407-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="d0407-530">Unity verrà avviata la compilazione del progetto per la *App* cartella.</span><span class="sxs-lookup"><span data-stu-id="d0407-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="d0407-531">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un *Esplora File* finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).</span><span class="sxs-lookup"><span data-stu-id="d0407-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="d0407-532">Capitolo 12 - distribuzione dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="d0407-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="d0407-533">Per distribuire l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="d0407-533">To deploy your application:</span></span>

1.  <span data-ttu-id="d0407-534">Passare al *App* cartella di cui è stata creata nel [ultimo capitolo](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="d0407-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="d0407-535">Verrà visualizzato un file con il nome dell'App con l'estensione '. sln', che è necessario fare doppio clic, pertanto, per aprirlo in *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="d0407-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="d0407-536">Nel **piattaforma soluzione**, selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="d0407-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="d0407-537">Nel **configurazione della soluzione** selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="d0407-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="d0407-538">Per il Microsoft HoloLens, può risultare più semplice impostare questa opzione su *computer remoto*, in modo che non Windows con tethering al computer in uso.</span><span class="sxs-lookup"><span data-stu-id="d0407-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="d0407-539">Tuttavia, è necessario inoltre eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0407-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="d0407-540">Conoscere il **indirizzo IP** di HoloLens, il che può trovarsi all'interno di *Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo è consigliabile usare.</span><span class="sxs-lookup"><span data-stu-id="d0407-540">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="d0407-541">Assicurarsi **modalità sviluppatore** viene **sul**; è stata trovata nel *Impostazioni > aggiornamento e sicurezza > per gli sviluppatori*.</span><span class="sxs-lookup"><span data-stu-id="d0407-541">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![distribuire soluzioni](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="d0407-543">Andare alla **compilare** dal menu e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.</span><span class="sxs-lookup"><span data-stu-id="d0407-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="d0407-544">L'App deve ora visualizzato nell'elenco delle App installate, pronta essere avviato e testati!</span><span class="sxs-lookup"><span data-stu-id="d0407-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="d0407-545">Le funzioni di Azure e applicazione di archiviazione completata</span><span class="sxs-lookup"><span data-stu-id="d0407-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="d0407-546">Complimenti, è stata compilata un'app per realtà mista che si avvale di servizi di archiviazione di Azure sia funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0407-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="d0407-547">L'app sarà in grado di ricavare sui dati archiviati e fornire un'azione basata su tali dati.</span><span class="sxs-lookup"><span data-stu-id="d0407-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![versione finale del prodotto-fine](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="d0407-549">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="d0407-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d0407-550">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="d0407-550">Exercise 1</span></span>

<span data-ttu-id="d0407-551">Creare una seconda generazione record il cui generare un oggetto è stato creato da punto e punto.</span><span class="sxs-lookup"><span data-stu-id="d0407-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="d0407-552">Quando si carica il file di dati, riprodurre le forme a cui viene generate dal percorso di che sono state create in origine.</span><span class="sxs-lookup"><span data-stu-id="d0407-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="d0407-553">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="d0407-553">Exercise 2</span></span>

<span data-ttu-id="d0407-554">Creare un modo per riavviare l'app, anziché dover aprirlo nuovamente ogni volta.</span><span class="sxs-lookup"><span data-stu-id="d0407-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="d0407-555">**Il caricamento in background** è il luogo ideale per iniziare.</span><span class="sxs-lookup"><span data-stu-id="d0407-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="d0407-556">Dopo questa operazione, creare un modo per cancellare l'elenco archiviato in *archiviazione di Azure*, in modo che possono essere reimpostata facilmente dall'app.</span><span class="sxs-lookup"><span data-stu-id="d0407-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
