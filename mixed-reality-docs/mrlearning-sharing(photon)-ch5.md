---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327190"
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

3. Proprio come alcune delle lezioni precedenti, importare un nuovo pacchetto personalizzato che è possibile ottenere [qui.](placeholderlink)

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. Una volta che viene importato, recuperare il punto di ancoraggio tabella appena aggiornata (dal pacchetto unity importato nel passaggio precedente) dalla cartella "prefabs" nel Pannello di progetto e rilasciarlo nell'oggetto padre "MixedRealityPlayspace."

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. Espandere l'oggetto padre "MixedRealityPlayspace", quindi l'oggetto "TableAnchor" e anche l'oggetto "pulsanti". 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. A questo punto della gerarchia, selezionare "ShareAzureAnchorButton" e spostare l'attenzione dell'utente al pannello di controllo. Scorrere verso il basso nel menu a discesa illustrato nell'immagine seguente e selezionare "AnchorModuleScript" e fare clic su "ShareAnchorNetework()."

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. Analogamente al passaggio 6, selezionare "GetAzureAnchorButton" e spostare l'attenzione dell'utente al pannello di controllo. Scorrere verso il basso nel menu a discesa illustrato nell'immagine seguente e selezionare "AnchorModuleScript" e fare clic su "GetSharedAnchorNetwork()." Quindi salvare.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Lezione completata

In questa lezione si è appreso come integrare potente nuovi spaziali Anchor Azure per allineare i dispositivi con risorse condivise in un'esperienza condiviso. In questa lezione si conclude anche il modulo di condivisione. Abbiamo appreso come configurare un nuovo account Photon, integrare Photon e il gioco di parole in una nuova applicazione di Unity, configurazione avatar e oggetti condivisi e infine allineamento più partecipanti tramite ASA. 

