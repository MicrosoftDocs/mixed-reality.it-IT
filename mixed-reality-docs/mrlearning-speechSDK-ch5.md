---
title: Modulo SpeechSDK di MR Learning-riconoscimento vocale e trascrizione
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: fc65dccfcbc181af0c0b321374c721797e120e5d
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460330"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a>Modulo di apprendimento vocale SDK-controllo lanciarazzi con comandi vocali

In questa lezione verrà usata la funzionalità finalità del servizio riconoscimento vocale di Azure per comprendere lo scopo del discorso. Per controllare l'utilità di avvio di Rocket verrà usato lo scopo di riconoscimento vocale rilevato. Durante questa lezione, verrà importato l'asset dell'utilità di avvio di Rocket, che verrà interfacciata nei pulsanti di controllo predefiniti per il controllo Rocket. 

## <a name="objectives"></a>Obiettivi

- Informazioni su come connettere la finalità vocale come comandi vocali.
- Informazioni su come usare i comandi vocali per finalità vocali come comandi di input di controllo Rocket.

## <a name="instructions"></a>Istruzioni
1. In questa esercitazione verrà usato un asset "BaseModule" per integrare Rocket Launcher con i comandi vocali. A tale proposito, è necessario importare l'asset nel progetto. È possibile scaricare l'asset "lanciarazzi" usando questo collegamento (collegamento al collegamento). 

2. Per importare l'asset, passare a Asset-> Importa pacchetto-> pacchetto personalizzato-> passare al file scaricato e fare clic su Importa.

![module4chapter5step1](images/module4chapter5step1.PNG)

3. Dopo aver importato l'asset di "lanciarazzi", spostarsi all'interno della cartella "Rocket Launcher"-> prefabbricates-> selezionare "Rocket Launcher_Complete", quindi trascinarlo e rilasciarlo nella gerarchia della scena esistente.

![module4chapter5step2](images/module4chapter5step2.PNG)

4. A questo punto è necessario integrare il "lanciarazzi lanciarazzi" con il progetto LUIS che abbiamo lavorato nella lezione precedente (collegamento per lesson4). A tale proposito, espandere il prefabbricato "Rocket Launcher_Complete" nella gerarchia e trovare i pulsanti "LaunchRoundButton", "ResetRoundButton" e "Placement Hints".

![module4chapter5step3](images/module4chapter5step3.PNG)

5. Selezionare "LaunchRoundButton" e nel pannello di controllo passare a "interactable" e in eventi "OnClick ()", trascinare il prefabbricato "LunarModule". Selezionare quindi la funzione a discesa e selezionare "LunarModule", quindi passare alla funzione "StartThruster ()" e selezionarla.

![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. Selezionare "ResetRoundButton" e nel pannello di controllo passare a "interactable" e in eventi "OnClick ()", trascinare il prefabbricato "LunarModule". Selezionare quindi la funzione a discesa e selezionare "LunarModule", quindi passare alla funzione "resetModule ()" e selezionarla.

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. Selezionare "hint di posizionamento" e nel pannello di controllo passare a "interactable" e in eventi "OnClick ()", trascinare il prefabbricato "LunarModule". Selezionare quindi la funzione a discesa e selezionare "LunarModule", quindi passare alla funzione "TogglePlacementHints" e selezionare ToggleGameOBjects ().

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  Selezionare quindi la prefabbricazione Lunarcom_Completed in Hierarchy e passare allo script "Lunarcom Intent Recognizer" in Inspector, quindi trascinare e rilasciare i pulsanti "LaunchRoundButton", "ResetRoundButton" e "hint di posizionamento" nelle rispettive posizioni.

![module4chapter5step4](images/module4chapter5step4.PNG)

9. Premere il pulsante Play nell'editor di Unity e fare clic sul pulsante "Rocket" e pronunciare le frasi come "push Rocket Launch Button" (Mostra un suggerimento di selezione host), "premere il pulsante Rest" o qualsiasi altra frase relativa alla richiesta di avvio, reimpostazione o suggerimento per l'utilità di avvio Rocket.

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a>Lezione completata

In questa lezione si è appreso come connettere i comandi vocali basati su intelligenza artificiale ai comandi vocali per usarli come metodo di input. Ora il programma può usare i relatori Intent come comandi vocali per fornire input per il lanciarazzi.

