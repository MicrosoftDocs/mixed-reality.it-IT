---
title: Uso dello spazio dei nomi Windows con le app Unity per HoloLens
description: Illustra come usare le API WinRT nel progetto Unity per HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, realtà mista di Windows, API, procedura dettagliata
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548726"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Uso dello spazio dei nomi Windows con le app Unity per HoloLens

Questa pagina descrive come usare le API WinRT nel progetto Unity per HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Includere in modo condizionale le chiamate all'API WinRT

È possibile sfruttare le API WinRT per i progetti Unity creati per la piattaforma piattaforma UWP (Universal Windows Platform) e Xbox One. qualsiasi codice scritto negli script Unity destinati alle API WinRT deve essere incluso in modo condizionale solo per le compilazioni. 

Questa operazione può essere eseguita con due passaggi in Unity:
1) Il livello di compatibilità API deve essere impostato su **.net 4,6** o **.NET standard 2,0** nelle impostazioni del lettore
    - **Modificare** >  >    il livello di compatibilità dell'API diconfigurazione > del lettore di impostazioni di progetto in .NET 4,6 o .NET standard 2,0 > 
2) La direttiva per il preprocessore **ENABLE_WINMD_SUPPORT** deve essere racchiusa tra qualsiasi codice sfruttato in WinRT

Il frammento di codice seguente si trova nella pagina manuale [di Unity per piattaforma UWP (Universal Windows Platform): API WinRT negli C# script](http://docs.unity3d.com/Manual/windowsstore-scripts.html). In questo esempio viene restituito un ID pubblicitario, ma solo in UWP e Xbox One viene compilata:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Modificare gli script in un progetto C# Unity

Quando si fa doppio clic su uno script nell'editor di Unity, viene avviato per impostazione predefinita lo script in un progetto di editor. Le API di WinRT sembreranno sconosciute perché il progetto di Visual Studio non fa riferimento al Windows Runtime. Inoltre, la direttiva **ENALBE_WINMD_SUPPORT** non sarà definita e tutti i *#if* codice di cui è stato eseguito il wrapper verranno ignorati fino a quando non si compila il progetto in una soluzione UWP di Visual Studio.

## <a name="see-also"></a>Vedere anche
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Unity support Windows Runtime](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)