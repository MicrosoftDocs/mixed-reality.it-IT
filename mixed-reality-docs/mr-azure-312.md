---
title: MR e 312 Azure - integrazione di Bot
description: Completare questo corso per informazioni su come creare e distribuire un bot, tramite Microsoft Bot Framework v4 e consentire la comunicazione in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, visione artificiale, hololens, vr immersivi, microsoft bot framework v4, bot per app web, bot framework, bot di microsoft
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604980"
---
>[!NOTE]
><span data-ttu-id="7ed07-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7ed07-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="7ed07-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7ed07-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7ed07-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="7ed07-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7ed07-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7ed07-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7ed07-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="7ed07-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="7ed07-110">MR e Azure 312: Integrazione di BOT</span><span class="sxs-lookup"><span data-stu-id="7ed07-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="7ed07-111">In questo corso, si apprenderà come creare e distribuire un bot tramite il Microsoft Bot Framework versione 4 e comunicare con esso tramite un'applicazione di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="7ed07-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="7ed07-112">Il **Microsoft Bot Framework V4** è un set di API progettato per offrire agli sviluppatori gli strumenti necessari per compilare un bot estendibile e scalabile dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="7ed07-113">Per altre informazioni, visitare il [pagina Microsoft Bot Framework](https://dev.botframework.com/) o nella [Git Repository V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="7ed07-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="7ed07-114">Dopo aver completato il corso, verrà generata un'applicazione di realtà mista di Windows, che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7ed07-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="7ed07-115">Usare un **movimento toccare** per avviare il bot in ascolto per la voce degli utenti.</span><span class="sxs-lookup"><span data-stu-id="7ed07-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="7ed07-116">Quando l'utente ha detto qualcosa, il bot proverà a fornire una risposta.</span><span class="sxs-lookup"><span data-stu-id="7ed07-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="7ed07-117">Visualizzare la risposta del Bot come testo, posizionato in prossimità del bot, nella scena Unity.</span><span class="sxs-lookup"><span data-stu-id="7ed07-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="7ed07-118">Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="7ed07-119">Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="7ed07-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="7ed07-120">È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7ed07-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="7ed07-121">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="7ed07-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7ed07-122">Corso</span><span class="sxs-lookup"><span data-stu-id="7ed07-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7ed07-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7ed07-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7ed07-124"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="7ed07-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="7ed07-125">MR e Azure 312: Integrazione di BOT</span><span class="sxs-lookup"><span data-stu-id="7ed07-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="7ed07-126">✔️</span><span class="sxs-lookup"><span data-stu-id="7ed07-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7ed07-127">✔️</span><span class="sxs-lookup"><span data-stu-id="7ed07-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="7ed07-128">Questo corso è incentrato principalmente sulla HoloLens, è inoltre possibile applicare informazioni in questo corso per auricolari (VR) coinvolgenti di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="7ed07-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="7ed07-129">Poiché immersive auricolari (VR) non è accessibile fotocamere, sarà necessario una fotocamera esterna connessa al PC.</span><span class="sxs-lookup"><span data-stu-id="7ed07-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="7ed07-130">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare immersive auricolari (VR).</span><span class="sxs-lookup"><span data-stu-id="7ed07-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7ed07-131">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="7ed07-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="7ed07-132">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="7ed07-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="7ed07-133">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="7ed07-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="7ed07-134">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quanto elencato di seguito.</span><span class="sxs-lookup"><span data-stu-id="7ed07-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="7ed07-135">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="7ed07-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="7ed07-136">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="7ed07-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="7ed07-137">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="7ed07-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7ed07-138">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="7ed07-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7ed07-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="7ed07-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7ed07-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7ed07-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="7ed07-141">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="7ed07-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="7ed07-142">Accesso a Internet per Azure e per il recupero di Bot di Azure.</span><span class="sxs-lookup"><span data-stu-id="7ed07-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="7ed07-143">Per altre informazioni, [, seguire questo collegamento](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="7ed07-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="7ed07-144">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="7ed07-144">Before you start</span></span>

1.  <span data-ttu-id="7ed07-145">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="7ed07-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="7ed07-146">Configurare e testare l'HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7ed07-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="7ed07-147">Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="7ed07-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="7ed07-148">È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova app per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente).</span><span class="sxs-lookup"><span data-stu-id="7ed07-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="7ed07-149">Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="7ed07-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="7ed07-150">Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="7ed07-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="7ed07-151">Capitolo 1: creare l'applicazione di Bot</span><span class="sxs-lookup"><span data-stu-id="7ed07-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="7ed07-152">Il primo passaggio consiste nella creazione del bot come un'applicazione Web ASP.Net Core locale.</span><span class="sxs-lookup"><span data-stu-id="7ed07-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="7ed07-153">Dopo avere completato e testato, si sarà pubblicarla nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="7ed07-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="7ed07-154">Aprire Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-154">Open Visual Studio.</span></span> <span data-ttu-id="7ed07-155">Creare un nuovo progetto, seleziona **ASP NET Core Web Application** come tipo di progetto (risulterà sotto la sottosezione .NET Core) e chiamarlo **MyBot**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="7ed07-156">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-156">Click **OK**.</span></span>

