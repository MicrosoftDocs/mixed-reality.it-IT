---
title: Esercitazioni sulle funzionalità multiutente - 3. Connessione di più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376393"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="62039-105">3. Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="62039-105">3. Connecting multiple users</span></span>

<span data-ttu-id="62039-106">In questa esercitazione imparerai a connettere più utenti all'interno di un'esperienza live condivisa.</span><span class="sxs-lookup"><span data-stu-id="62039-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="62039-107">Al termine dell'esercitazione sarà possibile eseguire l'app in più dispositivi e fare in modo che ogni utente visualizzi l'avatar degli altri utenti muoversi in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="62039-107">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="62039-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="62039-108">Objectives</span></span>

* <span data-ttu-id="62039-109">Imparare a connettere più utenti in un'esperienza condivisa</span><span class="sxs-lookup"><span data-stu-id="62039-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="62039-110">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="62039-110">Preparing the scene</span></span>

<span data-ttu-id="62039-111">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="62039-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="62039-112">Nella finestra Project (Progetto) passare alla cartella **Assets**  (Asset)  > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e quindi fare clic e trascinare i prefab seguenti sulla finestra Hierarchy (Gerarchia) per aggiungerli alla scena:</span><span class="sxs-lookup"><span data-stu-id="62039-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="62039-113">Prefab **NetworkLobby**</span><span class="sxs-lookup"><span data-stu-id="62039-113">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="62039-114">Prefab **SharedPlayground**</span><span class="sxs-lookup"><span data-stu-id="62039-114">**SharedPlayground** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="62039-116">Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Prefab) e quindi fare clic e trascinare il prefab seguente sulla finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:</span><span class="sxs-lookup"><span data-stu-id="62039-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="62039-117">Prefab **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="62039-117">**DebugWindow** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="62039-119">Creazione del prefab dell'utente</span><span class="sxs-lookup"><span data-stu-id="62039-119">Creating the user prefab</span></span>

<span data-ttu-id="62039-120">In questa sezione creerai un prefab che verrà usato per rappresentare gli utenti nell'esperienza condivisa.</span><span class="sxs-lookup"><span data-stu-id="62039-120">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="62039-121">1. Creare e configurare l'utente</span><span class="sxs-lookup"><span data-stu-id="62039-121">1. Create and configure the user</span></span>

<span data-ttu-id="62039-122">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su un'area vuota e seleziona **Create Empty** (Crea vuoto) per aggiungere alla scena un oggetto vuoto, assegna all'oggetto il nome **PhotonUser** e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="62039-122">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="62039-123">Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0:</span><span class="sxs-lookup"><span data-stu-id="62039-123">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="62039-125">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **PhotonUser** e quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon User (Script)** (Utente Photon - Script) all'oggetto PhotonUser:</span><span class="sxs-lookup"><span data-stu-id="62039-125">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="62039-127">Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Generic Net Sync (Script)** (Sincronizzazione rete generica - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="62039-127">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="62039-128">Seleziona la casella di controllo **Is User** (È utente)</span><span class="sxs-lookup"><span data-stu-id="62039-128">Check the **Is User** checkbox</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="62039-130">Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Photon View (Script)** (Visualizzazione Photon - Script) all'oggetto PhotonUser e configura l'oggetto nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="62039-130">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="62039-131">Al campo **Observed Components** (Componenti osservati) assegnare il componente **Generic Net Sync (Script)** (Sincronizzazione rete generica - Script)</span><span class="sxs-lookup"><span data-stu-id="62039-131">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="62039-133">2. Creare l'avatar</span><span class="sxs-lookup"><span data-stu-id="62039-133">2. Create the avatar</span></span>

<span data-ttu-id="62039-134">Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK** > **SDK** > **StandardAssets** > **Materials** (Materiali) per individuare i materiali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="62039-134">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="62039-135">Nella finestra Hierarchy (Gerarchia) fare quindi clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e selezionare **3D Object** > **Sphere** (Oggetto 3D > Sfera) per creare un oggetto sfera come elemento figlio dell'oggetto PhotonUser e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="62039-135">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="62039-136">Verifica che il campo **Position** (Posizione) della trasformazione sia impostato su X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="62039-136">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="62039-137">Imposta il campo **Scale** (Ridimensiona) della trasformazione su una dimensione appropriata, ad esempio X = 0.15, Y = 0.15, Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="62039-137">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="62039-138">Al campo MeshRenderer > Materials > **Element 0** (Materiali > Elemento 0) assegnare il materiale **MRTK_Standard_White**</span><span class="sxs-lookup"><span data-stu-id="62039-138">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="62039-140">3. Creare il prefab</span><span class="sxs-lookup"><span data-stu-id="62039-140">3. Create the prefab</span></span>

<span data-ttu-id="62039-141">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse):</span><span class="sxs-lookup"><span data-stu-id="62039-141">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="62039-143">Con la cartella Resources (Risorse) ancora selezionata, **fai clic e trascina** l'oggetto **PhotonUser** dalla finestra Hierarchy (Gerarchia) nella cartella **Resources** (Risorse) per convertire l'oggetto PhotonUser in un prefab:</span><span class="sxs-lookup"><span data-stu-id="62039-143">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="62039-145">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse sull'oggetto **PhotonUser** e seleziona **Delete** (Elimina) per rimuovere l'oggetto dalla scena:</span><span class="sxs-lookup"><span data-stu-id="62039-145">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="62039-147">Configurazione di PUN per creare un'istanza del prefab dell'utente</span><span class="sxs-lookup"><span data-stu-id="62039-147">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="62039-148">In questa sezione configurerai il progetto per l'uso del prefab PhotonUser creato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="62039-148">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="62039-149">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).</span><span class="sxs-lookup"><span data-stu-id="62039-149">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="62039-150">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="62039-150">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="62039-151">Al campo **Photon User Prefab** (Prefab utente Photon) assegna il prefab **PhotonUser** dalla cartella Resources (Risorse)</span><span class="sxs-lookup"><span data-stu-id="62039-151">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="62039-153">Prova dell'esperienza con più utenti</span><span class="sxs-lookup"><span data-stu-id="62039-153">Trying the experience with multiple users</span></span>

<span data-ttu-id="62039-154">Se si compila e distribuisce il progetto Unity in HoloLens e quindi, tornando in Unity, si attiva la modalità di gioco mentre l'app è in esecuzione in HoloLens, si visualizzerà l'avatar dell'utente HoloLens muoversi quando si muove la testa (HoloLens):</span><span class="sxs-lookup"><span data-stu-id="62039-154">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="62039-156">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="62039-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="62039-157">Poiché l'app deve connettersi a Photon, assicurarsi che il computer o il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="62039-157">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="62039-158">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="62039-158">Congratulations</span></span>

<span data-ttu-id="62039-159">Hai configurato il progetto per consentire a più utenti di connettersi alla stessa esperienza e vedere i movimenti gli uni degli altri.</span><span class="sxs-lookup"><span data-stu-id="62039-159">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="62039-160">Nella prossima esercitazione implementerai le funzionalità in modo che anche i movimenti degli oggetti vengano condivisi tra più dispositivi.</span><span class="sxs-lookup"><span data-stu-id="62039-160">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

[<span data-ttu-id="62039-161">Esercitazione successiva: 4. Condivisione dei movimenti di oggetti con più utenti</span><span class="sxs-lookup"><span data-stu-id="62039-161">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
