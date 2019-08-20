---
title: Panoramica sullo sviluppo
description: Questo articolo descrive i blocchi predefiniti di base per lo sviluppo di un'app di realtà mista di Windows.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: Introduzione, nozioni di base, HoloLens, HoloLens 2, auricolare immersivo, Unity, Visual Studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873981"
---
# <a name="development-overview"></a>Panoramica sullo sviluppo

È possibile sviluppare app per la realtà mista usando un'ampia gamma di tecnologie per sviluppatori.  HoloLens esegue le app compilate con il [piattaforma UWP (Universal Windows Platform)](https://dev.windows.com/getstarted).  Gli auricolari immersivi eseguono app piattaforma UWP (Universal Windows Platform) e applicazioni Win32.
Grazie alla familiarità con gli strumenti middleware come Unity, è possibile iniziare subito a creare esperienze di realtà miste.  Sfrutta il [Toolkit di realtà mista](install-the-tools.md) open source per iniziare rapidamente.
I <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">servizi di realtà mista</a>, ad esempio gli <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">ancoraggi spaziali di Azure</a>, dispongono di SDK che possono integrarsi in diverse tecnologie di sviluppo multipiattaforma.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Nozioni di base sullo sviluppo della realtà mista

Le nuove funzionalità di Windows per la conoscenza ambientale offrono la possibilità di realizzare esperienze di [realtà mista](mixed-reality.md). Con queste funzionalità, gli sviluppatori possono posizionare un [ologramma](hologram.md) nel mondo reale e consentire agli utenti di spostarsi attraverso i mondi digitali letteralmente con i propri passi. 

Ecco i componenti di base per lo sviluppo della realtà mista:

<table>
<tr>
<th>Input</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (prima generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> <a href="gaze.md">Puntamento con la testa</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Tracciamento oculare</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Mani/ <a href="gestures.md">movimenti</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voce</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Game pad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Controller del movimento</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Percezione e funzionalità spaziali</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (prima generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Coordinate globali</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Audio spaziale</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Mapping spaziale</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



Il modello di interazione di base per [HoloLens](hololens-hardware-details.md) è costituito dalla [direzione dello sguardo](gaze.md), dai [movimenti](gestures.md) e dai [comandi vocali](voice-input.md) ed è talvolta identificato dall'acronimo *GGV (Gaze, Gesture, Voice)* . Anche i [visori VR immersive di Windows Mixed Reality](immersive-headset-hardware-details.md) usano lo sguardo e la voce, ma sostituiscono ai movimenti i [controller del movimento](motion-controllers.md).


Tutti i dispositivi con realtà mista basate su Windows traggono vantaggio dall'ecosistema di input disponibile per Windows, tra cui mouse, tastiera, gamepad e altro ancora. Con HoloLens, gli [accessori hardware](hardware-accessories.md) sono connessi tramite Bluetooth. Con i visori VR immersive, gli accessori si connettono al PC host tramite Bluetooth, USB e altri protocolli supportati.

Le funzionalità per la conoscenza ambientale, come le [coordinate](coordinate-systems.md), l'[audio spaziale](spatial-sound.md) e il [mapping spaziale](spatial-mapping.md) offrono strumenti indispensabili per la realtà mista. Il mapping spaziale è una funzionalità esclusiva di HoloLens e consente agli ologrammi di interagire con l'utente e il mondo fisico circostante. I sistemi di coordinate consentono ai movimenti dell'utente di influire sui movimenti nel mondo digitale.

Gli [ologrammi](hologram.md) sono costituiti da luci e suoni, che si basano sul [rendering olografico](rendering.md). La comprensione dell'esperienza di posizionamento e persistenza, come illustrata nello [spazio iniziale di Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md), talvolta definito "shell", offre un ottimo modo per basare lo sviluppo di app sull'esperienza dell'utente.

## <a name="tools-for-developing-for-mixed-reality"></a>Strumenti di sviluppo per la realtà mista

Gli strumenti da usare dipendono dallo [stile dell'app](app-views.md) che vuoi creare.
* Le [app con visualizzazione 2D](building-2d-apps.md) sfruttano gli strumenti per la creazione di app Universal Windows Platform, adatte per ambienti come Windows Phone, PC e tablet. Queste app vengono vissute come proiezioni 2D inserite nello spazio iniziale di Windows Mixed Reality e possono funzionare su più tipi di dispositivi, inclusi PC e smartphone.
* Le app coinvolgenti e olografiche richiedono strumenti progettati in modo da sfruttare le API di Windows Mixed Reality. Per creare app di realtà mista ti [consigliamo di usare Unity](unity-development-overview.md). Gli sviluppatori interessati a creare un motore personalizzato possono [usare DirectX e altre API Windows](directx-development-overview.md).

Indipendentemente dal tipo di app che stai creando, questi strumenti faciliteranno la tua esperienza di sviluppo:
* [Visual Studio e Windows SDK](using-visual-studio.md)
* [Portale di dispositivi di Windows](using-the-windows-device-portal.md)
* [Emulatore di HoloLens](using-the-hololens-emulator.md) (L'emulatore HoloLens 2 sarà presto disponibile)
* [Simulatore di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Criteri di qualità delle app](app-quality-criteria.md)

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Servizi di realtà mista</a>
* [Esercitazioni sulla realtà mista](tutorials.md)
* [Progetti open source](open-source-projects.md)
* [Nozioni di base MR 100: Introduzione a Unity](holograms-100.md)
* [Linee guida per la compatibilità hardware con la realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Invio di un'app a Windows Store](submitting-an-app-to-the-microsoft-store.md)
