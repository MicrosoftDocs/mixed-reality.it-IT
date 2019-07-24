---
title: MR e Azure 301-traduzione in lingua
description: Completare questo corso per apprendere come implementare il API Traduzione testuale di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, traduzione testuale, hololens, immersiva, VR
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554018"
---
>[!NOTE]
><span data-ttu-id="8d442-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="8d442-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8d442-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="8d442-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8d442-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8d442-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8d442-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="8d442-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8d442-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8d442-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8d442-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="8d442-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="8d442-110">MR e Azure 301: Traduzioni</span><span class="sxs-lookup"><span data-stu-id="8d442-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="8d442-111">In questo corso si apprenderà come aggiungere funzionalità di traduzione a un'applicazione di realtà mista usando servizi cognitivi di Azure, con il API Traduzione testuale.</span><span class="sxs-lookup"><span data-stu-id="8d442-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Prodotto finale](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="8d442-113">Il API Traduzione testuale è un servizio di traduzione che funziona quasi in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="8d442-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="8d442-114">Il servizio è basato sul cloud e, usando una chiamata API REST, un'app può usare la tecnologia di traduzione dei computer neurali per tradurre il testo in un'altra lingua.</span><span class="sxs-lookup"><span data-stu-id="8d442-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="8d442-115">Per ulteriori informazioni, visitare la [pagina API traduzione testuale di Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="8d442-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="8d442-116">Al termine di questo corso, sarà disponibile un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="8d442-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="8d442-117">L'utente parlerà di un microfono connesso a un headset immersivo (VR) o del microfono incorporato di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8d442-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="8d442-118">L'app acquisisce la dettatura e la invia al API Traduzione testuale di Azure.</span><span class="sxs-lookup"><span data-stu-id="8d442-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="8d442-119">Il risultato della conversione verrà visualizzato in un gruppo di interfaccia utente semplice nella scena Unity.</span><span class="sxs-lookup"><span data-stu-id="8d442-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="8d442-120">Questo corso spiegherà come ottenere i risultati dal servizio di conversione in un'applicazione di esempio basata su Unity.</span><span class="sxs-lookup"><span data-stu-id="8d442-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="8d442-121">Sarà necessario applicare questi concetti a un'applicazione personalizzata che è possibile creare.</span><span class="sxs-lookup"><span data-stu-id="8d442-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="8d442-122">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="8d442-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8d442-123">Corso</span><span class="sxs-lookup"><span data-stu-id="8d442-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8d442-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8d442-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8d442-125"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="8d442-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="8d442-126">MR e Azure 301: Traduzioni</span><span class="sxs-lookup"><span data-stu-id="8d442-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="8d442-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8d442-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8d442-128">✔️</span><span class="sxs-lookup"><span data-stu-id="8d442-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="8d442-129">Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8d442-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="8d442-130">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8d442-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="8d442-131">Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.</span><span class="sxs-lookup"><span data-stu-id="8d442-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d442-132">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="8d442-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="8d442-133">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="8d442-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="8d442-134">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="8d442-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="8d442-135">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="8d442-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="8d442-136">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="8d442-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="8d442-137">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="8d442-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="8d442-138">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="8d442-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8d442-139">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="8d442-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8d442-140">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="8d442-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8d442-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8d442-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="8d442-142">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="8d442-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="8d442-143">Un set di cuffie con un microfono incorporato (se la cuffia non dispone di un MIC e di altoparlanti predefiniti)</span><span class="sxs-lookup"><span data-stu-id="8d442-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="8d442-144">Accesso a Internet per l'installazione e il recupero della traduzione in Azure</span><span class="sxs-lookup"><span data-stu-id="8d442-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="8d442-145">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="8d442-145">Before you start</span></span>

