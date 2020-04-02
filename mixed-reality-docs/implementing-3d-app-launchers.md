---
title: Implementare i lanci di app 3D (app UWP)
description: Come creare programmi di avvio e logo per app 3D per le app e i giochi di UWP di realtà mista di Windows (distribuiti tramite il Microsoft Store), sia su HoloLens che su cuffie immersive (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icona, modellazione, avvio, utilità di avvio 3D, riquadro, cubo attivo, collegamento profondo, SecondaryTile, riquadro secondario, UWP
ms.openlocfilehash: 0a2e2177ffa7e381c461a58f373c818c9c5e72c4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549385"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementare i lanci di app 3D (app UWP)

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte di 2017 Fall Creators Update (RS3) per gli auricolari immersivi ed è supportata da HoloLens con l'aggiornamento di Windows 10 aprile 2018. Assicurarsi che l'applicazione sia destinata a una versione del Windows SDK maggiore o uguale a) 10.0.16299 su auricolari immersivi e 10.0.17125 su HoloLens. È possibile trovare la Windows SDK più recente [qui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

La [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) è il punto di partenza in cui gli utenti atterrano prima di avviare le applicazioni. Quando si crea un'applicazione UWP per la realtà mista di Windows, per impostazione predefinita le app vengono avviate come lavagne 2D con il logo dell'app. Quando si sviluppano esperienze per la realtà mista di Windows, è possibile definire facoltativamente un utilità di avvio 3D per eseguire l'override dell'utilità di avvio 2D predefinita per l'applicazione. In generale, i programmi di avvio 3D sono consigliati per l'avvio di applicazioni immersive che riportano gli utenti fuori dalla Home realtà mista di Windows, mentre l'utilità di avvio 2D predefinita è preferibile quando l'app viene attivata sul posto. È anche possibile creare un [collegamento Deep 3D (SecondaryTile)](#3d-deep-links-secondarytiles) come avvio 3D al contenuto all'interno di un'app UWP 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>processo di creazione dell'utilità di avvio delle app 3D

Per la creazione di un avvio di app 3D sono necessari tre passaggi:
1. [Progettazione e concezione](3d-app-launcher-design-guidance.md)
2. [Modellazione ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrazione nell'applicazione (questo articolo)

gli asset 3D da usare come avvii per l'applicazione devono essere creati usando le [linee guida per la creazione di realtà miste di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per garantire la compatibilità. Gli asset che non soddisfano questa specifica di authoring non verranno sottoposti a rendering nella Home della realtà mista di Windows.

## <a name="configuring-the-3d-launcher"></a>Configurazione dell'utilità di avvio 3D

Quando crei un nuovo progetto in Visual Studio, viene creato un riquadro predefinito semplice che visualizza il nome e il logo dell'app. Per sostituire questa rappresentazione 2D con un modello 3D personalizzato, modificare il manifesto dell'applicazione per includere l'elemento "MixedRealityModel" come parte della definizione del riquadro predefinito. Per ripristinare l'utilità di avvio 2D, è sufficiente rimuovere la definizione MixedRealityModel dal manifesto.

### <a name="xml"></a>XML

Per prima cosa, individuare il manifesto del pacchetto dell'applicazione nel progetto corrente. Per impostazione predefinita, il manifesto verrà denominato Package. appxmanifest. Se si usa Visual Studio, fare clic con il pulsante destro del mouse sul manifesto nel Visualizzatore della soluzione e selezionare **Visualizza origine** per aprire il file XML per la modifica. 

Nella parte superiore del manifesto aggiungere lo schema uap5 e includerlo come spazio dei nomi ignorabile:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Specificare quindi "MixedRealityModel" nel riquadro predefinito per l'applicazione:

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

Gli elementi MixedRealityModel accettano un percorso di file che punta a un asset 3D archiviato nel pacchetto dell'app. Attualmente sono supportati solo i modelli 3D distribuiti usando il formato di file. glb e creati in base alle [istruzioni per la creazione di asset 3D con la realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) . Gli asset devono essere archiviati nel pacchetto dell'app e l'animazione non è attualmente supportata. Se il parametro "Path" viene lasciato vuoto, Windows visualizzerà lo Slate 2D anziché l'utilità di avvio 3D. **Nota:** l'asset. GLB deve essere contrassegnato come "contenuto" nelle impostazioni di compilazione prima di compilare ed eseguire l'app.


![selezionare il GLB in Esplora soluzioni e usare la sezione proprietà per contrassegnarlo come "contenuto" nelle impostazioni di compilazione](images/buildsetting-content-300px.png)<br>
*Selezionare il GLB in Esplora soluzioni e usare la sezione proprietà per contrassegnarlo come "contenuto" nelle impostazioni di compilazione*

### <a name="bounding-box"></a>Rettangolo di selezione

Un rettangolo di delimitazione può essere utilizzato per aggiungere facoltativamente un'area del buffer aggiuntiva intorno all'oggetto. Il rettangolo di delimitazione viene specificato utilizzando un punto centrale e gli extent che indicano la distanza tra il centro del rettangolo di delimitazione e i relativi bordi lungo ogni asse. È possibile eseguire il mapping delle unità per il rettangolo di delimitazione a 1 unità = 1 contatore. Se non viene fornito un rettangolo di delimitazione, ne verrà automaticamente inserito uno nella mesh dell'oggetto. Se il rettangolo di delimitazione specificato è inferiore a quello del modello, verrà ridimensionato per adattarsi alla rete.

Il supporto per l'attributo del rettangolo delimitatore verrà con l'aggiornamento di Windows RS4 come proprietà nell'elemento MixedRealityModel. Per definire innanzitutto un rettangolo di delimitazione nella parte superiore del manifesto dell'applicazione, aggiungere lo schema uap6 e includerlo come spazi dei nomi ignorabili:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Quindi, in MixedRealityModel impostare la proprietà SpatialBoundingBox per definire il rettangolo di delimitazione: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Uso di Unity

Quando si lavora con Unity, il progetto deve essere compilato e aperto in Visual Studio prima di poter modificare il manifesto dell'applicazione. 

>[!NOTE]
>Quando si compila e si distribuisce una nuova soluzione di Visual Studio da Unity, è necessario ridefinire l'utilità di avvio 3D nel manifesto.

## <a name="3d-deep-links-secondarytiles"></a>collegamenti profondi 3D (secondaryTiles)

> [!NOTE]
> Questa funzionalità è stata aggiunta come parte di 2017 Fall Creators Update (RS3) per auricolari immersivi (VR) e come parte dell'aggiornamento del 2018 aprile (RS4) per HoloLens. Assicurarsi che l'applicazione sia destinata a una versione del Windows SDK maggiore o uguale a) 10.0.16299 sugli auricolari immersivi (VR) e 10.0.17125 in HoloLens. È possibile trovare la Windows SDK più recente [qui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>i collegamenti profondi 3D (secondaryTiles) funzionano solo con le app UWP 2D. È tuttavia possibile creare un utilità di [avvio delle app 3D](implementing-3d-app-launchers.md) per avviare un'app esclusiva dalla Home realtà mista di Windows.

Le applicazioni 2D possono essere migliorate per la realtà mista di Windows aggiungendo la possibilità di inserire modelli 3D dall'app nella [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) come collegamenti profondi al contenuto all'interno dell'app 2D, proprio come i [riquadri secondari 2D](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) nel menu Start di Windows. Ad esempio, è possibile creare fotosfere 360 ° che si collegano direttamente a un'app del Visualizzatore foto di 360 ° o consentire agli utenti di inserire contenuto 3D da una raccolta di asset che apre una pagina di dettagli sull'autore. Si tratta solo di un paio di modi per espandere la funzionalità dell'applicazione 2D con contenuto 3D.

### <a name="creating-a-3d-secondarytile"></a>Creazione di un "secondaryTile" 3D

È possibile inserire contenuto 3D dall'applicazione usando "secondaryTiles" definendo un modello di realtà mista al momento della creazione. I modelli di realtà mista vengono creati facendo riferimento a un asset 3D nel pacchetto dell'app e, facoltativamente, definendo un rettangolo di delimitazione. 

> [!NOTE]
> La creazione di "secondaryTiles" dall'interno di una vista esclusiva non è attualmente supportata.

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

È possibile utilizzare un rettangolo di delimitazione per aggiungere un'area del buffer aggiuntiva intorno all'oggetto. Il rettangolo di delimitazione viene specificato utilizzando un punto centrale e gli extent che indicano la distanza tra il centro del rettangolo di delimitazione e i relativi bordi lungo ogni asse. È possibile eseguire il mapping delle unità per il rettangolo di delimitazione a 1 unità = 1 contatore. Se non viene fornito un rettangolo di delimitazione, ne verrà automaticamente inserito uno nella mesh dell'oggetto. Se il rettangolo di delimitazione specificato è inferiore a quello del modello, verrà ridimensionato per adattarsi alla rete.

### <a name="activation-behavior"></a>Comportamento di attivazione

> [!NOTE]
> Questa funzionalità sarà supportata a partire dall'aggiornamento di Windows RS4. Se si prevede di usare questa funzionalità, assicurarsi che l'applicazione sia destinata a una versione del Windows SDK maggiore o uguale a 10.0.17125.

È possibile definire il comportamento di attivazione di un secondaryTile 3D per controllare il modo in cui viene reagisce quando viene selezionato da un utente. Questo può essere usato per inserire gli oggetti 3D nella Home realtà mista che sono puramente informativi o decorativi. Sono supportati i tipi di comportamento di attivazione seguenti:
1. Impostazione predefinita: quando un utente seleziona il secondaryTile 3D, l'app viene attivata
2. None: se gli utenti selezionano il secondaryTile 3D, l'app non viene attivata.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Acquisizione e aggiornamento di un "secondaryTile" esistente

Gli sviluppatori possono ottenere un elenco dei riquadri secondari esistenti, che include le proprietà specificate in precedenza. Possono anche aggiornare le proprietà modificando il valore e quindi chiamando UpdateAsync ().

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Verifica per verificare se l'utente si trova in una realtà mista di Windows

i collegamenti profondi 3D (secondaryTiles) possono essere creati solo quando la visualizzazione viene visualizzata in un auricolare di realtà mista di Windows. Quando la visualizzazione non viene presentata in un headset di realtà mista di Windows, è consigliabile gestirla in modo appropriato nascondendo il punto di ingresso o mostrando un messaggio di errore. È possibile eseguire questa verifica eseguendo una query su [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Notifiche nei riquadri

Le notifiche dei riquadri attualmente non supportano l'invio di un aggiornamento con un asset 3D. Ciò significa che gli sviluppatori non saranno in grado di eseguire le operazioni seguenti
* Notifiche push
* Polling periodico
* Notifiche pianificate

Per altre informazioni sulle altre funzionalità e gli attributi dei riquadri e sul modo in cui vengono usati per i riquadri 2D, vedere la documentazione relativa ai [riquadri per le app UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Vedere anche

* [Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un utilità di avvio delle app 3D.
* [Linee guida per la progettazione di utilità di avvio di app 3D](3d-app-launcher-design-guidance.md)
* [Creazione di modelli 3D per l'utilizzo nella Home realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementazione di lanci di app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
* [Esplorazione dello spazio iniziale di Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
