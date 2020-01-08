---
title: Debug gestito con Unity IL2CPP
description: Questo articolo illustra come eseguire un debugger gestito nel progetto Unity IL2CPP UWP.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, debug, il2cpp
ms.openlocfilehash: 970d3000df995e7c6e331a41d10e25dc5aa370a8
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502662"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Debug gestito con Unity IL2CPP

Seguire questa procedura per aggiungere un debugger gestito alla build Unity IL2CPP UWP. Questa guida è stata sviluppata in origine per HoloLens e HoloLens 2.

1. È necessario trovarsi in una rete che supporta il [multicast](https://en.wikipedia.org/wiki/Multicast).
1. Verificare che **InternetClientServer** e **PrivateNetworkClientServer** siano archiviati in Unity con le funzionalità delle impostazioni di pubblicazione di UWP.

    ![Funzionalità delle impostazioni di pubblicazione UWP](images/il2cpp-debugging-capabilities.png)

1. Configurare le impostazioni di compilazione UWP per Unity:
    - Development Build
    - Debug degli script
    - Attendi debugger gestito (facoltativo)

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

1. Compilazione in Unity.
1. Compilare e distribuire dalla soluzione Visual Studio al dispositivo. È necessario compilare con le configurazioni di **debug** o di **rilascio** . La configurazione **Master** Disabilita il profiler di Unity ed è in grado di impedire il debug ottimale. Facoltativamente, verificare la **connessione Internet (client & Server)** e le **Reti Private (client & Server)** nell'elenco delle funzionalità di Package. appxmanifest nella soluzione.
1. Avviare l'app nel dispositivo. Verificare che il dispositivo sia connesso alla stessa rete del computer.
1. Verificare che il dispositivo **non sia** connesso al PC tramite USB.
1. Passare alla soluzione Visual Studio creata quando si fa doppio clic su uno script in Unity, in cui è possibile visualizzare e modificare gli C# script.
1. Debug-> connessione del debugger Unity.

    ![Collega debugger Unity](images/il2cpp-debugging-attach.png)

1. Selezionare il dispositivo nell'elenco e fare clic su "OK" per connettersi.

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)
