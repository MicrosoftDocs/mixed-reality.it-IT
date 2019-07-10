---
title: MR e Azure 309 - Application insights
description: Completare questo corso di informazioni su come raccogliere analitica relative a un comportamento utente all'interno di un'applicazione di realtà mista, l'utilizzo del servizio di Azure Application Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, insights dell'applicazione, hololens, coinvolgenti, vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694567"
---
>[!NOTE]
><span data-ttu-id="a0547-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="a0547-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a0547-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="a0547-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a0547-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="a0547-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a0547-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="a0547-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a0547-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a0547-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a0547-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="a0547-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="a0547-110">MR e Azure 309: Insights dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="a0547-110">MR and Azure 309: Application insights</span></span>

![versione finale del prodotto-avvio](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="a0547-112">In questo corso, si apprenderà come aggiungere funzionalità di Application Insights a un'applicazione di realtà mista, usando l'API di Azure Application Insights per raccogliere analitica riguardanti il comportamento degli utenti.</span><span class="sxs-lookup"><span data-stu-id="a0547-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="a0547-113">Application Insights è un servizio Microsoft, consentendo agli sviluppatori di raccogliere analitica dalle rispettive applicazioni e gestire da un portale facile da usare.</span><span class="sxs-lookup"><span data-stu-id="a0547-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="a0547-114">L'analitica può essere qualsiasi elemento, da prestazioni personalizzazione delle informazioni da raccogliere.</span><span class="sxs-lookup"><span data-stu-id="a0547-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="a0547-115">Per altre informazioni, visitare il [pagina di Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="a0547-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="a0547-116">Dopo aver completato il corso, si avrà un'applicazione di realtà mista visore VR immersivi che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0547-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="a0547-117">Consentire all'utente estasiati e spostarsi all'interno di una scena.</span><span class="sxs-lookup"><span data-stu-id="a0547-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="a0547-118">Attivare l'invio di analitica per la *servizio di Application Insights*, tramite l'uso di sguardo e prossimità agli oggetti nella scena.</span><span class="sxs-lookup"><span data-stu-id="a0547-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="a0547-119">L'app chiamerà anche al momento il servizio, il recupero di informazioni sull'oggetto che è stato affrontato il massimo dall'utente, nelle ultime 24 ore.</span><span class="sxs-lookup"><span data-stu-id="a0547-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="a0547-120">Tale oggetto cambierà il colore verde.</span><span class="sxs-lookup"><span data-stu-id="a0547-120">That object will change its color to green.</span></span>

<span data-ttu-id="a0547-121">Questo corso ti spiegherà come ottenere i risultati da del servizio Application Insights, in un'applicazione di esempio basate su Unity.</span><span class="sxs-lookup"><span data-stu-id="a0547-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="a0547-122">Sarà quindi compito è possibile applicare questi concetti a un'applicazione personalizzata, che potrebbe voler costruire.</span><span class="sxs-lookup"><span data-stu-id="a0547-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="a0547-123">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a0547-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a0547-124">Corso</span><span class="sxs-lookup"><span data-stu-id="a0547-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a0547-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a0547-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a0547-126"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="a0547-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a0547-127">MR e Azure 309: Insights dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="a0547-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="a0547-128">✔️</span><span class="sxs-lookup"><span data-stu-id="a0547-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a0547-129">✔️</span><span class="sxs-lookup"><span data-stu-id="a0547-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="a0547-130">Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0547-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="a0547-131">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0547-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="a0547-132">Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.</span><span class="sxs-lookup"><span data-stu-id="a0547-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0547-133">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a0547-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="a0547-134">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="a0547-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="a0547-135">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="a0547-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="a0547-136">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quanto elencato di seguito.</span><span class="sxs-lookup"><span data-stu-id="a0547-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="a0547-137">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="a0547-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="a0547-138">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="a0547-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="a0547-139">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="a0547-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a0547-140">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="a0547-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a0547-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="a0547-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a0547-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a0547-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="a0547-143">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="a0547-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="a0547-144">Le cuffie con un microfono incorporato (se le cuffie non ha un mic incorporati e altri relatori)</span><span class="sxs-lookup"><span data-stu-id="a0547-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="a0547-145">Accesso a Internet per la configurazione di Azure e il recupero dei dati di Application Insights</span><span class="sxs-lookup"><span data-stu-id="a0547-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="a0547-146">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="a0547-146">Before you start</span></span>

<span data-ttu-id="a0547-147">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="a0547-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="a0547-148">Tenere presente, i dati in transito per *Application Insights* richiede tempo, pertanto è necessario paziente.</span><span class="sxs-lookup"><span data-stu-id="a0547-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="a0547-149">Se si vuole verificare se il servizio ha ricevuto i dati, consultare [capitolo 14](#chapter-14---the-application-insights-service-portal), che illustrerà come esplorare il portale.</span><span class="sxs-lookup"><span data-stu-id="a0547-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="a0547-150">Capitolo 1 - portale di Azure</span><span class="sxs-lookup"><span data-stu-id="a0547-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="a0547-151">Per utilizzare *Application Insights*, sarà necessario creare e configurare un' *servizio Application Insights* nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="a0547-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="a0547-152">Accedi per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="a0547-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="a0547-153">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="a0547-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="a0547-154">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="a0547-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="a0547-155">Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *Application Insights*, fare clic su **invio**.</span><span class="sxs-lookup"><span data-stu-id="a0547-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a0547-156">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="a0547-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="a0547-158">La nuova pagina a destra fornirà una descrizione del *Azure Application Insights* servizio.</span><span class="sxs-lookup"><span data-stu-id="a0547-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="a0547-159">AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="a0547-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="a0547-161">Dopo avere fatto clic su **Create**:</span><span class="sxs-lookup"><span data-stu-id="a0547-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="a0547-162">Inserire la posizione desiderata **nome** per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="a0547-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="a0547-163">Come **tipo di applicazione**, selezionare **generali**.</span><span class="sxs-lookup"><span data-stu-id="a0547-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="a0547-164">Selezionare un'opzione appropriata **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="a0547-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="a0547-165">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="a0547-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a0547-166">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="a0547-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a0547-167">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="a0547-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="a0547-168">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="a0547-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="a0547-169">Selezionare una **posizione**.</span><span class="sxs-lookup"><span data-stu-id="a0547-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="a0547-170">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="a0547-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="a0547-171">Selezionare **Create**.</span><span class="sxs-lookup"><span data-stu-id="a0547-171">Select **Create**.</span></span>

        ![Portale di Azure](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="a0547-173">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="a0547-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="a0547-174">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="a0547-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="a0547-176">Fare clic su notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="a0547-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="a0547-178">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="a0547-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="a0547-179">Si verrà indirizzati alla nuova *servizio di Application Insights* istanza.</span><span class="sxs-lookup"><span data-stu-id="a0547-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="a0547-181">Tenere aperta questa pagina web e facile accesso, verrà tornare qui frequenza con cui visualizzare i dati raccolti.</span><span class="sxs-lookup"><span data-stu-id="a0547-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a0547-182">Per implementare Application Insights, è necessario usare valori specifici di tre (3): **Chiave di strumentazione**, **ID applicazione**, e **chiave API**.</span><span class="sxs-lookup"><span data-stu-id="a0547-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="a0547-183">Di seguito si vedrà come recuperare questi valori dal servizio.</span><span class="sxs-lookup"><span data-stu-id="a0547-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="a0547-184">Assicurarsi di annotare questi valori in uno spazio vuoto *Notepad* pagina, perché verrà usato presto nel codice.</span><span class="sxs-lookup"><span data-stu-id="a0547-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="a0547-185">Per trovare il **chiave di strumentazione**, sarà necessario scorrere verso il basso l'elenco di funzioni del servizio e fare clic su **proprietà**, verrà visualizzate nella scheda visualizzata il **chiave del servizio**.</span><span class="sxs-lookup"><span data-stu-id="a0547-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="a0547-187">Un po' di seguito **delle proprietà**, si noterà **l'accesso all'API**, che è necessario fare clic su.</span><span class="sxs-lookup"><span data-stu-id="a0547-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="a0547-188">Il pannello a destra fornirà il **ID applicazione** dell'app.</span><span class="sxs-lookup"><span data-stu-id="a0547-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="a0547-190">Con il **ID applicazione** ancora aperto, fare clic su pannello **Crea chiave API**, che apre il *Crea chiave API* pannello.</span><span class="sxs-lookup"><span data-stu-id="a0547-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="a0547-192">Entro l'ora di apertura *Crea chiave API* panel, digitare una descrizione, e **selezionare le tre caselle**.</span><span class="sxs-lookup"><span data-stu-id="a0547-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="a0547-193">Fare clic su **Genera chiave**.</span><span class="sxs-lookup"><span data-stu-id="a0547-193">Click **Generate Key**.</span></span> <span data-ttu-id="a0547-194">I **chiave API** verranno creati e visualizzati.</span><span class="sxs-lookup"><span data-stu-id="a0547-194">Your **API Key** will be created and displayed.</span></span> 

    ![Portale di Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="a0547-196">Questa è l'unica volta le **chiave del servizio** verranno visualizzati, pertanto è necessario verificare ora eseguire una copia di esso.</span><span class="sxs-lookup"><span data-stu-id="a0547-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="a0547-197">Capitolo 2 - configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="a0547-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="a0547-198">Di seguito è una tipica configurato per lo sviluppo con la realtà mista e di conseguenza, è un buon modello per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="a0547-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="a0547-199">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="a0547-199">Open *Unity* and click **New**.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="a0547-201">A questo punto si dovrà fornire un nome di progetto Unity, inserire **MR\_Azure\_Application\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="a0547-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="a0547-202">Assicurarsi che il *modello* è impostata su **3D**.</span><span class="sxs-lookup"><span data-stu-id="a0547-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="a0547-203">Impostare il *posizione* a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="a0547-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="a0547-204">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="a0547-204">Then, click **Create project**.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="a0547-206">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a0547-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a0547-207">Passare a **modifica \> Preferences** e quindi dalla nuova finestra, passare al **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="a0547-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a0547-208">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a0547-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a0547-209">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="a0547-209">Close the **Preferences** window.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="a0547-211">Passare quindi ad **File \> Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.</span><span class="sxs-lookup"><span data-stu-id="a0547-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="a0547-213">Passare a **File \> Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="a0547-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="a0547-214">**Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="a0547-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="a0547-215">Per il Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="a0547-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="a0547-216">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="a0547-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="a0547-217">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="a0547-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="a0547-218">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="a0547-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="a0547-219">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="a0547-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="a0547-220">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="a0547-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="a0547-221">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="a0547-221">A save window will appear.</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="a0547-223">Creare una nuova cartella per questo e qualsiasi futura scena, quindi scegliere il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="a0547-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="a0547-225">Aprire appena creato **scene** cartella e quindi la *nome File:* campo di testo, digitare **ApplicationInsightsScene**, quindi fare clic su **salvare**.</span><span class="sxs-lookup"><span data-stu-id="a0547-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="a0547-227">Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="a0547-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="a0547-228">Nel **Build Settings** finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il **Inspector** si trova.</span><span class="sxs-lookup"><span data-stu-id="a0547-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="a0547-230">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="a0547-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="a0547-231">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="a0547-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="a0547-232">**Scripting** **versione Runtime** deve essere **Experimental (.NET 4.6 equivalente)** , che attiverà una necessità di riavviare l'Editor.</span><span class="sxs-lookup"><span data-stu-id="a0547-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="a0547-233">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="a0547-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="a0547-234">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="a0547-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Configurare il progetto Unity](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="a0547-236">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="a0547-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="a0547-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="a0547-237">**InternetClient**</span></span>     

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="a0547-239">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **le impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **realtà mista di Windows SDK** viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="a0547-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurare il progetto Unity](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="a0547-241">Nuovamente in **Build Settings**, **Unity C# progetti** non è più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="a0547-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="a0547-242">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="a0547-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="a0547-243">Salvare la scena e il progetto (**FILE** > **SAVE SCENE /file** > **Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="a0547-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="a0547-244">Capitolo 3 - Importa pacchetto Unity</span><span class="sxs-lookup"><span data-stu-id="a0547-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a0547-245">Se si vuole ignorare la *configurare Unity* componenti di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [MR-Azure-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importarlo nel progetto come un [ **Pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="a0547-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="a0547-246">Questa conterrà anche la DLL del capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="a0547-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="a0547-247">Al termine dell'importazione, sono la prosecuzione [ **capitolo 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="a0547-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a0547-248">Per usare Application Insights in Unity, è necessario importare il file DLL, con la DLL Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="a0547-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="a0547-249">È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="a0547-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="a0547-250">Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.</span><span class="sxs-lookup"><span data-stu-id="a0547-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="a0547-251">Per importare Application Insights in un progetto, assicurarsi di avere [scaricato il '.unitypackage', che contiene i plug-in](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="a0547-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="a0547-252">Quindi, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0547-252">Then, do the following:</span></span>

1.  <span data-ttu-id="a0547-253">Aggiungere il **.unitypackage** a Unity tramite il **asset \> Importa pacchetto \> pacchetto personalizzato** l'opzione di menu.</span><span class="sxs-lookup"><span data-stu-id="a0547-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="a0547-254">Nel **Importa pacchetto Unity** scatola viene, assicurarsi che tutto ciò che in (e tra cui) **plug-in** sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="a0547-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="a0547-256">Scegliere il **importazione** pulsante, per aggiungere elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="a0547-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="a0547-257">Passare al **Insights** cartella sotto **Plugins** nel progetto consente di visualizzare e selezionare il plug-in seguenti *solo*:</span><span class="sxs-lookup"><span data-stu-id="a0547-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="a0547-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="a0547-258">Microsoft.ApplicationInsights</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="a0547-260">Con questo *plug-in* selezionato, assicurarsi che **Any Platform** viene **deselezionata**, quindi verificare che **WSAPlayer** anche  **unchecked**, quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="a0547-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="a0547-261">Questa operazione consiste nel verificare che i file siano configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="a0547-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="a0547-263">Contrassegnare i plug-in simile al seguente, li configura per essere usato solo nell'Editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="a0547-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="a0547-264">Esistono un diverso set di DLL nella cartella WSA che verrà usato dopo che il progetto viene esportato da Unity.</span><span class="sxs-lookup"><span data-stu-id="a0547-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="a0547-265">Successivamente, è necessario aprire la **WSA** cartella, all'interno di **Insights** cartella.</span><span class="sxs-lookup"><span data-stu-id="a0547-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="a0547-266">Si noterà una copia dello stesso file che appena configurato.</span><span class="sxs-lookup"><span data-stu-id="a0547-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="a0547-267">Selezionare questo file e quindi nella finestra di ispezione, assicurarsi che **piattaforma Any** viene **deselezionata**, quindi verificare che **solo** **WSAPlayer** è **controllato**.</span><span class="sxs-lookup"><span data-stu-id="a0547-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="a0547-268">Fare clic su **Applica**.</span><span class="sxs-lookup"><span data-stu-id="a0547-268">Click **Apply**.</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="a0547-270">Ora devi seguire **i passaggi 4-6**, ma per il *Newtonsoft* plug-in invece.</span><span class="sxs-lookup"><span data-stu-id="a0547-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="a0547-271">Vedere la seguente schermata per la quale il risultato deve essere simile.</span><span class="sxs-lookup"><span data-stu-id="a0547-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="a0547-273">Capitolo 4 - configurare fotocamera e all'utente di controlli</span><span class="sxs-lookup"><span data-stu-id="a0547-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="a0547-274">In questo capitolo si configurerà il la fotocamera e i controlli per consentire all'utente di visualizzare e spostarsi nella scena.</span><span class="sxs-lookup"><span data-stu-id="a0547-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="a0547-275">Fare clic in un'area vuota nel Pannello di gerarchia, quindi su **Create** > **vuoto**.</span><span class="sxs-lookup"><span data-stu-id="a0547-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="a0547-277">Rinominare il nuovo GameObject vuoto al **fotocamera padre**.</span><span class="sxs-lookup"><span data-stu-id="a0547-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="a0547-279">Fare clic in un'area vuota nel Pannello di gerarchia, quindi su **oggetto 3D**, quindi su **sfera**.</span><span class="sxs-lookup"><span data-stu-id="a0547-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="a0547-280">Rinominare la sfera **a destra**.</span><span class="sxs-lookup"><span data-stu-id="a0547-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="a0547-281">Impostare il **trasformare Scale** della mano destra per **0.1, 0.1, 0.1**</span><span class="sxs-lookup"><span data-stu-id="a0547-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="a0547-283">Rimuovere il **sfera Collider** l'icona della mano destra, fare clic sul componente il **a forma di ingranaggio** nel *Collider sfera* componente e quindi **Rimuovi componente** .</span><span class="sxs-lookup"><span data-stu-id="a0547-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="a0547-285">Trascinare la gerarchia pannello il **Main Camera** e il **a destra** gli oggetti il **fotocamera padre** oggetto.</span><span class="sxs-lookup"><span data-stu-id="a0547-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="a0547-287">Impostare il **posizione trasformare** di entrambi il **Main Camera** e il **a destra** oggetto **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="a0547-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-31.png)

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="a0547-290">Capitolo 5: configurare gli oggetti nella scena Unity</span><span class="sxs-lookup"><span data-stu-id="a0547-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="a0547-291">Ora si creerà alcune forme di base per la scena, con cui l'utente può interagire.</span><span class="sxs-lookup"><span data-stu-id="a0547-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="a0547-292">Pulsante destro del mouse in un'area vuota nel *Pannello di gerarchia*, quindi nella **oggetto 3D**, quindi selezionare **piano**.</span><span class="sxs-lookup"><span data-stu-id="a0547-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="a0547-293">Impostare il piano **trasformare posizione** al **0, -1, 0**.</span><span class="sxs-lookup"><span data-stu-id="a0547-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="a0547-294">Impostare il piano **trasformare Scale** al **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="a0547-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="a0547-296">Creare un materiale base da usare con il **piano** dell'oggetto, in modo che le altre forme sono più facili da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="a0547-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="a0547-297">Passare al *pannello progetto*, destro del mouse e quindi **crea**, quindi su **cartella**, per creare una nuova cartella.</span><span class="sxs-lookup"><span data-stu-id="a0547-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="a0547-298">Denominarlo **materiali**.</span><span class="sxs-lookup"><span data-stu-id="a0547-298">Name it **Materials**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-34.png) ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="a0547-301">Aprire il **materiali** cartella, quindi viene scelta, fare clic su **Create**, quindi **materiale**, per creare un nuovo materiale.</span><span class="sxs-lookup"><span data-stu-id="a0547-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="a0547-302">Denominarlo **blu**.</span><span class="sxs-lookup"><span data-stu-id="a0547-302">Name it **Blue**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-36.png) ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="a0547-305">Con la nuova **blu** materiale selezionata, cercare nel *Inspector*e fare clic sulla finestra rettangolare insieme **Albedo**.</span><span class="sxs-lookup"><span data-stu-id="a0547-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="a0547-306">Selezionare un colore blu (un'immagine seguente è **colore esadecimale: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="a0547-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="a0547-307">Dopo aver selezionato, fare clic sul pulsante Chiudi.</span><span class="sxs-lookup"><span data-stu-id="a0547-307">Click the close button once you have chosen.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="a0547-309">Trascinare di nuovo materiale dal **materiali** cartella, nel appena creato **piano**, all'interno della scena (o rilasciarlo sul **piano** all'interno dell'oggetto di  *Gerarchia*).</span><span class="sxs-lookup"><span data-stu-id="a0547-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="a0547-311">Pulsante destro del mouse in un'area vuota nel *Pannello di gerarchia*, quindi nella **oggetto 3D, Capsule**.</span><span class="sxs-lookup"><span data-stu-id="a0547-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="a0547-312">Con il **Capsule** selezionato, modificare relativo **trasformare** *posizione* da: **-10, 0 e 1**.</span><span class="sxs-lookup"><span data-stu-id="a0547-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="a0547-313">Pulsante destro del mouse in un'area vuota nel *Pannello di gerarchia*, quindi nella **oggetto 3D, il cubo**.</span><span class="sxs-lookup"><span data-stu-id="a0547-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="a0547-314">Con il **cubo** selezionato, modificare relativo **trasformare** *posizione* per: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="a0547-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="a0547-315">Pulsante destro del mouse in un'area vuota nel *Pannello di gerarchia*, quindi nella **oggetto 3D, sfera**.</span><span class="sxs-lookup"><span data-stu-id="a0547-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="a0547-316">Con il **sfera** selezionato, modificare relativo **trasformare** *posizione* per: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="a0547-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="a0547-318">Questi *posizione* i valori sono *suggerimenti*.</span><span class="sxs-lookup"><span data-stu-id="a0547-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="a0547-319">Si è liberi di impostare le posizioni degli oggetti per qualsiasi elemento desiderato, ma è più semplice per l'utente dell'applicazione se le distanze di oggetti non troppo lontano dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="a0547-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="a0547-320">Quando l'applicazione è in esecuzione, deve essere in grado di identificare gli oggetti all'interno della scena, per ottenere questo risultato, devono essere contrassegnati.</span><span class="sxs-lookup"><span data-stu-id="a0547-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="a0547-321">Selezionare uno degli oggetti e nel *Inspector* del pannello, fare clic su **aggiungere Tag...** , che verrà scambiata il *Inspector* con il **tag & tutti i livelli di** pannello.</span><span class="sxs-lookup"><span data-stu-id="a0547-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="a0547-322">![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="a0547-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="a0547-323">Scegliere il **+ (segno più)** dei simboli, quindi digitare il nome del tag come **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="a0547-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="a0547-325">Se si usa un nome diverso per il tag, sarà necessario assicurarsi che questa modifica viene apportata anche il *DataFromAnalytics*, *ObjectTrigger*, e *estasiati*, gli script in un secondo momento, in modo che i gli oggetti vengono trovati e rilevati, all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="a0547-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="a0547-326">Con il tag creato, è necessario ora applicarlo a tutte e tre gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="a0547-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="a0547-327">Dal *gerarchia*, tenere premuto il **MAIUSC** chiave, quindi fare clic il **Capsule**, **cubo**, e **sfera**, gli oggetti, quindi nella *Inspector*, fare clic sul menu a discesa accanto **Tag**, quindi fare clic sui *ObjectInScene* tag creato.</span><span class="sxs-lookup"><span data-stu-id="a0547-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="a0547-328">![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="a0547-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="a0547-329">Capitolo 6: creare la classe ApplicationInsightsTracker</span><span class="sxs-lookup"><span data-stu-id="a0547-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="a0547-330">È il primo script da creare **ApplicationInsightsTracker**, che è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="a0547-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="a0547-331">Creazione di eventi in base alle interazioni dell'utente per inviare ad Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a0547-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="a0547-332">Creazione di nomi di eventi appropriati, a seconda di interazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a0547-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="a0547-333">Invio di eventi all'istanza del servizio Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a0547-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="a0547-334">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="a0547-334">To create this class:</span></span>

1.  <span data-ttu-id="a0547-335">Fare doppio clic nella *Pannello di progetto*, quindi **creare** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="a0547-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="a0547-336">Denominare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="a0547-336">Name the folder **Scripts**.</span></span>

    ![Creare la classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Creare la classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="a0547-339">Con il **script** cartella creata, fare doppio clic sopra per avviarlo.</span><span class="sxs-lookup"><span data-stu-id="a0547-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="a0547-340">Quindi, all'interno di tale cartella, pulsante destro del mouse, **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a0547-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="a0547-341">Denominare lo script **ApplicationInsightsTracker**.</span><span class="sxs-lookup"><span data-stu-id="a0547-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="a0547-342">Fare doppio clic su nuova **ApplicationInsightsTracker** script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a0547-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="a0547-343">Aggiornare gli spazi dei nomi nella parte superiore dello script sia come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="a0547-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="a0547-344">All'interno della classe inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0547-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="a0547-345">Impostare il **instrumentationKey, applicationId e API_Key** i valori in modo appropriato, usando la *le chiavi del servizio* dal portale di Azure come indicato nella [capitolo 1](#chapter-1---the-azure-portal), passaggio 9 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a0547-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="a0547-346">Quindi aggiungere il **Start ()** e **Awake()** metodi, che verranno chiamati quando si inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="a0547-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="a0547-347">Aggiungere i metodi responsabili per l'invio di eventi e metriche registrate dall'applicazione:</span><span class="sxs-lookup"><span data-stu-id="a0547-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="a0547-348">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a0547-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="a0547-349">Capitolo 7 - creare uno script di sguardo</span><span class="sxs-lookup"><span data-stu-id="a0547-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="a0547-350">Lo script successivo da creare è il **estasiati** script.</span><span class="sxs-lookup"><span data-stu-id="a0547-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="a0547-351">Questo script è responsabile della creazione di un *Raycast* che sarà proiettato in avanti dalle *Main Camera*, per rilevare l'oggetto sta guardando l'utente.</span><span class="sxs-lookup"><span data-stu-id="a0547-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="a0547-352">In questo caso, il *Raycast* sarà necessario identificare se l'utente è osservando un oggetto con il **ObjectInScene** tag e quindi contare quanto tempo l'utente *gazes* in quell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a0547-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="a0547-353">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="a0547-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a0547-354">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a0547-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a0547-355">Denominare lo script **estasiati**.</span><span class="sxs-lookup"><span data-stu-id="a0547-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="a0547-356">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0547-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="a0547-357">Sostituire il codice esistente con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a0547-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="a0547-358">Il codice per il **Awake()** e **Start ()** metodi deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="a0547-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="a0547-359">All'interno di **estasiati** classe, aggiungere il codice seguente nel **Update ()** metodo al progetto un *Raycast* e rilevare il calo di destinazione:</span><span class="sxs-lookup"><span data-stu-id="a0547-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="a0547-360">Aggiungere il **ResetFocusedObject()** metodo, per inviare dati a **Application Insights** quando l'utente ha esaminato da un oggetto.</span><span class="sxs-lookup"><span data-stu-id="a0547-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="a0547-361">È stata completata la **estasiati** script.</span><span class="sxs-lookup"><span data-stu-id="a0547-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="a0547-362">Salvare le modifiche nel *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a0547-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="a0547-363">Capitolo 8 - creare la classe ObjectTrigger</span><span class="sxs-lookup"><span data-stu-id="a0547-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="a0547-364">Lo script successivo, è necessario creare sia **ObjectTrigger**, che è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="a0547-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="a0547-365">Aggiunta di componenti necessari per la collisione alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="a0547-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="a0547-366">Rilevare se la fotocamera si avvicina un oggetto contrassegnato come **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="a0547-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="a0547-367">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="a0547-367">To create the script:</span></span>

1.  <span data-ttu-id="a0547-368">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="a0547-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a0547-369">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a0547-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a0547-370">Denominare lo script **ObjectTrigger**.</span><span class="sxs-lookup"><span data-stu-id="a0547-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="a0547-371">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0547-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="a0547-372">Sostituire il codice esistente con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a0547-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="a0547-373">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a0547-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="a0547-374">Capitolo 9 - creare la classe DataFromAnalytics</span><span class="sxs-lookup"><span data-stu-id="a0547-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="a0547-375">È ora necessario creare il **DataFromAnalytics** script, che è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="a0547-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="a0547-376">Durante il recupero dei dati di analitica intorno al quale oggetto è stato affrontato dalla fotocamera più.</span><span class="sxs-lookup"><span data-stu-id="a0547-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="a0547-377">Usando il *le chiavi del servizio*, che consentono la comunicazione con l'istanza del servizio di Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a0547-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="a0547-378">Ordinare gli oggetti nella scena, in base ai quali ha il maggior numero di eventi.</span><span class="sxs-lookup"><span data-stu-id="a0547-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="a0547-379">Modifica il colore del materiale, dell'oggetto più approached, a *verde*.</span><span class="sxs-lookup"><span data-stu-id="a0547-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="a0547-380">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="a0547-380">To create the script:</span></span>

1.  <span data-ttu-id="a0547-381">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="a0547-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a0547-382">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a0547-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a0547-383">Denominare lo script **DataFromAnalytics**.</span><span class="sxs-lookup"><span data-stu-id="a0547-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="a0547-384">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0547-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="a0547-385">Inserisci gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0547-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="a0547-386">Nello script, inserire gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="a0547-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="a0547-387">All'interno del **DataFromAnalytics** classi, pulsante destro del mouse dopo il **Start ()** metodo, aggiungere il seguente metodo chiamato **FetchAnalytics()** .</span><span class="sxs-lookup"><span data-stu-id="a0547-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="a0547-388">Questo metodo è responsabile della compilazione dell'elenco di coppie chiave-valore, con un *GameObject* e un numero di conteggio di eventi di segnaposto.</span><span class="sxs-lookup"><span data-stu-id="a0547-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="a0547-389">Vengono quindi inizializzate le **GetWebRequest()** coroutine.</span><span class="sxs-lookup"><span data-stu-id="a0547-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="a0547-390">La struttura della query della chiamata a *Application Insights* sono disponibili all'interno di questo metodo, inoltre, come le *URL della Query* endpoint.</span><span class="sxs-lookup"><span data-stu-id="a0547-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="a0547-391">Sotto il **FetchAnalytics()** metodo, aggiungere un metodo denominato **GetWebRequest()** , che restituisce un' *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="a0547-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="a0547-392">Questo metodo è responsabile che richiede il numero di volte in cui un evento, corrispondente a uno specifico *GameObject*, è stato chiamato all'interno *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="a0547-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="a0547-393">Quando tutte le query inviate hanno restituito, il **DetermineWinner()** viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="a0547-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="a0547-394">Il metodo successivo viene **DetermineWinner()** , che consente di ordinare l'elenco dei *GameObject* e *Int* coppie, in base al maggior numero di eventi.</span><span class="sxs-lookup"><span data-stu-id="a0547-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="a0547-395">Viene quindi modificato il colore del materiale di tale *GameObject* al *verde* (come commenti e suggerimenti per tale necessità il numero più alto).</span><span class="sxs-lookup"><span data-stu-id="a0547-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="a0547-396">Ciò consente di visualizzare un messaggio con i risultati di analitica.</span><span class="sxs-lookup"><span data-stu-id="a0547-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="a0547-397">Aggiungere la struttura della classe che verrà usata per deserializzare l'oggetto JSON, ricevuto dal *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="a0547-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="a0547-398">Aggiungere queste classi nella parte inferiore dei **DataFromAnalytics** file di classe **di fuori** della definizione di classe.</span><span class="sxs-lookup"><span data-stu-id="a0547-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="a0547-399">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a0547-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="a0547-400">Capitolo 10 - creare la classe di movimento</span><span class="sxs-lookup"><span data-stu-id="a0547-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="a0547-401">Il **movimento** script è lo script successivo sarà necessario creare.</span><span class="sxs-lookup"><span data-stu-id="a0547-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="a0547-402">È responsabile per:</span><span class="sxs-lookup"><span data-stu-id="a0547-402">It is responsible for:</span></span>

- <span data-ttu-id="a0547-403">Spostamento della videocamera Main in base alla direzione della fotocamera esegue la ricerca nei confronti.</span><span class="sxs-lookup"><span data-stu-id="a0547-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="a0547-404">Aggiunta di tutti gli altri script per gli oggetti di scena.</span><span class="sxs-lookup"><span data-stu-id="a0547-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="a0547-405">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="a0547-405">To create the script:</span></span>

1.  <span data-ttu-id="a0547-406">Fare doppio clic sulla **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="a0547-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a0547-407">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a0547-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a0547-408">Denominare lo script **movimento**.</span><span class="sxs-lookup"><span data-stu-id="a0547-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="a0547-409">Fare doppio clic su script per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="a0547-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="a0547-410">Sostituire il codice esistente con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a0547-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="a0547-411">All'interno di **lo spostamento dei** (classe), *seguito* vuoto **Update ()** metodo, inserire i metodi seguenti che consentono di usare il controller manualmente per spostare in uno spazio virtuale:</span><span class="sxs-lookup"><span data-stu-id="a0547-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="a0547-412">Aggiungere infine la chiamata di metodo all'interno di **Update ()** (metodo).</span><span class="sxs-lookup"><span data-stu-id="a0547-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="a0547-413">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a0547-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="a0547-414">Capitolo 11 - configurazione i riferimenti di script</span><span class="sxs-lookup"><span data-stu-id="a0547-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="a0547-415">In questo capitolo è necessario inserire il **lo spostamento dei** nello script il **fotocamera padre** e impostare le destinazioni di riferimento.</span><span class="sxs-lookup"><span data-stu-id="a0547-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="a0547-416">Lo script gestirà quindi l'inserimento altri script in cui devono essere.</span><span class="sxs-lookup"><span data-stu-id="a0547-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="a0547-417">Dal **gli script** cartella nel *pannello progetto*, trascinare il **lo spostamento dei** generare uno script per il **fotocamera padre** oggetto, che si trova nel  *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="a0547-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Impostare i riferimenti di script nella scena Unity](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="a0547-419">Fare clic sui **fotocamera padre**.</span><span class="sxs-lookup"><span data-stu-id="a0547-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="a0547-420">Nel *pannello gerarchia*, trascinare il **a destra** dall'oggetto il *gerarchia pannello* alla destinazione di riferimento, **Controller**, nella *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="a0547-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="a0547-421">Impostare il **utente velocità** al **5**, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="a0547-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Impostare i riferimenti di script nella scena Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="a0547-423">Capitolo 12 - compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="a0547-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="a0547-424">Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.</span><span class="sxs-lookup"><span data-stu-id="a0547-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="a0547-425">Passare a **impostazioni di compilazione**, (**File** > **impostazioni di compilazione**).</span><span class="sxs-lookup"><span data-stu-id="a0547-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="a0547-426">Dal **Build Settings** finestra, fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="a0547-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilare il progetto Unity alla soluzione di piattaforma UWP](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="a0547-428">Oggetto **Esplora File** finestra will popup, cui è possibile specificare un percorso per la compilazione.</span><span class="sxs-lookup"><span data-stu-id="a0547-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="a0547-429">Creare una nuova cartella (facendo **nuova cartella** nell'angolo superiore sinistro) e denominarla **COMPILA**.</span><span class="sxs-lookup"><span data-stu-id="a0547-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Compilare il progetto Unity alla soluzione di piattaforma UWP](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="a0547-431">Aprire il nuovo **si basa** cartella e creare un'altra cartella (utilizzando **nuova cartella** ancora una volta) e denominarlo **MR\_Azure\_applicazione\_ Insights**.</span><span class="sxs-lookup"><span data-stu-id="a0547-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Compilare il progetto Unity alla soluzione di piattaforma UWP](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="a0547-433">Con il **MR\_Azure\_Application\_Insights** cartella selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="a0547-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="a0547-434">Il progetto avrà un minuto alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="a0547-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="a0547-435">Seguendo *compilare*, **Esplora File** apparirà mostrano la posizione del nuovo progetto.</span><span class="sxs-lookup"><span data-stu-id="a0547-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="a0547-436">Capitolo 13 - distribuire app MR_Azure_Application_Insights in un computer</span><span class="sxs-lookup"><span data-stu-id="a0547-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="a0547-437">Per distribuire il **MR\_Azure\_Application\_Insights** app nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="a0547-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="a0547-438">Aprire il file della soluzione delle **MR\_Azure\_Application\_Insights** in app **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a0547-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="a0547-439">Nel **piattaforma soluzione**, selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="a0547-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="a0547-440">Nel **configurazione della soluzione** selezionate **Debug**.</span><span class="sxs-lookup"><span data-stu-id="a0547-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Compilare il progetto Unity alla soluzione di piattaforma UWP](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="a0547-442">Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.</span><span class="sxs-lookup"><span data-stu-id="a0547-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="a0547-443">L'app deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="a0547-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="a0547-444">Avviare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a0547-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="a0547-445">Spostare la scena, per raggiungere gli oggetti e analizzando, quando la *servizio di Azure Insights* abbia raccolto abbastanza dati evento, imposterà l'oggetto che è stato affrontato al meglio su verde.</span><span class="sxs-lookup"><span data-stu-id="a0547-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="a0547-446">Mentre il tempo medio di attesa per il *metriche ed eventi* a essere raccolte dal servizio richiede circa 15 minuti, in alcuni casi potrebbe richiedere fino a 1 ora.</span><span class="sxs-lookup"><span data-stu-id="a0547-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="a0547-447">Capitolo 14 - portale di Application Insights Service</span><span class="sxs-lookup"><span data-stu-id="a0547-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="a0547-448">Dopo che in roaming intorno scena e gazed in diversi oggetti è possibile visualizzare i dati raccolti nel *servizio di Application Insights* portale.</span><span class="sxs-lookup"><span data-stu-id="a0547-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="a0547-449">Tornare al portale del servizio Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a0547-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="a0547-450">Fare clic su *Esplora metriche*.</span><span class="sxs-lookup"><span data-stu-id="a0547-450">Click on *Metrics Explorer*.</span></span>

    ![Esaminando i dati raccolti](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="a0547-452">Verrà aperto in una scheda che contiene il grafico che rappresenta il *metriche ed eventi* relative all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a0547-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="a0547-453">Come indicato in precedenza, potrebbe richiedere tempo (fino a 1 ora) per i dati da visualizzare nel grafico</span><span class="sxs-lookup"><span data-stu-id="a0547-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Esaminando i dati raccolti](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="a0547-455">Fare clic sul *sulla barra degli eventi* nel *totale di eventi* dalla versione dell'applicazione, per visualizzare una suddivisione dettagliata degli eventi con i relativi nomi.</span><span class="sxs-lookup"><span data-stu-id="a0547-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Esaminando i dati raccolti](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="a0547-457">Il termine l'applicazione di servizio di Application Insights</span><span class="sxs-lookup"><span data-stu-id="a0547-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="a0547-458">Complimenti, è stata compilata un'app per realtà mista che sfrutta il servizio Application Insights per monitorare l'attività dell'utente all'interno dell'app.</span><span class="sxs-lookup"><span data-stu-id="a0547-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![risultato del corso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="a0547-460">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="a0547-460">Bonus Exercises</span></span>

<span data-ttu-id="a0547-461">**Esercizio 1**</span><span class="sxs-lookup"><span data-stu-id="a0547-461">**Exercise 1**</span></span>

<span data-ttu-id="a0547-462">Provare a generazione, anziché creare manualmente gli oggetti ObjectInScene e impostare le coordinate sul piano all'interno degli script.</span><span class="sxs-lookup"><span data-stu-id="a0547-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="a0547-463">In questo modo, si può chiedere Azure quali l'oggetto più diffuso era (sia dai risultati sguardo o prossimità) e generare una *extra* uno di questi oggetti.</span><span class="sxs-lookup"><span data-stu-id="a0547-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="a0547-464">**Esercizio 2**</span><span class="sxs-lookup"><span data-stu-id="a0547-464">**Exercise 2**</span></span>

<span data-ttu-id="a0547-465">Per ordinare i risultati di Application Insights ora, in modo da ottenere i dati più rilevanti e implementare tali dati sensibili di tempo nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a0547-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

