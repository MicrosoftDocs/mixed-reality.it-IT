---
title: Estasiati Unity
description: Sguardo è un modo primario per gli utenti come destinazione il vntana che consente di creare l'app nella realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: estasiati, unity, ologrammi, realtà mista
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604800"
---
# <a name="gaze-in-unity"></a>Estasiati Unity

[Estasiati](gaze.md) è un modo per gli utenti come destinazione primario di [vntana](hologram.md) consente di creare l'app nel [realtà mista](mixed-reality.md).

## <a name="implementing-gaze"></a>Implementazione sguardo

Concettualmente [estasiati](gaze.md) viene implementato proiettando un raggio dall'inizio dell'utente in cui le cuffie, nella direzione avanti sono affiancate e determinare quali che ray è in conflitto con. In Unity, posizione principale dell'utente e la direzione sono esposte tramite l'oggetto principale di Unity [fotocamera](camera-in-unity.md), in particolare [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

La chiamata [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) comporta un' [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) struttura che contiene informazioni relative la collisione tra cui il punto 3D in cui si è verificato conflitto e gli altri elementi GameObject raggio sguardo sono in contrasto con.

### <a name="example-implement-gaze"></a>Esempio: Implementare sguardo

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

## <a name="gaze-in-mixed-reality-toolkit"></a>Estasiati nel Toolkit di realtà mista
Quando si importano [MRTK rilasciare pacchetti Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonare il progetto dal [repository di GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), si desidera trovare un nuovo menu 'Toolkit realtà mista' in Unity. Nel menu 'Configura', verrà visualizzato il menu 'Applica misto realtà scena impostazioni'. Quando si fa clic si, rimuove la fotocamera predefinita e aggiunge i componenti fondamentali - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menu MRTK per l'installazione di scena](images/MRTK_Input_Menu.png)<br>
*Menu MRTK per l'installazione di scena*

![Programma di installazione automatica di scena in MRTK](images/MRTK_HowTo_Input1.png)<br>
*Programma di installazione automatica di scena in MRTK*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>Estasiati script correlati nel Toolkit di realtà mista
Toolkit di realtà mista include InputManager prefab [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) e [estasiati stabilizzatore](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs). Sotto [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), è possibile assegnare il cursore personalizzato. Parola chiave default, animata [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) viene assegnato.

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) e [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) viene illustrato come visualizzare lo sguardo utilizzano i cursori.

## <a name="see-also"></a>Vedere anche
* [Fotocamera](camera-in-unity.md)
* [Sguardo](gaze.md)
* [Cursori](cursors.md)
* [Sguardo targeting](gaze-targeting.md)
