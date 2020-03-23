---
title: Esercitazioni sui servizi vocali di Azure - 2. Aggiunta di una modalità offline per la traduzione locale da voce a testo
description: Completa questo corso per imparare a implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031604"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a><span data-ttu-id="ea6da-105">2. Uso del riconoscimento vocale per l'esecuzione di comandi</span><span class="sxs-lookup"><span data-stu-id="ea6da-105">2. Using speech recognition to execute commands</span></span>

<span data-ttu-id="ea6da-106">In questa esercitazione aggiungerai la possibilità di eseguire comandi con il riconoscimento vocale di Azure, che consentirà di eseguire un evento in base alla parola o alla frase definita.</span><span class="sxs-lookup"><span data-stu-id="ea6da-106">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="ea6da-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="ea6da-107">Objectives</span></span>

* <span data-ttu-id="ea6da-108">Imparare a usare il riconoscimento vocale di Azure per eseguire comandi</span><span class="sxs-lookup"><span data-stu-id="ea6da-108">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="ea6da-109">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="ea6da-109">Instructions</span></span>

<span data-ttu-id="ea6da-110">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Wake Word Recognizer (Script)** (Riconoscimento parola di attivazione Lunarcom - Script) all'oggetto Lunarcom e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="ea6da-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="ea6da-111">Nel campo **Wake Word** (Parola di attivazione) immetti una frase appropriata, ad esempio _Activate Terminal_.</span><span class="sxs-lookup"><span data-stu-id="ea6da-111">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="ea6da-112">Nel campo **Dismiss Word** (Parola di eliminazione) immetti una frase appropriata, ad esempio _Dismiss Terminal_.</span><span class="sxs-lookup"><span data-stu-id="ea6da-112">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ea6da-114">Il componente Lunarcom Wake Word Recognizer (Script) (Riconoscimento parola di attivazione Lunarcom - Script) non fa parte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="ea6da-114">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="ea6da-115">È stato fornito con gli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="ea6da-115">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="ea6da-116">Se ora attivi la modalità gioco, come nell'esercitazione precedente, il pannello del terminale viene abilitato per impostazione predefinita. Tuttavia, puoi ora disabilitarlo pronunciando la parola di eliminazione **Dismiss terminal**:</span><span class="sxs-lookup"><span data-stu-id="ea6da-116">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="ea6da-118">Puoi anche riabilitarlo pronunciando la parola di attivazione **Activate terminal**:</span><span class="sxs-lookup"><span data-stu-id="ea6da-118">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="ea6da-120">Poiché l'applicazione deve connettersi ad Azure, assicurati che il computer o il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="ea6da-120">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="ea6da-121">Se prevedi di non essere spesso in grado di connetterti ad Azure, puoi implementare i comandi vocali anche con MRTK seguendo le istruzioni contenute in [Abilitazione dei comandi vocali](mrlearning-base-ch5.md#enabling-voice-commands).</span><span class="sxs-lookup"><span data-stu-id="ea6da-121">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Enabling Voice Commands](mrlearning-base-ch5.md#enabling-voice-commands) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ea6da-122">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="ea6da-122">Congratulations</span></span>

<span data-ttu-id="ea6da-123">Hai implementato i comandi vocali basati su Azure.</span><span class="sxs-lookup"><span data-stu-id="ea6da-123">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="ea6da-124">Esegui l'applicazione nel dispositivo per verificare che la funzionalità venga eseguita correttamente.</span><span class="sxs-lookup"><span data-stu-id="ea6da-124">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="ea6da-125">Nell'esercitazione successiva apprenderai come tradurre il parlato con la traduzione vocale di Azure.</span><span class="sxs-lookup"><span data-stu-id="ea6da-125">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

[<span data-ttu-id="ea6da-126">Esercitazione successiva: 3. Aggiunta del componente di traduzione vocale di Servizi cognitivi di Azure</span><span class="sxs-lookup"><span data-stu-id="ea6da-126">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
