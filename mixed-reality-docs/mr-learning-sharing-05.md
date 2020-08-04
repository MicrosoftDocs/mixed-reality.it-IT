---
title: Esercitazioni sulle funzionalità multiutente - 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: fc8e20a9ddaa595db0a3d59975e7c785d01c0a6d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376583"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa

In questa esercitazione apprenderai come integrare Ancoraggi nello spazio di Azure nell'esperienza condivisa. Ancoraggi nello spazio di Azure consente a più dispositivi di avere un riferimento comune al mondo fisico, in modo che gli utenti possano vedersi reciprocamente nella rispettiva posizione fisica effettiva e vedere l'esperienza condivisa nella medesima posizione.

## <a name="objectives"></a>Obiettivi

* Integrare Ancoraggi nello spazio di Azure in un'esperienza condivisa per l'allineamento di più dispositivi
* Apprendere le nozioni di base sul funzionamento di Ancoraggi nello spazio di Azure nel contesto di un'esperienza condivisa locale

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **SharedPlayground** e quindi l'oggetto **TableAnchor** per esporre i relativi oggetti figlio:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e trascinare il prefab **Buttons** nell'oggetto figlio **TableAnchor**, per aggiungerlo alla scena come elemento figlio dell'oggetto TableAnchor:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurazione dei pulsanti per il funzionamento della scena

In questa sezione verrà configurata una serie di eventi Button che illustrano le nozioni di base per poter usare Ancoraggi nello spazio di Azure e ottenere l'allineamento spaziale in un'esperienza condivisa.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **Button** e seleziona il primo oggetto pulsante figlio denominato **StartAzureSession**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

Nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:

* Al campo **None (Object)** (Nessuno - Oggetto) assegnare l'oggetto **TableAnchor**
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare la funzione **AnchorModuleScript** > **StartAzureSession ()**

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

Nella finestra Hierarchy (Gerarchia) seleziona il secondo oggetto pulsante figlio denominato **CreateAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:

* Al campo **None (Object)** (Nessuno - Oggetto) assegnare l'oggetto **TableAnchor**
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare la funzione **AnchorModuleScript** > **CreateAzureAnchor ()**
* Al nuovo campo **None (Game Object)** (Nessuno - Oggetto gioco) che viene visualizzato assegna l'oggetto **TableAnchor**

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

Nella finestra Hierarchy (Gerarchia) seleziona il terzo oggetto pulsante figlio denominato **ShareAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:

* Al campo **None (Object)** (Nessuno - Oggetto) assegnare l'oggetto **TableAnchor**
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare la funzione **SharingModuleScript** > **ShareAzureAnchor ()**

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

Nella finestra Hierarchy (Gerarchia) selezionare il quarto oggetto pulsante figlio denominato **GetAzureAnchor** e quindi nella finestra Inspector (Controllo) individuare il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configurare l'evento **OnClick ()** nel modo seguente:

* Al campo **None (Object)** (Nessuno - Oggetto) assegnare l'oggetto **TableAnchor**
* Nell'elenco a discesa **No Function** (Nessuna funzione) selezionare la funzione **SharingModuleScript** > **GetAzureAnchor ()**

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Connessione della scena alla risorsa di Azure

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **SharedPlayground** e seleziona l'oggetto **TableAnchor**.

Nella finestra Inspector (Controllo) individuare il componente **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - Script) e configurare la sezione **Credentials** (Credenziali) con le credenziali dell'account di Ancoraggi nello spazio di Azure creato in fase di definizione dei [Prerequisiti](mr-learning-sharing-01.md#prerequisites) per questa serie di esercitazioni:

