## <a name="lesson-4"></a><span data-ttu-id="83942-101">Lezione 4</span><span class="sxs-lookup"><span data-stu-id="83942-101">Lesson 4</span></span>

<span data-ttu-id="83942-102">Nel capitolo 4, esamineremo la funzionalità di finalità di servizi di riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="83942-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="83942-103">Si verrà configurato il portale di Azure LUIS, la finalità/entità/espressioni di installazione, pubblicare la risorsa con finalità di, connettere l'App nell'app Unity per la risorsa con finalità di ed effettuare la prima chiamata di API con finalità.</span><span class="sxs-lookup"><span data-stu-id="83942-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="83942-104">Consenti la macchina per abilitare la dettatura, a questo scopo, passare alle impostazioni di Windows, selezionare "privacy", quindi "speech" e infine "input penna e digitando" e attivare servizi di riconoscimento vocale e i suggerimenti di digitazione.</span><span class="sxs-lookup"><span data-stu-id="83942-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="83942-108">Nota: per informazioni su come eseguire questa operazione in un Mac/Macbook, fare clic su [qui](linkgoeshere).</span><span class="sxs-lookup"><span data-stu-id="83942-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="83942-109">Accedi per il [portale di Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="83942-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="83942-110">Una volta connessi, fare clic su Crea una risorsa e cercare "Language Understanding Intelligent Service" e fare clic su INVIO.</span><span class="sxs-lookup"><span data-stu-id="83942-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="83942-112">Selezionare il pulsante Crea, per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="83942-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="83942-113">Denominare il progetto "Speech_SDK_Learning_Module" e selezionare "Pagamento a consumo."</span><span class="sxs-lookup"><span data-stu-id="83942-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="83942-116">Selezionare l'area geografica.</span><span class="sxs-lookup"><span data-stu-id="83942-116">Select your Region.</span></span>  <span data-ttu-id="83942-117">Ai fini di questa esercitazione, selezionare "(Stati Uniti) West US".</span><span class="sxs-lookup"><span data-stu-id="83942-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="83942-118">Scegliere "F0" per il piano tariffario.</span><span class="sxs-lookup"><span data-stu-id="83942-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="83942-119">Per creare la risorsa a questo punto fare clic su "Crea" (che si trova nell'angolo inferiore sinistro).</span><span class="sxs-lookup"><span data-stu-id="83942-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="83942-120">Nota: dopo avere fatto clic su "Crea", si dovrà attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="83942-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="83942-121">Verrà visualizzata una notifica nel portale dopo aver creata la risorsa.</span><span class="sxs-lookup"><span data-stu-id="83942-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="83942-122">Fare clic su questa notifica e selezionare "Passare alla risorsa".</span><span class="sxs-lookup"><span data-stu-id="83942-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="83942-123">Dalla pagina del servizio "API LUIS" "" Guida introduttiva, passare al primo passaggio, individuare le "chiavi" e fare clic su "chiavi" (è possibile anche ottenere questo risultato facendo clic sul collegamento ipertestuale blu "chiavi", illustrate nell'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="83942-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="83942-124">Verrà visualizzato il servizio, "Chiavi".</span><span class="sxs-lookup"><span data-stu-id="83942-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="83942-125">Salvare una copia di una delle chiavi in modo che è possibile usarlo in seguito nell'app.</span><span class="sxs-lookup"><span data-stu-id="83942-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="83942-127">Nella pagina di "Avvio rapido" nella sezione 2b, fare clic su "Language Understanding Portal" (illustrato nell'immagine precedente) per essere reindirizzati alla pagina Web che verrà usato per creare il nuovo servizio, all'interno dell'applicazione LUIS.</span><span class="sxs-lookup"><span data-stu-id="83942-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="83942-128">Nota: Al raggiungimento "Language Understanding portale", si potrebbe essere necessario eseguire l'accesso, se non si ha ancora, con le stesse credenziali come il portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="83942-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="83942-129">Se questa è la prima volta, Usa LUIS, è necessario scorrere verso il basso la parte inferiore della pagina di benvenuto, per trovare e fare clic sul pulsante "Crea servizio LUIS" app.</span><span class="sxs-lookup"><span data-stu-id="83942-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="83942-130">Una volta effettuato l'accesso, fare clic su My Apps (se non attualmente in quella sezione).</span><span class="sxs-lookup"><span data-stu-id="83942-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="83942-131">È quindi possibile fare clic su Crea nuova app.</span><span class="sxs-lookup"><span data-stu-id="83942-131">You can then click on Create new app.</span></span> <span data-ttu-id="83942-132">Denominare la nuova app "Speech SDK Learning modulo".</span><span class="sxs-lookup"><span data-stu-id="83942-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="83942-133">Aggiungere "Speech SDK Learning modulo" al campo della descrizione.</span><span class="sxs-lookup"><span data-stu-id="83942-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="83942-134">Quindi fare clic su "done".</span><span class="sxs-lookup"><span data-stu-id="83942-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="83942-137">Nota: Se l'app dovrebbe per comprendere una lingua diversa dall'inglese, è necessario modificare il "Culture" per la lingua appropriata.</span><span class="sxs-lookup"><span data-stu-id="83942-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="83942-138">Fare clic su "Build" che si trova in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="83942-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="83942-139">In risorse di App a sinistra, selezionare "Intent", quindi fare clic su "Crea nuovo finalità" e denominarlo "PressButton."</span><span class="sxs-lookup"><span data-stu-id="83942-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="83942-141">Nota: è importante usare i nomi di finalità ed entità usate in questa esercitazione perché l'app Lunarcom verrà fatto riferimento in base al nome.</span><span class="sxs-lookup"><span data-stu-id="83942-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="83942-142">Per altri progetti, le convenzioni di denominazione possono essere qualsiasi elemento scelto.</span><span class="sxs-lookup"><span data-stu-id="83942-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="83942-143">Nota: sono ora 2 Intent - "PressButton" e "None".</span><span class="sxs-lookup"><span data-stu-id="83942-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="83942-144">In risorse di App a sinistra, selezionare "Entità" e fare clic su "Crea nuova entità" e denominarlo "Action" e mantenere il tipo di entità come "Semplice".</span><span class="sxs-lookup"><span data-stu-id="83942-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="83942-146">Fare clic nuovamente su "Crea nuova entità" e denominarlo "Target" e mantenere nonché il tipo di entità come "Semplice".</span><span class="sxs-lookup"><span data-stu-id="83942-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="83942-148">In asset App a sinistra, selezionare "Intent", quindi fare clic su "PressButton" intende creato nel passaggio 10.</span><span class="sxs-lookup"><span data-stu-id="83942-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="83942-150">Fare clic sull'elenco a discesa "Visualizza le opzioni" a destra e selezionare "Mostra i valori di entità".</span><span class="sxs-lookup"><span data-stu-id="83942-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="83942-152">Fare clic su di "entrano in un esempio..."</span><span class="sxs-lookup"><span data-stu-id="83942-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="83942-153">Nella casella di testo.</span><span class="sxs-lookup"><span data-stu-id="83942-153">textbox.</span></span> <span data-ttu-id="83942-154">Quindi, immettere le espressioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="83942-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="83942-156">Fare clic sull'elenco a discesa "Visualizza le opzioni" a destra e selezionare "Mostra i nomi dell'entità".</span><span class="sxs-lookup"><span data-stu-id="83942-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="83942-158">Assicurarsi che ciascuno dei 10 Utterances hanno le seguenti etichette entità nelle posizioni seguenti da 1.) facendo clic sulle parole che sono etichettate in modo errate e, nella finestra popup, selezionare "Rimuovi etichetta" e 2.) facendo clic sulle parole che devono avere l'etichetta e, nella finestra popup, selezionare l'etichetta appropriata.</span><span class="sxs-lookup"><span data-stu-id="83942-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="83942-160">A questo punto, per pubblicare il modello, fare clic su "Train" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="83942-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="83942-161">Quindi, una volta completato l'elaborazione, fare clic su "Test" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="83942-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="83942-163">Immettere "selezionare il pulsante di avvio" nella casella di testo.</span><span class="sxs-lookup"><span data-stu-id="83942-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="83942-164">Nota: è stata non aggiungiamo "select" come azione in uno dei nostri Utterances - ma se fa clic su "Controlla", il modello "seleziona" è riconosciuto come un'entità di azione.</span><span class="sxs-lookup"><span data-stu-id="83942-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="83942-166">A questo punto, scegliere "pubblica" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="83942-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="83942-167">Fare clic su "pubblica" nella finestra popup anche verificare che l'elenco a discesa afferma "Production".</span><span class="sxs-lookup"><span data-stu-id="83942-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="83942-169">Una volta pubblicato, un indicatore verde apparirà nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="83942-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="83942-170">Fare clic sulla barra di colore verde per essere visualizzata la pagina "Gestisci".</span><span class="sxs-lookup"><span data-stu-id="83942-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="83942-172">A sinistra, fare clic su "Chiavi e gli endpoint" in "Impostazioni".</span><span class="sxs-lookup"><span data-stu-id="83942-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="83942-173">Impostare quindi nell'elenco a discesa "Publish To" come "Production".</span><span class="sxs-lookup"><span data-stu-id="83942-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="83942-174">Impostare il fuso orario in modo che corrispondano a quelle in uso e selezionare la casella per includere tutti i punteggi di intent previsti.</span><span class="sxs-lookup"><span data-stu-id="83942-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="83942-175">Infine, fare clic su "Risorsa di assegnazione".</span><span class="sxs-lookup"><span data-stu-id="83942-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="83942-177">Selezionare tenant dal primo elenco a discesa e selezionare "Uso prepagato" nell'elenco a discesa Nome della sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="83942-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="83942-178">Nella colonna Nome risorsa servizio LUIS, scegliere la risorsa che viene creati in precedenza nei passaggi da 1 a 5.</span><span class="sxs-lookup"><span data-stu-id="83942-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="83942-179">Fare clic su "Assegnare risorse".</span><span class="sxs-lookup"><span data-stu-id="83942-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="83942-181">Nota: assicurarsi di copiare e salvare l'URL dell'Endpoint associato alla risorsa viene semplicemente assegnate in modo che siano facilmente accessibile per la sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="83942-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="83942-182">Nota: per il nome del Tenant, inserire che l'azienda o un profilo creato per questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="83942-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="83942-183">A questo punto, aprire la nuova app in Unity e selezionare l'oggetto Lunarcom_Base nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="83942-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="83942-184">Fare clic su "Add Component" nel Pannello di controllo e cercare e selezionare "LunarcomIntentRecognizer."</span><span class="sxs-lookup"><span data-stu-id="83942-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="83942-186">Nel campo Luis Endpoint di "LunarcomIntentRecognizer" nel Pannello di controllo, immettere l'URL dell'Endpoint che è stato salvato nel passaggio 22.</span><span class="sxs-lookup"><span data-stu-id="83942-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="83942-188">Nota: Nel componente "LunarcomOfflineRecognizer" nel Pannello di controllo, assicurarsi che sia selezionato "Disattiva" per "SimulateOfflineMode" in caso contrario, il programma di testing non funzionerà.</span><span class="sxs-lookup"><span data-stu-id="83942-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="83942-189">Fare clic sul pulsante Play nell'Editor di Unity e fare clic sul pulsante di rocket per avviare riconoscimento delle intenzioni.</span><span class="sxs-lookup"><span data-stu-id="83942-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="83942-190">Utter la frase "selezionare il pulsante di rocket launch".</span><span class="sxs-lookup"><span data-stu-id="83942-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="83942-191">Nota: L'app riconosciuta la funzione desiderata e attivato il pulsante di rocket.</span><span class="sxs-lookup"><span data-stu-id="83942-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="83942-193">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="83942-193">Congratulations</span></span>

<span data-ttu-id="83942-194">Ufficialmente, si è appreso come aggiungere comandi vocali dal programma di SDK di riconoscimento vocale!</span><span class="sxs-lookup"><span data-stu-id="83942-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="83942-195">A questo punto il programma possa riconoscere i comandi di riconoscimento vocale di tutti i tipi di varianti.</span><span class="sxs-lookup"><span data-stu-id="83942-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="83942-196">Testarlo ed è stata una piccola Divertiamoci un po'.</span><span class="sxs-lookup"><span data-stu-id="83942-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="83942-197">Lezione successiva: Speech SDK lezione 5</span><span class="sxs-lookup"><span data-stu-id="83942-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)

