---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 3. Salvataggio, recupero e condivisione di ancoraggi nello spazio di Azure
description: Completa questo corso per apprendere come implementare ancoraggi nello spazio di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 274722588f156cb01fdd45525912e2e15687bc2d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376533"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a>3. Salvataggio, recupero e condivisione di ancoraggi nello spazio di Azure

In questa esercitazione apprenderai come salvare gli ancoraggi nello spazio di Azure in più sessioni dell'app salvando l'ID ancoraggio nella memoria di HoloLens 2. Apprenderai anche come condividere questo ID con altri dispositivi per un allineamento degli ancoraggi su più dispositivi.

## <a name="objectives"></a>Obiettivi

* Apprendere come ottenere l'allineamento spaziale tra più sessioni dell'app.
* Apprendere come ottenere l'allineamento spaziale tra più dispositivi.

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent**. Seleziona gli **ultimi quattro oggetti pulsante figlio**. Nella finestra Inspector (Controllo) **seleziona** la casella di controllo accanto al campo del nome per rendere attivi tutti gli oggetti.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

Nella finestra Hierarchy (Gerarchia) seleziona gli oggetti **ButtonParent**. Quindi nella finestra Inspector (Controllo) individua il componente **GridObjectCollection** e fai clic sul pulsante **Update Collection** (Aggiorna raccolta) per aggiornare la posizione di tutti gli oggetti figlio dell'oggetto **ButtonParent**.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a>Mantenimento degli ancoraggi nello spazio di Azure tra sessioni dell'app

In questa sezione apprenderai come salvare e recuperare l'ID ancoraggio di Azure sul e dal disco locale di HoloLens. In questo modo potrai eseguire query su Azure per ottenere lo stesso ID ancoraggio tra sessioni diverse dell'app e gli ologrammi ancorati potranno essere collocati nella stessa posizione in cui si trovavano nella sessione precedente dell'app.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e individua i due pulsanti denominati **SaveAzureAnchorIdToDisk** e **GetAzureAnchorIdFromDisk**:

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

Segui la stessa procedura illustrata nelle istruzioni per la [configurazione dei pulsanti per il funzionamento della scena](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) contenute nell'esercitazione precedente per configurare il componente **Interactable (Script)** (Con supporto per interazioni - Script) per ognuno dei due pulsanti:

* Per l'oggetto pulsante **SaveAzureAnchorIdToDisk**, assegna la funzione AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Per l'oggetto pulsante **GetAzureAnchorIdFromDisk**, assegna la funzione AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Se compili l'app aggiornata in HoloLens, ora puoi rendere permanenti gli ancoraggi nello spazio di Azure, ovvero mantenerli da una sessione all'altra dell'app salvando l'ID ancoraggio di Azure. Per provare, puoi seguire questa procedura:

1. Sposta Rover Explorer (Esplora Rover) nella posizione desiderata
2. Avvia la sessione di Azure
3. Crea l'ancoraggio di Azure; gli ancoraggi vengono creati nella posizione di Rover Explorer (Esplora Rover)
4. Salva l'ID ancoraggio di Azure su disco
5. Riavvia l'app
6. Recupera l'ancoraggio di Azure dal disco; viene caricato l'ID ancoraggio appena salvato
7. Avvia la sessione di Azure
8. Trova l'ancoraggio di Azure; l'esperienza Rover Explorer (Esplora Rover) viene collocata nella posizione del passaggio 3

> [!NOTE]
> Per riavviare completamente l'app, dopo aver chiuso la visualizzazione di app immersiva devi chiudere la finestra dell'app nell'ambiente iniziale di realtà mista prima di eseguire il riavvio dal menu Start. Per altri dettagli, puoi fare riferimento alla documentazione sull'[uso di app in HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens).

## <a name="sharing-azure-spatial-anchors-between-devices"></a>Condivisione degli ancoraggi nello spazio di Azure tra dispositivi

