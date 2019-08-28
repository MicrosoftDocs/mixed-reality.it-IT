---
title: Integrazione di MR e Azure 312-bot
description: Completare questo corso per apprendere come creare e distribuire un bot, usando Microsoft bot Framework V4 e comunicare con esso in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, visione artificiale, hololens, immersiva, VR, Microsoft bot Framework V4, bot per app Web, bot Framework, Microsoft bot
ms.openlocfilehash: 481693b5af8c946e1cb45dda5144e78a175fa771
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047235"
---
>[!NOTE]
><span data-ttu-id="79cc7-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="79cc7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="79cc7-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="79cc7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="79cc7-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79cc7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="79cc7-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="79cc7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="79cc7-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79cc7-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="79cc7-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="79cc7-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="79cc7-110">MR e Azure 312: Integrazione bot</span><span class="sxs-lookup"><span data-stu-id="79cc7-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="79cc7-111">In questo corso si apprenderà come creare e distribuire un bot con Microsoft bot Framework V4 e come comunicare con esso tramite un'applicazione di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="79cc7-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="79cc7-112">**Microsoft bot Framework V4** è un set di API progettate per fornire agli sviluppatori gli strumenti necessari per creare un'applicazione bot estensibile e scalabile.</span><span class="sxs-lookup"><span data-stu-id="79cc7-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="79cc7-113">Per ulteriori informazioni, visitare la [pagina Microsoft bot Framework](https://dev.botframework.com/) o il [repository git V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="79cc7-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="79cc7-114">Al termine di questo corso, sarà stata compilata un'applicazione di realtà mista di Windows, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="79cc7-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="79cc7-115">Usare un **movimento Tap** per avviare il bot in ascolto per la voce degli utenti.</span><span class="sxs-lookup"><span data-stu-id="79cc7-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="79cc7-116">Quando l'utente ha detto qualcosa, il bot tenterà di fornire una risposta.</span><span class="sxs-lookup"><span data-stu-id="79cc7-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="79cc7-117">Visualizza la risposta dei bot come testo, posizionata vicino al bot, nella scena Unity.</span><span class="sxs-lookup"><span data-stu-id="79cc7-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="79cc7-118">Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="79cc7-119">Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="79cc7-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="79cc7-120">Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.</span><span class="sxs-lookup"><span data-stu-id="79cc7-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="79cc7-121">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="79cc7-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="79cc7-122">Corso</span><span class="sxs-lookup"><span data-stu-id="79cc7-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="79cc7-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="79cc7-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="79cc7-124"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="79cc7-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="79cc7-125">MR e Azure 312: Integrazione bot</span><span class="sxs-lookup"><span data-stu-id="79cc7-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="79cc7-126">✔️</span><span class="sxs-lookup"><span data-stu-id="79cc7-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="79cc7-127">✔️</span><span class="sxs-lookup"><span data-stu-id="79cc7-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="79cc7-128">Sebbene questo corso sia incentrato principalmente su HoloLens, è anche possibile applicare le informazioni apprese in questo corso agli auricolari per la realtà mista (VR) di Windows.</span><span class="sxs-lookup"><span data-stu-id="79cc7-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="79cc7-129">Poiché le cuffie immersive (VR) non hanno fotocamere accessibili, sarà necessaria una fotocamera esterna connessa al PC.</span><span class="sxs-lookup"><span data-stu-id="79cc7-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="79cc7-130">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare gli auricolari immersivi (VR).</span><span class="sxs-lookup"><span data-stu-id="79cc7-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79cc7-131">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="79cc7-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="79cc7-132">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="79cc7-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="79cc7-133">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="79cc7-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="79cc7-134">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="79cc7-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="79cc7-135">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="79cc7-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="79cc7-136">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="79cc7-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="79cc7-137">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="79cc7-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79cc7-138">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="79cc7-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79cc7-139">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="79cc7-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="79cc7-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="79cc7-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="79cc7-141">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="79cc7-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="79cc7-142">Accesso a Internet per Azure e per il recupero di bot di Azure.</span><span class="sxs-lookup"><span data-stu-id="79cc7-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="79cc7-143">Per ulteriori informazioni, [seguire questo collegamento](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="79cc7-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="79cc7-144">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="79cc7-144">Before you start</span></span>

1.  <span data-ttu-id="79cc7-145">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="79cc7-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="79cc7-146">Configurare e testare il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79cc7-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="79cc7-147">Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="79cc7-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="79cc7-148">Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="79cc7-149">Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="79cc7-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="79cc7-150">Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="79cc7-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="79cc7-151">Capitolo 1-creare l'applicazione bot</span><span class="sxs-lookup"><span data-stu-id="79cc7-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="79cc7-152">Il primo passaggio consiste nel creare il bot come applicazione Web ASP.Net Core locale.</span><span class="sxs-lookup"><span data-stu-id="79cc7-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="79cc7-153">Una volta completato e testato, sarà possibile pubblicarlo nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="79cc7-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="79cc7-154">Aprire Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-154">Open Visual Studio.</span></span> <span data-ttu-id="79cc7-155">Creare un nuovo progetto, selezionare **applicazione Web ASP NET Core** come tipo di progetto (sarà presente nella sottosezione .NET Core) e denominarlo **MyBot**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="79cc7-156">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-156">Click **OK**.</span></span>

