---
title: Movimenti e controller di movimento in Unity
description: Ci sono due modi principali per agire sullo sguardo in Unity, movimenti della mano e controller di movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: movimenti, controller di movimento, Unity, sguardo, input
ms.openlocfilehash: a7ca5a895015ba0458f0f64f1422612e797f5067
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435223"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Movimenti e controller di movimento in Unity

Ci sono due modi principali per agire sullo [sguardo in Unity](gaze-in-unity.md), [movimenti della mano](gaze-and-commit.md#composite-gestures) e [controller di movimento](motion-controllers.md) in HoloLens e HMD immersivi. È possibile accedere ai dati per entrambe le origini dell'input spaziale tramite le stesse API in Unity.

Unity offre due modi principali per accedere ai dati di input spaziali per la realtà mista di Windows, le API *input. GetButton/input. getaxis* comuni che funzionano su più SDK di Unity XR e un'API *InteractionManager/GestureRecognizer* specifica di Realtà mista di Windows che espone il set completo di dati di input spaziali disponibili.

## <a name="unity-buttonaxis-mapping-table"></a>Pulsante Unity/tabella di mapping asse

Gli ID dei pulsanti e degli assi nella tabella seguente sono supportati nel gestore di input di Unity per i controller di movimento della realtà mista di Windows tramite le API *input. GetButton/getaxis* , mentre la colonna "Windows specific" si riferisce alle proprietà disponibili nel Tipo *InteractionSourceState* . Ognuna di queste API è descritta in dettaglio nelle sezioni riportate di seguito.

I mapping degli ID di pulsanti/assi per la realtà mista di Windows in genere corrispondono agli ID dell'asse o del pulsante Oculus.

I mapping degli ID di pulsanti/assi per la realtà mista di Windows differiscono dai mapping di OpenVR in due modi:
1. Il mapping USA ID touchpad distinti da levetta per supportare i controller con ThumbSticks e touchpad.
2. Il mapping evita l'overload degli ID dei pulsanti A e X per i pulsanti di menu, in modo da lasciare quelli disponibili per i pulsanti ABXY fisici.

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API Unity comuni</a><br />(Input. GetButton/getaxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">API di input specifica di Windows</a><br />XR. WSA. Input</th>
</tr><tr>
<th> Mano sinistra </th><th> A destra</th>
</tr><tr>
<td> Seleziona trigger premuto </td><td> AXIS 9 = 1,0 </td><td> Asse 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Selezionare il trigger valore analogico </td><td> Asse 9 </td><td> Asse 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Selezione trigger parzialmente premuto </td><td> Pulsante 14 <i>(gamepad compat)</i> </td><td> Pulsante 15 <i>(gamepad compat)</i> </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Pulsante di menu premuto </td><td> Pulsante 6 * </td><td> Pulsante 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Pulsante grip premuto </td><td> Asse 11 = 1,0 (nessun valore analogo)<br />Pulsante 4 <i>(gamepad compat)</i> </td><td> Asse 12 = 1,0 (nessun valore analogo)<br />Pulsante 5 <i>(gamepad compat)</i> </td><td> afferrato</td>
</tr><tr>
<td> Levetta X <i>(Left:-1,0, right: 1,0)</i> </td><td> Asse 1 </td><td> Asse 4 </td><td> thumbstickPosition. x</td>
</tr><tr>
<td> Levetta Y <i>(Top:-1,0, bottom: 1,0)</i> </td><td> Asse 2 </td><td> Asse 5 </td><td> thumbstickPosition. y</td>
</tr><tr>
<td> Levetta premuto </td><td> Pulsante 8 </td><td> Pulsante 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(Left:-1,0, right: 1,0)</i> </td><td> Asse 17 * </td><td> Asse 19 * </td><td> touchpadPosition. x</td>
</tr><tr>
<td> Touchpad Y <i>(Top:-1,0, bottom: 1,0)</i> </td><td> Asse 18 * </td><td> Asse 20 * </td><td> touchpadPosition. y</td>
</tr><tr>
<td> Tocco touchpad </td><td> Pulsante 18 * </td><td> Pulsante 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad premuto </td><td> Pulsante 16 * </td><td> Pulsante 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF della posa o del puntatore del grip </td><td colspan="2"> Solo <i>grip</i> per la posa: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></td><td> Passare il <i>grip</i> o il <i>puntatore</i> come argomento: SourceState. sourcePose. TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Stato di rilevamento </td><td colspan="2"> L' <i>accuratezza della posizione e il rischio di perdita di codice sorgente sono disponibili solo tramite API specifiche</i> del </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. Properties. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Questi ID di pulsanti/assi sono diversi dagli ID usati da Unity per OpenVR a causa di conflitti nei mapping usati dai gamepad, Oculus touch e OpenVR.

## <a name="grip-pose-vs-pointing-pose"></a>Posa del grip e puntamento

La realtà mista di Windows supporta i controller di movimento in diversi fattori di forma, con la progettazione di ogni controller diversa nella relazione tra la posizione della mano dell'utente e la direzione naturale "Avanti" che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, esistono due tipi di pose che è possibile esaminare per ogni origine interazione, la **posizione del grip** e la **posizione del puntatore**. Sia le coordinate della formula del grip che del puntatore sono espresse da tutte le API Unity nelle coordinate globali di Unity.

### <a name="grip-pose"></a>Pose di grip

La posizione del **grip** rappresenta la posizione della Palma di una mano rilevata da un HoloLens o della palma che contiene un controller di movimento.

Negli auricolari immersivi, la disposizione dei grip è la scelta migliore per eseguire **il rendering della mano dell'utente** o di **un oggetto contenuto nella mano**, ad esempio una spada o una pistola. La posizione del grip viene usata anche durante la visualizzazione di un controller di movimento, perché il **modello di rendering** fornito da Windows per un controller di movimento usa la posizione del grip come origine e centro di rotazione.

Il grip viene definito in modo specifico come segue:
* **Posizione del grip**: il centro della palma quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del grip. Sul controller di movimento per la realtà mista di Windows, questa posizione viene in genere allineata con il pulsante afferra.
* L' **asse destro dell'orientamento del grip**: quando si apre completamente la mano per formare una formula a 5 dita piatta, il raggio normale per la Palma (in avanti dal palmo sinistro e viceversa)
* **Asse di avanzamento dell'orientamento del grip**: quando si chiude parzialmente la mano (come se si utilizzasse il controller), il raggio che punta "in poi" attraverso il tubo formato dalle dita non Thumb.
* **Asse verticale dell'orientamento del grip**: l'asse verso l'alto implicato dalle definizioni di destra e di avanzamento.

È possibile accedere al grip con l'API di input tra fornitori di Unity ( *[XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o tramite l'API specifica di Windows (*SourceState. SourcePose. TryGetPosition/Rotation*, che richiede i dati di post per il nodo **grip** ).

### <a name="pointer-pose"></a>Posa puntatore

Il **puntatore** posizionato rappresenta il suggerimento del controller che punta in futuro.

La disposizione del puntatore fornita dal sistema è ideale per Raycast quando si esegue **il rendering del modello di controller**. Se si esegue il rendering di un altro oggetto virtuale al posto del controller, ad esempio una pistola virtuale, è necessario puntare con un raggio più naturale per tale oggetto virtuale, ad esempio un raggio che viaggia lungo il barilotto del modello Gun definito dall'app. Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, puntare con l'oggetto virtuale sarà probabilmente più naturale per quelli che usano l'app.

Attualmente, la posa del puntatore è disponibile in Unity solo tramite l'API specifica di Windows, *sourceState. sourcePose. TryGetPosition/Rotation*, passando *InteractionSourceNode. pointer* come argomento.

## <a name="controller-tracking-state"></a>Stato di rilevamento del controller

Come gli auricolari, il controller di movimento di realtà mista di Windows non richiede l'installazione di sensori di rilevamento esterni. Il controller viene invece rilevato dai sensori nell'auricolare.

Se l'utente sposta i controller fuori dal campo di visualizzazione dell'auricolare, nella maggior parte dei casi Windows continuerà a dedurre le posizioni del controller e le fornirà all'app. Quando il controller ha perso il rilevamento visivo per un periodo di tempo sufficiente, le posizioni del controller vengono rilasciate a posizioni di accuratezza approssimativa.

A questo punto, il sistema bloccherà il controller all'utente, tenendo traccia della posizione dell'utente mentre si spostano, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano i controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con una precisione approssimativa senza che l'utente abbia notato.

Il modo migliore per ottenere questo aspetto è provare a eseguire l'operazione. Vedere questo video con esempi di contenuti immersivi che funzionano con i controller di movimento in diversi Stati di rilevamento:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Ragionamento sullo stato di rilevamento in modo esplicito

Le app che desiderano gestire le posizioni in modo diverso in base allo stato di rilevamento possono andare oltre e controllare le proprietà nello stato del controller, ad esempio *SourceLossRisk* e *PositionAccuracy*:

<table>
<tr>
<th> Stato di rilevamento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td>   di <b>accuratezza elevata</b></td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alta </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza elevata (a rischio di perdita)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alta </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza approssimativa</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Nessuna posizione</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: orange"> false</td>
</tr>
</table>

Questi stati di rilevamento del controller di movimento sono definiti come segue:
* **Accuratezza elevata:** Mentre il controller di movimento si trova all'interno del campo di visualizzazione dell'auricolare, in genere fornisce posizioni con accuratezza elevata, in base al rilevamento visivo. Si noti che un controller che sposta temporaneamente il campo di visualizzazione o è temporaneamente nascosto dai sensori dell'auricolare (ad esempio, da parte dell'utente) continuerà a restituire le pose con precisione elevata per un breve periodo di tempo, in base al rilevamento inerziale del controller. stesso.
* **Accuratezza elevata (a rischio di perdita):** Quando l'utente sposta il controller di movimento oltre il bordo del campo di visualizzazione dell'auricolare, l'auricolare non sarà presto in grado di rilevare visivamente la posizione del controller. L'app sa quando il controller ha raggiunto questo limite FOV visualizzando il **SourceLossRisk** REACH 1,0. A questo punto, l'app può scegliere di sospendere i movimenti del controller che richiedono un flusso costante di pose di qualità molto elevata.
* **Accuratezza approssimativa:** Quando il controller ha perso il rilevamento visivo per un periodo di tempo sufficiente, le posizioni del controller vengono rilasciate a posizioni di accuratezza approssimativa. A questo punto, il sistema bloccherà il controller all'utente, tenendo traccia della posizione dell'utente mentre si spostano, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni. Molte app che usano i controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con una precisione approssimativa senza che l'utente ne abbia notato. Le app con requisiti di input più pesanti possono scegliere di comprendere questo calo dall'accuratezza **elevata** all'accuratezza **approssimativa** controllando la proprietà **PositionAccuracy** , ad esempio per offrire all'utente un hitbox più generoso sulle destinazioni fuori schermo. Durante questo periodo di tempo.
* **Nessuna posizione:** Mentre il controller può funzionare con una precisione approssimativa per molto tempo, a volte il sistema sa che anche una posizione bloccata dal corpo non è al momento significativa. Ad esempio, un controller appena attivato potrebbe non essere mai stato osservato visivamente oppure un utente può arrestare un controller che viene quindi prelevato da qualcun altro. In questi casi, il sistema non fornirà alcuna posizione all'app e *TryGetPosition* restituirà false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>API Unity comuni (input. GetButton/getaxis)

**Spazio dei nomi:** *UnityEngine*, *UnityEngine. XR*<br>
**Tipi**: *input*, *XR. InputTracking*

Unity usa attualmente le API *input. GetButton/input. getaxis* per esporre l'input per [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [l'SDK di OpenVR e la](https://docs.unity3d.com/Manual/OpenVRControllers.html) realtà mista di Windows, inclusi i controller hands e Motion. Se l'app usa queste API per l'input, può supportare facilmente i controller di movimento tra più SDK XR, inclusa la realtà mista di Windows.

### <a name="getting-a-logical-buttons-pressed-state"></a>Recupero dello stato premuto di un pulsante logico

Per usare le API di input di Unity generale, si inizia in genere collegando pulsanti e assi ai nomi logici in [Gestione input Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), associando un pulsante o gli ID dell'asse a ogni nome. È quindi possibile scrivere codice che fa riferimento a tale nome di pulsante/asse logico.

Ad esempio, per eseguire il mapping del pulsante trigger del controller di movimento sinistro all'azione Invia, passare a **modifica > impostazioni progetto > input** in Unity ed espandere le proprietà della sezione Submit in assi. Modificare la proprietà **pulsante postali** o **ALT positivo pulsante** per leggere il **pulsante del joystick 14**, come indicato di seguito:

](images/unity-input-manager.png) InputManager di Unity ![<br>
*Unity InputManager*

Lo script può quindi verificare la presenza di un'azione di invio tramite *input. GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
È possibile aggiungere più pulsanti logici modificando la proprietà **size** in **assi**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Ottenere direttamente lo stato premuto di un pulsante fisico

È anche possibile accedere manualmente ai pulsanti con il nome completo, usando *input. GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Acquisizione di una mano o di un controller di movimento

È possibile accedere alla posizione e alla rotazione del controller usando *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Si noti che questo rappresenta la posizione del grip del controller (dove l'utente possiede il controller), che è utile per il rendering di una spada o di una pistola nella mano dell'utente o di un modello del controller stesso.

Si noti che la relazione tra la posizione del grip e la posizione del puntatore (dove la punta del controller sta puntando) può variare tra i controller. Al momento, l'accesso alla posizione del puntatore del controller è possibile solo tramite l'API di input specifica del sig, descritta nelle sezioni riportate di seguito.

## <a name="windows-specific-apis-xrwsainput"></a>API specifiche di Windows (XR. WSA. Input

**Spazio dei nomi:** *UnityEngine. XR. WSA. input*<br>
**Tipi**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Per ottenere informazioni più dettagliate sull'input della realtà mista di Windows (per HoloLens) e sui controller di movimento, è possibile scegliere di usare le API di input spaziali specifiche di Windows nello spazio dei nomi *UnityEngine. XR. WSA. input* . In questo modo è possibile accedere a informazioni aggiuntive, come l'accuratezza della posizione o il tipo di origine, che consentono di distinguere le mani e i controller.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Polling dello stato di hands and Motion Controllers

È possibile eseguire il polling dello stato di questo frame per ogni origine interazione (controller di movimento o mano) usando il metodo *GetCurrentReading* .

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Ogni *InteractionSourceState* restituito rappresenta un'origine interazione nel momento corrente. *InteractionSourceState* espone informazioni come:
* Quali [tipi di presse](motion-controllers.md) si verificano (Select/menu/afferrare/touchpad/levetta)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Altri dati specifici per i controller di movimento, come le coordinate XY di touchpad e/o levetta e lo stato toccato

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* InteractionSourceKind per verificare se l'origine è una mano o un controller di movimento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Polling per le pose di rendering con stima avanzata

* Quando si esegue il polling per i dati di origine dell'interazione da mani e controller, le pose ricevute sono le pose stimate in avanti per il momento in cui i fotoni del frame raggiungono gli occhi dell'utente.  Queste pose con stima avanzata vengono usate in modo ottimale per il **rendering** del controller o di un oggetto mantenuto per ogni frame.  Se si fa riferimento a una determinata pressione o rilascio con il controller, questo sarà più accurato se si usano le API degli eventi cronologici descritte di seguito.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* È anche possibile ottenere la formula Head con stima avanzata per il frame corrente.  Come per la posa di origine, questa operazione è utile per il **rendering** di un cursore, anche se la scelta di una determinata pressione o rilascio sarà più accurata se si usano le API degli eventi cronologici descritte di seguito.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Gestione degli eventi di origine interazione

Per gestire gli eventi di input Man mano che si verificano con i dati di posa cronologici accurati, è possibile gestire gli eventi di origine interazione anziché il polling.

Per gestire gli eventi di origine interazione:
* Eseguire la registrazione per un evento di input *InteractionManager* . Per ogni tipo di evento di interazione a cui si è interessati, è necessario sottoscriverlo.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Gestire l'evento. Una volta effettuata la sottoscrizione a un evento di interazione, si otterrà il callback quando appropriato. Nell'esempio *SourcePressed* , questo sarà dopo che l'origine è stata rilevata e prima che venga rilasciata o persa.

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

### <a name="how-to-stop-handling-an-event"></a>Come interrompere la gestione di un evento

È necessario arrestare la gestione di un evento quando non si è più interessati all'evento o si sta eliminando l'oggetto che ha sottoscritto l'evento. Per arrestare la gestione dell'evento, annullare la sottoscrizione all'evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Elenco di eventi di origine interazione

Gli eventi di origine interazione disponibili sono:
* *InteractionSourceDetected* (l'origine diventa attiva)
* *InteractionSourceLost* (diventa inattivo)
* *InteractionSourcePressed* (toccare, premere il pulsante o "Select")
* *InteractionSourceReleased* (fine di un tocco, pulsante rilasciato o fine di "Select" pronunciata)
* *InteractionSourceUpdated* (sposta o modifica in altro modo lo stato)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Gli eventi per il targeting cronologico rappresentano la corrispondenza più accurata tra una stampa o una versione

Le API di polling descritte in precedenza forniscono le pose previste dall'app.  Anche se queste pose stimate sono ideali per il rendering del controller o di un oggetto palmare virtuale, le pose future non sono ottimali per la destinazione, per due motivi principali:
* Quando l'utente preme un pulsante su un controller, è possibile che si verifichino 20ms di latenza wireless su Bluetooth prima che il sistema riceva la pressione.
* Quindi, se si usa una formula con stima di avanzamento, è possibile applicare un altro 20ms di stima in diretta per individuare l'ora in cui i fotoni del frame corrente raggiungono gli occhi dell'utente.

Questo significa che il polling fornisce una posizione di origine o una posizione Head che è 30-40ms in uscita dal punto in cui si è verificata l'intestazione e le mani dell'utente.  Per l'input della mano HoloLens, anche se non si verifica alcun ritardo di trasmissione wireless, si verifica un ritardo di elaborazione simile per rilevare la pressione.

Per definire la destinazione in modo accurato in base all'intento originale dell'utente per la pressione di un controller o una mano, è necessario usare la funzione di origine o di intestazione di origine cronologica da tale evento di input *InteractionSourcePressed* o *InteractionSourceReleased* .

È possibile fare riferimento a una stampa o a una versione con dati di posa cronologici dall'Head dell'utente o dal controller:
* Il primo posto nel momento in cui [si è verificato](gaze-and-commit.md) un movimento o un controller, che può essere **usato per definire** la scelta dell'utente:

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

* La posizione di origine nel momento in cui si è verificata la pressione di un controller di movimento, che può essere **usata per determinare** l'elemento che l'utente stava puntando al controller.  Si tratta dello stato del controller che ha riscontrato la pressione.  Se si esegue il rendering del controller stesso, è possibile richiedere la presenza del puntatore anziché il grip, per sparare al raggio di destinazione da quello che l'utente considererà il suggerimento naturale del controller sottoposto a rendering:

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

### <a name="event-handlers-example"></a>Esempio di gestori eventi

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>API per movimenti compositi di alto livello (GestureRecognizer)

**Spazio dei nomi:** *UnityEngine. XR. WSA. input*<br>
**Tipi**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

L'app può anche riconoscere movimenti compositi di livello superiore per le origini di input spaziali, i movimenti di tocco, di manipolazione e di navigazione. È possibile riconoscere questi movimenti compositi tra [le mani](gaze-and-commit.md#composite-gestures) e i [controller di movimento](motion-controllers.md) usando l'oggetto GestureRecognizer.

Ogni evento di movimento nell'oggetto GestureRecognizer fornisce SourceKind per l'input, nonché il raggio Head di destinazione al momento dell'evento. Alcuni eventi forniscono informazioni aggiuntive specifiche del contesto.

Sono necessari solo pochi passaggi per acquisire i movimenti usando un riconoscitore di movimento:
1. Creare un nuovo riconoscitore di movimento
2. Specificare i movimenti da controllare
3. Sottoscrivere gli eventi per questi movimenti
4. Avviare l'acquisizione di movimenti

### <a name="create-a-new-gesture-recognizer"></a>Creare un nuovo riconoscitore di movimento

Per utilizzare l'oggetto *GestureRecognizer*, è necessario avere creato un oggetto *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Specificare i movimenti da controllare

Specificare i movimenti a cui si è interessati tramite *SetRecognizableGestures ()* :

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Sottoscrivere gli eventi per questi movimenti

Sottoscrivere gli eventi per i movimenti a cui si è interessati.

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
>I movimenti di spostamento e manipolazione si escludono a vicenda in un'istanza di un oggetto *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Avviare l'acquisizione di movimenti

Per impostazione predefinita, un oggetto *GestureRecognizer* non monitora l'input fino a quando non viene chiamato *StartCapturingGestures ()* . È possibile che venga generato un evento di movimento dopo che è stato chiamato *StopCapturingGestures ()* se l'input è stato eseguito prima del frame in cui è stato elaborato *StopCapturingGestures ()* . L'oggetto *GestureRecognizer* ricorda se era attivo o disattivato durante il frame prece in cui si è effettivamente verificato il movimento ed è quindi affidabile per avviare e arrestare il monitoraggio dei movimenti in base alla destinazione dello sguardo del frame.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Interrompi acquisizione movimenti

Per arrestare il riconoscimento del movimento:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Rimozione di un riconoscimento di movimento

Ricordarsi di annullare la sottoscrizione agli eventi sottoscritti prima di eliminare un oggetto *GestureRecognizer* .

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Rendering del modello di controller di movimento in Unity

modello ![Motion controller e Teleporting](images/motioncontrollertest-teleport-1000px.png)<br>
*Modello e teleporting del controller di movimento*

Per eseguire il rendering dei controller di movimento nell'app che corrispondono ai controller fisici che gli utenti mantengono e si articolano con la pressione di vari pulsanti, è possibile usare la **prefabbricazione MotionController** nel [Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Questa prefabbricata carica dinamicamente il modello glTF corretto in fase di esecuzione dal driver del controller di movimento installato dal sistema.  È importante caricare i modelli in modo dinamico, anziché importarli manualmente nell'editor, in modo che l'app visualizzi modelli 3D fisicamente accurati per i controller correnti e futuri che possono avere gli utenti.

1. Seguire le istruzioni [Introduzione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) per scaricare il Toolkit di realtà mista e aggiungerlo al progetto Unity.
2. Se la fotocamera è stata sostituita con la prefabbricata *MixedRealityCameraParent* come parte del Introduzione passaggi, è possibile iniziare.  Il prefabbricato include il rendering del controller di movimento.  In caso contrario, aggiungere *assets/HoloToolkit/input/precasers/MotionControllers. prefabbricate* nella scena dal riquadro progetto.  È opportuno aggiungere tale prefabbricato come elemento figlio di qualsiasi oggetto padre utilizzato per spostare la fotocamera quando l'utente esegue il teleportamento all'interno della scena, in modo che i controller siano insieme all'utente.  Se l'app non implica il Teleporting, è sufficiente aggiungere il prefabbricato alla radice della scena.

## <a name="throwing-objects"></a>Generazione di oggetti

La generazione di oggetti in realtà virtuale è un problema più complesso che può sembrare. Come per la maggior parte delle interazioni basate fisicamente, quando la generazione di un gioco agisce in modo imprevisto, è immediatamente evidente e interrompe l'immersione. Abbiamo dedicato un po' di tempo a comprendere in modo approfondito come rappresentare un comportamento di generazione fisico corretto e avere a disposizione alcune linee guida, abilitate tramite aggiornamenti della piattaforma, che vogliamo condividere con te.

È possibile trovare un esempio di come si consiglia di implementare il lancio [qui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Questo esempio segue le quattro linee guida seguenti:
* **Utilizzare la *velocità* del controller invece della posizione**. Nell'aggiornamento di novembre di Windows è stata introdotta una modifica nel comportamento quando si [Verifica lo stato di rilevamento posizionale '' approssimativo](motion-controllers.md#controller-tracking-state). In questo stato, le informazioni sulla velocità del controller continueranno a essere segnalate fino a quando riteniamo che la precisione è elevata, che è spesso più lunga della posizione rimane alta.
* **Incorporare la *velocità angolare* del controller**. Questa logica è interamente contenuta nel file di `throwing.cs` nel metodo statico `GetThrownObjectVelAngVel`, all'interno del pacchetto collegato sopra:
   1. Poiché viene mantenuta la velocità angolare, l'oggetto generato deve mantenere la stessa velocità angolare del momento in cui si trovava al momento della generazione: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Poiché il centro della massa dell'oggetto generato è probabilmente diverso dall'origine della posizione del grip, probabilmente ha una velocità diversa rispetto a quella del controller nel frame di riferimento dell'utente. La parte della velocità dell'oggetto contribuito in questo modo è la velocità tangenziale istantanea del centro della massa dell'oggetto generato intorno all'origine del controller. Questa velocità tangenziale è il prodotto incrociato della velocità angolare del controller con il vettore che rappresenta la distanza tra l'origine del controller e il centro della massa dell'oggetto generato.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. La velocità totale dell'oggetto generato è quindi la somma della velocità del controller e della velocità tangenziale: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Prestare particolare attenzione all' *ora* in cui viene applicata la velocità**. Quando si preme un pulsante, può essere necessario fino a 20ms per l'evento per propagarsi attraverso la tecnologia Bluetooth al sistema operativo. Ciò significa che se si esegue il polling di una modifica dello stato del controller da Pressed a not Pressed o viceversa, il controller pone le informazioni che verranno apportate in precedenza in questa modifica dello stato. Inoltre, la presentazione del controller presentata dall'API di polling viene stimata in modo da riflettere una probabile situazione nel momento in cui verrà visualizzato il frame, che potrebbe essere più 20ms in futuro. Questo è ideale per il *rendering* degli oggetti conservati, ma costituisce un problema di tempo per la *destinazione* dell'oggetto durante il calcolo della traiettoria nel momento in cui l'utente ha rilasciato il proprio Throw. Fortunatamente, con l'aggiornamento di novembre, quando viene inviato un evento Unity, ad esempio *InteractionSourcePressed* o *InteractionSourceReleased* , lo stato include i dati cronologici di post di ritorno quando il pulsante è stato effettivamente premuto o rilasciato.  Per ottenere il rendering del controller più accurato e la destinazione del controller durante i lanci, è necessario usare correttamente il polling e la gestione degli eventi, in base alle esigenze:
   * Per il **rendering del controller** ogni frame, l'app deve posizionare il *GameObject* del controller in corrispondenza del controller con stima avanzata per l'ora del fotone del frame corrente.  Si ottengono questi dati dalle API di polling Unity, ad esempio *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o *[XR. WSA. Input. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .
   * Per il **controller che punta** alla stampa o al rilascio, l'app deve Raycast e calcolare le traiettorie in base alla definizione del controller cronologico per l'evento di stampa o di rilascio.  Si ottengono questi dati dalle API di gestione degli eventi di Unity, ad esempio *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .
* **Utilizzare la disposizione del grip**. La velocità e la velocità angolari vengono segnalate rispetto alla posizione del grip, non alla posizione del puntatore.

La generazione continuerà a migliorare con gli aggiornamenti futuri di Windows e ci si aspetterà di trovare altre informazioni su di essa.

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>Controller movimento e movimento in MRTK V2

È possibile accedere a gesture e Motion controller dal gestore di input. 
* [Movimento in MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [Controller di movimento in MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>Segui le esercitazioni

Le esercitazioni dettagliate, con esempi di personalizzazione più dettagliati, sono disponibili in Mixed Reality Academy:

- [Input MR 211: movimento](holograms-211.md)
- [Input MR 213: controller di movimento](mixed-reality-213.md)

[![MR input 213-controller di movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Input MR 213-controller di movimento*

## <a name="see-also"></a>Vedi anche

* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Controller del movimento](motion-controllers.md)


