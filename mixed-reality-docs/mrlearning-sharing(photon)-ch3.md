---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 44cc41b10ed79d3085ec601ec9cf21af47b0fea5
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523308"
---
# <a name="connecting-multiple-users"></a>Ci si connette più utenti

In questa lezione, è informazioni su come connettere più utenti come parte di una condividere esperienze in tempo reale. Al termine di questa lezione, sarà in grado di aprire l'applicazione in più dispositivi e vedere avatar, rappresentato da una sfera, le rappresentazioni di ogni persona che unisce in join. 

Obiettivi:

- Configurare il gioco di parole all'interno dell'applicazione
- Configurare i lettori
- Informazioni su come connettere più utenti un'esperienza condiviso

### <a name="instructions"></a>Istruzioni

1. Negli asset -> risorse -> cartella Prefabs nel Pannello di progetto selezionare e trascinare il prefab NetworkLobby in per la gerarchia come illustrato nell'immagine seguente.


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Quando si espande NetworkLobby, si noterà un oggetto figlio denominato NetworkRoom. Con NetworkRoom selezionate, passare al pannello di controllo e fare clic su Add Component. Cercare PhotonView e aggiungere il componente.

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Creare un nuovo oggetto gioco vuoto nella gerarchia. Fare clic con il pulsante destro nella gerarchia e seleziona vuoto dal menu di scelta rapida. Verificare che il posizionamento è impostato su x = 0, y = 0, z = 0 e assegnare il nome dell'oggetto, PhotonUser.

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Fare clic su Add Component e digitare generico sincronizzazione delta. Selezionare la classe generica sincronizzazione delta. Quando la classe viene visualizzata, fare clic sulla casella di controllo utente per accenderlo. 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Fare nuovamente clic su Add Component e digitare Photon View. Selezionare la classe di visualizzazione Photon che viene visualizzato nell'elenco a discesa.

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Fare clic sull'icona del File per la classe generica sincronizzazione delta. Trascinare e rilasciare il campo osservati i componenti della visualizzazione Photon. ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. Quindi, creiamo sfere per rappresentare ogni persona che unisce in join un'esperienza condivisa. L'oggetto PhotonUser appena creato e scrolldown a con il pulsante destro fare clic su "oggetto 3D e scegliere sfera. Questo verrà creato un oggetto gioco sfera come elemento figlio dell'oggetto PhotonUser.

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Ridimensionare la sfera down x = 0,06, y = 0,06, ad z = 0,06.

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Trascinare l'oggetto gioco PhotonUser nella cartella Prefabs nel Pannello di progetto e quindi eliminarlo dalla scena. A questo punto sono stati creati un prefab che può essere utilizzato quando durante la generazione o creare un'istanza nuova giocatori un'esperienza condiviso.

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Nota: assicurarsi che l'oggetto gioco ha copiato correttamente nella cartella Prefabs prima di eliminarlo dalla gerarchia.

10. Creare un nuovo oggetto nella gerarchia, seguendo le istruzioni nel passaggio 3 e denominarlo SharedPlayground. Quindi, fare clic su Add Component e cercare il gestore di rete generici e fare clic per aggiungere il componente di gestione di rete generici. Modificare la posizione dell'oggetto su x = 0, y = 0 e z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Lezione completata

Dopo che tutti i passaggi precedenti sono stati completati e il processo di compilazione è completo, fare clic sul pulsante play e connettersi i 2 HoloLens. Verrà visualizzata una sfera muove quando si sposta la testa. Questa informazione verrà visualizzata per tutti gli utenti che unisce in join di un progetto Unity.

[Lezione successiva: Sharing(photon) lezione 4](mrlearning-sharing(photon)-ch4.md)