2.  <span data-ttu-id="79cc7-157">Nella finestra che verrà visualizzata selezionare **vuoto**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="79cc7-158">Assicurarsi anche che la destinazione sia impostata su **ASP NET Core 2,0** e che l'autenticazione sia impostata su **Nessuna autenticazione**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="79cc7-159">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-159">Click **OK**.</span></span>  

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="79cc7-161">La soluzione verrà aperta.</span><span class="sxs-lookup"><span data-stu-id="79cc7-161">The solution will now open.</span></span> <span data-ttu-id="79cc7-162">Fare clic con il pulsante destro del mouse su soluzione **Mybot** nel **Esplora soluzioni** e fare clic su **Gestisci pacchetti NuGet per la soluzione**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="79cc7-164">Nella scheda **Sfoglia** cercare **Microsoft. bot. Builder. Integration. AspNet. Core** (assicurarsi di **includere la versione non definitiva** selezionata).</span><span class="sxs-lookup"><span data-stu-id="79cc7-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="79cc7-165">Selezionare la versione del pacchetto **4.0.1-Preview**e selezionare le caselle di progetto.</span><span class="sxs-lookup"><span data-stu-id="79cc7-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="79cc7-166">Quindi fare clic su **Installa**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-166">Then click on **Install**.</span></span> <span data-ttu-id="79cc7-167">Sono ora installate le librerie necessarie per **bot Framework V4**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="79cc7-168">Chiudere la pagina NuGet.</span><span class="sxs-lookup"><span data-stu-id="79cc7-168">Close the NuGet page.</span></span>

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="79cc7-170">Fare clic con il pulsante destro del mouse sul *progetto*, **MyBot**, nella **Esplora soluzioni** e fare clic su **Aggiungi** **|** **classe**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="79cc7-172">Assegnare alla classe il nome **MyBot** e fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="79cc7-174">Ripetere il punto precedente per creare un'altra classe denominata **ConversationContext**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="79cc7-175">Fare clic con il pulsante destro del mouse su **wwwroot** nel **Esplora soluzioni** e fare clic su **Aggiungi** **|** **nuovo elemento**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="79cc7-176">Selezionare la **pagina HTML** (si troverà nella sottosezione Web).</span><span class="sxs-lookup"><span data-stu-id="79cc7-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="79cc7-177">Denominare il file **default. html**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-177">Name the file **default.html**.</span></span> <span data-ttu-id="79cc7-178">Fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-178">Click **Add**.</span></span>

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="79cc7-180">L'elenco di classi/oggetti nel **Esplora soluzioni** dovrebbe essere simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="79cc7-182">Fare doppio clic sulla classe **ConversationContext** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="79cc7-183">Questa classe è responsabile della conservazione delle variabili usate dal bot per mantenere il contesto della conversazione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="79cc7-184">Questi valori del contesto di conversazione vengono mantenuti in un'istanza di questa classe, perché ogni istanza della classe **MyBot** verrà aggiornata ogni volta che viene ricevuta un'attività.</span><span class="sxs-lookup"><span data-stu-id="79cc7-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="79cc7-185">Aggiungere il codice seguente alla classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="79cc7-186">Fare doppio clic sulla classe **MyBot** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="79cc7-187">Questa classe ospiterà i gestori chiamati da qualsiasi attività in ingresso dal cliente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="79cc7-188">In questa classe verrà aggiunto il codice usato per compilare la conversazione tra il bot e il cliente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="79cc7-189">Come indicato in precedenza, un'istanza di questa classe viene inizializzata ogni volta che viene ricevuta un'attività.</span><span class="sxs-lookup"><span data-stu-id="79cc7-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="79cc7-190">Aggiungere il codice seguente a questa classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="79cc7-191">Fare doppio clic sulla classe **Startup** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="79cc7-192">Questa classe inizializza il bot.</span><span class="sxs-lookup"><span data-stu-id="79cc7-192">This class will initialize the bot.</span></span> <span data-ttu-id="79cc7-193">Aggiungere il codice seguente alla classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="79cc7-194">Aprire il file della classe **Program** e verificare che il codice sia uguale a quello riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="79cc7-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="79cc7-195">Ricordarsi di salvare le modifiche. a tale scopo, passare a **file** > **Salva tutto**, dalla barra degli strumenti nella parte superiore di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="79cc7-196">Capitolo 2: creare il servizio Azure bot</span><span class="sxs-lookup"><span data-stu-id="79cc7-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="79cc7-197">Ora che è stato compilato il codice per il bot, è necessario pubblicarlo in un'istanza del servizio *bot app Web* nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="79cc7-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="79cc7-198">In questo capitolo viene illustrato come creare e configurare il servizio bot in Azure e quindi come pubblicarvi il codice.</span><span class="sxs-lookup"><span data-stu-id="79cc7-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="79cc7-199">Per prima cosa, accedere al portale di Azure https://portal.azure.com) (.</span><span class="sxs-lookup"><span data-stu-id="79cc7-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="79cc7-200">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="79cc7-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="79cc7-201">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="79cc7-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="79cc7-202">Una volta effettuato l'accesso, fare clic su **Crea una risorsa** nell'angolo in alto a sinistra e cercare *bot app Web*e premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="79cc7-204">La nuova pagina fornirà una descrizione del servizio *bot per app Web* .</span><span class="sxs-lookup"><span data-stu-id="79cc7-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="79cc7-205">Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="79cc7-207">Una volta fatto clic su **Crea**:</span><span class="sxs-lookup"><span data-stu-id="79cc7-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="79cc7-208">Inserire il **nome** desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="79cc7-209">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="79cc7-210">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="79cc7-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79cc7-211">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="79cc7-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="79cc7-212">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="79cc7-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="79cc7-213">Per altre informazioni sui gruppi di risorse di Azure, vedere [il collegamento](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) seguente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="79cc7-214">Determinare il percorso del gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="79cc7-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="79cc7-215">Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="79cc7-216">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="79cc7-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="79cc7-217">Selezionare il piano tariffario appropriato. se è la prima volta che si crea un servizio *bot app Web* , è necessario che sia disponibile un livello gratuito (denominato F0)</span><span class="sxs-lookup"><span data-stu-id="79cc7-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="79cc7-218">Il **nome dell'app** può essere semplicemente lasciato lo stesso *nome del bot*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="79cc7-219">Lasciare il *modello bot* come **Basic (C#)** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="79cc7-220">Il *piano/percorso di servizio app* deve essere stato compilato automaticamente per l'account.</span><span class="sxs-lookup"><span data-stu-id="79cc7-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="79cc7-221">Impostare l' **archiviazione di Azure** che si vuole usare per ospitare il bot.</span><span class="sxs-lookup"><span data-stu-id="79cc7-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="79cc7-222">Se non ne è già disponibile uno, è possibile crearlo qui.</span><span class="sxs-lookup"><span data-stu-id="79cc7-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="79cc7-223">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="79cc7-224">Fare clic su Crea.</span><span class="sxs-lookup"><span data-stu-id="79cc7-224">Click Create.</span></span>
 
        ![Creare il servizio Azure bot](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="79cc7-226">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="79cc7-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="79cc7-227">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="79cc7-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="79cc7-229">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="79cc7-231">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="79cc7-232">Si verrà portati alla nuova istanza del servizio Azure.</span><span class="sxs-lookup"><span data-stu-id="79cc7-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="79cc7-234">A questo punto è necessario configurare una funzionalità denominata **Direct Line** per consentire all'applicazione client di comunicare con questo servizio bot.</span><span class="sxs-lookup"><span data-stu-id="79cc7-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="79cc7-235">Fare clic su **canali**, quindi nella sezione **Aggiungi un canale in primo piano** fare clic su **Configura canale linea diretta**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="79cc7-237">In questa pagina sono disponibili le **chiavi segrete** che consentiranno all'app client di eseguire l'autenticazione con il bot.</span><span class="sxs-lookup"><span data-stu-id="79cc7-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="79cc7-238">Fare clic sul pulsante **Mostra** per eseguire una copia di una delle chiavi visualizzate, perché sarà necessario in un secondo momento nel progetto.</span><span class="sxs-lookup"><span data-stu-id="79cc7-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="79cc7-240">Capitolo 3: pubblicare il bot nel servizio bot app Web di Azure</span><span class="sxs-lookup"><span data-stu-id="79cc7-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="79cc7-241">Ora che il servizio è pronto, è necessario pubblicare il codice bot, che è stato compilato in precedenza, per il servizio bot app Web appena creato.</span><span class="sxs-lookup"><span data-stu-id="79cc7-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="79cc7-242">Sarà necessario pubblicare il bot nel servizio di Azure ogni volta che si apportano modifiche al codice o alla soluzione bot.</span><span class="sxs-lookup"><span data-stu-id="79cc7-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="79cc7-243">Tornare alla soluzione di Visual Studio creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79cc7-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="79cc7-244">Fare clic con il pulsante destro del mouse sul progetto **MyBot** , nel **Esplora soluzioni**, quindi fare clic su **pubblica**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Pubblicare il bot nel servizio bot app Web di Azure](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="79cc7-246">Nella pagina *selezionare una destinazione di pubblicazione* fare clic su **servizio app**, quindi **selezionare esistente**, infine fare clic su **Crea profilo** . se non è visibile, potrebbe essere necessario fare clic sulla freccia a discesa insieme al pulsante *pubblica* .</span><span class="sxs-lookup"><span data-stu-id="79cc7-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Pubblicare il bot nel servizio bot app Web di Azure](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="79cc7-248">Se non si è ancora connessi all'account Microsoft, è necessario eseguire questa operazione qui.</span><span class="sxs-lookup"><span data-stu-id="79cc7-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="79cc7-249">Nella pagina **pubblica** si noterà che è necessario impostare la stessa **sottoscrizione** usata per la creazione del servizio *bot per app Web* .</span><span class="sxs-lookup"><span data-stu-id="79cc7-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="79cc7-250">Impostare quindi la **vista** come **gruppo di risorse** e nella struttura di cartelle a discesa selezionare il **gruppo di risorse** creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79cc7-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="79cc7-251">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-251">Click **OK**.</span></span> 

    ![Pubblicare il bot nel servizio bot app Web di Azure](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="79cc7-253">A questo punto fare clic sul pulsante **pubblica** e attendere che il bot venga pubblicato. potrebbero essere necessari alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="79cc7-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Pubblicare il bot nel servizio bot app Web di Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="79cc7-255">Capitolo 4: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="79cc7-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="79cc7-256">Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="79cc7-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="79cc7-257">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-257">Open *Unity* and click **New**.</span></span> 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="79cc7-259">A questo punto sarà necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="79cc7-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="79cc7-260">Inserire il **bot Hololens**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="79cc7-261">Verificare che il modello di progetto sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="79cc7-262">Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="79cc7-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="79cc7-263">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-263">Then, click **Create project**.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="79cc7-265">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="79cc7-266">Passare a **Modifica preferenze >** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="79cc7-267">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="79cc7-268">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-268">Close the **Preferences** window.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="79cc7-270">Passare quindi a **File > impostazioni di compilazione** e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="79cc7-272">Sempre in **File > impostazioni di compilazione** e verificare che:</span><span class="sxs-lookup"><span data-stu-id="79cc7-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="79cc7-273">Il **dispositivo di destinazione** è impostato su **Hololens**</span><span class="sxs-lookup"><span data-stu-id="79cc7-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="79cc7-274">Per gli auricolari immersivi, impostare **dispositivo di destinazione** su *qualsiasi dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="79cc7-275">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="79cc7-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="79cc7-276">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="79cc7-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="79cc7-277">La **versione di Visual Studio** è impostata su **installazione più recente**</span><span class="sxs-lookup"><span data-stu-id="79cc7-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="79cc7-278">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="79cc7-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="79cc7-279">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="79cc7-280">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="79cc7-281">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="79cc7-281">A save window will appear.</span></span>
        
            ![Configurare il progetto Unity](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="79cc7-283">Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella, assegnarle un nome.</span><span class="sxs-lookup"><span data-stu-id="79cc7-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Configurare il progetto Unity](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="79cc7-285">Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **BotScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="79cc7-287">Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="79cc7-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="79cc7-288">Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .</span><span class="sxs-lookup"><span data-stu-id="79cc7-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="79cc7-290">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="79cc7-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="79cc7-291">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="79cc7-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="79cc7-292">La **versione di runtime** di scripting deve essere **sperimentale (equivalente alla rete 4,6)** ; per modificare questa operazione, è necessario riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="79cc7-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="79cc7-293">Il **back-end** di scripting deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="79cc7-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="79cc7-294">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="79cc7-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="79cc7-296">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="79cc7-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="79cc7-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="79cc7-297">**InternetClient**</span></span>
        - <span data-ttu-id="79cc7-298">**Microfono**</span><span class="sxs-lookup"><span data-stu-id="79cc7-298">**Microphone**</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="79cc7-300">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurare il progetto Unity](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="79cc7-302">Nelle *impostazioni di compilazione* i progetti _Unity C#_  non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="79cc7-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="79cc7-303">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="79cc7-304">Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="79cc7-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="79cc7-305">Capitolo 5-configurazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="79cc7-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79cc7-306">Se si vuole ignorare il componente di *configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricare questo [Azure-Mr-312-Package. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare da [ Capitolo 7](#chapter-8--create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="79cc7-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-8--create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="79cc7-307">Nel *Pannello gerarchia*selezionare la **fotocamera principale**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="79cc7-308">Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="79cc7-309">L' **oggetto fotocamera** deve essere denominato **Main camera** (nota l'ortografia)</span><span class="sxs-lookup"><span data-stu-id="79cc7-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="79cc7-310">Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (annotare l'ortografia)</span><span class="sxs-lookup"><span data-stu-id="79cc7-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="79cc7-311">Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="79cc7-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="79cc7-312">Impostare **Cancella flag** su **colore a tinta unita**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="79cc7-313">Imposta il colore di **sfondo** del componente della fotocamera su **nero, alfa 0 (codice esadecimale: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="79cc7-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![Configurazione della fotocamera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="79cc7-315">Capitolo 6: importare la libreria Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="79cc7-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="79cc7-316">Per semplificare la deserializzazione e la serializzazione degli oggetti ricevuti e inviati al servizio bot, è necessario scaricare la libreria **Newtonsoft** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="79cc7-317">È disponibile una [versione compatibile già organizzata con la struttura di cartelle Unity corretta](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="79cc7-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="79cc7-318">Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornito con questo corso.</span><span class="sxs-lookup"><span data-stu-id="79cc7-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="79cc7-319">Aggiungere il *file unitypackage Tools* a Unity usando l'opzione di menu **Asset** > **Import Package** > **Custom Package** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Importare la libreria Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="79cc7-321">Nella casella **Importa pacchetto Unity** visualizzata verificare che siano selezionati tutti gli elementi in (e inclusi) **plug** -in.</span><span class="sxs-lookup"><span data-stu-id="79cc7-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importare la libreria Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="79cc7-323">Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="79cc7-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="79cc7-324">Passare alla cartella **Newtonsoft** in **plug** -in nella visualizzazione del progetto e selezionare il plug-in Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="79cc7-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="79cc7-325">Con il plug-in Newtonsoft selezionato, verificare che **qualsiasi piattaforma** sia deselezionata, quindi verificare che **WSAPlayer** sia deselezionata, quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="79cc7-326">Questa operazione è sufficiente per verificare che i file siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="79cc7-327">Contrassegnando questi plug-in, questi vengono configurati per essere usati solo nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="79cc7-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="79cc7-328">Nella cartella WSA è presente un set diverso che verrà usato dopo l'esportazione del progetto da Unity.</span><span class="sxs-lookup"><span data-stu-id="79cc7-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="79cc7-329">Successivamente, è necessario aprire la cartella **WSA** , all'interno della cartella **Newtonsoft** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="79cc7-330">Viene visualizzata una copia dello stesso file appena configurato.</span><span class="sxs-lookup"><span data-stu-id="79cc7-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="79cc7-331">Selezionare il file e quindi nel controllo verificare che</span><span class="sxs-lookup"><span data-stu-id="79cc7-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="79cc7-332">**Qualsiasi piattaforma** è deselezionata</span><span class="sxs-lookup"><span data-stu-id="79cc7-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="79cc7-333">**solo** **WSAPlayer** è **selezionato**</span><span class="sxs-lookup"><span data-stu-id="79cc7-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="79cc7-334">Il **processo** non è **selezionato**</span><span class="sxs-lookup"><span data-stu-id="79cc7-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="79cc7-335">Capitolo 7: creare il BotTag</span><span class="sxs-lookup"><span data-stu-id="79cc7-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="79cc7-336">Creare un nuovo oggetto **tag** denominato **BotTag**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="79cc7-337">Selezionare la fotocamera principale nella scena.</span><span class="sxs-lookup"><span data-stu-id="79cc7-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="79cc7-338">Fare clic sul menu a discesa Tag nel pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="79cc7-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="79cc7-339">Fare clic su **Aggiungi tag**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-339">Click on **Add Tag**.</span></span>

    ![Configurazione della fotocamera](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="79cc7-341">Fare clic sul **+** simbolo.</span><span class="sxs-lookup"><span data-stu-id="79cc7-341">Click on the **+** symbol.</span></span> <span data-ttu-id="79cc7-342">Denominare il nuovo **tag** come **BotTag**, *Save*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![Configurazione della fotocamera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="79cc7-344">Non applicare **BotTag** alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="79cc7-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="79cc7-345">Se questa operazione è stata eseguita accidentalmente, assicurarsi di modificare di nuovo il tag della fotocamera principale in *MainCamera*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="79cc7-346">Capitolo 8: creare la classe BotObjects</span><span class="sxs-lookup"><span data-stu-id="79cc7-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="79cc7-347">Il primo script che è necessario creare è la classe **BotObjects** , che è una classe vuota creata in modo che una serie di altri oggetti classe possa essere archiviata nello stesso script e accessibile da altri script nella scena.</span><span class="sxs-lookup"><span data-stu-id="79cc7-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="79cc7-348">La creazione di questa classe è puramente una scelta di architettura. questi oggetti possono invece essere ospitati nello script bot che verrà creato più avanti in questo corso.</span><span class="sxs-lookup"><span data-stu-id="79cc7-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="79cc7-349">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-349">To create this class:</span></span> 

1.  <span data-ttu-id="79cc7-350">Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare > cartella**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="79cc7-351">Denominare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="79cc7-351">Name the folder **Scripts**.</span></span> 

    ![Crea cartella script.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="79cc7-353">Fare doppio clic sulla cartella **script** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="79cc7-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="79cc7-354">Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse e scegliere **crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="79cc7-355">Denominare lo script **BotObjects**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="79cc7-356">Fare doppio clic sul nuovo script **BotObjects** per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="79cc7-357">Eliminare il contenuto dello script e sostituirlo con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="79cc7-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="79cc7-358">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="79cc7-359">Capitolo 9: creare la classe GazeInput</span><span class="sxs-lookup"><span data-stu-id="79cc7-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="79cc7-360">La classe successiva che si intende creare è la classe **GazeInput** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="79cc7-361">Questa classe è responsabile di:</span><span class="sxs-lookup"><span data-stu-id="79cc7-361">This class is responsible for:</span></span>

- <span data-ttu-id="79cc7-362">Creazione di un cursore che rappresenterà lo *sguardo* del lettore.</span><span class="sxs-lookup"><span data-stu-id="79cc7-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="79cc7-363">Rilevamento degli oggetti colpiti dallo sguardo del lettore e mantenimento di un riferimento agli oggetti rilevati.</span><span class="sxs-lookup"><span data-stu-id="79cc7-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="79cc7-364">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-364">To create this class:</span></span> 

1.  <span data-ttu-id="79cc7-365">Passare alla cartella **Scripts** creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79cc7-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="79cc7-366">Fare clic con il pulsante destro del mouse all'interno della cartella, quindi **creare > C# script**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="79cc7-367">Chiamare lo script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="79cc7-368">Fare doppio clic sul nuovo script **GazeInput** per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="79cc7-369">Inserire la riga seguente direttamente sopra il nome della classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="79cc7-370">Aggiungere quindi le variabili seguenti all'interno della classe **GazeInput** , sopra il metodo **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="79cc7-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="79cc7-371">È necessario aggiungere il codice per il metodo **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="79cc7-372">Questa operazione verrà chiamata quando la classe inizializza:</span><span class="sxs-lookup"><span data-stu-id="79cc7-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="79cc7-373">Implementare un metodo che creerà un'istanza e configurerà il cursore di sguardi:</span><span class="sxs-lookup"><span data-stu-id="79cc7-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="79cc7-374">Implementare i metodi per la configurazione di Raycast dalla fotocamera principale e per tenere traccia dell'oggetto attivo corrente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="79cc7-375">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="79cc7-376">Capitolo 10: creare la classe bot</span><span class="sxs-lookup"><span data-stu-id="79cc7-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="79cc7-377">Lo script che si intende creare è denominato **bot**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="79cc7-378">Questa è la classe principale dell'applicazione, che archivia:</span><span class="sxs-lookup"><span data-stu-id="79cc7-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="79cc7-379">Credenziali bot dell'app Web</span><span class="sxs-lookup"><span data-stu-id="79cc7-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="79cc7-380">Metodo che raccoglie i comandi vocali dell'utente</span><span class="sxs-lookup"><span data-stu-id="79cc7-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="79cc7-381">Metodo necessario per avviare conversazioni con il bot dell'app Web</span><span class="sxs-lookup"><span data-stu-id="79cc7-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="79cc7-382">Metodo necessario per inviare messaggi al bot dell'app Web</span><span class="sxs-lookup"><span data-stu-id="79cc7-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="79cc7-383">Per inviare messaggi al servizio bot, la coroutine **SendMessageToBot ()** compilerà un'attività, ovvero un oggetto riconosciuto da bot Framework come dati inviati dall'utente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="79cc7-384">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-384">To create this class:</span></span> 

1. <span data-ttu-id="79cc7-385">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="79cc7-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="79cc7-386">Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="79cc7-387">Assegnare un nome al **bot**di script.</span><span class="sxs-lookup"><span data-stu-id="79cc7-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="79cc7-388">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="79cc7-389">Aggiornare gli spazi dei nomi in modo che siano uguali a quelli riportati di seguito, nella parte superiore della classe **bot** :</span><span class="sxs-lookup"><span data-stu-id="79cc7-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="79cc7-390">All'interno della classe **bot** aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="79cc7-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="79cc7-391">Assicurarsi di inserire la **chiave privata bot** nella variabile **botSecret** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="79cc7-392">Si noterà che la **chiave privata del bot** è stata annotata all'inizio di questo corso, nel  **[capitolo 2](#chapter-2---create-the-azure-bot-service), passaggio 10**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="79cc7-393">È necessario aggiungere il codice per **sveglie ()** e **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="79cc7-394">Aggiungere i due gestori chiamati dalle librerie vocali quando l'acquisizione vocale inizia e termina.</span><span class="sxs-lookup"><span data-stu-id="79cc7-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="79cc7-395">Il *DictationRecognizer* arresterà automaticamente l'acquisizione della voce utente quando l'utente smette di parlare.</span><span class="sxs-lookup"><span data-stu-id="79cc7-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="79cc7-396">Il gestore seguente raccoglie il risultato dell'input vocale dell'utente e chiama la coroutine responsabile dell'invio del messaggio al servizio bot dell'app Web.</span><span class="sxs-lookup"><span data-stu-id="79cc7-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="79cc7-397">La seguente coroutine viene chiamata per avviare una conversazione con il bot.</span><span class="sxs-lookup"><span data-stu-id="79cc7-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="79cc7-398">Si noterà che, al termine della chiamata di conversazione, viene chiamato **SendMessageToCoroutine ()** passando una serie di parametri che imposteranno l'attività da inviare al servizio bot come messaggio vuoto.</span><span class="sxs-lookup"><span data-stu-id="79cc7-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="79cc7-399">Questa operazione viene eseguita per richiedere al servizio bot di avviare il dialogo.</span><span class="sxs-lookup"><span data-stu-id="79cc7-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="79cc7-400">La seguente coroutine viene chiamata per compilare l'attività da inviare al servizio bot.</span><span class="sxs-lookup"><span data-stu-id="79cc7-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="79cc7-401">La seguente coroutine viene chiamata per richiedere una risposta dopo l'invio di un'attività al servizio bot.</span><span class="sxs-lookup"><span data-stu-id="79cc7-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="79cc7-402">L'ultimo metodo da aggiungere a questa classe è necessario per visualizzare il messaggio nella scena:</span><span class="sxs-lookup"><span data-stu-id="79cc7-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="79cc7-403">È possibile che venga visualizzato un errore nella console dell'editor di Unity, in cui manca la classe **SceneOrganiser** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="79cc7-404">Ignorare questo messaggio, in quanto la classe verrà creata più avanti nell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="79cc7-405">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="79cc7-406">Capitolo 11: creare la classe di interazioni</span><span class="sxs-lookup"><span data-stu-id="79cc7-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="79cc7-407">La classe che si intende creare ora è chiamata **interazioni**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="79cc7-408">Questa classe viene usata per rilevare l'input di HoloLens Tap dall'utente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="79cc7-409">Se l'utente tocca osservando l'oggetto *bot* nella scena e il bot è pronto per l'ascolto degli input vocali, l'oggetto bot cambierà il colore in **rosso** e inizierà ad ascoltare gli input vocali.</span><span class="sxs-lookup"><span data-stu-id="79cc7-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="79cc7-410">Questa classe eredita dalla classe **GazeInput** ed è quindi in grado di fare riferimento al metodo **Start ()** e alle variabili da tale classe, identificate dall'uso di **base**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="79cc7-411">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-411">To create this class:</span></span>

1.  <span data-ttu-id="79cc7-412">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="79cc7-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="79cc7-413">Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="79cc7-414">Denominare le **interazioni**dello script.</span><span class="sxs-lookup"><span data-stu-id="79cc7-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="79cc7-415">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="79cc7-416">Aggiornare gli spazi dei nomi e l'ereditarietà della classe in modo che corrispondano a quanto riportato di seguito, nella parte superiore della classe Interactions:</span><span class="sxs-lookup"><span data-stu-id="79cc7-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="79cc7-417">All'interno della classe Interactions aggiungere la variabile seguente:</span><span class="sxs-lookup"><span data-stu-id="79cc7-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="79cc7-418">Aggiungere quindi il metodo **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="79cc7-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="79cc7-419">Aggiungere il gestore che verrà attivato quando l'utente esegue il gesto Tap davanti alla fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="79cc7-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="79cc7-420">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="79cc7-421">Capitolo 12: creare la classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="79cc7-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="79cc7-422">L'ultima classe richiesta in questo Lab è denominata **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="79cc7-423">Questa classe imposta la scena a livello di codice, aggiungendo componenti e script alla fotocamera principale e creando gli oggetti appropriati nella scena.</span><span class="sxs-lookup"><span data-stu-id="79cc7-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="79cc7-424">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="79cc7-424">To create this class:</span></span>

1.  <span data-ttu-id="79cc7-425">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="79cc7-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="79cc7-426">Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="79cc7-427">Denominare lo script **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="79cc7-428">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="79cc7-429">All'interno della classe **SceneOrganiser** aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="79cc7-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="79cc7-430">Aggiungere quindi i metodi **svegli ()** e **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="79cc7-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="79cc7-431">Aggiungere il metodo seguente, responsabile della creazione dell'oggetto bot nella scena e della configurazione dei parametri e dei componenti:</span><span class="sxs-lookup"><span data-stu-id="79cc7-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="79cc7-432">Aggiungere il metodo seguente, responsabile della creazione dell'oggetto dell'interfaccia utente nella scena, che rappresenta le risposte dal bot:</span><span class="sxs-lookup"><span data-stu-id="79cc7-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="79cc7-433">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="79cc7-434">Nell'editor di Unity trascinare lo script **SceneOrganiser** dalla cartella Scripts alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="79cc7-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="79cc7-435">Il componente dell'organizzatore della scena dovrebbe essere ora visualizzato nell'oggetto principale della fotocamera, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="79cc7-437">Capitolo 13: prima della compilazione</span><span class="sxs-lookup"><span data-stu-id="79cc7-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="79cc7-438">Per eseguire un test completo dell'applicazione, è necessario sideload nel HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79cc7-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="79cc7-439">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="79cc7-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="79cc7-440">Tutte le impostazioni indicate nel [**capitolo 4**](#chapter-4--set-up-the-unity-project) sono impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-440">All the settings mentioned in the [**Chapter 4**](#chapter-4--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="79cc7-441">Lo script **SceneOrganiser** è associato all'oggetto **principale della fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="79cc7-442">Nella classe **bot** verificare di aver inserito la **chiave privata bot** nella variabile **botSecret** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="79cc7-443">Capitolo 14: compilare e sideload in HoloLens</span><span class="sxs-lookup"><span data-stu-id="79cc7-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="79cc7-444">Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.</span><span class="sxs-lookup"><span data-stu-id="79cc7-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="79cc7-445">Passare a **impostazioni di compilazione**, **file > impostazioni di compilazione...** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="79cc7-446">Nella finestra **impostazioni di compilazione** fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="79cc7-448">Se non è già stato fatto, è necessario che i **progetti C# Unity**</span><span class="sxs-lookup"><span data-stu-id="79cc7-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="79cc7-449">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-449">Click **Build**.</span></span> <span data-ttu-id="79cc7-450">Unity avvierà una finestra di **Esplora file** , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="79cc7-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="79cc7-451">Creare la cartella adesso e denominarla **app**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="79cc7-452">Quindi, con la cartella dell' **app** selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="79cc7-453">Unity inizierà a compilare il progetto nella cartella dell' **app** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="79cc7-454">Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).</span><span class="sxs-lookup"><span data-stu-id="79cc7-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="79cc7-455">Capitolo 15: distribuire in HoloLens</span><span class="sxs-lookup"><span data-stu-id="79cc7-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="79cc7-456">Per eseguire la distribuzione in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="79cc7-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="79cc7-457">È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="79cc7-458">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="79cc7-458">To do this:</span></span>

    1. <span data-ttu-id="79cc7-459">Quando si indossa il HoloLens, aprire le **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="79cc7-460">Passare a **rete & Internet > opzioni avanzate Wi-Fi >**</span><span class="sxs-lookup"><span data-stu-id="79cc7-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="79cc7-461">Prendere nota dell'indirizzo **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="79cc7-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="79cc7-462">Quindi, tornare a **Settings (impostazioni**) e quindi **aggiornare & Security > per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="79cc7-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="79cc7-463">Impostare la modalità di sviluppo su.</span><span class="sxs-lookup"><span data-stu-id="79cc7-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="79cc7-464">Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="79cc7-465">Nella **configurazione della soluzione** selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="79cc7-466">Nella **piattaforma soluzione**selezionare **x86**, **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="79cc7-468">Passare al **menu Compila** e fare clic su **Distribuisci soluzione**per sideload l'applicazione in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79cc7-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="79cc7-469">L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="79cc7-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="79cc7-470">Per eseguire la distribuzione in un dispositivo headset immersivo, impostare la **piattaforma della soluzione** su *computer locale*e impostare la **configurazione** su *debug*, con *x86* come **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="79cc7-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="79cc7-471">Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*.</span><span class="sxs-lookup"><span data-stu-id="79cc7-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="79cc7-472">Capitolo 16: uso dell'applicazione in HoloLens</span><span class="sxs-lookup"><span data-stu-id="79cc7-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="79cc7-473">Una volta avviata l'applicazione, il bot viene visualizzato come una sfera blu davanti all'utente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="79cc7-474">Usare il **gesto Tap** mentre si sta guardando la sfera per avviare una conversazione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="79cc7-475">Attendere l'avvio della conversazione (l'interfaccia utente visualizzerà un messaggio quando si verifica).</span><span class="sxs-lookup"><span data-stu-id="79cc7-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="79cc7-476">Una volta ricevuto il messaggio introduttivo dal bot, toccare di nuovo sul bot in modo che diventi rosso e inizi ad ascoltare la voce.</span><span class="sxs-lookup"><span data-stu-id="79cc7-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="79cc7-477">Una volta terminata la conversazione, l'applicazione invierà il messaggio al bot e si riceverà immediatamente una risposta che verrà visualizzata nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="79cc7-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="79cc7-478">Ripetere il processo per inviare altri messaggi al bot (è necessario toccare ogni volta che si desidera un messaggio).</span><span class="sxs-lookup"><span data-stu-id="79cc7-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="79cc7-479">In questa conversazione viene illustrato come il bot può conservare le informazioni (il nome), fornendo anche informazioni note, ad esempio gli elementi che sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="79cc7-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="79cc7-480">Domande per chiedere al bot:</span><span class="sxs-lookup"><span data-stu-id="79cc7-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="79cc7-481">Applicazione bot (v4) per app Web completata</span><span class="sxs-lookup"><span data-stu-id="79cc7-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="79cc7-482">Congratulazioni, è stata creata un'app per realtà mista che sfrutta il bot app Web di Azure, Microsoft bot Framework V4.</span><span class="sxs-lookup"><span data-stu-id="79cc7-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Prodotto finale](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="79cc7-484">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="79cc7-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="79cc7-485">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="79cc7-485">Exercise 1</span></span>

<span data-ttu-id="79cc7-486">La struttura di conversazione in questo Lab è molto semplice.</span><span class="sxs-lookup"><span data-stu-id="79cc7-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="79cc7-487">Usare Microsoft LUIS per offrire al bot funzionalità di comprensione del linguaggio naturale.</span><span class="sxs-lookup"><span data-stu-id="79cc7-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="79cc7-488">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="79cc7-488">Exercise 2</span></span>

<span data-ttu-id="79cc7-489">Questo esempio non include la terminazione di una conversazione e il riavvio di un nuovo.</span><span class="sxs-lookup"><span data-stu-id="79cc7-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="79cc7-490">Per completare la funzionalità bot, provare a implementare la chiusura per la conversazione.</span><span class="sxs-lookup"><span data-stu-id="79cc7-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
