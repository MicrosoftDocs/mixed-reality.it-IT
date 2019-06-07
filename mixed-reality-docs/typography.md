---
title: Tipografia
description: Il testo è un elemento importante per la distribuzione di informazioni durante l'utilizzo di app.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, lo stile, del tipo di carattere, tipografia, dell'interfaccia utente, esperienza utente
ms.openlocfilehash: 6371aa9b12b61d12acdaaae5f7730ff2ae9757f0
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750343"
---
# <a name="typography"></a>Tipografia

Il testo è un elemento importante per la distribuzione di informazioni durante l'utilizzo di app. Proprio come tipografia nelle schermate 2D, l'obiettivo è sia chiaro e leggibile. Con l'aspetto tridimensionale della realtà mista, è un'opportunità per influire sul testo e l'utente complessiva esperienza in modo ancora più grande.

![Esempio di funzionalità tipografiche di HoloLens](images/typography-cover.png)<br>
*Esempio di funzionalità tipografiche di HoloLens*

Quando si parla di tipo in 3D, Tendiamo a pensare estruso, volumetrico testo 3D. Fatta eccezione per alcune progettazioni logotipo e diverse altre applicazioni limitate, testo estruso tende a diminuire la leggibilità del testo. Anche se è in fase di progettazione esperienze per 3D, utilizziamo 2D per il tipo perché è più leggibile e facile da leggere.

In HoloLens, tipo viene costruito con vntana usando la luce in base al sistema di colore sommano tra loro. Esattamente come altri vntana tipo può essere inserito nell'ambiente effettivo in cui sia possibile world bloccato e osservate da qualsiasi angolazione. Il [parallasse](https://en.wikipedia.org/wiki/Parallax) effetto tra il tipo e l'ambiente aggiunge inoltre profondità all'esperienza.

## <a name="typography-in-mixed-reality"></a>Funzionalità tipografiche di realtà mista

Regole tipografiche nella realtà mista non sono diverse da qualsiasi altra posizione. Il testo nel mondo fisico e il mondo virtuale deve essere leggibile e leggibile. Il testo può essere su una parete o sovrapposte su un oggetto fisico. Potrebbe essere mobile insieme a un'interfaccia utente digitale. Indipendentemente dal contesto, abbiamo si applicano le stesse regole tipografiche per la lettura e il riconoscimento.

### <a name="create-clear-hierarchy"></a>Creare la gerarchia non crittografata

Compilare a contrasto elevato e la gerarchia usando i pesi e le dimensioni di tipo diverso. La definizione di una rampa di tipo e la seguono in tutta l'esperienza delle app offrirà un'esperienza utente eccezionale con gerarchia informazioni coerenti.

![Esempi di tipi di preparazione](images/typography-ramp-1000px.jpg)<br>
*Definire la preparazione di tipo prima e nell'intera esperienza di app*

### <a name="limit-your-fonts"></a>Limitare i tipi di carattere

Evitare di usare più di due famiglie di caratteri diversi in un contesto singolo. Verrà interrompere l'armonia e la coerenza dell'esperienza e rendere più difficile la fruizione delle informazioni. In HoloLens, poiché le informazioni viene sovrapposto all'inizio l'ambiente fisico, usando gli stili dei caratteri troppi diminuirà l'esperienza. Segoe UI è il tipo di carattere per tutte le progettazioni digitali di Microsoft. Viene usato in modo coerente nella shell di realtà mista di Windows. È possibile scaricare il file del tipo di carattere Segoe UI dal [pagina toolkit di progettazione Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Altre informazioni sul carattere tipografico Segoe UI](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evitare i pesi del tipo di carattere thin

Evitare di utilizzare pesi chiaro o semilight del tipo di carattere per le dimensioni di tipo in 42pt poiché i tratti verticali sottili verranno vibrazione e influire negativamente sulla leggibilità. Tipi di carattere moderni con sufficiente lo spessore del tratto funziona correttamente. Ad esempio, Helvetica e Arial sono molto leggibile in HoloLens vengono usati pesi regolari o in grassetto.

### <a name="color"></a>Colore

In HoloLens, poiché il vntana viene costruiti con un sistema leggero sommano tra loro, è altamente leggibile testo bianco. È possibile trovare esempi di testo bianco su menu Start e barra dell'App. Anche se il testo bianco funziona anche senza un piatto indietro su HoloLens, uno sfondo fisico complesso potrebbe rendere il tipo difficili da leggere. Per migliorare lo stato attivo dell'utente e ridurre al minimo la distrazione da uno sfondo fisico, è consigliabile usare testo bianco su un piatto colorato nuovamente o scuro.

