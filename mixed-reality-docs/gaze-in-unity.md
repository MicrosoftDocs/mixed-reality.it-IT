---
title: Sguardo in Unity
description: Lo sguardo è un modo principale per consentire agli utenti di individuare gli ologrammi creati dall'app in realtà mista.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: sguardo, Unity, ologramma, realtà mista
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453716"
---
# <a name="head-gaze-in-unity"></a>Sguardo a testa in Unity

Lo [sguardo](gaze.md) è un modo principale per consentire agli utenti di individuare gli [ologrammi](hologram.md) creati dall'app in [realtà mista](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementazione dello sguardo a capo

Dal punto di vista concettuale, lo [sguardo](gaze.md) viene implementato proiettando un raggio dalla parte principale dell'utente in cui si trova l'auricolare, nella direzione in avanti che si trovano e determinano la collisione tra i raggi. In Unity, la posizione e la direzione della testa dell'utente vengono esposte tramite la [fotocamera](camera-in-unity.md)principale di Unity, in particolare [UnityEngine. camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. inoltr](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

La chiamata a [Physics. RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) genera una struttura [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) che contiene informazioni sulla collisione, tra cui il punto 3D in cui si è verificata la collisione e l'altro GameObject il raggio di sguardi in collisione con.

### <a name="example-implement-head-gaze"></a>Esempio: Implementare lo sguardo a capo

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>Procedure consigliate

Mentre nell'esempio precedente viene illustrato come eseguire un singolo Raycast in un ciclo di aggiornamento per trovare la destinazione dello sguardo, è consigliabile eseguire questa operazione in un singolo oggetto che gestisce lo sguardo invece di eseguire questa operazione in un oggetto potenzialmente interessato all'oggetto che si sta osservando. Ciò consente all'app di salvare l'elaborazione eseguendo un solo sguardo Raycast ogni frame.

## <a name="visualizing-gaze"></a>Visualizzazione dello sguardo

Proprio come nel desktop in cui si usa un puntatore del mouse per la destinazione e l'interazione con il contenuto, è necessario implementare un [cursore](cursors.md) che rappresenta lo sguardo dell'utente. In questo modo l'utente è in confidenza con l'interazione con.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Sguardo in Mixed Reality toolkit V2
È possibile accedere a sguardi da [Gestione input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK V2.

## <a name="see-also"></a>Vedere anche
* [Fotocamera](camera-in-unity.md)
* [Input sguardo](gaze.md)
* [Cursori](cursors.md)
* [Selezione della destinazione con lo sguardo](gaze-targeting.md)
