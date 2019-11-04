---
title: Esercitazioni su servizi vocali di Azure-2. Aggiunta di una modalità offline per la traduzione vocale locale
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 5382a1cce38e8607042c21b8dd3157d1da2fa72e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437561"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="0821b-105">2. aggiunta di una modalità offline per la traduzione vocale locale</span><span class="sxs-lookup"><span data-stu-id="0821b-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="0821b-106">In questa esercitazione verrà aggiunta una modalità offline che consente di eseguire la traduzione vocale locale quando non è possibile connettersi al servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="0821b-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="0821b-107">Si *simula* anche uno stato disconnesso.</span><span class="sxs-lookup"><span data-stu-id="0821b-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="0821b-108">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="0821b-108">Instructions</span></span>

1. <span data-ttu-id="0821b-109">Consente di selezionare l'oggetto Lunarcom_Base nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="0821b-109">Select the Lunarcom_Base object in the hierarchy.</span></span>
2. <span data-ttu-id="0821b-110">Fare clic su Aggiungi componente nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="0821b-110">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="0821b-111">Cercare e selezionare il riconoscimento Lunarcom offline.</span><span class="sxs-lookup"><span data-stu-id="0821b-111">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. <span data-ttu-id="0821b-113">Fare clic sull'elenco a discesa in LunarcomOfflineRecognizer e selezionare abilitato.</span><span class="sxs-lookup"><span data-stu-id="0821b-113">Click the drop-down in the LunarcomOfflineRecognizer and select Enabled.</span></span> <span data-ttu-id="0821b-114">Questo programma consente di eseguire il progetto per agire come l'utente non dispone di una connessione.</span><span class="sxs-lookup"><span data-stu-id="0821b-114">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. <span data-ttu-id="0821b-116">Premere Riproduci nell'editor di Unity e testarlo.</span><span class="sxs-lookup"><span data-stu-id="0821b-116">Press Play in Unity Editor, and test it.</span></span> <span data-ttu-id="0821b-117">Premere il microfono nell'angolo in basso a sinistra della scena e iniziare a pronunciare.</span><span class="sxs-lookup"><span data-stu-id="0821b-117">Press the microphone in the bottom-left corner in the scene and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="0821b-118">Poiché è offline, la funzionalità di riattivazione delle parole è stata disabilitata.</span><span class="sxs-lookup"><span data-stu-id="0821b-118">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="0821b-119">È necessario fare clic fisicamente sul microfono ogni volta che si desidera che il riconoscimento vocale venga riconosciuto quando è offline.</span><span class="sxs-lookup"><span data-stu-id="0821b-119">You'll need to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="0821b-120">Di seguito è riportato un esempio di come potrebbe apparire la scena.</span><span class="sxs-lookup"><span data-stu-id="0821b-120">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="0821b-122">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="0821b-122">Congratulations</span></span>

<span data-ttu-id="0821b-123">La modalità offline è stata abilitata.</span><span class="sxs-lookup"><span data-stu-id="0821b-123">The offline mode has been enabled.</span></span> <span data-ttu-id="0821b-124">A questo punto, quando si è offline, è possibile continuare a lavorare sul progetto con l'SDK di riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="0821b-124">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="0821b-125">Esercitazione successiva: 3. aggiunta del componente di traduzione vocale dei servizi cognitivi di Azure</span><span class="sxs-lookup"><span data-stu-id="0821b-125">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

