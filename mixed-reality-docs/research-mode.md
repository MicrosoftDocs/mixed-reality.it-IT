---
title: Modalità HoloLens Research
description: Usa la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi di sensore chiave dispositivo (profondità, l'ambiente di rilevamento e runtime di integrazione-riflettività).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modalità di ricerca, convalida incrociata, rs4, visione artificiale, ricerca, HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597512"
---
# <a name="hololens-research-mode"></a>Modalità HoloLens Research

> [!NOTE]
> Questa funzionalità è stato aggiunto durante la [Windows 10 April 2018 Update](release-notes-april-2018.md) per HoloLens e non è disponibile nelle versioni precedenti.

Modalità di ricerca è una nuova funzionalità di HoloLens che fornisce accesso alle applicazioni per i sensori di chiave nel dispositivo. tra cui:
- I quattro ambiente fotocamere utilizzate dal sistema per la creazione della mappa e rilevamento head di rilevamento.
- Due versioni dei dati della fotocamera profondità, una per quasi-depth rilevazione (30 FPS) ad alta frequenza, in genere utilizzato a disposizione di rilevamento e l'altro per frequenza inferiore (1 FPS) distante profondità sensibile, è attualmente usano da Mapping spaziale,
- Due versioni di un flusso di runtime di integrazione-riflettività, usata di HoloLens per calcolare profondità, ma siano utili in sé come queste immagini vengono illuminati di HoloLens e ragionevolmente interessata da luce ambientale.

![Schermata di app in modalità di ricerca](images/sensor-stream-viewer.jpg)<br>
*Un'acquisizione di realtà mista di un'applicazione di test che consente di visualizzare i flussi di otto sensore disponibili in modalità di ricerca*

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Modalità di ricerca</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a>Prima di usare la modalità di ricerca

Modalità di ricerca viene anche denominata: è destinata a ricercatori accademici e industriali provare nuove idee nei campi di visione artificiale e robotica.  Modalità di ricerca non è per le applicazioni che verranno distribuite in un'organizzazione o resa disponibile in di Microsoft Store. Il motivo è che la modalità di ricerca consente di ridurre la sicurezza del dispositivo e consuma energia della batteria significativamente maggiore rispetto al normale funzionamento. Microsoft non esegue il commit a questa modalità di supporto in qualsiasi dispositivo future. Di conseguenza, è consigliabile che usarlo per sviluppare e testare nuove idee; Tuttavia, non sarà in grado di distribuire ampiamente le applicazioni che usano la modalità di ricerca o qualsiasi garanzia che continuerà a lavorare su hardware future.

## <a name="enabling-research-mode"></a>Abilitazione della modalità di ricerca

Modalità di ricerca è una modalità secondaria della modalità sviluppatore. È innanzitutto necessario abilitare la modalità sviluppatore nell'app impostazioni (**Impostazioni > aggiornamento e sicurezza > per gli sviluppatori**):

1. Impostare "Usa funzionalità per sviluppatori" su **su**
2. Impostare "Abilita il portale del dispositivo" su **su**

Quindi usando un web browser che è connesso alla stessa rete Wi-Fi di HoloLens, passare all'indirizzo IP di HoloLens (ottenuto tramite **Impostazioni > rete e Internet > Wi-Fi > proprietà Hardware**). Questo è il [portale dispositivi](using-the-windows-device-portal.md), sarà presente una pagina di "Modalità di ricerca" nella sezione "Sistema" del portale:

![Scheda di modalità di ricerca del portale dei dispositivi HoloLens](images/ResearchModeDevPortal.png)<br>
*Modalità di ricerca nel portale di dispositivo HoloLens*

Dopo aver selezionato **consentire l'accesso ai flussi di sensore**, dovrai riavviare HoloLens. È possibile eseguire questa operazione dal portale di dispositivo, sotto la voce di menu "Power" nella parte superiore della pagina.

Dopo aver riavviato il dispositivo, le applicazioni che sono state caricate tramite il portale di dispositivo devono essere in grado di accedere ai flussi di modalità di ricerca.

## <a name="using-sensor-data-in-your-apps"></a>Usando i dati dei sensori nelle tue App

Le applicazioni possono accedere i dati del sensore flusso aprendo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) flussi in esattamente allo stesso modo che accedono al flusso di fotocamera foto/video. 

Tutte le API che funzionano per lo sviluppo di HoloLens sono anche disponibili in modalità di ricerca. In particolare, l'applicazione può sapere con precisione dove HoloLens è nello spazio 6DoF al momento dell'acquisizione frame ogni sensore.

Sono disponibili in applicazioni di esempio che illustra come registrare i flussi, come usare le funzioni intrinseche ed extrinsics e modalità di accesso i vari flussi modalità Research la [repository HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV).

## <a name="known-issues"></a>Problemi noti

Vedere le [tracker problema](https://github.com/Microsoft/HololensForCV/issues) nel repository HoloLensForCV.

## <a name="see-also"></a>Vedere anche

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repository HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)
* [Utilizzando il Windows Device Portal](using-the-windows-device-portal.md)
