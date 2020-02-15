---
title: Esercitazioni sugli ancoraggi spaziali di Azure-3. Visualizzazione del feedback di ancoraggio spaziale di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: f4f609a71b05a52e8761e282763a540b42e9f7f5
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250696"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Visualizzazione del feedback di ancoraggio spaziale di Azure

In questa esercitazione si apprenderà come fornire agli utenti feedback sull'individuazione, sugli eventi e sullo stato di ancoraggio quando si usano gli ancoraggi di Azure Spatial (ASA).

## <a name="objectives"></a>Obiettivi

* Informazioni su come configurare un pannello dell'interfaccia utente che visualizza informazioni importanti sulla sessione ASA corrente
* Comprendere ed esplorare gli elementi di feedback che l'SDK ASA rende disponibili agli utenti

## <a name="set-up-asa-feedback-ui-panel"></a>Configurare il pannello dell'interfaccia utente del feedback ASA

Nella finestra gerarchia, fare clic con il pulsante destro del mouse sulle **istruzioni** > oggetto **textContent** e selezionare **oggetto 3D** > **Text-TextMeshPro** per creare un oggetto di testo TextMeshPro come figlio delle istruzioni > oggetto TextContent e assegnargli un nome appropriato, ad esempio, **feedback**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Per semplificare l'uso della scena, impostare la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità della scena</a> per l'oggetto ParentAnchor su off facendo clic sull'icona a occhi a sinistra dell'oggetto. In questo modo, l'oggetto viene nascosto nella finestra della scena senza modificare la visibilità del gioco.

Con l'oggetto **feedback** ancora selezionato, nella finestra di controllo modificare la posizione e le dimensioni in modo che venga posizionato perfettamente sotto il testo dell'istruzione, ad esempio:

* Modificare la trasformazione Rect **pos Y** in-0,24
* Modificare la **larghezza** della trasformazione Rect in 0,555
* Modificare l' **altezza** di trasformazione Rect in 0,1

Quindi scegliere Proprietà carattere in modo che il testo si trovi perfettamente all'interno dell'area di testo, ad esempio:

* Modificare lo **stile del tipo di carattere** text mesh Pro (script) in grassetto
* Modificare le **dimensioni del tipo di carattere** text mesh Pro (script) in 0,17
* Modificare l' **allineamento** di Text mesh Pro (script) in centro e al centro

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Con l'oggetto **feedback** ancora selezionato, nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente script di **ancoraggio feedback (script)** all'oggetto feedback:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Assegnare l'oggetto **feedback** al campo **testo feedback** **dello script di ancoraggio (script)** del componente:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Complimenti

In questa esercitazione si è appreso come creare un pannello dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di ancoraggio spaziale di Azure per fornire agli utenti il feedback in tempo reale.
