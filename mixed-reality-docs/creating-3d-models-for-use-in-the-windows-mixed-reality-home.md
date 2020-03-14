---
title: Creare modelli 3D da usare nella Home page
description: Requisiti delle risorse e linee guida per la creazione di modelli 3D da usare nella Home realtà mista di Windows su cuffie HoloLens e Immersive (VR).
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, modellazione, linee guida per la modellazione, requisiti delle risorse, linee guida per la creazione, avvio, avvio 3D, trama, materiali, complessità, triangoli, mesh, poligoni, policount, limiti
ms.openlocfilehash: 536fd9bc2002d679ee3bf73d5c906b84c51e5d46
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375628"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Creare modelli 3D da usare nella Home page

La [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) è il punto di partenza in cui gli utenti atterrano prima di avviare le applicazioni. È possibile progettare l'applicazione per gli auricolari a realtà mista di Windows per sfruttare un [modello 3D come strumento di avvio delle app](implementing-3d-app-launchers.md) e per consentire [l'inserimento di collegamenti profondi 3D nella Home realtà mista di Windows](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) dall'interno dell'app. Questo articolo descrive le linee guida per la creazione di modelli 3D compatibili con la Home realtà mista di Windows.

## <a name="asset-requirements-overview"></a>Panoramica dei requisiti degli asset
Quando si creano modelli 3D per la realtà mista di Windows, è necessario che tutti gli asset soddisfino i requisiti seguenti: 
1. [Esportazione](#exporting-models) : gli asset devono essere recapitati nel formato di file GLB (glTF binario)
2. [Modellazione](#modeling-guidelines) : gli asset devono essere costituiti da un numero di triangoli inferiore a 10.000, avere non più di 64 nodi e 32 sottomesh per LOD
3. [Materials](#material-guidelines) : le trame non possono essere più grandi di 4096 x 4096 e la mappa MIP più piccola non deve essere maggiore di 4 su una delle due dimensioni
4. [Animazione](#animation-guidelines) : le animazioni non possono essere più lunghe di 20 minuti a 30 fps (fotogrammi chiave 36.000) e devono contenere < = 8192 vertici di destinazione morph
5. [Ottimizzazione](#optimizations) : gli asset devono essere ottimizzati con [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). Questa operazione è **necessaria per le versioni del sistema operativo windows < = 1709** e consigliata per le versioni del sistema operativo Windows > = 1803

Il resto di questo articolo include una panoramica dettagliata di questi requisiti, oltre a linee guida aggiuntive per garantire che i modelli funzionino correttamente con la Home realtà mista di Windows. 

## <a name="detailed-guidance"></a>Istruzioni dettagliate

### <a name="exporting-models"></a>Esportazione di modelli

La Home realtà mista di Windows prevede la distribuzione di asset 3D utilizzando il formato di file con estensione GLB con le immagini e i dati binari incorporati. GLB è la versione binaria del formato glTF che è uno standard aperto gratuito per la distribuzione di asset 3D gestito dal gruppo Khronos. Man mano che glTF si evolve come standard di settore per il contenuto 3D interoperativo, il supporto di Microsoft per il formato tra le app e le esperienze di Windows. Se non è stato creato un asset glTF prima di trovare un [elenco degli esportatori e dei convertitori supportati](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) nella pagina GitHub del gruppo di lavoro glTF.  

### <a name="modeling-guidelines"></a>Linee guida per la modellazione

Windows prevede che gli asset vengano generati usando le seguenti linee guida di modellazione per garantire la compatibilità con l'esperienza di casa realtà mista. Quando si crea una modellazione nel programma di propria scelta, tenere presenti le seguenti raccomandazioni e limitazioni:
1. L'asse su deve essere impostato su "Y".
2. L'asset deve riguardare "Avanti" verso l'asse Z positivo.
3. Tutte le risorse devono essere compilate sul piano di base all'origine della scena (0, 0, 0)
4. Le unità di lavoro devono essere impostate su contatori e asset in modo che le risorse possano essere create a livello globale
5. Non è necessario combinare tutte le mesh, ma è consigliabile usare i dispositivi con vincoli di risorse
6. Tutte le mesh devono condividere 1 materiale con un solo set di trame usato per l'intero asset
7. Le UV devono essere disposte in una disposizione quadrata nello spazio 0-1. Evitare di affiancare trame, sebbene siano consentite.
8. La funzionalità MULTIUV non è supportata
9. I materiali con doppia faccia non sono supportati

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Numeri di triangolo e livelli di dettaglio (LODs)

La Home realtà mista di Windows non supporta i modelli con più di 10.000 triangoli. Si consiglia di triangolare le mesh prima dell'esportazione per assicurarsi che non superino questo conteggio. Windows MR supporta anche i livelli di dettaglio di geometria facoltativi (LODs) per garantire un'esperienza efficiente e di alta qualità. [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) consentirà di combinare 3 versioni del modello in un singolo modello. glb. Windows determina quale LOD visualizzare in base alla quantità di spazio su schermo che il modello sta occupando. Sono supportati solo 3 livelli di LOD con i seguenti conteggi dei triangolo consigliati:
<br>

|  Livello LOD  |  Conteggio triangolo consigliato  |  Numero massimo di triangolo | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5\.000  |  10,000 | 
|  LOD 2 |  2\.500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>Conteggi dei nodi e limiti di sottomesh
La Home realtà mista di Windows non supporta i modelli con più di 64 nodi o sottomesh 32 per LOD. I nodi sono un concetto nella [specifica glTF](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) che definiscono gli oggetti nella scena. Le sottomesh sono definite nella matrice di [primitive](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) sulla mesh nell'oggetto. 

|  Caratteristica |  Descrizione  |  Massimo supportato | Documentazione |
|------|------|------|------|
|  Nodi |  Oggetti nella scena glTF |  64 per LOD | [Qui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Sottomesh |  Somma delle primitive in tutte le mesh |  32 per LOD | [Qui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Linee guida materiali

Le trame devono essere preparate usando un flusso di lavoro di rugosità Metal del PBR. Per iniziare, creare un set completo di trame, tra cui albedo, Normal, occlusione, Metallic e Rough. La realtà mista di Windows supporta le trame con risoluzioni fino a 4096x4096, ma è consigliabile creare in 512x512. Inoltre, le trame devono essere create in risoluzioni in multipli di 4, perché questo è un requisito per il formato di compressione applicato alle trame nei passaggi di esportazione descritti di seguito. Infine, quando si generano mappe MIP o una trama, il MIP minimo deve essere un massimo di 4x4.
<br>

|  Dimensioni di trama consigliate  |  Dimensioni massime trama | MIP più basso
|----|----|----|
|  512x512  |  4096x4096 | massimo 4x4|

### <a name="albedo-base-color-map"></a>Mappa albedo (colore di base)

Colore non elaborato senza informazioni sull'illuminazione. Questa mappa contiene anche le informazioni sulla riflettenza e la diffusione per i metal (bianco nella mappa metallica) e le superfici di isolamento (nero nella mappa metallica) rispettivamente.

### <a name="normal"></a>Normale

Mappa normale dello spazio tangente

### <a name="roughness-map"></a>Mappa di rugosità

Descrive la microsuperficie dell'oggetto. Il bianco 1,0 è molto nero 0,0 è uniforme. Questa mappa fornisce al cespite il maggior numero di caratteri in quanto descrive effettivamente la superficie, ad esempio graffi, impronte digitali, macchie, sporcizia e così via.

### <a name="ambient-occlusion-map"></a>Mappa di occlusione di ambiente

Mappa di scala dei valori che rappresenta le aree della luce bloccata che blocca le riflessioni

### <a name="metallic-map"></a>Mappa metallica

Indica allo shader se qualcosa è metal o no. Raw Metal = 1,0 bianco non metal = 0,0 nero. È possibile che siano presenti valori grigi di transizione che indicano un elemento che copre il metallo non elaborato, ad esempio Dirt, ma in generale questa mappa deve essere solo in bianco e nero.

## <a name="optimizations"></a>Ottimizzazioni

La Home realtà mista di Windows offre una serie di ottimizzazioni oltre alla specifica glTF di base definita con estensioni personalizzate. Queste ottimizzazioni sono necessarie nelle versioni di Windows < = 1709 e consigliate nelle versioni più recenti di Windows. È possibile ottimizzare facilmente qualsiasi modello glTF 2,0 usando il [convertitore di asset per la realtà mista di Windows disponibile su GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Questo strumento esegue le ottimizzazioni e la compressione delle trame corrette come specificato di seguito. Per un utilizzo generale è consigliabile usare WindowsMRAssetConverter, ma se è necessario un maggiore controllo sull'esperienza e si vuole creare una pipeline di ottimizzazione personalizzata, è possibile fare riferimento alla specifica dettagliata riportata di seguito.  

### <a name="materials"></a>Materiali

Per migliorare il tempo di caricamento degli asset negli ambienti con realtà mista, Windows MR supporta il rendering di trame DDS compresse in base allo schema di compressione della trama definito in questa sezione. Si fa riferimento alle trame DDS usando l' [estensione MSFT_texture_dds](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). Si consiglia vivamente di comprimere le trame. 

#### <a name="hololens"></a>HoloLens

Per le esperienze di realtà miste basate su HoloLens si prevede che le trame vengano compresse usando una configurazione a 2 trame usando la specifica di compressione seguente:
<br>

|  Proprietà glTF  |  Trama  |  Schema di compressione | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R), verde (G), blu (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normale (RG), rugosità (B), Metallic (A) | 


Quando si comprimono le trame DDS, per ogni mappa è prevista la compressione seguente:
<br>

|  Trama  |  Compressione prevista | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Cuffie immersive (VR)

Le esperienze di realtà mista di Windows basate su PC per auricolari immersivi (VR) prevedono che le trame vengano compresse usando una configurazione a 3 trame usando la specifica di compressione seguente:

##### <a name="windows-os--1803"></a>> Sistema operativo Windows = 1803

<br>

|  Proprietà glTF  |  Trama  |  Schema di compressione | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R), verde (G), blu (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusione (R), rugosità (G), Metallic (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normale (RG) | 

Quando si comprimono le trame DDS, per ogni mappa è prevista la compressione seguente:
<br>

|  Trama  |  Compressione prevista | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>< Sistema operativo Windows = 1709
<br>

|  Proprietà glTF  |  Trama  |  Schema di compressione | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R), verde (G), blu (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Rugosità (R), Metallic (G), occlusione (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normale (RG) | 

Quando si comprimono le trame DDS, per ogni mappa è prevista la compressione seguente:
<br>

|  Trama  |  Compressione prevista | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Aggiunta di LODs mesh

Windows MR usa il nodo Geometry LODs per eseguire il rendering di modelli 3D con diversi livelli di dettaglio a seconda della copertura dello schermo. Anche se questa funzionalità non è necessaria tecnicamente, è fortemente consigliata per tutti gli asset. Attualmente Windows supporta 3 livelli di dettaglio. Il valore predefinito di LOD è 0, che rappresenta la qualità più elevata. Gli altri LODs sono numerati in sequenza, ad esempio 1, 2 e ottengono progressivamente una riduzione della qualità. Il [convertitore di asset per la realtà mista di Windows](https://github.com/Microsoft/glTF-Toolkit/releases) supporta la generazione di asset che soddisfano questa specifica LOD accettando più modelli glTF e unendoli in un singolo asset con livelli di LOD validi. Nella tabella seguente vengono descritte le destinazioni del triangolo e l'ordinamento del LOD previsto:
<br>

|  Livello LOD  |  Conteggio triangolo consigliato  |  Numero massimo di triangolo | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5\.000  |  10,000 | 
|  LOD 2 |  2\.500  |  10,000 | 

Quando si usa LODs, specificare sempre 3 livelli LOD. LODs mancanti provocheranno il rendering imprevisto del modello perché il sistema LOD passa al livello di LOD mancante. glTF 2,0 non supporta attualmente LODs come parte della specifica di base. LODs deve pertanto essere definito utilizzando l' [estensione MSFT_LOD](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).

### <a name="screen-coverage"></a>Copertura dello schermo

LODs vengono visualizzati in realtà mista di Windows in base a un sistema basato sul valore della copertura dello schermo impostato in ogni LOD. Gli oggetti che attualmente utilizzano una parte più ampia dello spazio dello schermo vengono visualizzati a un livello di LOD superiore. Il code coverage dello schermo non fa parte della specifica glTF 2,0 di base e deve essere specificato usando MSFT_ScreenCoverage nella sezione "Extras" dell' [estensione MSFT_lod](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  Livello LOD  |  Intervallo consigliato  |  Intervallo predefinito | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  0,5 | 
|  LOD 1 |  Inferiore al 50%-20%  |  0,2 | 
|  LOD 2 |  Inferiore al 20%-1%  |  .01 | 
|  LOD 4  |  Inferiore all'1%  |  - | 

## <a name="animation-guidelines"></a>Linee guida sull'animazione

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte dell' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md). Nelle versioni precedenti di Windows queste animazioni non verranno riprodotte, ma verranno comunque caricate in base alle indicazioni fornite in questo articolo.  

La Home realtà mista supporta gli oggetti glTF animati su cuffie HoloLens e Immersive (VR). Se si desidera attivare animazioni sul modello, è necessario utilizzare l'estensione Mappa animazione nel formato glTF. Questa estensione consente di attivare animazioni nel modello glTF in base alla presenza degli utenti in tutto il mondo, ad esempio attivare un'animazione quando l'utente si avvicina all'oggetto o durante la ricerca. Se l'oggetto glTF ha animazioni, ma non definisce i trigger, le animazioni non verranno riprodotte. La sezione seguente descrive un flusso di lavoro per l'aggiunta di questi trigger a qualsiasi oggetto glTF animato.

### <a name="tools"></a>Strumenti
Prima di tutto, scaricare gli strumenti seguenti, se non sono già presenti. Questi strumenti semplificano l'apertura di qualsiasi modello glTF, l'anteprima, la modifica e il salvataggio come glTF o GLB:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Strumenti glTF per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Apertura e visualizzazione in anteprima del modello
Per iniziare, aprire il modello glTF in VSCode trascinando il file con estensione glTF nella finestra dell'editor. Si noti che se si dispone di un file con estensione GLB invece di un file con estensione glTF, è possibile importarlo in VSCode usando l'addon degli strumenti glTF scaricato. Passare a "View-> Command palette", quindi iniziare a digitare "glTF" nel riquadro comandi e selezionare "glTF: Import from GLB", in cui verrà visualizzata una selezione file per l'importazione di un file con estensione glb. 

Una volta aperto il modello glTF, il codice JSON dovrebbe essere visualizzato nella finestra dell'editor. Si noti che è anche possibile visualizzare in anteprima il modello in un visualizzatore 3D Live usando il pulsante destro del mouse sul nome del file e selezionando il collegamento del comando "glTF: Preview 3D Model" dal menu di scelta rapida. 

### <a name="adding-the-triggers"></a>Aggiunta dei trigger
I trigger di animazione vengono aggiunti al modello glTF JSON usando l'estensione della mappa di animazione. L'estensione della mappa di animazione è documentata pubblicamente [in GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (Nota: questa è un'estensione bozza). Per aggiungere l'estensione al modello, è sufficiente scorrere fino alla fine del file glTF nell'editor e aggiungere il blocco "extensionsUsed" e "Extensions" al file, se non esistono già. Nella sezione "extensionsUsed" si aggiungerà un riferimento all'estensione "EXT_animation_map" e nel blocco "Extensions" si aggiungeranno i mapping alle animazioni nel modello.

Come indicato [nella specifica](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) , si definisce che cosa attiva l'animazione usando la stringa "semantica" in un elenco di "animazioni", che è una matrice di indici di animazione. Nell'esempio seguente è stata specificata l'animazione da riprodurre mentre l'utente sta guardando l'oggetto:

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
La semantica dei trigger di animazione seguente è supportata dalla Home realtà mista di Windows.  
* "ALWAYs": ciclo continuo di un'animazione
* "Mantenuto": ciclo durante l'intera durata dell'acquisizione di un oggetto.
* "Sguardo": viene eseguito il ciclo mentre un oggetto viene esaminato
* "Prossimità": ciclo mentre un visualizzatore è vicino a un oggetto
* "Puntatore": ciclo mentre un utente punta a un oggetto

### <a name="saving-and-exporting"></a>Salvataggio ed esportazione
Dopo aver apportato le modifiche al modello glTF, è possibile salvarlo direttamente come glTF oppure fare clic con il pulsante destro del mouse sul nome del file nell'editor e selezionare "glTF: Export to GLB (file binario)" per esportare invece un file con estensione glb. 

### <a name="restrictions"></a>Restrizioni
Le animazioni non possono essere più lunghe di 20 minuti e non possono contenere più di 36.000 fotogrammi chiave (20 minuti a 30 FPS). Inoltre, quando si usano le animazioni basate su morph target, non devono superare 8192 vertici di destinazione morph o meno. Il superamento di questi conteggi farà sì che l'asset animato non sia supportato nella Home realtà mista di Windows. 

|Caratteristica|Massimo|
|-----|-----|
|Durata|20 minuti|
|KeyFrames|36,000| 
|Vertici di destinazione morph|8192|

## <a name="gltf-implementation-notes"></a>Note sull'implementazione di glTF
Windows non supporta il capovolgimento della geometria utilizzando scale negative. La geometria con scale negative provocherà probabilmente artefatti visivi.

L'asset glTF deve puntare alla scena predefinita usando l'attributo della scena per il rendering da parte di Windows MR. Inoltre, il caricatore di Windows glTF prima dell' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md) **richiede** funzioni di accesso:
* Deve avere valori min e max.
* Il tipo SCALAr deve essere componentType UNSIGNED_SHORT (5123) o UNSIGNED_INT (5125).
* Il tipo VEC2 e VEC3 deve essere componentType FLOAT (5126).

Le seguenti proprietà del materiale vengono usate dalla specifica di core glTF 2,0, ma non sono necessarie:
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: deve puntare a una trama archiviata in DDS.
* emissiveTexture: deve puntare a una trama archiviata in DDS.
* emissiveFactor
* alphaMode

Le seguenti proprietà del materiale vengono ignorate dalla specifica di base:
* Tutte le più UV
* metalRoughnessTexture: è necessario usare invece la compressione di trama ottimizzata Microsoft definita di seguito
* normalTexture: è necessario usare invece la compressione di trama ottimizzata Microsoft definita di seguito
* normalScale
* occlusionTexture: è necessario usare invece la compressione di trama ottimizzata Microsoft definita di seguito
* occlusionStrength

Windows non supporta le linee e i punti della modalità primitive. 

È supportato solo un singolo attributo vertice UV.

## <a name="additional-resources"></a>Risorse aggiuntive
* [esportatori e convertitori glTF](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [Toolkit glTF](https://github.com/Microsoft/glTF-Toolkit)
* [Specifica glTF 2,0](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Specifica dell'estensione LOD Microsoft glTF](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Specifiche delle estensioni di compressione della trama della realtà mista PC](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens Mixed Reality texture Packaging Extensions Specification](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Specifica delle estensioni di Microsoft DDS Textures glTF](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Vedere anche

* [Implementare utilità di avvio per app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Implementare utilità di avvio per app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
