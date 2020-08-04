---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 4. Visualizzazione del feedback su Ancoraggi nello spazio di Azure
description: Completare questo corso per imparare a implementare Ancoraggi nello spazio di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: afcd7753fb2296503e67a1977b183df951124560
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376523"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="5e19c-105">4. Visualizzazione del feedback su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="5e19c-105">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="5e19c-106">In questa esercitazione si apprenderà come fornire agli utenti feedback su individuazione, eventi e stato degli ancoraggi con Ancoraggi nello spazio di Azure (ASA).</span><span class="sxs-lookup"><span data-stu-id="5e19c-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="5e19c-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="5e19c-107">Objectives</span></span>

* <span data-ttu-id="5e19c-108">Imparare a configurare un riquadro dell'interfaccia utente in cui vengono visualizzate informazioni fondamentali sulla sessione ASA corrente</span><span class="sxs-lookup"><span data-stu-id="5e19c-108">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="5e19c-109">Imparare ed esplorare gli elementi di feedback che ASA SDK mette a disposizione degli utenti</span><span class="sxs-lookup"><span data-stu-id="5e19c-109">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="5e19c-110">Configurazione del riquadro per il feedback di ASA</span><span class="sxs-lookup"><span data-stu-id="5e19c-110">Setting up ASA feedback panel</span></span>

<span data-ttu-id="5e19c-111">Nella finestra Hierarchy (Gerarchia) fare clic con il pulsante destro del mouse sull'oggetto **Instructions** (Istruzioni)  > **TextContent**.</span><span class="sxs-lookup"><span data-stu-id="5e19c-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="5e19c-112">Selezionare **3D Object** (Oggetto 3D)  > **Text (Testo) - TextMeshPro** per creare un oggetto testo TextMeshPro come figlio dell'oggetto Instructions (Istruzioni) > TextContent:</span><span class="sxs-lookup"><span data-stu-id="5e19c-112">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="5e19c-114">Per rendere più agevole l'uso della scena, disattiva la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità</a> per l'oggetto ParentAnchor facendo clic sull'icona a forma di occhio a sinistra dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5e19c-114">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="5e19c-115">In questo modo, l'oggetto viene nascosto nella finestra Scene (Scena) senza effetti sulla sua visibilità nel gioco.</span><span class="sxs-lookup"><span data-stu-id="5e19c-115">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="5e19c-116">Rinominare l'oggetto Text (TMP) appena creato **Feedback** e quindi, modificare la relativa dimensione e posizione nella finestra Inspector (Controllo), in modo che l'oggetto venga posizionato perfettamente sotto il testo dell'istruzione, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="5e19c-116">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="5e19c-117">Modificare il valore di **Pos Y** (Posizione Y) per il componente Rect Transform (Trasformazione rettangolo) impostandolo su -0,24.</span><span class="sxs-lookup"><span data-stu-id="5e19c-117">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="5e19c-118">Modificare il valore di **Width** (Larghezza) per il componente Rect Transform (Trasformazione rettangolo) impostandolo su 0,555.</span><span class="sxs-lookup"><span data-stu-id="5e19c-118">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="5e19c-119">Modificare il valore di **Height** (Altezza) per il componente Rect Transform (Trasformazione rettangolo) impostandolo su -0,1.</span><span class="sxs-lookup"><span data-stu-id="5e19c-119">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="5e19c-120">Scegliere quindi le proprietà del tipo di carattere, in modo da adattare bene il testo all'interno dell'area di testo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="5e19c-120">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="5e19c-121">Modificare il valore di **Font Style** (Stile carattere) per il componente TextMeshPro - Text (Testo) impostandolo su Bold (Grassetto).</span><span class="sxs-lookup"><span data-stu-id="5e19c-121">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="5e19c-122">Modificare il valore di **Font Size** (Dimensioni carattere) per il componente TextMeshPro - Text (Testo) impostandolo su 0,17.</span><span class="sxs-lookup"><span data-stu-id="5e19c-122">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="5e19c-123">Modificare il valore di **Alignment** (Allineamento) per il componente TextMeshPro - Text (Testo) impostandolo su Center (Al centro verticalmente) e Middle (Al centro orizzontalmente).</span><span class="sxs-lookup"><span data-stu-id="5e19c-123">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="5e19c-125">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **Feedback** e quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente), per aggiungere il componente **Anchor Feedback Script (Script)** (Script di feedback Ancoraggi - Script) e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5e19c-125">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="5e19c-126">Assegnare l'oggetto **Feedback** stesso al campo **Feedback Text** (Testo feedback) del componente **Anchor Feedback Script (Script)** (Script di feedback Ancoraggi - Script).</span><span class="sxs-lookup"><span data-stu-id="5e19c-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="5e19c-128">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="5e19c-128">Congratulations</span></span>

<span data-ttu-id="5e19c-129">In questa esercitazione si è appreso come creare un pannello dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="5e19c-129">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="5e19c-130">Questo pannello visualizza lo stato corrente dell'esperienza di Ancoraggi nello spazio di Azure per fornire agli utenti feedback in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="5e19c-130">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

[<span data-ttu-id="5e19c-131">Esercitazione successiva: 5. Ancoraggi nello spazio di Azure per Android e iOS</span><span class="sxs-lookup"><span data-stu-id="5e19c-131">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
