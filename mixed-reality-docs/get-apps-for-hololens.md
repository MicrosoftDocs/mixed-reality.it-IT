---
title: Ottenere le app per HoloLens
description: Descrive l'installazione di app per HoloLens, sia tramite il Microsoft Store che il caricamento laterale.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: sideload, carico laterale, caricamento laterale, archivio, UWP, app, installazione
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522554"
---
# <a name="get-apps-for-hololens"></a>Ottenere le app per HoloLens

Come dispositivo Windows 10, HoloLens supporta molte applicazioni UWP esistenti dall'App Store, oltre a nuove app compilate in modo specifico per HoloLens. Oltre a questi elementi, è anche possibile [sviluppare](development-overview.md) e installare le proprie app o gli amici.

## <a name="installing-apps"></a>Installazione di app

Sono disponibili tre modi per installare le nuove app in HoloLens. Il metodo principale consisterà nell'installare nuove applicazioni da Windows Store. Tuttavia, è anche possibile installare applicazioni personalizzate usando il portale del dispositivo o distribuendo tali applicazioni da Visual Studio.

### <a name="from-the-microsoft-store"></a>Dal Microsoft Store
1. Eseguire un movimento [Bloom](gestures.md#bloom) per aprire il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selezionare l'App Store e quindi toccare per inserire il riquadro nel mondo.
3. Quando si apre l'App Store, usare la barra di ricerca per cercare le applicazioni desiderate.
4. Selezionare **Get** o **Install** nella pagina dell'applicazione (potrebbe essere necessario un acquisto).

### <a name="installing-an-application-package-with-the-device-portal"></a>Installazione di un pacchetto dell'applicazione con il portale del dispositivo
1. Stabilire una connessione dal [portale del dispositivo](using-the-windows-device-portal.md) al HoloLens di destinazione.
2. Passare alla pagina **app** nel percorso di spostamento a sinistra.
3. In **pacchetto app** selezionare il file con estensione appx associato all'applicazione.
  >[!IMPORTANT]
  >Assicurarsi di fare riferimento ai file di dipendenza e di certificato associati.

4. Fare clic su **Vai**.

![Installare il modulo dell'app nel portale per dispositivi Windows in Microsoft HoloLens](images/deviceportal-appmanager.jpg)<br>
Uso del portale per dispositivi Windows per installare un'app in HoloLens

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Distribuzione da Microsoft Visual Studio 2015
1. Aprire la soluzione Visual Studio dell'app (file con estensione sln).
2. Aprire le **Proprietà** del progetto.
3. Selezionare la configurazione di compilazione seguente: Master/x86/computer remoto.
4. Quando si seleziona computer remoto:
   * Assicurarsi che l'indirizzo punti all'indirizzo IP Wi-Fi HoloLens '.
   * Impostare l'autenticazione su universale (protocollo non crittografato).
5. Compilare la soluzione.
6. Fare clic sul pulsante **computer remoto** per distribuire l'app dal computer di sviluppo a HoloLens. Se si dispone già di una compilazione esistente nel HoloLens, selezionare Sì per reinstallare la versione più recente.<br>
  ![Distribuzione del computer remoto per le app in Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)<br>
7. L'applicazione viene installata e avviata automaticamente nella HoloLens.
