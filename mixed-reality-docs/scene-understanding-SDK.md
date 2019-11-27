---
title: Scenario di comprensione dell'SDK
description: Guida alla programmazione per l'SDK di informazioni sulla scena
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, realtà mista di Windows, Unity
ms.openlocfilehash: f365b0444576e03acd8dba194d7f8f24175e7bee
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539517"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="b7238-104">Panoramica dell'SDK per la comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="b7238-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="b7238-105">L'obiettivo della comprensione della scena consiste nel trasformare i dati dei sensori dell'ambiente non strutturati acquisiti dal dispositivo della realtà mista e convertirli in una rappresentazione potente ma astratta che è intuitiva e facile da sviluppare per.</span><span class="sxs-lookup"><span data-stu-id="b7238-105">The goal of Scene understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="b7238-106">L'SDK funge da livello di comunicazione tra l'applicazione e la scena che comprende il Runtime.</span><span class="sxs-lookup"><span data-stu-id="b7238-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="b7238-107">Ha lo scopo di simulare costrutti standard esistenti, ad esempio grafici della scena 3D per le rappresentazioni 3D e rettangoli/pannelli 2D per le applicazioni 2D.</span><span class="sxs-lookup"><span data-stu-id="b7238-107">It's aimed to mimic existing standard constructs such as 3d scene graphs for 3d representations and 2D rectangles/panels for 2d applications.</span></span> <span data-ttu-id="b7238-108">Mentre la scena dei costrutti che comprendono le simulazioni verrà mappata a Framework concreti che è possibile usare, in generale SceneUnderstanding è un Framework agnostico che consente l'interoperabilità tra diversi Framework che interagiscono con esso.</span><span class="sxs-lookup"><span data-stu-id="b7238-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="b7238-109">Poiché la comprensione della scena evolve il ruolo dell'SDK è garantire che le nuove rappresentazioni e funzionalità continuino a essere esposte in un framework unificato.</span><span class="sxs-lookup"><span data-stu-id="b7238-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="b7238-110">In questo documento vengono introdotti i concetti di alto livello che consentiranno di acquisire familiarità con l'ambiente di sviluppo e l'utilizzo e quindi fornire una documentazione più dettagliata per classi e costrutti specifici.</span><span class="sxs-lookup"><span data-stu-id="b7238-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="b7238-111">Dove è possibile ottenere l'SDK?</span><span class="sxs-lookup"><span data-stu-id="b7238-111">Where do I get the SDK?</span></span>

<span data-ttu-id="b7238-112">SceneUnderstanding SDK è scaricabile tramite NuGet.</span><span class="sxs-lookup"><span data-stu-id="b7238-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="b7238-113">SDK di SceneUnderstanding</span><span class="sxs-lookup"><span data-stu-id="b7238-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="b7238-114">**Nota:** la versione più recente dipende dai pacchetti di anteprima ed è necessario abilitare i pacchetti di versioni non definitive per visualizzarli.</span><span class="sxs-lookup"><span data-stu-id="b7238-114">**Note:** the latest release depends on preview packages and you will need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="b7238-115">A partire dalla versione 0.5.2022-RC, la comprensione della scena supporta le C# proiezioni di linguaggio per e C++ consente alle applicazioni di sviluppare applicazioni per piattaforme Win32 o UWP.</span><span class="sxs-lookup"><span data-stu-id="b7238-115">As of version 0.5.2022-rc, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="b7238-116">A partire da questa versione, SceneUnderstanding supporta Unity support in-Editor, bloccando il SceneObserver usato esclusivamente per la comunicazione con HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="b7238-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="b7238-117">SceneUnderstanding richiede Windows SDK versione 18362 o successiva.</span><span class="sxs-lookup"><span data-stu-id="b7238-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="b7238-118">Se si usa l'SDK in un progetto Unity, usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity) per installare il pacchetto nel progetto.</span><span class="sxs-lookup"><span data-stu-id="b7238-118">If you are using the SDK in a Unity project, please use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="b7238-119">Panoramica concettuale</span><span class="sxs-lookup"><span data-stu-id="b7238-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="b7238-120">Scena</span><span class="sxs-lookup"><span data-stu-id="b7238-120">The Scene</span></span>

<span data-ttu-id="b7238-121">Il dispositivo di realtà mista sta integrando costantemente le informazioni relative a ciò che viene visualizzato nell'ambiente in uso.</span><span class="sxs-lookup"><span data-stu-id="b7238-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="b7238-122">La comprensione della scena incanala tutte queste origini dati e produce un'unica astrazione coesiva.</span><span class="sxs-lookup"><span data-stu-id="b7238-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="b7238-123">La comprensione della scena genera scene che sono una composizione di [SceneObjects](scene-understanding-SDK.md#sceneobjects) che rappresenta un'istanza di un singolo elemento, ad esempio una parete/soffitto/piano. Gli oggetti scena stessi sono una composizione di [SceneComponents](scene-understanding-SDK.md#scenecomponents) che rappresentano parti più granulari che compongono questo SceneObject.</span><span class="sxs-lookup"><span data-stu-id="b7238-123">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="b7238-124">Esempi di componenti sono i quad e i mesh, ma in futuro potrebbero rappresentare i riquadri, le mesh di collisione, i metadati e così via.</span><span class="sxs-lookup"><span data-stu-id="b7238-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc...</span></span>

