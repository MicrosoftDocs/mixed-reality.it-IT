---
title: Usare HoloLens in nuovi spazi
description: HoloLens apprende l'aspetto di uno spazio nel tempo. Gli utenti possono semplificare questo processo spostando il HoloLens in determinati modi attraverso lo spazio.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Realtà mista di Windows, progettazione, mapping spaziale, HoloLens, ricostruzione di superficie, mesh, rilevamento Head, mapping
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566020"
---
# <a name="use-hololens-in-new-spaces"></a>Usare HoloLens in nuovi spazi

HoloLens *esegue il mapping*o apprende le informazioni relative all'ambiente quando l'utente si sposta su uno spazio. Nel corso del tempo, il HoloLens crea una *mappa spaziale* di tutte le parti dell'ambiente che sono state osservate. HoloLens aggiorna la mappa in modo che vengano osservate le modifiche nell'ambiente. Questa analisi verrà mantenute automaticamente tra i lanci dell'app.

HoloLens creerà e aggiornerà le mappe fino a quando il dispositivo è acceso e un utente è connesso. Se si tiene o si indossa il dispositivo con le fotocamere puntate a uno spazio, il dispositivo tenterà di eseguire il mapping dell'area. Sebbene il HoloLens apprenda uno spazio naturalmente nel tempo, sono disponibili suggerimenti e consigli per eseguire il mapping dello spazio in modo più rapido ed efficiente. 

Se il HoloLens non è in grado di eseguire il mapping dello spazio o non è disponibile, è possibile attivare la modalità Limited. In modalità limitata, non sarà possibile posizionare gli ologrammi nell'ambiente in uso.

## <a name="tips-and-tricks-for-mapping-spaces"></a>Suggerimenti e consigli per gli spazi di mapping

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a>Verificare che lo spazio sia configurato per la realtà mista

Le funzionalità in un ambiente possono rendere difficile per HoloLens interpretare uno spazio. I livelli leggeri, i materiali nello spazio, il layout degli oggetti e altro ancora possono influire sul modo in cui HoloLens esegue il mapping di un'area.

Suggerimenti per la configurazione dello spazio per HoloLens e altri dispositivi a realtà mista sono disponibili in [considerazioni sull'ambiente per HoloLens](environment-considerations-for-hololens.md).

### <a name="understand-the-scenarios-for-the-area"></a>Informazioni sugli scenari per l'area

È importante dedicare la maggior parte del tempo in cui si utilizzerà il HoloLens in modo che la mappa sia pertinente e completa. 

Se, ad esempio, uno scenario utente per HoloLens prevede lo spostamento dal punto A al punto B, passare a tale percorso due o tre volte, esaminando tutte le direzioni mentre si sposta. 

### <a name="walk-slowly-around-the-space"></a>Scorrere lentamente intorno allo spazio

Se si cammina troppo rapidamente intorno all'area, è probabile che il HoloLens non perda le aree di mapping. Esaminare lentamente lo spazio, arrestando ogni 5-8 metri di distanza per esplorare l'ambiente in uso.

I movimenti uniformi aiutano anche il HoloLens mappare più effeciently.

### <a name="look-in-all-directions"></a>Cerca in tutte le direzioni

Quando si esegue il mapping dello spazio, il HoloLens offre più dati su cui i punti sono relativi tra loro. 

Se non si cerca, ad esempio, il HoloLens potrebbe non essere in grado di individuare la posizione in cui si trova il limite massimo in una stanza. 

Quando si esegue il mapping dello spazio, non dimenticare di esaminare la superficie.

### <a name="cover-key-areas-multiple-times"></a>Aree principali di copertura più volte

Spostarsi più volte in un'area consente di prelevare le funzionalità che potrebbero mancare nella prima procedura dettagliata. Provare a attraversare un'area da due a tre volte per creare una mappa ideale.

Se possibile, durante la ripetizione di questi movimenti, dedicare tempo a esplorare un'area in una direzione, quindi a tornare indietro nel modo in cui si è arrivati.

### <a name="take-your-time-mapping-the-area"></a>Eseguire il mapping del tempo all'area

Possono essere necessari tra 15 e 20 minuti affinché il HoloLens sia completamente mappato e si adatta ai propri dintorni. Se si dispone di uno spazio in cui si prevede di usare un HoloLens di frequente, il tempo necessario per eseguire il mapping dello spazio può impedire problemi in un secondo momento. 

## <a name="possible-errors-in-the-spatial-map"></a>Possibili errori nella mappa spaziale

Gli errori nei dati di mapping spaziale rientrano in una delle tre categorie seguenti:

* *Buchi*: Nei dati di mapping spaziale mancano le superfici reali.
* *Allucinazioni*: Le superfici sono presenti nei dati di mapping spaziali che non esistono nel mondo reale.
* *Wormhole*: HoloLens "perde" parte della mappa spaziale pensando che si trovi in una parte diversa della mappa rispetto al fatto.
* *Distorsione*: Le superfici nei dati di mapping spaziale sono allineate in modo non perfetto con le superfici reali, spostate o estratte.

Molti di questi errori possono essere attenuati eliminando gli [ologrammi](environment-considerations-for-hololens.md) ed eseguendo di nuovo il mapping dello spazio.