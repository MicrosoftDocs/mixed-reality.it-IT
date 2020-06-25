---
title: Testo in Unity
description: "Per visualizzare il testo in Unity, è possibile usare due tipi di componenti di testo: testo dell'interfaccia utente e mesh di testo 3D."
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Realtà mista di Windows, progettazione, controlli, carattere, tipografia, interfaccia utente, UX
ms.openlocfilehash: 8662ff8a8e1e99455354392d7dc852feb1fe1589
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345711"
---
# <a name="text-in-unity"></a>Testo in Unity

Il testo è uno dei componenti più importanti nelle app olografiche. Per visualizzare il testo in Unity, sono disponibili tre tipi di componenti di testo che è possibile usare: testo dell'interfaccia utente, mesh di testo 3D e testo mesh Pro. Per impostazione predefinita, il testo dell'interfaccia utente e la mesh del testo 3D appaiono sfocate e sono troppo grandi. È necessario modificare alcune variabili per ottenere testo nitido e di alta qualità con dimensioni gestibili in HoloLens. Applicando un fattore di scalabilità per ottenere dimensioni appropriate quando si usa il testo dell'interfaccia utente e i componenti mesh di testo 3D, è possibile ottenere una migliore qualità di rendering.

![Come ottenere testo nitido e bello](images/hug-text-02-640px.png)<br>
*Testo predefinito sfuocato in Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Uso del testo 3D di Unity (mesh di testo) e del testo dell'interfaccia utente

Unity presuppone che tutti i nuovi elementi aggiunti a una scena siano di 1 unità Unity o di una scala di trasformazione 100%, che si traduce in circa 1 contatore in HoloLens. Nel caso dei tipi di carattere, il rettangolo di delimitazione di un TextMesh 3D viene visualizzato per impostazione predefinita a circa 1 metro in altezza.

![Uso dei tipi di carattere in Unity](images/640px-hug-text-03.png)<br>
*Il testo 3D di Unity predefinito (rete di testo) occupa 1 unità Unity che corrisponde a 1 contatore*

<br>
La maggior parte delle finestre di progettazione visiva utilizza punti per definire le dimensioni dei caratteri nel mondo reale. Sono presenti circa 2835 (834.645666399962) punti in 1 contatore. In base alla conversione del sistema del punto in 1 misuratore e le dimensioni del carattere della mesh di testo predefinite di Unity di 13, la matematica semplice di 13 divisa per 2835 equivale a 0,0046 (0.004586111116), che fornisce una scala standard corretta per iniziare (alcune potrebbero voler arrotondare a 0,005). Il ridimensionamento dell'oggetto o del contenitore di testo a questi valori non consentirà solo la conversione 1:1 delle dimensioni dei tipi di carattere in un programma di progettazione, ma fornisce anche uno standard che consente di mantenere la coerenza nell'intera esperienza.

![Mesh di testo 3D Unity con dimensioni del carattere diverse](images/Text_In_Unity_Measurements1.png)<br>
*Ridimensionamento dei valori per il testo 3D Unity e il testo dell'interfaccia utente*

<br>

![Mesh di testo 3D Unity con dimensioni del carattere diverse](images/hug-text-05-1000px.png)<br>
*Mesh di testo 3D Unity con valori ottimizzati*

<br>
Quando si aggiunge un'interfaccia utente o un elemento di testo basato su Canvas a una scena, la disparità delle dimensioni è ancora maggiore. Le differenze nelle due dimensioni sono pari a circa il 1000%, che porterebbe il fattore di scala per i componenti di testo basati sull'interfaccia utente a 0,00046 (0.0004586111116) o 0,0005 per il valore arrotondato.

