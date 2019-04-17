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
# <a name="gestures-and-motion-controllers-in-unity"></a>I movimenti e i controller di movimento in Unity

Esistono due modi principali per agire sul [estasiati Unity](gaze-in-unity.md), [mano i movimenti](gestures.md) e [controller di movimento](motion-controllers.md). Accedere ai dati per entrambe le origini di input spaziali tramite le stesse API in Unity.

Unity offre due metodi principali per accedere ai dati di input spaziali per realtà mista di Windows, comuni *Input.GetButton/Input.GetAxis* API che funzionano tra più SDK per Unity XR, e un *InteractionManager / GestureRecognizer* API specifiche in Windows Mixed Reality che espone il set completo di dati di input spaziali disponibili.

## <a name="unity-buttonaxis-mapping-table"></a>Tabella di mapping pulsante/asse di Unity

Gli ID del pulsante e asse nella tabella seguente sono supportati in Unity Input Manager per i controller del movimento di realtà mista di Windows tramite il *Input.GetButton/GetAxis* API, mentre la colonna di "MR Windows specifiche" si riferisce alle proprietà disponibili all'esterno della *InteractionSourceState* tipo. Ognuna di queste API sono descritte in dettaglio nelle sezioni seguenti.

Il mapping di ID pulsante/asse per realtà mista di Windows corrisponde in genere Oculus pulsante/ID asse.

I mapping di ID del pulsante/asse per realtà mista di Windows sono diversi dai mapping di OpenVR in due modi:
1. Il mapping utilizza gli ID touchpad sono distinti dagli thumbstick, per supportare i controller con levette e touchpad multipli.
2. Il mapping consente di evitare l'overload il pulsante A e X ID per i pulsanti di Menu, lasciare quelli disponibili per i pulsanti fisici ABXY.

<table>
<tr>
<th rowspan="2">Input </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API comuni di Unity</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">API di Input specifica MR Windows</a><br />(XR. WSA. Input)</th>
</tr><tr>
<th> A sinistra </th><th> A destra</th>
</tr><tr>
<td> Selezionare il trigger premuto </td><td> Asse 9 = 1.0 </td><td> Asse 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> Valore analogico selezionare il trigger </td><td> Asse 9 </td><td> Asse 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Selezionare il trigger parzialmente premuto </td><td> Pulsante 14 <i>(gamepad compat)</i> </td><td> Pulsante 15 <i>(gamepad compat)</i> </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Pulsante di menu selezionato </td><td> Pulsante 6 * </td><td> Pulsante 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Pressione del pulsante triangolo di ridimensionamento </td><td> Asse 11 = 1.0 (nessun valore analogico)<br />Pulsante 4 <i>(gamepad compat)</i> </td><td> Asse 12 = 1.0 (nessun valore analogico)<br />Pulsante 5 <i>(gamepad compat)</i> </td><td> compreso</td>
</tr><tr>
<td> X Thumbstick <i>(a sinistra: -1,0, a destra: 1.0)</i> </td><td> Asse 1 </td><td> Asse 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Y Thumbstick <i>(top: -1,0, nella parte inferiore: 1.0)</i> </td><td> Asse 2 </td><td> Asse 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Thumbstick premuto </td><td> Pulsante 8 </td><td> Pulsante 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> X touchpad <i>(a sinistra: -1,0, a destra: 1.0)</i> </td><td> Asse 17 * </td><td> Asse 19 * </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Y touchpad <i>(top: -1,0, nella parte inferiore: 1.0)</i> </td><td> Asse 18 * </td><td> Asse 20 * </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Touchpad interessate </td><td> Pulsante 18 * </td><td> Pulsante 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad premuto </td><td> Pulsante 16 * </td><td> Pulsante 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF triangolo posa o posa puntatore </td><td colspan="2"> <i>Triangolo di ridimensionamento</i> rappresentare solo: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> Passare <i>triangolo</i> oppure <i>puntatore</i> come argomento: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Tenere traccia dello stato </td><td colspan="2"> <i>Posizione accuratezza origine perdita dei rischi e disponibili solo tramite l'API di MR specifici</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Questi ID pulsante/asse sono diversi dagli ID che usa Unity per OpenVR a causa di collisioni nelle associazioni utilizzate dal gamepad, Oculus tocco e OpenVR.

