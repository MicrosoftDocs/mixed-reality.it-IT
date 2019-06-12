---
title: Testo in Unity
description: "Per visualizzare il testo in Unity, sono disponibili due tipi di componenti del testo è possibile usare: testo dell'interfaccia utente e della rete di testo 3D."
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Realtà mista di Windows, progettazione, consente di controllare, tipo di carattere, tipografia, dell'interfaccia utente, esperienza utente
ms.openlocfilehash: 7d40db2e0571e835e28e444c7921e1a086800936
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829967"
---
# <a name="text-in-unity"></a>Testo in Unity

Il testo è uno dei principali componenti nelle App holographic. Per visualizzare il testo in Unity, sono disponibili tre tipi di componenti del testo è possibile usare: testo dell'interfaccia utente, maglie 3D testo e testo Mesh Pro. Per impostazione predefinita il testo dell'interfaccia utente e della rete di testo 3D sono sfocati e sono troppo grande. È necessario modificare alcune variabili per ottenere il testo ben strutturato e di alta qualità con una dimensione gestibile in HoloLens. Applicando fattore di scala per ottenere le dimensioni appropriate, quando si usa il testo dell'interfaccia utente e i componenti della rete di testo 3D, è possibile ottenere una migliore qualità di rendering.

![Come ottenere il testo ben strutturato e accattivante](images/hug-text-02-640px.png)<br>
*Testo predefinito sfocati in Unity*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>Utilizzo di testo 3D (testo Mesh) di Unity e testo dell'interfaccia utente

Unity presuppone che tutti i nuovi elementi aggiunti a una scena sono 1 unità di Unity nelle dimensioni o scalabilità trasformazione 100%, si traduce in circa 1 metro su HoloLens. Nel caso di tipi di carattere, il riquadro delimitatore per un TextMesh 3D è disponibile in per impostazione predefinita in circa 1 metro dell'altezza.

![Utilizzo di tipi di carattere in Unity](images/640px-hug-text-03.png)<br>
*Predefinito Unity 3D testo (testo Mesh) occupa 1 unità di Unity, ovvero 1 metro*

