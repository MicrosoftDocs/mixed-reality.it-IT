---
title: Modalità di ricerca HoloLens
description: Usando la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi dei sensori del dispositivo chiave (profondità, rilevamento dell'ambiente e riflettanza IR).
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: Modalità di ricerca, CV, RS4, visione artificiale, ricerca, HoloLens, HoloLens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507695"
---
# <a name="hololens-research-mode"></a>Modalità di ricerca HoloLens

La modalità di ricerca è stata introdotta nella prima generazione HoloLens per consentire l'accesso ai sensori chiave sul dispositivo, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione.  La modalità di ricerca per HoloLens 2 mantiene le funzionalità di HoloLens 1, aggiungendo l'accesso a flussi aggiuntivi:

* **Fotocamere di rilevamento dell'ambiente chiaro visibile** : fotocamere con scalabilità orizzontale usate dal sistema per il rilevamento delle intestazioni e la compilazione della mappa.
* **Depth fotocamera** : funziona in due modalità:  
    + AHAT, rilevamento a frequenza elevata (45 FPS) usato per il rilevamento manuale. In modo diverso rispetto alla prima versione a breve termine, AHAT fornisce lo pseudo-Depth con la fase a capo superiore a 1 contatore. 
    + Rilevamento a lungo termine, a bassa frequenza (1-5 FPS) per un rilevamento approfondito usato dal [mapping spaziale](spatial-mapping.md)

* **Due versioni del flusso IR-riflettività** , usate dal HoloLens per calcolare la profondità. Queste immagini sono illuminate dall'infrarosso e non sono interessate dalla luce visibile dell'ambiente.

Se si usa un HoloLens 2, è anche possibile accedere agli input aggiuntivi seguenti:

* **Accelerometro** : usato dal sistema per determinare l'accelerazione lineare lungo gli assi X, Y e Z e la gravità.
* **Gyro** : utilizzato dal sistema per determinare le rotazioni.
* **Magnetometro** : utilizzato dal sistema per stimare l'orientamento assoluto.

> [!IMPORTANT]
> La modalità di ricerca è attualmente disponibile in anteprima pubblica. HoloLens 2 esempi, esercitazioni e la documentazione completa dell'API saranno disponibili in [ECCV 2020](https://eccv2020.eu/
 ) nel repository git della modalità di ricerca.

![Schermata dell'app modalità di ricerca](images/sensor-stream-viewer.jpg)<br>
*Acquisizione di realtà mista di un'applicazione di test che visualizza gli otto flussi di sensori disponibili in modalità ricerca*

## <a name="usage"></a>Utilizzo

La modalità di ricerca è progettata per ricercatori accademici e industriali che esplorano nuove idee nei campi di Visione artificiale e robotica.  Non è destinata alle applicazioni distribuite in ambienti aziendali o disponibili tramite il Microsoft Store o altri canali di distribuzione.

Inoltre, Microsoft non garantisce che la modalità di ricerca o la funzionalità equivalente verrà supportata negli aggiornamenti futuri dell'hardware o del sistema operativo. Tuttavia, ciò non impedisce di usarlo per sviluppare e testare nuove idee.

## <a name="security-and-performance"></a>Sicurezza e prestazioni

Tenere presente che l'abilitazione della modalità di ricerca usa più potenza della batteria rispetto all'uso di HoloLens 2 in condizioni normali. Questo vale anche se l'applicazione che usa le funzionalità della modalità di ricerca non è in esecuzione.  L'abilitazione di questa modalità può anche ridurre la sicurezza complessiva del dispositivo perché le applicazioni possono usare i dati del sensore in modo errato.  Altre informazioni sulla sicurezza del dispositivo sono disponibili nelle [domande frequenti sulla sicurezza di HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).  

## <a name="device-support"></a>Supporto di dispositivi
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>Fotocamere di rilevamento Head</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Profondità & fotocamera IR</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Accelerometro</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Giroscopio</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Magnetometro</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a>Abilitazione della modalità di ricerca (HoloLens 1 gen e HoloLens 2)

La modalità di ricerca è un'estensione della modalità sviluppatore. Prima di iniziare, è necessario abilitare le funzionalità di sviluppo del dispositivo per accedere alle impostazioni della modalità di ricerca: 

* Aprire il **menu Start > impostazioni** e selezionare **aggiornamenti**.
* Selezionare **per gli sviluppatori** e abilitare la **modalità sviluppatore**.
* Scorri verso il basso e abilita **Portale dispositivi**.

Una volta abilitate le funzionalità per gli sviluppatori, [connettersi al portale del dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) per abilitare le funzionalità della modalità di ricerca:

* Passare alla **modalità di ricerca di System >** nel **portale del dispositivo**.
* Selezionare **Consenti accesso al flusso del sensore**.
* Riavviare il dispositivo dalla voce del menu **Power** nella parte superiore della pagina.

Dopo aver riavviato il dispositivo, le applicazioni caricate tramite il **portale** per i dispositivi possono accedere ai flussi della modalità di ricerca.

![Scheda modalità ricerca del portale per dispositivi HoloLens](images/ResearchModeDevPortal.png)<br>
*Finestra modalità di ricerca nel portale per dispositivi HoloLens*

> [!IMPORTANT]
> La modalità di ricerca per HoloLens 2 è disponibile a partire dalla Build 19041,1356. Se è necessario accedere a una build precedente, iscriversi al programma di [Anteprima di insider](https://docs.microsoft.com/hololens/hololens-insider) .

### <a name="using-sensor-data-in-your-apps"></a>Uso dei dati dei sensori nelle app

Le applicazioni possono accedere ai dati del flusso dei sensori nello stesso modo in cui si accede ai flussi della fotocamera e della foto tramite [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197). 

Tutte le API che funzionano per lo sviluppo di HoloLens sono disponibili anche in modalità ricerca. In particolare, l'applicazione conosce esattamente dove HoloLens si trova nello spazio 6DoF a ogni tempo di acquisizione del fotogramma del sensore.

È possibile trovare applicazioni di esempio su come accedere ai vari flussi in modalità di ricerca, su come usare le [funzioni intrinseche e i dati estrinseci](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e su come registrare i flussi nel repository di [repository GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .

 > [!NOTE]
 > A questo punto, l'esempio HoloLensForCV non funziona in HoloLens 2.

## <a name="support"></a>Supporto

Usare lo strumento di [rilevamento dei problemi](https://github.com/Microsoft/HololensForCV/issues) nel repository HoloLensForCV per inviare commenti e suggerimenti e rilevare i problemi noti.

## <a name="see-also"></a>Vedi anche

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repository GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Avviare il Portale di dispositivi di Windows](using-the-windows-device-portal.md)
