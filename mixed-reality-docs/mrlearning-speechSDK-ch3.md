---
title: Modulo SpeechSDK di MR Learning-riconoscimento vocale e trascrizione
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 7fe3c96cf7b888a4a91960147270be81a0973980
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485762"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="ad155-104">3.    Aggiunta del componente traduzione vocale di servizi cognitivi di Azure</span><span class="sxs-lookup"><span data-stu-id="ad155-104">3.    Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="ad155-105">Questa esercitazione illustra come aabout il componente traduzione vocale dei servizi cognitivi di Azure nel progetto e come tradurre in tre lingue diverse.</span><span class="sxs-lookup"><span data-stu-id="ad155-105">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

## <a name="instructions"></a><span data-ttu-id="ad155-106">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="ad155-106">Instructions</span></span>

1. <span data-ttu-id="ad155-107">Selezionare l'oggetto Lunarcom_Base nella gerarchia e fare clic su Aggiungi componente nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="ad155-107">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="ad155-108">Cercare e selezionare LunarcomTranslationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="ad155-108">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="ad155-110">Nota: Verificare che il simulatore in modalità offline sia disabilitato prima di testare il traduttore dell'SDK vocale.</span><span class="sxs-lookup"><span data-stu-id="ad155-110">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="ad155-111">Per tradurre, è necessario essere connessi a Internet.</span><span class="sxs-lookup"><span data-stu-id="ad155-111">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="ad155-112">Vedere l'immagine seguente su dove trovare questa impostazione.</span><span class="sxs-lookup"><span data-stu-id="ad155-112">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="ad155-114">Fare clic sull'elenco a discesa in LunarcomTranslationRecognizer e selezionare la lingua in cui si desidera tradurre.</span><span class="sxs-lookup"><span data-stu-id="ad155-114">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="ad155-116">A questo punto, eseguire l'applicazione e testare il convertitore facendo clic sul pulsante satellite e iniziare a pronunciare.</span><span class="sxs-lookup"><span data-stu-id="ad155-116">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="ad155-117">Premere di nuovo il pulsante satellite per arrestare il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="ad155-117">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="ad155-118">Di seguito è riportato un esempio di come dovrebbe apparire la scena.</span><span class="sxs-lookup"><span data-stu-id="ad155-118">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="ad155-119">È possibile modificare la lingua nell'elenco a discesa "lingua di destinazione" (vedere l'immagine precedente) per esplorare la traduzione in altre lingue.</span><span class="sxs-lookup"><span data-stu-id="ad155-119">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="ad155-120">Nota: Prima di eseguire il test, verificare che il simulatore offline sia disabilitato, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="ad155-120">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="ad155-122">Di seguito è riportato un esempio di come dovrebbe apparire la scena:</span><span class="sxs-lookup"><span data-stu-id="ad155-122">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="ad155-124">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="ad155-124">Congratulations</span></span>

<span data-ttu-id="ad155-125">Il progetto può ora tradurre le parole che si parlano in diversi linguaggi.</span><span class="sxs-lookup"><span data-stu-id="ad155-125">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="ad155-126">È possibile provare a usare le lingue e testare l'accuratezza della traduzione.</span><span class="sxs-lookup"><span data-stu-id="ad155-126">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="ad155-127">Esercitazione successiva: 4.  Configurazione di finalità e comprensione del linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="ad155-127">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

