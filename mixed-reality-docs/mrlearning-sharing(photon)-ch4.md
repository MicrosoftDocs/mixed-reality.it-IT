---
title: Esercitazioni sulle funzionalità multiutente - 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604972"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="8b4cb-105">4. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="8b4cb-105">4. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="8b4cb-106">In questa esercitazione apprenderai come integrare Ancoraggi nello spazio di Azure nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="8b4cb-107">Ancoraggi nello spazio di Azure consente a più dispositivi di avere un riferimento comune al mondo fisico, in modo che gli utenti possano vedersi reciprocamente nella rispettiva posizione fisica effettiva e vedere l'esperienza condivisa nella medesima posizione.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="8b4cb-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="8b4cb-108">Objectives</span></span>

* <span data-ttu-id="8b4cb-109">Integrare Ancoraggi nello spazio di Azure in un'esperienza condivisa per l'allineamento di più dispositivi</span><span class="sxs-lookup"><span data-stu-id="8b4cb-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="8b4cb-110">Apprendere le nozioni di base sul funzionamento di Ancoraggi nello spazio di Azure nel contesto di un'esperienza condivisa locale</span><span class="sxs-lookup"><span data-stu-id="8b4cb-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="8b4cb-111">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="8b4cb-111">Preparing the scene</span></span>

<span data-ttu-id="8b4cb-112">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **SharedPlayground** e quindi l'oggetto **TableAnchor** per esporre i relativi oggetti figlio:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

<span data-ttu-id="8b4cb-114">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e trascina il prefab **Buttons** nella parte superiore dell'oggetto figlio **TableAnchor** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena come elemento figlio dell'oggetto TableAnchor:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab on top of the **TableAnchor** child object in the Hierarchy window to add it to your scene as a child of the TableAnchor object:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="8b4cb-116">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="8b4cb-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="8b4cb-117">In questa sezione configurerai una serie di eventi Button che illustrano le nozioni di base per poter usare Ancoraggi nello spazio di Azure e ottenere l'allineamento spaziale in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-117">In this section, you will configure a series of button events that demonstrate the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="8b4cb-118">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **Button** e seleziona il primo oggetto pulsante figlio denominato **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

<span data-ttu-id="8b4cb-120">Nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="8b4cb-121">Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-121">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="8b4cb-122">Nell'elenco a discesa **No Function** (Nessuna funzione) seleziona la funzione **AnchorModuleScript** > **StartAzureSession ()**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-122">From **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

<span data-ttu-id="8b4cb-124">Nella finestra Hierarchy (Gerarchia) seleziona il secondo oggetto pulsante figlio denominato **CreateAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="8b4cb-125">Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-125">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="8b4cb-126">Nell'elenco a discesa **No Function** (Nessuna funzione) seleziona la funzione **AnchorModuleScript** > **CreateAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-126">From **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="8b4cb-127">Al nuovo campo **None (Game Object)** (Nessuno - Oggetto gioco) che viene visualizzato assegna l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

<span data-ttu-id="8b4cb-129">Nella finestra Hierarchy (Gerarchia) seleziona il terzo oggetto pulsante figlio denominato **ShareAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="8b4cb-130">Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-130">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="8b4cb-131">Nell'elenco a discesa **No Function** (Nessuna funzione) seleziona la funzione **SharingModuleScript** > **ShareAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-131">From **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

<span data-ttu-id="8b4cb-133">Nella finestra Hierarchy (Gerarchia) seleziona il quarto oggetto pulsante figlio denominato **GetAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-133">In the Hierarchy window, select the forth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="8b4cb-134">Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-134">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="8b4cb-135">Nell'elenco a discesa **No Function** (Nessuna funzione) seleziona la funzione **SharingModuleScript** > **GetAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="8b4cb-135">From **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="8b4cb-137">Connessione della scena alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="8b4cb-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="8b4cb-138">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **SharedPlayground** e seleziona l'oggetto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span> <span data-ttu-id="8b4cb-139">Nella finestra Inspector (Controllo) individua quindi il componente **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - Script) e configura la sezione **Credentials** (Credenziali) con le credenziali dell'account di Ancoraggi nello spazio di Azure creato in fase di definizione dei [Prerequisiti](mrlearning-sharing(photon)-ch1.md#prerequisites) per questa serie di esercitazioni:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-139">Then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mrlearning-sharing(photon)-ch1.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="8b4cb-140">Nel campo **Spatial Anchors Account ID** (ID account Ancoraggi nello spazio) incolla il valore di **Account ID** (ID account) del tuo account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="8b4cb-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="8b4cb-141">Nel campo **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio) incolla il valore di **Access Key** (Chiave di accesso) primario o secondario del tuo account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="8b4cb-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

<span data-ttu-id="8b4cb-143">Con l'oggetto **TableAnchor** ancora selezionato, nella finestra Inspector (Controllo) verifica che tutti i componenti di script siano abilitati:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-143">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are enabled:</span></span>

