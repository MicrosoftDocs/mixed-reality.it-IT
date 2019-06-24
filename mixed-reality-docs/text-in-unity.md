---
title: Testo in Unity
description: "Per visualizzare il testo in Unity, sono disponibili due tipi di componenti del testo è possibile usare: testo dell'interfaccia utente e della rete di testo 3D."
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, consente di controllare, tipo di carattere, tipografia, dell'interfaccia utente, esperienza utente
ms.openlocfilehash: 45037f27f68a19478fd56a6edc940fbe45ae7671
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326296"
---
# <a name="text-in-unity"></a>Testo in Unity

Il testo è uno dei principali componenti nelle App holographic. Per visualizzare il testo in Unity, sono disponibili due tipi di componenti del testo è possibile usare: testo dell'interfaccia utente e della rete di testo 3D. Per impostazione predefinita sono visualizzati sfocati e sono troppo grandi. È necessario modificare alcune variabili per ottenere il testo ben strutturato e di alta qualità con una dimensione gestibile in HoloLens. Applicando fattore di scala per ottenere le dimensioni appropriate, quando si usa il testo dell'interfaccia utente e i componenti della rete di testo 3D, è possibile ottenere una migliore qualità di rendering.

![Come ottenere il testo ben strutturato e accattivante](images/hug-text-02-640px.png)<br>
*Testo predefinito sfocati in Unity*

## <a name="working-with-fonts-in-unity"></a>Utilizzo di tipi di carattere in Unity

Unity presuppone che tutti i nuovi elementi aggiunti a una scena sono 1 unità di Unity nelle dimensioni o scalabilità trasformazione 100%, si traduce in circa 1 metro su HoloLens. Nel caso di tipi di carattere, il riquadro delimitatore per un TextMesh 3D è disponibile in per impostazione predefinita in circa 1 metro dell'altezza.

![Utilizzo di tipi di carattere in Unity](images/640px-hug-text-03.png)<br>
*Testo predefinito Unity occupa 1 unità di Unity, ovvero 1 metro*

<br>
La maggior parte delle finestre di progettazione visiva utilizzare punti per definire le dimensioni dei caratteri nel mondo reale. Sono presenti circa 2835 (2,834.645666399962) punti 1 metro. Base la conversione di sistema del punto 1 metro e testo Mesh dimensioni del carattere predefinite di Unity pari a 13, le operazioni matematiche semplici pari a 13 diviso 2835 uguale 0.0046 (0.004586111116 per essere precisi) fornisce per iniziare con un buona scalabilità standard (alcuni può essere utile per l'arrotondamento su 0.005). Il ridimensionamento l'oggetto testo o del contenitore su questi valori non consentirà solo per la conversione di 1:1 del tipo di carattere con dimensioni in un programma di progettazione, ma fornisce inoltre standard, pertanto è possibile mantenere la coerenza in tutta l'applicazione o il gioco.

![Unity Mesh testo 3D con le dimensioni dei caratteri diverse](images/hug-text-05-1000px.png)<br>
*Unity Mesh testo 3D con i valori ottimizzati*

<br>
Quando si aggiunge un elemento di testo basati su interfaccia utente o dell'area di una scena, disparità la dimensione è ancora maggiore. Le differenze nelle due dimensioni è circa 1000%, che potrebbe offrire il fattore di scala per i componenti di testo dell'interfaccia utente in base a 0.00046 (0.0004586111116 per essere precisi) o 0.0005 per il valore arrotondato.

![Testo dell'interfaccia utente di Unity con diversi pixel dinamica per i valori dell'unità](images/hug-text-04-1000px.png)<br>
*Testo dell'interfaccia utente di Unity con valori ottimizzati*

<br>

>[!NOTE]
>Il valore predefinito di qualsiasi tipo di carattere può dipendere dalle dimensioni della trama di quel tipo di carattere o come tipo di carattere è stato importato in Unity. Questi test sono stati eseguiti in base sul tipo di carattere Arial predefinito in Unity, nonché un altro tipo di carattere importato.

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Ben strutturata di qualità di rendering di testo con dimensione corretta

Basati su tali fattori di scalabilità, è stata creata [prefabs testo con testo dell'interfaccia utente e della rete di testo 3D](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text). Gli sviluppatori possono utilizzare questi prefabs ottenere testo acuto e la dimensione del carattere coerente.

![Ben strutturata di qualità di rendering di testo con dimensione corretta](images/hug-text-06-1000px.png)<br>
*Ben strutturata di qualità di rendering di testo con dimensione corretta*

## <a name="shader-with-occlusion-support"></a>Shader con il supporto di occlusione

Materiale di tipo di carattere predefinito di Unity nepodporuje occlusione. Per questo motivo, verrà visualizzato il testo dietro gli oggetti per impostazione predefinita. È stato incluso un semplice [shader che supporta le relative all'occlusione](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders). L'immagine seguente mostra il testo con il materiale del tipo di carattere predefinito (sinistra) e il testo con occlusione appropriato (a destra).

![Shader con il supporto di occlusione](images/hug-text-07-1000px.png)<br>
*Shader con il supporto di occlusione*

## <a name="recommended-type-size"></a>Dimensioni di tipo consigliato

Come si può immaginare, le dimensioni di tipo che viene usato in un PC o un dispositivo Tablet PC (in genere compresa tra 12: 32 pt) esaminare risulta piuttosto piccole una distanza massima 2 metri. Dipende dalle caratteristiche di ogni tipo di carattere, ma in generale le dimensioni di tipo minimo consigliato per migliorare la leggibilità senza vibrazione di traccia sono tutto 30pt, in base al fattore di scala illustrato in precedenza. Se l'app dovrebbe essere utilizzato a una distanza di più da vicino, dimensioni dei tipi più piccoli possono essere usate. Per la selezione del tipo di carattere Segoe UI (tipo di carattere predefinito per Windows) funziona bene nella maggior parte dei casi. Tuttavia, evitare di usare light o semi luce i tipi di carattere per le dimensioni di tipo in 42pt poiché verranno vibrazione tratti verticali sottili e avrà alcun effetto di migliorare la leggibilità. Tipi di carattere moderni con sufficiente lo spessore del tratto funziona correttamente. Ad esempio, Helvetica e Arial aspetto ricche e sono molto leggibile in HoloLens con regolari o in grassetto.

![Dimensioni di tipo consigliato](images/hug-text-08-1000px.png)<br>
*Esempio di tipo ramp*

## <a name="see-also"></a>Vedere anche

* [Testo Prefab nel MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [Scena e layout di testo di esempio prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [Tipografia](typography.md)

 
