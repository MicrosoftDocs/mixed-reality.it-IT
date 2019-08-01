---
title: Esercitazioni su servizi vocali di Azure-4. Configurazione della finalità e della comprensione del linguaggio naturale
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 5ca2df56eee3ae41d97de4e8b1e88a39d4d36718
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701953"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="87df4-105">4. Configurazione della finalità e della comprensione del linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="87df4-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="87df4-106">In questa lezione verrà illustrata la funzionalità finalità del servizio riconoscimento vocale di Azure.</span><span class="sxs-lookup"><span data-stu-id="87df4-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="87df4-107">La funzionalità Intent consente di dotare l'applicazione di comandi vocali basati su intelligenza artificiale, in cui gli utenti possono pronunciare comandi vocali non specifici e hanno comunque lo scopo di comprendere il sistema.</span><span class="sxs-lookup"><span data-stu-id="87df4-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="87df4-108">Durante questa lezione verrà configurato il portale di Azure LUIS, verranno configurate le finalità, le entità e le espressioni, verranno pubblicate le risorse Intent, verrà configurata l'app Unity per la risorsa Intent e si effettuerà la prima chiamata API per finalità.</span><span class="sxs-lookup"><span data-stu-id="87df4-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="87df4-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="87df4-109">Objectives</span></span>

