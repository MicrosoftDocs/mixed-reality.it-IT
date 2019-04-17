---
title: Ottenere le App per HoloLens
description: Descrive installare le App per HoloLens, sia tramite il Microsoft Store e il caricamento laterale.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: sideload delle applicazioni, carico lato, trasferire localmente, store, uwp, app, installare
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597553"
---
# <a name="get-apps-for-hololens"></a>Ottenere le App per HoloLens

Come un dispositivo Windows 10, HoloLens supporta molte applicazioni UWP esistenti dall'archivio app, nonché nuove app sviluppata appositamente per HoloLens. Su questi elementi, si potrebbe anche voler [sviluppare](development-overview.md) e installare App personalizzate o quelli dei tuoi amici.

## <a name="installing-apps"></a>Installazione di App

Esistono tre modi per installare nuove app in di HoloLens. Il metodo principale sarà possibile installare le nuove applicazioni da Store di Windows. Tuttavia, è anche possibile installare applicazioni personalizzate tramite il portale di dispositivo o distribuirli da Visual Studio.

### <a name="from-the-microsoft-store"></a>Da di Microsoft Store
1. Eseguire un' [bloom](gestures.md#bloom) movimento per aprire il [dal Menu Start](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selezionare l'app Store e quindi toccare per inserire questo riquadro nel tuo mondo.
3. Quando si apre l'app Store, usare la barra di ricerca per cercare qualsiasi applicazione desiderata.
4. Selezionare **ottenere** oppure **installare** nella pagina dell'applicazione (un acquisto potrebbe essere necessario).

### <a name="installing-an-application-package-with-the-device-portal"></a>Installazione di un pacchetto di applicazione con il portale del dispositivo
1. Stabilire una connessione tra [dispositivo portale](using-the-windows-device-portal.md) alla destinazione HoloLens.
2. Passare il **app** pagina nel riquadro di spostamento a sinistra.
3. Sotto **pacchetto dell'App** individuare il file con estensione AppX associato all'applicazione.
  >[!IMPORTANT]
  >Assicurarsi di fare riferimento a tutti i file delle dipendenze e il certificato associati.

4. Fare clic su **Vai**.

![Installa modulo dell'app in Windows Device Portal in Microsoft HoloLens](images/deviceportal-appmanager.jpg)<br>
Utilizzo di Windows Device Portal per installare un'app in HoloLens

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Distribuzione da Microsoft Visual Studio 2015
1. Aprire la soluzione di Visual Studio della tua app (file con estensione sln).
2. Aprire il progetto **proprietà** .
3. Selezionare la configurazione di compilazione seguenti: Macchina master/x86/Remote.
4. Quando si seleziona computer remoto:
   * Assicurarsi che l'indirizzo punti all'indirizzo IP WiFi degli HoloLens.
   * Impostare l'autenticazione universale (protocollo non crittografato).
5. Compilare la soluzione.
6. Scegliere il **computer remoto** pulsante per distribuire l'app dal computer di sviluppo di HoloLens. Se si dispone già di una compilazione esistente nella finestra di HoloLens, selezionare Sì per reinstallare la versione più recente.<br>
  ![Distribuzione della macchina remota per le App per Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)<br>
7. L'applicazione venga installata ed auto avvio di HoloLens.
