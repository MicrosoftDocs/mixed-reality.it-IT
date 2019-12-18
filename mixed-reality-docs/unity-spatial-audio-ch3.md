---
title: Esercitazioni audio spaziali-3. Spatializing audio da un video
description: Importare un asset video nel progetto Unity e spatialize l'audio dal video.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182748"
---
# <a name="spatializing-audio-from-a-video"></a>Spatializing audio da un video
In questo terzo capitolo del modulo audio spaziale delle esercitazioni di HoloLens 2 Unity è possibile:
* Importare un video e aggiungere un lettore video
* Riprodurre il video su un quadrilatero
* Indirizzare l'audio dal video al quadrilatero e spatialize l'audio

## <a name="import-a-video-and-add-a-video-player"></a>Importare un video e aggiungere un lettore video

Trascinare un file video nel riquadro **progetto** del progetto Unity. È possibile utilizzare [questo video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) dal progetto di esempio di audio spaziale.

![Cartella asset con video](images/spatial-audio/assets-folder-with-video.png)

La regolazione delle impostazioni di qualità nel clip video può garantire la riproduzione uniforme in HoloLens 2. Fare clic sul file video nel riquadro **progetto** . Quindi, nel riquadro **Inspector** per il file video, sostituire le impostazioni per le app di Windows Store e:
* Abilita **transcodifica**
* Imposta **codec** su H264
* Impostare la **Modalità bitrate** su low
* Impostare la **qualità spaziale** su una qualità media spaziale

Dopo queste modifiche, il riquadro **Inspector** per il file video sarà simile al seguente:

![Riquadro proprietà video](images/spatial-audio/video-property-pane.png)

Successivamente, aggiungere un oggetto **lettore video** alla **gerarchia** facendo clic con il pulsante destro del mouse sul riquadro **gerarchia** e scegliendo **video-> lettore video**:

![Lettore video nella gerarchia](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>Riprodurre video su un quadrilatero
L'oggetto **Player video** necessita di un oggetto gioco con trama su cui eseguire il rendering del video. Per prima cosa, aggiungere un **Quad** alla **gerarchia** facendo clic con il pulsante destro del mouse sul riquadro **gerarchia** e scegliendo **oggetto 3D-> Quad**:

![Aggiungere Quad alla gerarchia](images/spatial-audio/add-quad-to-hierarchy.png)

Per assicurarsi che il **Quad** venga visualizzato davanti all'utente all'avvio dell'applicazione, impostare la proprietà **position** del **Quad** su (0, 0, 2) e la proprietà **scale** su (1,28, 0,72, 1). Una volta apportate queste modifiche, il componente **Transform** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:

![Trasformazione quad](images/spatial-audio/quad-transform.png)

Per creare una trama del **Quad** con video, creare una nuova **trama di rendering**. Nel riquadro **progetto** , fare clic con il pulsante destro del mouse e scegliere **Crea-> trama di rendering**:

![Crea trama di rendering](images/spatial-audio/create-render-texture.png)

Nel riquadro **Inspector** della trama di **rendering**impostare la proprietà **size** in modo che corrisponda alla risoluzione nativa del video 1280x720. Quindi, per garantire prestazioni di rendering ottimali in HoloLens 2, impostare la proprietà **depth buffer** su almeno **16 bit di profondità**. Dopo queste impostazioni, il riquadro **Inspector** per la **trama di rendering** sarà simile al seguente:

![Proprietà trama di rendering](images/spatial-audio/render-texture-properties.png)

Usare quindi la nuova **trama di rendering** come trama per il **Quad**:
1. Trascinare la **trama di rendering** dal riquadro **progetto** al **quadrato** della **gerarchia**
2. Per garantire prestazioni ottimali in HoloLens 2, nel riquadro **Inspector** per il **Quad**selezionare lo **shader standard del Toolkit di realtà mista**.

Con queste impostazioni, il componente **trama** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:

![Proprietà trama quad](images/spatial-audio/quad-texture-properties.png)

Per impostare il nuovo **lettore video** e il **rendering della trama** per riprodurre il clip video, aprire il riquadro **Inspector** per il **lettore video** e:
* Imposta la proprietà **video clip** sul file video
* Casella di controllo **ciclo**
* Imposta la **trama di destinazione** sulla nuova trama di rendering

Il riquadro **Inspector** per il **lettore video** sarà ora simile al seguente:

![Proprietà lettore video](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialize l'audio dal video
Nel riquadro **Inspector** per il **Quad**creare un' **origine audio** a cui indirizzare l'audio dal video:
* Fare clic su **Aggiungi componente** nella parte inferiore del riquadro
* Aggiungere un' **origine audio**

Quindi, nell' **origine audio**:
* Impostare l' **output** sul mixer
* Controllare la casella **Spatialize**
* Spostare il dispositivo di scorrimento di **Blend spaziale** su 1 (3D)

Una volta apportate queste modifiche, il componente di **origine audio** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:

![Controllo origine audio quad](images/spatial-audio/quad-audio-source-inspector.png)

Per impostare il **lettore video** in modo da instradare l'audio all' **origine audio** sul **Quad**, aprire il riquadro **Inspector** per il **lettore video** e:
* Impostare la **modalità di output audio** su' Audio source '
* Impostare la proprietà di **origine audio** sul quad

Dopo queste modifiche, il riquadro **Inspector** per il **lettore video** sarà simile al seguente:

![Origine audio del set di lettori video](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>Passaggi successivi
Provare l'app in un HoloLens 2 o nell'editor di Unity. Potrai visualizzare e ascoltare il video e l'audio del video sarà spaziali.

Continuare con il [capitolo 4](unity-spatial-audio-ch4.md) per usare il pulsante per abilitare e disabilitare la spazializzazione in fase di esecuzione.

