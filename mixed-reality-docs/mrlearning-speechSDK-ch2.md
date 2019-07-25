---
title: Modulo SpeechSDK di MR Learning-riconoscimento vocale e trascrizione
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: e8dc5da5a089079ba38a26969df6070af8bc6200
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460309"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="50545-104">2.    Aggiunta di una modalità offline per la traduzione vocale locale</span><span class="sxs-lookup"><span data-stu-id="50545-104">2.    Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="50545-105">In questa esercitazione verrà aggiunta una modalità offline che consente di eseguire la traduzione vocale locale quando non è possibile connettersi al servizio di Azure.</span><span class="sxs-lookup"><span data-stu-id="50545-105">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="50545-106">Si *simula* anche uno stato disconnesso.</span><span class="sxs-lookup"><span data-stu-id="50545-106">We will also *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="50545-107">Selezionare l'oggetto Lunarcom_Base nella gerarchia e fare clic su Aggiungi componente nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="50545-107">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="50545-108">Cercare e selezionare il riconoscimento Lunarcom offline.</span><span class="sxs-lookup"><span data-stu-id="50545-108">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="50545-110">Fare clic sull'elenco a discesa in LunarcomOfflineRecognizer e selezionare abilitato.</span><span class="sxs-lookup"><span data-stu-id="50545-110">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="50545-111">Questo programma consente di eseguire il progetto per agire come l'utente non dispone di una connessione.</span><span class="sxs-lookup"><span data-stu-id="50545-111">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="50545-113">A questo punto, premere Riproduci nell'editor di Unity e testarlo.</span><span class="sxs-lookup"><span data-stu-id="50545-113">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="50545-114">Premere il microfono nell'angolo in basso a sinistra della scena e iniziare a pronunciare.</span><span class="sxs-lookup"><span data-stu-id="50545-114">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="50545-115">Poiché è offline, la funzionalità di riattivazione delle parole è stata disabilitata.</span><span class="sxs-lookup"><span data-stu-id="50545-115">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="50545-116">È necessario fare clic fisicamente sul microfono ogni volta che si desidera che il riconoscimento vocale venga riconosciuto quando è offline.</span><span class="sxs-lookup"><span data-stu-id="50545-116">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="50545-117">Di seguito è riportato un esempio di come potrebbe apparire la scena.</span><span class="sxs-lookup"><span data-stu-id="50545-117">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="50545-119">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="50545-119">Congratulations</span></span>

<span data-ttu-id="50545-120">La modalità offline è stata abilitata.</span><span class="sxs-lookup"><span data-stu-id="50545-120">The offline mode has been enabled.</span></span> <span data-ttu-id="50545-121">A questo punto, quando si è offline, è possibile continuare a lavorare sul progetto con l'SDK di riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="50545-121">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="50545-122">Esercitazione successiva: 3.  Aggiunta del componente traduzione vocale di servizi cognitivi di Azure</span><span class="sxs-lookup"><span data-stu-id="50545-122">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

