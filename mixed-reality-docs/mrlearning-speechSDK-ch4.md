## <a name="lesson-4"></a>Lezione 4

Nel capitolo 4, esamineremo la funzionalità di finalità di servizi di riconoscimento vocale. Si verrà configurato il portale di Azure LUIS, la finalità/entità/espressioni di installazione, pubblicare la risorsa con finalità di, connettere l'App nell'app Unity per la risorsa con finalità di ed effettuare la prima chiamata di API con finalità.

1. Consenti la macchina per abilitare la dettatura, a questo scopo, passare alle impostazioni di Windows, selezionare "privacy", quindi "speech" e infine "input penna e digitando" e attivare servizi di riconoscimento vocale e i suggerimenti di digitazione.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> Nota: per informazioni su come eseguire questa operazione in un Mac/Macbook, fare clic su [qui](linkgoeshere).

2. Accedi per il [portale di Azure](https://portal.azure.com/). Una volta connessi, fare clic su Crea una risorsa e cercare "Language Understanding Intelligent Service" e fare clic su INVIO.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Selezionare il pulsante Crea, per creare un'istanza di questo servizio. Denominare il progetto "Speech_SDK_Learning_Module" e selezionare "Pagamento a consumo."

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Selezionare l'area geografica.  Ai fini di questa esercitazione, selezionare "(Stati Uniti) West US". Scegliere "F0" per il piano tariffario. Per creare la risorsa a questo punto fare clic su "Crea" (che si trova nell'angolo inferiore sinistro).

   >  Nota: dopo avere fatto clic su "Crea", si dovrà attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

5. Verrà visualizzata una notifica nel portale dopo aver creata la risorsa. Fare clic su questa notifica e selezionare "Passare alla risorsa".

6. Dalla pagina del servizio "API LUIS" "" Guida introduttiva, passare al primo passaggio, individuare le "chiavi" e fare clic su "chiavi" (è possibile anche ottenere questo risultato facendo clic sul collegamento ipertestuale blu "chiavi", illustrate nell'immagine seguente). Verrà visualizzato il servizio, "Chiavi". Salvare una copia di una delle chiavi in modo che è possibile usarlo in seguito nell'app.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. Nella pagina di "Avvio rapido" nella sezione 2b, fare clic su "Language Understanding Portal" (illustrato nell'immagine precedente) per essere reindirizzati alla pagina Web che verrà usato per creare il nuovo servizio, all'interno dell'applicazione LUIS.

> Nota: Al raggiungimento "Language Understanding portale", si potrebbe essere necessario eseguire l'accesso, se non si ha ancora, con le stesse credenziali come il portale di Azure. Se questa è la prima volta, Usa LUIS, è necessario scorrere verso il basso la parte inferiore della pagina di benvenuto, per trovare e fare clic sul pulsante "Crea servizio LUIS" app.

8. Una volta effettuato l'accesso, fare clic su My Apps (se non attualmente in quella sezione). È quindi possibile fare clic su Crea nuova app. Denominare la nuova app "Speech SDK Learning modulo". Aggiungere "Speech SDK Learning modulo" al campo della descrizione. Quindi fare clic su "done".

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> Nota: Se l'app dovrebbe per comprendere una lingua diversa dall'inglese, è necessario modificare il "Culture" per la lingua appropriata.

9. Fare clic su "Build" che si trova in alto a destra.

10. In risorse di App a sinistra, selezionare "Intent", quindi fare clic su "Crea nuovo finalità" e denominarlo "PressButton." 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Nota: è importante usare i nomi di finalità ed entità usate in questa esercitazione perché l'app Lunarcom verrà fatto riferimento in base al nome.  Per altri progetti, le convenzioni di denominazione possono essere qualsiasi elemento scelto. 
>
> Nota: sono ora 2 Intent - "PressButton" e "None".

11. In risorse di App a sinistra, selezionare "Entità" e fare clic su "Crea nuova entità" e denominarlo "Action" e mantenere il tipo di entità come "Semplice".

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Fare clic nuovamente su "Crea nuova entità" e denominarlo "Target" e mantenere nonché il tipo di entità come "Semplice".

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. In asset App a sinistra, selezionare "Intent", quindi fare clic su "PressButton" intende creato nel passaggio 10.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Fare clic sull'elenco a discesa "Visualizza le opzioni" a destra e selezionare "Mostra i valori di entità". 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Fare clic su di "entrano in un esempio..." Nella casella di testo. Quindi, immettere le espressioni seguenti: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Fare clic sull'elenco a discesa "Visualizza le opzioni" a destra e selezionare "Mostra i nomi dell'entità".

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Assicurarsi che ciascuno dei 10 Utterances hanno le seguenti etichette entità nelle posizioni seguenti da 1.) facendo clic sulle parole che sono etichettate in modo errate e, nella finestra popup, selezionare "Rimuovi etichetta" e 2.) facendo clic sulle parole che devono avere l'etichetta e, nella finestra popup, selezionare l'etichetta appropriata.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. A questo punto, per pubblicare il modello, fare clic su "Train" in alto a destra. Quindi, una volta completato l'elaborazione, fare clic su "Test" in alto a destra.

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Immettere "selezionare il pulsante di avvio" nella casella di testo.

