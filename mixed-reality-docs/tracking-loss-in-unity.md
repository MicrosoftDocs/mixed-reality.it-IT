---
title: Perdita di rilevamento in Unity
description: Gestione di rilevamento delle perdite all'interno di un'app Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, rilevamento di perdite, rilevamento immagine perdita
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602772"
---
# <a name="tracking-loss-in-unity"></a>Perdita di rilevamento in Unity

Quando il dispositivo non è possibile individuare se stessa nel mondo, l'app si verifichi "perdita di rilevamento". Per impostazione predefinita, Unity sarà sospendere il ciclo di aggiornamento e visualizzare un'immagine iniziale per l'utente. Quando il rilevamento viene recuperato, l'immagine iniziale scompare e rimane il ciclo di aggiornamento continua.

In alternativa, l'utente può gestire manualmente questa transizione annullando la partecipazione dell'impostazione. Tutto il contenuto potrebbe sembrare diventi corpo bloccato durante la perdita di rilevamento se non viene eseguita alcuna operazione per gestirlo.

## <a name="default-handling"></a>La gestione predefinita.

Per impostazione predefinita, il ciclo di aggiornamento dell'app, nonché tutti i messaggi e gli eventi arresterà per la durata della perdita di rilevamento. In quel momento stesso, verrà visualizzata all'utente un'immagine. È possibile personalizzare questa immagine andando su Modifica -> Impostazioni -> Windows Media Player, facendo clic immagine iniziale e l'impostazione dell'immagine di tenere traccia della perdita Holographic.

## <a name="manual-handling"></a>Gestione manuale

Per gestire manualmente la perdita di rilevamento, è necessario passare a **Edit** > **impostazioni del progetto** > **Player**  >   **Scheda Impostazioni di piattaforma Windows Universal** > **immagine iniziale** > **Windows Holographic** e deselezionare l'opzione "nel rilevamento perdite pausa e Mostra immagine ". Dopo questa operazione, è necessario gestire rilevamento delle modifiche con le API specificate di seguito.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldManager*

* World Manager espone un evento per il rilevamento di rilevamento persi/acquisita (*WorldManager.OnPositionalLocatorStateChanged*) e una proprietà per eseguire una query lo stato corrente (*WorldManager.state*)
* Quando lo stato di rilevamento non è attivo, la fotocamera non compariranno da convertire nel mondo virtuale anche quando l'utente viene convertito. Di conseguenza gli oggetti non sono più corrisponderà a qualsiasi posizione fisica e tutti verranno visualizzati corpo bloccato.

Quando si gestisce la registrazione delle modifiche nel proprio è necessario eseguire il polling per la proprietà state ogni frame o un handle di *OnPositionalLocatorStateChanged* evento.

### <a name="polling"></a>Polling

Lo stato più importante è *PositionalLocatorState.Active* che indica che il rilevamento è completamente funzionale. Qualsiasi altro stato comporterà solo i delta rotazionali alla fotocamera principale. Ad esempio: 

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Gestisce l'evento OnPositionalLocatorStateChanged

In alternativa e più semplice, è inoltre possibile sottoscrivere *OnPositionalLocatorStateChanged* per gestire le transizioni di:

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
* [Gestione di rilevamento delle perdite di DirectX](coordinate-systems-in-directx.md#handling-tracking-loss)
