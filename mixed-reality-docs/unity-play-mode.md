---
title: Modalità di gioco Unity
description: Usa la modalità Play nell'editor di Unity per visualizzare in anteprima le modifiche in un dispositivo senza distribuirvi un'app.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, .NET remoting, holographic .NET remoting, Windows Media player holographic .NET remoting
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597823"
---
# <a name="unity-play-mode"></a>Modalità di gioco Unity

Un modo rapido per lavorare al progetto di Unity è in modalità "riprodurre". Esegue l'app in locale nell'editor di Unity nel PC. Unity Usa Holographic .NET Remoting per fornire un modo rapido per visualizzare in anteprima il contenuto in un dispositivo HoloLens reale.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modalità di gioco Unity con .NET Remoting Holographic

Con .NET Remoting Holographic, si può provare l'app in HoloLens, mentre è in esecuzione nell'editor di Unity nel PC. Sguardo, gesti, vocale e mapping spaziale di input viene inviato da di HoloLens al computer. Fotogrammi sottoposti a rendering vengono quindi inviati nuovamente di HoloLens. Questo è un ottimo modo per rapidamente il debug dell'app senza compilazione e distribuzione di un progetto completo.
1. Nella finestra di HoloLens, andare al **Microsoft Store** e installare il **[Holographic Player .NET Remoting](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.
2. Nel HoloLens, avviare il **Holographic Remoting Player** app.
3. In Unity, passare al **finestra** dal menu **emulazione Holographic**.
4. Impostare **modalità di emulazione** al **remoto al dispositivo**.
5. Per la **computer remoto**, immettere l'indirizzo IP di HoloLens.
6. Fare clic su **Connetti**. Si noterà **lo stato della connessione** passare alla **connesso** e visualizzare la schermata, passare vuota nella finestra di HoloLens.
7. Fare clic sui **riprodurre** pulsante per avviare la modalità di riproduzione e l'esperienza dell'app in di HoloLens.

.NET Remoting holographic richiede una connessione veloce di PC e Wi-Fi. Visualizzare [Player Remoting Holographic](holographic-remoting-player.md) per i dettagli completi.

Per ottenere risultati ottimali, verificare che l'app imposta correttamente i [concentrarsi punto](focus-point-in-unity.md). In questo modo Holographic .NET Remoting per adattarsi meglio scena alla latenza della connessione wireless.

## <a name="see-also"></a>Vedere anche
* [.NET Remoting holographic Player](holographic-remoting-player.md)
