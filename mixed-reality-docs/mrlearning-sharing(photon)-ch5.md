---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 941bdc64ed614d5ce71f58f05585d0dfc86c3bb7
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415932"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Gli ancoraggi spaziali Azure ed esperienze condivise

In questa lezione, si verrà descrive come integrare Azure spaziali Anchor (ASA) nella nostra esperienza condiviso. ASA consente a più dispositivi con risorse condivise per avere una conoscenza comune se si verifica nel proprio ambiente fisico per ancorare virtuale in modo che tutti i partecipanti di visualizzare gli oggetti nella stessa posizione fisica.

Prima di procedere con questa lezione, è necessario completare il modulo di apprendimento ASA, che si occuperà ASA nozioni di base, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali che sono necessari affinché possiamo integrare ASA nella nostra esperienza condiviso.

Obiettivi:

- Integrare un'esperienza condivisa per l'allineamento di più dispositivi ASA
- Scopri le nozioni di base del funzionamento nel contesto di un'esperienza condiviso locale ASA

### <a name="instructions"></a>Istruzioni

1. Salvare il progetto nella lezione precedente (CTRL + S) e denominarlo "HLSharedProjectMainPart5.unity" in modo che risulti più facile individuare quando è necessario anche in questo caso.

2. Selezionare il prefab TableAnchor sotto l'oggetto padre "MixedRealityPlayspace" ed eliminarla.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  Nella visualizzazione del progetto, passare a asset > risorse > Prefabs e trascinare il TableAnchor prefab sopra l'oggetto SharedPlayground per renderlo un elemento figlio.
4.  Espandere l'oggetto padre "MixedRealityPlayspace", quindi l'oggetto "TableAnchor" e anche l'oggetto "pulsanti". 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. A questo punto della gerarchia, selezionare "ShareAzureAnchorButton" e spostare l'attenzione dell'utente al pannello di controllo. Scorrere verso il basso nel menu a discesa illustrato nell'immagine seguente e selezionare "AnchorModuleScript" e fare clic su "ShareAnchorNetework()."

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Analogamente al passaggio 4, selezionare "GetAzureAnchorButton" e spostare l'attenzione dell'utente al pannello di controllo. Scorrere verso il basso nel menu a discesa illustrato nell'immagine seguente e selezionare "AnchorModuleScript" e fare clic su "GetSharedAnchorNetwork()." Quindi salvare.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Lezione completata

In questa lezione si è appreso come integrare potente nuovi spaziali Anchor Azure per allineare i dispositivi con risorse condivise in un'esperienza condiviso. In questa lezione si conclude anche il modulo di condivisione. Abbiamo appreso come configurare un nuovo account Photon, integrare Photon e il gioco di parole in una nuova applicazione di Unity, configurazione avatar e oggetti condivisi e infine allineamento più partecipanti tramite ASA. 

