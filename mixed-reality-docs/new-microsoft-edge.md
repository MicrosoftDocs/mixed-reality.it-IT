---
title: Realtà mista di Windows e la nuova Microsoft Edge
description: Prepararsi per la nuova Microsoft Edge in realtà mista di Windows. Include le modifiche da prevedere, gli aggiornamenti per la ricerca e i problemi noti.
author: mattzmsft
ms.author: mazeller
ms.date: 07/31/2020
ms.topic: article
keywords: Edge, nuovo, Web immersivo, Microsoft Edge, browser, VR
ms.openlocfilehash: 107b825496cc318042da0e0cd9acdbe482994a69
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476983"
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

Per ottenere la migliore esperienza Microsoft Edge nella Home realtà mista, è consigliabile attendere **alcune ottimizzazioni della realtà mista di Windows per i nuovi Microsoft Edge che arrivano con l'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o versione successiva)**, che dovrebbe essere disponibile in Windows Update entro la fine del gennaio.

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

### <a name="monitor-and-input-handling-issues"></a>Problemi di monitoraggio e gestione degli input

Dopo aver eseguito l'aggiornamento cumulativo 2020-01 per Windows 10 versione 1903 (o successiva), i monitoraggi virtuali verranno visualizzati come monitoraggi fisici generici nelle **impostazioni > sistema > visualizzare durante le** sessioni della realtà mista di Windows. Alcuni clienti, in particolare quelli con più di un monitor fisico, possono riscontrare problemi con il layout del desktop e la gestione degli input di conseguenza.

**Perché si verifica questo problema**

Il supporto per le applicazioni Win32 classiche nella realtà mista di Windows è stato introdotto con l' [aggiornamento 2019 di Windows 10](#release-notes-may-2019.md). Per abilitare questo supporto, è necessario creare un monitor virtuale per ospitare l'applicazione Win32. Ogni volta che viene avviata una nuova applicazione Win32, è necessario creare un altro monitor virtuale. Sfortunatamente, la creazione di un monitoraggio virtuale è un'attività intensa che può causare un blocco breve della visualizzazione dell'auricolare. I clienti hanno offerto commenti e suggerimenti che si trattava di un'esperienza scomoda e problematica. Grazie a questo feedback, oltre a un maggiore utilizzo di applicazioni Win32, abbiamo deciso di pre-allocare tre monitoraggi virtuali durante l'avvio della realtà mista di Windows per evitare questa situazione di disturbo e consentire ai clienti di avviare fino a tre applicazioni Win32 simultanee senza dover visualizzare il blocco dello schermo dell'auricolare.

**Soluzione alternativa**

Abbiamo ricevuto il feedback che alcuni clienti, in particolare quelli con più monitoraggi fisici, preferiscono disabilitare questa pre-allocazione di monitoraggio virtuale. Per offrire ai clienti il controllo e la scelta, è stata abilitata una soluzione alternativa che comporta la modifica di un valore della chiave del registro di sistema (disponibile con l'aggiornamento cumulativo 2020-07 per Windows 10 versione 2004).

>[!NOTE]
>La modifica dei valori delle chiavi del registro di sistema è destinata agli utenti avanzati.

>[!WARNING]
>La disabilitazione della preallocazione di monitoraggio virtuale può comportare un blocco rapido della visualizzazione dell'auricolare quando si avvia un'applicazione Win32 (ad esempio, Steam, il nuovo Microsoft Edge o Google Chrome) in realtà mista di Windows.

Per disabilitare la preallocazione di monitoraggio virtuale:
1. Controllare **Windows Update** per l'aggiornamento cumulativo 2020-07 per Windows 10 versione 2004 e installare l'aggiornamento, se disponibile.
2. Avviare l' **Editor del registro di sistema**.
3. Passa a HKEY_CURRENT_USER \SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\PreallocateVirtualMonitors
4. Modificare il valore DWORD da 1 (valore predefinito) a 0 (zero)
    * TRUE-1
    * FALSE-0

I monitoraggi virtuali verranno allocati quando si tenta di avviare un'applicazione Win32 in realtà mista di Windows anziché pre-allocare. Per reimpostare questa impostazione e riabilitare la preallocazione di monitoraggio virtuale, restituire il valore DWORD su 1.

### <a name="additional-known-issues"></a>Problemi noti aggiuntivi

-   I siti Web aperti in realtà mista di Windows andranno perduti quando si chiude il portale di realtà mista, anche se le finestre Microsoft Edge rimarranno nella posizione in cui sono state inserite nella Home realtà mista.
- Le esperienze di WebXR, tra cui l'estensione del Visualizzatore 360, potrebbero non essere avviate correttamente nei PC con una configurazione GPU ibrida. È possibile risolvere questo problema selezionando la GPU dedicata come GPU predefinita nel software della scheda grafica.
-   L'audio da Microsoft Edge Windows non è spaziale.
-   **Correzione della versione dell'estensione del visualizzatore 360 2.3.8**: l'apertura di un video 360 da YouTube in realtà mista di Windows può comportare la distorsione del video nell'auricolare. Il riavvio di Edge dovrebbe aggiornare in modo invisibile l'estensione del Visualizzatore 360 per risolvere il problema. Per verificare quale versione dell'estensione è possibile immettere `edge://system/` nella barra degli indirizzi e selezionare il pulsante **Espandi** accanto a "estensioni".




