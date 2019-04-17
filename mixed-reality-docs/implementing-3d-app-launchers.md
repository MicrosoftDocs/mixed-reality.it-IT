---
title: Implementare nelle schermate di avvio app 3D (app UWP)
description: Come creare i logo per le app UWP di realtà mista di Windows e i giochi (distribuite tramite il Microsoft Store) e nelle schermate di avvio app 3D HoloLens e coinvolgenti auricolari (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icona, modellazione, utilità di avvio, 3D dell'utilità di avvio, riquadro, cubo in tempo reale, collegamento diretto, secondarytile, riquadro secondario, piattaforma UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604859"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementare nelle schermate di avvio app 3D (app UWP)

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte del 2017 Fall Creators Update (RS3) per le cuffie coinvolgenti e supportata da HoloLens con Windows 10 April 2018 Update. Assicurarsi che l'applicazione è destinato a una versione di Windows SDK maggiore o uguale a 10.0.16299 su auricolari coinvolgenti e 10.0.17125 su HoloLens. È possibile trovare la versione più recente di Windows SDK [qui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) è il punto iniziale in cui gli utenti ricevuti prima di avviare le applicazioni. Quando si crea un'applicazione UWP per realtà mista di Windows, per impostazione predefinita, le app vengono avviate come 2D Slate con il logo dell'app. Durante lo sviluppo di esperienze per realtà mista di Windows, un'utilità di avvio 3D, facoltativamente, è possibile definire per sostituire l'impostazione predefinita 2D dell'utilità di avvio per l'applicazione. In generale, 3D nelle schermate di avvio sono consigliati per l'avvio di applicazioni coinvolgenti che accettano la realtà mista di Windows home di utenti, mentre l'utilità di avvio predefinito 2D è preferibile quando l'app è attivato sul posto. È anche possibile creare un [collegamento diretto 3D (secondaryTile)](#3d-deep-links-secondarytiles) come un pulsante di visualizzazione 3D per il contenuto all'interno di un'app UWP 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>Processo di creazione dell'utilità di avvio app 3D

Sono previsti 3 passaggi per la creazione di un'utilità di avvio app 3D:
1. [Progettazione e concepting](3d-app-launcher-design-guidance.md)
2. [Modellazione e l'esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. L'integrazione nell'applicazione (questo articolo)

Gli asset 3D da utilizzare come utilità di avvio per l'applicazione deve essere creato usando il [realtà mista di Windows le linee guida di authoring](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per garantire la compatibilità. Gli asset che non soddisfano questa creazione specifica non vengono visualizzati nella home di realtà mista di Windows.

## <a name="configuring-the-3d-launcher"></a>Configurare l'utilità di avvio 3D

Quando crei un nuovo progetto in Visual Studio, viene creato un riquadro predefinito semplice che visualizza il nome e il logo dell'app. Per sostituire questo 2D rappresentazione con un modello 3D personalizzato modificare il manifesto dell'app dell'applicazione per includere l'elemento "MixedRealityModel" come parte della definizione di sezione predefiniti. Per ripristinare il 2D dell'utilità di avvio rimuovere semplicemente la definizione MixedRealityModel dal manifesto.

### <a name="xml"></a>XML

In primo luogo, individuare il manifesto di pacchetto dell'app nel progetto corrente. Per impostazione predefinita, il manifesto verrà denominato package. appxmanifest. Se si usa Visual Studio, quindi fare doppio clic il manifesto nel Visualizzatore di soluzione e selezionare **Visualizza origine** per aprire il codice xml per la modifica. 

Nella parte superiore del manifesto, aggiungere lo schema uap5 e includerlo come uno spazio dei nomi può essere ignorato:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Successivamente, specificare "MixedRealityModel" nel riquadro predefinito per l'applicazione:

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

Gli elementi MixedRealityModel accetta un percorso di file che punta a un asset 3D archiviato nel pacchetto dell'app. Attualmente i modelli 3D solo recapitati utilizzando il formato di file .glb e create in base al [asset 3D di realtà mista di Windows le istruzioni di creazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) sono supportati. Gli asset devono essere archiviati nel pacchetto dell'app e animazione non è attualmente supportata. Se il parametro "Path" viene lasciato vuoto Windows mostrerà lo slate 2D anziché l'utilità di avvio 3D. **Nota:** asset .glb devono essere contrassegnati come "Contenuto" nelle impostazioni di compilazione prima di compilare ed eseguire l'app.


![Selezionare il .glb in Esplora soluzioni e usare la sezione properties per contrassegnarlo come "Contenuto" nelle impostazioni di compilazione](images/buildsetting-content-300px.png)<br>
*Selezionare il .glb in Esplora soluzioni e usare la sezione properties per contrassegnarlo come "Contenuto" nelle impostazioni di compilazione*

### <a name="bounding-box"></a>Rettangolo di selezione

Un rettangolo di selezione è utilizzabile, facoltativamente, aggiungere un'area del buffer aggiuntivi attorno all'oggetto. Il rettangolo di selezione viene specificato usando un punto centrale e quelli che indicano la distanza tra il centro del rettangolo di selezione e bordi lungo ogni asse. Unità per il rettangolo di selezione possono essere mappate a 1 unità = 1 metro. Se non viene fornito un rettangolo quindi uno sarà essere adattato automaticamente al mesh dell'oggetto. Se il rettangolo specificato è inferiore rispetto al modello verrà ridimensionato per adattare il mesh.

Supporto per l'attributo casella delimitazione verrà fornito con l'aggiornamento di Windows RS4 come proprietà sull'elemento MixedRealityModel. Definire innanzitutto un rettangolo nella parte superiore dell'app manifesto aggiungere lo schema uap6 e includerlo come spazi dei nomi può essere ignorato:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Successivamente, nella finestra di MixedRealityModel impostare la proprietà SpatialBoundingBox per definire il rettangolo di selezione: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Con Unity

Quando si lavora con Unity il progetto deve essere creato e aperto in Visual Studio prima di modificare il manifesto dell'App. 

>[!NOTE]
>L'utilità di avvio 3D devono essere ridefinito nel manifesto durante la compilazione e distribuzione di una nuova soluzione di Visual Studio da Unity.

## <a name="3d-deep-links-secondarytiles"></a>Deep 3D collega (secondaryTiles)

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte del 2017 Fall Creators Update (RS3) per le cuffie (VR) coinvolgenti e come parte del mese di aprile 2018 Update (RS4) per HoloLens. Assicurarsi che l'applicazione è destinato a una versione di Windows SDK maggiore o uguale a 10.0.16299 su auricolari (VR) coinvolgenti e 10.0.17125 su HoloLens. È possibile trovare la versione più recente di Windows SDK [qui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>Collegamenti diretti 3D (secondaryTiles) funzionano solo con le app UWP 2D. Tuttavia, è possibile creare un [utilità di avvio app 3D](implementing-3d-app-launchers.md) per avviare un'app esclusiva da casa la realtà mista di Windows.

È possibile migliorare le applicazioni 2D per realtà mista di Windows aggiungendo la possibilità di inserire i modelli 3D dalla propria app nel [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) come collegamenti diretti al contenuto all'interno dell'app 2D, esattamente come [secondario 2D i riquadri](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) nel menu Start di Windows. Ad esempio, è possibile creare photospheres a 360° che collegano direttamente in un'app Visualizzatore foto di 360° o consentire agli utenti di inserire contenuto 3D da una raccolta di asset che viene aperta una pagina di dettagli sull'autore. Questi sono solo un paio di modi per espandere la funzionalità dell'applicazione 2D con contenuto 3D.

### <a name="creating-a-3d-secondarytile"></a>Creazione di una "secondaryTile" 3D

È possibile inserire contenuto 3D dall'applicazione usando "secondaryTiles" definendo un modello di realtà mista al momento della creazione. Vengono creati i modelli di realtà mista che fanno riferimento a un asset 3D nel pacchetto dell'app e, facoltativamente, definendo un rettangolo di selezione. 

> [!NOTE]
> Creazione di "secondaryTiles" da all'interno di una vista esclusiva non è attualmente supportata.

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>Rettangolo di selezione

Un rettangolo di selezione è utilizzabile per aggiungere un'area del buffer aggiuntivi attorno all'oggetto. Il rettangolo di selezione viene specificato usando un punto centrale e quelli che indicano la distanza tra il centro del rettangolo di selezione e bordi lungo ogni asse. Unità per il rettangolo di selezione possono essere mappate a 1 unità = 1 metro. Se non viene fornito un rettangolo quindi uno sarà essere adattato automaticamente al mesh dell'oggetto. Se il rettangolo specificato è inferiore rispetto al modello verrà ridimensionato per adattare il mesh.

### <a name="activation-behavior"></a>Comportamento di attivazione

> [!NOTE]
> Questa funzionalità sarà supportata al momento dell'aggiornamento Windows RS4. Assicurarsi che l'applicazione è destinato a una versione di Windows SDK maggiore o uguale a 10.0.17125 se si prevede di usare questa funzionalità

È possibile definire il comportamento di attivazione per un secondaryTile 3D controllare come reagisce quando viene selezionato un utente. Ciò consente di inserire oggetti 3D in realtà mista principali che sono purley decorativi o informativi. Sono supportati i seguenti tipi di comportamento di attivazione:
1. Default: Quando un utente seleziona il secondaryTile 3D viene attivato l'app
2. None: Quando gli utenti selezionano il 3D in secondaryTile rimangono invariate e l'app non è attivato.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Recupero e l'aggiornamento di un "secondaryTile" esistente

Gli sviluppatori possono ottenere nuovamente un elenco dei relativi riquadri secondari esistenti, che include le proprietà che sono specificati in precedenza. È anche possibile aggiornare le proprietà modificando il valore e chiamando quindi UpdateAsync().

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Verifica che l'utente è in realtà mista di Windows

Collegamenti diretti 3D (secondaryTiles) possono essere creati solo quando viene visualizzata in un visore VR realtà mista di Windows Vista. Quando la visualizzazione non viene visualizzata in un visore VR realtà mista di Windows è consigliabile normalmente questo gestito da nascondere il punto di ingresso o viene visualizzato un messaggio di errore. È possibile verificarlo eseguendo una query [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Notifiche nei riquadri

Notifiche di tipo riquadro attualmente non supportano l'invio di un aggiornamento con un asset 3D. Ciò significa che gli sviluppatori non sarà in grado di eseguire le operazioni seguenti
* Notifiche push
* Polling periodico
* Notifiche pianificate

Per altre informazioni su altro riquadri funzionalità e gli attributi e su come vengono usati per i riquadri 2D vedere le [riquadri per la documentazione di App UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Vedere anche

* [Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un'utilità di avvio app 3D.
* [Linee guida di progettazione di app 3D dell'utilità di avvio](3d-app-launcher-design-guidance.md)
* [Creazione di modelli 3D per l'uso di casa di realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementazione di utilità di avvio app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
* [Esplorazione di realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md)
