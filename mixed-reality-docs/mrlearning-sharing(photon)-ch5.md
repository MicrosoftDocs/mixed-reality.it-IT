---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465206"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Gli ancoraggi spaziali Azure ed esperienze condivise

In questa lezione si descrive come integrare Azure spaziali Anchor (ASA) nella nostra esperienza condiviso. ASA consente a più dispositivi con risorse condivise avere un riferimento comune se l'ambiente fisico a esperienze virtuale ancoraggio tale che tutti i partecipanti di visualizzare gli oggetti nella stessa posizione fisica.

Prima di procedere con questa lezione, è necessario completare il modulo di apprendimento ASA, che si occuperà ASA nozioni di base, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali che sono necessari affinché possiamo integrare ASA nella nostra esperienza condiviso.

Obiettivi:

- Integrare un'esperienza condivisa per l'allineamento di più dispositivi ASA
- Scopri le nozioni di base del funzionamento nel contesto di un'esperienza condiviso locale ASA

### <a name="instructions"></a>Istruzioni

1. Salvare il progetto nella lezione precedente (CTRL + S) e denominarlo "HLSharedProjectMainPart5.unity" in modo che risulti più facile individuare quando è necessario anche in questo caso.

2. Selezionare il prefab TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminarla.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  Nella visualizzazione del progetto, selezionare gli asset -> risorse -> Prefabs e trascinare il prefab TableAnchor sopra l'oggetto SharedPlayground per renderlo un elemento figlio.
4.  Espandere l'oggetto padre MixedRealityPlayspace, TableAnchor e anche l'oggetto di pulsanti. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. A questo punto della gerarchia, selezionare ShareAzureAnchorButton e spostare l'attenzione dell'utente al pannello di Inaspector. Scorrere verso il basso il menu di riepilogo a discesa mostrato nell'immagine seguente, AnchorModuleScript e selezionare ShareAnchorNetework().

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Selezionare GetAzureAnchorButton (vedere Passaggio 4), e spostare l'attenzione dell'utente al pannello di controllo. Scorrere verso il basso il menu di riepilogo a discesa mostrato nell'immagine seguente e selezionare AnchorModuleScript e fare clic su GetSharedAnchorNetwork() e salvare.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Lezione completata

In questa lezione si è appreso come integrare potente nuovi spaziali Anchor Azure per allineare i dispositivi con risorse condivise in un'esperienza condiviso. In questa lezione si conclude anche il modulo di condivisione. Abbiamo appreso come configurare un nuovo account Photon, integrare Photon e il gioco di parole in una nuova applicazione di Unity, configurazione avatar e oggetti condivisi e infine allineamento più partecipanti tramite ASA. 

