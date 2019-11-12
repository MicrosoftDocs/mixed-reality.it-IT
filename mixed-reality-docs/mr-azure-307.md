---
title: MR e Azure 307-Machine Learning
description: Completare questo corso per apprendere come implementare Azure Machine Learning Studio all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, Machine Learning, ml, Machine Learning Studio, hololens, immersive, VR
ms.openlocfilehash: e302e287049cd746a436904c2af2bcc2b0835796
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926613"
---
>[!NOTE]
><span data-ttu-id="cda5d-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="cda5d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="cda5d-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="cda5d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="cda5d-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cda5d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="cda5d-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="cda5d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="cda5d-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cda5d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="cda5d-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="cda5d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="cda5d-110">MR e Azure 307: Machine Learning</span><span class="sxs-lookup"><span data-stu-id="cda5d-110">MR and Azure 307: Machine learning</span></span>

![prodotto finale-inizio](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="cda5d-112">In questo corso si apprenderà come aggiungere le funzionalità di Machine Learning (ML) a un'applicazione di realtà mista usando Azure Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="cda5d-113">*Azure Machine Learning Studio* è un servizio Microsoft, che fornisce agli sviluppatori un numero elevato di algoritmi di Machine Learning, che possono essere utili per l'input, l'output, la preparazione e la visualizzazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="cda5d-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="cda5d-114">Da questi componenti è quindi possibile sviluppare un esperimento di analisi predittiva, eseguirne l'iterazione e usarlo per il training del modello.</span><span class="sxs-lookup"><span data-stu-id="cda5d-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="cda5d-115">Seguendo il training, è possibile rendere operativo il modello all'interno del cloud di Azure, in modo da poter assegnare un punteggio ai nuovi dati.</span><span class="sxs-lookup"><span data-stu-id="cda5d-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="cda5d-116">Per ulteriori informazioni, visitare la [pagina Azure Machine Learning Studio](https://azure.microsoft.com/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="cda5d-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="cda5d-117">Dopo aver completato questo corso, si disporrà di un'applicazione con cuffie immersive di realtà mista e si avrà appreso come eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="cda5d-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="cda5d-118">Fornire una tabella di dati di vendita al portale di *Azure Machine Learning Studio* e progettare un algoritmo per stimare le vendite future degli elementi più diffusi.</span><span class="sxs-lookup"><span data-stu-id="cda5d-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="cda5d-119">Creare un **progetto Unity**, che può ricevere e interpretare i dati di stima dal servizio ml.</span><span class="sxs-lookup"><span data-stu-id="cda5d-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="cda5d-120">Visualizza i dati di predicazione nel **progetto Unity**, fornendo gli elementi di vendita più diffusi, in uno scaffale.</span><span class="sxs-lookup"><span data-stu-id="cda5d-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="cda5d-121">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="cda5d-122">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="cda5d-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="cda5d-123">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="cda5d-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="cda5d-124">Questo corso è un'esercitazione autonoma, che non implica direttamente altri laboratori di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="cda5d-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="cda5d-125">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="cda5d-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="cda5d-126">Corso</span><span class="sxs-lookup"><span data-stu-id="cda5d-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="cda5d-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="cda5d-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="cda5d-128"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="cda5d-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="cda5d-129">MR e Azure 307: Machine Learning</span><span class="sxs-lookup"><span data-stu-id="cda5d-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="cda5d-130">✔️</span><span class="sxs-lookup"><span data-stu-id="cda5d-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="cda5d-131">✔️</span><span class="sxs-lookup"><span data-stu-id="cda5d-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="cda5d-132">Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cda5d-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="cda5d-133">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cda5d-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="cda5d-134">Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.</span><span class="sxs-lookup"><span data-stu-id="cda5d-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cda5d-135">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="cda5d-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="cda5d-136">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="cda5d-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="cda5d-137">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="cda5d-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="cda5d-138">È possibile utilizzare il software più recente, come indicato nell' [articolo installare gli strumenti](install-the-tools.md), ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="cda5d-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="cda5d-139">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="cda5d-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="cda5d-140">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="cda5d-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="cda5d-141">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="cda5d-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="cda5d-142">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="cda5d-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="cda5d-143">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="cda5d-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="cda5d-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="cda5d-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="cda5d-145">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="cda5d-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="cda5d-146">Accesso a Internet per l'installazione di Azure e il recupero dei dati ML</span><span class="sxs-lookup"><span data-stu-id="cda5d-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="cda5d-147">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="cda5d-147">Before you start</span></span>

<span data-ttu-id="cda5d-148">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="cda5d-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="cda5d-149">Capitolo 1-configurazione dell'account di archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="cda5d-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="cda5d-150">Per usare l'API di Azure translator, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="cda5d-151">Accedere al portale di [Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="cda5d-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="cda5d-152">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="cda5d-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="cda5d-153">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="cda5d-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="cda5d-154">Una volta effettuato l'accesso, fare clic su **account di archiviazione** nel menu a sinistra.</span><span class="sxs-lookup"><span data-stu-id="cda5d-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="cda5d-156">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="cda5d-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="cda5d-157">Nella scheda **account di archiviazione** fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="cda5d-159">Nel pannello **Crea account di archiviazione** :</span><span class="sxs-lookup"><span data-stu-id="cda5d-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="cda5d-160">Inserire un **nome** per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.</span><span class="sxs-lookup"><span data-stu-id="cda5d-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="cda5d-161">Per **modello di distribuzione** selezionare **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="cda5d-162">Per **tipo di account**selezionare **archiviazione (utilizzo generico V1)** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="cda5d-163">Per **prestazioni**, selezionare **standard**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="cda5d-164">Per la **replica** selezionare **l'archiviazione con ridondanza geografica e accesso in lettura (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="cda5d-165">Lasciare il **trasferimento sicuro necessario** come **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="cda5d-166">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="cda5d-167">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="cda5d-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="cda5d-168">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="cda5d-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="cda5d-169">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="cda5d-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="cda5d-170">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="cda5d-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="cda5d-171">Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="cda5d-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="cda5d-172">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="cda5d-173">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="cda5d-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="cda5d-174">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="cda5d-176">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="cda5d-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="cda5d-177">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="cda5d-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="cda5d-179">Capitolo 2: il Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="cda5d-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="cda5d-180">Per usare la *Azure Machine Learning*, è necessario configurare un'istanza del servizio Machine Learning da rendere disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="cda5d-181">Nel portale di Azure fare clic su **nuovo** nell'angolo in alto a sinistra e cercare **Machine Learning Studio area di lavoro**, quindi premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="cda5d-183">La nuova pagina fornirà una descrizione del servizio **Machine Learning Studio area di lavoro** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="cda5d-184">Nella parte inferiore sinistra del prompt, fare clic sul pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="cda5d-185">Una volta fatto clic su **Crea**, verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli sul nuovo **servizio Machine Learning Studio**:</span><span class="sxs-lookup"><span data-stu-id="cda5d-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="cda5d-186">Inserire il **nome dell'area di lavoro** desiderato per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="cda5d-187">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="cda5d-188">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="cda5d-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="cda5d-189">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="cda5d-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="cda5d-190">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="cda5d-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="cda5d-191">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="cda5d-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="cda5d-192">Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="cda5d-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="cda5d-193">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="cda5d-194">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="cda5d-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="cda5d-195">È necessario usare lo stesso gruppo di risorse usato per la creazione di archiviazione di Azure nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="cda5d-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="cda5d-196">Per la sezione **account di archiviazione** , fare clic su **Usa esistente**, quindi fare clic sul menu a discesa e fare clic sull' **account di archiviazione** creato nell'ultimo capitolo.</span><span class="sxs-lookup"><span data-stu-id="cda5d-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="cda5d-197">Selezionare il piano **tariffario dell'area di lavoro** appropriato dal menu a discesa.</span><span class="sxs-lookup"><span data-stu-id="cda5d-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="cda5d-198">Nella sezione **piano di servizio Web** fare clic su **Crea** **nuovo e** quindi inserire un nome per il campo nel campo di testo.</span><span class="sxs-lookup"><span data-stu-id="cda5d-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="cda5d-199">Nella sezione **piano tariffario del piano di servizio Web** selezionare il piano tariffario scelto.</span><span class="sxs-lookup"><span data-stu-id="cda5d-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="cda5d-200">Un livello di test di sviluppo denominato **DEVTEST standard** dovrebbe essere disponibile gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="cda5d-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="cda5d-201">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="cda5d-202">Fai clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="cda5d-204">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="cda5d-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="cda5d-205">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="cda5d-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="cda5d-207">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="cda5d-209">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="cda5d-210">Nella sezione **collegamenti aggiuntivi** della pagina visualizzata fare clic su **Avvia Machine Learning Studio**, che consente di indirizzare il browser al portale di **Machine Learning Studio** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="cda5d-212">Usare il pulsante **Sign in (accedi** ) in alto a destra o al centro per accedere al Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="cda5d-214">Capitolo 3-la Machine Learning Studio: impostazione del set di dati</span><span class="sxs-lookup"><span data-stu-id="cda5d-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="cda5d-215">Uno dei modi in cui Machine Learning gli algoritmi è l'analisi dei dati esistenti e quindi il tentativo di stimare i risultati futuri in base al set di dati esistente.</span><span class="sxs-lookup"><span data-stu-id="cda5d-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="cda5d-216">Ciò significa in genere che i dati più esistenti si presentano, migliore sarà l'algoritmo per la stima dei risultati futuri.</span><span class="sxs-lookup"><span data-stu-id="cda5d-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="cda5d-217">Viene fornita una tabella di esempio per questo corso, denominata ProductsTableCSV, che [può essere scaricata qui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="cda5d-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cda5d-218">Il file zip precedente contiene sia **ProductsTableCSV** che **file unitypackage Tools**, che sarà necessario nel [capitolo 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="cda5d-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="cda5d-219">Questo pacchetto viene fornito anche in questo capitolo, anche se separato dal file CSV.</span><span class="sxs-lookup"><span data-stu-id="cda5d-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="cda5d-220">Questo set di dati di esempio contiene un record degli oggetti più venduti ogni ora di ogni giorno dell'anno 2017.</span><span class="sxs-lookup"><span data-stu-id="cda5d-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Il Machine Learning Studio: impostazione del set di dati](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="cda5d-222">Ad esempio, il giorno 1 di 2017, alle 13.00 (ora 13), l'elemento più venduto era Salt e Pepper.</span><span class="sxs-lookup"><span data-stu-id="cda5d-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="cda5d-223">Questa tabella di esempio contiene 9998 voci.</span><span class="sxs-lookup"><span data-stu-id="cda5d-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="cda5d-224">Tornare al portale di **Machine Learning Studio** e aggiungere questa tabella come **set di dati** per ml.</span><span class="sxs-lookup"><span data-stu-id="cda5d-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="cda5d-225">A tale scopo, fare clic sul pulsante **+ nuovo** nell'angolo in basso a sinistra della schermata.</span><span class="sxs-lookup"><span data-stu-id="cda5d-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Il Machine Learning Studio: impostazione del set di dati](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="cda5d-227">Viene rilevata una sezione dalla parte inferiore e all'interno del pannello di navigazione a sinistra.</span><span class="sxs-lookup"><span data-stu-id="cda5d-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="cda5d-228">Fare clic su **set di dati**, quindi a destra di tale, **da file locale**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Il Machine Learning Studio: impostazione del set di dati](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="cda5d-230">Caricare il nuovo **set di dati** attenendosi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="cda5d-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="cda5d-231">Verrà visualizzata la finestra carica, in cui è possibile **esplorare** il disco rigido per il nuovo set di dati.</span><span class="sxs-lookup"><span data-stu-id="cda5d-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Il Machine Learning Studio: impostazione del set di dati](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="cda5d-233">Una volta selezionato e nuovamente nella finestra di caricamento, lasciare la casella di controllo non selezionata.</span><span class="sxs-lookup"><span data-stu-id="cda5d-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="cda5d-234">Nel campo di testo seguente immettere **ProductsTableCSV. csv** come nome per il set di dati, ma dovrebbe essere aggiunto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="cda5d-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="cda5d-235">Utilizzando il menu a discesa per **tipo**, selezionare **file CSV generico con un'intestazione (CSV)** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="cda5d-236">Premere il segno di selezione nella parte inferiore destra della finestra di caricamento e il **set di dati** verrà caricato.</span><span class="sxs-lookup"><span data-stu-id="cda5d-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="cda5d-237">Capitolo 4-il Machine Learning Studio: esperimento</span><span class="sxs-lookup"><span data-stu-id="cda5d-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="cda5d-238">Prima di poter compilare il sistema di Machine Learning, è necessario creare un esperimento per convalidare la teoria sui dati.</span><span class="sxs-lookup"><span data-stu-id="cda5d-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="cda5d-239">Con i risultati, sarà possibile sapere se sono necessari più dati o se non esiste alcuna correlazione tra i dati e un possibile risultato.</span><span class="sxs-lookup"><span data-stu-id="cda5d-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="cda5d-240">Per iniziare a creare un esperimento:</span><span class="sxs-lookup"><span data-stu-id="cda5d-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="cda5d-241">Fare di nuovo clic sul pulsante **+ nuovo** nella parte inferiore sinistra della pagina, quindi fare clic su **esperimento** > **esperimento vuoto**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="cda5d-243">Verrà visualizzata una nuova pagina con un esperimento vuoto:</span><span class="sxs-lookup"><span data-stu-id="cda5d-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="cda5d-244">Dal pannello a sinistra espandere set di **impostazioni salvati** > **My Datasets** e trascinare **ProductsTableCSV** sull'area di disegno dell' **esperimento**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="cda5d-246">Nel pannello a sinistra espandere **Data Transformation** > **Sample e Split**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="cda5d-247">Trascinare quindi l'elemento **Split data** nell'area di **disegno dell'esperimento**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="cda5d-248">L'elemento Split data suddividerà il set di dati in due parti.</span><span class="sxs-lookup"><span data-stu-id="cda5d-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="cda5d-249">Una parte che si userà per il training dell'algoritmo di machine learning.</span><span class="sxs-lookup"><span data-stu-id="cda5d-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="cda5d-250">La seconda parte verrà utilizzata per valutare l'accuratezza dell'algoritmo generato.</span><span class="sxs-lookup"><span data-stu-id="cda5d-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="cda5d-252">Nel pannello destro (mentre l'elemento Split data nell'area di disegno è selezionato) modificare la **frazione di righe nel primo set** di dati di output in **0,7**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="cda5d-253">I dati verranno suddivisi in due parti, la prima parte sarà pari al 70% dei dati e la seconda parte sarà il 30% rimanente.</span><span class="sxs-lookup"><span data-stu-id="cda5d-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="cda5d-254">Per assicurarsi che i dati vengano suddivisi in modo casuale, verificare che la casella di controllo **suddivisione casuale** rimanga selezionata.</span><span class="sxs-lookup"><span data-stu-id="cda5d-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="cda5d-256">Trascinare una connessione dalla base dell'elemento **ProductsTableCSV** nell'area di disegno all'inizio dell'elemento di dati divisi.</span><span class="sxs-lookup"><span data-stu-id="cda5d-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="cda5d-257">In questo modo si connetteranno gli elementi e si invierà l'output del set di dati **ProductsTableCSV** (i dati) all'input dei dati suddivisi.</span><span class="sxs-lookup"><span data-stu-id="cda5d-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="cda5d-259">Nel pannello **esperimenti** sul lato sinistro espandere **Machine Learning** > **Train**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="cda5d-260">Trascinare l'elemento **Train Model** nell'area di disegno dell'esperimento.</span><span class="sxs-lookup"><span data-stu-id="cda5d-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="cda5d-261">L'area di disegno dovrebbe avere un aspetto analogo a quello riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="cda5d-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="cda5d-263">Dalla parte ***inferiore sinistra*** dell'elemento **Split data** trascinare una connessione all' **angolo superiore destro** dell'elemento **Train Model** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="cda5d-264">La prima divisione del 70% dal set di dati verrà utilizzata dal modello Train per eseguire il training dell'algoritmo.</span><span class="sxs-lookup"><span data-stu-id="cda5d-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="cda5d-266">Selezionare l'elemento **Train Model** nell'area di disegno e nel pannello **Proprietà** (sul lato destro della finestra del browser) fare clic sul pulsante **Launch Column Selector** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="cda5d-267">Nella casella di testo digitare **Product** , quindi premere **invio**. il *prodotto* verrà impostato come colonna per eseguire il training delle stime.</span><span class="sxs-lookup"><span data-stu-id="cda5d-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="cda5d-268">A questo punto, fare clic sul **segno** di selezione nell'angolo in basso a destra per chiudere la finestra di dialogo di selezione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="cda5d-270">Si intende eseguire il training di un algoritmo di **regressione logistica multiclasse** per stimare il **prodotto** più venduto in base all'ora del giorno e alla data.</span><span class="sxs-lookup"><span data-stu-id="cda5d-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="cda5d-271">Esula dall'ambito di questo documento per spiegare i dettagli dei diversi algoritmi forniti da Azure Machine Learning Studio, tuttavia, è possibile ottenere altre informazioni dal foglio informativo sugli [algoritmi di Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="cda5d-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="cda5d-272">Dal pannello degli elementi dell'esperimento a sinistra espandere **Machine Learning** > **inizializzare il modello** > **classificazione**e trascinare l'elemento **regressione logistica multiclasse** nell'area di disegno dell'esperimento.</span><span class="sxs-lookup"><span data-stu-id="cda5d-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="cda5d-273">Connettere l'output, dalla parte inferiore della **regressione logistica multiclasse**, all'input in alto a sinistra dell'elemento del **modello Train** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="cda5d-275">Nell'elenco degli elementi dell'esperimento nel pannello a sinistra espandere **Machine Learning** > **Score**e trascinare l'elemento **Score Model** nell'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="cda5d-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="cda5d-276">Connettere l'output, dalla parte inferiore del **modello Train**, all'input superiore sinistro del **modello score**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="cda5d-277">Connettere l'output inferiore destro da **Split data**all'input superiore destro dell'elemento **Score Model** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="cda5d-279">Nell'elenco degli elementi dell' **esperimento** nel pannello a sinistra espandere **Machine Learning** > **Evaluate**e trascinare l'elemento **Evaluate Model** nell'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="cda5d-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="cda5d-280">Connettere l'output dal **modello di Punteggio** all'input superiore sinistro del **modello Evaluate**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="cda5d-282">Il primo esperimento Machine Learning è stato creato.</span><span class="sxs-lookup"><span data-stu-id="cda5d-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="cda5d-283">È ora possibile salvare ed eseguire l'esperimento.</span><span class="sxs-lookup"><span data-stu-id="cda5d-283">You can now save and run the experiment.</span></span> <span data-ttu-id="cda5d-284">Nel menu nella parte inferiore della pagina fare clic sul pulsante Save ( **Salva** ) per salvare l'esperimento e quindi fare clic su **Run (Esegui** ) per avviare l'esperimento.</span><span class="sxs-lookup"><span data-stu-id="cda5d-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="cda5d-286">È possibile visualizzare lo **stato** dell'esperimento nella parte superiore destra dell'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="cda5d-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="cda5d-287">Attendere alcuni istanti per il completamento dell'esperimento.</span><span class="sxs-lookup"><span data-stu-id="cda5d-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="cda5d-288">Se si dispone di un set di dati di grandi dimensioni (reale), è probabile che l'esecuzione dell'esperimento possa richiedere alcune ore.</span><span class="sxs-lookup"><span data-stu-id="cda5d-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="cda5d-290">Fare clic con il pulsante destro del mouse sull'elemento **Evaluate Model** nell'area di disegno e dal menu di scelta rapida posizionare il mouse sui **Risultati della valutazione**, quindi selezionare **Visualize (Visualizza**).</span><span class="sxs-lookup"><span data-stu-id="cda5d-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="cda5d-292">I risultati della valutazione verranno visualizzati mostrando i risultati stimati rispetto ai risultati effettivi.</span><span class="sxs-lookup"><span data-stu-id="cda5d-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="cda5d-293">Viene utilizzato il 30% del set di dati originale, diviso in precedenza, per la valutazione del modello.</span><span class="sxs-lookup"><span data-stu-id="cda5d-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="cda5d-294">È possibile osservare che i risultati non sono ottimali, idealmente il numero più alto in ogni riga è costituito dall'elemento evidenziato nelle colonne.</span><span class="sxs-lookup"><span data-stu-id="cda5d-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="cda5d-296">Chiudere i **risultati**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-296">Close the **Results**.</span></span>

24. <span data-ttu-id="cda5d-297">Per usare il modello di Machine Learning appena sottoposto a training, è necessario esporlo come **servizio Web**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="cda5d-298">A tale scopo, fare clic sulla voce di menu **Configura servizio Web** nel menu nella parte inferiore della pagina e fare clic su **servizio Web predittivo**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="cda5d-300">Viene creata una nuova scheda e il modello di training viene unito per creare il nuovo servizio Web.</span><span class="sxs-lookup"><span data-stu-id="cda5d-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="cda5d-301">Nel menu nella parte inferiore della pagina fare clic su **Salva**, quindi su **Esegui**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="cda5d-302">Viene visualizzato lo stato aggiornato nell'angolo superiore destro dell'area di disegno dell'esperimento.</span><span class="sxs-lookup"><span data-stu-id="cda5d-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="cda5d-304">Al termine dell'esecuzione, verrà visualizzato un pulsante **Distribuisci servizio Web** nella parte inferiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="cda5d-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="cda5d-305">Si è pronti per distribuire il servizio Web.</span><span class="sxs-lookup"><span data-stu-id="cda5d-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="cda5d-306">Fare clic su **Distribuisci servizio Web** (classico) nel menu nella parte inferiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="cda5d-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="cda5d-308">Il browser potrebbe richiedere di consentire un popup, che dovrebbe essere **consentito**, ma potrebbe essere necessario premere di nuovo **Distribuisci servizio Web** , se la pagina Distribuisci non viene visualizzata.</span><span class="sxs-lookup"><span data-stu-id="cda5d-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="cda5d-309">Una volta creato l'esperimento, si verrà reindirizzati a una pagina del **Dashboard** in cui verrà visualizzata la **chiave API** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="cda5d-310">Per il momento, copiarlo in un blocco note, sarà necessario nel codice molto presto.</span><span class="sxs-lookup"><span data-stu-id="cda5d-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="cda5d-311">Dopo aver annotato la chiave API, fare clic sul pulsante **richiesta/risposta** nella sezione **endpoint predefinito** sotto la chiave.</span><span class="sxs-lookup"><span data-stu-id="cda5d-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="cda5d-313">Se si fa clic su test in questa pagina, sarà possibile immettere i dati di input e visualizzare l'output.</span><span class="sxs-lookup"><span data-stu-id="cda5d-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="cda5d-314">Immettere il **giorno** e l' **ora**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="cda5d-315">Lasciare vuota la voce relativa al **prodotto** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="cda5d-316">Fare quindi clic sul pulsante **Confirm (conferma** ).</span><span class="sxs-lookup"><span data-stu-id="cda5d-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="cda5d-317">L'output nella parte inferiore della pagina visualizzerà il codice JSON che rappresenta la probabilità che ogni prodotto sia la scelta.</span><span class="sxs-lookup"><span data-stu-id="cda5d-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="cda5d-318">Viene visualizzata una nuova pagina Web che mostra le istruzioni e alcuni esempi sulla struttura di richiesta richiesta dal Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="cda5d-319">Copiare l' **URI della richiesta** visualizzato in questa pagina nel blocco note.</span><span class="sxs-lookup"><span data-stu-id="cda5d-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="cda5d-321">A questo punto è stato creato un sistema di Machine Learning che fornisce il prodotto più probabile da vendere in base ai dati di acquisto cronologici, correlati all'ora del giorno e al giorno dell'anno.</span><span class="sxs-lookup"><span data-stu-id="cda5d-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="cda5d-322">Per chiamare il servizio Web, è necessario l'URL per l'endpoint del servizio e una chiave API per il servizio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="cda5d-323">Fare clic sulla scheda **consume** nel menu in alto.</span><span class="sxs-lookup"><span data-stu-id="cda5d-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="cda5d-324">Nella pagina informazioni sul **consumo** vengono visualizzate le informazioni necessarie per chiamare il servizio Web dal codice.</span><span class="sxs-lookup"><span data-stu-id="cda5d-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="cda5d-325">Eseguire una copia della **chiave primaria** e dell'URL di **richiesta-risposta** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="cda5d-326">Questi sono necessari nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="cda5d-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="cda5d-327">Capitolo 5-configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="cda5d-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="cda5d-328">Configurare e testare l'auricolare immersiva della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="cda5d-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="cda5d-329">**Non** sarà necessario alcun controller di movimento per questo corso.</span><span class="sxs-lookup"><span data-stu-id="cda5d-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="cda5d-330">Per supportare la configurazione dell'auricolare immersiva, fare clic [qui](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="cda5d-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="cda5d-331">Aprire **Unity** e creare un nuovo progetto Unity denominato **Mr\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="cda5d-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="cda5d-332">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="cda5d-333">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="cda5d-334">Passare a **modifica** **Preferenze** > e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="cda5d-335">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="cda5d-336">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="cda5d-337">Passare quindi a **File** > **impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante ***Switch Platform*** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="cda5d-338">Assicurarsi inoltre che:</span><span class="sxs-lookup"><span data-stu-id="cda5d-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="cda5d-339">Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="cda5d-340">Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="cda5d-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="cda5d-341">Il **tipo di compilazione** è impostato su **D3D**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="cda5d-342">**SDK** è impostato sull' **ultima versione installata**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="cda5d-343">La **versione di Visual Studio** è impostata su **installazione più recente**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="cda5d-344">**Compilazione ed esecuzione** è impostato su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="cda5d-345">Non preoccuparti di configurare le **scene** in questo momento, perché verranno fornite in seguito.</span><span class="sxs-lookup"><span data-stu-id="cda5d-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="cda5d-346">Per il momento le impostazioni rimanenti devono essere lasciate come predefinite.</span><span class="sxs-lookup"><span data-stu-id="cda5d-346">The remaining settings should be left as default for now.</span></span>

        ![Configurazione del progetto Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="cda5d-348">Nella finestra **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="cda5d-349">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="cda5d-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="cda5d-350">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="cda5d-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="cda5d-351">La **versione di runtime** di **Scripting** deve essere **sperimentale** (equivalente a .NET 4,6)</span><span class="sxs-lookup"><span data-stu-id="cda5d-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="cda5d-352">Il **back-end di scripting** deve essere ***.NET***</span><span class="sxs-lookup"><span data-stu-id="cda5d-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="cda5d-353">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="cda5d-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurazione del progetto Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="cda5d-355">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="cda5d-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="cda5d-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="cda5d-356">**InternetClient**</span></span>

            ![Configurazione del progetto Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="cda5d-358">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Configurazione del progetto Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="cda5d-360">Nelle **impostazioni di compilazione** i progetti *Unity C#*  non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="cda5d-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="cda5d-361">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="cda5d-362">Salvare il progetto (**FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="cda5d-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="cda5d-363">Capitolo 6-importazione del pacchetto MLProducts Unity</span><span class="sxs-lookup"><span data-stu-id="cda5d-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="cda5d-364">Per questo corso, sarà necessario scaricare un pacchetto di asset Unity denominato [**Azure-Mr-307. file unitypackage Tools**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="cda5d-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="cda5d-365">Questo pacchetto viene completato con una scena, con tutti gli oggetti in che vengono precompilati, in modo da potersi concentrare sul funzionamento.</span><span class="sxs-lookup"><span data-stu-id="cda5d-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="cda5d-366">Viene fornito lo script **ShelfKeeper** , sebbene contenga solo le variabili pubbliche per lo scopo della struttura di configurazione della scena.</span><span class="sxs-lookup"><span data-stu-id="cda5d-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="cda5d-367">Sarà necessario eseguire tutte le altre sezioni.</span><span class="sxs-lookup"><span data-stu-id="cda5d-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="cda5d-368">Per importare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="cda5d-368">To import this package:</span></span>

1.  <span data-ttu-id="cda5d-369">Con il dashboard Unity davanti all'utente, fare clic su **Asset** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto, pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Importazione del pacchetto MLProducts Unity](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="cda5d-371">Usare il selettore file per selezionare il pacchetto **Azure-Mr-307. file unitypackage Tools** e fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="cda5d-372">Verrà visualizzato un elenco di componenti per questo asset.</span><span class="sxs-lookup"><span data-stu-id="cda5d-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="cda5d-373">Confermare l'importazione facendo clic su **Importa**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-373">Confirm the import by clicking **Import**.</span></span>

    ![Importazione del pacchetto MLProducts Unity](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="cda5d-375">Una volta completata l'importazione, si noterà che alcune nuove cartelle sono state visualizzate nel pannello del **progetto**Unity.</span><span class="sxs-lookup"><span data-stu-id="cda5d-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="cda5d-376">Questi sono i modelli 3D e i rispettivi materiali che fanno parte della scena preimpostata che si utilizzerà.</span><span class="sxs-lookup"><span data-stu-id="cda5d-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="cda5d-377">In questo corso verrà scritta la maggior parte del codice.</span><span class="sxs-lookup"><span data-stu-id="cda5d-377">You will write the majority of the code in this course.</span></span>

    ![Importazione del pacchetto MLProducts Unity](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="cda5d-379">Nella cartella del **Pannello del progetto** fare clic sulla cartella **Scenes** e fare doppio clic sulla scena all'interno (denominata **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="cda5d-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="cda5d-380">La scena si aprirà (vedere l'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="cda5d-380">The scene will open (see image below).</span></span> <span data-ttu-id="cda5d-381">Se i diamanti rossi sono mancanti, è sufficiente fare clic sul pulsante **gizmos (Gizmo** ) in alto a destra nel **Pannello del gioco**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Importazione del pacchetto MLProducts Unity](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="cda5d-383">Capitolo 7-controllo delle dll in Unity</span><span class="sxs-lookup"><span data-stu-id="cda5d-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="cda5d-384">Per sfruttare l'uso delle librerie JSON (usate per la serializzazione e la deserializzazione), è stata implementata una DLL Newtonsoft con il pacchetto fornito.</span><span class="sxs-lookup"><span data-stu-id="cda5d-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="cda5d-385">La libreria deve avere la configurazione corretta, sebbene valga la pena controllare (in particolare se si verificano problemi con il codice non funzionante).</span><span class="sxs-lookup"><span data-stu-id="cda5d-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="cda5d-386">A tale scopo:</span><span class="sxs-lookup"><span data-stu-id="cda5d-386">To do so:</span></span>

-  <span data-ttu-id="cda5d-387">Fare clic con il pulsante destro del mouse sul file Newtonsoft all'interno della cartella plugins ed esaminare il **pannello Inspector**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="cda5d-388">Verificare che **qualsiasi piattaforma** sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="cda5d-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="cda5d-389">Passare alla **scheda UWP** e assicurarsi che il **processo non** sia stato selezionato.</span><span class="sxs-lookup"><span data-stu-id="cda5d-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Importazione delle dll in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="cda5d-391">Capitolo 8: creare la classe ShelfKeeper</span><span class="sxs-lookup"><span data-stu-id="cda5d-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="cda5d-392">La classe **ShelfKeeper** ospita metodi che controllano l'interfaccia utente e i prodotti generati nella scena.</span><span class="sxs-lookup"><span data-stu-id="cda5d-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="cda5d-393">Come parte del pacchetto importato, si riceverà questa classe, sebbene sia incompleta.</span><span class="sxs-lookup"><span data-stu-id="cda5d-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="cda5d-394">A questo punto è necessario completare la classe:</span><span class="sxs-lookup"><span data-stu-id="cda5d-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="cda5d-395">Fare doppio clic sullo script **ShelfKeeper** , all'interno della cartella **Scripts** , per aprirlo con **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="cda5d-396">Sostituire tutto il codice esistente nello script con il codice seguente, che imposta la data e l'ora e dispone di un metodo per visualizzare un prodotto.</span><span class="sxs-lookup"><span data-stu-id="cda5d-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="cda5d-397">Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="cda5d-398">Tornare all'editor di Unity per verificare che la classe **ShelfKeeper** sia simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="cda5d-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Creazione della classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="cda5d-400">Se lo script non ha le destinazioni di riferimento (ad esempio *Data (rete di testo)* , trascinare semplicemente gli oggetti corrispondenti dal **Pannello gerarchia**nei campi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="cda5d-401">Vedere di seguito per una spiegazione, se necessario:</span><span class="sxs-lookup"><span data-stu-id="cda5d-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="cda5d-402">Per aprire la matrice di **punti di spawn** nello script del componente **ShelfKeeper** , fare clic su di essa.</span><span class="sxs-lookup"><span data-stu-id="cda5d-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="cda5d-403">Verrà visualizzata una sottosezione denominata **size**, che indica le dimensioni della matrice.</span><span class="sxs-lookup"><span data-stu-id="cda5d-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="cda5d-404">Digitare **3** nella casella di testo accanto a **size** e premere **invio**. verranno creati tre slot sotto.</span><span class="sxs-lookup"><span data-stu-id="cda5d-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="cda5d-405">All'interno della **gerarchia** espandere l'oggetto **visualizzazione dell'ora** (facendo clic con il pulsante sinistro del mouse sulla freccia accanto).</span><span class="sxs-lookup"><span data-stu-id="cda5d-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="cda5d-406">Fare quindi clic sulla ***videocamera principale*** dalla **gerarchia**, in modo che il **controllo** visualizzi le informazioni.</span><span class="sxs-lookup"><span data-stu-id="cda5d-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="cda5d-407">Selezionare la **fotocamera principale** nel **Pannello gerarchia**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="cda5d-408">Trascinare gli oggetti **Data** e **ora** dal **Pannello gerarchia** agli slot di testo **Data** e **ora** nel **controllo** della **fotocamera principale** del componente **ShelfKeeper** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="cda5d-409">Trascinare i **punti di spawn** dal **Pannello gerarchia** (sotto l'oggetto *scaffale* ) alle destinazioni di riferimento a **3** **elementi** sotto la matrice del **punto di spawn** , come illustrato nell'immagine.</span><span class="sxs-lookup"><span data-stu-id="cda5d-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Creazione della classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="cda5d-411">Capitolo 9: creare la classe ProductPrediction</span><span class="sxs-lookup"><span data-stu-id="cda5d-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="cda5d-412">La classe successiva che si intende creare è la classe **ProductPrediction** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="cda5d-413">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="cda5d-413">This class is responsible for:</span></span>

-   <span data-ttu-id="cda5d-414">Esecuzione di query sull'istanza del **servizio Machine Learning** , specificando la data e l'ora correnti.</span><span class="sxs-lookup"><span data-stu-id="cda5d-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="cda5d-415">Deserializzazione della risposta JSON in dati utilizzabili.</span><span class="sxs-lookup"><span data-stu-id="cda5d-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="cda5d-416">Interpretazione dei dati, recupero dei 3 prodotti consigliati.</span><span class="sxs-lookup"><span data-stu-id="cda5d-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="cda5d-417">Chiamare i metodi della classe **ShelfKeeper** per visualizzare i dati nella scena.</span><span class="sxs-lookup"><span data-stu-id="cda5d-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="cda5d-418">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="cda5d-418">To create this class:</span></span>

1.  <span data-ttu-id="cda5d-419">Passare alla cartella **Scripts** nel **Pannello Project**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="cda5d-420">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi **creare** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="cda5d-421">Chiamare lo script **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="cda5d-422">Fare doppio clic sul nuovo script **ProductPrediction** per aprirlo con **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="cda5d-423">Se viene visualizzata la finestra di dialogo **rilevamento modifiche file** , fare clic su \***ricarica soluzione**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="cda5d-424">Aggiungere gli spazi dei nomi seguenti all'inizio della classe ProductPrediction:</span><span class="sxs-lookup"><span data-stu-id="cda5d-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="cda5d-425">All'interno della classe **ProductPrediction** inserire i due oggetti seguenti che sono composti da un numero di classi annidate.</span><span class="sxs-lookup"><span data-stu-id="cda5d-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="cda5d-426">Queste classi vengono usate per serializzare e deserializzare il codice JSON per il servizio Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="cda5d-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="cda5d-427">Aggiungere quindi le variabili seguenti sopra il codice precedente, in modo che il codice JSON correlato si trovi nella parte inferiore dello script, sotto tutto il codice e non in linea:</span><span class="sxs-lookup"><span data-stu-id="cda5d-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="cda5d-428">Assicurarsi di inserire la **chiave primaria** e l' **endpoint richiesta-risposta**dal portale di machine learning nelle variabili qui.</span><span class="sxs-lookup"><span data-stu-id="cda5d-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="cda5d-429">Le immagini seguenti mostrano dove è stata eseguita la chiave e l'endpoint da.</span><span class="sxs-lookup"><span data-stu-id="cda5d-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="cda5d-432">Inserire questo codice all'interno del metodo **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="cda5d-433">Il metodo **Start ()** viene chiamato quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="cda5d-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="cda5d-434">Di seguito è riportato il metodo che raccoglie la data e l'ora da Windows e la converte in un formato che l'esperimento Machine Learning può utilizzare per eseguire il confronto con i dati archiviati nella tabella.</span><span class="sxs-lookup"><span data-stu-id="cda5d-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="cda5d-435">È possibile **eliminare** il metodo **Update ()** perché non verrà utilizzato da questa classe.</span><span class="sxs-lookup"><span data-stu-id="cda5d-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="cda5d-436">Aggiungere il metodo seguente che comunicherà la data e l'ora correnti all'endpoint Machine Learning e riceverà una risposta in formato JSON.</span><span class="sxs-lookup"><span data-stu-id="cda5d-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="cda5d-437">Aggiungere il metodo seguente, che è responsabile della deserializzazione della risposta JSON e della comunicazione del risultato della deserializzazione alla classe **ShelfKeeper** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="cda5d-438">Questo risultato sarà costituito dai nomi dei tre elementi stimati per la vendita del maggior numero alla data e all'ora correnti.</span><span class="sxs-lookup"><span data-stu-id="cda5d-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="cda5d-439">Inserire il codice seguente nella classe **ProductPrediction** , al di sotto del metodo precedente.</span><span class="sxs-lookup"><span data-stu-id="cda5d-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="cda5d-440">Salva **Visual Studio** e torna a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="cda5d-441">Trascinare lo script della classe **ProductPrediction** dalla cartella **script** nell'oggetto della **fotocamera principale** .</span><span class="sxs-lookup"><span data-stu-id="cda5d-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="cda5d-442">Salvare la scena e il **file** di progetto > **Salva scena/file** > **Salva progetto**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="cda5d-443">Capitolo 10: compilare la soluzione UWP</span><span class="sxs-lookup"><span data-stu-id="cda5d-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="cda5d-444">A questo punto è necessario compilare il progetto come soluzione UWP, in modo che possa essere eseguito come applicazione autonoma.</span><span class="sxs-lookup"><span data-stu-id="cda5d-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="cda5d-445">Per compilare:</span><span class="sxs-lookup"><span data-stu-id="cda5d-445">To Build:</span></span>

1.  <span data-ttu-id="cda5d-446">Salvare la scena corrente facendo clic su **File** > **Salva scene**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="cda5d-447">Vai a **File** > **impostazioni di compilazione**</span><span class="sxs-lookup"><span data-stu-id="cda5d-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="cda5d-448">Selezionare la casella denominata **progetti C# Unity** (questo aspetto è importante perché consente di modificare le classi al termine della compilazione).</span><span class="sxs-lookup"><span data-stu-id="cda5d-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="cda5d-449">Fare clic su **Aggiungi scene aperte**,</span><span class="sxs-lookup"><span data-stu-id="cda5d-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="cda5d-450">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-450">Click **Build**.</span></span>

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="cda5d-452">Verrà richiesto di selezionare la cartella in cui si vuole compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="cda5d-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="cda5d-453">Creare una cartella **compilazioni** e all'interno di tale cartella creare un'altra cartella con un nome appropriato.</span><span class="sxs-lookup"><span data-stu-id="cda5d-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="cda5d-454">Fare clic sulla nuova cartella e quindi fare clic su **Seleziona cartella**per iniziare la compilazione in quel percorso.</span><span class="sxs-lookup"><span data-stu-id="cda5d-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-55.png)

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="cda5d-457">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).</span><span class="sxs-lookup"><span data-stu-id="cda5d-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="cda5d-458">Capitolo 11-distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="cda5d-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="cda5d-459">Per distribuire l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="cda5d-459">To deploy your application:</span></span>

1.  <span data-ttu-id="cda5d-460">Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="cda5d-461">Con Visual Studio aperto è necessario ripristinare i pacchetti NuGet. a tale scopo, è possibile fare clic con il pulsante destro del mouse sulla soluzione MachineLearningLab_Build, dall'Esplora soluzioni (disponibile a destra di Visual Studio) e quindi scegliere Ripristina pacchetti NuGet:</span><span class="sxs-lookup"><span data-stu-id="cda5d-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="cda5d-463">Nella configurazione della soluzione selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="cda5d-464">Nella piattaforma soluzione selezionare **x86**, **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="cda5d-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="cda5d-465">Per Microsoft HoloLens, può risultare più semplice impostare questa impostazione su *computer remoto*, in modo da non essere collegati al computer.</span><span class="sxs-lookup"><span data-stu-id="cda5d-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="cda5d-466">Tuttavia, sarà necessario eseguire anche le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="cda5d-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="cda5d-467">Conosce l' **indirizzo IP** del HoloLens, disponibile all'interno delle *impostazioni > rete & Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare.</span><span class="sxs-lookup"><span data-stu-id="cda5d-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="cda5d-468">Verificare che la **modalità sviluppatore** sia **attiva**; disponibile in *impostazioni > aggiorna & > di sicurezza per gli sviluppatori*.</span><span class="sxs-lookup"><span data-stu-id="cda5d-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="cda5d-470">Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per SIDELOAD l'applicazione al PC.</span><span class="sxs-lookup"><span data-stu-id="cda5d-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="cda5d-471">L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="cda5d-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="cda5d-472">Quando si esegue l'applicazione di realtà mista, viene visualizzato il banco configurato nella scena Unity e, dall'inizializzazione, verranno recuperati i dati configurati in Azure.</span><span class="sxs-lookup"><span data-stu-id="cda5d-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="cda5d-473">I dati verranno deserializzati all'interno dell'applicazione e i tre risultati principali per la data e l'ora correnti verranno forniti visivamente, come tre modelli sul banco.</span><span class="sxs-lookup"><span data-stu-id="cda5d-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="cda5d-474">Applicazione Machine Learning completata</span><span class="sxs-lookup"><span data-stu-id="cda5d-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="cda5d-475">Congratulazioni, è stata creata un'app per realtà mista che sfrutta le Azure Machine Learning per eseguire stime dei dati e visualizzarle nella scena.</span><span class="sxs-lookup"><span data-stu-id="cda5d-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="cda5d-477">Esercizio</span><span class="sxs-lookup"><span data-stu-id="cda5d-477">Exercise</span></span>

<span data-ttu-id="cda5d-478">**Esercizio 1**</span><span class="sxs-lookup"><span data-stu-id="cda5d-478">**Exercise 1**</span></span>

<span data-ttu-id="cda5d-479">Provare a usare il tipo di ordinamento dell'applicazione e fare in modo che vengano visualizzate le tre stime in basso sullo scaffale, in quanto questi dati potrebbero essere utili anche.</span><span class="sxs-lookup"><span data-stu-id="cda5d-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="cda5d-480">**Esercizio 2**</span><span class="sxs-lookup"><span data-stu-id="cda5d-480">**Exercise 2**</span></span>

<span data-ttu-id="cda5d-481">Con le **tabelle di Azure** viene popolata una nuova tabella con le informazioni meteorologiche e viene creato un nuovo esperimento usando i dati.</span><span class="sxs-lookup"><span data-stu-id="cda5d-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
