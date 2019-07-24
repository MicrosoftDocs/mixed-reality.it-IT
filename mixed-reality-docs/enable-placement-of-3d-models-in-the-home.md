---
title: Abilitare la selezione host dei modelli 3D nella Home page
description: Come inserire modelli 3D dal sito Web o dall'applicazione nella Home realtà mista di Windows
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modello, posizione in casa, luogo, mondo, modellazione, Home realtà mista, Web, app
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829730"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="ad706-104">Abilitare la selezione host dei modelli 3D nella Home realtà mista</span><span class="sxs-lookup"><span data-stu-id="ad706-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="ad706-105">Questa funzionalità è stata aggiunta come parte dell' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md).</span><span class="sxs-lookup"><span data-stu-id="ad706-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="ad706-106">Le versioni precedenti di Windows non sono compatibili con questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="ad706-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="ad706-107">La [Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md) è il punto di partenza in cui gli utenti atterrano prima di avviare le applicazioni.</span><span class="sxs-lookup"><span data-stu-id="ad706-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="ad706-108">In alcuni scenari, le app 2D, ad esempio l'app Olografics, consentono di posizionare i modelli 3D direttamente nella Home realtà mista come decorazioni o per un ulteriore controllo in 3D completo.</span><span class="sxs-lookup"><span data-stu-id="ad706-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="ad706-109">Il *protocollo Aggiungi modello* consente di inviare un modello 3D dal sito Web o dall'applicazione direttamente nella Home realtà mista di Windows, in cui verrà mantenuto come i [lanci di app 3D](3d-app-launcher-design-guidance.md), le app 2D e gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="ad706-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="ad706-110">Se, ad esempio, si sta sviluppando un'applicazione che espone un catalogo di mobili 3D per la progettazione di uno spazio, è possibile usare il *protocollo Aggiungi modello* per consentire agli utenti di collocare i modelli di mobili 3D dal catalogo.</span><span class="sxs-lookup"><span data-stu-id="ad706-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="ad706-111">Una volta inserite in tutto il mondo, gli utenti possono spostare, ridimensionare e rimuovere questi modelli 3D esattamente come altri ologrammi nella Home page.</span><span class="sxs-lookup"><span data-stu-id="ad706-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="ad706-112">Questo articolo fornisce una panoramica dell'implementazione del *protocollo Add Model* in modo da consentire agli utenti di decorare il proprio mondo con oggetti 3D dall'app o dal Web.</span><span class="sxs-lookup"><span data-stu-id="ad706-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="ad706-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="ad706-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ad706-114"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="ad706-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="ad706-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="ad706-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="ad706-116"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="ad706-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ad706-117">Aggiungi protocollo modello</span><span class="sxs-lookup"><span data-stu-id="ad706-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="ad706-118">✔️</span><span class="sxs-lookup"><span data-stu-id="ad706-118">✔️</span></span></td>
        <td><span data-ttu-id="ad706-119">✔️</span><span class="sxs-lookup"><span data-stu-id="ad706-119">✔️</span></span></td>
    </tr>
</table>

## <a name="overview"></a><span data-ttu-id="ad706-120">Panoramica</span><span class="sxs-lookup"><span data-stu-id="ad706-120">Overview</span></span>

<span data-ttu-id="ad706-121">Per abilitare il posizionamento dei modelli 3D nella Home realtà mista di Windows sono necessari due passaggi:</span><span class="sxs-lookup"><span data-stu-id="ad706-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="ad706-122">[Verificare che il modello 3D sia compatibile con la Home realtà mista di Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="ad706-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="ad706-123">Implementare il *protocollo Aggiungi modello* nell'applicazione o nella pagina Web (questo articolo).</span><span class="sxs-lookup"><span data-stu-id="ad706-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="ad706-124">Implementazione del *protocollo Add Model*</span><span class="sxs-lookup"><span data-stu-id="ad706-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="ad706-125">Quando si dispone di un [modello 3D compatibile](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), è possibile implementare il *protocollo Add Model* attivando l'URI seguente da qualsiasi pagina Web o applicazione:</span><span class="sxs-lookup"><span data-stu-id="ad706-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="ad706-126">Se l'URI punta a una risorsa remota, verrà automaticamente scaricato e inserito nella Home page.</span><span class="sxs-lookup"><span data-stu-id="ad706-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="ad706-127">Le risorse locali verranno copiate nella cartella di dati dell'app della Home realtà mista prima di essere inserite nella Home page.</span><span class="sxs-lookup"><span data-stu-id="ad706-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="ad706-128">Si consiglia di progettare un'esperienza per gli scenari in cui l'utente potrebbe eseguire una versione precedente di Windows che non supporta questa funzionalità nascondendo il pulsante o disabilitando l'operazione, se possibile.</span><span class="sxs-lookup"><span data-stu-id="ad706-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="ad706-129">Richiamo del *protocollo Add Model* da un'app piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="ad706-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="ad706-130">Richiamo del *protocollo di aggiunta modello* da una pagina Web:</span><span class="sxs-lookup"><span data-stu-id="ad706-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="ad706-131">Considerazioni per auricolari immersivi (VR)</span><span class="sxs-lookup"><span data-stu-id="ad706-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="ad706-132">Per gli auricolari immersivi (VR), non è necessario che il portale per la realtà mista sia in esecuzione prima di richiamare il *protocollo di aggiunta del modello*.</span><span class="sxs-lookup"><span data-stu-id="ad706-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="ad706-133">In questo caso, il *protocollo Add Model* avvierà il portale di realtà mista e inserirà l'oggetto direttamente nel punto in cui l'auricolare sta cercando una volta arrivati nella Home realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ad706-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="ad706-134">Quando si richiama il *protocollo Aggiungi modello* dal desktop con il portale per la realtà mista già in esecuzione, assicurarsi che l'auricolare sia "sveglio".</span><span class="sxs-lookup"><span data-stu-id="ad706-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="ad706-135">In caso contrario, la selezione host non avrà esito positivo.</span><span class="sxs-lookup"><span data-stu-id="ad706-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="ad706-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ad706-136">See also</span></span>

* [<span data-ttu-id="ad706-137">Creazione di modelli 3D per l'utilizzo nella Home realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="ad706-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="ad706-138">Esplorazione dello spazio iniziale di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ad706-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
