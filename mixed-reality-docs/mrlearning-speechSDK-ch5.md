---
title: Modulo SpeechSDK di MR Learning-riconoscimento vocale e trascrizione
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: da485f167ef3902dd75adf8da8181504fbc6c6df
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913160"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="7a869-104">Modulo di apprendimento vocale SDK-controllo lanciarazzi con comandi vocali</span><span class="sxs-lookup"><span data-stu-id="7a869-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="7a869-105">In questa lezione verrà usata la funzionalità finalità del servizio riconoscimento vocale di Azure per comprendere lo scopo del discorso.</span><span class="sxs-lookup"><span data-stu-id="7a869-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="7a869-106">Per controllare l'utilità di avvio di Rocket verrà usato lo scopo di riconoscimento vocale rilevato.</span><span class="sxs-lookup"><span data-stu-id="7a869-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="7a869-107">Durante questa lezione, verrà importato l'asset dell'utilità di avvio di Rocket, che verrà interfacciata nei pulsanti di controllo predefiniti per il controllo Rocket.</span><span class="sxs-lookup"><span data-stu-id="7a869-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span>

## <a name="objectives"></a><span data-ttu-id="7a869-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="7a869-108">Objectives</span></span>

- <span data-ttu-id="7a869-109">Informazioni su come connettere la finalità vocale come comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="7a869-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="7a869-110">Informazioni su come usare i comandi vocali per finalità vocali come comandi di input di controllo Rocket.</span><span class="sxs-lookup"><span data-stu-id="7a869-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="7a869-111">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="7a869-111">Instructions</span></span>

1. <span data-ttu-id="7a869-112">In questa esercitazione verrà usato un asset "BaseModule" per integrare Rocket Launcher con i comandi vocali.</span><span class="sxs-lookup"><span data-stu-id="7a869-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="7a869-113">A tale proposito, è necessario importare l'asset nel progetto.</span><span class="sxs-lookup"><span data-stu-id="7a869-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="7a869-114">È possibile scaricare l'asset "lanciarazzi" con questo [collegamento](https://github.com/Developer-OI/MixedRealityLearning/releases/download/1.2.1/BaseModuleAssets-1.2.1.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="7a869-114">You can download the "Rocket Launcher" asset using this [link](https://github.com/Developer-OI/MixedRealityLearning/releases/download/1.2.1/BaseModuleAssets-1.2.1.unitypackage).</span></span>

2. <span data-ttu-id="7a869-115">Per importare l'asset, passare a Asset-> Importa pacchetto-> pacchetto personalizzato-> passare al file scaricato e fare clic su Importa.</span><span class="sxs-lookup"><span data-stu-id="7a869-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

    ![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="7a869-117">Dopo aver importato l'asset "asset modulo di base", spostarsi all'interno della cartella "asset modulo di base"-> prefabbricati-> selezionare "Rocket Launcher_Complete", quindi trascinarlo nella gerarchia della scena esistente.</span><span class="sxs-lookup"><span data-stu-id="7a869-117">After importing the  "Base Module Assets" asset, navigate inside the "Base Module Assets" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

    ![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="7a869-119">A questo punto è necessario integrare "Rocket Launcher" con il progetto LUIS che abbiamo lavorato nella [lezione](mrlearning-speechSDK-ch4.md)precedente.</span><span class="sxs-lookup"><span data-stu-id="7a869-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson [lesson](mrlearning-speechSDK-ch4.md).</span></span> <span data-ttu-id="7a869-120">A tale proposito, espandere il prefabbricato "Rocket Launcher_Complete" nella gerarchia e trovare i pulsanti "LaunchRoundButton", "ResetRoundButton" e "Placement Hints".</span><span class="sxs-lookup"><span data-stu-id="7a869-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

    ![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="7a869-122">Selezionare "LaunchRoundButton" e nel pannello di controllo passare a "interactable" e in eventi "OnClick ()", trascinare il prefabbricato "LunarModule".</span><span class="sxs-lookup"><span data-stu-id="7a869-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="7a869-123">Selezionare quindi la funzione a discesa e selezionare "LunarModule", quindi passare alla funzione "StartThruster ()" e selezionarla.</span><span class="sxs-lookup"><span data-stu-id="7a869-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

    ![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

    ![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="7a869-126">Selezionare "ResetRoundButton" e nel pannello di controllo passare a "interactable" e in eventi "OnClick ()", trascinare il prefabbricato "LunarModule".</span><span class="sxs-lookup"><span data-stu-id="7a869-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="7a869-127">Selezionare quindi la funzione a discesa e selezionare "LunarModule", quindi passare alla funzione "resetModule ()" e selezionarla.</span><span class="sxs-lookup"><span data-stu-id="7a869-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

    ![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="7a869-129">Selezionare "hint di posizionamento" e nel pannello di controllo passare a "interactable" e in eventi "OnClick ()", trascinare il prefabbricato "LunarModule".</span><span class="sxs-lookup"><span data-stu-id="7a869-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="7a869-130">Selezionare quindi la funzione a discesa e selezionare "LunarModule", quindi passare alla funzione "TogglePlacementHints" e selezionare ToggleGameOBjects ().</span><span class="sxs-lookup"><span data-stu-id="7a869-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

    ![module4chapter5step3c](images/module4chapter5step3c.PNG)

8. <span data-ttu-id="7a869-132">Selezionare quindi la Lunarcom_Completed prefabbricate in Hierarchy e passare allo script "Lunarcom Intent Recognizer" in Inspector, quindi trascinare e rilasciare i pulsanti "LaunchRoundButton", "ResetRoundButton" e "hint di posizionamento" nelle rispettive posizioni.</span><span class="sxs-lookup"><span data-stu-id="7a869-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

    ![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="7a869-134">Premere il pulsante Play nell'editor di Unity e fare clic sul pulsante "Rocket" e pronunciare le frasi come "push Rocket Launch Button" (Mostra un suggerimento di selezione host), "premere il pulsante Rest" o qualsiasi altra frase relativa alla richiesta di avvio, reimpostazione o suggerimento per l'utilità di avvio Rocket.</span><span class="sxs-lookup"><span data-stu-id="7a869-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

    ![module4chapter5step5a](images/module4chapter5step5a.PNG)

    ![module4chapter5step5b](images/module4chapter5step5b.PNG)

    ![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="7a869-138">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="7a869-138">Congratulations</span></span>

<span data-ttu-id="7a869-139">In questa lezione si è appreso come connettere i comandi vocali basati su intelligenza artificiale ai comandi vocali per usarli come metodo di input.</span><span class="sxs-lookup"><span data-stu-id="7a869-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="7a869-140">Ora il programma può usare i relatori Intent come comandi vocali per fornire input per il lanciarazzi.</span><span class="sxs-lookup"><span data-stu-id="7a869-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>
