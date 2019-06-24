---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326621"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>La sincronizzazione gli spostamenti degli oggetti condivisi

In questa lezione si apprenderà come condividere gli spostamenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa è possono collaborare insieme e visualizzare le interazioni degli altri. Questa lezione si basa l'utilità di avvio lunare che è stato compilato come parte del [esercitazioni di modulo Base](mrlearning-base.md).

Obiettivi:

- Importare l'utilità di avvio lunare completata come il modello 3D da condividere
- Configurare il progetto per condividere i movimenti del modello 3D.
- Informazioni su come compilare un'applicazione di collaborazione multiutente base

### <a name="instructions"></a>Istruzioni

1. Salvare la scena nella lezione precedente (CTRL + S). È possibile denominarlo "HLSharedProjectMainPart4.unity" in modo che risulti più facile individuare quando è necessario.

2. Eliminare l'oggetto "NetworkLobby" (selezionandolo e premendo CANC). Inoltre, passare alla cartella "prefabs" creato nella lezione 2 ed eliminare il prefab "NetworkLobby" anche dal.

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. Importare un nuovo pacchetto personalizzato (ad esempio, passaggio 2 nella lezione 2) e importare il [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) e il [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. A questo punto, nella cartella "prefabs", trascinare il prefab "NetworkLobby" nuovo nella gerarchia. 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> Nota: i due pacchetti sono stati importati nei passaggi precedenti aggiornati il prefab "NetworkLobby". Evita di molta digitazione.

5. A questo punto, fare clic sulla freccia a sinistra di "MixedRealityPlayspace" e spostare l'oggetto gioco figlio, "MainCamera" verso il basso nel prefab "SharedPlayground". Eliminare quindi il prefab "MixedRealityPlayspace" (per eliminare, selezionare il prefab e toccare "Elimina" sulla tastiera).

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. Creare un nuovo oggetto gioco impostata come un oggetto figlio all'oggetto padre "SharedPlayground" (per creare un nuovo oggetto, fare clic con il pulsante destro sull'oggetto padre e selezionare "Crea vuoto").
7. Con il nuovo oggetto selezionato nella gerarchia, è possibile modificare il nome dell'oggetto in "TableAnchor" nel Pannello di controllo. Inoltre, fare clic su "Aggiungi componente" e cercare il componente "TableAnchor". Selezionarlo e aggiungerlo all'oggetto.

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Nota: impostare il posizionamento su x = 1, y =-0,55 e z = 2. Inoltre, impostare la rotazione di y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. Nel Pannello di progetto, nella cartella "prefabs", trascinare ora il prefab "table" nell'oggetto figlio "TableAnchor" appena creato.

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. Selezionare "NetworkRoom", un oggetto figlio sotto "NetworkLobby" nella gerarchia e fare clic su "Aggiungi componente" nel Pannello di controllo e cercare "PhotonView" e aggiungere lo script per il "*NetworkRoom*" oggetti.

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. Infine, nell'oggetto "DebugWindow", modificare la larghezza a 80 e l'altezza su 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Lezione completata

Al termine, tutti gli utenti che eseguono join di un progetto Unity possono spostarsi l'utilità di avvio lunare. Tutti gli spostamenti siano sincronizzati affinché ogni utente può visualizzare le interazioni degli altri. Questi concetti può essere utilizzato come i blocchi predefiniti fondamentali per le esperienze complete collaborazione condiviso. 

Anche se tutti gli utenti connessi come parte di un'esperienza condivisa e vede i movimenti relativi degli oggetti, l'applicazione non riesce ancora a allineare accuratamente gli avatar e gli oggetti in modo che gli utenti locali vedono tra loro e gli oggetti nella stessa posizione all'interno di fisico World. Per ancorare un esperienze condivise locale, tutti i dispositivi richiede una conoscenza comune dell'ambiente fisico. In questo modulo a tale scopo mediante [Anchor spaziali Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), che verrà implementato nella lezione successiva.

Prima di procedere alla lezione successiva, è necessario completare il modulo di apprendimento ASA, che si occuperà nozioni di base ASA, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali necessarie prima che è possibile integrare questa funzionalità nella nostra esperienza condiviso.

[Lezione successiva: Sharing(photon) lezione 5](mrlearning-sharing(photon)-ch5.md)

