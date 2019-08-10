---
title: Scenario di comprensione dell'SDK
description: Guida alla programmazione per l'SDK di informazioni sulla scena
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, realtà mista di Windows, Unity
ms.openlocfilehash: 88138622987800ff86a24d05e1308e694e2dd2b1
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2019
ms.locfileid: "68941238"
---
## <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="3306b-104">Panoramica dell'SDK per la comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="3306b-104">Scene Understanding SDK Overview</span></span>

<span data-ttu-id="3306b-105">L'obiettivo della comprensione della scena consiste nel trasformare i dati dei sensori dell'ambiente non strutturati acquisiti dal dispositivo della realtà mista e convertirli in una rappresentazione potente ma astratta che è intuitiva e facile da sviluppare per.</span><span class="sxs-lookup"><span data-stu-id="3306b-105">The goal of Scene Understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="3306b-106">L'SDK funge da livello di comunicazione tra l'applicazione e la scena che comprende il Runtime.</span><span class="sxs-lookup"><span data-stu-id="3306b-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="3306b-107">Ha lo scopo di simulare costrutti standard esistenti, ad esempio grafici della scena 3D per le rappresentazioni 3D e rettangoli/pannelli 2D per le applicazioni 2D.</span><span class="sxs-lookup"><span data-stu-id="3306b-107">It's aimed to mimic existing standard constructs such as 3d scene graphs for 3d representations and 2D rectangles/panels for 2d applications.</span></span> <span data-ttu-id="3306b-108">Mentre la scena dei costrutti che comprendono le simulazioni verrà mappata a Framework concreti che è possibile usare, in generale SceneUnderstanding è un Framework agnostico che consente l'interoperabilità tra diversi Framework che interagiscono con esso.</span><span class="sxs-lookup"><span data-stu-id="3306b-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="3306b-109">Poiché la comprensione della scena evolve il ruolo dell'SDK è garantire che le nuove rappresentazioni e funzionalità continuino a essere esposte in un framework unificato.</span><span class="sxs-lookup"><span data-stu-id="3306b-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="3306b-110">In questo documento vengono introdotti i concetti di alto livello che consentiranno di acquisire familiarità con l'ambiente di sviluppo e l'utilizzo e quindi fornire una documentazione più dettagliata per classi e costrutti specifici.</span><span class="sxs-lookup"><span data-stu-id="3306b-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="3306b-111">Dove è possibile ottenere l'SDK?</span><span class="sxs-lookup"><span data-stu-id="3306b-111">Where do I get the SDK?</span></span>

<span data-ttu-id="3306b-112">SceneUnderstanding SDK è scaricabile tramite NuGet.</span><span class="sxs-lookup"><span data-stu-id="3306b-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="3306b-113">SDK di SceneUnderstanding</span><span class="sxs-lookup"><span data-stu-id="3306b-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="3306b-114">Prima di iniziare, si noti che l'SDK viene eseguito sopra il UWP e richiede Windows SDK versione 18362 o successiva.</span><span class="sxs-lookup"><span data-stu-id="3306b-114">Before you begin please note that the SDK runs on top of the UWP, and requires Windows SDK version 18362 or higher.</span></span> 

### <a name="the-scene"></a><span data-ttu-id="3306b-115">Scena</span><span class="sxs-lookup"><span data-stu-id="3306b-115">The Scene</span></span>

