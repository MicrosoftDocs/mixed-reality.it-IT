---
title: Esercitazioni sui servizi vocali di Azure - 2. Aggiunta di una modalità offline per la traduzione locale da voce a testo
description: Completa questo corso per imparare a implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7a0fa915a80763300eff470e29356034d6a0f841
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303672"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a>2. Uso del riconoscimento vocale per l'esecuzione di comandi

In questa esercitazione aggiungerai la possibilità di eseguire comandi con il riconoscimento vocale di Azure, che consentirà di eseguire un evento in base alla parola o alla frase definita.

## <a name="objectives"></a>Obiettivi

* Imparare a usare il riconoscimento vocale di Azure per eseguire comandi

## <a name="instructions"></a>Istruzioni

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Wake Word Recognizer (Script)** (Riconoscimento parola di attivazione Lunarcom - Script) all'oggetto Lunarcom e configuralo come indicato di seguito:

* Nel campo **Wake Word** (Parola di attivazione) immetti una frase appropriata, ad esempio _Activate Terminal_.
* Nel campo **Dismiss Word** (Parola di eliminazione) immetti una frase appropriata, ad esempio _Dismiss Terminal_.

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Il componente Lunarcom Wake Word Recognizer (Script) (Riconoscimento parola di attivazione Lunarcom - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

Se ora attivi la modalità gioco, come nell'esercitazione precedente, il pannello del terminale viene abilitato per impostazione predefinita. Tuttavia, puoi ora disabilitarlo pronunciando la parola di eliminazione **Dismiss terminal**:

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

Puoi anche riabilitarlo pronunciando la parola di attivazione **Activate terminal**:

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.

> [!TIP]
> Se si prevede di non essere spesso in grado di connettersi ad Azure, è possibile implementare i comandi vocali anche con MRTK seguendo le istruzioni contenute in [Uso dei comandi vocali](mr-learning-base-09.md).

## <a name="congratulations"></a>Lezione completata

Hai implementato i comandi vocali basati su Azure. Esegui l'applicazione nel dispositivo per verificare che la funzionalità venga eseguita correttamente.

Nell'esercitazione successiva apprenderai come tradurre il parlato con la traduzione vocale di Azure.

[Esercitazione successiva: 3. Aggiunta del componente di traduzione vocale di Servizi cognitivi di Azure](mrlearning-speechSDK-ch3.md)
