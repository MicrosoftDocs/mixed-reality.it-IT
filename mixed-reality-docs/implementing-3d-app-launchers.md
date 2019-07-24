---
title: Implementare i lanci di app 3D (app UWP)
description: Come creare programmi di avvio e logo per app 3D per le app e i giochi di UWP di realtà mista di Windows (distribuiti tramite il Microsoft Store), sia su HoloLens che su cuffie immersive (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logo, icona, modellazione, avvio, utilità di avvio 3D, riquadro, cubo attivo, collegamento profondo, SecondaryTile, riquadro secondario, UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516735"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="0f3c9-104">Implementare i lanci di app 3D (app UWP)</span><span class="sxs-lookup"><span data-stu-id="0f3c9-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="0f3c9-105">Questa funzionalità è stata aggiunta come parte di 2017 Fall Creators Update (RS3) per gli auricolari immersivi ed è supportata da HoloLens con l'aggiornamento di Windows 10 aprile 2018.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="0f3c9-106">Assicurarsi che l'applicazione sia destinata a una versione del Windows SDK maggiore o uguale a) 10.0.16299 su auricolari immersivi e 10.0.17125 su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="0f3c9-107">È possibile trovare la Windows SDK più recente [qui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="0f3c9-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="0f3c9-108">La [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) è il punto di partenza in cui gli utenti atterrano prima di avviare le applicazioni.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="0f3c9-109">Quando si crea un'applicazione UWP per la realtà mista di Windows, per impostazione predefinita le app vengono avviate come lavagne 2D con il logo dell'app.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="0f3c9-110">Quando si sviluppano esperienze per la realtà mista di Windows, è possibile definire facoltativamente un utilità di avvio 3D per eseguire l'override dell'utilità di avvio 2D predefinita per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="0f3c9-111">In generale, i programmi di avvio 3D sono consigliati per l'avvio di applicazioni immersive che riportano gli utenti fuori dalla Home realtà mista di Windows, mentre l'utilità di avvio 2D predefinita è preferibile quando l'app viene attivata sul posto.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="0f3c9-112">È anche possibile creare un [collegamento Deep 3D (SecondaryTile)](#3d-deep-links-secondarytiles) come avvio 3D al contenuto all'interno di un'app UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="0f3c9-113">processo di creazione dell'utilità di avvio delle app 3D</span><span class="sxs-lookup"><span data-stu-id="0f3c9-113">3D app launcher creation process</span></span>

<span data-ttu-id="0f3c9-114">Per la creazione di un avvio di app 3D sono necessari tre passaggi:</span><span class="sxs-lookup"><span data-stu-id="0f3c9-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="0f3c9-115">Progettazione e concezione</span><span class="sxs-lookup"><span data-stu-id="0f3c9-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="0f3c9-116">Modellazione ed esportazione</span><span class="sxs-lookup"><span data-stu-id="0f3c9-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="0f3c9-117">Integrazione nell'applicazione (questo articolo)</span><span class="sxs-lookup"><span data-stu-id="0f3c9-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="0f3c9-118">gli asset 3D da usare come avvii per l'applicazione devono essere creati usando le [linee guida](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) per la creazione di realtà miste di Windows per garantire la compatibilità.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="0f3c9-119">Gli asset che non soddisfano questa specifica di authoring non verranno sottoposti a rendering nella Home della realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="0f3c9-120">Configurazione dell'utilità di avvio 3D</span><span class="sxs-lookup"><span data-stu-id="0f3c9-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="0f3c9-121">Quando crei un nuovo progetto in Visual Studio, viene creato un riquadro predefinito semplice che visualizza il nome e il logo dell'app.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="0f3c9-122">Per sostituire questa rappresentazione 2D con un modello 3D personalizzato, modificare il manifesto dell'applicazione per includere l'elemento "MixedRealityModel" come parte della definizione del riquadro predefinito.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="0f3c9-123">Per ripristinare l'utilità di avvio 2D, è sufficiente rimuovere la definizione MixedRealityModel dal manifesto.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="0f3c9-124">XML</span><span class="sxs-lookup"><span data-stu-id="0f3c9-124">XML</span></span>

<span data-ttu-id="0f3c9-125">Per prima cosa, individuare il manifesto del pacchetto dell'applicazione nel progetto corrente.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="0f3c9-126">Per impostazione predefinita, il manifesto verrà denominato Package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="0f3c9-127">Se si usa Visual Studio, fare clic con il pulsante destro del mouse sul manifesto nel Visualizzatore della soluzione e selezionare **Visualizza origine** per aprire il file XML per la modifica.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="0f3c9-128">Nella parte superiore del manifesto aggiungere lo schema uap5 e includerlo come spazio dei nomi ignorabile:</span><span class="sxs-lookup"><span data-stu-id="0f3c9-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="0f3c9-129">Specificare quindi "MixedRealityModel" nel riquadro predefinito per l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="0f3c9-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

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

<span data-ttu-id="0f3c9-130">Gli elementi MixedRealityModel accettano un percorso di file che punta a un asset 3D archiviato nel pacchetto dell'app.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="0f3c9-131">Attualmente sono supportati solo i modelli 3D distribuiti usando il formato di file. glb e creati in base alle [istruzioni per la creazione di asset 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) con la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="0f3c9-132">Gli asset devono essere archiviati nel pacchetto dell'app e l'animazione non è attualmente supportata.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="0f3c9-133">Se il parametro "Path" viene lasciato vuoto, Windows visualizzerà lo Slate 2D anziché l'utilità di avvio 3D.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="0f3c9-134">**Nota:** l'asset. GLB deve essere contrassegnato come "contenuto" nelle impostazioni di compilazione prima di compilare ed eseguire l'app.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="0f3c9-135">![Selezionare il GLB in Esplora soluzioni e usare la sezione proprietà per contrassegnarlo come "contenuto" nelle impostazioni di compilazione](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="0f3c9-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="0f3c9-136">*Selezionare il GLB in Esplora soluzioni e usare la sezione proprietà per contrassegnarlo come "contenuto" nelle impostazioni di compilazione*</span><span class="sxs-lookup"><span data-stu-id="0f3c9-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="0f3c9-137">Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="0f3c9-137">Bounding box</span></span>

<span data-ttu-id="0f3c9-138">Un rettangolo di delimitazione può essere utilizzato per aggiungere facoltativamente un'area del buffer aggiuntiva intorno all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="0f3c9-139">Il rettangolo di delimitazione viene specificato utilizzando un punto centrale e gli extent che indicano la distanza tra il centro del rettangolo di delimitazione e i relativi bordi lungo ogni asse.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="0f3c9-140">È possibile eseguire il mapping delle unità per il rettangolo di delimitazione a 1 unità = 1 contatore.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="0f3c9-141">Se non viene fornito un rettangolo di delimitazione, ne verrà automaticamente inserito uno nella mesh dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="0f3c9-142">Se il rettangolo di delimitazione specificato è inferiore a quello del modello, verrà ridimensionato per adattarsi alla rete.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="0f3c9-143">Il supporto per l'attributo del rettangolo delimitatore verrà con l'aggiornamento di Windows RS4 come proprietà nell'elemento MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="0f3c9-144">Per definire innanzitutto un rettangolo di delimitazione nella parte superiore del manifesto dell'applicazione, aggiungere lo schema uap6 e includerlo come spazi dei nomi ignorabili:</span><span class="sxs-lookup"><span data-stu-id="0f3c9-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="0f3c9-145">Quindi, in MixedRealityModel impostare la proprietà SpatialBoundingBox per definire il rettangolo di delimitazione:</span><span class="sxs-lookup"><span data-stu-id="0f3c9-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="0f3c9-146">Uso di Unity</span><span class="sxs-lookup"><span data-stu-id="0f3c9-146">Using Unity</span></span>

<span data-ttu-id="0f3c9-147">Quando si lavora con Unity, il progetto deve essere compilato e aperto in Visual Studio prima di poter modificare il manifesto dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="0f3c9-148">Quando si compila e si distribuisce una nuova soluzione di Visual Studio da Unity, è necessario ridefinire l'utilità di avvio 3D nel manifesto.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="0f3c9-149">collegamenti profondi 3D (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="0f3c9-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="0f3c9-150">Questa funzionalità è stata aggiunta come parte di 2017 Fall Creators Update (RS3) per auricolari immersivi (VR) e come parte dell'aggiornamento del 2018 aprile (RS4) per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="0f3c9-151">Assicurarsi che l'applicazione sia destinata a una versione del Windows SDK maggiore o uguale a) 10.0.16299 sugli auricolari immersivi (VR) e 10.0.17125 in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="0f3c9-152">È possibile trovare la Windows SDK più recente [qui](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="0f3c9-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="0f3c9-153">i collegamenti profondi 3D (secondaryTiles) funzionano solo con le app UWP 2D.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="0f3c9-154">È tuttavia possibile creare un utilità di [avvio delle app 3D](implementing-3d-app-launchers.md) per avviare un'app esclusiva dalla Home realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="0f3c9-155">Le applicazioni 2D possono essere migliorate per la realtà mista di Windows grazie all'aggiunta della possibilità di inserire modelli 3D dall'app nella [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) come collegamenti profondi ai contenuti all'interno dell'app 2D, proprio come i riquadri [secondari 2D](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) all'avvio di Windows menu.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="0f3c9-156">Ad esempio, è possibile creare fotosfere 360 ° che si collegano direttamente a un'app del Visualizzatore foto di 360 ° o consentire agli utenti di inserire contenuto 3D da una raccolta di asset che apre una pagina di dettagli sull'autore.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="0f3c9-157">Si tratta solo di un paio di modi per espandere la funzionalità dell'applicazione 2D con contenuto 3D.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="0f3c9-158">Creazione di un "secondaryTile" 3D</span><span class="sxs-lookup"><span data-stu-id="0f3c9-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="0f3c9-159">È possibile inserire contenuto 3D dall'applicazione usando "secondaryTiles" definendo un modello di realtà mista al momento della creazione.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="0f3c9-160">I modelli di realtà mista vengono creati facendo riferimento a un asset 3D nel pacchetto dell'app e, facoltativamente, definendo un rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="0f3c9-161">La creazione di "secondaryTiles" dall'interno di una vista esclusiva non è attualmente supportata.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

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

### <a name="bounding-box"></a><span data-ttu-id="0f3c9-162">Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="0f3c9-162">Bounding box</span></span>

<span data-ttu-id="0f3c9-163">È possibile utilizzare un rettangolo di delimitazione per aggiungere un'area del buffer aggiuntiva intorno all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="0f3c9-164">Il rettangolo di delimitazione viene specificato utilizzando un punto centrale e gli extent che indicano la distanza tra il centro del rettangolo di delimitazione e i relativi bordi lungo ogni asse.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="0f3c9-165">È possibile eseguire il mapping delle unità per il rettangolo di delimitazione a 1 unità = 1 contatore.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="0f3c9-166">Se non viene fornito un rettangolo di delimitazione, ne verrà automaticamente inserito uno nella mesh dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="0f3c9-167">Se il rettangolo di delimitazione specificato è inferiore a quello del modello, verrà ridimensionato per adattarsi alla rete.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="0f3c9-168">Comportamento di attivazione</span><span class="sxs-lookup"><span data-stu-id="0f3c9-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="0f3c9-169">Questa funzionalità sarà supportata a partire dall'aggiornamento di Windows RS4.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="0f3c9-170">Se si prevede di usare questa funzionalità, assicurarsi che l'applicazione sia destinata a una versione del Windows SDK maggiore o uguale a 10.0.17125.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="0f3c9-171">È possibile definire il comportamento di attivazione di un secondaryTile 3D per controllare il modo in cui viene reagisce quando viene selezionato da un utente.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="0f3c9-172">Questo può essere usato per inserire gli oggetti 3D nella Home realtà mista che sono Purley informativi o decorativi.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="0f3c9-173">Sono supportati i tipi di comportamento di attivazione seguenti:</span><span class="sxs-lookup"><span data-stu-id="0f3c9-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="0f3c9-174">Valore predefinito: Quando un utente seleziona il secondaryTile 3D, l'app viene attivata</span><span class="sxs-lookup"><span data-stu-id="0f3c9-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="0f3c9-175">None: Quando gli utenti selezionano il secondaryTile 3D non accade nulla e l'app non è attivata.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="0f3c9-176">Acquisizione e aggiornamento di un "secondaryTile" esistente</span><span class="sxs-lookup"><span data-stu-id="0f3c9-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="0f3c9-177">Gli sviluppatori possono ottenere un elenco dei riquadri secondari esistenti, che include le proprietà specificate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="0f3c9-178">Possono anche aggiornare le proprietà modificando il valore e quindi chiamando UpdateAsync ().</span><span class="sxs-lookup"><span data-stu-id="0f3c9-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="0f3c9-179">Verifica per verificare se l'utente si trova in una realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="0f3c9-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="0f3c9-180">i collegamenti profondi 3D (secondaryTiles) possono essere creati solo quando la visualizzazione viene visualizzata in un auricolare di realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="0f3c9-181">Quando la visualizzazione non viene presentata in un headset di realtà mista di Windows, è consigliabile gestirla in modo appropriato nascondendo il punto di ingresso o mostrando un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="0f3c9-182">È possibile eseguire questa verifica eseguendo una query su [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="0f3c9-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="0f3c9-183">Notifiche nei riquadri</span><span class="sxs-lookup"><span data-stu-id="0f3c9-183">Tile notifications</span></span>

<span data-ttu-id="0f3c9-184">Le notifiche dei riquadri attualmente non supportano l'invio di un aggiornamento con un asset 3D.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="0f3c9-185">Ciò significa che gli sviluppatori non saranno in grado di eseguire le operazioni seguenti</span><span class="sxs-lookup"><span data-stu-id="0f3c9-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="0f3c9-186">Notifiche push</span><span class="sxs-lookup"><span data-stu-id="0f3c9-186">Push Notifications</span></span>
* <span data-ttu-id="0f3c9-187">Polling periodico</span><span class="sxs-lookup"><span data-stu-id="0f3c9-187">Periodic Polling</span></span>
* <span data-ttu-id="0f3c9-188">Notifiche pianificate</span><span class="sxs-lookup"><span data-stu-id="0f3c9-188">Scheduled Notifications</span></span>

<span data-ttu-id="0f3c9-189">Per altre informazioni sulle altre funzionalità e gli attributi dei riquadri e sul modo in cui vengono usati per i riquadri 2D, vedere la documentazione relativa ai [riquadri per le app UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="0f3c9-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f3c9-190">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f3c9-190">See also</span></span>

* <span data-ttu-id="0f3c9-191">[Esempio di modello di realtà mista](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contenente un utilità di avvio delle app 3D.</span><span class="sxs-lookup"><span data-stu-id="0f3c9-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="0f3c9-192">Linee guida per la progettazione di utilità di avvio di app 3D</span><span class="sxs-lookup"><span data-stu-id="0f3c9-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="0f3c9-193">Creazione di modelli 3D per l'utilizzo nella Home realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="0f3c9-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="0f3c9-194">Implementazione di lanci di app 3D (app Win32)</span><span class="sxs-lookup"><span data-stu-id="0f3c9-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="0f3c9-195">Esplorazione dello spazio iniziale di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="0f3c9-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
