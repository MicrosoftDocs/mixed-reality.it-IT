---
title: Punto di stato attivo in Unity
description: La modifica manuale di stabilità ologrammi in Unity, impostare il punto di stato attivo
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, il punto di stato attivo, piano messa a fuoco, piano di stabilizzazione, punto di stabilizzazione, reprojection, LSR, buffer di profondità
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604880"
---
# <a name="focus-point-in-unity"></a>Punto di stato attivo in Unity

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo**: *HolographicSettings*

Il [concentrarsi punto](hologram-stability.md#stabilization-plane) insieme per fornire un suggerimento su come eseguire meglio la stabilizzazione nel vntana attualmente HoloLens in corso visualizzabile.

Se si desidera impostare il punto di stato attivo in Unity, è necessario impostare ogni tramite cornice *HolographicSettings.SetFocusPointForFrame()*. Se il punto di attivazione non è impostato per un frame, verrà utilizzato il piano di stabilizzazione di default.

> [!NOTE]
> Per impostazione predefinita, i nuovi progetti di Unity impostare l'opzione "Abilita condivisione Buffer profondità".  Con questa opzione, un'app Unity in esecuzione su un auricolare desktop coinvolgente e concreto o un HoloLens che eseguono Windows 10 April 2018 Update (RS4) o in un secondo momento nel buffer di profondità di Windows per ottimizzare la stabilità di ologramma automaticamente, senza specificare l'app invia una punto di attivazione:
> * In un auricolare desktop coinvolgenti, ciò consentirà reprojection basato su profondità per pixel.
> * In un HoloLens che eseguono Windows 10 April 2018 Update o versione successiva, questo analizzerà il buffer di profondità per scegliere un piano ottimale stabilizzazione automaticamente.
>
> Entrambi gli approcci devono fornire anche una migliore qualità dell'immagine senza lavoro esplicito dall'app per selezionare un punto di stato attivo ogni fotogramma.  Si noti che se si fornisce manualmente un punto di stato attivo, che sostituirà il comportamento automatico descritto in precedenza e in genere ridurrà la stabilità di ologramma.  In generale, è necessario specificare solo un punto di attivazione manuale quando l'app è in esecuzione su un HoloLens che non è ancora stato aggiornato a Windows 10 April 2018 Update.

### <a name="example"></a>Esempio

Esistono diversi modi per impostare il punto di stato attivo, come suggerito dall'overload disponibile nel *SetFocusPointForFrame* funzione statica. Riportati di seguito è riportato un esempio semplice per impostare il piano dello stato attivo per l'oggetto fornito ogni frame:

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

Si noti che il semplice codice sopra riportato potrebbe finire la riduzione di stabilità ologrammi se l'oggetto con lo stato attivo finisce dietro l'utente.  Ecco perché è in genere consigliabile impostare "Consenti condivisione Buffer profondità" anziché specificare manualmente un punto di stato attivo.

### <a name="see-also"></a>Vedere anche
* [Piano di stabilizzazione](hologram-stability.md#stabilization-plane)
