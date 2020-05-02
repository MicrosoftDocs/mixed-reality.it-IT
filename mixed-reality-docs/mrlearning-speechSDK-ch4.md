---
title: Esercitazioni sui servizi vocali di Azure - 4 Configurazione della comprensione delle finalità e del linguaggio naturale
description: Completa questo corso per ottenere informazioni su come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: b2342e7d0d502af2787ca311d18a44f8726acf2d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028554"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="d0725-105">4. Configurazione della comprensione delle finalità e del linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="d0725-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="d0725-106">In questa esercitazione esplorerai il riconoscimento delle finalità del servizio vocale di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0725-106">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="d0725-107">Il riconoscimento delle finalità consente di dotare l'applicazione di comandi vocali basati sull'intelligenza artificiale, in cui gli utenti possono pronunciare comandi vocali non specifici e ottenere il riconoscimento delle finalità da parte del sistema.</span><span class="sxs-lookup"><span data-stu-id="d0725-107">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="d0725-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="d0725-108">Objectives</span></span>

* <span data-ttu-id="d0725-109">Ottenere informazioni su come configurare finalità, entità ed espressioni nel portale LUIS</span><span class="sxs-lookup"><span data-stu-id="d0725-109">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="d0725-110">Ottenere informazioni su come implementare la comprensione delle finalità e del linguaggio naturale nell'applicazione</span><span class="sxs-lookup"><span data-stu-id="d0725-110">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="d0725-111">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="d0725-111">Preparing the scene</span></span>