<span data-ttu-id="b7238-125">Il processo di conversione dei dati dei sensori non elaborati in una scena è un'operazione potenzialmente costosa che può richiedere secondi per spazi medi (~ 10x10m) a minuti per spazi di dimensioni molto grandi (~ 50x50m) e pertanto non è un elemento che viene calcolato dal dispositivo senza richiesta dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b7238-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="b7238-126">La generazione della scena viene invece attivata dall'applicazione su richiesta.</span><span class="sxs-lookup"><span data-stu-id="b7238-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="b7238-127">La classe SceneObserver dispone di metodi statici che consentono di calcolare o deserializzare una scena, con cui è possibile enumerare/interagire.</span><span class="sxs-lookup"><span data-stu-id="b7238-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="b7238-128">L'azione "calcolo" viene eseguita su richiesta ed eseguita sulla CPU, ma in un processo separato (il driver della realtà mista).</span><span class="sxs-lookup"><span data-stu-id="b7238-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="b7238-129">Tuttavia, mentre si esegue il calcolo in un altro processo, i dati della scena risultanti vengono archiviati e conservati nell'applicazione nell'oggetto scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="b7238-130">Di seguito è riportato un diagramma che illustra il flusso del processo e Mostra esempi di due applicazioni che si confrontano con la scena Understanding Runtime.</span><span class="sxs-lookup"><span data-stu-id="b7238-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagramma di processo](images/SU-ProcessFlow.png)

<span data-ttu-id="b7238-132">Sul lato sinistro è presente un diagramma del runtime di realtà mista che è sempre attivo e in esecuzione nel proprio processo.</span><span class="sxs-lookup"><span data-stu-id="b7238-132">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="b7238-133">Questo runtime è responsabile dell'esecuzione del rilevamento dei dispositivi, del mapping spaziale e di altre operazioni che la comprensione della scena USA per comprendere e ragionare in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="b7238-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="b7238-134">Sul lato destro del diagramma sono illustrate due applicazioni teoriche che fanno uso della comprensione della scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="b7238-135">La prima interfaccia dell'applicazione con MRTK che usa la scena Understanding SDK internamente, la seconda app calcola e usa due istanze della scena separate.</span><span class="sxs-lookup"><span data-stu-id="b7238-135">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="b7238-136">Tutte e tre le scene in questo diagramma generano istanze distinte delle scene, il driver non rileva lo stato globale condiviso tra le applicazioni e gli oggetti scena in un'unica scena non è presente in un altro.</span><span class="sxs-lookup"><span data-stu-id="b7238-136">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="b7238-137">La comprensione della scena fornisce un meccanismo per tenere traccia nel tempo, ma questa operazione viene eseguita usando l'SDK e il codice che esegue questo rilevamento viene eseguito nell'SDK nel processo dell'app.</span><span class="sxs-lookup"><span data-stu-id="b7238-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="b7238-138">Poiché ogni scena archivia i dati nello spazio di memoria dell'applicazione, si può presupporre che tutte le funzioni dell'oggetto scene o dei dati interni vengano sempre eseguite nel processo dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b7238-138">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="b7238-139">Layout</span><span class="sxs-lookup"><span data-stu-id="b7238-139">Layout</span></span>

