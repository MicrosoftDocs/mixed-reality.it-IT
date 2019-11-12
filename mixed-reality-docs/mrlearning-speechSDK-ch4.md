---
title: Esercitazioni su servizi vocali di Azure-4. Configurazione della finalità e della comprensione del linguaggio naturale
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 9235452d9dce38e9d849821a694a5d4c710d8e87
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913284"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="48fe5-105">4. configurazione della finalità e della comprensione del linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="48fe5-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="48fe5-106">In questa lezione verrà illustrata la funzionalità finalità del servizio riconoscimento vocale di Azure.</span><span class="sxs-lookup"><span data-stu-id="48fe5-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="48fe5-107">La funzionalità Intent consente di dotare l'applicazione di comandi vocali basati su intelligenza artificiale, in cui gli utenti possono pronunciare comandi vocali non specifici e hanno comunque lo scopo di comprendere il sistema.</span><span class="sxs-lookup"><span data-stu-id="48fe5-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="48fe5-108">Durante questa lezione verrà configurato il portale di Azure LUIS, verranno configurate le finalità, le entità e le espressioni, verranno pubblicate le risorse Intent, verrà configurata l'app Unity per la risorsa Intent e si effettuerà la prima chiamata API per finalità.</span><span class="sxs-lookup"><span data-stu-id="48fe5-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="48fe5-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="48fe5-109">Objectives</span></span>

- <span data-ttu-id="48fe5-110">Informazioni su come configurare la comprensione del linguaggio naturale e della finalità nell'applicazione</span><span class="sxs-lookup"><span data-stu-id="48fe5-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="48fe5-111">Informazioni su come configurare il portale LUIS di Azure</span><span class="sxs-lookup"><span data-stu-id="48fe5-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="48fe5-112">Informazioni su come configurare finalità, entità ed espressioni in Azure</span><span class="sxs-lookup"><span data-stu-id="48fe5-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="48fe5-113">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="48fe5-113">Instructions</span></span>

