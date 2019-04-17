---
title: Processo di creazione dell'Asset
description: Materiale sussidiario sulla creazione di asset per le esperienze di realtà mista.
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: Asset, creazione, processo, budget, polygons, trame, gli shader, prestazioni
ms.openlocfilehash: cec689ab4d44591d2d3e84679c3fe51dba161bc5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604710"
---
# <a name="asset-creation-process"></a>Processo di creazione dell'Asset

Realtà mista di Windows si basa su decenni di investimento che Microsoft ha apportato in DirectX. Ciò significa che tutti gli sviluppatori esperienze e competenze con la creazione 3D grafica continua a essere preziose con HoloLens.

Gli asset creati per un progetto sono disponibili in molte forme e form. Può essere costituiti da una serie di trame o immagini, audio, video, modelli 3D e le animazioni. Non possiamo iniziare a coprire tutti gli strumenti che è possibile creare diversi tipi di risorse usati in un progetto. Per questo articolo ci concentreremo su metodi di creazione di asset 3D.

![Flusso concetto, la creazione, integrazione e iterazione](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Flusso concetto, la creazione, integrazione e iterazione*

## <a name="things-to-consider"></a>Aspetti da considerare

Quando esaminando l'esperienza si sta tentando di creare considerala come un **budget** che è possibile impiegare per tentare di creare un'esperienza ottimale. Non è necessariamente complicati limiti sul numero di **poligoni** oppure **tipi di materiali** usare gli asset ma più di un set budget di compromessi.

Di seguito è riportato un budget di esempio per la tua esperienza. Le prestazioni non sono in genere un singolo punto di errore, ma morte da tagli mille per se.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Asset</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Memoria</th>
</tr><tr>
<td> Poligoni</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> Trame</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> Shader</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Fisica</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> Illuminazione in tempo reale</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> Multimediali (audio/video)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> Lo script o per la logica</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> Overhead generale</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>Totale</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Numero totale di asset**
* Gli asset di quanti sono attivi nella scena?

**Complessità degli asset**
* Quanti triangoli / poligoni?
* Complessità è lo shader?

Sia gli sviluppatori e artisti sono necessario prendere in considerazione le funzionalità del dispositivo e il motore della grafica. Microsoft HoloLens dispone di tutti di calcolo e grafica incorporate nel dispositivo. Condivide le funzionalità gli sviluppatori si troverà in una piattaforma per dispositivi mobili.

Il processo di creazione per le risorse è la stessa indipendentemente dal fatto che la destinazione scelta è un'esperienza per un [holographic o un dispositivo coinvolgente](mixed-reality.md#the-mixed-reality-spectrum). La prima cosa da notare è la funzionalità del dispositivo come indicato in precedenza, nonché scalabilità perché è possibile visualizzare il mondo reale in realtà mista, che è opportuno mantenere la scala corretta basata sull'esperienza. 

## <a name="authoring-assets"></a>Creazione di asset

Si inizierà con la modalità di acquisizione di asset per il progetto:
1. Creazione di asset (oggetti acquisire e gli strumenti di creazione e modifica)
2. Acquisto di risorse (acquisto asset online)
3. Porting di asset (accettando gli asset esistenti)
4. Stiamo parlando di esternalizzazione asset (attività di importazione di parti 3rd)

### <a name="creating-assets"></a>Creazione di asset

**Strumenti di creazione**<br>
Prima di tutto è possibile creare il proprio asset in molti modi diversi. Alle creazioni degli artisti 3D usare un numero di applicazioni e strumenti per creare modelli costituite **trame**, **trame**, e **materiali**. Il valore viene quindi salvato in un formato di file che può essere importato o utilizzato dal motore di grafica utilizzato dall'app, ad esempio **. FBX** o **. OBJ**. Funziona in qualsiasi strumento che genera un modello che supporta il motore grafico scelto **HoloLens**. Tra esperti di grafica 3D, molti scelgono di usare [Autodesk Maya che a sua volta è in grado di usare HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) per trasformare l'asset modo vengono creati. Se si desidera ottenere qualcosa in Guida introduttiva è anche possibile usare [generatore 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) fornito con Windows da esportare. OBJ per l'utilizzo nell'applicazione.

**Acquisizione di oggetto**<br>
È inoltre disponibile l'opzione per acquisire oggetti in 3D. Acquisizione oggetti inanimati in 3D e la modifica di questi elementi con il software di creazione di contenuti digitali è sempre più comune con la diffusione di video sulla stampa 3D. Usando il **2 Kinect** sensore e [generatore 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) è possibile usare la funzionalità di acquisizione per creare gli asset da oggetti reali. Questo è anche un [suite di strumenti](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) per eseguire la stessa operazione con **photogrammetry** attraverso l'elaborazione di un numero di immagini insieme a sella e mesh e trame.

### <a name="purchasing-assets"></a>Acquisto di risorse

Un'altra opzione eccellente consiste nell'acquisto di risorse per la tua esperienza. Sono disponibili moltissime risorse tramite i servizi, ad esempio la [Unity Asset Store](https://www.assetstore.unity3d.com/) oppure [TurboSquid](http://www.turbosquid.com/) tra gli altri.

Quando si acquistano gli asset di parti 3rd sempre si vuole verificare quanto segue:
* **Che cos'è il conteggio poli?**
  * Adatta entro il tuo budget?
* **Sono disponibili livelli di dettaglio (LOD) per il modello?**
  * Livello di dettaglio di un modello consentono di ridimensionare i dettagli di un modello per le prestazioni.
* **È disponibile il file di origine?**
  * In genere non è incluso con [Unity Asset Store](https://www.assetstore.unity3d.com/) ma sempre incluso con servizi quali [TurboSquid](http://www.turbosquid.com/).
  * Senza il file di origine sarà in grado di modificare l'asset.
  * Assicurarsi che il file di origine specificato può essere importato da strumenti 3D.
* **Sapere dove si andrà**
  * Le animazioni sono disponibili?
  * Assicurarsi di controllare l'elenco di contenuto dell'asset di cui che si acquista.

### <a name="porting-assets"></a>Porting di asset

In alcuni casi sarà consegnato asset esistenti che sono stati originariamente creati per altri dispositivi e App diverse. Nella maggior parte dei casi queste risorse possono essere convertite nei formati compatibili con il motore della grafica che usa l'app.

Durante il trasferimento di risorse da usare nell'applicazione HoloLens che è opportuno chiedere quanto segue:
* **È possibile importare direttamente o devono essere convertiti in un altro formato?** Controllare il formato in cui che si sta importando con il motore della grafica in uso.
* **Se la conversione in un formato compatibile con viene persa alcuna operazione?** In alcuni casi i dettagli possono essere persi o l'importazione può causare gli elementi devono essere ripulite in strumento di creazione 3D.
* **What ' s triangoli o i poligoni contare per l'asset?** Il budget per l'applicazione è possibile usare [Simplygon](https://www.simplygon.com/) o strumenti simili a Sbaragliate (livello di routine o manualmente ridurre il numero di poligono) la risorsa originale per rientrare il budget per le applicazioni.

### <a name="outsourcing-assets"></a>Asset di servizi di outsourcing

È un'altra opzione per i progetti di grandi dimensioni che richiedono più risorse rispetto al team attrezzata per creare sia per l'outsourcing della creazione dell'asset. Il processo di outsourcing prevede l'individuazione del giusto studio o agenzia che specializza negli asset dell'outsourcing. Ciò può essere l'opzione più costosa ma anche essere le più flessibili in vantaggi.
* **Definire chiaramente che cosa si sta richiedendo**
  * Specificare il livello di dettaglio possibile
  * Front-end, lato e immagini concetto indietro
  * Asset con art di riferimento nel contesto
  * Scalabilità dell'oggetto (in genere specificata in centimetri)
* **Fornire un Budget**
  * Intervallo numero poli
  * Numero di trame
  * Tipo di shader (per Unity e HoloLens è deve essere sempre predefinito per gli shader per dispositivi mobili prima di tutto)
* **Comprendere i costi**
  * Che cos'è il criterio di outsourcing per richieste di modifica?

L'esternalizzazione può lavorare molto efficace basata sul diario di progetti ma richiede ulteriori supervisione per garantire la possibilità di ottenere l'asset a destra che necessaria la prima volta.
