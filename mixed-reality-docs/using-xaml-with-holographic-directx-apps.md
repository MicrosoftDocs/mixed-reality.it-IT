---
title: Uso di XAML con holographic nelle App DirectX
description: Viene illustrato l'impatto del passaggio tra le visualizzazioni XAML 2D e coinvolgenti visualizzazioni nelle app DirectX e su come usare un XAML visualizzazione sia coinvolgente e concreto al meglio.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: app per realtà mista, UWP, Windows Visualizza gestione, xaml, tastiera, la procedura dettagliata, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598683"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Uso di XAML con holographic nelle App DirectX

Questo argomento viene illustrato l'impatto del passaggio tra [2D visualizzazioni XAML e coinvolgenti](app-views.md) nelle app DirectX e su come usare un XAML visualizzazione sia coinvolgente e concreto al meglio.

## <a name="xaml-view-switching-overview"></a>Visualizzazione XAML il passaggio di panoramica

Su HoloLens, un'app immersiva a livello generale che può in seguito una visualizzazione 2D XAML deve inizializzare innanzitutto tale visualizzazione XAML e tornare immediatamente a una vista coinvolgente da tale posizione. Ciò significa che verrà caricato XAML prima che l'app può eseguire alcuna operazione. Di conseguenza, sarà presente un piccolo aumento il tempo di avvio e XAML continueranno a occupare lo spazio di memoria nel processo di app, mentre questo risiede in background. la quantità di memoria utilizzo varia a seconda che la tua applicazione e ritardo di avvio non con XAML prima di passare alla visualizzazione nativa. Se non si interviene nel codice all'inizio con la differenza, avviare la vista coinvolgente di avvio di XAML, l'impatto dovrebbe essere minore. Inoltre, poiché viene effettuato il rendering holographic direttamente alla vista coinvolgente e concreto, si eviteranno eventuali restrizioni basate su XAML che per il rendering.

Si noti che l'utilizzo della memoria dati relativi al numero di CPU e GPU. Direct3D 11 è in grado di eseguire lo swapping di memoria grafica virtuale, ma potrebbe non essere in grado di eseguire lo swapping su alcune o tutte le risorse XAML GPU e potrebbe esserci un calo di prestazioni significativo. In entrambi i casi, non il caricamento di tutte le funzionalità XAML non necessari verranno lasciare più spazio per l'app e offrire un'esperienza migliore.

## <a name="xaml-view-switching-workflow"></a>Visualizzazione XAML il passaggio del flusso di lavoro

Il flusso di lavoro per un'app che accede direttamente da XAML in modalità immersive è come segue:
* Avvio dell'app nella visualizzazione XAML 2D.
* Sequenza di avvio dell'app XAML rileva se il sistema corrente supporta il rendering holographic:
* In questo caso, l'app crea la visualizzazione coinvolgente e porta immediatamente in primo piano. Il caricamento di XAML viene ignorato per tutti gli elementi non necessari nei dispositivi di realtà mista di Windows, inclusi eventuali classi di rendering e asset, il caricamento nella visualizzazione XAML. Se l'app Usa XAML per l'input da tastiera, è necessario creare comunque tale pagina di input.
* In caso contrario, la visualizzazione XAML può procedere con business come di consueto.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Suggerimento per il rendering grafica in entrambe le visualizzazioni

Se l'app deve implementare certo livello di rendering in DirectX per la visualizzazione XAML in realtà mista di Windows, la soluzione migliore consiste nel creare un renderer che può funzionare con entrambe le visualizzazioni. Il renderer deve essere un'istanza che è accessibile da entrambe le visualizzazioni e deve essere in grado di passare tra rendering 2D e holographic. In questo modo gli asset GPU vengono caricati solo una volta - questo riduce i tempi di caricamento, impatto della memoria e la quantità di risorse da scambiare quando si passa le visualizzazioni.
