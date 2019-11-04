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
# <a name="managed-debugging-with-unity-il2cpp"></a>Debug gestito con Unity IL2CPP

Seguire questa procedura per aggiungere un debugger gestito alla build Unity IL2CPP UWP. Questa guida è stata sviluppata in origine per HoloLens e HoloLens 2.

1. È necessario trovarsi in una rete che supporta il [multicast](https://en.wikipedia.org/wiki/Multicast).
1. Verificare che **InternetClientServer** e **PrivateNetworkClientServer** siano archiviati in Unity con le funzionalità delle impostazioni di pubblicazione di UWP.

    ![Funzionalità delle impostazioni di pubblicazione UWP](images/il2cpp-debugging-capabilities.png)

1. Configurare le impostazioni di compilazione UWP per Unity:
    - Compilazione di sviluppo
    - Debug degli script
    - Attendi debugger gestito (facoltativo)

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

1. Compilazione in Unity.
1. Compilare e distribuire dalla soluzione Visual Studio al dispositivo. È necessario compilare con le configurazioni di **debug** o di **rilascio** . La configurazione **Master** Disabilita il profiler di Unity ed è in grado di impedire il debug ottimale. Facoltativamente, verificare la **connessione Internet (client & Server)** e le **Reti Private (client & Server)** nell'elenco delle funzionalità di Package. appxmanifest nella soluzione.
1. Avviare l'app nel dispositivo. Verificare che il dispositivo sia connesso alla stessa rete del computer.
1. Verificare che il dispositivo **non sia** connesso al PC tramite USB.
1. Passare alla soluzione Visual Studio creata quando si fa doppio clic su uno script in Unity, in cui è possibile visualizzare e modificare C# gli script.
1. Debug-> connessione del debugger Unity.

    ![Connetti debugger Unity](images/il2cpp-debugging-attach.png)

1. Selezionare il dispositivo nell'elenco e fare clic su "OK" per connettersi.

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)
