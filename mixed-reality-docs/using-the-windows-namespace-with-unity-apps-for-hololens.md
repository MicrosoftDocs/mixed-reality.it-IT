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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Utilizzo dello spazio dei nomi Windows con le app Unity per HoloLens

Questa pagina descrive come usare WinRT APIs nel progetto Unity per HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Includere in modo condizionale le chiamate API WinRT

WinRT APIs verrà usato solo nelle compilazioni di progetto Unity destinate a Windows 8, Windows 8.1 o la piattaforma universale di Windows; tutto il codice scritto in script Unity che ha come destinazione APIs WinRT deve essere incluso in modo condizionale per solo tali compilazioni. Questa operazione viene eseguita utilizzando le definizioni del preprocessore NETFX_CORE o WINDOWS_UWP. Questa regola si applica all'utilizzo di istruzioni, nonché altro codice.

Il frammento di codice seguente è dalla pagina di manuale di Unity per [(Universal Windows Platform): API di WinRT nel C# script](http://docs.unity3d.com/Manual/windowsstore-scripts.html). In questo esempio, un ID pubblicità viene restituito, ma solo in Windows 8.0 o versione successiva target compilazioni:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Modificare gli script in un'istanza di Unity C# progetto

Quando si fa doppio clic su uno script nell'editor di Unity, per impostazione predefinita avvierà lo script in un editor di progetto. APIs WinRT risulterà sconosciuta per due motivi: NETFX_CORE non è definito in questo ambiente e il progetto non fa riferimento il Runtime di Windows. Se si usa la [consiglia di esportazione e compilato le impostazioni](exporting-and-building-a-unity-visual-studio-solution.md)e modificare gli script in tale progetto, invece, verrà definita NETFX_CORE e inoltre includere un riferimento al Runtime di Windows; con questa configurazione posto, WinRT APIs sarà è disponibile per IntelliSense.

Si noti che Unity C# progetto consente inoltre di eseguire il debug tramite gli script premendo F5 in Visual Studio di debug remoto. Se non viene visualizzato IntelliSense funziona la prima volta che si apre Unity C# del progetto, chiudere il progetto e aprirlo nuovamente. IntelliSense dovrebbe iniziare a lavorare.

## <a name="see-also"></a>Vedere anche
* [Esportazione e creazione di una soluzione di Visual Studio a Unity](exporting-and-building-a-unity-visual-studio-solution.md)
