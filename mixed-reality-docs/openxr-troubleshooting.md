---
title: Risoluzione dei problemi di OpenXR
description: Risolvere i problemi delle applicazioni OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware, risoluzione dei problemi
ms.openlocfilehash: 269982596ed6162d9c2f1ec999a446bcecd6ba2a
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228006"
---
# <a name="openxr-troubleshooting"></a>Risoluzione dei problemi di OpenXR

Di seguito sono riportati alcuni suggerimenti per la risoluzione dei problemi durante lo sviluppo di un'app OpenXR con la realtà mista di Windows OpenXR Runtime.  Per eventuali altre domande sulla <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">specifica OpenXR 1,0</a>, visitare il <a href="https://community.khronos.org/c/openxr" target="_blank">Forum Khronos OpenXR</a> o il <a href="https://khr.io/slack" target="_blank">canale Slack #openxr</a>.

>[!NOTE]
>Si sono verificati problemi noti nel runtime corrente di Windows mixed OpenXR con app x86.  Al momento, è necessario compilare app desktop OpenXR per x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>App OpenXR che non avvia la realtà mista di Windows

Se l'app OpenXR non avvia la realtà mista di Windows quando viene eseguita, il runtime di OpenXR per la realtà mista di Windows non può essere impostato come runtime attivo.  Assicurarsi di seguire le istruzioni riportate sopra per iniziare a usare [OpenXR per le cuffie di realtà miste di Windows](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) in modo che il Runtime sia attivo.

È anche possibile eseguire la [realtà mista di Windows OpenXR strumenti di sviluppo](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) per ulteriori informazioni sulla risoluzione dei problemi in merito allo stato del runtime di OpenXR per la realtà mista di Windows nel sistema.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Il portale per la realtà mista non Mostra la voce di menu "Configura OpenXR"

Assicurarsi di eseguire almeno l'aggiornamento di Windows 10 ottobre 2018 (1809).  Se si usa una versione precedente di Windows 10, è possibile eseguire l'aggiornamento all'aggiornamento 2019 di maggio (1903) con [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10).

La voce di menu "Configura OpenXR" potrebbe non essere disponibile se si dispone di una versione precedente dell'app del portale per la realtà mista.  Verificare la presenza di un [aggiornamento dell'app portale per realtà mista](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) per assicurarsi di avere la versione più recente.

Si noti che la voce di menu "Configura OpenXR" non verrà visualizzata se il runtime OpenXR di Windows Mixed Reality è già installato e attivo.  È possibile installare la [realtà mista di Windows OpenXR strumenti di sviluppo](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) per determinare lo stato corrente del runtime di OpenXR nel sistema.