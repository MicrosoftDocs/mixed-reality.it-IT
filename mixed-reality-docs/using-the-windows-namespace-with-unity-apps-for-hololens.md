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
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="7c27f-104">API WinRT con Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="7c27f-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="7c27f-105">Questa pagina descrive come usare le API WinRT nel progetto Unity per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7c27f-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="7c27f-106">API di realtà mista</span><span class="sxs-lookup"><span data-stu-id="7c27f-106">Mixed Reality APIs</span></span>

<span data-ttu-id="7c27f-107">Un subset incentrato sulla realtà mista del Windows SDK è stato reso disponibile in una proiezione compatibile .NET Standard 2,0, che è possibile usare nel progetto senza direttive per il preprocessore.</span><span class="sxs-lookup"><span data-stu-id="7c27f-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="7c27f-108">Sono incluse la maggior parte delle API negli spazi dei nomi Windows. Perception e Windows. UI. input. Spatial e possono espandersi per includere altre API in futuro.</span><span class="sxs-lookup"><span data-stu-id="7c27f-108">This includes most APIs in the Windows.Perception and Windows.UI.Input.Spatial namespaces, and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="7c27f-109">Le API proiettate possono essere usate durante l'esecuzione nell'editor, che consente l'uso della [modalità di riproduzione](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span><span class="sxs-lookup"><span data-stu-id="7c27f-109">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="7c27f-110">Per usare questa proiezione, apportare le modifiche seguenti al progetto:</span><span class="sxs-lookup"><span data-stu-id="7c27f-110">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="7c27f-111">Aggiungere un riferimento al pacchetto NuGet [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) usando [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="7c27f-111">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="7c27f-112">Prefissi i riferimenti allo spazio dei nomi `Windows` con `Microsoft.`:</span><span class="sxs-lookup"><span data-stu-id="7c27f-112">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="7c27f-113">Sostituire i cast puntatore nativi con `FromNativePtr`:</span><span class="sxs-lookup"><span data-stu-id="7c27f-113">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="7c27f-114">Includere in modo condizionale le chiamate all'API WinRT</span><span class="sxs-lookup"><span data-stu-id="7c27f-114">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="7c27f-115">In alternativa, è possibile sfruttare le API WinRT per i progetti Unity creati per il piattaforma UWP (Universal Windows Platform) e la piattaforma Xbox One usando le direttive per il preprocessore; qualsiasi codice scritto negli script Unity destinati alle API WinRT deve essere incluso in modo condizionale solo per le compilazioni.</span><span class="sxs-lookup"><span data-stu-id="7c27f-115">Alternatively, WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="7c27f-116">Questa operazione può essere eseguita con due passaggi in Unity:</span><span class="sxs-lookup"><span data-stu-id="7c27f-116">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="7c27f-117">Il livello di compatibilità API deve essere impostato su **.net 4,6** o **.NET standard 2,0** nelle impostazioni del lettore</span><span class="sxs-lookup"><span data-stu-id="7c27f-117">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="7c27f-118">**Modificare** **le impostazioni del progetto** >  > **Player** > **Configuration** > **livello di compatibilità API** a **.NET 4,6** o **.NET standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="7c27f-118">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="7c27f-119">La direttiva per il preprocessore **ENABLE_WINMD_SUPPORT** deve essere racchiusa tra qualsiasi codice sfruttato in WinRT</span><span class="sxs-lookup"><span data-stu-id="7c27f-119">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="7c27f-120">Il frammento di codice seguente si trova nella pagina manuale di Unity per [piattaforma UWP (Universal Windows Platform) C# : API WinRT negli script](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="7c27f-120">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="7c27f-121">In questo esempio viene restituito un ID pubblicitario, ma solo in UWP e Xbox One viene compilata:</span><span class="sxs-lookup"><span data-stu-id="7c27f-121">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="7c27f-122">Modificare gli script in un progetto C# Unity</span><span class="sxs-lookup"><span data-stu-id="7c27f-122">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="7c27f-123">Quando si fa doppio clic su uno script nell'editor di Unity, viene avviato per impostazione predefinita lo script in un progetto di editor.</span><span class="sxs-lookup"><span data-stu-id="7c27f-123">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="7c27f-124">Le API di WinRT sembreranno sconosciute perché il progetto di Visual Studio non fa riferimento al Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="7c27f-124">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="7c27f-125">Inoltre, la direttiva **ENABLE_WINMD_SUPPORT** non sarà definita e tutti i *#if* codice con wrapper verranno ignorati fino a quando non si compila il progetto in una soluzione UWP di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7c27f-125">Further, the **ENABLE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c27f-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7c27f-126">See also</span></span>
* [<span data-ttu-id="7c27f-127">Esportazione e creazione di una soluzione di Visual Studio Unity</span><span class="sxs-lookup"><span data-stu-id="7c27f-127">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="7c27f-128">Unity support Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="7c27f-128">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
