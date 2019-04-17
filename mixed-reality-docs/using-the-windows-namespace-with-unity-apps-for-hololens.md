---
title: Utilizzo dello spazio dei nomi Windows con le app Unity per HoloLens
description: Viene illustrato come usare WinRT APIs nel progetto Unity per HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Procedura dettagliata di Unity, WinRT, windows realtà mista, API,
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599872"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="ea4fa-104">Utilizzo dello spazio dei nomi Windows con le app Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="ea4fa-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="ea4fa-105">Questa pagina descrive come usare WinRT APIs nel progetto Unity per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="ea4fa-106">Includere in modo condizionale le chiamate API WinRT</span><span class="sxs-lookup"><span data-stu-id="ea4fa-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="ea4fa-107">WinRT APIs verrà usato solo nelle compilazioni di progetto Unity destinate a Windows 8, Windows 8.1 o la piattaforma universale di Windows; tutto il codice scritto in script Unity che ha come destinazione APIs WinRT deve essere incluso in modo condizionale per solo tali compilazioni.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-107">WinRT APIs will only be used in Unity project builds that target Windows 8, Windows 8.1, or the Universal Windows Platform; any code that you write in Unity scripts that targets WinRT APIs must be conditionally included for only those builds.</span></span> <span data-ttu-id="ea4fa-108">Questa operazione viene eseguita utilizzando le definizioni del preprocessore NETFX_CORE o WINDOWS_UWP.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-108">This is done using the NETFX_CORE or WINDOWS_UWP preprocessor definitions.</span></span> <span data-ttu-id="ea4fa-109">Questa regola si applica all'utilizzo di istruzioni, nonché altro codice.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-109">This rule applies to using statements, as well as other code.</span></span>

<span data-ttu-id="ea4fa-110">Il frammento di codice seguente è dalla pagina di manuale di Unity per [(Universal Windows Platform): API di WinRT nel C# script](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="ea4fa-110">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="ea4fa-111">In questo esempio, un ID pubblicità viene restituito, ma solo in Windows 8.0 o versione successiva target compilazioni:</span><span class="sxs-lookup"><span data-stu-id="ea4fa-111">In this example, an advertising ID is returned, but only on Windows 8.0 or higher target builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="ea4fa-112">Modificare gli script in un'istanza di Unity C# progetto</span><span class="sxs-lookup"><span data-stu-id="ea4fa-112">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="ea4fa-113">Quando si fa doppio clic su uno script nell'editor di Unity, per impostazione predefinita avvierà lo script in un editor di progetto.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-113">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="ea4fa-114">APIs WinRT risulterà sconosciuta per due motivi: NETFX_CORE non è definito in questo ambiente e il progetto non fa riferimento il Runtime di Windows.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-114">The WinRT APIs will appear to be unknown for two reasons: NETFX_CORE is not defined in this environment, and the project does not reference the Windows Runtime.</span></span> <span data-ttu-id="ea4fa-115">Se si usa la [consiglia di esportazione e compilato le impostazioni](exporting-and-building-a-unity-visual-studio-solution.md)e modificare gli script in tale progetto, invece, verrà definita NETFX_CORE e inoltre includere un riferimento al Runtime di Windows; con questa configurazione posto, WinRT APIs sarà è disponibile per IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-115">If you use the [recommended export and built settings](exporting-and-building-a-unity-visual-studio-solution.md), and edit the scripts in that project instead, it will define NETFX_CORE and also include a reference to the Windows Runtime; with this configuration in place, WinRT APIs will be available for IntelliSense.</span></span>

<span data-ttu-id="ea4fa-116">Si noti che Unity C# progetto consente inoltre di eseguire il debug tramite gli script premendo F5 in Visual Studio di debug remoto.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-116">Note that your Unity C# project can also be used to debug through your scripts using F5 remote debugging in Visual Studio.</span></span> <span data-ttu-id="ea4fa-117">Se non viene visualizzato IntelliSense funziona la prima volta che si apre Unity C# del progetto, chiudere il progetto e aprirlo nuovamente.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-117">If you do not see IntelliSense working the first time that you open your Unity C# project, close the project and re-open it.</span></span> <span data-ttu-id="ea4fa-118">IntelliSense dovrebbe iniziare a lavorare.</span><span class="sxs-lookup"><span data-stu-id="ea4fa-118">IntelliSense should start working.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea4fa-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ea4fa-119">See also</span></span>
* [<span data-ttu-id="ea4fa-120">Esportazione e creazione di una soluzione di Visual Studio a Unity</span><span class="sxs-lookup"><span data-stu-id="ea4fa-120">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
