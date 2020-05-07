---
title: Rilevamento manuale in Unreal
description: Spiega come usare il rilevamento manuale in Unreal
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, rilevamento manuale
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835444"
---
# <a name="hand-tracking"></a>Rilevamento della mano

Il sistema di rilevamento manuale usa le palme e le dita di una persona come input per irreale. Uno sviluppatore può ottenere la posizione e la rotazione di ogni dito, l'intero Palm e persino i movimenti di mano da usare nel proprio codice. 

## <a name="hand-pose"></a>Hand Pose

Utilizzando la mano, gli sviluppatori possono tenere traccia delle mani e delle dita dell'utente attivo come input. Questo sistema viene esposto tramite progetti e C++. I dettagli tecnici si trovano nella classe WinRT corrispondente [Windows. Perception. people. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) questa API Unreal fornisce i dati nel formato di sistema di coordinate Unreal e i segni di selezione sono sincronizzati con il motore Unreal.

### <a name="enum"></a>Enum

EWMRHandKeypoint descrive la gerarchia ossea della mano. 

Progetto

![BP punto di riferimento della mano](images/unreal/hand-keypoint-bp.png)
 
C++:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![Scheletro mano](images/hand-skeleton.png)

I valori numerici sono disponibili nella tabella [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)
 
### <a name="functions"></a>Funzioni

Per usare le funzioni di rilevamento manuale nei progetti, aprire "rilevamento della mano/realtà mista di Windows"

![Verifica della mano BP](images/unreal/hand-tracking-bp.png)

Per le funzioni C++, includere "WindowsMixedRealityHandTrackingFunctionLibrary. h"

BP

