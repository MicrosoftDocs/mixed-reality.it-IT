---
title: MR e Azure 301 - traduzione
description: Completare questo corso di informazioni su come implementare l'API traduzione testuale Azure all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, traduzione testuale Microsoft translator, hololens, coinvolgenti, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603611"
---
>[!NOTE]
><span data-ttu-id="46b4e-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="46b4e-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="46b4e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="46b4e-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="46b4e-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="46b4e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="46b4e-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="46b4e-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="46b4e-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="46b4e-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="46b4e-110">MR e Azure 301: Traduzioni</span><span class="sxs-lookup"><span data-stu-id="46b4e-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="46b4e-111">In questo corso, si apprenderà come aggiungere funzionalità di conversione a un'applicazione di realtà mista tramite servizi cognitivi di Azure, con l'API traduzione testuale.</span><span class="sxs-lookup"><span data-stu-id="46b4e-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Versione finale del prodotto](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="46b4e-113">L'API traduzione testuale è una servizio che funziona quasi in tempo reale di conversione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="46b4e-114">Il servizio è basato sul cloud e, tramite una chiamata API REST, possa rendere un'app per usare la tecnologia di traduzione automatica neurale per tradurre il testo in un altro linguaggio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="46b4e-115">Per altre informazioni, visitare il [pagina API traduzione testuale Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="46b4e-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="46b4e-116">Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="46b4e-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="46b4e-117">L'utente leggerà in un microfono connessi a un auricolare (VR) coinvolgenti (o il microfono incorporato di HoloLens).</span><span class="sxs-lookup"><span data-stu-id="46b4e-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="46b4e-118">L'app verrà acquisire la dettatura e inviarlo per l'API traduzione testuale di Azure.</span><span class="sxs-lookup"><span data-stu-id="46b4e-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="46b4e-119">Il risultato di traduzione verrà visualizzato in un gruppo dell'interfaccia utente semplice nella scena Unity.</span><span class="sxs-lookup"><span data-stu-id="46b4e-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="46b4e-120">Questo corso ti spiegherà come ottenere i risultati dal servizio di Microsoft Translator in un'applicazione di esempio basate su Unity.</span><span class="sxs-lookup"><span data-stu-id="46b4e-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="46b4e-121">Sarà quindi compito è possibile applicare questi concetti a un'applicazione personalizzata, che potrebbe voler costruire.</span><span class="sxs-lookup"><span data-stu-id="46b4e-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="46b4e-122">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="46b4e-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="46b4e-123">Corso</span><span class="sxs-lookup"><span data-stu-id="46b4e-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="46b4e-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="46b4e-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="46b4e-125"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="46b4e-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="46b4e-126">MR e Azure 301: Traduzioni</span><span class="sxs-lookup"><span data-stu-id="46b4e-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="46b4e-127">✔️</span><span class="sxs-lookup"><span data-stu-id="46b4e-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="46b4e-128">✔️</span><span class="sxs-lookup"><span data-stu-id="46b4e-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="46b4e-129">Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="46b4e-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="46b4e-130">Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="46b4e-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="46b4e-131">Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.</span><span class="sxs-lookup"><span data-stu-id="46b4e-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46b4e-132">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="46b4e-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="46b4e-133">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#.</span><span class="sxs-lookup"><span data-stu-id="46b4e-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="46b4e-134">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018).</span><span class="sxs-lookup"><span data-stu-id="46b4e-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="46b4e-135">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .</span><span class="sxs-lookup"><span data-stu-id="46b4e-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="46b4e-136">È consigliabile seguenti prodotti hardware e software per questo corso di:</span><span class="sxs-lookup"><span data-stu-id="46b4e-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="46b4e-137">Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)</span><span class="sxs-lookup"><span data-stu-id="46b4e-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="46b4e-138">Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="46b4e-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="46b4e-139">La versione più recente di Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="46b4e-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="46b4e-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="46b4e-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="46b4e-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="46b4e-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="46b4e-142">Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore</span><span class="sxs-lookup"><span data-stu-id="46b4e-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="46b4e-143">Le cuffie con un microfono incorporato (se le cuffie non è presente un mic incorporati e altri relatori)</span><span class="sxs-lookup"><span data-stu-id="46b4e-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="46b4e-144">Accesso a Internet per il recupero di programma di installazione e la conversione di Azure</span><span class="sxs-lookup"><span data-stu-id="46b4e-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="46b4e-145">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="46b4e-145">Before you start</span></span>

- <span data-ttu-id="46b4e-146">Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).</span><span class="sxs-lookup"><span data-stu-id="46b4e-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="46b4e-147">Il codice in questa esercitazione è possibile registrare dal dispositivo microfono predefinito connesso al PC.</span><span class="sxs-lookup"><span data-stu-id="46b4e-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="46b4e-148">Assicurarsi che il dispositivo di microfono predefinito viene impostato per il dispositivo che si intende usare per acquisire la voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="46b4e-149">Per consentire al computer abilitare la dettatura, passare a **Impostazioni > Privacy > vocale, input penna e digitando** e selezionare il pulsante **Turn On servizi di riconoscimento vocale e i suggerimenti di digitazione**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="46b4e-150">Se si usa un microfono e cuffie connesso a (o incorporato in) le cuffie, assicurarsi che l'opzione "Quando wear my le cuffie, passare a microfono auricolare" attivata nel **Impostazioni > realtà mista > Audio e vocale**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Impostazioni di realtà mista](images/AzureLabs-Lab1-00-5.png)

   ![Impostazione di microfono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="46b4e-153">Tenere presente che se si sta sviluppando per un visore VR immersivi per questo lab, potrebbero verificarsi problemi di dispositivo di output audio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="46b4e-154">Si è verificato un errore con Unity, che è stato risolto in versioni successive di Unity (Unity 2018.2).</span><span class="sxs-lookup"><span data-stu-id="46b4e-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="46b4e-155">Il problema impedisce Unity di cambiare il dispositivo di output audio predefinito in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="46b4e-156">Come per risolvere il problema, assicurarsi di che aver completato i passaggi precedenti, chiudere e riaprire l'Editor, quando questo problema si manifesta.</span><span class="sxs-lookup"><span data-stu-id="46b4e-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="46b4e-157">Capitolo 1: il portale di Azure</span><span class="sxs-lookup"><span data-stu-id="46b4e-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="46b4e-158">Per usare l'API di traduzione di Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="46b4e-159">Accedi per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="46b4e-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="46b4e-160">Se non hai già un account Azure, è necessario crearne uno.</span><span class="sxs-lookup"><span data-stu-id="46b4e-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="46b4e-161">Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="46b4e-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="46b4e-162">Una volta connessi, fare clic su **New** in alto a sinistra angolo e cercare "API traduzione testuale."</span><span class="sxs-lookup"><span data-stu-id="46b4e-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="46b4e-163">Selezionare **immettere**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-163">Select **Enter**.</span></span>

    ![Nuova risorsa](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="46b4e-165">La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="46b4e-166">La nuova pagina fornirà una descrizione del *API traduzione testuale* servizio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="46b4e-167">AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Crea servizio API di traduzione testo](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="46b4e-169">Dopo avere fatto clic su **Create**:</span><span class="sxs-lookup"><span data-stu-id="46b4e-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="46b4e-170">Inserire la posizione desiderata **nome** per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="46b4e-171">Selezionare un'opzione appropriata **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="46b4e-172">Selezionare il **piano tariffario** appropriati per l'utente, se questo è il primo tempo nella creazione una *servizio di traduzione testo*, un livello gratuito, denominato F0, debba essere disponibile.</span><span class="sxs-lookup"><span data-stu-id="46b4e-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="46b4e-173">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="46b4e-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="46b4e-174">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="46b4e-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="46b4e-175">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="46b4e-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="46b4e-176">Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="46b4e-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="46b4e-177">Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse).</span><span class="sxs-lookup"><span data-stu-id="46b4e-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="46b4e-178">La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita.</span><span class="sxs-lookup"><span data-stu-id="46b4e-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="46b4e-179">Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.</span><span class="sxs-lookup"><span data-stu-id="46b4e-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="46b4e-180">È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="46b4e-181">Selezionare **Create**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-181">Select **Create**.</span></span>

        ![Selezionare il pulsante Crea.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="46b4e-183">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="46b4e-184">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="46b4e-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Notifica di creazione del servizio Azure](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="46b4e-186">Fare clic sulla notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Passare alla finestra popup di risorse.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="46b4e-188">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="46b4e-189">Si verrà indirizzati all'istanza del servizio API di traduzione testo nuovo.</span><span class="sxs-lookup"><span data-stu-id="46b4e-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Pagina del servizio API di testo Microsoft Translator](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="46b4e-191">All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, questa operazione viene eseguita tramite chiave di sottoscrizione del servizio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="46b4e-192">Dal *avvio rapido* pagina delle *traduzione testuale Microsoft Translator* servizio, passare al primo passaggio *individuare le chiavi*e fare clic su **chiavi** (è possibile anche ottenere questo risultato facendo il collegamento blu chiavi, che si trova nel menu di spostamento dei servizi, indicato dall'icona della chiave).</span><span class="sxs-lookup"><span data-stu-id="46b4e-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="46b4e-193">Il servizio verrà visualizzata *chiavi*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="46b4e-194">Richiedere una copia di una delle chiavi visualizzate, in quanto sarà necessaria in un secondo momento nel progetto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="46b4e-195">Capitolo 2: configurare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="46b4e-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="46b4e-196">Configurare e testare il visore VR immersivi di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="46b4e-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="46b4e-197">A questo corso non è necessario il controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="46b4e-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="46b4e-198">Se è necessario il supporto di configurazione di un visore VR immersivi, please [seguire questa procedura](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="46b4e-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="46b4e-199">Di seguito è un set tipico backup per lo sviluppo con realtà mista e, di conseguenza, è un buon modello per altri progetti:</span><span class="sxs-lookup"><span data-stu-id="46b4e-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="46b4e-200">Aprire *Unity* e fare clic su **New**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-200">Open *Unity* and click **New**.</span></span> 

    ![Avvio nuovo progetto Unity.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="46b4e-202">A questo punto, è necessario specificare un nome di progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="46b4e-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="46b4e-203">Inserire **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="46b4e-204">Verificare che il tipo di progetto è impostato su **3D**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="46b4e-205">Impostare il *posizione* a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice).</span><span class="sxs-lookup"><span data-stu-id="46b4e-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="46b4e-206">Fare quindi clic **Crea progetto**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-206">Then, click **Create project**.</span></span>

    ![Fornire i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="46b4e-208">Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="46b4e-209">Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="46b4e-210">Change **External Script Editor** al **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="46b4e-211">Chiudi il **preferenze** finestra.</span><span class="sxs-lookup"><span data-stu-id="46b4e-211">Close the **Preferences** window.</span></span>

    ![Aggiornamento delle preferenze dell'editor di script.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="46b4e-213">Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.</span><span class="sxs-lookup"><span data-stu-id="46b4e-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crea finestra delle impostazioni, la piattaforma del commutatore alla piattaforma UWP.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="46b4e-215">Passare a **File > Build Settings** e assicurarsi che:</span><span class="sxs-lookup"><span data-stu-id="46b4e-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="46b4e-216">**Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="46b4e-217">Per Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="46b4e-218">**Tipo di compilazione** è impostata su **D3D**</span><span class="sxs-lookup"><span data-stu-id="46b4e-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="46b4e-219">**SDK** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="46b4e-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="46b4e-220">**Versione di Visual Studio** è impostata su **installata più recente**</span><span class="sxs-lookup"><span data-stu-id="46b4e-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="46b4e-221">**Compilare ed eseguire** è impostata su **computer locale**</span><span class="sxs-lookup"><span data-stu-id="46b4e-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="46b4e-222">Salvare la scena e aggiungerlo alla compilazione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="46b4e-223">Eseguire questa operazione selezionando **aggiungere scene Open**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="46b4e-224">Verrà visualizzata una finestra di salvataggio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-224">A save window will appear.</span></span>

            ![Fare clic su Aggiungi pulsante Apri scene](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="46b4e-226">Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crea nuova cartella scripts](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="46b4e-228">Aprire appena creato **scene** cartella e quindi il *nome File*: campo di testo, digitare **MR_TranslationScene**, quindi premere **Salva**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Assegnare un nome nuova scena.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="46b4e-230">Tenere presente, è necessario salvare le scene di Unity all'interno di *asset* cartella, come devono essere associate al progetto di Unity.</span><span class="sxs-lookup"><span data-stu-id="46b4e-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="46b4e-231">Creare la cartella scene (e altre simili) è un modo tipico strutturare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="46b4e-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="46b4e-232">Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.</span><span class="sxs-lookup"><span data-stu-id="46b4e-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="46b4e-233">Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.</span><span class="sxs-lookup"><span data-stu-id="46b4e-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Aprire le impostazioni del giocatore.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="46b4e-235">In questo pannello, alcune impostazioni devono essere verificati:</span><span class="sxs-lookup"><span data-stu-id="46b4e-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="46b4e-236">Nel **altre impostazioni** scheda:</span><span class="sxs-lookup"><span data-stu-id="46b4e-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="46b4e-237">**Versione del Runtime di scripting** deve essere **stabile** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="46b4e-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="46b4e-238">**Back-end di scripting** deve essere **.NET**</span><span class="sxs-lookup"><span data-stu-id="46b4e-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="46b4e-239">**Livello di compatibilità delle API** deve essere **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="46b4e-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Aggiornare le altre impostazioni.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="46b4e-241">All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:</span><span class="sxs-lookup"><span data-stu-id="46b4e-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="46b4e-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="46b4e-242">**InternetClient**</span></span>
        2. <span data-ttu-id="46b4e-243">**Microfono**</span><span class="sxs-lookup"><span data-stu-id="46b4e-243">**Microphone**</span></span>

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="46b4e-245">Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Aggiornare le impostazioni di R X.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="46b4e-247">Nuovamente in **Build Settings**, *Unity C# progetti* non è più è disattivata; selezionare la casella di controllo accanto a questo.</span><span class="sxs-lookup"><span data-stu-id="46b4e-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="46b4e-248">Chiudere la finestra Impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="46b4e-249">Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).</span><span class="sxs-lookup"><span data-stu-id="46b4e-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="46b4e-250">Capitolo 3: impostazione della fotocamera principale</span><span class="sxs-lookup"><span data-stu-id="46b4e-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46b4e-251">Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importarlo nel progetto come un [ *Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="46b4e-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="46b4e-252">È comunque necessario creare un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="46b4e-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="46b4e-253">Nel *Pannello di gerarchia*, si noterà un oggetto denominato **Main Camera**, questo oggetto rappresenta il punto di vista della "head" quando si è "l'applicazione interni".</span><span class="sxs-lookup"><span data-stu-id="46b4e-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="46b4e-254">Con il Dashboard di Unity fronte, selezionare la **Main Camera GameObject**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="46b4e-255">Si noterà che il *Pannello di controllo* (in genere trovato a destra, all'interno del Dashboard) mostrerà i vari componenti di tale *GameObject*, con *trasformare* nella parte superiore, seguita da *fotocamera*e alcuni altri componenti.</span><span class="sxs-lookup"><span data-stu-id="46b4e-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="46b4e-256">È necessario reimpostare la trasformazione della fotocamera principale, in modo che sia posizionato correttamente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="46b4e-257">A questo scopo, selezionare la **a forma di ingranaggio** icona accanto della fotocamera *trasformare* componente e selezionando **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Reimpostare la trasformazione Main Camera.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="46b4e-259">Il *trasformare* componente sarà quindi simile:</span><span class="sxs-lookup"><span data-stu-id="46b4e-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="46b4e-260">Il *posizione* è impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="46b4e-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="46b4e-261">*Rotazione* è impostata su **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="46b4e-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="46b4e-262">E *scalabilità* è impostata su **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="46b4e-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Trasformare le informazioni per la fotocamera](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="46b4e-264">Successivamente, con la **Main Camera** oggetti selezionati, vedere il **Add Component** che si trova nella parte inferiore del *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="46b4e-265">Selezionare questo pulsante e di ricerca (digitandone *origine Audio* nel campo di ricerca o passare le sezioni) per il componente denominato **origine Audio** come illustrato di seguito e selezionarlo (premendo INVIO su di esso funziona anche).</span><span class="sxs-lookup"><span data-stu-id="46b4e-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="46b4e-266">Un' *origine Audio* verrà aggiunto al componente la **Main Camera**, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="46b4e-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Aggiungere un componente di origine Audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="46b4e-268">Per Microsoft HoloLens, sarà necessario modificare anche il comando seguente, che fanno parte del **fotocamera** componente le **Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="46b4e-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="46b4e-269">**Cancellare i flag:** Colore a tinta unita.</span><span class="sxs-lookup"><span data-stu-id="46b4e-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="46b4e-270">**Sfondo** ' nero, Alpha 0'-colore esadecimale: #00000000.</span><span class="sxs-lookup"><span data-stu-id="46b4e-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="46b4e-271">Capitolo 4: configurazione Debug Canvas</span><span class="sxs-lookup"><span data-stu-id="46b4e-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="46b4e-272">Per visualizzare l'input e output della conversione, è necessario creare un'interfaccia utente di base.</span><span class="sxs-lookup"><span data-stu-id="46b4e-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="46b4e-273">A questo corso, si creerà un oggetto di interfaccia utente di Canvas con vari oggetti 'Text' per visualizzare i dati.</span><span class="sxs-lookup"><span data-stu-id="46b4e-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="46b4e-274">Pulsante destro del mouse in un'area vuota della *pannello gerarchia*, in **UI**, aggiungere un **Canvas**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Aggiungere nuovo oggetto area di disegno dell'interfaccia utente.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="46b4e-276">Con l'oggetto Canvas selezionato, nella *Pannello di controllo* (all'interno del componente 'Area di disegno'), cambiare **modalità di rendering** a **spazio globale**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="46b4e-277">Successivamente, modificare i parametri seguenti nel *Rect trasformazione del Pannello di controllo*:</span><span class="sxs-lookup"><span data-stu-id="46b4e-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="46b4e-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="46b4e-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="46b4e-279">*Larghezza* : 500</span><span class="sxs-lookup"><span data-stu-id="46b4e-279">*Width* -    500</span></span>
    3. <span data-ttu-id="46b4e-280">*Altezza* - 300</span><span class="sxs-lookup"><span data-stu-id="46b4e-280">*Height* -   300</span></span>
    4. <span data-ttu-id="46b4e-281">*Scala* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="46b4e-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Aggiornare la trasformazione rect per l'area di disegno.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="46b4e-283">Fare clic con il pulsante destro sul **Canvas** nel *pannello gerarchia*, sotto **dell'interfaccia utente**e aggiungere un **pannello**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="46b4e-284">Ciò **pannello** fornirà uno sfondo per il testo che si prevede di visualizzare nella scena.</span><span class="sxs-lookup"><span data-stu-id="46b4e-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="46b4e-285">Fare clic con il pulsante destro sul **pannello** nel *pannello gerarchia*, sotto **dell'interfaccia utente**e aggiungere un **oggetto testo**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="46b4e-286">Ripetere lo stesso processo finché vengono creati quattro oggetti di testo dell'interfaccia utente in totale (Suggerimento: se hai selezionato il primo oggetto di 'Testo', è possibile premere semplicemente **'Ctrl' + era '**, in caso di necessità, fino a quando non si avranno quattro in totale).</span><span class="sxs-lookup"><span data-stu-id="46b4e-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="46b4e-287">Per ogni **oggetto testo**, selezionarlo e usare le seguenti tabelle per impostare i parametri *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="46b4e-288">Per il *Rect trasformazione* componente:</span><span class="sxs-lookup"><span data-stu-id="46b4e-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="46b4e-289">Nome</span><span class="sxs-lookup"><span data-stu-id="46b4e-289">Name</span></span>                   | <span data-ttu-id="46b4e-290">Trasformare - *posizione*</span><span class="sxs-lookup"><span data-stu-id="46b4e-290">Transform - *Position*</span></span>             | <span data-ttu-id="46b4e-291">Larghezza</span><span class="sxs-lookup"><span data-stu-id="46b4e-291">Width</span></span>      | <span data-ttu-id="46b4e-292">Altezza</span><span class="sxs-lookup"><span data-stu-id="46b4e-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="46b4e-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="46b4e-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="46b4e-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="46b4e-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="46b4e-295">300</span><span class="sxs-lookup"><span data-stu-id="46b4e-295">300</span></span>        | <span data-ttu-id="46b4e-296">30</span><span class="sxs-lookup"><span data-stu-id="46b4e-296">30</span></span>        |
        | <span data-ttu-id="46b4e-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="46b4e-297">AzureResponseLabel</span></span>     | <span data-ttu-id="46b4e-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="46b4e-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="46b4e-299">300</span><span class="sxs-lookup"><span data-stu-id="46b4e-299">300</span></span>        | <span data-ttu-id="46b4e-300">30</span><span class="sxs-lookup"><span data-stu-id="46b4e-300">30</span></span>        |
        | <span data-ttu-id="46b4e-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="46b4e-301">DictationLabel</span></span>         | <span data-ttu-id="46b4e-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="46b4e-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="46b4e-303">300</span><span class="sxs-lookup"><span data-stu-id="46b4e-303">300</span></span>        | <span data-ttu-id="46b4e-304">30</span><span class="sxs-lookup"><span data-stu-id="46b4e-304">30</span></span>        |
        | <span data-ttu-id="46b4e-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="46b4e-305">TranslationResultLabel</span></span> | <span data-ttu-id="46b4e-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="46b4e-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="46b4e-307">300</span><span class="sxs-lookup"><span data-stu-id="46b4e-307">300</span></span>        | <span data-ttu-id="46b4e-308">30</span><span class="sxs-lookup"><span data-stu-id="46b4e-308">30</span></span>        |


    2. <span data-ttu-id="46b4e-309">Per il **testo (Script)** componente:</span><span class="sxs-lookup"><span data-stu-id="46b4e-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="46b4e-310">Nome</span><span class="sxs-lookup"><span data-stu-id="46b4e-310">Name</span></span>                   | <span data-ttu-id="46b4e-311">Testo</span><span class="sxs-lookup"><span data-stu-id="46b4e-311">Text</span></span>               | <span data-ttu-id="46b4e-312">Dimensione carattere</span><span class="sxs-lookup"><span data-stu-id="46b4e-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="46b4e-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="46b4e-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="46b4e-314">Stato microfono:</span><span class="sxs-lookup"><span data-stu-id="46b4e-314">Microphone Status:</span></span> | <span data-ttu-id="46b4e-315">20</span><span class="sxs-lookup"><span data-stu-id="46b4e-315">20</span></span>           |
        | <span data-ttu-id="46b4e-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="46b4e-316">AzureResponseLabel</span></span>     | <span data-ttu-id="46b4e-317">Risposta Web di Azure</span><span class="sxs-lookup"><span data-stu-id="46b4e-317">Azure Web Response</span></span> | <span data-ttu-id="46b4e-318">20</span><span class="sxs-lookup"><span data-stu-id="46b4e-318">20</span></span>           |
        | <span data-ttu-id="46b4e-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="46b4e-319">DictationLabel</span></span>         |   <span data-ttu-id="46b4e-320">Hai appena detto:</span><span class="sxs-lookup"><span data-stu-id="46b4e-320">You just said:</span></span>   | <span data-ttu-id="46b4e-321">20</span><span class="sxs-lookup"><span data-stu-id="46b4e-321">20</span></span>           |
        | <span data-ttu-id="46b4e-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="46b4e-322">TranslationResultLabel</span></span> |    <span data-ttu-id="46b4e-323">Conversione:</span><span class="sxs-lookup"><span data-stu-id="46b4e-323">Translation:</span></span>    | <span data-ttu-id="46b4e-324">20</span><span class="sxs-lookup"><span data-stu-id="46b4e-324">20</span></span>           |

        ![Immettere i valori corrispondenti per le etichette dell'interfaccia utente.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="46b4e-326">Assicurarsi, inoltre, lo stile del carattere **grassetto**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="46b4e-327">Il testo in questo modo più semplice da leggere.</span><span class="sxs-lookup"><span data-stu-id="46b4e-327">This will make the text easier to read.</span></span>

        ![Tipo di carattere grassetto.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="46b4e-329">Per ognuno *oggetto testo dell'interfaccia utente* creato nel [capitolo 5](#chapter-5--create-the-results-class), creare un nuovo *figlio* **oggetto testo dell'interfaccia utente**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="46b4e-330">Questi elementi figlio verranno visualizzato l'output dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-330">These children will display the output of the application.</span></span> <span data-ttu-id="46b4e-331">Creare *figlio* oggetti tramite il pulsante destro del tuo genitore desiderato (ad esempio *MicrophoneStatusLabel*) e quindi selezionare **UI** e quindi selezionare **testo**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="46b4e-332">Per ognuno di questi elementi figlio, selezionarlo e usare le tabelle per impostare i parametri nel Pannello di controllo seguenti.</span><span class="sxs-lookup"><span data-stu-id="46b4e-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="46b4e-333">Per il **Rect trasformazione** componente:</span><span class="sxs-lookup"><span data-stu-id="46b4e-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="46b4e-334">Nome</span><span class="sxs-lookup"><span data-stu-id="46b4e-334">Name</span></span>                  | <span data-ttu-id="46b4e-335">Trasformare - *posizione*</span><span class="sxs-lookup"><span data-stu-id="46b4e-335">Transform - *Position*</span></span> | <span data-ttu-id="46b4e-336">Larghezza</span><span class="sxs-lookup"><span data-stu-id="46b4e-336">Width</span></span>      | <span data-ttu-id="46b4e-337">Altezza</span><span class="sxs-lookup"><span data-stu-id="46b4e-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="46b4e-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="46b4e-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="46b4e-339">X Z Y -30 0 0</span><span class="sxs-lookup"><span data-stu-id="46b4e-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="46b4e-340">300</span><span class="sxs-lookup"><span data-stu-id="46b4e-340">300</span></span>        | <span data-ttu-id="46b4e-341">30</span><span class="sxs-lookup"><span data-stu-id="46b4e-341">30</span></span>        |
        | <span data-ttu-id="46b4e-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="46b4e-342">AzureResponseText</span></span>     | <span data-ttu-id="46b4e-343">X Z Y -30 0 0</span><span class="sxs-lookup"><span data-stu-id="46b4e-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="46b4e-344">300</span><span class="sxs-lookup"><span data-stu-id="46b4e-344">300</span></span>        | <span data-ttu-id="46b4e-345">30</span><span class="sxs-lookup"><span data-stu-id="46b4e-345">30</span></span>        |
        | <span data-ttu-id="46b4e-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="46b4e-346">DictationText</span></span>         | <span data-ttu-id="46b4e-347">X Z Y -30 0 0</span><span class="sxs-lookup"><span data-stu-id="46b4e-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="46b4e-348">300</span><span class="sxs-lookup"><span data-stu-id="46b4e-348">300</span></span>        | <span data-ttu-id="46b4e-349">30</span><span class="sxs-lookup"><span data-stu-id="46b4e-349">30</span></span>        |
        | <span data-ttu-id="46b4e-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="46b4e-350">TranslationResultText</span></span> | <span data-ttu-id="46b4e-351">X Z Y -30 0 0</span><span class="sxs-lookup"><span data-stu-id="46b4e-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="46b4e-352">300</span><span class="sxs-lookup"><span data-stu-id="46b4e-352">300</span></span>        | <span data-ttu-id="46b4e-353">30</span><span class="sxs-lookup"><span data-stu-id="46b4e-353">30</span></span>        |

    2. <span data-ttu-id="46b4e-354">Per il **testo (Script)** componente:</span><span class="sxs-lookup"><span data-stu-id="46b4e-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="46b4e-355">Nome</span><span class="sxs-lookup"><span data-stu-id="46b4e-355">Name</span></span>                  | <span data-ttu-id="46b4e-356">Testo</span><span class="sxs-lookup"><span data-stu-id="46b4e-356">Text</span></span>          | <span data-ttu-id="46b4e-357">Dimensione carattere</span><span class="sxs-lookup"><span data-stu-id="46b4e-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="46b4e-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="46b4e-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="46b4e-359">??</span><span class="sxs-lookup"><span data-stu-id="46b4e-359">??</span></span>       | <span data-ttu-id="46b4e-360">20</span><span class="sxs-lookup"><span data-stu-id="46b4e-360">20</span></span>           |
        | <span data-ttu-id="46b4e-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="46b4e-361">AzureResponseText</span></span>     |      <span data-ttu-id="46b4e-362">??</span><span class="sxs-lookup"><span data-stu-id="46b4e-362">??</span></span>       | <span data-ttu-id="46b4e-363">20</span><span class="sxs-lookup"><span data-stu-id="46b4e-363">20</span></span>           |
        | <span data-ttu-id="46b4e-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="46b4e-364">DictationText</span></span>         |      <span data-ttu-id="46b4e-365">??</span><span class="sxs-lookup"><span data-stu-id="46b4e-365">??</span></span>       | <span data-ttu-id="46b4e-366">20</span><span class="sxs-lookup"><span data-stu-id="46b4e-366">20</span></span>           |
        | <span data-ttu-id="46b4e-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="46b4e-367">TranslationResultText</span></span> |      <span data-ttu-id="46b4e-368">??</span><span class="sxs-lookup"><span data-stu-id="46b4e-368">??</span></span>       | <span data-ttu-id="46b4e-369">20</span><span class="sxs-lookup"><span data-stu-id="46b4e-369">20</span></span>           |

9. <span data-ttu-id="46b4e-370">Successivamente, selezionare l'opzione di allineamento 'centre' per ogni componente di testo:</span><span class="sxs-lookup"><span data-stu-id="46b4e-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![Allinea il testo.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="46b4e-372">Per garantire la **testo dell'interfaccia utente figlio** gli oggetti sono facilmente leggibili, modificare le *colore*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="46b4e-373">Eseguire questa operazione, fare clic sulla barra dei (attualmente ' nero') accanto a *colore*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Immettere i valori per gli output di testo dell'interfaccia utente corrispondente.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="46b4e-375">Quindi, nella nuova, piccola, *colore* finestra Modifica il *colore esadecimale* per: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="46b4e-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Aggiornare il colore blu.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="46b4e-377">Di seguito è riportato il **dell'interfaccia utente** dovrebbe avere un aspetto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="46b4e-378">Nel *gerarchia pannello*:</span><span class="sxs-lookup"><span data-stu-id="46b4e-378">In the *Hierarchy Panel*:</span></span>

        ![La gerarchia è la struttura fornita.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="46b4e-380">Nel *scena* e *visualizzazioni di giochi*:</span><span class="sxs-lookup"><span data-stu-id="46b4e-380">In the *Scene* and *Game Views*:</span></span>

        ![Disporre le visualizzazioni scena e giochi nella stessa struttura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="46b4e-382">Capitolo 5: creare la classe di risultati</span><span class="sxs-lookup"><span data-stu-id="46b4e-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="46b4e-383">È il primo script è necessario creare il *risultati* (classe), che è responsabile di fornire un modo per visualizzare i risultati della conversione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="46b4e-384">La classe archivia e visualizza quanto segue:</span><span class="sxs-lookup"><span data-stu-id="46b4e-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="46b4e-385">Il risultato della risposta da Azure.</span><span class="sxs-lookup"><span data-stu-id="46b4e-385">The response result from Azure.</span></span>
- <span data-ttu-id="46b4e-386">Lo stato di microfono.</span><span class="sxs-lookup"><span data-stu-id="46b4e-386">The microphone status.</span></span> 
- <span data-ttu-id="46b4e-387">Il risultato della dettatura (sintesi vocale).</span><span class="sxs-lookup"><span data-stu-id="46b4e-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="46b4e-388">Il risultato della traduzione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-388">The result of the translation.</span></span>

<span data-ttu-id="46b4e-389">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="46b4e-389">To create this class:</span></span> 

1.  <span data-ttu-id="46b4e-390">Fare doppio clic nella *Pannello di progetto*, quindi **Crea > cartella**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="46b4e-391">Denominare la cartella **script**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-391">Name the folder **Scripts**.</span></span> 
 
    ![Crea cartella scripts.](images/AzureLabs-Lab1-31.png)

    ![Aprire la cartella degli script.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="46b4e-394">Con il **script** cartella creare, fare doppio clic sopra per avviarlo.</span><span class="sxs-lookup"><span data-stu-id="46b4e-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="46b4e-395">Quindi all'interno di tale cartella, pulsante destro del mouse e scegliere **Crea >** quindi  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="46b4e-396">Denominare lo script *risultati*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-396">Name the script *Results*.</span></span> 

    ![Creare il primo script.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="46b4e-398">Fare doppio clic su nuova *risultati* script per aprirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="46b4e-399">Inserisci gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="46b4e-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="46b4e-400">All'interno della classe inserire le variabili seguenti:</span><span class="sxs-lookup"><span data-stu-id="46b4e-400">Inside the Class insert the following variables:</span></span>

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

6.  <span data-ttu-id="46b4e-401">Quindi aggiungere il *Awake()* metodo, che verrà chiamato quando si inizializza la classe.</span><span class="sxs-lookup"><span data-stu-id="46b4e-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="46b4e-402">Infine, aggiungere i metodi che sono responsabili per l'output di varie informazioni relative ai risultati all'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

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

8.  <span data-ttu-id="46b4e-403">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="46b4e-404">Capitolo 6: creare il *MicrophoneManager* classe</span><span class="sxs-lookup"><span data-stu-id="46b4e-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="46b4e-405">Si intende creare la seconda classe è il *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="46b4e-406">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="46b4e-406">This class is responsible for:</span></span>

- <span data-ttu-id="46b4e-407">Rilevamento il dispositivo di registrazione associato a visore VR o machine (a seconda del valore è il valore predefinito).</span><span class="sxs-lookup"><span data-stu-id="46b4e-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="46b4e-408">Acquisire l'audio (voce) e usare la dettatura per archiviarlo sotto forma di stringa.</span><span class="sxs-lookup"><span data-stu-id="46b4e-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="46b4e-409">Dopo la voce è stato sospeso, inviare la dettatura alla classe del convertitore.</span><span class="sxs-lookup"><span data-stu-id="46b4e-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="46b4e-410">Ospitare un metodo che può arrestare l'acquisizione voce se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="46b4e-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="46b4e-411">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="46b4e-411">To create this class:</span></span> 
1.  <span data-ttu-id="46b4e-412">Fare doppio clic sui **script** cartella per aprirla.</span><span class="sxs-lookup"><span data-stu-id="46b4e-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="46b4e-413">Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="46b4e-414">Denominare lo script *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="46b4e-415">Fare doppio clic sul nuovo script per aprirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46b4e-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="46b4e-416">Aggiornare gli spazi dei nomi affinché corrisponda al seguente, in cima il *MicrophoneManager* classe:</span><span class="sxs-lookup"><span data-stu-id="46b4e-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="46b4e-417">Quindi, aggiungere le variabili seguenti all'interno di *MicrophoneManager* classe:</span><span class="sxs-lookup"><span data-stu-id="46b4e-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

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

6.  <span data-ttu-id="46b4e-418">Il codice per il *Awake()* e *Start ()* metodi deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="46b4e-419">Questi verranno chiamati quando inizializza la classe:</span><span class="sxs-lookup"><span data-stu-id="46b4e-419">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="46b4e-420">È possibile *eliminare* le *Update ()* metodo poiché questa classe non verrà utilizzate.</span><span class="sxs-lookup"><span data-stu-id="46b4e-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="46b4e-421">È ora necessario i metodi usati dall'App per avviare e arrestare l'acquisizione voce e passarlo al *traduttore* (classe), che verrà compilata a breve.</span><span class="sxs-lookup"><span data-stu-id="46b4e-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="46b4e-422">Copiare il codice seguente e incollarlo sotto la *Start ()* (metodo).</span><span class="sxs-lookup"><span data-stu-id="46b4e-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

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
    > <span data-ttu-id="46b4e-423">Anche se questa applicazione non apporterà di usarla, il *StopCapturingAudio()* metodo è stato incluso anche in questo caso, se si vuole implementare la possibilità di arrestare l'acquisizione audio nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="46b4e-424">È ora necessario aggiungere un gestore di dettatura che verrà richiamato quando si arresta la voce.</span><span class="sxs-lookup"><span data-stu-id="46b4e-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="46b4e-425">Questo metodo passa il testo dettato per il *traduttore* classe.</span><span class="sxs-lookup"><span data-stu-id="46b4e-425">This method will then pass the dictated text to the *Translator* class.</span></span>

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

10. <span data-ttu-id="46b4e-426">Assicurarsi di salvare le modifiche in Visual Studio prima di tornare a Unity.</span><span class="sxs-lookup"><span data-stu-id="46b4e-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="46b4e-427">A questo punto si noterà un errore dei *Console di Editor di Unity* pannello ("il nome 'Conversione' non esiste...").</span><span class="sxs-lookup"><span data-stu-id="46b4e-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="46b4e-428">Infatti, il codice fa riferimento il *traduttore* (classe), che verrà creato nel capitolo successivo.</span><span class="sxs-lookup"><span data-stu-id="46b4e-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="46b4e-429">Capitolo 7 su chiamata al servizio di Azure e Microsoft translator</span><span class="sxs-lookup"><span data-stu-id="46b4e-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="46b4e-430">È l'ultimo script è necessario creare il *traduttore* classe.</span><span class="sxs-lookup"><span data-stu-id="46b4e-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="46b4e-431">Questa classe è responsabile per:</span><span class="sxs-lookup"><span data-stu-id="46b4e-431">This class is responsible for:</span></span>

-   <span data-ttu-id="46b4e-432">L'autenticazione all'App con *Azure*, in exchange per un' **Token di autenticazione**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="46b4e-433">Usare il **Auth Token** per inviare testo (ricevuto dal *MicrophoneManager* classe) da tradurre.</span><span class="sxs-lookup"><span data-stu-id="46b4e-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="46b4e-434">Ricevere il risultato convertito e passarlo al *risultati* classe da visualizzare nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="46b4e-435">Per creare questa classe:</span><span class="sxs-lookup"><span data-stu-id="46b4e-435">To create this Class:</span></span> 
1.  <span data-ttu-id="46b4e-436">Andare alla **script** cartella creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="46b4e-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="46b4e-437">Fare doppio clic nella **Pannello di progetto**, **Crea > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="46b4e-438">Chiamare lo script *traduttore*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="46b4e-439">Fare doppio clic su nuova *traduttore* script per aprirlo **con Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="46b4e-440">Aggiungere spazi dei nomi seguenti all'inizio del file:</span><span class="sxs-lookup"><span data-stu-id="46b4e-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="46b4e-441">Quindi aggiungere le variabili seguenti all'interno di *traduttore* classe:</span><span class="sxs-lookup"><span data-stu-id="46b4e-441">Then add the following variables inside the *Translator* class:</span></span>

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
    > - <span data-ttu-id="46b4e-442">Le lingue inserite i linguaggi **enum** sono solo esempi.</span><span class="sxs-lookup"><span data-stu-id="46b4e-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="46b4e-443">È possibile aggiungere più se si vuole; il [API supporta oltre 60 lingue](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (inclusi Klingon).</span><span class="sxs-lookup"><span data-stu-id="46b4e-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="46b4e-444">È presente una [pagina più interattiva copertura delle lingue disponibili](https://www.microsoft.com/translator/business/languages/), tenere tuttavia presente la pagina viene visualizzata solo quando la lingua del sito è impostata su "en-us' (e il sito di Microsoft verranno probabilmente di reindirizzamento per la sua lingua madre).</span><span class="sxs-lookup"><span data-stu-id="46b4e-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="46b4e-445">È possibile modificare la lingua nella parte inferiore della pagina o modificando l'URL del sito.</span><span class="sxs-lookup"><span data-stu-id="46b4e-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="46b4e-446">Il **authorizationKey** valore, nel frammento di codice precedente, deve essere il **chiave** ricevuto la sottoscrizione per il *API traduzione testuale di Azure*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="46b4e-447">Questa attività è stata descritta nella [capitolo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="46b4e-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="46b4e-448">Il codice per il *Awake()* e *Start ()* metodi deve ora essere aggiunto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="46b4e-449">In questo caso, il codice effettua una chiamata a *Azure* usando la chiave di autorizzazione per ottenere un *Token*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

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
    > <span data-ttu-id="46b4e-450">Il token scade dopo 10 minuti.</span><span class="sxs-lookup"><span data-stu-id="46b4e-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="46b4e-451">A seconda dello scenario per l'app, potrebbe essere necessario apportare la stessa coroutine chiamare più volte.</span><span class="sxs-lookup"><span data-stu-id="46b4e-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="46b4e-452">Le coroutine per ottenere il Token è il seguente:</span><span class="sxs-lookup"><span data-stu-id="46b4e-452">The coroutine to obtain the Token is the following:</span></span>

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
    > <span data-ttu-id="46b4e-453">Se si modifica il nome del metodo IEnumerator **GetTokenCoroutine()**, è necessario aggiornare il *StartCoroutine* e *StopCoroutine* chiamare i valori stringa nel codice precedente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="46b4e-454">[In base alla documentazione di Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), per arrestare uno specifico *Coroutine*, è necessario usare il metodo di valore di stringa.</span><span class="sxs-lookup"><span data-stu-id="46b4e-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="46b4e-455">Successivamente, aggiungere le coroutine (con un metodo flusso "supporto" immediatamente di sotto) per ottenere la traduzione del testo ricevuto dal *MicrophoneManager* classe.</span><span class="sxs-lookup"><span data-stu-id="46b4e-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="46b4e-456">Questo codice crea una stringa di query da inviare per la *API traduzione testuale Azure*e quindi Usa la classe di Unity UnityWebRequest interna per effettuare una chiamata a 'Get' per l'endpoint con la stringa di query.</span><span class="sxs-lookup"><span data-stu-id="46b4e-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="46b4e-457">Il risultato viene quindi utilizzato per la conversione del set nell'oggetto risultati.</span><span class="sxs-lookup"><span data-stu-id="46b4e-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="46b4e-458">Il codice seguente illustra l'implementazione:</span><span class="sxs-lookup"><span data-stu-id="46b4e-458">The code below shows the implementation:</span></span>

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

10. <span data-ttu-id="46b4e-459">Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="46b4e-460">Capitolo 8: configurare la scena Unity</span><span class="sxs-lookup"><span data-stu-id="46b4e-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="46b4e-461">Indietro nell'Editor di Unity, fare clic e trascinare il *risultati* classe *dalla* il **script** cartella in cui la **Main Camera** oggetto nel  *Pannello gerarchia*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="46b4e-462">Fare clic sui **Main Camera** ed esaminare le *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="46b4e-463">Si noterà che all'interno di appena aggiunta *Script* componente, sono presenti quattro campi con valori vuoti.</span><span class="sxs-lookup"><span data-stu-id="46b4e-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="46b4e-464">Questi sono i riferimenti all'output per le proprietà nel codice.</span><span class="sxs-lookup"><span data-stu-id="46b4e-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="46b4e-465">Trascinare l'appropriato **testo** oggetti dal *gerarchia pannello* a questi quattro slot, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Aggiornare i riferimenti di destinazione con valori specificati.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="46b4e-467">Successivamente, fare clic e trascinare il *Translator* classe il **script** cartella per il **Main Camera** dell'oggetto nel *gerarchia pannello*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="46b4e-468">Quindi fare clic e trascinare il *MicrophoneManager* classe il **script** cartella per il **Main Camera** dell'oggetto nel *gerarchia pannello*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="46b4e-469">Infine, fare clic sui **Main Camera** ed esaminare le *Pannello di controllo*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="46b4e-470">Si noterà che nello script che è stato trascinato sul, esistono due caselle che ti permetterà di impostare le lingue a discesa.</span><span class="sxs-lookup"><span data-stu-id="46b4e-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Verificare che le lingue di traduzione previsto costituiscono l'input.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="46b4e-472">Capitolo 9: Test nella realtà mista</span><span class="sxs-lookup"><span data-stu-id="46b4e-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="46b4e-473">A questo punto è necessario verificare che la scena sia stata implementata correttamente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="46b4e-474">Verifica che:</span><span class="sxs-lookup"><span data-stu-id="46b4e-474">Ensure that:</span></span>

- <span data-ttu-id="46b4e-475">Tutte le impostazioni indicate nella [capitolo 1](#chapter-1--the-azure-portal) siano impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="46b4e-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="46b4e-476">Il *risultati*, *Translator*, e *MicrophoneManager*, gli script sono associati ai **Main Camera** oggetto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="46b4e-477">È stato inserito il *API traduzione testuale di Azure* Service **chiave** all'interno del **authorizationKey** variabile all'interno del *Translator* copione.</span><span class="sxs-lookup"><span data-stu-id="46b4e-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="46b4e-478">Tutti i campi di *Pannello controllo fotocamera principale* vengono assegnati in modo corretto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="46b4e-479">Il microfono funzioni durante l'esecuzione della scena (in caso contrario, verificare che il microfono associato sia la *predefiniti* dispositivo e aver [configurarlo correttamente all'interno di Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="46b4e-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="46b4e-480">È possibile testare il visore VR immersivi premendo la **riprodurre** pulsante il *Editor di Unity*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="46b4e-481">L'App dovrebbe funzionare attraverso il visore VR immersivi collegati.</span><span class="sxs-lookup"><span data-stu-id="46b4e-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="46b4e-482">Se viene visualizzato un errore nella console di Unity sul dispositivo audio predefinito modifica, la scena potrebbe non funzionare come previsto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="46b4e-483">Ciò è dovuto al modo in cui che il portale di realtà mista si occupa microfoni incorporati per auricolari sia disponibile.</span><span class="sxs-lookup"><span data-stu-id="46b4e-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="46b4e-484">Se è visualizzato questo errore, è sufficiente arrestare la scena e avviarla nuovamente e cose dovrebbero funzionare come previsto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="46b4e-485">Capitolo 10: creare la soluzione di piattaforma UWP e trasferirla in locale nel computer locale</span><span class="sxs-lookup"><span data-stu-id="46b4e-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="46b4e-486">Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.</span><span class="sxs-lookup"><span data-stu-id="46b4e-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="46b4e-487">Passare a **impostazioni di compilazione**: **File > Impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="46b4e-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="46b4e-488">Dal **Build Settings** finestra, fare clic su **compilazione**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilare la scena Unity.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="46b4e-490">Se non è già, graduazione **Unity C# progetti**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="46b4e-491">Fai clic su **Compila**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-491">Click **Build**.</span></span> <span data-ttu-id="46b4e-492">Unity avvierà una *Esplora File* finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in.</span><span class="sxs-lookup"><span data-stu-id="46b4e-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="46b4e-493">Creare ora tale cartella e denominarlo *App*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="46b4e-494">Quindi con il *App* cartella selezionata, premere **Seleziona cartella**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="46b4e-495">Unity verrà avviata la compilazione del progetto per la *App* cartella.</span><span class="sxs-lookup"><span data-stu-id="46b4e-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="46b4e-496">Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un *Esplora File* finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).</span><span class="sxs-lookup"><span data-stu-id="46b4e-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="46b4e-497">Capitolo 11: distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="46b4e-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="46b4e-498">Per distribuire l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="46b4e-498">To deploy your application:</span></span>

1.  <span data-ttu-id="46b4e-499">Passare alla nuova build Unity (le *App* cartella) e aprire il file di soluzione con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="46b4e-500">Selezione configurazione di soluzione **Debug**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="46b4e-501">La piattaforma della soluzione, selezionare **x86**, **computer locale**.</span><span class="sxs-lookup"><span data-stu-id="46b4e-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="46b4e-502">Per il Microsoft HoloLens, può risultare più semplice impostare questa opzione su *computer remoto*, in modo che non Windows con tethering al computer in uso.</span><span class="sxs-lookup"><span data-stu-id="46b4e-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="46b4e-503">Tuttavia, è necessario inoltre eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="46b4e-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="46b4e-504">Conoscere il **indirizzo IP** di HoloLens, il che può trovarsi all'interno di *Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo è consigliabile usare.</span><span class="sxs-lookup"><span data-stu-id="46b4e-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="46b4e-505">Assicurarsi *modalità sviluppatore* viene **sul**; è stata trovata nel *Impostazioni > aggiornamento e sicurezza > per gli sviluppatori*.</span><span class="sxs-lookup"><span data-stu-id="46b4e-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="46b4e-507">Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione al computer.</span><span class="sxs-lookup"><span data-stu-id="46b4e-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="46b4e-508">L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.</span><span class="sxs-lookup"><span data-stu-id="46b4e-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="46b4e-509">Una volta avviata, l'App verrà richiesto di autorizzare l'accesso al microfono.</span><span class="sxs-lookup"><span data-stu-id="46b4e-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="46b4e-510">Assicurarsi di selezionare il **Sì** pulsante.</span><span class="sxs-lookup"><span data-stu-id="46b4e-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="46b4e-511">È ora pronti per iniziare a tradurre.</span><span class="sxs-lookup"><span data-stu-id="46b4e-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="46b4e-512">L'applicazione API traduzione testuale conversione completata</span><span class="sxs-lookup"><span data-stu-id="46b4e-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="46b4e-513">Complimenti, è stata compilata un'app per realtà mista che sfrutta l'API di testo Azure traduzioni per convertire testo parlato in testo tradotto.</span><span class="sxs-lookup"><span data-stu-id="46b4e-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Prodotto finale.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="46b4e-515">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="46b4e-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="46b4e-516">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="46b4e-516">Exercise 1</span></span>

<span data-ttu-id="46b4e-517">È possibile aggiungere funzionalità di sintesi vocale per l'app, in modo che il testo restituito viene pronunciato?</span><span class="sxs-lookup"><span data-stu-id="46b4e-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="46b4e-518">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="46b4e-518">Exercise 2</span></span>

<span data-ttu-id="46b4e-519">Consentono all'utente di modificare le lingue di origine e di output ('from' e 'a') all'interno dell'app stessa, in modo che l'app non dovrà essere ricompilato ogni volta che si desidera modificare le lingue.</span><span class="sxs-lookup"><span data-stu-id="46b4e-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