2.  <span data-ttu-id="7ed07-157">Nella finestra che verrà visualizzato seleziona **vuoto**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="7ed07-158">Inoltre assicurarsi che la destinazione è impostata su **ASP NET Core 2.0** e l'autenticazione è impostata su **Nessuna autenticazione**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="7ed07-159">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-159">Click **OK**.</span></span>  

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="7ed07-161">A questo punto verrà aperta la soluzione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-161">The solution will now open.</span></span> <span data-ttu-id="7ed07-162">Pulsante destro del mouse sulla soluzione **Mybot** nel **Esplora soluzioni** e fare clic su **Gestisci pacchetti NuGet per la soluzione**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Creare l'applicazione di Bot](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="7ed07-164">Nel **esplorare** scheda, cercare **Microsoft.Bot.Builder.Integration.AspNet.Core** (assicurarsi di avere **includono versioni non definitive** selezionata).</span><span class="sxs-lookup"><span data-stu-id="7ed07-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="7ed07-165">Selezionare la versione del pacchetto **4.0.1-Preview**e selezionare le caselle di progetto.</span><span class="sxs-lookup"><span data-stu-id="7ed07-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="7ed07-166">Quindi fare clic su **installare**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-166">Then click on **Install**.</span></span> <span data-ttu-id="7ed07-167">Ora state installate le librerie necessarie per la **Bot Framework v4**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="7ed07-168">Chiudere la pagina di NuGet.</span><span class="sxs-lookup"><span data-stu-id="7ed07-168">Close the NuGet page.</span></span>

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="7ed07-170">Fare clic sui *Project*, **MyBot**, nel **Esplora soluzioni** e fare clic su **Aggiungi** **|** **Classe**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Creare l'applicazione di Bot](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="7ed07-172">Denominare la classe **MyBot** e fare clic su **Add**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="7ed07-174">Ripetere il precedente punto, per creare un'altra classe denominata **ConversationContext**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="7ed07-175">Fare clic su **wwwroot** nel **Esplora soluzioni** e fare clic su **Add** **|** **nuovo elemento**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="7ed07-176">Selezionare **pagina HTML** (risulterà sotto la sottosezione Web).</span><span class="sxs-lookup"><span data-stu-id="7ed07-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="7ed07-177">Denominare il file **default. HTML**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-177">Name the file **default.html**.</span></span> <span data-ttu-id="7ed07-178">Fai clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-178">Click **Add**.</span></span>

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="7ed07-180">L'elenco delle classi / gli oggetti di **Esplora soluzioni** dovrebbe essere simile all'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="7ed07-182">Fare doppio clic sulla **ConversationContext** classe.</span><span class="sxs-lookup"><span data-stu-id="7ed07-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="7ed07-183">Questa classe è responsabilità delle variabili utilizzate dal bot per mantenere il contesto della conversazione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="7ed07-184">I valori di contesto conversazione sono gestiti in un'istanza di questa classe, poiché qualsiasi istanza del **MyBot** classe verrà aggiornata ogni volta che viene ricevuta un'attività.</span><span class="sxs-lookup"><span data-stu-id="7ed07-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="7ed07-185">Aggiungere il codice seguente alla classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-185">Add the following code to the class:</span></span>

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

11. <span data-ttu-id="7ed07-186">Fare doppio clic sulla **MyBot** classe.</span><span class="sxs-lookup"><span data-stu-id="7ed07-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="7ed07-187">Questa classe ospiterà i gestori di chiamata da qualsiasi attività in ingresso dal cliente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="7ed07-188">In questa classe si aggiungerà il codice usato per compilare la conversazione tra il bot e il cliente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="7ed07-189">Come accennato in precedenza, un'istanza di questa classe viene inizializzata ogni volta che viene ricevuta un'attività.</span><span class="sxs-lookup"><span data-stu-id="7ed07-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="7ed07-190">Aggiungere il codice seguente alla classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-190">Add the following code to this class:</span></span>

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

12. <span data-ttu-id="7ed07-191">Fare doppio clic sulla **avvio** classe.</span><span class="sxs-lookup"><span data-stu-id="7ed07-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="7ed07-192">Questa classe verrà inizializzato il bot.</span><span class="sxs-lookup"><span data-stu-id="7ed07-192">This class will initialize the bot.</span></span> <span data-ttu-id="7ed07-193">Aggiungere il codice seguente alla classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-193">Add the following code to the class:</span></span>

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

13. <span data-ttu-id="7ed07-194">Aprire il **programma** file di classe e verificare il codice in esso è lo stesso come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="7ed07-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

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

