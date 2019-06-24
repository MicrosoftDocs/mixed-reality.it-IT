---
title: MR Learning condivisione del modulo per HoloLens 2
description: Completare questo corso di informazioni su come implementare esperienze condivise con più utenti all'interno di un'applicazione 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327444"
---
# <a name="connecting-multiple-users"></a>**Ci si connette più utenti** 

In questa lezione si apprenderà come connettersi a più utenti come parte di una condividere esperienze in tempo reale. Al termine di questa lezione, sarà in grado di aprire l'applicazione in più dispositivi e visualizzare rappresentazioni "avatar" di ogni persona che unisce in join (avatar rappresentato da una sfera). 

Obiettivi:

- Configurare il gioco di parole all'interno dell'applicazione
- Configurare i lettori
- Informazioni su come connettere più utenti un'esperienza condiviso

### <a name="instructions"></a>Istruzioni

1. Negli asset > risorse > Prefabs cartella del pannello progetto, trascinamento e rilascio "NetworkLobby" prefab alla gerarchia, come illustrato nell'immagine seguente.


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Quando si espande il prefab "NetworkLobby", verrà visualizzato un oggetto figlio denominato "NetworkRoom." Con essa selezionate, passare al pannello di controllo e fare clic su "Aggiungi componente". Cercare "PhotonView" e aggiungere il componente.

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Creare un nuovo oggetto gioco vuoto nella gerarchia (fare clic con il pulsante destro nella gerarchia e selezionare "Vuoto" dal menu di scelta rapida). Verificare che il posizionamento è impostato su x = 0, y = 0, z = 0 e assegnare il nome dell'oggetto, "PhotonUser."

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Successivamente, si vuole creare sfere per rappresentare ogni persona che unisce in join un'esperienza condivisa. Fare clic con il pulsante destro l'oggetto "PhotonUser" appena creato, andare alla "oggetto 3D" e fare clic su "Sfera." Questo verrà creato un oggetto gioco sfera come elemento figlio dell'oggetto PhotonUser.

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. Ridimensionare la sfera down x = 0,06, y = 0,06, ad z = 0,06.

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. Trascinare l'oggetto gioco "PhotonUser" nella cartella "prefabs" nel Pannello di progetto. Quindi, eliminarlo dalla scena. A questo punto sono stati creati un prefab che verrà utilizzato quando durante la generazione o creare un'istanza nuova giocatori un'esperienza condiviso.

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Nota: assicurarsi che l'oggetto gioco ha copiato correttamente nella cartella "prefabs" prima di eliminarlo dalla gerarchia.

7. Creare un nuovo oggetto della gerarchia (con istruzioni simili a quello del passaggio 3) e denominarlo "SharedPlayground." Quindi, fare clic su "Add Component" e cercare "gestione di rete generica" e fare clic per aggiungere il componente di gestione di rete generico. Modificare la posizione dell'oggetto su x = 0, y = 0 e z = 0.

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Lezione completata

Dopo tutti i passaggi precedenti sono stati completati e il processo di compilazione è completo, quando si preme il pulsante di riproduzione e connette la 2 HoloLens, viene visualizzata una sfera muove quando si sposta la testa. Questa informazione verrà visualizzata per tutti gli utenti che unisce in join di un progetto Unity.

[Lezione successiva: Sharing(photon) lezione 4](mrlearning-sharing(photon)-ch4.md)

