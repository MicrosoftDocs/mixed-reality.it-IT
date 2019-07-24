---
title: Uso di XAML con app DirectX olografiche
description: Illustra l'effetto del cambio tra visualizzazioni XAML 2D e visualizzazioni immersive nell'app DirectX e come usare in modo efficiente sia una visualizzazione XAML che una visualizzazione immersiva.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: realtà mista di Windows, UWP, gestione visualizzazione App, XAML, tastiera, procedura dettagliata, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548707"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Uso di XAML con app DirectX olografiche

Questo argomento illustra l'effetto del cambio tra [visualizzazioni XAML 2D e viste immersive](app-views.md) nell'app DirectX e come usare in modo efficiente sia una visualizzazione XAML che una visualizzazione immersiva.

## <a name="xaml-view-switching-overview"></a>Panoramica sul cambio di visualizzazione XAML

In HoloLens, un'app in genere immersiva che può visualizzare in seguito una visualizzazione XAML 2D deve inizializzare prima la visualizzazione XAML e passare immediatamente a una visualizzazione immersiva. Questo significa che XAML verrà caricato prima che l'app possa eseguire qualsiasi operazione. Di conseguenza, si verifica un piccolo aumento del tempo di avvio e XAML continuerà a occupare lo spazio di memoria nel processo dell'app mentre risiede in background; la quantità di ritardo di avvio e di utilizzo della memoria dipende dalle operazioni svolte dall'app con XAML prima di passare alla visualizzazione nativa. Se non si esegue alcuna operazione nel codice di avvio XAML inizialmente, eccetto avviare la visualizzazione immersiva, l'effetto dovrebbe essere minore. Inoltre, poiché il rendering olografico viene eseguito direttamente nella visualizzazione immersiva, si eviteranno eventuali restrizioni correlate a XAML su tale rendering.

Si noti che i conteggi di utilizzo della memoria per CPU e GPU. Direct3D 11 è in grado di scambiare memoria grafica virtuale, ma potrebbe non essere in grado di scambiare alcune o tutte le risorse GPU XAML e potrebbe essersi verificato un notevole impatto sulle prestazioni. In entrambi i casi, se non si caricano funzionalità XAML non necessarie, non sarà più disponibile una maggiore quantità di spazio per l'app e sarà possibile migliorare l'esperienza.

## <a name="xaml-view-switching-workflow"></a>Flusso di lavoro cambio visualizzazione XAML

Il flusso di lavoro per un'app che passa direttamente da XAML alla modalità immersiva è simile al seguente:
* L'app viene avviata nella visualizzazione XAML 2D.
* La sequenza di avvio XAML dell'app rileva se il sistema corrente supporta il rendering olografico:
* In tal caso, l'app crea la visualizzazione immersiva e la porta immediatamente in primo piano. Il caricamento XAML viene ignorato per tutto ciò che non è necessario nei dispositivi di realtà mista di Windows, incluse le classi di rendering e il caricamento di asset nella visualizzazione XAML. Se l'app usa XAML per l'input da tastiera, è comunque necessario creare la pagina di input.
* In caso contrario, la visualizzazione XAML può procedere normalmente con le aziende.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Suggerimento per il rendering di elementi grafici in entrambe le visualizzazioni

Se l'app deve implementare una certa quantità di rendering in DirectX per la visualizzazione XAML in realtà mista di Windows, la scommessa migliore consiste nel creare un renderer che può funzionare con entrambe le visualizzazioni. Il renderer deve essere un'istanza a cui è possibile accedere da entrambe le visualizzazioni e deve essere in grado di passare dal rendering 2D a quello olografico. In questo modo, gli asset GPU vengono caricati solo una volta, riducendo i tempi di caricamento, l'effetto della memoria e la quantità di risorse da scambiare durante il cambio di visualizzazione.
