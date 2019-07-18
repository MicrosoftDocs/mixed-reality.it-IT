---
title: Modulo MR Learning ASA-Azure Spatial Anchor su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: c6e902710eebe205b9e944b1bf95a9ddd3bd9044
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293810"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="58fcc-104">Visualizzazione del feedback di ancoraggio spaziale di Azure</span><span class="sxs-lookup"><span data-stu-id="58fcc-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="58fcc-105">In questa lezione verranno illustrate le procedure per fornire agli utenti il feedback sull'individuazione di ancoraggio, sugli eventi e sullo stato quando si usano gli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="58fcc-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="58fcc-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="58fcc-106">Objectives:</span></span>

* <span data-ttu-id="58fcc-107">Informazioni su come configurare un pannello dell'interfaccia utente che visualizza informazioni importanti sulla sessione ASA corrente</span><span class="sxs-lookup"><span data-stu-id="58fcc-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="58fcc-108">Comprendere ed esplorare gli elementi di feedback che l'SDK ASA rende disponibili agli utenti</span><span class="sxs-lookup"><span data-stu-id="58fcc-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="58fcc-109">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="58fcc-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="58fcc-110">Configurare il pannello dell'interfaccia utente del feedback ASA</span><span class="sxs-lookup"><span data-stu-id="58fcc-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="58fcc-111">In questa lezione non verranno usati i pulsanti "SaveAnchorToDisk" e "ShareAnchor", quindi selezionare entrambi i pulsanti e deselezionare la casella di controllo nel pannello Inspector (come illustrato di seguito) per nascondere questi pulsanti.</span><span class="sxs-lookup"><span data-stu-id="58fcc-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="58fcc-113">Successivamente, creare il pannello di istruzioni.</span><span class="sxs-lookup"><span data-stu-id="58fcc-113">Next, create the instruction panel.</span></span> <span data-ttu-id="58fcc-114">Per iniziare, fare clic con il pulsante destro del mouse sul pulsante "istruzioni", passare il puntatore su "oggetto 3D" e selezionare "textmeshpro-Text".</span><span class="sxs-lookup"><span data-stu-id="58fcc-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="58fcc-116">Regolare la scala e il posizionamento del testo in modo che corrisponda alle istruzioni della scena.</span><span class="sxs-lookup"><span data-stu-id="58fcc-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="58fcc-117">Assicurarsi inoltre che l'allineamento per tutto il testo sia centrato.</span><span class="sxs-lookup"><span data-stu-id="58fcc-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="58fcc-118">Eliminare quindi il testo di esempio dall'editor di testo, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="58fcc-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="58fcc-120">Modificare il nome dell'oggetto TextMeshPro in "FeedbackPanel".</span><span class="sxs-lookup"><span data-stu-id="58fcc-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="58fcc-122">Nel pannello progetto selezionare "asset" e fare clic con il pulsante destro del mouse, quindi selezionare "Mostra in Esplora".</span><span class="sxs-lookup"><span data-stu-id="58fcc-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="58fcc-124">A questo punto, fare clic [qui](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) per scaricare i file necessari nei passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="58fcc-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="58fcc-125">Una volta aperta la finestra di esplorazione, selezionare la cartella assets, quindi la cartella "ASAmodulesAssets" e copiare lo script di ancoraggio feedback e i file script del modulo di ancoraggio nella cartella.</span><span class="sxs-lookup"><span data-stu-id="58fcc-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="58fcc-127">Nota: se viene visualizzata una finestra popup in cui viene chiesto se si desidera sovrascrivere il vecchio o conservare il vecchio, assicurarsi di selezionare Sovrascrivi.</span><span class="sxs-lookup"><span data-stu-id="58fcc-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="58fcc-128">Tornare ora alla cartella assets.</span><span class="sxs-lookup"><span data-stu-id="58fcc-128">Now return to the Assets folder.</span></span> <span data-ttu-id="58fcc-129">Passare quindi alla cartella "AzureSpatialAnchorsPlugin", alla cartella Examples e infine alla cartella Scripts e copiare il wrapper demo di Azure Spatial Anchors in tale cartella.</span><span class="sxs-lookup"><span data-stu-id="58fcc-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="58fcc-131">Ora che i file sono stati caricati, assicurarsi che sia selezionato il testo "feedbackpanel", nella gerarchia di ASA_feedback e fare clic su "Aggiungi componente" e aggiungere lo script per il feedback di ancoraggio cercandolo e selezionando il testo quando viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="58fcc-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="58fcc-133">Trascinare l'oggetto testo "feedbackPanel" dalla gerarchia ASA_Feedback nello slot vuoto sotto lo script, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="58fcc-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="58fcc-135">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="58fcc-135">Congratulations</span></span>

<span data-ttu-id="58fcc-136">In questa lezione è stato illustrato come creare un pannello dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di ancoraggio spaziale di Azure per fornire all'utente un feedback in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="58fcc-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


