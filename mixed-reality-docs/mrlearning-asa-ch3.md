---
title: Esercitazioni sugli ancoraggi spaziali di Azure-3. Visualizzazione del feedback di ancoraggio spaziale di Azure
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 19529cbfebd74938395545c329097d42b5af9ff9
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334405"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="6f229-105">3. Visualizzazione del feedback di ancoraggio spaziale di Azure</span><span class="sxs-lookup"><span data-stu-id="6f229-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="6f229-106">In questa lezione si apprenderà come fornire agli utenti feedback sull'individuazione di ancoraggio, sugli eventi e sullo stato quando si usano gli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="6f229-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="6f229-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6f229-107">Objectives</span></span>

* <span data-ttu-id="6f229-108">Informazioni su come configurare un pannello dell'interfaccia utente che visualizza informazioni importanti sulla sessione ASA corrente</span><span class="sxs-lookup"><span data-stu-id="6f229-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="6f229-109">Comprendere ed esplorare gli elementi di feedback che l'SDK ASA rende disponibili agli utenti</span><span class="sxs-lookup"><span data-stu-id="6f229-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="6f229-110">Configurare il pannello dell'interfaccia utente del feedback ASA</span><span class="sxs-lookup"><span data-stu-id="6f229-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="6f229-111">In questa lezione non verranno usati i pulsanti "SaveAnchorToDisk" e "ShareAnchor", quindi selezionare entrambi i pulsanti e deselezionare la casella di controllo nel pannello Inspector (come illustrato di seguito) per nascondere questi pulsanti.</span><span class="sxs-lookup"><span data-stu-id="6f229-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>

    ![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="6f229-113">Creare il pannello di istruzioni.</span><span class="sxs-lookup"><span data-stu-id="6f229-113">Create the instruction panel.</span></span> <span data-ttu-id="6f229-114">Per iniziare, fare clic con il pulsante destro del mouse sul pulsante "istruzioni", passare il puntatore su "oggetto 3D" e selezionare "textmeshpro-Text".</span><span class="sxs-lookup"><span data-stu-id="6f229-114">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

    ![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="6f229-116">Modificare la scala e il posizionamento del testo, in modo che corrisponda alle istruzioni della scena.</span><span class="sxs-lookup"><span data-stu-id="6f229-116">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="6f229-117">Assicurarsi inoltre che l'allineamento per tutto il testo sia centrato.</span><span class="sxs-lookup"><span data-stu-id="6f229-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="6f229-118">Eliminare quindi il testo di esempio dall'editor di testo, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="6f229-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

    ![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="6f229-120">Modificare il nome dell'oggetto TextMeshPro in "FeedbackPanel".</span><span class="sxs-lookup"><span data-stu-id="6f229-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>

    ![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="6f229-122">Verificare che nel ASA_feedback gerarchia sia selezionato il testo "feedbackpanel", fare clic su "Aggiungi componente" e aggiungere lo script per il feedback di ancoraggio cercandolo e selezionando il testo quando viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="6f229-122">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span>

    ![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="6f229-124">Trascinare l'oggetto testo "feedbackPanel" dalla gerarchia di ASA_Feedback nello slot vuoto sotto lo script, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="6f229-124">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span>

    ![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="6f229-126">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="6f229-126">Congratulations</span></span>

<span data-ttu-id="6f229-127">In questa lezione è stato illustrato come creare un pannello dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di ancoraggio spaziale di Azure per fornire agli utenti il feedback in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="6f229-127">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