<span data-ttu-id="b7238-140">Per lavorare con la comprensione della scena, può essere utile conoscere e comprendere il modo in cui il runtime rappresenta i componenti in modo logico e fisico.</span><span class="sxs-lookup"><span data-stu-id="b7238-140">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="b7238-141">La scena rappresenta i dati con un layout specifico che è stato scelto per essere semplice mantenendo una struttura sottostante flessibile per soddisfare i requisiti futuri senza che siano necessarie revisioni principali.</span><span class="sxs-lookup"><span data-stu-id="b7238-141">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="b7238-142">Questa operazione viene eseguita archiviando tutti i componenti (elementi di base per tutti gli oggetti della scena) in un elenco semplice e definendo la gerarchia e la composizione tramite riferimenti in cui componenti specifici fanno riferimento ad altri.</span><span class="sxs-lookup"><span data-stu-id="b7238-142">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="b7238-143">Di seguito viene presentato un esempio di una struttura sia nel formato flat che nella forma logica.</span><span class="sxs-lookup"><span data-stu-id="b7238-143">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="b7238-144">Layout logico</span><span class="sxs-lookup"><span data-stu-id="b7238-144">Logical Layout</span></span></th><th><span data-ttu-id="b7238-145">Layout fisico</span><span class="sxs-lookup"><span data-stu-id="b7238-145">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="b7238-146">Scena</span><span class="sxs-lookup"><span data-stu-id="b7238-146">Scene</span></span>
  <ul>
  <li><span data-ttu-id="b7238-147">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="b7238-147">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="b7238-148">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="b7238-148">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="b7238-149">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="b7238-149">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="b7238-150">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="b7238-150">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="b7238-151">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="b7238-151">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="b7238-152">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="b7238-152">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="b7238-153">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="b7238-153">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="b7238-154">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="b7238-154">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="b7238-155">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="b7238-155">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="b7238-156">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="b7238-156">SceneObject_1</span></span></li>
  <li><span data-ttu-id="b7238-157">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="b7238-157">SceneObject_2</span></span></li>
  <li><span data-ttu-id="b7238-158">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="b7238-158">SceneObject_3</span></span></li>
  <li><span data-ttu-id="b7238-159">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="b7238-159">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="b7238-160">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="b7238-160">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="b7238-161">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="b7238-161">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="b7238-162">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="b7238-162">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="b7238-163">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="b7238-163">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="b7238-164">In questa illustrazione viene evidenziata la differenza tra il layout fisico e logico della scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-164">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="b7238-165">A sinistra viene visualizzato il layout gerarchico dei dati visualizzati dall'applicazione durante l'enumerazione della scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-165">On the left we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="b7238-166">A destra si noterà che la scena è in realtà costituita da 12 componenti distinti che sono accessibili singolarmente, se necessario.</span><span class="sxs-lookup"><span data-stu-id="b7238-166">On the right we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="b7238-167">Quando si elabora una nuova scena, si prevede che le applicazioni analizzino logicamente questa gerarchia. Tuttavia, durante il rilevamento tra gli aggiornamenti della scena, alcune applicazioni potrebbero essere interessate solo a specifici componenti condivisi tra due scene.</span><span class="sxs-lookup"><span data-stu-id="b7238-167">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="b7238-168">Panoramica delle API</span><span class="sxs-lookup"><span data-stu-id="b7238-168">API overview</span></span>

<span data-ttu-id="b7238-169">Nella sezione seguente viene fornita una panoramica di alto livello dei costrutti nella comprensione della scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-169">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="b7238-170">Leggendo questa sezione si apprenderà a comprendere come vengono rappresentate le scene e quali sono i vari componenti usati per.</span><span class="sxs-lookup"><span data-stu-id="b7238-170">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="b7238-171">La sezione successiva fornirà esempi di codice concreti e dettagli aggiuntivi che verranno descritti in questa panoramica.</span><span class="sxs-lookup"><span data-stu-id="b7238-171">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="b7238-172">Tutti i tipi descritti di seguito si trovano nello spazio dei nomi `Microsoft.MixedReality.SceneUnderstanding`.</span><span class="sxs-lookup"><span data-stu-id="b7238-172">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="b7238-173">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="b7238-173">SceneComponents</span></span>

<span data-ttu-id="b7238-174">Dopo aver compreso il layout logico delle scene, è ora possibile presentare il concetto di SceneComponents e il modo in cui vengono usate per comporre la gerarchia.</span><span class="sxs-lookup"><span data-stu-id="b7238-174">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="b7238-175">SceneComponents sono le scomposizione più granulari in SceneUnderstanding che rappresentano un'unica cosa fondamentale, ad esempio una mesh o un quad o un rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="b7238-175">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="b7238-176">SceneComponents sono elementi che possono essere aggiornati in modo indipendente ed è possibile farvi riferimento da altri SceneComponents, di conseguenza hanno un'unica proprietà globale un ID univoco, che consente questo tipo di meccanismo di rilevamento/riferimento.</span><span class="sxs-lookup"><span data-stu-id="b7238-176">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="b7238-177">Gli ID vengono usati per la composizione logica della gerarchia della scena e per la persistenza degli oggetti, ovvero l'operazione di aggiornamento di una scena rispetto a un'altra.</span><span class="sxs-lookup"><span data-stu-id="b7238-177">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="b7238-178">Se si tratta di una nuova scena calcolata come distinta e si esegue semplicemente l'enumerazione di tutti i dati al suo interno, gli ID sono in gran parte trasparenti.</span><span class="sxs-lookup"><span data-stu-id="b7238-178">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="b7238-179">Tuttavia, se si prevede di tenere traccia dei componenti in diversi aggiornamenti, si useranno gli ID per indicizzare e trovare SceneComponents tra gli oggetti scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-179">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="b7238-180">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="b7238-180">SceneObjects</span></span>

