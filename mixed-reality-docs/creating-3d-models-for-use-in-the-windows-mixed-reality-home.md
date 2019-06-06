---
title: Creare modelli 3D per l'uso nell'ambiente domestico
description: Requisiti di asset e linee guida per i modelli 3D da utilizzare per la realtà mista di Windows home su HoloLens e coinvolgenti auricolari (VR) di creazione.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Limiti di modellazione 3D, indicazioni, requisiti di asset, creazione di linee guida, utilità di avvio, 3D dell'utilità di avvio, la trama, materiali, complessità, triangoli, mesh, poligoni, polycount, di modellazione
ms.openlocfilehash: 73af40cf2915742cab612625c8243a36ee74d748
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692290"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Creare modelli 3D per l'uso nell'ambiente domestico

Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) è il punto iniziale in cui gli utenti ricevuti prima di avviare le applicazioni. È possibile progettare l'applicazione per le cuffie realtà mista di Windows di sfruttare una [un modello 3D come un'icona di avvio delle app](implementing-3d-app-launchers.md) e per consentire [3D collegamenti diretti da inserire nella realtà mista di Windows home](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) all'interno dell'app. Questo articolo illustra le linee guida per la creazione di modelli 3D compatibile con la realtà mista di Windows home.

## <a name="asset-requirements-overview"></a>Panoramica dei requisiti di asset
Durante la creazione di modelli 3D per realtà mista di Windows esistono alcuni requisiti che devono soddisfare tutti gli asset: 
1. [Esportazione](#exporting-models) -asset devono essere recapitati nel formato di file .glb (glTF binaria)
2. [Modellazione](#modeling-guidelines) -asset deve essere inferiore a 10 triangoli k, avere non più di 64 nodi e 32 submeshes per TRAMA
3. [Materiali](#material-guidelines) : non possono essere maggiore di 4096x4096 trame e le mappe mip più piccolo devono essere superiore a 4 su una dimensione
4. [Animazione](#animation-guidelines) -le animazioni non possono contenere più di 20 minuti 30 fps (36.000 fotogrammi chiave) e può contenere < = 8192 vertici di destinazione morph
5. [Ottimizzazione](#optimizations) -asset devono essere ottimizzati usando il [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). Si tratta **necessarie nelle versioni del sistema operativo Windows < = 1709** e consigliato nelle versioni del sistema operativo Windows > = 1803

Il resto di questo articolo include una panoramica dettagliata di questi requisiti, nonché le ulteriori linee guida per assicurarsi che i modelli funzionano bene con la realtà mista di Windows home. 

## <a name="detailed-guidance"></a>Indicazioni dettagliate

### <a name="exporting-models"></a>Esportazione di modelli

La realtà mista di Windows home prevede che gli asset 3D da recapitare usando il formato di file .glb con immagini incorporate e i dati binari. Glb è la versione binaria del formato di glTF ovvero royalty gratuita standard aperto per il recapito di asset 3D gestito dal gruppo di Khronos. Evolversi glTF come standard per il contenuto 3D interoperativo di settore tra esperienze e le app di Windows verrà così il supporto Microsoft per il formato. Se è stato ancora creato un asset glTF prima di poter trovare una [elenco di utilità di esportazione supportati e i convertitori](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) nella pagina github del gruppo di lavoro glTF.  

### <a name="modeling-guidelines"></a>Linee guida per la modellazione delle minacce

Windows prevede che l'asset deve essere generato usando le linee guida di modellazione seguenti per garantire la compatibilità con l'esperienza iniziale di realtà mista. Durante la modellazione nel programma di propria scelta tenere presente le raccomandazioni e le limitazioni seguenti:
1. L'asse verticale deve essere impostato su "Y".
2. L'asset debba affrontare "forward" rispetto all'asse Z positivo.
3. Tutte le risorse devono essere compilate nel piano di massa in corrispondenza dell'origine della scena (0, 0,0)
4. Unità di lavoro deve essere impostata per i contatori e gli asset in modo che gli asset possono essere creati su scala mondiale
5. Non è necessario che tutte le trame kombinovat s ma è consigliabile se si sviluppano App per dispositivi con risorse limitate
6. Tutte le reti mesh deve condividere 1 materiale, con 1 sola trama impostata viene utilizzato per l'intero asset
7. UVs deve essere disposto in una disposizione quadrata in 0-1 dello spazio. Evitare le trame di affiancamento anche se sono ammessi.
8. Multi-UVs non sono supportati
9. Materiali faccia doppie non sono supportati

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Triangolo conteggi e i livelli di dettaglio (LOD)

La realtà mista di Windows home non supporta i modelli con più di 10.000 triangoli. È consigliabile che il mesh triangolare prima dell'esportazione per garantire che non superano questo conteggio. MR Windows supporta inoltre livelli di geometria facoltativo di dettaglio (LOD) per garantire un'esperienza di qualità elevata e ad alte prestazioni. [Il WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) consentono di combinare 3 versioni del modello in un modello .glb singolo. Windows determina quale della TRAMA per la visualizzazione in base alla quantità di superficie sullo schermo che sta utilizzando il modello. Solo 3 livelli di LOD sono supportati con gli elementi seguenti consigliati triangolo conteggi:
<br>

|  Livello della TRAMA  |  Conteggio triangolo consigliato  |  Numero massimo di triangolo | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>Il sottomesh limiti e i conteggi di nodo
La realtà mista di Windows home non supporta i modelli con più di 64 nodi o 32 submeshes per TRAMA. I nodi sono un concetto del [glTF specifica](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) che definiscono gli oggetti nella scena. Submeshes sono definiti nella matrice di [primitive](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) nel mesh nell'oggetto. 

|  Funzionalità |  Descrizione  |  Numero massimo supportato | Documentazione |
|------|------|------|------|
|  Nodi |  Oggetti in glTF scena |  64 per TRAMA | [Qui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  Somma delle primitive in tutte le trame |  32 per TRAMA | [Qui](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Linee guida materiale

Le trame devono essere preparate con un flusso di lavoro PBR asperità bare metal. Iniziare creando un set completo di trame Albedo, normale, relative all'occlusione, metallici e disturbo. Realtà mista di Windows supporta trame con le risoluzioni fino a 4096x4096 ma si consiglia di autore a 512 x 512. Le trame inoltre devono essere create con risoluzioni in multipli di 4, poiché si tratta di un requisito per il formato di compressione applicato alle trame nell'esportazione passaggi descritti di seguito. Infine, quando viene eseguito il mapping mip gerating o una trama di mip più basso debba contenere un massimo di 4 x 4.
<br>

|  Dimensioni trama consigliate  |  Dimensioni della trama max | Mip più basso
|----|----|----|
|  512x512  |  4096x4096 | max 4x4|

### <a name="albedo-base-color-map"></a>Mappa albedo (colore di base)

Colori non elaborati senza informazioni di illuminazione. Questa mappa contiene inoltre il riflettanza e con riflessione diffusa per bare metal (bianco nella mappa metallica) e le superfici insulator (nero nella mappa metallica) rispettivamente.

### <a name="normal"></a>Normale

Mappa di normali spazio tangente

### <a name="roughness-map"></a>Mapping dei asperità

Viene descritto il microsurface dell'oggetto. White 1.0 è approssimativa nero 0.0 è uniforme. Questa mappa offre l'asset che più caratteri in quanto realmente descrive l'area, ad esempio generica, le impronte digitali, sbavature, grime e così via.

### <a name="ambient-occlusion-map"></a>Mappa di ambiente relative all'occlusione

Mappa di scala di valori che descrivono le aree della luce bloccati che blocca i riflessi

### <a name="metallic-map"></a>Mappa metallica

Indica lo shader se qualcosa è bare metal o meno. Bare Metal non elaborati = 1,0 bare metal Non bianco = 0,0 nero. Possono esserci valori grigio transitori che forniscono indicazioni che coprono le bare metal non elaborati, ad esempio sporco, ma in genere questa mappa deve essere solo in bianco e nero.

## <a name="optimizations"></a>ottimizzazioni

Realtà mista di Windows home offre una serie di ottimizzazioni sopra la specifica di glTF core definiti usando le estensioni personalizzate. Queste ottimizzazioni sono obbligatori in versioni di Windows < = 1709 e consigliato nelle versioni più recenti di Windows. È possibile ottimizzare facilmente qualsiasi modello glTF 2.0 utilizzando la [mista realtà Asset convertitore Windows disponibile in GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Questo strumento esegue la trama corretta di compressione e le ottimizzazioni come specificato di seguito. Per l'utilizzo generale è consigliabile usare il WindowsMRAssetConverter, ma se è necessario maggiore controllo sull'esperienza e si vuole creare la propria pipeline per l'ottimizzazione quindi è possibile fare riferimento alla specifica dettagliata riportato di seguito.  

### <a name="materials"></a>Materiali

Per migliorare il tempo in ambienti di realtà mista Windows MR di caricamento di asset supporta il rendering le trame compresse di DDS compresse in base alla trama schema definito in questa sezione di compressione. Le trame DDS vengono fatto riferimento tramite il [MSFT_texture_dds estensione](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). La compressione delle trame è vivamente consigliata. 

#### <a name="hololens"></a>HoloLens

Esperienze basate su HoloLens realtà mista prevede che le trame per essere compresse utilizzando un programma di installazione 2 a trama utilizzando la specifica di compressione seguenti:
<br>

|  glTF proprietà  |  Trama  |  Schema di compressione | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R) e verde (G), blu (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normale (RG), (B), asperità metallici (A) | 


Quando si comprime le trame DDS su ogni mappa è previsto la compressione seguente:
<br>

|  Trama  |  Previsto la compressione | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Immersive auricolari (VR)

Esperienze di realtà mista di Windows basati su PC per immersive auricolari (VR) prevede che le trame per essere compresse utilizzando un programma di installazione di 3 a trama utilizzando la specifica di compressione seguenti:

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  glTF proprietà  |  Trama  |  Schema di compressione | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R) e verde (G), blu (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R), asperità (G), metallici (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normale (RG) | 

Quando si comprime le trame DDS su ogni mappa è previsto la compressione seguente:
<br>

|  Trama  |  Previsto la compressione | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  glTF proprietà  |  Trama  |  Schema di compressione | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rosso (R) e verde (G), blu (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  ROUGHNESS (R), metallici (G), relative all'occlusione (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normale (RG) | 

Quando si comprime le trame DDS su ogni mappa è previsto la compressione seguente:
<br>

|  Trama  |  Previsto la compressione | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Aggiunta mesh LOD

MR Windows Usa nodo geometry LOD per il rendering di modelli 3D in diversi livelli di dettaglio in base alla copertura dello schermo. Anche questa funzionalità non è tecnicamente obbligatorio, è consigliabile per tutti gli asset. Windows supporta attualmente 3 livelli di dettaglio. Il valore predefinito della TRAMA è 0, che rappresenta la qualità più elevata. Altri LOD sono numerate in sequenza, ad esempio, 1, 2 e get progressivamente più basso della qualità. Il [convertitore Asset per realtà mista Windows](https://github.com/Microsoft/glTF-Toolkit/releases) supporta la generazione di risorse che soddisfano tali requisiti della TRAMA accettando più modelli glTF e unirli in un singolo asset con i livelli validi della TRAMA. La tabella seguente descrive gli obiettivi di ordinamento e triangolo LOD previsto:
<br>

|  Livello della TRAMA  |  Conteggio triangolo consigliato  |  Numero massimo di triangolo | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

Quando si usa sempre LOD specificare 3 livelli della TRAMA. Missing LOD causerà il modello per non eseguire il rendering in modo imprevisto come le opzioni di sistema della TRAMA al livello di LOD manca. glTF 2.0 non supporta attualmente LOD come parte della specifica di core. LOD deve pertanto essere definite utilizzando la [estensione MSFT_LOD](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).

### <a name="screen-coverage"></a>Code coverage dello schermo

LOD vengono visualizzati in realtà mista di Windows basato su un sistema dovuto al valore di code coverage schermata impostato su ogni della TRAMA. Gli oggetti che attualmente utilizzano una porzione più grande dello spazio dello schermo vengono visualizzati a un livello superiore della TRAMA. Code coverage schermata non è una parte della specifica di glTF 2.0 core e deve essere specificata tramite MSFT_ScreenCoverage nella sezione "extra" del [MSFT_lod estensione](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  Livello della TRAMA  |  Intervallo consigliato  |  L'intervallo predefinito | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  .5 | 
|  LOD 1 |  Sotto il 50% - 20%  |  .2 | 
|  LOD 2 |  Sotto il 20% - 1%  |  .01 | 
|  LOD 4  |  In % 1  |  - | 

## <a name="animation-guidelines"></a>Linee guida di animazione

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte della [Windows 10 April 2018 Update](release-notes-april-2018.md). Nelle versioni precedenti di Windows queste animazioni non verranno riprodotti, tuttavia, sono comunque caricherà se creato seguendo le istruzioni riportate in questo articolo.  

La home page di realtà mista supporta glTF animata oggetti su HoloLens e coinvolgenti auricolari (VR). Se si desidera attivare le animazioni sul modello, è necessario usare l'estensione di mapping di animazione sul formato glTF. Questa estensione consente di attivare le animazioni nel modello glTF in base alla presenza di utenti in tutto il mondo, ad esempio attivare un'animazione quando l'utente è in prossimità dell'oggetto o mentre si stanno analizzando. Se si glTF oggetto dispone di animazioni, ma non definisce i trigger le animazioni verranno non riprodotte. La sezione seguente descrive un flusso di lavoro per l'aggiunta di questi trigger per qualsiasi oggetto glTF animata.

### <a name="tools"></a>Strumenti
Scaricare gli strumenti seguenti in primo luogo, se non si dispone già. Questi strumenti renderà più facile aprire qualsiasi modello glTF, visualizzarlo in anteprima, apportare le modifiche e salvare nuovamente out glTF o .glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [glTF Tools per Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Apertura e visualizzazione in anteprima il modello
Iniziare aprendo il modello glTF in VSCode trascinando il file .glTF nella finestra dell'editor. Si noti che se hai un .glb anziché un file .glTF è possibile importarlo in VSCode mediante il componente aggiuntivo Strumenti glTF scaricato. Passare a "Riquadro comandi Visualizza ->" e quindi iniziare a digitare "glTF" nel riquadro comandi e selezionare "glTF: Importa da glb"che verrà visualizzata una selezione di file per importare un .glb con. 

Dopo aver aperto il modello glTF verrà visualizzato il codice JSON nella finestra dell'editor. Si noti che è possibile anche visualizzare in anteprima il modello in un visualizzatore 3D in tempo reale usando il pulsante destro del mouse sul nome file e selezionando le "glTF: Anteprima modello 3D di"collegamento comando dal menu di scelta rapida. 

### <a name="adding-the-triggers"></a>L'aggiunta dei trigger
Trigger animazione vengono aggiunti al modello glTF JSON usando l'estensione di mapping di animazione. L'estensione di mapping di animazione è pubblicamente documentata [in GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (Nota: QUESTA È UN'ESTENSIONE DI BOZZA). Per aggiungere l'estensione di scorrimento solo modello alla fine del file glTF nell'editor e aggiungere il blocco "extensionsUsed" e "estensioni" al file se non sono già presenti. Nella sezione "extensionsUsed" verrà aggiunto un riferimento all'estensione "EXT_animation_map" e nel blocco di "estensioni" si aggiungeranno i mapping per le animazioni nel modello.

Come notato [nella specifica](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) si definiscono che cosa attiva l'animazione usando la stringa "semantica" in un elenco di "animazioni" che è una matrice di indici di animazione. Nell'esempio seguente è stato indicato l'animazione venga eseguita anche se l'utente è gazing all'oggetto:

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
La semantica di trigger animazione seguenti è supportata da casa la realtà mista di Windows.  
* "SEMPRE": Ciclo costantemente un'animazione
* "SOSPENSIONE": Un oggetto riattivando l'intera durata acquisizione.
* "SGUARDO": Chiuso mentre si sta visualizzando un oggetto
* "VICINANZA": Chiuso durante un visualizzatore è nelle vicinanze di un oggetto
* "POINTING": Chiuso anche se un utente punta a un oggetto

### <a name="saving-and-exporting"></a>Salvataggio ed esportazione
Una volta apportate le modifiche al modello glTF è possibile salvarlo direttamente come glTF o è possibile con il pulsante destro fare clic sul nome del file nell'editor e selezionare "glTF: Esportare in GLB (file binario) "per esportare invece un .glb. 

### <a name="restrictions"></a>Restrizioni
Le animazioni non possono contenere più di 20 minuti e non possono contenere più di 36.000 fotogrammi chiave (20 minuti 30 fps). Inoltre quando si usa destinazione morph basato le animazioni non superino i vertici di destinazione 8192 morph o meno. Superamento causare questi verranno conteggio bene animato non saranno supportate nella home page di realtà mista di Windows. 

|Funzionalità|Massimo|
|-----|-----|
|Durata|20 minuti|
|Fotogrammi chiave|36,000| 
|Morph destinazione vertici|8192|

## <a name="gltf-implementation-notes"></a>note sull'implementazione glTF
MR Windows non supporta la geometria di capovolgimento utilizzando scale negative. Geometria con scale negativo determinerà probabilmente in elementi visivi.

L'asset glTF deve puntare alla scena predefinita usando l'attributo scena per eseguire il rendering da Windows MR. Anche il caricatore glTF SIG Windows precedenti al [Windows 10 April 2018 update](release-notes-april-2018.md) **richiede** le funzioni di accesso:
* Deve avere i valori minimo e massimo.
* Tipo di valore SCALARE deve essere componentType UNSIGNED_SHORT (5123) o UNSIGNED_INT (5125).
* Tipo VEC2 e VEC3 devono essere componentType FLOAT (5126).

Le proprietà di materiali seguenti vengono utilizzate dalla specifica glTF 2.0 core ma non necessari:
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: Deve puntare a una trama archiviata in dds.
* emissiveTexture: Deve puntare a una trama archiviata in dds.
* emissiveFactor
* alphaMode

Le proprietà di materiali seguenti vengono ignorate dalla specifica di core:
* Multi-UVs tutti
* metalRoughnessTexture: È necessario usare invece compressione di trama Microsoft ottimizzato definito di seguito
* normalTexture: È necessario usare invece compressione di trama Microsoft ottimizzato definito di seguito
* normalScale
* occlusionTexture: È necessario usare invece compressione di trama Microsoft ottimizzato definito di seguito
* occlusionStrength

MR Windows non supporta i punti e linee di modalità primitivo. 

È supportato solo un singolo attributo di vertice UV.

## <a name="additional-resources"></a>Risorse aggiuntive
* [utilità di esportazione glTF e convertitori di tipi](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 Specification](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF specifica di estensione della TRAMA](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC specifica delle estensioni compressione della trama realtà mista](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens specifica delle estensioni compressione della trama realtà mista](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Specifica delle estensioni Microsoft DDS trame glTF](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Vedere anche

* [Implementare utilità di avvio per app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Implementare utilità di avvio per app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