<span data-ttu-id="d0725-112">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Intent Recognizer (Script)** (Riconoscimento finalità Lunarcom - Script) all'oggetto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="d0725-112">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="d0725-114">Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **RocketLauncher**, trascina il prefab **RocketLauncher_Complete** nella finestra Hierarchy (Gerarchia) e quindi posizionalo in un punto appropriato davanti alla fotocamera, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="d0725-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="d0725-115">Trasforma la **posizione** X = 0, Y = -0.4, Z = 1</span><span class="sxs-lookup"><span data-stu-id="d0725-115">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="d0725-116">Trasforma la **rotazione** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="d0725-116">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="d0725-118">Nella finestra Hierarchy (Gerarchia) seleziona di nuovo l'oggetto **Lunarcom**, quindi espandi l'oggetto **RocketLauncher_Complete** > **Button** e assegna ognuno degli oggetti figlio dell'oggetto **Buttons** al campo **Lunar Launcher Buttons** (Pulsanti lancio lunare) corrispondente:</span><span class="sxs-lookup"><span data-stu-id="d0725-118">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="d0725-120">Creazione della risorsa Azure Language Understanding</span><span class="sxs-lookup"><span data-stu-id="d0725-120">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="d0725-121">In questa sezione creerai una risorsa di stima di Azure per l'app LUIS (Language Understanding Intelligent Service) che verrà creata nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="d0725-121">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="d0725-122">Accedi ad <a href="https://portal.azure.com" target="_blank">Azure</a> e fai clic su **Crea una risorsa**.</span><span class="sxs-lookup"><span data-stu-id="d0725-122">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="d0725-123">Cerca quindi e seleziona **Language Understanding**:</span><span class="sxs-lookup"><span data-stu-id="d0725-123">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="d0725-125">Fai clic sul pulsante **Create** (Crea) per creare un'istanza del servizio:</span><span class="sxs-lookup"><span data-stu-id="d0725-125">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="d0725-127">Nella pagina Create (Crea) fai clic sull'opzione **Prediction** (Stima) e immetti i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0725-127">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="d0725-128">In **Subscription** (Sottoscrizione) seleziona **Free Trail** (Prova gratuita) se disponi di una sottoscrizione di prova gratuita, altrimenti seleziona una delle altre sottoscrizioni</span><span class="sxs-lookup"><span data-stu-id="d0725-128">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="d0725-129">In **Resource group** (Gruppo risorse) fai clic sul collegamento **Create new** (Crea nuovo), immetti un nome appropriato, ad esempio *MRKT-Tutorials*, e quindi fai clic su **OK**</span><span class="sxs-lookup"><span data-stu-id="d0725-129">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click the **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="d0725-131">Al momento della stesura di questo articolo, non è necessario creare una risorsa di creazione perché quando viene creata l'app LUIS (Language Understanding Intelligent Service) nella sezione successiva viene generata automaticamente una chiave di prova per la creazione in LUIS.</span><span class="sxs-lookup"><span data-stu-id="d0725-131">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="d0725-132">Se disponi già di un altro gruppo di risorse appropriato nell'account di Azure, ad esempio se hai completato l'esercitazione sugli [ancoraggi nello spazio di Azure](mrlearning-asa-ch1.md), puoi usarlo anziché crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="d0725-132">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mrlearning-asa-ch1.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="d0725-133">Sempre nella pagina Create (Crea) immetti i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0725-133">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="d0725-134">In **Name** (Nome) immetti un nome appropriato per il servizio, ad esempio *MRTK-Tutorials-AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="d0725-134">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="d0725-135">In **Prediction location** (Posizione di stima) scegli una posizione vicina alla posizione fisica degli utenti dell'app, ad esempio *(US) West US* (Stati Uniti occidentali)</span><span class="sxs-lookup"><span data-stu-id="d0725-135">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="d0725-136">Ai fini di questa esercitazione, in **Prediction pricing tier** (Piano tariffario di stima) seleziona **F0 (5 Calls per second, 10K Calls per month)** (F0 - 5 chiamate al secondo, 10.000 chiamate al mese)</span><span class="sxs-lookup"><span data-stu-id="d0725-136">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="d0725-138">Passa quindi alla scheda **Review + create** (Verifica e crea), esamina i dettagli e quindi fai clic sul pulsante **Create** (Crea), disponibile nella parte inferiore della pagina, per creare la risorsa e il nuovo gruppo di risorse se ne hai configurato uno per la creazione:</span><span class="sxs-lookup"><span data-stu-id="d0725-138">Next, go to the **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="d0725-140">Dopo aver fatto clic sul pulsante Create (Crea), dovrai attendere alcuni minuti per la creazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="d0725-140">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="d0725-141">Al termine del processo di creazione delle risorse, visualizzerai il messaggio **Your deployment is complete** (Distribuzione completata):</span><span class="sxs-lookup"><span data-stu-id="d0725-141">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="d0725-143">Creazione di un'app LUIS (Language Understanding Intelligent Service)</span><span class="sxs-lookup"><span data-stu-id="d0725-143">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="d0725-144">In questa sezione eseguirai la creazione di un'app LUIS, la configurazione e il training del modello di stima e la connessione alla risorsa di stima di Azure creata nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="d0725-144">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="d0725-145">In particolare, creerai una finalità in base alla quale se l'utente pronuncia un'azione da eseguire, l'app attiverà l'evento Interactable.OnClick() su uno dei tre pulsanti rossi della scena, a seconda del pulsante a cui fa riferimento l'utente.</span><span class="sxs-lookup"><span data-stu-id="d0725-145">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="d0725-146">Se ad esempio l'utente pronuncia **go ahead and launch the rocket** (vai avanti e lancia il missile), l'app stimerà che **vai avanti** indica un'**azione** da eseguire e che l'evento Interactable.OnClick() **target** sia il pulsante di **lancio**.</span><span class="sxs-lookup"><span data-stu-id="d0725-146">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="d0725-147">Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="d0725-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="d0725-148">Creare un'app LUIS</span><span class="sxs-lookup"><span data-stu-id="d0725-148">Create a LUIS app</span></span>
2. <span data-ttu-id="d0725-149">Creare finalità</span><span class="sxs-lookup"><span data-stu-id="d0725-149">Create intents</span></span>
3. <span data-ttu-id="d0725-150">Creare espressioni di esempio</span><span class="sxs-lookup"><span data-stu-id="d0725-150">Create example utterances</span></span>
4. <span data-ttu-id="d0725-151">Creare entità</span><span class="sxs-lookup"><span data-stu-id="d0725-151">Create entities</span></span>
5. <span data-ttu-id="d0725-152">Assegnare entità alle espressioni di esempio</span><span class="sxs-lookup"><span data-stu-id="d0725-152">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="d0725-153">Eseguire il training, il test e la pubblicazione dell'app</span><span class="sxs-lookup"><span data-stu-id="d0725-153">Train, test, and publish the app</span></span>
7. <span data-ttu-id="d0725-154">Assegnare una risorsa di stima di Azure all'app</span><span class="sxs-lookup"><span data-stu-id="d0725-154">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="d0725-155">1. Creare un'app LUIS</span><span class="sxs-lookup"><span data-stu-id="d0725-155">1. Create a LUIS app</span></span>

