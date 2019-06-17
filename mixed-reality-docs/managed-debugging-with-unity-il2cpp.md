---
title: Il debug con Unity IL2CPP gestito
description: Questo articolo illustra come eseguire un debugger gestito nel progetto Unity IL2CPP UWP.
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: Unity, visual studio, il debug, il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148856"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="cd5b6-104">Il debug con Unity IL2CPP gestito</span><span class="sxs-lookup"><span data-stu-id="cd5b6-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="cd5b6-105">Seguire questi passaggi per collegare un debugger gestito per la compilazione di Unity IL2CPP UWP.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="cd5b6-106">Questa guida è stato originariamente sviluppata per HoloLens e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="cd5b6-107">Assicurarsi che **InternetClientServer** e **PrivateNetworkClientServer** vengono controllate in Unity con le funzionalità di impostazioni di pubblicazione di piattaforma UWP.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-107">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Piattaforma UWP funzionalità impostazioni di pubblicazione](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="cd5b6-109">Configurare le impostazioni di compilazione UWP Unity:</span><span class="sxs-lookup"><span data-stu-id="cd5b6-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="cd5b6-110">Build di sviluppo</span><span class="sxs-lookup"><span data-stu-id="cd5b6-110">Development Build</span></span>
    - <span data-ttu-id="cd5b6-111">Debug degli script</span><span class="sxs-lookup"><span data-stu-id="cd5b6-111">Script Debugging</span></span>
    - <span data-ttu-id="cd5b6-112">Attendere che il Debugger gestito (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="cd5b6-112">Wait for Managed Debugger (optional)</span></span>

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="cd5b6-114">Compilare in Unity.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-114">Build in Unity.</span></span>
1. <span data-ttu-id="cd5b6-115">Compilare e distribuire dalla soluzione di Visual Studio al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="cd5b6-116">È necessario compilare con la **Debug** oppure **versione** configurazioni.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="cd5b6-117">Il **Master** configurazione consente di disattivare il profiler di Unity e può impedire il debug ottimale.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="cd5b6-118">Facoltativamente, verificare **Internet (Client e Server)** e **reti Private (Client e Server)** nell'elenco di funzionalità nel package. appxmanifest nella soluzione.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="cd5b6-119">Avviare l'app nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-119">Start the app on your device.</span></span> <span data-ttu-id="cd5b6-120">Assicurarsi che il dispositivo è connesso alla stessa rete dei PC.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-120">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="cd5b6-121">Assicurarsi che il dispositivo **non è** connesso al PC tramite USB.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-121">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="cd5b6-122">Passare alla soluzione di Visual Studio che viene creata quando si fa doppio clic uno script di Unity, in cui è possibile visualizzare e modificare il C# script.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-122">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="cd5b6-123">Debug -> Collega Debugger Unity.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-123">Debug -> Attach Unity Debugger.</span></span>

    ![Collega Debugger Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="cd5b6-125">Selezionare il dispositivo nell'elenco e fare clic su "OK" per collegare.</span><span class="sxs-lookup"><span data-stu-id="cd5b6-125">Select your device in the list and click "OK" to attach.</span></span>

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)
