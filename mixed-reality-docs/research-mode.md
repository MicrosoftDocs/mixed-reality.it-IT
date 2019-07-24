---
title: Modalità di ricerca HoloLens
description: Usando la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi dei sensori del dispositivo chiave (profondità, rilevamento dell'ambiente e riflettanza IR).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modalità di ricerca, CV, RS4, visione artificiale, ricerca, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829929"
---
# <a name="hololens-research-mode"></a>Modalità di ricerca HoloLens

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte dell' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md) per HoloLens e non è disponibile nelle versioni precedenti.

La modalità di ricerca è una nuova funzionalità di HoloLens che fornisce l'accesso alle applicazioni ai sensori chiave del dispositivo. Sono inclusi:
- Le quattro fotocamere di rilevamento dell'ambiente usate dal sistema per la creazione e il rilevamento della mappa.
- Due versioni dei dati di profondità della fotocamera, una per il rilevamento ad alta frequenza (30 FPS), comunemente usata per il rilevamento manuale e l'altra per il rilevamento di più bassa frequenza (1 FPS), attualmente usata dal mapping spaziale,
- Due versioni di un flusso IR-riflettività, usate dal HoloLens per calcolare la profondità, ma preziose nel proprio diritto, perché queste immagini sono illuminate dalla HoloLens e ragionevolmente non interessate dalla luce ambientale.

![Schermata dell'app modalità di ricerca](images/sensor-stream-viewer.jpg)<br>
*Acquisizione di realtà mista di un'applicazione di test che visualizza gli otto flussi di sensori disponibili in modalità ricerca*

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Modalità di ricerca</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>Prima di usare la modalità di ricerca

La modalità di ricerca è ben denominata: è destinata ai ricercatori accademici e industriali che provano nuove idee nei campi di Visione artificiale e robotica.  La modalità di ricerca non è destinata alle applicazioni che verranno distribuite in un'organizzazione o rese disponibili nella Microsoft Store. Il motivo è che la modalità di ricerca riduce la sicurezza del dispositivo e utilizza significativamente più energia della batteria rispetto al normale funzionamento. Microsoft non sta eseguendo alcun commit per supportare questa modalità in tutti i dispositivi futuri. Pertanto, è consigliabile utilizzarlo per sviluppare e testare nuove idee; Tuttavia, non sarà possibile distribuire ampiamente le applicazioni che usano la modalità di ricerca o avere garanzie che continueranno a funzionare su hardware futuro.

## <a name="enabling-research-mode"></a>Abilitazione della modalità ricerca

La modalità di ricerca è una modalità secondaria della modalità sviluppatore. Per prima cosa è necessario abilitare la modalità sviluppatore nell'app Impostazioni (**impostazioni > aggiornare & > di sicurezza per gli sviluppatori**):

1. Imposta "USA funzionalità per sviluppatori" **su on**
2. Imposta "Abilita il portale del dispositivo" **su on**

Usando un Web browser connesso alla stessa rete Wi-Fi della HoloLens, passare all'indirizzo IP della HoloLens (ottenuto tramite **le impostazioni > rete & Internet > Wi-fi > le proprietà hardware**). Si tratta del [portale del dispositivo](using-the-windows-device-portal.md)ed è presente una pagina "modalità di ricerca" nella sezione "sistema" del portale:

![Scheda modalità ricerca del portale per dispositivi HoloLens](images/ResearchModeDevPortal.png)<br>
*Modalità di ricerca nel portale per dispositivi HoloLens*

Dopo aver selezionato **Consenti accesso ai flussi di sensori**, sarà necessario riavviare HoloLens. Questa operazione può essere eseguita dal portale del dispositivo, sotto la voce di menu "Power" nella parte superiore della pagina.

Una volta riavviato il dispositivo, le applicazioni che sono state caricate tramite il portale per i dispositivi devono essere in grado di accedere ai flussi della modalità di ricerca.

## <a name="using-sensor-data-in-your-apps"></a>Uso dei dati dei sensori nelle app

Le applicazioni possono accedere ai dati del flusso dei sensori aprendo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) flussi esattamente allo stesso modo in cui accedono al flusso della fotocamera Photo/video. 

Tutte le API che funzionano per lo sviluppo HoloLens sono disponibili anche in modalità di ricerca. In particolare, l'applicazione è in grado di individuare con esattezza il punto in cui HoloLens si trova nello spazio 6DoF a ogni tempo di acquisizione del frame del sensore

Applicazioni di esempio che illustrano come accedere ai vari flussi in modalità di ricerca, come usare le funzioni intrinseche ed estrinseche e come registrare i flussi sono disponibili nel [repository GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV).

## <a name="known-issues"></a>Problemi noti

Vedere la pagina relativa al [rilevamento dei problemi](https://github.com/Microsoft/HololensForCV/issues) nel repository HoloLensForCV.

## <a name="see-also"></a>Vedere anche

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repository GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Avviare il Portale di dispositivi di Windows](using-the-windows-device-portal.md)