![Testo dell'interfaccia utente Unity con diversi pixel dinamici per unità](images/hug-text-04-1000px.png)<br>
*Testo dell'interfaccia utente Unity con valori ottimizzati*

<br>

>[!NOTE]
>Il valore predefinito di qualsiasi tipo di carattere può essere influenzato dalla dimensione della trama del tipo di carattere o dalla modalità di importazione del tipo di carattere in Unity. Questi test sono stati eseguiti in base al tipo di carattere Arial predefinito in Unity, oltre a un altro tipo di carattere importato.

## <a name="working-with-text-mesh-pro"></a>Uso di Text mesh Pro

Con la funzionalità text mesh di Unity Pro, è possibile proteggere la qualità del rendering del testo. Supporta la delineatura di testo croccante indipendentemente dalla distanza utilizzando la tecnica [SDF (signed distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) . Usando lo stesso metodo di calcolo usato in precedenza per la mesh di testo 3D e il testo dell'interfaccia utente, è possibile trovare i valori di ridimensionamento appropriati da usare con i punti tipografici convenzionali. Poiché il tipo di carattere 3D di mesh Pro predefinito con dimensioni pari a 36 ha una dimensione di delimitazione di 2,5 unità Unity (2,5 m), è possibile usare un valore di scala 0,005 per ottenere la dimensione del punto. Il testo Pro mesh nel menu dell'interfaccia utente ha una dimensione di delimitazione predefinita di 25 unità Unity (25m). In questo modo si ottiene 0,0005 per il valore di scalabilità.

![Mesh di testo 3D Unity con dimensioni del carattere diverse](images/Text_In_Unity_Measurements2.png)<br>
*Ridimensionamento dei valori per il testo 3D Unity e il testo dell'interfaccia utente*

## <a name="recommended-text-size"></a>Dimensioni consigliate del testo
Come si può immaginare, i tipi di dimensioni usati in un PC o un Tablet (in genere tra 12-32pt) sembrano abbastanza piccoli a una distanza di 2 metri. Dipende dalle caratteristiche di ogni tipo di carattere, ma in generale l'angolo di visualizzazione minimo consigliato e l'altezza del tipo di carattere per la leggibilità sono circa 0,35 °-0,4 °/12.21-13.97mm in base agli studi di ricerca degli utenti. È di circa 35 40pt con il fattore di scala introdotto in precedenza. 

Per l'interazione near a 0,45 m (45 cm), l'angolo di visualizzazione del tipo di carattere leggibile minimo e l'altezza sono 0.4 °-0,5 °/3.14 – 3,9 mm. Si tratta di circa 9 12pt con il fattore di scala introdotto in precedenza.

![Contenuto dell'intervallo di interazione near-and-distante ](images/typography-distance-1000px.jpg)
 *nell'intervallo di interazione near and lontano*

### <a name="the-minimum-legible-font-size"></a>Dimensioni minime del carattere leggibili
| Distance | Angolo di visualizzazione | Altezza testo | Dimensioni del carattere |
|---------|---------|---------|---------|
| 45 cm (distanza di manipolazione diretta) | 0.4 °-0,5 ° | 3.14 – 3,9 mm | 8,9 – 11.13 PT |
| 2m | 0,35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 PT |


### <a name="the-comfortably-legible-font-size"></a>Dimensioni del carattere facilmente leggibili
| Distance | Angolo di visualizzazione | Altezza testo | Dimensioni del carattere |
|---------|---------|---------|---------|
| 45 cm (distanza di manipolazione diretta) | 0,65 °-0,8 ° | 5.1-6,3 mm | 14.47-17,8 PT |
| 2m | 0.6 °-0,75 ° | 20,9-26.2 mm | 59.4-74.2 PT |

Segoe UI (il tipo di carattere predefinito per Windows) funziona correttamente nella maggior parte dei casi. Tuttavia, evitare di usare famiglie di caratteri chiaro o semichiaro in piccole dimensioni poiché i tratti verticali sottili vibrano e diminuiscono la leggibilità. I tipi di carattere moderni con uno spessore del tratto sufficiente funzionano correttamente. Ad esempio, Helvetica e Arial sembrano splendidi e sono molto leggibili in HoloLens con pesi regolari o in grassetto.


![Visualizzazione angolo, ](images/Text_In_Unity_ViewingAngle.jpg)
 *angolo e altezza del testo*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Qualità rendering testo nitido con dimensione corretta

In base a questi fattori di scalabilità, sono stati creati [prefabbricati di testo con testo dell'interfaccia utente e mesh di testo 3D](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text). Gli sviluppatori possono usare questi prefabbricati per ottenere testo nitido e dimensioni del carattere coerenti.

![Qualità rendering testo nitido con dimensione corretta](images/hug-text-06-1000px.png)<br>
*Qualità rendering testo nitido con dimensione corretta*

## <a name="shader-with-occlusion-support"></a>Shader con supporto occlusione

Il materiale del tipo di carattere predefinito di Unity non supporta l'occlusione. Per questo motivo, per impostazione predefinita verrà visualizzato il testo dietro gli oggetti. È stato incluso un semplice [shader che supporta l'occlusione](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader). L'immagine seguente mostra il testo con il materiale carattere predefinito (a sinistra) e il testo con occlusione corretta (destra).

![Shader con supporto occlusione](images/hug-text-07-1000px.png)<br>
*Shader con supporto occlusione*


## <a name="see-also"></a>Vedi anche
* [Prefabbricato di testo in MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [Tipografia](typography.md)

 
