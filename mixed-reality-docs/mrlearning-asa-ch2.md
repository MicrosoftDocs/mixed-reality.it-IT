---
title: Esercitazioni sugli ancoraggi spaziali di Azure-2. Salvataggio, recupero e condivisione di ancoraggi spaziali di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250741"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. salvataggio, recupero e condivisione di ancoraggi spaziali di Azure

In questa esercitazione si apprenderà come salvare gli ancoraggi spaziali di Azure tra più sessioni dell'app salvando l'ID di ancoraggio nell'archivio di HoloLens 2. Si apprenderà anche come condividere questo ID di ancoraggio ad altri dispositivi per un allineamento di ancoraggio a più dispositivi.

## <a name="objectives"></a>Obiettivi

* Informazioni su come salvare e recuperare gli ID di ancoraggio spaziale di Azure da e verso il disco locale HoloLens 2, per la persistenza tra le sessioni dell'app
* Informazioni su come condividere gli ID di ancoraggio spaziali di Azure tra gli utenti in uno scenario con più dispositivi

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra del progetto passare a **assets** > **MRTK. Tutorials. AzureSpatialAnchors** > cartella **prefabbricates** . Tenendo premuto il pulsante CTRL, fare clic su **ButtonParent_SaveAnchorId** e **ButtonParent_ShareAnchorId** per selezionare i due prefissi, quindi trascinarli nella finestra della gerarchia per aggiungerli alla scena:

