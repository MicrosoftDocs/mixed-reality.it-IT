---
title: Sguardo in Unity
description: Lo sguardo è un modo principale per consentire agli utenti di individuare gli ologrammi creati dall'app in realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: occhi, sguardi, Unity, ologramma, realtà mista
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435300"
---
# <a name="head-gaze-in-unity"></a>Sguardo da capo in Unity

Lo [sguardo](gaze-and-commit.md) è un modo principale per consentire agli utenti di individuare gli [ologrammi](hologram.md) creati dall'app in [realtà mista](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementazione dell'Head-sguardi

Dal punto di vista concettuale, l' [Head-sguardi](gaze-and-commit.md) viene implementato proiettando un raggio dalla parte iniziale dell'utente in cui si trova l'auricolare, nella direzione in avanti che si trovano e determinano la collisione del raggio. In Unity, la posizione e la direzione della testa dell'utente vengono esposte tramite la [fotocamera](camera-in-unity.md)principale di Unity, in particolare [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. inoltr](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

La chiamata a [Physics. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) genera una struttura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) che contiene informazioni sulla collisione, tra cui il punto 3D in cui si è verificata la collisione e l'altro GameObject del raggio di puntamento.

### <a name="example-implement-head-gaze"></a>Esempio: implementare l'Head-sguardi

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

Mentre l'esempio precedente illustra come eseguire un singolo Raycast in un ciclo di aggiornamento per trovare la destinazione in cui si trovano i puntini dell'utente, è consigliabile eseguire questa operazione in un singolo oggetto che gestisce il testing, invece di eseguire questa operazione in qualsiasi oggetto potenzialmente interessato al oggetto t guardato. In questo modo, l'app consente di salvare l'elaborazione eseguendo solo uno sguardo a capo Raycast ogni frame.

## <a name="visualizing-head-gaze"></a>Visualizzazione dell'Head-sguardi

Proprio come nel desktop in cui si usa un puntatore del mouse per la destinazione e l'interazione con il contenuto, è necessario implementare un [cursore](cursors.md) che rappresenti il capo dell'utente. In questo modo l'utente è in confidenza con l'interazione con.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Head-sguardi nel Toolkit di realtà misto V2
È possibile accedere a Head-sguardi da [Gestione input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK V2.

## <a name="see-also"></a>Vedi anche
* [Fotocamera](camera-in-unity.md)
* [Cursori](cursors.md)
* [Puntamento con la testa e commit](gaze-and-commit.md)
