---
title: Esercitazioni su Ancoraggi nello spazio di Azure - 3. Visualizzazione del feedback su Ancoraggi nello spazio di Azure
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 11342bada65e963db6393d35c99e2c2fbffe8ff1
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031257"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="f9443-105">3. Visualizzazione del feedback su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="f9443-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="f9443-106">In questa esercitazione apprenderai come fornire agli utenti feedback su individuazione, eventi e stato degli ancoraggi con Ancoraggi nello spazio di Azure (ASA).</span><span class="sxs-lookup"><span data-stu-id="f9443-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="f9443-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f9443-107">Objectives</span></span>

* <span data-ttu-id="f9443-108">Imparare a configurare un riquadro dell'interfaccia utente in cui vengono visualizzate informazioni importanti sulla sessione ASA corrente</span><span class="sxs-lookup"><span data-stu-id="f9443-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="f9443-109">Comprendere ed esplorare gli elementi di feedback che l'SDK di ASA mette a disposizione degli utenti</span><span class="sxs-lookup"><span data-stu-id="f9443-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="f9443-110">Configurare il riquadro dell'interfaccia utente per il feedback ASA</span><span class="sxs-lookup"><span data-stu-id="f9443-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="f9443-111">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su **Instructions** > **TextContent** (Istruzioni > TextContent) e scegli **3D Object** > **Text - TextMeshPro** (Oggetto 3D > Testo - TextMeshPro) per creare un oggetto di testo TextMeshPro come elemento figlio di Instructions > TextContent (Istruzioni > TextContent) e assegnargli un nome appropriato, ad esempio **Feedback**:</span><span class="sxs-lookup"><span data-stu-id="f9443-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="f9443-113">Per rendere più agevole l'uso della scena, disattiva la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilità</a> per l'oggetto ParentAnchor facendo clic sull'icona a forma di occhio a sinistra dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="f9443-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="f9443-114">In questo modo, l'oggetto viene nascosto nella finestra Scene (Scena) senza effetti sulla sua visibilità nel gioco.</span><span class="sxs-lookup"><span data-stu-id="f9443-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="f9443-115">Mantenendo l'oggetto **Feedback** selezionato, modifica le relative dimensioni e posizione nella finestra Inspector (Controllo), in modo che tale oggetto venga posizionato perfettamente sotto il testo dell'istruzione, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f9443-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="f9443-116">Modifica il valore di **Pos Y** per Rect Transform (Trasformazione rettangolo) impostandolo su -0.24</span><span class="sxs-lookup"><span data-stu-id="f9443-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="f9443-117">Modifica il valore di **Width** (Larghezza) per Rect Transform (Trasformazione rettangolo) impostandolo su 0.555</span><span class="sxs-lookup"><span data-stu-id="f9443-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="f9443-118">Modifica il valore di **Height** (Altezza) per Rect Transform (Trasformazione rettangolo) impostandolo su 0.1</span><span class="sxs-lookup"><span data-stu-id="f9443-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="f9443-119">Scegli quindi le proprietà del tipo di carattere, in modo da adattare bene il testo all'interno dell'area di testo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f9443-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="f9443-120">Modifica il valore di **Font Style** (Stile carattere) per Text Mesh Pro (Script) impostandolo su Bold (Grassetto)</span><span class="sxs-lookup"><span data-stu-id="f9443-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="f9443-121">Modifica il valore di **Font Size** (Dimensione carattere) per Text Mesh Pro (Script) impostandolo su 0.17</span><span class="sxs-lookup"><span data-stu-id="f9443-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="f9443-122">Modifica il valore di **Alignment** (Allineamento) impostandolo su Center (Al centro) e Middle (In mezzo)</span><span class="sxs-lookup"><span data-stu-id="f9443-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="f9443-124">Con l'oggetto **Feedback** ancora selezionato, nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Anchor Feedback Script (Script)** (Script di feedback Ancoraggi - Script) all'oggetto Feedback:</span><span class="sxs-lookup"><span data-stu-id="f9443-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="f9443-126">Assegna l'oggetto **Feedback** stesso al campo **Feedback Text** (Testo feedback) del componente **Anchor Feedback Script (Script)** (Script di feedback Ancoraggi - Script).</span><span class="sxs-lookup"><span data-stu-id="f9443-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="f9443-128">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="f9443-128">Congratulations</span></span>

<span data-ttu-id="f9443-129">In questa esercitazione hai appreso come creare un riquadro dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di Ancoraggi nello spazio di Azure e fornire agli utenti feedback in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="f9443-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
