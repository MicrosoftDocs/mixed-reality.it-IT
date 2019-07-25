---
title: Modulo SpeechSDK di MR Learning-riconoscimento vocale e trascrizione
description: Completare questo corso per apprendere come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 0cffb9ac8f61f77b77fc5925264b95ba57d94ece
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460340"
---
# <a name="speech-sdk-learning-module---intent-and-natural-language-understanding"></a>Modulo di apprendimento per Speech SDK: finalità e Language Understanding naturali

In questa lezione verrà illustrata la funzionalità finalità del servizio riconoscimento vocale di Azure. La funzionalità Intent consente di dotare l'applicazione di comandi vocali basati su intelligenza artificiale, in cui gli utenti possono pronunciare comandi vocali non specifici e hanno comunque lo scopo di comprendere il sistema. Durante questa lezione verrà configurato il portale di Azure LUIS, verranno configurate le finalità, le entità e le espressioni, verranno pubblicate le risorse Intent, verrà configurata l'app Unity per la risorsa Intent e si effettuerà la prima chiamata API per finalità.

## <a name="objectives"></a>Obiettivi

- Informazioni su come configurare la comprensione del linguaggio naturale e della finalità nell'applicazione
- Informazioni su come configurare il portale LUIS di Azure
- Informazioni su come configurare finalità, entità ed espressioni in Azure

## <a name="instructions"></a>Istruzioni
1. Consenti alla macchina virtuale di abilitare la dettatura. a tale scopo, passare a impostazioni di Windows, selezionare "privacy", "vocale", infine "Inking & digitando" e attivare servizi vocali e digitare suggerimenti.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. Accedere al [portale di Azure](https://portal.azure.com/). Una volta effettuato l'accesso, fare clic su Crea una risorsa e cercare "Language Understanding" e premere INVIO.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Selezionare il pulsante Crea per creare un'istanza di questo servizio. Denominare il progetto "Speech_SDK_Learning_Module" e selezionare "con pagamento in base al consumo".

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Selezionare l'area geografica.  Ai fini di questa esercitazione, selezionare "(Stati Uniti) Stati Uniti occidentali". Scegliere quindi "F0" per il piano tariffario. A questo punto fare clic su "Crea" (nell'angolo in basso a sinistra) per creare la risorsa.

>  Nota: dopo aver fatto clic su "Crea", sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

5. Una volta creata la risorsa, nel portale verrà visualizzata una notifica. Fare clic su questa notifica e selezionare "Vai alla risorsa".

