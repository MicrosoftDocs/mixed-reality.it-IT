---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 2. Salvataggio, recupero e condivisione di ancoraggi nello spazio di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362013"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Salvataggio, recupero e condivisione di ancoraggi nello spazio di Azure

In questa esercitazione apprenderai come salvare gli ancoraggi nello spazio di Azure in più sessioni dell'app salvando l'ID ancoraggio nella memoria di HoloLens 2. Apprenderai anche come condividere questo ID con altri dispositivi per un allineamento degli ancoraggi su più dispositivi.

## <a name="objectives"></a>Obiettivi

* Apprendere come salvare e recuperare gli ID degli ancoraggi nello spazio di Azure sul e dal disco locale di HoloLens 2 per renderli permanenti tra una sessione e l'altra dell'app
* Apprendere come condividere gli ID degli ancoraggi nello spazio di Azure tra gli utenti in uno scenario con più dispositivi

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Prefab). Tenendo premuto il pulsante CTRL, fai clic su **ButtonParent_SaveAnchorId** e su **ButtonParent_ShareAnchorId** per selezionare i due prefab, quindi trascinali nella finestra Hierarchy (Gerarchia) per aggiungerli alla scena:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Rendere permanenti gli ancoraggi di Azure tra una sessione e l'altra dell'app - Salvare l'ID ancoraggio sul disco
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

In questa sezione apprenderai come salvare e recuperare l'ID ancoraggio di Azure sul e dal disco locale di HoloLens 2. In questo modo potrai eseguire query su Azure per ottenere lo stesso ID ancoraggio tra sessioni diverse dell'app e gli ologrammi ancorati potranno essere collocati nella stessa posizione in cui si trovavano nella sessione precedente dell'app.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent_SaveAnchorId** che contiene due pulsanti, uno per salvare l'ID ancoraggio di Azure nella memoria di HoloLens 2 e un altro per recuperare dal disco l'ID salvato:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

Segui la stessa procedura illustrata nelle istruzioni per la [configurazione dei pulsanti per il funzionamento della scena](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) contenute nell'esercitazione precedente per configurare i componenti **Pressable Button Holo Lens 2 (Script)** (Pulsante a pressione Holo Lens 2 - Script) e **Interactable (Script)** (Con supporto per interazioni - Script) per ognuno dei due pulsanti:

* Per l'oggetto **SaveAzureAnchorIdToDisk**, assegna la funzione AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Per l'oggetto **GetAzureAnchorIdFromDisk**, assegna la funzione AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Se compili l'applicazione aggiornata in HoloLens, ora puoi rendere permanenti gli ancoraggi nello spazio di Azure, ovvero mantenerli da una sessione all'altra dell'app salvando l'ID ancoraggio di Azure. Per provare, puoi seguire questa procedura:

1. Sposta l'esperienza Rocket Launcher (Lanciamissili) nella posizione desiderata.
2. Avvia la sessione di Azure.
3. Crea l'ancoraggio di Azure. Gli ancoraggi vengono creati nella posizione dell'esperienza Rocket Launcher (Lanciamissili).
4. Salva l'ID ancoraggio di Azure su disco.
5. Riavvia l'applicazione.
6. Recupera l'ancoraggio di Azure dal disco. Viene caricato l'ID ancoraggio appena salvato.
7. Avvia la sessione di Azure.
8. Trova l'ancoraggio di Azure. L'esperienza Rocket Launcher (Lanciamissili) viene collocata nella posizione del passaggio 3.

> [!NOTE]
> Per riavviare completamente l'applicazione, dopo aver chiuso la visualizzazione di app immersiva, devi chiudere la finestra dell'app nell'ambiente iniziale prima di eseguire il riavvio dal menu Start. Per altri dettagli, puoi fare riferimento alla documentazione sull'[uso di app in HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens).

## <a name="share-azure-anchors-between-multiple-devices"></a>Condividere gli ancoraggi di Azure tra più dispositivi