- <span data-ttu-id="8d442-146">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="8d442-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="8d442-147">Il codice in questa esercitazione consentirà di registrare dal dispositivo microfono predefinito connesso al PC.</span><span class="sxs-lookup"><span data-stu-id="8d442-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="8d442-148">Verificare che il dispositivo microfonico predefinito sia impostato sul dispositivo che si intende usare per acquisire la voce.</span><span class="sxs-lookup"><span data-stu-id="8d442-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="8d442-149">Per consentire al PC di abilitare la dettatura, passare a **impostazioni > Privacy > vocale, Inking &** digitando e selezionare il pulsante **Attiva servizi vocali e digitando suggerimenti**.</span><span class="sxs-lookup"><span data-stu-id="8d442-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="8d442-150">Se si usa un microfono e cuffie connesse a (o incorporata), assicurarsi che l'opzione "quando si indossa la cuffia, passa alla cuffia auricolare" sia attivata in **impostazioni > realtà mista > audio e sintesi vocale**.</span><span class="sxs-lookup"><span data-stu-id="8d442-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Impostazioni della realtà mista](images/AzureLabs-Lab1-00-5.png)

   ![Impostazione del microfono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="8d442-153">Si tenga presente che, se si sta sviluppando per un auricolare immersivo per questo Lab, è possibile che si verifichino problemi di dispositivo di output audio.</span><span class="sxs-lookup"><span data-stu-id="8d442-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="8d442-154">Ciò è dovuto a un problema di Unity, che è stato risolto nelle versioni successive di Unity (Unity 2018,2).</span><span class="sxs-lookup"><span data-stu-id="8d442-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="8d442-155">Il problema impedisce a Unity di modificare il dispositivo di output audio predefinito in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8d442-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="8d442-156">Per risolvere il problema, assicurarsi di aver completato i passaggi precedenti, quindi chiudere e riaprire l'editor quando si presenta questo problema.</span><span class="sxs-lookup"><span data-stu-id="8d442-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="8d442-157">Capitolo 1: portale di Azure</span><span class="sxs-lookup"><span data-stu-id="8d442-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="8d442-158">Per usare l'API di Azure translator, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8d442-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="8d442-159">Accedere al portale di [Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="8d442-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d442-160">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="8d442-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="8d442-161">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="8d442-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="8d442-162">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare "API traduzione testuale".</span><span class="sxs-lookup"><span data-stu-id="8d442-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="8d442-163">Premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="8d442-163">Select **Enter**.</span></span>

    ![Nuova risorsa](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="8d442-165">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="8d442-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="8d442-166">La nuova pagina fornirà una descrizione del servizio *API traduzione testuale* .</span><span class="sxs-lookup"><span data-stu-id="8d442-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="8d442-167">Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="8d442-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Crea servizio API Traduzione testuale](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="8d442-169">Una volta fatto clic su **Crea**:</span><span class="sxs-lookup"><span data-stu-id="8d442-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="8d442-170">Inserire il **nome** desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="8d442-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="8d442-171">Selezionare una **sottoscrizione**appropriata.</span><span class="sxs-lookup"><span data-stu-id="8d442-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="8d442-172">Selezionare il  piano tariffario appropriato. se è la prima volta che si crea un *servizio di traduzione testuale*, è necessario che sia disponibile un livello gratuito (denominato F0).</span><span class="sxs-lookup"><span data-stu-id="8d442-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="8d442-173">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="8d442-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8d442-174">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="8d442-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8d442-175">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="8d442-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="8d442-176">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="8d442-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="8d442-177">Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="8d442-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="8d442-178">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8d442-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="8d442-179">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="8d442-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="8d442-180">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="8d442-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="8d442-181">Selezionare **Create**.</span><span class="sxs-lookup"><span data-stu-id="8d442-181">Select **Create**.</span></span>

        ![Fare clic sul pulsante Crea.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="8d442-183">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="8d442-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="8d442-184">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="8d442-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Notifica di creazione del servizio di Azure](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="8d442-186">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="8d442-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Passare a finestra popup risorsa.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="8d442-188">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="8d442-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="8d442-189">Si verrà portati alla nuova istanza del servizio API Traduzione testuale.</span><span class="sxs-lookup"><span data-stu-id="8d442-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Pagina servizio API Traduzione testuale](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="8d442-191">All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita usando la chiave di sottoscrizione del servizio.</span><span class="sxs-lookup"><span data-stu-id="8d442-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="8d442-192">Dalla pagina *avvio rapido* del servizio *traduzione testuale* passare al primo passaggio, recuperare *le chiavi*e fare clic su **chiavi** . a tale scopo, fare clic sui tasti di collegamento ipertestuale blu disponibili nel menu di navigazione servizi, indicato dall'icona della chiave).</span><span class="sxs-lookup"><span data-stu-id="8d442-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="8d442-193">Le *chiavi*del servizio vengono rivelate.</span><span class="sxs-lookup"><span data-stu-id="8d442-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="8d442-194">Eseguire una copia di una delle chiavi visualizzate, perché sarà necessario in un secondo momento nel progetto.</span><span class="sxs-lookup"><span data-stu-id="8d442-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="8d442-195">Capitolo 2: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="8d442-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="8d442-196">Configurare e testare l'auricolare immersiva della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="8d442-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="8d442-197">Non sarà necessario alcun controller di movimento per questo corso.</span><span class="sxs-lookup"><span data-stu-id="8d442-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="8d442-198">Se è necessario supporto per la configurazione di un auricolare immersivo, [attenersi alla seguente procedura](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="8d442-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="8d442-199">Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, è un modello valido per altri progetti:</span><span class="sxs-lookup"><span data-stu-id="8d442-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="8d442-200">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="8d442-200">Open *Unity* and click **New**.</span></span> 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="8d442-202">A questo punto sarà necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="8d442-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="8d442-203">Inserire **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="8d442-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="8d442-204">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="8d442-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="8d442-205">Impostare il *percorso* su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="8d442-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="8d442-206">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="8d442-206">Then, click **Create project**.</span></span>

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="8d442-208">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8d442-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="8d442-209">Passare a **Modifica preferenze >** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="8d442-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="8d442-210">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="8d442-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="8d442-211">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="8d442-211">Close the **Preferences** window.</span></span>

    ![Aggiornare la preferenza dell'editor di script.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="8d442-213">Passare quindi a **File > impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="8d442-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Finestra impostazioni di compilazione, passa alla piattaforma UWP.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="8d442-215">Passare a **File > impostazioni di compilazione** e verificare che:</span><span class="sxs-lookup"><span data-stu-id="8d442-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="8d442-216">Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="8d442-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="8d442-217">Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="8d442-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="8d442-218">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="8d442-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="8d442-219">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="8d442-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="8d442-220">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="8d442-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="8d442-221">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="8d442-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="8d442-222">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="8d442-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="8d442-223">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="8d442-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="8d442-224">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="8d442-224">A save window will appear.</span></span>

            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="8d442-226">Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.</span><span class="sxs-lookup"><span data-stu-id="8d442-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crea nuova cartella script](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="8d442-228">Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **MR_TranslationScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="8d442-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="8d442-230">Tenere presente che è necessario salvare le scene Unity all'  interno della cartella assets, in quanto devono essere associate al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="8d442-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="8d442-231">La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="8d442-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="8d442-232">Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="8d442-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="8d442-233">Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .</span><span class="sxs-lookup"><span data-stu-id="8d442-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="8d442-235">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="8d442-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="8d442-236">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="8d442-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="8d442-237">La **versione di runtime** di scripting deve essere **stabile** (equivalente a .NET 3,5).</span><span class="sxs-lookup"><span data-stu-id="8d442-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="8d442-238">Il **back-end** di scripting deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="8d442-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="8d442-239">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="8d442-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="8d442-241">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="8d442-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="8d442-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="8d442-242">**InternetClient**</span></span>
        2. <span data-ttu-id="8d442-243">**Microfono**</span><span class="sxs-lookup"><span data-stu-id="8d442-243">**Microphone**</span></span>

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="8d442-245">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="8d442-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aggiornare le impostazioni X R.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="8d442-247">Nelle **impostazioni di compilazione**, *i C# progetti Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="8d442-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="8d442-248">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="8d442-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="8d442-249">Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="8d442-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="8d442-250">Capitolo 3-configurazione della fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="8d442-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d442-251">Se si desidera ignorare il componente *di configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile [scaricarlo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importarlo nel progetto come [*pacchetto personalizzato*](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="8d442-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="8d442-252">Sarà comunque necessario creare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="8d442-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="8d442-253">Nel *Pannello gerarchia*è presente un oggetto denominato **Main camera**, che rappresenta il punto di visualizzazione "Head" dopo che l'applicazione è stata "interna".</span><span class="sxs-lookup"><span data-stu-id="8d442-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="8d442-254">Con il dashboard Unity in primo piano, selezionare la **fotocamera principale GameObject**.</span><span class="sxs-lookup"><span data-stu-id="8d442-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="8d442-255">Si noterà che il *pannello Inspector* , disponibile in genere a destra, all'interno del dashboard, visualizzerà i vari componenti di tale *GameObject*, con la *trasformazione* nella parte superiore, seguita dalla *fotocamera*e da altri componenti.</span><span class="sxs-lookup"><span data-stu-id="8d442-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="8d442-256">Sarà necessario reimpostare la trasformazione della fotocamera principale, in modo che venga posizionata correttamente.</span><span class="sxs-lookup"><span data-stu-id="8d442-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="8d442-257">A tale scopo, selezionare l'  icona dell'ingranaggio accanto al componente *trasformazione* della fotocamera e selezionare **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="8d442-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Reimposta la trasformazione della fotocamera principale.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="8d442-259">Il componente *Transform* dovrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="8d442-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="8d442-260">La *posizione* è impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="8d442-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="8d442-261">*Rotation* è impostato su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="8d442-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="8d442-262">E  la scalabilità è impostata su **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="8d442-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Trasforma informazioni per la fotocamera](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="8d442-264">Quindi, con l'oggetto **principale della fotocamera** selezionato, vedere il pulsante **Aggiungi componente** che si trova nella parte inferiore del *pannello Inspector*.</span><span class="sxs-lookup"><span data-stu-id="8d442-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="8d442-265">Selezionare tale pulsante e cercare (digitando *origine audio* nel campo di ricerca o spostandosi nelle sezioni) per il componente denominato **origine audio** , come illustrato di seguito, e selezionarlo (premendo invio anche in questo caso).</span><span class="sxs-lookup"><span data-stu-id="8d442-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="8d442-266">Un componente di *origine audio* verrà aggiunto alla **fotocamera principale**, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="8d442-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Aggiungere un componente di origine audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="8d442-268">Per Microsoft HoloLens, è necessario modificare anche quanto segue, che fa parte del componente della **fotocamera** della **fotocamera principale**:</span><span class="sxs-lookup"><span data-stu-id="8d442-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="8d442-269">**Cancella flag:** Colore a tinta unita.</span><span class="sxs-lookup"><span data-stu-id="8d442-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="8d442-270">**Informazioni preliminari** ' Black, Alpha 0'-colore esadecimale: #00000000.</span><span class="sxs-lookup"><span data-stu-id="8d442-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="8d442-271">Capitolo 4: installazione dell'area di disegno debug</span><span class="sxs-lookup"><span data-stu-id="8d442-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="8d442-272">Per visualizzare l'input e l'output della traduzione, è necessario creare un'interfaccia utente di base.</span><span class="sxs-lookup"><span data-stu-id="8d442-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="8d442-273">Per questo corso, verrà creato un oggetto dell'interfaccia utente Canvas con diversi oggetti ' text ' per visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="8d442-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="8d442-274">Fare clic con il pulsante destro del mouse in un'area vuota del *Pannello gerarchia*, in **interfaccia utente**, Aggiungi un'area di **disegno**.</span><span class="sxs-lookup"><span data-stu-id="8d442-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Aggiungere un nuovo oggetto interfaccia utente Canvas.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="8d442-276">Con l'oggetto Canvas selezionato, nel *pannello Inspector* (nel componente "canvas") modificare la modalità di **rendering** in **spazio globale**.</span><span class="sxs-lookup"><span data-stu-id="8d442-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="8d442-277">Modificare quindi i parametri seguenti nella *trasformazione Rect del pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="8d442-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="8d442-278">*POS*    X 0 Y 0 Z 40 -  </span><span class="sxs-lookup"><span data-stu-id="8d442-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="8d442-279">*Larghezza* -500</span><span class="sxs-lookup"><span data-stu-id="8d442-279">*Width* -    500</span></span>
    3. <span data-ttu-id="8d442-280">*Altezza* -300</span><span class="sxs-lookup"><span data-stu-id="8d442-280">*Height* -   300</span></span>
    4. <span data-ttu-id="8d442-281">*Scala*    X 0,13 Y 0,13 Z 0,13 - </span><span class="sxs-lookup"><span data-stu-id="8d442-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Aggiornare la trasformazione Rect per l'area di disegno.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="8d442-283">Fare clic con il pulsante destro del mouse sull' **area di disegno** nel *Pannello gerarchia*, in **interfaccia utente**e aggiungere un **Pannello**.</span><span class="sxs-lookup"><span data-stu-id="8d442-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="8d442-284">Questo **Pannello** fornirà uno sfondo al testo che verrà visualizzato nella scena.</span><span class="sxs-lookup"><span data-stu-id="8d442-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="8d442-285">Fare clic con il pulsante destro del mouse sul **Pannello nel** *Pannello gerarchia*in **interfaccia utente**e aggiungere un **oggetto testo**.</span><span class="sxs-lookup"><span data-stu-id="8d442-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="8d442-286">Ripetere lo stesso processo fino a quando non sono stati creati quattro oggetti testo dell'interfaccia utente in totale (Suggerimento: se è stato selezionato il primo oggetto ' text ', è possibile premere **' Ctrl ' + d''** per duplicarlo, fino a quando non si dispone di quattro in totale).</span><span class="sxs-lookup"><span data-stu-id="8d442-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="8d442-287">Per ogni **oggetto testo**, selezionarlo e utilizzare le tabelle seguenti per impostare i parametri nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="8d442-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="8d442-288">Per il componente di *trasformazione Rect* :</span><span class="sxs-lookup"><span data-stu-id="8d442-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="8d442-289">Nome</span><span class="sxs-lookup"><span data-stu-id="8d442-289">Name</span></span>                   | <span data-ttu-id="8d442-290">Trasformazione- *posizione*</span><span class="sxs-lookup"><span data-stu-id="8d442-290">Transform - *Position*</span></span>             | <span data-ttu-id="8d442-291">Larghezza</span><span class="sxs-lookup"><span data-stu-id="8d442-291">Width</span></span>      | <span data-ttu-id="8d442-292">Altezza</span><span class="sxs-lookup"><span data-stu-id="8d442-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="8d442-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="8d442-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="8d442-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="8d442-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="8d442-295">300</span><span class="sxs-lookup"><span data-stu-id="8d442-295">300</span></span>        | <span data-ttu-id="8d442-296">30</span><span class="sxs-lookup"><span data-stu-id="8d442-296">30</span></span>        |
        | <span data-ttu-id="8d442-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="8d442-297">AzureResponseLabel</span></span>     | <span data-ttu-id="8d442-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="8d442-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="8d442-299">300</span><span class="sxs-lookup"><span data-stu-id="8d442-299">300</span></span>        | <span data-ttu-id="8d442-300">30</span><span class="sxs-lookup"><span data-stu-id="8d442-300">30</span></span>        |
        | <span data-ttu-id="8d442-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="8d442-301">DictationLabel</span></span>         | <span data-ttu-id="8d442-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="8d442-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="8d442-303">300</span><span class="sxs-lookup"><span data-stu-id="8d442-303">300</span></span>        | <span data-ttu-id="8d442-304">30</span><span class="sxs-lookup"><span data-stu-id="8d442-304">30</span></span>        |
        | <span data-ttu-id="8d442-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="8d442-305">TranslationResultLabel</span></span> | <span data-ttu-id="8d442-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="8d442-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="8d442-307">300</span><span class="sxs-lookup"><span data-stu-id="8d442-307">300</span></span>        | <span data-ttu-id="8d442-308">30</span><span class="sxs-lookup"><span data-stu-id="8d442-308">30</span></span>        |


    2. <span data-ttu-id="8d442-309">Per il componente **testo (script)** :</span><span class="sxs-lookup"><span data-stu-id="8d442-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="8d442-310">Name</span><span class="sxs-lookup"><span data-stu-id="8d442-310">Name</span></span>                   | <span data-ttu-id="8d442-311">Testo</span><span class="sxs-lookup"><span data-stu-id="8d442-311">Text</span></span>               | <span data-ttu-id="8d442-312">Dimensione carattere</span><span class="sxs-lookup"><span data-stu-id="8d442-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="8d442-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="8d442-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="8d442-314">Stato microfono:</span><span class="sxs-lookup"><span data-stu-id="8d442-314">Microphone Status:</span></span> | <span data-ttu-id="8d442-315">20</span><span class="sxs-lookup"><span data-stu-id="8d442-315">20</span></span>           |
        | <span data-ttu-id="8d442-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="8d442-316">AzureResponseLabel</span></span>     | <span data-ttu-id="8d442-317">Risposta Web di Azure</span><span class="sxs-lookup"><span data-stu-id="8d442-317">Azure Web Response</span></span> | <span data-ttu-id="8d442-318">20</span><span class="sxs-lookup"><span data-stu-id="8d442-318">20</span></span>           |
        | <span data-ttu-id="8d442-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="8d442-319">DictationLabel</span></span>         |   <span data-ttu-id="8d442-320">Si è appena detto:</span><span class="sxs-lookup"><span data-stu-id="8d442-320">You just said:</span></span>   | <span data-ttu-id="8d442-321">20</span><span class="sxs-lookup"><span data-stu-id="8d442-321">20</span></span>           |
        | <span data-ttu-id="8d442-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="8d442-322">TranslationResultLabel</span></span> |    <span data-ttu-id="8d442-323">Traduzione</span><span class="sxs-lookup"><span data-stu-id="8d442-323">Translation:</span></span>    | <span data-ttu-id="8d442-324">20</span><span class="sxs-lookup"><span data-stu-id="8d442-324">20</span></span>           |

        ![Immettere i valori corrispondenti per le etichette dell'interfaccia utente.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="8d442-326">Inoltre, applicare lo stile del carattere in grassetto.</span><span class="sxs-lookup"><span data-stu-id="8d442-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="8d442-327">In questo modo sarà più facile leggere il testo.</span><span class="sxs-lookup"><span data-stu-id="8d442-327">This will make the text easier to read.</span></span>

        ![Carattere grassetto.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="8d442-329">Per ogni *oggetto testo dell'interfaccia utente* creato nel [capitolo 5](#chapter-5--create-the-results-class), creare un nuovo **oggetto testo dell'interfaccia utente** *figlio* .</span><span class="sxs-lookup"><span data-stu-id="8d442-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="8d442-330">Questi elementi figlio visualizzeranno l'output dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8d442-330">These children will display the output of the application.</span></span> <span data-ttu-id="8d442-331">Creare oggetti *figlio* facendo clic con il pulsante destro del mouse sul padre desiderato, ad esempio *MicrophoneStatusLabel*, e quindi selezionando **interfaccia utente** e quindi selezionando **testo**.</span><span class="sxs-lookup"><span data-stu-id="8d442-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="8d442-332">Per ognuno di questi elementi figlio, selezionarlo e utilizzare le tabelle seguenti per impostare i parametri nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="8d442-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="8d442-333">Per il componente di **trasformazione Rect** :</span><span class="sxs-lookup"><span data-stu-id="8d442-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="8d442-334">NOME</span><span class="sxs-lookup"><span data-stu-id="8d442-334">Name</span></span>                  | <span data-ttu-id="8d442-335">Trasformazione- *posizione*</span><span class="sxs-lookup"><span data-stu-id="8d442-335">Transform - *Position*</span></span> | <span data-ttu-id="8d442-336">Larghezza</span><span class="sxs-lookup"><span data-stu-id="8d442-336">Width</span></span>      | <span data-ttu-id="8d442-337">Altezza</span><span class="sxs-lookup"><span data-stu-id="8d442-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="8d442-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="8d442-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="8d442-339">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="8d442-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="8d442-340">300</span><span class="sxs-lookup"><span data-stu-id="8d442-340">300</span></span>        | <span data-ttu-id="8d442-341">30</span><span class="sxs-lookup"><span data-stu-id="8d442-341">30</span></span>        |
        | <span data-ttu-id="8d442-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="8d442-342">AzureResponseText</span></span>     | <span data-ttu-id="8d442-343">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="8d442-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="8d442-344">300</span><span class="sxs-lookup"><span data-stu-id="8d442-344">300</span></span>        | <span data-ttu-id="8d442-345">30</span><span class="sxs-lookup"><span data-stu-id="8d442-345">30</span></span>        |
        | <span data-ttu-id="8d442-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="8d442-346">DictationText</span></span>         | <span data-ttu-id="8d442-347">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="8d442-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="8d442-348">300</span><span class="sxs-lookup"><span data-stu-id="8d442-348">300</span></span>        | <span data-ttu-id="8d442-349">30</span><span class="sxs-lookup"><span data-stu-id="8d442-349">30</span></span>        |
        | <span data-ttu-id="8d442-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="8d442-350">TranslationResultText</span></span> | <span data-ttu-id="8d442-351">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="8d442-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="8d442-352">300</span><span class="sxs-lookup"><span data-stu-id="8d442-352">300</span></span>        | <span data-ttu-id="8d442-353">30</span><span class="sxs-lookup"><span data-stu-id="8d442-353">30</span></span>        |

    2. <span data-ttu-id="8d442-354">Per il componente **testo (script)** :</span><span class="sxs-lookup"><span data-stu-id="8d442-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="8d442-355">Nome</span><span class="sxs-lookup"><span data-stu-id="8d442-355">Name</span></span>                  | <span data-ttu-id="8d442-356">Testo</span><span class="sxs-lookup"><span data-stu-id="8d442-356">Text</span></span>          | <span data-ttu-id="8d442-357">Dimensione carattere</span><span class="sxs-lookup"><span data-stu-id="8d442-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="8d442-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="8d442-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="8d442-359">??</span><span class="sxs-lookup"><span data-stu-id="8d442-359">??</span></span>       | <span data-ttu-id="8d442-360">20</span><span class="sxs-lookup"><span data-stu-id="8d442-360">20</span></span>           |
        | <span data-ttu-id="8d442-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="8d442-361">AzureResponseText</span></span>     |      <span data-ttu-id="8d442-362">??</span><span class="sxs-lookup"><span data-stu-id="8d442-362">??</span></span>       | <span data-ttu-id="8d442-363">20</span><span class="sxs-lookup"><span data-stu-id="8d442-363">20</span></span>           |
        | <span data-ttu-id="8d442-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="8d442-364">DictationText</span></span>         |      <span data-ttu-id="8d442-365">??</span><span class="sxs-lookup"><span data-stu-id="8d442-365">??</span></span>       | <span data-ttu-id="8d442-366">20</span><span class="sxs-lookup"><span data-stu-id="8d442-366">20</span></span>           |
        | <span data-ttu-id="8d442-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="8d442-367">TranslationResultText</span></span> |      <span data-ttu-id="8d442-368">??</span><span class="sxs-lookup"><span data-stu-id="8d442-368">??</span></span>       | <span data-ttu-id="8d442-369">20</span><span class="sxs-lookup"><span data-stu-id="8d442-369">20</span></span>           |

9. <span data-ttu-id="8d442-370">Selezionare quindi l'opzione di allineamento "Center" per ogni componente di testo:</span><span class="sxs-lookup"><span data-stu-id="8d442-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![Allinea il testo.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="8d442-372">Per assicurarsi che gli oggetti **testo dell'interfaccia utente figlio** siano facilmente leggibili, modificarne il *colore*.</span><span class="sxs-lookup"><span data-stu-id="8d442-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="8d442-373">A tale scopo, fare clic sulla barra (attualmente "nero") accanto a *colore*.</span><span class="sxs-lookup"><span data-stu-id="8d442-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Immettere i valori corrispondenti per gli output di testo dell'interfaccia utente.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="8d442-375">Quindi, nella finestra nuovo, piccolo, *colore* , modificare il *colore esadecimale* in: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="8d442-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Aggiornare il colore al blu.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="8d442-377">Di seguito è illustrata l'aspetto dell' **interfaccia utente** .</span><span class="sxs-lookup"><span data-stu-id="8d442-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="8d442-378">Nel *Pannello gerarchia*:</span><span class="sxs-lookup"><span data-stu-id="8d442-378">In the *Hierarchy Panel*:</span></span>

        ![Dispone della gerarchia nella struttura fornita.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="8d442-380">Nelle viste *scene* e *giochi*:</span><span class="sxs-lookup"><span data-stu-id="8d442-380">In the *Scene* and *Game Views*:</span></span>

        ![Includere le viste scene e giochi nella stessa struttura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="8d442-382">Capitolo 5: creare la classe Results</span><span class="sxs-lookup"><span data-stu-id="8d442-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="8d442-383">Il primo script che è necessario creare è la  classe results, che è responsabile di fornire un modo per visualizzare i risultati della conversione.</span><span class="sxs-lookup"><span data-stu-id="8d442-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="8d442-384">La classe archivia e visualizza quanto segue:</span><span class="sxs-lookup"><span data-stu-id="8d442-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="8d442-385">Risultato della risposta da Azure.</span><span class="sxs-lookup"><span data-stu-id="8d442-385">The response result from Azure.</span></span>
- <span data-ttu-id="8d442-386">Stato del microfono.</span><span class="sxs-lookup"><span data-stu-id="8d442-386">The microphone status.</span></span> 
- <span data-ttu-id="8d442-387">Risultato della dettatura (Voice to Text).</span><span class="sxs-lookup"><span data-stu-id="8d442-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="8d442-388">Risultato della traslazione.</span><span class="sxs-lookup"><span data-stu-id="8d442-388">The result of the translation.</span></span>

<span data-ttu-id="8d442-389">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="8d442-389">To create this class:</span></span> 

1.  <span data-ttu-id="8d442-390">Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare > cartella**.</span><span class="sxs-lookup"><span data-stu-id="8d442-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="8d442-391">Denominare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="8d442-391">Name the folder **Scripts**.</span></span> 
 
    ![Crea cartella script.](images/AzureLabs-Lab1-31.png)

    ![Aprire la cartella script.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="8d442-394">Con la  cartella Scripts create, fare doppio clic su di essa per aprirla.</span><span class="sxs-lookup"><span data-stu-id="8d442-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="8d442-395">Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse e selezionare **Crea >** quindi  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="8d442-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="8d442-396">Assegnare un nome ai *risultati*dello script.</span><span class="sxs-lookup"><span data-stu-id="8d442-396">Name the script *Results*.</span></span> 

    ![Creare il primo script.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="8d442-398">Fare doppio clic sul nuovo script *dei risultati* per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8d442-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="8d442-399">Inserire gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="8d442-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="8d442-400">All'interno della classe inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="8d442-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="8d442-401">Aggiungere quindi il metodo *sveglie ()* che verrà chiamato quando la classe viene inizializzata.</span><span class="sxs-lookup"><span data-stu-id="8d442-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="8d442-402">Aggiungere infine i metodi che sono responsabili dell'output delle varie informazioni sui risultati nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="8d442-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="8d442-403">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="8d442-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="8d442-404">Capitolo 6: creare la classe *MicrophoneManager*</span><span class="sxs-lookup"><span data-stu-id="8d442-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="8d442-405">La seconda classe che si intende creare è *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="8d442-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="8d442-406">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="8d442-406">This class is responsible for:</span></span>

- <span data-ttu-id="8d442-407">Rilevamento del dispositivo di registrazione collegato all'auricolare o al computer (a seconda di quale sia l'impostazione predefinita).</span><span class="sxs-lookup"><span data-stu-id="8d442-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="8d442-408">Acquisire l'audio (voce) e utilizzare la dettatura per archiviarlo come stringa.</span><span class="sxs-lookup"><span data-stu-id="8d442-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="8d442-409">Una volta sospesa la voce, inviare la dettatura alla classe Translator.</span><span class="sxs-lookup"><span data-stu-id="8d442-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="8d442-410">Ospitare un metodo che può arrestare l'acquisizione vocale, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="8d442-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="8d442-411">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="8d442-411">To create this class:</span></span> 
1.  <span data-ttu-id="8d442-412">Fare doppio clic sulla  cartella Scripts per aprirla.</span><span class="sxs-lookup"><span data-stu-id="8d442-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="8d442-413">Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="8d442-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="8d442-414">Denominare lo script *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="8d442-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="8d442-415">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d442-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="8d442-416">Aggiornare gli spazi dei nomi in modo che corrispondano a quelli riportati di seguito, all'inizio della classe *MicrophoneManager* :</span><span class="sxs-lookup"><span data-stu-id="8d442-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="8d442-417">Aggiungere quindi le variabili seguenti all'interno della classe *MicrophoneManager* :</span><span class="sxs-lookup"><span data-stu-id="8d442-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="8d442-418">È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="8d442-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="8d442-419">Questi verranno chiamati quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="8d442-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="8d442-420">È possibile *eliminare* il metodo *Update ()* perché non verrà utilizzato da questa classe.</span><span class="sxs-lookup"><span data-stu-id="8d442-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="8d442-421">A questo punto sono necessari i metodi usati dall'app per avviare e arrestare l'acquisizione vocale e passarli alla classe *Translator* , che verrà compilata a breve.</span><span class="sxs-lookup"><span data-stu-id="8d442-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="8d442-422">Copiare il codice seguente e incollarlo sotto il metodo *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="8d442-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="8d442-423">Anche se questa applicazione non lo userà, il metodo *StopCapturingAudio ()* è stato fornito qui. Se si vuole implementare la possibilità di arrestare l'acquisizione dell'audio nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8d442-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="8d442-424">A questo punto è necessario aggiungere un gestore di dettatura che verrà richiamato quando la voce viene arrestata.</span><span class="sxs-lookup"><span data-stu-id="8d442-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="8d442-425">Questo metodo passerà quindi il testo imposto alla classe *Translator* .</span><span class="sxs-lookup"><span data-stu-id="8d442-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="8d442-426">Assicurarsi di salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="8d442-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="8d442-427">A questo punto si noterà un errore nel pannello *console Editor Unity* ("il nome ' Translator ' non esiste...").</span><span class="sxs-lookup"><span data-stu-id="8d442-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="8d442-428">Questo perché il codice fa riferimento alla classe *Translator* , che verrà creata nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="8d442-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="8d442-429">Capitolo 7-chiamata a Azure e al servizio Translator</span><span class="sxs-lookup"><span data-stu-id="8d442-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="8d442-430">L'ultimo script che è necessario creare è la classe *Translator* .</span><span class="sxs-lookup"><span data-stu-id="8d442-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="8d442-431">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="8d442-431">This class is responsible for:</span></span>

-   <span data-ttu-id="8d442-432">Autenticazione dell'app con *Azure*, in Exchange per un **token di autenticazione**.</span><span class="sxs-lookup"><span data-stu-id="8d442-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="8d442-433">Usare il **token di autenticazione** per inviare il testo (ricevuto dalla classe *MicrophoneManager* ) da tradurre.</span><span class="sxs-lookup"><span data-stu-id="8d442-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="8d442-434">Ricevere il risultato tradotto e passarlo alla  classe results da visualizzare nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="8d442-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="8d442-435">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="8d442-435">To create this Class:</span></span> 
1.  <span data-ttu-id="8d442-436">Passare alla cartella **Scripts** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="8d442-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="8d442-437">Fare clic con il pulsante destro del mouse sul **Pannello del progetto**, quindi **creare > C# script**.</span><span class="sxs-lookup"><span data-stu-id="8d442-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="8d442-438">Chiamare lo script *Translator*.</span><span class="sxs-lookup"><span data-stu-id="8d442-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="8d442-439">Fare doppio clic sul nuovo script di *conversione* per aprirlo **con Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8d442-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="8d442-440">Aggiungere i seguenti spazi dei nomi all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="8d442-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="8d442-441">Aggiungere quindi le variabili seguenti all'interno della classe *Translator* :</span><span class="sxs-lookup"><span data-stu-id="8d442-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="8d442-442">Le lingue inserite nell' **enum** di lingue sono solo esempi.</span><span class="sxs-lookup"><span data-stu-id="8d442-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="8d442-443">Se lo si desidera, è possibile aggiungerne altri. l' [API supporta oltre 60 lingue](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluso Klingon).</span><span class="sxs-lookup"><span data-stu-id="8d442-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="8d442-444">Esiste una [pagina più interattiva che copre le lingue disponibili](https://www.microsoft.com/translator/business/languages/), ma è importante tenere presente che la pagina sembra funzionare solo quando la lingua del sito è impostata su "en-US" (e il sito Microsoft verrà probabilmente reindirizzato alla lingua nativa).</span><span class="sxs-lookup"><span data-stu-id="8d442-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="8d442-445">È possibile modificare la lingua del sito nella parte inferiore della pagina o modificando l'URL.</span><span class="sxs-lookup"><span data-stu-id="8d442-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="8d442-446">Il valore **authorizationKey** , nel frammento di codice precedente, deve essere la **chiave** ricevuta quando si è effettuata la sottoscrizione al *API traduzione testuale di Azure*.</span><span class="sxs-lookup"><span data-stu-id="8d442-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="8d442-447">Questo è stato trattato nel [capitolo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="8d442-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="8d442-448">È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="8d442-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="8d442-449">In questo caso, il codice effettuerà una chiamata ad *Azure* usando la chiave di autorizzazione per ottenere un *token*.</span><span class="sxs-lookup"><span data-stu-id="8d442-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="8d442-450">Il token scadrà dopo 10 minuti.</span><span class="sxs-lookup"><span data-stu-id="8d442-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="8d442-451">A seconda dello scenario per l'app, potrebbe essere necessario eseguire più volte la stessa chiamata di coroutine.</span><span class="sxs-lookup"><span data-stu-id="8d442-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="8d442-452">La coroutine per ottenere il token è la seguente:</span><span class="sxs-lookup"><span data-stu-id="8d442-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="8d442-453">Se si modifica il nome del metodo IEnumerator **GetTokenCoroutine ()** , è necessario aggiornare i valori della stringa di chiamata *StartCoroutine* e *StopCoroutine* nel codice riportato sopra.</span><span class="sxs-lookup"><span data-stu-id="8d442-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="8d442-454">In base alla [documentazione](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)di Unity, per arrestare una coroutine specifica, è necessario usare il metodo del valore stringa.</span><span class="sxs-lookup"><span data-stu-id="8d442-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="8d442-455">Successivamente, aggiungere la coroutine (con un metodo del flusso di "supporto" sotto di essa) per ottenere la traduzione del testo ricevuto dalla classe *MicrophoneManager* .</span><span class="sxs-lookup"><span data-stu-id="8d442-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="8d442-456">Questo codice crea una stringa di query da inviare al *API traduzione testuale di Azure*, quindi usa la classe UnityWebRequest di Unity interna per effettuare una chiamata Get all'endpoint con la stringa di query.</span><span class="sxs-lookup"><span data-stu-id="8d442-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="8d442-457">Il risultato viene quindi utilizzato per impostare la traduzione nell'oggetto risultati.</span><span class="sxs-lookup"><span data-stu-id="8d442-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="8d442-458">Il codice seguente illustra l'implementazione:</span><span class="sxs-lookup"><span data-stu-id="8d442-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="8d442-459">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="8d442-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="8d442-460">Capitolo 8: configurare la scena Unity</span><span class="sxs-lookup"><span data-stu-id="8d442-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="8d442-461">Nell'editor di Unity fare clic e trascinare la  classe results *dalla* cartella Scripts all'oggetto **principale della fotocamera**  nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="8d442-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="8d442-462">Fare clic sulla **fotocamera principale** ed esaminare il *pannello Inspector*.</span><span class="sxs-lookup"><span data-stu-id="8d442-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="8d442-463">Si noterà che all'interno del componente *script* appena aggiunto sono presenti quattro campi con valori vuoti.</span><span class="sxs-lookup"><span data-stu-id="8d442-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="8d442-464">Questi sono i riferimenti di output alle proprietà nel codice.</span><span class="sxs-lookup"><span data-stu-id="8d442-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="8d442-465">Trascinare gli oggetti **testo** appropriati dal *Pannello gerarchia* a questi quattro slot, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="8d442-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Aggiornare i riferimenti di destinazione con i valori specificati.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="8d442-467">Quindi, fare clic e trascinare la classe *Translator* dalla  cartella Scripts all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="8d442-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="8d442-468">Quindi, fare clic e trascinare la classe *MicrophoneManager* dalla  cartella Scripts all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="8d442-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="8d442-469">Infine, fare clic sulla **videocamera principale** ed esaminare il *pannello Inspector*.</span><span class="sxs-lookup"><span data-stu-id="8d442-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="8d442-470">Si noterà che nello script che è stato trascinato sono presenti due caselle di riepilogo a discesa che consentono di impostare le lingue.</span><span class="sxs-lookup"><span data-stu-id="8d442-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Verificare che i linguaggi di traduzione previsti siano di input.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="8d442-472">Capitolo 9: test in realtà mista</span><span class="sxs-lookup"><span data-stu-id="8d442-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="8d442-473">A questo punto è necessario testare che la scena è stata implementata correttamente.</span><span class="sxs-lookup"><span data-stu-id="8d442-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="8d442-474">Assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="8d442-474">Ensure that:</span></span>

- <span data-ttu-id="8d442-475">Tutte le impostazioni indicate nel [capitolo 1](#chapter-1--the-azure-portal) sono impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="8d442-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="8d442-476">I *risultati*, *Translator*e *MicrophoneManager*, gli script sono allegati all'oggetto della **fotocamera principale** .</span><span class="sxs-lookup"><span data-stu-id="8d442-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="8d442-477">La **chiave** del servizio *API traduzione testuale di Azure* è stata inserita nella variabile **AuthorizationKey** all'interno dello script *Translator* .</span><span class="sxs-lookup"><span data-stu-id="8d442-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="8d442-478">Tutti i campi nel *pannello principale di controllo della fotocamera* sono assegnati correttamente.</span><span class="sxs-lookup"><span data-stu-id="8d442-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="8d442-479">Il microfono funziona quando si esegue la scena. in caso contrario, verificare che il microfono collegato sia il dispositivo *predefinito* e che sia stato [configurato correttamente all'interno di Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10).</span><span class="sxs-lookup"><span data-stu-id="8d442-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="8d442-480">È possibile testare l'auricolare immersivo premendo il pulsante **Play** nell'editor di *Unity*.</span><span class="sxs-lookup"><span data-stu-id="8d442-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="8d442-481">L'app deve funzionare tramite l'auricolare immersivo collegato.</span><span class="sxs-lookup"><span data-stu-id="8d442-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="8d442-482">Se nella console di Unity viene visualizzato un errore relativo alla modifica del dispositivo audio predefinito, è possibile che la scena non funzioni come previsto.</span><span class="sxs-lookup"><span data-stu-id="8d442-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="8d442-483">Questo è dovuto al modo in cui il portale di realtà mista gestisce i microfoni predefiniti per le cuffie che li hanno.</span><span class="sxs-lookup"><span data-stu-id="8d442-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="8d442-484">Se viene visualizzato questo errore, è sufficiente arrestare la scena e avviarla di nuovo e le operazioni dovrebbero funzionare come previsto.</span><span class="sxs-lookup"><span data-stu-id="8d442-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="8d442-485">Capitolo 10: compilare la soluzione UWP e sideload nel computer locale</span><span class="sxs-lookup"><span data-stu-id="8d442-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="8d442-486">Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.</span><span class="sxs-lookup"><span data-stu-id="8d442-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="8d442-487">Passare a **impostazioni di compilazione**: **File > impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="8d442-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="8d442-488">Nella finestra **impostazioni di compilazione** fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="8d442-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilare la scena Unity.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="8d442-490">Se non è già stato fatto, è necessario che i **progetti C# Unity**</span><span class="sxs-lookup"><span data-stu-id="8d442-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="8d442-491">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="8d442-491">Click **Build**.</span></span> <span data-ttu-id="8d442-492">Unity avvierà una finestra di *Esplora file* , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="8d442-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="8d442-493">Creare la cartella adesso e denominarla *app*.</span><span class="sxs-lookup"><span data-stu-id="8d442-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="8d442-494">Quindi, con la cartella dell' *app* selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="8d442-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="8d442-495">Unity inizierà a compilare il progetto nella cartella dell' *app* .</span><span class="sxs-lookup"><span data-stu-id="8d442-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="8d442-496">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra *Esplora file* nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).</span><span class="sxs-lookup"><span data-stu-id="8d442-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="8d442-497">Capitolo 11-distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="8d442-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="8d442-498">Per distribuire l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="8d442-498">To deploy your application:</span></span>

1.  <span data-ttu-id="8d442-499">Passare alla nuova compilazione Unity (cartella *app* ) e aprire il file della soluzione con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="8d442-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="8d442-500">Nella configurazione della soluzione selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="8d442-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="8d442-501">Nella piattaforma soluzione selezionare **x86**, **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="8d442-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="8d442-502">Per Microsoft HoloLens, può risultare più semplice impostare questa impostazione su *computer remoto*, in modo da non essere collegati al computer.</span><span class="sxs-lookup"><span data-stu-id="8d442-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="8d442-503">Tuttavia, sarà necessario eseguire anche le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="8d442-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="8d442-504">Conosce l' **indirizzo IP** del HoloLens, disponibile all'interno delle *impostazioni > rete & Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare.</span><span class="sxs-lookup"><span data-stu-id="8d442-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="8d442-505">Verificare che la *modalità sviluppatore* sia **attiva**; disponibile in *impostazioni > aggiorna & > di sicurezza per gli sviluppatori*.</span><span class="sxs-lookup"><span data-stu-id="8d442-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="8d442-507">Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per SIDELOAD l'applicazione al PC.</span><span class="sxs-lookup"><span data-stu-id="8d442-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="8d442-508">L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="8d442-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="8d442-509">Una volta avviata, l'app richiederà di autorizzare l'accesso al microfono.</span><span class="sxs-lookup"><span data-stu-id="8d442-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="8d442-510">Assicurarsi di fare clic sul pulsante **Sì** .</span><span class="sxs-lookup"><span data-stu-id="8d442-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="8d442-511">A questo punto è possibile iniziare a tradurre.</span><span class="sxs-lookup"><span data-stu-id="8d442-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="8d442-512">Applicazione API testo traduzione completata</span><span class="sxs-lookup"><span data-stu-id="8d442-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="8d442-513">Congratulazioni, è stata creata un'app per realtà mista che sfrutta l'API traduzione testuale di Azure per convertire il riconoscimento vocale in testo tradotto.</span><span class="sxs-lookup"><span data-stu-id="8d442-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Prodotto finale.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="8d442-515">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="8d442-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="8d442-516">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="8d442-516">Exercise 1</span></span>

<span data-ttu-id="8d442-517">È possibile aggiungere funzionalità di sintesi vocale all'app, in modo che il testo restituito venga pronunciato?</span><span class="sxs-lookup"><span data-stu-id="8d442-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="8d442-518">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="8d442-518">Exercise 2</span></span>

<span data-ttu-id="8d442-519">Consentire all'utente di modificare le lingue di origine e di output ("da" e "in") nell'app stessa, in modo che l'app non debba essere ricompilata ogni volta che si desidera modificare le lingue.</span><span class="sxs-lookup"><span data-stu-id="8d442-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
