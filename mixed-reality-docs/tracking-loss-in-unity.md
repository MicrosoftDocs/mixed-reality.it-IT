---
title: Rilevamento della perdita in Unity
description: Gestione della perdita di rilevamento all'interno di un'app Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perdita di rilevamento, immagine della perdita di rilevamento
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548751"
---
# <a name="tracking-loss-in-unity"></a>Rilevamento della perdita in Unity

Quando il dispositivo non è in grado di trovarsi nel mondo, l'app riscontra una "perdita di rilevamento". Per impostazione predefinita, Unity sospende il ciclo di aggiornamento e visualizza un'immagine iniziale per l'utente. Quando il rilevamento viene recuperato, l'immagine iniziale viene interrotta e il ciclo di aggiornamento continua.

In alternativa, l'utente può gestire manualmente questa transizione scegliendo l'impostazione. Se non viene eseguita alcuna operazione per la gestione, tutto il contenuto sembrerà bloccato nel corpo durante la perdita del rilevamento.

## <a name="default-handling"></a>Gestione predefinita

Per impostazione predefinita, il ciclo di aggiornamento dell'app, nonché tutti i messaggi e gli eventi, si arresteranno per la durata della perdita del rilevamento. Allo stesso tempo, all'utente verrà visualizzata un'immagine. È possibile personalizzare questa immagine scegliendo Modifica-> Impostazioni-> Player, facendo clic su immagine iniziale e impostando l'immagine della perdita del rilevamento olografico.

## <a name="manual-handling"></a>Gestione manuale

Per gestire manualmente la perdita del rilevamento, è necessario passare **a modifica** > **Impostazioni** > progetto**lettore** > piattaforma UWP (Universal Windows Platform)**immagine**  > inizialedellaschedaImpostazioni >  **Windows olografico** e deselezionare "on Tracking Loss pause and Show image". Successivamente, è necessario gestire le modifiche di rilevamento con le API specificate di seguito.

**Namespace** *UnityEngine. XR. WSA*<br>
**Tipo** *WorldManager*

* World Manager espone un evento per rilevare il rilevamento perso/acquisito (*WorldManager. OnPositionalLocatorStateChanged*) e una proprietà per eseguire una query sullo stato corrente (*WorldManager. state*)
* Quando lo stato di rilevamento non è attivo, la fotocamera non sembra tradursi nel mondo virtuale, anche quando l'utente si traduce. Ciò significa che gli oggetti non corrisponderanno più a una posizione fisica e tutti verranno visualizzati corpo bloccati.

Quando si gestiscono le modifiche di rilevamento, è necessario eseguire il polling per la proprietà di stato ogni frame o gestire l'evento *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Polling

Lo stato più importante è *PositionalLocatorState. Active* , che significa che il rilevamento è completamente funzionante. Qualsiasi altro stato comporterà solo Delta rotazionali alla fotocamera principale. Ad esempio:

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Gestione dell'evento OnPositionalLocatorStateChanged

In alternativa, è anche possibile eseguire la sottoscrizione a *OnPositionalLocatorStateChanged* per gestire le transizioni:

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>Vedere anche
* [Gestione della perdita di rilevamento in DirectX](coordinate-systems-in-directx.md#handling-tracking-loss)
