---
title: MR e Azure 311-Microsoft Graph
description: Completare questo corso per apprendere come sfruttare Microsoft Graph e connettersi ai dati che determinano la produttività, all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, Microsoft Graph, hololens, immersive, VR
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694521"
---
>[!NOTE]
><span data-ttu-id="f8fad-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f8fad-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f8fad-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="f8fad-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f8fad-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f8fad-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f8fad-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="f8fad-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f8fad-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f8fad-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f8fad-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="f8fad-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="f8fad-110">MR e Azure 311-Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="f8fad-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="f8fad-111">In questo corso si apprenderà come usare *Microsoft Graph* per accedere al account Microsoft usando l'autenticazione protetta all'interno di un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f8fad-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="f8fad-112">Sarà quindi possibile recuperare e visualizzare le riunioni pianificate nell'interfaccia dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f8fad-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="f8fad-113">*Microsoft Graph* è un set di API progettate per consentire l'accesso a molti dei servizi Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f8fad-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="f8fad-114">Microsoft descrive Microsoft Graph come una matrice di risorse connesse da relazioni, il che significa che consente a un'applicazione di accedere a tutti i tipi di dati utente connessi.</span><span class="sxs-lookup"><span data-stu-id="f8fad-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="f8fad-115">Per ulteriori informazioni, visitare la [pagina Microsoft Graph](https://developer.microsoft.com/graph).</span><span class="sxs-lookup"><span data-stu-id="f8fad-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="f8fad-116">Lo sviluppo includerà la creazione di un'app in cui l'utente verrà istruito a osservare e quindi toccare una sfera, che chiederà all'utente di accedere in modo sicuro a una account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f8fad-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="f8fad-117">Una volta effettuato l'accesso al proprio account, l'utente sarà in grado di visualizzare un elenco di riunioni pianificate per la giornata.</span><span class="sxs-lookup"><span data-stu-id="f8fad-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="f8fad-118">Dopo aver completato questo corso, si disporrà di un'applicazione HoloLens in realtà mista, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="f8fad-119">Usando il gesto Tap, toccare un oggetto per richiedere all'utente di accedere a un account Microsoft (uscendo dall'app per accedere e quindi nuovamente nell'app).</span><span class="sxs-lookup"><span data-stu-id="f8fad-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="f8fad-120">Visualizza un elenco di riunioni pianificate per il giorno.</span><span class="sxs-lookup"><span data-stu-id="f8fad-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="f8fad-121">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="f8fad-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="f8fad-122">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="f8fad-123">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="f8fad-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="f8fad-124">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="f8fad-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f8fad-125">Corso</span><span class="sxs-lookup"><span data-stu-id="f8fad-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f8fad-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f8fad-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f8fad-127"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="f8fad-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f8fad-128">MR e Azure 311: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="f8fad-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="f8fad-129">✔️</span><span class="sxs-lookup"><span data-stu-id="f8fad-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="f8fad-130">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="f8fad-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f8fad-131">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="f8fad-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f8fad-132">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="f8fad-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="f8fad-133">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="f8fad-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="f8fad-134">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f8fad-135">Un computer di sviluppo</span><span class="sxs-lookup"><span data-stu-id="f8fad-135">A development PC</span></span>
- [<span data-ttu-id="f8fad-136">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="f8fad-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f8fad-137">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="f8fad-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f8fad-138">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="f8fad-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f8fad-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f8fad-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="f8fad-140">[Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="f8fad-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f8fad-141">Accesso a Internet per il programma di installazione di Azure e Microsoft Graph il recupero dei dati</span><span class="sxs-lookup"><span data-stu-id="f8fad-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="f8fad-142">Un **account Microsoft** valido (personale o aziendale/dell'Istituto di istruzione)</span><span class="sxs-lookup"><span data-stu-id="f8fad-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="f8fad-143">Alcune riunioni pianificate per il giorno corrente, usando lo stesso account Microsoft</span><span class="sxs-lookup"><span data-stu-id="f8fad-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="f8fad-144">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="f8fad-144">Before you start</span></span>

1.  <span data-ttu-id="f8fad-145">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="f8fad-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="f8fad-146">Configurare e testare il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f8fad-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="f8fad-147">Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="f8fad-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="f8fad-148">Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="f8fad-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="f8fad-149">Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="f8fad-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="f8fad-150">Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="f8fad-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="f8fad-151">Capitolo 1-creare l'app nel portale di registrazione delle applicazioni</span><span class="sxs-lookup"><span data-stu-id="f8fad-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="f8fad-152">Per iniziare, sarà necessario creare e registrare l'applicazione nel **portale di registrazione dell'applicazione**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="f8fad-153">In questo capitolo si troverà anche la chiave del servizio che consentirà di effettuare chiamate a *Microsoft Graph* per accedere al contenuto dell'account.</span><span class="sxs-lookup"><span data-stu-id="f8fad-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="f8fad-154">Passare al [portale di registrazione delle applicazioni Microsoft](https://apps.dev.microsoft.com) e accedere con l'account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f8fad-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="f8fad-155">Dopo aver eseguito l'accesso, si verrà reindirizzati al **portale di registrazione delle applicazioni**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="f8fad-156">Nella sezione **applicazioni personali** fare clic sul pulsante **Aggiungi un'app**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="f8fad-157">Il **portale di registrazione delle applicazioni** può avere un aspetto diverso, a seconda che in precedenza sia stato usato *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="f8fad-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="f8fad-158">Le schermate seguenti visualizzano queste versioni diverse.</span><span class="sxs-lookup"><span data-stu-id="f8fad-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="f8fad-159">Aggiungere un nome per l'applicazione e fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="f8fad-160">Una volta creata l'applicazione, si verrà reindirizzati alla pagina principale dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f8fad-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="f8fad-161">Copiare l' **ID applicazione** e assicurarsi di prendere nota di questo valore in un punto sicuro, che verrà usato a breve nel codice.</span><span class="sxs-lookup"><span data-stu-id="f8fad-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="f8fad-162">Nella sezione **piattaforme** verificare che sia visualizzata l' **applicazione nativa** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="f8fad-163">Se *non* si fa clic su **Aggiungi piattaforma** e selezionare **applicazione nativa**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="f8fad-164">Scorrere verso il basso nella stessa pagina e nella sezione chiamata **autorizzazioni Microsoft Graph** sarà necessario aggiungere altre autorizzazioni per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f8fad-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="f8fad-165">Fare clic su **Aggiungi** accanto a **autorizzazioni delegate**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="f8fad-166">Poiché si desidera che l'applicazione acceda al calendario dell'utente, selezionare la casella **calendari. Read** e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="f8fad-167">Scorrere fino alla fine e fare clic sul pulsante **Salva** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="f8fad-168">Il salvataggio verrà confermato ed è possibile disconnettersi dal **portale di registrazione delle applicazioni**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="f8fad-169">Capitolo 2: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="f8fad-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="f8fad-170">Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="f8fad-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="f8fad-171">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="f8fad-172">È necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="f8fad-173">Inserire **MSGraphMR**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="f8fad-174">Verificare che il modello di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="f8fad-175">Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="f8fad-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="f8fad-176">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="f8fad-177">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f8fad-178">Passare a **modifica** > **Preferenze** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f8fad-179">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f8fad-180">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="f8fad-181">Passare a**impostazioni di compilazione** **file** > e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="f8fad-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="f8fad-182">Sempre nelle**impostazioni di compilazione** **file** > , verificare che:</span><span class="sxs-lookup"><span data-stu-id="f8fad-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="f8fad-183">Il **dispositivo di destinazione** è impostato su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="f8fad-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="f8fad-184">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="f8fad-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="f8fad-185">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="f8fad-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="f8fad-186">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="f8fad-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="f8fad-187">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="f8fad-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="f8fad-188">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="f8fad-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="f8fad-189">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="f8fad-190">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="f8fad-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="f8fad-191">Creare una nuova cartella per questo e qualsiasi scena futura.</span><span class="sxs-lookup"><span data-stu-id="f8fad-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="f8fad-192">Selezionare il pulsante **nuova cartella** per creare una nuova cartella, denominarla **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="f8fad-193">Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **MR_ComputerVisionScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="f8fad-194">Tenere presente che è necessario salvare le scene Unity all' interno della cartella assets, in quanto devono essere associate al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="f8fad-195">La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="f8fad-196">Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="f8fad-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="f8fad-197">Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .</span><span class="sxs-lookup"><span data-stu-id="f8fad-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="f8fad-198">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="f8fad-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="f8fad-199">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="f8fad-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="f8fad-200">Creazione di **script** La **versione di runtime** deve essere **sperimentale** (equivalente a .NET 4,6), che attiverà la necessità di riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="f8fad-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="f8fad-201">Il **back-end** di scripting deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="f8fad-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="f8fad-202">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="f8fad-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="f8fad-203">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="f8fad-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="f8fad-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f8fad-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="f8fad-205">Nella parte inferiore del pannello, in **Impostazioni XR** (disponibili sotto **le impostazioni di pubblicazione**), controllare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="f8fad-206">Nelle *impostazioni di compilazione*, *i C# progetti Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="f8fad-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="f8fad-207">Chiudere la finestra *impostazioni di compilazione* .</span><span class="sxs-lookup"><span data-stu-id="f8fad-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="f8fad-208">Salva la scena e il progetto (**progetto**Salva**file** >  **/Salva file** > ).</span><span class="sxs-lookup"><span data-stu-id="f8fad-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="f8fad-209">Capitolo 3-importare le librerie in Unity</span><span class="sxs-lookup"><span data-stu-id="f8fad-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8fad-210">Se si vuole ignorare il componente di *configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricare questo [Azure-Mr-311. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 5 ](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="f8fad-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="f8fad-211">Per usare *Microsoft Graph* in Unity, è necessario usare la dll **Microsoft. Identity. client** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="f8fad-212">È possibile usare l'SDK Microsoft Graph, tuttavia, richiede l'aggiunta di un pacchetto NuGet dopo la compilazione del progetto Unity (ovvero la modifica del progetto post-compilazione).</span><span class="sxs-lookup"><span data-stu-id="f8fad-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="f8fad-213">È considerato più semplice importare le DLL necessarie direttamente in Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="f8fad-214">Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="f8fad-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="f8fad-215">Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.</span><span class="sxs-lookup"><span data-stu-id="f8fad-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="f8fad-216">Per importare *Microsoft Graph* nel progetto, [scaricare il file MSGraph_LabPlugins. zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="f8fad-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="f8fad-217">Questo pacchetto è stato creato con le versioni delle librerie testate.</span><span class="sxs-lookup"><span data-stu-id="f8fad-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="f8fad-218">Per altre informazioni su come aggiungere DLL personalizzate al progetto Unity, vedere il [collegamento](https://docs.unity3d.com/Manual/UsingDLL.html)seguente.</span><span class="sxs-lookup"><span data-stu-id="f8fad-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="f8fad-219">Per importare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="f8fad-219">To import the package:</span></span>

1.  <span data-ttu-id="f8fad-220">Aggiungere il pacchetto Unity a Unity usando l'opzione di menu **Asset** > **Import Package** > **Custom Package** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="f8fad-221">Selezionare il pacchetto appena scaricato.</span><span class="sxs-lookup"><span data-stu-id="f8fad-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="f8fad-222">Nella casella **Importa pacchetto Unity** visualizzata verificare che siano selezionati tutti gli elementi in (e inclusi) **plug** -in.</span><span class="sxs-lookup"><span data-stu-id="f8fad-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="f8fad-223">Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="f8fad-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="f8fad-224">Passare alla cartella **MSGraph** in **plugins** nel *Pannello Project* e selezionare il plug-in denominato **Microsoft. Identity. client**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="f8fad-225">Con il *plug* -in selezionato, assicurarsi che **qualsiasi piattaforma** sia deselezionata, quindi assicurarsi che **WSAPlayer** sia deselezionata, quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="f8fad-226">Questa operazione è sufficiente per verificare che i file siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="f8fad-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="f8fad-227">Contrassegnando questi plug-in, questi vengono configurati per essere usati solo nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="f8fad-228">Nella cartella WSA è presente un set di dll diverso che verrà usato dopo che il progetto viene esportato da Unity come applicazione Windows universale.</span><span class="sxs-lookup"><span data-stu-id="f8fad-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="f8fad-229">Successivamente, è necessario aprire la cartella **WSA** , all'interno della cartella **MSGraph** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="f8fad-230">Viene visualizzata una copia dello stesso file appena configurato.</span><span class="sxs-lookup"><span data-stu-id="f8fad-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="f8fad-231">Selezionare il file e quindi nell'Ispettore:</span><span class="sxs-lookup"><span data-stu-id="f8fad-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="f8fad-232">Verificare che **qualsiasi piattaforma** siadeselezionata e che sia **selezionato** **solo** **WSAPlayer** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="f8fad-233">Verificare che l' **SDK** sia impostato su **UWP**e che **lo scripting back-end** sia impostato su **dot net**</span><span class="sxs-lookup"><span data-stu-id="f8fad-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="f8fad-234">Assicurarsi che l'opzione **non elaborare** sia **selezionata**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="f8fad-235">Fare clic su **Applica**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="f8fad-236">Capitolo 4-configurazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="f8fad-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="f8fad-237">Durante questo capitolo verrà configurata la fotocamera principale della scena:</span><span class="sxs-lookup"><span data-stu-id="f8fad-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="f8fad-238">Nel *Pannello gerarchia*selezionare la **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="f8fad-239">Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel pannello di *controllo* .</span><span class="sxs-lookup"><span data-stu-id="f8fad-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="f8fad-240">L' **oggetto fotocamera** deve essere denominato **Main camera** (nota l'ortografia).</span><span class="sxs-lookup"><span data-stu-id="f8fad-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="f8fad-241">Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (si noti l'ortografia).</span><span class="sxs-lookup"><span data-stu-id="f8fad-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="f8fad-242">Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="f8fad-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="f8fad-243">Imposta **Cancella flag** su **colore a tinta unita**</span><span class="sxs-lookup"><span data-stu-id="f8fad-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="f8fad-244">Imposta il **colore di sfondo** del componente della fotocamera su **nero, alfa 0** **(codice esadecimale: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="f8fad-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="f8fad-245">La struttura dell'oggetto finale nel *Pannello gerarchia* deve essere simile a quella illustrata nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="f8fad-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="f8fad-246">Capitolo 5-creare la classe MeetingsUI</span><span class="sxs-lookup"><span data-stu-id="f8fad-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="f8fad-247">Il primo script che è necessario creare è **MeetingsUI**, che è responsabile dell'hosting e del popolamento dell'interfaccia utente dell'applicazione (messaggio di benvenuto, istruzioni e dettagli delle riunioni).</span><span class="sxs-lookup"><span data-stu-id="f8fad-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="f8fad-248">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="f8fad-248">To create this class:</span></span>

1.  <span data-ttu-id="f8fad-249">Fare clic con il pulsante destro del mouse sulla cartella **Asset** nel *pannello progetto*, quindi scegliere **Crea** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="f8fad-250">Denominare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="f8fad-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="f8fad-251">Aprire la cartella Scripts, quindi, in tale cartella, fare clic con il pulsante destro del mouse su **Crea**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="f8fad-252">Denominare lo script **MeetingsUI.**</span><span class="sxs-lookup"><span data-stu-id="f8fad-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="f8fad-253">Fare doppio clic sul nuovo script **MeetingsUI** per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="f8fad-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="f8fad-254">Inserire gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="f8fad-255">All'interno della classe inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="f8fad-256">Sostituire quindi il metodo **Start ()** e aggiungere un metodo **svegli ()** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="f8fad-257">Questi verranno chiamati quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="f8fad-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="f8fad-258">Aggiungere i metodi responsabili della creazione dell' *interfaccia utente riunioni* e popolarla con le riunioni correnti quando richiesto:</span><span class="sxs-lookup"><span data-stu-id="f8fad-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="f8fad-259">**Eliminare** il metodo **Update ()** e **salvare le modifiche** in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="f8fad-260">Capitolo 6: creare la classe Graph</span><span class="sxs-lookup"><span data-stu-id="f8fad-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="f8fad-261">Lo script successivo da creare è lo script **Graph** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="f8fad-262">Questo script è responsabile dell'esecuzione delle chiamate per autenticare l'utente e recuperare le riunioni pianificate per il giorno corrente dal calendario dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f8fad-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="f8fad-263">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="f8fad-263">To create this class:</span></span>

1.  <span data-ttu-id="f8fad-264">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="f8fad-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="f8fad-265">Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="f8fad-266">Denominare lo script **Graph**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="f8fad-267">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8fad-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="f8fad-268">Inserire gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f8fad-269">Si noterà che le parti del codice in questo script sono incapsulate intorno alle [direttive di precompilazione](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), in modo da evitare problemi con le librerie durante la compilazione della soluzione di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8fad-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="f8fad-270">Eliminare i metodi **Start ()** e **Update ()** perché non verranno usati.</span><span class="sxs-lookup"><span data-stu-id="f8fad-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="f8fad-271">All'esterno della classe **Graph** inserire gli oggetti seguenti, necessari per deserializzare l'oggetto JSON che rappresenta le riunioni pianificate giornaliere:</span><span class="sxs-lookup"><span data-stu-id="f8fad-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="f8fad-272">All'interno della classe **Graph** aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="f8fad-273">Modificare il valore **AppID** in modo che sia l' **ID app** annotato nel  **[capitolo 1](#chapter-1---create-your-app-in-the-application-registration-portal), passaggio 4**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="f8fad-274">Questo valore deve corrispondere a quello visualizzato nel **portale di registrazione delle applicazioni,** nella pagina di registrazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f8fad-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="f8fad-275">All'interno della classe **Graph** aggiungere i metodi **SignInAsync ()** e **AquireTokenAsync ()** che richiederanno all'utente di inserire le credenziali di accesso.</span><span class="sxs-lookup"><span data-stu-id="f8fad-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="f8fad-276">Aggiungere i due metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="f8fad-277">**BuildTodayCalendarEndpoint ()** , che compila l'URI che specifica il giorno e l'intervallo di tempo in cui vengono recuperate le riunioni pianificate.</span><span class="sxs-lookup"><span data-stu-id="f8fad-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="f8fad-278">**ListMeetingsAsync ()** , che richiede le riunioni pianificate da *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="f8fad-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="f8fad-279">A questo punto è stato completato lo script **Graph** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="f8fad-280">**Salvare le modifiche** in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="f8fad-281">Capitolo 7: creare lo script GazeInput</span><span class="sxs-lookup"><span data-stu-id="f8fad-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="f8fad-282">A questo punto verrà creato il **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="f8fad-283">Questa classe gestisce e tiene traccia dello sguardo dell'utente, usando un **Raycast** proveniente dalla **fotocamera principale**, proiettando in futuro.</span><span class="sxs-lookup"><span data-stu-id="f8fad-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="f8fad-284">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="f8fad-284">To create the script:</span></span>

1.  <span data-ttu-id="f8fad-285">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="f8fad-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="f8fad-286">Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="f8fad-287">Denominare lo script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="f8fad-288">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8fad-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="f8fad-289">Modificare il codice degli spazi dei nomi in modo che corrisponda a quello riportato di seguito, oltre ad aggiungere il tag ' **\[System. Serializable\]** ' sopra la classe **GazeInput** , in modo che possa essere serializzato:</span><span class="sxs-lookup"><span data-stu-id="f8fad-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="f8fad-290">All'interno della classe **GazeInput** aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="f8fad-291">Aggiungere il metodo **CreateCursor ()** per creare il cursore HoloLens nella scena e chiamare il metodo dal metodo **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="f8fad-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="f8fad-292">I metodi seguenti abilitano lo sguardo Raycast e tengono traccia degli oggetti specifici.</span><span class="sxs-lookup"><span data-stu-id="f8fad-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="f8fad-293">**Salvare le modifiche** in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="f8fad-294">Capitolo 8: creare la classe di interazioni</span><span class="sxs-lookup"><span data-stu-id="f8fad-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="f8fad-295">A questo punto sarà necessario creare lo script delle **interazioni** , responsabile di:</span><span class="sxs-lookup"><span data-stu-id="f8fad-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="f8fad-296">Gestione dell'interazione **Tap** e dello **sguardo della fotocamera**, che consente all'utente di interagire con il pulsante di accesso nella scena.</span><span class="sxs-lookup"><span data-stu-id="f8fad-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="f8fad-297">Creazione dell'oggetto di accesso "button" nella scena per l'interazione dell'utente con.</span><span class="sxs-lookup"><span data-stu-id="f8fad-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="f8fad-298">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="f8fad-298">To create the script:</span></span>

1.  <span data-ttu-id="f8fad-299">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="f8fad-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="f8fad-300">Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="f8fad-301">Denominare le **interazioni**dello script.</span><span class="sxs-lookup"><span data-stu-id="f8fad-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="f8fad-302">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8fad-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="f8fad-303">Inserire gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f8fad-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="f8fad-304">Modificare l'ereditarietà della classe di **interazione** da *monobehavior* a **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="f8fad-305">~~Interazioni tra classi pubbliche: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="f8fad-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="f8fad-306">All'interno della classe di **interazione** inserire la variabile seguente:</span><span class="sxs-lookup"><span data-stu-id="f8fad-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="f8fad-307">Sostituire il metodo **Start** ; Si noti che si tratta di un metodo di override, che chiama il metodo della classe di sguardi "base".</span><span class="sxs-lookup"><span data-stu-id="f8fad-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="f8fad-308">**Start ()** verrà chiamato quando la classe viene inizializzata, registrandosi per il riconoscimento dell'input e creando il *pulsante* di accesso nella scena:</span><span class="sxs-lookup"><span data-stu-id="f8fad-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="f8fad-309">Aggiungere il metodo **CreateSignInButton ()** che creerà un'istanza del *pulsante* Accedi nella scena e ne imposterà le proprietà:</span><span class="sxs-lookup"><span data-stu-id="f8fad-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="f8fad-310">Aggiungere il metodo **GestureRecognizer_Tapped ()** che risponde per l'evento *Tap* User.</span><span class="sxs-lookup"><span data-stu-id="f8fad-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="f8fad-311">**Eliminare** il metodo **Update ()** e quindi **salvare le modifiche** in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="f8fad-312">Capitolo 9: impostare i riferimenti agli script</span><span class="sxs-lookup"><span data-stu-id="f8fad-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="f8fad-313">In questo capitolo è necessario inserire lo script delle **interazioni** sulla **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="f8fad-314">Tale script gestirà quindi l'inserimento degli altri script in cui devono essere.</span><span class="sxs-lookup"><span data-stu-id="f8fad-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="f8fad-315">Dalla cartella **script** nel pannello del *progetto*trascinare le **interazioni** degli script nell'oggetto della **fotocamera principale** , come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="f8fad-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="f8fad-316">Capitolo 10-configurazione del tag</span><span class="sxs-lookup"><span data-stu-id="f8fad-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="f8fad-317">Il codice che gestisce lo sguardo utilizzerà il tag **SignInButton** per identificare l'oggetto con cui l'utente interagirà per accedere *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="f8fad-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="f8fad-318">Per creare il tag:</span><span class="sxs-lookup"><span data-stu-id="f8fad-318">To create the Tag:</span></span>

1.  <span data-ttu-id="f8fad-319">Nell'editor di Unity fare clic sulla **fotocamera principale** nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="f8fad-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="f8fad-320">Nel *Pannello di controllo* fare clic sul *tag* MainCamera per aprire un elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="f8fad-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="f8fad-321">Fare clic su **Aggiungi tag...**</span><span class="sxs-lookup"><span data-stu-id="f8fad-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="f8fad-322">Fare clic sul **+** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f8fad-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="f8fad-323">Scrivere il nome del tag come **SignInButton** e fare clic su Save.</span><span class="sxs-lookup"><span data-stu-id="f8fad-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="f8fad-324">Capitolo 11: compilare il progetto Unity in UWP</span><span class="sxs-lookup"><span data-stu-id="f8fad-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="f8fad-325">Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.</span><span class="sxs-lookup"><span data-stu-id="f8fad-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="f8fad-326">Passare a *impostazioni di compilazione* (**File*>*Impostazioni di compilazione**).</span><span class="sxs-lookup"><span data-stu-id="f8fad-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="f8fad-327">Se non è già stato fatto, è necessario che i **progetti Unity C\#** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="f8fad-328">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-328">Click **Build**.</span></span> <span data-ttu-id="f8fad-329">Unity avvierà una finestra di **Esplora file** , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="f8fad-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="f8fad-330">Creare la cartella adesso e denominarla **app**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="f8fad-331">Quindi, con la cartella dell' **app** selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="f8fad-332">Unity inizierà a compilare il progetto nella cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="f8fad-333">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).</span><span class="sxs-lookup"><span data-stu-id="f8fad-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="f8fad-334">Capitolo 12: eseguire la distribuzione in HoloLens</span><span class="sxs-lookup"><span data-stu-id="f8fad-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="f8fad-335">Per eseguire la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="f8fad-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="f8fad-336">È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore.**</span><span class="sxs-lookup"><span data-stu-id="f8fad-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="f8fad-337">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="f8fad-337">To do this:</span></span>

    1.  <span data-ttu-id="f8fad-338">Quando si indossa il HoloLens, aprire le **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="f8fad-339">Passa a **rete &**  > **Opzioni avanzate** **Wi-Fi** > Internet</span><span class="sxs-lookup"><span data-stu-id="f8fad-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="f8fad-340">Prendere nota dell'indirizzo **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="f8fad-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="f8fad-341">Tornare quindi a Settings ( **Impostazioni**) e quindi **aggiornare & Security** > **per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="f8fad-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="f8fad-342">Impostare la **modalità di sviluppo su**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="f8fad-343">Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="f8fad-344">Nella **configurazione della soluzione** selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="f8fad-345">Nella **piattaforma soluzione**selezionare **x86, computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="f8fad-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="f8fad-346">Verrà richiesto di inserire l' **indirizzo IP** di un dispositivo remoto (HoloLens, in questo caso, annotato).</span><span class="sxs-lookup"><span data-stu-id="f8fad-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="f8fad-347">Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f8fad-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="f8fad-348">L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="f8fad-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="f8fad-349">Applicazione Microsoft Graph HoloLens</span><span class="sxs-lookup"><span data-stu-id="f8fad-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="f8fad-350">Congratulazioni, è stata creata un'app per realtà mista che sfrutta i Microsoft Graph per leggere e visualizzare i dati del calendario degli utenti.</span><span class="sxs-lookup"><span data-stu-id="f8fad-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f8fad-351">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="f8fad-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f8fad-352">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="f8fad-352">Exercise 1</span></span>

<span data-ttu-id="f8fad-353">Usare Microsoft Graph per visualizzare altre informazioni sull'utente</span><span class="sxs-lookup"><span data-stu-id="f8fad-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="f8fad-354">Indirizzo di posta elettronica utente/numero di telefono/profilo</span><span class="sxs-lookup"><span data-stu-id="f8fad-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f8fad-355">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="f8fad-355">Exercise 1</span></span>

<span data-ttu-id="f8fad-356">Implementare il controllo vocale per spostarsi nell'interfaccia utente di Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="f8fad-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
