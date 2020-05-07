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
# <a name="hand-tracking"></a><span data-ttu-id="16310-104">Rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="16310-104">Hand Tracking</span></span>

<span data-ttu-id="16310-105">Il sistema di rilevamento manuale usa le palme e le dita di una persona come input per irreale.</span><span class="sxs-lookup"><span data-stu-id="16310-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="16310-106">Uno sviluppatore può ottenere la posizione e la rotazione di ogni dito, l'intero Palm e persino i movimenti di mano da usare nel proprio codice.</span><span class="sxs-lookup"><span data-stu-id="16310-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="16310-107">Hand Pose</span><span class="sxs-lookup"><span data-stu-id="16310-107">Hand Pose</span></span>

<span data-ttu-id="16310-108">Utilizzando la mano, gli sviluppatori possono tenere traccia delle mani e delle dita dell'utente attivo come input.</span><span class="sxs-lookup"><span data-stu-id="16310-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="16310-109">Questo sistema viene esposto tramite progetti e C++.</span><span class="sxs-lookup"><span data-stu-id="16310-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="16310-110">I dettagli tecnici si trovano nella classe WinRT corrispondente [Windows. Perception. people. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) questa API Unreal fornisce i dati nel formato di sistema di coordinate Unreal e i segni di selezione sono sincronizzati con il motore Unreal.</span><span class="sxs-lookup"><span data-stu-id="16310-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="16310-111">Enum</span><span class="sxs-lookup"><span data-stu-id="16310-111">Enum</span></span>

<span data-ttu-id="16310-112">EWMRHandKeypoint descrive la gerarchia ossea della mano.</span><span class="sxs-lookup"><span data-stu-id="16310-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="16310-113">Progetto</span><span class="sxs-lookup"><span data-stu-id="16310-113">Blueprint:</span></span>

