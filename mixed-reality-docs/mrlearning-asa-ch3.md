---
title: Esercitazioni sugli ancoraggi spaziali di Azure-3. Visualizzazione del feedback di ancoraggio spaziale di Azure
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438420"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="6de6b-105">3. Visualizzazione del feedback di ancoraggio spaziale di Azure</span><span class="sxs-lookup"><span data-stu-id="6de6b-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="6de6b-106">In questa lezione si apprenderà come fornire agli utenti feedback sull'individuazione di ancoraggio, sugli eventi e sullo stato quando si usano gli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="6de6b-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="6de6b-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="6de6b-107">Objectives</span></span>

* <span data-ttu-id="6de6b-108">Informazioni su come configurare un pannello dell'interfaccia utente che visualizza informazioni importanti sulla sessione ASA corrente</span><span class="sxs-lookup"><span data-stu-id="6de6b-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="6de6b-109">Comprendere ed esplorare gli elementi di feedback che l'SDK ASA rende disponibili agli utenti</span><span class="sxs-lookup"><span data-stu-id="6de6b-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="6de6b-110">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="6de6b-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="6de6b-111">Configurare il pannello dell'interfaccia utente del feedback ASA</span><span class="sxs-lookup"><span data-stu-id="6de6b-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="6de6b-112">In questa lezione non verranno usati i pulsanti "SaveAnchorToDisk" e "ShareAnchor", quindi selezionare entrambi i pulsanti e deselezionare la casella di controllo nel pannello Inspector (come illustrato di seguito) per nascondere questi pulsanti.</span><span class="sxs-lookup"><span data-stu-id="6de6b-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="6de6b-114">Creare il pannello di istruzioni.</span><span class="sxs-lookup"><span data-stu-id="6de6b-114">Create the instruction panel.</span></span> <span data-ttu-id="6de6b-115">Per iniziare, fare clic con il pulsante destro del mouse sul pulsante "istruzioni", passare il puntatore su "oggetto 3D" e selezionare "textmeshpro-Text".</span><span class="sxs-lookup"><span data-stu-id="6de6b-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="6de6b-117">Modificare la scala e il posizionamento del testo, in modo che corrisponda alle istruzioni della scena.</span><span class="sxs-lookup"><span data-stu-id="6de6b-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="6de6b-118">Assicurarsi inoltre che l'allineamento per tutto il testo sia centrato.</span><span class="sxs-lookup"><span data-stu-id="6de6b-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="6de6b-119">Eliminare quindi il testo di esempio dall'editor di testo, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="6de6b-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="6de6b-121">Modificare il nome dell'oggetto TextMeshPro in "FeedbackPanel".</span><span class="sxs-lookup"><span data-stu-id="6de6b-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="6de6b-123">Nel pannello progetto selezionare "asset" e fare clic con il pulsante destro del mouse, quindi selezionare "Mostra in Esplora".</span><span class="sxs-lookup"><span data-stu-id="6de6b-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="6de6b-125">Fare clic [qui](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) per scaricare i file necessari nei passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="6de6b-125">Click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="6de6b-126">Dopo aver aperto Esplora risorse, selezionare la cartella assets, quindi la cartella "ASAmodulesAssets" e copiare lo script di ancoraggio feedback e i file script del modulo di ancoraggio nella cartella.</span><span class="sxs-lookup"><span data-stu-id="6de6b-126">Once Explorer opens, select the Assets folder, then the "ASAmodulesAssets" folder and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="6de6b-128">Nota: se viene visualizzato un messaggio popup in cui viene chiesto se si desidera sovrascrivere il vecchio o conservare il vecchio, selezionare Sovrascrivi.</span><span class="sxs-lookup"><span data-stu-id="6de6b-128">note: if you get a pop-up message asking if you to overwrite the old or keep the old, select overwrite.</span></span>

7. <span data-ttu-id="6de6b-129">Tornare alla cartella assets.</span><span class="sxs-lookup"><span data-stu-id="6de6b-129">Return to the Assets folder.</span></span> <span data-ttu-id="6de6b-130">Passare quindi alla cartella "AzureSpatialAnchorsPlugin", seguita dalla cartella Examples e infine dalla cartella Scripts.</span><span class="sxs-lookup"><span data-stu-id="6de6b-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, followed by the Examples folder and finally the Scripts folder.</span></span> <span data-ttu-id="6de6b-131">Copiare quindi il wrapper demo di Azure Spatial Anchors in tale cartella.</span><span class="sxs-lookup"><span data-stu-id="6de6b-131">Then copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="6de6b-133">Ora che i file sono stati caricati, assicurarsi che sia selezionato il testo "feedbackpanel" nella gerarchia ASA_feedback, fare clic su "Aggiungi componente" e aggiungere lo script di ancoraggio feedback cercandolo e selezionando il testo quando viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="6de6b-133">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="6de6b-135">Trascinare l'oggetto testo "feedbackPanel" dalla gerarchia ASA_Feedback nello slot vuoto sotto lo script, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="6de6b-135">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="6de6b-137">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="6de6b-137">Congratulations</span></span>

<span data-ttu-id="6de6b-138">In questa lezione è stato illustrato come creare un pannello dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di ancoraggio spaziale di Azure per fornire agli utenti il feedback in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="6de6b-138">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