## <a name="grip-pose-vs-pointing-pose"></a>Triangolo di ridimensionamento posa confronto posa puntamento

Realtà mista di Windows supporta controller di movimento in un'ampia gamma di fattori di forma, con la progettazione del ogni controller che differiscono per la relazione tra la posizione dell'utente mano e naturale "inoltro" direzione tale app deve usare per fare riferimento durante il rendering di controller.

Per rappresentare meglio questi controller, esistono due tipi di può causare per ogni origine di interazione, è possibile esaminare i **posa triangolo** e il **posa puntatore**. Sia il triangolo di ridimensionamento posa e puntatore posa le coordinate sono espresse da tutte le API di Unity in coordinate complessive di Unity globale.

### <a name="grip-pose"></a>Triangolo di ridimensionamento posa

Il **triangolo posa** rappresenta la posizione di palmo di una mano rilevata da un HoloLens o palmo che contiene un controller di movimento.

In coinvolgenti auricolari, posa il triangolo di ridimensionamento è particolarmente utile per eseguire il rendering **manuale dell'utente** oppure **mantenuto un oggetto a disposizione dell'utente**, ad esempio un doppio taglio o gun. Posa il triangolo di ridimensionamento viene usata anche quando la visualizzazione di un controller di movimento, come le **renderizzabili modello** fornite da Windows per un movimento controller utilizza posa il triangolo di ridimensionamento come origine e il centro di rotazione.

Posa il triangolo di ridimensionamento è definita in modo specifico come indicato di seguito:
* Il **afferrare posizione**: Il centroide palm quando tenendo naturalmente, il controller è regolato sinistro o destro da allineare al centro la posizione all'interno del triangolo di ridimensionamento. Nel controller di movimento di realtà mista di Windows, questa posizione viene allineato a livello generale con il pulsante. é quindi.
* Il **afferrare asse a destra dell'orientamento**: Quando si apre completamente la mano per formare una posa flat con un dito di 5, il raggio è normale che palm (in avanti dal palmo a sinistra, con le versioni precedenti dal palmo a destra)
* Il **afferrare asse diretta dell'orientamento**: Quando si chiude la mano parzialmente (come se che contiene il controller), il raggio che punta "forward" tramite il tubo costituita dalle dita non thumb.
* Il **afferrare orientamento di asse**: L'asse verticale in cui è inclusa per le definizioni di destra e l'inoltro.

È possibile accedere posa il triangolo di ridimensionamento tramite l'API di input tra fornitori entrambi di Unity (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o tramite l'API Windows MR specifiche (*sourceState.sourcePose.TryGetPosition/Rotation*, che richiede di rappresentare i dati per il **triangolo** nodo).

### <a name="pointer-pose"></a>Puntatore posa

Il **posa puntatore** rappresenta la punta del controller in avanti che punta.

Il puntatore fornito dal sistema posa è particolarmente utile per raycast quando sei **il modello controller stesso per il rendering**. Se si esegue il rendering di un altro oggetto virtuale al posto di controller, ad esempio un gun virtuale, è necessario puntare con un raggio che risulta più naturale per l'oggetto virtuale, ad esempio un raggio che percorre cilindro del modello gun definito dall'app. Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, che punta all'oggetto virtuale sarà probabilmente più naturale per chi usa l'app.

È attualmente disponibile in Unity solo tramite l'API Windows MR specifici, posa il puntatore *sourceState.sourcePose.TryGetPosition/Rotation*passando *InteractionSourceNode.Pointer* come il discussione.

