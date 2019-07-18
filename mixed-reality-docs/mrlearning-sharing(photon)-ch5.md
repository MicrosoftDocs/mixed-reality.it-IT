---
title: Modulo MR Learning sharing per HoloLens 2
description: Completare questo corso per apprendere come implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293630"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Ancoraggi spaziali e esperienze condivise di Azure

In questa lezione viene illustrato come integrare Azure Spatial Anchors (ASA) nell'esperienza condivisa. ASA consente a più dispositivi con percorso condiviso di avere un riferimento comune se l'ambiente fisico prevede l'ancoraggio di esperienze virtuali in modo che tutti i partecipanti vedano gli oggetti nella stessa posizione fisica.

Prima di procedere con questa lezione, è necessario completare il modulo ASA Learning, che riguarderà le nozioni di base di ASA, la creazione di account e risorse di Azure e altri blocchi di edifici fondamentali necessari prima di poter integrare ASA nell'esperienza condivisa.

Obiettivi

- Integrare ASA in un'esperienza condivisa per l'allineamento di più dispositivi.
- Informazioni sulle nozioni di base sul funzionamento di ASA nel contesto di un'esperienza condivisa locale.

### <a name="instructions"></a>Istruzioni

1. Salvare il progetto dalla lezione precedente (CTRL + S) e denominarlo "HLSharedProjectMainPart5. Unity" in modo che sia più facile da trovare quando è necessario.

2. Selezionare la prefabbricazione TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminarla.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  Nella visualizzazione del progetto passare a assets-> Resources-> prefabbricates e trascinare il prefabbricato TableAnchor sull'oggetto SharedPlayground per impostarlo come figlio.
4.  Espandere l'oggetto padre MixedRealityPlayspace, l'oggetto TableAnchor ed espandere anche l'oggetto Buttons. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. A questo punto, nella gerarchia selezionare ShareAzureAnchorButton e spostare l'attenzione sul pannello inaspectr. Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente e selezionare AnchorModuleScript e fare clic su ShareAnchorNetework ().

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Selezionare GetAzureAnchorButton (vedere il passaggio 4) e riportare l'attenzione al pannello Inspector. Scorrere verso il basso fino al menu a discesa visualizzato nell'immagine seguente e selezionare AnchorModuleScript, quindi fare clic su GetSharedAnchorNetwork () e quindi su Salva.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Per testare il modulo di condivisione, fare clic sul pulsante "Avvia sessione di Azure ASA" che avvierà la sessione di ancoraggio spaziale di Azure e quindi creare l'ancoraggio di Azure facendo clic sul pulsante "Crea ancoraggio Azure" e attendere qualche minuto per la creazione dell'ancoraggio di Azure. Dopo aver creato l'ancoraggio di Azure, fare clic sul pulsante "Condividi Azure Anchor" per condividere l'ancoraggio Azure creato dal HoloLens.

7. Per ricevere l'ancoraggio Azure condiviso in un altro HoloLens, fare clic su "Avvia sessione di Azure ASA" per avviare e ottenere la sessione ASA corrente e fare clic sul pulsante "Ottieni ancoraggio di Azure" per ottenere l'ancoraggio Azure condiviso dall'altro HoloLens.

   > Nota: Tutti i dettagli delle azioni corrispondenti sui singoli pulsanti verranno visualizzati nella finestra di debug.

## <a name="congratulations"></a>Lezione completata

In questa lezione si è appreso come integrare i nuovi ancoraggi spaziali di Azure per allineare i dispositivi con percorso condiviso in un'esperienza condivisa. Questa lezione conclude anche il modulo sharing. Si è appreso come configurare un nuovo account Photon, integrare Photon e PUN in una nuova applicazione Unity, configurare gli avatar e gli oggetti condivisi e infine allineare più partecipanti usando ASA. 

