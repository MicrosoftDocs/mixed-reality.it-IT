---
title: Visualizzazione analisi chat room
description: Le applicazioni che richiedono dati di mapping spaziali si basano sul dispositivo per raccogliere automaticamente questi dati nel tempo e nelle sessioni mentre l'utente Esplora il proprio ambiente con il dispositivo attivo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, modelli di app, progettazione, HoloLens, analisi chat room, mapping spaziale, ricostruzione superficie, mesh
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829907"
---
# <a name="room-scan-visualization"></a>Visualizzazione analisi chat room

Le applicazioni che richiedono dati di mapping spaziali si basano sul dispositivo per raccogliere automaticamente questi dati nel tempo e nelle sessioni mentre l'utente Esplora il proprio ambiente con il dispositivo attivo. La completezza e la qualità di questi dati dipendono da diversi fattori, tra cui la quantità di esplorazione eseguita dall'utente, il tempo trascorso dall'esplorazione e l'eventuale spostamento degli oggetti, ad esempio mobili e porte, dal momento in cui il dispositivo ha analizzato l'area.

Per garantire dati di mapping spaziali utili, gli sviluppatori di applicazioni dispongono di diverse opzioni:
* Basarsi su ciò che è già stato raccolto. Questi dati potrebbero essere inizialmente incompleti.
* Chiedere all'utente di usare il movimento Bloom per ottenere la Home realtà mista di Windows e quindi esplorare l'area che si vuole usare per l'esperienza. Possono usare il tocco aereo per verificare che tutte le aree necessarie siano note al dispositivo.
* Crea un'esperienza di esplorazione personalizzata nella propria applicazione.

Si noti che in tutti questi casi i dati effettivi raccolti durante l'esplorazione vengono archiviati dal sistema e non è necessario che l'applicazione esegua questa operazione.

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
        <td>Visualizzazione analisi chat room</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Creazione di un'esperienza di analisi personalizzata

Le applicazioni possono decidere di analizzare i dati di mapping spaziali all'inizio dell'esperienza per valutare se desiderano che l'utente esegua ulteriori passaggi per migliorare la sua completezza e qualità. Se l'analisi indica che è necessario migliorare la qualità, gli sviluppatori devono fornire una visualizzazione da sovrapporre al mondo per indicare:
* La quantità di volume totale in prossimità degli utenti deve essere parte integrante dell'esperienza
* Dove l'utente deve passare per migliorare i dati

Gli utenti non sono a conoscenza di ciò che fa un'analisi "positiva". È necessario visualizzare o indicare gli elementi da cercare se viene chiesto di valutare un'analisi, ovvero la planarità, la distanza dai muri effettivi e così via. Lo sviluppatore deve implementare un ciclo di feedback che includa l'aggiornamento dei dati di mapping spaziale durante la fase di analisi o di esplorazione.

In molti casi, può essere preferibile informare l'utente di cosa è necessario fare (ad esempio, osservare il soffitto, guardare dietro la mobilia), per ottenere la qualità di analisi necessaria.

## <a name="cached-versus-continuous-spatial-mapping"></a>Memorizzazione nella cache rispetto al mapping spaziale continuo

I dati di mapping spaziali sono le applicazioni che possono essere utilizzate dalle applicazioni di origine dati con maggiore peso. Per evitare problemi di prestazioni, ad esempio i frame eliminati o la balbuzie, l'utilizzo di questi dati deve essere eseguito con cautela.

L'analisi attiva durante un'esperienza può essere utile o dannosa e lo sviluppatore dovrà decidere quale metodo utilizzare in base all'esperienza.

### <a name="cached-spatial-mapping"></a>Mapping spaziale memorizzato nella cache

Nel caso del mapping spaziale memorizzato nella cache, l'applicazione esegue in genere uno snapshot dei dati di mapping spaziali e utilizza questo snapshot per la durata dell'esperienza.

**Vantaggi**
* Riduzione del sovraccarico sul sistema durante l'esecuzione dell'esperienza con un notevole miglioramento delle prestazioni, della temperatura e della CPU.
* Un'implementazione più semplice dell'esperienza principale, poiché non viene interrotta dalle modifiche nei dati spaziali.
* Costo singolo per ogni post elaborazione dei dati spaziali per la fisica, la grafica e altri scopi.

**Svantaggi**
* Lo spostamento di oggetti o persone reali non viene riflesso dai dati memorizzati nella cache. ad esempio è possibile che l'applicazione prenda in considerazione uno sportello aperto quando viene effettivamente chiuso.
* Potenzialmente più memoria dell'applicazione per mantenere la versione memorizzata nella cache dei dati.

Un caso valido per questo metodo è un ambiente controllato o una tabella Top Game.

### <a name="continuous-spatial-mapping"></a>Mapping spaziale continuo

Alcune applicazioni possono basarsi sull'analisi continua per aggiornare i dati di mapping spaziali.

**Vantaggi**
* Non è necessario creare un'esperienza di analisi o esplorazione separata in anticipo nell'applicazione.
* Lo spostamento di oggetti reali può essere riflesso dal gioco, anche se con un certo ritardo.

**Svantaggi**
* Maggiore complessità nell'implementazione dell'esperienza principale.
* Potenziale sovraccarico dell'elaborazione aggiuntiva per la grafica o la fisica, in quanto le modifiche devono essere inserite in modo incrementale da questi sistemi.
* Maggiore potenza, temperatura e effetti sulla CPU.

Un caso ideale per questo metodo è quello in cui gli ologrammi devono interagire con gli oggetti mobili, ad esempio, un'automobile olografica che può inserirsi in uno sportello a seconda che sia aperta o chiusa.

## <a name="see-also"></a>Vedere anche
* [Progettazione del mapping spaziale](spatial-mapping-design.md)
* [Sistemi di coordinate](coordinate-systems.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