* <span data-ttu-id="8b4cb-144">Seleziona la casella di controllo accanto a **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - Script) per abilitarlo</span><span class="sxs-lookup"><span data-stu-id="8b4cb-144">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="8b4cb-145">Seleziona la casella di controllo accanto a **Anchor Module Script (Script)** (Script modulo di ancoraggio - Script) per abilitarlo</span><span class="sxs-lookup"><span data-stu-id="8b4cb-145">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="8b4cb-146">Seleziona la casella di controllo accanto a **Sharing Module Script (Script)** (Script modulo di condivisione - Script) per abilitarlo</span><span class="sxs-lookup"><span data-stu-id="8b4cb-146">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="8b4cb-148">Prova dell'esperienza con l'allineamento spaziale</span><span class="sxs-lookup"><span data-stu-id="8b4cb-148">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="8b4cb-149">Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-149">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="8b4cb-150">Pertanto, per testare la funzionalità di questo servizio devi distribuire il progetto in almeno due dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-150">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two HoloLens devices.</span></span>

<span data-ttu-id="8b4cb-151">Se ora compili e distribuisci il progetto Unity in due dispositivi HoloLens, puoi ottenere l'allineamento spaziale tra i dispositivi condividendo l'ID ancoraggio di Azure.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-151">If you now build and deploy the Unity project to two HoloLens devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="8b4cb-152">Per provare, puoi seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="8b4cb-152">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="8b4cb-153">Sul dispositivo HoloLens 1 - **Avvia l'applicazione** (è stata creata un'istanza di Rocket Launcher e posizionata sulla tabella)</span><span class="sxs-lookup"><span data-stu-id="8b4cb-153">On HoloLens device 1: **Start the application** (the Rocket Launcher is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="8b4cb-154">Sul dispositivo HoloLens 2 - **Avvia l'applicazione** (entrambi gli utenti vedono la tabella con Rocket Launcher, ma la tabella non è visualizzata nella stessa posizione e gli avatar degli utenti non compaiono nella posizione reale degli utenti)</span><span class="sxs-lookup"><span data-stu-id="8b4cb-154">On HoloLens device 2: **Start the application** (both users see the table with the Rocket Launcher, however, the table does not appear in the same place and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="8b4cb-155">Sul dispositivo HoloLens 1 - Premi il pulsante **Start Azure Session** (Avvia sessione di Azure)</span><span class="sxs-lookup"><span data-stu-id="8b4cb-155">On HoloLens device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="8b4cb-156">Sul dispositivo HoloLens 1 - Premi il pulsante **Create Azure Anchor** (Crea ancoraggio di Azure) (crea l'ancoraggio nella posizione dell'oggetto TableAnchor e archivia le informazioni relative all'ancoraggio nella risorsa di Azure).</span><span class="sxs-lookup"><span data-stu-id="8b4cb-156">On HoloLens device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="8b4cb-157">Sul dispositivo HoloLens 1 - Premi il pulsante **Share Azure Anchor** (Condividi ancoraggio di Azure) (condivide l'ID ancoraggio con altri utenti in tempo reale)</span><span class="sxs-lookup"><span data-stu-id="8b4cb-157">On HoloLens device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="8b4cb-158">Sul dispositivo HoloLens 2 - Premi il pulsante **Start Azure Session** (Avvia sessione di Azure)</span><span class="sxs-lookup"><span data-stu-id="8b4cb-158">On HoloLens device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="8b4cb-159">Sul dispositivo HoloLens 2 - Premi il pulsante **Get Azure Anchor** (Ottieni ancoraggio di Azure) (si connette alla risorsa di Azure per recuperare le informazioni relative all'ancoraggio per l'ID ancoraggio condiviso e quindi sposta l'oggetto TableAnchor nella posizione in cui è stato creato l'ancoraggio con il dispositivo HoloLens 1)</span><span class="sxs-lookup"><span data-stu-id="8b4cb-159">On HoloLens device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the HoloLens device 1)</span></span>

## <a name="congratulations"></a><span data-ttu-id="8b4cb-160">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="8b4cb-160">Congratulations</span></span>

<span data-ttu-id="8b4cb-161">In questa esercitazione hai appreso come integrare il potente servizio Ancoraggi nello spazio di Azure per allineare i dispositivi in un'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-161">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span> <span data-ttu-id="8b4cb-162">Si conclude così la serie di esercitazioni in cui hai appreso come impostare un account e un'applicazione Photon, integrare Photon e PUN in un'applicazione Unity, configurare gli avatar degli utenti e gli oggetti condivisi e infine allineare più partecipanti con Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="8b4cb-162">This also concludes this tutorial series where you have learned how to set up a Photon account and application, integrate Photon and PUN into a Unity application, configure user avatars and shared objects, and finally align multiple participants using ASA.</span></span>
