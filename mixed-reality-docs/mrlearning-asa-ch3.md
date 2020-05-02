---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 3. Visualizzazione del feedback su Ancoraggi nello spazio di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 11342bada65e963db6393d35c99e2c2fbffe8ff1
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031257"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Visualizzazione del feedback su Ancoraggi nello spazio di Azure

In questa esercitazione apprenderai come fornire agli utenti feedback su individuazione, eventi e stato degli ancoraggi con Ancoraggi nello spazio di Azure (ASA).

## <a name="objectives"></a>Obiettivi

* Imparare a configurare un riquadro dell'interfaccia utente in cui vengono visualizzate informazioni importanti sulla sessione ASA corrente
* Comprendere ed esplorare gli elementi di feedback che l'SDK di ASA mette a disposizione degli utenti

## <a name="set-up-asa-feedback-ui-panel"></a>Configurare il riquadro dell'interfaccia utente per il feedback ASA

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su **Instructions** > **TextContent** (Istruzioni > TextContent) e scegli **3D Object** > **Text - TextMeshPro** (Oggetto 3D > Testo - TextMeshPro) per creare un oggetto di testo TextMeshPro come elemento figlio di Instructions > TextContent (Istruzioni > TextContent) e assegnargli un nome appropriato, ad esempio **Feedback**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Per rendere più agevole l'uso della scena, disattiva la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità</a> per l'oggetto ParentAnchor facendo clic sull'icona a forma di occhio a sinistra dell'oggetto. In questo modo, l'oggetto viene nascosto nella finestra Scene (Scena) senza effetti sulla sua visibilità nel gioco.

Mantenendo l'oggetto **Feedback** selezionato, modifica le relative dimensioni e posizione nella finestra Inspector (Controllo), in modo che tale oggetto venga posizionato perfettamente sotto il testo dell'istruzione, ad esempio:

* Modifica il valore di **Pos Y** per Rect Transform (Trasformazione rettangolo) impostandolo su -0.24
* Modifica il valore di **Width** (Larghezza) per Rect Transform (Trasformazione rettangolo) impostandolo su 0.555
* Modifica il valore di **Height** (Altezza) per Rect Transform (Trasformazione rettangolo) impostandolo su 0.1

Scegli quindi le proprietà del tipo di carattere, in modo da adattare bene il testo all'interno dell'area di testo, ad esempio:

* Modifica il valore di **Font Style** (Stile carattere) per Text Mesh Pro (Script) impostandolo su Bold (Grassetto)
* Modifica il valore di **Font Size** (Dimensione carattere) per Text Mesh Pro (Script) impostandolo su 0.17
* Modifica il valore di **Alignment** (Allineamento) impostandolo su Center (Al centro) e Middle (In mezzo)

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Con l'oggetto **Feedback** ancora selezionato, nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Anchor Feedback Script (Script)** (Script di feedback Ancoraggi - Script) all'oggetto Feedback:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Assegna l'oggetto **Feedback** stesso al campo **Feedback Text** (Testo feedback) del componente **Anchor Feedback Script (Script)** (Script di feedback Ancoraggi - Script).

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come creare un riquadro dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di Ancoraggi nello spazio di Azure e fornire agli utenti feedback in tempo reale.
