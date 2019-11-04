---
title: Debug gestito con Unity IL2CPP
description: Questo articolo illustra come eseguire un debugger gestito nel progetto Unity IL2CPP UWP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, debug, il2cpp
ms.openlocfilehash: fd09c3ca1bd410c56e46eb8e8815742f87482d08
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439632"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="6e579-104">Debug gestito con Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="6e579-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="6e579-105">Seguire questa procedura per aggiungere un debugger gestito alla build Unity IL2CPP UWP.</span><span class="sxs-lookup"><span data-stu-id="6e579-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="6e579-106">Questa guida è stata sviluppata in origine per HoloLens e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6e579-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="6e579-107">È necessario trovarsi in una rete che supporta il [multicast](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="6e579-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="6e579-108">Verificare che **InternetClientServer** e **PrivateNetworkClientServer** siano archiviati in Unity con le funzionalità delle impostazioni di pubblicazione di UWP.</span><span class="sxs-lookup"><span data-stu-id="6e579-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Funzionalità delle impostazioni di pubblicazione UWP](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="6e579-110">Configurare le impostazioni di compilazione UWP per Unity:</span><span class="sxs-lookup"><span data-stu-id="6e579-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="6e579-111">Compilazione di sviluppo</span><span class="sxs-lookup"><span data-stu-id="6e579-111">Development Build</span></span>
    - <span data-ttu-id="6e579-112">Debug degli script</span><span class="sxs-lookup"><span data-stu-id="6e579-112">Script Debugging</span></span>
    - <span data-ttu-id="6e579-113">Attendi debugger gestito (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="6e579-113">Wait for Managed Debugger (optional)</span></span>

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="6e579-115">Compilazione in Unity.</span><span class="sxs-lookup"><span data-stu-id="6e579-115">Build in Unity.</span></span>
1. <span data-ttu-id="6e579-116">Compilare e distribuire dalla soluzione Visual Studio al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6e579-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="6e579-117">È necessario compilare con le configurazioni di **debug** o di **rilascio** .</span><span class="sxs-lookup"><span data-stu-id="6e579-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="6e579-118">La configurazione **Master** Disabilita il profiler di Unity ed è in grado di impedire il debug ottimale.</span><span class="sxs-lookup"><span data-stu-id="6e579-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="6e579-119">Facoltativamente, verificare la **connessione Internet (client & Server)** e le **Reti Private (client & Server)** nell'elenco delle funzionalità di Package. appxmanifest nella soluzione.</span><span class="sxs-lookup"><span data-stu-id="6e579-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="6e579-120">Avviare l'app nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6e579-120">Start the app on your device.</span></span> <span data-ttu-id="6e579-121">Verificare che il dispositivo sia connesso alla stessa rete del computer.</span><span class="sxs-lookup"><span data-stu-id="6e579-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="6e579-122">Verificare che il dispositivo **non sia** connesso al PC tramite USB.</span><span class="sxs-lookup"><span data-stu-id="6e579-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="6e579-123">Passare alla soluzione Visual Studio creata quando si fa doppio clic su uno script in Unity, in cui è possibile visualizzare e modificare C# gli script.</span><span class="sxs-lookup"><span data-stu-id="6e579-123">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="6e579-124">Debug-> connessione del debugger Unity.</span><span class="sxs-lookup"><span data-stu-id="6e579-124">Debug -> Attach Unity Debugger.</span></span>

    ![Connetti debugger Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="6e579-126">Selezionare il dispositivo nell'elenco e fare clic su "OK" per connettersi.</span><span class="sxs-lookup"><span data-stu-id="6e579-126">Select your device in the list and click "OK" to attach.</span></span>

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)