<br>
La maggior parte delle finestre di progettazione visiva utilizzare punti per definire le dimensioni dei caratteri nel mondo reale. Sono presenti circa 2835 (2,834.645666399962) punti 1 metro. Base la conversione di sistema del punto 1 metro e testo Mesh dimensioni del carattere predefinite di Unity pari a 13, le operazioni matematiche semplici pari a 13 diviso 2835 uguale 0.0046 (0.004586111116 per essere precisi) fornisce per iniziare con un buona scalabilità standard (alcuni può essere utile per l'arrotondamento su 0.005). Il ridimensionamento l'oggetto testo o del contenitore su questi valori non consentirà solo per la conversione di 1:1 del tipo di carattere con dimensioni in un programma di progettazione, ma fornisce inoltre standard, pertanto è possibile mantenere la coerenza nell'intera l'esperienza.

![Unity Mesh testo 3D con le dimensioni dei caratteri diverse](images/Text_In_Unity_Measurements1.png)<br>
*Valori di scala per il testo di Unity 3D e il testo dell'interfaccia utente*

![Unity Mesh testo 3D con le dimensioni dei caratteri diverse](images/hug-text-05-1000px.png)<br>
*Unity Mesh testo 3D con i valori ottimizzati*

<br>
Quando si aggiunge un elemento di testo basati su interfaccia utente o dell'area di una scena, disparità la dimensione è ancora maggiore. Le differenze nelle due dimensioni è circa 1000%, che potrebbe offrire il fattore di scala per i componenti di testo dell'interfaccia utente in base a 0.00046 (0.0004586111116 per essere precisi) o 0.0005 per il valore arrotondato.

![Testo dell'interfaccia utente di Unity con diversi pixel dinamica per i valori dell'unità](images/hug-text-04-1000px.png)<br>
*Testo dell'interfaccia utente di Unity con valori ottimizzati*

<br>

>[!NOTE]
>Il valore predefinito di qualsiasi tipo di carattere può dipendere dalle dimensioni della trama di quel tipo di carattere o come tipo di carattere è stato importato in Unity. Questi test sono stati eseguiti in base sul tipo di carattere Arial predefinito in Unity, nonché un altro tipo di carattere importato.

## <a name="working-with-text-mesh-pro"></a>Utilizzo di testo Mesh Pro

Con Unity testo Mesh Pro, è possibile proteggere la qualità di rendering di testo. Supporta la struttura di testo crisp indipendentemente dalla distanza utilizzando il [SDF (campo distanza Signed)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) tecnica. Con lo stesso metodo di calcolo che è stato usato in precedenza per il testo 3D Mesh e il testo dell'interfaccia utente, è possibile trovare i valori di scala corretti uso punto tipografica convenzionale. Poiché il carattere di testo Mesh Pro 3D predefinito con le dimensioni 36 Mostra il rettangolo di selezione di 2,5 Unit(2.5m) Unity, è possibile usare il valore di scala 0.005 per usare la dimensione del punto. Il testo della rete di Pro nel menu dell'interfaccia utente ha il valore predefinito pari a 25 Unit(25m) Unity di delimitazione. Questo ci offre 0.0005 per il valore della scala.

![Unity Mesh testo 3D con le dimensioni dei caratteri diverse](images/Text_In_Unity_Measurements2.png)<br>
*Valori di scala per il testo di Unity 3D e il testo dell'interfaccia utente*

## <a name="recommended-text-size"></a>Dimensione del testo consigliato
Come si può immaginare, le dimensioni di tipo che viene usato in un PC o un dispositivo Tablet PC (in genere compresa tra 12: 32 pt) esaminare risulta piuttosto piccole una distanza massima 2 metri. Dipende dalle caratteristiche di ogni tipo di carattere, ma sono in genere quello minimo consigliato visualizzazione angolo e l'altezza dei caratteri per migliorare la leggibilità intorno 0.35°-0.4°/12.21-13.97mm basato sul nostro ricerche su utente. Ciò che è 35 40pt con il fattore di scala illustrato in precedenza. 

Per l'interazione quasi in 0.45m(45cm), angolo di visualizzazione minima leggibile del tipo di carattere e l'altezza sono 0.4 °-0,5 ° / 3.14-3.9 mm. Ciò che è 12 pt 9 con fattore di scala illustrato in precedenza.

![Più vicino e lontano intervallo interazione](images/typography-distance-1000px.jpg)
*intervallo contenuto in vicino e lontano interazione*

### <a name="the-minimum-legible-font-size"></a>Le dimensioni minime del carattere leggibili
| distanza | Angolo di visualizzazione | Altezza del testo | Dimensione del carattere |
|---------|---------|---------|---------|
| 45cm (distanza manipolazione diretta) | 0.4°-0.5° | 3.14-3.9 mm | 8.9 – 11.13pt |
| 2 minuti | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>Le dimensioni del carattere facilmente leggibili
| distanza | Angolo di visualizzazione | Altezza del testo | Dimensione del carattere |
|---------|---------|---------|---------|
| 45cm (distanza manipolazione diretta) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8pt |
| 2 minuti | 0.6°-0.75° | 20,9-26,2 mm | hanno raggiunto 59,4-74.2pt |

Segoe UI (tipo di carattere predefinito per Windows) funziona bene nella maggior parte dei casi. Tuttavia, evitare di usare light o semi chiaro famiglie di caratteri di piccole dimensioni poiché verranno vibrazione tratti verticali sottili e avrà alcun effetto di migliorare la leggibilità. Tipi di carattere moderni con sufficiente lo spessore del tratto funziona correttamente. Ad esempio, Helvetica e Arial aspetto ricche e sono molto leggibile in HoloLens con regolari o in grassetto.


![Angolo di visualizzazione](images/Text_In_Unity_ViewingAngle.jpg)
*visualizzazione altezza distanza angolo e testo*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Ben strutturata di qualità di rendering di testo con dimensione corretta

Basati su tali fattori di scalabilità, è stata creata [prefabs testo con testo dell'interfaccia utente e della rete di testo 3D](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text). Gli sviluppatori possono utilizzare questi prefabs ottenere testo acuto e la dimensione del carattere coerente.

![Ben strutturata di qualità di rendering di testo con dimensione corretta](images/hug-text-06-1000px.png)<br>
*Ben strutturata di qualità di rendering di testo con dimensione corretta*

## <a name="shader-with-occlusion-support"></a>Shader con il supporto di occlusione

Materiale di tipo di carattere predefinito di Unity nepodporuje occlusione. Per questo motivo, verrà visualizzato il testo dietro gli oggetti per impostazione predefinita. È stato incluso un semplice [shader che supporta le relative all'occlusione](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader). L'immagine seguente mostra il testo con il materiale del tipo di carattere predefinito (sinistra) e il testo con occlusione appropriato (a destra).

![Shader con il supporto di occlusione](images/hug-text-07-1000px.png)<br>
*Shader con il supporto di occlusione*


## <a name="see-also"></a>Vedere anche
* [Testo Prefab nel MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [Tipografia](typography.md)

 
