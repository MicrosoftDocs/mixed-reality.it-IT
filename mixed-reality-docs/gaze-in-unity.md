---
title: Estasiati Unity
description: Sguardo è un modo primario per gli utenti come destinazione il vntana che consente di creare l'app nella realtà mista.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: estasiati, unity, ologrammi, realtà mista
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453716"
---
# <a name="head-gaze-in-unity"></a>Head estasiati Unity

[Estasiati](gaze.md) è un modo per gli utenti come destinazione primario di [vntana](hologram.md) consente di creare l'app nel [realtà mista](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementazione sguardo head

Concettualmente [estasiati](gaze.md) viene implementato proiettando un raggio dall'inizio dell'utente in cui le cuffie, nella direzione avanti sono affiancate e determinare quali che ray è in conflitto con. In Unity, posizione principale dell'utente e la direzione sono esposte tramite l'oggetto principale di Unity [fotocamera](camera-in-unity.md), in particolare [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

La chiamata [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) comporta un' [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) struttura che contiene informazioni relative la collisione tra cui il punto 3D in cui si è verificato conflitto e gli altri elementi GameObject raggio sguardo sono in contrasto con.

### <a name="example-implement-head-gaze"></a>Esempio: Implementare sguardo head

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

Mentre l'esempio precedente illustra come eseguire un singolo raycast in un ciclo di aggiornamento per trovare la destinazione sguardo, è consigliabile eseguire questa operazione in un singolo oggetto sguardo invece di eseguire questa operazione in qualsiasi oggetto che è potenzialmente interessato l'oggetto in corso gazed nella gestione. In questo modo l'app Salva l'elaborazione in questo modo un solo sguardo raycast ogni fotogramma.

## <a name="visualizing-gaze"></a>Visualizzazione sguardo

Esattamente come sul desktop in cui è usare il puntatore del mouse di destinazione e interagire con il contenuto, è necessario implementare una [cursore](cursors.md) che rappresenta sguardo dell'utente. In questo modo la fiducia degli utenti sugli aspetti che stanno per interagirvi.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Realtà mista estasiati Toolkit v2
È possibile accedere a sguardo dal [Manager di input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) MRTK v2.

## <a name="see-also"></a>Vedere anche
* [Fotocamera](camera-in-unity.md)
* [Input sguardo](gaze.md)
* [Cursori](cursors.md)
* [Selezione della destinazione con lo sguardo](gaze-targeting.md)
