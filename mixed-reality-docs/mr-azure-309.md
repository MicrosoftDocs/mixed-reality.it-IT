---
title: MR e Azure 309-Application Insights
description: Completare questo corso per informazioni su come raccogliere i dati analitici sul comportamento dell'utente all'interno di un'applicazione di realtà mista usando il servizio applicazione Azure Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, Application Insights, hololens, immersive, VR
ms.openlocfilehash: 481fe3fc16ada06085a64c86867a1a892c76f2ad
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926894"
---
>[!NOTE]
><span data-ttu-id="b1675-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b1675-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b1675-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="b1675-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b1675-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b1675-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b1675-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="b1675-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b1675-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b1675-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b1675-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="b1675-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="b1675-110">MR e Azure 309: Application Insights</span><span class="sxs-lookup"><span data-stu-id="b1675-110">MR and Azure 309: Application insights</span></span>

![prodotto finale-inizio](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="b1675-112">In questo corso si apprenderà come aggiungere Application Insights funzionalità a un'applicazione di realtà mista usando l'API applicazione Azure Insights per raccogliere le analisi relative al comportamento degli utenti.</span><span class="sxs-lookup"><span data-stu-id="b1675-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="b1675-113">Application Insights è un servizio Microsoft, che consente agli sviluppatori di raccogliere le analisi dalle applicazioni e di gestirle da un portale di facile utilizzo.</span><span class="sxs-lookup"><span data-stu-id="b1675-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="b1675-114">L'analisi può essere di qualsiasi tipo, dalle prestazioni alle informazioni personalizzate da raccogliere.</span><span class="sxs-lookup"><span data-stu-id="b1675-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="b1675-115">Per ulteriori informazioni, visitare la [pagina Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="b1675-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="b1675-116">Dopo aver completato questo corso, si disporrà di un'applicazione con un auricolare immersiva a realtà mista che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1675-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="b1675-117">Consente all'utente di guardare e spostarsi in una scena.</span><span class="sxs-lookup"><span data-stu-id="b1675-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="b1675-118">Attivare l'invio di analisi al *servizio Application Insights*, tramite l'uso di sguardi e prossimità di oggetti in scena.</span><span class="sxs-lookup"><span data-stu-id="b1675-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="b1675-119">L'app chiamerà anche il servizio, recuperando le informazioni sull'oggetto che è stato più o meno affrontato dall'utente nelle ultime 24 ore.</span><span class="sxs-lookup"><span data-stu-id="b1675-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="b1675-120">Tale oggetto cambierà il colore in verde.</span><span class="sxs-lookup"><span data-stu-id="b1675-120">That object will change its color to green.</span></span>

<span data-ttu-id="b1675-121">Questo corso spiegherà come ottenere i risultati dal servizio Application Insights in un'applicazione di esempio basata su Unity.</span><span class="sxs-lookup"><span data-stu-id="b1675-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="b1675-122">Sarà necessario applicare questi concetti a un'applicazione personalizzata che è possibile creare.</span><span class="sxs-lookup"><span data-stu-id="b1675-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="b1675-123">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="b1675-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b1675-124">Corso</span><span class="sxs-lookup"><span data-stu-id="b1675-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b1675-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b1675-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b1675-126"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="b1675-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b1675-127">MR e Azure 309: Application Insights</span><span class="sxs-lookup"><span data-stu-id="b1675-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="b1675-128">✔️</span><span class="sxs-lookup"><span data-stu-id="b1675-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b1675-129">✔️</span><span class="sxs-lookup"><span data-stu-id="b1675-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b1675-130">Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b1675-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="b1675-131">Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b1675-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="b1675-132">Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.</span><span class="sxs-lookup"><span data-stu-id="b1675-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1675-133">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="b1675-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b1675-134">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e.</span><span class="sxs-lookup"><span data-stu-id="b1675-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b1675-135">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="b1675-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="b1675-136">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="b1675-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="b1675-137">Per questo corso è consigliabile usare i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1675-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b1675-138">Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="b1675-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b1675-139">Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="b1675-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b1675-140">Windows 10 SDK più recente</span><span class="sxs-lookup"><span data-stu-id="b1675-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b1675-141">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="b1675-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b1675-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b1675-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b1675-143">Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata</span><span class="sxs-lookup"><span data-stu-id="b1675-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b1675-144">Un set di cuffie con un microfono incorporato (se la cuffia non dispone di un MIC e di altoparlanti predefiniti)</span><span class="sxs-lookup"><span data-stu-id="b1675-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="b1675-145">Accesso a Internet per il programma di installazione di Azure e Application Insights il recupero dei dati</span><span class="sxs-lookup"><span data-stu-id="b1675-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b1675-146">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="b1675-146">Before you start</span></span>

<span data-ttu-id="b1675-147">Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="b1675-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="b1675-148">Tenere presente che i dati che passano a *Application Insights* richiedono tempo, quindi possono essere pazienti.</span><span class="sxs-lookup"><span data-stu-id="b1675-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="b1675-149">Se si vuole controllare se il servizio ha ricevuto i dati, vedere il [capitolo 14](#chapter-14---the-application-insights-service-portal), che illustra come spostarsi nel portale.</span><span class="sxs-lookup"><span data-stu-id="b1675-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="b1675-150">Capitolo 1-portale di Azure</span><span class="sxs-lookup"><span data-stu-id="b1675-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="b1675-151">Per usare *Application Insights*, è necessario creare e configurare un servizio di *Application Insights* nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="b1675-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="b1675-152">Accedere al portale di [Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="b1675-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b1675-153">Se non si dispone già di un account Azure, sarà necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="b1675-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b1675-154">Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="b1675-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="b1675-155">Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *Application Insights*e premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="b1675-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b1675-156">La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.</span><span class="sxs-lookup"><span data-stu-id="b1675-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="b1675-158">La nuova pagina a destra fornirà una descrizione del servizio *applicazione Azure Insights* .</span><span class="sxs-lookup"><span data-stu-id="b1675-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="b1675-159">Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="b1675-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="b1675-161">Una volta fatto clic su **Crea**:</span><span class="sxs-lookup"><span data-stu-id="b1675-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="b1675-162">Inserire il **nome** desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="b1675-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="b1675-163">In **tipo di applicazione**selezionare **generale**.</span><span class="sxs-lookup"><span data-stu-id="b1675-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="b1675-164">Selezionare una **sottoscrizione**appropriata.</span><span class="sxs-lookup"><span data-stu-id="b1675-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="b1675-165">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="b1675-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b1675-166">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="b1675-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b1675-167">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="b1675-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="b1675-168">Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="b1675-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="b1675-169">Selezionare una **località**.</span><span class="sxs-lookup"><span data-stu-id="b1675-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="b1675-170">Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="b1675-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="b1675-171">Seleziona **Crea**.</span><span class="sxs-lookup"><span data-stu-id="b1675-171">Select **Create**.</span></span>

        ![Portale di Azure](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="b1675-173">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="b1675-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="b1675-174">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="b1675-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="b1675-176">Fare clic sulle notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="b1675-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="b1675-178">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="b1675-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b1675-179">Si verrà portati alla nuova istanza del *servizio Application Insights* .</span><span class="sxs-lookup"><span data-stu-id="b1675-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="b1675-181">Questa pagina Web è aperta e facile da accedere. si tornerà spesso a visualizzare i dati raccolti.</span><span class="sxs-lookup"><span data-stu-id="b1675-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b1675-182">Per implementare Application Insights, sarà necessario usare tre (3) valori specifici: chiave di **strumentazione**, **ID applicazione**e **chiave API**.</span><span class="sxs-lookup"><span data-stu-id="b1675-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="b1675-183">Di seguito viene illustrato come recuperare questi valori dal servizio.</span><span class="sxs-lookup"><span data-stu-id="b1675-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="b1675-184">Assicurarsi di prendere nota di questi valori in una pagina del *blocco note* vuota, perché saranno presto usati nel codice.</span><span class="sxs-lookup"><span data-stu-id="b1675-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="b1675-185">Per trovare la **chiave di strumentazione**, è necessario scorrere verso il basso l'elenco di funzioni del servizio e fare clic su **Proprietà**. la scheda visualizzata mostrerà la **chiave del servizio**.</span><span class="sxs-lookup"><span data-stu-id="b1675-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="b1675-187">Di seguito sono riportate alcune **Proprietà**che consentono di **accedere all'API**, che è necessario fare clic su.</span><span class="sxs-lookup"><span data-stu-id="b1675-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="b1675-188">Il pannello a destra fornirà l' **ID applicazione** dell'app.</span><span class="sxs-lookup"><span data-stu-id="b1675-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="b1675-190">Con il pannello **ID applicazione** ancora aperto, fare clic su **Crea chiave API**, che consente di aprire il pannello *Crea chiave API* .</span><span class="sxs-lookup"><span data-stu-id="b1675-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Portale di Azure](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="b1675-192">All'interno del pannello Apri *chiave API crea* Digitare una descrizione e quindi **le tre caselle**.</span><span class="sxs-lookup"><span data-stu-id="b1675-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="b1675-193">Fare clic su **Genera chiave**.</span><span class="sxs-lookup"><span data-stu-id="b1675-193">Click **Generate Key**.</span></span> <span data-ttu-id="b1675-194">La **chiave API** verrà creata e visualizzata.</span><span class="sxs-lookup"><span data-stu-id="b1675-194">Your **API Key** will be created and displayed.</span></span> 

    ![Portale di Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="b1675-196">Questa è l'unica volta in cui verrà visualizzata la **chiave del servizio** , quindi assicurarsi di crearne una copia adesso.</span><span class="sxs-lookup"><span data-stu-id="b1675-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="b1675-197">Capitolo 2: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="b1675-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="b1675-198">Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, un modello valido per altri progetti.</span><span class="sxs-lookup"><span data-stu-id="b1675-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b1675-199">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="b1675-199">Open *Unity* and click **New**.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="b1675-201">A questo punto è necessario specificare un nome di progetto Unity, inserire **MR\_Azure\_Application\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="b1675-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="b1675-202">Verificare che il *modello* sia impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="b1675-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="b1675-203">Impostare il *percorso* su un punto appropriato (ricordare che più vicino alle directory radice è migliore).</span><span class="sxs-lookup"><span data-stu-id="b1675-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b1675-204">Fare quindi clic su **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="b1675-204">Then, click **Create project**.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="b1675-206">Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b1675-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b1675-207">Passare a **Modifica preferenze \>** e quindi dalla nuova finestra passare a **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="b1675-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b1675-208">Modificare l' **editor di script esterno** in **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="b1675-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b1675-209">Chiudere la finestra delle **Preferenze** .</span><span class="sxs-lookup"><span data-stu-id="b1675-209">Close the **Preferences** window.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="b1675-211">Passare quindi a **File \> impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .</span><span class="sxs-lookup"><span data-stu-id="b1675-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="b1675-213">Passare a **File \> impostazioni di compilazione** e verificare che:</span><span class="sxs-lookup"><span data-stu-id="b1675-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="b1675-214">Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**</span><span class="sxs-lookup"><span data-stu-id="b1675-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="b1675-215">Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="b1675-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="b1675-216">Il **tipo di compilazione** è impostato su **D3D**</span><span class="sxs-lookup"><span data-stu-id="b1675-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="b1675-217">**SDK** è impostato sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="b1675-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="b1675-218">**Compilazione ed esecuzione** è impostato su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="b1675-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="b1675-219">Salvare la scena e aggiungerla alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="b1675-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="b1675-220">A tale scopo, selezionare **Aggiungi scene aperte**.</span><span class="sxs-lookup"><span data-stu-id="b1675-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b1675-221">Verrà visualizzata una finestra Salva.</span><span class="sxs-lookup"><span data-stu-id="b1675-221">A save window will appear.</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="b1675-223">Creare una nuova cartella per questo e qualsiasi scena futura, quindi fare clic sul pulsante **nuova cartella** per creare una nuova cartella, denominarla **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="b1675-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="b1675-225">Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file:* testo digitare **ApplicationInsightsScene**e quindi fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="b1675-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="b1675-227">Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.</span><span class="sxs-lookup"><span data-stu-id="b1675-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="b1675-228">Nella finestra **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .</span><span class="sxs-lookup"><span data-stu-id="b1675-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="b1675-230">In questo pannello è necessario verificare alcune impostazioni:</span><span class="sxs-lookup"><span data-stu-id="b1675-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="b1675-231">Nella scheda **altre impostazioni** :</span><span class="sxs-lookup"><span data-stu-id="b1675-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="b1675-232">La **versione di runtime** di **Scripting** deve essere **sperimentale (equivalente a .NET 4,6)** , che attiverà la necessità di riavviare l'editor.</span><span class="sxs-lookup"><span data-stu-id="b1675-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="b1675-233">Il **back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="b1675-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="b1675-234">Il **livello di compatibilità API** deve essere **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="b1675-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Configurare il progetto Unity](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="b1675-236">Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:</span><span class="sxs-lookup"><span data-stu-id="b1675-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="b1675-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b1675-237">**InternetClient**</span></span>     

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="b1675-239">Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .</span><span class="sxs-lookup"><span data-stu-id="b1675-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurare il progetto Unity](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="b1675-241">Nelle **impostazioni di compilazione**, **i C# progetti Unity** non sono più disattivati; Selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="b1675-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="b1675-242">Chiudere la finestra impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="b1675-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="b1675-243">Salvare la scena e il progetto (**file** > **Salva scena/file** > **Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="b1675-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="b1675-244">Capitolo 3: importare il pacchetto Unity</span><span class="sxs-lookup"><span data-stu-id="b1675-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1675-245">Se si vuole ignorare i componenti di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile scaricare questo [Azure-Mr-309. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)e importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="b1675-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="b1675-246">Questo conterrà anche le dll del capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="b1675-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="b1675-247">Dopo l'importazione, continuare con il [**capitolo 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="b1675-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1675-248">Per usare Application Insights in Unity, è necessario importare la DLL, insieme alla DLL Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="b1675-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="b1675-249">Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione.</span><span class="sxs-lookup"><span data-stu-id="b1675-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="b1675-250">Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.</span><span class="sxs-lookup"><span data-stu-id="b1675-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="b1675-251">Per importare Application Insights nel progetto, assicurarsi di aver [scaricato il '. file unitypackage Tools ', contenente i plug](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)-in.</span><span class="sxs-lookup"><span data-stu-id="b1675-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="b1675-252">Eseguire quindi le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1675-252">Then, do the following:</span></span>

1.  <span data-ttu-id="b1675-253">Aggiungere il **file unitypackage Tools** a Unity usando l'opzione di menu **Asset \> importa pacchetto \> pacchetto personalizzato** .</span><span class="sxs-lookup"><span data-stu-id="b1675-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="b1675-254">Nella casella **Importa pacchetto Unity** visualizzata verificare che siano selezionati tutti gli elementi in (e inclusi) **plug** -in.</span><span class="sxs-lookup"><span data-stu-id="b1675-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="b1675-256">Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.</span><span class="sxs-lookup"><span data-stu-id="b1675-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="b1675-257">Passare alla cartella **Insights** in **plug** -in nella visualizzazione del progetto e selezionare *solo*i plug-in seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1675-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="b1675-258">Microsoft. ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="b1675-258">Microsoft.ApplicationInsights</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="b1675-260">Con questo *plug* -in selezionato, verificare che **qualsiasi piattaforma** sia **deselezionata**, quindi assicurarsi che **WSAPlayer** sia **deselezionata**, quindi fare clic su **applica**.</span><span class="sxs-lookup"><span data-stu-id="b1675-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="b1675-261">Questa operazione è sufficiente per confermare che i file sono configurati correttamente.</span><span class="sxs-lookup"><span data-stu-id="b1675-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="b1675-263">Contrassegnando i plug-in come questo, questi vengono configurati per essere usati solo nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="b1675-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="b1675-264">Nella cartella WSA è presente un set di dll diverso che verrà usato dopo l'esportazione del progetto da Unity.</span><span class="sxs-lookup"><span data-stu-id="b1675-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="b1675-265">Successivamente, è necessario aprire la cartella **WSA** , all'interno della cartella **Insights** .</span><span class="sxs-lookup"><span data-stu-id="b1675-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="b1675-266">Viene visualizzata una copia dello stesso file appena configurato.</span><span class="sxs-lookup"><span data-stu-id="b1675-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="b1675-267">Selezionare questo file, quindi nel controllo verificare che **qualsiasi piattaforma** sia **deselezionata**, quindi assicurarsi che sia **selezionato** **solo** **WSAPlayer** .</span><span class="sxs-lookup"><span data-stu-id="b1675-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="b1675-268">Fai clic su **Applica**.</span><span class="sxs-lookup"><span data-stu-id="b1675-268">Click **Apply**.</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="b1675-270">A questo punto, è necessario seguire i **passaggi 4-6**, ma per i plug-in *Newtonsoft* .</span><span class="sxs-lookup"><span data-stu-id="b1675-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="b1675-271">Vedere lo screenshot seguente per il risultato dell'aspetto.</span><span class="sxs-lookup"><span data-stu-id="b1675-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="b1675-273">Capitolo 4: impostare la fotocamera e i controlli utente</span><span class="sxs-lookup"><span data-stu-id="b1675-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="b1675-274">In questo capitolo verrà illustrato come configurare la fotocamera e i controlli per consentire all'utente di visualizzare e spostare la scena.</span><span class="sxs-lookup"><span data-stu-id="b1675-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="b1675-275">Fare clic con il pulsante destro del mouse in un'area vuota nel pannello gerarchia e quindi su **crea** > **vuoto**.</span><span class="sxs-lookup"><span data-stu-id="b1675-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="b1675-277">Rinominare il nuovo GameObject vuoto nell' **elemento padre della fotocamera**.</span><span class="sxs-lookup"><span data-stu-id="b1675-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="b1675-279">Fare clic con il pulsante destro del mouse in un'area vuota nel pannello gerarchia, quindi su **oggetto 3D**, quindi su **sfera**.</span><span class="sxs-lookup"><span data-stu-id="b1675-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="b1675-280">Rinominare la sfera nella **parte destra**.</span><span class="sxs-lookup"><span data-stu-id="b1675-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="b1675-281">Imposta la **scala di trasformazione** della mano destra su **0,1, 0,1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="b1675-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="b1675-283">Rimuovere il componente **Sphere Collider** dalla destra facendo clic sull' **ingranaggio** nel componente *Sphere Collider* , quindi **rimuovere Component**.</span><span class="sxs-lookup"><span data-stu-id="b1675-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="b1675-285">Nel pannello gerarchia trascinare la **fotocamera principale** e gli oggetti **destro** nell'oggetto padre della **fotocamera** .</span><span class="sxs-lookup"><span data-stu-id="b1675-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="b1675-287">Impostare la **posizione di trasformazione** della **fotocamera principale** e dell'oggetto **destro** su **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="b1675-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-31.png)

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="b1675-290">Capitolo 5: configurare gli oggetti nella scena Unity</span><span class="sxs-lookup"><span data-stu-id="b1675-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="b1675-291">Verranno ora create alcune forme di base per la scena, con cui l'utente può interagire.</span><span class="sxs-lookup"><span data-stu-id="b1675-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="b1675-292">Fare clic con il pulsante destro del mouse in un'area vuota nel *Pannello gerarchia*, quindi su **oggetto 3D**, quindi selezionare **piano**.</span><span class="sxs-lookup"><span data-stu-id="b1675-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="b1675-293">Impostare la **posizione di trasformazione** del piano su **0,-1, 0**.</span><span class="sxs-lookup"><span data-stu-id="b1675-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="b1675-294">Impostare **scala trasformazione** piano su **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="b1675-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="b1675-296">Creare un materiale di base da usare con l'oggetto **piano** , in modo che le altre forme siano più semplici da vedere.</span><span class="sxs-lookup"><span data-stu-id="b1675-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="b1675-297">Passare al *Pannello del progetto*, fare clic con il pulsante destro del mouse, quindi scegliere **Crea**, seguito da **cartella**, per creare una nuova cartella.</span><span class="sxs-lookup"><span data-stu-id="b1675-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="b1675-298">Assegnare un nome ai **materiali**.</span><span class="sxs-lookup"><span data-stu-id="b1675-298">Name it **Materials**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-34.png) ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="b1675-301">Aprire la cartella **Materials** , quindi fare clic con il pulsante destro del mouse, scegliere **Crea**, quindi **Material**, per creare un nuovo materiale.</span><span class="sxs-lookup"><span data-stu-id="b1675-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="b1675-302">Denominarlo **blu**.</span><span class="sxs-lookup"><span data-stu-id="b1675-302">Name it **Blue**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-36.png) ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="b1675-305">Con il nuovo materiale **blu** selezionato, esaminare il *controllo*e fare clic sulla finestra rettangolare accanto a **albedo**.</span><span class="sxs-lookup"><span data-stu-id="b1675-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="b1675-306">Selezionare un colore blu (l'immagine seguente è il **colore esadecimale: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="b1675-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="b1675-307">Una volta scelto, fare clic sul pulsante Chiudi.</span><span class="sxs-lookup"><span data-stu-id="b1675-307">Click the close button once you have chosen.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="b1675-309">Trascinare il nuovo materiale dalla cartella **Materials** , nel **piano**appena creato, all'interno della scena o rilasciarlo sull'oggetto **piano** all'interno della *gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="b1675-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="b1675-311">Fare clic con il pulsante destro del mouse in un'area vuota nel *Pannello gerarchia*, quindi su **oggetto 3D, capsula**.</span><span class="sxs-lookup"><span data-stu-id="b1675-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="b1675-312">Con la **capsula** selezionata, modificare la *posizione* di trasformazione in: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="b1675-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="b1675-313">Fare clic con il pulsante destro del mouse in un'area vuota nel *Pannello gerarchia*, quindi su **oggetto 3D, cubo**.</span><span class="sxs-lookup"><span data-stu-id="b1675-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="b1675-314">Con il **cubo** selezionato, modificare la *posizione* di trasformazione in: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="b1675-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="b1675-315">Fare clic con il pulsante destro del mouse in un'area vuota nel *Pannello gerarchia*, quindi su **oggetto 3D, sfera**.</span><span class="sxs-lookup"><span data-stu-id="b1675-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="b1675-316">Con la **sfera** selezionata, modificare la *posizione* di trasformazione in: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="b1675-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="b1675-318">Questi valori di *posizione* sono *suggerimenti*.</span><span class="sxs-lookup"><span data-stu-id="b1675-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="b1675-319">È possibile impostare le posizioni degli oggetti su quello che si desidera, sebbene sia più semplice per l'utente dell'applicazione se le distanze degli oggetti non sono troppo distanti dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="b1675-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="b1675-320">Quando l'applicazione è in esecuzione, deve essere in grado di identificare gli oggetti all'interno della scena, a tale scopo è necessario contrassegnarli.</span><span class="sxs-lookup"><span data-stu-id="b1675-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="b1675-321">Selezionare uno degli oggetti e nel pannello di *controllo* fare clic su **Aggiungi tag...** , che consente di scambiare il *controllo* con il pannello **tag & livelli** .</span><span class="sxs-lookup"><span data-stu-id="b1675-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="b1675-322">![configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="b1675-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="b1675-323">Fare clic sul simbolo **+ (segno più)** , quindi digitare il nome del tag come **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="b1675-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="b1675-325">Se si usa un nome diverso per il tag, è necessario assicurarsi che questa modifica sia anche *DataFromAnalytics*, *ObjectTrigger*e *sguardi*, script in un secondo momento, in modo che gli oggetti vengano trovati e rilevati all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="b1675-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="b1675-326">Con il tag creato, è ora necessario applicarlo a tutti e tre gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="b1675-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="b1675-327">Dalla *gerarchia*tenere premuto il tasto **MAIUSC** , quindi fare clic su **capsula**, **cubo**e **sfera**, oggetti, quindi, nel *controllo*, fare clic sul menu a discesa insieme a **tag**, quindi fare clic sul tag *ObjectInScene* creato.</span><span class="sxs-lookup"><span data-stu-id="b1675-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="b1675-328">![configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="b1675-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="b1675-329">Capitolo 6: creare la classe ApplicationInsightsTracker</span><span class="sxs-lookup"><span data-stu-id="b1675-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="b1675-330">Il primo script che è necessario creare è **ApplicationInsightsTracker**, responsabile di:</span><span class="sxs-lookup"><span data-stu-id="b1675-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="b1675-331">Creazione di eventi in base alle interazioni dell'utente da inviare ad applicazione Azure Insights.</span><span class="sxs-lookup"><span data-stu-id="b1675-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="b1675-332">Creazione di nomi di evento appropriati, a seconda dell'interazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="b1675-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="b1675-333">Invio di eventi all'istanza del servizio Application Insights.</span><span class="sxs-lookup"><span data-stu-id="b1675-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="b1675-334">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="b1675-334">To create this class:</span></span>

1.  <span data-ttu-id="b1675-335">Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare** > **cartella**.</span><span class="sxs-lookup"><span data-stu-id="b1675-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="b1675-336">Denominare gli **script**della cartella.</span><span class="sxs-lookup"><span data-stu-id="b1675-336">Name the folder **Scripts**.</span></span>

    ![Creazione della classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Creazione della classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="b1675-339">Con la cartella **Scripts** creata, fare doppio clic su di essa per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b1675-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="b1675-340">Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse su **Crea**  **C# script** > .</span><span class="sxs-lookup"><span data-stu-id="b1675-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="b1675-341">Denominare lo script **ApplicationInsightsTracker**.</span><span class="sxs-lookup"><span data-stu-id="b1675-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="b1675-342">Fare doppio clic sul nuovo script **ApplicationInsightsTracker** per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b1675-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="b1675-343">Aggiornare gli spazi dei nomi nella parte superiore dello script come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b1675-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="b1675-344">All'interno della classe inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1675-344">Inside the class insert the following variables:</span></span>

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
    > <span data-ttu-id="b1675-345">Impostare i valori **instrumentationKey, ApplicationId e API_Key** in modo appropriato, usando le *chiavi del servizio* dal portale di Azure, come indicato nel [capitolo 1](#chapter-1---the-azure-portal), passaggio 9 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="b1675-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="b1675-346">Aggiungere quindi i metodi **Start ()** e **svegli ()** , che verranno chiamati al momento dell'inizializzazione della classe:</span><span class="sxs-lookup"><span data-stu-id="b1675-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="b1675-347">Aggiungere i metodi responsabili dell'invio degli eventi e delle metriche registrati dall'applicazione:</span><span class="sxs-lookup"><span data-stu-id="b1675-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

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

8.  <span data-ttu-id="b1675-348">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b1675-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="b1675-349">Capitolo 7: creare lo script di sguardi</span><span class="sxs-lookup"><span data-stu-id="b1675-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="b1675-350">Lo script successivo da creare è lo **sguardo** .</span><span class="sxs-lookup"><span data-stu-id="b1675-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="b1675-351">Questo script è responsabile della creazione di un *Raycast* che verrà proiettato in futuro dalla *fotocamera principale*, per individuare l'oggetto analizzato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="b1675-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="b1675-352">In questo caso, *Raycast* deve identificare se l'utente sta esaminando un oggetto con il tag **ObjectInScene** , quindi contare il tempo che *l'utente guarda* a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="b1675-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="b1675-353">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b1675-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b1675-354">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="b1675-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="b1675-355">Denominare **lo script.**</span><span class="sxs-lookup"><span data-stu-id="b1675-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="b1675-356">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1675-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="b1675-357">Sostituire il codice esistente con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="b1675-357">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="b1675-358">È ora necessario aggiungere il codice per i metodi **svegli ()** e **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="b1675-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

6.  <span data-ttu-id="b1675-359">All'interno della classe **sguardi** aggiungere il codice seguente nel metodo **Update ()** per proiettare un *Raycast* e rilevare il raggiungimento della destinazione:</span><span class="sxs-lookup"><span data-stu-id="b1675-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

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

7.  <span data-ttu-id="b1675-360">Aggiungere il metodo **ResetFocusedObject ()** per inviare dati a **Application Insights** quando l'utente ha esaminato un oggetto.</span><span class="sxs-lookup"><span data-stu-id="b1675-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

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

8.  <span data-ttu-id="b1675-361">Lo script di **sguardi** è stato completato.</span><span class="sxs-lookup"><span data-stu-id="b1675-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="b1675-362">Salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b1675-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="b1675-363">Capitolo 8: creare la classe ObjectTrigger</span><span class="sxs-lookup"><span data-stu-id="b1675-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="b1675-364">Lo script successivo che è necessario creare è **ObjectTrigger**, responsabile di:</span><span class="sxs-lookup"><span data-stu-id="b1675-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="b1675-365">Aggiunta di componenti necessari per la collisione alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="b1675-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="b1675-366">Rilevamento della presenza della fotocamera vicino a un oggetto contrassegnato come **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="b1675-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="b1675-367">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="b1675-367">To create the script:</span></span>

1.  <span data-ttu-id="b1675-368">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b1675-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b1675-369">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="b1675-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="b1675-370">Denominare lo script **ObjectTrigger**.</span><span class="sxs-lookup"><span data-stu-id="b1675-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="b1675-371">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1675-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="b1675-372">Sostituire il codice esistente con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="b1675-372">Replace the existing code with the following:</span></span>

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

4.  <span data-ttu-id="b1675-373">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b1675-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="b1675-374">Capitolo 9: creare la classe DataFromAnalytics</span><span class="sxs-lookup"><span data-stu-id="b1675-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="b1675-375">A questo punto sarà necessario creare lo script **DataFromAnalytics** , responsabile di:</span><span class="sxs-lookup"><span data-stu-id="b1675-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="b1675-376">Recupero dei dati di analisi sull'oggetto che è stato più utilizzato dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="b1675-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="b1675-377">Usando le *chiavi del servizio*, che consentono la comunicazione con l'istanza del servizio applicazione Azure Insights.</span><span class="sxs-lookup"><span data-stu-id="b1675-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="b1675-378">Ordinamento degli oggetti in scena, in base al quale ha il numero massimo di eventi.</span><span class="sxs-lookup"><span data-stu-id="b1675-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="b1675-379">Modifica del colore del materiale, dell'oggetto più affrontato, in *verde*.</span><span class="sxs-lookup"><span data-stu-id="b1675-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="b1675-380">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="b1675-380">To create the script:</span></span>

1.  <span data-ttu-id="b1675-381">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b1675-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b1675-382">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="b1675-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="b1675-383">Denominare lo script **DataFromAnalytics**.</span><span class="sxs-lookup"><span data-stu-id="b1675-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="b1675-384">Fare doppio clic sullo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1675-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="b1675-385">Inserire gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b1675-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="b1675-386">All'interno dello script, inserire quanto segue:</span><span class="sxs-lookup"><span data-stu-id="b1675-386">Inside the script, insert the following:</span></span>

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

6.  <span data-ttu-id="b1675-387">All'interno della classe **DataFromAnalytics** , subito dopo il metodo **Start ()** , aggiungere il metodo seguente denominato **FetchAnalytics ()** .</span><span class="sxs-lookup"><span data-stu-id="b1675-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="b1675-388">Questo metodo è responsabile del popolamento dell'elenco di coppie chiave-valore, con *GameObject* e un numero di conteggio eventi segnaposto.</span><span class="sxs-lookup"><span data-stu-id="b1675-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="b1675-389">Inizializza quindi la coroutine **GetWebRequest ()** .</span><span class="sxs-lookup"><span data-stu-id="b1675-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="b1675-390">La struttura di query della chiamata a *Application Insights* è disponibile anche all'interno di questo metodo, come endpoint dell' *URL della query* .</span><span class="sxs-lookup"><span data-stu-id="b1675-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

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

7.  <span data-ttu-id="b1675-391">Al di sotto del metodo **FetchAnalytics ()** aggiungere un metodo denominato **GetWebRequest ()** che restituisce un *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="b1675-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="b1675-392">Questo metodo è responsabile della richiesta del numero di volte in cui un evento, corrispondente a un *GameObject*specifico, è stato chiamato all'interno *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="b1675-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="b1675-393">Quando tutte le query inviate sono state restituite, viene chiamato il metodo **DetermineWinner ()** .</span><span class="sxs-lookup"><span data-stu-id="b1675-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
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

8.  <span data-ttu-id="b1675-394">Il metodo successivo è **DetermineWinner ()** , che ordina l'elenco di coppie *GameObject* e *int* , in base al numero massimo di eventi.</span><span class="sxs-lookup"><span data-stu-id="b1675-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="b1675-395">Il colore del materiale di tale *GameObject* viene quindi modificato in *verde* (come feedback per il numero più alto).</span><span class="sxs-lookup"><span data-stu-id="b1675-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="b1675-396">Viene visualizzato un messaggio con i risultati dell'analisi.</span><span class="sxs-lookup"><span data-stu-id="b1675-396">This displays a message with the analytics results.</span></span>

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

9.  <span data-ttu-id="b1675-397">Aggiungere la struttura della classe che verrà usata per deserializzare l'oggetto JSON, ricevuto da *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="b1675-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="b1675-398">Aggiungere queste classi nella parte inferiore del file della classe **DataFromAnalytics** , al di **fuori** della definizione della classe.</span><span class="sxs-lookup"><span data-stu-id="b1675-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

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

10. <span data-ttu-id="b1675-399">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b1675-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="b1675-400">Capitolo 10: creare la classe Movement</span><span class="sxs-lookup"><span data-stu-id="b1675-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="b1675-401">Lo script di **spostamento** è lo script successivo che sarà necessario creare.</span><span class="sxs-lookup"><span data-stu-id="b1675-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="b1675-402">È responsabile di:</span><span class="sxs-lookup"><span data-stu-id="b1675-402">It is responsible for:</span></span>

- <span data-ttu-id="b1675-403">Lo sposti della fotocamera principale in base alla direzione che la fotocamera sta cercando.</span><span class="sxs-lookup"><span data-stu-id="b1675-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="b1675-404">Aggiunta di tutti gli altri script agli oggetti scena.</span><span class="sxs-lookup"><span data-stu-id="b1675-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="b1675-405">Per creare lo script:</span><span class="sxs-lookup"><span data-stu-id="b1675-405">To create the script:</span></span>

1.  <span data-ttu-id="b1675-406">Fare doppio clic sulla cartella **Scripts** per aprirla.</span><span class="sxs-lookup"><span data-stu-id="b1675-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="b1675-407">Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="b1675-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="b1675-408">Assegnare un nome allo **spostamento**dello script.</span><span class="sxs-lookup"><span data-stu-id="b1675-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="b1675-409">Fare doppio clic sullo script per aprirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="b1675-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="b1675-410">Sostituire il codice esistente con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="b1675-410">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="b1675-411">All'interno della classe **Movement** , *sotto* il metodo **Update ()** vuoto, inserire i metodi seguenti che consentono all'utente di usare il controller della mano per spostarsi nello spazio virtuale:</span><span class="sxs-lookup"><span data-stu-id="b1675-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

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

6.  <span data-ttu-id="b1675-412">Aggiungere infine la chiamata al metodo all'interno del metodo **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="b1675-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="b1675-413">Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b1675-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="b1675-414">Capitolo 11-Configurazione dei riferimenti agli script</span><span class="sxs-lookup"><span data-stu-id="b1675-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="b1675-415">In questo capitolo è necessario inserire lo script di **spostamento** sull' **elemento padre della fotocamera** e impostare le relative destinazioni di riferimento.</span><span class="sxs-lookup"><span data-stu-id="b1675-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="b1675-416">Tale script gestirà quindi l'inserimento degli altri script in cui devono essere.</span><span class="sxs-lookup"><span data-stu-id="b1675-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="b1675-417">Dalla cartella **Scripts** nel *Pannello Project*trascinare lo script **Movement** nell'oggetto padre della **fotocamera** , che si trova nel *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="b1675-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Configurazione dei riferimenti agli script nella scena Unity](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="b1675-419">Fare clic sull' **elemento padre della fotocamera**.</span><span class="sxs-lookup"><span data-stu-id="b1675-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="b1675-420">Nel *Pannello gerarchia*trascinare l'oggetto **destro** dal *Pannello gerarchia* alla destinazione di riferimento, **controller**, nel *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="b1675-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="b1675-421">Impostare la **velocità utente** su **5**, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="b1675-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Configurazione dei riferimenti agli script nella scena Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="b1675-423">Capitolo 12: creare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="b1675-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="b1675-424">Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.</span><span class="sxs-lookup"><span data-stu-id="b1675-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="b1675-425">Passare a **impostazioni di compilazione**(**file** > **impostazioni di compilazione**).</span><span class="sxs-lookup"><span data-stu-id="b1675-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="b1675-426">Nella finestra **impostazioni di compilazione** fare clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="b1675-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilare il progetto Unity per la soluzione UWP](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="b1675-428">Verrà visualizzata una finestra di **Esplora file** con la richiesta di un percorso per la compilazione.</span><span class="sxs-lookup"><span data-stu-id="b1675-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="b1675-429">Creare una nuova cartella (facendo clic su **nuova cartella** nell'angolo superiore sinistro) e denominarla **compilata**.</span><span class="sxs-lookup"><span data-stu-id="b1675-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Compilare il progetto Unity per la soluzione UWP](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="b1675-431">Aprire la nuova cartella **compilazioni** e creare un'altra cartella (usando una **nuova cartella** ancora una volta) e denominarla **MR\_Azure\_Application\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="b1675-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Compilare il progetto Unity per la soluzione UWP](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="b1675-433">Con la cartella **\_Azure\_Application\_Insights** selezionata, fare clic su **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="b1675-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="b1675-434">La compilazione del progetto verrà eseguita per un minuto.</span><span class="sxs-lookup"><span data-stu-id="b1675-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="b1675-435">Nella *compilazione*seguente verrà visualizzato **Esplora file** che indica il percorso del nuovo progetto.</span><span class="sxs-lookup"><span data-stu-id="b1675-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a><span data-ttu-id="b1675-436">Capitolo 13: distribuire MR_Azure_Application_Insights app nel computer</span><span class="sxs-lookup"><span data-stu-id="b1675-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="b1675-437">Per distribuire l'app **\_Azure\_Application\_Insights** nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="b1675-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="b1675-438">Aprire il file di soluzione dell'app **\_Azure\_Application\_Insights** in **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b1675-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="b1675-439">Nella **piattaforma soluzione**selezionare **x86, computer locale**.</span><span class="sxs-lookup"><span data-stu-id="b1675-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="b1675-440">Nella **configurazione della soluzione** selezionare **debug**.</span><span class="sxs-lookup"><span data-stu-id="b1675-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Compilare il progetto Unity per la soluzione UWP](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="b1675-442">Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.</span><span class="sxs-lookup"><span data-stu-id="b1675-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="b1675-443">L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.</span><span class="sxs-lookup"><span data-stu-id="b1675-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="b1675-444">Avviare l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b1675-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="b1675-445">Spostarsi nella scena, avvicinarsi agli oggetti e esaminarli, quando il *servizio Azure Insight* ha raccolto un numero sufficiente di dati degli eventi, imposta l'oggetto che è stato avvicinato al più verde.</span><span class="sxs-lookup"><span data-stu-id="b1675-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="b1675-446">Il tempo medio di attesa per la raccolta di *eventi e metriche* da parte del servizio richiede circa 15 minuti, in alcune occasioni potrebbe richiedere fino a 1 ora.</span><span class="sxs-lookup"><span data-stu-id="b1675-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="b1675-447">Capitolo 14-portale del servizio Application Insights</span><span class="sxs-lookup"><span data-stu-id="b1675-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="b1675-448">Dopo aver eseguito il roaming nella scena e aver guardato diversi oggetti, è possibile visualizzare i dati raccolti nel portale del *servizio Application Insights* .</span><span class="sxs-lookup"><span data-stu-id="b1675-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="b1675-449">Tornare al portale del servizio Application Insights.</span><span class="sxs-lookup"><span data-stu-id="b1675-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="b1675-450">Fare clic su *Esplora metriche*.</span><span class="sxs-lookup"><span data-stu-id="b1675-450">Click on *Metrics Explorer*.</span></span>

    ![Esaminare i dati raccolti](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="b1675-452">Verrà aperto in una scheda contenente il grafico che rappresenta gli *eventi e le metriche* correlate all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b1675-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="b1675-453">Come indicato in precedenza, la visualizzazione dei dati nel grafico potrebbe richiedere del tempo (fino a un'ora)</span><span class="sxs-lookup"><span data-stu-id="b1675-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Esaminare i dati raccolti](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="b1675-455">Fare clic sulla *barra degli eventi* nel *totale degli eventi* in base alla versione dell'applicazione per visualizzare una suddivisione dettagliata degli eventi con i relativi nomi.</span><span class="sxs-lookup"><span data-stu-id="b1675-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Esaminare i dati raccolti](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="b1675-457">L'applicazione di servizio Application Insights completata</span><span class="sxs-lookup"><span data-stu-id="b1675-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="b1675-458">Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio Application Insights per monitorare l'attività dell'utente all'interno dell'app.</span><span class="sxs-lookup"><span data-stu-id="b1675-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![risultato del corso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b1675-460">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="b1675-460">Bonus Exercises</span></span>

<span data-ttu-id="b1675-461">**Esercizio 1**</span><span class="sxs-lookup"><span data-stu-id="b1675-461">**Exercise 1**</span></span>

<span data-ttu-id="b1675-462">Provare a generare, anziché creare manualmente gli oggetti ObjectInScene e impostare le rispettive coordinate sul piano all'interno degli script.</span><span class="sxs-lookup"><span data-stu-id="b1675-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="b1675-463">In questo modo, è possibile richiedere ad Azure l'oggetto più diffuso (da uno sguardo o risultati di prossimità) e *generare un altro* oggetto.</span><span class="sxs-lookup"><span data-stu-id="b1675-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="b1675-464">**Esercizio 2**</span><span class="sxs-lookup"><span data-stu-id="b1675-464">**Exercise 2**</span></span>

<span data-ttu-id="b1675-465">Ordinare i risultati del Application Insights in base all'ora, in modo da ottenere i dati più rilevanti e implementare tali dati sensibili all'ora nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b1675-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