<span data-ttu-id="3306b-116">Il dispositivo di realtà mista sta integrando costantemente le informazioni relative a ciò che viene visualizzato nell'ambiente in uso.</span><span class="sxs-lookup"><span data-stu-id="3306b-116">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="3306b-117">La comprensione della scena incanala tutte queste origini dati e produce un'unica astrazione coesiva.</span><span class="sxs-lookup"><span data-stu-id="3306b-117">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="3306b-118">La comprensione della scena genera scene che sono una composizione di [SceneObjects](scene-understanding-SDK.md#sceneobjects) che rappresenta un'istanza di un singolo elemento, ad esempio una parete/soffitto/piano. Gli oggetti scena stessi sono una composizione di [SceneComponents](scene-understanding-SDK.md#scenecomponents) che rappresentano parti più granulari che compongono questo SceneObject.</span><span class="sxs-lookup"><span data-stu-id="3306b-118">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="3306b-119">Esempi di componenti sono i quad e i mesh, ma in futuro potrebbero rappresentare i rettangoli di delimitazione, i mehses di collisione, i metadati e così via.</span><span class="sxs-lookup"><span data-stu-id="3306b-119">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision mehses, metadata etc...</span></span>

<span data-ttu-id="3306b-120">Il processo di conversione dei dati dei sensori non elaborati in una scena è un'operazione potenzialmente costosa che può richiedere secondi per spazi medi (~ 10x10m) a minuti per spazi di dimensioni molto grandi (~ 50x50m) e pertanto non è un elemento che viene calcolato dal dispositivo senza richiesta dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="3306b-120">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="3306b-121">La generazione della scena viene invece attivata dall'applicazione su richiesta.</span><span class="sxs-lookup"><span data-stu-id="3306b-121">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="3306b-122">La classe SceneObserver dispone di metodi statici che consentono di calcolare o deserializzare una scena, con cui è possibile enumerare/interagire.</span><span class="sxs-lookup"><span data-stu-id="3306b-122">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="3306b-123">L'azione "calcolo" viene eseguita su richiesta ed eseguita sulla CPU, ma in un processo separato (il driver della realtà mista).</span><span class="sxs-lookup"><span data-stu-id="3306b-123">The "Compute" action is executed on-demand and executes on the CPU but in a seperate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="3306b-124">Tuttavia, mentre si esegue il calcolo in un altro processo, i dati della scena risultanti vengono archiviati e conservati nell'applicazione nell'oggetto scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-124">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="3306b-125">Di seguito è riportato un diagramma che illustra il flusso del processo e Mostra esempi di due applicazioni che si confrontano con la scena Understanding Runtime.</span><span class="sxs-lookup"><span data-stu-id="3306b-125">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagramma di processo](images/SU-ProcessFlow.png)

<span data-ttu-id="3306b-127">Sul lato sinistro è presente un diagramma del runtime di realtà mista che è sempre attivo e in esecuzione nel proprio processo.</span><span class="sxs-lookup"><span data-stu-id="3306b-127">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="3306b-128">Questo runtime è responsabile dell'esecuzione del rilevamento dei dispositivi, della ricostruzione della superficie e di altre operazioni che la comprensione della scena USA per comprendere e motivare il mondo.</span><span class="sxs-lookup"><span data-stu-id="3306b-128">This runtime is responsible for performing device tracking, surface reconstruction, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="3306b-129">Sul lato destro del diagramma sono illustrate due applicazioni teoriche che fanno uso della comprensione della scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-129">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="3306b-130">La prima interfaccia dell'applicazione con MRTK che usa la scena Understanding SDK internamente, la seconda app calcola e usa due istanze della scena sepèree.</span><span class="sxs-lookup"><span data-stu-id="3306b-130">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two sepereate scene instances.</span></span> <span data-ttu-id="3306b-131">Tutte e tre le scene in questo diagramma generano istanze distinte delle scene, il driver non rileva lo stato globale condiviso tra le applicazioni e gli oggetti scena in un'unica scena non è presente in un altro.</span><span class="sxs-lookup"><span data-stu-id="3306b-131">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="3306b-132">La comprensione della scena fornisce un meccanismo per tenere traccia nel tempo, ma questa operazione viene eseguita usando l'SDK e il codice che esegue questo rilevamento viene eseguito nell'SDK nel processo dell'app.</span><span class="sxs-lookup"><span data-stu-id="3306b-132">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and code the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="3306b-133">Poiché ogni scena archivia i dati nello spazio di memoria dell'applicazione, si può presupporre che tutte le funzioni dell'oggetto scene o dei dati interni vengano sempre eseguite nel processo dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="3306b-133">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

#### <a name="layout"></a><span data-ttu-id="3306b-134">Layout</span><span class="sxs-lookup"><span data-stu-id="3306b-134">Layout</span></span>

<span data-ttu-id="3306b-135">Per lavorare con la comprensione della scena, può essere utile conoscere e comprendere il modo in cui il runtime rappresenta i componenti in modo logico e fisico.</span><span class="sxs-lookup"><span data-stu-id="3306b-135">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="3306b-136">La scena rappresenta i dati con un layout specifico che è stato scelto per essere semplice mantenendo una struttura sottostante flessibile per soddisfare i requisiti futuri senza che siano necessarie revisioni principali.</span><span class="sxs-lookup"><span data-stu-id="3306b-136">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="3306b-137">Questa operazione viene eseguita archiviando tutti i componenti (elementi di base per tutti gli oggetti della scena) in un elenco semplice e definendo la gerarchia e la composizione tramite riferimenti in cui componenti specifici fanno riferimento ad altri.</span><span class="sxs-lookup"><span data-stu-id="3306b-137">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="3306b-138">Di seguito viene presentato un esempio di una struttura sia nel formato flat che nella forma logica.</span><span class="sxs-lookup"><span data-stu-id="3306b-138">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="3306b-139">Layout logico</span><span class="sxs-lookup"><span data-stu-id="3306b-139">Logical Layout</span></span></th><th><span data-ttu-id="3306b-140">Layout fisico</span><span class="sxs-lookup"><span data-stu-id="3306b-140">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="3306b-141">Scena</span><span class="sxs-lookup"><span data-stu-id="3306b-141">Scene</span></span>
  <ul>
  <li><span data-ttu-id="3306b-142">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="3306b-142">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="3306b-143">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="3306b-143">Mesh_1</span></span></li>
      <li><span data-ttu-id="3306b-144">Quad_1</span><span class="sxs-lookup"><span data-stu-id="3306b-144">Quad_1</span></span></li>
      <li><span data-ttu-id="3306b-145">Quad_2</span><span class="sxs-lookup"><span data-stu-id="3306b-145">Quad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="3306b-146">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="3306b-146">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="3306b-147">Quad_1</span><span class="sxs-lookup"><span data-stu-id="3306b-147">Quad_1</span></span></li>
      <li><span data-ttu-id="3306b-148">Quad_3</span><span class="sxs-lookup"><span data-stu-id="3306b-148">Quad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="3306b-149">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="3306b-149">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="3306b-150">Mesh_3</span><span class="sxs-lookup"><span data-stu-id="3306b-150">Mesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="3306b-151">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="3306b-151">SceneObject_1</span></span></li>
  <li><span data-ttu-id="3306b-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="3306b-152">SceneObject_2</span></span></li>
  <li><span data-ttu-id="3306b-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="3306b-153">SceneObject_3</span></span></li>
  <li><span data-ttu-id="3306b-154">Quad_1</span><span class="sxs-lookup"><span data-stu-id="3306b-154">Quad_1</span></span></li>
  <li><span data-ttu-id="3306b-155">Quad_2</span><span class="sxs-lookup"><span data-stu-id="3306b-155">Quad_2</span></span></li>
  <li><span data-ttu-id="3306b-156">Quad_3</span><span class="sxs-lookup"><span data-stu-id="3306b-156">Quad_3</span></span></li>
  <li><span data-ttu-id="3306b-157">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="3306b-157">Mesh_1</span></span></li>
  <li><span data-ttu-id="3306b-158">Mesh_2</span><span class="sxs-lookup"><span data-stu-id="3306b-158">Mesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="3306b-159">In questa illustrazione viene evidenziata la differenza tra il layout fisico e logico della scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-159">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="3306b-160">A destra viene visualizzato il layout gerarchico dei dati visualizzati dall'applicazione durante l'enumerazione della scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-160">On the right we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="3306b-161">A sinistra si noterà che la scena è costituita da 12 componenti distinti, se necessario, accessibili singolarmente.</span><span class="sxs-lookup"><span data-stu-id="3306b-161">On the left we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="3306b-162">Quando si elabora una nuova scena, si prevede che le applicazioni analizzino logicamente questa gerarchia. Tuttavia, durante il rilevamento tra gli aggiornamenti della scena, alcune applicazioni potrebbero essere interessate solo a specifici componenti condivisi tra due scene.</span><span class="sxs-lookup"><span data-stu-id="3306b-162">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

### <a name="high-level-overview"></a><span data-ttu-id="3306b-163">Panoramica di alto livello</span><span class="sxs-lookup"><span data-stu-id="3306b-163">High-level Overview</span></span>

<span data-ttu-id="3306b-164">Nella sezione seguente viene fornita una panoramica di alto livello dei costrutti nella comprensione della scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-164">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="3306b-165">Leggendo questa sezione si apprenderà a comprendere come vengono rappresentate le scene e quali sono i vari componenti usati per.</span><span class="sxs-lookup"><span data-stu-id="3306b-165">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="3306b-166">La sezione successiva fornirà esempi di codice concreti e dettagli aggiuntivi che verranno descritti in questa panoramica.</span><span class="sxs-lookup"><span data-stu-id="3306b-166">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

#### <a name="scenecomponents"></a><span data-ttu-id="3306b-167">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="3306b-167">SceneComponents</span></span>

<span data-ttu-id="3306b-168">Dopo aver compreso il layout logico delle scene, è ora possibile presentare il concetto di SceneComponents e il modo in cui vengono usate per comporre la gerarchia.</span><span class="sxs-lookup"><span data-stu-id="3306b-168">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="3306b-169">SceneComponents sono le scomposizione più granulari in SceneUnderstanding che rappresentano un'unica cosa fondamentale, ad esempio una mesh o un quad o un rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="3306b-169">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="3306b-170">SceneComponents sono elementi che possono essere aggiornati in modo indipendente ed è possibile farvi riferimento da altri SceneComponents, di conseguenza hanno un'unica proprietà globale un ID univoco, che consente questo tipo di meccanismo di rilevamento/riferimento.</span><span class="sxs-lookup"><span data-stu-id="3306b-170">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="3306b-171">Gli ID vengono usati per la composizione logica della gerarchia della scena e per la persistenza degli oggetti, ovvero l'operazione di aggiornamento di una scena rispetto a un'altra.</span><span class="sxs-lookup"><span data-stu-id="3306b-171">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="3306b-172">Se si tratta di una nuova scena calcolata come distinta e si esegue semplicemente l'enumerazione di tutti i dati al suo interno, gli ID sono in gran parte trasparenti.</span><span class="sxs-lookup"><span data-stu-id="3306b-172">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="3306b-173">Tuttavia, se si prevede di tenere traccia dei componenti in diversi aggiornamenti, si useranno gli ID per indicizzare e trovare SceneComponents tra gli oggetti scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-173">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

#### <a name="sceneobjects"></a><span data-ttu-id="3306b-174">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="3306b-174">SceneObjects</span></span>

<span data-ttu-id="3306b-175">Un SceneObject è un SceneComponent che rappresenta un'istanza di un elemento "Thing", ad esempio un muro, un piano, un soffitto e così via. espressa dalla relativa proprietà Kind.</span><span class="sxs-lookup"><span data-stu-id="3306b-175">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="3306b-176">SceneObjects sono geometriche e quindi hanno funzioni e proprietà che rappresentano la loro posizione nello spazio, ma non contengono alcuna struttura geometrica o logica.</span><span class="sxs-lookup"><span data-stu-id="3306b-176">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="3306b-177">SceneObjects, invece, fanno riferimento ad altri SceneComponents, in particolare SceneQuads e SceneMeshes, che forniscono le varie rappresentazioni supportate dal sistema.</span><span class="sxs-lookup"><span data-stu-id="3306b-177">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="3306b-178">Quando viene calcolata una nuova scena, l'applicazione enumera in modo più probabile la SceneObjects della scena per elaborare gli elementi interessati.</span><span class="sxs-lookup"><span data-stu-id="3306b-178">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="3306b-179">SceneObjects può avere uno dei seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="3306b-179">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="3306b-180">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="3306b-180">SceneObjectKind</span></span></th> <th><span data-ttu-id="3306b-181">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3306b-181">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="3306b-182">Sfondo</span><span class="sxs-lookup"><span data-stu-id="3306b-182">Background</span></span></td><td><span data-ttu-id="3306b-183">Il SceneObject <b>non</b> è noto come uno degli altri tipi di oggetto scena riconosciuti.</span><span class="sxs-lookup"><span data-stu-id="3306b-183">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="3306b-184">Questa classe non deve essere confusa con Unknown, in cui lo sfondo non è a parete/piano/soffitto e così via... mentre Unknown non è ancora stato categorizzato.</span><span class="sxs-lookup"><span data-stu-id="3306b-184">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="3306b-185">Parete</span><span class="sxs-lookup"><span data-stu-id="3306b-185">Wall</span></span></td><td><span data-ttu-id="3306b-186">Una parete fisica.</span><span class="sxs-lookup"><span data-stu-id="3306b-186">A physical wall.</span></span> <span data-ttu-id="3306b-187">Si presuppone che i muri siano strutture ambientali non mobili.</span><span class="sxs-lookup"><span data-stu-id="3306b-187">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="3306b-188">Floor</span><span class="sxs-lookup"><span data-stu-id="3306b-188">Floor</span></span></td><td><span data-ttu-id="3306b-189">I piani sono superfici in cui è possibile spostarsi.</span><span class="sxs-lookup"><span data-stu-id="3306b-189">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="3306b-190">Nota: le scale non sono piani.</span><span class="sxs-lookup"><span data-stu-id="3306b-190">Note: stairs are not floors.</span></span> <span data-ttu-id="3306b-191">Si noti inoltre che le pavimentazioni presuppongono una superficie a cui è possibile spostarsi e pertanto non esiste alcun presupposto esplicito di un pavimento singolare.</span><span class="sxs-lookup"><span data-stu-id="3306b-191">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="3306b-192">Strutture a più livelli, rampe e così via... deve essere classificata come floor.</span><span class="sxs-lookup"><span data-stu-id="3306b-192">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="3306b-193">Ceiling</span><span class="sxs-lookup"><span data-stu-id="3306b-193">Ceiling</span></span></td><td><span data-ttu-id="3306b-194">Superficie superiore di una stanza.</span><span class="sxs-lookup"><span data-stu-id="3306b-194">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="3306b-195">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="3306b-195">Platform</span></span></td><td><span data-ttu-id="3306b-196">Una superficie piana grande su cui posizionare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="3306b-196">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="3306b-197">Che tendono a rappresentare tabelle, piani di ridimensionamento e altre superfici orizzontali di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="3306b-197">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="3306b-198">World</span><span class="sxs-lookup"><span data-stu-id="3306b-198">World</span></span></td><td><span data-ttu-id="3306b-199">Etichetta riservata per i dati geometrici indipendenti dall'assegnazione di etichette.</span><span class="sxs-lookup"><span data-stu-id="3306b-199">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="3306b-200">La mesh generata impostando il flag di aggiornamento EnableWorldMesh verrebbe classificato come World.</span><span class="sxs-lookup"><span data-stu-id="3306b-200">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="3306b-201">Sconosciuto</span><span class="sxs-lookup"><span data-stu-id="3306b-201">Unknown</span></span></td><td><span data-ttu-id="3306b-202">Questo oggetto scena deve ancora essere classificato e assegnato un tipo.</span><span class="sxs-lookup"><span data-stu-id="3306b-202">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="3306b-203">Questa operazione non deve essere confusa con lo sfondo, perché questo oggetto può essere qualsiasi cosa, il sistema non ha ancora una classificazione sufficientemente forte per il sistema.</span><span class="sxs-lookup"><span data-stu-id="3306b-203">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

#### <a name="scenemesh"></a><span data-ttu-id="3306b-204">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="3306b-204">SceneMesh</span></span>

<span data-ttu-id="3306b-205">Un SceneMesh è un SceneComponent che approssima la geometria degli oggetti geometrici arbitrari usando un elenco di triangolo.</span><span class="sxs-lookup"><span data-stu-id="3306b-205">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="3306b-206">SceneMeshes vengono usati in diversi contesti, possono rappresentare i componenti della struttura di celle stagne o come WorldMesh che rappresenta la ricostruzione della superficie non associata associata alla scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-206">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded Surface Reconstruction associated with the Scene.</span></span> <span data-ttu-id="3306b-207">I dati relativi a indici e vertici forniti con ogni mesh utilizzano lo stesso layout familiare dei [buffer di vertice e di indice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) utilizzati per il rendering di mesh triangolari in tutte le moderne API di rendering.</span><span class="sxs-lookup"><span data-stu-id="3306b-207">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="3306b-208">Si noti che nella comprensione della scena le maglie usano gli indici a 32 bit e potrebbero dover essere suddivise in blocchi per determinati motori di rendering.</span><span class="sxs-lookup"><span data-stu-id="3306b-208">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="scenequad"></a><span data-ttu-id="3306b-209">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="3306b-209">SceneQuad</span></span>

<span data-ttu-id="3306b-210">Un SceneQuad è un SceneComponent che rappresenta le superfici 2D che occupano il mondo 3D.</span><span class="sxs-lookup"><span data-stu-id="3306b-210">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="3306b-211">SceneQuads può essere usato in modo analogo ai piani ARKit ARPlaneAnchor o ARCore, ma offre funzionalità più avanzate come Canvas 2D da usare con le app flat o UX potenziato.</span><span class="sxs-lookup"><span data-stu-id="3306b-211">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="3306b-212">sono disponibili API specifiche 2D per i quad che semplificano l'uso del posizionamento e del layout e lo sviluppo (ad eccezione del rendering) con i quad dovrebbe essere più simile all'utilizzo di Canvas 2D rispetto alle mesh 3D.</span><span class="sxs-lookup"><span data-stu-id="3306b-212">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

### <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="3306b-213">Informazioni dettagliate e informazioni di riferimento sull'SDK della scena</span><span class="sxs-lookup"><span data-stu-id="3306b-213">Scene Understanding SDK Details and Reference</span></span>

#### <a name="sdk"></a><span data-ttu-id="3306b-214">SDK</span><span class="sxs-lookup"><span data-stu-id="3306b-214">SDK</span></span>

<span data-ttu-id="3306b-215">La sezione seguente consente di acquisire familiarità con le nozioni di base di SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="3306b-215">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="3306b-216">In questa sezione vengono fornite le nozioni di base, a questo punto è necessario disporre di un contesto sufficiente per esplorare le applicazioni di esempio per vedere come SceneUnderstanding viene usato in modo olistico.</span><span class="sxs-lookup"><span data-stu-id="3306b-216">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

#### <a name="initialization"></a><span data-ttu-id="3306b-217">Inizializzazione</span><span class="sxs-lookup"><span data-stu-id="3306b-217">Initialization</span></span>

<span data-ttu-id="3306b-218">Il primo passaggio per lavorare con SceneUnderstanding è che l'applicazione ottenga un riferimento a un oggetto scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-218">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="3306b-219">Questa operazione può essere eseguita in uno dei due modi seguenti, una scena può essere calcolata dal driver o una scena esistente calcolata in passato può essere deserializzata.</span><span class="sxs-lookup"><span data-stu-id="3306b-219">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="3306b-220">Quest'ultimo è particolarmente utile per lavorare con SceneUnderstanding durante lo sviluppo, in cui le applicazioni e le esperienze possono essere prototipate rapidamente senza un dispositivo di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3306b-220">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="3306b-221">Le scene vengono calcolate usando un SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="3306b-221">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="3306b-222">Prima di creare una scena, l'applicazione deve eseguire una query sul dispositivo per assicurarsi che supporti SceneUnderstanding, oltre a richiedere l'accesso utente per le informazioni necessarie a SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="3306b-222">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="3306b-223">Se RequestAccessAsync () non viene chiamato, il calcolo di una nuova scena avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="3306b-223">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="3306b-224">Successivamente, verrà calcolata una nuova scena che è radicata intorno all'auricolare della realtà mista e ha un raggio di 10 metri.</span><span class="sxs-lookup"><span data-stu-id="3306b-224">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.Compute(querySettings, 10.0f);
```

#### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="3306b-225">Inizializzazione dai dati (noto anche come.</span><span class="sxs-lookup"><span data-stu-id="3306b-225">Initialization from Data (aka.</span></span> <span data-ttu-id="3306b-226">Percorso PC)</span><span class="sxs-lookup"><span data-stu-id="3306b-226">the PC Path)</span></span>

<span data-ttu-id="3306b-227">Mentre le scene possono essere calcolate per il consumo diretto, possono anche essere calcolate in formato serializzato per un uso successivo.</span><span class="sxs-lookup"><span data-stu-id="3306b-227">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="3306b-228">Questo si è dimostrato di essere molto utile per lo sviluppo, in quanto consente agli sviluppatori di lavorare e testare la comprensione della scena senza la necessità di un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3306b-228">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="3306b-229">L'azione di serializzazione di una scena è quasi identica a quella di elaborazione. i dati vengono restituiti all'applicazione anziché essere deserializzati localmente dall'SDK.</span><span class="sxs-lookup"><span data-stu-id="3306b-229">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="3306b-230">Sarà quindi possibile deserializzarlo manualmente o salvarlo per un uso futuro.</span><span class="sxs-lookup"><span data-stu-id="3306b-230">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneUnderstanding.QuerySettings querySettings;

// Compute a scene but serialized as a byte array
byte[] newSceneBlob = SceneObserver.ComputeSerialized(querySettings, 10.0f);

// If we want to use it immediatley we can de-serialize the scene ourselves
Scene mySceneDeSerialized = Scene.Deserialize(newSceneBlob);

// Save newSceneBlob for later
```

#### <a name="sceneobject-enumeration"></a><span data-ttu-id="3306b-231">Enumerazione SceneObject</span><span class="sxs-lookup"><span data-stu-id="3306b-231">SceneObject Enumeration</span></span>

<span data-ttu-id="3306b-232">Ora che l'applicazione ha una scena, l'applicazione verrà esaminata e interagirà con SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="3306b-232">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="3306b-233">Questa operazione viene eseguita accedendo alla proprietà **SceneObjects** :</span><span class="sxs-lookup"><span data-stu-id="3306b-233">This is done by accessing the **SceneObjects** property:</span></span>

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

#### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="3306b-234">Aggiornamento dei componenti e riricerca dei componenti</span><span class="sxs-lookup"><span data-stu-id="3306b-234">Component update and re-finding components</span></span>

<span data-ttu-id="3306b-235">Esiste un'altra funzione che recupera i componenti nella scena denominata ***findComponent***.</span><span class="sxs-lookup"><span data-stu-id="3306b-235">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="3306b-236">Questa funzione è utile quando si aggiornano gli oggetti di rilevamento e li si trova nelle scene successive.</span><span class="sxs-lookup"><span data-stu-id="3306b-236">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="3306b-237">Il codice seguente consente di calcolare una nuova scena rispetto a una scena precedente e quindi di trovare il piano nella nuova scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-237">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, but tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.Compute(querySettings, 10.0f, myScene);

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attatched to this floor transform
}
```

### <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="3306b-238">Accesso a mesh e quad da oggetti scene</span><span class="sxs-lookup"><span data-stu-id="3306b-238">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="3306b-239">Una volta rilevate SceneObjects, è probabile che l'applicazione acceda ai dati che contengono n i quad/mesh di cui è costituita.</span><span class="sxs-lookup"><span data-stu-id="3306b-239">Once SceneObjects have been found your application will most likely want to access the data that is contained n the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="3306b-240">Questi dati sono accessibili con le proprietà ***Quad*** e ***mesh*** .</span><span class="sxs-lookup"><span data-stu-id="3306b-240">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="3306b-241">Il codice seguente enumera tutti i quad e le maglie dell'oggetto Floor.</span><span class="sxs-lookup"><span data-stu-id="3306b-241">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the matrix for the SceneObject
System.Numerics.Matrix4x4 floorTransform = firstFloor.LocationAsMatrix();

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

<span data-ttu-id="3306b-242">Si noti che si tratta del SceneObject con la trasformazione rispetto all'origine della scena.</span><span class="sxs-lookup"><span data-stu-id="3306b-242">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="3306b-243">Questo perché SceneObject rappresenta un'istanza di una "cosa" ed è locatable nello spazio, i quad e le mesh rappresentano la geometria che viene trasformata in relazione al rispettivo elemento padre.</span><span class="sxs-lookup"><span data-stu-id="3306b-243">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="3306b-244">È possibile che SceneObjects separate facciano riferimento allo stesso SceneComponewnts SceneMesh/SceneQuad ed è anche possibile che un SceneObject disponga di più di un SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="3306b-244">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponewnts, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="3306b-245">Gestione delle trasformazioni</span><span class="sxs-lookup"><span data-stu-id="3306b-245">Dealing with Transforms</span></span>

<span data-ttu-id="3306b-246">La comprensione della scena ha effettuato un tentativo intenzionale di allinearsi alle rappresentazioni tradizionali della scena 3D quando si gestiscono le trasformazioni.</span><span class="sxs-lookup"><span data-stu-id="3306b-246">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="3306b-247">Ogni scena è quindi confinata a un singolo sistema di coordinate, in modo analogo alla maggior parte delle rappresentazioni ambientali 3D.</span><span class="sxs-lookup"><span data-stu-id="3306b-247">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="3306b-248">Se l'applicazione sta affrontando scenari che estendono il limite di una singola origine, può ancorare SceneObjects a SpatialAnchors o generare diverse scene e unirle, ma per semplicità si presuppone che le scene stagne esistano nei propri origine localizzata da un NodeId definito da scene:: OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="3306b-248">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene::OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="3306b-249">Il codice Unity seguente, ad esempio, Mostra come usare la percezione di Windows e le API Unity per allineare i sistemi di Coordinate:</span><span class="sxs-lookup"><span data-stu-id="3306b-249">The following unity code, for example, shows how to use windows perception and Unity APIs to align coordinate systems together:</span></span>


```cs
    public static System.Numerics.Matrix4x4? GetSceneToUnityTransform(Guid nodeId)
    {
        System.Numerics.Matrix4x4? sceneToUnityTransform; 
       
        SpatialCoordinateSystem sceneSpatialCoordinateSystem = Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(nodeId);
        SpatialCoordinateSystem unitySpatialCoordinateSystem = (SpatialCoordinateSystem)System.Runtime.InteropServices.Marshal.GetObjectForIUnknown(UnityEngine.XR.WSA.WorldManager.GetNativeISpatialCoordinateSystemPtr());

        sceneToUnityTransform = sceneSpatialCoordinateSystem.TryGetTransformTo(unitySpatialCoordinateSystem);

        if (sceneToUnityTransform != null)
        {
            sceneToUnityTransform = TransformUtils.ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
        }
        
        return sceneToUnityTransform;
    }

    // Converts from right-handed to left handed coordinates
    public System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 transformationMatrix)
    {
        transformationMatrix.M13 = -transformationMatrix.M13;
        transformationMatrix.M23 = -transformationMatrix.M23;
        transformationMatrix.M43 = -transformationMatrix.M43;

        transformationMatrix.M31 = -transformationMatrix.M31;
        transformationMatrix.M32 = -transformationMatrix.M32;
        transformationMatrix.M34 = -transformationMatrix.M34;

        return transformationMatrix;
    }
