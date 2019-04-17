---
title: MR e Azure 303 - linguaggio naturale, comprensione (LUIS)
description: Completare questo corso di informazioni su come implementare Azure Intelligence servizio LUIS (Language Understanding) all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, servizio di intelligence language understanding, luis, hololens, vr immersivi,
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603075"
---
>[!NOTE]
><span data-ttu-id="96017-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="96017-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="96017-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="96017-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="96017-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="96017-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="96017-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="96017-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="96017-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="96017-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="96017-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="96017-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="96017-110">MR e Azure 303: Naturale LUIS (language understanding)</span><span class="sxs-lookup"><span data-stu-id="96017-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="96017-111">In questo corso, si apprenderà come integrare un'applicazione di realtà mista con servizi cognitivi di Azure, con l'API di Language Understanding Language Understanding Intelligent Service.</span><span class="sxs-lookup"><span data-stu-id="96017-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![risultato di Lab](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="96017-113">*LUIS (Language Understanding)* è un servizio di Microsoft Azure, che offre alle applicazioni grazie alla possibilità di rendere significato all'esterno di input dell'utente, ad esempio tramite l'estrazione di ciò che potrebbe essere una persona, opinione.</span><span class="sxs-lookup"><span data-stu-id="96017-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="96017-114">Questo risultato viene ottenuto tramite machine learning, che riconosce e apprende le informazioni di input e quindi possono rispondere con informazioni dettagliate rilevanti.</span><span class="sxs-lookup"><span data-stu-id="96017-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="96017-115">Per altre informazioni, visitare il [pagina Azure LUIS (Language Understanding)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="96017-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="96017-116">Dopo aver completato il corso, si avrà un'applicazione di realtà mista visore VR immersivi che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="96017-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="96017-117">Acquisire il riconoscimento vocale input utente, usare il microfono collegato al visore VR immersivi.</span><span class="sxs-lookup"><span data-stu-id="96017-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="96017-118">Inviare la dettatura acquisita la *Azure Language Understanding Intelligent Service* (*LUIS*).</span><span class="sxs-lookup"><span data-stu-id="96017-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="96017-119">Disporre di estrazione LUIS vale a dire dalle informazioni di trasmissione, che verranno analizzate e tentano di determinare che lo scopo della richiesta dell'utente verrà apportato.</span><span class="sxs-lookup"><span data-stu-id="96017-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="96017-120">Lo sviluppo include la creazione di un'app in cui l'utente sarà in grado di usare la forma e/o estasiati per modificare le dimensioni e il colore degli oggetti nella scena.</span><span class="sxs-lookup"><span data-stu-id="96017-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="96017-121">Non verrà descritto l'utilizzo di controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="96017-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="96017-122">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="96017-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="96017-123">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="96017-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="96017-124">È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="96017-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="96017-125">Essere preparati a LUIS Train più volte, illustrata nel [capitolo 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="96017-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="96017-126">Si otterranno risultati migliori di altre volte che LUIS è stato eseguito il training.</span><span class="sxs-lookup"><span data-stu-id="96017-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="96017-127">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="96017-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="96017-128">Corso</span><span class="sxs-lookup"><span data-stu-id="96017-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="96017-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="96017-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="96017-130"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="96017-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="96017-131">MR e Azure 303: Naturale LUIS (language understanding)</span><span class="sxs-lookup"><span data-stu-id="96017-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="96017-132">✔️</span><span class="sxs-lookup"><span data-stu-id="96017-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="96017-133">✔️</span><span class="sxs-lookup"><span data-stu-id="96017-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="96017-134">Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="96017-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="96017-135">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="96017-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="96017-136">Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.</span><span class="sxs-lookup"><span data-stu-id="96017-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96017-137">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="96017-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="96017-138">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="96017-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="96017-139">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="96017-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="96017-140">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .</span><span class="sxs-lookup"><span data-stu-id="96017-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="96017-141">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="96017-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="96017-142">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="96017-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="96017-143">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="96017-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="96017-144">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="96017-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="96017-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="96017-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="96017-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="96017-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="96017-147">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="96017-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="96017-148">Le cuffie con un microfono incorporato (se le cuffie non è presente un mic incorporati e altri relatori)</span><span class="sxs-lookup"><span data-stu-id="96017-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="96017-149">Accesso a Internet per la configurazione di Azure e il recupero di LUIS</span><span class="sxs-lookup"><span data-stu-id="96017-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="96017-150">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="96017-150">Before you start</span></span>

1.  <span data-ttu-id="96017-151">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="96017-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="96017-152">Per consentire la macchina per abilitare la dettatura, passare a **delle impostazioni di Windows > Privacy > vocale, input penna e digitando** e premere il pulsante **Turn On servizi di riconoscimento vocale e i suggerimenti di digitazione**.</span><span class="sxs-lookup"><span data-stu-id="96017-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="96017-153">Il codice in questa esercitazione sarà possibile registrare dal **Default Device microfono** impostata nel computer.</span><span class="sxs-lookup"><span data-stu-id="96017-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="96017-154">Assicurarsi che il dispositivo di microfono predefinito viene impostato come quello che si desidera usare per acquisire la voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="96017-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="96017-155">Se le cuffie dispone di un microfono incorporato, assicurarsi che l'opzione *"Quando wear my le cuffie, passare a microfono auricolare"* attivata nel *portale di realtà mista* impostazioni.</span><span class="sxs-lookup"><span data-stu-id="96017-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Configurazione di visore VR immersivi](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="96017-157">Capitolo 1: configurare il portale di Azure</span><span class="sxs-lookup"><span data-stu-id="96017-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="96017-158">Usare la *Language Understanding Intelligent Service* servizio in Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="96017-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="96017-159">Accedi per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="96017-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="96017-160">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="96017-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="96017-161">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="96017-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="96017-162">Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *Language Understanding Intelligent Service*, fare clic su **invio**.</span><span class="sxs-lookup"><span data-stu-id="96017-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Crea risorsa di LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="96017-164">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="96017-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="96017-165">La nuova pagina a destra fornirà una descrizione del servizio Language Understanding Intelligent Service.</span><span class="sxs-lookup"><span data-stu-id="96017-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="96017-166">AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="96017-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Creazione di un servizio LUIS - note legali](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="96017-168">Dopo avere fatto clic su Crea:</span><span class="sxs-lookup"><span data-stu-id="96017-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="96017-169">Inserire la posizione desiderata **nome** per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="96017-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="96017-170">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="96017-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="96017-171">Selezionare il **piano tariffario** appropriati per l'utente, se questo è il primo tempo nella creazione una *LUIS Service*, un livello gratuito, denominato F0, debba essere disponibile.</span><span class="sxs-lookup"><span data-stu-id="96017-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="96017-172">L'allocazione gratuito deve essere più che sufficiente per questo corso.</span><span class="sxs-lookup"><span data-stu-id="96017-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="96017-173">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="96017-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="96017-174">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="96017-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="96017-175">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="96017-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="96017-176">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="96017-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="96017-177">Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="96017-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="96017-178">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="96017-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="96017-179">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="96017-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="96017-180">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="96017-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="96017-181">Selezionare **Create**.</span><span class="sxs-lookup"><span data-stu-id="96017-181">Select **Create**.</span></span>

        ![Crea servizio LUIS - input dell'utente](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="96017-183">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="96017-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="96017-184">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="96017-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Nuova immagine di notifica di Azure](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="96017-186">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="96017-186">Click on the notification to explore your new Service instance.</span></span>

    ![Notifica relativa alla creazione risorsa ha esito positivo](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="96017-188">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="96017-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="96017-189">Verrà visualizzata per la nuova istanza del servizio LUIS.</span><span class="sxs-lookup"><span data-stu-id="96017-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![L'accesso alle chiavi di LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="96017-191">All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, questa operazione viene eseguita tramite chiave di sottoscrizione del servizio.</span><span class="sxs-lookup"><span data-stu-id="96017-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="96017-192">Dal *avvio rapido* pagina, delle *API LUIS* del servizio, passare al primo passaggio *individuare le chiavi*e fare clic su **chiavi** (è anche possibile ottenere questo risultato facendo il collegamento blu chiavi, che si trova nel menu di spostamento dei servizi, indicato dall'icona della chiave).</span><span class="sxs-lookup"><span data-stu-id="96017-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="96017-193">Il servizio verrà visualizzata *chiavi*.</span><span class="sxs-lookup"><span data-stu-id="96017-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="96017-194">Richiedere una copia di una delle chiavi visualizzate, in quanto sarà necessaria in un secondo momento nel progetto.</span><span class="sxs-lookup"><span data-stu-id="96017-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="96017-195">Nel *Service* pagina, fare clic su *portale di Language Understanding* essere reindirizzati alla pagina Web che verrà usato per creare il nuovo servizio, all'interno dell'App LUIS.</span><span class="sxs-lookup"><span data-stu-id="96017-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="96017-196">Capitolo 2: il portale di Language Understanding</span><span class="sxs-lookup"><span data-stu-id="96017-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="96017-197">In questa sezione si apprenderà come creare un'App LUIS nel portale di LUIS.</span><span class="sxs-lookup"><span data-stu-id="96017-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="96017-198">Tenere presente, tale impostazione il *entità*, *Intent*, e *Utterances* all'interno di questo capitolo è solo il primo passaggio nella creazione del servizio LUIS: è necessario anche per Ripetere il training del servizio, più volte, quindi, per renderlo più accurate.</span><span class="sxs-lookup"><span data-stu-id="96017-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="96017-199">Ripetizione del training del servizio viene trattato nel [ultimo capitolo](#chapter-12--improving-your-luis-service) di questo corso, pertanto è necessario verificare completarla.</span><span class="sxs-lookup"><span data-stu-id="96017-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="96017-200">Al raggiungimento di *portale di Language Understanding*, potrebbe essere necessario eseguire l'accesso, se non si ha ancora, con le stesse credenziali come il portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="96017-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Pagina di accesso di LUIS](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="96017-202">Se questa è la prima volta, Usa LUIS, è necessario scorrere verso il basso la parte inferiore della pagina di benvenuto, per trovare e fare clic sui **app LUIS creare** pulsante.</span><span class="sxs-lookup"><span data-stu-id="96017-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Creare una pagina dell'app LUIS](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="96017-204">Una volta effettuato l'accesso, fare clic su **le mie app** (se non attualmente in quella sezione).</span><span class="sxs-lookup"><span data-stu-id="96017-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="96017-205">È possibile fare clic su **Crea nuova app**.</span><span class="sxs-lookup"><span data-stu-id="96017-205">You can then click on **Create new app**.</span></span>

    ![LUIS - l'immagine dell'App](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="96017-207">Assegnare all'app un *nome*.</span><span class="sxs-lookup"><span data-stu-id="96017-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="96017-208">Se l'app dovrebbe per comprendere una lingua diversa dall'inglese, è necessario modificare il *delle impostazioni cultura* per la lingua appropriata.</span><span class="sxs-lookup"><span data-stu-id="96017-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="96017-209">Qui è anche possibile aggiungere un *descrizione* della nuova app LUIS.</span><span class="sxs-lookup"><span data-stu-id="96017-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS - creare una nuova app](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="96017-211">Quando si preme **eseguite**, sarà necessario immettere il *compilare* pagina del nuovo *LUIS* dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="96017-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="96017-212">Esistono alcuni concetti importanti di seguito:</span><span class="sxs-lookup"><span data-stu-id="96017-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="96017-213">*Finalità*, rappresenta il metodo che verrà chiamato dopo una query da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="96017-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="96017-214">Un' *finalità* può avere uno o più *entità*.</span><span class="sxs-lookup"><span data-stu-id="96017-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="96017-215">*Entity*, è un componente di query che descrive le informazioni rilevanti per il *INTENT*.</span><span class="sxs-lookup"><span data-stu-id="96017-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="96017-216">*Espressioni*, vengono forniti esempi di query fornite dallo sviluppatore, userà tale LUIS per eseguire il training di se stesso.</span><span class="sxs-lookup"><span data-stu-id="96017-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="96017-217">Se questi concetti non sono perfettamente cancellare, comunque, questo corso chiarirà più avanti in questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="96017-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="96017-218">Inizierà creando il *entità* necessari per compilare questo corso.</span><span class="sxs-lookup"><span data-stu-id="96017-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="96017-219">Sul lato sinistro della pagina, fare clic su *Entities*, quindi fare clic su **Crea nuova entità**.</span><span class="sxs-lookup"><span data-stu-id="96017-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Crea nuova entità](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="96017-221">Chiamare la nuova entità *colore*, impostarne il tipo *semplice*, quindi premere **eseguita**.</span><span class="sxs-lookup"><span data-stu-id="96017-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Creare entità semplice - colore](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="96017-223">Ripetere questo processo di creazione di tre (3) più semplice entità denominate:</span><span class="sxs-lookup"><span data-stu-id="96017-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="96017-224">*upsize*</span><span class="sxs-lookup"><span data-stu-id="96017-224">*upsize*</span></span>
    -   <span data-ttu-id="96017-225">*downsize*</span><span class="sxs-lookup"><span data-stu-id="96017-225">*downsize*</span></span>
    -   <span data-ttu-id="96017-226">*target*</span><span class="sxs-lookup"><span data-stu-id="96017-226">*target*</span></span>

<span data-ttu-id="96017-227">Il risultato dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="96017-227">The result should look like the image below:</span></span>

![Risultato della creazione di entità](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="96017-229">A questo punto è possibile iniziare a creare *Intent*.</span><span class="sxs-lookup"><span data-stu-id="96017-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="96017-230">Non eliminare le **None** finalità.</span><span class="sxs-lookup"><span data-stu-id="96017-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="96017-231">Sul lato sinistro della pagina, fare clic su **Intent**, quindi fare clic su **Crea nuovo finalità**.</span><span class="sxs-lookup"><span data-stu-id="96017-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Creare nuovo Intent](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="96017-233">Chiamare il nuovo *finalità* **ChangeObjectColor**.</span><span class="sxs-lookup"><span data-stu-id="96017-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="96017-234">Ciò *finalità* nome viene usato all'interno del codice più avanti in questo corso, pertanto, per ottenere risultati ottimali, usare questo nome esattamente come fornito.</span><span class="sxs-lookup"><span data-stu-id="96017-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="96017-235">Dopo aver verificato il nome che si verrà indirizzati alla pagina di Intent.</span><span class="sxs-lookup"><span data-stu-id="96017-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS - pagina Intent](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="96017-237">Si noterà che è presente una casella di testo che chiede al tipo 5 o più diverso *Utterances*.</span><span class="sxs-lookup"><span data-stu-id="96017-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="96017-238">LUIS converte tutte le espressioni in lettere minuscole.</span><span class="sxs-lookup"><span data-stu-id="96017-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="96017-239">Inserire il codice seguente *Utterance* nella casella di testo superiore (attualmente con il testo *digitare esempi circa 5...*</span><span class="sxs-lookup"><span data-stu-id="96017-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="96017-240">), quindi premere **invio**:</span><span class="sxs-lookup"><span data-stu-id="96017-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="96017-241">Si noterà che il nuovo *Utterance* verranno visualizzati in un elenco sotto.</span><span class="sxs-lookup"><span data-stu-id="96017-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="96017-242">In seguito lo stesso processo, inserire le seguenti espressioni sei (6):</span><span class="sxs-lookup"><span data-stu-id="96017-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="96017-243">Per ogni Utterance che è stato creato, è necessario identificare le parole devono essere utilizzate dal servizio LUIS come entità.</span><span class="sxs-lookup"><span data-stu-id="96017-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="96017-244">In questo esempio è necessario assegnare un'etichetta di tutti i colori come un *colore* entità e tutti i possibili riferimenti a una destinazione come una *destinazione* entità.</span><span class="sxs-lookup"><span data-stu-id="96017-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="96017-245">A tale scopo, provare a fare clic sulla parola *cilindro* nel primo Utterance e selezionare *destinazione*.</span><span class="sxs-lookup"><span data-stu-id="96017-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Identificare le destinazioni Utterance](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="96017-247">Fare clic sulla parola *rossa* nel primo Utterance e selezionare *colore*.</span><span class="sxs-lookup"><span data-stu-id="96017-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Identificare le entità Utterance](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="96017-249">Etichetta, inoltre, la riga successiva in cui *cubo* deve essere un *destinazione*, e *nero* deve essere un *colore*.</span><span class="sxs-lookup"><span data-stu-id="96017-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="96017-250">Si noti inoltre l'utilizzo delle parole *'this'*, *','*, e *'questo oggetto'*, quale forniamo, quindi avere anche tipi di destinazione non specifiche disponibili.</span><span class="sxs-lookup"><span data-stu-id="96017-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="96017-251">Ripetere il processo precedente fino a quando tutte le espressioni sono le entità denominate.</span><span class="sxs-lookup"><span data-stu-id="96017-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="96017-252">Vedere la seguente immagine se ti serve assistenza.</span><span class="sxs-lookup"><span data-stu-id="96017-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="96017-253">Quando si selezionano le parole per etichettarle come entità:</span><span class="sxs-lookup"><span data-stu-id="96017-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="96017-254">Per singole parole fai clic su essi.</span><span class="sxs-lookup"><span data-stu-id="96017-254">For single words just click them.</span></span>
    > - <span data-ttu-id="96017-255">Per un set di due o più parole, fare clic all'inizio e quindi alla fine del set.</span><span class="sxs-lookup"><span data-stu-id="96017-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="96017-256">È possibile usare la *Visualizza i token* pulsante Mostra/Nascondi per alternare **entità / token visualizzare**!</span><span class="sxs-lookup"><span data-stu-id="96017-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="96017-257">I risultati dovrebbero essere come illustrato nelle immagini seguenti, che mostra le **Entities / token visualizzare**:</span><span class="sxs-lookup"><span data-stu-id="96017-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Viste di entità e i token](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="96017-259">A questo punto premere il **Train** pulsante in alto a destra della pagina e attendere che l'indicatore di arrotondamento piccolo in modo da diventare verde.</span><span class="sxs-lookup"><span data-stu-id="96017-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="96017-260">Ciò indica che LUIS è stato correttamente eseguito il training riconosca questa finalità.</span><span class="sxs-lookup"><span data-stu-id="96017-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Train LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="96017-262">Come esercizio per l'utente, creare una nuova con finalità di chiamata **ChangeObjectSize**, usando le entità *destinazione*, *upsize*, e *ridimensionare*.</span><span class="sxs-lookup"><span data-stu-id="96017-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="96017-263">Seguendo lo stesso processo come l'intento precedente, inserire le seguenti espressioni otto (8) per *dimensioni* modificare:</span><span class="sxs-lookup"><span data-stu-id="96017-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

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

23. <span data-ttu-id="96017-264">Il risultato dovrebbe essere simile a quello nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="96017-264">The result should be like the one in the image below:</span></span>

    ![Configurare i token ChangeObjectSize / entità](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="96017-266">Una volta, entrambe le finalità **ChangeObjectColor** e **ChangeObjectSize**, sono stati creati e sottoposti a training, fare clic sul **PUBLISH** pulsante nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="96017-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Pubblicare il servizio LUIS](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="96017-268">Nel *pubblica* pagina verranno completate e pubblicare l'App LUIS in modo che sia accessibile dal codice.</span><span class="sxs-lookup"><span data-stu-id="96017-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="96017-269">Impostare l'elenco verso il basso *Publish To* come **produzione**.</span><span class="sxs-lookup"><span data-stu-id="96017-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="96017-270">Impostare il *Timezone* nel fuso orario locale.</span><span class="sxs-lookup"><span data-stu-id="96017-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="96017-271">Selezionare la casella **Include tutti i prevista i punteggi di intent**.</span><span class="sxs-lookup"><span data-stu-id="96017-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="96017-272">Fare clic su **pubblicare nello slot di produzione**.</span><span class="sxs-lookup"><span data-stu-id="96017-272">Click on **Publish to Production Slot**.</span></span>

        ![Impostazioni di pubblicazione](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="96017-274">Nella sezione *risorse e le chiavi*:</span><span class="sxs-lookup"><span data-stu-id="96017-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="96017-275">Selezionare l'area che è impostato per l'istanza di servizio nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="96017-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="96017-276">Si noterà una **Starter_Key** elemento riportato di seguito, ignorarlo.</span><span class="sxs-lookup"><span data-stu-id="96017-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="96017-277">Fare clic su **Add Key** e inserire le *chiave* ottenuto nel portale di Azure quando si crea l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="96017-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="96017-278">Se Azure e il portale di LUIS effettuati lo stesso utente, si riceveranno menu a discesa dei *nome del Tenant*, *il nome della sottoscrizione*e il *chiave* si desidera utilizzare ( avrà lo stesso nome come specificato in precedenza nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="96017-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="96017-279">Trova di sotto *Endpoint*, eseguire una copia dell'endpoint corrispondente alla chiave sono stati inseriti, si verrà presto usarla nel codice.</span><span class="sxs-lookup"><span data-stu-id="96017-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="96017-280">Capitolo 3-configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="96017-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="96017-281">Di seguito è una tipica configurato per lo sviluppo con la realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="96017-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="96017-282">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="96017-282">Open *Unity* and click **New**.</span></span> 

    ![Avvio nuovo progetto Unity.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="96017-284">A questo punto si dovrà fornire un nome di progetto Unity, inserire **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="96017-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="96017-285">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="96017-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="96017-286">Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="96017-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="96017-287">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="96017-287">Then, click **Create project**.</span></span>

    ![Fornire i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="96017-289">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="96017-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="96017-290">Scegliere Modifica > Preferenze e dalla nuova finestra, quindi passare al **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="96017-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="96017-291">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="96017-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="96017-292">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="96017-292">Close the **Preferences** window.</span></span>

    ![Aggiornamento delle preferenze dell'editor di script.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="96017-294">Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.</span><span class="sxs-lookup"><span data-stu-id="96017-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crea finestra delle impostazioni, la piattaforma del commutatore alla piattaforma UWP.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="96017-296">Passare a **File > Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="96017-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="96017-297">**Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="96017-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="96017-298">Per il Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="96017-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="96017-299">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="96017-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="96017-300">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="96017-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="96017-301">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="96017-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="96017-302">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="96017-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="96017-303">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="96017-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="96017-304">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="96017-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="96017-305">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="96017-305">A save window will appear.</span></span>
        
            ![Fare clic su Aggiungi pulsante Apri scene](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="96017-307">Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="96017-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crea nuova cartella scripts](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="96017-309">Aprire appena creato **scene** cartella e quindi il *nome File*: campo di testo, digitare **MR_LuisScene**, quindi premere **Salva**.</span><span class="sxs-lookup"><span data-stu-id="96017-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Assegnare un nome nuova scena.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="96017-311">Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="96017-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="96017-312">Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.</span><span class="sxs-lookup"><span data-stu-id="96017-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Aprire le impostazioni del giocatore.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="96017-314">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="96017-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="96017-315">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="96017-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="96017-316">**Versione del Runtime di scripting** deve essere **stabile** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="96017-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="96017-317">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="96017-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="96017-318">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="96017-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aggiornare le altre impostazioni.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="96017-320">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="96017-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="96017-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="96017-321">**InternetClient**</span></span>
        2. <span data-ttu-id="96017-322">**Microfono**</span><span class="sxs-lookup"><span data-stu-id="96017-322">**Microphone**</span></span>

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="96017-324">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="96017-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aggiornare le impostazioni di R X.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="96017-326">Nuovamente in *Build Settings* _Unity C#_  progetti non sono più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="96017-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="96017-327">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="96017-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="96017-328">Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="96017-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="96017-329">Capitolo 4: creazione della scena</span><span class="sxs-lookup"><span data-stu-id="96017-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96017-330">Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importarlo nel progetto come un [pacchetto personalizzato ](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="96017-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="96017-331">Pulsante destro del mouse in un'area vuota del *Pannello di gerarchia*, in **oggetto 3D**, aggiungere un **piano**.</span><span class="sxs-lookup"><span data-stu-id="96017-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Creare un piano.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="96017-333">Tenere presente che quando è fare doppio clic all'interno di *gerarchia* nuovamente per creare più oggetti, se hai ancora l'ultimo oggetto selezionato, l'oggetto selezionato sarà l'elemento padre del nuovo oggetto.</span><span class="sxs-lookup"><span data-stu-id="96017-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="96017-334">Evitare di mouse in uno spazio vuoto all'interno della gerarchia e quindi facendo clic su.</span><span class="sxs-lookup"><span data-stu-id="96017-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="96017-335">Ripetere questa procedura per aggiungere gli oggetti seguenti:</span><span class="sxs-lookup"><span data-stu-id="96017-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="96017-336">*Sfera*</span><span class="sxs-lookup"><span data-stu-id="96017-336">*Sphere*</span></span>
    2. <span data-ttu-id="96017-337">*Cilindro*</span><span class="sxs-lookup"><span data-stu-id="96017-337">*Cylinder*</span></span>
    3. <span data-ttu-id="96017-338">*Cubo*</span><span class="sxs-lookup"><span data-stu-id="96017-338">*Cube*</span></span>
    4. <span data-ttu-id="96017-339">*Testo 3D*</span><span class="sxs-lookup"><span data-stu-id="96017-339">*3D Text*</span></span>

4.  <span data-ttu-id="96017-340">La scena risulta *gerarchia* dovrebbe essere simile a quello nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="96017-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Impostazione di gerarchie di scena.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="96017-342">A sinistra fare clic sul **Main Camera** per selezionarlo, esaminare il *Pannello di controllo* verrà visualizzato l'oggetto della fotocamera con tutti i relativi componenti.</span><span class="sxs-lookup"><span data-stu-id="96017-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="96017-343">Fare clic sui **Add Component** che si trova nella parte inferiore delle *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="96017-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Aggiungi origine Audio](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="96017-345">Ricerca per il componente chiamato *origine Audio*, come illustrato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="96017-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="96017-346">Assicurarsi anche che il *trasformare* componente della fotocamera principale è impostato su (0, 0,0), questa operazione può essere eseguita facendo clic la **a forma di ingranaggio** icona accanto della Camera *trasformare* componente e selezionando **reimpostare**.</span><span class="sxs-lookup"><span data-stu-id="96017-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="96017-347">Il *trasformare* componente sarà quindi simile:</span><span class="sxs-lookup"><span data-stu-id="96017-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="96017-348">*Posizione* è impostata su **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="96017-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="96017-349">*Rotazione* è impostata su **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="96017-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="96017-350">Per il Microsoft HoloLens, sarà necessario modificare anche il comando seguente, che fanno parte del **fotocamera** componente, che è attivata il **Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="96017-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="96017-351">**Cancellare i flag:** Colore a tinta unita.</span><span class="sxs-lookup"><span data-stu-id="96017-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="96017-352">**Sfondo** ' nero, Alpha 0'-colore esadecimale: #00000000.</span><span class="sxs-lookup"><span data-stu-id="96017-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="96017-353">Fare clic sulla **piano** per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="96017-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="96017-354">Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="96017-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="96017-355">Trasformare - *posizione*</span><span class="sxs-lookup"><span data-stu-id="96017-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="96017-356">**X**</span><span class="sxs-lookup"><span data-stu-id="96017-356">**X**</span></span> | <span data-ttu-id="96017-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="96017-357">**Y**</span></span>                  | <span data-ttu-id="96017-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="96017-358">**Z**</span></span> |
    | <span data-ttu-id="96017-359">0</span><span class="sxs-lookup"><span data-stu-id="96017-359">0</span></span>     | <span data-ttu-id="96017-360">-1</span><span class="sxs-lookup"><span data-stu-id="96017-360">-1</span></span>                     | <span data-ttu-id="96017-361">0</span><span class="sxs-lookup"><span data-stu-id="96017-361">0</span></span>     |


10. <span data-ttu-id="96017-362">Fare clic sulla **sfera** per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="96017-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="96017-363">Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="96017-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="96017-364">Trasformare - *posizione*</span><span class="sxs-lookup"><span data-stu-id="96017-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="96017-365">**X**</span><span class="sxs-lookup"><span data-stu-id="96017-365">**X**</span></span> | <span data-ttu-id="96017-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="96017-366">**Y**</span></span>                  | <span data-ttu-id="96017-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="96017-367">**Z**</span></span> |
    | <span data-ttu-id="96017-368">2</span><span class="sxs-lookup"><span data-stu-id="96017-368">2</span></span>     | <span data-ttu-id="96017-369">1</span><span class="sxs-lookup"><span data-stu-id="96017-369">1</span></span>                      | <span data-ttu-id="96017-370">2</span><span class="sxs-lookup"><span data-stu-id="96017-370">2</span></span>     |

11. <span data-ttu-id="96017-371">Fare clic sulla **cilindro** per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="96017-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="96017-372">Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="96017-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="96017-373">Trasformare - *posizione*</span><span class="sxs-lookup"><span data-stu-id="96017-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="96017-374">**X**</span><span class="sxs-lookup"><span data-stu-id="96017-374">**X**</span></span> | <span data-ttu-id="96017-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="96017-375">**Y**</span></span>                  | <span data-ttu-id="96017-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="96017-376">**Z**</span></span> |
    | <span data-ttu-id="96017-377">-2</span><span class="sxs-lookup"><span data-stu-id="96017-377">-2</span></span>    | <span data-ttu-id="96017-378">1</span><span class="sxs-lookup"><span data-stu-id="96017-378">1</span></span>                      | <span data-ttu-id="96017-379">2</span><span class="sxs-lookup"><span data-stu-id="96017-379">2</span></span>     |

12. <span data-ttu-id="96017-380">Fare clic sulla **cubo** per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="96017-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="96017-381">Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="96017-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="96017-382">Trasformare - *posizione*</span><span class="sxs-lookup"><span data-stu-id="96017-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="96017-383">Trasformare - *rotazione*</span><span class="sxs-lookup"><span data-stu-id="96017-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="96017-384">**X**</span><span class="sxs-lookup"><span data-stu-id="96017-384">**X**</span></span> | <span data-ttu-id="96017-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="96017-385">**Y**</span></span>                   | <span data-ttu-id="96017-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="96017-386">**Z**</span></span> |  \| | <span data-ttu-id="96017-387">**X**</span><span class="sxs-lookup"><span data-stu-id="96017-387">**X**</span></span> | <span data-ttu-id="96017-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="96017-388">**Y**</span></span>                  | <span data-ttu-id="96017-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="96017-389">**Z**</span></span> |
    | <span data-ttu-id="96017-390">0</span><span class="sxs-lookup"><span data-stu-id="96017-390">0</span></span>     | <span data-ttu-id="96017-391">1</span><span class="sxs-lookup"><span data-stu-id="96017-391">1</span></span>                       | <span data-ttu-id="96017-392">4</span><span class="sxs-lookup"><span data-stu-id="96017-392">4</span></span>     |  \| | <span data-ttu-id="96017-393">45</span><span class="sxs-lookup"><span data-stu-id="96017-393">45</span></span>    | <span data-ttu-id="96017-394">45</span><span class="sxs-lookup"><span data-stu-id="96017-394">45</span></span>                     | <span data-ttu-id="96017-395">0</span><span class="sxs-lookup"><span data-stu-id="96017-395">0</span></span>     | 

13. <span data-ttu-id="96017-396">Fare clic sulla **nuovo testo** oggetto per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="96017-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="96017-397">Nel *Pannello di controllo* impostare il *trasformare* componente con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="96017-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="96017-398">Trasformare - *posizione*</span><span class="sxs-lookup"><span data-stu-id="96017-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="96017-399">Trasformare - *scalabilità*</span><span class="sxs-lookup"><span data-stu-id="96017-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="96017-400">**X**</span><span class="sxs-lookup"><span data-stu-id="96017-400">**X**</span></span> | <span data-ttu-id="96017-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="96017-401">**Y**</span></span>                  | <span data-ttu-id="96017-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="96017-402">**Z**</span></span> |  \| | <span data-ttu-id="96017-403">**X**</span><span class="sxs-lookup"><span data-stu-id="96017-403">**X**</span></span> | <span data-ttu-id="96017-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="96017-404">**Y**</span></span>               | <span data-ttu-id="96017-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="96017-405">**Z**</span></span> |
    | <span data-ttu-id="96017-406">-2</span><span class="sxs-lookup"><span data-stu-id="96017-406">-2</span></span>    | <span data-ttu-id="96017-407">6</span><span class="sxs-lookup"><span data-stu-id="96017-407">6</span></span>                      | <span data-ttu-id="96017-408">9</span><span class="sxs-lookup"><span data-stu-id="96017-408">9</span></span>     |  \| | <span data-ttu-id="96017-409">0.1</span><span class="sxs-lookup"><span data-stu-id="96017-409">0.1</span></span>   | <span data-ttu-id="96017-410">0.1</span><span class="sxs-lookup"><span data-stu-id="96017-410">0.1</span></span>                 | <span data-ttu-id="96017-411">0.1</span><span class="sxs-lookup"><span data-stu-id="96017-411">0.1</span></span>   | 

14. <span data-ttu-id="96017-412">Change **Font Size** nel **testo Mesh** componente **50**.</span><span class="sxs-lookup"><span data-stu-id="96017-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="96017-413">Modifica il *nome* delle **testo Mesh** oggetto **dettatura testo**.</span><span class="sxs-lookup"><span data-stu-id="96017-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![Creare l'oggetto testo 3D](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="96017-415">La struttura di gerarchia pannello sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="96017-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![testo mesh nella visualizzazione scena](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="96017-417">La scena finale dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="96017-417">The final scene should look like the image below:</span></span>

    ![La visualizzazione di scena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="96017-419">Capitolo 5: creare la classe MicrophoneManager</span><span class="sxs-lookup"><span data-stu-id="96017-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="96017-420">È il primo Script si intende creare il *MicrophoneManager* classe.</span><span class="sxs-lookup"><span data-stu-id="96017-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="96017-421">In seguito, si creerà il *LuisManager*, il *comportamenti* (classe) e infine il *estasiati* (è possibile creare tutti questi ora, ma che verrà trattato come classe raggiungere ogni capitolo).</span><span class="sxs-lookup"><span data-stu-id="96017-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="96017-422">Il *MicrophoneManager* classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="96017-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="96017-423">Rilevamento il dispositivo di registrazione associato a visore VR o machine (a seconda del valore è quello predefinito).</span><span class="sxs-lookup"><span data-stu-id="96017-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="96017-424">Acquisire l'audio (voce) e usare la dettatura per archiviarlo sotto forma di stringa.</span><span class="sxs-lookup"><span data-stu-id="96017-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="96017-425">Dopo la voce è stato sospeso, inviare la dettatura per il *LuisManager* classe.</span><span class="sxs-lookup"><span data-stu-id="96017-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="96017-426">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="96017-426">To create this class:</span></span> 

1.  <span data-ttu-id="96017-427">Fare doppio clic nella *Pannello di progetto*, **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="96017-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="96017-428">Chiamare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="96017-428">Call the folder **Scripts**.</span></span> 

    ![Crea cartella Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="96017-430">Con il **script** cartella creata, fare doppio clic sopra per avviarlo.</span><span class="sxs-lookup"><span data-stu-id="96017-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="96017-431">Quindi, all'interno di tale cartella, pulsante destro del mouse, **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="96017-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="96017-432">Denominare lo script *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="96017-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="96017-433">Fare doppio clic su *MicrophoneManager* per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="96017-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="96017-434">Aggiungere spazi dei nomi seguenti all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="96017-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="96017-435">Quindi aggiungere le variabili seguenti all'interno di *MicrophoneManager* classe:</span><span class="sxs-lookup"><span data-stu-id="96017-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="96017-436">Codice per un *Awake()* e *Start ()* metodi deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="96017-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="96017-437">Questi verranno chiamati quando inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="96017-437">These will be called when the class initializes:</span></span>

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
 
7.  <span data-ttu-id="96017-438">A questo punto è necessario il metodo che l'App Usa per avviare e arrestare l'acquisizione voce e passarlo al *LuisManager* (classe), che verrà compilata a breve.</span><span class="sxs-lookup"><span data-stu-id="96017-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

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

8.  <span data-ttu-id="96017-439">Aggiungere un *dettatura gestore* che verrà richiamato quando la voce viene sospesa.</span><span class="sxs-lookup"><span data-stu-id="96017-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="96017-440">Questo metodo passerà il testo di dettatura dal *LuisManager* classe.</span><span class="sxs-lookup"><span data-stu-id="96017-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

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
    > <span data-ttu-id="96017-441">Eliminare il *Update ()* metodo poiché questa classe non verrà utilizzate.</span><span class="sxs-lookup"><span data-stu-id="96017-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="96017-442">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="96017-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="96017-443">A questo punto si noterà un errore dei *pannello della Console dell'Editor Unity*.</span><span class="sxs-lookup"><span data-stu-id="96017-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="96017-444">Infatti, il codice fa riferimento il *LuisManager* classe che verrà creato nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="96017-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="96017-445">Capitolo 6: creare la classe LUISManager</span><span class="sxs-lookup"><span data-stu-id="96017-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="96017-446">È il momento in cui creare il *LuisManager* classe, che renderà la chiamata al servizio Azure LUIS.</span><span class="sxs-lookup"><span data-stu-id="96017-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="96017-447">Lo scopo di questa classe è per ricevere il testo di dettatura dal *MicrophoneManager* classe e inviarle per il *API di Azure Language Understanding* da analizzare.</span><span class="sxs-lookup"><span data-stu-id="96017-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="96017-448">Eseguirà la deserializzazione di questa classe la *JSON* risposta e chiamare i metodi appropriati della *comportamenti* classe da attivare un'azione.</span><span class="sxs-lookup"><span data-stu-id="96017-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="96017-449">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="96017-449">To create this class:</span></span> 

1.  <span data-ttu-id="96017-450">Fare doppio clic sui **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="96017-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="96017-451">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="96017-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="96017-452">Denominare lo script *LuisManager*.</span><span class="sxs-lookup"><span data-stu-id="96017-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="96017-453">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96017-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="96017-454">Aggiungere spazi dei nomi seguenti all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="96017-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="96017-455">Inizierà creando tre classi **all'interno** il *LuisManager* classe (all'interno del file di script stesso, sopra la *Start ()* (metodo)) che rappresenterà il deserializzati Risposta JSON da Azure.</span><span class="sxs-lookup"><span data-stu-id="96017-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

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

6.  <span data-ttu-id="96017-456">Successivamente, aggiungere le variabili seguenti all'interno di *LuisManager* classe:</span><span class="sxs-lookup"><span data-stu-id="96017-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="96017-457">Assicurarsi di inserire l'endpoint di LUIS in ora (che sarà necessario dal portale di LUIS).</span><span class="sxs-lookup"><span data-stu-id="96017-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="96017-458">Il codice per il *Awake()* metodo deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="96017-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="96017-459">Questo metodo verrà chiamato quando si inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="96017-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="96017-460">È ora necessario i metodi di questa applicazione usa per inviare la dettatura ricevuta dal *MicrophoneManager* classe *LUIS*, quindi ricevere e deserializzare la risposta.</span><span class="sxs-lookup"><span data-stu-id="96017-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="96017-461">Dopo aver determinato il valore della finalità e le entità associate, vengono passati all'istanza del *comportamenti* classe per attivare l'azione desiderata.</span><span class="sxs-lookup"><span data-stu-id="96017-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

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
 
11. <span data-ttu-id="96017-462">Creare un nuovo metodo denominato *AnalyseResponseElements()* che leggerà risultante *AnalysedQuery* e determinare l'entità.</span><span class="sxs-lookup"><span data-stu-id="96017-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="96017-463">Una volta vengono determinate le entità, verranno passate all'istanza del *comportamenti* classe da utilizzare nelle azioni.</span><span class="sxs-lookup"><span data-stu-id="96017-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

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

            // Depending on the topmost recognised intent, read the entities name
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
    > <span data-ttu-id="96017-464">Eliminare il *Start ()* e *Update ()* poiché questa classe non verrà utilizzati i metodi.</span><span class="sxs-lookup"><span data-stu-id="96017-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="96017-465">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="96017-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="96017-466">A questo punto noterai che diversi errori dei *pannello della Console dell'Editor Unity*.</span><span class="sxs-lookup"><span data-stu-id="96017-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="96017-467">Infatti, il codice fa riferimento il *comportamenti* classe che verrà creato nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="96017-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="96017-468">Capitolo 7: creare la classe di comportamenti</span><span class="sxs-lookup"><span data-stu-id="96017-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="96017-469">Il *comportamenti* classe attiverà le azioni con l'entità fornita dalle *LuisManager* classe.</span><span class="sxs-lookup"><span data-stu-id="96017-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="96017-470">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="96017-470">To create this class:</span></span> 

1.  <span data-ttu-id="96017-471">Fare doppio clic sui **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="96017-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="96017-472">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="96017-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="96017-473">Denominare lo script *comportamenti*.</span><span class="sxs-lookup"><span data-stu-id="96017-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="96017-474">Fare doppio clic sullo script per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="96017-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="96017-475">Quindi aggiungere le variabili seguenti all'interno di *comportamenti* classe:</span><span class="sxs-lookup"><span data-stu-id="96017-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="96017-476">Aggiungere il *Awake()* codice del metodo.</span><span class="sxs-lookup"><span data-stu-id="96017-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="96017-477">Questo metodo verrà chiamato quando si inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="96017-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="96017-478">I seguenti metodi vengono chiamati i *LuisManager* classe (che è stato creato in precedenza) per determinare l'oggetto di destinazione della query e quindi attivare l'azione appropriata.</span><span class="sxs-lookup"><span data-stu-id="96017-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

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
 
7.  <span data-ttu-id="96017-479">Aggiungere il *FindTarget()* metodo per determinare quali le *Gameobject* è la destinazione delle finalità corrente.</span><span class="sxs-lookup"><span data-stu-id="96017-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="96017-480">Questo metodo di impostazione predefinita è la destinazione per il *GameObject* in corso "gazed" Se non viene definita alcuna destinazione esplicite nelle entità.</span><span class="sxs-lookup"><span data-stu-id="96017-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
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
    > <span data-ttu-id="96017-481">Eliminare il *Start ()* e *Update ()* poiché questa classe non verrà utilizzati i metodi.</span><span class="sxs-lookup"><span data-stu-id="96017-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="96017-482">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="96017-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="96017-483">Capitolo 8: creare la classe sguardo</span><span class="sxs-lookup"><span data-stu-id="96017-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="96017-484">La classe ultimo che è necessario per completare questa app è il *estasiati* classe.</span><span class="sxs-lookup"><span data-stu-id="96017-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="96017-485">Questa classe aggiorna il riferimento di *GameObject* attualmente in visivi dello stato attivo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="96017-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="96017-486">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="96017-486">To create this Class:</span></span> 

1.  <span data-ttu-id="96017-487">Fare doppio clic sui **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="96017-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="96017-488">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="96017-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="96017-489">Denominare lo script *estasiati*.</span><span class="sxs-lookup"><span data-stu-id="96017-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="96017-490">Fare doppio clic sullo script per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="96017-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="96017-491">Inserire il codice seguente per questa classe:</span><span class="sxs-lookup"><span data-stu-id="96017-491">Insert the following code for this class:</span></span>

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
 
5.  <span data-ttu-id="96017-492">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="96017-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="96017-493">Capitolo 9: completamento dell'installazione di scena</span><span class="sxs-lookup"><span data-stu-id="96017-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="96017-494">Per completare l'installazione della scena, trascinare ogni script che sono creati dalla cartella degli script per il **Main Camera** dell'oggetto nel *gerarchia pannello*.</span><span class="sxs-lookup"><span data-stu-id="96017-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="96017-495">Selezionare il **Main Camera** ed esaminare le *Pannello di controllo*, dovrebbe essere possibile per ogni script che sono stati connessi e si noterà che esistono parametri che devono ancora essere impostato su ogni script.</span><span class="sxs-lookup"><span data-stu-id="96017-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![L'impostazione delle destinazioni di riferimento della fotocamera.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="96017-497">Per impostare questi parametri in modo corretto, seguire queste istruzioni:</span><span class="sxs-lookup"><span data-stu-id="96017-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="96017-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="96017-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="96017-499">Dal *Pannello di gerarchia*, trascinare il **dettatura testo** nell'oggetto il **dettatura testo** casella di valore del parametro.</span><span class="sxs-lookup"><span data-stu-id="96017-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="96017-500">*Comportamenti*, dal *gerarchia pannello*:</span><span class="sxs-lookup"><span data-stu-id="96017-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="96017-501">Trascinare il **sfera** all'oggetto il *sfera* la destinazione di riferimento.</span><span class="sxs-lookup"><span data-stu-id="96017-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="96017-502">Trascinare il **cilindro** nel *cilindro* la destinazione di riferimento.</span><span class="sxs-lookup"><span data-stu-id="96017-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="96017-503">Trascinare il **cubo** nel *cubo* la destinazione di riferimento.</span><span class="sxs-lookup"><span data-stu-id="96017-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="96017-504">*Estasiati*:</span><span class="sxs-lookup"><span data-stu-id="96017-504">*Gaze*:</span></span>

        - <span data-ttu-id="96017-505">Impostare il *estasiati distanza massima* al **300** (se non è già).</span><span class="sxs-lookup"><span data-stu-id="96017-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="96017-506">Il risultato dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="96017-506">The result should look like the image below:</span></span>

    ![Ora che mostra le destinazioni di riferimento della fotocamera, impostare.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="96017-508">Capitolo 10: Test nell'Editor di Unity</span><span class="sxs-lookup"><span data-stu-id="96017-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="96017-509">Verificare che il programma di installazione di scena sia implementato correttamente.</span><span class="sxs-lookup"><span data-stu-id="96017-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="96017-510">Verifica che:</span><span class="sxs-lookup"><span data-stu-id="96017-510">Ensure that:</span></span>

-   <span data-ttu-id="96017-511">Tutti gli script associati per il **Main Camera** oggetto.</span><span class="sxs-lookup"><span data-stu-id="96017-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="96017-512">Tutti i campi di *Pannello controllo fotocamera principale* vengono assegnati in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="96017-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="96017-513">Premere il **riprodurre** pulsante il *Editor di Unity*.</span><span class="sxs-lookup"><span data-stu-id="96017-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="96017-514">L'App dovrebbe essere eseguito all'interno di visore VR immersivi collegati.</span><span class="sxs-lookup"><span data-stu-id="96017-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="96017-515">Provare alcune espressioni, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="96017-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="96017-516">Se viene visualizzato un errore nella console di Unity sul dispositivo audio predefinito modifica, la scena potrebbe non funzionare come previsto.</span><span class="sxs-lookup"><span data-stu-id="96017-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="96017-517">Ciò è dovuto al modo in cui che il portale di realtà mista si occupa microfoni incorporati per auricolari sia disponibile.</span><span class="sxs-lookup"><span data-stu-id="96017-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="96017-518">Se è visualizzato questo errore, è sufficiente arrestare la scena e avviarla nuovamente e cose dovrebbero funzionare come previsto.</span><span class="sxs-lookup"><span data-stu-id="96017-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="96017-519">Capitolo 11: compilazione e trasferire localmente la soluzione di piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="96017-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="96017-520">Dopo aver verificato che l'applicazione funziona nell'Editor di Unity, si è pronti per compilare e distribuire.</span><span class="sxs-lookup"><span data-stu-id="96017-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="96017-521">Per compilare:</span><span class="sxs-lookup"><span data-stu-id="96017-521">To Build:</span></span>

1.  <span data-ttu-id="96017-522">Salvare nella scena corrente facendo clic su **File > Salva**.</span><span class="sxs-lookup"><span data-stu-id="96017-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="96017-523">Passare a **File > Impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="96017-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="96017-524">Selezionare la casella denominata **Unity C# progetti** (utile per la visualizzazione e debug del codice dopo aver creato il progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="96017-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="96017-525">Fare clic su **aggiungere scene Open**, quindi fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="96017-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Finestra delle impostazioni di compilazione](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="96017-527">Viene chiesto di selezionare la cartella in cui si desidera compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="96017-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="96017-528">Creare un *COMPILAZIONI* cartella e all'interno della cartella creare un'altra cartella con un nome appropriato di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="96017-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="96017-529">Fare clic su **selezionare la cartella** per avviare la compilazione nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="96017-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="96017-530">![Crea cartella Compilazioni](images/AzureLabs-Lab3-44.png)
    ![selezionare Crea cartella](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="96017-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="96017-531">Una volta Unity ha terminato (potrebbe richiedere alcuni minuti) predefiniti, dovrebbe aprirsi una **Esplora File** finestra in corrispondenza della posizione della compilazione.</span><span class="sxs-lookup"><span data-stu-id="96017-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="96017-532">Per distribuire nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="96017-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="96017-533">Nelle *Visual Studio*, aprire il file di soluzione che è stato creato nel [capitolo precedente](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="96017-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="96017-534">Nel **piattaforma soluzione**, selezionare **x86**, **macchina locale**.</span><span class="sxs-lookup"><span data-stu-id="96017-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="96017-535">Nel **configurazione della soluzione** selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="96017-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="96017-536">Per il Microsoft HoloLens, può risultare più semplice impostare questa opzione su *computer remoto*, in modo che non Windows con tethering al computer in uso.</span><span class="sxs-lookup"><span data-stu-id="96017-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="96017-537">Tuttavia, è necessario inoltre eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="96017-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="96017-538">Conoscere il **indirizzo IP** di HoloLens, il che può trovarsi all'interno di *Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo è consigliabile usare.</span><span class="sxs-lookup"><span data-stu-id="96017-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="96017-539">Assicurarsi **modalità sviluppatore** viene **sul**; è stata trovata nel *Impostazioni > aggiornamento e sicurezza > per gli sviluppatori*.</span><span class="sxs-lookup"><span data-stu-id="96017-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Distribuire App](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="96017-541">Andare alla **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.</span><span class="sxs-lookup"><span data-stu-id="96017-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="96017-542">L'App deve vengono ora visualizzati nell'elenco delle App installate, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="96017-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="96017-543">Una volta avviata, l'App verrà richiesto di autorizzare l'accesso per il _microfono_.</span><span class="sxs-lookup"><span data-stu-id="96017-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="96017-544">Usare il *controller di movimento*, o *Input vocale*, o il *tastiera* necessario premere il **Sì** pulsante.</span><span class="sxs-lookup"><span data-stu-id="96017-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="96017-545">Capitolo 12: migliorare il servizio LUIS</span><span class="sxs-lookup"><span data-stu-id="96017-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="96017-546">In questo capitolo è molto importante e potrebbe essere necessario scorrere su più volte, evitare di migliorare l'accuratezza del servizio LUIS: verificare di aver completato questa.</span><span class="sxs-lookup"><span data-stu-id="96017-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="96017-547">Per migliorare il livello di informazioni fornite da LUIS è necessario acquisire nuove espressioni e usarli per ripetere il training dell'App LUIS.</span><span class="sxs-lookup"><span data-stu-id="96017-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="96017-548">Ad esempio, si potrebbe aver eseguito il training LUIS per comprendere "Increase" e "Ci", ma non si vuole che l'app anche per comprendere parole come "Ingrandisci"?</span><span class="sxs-lookup"><span data-stu-id="96017-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="96017-549">Dopo aver usato l'applicazione più volte, tutto ciò che avrebbe dovuto dirlo verranno raccolti dal servizio LUIS e disponibili nel portale di LUIS.</span><span class="sxs-lookup"><span data-stu-id="96017-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="96017-550">Passare all'applicazione del portale seguendo questa [collegamento](https://www.luis.ai/home)e nel Log.</span><span class="sxs-lookup"><span data-stu-id="96017-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="96017-551">Una volta che si è connessi con le Credentials MS, fare clic sui *nome App*.</span><span class="sxs-lookup"><span data-stu-id="96017-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="96017-552">Scegliere il **esaminare utterances endpoint** pulsante a sinistra della pagina.</span><span class="sxs-lookup"><span data-stu-id="96017-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Espressioni di revisione](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="96017-554">Si verrà visualizzato un elenco di espressioni che sono state inviate al servizio LUIS per le applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="96017-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Elenco di espressioni](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="96017-556">Noteranno alcune evidenziato *Entities*.</span><span class="sxs-lookup"><span data-stu-id="96017-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="96017-557">Passando il puntatore del mouse su ogni parola evidenziata, è possibile esaminare ogni Utterance e determinare quali entità è stato riconosciuto correttamente, quali entità sono errate e quali non sono presenti entità.</span><span class="sxs-lookup"><span data-stu-id="96017-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="96017-558">Nell'esempio precedente, è emerso che era stata evidenziata la parola "spear" come destinazione, pertanto è necessario correggere l'errore, questa operazione viene eseguita al passaggio del mouse sulla parola con il mouse e scegliendo **Rimuovi etichetta**.</span><span class="sxs-lookup"><span data-stu-id="96017-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="96017-559">![Controllare utterances](images/AzureLabs-Lab3-49.png)
![Rimuovi etichetta immagine](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="96017-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="96017-560">Se si ritiene di espressioni che non sono completamente errate, è possibile eliminarli usando il **eliminare** pulsante sul lato destro dello schermo.</span><span class="sxs-lookup"><span data-stu-id="96017-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Elimina utterances errato](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="96017-562">O se si ritiene che LUIS ha interpretato il Utterance correttamente, è possibile convalidare la comprensione utilizzando il **Aggiungi a allineato con finalità di** pulsante.</span><span class="sxs-lookup"><span data-stu-id="96017-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Aggiungere finalità allineato](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="96017-564">Dopo aver ordinato tutte le espressioni visualizzate, provare e ricaricare la pagina per verificare se informazioni sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="96017-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="96017-565">È molto importante ripetere questo processo le volte che è possibile migliorare la comprensione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="96017-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="96017-566">**Buon divertimento!**</span><span class="sxs-lookup"><span data-stu-id="96017-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="96017-567">L'applicazione LUIS integrata completata</span><span class="sxs-lookup"><span data-stu-id="96017-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="96017-568">Complimenti, è stata compilata un'app per realtà mista che sfrutta Azure Language Understanding Intelligence Service, per comprendere ciò che viene visualizzato un utente e agire su tali informazioni.</span><span class="sxs-lookup"><span data-stu-id="96017-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![risultato di Lab](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="96017-570">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="96017-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="96017-571">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="96017-571">Exercise 1</span></span>

<span data-ttu-id="96017-572">Quando si usa questa applicazione è possibile notare che se si fissare oggetto Floor e richiedere di modificare il colore, verranno eseguite in modo.</span><span class="sxs-lookup"><span data-stu-id="96017-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="96017-573">È possibile usare le modalità arrestare l'applicazione di modificare il colore della base?</span><span class="sxs-lookup"><span data-stu-id="96017-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="96017-574">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="96017-574">Exercise 2</span></span>

<span data-ttu-id="96017-575">Provare a estendere le funzionalità di LUIS e App, aggiunta di funzionalità aggiuntive per gli oggetti nella scena; ad esempio, creare nuovi oggetti alla sguardo punto hit, a seconda di ciò che l'utente indicato e quindi essere in grado di utilizzare tali oggetti insieme a oggetti di scena corrente, con i comandi esistenti.</span><span class="sxs-lookup"><span data-stu-id="96017-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