<span data-ttu-id="d0725-156">Con lo stesso account utente usato durante la creazione della risorsa di Azure nella sezione precedente, accedi a <a href="https://www.luis.ai" target="_blank">LUIS</a>, seleziona il tuo paese e accetta le condizioni per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="d0725-156">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="d0725-157">Nel passaggio successivo, quando viene visualizzata la richiesta **Link your Azure account** (Collega il tuo account Azure), scegli **Continue using your trial key** (Continua a usare la chiave di prova) per usare invece una risorsa di creazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="d0725-157">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="d0725-158">Se hai già effettuato l'iscrizione a LUIS e la chiave di prova per la creazione è scaduta, puoi fare riferimento alla documentazione [Eseguire la migrazione a una chiave di creazione delle risorse di Azure](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) per passare ad Azure per la risorsa di creazione LUIS.</span><span class="sxs-lookup"><span data-stu-id="d0725-158">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="d0725-159">Dopo aver eseguito l'accesso, passa alla pagina **My apps** (App personali), quindi fai clic su **Create new app** (Crea nuova app) e immetti i valori seguenti nella finestra popup **Create new app** (Crea nuova app):</span><span class="sxs-lookup"><span data-stu-id="d0725-159">Once signed in, navigate to the **My apps** page, then click **Create new app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="d0725-160">In **Name** (Nome) immetti un nome appropriato, ad esempio *MRTK Tutorials - AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="d0725-160">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="d0725-161">In **Culture** (Impostazioni cultura) seleziona **English** (Inglese)</span><span class="sxs-lookup"><span data-stu-id="d0725-161">For **Culture**, select **English**</span></span>
* <span data-ttu-id="d0725-162">In **Description** (Descrizione) immetti facoltativamente una descrizione appropriata</span><span class="sxs-lookup"><span data-stu-id="d0725-162">For **Description**, optionally enter a suitable description</span></span>

<span data-ttu-id="d0725-163">Fai quindi clic sul pulsante **Done** (Fine) per creare la nuova app:</span><span class="sxs-lookup"><span data-stu-id="d0725-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="d0725-165">Al termine della creazione della nuova app, visualizzerai la pagina **Dashboard** dell'app:</span><span class="sxs-lookup"><span data-stu-id="d0725-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="d0725-167">2. Creare finalità</span><span class="sxs-lookup"><span data-stu-id="d0725-167">2. Create intents</span></span>

<span data-ttu-id="d0725-168">Dalla pagina Dashboard passa alla pagina Build (Compila) > App Assets (Asset app) > **Intents** (Finalità), quindi fai clic su **Create new intent** (Crea nuova finalità) e immetti il valore seguente nella finestra popup **Create new intent** (Crea nuova finalità):</span><span class="sxs-lookup"><span data-stu-id="d0725-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create new intent** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="d0725-169">In **Intent name** (Nome finalità) immetti **PressButton**</span><span class="sxs-lookup"><span data-stu-id="d0725-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="d0725-170">Fai quindi clic sul pulsante **Done** (Fine) per creare la nuova finalità:</span><span class="sxs-lookup"><span data-stu-id="d0725-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="d0725-172">Ai fini di questa esercitazione, il progetto Unity farà riferimento a questa finalità in base al nome, ad esempio 'PressButton'.</span><span class="sxs-lookup"><span data-stu-id="d0725-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="d0725-173">Di conseguenza, è estremamente importante assegnare alla finalità esattamente lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="d0725-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="d0725-174">Al termine della creazione della nuova finalità, visualizzerai la pagina corrispondente:</span><span class="sxs-lookup"><span data-stu-id="d0725-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="d0725-176">3. Creare espressioni di esempio</span><span class="sxs-lookup"><span data-stu-id="d0725-176">3. Create example utterances</span></span>

