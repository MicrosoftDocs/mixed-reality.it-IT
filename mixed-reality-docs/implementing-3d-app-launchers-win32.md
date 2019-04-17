---
title: Implementare nelle schermate di avvio app 3D (app Win32)
description: Come creare i logo per le app di realtà virtuale Win32 e giochi (distribuite di fuori di Steam) e nelle schermate di avvio app 3D pertanto vengono visualizzati nell'ambiente home page e menu Start realtà mista di Windows.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icona, modellazione, utilità di avvio, 3D dell'utilità di avvio, tile, cubo in tempo reale, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600993"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="49c48-104">Implementare nelle schermate di avvio app 3D (app Win32)</span><span class="sxs-lookup"><span data-stu-id="49c48-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="49c48-105">Questa funzionalità è disponibile solo per i PC che eseguono la versione più recente [Windows Insider](https://insider.windows.com) voli (RS5), la compilazione 17704 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="49c48-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="49c48-106">Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) è il punto iniziale in cui gli utenti ricevuti prima di avviare le applicazioni.</span><span class="sxs-lookup"><span data-stu-id="49c48-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="49c48-107">Per impostazione predefinita, giochi e App Win32 VR immersivi devono essere avviate all'esterno di visore VR e non sarà più visualizzato nell'elenco "Tutte le app" nel menu Start realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="49c48-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="49c48-108">Tuttavia, seguendo le istruzioni riportate in questo articolo per implementare un'utilità di avvio app 3D, l'esperienza di Win32 VR immersive può essere avviato da entro il menu Start realtà mista di Windows e l'ambiente domestico.</span><span class="sxs-lookup"><span data-stu-id="49c48-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="49c48-109">Questo vale solo per distributied esperienze di Win32 VR immersivi di fuori di Steam.</span><span class="sxs-lookup"><span data-stu-id="49c48-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="49c48-110">Per usufruire di VR [distribuiti tramite Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), che abbiamo [aggiornata la realtà mista di Windows per la versione SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) insieme il RS5 Insider di Windows più recenti voli in modo che mostra i titoli SteamVR backup in di Windows Menu Start di realtà misto nell'elenco "Tutte le app" automaticamente usando un'utilità di avvio predefinito.</span><span class="sxs-lookup"><span data-stu-id="49c48-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="49c48-111">In altre parole, il metodo descritto in questo articolo non è necessario per i titoli SteamVR e la realtà mista di Windows per la funzionalità SteamVR Beta eseguirà l'override.</span><span class="sxs-lookup"><span data-stu-id="49c48-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="49c48-112">Processo di creazione dell'utilità di avvio app 3D</span><span class="sxs-lookup"><span data-stu-id="49c48-112">3D app launcher creation process</span></span>

<span data-ttu-id="49c48-113">Sono previsti 3 passaggi per la creazione di un'utilità di avvio app 3D:</span><span class="sxs-lookup"><span data-stu-id="49c48-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="49c48-114">Progettazione e concepting</span><span class="sxs-lookup"><span data-stu-id="49c48-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="49c48-115">Modellazione e l'esportazione</span><span class="sxs-lookup"><span data-stu-id="49c48-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="49c48-116">L'integrazione nell'applicazione (questo articolo)</span><span class="sxs-lookup"><span data-stu-id="49c48-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="49c48-117">Gli asset 3D da utilizzare come utilità di avvio per l'applicazione deve essere creato usando il [realtà mista di Windows le linee guida di authoring](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per garantire la compatibilità.</span><span class="sxs-lookup"><span data-stu-id="49c48-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="49c48-118">Gli asset che non soddisfano questa creazione specifica non vengono visualizzati nella home di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="49c48-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="49c48-119">Configurare l'utilità di avvio 3D</span><span class="sxs-lookup"><span data-stu-id="49c48-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="49c48-120">Le applicazioni Win32 verranno visualizzata nell'elenco "Tutte le app" nel menu Start realtà mista di Windows se si crea un'utilità di avvio app 3D per loro.</span><span class="sxs-lookup"><span data-stu-id="49c48-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="49c48-121">A tale scopo, creare un [manifesto Visual elementi](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) file XML che fa riferimento l'utilità di avvio App 3D seguendo questa procedura:</span><span class="sxs-lookup"><span data-stu-id="49c48-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="49c48-122">Creare un **file GLB asset di utilità di avvio App 3D** (vedere [modellazioni ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="49c48-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="49c48-123">Creare un **[manifesto elementi Visual](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="49c48-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="49c48-124">È possibile iniziare con il [esempio riportato di seguito](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="49c48-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="49c48-125">Visualizzare la versione completa [manifesto Visual elementi](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) informazioni più dettagliate.</span><span class="sxs-lookup"><span data-stu-id="49c48-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="49c48-126">Update **Square150x150Logo** e **Square70x70Logo** con PNG o JPG o GIF per l'app.</span><span class="sxs-lookup"><span data-stu-id="49c48-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="49c48-127">Questi verranno usati per il logo 2D dell'app nell'elenco di App tutti realtà mista Windows e per il Menu Start sul desktop.</span><span class="sxs-lookup"><span data-stu-id="49c48-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="49c48-128">Il percorso del file è relativo alla cartella che contiene il manifesto di elementi Visual.</span><span class="sxs-lookup"><span data-stu-id="49c48-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="49c48-129">È comunque necessario fornire un desktop sull'icona del Menu Start per l'app tramite i meccanismi standard.</span><span class="sxs-lookup"><span data-stu-id="49c48-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="49c48-130">Può essere direttamente nel file eseguibile o il collegamento creato (ad esempio, tramite IShellLink::SetIconLocation).</span><span class="sxs-lookup"><span data-stu-id="49c48-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="49c48-131">*Facoltativo:* È possibile usare un file resources.pri se si desidera per MRT fornire varie dimensioni di asset per le scale diverse risoluzioni e i temi a contrasto elevato.</span><span class="sxs-lookup"><span data-stu-id="49c48-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="49c48-132">Aggiorna il **MixedRealityModel percorso** in modo che punti la GLB per l'utilità di avvio App 3D</span><span class="sxs-lookup"><span data-stu-id="49c48-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="49c48-133">Salvare il file con lo stesso nome di file eseguibile, con estensione ". VisualElementsManifest.xml"e salvarlo nella stessa directory.</span><span class="sxs-lookup"><span data-stu-id="49c48-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="49c48-134">Ad esempio, per il file eseguibile "contoso.exe", il file XML denominato "contoso.visualelementsmanifest.xml".</span><span class="sxs-lookup"><span data-stu-id="49c48-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="49c48-135">**Aggiungere un collegamento** all'applicazione al Menu Start di Windows desktop.</span><span class="sxs-lookup"><span data-stu-id="49c48-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="49c48-136">Vedere le [esempio riportato di seguito](#sample-app-launcher-shortcut-creation) per un esempio C++ implementazione.</span><span class="sxs-lookup"><span data-stu-id="49c48-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="49c48-137">Crearlo in %ALLUSERSPROFILE%\Microsoft\Windows\Start %SystemDrive%\programdata\microsoft\windows\start Menu\Programmi. (computer) o %APPDATA%\Microsoft\Windows\Start %SystemDrive%\programdata\microsoft\windows\start Menu\Programmi. (utente)</span><span class="sxs-lookup"><span data-stu-id="49c48-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="49c48-138">Se un aggiornamento viene modificato il manifesto di oggetti visivi o gli asset di cui viene fatto riferimenti da esso, l'aggiornamento o il programma di installazione deve aggiornare il collegamento in modo che il manifesto viene nuovamente analizzato e asset memorizzati nella cache vengono aggiornati.</span><span class="sxs-lookup"><span data-stu-id="49c48-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="49c48-139">*Facoltativo:* Se il collegamento sul desktop non punta direttamente al file EXE dell'applicazione (ad esempio, se richiama un gestore di protocollo personalizzato, ad esempio "myapp: / /"), nel Menu Start non trovare automaticamente i file VisualElementsManifest.xml dell'app.</span><span class="sxs-lookup"><span data-stu-id="49c48-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="49c48-140">Per risolvere questo problema, il collegamento deve specificare il percorso del file di manifesto elementi Visual usando System.AppUserModel.VisualElementsManifestHintPath ().</span><span class="sxs-lookup"><span data-stu-id="49c48-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="49c48-141">Questo può essere impostato il collegamento con le stesse tecniche come System.AppUserModel.ID.</span><span class="sxs-lookup"><span data-stu-id="49c48-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="49c48-142">Non si deve usare System.AppUserModel.ID ma è possibile eseguire questa operazione se si vuole far corrispondere l'ID modello utente applicazione esplicita dell'applicazione se ne viene usato il collegamento.</span><span class="sxs-lookup"><span data-stu-id="49c48-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="49c48-143">Vedere le [creazione del collegamento dell'utilità di avvio app di esempio](#sample-app-launcher-shortcut-creation) sezione di seguito per un C++ esempio.</span><span class="sxs-lookup"><span data-stu-id="49c48-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="49c48-144">Manifesto degli elementi visivi di esempio</span><span class="sxs-lookup"><span data-stu-id="49c48-144">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="49c48-145">Creazione del collegamento di utilità di avvio app di esempio</span><span class="sxs-lookup"><span data-stu-id="49c48-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="49c48-146">Il codice di esempio seguente viene illustrato come creare un collegamento in C++, incluso il percorso del file XML manifesto Visual di elementi viene sottoposto a override.</span><span class="sxs-lookup"><span data-stu-id="49c48-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="49c48-147">Si noti che la sostituzione è richiesto solo in casi in cui il collegamento non punta direttamente al file. EXE associato al manifesto (ad es.</span><span class="sxs-lookup"><span data-stu-id="49c48-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="49c48-148">il collegamento viene utilizzato un gestore di protocollo personalizzato, ad esempio "myapp: / /").</span><span class="sxs-lookup"><span data-stu-id="49c48-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="49c48-149">Esempio di. La creazione di collegamenti LNK (C++)</span><span class="sxs-lookup"><span data-stu-id="49c48-149">Sample .LNK shortcut creation (C++)</span></span>

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="49c48-150">Esempio di. Collegamento all'URL dell'utilità di avvio</span><span class="sxs-lookup"><span data-stu-id="49c48-150">Sample .URL launcher shortcut</span></span> 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a><span data-ttu-id="49c48-151">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="49c48-151">See also</span></span>

* <span data-ttu-id="49c48-152">[Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un'utilità di avvio app 3D.</span><span class="sxs-lookup"><span data-stu-id="49c48-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="49c48-153">Linee guida di progettazione di app 3D dell'utilità di avvio</span><span class="sxs-lookup"><span data-stu-id="49c48-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="49c48-154">Creazione di modelli 3D per l'uso di casa di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="49c48-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="49c48-155">Implementazione di utilità di avvio app 3D (app UWP)</span><span class="sxs-lookup"><span data-stu-id="49c48-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="49c48-156">Esplorazione di realtà mista di Windows home</span><span class="sxs-lookup"><span data-stu-id="49c48-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
