---
title: Modulo SpeechSDK di MR Learning-riconoscimento vocale e trascrizione
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485782"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="95a46-104">4. Configurazione della finalità e della comprensione del linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="95a46-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="95a46-105">In questa lezione verrà illustrata la funzionalità finalità del servizio riconoscimento vocale di Azure.</span><span class="sxs-lookup"><span data-stu-id="95a46-105">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="95a46-106">La funzionalità Intent consente di dotare l'applicazione di comandi vocali basati su intelligenza artificiale, in cui gli utenti possono pronunciare comandi vocali non specifici e hanno comunque lo scopo di comprendere il sistema.</span><span class="sxs-lookup"><span data-stu-id="95a46-106">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="95a46-107">Durante questa lezione verrà configurato il portale di Azure LUIS, verranno configurate le finalità, le entità e le espressioni, verranno pubblicate le risorse Intent, verrà configurata l'app Unity per la risorsa Intent e si effettuerà la prima chiamata API per finalità.</span><span class="sxs-lookup"><span data-stu-id="95a46-107">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="95a46-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="95a46-108">Objectives</span></span>

- <span data-ttu-id="95a46-109">Informazioni su come configurare la comprensione del linguaggio naturale e della finalità nell'applicazione</span><span class="sxs-lookup"><span data-stu-id="95a46-109">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="95a46-110">Informazioni su come configurare il portale LUIS di Azure</span><span class="sxs-lookup"><span data-stu-id="95a46-110">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="95a46-111">Informazioni su come configurare finalità, entità ed espressioni in Azure</span><span class="sxs-lookup"><span data-stu-id="95a46-111">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="95a46-112">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="95a46-112">Instructions</span></span>
1. <span data-ttu-id="95a46-113">Consenti alla macchina virtuale di abilitare la dettatura. a tale scopo, passare a impostazioni di Windows, selezionare "privacy", "vocale", infine "Inking & digitando" e attivare servizi vocali e digitare suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="95a46-113">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="95a46-117">Accedere al [portale di Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="95a46-117">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="95a46-118">Una volta effettuato l'accesso, fare clic su Crea una risorsa e cercare "Language Understanding" e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="95a46-118">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="95a46-120">Selezionare il pulsante Crea per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="95a46-120">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="95a46-121">Denominare il progetto "Speech_SDK_Learning_Module" e selezionare "con pagamento in base al consumo".</span><span class="sxs-lookup"><span data-stu-id="95a46-121">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="95a46-124">Selezionare l'area geografica.</span><span class="sxs-lookup"><span data-stu-id="95a46-124">Select your Region.</span></span>  <span data-ttu-id="95a46-125">Ai fini di questa esercitazione, selezionare "(Stati Uniti) Stati Uniti occidentali".</span><span class="sxs-lookup"><span data-stu-id="95a46-125">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="95a46-126">Scegliere quindi "F0" per il piano tariffario.</span><span class="sxs-lookup"><span data-stu-id="95a46-126">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="95a46-127">A questo punto fare clic su "Crea" (nell'angolo in basso a sinistra) per creare la risorsa.</span><span class="sxs-lookup"><span data-stu-id="95a46-127">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="95a46-128">Nota: dopo aver fatto clic su "Crea", sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="95a46-128">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="95a46-129">Una volta creata la risorsa, nel portale verrà visualizzata una notifica.</span><span class="sxs-lookup"><span data-stu-id="95a46-129">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="95a46-130">Fare clic su questa notifica e selezionare "Vai alla risorsa".</span><span class="sxs-lookup"><span data-stu-id="95a46-130">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="95a46-131">Dalla pagina "Avvio rapido" del servizio "API LUIS", passare al primo passaggio, selezionare "chiavi" e fare clic su "chiavi". a tale scopo, è possibile fare clic sul collegamento ipertestuale blu "chiavi", come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="95a46-131">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="95a46-132">Il servizio verrà rivelato "chiavi".</span><span class="sxs-lookup"><span data-stu-id="95a46-132">This will reveal your service, "Keys."</span></span> <span data-ttu-id="95a46-133">Salvare una copia di una delle chiavi in modo che sia possibile usarla in un secondo momento nell'app.</span><span class="sxs-lookup"><span data-stu-id="95a46-133">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="95a46-135">Tornare alla pagina "Avvio rapido" nella sezione 2b, fare clic su "portale Language Understanding" (illustrato nell'immagine precedente) per essere reindirizzati alla pagina Web che verrà usata per creare il nuovo servizio nell'applicazione LUIS.</span><span class="sxs-lookup"><span data-stu-id="95a46-135">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="95a46-136">Nota: Quando si raggiunge il "portale di Language Understanding", potrebbe essere necessario eseguire l'accesso, se non lo si è già fatto, con le stesse credenziali del portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="95a46-136">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="95a46-137">Se è la prima volta che si usa LUIS, sarà necessario scorrere fino alla fine della pagina iniziale per trovare e fare clic sul pulsante "Crea LUIS" dell'app.</span><span class="sxs-lookup"><span data-stu-id="95a46-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="95a46-138">Una volta effettuato l'accesso, fare clic su App personali (se non si è attualmente in questa sezione).</span><span class="sxs-lookup"><span data-stu-id="95a46-138">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="95a46-139">È quindi possibile fare clic su Crea nuova app.</span><span class="sxs-lookup"><span data-stu-id="95a46-139">You can then click on Create new app.</span></span> <span data-ttu-id="95a46-140">Assegnare alla nuova app il nome "modulo learning per l'SDK vocale".</span><span class="sxs-lookup"><span data-stu-id="95a46-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="95a46-141">Aggiungere anche "modulo di apprendimento per l'SDK vocale" al campo Description.</span><span class="sxs-lookup"><span data-stu-id="95a46-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="95a46-142">Quindi fare clic su "fine".</span><span class="sxs-lookup"><span data-stu-id="95a46-142">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="95a46-145">Si noti Se l'app deve comprendere una lingua diversa dall'inglese, è necessario modificare le "impostazioni cultura" per la lingua appropriata.</span><span class="sxs-lookup"><span data-stu-id="95a46-145">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="95a46-146">Fare clic su "Compila" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="95a46-146">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="95a46-147">In asset app a sinistra selezionare "Intent", quindi fare clic su "Crea nuovo scopo" e denominarlo "PressButton".</span><span class="sxs-lookup"><span data-stu-id="95a46-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="95a46-149">Nota: È importante usare i nomi di Intent ed entità usati in questa esercitazione, perché l'app Lunarcom ne faranno riferimento in base al nome.</span><span class="sxs-lookup"><span data-stu-id="95a46-149">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="95a46-150">Nota: a questo punto si dispone di 2 Intent, ovvero "PressButton" e "None".</span><span class="sxs-lookup"><span data-stu-id="95a46-150">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="95a46-151">In asset dell'app a sinistra selezionare "entità" e fare clic su "Crea nuova entità" e denominarla "azione" e impostare il tipo di entità su "semplice".</span><span class="sxs-lookup"><span data-stu-id="95a46-151">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="95a46-153">Fare di nuovo clic su "Crea nuova entità" e denominarla "destinazione" e mantenerne il tipo "semplice".</span><span class="sxs-lookup"><span data-stu-id="95a46-153">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="95a46-155">In asset app a sinistra selezionare "Intent" e quindi fare clic sull'intento "PressButton" creato nel passaggio 10.</span><span class="sxs-lookup"><span data-stu-id="95a46-155">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="95a46-157">Fare clic sull'elenco a discesa "Visualizza opzioni" a destra e selezionare "Mostra valori entità".</span><span class="sxs-lookup"><span data-stu-id="95a46-157">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="95a46-159">Fare clic su "immettere un esempio..."</span><span class="sxs-lookup"><span data-stu-id="95a46-159">Click on the “Enter an example…”</span></span> <span data-ttu-id="95a46-160">TextBox.</span><span class="sxs-lookup"><span data-stu-id="95a46-160">textbox.</span></span> <span data-ttu-id="95a46-161">Immettere quindi le espressioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="95a46-161">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="95a46-163">Fare clic sull'elenco a discesa "Visualizza opzioni" a destra e selezionare "Mostra nomi entità".</span><span class="sxs-lookup"><span data-stu-id="95a46-163">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="95a46-165">Verificare che ogni 10 espressioni includa le seguenti etichette di entità nelle posizioni seguenti per 1. facendo clic su parole che non sono state etichettate e, nella finestra popup, selezionando "Rimuovi etichetta" e 2. facendo clic su parole che devono essere etichettate e, nella finestra popup, selezionare l'etichetta appropriata.</span><span class="sxs-lookup"><span data-stu-id="95a46-165">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="95a46-167">A questo punto, per pubblicare il modello, fare clic su "Train" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="95a46-167">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="95a46-168">Al termine dell'elaborazione, fare clic su "test" in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="95a46-168">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="95a46-170">Immettere in "selezionare il pulsante di avvio" nella casella di testo.</span><span class="sxs-lookup"><span data-stu-id="95a46-170">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="95a46-171">Nota: non è stato aggiunto "Select" come azione in nessuno dei nostri enunciati, ma se si fa clic su "ispeziona", il modello ha riconosciuto "Select" come un'entità di azione.</span><span class="sxs-lookup"><span data-stu-id="95a46-171">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="95a46-173">A questo punto, fare clic su "Publish" (pubblica) in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="95a46-173">Now, click "publish" in the top right.</span></span> <span data-ttu-id="95a46-174">Verificare che l'elenco a discesa indichi "produzione" e fare clic su "pubblica" anche nel popup.</span><span class="sxs-lookup"><span data-stu-id="95a46-174">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="95a46-176">Una volta pubblicato, viene visualizzata una barra verde nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="95a46-176">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="95a46-177">Fare clic sulla barra verde per andare alla pagina "Gestisci".</span><span class="sxs-lookup"><span data-stu-id="95a46-177">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="95a46-179">Fare clic su "chiavi ed endpoint" in "Impostazioni applicazione" a sinistra.</span><span class="sxs-lookup"><span data-stu-id="95a46-179">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="95a46-180">Quindi, impostare l'elenco a discesa "pubblica su" come "produzione".</span><span class="sxs-lookup"><span data-stu-id="95a46-180">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="95a46-181">Impostare il fuso orario in modo che corrisponda al proprio e selezionare la casella per includere tutti i punteggi previsti per le finalità.</span><span class="sxs-lookup"><span data-stu-id="95a46-181">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="95a46-182">Infine, fare clic su "Assegna risorsa".</span><span class="sxs-lookup"><span data-stu-id="95a46-182">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="95a46-184">Selezionare tenant dal primo elenco a discesa e selezionare "pagamento a consumo" nell'elenco a discesa nome sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="95a46-184">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="95a46-185">In nome risorsa LUIS scegliere la risorsa creata in precedenza nei passaggi 1-5.</span><span class="sxs-lookup"><span data-stu-id="95a46-185">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="95a46-186">Quindi, fare clic su "Assegna risorsa".</span><span class="sxs-lookup"><span data-stu-id="95a46-186">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="95a46-188">Nota: Assicurarsi di copiare e salvare l'URL dell'endpoint associato alla risorsa appena assegnata in modo che sia facilmente accessibile per la sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="95a46-188">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="95a46-189">Nota: Per il nome del tenant, inserire la società o il profilo creato per questa applicazione.</span><span class="sxs-lookup"><span data-stu-id="95a46-189">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="95a46-190">A questo punto, aprire la nuova app in Unity e selezionare l'oggetto Lunarcom_Base nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="95a46-190">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="95a46-191">Fare clic su "Aggiungi componente" nel pannello di controllo e cercare e selezionare "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="95a46-191">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="95a46-193">Nel campo Luis endpoint di "LunarcomIntentRecognizer" nel pannello Inspector immettere l'URL dell'endpoint salvato nel passaggio 22.</span><span class="sxs-lookup"><span data-stu-id="95a46-193">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="95a46-195">Nota: Nel componente "LunarcomOfflineRecognizer" del pannello Inspector verificare che sia selezionata l'opzione "Disabilita" per "SimulateOfflineMode". in caso contrario, il test del programma non funzionerà.</span><span class="sxs-lookup"><span data-stu-id="95a46-195">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="95a46-196">Premere il pulsante Play nell'editor di Unity e fare clic sul pulsante Rocket per avviare il riconoscimento preventivo.</span><span class="sxs-lookup"><span data-stu-id="95a46-196">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="95a46-197">Pronunciare la frase "selezionare il pulsante Launch Rocket".</span><span class="sxs-lookup"><span data-stu-id="95a46-197">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="95a46-198">Nota: L'app ha riconosciuto la funzione desiderata e attivato il pulsante Rocket.</span><span class="sxs-lookup"><span data-stu-id="95a46-198">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="95a46-200">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="95a46-200">Congratulations</span></span>

<span data-ttu-id="95a46-201">In questa lezione si è appreso come aggiungere comandi di riconoscimento vocale basati su intelligenza artificiale.</span><span class="sxs-lookup"><span data-stu-id="95a46-201">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="95a46-202">A questo punto il programma è in grado di riconoscere le finalità degli utenti anche se non hanno un comando vocale preciso.</span><span class="sxs-lookup"><span data-stu-id="95a46-202">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

