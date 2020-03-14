---
title: Tipografia
description: Il testo è un elemento importante per la distribuzione di informazioni nell'esperienza dell'app.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Realtà mista di Windows, progettazione, stile, carattere, tipografia, interfaccia utente, UX
ms.openlocfilehash: 9664d355e941d800ac1ac862860fc5889b6b7686
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375798"
---
# <a name="typography"></a>Tipografia

![Esempio di tipografia in HoloLens](images/typography-cover.png)<br>


Il testo è un elemento importante per la distribuzione di informazioni nell'esperienza dell'app. Proprio come per la tipografia su schermi 2D, l'obiettivo è chiarezza e leggibilità. Grazie all'aspetto tridimensionale della realtà mista, è possibile influire sul testo e sull'esperienza utente complessiva in modo ancora più significativo.

Quando si parla di tipo in 3D, si tende a pensare a testo 3D estruso e volumetrico. Fatta eccezione per alcune progettazioni di logotipi e altre applicazioni limitate, il testo estruso tende a ridurre la leggibilità del testo. Anche se stiamo progettando esperienze per 3D, usiamo 2D per il tipo perché è più leggibile e più facile da leggere.

In HoloLens, il tipo viene costruito con ologrammi usando la luce basata sul sistema di colori additivi. Analogamente ad altri ologrammi, il tipo può essere posizionato nell'ambiente effettivo, dove può essere bloccato e osservato da qualsiasi angolo. L'effetto di [parallasse](https://en.wikipedia.org/wiki/Parallax) tra il tipo e l'ambiente aggiunge anche profondità all'esperienza.

## <a name="typography-in-mixed-reality"></a>Tipografia in realtà mista

Le regole tipografiche in realtà mista non sono diverse da qualsiasi altra posizione. Il testo nel mondo fisico e nel mondo virtuale deve essere leggibile e leggibile. Il testo potrebbe trovarsi su una parete o sovrapposto a un oggetto fisico. Potrebbe essere mobile insieme a un'interfaccia utente digitale. Indipendentemente dal contesto, si applicano le stesse regole tipografiche per la lettura e il riconoscimento.

### <a name="create-clear-hierarchy"></a>Crea gerarchia chiara

Contrasto e gerarchia di compilazione utilizzando dimensioni e pesi diversi per i tipi. La definizione di una rampa di tipo e la successiva esperienza nell'app offriranno un'esperienza utente ottimale con una gerarchia di informazioni coerenti.

esempi di ![di tipo ramp](images/typography-ramp-1000px.jpg)<br>
*Definire la rampa di tipo e seguirla in tutta l'esperienza dell'app*

### <a name="limit-your-fonts"></a>Limitare i tipi di carattere

Evitare di usare più di due famiglie di caratteri diverse in un unico contesto. In questo modo si interromperà l'armonia e la coerenza dell'esperienza e si renderà più difficile l'utilizzo delle informazioni. In HoloLens, poiché le informazioni sono sovrapposte all'ambiente fisico, l'utilizzo di un numero eccessivo di stili dei tipi di carattere comporta un peggioramento dell'esperienza. Segoe UI è il tipo di carattere per tutti i progetti digitali Microsoft. Viene usato in modo coerente nella shell della realtà mista di Windows. È possibile scaricare il file del tipo di carattere Segoe UI dalla [pagina Windows Design Toolkit](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Ulteriori informazioni sul carattere tipografico Segoe UI](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evitare i pesi del carattere sottile

Evitare di usare i pesi per i tipi di carattere chiaro o Semilight per le dimensioni dei tipi in essere, poiché i tratti verticali sottili comportano vibrazioni e riducono la leggibilità I tipi di carattere moderni con uno spessore del tratto sufficiente funzionano correttamente. Ad esempio, Helvetica e Arial sono molto leggibili in HoloLens usando pesi regolari o in grassetto.

### <a name="color"></a>Colore

In HoloLens, poiché gli ologrammi vengono costruiti con un sistema di luce additiva, il testo bianco è altamente leggibile. È possibile trovare esempi di testo bianco nel menu Start e nella barra dell'app. Anche se il testo bianco funziona bene senza una piastra posteriore in HoloLens, un background fisico complesso potrebbe rendere difficile la lettura del tipo. Per migliorare l'attenzione dell'utente e ridurre al minimo la distrazione da uno sfondo fisico, è consigliabile usare un testo bianco su un pannello scuro o colorato.

<br>


![si consiglia di usare testo bianco su un pannello posteriore scuro o colorato.](images/typography-whiteonblack2-1000px.jpg)
*esempi di testo bianco su un pannello posteriore scuro o colorato.*
<br>

Per usare testo scuro, è necessario usare una piastra indietro luminosa per renderla leggibile. Nei sistemi di colori additivi, il nero viene visualizzato come trasparente. Ciò significa che non sarà possibile visualizzare il testo nero senza una piastra posteriore colorata.

:::row:::
    :::column:::
        ![esempi di testo nero](images/typography-whiteonblack.png)<br>
        *Esempi di bianco su nero e nero su testo bianco*<br>
    :::column-end:::
    :::column:::
        ![esempi di testo nero](images/640px-typography-blackonwhite.jpg)<br>
        *Esempi di testo nero nelle app di sistema-archivio e impostazioni*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>Dimensioni del carattere consigliate

Come si può immaginare, i tipi di dimensioni usati in un PC o un Tablet (in genere tra 12-32pt) sembrano abbastanza piccoli a una distanza di 2 metri. Dipende dalle caratteristiche di ogni tipo di carattere, ma in generale l'angolo di visualizzazione minimo consigliato e l'altezza del tipo di carattere per la leggibilità sono circa 0,35 °-0,4 °/12.21-13.97mm in base agli studi di ricerca degli utenti. È pari a circa 35 40pt con il fattore di scalabilità introdotto nel [testo nella pagina Unity](text-in-unity.md) . 

Per l'interazione near a 0,45 m (45 cm), l'angolo di visualizzazione del tipo di carattere leggibile minimo e l'altezza sono 0.4 °-0,5 °/3.14 – 3,9 mm. Si tratta di circa 9 12pt con il fattore di scala introdotto nel [testo in Unity](text-in-unity.md).

![intervallo di interazione near and lontano](images/typography-distance-1000px.jpg)
*contenuto nell'intervallo di interazione near and lontano*

### <a name="the-minimum-legible-font-size"></a>Dimensioni minime del carattere leggibili
| Distanza | Angolo di visualizzazione | Altezza testo | Dimensioni carattere * * |
|---------|---------|---------|---------|
| 45 cm (distanza di manipolazione diretta) | 0.4 °-0,5 ° | 3.14 – 3,9 mm | 8,9 – 11.13 PT |
| 2m | 0,35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 PT |


### <a name="the-comfortably-legible-font-size"></a>Dimensioni del carattere facilmente leggibili
| Distanza | Angolo di visualizzazione | Altezza testo | Dimensioni carattere * * |
|---------|---------|---------|---------|
| 45 cm (distanza di manipolazione diretta) | 0,65 °-0,8 ° | 5.1-6,3 mm | 14.47-17,8 PT |
| 2m | 0.6 °-0,75 ° | 20,9-26.2 mm | 59.4-74.2 PT |


Segoe UI (il tipo di carattere predefinito per Windows) funziona correttamente nella maggior parte dei casi. Tuttavia, evitare di usare famiglie di caratteri chiaro o semichiaro in piccole dimensioni poiché i tratti verticali sottili vibrano e diminuiscono la leggibilità. I tipi di carattere moderni con uno spessore del tratto sufficiente funzionano correttamente. Ad esempio, Helvetica e Arial sembrano splendidi e sono molto leggibili in HoloLens con pesi regolari o in grassetto.

**Per informazioni più dettagliate sul calcolo delle dimensioni del testo in Unity, consultare il [testo in Unity](text-in-unity.md)**

Angolo di visualizzazione ![](images/Text_In_Unity_ViewingAngle.jpg)
*visualizzazione della distanza, dell'angolo e dell'altezza del testo*

<br>

---

## <a name="resources"></a>Risorse

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Tipi di carattere Segoe](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (File zip)<br>
    ### <a name="hololens-fontbr"></a>[Tipo di carattere HoloLens](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (File zip)<br>
    <br>
    *Image: il tipo di carattere HoloLens fornisce i glifi dei simboli usati nella realtà mista di Windows.*
    :::column-end:::
        :::column:::
        ![Il tipo di carattere HoloLens fornisce i glifi dei simboli usati nella realtà mista di Windows](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a>Vedere anche
* [Testo in Unity](text-in-unity.md)
* [Colore, luce e materiali](color,-light-and-materials.md)