In questa sezione apprenderai come condividere l'ID ancoraggio di Azure tra più dispositivi. In questo modo, diversi dispositivi potranno eseguire query su Azure per ottenere lo stesso ID ancoraggio, consentendo l'allineamento spaziale degli ologrammi ancorati. L'allineamento spaziale, ovvero la visualizzazione degli stessi ologrammi nella stessa posizione fisica su più dispositivi, è fondamentale per le esperienze condivise locali in HoloLens 2.

Esistono diversi modi per trasferire gli ID ancoraggio di Azure da un dispositivo all'altro, inclusi i metodi descritti nella serie [Esercitazioni sulle funzionalità multiutente](mrlearning-sharing(photon)-ch1.md). In questo esempio userai un servizio Web semplice per caricare e scaricare gli ID ancoraggio tra dispositivi.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent_ShareAnchorId** che contiene due pulsanti, uno per caricare l'ID ancoraggio di Azure nel server Web e un altro per scaricare l'ID dal server Web:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

Segui la stessa procedura illustrata nelle istruzioni per la [configurazione dei pulsanti per il funzionamento della scena](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) contenute nell'esercitazione precedente per configurare i componenti **Pressable Button Holo Lens 2 (Script)** (Pulsante a pressione Holo Lens 2 - Script) e **Interactable (Script)** (Con supporto per interazioni - Script) per ognuno dei due pulsanti:

* Per l'oggetto **ShareAzureAnchorIdToNetwork**, assegna la funzione AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Per l'oggetto **GetAzureAnchorIdFromNetwork**, assegna la funzione AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Se compili l'applicazione aggiornata in due dispositivi HoloLens, ora puoi ottenere l'allineamento spaziale tra di essi condividendo l'ID ancoraggio di Azure. Per provare, puoi seguire questa procedura:

1. Sul dispositivo HoloLens 1 - Sposta l'esperienza Rocket Launcher (Lanciamissili) nella posizione desiderata.
2. Sul dispositivo HoloLens 1 - Avvia la sessione di Azure.
3. Sul dispositivo HoloLens 1 - Crea l'ancoraggio di Azure. Gli ancoraggi vengono creati nella posizione dell'esperienza Rocket Launcher (Lanciamissili).
4. Sul dispositivo HoloLens 1 - Condividi l'ID ancoraggio di Azure sulla rete.
5. Sul dispositivo HoloLens 2 - Avvia l'applicazione.
6. Sul dispositivo HoloLens 2 - Ottieni l'ID ancoraggio condiviso dalla rete. Dal dispositivo HoloLens 1 viene recuperato l'ID ancoraggio appena condiviso.
7. Sul dispositivo HoloLens 2 - Avvia la sessione di Azure.
8. Sul dispositivo HoloLens 2 - Trova l'ancoraggio di Azure. L'esperienza Rocket Launcher (Lanciamissili) viene collocata nella posizione del passaggio 3.

> [!TIP]
> Se è presente un solo HoloLens, puoi comunque provare la funzionalità riavviando l'applicazione invece di usare un secondo HoloLens.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come mantenere gli ancoraggi nello spazio di Azure tra una sessione e l'altra o un riavvio e l'altro dell'applicazione salvando l'ID ancoraggio nello spazio di Azure sul disco locale di HoloLens. Hai anche appreso come condividere gli ancoraggi nello spazio di Azure tra più dispositivi per un'esperienza condivisa di base multiutente con ologrammi statici.

Nell'esercitazione successiva apprenderai come fornire agli utenti il feedback in tempo reale. Questo feedback includerà informazioni sulla creazione degli ancoraggi, sulla qualità della comprensione dell'ambiente e sullo stato della sessione di Azure. Senza feedback, gli utenti potrebbero non sapere se un ancoraggio è stato caricato correttamente in Azure, se la qualità dell'ambiente è sufficiente per la creazione degli ancoraggi o quale sia lo stato corrente.

[Lezione successiva: 3. Visualizzazione del feedback su Ancoraggi nello spazio di Azure](mrlearning-asa-ch3.md)
