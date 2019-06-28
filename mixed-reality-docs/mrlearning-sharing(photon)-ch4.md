---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416012"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>La sincronizzazione gli spostamenti degli oggetti condivisi

In questa lezione si apprenderà come condividere gli spostamenti degli oggetti in modo che tutti i partecipanti di una sessione condivisa è possono collaborare insieme e visualizzare le interazioni degli altri. Questa lezione si basa l'utilità di avvio lunare che è stato compilato come parte del [esercitazioni di modulo Base](mrlearning-base.md).

Obiettivi:

- Portare nell'utilità di avvio lunare come il modello 3D da condividere
- Configurare il progetto per condividere i movimenti del modello 3D.
- Informazioni su come compilare un'applicazione di collaborazione multiutente base

### <a name="instructions"></a>Istruzioni

1. Salvare la scena nella lezione precedente (CTRL + S). È possibile denominarlo "HLSharedProjectMainPart4.unity" in modo che risulti più facile individuare quando è necessario.

2. Nella finestra del progetto, negli asset > cartella degli script, fare doppio clic sul GenericNetSync per aprirlo in Visual Studio o che mai code editor in uso.  ![](images/module3chapter4updatestep2.png)

3. Nelle righe 34 e 38, rimuovere il "/ /" per attivare il codice per la tabella che verrà usato in questa lezione.  Quindi salvare il file. ![](images/module3chapter4updatestep3.png)

4. Nella finestra del progetto, fare doppio clic sul file PhotonRoom.cs negli asset > cartella Scripts per aprirla nuovamente in Visual Studio. ![](images/module3chapter4updatestep4.png)

5. Proprio come nel passaggio 3 è necessario rimuovere il "/ /" per attivare il codice alla righe 26, 25 e 106.![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. Nella visualizzazione gerarchia, selezionare l'oggetto NetworkRoom.![](images/module3chapter4updatestep6.png)

7. Nella visualizzazione del progetto, passare a asset > risorse > Prefabs. In primo luogo, trascinare e rilasciare il prefab tabella allo slot di "Tableprefab" nella classe PhotonRoom. Trascinare quindi il prefab LunarModule allo slot di "Modulo Prefab" nella classe PhotonRoom. ![](images/module3chapter4updatestep7.png)

   Nota: Se si fa clic su uno degli oggetti prefab e versione, il controllo passerà a quell'oggetto. Fare clic su, trascinare e rilasciare ogni oggetto al relativo slot appropriato.



8. A questo punto, fare clic sulla freccia a sinistra di "MixedRealityPlayspace" e spostare l'oggetto gioco figlio, "MainCamera" verso il basso nel prefab "SharedPlayground". Eliminare quindi il prefab "MixedRealityPlayspace" (per eliminare, selezionare il prefab e toccare "Elimina" sulla tastiera).

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

Nota:  Assicurarsi che sia il Main Camera SharedPlayground significativi vengono impostati su 0, 0,0.

9. Creare un nuovo oggetto gioco impostata come un oggetto figlio all'oggetto padre "SharedPlayground" (per creare un nuovo oggetto, fare clic con il pulsante destro sull'oggetto padre e selezionare "Crea vuoto"). 

10. Con il nuovo oggetto selezionato nella gerarchia, è possibile modificare il nome dell'oggetto in "TableAnchor" nel Pannello di controllo. Inoltre, fare clic su "Aggiungi componente" e cercare il componente "TableAnchor". Selezionarlo e aggiungerlo all'oggetto. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Nota: impostare il posizionamento su x = 1, y =-0,55 e z = 2. Inoltre, impostare la rotazione di y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. Nel Pannello di progetto, nella cartella "prefabs", trascinare ora il prefab "table" nell'oggetto figlio "TableAnchor" appena creato.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. Infine, nell'oggetto "DebugWindow", modificare la larghezza a 80 e l'altezza su 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Lezione completata

Al termine, tutti gli utenti che eseguono join di un progetto Unity possono spostarsi l'utilità di avvio lunare. Tutti gli spostamenti siano sincronizzati affinché ogni utente può visualizzare le interazioni degli altri. Questi concetti può essere utilizzato come i blocchi predefiniti fondamentali per le esperienze complete collaborazione condiviso. 

Anche se tutti gli utenti connessi come parte di un'esperienza condivisa e vede i movimenti relativi degli oggetti, l'applicazione non riesce ancora a allineare accuratamente gli avatar e gli oggetti in modo che gli utenti locali vedono tra loro e gli oggetti nella stessa posizione all'interno di fisico World. Per ancorare un esperienze condivise locale, tutti i dispositivi richiede una conoscenza comune dell'ambiente fisico. In questo modulo a tale scopo mediante [Anchor spaziali Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), che verrà implementato nella lezione successiva.

Prima di procedere alla lezione successiva, è necessario completare il modulo di apprendimento ASA, che si occuperà nozioni di base ASA, account di Azure e la creazione di risorse e altri blocchi di edifici fondamentali necessarie prima che è possibile integrare questa funzionalità nella nostra esperienza condiviso.

[Lezione successiva: Sharing(photon) lezione 5](mrlearning-sharing(photon)-ch5.md)

