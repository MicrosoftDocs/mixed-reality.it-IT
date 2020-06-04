---
title: Input vocale
description: Esercitazione sulla configurazione e l'uso dell'input vocale in HoloLens 2 e Unreal Engine
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Realtà mista di Windows, Unreal, Unreal Engine 4, UE4, HoloLens 2, Voice, input vocale, riconoscimento vocale, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330633"
---
# <a name="voice-input-in-unreal"></a>Input vocale in Unreal

## <a name="overview"></a>Panoramica
L'input vocale consente di interagire con un ologramma senza dover usare i movimenti della mano ed è supportato in HoloLens (1a generazione) e HoloLens 2. È alimentato dallo stesso motore che supporta la sintesi vocale in tutte le altre app di Windows universale e può aggiungere una sensazione naturale al modo in cui si interagisce in realtà mista. 

Le funzionalità vocali supportate includono:
- [Comando SELECT](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)
- [Salve, Cortana](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- "Vedere, Say it" per l'interazione di pulsanti e etichette
- Dettatura

Per altre informazioni, vedere la documentazione principale di [input vocale](voice-input.md) .

## <a name="enabling-speech-recognition"></a>Abilitazione del riconoscimento vocale

Per abilitare il riconoscimento vocale in HoloLens:
1. Selezionare **Impostazioni progetto > piattaforma > funzionalità di > HoloLens** e abilitare il **microfono**. 
2. Recogniztion vocale abilitato in **impostazioni > Privacy > vocale** e selezionare **inglese**.

> [!NOTE]
> Il riconoscimento vocale funziona sempre nella lingua di visualizzazione di Windows configurata nell'app **Impostazioni** . È inoltre consigliabile abilitare il **riconoscimento vocale online** per la qualità del servizio migliore.

![Impostazioni di riconoscimento vocale Windows](images/unreal/speech-recognition-settings.png)

3. Una finestra di dialogo viene visualizzata quando l'applicazione inizia per la prima volta a richiedere se si vuole abilitare il microfono. Se **si seleziona Sì** , viene avviato l'input vocale nell'app.

L'input vocale non richiede alcuna API della realtà mista di Windows speciale; si basa sull'API di mapping di [input](https://docs.unrealengine.com/Gameplay/Input/index.html) Unreal Engine 4 esistente. 

## <a name="adding-speech-mappings"></a>Aggiunta di mapping vocale
La connessione vocale all'azione è un passaggio importante quando si usa l'input vocale. Questi mapping monitorano l'app per le parole chiave vocali che un utente potrebbe pronunciare, quindi avviare un'azione collegata. È possibile trovare mapping vocale per:
1. Selezionare **modifica > impostazioni progetto**, scorrere fino alla sezione **motore** e fare clic su **input**.

Per aggiungere un nuovo mapping vocale per un comando Jump:
1. Fare clic sull' **+** icona accanto agli **elementi della matrice** e compilare i valori seguenti:
    * **jumpWord** per **nome azione**
    * **passa** alla **parola chiave Speech**

> [!NOTE]
> Tutte le parole o le frasi brevi possono essere utilizzate come parola chiave. 

![Setttings input motore UE4](images/unreal/engine-input.png)

I mapping vocale possono essere usati come componenti di input come mapping di azioni o assi o come nodi del progetto nel grafico eventi. Ad esempio, è possibile collegare il comando Jump per stampare due log diversi a seconda del momento in cui viene pronunciata la parola:

1. Fare doppio clic su un progetto per aprirlo nel **grafico eventi**.
2. **Fare clic con il pulsante destro del mouse** e cercare il **nome dell'azione** del mapping vocale (in questo caso **JumpWord**), quindi premere **invio**. In questo modo viene aggiunto un nodo **azione di input** al grafico.
3. Trascinare e rilasciare il pin **premuto** nel nodo della **stringa di stampa** come illustrato nell'immagine seguente. È possibile lasciare vuoto il pin **rilasciato** e non eseguire alcuna operazione per i mapping vocale.
 
![Azione semplice per la voce](images/unreal/voice-input-img-03.png)

4. Riprodurre l'app, ad indicare la parola **Jump** e guardare la console per stampare i log.

Questa è tutta la configurazione necessaria per iniziare ad aggiungere input voce alle app HoloLens in Unreal. Per altre informazioni sulla sintesi vocale e sull'interattività, vedere i collegamenti seguenti e assicurarsi di considerare l'esperienza che si sta creando per gli utenti.

## <a name="see-also"></a>Vedere anche
* [Sguardo e commit](gaze-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input MR 212: Voce](holograms-212.md)
