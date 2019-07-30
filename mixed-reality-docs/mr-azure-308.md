---
title: MR e Azure 308-notifiche tra dispositivi
description: Completare questo corso per apprendere come implementare Hub di notifica di Azure, funzioni di Azure e archiviazione di Azure e tabelle in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, notifiche, funzioni, tabelle, hub di notifica, hololens, immersive, VR
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694608"
---
>[!NOTE]
><span data-ttu-id="79b66-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="79b66-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="79b66-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="79b66-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="79b66-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79b66-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="79b66-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="79b66-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="79b66-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79b66-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="79b66-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="79b66-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="79b66-110">MR e Azure 308: Notifiche tra dispositivi</span><span class="sxs-lookup"><span data-stu-id="79b66-110">MR and Azure 308: Cross-device notifications</span></span>

![prodotto finale-inizio](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="79b66-112">In questo corso verrà illustrato come aggiungere funzionalità di hub di notifica a un'applicazione di realtà mista usando hub di notifica di Azure, tabelle di Azure e funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="79b66-113">**Hub di notifica di Azure** è un servizio Microsoft che consente agli sviluppatori di inviare notifiche push mirate e personalizzate a qualsiasi piattaforma, tutto alimentato all'interno del cloud.</span><span class="sxs-lookup"><span data-stu-id="79b66-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="79b66-114">Ciò consente agli sviluppatori di comunicare con gli utenti finali o persino di comunicare tra le varie applicazioni, a seconda dello scenario.</span><span class="sxs-lookup"><span data-stu-id="79b66-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="79b66-115">Per altre informazioni, visitare la [pagina](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)Hub di notifica di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="79b66-116">**Funzioni di Azure** è un servizio Microsoft che consente agli sviluppatori di eseguire piccole porzioni di codice, "funzioni", in Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="79b66-117">Questo consente di delegare il lavoro al cloud, anziché l'applicazione locale, che può avere molti vantaggi.</span><span class="sxs-lookup"><span data-stu-id="79b66-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="79b66-118">**Funzioni di Azure** supporta diversi linguaggi di sviluppo,\#tra cui\#C, F, node. js, Java e php.</span><span class="sxs-lookup"><span data-stu-id="79b66-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="79b66-119">Per altre informazioni, visitare la [pagina](https://docs.microsoft.com/azure/azure-functions/functions-overview)funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="79b66-120">**Tabelle di Azure** è un servizio cloud Microsoft che consente agli sviluppatori di archiviare dati non SQL strutturati nel cloud, rendendoli facilmente accessibili ovunque.</span><span class="sxs-lookup"><span data-stu-id="79b66-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="79b66-121">Il servizio è caratterizzato da una progettazione non schema, che consente l'evoluzione delle tabelle in base alle esigenze e pertanto è molto flessibile.</span><span class="sxs-lookup"><span data-stu-id="79b66-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="79b66-122">Per altre informazioni, visita la [pagina](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) delle tabelle di Azure</span><span class="sxs-lookup"><span data-stu-id="79b66-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="79b66-123">Dopo aver completato questo corso, si disporrà di un'applicazione per le cuffie immersive a realtà mista e di un'applicazione per PC desktop, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="79b66-124">L'app desktop PC consentirà all'utente di spostare un oggetto nello spazio 2D (X e Y), usando il mouse.</span><span class="sxs-lookup"><span data-stu-id="79b66-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="79b66-125">Lo spostamento di oggetti all'interno dell'app PC verrà inviato al cloud usando JSON, che avrà il formato di una stringa, contenente un ID oggetto, un tipo e le informazioni di trasformazione (coordinate X e Y).</span><span class="sxs-lookup"><span data-stu-id="79b66-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="79b66-126">L'app per la realtà mista, che ha una scena identica per l'app desktop, riceverà le notifiche relative allo spostamento degli oggetti, dal servizio Hub di notifica, che è stato appena aggiornato dall'app per PC desktop.</span><span class="sxs-lookup"><span data-stu-id="79b66-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="79b66-127">Quando riceve una notifica, che conterrà l'ID oggetto, il tipo e le informazioni di trasformazione, l'app realtà mista applica le informazioni ricevute alla propria scena.</span><span class="sxs-lookup"><span data-stu-id="79b66-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="79b66-128">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="79b66-129">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="79b66-130">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="79b66-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="79b66-131">Questo corso è un'esercitazione autonoma, che non implica direttamente altri laboratori di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="79b66-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="79b66-132">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="79b66-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="79b66-133">Corso</span><span class="sxs-lookup"><span data-stu-id="79b66-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="79b66-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="79b66-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="79b66-135"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="79b66-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="79b66-136">MR e Azure 308: Notifiche tra dispositivi</span><span class="sxs-lookup"><span data-stu-id="79b66-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="79b66-137">✔️</span><span class="sxs-lookup"><span data-stu-id="79b66-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="79b66-138">✔️</span><span class="sxs-lookup"><span data-stu-id="79b66-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="79b66-139">Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79b66-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="79b66-140">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79b66-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="79b66-141">Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.</span><span class="sxs-lookup"><span data-stu-id="79b66-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79b66-142">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="79b66-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="79b66-143">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="79b66-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="79b66-144">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="79b66-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="79b66-145">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b66-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="79b66-146">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="79b66-147">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="79b66-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="79b66-148">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="79b66-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79b66-149">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="79b66-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79b66-150">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="79b66-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79b66-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="79b66-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="79b66-152">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="79b66-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="79b66-153">Accesso a Internet per il programma di installazione di Azure e per accedere a hub di notifica</span><span class="sxs-lookup"><span data-stu-id="79b66-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="79b66-154">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="79b66-154">Before you start</span></span>

- <span data-ttu-id="79b66-155">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="79b66-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="79b66-156">È necessario essere il proprietario del portale per sviluppatori Microsoft e il portale di registrazione delle applicazioni. in caso contrario, non si sarà autorizzati ad accedere all'app nel [capitolo 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="79b66-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="79b66-157">Capitolo 1-creare un'applicazione nel portale per sviluppatori Microsoft</span><span class="sxs-lookup"><span data-stu-id="79b66-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="79b66-158">Per usare il servizio **Hub di notifica di Azure** , è necessario creare un'applicazione nel portale per sviluppatori Microsoft, in quanto l'applicazione deve essere registrata, in modo che possa inviare e ricevere notifiche.</span><span class="sxs-lookup"><span data-stu-id="79b66-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="79b66-159">Accedere al portale per [sviluppatori Microsoft](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="79b66-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="79b66-160">Sarà necessario accedere al proprio account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="79b66-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="79b66-161">Dal dashboard fare clic su **Crea una nuova app**.</span><span class="sxs-lookup"><span data-stu-id="79b66-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Creare un'app](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="79b66-163">Verrà visualizzata una finestra popup in cui è necessario riservare un nome per la nuova app.</span><span class="sxs-lookup"><span data-stu-id="79b66-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="79b66-164">Nella casella di testo inserire un nome appropriato. Se il nome scelto è disponibile, verrà visualizzato un segno di spunta a destra della casella di testo.</span><span class="sxs-lookup"><span data-stu-id="79b66-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="79b66-165">Una volta inserito un nome disponibile, fare clic sul pulsante **riserva nome prodotto** nella parte inferiore sinistra della finestra popup.</span><span class="sxs-lookup"><span data-stu-id="79b66-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![invertire un nome](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="79b66-167">Ora che l'app è stata creata, è possibile passare al capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="79b66-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="79b66-168">Capitolo 2: recuperare le nuove credenziali per le app</span><span class="sxs-lookup"><span data-stu-id="79b66-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="79b66-169">Accedere al portale di registrazione delle applicazioni, in cui sarà elencata la nuova app e recuperare le credenziali che verranno usate per configurare il **servizio Hub di notifica** nel **portale di Azure**.</span><span class="sxs-lookup"><span data-stu-id="79b66-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="79b66-170">Passare al [portale di registrazione delle applicazioni](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="79b66-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![portale di registrazione delle applicazioni](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="79b66-172">Per accedere è necessario usare il proprio account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="79b66-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="79b66-173">**Deve** corrispondere all'account Microsoft usato nel [capitolo](#chapter-1---create-an-application-on-the-microsoft-developer-portal)precedente, con il portale per sviluppatori di Windows Store.</span><span class="sxs-lookup"><span data-stu-id="79b66-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="79b66-174">L'app sarà presente nella sezione **applicazioni personali** .</span><span class="sxs-lookup"><span data-stu-id="79b66-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="79b66-175">Una volta individuato, fare clic su di esso e verrà eseguita una nuova pagina con il nome dell'app e la **registrazione**.</span><span class="sxs-lookup"><span data-stu-id="79b66-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![app appena registrata](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="79b66-177">Scorrere la pagina di registrazione per trovare la sezione dei **segreti dell'applicazione** e il **SID del pacchetto** per l'app.</span><span class="sxs-lookup"><span data-stu-id="79b66-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="79b66-178">Copiare entrambi per l'uso con la configurazione del **servizio Hub di notifica di Azure** nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="79b66-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![segreti dell'applicazione](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="79b66-180">Capitolo 3: configurare il portale di Azure: creare il servizio Hub di notifica</span><span class="sxs-lookup"><span data-stu-id="79b66-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="79b66-181">Con le credenziali delle app recuperate, sarà necessario accedere al portale di Azure, in cui si creerà un servizio Hub di notifica di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="79b66-182">Accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="79b66-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="79b66-183">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="79b66-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="79b66-184">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="79b66-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="79b66-185">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare **Hub di notifica**e quindi premere ***invio***.</span><span class="sxs-lookup"><span data-stu-id="79b66-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![ricerca di hub di notifica](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="79b66-187">La parola ***New*** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="79b66-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="79b66-188">La nuova pagina fornirà una descrizione del servizio *Hub di notifica* .</span><span class="sxs-lookup"><span data-stu-id="79b66-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="79b66-189">Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![creare un'istanza di hub di notifica](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="79b66-191">Una volta fatto clic su ***Crea***:</span><span class="sxs-lookup"><span data-stu-id="79b66-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="79b66-192">Inserire il nome desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="79b66-193">Fornire uno **spazio dei nomi** che sarà possibile associare a questa app.</span><span class="sxs-lookup"><span data-stu-id="79b66-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="79b66-194">Selezionare una **località.**</span><span class="sxs-lookup"><span data-stu-id="79b66-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="79b66-195">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="79b66-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79b66-196">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="79b66-197">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="79b66-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="79b66-198">Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="79b66-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="79b66-199">Selezionare una **sottoscrizione**appropriata.</span><span class="sxs-lookup"><span data-stu-id="79b66-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="79b66-200">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="79b66-201">Selezionare **Create**.</span><span class="sxs-lookup"><span data-stu-id="79b66-201">Select **Create**.</span></span>

        ![dettagli del servizio di riempimento](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="79b66-203">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="79b66-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="79b66-204">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="79b66-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notifica](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="79b66-206">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="79b66-207">Si verrà portati alla nuova istanza del servizio **Hub di notifica** .</span><span class="sxs-lookup"><span data-stu-id="79b66-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Vai alla risorsa](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="79b66-209">Dalla pagina Panoramica, a metà della pagina, fare clic su **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="79b66-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="79b66-210">Il pannello a destra cambierà in modo da visualizzare due campi di testo, che richiedono il **SID del pacchetto** e la **chiave di sicurezza**, dall'App configurata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79b66-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![servizio Hub appena creato](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="79b66-212">Dopo aver copiato i dettagli nei campi corretti, fare clic su **Salva**e si riceverà una notifica quando l'hub di notifica è stato aggiornato correttamente.</span><span class="sxs-lookup"><span data-stu-id="79b66-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![Copia dettagli sicurezza](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="79b66-214">Capitolo 4: configurare il portale di Azure: creare il servizio tabelle</span><span class="sxs-lookup"><span data-stu-id="79b66-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="79b66-215">Dopo aver creato l'istanza del servizio Hub di notifica, tornare al portale di Azure, in cui si creerà un servizio tabelle di Azure creando una risorsa di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="79b66-216">Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="79b66-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="79b66-217">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare **account di archiviazione**e premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="79b66-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="79b66-218">La parola ***New*** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="79b66-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="79b66-219">Selezionare **account di archiviazione: BLOB, file, tabella e coda** dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="79b66-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Cerca account di archiviazione](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="79b66-221">La nuova pagina fornirà una descrizione del servizio dell' **account di archiviazione** .</span><span class="sxs-lookup"><span data-stu-id="79b66-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="79b66-222">Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="79b66-224">Una volta fatto clic su **Crea**, verrà visualizzato un pannello:</span><span class="sxs-lookup"><span data-stu-id="79b66-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="79b66-225">Inserire il **nome** desiderato per l'istanza del servizio (deve essere in lettere minuscole).</span><span class="sxs-lookup"><span data-stu-id="79b66-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="79b66-226">Per **modello di distribuzione**, fare clic su **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="79b66-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="79b66-227">Per **tipo di account**, usando il menu a discesa selezionare **archiviazione (utilizzo generico V1)** .</span><span class="sxs-lookup"><span data-stu-id="79b66-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="79b66-228">Selezionare un **percorso**appropriato.</span><span class="sxs-lookup"><span data-stu-id="79b66-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="79b66-229">Per il menu a discesa **replica** , selezionare **lettura-accesso-archiviazione con ridondanza geografica (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="79b66-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="79b66-230">Per **prestazioni**, fare clic su **standard**.</span><span class="sxs-lookup"><span data-stu-id="79b66-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="79b66-231">Nella sezione **trasferimento sicuro obbligatorio** selezionare disabilitato.</span><span class="sxs-lookup"><span data-stu-id="79b66-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="79b66-232">Dal menu a discesa **sottoscrizione** selezionare una sottoscrizione appropriata.</span><span class="sxs-lookup"><span data-stu-id="79b66-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="79b66-233">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="79b66-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79b66-234">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="79b66-235">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="79b66-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="79b66-236">Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="79b66-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="79b66-237">Lasciare le **reti virtuali** **disabilitate** se si tratta di un'opzione.</span><span class="sxs-lookup"><span data-stu-id="79b66-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="79b66-238">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="79b66-238">Click **Create**.</span></span>

        ![specificare i dettagli di archiviazione](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="79b66-240">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="79b66-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="79b66-241">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="79b66-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="79b66-242">Fare clic sulle notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-242">Click on the notifications to explore your new Service instance.</span></span>

    ![nuova notifica di archiviazione](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="79b66-244">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="79b66-245">Si verrà portati alla nuova pagina Panoramica dell'istanza del servizio di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Vai alla risorsa](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="79b66-247">Nella pagina Panoramica fare clic su **tabelle**sul lato destro.</span><span class="sxs-lookup"><span data-stu-id="79b66-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="79b66-248">Il pannello a destra cambierà in modo da visualizzare le informazioni sul **servizio tabelle** , in cui è necessario aggiungere una nuova tabella.</span><span class="sxs-lookup"><span data-stu-id="79b66-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="79b66-249">A tale scopo, fare **+** clic sul pulsante **tabella** nell'angolo superiore sinistro.</span><span class="sxs-lookup"><span data-stu-id="79b66-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![Apri tabelle](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="79b66-251">Verrà visualizzata una nuova pagina, in cui è necessario immettere un nome di **tabella**.</span><span class="sxs-lookup"><span data-stu-id="79b66-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="79b66-252">Si tratta del nome che verrà usato per fare riferimento ai dati nell'applicazione nei capitoli successivi.</span><span class="sxs-lookup"><span data-stu-id="79b66-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="79b66-253">Inserire un nome appropriato e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="79b66-253">Insert an appropriate name and click **OK**.</span></span>

    ![Crea nuova tabella](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="79b66-255">Una volta creata la nuova tabella, sarà possibile visualizzarla nella pagina del **servizio tabelle** (nella parte inferiore).</span><span class="sxs-lookup"><span data-stu-id="79b66-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![nuova tabella creata](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="79b66-257">Capitolo 5-completamento della tabella di Azure in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79b66-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="79b66-258">Ora che l'account di archiviazione del **servizio tabelle** è stato configurato, è possibile aggiungervi dati, che verranno usati per archiviare e recuperare le informazioni.</span><span class="sxs-lookup"><span data-stu-id="79b66-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="79b66-259">La modifica delle tabelle può essere eseguita tramite **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79b66-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="79b66-260">Aprire **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79b66-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="79b66-261">Dal menu fare clic su **Visualizza** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="79b66-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Aprire Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="79b66-263">Il **Cloud Explorer** verrà aperto come elemento ancorato (essere paziente, perché il caricamento potrebbe richiedere tempo).</span><span class="sxs-lookup"><span data-stu-id="79b66-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="79b66-264">Se la sottoscrizione usata per creare gli *account di archiviazione* non è visibile, assicurarsi di disporre di:</span><span class="sxs-lookup"><span data-stu-id="79b66-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="79b66-265">Si è connessi allo stesso account usato per il portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="79b66-266">È stata selezionata la sottoscrizione dalla pagina di gestione degli account. potrebbe essere necessario applicare un filtro dalle impostazioni dell'account:</span><span class="sxs-lookup"><span data-stu-id="79b66-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![trova sottoscrizione](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="79b66-268">Verranno visualizzati i servizi cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="79b66-269">Trovare gli **account di archiviazione** e fare clic sulla freccia a sinistra di per espandere gli account.</span><span class="sxs-lookup"><span data-stu-id="79b66-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![aprire gli account di archiviazione](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="79b66-271">Una volta espansa, l' **account di archiviazione** appena creato dovrebbe essere disponibile.</span><span class="sxs-lookup"><span data-stu-id="79b66-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="79b66-272">Fare clic sulla freccia a sinistra della risorsa di archiviazione, quindi, una volta espansa, trovare le **tabelle** e fare clic sulla freccia accanto a questa, per visualizzare la **tabella** creata nell'ultimo capitolo.</span><span class="sxs-lookup"><span data-stu-id="79b66-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="79b66-273">Fare doppio clic sulla **tabella**.</span><span class="sxs-lookup"><span data-stu-id="79b66-273">Double click your **Table**.</span></span>

    ![Apri tabella oggetti scena](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="79b66-275">La tabella verrà aperta al centro della finestra di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79b66-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="79b66-276">Fare clic sull'icona della tabella **+** con il segno (più).</span><span class="sxs-lookup"><span data-stu-id="79b66-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![Aggiungi nuova tabella](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="79b66-278">Verrà visualizzata una finestra con la richiesta di *aggiungere un'entità*.</span><span class="sxs-lookup"><span data-stu-id="79b66-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="79b66-279">Si creeranno tre entità in totale, ognuna con diverse proprietà.</span><span class="sxs-lookup"><span data-stu-id="79b66-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="79b66-280">Si noterà che *PartitionKey* e *RowKey* sono già disponibili, perché vengono usati dalla tabella per trovare i dati.</span><span class="sxs-lookup"><span data-stu-id="79b66-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![chiave di partizione e di riga](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="79b66-282">Aggiornare il *valore* di **PartitionKey** e **RowKey** come indicato di seguito. a tale scopo, è necessario eseguire questa operazione per ogni proprietà di riga aggiunta, ma incrementare ogni volta il RowKey:</span><span class="sxs-lookup"><span data-stu-id="79b66-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![Aggiungi valori corretti](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="79b66-284">Fare clic su **Aggiungi proprietà** per aggiungere righe di dati aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="79b66-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="79b66-285">Fare in modo che la prima tabella vuota corrisponda alla tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="79b66-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="79b66-286">Al termine, fare clic su **OK** .</span><span class="sxs-lookup"><span data-stu-id="79b66-286">Click **OK** when you are finished.</span></span>

    ![al termine, fare clic su OK](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="79b66-288">Assicurarsi di aver modificato il **tipo** delle voci **X**, **Y**e **Z**in **Double**.</span><span class="sxs-lookup"><span data-stu-id="79b66-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="79b66-289">Si noterà che la tabella dispone ora di una riga di dati.</span><span class="sxs-lookup"><span data-stu-id="79b66-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="79b66-290">Fare di nuovo clic sull'icona **(più)peraggiungereun'altraentità.+**</span><span class="sxs-lookup"><span data-stu-id="79b66-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![prima riga](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="79b66-292">Creare una proprietà aggiuntiva, quindi impostare i valori della nuova entità in modo che corrispondano a quelli mostrati di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b66-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Aggiungi cubo](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="79b66-294">Ripetere l'ultimo passaggio per aggiungere un'altra entità.</span><span class="sxs-lookup"><span data-stu-id="79b66-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="79b66-295">Impostare i valori per questa entità su quelli mostrati di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b66-295">Set the values for this entity to those shown below.</span></span>

    ![Aggiungi cilindro](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="79b66-297">La tabella dovrebbe essere simile a quella riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b66-297">Your table should now look like the one below.</span></span>

    ![tabella completata](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="79b66-299">Il capitolo è stato completato.</span><span class="sxs-lookup"><span data-stu-id="79b66-299">You have completed this Chapter.</span></span> <span data-ttu-id="79b66-300">Assicurarsi di salvare.</span><span class="sxs-lookup"><span data-stu-id="79b66-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="79b66-301">Capitolo 6: creare un app per le funzioni di Azure</span><span class="sxs-lookup"><span data-stu-id="79b66-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="79b66-302">Creare una app per le funzioni di Azure, che verrà chiamata dall'applicazione desktop per aggiornare il servizio **tabelle** e inviare una notifica tramite l' **Hub di notifica**.</span><span class="sxs-lookup"><span data-stu-id="79b66-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="79b66-303">In primo luogo, è necessario creare un file che consentirà alla funzione di Azure di caricare le librerie necessarie.</span><span class="sxs-lookup"><span data-stu-id="79b66-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="79b66-304">Aprire **blocco note** (premere il tasto Windows e digitare blocco note).</span><span class="sxs-lookup"><span data-stu-id="79b66-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![Apri blocco note](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="79b66-306">Con blocco note aperto, inserire la struttura JSON riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b66-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="79b66-307">Una volta completata questa operazione, salvarla sul desktop come **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="79b66-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="79b66-308">È importante che la denominazione sia corretta: assicurarsi che non sia **presente un'estensione di file txt** .</span><span class="sxs-lookup"><span data-stu-id="79b66-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="79b66-309">Questo file definisce le librerie che la funzione userà, se è stato usato NuGet, avrà un aspetto familiare.</span><span class="sxs-lookup"><span data-stu-id="79b66-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="79b66-310">Accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="79b66-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="79b66-311">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare **app per le funzioni**, quindi premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="79b66-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![Cerca app per le funzioni](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="79b66-313">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="79b66-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="79b66-314">La nuova pagina fornirà una descrizione del servizio **app per le funzioni** .</span><span class="sxs-lookup"><span data-stu-id="79b66-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="79b66-315">Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![istanza dell'app per le funzioni](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="79b66-317">Una volta fatto clic su **Crea**, compilare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="79b66-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="79b66-318">Per **nome app**, inserire il nome desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="79b66-319">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="79b66-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="79b66-320">Selezionare il piano tariffario appropriato, se è la prima volta che si crea un **servizio app per le funzioni**, sarà disponibile un livello gratuito.</span><span class="sxs-lookup"><span data-stu-id="79b66-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="79b66-321">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="79b66-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79b66-322">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="79b66-323">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="79b66-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="79b66-324">Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="79b66-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="79b66-325">Per **sistema operativo**, fare clic su Windows, che corrisponde alla piattaforma desiderata.</span><span class="sxs-lookup"><span data-stu-id="79b66-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="79b66-326">Selezionare un **piano di hosting** . questa esercitazione usa un **piano a consumo**.</span><span class="sxs-lookup"><span data-stu-id="79b66-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="79b66-327">Selezionare un **percorso** **(scegliere la stessa posizione della risorsa di archiviazione compilata nel passaggio precedente)**</span><span class="sxs-lookup"><span data-stu-id="79b66-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="79b66-328">Per la sezione **archiviazione** **è necessario selezionare il servizio di archiviazione creato nel passaggio precedente**.</span><span class="sxs-lookup"><span data-stu-id="79b66-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="79b66-329">Non sarà necessario *Application Insights* in questa app, quindi è possibile lasciarla disattivata.</span><span class="sxs-lookup"><span data-stu-id="79b66-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="79b66-330">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="79b66-330">Click **Create**.</span></span>

        ![Crea nuova istanza](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="79b66-332">Una volta fatto clic su **Crea** , è necessario attendere che il servizio venga creato. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="79b66-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="79b66-333">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="79b66-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nuova notifica](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="79b66-335">Fare clic sulle notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="79b66-336">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b66-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Vai alla risorsa](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="79b66-338">Fare clic **+** sull'icona (segno più) accanto a *funzioni*per crearne una *nuova*.</span><span class="sxs-lookup"><span data-stu-id="79b66-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Aggiungi nuova funzione](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="79b66-340">All'interno del pannello centrale verrà visualizzata la finestra di creazione della **funzione** .</span><span class="sxs-lookup"><span data-stu-id="79b66-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="79b66-341">Ignorare le informazioni nella metà superiore del pannello e fare clic su **funzione personalizzata**, posizionata nella parte inferiore dell'area blu, come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b66-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="79b66-343">La nuova pagina all'interno della finestra mostrerà vari tipi di funzione.</span><span class="sxs-lookup"><span data-stu-id="79b66-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="79b66-344">Scorrere verso il basso per visualizzare i tipi viola, quindi fare clic su elemento **http put** .</span><span class="sxs-lookup"><span data-stu-id="79b66-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![collegamento http put](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="79b66-346">Potrebbe essere necessario scorrere verso il basso la pagina (e questa immagine potrebbe non essere esattamente identica, se si sono verificati aggiornamenti del portale di Azure), tuttavia, si cerca un elemento denominato *http put*.</span><span class="sxs-lookup"><span data-stu-id="79b66-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="79b66-347">Verrà visualizzata la finestra **PUT http** in cui è necessario configurare la funzione (vedere di seguito per l'immagine).</span><span class="sxs-lookup"><span data-stu-id="79b66-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="79b66-348">Per **lingua** scegliere C\#dal menu a discesa.</span><span class="sxs-lookup"><span data-stu-id="79b66-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="79b66-349">Per **nome** immettere un nome appropriato.</span><span class="sxs-lookup"><span data-stu-id="79b66-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="79b66-350">Nel menu a discesa **livello di autenticazione** selezionare **funzione**.</span><span class="sxs-lookup"><span data-stu-id="79b66-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="79b66-351">Per la sezione **nome tabella** è necessario usare il nome esatto usato per creare il servizio **tabelle** in precedenza (incluso lo stesso caso della lettera).</span><span class="sxs-lookup"><span data-stu-id="79b66-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="79b66-352">Nella sezione **connessione dell'account di archiviazione** usare il menu a discesa e selezionare l'account di archiviazione da qui.</span><span class="sxs-lookup"><span data-stu-id="79b66-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="79b66-353">In caso contrario, fare clic sul collegamento ipertestuale **nuovo** accanto al titolo della sezione per visualizzare un altro pannello in cui è necessario elencare l'account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![nuova risorsa di archiviazione](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="79b66-355">Fare clic su **Crea** . si riceverà una notifica che segnala che le impostazioni sono state aggiornate correttamente.</span><span class="sxs-lookup"><span data-stu-id="79b66-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![Create (funzione)](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="79b66-357">Dopo aver fatto clic su **Crea**, si verrà reindirizzati all'editor di funzioni.</span><span class="sxs-lookup"><span data-stu-id="79b66-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![aggiornare il codice della funzione](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="79b66-359">Inserire il codice seguente nell'editor di funzioni (sostituendo il codice nella funzione):</span><span class="sxs-lookup"><span data-stu-id="79b66-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="79b66-360">Usando le librerie incluse, la funzione riceve il nome e il percorso dell'oggetto che è stato spostato nella scena Unity (come C# oggetto, denominato **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="79b66-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="79b66-361">Questo oggetto viene quindi utilizzato per aggiornare i parametri dell'oggetto all'interno della tabella creata.</span><span class="sxs-lookup"><span data-stu-id="79b66-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="79b66-362">In seguito, la funzione effettua una chiamata al servizio Hub di notifica creato, che notifica tutte le applicazioni sottoscritte.</span><span class="sxs-lookup"><span data-stu-id="79b66-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="79b66-363">Con il codice sul posto, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="79b66-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="79b66-364">Fare quindi clic **\<** sull'icona (freccia) sul lato destro della pagina.</span><span class="sxs-lookup"><span data-stu-id="79b66-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Apri il pannello di caricamento](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="79b66-366">Un pannello scorrerà verso destra.</span><span class="sxs-lookup"><span data-stu-id="79b66-366">A panel will slide in from the right.</span></span> <span data-ttu-id="79b66-367">In tale pannello fare clic su **carica**e verrà visualizzato un browser file.</span><span class="sxs-lookup"><span data-stu-id="79b66-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="79b66-368">Passare a e fare clic sul file **Project. JSON** , creato in precedenza nel **blocco note** , quindi fare clic sul pulsante **Apri** .</span><span class="sxs-lookup"><span data-stu-id="79b66-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="79b66-369">Questo file definisce le librerie che la funzione utilizzerà.</span><span class="sxs-lookup"><span data-stu-id="79b66-369">This file defines the libraries that your function will use.</span></span>

    ![carica JSON](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="79b66-371">Quando il file è stato caricato, verrà visualizzato nel pannello a destra.</span><span class="sxs-lookup"><span data-stu-id="79b66-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="79b66-372">Facendo clic su di esso verrà aperto nell'editor di **funzioni** .</span><span class="sxs-lookup"><span data-stu-id="79b66-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="79b66-373">Deve essere **esattamente** uguale all'immagine successiva (al passaggio 23).</span><span class="sxs-lookup"><span data-stu-id="79b66-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="79b66-374">Quindi, nel pannello a sinistra, sotto **funzioni**, fare clic sul collegamento **integra** .</span><span class="sxs-lookup"><span data-stu-id="79b66-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![integra funzione](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="79b66-376">Nella pagina successiva, nell'angolo in alto a destra, fare clic su **Editor avanzato** (come indicato di seguito).</span><span class="sxs-lookup"><span data-stu-id="79b66-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![editor avanzato aperto](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="79b66-378">Un file **Function. JSON** verrà aperto nel pannello centrale, che deve essere sostituito con il frammento di codice seguente.</span><span class="sxs-lookup"><span data-stu-id="79b66-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="79b66-379">Definisce la funzione che si sta compilando e i parametri passati alla funzione.</span><span class="sxs-lookup"><span data-stu-id="79b66-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="79b66-380">L'editor dovrebbe ora apparire come l'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="79b66-380">Your editor should now look like the image below:</span></span>

    ![Torna all'editor standard](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="79b66-382">È possibile notare che i parametri di input appena inseriti potrebbero non corrispondere ai dettagli della tabella e dell'archiviazione e pertanto dovranno essere aggiornati con le informazioni.</span><span class="sxs-lookup"><span data-stu-id="79b66-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="79b66-383">**Questa operazione non**viene eseguita in questo argomento, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b66-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="79b66-384">È sufficiente fare clic sul collegamento dell' **editor standard** , nell'angolo in alto a destra della pagina, per tornare indietro.</span><span class="sxs-lookup"><span data-stu-id="79b66-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="79b66-385">Tornare all' **editor standard**, fare clic su **archiviazione tabelle di Azure (tabella)** in **input**.</span><span class="sxs-lookup"><span data-stu-id="79b66-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Input tabella](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="79b66-387">Assicurarsi che **le informazioni seguenti** corrispondano alle informazioni, in quanto potrebbero essere diverse (esiste un'immagine sotto la seguente procedura):</span><span class="sxs-lookup"><span data-stu-id="79b66-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="79b66-388">**Nome tabella**: il nome della tabella creata nel servizio tabelle di archiviazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="79b66-389">**Connessione dell'account di archiviazione:** fare clic su **nuovo**, che viene visualizzato accanto al menu a discesa e un pannello verrà visualizzato a destra della finestra.</span><span class="sxs-lookup"><span data-stu-id="79b66-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![nuova risorsa di archiviazione](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="79b66-391">Selezionare l' **account di archiviazione**creato in precedenza per ospitare le app per le **funzioni.**</span><span class="sxs-lookup"><span data-stu-id="79b66-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="79b66-392">Si noterà che il valore di connessione dell' **account di archiviazione** è stato creato.</span><span class="sxs-lookup"><span data-stu-id="79b66-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="79b66-393">Assicurarsi di premere **Salva** al termine dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="79b66-394">La pagina **input** dovrebbe ora corrispondere a quanto riportato di seguito, mostrando **le** informazioni.</span><span class="sxs-lookup"><span data-stu-id="79b66-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![input completati](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="79b66-396">Fare quindi clic su **Hub di notifica di Azure (notifica)** , in **output**.</span><span class="sxs-lookup"><span data-stu-id="79b66-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="79b66-397">Verificare che le informazioni riportate di seguito corrispondano a quelle dell' **utente** , in quanto potrebbero essere diverse (esiste un'immagine sotto la seguente procedura):</span><span class="sxs-lookup"><span data-stu-id="79b66-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="79b66-398">**Nome Hub di notifica**: è il nome dell'istanza del servizio **Hub di notifica** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79b66-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="79b66-399">**Connessione spazio dei nomi di hub di notifica**: fare clic su **nuovo**, che viene visualizzato accanto al menu a discesa.</span><span class="sxs-lookup"><span data-stu-id="79b66-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![Controlla output](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="79b66-401">Verrà visualizzato il popup della **connessione** (vedere l'immagine seguente), in cui è necessario selezionare lo **spazio dei nomi** dell' **Hub di notifica**, configurato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79b66-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="79b66-402">Nel menu a discesa centrale selezionare il nome dell' **Hub di notifica** .</span><span class="sxs-lookup"><span data-stu-id="79b66-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="79b66-403">Impostare il menu a discesa **criterio** su **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="79b66-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="79b66-404">Fare clic sul pulsante **Seleziona** per tornare indietro.</span><span class="sxs-lookup"><span data-stu-id="79b66-404">Click the **Select** button to go back.</span></span>

        ![aggiornamento dell'output](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="79b66-406">La pagina degli **output** dovrebbe ora corrispondere a quanto segue, ma con **le** informazioni.</span><span class="sxs-lookup"><span data-stu-id="79b66-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="79b66-407">Assicurarsi di premere **Salva**.</span><span class="sxs-lookup"><span data-stu-id="79b66-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="79b66-408">Non *modificare direttamente il nome dell'hub di notifica* Questa operazione dovrebbe essere eseguita con il **Editor avanzato**, purché siano stati eseguiti correttamente i passaggi precedenti.</span><span class="sxs-lookup"><span data-stu-id="79b66-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![output completati](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="79b66-410">A questo punto, è necessario testare la funzione per verificare che funzioni.</span><span class="sxs-lookup"><span data-stu-id="79b66-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="79b66-411">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="79b66-411">To do this:</span></span> 

    1. <span data-ttu-id="79b66-412">Passare alla pagina della funzione ancora una volta:</span><span class="sxs-lookup"><span data-stu-id="79b66-412">Navigate to the function page once more:</span></span>

        ![output completati](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="79b66-414">Tornare alla pagina funzione, fare clic sulla scheda **test** al lato destro della pagina per aprire il pannello *test* :</span><span class="sxs-lookup"><span data-stu-id="79b66-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![output completati](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="79b66-416">Nella casella di testo **corpo della richiesta** del pannello incollare il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="79b66-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="79b66-417">Con il codice di test, fare clic sul pulsante **Run (Esegui** ) in basso a destra e il test verrà eseguito.</span><span class="sxs-lookup"><span data-stu-id="79b66-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="79b66-418">I log di output del test verranno visualizzati nell'area della console, sotto il codice della funzione.</span><span class="sxs-lookup"><span data-stu-id="79b66-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![output completati](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="79b66-420">Se il test precedente non riesce, è necessario verificare di aver seguito esattamente i passaggi precedenti, in particolare le impostazioni nel **Pannello integra**.</span><span class="sxs-lookup"><span data-stu-id="79b66-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="79b66-421">Capitolo 7: configurare il progetto di Unity desktop</span><span class="sxs-lookup"><span data-stu-id="79b66-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79b66-422">L'applicazione desktop attualmente creata **non** funzionerà nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="79b66-423">Deve essere eseguito all'esterno dell'editor, dopo la compilazione dell'applicazione, usando Visual Studio (o l'applicazione distribuita).</span><span class="sxs-lookup"><span data-stu-id="79b66-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="79b66-424">Di seguito è riportata una configurazione tipica per lo sviluppo con Unity e realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="79b66-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="79b66-425">Configurare e testare l'auricolare immersiva della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="79b66-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="79b66-426">**Non** sarà necessario alcun controller di movimento per questo corso.</span><span class="sxs-lookup"><span data-stu-id="79b66-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="79b66-427">Se è necessario supportare la configurazione dell'auricolare immersivo, seguire questo [collegamento per configurare la realtà mista di Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="79b66-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="79b66-428">Aprire **Unity** e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="79b66-428">Open **Unity** and click **New**.</span></span>

    ![nuovo progetto Unity](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="79b66-430">È necessario specificare un nome di progetto Unity, inserire **UnityDesktopNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="79b66-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="79b66-431">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="79b66-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="79b66-432">Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="79b66-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="79b66-433">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="79b66-433">Then, click **Create project**.</span></span>

    ![Crea progetto](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="79b66-435">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79b66-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="79b66-436">Passare a **modifica** > **Preferenze** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="79b66-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="79b66-437">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="79b66-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="79b66-438">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="79b66-438">Close the **Preferences** window.</span></span>

    ![imposta strumenti esterni di Visual Studio](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="79b66-440">Passare quindi a**impostazioni di compilazione** **file** > e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="79b66-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![piattaforme switch](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="79b66-442">Sempre nelle**impostazioni di compilazione** **file** > , verificare che:</span><span class="sxs-lookup"><span data-stu-id="79b66-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="79b66-443">Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="79b66-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="79b66-444">Questa applicazione sarà per il desktop, quindi deve essere **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="79b66-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="79b66-445">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="79b66-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="79b66-446">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="79b66-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="79b66-447">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="79b66-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="79b66-448">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="79b66-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="79b66-449">Sebbene qui valga la pena salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="79b66-450">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="79b66-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="79b66-451">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="79b66-451">A save window will appear.</span></span>

            ![Aggiungi scene aperte](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="79b66-453">Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.</span><span class="sxs-lookup"><span data-stu-id="79b66-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nuova cartella scenes](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="79b66-455">Aprire la cartella **Scenes** appena creata e quindi, nel campo **nome file:** testo, digitare **NH\_Desktop\_scene**, quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="79b66-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![nuovo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="79b66-457">Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="79b66-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="79b66-458">Nella stessa finestra fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .</span><span class="sxs-lookup"><span data-stu-id="79b66-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="79b66-459">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="79b66-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="79b66-460">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="79b66-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="79b66-461">La **versione di runtime** di scripting deve essere **sperimentale (equivalente a .NET 4,6)**</span><span class="sxs-lookup"><span data-stu-id="79b66-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="79b66-462">Il **back-end** di scripting deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="79b66-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="79b66-463">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="79b66-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4,6 versione NET](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="79b66-465">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="79b66-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="79b66-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="79b66-466">**InternetClient**</span></span>

            ![Seleziona client Internet](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="79b66-468">Nelle **impostazioni di compilazione** i progetti di *Unity C\#*  non sono più disattivati; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="79b66-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="79b66-469">Chiudere la finestra **impostazioni di compilazione** .</span><span class="sxs-lookup"><span data-stu-id="79b66-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="79b66-470">Salva la scena e il progetto Salva **file** > di**scena/**  > **Salva**file.</span><span class="sxs-lookup"><span data-stu-id="79b66-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="79b66-471">Se si vuole ignorare il componente di *configurazione Unity* per questo progetto (app desktop) e continuare direttamente con il codice, è possibile [scaricare questo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="79b66-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="79b66-472">Sarà comunque necessario aggiungere i componenti di script.</span><span class="sxs-lookup"><span data-stu-id="79b66-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="79b66-473">Capitolo 8-importazione delle dll in Unity</span><span class="sxs-lookup"><span data-stu-id="79b66-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="79b66-474">Si utilizzerà archiviazione di Azure per Unity (che a sua volta USA .NET SDK per Azure).</span><span class="sxs-lookup"><span data-stu-id="79b66-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="79b66-475">Per altre informazioni, seguire questo [collegamento su archiviazione di Azure per Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="79b66-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="79b66-476">Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="79b66-477">Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.</span><span class="sxs-lookup"><span data-stu-id="79b66-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="79b66-478">Per importare l'SDK nel progetto, assicurarsi di aver scaricato la versione più recente di [**file unitypackage Tools**](https://aka.ms/azstorage-unitysdk) da GitHub.</span><span class="sxs-lookup"><span data-stu-id="79b66-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="79b66-479">Eseguire quindi le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-479">Then, do the following:</span></span>

1.  <span data-ttu-id="79b66-480">Aggiungere il **file unitypackage Tools** a Unity usando l'opzione di menu  **\> asset \> Import Package Custom Package** .</span><span class="sxs-lookup"><span data-stu-id="79b66-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="79b66-481">Nella casella **Importa pacchetto Unity** visualizzata è possibile selezionare tutti gli elementi sotto \* \**plugin* \> \* storage \* \* \*.</span><span class="sxs-lookup"><span data-stu-id="79b66-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="79b66-482">Deselezionare tutti gli altri elementi, perché non sono necessari per questo corso.</span><span class="sxs-lookup"><span data-stu-id="79b66-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Importa nel pacchetto](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="79b66-484">Fare clic sul pulsante ***Importa*** per aggiungere gli elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="79b66-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="79b66-485">Passare alla cartella **archiviazione** in **plug** -in nella visualizzazione del progetto e selezionare *solo*i plug-in seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="79b66-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="79b66-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="79b66-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="79b66-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="79b66-488">Microsoft. WindowsAzure. storage</span><span class="sxs-lookup"><span data-stu-id="79b66-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="79b66-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="79b66-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="79b66-490">System. Spatial</span><span class="sxs-lookup"><span data-stu-id="79b66-490">System.Spatial</span></span>

![deseleziona qualsiasi piattaforma](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="79b66-492">Con *questi plug* -in specifici selezionati, **deselezionare** **qualsiasi piattaforma** e **deselezionare** **WSAPlayer** , quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="79b66-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![applica dll della piattaforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="79b66-494">Questi specifici plug-in vengono contrassegnati per essere usati solo nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="79b66-495">Questo è dovuto al fatto che esistono versioni diverse degli stessi plug-in nella cartella WSA che verranno usate dopo l'esportazione del progetto da Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="79b66-496">Nella cartella plugin di **archiviazione** selezionare solo:</span><span class="sxs-lookup"><span data-stu-id="79b66-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="79b66-497">Microsoft. Data. Services. client</span><span class="sxs-lookup"><span data-stu-id="79b66-497">Microsoft.Data.Services.Client</span></span>

        ![impostazione non elabora per le dll](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="79b66-499">Selezionare la casella **non elaborare** in **Impostazioni piattaforma** e fare clic su ***applica***.</span><span class="sxs-lookup"><span data-stu-id="79b66-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="79b66-501">Si sta contrassegnando questo plug-in "non elaborare", perché il plug-in assembly Unity ha difficoltà nell'elaborare questo plug-in.</span><span class="sxs-lookup"><span data-stu-id="79b66-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="79b66-502">Il plug-in continuerà a funzionare anche se non viene elaborato.</span><span class="sxs-lookup"><span data-stu-id="79b66-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="79b66-503">Capitolo 9: creare la classe TableToScene nel progetto di Unity desktop</span><span class="sxs-lookup"><span data-stu-id="79b66-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="79b66-504">È ora necessario creare gli script contenenti il codice per eseguire questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="79b66-505">Il primo script che è necessario creare è **TableToScene**, responsabile di:</span><span class="sxs-lookup"><span data-stu-id="79b66-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="79b66-506">Lettura di entità all'interno della tabella di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="79b66-507">Utilizzando i dati della tabella, determinare gli oggetti da generare e in quale posizione.</span><span class="sxs-lookup"><span data-stu-id="79b66-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="79b66-508">Il secondo script che è necessario creare è **CloudScene**, responsabile di:</span><span class="sxs-lookup"><span data-stu-id="79b66-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="79b66-509">Registrazione dell'evento di clic per consentire all'utente di trascinare gli oggetti intorno alla scena.</span><span class="sxs-lookup"><span data-stu-id="79b66-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="79b66-510">Serializzare i dati dell'oggetto da questa scena Unity e inviarli al app per le funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="79b66-511">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="79b66-511">To create this class:</span></span>

1.  <span data-ttu-id="79b66-512">Fare clic con il pulsante destro del mouse nella cartella **Asset** che si trova nel pannello progetto, ovvero **Crea** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="79b66-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="79b66-513">Denominare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="79b66-513">Name the folder **Scripts**.</span></span>

    ![Crea cartella script](images/AzureLabs-Lab8-66.png)

    ![Creazione cartella script 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="79b66-516">Fare doppio clic sulla cartella appena creata per aprirla.</span><span class="sxs-lookup"><span data-stu-id="79b66-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="79b66-517">Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="79b66-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="79b66-518">Denominare lo script **TableToScene**.</span><span class="sxs-lookup"><span data-stu-id="79b66-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="79b66-519">![nuovo TableToScene script](images/AzureLabs-Lab8-68.png)
    ![c# Rinomina](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="79b66-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="79b66-520">Fare doppio clic sullo script per aprirlo in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="79b66-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="79b66-521">Aggiungere gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="79b66-522">All'interno della classe, inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="79b66-523">Sostituire il valore AccountName con il nome del servizio di archiviazione di Azure e il valore **AccountKey** con il valore di chiave trovato nel servizio di archiviazione di Azure, nel portale di Azure (vedere l'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="79b66-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![Recupera chiave dell'account](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="79b66-525">A questo punto aggiungere i metodi **Start ()** e **svegli ()** per inizializzare la classe.</span><span class="sxs-lookup"><span data-stu-id="79b66-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="79b66-526">All'interno della classe **TableToScene** aggiungere il metodo che recupererà i valori dalla tabella di Azure e li userà per generare le primitive appropriate nella scena.</span><span class="sxs-lookup"><span data-stu-id="79b66-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="79b66-527">Al di fuori della classe **TableToScene** , è necessario definire la classe usata dall'applicazione per serializzare e deserializzare le **entità di tabella**.</span><span class="sxs-lookup"><span data-stu-id="79b66-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="79b66-528">Assicurarsi di **salvare** prima di tornare all'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="79b66-529">Fare clic sulla **fotocamera principale** nel pannello **gerarchia** , in modo che le relative proprietà vengano visualizzate nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="79b66-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="79b66-530">Con la cartella degli **script** aperta, selezionare il **file TableToScene** dello script e trascinarlo sulla **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="79b66-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="79b66-531">Il risultato dovrebbe essere il seguente:</span><span class="sxs-lookup"><span data-stu-id="79b66-531">The result should be as below:</span></span>

    ![aggiungere lo script alla fotocamera principale](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="79b66-533">Capitolo 10: creare la classe CloudScene nel progetto di Unity desktop</span><span class="sxs-lookup"><span data-stu-id="79b66-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="79b66-534">Il secondo script che è necessario creare è **CloudScene**, responsabile di:</span><span class="sxs-lookup"><span data-stu-id="79b66-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="79b66-535">Registrazione dell'evento di clic per consentire all'utente di trascinare gli oggetti intorno alla scena.</span><span class="sxs-lookup"><span data-stu-id="79b66-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="79b66-536">Serializzare i dati dell'oggetto da questa scena Unity e inviarli al app per le funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b66-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="79b66-537">Per creare il secondo script:</span><span class="sxs-lookup"><span data-stu-id="79b66-537">To create the second script:</span></span>

1.  <span data-ttu-id="79b66-538">Fare clic con il pulsante destro del mouse all'interno della cartella **script** , quindi scegliere **Crea**, **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="79b66-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="79b66-539">Denominare lo script **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="79b66-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="79b66-540">![nuovo script](images/AzureLabs-Lab8-72.png)
    ![c# rinominare CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="79b66-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="79b66-541">Aggiungere gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="79b66-542">Inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="79b66-543">Sostituire il valore di **azureFunctionEndpoint** con l'URL del app per le funzioni di Azure trovato nel servizio app per le funzioni di Azure, nel portale di Azure, come illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="79b66-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![Ottenere l'URL della funzione](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="79b66-545">A questo punto aggiungere i metodi **Start ()** e **svegli ()** per inizializzare la classe.</span><span class="sxs-lookup"><span data-stu-id="79b66-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="79b66-546">All'interno del metodo **Update ()** aggiungere il codice seguente che rileverà l'input e il trascinamento del mouse, che a sua volta sposta GameObject nella scena.</span><span class="sxs-lookup"><span data-stu-id="79b66-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="79b66-547">Se l'utente ha trascinato e rilasciato un oggetto, passerà il nome e le coordinate dell'oggetto al metodo **UpdateCloudScene ()** , che chiamerà il servizio app per le funzioni di Azure, che aggiornerà la tabella di Azure e attiverà la notifica.</span><span class="sxs-lookup"><span data-stu-id="79b66-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="79b66-548">A questo punto aggiungere il metodo **UpdateCloudScene ()** , come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="79b66-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="79b66-549">Salvare il codice e tornare a Unity</span><span class="sxs-lookup"><span data-stu-id="79b66-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="79b66-550">Trascinare lo script **CloudScene** sulla **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="79b66-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="79b66-551">Fare clic sulla **fotocamera principale** nel pannello **gerarchia** , in modo che le relative proprietà vengano visualizzate nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="79b66-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="79b66-552">Con la cartella degli **script** aperta, selezionare lo script **CloudScene** e trascinarlo sulla **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="79b66-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="79b66-553">Il risultato dovrebbe essere il seguente:</span><span class="sxs-lookup"><span data-stu-id="79b66-553">The result should be as below:</span></span>

        > ![Trascinare lo script cloud sulla fotocamera principale](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="79b66-555">Capitolo 11: compilare il progetto desktop in UWP</span><span class="sxs-lookup"><span data-stu-id="79b66-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="79b66-556">Tutti gli elementi necessari per la sezione Unity di questo progetto sono ora completati.</span><span class="sxs-lookup"><span data-stu-id="79b66-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="79b66-557">Passare a **impostazioni di compilazione** (**impostazioni di compilazione** **file** > ).</span><span class="sxs-lookup"><span data-stu-id="79b66-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="79b66-558">Nella finestra **impostazioni di compilazione** fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="79b66-558">From the **Build Settings** window, click **Build**.</span></span>

    ![Compila progetto](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="79b66-560">Verrà visualizzata una finestra **Esplora file** con la richiesta di un percorso da compilare.</span><span class="sxs-lookup"><span data-stu-id="79b66-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="79b66-561">Creare una nuova cartella (facendo clic su **nuova cartella** nell'angolo superiore sinistro) e denominarla compilata.</span><span class="sxs-lookup"><span data-stu-id="79b66-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![nuova cartella per la compilazione](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="79b66-563">Aprire la nuova cartella compilazioni e creare un'altra cartella (usando una **nuova cartella** ancora una volta) e denominarla **\_NH Desktop\_app**.</span><span class="sxs-lookup"><span data-stu-id="79b66-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![nome cartella NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="79b66-565">Con l' **app\_Desktop\_di NH** selezionata.</span><span class="sxs-lookup"><span data-stu-id="79b66-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="79b66-566">Fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="79b66-566">click **Select Folder**.</span></span> <span data-ttu-id="79b66-567">La compilazione del progetto verrà eseguita per un minuto.</span><span class="sxs-lookup"><span data-stu-id="79b66-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="79b66-568">Nella compilazione seguente verrà visualizzato **Esplora file** che indica il percorso del nuovo progetto.</span><span class="sxs-lookup"><span data-stu-id="79b66-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="79b66-569">Tuttavia, non è necessario aprirlo, perché è necessario creare prima l'altro progetto Unity nei prossimi capitoli.</span><span class="sxs-lookup"><span data-stu-id="79b66-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="79b66-570">Capitolo 12: configurare un progetto Unity per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="79b66-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="79b66-571">Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="79b66-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="79b66-572">Aprire **Unity** e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="79b66-572">Open **Unity** and click **New**.</span></span>

    ![nuovo progetto Unity](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="79b66-574">A questo punto sarà necessario specificare un nome di progetto Unity, inserire **UnityMRNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="79b66-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="79b66-575">Verificare che il tipo di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="79b66-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="79b66-576">Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="79b66-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="79b66-577">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="79b66-577">Then, click **Create project**.</span></span>

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="79b66-579">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79b66-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="79b66-580">Passare a **modifica** > **Preferenze** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="79b66-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="79b66-581">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="79b66-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="79b66-582">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="79b66-582">Close the **Preferences** window.</span></span>

    ![imposta editor esterno su Visual Studio](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="79b66-584">Passare quindi a**impostazioni di compilazione** **file** > e passare alla piattaforma **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="79b66-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![passare da una piattaforma all'altra a UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="79b66-586">Passare a**impostazioni di compilazione** **file** > e verificare che:</span><span class="sxs-lookup"><span data-stu-id="79b66-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="79b66-587">Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="79b66-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="79b66-588">Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="79b66-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="79b66-589">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="79b66-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="79b66-590">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="79b66-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="79b66-591">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="79b66-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="79b66-592">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="79b66-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="79b66-593">Sebbene qui valga la pena salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="79b66-594">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="79b66-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="79b66-595">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="79b66-595">A save window will appear.</span></span>

            ![Aggiungi scene aperte](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="79b66-597">Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.</span><span class="sxs-lookup"><span data-stu-id="79b66-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nuova cartella scenes](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="79b66-599">Aprire la cartella **Scenes** appena creata e quindi nel campo **nome file:** testo digitare **\_NH Mr\_scene**, quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="79b66-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![nuova scena-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="79b66-601">Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="79b66-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="79b66-602">Nella stessa finestra fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .</span><span class="sxs-lookup"><span data-stu-id="79b66-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![Apri Impostazioni lettore](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="79b66-604">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="79b66-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="79b66-605">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="79b66-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="79b66-606">La **versione di runtime** di scripting deve essere **sperimentale** (equivalente a .NET 4,6)</span><span class="sxs-lookup"><span data-stu-id="79b66-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="79b66-607">Il **back-end** di scripting deve essere ***.NET***</span><span class="sxs-lookup"><span data-stu-id="79b66-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="79b66-608">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="79b66-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![compatibilità API](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="79b66-610">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="79b66-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![aggiornare le impostazioni di XR](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="79b66-612">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, Heck:</span><span class="sxs-lookup"><span data-stu-id="79b66-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="79b66-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="79b66-613">**InternetClient**</span></span>           

            ![Seleziona client Internet](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="79b66-615">Nelle **impostazioni di compilazione**, **i C# progetti Unity** non sono più disattivati: selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="79b66-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="79b66-616">Al termine di queste modifiche, chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="79b66-617">Salva la scena e il progetto Salva **file** > di**scena/**  > **Salva**file.</span><span class="sxs-lookup"><span data-stu-id="79b66-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="79b66-618">Se si vuole ignorare il componente di *configurazione Unity* per questo progetto (app realtà mista) e continuare direttamente con il codice, è possibile [scaricare questo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare da [ Capitolo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="79b66-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="79b66-619">Sarà comunque necessario aggiungere i componenti di script.</span><span class="sxs-lookup"><span data-stu-id="79b66-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="79b66-620">Capitolo 13-importazione delle dll nel progetto di Unity per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="79b66-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="79b66-621">Verrà usata la libreria di archiviazione di Azure per Unity (che usa .NET SDK per Azure).</span><span class="sxs-lookup"><span data-stu-id="79b66-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="79b66-622">Seguire questo collegamento per l' [uso di archiviazione di Azure con Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="79b66-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="79b66-623">Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="79b66-624">Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.</span><span class="sxs-lookup"><span data-stu-id="79b66-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="79b66-625">Per importare l'SDK nel progetto, assicurarsi di aver scaricato la versione più recente di [. file unitypackage Tools](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="79b66-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="79b66-626">Eseguire quindi le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-626">Then, do the following:</span></span>

1.  <span data-ttu-id="79b66-627">Aggiungere il. file unitypackage Tools scaricato dal precedente a Unity usando l'opzione di menu **Asset** > **Import Package** > **Custom** Package.</span><span class="sxs-lookup"><span data-stu-id="79b66-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="79b66-628">Nella casella **Importa pacchetto Unity** visualizzata è possibile selezionare tutti gli elementi in**archiviazione** **plug** > -in.</span><span class="sxs-lookup"><span data-stu-id="79b66-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![Importa pacchetto](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="79b66-630">Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="79b66-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="79b66-631">Passare alla cartella **archiviazione** in **plug** -in nella visualizzazione del progetto e selezionare *solo*i plug-in seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="79b66-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="79b66-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="79b66-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="79b66-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="79b66-634">Microsoft. WindowsAzure. storage</span><span class="sxs-lookup"><span data-stu-id="79b66-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="79b66-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="79b66-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="79b66-636">System. Spatial</span><span class="sxs-lookup"><span data-stu-id="79b66-636">System.Spatial</span></span>

    ![Selezionare i plug-in](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="79b66-638">Con *questi plug* -in specifici selezionati, **deselezionare** **qualsiasi piattaforma** e **deselezionare** **WSAPlayer** , quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="79b66-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![applicare le modifiche alla piattaforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="79b66-640">Si sta contrassegnando questi plug-in particolari da usare solo nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="79b66-641">Questo è dovuto al fatto che esistono versioni diverse degli stessi plug-in nella cartella WSA che verranno usate dopo l'esportazione del progetto da Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="79b66-642">Nella cartella plugin di **archiviazione** selezionare solo:</span><span class="sxs-lookup"><span data-stu-id="79b66-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="79b66-643">Microsoft. Data. Services. client</span><span class="sxs-lookup"><span data-stu-id="79b66-643">Microsoft.Data.Services.Client</span></span>

        ![Selezione client Servizi dati](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="79b66-645">Selezionare la casella **non elaborare** in **Impostazioni piattaforma** e fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="79b66-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![non elaborare](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="79b66-647">Si sta contrassegnando questo plug-in "non elaborare" perché il plug-in assembly Unity ha difficoltà nell'elaborare questo plug-in.</span><span class="sxs-lookup"><span data-stu-id="79b66-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="79b66-648">Il plug-in continuerà a funzionare anche se non viene elaborato.</span><span class="sxs-lookup"><span data-stu-id="79b66-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="79b66-649">Capitolo 14-creazione della classe TableToScene nel progetto Unity della realtà mista</span><span class="sxs-lookup"><span data-stu-id="79b66-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="79b66-650">La classe **TableToScene** è identica a quella illustrata nel [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="79b66-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="79b66-651">Creare la stessa classe nel progetto Unity della realtà mista seguendo la stessa procedura descritta nel [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="79b66-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="79b66-652">Una volta completato questo capitolo, per entrambi i **progetti Unity** questa classe verrà configurata nella fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="79b66-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="79b66-653">Capitolo 15-creazione della classe NotificationReceiver nel progetto di Unity per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="79b66-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="79b66-654">Il secondo script che è necessario creare è **NotificationReceiver**, responsabile di:</span><span class="sxs-lookup"><span data-stu-id="79b66-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="79b66-655">Registrazione dell'app con l'hub di notifica al momento dell'inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="79b66-656">Ascolto delle notifiche provenienti dall'hub di notifica.</span><span class="sxs-lookup"><span data-stu-id="79b66-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="79b66-657">Deserializzazione dei dati dell'oggetto da notifiche ricevute.</span><span class="sxs-lookup"><span data-stu-id="79b66-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="79b66-658">Spostare GameObject nella scena in base ai dati deserializzati.</span><span class="sxs-lookup"><span data-stu-id="79b66-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="79b66-659">Per creare lo script **NotificationReceiver** :</span><span class="sxs-lookup"><span data-stu-id="79b66-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="79b66-660">Fare clic con il pulsante destro del mouse all'interno della cartella **script** , quindi scegliere **Crea**, **script C\#** .</span><span class="sxs-lookup"><span data-stu-id="79b66-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="79b66-661">Denominare lo script **NotificationReceiver**.</span><span class="sxs-lookup"><span data-stu-id="79b66-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="79b66-662">![creare un nuovo nome](images/AzureLabs-Lab8-95.png)
    di script![c# NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="79b66-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="79b66-663">Fare doppio clic sullo script per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="79b66-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="79b66-664">Aggiungere gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="79b66-665">Inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b66-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="79b66-666">Sostituire il valore di **hubName** con il nome del servizio Hub di notifica e il valore **hubListenEndpoint** con il valore dell'endpoint disponibile nella scheda criteri di accesso, servizio Hub di notifica di Azure nel portale di Azure (vedere l'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="79b66-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Inserisci endpoint dei criteri di hub di notifica](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="79b66-668">A questo punto aggiungere i metodi **Start ()** e **svegli ()** per inizializzare la classe.</span><span class="sxs-lookup"><span data-stu-id="79b66-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="79b66-669">Aggiungere il metodo **WaitForNotification** per consentire all'app di ricevere notifiche dalla libreria di hub di notifica senza conflitti con il thread principale:</span><span class="sxs-lookup"><span data-stu-id="79b66-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="79b66-670">Il metodo seguente, **InitNotificationAsync ()** , registrerà l'applicazione con il servizio Hub di notifica al momento dell'inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="79b66-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="79b66-671">Il codice è impostato come commento perché Unity non sarà in grado di compilare il progetto.</span><span class="sxs-lookup"><span data-stu-id="79b66-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="79b66-672">I commenti vengono rimossi quando si importa il pacchetto NuGet di messaggistica di Azure in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79b66-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="79b66-673">Il seguente gestore, **Channel\_PushNotificationReceived ()** , verrà attivato ogni volta che viene ricevuta una notifica.</span><span class="sxs-lookup"><span data-stu-id="79b66-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="79b66-674">La notifica verrà deserializzata, che sarà l'entità di tabella di Azure che è stata spostata nell'applicazione desktop, quindi spostare il GameObject corrispondente nella scena MR nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="79b66-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="79b66-675">Il codice è impostato come commento perché il codice fa riferimento alla libreria di messaggistica di Azure, che verrà aggiunta dopo aver compilato il progetto Unity usando Gestione pacchetti NuGet, all'interno di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79b66-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="79b66-676">Di conseguenza, il progetto Unity non sarà in grado di eseguire la compilazione, a meno che non sia impostato come commento. Tenere presente che, quando si compila il progetto e quindi si vuole tornare a Unity, è necessario aggiungere di **nuovo il commento** a tale codice.</span><span class="sxs-lookup"><span data-stu-id="79b66-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="79b66-677">Ricordarsi di salvare le modifiche prima di tornare all'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="79b66-678">Fare clic sulla **fotocamera principale** nel pannello **gerarchia** , in modo che le relative proprietà vengano visualizzate nel **controllo**.</span><span class="sxs-lookup"><span data-stu-id="79b66-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="79b66-679">Con la cartella degli **script** aperta, selezionare lo script **NotificationReceiver** e trascinarlo sulla **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="79b66-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="79b66-680">Il risultato dovrebbe essere il seguente:</span><span class="sxs-lookup"><span data-stu-id="79b66-680">The result should be as below:</span></span>

    ![Trascinare lo script del ricevitore di notifiche nella fotocamera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="79b66-682">Se si sta sviluppando questo per Microsoft HoloLens, sarà necessario aggiornare il componente della *fotocamera* della **fotocamera principale**, in modo che:</span><span class="sxs-lookup"><span data-stu-id="79b66-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="79b66-683">Cancella flag: Colore a tinta unita</span><span class="sxs-lookup"><span data-stu-id="79b66-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="79b66-684">Background: Nero</span><span class="sxs-lookup"><span data-stu-id="79b66-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="79b66-685">Capitolo 16: compilare il progetto di realtà mista in UWP</span><span class="sxs-lookup"><span data-stu-id="79b66-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="79b66-686">Questo capitolo è identico al processo di compilazione per il progetto precedente.</span><span class="sxs-lookup"><span data-stu-id="79b66-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="79b66-687">Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.</span><span class="sxs-lookup"><span data-stu-id="79b66-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="79b66-688">Passare a **impostazioni di compilazione** (**impostazioni di compilazione** **file** > ).</span><span class="sxs-lookup"><span data-stu-id="79b66-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="79b66-689">Dal menu **Impostazioni compilazione** verificare che **Unity C# progetti**\* sia selezionato (che consente di modificare gli script in questo progetto, dopo la compilazione).</span><span class="sxs-lookup"><span data-stu-id="79b66-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="79b66-690">Al termine, fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="79b66-690">After this is done, click **Build**.</span></span>

    ![Compila progetto](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="79b66-692">Verrà visualizzata una finestra **Esplora file** con la richiesta di un percorso da compilare.</span><span class="sxs-lookup"><span data-stu-id="79b66-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="79b66-693">Creare una nuova cartella (facendo clic su **nuova cartella** nell'angolo superiore sinistro) e denominarla compilata.</span><span class="sxs-lookup"><span data-stu-id="79b66-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Crea cartella compilazioni](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="79b66-695">Aprire la nuova cartella compilazioni e creare un'altra cartella (usando una **nuova cartella** ancora una volta) e denominarla **\_NH Mr\_app**.</span><span class="sxs-lookup"><span data-stu-id="79b66-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![Crea cartella NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="79b66-697">Con l' **app\_NH\_Mr** selezionata.</span><span class="sxs-lookup"><span data-stu-id="79b66-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="79b66-698">Fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="79b66-698">click **Select Folder**.</span></span> <span data-ttu-id="79b66-699">La compilazione del progetto verrà eseguita per un minuto.</span><span class="sxs-lookup"><span data-stu-id="79b66-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="79b66-700">Dopo la compilazione, viene aperta una finestra **Esplora file** nella posizione del nuovo progetto.</span><span class="sxs-lookup"><span data-stu-id="79b66-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="79b66-701">Capitolo 17: aggiungere pacchetti NuGet alla soluzione UnityMRNotifHub</span><span class="sxs-lookup"><span data-stu-id="79b66-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="79b66-702">Tenere presente che, una volta aggiunti i pacchetti NuGet seguenti (e rimuovere il commento dal codice nel [capitolo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)successivo), il codice, quando riaperto nel progetto Unity, presenta degli errori.</span><span class="sxs-lookup"><span data-stu-id="79b66-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="79b66-703">Se si vuole tornare indietro e continuare la modifica nell'editor di Unity, è necessario aggiungere un commento al codice errosome, quindi rimuovere il commento più tardi, quando si torna in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79b66-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="79b66-704">Una volta completata la compilazione di realtà mista, passare al progetto di realtà mista compilato, quindi fare doppio clic sul file di soluzione (con estensione sln) all'interno della cartella per aprire la soluzione con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="79b66-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="79b66-705">A questo punto sarà necessario aggiungere il pacchetto NuGet **WindowsAzure. Messaging. Managed** ; si tratta di una libreria usata per ricevere notifiche dall'hub di notifica.</span><span class="sxs-lookup"><span data-stu-id="79b66-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="79b66-706">Per importare il pacchetto NuGet:</span><span class="sxs-lookup"><span data-stu-id="79b66-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="79b66-707">Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione</span><span class="sxs-lookup"><span data-stu-id="79b66-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="79b66-708">Fare clic su **Gestisci pacchetti NuGet**.</span><span class="sxs-lookup"><span data-stu-id="79b66-708">Click on **Manage NuGet Packages**.</span></span>

    ![Apri Gestione NuGet](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="79b66-710">Selezionare la scheda ***Sfoglia*** e cercare **WindowsAzure. Messaging. Managed**.</span><span class="sxs-lookup"><span data-stu-id="79b66-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![trovare il pacchetto di messaggistica di Windows Azure](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="79b66-712">Selezionare il risultato (come illustrato di seguito) e nella finestra a destra selezionare la casella di controllo accanto a **progetto**.</span><span class="sxs-lookup"><span data-stu-id="79b66-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="79b66-713">Verrà inserito un segno di spunta nella casella di controllo accanto a **progetto**, insieme alla casella di controllo accanto al progetto **UnityMRNotifHub** e **CSharp assembly** .</span><span class="sxs-lookup"><span data-stu-id="79b66-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![Seleziona tutti i progetti](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="79b66-715">La versione fornita inizialmente **potrebbe non** essere compatibile con il progetto.</span><span class="sxs-lookup"><span data-stu-id="79b66-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="79b66-716">Quindi, fare clic sul menu a discesa accanto a **versione**, scegliere **versione 0.1.7.9**, quindi fare clic su **Installa**.</span><span class="sxs-lookup"><span data-stu-id="79b66-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="79b66-717">A questo punto è stata completata l'installazione del pacchetto NuGet.</span><span class="sxs-lookup"><span data-stu-id="79b66-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="79b66-718">Trovare il codice commentato immesso nella classe **NotificationReceiver** e rimuovere i commenti.</span><span class="sxs-lookup"><span data-stu-id="79b66-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="79b66-719">Capitolo 18: modificare l'applicazione UnityMRNotifHub, classe NotificationReceiver</span><span class="sxs-lookup"><span data-stu-id="79b66-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="79b66-720">Dopo aver aggiunto i **pacchetti NuGet**, sarà necessario rimuovere il *Commento* da parte del codice all'interno della classe **NotificationReceiver** .</span><span class="sxs-lookup"><span data-stu-id="79b66-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="79b66-721">È possibile creare, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="79b66-721">This includes:</span></span>

1. <span data-ttu-id="79b66-722">Lo spazio dei nomi nella parte superiore:</span><span class="sxs-lookup"><span data-stu-id="79b66-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="79b66-723">Tutto il codice all'interno del metodo **InitNotificationsAsync ()** :</span><span class="sxs-lookup"><span data-stu-id="79b66-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="79b66-724">Il codice precedente contiene un commento: assicurarsi che non sia stato accidentalmente annullato il *Commento* (poiché il codice non verrà compilato se si dispone di!).</span><span class="sxs-lookup"><span data-stu-id="79b66-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="79b66-725">Infine, l'evento **Channel_PushNotificationReceived** :</span><span class="sxs-lookup"><span data-stu-id="79b66-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="79b66-726">Con questi commenti, assicurarsi di salvare e quindi passare al capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="79b66-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="79b66-727">Capitolo 19: associare il progetto di realtà mista all'app dello Store</span><span class="sxs-lookup"><span data-stu-id="79b66-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="79b66-728">È ora necessario associare il progetto di **realtà mista** all'app dello Store creata in all'inizio del Lab.</span><span class="sxs-lookup"><span data-stu-id="79b66-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="79b66-729">Aprire la soluzione.</span><span class="sxs-lookup"><span data-stu-id="79b66-729">Open the solution.</span></span>

2.  <span data-ttu-id="79b66-730">Fare clic con il pulsante destro del mouse sul progetto di app UWP nel pannello Esplora soluzioni, passare all' **Archivio**e **associare l'app allo Store...** .</span><span class="sxs-lookup"><span data-stu-id="79b66-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![Apri associazione di archiviazione](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="79b66-732">Verrà visualizzata una nuova finestra denominata **associare l'app a Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="79b66-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="79b66-733">Fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="79b66-733">Click **Next**.</span></span>

    ![passa alla schermata successiva](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="79b66-735">Caricherà tutte le applicazioni associate all'account a cui è stato effettuato l'accesso.</span><span class="sxs-lookup"><span data-stu-id="79b66-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="79b66-736">Se non è stato effettuato l'accesso al proprio account, è possibile **accedere** a questa pagina.</span><span class="sxs-lookup"><span data-stu-id="79b66-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="79b66-737">Trovare il **nome dell'app dello Store** creato all'inizio di questa esercitazione e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="79b66-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="79b66-738">Scegliere quindi **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="79b66-738">Then click **Next**.</span></span>

    ![trovare e selezionare il nome dell'archivio](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="79b66-740">Fare clic su **associa**.</span><span class="sxs-lookup"><span data-stu-id="79b66-740">Click **Associate**.</span></span>

    ![associare l'app](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="79b66-742">L'app è ora **associata** all'app dello Store.</span><span class="sxs-lookup"><span data-stu-id="79b66-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="79b66-743">Questa operazione è necessaria per abilitare le notifiche.</span><span class="sxs-lookup"><span data-stu-id="79b66-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="79b66-744">Capitolo 20: distribuire applicazioni UnityMRNotifHub e UnityDesktopNotifHub</span><span class="sxs-lookup"><span data-stu-id="79b66-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="79b66-745">Questo capitolo può essere più semplice con due persone, in quanto il risultato includerà sia le app che eseguono, una in esecuzione sul desktop del computer che l'altra all'interno dell'auricolare immersiva.</span><span class="sxs-lookup"><span data-stu-id="79b66-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="79b66-746">L'app immersive per la cuffia è in attesa di ricevere le modifiche apportate alla scena (posizione delle modifiche della GameObject locale) e l'app desktop apporterà modifiche alla scena locale (modifiche alla posizione), che verranno condivise nell'app MR.</span><span class="sxs-lookup"><span data-stu-id="79b66-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="79b66-747">È opportuno distribuire prima l'app MR, seguita dall'app desktop, in modo che il ricevitore possa iniziare l'ascolto.</span><span class="sxs-lookup"><span data-stu-id="79b66-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="79b66-748">Per distribuire l'app **UnityMRNotifHub** nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="79b66-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="79b66-749">Aprire il file di soluzione dell'app **UnityMRNotifHub** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="79b66-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="79b66-750">Nella **piattaforma soluzione**selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="79b66-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="79b66-751">Nella **configurazione della soluzione** selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="79b66-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![Imposta configurazione progetto](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="79b66-753">Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.</span><span class="sxs-lookup"><span data-stu-id="79b66-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="79b66-754">L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="79b66-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="79b66-755">Per distribuire l'app **UnityDesktopNotifHub** nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="79b66-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="79b66-756">Aprire il file di soluzione dell'app **UnityDesktopNotifHub** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="79b66-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="79b66-757">Nella **piattaforma soluzione**selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="79b66-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="79b66-758">Nella **configurazione della soluzione** selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="79b66-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![Imposta configurazione progetto](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="79b66-760">Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.</span><span class="sxs-lookup"><span data-stu-id="79b66-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="79b66-761">L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="79b66-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="79b66-762">Avviare l'applicazione di realtà mista, seguita dall'applicazione desktop.</span><span class="sxs-lookup"><span data-stu-id="79b66-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="79b66-763">Con entrambe le applicazioni in esecuzione, spostare un oggetto nella scena del desktop (usando il pulsante sinistro del mouse).</span><span class="sxs-lookup"><span data-stu-id="79b66-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="79b66-764">Queste modifiche posizionali verranno apportate localmente, serializzate e inviate al servizio app per le funzioni.</span><span class="sxs-lookup"><span data-stu-id="79b66-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="79b66-765">Il servizio di app per le funzioni aggiornerà quindi la tabella insieme all'hub di notifica.</span><span class="sxs-lookup"><span data-stu-id="79b66-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="79b66-766">Dopo aver ricevuto un aggiornamento, l'hub di notifica invierà i dati aggiornati direttamente a tutte le applicazioni registrate, in questo caso l'app immersiva per le cuffie, che deserializza i dati in arrivo e applica i nuovi dati posizionali agli oggetti locali. spostarli in scena.</span><span class="sxs-lookup"><span data-stu-id="79b66-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="79b66-767">L'applicazione Hub di notifica di Azure è stata completata</span><span class="sxs-lookup"><span data-stu-id="79b66-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="79b66-768">Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio Hub di notifica di Azure e consente la comunicazione tra le app.</span><span class="sxs-lookup"><span data-stu-id="79b66-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![fine prodotto finale](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="79b66-770">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="79b66-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="79b66-771">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="79b66-771">Exercise 1</span></span>

<span data-ttu-id="79b66-772">È possibile capire come modificare il colore di GameObject e inviare la notifica ad altre app che visualizzano la scena?</span><span class="sxs-lookup"><span data-stu-id="79b66-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="79b66-773">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="79b66-773">Exercise 2</span></span>

<span data-ttu-id="79b66-774">È possibile aggiungere lo spostamento di GameObject all'app MR e visualizzare la scena aggiornata nell'app desktop?</span><span class="sxs-lookup"><span data-stu-id="79b66-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
