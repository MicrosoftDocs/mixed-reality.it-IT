---
title: Modulo ASA Learning MR Azure spaziali ancoraggio su HoloLens 2
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326549"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="66d91-104">Visualizzazione dei commenti di Azure ancoraggio spaziali</span><span class="sxs-lookup"><span data-stu-id="66d91-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="66d91-105">In questa lezione, scoprirai procedura fornire agli utenti con commenti e suggerimenti sull'individuazione di ancoraggio, eventi e lo stato quando si usa Azure spaziali ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="66d91-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="66d91-106">Obiettivi:</span><span class="sxs-lookup"><span data-stu-id="66d91-106">Objectives:</span></span>

* <span data-ttu-id="66d91-107">Informazioni su come configurare un pannello dell'interfaccia utente che visualizza informazioni importanti relative alla sessione corrente di ASA</span><span class="sxs-lookup"><span data-stu-id="66d91-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="66d91-108">Comprendere ed esplorare gli elementi di feedback che il SDK ASA rende disponibile agli utenti</span><span class="sxs-lookup"><span data-stu-id="66d91-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="66d91-109">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="66d91-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="66d91-110">Configurare Panel dell'interfaccia utente di commenti e suggerimenti ASA</span><span class="sxs-lookup"><span data-stu-id="66d91-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="66d91-111">In questa lezione non si userà "SaveAnchorToDisk" e i pulsanti "ShareAnchor", quindi selezionare entrambi i pulsanti e deselezionare la casella di controllo nel Pannello di controllo (come illustrato di seguito) per nascondere questi pulsanti.</span><span class="sxs-lookup"><span data-stu-id="66d91-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="66d91-113">Successivamente, creare il pannello di istruzione.</span><span class="sxs-lookup"><span data-stu-id="66d91-113">Next, create the instruction panel.</span></span> <span data-ttu-id="66d91-114">Iniziare con il pulsante destro facendo clic sul pulsante "instructions", passare il mouse su "oggetto 3D" e selezionare "textmeshpro-text".</span><span class="sxs-lookup"><span data-stu-id="66d91-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="66d91-116">Modificare la scala e il posizionamento del testo in modo che corrisponda con le istruzioni riportate nella scena.</span><span class="sxs-lookup"><span data-stu-id="66d91-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="66d91-117">Inoltre, assicurarsi che l'allineamento per tutto il testo è centrato.</span><span class="sxs-lookup"><span data-stu-id="66d91-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="66d91-118">Quindi eliminare il testo di esempio dall'editor di testo, come nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="66d91-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="66d91-120">Modificare il nome dell'oggetto TextMeshPro in "FeedbackPanel."</span><span class="sxs-lookup"><span data-stu-id="66d91-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="66d91-122">Nel Pannello di progetto, selezionare "risorse" e fare clic destro, quindi selezionare "Visualizza Explorer".</span><span class="sxs-lookup"><span data-stu-id="66d91-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="66d91-124">A questo punto, fare clic su [qui](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) per scaricare i file necessari entro i prossimi passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="66d91-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="66d91-125">Quando si apre Esplora, selezionare la cartella assets, quindi la cartella "ASAmodulesAssets" e copiare lo script di feedback di ancoraggio e i file di script di ancoraggio modulo nella cartella.</span><span class="sxs-lookup"><span data-stu-id="66d91-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="66d91-127">Nota: se viene visualizzato un messaggio popup che chiede se si desidera sovrascrivere il vecchio o mantenere il vecchio assicurarsi di selezionare sovrascrittura.</span><span class="sxs-lookup"><span data-stu-id="66d91-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="66d91-128">Tornare ora alla cartella Assets.</span><span class="sxs-lookup"><span data-stu-id="66d91-128">Now return to the Assets folder.</span></span> <span data-ttu-id="66d91-129">Quindi, passare alla cartella "AzureSpatialAnchorsPlugin", quindi la cartella di esempi e infine la cartella degli script e copiare il wrapper di demo Anchor spaziali Azure nella cartella.</span><span class="sxs-lookup"><span data-stu-id="66d91-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="66d91-131">Ora che i file vengono caricati, assicurarsi che il testo "feedbackpanel" sia selezionato, nella gerarchia di ASA_feedback e fare clic su "Aggiungi componente" e aggiungere lo script di ancoraggio commenti e suggerimenti per la ricerca e selezionarlo quando viene visualizzato.</span><span class="sxs-lookup"><span data-stu-id="66d91-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="66d91-133">Trascinare l'oggetto testo "feedbackPanel" dalla gerarchia di ASA_Feedback lo slot vuoto sotto lo script come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="66d91-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="66d91-135">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="66d91-135">Congratulations</span></span>

<span data-ttu-id="66d91-136">In questa lezione è stato illustrato come creare un pannello dell'interfaccia utente per visualizzare lo stato corrente dell'esperienza di ancoraggio spaziale di Azure per fornire utente con il feedback in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="66d91-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


