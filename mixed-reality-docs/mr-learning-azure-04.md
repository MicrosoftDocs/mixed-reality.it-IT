---
title: Esercitazioni sul cloud di Azure - 4. Integrazione di Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come implementare Ancoraggi nello spazio di Azure in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, Ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: 4eac2b96519abeebc277a53ad83d1b6dec8d61fd
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304932"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="fabc1-105">4. Integrazione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="fabc1-105">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="fabc1-106">In questa esercitazione verrà spiegato come usare **Ancoraggi nello spazio di Azure**.</span><span class="sxs-lookup"><span data-stu-id="fabc1-106">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="fabc1-107">Si archivierà la posizione di un **oggetto tracciato** come oggetto di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="fabc1-107">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="fabc1-108">Quindi si eseguirà una query e si presenterà all'utente una freccia guida che punta alla posizione.</span><span class="sxs-lookup"><span data-stu-id="fabc1-108">Then you will query and present the user with a guiding arrow pointing to the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="fabc1-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="fabc1-109">Objectives</span></span>

* <span data-ttu-id="fabc1-110">Acquisire le nozioni di base su Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="fabc1-110">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="fabc1-111">Imparare a impostare la scena per l'uso di Ancoraggi nello spazio di Azure in questo progetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-111">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="fabc1-112">Scoprire come integrare le posizioni di archiviazione e query.</span><span class="sxs-lookup"><span data-stu-id="fabc1-112">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="fabc1-113">Informazioni su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="fabc1-113">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="fabc1-114">**Ancoraggi nello spazio di Azure** fa parte della famiglia di Servizi cloud di Azure e viene utilizzato per salvare posizioni di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="fabc1-114">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="fabc1-115">Le posizioni di ancoraggio salvate possono essere recuperate in base all'*ID di ancoraggio* dal cloud.</span><span class="sxs-lookup"><span data-stu-id="fabc1-115">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="fabc1-116">Questa posizione di ancoraggio è condivisibile e accessibile da dispositivi multipiattaforma come i dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="fabc1-116">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="fabc1-117">Altre informazioni su [Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="fabc1-117">Learn more about [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="fabc1-118">Preparazione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="fabc1-118">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="fabc1-119">Prima di iniziare, è necessario creare una risorsa di ancoraggio nello spazio nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="fabc1-119">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="fabc1-120">Vedere come [creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span><span class="sxs-lookup"><span data-stu-id="fabc1-120">Learn how to make a [spatial anchor resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="fabc1-121">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="fabc1-121">Preparing the scene</span></span>

<span data-ttu-id="fabc1-122">In questa sezione verrà illustrato come configurare la scena e apportare le modifiche necessarie.</span><span class="sxs-lookup"><span data-stu-id="fabc1-122">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="fabc1-123">Nella finestra Project (Progetto) passa a **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span><span class="sxs-lookup"><span data-stu-id="fabc1-123">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="fabc1-125">Dalla cartella **Manager** trascinare e rilasciare il prefab **Anchor Manager** (Gestione ancoraggi) nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="fabc1-125">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="fabc1-126">Selezionare il GameObject **Anchor Manager** nella gerarchia e nella sezione Inspector (Controllo) si noterà **Spatial Anchor Manager** (Script).</span><span class="sxs-lookup"><span data-stu-id="fabc1-126">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="fabc1-127">Trovare il campo ID account chiave e aggiungere le credenziali che create nel prerequisito nella fase precedente.</span><span class="sxs-lookup"><span data-stu-id="fabc1-127">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="fabc1-129">Ora trovare l'oggetto **Scene Controller** (Controllo scena) nella gerarchia della scena e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="fabc1-129">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="fabc1-130">Verrà visualizzata la finestra Inspector (Controllo) di **Scene Controller** (Controllo scena).</span><span class="sxs-lookup"><span data-stu-id="fabc1-130">You will see the **Scene Controller** Inspector.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="fabc1-132">Si osserverà che il campo **Anchor Manager** (Gestione ancoraggi) nel componente **Scene Controller** (Controllo scena) è vuoto. Trascinare **Anchor Manager** (Gestione ancoraggi) da Hierarchy (Gerarchia) nella scena, rilasciarlo nel campo e salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="fabc1-132">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="fabc1-133">Creare e distribuire l'app in un dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fabc1-133">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="fabc1-134">Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity. Pertanto, per testare la funzionalità di questo servizio devi distribuire il progetto nel tuo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fabc1-134">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="fabc1-135">Per un promemoria su come compilare e distribuire il progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilare l'applicazione nel dispositivo](mr-learning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="fabc1-135">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mr-learning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="fabc1-136">Eseguire l'app in HoloLens 2 e seguire le istruzioni in-app</span><span class="sxs-lookup"><span data-stu-id="fabc1-136">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="fabc1-137">Creare un ancoraggio per archiviare una posizione</span><span class="sxs-lookup"><span data-stu-id="fabc1-137">Create an anchor to store a location</span></span>

<span data-ttu-id="fabc1-138">In questa sezione verrà illustrato come salvare la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-138">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="fabc1-139">Eseguire l'applicazione e fare clic su **Set Object** (Imposta oggetto) nel menu principale dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="fabc1-139">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="fabc1-140">Specificare il **nome** dell'oggetto da salvare e fare clic su **Set Object** (Imposta oggetto) per proseguire.</span><span class="sxs-lookup"><span data-stu-id="fabc1-140">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="fabc1-141">Per aggiungere altre informazioni sull'oggetto, selezionare l'**immagine** e descrivere l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-141">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="fabc1-142">Per salvare la posizione, fare clic su **Save Location** (Salva posizione)</span><span class="sxs-lookup"><span data-stu-id="fabc1-142">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="fabc1-143">Viene visualizzato un **puntatore di ancoraggio** che è possibile spostare e posizionare nella posizione da salvare.</span><span class="sxs-lookup"><span data-stu-id="fabc1-143">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="fabc1-144">Successivamente, viene visualizzata una finestra popup di conferma.</span><span class="sxs-lookup"><span data-stu-id="fabc1-144">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="fabc1-145">Se si vuole confermare e salvare la posizione, fare clic su **Yes** (Sì); in caso contrario, è possibile modificare la posizione facendo clic su **No** e selezionando nuovamente la posizione.</span><span class="sxs-lookup"><span data-stu-id="fabc1-145">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="fabc1-146">Dopo avere confermato la posizione facendo clic su **Yes** (Sì), la posizione e l'ID di ancoraggio verranno salvati nell'archiviazione cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="fabc1-146">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="fabc1-147">Eseguito il salvataggio, verrà visualizzato il **tag dell'oggetto** nell'ancoraggio con il nome dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-147">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="fabc1-148">A questo punto, la posizione dell'oggetto è salvata correttamente.</span><span class="sxs-lookup"><span data-stu-id="fabc1-148">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="fabc1-149">Query per trovare una posizione di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="fabc1-149">Query for finding an anchor location</span></span>

<span data-ttu-id="fabc1-150">Dopo avere salvato la posizione di ancoraggio, è possibile trovarla selezionando **Search Object** (Cerca oggetto) nel menu principale.</span><span class="sxs-lookup"><span data-stu-id="fabc1-150">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="fabc1-151">Facendo clic su **Search Object** (Cerca oggetto), viene visualizzata una nuova finestra in cui occorre specificare il nome dell'oggetto da cercare.</span><span class="sxs-lookup"><span data-stu-id="fabc1-151">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="fabc1-152">Immettere il nome dell'oggetto e fare clic su **Search Object** (Cerca oggetto).</span><span class="sxs-lookup"><span data-stu-id="fabc1-152">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="fabc1-153">Se l'oggetto è stato salvato in precedenza ed è presente nel database, si otterrà la scheda dell'oggetto con tutti i dettagli che lo riguardano.</span><span class="sxs-lookup"><span data-stu-id="fabc1-153">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="fabc1-154">A questo punto è possibile fare clic su **Show Location** (Mostra posizione) per trovare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-154">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="fabc1-155">Dopo avere fatto clic su **Show Location** (Mostra percorso), il sistema eseguirà una query nella risorsa di archiviazione cloud alla ricerca dell'indirizzo dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-155">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="fabc1-156">Una volta recuperata a posizione, apparirà una **freccia** rivolta verso la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-156">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="fabc1-157">Seguire il segno della freccia fino a trovare la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-157">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="fabc1-158">Una volta trovato l'oggetto, nella parte superiore verrà visualizzato il nome dell'oggetto, il segno della freccia scomparirà e sarà possibile fare clic sul **tag dell'oggetto** per visualizzare i dettagli dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fabc1-158">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fabc1-159">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="fabc1-159">Congratulations</span></span>

<span data-ttu-id="fabc1-160">In questa esercitazione è stato illustrato come salvare e recuperare la posizione di un oggetto in HoloLens 2 con Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="fabc1-160">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="fabc1-161">Nell'esercitazione finale si imparerà a usare il **Servizio Azure Bot** per aggiungere il linguaggio naturale come nuovo metodo di interazione per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="fabc1-161">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

[<span data-ttu-id="fabc1-162">Esercitazione successiva: 5. Integrazione del servizio Azure Bot con LUIS</span><span class="sxs-lookup"><span data-stu-id="fabc1-162">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