> Nota: è stata non aggiungiamo "select" come azione in uno dei nostri Utterances - ma se fa clic su "Controlla", il modello "seleziona" è riconosciuto come un'entità di azione.
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. A questo punto, scegliere "pubblica" in alto a destra. Fare clic su "pubblica" nella finestra popup anche verificare che l'elenco a discesa afferma "Production". 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. Una volta pubblicato, un indicatore verde apparirà nella parte superiore della pagina.  Fare clic sulla barra di colore verde per essere visualizzata la pagina "Gestisci". 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. A sinistra, fare clic su "Chiavi e gli endpoint" in "Impostazioni". Impostare quindi nell'elenco a discesa "Publish To" come "Production". Impostare il fuso orario in modo che corrispondano a quelle in uso e selezionare la casella per includere tutti i punteggi di intent previsti. Infine, fare clic su "Risorsa di assegnazione".

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Selezionare tenant dal primo elenco a discesa e selezionare "Uso prepagato" nell'elenco a discesa Nome della sottoscrizione. Nella colonna Nome risorsa servizio LUIS, scegliere la risorsa che viene creati in precedenza nei passaggi da 1 a 5. Fare clic su "Assegnare risorse". 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Nota: assicurarsi di copiare e salvare l'URL dell'Endpoint associato alla risorsa viene semplicemente assegnate in modo che siano facilmente accessibile per la sezione successiva.
>
> Nota: per il nome del Tenant, inserire che l'azienda o un profilo creato per questa applicazione.

23. A questo punto, aprire la nuova app in Unity e selezionare l'oggetto Lunarcom_Base nella gerarchia. Fare clic su "Add Component" nel Pannello di controllo e cercare e selezionare "LunarcomIntentRecognizer."

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. Nel campo Luis Endpoint di "LunarcomIntentRecognizer" nel Pannello di controllo, immettere l'URL dell'Endpoint che è stato salvato nel passaggio 22. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Nota: Nel componente "LunarcomOfflineRecognizer" nel Pannello di controllo, assicurarsi che sia selezionato "Disattiva" per "SimulateOfflineMode" in caso contrario, il programma di testing non funzionerà. 

25. Fare clic sul pulsante Play nell'Editor di Unity e fare clic sul pulsante di rocket per avviare riconoscimento delle intenzioni. Utter la frase "selezionare il pulsante di rocket launch".

>  Nota: L'app riconosciuta la funzione desiderata e attivato il pulsante di rocket.
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Lezione completata

Ufficialmente, si è appreso come aggiungere comandi vocali dal programma di SDK di riconoscimento vocale! A questo punto il programma possa riconoscere i comandi di riconoscimento vocale di tutti i tipi di varianti. Testarlo ed è stata una piccola Divertiamoci un po'.

[Lezione successiva: Speech SDK lezione 5](placeholderlink)