* Nel campo **Spatial Anchors Account ID** (ID account Ancoraggi nello spazio) incolla il valore di **Account ID** (ID account) del tuo account di Ancoraggi nello spazio di Azure
* Nel campo **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio) incolla il valore di **Access Key** (Chiave di accesso) primario o secondario del tuo account di Ancoraggi nello spazio di Azure

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> Anziché impostare nella scena l'ID e la chiave dell'account di Ancoraggi nello spazio, è possibile impostarla per l'intero progetto. Questa soluzione può risultare vantaggiosa se sono disponibili più scene con ASA. A tale scopo, nella finestra Project (Progetto) passare all'asset Assets (Asset) > AzureSpatialAnchors.SDK > Resources (Risorse) > **SpatialAnchorConfig** e quindi impostare i valori nella finestra Inspector (Controllo).

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **TableAnchor** e quindi nella finestra Inspector (Controllo) individuare il componente **Anchor Module (Script)** (Modulo di ancoraggio - Script) e configuralo nel modo seguente:

* Nel campo **Public Sharing Pin** (PIN di condivisione pubblico) modificare alcune cifre, in modo che il PIN diventi univoco per il progetto

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

Con l'oggetto **TableAnchor** ancora selezionato, nella finestra Inspector (Controllo) verificare che tutti i componenti dello script siano **abilitati**:

* Seleziona la casella di controllo accanto a **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - Script) per abilitarlo
* Seleziona la casella di controllo accanto a **Anchor Module Script (Script)** (Script modulo di ancoraggio - Script) per abilitarlo
* Seleziona la casella di controllo accanto a **Sharing Module Script (Script)** (Script modulo di condivisione - Script) per abilitarlo

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>Prova dell'esperienza con l'allineamento spaziale

> [!NOTE]
> Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity. Di conseguenza, per testare la funzionalità di questo servizio, è necessario distribuire il progetto in almeno due dispositivi.

Se si compila e distribuisce il progetto Unity in due dispositivi, è possibile ottenere l'allineamento spaziale tra i dispositivi condividendo l'ID ancoraggio di Azure. Per provare, puoi seguire questa procedura:

1. Nel dispositivo 1: **Avviare l'app** (un'istanza di Rover Explorer è stata creata e posizionata sulla tabella)
2. Nel dispositivo 2: **Avviare l'app** (entrambi gli utenti visualizzano la tabella con Rover Explorer, ma la tabella non è visualizzata nella stessa posizione e gli avatar degli utenti non compaiono nella posizione reale degli utenti)
3. Nel dispositivo 1: Premi il pulsante **Start Azure Session** (Avvia sessione di Azure)
4. Nel dispositivo 1: Premi il pulsante **Create Azure Anchor** (Crea ancoraggio di Azure) (crea l'ancoraggio nella posizione dell'oggetto TableAnchor e archivia le informazioni relative all'ancoraggio nella risorsa di Azure).
5. Nel dispositivo 1: Premi il pulsante **Share Azure Anchor** (Condividi ancoraggio di Azure) (condivide l'ID ancoraggio con altri utenti in tempo reale)
6. Nel dispositivo 2: Premi il pulsante **Start Azure Session** (Avvia sessione di Azure)
7. Nel dispositivo 2: Premere il pulsante **Get Azure Anchor** (Ottieni ancoraggio di Azure) (si connette alla risorsa di Azure per recuperare le informazioni relative all'ancoraggio per l'ID ancoraggio condiviso e quindi sposta l'oggetto TableAnchor nella posizione in cui è stato creato l'ancoraggio con il dispositivo 1)

> [!TIP]
> Se non si ha accesso a due dispositivi HoloLens, è possibile seguire la procedura per la [creazione di Ancoraggi nello spazio di Azure per dispositivi mobili](mr-learning-asa-05.md) per distribuire il progetto nel dispositivo mobile.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come integrare il potente servizio Ancoraggi nello spazio di Azure per allineare i dispositivi in un'esperienza condivisa.

Si conclude così la serie di esercitazioni in cui sono state fornite istruzioni per impostare un account Photon, creare un'app PUN, integrare PUN nel progetto Unity, configurare gli avatar degli utenti e gli oggetti condivisi e infine allineare più partecipanti tramite Ancoraggi nello spazio di Azure.