<br>


![È consigliabile usare testo bianco su un piatto indietro scuro o colorato. ](images/typography-whiteonblack2-1000px.jpg)
 *Esempi di testo bianco su un piatto indietro scuro o colorato.*
<br>

Per utilizzare testo scuro, è necessario utilizzare un vivace piatto back-per renderlo leggibile. Nei sistemi di addizione colore nero viene visualizzato come trasparente. Ciò significa che non sarà in grado di visualizzare il testo di colore nero senza colorate di eseguire il piatto.

![Esempi di testo di colore nero](images/typography-whiteonblack.png)
<br>*Esempi di bianco su back e nero con testo bianco*


![Esempi di testo di colore nero](images/640px-typography-blackonwhite.jpg)
<br>*Esempi di testo di colore nero nelle app di sistema - Store e le impostazioni*

## <a name="recommended-font-size"></a>Dimensione del carattere consigliato

Come si può immaginare, le dimensioni di tipo che viene usato in un PC o un dispositivo Tablet PC (in genere compresa tra 12: 32 pt) esaminare risulta piuttosto piccole una distanza massima 2 metri. Dipende dalle caratteristiche di ogni tipo di carattere, ma sono in genere quello minimo consigliato visualizzazione angolo e l'altezza dei caratteri per migliorare la leggibilità intorno 0.35°-0.4°/12.21-13.97mm basato sul nostro ricerche su utente. Si tratta di 35 40pt con il fattore di scala introdotta in [testo in Unity](text-in-unity.md) pagina. 

Per l'interazione quasi in 0.45m(45cm), angolo di visualizzazione minima leggibile del tipo di carattere e l'altezza sono 0.4 °-0,5 ° / 3.14-3.9 mm. Si tratta di 9 a 12 pt con il fattore di scala introdotta in [testo in Unity](text-in-unity.md).

![Più vicino e lontano intervallo interazione](images/typography-distance-1000px.jpg)
*intervallo contenuto in vicino e lontano interazione*

### <a name="the-minimum-legible-font-size"></a>Le dimensioni minime del carattere leggibili
| distanza | Angolo di visualizzazione | Altezza del testo | Le dimensioni del carattere * * |
|---------|---------|---------|---------|
| 45cm (distanza manipolazione diretta) | 0.4°-0.5° | 3.14-3.9 mm | 8.9 – 11.13pt |
| 2 minuti | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>Le dimensioni del carattere facilmente leggibili
| distanza | Angolo di visualizzazione | Altezza del testo | Le dimensioni del carattere * * |
|---------|---------|---------|---------|
| 45cm (distanza manipolazione diretta) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8pt |
| 2 minuti | 0.6°-0.75° | 20,9-26,2 mm | hanno raggiunto 59,4-74.2pt |


Segoe UI (tipo di carattere predefinito per Windows) funziona bene nella maggior parte dei casi. Tuttavia, evitare di usare light o semi chiaro famiglie di caratteri di piccole dimensioni poiché verranno vibrazione tratti verticali sottili e avrà alcun effetto di migliorare la leggibilità. Tipi di carattere moderni con sufficiente lo spessore del tratto funziona correttamente. Ad esempio, Helvetica e Arial aspetto ricche e sono molto leggibile in HoloLens con regolari o in grassetto.

* * Per ulteriori informazioni sul calcolo delle dimensioni del testo in Unity, fare riferimento alla pagina [testo in Unity](text-in-unity.md)

![Angolo di visualizzazione](images/Text_In_Unity_ViewingAngle.jpg)
*visualizzazione altezza distanza angolo e testo*

## <a name="resources"></a>Risorse
* [Tipi di carattere Segoe](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [Tipo di carattere HoloLens](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![Il tipo di carattere HoloLens ti offre i glifi di simbolo usati in realtà mista di Windows](images/300px-hololensmdl2symbols.jpg)
<br>*Il tipo di carattere HoloLens offre i glifi di simbolo usati in realtà mista di Windows.*

## <a name="see-also"></a>Vedere anche
* [Testo in Unity](text-in-unity.md)
* [Colore, luce e materiali](color,-light-and-materials.md)
