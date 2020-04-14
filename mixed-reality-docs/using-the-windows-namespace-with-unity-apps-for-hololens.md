---
title: API WinRT con Unity per HoloLens
description: Illustra come usare le API WinRT (lo spazio dei nomi Windows) nel progetto Unity per HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, realtà mista di Windows, API, procedura dettagliata
ms.openlocfilehash: 80f950d7571a936e93eb08490ad83dbb34a50b3a
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277989"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>API WinRT con Unity per HoloLens

Questa pagina descrive come usare le API WinRT nel progetto Unity per HoloLens.

## <a name="mixed-reality-apis"></a>API di realtà mista

Un subset incentrato sulla realtà mista del Windows SDK è stato reso disponibile in una proiezione compatibile .NET Standard 2,0, che è possibile usare nel progetto senza direttive per il preprocessore. Sono incluse la maggior parte delle API negli spazi dei nomi Windows. Perception e Windows. UI. input. Spatial e possono espandersi per includere altre API in futuro. Le API proiettate possono essere usate durante l'esecuzione nell'editor, che consente l'uso della [modalità di riproduzione](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode). Per usare questa proiezione, apportare le modifiche seguenti al progetto:

1) Aggiungere un riferimento al pacchetto NuGet [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) usando [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Prefissi i riferimenti allo spazio dei nomi `Windows` con `Microsoft.`:
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Sostituire i cast puntatore nativi con `FromNativePtr`:
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Includere in modo condizionale le chiamate all'API WinRT

In alternativa, è possibile sfruttare le API WinRT per i progetti Unity creati per il piattaforma UWP (Universal Windows Platform) e la piattaforma Xbox One usando le direttive per il preprocessore; qualsiasi codice scritto negli script Unity destinati alle API WinRT deve essere incluso in modo condizionale solo per le compilazioni. 

Questa operazione può essere eseguita con due passaggi in Unity:
1) Il livello di compatibilità API deve essere impostato su **.net 4,6** o **.NET standard 2,0** nelle impostazioni del lettore
    - **Modificare** **le impostazioni del progetto** >  > **Player** > **Configuration** > **livello di compatibilità API** a **.NET 4,6** o **.NET standard 2,0**
2) La direttiva per il preprocessore **ENABLE_WINMD_SUPPORT** deve essere racchiusa tra qualsiasi codice sfruttato in WinRT

Il frammento di codice seguente si trova nella pagina manuale di Unity per [piattaforma UWP (Universal Windows Platform) C# : API WinRT negli script](https://docs.unity3d.com/Manual/windowsstore-scripts.html). In questo esempio viene restituito un ID pubblicitario, ma solo in UWP e Xbox One viene compilata:

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

Quando si fa doppio clic su uno script nell'editor di Unity, viene avviato per impostazione predefinita lo script in un progetto di editor. Le API di WinRT sembreranno sconosciute perché il progetto di Visual Studio non fa riferimento al Windows Runtime. Inoltre, la direttiva **ENABLE_WINMD_SUPPORT** non sarà definita e tutti i *#if* codice con wrapper verranno ignorati fino a quando non si compila il progetto in una soluzione UWP di Visual Studio.

## <a name="see-also"></a>Vedere anche
* [Esportazione e creazione di una soluzione di Visual Studio Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Unity support Windows Runtime](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
