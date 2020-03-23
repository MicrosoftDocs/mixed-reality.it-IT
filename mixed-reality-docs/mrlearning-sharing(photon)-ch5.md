---
title: Esercitazioni sulle funzionalità multiutente - 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031684"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa

In questa lezione apprenderai come integrare Ancoraggi nello spazio di Azure nell'esperienza condivisa. Questo servizio consente a più dispositivi con percorso condiviso di avere un riferimento comune se l'ambiente fisico prevede l'ancoraggio di esperienze virtuali in modo che tutti i partecipanti vedano gli oggetti nella stessa posizione fisica.

## <a name="objectives"></a>Obiettivi

* Integrare Ancoraggi nello spazio di Azure in un'esperienza condivisa per l'allineamento di più dispositivi.
* Apprendere le nozioni di base sul funzionamento di Ancoraggi nello spazio di Azure nel contesto di un'esperienza condivisa locale.

## <a name="instructions"></a>Istruzioni

1. Seleziona il prefab TableAnchor sotto l'oggetto padre MixedRealityPlayspace ed eliminalo.

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. Nella vista Project (Progetto) passa ad Assets (Asset)->Resources (Risorse)->Prefabs (Prefab) e trascina il prefab TableAnchor sull'oggetto SharedPlayground per farlo diventare un oggetto figlio.

3. Espandi l'oggetto padre MixedRealityPlayspace, l'oggetto TableAnchor ed espandi anche l'oggetto Buttons.

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. A questo punto, nella gerarchia seleziona ShareAzureAnchorButton e concentra la tua attenzione sul pannello Inspector (Controllo). Scorri verso il basso fino al menu a discesa visualizzato nell'immagine seguente, scegli AnchorModuleScript e fai clic su ShareAnchorNetwork().

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Seleziona GetAzureAnchorButton (vedi il passaggio 4) e concentrati di nuovo sul pannello Inspector (Controllo). Scorri verso il basso fino al menu a discesa visualizzato nell'immagine seguente, scegli AnchorModuleScript, fai clic su GetSharedAnchorNetwork() ed effettua il salvataggio.

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Ripeti il passaggio 4 per collegare la funzione StartAzureSession () a StartAzureSessionButton.

7. Ripeti il passaggio 4 per collegare la funzione CreateAzureAnchor () a CreateAzureAnchorButton e verifica che l'oggetto TableAnchor sia assegnato al campo "Game Object" (Oggetto Game) del parametro della funzione.

8. Segui le istruzioni contenute in [Collegare la scena alla risorsa di Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) per aggiungere le tue credenziali del servizio Ancoraggi nello spazio di Azure.

9. Per provare il modulo di condivisione, avvia la sessione facendo clic sul pulsante "Start Azure ASA Session" (Avvia sessione di Ancoraggi nello spazio di Azure) e quindi crea l'ancoraggio facendo clic sul pulsante "Create Azure Anchor" (Crea ancoraggio di Azure). Attendi che l'ancoraggio di Azure venga creato. Dopo aver creato l'ancoraggio di Azure, fai clic sul pulsante "Share Azure Anchor" (Condividi ancoraggio di Azure) per condividere da HoloLens l'ancoraggio di Azure creato.

10. Per ricevere l'ancoraggio di Azure condiviso in un altro HoloLens, fai clic su "Start Azure ASA Session" (Avvia sessione di Ancoraggi nello spazio di Azure) per avviare e accedere alla sessione corrente di Ancoraggi nello spazio di Azure.

11. Fai clic sul pulsante "Get Azure Anchor" (Ottieni ancoraggio di Azure) per ottenere dall'altro HoloLens l'ancoraggio di Azure condiviso.

## <a name="congratulations"></a>Lezione completata

In questa lezione hai appreso come integrare il nuovo e potente servizio Ancoraggi nello spazio di Azure per allineare i dispositivi con percorso condiviso in un'esperienza condivisa. Qui inoltre si conclude il modulo di condivisione. Hai appreso come impostare un nuovo account Photon, integrare Photon e PUN in una nuova applicazione Unity, configurare avatar e oggetti condivisi e infine allineare più partecipanti con Ancoraggio nello spazio di Azure.
