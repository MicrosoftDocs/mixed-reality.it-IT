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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="eb227-104">Uso dello spazio dei nomi Windows con le app Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="eb227-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="eb227-105">Questa pagina descrive come usare le API WinRT nel progetto Unity per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="eb227-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="eb227-106">Includere in modo condizionale le chiamate all'API WinRT</span><span class="sxs-lookup"><span data-stu-id="eb227-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="eb227-107">È possibile sfruttare le API WinRT per i progetti Unity creati per la piattaforma piattaforma UWP (Universal Windows Platform) e Xbox One. qualsiasi codice scritto negli script Unity destinati alle API WinRT deve essere incluso in modo condizionale solo per le compilazioni.</span><span class="sxs-lookup"><span data-stu-id="eb227-107">WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="eb227-108">Questa operazione può essere eseguita con due passaggi in Unity:</span><span class="sxs-lookup"><span data-stu-id="eb227-108">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="eb227-109">Il livello di compatibilità API deve essere impostato su **.net 4,6** o **.NET standard 2,0** nelle impostazioni del lettore</span><span class="sxs-lookup"><span data-stu-id="eb227-109">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="eb227-110">**Modificare** >  >    il livello di compatibilità dell'API diconfigurazione > del lettore di impostazioni di progetto in .NET 4,6 o .NET standard 2,0 > </span><span class="sxs-lookup"><span data-stu-id="eb227-110">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="eb227-111">La direttiva per il preprocessore **ENABLE_WINMD_SUPPORT** deve essere racchiusa tra qualsiasi codice sfruttato in WinRT</span><span class="sxs-lookup"><span data-stu-id="eb227-111">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="eb227-112">Il frammento di codice seguente si trova nella pagina manuale [di Unity per piattaforma UWP (Universal Windows Platform): API WinRT negli C# script](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="eb227-112">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="eb227-113">In questo esempio viene restituito un ID pubblicitario, ma solo in UWP e Xbox One viene compilata:</span><span class="sxs-lookup"><span data-stu-id="eb227-113">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="eb227-114">Modificare gli script in un progetto C# Unity</span><span class="sxs-lookup"><span data-stu-id="eb227-114">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="eb227-115">Quando si fa doppio clic su uno script nell'editor di Unity, viene avviato per impostazione predefinita lo script in un progetto di editor.</span><span class="sxs-lookup"><span data-stu-id="eb227-115">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="eb227-116">Le API di WinRT sembreranno sconosciute perché il progetto di Visual Studio non fa riferimento al Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="eb227-116">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="eb227-117">Inoltre, la direttiva **ENALBE_WINMD_SUPPORT** non sarà definita e tutti i *#if* codice di cui è stato eseguito il wrapper verranno ignorati fino a quando non si compila il progetto in una soluzione UWP di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb227-117">Further, the **ENALBE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb227-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eb227-118">See also</span></span>
* [<span data-ttu-id="eb227-119">Esportazione e creazione di una soluzione di Visual Studio Unity</span><span class="sxs-lookup"><span data-stu-id="eb227-119">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="eb227-120">Unity support Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="eb227-120">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)