<span data-ttu-id="d0725-177">Aggiungi le espressioni di esempio seguenti all'elenco **Example utterance** (Espressioni di esempio) della finalità **PressButton**:</span><span class="sxs-lookup"><span data-stu-id="d0725-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="d0725-178">activate launch sequence (attiva sequenza di lancio)</span><span class="sxs-lookup"><span data-stu-id="d0725-178">activate launch sequence</span></span>
* <span data-ttu-id="d0725-179">show me a placement hint (mostra un suggerimento per il posizionamento)</span><span class="sxs-lookup"><span data-stu-id="d0725-179">show me a placement hint</span></span>
* <span data-ttu-id="d0725-180">initiate the launch sequence (avvia la sequenza di lancio)</span><span class="sxs-lookup"><span data-stu-id="d0725-180">initiate the launch sequence</span></span>
* <span data-ttu-id="d0725-181">press placement hints button (premi il pulsante dei suggerimenti per il posizionamento)</span><span class="sxs-lookup"><span data-stu-id="d0725-181">press placement hints button</span></span>
* <span data-ttu-id="d0725-182">give me a hint (fornisci un suggerimento)</span><span class="sxs-lookup"><span data-stu-id="d0725-182">give me a hint</span></span>
* <span data-ttu-id="d0725-183">push the launch button (premi il pulsante di lancio)</span><span class="sxs-lookup"><span data-stu-id="d0725-183">push the launch button</span></span>
* <span data-ttu-id="d0725-184">i need a hint (ho bisogno di un suggerimento)</span><span class="sxs-lookup"><span data-stu-id="d0725-184">i need a hint</span></span>
* <span data-ttu-id="d0725-185">press the reset button (premi il pulsante di reimpostazione)</span><span class="sxs-lookup"><span data-stu-id="d0725-185">press the reset button</span></span>
* <span data-ttu-id="d0725-186">time to reset the experience (tempo per reimpostare l'esperienza)</span><span class="sxs-lookup"><span data-stu-id="d0725-186">time to reset the experience</span></span>
* <span data-ttu-id="d0725-187">go ahead and launch the rocket (vai avanti e lancia il missile)</span><span class="sxs-lookup"><span data-stu-id="d0725-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="d0725-188">Dopo aver aggiunto tutte le espressioni di esempio, la pagina della finalità PressButton dovrebbe essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="d0725-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="d0725-190">Ai fini di questa esercitazione, il progetto Unity farà riferimento alle parole 'hint' (suggerimento), 'hints' (suggerimenti), 'reset' (reimpostazione) e 'launch' (lancia).</span><span class="sxs-lookup"><span data-stu-id="d0725-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="d0725-191">Di conseguenza, è estremamente importante che le parole vengano scritte esattamente nello stesso modo.</span><span class="sxs-lookup"><span data-stu-id="d0725-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="d0725-192">4. Creare entità</span><span class="sxs-lookup"><span data-stu-id="d0725-192">4. Create entities</span></span>

<span data-ttu-id="d0725-193">Dalla pagina della finalità PressButton passa alla pagina Build (Compila) > App Assets (Asset app) > **Entities** (Entità), quindi fai clic su **Create new entity** (Crea nuova entità) e immetti i valori seguenti nella finestra popup **Create new entity** (Crea nuova entità):</span><span class="sxs-lookup"><span data-stu-id="d0725-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create new entity** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="d0725-194">In **Entity name** (Nome entità) immetti **Action** (Azione)</span><span class="sxs-lookup"><span data-stu-id="d0725-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="d0725-195">In **Entity type** (Tipo entità) seleziona **Simple** (Semplice)</span><span class="sxs-lookup"><span data-stu-id="d0725-195">For **Entity type**, select **Simple**</span></span>

<span data-ttu-id="d0725-196">Fai quindi clic sul pulsante **Done** (Fine) per creare la nuova entità:</span><span class="sxs-lookup"><span data-stu-id="d0725-196">Then click the **Done** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="d0725-198">**Ripeti** il passaggio precedente per creare un'altra entità denominata **Target**, in modo da avere due entità denominate Action (Azione) e Target:</span><span class="sxs-lookup"><span data-stu-id="d0725-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="d0725-200">Ai fini di questa esercitazione, il progetto Unity farà riferimento a queste entità in base al nome, ad esempio 'Action' (Azione) e 'Target'.</span><span class="sxs-lookup"><span data-stu-id="d0725-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="d0725-201">Di conseguenza, è estremamente importante assegnare alle entità esattamente lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="d0725-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="d0725-202">5. Assegnare entità alle espressioni di esempio</span><span class="sxs-lookup"><span data-stu-id="d0725-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="d0725-203">Dalla pagina Entities (Entità) torna alla pagina della finalità **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="d0725-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="d0725-204">Dopo essere tornato alla pagina della finalità PressButton, fai clic sulla parola **go** (vai) e quindi sulla parola **ahead** (avanti) e infine scegli **Action (Simple)** (Azione - Semplice) dal menu popup contestuale per etichettare **go ahead** (vai avanti) come valore dell'entità **Action** (Azione):</span><span class="sxs-lookup"><span data-stu-id="d0725-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="d0725-206">La frase **go ahead** (vai avanti) è ora definita come valore dell'entità **Action** (Azione).</span><span class="sxs-lookup"><span data-stu-id="d0725-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="d0725-207">Se passi il cursore del mouse sopra il nome dell'entità Action (Azione), puoi visualizzare il valore dell'entità Action (Azione) associato:</span><span class="sxs-lookup"><span data-stu-id="d0725-207">If you hover your mouse cursor above the Action entity name, you can see the associated Action entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="d0725-209">La linea rossa visualizzata sotto l'etichetta nell'immagine precedente indica che il valore dell'entità non è stato stimato. Questa operazione verrà risolta quando esegui il training del modello nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="d0725-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="d0725-210">Fai quindi clic sulla parola **launch** (lancia) e infine scegli **Target (Simple)** (Target - Semplice) dal menu popup contestuale per etichettare **launch** (lancia) come valore dell'entità **Target**:</span><span class="sxs-lookup"><span data-stu-id="d0725-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="d0725-212">La parola **launch** (lancia) è ora definita come valore dell'entità **Target**.</span><span class="sxs-lookup"><span data-stu-id="d0725-212">The **launch** word is now defined as a **Target** entity value.</span></span> <span data-ttu-id="d0725-213">Se passi il cursore del mouse sopra il nome dell'entità Target, puoi visualizzare il valore dell'entità Target associato:</span><span class="sxs-lookup"><span data-stu-id="d0725-213">If you hover your mouse cursor above the Target entity name, you can see the associated Target entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="d0725-215">L'espressione di esempio della finalità PressButton 'go ahead and launch the rocket' (vai avanti e lancia il missile) è ora configurata per essere stimata come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d0725-215">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="d0725-216">Finalità: PressButton</span><span class="sxs-lookup"><span data-stu-id="d0725-216">Intent: PressButton</span></span>
* <span data-ttu-id="d0725-217">Entità Action (Azione): go ahead (vai avanti)</span><span class="sxs-lookup"><span data-stu-id="d0725-217">Action entity: go ahead</span></span>
* <span data-ttu-id="d0725-218">Entità Target: launch (lancia)</span><span class="sxs-lookup"><span data-stu-id="d0725-218">Target entity: launch</span></span>

<span data-ttu-id="d0725-219">**Ripeti**  il processo in due passaggi sopra descritto per assegnare un'etichetta di entità Action (Azione) e Target a ogni espressione di esempio, tenendo presente che le parole seguenti devono essere etichettate come entità **Target**:</span><span class="sxs-lookup"><span data-stu-id="d0725-219">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="d0725-220">**hint** (suggerimento) (il target è HintsButton nel progetto Unity)</span><span class="sxs-lookup"><span data-stu-id="d0725-220">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="d0725-221">**hints** (suggerimenti) (il target è HintsButton nel progetto Unity)</span><span class="sxs-lookup"><span data-stu-id="d0725-221">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="d0725-222">**reset** (reimpostazione) (il target è ResetButton nel progetto Unity)</span><span class="sxs-lookup"><span data-stu-id="d0725-222">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="d0725-223">**launch** (lancia) (il target è LaunchButton nel progetto Unity)</span><span class="sxs-lookup"><span data-stu-id="d0725-223">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="d0725-224">Dopo aver etichettato tutte le espressioni di esempio, la pagina della finalità PressButton dovrebbe essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="d0725-224">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

<span data-ttu-id="d0725-226">Come metodo alternativo per verificare che siano state assegnate le entità corrette, fai clic sul menu **View options** (Opzioni vista) e passa alla vista **Show entity values** (Mostra valori entità):</span><span class="sxs-lookup"><span data-stu-id="d0725-226">For an alternative way to double-check that you have assigned the correct entities, click the **View options** menu and switch the view to **Show entity values**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

<span data-ttu-id="d0725-228">Ora, con la vista impostata in modo da mostrare i valori delle entità, puoi passare il cursore del mouse sulle parole e le frasi con etichetta per verificare rapidamente il nome dell'entità assegnata:</span><span class="sxs-lookup"><span data-stu-id="d0725-228">Now, with the view set to show entity values, you can hover the mouse courser over the labeled words and phrases to quickly verify the assigned entity name:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="d0725-230">6. Eseguire il training, il test e la pubblicazione dell'app</span><span class="sxs-lookup"><span data-stu-id="d0725-230">6. Train, test, and publish the app</span></span>

<span data-ttu-id="d0725-231">Per eseguire il training dell'app, fai clic sul pulsante **Train** (Esegui training) e attendi il completamento del processo di training:</span><span class="sxs-lookup"><span data-stu-id="d0725-231">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="d0725-233">Come puoi vedere nell'immagine precedente, le linee rosse sotto tutte le etichette sono state rimosse, a indicare che tutti i valori delle entità sono stati stimati.</span><span class="sxs-lookup"><span data-stu-id="d0725-233">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="d0725-234">Osserva inoltre che l'icona di stato a sinistra del pulsante Train (Esegui training) ha cambiato colore da rosso a verde.</span><span class="sxs-lookup"><span data-stu-id="d0725-234">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="d0725-235">Al termine dell'elaborazione del training, fai clic sul pulsante **Test**, quindi digita **go ahead and launch the rocket** (vai avanti e lancia il missile) e premi INVIO:</span><span class="sxs-lookup"><span data-stu-id="d0725-235">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="d0725-237">Dopo l'elaborazione dell'espressione di test, fai clic su **Inspect** (Ispeziona) per visualizzare il risultato del test:</span><span class="sxs-lookup"><span data-stu-id="d0725-237">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="d0725-238">Finalità: PressButton (con un'attendibilità del 98,5%)</span><span class="sxs-lookup"><span data-stu-id="d0725-238">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="d0725-239">Entità Action (Azione): go ahead (vai avanti)</span><span class="sxs-lookup"><span data-stu-id="d0725-239">Action entity: go ahead</span></span>
* <span data-ttu-id="d0725-240">Entità Target: launch (lancia)</span><span class="sxs-lookup"><span data-stu-id="d0725-240">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="d0725-242">Per pubblicare l'app, fai clic sul pulsante **Publish** (Pubblica) in alto a destra, quindi nella finestra popup **Choose your publishing slot and settings** (Scegli lo slot e le impostazioni di pubblicazione) seleziona **Production** (Produzione) e fai clic sul pulsante **Publish** (Pubblica):</span><span class="sxs-lookup"><span data-stu-id="d0725-242">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Publish** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="d0725-244">Attendi il completamento del processo di pubblicazione:</span><span class="sxs-lookup"><span data-stu-id="d0725-244">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a><span data-ttu-id="d0725-246">7. Assegnare una risorsa di stima di Azure all'app</span><span class="sxs-lookup"><span data-stu-id="d0725-246">7. Assign an Azure prediction resource to the app</span></span>

<span data-ttu-id="d0725-247">Passa alla pagina Manage (Gestisci) > Application Settings (Impostazioni applicazione) > **Azure Resources** (Risorse di Azure):</span><span class="sxs-lookup"><span data-stu-id="d0725-247">Navigate to the Manage > Application Settings > **Azure Resources** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

<span data-ttu-id="d0725-249">Nella pagina Azure Resources (Risorse di Azure) fai clic sul pulsante **Add prediction resource** (Aggiungi risorsa di stima) e seleziona i valori seguenti nella finestra popup **Assign a resource to your app** (Assegna una risorsa all'app):</span><span class="sxs-lookup"><span data-stu-id="d0725-249">On the Azure Resources page, click the **Add prediction resource** button and select the following values in the **Assign a resource to your app** popup window:</span></span>

* <span data-ttu-id="d0725-250">In **Tenant name** (Nome tenant) seleziona il nome del tenant</span><span class="sxs-lookup"><span data-stu-id="d0725-250">For **Tenant name**, select your tenant name</span></span>
* <span data-ttu-id="d0725-251">In **Subscription Name** (Nome sottoscrizione) seleziona la stessa sottoscrizione usata in precedenza nella sezione [Creazione della risorsa Azure Language Understanding](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span><span class="sxs-lookup"><span data-stu-id="d0725-251">For **Subscription Name**, select the same subscription you used earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>
* <span data-ttu-id="d0725-252">In **LUIS resource name** (Nome risorsa LUIS) seleziona la risorsa di stima creata in precedenza nella sezione [Creazione della risorsa Azure Language Understanding](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span><span class="sxs-lookup"><span data-stu-id="d0725-252">For **LUIS resource name**, select the prediction resource you created earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>

<span data-ttu-id="d0725-253">Fai quindi clic sul pulsante **Assign Resource** (Assegna risorsa) per assegnare la risorsa di stima di Azure all'app:</span><span class="sxs-lookup"><span data-stu-id="d0725-253">Then click the **Assign resource** button to assign the Azure prediction resource to your app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

<span data-ttu-id="d0725-255">Dopo l'assegnazione della risorsa, la pagina Azure Resources (Risorse di Azure) dovrebbe essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="d0725-255">When the resource has been assigned, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="d0725-257">Connessione del progetto Unity all'app LUIS</span><span class="sxs-lookup"><span data-stu-id="d0725-257">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="d0725-258">Nella pagina Manage (Gestisci) > Application Settings (Impostazioni applicazione) **Azure Resources** (Risorse di Azure) fai clic sull'icona di **copia** per copiare il contenuto di **Example Query** (Query di esempio):</span><span class="sxs-lookup"><span data-stu-id="d0725-258">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="d0725-260">Tornato nel progetto Unity, nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom**, quindi nella finestra Inspector (Controllo) individua il componente **Lunarcom Intent Recognizer (Script)** (Riconoscimento finalità Lunarcom - Script) e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d0725-260">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="d0725-261">Nel campo **LUIS Endpoint** (Endpoint LUIS) incolla il contenuto di **Example Query** (Query di esempio) copiato nel passaggio precedente:</span><span class="sxs-lookup"><span data-stu-id="d0725-261">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="d0725-263">Test e miglioramento del riconoscimento delle finalità</span><span class="sxs-lookup"><span data-stu-id="d0725-263">Testing and improving the intent recognition</span></span>

<span data-ttu-id="d0725-264">Per usare il riconoscimento delle finalità direttamente nell'editor di Unity, devi consentire al computer di sviluppo di usare la dettatura.</span><span class="sxs-lookup"><span data-stu-id="d0725-264">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="d0725-265">Per verificare questa impostazione, apri **Impostazioni** di Windows, quindi scegli **Privacy** > **Comandi vocali** e assicurati che sia attivato **Riconoscimento vocale online**:</span><span class="sxs-lookup"><span data-stu-id="d0725-265">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="d0725-267">Se ora attivi la modalità di gioco, puoi testare il riconoscimento delle finalità selezionando prima il pulsante relativo al missile.</span><span class="sxs-lookup"><span data-stu-id="d0725-267">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="d0725-268">Supponendo quindi che il computer disponga di un microfono, quando pronunci la prima espressione di esempio, **go ahead and launch the rocket** (vai avanti e lancia il missile) potrai osservare il lancio del modulo lunare LunarModule nello spazio:</span><span class="sxs-lookup"><span data-stu-id="d0725-268">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="d0725-270">Prova tutte le **espressioni di esempio**, quindi alcune **varianti delle espressioni di esempio**, nonché alcune **espressioni casuali**.</span><span class="sxs-lookup"><span data-stu-id="d0725-270">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="d0725-271">Torna quindi a <a href="https://www.luis.ai" target="_blank">LUIS</a> e passa alla pagina Build (Compila) > Improve app performance (Migliora prestazioni app) > **Review endpoint utterances** (Rivedi espressioni endpoint), usa il pulsante di **attivazione/disattivazione** per passare dalla vista predefinita Entities View (Vista entità) a **Tokens View** (Vista token) e quindi rivedi le espressioni:</span><span class="sxs-lookup"><span data-stu-id="d0725-271">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="d0725-272">Nella colonna **Utterance** (Espressione) modifica e rimuovi in base alle esigenze le etichette assegnate in modo da allinearle alla finalità</span><span class="sxs-lookup"><span data-stu-id="d0725-272">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="d0725-273">Nella colonna **Aligned intent** (Finalità allineata) verifica che la finalità sia corretta</span><span class="sxs-lookup"><span data-stu-id="d0725-273">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="d0725-274">Nella colonna **Add/Delete** (Aggiungi/Elimina) fai clic sul pulsante con il segno di spunta verde per aggiungere l'espressione o il pulsante con la x rossa per eliminarla.</span><span class="sxs-lookup"><span data-stu-id="d0725-274">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="d0725-275">Dopo aver esaminato tutte le espressioni desiderate, fai clic sul pulsante **Train** (Esegui training) per ripetere il training del modello e quindi sul pulsante **Publish** (Pubblica) per ripubblicare l'app aggiornata:</span><span class="sxs-lookup"><span data-stu-id="d0725-275">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="d0725-277">Se un'espressione dell'endpoint non è allineata alla finalità PressButton, ma vuoi indicare al modello che l'espressione non ha finalità, puoi modificare Aligned intent (Finalità allineata) impostando None (Nessuna).</span><span class="sxs-lookup"><span data-stu-id="d0725-277">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="d0725-278">**Ripeti** questo processo il numero di volte desiderato per migliorare il modello di app.</span><span class="sxs-lookup"><span data-stu-id="d0725-278">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d0725-279">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="d0725-279">Congratulations</span></span>

<span data-ttu-id="d0725-280">Il progetto ora dispone di comandi di riconoscimento vocale basati sull'intelligenza artificiale, consentendo all'applicazione di riconoscere le finalità degli utenti anche se non pronunciano comandi precisi.</span><span class="sxs-lookup"><span data-stu-id="d0725-280">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="d0725-281">Esegui l'applicazione sul dispositivo per verificare che la funzionalità venga eseguita correttamente.</span><span class="sxs-lookup"><span data-stu-id="d0725-281">Run the application on your device to ensure the feature is working properly.</span></span>