- <span data-ttu-id="87df4-110">Informazioni su come configurare la comprensione del linguaggio naturale e della finalità nell'applicazione</span><span class="sxs-lookup"><span data-stu-id="87df4-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="87df4-111">Informazioni su come configurare il portale LUIS di Azure</span><span class="sxs-lookup"><span data-stu-id="87df4-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="87df4-112">Informazioni su come configurare finalità, entità ed espressioni in Azure</span><span class="sxs-lookup"><span data-stu-id="87df4-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="87df4-113">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="87df4-113">Instructions</span></span>
1. <span data-ttu-id="87df4-114">Consenti alla macchina virtuale di abilitare la dettatura. a tale scopo, passare a impostazioni di Windows, selezionare "privacy", "vocale", infine "Inking & digitando" e attivare servizi vocali e digitare suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="87df4-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="87df4-118">Accedere al [portale di Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="87df4-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="87df4-119">Una volta effettuato l'accesso, fare clic su Crea una risorsa e cercare "Language Understanding" e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="87df4-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="87df4-121">Selezionare il pulsante Crea per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="87df4-121">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="87df4-122">Denominare il progetto "Speech_SDK_Learning_Module" e selezionare "con pagamento in base al consumo".</span><span class="sxs-lookup"><span data-stu-id="87df4-122">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="87df4-125">Selezionare l'area geografica.</span><span class="sxs-lookup"><span data-stu-id="87df4-125">Select your Region.</span></span>  <span data-ttu-id="87df4-126">Ai fini di questa esercitazione, selezionare "(Stati Uniti) Stati Uniti occidentali".</span><span class="sxs-lookup"><span data-stu-id="87df4-126">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="87df4-127">Scegliere quindi "F0" per il piano tariffario.</span><span class="sxs-lookup"><span data-stu-id="87df4-127">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="87df4-128">A questo punto fare clic su "Crea" (nell'angolo in basso a sinistra) per creare la risorsa.</span><span class="sxs-lookup"><span data-stu-id="87df4-128">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="87df4-129">Nota: dopo aver fatto clic su "Crea", sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="87df4-129">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="87df4-130">Una volta creata la risorsa, nel portale verrà visualizzata una notifica.</span><span class="sxs-lookup"><span data-stu-id="87df4-130">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="87df4-131">Fare clic su questa notifica e selezionare "Vai alla risorsa".</span><span class="sxs-lookup"><span data-stu-id="87df4-131">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="87df4-132">Dalla pagina "Avvio rapido" del servizio "API LUIS", passare al primo passaggio, selezionare "chiavi" e fare clic su "chiavi". a tale scopo, è possibile fare clic sul collegamento ipertestuale blu "chiavi", come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="87df4-132">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="87df4-133">Il servizio verrà rivelato "chiavi".</span><span class="sxs-lookup"><span data-stu-id="87df4-133">This will reveal your service, "Keys."</span></span> <span data-ttu-id="87df4-134">Salvare una copia di una delle chiavi in modo che sia possibile usarla in un secondo momento nell'app.</span><span class="sxs-lookup"><span data-stu-id="87df4-134">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="87df4-136">Tornare alla pagina "Avvio rapido" nella sezione 2b, fare clic su "portale Language Understanding" (illustrato nell'immagine precedente) per essere reindirizzati alla pagina Web che verrà usata per creare il nuovo servizio nell'applicazione LUIS.</span><span class="sxs-lookup"><span data-stu-id="87df4-136">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="87df4-137">Nota: Quando si raggiunge il "portale di Language Understanding", potrebbe essere necessario eseguire l'accesso, se non lo si è già fatto, con le stesse credenziali del portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="87df4-137">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="87df4-138">Se è la prima volta che si usa LUIS, sarà necessario scorrere fino alla fine della pagina iniziale per trovare e fare clic sul pulsante "Crea LUIS" dell'app.</span><span class="sxs-lookup"><span data-stu-id="87df4-138">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="87df4-139">Una volta effettuato l'accesso, fare clic su App personali (se non si è attualmente in questa sezione).</span><span class="sxs-lookup"><span data-stu-id="87df4-139">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="87df4-140">È quindi possibile fare clic su Crea nuova app.</span><span class="sxs-lookup"><span data-stu-id="87df4-140">You can then click on Create new app.</span></span> <span data-ttu-id="87df4-141">Assegnare alla nuova app il nome "modulo learning per l'SDK vocale".</span><span class="sxs-lookup"><span data-stu-id="87df4-141">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="87df4-142">Aggiungere anche "modulo di apprendimento per l'SDK vocale" al campo Description.</span><span class="sxs-lookup"><span data-stu-id="87df4-142">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="87df4-143">Quindi fare clic su "fine".</span><span class="sxs-lookup"><span data-stu-id="87df4-143">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="87df4-146">Si noti Se l'app deve comprendere una lingua diversa dall'inglese, è necessario modificare le "impostazioni cultura" per la lingua appropriata.</span><span class="sxs-lookup"><span data-stu-id="87df4-146">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="87df4-147">Fare clic su "Compila" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="87df4-147">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="87df4-148">In asset app a sinistra selezionare "Intent", quindi fare clic su "Crea nuovo scopo" e denominarlo "PressButton".</span><span class="sxs-lookup"><span data-stu-id="87df4-148">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="87df4-150">Nota: È importante usare i nomi di Intent ed entità usati in questa esercitazione, perché l'app Lunarcom ne faranno riferimento in base al nome.</span><span class="sxs-lookup"><span data-stu-id="87df4-150">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="87df4-151">Nota: a questo punto si dispone di 2 Intent, ovvero "PressButton" e "None".</span><span class="sxs-lookup"><span data-stu-id="87df4-151">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="87df4-152">In asset dell'app a sinistra selezionare "entità" e fare clic su "Crea nuova entità" e denominarla "azione" e impostare il tipo di entità su "semplice".</span><span class="sxs-lookup"><span data-stu-id="87df4-152">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="87df4-154">Fare di nuovo clic su "Crea nuova entità" e denominarla "destinazione" e mantenerne il tipo "semplice".</span><span class="sxs-lookup"><span data-stu-id="87df4-154">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="87df4-156">In asset app a sinistra selezionare "Intent" e quindi fare clic sull'intento "PressButton" creato nel passaggio 10.</span><span class="sxs-lookup"><span data-stu-id="87df4-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="87df4-158">Fare clic sull'elenco a discesa "Visualizza opzioni" a destra e selezionare "Mostra valori entità".</span><span class="sxs-lookup"><span data-stu-id="87df4-158">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="87df4-160">Fare clic su "immettere un esempio..."</span><span class="sxs-lookup"><span data-stu-id="87df4-160">Click on the “Enter an example…”</span></span> <span data-ttu-id="87df4-161">TextBox.</span><span class="sxs-lookup"><span data-stu-id="87df4-161">textbox.</span></span> <span data-ttu-id="87df4-162">Immettere quindi le espressioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="87df4-162">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="87df4-164">Fare clic sull'elenco a discesa "Visualizza opzioni" a destra e selezionare "Mostra nomi entità".</span><span class="sxs-lookup"><span data-stu-id="87df4-164">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="87df4-166">Verificare che ogni 10 espressioni includa le seguenti etichette di entità nelle posizioni seguenti per 1. facendo clic su parole che non sono state etichettate e, nella finestra popup, selezionando "Rimuovi etichetta" e 2. facendo clic su parole che devono essere etichettate e, nella finestra popup, selezionare l'etichetta appropriata.</span><span class="sxs-lookup"><span data-stu-id="87df4-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="87df4-168">A questo punto, per pubblicare il modello, fare clic su "Train" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="87df4-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="87df4-169">Al termine dell'elaborazione, fare clic su "test" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="87df4-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="87df4-171">Immettere in "selezionare il pulsante di avvio" nella casella di testo.</span><span class="sxs-lookup"><span data-stu-id="87df4-171">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="87df4-172">Nota: non è stato aggiunto "Select" come azione in nessuno dei nostri enunciati, ma se si fa clic su "ispeziona", il modello ha riconosciuto "Select" come un'entità di azione.</span><span class="sxs-lookup"><span data-stu-id="87df4-172">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="87df4-174">A questo punto, fare clic su "Publish" (pubblica) in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="87df4-174">Now, click "publish" in the top right.</span></span> <span data-ttu-id="87df4-175">Verificare che l'elenco a discesa indichi "produzione" e fare clic su "pubblica" anche nel popup.</span><span class="sxs-lookup"><span data-stu-id="87df4-175">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="87df4-177">Una volta pubblicato, viene visualizzata una barra verde nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="87df4-177">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="87df4-178">Fare clic sulla barra verde per andare alla pagina "Gestisci".</span><span class="sxs-lookup"><span data-stu-id="87df4-178">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="87df4-180">Fare clic su "chiavi ed endpoint" in "Impostazioni applicazione" a sinistra.</span><span class="sxs-lookup"><span data-stu-id="87df4-180">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="87df4-181">Quindi, impostare l'elenco a discesa "pubblica su" come "produzione".</span><span class="sxs-lookup"><span data-stu-id="87df4-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="87df4-182">Impostare il fuso orario in modo che corrisponda al proprio e selezionare la casella per includere tutti i punteggi previsti per le finalità.</span><span class="sxs-lookup"><span data-stu-id="87df4-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="87df4-183">Infine, fare clic su "Assegna risorsa".</span><span class="sxs-lookup"><span data-stu-id="87df4-183">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="87df4-185">Selezionare tenant dal primo elenco a discesa e selezionare "pagamento a consumo" nell'elenco a discesa nome sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="87df4-185">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="87df4-186">In nome risorsa LUIS scegliere la risorsa creata in precedenza nei passaggi 1-5.</span><span class="sxs-lookup"><span data-stu-id="87df4-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="87df4-187">Quindi, fare clic su "Assegna risorsa".</span><span class="sxs-lookup"><span data-stu-id="87df4-187">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="87df4-189">Nota: Assicurarsi di copiare e salvare l'URL dell'endpoint associato alla risorsa appena assegnata in modo che sia facilmente accessibile per la sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="87df4-189">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="87df4-190">Nota: Per il nome del tenant, inserire la società o il profilo creato per questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="87df4-190">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="87df4-191">A questo punto, aprire la nuova app in Unity e selezionare l'oggetto Lunarcom_Base nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="87df4-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="87df4-192">Fare clic su "Aggiungi componente" nel pannello di controllo e cercare e selezionare "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="87df4-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="87df4-194">Nel campo Luis endpoint di "LunarcomIntentRecognizer" nel pannello Inspector immettere l'URL dell'endpoint salvato nel passaggio 22.</span><span class="sxs-lookup"><span data-stu-id="87df4-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="87df4-196">Nota: Nel componente "LunarcomOfflineRecognizer" del pannello Inspector verificare che sia selezionata l'opzione "Disabilita" per "SimulateOfflineMode". in caso contrario, il test del programma non funzionerà.</span><span class="sxs-lookup"><span data-stu-id="87df4-196">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="87df4-197">Premere il pulsante Play nell'editor di Unity e fare clic sul pulsante Rocket per avviare il riconoscimento preventivo.</span><span class="sxs-lookup"><span data-stu-id="87df4-197">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="87df4-198">Pronunciare la frase "selezionare il pulsante Launch Rocket".</span><span class="sxs-lookup"><span data-stu-id="87df4-198">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="87df4-199">Nota: L'app ha riconosciuto la funzione desiderata e attivato il pulsante Rocket.</span><span class="sxs-lookup"><span data-stu-id="87df4-199">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="87df4-201">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="87df4-201">Congratulations</span></span>

<span data-ttu-id="87df4-202">In questa lezione si è appreso come aggiungere comandi di riconoscimento vocale basati su intelligenza artificiale.</span><span class="sxs-lookup"><span data-stu-id="87df4-202">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="87df4-203">A questo punto il programma è in grado di riconoscere le finalità degli utenti anche se non hanno un comando vocale preciso.</span><span class="sxs-lookup"><span data-stu-id="87df4-203">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

