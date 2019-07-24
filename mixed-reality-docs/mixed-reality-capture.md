---
title: Acquisizione in realtà mista (MRC, Mixed Reality Capture)
description: Informazioni sull'uso dell'acquisizione di realtà mista.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: MRC, acquisizione di realtà mista, foto, video, fotocamera, acquisizione, utilizzo, flusso, Livestream, demo
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694498"
---
# <a name="mixed-reality-capture"></a>Acquisizione in realtà mista (MRC, Mixed Reality Capture)

HoloLens offre agli utenti l'esperienza di combinare il mondo reale con il mondo digitale. L'acquisizione di realtà mista (MRC) consente di acquisire l'esperienza come foto o video. Ciò consente di condividere l'esperienza con altri utenti, consentendo loro di visualizzare gli ologrammi mentre vengono visualizzati. Questi video e foto sono da un punto di vista della prima persona. Per un punto di vista di terze persone, usare [View spectator](spectator-view.md).

I casi di utilizzo per l'acquisizione di realtà mista vanno oltre la condivisione di video tra un cerchio sociale. I video possono essere usati per indicare ad altri utenti come usare un'app. Gli sviluppatori possono usare video o ancora per migliorare le fasi di ripetizione e l'esperienza di debug delle app.

## <a name="live-streaming-from-hololens"></a>Streaming live da HoloLens

L' [aggiornamento di Windows 10 ottobre 2018](release-notes-october-2018.md) aggiunge il supporto di Miracast a HoloLens. Selezionare il pulsante **Connetti** nella parte inferiore del menu Start per visualizzare una selezione per le schede e i dispositivi abilitati per Miracast. Selezionare il dispositivo in cui si vuole avviare lo streaming. Al termine, selezionare il pulsante **Disconnetti** nella parte inferiore del menu Start.  **Connessione** e **disconnessione** sono disponibili anche nel menu azioni rapide.

Il [portale](using-the-windows-device-portal.md) per dispositivi Windows e l' [app complementare Microsoft HoloLens](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) espongono le opzioni di streaming live per i dispositivi in modalità sviluppatore.

[Dynamics 365 Remote Assist](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist) supporta lo streaming live da HoloLens ai dipendenti in posizioni remote.

## <a name="taking-mixed-reality-captures"></a>Acquisizione di realtà miste