## <a name="controller-tracking-state"></a>Stato di rilevamento del controller

Ad esempio le cuffie, il controller di movimento di realtà mista di Windows non richiede alcuna configurazione dei sensori esterna tracciamento. Al contrario, i controller vengono rilevati da sensori in auricolare stesso.

Se l'utente sposta il controller all'esterno il della cuffia campo visivo, nella maggior parte dei casi Windows continuerà a dedurre le posizioni di controller e fornire all'app. Quando il controller ha perso visual rilevamento per tempo sufficiente, eliminerà le posizioni del controller nelle posizioni di accuratezza approssimativo.

A questo punto, il sistema eseguirà il corpo del blocco il controller per l'utente e la posizione dell'utente di rilevamento durante lo spostamento, quando si espongono ancora orientamento true del controller tramite sensori relativo orientamento interno. Molte App che usano i controller per puntare alla e attivare gli elementi dell'interfaccia utente può funzionare normalmente anche se in accuratezza approssimativo senza che l'utente vengano rilevate.

Il modo migliore per farsi un'idea di ciò è prova in prima persona. Guarda questo video con esempi di contenuti coinvolgenti che funziona con i controller di movimento in vari stati di rilevamento:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Ha a che fare in modo esplicito lo stato di rilevamento

Le app che si desiderano considerare le posizioni diverso a seconda dello stato di rilevamento possono andare oltre e controllare le proprietà sullo stato del controller, ad esempio *SourceLossRisk* e *PositionAccuracy*:

<table>
<tr>
<th> Tenere traccia dello stato </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Accuratezza elevata</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Elevata precisione per (a rischio di perdita)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Accuratezza approssimativo</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Nessuna posizione</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: orange"> false</td>
</tr>
</table>

Questi stati di rilevamento movimento controller sono definiti come segue:
* **Alta precisione:** Anche se il controller di movimento è all'interno il della cuffia campo visivo, in genere fornirà le posizioni di elevata precisione, basate sul rilevamento visual. Si noti che un controller di spostamento che momentaneamente lascia il campo visivo o momentaneamente è nascosto dai sensori visore VR (ad esempio, da altra parte dell'utente) continuerà a restituire pose elevata precisione per un breve periodo di tempo, basato sul rilevamento movimento inerziale del controller di sé stesso.
* **Elevata precisione (a rischio di perdita):** Quando l'utente sposta il controller di movimento oltre il bordo del campo visivo della cuffia, le cuffie saranno presto possibile tenere traccia visivamente della posizione del controller. L'app conosce quando il controller ha raggiunto il limite del campo di visualizzazione, vedere l'articolo di **SourceLossRisk** raggiungere 1.0. A questo punto, l'app può scegliere di sospendere i movimenti di controller che richiedono un flusso costante di altissima qualità creeranno.
* **Accuratezza approssimativo:** Quando il controller ha perso visual rilevamento per tempo sufficiente, eliminerà le posizioni del controller nelle posizioni di accuratezza approssimativo. A questo punto, il sistema eseguirà il corpo del blocco il controller per l'utente e la posizione dell'utente di rilevamento durante lo spostamento, quando si espongono ancora orientamento true del controller tramite sensori relativo orientamento interno. Molte App che usano i controller per puntare alla e attivare gli elementi dell'interfaccia utente possono operare come normale periodo di tempo accuratezza approssimativo senza che l'utente vengano rilevate. Le app con più intensi i requisiti di input possono scegliere di questo elenco da rilevare **elevata** approssimazione pari a **approssimato** accuratezza controllando il **PositionAccuracy** proprietà, per esempio per consentire all'utente un hitbox maggiori nelle destinazioni fuori dello schermo durante questo periodo.
* **Nessuna posizione:** Mentre il controller può operare accuratezza approssimativo per molto tempo, in alcuni casi il sistema sa che anche una posizione bloccata corpo non è significativa al momento. Ad esempio, un controller che è stato appena abilitato non può sono mai stato osservato visivamente o un utente può inserire verso il basso un controller che viene quindi prelevato da un altro utente. In tali casi, il sistema non fornirà a qualsiasi posizione all'app, e *TryGetPosition* restituirà false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>API di Unity comuni (Input.GetButton/GetAxis)

