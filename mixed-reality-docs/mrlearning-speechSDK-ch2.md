---
title: Esercitazioni su servizi vocali di Azure-2. Aggiunta di una modalità offline per la traduzione vocale locale
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 5382a1cce38e8607042c21b8dd3157d1da2fa72e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437561"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. aggiunta di una modalità offline per la traduzione vocale locale

In questa esercitazione verrà aggiunta una modalità offline che consente di eseguire la traduzione vocale locale quando non è possibile connettersi al servizio di Azure. Si *simula* anche uno stato disconnesso.

## <a name="instructions"></a>Istruzioni

1. Consente di selezionare l'oggetto Lunarcom_Base nella gerarchia.
2. Fare clic su Aggiungi componente nel pannello di controllo. Cercare e selezionare il riconoscimento Lunarcom offline.

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. Fare clic sull'elenco a discesa in LunarcomOfflineRecognizer e selezionare abilitato. Questo programma consente di eseguire il progetto per agire come l'utente non dispone di una connessione. 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. Premere Riproduci nell'editor di Unity e testarlo. Premere il microfono nell'angolo in basso a sinistra della scena e iniziare a pronunciare. 

> [!NOTE]
> Poiché è offline, la funzionalità di riattivazione delle parole è stata disabilitata. È necessario fare clic fisicamente sul microfono ogni volta che si desidera che il riconoscimento vocale venga riconosciuto quando è offline. 

Di seguito è riportato un esempio di come potrebbe apparire la scena.

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>Lezione completata

La modalità offline è stata abilitata. A questo punto, quando si è offline, è possibile continuare a lavorare sul progetto con l'SDK di riconoscimento vocale. 


[Esercitazione successiva: 3. aggiunta del componente di traduzione vocale dei servizi cognitivi di Azure](mrlearning-speechSDK-ch3.md)

