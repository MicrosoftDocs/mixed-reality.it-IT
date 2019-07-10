---
title: MR e Azure Machine learning 307-
description: Completare questo corso di informazioni su come implementare Azure Machine Learning Studio all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, machine learning, Machine Learning, machine learning studio, hololens, coinvolgenti, vr
ms.openlocfilehash: 89d9758dedb6a2389644dda887bfadf5b28f6dd2
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694547"
---
>[!NOTE]
><span data-ttu-id="5f958-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="5f958-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5f958-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="5f958-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5f958-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="5f958-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5f958-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="5f958-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5f958-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5f958-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5f958-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="5f958-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="5f958-110">MR e Azure 307: Machine Learning</span><span class="sxs-lookup"><span data-stu-id="5f958-110">MR and Azure 307: Machine learning</span></span>

![versione finale del prodotto-avvio](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="5f958-112">In questo corso, si apprenderà come aggiungere funzionalità di Machine Learning (ML) a un'applicazione di realtà mista tramite Azure Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="5f958-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="5f958-113">*Azure Machine Learning Studio* è un servizio Microsoft, che offre agli sviluppatori con un numero elevato di algoritmi di machine learning, che possono contribuire con dati di input, output, preparazione e visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="5f958-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="5f958-114">Questi componenti, è quindi possibile sviluppare un esperimento predittivo analitica, eseguire l'iterazione su di esso e utilizzarlo per il training del modello.</span><span class="sxs-lookup"><span data-stu-id="5f958-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="5f958-115">Seguire corsi di formazione, è possibile rendere il modello operativa nell'ambito del cloud di Azure, in modo che è possibile quindi assegnare punteggi ai nuovi dati.</span><span class="sxs-lookup"><span data-stu-id="5f958-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="5f958-116">Per altre informazioni, visitare il [pagina di Azure Machine Learning Studio](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="5f958-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="5f958-117">Dopo aver completato il corso, si avrà un'applicazione immersive visore VR realtà mista e sarà appreso come eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="5f958-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="5f958-118">Fornire una tabella di dati di vendita per il *Azure Machine Learning Studio* portale e la progettazione, un algoritmo per stimare le vendite future di elementi più diffusi.</span><span class="sxs-lookup"><span data-stu-id="5f958-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="5f958-119">Creare un **progetto Unity**, che può ricevere e interpretare i dati di stima dal servizio di Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="5f958-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="5f958-120">Visualizzare i dati predication visivamente all'interno di **progetto Unity**, fornendo gli elementi di vendita più diffusi su uno scaffale tramite.</span><span class="sxs-lookup"><span data-stu-id="5f958-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="5f958-121">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="5f958-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="5f958-122">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="5f958-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="5f958-123">È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5f958-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="5f958-124">Questo corso è un'esercitazione completa, che non implicano direttamente eventuali altri laboratori di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5f958-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="5f958-125">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="5f958-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5f958-126">Corso</span><span class="sxs-lookup"><span data-stu-id="5f958-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5f958-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5f958-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5f958-128"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="5f958-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="5f958-129">MR e Azure 307: Machine Learning</span><span class="sxs-lookup"><span data-stu-id="5f958-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="5f958-130">✔️</span><span class="sxs-lookup"><span data-stu-id="5f958-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5f958-131">✔️</span><span class="sxs-lookup"><span data-stu-id="5f958-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="5f958-132">Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5f958-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="5f958-133">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5f958-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="5f958-134">Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.</span><span class="sxs-lookup"><span data-stu-id="5f958-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f958-135">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5f958-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="5f958-136">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="5f958-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="5f958-137">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="5f958-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="5f958-138">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare l'articolo strumenti](install-the-tools.md), anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .</span><span class="sxs-lookup"><span data-stu-id="5f958-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="5f958-139">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="5f958-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="5f958-140">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="5f958-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="5f958-141">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="5f958-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5f958-142">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="5f958-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5f958-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="5f958-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="5f958-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5f958-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="5f958-145">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="5f958-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="5f958-146">Accesso a Internet per la configurazione di Azure e il recupero dei dati di Machine Learning</span><span class="sxs-lookup"><span data-stu-id="5f958-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="5f958-147">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="5f958-147">Before you start</span></span>

<span data-ttu-id="5f958-148">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="5f958-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="5f958-149">Capitolo 1: configurazione dell'Account di archiviazione Azure</span><span class="sxs-lookup"><span data-stu-id="5f958-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="5f958-150">Per usare l'API di traduzione di Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5f958-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="5f958-151">Accedi per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="5f958-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5f958-152">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="5f958-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="5f958-153">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="5f958-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="5f958-154">Una volta connessi, fare clic su **gli account di archiviazione** nel menu a sinistra.</span><span class="sxs-lookup"><span data-stu-id="5f958-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="5f958-156">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="5f958-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="5f958-157">Nel **gli account di archiviazione** scheda, fare clic su **Add**.</span><span class="sxs-lookup"><span data-stu-id="5f958-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="5f958-159">Nel **crea Account di archiviazione** pannello:</span><span class="sxs-lookup"><span data-stu-id="5f958-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="5f958-160">Inserire un **nome** per l'account, tenere presente questo campo accetta solo numeri e lettere minuscole.</span><span class="sxs-lookup"><span data-stu-id="5f958-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="5f958-161">Per la **modello di distribuzione** selezionate **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="5f958-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="5f958-162">Per la **tipologia Account**, selezionare **archiviazione (utilizzo generico v1)** .</span><span class="sxs-lookup"><span data-stu-id="5f958-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="5f958-163">Per la **Performance**, selezionare **Standard**.</span><span class="sxs-lookup"><span data-stu-id="5f958-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="5f958-164">Per la **replica** selezionate **Read-access-archiviazione geograficamente ridondante (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="5f958-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="5f958-165">Lasciare **trasferimento sicuro obbligatorio** come **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="5f958-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="5f958-166">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="5f958-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="5f958-167">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="5f958-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5f958-168">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="5f958-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5f958-169">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="5f958-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="5f958-170">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="5f958-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="5f958-171">Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="5f958-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5f958-172">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="5f958-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5f958-173">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="5f958-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="5f958-174">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="5f958-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="5f958-176">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="5f958-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="5f958-177">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="5f958-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="5f958-179">Capitolo 2 - Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="5f958-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="5f958-180">Usare la *Azure Machine Learning*, è necessario configurare un'istanza del servizio Machine Learning da rendere disponibili all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5f958-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="5f958-181">Nel portale di Azure, fare clic su **New** nell'angolo in alto a sinistra e cercare **dell'area di lavoro di Machine Learning Studio**, premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="5f958-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="5f958-183">La nuova pagina fornirà una descrizione del **dell'area di lavoro di Machine Learning Studio** servizio.</span><span class="sxs-lookup"><span data-stu-id="5f958-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="5f958-184">AT nella parte inferiore sinistra di questo prompt, fare clic sui **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="5f958-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="5f958-185">Dopo avere fatto clic su **Create**, verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli sulla nuova **servizio Machine Learning Studio**:</span><span class="sxs-lookup"><span data-stu-id="5f958-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="5f958-186">Inserire la posizione desiderata **nome area di lavoro** per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="5f958-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="5f958-187">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="5f958-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="5f958-188">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="5f958-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5f958-189">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="5f958-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5f958-190">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="5f958-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="5f958-191">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="5f958-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="5f958-192">Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="5f958-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5f958-193">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="5f958-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5f958-194">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="5f958-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="5f958-195">È consigliabile usare stesso gruppo di risorse usato per la creazione di archiviazione di Azure nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="5f958-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="5f958-196">Per il **account di archiviazione** fare clic su **Usa esistente**, quindi fare clic sul menu a discesa e da lì, fare clic sui **Account di archiviazione** creato nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="5f958-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="5f958-197">Selezionare un valore appropriato **piano tariffario dell'area di lavoro** alle proprie esigenze, nel menu a discesa.</span><span class="sxs-lookup"><span data-stu-id="5f958-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="5f958-198">All'interno di **piano di servizio Web** fare clic su **Create** **nuovi,** quindi inserire un nome digitandolo nel campo di testo.</span><span class="sxs-lookup"><span data-stu-id="5f958-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="5f958-199">Dal **piano di servizio Web tariffario** , selezionare il livello di prezzo di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="5f958-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="5f958-200">Un livello denominato di test di sviluppo **DEVTEST Standard** deve essere disponibile senza costi aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="5f958-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="5f958-201">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="5f958-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="5f958-202">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="5f958-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="5f958-204">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="5f958-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="5f958-205">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="5f958-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="5f958-207">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="5f958-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="5f958-209">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="5f958-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="5f958-210">Nella pagina visualizzata, sotto il **collegamenti aggiuntivi** fare clic su **avvia Machine Learning Studio**, che reindirizzerà il browser per il **Machine Learning Studio** portale.</span><span class="sxs-lookup"><span data-stu-id="5f958-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="5f958-212">Usare la **Accedi** pulsante in alto a destra o al centro, per accedere a Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="5f958-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="5f958-214">Capitolo 3 - Machine Learning Studio: Programma di installazione di set di dati</span><span class="sxs-lookup"><span data-stu-id="5f958-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="5f958-215">Analizzando i dati esistenti e quindi si prova a prevedere risultati futuri in una delle modalità di algoritmi di Machine Learning è basata sul set di dati esistente.</span><span class="sxs-lookup"><span data-stu-id="5f958-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="5f958-216">Ciò in genere significa che i dati più esistenti che si dispone, migliore sarà l'algoritmo dovrà essere eseguita prevedere risultati futuri.</span><span class="sxs-lookup"><span data-stu-id="5f958-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="5f958-217">Una tabella di esempio viene fornita all'utente, a questo corso, chiamato [ProductsTableCSV e può essere scaricato da qui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="5f958-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f958-218">Il file con estensione zip contiene sia la **ProductsTableCSV** e il **.unitypackage**, che servirà nei [capitolo 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="5f958-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="5f958-219">Questo pacchetto viene inoltre fornito all'interno di questo capitolo, anche se distinta nel file csv.</span><span class="sxs-lookup"><span data-stu-id="5f958-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="5f958-220">Questo set di dati di esempio contiene un record degli oggetti più venduti in ogni ora di ogni giorno dell'anno 2017.</span><span class="sxs-lookup"><span data-stu-id="5f958-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio: Programma di installazione di set di dati](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="5f958-222">Ad esempio, il giorno 1 del 2017, Vediamoci (ora 13), l'elemento più venduto era salt e pepper.</span><span class="sxs-lookup"><span data-stu-id="5f958-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="5f958-223">Questa tabella di esempio contiene le 9998 voci.</span><span class="sxs-lookup"><span data-stu-id="5f958-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="5f958-224">Tornando al **Machine Learning Studio** portale, e aggiunge questa tabella come una **Dataset** per il Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="5f958-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="5f958-225">Eseguire questa operazione facendo il **+ nuovo** pulsante nell'angolo inferiore sinistro della schermata.</span><span class="sxs-lookup"><span data-stu-id="5f958-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio: Programma di installazione di set di dati](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="5f958-227">Una sezione verrà visualizzata nella parte inferiore e all'interno che vi sia Pannello di navigazione a sinistra.</span><span class="sxs-lookup"><span data-stu-id="5f958-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="5f958-228">Fare clic su **set di dati**, quindi a destra di quella **dal File locale**.</span><span class="sxs-lookup"><span data-stu-id="5f958-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio: Programma di installazione di set di dati](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="5f958-230">Caricare il nuovo **set di dati** seguendo questa procedura:</span><span class="sxs-lookup"><span data-stu-id="5f958-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="5f958-231">Verrà visualizzata la finestra di caricamento, in cui è possibile **esplorare** sul disco rigido per il nuovo set di dati.</span><span class="sxs-lookup"><span data-stu-id="5f958-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio: Programma di installazione di set di dati](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="5f958-233">Una volta selezionato e di nuovo la finestra di caricamento, lasciare la casella di controllo senza tick.</span><span class="sxs-lookup"><span data-stu-id="5f958-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="5f958-234">Nel campo di testo seguente, immettere **ProductsTableCSV.csv** come nome per il set di dati (anche se deve essere aggiunto automaticamente).</span><span class="sxs-lookup"><span data-stu-id="5f958-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="5f958-235">Usando il menu a discesa per **tipo**, selezionare **Generic CSV File con un'intestazione (con estensione csv)** .</span><span class="sxs-lookup"><span data-stu-id="5f958-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="5f958-236">Premere il segno di spunta nella parte inferiore destra della finestra di caricamento, in quello **set di dati** verrà caricato.</span><span class="sxs-lookup"><span data-stu-id="5f958-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="5f958-237">Capitolo 4 - Machine Learning Studio: L'esperimento</span><span class="sxs-lookup"><span data-stu-id="5f958-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="5f958-238">Prima di poter compilare il sistema di machine learning, è necessario creare un esperimento, per convalidare la teoria sui dati.</span><span class="sxs-lookup"><span data-stu-id="5f958-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="5f958-239">Con i risultati, sarà possibile sapere se sono necessari più dati o se è presente alcuna correlazione tra i dati e un risultato possibili.</span><span class="sxs-lookup"><span data-stu-id="5f958-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="5f958-240">Per iniziare a creare un esperimento:</span><span class="sxs-lookup"><span data-stu-id="5f958-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="5f958-241">Fare clic nuovamente sul **+ nuovo** sulla sinistra nella parte inferiore della pagina e quindi fare clic su **esperimento** > **esperimento vuoto**.</span><span class="sxs-lookup"><span data-stu-id="5f958-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="5f958-243">Verrà visualizzata una nuova pagina con un esperimento vuoto:</span><span class="sxs-lookup"><span data-stu-id="5f958-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="5f958-244">Nel pannello a sinistra espandere **Saved Datasets** > **My Datasets** e trascinare il **ProductsTableCSV** al **area di disegno esperimento**.</span><span class="sxs-lookup"><span data-stu-id="5f958-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="5f958-246">Nel pannello a sinistra, espandere **Data Transformation** > **Sample and Split**.</span><span class="sxs-lookup"><span data-stu-id="5f958-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="5f958-247">Trascinare quindi il **Split Data** elemento per il **area di disegno esperimento**.</span><span class="sxs-lookup"><span data-stu-id="5f958-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="5f958-248">L'elemento di suddivisione dei dati verrà suddiviso il set di dati in due parti.</span><span class="sxs-lookup"><span data-stu-id="5f958-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="5f958-249">Una parte si userà per il training di algoritmi di machine learning.</span><span class="sxs-lookup"><span data-stu-id="5f958-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="5f958-250">La seconda parte verrà utilizzata per valutare l'accuratezza dell'algoritmo generato.</span><span class="sxs-lookup"><span data-stu-id="5f958-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="5f958-252">Nel Pannello di destra (durante la suddivisione dei dati nell'area di disegno viene selezionato), modificare il **frazione di righe nel primo set di dati di output** al **0,7**.</span><span class="sxs-lookup"><span data-stu-id="5f958-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="5f958-253">Si suddivideranno i dati in due parti, la prima parte è 70% dei dati e la seconda parte sarà il restante 30%.</span><span class="sxs-lookup"><span data-stu-id="5f958-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="5f958-254">Per garantire che i dati vengono suddivisi in modo casuale, verificare che il **suddivisione casuale** casella di controllo rimanga selezionata.</span><span class="sxs-lookup"><span data-stu-id="5f958-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="5f958-256">Trascinare una connessione dalla base del **ProductsTableCSV** elemento nell'area di disegno nella parte superiore dell'elemento di dati di divisione.</span><span class="sxs-lookup"><span data-stu-id="5f958-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="5f958-257">Ciò si connetterà gli elementi e inviare il **ProductsTableCSV** output di set di dati (dati) della suddivisione dei dati di input.</span><span class="sxs-lookup"><span data-stu-id="5f958-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="5f958-259">Nel **esperimenti** pannello sul lato sinistro, espandere **Machine Learning** > **Train**.</span><span class="sxs-lookup"><span data-stu-id="5f958-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="5f958-260">Trascinare il **Train Model** elemento indietro nell'area di disegno dell'esperimento.</span><span class="sxs-lookup"><span data-stu-id="5f958-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="5f958-261">Area di disegno deve avere lo stesso aspetto come di seguito.</span><span class="sxs-lookup"><span data-stu-id="5f958-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="5f958-263">Dal ***in basso a sinistra*** delle **Split Data** elemento trascinare una connessione al **in alto a destra** del **Train Model** elemento.</span><span class="sxs-lookup"><span data-stu-id="5f958-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="5f958-264">La prima divisione 70% del set di dati userà il modello di training per eseguire il training dell'algoritmo.</span><span class="sxs-lookup"><span data-stu-id="5f958-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="5f958-266">Selezionare il **Train Model** elemento nell'area di disegno e nel **proprietà** fare clic su pannello (sul lato destro della finestra del browser) il **Avvia selettore di colonna** pulsante.</span><span class="sxs-lookup"><span data-stu-id="5f958-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="5f958-267">Nella casella di testo digitare **prodotto** e quindi premere **invio**, *prodotto* verrà impostato come una colonna per il training di stime.</span><span class="sxs-lookup"><span data-stu-id="5f958-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="5f958-268">In seguito, fare clic sui **segni di graduazione** nell'angolo in basso a destra per chiudere la finestra di dialogo di selezione.</span><span class="sxs-lookup"><span data-stu-id="5f958-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="5f958-270">Si intende eseguire il training di un **Multiclass Logistic Regression** algoritmo per stimare i più venduti **prodotto** in base all'ora del giorno e la data.</span><span class="sxs-lookup"><span data-stu-id="5f958-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="5f958-271">È oltre l'ambito di questo documento illustrano in dettaglio i diversi algoritmi disponibili in Azure Machine Learning studio, tuttavia, è possibile trovare informazioni dal [foglio informativo di algoritmi di Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="5f958-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="5f958-272">Nel pannello elementi esperimento a sinistra, espandere **Machine Learning** > **modello di inizializzazione** > **classificazione**, trascinare il  **Regressione logistica multiclasse** elemento all'area di disegno dell'esperimento.</span><span class="sxs-lookup"><span data-stu-id="5f958-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="5f958-273">Connettere l'output, dal livello inferiore di **Multiclass Logistic Regression**, all'input dell'angolo superiore sinistro il **Train Model** elemento.</span><span class="sxs-lookup"><span data-stu-id="5f958-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="5f958-275">Nell'elenco di elementi di esperimento nel pannello a sinistra, espandere **Machine Learning** > **punteggio**, trascinare il **Score Model** elemento nell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="5f958-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="5f958-276">Connettere l'output, dal livello inferiore di **Train Model**, all'input dell'angolo superiore sinistro il **Score Model**.</span><span class="sxs-lookup"><span data-stu-id="5f958-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="5f958-277">Connettere l'output in basso a destra **Split Data**, l'input superiore destro del **Score Model** elemento.</span><span class="sxs-lookup"><span data-stu-id="5f958-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="5f958-279">Nell'elenco degli **esperimento** gli elementi del pannello a sinistra, espandere **Machine Learning** > **Evaluate**e trascinare il **Evaluate Model** elemento nell'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="5f958-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="5f958-280">Connettere l'output dal **Score Model** all'input dell'angolo superiore sinistro il **Evaluate Model**.</span><span class="sxs-lookup"><span data-stu-id="5f958-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="5f958-282">Aver creato il primo esperimento di Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="5f958-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="5f958-283">È ora possibile salvare ed eseguire l'esperimento.</span><span class="sxs-lookup"><span data-stu-id="5f958-283">You can now save and run the experiment.</span></span> <span data-ttu-id="5f958-284">Nel menu nella parte inferiore della pagina, fare clic sui **salvare** per salvare l'esperimento e quindi fare clic su **eseguire** all'inizio dell'esperimento.</span><span class="sxs-lookup"><span data-stu-id="5f958-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="5f958-286">È possibile vedere le **stato** dell'esperimento in alto a destra dell'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="5f958-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="5f958-287">Attendere alcuni istanti per l'esperimento terminare.</span><span class="sxs-lookup"><span data-stu-id="5f958-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="5f958-288">Se si dispone di un set di dati di grandi dimensioni (reali) è probabile che l'esperimento può richiedere ore per l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="5f958-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="5f958-290">Fare clic con il pulsante destro sul **Evaluate Model** nell'area di disegno e gli articoli dal passaggio del mouse menu di scelta rapida del mouse su **i risultati della valutazione**, quindi selezionare **Visualize**.</span><span class="sxs-lookup"><span data-stu-id="5f958-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="5f958-292">Verrà visualizzati i risultati della valutazione che mostra i risultati stimati e i risultati effettivi.</span><span class="sxs-lookup"><span data-stu-id="5f958-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="5f958-293">Questo metodo utilizza il 30% del set di dati originale, che è stata suddivisa in precedenza, per valutare il modello.</span><span class="sxs-lookup"><span data-stu-id="5f958-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="5f958-294">È possibile visualizzare che i risultati non sono eccezionali, che idealmente sarebbe necessario il numero più alto in ogni riga di essere l'elemento evidenziato nelle colonne.</span><span class="sxs-lookup"><span data-stu-id="5f958-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="5f958-296">Chiudi il **risultati**.</span><span class="sxs-lookup"><span data-stu-id="5f958-296">Close the **Results**.</span></span>

24. <span data-ttu-id="5f958-297">Per usare il modello appena sottoposto a training di Machine Learning è necessario esporre come un **servizio Web**.</span><span class="sxs-lookup"><span data-stu-id="5f958-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="5f958-298">A tale scopo, fare clic sui **Set Up Web Service** dal menu di elemento nel menu nella parte inferiore della pagina e fare clic su **servizio Web predittivo**.</span><span class="sxs-lookup"><span data-stu-id="5f958-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="5f958-300">Verrà creata una nuova scheda e il modello di training uniti per creare il nuovo servizio web.</span><span class="sxs-lookup"><span data-stu-id="5f958-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="5f958-301">Nel menu nella parte inferiore della pagina fare clic su **salvare**, quindi fare clic su **eseguire**.</span><span class="sxs-lookup"><span data-stu-id="5f958-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="5f958-302">Verrà visualizzato lo stato aggiornato nell'angolo superiore destro dell'area di disegno dell'esperimento.</span><span class="sxs-lookup"><span data-stu-id="5f958-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="5f958-304">Al termine dell'esecuzione, una **Distribuisci servizio Web** pulsante verrà visualizzato nella parte inferiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="5f958-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="5f958-305">Si è pronti per distribuire il servizio web.</span><span class="sxs-lookup"><span data-stu-id="5f958-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="5f958-306">Fare clic su **Distribuisci servizio Web** (classico) nel menu nella parte inferiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="5f958-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="5f958-308">Il browser può richiedere per consentire un messaggio popup, dovrebbe **consentire**, anche se potrebbe essere necessario premere **Distribuisci servizio Web** anche in questo caso, se non viene visualizzata la pagina di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="5f958-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="5f958-309">Dopo aver creato l'esperimento si verrà reindirizzati a un **Dashboard** pagina in cui si avrà la **chiave API** visualizzato.</span><span class="sxs-lookup"><span data-stu-id="5f958-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="5f958-310">Copiarlo in un blocco note per il momento, sarà necessario nel codice molto presto.</span><span class="sxs-lookup"><span data-stu-id="5f958-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="5f958-311">Una volta che si sia preso nota prima la chiave API, fare clic sul **REQUEST/RESPONSE** pulsante il **Endpoint predefinito** sezione sotto la chiave.</span><span class="sxs-lookup"><span data-stu-id="5f958-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="5f958-313">Se si fa clic sul Test in questa pagina, sarà possibile immettere i dati di input e visualizzare l'output.</span><span class="sxs-lookup"><span data-stu-id="5f958-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="5f958-314">Immettere il **giorno** e **ora**.</span><span class="sxs-lookup"><span data-stu-id="5f958-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="5f958-315">Lasciare il **prodotto** voce vuota.</span><span class="sxs-lookup"><span data-stu-id="5f958-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="5f958-316">Scegliere il **Confirm** pulsante.</span><span class="sxs-lookup"><span data-stu-id="5f958-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="5f958-317">L'output nella parte inferiore della pagina verrà visualizzato il codice JSON che rappresenta la probabilità di ogni prodotto in corso la scelta.</span><span class="sxs-lookup"><span data-stu-id="5f958-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="5f958-318">Una nuova pagina web verrà aperta, visualizzare le istruzioni e alcuni esempi sulla struttura richiesta richiesti da Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="5f958-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="5f958-319">Copia il **URI della richiesta** visualizzato in questa pagina, nel blocco note.</span><span class="sxs-lookup"><span data-stu-id="5f958-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="5f958-321">È stato compilato un sistema di machine learning che fornisce il prodotto più probabilmente verranno venduti basato sui dati cronologici di acquisti, in correlazione con l'ora del giorno e giorno dell'anno.</span><span class="sxs-lookup"><span data-stu-id="5f958-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="5f958-322">Per chiamare il servizio web, è necessario l'URL per l'endpoint di servizio e una chiave API per il servizio.</span><span class="sxs-lookup"><span data-stu-id="5f958-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="5f958-323">Fare clic sui **Consume** scheda, dal menu in alto.</span><span class="sxs-lookup"><span data-stu-id="5f958-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="5f958-324">Il **consumo** informazioni pagina visualizzerà le informazioni necessarie chiamare il servizio web dal codice.</span><span class="sxs-lookup"><span data-stu-id="5f958-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="5f958-325">Richiedere una copia di **chiave primaria** e il **richiesta-risposta** URL.</span><span class="sxs-lookup"><span data-stu-id="5f958-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="5f958-326">Sono necessari questi elementi nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="5f958-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="5f958-327">Capitolo 5 - configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="5f958-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="5f958-328">Configurare e testare il visore VR Immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="5f958-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="5f958-329">Verrà **non** richiedono controller di movimento a questo corso.</span><span class="sxs-lookup"><span data-stu-id="5f958-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="5f958-330">Se è necessario il supporto di configurazione di visore VR Immersivi, fai clic [qui](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="5f958-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="5f958-331">Aprire **Unity** e creare un nuovo progetto Unity chiamato **MR\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="5f958-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="5f958-332">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="5f958-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="5f958-333">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5f958-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="5f958-334">Passare a **Edit** > **preferenze** e quindi dalla nuova finestra, passare al **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="5f958-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="5f958-335">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="5f958-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="5f958-336">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="5f958-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="5f958-337">Passare quindi ad **File** > **Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic su di ***commutatore piattaforma***  pulsante.</span><span class="sxs-lookup"><span data-stu-id="5f958-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="5f958-338">Assicurarsi anche che:</span><span class="sxs-lookup"><span data-stu-id="5f958-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="5f958-339">**Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="5f958-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="5f958-340">Per il Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="5f958-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="5f958-341">**Tipo di compilazione** è impostata su **D3D**.</span><span class="sxs-lookup"><span data-stu-id="5f958-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="5f958-342">**SDK** è impostata su **installata più recente**.</span><span class="sxs-lookup"><span data-stu-id="5f958-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="5f958-343">**Versione di Visual Studio** è impostata su **installata più recente**.</span><span class="sxs-lookup"><span data-stu-id="5f958-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="5f958-344">**Compilare ed eseguire** è impostata su **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="5f958-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="5f958-345">Non è necessario configurare **scene** subito, come i Broker sono forniti in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="5f958-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="5f958-346">Le impostazioni rimanenti devono essere lasciate come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="5f958-346">The remaining settings should be left as default for now.</span></span>

        ![Impostazione del progetto Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="5f958-348">Nel **Build Settings** finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il **Inspector** si trova.</span><span class="sxs-lookup"><span data-stu-id="5f958-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="5f958-349">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="5f958-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="5f958-350">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="5f958-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="5f958-351">**Scripting** **versione Runtime** deve essere **sperimentale** (.NET 4.6 equivalente)</span><span class="sxs-lookup"><span data-stu-id="5f958-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="5f958-352">**Back-end di scripting** deve essere ***.NET***</span><span class="sxs-lookup"><span data-stu-id="5f958-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="5f958-353">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="5f958-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Impostazione del progetto Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="5f958-355">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="5f958-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="5f958-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="5f958-356">**InternetClient**</span></span>

            ![Impostazione del progetto Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="5f958-358">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto</span><span class="sxs-lookup"><span data-stu-id="5f958-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Impostazione del progetto Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="5f958-360">Nuovamente in **Build Settings** *Unity C#*  progetti non sono più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="5f958-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="5f958-361">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="5f958-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="5f958-362">Salvare il progetto (**FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="5f958-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="5f958-363">Capitolo 6: importazione del pacchetto Unity MLProducts</span><span class="sxs-lookup"><span data-stu-id="5f958-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="5f958-364">A questo corso, è necessario scaricare un pacchetto di Asset Unity chiamato [ **Azure-SIG-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="5f958-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="5f958-365">Questo pacchetto è dotato di una scena, con tutti gli oggetti che predefiniti, per consentirti di concentrarti su come ottenere tutto funzioni.</span><span class="sxs-lookup"><span data-stu-id="5f958-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="5f958-366">Il **ShelfKeeper** viene fornito uno script, anche se contiene solo le variabili pubbliche, allo scopo di struttura di configurazione di scena.</span><span class="sxs-lookup"><span data-stu-id="5f958-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="5f958-367">È necessario eseguire tutte le altre sezioni.</span><span class="sxs-lookup"><span data-stu-id="5f958-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="5f958-368">Per importare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="5f958-368">To import this package:</span></span>

1.  <span data-ttu-id="5f958-369">Con il dashboard di Unity fronte, fare clic su **Assets** nel menu nella parte superiore della schermata, quindi fare clic su **Import Package, pacchetto personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="5f958-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="5f958-371">Usare il selettore file per selezionare i **Azure-SIG-307.unitypackage** del pacchetto e fare clic su **Open**.</span><span class="sxs-lookup"><span data-stu-id="5f958-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="5f958-372">Verrà visualizzato un elenco di componenti per questo asset all'utente.</span><span class="sxs-lookup"><span data-stu-id="5f958-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="5f958-373">Confermare l'importazione facendo **importare**.</span><span class="sxs-lookup"><span data-stu-id="5f958-373">Confirm the import by clicking **Import**.</span></span>

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="5f958-375">Una volta completato l'importazione, si noterà che alcune nuove cartelle visualizzate nel tuo gioco **pannello progetto**.</span><span class="sxs-lookup"><span data-stu-id="5f958-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="5f958-376">Questi sono i modelli 3D e i rispettivi materiali che fanno parte della scena già pronto che verranno usati.</span><span class="sxs-lookup"><span data-stu-id="5f958-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="5f958-377">Si scriverà la maggior parte del codice in questo corso.</span><span class="sxs-lookup"><span data-stu-id="5f958-377">You will write the majority of the code in this course.</span></span>

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="5f958-379">All'interno di **pannello progetto** cartella, fare clic sul **scene** cartella e fare doppio clic sulla scena all'interno di (denominata **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="5f958-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="5f958-380">Verrà aperta la scena (vedere la figura seguente).</span><span class="sxs-lookup"><span data-stu-id="5f958-380">The scene will open (see image below).</span></span> <span data-ttu-id="5f958-381">Se mancano i rombi rosso, è sufficiente fare clic sul **Gizmo** pulsante, nella parte superiore destra del **Pannello di gioco**.</span><span class="sxs-lookup"><span data-stu-id="5f958-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="5f958-383">Capitolo 7 - controllare le DLL in Unity</span><span class="sxs-lookup"><span data-stu-id="5f958-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="5f958-384">Per sfruttare l'uso delle librerie JSON (utilizzato per serializzare e deserializzare), è stata implementata con il pacchetto in che è stata avviata una DLL Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="5f958-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="5f958-385">La libreria deve avere la configurazione corretta, anche se è opportuno verificare (in particolare se si verificano problemi con il codice non funziona).</span><span class="sxs-lookup"><span data-stu-id="5f958-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="5f958-386">A tale scopo:</span><span class="sxs-lookup"><span data-stu-id="5f958-386">To do so:</span></span>

-  <span data-ttu-id="5f958-387">Fare clic sul file Newtonsoft all'interno della cartella Plugins ed esaminare i **Pannello di controllo**.</span><span class="sxs-lookup"><span data-stu-id="5f958-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="5f958-388">Assicurarsi che **piattaforma Any** sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="5f958-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="5f958-389">Andare alla **scheda UWP** e verificare inoltre **non elabora** sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="5f958-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![L'importazione di DLL in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="5f958-391">Capitolo 8 - creare la classe ShelfKeeper</span><span class="sxs-lookup"><span data-stu-id="5f958-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="5f958-392">Il **ShelfKeeper** classe ne ospita i metodi che consentono di controllare l'interfaccia utente e i prodotti generati nella scena.</span><span class="sxs-lookup"><span data-stu-id="5f958-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="5f958-393">Come parte del pacchetto importato, si verrà assegnato questa classe, anche se è incompleta.</span><span class="sxs-lookup"><span data-stu-id="5f958-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="5f958-394">È giunto il momento per completare tale classe:</span><span class="sxs-lookup"><span data-stu-id="5f958-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="5f958-395">Fare doppio clic sul **ShelfKeeper** uno script, all'interno di **script** cartella, aprirlo con **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="5f958-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="5f958-396">Sostituire tutto il codice esistente nello script con il codice seguente, che imposta la data e ora e ha un metodo per la visualizzazione di un prodotto.</span><span class="sxs-lookup"><span data-stu-id="5f958-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="5f958-397">Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.</span><span class="sxs-lookup"><span data-stu-id="5f958-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="5f958-398">Indietro nell'Editor di Unity, verificare che il **ShelfKeeper** classe simile di seguito:</span><span class="sxs-lookup"><span data-stu-id="5f958-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Creare la classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="5f958-400">Se lo script non ha le destinazioni di riferimento (vale a dire *data (testo Mesh)* ), è sufficiente trascinare gli oggetti corrispondenti dalle **gerarchia pannello**, nei campi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="5f958-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="5f958-401">Vedere di seguito per una descrizione, se necessario:</span><span class="sxs-lookup"><span data-stu-id="5f958-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="5f958-402">Aprire il **punto Spawn** all'interno della matrice il **ShelfKeeper** per mouse lo script di componente.</span><span class="sxs-lookup"><span data-stu-id="5f958-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="5f958-403">Una sottosezione apparirà chiamata **dimensioni**, che indica la dimensione della matrice.</span><span class="sxs-lookup"><span data-stu-id="5f958-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="5f958-404">Tipo **3** nella casella di controllo accanto a **Size** , quindi premere **invio**, e verrà creato di sotto di tre slot.</span><span class="sxs-lookup"><span data-stu-id="5f958-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="5f958-405">All'interno di **gerarchia** espandere il **visualizzazione cronologica** oggetto (di mouse sulla freccia accanto a esso).</span><span class="sxs-lookup"><span data-stu-id="5f958-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="5f958-406">Successivamente fare clic sul ***Main Camera*** dall'interno la **gerarchia**, in modo che il **Inspector** Mostra le relative informazioni.</span><span class="sxs-lookup"><span data-stu-id="5f958-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="5f958-407">Selezionare il **fotocamera principale** nel **gerarchia pannello**.</span><span class="sxs-lookup"><span data-stu-id="5f958-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="5f958-408">Trascinare il **data** e **ora** oggetti dal **gerarchia pannello** per il **testo data** e **testo della fase di** slot all'interno di **Inspector** del **Main Camera** nel **ShelfKeeper** componente.</span><span class="sxs-lookup"><span data-stu-id="5f958-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="5f958-409">Trascinare il **Spawn punti** dal **pannello gerarchia** (sotto la *dello scaffale dei* oggetto) per il **3** **elemento**fanno riferimento a destinazioni sotto il **Spawn punto** della matrice, come illustrato nell'immagine.</span><span class="sxs-lookup"><span data-stu-id="5f958-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Creare la classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="5f958-411">Capitolo 9 - creare la classe ProductPrediction</span><span class="sxs-lookup"><span data-stu-id="5f958-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="5f958-412">La classe successiva si intende creare è il **ProductPrediction** classe.</span><span class="sxs-lookup"><span data-stu-id="5f958-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="5f958-413">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="5f958-413">This class is responsible for:</span></span>

-   <span data-ttu-id="5f958-414">L'esecuzione di query di **servizio di Machine Learning** istanza, che fornisce la data e ora correnti.</span><span class="sxs-lookup"><span data-stu-id="5f958-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="5f958-415">Durante la deserializzazione della risposta JSON in dati utilizzabili.</span><span class="sxs-lookup"><span data-stu-id="5f958-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="5f958-416">Interpretazione dei dati, il recupero di prodotti consigliati 3.</span><span class="sxs-lookup"><span data-stu-id="5f958-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="5f958-417">Chiama il **ShelfKeeper** metodi per visualizzare i dati nella scena della classe.</span><span class="sxs-lookup"><span data-stu-id="5f958-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="5f958-418">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="5f958-418">To create this class:</span></span>

1.  <span data-ttu-id="5f958-419">Andare alla **gli script** cartella, nella **pannello progetto**.</span><span class="sxs-lookup"><span data-stu-id="5f958-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="5f958-420">Pulsante destro del mouse all'interno della cartella **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="5f958-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="5f958-421">Chiamare lo script **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="5f958-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="5f958-422">Fare doppio clic su nuova **ProductPrediction** script per aprirlo con **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="5f958-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="5f958-423">Se il **rilevate modifiche ai File** finestra di dialogo visualizzata, fare clic su \***Ricarica soluzione**.</span><span class="sxs-lookup"><span data-stu-id="5f958-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="5f958-424">Aggiungere spazi dei nomi seguenti all'inizio della classe ProductPrediction:</span><span class="sxs-lookup"><span data-stu-id="5f958-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="5f958-425">All'interno di **ProductPrediction** classe inserire i seguenti due oggetti che sono costituiti da un numero di classi annidate.</span><span class="sxs-lookup"><span data-stu-id="5f958-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="5f958-426">Queste classi vengono usate per serializzare e deserializzare il codice JSON per il servizio Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="5f958-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="5f958-427">Aggiungere quindi le variabili seguenti sopra il codice precedente (in modo che il codice JSON correlato codice è riportato alla fine dello script, tutti gli altri codice riportato di seguito e all'esterno di quelle):</span><span class="sxs-lookup"><span data-stu-id="5f958-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="5f958-428">Assicurarsi di inserire le **chiave primaria** e **endpoint di richiesta-risposta**, dal portale di Machine Learning, in questo caso le variabili.</span><span class="sxs-lookup"><span data-stu-id="5f958-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="5f958-429">Di seguito le immagini mostrano in cui si avrebbe richiesto la chiave e l'endpoint da.</span><span class="sxs-lookup"><span data-stu-id="5f958-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="5f958-432">Inserire il codice all'interno di **Start ()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="5f958-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="5f958-433">Il **Start ()** metodo viene chiamato quando inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="5f958-433">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="5f958-434">Di seguito è riportato il metodo che raccoglie la data e ora da Windows e lo converte in un formato che l'esperimento di Machine Learning è possibile usare per confrontare i dati archiviati nella tabella.</span><span class="sxs-lookup"><span data-stu-id="5f958-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="5f958-435">È possibile **eliminare** le **Update ()** metodo poiché questa classe non verrà utilizzate.</span><span class="sxs-lookup"><span data-stu-id="5f958-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="5f958-436">Aggiungere il metodo seguente che consente di comunicare la data e ora correnti per l'endpoint di Machine Learning e di ricevere una risposta in formato JSON.</span><span class="sxs-lookup"><span data-stu-id="5f958-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

            // Serialise the request
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

12. <span data-ttu-id="5f958-437">Aggiungere il metodo seguente, che è responsabile della deserializzazione della risposta JSON e comunica il risultato della deserializzazione per il **ShelfKeeper** classe.</span><span class="sxs-lookup"><span data-stu-id="5f958-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="5f958-438">Questo risultato sarà i nomi dei tre elementi stimati per la vendita al meglio alla data e ora correnti.</span><span class="sxs-lookup"><span data-stu-id="5f958-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="5f958-439">Inserire il codice seguente nel **ProductPrediction** (classe), sotto il metodo precedente.</span><span class="sxs-lookup"><span data-stu-id="5f958-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="5f958-440">Salvare **Visual Studio** e tornare alla **Unity**.</span><span class="sxs-lookup"><span data-stu-id="5f958-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="5f958-441">Trascinare il **ProductPrediction** classe script dalle **Script** cartella, nel **Main Camera** oggetto.</span><span class="sxs-lookup"><span data-stu-id="5f958-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="5f958-442">Salvare il progetto e la scena **File** > **salvare/File della scena** > **Salva progetto**.</span><span class="sxs-lookup"><span data-stu-id="5f958-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="5f958-443">Capitolo 10 - compilare la soluzione di piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="5f958-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="5f958-444">È ora possibile compilare il progetto come soluzione di piattaforma UWP, in modo che possa essere eseguita come applicazione autonoma.</span><span class="sxs-lookup"><span data-stu-id="5f958-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="5f958-445">Per compilare:</span><span class="sxs-lookup"><span data-stu-id="5f958-445">To Build:</span></span>

1.  <span data-ttu-id="5f958-446">Salvare nella scena corrente facendo clic su **File** > **salvare scene**.</span><span class="sxs-lookup"><span data-stu-id="5f958-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="5f958-447">Passare a **File** > **le impostazioni di compilazione**</span><span class="sxs-lookup"><span data-stu-id="5f958-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="5f958-448">Selezionare la casella denominata **Unity C# progetti** (questo è importante poiché ciò permette di modificare le classi dopo la compilazione è stata completata).</span><span class="sxs-lookup"><span data-stu-id="5f958-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="5f958-449">Fare clic su **aggiungere scene Open**,</span><span class="sxs-lookup"><span data-stu-id="5f958-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="5f958-450">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="5f958-450">Click **Build**.</span></span>

    ![Compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="5f958-452">Viene chiesto di selezionare la cartella in cui si desidera compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="5f958-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="5f958-453">Creare un **COMPILAZIONI** cartella e all'interno della cartella creare un'altra cartella con un nome appropriato di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="5f958-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="5f958-454">Fare clic sulla nuova cartella e quindi fare clic su **selezionare la cartella**da cui avviare la compilazione nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="5f958-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab7-55.png)

    ![Compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="5f958-457">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).</span><span class="sxs-lookup"><span data-stu-id="5f958-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="5f958-458">Capitolo 11 - distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="5f958-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="5f958-459">Per distribuire l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="5f958-459">To deploy your application:</span></span>

1.  <span data-ttu-id="5f958-460">Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5f958-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="5f958-461">Con Visual Studio aperto, è necessario ripristinare i pacchetti NuGet, che può essere eseguita tramite il pulsante destro del soluzione MachineLearningLab_Build, da Esplora soluzioni (disponibili a destra di Visual Studio) e quindi facendo clic su Ripristina pacchetti NuGet:</span><span class="sxs-lookup"><span data-stu-id="5f958-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Aggiungere i pacchetti NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="5f958-463">Selezione configurazione di soluzione **Debug**.</span><span class="sxs-lookup"><span data-stu-id="5f958-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="5f958-464">La piattaforma della soluzione, selezionare **x86**, **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="5f958-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="5f958-465">Per il Microsoft HoloLens, può risultare più semplice impostare questa opzione su *computer remoto*, in modo che non Windows con tethering al computer in uso.</span><span class="sxs-lookup"><span data-stu-id="5f958-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="5f958-466">Tuttavia, è necessario inoltre eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="5f958-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="5f958-467">Conoscere il **indirizzo IP** di HoloLens, il che può trovarsi all'interno di *Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo è consigliabile usare.</span><span class="sxs-lookup"><span data-stu-id="5f958-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="5f958-468">Assicurarsi **modalità sviluppatore** viene **sul**; è stata trovata nel *Impostazioni > aggiornamento e sicurezza > per gli sviluppatori*.</span><span class="sxs-lookup"><span data-stu-id="5f958-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Aggiungere i pacchetti NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="5f958-470">Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione al computer.</span><span class="sxs-lookup"><span data-stu-id="5f958-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="5f958-471">L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="5f958-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="5f958-472">Quando si esegue l'applicazione di realtà mista, si noterà banco di cui è stata configurata nella scena Unity e dall'inizializzazione, verranno recuperati i dati impostati all'interno di Azure.</span><span class="sxs-lookup"><span data-stu-id="5f958-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="5f958-473">Verranno deserializzati i dati all'interno dell'applicazione e verranno forniti in modo visivo, come i tre modelli sul banco di tre risultati principali per la data e ora correnti.</span><span class="sxs-lookup"><span data-stu-id="5f958-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="5f958-474">L'applicazione di Machine Learning completata</span><span class="sxs-lookup"><span data-stu-id="5f958-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="5f958-475">Complimenti, è stata compilata un'app per realtà mista che si basa su Azure Machine Learning per eseguire stime dei dati e visualizzarlo nella scena.</span><span class="sxs-lookup"><span data-stu-id="5f958-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Aggiungere i pacchetti NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="5f958-477">Esercizio</span><span class="sxs-lookup"><span data-stu-id="5f958-477">Exercise</span></span>

<span data-ttu-id="5f958-478">**Esercizio 1**</span><span class="sxs-lookup"><span data-stu-id="5f958-478">**Exercise 1**</span></span>

<span data-ttu-id="5f958-479">Sperimentare l'ordinamento dell'applicazione e visualizzare le stime di tre in basso sullo scaffale, come i dati potenzialmente sarebbe utili anche.</span><span class="sxs-lookup"><span data-stu-id="5f958-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="5f958-480">**Esercizio 2**</span><span class="sxs-lookup"><span data-stu-id="5f958-480">**Exercise 2**</span></span>

<span data-ttu-id="5f958-481">Usando **tabelle di Azure** popolare una nuova tabella con informazioni meteorologiche e creare un nuovo esperimento usando i dati.</span><span class="sxs-lookup"><span data-stu-id="5f958-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
