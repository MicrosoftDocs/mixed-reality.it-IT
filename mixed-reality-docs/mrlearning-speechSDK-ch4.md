---
title: Esercitazioni su servizi vocali di Azure-4. Configurazione della finalità e della comprensione del linguaggio naturale
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 8805fa6410e882bce2f0fe8da780dfd5f794cc74
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553999"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. configurazione della finalità e della comprensione del linguaggio naturale

In questa lezione verrà illustrata la funzionalità finalità del servizio riconoscimento vocale di Azure. La funzionalità Intent consente di dotare l'applicazione di comandi vocali basati su intelligenza artificiale, in cui gli utenti possono pronunciare comandi vocali non specifici e hanno comunque lo scopo di comprendere il sistema. Durante questa lezione verrà configurato il portale di Azure LUIS, verranno configurate le finalità, le entità e le espressioni, verranno pubblicate le risorse Intent, verrà configurata l'app Unity per la risorsa Intent e si effettuerà la prima chiamata API per finalità.

## <a name="objectives"></a>Obiettivi

- Informazioni su come configurare la comprensione del linguaggio naturale e della finalità nell'applicazione
- Informazioni su come configurare il portale LUIS di Azure
- Informazioni su come configurare finalità, entità ed espressioni in Azure

## <a name="instructions"></a>Istruzioni

