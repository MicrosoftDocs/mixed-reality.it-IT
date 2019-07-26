---
title: Modulo MR Learning sharing per HoloLens 2
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 53519d7bb2832fe8ce500f1ee146c91488b09366
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485665"
---
# <a name="3-connecting-multiple-users"></a>3. Connessione di più utenti

In questa lezione verrà illustrato come connettere più utenti nell'ambito di un'esperienza condivisa Live. Al termine di questa lezione sarà possibile aprire l'applicazione su più dispositivi e visualizzare avatar, rappresentati da una sfera, rappresentazioni di ogni persona che si unisce. 

Obiettivi

- Configurare il PUN all'interno dell'applicazione
- Configurare i giocatori
- Informazioni su come connettere più utenti in un'esperienza condivisa

## <a name="instructions"></a>Istruzioni

1. Nella cartella Asset-> Resources-> prefabbricates nel pannello del progetto, trascinare il prefabbricato NetworkLobby nella gerarchia, come illustrato nell'immagine seguente.

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Quando si espande NetworkLobby, viene visualizzato un oggetto figlio denominato NetworkRoom. Con NetworkRoom selezionato, passare al pannello Inspector e fare clic su Add Component. Cercare PhotonView e aggiungere il componente.

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Creare un nuovo oggetto gioco vuoto nella gerarchia. Fare clic con il pulsante destro del mouse nella gerarchia e scegliere vuota dal menu di scelta rapida. Verificare che il posizionamento sia impostato su x = 0, y = 0, z = 0 e assegnare un nome all'oggetto, PhotonUser.

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Fare clic su Add Component e digitare Generic NET Sync. Selezionare la classe di sincronizzazione NET generica. Quando viene visualizzata la classe, fare clic sulla casella di controllo utente per attivarla. 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Fare di nuovo clic su Add Component e digitare Photon View. Selezionare la classe di visualizzazione Photon visualizzata nell'elenco a discesa.

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Fare clic sull'icona file per la classe net Sync generica. Trascinarla e rilasciarla nel campo componenti osservati della visualizzazione Photon. 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. Si creeranno quindi le sfere per rappresentare ogni persona che partecipa a un'esperienza condivisa. Fare clic con il pulsante destro del mouse sull'oggetto PhotonUser appena creato e ScrollDown su "oggetto 3D e scegliere Sphere. Verrà creato un oggetto gioco Sphere come figlio dell'oggetto PhotonUser.

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Ridimensionare la sfera fino a x = 0,06, y = 0,06, ad z = 0,06.

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Trascinare l'oggetto PhotonUser Game nella cartella prefabbricates nel pannello Project, quindi eliminarlo dalla scena. A questo punto è stata creata una prefabbricata che può essere usata durante la generazione o la creazione di un'istanza di nuovi giocatori in un'esperienza condivisa.

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Nota: assicurarsi che l'oggetto Game sia stato copiato correttamente nella cartella prefabbricates prima di eliminarlo dalla gerarchia.

10. Creare un nuovo oggetto nella gerarchia seguendo le istruzioni riportate nel passaggio 3 e denominarlo SharedPlayground. Quindi, fare clic su Aggiungi componente e cercare gestore reti generico e fare clic su di esso per aggiungere il componente generico di gestione reti. Modificare la posizione dell'oggetto in x = 0, y = 0 e z = 0.

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Lezione completata

Una volta completati tutti i passaggi precedenti e il processo di compilazione è stato completato, premere il pulsante Play (Riproduci) e connettere HoloLens 2. Quando si sposta la testa, verrà visualizzata una sfera. Verrà visualizzato per tutti gli utenti che partecipano al progetto Unity.

[Lezione successiva: 4. Condivisione dei movimenti di oggetti con più utenti](mrlearning-sharing(photon)-ch4.md)

