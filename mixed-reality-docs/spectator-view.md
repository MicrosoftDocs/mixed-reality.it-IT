---
title: Spectator View
description: Visualizzare gli ologrammi da un dispositivo esterno per mostrare un'esperienza di realtà mista su un display esterno o registrare un video di tale esperienza.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Camera, ARKit, HoloLens, Realtà mista, MixedRealityToolkit, demo, record
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491167"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Spectator View per HoloLens e HoloLens 2

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Panoramica

Quando indossiamo un dispositivo HoloLens, spesso dimentichiamo che le persone che non lo hanno non possono assistere alle cose straordinarie che possiamo vedere. Spectator View consente agli altri di visualizzare su uno schermo 2D ciò che un utente di HoloLens può vedere nel proprio mondo.
Questo strumento offre un approccio rapido e conveniente per registrare ologrammi in HD usando dispositivi mobili. Offre inoltre la possibilità di eseguire registrazioni degli ologrammi di qualità professionale con videocamere.

## <a name="key-resources"></a>Risorse principali

* [**Spectator View su GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Documentazione di Spectator View**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Esempi di Spectator View**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Casi d'uso
* Puoi registrare un'esperienza di realtà mista usando un iPhone o un dispositivo Android. Esegui una registrazione in Full HD e applica l'anti-aliasing agli ologrammi e persino le ombre. È un modo economico e rapido per acquisire video di ologrammi.
* Trasmetti in streaming le esperienze di realtà mista a un dispositivo Apple TV direttamente dal tuo iPhone o iPad, in tempo reale.
* Condividi l'esperienza con i tuoi ospiti: consenti alle persone che non hanno HoloLens di visualizzare gli ologrammi direttamente dai loro telefoni o tablet.

## <a name="current-features"></a>Funzionalità attualmente disponibili

* Sincronizzazione spaziale degli ologrammi, in modo che tutti possano visualizzare gli ologrammi esattamente nella stessa posizione.
* Supporto per iOS (dispositivi abilitati per ARKit) e Android (dispositivi abilitati per ARCore).
Più utenti guest iOS.
Registrazione di video + ologrammi + audio dell'ambiente + audio dell'ologramma.
Strumento di condivisione per poter salvare video, inviare un messaggio e-mail o condividere l'esperienza con altre app supportate.

![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)

La tabella seguente illustra le diverse funzionalità di Spectator View e le opzioni supportate. Scegli l'opzione più adatta alle tue esigenze di registrazione video:

|                                      | Dispositivi mobili                  |                    Videocamera              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualità HD                           |         Full HD         |        Registrazioni di qualità professionale (in base alla videocamera)      |
| Facilità di spostamento della videocamera                 |            ✔            |                      ✔                      |
| Visualizzazione di altre persone                    |            ✔            |                      ✔                      |
| Trasmissione in streaming su uno schermo           |            ✔            |                      ✔                      |
| Portabile                             |            ✔            |                                             |
| Wireless                             |            ✔            |                                             |
| Altri requisiti hardware         |     Telefono Android, iPhone    | HoloLens + attrezzatura + treppiede + videocamera + PC + Unity |
| Investimento hardware                  |           Bassa            |                     Alto                    |
| Multipiattaforma                       |           Android, iOS   |                                             |
| Contenuto sincronizzato                 |            ✔            |                      ✔                      |
| Durata di configurazione del runtime               |         Istantanea          |                     Lenta                    |
## <a name="see-also"></a>Vedi anche

* [Acquisizione realtà mista](mixed-reality-capture.md) 
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)
* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