![BP punto di riferimento della mano](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="16310-115">C++:</span><span class="sxs-lookup"><span data-stu-id="16310-115">C++:</span></span>
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

<span data-ttu-id="16310-117">I valori numerici sono disponibili nella tabella [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span><span class="sxs-lookup"><span data-stu-id="16310-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="16310-118">Funzioni</span><span class="sxs-lookup"><span data-stu-id="16310-118">Functions</span></span>

<span data-ttu-id="16310-119">Per usare le funzioni di rilevamento manuale nei progetti, aprire "rilevamento della mano/realtà mista di Windows"</span><span class="sxs-lookup"><span data-stu-id="16310-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![Verifica della mano BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="16310-121">Per le funzioni C++, includere "WindowsMixedRealityHandTrackingFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="16310-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="16310-122">BP</span><span class="sxs-lookup"><span data-stu-id="16310-122">BP:</span></span>

![Supporta la verifica della mano BP](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="16310-124">C++:</span><span class="sxs-lookup"><span data-stu-id="16310-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="16310-125">Restituisce true se il rilevamento manuale è supportato nel dispositivo, false se la verifica della mano non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="16310-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="16310-126">BP</span><span class="sxs-lookup"><span data-stu-id="16310-126">BP:</span></span>

![Ottenere la trasformazione congiunta della mano](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="16310-128">C++:</span><span class="sxs-lookup"><span data-stu-id="16310-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="16310-129">Questa funzione restituisce i dati spaziali della mano.</span><span class="sxs-lookup"><span data-stu-id="16310-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="16310-130">I dati vengono aggiornati ogni frame, all'interno di un frame. i valori restituiti vengono memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="16310-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="16310-131">Per motivi di prestazioni, non è consigliabile avere una logica intensa su questa funzione.</span><span class="sxs-lookup"><span data-stu-id="16310-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="16310-132">**Hand** -Hand dell'utente, può essere Left o right</span><span class="sxs-lookup"><span data-stu-id="16310-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="16310-133">**Punto di riferimento** : l'osso della mano.</span><span class="sxs-lookup"><span data-stu-id="16310-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="16310-134">**Transform** : coordinate e orientamento della base dell'osso.</span><span class="sxs-lookup"><span data-stu-id="16310-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="16310-135">Per ottenere i dati di trasformazione per la fine di un osso, è necessario che venga richiesta la base dell'osso successivo.</span><span class="sxs-lookup"><span data-stu-id="16310-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="16310-136">Un osso Tip speciale fornisce la fine del valore distali.</span><span class="sxs-lookup"><span data-stu-id="16310-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="16310-137">**RADIUS** : raggio della base dell'osso.</span><span class="sxs-lookup"><span data-stu-id="16310-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="16310-138">**Valore restituito** : true se l'osso rileva il frame, false se l'osso non viene rilevato.</span><span class="sxs-lookup"><span data-stu-id="16310-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="16310-139">Animazione collegamento dinamico</span><span class="sxs-lookup"><span data-stu-id="16310-139">Hand Live Link Animation</span></span>
<span data-ttu-id="16310-140">Le pose della mano vengono esposte all'animazione usando il plug-in live link.</span><span class="sxs-lookup"><span data-stu-id="16310-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="16310-141">La documentazione del plug- [in è disponibile](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span><span class="sxs-lookup"><span data-stu-id="16310-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="16310-142">Se sono abilitati i plug-in per la realtà mista di Windows e il collegamento attivo, passare a **finestra > collegamento Live** per aprire la finestra Editor collegamento Live.</span><span class="sxs-lookup"><span data-stu-id="16310-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="16310-143">Fare clic sul **pulsante + Source** e abilitare l'origine del rilevamento a mano della realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="16310-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![Origine collegamento dinamico](images/unreal/live-link-source.png)
 
<span data-ttu-id="16310-145">Dopo l'abilitazione dell'origine e l'apertura di qualsiasi asset di animazione, la scheda della scena di anteprima dell'animazione avrà le opzioni aggiuntive seguenti (i dettagli si trovano nella documentazione di collegamento in tempo reale, perché il plug-in è in versione beta, il processo può cambiare in seguito)</span><span class="sxs-lookup"><span data-stu-id="16310-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![Animazione collegamento dinamico](images/unreal/live-link-animation.png)
 
<span data-ttu-id="16310-147">La gerarchia di animazione della mano è identica a quella di EWMRHandKeypoint.</span><span class="sxs-lookup"><span data-stu-id="16310-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="16310-148">L'animazione può essere ridestinata usando WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span><span class="sxs-lookup"><span data-stu-id="16310-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![Animazione collegamento dinamico 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="16310-150">Può essere sottoclassata nell'editor</span><span class="sxs-lookup"><span data-stu-id="16310-150">It can be subclassed in the editor</span></span>

![Modifica del mapping di Live link](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="16310-152">Mesh mano</span><span class="sxs-lookup"><span data-stu-id="16310-152">Hand Mesh</span></span>
<span data-ttu-id="16310-153">Mesh che rappresenta le mani dell'utente.</span><span class="sxs-lookup"><span data-stu-id="16310-153">Mesh representing the user hands.</span></span> 

![Mesh mano](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="16310-155">Come abilitare e configurare</span><span class="sxs-lookup"><span data-stu-id="16310-155">How to enable and configure</span></span>

<span data-ttu-id="16310-156">Gli sviluppatori possono ottenere l'accesso diretto ai mesh a mano per i propri scopi.</span><span class="sxs-lookup"><span data-stu-id="16310-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="16310-157">Questo accesso deve essere abilitato in ARSessionConfig: AR Settings-> mapping del mondo-> generare dati mesh dalla geometria rilevata.</span><span class="sxs-lookup"><span data-stu-id="16310-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="16310-158">Ecco i parametri predefiniti per le mesh:</span><span class="sxs-lookup"><span data-stu-id="16310-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="16310-159">Usare i dati mesh per l'occlusione</span><span class="sxs-lookup"><span data-stu-id="16310-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="16310-160">Genera collisione per i dati mesh</span><span class="sxs-lookup"><span data-stu-id="16310-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="16310-161">Genera la mesh NAV per i dati mesh</span><span class="sxs-lookup"><span data-stu-id="16310-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="16310-162">Eseguire il rendering dei dati mesh nel parametro wireframe-debug che mostra la mesh generata</span><span class="sxs-lookup"><span data-stu-id="16310-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="16310-163">Per i progetti di realtà mista, questi valori di parametro verranno usati come il mapping spaziale mesh e le impostazioni predefinite mesh a mano.</span><span class="sxs-lookup"><span data-stu-id="16310-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="16310-164">Gli sviluppatori possono modificarli in BP o nel codice per qualsiasi mesh particolare.</span><span class="sxs-lookup"><span data-stu-id="16310-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="16310-165">Informazioni di riferimento sulle API C++</span><span class="sxs-lookup"><span data-stu-id="16310-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="16310-166">Questo valore è il mesh a mano tra tutti gli oggetti rilevabili.</span><span class="sxs-lookup"><span data-stu-id="16310-166">This value is the hand mesh among all trackable objects.</span></span>

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

<span data-ttu-id="16310-167">Questi delegati vengono chiamati quando il sistema rileva qualsiasi oggetto rilevabile, inclusa una mesh mano.</span><span class="sxs-lookup"><span data-stu-id="16310-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="16310-168">I gestori dei delegati devono avere la firma seguente:</span><span class="sxs-lookup"><span data-stu-id="16310-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="16310-169">È possibile accedere ai dati mesh`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="16310-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="16310-170">Riferimento all'API Blueprint</span><span class="sxs-lookup"><span data-stu-id="16310-170">Blueprint API Reference</span></span>

<span data-ttu-id="16310-171">Gli sviluppatori devono aggiungere un componente di notifica di AR Trackable a un attore del progetto</span><span class="sxs-lookup"><span data-stu-id="16310-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![Notifica ARTrackable](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="16310-173">Passare quindi ai dettagli del componente</span><span class="sxs-lookup"><span data-stu-id="16310-173">Then go to the component’s details</span></span> 

![Notifica ARTrackable 2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="16310-175">E Sovrascrivi in Aggiungi/Aggiorna/Rimuovi geometria rilevata con codice simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="16310-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![In ARTrackable notifica](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="16310-177">Raggi mano</span><span class="sxs-lookup"><span data-stu-id="16310-177">Hand Rays</span></span>

<span data-ttu-id="16310-178">Gli sviluppatori possono usare un raggio di mano come un dispositivo di puntamento.</span><span class="sxs-lookup"><span data-stu-id="16310-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="16310-179">Il sistema è disponibile in C++ e progetto.</span><span class="sxs-lookup"><span data-stu-id="16310-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="16310-180">Tecnicamente viene esposto [Windows. UI. input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span><span class="sxs-lookup"><span data-stu-id="16310-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="16310-181">È importante ricordare che, poiché i risultati di tutte le funzioni cambiano ogni frame, sono tutti resi richiamabili.</span><span class="sxs-lookup"><span data-stu-id="16310-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="16310-182">Per ulteriori informazioni sulle funzioni non pure o richiamabili di Visual Studio [, vedere](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="16310-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="16310-183">Per il progetto aperto "Windows Mixed Reality HMD"</span><span class="sxs-lookup"><span data-stu-id="16310-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![Raggi mano BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="16310-185">Per C++ includere "WindowsMixedRealityFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="16310-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="16310-186">Enum</span><span class="sxs-lookup"><span data-stu-id="16310-186">Enum</span></span>

![Pulsanti del controller di input](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="16310-188">**Select** --l'utente ha attivato l'evento Select, che può essere attivato in HoloLens 2 da AirTap o lo sguardo e il commit.</span><span class="sxs-lookup"><span data-stu-id="16310-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="16310-189">Un altro modo per attivare questo evento consiste nel pronunciare "Select".</span><span class="sxs-lookup"><span data-stu-id="16310-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="16310-190">**Afferrare** : l'evento di comprensione attivato dall'utente, che viene attivato in HoloLens 2 chiudendo le dita dell'utente su un ologramma.</span><span class="sxs-lookup"><span data-stu-id="16310-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="16310-191">**NotTracked** : la mano non è visibile</span><span class="sxs-lookup"><span data-stu-id="16310-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="16310-192">**Rilevato** : la mano viene rilevata completamente</span><span class="sxs-lookup"><span data-stu-id="16310-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="16310-193">Struct</span><span class="sxs-lookup"><span data-stu-id="16310-193">Struct</span></span>

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
* <span data-ttu-id="16310-195">**Origin** : origine della mano</span><span class="sxs-lookup"><span data-stu-id="16310-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="16310-196">**Direzione** : direzione della mano</span><span class="sxs-lookup"><span data-stu-id="16310-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="16310-197">Vettore **attivo** della mano</span><span class="sxs-lookup"><span data-stu-id="16310-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="16310-198">**Orientamento** -quaternione orientamento</span><span class="sxs-lookup"><span data-stu-id="16310-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="16310-199">**Stato di rilevamento** -stato di rilevamento corrente</span><span class="sxs-lookup"><span data-stu-id="16310-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="16310-200">Funzioni</span><span class="sxs-lookup"><span data-stu-id="16310-200">Functions</span></span>

<span data-ttu-id="16310-201">Tutte le funzioni devono essere richiamabili in ogni frame per il monitoraggio continuo.</span><span class="sxs-lookup"><span data-stu-id="16310-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![Ottenere le informazioni sulla posa del puntatore](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="16310-203">La funzione restituisce le informazioni complete sulla direzione del raggio di mano in questo frame.</span><span class="sxs-lookup"><span data-stu-id="16310-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![Viene afferrato BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="16310-205">Restituisce true se la mano viene afferrata in questo frame.</span><span class="sxs-lookup"><span data-stu-id="16310-205">Returns true if the hand is grasped in this frame.</span></span> 

![Seleziona BP premuto](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="16310-207">Restituisce true se l'utente ha attivato SELECT in questo frame.</span><span class="sxs-lookup"><span data-stu-id="16310-207">Returns true if the user triggered Select in this frame.</span></span>

![Pulsante è selezionato BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="16310-209">Restituisce true se l'evento o il pulsante viene attivato in questo frame.</span><span class="sxs-lookup"><span data-stu-id="16310-209">Returns true if the event/button is triggered in this frame.</span></span>

![Ottenere lo stato di rilevamento del controller BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="16310-211">Restituisce lo stato di rilevamento in questo frame.</span><span class="sxs-lookup"><span data-stu-id="16310-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="16310-212">Movimenti</span><span class="sxs-lookup"><span data-stu-id="16310-212">Gestures</span></span>

<span data-ttu-id="16310-213">Hololens 2 consente di tenere traccia dei movimenti spaziali.</span><span class="sxs-lookup"><span data-stu-id="16310-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="16310-214">Le informazioni dettagliate su questi movimenti [sono disponibili per](https://docs.microsoft.com/hololens/hololens2-basic-usage) gli sviluppatori che possono acquisirle come input per l'applicazione di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="16310-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="16310-215">La funzione C++ si trova in "WindowsMixedRealitySpatialInputFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="16310-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="16310-216">La funzione Blueprint è nell'input spaziale di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="16310-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![Acquisisci movimenti](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="16310-218">Enum</span><span class="sxs-lookup"><span data-stu-id="16310-218">Enum</span></span>

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
<span data-ttu-id="16310-220">Questa enumerazione descrive i movimenti dell'asse spaziale.</span><span class="sxs-lookup"><span data-stu-id="16310-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="16310-221">È possibile leggere le informazioni [qui](holograms-211.md)</span><span class="sxs-lookup"><span data-stu-id="16310-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="16310-222">Function</span><span class="sxs-lookup"><span data-stu-id="16310-222">Function</span></span>

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
<span data-ttu-id="16310-224">La funzione Abilita e Disabilita l'acquisizione dei movimenti.</span><span class="sxs-lookup"><span data-stu-id="16310-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="16310-225">I movimenti abilitati generano eventi di input.</span><span class="sxs-lookup"><span data-stu-id="16310-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="16310-226">Restituisce true se l'abilitazione dell'acquisizione del movimento è riuscita e false se si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="16310-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="16310-227">Eventi principali</span><span class="sxs-lookup"><span data-stu-id="16310-227">Key Events</span></span>

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
<span data-ttu-id="16310-230">Se il movimento è abilitato, inizia la generazione degli eventi.</span><span class="sxs-lookup"><span data-stu-id="16310-230">If the gesture is enabled, the events begin firing.</span></span> 

