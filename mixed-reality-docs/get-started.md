---
title: Informazioni di base
description: Questa guida illustra il modo più rapido per iniziare subito con lo sviluppo della realtà mista.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: iniziare a usare, nozioni di base, HoloLens, visore VR immersivi, ar, vr, unity, visual studio, Guida introduttiva, come
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873966"
---
# <a name="get-started"></a>Informazioni di base

Benvenuti nel mondo dello sviluppo di realtà mista. Se si ha familiarità con MR, questa Guida sarà l'hub per iniziare subito e in esecuzione nel minor tempo. Consente di ottenere un set di PC per lo sviluppo, preparazione dei dispositivi e installare gli strumenti che consente di velocizzare il processo di sviluppo MR. 

## <a name="intro-to-mixed-reality"></a>Introduzione alla realtà mista

Si potrebbero avere alcune domande su cosa si intende per "mixed reality" e la sua relazione con la realtà aumentata (AR) e la realtà virtuale (VR). In breve, realtà mista è la combinazione del mondo fisico con il mondo digitale, pertanto è uno spettro che copre tutti i dati da realtà aumentata, in cui viene inserito contenuto digitale nel mondo reale, in realtà virtuale, in cui il mondo reale è quasi interamente sostituito dalla firma digitale. 

![Esempio di un'app per realtà mista che supporta HoloLens e coinvolgenti auricolari (VR)](images/mr-island.png)<br>
*Le App per realtà mista possono supportare sia HoloLens e coinvolgenti auricolari (VR)*

Realtà mista di Windows creato come una sola piattaforma di sviluppo e il set di strumenti che è possibile coprire la gamma di MR e sono attualmente supportati due tipi di dispositivo che coprono lo spettro stesso: [Microsoft HoloLens](https://www.microsoft.com/hololens), prima self-contained holographic le cuffie al mondo, e [auricolari coinvolgenti di realtà mista di Windows e i controller di movimento](https://www.microsoft.com/windows/windows-mixed-reality), che la connessione a un PC per usufruire di realtà virtuale potente. È possibile estrarre la cosa è [realtà mista?] (articolo per una risposta più completa, se si è interessati.

## <a name="choose-your-development-path"></a>Scegliere il percorso di sviluppo

Usa il modo più semplice per sviluppare un'app di realtà mista [Unity](https://unity3d.com), uno strumento potente e diffuso middleware spesso usato per lo sviluppo di giochi. Se si desidera usare un motore personalizzato, è anche possibile [sfrutti DirectX](directx-development-overview.md), ma la maggior parte degli sviluppatori di MR usano Unity per le App e giochi. Con Unity sarà in grado di creare un'app per realtà mista destinata a HoloLens, coinvolgenti auricolari (VR) o entrambi.

## <a name="prepare-your-pc-and-devices-for-development"></a>Preparare il PC e dispositivi per lo sviluppo

Che tu stia creando un'app di realtà mista destinata a HoloLens, coinvolgenti auricolari (VR) o entrambi, si userà un set comune di strumenti e API. È anche opportuno assicurarsi che il PC è sufficientemente potente per lo sviluppo che procedura. 

>[!NOTE]
>È possibile trovare le raccomandazioni sul computer di sviluppo specifiche, le versioni supportate di ogni strumento software, e note sulla configurazione o impostazioni pertinenti per ciascuno di essi nel [installare gli strumenti](install-the-tools.md) articolo. Prima di installare strumenti indicati di seguito, consultare questo articolo.

Strumenti da installare:
* [Unity](https://store.unity.com/download)
* [Visual Studio (con Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [Toolkit di realtà mista per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

È opportuno inoltre [porre il dispositivo di destinazione in modalità sviluppatore e configurare Visual Studio per la distribuzione di App nel dispositivo di destinazione](using-visual-studio.md).

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Una nota sul Toolkit di realtà mista per Unity

![MRTK per Unity](images/mrtkandunity.png)<br>

***YOYO ANALIZZARE LA NATURA E INDICARE TUTTI GLI UTENTI PERCHÉ MRTK UNITY È COSÌ STRAORDINARI E TUTTE LE OPERAZIONI PIÙ INTERESSANTI HA ALL'INTERNO DI :)***

Il Toolkit di realtà mista è una raccolta di script e i componenti utili per accelerare lo sviluppo di applicazioni destinate a auricolari Microsoft HoloLens e realtà mista di Windows. Il progetto mira a ridurre gli ostacoli alla voce per creare applicazioni di realtà mista e contribuire alla community di noi crescita.

## <a name="start-your-first-mr-project"></a>Avvia il tuo primo progetto di MR

Ora che i PC e dispositivi sono configurati, si è pronti per creare il primo progetto di realtà mista in Unity. Segui il corso di academy MR prima, [SIG nozioni di base 100: Introduzione a Unity](holograms-100.md), e al termine si avrà un cubo l'esecuzione in un visore VR realtà mista.

![Screenshot di un cubo in un progetto di Unity di realtà mista](images/mr-cube.PNG)<br>
*Il primo progetto di realtà mista in Unity - world hello!*

## <a name="learn-more-and-get-help"></a>Altre informazioni e assistenza

Ora che è stato creato correttamente il primo progetto di MR, ora è possibile probabilmente fame per altre informazioni. Ecco alcune risorse per:
* [Documentazione per sviluppatori di realtà mista](mixed-reality.md) : si è già qui, ma è molto altro ancora per l'estrazione, tra cui documentazione tecnica, linee guida di progettazione, progetti di esempio e casi di Studio.
* [Esercitazioni di realtà mista](tutorials.md) -segui le esercitazioni che trattano di tutto impostare progetti, all'implementazione di blocchi di compilazione MR principali, per l'integrazione di Azure, servizi cloud nella tua app MR.
* [Informazioni su Unity](https://unity3d.com/learn) -sito Web di Unity offre esercitazioni, progetti e sessioni di formazione in tempo reale per gli autori in ogni fase di apprendimento.

È anche possibile ottenere assistenza da queste risorse grande community:
* [Forum per sviluppatori di realtà mista](https://forums.hololens.com/) -forum ufficiale per gli sviluppatori di realtà mista per porre e rispondere alle domande, nonché leggere novità sullo sviluppo di MR direttamente da Microsoft.
* [Canale di Slack HoloDevelopers](https://holodevelopersslack.azurewebsites.net/) -external più solido e trasformiamo mixed canale sviluppatore specifico della realtà; qui gli sviluppatori sono esperti e utile.
* [Forum di Unity](https://forum.unity3d.com/) -forum ufficiale di Unity.