<span data-ttu-id="b7238-181">Un SceneObject è un SceneComponent che rappresenta un'istanza di un elemento "Thing", ad esempio un muro, un piano, un soffitto e così via. espressa dalla relativa proprietà Kind.</span><span class="sxs-lookup"><span data-stu-id="b7238-181">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="b7238-182">SceneObjects sono geometriche e quindi hanno funzioni e proprietà che rappresentano la loro posizione nello spazio, ma non contengono alcuna struttura geometrica o logica.</span><span class="sxs-lookup"><span data-stu-id="b7238-182">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="b7238-183">SceneObjects, invece, fanno riferimento ad altri SceneComponents, in particolare SceneQuads e SceneMeshes, che forniscono le varie rappresentazioni supportate dal sistema.</span><span class="sxs-lookup"><span data-stu-id="b7238-183">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="b7238-184">Quando viene calcolata una nuova scena, l'applicazione enumera in modo più probabile la SceneObjects della scena per elaborare gli elementi interessati.</span><span class="sxs-lookup"><span data-stu-id="b7238-184">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="b7238-185">SceneObjects può avere uno dei seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="b7238-185">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="b7238-186">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="b7238-186">SceneObjectKind</span></span></th> <th><span data-ttu-id="b7238-187">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b7238-187">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="b7238-188">Informazioni</span><span class="sxs-lookup"><span data-stu-id="b7238-188">Background</span></span></td><td><span data-ttu-id="b7238-189">Il SceneObject <b>non</b> è noto come uno degli altri tipi di oggetto scena riconosciuti.</span><span class="sxs-lookup"><span data-stu-id="b7238-189">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="b7238-190">Questa classe non deve essere confusa con Unknown, in cui lo sfondo non è a parete/piano/soffitto e così via... mentre Unknown non è ancora stato categorizzato.</span><span class="sxs-lookup"><span data-stu-id="b7238-190">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="b7238-191">Parete</span><span class="sxs-lookup"><span data-stu-id="b7238-191">Wall</span></span></td><td><span data-ttu-id="b7238-192">Una parete fisica.</span><span class="sxs-lookup"><span data-stu-id="b7238-192">A physical wall.</span></span> <span data-ttu-id="b7238-193">Si presuppone che i muri siano strutture ambientali non mobili.</span><span class="sxs-lookup"><span data-stu-id="b7238-193">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="b7238-194">Floor</span><span class="sxs-lookup"><span data-stu-id="b7238-194">Floor</span></span></td><td><span data-ttu-id="b7238-195">I piani sono superfici in cui è possibile spostarsi.</span><span class="sxs-lookup"><span data-stu-id="b7238-195">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="b7238-196">Nota: le scale non sono piani.</span><span class="sxs-lookup"><span data-stu-id="b7238-196">Note: stairs are not floors.</span></span> <span data-ttu-id="b7238-197">Si noti inoltre che le pavimentazioni presuppongono una superficie a cui è possibile spostarsi e pertanto non esiste alcun presupposto esplicito di un pavimento singolare.</span><span class="sxs-lookup"><span data-stu-id="b7238-197">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="b7238-198">Strutture a più livelli, rampe e così via... deve essere classificata come floor.</span><span class="sxs-lookup"><span data-stu-id="b7238-198">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="b7238-199">Ceiling</span><span class="sxs-lookup"><span data-stu-id="b7238-199">Ceiling</span></span></td><td><span data-ttu-id="b7238-200">Superficie superiore di una stanza.</span><span class="sxs-lookup"><span data-stu-id="b7238-200">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="b7238-201">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="b7238-201">Platform</span></span></td><td><span data-ttu-id="b7238-202">Una superficie piana grande su cui posizionare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="b7238-202">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="b7238-203">Che tendono a rappresentare tabelle, piani di ridimensionamento e altre superfici orizzontali di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="b7238-203">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="b7238-204">World</span><span class="sxs-lookup"><span data-stu-id="b7238-204">World</span></span></td><td><span data-ttu-id="b7238-205">Etichetta riservata per i dati geometrici indipendenti dall'assegnazione di etichette.</span><span class="sxs-lookup"><span data-stu-id="b7238-205">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="b7238-206">La mesh generata impostando il flag di aggiornamento EnableWorldMesh verrebbe classificato come World.</span><span class="sxs-lookup"><span data-stu-id="b7238-206">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="b7238-207">Sconosciuta</span><span class="sxs-lookup"><span data-stu-id="b7238-207">Unknown</span></span></td><td><span data-ttu-id="b7238-208">Questo oggetto scena deve ancora essere classificato e assegnato un tipo.</span><span class="sxs-lookup"><span data-stu-id="b7238-208">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="b7238-209">Questa operazione non deve essere confusa con lo sfondo, perché questo oggetto può essere qualsiasi cosa, il sistema non ha ancora una classificazione sufficientemente forte per il sistema.</span><span class="sxs-lookup"><span data-stu-id="b7238-209">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="b7238-210">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="b7238-210">SceneMesh</span></span>

