---
title: La posizione di modelli 3D nell'ambiente domestico
description: Come inserire i modelli 3D dal sito Web o applicazione in casa la realtà mista di Windows
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, model, sul posto nella home page, sul posto, mondo, modellazione, realtà mista home, web, app
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605020"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="b82d9-104">La posizione di modelli 3D in realtà mista home</span><span class="sxs-lookup"><span data-stu-id="b82d9-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="b82d9-105">Questa funzionalità è stato aggiunto durante la [Windows 10 April 2018 Update](release-notes-april-2018.md).</span><span class="sxs-lookup"><span data-stu-id="b82d9-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="b82d9-106">Le versioni precedenti di Windows non sono compatibili con questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="b82d9-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="b82d9-107">Il [realtà mista di Windows home](navigating-the-windows-mixed-reality-home.md) è il punto iniziale in cui gli utenti ricevuti prima di avviare le applicazioni.</span><span class="sxs-lookup"><span data-stu-id="b82d9-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="b82d9-108">In alcuni scenari, le app 2D (ad esempio, l'app Vntana) la posizione di modelli 3D direttamente nella home page di realtà mista come decorazioni o per un'ulteriore l'ispezione in 3D completo.</span><span class="sxs-lookup"><span data-stu-id="b82d9-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="b82d9-109">Il *Aggiungi modello protocollo* consente di inviare un modello 3D dal sito Web o all'applicazione direttamente nella realtà mista di Windows Home page, dove salverà come [nelle schermate di avvio app 3D](3d-app-launcher-design-guidance.md), App 2D e vntana.</span><span class="sxs-lookup"><span data-stu-id="b82d9-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="b82d9-110">Ad esempio, se si sta sviluppando un'applicazione che espone un catalogo di 3D arredamento per la progettazione di uno spazio, è possibile usare la *Aggiungi modello protocollo* per consentire agli utenti di inserire tali modelli 3D mobili dal catalogo.</span><span class="sxs-lookup"><span data-stu-id="b82d9-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="b82d9-111">Una volta inseriti nel mondo, gli utenti possono spostare, ridimensionare e rimuovere questi modelli 3D esattamente come altri vntana nella home page.</span><span class="sxs-lookup"><span data-stu-id="b82d9-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="b82d9-112">Questo articolo offre una panoramica dell'implementazione di *aggiungere protocollo del modello* in modo che sia possibile iniziare consentendo agli utenti decorare il mondo con oggetti 3D da app o sul web.</span><span class="sxs-lookup"><span data-stu-id="b82d9-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="b82d9-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="b82d9-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b82d9-114">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="b82d9-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="b82d9-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b82d9-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b82d9-116"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="b82d9-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b82d9-117">Aggiungere il protocollo di modello</span><span class="sxs-lookup"><span data-stu-id="b82d9-117">Add model protocol</span></span></td><td style="text-align: center;"> <span data-ttu-id="b82d9-118">✔️</span><span class="sxs-lookup"><span data-stu-id="b82d9-118">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b82d9-119">✔️</span><span class="sxs-lookup"><span data-stu-id="b82d9-119">✔️</span></span></td>
</tr>
</table>

## <a name="overview"></a><span data-ttu-id="b82d9-120">Panoramica</span><span class="sxs-lookup"><span data-stu-id="b82d9-120">Overview</span></span>

<span data-ttu-id="b82d9-121">Esistono 2 passaggi per abilitare il posizionamento dei modelli 3D in casa la realtà mista di Windows:</span><span class="sxs-lookup"><span data-stu-id="b82d9-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="b82d9-122">[Verificare che il modello 3D è compatibile con la realtà mista di Windows home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="b82d9-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="b82d9-123">Implementare il *Aggiungi modello protocollo* nell'applicazione o pagina Web (questo articolo).</span><span class="sxs-lookup"><span data-stu-id="b82d9-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="b82d9-124">Implementazione di *aggiungere protocollo del modello*</span><span class="sxs-lookup"><span data-stu-id="b82d9-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="b82d9-125">Dopo aver creato un [compatibile con modelli 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), è possibile implementare le *aggiungere protocollo del modello* attivando l'URI seguente da qualsiasi pagina Web o un'applicazione:</span><span class="sxs-lookup"><span data-stu-id="b82d9-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="b82d9-126">Se l'URI punta a una risorsa remota, quindi verrà automaticamente scaricato e inserito nella home page.</span><span class="sxs-lookup"><span data-stu-id="b82d9-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="b82d9-127">Le risorse locali verranno copiate alla cartella di dati di app di realtà mista domestico prima di essere inserito nella home page.</span><span class="sxs-lookup"><span data-stu-id="b82d9-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="b82d9-128">È consigliabile progettare l'esperienza all'account per gli scenari in cui l'utente potrebbe essere in esecuzione una versione precedente di Windows che non supporta questa funzionalità se si nasconde il pulsante o disabilitando, se possibile.</span><span class="sxs-lookup"><span data-stu-id="b82d9-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="b82d9-129">Richiama il *Aggiungi modello protocollo* da un'app Universal Windows Platform:</span><span class="sxs-lookup"><span data-stu-id="b82d9-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="b82d9-130">Richiama il *Aggiungi modello protocollo* da una pagina Web:</span><span class="sxs-lookup"><span data-stu-id="b82d9-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="b82d9-131">Considerazioni per immersive auricolari (VR)</span><span class="sxs-lookup"><span data-stu-id="b82d9-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="b82d9-132">Per immersive auricolari (VR), il portale di realtà mista non dispone sia in esecuzione prima di richiamare il *Aggiungi modello protocollo*.</span><span class="sxs-lookup"><span data-stu-id="b82d9-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="b82d9-133">In questo caso, il *Aggiungi modello protocollo* avvierà il portale di realtà mista e porre l'oggetto direttamente in cui le cuffie necessita di una volta arrivati in realtà mista home.</span><span class="sxs-lookup"><span data-stu-id="b82d9-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="b82d9-134">Quando si richiama il *Aggiungi modello protocollo* dal desktop con il portale di realtà mista è già in esecuzione, assicurarsi che le cuffie sono "attivo".</span><span class="sxs-lookup"><span data-stu-id="b82d9-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="b82d9-135">In caso contrario, la selezione host non riuscirà.</span><span class="sxs-lookup"><span data-stu-id="b82d9-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="b82d9-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b82d9-136">See also</span></span>

* [<span data-ttu-id="b82d9-137">Creazione di modelli 3D per l'uso di casa di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="b82d9-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="b82d9-138">Esplorazione di realtà mista di Windows home</span><span class="sxs-lookup"><span data-stu-id="b82d9-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