6. Dalla pagina "Avvio rapido" del servizio "API LUIS", passare al primo passaggio, selezionare "chiavi" e fare clic su "chiavi". a tale scopo, è possibile fare clic sul collegamento ipertestuale blu "chiavi", come illustrato nell'immagine seguente. Il servizio verrà rivelato "chiavi". Salvare una copia di una delle chiavi in modo che sia possibile usarla in un secondo momento nell'app.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. Tornare alla pagina "Avvio rapido" nella sezione 2b, fare clic su "portale Language Understanding" (illustrato nell'immagine precedente) per essere reindirizzati alla pagina Web che verrà usata per creare il nuovo servizio nell'applicazione LUIS.

> Nota: Quando si raggiunge il "portale di Language Understanding", potrebbe essere necessario eseguire l'accesso, se non lo si è già fatto, con le stesse credenziali del portale di Azure. Se è la prima volta che si usa LUIS, sarà necessario scorrere fino alla fine della pagina iniziale per trovare e fare clic sul pulsante "Crea LUIS" dell'app.

8. Una volta effettuato l'accesso, fare clic su App personali (se non si è attualmente in questa sezione). È quindi possibile fare clic su Crea nuova app. Assegnare alla nuova app il nome "modulo learning per l'SDK vocale". Aggiungere anche "modulo di apprendimento per l'SDK vocale" al campo Description. Quindi fare clic su "fine".

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> Si noti Se l'app deve comprendere una lingua diversa dall'inglese, è necessario modificare le "impostazioni cultura" per la lingua appropriata.

9. Fare clic su "Compila" in alto a destra.

10. In asset app a sinistra selezionare "Intent", quindi fare clic su "Crea nuovo scopo" e denominarlo "PressButton". 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Nota: È importante usare i nomi di Intent ed entità usati in questa esercitazione, perché l'app Lunarcom ne faranno riferimento in base al nome. 
>
> Nota: a questo punto si dispone di 2 Intent, ovvero "PressButton" e "None".

11. In asset dell'app a sinistra selezionare "entità" e fare clic su "Crea nuova entità" e denominarla "azione" e impostare il tipo di entità su "semplice".

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Fare di nuovo clic su "Crea nuova entità" e denominarla "destinazione" e mantenerne il tipo "semplice".

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. In asset app a sinistra selezionare "Intent" e quindi fare clic sull'intento "PressButton" creato nel passaggio 10.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Fare clic sull'elenco a discesa "Visualizza opzioni" a destra e selezionare "Mostra valori entità". 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Fare clic su "immettere un esempio..." TextBox. Immettere quindi le espressioni seguenti: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Fare clic sull'elenco a discesa "Visualizza opzioni" a destra e selezionare "Mostra nomi entità".

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Verificare che ogni 10 espressioni includa le seguenti etichette di entità nelle posizioni seguenti per 1. facendo clic su parole che non sono state etichettate e, nella finestra popup, selezionando "Rimuovi etichetta" e 2. facendo clic su parole che devono essere etichettate e, nella finestra popup, selezionare l'etichetta appropriata.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. A questo punto, per pubblicare il modello, fare clic su "Train" in alto a destra. Al termine dell'elaborazione, fare clic su "test" in alto a destra.

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Immettere in "selezionare il pulsante di avvio" nella casella di testo.

> Nota: non è stato aggiunto "Select" come azione in nessuno dei nostri enunciati, ma se si fa clic su "ispeziona", il modello ha riconosciuto "Select" come un'entità di azione.
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. A questo punto, fare clic su "Publish" (pubblica) in alto a destra. Verificare che l'elenco a discesa indichi "produzione" e fare clic su "pubblica" anche nel popup. 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. Una volta pubblicato, viene visualizzata una barra verde nella parte superiore della pagina.  Fare clic sulla barra verde per andare alla pagina "Gestisci". 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. Fare clic su "chiavi ed endpoint" in "Impostazioni applicazione" a sinistra. Quindi, impostare l'elenco a discesa "pubblica su" come "produzione". Impostare il fuso orario in modo che corrisponda al proprio e selezionare la casella per includere tutti i punteggi previsti per le finalità. Infine, fare clic su "Assegna risorsa".

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Selezionare tenant dal primo elenco a discesa e selezionare "pagamento a consumo" nell'elenco a discesa nome sottoscrizione. In nome risorsa LUIS scegliere la risorsa creata in precedenza nei passaggi 1-5. Quindi, fare clic su "Assegna risorsa". 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Nota: Assicurarsi di copiare e salvare l'URL dell'endpoint associato alla risorsa appena assegnata in modo che sia facilmente accessibile per la sezione successiva.
>
> Nota: Per il nome del tenant, inserire la società o il profilo creato per questa applicazione.

23. A questo punto, aprire la nuova app in Unity e selezionare l'oggetto Lunarcom_Base nella gerarchia. Fare clic su "Aggiungi componente" nel pannello di controllo e cercare e selezionare "LunarcomIntentRecognizer".

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. Nel campo Luis endpoint di "LunarcomIntentRecognizer" nel pannello Inspector immettere l'URL dell'endpoint salvato nel passaggio 22. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Nota: Nel componente "LunarcomOfflineRecognizer" del pannello Inspector verificare che sia selezionata l'opzione "Disabilita" per "SimulateOfflineMode". in caso contrario, il test del programma non funzionerà. 

25. Premere il pulsante Play nell'editor di Unity e fare clic sul pulsante Rocket per avviare il riconoscimento preventivo. Pronunciare la frase "selezionare il pulsante Launch Rocket".

>  Nota: L'app ha riconosciuto la funzione desiderata e attivato il pulsante Rocket.
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Lezione completata

In questa lezione si è appreso come aggiungere comandi di riconoscimento vocale basati su intelligenza artificiale. A questo punto il programma è in grado di riconoscere le finalità degli utenti anche se non hanno un comando vocale preciso.

