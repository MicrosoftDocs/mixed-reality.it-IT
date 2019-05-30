---
title: .NET Remoting holographic Player
description: Il lettore di .NET Remoting Holographic è un'app complementare che si connette a PC App e giochi che supportano la comunicazione remota Holographic. .NET Remoting holographic streaming holographic contenuto da un PC per i Microsoft HoloLens in tempo reale, usando una connessione Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, servizi remoti .NET Remoting Holographic
ms.openlocfilehash: 24213444686dd2e5dbda4016dd551a8ead8f305a
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270308"
---
# <a name="holographic-remoting-player"></a>.NET Remoting holographic Player

Il lettore di .NET Remoting Holographic è un'app complementare che si connette a PC App e giochi che supportano la comunicazione remota Holographic. .NET Remoting holographic streaming holographic contenuto da un PC per i Microsoft HoloLens in tempo reale, usando una connessione Wi-Fi.

Il giocatore remoto Holographic utilizzabile solo con le app a PC che sono progettate specificamente per supportare la comunicazione remota Holographic.

Il lettore di .NET Remoting Holographic è disponibile per HoloLens e HoloLens 2.  Le app PC supportati .NET Remoting Holographic con HoloLens devono essere aggiornate per supportare Holographic Remtoing con 2 HoloLens.  Se si hanno domande sulle versioni supportate, contattare il provider di app.

## <a name="connecting-to-the-holographic-remoting-player"></a>La connessione al lettore Holographic .NET Remoting

Seguire le istruzioni dell'app per la connessione al lettore di .NET Remoting Holographic. È necessario immettere l'indirizzo IP del dispositivo HoloLens, che è possibile visualizzare nella schermata principale del giocatore remoto come indicato di seguito:

![.NET Remoting holographic Player](images/holographicremotingplayer.png)

Ogni volta che viene visualizzata la schermata principale, si saprà che non è un'app connessa.

Si noti che la connessione di .NET remoting holographic **non crittografato**. È necessario utilizzare sempre Holographic servizi remoti tramite una connessione Wi-Fi sicura attendibili.

## <a name="quality-and-performance"></a>Qualità e prestazioni

Qualità e prestazioni della tua esperienza possono variare in base tre fattori:
* **Esperienza olografica stai lavorando** -App che eseguono il rendering di contenuto ad alta risoluzione o estremamente dettagliata può essere necessario un computer più veloce o più veloce connessione wireless.
* **Hardware del PC** -il PC deve essere in grado di eseguire e codificare l'esperienza olografica a 60 fotogrammi al secondo. Per una scheda grafica, è consigliabile in genere un GeForce GTX 970 o AMD Radeon R9 290 o migliore. Anche in questo caso, l'esperienza di particolare può richiedere una carta di fascia bassa o versione successiva.
* **La connessione Wi-Fi** -l'esperienza olografica viene trasmesso tramite Wi-Fi. Usare una rete veloce di congestione bassa per ottimizzare la qualità. Usa un PC che è connesso tramite un cavo Ethernet, anziché Wi-Fi, può anche migliorare la qualità.

## <a name="diagnostics"></a>Diagnostica

Per misurare la qualità della connessione, ad esempio **"abilitare la diagnostica"** mentre nella schermata principale del lettore Remoting Holographic. Quando è abilitata la diagnostica, l'app verrà illustrato:
* **FPS** : il numero medio di fotogrammi sottoposti a rendering il giocatore di .NET remoting è la ricezione e il rendering al secondo. La soluzione ideale è 60 FPS.
* **Latenza** -la quantità media di tempo necessario per un frame passare da PC a di HoloLens. Minore è la migliore. Ciò dipende in gran parte della rete Wi-Fi.

Quando è attiva la schermata principale, è possibile dire **"disabilitare la diagnostica"** per disattivare la diagnostica.

## <a name="pc-system-requirements"></a>Requisiti di sistema:
* I PC **necessario** eseguire l'aggiornamento dell'anniversario di Windows 10 o versione successiva.
* È consigliabile un GeForce GTX 970 o AMD Radeon R9 290 o una scheda grafica migliorata.
* È consigliabile che Connetti il tuo PC alla rete tramite ethernet per ridurre il numero di hop Wireless.

## <a name="see-also"></a>Vedere anche
* [Condizioni di licenza software per Holographic Remoting](microsoft-holographic-remoting-software-license-terms.md)
* [Informativa sulla Privacy di Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