1. Consentire al computer di abilitare la dettatura. A tale scopo, passare a impostazioni di Windows, selezionare "privacy", quindi "voce", seguito da "Inking & digitando" e attivare servizi vocali e digitando suggerimenti.

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. Accedere al portale di [Azure](https://portal.azure.com/). Una volta effettuato l'accesso, fare clic su Crea una risorsa, cercare "Language Understanding" e premere INVIO.

    ![mrlearning-Speech-CH4-1-Step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. Fare clic sul pulsante **Crea** per creare un'istanza del servizio.

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    Assegnare un **nome**alla risorsa, ad esempio *Speech-SDK-Learning-Module*. Per **sottoscrizione**, selezionare *con pagamento in base* al consumo o *traccia gratuita* se si dispone di un account di valutazione. Successivamente, creare un nuovo **gruppo di risorse** facendo clic sul collegamento **Crea nuovo** , immettere un nome, ad esempio *HoloLens-2-Tutorials-Resource-Group*, quindi fare clic sul pulsante **OK** .

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. Selezionare la **posizione di creazione** e il **percorso di runtime**. Ai fini di questa esercitazione, usare *(US) Stati Uniti occidentali*, quindi scegliere *F0 (5 chiamate al secondo, 10.000 chiamate al mese)* per il piano **tariffario** per la creazione e il piano **tariffario di runtime**. Infine, fare clic sul pulsante **Create (crea** ) per creare la risorsa e il nuovo gruppo di risorse.

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    >Dopo aver fatto clic sul pulsante Crea, è necessario attendere la creazione del servizio. l'operazione potrebbe richiedere alcuni minuti.

5. Al termine del processo di creazione delle risorse, verrà visualizzato il messaggio la **distribuzione è stata completata**.

    ![mrlearning-Speech-CH4-1-STEP5. png](images/mrlearning-speech-ch4-1-step5.png)

6. Utilizzando lo stesso account utente, accedere al portale di [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) , selezionare il paese e accettare le condizioni per l'utilizzo.

    >[!NOTE]
    >Quando si raggiunge il portale di Language Understanding, potrebbe essere necessario eseguire l'accesso, se non è già stato fatto, con le stesse credenziali del portale di Azure. Se è la prima volta che si usa LUIS, sarà necessario scorrere verso il basso fino alla fine della pagina iniziale per trovare e fare clic sul pulsante "Crea LUIS" dell'app.

7. Una volta effettuato l'accesso, fare clic su App personali (se non si è attualmente in questa sezione). È quindi possibile fare clic su Crea nuova app. Assegnare alla nuova app il nome "modulo learning per l'SDK vocale". Aggiungere anche "modulo di apprendimento per l'SDK vocale" al campo Description. Quindi fare clic su "fine".

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    >Se l'app deve comprendere una lingua diversa dall'inglese, è necessario modificare le "impostazioni cultura" per la lingua appropriata.

8. Fare clic su "Compila" in alto a destra.

9. In asset app a sinistra selezionare "Intent", quindi fare clic su "Crea nuovo scopo" e denominarlo "PressButton".

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    >È importante usare i nomi di Intent ed entità usati in questa esercitazione, perché l'app Lunarcom ne faranno riferimento in base al nome.

    >[!NOTE]
    >A questo punto dovrebbero essere presenti 2 Intent, ovvero "PressButton" e "None".

10. In asset app a sinistra selezionare "entità", fare clic su "Crea nuova entità", denominarla "azione" e impostare il tipo di entità su "semplice".

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. Fare di nuovo clic su "Crea nuova entità" e denominarlo "destinazione". Mantieni anche il tipo di entità "Simple".

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. In asset app a sinistra selezionare "Intent" e quindi fare clic sull'intento "PressButton" creato nel passaggio 10.

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. Fare clic sull'elenco a discesa "opzioni di visualizzazione" a destra e selezionare "Mostra valori entità".

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    Fare clic su "immettere un esempio..." TextBox. Immettere quindi le espressioni seguenti:

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. Fare clic sull'elenco a discesa "opzioni di visualizzazione" a destra e selezionare "Mostra nomi entità".

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. Verificare che ogni 10 espressioni includa le seguenti etichette di entità nelle posizioni seguenti per 1. facendo clic su parole che non sono state etichettate e, nella finestra popup, selezionando "Rimuovi etichetta" e 2. facendo clic su parole che devono essere etichettate e, nella finestra popup, selezionare l'etichetta appropriata.

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. A questo punto, per pubblicare il modello, fare clic su "Train" in alto a destra. Al termine dell'elaborazione, fare clic su "test" in alto a destra.

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. Immettere in "selezionare il pulsante di avvio" nella casella di testo.

    >[!NOTE]
    >Non è stato aggiunto "Select" come azione in nessuno dei nostri enunciati, ma se si fa clic su "ispeziona", il modello ha riconosciuto "Select" come un'entità di azione.
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. Fare clic su "pubblica" in alto a destra. Assicurarsi che l'elenco a discesa indichi "produzione" e fare clic su "pubblica" anche nella finestra popup.

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. Una volta pubblicato, viene visualizzata una barra verde nella parte superiore della pagina. Fare clic sulla barra verde per visualizzare la pagina "Gestisci".

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. Fare clic su "chiavi ed endpoint" in "Impostazioni applicazione" a sinistra. Quindi, impostare l'elenco a discesa "pubblica su" come "produzione". Impostare il fuso orario in modo che corrisponda al proprio e selezionare la casella per includere tutti i punteggi previsti per le finalità. Infine, fare clic su "Assegna risorsa".

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. Selezionare tenant dal primo elenco a discesa e selezionare "pagamento a consumo" nell'elenco a discesa nome sottoscrizione. In nome risorsa LUIS scegliere la risorsa creata in precedenza nei passaggi 1-5. Quindi, fare clic su "Assegna risorsa".

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    >Assicurarsi di copiare e salvare l'URL dell'endpoint associato alla risorsa appena assegnata, in modo che sia facilmente accessibile per la sezione successiva.

    >[!NOTE]
    >Per il nome del tenant, inserire la società o il profilo creato per questa applicazione.

22. A questo punto, aprire la nuova app in Unity e selezionare l'oggetto Lunarcom_Base nella gerarchia. Fare clic su "Aggiungi componente" nel pannello di controllo e cercare e selezionare "LunarcomIntentRecognizer".

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. Nel campo Luis endpoint di "LunarcomIntentRecognizer" nel pannello Inspector immettere l'URL dell'endpoint salvato nel passaggio 21.

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    >Nel componente "LunarcomOfflineRecognizer" del pannello Inspector verificare che sia selezionata l'opzione "Disabilita" per "SimulateOfflineMode". in caso contrario, il test del programma non funzionerà.

24. Nella finestra del progetto passare al Asset > MRTK. Esercitazioni. GettingStarted > prefabbricati > cartella RocketLauncher, trascinare il RocketLauncher_Complete prefabbricato nella finestra della gerarchia e posizionarlo davanti all'oggetto Lunarcom_Base.

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing01.png)

25. Nella finestra gerarchia selezionare l'oggetto Lunarcom_Base e individuare il componente Lunarcom Intent Recognizer (script), quindi espandere l'oggetto RocketLauncher_Complete > Button e assegnare ciascuno degli oggetti Button ai pulsanti di avvio Lunar corrispondenti campo.

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing02.png)

26. Premere il pulsante Play nell'editor di Unity e fare clic sul pulsante Rocket per avviare il riconoscimento preventivo. Pronunciare la frase "selezionare il pulsante Launch Rocket".

    >[!NOTE]
    >L'app ha riconosciuto la funzione desiderata e attivato il pulsante Rocket.
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Complimenti

In questa lezione si è appreso come aggiungere comandi vocali basati su intelligenza artificiale. A questo punto il programma è in grado di riconoscere le finalità degli utenti, anche se non comunicano comandi vocali precisi.
