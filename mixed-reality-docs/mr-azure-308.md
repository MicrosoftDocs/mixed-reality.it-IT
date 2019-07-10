---
title: MR e Azure 308 - notifiche a più dispositivi
description: Completa questo corso per imparare a implementare gli hub di notifica di Azure, funzioni di Azure e archiviazione di Azure e le tabelle all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, la notifica, funzioni, tabelle, hub di notifica, hololens, vr immersivi,
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694608"
---
>[!NOTE]
><span data-ttu-id="fc580-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="fc580-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fc580-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="fc580-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fc580-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="fc580-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fc580-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="fc580-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fc580-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fc580-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fc580-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="fc580-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="fc580-110">MR e Azure 308: Notifiche di più dispositivi</span><span class="sxs-lookup"><span data-stu-id="fc580-110">MR and Azure 308: Cross-device notifications</span></span>

![versione finale del prodotto-avvio](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="fc580-112">In questo corso, si apprenderà come aggiungere funzionalità di hub di notifica a un'applicazione di realtà mista tramite hub di notifica di Azure, tabelle di Azure e funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="fc580-113">**Hub di notifica di Azure** è un servizio Microsoft, che consente agli sviluppatori di inviare notifiche push mirate e personalizzate a qualsiasi piattaforma, tutto con tecnologia nell'ambito del cloud.</span><span class="sxs-lookup"><span data-stu-id="fc580-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="fc580-114">Questo può consentire in modo efficace agli sviluppatori di comunicare con gli utenti finali o anche la comunicazione tra diverse applicazioni, a seconda dello scenario.</span><span class="sxs-lookup"><span data-stu-id="fc580-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="fc580-115">Per altre informazioni, visitare il **hub di notifica** [pagina](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span><span class="sxs-lookup"><span data-stu-id="fc580-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="fc580-116">**Funzioni di Azure** è un servizio Microsoft, che consente agli sviluppatori di eseguire piccole porzioni di codice, 'le funzioni', in Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="fc580-117">Ciò consente di delegare lavoro nel cloud, anziché l'applicazione locale, che può avere molti vantaggi.</span><span class="sxs-lookup"><span data-stu-id="fc580-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="fc580-118">**Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, Node. js, Java e PHP.</span><span class="sxs-lookup"><span data-stu-id="fc580-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="fc580-119">Per altre informazioni, visitare il **funzioni di Azure** [pagina](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="fc580-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="fc580-120">**Le tabelle di Azure** è un servizio cloud Microsoft, che consente agli sviluppatori di archiviare dati strutturati non-SQL nel cloud, per renderla facilmente accessibile ovunque.</span><span class="sxs-lookup"><span data-stu-id="fc580-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="fc580-121">Il servizio vanta una struttura senza schema, che consente l'evoluzione delle tabelle in base alle esigenze e pertanto è molto flessibile.</span><span class="sxs-lookup"><span data-stu-id="fc580-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="fc580-122">Per altre informazioni, visitare il **tabelle di Azure** [pagina](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="fc580-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="fc580-123">Dopo aver completato il corso, si avrà un'applicazione immersive visore VR realtà mista e un'applicazione di PC Desktop, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="fc580-124">L'app a PC Desktop consentirà all'utente di spostare un oggetto nello spazio 2D (X e Y), utilizzando il mouse.</span><span class="sxs-lookup"><span data-stu-id="fc580-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="fc580-125">Lo spostamento di oggetti all'interno dell'app PC verrà inviato al cloud usando JSON, che sarà sotto forma di stringa, contenente un ID di oggetto, tipo e trasforma le informazioni (coordinate X e Y).</span><span class="sxs-lookup"><span data-stu-id="fc580-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="fc580-126">L'app di realtà mista, che dispone di una scena identica all'app desktop, sarà inviate notifiche relative alle spostamento di un oggetto, dal servizio hub di notifica (che è stata appena aggiornato dall'app per PC Desktop).</span><span class="sxs-lookup"><span data-stu-id="fc580-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="fc580-127">Dopo aver ricevuto una notifica, che conterrà l'ID di oggetto, tipo e le informazioni di trasformazione, l'app di realtà mista applicherà le informazioni ricevute per il proprio scena.</span><span class="sxs-lookup"><span data-stu-id="fc580-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="fc580-128">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="fc580-129">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="fc580-130">È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="fc580-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="fc580-131">Questo corso è un'esercitazione completa, che non implicano direttamente eventuali altri laboratori di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="fc580-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="fc580-132">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="fc580-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fc580-133">Corso</span><span class="sxs-lookup"><span data-stu-id="fc580-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fc580-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fc580-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fc580-135"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="fc580-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="fc580-136">MR e Azure 308: Notifiche di più dispositivi</span><span class="sxs-lookup"><span data-stu-id="fc580-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="fc580-137">✔️</span><span class="sxs-lookup"><span data-stu-id="fc580-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fc580-138">✔️</span><span class="sxs-lookup"><span data-stu-id="fc580-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="fc580-139">Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fc580-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="fc580-140">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fc580-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="fc580-141">Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.</span><span class="sxs-lookup"><span data-stu-id="fc580-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fc580-142">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="fc580-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="fc580-143">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="fc580-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="fc580-144">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="fc580-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="fc580-145">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .</span><span class="sxs-lookup"><span data-stu-id="fc580-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="fc580-146">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="fc580-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="fc580-147">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="fc580-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="fc580-148">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="fc580-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fc580-149">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="fc580-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fc580-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="fc580-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="fc580-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fc580-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="fc580-152">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="fc580-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="fc580-153">Accesso a Internet per la configurazione di Azure e di accedere agli hub di notifica</span><span class="sxs-lookup"><span data-stu-id="fc580-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="fc580-154">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="fc580-154">Before you start</span></span>

- <span data-ttu-id="fc580-155">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="fc580-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="fc580-156">È necessario essere il proprietario del portale per sviluppatori Microsoft e il portale di registrazione dell'applicazione, in caso contrario, non si disporrà dell'autorizzazione per accedere all'app nel [capitolo 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="fc580-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="fc580-157">Capitolo 1 - creare un'applicazione nel portale per sviluppatori Microsoft</span><span class="sxs-lookup"><span data-stu-id="fc580-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="fc580-158">Usare la **hub di notifica** servizio, sarà necessario creare un'applicazione nel portale per sviluppatori Microsoft, come l'applicazione dovrà essere registrata, in modo che possa inviare e ricevere le notifiche.</span><span class="sxs-lookup"><span data-stu-id="fc580-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="fc580-159">Accedi per il [portale per sviluppatori Microsoft](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="fc580-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="fc580-160">È necessario accedere al tuo Account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fc580-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="fc580-161">Dal Dashboard, fare clic su **creare una nuova app**.</span><span class="sxs-lookup"><span data-stu-id="fc580-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Creare un'app](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="fc580-163">Verrà visualizzata una finestra popup, in cui è necessario riservare un nome per la nuova app.</span><span class="sxs-lookup"><span data-stu-id="fc580-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="fc580-164">Nella casella di testo, inserire un nome appropriato. Se il nome scelto è disponibile, verrà visualizzato un segno di spunta a destra della casella di testo.</span><span class="sxs-lookup"><span data-stu-id="fc580-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="fc580-165">Dopo aver creato un nome disponibile inserito, scegliere il **riserva nome prodotto** pulsante in basso a sinistra della finestra popup.</span><span class="sxs-lookup"><span data-stu-id="fc580-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![un nome inverso](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="fc580-167">L'App creata a questo punto, sei pronto a passare al capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="fc580-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="fc580-168">Capitolo 2: recuperare le nuove credenziali di App</span><span class="sxs-lookup"><span data-stu-id="fc580-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="fc580-169">Accedere al portale di registrazione dell'applicazione, in cui la nuova app verrà elencato e recuperare le credenziali che verranno usato per il programma di installazione di **servizio hub di notifica** all'interno di **portale di Azure**.</span><span class="sxs-lookup"><span data-stu-id="fc580-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="fc580-170">Passare il [portale di registrazione applicazione](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="fc580-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![portale di registrazione dell'applicazione](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="fc580-172">È necessario usare l'Account Microsoft all'account di accesso.</span><span class="sxs-lookup"><span data-stu-id="fc580-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="fc580-173">Ciò **devono** l'account di Microsoft che è stato utilizzato nella precedente [capitolo](#chapter-1---create-an-application-on-the-microsoft-developer-portal), con il portale per sviluppatori di Windows Store.</span><span class="sxs-lookup"><span data-stu-id="fc580-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="fc580-174">Si noterà l'app con il **mie applicazioni** sezione.</span><span class="sxs-lookup"><span data-stu-id="fc580-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="fc580-175">Una volta che si sia notato, fare clic su di esso e si accederà a una nuova pagina in cui è installata l'app nome seguito da **registrazione**.</span><span class="sxs-lookup"><span data-stu-id="fc580-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![l'app appena registrata](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="fc580-177">Scorrere verso il basso la pagina di registrazione per trovare le **i segreti dell'applicazione** sezione e la **SID pacchetto** per l'app.</span><span class="sxs-lookup"><span data-stu-id="fc580-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="fc580-178">Copiare entrambe per l'utilizzo con configurazione di **servizio di hub di notifica di Azure** nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="fc580-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![Segreti dell'applicazione](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="fc580-180">Capitolo 3 - portale di Azure il programma di installazione: creare il servizio di hub di notifica</span><span class="sxs-lookup"><span data-stu-id="fc580-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="fc580-181">Con le credenziali dell'App recuperato, dovrai accedere al portale di Azure, in cui verrà creato un servizio di hub di notifica di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="fc580-182">Accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="fc580-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="fc580-183">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="fc580-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="fc580-184">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="fc580-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="fc580-185">Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare **Hub di notifica**, fare clic su ***invio***.</span><span class="sxs-lookup"><span data-stu-id="fc580-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![ricerca per hub di notifica](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="fc580-187">La parola ***New*** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="fc580-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="fc580-188">La nuova pagina fornirà una descrizione del *hub di notifica* servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="fc580-189">AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![creare l'istanza di hub di notifica](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="fc580-191">Dopo avere fatto clic su ***Create***:</span><span class="sxs-lookup"><span data-stu-id="fc580-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="fc580-192">Inserire il nome desiderato per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="fc580-193">Fornire una **dello spazio dei nomi** che sarà in grado di associare a questa app.</span><span class="sxs-lookup"><span data-stu-id="fc580-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="fc580-194">Selezionare un **posizione.**</span><span class="sxs-lookup"><span data-stu-id="fc580-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="fc580-195">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="fc580-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="fc580-196">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fc580-197">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="fc580-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="fc580-198">Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="fc580-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="fc580-199">Selezionare un'opzione appropriata **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="fc580-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="fc580-200">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="fc580-201">Selezionare **Create**.</span><span class="sxs-lookup"><span data-stu-id="fc580-201">Select **Create**.</span></span>

        ![Compilandone i dettagli del servizio](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="fc580-203">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="fc580-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="fc580-204">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="fc580-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notifica](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="fc580-206">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="fc580-207">Si verrà indirizzati alla nuova **Hub di notifica** l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Vai alla risorsa](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="fc580-209">Dalla pagina di panoramica, trova a metà della pagina, fare clic su **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="fc580-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="fc580-210">Il pannello sulla destra verrà modificato in campi di testo Mostra due, che richiedono il **SID pacchetto** e **chiave di sicurezza**, dall'app è configurato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="fc580-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![nuovo servizio hub](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="fc580-212">Dopo aver copiato i dettagli nei campi corretti, fare clic su **salvare**, e si riceverà una notifica quando l'Hub di notifica è stata aggiornata.</span><span class="sxs-lookup"><span data-stu-id="fc580-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![copiare i dettagli di sicurezza](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="fc580-214">Capitolo 4 - portale di Azure il programma di installazione: creazione del servizio tabelle</span><span class="sxs-lookup"><span data-stu-id="fc580-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="fc580-215">Dopo aver creato l'istanza del servizio hub di notifica, passare al portale di Azure, in cui verrà creato un servizio di tabelle di Azure tramite la creazione di una risorsa di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="fc580-216">Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="fc580-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="fc580-217">Una volta effettuato l'accesso, fare clic su **New** nell'angolo in alto a sinistra e cercare **account di archiviazione**, fare clic su **invio**.</span><span class="sxs-lookup"><span data-stu-id="fc580-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="fc580-218">La parola ***New*** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="fc580-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="fc580-219">Selezionare **account di archiviazione: blob, file, tabella, coda** dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="fc580-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![eseguire la ricerca di account di archiviazione](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="fc580-221">La nuova pagina fornirà una descrizione del **account di archiviazione** servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="fc580-222">AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="fc580-224">Dopo avere fatto clic su **Create**, verrà visualizzato un pannello:</span><span class="sxs-lookup"><span data-stu-id="fc580-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="fc580-225">Inserire la posizione desiderata **nome** per questa istanza del servizio (deve contenere solo lettere minuscole).</span><span class="sxs-lookup"><span data-stu-id="fc580-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="fc580-226">Per la **modello di distribuzione**, fare clic su **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="fc580-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="fc580-227">Per la **tipologia Account**, usando il menu a discesa, selezionare **archiviazione (utilizzo generico v1)** .</span><span class="sxs-lookup"><span data-stu-id="fc580-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="fc580-228">Selezionare un'opzione appropriata **posizione**.</span><span class="sxs-lookup"><span data-stu-id="fc580-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="fc580-229">Per il **replica** dal menu a discesa, seleziona **Read-access-archiviazione geograficamente ridondante (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="fc580-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="fc580-230">Per la **Performance**, fare clic su **Standard**.</span><span class="sxs-lookup"><span data-stu-id="fc580-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="fc580-231">All'interno di **trasferimento sicuro obbligatorio** sezione, selezionare **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="fc580-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="fc580-232">Dal **sottoscrizione** menu a discesa, selezionare una sottoscrizione appropriata.</span><span class="sxs-lookup"><span data-stu-id="fc580-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="fc580-233">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="fc580-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="fc580-234">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fc580-235">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="fc580-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="fc580-236">Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="fc580-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="fc580-237">Lasciare **reti virtuali** come **disabilitato** se si tratta di un'opzione per l'utente.</span><span class="sxs-lookup"><span data-stu-id="fc580-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="fc580-238">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="fc580-238">Click **Create**.</span></span>

        ![Compilandone i dettagli di archiviazione](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="fc580-240">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="fc580-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="fc580-241">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="fc580-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="fc580-242">Fare clic su notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-242">Click on the notifications to explore your new Service instance.</span></span>

    ![nuova notifica di archiviazione](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="fc580-244">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="fc580-245">Si verrà indirizzati alla nuova pagina di panoramica di istanza del servizio di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Vai alla risorsa](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="fc580-247">Dalla pagina di panoramica, per il lato destro, fare clic su **tabelle**.</span><span class="sxs-lookup"><span data-stu-id="fc580-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="fc580-248">Il pannello sulla destra cambierà e indicherà il **servizio tabelle** informazioni, in cui è necessario aggiungere una nuova tabella.</span><span class="sxs-lookup"><span data-stu-id="fc580-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="fc580-249">Eseguire questa operazione facendo il **+** **tabella** pulsante nell'angolo superiore sinistro.</span><span class="sxs-lookup"><span data-stu-id="fc580-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![Aprire le tabelle](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="fc580-251">Verrà visualizzata una nuova pagina, in cui è necessario immettere un **nome della tabella**.</span><span class="sxs-lookup"><span data-stu-id="fc580-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="fc580-252">Questo è il nome che verrà utilizzato per fare riferimento ai dati nell'applicazione nei capitoli successivi.</span><span class="sxs-lookup"><span data-stu-id="fc580-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="fc580-253">Inserire un nome appropriato e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc580-253">Insert an appropriate name and click **OK**.</span></span>

    ![Creare una nuova tabella](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="fc580-255">Dopo aver creata la nuova tabella, sarà possibile visualizzarlo all'interno di **servizio tabelle** (inferiore) della pagina.</span><span class="sxs-lookup"><span data-stu-id="fc580-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![nuova tabella creata](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="fc580-257">Capitolo 5: completare la tabella di Azure in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc580-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="fc580-258">Ora che il **servizio tabelle** account di archiviazione è stata configurata, è possibile aggiungere dati a esso, che verrà usato per archiviare e recuperare informazioni.</span><span class="sxs-lookup"><span data-stu-id="fc580-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="fc580-259">La modifica delle tabelle può essere eseguita tramite **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="fc580-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="fc580-260">Aprire **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="fc580-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="fc580-261">Dal menu, fare clic su **View** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="fc580-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Aprire cloud explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="fc580-263">Il **Cloud Explorer** verranno aperte come un elemento ancoraggio (essere paziente, come il caricamento potrebbe richiedere tempo).</span><span class="sxs-lookup"><span data-stu-id="fc580-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="fc580-264">Se la sottoscrizione è stata usata per creare le *gli account di archiviazione* non è visibile, assicurarsi di avere:</span><span class="sxs-lookup"><span data-stu-id="fc580-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="fc580-265">Per lo stesso account come quello usato per il portale di Azure connesso.</span><span class="sxs-lookup"><span data-stu-id="fc580-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="fc580-266">Selezionare la sottoscrizione dalla pagina di gestione di Account (potrebbe essere necessario applicare un filtro da impostazioni dell'account):</span><span class="sxs-lookup"><span data-stu-id="fc580-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![trovare la sottoscrizione](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="fc580-268">Verranno visualizzati i servizi cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="fc580-269">Trovare **gli account di archiviazione** e fare clic sulla freccia a sinistra di tale per espandere l'account.</span><span class="sxs-lookup"><span data-stu-id="fc580-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Aprire l'account di archiviazione](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="fc580-271">Una volta espanso, appena creato **account di archiviazione** devono essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="fc580-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="fc580-272">Fare clic sulla freccia a sinistra della risorsa di archiviazione e quindi una volta che viene espanso, individuare **tabelle** e fare clic sulla freccia accanto a cui, per visualizzare i **tabella** creato nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="fc580-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="fc580-273">Fare doppio clic il **tabella**.</span><span class="sxs-lookup"><span data-stu-id="fc580-273">Double click your **Table**.</span></span>

    ![Aprire la tabella oggetti di scena](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="fc580-275">La tabella verrà aperta al centro della finestra di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc580-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="fc580-276">Fare clic sull'icona di tabella con il **+** (più) su di esso.</span><span class="sxs-lookup"><span data-stu-id="fc580-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![Aggiungi nuova tabella](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="fc580-278">Verrà visualizzata richiede una finestra per poter *Aggiungi entità*.</span><span class="sxs-lookup"><span data-stu-id="fc580-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="fc580-279">Si creerà tre entità in totale, ciascuno con diverse proprietà.</span><span class="sxs-lookup"><span data-stu-id="fc580-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="fc580-280">Si noterà che *PartitionKey* e *RowKey* già disponibili, poiché verranno usati per trovare i dati dalla tabella.</span><span class="sxs-lookup"><span data-stu-id="fc580-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![chiave di partizione e di riga](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="fc580-282">Aggiornamento di *valore* del **PartitionKey** e **RowKey** come indicato di seguito (ricordarsi di eseguire questa operazione per ogni proprietà di riga si aggiungono, tuttavia incrementare ogni volta che l'elemento RowKey):</span><span class="sxs-lookup"><span data-stu-id="fc580-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![aggiungere i valori corretti](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="fc580-284">Fare clic su **aggiungere proprietà** per aggiungere ulteriori righe di dati.</span><span class="sxs-lookup"><span data-stu-id="fc580-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="fc580-285">Creare la prima tabella vuota corrisponde la tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="fc580-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="fc580-286">Fare clic su **OK** al termine.</span><span class="sxs-lookup"><span data-stu-id="fc580-286">Click **OK** when you are finished.</span></span>

    ![Fare clic su ok al termine](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="fc580-288">Assicurarsi di aver modificato il **tipo** delle **X**, **Y**, e **Z**, le voci per **Double**.</span><span class="sxs-lookup"><span data-stu-id="fc580-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="fc580-289">Si noterà che la tabella ora presenta una riga di dati.</span><span class="sxs-lookup"><span data-stu-id="fc580-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="fc580-290">Scegliere il **+** (icona Nuovo per aggiungere un'altra entità più).</span><span class="sxs-lookup"><span data-stu-id="fc580-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![prima riga](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="fc580-292">Creare una proprietà aggiuntiva e quindi impostare i valori della nuova entità in modo che corrispondano a quelle riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="fc580-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![aggiungere cubo](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="fc580-294">Ripetere l'ultimo passaggio per aggiungere un'altra entità.</span><span class="sxs-lookup"><span data-stu-id="fc580-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="fc580-295">Impostare i valori per questa entità su quelle riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="fc580-295">Set the values for this entity to those shown below.</span></span>

    ![aggiungere cilindro](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="fc580-297">La tabella dovrebbe ora essere simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="fc580-297">Your table should now look like the one below.</span></span>

    ![tabella completa](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="fc580-299">È stata completata in questo capitolo.</span><span class="sxs-lookup"><span data-stu-id="fc580-299">You have completed this Chapter.</span></span> <span data-ttu-id="fc580-300">Assicurarsi di salvare.</span><span class="sxs-lookup"><span data-stu-id="fc580-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="fc580-301">Capitolo 6: creare un'App per le funzioni di Azure</span><span class="sxs-lookup"><span data-stu-id="fc580-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="fc580-302">Creare un'App di funzione di Azure, che verrà chiamato dall'applicazione Desktop per aggiornare il **tabella** del servizio e invia una notifica tramite il **Hub di notifica**.</span><span class="sxs-lookup"><span data-stu-id="fc580-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="fc580-303">In primo luogo, è necessario creare un file che consentirà la funzione di Azure caricare le librerie che necessarie.</span><span class="sxs-lookup"><span data-stu-id="fc580-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="fc580-304">Aprire **Notepad** (premere tasto Windows e digitare notepad).</span><span class="sxs-lookup"><span data-stu-id="fc580-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![Aprire Blocco note](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="fc580-306">Aprire Blocco note, inserire la struttura JSON seguente al suo interno.</span><span class="sxs-lookup"><span data-stu-id="fc580-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="fc580-307">Una volta che è stato fatto che, salvarlo sul desktop come **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="fc580-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="fc580-308">È importante che il nome sia corretto: assicurarsi che avviene **non è un file con estensione txt** estensione di file.</span><span class="sxs-lookup"><span data-stu-id="fc580-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="fc580-309">Questo file definisce le librerie che userà la funzione, se si usa NuGet avrà un aspetto familiare.</span><span class="sxs-lookup"><span data-stu-id="fc580-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

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

3.  <span data-ttu-id="fc580-310">Accedi per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="fc580-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="fc580-311">Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare **App per le funzioni**, premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="fc580-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![cercare app per le funzioni](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="fc580-313">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="fc580-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="fc580-314">La nuova pagina fornirà una descrizione del **App per le funzioni** servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="fc580-315">AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![istanza dell'app (funzione)](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="fc580-317">Dopo avere fatto clic su **Create**, compilare i campi seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="fc580-318">Per la **nome App**, inserire il nome desiderato per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="fc580-319">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="fc580-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="fc580-320">Selezionare il piano tariffario appropriato per l'utente, se questa è la prima volta che la creazione di un **servizio App di funzione**, un livello gratuito deve essere disponibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="fc580-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="fc580-321">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="fc580-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="fc580-322">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="fc580-323">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="fc580-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="fc580-324">Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="fc580-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="fc580-325">Per la **OS**, fare clic su Windows, che è la piattaforma desiderata.</span><span class="sxs-lookup"><span data-stu-id="fc580-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="fc580-326">Selezionare una **piano di Hosting** (questa esercitazione Usa un **piano a consumo**.</span><span class="sxs-lookup"><span data-stu-id="fc580-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="fc580-327">Selezionare una **ubicazione** **(scegliere la stessa ubicazione come risorsa di archiviazione che hanno creato nel passaggio precedente)**</span><span class="sxs-lookup"><span data-stu-id="fc580-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="fc580-328">Per il **memorizzazione** sezione **è necessario selezionare il servizio di archiviazione creato nel passaggio precedente**.</span><span class="sxs-lookup"><span data-stu-id="fc580-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="fc580-329">Non è necessario *Application Insights* in questa app, è possibile lasciarlo **Off**.</span><span class="sxs-lookup"><span data-stu-id="fc580-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="fc580-330">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="fc580-330">Click **Create**.</span></span>

        ![creare una nuova istanza](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="fc580-332">Dopo avere fatto clic su **Create** si dovrà attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="fc580-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="fc580-333">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="fc580-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nuova notifica](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="fc580-335">Fare clic su notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="fc580-336">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="fc580-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Vai alla risorsa](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="fc580-338">Scegliere il **+** (più) icona accanto a *funzioni*, a *Crea nuovo*.</span><span class="sxs-lookup"><span data-stu-id="fc580-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Aggiungi nuova funzione](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="fc580-340">All'interno del pannello centrale, il **funzione** verrà visualizzata la finestra di creazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="fc580-341">Ignorare le informazioni nella parte superiore del pannello e fare clic su **funzione personalizzata**, che si trova nella parte inferiore (nell'area blu, come indicato di seguito).</span><span class="sxs-lookup"><span data-stu-id="fc580-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="fc580-343">Nella pagina nuovo all'interno della finestra verranno visualizzati diversi tipi di funzione.</span><span class="sxs-lookup"><span data-stu-id="fc580-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="fc580-344">Scorrere verso il basso per visualizzare i tipi di colore viola e fare clic su **PUT HTTP** elemento.</span><span class="sxs-lookup"><span data-stu-id="fc580-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![collegamento put http](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="fc580-346">Potrebbe essere necessario scorrere ulteriormente verso la freccia giù della pagina e questa immagine potrebbe non esattamente lo stesso aspetto, se siano stati eseguiti aggiornamenti del portale di Azure, tuttavia, si sta cercando un elemento denominato *PUT HTTP*.</span><span class="sxs-lookup"><span data-stu-id="fc580-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="fc580-347">Il **PUT HTTP** verrà visualizzata la finestra in cui è necessario configurare la funzione (vedere di seguito per l'immagine).</span><span class="sxs-lookup"><span data-stu-id="fc580-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="fc580-348">Per la **linguaggio** utilizzando il menu a discesa, selezionare C\#.</span><span class="sxs-lookup"><span data-stu-id="fc580-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="fc580-349">Per la **nome,** immettere un nome appropriato.</span><span class="sxs-lookup"><span data-stu-id="fc580-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="fc580-350">Nel **a livello di autenticazione** dal menu a discesa, seleziona **funzione**.</span><span class="sxs-lookup"><span data-stu-id="fc580-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="fc580-351">Per il **nome della tabella** sezione, è necessario usare il nome esatto usato per creare le **tabella** servizio precedentemente (tra cui le stesse maiuscole/minuscole).</span><span class="sxs-lookup"><span data-stu-id="fc580-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="fc580-352">All'interno di **connessione dell'account di archiviazione** sezione, usare il menu a discesa e selezionare l'account di archiviazione da tale posizione.</span><span class="sxs-lookup"><span data-stu-id="fc580-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="fc580-353">Se non è presente, fare clic il **New** hyperlink insieme il titolo di sezione, per visualizzare un altro pannello, in cui dovrebbe essere elencato nell'account di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![nuova risorsa di archiviazione](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="fc580-355">Fare clic su **Create** e si riceverà una notifica che le impostazioni sono state aggiornate correttamente.</span><span class="sxs-lookup"><span data-stu-id="fc580-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![creare (funzione)](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="fc580-357">Dopo aver fatto clic **Create**, si verrà reindirizzati all'editor di funzione.</span><span class="sxs-lookup"><span data-stu-id="fc580-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![aggiornare il codice di funzione](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="fc580-359">Inserire il codice seguente nell'editor di funzione (sostituendo il codice nella funzione di):</span><span class="sxs-lookup"><span data-stu-id="fc580-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

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
    > <span data-ttu-id="fc580-360">Usando le librerie incluse, la funzione riceve il nome e il percorso dell'oggetto che è stato spostato nella scena Unity (come un C# oggetto, definito **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="fc580-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="fc580-361">Questo oggetto viene quindi usato per aggiornare i parametri dell'oggetto all'interno della tabella creata.</span><span class="sxs-lookup"><span data-stu-id="fc580-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="fc580-362">In seguito, la funzione effettua una chiamata al servizio Hub di notifica creato, che notifica alle applicazioni tutti sottoscritte.</span><span class="sxs-lookup"><span data-stu-id="fc580-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="fc580-363">Con il codice, fare clic su **salvare**.</span><span class="sxs-lookup"><span data-stu-id="fc580-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="fc580-364">Successivamente, fare clic il **\<** icona (freccia), sul lato destro della pagina.</span><span class="sxs-lookup"><span data-stu-id="fc580-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Pannello Apri caricamento](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="fc580-366">Un pannello verrà diapositiva da destra.</span><span class="sxs-lookup"><span data-stu-id="fc580-366">A panel will slide in from the right.</span></span> <span data-ttu-id="fc580-367">In questo pannello, fare clic su **caricare**, e verrà visualizzato un Browser di File.</span><span class="sxs-lookup"><span data-stu-id="fc580-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="fc580-368">Passare a e quindi, il **Project. JSON** file, che è stato creato in **blocco note** in precedenza e quindi fare clic sui **Open** pulsante.</span><span class="sxs-lookup"><span data-stu-id="fc580-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="fc580-369">Questo file definisce le librerie che userà la funzione.</span><span class="sxs-lookup"><span data-stu-id="fc580-369">This file defines the libraries that your function will use.</span></span>

    ![Carica json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="fc580-371">Quando il file è stato caricato, verrà visualizzato nel pannello a destra.</span><span class="sxs-lookup"><span data-stu-id="fc580-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="fc580-372">Clic su di esso verrà aperta all'interno di **funzione** editor.</span><span class="sxs-lookup"><span data-stu-id="fc580-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="fc580-373">È necessario ottenere **esattamente** quello utilizzato per l'immagine successiva (in basso passaggio 23).</span><span class="sxs-lookup"><span data-stu-id="fc580-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="fc580-374">Quindi, nel pannello a sinistra, sotto **funzioni**, fare clic sui **integra** collegamento.</span><span class="sxs-lookup"><span data-stu-id="fc580-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![integrare (funzione)](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="fc580-376">Nella pagina successiva, nell'angolo superiore destro, fare clic su **editor avanzato** (come indicato di seguito).</span><span class="sxs-lookup"><span data-stu-id="fc580-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![editor avanzato aperto](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="fc580-378">Oggetto **Function. JSON** file verrà aperto nel Pannello di center, che deve essere sostituito con il frammento di codice seguente.</span><span class="sxs-lookup"><span data-stu-id="fc580-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="fc580-379">Questa impostazione definisce la funzione crei e i parametri passati alla funzione.</span><span class="sxs-lookup"><span data-stu-id="fc580-379">This defines the function you are building and the parameters passed into the function.</span></span>

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

26. <span data-ttu-id="fc580-380">L'editor dovrebbe ora essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="fc580-380">Your editor should now look like the image below:</span></span>

    ![tornare all'editor standard](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="fc580-382">È possibile riscontrare i parametri di input che è stato inserito potrebbero non corrispondere i dettagli della tabella e archiviazione e pertanto dovrà essere aggiornata con le informazioni.</span><span class="sxs-lookup"><span data-stu-id="fc580-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="fc580-383">**Non eseguire questa operazione qui**, perché è coperto successivamente.</span><span class="sxs-lookup"><span data-stu-id="fc580-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="fc580-384">È sufficiente fare clic il **editor Standard** collegamento, nell'angolo superiore destro della pagina, tornare indietro.</span><span class="sxs-lookup"><span data-stu-id="fc580-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="fc580-385">Nel **editor Standard**, fare clic su **archiviazione tabelle di Azure (tabella)** , sotto **input**.</span><span class="sxs-lookup"><span data-stu-id="fc580-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Input di tabelle](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="fc580-387">Verificare che la corrispondenza seguente per **il** informazioni, queste potrebbero essere diversi (è disponibile un'immagine di seguito i passaggi seguenti):</span><span class="sxs-lookup"><span data-stu-id="fc580-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="fc580-388">**Nome della tabella**: il nome della tabella creata all'interno di archiviazione di Azure, servizio tabelle.</span><span class="sxs-lookup"><span data-stu-id="fc580-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="fc580-389">**Connessione dell'account di archiviazione:** fare clic su **nuovi**, che viene visualizzata accanto nel menu a discesa e verrà visualizzato un pannello a destra della finestra.</span><span class="sxs-lookup"><span data-stu-id="fc580-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![nuova risorsa di archiviazione](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="fc580-391">Selezionare i **Account di archiviazione**, creato in precedenza per ospitare il **App per le funzioni.**</span><span class="sxs-lookup"><span data-stu-id="fc580-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="fc580-392">Si noterà che il **Account di archiviazione** valore di connessione è stato creato.</span><span class="sxs-lookup"><span data-stu-id="fc580-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="fc580-393">Assicurarsi di premere **salvare** dopo aver terminato.</span><span class="sxs-lookup"><span data-stu-id="fc580-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="fc580-394">Il **input** pagina dovrebbe ora corrispondere il seguente, che mostra **il** informazioni.</span><span class="sxs-lookup"><span data-stu-id="fc580-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![input completo](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="fc580-396">Fare quindi clic **Hub di notifica di Azure (notifica)** : in **output**.</span><span class="sxs-lookup"><span data-stu-id="fc580-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="fc580-397">Assicurarsi che corrispondono a quanto segue **il** informazioni, queste potrebbero essere diversi (è disponibile un'immagine di seguito la procedura seguente):</span><span class="sxs-lookup"><span data-stu-id="fc580-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="fc580-398">**Nome Hub di notifica**: si tratta del nome delle **dell'Hub di notifica** istanza del servizio creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="fc580-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="fc580-399">**Connessione dello spazio dei nomi hub di notifica**: fare clic su **nuovi**, che viene visualizzata accanto nel menu a discesa.</span><span class="sxs-lookup"><span data-stu-id="fc580-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![controllare gli output](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="fc580-401">Il **Connection** popup verrà visualizzati (vedere la figura seguente), in cui è necessario selezionare la **Namespace** del **Hub di notifica**, che devono essere impostate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="fc580-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="fc580-402">Selezionare i **Hub di notifica** nome dal menu a discesa intermedio.</span><span class="sxs-lookup"><span data-stu-id="fc580-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="fc580-403">Impostare il **criterio** dal menu a discesa per **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="fc580-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="fc580-404">Scegliere il **seleziona** pulsante per tornare indietro.</span><span class="sxs-lookup"><span data-stu-id="fc580-404">Click the **Select** button to go back.</span></span>

        ![aggiornamento di output](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="fc580-406">Il **output** pagina dovrebbe ora corrispondere il più avanti, ma con **il** informazioni invece.</span><span class="sxs-lookup"><span data-stu-id="fc580-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="fc580-407">Assicurarsi di premere **salvare**.</span><span class="sxs-lookup"><span data-stu-id="fc580-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="fc580-408">*Non modificare direttamente il nome dell'Hub di notifica* (tutti eseguire questa operazione usando il **Editor avanzato**, a condizione che è stata seguita la procedura precedente in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="fc580-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![output completo](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="fc580-410">A questo punto, è consigliabile testare la funzione, per assicurarsi che del corretto funzionamento.</span><span class="sxs-lookup"><span data-stu-id="fc580-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="fc580-411">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="fc580-411">To do this:</span></span> 

    1. <span data-ttu-id="fc580-412">Passare alla pagina di funzione ancora una volta:</span><span class="sxs-lookup"><span data-stu-id="fc580-412">Navigate to the function page once more:</span></span>

        ![output completo](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="fc580-414">Tornare alla pagina di funzione e fare clic sui **Test** scheda all'estrema destra di destra della pagina, aprire il *Test* pannello:</span><span class="sxs-lookup"><span data-stu-id="fc580-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![output completo](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="fc580-416">All'interno di **corpo della richiesta** nella casella di testo del pannello, incollare il codice riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="fc580-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

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

    4. <span data-ttu-id="fc580-417">Con il test di codice, scegliere il **eseguire** pulsante in basso a destra e il test verrà eseguito.</span><span class="sxs-lookup"><span data-stu-id="fc580-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="fc580-418">I log di output del test saranno visualizzati nell'area di console, sotto il codice della funzione.</span><span class="sxs-lookup"><span data-stu-id="fc580-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![output completo](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="fc580-420">Se il test precedente non riesce, è necessario per controllare di aver seguito i passaggi precedenti esattamente, in particolare le impostazioni all'interno di **integrare pannello**.</span><span class="sxs-lookup"><span data-stu-id="fc580-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="fc580-421">Capitolo 7 - configurazione di progetto Desktop di Unity</span><span class="sxs-lookup"><span data-stu-id="fc580-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fc580-422">L'applicazione Desktop che si sta ora creando, **non** funzionano nell'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="fc580-423">Deve essere eseguito all'esterno dell'Editor, dopo la compilazione dell'applicazione, usando Visual Studio (o l'applicazione distribuita).</span><span class="sxs-lookup"><span data-stu-id="fc580-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="fc580-424">Di seguito è una tipica configurato per lo sviluppo con Unity e realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="fc580-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="fc580-425">Configurare e testare il visore VR immersivi di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="fc580-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="fc580-426">Verrà **non** richiedono controller di movimento a questo corso.</span><span class="sxs-lookup"><span data-stu-id="fc580-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="fc580-427">Se è necessario il supporto di configurazione di visore VR immersivi, seguire questa [collegamento su come impostare la realtà mista di Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="fc580-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="fc580-428">Aprire **Unity** e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="fc580-428">Open **Unity** and click **New**.</span></span>

    ![nuovo progetto unity](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="fc580-430">È necessario specificare un nome di progetto Unity, inserire **UnityDesktopNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="fc580-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="fc580-431">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="fc580-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="fc580-432">Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="fc580-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="fc580-433">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="fc580-433">Then, click **Create project**.</span></span>

    ![Crea progetto](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="fc580-435">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="fc580-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="fc580-436">Passare a **Edit** > **preferenze** e quindi dalla nuova finestra, passare al **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="fc580-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="fc580-437">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="fc580-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="fc580-438">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="fc580-438">Close the **Preferences** window.</span></span>

    ![set di strumenti di Visual Studio esterni](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="fc580-440">Passare quindi ad **File** > **Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic su di **commutatore piattaforma**pulsante per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="fc580-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![passare a piattaforme](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="fc580-442">Mentre si trovano ancora nella **File** > **Build Settings**, assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="fc580-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="fc580-443">**Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="fc580-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="fc580-444">Questa applicazione sarà per il desktop, pertanto deve essere **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="fc580-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="fc580-445">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="fc580-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="fc580-446">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="fc580-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="fc580-447">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="fc580-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="fc580-448">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="fc580-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="fc580-449">A questo punto, vale la pena di salvataggio della scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="fc580-450">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="fc580-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="fc580-451">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="fc580-451">A save window will appear.</span></span>

            ![aggiungere scene open](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="fc580-453">Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="fc580-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nuova cartella scene](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="fc580-455">Aprire appena creato **scene** cartella e quindi il **nome File:** campo di testo, digitare **hub di notifica\_Desktop\_scena**, quindi premere **Salvare**.</span><span class="sxs-lookup"><span data-stu-id="fc580-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![new NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="fc580-457">Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="fc580-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="fc580-458">Nella stessa finestra fare clic sui **le impostazioni del giocatore** pulsante, si aprirà il pannello correlato nello spazio in cui le **Inspector** si trova.</span><span class="sxs-lookup"><span data-stu-id="fc580-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="fc580-459">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="fc580-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="fc580-460">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="fc580-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="fc580-461">**Versione del Runtime di scripting** deve essere **sperimentale (equivalente con .NET 4.6)**</span><span class="sxs-lookup"><span data-stu-id="fc580-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="fc580-462">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="fc580-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="fc580-463">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="fc580-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![versione di .NET 4.6](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="fc580-465">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="fc580-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="fc580-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="fc580-466">**InternetClient**</span></span>

            ![client internet di segni di graduazione](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="fc580-468">Nuovamente in **Build Settings** *Unity C\# progetti* non è non è più in grigio, selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="fc580-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="fc580-469">Chiudi il **Build Settings** finestra.</span><span class="sxs-lookup"><span data-stu-id="fc580-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="fc580-470">Salvare il progetto e la scena **File** > **Salva scena /file** > **Salva progetto**.</span><span class="sxs-lookup"><span data-stu-id="fc580-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fc580-471">Se si vuole ignorare la *configurare Unity* componente per il progetto (App Desktop) e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importarlo nel progetto come un [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="fc580-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="fc580-472">È comunque necessario aggiungere i componenti di script.</span><span class="sxs-lookup"><span data-stu-id="fc580-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="fc580-473">Capitolo 8 - importazione di DLL in Unity</span><span class="sxs-lookup"><span data-stu-id="fc580-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="fc580-474">Si userà archiviazione di Azure per Unity (che a sua volta si basa su .net SDK per Azure).</span><span class="sxs-lookup"><span data-stu-id="fc580-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="fc580-475">Per altre informazioni, seguire questo [collegamento su archiviazione di Azure per Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="fc580-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="fc580-476">È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="fc580-477">Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.</span><span class="sxs-lookup"><span data-stu-id="fc580-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="fc580-478">Per importare il SDK in un progetto, assicurarsi di aver scaricato la versione più recente [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) da GitHub.</span><span class="sxs-lookup"><span data-stu-id="fc580-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="fc580-479">Quindi, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-479">Then, do the following:</span></span>

1.  <span data-ttu-id="fc580-480">Aggiungere il **.unitypackage** a Unity tramite il **asset \> Importa pacchetto \> pacchetto personalizzato** l'opzione di menu.</span><span class="sxs-lookup"><span data-stu-id="fc580-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="fc580-481">Nel **Importa pacchetto Unity** casella visualizzata, è possibile selezionare tutti gli elementi in \* \**plug-in* \> \* archiviazione \* \* \*.</span><span class="sxs-lookup"><span data-stu-id="fc580-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="fc580-482">Deseleziona tutto il resto, perché non è necessaria per questo corso.</span><span class="sxs-lookup"><span data-stu-id="fc580-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Importa pacchetto](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="fc580-484">Scegliere il ***importazione*** pulsante per aggiungere elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="fc580-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="fc580-485">Andare alla **Storage** cartella sotto **plug-in** nel progetto consente di visualizzare e selezionare il plug-in seguenti *solo*:</span><span class="sxs-lookup"><span data-stu-id="fc580-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="fc580-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="fc580-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="fc580-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="fc580-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="fc580-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="fc580-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="fc580-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="fc580-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="fc580-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="fc580-490">System.Spatial</span></span>

![Deselezionare qualsiasi piattaforma](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="fc580-492">Con *questi plug-in specifici* è selezionata, **deselezionare** **Any Platform** e **deselezionare** **WSAPlayer** quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="fc580-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![applicare le DLL di piattaforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="fc580-494">Vengono contrassegnati questi plug-in particolare per essere usato solo nell'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="fc580-495">Questo avviene perché sono presenti versioni diverse dello stesso plug-nella cartella WSA che verrà utilizzata dopo che il progetto viene esportato da Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="fc580-496">Nel **archiviazione** cartella plug-in, selezionare solo:</span><span class="sxs-lookup"><span data-stu-id="fc580-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="fc580-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="fc580-497">Microsoft.Data.Services.Client</span></span>

        ![non elabora set di DLL](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="fc580-499">Verificare i **processo non** nella casella **impostazioni piattaforma** e fare clic su ***Apply***.</span><span class="sxs-lookup"><span data-stu-id="fc580-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="fc580-501">Vengono contrassegnati questo plug-in "Non elabora", perché il patcher assembly di Unity ha difficoltà a questo plug-in di elaborazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="fc580-502">Il plug-in continuerà a funzionare anche se non è stato elaborato.</span><span class="sxs-lookup"><span data-stu-id="fc580-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="fc580-503">Capitolo 9 - creare la classe TableToScene nel progetto Unity Desktop</span><span class="sxs-lookup"><span data-stu-id="fc580-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="fc580-504">È ora necessario creare gli script che contiene il codice per eseguire questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="fc580-505">È il primo script da creare **TableToScene**, che è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="fc580-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="fc580-506">La lettura delle entità all'interno della tabella di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="fc580-507">Usando i dati della tabella, determinare gli oggetti da generare e in quale posizione.</span><span class="sxs-lookup"><span data-stu-id="fc580-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="fc580-508">È il secondo script è necessario creare **CloudScene**, che è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="fc580-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="fc580-509">Registrazione dell'evento, quindi fare clic su per consentire all'utente di trascinare gli oggetti per la scena.</span><span class="sxs-lookup"><span data-stu-id="fc580-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="fc580-510">Serializzare i dati dell'oggetto da questa scena Unity e inviarlo all'App per le funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="fc580-511">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="fc580-511">To create this class:</span></span>

1.  <span data-ttu-id="fc580-512">Fare doppio clic nella **bene** cartella si trova nel pannello dei progetti **Create** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="fc580-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="fc580-513">Denominare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="fc580-513">Name the folder **Scripts**.</span></span>

    ![Crea cartella scripts](images/AzureLabs-Lab8-66.png)

    ![creare la cartella degli script 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="fc580-516">Fare doppio clic sulla cartella appena creata, per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="fc580-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="fc580-517">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="fc580-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="fc580-518">Denominare lo script **TableToScene**.</span><span class="sxs-lookup"><span data-stu-id="fc580-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="fc580-519">![nuovo script c#](images/AzureLabs-Lab8-68.png)
    ![TableToScene ridenominazione](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="fc580-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="fc580-520">Fare doppio clic sullo script per aprirlo in Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fc580-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="fc580-521">Aggiungere spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="fc580-522">All'interno della classe, inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-522">Within the class, insert the following variables:</span></span>

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
    > <span data-ttu-id="fc580-523">Sostituire il **NomeAccount** valore con il nome del servizio di archiviazione di Azure e **accountKey** valore con il valore della chiave trovato nel servizio di archiviazione di Azure, nel portale di Azure (vedere immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="fc580-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![chiave dell'account di recupero](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="fc580-525">A questo punto aggiungere il **Start ()** e **Awake()** metodi per inizializzare la classe.</span><span class="sxs-lookup"><span data-stu-id="fc580-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

8.  <span data-ttu-id="fc580-526">All'interno di **TableToScene** classe, aggiungere il metodo che recupererà i valori della tabella di Azure e usarle per generare le primitive appropriate nella scena.</span><span class="sxs-lookup"><span data-stu-id="fc580-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

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

9.  <span data-ttu-id="fc580-527">Di fuori di **TableToScene** (classe), è necessario definire la classe utilizzata dall'applicazione per serializzare e deserializzare le **entità tabella**.</span><span class="sxs-lookup"><span data-stu-id="fc580-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

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

10. <span data-ttu-id="fc580-528">Assicurarsi di aver **salvare** prima di tornare all'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="fc580-529">Fare clic sui **Main Camera** dalle **gerarchia** pannello, in modo che le proprietà visualizzate nella **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="fc580-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="fc580-530">Con il **gli script** cartella aperta, selezionare lo script **file TableToScene** e trascinarla nel **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="fc580-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="fc580-531">Il risultato dovrebbe essere come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="fc580-531">The result should be as below:</span></span>

    ![aggiungere script alla fotocamera principale](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="fc580-533">Capitolo 10 - creare la classe CloudScene nel progetto Unity Desktop</span><span class="sxs-lookup"><span data-stu-id="fc580-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="fc580-534">È il secondo script è necessario creare **CloudScene**, che è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="fc580-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="fc580-535">Registrazione dell'evento, quindi fare clic su per consentire all'utente di trascinare gli oggetti per la scena.</span><span class="sxs-lookup"><span data-stu-id="fc580-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="fc580-536">Serializzare i dati dell'oggetto da questa scena Unity e inviarlo all'App per le funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="fc580-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="fc580-537">Per creare il secondo script:</span><span class="sxs-lookup"><span data-stu-id="fc580-537">To create the second script:</span></span>

1.  <span data-ttu-id="fc580-538">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**, **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="fc580-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="fc580-539">Denominare lo script **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="fc580-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="fc580-540">![nuovo script c#](images/AzureLabs-Lab8-72.png)
    ![rinominare CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="fc580-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="fc580-541">Aggiungere spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="fc580-542">Inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-542">Insert the following variables:</span></span>

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

4.  <span data-ttu-id="fc580-543">Sostituire il **azureFunctionEndpoint** valore con l'URL dell'App funzione Azure trovare la funzione di servizio App di Azure, nel portale di Azure, come illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="fc580-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![Recupera URL della funzione](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="fc580-545">A questo punto aggiungere il **Start ()** e **Awake()** metodi per inizializzare la classe.</span><span class="sxs-lookup"><span data-stu-id="fc580-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

6.  <span data-ttu-id="fc580-546">All'interno di **Update ()** metodo, aggiungere il codice seguente che rileva l'input del mouse e trascinare, che a sua volta sposterà Gameobject nella scena.</span><span class="sxs-lookup"><span data-stu-id="fc580-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="fc580-547">Se l'utente ha trascinato e rilasciato un oggetto, passerà il nome e le coordinate dell'oggetto al metodo **UpdateCloudScene()** , che chiamerà il servizio App di funzioni di Azure, che aggiornerà le tabelle di Azure e i trigger di notifica.</span><span class="sxs-lookup"><span data-stu-id="fc580-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

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

7.  <span data-ttu-id="fc580-548">A questo punto aggiungere il **UpdateCloudScene()** (metodo), come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="fc580-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

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

8.  <span data-ttu-id="fc580-549">Salvare il codice e tornare a Unity</span><span class="sxs-lookup"><span data-stu-id="fc580-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="fc580-550">Trascinare il **CloudScene** nello script le **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="fc580-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="fc580-551">Fare clic sui **Main Camera** dalle **gerarchia** pannello, in modo che le proprietà visualizzate nella **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="fc580-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="fc580-552">Con il **gli script** aperto, selezionare cartella la **CloudScene** script e trascinarla nel **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="fc580-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="fc580-553">Il risultato dovrebbe essere come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="fc580-553">The result should be as below:</span></span>

        > ![Trascinare uno script cloud fotocamera principale](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="fc580-555">Capitolo 11 - compilare il progetto per Desktop alla piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="fc580-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="fc580-556">Tutti gli elementi necessari per la sezione di Unity di questo progetto a questo punto è stato completato.</span><span class="sxs-lookup"><span data-stu-id="fc580-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="fc580-557">Passare a **impostazioni di compilazione** (**File** > **impostazioni di compilazione**).</span><span class="sxs-lookup"><span data-stu-id="fc580-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="fc580-558">Dal **Build Settings** finestra, fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="fc580-558">From the **Build Settings** window, click **Build**.</span></span>

    ![Compila progetto](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="fc580-560">Oggetto **Esplora File** popup verrà finestra, di cui è possibile specificare un percorso di compilazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="fc580-561">Creare una nuova cartella (facendo **nuova cartella** nell'angolo superiore sinistro) e denominarla **COMPILA**.</span><span class="sxs-lookup"><span data-stu-id="fc580-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![nuova cartella per la compilazione](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="fc580-563">Aprire il nuovo **si basa** cartella e creare un'altra cartella (utilizzando **nuova cartella** ancora una volta) e denominarlo **hub di notifica\_Desktop\_App**.</span><span class="sxs-lookup"><span data-stu-id="fc580-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![folder name NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="fc580-565">Con il **hub di notifica\_Desktop\_App** selezionato.</span><span class="sxs-lookup"><span data-stu-id="fc580-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="fc580-566">Fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="fc580-566">click **Select Folder**.</span></span> <span data-ttu-id="fc580-567">Il progetto avrà un minuto alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="fc580-568">Compilazione, in seguito **Esplora File** apparirà mostrano la posizione del nuovo progetto.</span><span class="sxs-lookup"><span data-stu-id="fc580-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="fc580-569">Nessuna necessità di aprire il file, tuttavia, che è necessario creare anche l'altro Unity project in primo luogo, entro i prossimi capitoli.</span><span class="sxs-lookup"><span data-stu-id="fc580-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="fc580-570">Capitolo 12: configurare progetti di Unity di realtà mista</span><span class="sxs-lookup"><span data-stu-id="fc580-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="fc580-571">Di seguito è una tipica configurato per lo sviluppo con la realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="fc580-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="fc580-572">Aprire **Unity** e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="fc580-572">Open **Unity** and click **New**.</span></span>

    ![nuovo progetto unity](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="fc580-574">A questo punto si dovrà fornire un nome di progetto Unity, inserire **UnityMRNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="fc580-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="fc580-575">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="fc580-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="fc580-576">Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="fc580-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="fc580-577">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="fc580-577">Then, click **Create project**.</span></span>

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="fc580-579">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="fc580-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="fc580-580">Passare a **Edit** > **preferenze** e quindi dalla nuova finestra, passare al **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="fc580-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="fc580-581">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="fc580-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="fc580-582">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="fc580-582">Close the **Preferences** window.</span></span>

    ![set editor esterno a Visual Studio](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="fc580-584">Passare quindi ad **File** > **Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic su di **commutatore piattaforma**  pulsante.</span><span class="sxs-lookup"><span data-stu-id="fc580-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![piattaforme commutatore alla piattaforma UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="fc580-586">Passare a **File** > **Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="fc580-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="fc580-587">**Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="fc580-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="fc580-588">Per il Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="fc580-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="fc580-589">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="fc580-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="fc580-590">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="fc580-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="fc580-591">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="fc580-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="fc580-592">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="fc580-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="fc580-593">A questo punto, vale la pena di salvataggio della scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="fc580-594">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="fc580-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="fc580-595">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="fc580-595">A save window will appear.</span></span>

            ![aggiungere scene open](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="fc580-597">Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="fc580-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nuova cartella scene](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="fc580-599">Aprire appena creato **scene** cartella e quindi la **nome File:** campo di testo, digitare **hub di notifica\_MR\_scena**, quindi premere  **Salvare**.</span><span class="sxs-lookup"><span data-stu-id="fc580-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![new scene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="fc580-601">Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="fc580-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="fc580-602">Nella stessa finestra fare clic sui **le impostazioni del giocatore** pulsante, si aprirà il pannello correlato nello spazio in cui le **Inspector** si trova.</span><span class="sxs-lookup"><span data-stu-id="fc580-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![Aprire le impostazioni del giocatore](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="fc580-604">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="fc580-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="fc580-605">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="fc580-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="fc580-606">**Versione del Runtime di scripting** deve essere **sperimentale** (.NET 4.6 equivalente)</span><span class="sxs-lookup"><span data-stu-id="fc580-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="fc580-607">**Back-end di scripting** deve essere ***.NET***</span><span class="sxs-lookup"><span data-stu-id="fc580-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="fc580-608">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="fc580-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![compatibilità con le API](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="fc580-610">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto</span><span class="sxs-lookup"><span data-stu-id="fc580-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![xr Aggiorna impostazioni](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="fc580-612">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, archivia il:</span><span class="sxs-lookup"><span data-stu-id="fc580-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="fc580-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="fc580-613">**InternetClient**</span></span>           

            ![client internet di segni di graduazione](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="fc580-615">Nuovamente in **Build Settings**, **Unity C# progetti** non è non è più in grigio: selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="fc580-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="fc580-616">Con queste modifiche eseguite, chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="fc580-617">Salvare il progetto e la scena **File** > **Salva scena /file** > **Salva progetto**.</span><span class="sxs-lookup"><span data-stu-id="fc580-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fc580-618">Se si vuole ignorare la *configurare Unity* componente per questo progetto (App di realtà misto) e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importarlo nel progetto come una [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), quindi continuare dal [capitolo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="fc580-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="fc580-619">È comunque necessario aggiungere i componenti di script.</span><span class="sxs-lookup"><span data-stu-id="fc580-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="fc580-620">Capitolo 13 - importazione di DLL nel progetto Unity realtà mista</span><span class="sxs-lookup"><span data-stu-id="fc580-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="fc580-621">Si userà archiviazione di Azure per la libreria di Unity (che usa .net SDK per Azure).</span><span class="sxs-lookup"><span data-stu-id="fc580-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="fc580-622">Seguire questa [collegamento su come usare archiviazione di Azure con Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="fc580-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="fc580-623">È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="fc580-624">Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.</span><span class="sxs-lookup"><span data-stu-id="fc580-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="fc580-625">Per importare il SDK in un progetto, assicurarsi di aver scaricato la versione più recente [.unitypackage](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="fc580-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="fc580-626">Quindi, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-626">Then, do the following:</span></span>

1.  <span data-ttu-id="fc580-627">Aggiungere il .unitypackage scaricato da quanto sopra, Unity tramite il **asset** > **Importa pacchetto** > **pacchetto personalizzato** l'opzione di menu .</span><span class="sxs-lookup"><span data-stu-id="fc580-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="fc580-628">Nel **Importa pacchetto Unity** casella visualizzata, è possibile selezionare tutti gli elementi sotto **plug-in** > **archiviazione**.</span><span class="sxs-lookup"><span data-stu-id="fc580-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![Importa pacchetto](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="fc580-630">Scegliere il **importazione** pulsante per aggiungere elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="fc580-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="fc580-631">Andare alla **Storage** cartella sotto **plug-in** nel progetto consente di visualizzare e selezionare il plug-in seguenti *solo*:</span><span class="sxs-lookup"><span data-stu-id="fc580-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="fc580-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="fc580-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="fc580-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="fc580-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="fc580-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="fc580-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="fc580-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="fc580-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="fc580-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="fc580-636">System.Spatial</span></span>

    ![Selezionare i plug-in](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="fc580-638">Con *questi plug-in specifici* è selezionata, **deselezionare** **Any Platform** e **deselezionare** **WSAPlayer** quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="fc580-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![applicare le modifiche alla piattaforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="fc580-640">Si contrassegna questi plug-in particolare per essere usato solo nell'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="fc580-641">Questo avviene perché sono presenti versioni diverse dello stesso plug-nella cartella WSA che verrà utilizzata dopo che il progetto viene esportato da Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="fc580-642">Nel **archiviazione** cartella plug-in, selezionare solo:</span><span class="sxs-lookup"><span data-stu-id="fc580-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="fc580-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="fc580-643">Microsoft.Data.Services.Client</span></span>

        ![Selezionare il client di servizi dati](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="fc580-645">Verificare i **processo non** nella casella **impostazioni piattaforma** e fare clic su **Apply**.</span><span class="sxs-lookup"><span data-stu-id="fc580-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![non elaborare](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="fc580-647">Si contrassegna questo plug-in "Non elabora" perché il patcher assembly di Unity ha difficoltà a questo plug-in di elaborazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="fc580-648">Il plug-in continuerà a funzionare anche se questa non viene elaborata.</span><span class="sxs-lookup"><span data-stu-id="fc580-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="fc580-649">Capitolo 14 - Creazione della classe TableToScene nel progetto Unity realtà mista</span><span class="sxs-lookup"><span data-stu-id="fc580-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="fc580-650">Il **TableToScene** classe è identico a quello illustrato in [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="fc580-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="fc580-651">Creare la stessa classe nella realtà mista progetto Unity seguendo la stessa procedura illustrata nel [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="fc580-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="fc580-652">Dopo aver completato questo capitolo, entrambi i **i progetti Unity** avrà questa classe impostato su Main Camera.</span><span class="sxs-lookup"><span data-stu-id="fc580-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="fc580-653">Capitolo 15 - creazione della classe NotificationReceiver nel progetto Unity realtà mista</span><span class="sxs-lookup"><span data-stu-id="fc580-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="fc580-654">È il secondo script è necessario creare **NotificationReceiver**, che è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="fc580-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="fc580-655">La registrazione dell'app con l'Hub di notifica in fase di inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="fc580-656">Ascoltare le notifiche provenienti dall'Hub di notifica.</span><span class="sxs-lookup"><span data-stu-id="fc580-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="fc580-657">Durante la deserializzazione di dati dell'oggetto dalle notifiche ricevute.</span><span class="sxs-lookup"><span data-stu-id="fc580-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="fc580-658">Spostare il Gameobject nella scena, in base i dati deserializzati.</span><span class="sxs-lookup"><span data-stu-id="fc580-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="fc580-659">Per creare il **NotificationReceiver** script:</span><span class="sxs-lookup"><span data-stu-id="fc580-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="fc580-660">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**, **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="fc580-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="fc580-661">Denominare lo script **NotificationReceiver**.</span><span class="sxs-lookup"><span data-stu-id="fc580-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="fc580-662">![creare il nuovo script c#](images/AzureLabs-Lab8-95.png)
    ![denominarlo NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="fc580-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="fc580-663">Fare doppio clic sullo script per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="fc580-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="fc580-664">Aggiungere spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-664">Add the following namespaces:</span></span>

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

4.  <span data-ttu-id="fc580-665">Inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="fc580-665">Insert the following variables:</span></span>

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

5.  <span data-ttu-id="fc580-666">Sostituire il **hubName** valore con il nome del servizio Hub di notifica e **hubListenEndpoint** valore con il valore di endpoint disponibile nella scheda Criteri di accesso, servizio di Hub di notifica di Azure, nel Portale di Azure (vedere la figura seguente).</span><span class="sxs-lookup"><span data-stu-id="fc580-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Inserisci endpoint criteri hub di notifica](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="fc580-668">A questo punto aggiungere il **Start ()** e **Awake()** metodi per inizializzare la classe.</span><span class="sxs-lookup"><span data-stu-id="fc580-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

7.  <span data-ttu-id="fc580-669">Aggiungere il **WaitForNotification** metodo per consentire all'app di ricevere le notifiche dalla libreria di Hub di notifica senza sovrapposizioni con il Thread principale:</span><span class="sxs-lookup"><span data-stu-id="fc580-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

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

8.  <span data-ttu-id="fc580-670">Il metodo seguente, **InitNotificationAsync()** , registrerà l'applicazione con il servizio Hub di notifica in fase di inizializzazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="fc580-671">Il codice viene commentato poiché Unity non saranno in grado di compilare il progetto.</span><span class="sxs-lookup"><span data-stu-id="fc580-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="fc580-672">Quando si importa il pacchetto Nuget di messaggistica di Azure in Visual Studio verranno rimossi i commenti.</span><span class="sxs-lookup"><span data-stu-id="fc580-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

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

9.  <span data-ttu-id="fc580-673">Il seguente gestore **Channel\_PushNotificationReceived()** , verrà attivata ogni volta che viene ricevuta una notifica.</span><span class="sxs-lookup"><span data-stu-id="fc580-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="fc580-674">Eseguirà la deserializzazione di notifica, che verrà entità della tabella di Azure che è stato spostato nell'applicazione Desktop e quindi spostare il GameObject corrispondente nella scena MR nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="fc580-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="fc580-675">Il codice viene commentato perché il codice fa riferimento la libreria di messaggistica di Azure, che verranno aggiunti dopo la compilazione del progetto Unity usando Gestione pacchetti Nuget, Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc580-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="fc580-676">Di conseguenza, il progetto Unity non sarà possibile creare, a meno che questo non è commentato. Tenere presente, che dovrebbe si compila il progetto e quindi si vuole tornare a Unity, dovrai **nuovamente commento** tale codice.</span><span class="sxs-lookup"><span data-stu-id="fc580-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

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

10. <span data-ttu-id="fc580-677">Ricordarsi di salvare le modifiche prima di tornare all'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="fc580-678">Fare clic sui **Main Camera** dalle **gerarchia** pannello, in modo che le proprietà visualizzate nella **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="fc580-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="fc580-679">Con il **gli script** aperto, selezionare cartella la **NotificationReceiver** script e trascinarla nel **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="fc580-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="fc580-680">Il risultato dovrebbe essere come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="fc580-680">The result should be as below:</span></span>

    ![Trascinare script del destinatario notifica alla fotocamera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="fc580-682">Se si sta sviluppando ciò per i Microsoft HoloLens, dovrai aggiornare il **Main Camera**del *fotocamera* componente, in modo che:</span><span class="sxs-lookup"><span data-stu-id="fc580-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="fc580-683">Cancellare i flag: Colore a tinta unita</span><span class="sxs-lookup"><span data-stu-id="fc580-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="fc580-684">Background: Nero</span><span class="sxs-lookup"><span data-stu-id="fc580-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="fc580-685">Capitolo 16 - compilare il progetto di realtà mista alla piattaforma UWP</span><span class="sxs-lookup"><span data-stu-id="fc580-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="fc580-686">In questo capitolo è identico al processo per il progetto precedente di compilazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="fc580-687">Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.</span><span class="sxs-lookup"><span data-stu-id="fc580-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="fc580-688">Passare a **impostazioni di compilazione** ( **File** > **impostazioni di compilazione** ).</span><span class="sxs-lookup"><span data-stu-id="fc580-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="fc580-689">Dal **Build Settings** menu, assicurarsi che **Unity C# progetti**\* è selezionata (che consente di modificare gli script di questo progetto, dopo la compilazione).</span><span class="sxs-lookup"><span data-stu-id="fc580-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="fc580-690">Dopo questa operazione, fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="fc580-690">After this is done, click **Build**.</span></span>

    ![Compila progetto](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="fc580-692">Oggetto **Esplora File** popup verrà finestra, di cui è possibile specificare un percorso di compilazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="fc580-693">Creare una nuova cartella (facendo **nuova cartella** nell'angolo superiore sinistro) e denominarla **COMPILA**.</span><span class="sxs-lookup"><span data-stu-id="fc580-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![creare una cartella delle build](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="fc580-695">Aprire il nuovo **si basa** cartella e creare un'altra cartella (utilizzando **nuova cartella** ancora una volta) e denominarlo **hub di notifica\_MR\_App**.</span><span class="sxs-lookup"><span data-stu-id="fc580-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![Crea cartella NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="fc580-697">Con il **hub di notifica\_MR\_App** selezionato.</span><span class="sxs-lookup"><span data-stu-id="fc580-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="fc580-698">Fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="fc580-698">click **Select Folder**.</span></span> <span data-ttu-id="fc580-699">Il progetto avrà un minuto alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="fc580-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="fc580-700">Dopo la compilazione, un **Esplora File** aprirà la finestra in corrispondenza della posizione del nuovo progetto.</span><span class="sxs-lookup"><span data-stu-id="fc580-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="fc580-701">Capitolo 17 - aggiungere pacchetti NuGet alla soluzione UnityMRNotifHub</span><span class="sxs-lookup"><span data-stu-id="fc580-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="fc580-702">Si ricordi che, dopo aver aggiunto i pacchetti NuGet seguenti (e rimuovere il commento il codice entro i prossimi [capitolo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), il codice, quando all'interno del progetto Unity, riaperto presenterà errori.</span><span class="sxs-lookup"><span data-stu-id="fc580-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="fc580-703">Se si vuole tornare indietro e continuare la modifica nell'Editor di Unity, sarà necessario commentare tale codice errosome e quindi rimuovere il commento nuovamente in un secondo momento, quando si è in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc580-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="fc580-704">Dopo aver completata la compilazione di realtà mista, passare al progetto di realtà mista, è stata compilata, e fare doppio clic sul file di soluzione (sln) da quella cartella, aprire la soluzione con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fc580-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="fc580-705">È ora necessario aggiungere il **Windowsazure** pacchetto NuGet; si tratta di una libreria che consente di ricevere le notifiche dall'Hub di notifica.</span><span class="sxs-lookup"><span data-stu-id="fc580-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="fc580-706">Per importare il pacchetto NuGet:</span><span class="sxs-lookup"><span data-stu-id="fc580-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="fc580-707">Nel **Esplora soluzioni**, fare clic con il pulsante destro sulla soluzione</span><span class="sxs-lookup"><span data-stu-id="fc580-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="fc580-708">Fare clic su **Gestisci pacchetti NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fc580-708">Click on **Manage NuGet Packages**.</span></span>

    ![Aprire Gestione nuget](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="fc580-710">Selezionare il ***esplorare*** scheda e cercare **Windowsazure**.</span><span class="sxs-lookup"><span data-stu-id="fc580-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![trovare il pacchetto di messaggistica di windows azure](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="fc580-712">Selezionare il risultato (come illustrato di seguito) e nella finestra a destra, selezionare la casella di controllo accanto a **progetto**.</span><span class="sxs-lookup"><span data-stu-id="fc580-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="fc580-713">Verrà inserito un segno di spunta nella casella di controllo accanto a **Project**, con la casella di controllo accanto al **Assembly-CSharp** e **UnityMRNotifHub** progetto.</span><span class="sxs-lookup"><span data-stu-id="fc580-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![tutti i progetti di graduazione](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="fc580-715">La versione fornita inizialmente **potrebbe non** siano compatibili con questo progetto.</span><span class="sxs-lookup"><span data-stu-id="fc580-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="fc580-716">Pertanto, fare clic sul menu a discesa accanto a **versione**, fare clic su **versione 0.1.7.9**, quindi fare clic su **installare**.</span><span class="sxs-lookup"><span data-stu-id="fc580-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="fc580-717">È ora di installazione del pacchetto NuGet è stata completata.</span><span class="sxs-lookup"><span data-stu-id="fc580-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="fc580-718">Trovare il codice con commento immessi nella **NotificationReceiver** classe e rimuovere i commenti...</span><span class="sxs-lookup"><span data-stu-id="fc580-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="fc580-719">Capitolo 18 - classe NotificationReceiver, UnityMRNotifHub Modifica applicazione</span><span class="sxs-lookup"><span data-stu-id="fc580-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="fc580-720">Dopo avere aggiunto il **i pacchetti NuGet**, sarà necessario *rimuovere il commento* parte del codice all'interno del **NotificationReceiver** classe.</span><span class="sxs-lookup"><span data-stu-id="fc580-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="fc580-721">È possibile creare, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="fc580-721">This includes:</span></span>

1. <span data-ttu-id="fc580-722">Lo spazio dei nomi nella parte superiore:</span><span class="sxs-lookup"><span data-stu-id="fc580-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="fc580-723">Tutto il codice all'interno di **InitNotificationsAsync()** metodo:</span><span class="sxs-lookup"><span data-stu-id="fc580-723">All the code within the **InitNotificationsAsync()** method:</span></span>

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
> <span data-ttu-id="fc580-724">Il codice precedente contiene un commento: assicurarsi di aver accidentalmente *senza commenti* che come commento (come il codice non verrà compilato se hai!).</span><span class="sxs-lookup"><span data-stu-id="fc580-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="fc580-725">E, infine, il **Channel_PushNotificationReceived** evento:</span><span class="sxs-lookup"><span data-stu-id="fc580-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

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

<span data-ttu-id="fc580-726">Con questi senza commenti, assicurarsi di salvare e quindi procedere al capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="fc580-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="fc580-727">Capitolo 19 - associare il progetto di realtà mista per l'app Store</span><span class="sxs-lookup"><span data-stu-id="fc580-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="fc580-728">È ora necessario associare il **realtà mista** progetto nell'App Store creato all'inizio del lab.</span><span class="sxs-lookup"><span data-stu-id="fc580-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="fc580-729">Aprire la soluzione.</span><span class="sxs-lookup"><span data-stu-id="fc580-729">Open the solution.</span></span>

2.  <span data-ttu-id="fc580-730">Fare clic con il pulsante destro sul progetto di app UWP nel Pannello di Esplora soluzioni, andare al **Store**, e **Associa applicazione a Store di...** .</span><span class="sxs-lookup"><span data-stu-id="fc580-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![Aprire associazione archivio](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="fc580-732">Verrà visualizzata una nuova finestra chiamata **associa l'applicazione con il Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="fc580-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="fc580-733">Fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="fc580-733">Click **Next**.</span></span>

    ![Passare alla schermata successiva](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="fc580-735">Verrà caricato tutte le applicazioni associate con l'Account che hanno effettuato l'accesso.</span><span class="sxs-lookup"><span data-stu-id="fc580-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="fc580-736">Se non si è connessi al proprio account, è possibile **Log In** in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="fc580-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="fc580-737">Trovare il **nome dell'App Store** creato all'inizio di questa esercitazione e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="fc580-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="fc580-738">Fare quindi clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="fc580-738">Then click **Next**.</span></span>

    ![Individuare e selezionare il nome dell'archivio](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="fc580-740">Fare clic su **associare**.</span><span class="sxs-lookup"><span data-stu-id="fc580-740">Click **Associate**.</span></span>

    ![associare l'app](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="fc580-742">L'App è ora **Associated** con l'App Store.</span><span class="sxs-lookup"><span data-stu-id="fc580-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="fc580-743">Ciò è necessario per l'abilitazione di notifiche.</span><span class="sxs-lookup"><span data-stu-id="fc580-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="fc580-744">Capitolo 20 - distribuire applicazioni UnityMRNotifHub e UnityDesktopNotifHub</span><span class="sxs-lookup"><span data-stu-id="fc580-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="fc580-745">In questo capitolo può essere più semplice con due persone, poiché il risultato includerà sia le App in esecuzione, una in esecuzione nel computer Desktop e l'altro all'interno di visore VR immersivi.</span><span class="sxs-lookup"><span data-stu-id="fc580-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="fc580-746">L'app visore VR immersivi è in attesa di ricevere le modifiche alla scena (modifiche della posizione del Gameobject locale) e l'app Desktop subirà modifiche alla loro scena locale (modifiche della posizione), che verrà condiviso con l'app MR.</span><span class="sxs-lookup"><span data-stu-id="fc580-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="fc580-747">È opportuno distribuire l'app MR in primo luogo, seguita dall'app Desktop, in modo che il destinatario può iniziare in ascolto.</span><span class="sxs-lookup"><span data-stu-id="fc580-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="fc580-748">Per distribuire il **UnityMRNotifHub** app nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="fc580-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="fc580-749">Aprire il file della soluzione delle **UnityMRNotifHub** in app **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="fc580-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="fc580-750">Nel **piattaforma soluzione**, selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="fc580-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="fc580-751">Nel **configurazione della soluzione** selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="fc580-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![set di configurazione del progetto](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="fc580-753">Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.</span><span class="sxs-lookup"><span data-stu-id="fc580-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="fc580-754">L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="fc580-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="fc580-755">Per distribuire il **UnityDesktopNotifHub** app nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="fc580-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="fc580-756">Aprire il file della soluzione delle **UnityDesktopNotifHub** in app **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="fc580-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="fc580-757">Nel **piattaforma soluzione**, selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="fc580-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="fc580-758">Nel **configurazione della soluzione** selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="fc580-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![set di configurazione del progetto](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="fc580-760">Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.</span><span class="sxs-lookup"><span data-stu-id="fc580-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="fc580-761">L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="fc580-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="fc580-762">Avviare l'applicazione di realtà mista, seguito dall'applicazione Desktop.</span><span class="sxs-lookup"><span data-stu-id="fc580-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="fc580-763">Con entrambe le applicazioni in esecuzione, spostare un oggetto nella scena desktop (con il pulsante del Mouse a sinistra).</span><span class="sxs-lookup"><span data-stu-id="fc580-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="fc580-764">Queste modifiche posizionali verranno essere eseguite in locale, serializzate e inviate al servizio App per le funzioni.</span><span class="sxs-lookup"><span data-stu-id="fc580-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="fc580-765">Il servizio App per le funzioni aggiornerà quindi la tabella con l'Hub di notifica.</span><span class="sxs-lookup"><span data-stu-id="fc580-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="fc580-766">Aver ricevuto un aggiornamento, l'Hub di notifica invia i dati aggiornati direttamente a tutte le applicazioni registrate (in questo caso l'app visore VR immersivi), che verranno quindi deserializzare i dati in ingresso e applicare i nuovi dati posizionali agli oggetti locali, lo spostamento nella scena.</span><span class="sxs-lookup"><span data-stu-id="fc580-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="fc580-767">Il termine applicazione hub di notifica di Azure</span><span class="sxs-lookup"><span data-stu-id="fc580-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="fc580-768">Complimenti, è stata compilata un'app per realtà mista che sfrutta il servizio hub di notifica di Azure e consentire la comunicazione tra app.</span><span class="sxs-lookup"><span data-stu-id="fc580-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![versione finale del prodotto-fine](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="fc580-770">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="fc580-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="fc580-771">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="fc580-771">Exercise 1</span></span>

<span data-ttu-id="fc580-772">È possibile usare le istruzioni per modificare il colore del Gameobject e inviare notifica ad altre App visualizzazione scena?</span><span class="sxs-lookup"><span data-stu-id="fc580-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="fc580-773">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="fc580-773">Exercise 2</span></span>

<span data-ttu-id="fc580-774">È possibile aggiungere lo spostamento del Gameobject all'app di MR e visualizzato la scena aggiornata nell'app desktop?</span><span class="sxs-lookup"><span data-stu-id="fc580-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
