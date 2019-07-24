---
title: Attività iniziali
description: Questa guida descrive il modo più rapido per iniziare a usare lo sviluppo di realtà miste.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: Introduzione, nozioni di base, HoloLens, Headset immersivo, AR, VR, Unity, Visual Studio, avvio rapido, procedure
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873966"
---
# <a name="get-started"></a>Attività iniziali

Benvenuti nel mondo dello sviluppo di realtà mista. Se non si ha familiarità con MR, questa guida sarà l'hub per iniziare subito a funzionare. Ti aiuteremo a configurare il tuo PC per lo sviluppo, a preparare i tuoi dispositivi e a installare strumenti che accelereranno il processo di sviluppo. 

## <a name="intro-to-mixed-reality"></a>Introduzione alla realtà mista

È possibile porre domande su ciò che si intende per "realtà mista" e su come si riferisce alla realtà aumentata (AR) e alla realtà virtuale (VR). In breve, la realtà mista è la fusione del mondo fisico con il mondo digitale, quindi è uno spettro che copre tutto dalla realtà aumentata, in cui il contenuto digitale è inserito nel mondo reale, alla realtà virtuale, dove il mondo reale è quasi completamente sostituito da Digital. 

![Esempio di un'app per realtà mista che supporta gli auricolari HoloLens e immersivi (VR)](images/mr-island.png)<br>
*Le app per la realtà mista possono supportare sia cuffie HoloLens che immersive (VR)*

Abbiamo creato la realtà mista di Windows come una singola piattaforma di sviluppo e un set di strumenti in grado di coprire lo spettro di MR e attualmente sono supportati due tipi di dispositivi che coprono lo stesso spettro: [Microsoft HoloLens](https://www.microsoft.com/hololens), il primo Headset autosufficiente di tutto il mondo e gli [auricolari e i controller di movimento di Windows Mixed Reality](https://www.microsoft.com/windows/windows-mixed-reality), che si connettono a un PC per esperienze di realtà virtuale avanzate. È possibile consultare la [realtà mista?] (per una risposta più approfondita, se si è interessati.

## <a name="choose-your-development-path"></a>Scegliere il percorso di sviluppo

Il modo più semplice per sviluppare un'app per realtà mista consiste nell'usare [Unity](https://unity3d.com), uno strumento middleware potente e diffuso spesso usato per lo sviluppo di giochi. Se si vuole usare un motore personalizzato, è anche possibile eseguire la [compilazione in DirectX](directx-development-overview.md), ma la maggior parte degli sviluppatori di Mr USA Unity per i giochi e le app. Con Unity potrai creare un'app per realtà mista destinata a HoloLens, immersive (VR) o entrambi.

## <a name="prepare-your-pc-and-devices-for-development"></a>Preparare il PC e i dispositivi per lo sviluppo

Che tu stia compilando un'app per realtà mista destinata a HoloLens, immersive (VR) o entrambi, userai un insieme comune di strumenti e API. Sarà inoltre necessario assicurarsi che il PC sia sufficientemente potente per lo sviluppo che si intende eseguire. 

>[!NOTE]
>È possibile trovare le indicazioni sulle specifiche del PC di sviluppo, sulle versioni supportate di ogni strumento software e sulle relative impostazioni o note di configurazione per ognuna nell'articolo [installare gli strumenti](install-the-tools.md) . Leggere questo articolo prima di installare gli strumenti seguenti.

Strumenti da installare:
* [Unity](https://store.unity.com/download)
* [Visual Studio (con Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [Toolkit per realtà mista per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

È anche necessario impostare [il dispositivo di destinazione in modalità sviluppatore e configurare Visual Studio per la distribuzione di app nel dispositivo di destinazione](using-visual-studio.md).

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Nota sul Toolkit di realtà mista per Unity

![MRTK per Unity](images/mrtkandunity.png)<br>

***YOYO, PER SPIEGARE A TUTTI I MOTIVI PER CUI MRTK-UNITY È COSÌ SORPRENDENTE E TUTTI GLI ELEMENTI INTERESSANTI SONO CONTENUTI ALL'INTERNO:)***

Il Toolkit di realtà mista è una raccolta di script e componenti destinati ad accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens e alle cuffie di realtà miste di Windows. Il progetto mira a ridurre le barriere di accesso alla creazione di applicazioni di realtà mista offrendo inoltre un contributo alla community.

## <a name="start-your-first-mr-project"></a>Avvia il primo progetto MR

Ora che il PC e i dispositivi sono configurati, si è pronti per creare il primo progetto di realtà mista in Unity. Segui il primo corso di Mr Academy, [nozioni fondamentali 100: Introduzione a Unity](holograms-100.md)e, al termine, il cubo sarà operativo in un auricolare a realtà mista.

![Screenshot di un cubo in un progetto di Unity per la realtà mista](images/mr-cube.PNG)<br>
*Il primo progetto di realtà mista in Unity-Hello World!*

## <a name="learn-more-and-get-help"></a>Scopri di più e Ottieni assistenza

Ora che è stato creato il primo progetto MR, è probabile che sia affamato per altro. Di seguito sono riportate alcune risorse che consentono di:
* [Documentazione](mixed-reality.md) per gli sviluppatori di realtà mista: ci si trova già in questo articolo, ma c'è molto altro da vedere, tra cui documentazione tecnica, linee guida di progettazione, progetti di esempio e case study.
* [Esercitazioni sulla realtà mista](tutorials.md) : seguire le esercitazioni che illustrano tutti gli aspetti della configurazione dei progetti, l'implementazione dei principali blocchi predefiniti per l'integrazione di servizi cloud di Azure nell'app Mr.
* [Informazioni](https://unity3d.com/learn) su Unity: il sito Web di Unity offre esercitazioni, progetti e sessioni di formazione live per gli autori in ogni fase dell'apprendimento.

È anche possibile ottenere supporto da queste eccezionali risorse della community:
* Forum per sviluppatori di [realtà mista](https://forums.hololens.com/) : il forum ufficiale per gli sviluppatori di realtà mista per porre domande e rispondere alle domande, oltre a leggere le notizie sullo sviluppo di Microsoft direttamente da Microsoft.
* [Canale Slack HoloDevelopers](https://holodevelopersslack.azurewebsites.net/) : canale per sviluppatori più robusto e con risorse eterogenee per la realtà esterna. gli sviluppatori sono informati e utili.
* [Forum](https://forum.unity3d.com/) di Unity-forum ufficiali di Unity.
