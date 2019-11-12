---
title: MR e Azure 303-LUIS (Natural Language Understanding)
description: Completare questo corso per apprendere come implementare Azure Language Understanding Intelligence Service (LUIS) in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, Language Understanding Intelligence Service, Luis, hololens, immersive, VR
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926809"
---
>[!NOTE]
><span data-ttu-id="b5766-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b5766-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b5766-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="b5766-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b5766-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b5766-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b5766-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="b5766-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b5766-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b5766-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b5766-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="b5766-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="b5766-110">MR e Azure 303: LUIS (Natural Language Understanding)</span><span class="sxs-lookup"><span data-stu-id="b5766-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="b5766-111">In questo corso si apprenderà come integrare Language Understanding in un'applicazione di realtà mista usando servizi cognitivi di Azure, con il API Language Understanding.</span><span class="sxs-lookup"><span data-stu-id="b5766-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![risultato Lab](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="b5766-113">*Language Understanding (Luis)* è un servizio di Microsoft Azure, che offre alle applicazioni la possibilità di rendere il significato fuori dall'input dell'utente, ad esempio tramite l'estrazione di ciò che un utente potrebbe desiderare, nelle proprie parole.</span><span class="sxs-lookup"><span data-stu-id="b5766-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="b5766-114">Questa operazione viene eseguita tramite Machine Learning, che comprende e apprende le informazioni di input e quindi può rispondere con informazioni dettagliate, pertinenti.</span><span class="sxs-lookup"><span data-stu-id="b5766-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="b5766-115">Per ulteriori informazioni, visitare la [pagina Azure Language Understanding (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="b5766-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="b5766-116">Dopo aver completato questo corso, si disporrà di un'applicazione con un auricolare immersiva a realtà mista che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="b5766-117">Acquisire la voce di input dell'utente, usando il microfono collegato alla cuffia ad immersiva.</span><span class="sxs-lookup"><span data-stu-id="b5766-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="b5766-118">Inviare la dettatura acquisita ad *Azure Language Understanding Intelligent Service* (*Luis*).</span><span class="sxs-lookup"><span data-stu-id="b5766-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="b5766-119">Ottenere il significato di LUIS Extract dalle informazioni di invio, che verranno analizzate e verrà effettuato un tentativo di determinare lo scopo della richiesta dell'utente.</span><span class="sxs-lookup"><span data-stu-id="b5766-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="b5766-120">Lo sviluppo includerà la creazione di un'app in cui l'utente potrà usare la voce e/o lo sguardo per modificare le dimensioni e il colore degli oggetti nella scena.</span><span class="sxs-lookup"><span data-stu-id="b5766-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="b5766-121">L'uso dei controller di movimento non verrà analizzato.</span><span class="sxs-lookup"><span data-stu-id="b5766-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="b5766-122">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="b5766-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="b5766-123">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="b5766-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="b5766-124">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="b5766-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="b5766-125">Prepararsi a eseguire il training di LUIS più volte, come spiegato nel [capitolo 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="b5766-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="b5766-126">Si otterranno risultati migliori più volte che LUIS è stato sottoposto a training.</span><span class="sxs-lookup"><span data-stu-id="b5766-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="b5766-127">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="b5766-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b5766-128">Corso</span><span class="sxs-lookup"><span data-stu-id="b5766-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b5766-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b5766-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b5766-130"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="b5766-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b5766-131">MR e Azure 303: LUIS (Natural Language Understanding)</span><span class="sxs-lookup"><span data-stu-id="b5766-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="b5766-132">✔️</span><span class="sxs-lookup"><span data-stu-id="b5766-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b5766-133">✔️</span><span class="sxs-lookup"><span data-stu-id="b5766-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b5766-134">Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5766-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="b5766-135">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5766-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="b5766-136">Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.</span><span class="sxs-lookup"><span data-stu-id="b5766-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5766-137">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="b5766-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b5766-138">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="b5766-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b5766-139">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="b5766-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="b5766-140">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="b5766-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="b5766-141">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b5766-142">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="b5766-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b5766-143">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="b5766-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="b5766-144">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="b5766-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="b5766-145">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="b5766-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="b5766-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b5766-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="b5766-147">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="b5766-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b5766-148">Un set di cuffie con un microfono incorporato (se la cuffia non dispone di un MIC e di altoparlanti predefiniti)</span><span class="sxs-lookup"><span data-stu-id="b5766-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="b5766-149">Accesso a Internet per il programma di installazione di Azure e il recupero LUIS</span><span class="sxs-lookup"><span data-stu-id="b5766-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b5766-150">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="b5766-150">Before you start</span></span>

1.  <span data-ttu-id="b5766-151">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="b5766-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="b5766-152">Per consentire al computer di abilitare la dettatura, passare a **impostazioni di Windows > Privacy > vocale, Inking & digitando** e premere il pulsante **Attiva servizi vocali e digitando suggerimenti**.</span><span class="sxs-lookup"><span data-stu-id="b5766-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="b5766-153">Il codice in questa esercitazione consentirà di registrare dal set di **dispositivi del microfono predefinito** nel computer.</span><span class="sxs-lookup"><span data-stu-id="b5766-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="b5766-154">Verificare che il dispositivo microfonico predefinito sia impostato come quello che si vuole usare per acquisire la voce.</span><span class="sxs-lookup"><span data-stu-id="b5766-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="b5766-155">Se la cuffia ha un microfono incorporato, assicurarsi che l'opzione *"quando si indossa la cuffia, passa alla cuffia auricolare"* sia attivata nelle impostazioni del portale per la *realtà mista* .</span><span class="sxs-lookup"><span data-stu-id="b5766-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Configurazione dell'auricolare immersivo](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="b5766-157">Capitolo 1: configurare il portale di Azure</span><span class="sxs-lookup"><span data-stu-id="b5766-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="b5766-158">Per usare il servizio *Language Understanding* in Azure, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b5766-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="b5766-159">Accedere al portale di [Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="b5766-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b5766-160">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="b5766-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b5766-161">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="b5766-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="b5766-162">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *Language Understanding*e premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="b5766-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Crea risorsa LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="b5766-164">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="b5766-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="b5766-165">La nuova pagina a destra fornirà una descrizione del servizio Language Understanding.</span><span class="sxs-lookup"><span data-stu-id="b5766-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="b5766-166">Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="b5766-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Creazione del servizio LUIS-note legali](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="b5766-168">Una volta fatto clic su Crea:</span><span class="sxs-lookup"><span data-stu-id="b5766-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="b5766-169">Inserire il **nome** desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="b5766-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="b5766-170">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="b5766-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="b5766-171">Selezionare il piano **tariffario** appropriato. se è la prima volta che si crea un *servizio Luis*, è necessario che sia disponibile un livello gratuito (denominato F0).</span><span class="sxs-lookup"><span data-stu-id="b5766-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="b5766-172">L'allocazione gratuita dovrebbe essere più che sufficiente per questo corso.</span><span class="sxs-lookup"><span data-stu-id="b5766-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="b5766-173">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="b5766-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b5766-174">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="b5766-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b5766-175">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="b5766-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="b5766-176">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="b5766-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="b5766-177">Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="b5766-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="b5766-178">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b5766-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="b5766-179">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="b5766-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="b5766-180">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="b5766-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="b5766-181">Seleziona **Crea**.</span><span class="sxs-lookup"><span data-stu-id="b5766-181">Select **Create**.</span></span>

        ![Crea servizio LUIS-input utente](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="b5766-183">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="b5766-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="b5766-184">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="b5766-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Nuova immagine di notifica di Azure](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="b5766-186">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="b5766-186">Click on the notification to explore your new Service instance.</span></span>

    ![Notifica di creazione risorse riuscita](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="b5766-188">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="b5766-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b5766-189">Si verrà portati alla nuova istanza del servizio LUIS.</span><span class="sxs-lookup"><span data-stu-id="b5766-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Accesso alle chiavi LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="b5766-191">All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita usando la chiave di sottoscrizione del servizio.</span><span class="sxs-lookup"><span data-stu-id="b5766-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="b5766-192">Dalla pagina *avvio rapido* , del servizio *API Luis* , passare al primo passaggio, recuperare *le chiavi*e fare clic su **chiavi** . a tale scopo, fare clic sui tasti di collegamento ipertestuale blu, che si trovano nel menu di navigazione dei servizi, indicato dall'icona a forma di chiave.</span><span class="sxs-lookup"><span data-stu-id="b5766-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="b5766-193">Le *chiavi*del servizio vengono rivelate.</span><span class="sxs-lookup"><span data-stu-id="b5766-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="b5766-194">Eseguire una copia di una delle chiavi visualizzate, perché sarà necessario in un secondo momento nel progetto.</span><span class="sxs-lookup"><span data-stu-id="b5766-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="b5766-195">Nella pagina del *servizio* fare clic su *Language Understanding portale* per essere reindirizzati alla pagina Web che verrà usata per creare il nuovo servizio, all'interno dell'app Luis.</span><span class="sxs-lookup"><span data-stu-id="b5766-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="b5766-196">Capitolo 2: portale di Language Understanding</span><span class="sxs-lookup"><span data-stu-id="b5766-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="b5766-197">In questa sezione si apprenderà come creare un'app LUIS nel portale LUIS.</span><span class="sxs-lookup"><span data-stu-id="b5766-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="b5766-198">Tenere presente che la configurazione di *entità*, finalità ed *espressioni* in questo capitolo è solo il primo passaggio per la creazione del servizio Luis: è anche necessario ripetere il training del servizio, più *volte, in*modo da renderlo più accurato.</span><span class="sxs-lookup"><span data-stu-id="b5766-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="b5766-199">La ripetizione del training del servizio è trattata nell' [ultimo capitolo](#chapter-12--improving-your-luis-service) di questo corso, quindi è necessario verificarne il completamento.</span><span class="sxs-lookup"><span data-stu-id="b5766-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="b5766-200">Quando si raggiunge il *portale di Language Understanding*, potrebbe essere necessario eseguire l'accesso, se non lo si è già fatto, con le stesse credenziali del portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="b5766-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Pagina di accesso LUIS](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="b5766-202">Se è la prima volta che si usa LUIS, sarà necessario scorrere verso il basso fino alla fine della pagina iniziale per trovare e fare clic sul pulsante **create Luis app** .</span><span class="sxs-lookup"><span data-stu-id="b5766-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Pagina Crea app LUIS](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="b5766-204">Una volta effettuato l'accesso, fare clic su **app personali** (se non si è attualmente in questa sezione).</span><span class="sxs-lookup"><span data-stu-id="b5766-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="b5766-205">È quindi possibile fare clic su **Crea nuova app**.</span><span class="sxs-lookup"><span data-stu-id="b5766-205">You can then click on **Create new app**.</span></span>

    ![Immagine di LUIS-My Apps](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="b5766-207">Assegnare un *nome*all'app.</span><span class="sxs-lookup"><span data-stu-id="b5766-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="b5766-208">Se l'app dovrebbe comprendere una lingua diversa dall'inglese, è necessario modificare le *impostazioni cultura* in base alla lingua appropriata.</span><span class="sxs-lookup"><span data-stu-id="b5766-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="b5766-209">Qui è anche possibile aggiungere una *Descrizione* della nuova app Luis.</span><span class="sxs-lookup"><span data-stu-id="b5766-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-crea una nuova app](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="b5766-211">Una volta fatto clic su **fine**, si passerà alla pagina *Compila* della nuova applicazione *Luis* .</span><span class="sxs-lookup"><span data-stu-id="b5766-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="b5766-212">Ecco alcuni concetti importanti da comprendere:</span><span class="sxs-lookup"><span data-stu-id="b5766-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="b5766-213">*Intent*, rappresenta il metodo che verrà chiamato dopo una query dall'utente.</span><span class="sxs-lookup"><span data-stu-id="b5766-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="b5766-214">Una *finalità* può includere una o più *entità*.</span><span class="sxs-lookup"><span data-stu-id="b5766-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="b5766-215">*Entity*, è un componente della query che descrive le informazioni relative allo *scopo*.</span><span class="sxs-lookup"><span data-stu-id="b5766-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="b5766-216">Le *espressioni*sono esempi di query fornite dallo sviluppatore, che Luis utilizzerà per eseguire il training.</span><span class="sxs-lookup"><span data-stu-id="b5766-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="b5766-217">Se questi concetti non sono perfettamente chiari, non preoccuparti, perché in questo corso verranno chiariti più avanti in questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="b5766-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="b5766-218">Si inizierà creando le *entità* necessarie per compilare questo corso.</span><span class="sxs-lookup"><span data-stu-id="b5766-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="b5766-219">Sul lato sinistro della pagina fare clic su *entità*e quindi su **Crea nuova entità**.</span><span class="sxs-lookup"><span data-stu-id="b5766-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Crea nuova entità](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="b5766-221">Chiamare il nuovo *colore*dell'entità, impostarne il tipo su *Simple*, quindi fare clic su **done**.</span><span class="sxs-lookup"><span data-stu-id="b5766-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Crea entità-colore semplice](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="b5766-223">Ripetere questo processo per creare tre (3) entità più semplici denominate:</span><span class="sxs-lookup"><span data-stu-id="b5766-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="b5766-224">*Upsize*</span><span class="sxs-lookup"><span data-stu-id="b5766-224">*upsize*</span></span>
    -   <span data-ttu-id="b5766-225">*ridimensionare*</span><span class="sxs-lookup"><span data-stu-id="b5766-225">*downsize*</span></span>
    -   <span data-ttu-id="b5766-226">*destinazione*</span><span class="sxs-lookup"><span data-stu-id="b5766-226">*target*</span></span>

<span data-ttu-id="b5766-227">Il risultato dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="b5766-227">The result should look like the image below:</span></span>

![Risultato della creazione di entità](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="b5766-229">A questo punto è possibile iniziare la creazione di *Intent*.</span><span class="sxs-lookup"><span data-stu-id="b5766-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="b5766-230">Non eliminare la finalità **None** .</span><span class="sxs-lookup"><span data-stu-id="b5766-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="b5766-231">Sul lato sinistro della pagina fare clic su **Intent**, quindi fare clic su **Crea nuovo scopo**.</span><span class="sxs-lookup"><span data-stu-id="b5766-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Crea nuovi Intent](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="b5766-233">Chiamare la nuova *finalità* **ChangeObjectColor**.</span><span class="sxs-lookup"><span data-stu-id="b5766-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b5766-234">Questo nome di *finalità* viene usato all'interno del codice più avanti in questo corso. per ottenere risultati ottimali, usare questo nome esattamente come fornito.</span><span class="sxs-lookup"><span data-stu-id="b5766-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="b5766-235">Dopo aver confermato il nome, si verrà indirizzati alla pagina Intent.</span><span class="sxs-lookup"><span data-stu-id="b5766-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![Pagina LUIS-Intent](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="b5766-237">Si noterà che è presente una casella di testo in cui viene chiesto di digitare 5 o più *espressioni*diverse.</span><span class="sxs-lookup"><span data-stu-id="b5766-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="b5766-238">LUIS converte tutti gli enunciati in lettere minuscole.</span><span class="sxs-lookup"><span data-stu-id="b5766-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="b5766-239">Inserire l' *espressione* seguente nella casella di testo top (attualmente con il *tipo di testo circa 5 esempi...*</span><span class="sxs-lookup"><span data-stu-id="b5766-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="b5766-240">) e premere **invio**:</span><span class="sxs-lookup"><span data-stu-id="b5766-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="b5766-241">Si noterà che il nuovo *enunciato* verrà visualizzato in un elenco sottostante.</span><span class="sxs-lookup"><span data-stu-id="b5766-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="b5766-242">Seguendo lo stesso processo, inserire le sei (6) espressioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="b5766-243">Per ogni espressione creata è necessario identificare le parole che devono essere usate da LUIS come entità.</span><span class="sxs-lookup"><span data-stu-id="b5766-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="b5766-244">In questo esempio è necessario etichettare tutti i colori come entità di *colore* e il riferimento possibile a una destinazione come entità di *destinazione* .</span><span class="sxs-lookup"><span data-stu-id="b5766-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="b5766-245">A tale scopo, provare a fare clic sulla parola *Cylinder* nel primo enunciatore e selezionare *destinazione*.</span><span class="sxs-lookup"><span data-stu-id="b5766-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Identificare le destinazioni di espressione](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="b5766-247">A questo punto, fare clic sulla parola *rosso* nel primo enunciato e selezionare *colore*.</span><span class="sxs-lookup"><span data-stu-id="b5766-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Identificare le entità enunciate](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="b5766-249">Etichettare anche la riga successiva, dove *Cube* deve essere una *destinazione*e il *nero* deve essere un *colore*.</span><span class="sxs-lookup"><span data-stu-id="b5766-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="b5766-250">Si noti anche l'uso delle parole *' This '* , *' it '* e *' This object '* , che vengono fornite, in modo da rendere disponibili anche tipi di destinazione non specifici.</span><span class="sxs-lookup"><span data-stu-id="b5766-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="b5766-251">Ripetere il processo precedente fino a quando non sono presenti le entità etichettate per tutte le espressioni.</span><span class="sxs-lookup"><span data-stu-id="b5766-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="b5766-252">Se è necessaria assistenza, vedere l'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="b5766-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="b5766-253">Quando si selezionano le parole per etichettarle come entità:</span><span class="sxs-lookup"><span data-stu-id="b5766-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="b5766-254">Per le singole parole, basta fare clic su di essi.</span><span class="sxs-lookup"><span data-stu-id="b5766-254">For single words just click them.</span></span>
    > - <span data-ttu-id="b5766-255">Per un set di due o più parole, fare clic all'inizio, quindi alla fine del set.</span><span class="sxs-lookup"><span data-stu-id="b5766-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b5766-256">È possibile usare l'interruttore di *visualizzazione token* per passare dalla **visualizzazione entità/token**.</span><span class="sxs-lookup"><span data-stu-id="b5766-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="b5766-257">I risultati dovrebbero essere come illustrato nelle immagini seguenti, mostrando la **visualizzazione entità/token**:</span><span class="sxs-lookup"><span data-stu-id="b5766-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Token & viste entità](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="b5766-259">A questo punto, fare clic sul pulsante di **Train** nella parte superiore destra della pagina e attendere che il piccolo indicatore rotondo venga trasformato in verde.</span><span class="sxs-lookup"><span data-stu-id="b5766-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="b5766-260">Indica che LUIS è stato sottoposto a training per riconoscere questa finalità.</span><span class="sxs-lookup"><span data-stu-id="b5766-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Train LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="b5766-262">Come esercizio, creare una nuova finalità denominata **ChangeObjectSize**, usando la *destinazione*delle entità, le *dimensioni*e il *ridimensionamento*.</span><span class="sxs-lookup"><span data-stu-id="b5766-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="b5766-263">Seguendo lo stesso processo dell'intento precedente, inserire i seguenti otto (8) espressioni per la modifica delle *dimensioni* :</span><span class="sxs-lookup"><span data-stu-id="b5766-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="b5766-264">Il risultato dovrebbe essere simile a quello dell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="b5766-264">The result should be like the one in the image below:</span></span>

    ![Configurare i token/entità di ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="b5766-266">Una volta creati e sottoposti a training entrambi gli Intent, **ChangeObjectColor** e **ChangeObjectSize**, fare clic sul pulsante **pubblica** nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="b5766-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Pubblica servizio LUIS](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="b5766-268">Nella pagina *pubblica* verrà finalizzata e pubblicata l'app Luis in modo che possa accedere al codice.</span><span class="sxs-lookup"><span data-stu-id="b5766-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="b5766-269">Impostare la casella *di riepilogo a discesa pubblica su* come **produzione**.</span><span class="sxs-lookup"><span data-stu-id="b5766-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="b5766-270">Impostare il *fuso orario* sul fuso orario.</span><span class="sxs-lookup"><span data-stu-id="b5766-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="b5766-271">Selezionare la casella **Includi tutti i punteggi della finalità stimati**.</span><span class="sxs-lookup"><span data-stu-id="b5766-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="b5766-272">Fare clic su **pubblica in slot di produzione**.</span><span class="sxs-lookup"><span data-stu-id="b5766-272">Click on **Publish to Production Slot**.</span></span>

        ![Impostazioni di pubblicazione](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="b5766-274">Nella sezione *risorse e chiavi*:</span><span class="sxs-lookup"><span data-stu-id="b5766-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="b5766-275">Selezionare l'area impostata per l'istanza del servizio nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="b5766-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="b5766-276">Si noterà un **Starter_Key** elemento riportato di seguito, che verrà ignorato.</span><span class="sxs-lookup"><span data-stu-id="b5766-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="b5766-277">Fare clic su **Aggiungi chiave** e inserire la *chiave* ottenuta nel portale di Azure al momento della creazione dell'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="b5766-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="b5766-278">Se il portale di Azure e il portale LUIS sono connessi allo stesso utente, verranno forniti menu a discesa per *nome tenant*, *nome sottoscrizione*e *chiave* che si vuole usare (avrà lo stesso nome fornito in precedenza nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="b5766-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="b5766-279">Sotto l' *endpoint*, eseguire una copia dell'endpoint corrispondente alla chiave inserita, che verrà a breve usata nel codice.</span><span class="sxs-lookup"><span data-stu-id="b5766-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="b5766-280">Capitolo 3: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="b5766-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="b5766-281">Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="b5766-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b5766-282">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="b5766-282">Open *Unity* and click **New**.</span></span> 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="b5766-284">A questo punto è necessario specificare un nome di progetto Unity, inserendo **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="b5766-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="b5766-285">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="b5766-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="b5766-286">Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="b5766-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b5766-287">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="b5766-287">Then, click **Create project**.</span></span>

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="b5766-289">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b5766-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b5766-290">Passare a Modifica Preferenze > e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="b5766-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b5766-291">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="b5766-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b5766-292">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="b5766-292">Close the **Preferences** window.</span></span>

    ![Aggiornare la preferenza dell'editor di script.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="b5766-294">Passare quindi a **File > impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="b5766-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Finestra impostazioni di compilazione, passa alla piattaforma UWP.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="b5766-296">Passare a **File > impostazioni di compilazione** e verificare che:</span><span class="sxs-lookup"><span data-stu-id="b5766-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="b5766-297">Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="b5766-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="b5766-298">Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="b5766-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="b5766-299">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="b5766-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="b5766-300">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="b5766-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="b5766-301">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="b5766-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="b5766-302">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="b5766-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="b5766-303">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="b5766-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="b5766-304">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="b5766-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b5766-305">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="b5766-305">A save window will appear.</span></span>
        
            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="b5766-307">Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.</span><span class="sxs-lookup"><span data-stu-id="b5766-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crea nuova cartella script](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="b5766-309">Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **MR_LuisScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="b5766-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="b5766-311">Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="b5766-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="b5766-312">Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .</span><span class="sxs-lookup"><span data-stu-id="b5766-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="b5766-314">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="b5766-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="b5766-315">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="b5766-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="b5766-316">La **versione di runtime di scripting** deve essere **stabile** (equivalente a .NET 3,5).</span><span class="sxs-lookup"><span data-stu-id="b5766-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="b5766-317">Il **back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="b5766-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="b5766-318">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="b5766-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="b5766-320">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="b5766-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="b5766-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b5766-321">**InternetClient**</span></span>
        2. <span data-ttu-id="b5766-322">**Microfono**</span><span class="sxs-lookup"><span data-stu-id="b5766-322">**Microphone**</span></span>

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="b5766-324">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="b5766-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aggiornare le impostazioni X R.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="b5766-326">Nelle *impostazioni di compilazione* i progetti _Unity C#_  non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="b5766-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="b5766-327">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="b5766-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="b5766-328">Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="b5766-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="b5766-329">Capitolo 4: creare la scena</span><span class="sxs-lookup"><span data-stu-id="b5766-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5766-330">Se si desidera ignorare il componente di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile scaricarlo [. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importarlo nel progetto come [pacchetto personalizzato](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="b5766-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="b5766-331">Fare clic con il pulsante destro del mouse in un'area vuota del *Pannello gerarchia*, sotto **oggetto 3D**, Aggiungi un **piano**.</span><span class="sxs-lookup"><span data-stu-id="b5766-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Creare un piano.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="b5766-333">Tenere presente che quando si fa di nuovo clic con il pulsante destro del mouse all'interno della *gerarchia* per creare più oggetti, se è ancora stato selezionato l'ultimo oggetto, l'oggetto selezionato sarà l'elemento padre del nuovo oggetto.</span><span class="sxs-lookup"><span data-stu-id="b5766-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="b5766-334">Per evitare questo problema, fare clic con il pulsante destro del mouse su uno spazio vuoto all'interno della gerarchia.</span><span class="sxs-lookup"><span data-stu-id="b5766-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="b5766-335">Ripetere la procedura precedente per aggiungere gli oggetti seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="b5766-336">*Sfera*</span><span class="sxs-lookup"><span data-stu-id="b5766-336">*Sphere*</span></span>
    2. <span data-ttu-id="b5766-337">*Cilindro*</span><span class="sxs-lookup"><span data-stu-id="b5766-337">*Cylinder*</span></span>
    3. <span data-ttu-id="b5766-338">*Cubo*</span><span class="sxs-lookup"><span data-stu-id="b5766-338">*Cube*</span></span>
    4. <span data-ttu-id="b5766-339">*Testo 3D*</span><span class="sxs-lookup"><span data-stu-id="b5766-339">*3D Text*</span></span>

4.  <span data-ttu-id="b5766-340">La *gerarchia* della scena risultante deve essere simile a quella dell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="b5766-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Impostazione della gerarchia della scena.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="b5766-342">Fare clic sulla **fotocamera principale** per selezionarla. esaminare il *pannello Inspector* per visualizzare l'oggetto fotocamera con tutti i relativi componenti.</span><span class="sxs-lookup"><span data-stu-id="b5766-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="b5766-343">Fare clic sul pulsante **Aggiungi componente** che si trova nella parte inferiore del *pannello Inspector*.</span><span class="sxs-lookup"><span data-stu-id="b5766-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Aggiungi origine audio](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="b5766-345">Cercare il componente denominato *origine audio*, come illustrato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="b5766-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="b5766-346">Assicurarsi inoltre che il componente *trasformazione* della fotocamera principale sia impostato su (0, 0, 0). a tale scopo, è possibile premere l'icona a forma di **ingranaggio** accanto al componente *trasformazione* della fotocamera e selezionare **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="b5766-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="b5766-347">Il componente *Transform* dovrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="b5766-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="b5766-348">*Position* è impostato su **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="b5766-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="b5766-349">*Rotation* è impostato su **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="b5766-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="b5766-350">Per Microsoft HoloLens, è necessario modificare anche quanto segue, che fa parte del componente della **fotocamera** , presente nella **fotocamera principale**:</span><span class="sxs-lookup"><span data-stu-id="b5766-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="b5766-351">**Cancella flag:** Colore a tinta unita.</span><span class="sxs-lookup"><span data-stu-id="b5766-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="b5766-352">**Informazioni preliminari** ' Black, Alpha 0'-colore esadecimale: #00000000.</span><span class="sxs-lookup"><span data-stu-id="b5766-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="b5766-353">Fare clic sul **piano** per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="b5766-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="b5766-354">Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="b5766-355">Trasformazione- *posizione*</span><span class="sxs-lookup"><span data-stu-id="b5766-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="b5766-356">**X**</span><span class="sxs-lookup"><span data-stu-id="b5766-356">**X**</span></span> | <span data-ttu-id="b5766-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="b5766-357">**Y**</span></span>                  | <span data-ttu-id="b5766-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="b5766-358">**Z**</span></span> |
    | <span data-ttu-id="b5766-359">0</span><span class="sxs-lookup"><span data-stu-id="b5766-359">0</span></span>     | <span data-ttu-id="b5766-360">-1</span><span class="sxs-lookup"><span data-stu-id="b5766-360">-1</span></span>                     | <span data-ttu-id="b5766-361">0</span><span class="sxs-lookup"><span data-stu-id="b5766-361">0</span></span>     |


10. <span data-ttu-id="b5766-362">Fare clic sulla **sfera** per selezionarla.</span><span class="sxs-lookup"><span data-stu-id="b5766-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="b5766-363">Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="b5766-364">Trasformazione- *posizione*</span><span class="sxs-lookup"><span data-stu-id="b5766-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="b5766-365">**X**</span><span class="sxs-lookup"><span data-stu-id="b5766-365">**X**</span></span> | <span data-ttu-id="b5766-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="b5766-366">**Y**</span></span>                  | <span data-ttu-id="b5766-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="b5766-367">**Z**</span></span> |
    | <span data-ttu-id="b5766-368">2</span><span class="sxs-lookup"><span data-stu-id="b5766-368">2</span></span>     | <span data-ttu-id="b5766-369">1</span><span class="sxs-lookup"><span data-stu-id="b5766-369">1</span></span>                      | <span data-ttu-id="b5766-370">2</span><span class="sxs-lookup"><span data-stu-id="b5766-370">2</span></span>     |

11. <span data-ttu-id="b5766-371">Fare clic sul **cilindro** per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="b5766-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="b5766-372">Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="b5766-373">Trasformazione- *posizione*</span><span class="sxs-lookup"><span data-stu-id="b5766-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="b5766-374">**X**</span><span class="sxs-lookup"><span data-stu-id="b5766-374">**X**</span></span> | <span data-ttu-id="b5766-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="b5766-375">**Y**</span></span>                  | <span data-ttu-id="b5766-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="b5766-376">**Z**</span></span> |
    | <span data-ttu-id="b5766-377">2</span><span class="sxs-lookup"><span data-stu-id="b5766-377">-2</span></span>    | <span data-ttu-id="b5766-378">1</span><span class="sxs-lookup"><span data-stu-id="b5766-378">1</span></span>                      | <span data-ttu-id="b5766-379">2</span><span class="sxs-lookup"><span data-stu-id="b5766-379">2</span></span>     |

12. <span data-ttu-id="b5766-380">Fare clic sul **cubo** per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="b5766-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="b5766-381">Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="b5766-382">Trasformazione- *posizione*</span><span class="sxs-lookup"><span data-stu-id="b5766-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="b5766-383">Trasformazione- *rotazione*</span><span class="sxs-lookup"><span data-stu-id="b5766-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="b5766-384">**X**</span><span class="sxs-lookup"><span data-stu-id="b5766-384">**X**</span></span> | <span data-ttu-id="b5766-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="b5766-385">**Y**</span></span>                   | <span data-ttu-id="b5766-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="b5766-386">**Z**</span></span> |  \| | <span data-ttu-id="b5766-387">**X**</span><span class="sxs-lookup"><span data-stu-id="b5766-387">**X**</span></span> | <span data-ttu-id="b5766-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="b5766-388">**Y**</span></span>                  | <span data-ttu-id="b5766-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="b5766-389">**Z**</span></span> |
    | <span data-ttu-id="b5766-390">0</span><span class="sxs-lookup"><span data-stu-id="b5766-390">0</span></span>     | <span data-ttu-id="b5766-391">1</span><span class="sxs-lookup"><span data-stu-id="b5766-391">1</span></span>                       | <span data-ttu-id="b5766-392">4</span><span class="sxs-lookup"><span data-stu-id="b5766-392">4</span></span>     |  \| | <span data-ttu-id="b5766-393">45</span><span class="sxs-lookup"><span data-stu-id="b5766-393">45</span></span>    | <span data-ttu-id="b5766-394">45</span><span class="sxs-lookup"><span data-stu-id="b5766-394">45</span></span>                     | <span data-ttu-id="b5766-395">0</span><span class="sxs-lookup"><span data-stu-id="b5766-395">0</span></span>     | 

13. <span data-ttu-id="b5766-396">Fare clic sul **nuovo oggetto testo** per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="b5766-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="b5766-397">Nel *pannello Inspector* impostare il componente *Transform* con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="b5766-398">Trasformazione- *posizione*</span><span class="sxs-lookup"><span data-stu-id="b5766-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="b5766-399">Trasformazione- *Ridimensiona*</span><span class="sxs-lookup"><span data-stu-id="b5766-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="b5766-400">**X**</span><span class="sxs-lookup"><span data-stu-id="b5766-400">**X**</span></span> | <span data-ttu-id="b5766-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="b5766-401">**Y**</span></span>                  | <span data-ttu-id="b5766-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="b5766-402">**Z**</span></span> |  \| | <span data-ttu-id="b5766-403">**X**</span><span class="sxs-lookup"><span data-stu-id="b5766-403">**X**</span></span> | <span data-ttu-id="b5766-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="b5766-404">**Y**</span></span>               | <span data-ttu-id="b5766-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="b5766-405">**Z**</span></span> |
    | <span data-ttu-id="b5766-406">2</span><span class="sxs-lookup"><span data-stu-id="b5766-406">-2</span></span>    | <span data-ttu-id="b5766-407">6</span><span class="sxs-lookup"><span data-stu-id="b5766-407">6</span></span>                      | <span data-ttu-id="b5766-408">9</span><span class="sxs-lookup"><span data-stu-id="b5766-408">9</span></span>     |  \| | <span data-ttu-id="b5766-409">0,1</span><span class="sxs-lookup"><span data-stu-id="b5766-409">0.1</span></span>   | <span data-ttu-id="b5766-410">0,1</span><span class="sxs-lookup"><span data-stu-id="b5766-410">0.1</span></span>                 | <span data-ttu-id="b5766-411">0,1</span><span class="sxs-lookup"><span data-stu-id="b5766-411">0.1</span></span>   | 

14. <span data-ttu-id="b5766-412">Modificare le **dimensioni del carattere** nel componente mesh di **testo** in **50**.</span><span class="sxs-lookup"><span data-stu-id="b5766-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="b5766-413">Modificare il *nome* dell'oggetto **mesh di testo** in **testo di dettatura**.</span><span class="sxs-lookup"><span data-stu-id="b5766-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![Crea oggetto testo 3D](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="b5766-415">La struttura del pannello della gerarchia dovrebbe ora essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="b5766-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![mesh di testo in visualizzazione scena](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="b5766-417">La scena finale dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="b5766-417">The final scene should look like the image below:</span></span>

    ![Visualizzazione della scena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="b5766-419">Capitolo 5: creare la classe MicrophoneManager</span><span class="sxs-lookup"><span data-stu-id="b5766-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="b5766-420">Il primo script che si intende creare è la classe *MicrophoneManager* .</span><span class="sxs-lookup"><span data-stu-id="b5766-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="b5766-421">A questo punto si creeranno i *LuisManager*, la classe *behaviors* e infine la classe *sguardi* (è possibile crearli tutti ora, anche se verranno trattati quando si raggiunge ogni capitolo).</span><span class="sxs-lookup"><span data-stu-id="b5766-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="b5766-422">La classe *MicrophoneManager* è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="b5766-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="b5766-423">Rilevamento del dispositivo di registrazione collegato all'auricolare o al computer (a seconda del valore predefinito).</span><span class="sxs-lookup"><span data-stu-id="b5766-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="b5766-424">Acquisire l'audio (voce) e utilizzare la dettatura per archiviarlo come stringa.</span><span class="sxs-lookup"><span data-stu-id="b5766-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="b5766-425">Una volta sospesa la voce, inviare la dettatura alla classe *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="b5766-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="b5766-426">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="b5766-426">To create this class:</span></span> 

1.  <span data-ttu-id="b5766-427">Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare > cartella**.</span><span class="sxs-lookup"><span data-stu-id="b5766-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="b5766-428">Chiamare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="b5766-428">Call the folder **Scripts**.</span></span> 

    ![Crea cartella script.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="b5766-430">Con la cartella **Scripts** creata, fare doppio clic su di essa per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b5766-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="b5766-431">Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse su **Crea Script > C#** .</span><span class="sxs-lookup"><span data-stu-id="b5766-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="b5766-432">Denominare lo script *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="b5766-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="b5766-433">Fare doppio clic su *MicrophoneManager* per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="b5766-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="b5766-434">Aggiungere i seguenti spazi dei nomi all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="b5766-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="b5766-435">Aggiungere quindi le variabili seguenti all'interno della classe *MicrophoneManager* :</span><span class="sxs-lookup"><span data-stu-id="b5766-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="b5766-436">È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="b5766-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="b5766-437">Questi verranno chiamati quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="b5766-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="b5766-438">A questo punto è necessario il metodo che l'app usa per avviare e arrestare l'acquisizione vocale e passarla alla classe *LuisManager* , che verrà compilata a breve.</span><span class="sxs-lookup"><span data-stu-id="b5766-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="b5766-439">Aggiungere un *gestore di dettatura* che verrà richiamato quando la voce viene sospesa.</span><span class="sxs-lookup"><span data-stu-id="b5766-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="b5766-440">Questo metodo passerà il testo della dettatura alla classe *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="b5766-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="b5766-441">Eliminare il metodo *Update ()* perché non verrà utilizzato da questa classe.</span><span class="sxs-lookup"><span data-stu-id="b5766-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="b5766-442">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5766-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b5766-443">A questo punto si noterà un errore nel *Pannello console dell'editor di Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5766-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="b5766-444">Questo perché il codice fa riferimento alla classe *LuisManager* che verrà creata nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="b5766-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="b5766-445">Capitolo 6: creare la classe LUISManager</span><span class="sxs-lookup"><span data-stu-id="b5766-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="b5766-446">È il momento di creare la classe *LuisManager* , che effettuerà la chiamata al servizio Azure Luis.</span><span class="sxs-lookup"><span data-stu-id="b5766-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="b5766-447">Lo scopo di questa classe è di ricevere il testo della dettatura dalla classe *MicrophoneManager* e di inviarlo al *API Language Understanding di Azure* da analizzare.</span><span class="sxs-lookup"><span data-stu-id="b5766-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="b5766-448">Questa classe deserializzare la risposta *JSON* e chiamare i metodi appropriati della classe *behaviors* per attivare un'azione.</span><span class="sxs-lookup"><span data-stu-id="b5766-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="b5766-449">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="b5766-449">To create this class:</span></span> 

1.  <span data-ttu-id="b5766-450">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b5766-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="b5766-451">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="b5766-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b5766-452">Denominare lo script *LuisManager*.</span><span class="sxs-lookup"><span data-stu-id="b5766-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="b5766-453">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5766-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="b5766-454">Aggiungere i seguenti spazi dei nomi all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="b5766-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="b5766-455">Si inizierà creando tre classi **all'interno** della classe *LuisManager* (all'interno dello stesso file di script, sopra il metodo *Start ()* ) che rappresenterà la risposta JSON deserializzata da Azure.</span><span class="sxs-lookup"><span data-stu-id="b5766-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="b5766-456">Aggiungere quindi le variabili seguenti all'interno della classe *LuisManager* :</span><span class="sxs-lookup"><span data-stu-id="b5766-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="b5766-457">Assicurarsi di inserire l'endpoint LUIS in ora, che sarà disponibile nel portale LUIS.</span><span class="sxs-lookup"><span data-stu-id="b5766-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="b5766-458">È ora necessario aggiungere il codice per il metodo *svegli ()* .</span><span class="sxs-lookup"><span data-stu-id="b5766-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="b5766-459">Questo metodo verrà chiamato quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="b5766-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="b5766-460">A questo punto sono necessari i metodi usati da questa applicazione per inviare la dettatura ricevuta dalla classe *MicrophoneManager* a *Luis*, quindi ricevere e deserializzare la risposta.</span><span class="sxs-lookup"><span data-stu-id="b5766-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="b5766-461">Una volta che il valore dello scopo e le entità associate sono stati determinati, vengono passati all'istanza della classe *behaviors* per attivare l'azione desiderata.</span><span class="sxs-lookup"><span data-stu-id="b5766-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="b5766-462">Creare un nuovo metodo denominato *AnalyseResponseElements ()* in grado di leggere il *AnalysedQuery* risultante e determinare le entità.</span><span class="sxs-lookup"><span data-stu-id="b5766-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="b5766-463">Una volta determinate tali entità, verranno passate all'istanza della classe *behaviors* da usare nelle azioni.</span><span class="sxs-lookup"><span data-stu-id="b5766-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="b5766-464">Eliminare i metodi *Start ()* e *Update ()* perché questa classe non li utilizzerà.</span><span class="sxs-lookup"><span data-stu-id="b5766-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="b5766-465">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5766-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="b5766-466">A questo punto si noterà che nel *Pannello console dell'editor di Unity*verranno visualizzati diversi errori.</span><span class="sxs-lookup"><span data-stu-id="b5766-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="b5766-467">Questo perché il codice fa riferimento alla classe *behaviors* che verrà creata nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="b5766-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="b5766-468">Capitolo 7: creare la classe Behaviors</span><span class="sxs-lookup"><span data-stu-id="b5766-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="b5766-469">La classe *behaviors* attiverà le azioni usando le entità fornite dalla classe *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="b5766-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="b5766-470">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="b5766-470">To create this class:</span></span> 

1.  <span data-ttu-id="b5766-471">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b5766-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="b5766-472">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="b5766-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b5766-473">Assegnare un nome ai *comportamenti*dello script.</span><span class="sxs-lookup"><span data-stu-id="b5766-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="b5766-474">Fare doppio clic sullo script per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="b5766-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="b5766-475">Aggiungere quindi le variabili seguenti all'interno della classe *behaviors* :</span><span class="sxs-lookup"><span data-stu-id="b5766-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="b5766-476">Aggiungere il codice del metodo *sveglie ()* .</span><span class="sxs-lookup"><span data-stu-id="b5766-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="b5766-477">Questo metodo verrà chiamato quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="b5766-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="b5766-478">I metodi seguenti vengono chiamati dalla classe *LuisManager* (creata in precedenza) per determinare quale oggetto è la destinazione della query e quindi attivare l'azione appropriata.</span><span class="sxs-lookup"><span data-stu-id="b5766-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="b5766-479">Aggiungere il metodo *FindTarget ()* per determinare quale *GameObject* è la destinazione dello scopo corrente.</span><span class="sxs-lookup"><span data-stu-id="b5766-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="b5766-480">Questo metodo imposta come valore predefinito la destinazione per *GameObject* che viene "guardato" se nelle entità non è definita alcuna destinazione esplicita.</span><span class="sxs-lookup"><span data-stu-id="b5766-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="b5766-481">Eliminare i metodi *Start ()* e *Update ()* perché questa classe non li utilizzerà.</span><span class="sxs-lookup"><span data-stu-id="b5766-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="b5766-482">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5766-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="b5766-483">Capitolo 8-creare la classe sguardi</span><span class="sxs-lookup"><span data-stu-id="b5766-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="b5766-484">L'ultima classe che sarà necessario completare questa app è la classe *sguardi* .</span><span class="sxs-lookup"><span data-stu-id="b5766-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="b5766-485">Questa classe aggiorna il riferimento a *GameObject* attualmente nello stato attivo visivo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="b5766-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="b5766-486">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="b5766-486">To create this Class:</span></span> 

1.  <span data-ttu-id="b5766-487">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b5766-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="b5766-488">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="b5766-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b5766-489">Denominare *lo script.*</span><span class="sxs-lookup"><span data-stu-id="b5766-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="b5766-490">Fare doppio clic sullo script per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="b5766-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="b5766-491">Inserire il codice seguente per questa classe:</span><span class="sxs-lookup"><span data-stu-id="b5766-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="b5766-492">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5766-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="b5766-493">Capitolo 9: completamento della configurazione della scena</span><span class="sxs-lookup"><span data-stu-id="b5766-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="b5766-494">Per completare l'installazione della scena, trascinare ogni script creato dalla cartella Scripts all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="b5766-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="b5766-495">Selezionare la **fotocamera principale** ed esaminare il *pannello Inspector*. dovrebbe essere possibile visualizzare ogni script collegato e si noterà che sono presenti parametri per ogni script che è ancora necessario impostare.</span><span class="sxs-lookup"><span data-stu-id="b5766-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Impostazione delle destinazioni di riferimento per la fotocamera.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="b5766-497">Per impostare correttamente questi parametri, attenersi alle istruzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="b5766-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="b5766-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="b5766-499">Dal *Pannello gerarchia*trascinare l'oggetto **testo di dettatura** nella casella valore parametro **testo di dettatura** .</span><span class="sxs-lookup"><span data-stu-id="b5766-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="b5766-500">*Comportamenti*, dal *Pannello gerarchia*:</span><span class="sxs-lookup"><span data-stu-id="b5766-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="b5766-501">Trascinare l'oggetto **Sphere** nella casella destinazione riferimento a *sfera* .</span><span class="sxs-lookup"><span data-stu-id="b5766-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="b5766-502">Trascinare il **cilindro** nella casella destinazione riferimento *cilindro* .</span><span class="sxs-lookup"><span data-stu-id="b5766-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="b5766-503">Trascinare il **cubo** nella casella destinazione riferimento *cubo* .</span><span class="sxs-lookup"><span data-stu-id="b5766-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="b5766-504">*Sguardo*:</span><span class="sxs-lookup"><span data-stu-id="b5766-504">*Gaze*:</span></span>

        - <span data-ttu-id="b5766-505">Imposta la *distanza massima di sguardi* su **300** (se non è già presente).</span><span class="sxs-lookup"><span data-stu-id="b5766-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="b5766-506">Il risultato dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="b5766-506">The result should look like the image below:</span></span>

    ![Visualizzazione delle destinazioni di riferimento della fotocamera, ora impostate.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="b5766-508">Capitolo 10: eseguire il test nell'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="b5766-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="b5766-509">Verificare che l'installazione della scena sia implementata correttamente.</span><span class="sxs-lookup"><span data-stu-id="b5766-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="b5766-510">Verifica che:</span><span class="sxs-lookup"><span data-stu-id="b5766-510">Ensure that:</span></span>

-   <span data-ttu-id="b5766-511">Tutti gli script sono collegati all'oggetto **principale della fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="b5766-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="b5766-512">Tutti i campi nel *pannello principale di controllo della fotocamera* sono assegnati correttamente.</span><span class="sxs-lookup"><span data-stu-id="b5766-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="b5766-513">Premere il pulsante **Play** nell' *editor di Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5766-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="b5766-514">L'app deve essere in esecuzione all'interno dell'auricolare immersivo collegato.</span><span class="sxs-lookup"><span data-stu-id="b5766-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="b5766-515">Provare alcune espressioni, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b5766-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="b5766-516">Se nella console di Unity viene visualizzato un errore relativo alla modifica del dispositivo audio predefinito, è possibile che la scena non funzioni come previsto.</span><span class="sxs-lookup"><span data-stu-id="b5766-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="b5766-517">Questo è dovuto al modo in cui il portale di realtà mista gestisce i microfoni predefiniti per le cuffie che li hanno.</span><span class="sxs-lookup"><span data-stu-id="b5766-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="b5766-518">Se viene visualizzato questo errore, è sufficiente arrestare la scena e avviarla di nuovo e le operazioni dovrebbero funzionare come previsto.</span><span class="sxs-lookup"><span data-stu-id="b5766-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="b5766-519">Capitolo 11: compilare e sideload la soluzione UWP</span><span class="sxs-lookup"><span data-stu-id="b5766-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="b5766-520">Dopo aver verificato che l'applicazione funzioni nell'editor di Unity, è possibile eseguire la compilazione e la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="b5766-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="b5766-521">Per compilare:</span><span class="sxs-lookup"><span data-stu-id="b5766-521">To Build:</span></span>

1.  <span data-ttu-id="b5766-522">Salvare la scena corrente facendo clic su **File > Salva**.</span><span class="sxs-lookup"><span data-stu-id="b5766-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="b5766-523">Passare a **File > impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="b5766-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="b5766-524">Seleziona la casella denominata **progetti C# Unity** (utile per visualizzare ed eseguire il debug del codice una volta creato il progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="b5766-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="b5766-525">Fare clic su **Aggiungi scene aperte**, quindi fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="b5766-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Finestra impostazioni di compilazione](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="b5766-527">Verrà richiesto di selezionare la cartella in cui si vuole compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="b5766-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="b5766-528">Creare una cartella *compilazioni* e all'interno di tale cartella creare un'altra cartella con un nome appropriato.</span><span class="sxs-lookup"><span data-stu-id="b5766-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="b5766-529">Fare clic su **Seleziona cartella** per iniziare la compilazione in quel percorso.</span><span class="sxs-lookup"><span data-stu-id="b5766-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="b5766-530">![crea cartella compilazioni](images/AzureLabs-Lab3-44.png)
    ![selezionare la cartella compilazioni](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="b5766-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="b5766-531">Al termine della compilazione di Unity (potrebbe richiedere del tempo), dovrebbe aprire una finestra di **Esplora file** nel percorso della compilazione.</span><span class="sxs-lookup"><span data-stu-id="b5766-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="b5766-532">Per eseguire la distribuzione nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="b5766-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="b5766-533">In *Visual Studio*aprire il file di soluzione creato nel [capitolo precedente](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="b5766-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="b5766-534">Nella **piattaforma soluzione**selezionare **x86**, **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="b5766-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="b5766-535">Nella **configurazione della soluzione** selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="b5766-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="b5766-536">Per Microsoft HoloLens, può risultare più semplice impostare questa impostazione su *computer remoto*, in modo da non essere collegati al computer.</span><span class="sxs-lookup"><span data-stu-id="b5766-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="b5766-537">Tuttavia, sarà necessario eseguire anche le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5766-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="b5766-538">Conosce l' **indirizzo IP** del HoloLens, disponibile all'interno delle *impostazioni > rete & Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare.</span><span class="sxs-lookup"><span data-stu-id="b5766-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="b5766-539">Verificare che la **modalità sviluppatore** sia **attiva**; disponibile in *impostazioni > aggiorna & > di sicurezza per gli sviluppatori*.</span><span class="sxs-lookup"><span data-stu-id="b5766-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Distribuisci app](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="b5766-541">Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.</span><span class="sxs-lookup"><span data-stu-id="b5766-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="b5766-542">L'app verrà visualizzata nell'elenco delle app installate, pronta per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="b5766-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="b5766-543">Una volta avviata, l'app richiederà di autorizzare l'accesso al _microfono_.</span><span class="sxs-lookup"><span data-stu-id="b5766-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="b5766-544">Usare i *controller di movimento*o l' *input vocale*o la *tastiera* per premere il pulsante **Sì** .</span><span class="sxs-lookup"><span data-stu-id="b5766-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="b5766-545">Capitolo 12: miglioramento del servizio LUIS</span><span class="sxs-lookup"><span data-stu-id="b5766-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="b5766-546">Questo capitolo è estremamente importante e può essere necessario iterare più volte, in quanto consente di migliorare l'accuratezza del servizio LUIS: assicurarsi di completare questa operazione.</span><span class="sxs-lookup"><span data-stu-id="b5766-546">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="b5766-547">Per migliorare il livello di comprensione fornito da LUIS, è necessario acquisire nuove espressioni e usarle per ripetere il training dell'app LUIS.</span><span class="sxs-lookup"><span data-stu-id="b5766-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="b5766-548">Ad esempio, è possibile che sia stato eseguito il training di LUIS per comprendere "aumento" e "ridimensionamento", ma non si vuole che l'app includa anche parole come "ingrandire"?</span><span class="sxs-lookup"><span data-stu-id="b5766-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="b5766-549">Una volta che l'applicazione è stata usata più volte, tutto ciò che si è detto verrà raccolto da LUIS e sarà disponibile nel portale LUIS.</span><span class="sxs-lookup"><span data-stu-id="b5766-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="b5766-550">Passare all'applicazione del portale dopo questo [collegamento](https://www.luis.ai/home)ed eseguire l'accesso.</span><span class="sxs-lookup"><span data-stu-id="b5766-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="b5766-551">Dopo aver eseguito l'accesso con le credenziali MS, fare clic sul *nome dell'app*.</span><span class="sxs-lookup"><span data-stu-id="b5766-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="b5766-552">Fare clic sul pulsante **Verifica espressioni endpoint** a sinistra della pagina.</span><span class="sxs-lookup"><span data-stu-id="b5766-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Esaminare le espressioni](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="b5766-554">Verrà visualizzato un elenco di espressioni inviate a LUIS dall'applicazione per realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b5766-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Elenco di espressioni](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="b5766-556">Si noteranno alcune *entità*evidenziate.</span><span class="sxs-lookup"><span data-stu-id="b5766-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="b5766-557">Passando il mouse su ogni parola evidenziata, è possibile esaminare ogni espressione e determinare quale entità è stata riconosciuta correttamente, quali entità sono errate e quali entità mancano.</span><span class="sxs-lookup"><span data-stu-id="b5766-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="b5766-558">Nell'esempio precedente, è stato rilevato che la parola "Spear" era stata evidenziata come destinazione, quindi è necessario correggere l'errore, eseguendo il passaggio del mouse sulla parola con il mouse e scegliendo **Rimuovi etichetta**.</span><span class="sxs-lookup"><span data-stu-id="b5766-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="b5766-559">![controllare le espressioni](images/AzureLabs-Lab3-49.png)
![rimuovere l'immagine dell'etichetta](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="b5766-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="b5766-560">Se si trovano espressioni completamente errate, è possibile eliminarle usando il pulsante **Elimina** sul lato destro dello schermo.</span><span class="sxs-lookup"><span data-stu-id="b5766-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Elimina espressioni non corrette](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="b5766-562">In alternativa, se si ritiene che LUIS abbia interpretato correttamente l'espressione, è possibile convalidarne la comprensione usando il pulsante **Aggiungi a scopo allineato** .</span><span class="sxs-lookup"><span data-stu-id="b5766-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Aggiungi a finalità allineata](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="b5766-564">Una volta ordinate tutte le espressioni visualizzate, provare a ricaricare la pagina per verificare se sono disponibili ulteriori informazioni.</span><span class="sxs-lookup"><span data-stu-id="b5766-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="b5766-565">È molto importante ripetere questo processo il maggior numero di volte possibile per migliorare la comprensione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b5766-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="b5766-566">**Buon divertimento!**</span><span class="sxs-lookup"><span data-stu-id="b5766-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="b5766-567">Applicazione integrata LUIS completata</span><span class="sxs-lookup"><span data-stu-id="b5766-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="b5766-568">Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio Azure Language Understanding Intelligence, per comprendere cosa dice un utente e agire su tali informazioni.</span><span class="sxs-lookup"><span data-stu-id="b5766-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![risultato Lab](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b5766-570">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="b5766-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b5766-571">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="b5766-571">Exercise 1</span></span>

<span data-ttu-id="b5766-572">Quando si usa questa applicazione è possibile notare che, se si osserva l'oggetto Floor e si chiede di modificarne il colore, questa operazione verrà eseguita.</span><span class="sxs-lookup"><span data-stu-id="b5766-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="b5766-573">È possibile risolvere il modo in cui arrestare l'applicazione modificando il colore del piano?</span><span class="sxs-lookup"><span data-stu-id="b5766-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b5766-574">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="b5766-574">Exercise 2</span></span>

<span data-ttu-id="b5766-575">Provare a estendere le funzionalità di LUIS e app, aggiungendo funzionalità aggiuntive per gli oggetti nella scena. è ad esempio possibile creare nuovi oggetti in corrispondenza del punto di riscontro, a seconda di ciò che viene indicato dall'utente e quindi usare tali oggetti insieme agli oggetti scena correnti, con i comandi esistenti.</span><span class="sxs-lookup"><span data-stu-id="b5766-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
