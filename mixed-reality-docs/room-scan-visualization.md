---
title: Visualizzazione analisi chat room
description: Le applicazioni che richiedono i dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente i dati nel tempo e tra le sessioni dell'utente esamina il proprio ambiente con il dispositivo attivo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, i modelli dell'App, la progettazione, HoloLens, analisi di chat, spaziali mapping, surface, ricostruzione mesh
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829907"
---
# <a name="room-scan-visualization"></a>Visualizzazione analisi chat room

Le applicazioni che richiedono i dati di mapping spaziale si basano sul dispositivo per raccogliere automaticamente i dati nel tempo e tra le sessioni dell'utente esamina il proprio ambiente con il dispositivo attivo. La completezza e la qualità dei dati dipende da diversi fattori tra cui la quantità di esplorazione che l'utente ha eseguito, quanto tempo è trascorso l'esplorazione e se gli oggetti, ad esempio le porte e mobili hanno spostata dal momento che il dispositivo analizzato l'area.

Per assicurarsi che i dati di mapping spaziale utili, gli sviluppatori di applicazioni dispongono diverse opzioni:
* Si basano su ciò che potrebbe già raccolti. Inizialmente, i dati potrebbero essere incompleti.
* Chiedere all'utente di usare il movimento bloom per ottenere in Windows Mixed Reality casa e poi ne esplorerò l'area in cui che si vuole usare per l'esperienza. Usano indice puntato per confermare che tutta l'area necessario sia note al dispositivo.
* Creare un'esperienza di esplorazione personalizzata nelle proprie applicazioni.

Si noti che in tutti questi casi i dati effettivi raccolti durante l'esplorazione vengano memorizzati dal sistema e l'applicazione non è necessario eseguire questa operazione.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Visualizzazione analisi chat room</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Creazione di un'esperienza di analisi personalizzata

Le applicazioni possono decidere di analizzare i dati di mapping spaziale all'inizio dell'esperienza per giudicare se desiderano all'utente di eseguire passaggi aggiuntivi per migliorare la qualità e la completezza. Se analisi indicano che occorre migliorare qualità, gli sviluppatori devono fornire una visualizzazione a sovrapposizione nel mondo per indicare:
* In che misura il volume totale in prossimità degli utenti deve far parte dell'esperienza
* In cui l'utente deve passare per migliorare i dati

Gli utenti non conosce ciò che rende un'analisi "good". Devono essere visualizzato o indicato cosa cercare se viene chiesto di valutazione di un'analisi – appiattimento, distanza dal pareti effettive, e così via. Lo sviluppatore deve implementare un ciclo di feedback che include l'aggiornamento dei dati di mapping spaziale durante la fase di analisi o esplorazione.

In molti casi, potrebbe essere preferibile informare l'utente ne servano per (ad esempio, esaminare il tetto massimo, cercare dietro mobili), per ottenere la qualità di analisi necessarie.

## <a name="cached-versus-continuous-spatial-mapping"></a>Memorizzato nella cache rispetto a continuo mapping spaziale

I dati di mapping spaziale sono il peso più elevato possono utilizzare le applicazioni di origine dati. Per evitare problemi di prestazioni, ad esempio fotogrammi rimossi o stuttering, il consumo dei dati deve essere eseguito con attenzione.

La scansione attiva durante un'esperienza può essere sia utile o effetti negativi sulla e lo sviluppatore avrà bisogno decidere quale metodo utilizzare basati sull'esperienza.

### <a name="cached-spatial-mapping"></a>Mapping spaziale memorizzato nella cache

Nel caso di mapping spaziale memorizzato nella cache, l'applicazione in genere uno snapshot dei dati di mapping spaziale e Usa questo snapshot per la durata dell'esperienza.

**Vantaggi**
* Ridotto il sovraccarico del sistema durante l'esperienza di esecuzione iniziale alla sostanziale potenza, termico e miglioramento delle prestazioni della cpu.
* Un'implementazione più semplice dell'esperienza di principale, dal momento che non venga interrotto dalle modifiche apportate ai dati spaziali.
* Un singolo momento i costi qualsiasi post-elaborazione dei dati spaziali per altri scopi, grafica ed effetti fisici.

**Svantaggi**
* Lo spostamento di oggetti reali o persone che non si riflette in base ai dati memorizzati nella cache. Ad esempio l'applicazione potrebbe prendere in considerazione lo sportello di un'aperta quando è effettivamente chiusa ora.
* Potenzialmente più memoria dell'applicazione per gestire la versione memorizzata nella cache dei dati.

Un buon caso per questo metodo è un ambiente controllato o un gioco tabella principale.

### <a name="continuous-spatial-mapping"></a>Mapping spaziale continuo

Alcune applicazioni possono basarsi via prosegue l'analisi per aggiornare i dati di mapping spaziale.

**Vantaggi**
* Non è necessario compilare un' separato la scansione o l'esplorazione esperienza costo anticipato nell'applicazione.
* Lo spostamento di oggetti reali può essere ottenuto mediante reflection da gioco, sebbene con un ritardo.

**Svantaggi**
* Maggiore complessità nell'implementazione dell'esperienza di principale.
* Potenziale sovraccarico dell'elaborazione aggiuntiva per l'elemento grafico o fisica come modifiche devono essere inseriti in modo incrementale da questi sistemi.
* Una capacità superiore, termico e impatto sulla CPU.

Un buon caso per questo metodo è uno in cui è previsti vntana per interagire con lo spostamento di oggetti, ad esempio, un'automobile holographic unità sul pavimento potrebbe voler correttamente si incorra nello sportello di una se è aperto o chiuso.

## <a name="see-also"></a>Vedere anche
* [Progettazione del mapping spaziale](spatial-mapping-design.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
