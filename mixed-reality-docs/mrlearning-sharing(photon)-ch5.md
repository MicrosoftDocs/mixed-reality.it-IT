---
title: Esercitazioni sulle funzionalità multiutente-5. Integrazione di ancoraggi spaziali di Azure in un'esperienza condivisa
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553809"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. integrazione di ancoraggi spaziali di Azure in un'esperienza condivisa

In questa lezione si apprenderà come integrare Azure Spatial Anchors (ASA) nell'esperienza condivisa. ASA consente a più dispositivi con percorso condiviso di avere un riferimento comune se l'ambiente fisico prevede l'ancoraggio di esperienze virtuali in modo che tutti i partecipanti vedano gli oggetti nella stessa posizione fisica.

## <a name="objectives"></a>Obiettivi

* Integrare ASA in un'esperienza condivisa per l'allineamento di più dispositivi.
* Informazioni sulle nozioni di base sul funzionamento di ASA nel contesto di un'esperienza condivisa locale.

## <a name="instructions"></a>Istruzioni

1. Selezionare la prefabbricazione TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminarla.

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. Nella visualizzazione del progetto passare a assets-> Resources-> prefabbricates e trascinare il prefabbricato TableAnchor sull'oggetto SharedPlayground per impostarlo come figlio.

3. Espandere l'oggetto padre MixedRealityPlayspace, l'oggetto TableAnchor ed espandere anche l'oggetto Buttons.

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. A questo punto, nella gerarchia selezionare ShareAzureAnchorButton e spostare l'attenzione sul pannello Inspector. Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente, selezionare AnchorModuleScript e fare clic su ShareAnchorNetwork ().

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Selezionare GetAzureAnchorButton (vedere il passaggio 4) e riportare l'attenzione al pannello Inspector. Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente, selezionare AnchorModuleScript, fare clic su GetSharedAnchorNetwork () e quindi su Save (Salva).

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Ripetere il passaggio 4 per collegare la funzione StartAzureSession () a StartAzureSessionButton.

7. Ripetere il passaggio 4 per collegare la funzione CreateAzureAnchor () a CreateAzureAnchorButton e verificare che l'oggetto TableAnchor sia assegnato al campo ' oggetto gioco ' del parametro della funzione.

8. Seguire le istruzioni per la [connessione della scena alle risorse di Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) per aggiungere le credenziali del servizio ancoraggi spaziali di Azure.

9. Per testare il modulo di condivisione, fare clic sul pulsante "Avvia sessione di Azure ASA" che avvierà la sessione di ancoraggi spaziali di Azure e quindi creare l'ancoraggio di Azure facendo clic sul pulsante "Crea ancoraggio Azure". Attendere che l'ancoraggio di Azure venga creato. Dopo aver creato l'ancoraggio di Azure, fare clic sul pulsante "Condividi Azure Anchor" per condividere l'ancoraggio Azure creato dal HoloLens.

10. Per ricevere l'ancoraggio Azure condiviso in un altro HoloLens, fare clic su "Avvia sessione di Azure ASA" per avviare e ottenere la sessione ASA corrente

11. Fare clic sul pulsante "Get Azure Anchor" per ottenere l'ancoraggio Azure condiviso dall'altro HoloLens.

## <a name="congratulations"></a>Complimenti

In questa lezione si è appreso come integrare i nuovi ancoraggi spaziali avanzati di Azure per allineare i dispositivi con percorso condiviso in un'esperienza condivisa. Si conclude anche il modulo sharing. Si è appreso come configurare un nuovo account Photon, integrare Photon e PUN in una nuova applicazione Unity, configurare avatar e oggetti condivisi e infine allineare più partecipanti usando ASA.
