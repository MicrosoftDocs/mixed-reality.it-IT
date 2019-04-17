---
title: Sistemi di coordinate in Unity
description: Informazioni su come compilare seduti, permanente, a scalabilità chat room e su scala mondiale mista realtà esperienze in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate spaziale, solo l'orientamento, seduti a scalabilità, la condizione di scalabilità, chat room-scalabilità, mondo della scala, viene posizionata a 360 gradi, e in esecuzione, chat, mondo, scalabilità, posizione, orientamento, Unity, ancoraggio, ancoraggio spaziale, ancoraggio world, bloccato world, blocco a livello mondiale, bloccato corpo, corpo del blocco, rilevamento perdite, locatability, limiti, centrare di nuovo
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605050"
---
# <a name="coordinate-systems-in-unity"></a>Sistemi di coordinate in Unity

Realtà mista di Windows supporta le App in un'ampia gamma di [esperienza Scale](coordinate-systems.md), dalle App solo l'orientamento e la scala seduto backup tramite chat-ridimensionare le app. HoloLens, consentono di andare oltre e compilare le app su scala mondiale che consentono agli utenti di scorrere oltre 5 metri, esplorazione di un intero piano di un edificio e versioni successive.

Il primo passaggio nella creazione di un'esperienza di realtà mista in Unity consiste nel determinare quale [esperienza scalabilità](coordinate-systems.md) destinazione per l'app.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creazione di un'esperienza solo orientamento seduto scala o

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Per creare un **orientamento sola** o **esperienza su scala seduto**, è necessario impostare Unity per il fermo rilevamento tipo dello spazio. Sistema di coordinate complessive di Unity per tenere traccia consente di impostare il [fotogramma di riferimento fisso](coordinate-systems.md#spatial-coordinate-systems). Nella modalità di rilevamento fisso, il contenuto inserito nell'editor subito prima di percorso predefinito della camera (in avanti è -Z) verrà visualizzato davanti all'utente quando l'app viene avviata.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *InputTracking*

Per un puro **esperienza solo orientamento** , ad esempio un visualizzatore di video a 360 gradi (in cui gli aggiornamenti di head posizionali potrebbero danneggiare la l'illusione), è quindi possibile impostare [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) su true:

```cs
InputTracking.disablePositionalTracking = true;
```

Per un **esperienza su scala seduto**, per consentire all'utente in un secondo momento centrare di nuovo l'origine seduto, è possibile chiamare il [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) metodo:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creazione di un'esperienza su scala permanente o gradazioni di chat room

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Per un **permanente-scalabilità** oppure **esperienza su scala chat room**, è necessario collocare il contenuto relativo al piano. Meglio il suo floor usando il  **[fase spaziali](coordinate-systems.md#spatial-coordinate-systems)**, che rappresenta l'utente definito a livello di parte intera origine e limiti di spazio facoltativo, configurato durante la prima esecuzione.

Per assicurarsi che funzioni con il sistema di coordinate world floor a livello di Unity, è possibile impostare Unity per il RoomScale rilevamento tipo dello spazio e assicurarsi che il set ha esito positivo:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Se SetTrackingSpaceType restituisce true, Unity è passata relativo sistema di coordinate world per tenere traccia di [fase fotogramma di riferimento](coordinate-systems.md#spatial-coordinate-systems).
* Se SetTrackingSpaceType restituisce false, Unity non è riuscito a passare alla fase frame di riferimento, probabilmente perché l'utente non ha configurato anche un piano nel proprio ambiente. Non è comune, ma può verificarsi se la fase è stata configurata in una stanza diversi e il dispositivo è stato spostato alla chat corrente senza l'utente che configura una nuova fase.

Una volta che l'app imposta correttamente i RoomScale rilevamento tipo dello spazio, contenuto inserito in y = 0 piano verrà visualizzati sul pavimento. L'origine in corrispondenza (0, 0, 0) sarà la posizione specifica nell'ambiente operativo in cui l'utente si durante l'installazione di chat, con -Z che rappresenta la direzione in avanti che riscontrato durante l'installazione.

**Namespace:** *UnityEngine.Experimental.XR*<br>
**Tipo:** *Boundary*

Nel codice di script, è quindi possibile chiamare il metodo TryGetGeometry per l'utente è il tipo UnityEngine.Experimental.XR.Boundary per ottenere un poligono di confine, che specifica un tipo di limite di TrackedArea. Se l'utente ha definito un limite (verrà restituito un elenco di vertici), si saprà già sia sicuro offrire una **esperienza su scala chat room** all'utente, in cui sono inoltre informazioni dettagliate per la scena creare.

Si noti che il sistema esegue il rendering automatico il limite quando l'utente si avvicina. L'app non dovrà utilizzare questo poligono per il rendering del limite se stesso. Tuttavia, è possibile scegliere di disporre gli oggetti di scena usando questo poligono di confine, per garantire che l'utente possa raggiungere fisicamente gli oggetti senza teleporting:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala mondiale

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldAnchor*

Per true **esperienze su scala mondiale** in HoloLens che consentono agli utenti di vagare oltre 5 metri, sarà necessario nuove tecniche oltre a quelli usati per le esperienze su scala chat room. Una tecnica fondamentale userai consiste nel creare un [ancoraggio spaziale](coordinate-systems.md#spatial-anchors) per bloccare un cluster di vntana con precisione in posti del mondo fisico, indipendentemente dal fatto fino a quando l'utente dispone di roaming e quindi [trovare tali vntana nuovamente in un secondo momento le sessioni](coordinate-systems.md#spatial-anchor-persistence).

In Unity, un punto di ancoraggio spaziale viene creato aggiungendo i **WorldAnchor** componente di Unity al GameObject.

### <a name="adding-a-world-anchor"></a>Aggiunta di un punto di ancoraggio del mondo

Per aggiungere un punto di ancoraggio del mondo, chiamare AddComponent<WorldAnchor>() per l'oggetto gioco con la trasformazione che si desidera ancorare nel mondo reale.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

La procedura è terminata. L'oggetto gioco verrà ora ancorata alla posizione corrente nel mondo fisico, è possibile visualizzare le relative coordinate world Unity modificare leggermente nel corso del tempo per verificare che tale allineamento fisico. Uso [persistenza](persistence-in-unity.md) a trovarlo ancorata percorso nuovamente in una sessione di app future.

### <a name="removing-a-world-anchor"></a>Rimozione di un punto di ancoraggio del mondo

Se desidera che gli elementi GameObject bloccato in una posizione del mondo fisico e non prevede sullo spostamento di questo frame, è possibile chiamare semplicemente Destroy sul componente World ancoraggio.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Se si desidera spostare gli elementi GameObject questo frame, è necessario chiamare invece DestroyImmediate.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Lo spostamento di un mondo ancorata GameObject

GameObject non è possibile spostare un punto di ancoraggio World posizionato su di esso. Se è necessario spostare gli elementi GameObject questo frame, è necessario:
1. Il componente World ancoraggio DestroyImmediate
2. Spostare gli elementi GameObject
3. Aggiungere un nuovo componente World ancoraggio per gli elementi GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Gestione delle modifiche Locatability

Un WorldAnchor potrebbe non essere individuabili nel mondo fisico a un punto nel tempo. In tal caso, Unity non aggiornerà la trasformazione dell'oggetto ancorato. Questo inoltre può cambiare durante l'esecuzione di un'app. L'incapacità di gestire la modifica in locatability causerà l'oggetto non viene visualizzato nella posizione corretta nel mondo fisica.

Per ricevere una notifica sulle modifiche locatability:
1. Sottoscrivere l'evento OnTrackingChanged
2. Gestire l'evento

Il **OnTrackingChanged** eventi verranno chiamato ogni volta che il punto di ancoraggio spaziale sottostante viene modificato tra uno stato di essere individuabili e non è individuabile.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Gestire l'evento:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

In alcuni casi gli ancoraggi si trovano immediatamente. In questo caso, isLocated dell'ancoraggio sarà essere impostata su true quando AddComponent<WorldAnchor>() restituisce. Di conseguenza, l'evento OnTrackingChanged non verrà attivata. Un modello pulito, è possibile chiamare il gestore OnTrackingChanged con lo stato IsLocated iniziale dopo aver collegato un ancoraggio.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Condivisione Anchor tra i dispositivi

È possibile usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Anchor spaziali Azure</a> per creare un punto di ancoraggio cloud permanenti da un WorldAnchor locale, che consente quindi di individuare l'app in più HoloLens, dispositivi iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto sottoposto a rendering relativo tale ancoraggio nella stessa posizione fisica.  Ciò consente esperienze condivise in tempo reale.

Per iniziare a creare esperienze condivise in Unity, provare i 5 minuti <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive di Azure spaziali Anchor Unity</a>.

Quando si è in esecuzione con Azure Anchor spaziale, è possibile quindi <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare gli ancoraggi in Unity</a>.

## <a name="see-also"></a>Vedere anche
* [Esperienza scale](coordinate-systems.md#mixed-reality-experience-scales)
* [Fase spaziali](coordinate-systems.md#stage-frame-of-reference)
* [Perdita di rilevamento in Unity](tracking-loss-in-unity.md)
* [Ancoraggi spaziali](spatial-anchors.md)
* [Persistenza in Unity](persistence-in-unity.md)
* [Esperienze condivise in Unity](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Anchor spaziali</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Ancoraggi spaziali Azure SDK per Unity</a>