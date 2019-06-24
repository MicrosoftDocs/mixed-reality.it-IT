---
title: Modulo ASA Learning MR Azure spaziali ancoraggio su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326549"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Visualizzazione dei commenti di Azure ancoraggio spaziali

In questa lezione, scoprirai procedura fornire agli utenti con commenti e suggerimenti sull'individuazione di ancoraggio, eventi e lo stato quando si usa Azure spaziali ancoraggi.

Obiettivi:

* Informazioni su come configurare un pannello dell'interfaccia utente che visualizza informazioni importanti relative alla sessione corrente di ASA

* Comprendere ed esplorare gli elementi di feedback che il SDK ASA rende disponibile agli utenti

  

## <a name="instructions"></a>Istruzioni

### <a name="set-up-asa-feedback-ui-panel"></a>Configurare Panel dell'interfaccia utente di commenti e suggerimenti ASA

1. In questa lezione non si userà "SaveAnchorToDisk" e i pulsanti "ShareAnchor", quindi selezionare entrambi i pulsanti e deselezionare la casella di controllo nel Pannello di controllo (come illustrato di seguito) per nascondere questi pulsanti.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Successivamente, creare il pannello di istruzione. Iniziare con il pulsante destro facendo clic sul pulsante "instructions", passare il mouse su "oggetto 3D" e selezionare "textmeshpro-text".

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. Modificare la scala e il posizionamento del testo in modo che corrisponda con le istruzioni riportate nella scena. Inoltre, assicurarsi che l'allineamento per tutto il testo è centrato. Quindi eliminare il testo di esempio dall'editor di testo, come nell'immagine seguente.


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Modificare il nome dell'oggetto TextMeshPro in "FeedbackPanel."
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. Nel Pannello di progetto, selezionare "risorse" e fare clic destro, quindi selezionare "Visualizza Explorer".
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

A questo punto, fare clic su [qui](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) per scaricare i file necessari entro i prossimi passaggi successivi.

6. Quando si apre Esplora, selezionare la cartella assets, quindi la cartella "ASAmodulesAssets" e copiare lo script di feedback di ancoraggio e i file di script di ancoraggio modulo nella cartella. 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Nota: se viene visualizzato un messaggio popup che chiede se si desidera sovrascrivere il vecchio o mantenere il vecchio assicurarsi di selezionare sovrascrittura.

7. Tornare ora alla cartella Assets. Quindi, passare alla cartella "AzureSpatialAnchorsPlugin", quindi la cartella di esempi e infine la cartella degli script e copiare il wrapper di demo Anchor spaziali Azure nella cartella. 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Ora che i file vengono caricati, assicurarsi che il testo "feedbackpanel" sia selezionato, nella gerarchia di ASA_feedback e fare clic su "Aggiungi componente" e aggiungere lo script di ancoraggio commenti e suggerimenti per la ricerca e selezionarlo quando viene visualizzato. 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Trascinare l'oggetto testo "feedbackPanel" dalla gerarchia di ASA_Feedback lo slot vuoto sotto lo script come illustrato nell'immagine seguente. 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a>Lezione completata

In questa lezione è stato illustrato come creare un pannello dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di ancoraggio spaziale di Azure per fornire utente con il feedback in tempo reale.