![Supporta la verifica della mano BP](images/unreal/supports-hand-tracking-bp.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

Restituisce true se il rilevamento manuale è supportato nel dispositivo, false se la verifica della mano non è disponibile.

BP

![Ottenere la trasformazione congiunta della mano](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Questa funzione restituisce i dati spaziali della mano. I dati vengono aggiornati ogni frame, all'interno di un frame. i valori restituiti vengono memorizzati nella cache. Per motivi di prestazioni, non è consigliabile avere una logica intensa su questa funzione. 

* **Hand** -Hand dell'utente, può essere Left o right
* **Punto di riferimento** : l'osso della mano. 
* **Transform** : coordinate e orientamento della base dell'osso. Per ottenere i dati di trasformazione per la fine di un osso, è necessario che venga richiesta la base dell'osso successivo. Un osso Tip speciale fornisce la fine del valore distali. 
* **RADIUS** : raggio della base dell'osso.
* **Valore restituito** : true se l'osso rileva il frame, false se l'osso non viene rilevato.

## <a name="hand-live-link-animation"></a>Animazione collegamento dinamico
Le pose della mano vengono esposte all'animazione usando il plug-in live link. La documentazione del plug- [in è disponibile](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)

Se sono abilitati i plug-in per la realtà mista di Windows e il collegamento attivo, passare a **finestra > collegamento Live** per aprire la finestra Editor collegamento Live. Fare clic sul **pulsante + Source** e abilitare l'origine del rilevamento a mano della realtà mista di Windows

![Origine collegamento dinamico](images/unreal/live-link-source.png)
 
Dopo l'abilitazione dell'origine e l'apertura di qualsiasi asset di animazione, la scheda della scena di anteprima dell'animazione avrà le opzioni aggiuntive seguenti (i dettagli si trovano nella documentazione di collegamento in tempo reale, perché il plug-in è in versione beta, il processo può cambiare in seguito)

![Animazione collegamento dinamico](images/unreal/live-link-animation.png)
 
La gerarchia di animazione della mano è identica a quella di EWMRHandKeypoint. L'animazione può essere ridestinata usando WindowsMixedRealityHandTrackingLiveLinkRemapAsset. 

![Animazione collegamento dinamico 2](images/unreal/live-link-animation2.png)
 
Può essere sottoclassata nell'editor

![Modifica del mapping di Live link](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>Mesh mano
Mesh che rappresenta le mani dell'utente. 

![Mesh mano](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>Come abilitare e configurare

Gli sviluppatori possono ottenere l'accesso diretto ai mesh a mano per i propri scopi. Questo accesso deve essere abilitato in ARSessionConfig: AR Settings-> mapping del mondo-> generare dati mesh dalla geometria rilevata. 

Ecco i parametri predefiniti per le mesh:

1.  Usare i dati mesh per l'occlusione
2.  Genera collisione per i dati mesh
3.  Genera la mesh NAV per i dati mesh
4.  Eseguire il rendering dei dati mesh nel parametro wireframe-debug che mostra la mesh generata

Per i progetti di realtà mista, questi valori di parametro verranno usati come il mapping spaziale mesh e le impostazioni predefinite mesh a mano. Gli sviluppatori possono modificarli in BP o nel codice per qualsiasi mesh particolare.

### <a name="c-api-reference"></a>Informazioni di riferimento sulle API C++ 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

Questo valore è il mesh a mano tra tutti gli oggetti rilevabili.

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Questi delegati vengono chiamati quando il sistema rileva qualsiasi oggetto rilevabile, inclusa una mesh mano. 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
I gestori dei delegati devono avere la firma seguente:
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

È possibile accedere ai dati mesh`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>Riferimento all'API Blueprint

Gli sviluppatori devono aggiungere un componente di notifica di AR Trackable a un attore del progetto

![Notifica ARTrackable](images/unreal/ar-trackable-notify.png)
 
Passare quindi ai dettagli del componente 

![Notifica ARTrackable 2](images/unreal/ar-trackable-notify2.png)
 
E Sovrascrivi in Aggiungi/Aggiorna/Rimuovi geometria rilevata con codice simile al seguente:

![In ARTrackable notifica](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Raggi mano

Gli sviluppatori possono usare un raggio di mano come un dispositivo di puntamento. Il sistema è disponibile in C++ e progetto. Tecnicamente viene esposto [Windows. UI. input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)

È importante ricordare che, poiché i risultati di tutte le funzioni cambiano ogni frame, sono tutti resi richiamabili. Per ulteriori informazioni sulle funzioni non pure o richiamabili di Visual Studio [, vedere](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

Per il progetto aperto "Windows Mixed Reality HMD"

![Raggi mano BP](images/unreal/hand-rays-bp.png)
 
Per C++ includere "WindowsMixedRealityFunctionLibrary. h"

### <a name="enum"></a>Enum

![Pulsanti del controller di input](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* **Select** --l'utente ha attivato l'evento Select, che può essere attivato in HoloLens 2 da AirTap o lo sguardo e il commit. Un altro modo per attivare questo evento consiste nel pronunciare "Select". 
* **Afferrare** : l'evento di comprensione attivato dall'utente, che viene attivato in HoloLens 2 chiudendo le dita dell'utente su un ologramma. 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* **NotTracked** : la mano non è visibile
* **Rilevato** : la mano viene rilevata completamente

### <a name="struct"></a>Struct

![Indicatore di posa indicatore BP](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* **Origin** : origine della mano
* **Direzione** : direzione della mano
* Vettore **attivo** della mano
* **Orientamento** -quaternione orientamento 
* **Stato di rilevamento** -stato di rilevamento corrente

### <a name="functions"></a>Funzioni

Tutte le funzioni devono essere richiamabili in ogni frame per il monitoraggio continuo. 

![Ottenere le informazioni sulla posa del puntatore](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
La funzione restituisce le informazioni complete sulla direzione del raggio di mano in questo frame. 

![Viene afferrato BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
Restituisce true se la mano viene afferrata in questo frame. 

![Seleziona BP premuto](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
Restituisce true se l'utente ha attivato SELECT in questo frame.

![Pulsante è selezionato BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
Restituisce true se l'evento o il pulsante viene attivato in questo frame.

![Ottenere lo stato di rilevamento del controller BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
Restituisce lo stato di rilevamento in questo frame.

## <a name="gestures"></a>Movimenti

Hololens 2 consente di tenere traccia dei movimenti spaziali. Le informazioni dettagliate su questi movimenti [sono disponibili per](https://docs.microsoft.com/hololens/hololens2-basic-usage) gli sviluppatori che possono acquisirle come input per l'applicazione di realtà mista. 

La funzione C++ si trova in "WindowsMixedRealitySpatialInputFunctionLibrary. h"

La funzione Blueprint è nell'input spaziale di realtà mista di Windows

![Acquisisci movimenti](images/unreal/capture-gestures.png)

### <a name="enum"></a>Enum

![Tipo di movimento](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
Questa enumerazione descrive i movimenti dell'asse spaziale. È possibile leggere le informazioni [qui](holograms-211.md)

### <a name="function"></a>Function

![Movimenti di acquisizione BP](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
La funzione Abilita e Disabilita l'acquisizione dei movimenti. I movimenti abilitati generano eventi di input. Restituisce true se l'abilitazione dell'acquisizione del movimento è riuscita e false se si verifica un errore.
Eventi principali

![Eventi principali](images/unreal/key-events.png)

![Eventi chiave 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
Se il movimento è abilitato, inizia la generazione degli eventi. 