1. <span data-ttu-id="48fe5-114">Consenti alla macchina virtuale di abilitare la dettatura. a tale scopo, passare a impostazioni di Windows, selezionare "privacy", "vocale", infine "Inking & digitando" e attivare servizi vocali e digitare suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="48fe5-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="48fe5-118">Accedere al portale di [Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="48fe5-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="48fe5-119">Una volta effettuato l'accesso, fare clic su Crea una risorsa e cercare "Language Understanding" e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="48fe5-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

    ![mrlearning-Speech-CH4-1-Step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="48fe5-121">Fare clic sul pulsante **Crea** per creare un'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="48fe5-121">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="48fe5-123">Assegnare un **nome**alla risorsa, ad esempio *Speech-SDK-Learning-Module*.</span><span class="sxs-lookup"><span data-stu-id="48fe5-123">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="48fe5-124">Per **sottoscrizione**, selezionare *con pagamento in base* al consumo o *traccia gratuita* se si dispone di un account di valutazione.</span><span class="sxs-lookup"><span data-stu-id="48fe5-124">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="48fe5-125">Successivamente, creare un nuovo **gruppo di risorse** facendo clic sul collegamento **Crea nuovo** , immettere un nome, ad esempio *HoloLens-2-Tutorials-Resource-Group*, quindi fare clic sul pulsante **OK** .</span><span class="sxs-lookup"><span data-stu-id="48fe5-125">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and clicking the **OK** button.</span></span>

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="48fe5-127">Selezionare la **posizione di creazione** e il **percorso di runtime**ai fini di questa esercitazione, usare gli stati *Uniti occidentali*.</span><span class="sxs-lookup"><span data-stu-id="48fe5-127">Select your **Authoring location** and **Runtime location**, for the purpose of this tutorial, use *(US) West US*.</span></span> <span data-ttu-id="48fe5-128">Scegliere quindi *F0 (5 chiamate al secondo, 10.000 chiamate al mese)* per il piano **tariffario di creazione** e il piano **tariffario di runtime**.</span><span class="sxs-lookup"><span data-stu-id="48fe5-128">Then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="48fe5-129">Infine, fare clic sul pulsante **Create (crea** ) per creare la risorsa e il nuovo gruppo di risorse.</span><span class="sxs-lookup"><span data-stu-id="48fe5-129">Finally, click the **Create** button to create the resource as well as the new resource group.</span></span>

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="48fe5-131">Dopo aver fatto clic sul pulsante Crea, è necessario attendere che il servizio venga creato. l'operazione potrebbe richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="48fe5-131">After you click the Create button you will have to wait for the service to be created, this might take a few minute.</span></span>

5. <span data-ttu-id="48fe5-132">Al termine del processo di creazione delle risorse, verrà visualizzato il messaggio la **distribuzione è stata completata**.</span><span class="sxs-lookup"><span data-stu-id="48fe5-132">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-Speech-CH4-1-STEP5. png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="48fe5-134">Utilizzando lo stesso account utente, accedere al portale di [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) , selezionare il paese e accettare le condizioni per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="48fe5-134">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="48fe5-135">Quando si raggiunge il portale di Language Understanding, potrebbe essere necessario eseguire l'accesso, se non lo si è già fatto, con le stesse credenziali del portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="48fe5-135">Upon reaching the Language Understanding portal, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="48fe5-136">Se è la prima volta che si usa LUIS, sarà necessario scorrere fino alla fine della pagina iniziale per trovare e fare clic sul pulsante "Crea LUIS" dell'app.</span><span class="sxs-lookup"><span data-stu-id="48fe5-136">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="48fe5-137">Una volta effettuato l'accesso, fare clic su App personali (se non si è attualmente in questa sezione).</span><span class="sxs-lookup"><span data-stu-id="48fe5-137">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="48fe5-138">È quindi possibile fare clic su Crea nuova app.</span><span class="sxs-lookup"><span data-stu-id="48fe5-138">You can then click on Create new app.</span></span> <span data-ttu-id="48fe5-139">Assegnare alla nuova app il nome "modulo learning per l'SDK vocale".</span><span class="sxs-lookup"><span data-stu-id="48fe5-139">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="48fe5-140">Aggiungere anche "modulo di apprendimento per l'SDK vocale" al campo Description.</span><span class="sxs-lookup"><span data-stu-id="48fe5-140">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="48fe5-141">Quindi fare clic su "fine".</span><span class="sxs-lookup"><span data-stu-id="48fe5-141">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="48fe5-144">Se l'app deve comprendere una lingua diversa dall'inglese, è necessario modificare le "impostazioni cultura" per la lingua appropriata.</span><span class="sxs-lookup"><span data-stu-id="48fe5-144">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="48fe5-145">Fare clic su "Compila" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="48fe5-145">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="48fe5-146">In asset app a sinistra selezionare "Intent", quindi fare clic su "Crea nuovo scopo" e denominarlo "PressButton".</span><span class="sxs-lookup"><span data-stu-id="48fe5-146">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="48fe5-148">È importante usare i nomi di Intent ed entità usati in questa esercitazione, perché l'app Lunarcom ne faranno riferimento in base al nome.</span><span class="sxs-lookup"><span data-stu-id="48fe5-148">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="48fe5-149">A questo punto dovrebbero essere presenti 2 Intent, ovvero "PressButton" e "None".</span><span class="sxs-lookup"><span data-stu-id="48fe5-149">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="48fe5-150">In asset dell'app a sinistra selezionare "entità" e fare clic su "Crea nuova entità" e denominarla "azione" e impostare il tipo di entità su "semplice".</span><span class="sxs-lookup"><span data-stu-id="48fe5-150">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="48fe5-152">Fare di nuovo clic su "Crea nuova entità" e denominarla "destinazione" e mantenerne il tipo "semplice".</span><span class="sxs-lookup"><span data-stu-id="48fe5-152">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="48fe5-154">In asset app a sinistra selezionare "Intent" e quindi fare clic sull'intento "PressButton" creato nel passaggio 10.</span><span class="sxs-lookup"><span data-stu-id="48fe5-154">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="48fe5-156">Fare clic sull'elenco a discesa "Visualizza opzioni" a destra e selezionare "Mostra valori entità".</span><span class="sxs-lookup"><span data-stu-id="48fe5-156">Click on the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="48fe5-158">Fare clic su "immettere un esempio..."</span><span class="sxs-lookup"><span data-stu-id="48fe5-158">Click on the “Enter an example…”</span></span> <span data-ttu-id="48fe5-159">TextBox.</span><span class="sxs-lookup"><span data-stu-id="48fe5-159">textbox.</span></span> <span data-ttu-id="48fe5-160">Immettere quindi le espressioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="48fe5-160">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="48fe5-162">Fare clic sull'elenco a discesa "Visualizza opzioni" a destra e selezionare "Mostra nomi entità".</span><span class="sxs-lookup"><span data-stu-id="48fe5-162">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="48fe5-164">Verificare che ogni 10 espressioni includa le seguenti etichette di entità nelle posizioni seguenti per 1. facendo clic su parole che non sono state etichettate e, nella finestra popup, selezionando "Rimuovi etichetta" e 2. facendo clic su parole che devono essere etichettate e, nella finestra popup, selezionare l'etichetta appropriata.</span><span class="sxs-lookup"><span data-stu-id="48fe5-164">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="48fe5-166">A questo punto, per pubblicare il modello, fare clic su "Train" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="48fe5-166">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="48fe5-167">Al termine dell'elaborazione, fare clic su "test" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="48fe5-167">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="48fe5-169">Immettere in "selezionare il pulsante di avvio" nella casella di testo.</span><span class="sxs-lookup"><span data-stu-id="48fe5-169">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="48fe5-170">Non è stato aggiunto "Select" come azione in nessuno dei nostri enunciati, ma se si fa clic su "ispeziona", il modello ha riconosciuto "Select" come un'entità di azione.</span><span class="sxs-lookup"><span data-stu-id="48fe5-170">We did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="48fe5-172">A questo punto, fare clic su "Publish" (pubblica) in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="48fe5-172">Now, click "publish" in the top right.</span></span> <span data-ttu-id="48fe5-173">Verificare che l'elenco a discesa indichi "produzione" e fare clic su "pubblica" anche nel popup.</span><span class="sxs-lookup"><span data-stu-id="48fe5-173">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="48fe5-175">Una volta pubblicato, viene visualizzata una barra verde nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="48fe5-175">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="48fe5-176">Fare clic sulla barra verde per andare alla pagina "Gestisci".</span><span class="sxs-lookup"><span data-stu-id="48fe5-176">Click on the green bar to be taken to the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="48fe5-178">Fare clic su "chiavi ed endpoint" in "Impostazioni applicazione" a sinistra.</span><span class="sxs-lookup"><span data-stu-id="48fe5-178">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="48fe5-179">Quindi, impostare l'elenco a discesa "pubblica su" come "produzione".</span><span class="sxs-lookup"><span data-stu-id="48fe5-179">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="48fe5-180">Impostare il fuso orario in modo che corrisponda al proprio e selezionare la casella per includere tutti i punteggi previsti per le finalità.</span><span class="sxs-lookup"><span data-stu-id="48fe5-180">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="48fe5-181">Infine, fare clic su "Assegna risorsa".</span><span class="sxs-lookup"><span data-stu-id="48fe5-181">Lastly, Click on "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="48fe5-183">Selezionare tenant dal primo elenco a discesa e selezionare "pagamento a consumo" nell'elenco a discesa nome sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="48fe5-183">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="48fe5-184">In nome risorsa LUIS scegliere la risorsa creata in precedenza nei passaggi 1-5.</span><span class="sxs-lookup"><span data-stu-id="48fe5-184">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="48fe5-185">Quindi, fare clic su "Assegna risorsa".</span><span class="sxs-lookup"><span data-stu-id="48fe5-185">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="48fe5-187">Assicurarsi di copiare e salvare l'URL dell'endpoint associato alla risorsa appena assegnata in modo che sia facilmente accessibile per la sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="48fe5-187">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="48fe5-188">Per il nome del tenant, inserire la società o il profilo creato per questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="48fe5-188">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="48fe5-189">A questo punto, aprire la nuova app in Unity e selezionare l'oggetto Lunarcom_Base nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="48fe5-189">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="48fe5-190">Fare clic su "Aggiungi componente" nel pannello di controllo e cercare e selezionare "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="48fe5-190">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="48fe5-192">Nel campo Luis endpoint di "LunarcomIntentRecognizer" nel pannello Inspector immettere l'URL dell'endpoint salvato nel passaggio 22.</span><span class="sxs-lookup"><span data-stu-id="48fe5-192">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="48fe5-194">Nel componente "LunarcomOfflineRecognizer" del pannello Inspector verificare che sia selezionata l'opzione "Disabilita" per "SimulateOfflineMode". in caso contrario, il test del programma non funzionerà.</span><span class="sxs-lookup"><span data-stu-id="48fe5-194">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="48fe5-195">Premere il pulsante Play nell'editor di Unity e fare clic sul pulsante Rocket per avviare il riconoscimento preventivo.</span><span class="sxs-lookup"><span data-stu-id="48fe5-195">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="48fe5-196">Pronunciare la frase "selezionare il pulsante Launch Rocket".</span><span class="sxs-lookup"><span data-stu-id="48fe5-196">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="48fe5-197">L'app ha riconosciuto la funzione desiderata e attivato il pulsante Rocket.</span><span class="sxs-lookup"><span data-stu-id="48fe5-197">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="48fe5-199">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="48fe5-199">Congratulations</span></span>

<span data-ttu-id="48fe5-200">In questa lezione si è appreso come aggiungere comandi di riconoscimento vocale basati su intelligenza artificiale.</span><span class="sxs-lookup"><span data-stu-id="48fe5-200">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="48fe5-201">A questo punto il programma è in grado di riconoscere le finalità degli utenti anche se non hanno un comando vocale preciso.</span><span class="sxs-lookup"><span data-stu-id="48fe5-201">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>
