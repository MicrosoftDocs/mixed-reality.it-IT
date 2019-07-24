---
title: Lettore di comunicazione remota olografica
description: Il lettore di comunicazione remota olografico è un'app complementare che si connette a app e giochi per PC che supportano la comunicazione remota olografica. La comunicazione remota olografica trasmette contenuto olografico da un PC a Microsoft HoloLens in tempo reale, usando una connessione Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, comunicazione remota, comunicazione remota olografica
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813714"
---
# <a name="holographic-remoting-player"></a>Lettore di comunicazione remota olografica

Il lettore di comunicazione remota olografico è un'app complementare che si connette a app e giochi per PC che supportano la comunicazione remota olografica. La comunicazione remota olografica trasmette contenuto olografico da un PC a Microsoft HoloLens in tempo reale, usando una connessione Wi-Fi.

Il lettore di servizi remoti olografici può essere usato solo con le app PC progettate appositamente per supportare la comunicazione remota olografica.

Il lettore di comunicazione remota olografico è disponibile sia per HoloLens che per HoloLens 2.  Per supportare Remtoing olografici con HoloLens 2, è necessario aggiornare le app PC che supportano la comunicazione remota olografica con HoloLens.  Per domande sulle versioni supportate, contattare il provider di app.

## <a name="connecting-to-the-holographic-remoting-player"></a>Connessione al lettore di comunicazione remota olografica

Seguire le istruzioni dell'app per connettersi al lettore di comunicazione remota olografica. È necessario immettere l'indirizzo IP del dispositivo HoloLens, che è possibile visualizzare nella schermata principale del lettore remoto come segue:

![Lettore di comunicazione remota olografica](images/holographicremotingplayer.png)

Quando viene visualizzata la schermata principale, si saprà che non è presente un'app connessa.

Si noti che la connessione remota olografica **non**è crittografata. È consigliabile usare sempre la comunicazione remota olografica su una connessione Wi-Fi sicura attendibile.

## <a name="quality-and-performance"></a>Qualità e prestazioni

La qualità e le prestazioni dell'esperienza variano in base a tre fattori:
* **L'esperienza olografica che si sta eseguendo: le** app che eseguono il rendering di contenuto ad alta risoluzione o altamente dettagliato possono richiedere un PC più veloce o una connessione wireless più veloce.
* **Hardware del PC** : il PC deve essere in grado di eseguire e codificare l'esperienza olografica a 60 fotogrammi al secondo. Per una scheda grafica, è in genere consigliabile usare GeForce GTX 970 o AMD Radeon R9 290 o una soluzione migliore. Anche in questo caso, la tua esperienza specifica potrebbe richiedere una scheda di fascia superiore o inferiore.
* **Connessione Wi-Fi** : l'esperienza olografica viene trasmessa tramite Wi-Fi. Usa una rete veloce con congestione ridotta per massimizzare la qualità. L'uso di un PC connesso tramite un cavo Ethernet, anziché di un Wi-Fi, può migliorare anche la qualità.

## <a name="diagnostics"></a>Diagnostica

Per misurare la qualità della connessione, pronunciare **"Abilita diagnostica"** mentre è presente nella schermata principale del lettore di comunicazione remota olografica. Quando la diagnostica è abilitata, l'app visualizzerà:
* **Fps** : numero medio di frame di cui è stato eseguito il rendering il lettore remoto riceve e il rendering al secondo. La soluzione ideale è 60 FPS.
* **Latenza** : la quantità media di tempo necessaria per il passaggio di un frame dal PC alla HoloLens. Più basso è il migliore. Questo dipende in gran parte dalla rete Wi-Fi.

Nella schermata principale è possibile **disabilitare** la diagnostica per disattivare la diagnostica.

## <a name="pc-system-requirements"></a>Requisiti di sistema del PC
* Il PC **deve** eseguire l'aggiornamento dell'anniversario di Windows 10 o versione successiva.
* Si consiglia di usare una scheda grafica GeForce GTX 970 o AMD Radeon R9 290 o superiore.
* Si consiglia di connettere il PC alla rete tramite Ethernet per ridurre il numero di hop wireless.

## <a name="see-also"></a>Vedere anche
* [Condizioni di licenza software per Holographic Remoting](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Informativa sulla privacy Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