<span data-ttu-id="b7238-211">Un SceneMesh è un SceneComponent che approssima la geometria degli oggetti geometrici arbitrari usando un elenco di triangolo.</span><span class="sxs-lookup"><span data-stu-id="b7238-211">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="b7238-212">SceneMeshes vengono usati in diversi contesti, possono rappresentare i componenti della struttura di celle stagne o come WorldMesh che rappresenta la mesh di mapping spaziale senza limiti associata alla scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-212">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="b7238-213">I dati relativi a indici e vertici forniti con ogni mesh utilizzano lo stesso layout familiare dei [buffer di vertice e di indice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) utilizzati per il rendering di mesh triangolari in tutte le moderne API di rendering.</span><span class="sxs-lookup"><span data-stu-id="b7238-213">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="b7238-214">Si noti che nella comprensione della scena le maglie usano gli indici a 32 bit e potrebbero dover essere suddivise in blocchi per determinati motori di rendering.</span><span class="sxs-lookup"><span data-stu-id="b7238-214">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="b7238-215">Ordine di avvolgimento e sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="b7238-215">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="b7238-216">Tutte le mesh prodotte dalla comprensione della scena dovrebbero restituire mesh in un sistema di coordinate di destra usando l'ordine di avvolgimento in senso orario.</span><span class="sxs-lookup"><span data-stu-id="b7238-216">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="b7238-217">Nota: le compilazioni del sistema operativo precedenti a. 191105 possono avere un bug noto in cui le mesh "World" hanno restituito un ordine di avvolgimento in senso antiorario, che in seguito è stato risolto.</span><span class="sxs-lookup"><span data-stu-id="b7238-217">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="b7238-218">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="b7238-218">SceneQuad</span></span>

<span data-ttu-id="b7238-219">Un SceneQuad è un SceneComponent che rappresenta le superfici 2D che occupano il mondo 3D.</span><span class="sxs-lookup"><span data-stu-id="b7238-219">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="b7238-220">SceneQuads può essere usato in modo analogo ai piani ARKit ARPlaneAnchor o ARCore, ma offre funzionalità più avanzate come Canvas 2D da usare con le app flat o UX potenziato.</span><span class="sxs-lookup"><span data-stu-id="b7238-220">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="b7238-221">sono disponibili API specifiche 2D per i quad che semplificano l'uso del posizionamento e del layout e lo sviluppo (ad eccezione del rendering) con i quad dovrebbe essere più simile all'utilizzo di Canvas 2D rispetto alle mesh 3D.</span><span class="sxs-lookup"><span data-stu-id="b7238-221">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="b7238-222">Forma SceneQuad</span><span class="sxs-lookup"><span data-stu-id="b7238-222">SceneQuad shape</span></span>

<span data-ttu-id="b7238-223">SceneQuads definire una superficie rettangolare delimitata in 2D.</span><span class="sxs-lookup"><span data-stu-id="b7238-223">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="b7238-224">Tuttavia, SceneQuads rappresentano le superfici con forme arbitrarie e potenzialmente complesse, ad esempio una tabella con forma di anello. Per rappresentare la forma complessa della superficie di un quad, è possibile usare l'API GetSurfaceMask per eseguire il rendering della forma della superficie in un buffer di immagine fornito.</span><span class="sxs-lookup"><span data-stu-id="b7238-224">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="b7238-225">Se anche il SceneObject con il quad ha una mesh, i triangoli di mesh devono essere equivalenti a questa immagine sottoposta a rendering, entrambi rappresentano la geometria reale della superficie, solo in coordinate 2D o 3D.</span><span class="sxs-lookup"><span data-stu-id="b7238-225">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, just either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="b7238-226">Informazioni dettagliate e informazioni di riferimento sull'SDK della scena</span><span class="sxs-lookup"><span data-stu-id="b7238-226">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="b7238-227">La sezione seguente consente di acquisire familiarità con le nozioni di base di SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="b7238-227">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="b7238-228">In questa sezione vengono fornite le nozioni di base, a questo punto è necessario disporre di un contesto sufficiente per esplorare le applicazioni di esempio per vedere come SceneUnderstanding viene usato in modo olistico.</span><span class="sxs-lookup"><span data-stu-id="b7238-228">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="b7238-229">Inizializzazione</span><span class="sxs-lookup"><span data-stu-id="b7238-229">Initialization</span></span>

<span data-ttu-id="b7238-230">Il primo passaggio per lavorare con SceneUnderstanding è che l'applicazione ottenga un riferimento a un oggetto scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-230">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="b7238-231">Questa operazione può essere eseguita in uno dei due modi seguenti, una scena può essere calcolata dal driver o una scena esistente calcolata in passato può essere deserializzata.</span><span class="sxs-lookup"><span data-stu-id="b7238-231">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="b7238-232">Quest'ultimo è particolarmente utile per lavorare con SceneUnderstanding durante lo sviluppo, in cui le applicazioni e le esperienze possono essere prototipate rapidamente senza un dispositivo di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b7238-232">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="b7238-233">Le scene vengono calcolate usando un SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="b7238-233">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="b7238-234">Prima di creare una scena, l'applicazione deve eseguire una query sul dispositivo per assicurarsi che supporti SceneUnderstanding, oltre a richiedere l'accesso utente per le informazioni necessarie a SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="b7238-234">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="b7238-235">Se RequestAccessAsync () non viene chiamato, il calcolo di una nuova scena avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="b7238-235">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="b7238-236">Successivamente, verrà calcolata una nuova scena che è radicata intorno all'auricolare della realtà mista e ha un raggio di 10 metri.</span><span class="sxs-lookup"><span data-stu-id="b7238-236">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="b7238-237">Inizializzazione dai dati (noto anche come.</span><span class="sxs-lookup"><span data-stu-id="b7238-237">Initialization from Data (aka.</span></span> <span data-ttu-id="b7238-238">Percorso PC)</span><span class="sxs-lookup"><span data-stu-id="b7238-238">the PC Path)</span></span>