**Namespace:** *UnityEngine*, *UnityEngine.XR*<br>
**Tipi**: *Input*, *XR.InputTracking*

Unity Usa attualmente il general *Input.GetButton/Input.GetAxis* API per esporre l'input per [SDK Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [SDK OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html) e realtà mista di Windows, tra cui le mani e controller di movimento. Se l'app Usa queste API per l'input, può supportare facilmente i controller di transito tra più XR SDK, tra cui la realtà mista di Windows.

### <a name="getting-a-logical-buttons-pressed-state"></a>Recupero dello stato di premuto del pulsante logico

Per usare l'API di input di Unity generale, verranno in genere iniziare associando i pulsanti e assi per i nomi logici nel [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), associazione a ogni nome di un pulsante o un ID dell'asse. È quindi possibile scrivere codice che fa riferimento a tale nome logico pulsante / dell'asse.

Ad esempio, per eseguire il mapping per l'azione di invio grilletto del controller movimento a sinistra, passare a **Modifica > Impostazioni di progetto > Input** in Unity ed espandere le proprietà della sezione invio in assi. Modifica il **pulsante positivo** oppure **pulsante positivo Alt** proprietà da leggere **pulsante joystick 14**, simile al seguente:

![InputManager di Unity](images/unity-input-manager.png)<br>
*InputManager Unity*

Quindi è possibile controllare lo script per l'azione di invio utilizzando *Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
È possibile aggiungere pulsanti più logici modificando la **dimensioni** proprietà sotto **assi**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Recupero stato premuto di un pulsante fisico direttamente

È anche possibile accedere a manualmente i pulsanti da loro completo nome, utilizzando *Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Recupero di una mano o posa del controller di movimento