In questa sezione apprenderai come condividere l'ID ancoraggio di Azure tra più dispositivi. In questo modo, diversi dispositivi potranno eseguire query su Azure per ottenere lo stesso ID ancoraggio, consentendo l'allineamento spaziale degli ologrammi ancorati. L'allineamento spaziale, ovvero la visualizzazione degli stessi ologrammi nella stessa posizione fisica su più dispositivi, è fondamentale per le esperienze condivise locali in HoloLens 2.

Esistono diversi modi per trasferire gli ID ancoraggio di Azure da un dispositivo all'altro, inclusi i metodi descritti nella serie [Esercitazioni sulle funzionalità multiutente](mr-learning-sharing-02.md). In questo esempio userai un servizio Web semplice per caricare e scaricare gli ID ancoraggio tra dispositivi.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent**.   Individua i due pulsanti denominati **ShareAzureAnchorIdToNetwork** e **GetAzureAnchorIdFromNetwork**:

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

Segui la stessa procedura illustrata nelle istruzioni per la [configurazione dei pulsanti per il funzionamento della scena](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) contenute nell'esercitazione precedente per configurare il componente **Interactable (Script)** (Con supporto per interazioni - Script) per ognuno dei due pulsanti:

* Per l'oggetto **ShareAzureAnchorIdToNetwork**, assegna la funzione AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Per l'oggetto **GetAzureAnchorIdFromNetwork**, assegna la funzione AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Se compili l'app aggiornata in due dispositivi HoloLens, ora puoi ottenere l'allineamento spaziale condividendo l'ID ancoraggio di Azure. Per provare, puoi seguire questa procedura:

1. Sul dispositivo HoloLens 1 - Sposta Rover Explorer (Esplora Rover) nella posizione desiderata.
2. Sul dispositivo HoloLens 1 - Avvia la sessione di Azure.
3. Sul dispositivo HoloLens 1 - Crea l'ancoraggio di Azure. Gli ancoraggi vengono creati nella posizione di Rover Explorer (Esplora Rover).
4. Sul dispositivo HoloLens 1 - Condividi l'ID ancoraggio di Azure sulla rete.
5. Sul dispositivo HoloLens 2 - Avvia l'app.
6. Sul dispositivo HoloLens 2 - Ottieni l'ID ancoraggio condiviso dalla rete. Dal dispositivo HoloLens 1 viene recuperato l'ID ancoraggio appena condiviso.
7. Sul dispositivo HoloLens 2 - Avvia la sessione di Azure.
8. Sul dispositivo HoloLens 2 - Trova l'ancoraggio di Azure. L'esperienza Rover Explorer (Esplora Rover) viene collocata nella posizione del passaggio 3.

> [!TIP]
> Se è presente un solo dispositivo HoloLens, puoi comunque testare la funzionalità riavviando l'app invece di usare un secondo dispositivo HoloLens.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come mantenere gli ancoraggi nello spazio di Azure tra una sessione e l'altra e un riavvio e l'altro dell'app salvando l'ID ancoraggio nello spazio di Azure sul disco locale di HoloLens. Hai anche appreso come condividere gli ancoraggi nello spazio di Azure tra più dispositivi per un'esperienza condivisa di base multiutente con ologrammi statici.

Nell'esercitazione successiva apprenderai come fornire agli utenti il feedback in tempo reale. Questo feedback includerà informazioni sulla creazione degli ancoraggi, sulla qualità della comprensione dell'ambiente e sullo stato della sessione di Azure. Senza feedback, gli utenti potrebbero non sapere se un ancoraggio è stato caricato correttamente in Azure, se la qualità dell'ambiente è sufficiente per la creazione degli ancoraggi o quale sia lo stato corrente.

[Esercitazione successiva: 4. Visualizzazione del feedback su Ancoraggi nello spazio di Azure](mr-learning-asa-04.md)
