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
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementare nelle schermate di avvio app 3D (app Win32)

> [!NOTE]
> Questa funzionalità è disponibile solo per i PC che eseguono la versione più recente [Windows Insider](https://insider.windows.com) voli (RS5), la compilazione 17704 e versioni successive.

Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) è il punto iniziale in cui gli utenti ricevuti prima di avviare le applicazioni. Per impostazione predefinita, giochi e App Win32 VR immersivi devono essere avviate all'esterno di visore VR e non sarà più visualizzato nell'elenco "Tutte le app" nel menu Start realtà mista di Windows. Tuttavia, seguendo le istruzioni riportate in questo articolo per implementare un'utilità di avvio app 3D, l'esperienza di Win32 VR immersive può essere avviato da entro il menu Start realtà mista di Windows e l'ambiente domestico.

Questo vale solo per distributied esperienze di Win32 VR immersivi di fuori di Steam. Per usufruire di VR [distribuiti tramite Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), che abbiamo [aggiornata la realtà mista di Windows per la versione SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) insieme il RS5 Insider di Windows più recenti voli in modo che mostra i titoli SteamVR backup in di Windows Menu Start di realtà misto nell'elenco "Tutte le app" automaticamente usando un'utilità di avvio predefinito. In altre parole, il metodo descritto in questo articolo non è necessario per i titoli SteamVR e la realtà mista di Windows per la funzionalità SteamVR Beta eseguirà l'override.

## <a name="3d-app-launcher-creation-process"></a>Processo di creazione dell'utilità di avvio app 3D

Sono previsti 3 passaggi per la creazione di un'utilità di avvio app 3D:
1. [Progettazione e concepting](3d-app-launcher-design-guidance.md)
2. [Modellazione e l'esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. L'integrazione nell'applicazione (questo articolo)

Gli asset 3D da utilizzare come utilità di avvio per l'applicazione deve essere creato usando il [realtà mista di Windows le linee guida di authoring](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per garantire la compatibilità. Gli asset che non soddisfano questa creazione specifica non vengono visualizzati nella home di realtà mista di Windows.

## <a name="configuring-the-3d-launcher"></a>Configurare l'utilità di avvio 3D

Le applicazioni Win32 verranno visualizzata nell'elenco "Tutte le app" nel menu Start realtà mista di Windows se si crea un'utilità di avvio app 3D per loro. A tale scopo, creare un [manifesto Visual elementi](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) file XML che fa riferimento l'utilità di avvio App 3D seguendo questa procedura:

1. Creare un **file GLB asset di utilità di avvio App 3D** (vedere [modellazioni ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Creare un **[manifesto elementi Visual](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** per l'applicazione.
    1. È possibile iniziare con il [esempio riportato di seguito](#sample-visual-elements-manifest).  Visualizzare la versione completa [manifesto Visual elementi](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) informazioni più dettagliate.
    2. Update **Square150x150Logo** e **Square70x70Logo** con PNG o JPG o GIF per l'app.
        * Questi verranno usati per il logo 2D dell'app nell'elenco di App tutti realtà mista Windows e per il Menu Start sul desktop.
        * Il percorso del file è relativo alla cartella che contiene il manifesto di elementi Visual.
        * È comunque necessario fornire un desktop sull'icona del Menu Start per l'app tramite i meccanismi standard. Può essere direttamente nel file eseguibile o il collegamento creato (ad esempio, tramite IShellLink::SetIconLocation).
        * *Facoltativo:* È possibile usare un file resources.pri se si desidera per MRT fornire varie dimensioni di asset per le scale diverse risoluzioni e i temi a contrasto elevato.
    3. Aggiorna il **MixedRealityModel percorso** in modo che punti la GLB per l'utilità di avvio App 3D
    4. Salvare il file con lo stesso nome di file eseguibile, con estensione ". VisualElementsManifest.xml"e salvarlo nella stessa directory. Ad esempio, per il file eseguibile "contoso.exe", il file XML denominato "contoso.visualelementsmanifest.xml".
3. **Aggiungere un collegamento** all'applicazione al Menu Start di Windows desktop. Vedere le [esempio riportato di seguito](#sample-app-launcher-shortcut-creation) per un esempio C++ implementazione. 
    * Crearlo in %ALLUSERSPROFILE%\Microsoft\Windows\Start %SystemDrive%\programdata\microsoft\windows\start Menu\Programmi. (computer) o %APPDATA%\Microsoft\Windows\Start %SystemDrive%\programdata\microsoft\windows\start Menu\Programmi. (utente)
    * Se un aggiornamento viene modificato il manifesto di oggetti visivi o gli asset di cui viene fatto riferimenti da esso, l'aggiornamento o il programma di installazione deve aggiornare il collegamento in modo che il manifesto viene nuovamente analizzato e asset memorizzati nella cache vengono aggiornati.
4. *Facoltativo:* Se il collegamento sul desktop non punta direttamente al file EXE dell'applicazione (ad esempio, se richiama un gestore di protocollo personalizzato, ad esempio "myapp: / /"), nel Menu Start non trovare automaticamente i file VisualElementsManifest.xml dell'app. Per risolvere questo problema, il collegamento deve specificare il percorso del file di manifesto elementi Visual usando System.AppUserModel.VisualElementsManifestHintPath (). Questo può essere impostato il collegamento con le stesse tecniche come System.AppUserModel.ID. Non si deve usare System.AppUserModel.ID ma è possibile eseguire questa operazione se si vuole far corrispondere l'ID modello utente applicazione esplicita dell'applicazione se ne viene usato il collegamento.  Vedere le [creazione del collegamento dell'utilità di avvio app di esempio](#sample-app-launcher-shortcut-creation) sezione di seguito per un C++ esempio.

### <a name="sample-visual-elements-manifest"></a>Manifesto degli elementi visivi di esempio

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

### <a name="sample-app-launcher-shortcut-creation"></a>Creazione del collegamento di utilità di avvio app di esempio

Il codice di esempio seguente viene illustrato come creare un collegamento in C++, incluso il percorso del file XML manifesto Visual di elementi viene sottoposto a override. Si noti che la sostituzione è richiesto solo in casi in cui il collegamento non punta direttamente al file. EXE associato al manifesto (ad es. il collegamento viene utilizzato un gestore di protocollo personalizzato, ad esempio "myapp: / /").

#### <a name="sample-lnk-shortcut-creation-c"></a>Esempio di. La creazione di collegamenti LNK (C++)

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

#### <a name="sample-url-launcher-shortcut"></a>Esempio di. Collegamento all'URL dell'utilità di avvio 

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

## <a name="see-also"></a>Vedere anche

* [Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un'utilità di avvio app 3D.
* [Linee guida di progettazione di app 3D dell'utilità di avvio](3d-app-launcher-design-guidance.md)
* [Creazione di modelli 3D per l'uso di casa di realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementazione di utilità di avvio app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Esplorazione di realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md)
