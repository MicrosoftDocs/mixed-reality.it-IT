---
title: Aggiornamento dell'applicazione SteamVR
description: Procedure consigliate per l'aggiornamento dell'applicazione SteamVR per ottimizzare compatibilità con le cuffie di realtà mista di Windows.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilità
ms.openlocfilehash: 6479130b14b8b50828ebecd3a648fd8a425aec15
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438211"
---
# <a name="updating-your-steamvr-application"></a>Aggiornamento dell'applicazione SteamVR
Invitiamo gli sviluppatori a testare e ottimizzare le proprie esperienze di SteamVR per l'esecuzione su cuffie di realtà miste Windows. Questa documentazione illustra i miglioramenti più comuni che gli sviluppatori possono fare per garantire che la loro esperienza sia ottimale in realtà mista di Windows.

## <a name="initial-setup-instructions"></a>Istruzioni per la configurazione iniziale

Per iniziare a testare il gioco o l'app in realtà mista di Windows, assicurarsi di seguire prima la [Guida introduttiva.](https://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Modelli di controller
1. Se l'app esegue il rendering dei modelli di controller:
    * Usare i [modelli di controller di movimento per la realtà mista di Windows](motion-controllers.md#rendering-the-motion-controller-model)
    * Usare IVRRenderModel:: GetComponentState per ottenere le trasformazioni locali per le parti del componente, ad esempio Pose del puntatore)
2. Le esperienze con una nozione di manualità dovrebbero ricevere suggerimenti dalle API di input per distinguere i controller [(esempio di Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controlli

Quando si progetta o si modifica il layout del controllo, tenere presente il seguente set di comandi riservati:
1. Se si fa clic su un **levetta analogico a sinistra e a destra** viene riservato il **dashboard di Steam**.
2. Il **pulsante Windows** restituirà sempre gli utenti alla Home realtà mista di Windows.

Se possibile, per impostazione predefinita la teleportatura basata su Thumb Stick corrisponde al comportamento di teleportazione [principale della realtà mista di Windows](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)

## <a name="tooltips-and-ui"></a>Descrizioni comando e interfaccia utente

Molti giochi VR sfruttano le descrizioni comandi e le sovrapposizioni del controller di movimento per insegnare agli utenti i comandi più importanti per il gioco o l'app. Quando si esegue l'ottimizzazione dell'applicazione per la realtà mista di Windows, è consigliabile esaminare questa parte dell'esperienza per assicurarsi che le descrizioni comandi siano mappate ai modelli di controller Windows.

Inoltre, se sono presenti punti nell'esperienza in cui si visualizzano immagini dei controller, assicurarsi di fornire immagini aggiornate usando i controller di movimento della realtà mista di Windows.

## <a name="haptics"></a>Haptics

A partire dall' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md), haptics sono ora supportati per le esperienze SteamVR in realtà mista di Windows. Se l'app o il gioco SteamVR include già il supporto per haptics, dovrebbe funzionare ora (senza lavoro aggiuntivo) con i controller di movimento per la [realtà mista di Windows](motion-controllers.md).

I controller di movimento per la realtà mista di Windows usano un motore haptics standard, anziché gli attuatori lineari presenti in altri controller di movimento SteamVR, che possono causare un'esperienza utente leggermente diversa da quella prevista. È quindi consigliabile testare e ottimizzare la progettazione haptics con i controller di movimento di realtà mista di Windows. Ad esempio, talvolta gli impulsi brevi (5-10 ms) sono meno evidenti nei controller di movimento della realtà mista di Windows. Per produrre un impulso più evidente, provare a inviare un "clic" più lungo (40-70ms) per fornire al motore più tempo per l'avvio prima di essere richiamato.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Avvio di app SteamVR dal menu Start della realtà mista di Windows

Per le esperienze VR distribuite tramite Steam, abbiamo [aggiornato la realtà mista di Windows per SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) insieme ai più recenti voli RS5 di [Windows Insider](https://insider.windows.com) , in modo che i titoli di SteamVR ora vengano visualizzati nel menu Start della realtà mista di Windows in "tutte le app" elenco automatico. Con queste versioni del software installate, i clienti possono ora avviare i titoli SteamVR direttamente dall'interno della Home realtà mista di Windows senza rimuovere gli auricolari.

## <a name="windows-mixed-reality-logo"></a>Logo della realtà mista di Windows

Per visualizzare il supporto della realtà mista di Windows per il titolo, andare al collegamento "modifica pagina Archivio" nella pagina di destinazione dell'app, fare clic sulla scheda "informazioni di base" e scorrere verso il basso fino a "realtà virtuale". Deselezionare l'opzione "Nascondi realtà mista di Windows" e quindi pubblicare nell'archivio.

## <a name="bugs-and-feedback"></a>Bug e commenti

I commenti e i suggerimenti sono utili per migliorare l'esperienza di SteamVR di realtà mista di Windows. Inviare tutti i commenti e i bug tramite l' [Hub feedback di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Ecco alcuni [suggerimenti su come fare in modo che il feedback di SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)sia il più utile possibile.

In caso di domande o commenti da condividere, è anche possibile contattarci nel forum di [Steam](https://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Domande frequenti e risoluzione dei problemi

Se si verificano problemi generali durante l'impostazione o la riproduzione dell'esperienza, [vedere le procedure di risoluzione dei problemi più recenti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Vedi anche
* [Installare gli strumenti](install-the-tools.md)
* [Cronologia driver per cuffie e controller di movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Linee guida per la compatibilità hardware con la realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
