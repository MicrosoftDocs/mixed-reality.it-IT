---
title: MR e 311 - Microsoft Graph di Azure
description: Completa questo corso per imparare a usare Microsoft Graph e connettersi ai dati che contribuiscono alla produttività, all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, graph microsoft, hololens, coinvolgenti, vr
ms.openlocfilehash: 98fe2c872f332a21fff3af6751ae555968073a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597662"
---
>[!NOTE]
><span data-ttu-id="89e3f-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="89e3f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="89e3f-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="89e3f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="89e3f-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="89e3f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="89e3f-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="89e3f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="89e3f-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="89e3f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="89e3f-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="89e3f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="89e3f-110">MR e 311 - Microsoft Graph di Azure</span><span class="sxs-lookup"><span data-stu-id="89e3f-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="89e3f-111">In questo corso, si apprenderà come usare *Microsoft Graph* per accedere all'account Microsoft usando l'autenticazione sicura all'interno di un'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="89e3f-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="89e3f-112">È quindi e visualizzerà le riunioni pianificate nell'interfaccia dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="89e3f-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="89e3f-113">*Microsoft Graph* è un set di API progettate per consentire l'accesso a molti dei servizi Microsoft.</span><span class="sxs-lookup"><span data-stu-id="89e3f-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="89e3f-114">Microsoft descrive Microsoft Graph come una matrice di risorse connesse tramite relazioni, vale a dire che consente a un'applicazione accedere a tutti i tipi di dati dell'utente connesso.</span><span class="sxs-lookup"><span data-stu-id="89e3f-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="89e3f-115">Per altre informazioni, visitare il [pagina di Microsoft Graph](https://developer.microsoft.com/graph).</span><span class="sxs-lookup"><span data-stu-id="89e3f-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="89e3f-116">Lo sviluppo include la creazione di un'app in cui l'utente verrà indicato per fissare e quindi toccare una sfera, verrà richiesto all'utente di accedere in modo sicuro a un account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="89e3f-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="89e3f-117">Una volta effettuato l'accesso al proprio account, l'utente sarà in grado di visualizzare un elenco delle riunioni pianificate per la giornata.</span><span class="sxs-lookup"><span data-stu-id="89e3f-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="89e3f-118">Dopo aver completato il corso, si avrà una realtà mista applicazione HoloLens, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="89e3f-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="89e3f-119">Uso di movimenti di tocco, toccare su un oggetto che richiederà all'utente di accedere a un Account Microsoft (lo spostamento all'esterno dell'app per accedere e quindi eseguire nuovamente il backup nell'app).</span><span class="sxs-lookup"><span data-stu-id="89e3f-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="89e3f-120">Visualizzare un elenco delle riunioni pianificate per il giorno.</span><span class="sxs-lookup"><span data-stu-id="89e3f-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="89e3f-121">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="89e3f-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="89e3f-122">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="89e3f-123">È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="89e3f-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="89e3f-124">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="89e3f-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="89e3f-125">Corso</span><span class="sxs-lookup"><span data-stu-id="89e3f-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="89e3f-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="89e3f-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="89e3f-127"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="89e3f-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="89e3f-128">MR e 311 Azure: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="89e3f-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="89e3f-129">✔️</span><span class="sxs-lookup"><span data-stu-id="89e3f-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="89e3f-130">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="89e3f-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="89e3f-131">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="89e3f-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="89e3f-132">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="89e3f-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="89e3f-133">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quanto elencato di seguito.</span><span class="sxs-lookup"><span data-stu-id="89e3f-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="89e3f-134">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="89e3f-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="89e3f-135">Un computer di sviluppo</span><span class="sxs-lookup"><span data-stu-id="89e3f-135">A development PC</span></span>
- [<span data-ttu-id="89e3f-136">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="89e3f-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="89e3f-137">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="89e3f-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="89e3f-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="89e3f-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="89e3f-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="89e3f-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="89e3f-140">Oggetto [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="89e3f-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="89e3f-141">Accesso a Internet per la configurazione di Azure e il recupero dei dati di Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="89e3f-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="89e3f-142">Un valore valido **Account Microsoft** (personale o o dell'istituto)</span><span class="sxs-lookup"><span data-stu-id="89e3f-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="89e3f-143">Alcune riunioni pianificate per il giorno corrente, usando lo stesso Account Microsoft</span><span class="sxs-lookup"><span data-stu-id="89e3f-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="89e3f-144">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="89e3f-144">Before you start</span></span>

1.  <span data-ttu-id="89e3f-145">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="89e3f-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="89e3f-146">Configurare e testare l'HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89e3f-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="89e3f-147">Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="89e3f-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="89e3f-148">È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova App per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente).</span><span class="sxs-lookup"><span data-stu-id="89e3f-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="89e3f-149">Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="89e3f-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="89e3f-150">Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="89e3f-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="89e3f-151">Capitolo 1 - creare l'app nel portale di registrazione dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="89e3f-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="89e3f-152">Per iniziare, è necessario creare e registrare l'applicazione nel **portale di registrazione applicazione**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="89e3f-153">In questo capitolo sono inoltre disponibili la chiave del servizio che ti permetterà di effettuare chiamate a *Microsoft Graph* di accedere ai contenuti di account.</span><span class="sxs-lookup"><span data-stu-id="89e3f-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="89e3f-154">Passare al [portale di registrazione dell'applicazione Microsoft](https://apps.dev.microsoft.com) ed eseguire l'accesso con l'Account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="89e3f-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="89e3f-155">Dopo aver eseguito l'accesso, si verrà reindirizzati per il **portale di registrazione applicazione**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="89e3f-156">Nel **applicazioni personali** sezione, fare clic sul pulsante **Aggiungi un'app**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="89e3f-157">Il **portale di registrazione dell'applicazione** può risultare diversa, a seconda se si è precedentemente utilizzato con *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="89e3f-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="89e3f-158">Di seguito le schermate visualizzate queste diverse versioni.</span><span class="sxs-lookup"><span data-stu-id="89e3f-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="89e3f-159">Aggiungere un nome per l'applicazione e fare clic su **Create**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="89e3f-160">Dopo aver creata l'applicazione, si verrà reindirizzati alla pagina principale dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="89e3f-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="89e3f-161">Copia il **Id applicazione** e assicurarsi di prendere nota del valore in una posizione sicuro, verrà usato presto nel codice.</span><span class="sxs-lookup"><span data-stu-id="89e3f-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="89e3f-162">Nel **piattaforme** assicurarsi che **applicazione nativa** viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="89e3f-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="89e3f-163">Se *non* fare clic su **Aggiungi piattaforma** e selezionare **applicazione nativa**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="89e3f-164">Scorrere verso il basso nella stessa pagina e nella sezione denominata **autorizzazioni di Microsoft Graph** sarà necessario aggiungere altre autorizzazioni per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="89e3f-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="89e3f-165">Fare clic su **Add** accanto a **autorizzazioni delegate**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="89e3f-166">Poiché si desidera che l'applicazione per accedere al calendario dell'utente, selezionare la casella denominata **Calendars** e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="89e3f-167">Scorrere verso il basso e scegliere il **salvare** pulsante.</span><span class="sxs-lookup"><span data-stu-id="89e3f-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="89e3f-168">Verrà confermata la salva, è possibile disconnettersi quindi dal **portale di registrazione applicazione**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="89e3f-169">Capitolo 2 - configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="89e3f-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="89e3f-170">Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="89e3f-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="89e3f-171">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="89e3f-172">È necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="89e3f-173">Insert **MSGraphMR**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="89e3f-174">Verificare che il modello di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="89e3f-175">Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="89e3f-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="89e3f-176">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="89e3f-177">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="89e3f-178">Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-178">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="89e3f-179">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="89e3f-180">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="89e3f-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="89e3f-181">Passare a **File > Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sui **commutatore piattaforma** pulsante per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="89e3f-181">Go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="89e3f-182">Mentre si trovano ancora nella **File > Build Settings**, assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="89e3f-182">While still in **File > Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="89e3f-183">**Dispositivo di destinazione** è impostata su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="89e3f-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="89e3f-184">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="89e3f-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="89e3f-185">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="89e3f-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="89e3f-186">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="89e3f-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="89e3f-187">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="89e3f-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="89e3f-188">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="89e3f-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="89e3f-189">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="89e3f-190">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="89e3f-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="89e3f-191">Creare una nuova cartella per questa operazione e qualsiasi futuro, la scena.</span><span class="sxs-lookup"><span data-stu-id="89e3f-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="89e3f-192">Selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="89e3f-193">Aprire appena creato **scene** cartella e quindi la *nome File*: campo di testo, digitare **MR_ComputerVisionScene**, quindi fare clic su **Salva** .</span><span class="sxs-lookup"><span data-stu-id="89e3f-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="89e3f-194">Tenere presente, è necessario salvare le scene di Unity all'interno di *asset* cartella, come devono essere associate al progetto di Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="89e3f-195">Creare la cartella scene (e altre simili) è un modo tipico strutturare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="89e3f-196">Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="89e3f-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="89e3f-197">Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.</span><span class="sxs-lookup"><span data-stu-id="89e3f-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="89e3f-198">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="89e3f-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="89e3f-199">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="89e3f-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="89e3f-200">**Scripting** **versione Runtime** deve essere **sperimentale** (.NET 4.6 equivalente), che attiverà una necessità di riavviare l'Editor.</span><span class="sxs-lookup"><span data-stu-id="89e3f-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="89e3f-201">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="89e3f-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="89e3f-202">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="89e3f-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="89e3f-203">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="89e3f-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="89e3f-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="89e3f-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="89e3f-205">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), controllare **supportato di realtà virtuale**, assicurarsi che il **realtà mista di Windows SDK** viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="89e3f-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="89e3f-206">Nuovamente in *Build Settings*, *Unity C# progetti* non è più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="89e3f-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="89e3f-207">Chiudi il *Build Settings* finestra.</span><span class="sxs-lookup"><span data-stu-id="89e3f-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="89e3f-208">Salvare la scena e il progetto (**FILE > Salva SCENE / FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="89e3f-208">Save your scene and project (**FILE > SAVE SCENES / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="89e3f-209">Capitolo 3 - librerie di importazione in Unity</span><span class="sxs-lookup"><span data-stu-id="89e3f-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89e3f-210">Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [MR-Azure-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importarlo nel progetto come un [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 5](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="89e3f-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="89e3f-211">Per usare *Microsoft Graph* all'interno di Unity è necessario apportare utilizzare il **Microsoft.Identity.Client** DLL.</span><span class="sxs-lookup"><span data-stu-id="89e3f-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="89e3f-212">È possibile usare il SDK di Microsoft Graph, tuttavia, sarà necessario l'aggiunta di un pacchetto NuGet dopo aver compilato il progetto di Unity (ovvero la post-compilazione del progetto di modifica).</span><span class="sxs-lookup"><span data-stu-id="89e3f-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="89e3f-213">Viene considerato più semplice importare le librerie DLL richieste direttamente in Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="89e3f-214">È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="89e3f-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="89e3f-215">Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.</span><span class="sxs-lookup"><span data-stu-id="89e3f-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="89e3f-216">Per importare *Microsoft Graph* nel progetto, [scaricare il file MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="89e3f-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="89e3f-217">Questo pacchetto è stato creato con le versioni delle librerie che sono state testate.</span><span class="sxs-lookup"><span data-stu-id="89e3f-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="89e3f-218">Se si vuole saperne di più su come aggiungere DLL personalizzata al progetto Unity [fare clic sul collegamento](https://docs.unity3d.com/Manual/UsingDLL.html).</span><span class="sxs-lookup"><span data-stu-id="89e3f-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="89e3f-219">Per importare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="89e3f-219">To import the package:</span></span>

1.  <span data-ttu-id="89e3f-220">Aggiungere il pacchetto Unity per Unity usando il **Assets* > *Importa pacchetto* > *pacchetto personalizzato** opzione di menu.</span><span class="sxs-lookup"><span data-stu-id="89e3f-220">Add the Unity Package to Unity by using the **Assets* > *Import Package* > *Custom Package** menu option.</span></span> <span data-ttu-id="89e3f-221">Selezionare il pacchetto che appena scaricato.</span><span class="sxs-lookup"><span data-stu-id="89e3f-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="89e3f-222">Nel **Importa pacchetto Unity** scatola viene, assicurarsi che tutto ciò che in (e tra cui) **plug-in** sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="89e3f-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="89e3f-223">Scegliere il **importazione** pulsante per aggiungere elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="89e3f-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="89e3f-224">Andare alla **Microsoft Graph** cartella sotto **plug-in** nel *pannello progetto* e selezionare il plug-in denominato **Microsoft.Identity.Client**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="89e3f-225">Con il *plug-in* selezionato, assicurarsi che **Any Platform** non è selezionata, quindi verificare che **WSAPlayer** anche è deselezionata, quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="89e3f-226">Si tratta semplicemente di confermare che i file siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="89e3f-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="89e3f-227">Contrassegnare questi plug-in Configura perché possano essere usati solo nell'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="89e3f-228">Esistono un diverso set di DLL nella cartella WSA che verrà usato dopo che il progetto viene esportato da Unity come un'applicazione di Windows universale.</span><span class="sxs-lookup"><span data-stu-id="89e3f-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="89e3f-229">Successivamente, è necessario aprire la **WSA** cartella, all'interno di **Microsoft Graph** cartella.</span><span class="sxs-lookup"><span data-stu-id="89e3f-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="89e3f-230">Si noterà una copia dello stesso file che appena configurato.</span><span class="sxs-lookup"><span data-stu-id="89e3f-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="89e3f-231">Selezionare il file, quindi nella finestra di ispezione:</span><span class="sxs-lookup"><span data-stu-id="89e3f-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="89e3f-232">Assicurarsi che **piattaforma Any** viene **deselezionata**e che **solo** **WSAPlayer** è **selezionata**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="89e3f-233">Assicurarsi **SDK** è impostata su **UWP**, e **back-end di Scripting** è impostata su **Dot Net**</span><span class="sxs-lookup"><span data-stu-id="89e3f-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="89e3f-234">Assicurarsi che **non elabora** viene **controllato**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="89e3f-235">Fare clic su **Applica**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="89e3f-236">Capitolo 4 - impostazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="89e3f-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="89e3f-237">Durante questo capitolo si configurerà la fotocamera principale della scena:</span><span class="sxs-lookup"><span data-stu-id="89e3f-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="89e3f-238">Nel *Pannello di gerarchia*, selezionare la **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="89e3f-239">Una volta selezionata, sarà possibile visualizzare tutti i componenti del **Main Camera** nel *Inspector* pannello.</span><span class="sxs-lookup"><span data-stu-id="89e3f-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="89e3f-240">Il **oggetto della fotocamera** devono essere denominati **Main Camera** (si noti l'ortografici!)</span><span class="sxs-lookup"><span data-stu-id="89e3f-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="89e3f-241">Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici!)</span><span class="sxs-lookup"><span data-stu-id="89e3f-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="89e3f-242">Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="89e3f-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="89e3f-243">Impostare **cancellare i flag** a **colore a tinta unita**</span><span class="sxs-lookup"><span data-stu-id="89e3f-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="89e3f-244">Impostare il **colore di sfondo** del componente della fotocamera **nero, Alpha 0** **(Hex codice: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="89e3f-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="89e3f-245">La struttura dell'oggetto finale nel *gerarchia pannello* dovrebbe essere simile a quello illustrato nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="89e3f-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="89e3f-246">Capitolo 5 - creare MeetingsUI classe</span><span class="sxs-lookup"><span data-stu-id="89e3f-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="89e3f-247">È il primo script da creare **MeetingsUI**, che è responsabile dell'hosting e popolando l'interfaccia utente dell'applicazione (messaggio di benvenuto, istruzioni e i dettagli di riunioni).</span><span class="sxs-lookup"><span data-stu-id="89e3f-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="89e3f-248">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="89e3f-248">To create this class:</span></span>

1.  <span data-ttu-id="89e3f-249">Fare clic sul **asset** cartella la *pannello progetto*, quindi selezionare \**crea* > \*cartella\*\*.</span><span class="sxs-lookup"><span data-stu-id="89e3f-249">Right-click on the **Assets** folder in the *Project Panel*, then select \**Create* > \*Folder\*\*.</span></span> <span data-ttu-id="89e3f-250">Denominare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="89e3f-251">Aprire il **gli script** cartella, quindi, all'interno di tale cartella, fare doppio clic su, \**Create* > \*C\# Script\*\*.</span><span class="sxs-lookup"><span data-stu-id="89e3f-251">Open the **Scripts** folder then, within that folder, right-click, \**Create* > \*C\# Script\*\*.</span></span> <span data-ttu-id="89e3f-252">Denominare lo script **MeetingsUI.**</span><span class="sxs-lookup"><span data-stu-id="89e3f-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="89e3f-253">Fare doppio clic su nuova **MeetingsUI** script per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="89e3f-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="89e3f-254">Inserisci gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="89e3f-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="89e3f-255">All'interno della classe inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="89e3f-255">Inside the class insert the following variables:</span></span>

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

6.  <span data-ttu-id="89e3f-256">Quindi sostituire il **Start ()** metodo e aggiungere un' **Awake()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="89e3f-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="89e3f-257">Questi verranno chiamati quando inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="89e3f-257">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="89e3f-258">Aggiungere i metodi responsabili per la creazione di *riunioni UI* e popolarla con le riunioni corrente quando richiesto:</span><span class="sxs-lookup"><span data-stu-id="89e3f-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

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

8. <span data-ttu-id="89e3f-259">**Eliminare** il **Update ()** metodo, e **salvare le modifiche** in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="89e3f-260">Capitolo 6: creare la classe di Graph</span><span class="sxs-lookup"><span data-stu-id="89e3f-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="89e3f-261">Lo script successivo da creare è il **Graph** script.</span><span class="sxs-lookup"><span data-stu-id="89e3f-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="89e3f-262">Questo script è responsabile di rendere le chiamate per autenticare l'utente e recuperare le riunioni pianificate per il giorno corrente dal calendario dell'utente.</span><span class="sxs-lookup"><span data-stu-id="89e3f-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="89e3f-263">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="89e3f-263">To create this class:</span></span>

1.  <span data-ttu-id="89e3f-264">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="89e3f-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="89e3f-265">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="89e3f-266">Denominare lo script **Graph**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="89e3f-267">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89e3f-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="89e3f-268">Inserisci gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="89e3f-268">Insert the following namespaces:</span></span>

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
    > <span data-ttu-id="89e3f-269">Si noterà che le parti del codice in questo script vengono eseguito il wrapping intorno [precompilare le direttive](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), questo serve a evitare problemi con le librerie quando si compila la soluzione Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89e3f-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="89e3f-270">Eliminare il **Start ()** e **Update ()** metodi, poiché essi non verrà utilizzati.</span><span class="sxs-lookup"><span data-stu-id="89e3f-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="89e3f-271">Di fuori di **Graph** classe, inserire gli oggetti seguenti, che sono necessari per deserializzare l'oggetto JSON che rappresenta le riunioni pianificate giornaliere:</span><span class="sxs-lookup"><span data-stu-id="89e3f-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

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

7.  <span data-ttu-id="89e3f-272">All'interno di **Graph** classe, aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="89e3f-272">Inside the **Graph** class, add the following variables:</span></span>

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
    > <span data-ttu-id="89e3f-273">Modifica il **appId** valore sia il **App Id** annotato nella  **[capitolo 1](#chapter-1---create-your-app-in-the-application-registration-portal), passaggio 4**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="89e3f-274">Questo valore deve essere uguale a quello visualizzato nei **portale di registrazione delle applicazioni,** nella pagina di registrazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="89e3f-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="89e3f-275">All'interno di **Graph** classe, aggiungere i metodi **SignInAsync()** e **AquireTokenAsync()**, che chiederà all'utente di inserire le credenziali di log.</span><span class="sxs-lookup"><span data-stu-id="89e3f-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

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

9.  <span data-ttu-id="89e3f-276">Aggiungere i due metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="89e3f-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="89e3f-277">**BuildTodayCalendarEndpoint()**, che si basa l'URI che specifica il giorno e intervallo di tempo, in cui vengono recuperate le riunioni pianificate.</span><span class="sxs-lookup"><span data-stu-id="89e3f-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="89e3f-278">**ListMeetingsAsync()**, che richiede le riunioni pianificate da *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="89e3f-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

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

10. <span data-ttu-id="89e3f-279">È stata completata la **Graph** script.</span><span class="sxs-lookup"><span data-stu-id="89e3f-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="89e3f-280">**Salvare le modifiche** in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="89e3f-281">Capitolo 7 - creare uno script di GazeInput</span><span class="sxs-lookup"><span data-stu-id="89e3f-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="89e3f-282">Ora si creerà il **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="89e3f-283">Questa classe gestisce e tiene traccia di sguardo dell'utente, utilizzando un **Raycast** provenienti dalle **Main Camera**, la proiezione in avanti.</span><span class="sxs-lookup"><span data-stu-id="89e3f-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="89e3f-284">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="89e3f-284">To create the script:</span></span>

1.  <span data-ttu-id="89e3f-285">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="89e3f-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="89e3f-286">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="89e3f-287">Denominare lo script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="89e3f-288">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89e3f-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="89e3f-289">Modificare il codice degli spazi dei nomi in modo che corrisponda a quello riportato di seguito, con l'aggiunta di '**\[System.Serializable\]**' tag sopra il **GazeInput** classe, in modo che possa essere serializzato:</span><span class="sxs-lookup"><span data-stu-id="89e3f-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="89e3f-290">All'interno di **GazeInput** classe, aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="89e3f-290">Inside the **GazeInput** class, add the following variables:</span></span>

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

6.  <span data-ttu-id="89e3f-291">Aggiungere il **CreateCursor()** per creare il cursore di HoloLens nella scena e chiamare il metodo dalle **Start ()** metodo:</span><span class="sxs-lookup"><span data-stu-id="89e3f-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

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

7.  <span data-ttu-id="89e3f-292">I metodi seguenti abilitare sguardo Raycast e tenere traccia degli oggetti con lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="89e3f-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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

8.  <span data-ttu-id="89e3f-293">**Salvare le modifiche** in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="89e3f-294">Capitolo 8 - creare la classe interazioni</span><span class="sxs-lookup"><span data-stu-id="89e3f-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="89e3f-295">È ora necessario creare il **interazioni** script, che è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="89e3f-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="89e3f-296">La gestione di **toccare** interazione e il **fotocamera estasiati**, che consente all'utente di interagire con i log in "button" nella scena.</span><span class="sxs-lookup"><span data-stu-id="89e3f-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="89e3f-297">Creazione del log nell'oggetto "button" nella scena per l'utente può interagire.</span><span class="sxs-lookup"><span data-stu-id="89e3f-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="89e3f-298">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="89e3f-298">To create the script:</span></span>

1.  <span data-ttu-id="89e3f-299">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="89e3f-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="89e3f-300">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="89e3f-301">Denominare lo script **interazioni**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="89e3f-302">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89e3f-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="89e3f-303">Inserisci gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="89e3f-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="89e3f-304">Modificare l'ereditarietà del **interazione** classe *MonoBehaviour* al **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="89e3f-305">~~classe pubblica le interazioni: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="89e3f-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="89e3f-306">All'interno di **interazione** classe inserire la variabile seguente:</span><span class="sxs-lookup"><span data-stu-id="89e3f-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="89e3f-307">Sostituire il **avviare** metodo; si noti che è un metodo di override, che chiama il metodo della classe sguardo 'base'.</span><span class="sxs-lookup"><span data-stu-id="89e3f-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="89e3f-308">**Start ()** verrà chiamato quando si inizializza la classe, la registrazione per il riconoscimento di input e la creazione di accesso *pulsante* nella scena:</span><span class="sxs-lookup"><span data-stu-id="89e3f-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

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

8.  <span data-ttu-id="89e3f-309">Aggiungere il **CreateSignInButton()** metodo, che verrà creata un'istanza di accesso *pulsante* nella scena e impostarne le proprietà:</span><span class="sxs-lookup"><span data-stu-id="89e3f-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

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

9.  <span data-ttu-id="89e3f-310">Aggiungere il **GestureRecognizer_Tapped()** metodo, che è possibile rispondere per il *toccare* evento utente.</span><span class="sxs-lookup"><span data-stu-id="89e3f-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

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

10. <span data-ttu-id="89e3f-311">**Eliminare** il **Update ()** metodo e quindi **salvare le modifiche** in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="89e3f-312">Capitolo 9: configurare i riferimenti a script</span><span class="sxs-lookup"><span data-stu-id="89e3f-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="89e3f-313">In questo capitolo è necessario inserire il **interazioni** nello script le **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="89e3f-314">Lo script gestirà quindi l'inserimento altri script in cui devono essere.</span><span class="sxs-lookup"><span data-stu-id="89e3f-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="89e3f-315">Dal **script** cartella il *pannello progetto*, trascinare lo script **interazioni** per il **Main Camera** dell'oggetto, come illustrata di seguito.</span><span class="sxs-lookup"><span data-stu-id="89e3f-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="89e3f-316">Capitolo 10 - configurare i Tag</span><span class="sxs-lookup"><span data-stu-id="89e3f-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="89e3f-317">Il codice che gestisce lo sguardo useranno il Tag **SignInButton** per identificare l'oggetto con cui interagirà l'utente con effettuare l'accesso per *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="89e3f-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="89e3f-318">Per creare il Tag:</span><span class="sxs-lookup"><span data-stu-id="89e3f-318">To create the Tag:</span></span>

1.  <span data-ttu-id="89e3f-319">Nell'Editor di Unity fare clic sui **Main Camera** nel *gerarchia pannello*.</span><span class="sxs-lookup"><span data-stu-id="89e3f-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="89e3f-320">Nel *Pannello di controllo* fare clic sulla **MainCamera** *Tag* per aprire un elenco a discesa.</span><span class="sxs-lookup"><span data-stu-id="89e3f-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="89e3f-321">Fare clic su **aggiungere Tag...**</span><span class="sxs-lookup"><span data-stu-id="89e3f-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="89e3f-322">Fare clic sui **+** pulsante.</span><span class="sxs-lookup"><span data-stu-id="89e3f-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="89e3f-323">Scrivere il nome del Tag come **SignInButton** e fare clic su Salva.</span><span class="sxs-lookup"><span data-stu-id="89e3f-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="89e3f-324">Capitolo 11 - compilare il progetto di Unity per UWP</span><span class="sxs-lookup"><span data-stu-id="89e3f-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="89e3f-325">Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.</span><span class="sxs-lookup"><span data-stu-id="89e3f-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="89e3f-326">Passare a *impostazioni di compilazione* (\**File* > \*Impostazioni di compilazione\*\*).</span><span class="sxs-lookup"><span data-stu-id="89e3f-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="89e3f-327">Se non è già, graduazione **C Unity\# progetti**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="89e3f-328">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-328">Click **Build**.</span></span> <span data-ttu-id="89e3f-329">Unity avvierà una **Esplora File** finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in.</span><span class="sxs-lookup"><span data-stu-id="89e3f-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="89e3f-330">Creare ora tale cartella e denominarlo **App**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="89e3f-331">Quindi con il **App** cartella selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="89e3f-332">Unity verrà avviata la compilazione del progetto per la **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="89e3f-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="89e3f-333">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).</span><span class="sxs-lookup"><span data-stu-id="89e3f-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="89e3f-334">Capitolo 12 - distribuire a HoloLens</span><span class="sxs-lookup"><span data-stu-id="89e3f-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="89e3f-335">Per distribuire in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="89e3f-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="89e3f-336">È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore.**</span><span class="sxs-lookup"><span data-stu-id="89e3f-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="89e3f-337">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="89e3f-337">To do this:</span></span>

    1.  <span data-ttu-id="89e3f-338">Durante l'uso di HoloLens, aprire il **impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="89e3f-339">Passare a **rete e Internet** > **Wi-Fi** > **opzioni avanzate**</span><span class="sxs-lookup"><span data-stu-id="89e3f-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="89e3f-340">Si noti il **IPv4** indirizzo.</span><span class="sxs-lookup"><span data-stu-id="89e3f-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="89e3f-341">Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza** > **per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="89e3f-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="89e3f-342">Impostare **modalità sviluppatore su**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="89e3f-343">Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="89e3f-344">Nel **configurazione della soluzione** selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="89e3f-345">Nel **piattaforma soluzione**, selezionare **x86, computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="89e3f-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="89e3f-346">Verrà richiesto di inserire le **indirizzo IP** di un dispositivo remoto (il HoloLens, in questo caso, che si è preso nota).</span><span class="sxs-lookup"><span data-stu-id="89e3f-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="89e3f-347">Passare a **compilare** dal menu e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="89e3f-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="89e3f-348">L'app deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="89e3f-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="89e3f-349">L'applicazione di Microsoft Graph HoloLens</span><span class="sxs-lookup"><span data-stu-id="89e3f-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="89e3f-350">Complimenti, è stata compilata un'app per realtà mista che si basa su Microsoft Graph, per leggere e visualizzare i dati del calendario di utente.</span><span class="sxs-lookup"><span data-stu-id="89e3f-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="89e3f-351">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="89e3f-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="89e3f-352">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="89e3f-352">Exercise 1</span></span>

<span data-ttu-id="89e3f-353">Usare Microsoft Graph per visualizzare altre informazioni sull'utente</span><span class="sxs-lookup"><span data-stu-id="89e3f-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="89e3f-354">Messaggio di posta elettronica utente / numero di telefono / immagine del profilo</span><span class="sxs-lookup"><span data-stu-id="89e3f-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="89e3f-355">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="89e3f-355">Exercise 1</span></span>

<span data-ttu-id="89e3f-356">Implementare il controllo di casella vocale per passare l'interfaccia utente di Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="89e3f-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
