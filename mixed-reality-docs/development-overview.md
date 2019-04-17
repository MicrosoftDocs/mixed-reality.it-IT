---
title: Cenni preliminari sullo sviluppo
description: Questo articolo illustra i concetti fondamentali dello sviluppo di un'app per realtà mista di Windows.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: recupero started, nozioni di base, HoloLens, 2, HoloLens visore VR immersivi, unity, visual studio
ms.openlocfilehash: 1d23e458477cc23252ccd4c44f67c400aa356965
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605110"
---
# <a name="development-overview"></a>Cenni preliminari sullo sviluppo

È possibile sviluppare app di realtà mista tramite un'ampia gamma di tecnologie per sviluppatori.  HoloLens esegue le app che vengono compilate con il [Universal Windows Platform](https://dev.windows.com/getstarted).  Eseguire le app Universal Windows Platform, nonché applicazioni Win32 auricolari coinvolgente e concreto.
Ottenendo familiarità con gli strumenti di middleware, ad esempio Unity, è possibile avviare compilazione odierna esperienze di realtà mista.  Open source di sfruttare [Toolkit di realtà mista](install-the-tools.md) per essere subito operativi.
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Servizi di realtà mista</a>, ad esempio <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Anchor spaziali Azure</a>, dispongono di SDK che consente di integrare diverse tecnologie per sviluppatori multipiattaforma anche.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Nozioni di base dello sviluppo di realtà mista

[Realtà mista](mixed-reality.md) esperienze sono abilitate per nuove funzionalità di Windows per la comprensione dell'ambiente. Questi consentono agli sviluppatori di inserire un [ologrammi](hologram.md) nel mondo reale, e consentire agli utenti di spostarsi tra i mondi digitali scorrendo letteralmente su. 

Questi sono i blocchi predefiniti di base per lo sviluppo della realtà mista:

<table>
<tr>
<th>Input</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> <a href="gaze.md">Head sguardo</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Sguardo sotto controllo</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Le mani / <a href="gestures.md">movimenti</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voce</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Controller di movimento</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Percezione e nuove funzionalità spaziali</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Coordinate complessive</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Spaziale audio</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Mapping spaziale</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



Il modello di interazione di base per [HoloLens](hololens-hardware-details.md) viene [estasiati](gaze.md), [movimento](gestures.md), e [vocali](voice-input.md), talvolta detta *GGV* . [Auricolari coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) inoltre utilizzare sguardo e vocali, ma lo scambio [movimento controller](motion-controllers.md) per movimenti.


Tutti i dispositivi basati su Windows realtà mista trarre vantaggio dall'ecosistema di input disponibile per Windows, inclusi mouse, tastiera, gamepad e altro ancora. Con, HoloLens [accessori hardware](hardware-accessories.md) sono connessi tramite Bluetooth. Con auricolari coinvolgenti, accessori connettersi al PC host tramite Bluetooth, USB e altri protocolli supportati.

La funzionalità di comprensione dell'ambiente, ad esempio [coordinate](coordinate-systems.md), [spaziale audio](spatial-sound.md), e [mapping spaziale](spatial-mapping.md) forniscono le funzionalità necessarie per la combinazione di realtà. Mapping spaziale è univoco per HoloLens e Abilita vntana interagire con l'utente sia il mondo fisico. Sistemi di coordinate consentire lo spostamento dell'utente influire sul movimento del mondo digitale.

[Ologrammi](hologram.md) sono costituite chiaro e audio, che si affidano [rendering holographic](rendering.md). Comprendere l'esperienza di selezione host e la persistenza, come illustrato nel [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) (operazione talvolta denominata "shell") è un ottimo modo a terra nell'esperienza dell'utente.

## <a name="tools-for-developing-for-mixed-reality"></a>Strumenti per lo sviluppo per realtà mista

Gli strumenti che usi varia in base il [stile di visualizzazione dell'app](app-views.md) da compilare.
* [Le app con una visualizzazione 2D](building-2d-apps.md) sfrutta gli strumenti per la creazione di App Universal Windows Platform adatti per gli ambienti, ad esempio Windows Phone, PC e Tablet. Queste App sono principalmente come proiezioni 2D inserite nella home di realtà mista di Windows e possono funzionare in più tipi di dispositivo (inclusi PC e telefono).
* App coinvolgenti e holographic necessario gli strumenti progettati per sfruttare le API di realtà mista di Windows. Abbiamo [consiglia di usare Unity](unity-development-overview.md) per compilare le App per realtà mista. Gli sviluppatori interessati alla creazione di proprio motore possono [utilizzano DirectX e altre API Windows](directx-development-overview.md).

Indipendentemente dal tipo di app che tu stia creando, questi strumenti faciliterà l'esperienza di sviluppo di app:
* [Visual Studio e il Windows SDK](using-visual-studio.md)
* [Portale di dispositivi di Windows](using-the-windows-device-portal.md)
* [HoloLens emulatore](using-the-hololens-emulator.md) (emulatore HoloLens 2 presto disponibile)
* [Simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md)
* [Criteri di qualità delle App](app-quality-criteria.md)

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Servizi di realtà mista</a>
* [Esercitazioni di realtà miste](academy.md)
* [Progetti open source](open-source-projects.md)
* [Nozioni fondamentali di MR 100: Introduzione a Unity](holograms-100.md)
* [Realtà mista di Windows minimo PC compatibilità alle linee guida hardware](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Invio di un'app di Windows Store](submitting-an-app-to-the-microsoft-store.md)
