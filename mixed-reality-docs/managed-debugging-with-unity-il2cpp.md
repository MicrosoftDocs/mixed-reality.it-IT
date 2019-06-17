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
# <a name="managed-debugging-with-unity-il2cpp"></a>Il debug con Unity IL2CPP gestito

Seguire questi passaggi per collegare un debugger gestito per la compilazione di Unity IL2CPP UWP. Questa guida è stato originariamente sviluppata per HoloLens e HoloLens 2.

1. Assicurarsi che **InternetClientServer** e **PrivateNetworkClientServer** vengono controllate in Unity con le funzionalità di impostazioni di pubblicazione di piattaforma UWP.

    ![Piattaforma UWP funzionalità impostazioni di pubblicazione](images/il2cpp-debugging-capabilities.png)

1. Configurare le impostazioni di compilazione UWP Unity:
    - Build di sviluppo
    - Debug degli script
    - Attendere che il Debugger gestito (facoltativo)

    ![Impostazioni di compilazione UWP](images/il2cpp-debugging-build.png)

1. Compilare in Unity.
1. Compilare e distribuire dalla soluzione di Visual Studio al dispositivo. È necessario compilare con la **Debug** oppure **versione** configurazioni. Il **Master** configurazione consente di disattivare il profiler di Unity e può impedire il debug ottimale. Facoltativamente, verificare **Internet (Client e Server)** e **reti Private (Client e Server)** nell'elenco di funzionalità nel package. appxmanifest nella soluzione.
1. Avviare l'app nel dispositivo. Assicurarsi che il dispositivo è connesso alla stessa rete dei PC.
1. Assicurarsi che il dispositivo **non è** connesso al PC tramite USB.
1. Passare alla soluzione di Visual Studio che viene creata quando si fa doppio clic uno script di Unity, in cui è possibile visualizzare e modificare il C# script.
1. Debug -> Collega Debugger Unity.

    ![Collega Debugger Unity](images/il2cpp-debugging-attach.png)

1. Selezionare il dispositivo nell'elenco e fare clic su "OK" per collegare.

    ![Elenco dei dispositivi](images/il2cpp-debugging-machines.png)
