---
title: Modulo SpeechSDK di MR Learning-riconoscimento vocale e trascrizione
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: e5d0919a69c9e6b0c4233d23bf6d370f3def6576
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460317"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a>3.    Aggiunta del componente traduzione vocale di servizi cognitivi di Azure

Questa esercitazione illustra come aabout il componente traduzione vocale dei servizi cognitivi di Azure nel progetto e come tradurre in tre lingue diverse. 

1. Selezionare l'oggetto Lunarcom_Base nella gerarchia e fare clic su Aggiungi componente nel pannello di controllo. Cercare e selezionare LunarcomTranslationRecognizer.

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> Nota: Verificare che il simulatore in modalità offline sia disabilitato prima di testare il traduttore dell'SDK vocale. Per tradurre, è necessario essere connessi a Internet. Vedere l'immagine seguente su dove trovare questa impostazione. 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. Fare clic sull'elenco a discesa in LunarcomTranslationRecognizer e selezionare la lingua in cui si desidera tradurre.

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. A questo punto, eseguire l'applicazione e testare il convertitore facendo clic sul pulsante satellite e iniziare a pronunciare. Premere di nuovo il pulsante satellite per arrestare il riconoscimento. Di seguito è riportato un esempio di come dovrebbe apparire la scena. È possibile modificare la lingua nell'elenco a discesa "lingua di destinazione" (vedere l'immagine precedente) per esplorare la traduzione in altre lingue.

> Nota: Prima di eseguire il test, verificare che il simulatore offline sia disabilitato, come illustrato nell'immagine seguente.
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

Di seguito è riportato un esempio di come dovrebbe apparire la scena:

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Lezione completata

Il progetto può ora tradurre le parole che si parlano in diversi linguaggi. È possibile provare a usare le lingue e testare l'accuratezza della traduzione. 

[Esercitazione successiva: 4.  Configurazione di finalità e comprensione del linguaggio naturale](mrlearning-speechSDK-ch4.md)

