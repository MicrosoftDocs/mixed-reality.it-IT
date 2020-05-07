---
title: Esercitazioni sulle funzionalità multiutente - 4. Condivisione dei movimenti di oggetti con più utenti
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610645"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="f3812-105">3. Condivisione dei movimenti di oggetti con più utenti</span><span class="sxs-lookup"><span data-stu-id="f3812-105">3. Sharing object movements with multiple users</span></span>

<span data-ttu-id="f3812-106">In questa esercitazione imparerai a condividere i movimenti degli oggetti in modo che tutti i partecipanti di un'esperienza condivisa possano collaborare e visualizzare le interazioni reciproche.</span><span class="sxs-lookup"><span data-stu-id="f3812-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each others' interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="f3812-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f3812-107">Objectives</span></span>

* <span data-ttu-id="f3812-108">Configurare il progetto per condividere i movimenti degli oggetti</span><span class="sxs-lookup"><span data-stu-id="f3812-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="f3812-109">Imparare a creare un'applicazione collaborativa multiutente di base</span><span class="sxs-lookup"><span data-stu-id="f3812-109">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="f3812-110">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="f3812-110">Preparing the scene</span></span>

<span data-ttu-id="f3812-111">In questa sezione preparerai la scena aggiungendo il prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="f3812-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="f3812-112">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e trascina il prefab **TableAnchor** nella parte superiore dell'oggetto **SharedPlayground** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena come elemento figlio dell'oggetto SharedPlayground:</span><span class="sxs-lookup"><span data-stu-id="f3812-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab on top of the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="f3812-114">Configurazione di PUN per creare un'istanza degli oggetti</span><span class="sxs-lookup"><span data-stu-id="f3812-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="f3812-115">In questa sezione configurerai il progetto per l'uso del prefab RocketLauncher_Complete_Variant creato nella sezione precedente e definirai la posizione in cui verrà creata l'istanza.</span><span class="sxs-lookup"><span data-stu-id="f3812-115">In this section, you will configure the project to use the RocketLauncher_Complete_Variant prefab you created in the previous section and define where it will be instantiated.</span></span>

<span data-ttu-id="f3812-116">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Risorse).</span><span class="sxs-lookup"><span data-stu-id="f3812-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="f3812-117">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **NetworkLobby** e seleziona l'oggetto figlio **NetworkRoom** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="f3812-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="f3812-118">Al campo **Photon User Prefab** (Prefab utente Photon) assegna il prefab **PhotonUser** dalla cartella Resources (Risorse)</span><span class="sxs-lookup"><span data-stu-id="f3812-118">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

<span data-ttu-id="f3812-120">Con l'oggetto figlio **NetworkRoom** ancora selezionato, nella finestra Hierarchy (Gerarchia) espandi l'oggetto **TableAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Photon Room (Script)** (Stanza Photon - Script) e configuralo nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="f3812-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="f3812-121">Al campo **Rocket Launcher Location** (Posizione lanciamissili) assegna l'oggetto figlio **Table** dalla finestra Hierarchy (Gerarchia)</span><span class="sxs-lookup"><span data-stu-id="f3812-121">To the **Rocket Launcher Location** field, assign the **Table** child object from the Hierarchy window</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="f3812-123">Prova dell'esperienza con il movimento di un oggetto condiviso</span><span class="sxs-lookup"><span data-stu-id="f3812-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="f3812-124">Se ora compili e distribuisci il progetto Unity in HoloLens e quindi, tornando in Unity, premi il pulsante Play per attivare la modalità di gioco mentre l'applicazione è in esecuzione in HoloLens, vedrai l'oggetto muoversi in Unity quando lo muovi in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="f3812-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="f3812-126">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="f3812-126">Congratulations</span></span>

<span data-ttu-id="f3812-127">Hai configurato il progetto in modo che i movimenti degli oggetti siano sincronizzati e gli utenti possano vedere gli oggetti muoversi quando vengono mossi da altri utenti.</span><span class="sxs-lookup"><span data-stu-id="f3812-127">You have successfully configured your project so object movements are synchronized and users can see the objects move when other users move the objects.</span></span> <span data-ttu-id="f3812-128">Nella prossima esercitazione implementerai le funzionalità in modo che l'esperienza condivisa sia allineata nel mondo fisico, gli utenti possano vedersi nella rispettiva posizione fisica effettiva e quindi gli oggetti vengano visualizzati nella stessa posizione fisica e con la medesima rotazione per tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="f3812-128">In the next tutorial, you will implement functionality so the shared experience is aligned in the physical world and the users see each other in their actual physical location and so the objects appear in the same physical position and rotation for all users.</span></span>

<span data-ttu-id="f3812-129">[Esercitazione successiva: 4. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="f3812-129">[Next tutorial: 4. Integrating Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch4.md)</span></span>
