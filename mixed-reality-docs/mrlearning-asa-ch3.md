---
title: Esercitazioni sugli ancoraggi spaziali di Azure-3. Visualizzazione del feedback di ancoraggio spaziale di Azure
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438420"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Visualizzazione del feedback di ancoraggio spaziale di Azure

In questa lezione si apprenderà come fornire agli utenti feedback sull'individuazione di ancoraggio, sugli eventi e sullo stato quando si usano gli ancoraggi spaziali di Azure.

## <a name="objectives"></a>Obiettivi

* Informazioni su come configurare un pannello dell'interfaccia utente che visualizza informazioni importanti sulla sessione ASA corrente

* Comprendere ed esplorare gli elementi di feedback che l'SDK ASA rende disponibili agli utenti

## <a name="instructions"></a>Istruzioni

### <a name="set-up-asa-feedback-ui-panel"></a>Configurare il pannello dell'interfaccia utente del feedback ASA

1. In questa lezione non verranno usati i pulsanti "SaveAnchorToDisk" e "ShareAnchor", quindi selezionare entrambi i pulsanti e deselezionare la casella di controllo nel pannello Inspector (come illustrato di seguito) per nascondere questi pulsanti.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Creare il pannello di istruzioni. Per iniziare, fare clic con il pulsante destro del mouse sul pulsante "istruzioni", passare il puntatore su "oggetto 3D" e selezionare "textmeshpro-Text".

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. Modificare la scala e il posizionamento del testo, in modo che corrisponda alle istruzioni della scena. Assicurarsi inoltre che l'allineamento per tutto il testo sia centrato. Eliminare quindi il testo di esempio dall'editor di testo, come illustrato nell'immagine seguente.

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Modificare il nome dell'oggetto TextMeshPro in "FeedbackPanel".
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. Nel pannello progetto selezionare "asset" e fare clic con il pulsante destro del mouse, quindi selezionare "Mostra in Esplora".
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Fare clic [qui](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) per scaricare i file necessari nei passaggi successivi.

6. Dopo aver aperto Esplora risorse, selezionare la cartella assets, quindi la cartella "ASAmodulesAssets" e copiare lo script di ancoraggio feedback e i file script del modulo di ancoraggio nella cartella. 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Nota: se viene visualizzato un messaggio popup in cui viene chiesto se si desidera sovrascrivere il vecchio o conservare il vecchio, selezionare Sovrascrivi.

7. Tornare alla cartella assets. Passare quindi alla cartella "AzureSpatialAnchorsPlugin", seguita dalla cartella Examples e infine dalla cartella Scripts. Copiare quindi il wrapper demo di Azure Spatial Anchors in tale cartella. 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Ora che i file sono stati caricati, assicurarsi che sia selezionato il testo "feedbackpanel" nella gerarchia ASA_feedback, fare clic su "Aggiungi componente" e aggiungere lo script di ancoraggio feedback cercandolo e selezionando il testo quando viene visualizzato. 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Trascinare l'oggetto testo "feedbackPanel" dalla gerarchia ASA_Feedback nello slot vuoto sotto lo script, come illustrato nell'immagine seguente. 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>Lezione completata

In questa lezione è stato illustrato come creare un pannello dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di ancoraggio spaziale di Azure per fornire agli utenti il feedback in tempo reale.


