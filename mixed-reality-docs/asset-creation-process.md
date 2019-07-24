---
title: Processo di creazione dell'asset
description: Linee guida per la creazione di asset per esperienze di realtà miste.
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: Asset, creazione, processo, Budget, poligoni, trame, shader, prestazioni
ms.openlocfilehash: 513a9856ac35e4229cfb7bc8bcb92d9d6a152980
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692295"
---
# <a name="asset-creation-process"></a>Processo di creazione dell'asset

La realtà mista di Windows si basa su decenni di investimenti effettuati da Microsoft in DirectX. Ciò significa che tutti gli sviluppatori di esperienza e competenze hanno la possibilità di creare grafica 3D continua a essere utile con HoloLens.

Gli asset creati per un progetto sono disponibili in molte forme e form. Possono essere costituiti da una serie di trame/immagini, audio, video, modelli 3D e animazioni. Non è possibile iniziare a coprire tutti gli strumenti disponibili per creare i diversi tipi di asset usati in un progetto. Per questo articolo, si escentreranno sui metodi di creazione di asset 3D.

![Concetto, creazione, integrazione e flusso di iterazione](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Concetto, creazione, integrazione e flusso di iterazione*

## <a name="things-to-consider"></a>Aspetti da considerare

Quando si esamina l'esperienza che si sta tentando di creare, considerarlo come un **budget** che è possibile spendere per provare a creare l'esperienza migliore. Non esistono necessariamente limiti rigidi sul numero di **poligoni** o **tipi di materiali** usati negli asset, ma più un set di compromessi con budget.

Di seguito è riportato un budget di esempio per la propria esperienza. Le prestazioni non sono in genere un singolo punto di errore, ma la morte è di mille tagli per sé.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Asset</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Memoria</th>
</tr><tr>
<td> Poligoni</td><td> 0</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> Trame</td><td> 5%</td><td> 15</td><td>25%</td>
</tr><tr>
<td> Shader</td><td> 15</td><td> 35%</td><td> 0</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Fisica</td><td> 5%</td><td> 15</td><td> 0</td>
</tr><tr>
<td> Illuminazione in tempo reale</td><td> 10%</td><td> 0</td><td> 0</td>
</tr><tr>
<td> Supporti (audio/video)</td><td> -</td><td> 15</td><td> 25%</td>
</tr><tr>
<td> Script/logica</td><td> 25%</td><td> 0</td><td> 5%</td>
</tr><tr>
<td> Overhead generale</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>Totale</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Numero totale di asset**
* Quanti asset sono attivi nella scena?

**Complessità degli asset**
* Quanti triangoli/poligoni?
* Quanto è complesso lo shader?

Gli sviluppatori e gli artisti devono prendere in considerazione le funzionalità del dispositivo e del motore di grafica. Microsoft HoloLens ha tutto il calcolo e la grafica integrati nel dispositivo. Condivide le funzionalità che gli sviluppatori troveranno in una piattaforma mobile.

Il processo di creazione per gli asset è lo stesso indipendentemente dal fatto che la destinazione sia un'esperienza per un [dispositivo olografico o](mixed-reality.md#the-mixed-reality-spectrum)per un dispositivo immersivo. L'aspetto principale da tenere presente è la funzionalità del dispositivo come indicato in precedenza, nonché la scalabilità, poiché è possibile vedere il mondo reale in realtà mista, in modo da mantenere la scalabilità corretta in base all'esperienza. 

## <a name="authoring-assets"></a>Creazione di asset

Si inizierà con i modi per ottenere gli asset per il progetto:
1. Creazione di asset (strumenti di creazione e acquisizione di oggetti)
2. Acquisti di risorse (acquisto di asset online)
3. Porting degli asset (prendendo gli asset esistenti)
4. Risorse di outsourcing (importazione di asset da terze parti)

### <a name="creating-assets"></a>Creazione di asset

**Strumenti di creazione**<br>
Per prima cosa è possibile creare asset personalizzati in diversi modi. gli artisti 3D usano una serie di applicazioni e strumenti per creare modelli che sono costituiti da **mesh**, **trame**e **materiali**. Questa operazione viene quindi salvata in un formato di file che può essere importato o usato dal motore di grafica usato dall'app, ad esempio **. FBX** o **. OBJ**. Tutti gli strumenti che generano un modello supportato dal motore di grafica scelto funzioneranno in **HoloLens**. Tra gli artisti 3D, molti scelgono di usare il [Maya di Autodesk, che a sua volta è in grado di usare HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) per trasformare il modo in cui vengono create le risorse. Se si vuole ottenere un risultato rapido, è anche possibile usare il [Generatore 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) incluso in Windows per l'esportazione. OBJ da usare nell'applicazione.

**Acquisizione oggetti**<br>
È anche possibile acquisire oggetti in 3D. L'acquisizione di oggetti inanimati in 3D e la relativa modifica con il software di creazione di contenuti digitali è sempre più diffusa con la crescita della stampa 3D. Utilizzando il sensore **Kinect 2** e il [Generatore 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) è possibile utilizzare la funzionalità di acquisizione per creare asset da oggetti reali. Si tratta anche di una [suite di strumenti](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) che consentono di eseguire la stessa operazione con **fotogrammetria** elaborando un numero di immagini da unire e mesh e trame.

### <a name="purchasing-assets"></a>Acquisti di asset

Un'altra opzione eccellente è quella di acquistare asset per la propria esperienza. Sono disponibili moltissime risorse tramite servizi, ad esempio Unity [Asset Store](https://www.assetstore.unity3d.com/) o [TurboSquid](http://www.turbosquid.com/) , tra gli altri.

Quando si acquistano asset da terze parti, è sempre necessario controllare quanto segue:
* **Qual è il numero di Poly?**
  * Rientra nel budget?
* **Sono disponibili livelli di dettaglio (LODs) per il modello?**
  * Il livello di dettaglio di un modello consente di ridimensionare i dettagli di un modello in modo da ottenere prestazioni ottimali.
* **Il file di origine è disponibile?**
  * In genere non è incluso in [archivio risorse](https://www.assetstore.unity3d.com/) di Unity ma sempre incluso con servizi come [TurboSquid](http://www.turbosquid.com/).
  * Senza il file di origine, non sarà possibile modificare l'asset.
  * Verificare che il file di origine fornito possa essere importato dagli strumenti 3D.
* **Scopri cosa stai ricevendo**
  * Sono disponibili animazioni?
  * Assicurarsi di controllare l'elenco dei contenuti dell'asset che si sta acquistando.

### <a name="porting-assets"></a>Porting degli asset

In alcuni casi verranno gestite risorse esistenti originariamente create per altri dispositivi e app diverse. Nella maggior parte dei casi questi asset possono essere convertiti in formati compatibili con il motore di grafica usato dall'app.

Quando si trasferiscono asset da usare nell'applicazione HoloLens, è necessario richiedere quanto segue:
* **È possibile importare direttamente o è necessario convertirli in un altro formato?** Controllare il formato che si sta importando con il motore grafico in uso.
* **Se la conversione in un formato compatibile è qualcosa di perduto,** Talvolta è possibile che i dettagli vengano persi o che l'importazione possa causare la pulizia degli artefatti in uno strumento di creazione 3D.
* **Qual è il numero di triangoli/poligoni per l'asset?** A seconda del budget per l'applicazione, è possibile usare [Simplygon](https://www.simplygon.com/) o strumenti simili per decimare (in modo procedurale o ridurre manualmente il numero di Poly) l'asset originale per adattarsi al budget per le applicazioni.

### <a name="outsourcing-assets"></a>Asset di outsourcing

Un'altra opzione per progetti più grandi che richiedono più risorse rispetto al team è attrezzata per la creazione di asset di origine. Il processo di outsourcing implica la ricerca del giusto studio o agenzia specializzato nell'esternalizzazione degli asset. Questa è l'opzione più costosa, ma è anche la più flessibile per quanto possibile.
* **Definire chiaramente ciò che si sta richiedendo**
  * Fornire il maggior dettaglio possibile
  * Immagini del concetto anteriore, laterale e posteriore
  * Arte di riferimento che mostra asset nel contesto
  * Scala dell'oggetto (in genere specificato in centimetri)
* **Fornire un budget**
  * Intervallo conteggio Poly
  * Numero di trame
  * Tipo di shader (per Unity e HoloLens è sempre necessario default per i dispositivi mobili shader)
* **Informazioni sui costi**
  * Quali sono i criteri di outsourcing per le richieste di modifica?

L'outsourcing può funzionare in modo estremamente efficace in base alla sequenza temporale dei progetti, ma richiede una supervisione per garantire che si ottengano le risorse corrette necessarie per la prima volta.
