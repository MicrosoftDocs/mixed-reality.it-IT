---
title: Esercitazioni audio spaziali-2. Suoni interazione pulsante Spatializing
description: Aggiungere un pulsante al progetto e spatialize i suoni di interazione dei pulsanti.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale
ms.openlocfilehash: bd70e3bc88ee39b2c6257089ac3a2b93dfae0ad1
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182778"
---
# <a name="spatializing-button-interaction-sounds"></a>Suoni interazione pulsante Spatializing

## <a name="objectives"></a>Obiettivi
In questo secondo capitolo del modulo audio spaziale delle esercitazioni di HoloLens 2 è possibile:
* Aggiungere un pulsante
* Spatialize i suoni dei clic del pulsante

## <a name="add-a-button"></a>Aggiungere un pulsante
Nel riquadro **progetto** selezionare **Asset** e digitare "PressableButtonHoloLens2" nella barra di ricerca:

![Prefabbricato Button negli asset](images/spatial-audio/button-prefab-in-assets.png)

Il prefabbricato del pulsante è la voce rappresentata da un'icona blu, anziché da un'icona bianca. Trascinare il prefabbricato denominato **PressableButtonHoloLens2** nel riquadro **gerarchia** . Nel riquadro **Inspector** del pulsante nuovo impostare la proprietà **position** su (0,-0,4, 2) in modo che venga visualizzata davanti all'utente all'avvio dell'applicazione. Il componente **Transform** del pulsante sarà simile al seguente:

![Trasformazione pulsante](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a>Commenti e suggerimenti sul pulsante Spatialize
In questo passaggio si spatialize il feedback audio per il pulsante. Per suggerimenti sulla progettazione correlati, vedere [progettazione di suoni spaziali](spatial-sound-design.md). 

Il riquadro **mixer audio** è il punto in cui definire le destinazioni, denominate **gruppi di mixer**, per la riproduzione audio dai componenti di **origine audio** . 
* Aprire il riquadro **mixer audio** dalla barra dei menu usando la **finestra > audio-> Audio Mixer**
* Per creare un **mixer** , fare clic su "+" accanto a **mixer**. Il nuovo mixer includerà un **gruppo** predefinito denominato **Master**.

Il riquadro del **mixer** sarà ora simile al seguente:

![Pannello mixer con primo mixer](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> Fino a quando non viene abilitato il riverbero nel [capitolo 5](unity-spatial-audio-ch5.md), il contatore del volume del mixer non Mostra l'attività per i suoni riprodotti tramite Microsoft Spatializer

Fare clic su **PressableButtonHoloLens2** nel riquadro **gerarchia** . Nel riquadro **Inspector** :
1. Trovare il componente di **origine audio**
2. Per la proprietà **output** , fare clic sul selettore e scegliere il mixer
3. Selezionare la casella di controllo **Spatialize**
4. Spostare il dispositivo di scorrimento **Blend spaziale** su 3D (1).

> [!NOTE]
> Nelle versioni di Unity precedenti alla 2019, la casella di controllo ' Spatialize ' si trova nella parte inferiore del riquadro **Inspector** per l' **origine audio**.

Dopo queste modifiche, il componente di **origine audio** del **PressableButtonHoloLens2** sarà simile al seguente:

![Origine audio pulsante](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> Se si sposta **Blend spaziale** in 1 (3D) senza selezionare la casella di controllo **Spatialize** , Unity utilizzerà il relativo Spatializer di panoramica anziché **Microsoft Spatializer** con HRTFs.

## <a name="adjust-the-volume-curve"></a>Modificare la curva del volume
Per impostazione predefinita, Unity attenua i suoni spaziali Man mano che si ottengono più lontano dal listener. Quando questa attenuazione viene applicata ai suoni di feedback interazione, l'interfaccia può diventare più difficile da usare.

Per disabilitare questa attenuazione, modificare la curva del **volume** . Nel componente **origine audio** del riquadro **Inspector** per **PressableButtonHoloLens2**è presente una sezione denominata **impostazioni audio 3D**. In questa sezione:
1. Impostare la proprietà **volume attenuazione** su Linear
2. Trascinare l'endpoint sulla curva del **volume** (la curva rossa) da' 0' sull'asse y fino a' 1'
3. Per regolare la forma della curva del **volume** in modo che sia piatta, trascinare il controllo forma curva bianca in modo che sia parallelo all'asse X

Una volta apportate queste modifiche, la sezione **impostazioni audio 3D** delle proprietà di **origine audio** del **PressableButtonHoloLens2** sarà simile alla seguente:

![Impostazioni suono 3D pulsante](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a>Passaggi successivi

Provare l'app in un HoloLens 2 o nell'editor di Unity. Nell'app è possibile toccare il pulsante e sentire i suoni di interazione dei pulsanti spaziali.

Quando si esegue il test nell'editor di Unity, premere la barra spaziatrice e scorrere con la rotellina di scorrimento per attivare la simulazione manuale. Per ulteriori informazioni, vedere la [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).

Continuare con il [capitolo 3](unity-spatial-audio-ch3.md) per aggiungere un video all'app e spatialize l'audio dal video.

