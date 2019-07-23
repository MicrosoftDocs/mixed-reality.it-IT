---
title: Visualizzazione Spectator
description: Visualizza gli ologrammi da un dispositivo esterno come mezzo per dimostrare un'esperienza di realtà mista su una visualizzazione esterna o la registrazione di un video di un'esperienza di realtà mista.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Visualizzazione Spectator, iPhone, iOS, iPad, OpenCV, fotocamera, ARKit, HoloLens, realtà mista, MixedRealityToolkit, demo, record
ms.openlocfilehash: 135a566456f1000669d2033edcf0d0b4649ccdf3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387671"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Visualizzazione spectator per HoloLens e HoloLens 2

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Panoramica

Quando si usa un HoloLens, spesso si dimentica che una persona che non lo dispone di non è in grado di sperimentare le meraviglie che possiamo. La visualizzazione spectator consente ad altri utenti di visualizzare in una schermata 2D ciò che un utente HoloLens vede nel proprio mondo.
La visualizzazione spectator offre un approccio rapido e conveniente per la registrazione di ologrammi in HD con dispositivi mobili. Offre anche una registrazione di qualità professionale degli ologrammi con le videocamere.

## <a name="key-resources"></a>Risorse chiave

* [**Visualizzazione spectator su GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Architettura**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [**Campioni**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [**Istruzioni per la configurazione di dispositivi mobili**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [**Istruzioni di configurazione della fotocamera video**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.VideoCamera.md)

## <a name="use-cases"></a>Casi d'uso
* È possibile registrare un'esperienza di realtà mista usando un dispositivo iPhone o Android. Registra in Full HD e applica l'anti-aliasing a ologrammi e anche ombre. Si tratta di un modo economico e rapido per acquisire video di ologrammi.
* Trasmetti Live Live mixed Experience a un Apple TV direttamente da iPhone o iPad, senza ritardo.
* Condividi la tua esperienza con i guest: Consentire agli utenti non HoloLens di provare gli ologrammi direttamente dai loro telefoni o tablet.

## <a name="current-features"></a>Funzionalità correnti

* La sincronizzazione spaziale degli ologrammi consente a tutti di visualizzare gli ologrammi nello stesso punto.
* supporto per iOS (dispositivi abilitati per ARKit) e Android (dispositivi abilitati per ARCore).
Più Guest iOS.
Registrazione di video e ologrammi + suono ambiente + suono ologramma.
Condividi il foglio per poter salvare video, inviare un messaggio di posta elettronica o condividere con altre app di supporto.

![](images/SpecViewPhoneDemo.jpg)
![Marcatoremarcatoremarcatore](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)

La tabella seguente illustra le diverse funzionalità di visualizzazione Spectator e le rispettive funzionalità. Scegliere l'opzione più adatta alle proprie esigenze di registrazione video:

|                                      | Cellulare                  |                    Videocamera              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualità HD                           |         Full HD         |        Film di qualità professionale (come determinato dalla videocamera video)      |
| Spostamento della fotocamera semplice                 |            ✔            |                      ✔                      |
| Visualizzazione di terze persone                    |            ✔            |                      ✔                      |
| Può essere trasmesso a schermate           |            ✔            |                      ✔                      |
| Portabile                             |            ✔            |                                             |
| Wireless                             |            ✔            |                                             |
| Hardware aggiuntivo necessario         |     Telefono Android, iPhone    | HoloLens + rig + treppiede + videocamera video + PC + Unity |
| Investimenti hardware                  |           Basso            |                     Alto                    |
| Multipiattaforma                       |           Android, iOS   |                                             |
| Contenuto sincronizzato                 |            ✔            |                      ✔                      |
| Durata configurazione Runtime               |         Istante          |                     Lento                    |
## <a name="see-also"></a>Vedere anche

* [Acquisizione realtà mista](mixed-reality-capture.md) 
* [Acquisizione realtà mista per sviluppatori](mixed-reality-capture-for-developers.md)
* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