![mrlearning-ASA](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Mantieni gli ancoraggi di Azure tra le sessioni dell'app-salva l'ID ancoraggio sul disco
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

In questa sezione si apprenderà come salvare e recuperare l'ID di ancoraggio di Azure da e verso il disco locale HoloLens 2. In questo modo sarà possibile eseguire query in Azure per lo stesso ID di ancoraggio tra diverse sessioni dell'app, consentendo agli ologrammi ancorati di essere posizionati nella stessa posizione della sessione dell'app precedente.

Nella finestra gerarchia espandere l'oggetto **ButtonParent_SaveAnchorId** contenente due pulsanti, un pulsante per il salvataggio dell'ID di ancoraggio di Azure nell'archiviazione HoloLens 2 e un altro per il recupero dell'ID salvato dal disco:

![mrlearning-ASA](images/mrlearning-asa/tutorial2-section2-step1-1.png)

Seguire la stessa procedura illustrata nella sezione [configurazione dei pulsanti per usare le](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) istruzioni della scena dell'esercitazione precedente per configurare il componente di controllo di **Holo Lens 2 (script)** e il componente **interactable (script)** in ognuno dei due pulsanti:

* Per l'oggetto **SaveAzureAnchorIdToDisk** , assegnare la funzione AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Per l'oggetto **GetAzureAnchorIdFromDisk** , assegnare la funzione AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Se si compila l'applicazione aggiornata in HoloLens, è ora possibile salvare in modo permanente gli ancoraggi spaziali di Azure tra le sessioni dell'app salvando l'ID di ancoraggio di Azure. Per eseguire il test, è possibile seguire questa procedura:

1. Spostare l'esperienza di avvio del Rocket nella posizione desiderata.
2. Avviare la sessione di Azure.
3. Creare Anchor di Azure (crea ancoraggi in corrispondenza della posizione dell'esperienza di avvio Rocket).
4. Salvare l'ID ancoraggio di Azure su disco.
5. Riavviare l'applicazione.
6. Ottenere Azure Anchor dal disco (carica l'ID di ancoraggio appena salvato).
7. Avviare la sessione di Azure.
8. Trovare l'ancoraggio di Azure (posiziona l'esperienza di avvio Rocket nella posizione del passaggio 3).

## <a name="share-azure-anchors-between-multiple-devices"></a>Condividere gli ancoraggi di Azure tra più dispositivi

In questa sezione si apprenderà come condividere l'ID ancoraggio di Azure tra più dispositivi. Questo consentirà a più dispositivi di eseguire query su Azure per lo stesso ID ancoraggio, consentendo agli ologrammi ancorati di essere allineati dal punto di vista spaziale. L'allineamento spaziale, ovvero la visualizzazione degli stessi ologrammi nella stessa posizione fisica tra più dispositivi, è fondamentale per le esperienze condivise locali in HoloLens 2.

Esistono diversi modi per trasferire gli ID di ancoraggio di Azure tra i dispositivi, inclusi i metodi descritti nella serie di [esercitazioni sulle funzionalità multiutente](mrlearning-sharing(photon)-ch1.md) . In questo esempio si userà un semplice servizio Web per caricare e scaricare gli ID di ancoraggio tra i dispositivi.

Nella finestra gerarchia espandere l'oggetto **ButtonParent_ShareAnchorId** contenente due pulsanti; un pulsante per caricare l'ID di ancoraggio di Azure nel server Web e un altro per scaricare l'ID dal server Web:

![mrlearning-ASA](images/mrlearning-asa/tutorial2-section3-step1-1.png)

Seguire la stessa procedura illustrata nella sezione [configurazione dei pulsanti per usare le](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) istruzioni della scena dell'esercitazione precedente per configurare il componente di controllo di **Holo Lens 2 (script)** e il componente **interactable (script)** in ognuno dei due pulsanti:

* Per l'oggetto **ShareAzureAnchorIdToNetwork** , assegnare la funzione AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Per l'oggetto **GetAzureAnchorIdFromNetwork** , assegnare la funzione AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Se si compila l'applicazione aggiornata in due dispositivi HoloLens, è ora possibile ottenere l'allineamento spaziale tra di essi condividendo l'ID ancoraggio di Azure. Per eseguire il test, è possibile seguire questa procedura:

1. Sul dispositivo HoloLens 1: spostare l'esperienza dell'utilità di avvio Rocket nella posizione desiderata.
2. Sul dispositivo HoloLens 1: avviare la sessione di Azure.
3. In HoloLens Device 1: create Azure Anchor (crea ancoraggi in corrispondenza della posizione dell'esperienza di avvio di Rocket).
4. Sul dispositivo HoloLens 1: condividere l'ID ancoraggio di Azure con la rete.
5. Sul dispositivo HoloLens 2: riavviare l'applicazione.
6. Sul dispositivo HoloLens 2: ottenere l'ID di ancoraggio condiviso dalla rete (Recupera l'ID di ancoraggio appena condiviso dal dispositivo HoloLens 1).
7. Nel dispositivo HoloLens 2: avviare la sessione di Azure.
8. Sul dispositivo HoloLens 2: trovare l'ancoraggio di Azure (posiziona l'esperienza di avvio Rocket in corrispondenza della posizione del passaggio 3).

> [!TIP]
> Se è presente un solo HoloLens, è comunque possibile testare la funzionalità riavviando l'applicazione invece di usare un secondo dispositivo HoloLens.

## <a name="congratulations"></a>Complimenti

In questa esercitazione si è appreso come salvare in modo permanente gli ancoraggi spaziali di Azure tra le sessioni dell'applicazione e i riavvii delle applicazioni salvando l'ID di ancoraggio spaziale di Azure nel disco locale in HoloLens. Si è anche appreso come condividere gli ancoraggi spaziali di Azure tra più dispositivi per un'esperienza condivisa di base di un ologramma statico multiutente.

Nell'esercitazione successiva si apprenderà come fornire agli utenti il feedback in tempo reale. Questo feedback includerà informazioni sulla creazione di ancoraggi, sulla qualità della comprensione dell'ambiente e sullo stato della sessione di Azure. Senza commenti, gli utenti potrebbero non sapere se un ancoraggio è stato caricato correttamente in Azure, se la qualità dell'ambiente è sufficiente per la creazione dell'ancoraggio o lo stato corrente.

[Lezione successiva: 3. Visualizzazione del feedback di ancoraggio spaziale di Azure](mrlearning-asa-ch3.md)