<span data-ttu-id="b7238-239">Mentre le scene possono essere calcolate per il consumo diretto, possono anche essere calcolate in formato serializzato per un uso successivo.</span><span class="sxs-lookup"><span data-stu-id="b7238-239">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="b7238-240">Questo si è dimostrato di essere molto utile per lo sviluppo, in quanto consente agli sviluppatori di lavorare e testare la comprensione della scena senza la necessità di un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b7238-240">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="b7238-241">L'azione di serializzazione di una scena è quasi identica a quella di elaborazione. i dati vengono restituiti all'applicazione anziché essere deserializzati localmente dall'SDK.</span><span class="sxs-lookup"><span data-stu-id="b7238-241">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="b7238-242">Sarà quindi possibile deserializzarlo manualmente o salvarlo per un uso futuro.</span><span class="sxs-lookup"><span data-stu-id="b7238-242">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneBlob for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="b7238-243">Enumerazione SceneObject</span><span class="sxs-lookup"><span data-stu-id="b7238-243">SceneObject Enumeration</span></span>

<span data-ttu-id="b7238-244">Ora che l'applicazione ha una scena, l'applicazione verrà esaminata e interagirà con SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="b7238-244">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="b7238-245">Questa operazione viene eseguita accedendo alla proprietà **SceneObjects** :</span><span class="sxs-lookup"><span data-stu-id="b7238-245">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="b7238-246">Aggiornamento dei componenti e riricerca dei componenti</span><span class="sxs-lookup"><span data-stu-id="b7238-246">Component update and re-finding components</span></span>

<span data-ttu-id="b7238-247">Esiste un'altra funzione che recupera i componenti nella scena denominata ***findComponent***.</span><span class="sxs-lookup"><span data-stu-id="b7238-247">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="b7238-248">Questa funzione è utile quando si aggiornano gli oggetti di rilevamento e li si trova nelle scene successive.</span><span class="sxs-lookup"><span data-stu-id="b7238-248">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="b7238-249">Il codice seguente consente di calcolare una nuova scena rispetto a una scena precedente e quindi di trovare il piano nella nuova scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-249">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="b7238-250">Accesso a mesh e quad da oggetti scene</span><span class="sxs-lookup"><span data-stu-id="b7238-250">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="b7238-251">Una volta rilevate SceneObjects, è probabile che l'applicazione acceda ai dati contenuti nei Quad/mesh di cui è costituita.</span><span class="sxs-lookup"><span data-stu-id="b7238-251">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="b7238-252">Questi dati sono accessibili con le proprietà ***Quad*** e ***mesh*** .</span><span class="sxs-lookup"><span data-stu-id="b7238-252">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="b7238-253">Il codice seguente enumera tutti i quad e le maglie dell'oggetto Floor.</span><span class="sxs-lookup"><span data-stu-id="b7238-253">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="b7238-254">Si noti che si tratta del SceneObject con la trasformazione rispetto all'origine della scena.</span><span class="sxs-lookup"><span data-stu-id="b7238-254">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="b7238-255">Questo perché SceneObject rappresenta un'istanza di una "cosa" ed è locatable nello spazio, i quad e le mesh rappresentano la geometria che viene trasformata in relazione al rispettivo elemento padre.</span><span class="sxs-lookup"><span data-stu-id="b7238-255">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="b7238-256">È possibile che SceneObjects separate facciano riferimento allo stesso SceneComponents SceneMesh/SceneQuad ed è anche possibile che un SceneObject disponga di più di un SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="b7238-256">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="b7238-257">Gestione delle trasformazioni</span><span class="sxs-lookup"><span data-stu-id="b7238-257">Dealing with Transforms</span></span>

