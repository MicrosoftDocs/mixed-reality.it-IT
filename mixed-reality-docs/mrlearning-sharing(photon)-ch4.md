---
title: Esercitazioni sulle funzionalità multiutente - 5. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa
description: Completa questo corso per imparare a implementare esperienze condivise multiutente all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604972"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a>4. Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa

In questa esercitazione apprenderai come integrare Ancoraggi nello spazio di Azure nell'esperienza condivisa. Ancoraggi nello spazio di Azure consente a più dispositivi di avere un riferimento comune al mondo fisico, in modo che gli utenti possano vedersi reciprocamente nella rispettiva posizione fisica effettiva e vedere l'esperienza condivisa nella medesima posizione.

## <a name="objectives"></a>Obiettivi

* Integrare Ancoraggi nello spazio di Azure in un'esperienza condivisa per l'allineamento di più dispositivi
* Apprendere le nozioni di base sul funzionamento di Ancoraggi nello spazio di Azure nel contesto di un'esperienza condivisa locale

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **SharedPlayground** e quindi l'oggetto **TableAnchor** per esporre i relativi oggetti figlio:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Prefab) e trascina il prefab **Buttons** nella parte superiore dell'oggetto figlio **TableAnchor** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena come elemento figlio dell'oggetto TableAnchor:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurazione dei pulsanti per il funzionamento della scena

In questa sezione configurerai una serie di eventi Button che illustrano le nozioni di base per poter usare Ancoraggi nello spazio di Azure e ottenere l'allineamento spaziale in un'esperienza condivisa.

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **Button** e seleziona il primo oggetto pulsante figlio denominato **StartAzureSession**:

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

Nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:

* Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **TableAnchor**
* Nell'elenco a discesa **No Function** (Nessuna funzione) seleziona la funzione **AnchorModuleScript** > **StartAzureSession ()**

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

Nella finestra Hierarchy (Gerarchia) seleziona il secondo oggetto pulsante figlio denominato **CreateAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:

* Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **TableAnchor**
* Nell'elenco a discesa **No Function** (Nessuna funzione) seleziona la funzione **AnchorModuleScript** > **CreateAzureAnchor ()**
* Al nuovo campo **None (Game Object)** (Nessuno - Oggetto gioco) che viene visualizzato assegna l'oggetto **TableAnchor**

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

Nella finestra Hierarchy (Gerarchia) seleziona il terzo oggetto pulsante figlio denominato **ShareAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:

* Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **TableAnchor**
* Nell'elenco a discesa **No Function** (Nessuna funzione) seleziona la funzione **SharingModuleScript** > **ShareAzureAnchor ()**

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

Nella finestra Hierarchy (Gerarchia) seleziona il quarto oggetto pulsante figlio denominato **GetAzureAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e configura l'evento **OnClick ()** nel modo seguente:

* Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **TableAnchor**
* Nell'elenco a discesa **No Function** (Nessuna funzione) seleziona la funzione **SharingModuleScript** > **GetAzureAnchor ()**

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Connessione della scena alla risorsa di Azure

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **SharedPlayground** e seleziona l'oggetto **TableAnchor**. Nella finestra Inspector (Controllo) individua quindi il componente **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - Script) e configura la sezione **Credentials** (Credenziali) con le credenziali dell'account di Ancoraggi nello spazio di Azure creato in fase di definizione dei [Prerequisiti](mrlearning-sharing(photon)-ch1.md#prerequisites) per questa serie di esercitazioni:

* Nel campo **Spatial Anchors Account ID** (ID account Ancoraggi nello spazio) incolla il valore di **Account ID** (ID account) del tuo account di Ancoraggi nello spazio di Azure
* Nel campo **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio) incolla il valore di **Access Key** (Chiave di accesso) primario o secondario del tuo account di Ancoraggi nello spazio di Azure

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

Con l'oggetto **TableAnchor** ancora selezionato, nella finestra Inspector (Controllo) verifica che tutti i componenti di script siano abilitati:

* Seleziona la casella di controllo accanto a **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - Script) per abilitarlo
* Seleziona la casella di controllo accanto a **Anchor Module Script (Script)** (Script modulo di ancoraggio - Script) per abilitarlo
* Seleziona la casella di controllo accanto a **Sharing Module Script (Script)** (Script modulo di condivisione - Script) per abilitarlo

![Condivisione apprendimento Realtà mista](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>Prova dell'esperienza con l'allineamento spaziale

> [!NOTE]
> Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity. Pertanto, per testare la funzionalità di questo servizio devi distribuire il progetto in almeno due dispositivi HoloLens.

Se ora compili e distribuisci il progetto Unity in due dispositivi HoloLens, puoi ottenere l'allineamento spaziale tra i dispositivi condividendo l'ID ancoraggio di Azure. Per provare, puoi seguire questa procedura:

1. Sul dispositivo HoloLens 1 - **Avvia l'applicazione** (è stata creata un'istanza di Rocket Launcher e posizionata sulla tabella)
2. Sul dispositivo HoloLens 2 - **Avvia l'applicazione** (entrambi gli utenti vedono la tabella con Rocket Launcher, ma la tabella non è visualizzata nella stessa posizione e gli avatar degli utenti non compaiono nella posizione reale degli utenti)
3. Sul dispositivo HoloLens 1 - Premi il pulsante **Start Azure Session** (Avvia sessione di Azure)
4. Sul dispositivo HoloLens 1 - Premi il pulsante **Create Azure Anchor** (Crea ancoraggio di Azure) (crea l'ancoraggio nella posizione dell'oggetto TableAnchor e archivia le informazioni relative all'ancoraggio nella risorsa di Azure).
5. Sul dispositivo HoloLens 1 - Premi il pulsante **Share Azure Anchor** (Condividi ancoraggio di Azure) (condivide l'ID ancoraggio con altri utenti in tempo reale)
6. Sul dispositivo HoloLens 2 - Premi il pulsante **Start Azure Session** (Avvia sessione di Azure)
7. Sul dispositivo HoloLens 2 - Premi il pulsante **Get Azure Anchor** (Ottieni ancoraggio di Azure) (si connette alla risorsa di Azure per recuperare le informazioni relative all'ancoraggio per l'ID ancoraggio condiviso e quindi sposta l'oggetto TableAnchor nella posizione in cui è stato creato l'ancoraggio con il dispositivo HoloLens 1)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come integrare il potente servizio Ancoraggi nello spazio di Azure per allineare i dispositivi in un'esperienza condivisa. Si conclude così la serie di esercitazioni in cui hai appreso come impostare un account e un'applicazione Photon, integrare Photon e PUN in un'applicazione Unity, configurare gli avatar degli utenti e gli oggetti condivisi e infine allineare più partecipanti con Ancoraggi nello spazio di Azure.
