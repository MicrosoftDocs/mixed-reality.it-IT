---
title: Esercitazioni sulle funzionalità multiutente - 3. Connessione di più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610912"
---
# <a name="2-connecting-multiple-users"></a><span data-ttu-id="d1dbd-105">2. Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="d1dbd-105">2. Connecting multiple users</span></span>

<span data-ttu-id="d1dbd-106">In questa esercitazione imparerai a connettere più utenti all'interno di un'esperienza live condivisa.</span><span class="sxs-lookup"><span data-stu-id="d1dbd-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="d1dbd-107">Al termine dell'esercitazione sarai in grado di eseguire l'applicazione in più dispositivi e fare in modo che ogni utente veda che l'avatar degli altri utenti muoversi in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="d1dbd-107">By the end of the tutorial you will be able to run the application on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="d1dbd-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="d1dbd-108">Objectives</span></span>

* <span data-ttu-id="d1dbd-109">Imparare a connettere più utenti in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="d1dbd-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="d1dbd-110">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="d1dbd-110">Preparing the scene</span></span>

<span data-ttu-id="d1dbd-111">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="d1dbd-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="d1dbd-112">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab).</span><span class="sxs-lookup"><span data-stu-id="d1dbd-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder.</span></span> <span data-ttu-id="d1dbd-113">Tenendo premuto il pulsante CTRL, fai clic su **DebugWindow**, **NetworkLobby** e **SharedPlayground** per selezionare i tre prefab:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-113">While holding down the CTRL button, click on **DebugWindow**, **NetworkLobby**, and **SharedPlayground** to select the three prefabs:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

<span data-ttu-id="d1dbd-115">Trascina i tre prefab ancora selezionati nella finestra Hierarchy (Gerarchia) per aggiungerli alla scena:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-115">With the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="d1dbd-117">Creazione del prefab dell'utente</span><span class="sxs-lookup"><span data-stu-id="d1dbd-117">Creating the user prefab</span></span>

<span data-ttu-id="d1dbd-118">In questa sezione creerai un prefab che verrà usato per rappresentare gli utenti nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="d1dbd-118">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="d1dbd-119">1. Creare e configurare l'utente</span><span class="sxs-lookup"><span data-stu-id="d1dbd-119">1. Create and configure the user</span></span>

<span data-ttu-id="d1dbd-120">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su un'area vuota e seleziona **Create Empty** (Crea vuoto) per aggiungere alla scena un oggetto vuoto, assegna all'oggetto il nome **PhotonUser** e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-120">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="d1dbd-121">Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-121">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

<span data-ttu-id="d1dbd-123">Con l'oggetto **PhotonUser** ancora selezionato, nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon User (Script)** (Utente Photon - Script) all'oggetto PhotonUser:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-123">With the **PhotonUser** object still selected, in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

<span data-ttu-id="d1dbd-125">Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Generic Net Sync (Script)** (Sincronizzazione rete generica - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-125">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="d1dbd-126">Seleziona la casella di controllo **Is User** (È utente)</span><span class="sxs-lookup"><span data-stu-id="d1dbd-126">Check the **Is User** checkbox</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

<span data-ttu-id="d1dbd-128">Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon View (Script)** (Visualizzazione Photon - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-128">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="d1dbd-129">Al campo **Observed Components** (Componenti osservati) assegna il componente Generic Net Sync (Script) (Sincronizzazione rete generica - Script)</span><span class="sxs-lookup"><span data-stu-id="d1dbd-129">To the **Observed Components** field, assign the Generic Net Sync (Script) component</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="d1dbd-131">2. Creare l'avatar</span><span class="sxs-lookup"><span data-stu-id="d1dbd-131">2. Create the avatar</span></span>

<span data-ttu-id="d1dbd-132">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e seleziona **3D Object** (Oggetto 3D) > **Sphere** per creare un oggetto sfera come elemento figlio dell'oggetto PhotonUser e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-132">In the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="d1dbd-133">Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="d1dbd-133">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="d1dbd-134">Imposta il campo **Scale** (Ridimensiona) della trasformazione su una dimensione appropriata, ad esempio X = 0.15, Y = 0.15, Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="d1dbd-134">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="d1dbd-136">3. Creare il prefab</span><span class="sxs-lookup"><span data-stu-id="d1dbd-136">3. Create the prefab</span></span>

<span data-ttu-id="d1dbd-137">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse):</span><span class="sxs-lookup"><span data-stu-id="d1dbd-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

<span data-ttu-id="d1dbd-139">Con la cartella Resources (Risorse) ancora selezionata, **fai clic e trascina** l'oggetto **PhotonUser** dalla finestra Hierarchy (Gerarchia) nella cartella **Resources** (Risorse) per convertire l'oggetto PhotonUser in un prefab:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-139">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

<span data-ttu-id="d1dbd-141">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e seleziona **Delete** (Elimina) per rimuovere l'oggetto dalla scena:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-141">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="d1dbd-143">Configurazione di PUN per creare un'istanza del prefab dell'utente</span><span class="sxs-lookup"><span data-stu-id="d1dbd-143">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="d1dbd-144">In questa sezione configurerai il progetto per l'uso del prefab PhotonUser creato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="d1dbd-144">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="d1dbd-145">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).</span><span class="sxs-lookup"><span data-stu-id="d1dbd-145">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="d1dbd-146">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="d1dbd-146">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="d1dbd-147">Al campo **Photon User Prefab** (Prefab utente Photon) assegna il prefab **PhotonUser** dalla cartella Resources (Risorse)</span><span class="sxs-lookup"><span data-stu-id="d1dbd-147">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="d1dbd-149">Prova dell'esperienza con più utenti</span><span class="sxs-lookup"><span data-stu-id="d1dbd-149">Trying the experience with multiple users</span></span>

<span data-ttu-id="d1dbd-150">Se ora compili e distribuisci il progetto Unity in HoloLens e quindi, tornando in Unity, premi il pulsante Play per attivare la modalità di gioco mentre l'applicazione è in esecuzione in HoloLens, vedrai l'avatar dell'utente HoloLens muoversi quando muovi la testa (HoloLens):</span><span class="sxs-lookup"><span data-stu-id="d1dbd-150">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="d1dbd-152">Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilare l'applicazione nel dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="d1dbd-152">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="d1dbd-153">Poiché l'applicazione deve connettersi a Photon, assicurati che il computer o il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="d1dbd-153">The application needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d1dbd-154">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="d1dbd-154">Congratulations</span></span>

<span data-ttu-id="d1dbd-155">Hai configurato il progetto per consentire a più utenti di connettersi alla stessa esperienza e vedere i movimenti gli uni degli altri.</span><span class="sxs-lookup"><span data-stu-id="d1dbd-155">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="d1dbd-156">Nella prossima esercitazione implementerai le funzionalità in modo che anche i movimenti degli oggetti vengano condivisi tra più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="d1dbd-156">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

<span data-ttu-id="d1dbd-157">[Esercitazione successiva: 2. Condivisione dei movimenti di oggetti con più utenti](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="d1dbd-157">[Next tutorial: 2. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
