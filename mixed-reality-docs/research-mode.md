---
title: Modalità di ricerca HoloLens
description: Usando la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi dei sensori del dispositivo chiave (profondità, rilevamento dell'ambiente e riflettanza IR).
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: modalità di ricerca, CV, RS4, visione artificiale, ricerca, HoloLens, HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533103"
---
# <a name="hololens-research-mode"></a>Modalità ricerca HoloLens

## <a name="overview"></a>Panoramica

La modalità di ricerca è stata introdotta nella prima generazione HoloLens per consentire l'accesso ai sensori chiave sul dispositivo, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione. È ora possibile raccogliere dati dagli input seguenti:

* **Telecamere di rilevamento dell'ambiente chiaro visibili** : usate dal sistema per il rilevamento Head e la compilazione della mappa.
* **Depth fotocamera** : funziona in due modalità:  
    + Rilevamento a breve termine, ad alta frequenza (30 FPS) usato per il [rilevamento manuale](interaction-fundamentals.md)
    + Rilevamento a lungo termine, a bassa frequenza (1-5 FPS) per un rilevamento approfondito usato dal [mapping spaziale](spatial-mapping.md)
* **Due versioni del flusso IR-riflettività** , usate dal HoloLens per calcolare la profondità. Queste immagini sono illuminate dall'infrarosso e non sono interessate dalla luce visibile dell'ambiente.

Se si usa un HoloLens 2, sarà anche possibile accedere agli input seguenti:

* **Accelerometro** : usato dal sistema per determinare l'accelerazione lineare lungo gli assi X, Y e Z e la gravità.
* **Gyro** : utilizzato dal sistema per determinare le rotazioni.
* **Magnetometro** : utilizzato dal sistema per stimare l'orientamento assoluto.

![Schermata dell'app modalità di ricerca](images/sensor-stream-viewer.jpg)<br>
*Acquisizione di realtà mista di un'applicazione di test che visualizza gli otto flussi di sensori disponibili in modalità ricerca*

> [!NOTE]
> La funzionalità modalità di ricerca è stata aggiunta come parte dell' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md) per HoloLens e non è disponibile nelle versioni precedenti.

## <a name="usage"></a>Uso

La modalità di ricerca è progettata per ricercatori accademici e industriali che esplorano nuove idee nei campi di Visione artificiale e robotica.  Non è destinata alle applicazioni distribuite in ambienti aziendali o disponibili tramite il Microsoft Store o altri canali di distribuzione.

Inoltre, Microsoft non garantisce che la modalità di ricerca o la funzionalità equivalente verrà supportata negli aggiornamenti futuri dell'hardware o del sistema operativo. Tuttavia, ciò non impedisce di usarlo per sviluppare e testare nuove idee.

## <a name="security-and-performance"></a>Sicurezza e prestazioni

Tenere presente che l'abilitazione della modalità di ricerca usa più potenza della batteria rispetto all'uso di HoloLens 2 in condizioni normali. Questo vale anche se l'applicazione che usa le funzionalità della modalità di ricerca non è in esecuzione.  L'abilitazione di questa modalità può anche ridurre la sicurezza complessiva del dispositivo perché le applicazioni possono usare i dati del sensore in modo errato.  Altre informazioni sulla sicurezza del dispositivo sono disponibili nelle [domande frequenti sulla sicurezza di HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).  


## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens 1 gen</strong></a></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td>Fotocamere di rilevamento Head</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Profondità & fotocamera IR</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Accelerometro</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Giroscopio</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Magnetometro</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> Il supporto della modalità di ricerca per HoloLens 2 dovrebbe essere disponibile in versione di anteprima pubblica nel 2020 luglio e includerà tutte le funzionalità elencate in precedenza. Per ulteriori informazioni, consultare nuovamente. 

## <a name="enabling-research-mode"></a>Abilitazione della modalità ricerca

La modalità di ricerca è un'estensione della modalità sviluppatore. Prima di iniziare, è necessario abilitare le funzionalità di sviluppo del dispositivo per accedere alle impostazioni della modalità di ricerca: 

* Aprire il **menu Start > impostazioni** e selezionare **aggiornamenti**.
* Selezionare **per gli sviluppatori** e abilitare la **modalità sviluppatore**.
* Scorrere verso il basso e abilitare il **portale del dispositivo**.

Una volta abilitate le funzionalità per gli sviluppatori, [connettersi al portale del dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) per abilitare le funzionalità della modalità di ricerca.

In *HoloLens 1 gen*:

* Passare alla **modalità di ricerca di System >** nel **portale del dispositivo**.
* Selezionare **Consenti accesso al flusso del sensore**.
* Riavviare il dispositivo dalla voce del menu **Power** nella parte superiore della pagina.

Dopo aver riavviato il dispositivo, le applicazioni caricate tramite il **portale** per i dispositivi possono accedere ai flussi della modalità di ricerca.

![Scheda modalità ricerca del portale per dispositivi HoloLens](images/ResearchModeDevPortal.png)<br>
*Finestra modalità di ricerca nel portale per dispositivi HoloLens*

## <a name="using-sensor-data-in-your-apps"></a>Uso dei dati dei sensori nelle app

*HoloLens 1 gen*

Le applicazioni possono accedere ai dati del flusso dei sensori nello stesso modo in cui si accede ai flussi della fotocamera e della foto tramite [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197). 

Tutte le API che funzionano per lo sviluppo di HoloLens sono disponibili anche in modalità ricerca. In particolare, l'applicazione conosce esattamente dove HoloLens si trova nello spazio 6DoF a ogni tempo di acquisizione del fotogramma del sensore.

È possibile trovare applicazioni di esempio su come accedere ai vari flussi in modalità di ricerca, su come usare le [funzioni intrinseche e i dati estrinseci](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e su come registrare i flussi nel repository di [repository GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .

 > [!NOTE]
 > A questo punto, l'esempio HoloLensForCV non funziona in HoloLens 2.

## <a name="known-issues"></a>Problemi noti

È possibile usare lo strumento di [rilevamento](https://github.com/Microsoft/HololensForCV/issues) dei problemi nel repository HoloLensForCV per seguire i problemi noti.

## <a name="see-also"></a>Vedere anche

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repository GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Avviare il Portale di dispositivi di Windows](using-the-windows-device-portal.md)