14. <span data-ttu-id="7ed07-195">Ricordarsi di salvare le modifiche, a tale scopo, passare a **File** > **Salva tutto**, nella barra degli strumenti nella parte superiore di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="7ed07-196">Capitolo 2: creare il servizio Azure Bot</span><span class="sxs-lookup"><span data-stu-id="7ed07-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="7ed07-197">Ora che è stata compilata nel codice per il bot, è necessario pubblicarlo in un'istanza di *Bot per App Web* Service, nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="7ed07-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="7ed07-198">In questo capitolo illustrerà come creare e configurare il servizio Bot in Azure e quindi pubblica il codice ad esso.</span><span class="sxs-lookup"><span data-stu-id="7ed07-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="7ed07-199">In primo luogo, accedere al portale di Azure (https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="7ed07-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="7ed07-200">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="7ed07-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="7ed07-201">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="7ed07-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="7ed07-202">Una volta connessi, fare clic su **crea una risorsa** nell'angolo in alto a sinistra e cercare *bot per App Web*, fare clic su **invio**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="7ed07-204">La nuova pagina fornirà una descrizione del *Bot per App Web* servizio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="7ed07-205">AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="7ed07-207">Dopo avere fatto clic su **Create**:</span><span class="sxs-lookup"><span data-stu-id="7ed07-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="7ed07-208">Inserire la posizione desiderata **nome** per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="7ed07-209">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="7ed07-210">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="7ed07-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7ed07-211">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="7ed07-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="7ed07-212">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="7ed07-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="7ed07-213">Per altre informazioni sui gruppi di risorse di Azure, [, seguire questo collegamento](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="7ed07-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="7ed07-214">Determinare il percorso per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="7ed07-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="7ed07-215">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="7ed07-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="7ed07-216">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="7ed07-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="7ed07-217">Selezionare il **piano tariffario** appropriati per l'utente, se questo è il primo tempo nella creazione una *Bot per App Web* servizio, un livello gratuito (denominato F0) deve essere disponibile all'utente</span><span class="sxs-lookup"><span data-stu-id="7ed07-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="7ed07-218">**Nome dell'app** possono solo essere lasciate quello utilizzato per il *nome Bot*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="7ed07-219">Lasciare il *modello di Bot* come **base (C#)**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="7ed07-220">*Piano di servizio App/località* doveva essere compilati automaticamente per l'account.</span><span class="sxs-lookup"><span data-stu-id="7ed07-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="7ed07-221">Impostare il **archiviazione di Azure** che si desidera usare per ospitare il tuo Bot.</span><span class="sxs-lookup"><span data-stu-id="7ed07-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="7ed07-222">Se non è già, è possibile crearlo qui.</span><span class="sxs-lookup"><span data-stu-id="7ed07-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="7ed07-223">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="7ed07-224">Fare clic su Crea.</span><span class="sxs-lookup"><span data-stu-id="7ed07-224">Click Create.</span></span>
 
        ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="7ed07-226">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="7ed07-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="7ed07-227">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="7ed07-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="7ed07-229">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="7ed07-231">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="7ed07-232">Verrà visualizzata nella nuova istanza di servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="7ed07-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="7ed07-234">A questo punto è necessario configurare una funzionalità denominata **Direct Line** per consentire all'applicazione client comunicare con questo servizio Bot.</span><span class="sxs-lookup"><span data-stu-id="7ed07-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="7ed07-235">Fare clic su **canali**, quindi nella **aggiungere un canale in primo piano** sezione, fare clic sul **canale Direct Line configurare**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="7ed07-237">In questa pagina sono disponibili i **chiavi private** che consentirà l'autenticazione con il bot dell'app client.</span><span class="sxs-lookup"><span data-stu-id="7ed07-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="7ed07-238">Fare clic sui **mostrare** pulsante e richiedere una copia di una delle chiavi visualizzate, perché sarà necessaria in un secondo momento nel progetto.</span><span class="sxs-lookup"><span data-stu-id="7ed07-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="7ed07-240">Capitolo 3: pubblicare il Bot per il servizio Bot per App Web di Azure</span><span class="sxs-lookup"><span data-stu-id="7ed07-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="7ed07-241">Ora che il servizio è pronto, è necessario pubblicare il codice di Bot, creato in precedenza, per il servizio Bot di App Web appena creata.</span><span class="sxs-lookup"><span data-stu-id="7ed07-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="7ed07-242">È necessario pubblicare il Bot per il servizio di Azure ogni volta che si apportano modifiche alla soluzione Bot / code.</span><span class="sxs-lookup"><span data-stu-id="7ed07-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="7ed07-243">Tornare alla soluzione Visual Studio creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="7ed07-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="7ed07-244">Fare clic sui **MyBot** progetto le **Esplora soluzioni**, quindi fare clic su **Publish**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Pubblicare il Bot per il servizio Bot per App Web di Azure](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="7ed07-246">Nel *selezionare una destinazione di pubblicazione* pagina, fare clic su **servizio App**, quindi **seleziona esistente**, infine fare clic su **Crea profilo** (potrebbe essere necessario Fare clic sulla freccia a discesa con i *pubblica* pulsante, se questo non è visibile).</span><span class="sxs-lookup"><span data-stu-id="7ed07-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Pubblicare il Bot per il servizio Bot per App Web di Azure](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="7ed07-248">Se non ancora effettuato l'accesso all'account Microsoft, è necessario farlo qui.</span><span class="sxs-lookup"><span data-stu-id="7ed07-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="7ed07-249">Nel **Publish** pagina si noterà che è necessario impostare lo stesso **sottoscrizione** usato per il *Bot per App Web* creazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="7ed07-250">Quindi impostare il **View** come **gruppo di risorse** e, nell'elenco a discesa di struttura di cartelle, selezionare il **gruppo di risorse** hanno creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="7ed07-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="7ed07-251">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-251">Click **OK**.</span></span> 

    ![Pubblicare il Bot per il servizio Bot per App Web di Azure](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="7ed07-253">Fare clic sulla **pubblica** pulsante e attendere il Bot da pubblicare (potrebbe richiedere alcuni minuti).</span><span class="sxs-lookup"><span data-stu-id="7ed07-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Pubblicare il Bot per il servizio Bot per App Web di Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="7ed07-255">Capitolo 4: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="7ed07-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="7ed07-256">Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="7ed07-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="7ed07-257">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-257">Open *Unity* and click **New**.</span></span> 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="7ed07-259">A questo punto, è necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="7ed07-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="7ed07-260">Inserire **Hololens Bot**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="7ed07-261">Verificare che il modello di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="7ed07-262">Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="7ed07-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="7ed07-263">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-263">Then, click **Create project**.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="7ed07-265">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="7ed07-266">Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="7ed07-267">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="7ed07-268">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="7ed07-268">Close the **Preferences** window.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="7ed07-270">Passare quindi ad **File > Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sui **commutatore piattaforma** pulsante per applicare la selezione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="7ed07-272">Mentre si trovano ancora nella **File > Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="7ed07-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="7ed07-273">**Dispositivo di destinazione** è impostata su **Hololens**</span><span class="sxs-lookup"><span data-stu-id="7ed07-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="7ed07-274">Per le cuffie coinvolgenti, impostare **dispositivo di destinazione** al *qualsiasi dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="7ed07-275">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="7ed07-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="7ed07-276">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="7ed07-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="7ed07-277">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="7ed07-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="7ed07-278">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="7ed07-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="7ed07-279">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="7ed07-280">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="7ed07-281">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-281">A save window will appear.</span></span>
        
            ![Configurare il progetto Unity](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="7ed07-283">Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Configurare il progetto Unity](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="7ed07-285">Aprire appena creato **scene** cartella e quindi il *nome File*: campo di testo, digitare **BotScene**, quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="7ed07-287">Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="7ed07-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="7ed07-288">Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.</span><span class="sxs-lookup"><span data-stu-id="7ed07-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="7ed07-290">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="7ed07-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="7ed07-291">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="7ed07-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="7ed07-292">**Versione del Runtime di scripting** deve essere **sperimentale (equivalente NET 4.6)**; questa modifica richiede il riavvio dell'Editor.</span><span class="sxs-lookup"><span data-stu-id="7ed07-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="7ed07-293">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="7ed07-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="7ed07-294">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="7ed07-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="7ed07-296">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="7ed07-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="7ed07-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="7ed07-297">**InternetClient**</span></span>
        - <span data-ttu-id="7ed07-298">**Microfono**</span><span class="sxs-lookup"><span data-stu-id="7ed07-298">**Microphone**</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="7ed07-300">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="7ed07-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurare il progetto Unity](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="7ed07-302">Nuovamente in *Build Settings* _Unity C#_  progetti non sono più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="7ed07-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="7ed07-303">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="7ed07-304">Salvare la scena e il progetto (**FILE > Salva scena / FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="7ed07-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="7ed07-305">Capitolo 5: impostazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="7ed07-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ed07-306">Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [Package.unitypackage-Azure-SIG-312](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importarlo nel progetto come una [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), quindi continuare dal [capitolo 7](#chapter-7-–-create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="7ed07-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="7ed07-307">Nel *Pannello di gerarchia*, selezionare la **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="7ed07-308">Una volta selezionata, sarà possibile visualizzare tutti i componenti del **Main Camera** nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="7ed07-309">Il **oggetto della fotocamera** devono essere denominati **Main Camera** (si noti l'ortografici)</span><span class="sxs-lookup"><span data-stu-id="7ed07-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="7ed07-310">Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici)</span><span class="sxs-lookup"><span data-stu-id="7ed07-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="7ed07-311">Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="7ed07-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="7ed07-312">Impostare **cancellare i flag** al **colore a tinta unita**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="7ed07-313">Impostare il **sfondo** colore del componente della fotocamera su **nero, Alpha 0 (codice esadecimale: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="7ed07-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![il programma di installazione della fotocamera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="7ed07-315">Capitolo 6: importazione della libreria Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="7ed07-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="7ed07-316">Che consentono di deserializzano e serializzano oggetti ricevuti e inviati al servizio Bot è necessario scaricare il **Newtonsoft** libreria.</span><span class="sxs-lookup"><span data-stu-id="7ed07-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="7ed07-317">Si noterà una [versione compatibile già organizzati con la struttura cartella corretta Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="7ed07-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="7ed07-318">Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornita con questo corso.</span><span class="sxs-lookup"><span data-stu-id="7ed07-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="7ed07-319">Aggiungere il *.unitypackage* a Unity tramite il **asset** > **Importa pacchetto** > **pacchetto personalizzato** opzione di menu.</span><span class="sxs-lookup"><span data-stu-id="7ed07-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Importazione della libreria Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="7ed07-321">Nel **Importa pacchetto Unity** scatola viene, assicurarsi che tutto ciò che in (e tra cui) **plug-in** sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="7ed07-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importazione della libreria Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="7ed07-323">Scegliere il **importazione** pulsante per aggiungere elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="7ed07-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="7ed07-324">Andare alla **Newtonsoft** cartella sotto **plug-in** nella visualizzazione del progetto e selezionare il plug-in di Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="7ed07-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="7ed07-325">Con il plug-in di Newtonsoft selezionato, assicurarsi che **Any Platform** viene **deselezionata**, quindi verificare che **WSAPlayer** anche **deselezionata**, quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="7ed07-326">Si tratta semplicemente di confermare che i file siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="7ed07-327">Contrassegnare questi plug-in Configura perché possano essere usati solo nell'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="7ed07-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="7ed07-328">Sono presenti un set diverso di esse nella cartella WSA che verrà usato dopo che il progetto viene esportato da Unity.</span><span class="sxs-lookup"><span data-stu-id="7ed07-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="7ed07-329">Successivamente, è necessario aprire la **WSA** cartella, all'interno di **Newtonsoft** cartella.</span><span class="sxs-lookup"><span data-stu-id="7ed07-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="7ed07-330">Si noterà una copia dello stesso file che appena configurato.</span><span class="sxs-lookup"><span data-stu-id="7ed07-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="7ed07-331">Selezionare il file e quindi nella finestra di ispezione, assicurarsi che</span><span class="sxs-lookup"><span data-stu-id="7ed07-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="7ed07-332">**Qualsiasi piattaforma** è **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="7ed07-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="7ed07-333">**solo** **WSAPlayer** è **selezionata**</span><span class="sxs-lookup"><span data-stu-id="7ed07-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="7ed07-334">**Non elaborare** è **selezionata**</span><span class="sxs-lookup"><span data-stu-id="7ed07-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="7ed07-335">Capitolo 7-creare il BotTag</span><span class="sxs-lookup"><span data-stu-id="7ed07-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="7ed07-336">Creare una nuova **Tag** oggetto chiamato **BotTag**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="7ed07-337">Selezionare la fotocamera principale nella scena.</span><span class="sxs-lookup"><span data-stu-id="7ed07-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="7ed07-338">Fare clic sul menu nel Pannello di controllo a discesa Tag.</span><span class="sxs-lookup"><span data-stu-id="7ed07-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="7ed07-339">Fare clic su **aggiungere Tag**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-339">Click on **Add Tag**.</span></span>

    ![il programma di installazione della fotocamera](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="7ed07-341">Fare clic sui **+** simbolo.</span><span class="sxs-lookup"><span data-stu-id="7ed07-341">Click on the **+** symbol.</span></span> <span data-ttu-id="7ed07-342">Denominare il nuovo **Tag** come **BotTag**, *Salva*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![il programma di installazione della fotocamera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="7ed07-344">**Non li** applicare le **BotTag** alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="7ed07-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="7ed07-345">Se accidentalmente si hanno fatto, assicurarsi di modificare la fotocamera principale al tag *MainCamera*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="7ed07-346">Capitolo 8: creare la classe BotObjects</span><span class="sxs-lookup"><span data-stu-id="7ed07-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="7ed07-347">È il primo script è necessario creare il **BotObjects** (classe), che è una classe vuota creata in modo che una serie di altri oggetti di classe possono essere archiviata nello stesso alfabeto e accessibile da altri script nella scena.</span><span class="sxs-lookup"><span data-stu-id="7ed07-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="7ed07-348">La creazione di questa classe è esclusivamente una scelta dell'architettura, questi oggetti possono invece essere ospitati in script Bot che verrà creato più avanti in questo corso.</span><span class="sxs-lookup"><span data-stu-id="7ed07-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="7ed07-349">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-349">To create this class:</span></span> 

1.  <span data-ttu-id="7ed07-350">Fare doppio clic nella *pannello progetto*, quindi **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="7ed07-351">Denominare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-351">Name the folder **Scripts**.</span></span> 

    ![Crea cartella scripts.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="7ed07-353">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="7ed07-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="7ed07-354">Quindi all'interno di tale cartella, pulsante destro del mouse e scegliere **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="7ed07-355">Denominare lo script **BotObjects**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="7ed07-356">Fare doppio clic su nuova **BotObjects** script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="7ed07-357">Eliminare il contenuto dello script e sostituirlo con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="7ed07-357">Delete the content of the script and replace it with the following code:</span></span>

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

6.  <span data-ttu-id="7ed07-358">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="7ed07-359">Capitolo 9: creare la classe GazeInput</span><span class="sxs-lookup"><span data-stu-id="7ed07-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="7ed07-360">La classe successiva si intende creare è il **GazeInput** classe.</span><span class="sxs-lookup"><span data-stu-id="7ed07-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="7ed07-361">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="7ed07-361">This class is responsible for:</span></span>

- <span data-ttu-id="7ed07-362">Creazione di un cursore che rappresenterà il *estasiati* del lettore.</span><span class="sxs-lookup"><span data-stu-id="7ed07-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="7ed07-363">Rilevamento di oggetti colpiti sguardo del lettore e che contiene un riferimento agli oggetti rilevati.</span><span class="sxs-lookup"><span data-stu-id="7ed07-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="7ed07-364">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-364">To create this class:</span></span> 

1.  <span data-ttu-id="7ed07-365">Andare alla **script** cartella creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="7ed07-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="7ed07-366">Pulsante destro del mouse all'interno della cartella **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="7ed07-367">Chiamare lo script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="7ed07-368">Fare doppio clic su nuova **GazeInput** script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="7ed07-369">Inserire la riga seguente a destra in alto del nome della classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="7ed07-370">Quindi aggiungere le variabili seguenti all'interno di **GazeInput** classe sopra il **Start ()** metodo:</span><span class="sxs-lookup"><span data-stu-id="7ed07-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="7ed07-371">Codice per un **Start ()** metodo deve essere aggiunti.</span><span class="sxs-lookup"><span data-stu-id="7ed07-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="7ed07-372">Questo evento viene chiamato quando si inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-372">This will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="7ed07-373">Implementare un metodo che crea un'istanza e impostare il cursore sguardo:</span><span class="sxs-lookup"><span data-stu-id="7ed07-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

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

8.  <span data-ttu-id="7ed07-374">Implementare i metodi che consentono di configurare il Raycast dalla fotocamera principale e terrà traccia dell'oggetto con lo stato attivo corrente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
 
9.  <span data-ttu-id="7ed07-375">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="7ed07-376">Capitolo 10: creare la classe di Bot</span><span class="sxs-lookup"><span data-stu-id="7ed07-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="7ed07-377">Lo script si intende creare a questo punto viene chiamato **Bot**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="7ed07-378">Si tratta della classe di base dell'applicazione, archivia:</span><span class="sxs-lookup"><span data-stu-id="7ed07-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="7ed07-379">Le credenziali di Bot per App Web</span><span class="sxs-lookup"><span data-stu-id="7ed07-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="7ed07-380">Il metodo che raccoglie i comandi vocali utente</span><span class="sxs-lookup"><span data-stu-id="7ed07-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="7ed07-381">Il metodo necessario per avviare le conversazioni con il Bot per App Web</span><span class="sxs-lookup"><span data-stu-id="7ed07-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="7ed07-382">Il metodo necessario per inviare messaggi al tuo Bot di App Web</span><span class="sxs-lookup"><span data-stu-id="7ed07-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="7ed07-383">Per inviare messaggi al servizio Bot, il **SendMessageToBot()** coroutine creerà un'attività, che è un oggetto riconosciuto dal Bot Framework, come i dati inviati dall'utente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="7ed07-384">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-384">To create this class:</span></span> 

1. <span data-ttu-id="7ed07-385">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="7ed07-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="7ed07-386">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7ed07-387">Denominare lo script **Bot**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="7ed07-388">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="7ed07-389">Aggiornare gli spazi dei nomi affinché corrisponda al seguente, in cima il **Bot** classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="7ed07-390">All'interno di **Bot** classe aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="7ed07-390">Inside the **Bot** class add the following variables:</span></span>

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
    > <span data-ttu-id="7ed07-391">Assicurarsi di inserire le **Bot Secret Key** nel **botSecret** variabile.</span><span class="sxs-lookup"><span data-stu-id="7ed07-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="7ed07-392">Verrà annotati i **Bot Secret Key** all'inizio di questo corso, in  **[capitolo 2](#chapter-2---create-the-azure-bot-service), passaggio 10**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="7ed07-393">Codice per un **Awake()** e **Start ()** deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="7ed07-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

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

8. <span data-ttu-id="7ed07-394">Aggiungere i due gestori che vengono chiamati dalle librerie di riconoscimento vocale quando inizia e finisce di acquisizione della voce.</span><span class="sxs-lookup"><span data-stu-id="7ed07-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="7ed07-395">Il *DictationRecognizer* arresterà automaticamente i suggerimenti degli utenti per l'acquisizione quando l'utente interrompe il modo di parlare.</span><span class="sxs-lookup"><span data-stu-id="7ed07-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

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

1. <span data-ttu-id="7ed07-396">Il gestore seguente consente di raccogliere il risultato dell'input vocale dell'utente e chiama le coroutine responsabile dell'invio del messaggio al servizio Web App Bot.</span><span class="sxs-lookup"><span data-stu-id="7ed07-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

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

10. <span data-ttu-id="7ed07-397">Le coroutine seguente viene chiamato per iniziare una conversazione con il Bot.</span><span class="sxs-lookup"><span data-stu-id="7ed07-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="7ed07-398">Si noterà che al termine della chiamata di conversazione, chiama il **SendMessageToCoroutine()** passando una serie di parametri che imposta l'attività da inviare al servizio Bot come un messaggio vuoto.</span><span class="sxs-lookup"><span data-stu-id="7ed07-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="7ed07-399">Questa operazione viene eseguita per richiedere il servizio Bot per avviare la finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="7ed07-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

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

11. <span data-ttu-id="7ed07-400">Le coroutine seguente viene chiamato per compilare l'attività da inviare al servizio Bot.</span><span class="sxs-lookup"><span data-stu-id="7ed07-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

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

12. <span data-ttu-id="7ed07-401">Le coroutine seguente viene chiamato per richiedere una risposta dopo l'invio di un'attività per il servizio Bot.</span><span class="sxs-lookup"><span data-stu-id="7ed07-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

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

13. <span data-ttu-id="7ed07-402">Quest'ultimo metodo da aggiungere a questa classe, è necessario per visualizzare il messaggio nella scena:</span><span class="sxs-lookup"><span data-stu-id="7ed07-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

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
    > <span data-ttu-id="7ed07-403">Si potrebbe comparire un errore interno della Console di Editor di Unity, assenza di **SceneOrganiser** classe.</span><span class="sxs-lookup"><span data-stu-id="7ed07-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="7ed07-404">Ignorare questo messaggio, come verrà creata questa classe in un secondo momento nell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="7ed07-405">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="7ed07-406">Capitolo 11: creare la classe interazioni</span><span class="sxs-lookup"><span data-stu-id="7ed07-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="7ed07-407">La classe a cui vuole creare a questo punto viene chiamata **interazioni**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="7ed07-408">Questa classe viene utilizzata per rilevare il HoloLens toccare Input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="7ed07-409">Se l'utente tocca mentre si esaminano le *Bot* oggetti nella scena e Bot sono pronto per l'ascolto per gli input vocale, l'oggetto Bot cambierà colore **rosso** e iniziare l'ascolto per gli input vocale.</span><span class="sxs-lookup"><span data-stu-id="7ed07-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="7ed07-410">Questa classe eredita dal **GazeInput** classe e quindi, è in grado di fare riferimento il **Start ()** metodo e variabili da tale classe, indicato mediante l'utilizzo di **base**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="7ed07-411">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-411">To create this class:</span></span>

1.  <span data-ttu-id="7ed07-412">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="7ed07-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7ed07-413">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7ed07-414">Denominare lo script **interazioni**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="7ed07-415">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="7ed07-416">Aggiornare gli spazi dei nomi e l'ereditarietà delle classi sia lo stesso come illustrato di seguito, nella parte superiore del **interazioni** classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="7ed07-417">All'interno di **interazioni** classe aggiungere la variabile seguente:</span><span class="sxs-lookup"><span data-stu-id="7ed07-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="7ed07-418">Quindi aggiungere il **Start ()** metodo:</span><span class="sxs-lookup"><span data-stu-id="7ed07-418">Then add the **Start()** method:</span></span>

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

7.  <span data-ttu-id="7ed07-419">Aggiungere il gestore che verrà attivato quando l'utente esegue il gesto tocco davanti alla fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="7ed07-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

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

8. <span data-ttu-id="7ed07-420">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="7ed07-421">Capitolo 12: creare la classe SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="7ed07-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="7ed07-422">Viene chiamato l'ultima classe necessaria in questo laboratorio **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="7ed07-423">Questa classe configurerà la scena a livello di codice, aggiungendo componenti e gli script alla fotocamera principale, e creando gli oggetti appropriati nella scena.</span><span class="sxs-lookup"><span data-stu-id="7ed07-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="7ed07-424">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="7ed07-424">To create this class:</span></span>

1.  <span data-ttu-id="7ed07-425">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="7ed07-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="7ed07-426">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="7ed07-427">Denominare lo script **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="7ed07-428">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ed07-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="7ed07-429">All'interno di **SceneOrganiser** classe aggiungere le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="7ed07-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

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

6.  <span data-ttu-id="7ed07-430">Quindi aggiungere il **Awake()** e **Start ()** metodi:</span><span class="sxs-lookup"><span data-stu-id="7ed07-430">Then add the **Awake()** and **Start()** methods:</span></span>

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

7.  <span data-ttu-id="7ed07-431">Aggiungere il metodo seguente, responsabile della creazione dell'oggetto Bot nella scena e configurando i parametri e i componenti:</span><span class="sxs-lookup"><span data-stu-id="7ed07-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

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

7.  <span data-ttu-id="7ed07-432">Aggiungere il metodo seguente, responsabile della creazione dell'oggetto dell'interfaccia utente nella scena, che rappresenta le risposte provenienti dai Bot:</span><span class="sxs-lookup"><span data-stu-id="7ed07-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

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

8.  <span data-ttu-id="7ed07-433">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="7ed07-434">Nell'Editor di Unity trascinare la **SceneOrganiser** script dalla cartella degli script per la fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="7ed07-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="7ed07-435">Il componente scena Organizer dovrebbe ora apparire sull'oggetto Main Camera, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="7ed07-437">Capitolo 13-prima della compilazione</span><span class="sxs-lookup"><span data-stu-id="7ed07-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="7ed07-438">Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7ed07-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="7ed07-439">Prima di procedere, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="7ed07-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="7ed07-440">Tutte le impostazioni indicate nella [ **capitolo 4** ](#Chapter-4-–-Set-up-the-unity-project) siano impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="7ed07-441">Lo script **SceneOrganiser** è collegato il **Main Camera** oggetto.</span><span class="sxs-lookup"><span data-stu-id="7ed07-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="7ed07-442">Nel **Bot** classe, assicurarsi di avere inserito il **Bot Secret Key** nel **botSecret** variabile.</span><span class="sxs-lookup"><span data-stu-id="7ed07-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="7ed07-443">Capitolo 14: compilazione e trasferirla in locale per il HoloLens</span><span class="sxs-lookup"><span data-stu-id="7ed07-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="7ed07-444">Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.</span><span class="sxs-lookup"><span data-stu-id="7ed07-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="7ed07-445">Passare a **impostazioni di compilazione**, **File > Impostazioni di compilazione...** .</span><span class="sxs-lookup"><span data-stu-id="7ed07-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="7ed07-446">Dal **Build Settings** finestra, fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="7ed07-448">Se non è già, graduazione **Unity C# progetti**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="7ed07-449">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-449">Click **Build**.</span></span> <span data-ttu-id="7ed07-450">Unity avvierà una **Esplora File** finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in.</span><span class="sxs-lookup"><span data-stu-id="7ed07-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="7ed07-451">Creare ora tale cartella e denominarlo **App**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="7ed07-452">Quindi con il **App** cartella selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="7ed07-453">Unity verrà avviata la compilazione del progetto per la **App** cartella.</span><span class="sxs-lookup"><span data-stu-id="7ed07-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="7ed07-454">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).</span><span class="sxs-lookup"><span data-stu-id="7ed07-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="7ed07-455">Capitolo 15 – distribuire a HoloLens</span><span class="sxs-lookup"><span data-stu-id="7ed07-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="7ed07-456">Per distribuire in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="7ed07-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="7ed07-457">È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="7ed07-458">A tale scopo, effettuare le seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="7ed07-458">To do this:</span></span>

    1. <span data-ttu-id="7ed07-459">Durante l'uso di HoloLens, aprire il **impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="7ed07-460">Passare a **rete e Internet > Wi-Fi > Opzioni avanzate**</span><span class="sxs-lookup"><span data-stu-id="7ed07-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="7ed07-461">Si noti il **IPv4** indirizzo.</span><span class="sxs-lookup"><span data-stu-id="7ed07-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="7ed07-462">Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza > per gli sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="7ed07-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="7ed07-463">Attivare la modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="7ed07-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="7ed07-464">Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="7ed07-465">Nel **configurazione della soluzione** selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="7ed07-466">Nel **piattaforma soluzione**, selezionare **x86**, **computer remoto**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="7ed07-468">Andare alla **dal menu Compila** e fare clic su **Distribuisci soluzione**, trasferire localmente l'applicazione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7ed07-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="7ed07-469">L'app deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="7ed07-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ed07-470">Per distribuire visore VR immersivi, impostare il **piattaforma soluzione** al *computer locale*e impostare il **configurazione** a *Debug*, con *x86* come la **piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="7ed07-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="7ed07-471">Quindi distribuire in locale del computer, utilizzando il **dal menu Compila**, selezionando *Distribuisci soluzione*.</span><span class="sxs-lookup"><span data-stu-id="7ed07-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="7ed07-472">Capitolo 16 utilizzando l'applicazione nella finestra di HoloLens</span><span class="sxs-lookup"><span data-stu-id="7ed07-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="7ed07-473">Dopo aver avviato l'applicazione, il Bot verrà visualizzato come una sfera davanti è blu.</span><span class="sxs-lookup"><span data-stu-id="7ed07-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="7ed07-474">Usare la **movimento toccare** mentre sono gazing alla sfera per avviare una conversazione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="7ed07-475">Attesa della conversazione da avviare (l'interfaccia utente verrà visualizzato un messaggio se succede).</span><span class="sxs-lookup"><span data-stu-id="7ed07-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="7ed07-476">Dopo aver ricevuto il messaggio introduttivo di Bot, toccare di nuovo su Bot in modo che verrà divengono rosso e iniziare ad ascoltare la voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="7ed07-477">Dopo aver interrotto la conversazione, l'applicazione invierà il messaggio per il Bot e tempestivamente il cliente si riceverà una risposta che verrà visualizzata nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="7ed07-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="7ed07-478">Ripetere il processo per inviare più messaggi al tuo Bot (è necessario toccare ogni volta che si desidera invia un messaggio).</span><span class="sxs-lookup"><span data-stu-id="7ed07-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="7ed07-479">La conversazione viene illustrato come il Bot di mantenere le informazioni (il nome), fornendo anche informazioni note (ad esempio, gli elementi che sono immagazzinati) allo stesso tempo.</span><span class="sxs-lookup"><span data-stu-id="7ed07-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="7ed07-480">Alcune domande da chiedere al Bot:</span><span class="sxs-lookup"><span data-stu-id="7ed07-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="7ed07-481">L'applicazione finita Bot per App Web (v4)</span><span class="sxs-lookup"><span data-stu-id="7ed07-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="7ed07-482">Complimenti, è stata compilata un'app per realtà mista che sfrutta il Bot per App Web Azure, Microsoft Bot Framework v4.</span><span class="sxs-lookup"><span data-stu-id="7ed07-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Versione finale del prodotto](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7ed07-484">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="7ed07-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7ed07-485">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="7ed07-485">Exercise 1</span></span>

<span data-ttu-id="7ed07-486">La struttura di conversazione in questo laboratorio è molto semplice.</span><span class="sxs-lookup"><span data-stu-id="7ed07-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="7ed07-487">Usare Microsoft LUIS per fornire il bot le funzionalità di comprensione del linguaggio naturale.</span><span class="sxs-lookup"><span data-stu-id="7ed07-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="7ed07-488">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="7ed07-488">Exercise 2</span></span>

<span data-ttu-id="7ed07-489">In questo esempio non include terminare una conversazione e il riavvio di una nuova.</span><span class="sxs-lookup"><span data-stu-id="7ed07-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="7ed07-490">Per verificare la funzionalità di Bot completato, provare a implementare la chiusura per la conversazione.</span><span class="sxs-lookup"><span data-stu-id="7ed07-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
