---
title: I movimenti e i controller di movimento in Unity
description: Esistono due modi principali per agire sullo sguardo in Unity, movimenti della mano e controller di movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: i movimenti, i controller di movimento, unity, sguardo, di input
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597653"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="0ed81-104">I movimenti e i controller di movimento in Unity</span><span class="sxs-lookup"><span data-stu-id="0ed81-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="0ed81-105">Esistono due modi principali per agire sul [estasiati Unity](gaze-in-unity.md), [mano i movimenti](gestures.md) e [controller di movimento](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="0ed81-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="0ed81-106">Accedere ai dati per entrambe le origini di input spaziali tramite le stesse API in Unity.</span><span class="sxs-lookup"><span data-stu-id="0ed81-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="0ed81-107">Unity offre due metodi principali per accedere ai dati di input spaziali per realtà mista di Windows, comuni *Input.GetButton/Input.GetAxis* API che funzionano tra più SDK per Unity XR, e un *InteractionManager / GestureRecognizer* API specifiche in Windows Mixed Reality che espone il set completo di dati di input spaziali disponibili.</span><span class="sxs-lookup"><span data-stu-id="0ed81-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="0ed81-108">Tabella di mapping pulsante/asse di Unity</span><span class="sxs-lookup"><span data-stu-id="0ed81-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="0ed81-109">Gli ID del pulsante e asse nella tabella seguente sono supportati in Unity Input Manager per i controller del movimento di realtà mista di Windows tramite il *Input.GetButton/GetAxis* API, mentre la colonna di "MR Windows specifiche" si riferisce alle proprietà disponibili all'esterno della *InteractionSourceState* tipo.</span><span class="sxs-lookup"><span data-stu-id="0ed81-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="0ed81-110">Ognuna di queste API sono descritte in dettaglio nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="0ed81-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="0ed81-111">Il mapping di ID pulsante/asse per realtà mista di Windows corrisponde in genere Oculus pulsante/ID asse.</span><span class="sxs-lookup"><span data-stu-id="0ed81-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="0ed81-112">I mapping di ID del pulsante/asse per realtà mista di Windows sono diversi dai mapping di OpenVR in due modi:</span><span class="sxs-lookup"><span data-stu-id="0ed81-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="0ed81-113">Il mapping utilizza gli ID touchpad sono distinti dagli thumbstick, per supportare i controller con levette e touchpad multipli.</span><span class="sxs-lookup"><span data-stu-id="0ed81-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="0ed81-114">Il mapping consente di evitare l'overload il pulsante A e X ID per i pulsanti di Menu, lasciare quelli disponibili per i pulsanti fisici ABXY.</span><span class="sxs-lookup"><span data-stu-id="0ed81-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="0ed81-115">Input</span><span class="sxs-lookup"><span data-stu-id="0ed81-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="0ed81-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API comuni di Unity</a></span><span class="sxs-lookup"><span data-stu-id="0ed81-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="0ed81-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="0ed81-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="0ed81-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">API di Input specifica MR Windows</a></span><span class="sxs-lookup"><span data-stu-id="0ed81-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="0ed81-119">(XR. WSA. Input)</span><span class="sxs-lookup"><span data-stu-id="0ed81-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="0ed81-120">A sinistra</span><span class="sxs-lookup"><span data-stu-id="0ed81-120">Left hand</span></span> </th><th> <span data-ttu-id="0ed81-121">A destra</span><span class="sxs-lookup"><span data-stu-id="0ed81-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0ed81-122">Selezionare il trigger premuto</span><span class="sxs-lookup"><span data-stu-id="0ed81-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="0ed81-123">Asse 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="0ed81-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="0ed81-124">Asse 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="0ed81-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="0ed81-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="0ed81-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-126">Valore analogico selezionare il trigger</span><span class="sxs-lookup"><span data-stu-id="0ed81-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="0ed81-127">Asse 9</span><span class="sxs-lookup"><span data-stu-id="0ed81-127">Axis 9</span></span> </td><td> <span data-ttu-id="0ed81-128">Asse 10</span><span class="sxs-lookup"><span data-stu-id="0ed81-128">Axis 10</span></span> </td><td> <span data-ttu-id="0ed81-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="0ed81-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-130">Selezionare il trigger parzialmente premuto</span><span class="sxs-lookup"><span data-stu-id="0ed81-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="0ed81-131">Pulsante 14 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0ed81-132">Pulsante 15 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0ed81-133">selectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="0ed81-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-134">Pulsante di menu selezionato</span><span class="sxs-lookup"><span data-stu-id="0ed81-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="0ed81-135">Pulsante 6 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-135">Button 6\*</span></span> </td><td> <span data-ttu-id="0ed81-136">Pulsante 7 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-136">Button 7\*</span></span> </td><td> <span data-ttu-id="0ed81-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="0ed81-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-138">Pressione del pulsante triangolo di ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="0ed81-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="0ed81-139">Asse 11 = 1.0 (nessun valore analogico)</span><span class="sxs-lookup"><span data-stu-id="0ed81-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="0ed81-140">Pulsante 4 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0ed81-141">Asse 12 = 1.0 (nessun valore analogico)</span><span class="sxs-lookup"><span data-stu-id="0ed81-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="0ed81-142">Pulsante 5 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0ed81-143">compreso</span><span class="sxs-lookup"><span data-stu-id="0ed81-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-144">X Thumbstick <i>(a sinistra: -1,0, a destra: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="0ed81-145">Asse 1</span><span class="sxs-lookup"><span data-stu-id="0ed81-145">Axis 1</span></span> </td><td> <span data-ttu-id="0ed81-146">Asse 4</span><span class="sxs-lookup"><span data-stu-id="0ed81-146">Axis 4</span></span> </td><td> <span data-ttu-id="0ed81-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="0ed81-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-148">Y Thumbstick <i>(top: -1,0, nella parte inferiore: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="0ed81-149">Asse 2</span><span class="sxs-lookup"><span data-stu-id="0ed81-149">Axis 2</span></span> </td><td> <span data-ttu-id="0ed81-150">Asse 5</span><span class="sxs-lookup"><span data-stu-id="0ed81-150">Axis 5</span></span> </td><td> <span data-ttu-id="0ed81-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="0ed81-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-152">Thumbstick premuto</span><span class="sxs-lookup"><span data-stu-id="0ed81-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="0ed81-153">Pulsante 8</span><span class="sxs-lookup"><span data-stu-id="0ed81-153">Button 8</span></span> </td><td> <span data-ttu-id="0ed81-154">Pulsante 9</span><span class="sxs-lookup"><span data-stu-id="0ed81-154">Button 9</span></span> </td><td> <span data-ttu-id="0ed81-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="0ed81-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-156">X touchpad <i>(a sinistra: -1,0, a destra: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="0ed81-157">Asse 17 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="0ed81-158">Asse 19 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="0ed81-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="0ed81-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-160">Y touchpad <i>(top: -1,0, nella parte inferiore: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="0ed81-161">Asse 18 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="0ed81-162">Asse 20 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="0ed81-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="0ed81-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-164">Touchpad interessate</span><span class="sxs-lookup"><span data-stu-id="0ed81-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="0ed81-165">Pulsante 18 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-165">Button 18\*</span></span> </td><td> <span data-ttu-id="0ed81-166">Pulsante 19 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-166">Button 19\*</span></span> </td><td> <span data-ttu-id="0ed81-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="0ed81-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-168">Touchpad premuto</span><span class="sxs-lookup"><span data-stu-id="0ed81-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="0ed81-169">Pulsante 16 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-169">Button 16\*</span></span> </td><td> <span data-ttu-id="0ed81-170">Pulsante 17 \*</span><span class="sxs-lookup"><span data-stu-id="0ed81-170">Button 17\*</span></span> </td><td> <span data-ttu-id="0ed81-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="0ed81-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-172">6DoF triangolo posa o posa puntatore</span><span class="sxs-lookup"><span data-stu-id="0ed81-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="0ed81-173"><i>Triangolo di ridimensionamento</i> rappresentare solo: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="0ed81-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="0ed81-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="0ed81-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="0ed81-175">Passare <i>triangolo</i> oppure <i>puntatore</i> come argomento: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="0ed81-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="0ed81-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="0ed81-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-177">Tenere traccia dello stato</span><span class="sxs-lookup"><span data-stu-id="0ed81-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="0ed81-178"><i>Posizione accuratezza origine perdita dei rischi e disponibili solo tramite l'API di MR specifici</i> </span><span class="sxs-lookup"><span data-stu-id="0ed81-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="0ed81-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="0ed81-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="0ed81-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="0ed81-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="0ed81-181">Questi ID pulsante/asse sono diversi dagli ID che usa Unity per OpenVR a causa di collisioni nelle associazioni utilizzate dal gamepad, Oculus tocco e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="0ed81-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="0ed81-182">Triangolo di ridimensionamento posa confronto posa puntamento</span><span class="sxs-lookup"><span data-stu-id="0ed81-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="0ed81-183">Realtà mista di Windows supporta controller di movimento in un'ampia gamma di fattori di forma, con la progettazione del ogni controller che differiscono per la relazione tra la posizione dell'utente mano e naturale "inoltro" direzione tale app deve usare per fare riferimento durante il rendering di controller.</span><span class="sxs-lookup"><span data-stu-id="0ed81-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="0ed81-184">Per rappresentare meglio questi controller, esistono due tipi di può causare per ogni origine di interazione, è possibile esaminare i **posa triangolo** e il **posa puntatore**.</span><span class="sxs-lookup"><span data-stu-id="0ed81-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="0ed81-185">Sia il triangolo di ridimensionamento posa e puntatore posa le coordinate sono espresse da tutte le API di Unity in coordinate complessive di Unity globale.</span><span class="sxs-lookup"><span data-stu-id="0ed81-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="0ed81-186">Triangolo di ridimensionamento posa</span><span class="sxs-lookup"><span data-stu-id="0ed81-186">Grip pose</span></span>

<span data-ttu-id="0ed81-187">Il **triangolo posa** rappresenta la posizione di palmo di una mano rilevata da un HoloLens o palmo che contiene un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="0ed81-188">In coinvolgenti auricolari, posa il triangolo di ridimensionamento è particolarmente utile per eseguire il rendering **manuale dell'utente** oppure **mantenuto un oggetto a disposizione dell'utente**, ad esempio un doppio taglio o gun.</span><span class="sxs-lookup"><span data-stu-id="0ed81-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="0ed81-189">Posa il triangolo di ridimensionamento viene usata anche quando la visualizzazione di un controller di movimento, come le **renderizzabili modello** fornite da Windows per un movimento controller utilizza posa il triangolo di ridimensionamento come origine e il centro di rotazione.</span><span class="sxs-lookup"><span data-stu-id="0ed81-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="0ed81-190">Posa il triangolo di ridimensionamento è definita in modo specifico come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="0ed81-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="0ed81-191">Il **afferrare posizione**: Il centroide palm quando tenendo naturalmente, il controller è regolato sinistro o destro da allineare al centro la posizione all'interno del triangolo di ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="0ed81-192">Nel controller di movimento di realtà mista di Windows, questa posizione viene allineato a livello generale con il pulsante. é quindi.</span><span class="sxs-lookup"><span data-stu-id="0ed81-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="0ed81-193">Il **afferrare asse a destra dell'orientamento**: Quando si apre completamente la mano per formare una posa flat con un dito di 5, il raggio è normale che palm (in avanti dal palmo a sinistra, con le versioni precedenti dal palmo a destra)</span><span class="sxs-lookup"><span data-stu-id="0ed81-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="0ed81-194">Il **afferrare asse diretta dell'orientamento**: Quando si chiude la mano parzialmente (come se che contiene il controller), il raggio che punta "forward" tramite il tubo costituita dalle dita non thumb.</span><span class="sxs-lookup"><span data-stu-id="0ed81-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="0ed81-195">Il **afferrare orientamento di asse**: L'asse verticale in cui è inclusa per le definizioni di destra e l'inoltro.</span><span class="sxs-lookup"><span data-stu-id="0ed81-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="0ed81-196">È possibile accedere posa il triangolo di ridimensionamento tramite l'API di input tra fornitori entrambi di Unity (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o tramite l'API Windows MR specifiche (*sourceState.sourcePose.TryGetPosition/Rotation*, che richiede di rappresentare i dati per il **triangolo** nodo).</span><span class="sxs-lookup"><span data-stu-id="0ed81-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="0ed81-197">Puntatore posa</span><span class="sxs-lookup"><span data-stu-id="0ed81-197">Pointer pose</span></span>

<span data-ttu-id="0ed81-198">Il **posa puntatore** rappresenta la punta del controller in avanti che punta.</span><span class="sxs-lookup"><span data-stu-id="0ed81-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="0ed81-199">Il puntatore fornito dal sistema posa è particolarmente utile per raycast quando sei **il modello controller stesso per il rendering**.</span><span class="sxs-lookup"><span data-stu-id="0ed81-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="0ed81-200">Se si esegue il rendering di un altro oggetto virtuale al posto di controller, ad esempio un gun virtuale, è necessario puntare con un raggio che risulta più naturale per l'oggetto virtuale, ad esempio un raggio che percorre cilindro del modello gun definito dall'app.</span><span class="sxs-lookup"><span data-stu-id="0ed81-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="0ed81-201">Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, che punta all'oggetto virtuale sarà probabilmente più naturale per chi usa l'app.</span><span class="sxs-lookup"><span data-stu-id="0ed81-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="0ed81-202">È attualmente disponibile in Unity solo tramite l'API Windows MR specifici, posa il puntatore *sourceState.sourcePose.TryGetPosition/Rotation*passando *InteractionSourceNode.Pointer* come il discussione.</span><span class="sxs-lookup"><span data-stu-id="0ed81-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="0ed81-203">Stato di rilevamento del controller</span><span class="sxs-lookup"><span data-stu-id="0ed81-203">Controller tracking state</span></span>

<span data-ttu-id="0ed81-204">Ad esempio le cuffie, il controller di movimento di realtà mista di Windows non richiede alcuna configurazione dei sensori esterna tracciamento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="0ed81-205">Al contrario, i controller vengono rilevati da sensori in auricolare stesso.</span><span class="sxs-lookup"><span data-stu-id="0ed81-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="0ed81-206">Se l'utente sposta il controller all'esterno il della cuffia campo visivo, nella maggior parte dei casi Windows continuerà a dedurre le posizioni di controller e fornire all'app.</span><span class="sxs-lookup"><span data-stu-id="0ed81-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="0ed81-207">Quando il controller ha perso visual rilevamento per tempo sufficiente, eliminerà le posizioni del controller nelle posizioni di accuratezza approssimativo.</span><span class="sxs-lookup"><span data-stu-id="0ed81-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="0ed81-208">A questo punto, il sistema eseguirà il corpo del blocco il controller per l'utente e la posizione dell'utente di rilevamento durante lo spostamento, quando si espongono ancora orientamento true del controller tramite sensori relativo orientamento interno.</span><span class="sxs-lookup"><span data-stu-id="0ed81-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="0ed81-209">Molte App che usano i controller per puntare alla e attivare gli elementi dell'interfaccia utente può funzionare normalmente anche se in accuratezza approssimativo senza che l'utente vengano rilevate.</span><span class="sxs-lookup"><span data-stu-id="0ed81-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="0ed81-210">Il modo migliore per farsi un'idea di ciò è prova in prima persona.</span><span class="sxs-lookup"><span data-stu-id="0ed81-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="0ed81-211">Guarda questo video con esempi di contenuti coinvolgenti che funziona con i controller di movimento in vari stati di rilevamento:</span><span class="sxs-lookup"><span data-stu-id="0ed81-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="0ed81-212">Ha a che fare in modo esplicito lo stato di rilevamento</span><span class="sxs-lookup"><span data-stu-id="0ed81-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="0ed81-213">Le app che si desiderano considerare le posizioni diverso a seconda dello stato di rilevamento possono andare oltre e controllare le proprietà sullo stato del controller, ad esempio *SourceLossRisk* e *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="0ed81-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="0ed81-214">Tenere traccia dello stato</span><span class="sxs-lookup"><span data-stu-id="0ed81-214">Tracking state</span></span> </th><th> <span data-ttu-id="0ed81-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="0ed81-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="0ed81-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="0ed81-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="0ed81-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="0ed81-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0ed81-218"><b>Accuratezza elevata</b> </span><span class="sxs-lookup"><span data-stu-id="0ed81-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="0ed81-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="0ed81-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0ed81-220">Alto</span><span class="sxs-lookup"><span data-stu-id="0ed81-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0ed81-221">true</span><span class="sxs-lookup"><span data-stu-id="0ed81-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-222"><b>Elevata precisione per (a rischio di perdita)</b> </span><span class="sxs-lookup"><span data-stu-id="0ed81-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0ed81-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="0ed81-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0ed81-224">Alto</span><span class="sxs-lookup"><span data-stu-id="0ed81-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0ed81-225">true</span><span class="sxs-lookup"><span data-stu-id="0ed81-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-226"><b>Accuratezza approssimativo</b> </span><span class="sxs-lookup"><span data-stu-id="0ed81-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0ed81-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="0ed81-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0ed81-228">Approximate</span><span class="sxs-lookup"><span data-stu-id="0ed81-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0ed81-229">true</span><span class="sxs-lookup"><span data-stu-id="0ed81-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0ed81-230"><b>Nessuna posizione</b> </span><span class="sxs-lookup"><span data-stu-id="0ed81-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0ed81-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="0ed81-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0ed81-232">Approximate</span><span class="sxs-lookup"><span data-stu-id="0ed81-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0ed81-233">false</span><span class="sxs-lookup"><span data-stu-id="0ed81-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="0ed81-234">Questi stati di rilevamento movimento controller sono definiti come segue:</span><span class="sxs-lookup"><span data-stu-id="0ed81-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="0ed81-235">**Alta precisione:** Anche se il controller di movimento è all'interno il della cuffia campo visivo, in genere fornirà le posizioni di elevata precisione, basate sul rilevamento visual.</span><span class="sxs-lookup"><span data-stu-id="0ed81-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="0ed81-236">Si noti che un controller di spostamento che momentaneamente lascia il campo visivo o momentaneamente è nascosto dai sensori visore VR (ad esempio, da altra parte dell'utente) continuerà a restituire pose elevata precisione per un breve periodo di tempo, basato sul rilevamento movimento inerziale del controller di sé stesso.</span><span class="sxs-lookup"><span data-stu-id="0ed81-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="0ed81-237">**Elevata precisione (a rischio di perdita):** Quando l'utente sposta il controller di movimento oltre il bordo del campo visivo della cuffia, le cuffie saranno presto possibile tenere traccia visivamente della posizione del controller.</span><span class="sxs-lookup"><span data-stu-id="0ed81-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="0ed81-238">L'app conosce quando il controller ha raggiunto il limite del campo di visualizzazione, vedere l'articolo di **SourceLossRisk** raggiungere 1.0.</span><span class="sxs-lookup"><span data-stu-id="0ed81-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="0ed81-239">A questo punto, l'app può scegliere di sospendere i movimenti di controller che richiedono un flusso costante di altissima qualità creeranno.</span><span class="sxs-lookup"><span data-stu-id="0ed81-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="0ed81-240">**Accuratezza approssimativo:** Quando il controller ha perso visual rilevamento per tempo sufficiente, eliminerà le posizioni del controller nelle posizioni di accuratezza approssimativo.</span><span class="sxs-lookup"><span data-stu-id="0ed81-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="0ed81-241">A questo punto, il sistema eseguirà il corpo del blocco il controller per l'utente e la posizione dell'utente di rilevamento durante lo spostamento, quando si espongono ancora orientamento true del controller tramite sensori relativo orientamento interno.</span><span class="sxs-lookup"><span data-stu-id="0ed81-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="0ed81-242">Molte App che usano i controller per puntare alla e attivare gli elementi dell'interfaccia utente possono operare come normale periodo di tempo accuratezza approssimativo senza che l'utente vengano rilevate.</span><span class="sxs-lookup"><span data-stu-id="0ed81-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="0ed81-243">Le app con più intensi i requisiti di input possono scegliere di questo elenco da rilevare **elevata** approssimazione pari a **approssimato** accuratezza controllando il **PositionAccuracy** proprietà, per esempio per consentire all'utente un hitbox maggiori nelle destinazioni fuori dello schermo durante questo periodo.</span><span class="sxs-lookup"><span data-stu-id="0ed81-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="0ed81-244">**Nessuna posizione:** Mentre il controller può operare accuratezza approssimativo per molto tempo, in alcuni casi il sistema sa che anche una posizione bloccata corpo non è significativa al momento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="0ed81-245">Ad esempio, un controller che è stato appena abilitato non può sono mai stato osservato visivamente o un utente può inserire verso il basso un controller che viene quindi prelevato da un altro utente.</span><span class="sxs-lookup"><span data-stu-id="0ed81-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="0ed81-246">In tali casi, il sistema non fornirà a qualsiasi posizione all'app, e *TryGetPosition* restituirà false.</span><span class="sxs-lookup"><span data-stu-id="0ed81-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="0ed81-247">API di Unity comuni (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="0ed81-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="0ed81-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="0ed81-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="0ed81-249">**Tipi**: *Input*, *XR.InputTracking*</span><span class="sxs-lookup"><span data-stu-id="0ed81-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="0ed81-250">Unity Usa attualmente il general *Input.GetButton/Input.GetAxis* API per esporre l'input per [SDK Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [SDK OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html) e realtà mista di Windows, tra cui le mani e controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="0ed81-251">Se l'app Usa queste API per l'input, può supportare facilmente i controller di transito tra più XR SDK, tra cui la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="0ed81-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="0ed81-252">Recupero dello stato di premuto del pulsante logico</span><span class="sxs-lookup"><span data-stu-id="0ed81-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="0ed81-253">Per usare l'API di input di Unity generale, verranno in genere iniziare associando i pulsanti e assi per i nomi logici nel [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), associazione a ogni nome di un pulsante o un ID dell'asse.</span><span class="sxs-lookup"><span data-stu-id="0ed81-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="0ed81-254">È quindi possibile scrivere codice che fa riferimento a tale nome logico pulsante / dell'asse.</span><span class="sxs-lookup"><span data-stu-id="0ed81-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="0ed81-255">Ad esempio, per eseguire il mapping per l'azione di invio grilletto del controller movimento a sinistra, passare a **Modifica > Impostazioni di progetto > Input** in Unity ed espandere le proprietà della sezione invio in assi.</span><span class="sxs-lookup"><span data-stu-id="0ed81-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="0ed81-256">Modifica il **pulsante positivo** oppure **pulsante positivo Alt** proprietà da leggere **pulsante joystick 14**, simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="0ed81-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="0ed81-257">![InputManager di Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="0ed81-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="0ed81-258">*InputManager Unity*</span><span class="sxs-lookup"><span data-stu-id="0ed81-258">*Unity InputManager*</span></span>

<span data-ttu-id="0ed81-259">Quindi è possibile controllare lo script per l'azione di invio utilizzando *Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="0ed81-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="0ed81-260">È possibile aggiungere pulsanti più logici modificando la **dimensioni** proprietà sotto **assi**.</span><span class="sxs-lookup"><span data-stu-id="0ed81-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="0ed81-261">Recupero stato premuto di un pulsante fisico direttamente</span><span class="sxs-lookup"><span data-stu-id="0ed81-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="0ed81-262">È anche possibile accedere a manualmente i pulsanti da loro completo nome, utilizzando *Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="0ed81-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="0ed81-263">Recupero di una mano o posa del controller di movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="0ed81-264">È possibile accedere la posizione e la rotazione del controller, usando *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="0ed81-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="0ed81-265">Si noti che questo rappresenti posa triangolo di ridimensionamento del controller (in cui l'utente tiene premuto il controller) che è utile per il rendering di un doppio taglio o gun nel manuale dell'utente o un modello del controller stesso.</span><span class="sxs-lookup"><span data-stu-id="0ed81-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="0ed81-266">Si noti che la relazione tra questo posa triangolo di ridimensionamento e la posa puntatore (in cui il suggerimento del controller di punta) può variare tra i controller.</span><span class="sxs-lookup"><span data-stu-id="0ed81-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="0ed81-267">In questo momento, l'accesso a posa puntatore del controller è possibile solo tramite l'input di MR specifiche API, descritti nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="0ed81-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="0ed81-268">API di Windows specifiche (XR. WSA. Input)</span><span class="sxs-lookup"><span data-stu-id="0ed81-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="0ed81-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="0ed81-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="0ed81-270">**Tipi**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="0ed81-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="0ed81-271">Per ottenere informazioni più dettagliate sugli input manuale di realtà mista di Windows (per HoloLens) e i controller di movimento, è possibile scegliere di usare le API di input spaziali specifiche di Windows con il *UnityEngine.XR.WSA.Input* dello spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="0ed81-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="0ed81-272">Ciò consente di accedere a informazioni aggiuntive, ad esempio accuratezza posizione o il tipo di origine, consentendo di indicare le mani e controller distanti.</span><span class="sxs-lookup"><span data-stu-id="0ed81-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="0ed81-273">Esecuzione del polling dello stato della mani e controller di movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="0ed81-274">È possibile eseguire il polling per questo stato per ogni origine (manualmente o movimento controller) l'interazione con il *GetCurrentReading* (metodo).</span><span class="sxs-lookup"><span data-stu-id="0ed81-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="0ed81-275">Ciascuna *InteractionSourceState* otterrai back rappresenta un'origine l'interazione nel momento attuale nel tempo.</span><span class="sxs-lookup"><span data-stu-id="0ed81-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="0ed81-276">Il *InteractionSourceState* espone informazioni quali:</span><span class="sxs-lookup"><span data-stu-id="0ed81-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="0ed81-277">Quale [tipi di pressioni](motion-controllers.md) si verificano (selezione/Menu /. é quindi/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="0ed81-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="0ed81-278">Altri dati specifici di movimento controller, tali il touchpad e/o del thumbstick coordinate XY e lo stato aggiornato</span><span class="sxs-lookup"><span data-stu-id="0ed81-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="0ed81-279">InteractionSourceKind sapere se l'origine è una mano o un controller di movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="0ed81-280">Esecuzione del polling può causare forward-stimato per il rendering</span><span class="sxs-lookup"><span data-stu-id="0ed81-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="0ed81-281">Per il polling dei dati di origine l'interazione da mani e controller, le pose che otterrai sono pose forward-stimato per il momento nel tempo quando fotoni questo frame raggiungeranno gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="0ed81-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="0ed81-282">Tali può causare stimato forward risultano particolarmente adatte per **rendering** il controller o un mantenuto ogni fotogramma dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="0ed81-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="0ed81-283">Se si ha come destinazione la pressione di un determinato o di rilascio con il controller, che sarà più accurato se si usa l'evento cronologico le API descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="0ed81-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="0ed81-284">È anche possibile ottenere la posa head stimato forward per il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="0ed81-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="0ed81-285">Come con la posa di origine, ciò è utile per **rendering** un cursore, anche se destinate a una determinata premere o una versione sarà più accurato se si usa l'evento cronologico le API descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="0ed81-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="0ed81-286">Gestione degli eventi di origine di interazione</span><span class="sxs-lookup"><span data-stu-id="0ed81-286">Handling interaction source events</span></span>

<span data-ttu-id="0ed81-287">Per gestire gli eventi di input in tempo reale con i propri dati accurati posa cronologici, è possibile gestire l'interazione dell'origine eventi invece di polling.</span><span class="sxs-lookup"><span data-stu-id="0ed81-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="0ed81-288">Per gestire l'interazione dell'origine eventi:</span><span class="sxs-lookup"><span data-stu-id="0ed81-288">To handle interaction source events:</span></span>
* <span data-ttu-id="0ed81-289">Iscriviti a una *InteractionManager* evento di input.</span><span class="sxs-lookup"><span data-stu-id="0ed81-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="0ed81-290">Per ogni tipo di evento di interazione che si è interessati, è necessario eseguire la sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="0ed81-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="0ed81-291">Gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-291">Handle the event.</span></span> <span data-ttu-id="0ed81-292">Dopo che è necessario sottoscrivere un evento di interazione, si otterrà il callback quando appropriato.</span><span class="sxs-lookup"><span data-stu-id="0ed81-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="0ed81-293">Nel *SourcePressed* esempio, si tratterà dopo che è stata rilevata l'origine e prima che venga rilasciato o persi.</span><span class="sxs-lookup"><span data-stu-id="0ed81-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="0ed81-294">Come interrompere la gestione di un evento</span><span class="sxs-lookup"><span data-stu-id="0ed81-294">How to stop handling an event</span></span>

<span data-ttu-id="0ed81-295">È necessario interrompere la gestione di un evento quando sono più interessati nell'evento o si è l'eliminazione dell'oggetto che ha sottoscritto l'evento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="0ed81-296">Per interrompere la gestione dell'evento, annullare la sottoscrizione dall'evento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="0ed81-297">Elenco di eventi di origine di interazione</span><span class="sxs-lookup"><span data-stu-id="0ed81-297">List of interaction source events</span></span>

<span data-ttu-id="0ed81-298">Gli eventi di origine interazione disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="0ed81-298">The available interaction source events are:</span></span>
* <span data-ttu-id="0ed81-299">*InteractionSourceDetected* (origine diventa attiva)</span><span class="sxs-lookup"><span data-stu-id="0ed81-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="0ed81-300">*InteractionSourceLost* (diventa inattivo)</span><span class="sxs-lookup"><span data-stu-id="0ed81-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="0ed81-301">*InteractionSourcePressed* (tap, fare clic sul pulsante o pronunciato "selezionare")</span><span class="sxs-lookup"><span data-stu-id="0ed81-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="0ed81-302">*InteractionSourceReleased* (fine di un tocco, il rilascio del pulsante o alla fine di "Select" pronunciato)</span><span class="sxs-lookup"><span data-stu-id="0ed81-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="0ed81-303">*InteractionSourceUpdated* (sposta o in caso contrario, viene modificato uno stato)</span><span class="sxs-lookup"><span data-stu-id="0ed81-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="0ed81-304">Eventi per cronologici pose destinazione che corrispondono in modo più accurato una pressione o una versione</span><span class="sxs-lookup"><span data-stu-id="0ed81-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="0ed81-305">Le API di polling descritte in precedenza assegnare all'app pose stimato in avanti.</span><span class="sxs-lookup"><span data-stu-id="0ed81-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="0ed81-306">Durante le pose stimati sono ottimali per il rendering del controller o un oggetto virtuale palmare, può causare future non sono ottimali per lo sviluppo, per due motivi principali per:</span><span class="sxs-lookup"><span data-stu-id="0ed81-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="0ed81-307">Quando l'utente preme un pulsante in un controller, può essere presente circa 20 ms di latenza wireless tramite Bluetooth prima che il sistema riceve la stampa.</span><span class="sxs-lookup"><span data-stu-id="0ed81-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="0ed81-308">Quindi, se si usa una posa stimato forward, vi viene applicato per il tempo fotoni del frame corrente verranno raggiungere gli occhi dell'utente di destinazione un altro 10 a 20 ms della stima in avanti.</span><span class="sxs-lookup"><span data-stu-id="0ed81-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="0ed81-309">Ciò significa che il polling ti offre una posa origine o head costituire vale a dire 30-40 MS forward da dove head e le mani dell'utente in realtà sono state nuovamente quando la pressione o la versione si è verificato.</span><span class="sxs-lookup"><span data-stu-id="0ed81-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="0ed81-310">Per l'input manuale HoloLens, anche se non si verifichino ritardi nella trasmissione wireless, si verifica un ritardo di elaborazione simili per rilevare la stampa.</span><span class="sxs-lookup"><span data-stu-id="0ed81-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="0ed81-311">Di destinazione in modo accurato in base l'intenzione dell'utente originale per la pressione di un controller o manualmente, è consigliabile utilizzare l'origine cronologici posa o head posa da quella *InteractionSourcePressed* o *InteractionSourceReleased* evento di input.</span><span class="sxs-lookup"><span data-stu-id="0ed81-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="0ed81-312">È possibile una pressione di destinazione o di rilascio con i dati cronologici posa head dell'utente o il controller:</span><span class="sxs-lookup"><span data-stu-id="0ed81-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="0ed81-313">Si è verificato il posa head al momento nel tempo quando preme un movimento o un controller, che può essere usato per **targeting** per determinare l'utente era [gazing](gaze.md) in:</span><span class="sxs-lookup"><span data-stu-id="0ed81-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="0ed81-314">Si è verificato il posa di origine al momento nel tempo quando preme un controller di movimento, che può essere usato per **targeting** per determinare ciò che l'utente stava puntando il controller.</span><span class="sxs-lookup"><span data-stu-id="0ed81-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="0ed81-315">Questo sarà lo stato del controller che ha riscontrato la stampa.</span><span class="sxs-lookup"><span data-stu-id="0ed81-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="0ed81-316">Se si esegue il rendering il controller stesso, è possibile richiedere la posa puntatore anziché posa il triangolo di ridimensionamento, per riprendere il raggio da ciò che l'utente prenderà in considerazione i suggerimenti naturali che viene eseguito il rendering di controller di destinazione:</span><span class="sxs-lookup"><span data-stu-id="0ed81-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="0ed81-317">Esempio di gestori di eventi</span><span class="sxs-lookup"><span data-stu-id="0ed81-317">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="0ed81-318">Movimento composito ad alto livello API (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="0ed81-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="0ed81-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="0ed81-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="0ed81-320">**Tipi**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="0ed81-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="0ed81-321">L'app anche è in grado di riconoscere i movimenti compositi livello superiore per i movimenti tenere premuto, manipolazione e l'esplorazione spaziale origini di input, Tap.</span><span class="sxs-lookup"><span data-stu-id="0ed81-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="0ed81-322">È in grado di riconoscere i movimenti compositi in entrambi [mani](gestures.md) e [movimento controller](motion-controllers.md) usando il GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="0ed81-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="0ed81-323">Ogni evento di movimento nel GestureRecognizer fornisce il SourceKind per l'input, nonché il raggio head destinazione al momento dell'evento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="0ed81-324">Alcuni eventi forniscono informazioni specifiche di contesto aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="0ed81-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="0ed81-325">Sono disponibili solo pochi passaggi necessari per acquisire i movimenti usando un riconoscitore di movimento:</span><span class="sxs-lookup"><span data-stu-id="0ed81-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="0ed81-326">Creare un nuovo riconoscitore di movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="0ed81-327">Specificare quali i movimenti per il controllo</span><span class="sxs-lookup"><span data-stu-id="0ed81-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="0ed81-328">Sottoscrivere eventi per questi gesti</span><span class="sxs-lookup"><span data-stu-id="0ed81-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="0ed81-329">Avvio dell'acquisizione movimenti</span><span class="sxs-lookup"><span data-stu-id="0ed81-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="0ed81-330">Creare un nuovo riconoscitore di movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="0ed81-331">Usare la *GestureRecognizer*, è necessario avere creato una *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="0ed81-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="0ed81-332">Specificare quali i movimenti per il controllo</span><span class="sxs-lookup"><span data-stu-id="0ed81-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="0ed81-333">Specificare i movimenti di cui si è interessati tramite *SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="0ed81-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="0ed81-334">Sottoscrivere eventi per questi gesti</span><span class="sxs-lookup"><span data-stu-id="0ed81-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="0ed81-335">Sottoscrivere eventi per i movimenti che si è interessati.</span><span class="sxs-lookup"><span data-stu-id="0ed81-335">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="0ed81-336">Navigazione e modifica i movimenti si escludono a vicenda in un'istanza di un *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="0ed81-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="0ed81-337">Avvio dell'acquisizione movimenti</span><span class="sxs-lookup"><span data-stu-id="0ed81-337">Start capturing gestures</span></span>

<span data-ttu-id="0ed81-338">Per impostazione predefinita, un *GestureRecognizer* non esegue il monitoraggio input finché *StartCapturingGestures()* viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="0ed81-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="0ed81-339">È possibile che un evento di movimento può essere generato dopo *StopCapturingGestures()* viene chiamato se l'input è stato eseguito prima il frame in cui *StopCapturingGestures()* è stata elaborata.</span><span class="sxs-lookup"><span data-stu-id="0ed81-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="0ed81-340">Il *GestureRecognizer* memorizzerà se era attiva o disattiva durante il frame previou in cui il movimento è stata effettivamente eseguita, pertanto è affidabile per avviare e movimento di arresto monitoraggio basato su sguardo di questo frame destinazione.</span><span class="sxs-lookup"><span data-stu-id="0ed81-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="0ed81-341">Arrestare l'acquisizione di movimenti</span><span class="sxs-lookup"><span data-stu-id="0ed81-341">Stop capturing gestures</span></span>

<span data-ttu-id="0ed81-342">Per arrestare il riconoscimento di movimento:</span><span class="sxs-lookup"><span data-stu-id="0ed81-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="0ed81-343">Rimozione di un sistema di riconoscimento di movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="0ed81-344">Ricordarsi di annullare la sottoscrizione agli eventi sottoscritti prima dell'eliminazione di un *GestureRecognizer* oggetto.</span><span class="sxs-lookup"><span data-stu-id="0ed81-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="0ed81-345">Il modello di controller di movimento in Unity per il rendering</span><span class="sxs-lookup"><span data-stu-id="0ed81-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="0ed81-346">![Teletrasporto e modello di Controller di movimento](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="0ed81-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="0ed81-347">*Teletrasporto e modello di controller di movimento*</span><span class="sxs-lookup"><span data-stu-id="0ed81-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="0ed81-348">Per eseguire il rendering controller movimento nell'app che soddisfano i controller fisici utenti mantengono attivi e illustrare come vari pulsanti vengono premuti, è possibile usare la **MotionController prefab** nel [Toolkit di realtà mista ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="0ed81-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="0ed81-349">Il prefab carica in modo dinamico il modello glTF corretto in fase di esecuzione dal driver del controller installato movimento del sistema.</span><span class="sxs-lookup"><span data-stu-id="0ed81-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="0ed81-350">È importante caricare dinamicamente questi modelli piuttosto che importarli manualmente nell'editor, in modo che l'app Visualizza modelli 3D fisicamente accurati per tutti i controller attuali e futuri utenti può avere.</span><span class="sxs-lookup"><span data-stu-id="0ed81-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="0ed81-351">Seguire le [introduttiva](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) istruzioni per scaricare il Toolkit di realtà mista e aggiungerlo al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="0ed81-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="0ed81-352">Se è stato sostituito con il *MixedRealityCameraParent* prefab come parte dei passaggi di Guida introduttiva, ora possibile iniziare.</span><span class="sxs-lookup"><span data-stu-id="0ed81-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="0ed81-353">Il prefab include per il rendering di movimento controller.</span><span class="sxs-lookup"><span data-stu-id="0ed81-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="0ed81-354">In caso contrario, aggiungere *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* in scena dal riquadro del progetto.</span><span class="sxs-lookup"><span data-stu-id="0ed81-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="0ed81-355">È opportuno aggiungere prefab come figlio di qualsiasi oggetto padre utilizzato per spostare la camera intorno a quando l'utente teleports all'interno della scena, in modo che i controller di lavoro con l'utente.</span><span class="sxs-lookup"><span data-stu-id="0ed81-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="0ed81-356">Se l'app non comporta la teleporting, è sufficiente aggiungere il prefab alla radice della scena.</span><span class="sxs-lookup"><span data-stu-id="0ed81-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="0ed81-357">Generazione di oggetti</span><span class="sxs-lookup"><span data-stu-id="0ed81-357">Throwing objects</span></span>

<span data-ttu-id="0ed81-358">La generazione di oggetti in realtà virtuale è un problema più difficile e può inizialmente sembrare.</span><span class="sxs-lookup"><span data-stu-id="0ed81-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="0ed81-359">Come con più fisicamente in base interazioni, quando si genera in gioco si comporta in modo imprevisto, è immediatamente evidente e interruzioni di full immersion.</span><span class="sxs-lookup"><span data-stu-id="0ed81-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="0ed81-360">Abbiamo investito alcuni tempo a pensare in profondità come rappresentare un comportamento generando un'eccezione fisicamente corretto e hanno ideare alcune linee guida, abilitate tramite gli aggiornamenti alla piattaforma, che si vuole condividere con l'utente.</span><span class="sxs-lookup"><span data-stu-id="0ed81-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="0ed81-361">È possibile trovare un esempio del modo in cui è consigliabile implementare generando un'eccezione [qui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="0ed81-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="0ed81-362">In questo esempio segue queste linee quattro Guida:</span><span class="sxs-lookup"><span data-stu-id="0ed81-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="0ed81-363">**Utilizzare il controller *velocità* invece di posizione**.</span><span class="sxs-lookup"><span data-stu-id="0ed81-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="0ed81-364">Nell'aggiornamento di novembre di Windows, è stata introdotta una modifica nel comportamento quando nel [' approssimare ' stato di rilevamento posizionali](motion-controllers.md#controller-tracking-state).</span><span class="sxs-lookup"><span data-stu-id="0ed81-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="0ed81-365">In questo stato, informazioni velocità sul controller continueranno a essere segnalati per, purché si ritiene che sia elevata accuratezza, che spesso è più lungo posizione rimane elevata precisione.</span><span class="sxs-lookup"><span data-stu-id="0ed81-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="0ed81-366">**Incorporare il *velocità angolare* del controller**.</span><span class="sxs-lookup"><span data-stu-id="0ed81-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="0ed81-367">Questa logica è contenuta nel `throwing.cs` del file nei `GetThrownObjectVelAngVel` metodo statico, all'interno del pacchetto con collegato riportato sopra:</span><span class="sxs-lookup"><span data-stu-id="0ed81-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="0ed81-368">Come è consente di risparmiare velocità angolare, l'oggetto viene generata deve mantenere la stessa velocità angolare con cui erano al momento del lancio: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="0ed81-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="0ed81-369">Come il centro della massa dell'oggetto generata è probabile che non in corrispondenza dell'origine di posa il triangolo di ridimensionamento, probabilmente ha una velocità diverse e il controller di nel frame di riferimento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="0ed81-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="0ed81-370">La parte della velocità dell'oggetto fornita in questo modo è la velocità di tangente istantanea del baricentro dell'oggetto intorno all'origine di controller.</span><span class="sxs-lookup"><span data-stu-id="0ed81-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="0ed81-371">Questa velocità tangente è il prodotto incrociato di velocità angolare del controller con il vettore che rappresenta la distanza tra l'origine di controller e al centro della massa dell'oggetto viene generata.</span><span class="sxs-lookup"><span data-stu-id="0ed81-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="0ed81-372">La velocità totale dell'oggetto generata è pertanto la somma della velocità del controller e questa velocità tangente: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="0ed81-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="0ed81-373">**Leggere con attenzione il *tempo* in corrispondenza del quale si applica alla velocità**.</span><span class="sxs-lookup"><span data-stu-id="0ed81-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="0ed81-374">Quando viene premuto un pulsante, può richiedere fino a 20 ms per l'evento di bubbling tramite Bluetooth al sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="0ed81-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="0ed81-375">Ciò significa che se si effettuare il polling di una modifica dello stato di controller da premuto per non premuto o viceversa, le informazioni sul posa controller che ti offriamo, sarà prima di questa modifica nello stato.</span><span class="sxs-lookup"><span data-stu-id="0ed81-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="0ed81-376">Inoltre, posa il controller presentata tramite l'API di polling in avanti stimata in modo da riflettere una probabile posa al momento verrà visualizzato il frame che può essere 20 ms quindi altre in futuro.</span><span class="sxs-lookup"><span data-stu-id="0ed81-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="0ed81-377">Questa opzione è utile per *rendering* archiviati oggetti, ma si sommano il problema in fase di *targeting* l'oggetto come vengono calcolati i traiettoria per il momento in cui l'utente ha rilasciato i throw.</span><span class="sxs-lookup"><span data-stu-id="0ed81-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="0ed81-378">Per fortuna, con l'aggiornamento di novembre, quando si desidera che un evento di Unity *InteractionSourcePressed* oppure *InteractionSourceReleased* viene inviata, lo stato include i dati cronologici posa da eseguire quando il pulsante è stato effettivamente premuto o rilasciato.</span><span class="sxs-lookup"><span data-stu-id="0ed81-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="0ed81-379">Per ottenere il più accurati per il rendering di controller e controller targeting durante genera un'eccezione, è necessario utilizzare correttamente il polling e gestione degli eventi, come appropriato:</span><span class="sxs-lookup"><span data-stu-id="0ed81-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="0ed81-380">Per la **rendering controller** ogni fotogramma, l'app deve prevedere il posizionamento del controller *GameObject* nel controller stimato forward comportare per volta photon del frame corrente.</span><span class="sxs-lookup"><span data-stu-id="0ed81-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="0ed81-381">Ottenere i dati da Unity, ad esempio le API di polling *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oppure  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="0ed81-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="0ed81-382">Per la **destinato a controller** dopo una pressione o una versione, l'app deve raycast e calcolare traiettorie base la posa controller cronologici per l'evento premere o versione.</span><span class="sxs-lookup"><span data-stu-id="0ed81-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="0ed81-383">Ottenere i dati dalla gestione degli eventi Unity API, ad esempio  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="0ed81-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="0ed81-384">**Usare il triangolo di ridimensionamento posa**.</span><span class="sxs-lookup"><span data-stu-id="0ed81-384">**Use the grip pose**.</span></span> <span data-ttu-id="0ed81-385">Velocità e velocità angolare vengono segnalati rispetto al posa triangolo, non posa puntatore.</span><span class="sxs-lookup"><span data-stu-id="0ed81-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="0ed81-386">Generando un'eccezione continuerà a migliorare con i futuri aggiornamenti di Windows e sarà possibile trovare altre informazioni su di esso.</span><span class="sxs-lookup"><span data-stu-id="0ed81-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="0ed81-387">Accelera lo sviluppo con il Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="0ed81-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="0ed81-388">Esistono due scene di esempio su InputManager e MotionController in Unity.</span><span class="sxs-lookup"><span data-stu-id="0ed81-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="0ed81-389">Tramite questi scene, è possibile imparare a utilizzare InputManager del MRTK e accesso dati gestiscono gli eventi dai pulsanti di controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="0ed81-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="0ed81-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="0ed81-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="0ed81-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="0ed81-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="0ed81-392">File Leggimi di dettagli tecnici</span><span class="sxs-lookup"><span data-stu-id="0ed81-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="0ed81-393">![Esempio di input in background nelle MRTK](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="0ed81-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="0ed81-394">*Esempio di input in background nelle MRTK*</span><span class="sxs-lookup"><span data-stu-id="0ed81-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="0ed81-395">Programma di installazione automatica scena</span><span class="sxs-lookup"><span data-stu-id="0ed81-395">Automatic scene setup</span></span>

<span data-ttu-id="0ed81-396">Quando si importano [MRTK rilasciare pacchetti Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonare il progetto dal [repository di GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), si desidera trovare un nuovo menu 'Toolkit realtà mista' in Unity.</span><span class="sxs-lookup"><span data-stu-id="0ed81-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="0ed81-397">Nel menu 'Configura', verrà visualizzato il menu 'Applica misto realtà scena impostazioni'.</span><span class="sxs-lookup"><span data-stu-id="0ed81-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="0ed81-398">Quando si fa clic si, rimuove la fotocamera predefinita e aggiunge i componenti fondamentali - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="0ed81-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="0ed81-399">![Menu MRTK per l'installazione di scena](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="0ed81-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="0ed81-400">*Menu MRTK per l'installazione di scena*</span><span class="sxs-lookup"><span data-stu-id="0ed81-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="0ed81-401">![Programma di installazione automatica di scena in MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="0ed81-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="0ed81-402">*Programma di installazione automatica di scena in MRTK*</span><span class="sxs-lookup"><span data-stu-id="0ed81-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="0ed81-403">MixedRealityCamera prefab</span><span class="sxs-lookup"><span data-stu-id="0ed81-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="0ed81-404">È possibile aggiungere anche manualmente queste informazioni dal Pannello di progetto.</span><span class="sxs-lookup"><span data-stu-id="0ed81-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="0ed81-405">È possibile trovare questi componenti come prefabs.</span><span class="sxs-lookup"><span data-stu-id="0ed81-405">You can find these components as prefabs.</span></span> <span data-ttu-id="0ed81-406">Quando si cercano **MixedRealityCamera**, sarà possibile visualizzare due diversi fotocamera prefabs.</span><span class="sxs-lookup"><span data-stu-id="0ed81-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="0ed81-407">È, la differenza **MixedRealityCamera** è la fotocamera solo prefab mentre **MixedRealityCameraParent** include i componenti aggiuntivi per le cuffie coinvolgente e concreto, ad esempio teletrasporto, movimento Controller e limiti.</span><span class="sxs-lookup"><span data-stu-id="0ed81-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="0ed81-408">![Fotocamera prefab nel MRTK](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="0ed81-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="0ed81-409">*Fotocamera prefab nel MRTK*</span><span class="sxs-lookup"><span data-stu-id="0ed81-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="0ed81-410">**MixedRealtyCamera** supporta visore VR immersivi e HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ed81-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="0ed81-411">Rileva il tipo di dispositivo e consente di ottimizzare le proprietà, ad esempio cancella i flag e Skybox.</span><span class="sxs-lookup"><span data-stu-id="0ed81-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="0ed81-412">Di seguito è possibile trovare alcune delle proprietà più utili è possibile personalizzare, ad esempio un cursore personalizzato, i modelli di Controller di movimento e Floor.</span><span class="sxs-lookup"><span data-stu-id="0ed81-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="0ed81-413">![Proprietà per il controller di movimento, cursore e Floor](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="0ed81-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="0ed81-414">*Proprietà per il controller di movimento, cursore e Floor*</span><span class="sxs-lookup"><span data-stu-id="0ed81-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="0ed81-415">Segui le esercitazioni</span><span class="sxs-lookup"><span data-stu-id="0ed81-415">Follow along with tutorials</span></span>

<span data-ttu-id="0ed81-416">Esercitazioni dettagliate, con esempi di personalizzazione più dettagliati, sono disponibili in Academy la realtà mista:</span><span class="sxs-lookup"><span data-stu-id="0ed81-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="0ed81-417">Input di MR 211: Movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="0ed81-418">Input di MR 213: Controller di movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="0ed81-419">[![Input di MR 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="0ed81-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="0ed81-420">*Input di MR 213 - Motion controller*</span><span class="sxs-lookup"><span data-stu-id="0ed81-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="0ed81-421">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0ed81-421">See also</span></span>

* [<span data-ttu-id="0ed81-422">Movimenti</span><span class="sxs-lookup"><span data-stu-id="0ed81-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="0ed81-423">Controller di movimento</span><span class="sxs-lookup"><span data-stu-id="0ed81-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="0ed81-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="0ed81-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="0ed81-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="0ed81-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="0ed81-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="0ed81-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