<span data-ttu-id="b7238-258">La comprensione della scena ha effettuato un tentativo intenzionale di allinearsi alle rappresentazioni tradizionali della scena 3D quando si gestiscono le trasformazioni.</span><span class="sxs-lookup"><span data-stu-id="b7238-258">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="b7238-259">Ogni scena è quindi confinata a un singolo sistema di coordinate, in modo analogo alla maggior parte delle rappresentazioni ambientali 3D.</span><span class="sxs-lookup"><span data-stu-id="b7238-259">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="b7238-260">SceneObjects forniscono la posizione e l'orientamento all'interno del sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="b7238-260">SceneObjects each provide their location as a position and orientation within that coordinate system.</span></span> <span data-ttu-id="b7238-261">Se l'applicazione sta affrontando scenari che estendono il limite di una singola origine, può ancorare SceneObjects a SpatialAnchors o generare diverse scene e unirle, ma per semplicità si presuppone che le scene stagne esistano nei propri origine localizzata da un NodeId definito da scene. OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="b7238-261">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="b7238-262">Il codice Unity seguente, ad esempio, Mostra come usare la percezione di Windows e le API Unity per allineare i sistemi di coordinate.</span><span class="sxs-lookup"><span data-stu-id="b7238-262">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="b7238-263">Vedere [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) per informazioni dettagliate sulle API di percezione di Windows e sugli [oggetti nativi della realtà mista in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) per informazioni dettagliate su come ottenere un SpatialCoordinateSystem che corrisponde a Unity ' s di origine, nonché il metodo di estensione `.ToUnity()` per la conversione tra `System.Numerics.Matrix4x4` e `UnityEngine.Matrix4x4`.</span><span class="sxs-lookup"><span data-stu-id="b7238-263">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin, as well as the `.ToUnity()` extension method for converting between `System.Numerics.Matrix4x4` and `UnityEngine.Matrix4x4`.</span></span>

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

<span data-ttu-id="b7238-264">Ogni `SceneObject` dispone di una proprietà `Position` e `Orientation` che può essere usata per posizionare il contenuto corrispondente rispetto all'origine del `Scene`che lo contiene.</span><span class="sxs-lookup"><span data-stu-id="b7238-264">Each `SceneObject` has a `Position` and `Orientation` property which can be used to position corresponding content relative to the origin of the containing `Scene`.</span></span> <span data-ttu-id="b7238-265">Ad esempio, nell'esempio seguente si presuppone che il gioco sia un figlio della radice della scena e assegna la posizione e la rotazione locali per l'allineamento a una determinata `SceneObject`:</span><span class="sxs-lookup"><span data-stu-id="b7238-265">For example, the following example assumes that the game is a child of the scene root, and assigns its local position and rotation to align to a given `SceneObject`:</span></span>

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a><span data-ttu-id="b7238-266">Quad</span><span class="sxs-lookup"><span data-stu-id="b7238-266">Quad</span></span>

<span data-ttu-id="b7238-267">I quad sono stati progettati per semplificare gli scenari di posizionamento 2D e dovrebbero essere considerati come estensioni per gli elementi UX di Canvas 2D.</span><span class="sxs-lookup"><span data-stu-id="b7238-267">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="b7238-268">Mentre i quad sono componenti di SceneObjects e possono essere sottoposti a rendering in 3D, le API quadre presuppongono quad sono strutture 2D.</span><span class="sxs-lookup"><span data-stu-id="b7238-268">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="b7238-269">Offrono informazioni come extent, Shape e forniscono API per la selezione host.</span><span class="sxs-lookup"><span data-stu-id="b7238-269">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="b7238-270">I quad hanno extent rettangolari, ma rappresentano superfici 2D a forma arbitraria.</span><span class="sxs-lookup"><span data-stu-id="b7238-270">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="b7238-271">Per abilitare la selezione host in queste superfici 2D che interagiscono con i quad dell'ambiente 3D offrono utilità per rendere possibile questa interazione.</span><span class="sxs-lookup"><span data-stu-id="b7238-271">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="b7238-272">Attualmente la comprensione della scena fornisce due funzioni di questo tipo, **FindCentermostPlacement** e **GetOcclusionMask**.</span><span class="sxs-lookup"><span data-stu-id="b7238-272">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="b7238-273">FindCentermostPlacement è un'API di alto livello che individua una posizione nel quad in cui è possibile posizionare un oggetto e tenterà di trovare la posizione migliore per l'oggetto, garantendo che il rettangolo di delimitazione fornito si trovi sulla superficie sottostante.</span><span class="sxs-lookup"><span data-stu-id="b7238-273">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="b7238-274">Nell'esempio seguente viene illustrato come trovare la posizione posizionabile effettuare e come ancorare un ologramma al quad.</span><span class="sxs-lookup"><span data-stu-id="b7238-274">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="b7238-275">I passaggi 1-4 dipendono in modo estremamente da un particolare Framework/implementazione, ma i temi dovrebbero essere simili.</span><span class="sxs-lookup"><span data-stu-id="b7238-275">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="b7238-276">È importante notare che il quad rappresenta semplicemente un piano 2D con binding localizzato nello spazio.</span><span class="sxs-lookup"><span data-stu-id="b7238-276">It is important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="b7238-277">Se il motore/Framework sa dove si trova il quad e si radicano gli oggetti rispetto al quad, gli ologrammi saranno posizionati correttamente rispetto al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="b7238-277">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> <span data-ttu-id="b7238-278">Per informazioni più dettagliate, vedere gli esempi su quad che mostrano implementazioni specifiche.</span><span class="sxs-lookup"><span data-stu-id="b7238-278">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="b7238-279">Mesh</span><span class="sxs-lookup"><span data-stu-id="b7238-279">Mesh</span></span>

