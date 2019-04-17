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
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="4cac5-104">Implementare nelle schermate di avvio app 3D (app UWP)</span><span class="sxs-lookup"><span data-stu-id="4cac5-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="4cac5-105">Questa funzionalità è stata aggiunta come parte del 2017 Fall Creators Update (RS3) per le cuffie coinvolgenti e supportata da HoloLens con Windows 10 April 2018 Update.</span><span class="sxs-lookup"><span data-stu-id="4cac5-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="4cac5-106">Assicurarsi che l'applicazione è destinato a una versione di Windows SDK maggiore o uguale a 10.0.16299 su auricolari coinvolgenti e 10.0.17125 su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4cac5-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="4cac5-107">È possibile trovare la versione più recente di Windows SDK [qui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="4cac5-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="4cac5-108">Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) è il punto iniziale in cui gli utenti ricevuti prima di avviare le applicazioni.</span><span class="sxs-lookup"><span data-stu-id="4cac5-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="4cac5-109">Quando si crea un'applicazione UWP per realtà mista di Windows, per impostazione predefinita, le app vengono avviate come 2D Slate con il logo dell'app.</span><span class="sxs-lookup"><span data-stu-id="4cac5-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="4cac5-110">Durante lo sviluppo di esperienze per realtà mista di Windows, un'utilità di avvio 3D, facoltativamente, è possibile definire per sostituire l'impostazione predefinita 2D dell'utilità di avvio per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="4cac5-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="4cac5-111">In generale, 3D nelle schermate di avvio sono consigliati per l'avvio di applicazioni coinvolgenti che accettano la realtà mista di Windows home di utenti, mentre l'utilità di avvio predefinito 2D è preferibile quando l'app è attivato sul posto.</span><span class="sxs-lookup"><span data-stu-id="4cac5-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="4cac5-112">È anche possibile creare un [collegamento diretto 3D (secondaryTile)](#3d-deep-links-secondarytiles) come un pulsante di visualizzazione 3D per il contenuto all'interno di un'app UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="4cac5-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="4cac5-113">Processo di creazione dell'utilità di avvio app 3D</span><span class="sxs-lookup"><span data-stu-id="4cac5-113">3D app launcher creation process</span></span>

<span data-ttu-id="4cac5-114">Sono previsti 3 passaggi per la creazione di un'utilità di avvio app 3D:</span><span class="sxs-lookup"><span data-stu-id="4cac5-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="4cac5-115">Progettazione e concepting</span><span class="sxs-lookup"><span data-stu-id="4cac5-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="4cac5-116">Modellazione e l'esportazione</span><span class="sxs-lookup"><span data-stu-id="4cac5-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="4cac5-117">L'integrazione nell'applicazione (questo articolo)</span><span class="sxs-lookup"><span data-stu-id="4cac5-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="4cac5-118">Gli asset 3D da utilizzare come utilità di avvio per l'applicazione deve essere creato usando il [realtà mista di Windows le linee guida di authoring](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per garantire la compatibilità.</span><span class="sxs-lookup"><span data-stu-id="4cac5-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="4cac5-119">Gli asset che non soddisfano questa creazione specifica non vengono visualizzati nella home di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="4cac5-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="4cac5-120">Configurare l'utilità di avvio 3D</span><span class="sxs-lookup"><span data-stu-id="4cac5-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="4cac5-121">Quando crei un nuovo progetto in Visual Studio, viene creato un riquadro predefinito semplice che visualizza il nome e il logo dell'app.</span><span class="sxs-lookup"><span data-stu-id="4cac5-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="4cac5-122">Per sostituire questo 2D rappresentazione con un modello 3D personalizzato modificare il manifesto dell'app dell'applicazione per includere l'elemento "MixedRealityModel" come parte della definizione di sezione predefiniti.</span><span class="sxs-lookup"><span data-stu-id="4cac5-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="4cac5-123">Per ripristinare il 2D dell'utilità di avvio rimuovere semplicemente la definizione MixedRealityModel dal manifesto.</span><span class="sxs-lookup"><span data-stu-id="4cac5-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="4cac5-124">XML</span><span class="sxs-lookup"><span data-stu-id="4cac5-124">XML</span></span>

<span data-ttu-id="4cac5-125">In primo luogo, individuare il manifesto di pacchetto dell'app nel progetto corrente.</span><span class="sxs-lookup"><span data-stu-id="4cac5-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="4cac5-126">Per impostazione predefinita, il manifesto verrà denominato package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="4cac5-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="4cac5-127">Se si usa Visual Studio, quindi fare doppio clic il manifesto nel Visualizzatore di soluzione e selezionare **Visualizza origine** per aprire il codice xml per la modifica.</span><span class="sxs-lookup"><span data-stu-id="4cac5-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="4cac5-128">Nella parte superiore del manifesto, aggiungere lo schema uap5 e includerlo come uno spazio dei nomi può essere ignorato:</span><span class="sxs-lookup"><span data-stu-id="4cac5-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="4cac5-129">Successivamente, specificare "MixedRealityModel" nel riquadro predefinito per l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="4cac5-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

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

<span data-ttu-id="4cac5-130">Gli elementi MixedRealityModel accetta un percorso di file che punta a un asset 3D archiviato nel pacchetto dell'app.</span><span class="sxs-lookup"><span data-stu-id="4cac5-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="4cac5-131">Attualmente i modelli 3D solo recapitati utilizzando il formato di file .glb e create in base al [asset 3D di realtà mista di Windows le istruzioni di creazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) sono supportati.</span><span class="sxs-lookup"><span data-stu-id="4cac5-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="4cac5-132">Gli asset devono essere archiviati nel pacchetto dell'app e animazione non è attualmente supportata.</span><span class="sxs-lookup"><span data-stu-id="4cac5-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="4cac5-133">Se il parametro "Path" viene lasciato vuoto Windows mostrerà lo slate 2D anziché l'utilità di avvio 3D.</span><span class="sxs-lookup"><span data-stu-id="4cac5-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="4cac5-134">**Nota:** asset .glb devono essere contrassegnati come "Contenuto" nelle impostazioni di compilazione prima di compilare ed eseguire l'app.</span><span class="sxs-lookup"><span data-stu-id="4cac5-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="4cac5-135">![Selezionare il .glb in Esplora soluzioni e usare la sezione properties per contrassegnarlo come "Contenuto" nelle impostazioni di compilazione](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="4cac5-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="4cac5-136">*Selezionare il .glb in Esplora soluzioni e usare la sezione properties per contrassegnarlo come "Contenuto" nelle impostazioni di compilazione*</span><span class="sxs-lookup"><span data-stu-id="4cac5-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="4cac5-137">Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="4cac5-137">Bounding box</span></span>

<span data-ttu-id="4cac5-138">Un rettangolo di selezione è utilizzabile, facoltativamente, aggiungere un'area del buffer aggiuntivi attorno all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="4cac5-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="4cac5-139">Il rettangolo di selezione viene specificato usando un punto centrale e quelli che indicano la distanza tra il centro del rettangolo di selezione e bordi lungo ogni asse.</span><span class="sxs-lookup"><span data-stu-id="4cac5-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="4cac5-140">Unità per il rettangolo di selezione possono essere mappate a 1 unità = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="4cac5-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="4cac5-141">Se non viene fornito un rettangolo quindi uno sarà essere adattato automaticamente al mesh dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="4cac5-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="4cac5-142">Se il rettangolo specificato è inferiore rispetto al modello verrà ridimensionato per adattare il mesh.</span><span class="sxs-lookup"><span data-stu-id="4cac5-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="4cac5-143">Supporto per l'attributo casella delimitazione verrà fornito con l'aggiornamento di Windows RS4 come proprietà sull'elemento MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="4cac5-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="4cac5-144">Definire innanzitutto un rettangolo nella parte superiore dell'app manifesto aggiungere lo schema uap6 e includerlo come spazi dei nomi può essere ignorato:</span><span class="sxs-lookup"><span data-stu-id="4cac5-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="4cac5-145">Successivamente, nella finestra di MixedRealityModel impostare la proprietà SpatialBoundingBox per definire il rettangolo di selezione:</span><span class="sxs-lookup"><span data-stu-id="4cac5-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="4cac5-146">Con Unity</span><span class="sxs-lookup"><span data-stu-id="4cac5-146">Using Unity</span></span>

<span data-ttu-id="4cac5-147">Quando si lavora con Unity il progetto deve essere creato e aperto in Visual Studio prima di modificare il manifesto dell'App.</span><span class="sxs-lookup"><span data-stu-id="4cac5-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="4cac5-148">L'utilità di avvio 3D devono essere ridefinito nel manifesto durante la compilazione e distribuzione di una nuova soluzione di Visual Studio da Unity.</span><span class="sxs-lookup"><span data-stu-id="4cac5-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="4cac5-149">Deep 3D collega (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="4cac5-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="4cac5-150">Questa funzionalità è stata aggiunta come parte del 2017 Fall Creators Update (RS3) per le cuffie (VR) coinvolgenti e come parte del mese di aprile 2018 Update (RS4) per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4cac5-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="4cac5-151">Assicurarsi che l'applicazione è destinato a una versione di Windows SDK maggiore o uguale a 10.0.16299 su auricolari (VR) coinvolgenti e 10.0.17125 su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4cac5-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="4cac5-152">È possibile trovare la versione più recente di Windows SDK [qui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="4cac5-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="4cac5-153">Collegamenti diretti 3D (secondaryTiles) funzionano solo con le app UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="4cac5-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="4cac5-154">Tuttavia, è possibile creare un [utilità di avvio app 3D](implementing-3d-app-launchers.md) per avviare un'app esclusiva da casa la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="4cac5-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="4cac5-155">È possibile migliorare le applicazioni 2D per realtà mista di Windows aggiungendo la possibilità di inserire i modelli 3D dalla propria app nel [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) come collegamenti diretti al contenuto all'interno dell'app 2D, esattamente come [secondario 2D i riquadri](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) nel menu Start di Windows.</span><span class="sxs-lookup"><span data-stu-id="4cac5-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="4cac5-156">Ad esempio, è possibile creare photospheres a 360° che collegano direttamente in un'app Visualizzatore foto di 360° o consentire agli utenti di inserire contenuto 3D da una raccolta di asset che viene aperta una pagina di dettagli sull'autore.</span><span class="sxs-lookup"><span data-stu-id="4cac5-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="4cac5-157">Questi sono solo un paio di modi per espandere la funzionalità dell'applicazione 2D con contenuto 3D.</span><span class="sxs-lookup"><span data-stu-id="4cac5-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="4cac5-158">Creazione di una "secondaryTile" 3D</span><span class="sxs-lookup"><span data-stu-id="4cac5-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="4cac5-159">È possibile inserire contenuto 3D dall'applicazione usando "secondaryTiles" definendo un modello di realtà mista al momento della creazione.</span><span class="sxs-lookup"><span data-stu-id="4cac5-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="4cac5-160">Vengono creati i modelli di realtà mista che fanno riferimento a un asset 3D nel pacchetto dell'app e, facoltativamente, definendo un rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="4cac5-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="4cac5-161">Creazione di "secondaryTiles" da all'interno di una vista esclusiva non è attualmente supportata.</span><span class="sxs-lookup"><span data-stu-id="4cac5-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

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

### <a name="bounding-box"></a><span data-ttu-id="4cac5-162">Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="4cac5-162">Bounding box</span></span>

<span data-ttu-id="4cac5-163">Un rettangolo di selezione è utilizzabile per aggiungere un'area del buffer aggiuntivi attorno all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="4cac5-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="4cac5-164">Il rettangolo di selezione viene specificato usando un punto centrale e quelli che indicano la distanza tra il centro del rettangolo di selezione e bordi lungo ogni asse.</span><span class="sxs-lookup"><span data-stu-id="4cac5-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="4cac5-165">Unità per il rettangolo di selezione possono essere mappate a 1 unità = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="4cac5-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="4cac5-166">Se non viene fornito un rettangolo quindi uno sarà essere adattato automaticamente al mesh dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="4cac5-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="4cac5-167">Se il rettangolo specificato è inferiore rispetto al modello verrà ridimensionato per adattare il mesh.</span><span class="sxs-lookup"><span data-stu-id="4cac5-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="4cac5-168">Comportamento di attivazione</span><span class="sxs-lookup"><span data-stu-id="4cac5-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="4cac5-169">Questa funzionalità sarà supportata al momento dell'aggiornamento Windows RS4.</span><span class="sxs-lookup"><span data-stu-id="4cac5-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="4cac5-170">Assicurarsi che l'applicazione è destinato a una versione di Windows SDK maggiore o uguale a 10.0.17125 se si prevede di usare questa funzionalità</span><span class="sxs-lookup"><span data-stu-id="4cac5-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="4cac5-171">È possibile definire il comportamento di attivazione per un secondaryTile 3D controllare come reagisce quando viene selezionato un utente.</span><span class="sxs-lookup"><span data-stu-id="4cac5-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="4cac5-172">Ciò consente di inserire oggetti 3D in realtà mista principali che sono purley decorativi o informativi.</span><span class="sxs-lookup"><span data-stu-id="4cac5-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="4cac5-173">Sono supportati i seguenti tipi di comportamento di attivazione:</span><span class="sxs-lookup"><span data-stu-id="4cac5-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="4cac5-174">Default: Quando un utente seleziona il secondaryTile 3D viene attivato l'app</span><span class="sxs-lookup"><span data-stu-id="4cac5-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="4cac5-175">None: Quando gli utenti selezionano il 3D in secondaryTile rimangono invariate e l'app non è attivato.</span><span class="sxs-lookup"><span data-stu-id="4cac5-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="4cac5-176">Recupero e l'aggiornamento di un "secondaryTile" esistente</span><span class="sxs-lookup"><span data-stu-id="4cac5-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="4cac5-177">Gli sviluppatori possono ottenere nuovamente un elenco dei relativi riquadri secondari esistenti, che include le proprietà che sono specificati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="4cac5-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="4cac5-178">È anche possibile aggiornare le proprietà modificando il valore e chiamando quindi UpdateAsync().</span><span class="sxs-lookup"><span data-stu-id="4cac5-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="4cac5-179">Verifica che l'utente è in realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="4cac5-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="4cac5-180">Collegamenti diretti 3D (secondaryTiles) possono essere creati solo quando viene visualizzata in un visore VR realtà mista di Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="4cac5-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="4cac5-181">Quando la visualizzazione non viene visualizzata in un visore VR realtà mista di Windows è consigliabile normalmente questo gestito da nascondere il punto di ingresso o viene visualizzato un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="4cac5-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="4cac5-182">È possibile verificarlo eseguendo una query [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="4cac5-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="4cac5-183">Notifiche nei riquadri</span><span class="sxs-lookup"><span data-stu-id="4cac5-183">Tile notifications</span></span>

<span data-ttu-id="4cac5-184">Notifiche di tipo riquadro attualmente non supportano l'invio di un aggiornamento con un asset 3D.</span><span class="sxs-lookup"><span data-stu-id="4cac5-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="4cac5-185">Ciò significa che gli sviluppatori non sarà in grado di eseguire le operazioni seguenti</span><span class="sxs-lookup"><span data-stu-id="4cac5-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="4cac5-186">Notifiche push</span><span class="sxs-lookup"><span data-stu-id="4cac5-186">Push Notifications</span></span>
* <span data-ttu-id="4cac5-187">Polling periodico</span><span class="sxs-lookup"><span data-stu-id="4cac5-187">Periodic Polling</span></span>
* <span data-ttu-id="4cac5-188">Notifiche pianificate</span><span class="sxs-lookup"><span data-stu-id="4cac5-188">Scheduled Notifications</span></span>

<span data-ttu-id="4cac5-189">Per altre informazioni su altro riquadri funzionalità e gli attributi e su come vengono usati per i riquadri 2D vedere le [riquadri per la documentazione di App UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="4cac5-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="4cac5-190">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4cac5-190">See also</span></span>

* <span data-ttu-id="4cac5-191">[Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un'utilità di avvio app 3D.</span><span class="sxs-lookup"><span data-stu-id="4cac5-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="4cac5-192">Linee guida di progettazione di app 3D dell'utilità di avvio</span><span class="sxs-lookup"><span data-stu-id="4cac5-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="4cac5-193">Creazione di modelli 3D per l'uso di casa di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="4cac5-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="4cac5-194">Implementazione di utilità di avvio app 3D (app Win32)</span><span class="sxs-lookup"><span data-stu-id="4cac5-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="4cac5-195">Esplorazione di realtà mista di Windows home</span><span class="sxs-lookup"><span data-stu-id="4cac5-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