È possibile accedere la posizione e la rotazione del controller, usando *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Si noti che questo rappresenti posa triangolo di ridimensionamento del controller (in cui l'utente tiene premuto il controller) che è utile per il rendering di un doppio taglio o gun nel manuale dell'utente o un modello del controller stesso.

Si noti che la relazione tra questo posa triangolo di ridimensionamento e la posa puntatore (in cui il suggerimento del controller di punta) può variare tra i controller. In questo momento, l'accesso a posa puntatore del controller è possibile solo tramite l'input di MR specifiche API, descritti nelle sezioni seguenti.

## <a name="windows-specific-apis-xrwsainput"></a>API di Windows specifiche (XR. WSA. Input)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Tipi**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Per ottenere informazioni più dettagliate sugli input manuale di realtà mista di Windows (per HoloLens) e i controller di movimento, è possibile scegliere di usare le API di input spaziali specifiche di Windows con il *UnityEngine.XR.WSA.Input* dello spazio dei nomi. Ciò consente di accedere a informazioni aggiuntive, ad esempio accuratezza posizione o il tipo di origine, consentendo di indicare le mani e controller distanti.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Esecuzione del polling dello stato della mani e controller di movimento

È possibile eseguire il polling per questo stato per ogni origine (manualmente o movimento controller) l'interazione con il *GetCurrentReading* (metodo).

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Ciascuna *InteractionSourceState* otterrai back rappresenta un'origine l'interazione nel momento attuale nel tempo. Il *InteractionSourceState* espone informazioni quali:
* Quale [tipi di pressioni](motion-controllers.md) si verificano (selezione/Menu /. é quindi/Touchpad/Thumbstick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Altri dati specifici di movimento controller, tali il touchpad e/o del thumbstick coordinate XY e lo stato aggiornato

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* InteractionSourceKind sapere se l'origine è una mano o un controller di movimento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Esecuzione del polling può causare forward-stimato per il rendering

* Per il polling dei dati di origine l'interazione da mani e controller, le pose che otterrai sono pose forward-stimato per il momento nel tempo quando fotoni questo frame raggiungeranno gli occhi dell'utente.  Tali può causare stimato forward risultano particolarmente adatte per **rendering** il controller o un mantenuto ogni fotogramma dell'oggetto.  Se si ha come destinazione la pressione di un determinato o di rilascio con il controller, che sarà più accurato se si usa l'evento cronologico le API descritte di seguito.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* È anche possibile ottenere la posa head stimato forward per il frame corrente.  Come con la posa di origine, ciò è utile per **rendering** un cursore, anche se destinate a una determinata premere o una versione sarà più accurato se si usa l'evento cronologico le API descritte di seguito.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Gestione degli eventi di origine di interazione

Per gestire gli eventi di input in tempo reale con i propri dati accurati posa cronologici, è possibile gestire l'interazione dell'origine eventi invece di polling.

Per gestire l'interazione dell'origine eventi:
* Iscriviti a una *InteractionManager* evento di input. Per ogni tipo di evento di interazione che si è interessati, è necessario eseguire la sottoscrizione.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Gestire l'evento. Dopo che è necessario sottoscrivere un evento di interazione, si otterrà il callback quando appropriato. Nel *SourcePressed* esempio, si tratterà dopo che è stata rilevata l'origine e prima che venga rilasciato o persi.

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

È necessario interrompere la gestione di un evento quando sono più interessati nell'evento o si è l'eliminazione dell'oggetto che ha sottoscritto l'evento. Per interrompere la gestione dell'evento, annullare la sottoscrizione dall'evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Elenco di eventi di origine di interazione

Gli eventi di origine interazione disponibili sono:
* *InteractionSourceDetected* (origine diventa attiva)
* *InteractionSourceLost* (diventa inattivo)
* *InteractionSourcePressed* (tap, fare clic sul pulsante o pronunciato "selezionare")
* *InteractionSourceReleased* (fine di un tocco, il rilascio del pulsante o alla fine di "Select" pronunciato)
* *InteractionSourceUpdated* (sposta o in caso contrario, viene modificato uno stato)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Eventi per cronologici pose destinazione che corrispondono in modo più accurato una pressione o una versione

Le API di polling descritte in precedenza assegnare all'app pose stimato in avanti.  Durante le pose stimati sono ottimali per il rendering del controller o un oggetto virtuale palmare, può causare future non sono ottimali per lo sviluppo, per due motivi principali per:
* Quando l'utente preme un pulsante in un controller, può essere presente circa 20 ms di latenza wireless tramite Bluetooth prima che il sistema riceve la stampa.
* Quindi, se si usa una posa stimato forward, vi viene applicato per il tempo fotoni del frame corrente verranno raggiungere gli occhi dell'utente di destinazione un altro 10 a 20 ms della stima in avanti.

Ciò significa che il polling ti offre una posa origine o head costituire vale a dire 30-40 MS forward da dove head e le mani dell'utente in realtà sono state nuovamente quando la pressione o la versione si è verificato.  Per l'input manuale HoloLens, anche se non si verifichino ritardi nella trasmissione wireless, si verifica un ritardo di elaborazione simili per rilevare la stampa.

Di destinazione in modo accurato in base l'intenzione dell'utente originale per la pressione di un controller o manualmente, è consigliabile utilizzare l'origine cronologici posa o head posa da quella *InteractionSourcePressed* o *InteractionSourceReleased* evento di input.

È possibile una pressione di destinazione o di rilascio con i dati cronologici posa head dell'utente o il controller:
* Si è verificato il posa head al momento nel tempo quando preme un movimento o un controller, che può essere usato per **targeting** per determinare l'utente era [gazing](gaze.md) in:

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

* Si è verificato il posa di origine al momento nel tempo quando preme un controller di movimento, che può essere usato per **targeting** per determinare ciò che l'utente stava puntando il controller.  Questo sarà lo stato del controller che ha riscontrato la stampa.  Se si esegue il rendering il controller stesso, è possibile richiedere la posa puntatore anziché posa il triangolo di ridimensionamento, per riprendere il raggio da ciò che l'utente prenderà in considerazione i suggerimenti naturali che viene eseguito il rendering di controller di destinazione:

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

### <a name="event-handlers-example"></a>Esempio di gestori di eventi

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>Movimento composito ad alto livello API (GestureRecognizer)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Tipi**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

L'app anche è in grado di riconoscere i movimenti compositi livello superiore per i movimenti tenere premuto, manipolazione e l'esplorazione spaziale origini di input, Tap. È in grado di riconoscere i movimenti compositi in entrambi [mani](gestures.md) e [movimento controller](motion-controllers.md) usando il GestureRecognizer.

Ogni evento di movimento nel GestureRecognizer fornisce il SourceKind per l'input, nonché il raggio head destinazione al momento dell'evento. Alcuni eventi forniscono informazioni specifiche di contesto aggiuntive.

Sono disponibili solo pochi passaggi necessari per acquisire i movimenti usando un riconoscitore di movimento:
1. Creare un nuovo riconoscitore di movimento
2. Specificare quali i movimenti per il controllo
3. Sottoscrivere eventi per questi gesti
4. Avvio dell'acquisizione movimenti

### <a name="create-a-new-gesture-recognizer"></a>Creare un nuovo riconoscitore di movimento

Usare la *GestureRecognizer*, è necessario avere creato una *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Specificare quali i movimenti per il controllo

Specificare i movimenti di cui si è interessati tramite *SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Sottoscrivere eventi per questi gesti

Sottoscrivere eventi per i movimenti che si è interessati.

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
>Navigazione e modifica i movimenti si escludono a vicenda in un'istanza di un *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Avvio dell'acquisizione movimenti

Per impostazione predefinita, un *GestureRecognizer* non esegue il monitoraggio input finché *StartCapturingGestures()* viene chiamato. È possibile che un evento di movimento può essere generato dopo *StopCapturingGestures()* viene chiamato se l'input è stato eseguito prima il frame in cui *StopCapturingGestures()* è stata elaborata. Il *GestureRecognizer* memorizzerà se era attiva o disattiva durante il frame previou in cui il movimento è stata effettivamente eseguita, pertanto è affidabile per avviare e movimento di arresto monitoraggio basato su sguardo di questo frame destinazione.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Arrestare l'acquisizione di movimenti

Per arrestare il riconoscimento di movimento:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Rimozione di un sistema di riconoscimento di movimento

Ricordarsi di annullare la sottoscrizione agli eventi sottoscritti prima dell'eliminazione di un *GestureRecognizer* oggetto.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Il modello di controller di movimento in Unity per il rendering

![Teletrasporto e modello di Controller di movimento](images/motioncontrollertest-teleport-1000px.png)<br>
*Teletrasporto e modello di controller di movimento*

Per eseguire il rendering controller movimento nell'app che soddisfano i controller fisici utenti mantengono attivi e illustrare come vari pulsanti vengono premuti, è possibile usare la **MotionController prefab** nel [Toolkit di realtà mista ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Il prefab carica in modo dinamico il modello glTF corretto in fase di esecuzione dal driver del controller installato movimento del sistema.  È importante caricare dinamicamente questi modelli piuttosto che importarli manualmente nell'editor, in modo che l'app Visualizza modelli 3D fisicamente accurati per tutti i controller attuali e futuri utenti può avere.

1. Seguire le [introduttiva](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) istruzioni per scaricare il Toolkit di realtà mista e aggiungerlo al progetto Unity.
2. Se è stato sostituito con il *MixedRealityCameraParent* prefab come parte dei passaggi di Guida introduttiva, ora possibile iniziare.  Il prefab include per il rendering di movimento controller.  In caso contrario, aggiungere *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* in scena dal riquadro del progetto.  È opportuno aggiungere prefab come figlio di qualsiasi oggetto padre utilizzato per spostare la camera intorno a quando l'utente teleports all'interno della scena, in modo che i controller di lavoro con l'utente.  Se l'app non comporta la teleporting, è sufficiente aggiungere il prefab alla radice della scena.

## <a name="throwing-objects"></a>Generazione di oggetti

La generazione di oggetti in realtà virtuale è un problema più difficile e può inizialmente sembrare. Come con più fisicamente in base interazioni, quando si genera in gioco si comporta in modo imprevisto, è immediatamente evidente e interruzioni di full immersion. Abbiamo investito alcuni tempo a pensare in profondità come rappresentare un comportamento generando un'eccezione fisicamente corretto e hanno ideare alcune linee guida, abilitate tramite gli aggiornamenti alla piattaforma, che si vuole condividere con l'utente.

È possibile trovare un esempio del modo in cui è consigliabile implementare generando un'eccezione [qui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). In questo esempio segue queste linee quattro Guida:
* **Utilizzare il controller *velocità* invece di posizione**. Nell'aggiornamento di novembre di Windows, è stata introdotta una modifica nel comportamento quando nel [' approssimare ' stato di rilevamento posizionali](motion-controllers.md#controller-tracking-state). In questo stato, informazioni velocità sul controller continueranno a essere segnalati per, purché si ritiene che sia elevata accuratezza, che spesso è più lungo posizione rimane elevata precisione.
* **Incorporare il *velocità angolare* del controller**. Questa logica è contenuta nel `throwing.cs` del file nei `GetThrownObjectVelAngVel` metodo statico, all'interno del pacchetto con collegato riportato sopra:
   1. Come è consente di risparmiare velocità angolare, l'oggetto viene generata deve mantenere la stessa velocità angolare con cui erano al momento del lancio: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Come il centro della massa dell'oggetto generata è probabile che non in corrispondenza dell'origine di posa il triangolo di ridimensionamento, probabilmente ha una velocità diverse e il controller di nel frame di riferimento dell'utente. La parte della velocità dell'oggetto fornita in questo modo è la velocità di tangente istantanea del baricentro dell'oggetto intorno all'origine di controller. Questa velocità tangente è il prodotto incrociato di velocità angolare del controller con il vettore che rappresenta la distanza tra l'origine di controller e al centro della massa dell'oggetto viene generata.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. La velocità totale dell'oggetto generata è pertanto la somma della velocità del controller e questa velocità tangente: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Leggere con attenzione il *tempo* in corrispondenza del quale si applica alla velocità**. Quando viene premuto un pulsante, può richiedere fino a 20 ms per l'evento di bubbling tramite Bluetooth al sistema operativo. Ciò significa che se si effettuare il polling di una modifica dello stato di controller da premuto per non premuto o viceversa, le informazioni sul posa controller che ti offriamo, sarà prima di questa modifica nello stato. Inoltre, posa il controller presentata tramite l'API di polling in avanti stimata in modo da riflettere una probabile posa al momento verrà visualizzato il frame che può essere 20 ms quindi altre in futuro. Questa opzione è utile per *rendering* archiviati oggetti, ma si sommano il problema in fase di *targeting* l'oggetto come vengono calcolati i traiettoria per il momento in cui l'utente ha rilasciato i throw. Per fortuna, con l'aggiornamento di novembre, quando si desidera che un evento di Unity *InteractionSourcePressed* oppure *InteractionSourceReleased* viene inviata, lo stato include i dati cronologici posa da eseguire quando il pulsante è stato effettivamente premuto o rilasciato.  Per ottenere il più accurati per il rendering di controller e controller targeting durante genera un'eccezione, è necessario utilizzare correttamente il polling e gestione degli eventi, come appropriato:
   * Per la **rendering controller** ogni fotogramma, l'app deve prevedere il posizionamento del controller *GameObject* nel controller stimato forward comportare per volta photon del frame corrente.  Ottenere i dati da Unity, ad esempio le API di polling *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oppure  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Per la **destinato a controller** dopo una pressione o una versione, l'app deve raycast e calcolare traiettorie base la posa controller cronologici per l'evento premere o versione.  Ottenere i dati dalla gestione degli eventi Unity API, ad esempio  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Usare il triangolo di ridimensionamento posa**. Velocità e velocità angolare vengono segnalati rispetto al posa triangolo, non posa puntatore.

Generando un'eccezione continuerà a migliorare con i futuri aggiornamenti di Windows e sarà possibile trovare altre informazioni su di esso.

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>Accelera lo sviluppo con il Toolkit di realtà mista

Esistono due scene di esempio su InputManager e MotionController in Unity. Tramite questi scene, è possibile imparare a utilizzare InputManager del MRTK e accesso dati gestiscono gli eventi dai pulsanti di controller di movimento.

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [File Leggimi di dettagli tecnici](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![Esempio di input in background nelle MRTK](images/MRTK_ExampleScene_Input.png)<br>
*Esempio di input in background nelle MRTK*

### <a name="automatic-scene-setup"></a>Programma di installazione automatica scena

Quando si importano [MRTK rilasciare pacchetti Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonare il progetto dal [repository di GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), si desidera trovare un nuovo menu 'Toolkit realtà mista' in Unity. Nel menu 'Configura', verrà visualizzato il menu 'Applica misto realtà scena impostazioni'. Quando si fa clic si, rimuove la fotocamera predefinita e aggiunge i componenti fondamentali - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menu MRTK per l'installazione di scena](images/MRTK_Input_Menu.png)<br>
*Menu MRTK per l'installazione di scena*

![Programma di installazione automatica di scena in MRTK](images/MRTK_HowTo_Input1.png)<br>
*Programma di installazione automatica di scena in MRTK*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefab

È possibile aggiungere anche manualmente queste informazioni dal Pannello di progetto. È possibile trovare questi componenti come prefabs. Quando si cercano **MixedRealityCamera**, sarà possibile visualizzare due diversi fotocamera prefabs. È, la differenza **MixedRealityCamera** è la fotocamera solo prefab mentre **MixedRealityCameraParent** include i componenti aggiuntivi per le cuffie coinvolgente e concreto, ad esempio teletrasporto, movimento Controller e limiti.

![Fotocamera prefab nel MRTK](images/MRTK_HowTo_Input2.png)<br>
*Fotocamera prefab nel MRTK*

**MixedRealtyCamera** supporta visore VR immersivi e HoloLens. Rileva il tipo di dispositivo e consente di ottimizzare le proprietà, ad esempio cancella i flag e Skybox. Di seguito è possibile trovare alcune delle proprietà più utili è possibile personalizzare, ad esempio un cursore personalizzato, i modelli di Controller di movimento e Floor.

![Proprietà per il controller di movimento, cursore e Floor](images/MRTK_HowTo_Input3.png)<br>
*Proprietà per il controller di movimento, cursore e Floor*

## <a name="follow-along-with-tutorials"></a>Segui le esercitazioni

Esercitazioni dettagliate, con esempi di personalizzazione più dettagliati, sono disponibili in Academy la realtà mista:

- [Input di MR 211: Movimento](holograms-211.md)
- [Input di MR 213: Controller di movimento](mixed-reality-213.md)

[![Input di MR 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Input di MR 213 - Motion controller*

## <a name="see-also"></a>Vedere anche

* [Movimenti](gestures.md)
* [Controller di movimento](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [InteractionInputSource.cs in MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