![Fare clic sull'icona della fotocamera nella parte inferiore del menu Start.](images/cameraiconinpins-300px.png)<br>
*Fare clic sull'icona della fotocamera nella parte inferiore del menu Start.*

Esistono diversi modi per avviare un'acquisizione di realtà mista:
* Cortana può essere usato in qualsiasi momento indipendentemente dall'app attualmente in esecuzione. Basta dire "Hey Cortana, Take a Picture" o "Hey Cortana, Start registration". Per arrestare un video, pronunciare "Hey Cortana, stop Registration".
* Nel menu Start selezionare **fotocamera** o **video**. Usare il [tocco aereo](gestures.md#air-tap) per aprire l'interfaccia utente della fotocamera MRC incorporata.
* Scegliere **fotocamera** o **video** dal menu azioni rapide per aprire l'interfaccia utente della fotocamera MRC incorporata.
* Le app sono in grado di esporre la propria interfaccia utente per l'acquisizione di realtà mista usando Custom o, a partire dall' [aggiornamento di Windows 10 ottobre 2018](release-notes-october-2018.md), l' [interfaccia utente predefinita della fotocamera MRC](mixed-reality-capture-for-developers.md).
* Univoco per HoloLens: 
    * Il [portale per dispositivi Windows](using-the-windows-device-portal.md) include una pagina di acquisizione di realtà mista che può essere usata per scattare foto, video, streaming live e acquisizioni di visualizzazioni.
    * Premere contemporaneamente i pulsanti **volume su** e **volume giù** per scattare un'immagine, indipendentemente dall'app attualmente in esecuzione.
    * Per avviare la registrazione di un video, mantenere i pulsanti **volume su** e **volume in basso** per tre secondi. Per arrestare un video, toccare contemporaneamente i pulsanti **volume su** e **volume giù** .
* Univoco per le cuffie immersive: 
    * Utilizzando un controller di movimento, premere il pulsante **Windows** e quindi toccare il **trigger** per scattare un'immagine. 
    * Utilizzando un controller di movimento, premere il pulsante **Windows** e quindi toccare il pulsante di **menu** per avviare la registrazione del video. Premere il pulsante **Windows** e quindi toccare il **trigger** per arrestare la registrazione del video.
    
>[!NOTE]
>L' [aggiornamento di Windows 10 ottobre 2018](release-notes-october-2018.md) modifica il comportamento di Bloom e Windows Button. Prima dell'aggiornamento, il movimento di Bloom o il pulsante di Windows arresterà la registrazione. Dopo l'aggiornamento, il movimento Bloom o il pulsante Windows apre il menu Start o il menu azioni rapide se ci si trova in un'app. Nel menu selezionare **Arresta video** per arrestare la registrazione.

### <a name="limitations-of-mixed-reality-capture"></a>Limitazioni dell'acquisizione di realtà mista

In HoloLens il sistema limiterà la velocità di rendering a 30Hz. Questa operazione crea una certa capacità per l'esecuzione di MRC, in modo che l'app non debba conservare una riserva di budget costante e corrisponda anche al framerate dei record video MRC di (fino a) 30 fps.

I video hanno una lunghezza massima di cinque minuti.

L'interfaccia utente della fotocamera MRC predefinita supporta solo una singola operazione di MRC alla volta (l'acquisizione di un'immagine si escludono a vicenda dalla registrazione di un video).

### <a name="file-formats"></a>Formati di file

Le acquisizioni di realtà miste dai comandi Cortana Voice e dagli strumenti del menu Start creano file nei formati seguenti:

|  type  |  Formato  |  Estensione  |  Risoluzione  |  Audio | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px (cuffie immersive) |  N/D | 
|  Video  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920x1080px a 30 fps (HoloLens 2)<br> 1216x684px in 24fps (HoloLens)<br> 1632x918px a 30 fps (cuffie immersive) |  Stereo a 48 kHz | 

>[!NOTE]
>La risoluzione di foto e video può essere inferiore se la fotocamera foto/video è già in uso da un'altra applicazione, durante lo streaming live o quando le risorse di sistema sono insufficienti.

### <a name="video-stabilization"></a>Stabilizzazione video

Per impostazione predefinita:
* La stabilizzazione video a latenza zero viene applicata quando si esegue lo streaming live su Miracast.
* La stabilizzazione video a latenza elevata viene applicata ai video acquisiti usando l'interfaccia utente della fotocamera MRC predefinita, i comandi Cortana Voice e il portale per dispositivi Windows.

## <a name="viewing-mixed-reality-captures"></a>Visualizzazione di acquisizioni di realtà miste

Le foto e i video di acquisizione della realtà mista vengono salvati nella cartella del dispositivo "fotocamera Roll". È possibile accedervi tramite l' [app Photos](see-your-photos.md#photos-app) o Esplora file.

In un PC connesso a HoloLens è anche possibile usare il [portale per dispositivi Windows](using-the-windows-device-portal.md#mixed-reality-capture) o Esplora file del PC ([tramite MTP](release-notes-april-2018.md#new-features-for-hololens)).

Se si installa l' [app OneDrive](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), è possibile attivare il **caricamento della fotocamera** e le foto e i video di MRC si sincronizzano con OneDrive e con gli altri dispositivi usando OneDrive.

>[!NOTE]
>A partire dall'aggiornamento di Windows 10 aprile 2018, l'app Photos non caricherà più le foto e i video in OneDrive.

## <a name="see-also"></a>Vedere anche
* [Visualizzazione spettatore](spectator-view.md)
* [Fotocamera individuabile](locatable-camera.md)
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)
* [Vedere le foto](see-your-photos.md)
* [Avviare il Portale di dispositivi di Windows](using-the-windows-device-portal.md)