<span data-ttu-id="b7238-280">Le mesh rappresentano rappresentazioni geometriche di oggetti o ambienti.</span><span class="sxs-lookup"><span data-stu-id="b7238-280">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="b7238-281">In modo analogo al [mapping spaziale](spatial-mapping.md), i dati relativi a indici mesh e vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei vertex buffer e degli indici utilizzati per il rendering di mesh triangolari in tutte le moderne API per il rendering.</span><span class="sxs-lookup"><span data-stu-id="b7238-281">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="b7238-282">Le posizioni dei vertici vengono fornite nel sistema di coordinate del `Scene`.</span><span class="sxs-lookup"><span data-stu-id="b7238-282">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="b7238-283">Le API specifiche usate per fare riferimento a questi dati sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="b7238-283">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="b7238-284">Il codice seguente fornisce un esempio di generazione di un elenco di triangolo dalla struttura mesh:</span><span class="sxs-lookup"><span data-stu-id="b7238-284">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="b7238-285">I buffer di indice/vertice devono essere > = i conteggi di indice/vertice, ma in caso contrario possono essere dimensionati arbitrariamente, consentendo un utilizzo efficace della memoria.</span><span class="sxs-lookup"><span data-stu-id="b7238-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

## <a name="developing-with-scene-understandings"></a><span data-ttu-id="b7238-286">Sviluppo con informazioni sulle scene</span><span class="sxs-lookup"><span data-stu-id="b7238-286">Developing with scene understandings</span></span>

<span data-ttu-id="b7238-287">A questo punto è necessario comprendere i componenti di base della scena Understanding Runtime and SDK.</span><span class="sxs-lookup"><span data-stu-id="b7238-287">At this point you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="b7238-288">La maggior parte della potenza e della complessità si basa sui modelli di accesso, sull'interazione con i framework 3D e sugli strumenti che possono essere scritti su queste API per eseguire attività più avanzate, come la pianificazione spaziale, l'analisi delle stanze, la navigazione, la fisica e così via. Ci auguriamo che questi esempi vengano acquisiti in esempi che dovrebbero guidare l'utente nella direzione corretta per rendere più brillanti gli scenari.</span><span class="sxs-lookup"><span data-stu-id="b7238-288">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc. We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="b7238-289">Se sono presenti esempi/scenari non indirizzati, è possibile inviare una notifica e provare a documentare/prototipare gli elementi necessari.</span><span class="sxs-lookup"><span data-stu-id="b7238-289">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="b7238-290">Dove è possibile ottenere il codice di esempio?</span><span class="sxs-lookup"><span data-stu-id="b7238-290">Where can I get sample code?</span></span>

<span data-ttu-id="b7238-291">Scenario per informazioni sul codice di esempio per Unity, vedere la pagina di [esempio Unity](https://github.com/sceneunderstanding-microsoft/unitysample) .</span><span class="sxs-lookup"><span data-stu-id="b7238-291">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="b7238-292">Questa applicazione consente di comunicare con il dispositivo ed eseguire il rendering dei vari oggetti scena, oppure di caricare una scena serializzata nel PC e di sperimentare la comprensione della scena senza un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b7238-292">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="b7238-293">Dove è possibile ottenere scene di esempio?</span><span class="sxs-lookup"><span data-stu-id="b7238-293">Where can I get sample scenes?</span></span>

<span data-ttu-id="b7238-294">Se si dispone di un HoloLens2, è possibile salvare qualsiasi scena acquisita salvando l'output di ComputeSerializedAsync in file e deserializzarlo in base alla propria convenienza.</span><span class="sxs-lookup"><span data-stu-id="b7238-294">If you have a HoloLens2 you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="b7238-295">Se non si ha un dispositivo HoloLens2 ma si vuole giocare con la comprensione della scena, è necessario scaricare una scena pre-acquisita.</span><span class="sxs-lookup"><span data-stu-id="b7238-295">If you do not have a HoloLens2 device but want to play with Scene Understanding you will need to download a pre-captured scene.</span></span> <span data-ttu-id="b7238-296">L'esempio di comprensione della scena è attualmente fornito con scene serializzate che possono essere scaricate e usate con facilità.</span><span class="sxs-lookup"><span data-stu-id="b7238-296">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="b7238-297">È possibile trovarli qui:</span><span class="sxs-lookup"><span data-stu-id="b7238-297">You can find them here:</span></span>

[<span data-ttu-id="b7238-298">Scene di esempio sulla comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="b7238-298">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="b7238-299">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b7238-299">See also</span></span>

* [<span data-ttu-id="b7238-300">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="b7238-300">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="b7238-301">Informazioni sulle scene</span><span class="sxs-lookup"><span data-stu-id="b7238-301">Scene understanding</span></span>](scene-understanding.md)
* [<span data-ttu-id="b7238-302">Esempio di Unity</span><span class="sxs-lookup"><span data-stu-id="b7238-302">Unity Sample</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample)
