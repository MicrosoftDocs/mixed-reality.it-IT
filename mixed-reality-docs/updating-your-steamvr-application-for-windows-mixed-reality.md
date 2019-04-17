---
title: L'aggiornamento dell'applicazione SteamVR per realtà mista di Windows
description: Procedure consigliate per l'aggiornamento dell'applicazione SteamVR per ottimizzare la compatibilità con le cuffie realtà mista di Windows.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilità
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597853"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>L'aggiornamento dell'applicazione SteamVR per realtà mista di Windows

E invita gli sviluppatori per testare e ottimizzare le proprie esperienze SteamVR per eseguire in auricolari realtà mista di Windows. Questa documentazione include miglioramenti comuni possono rendere gli sviluppatori per garantire che l'esperienza funziona correttamente sulle realtà mista di Windows.

## <a name="initial-setup-instructions"></a>Istruzioni di installazione iniziali

Per avviare il test orizzontale gioco o nell'app su marca di realtà mista di Windows assicurarsi di seguire prima i [Guida introduttiva.](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Modelli di controller
1. Se l'app esegue il rendering dei modelli di controller:
    * Usare il [modelli controller movimento di realtà mista di Windows](motion-controllers.md#rendering-the-motion-controller-model)
    * Usare IVRRenderModel::GetComponentState ottenere locale Trasforma alle parti componente (ad es. Puntatore posa)
2. Esperienze che dispongono di una nozione di mano dovrebbe essere hint dell'input API per differenziare i controller [(ad esempio Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controlli

Quando si progetta o modificando il layout del controllo tenere presente il seguente set di comandi riservati:
1. Facendo clic verso il basso il **thumbstick sinistro e destro analogico** è riservato per il **Dashboard Steam**.
2. Il **pulsante Windows** restituirà sempre agli utenti in Windows Mixed Reality home.

Se possibile, il valore predefinito per thumb stilizzata basa teletrasporto in modo che corrisponda il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teletrasporto comportamento

## <a name="tooltips-and-ui"></a>Le descrizioni comandi e l'interfaccia utente

Molti giochi di realtà virtuale sfruttano i vantaggi di descrizioni comandi di controller di animazione e sovrapposizioni di insegnare agli utenti i comandi più importanti per i propri giochi o app. Durante l'ottimizzazione dell'applicazione per realtà mista di Windows si consiglia di esaminare questa parte della tua esperienza per assicurarsi che le descrizioni comandi eseguire il mapping per i modelli di controller di Windows.

Anche se sono presenti i punti durante l'utilizzo in cui si visualizzano le immagini dei controller di assicurarsi di fornire le immagini aggiornate con i controller di movimento di realtà mista di Windows.

## <a name="haptics"></a>Haptics

Inizia con la [Windows 10 April 2018 Update](release-notes-april-2018.md), haptics sono ora supportati per usufruire di SteamVR realtà mista di Windows. Se l'app SteamVR o il gioco include già il supporto per haptics, che dovrebbe funzionare (con alcuna attività aggiuntiva) con [controller di movimento di realtà mista di Windows](motion-controllers.md).

I controller di movimento di realtà mista di Windows usano un motore haptics standard, a differenza di attuatori lineari trovato in alcuni altri SteamVR movimento controller, che può comportare un'esperienza utente leggermente diversa-rispetto al previsto. È quindi consigliabile test e ottimizzazione della progettazione haptics con i controller del movimento di realtà mista di Windows. Ad esempio, impulsi aptico talvolta brevi (da 5 a 10 ms) sono meno evidente nei controller di movimento di realtà mista di Windows. Per produrre un impulso più evidente, provare a usare l'invio di un più lungo "fare clic su" (40 70ms) per concedere il motore più tempo per creare rapidamente prima indicato alla potenza nuovamente.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Avvio delle App SteamVR dal menu Start realtà mista di Windows

Per esperienze di realtà virtuale distribuite tramite Steam, abbiamo [aggiornata la realtà mista di Windows per la versione SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) con la versione più recente [Windows Insider](https://insider.windows.com) RS5 voli in modo che i titoli SteamVR ora visualizzati di Dal menu Start realtà mista di Windows in "tutte le app" elenco automaticamente. Con le versioni di software installate, i clienti possono ora avviare titoli SteamVR direttamente da all'interno di realtà mista di Windows home senza rimuovere le cuffie.

## <a name="windows-mixed-reality-logo"></a>Logo di realtà mista di Windows

Per visualizzare il supporto di realtà mista di Windows per il titolo, passare al collegamento "Modifica pagina Store" nella pagina di destinazione dell'App, fare clic sulla scheda "Le informazioni di base" e scorrere verso il basso "Virtuale Reality". Deselezionare l'opzione di "nascondere realtà mista di Windows" e quindi pubblicarla nello store.

## <a name="bugs-and-feedback"></a>Bug e feedback

Commenti e suggerimenti sono estremamente utile se si desidera migliorare l'esperienza SteamVR realtà mista di Windows. Inviare tutti i commenti e suggerimenti e bug tramite la [Hub di Feedback Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Ecco alcune [suggerimenti su come rendere il tuo feedback SteamVR utile come possibili](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Se hai domande o commenti per condividere, è possibile anche contattare Microsoft sul nostro [forum di Steam](http://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Domande frequenti e risoluzione dei problemi

Se si verificano problemi generali di configurazione o la tua esperienza di riproduzione [consultare i passaggi di risoluzione dei problemi più recenti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Vedere anche
* [Installare gli strumenti](install-the-tools.md)
* [Cronologia dei driver di controller visore VR e movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Realtà mista di Windows minimo PC compatibilità alle linee guida hardware](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
