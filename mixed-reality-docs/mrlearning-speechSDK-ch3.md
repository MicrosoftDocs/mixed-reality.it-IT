---
title: Esercitazioni su servizi vocali di Azure-3. Aggiunta del componente traduzione vocale di servizi cognitivi di Azure
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913205"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="1cbae-105">3. aggiunta del componente traduzione vocale di servizi cognitivi di Azure</span><span class="sxs-lookup"><span data-stu-id="1cbae-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="1cbae-106">In questa esercitazione vengono fornite informazioni sul componente traduzione vocale dei servizi cognitivi di Azure nel progetto, oltre a tradurre in tre lingue diverse.</span><span class="sxs-lookup"><span data-stu-id="1cbae-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="1cbae-107">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="1cbae-107">Instructions</span></span>

1. <span data-ttu-id="1cbae-108">Selezionare l'oggetto Lunarcom_Base nella gerarchia e fare clic su Aggiungi componente nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="1cbae-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="1cbae-109">Cercare e selezionare Lunarcom Translation Recognizer.</span><span class="sxs-lookup"><span data-stu-id="1cbae-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="1cbae-111">Disabilitare il simulatore in modalità offline.</span><span class="sxs-lookup"><span data-stu-id="1cbae-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="1cbae-113">Prima di procedere, verificare che il simulatore in modalità offline sia disabilitato, come illustrato nell'immagine precedente, prima di testare il traduttore dell'SDK vocale.</span><span class="sxs-lookup"><span data-stu-id="1cbae-113">Before moving on, ensure the offline mode simulator is disabled, as shown in the image above, before testing the Speech-SDK translator.</span></span> <span data-ttu-id="1cbae-114">Per tradurre, è necessario essere connessi a Internet.</span><span class="sxs-lookup"><span data-stu-id="1cbae-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="1cbae-115">Fare clic sull'elenco a discesa nel riconoscimento Lunarcom translation e selezionare la lingua in cui si desidera tradurre.</span><span class="sxs-lookup"><span data-stu-id="1cbae-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="1cbae-117">A questo punto, eseguire l'applicazione e testare il convertitore facendo clic sul pulsante satellite e iniziare a pronunciare.</span><span class="sxs-lookup"><span data-stu-id="1cbae-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="1cbae-118">Premere di nuovo il pulsante satellite per arrestare il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="1cbae-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="1cbae-119">Di seguito è riportato un esempio di come dovrebbe apparire la scena.</span><span class="sxs-lookup"><span data-stu-id="1cbae-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="1cbae-120">È possibile modificare la lingua nell'elenco a discesa "lingua di destinazione" (vedere l'immagine precedente) per esplorare la traduzione in altre lingue.</span><span class="sxs-lookup"><span data-stu-id="1cbae-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="1cbae-121">Di seguito è riportato un esempio di come dovrebbe apparire la scena:</span><span class="sxs-lookup"><span data-stu-id="1cbae-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="1cbae-123">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="1cbae-123">Congratulations</span></span>

<span data-ttu-id="1cbae-124">Il progetto può ora tradurre le parole che si parlano in diversi linguaggi.</span><span class="sxs-lookup"><span data-stu-id="1cbae-124">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="1cbae-125">È possibile provare a usare le lingue e testare l'accuratezza della traduzione.</span><span class="sxs-lookup"><span data-stu-id="1cbae-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="1cbae-126">Esercitazione successiva: 4. configurazione della finalità e della comprensione del linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="1cbae-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