```

<span data-ttu-id="3306b-250">E il codice seguente chiama questa funzione:</span><span class="sxs-lookup"><span data-stu-id="3306b-250">And the following code calls this function:</span></span>

```cs
System.Numerics.Matrix4x4? sceneToUnityTransform = TransformUtils.GetSceneToUnityTransform(scene.OriginSpatialGraphNodeId);

// Set the root transform
Vector3 t;
Quaternion r;
Vector3 s;

System.Numerics.Matrix4x4.Decompose(sceneToUnityTransform, out s, out r, out t);
SceneRoot.Transform.SetPositionAndRotation(t, r);
```

### <a name="quad"></a><span data-ttu-id="3306b-251">Quad</span><span class="sxs-lookup"><span data-stu-id="3306b-251">Quad</span></span>

<span data-ttu-id="3306b-252">I quad sono stati progettati per semplificare gli scenari di posizionamento 2D e dovrebbero essere considerati come estensioni per gli elementi UX di Canvas 2D.</span><span class="sxs-lookup"><span data-stu-id="3306b-252">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="3306b-253">Mentre i quad sono componenti di SceneObjects e possono essere sottoposti a rendering in 3D, le API quadre presuppongono quad sono strutture 2D.</span><span class="sxs-lookup"><span data-stu-id="3306b-253">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="3306b-254">Offrono informazioni come extent, Shape e forniscono API per la selezione host.</span><span class="sxs-lookup"><span data-stu-id="3306b-254">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="3306b-255">I quad hanno extent rettangolari, ma rappresentano superfici 2D a forma arbitraria.</span><span class="sxs-lookup"><span data-stu-id="3306b-255">Quads have rectangular extents, but they represent arbitrarily shaped 2d surfaces.</span></span> <span data-ttu-id="3306b-256">Per abilitare la selezione host in queste superfici 2D che interagiscono con i quad dell'ambiente 3D offrono utilità per rendere possibile questa interazione.</span><span class="sxs-lookup"><span data-stu-id="3306b-256">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="3306b-257">Attualmente la comprensione della scena fornisce due funzioni di questo tipo, **FindCentermostPlacement** e **GetOcclusionMask**.</span><span class="sxs-lookup"><span data-stu-id="3306b-257">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="3306b-258">FindCentermostPlacement è un'API di alto livello che individua una posizione nel quad in cui è possibile posizionare un oggetto e tenterà di trovare la posizione migliore per l'oggetto, garantendo che il rettangolo di delimitazione fornito si trovi sulla superficie sottostante.</span><span class="sxs-lookup"><span data-stu-id="3306b-258">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="3306b-259">Nell'esempio seguente viene illustrato come trovare la posizione posizionabile effettuare e come ancorare un ologramma al quad.</span><span class="sxs-lookup"><span data-stu-id="3306b-259">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

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
                // Step 1: Create a new node QuadTransformNode as a child of Root, and set the transform from quad[0].Transform
                // Step 2: Create your hologram and set it as a child of QuadTransformNode
                // Step 3: Set the QuadTransformNode tranform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="3306b-260">I passaggi 1-3 dipendono in modo estremamente da un particolare Framework/implementazione, ma i temi dovrebbero essere simili.</span><span class="sxs-lookup"><span data-stu-id="3306b-260">Steps 1-3 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="3306b-261">È importante notare che il quad non è in genere progettato per essere, rappresenta semplicemente un piano 2D con binding localizzato nello spazio.</span><span class="sxs-lookup"><span data-stu-id="3306b-261">It is important to note that the Quad is not usually intended to be, is just represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="3306b-262">Se il motore/Framework sa dove si trova il quad e si radicano gli oggetti rispetto al quad, gli ologrammi verranno posizionati correttamente.</span><span class="sxs-lookup"><span data-stu-id="3306b-262">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly.</span></span> <span data-ttu-id="3306b-263">Per informazioni più dettagliate, vedere gli esempi su quad che mostrano implementazioni specifiche.</span><span class="sxs-lookup"><span data-stu-id="3306b-263">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="3306b-264">Mesh</span><span class="sxs-lookup"><span data-stu-id="3306b-264">Mesh</span></span>

<span data-ttu-id="3306b-265">Le mesh rappresentano rappresentazioni geometriche di oggetti o ambienti.</span><span class="sxs-lookup"><span data-stu-id="3306b-265">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="3306b-266">In modo analogo al [mapping spaziale](spatial-mapping.md), i dati relativi a indici mesh e vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei vertex buffer e degli indici utilizzati per il rendering di mesh triangolari in tutte le moderne API per il rendering.</span><span class="sxs-lookup"><span data-stu-id="3306b-266">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="3306b-267">Le API specifiche usate per fare riferimento a questi dati sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="3306b-267">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(float[] vertices);
```

