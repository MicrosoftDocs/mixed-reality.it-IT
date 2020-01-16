---
title: Realtà mista di Windows e la nuova Microsoft Edge
description: Prepararsi per la nuova Microsoft Edge in realtà mista di Windows. Include le modifiche da prevedere, gli aggiornamenti per la ricerca e i problemi noti.
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: Edge, nuovo, Web immersivo, Microsoft Edge, browser, VR
ms.openlocfilehash: e38cd83cef274281f0d36ae8714ea82aac5f0c65
ms.sourcegitcommit: e9e4e722f4b607888ce69185f8bda9549ad526ad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76040996"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Realtà mista di Windows e la nuova Microsoft Edge

Il [nuovo Microsoft Edge è ora disponibile per il download](https://blogs.windows.com/windowsexperience/?p=173496), ma i clienti possono anche [attendere che sia installato in un futuro aggiornamento a Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), seguendo un approccio di implementazione misurato nei prossimi mesi. 

Con questa notizia, **abbiamo voluto lasciare che i clienti di Windows Mixed Reality VR conoscano cosa aspettarsi dal nuovo Microsoft Edge e informano alcuni aggiornamenti in sospeso che miglioreranno l'esperienza di esplorazione Web in realtà mista di Windows**.

## <a name="introducing-the-new-microsoft-edge"></a>Introduzione al nuovo Microsoft Edge

Il nuovo Microsoft Edge [adotta il progetto Chromium Open Source](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) sul desktop per creare una migliore compatibilità Web per i clienti e meno frammentazione del Web per tutti gli sviluppatori Web. Supporta anche WebXR al lancio, il nuovo standard per la creazione di esperienze Web Immersive per gli auricolari VR, al posto di WebVR.

>[!IMPORTANT]
>Quando si installa Microsoft Edge in un dispositivo Windows 10 aggiornato, la versione precedente (legacy) del PC verrà sostituita.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Preparazione per il nuovo Microsoft Edge

I clienti che vogliono usare la nuova Microsoft Edge nella Home realtà mista di Windows per la realtà mista di Windows sono in grado di **eseguire l'aggiornamento a Windows 10 versione 1903 o successiva per il supporto nativo di applicazioni Win32, come il nuovo Microsoft Edge,** nella Home realtà mista. Controllare Windows Update o [installare manualmente la versione più recente di Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Per ottenere la migliore esperienza Microsoft Edge nella Home realtà mista, è consigliabile attendere **alcune ottimizzazioni della realtà mista di Windows per i nuovi Microsoft Edge che arrivano con l'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o versione successiva)** , che dovrebbe essere disponibile in Windows Update entro la fine del gennaio.

>[!IMPORTANT]
>Se si sceglie di scaricare il nuovo Microsoft Edge prima di eseguire questi aggiornamenti, si verificano alcuni problemi noti con il relativo comportamento nella realtà mista di Windows (che è possibile leggere di seguito).

## <a name="known-issues"></a>Problemi noti

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemi noti risolti dall'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o versioni successive)

- L'avvio di qualsiasi app Win32, incluso il nuovo Microsoft Edge, causa un blocco breve della visualizzazione dell'auricolare.
- Il riquadro Microsoft Edge scompare dal menu Start della realtà mista di Windows (è possibile trovarlo nella cartella "app classiche").
- Windows dal Microsoft Edge precedente è ancora situato intorno alla Home realtà mista, ma non può essere usato. Il tentativo di attivare tali finestre viene avviato all'interno dell'app desktop.
- Selezionando un collegamento ipertestuale nella Home realtà mista viene avviato un Web browser sul desktop anziché la Home realtà mista.
- L'app WebVR Showcase è presente nella Home realtà mista, nonostante WebVR non sia più supportata.
- Miglioramenti generali al lancio da tastiera e agli oggetti visivi.

### <a name="additional-known-issues"></a>Problemi noti aggiuntivi

-   I siti Web aperti in realtà mista di Windows andranno perduti quando si chiude il portale di realtà mista, anche se le finestre Microsoft Edge rimarranno nella posizione in cui sono state inserite nella Home realtà mista.
-   L'audio da Microsoft Edge Windows non è spaziale.
-   L'apertura di un video 360 da YouTube in realtà mista di Windows può causare la distorsione del video nell'auricolare. L'aggiornamento della pagina del video di YouTube e il rilancio del video 360 *possono* risolvere il problema, ma è stato riscontrato un feedback che il problema potrebbe persistere.
-   Durante le sessioni di realtà mista di Windows, i monitoraggi virtuali verranno visualizzati come monitoraggi fisici generici nelle impostazioni > Visualizzazione > di sistema.



