---
title: Esercitazioni su servizi vocali di Azure-3. Aggiunta del componente traduzione vocale di servizi cognitivi di Azure
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913205"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. aggiunta del componente traduzione vocale di servizi cognitivi di Azure

In questa esercitazione vengono fornite informazioni sul componente traduzione vocale dei servizi cognitivi di Azure nel progetto, oltre a tradurre in tre lingue diverse.

## <a name="instructions"></a>Istruzioni

1. Selezionare l'oggetto Lunarcom_Base nella gerarchia e fare clic su Aggiungi componente nel pannello di controllo. Cercare e selezionare Lunarcom Translation Recognizer.

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    Disabilitare il simulatore in modalità offline.

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >Prima di procedere, verificare che il simulatore in modalità offline sia disabilitato, come illustrato nell'immagine precedente, prima di testare il traduttore dell'SDK vocale. Per tradurre, è necessario essere connessi a Internet.

2. Fare clic sull'elenco a discesa nel riconoscimento Lunarcom translation e selezionare la lingua in cui si desidera tradurre.

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. A questo punto, eseguire l'applicazione e testare il convertitore facendo clic sul pulsante satellite e iniziare a pronunciare. Premere di nuovo il pulsante satellite per arrestare il riconoscimento. Di seguito è riportato un esempio di come dovrebbe apparire la scena. È possibile modificare la lingua nell'elenco a discesa "lingua di destinazione" (vedere l'immagine precedente) per esplorare la traduzione in altre lingue.

    Di seguito è riportato un esempio di come dovrebbe apparire la scena:

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Lezione completata

Il progetto può ora tradurre le parole che si parlano in diversi linguaggi. È possibile provare a usare le lingue e testare l'accuratezza della traduzione.

[Esercitazione successiva: 4. configurazione della finalità e della comprensione del linguaggio naturale](mrlearning-speechSDK-ch4.md)
