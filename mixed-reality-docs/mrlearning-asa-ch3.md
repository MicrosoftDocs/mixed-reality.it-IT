---
title: Esercitazioni sugli ancoraggi spaziali di Azure-3. Visualizzazione del feedback di ancoraggio spaziale di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553939"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="2739b-105">3. Visualizzazione del feedback di ancoraggio spaziale di Azure</span><span class="sxs-lookup"><span data-stu-id="2739b-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="2739b-106">In questa esercitazione si apprenderà come fornire agli utenti feedback sull'individuazione, sugli eventi e sullo stato di ancoraggio quando si usano gli ancoraggi di Azure Spatial (ASA).</span><span class="sxs-lookup"><span data-stu-id="2739b-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="2739b-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="2739b-107">Objectives</span></span>

* <span data-ttu-id="2739b-108">Informazioni su come configurare un pannello dell'interfaccia utente che visualizza informazioni importanti sulla sessione ASA corrente</span><span class="sxs-lookup"><span data-stu-id="2739b-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="2739b-109">Comprendere ed esplorare gli elementi di feedback che l'SDK ASA rende disponibili agli utenti</span><span class="sxs-lookup"><span data-stu-id="2739b-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="2739b-110">Configurare il pannello dell'interfaccia utente del feedback ASA</span><span class="sxs-lookup"><span data-stu-id="2739b-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="2739b-111">Nella finestra gerarchia, fare clic con il pulsante destro del mouse sulle **istruzioni** > oggetto **textContent** e selezionare **oggetto 3D** > **Text-TextMeshPro** per creare un oggetto di testo TextMeshPro come figlio delle istruzioni > oggetto TextContent e assegnargli un nome appropriato, ad esempio, **feedback**:</span><span class="sxs-lookup"><span data-stu-id="2739b-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="2739b-113">Per semplificare l'uso della scena, impostare la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità della scena</a> per l'oggetto ParentAnchor su off facendo clic sull'icona a occhi a sinistra dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2739b-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="2739b-114">In questo modo, l'oggetto viene nascosto nella finestra della scena senza modificare la visibilità del gioco.</span><span class="sxs-lookup"><span data-stu-id="2739b-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="2739b-115">Con l'oggetto **feedback** ancora selezionato, nella finestra di controllo modificare la posizione e le dimensioni in modo che venga posizionato perfettamente sotto il testo dell'istruzione, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="2739b-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="2739b-116">Modificare la trasformazione Rect **pos Y** in-0,24</span><span class="sxs-lookup"><span data-stu-id="2739b-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="2739b-117">Modificare la **larghezza** della trasformazione Rect in 0,555</span><span class="sxs-lookup"><span data-stu-id="2739b-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="2739b-118">Modificare l' **altezza** di trasformazione Rect in 0,1</span><span class="sxs-lookup"><span data-stu-id="2739b-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="2739b-119">Quindi scegliere Proprietà carattere in modo che il testo si trovi perfettamente all'interno dell'area di testo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="2739b-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="2739b-120">Modificare lo **stile del tipo di carattere** text mesh Pro (script) in grassetto</span><span class="sxs-lookup"><span data-stu-id="2739b-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="2739b-121">Modificare le **dimensioni del tipo di carattere** text mesh Pro (script) in 0,17</span><span class="sxs-lookup"><span data-stu-id="2739b-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="2739b-122">Modificare l' **allineamento** di Text mesh Pro (script) in centro e al centro</span><span class="sxs-lookup"><span data-stu-id="2739b-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="2739b-124">Con l'oggetto **feedback** ancora selezionato, nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente script di **ancoraggio feedback (script)** all'oggetto feedback:</span><span class="sxs-lookup"><span data-stu-id="2739b-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="2739b-126">Assegnare l'oggetto **feedback** a se stesso al campo **testo feedback** **dello script di ancoraggio (script)** del componente:</span><span class="sxs-lookup"><span data-stu-id="2739b-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="2739b-128">Complimenti</span><span class="sxs-lookup"><span data-stu-id="2739b-128">Congratulations</span></span>

<span data-ttu-id="2739b-129">In questa esercitazione si è appreso come creare un pannello dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di ancoraggio spaziale di Azure per fornire agli utenti il feedback in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="2739b-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
