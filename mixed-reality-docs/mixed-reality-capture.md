---
title: Acquisizione in realtà mista (MRC, Mixed Reality Capture)
description: Informazioni sull'uso di acquisizione di realtà mista.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: MRC, mista acquisizione realtà, foto, video, fotocamera, acquisizione, utilizzo, flusso, streaming Live, demo
ms.openlocfilehash: 18a80083bd25974905874c6c2ec0de87dc7424ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604139"
---
# <a name="mixed-reality-capture"></a>Acquisizione in realtà mista (MRC, Mixed Reality Capture)

HoloLens offre agli utenti l'esperienza di combinare il mondo reale con il mondo digitale. Acquisizione di realtà mista (MRC) consentono di acquisire tale esperienza come una foto o video. Ciò consente di condividere l'esperienza con altri utenti consentendo loro di vedere il vntana così come vengono visualizzati. Tale video e foto sono dal punto di vista della prima persona. Per un punto di vista di terza persona, usare [vista spectator](spectator-view.md).

Casi d'uso per l'acquisizione di realtà mista va oltre la condivisione di video tra un cerchio basati su social network. I video possono essere usati per indicare ad altri utenti su come usare un'app. Gli sviluppatori possono utilizzare i video o continua a migliorare passaggi ripetizione bug e il debug di app che offrono esperienze.

## <a name="live-streaming-from-hololens"></a>Live streaming di HoloLens

Il [Windows 10 ottobre 2018 Update](release-notes-october-2018.md) aggiunge supporto per Miracast per HoloLens. Selezionare il **Connect** nella parte inferiore del menu Start per visualizzare un controllo di selezione per dispositivi abilitati per Miracast e schede. Selezionare il dispositivo a cui si desidera iniziare lo streaming. Al termine, selezionare la **Disconnect** nella parte inferiore del menu Start.  **Connettere** e **Disconnect** sono disponibili anche nel menu Azioni rapide. 

Il [Windows Device Portal](using-the-windows-device-portal.md) espone live streaming opzioni per i dispositivi che sono in modalità sviluppatore.

## <a name="taking-mixed-reality-captures"></a>Prendendo di realtà mista consente di acquisire

![Fai clic sull'icona della telecamera nella parte inferiore del menu Start](images/cameraiconinpins-300px.png)<br>
*Fai clic sull'icona della telecamera nella parte inferiore del menu Start*

Esistono diversi modi per avviare un'acquisizione di realtà mista:
* Cortana può essere usata in tutte le volte indipendentemente dall'app attualmente in esecuzione. È sufficiente "Ehi Cortana, acquisire un'immagine" o "Ehi Cortana, avviare la registrazione." Per arrestare un video, pronunciare "Ehi Cortana, arrestare la registrazione."
* Nel menu Start, selezionare **fotocamera** oppure **Video**. Uso [puntato](gestures.md#air-tap) per aprire la fotocamera MRC predefinita dell'interfaccia utente.
* Nel menu Azioni rapide, selezionare **fotocamera** oppure **Video** per aprire la fotocamera MRC predefinita dell'interfaccia utente.
* Le app sono in grado di esporre la propria interfaccia utente per l'acquisizione di realtà mista tramite personalizzato o, a partire il [Windows 10 ottobre 2018 Update](release-notes-october-2018.md), [interfaccia utente della fotocamera MRC incorporati](mixed-reality-capture-for-developers.md).
* Univoco per HoloLens: 
    * [Windows Device Portal](using-the-windows-device-portal.md) dispone di una pagina di acquisizione di realtà mista che può essere usata per eseguire foto, video, streaming live e visualizzare le acquisizioni.
    * Premere sia la **aumento volume** e **riduzione volume** pulsanti contemporaneamente per scattare una foto, indipendentemente dall'app attualmente in esecuzione.
    * Tenere premuto il **aumento volume** e **riduzione volume** pulsanti per tre secondi avviare la registrazione di un video. Per arrestare un video, toccare **aumento volume** e **riduzione volume** pulsanti contemporaneamente.
* Univoco per immersive auricolari: 
    * Utilizzando un controller di movimento, tenere premuto il **Windows** pulsante e quindi toccare il **trigger** per scattare una foto. 
    * Utilizzando un controller di movimento, tenere premuto il **Windows** pulsante e quindi toccare il **menu** per avviare la registrazione di video. Tenere premuto il **Windows** pulsante e quindi toccare il **trigger** per interrompere la registrazione video.
    
>[!NOTE]
>Il [Windows 10 ottobre 2018 Update](release-notes-october-2018.md) cambia modalità di comportamento bloom e pulsante di Windows. Prima dell'aggiornamento, il movimento bloom o pulsante di Windows potrebbe interrompere la registrazione. Dopo l'aggiornamento, il movimento bloom o con il pulsante Windows apre il menu di avvio (o il menu Azioni rapide in presenza di un'app). Nel menu, selezionare **Stop video** per arrestare la registrazione.

### <a name="limitations-of-mixed-reality-capture"></a>Limitazioni dell'acquisizione di realtà mista

Su HoloLens, il sistema limiterà la velocità di rendering per il 30Hz. Questo consente di creare alcune capacità aggiuntiva per MRC di eseguire l'app non è necessario mantenere una riserva di budget costante e corrisponde anche la frequenza dei fotogrammi video record MRC di 30fps.

Video di avere una lunghezza massima di cinque minuti.

La fotocamera MRC predefinita dell'interfaccia utente supporta solo una singola operazione MRC alla volta (un'immagine si escludono a vicenda dalla registrazione di un video).

### <a name="file-formats"></a>Formati di file

Realtà mista consente di acquisire da comandi vocali Cortana e Menu Start strumenti creano i file nei formati seguenti:

|  Tipo  |  Formato  |  Estensione  |  Risoluzione  |  Audio | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  1408x792px 1920x1080 px (HoloLens) (auricolari coinvolgente e concreto) |  N/D | 
|  Video  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1408x792px 1632x918px (HoloLens) (auricolari coinvolgente e concreto) |  48kHz Stereo | 

## <a name="viewing-mixed-reality-captures"></a>Visualizzazione di realtà mista consente di acquisire

Realtà mista acquisizione foto e video vengono salvati nella cartella "Rullino della fotocamera" del dispositivo. È possibile accedervi tramite il [app foto](see-your-photos.md#photos-app) o Esplora File.

In un PC connesso a HoloLens, è anche possibile usare [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture) risorse o Esplora File del PC ([tramite MTP](release-notes-april-2018.md#new-features-for-hololens)).

Se si installa il [app OneDrive](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), è possibile attivare **caricamento della fotocamera,** e MRC foto e video verranno sincronizzate con OneDrive e altri dispositivi l'uso di OneDrive.

>[!NOTE]
>A partire da Windows 10 April 2018 Update, l'app foto non sono più caricherà le tue foto e video in OneDrive.

## <a name="see-also"></a>Vedere anche
* [Visualizzazione spectator](spectator-view.md)
* [Fotocamera individuabile](locatable-camera.md)
* [Mista acquisizione realtà per gli sviluppatori](mixed-reality-capture-for-developers.md)
* [Vedere le foto](see-your-photos.md)
* [Utilizzando il Windows Device Portal](using-the-windows-device-portal.md)