<span data-ttu-id="3306b-268">\* \* Nota: Getvertici restituisce un elenco di vertici in cui ogni tupla con 3 Tuple di valori a virgola mobile rappresenta una singola coordinata nello spazio cartesiano x, y e z.</span><span class="sxs-lookup"><span data-stu-id="3306b-268">\*\*Note: GetVertices returns a list of vertices where every 3-tuple of floating point values represents a single coordinate in cartesian x,y and z space.</span></span>

<span data-ttu-id="3306b-269">Il codice seguente fornisce un esempio di generazione di un elenco di triangolo dalla struttura mesh:</span><span class="sxs-lookup"><span data-stu-id="3306b-269">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
float[] positions = new float[mesh.VertexCount * 3];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="3306b-270">I buffer di indice/vertice devono essere > = i conteggi di indice/vertice, ma in caso contrario possono essere dimensionati arbitrariamente, consentendo un utilizzo efficace della memoria.</span><span class="sxs-lookup"><span data-stu-id="3306b-270">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

### <a name="developing-with-scene-understandings"></a><span data-ttu-id="3306b-271">Sviluppo con informazioni sulle scene</span><span class="sxs-lookup"><span data-stu-id="3306b-271">Developing with Scene Understandings</span></span>

<span data-ttu-id="3306b-272">A questo punto è necessario comprendere i componenti di base della scena Understanding Runtime and SDK.</span><span class="sxs-lookup"><span data-stu-id="3306b-272">At this point you should understand the core building blocks of the Scene Understanding runtime and SDK.</span></span> <span data-ttu-id="3306b-273">La maggior parte della potenza e della complessità si basa sui modelli di accesso, sull'interazione con i framework 3D e sugli strumenti che possono essere scritti su queste API per eseguire attività più avanzate come la pianificazione spaziale, l'analisi delle stanze, la navigazione, la fisica e così via. Ci auguriamo che questi esempi vengano acquisiti in esempi che dovrebbero guidare l'utente nella direzione corretta per rendere più brillanti gli scenari.</span><span class="sxs-lookup"><span data-stu-id="3306b-273">The bulk of the power and complexity lies in access patterns, interaction with 3d frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc... We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="3306b-274">Se sono presenti esempi/scenari non indirizzati, è possibile inviare una notifica e provare a documentare/prototipare gli elementi necessari.</span><span class="sxs-lookup"><span data-stu-id="3306b-274">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="3306b-275">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3306b-275">See also</span></span>

* [<span data-ttu-id="3306b-276">mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="3306b-276">spatial mapping</span></span>](spatial-mapping.md)
