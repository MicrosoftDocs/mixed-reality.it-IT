---
title: Esercitazioni sui servizi vocali di Azure - 4 Configurazione della comprensione delle finalità e del linguaggio naturale
description: Completa questo corso per ottenere informazioni su come implementare Azure Speech SDK in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8cebe1fb203aeed9a262a2e9f482993b4775e0a6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303662"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Configurazione della comprensione delle finalità e del linguaggio naturale

In questa esercitazione esplorerai il riconoscimento delle finalità del servizio vocale di Azure. Il riconoscimento delle finalità consente di dotare l'applicazione di comandi vocali basati sull'intelligenza artificiale, in cui gli utenti possono pronunciare comandi vocali non specifici e ottenere il riconoscimento delle finalità da parte del sistema.

## <a name="objectives"></a>Obiettivi

* Ottenere informazioni su come configurare finalità, entità ed espressioni nel portale LUIS
* Ottenere informazioni su come implementare la comprensione delle finalità e del linguaggio naturale nell'applicazione

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Lunarcom Intent Recognizer (Script)** (Riconoscimento finalità Lunarcom - Script) all'oggetto Lunarcom:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **RocketLauncher**, trascina il prefab **RocketLauncher_Complete** nella finestra Hierarchy (Gerarchia) e quindi posizionalo in un punto appropriato davanti alla fotocamera, ad esempio:

* Trasforma la **posizione** X = 0, Y = -0.4, Z = 1
* Trasforma la **rotazione** X = 0, Y = 90, Z = 0

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

Nella finestra Hierarchy (Gerarchia) seleziona di nuovo l'oggetto **Lunarcom**, quindi espandi l'oggetto **RocketLauncher_Complete** > **Button** e assegna ognuno degli oggetti figlio dell'oggetto **Buttons** al campo **Lunar Launcher Buttons** (Pulsanti lancio lunare) corrispondente:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>Creazione della risorsa Azure Language Understanding

In questa sezione creerai una risorsa di stima di Azure per l'app LUIS (Language Understanding Intelligent Service) che verrà creata nella sezione successiva.

Accedi ad <a href="https://portal.azure.com" target="_blank">Azure</a> e fai clic su **Crea una risorsa**. Cerca quindi e seleziona **Language Understanding**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

Fai clic sul pulsante **Create** (Crea) per creare un'istanza del servizio:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

Nella pagina Create (Crea) fai clic sull'opzione **Prediction** (Stima) e immetti i valori seguenti:

* In **Subscription** (Sottoscrizione) seleziona **Free Trail** (Prova gratuita) se disponi di una sottoscrizione di prova gratuita, altrimenti seleziona una delle altre sottoscrizioni
* In **Resource group** (Gruppo risorse) fai clic sul collegamento **Create new** (Crea nuovo), immetti un nome appropriato, ad esempio *MRKT-Tutorials*, e quindi fai clic su **OK**

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> Al momento della stesura di questo articolo, non è necessario creare una risorsa di creazione perché quando viene creata l'app LUIS (Language Understanding Intelligent Service) nella sezione successiva viene generata automaticamente una chiave di prova per la creazione in LUIS.

> [!TIP]
> Se disponi già di un altro gruppo di risorse appropriato nell'account di Azure, ad esempio se hai completato l'esercitazione sugli [ancoraggi nello spazio di Azure](mr-learning-asa-01.md), puoi usarlo anziché crearne uno nuovo.

Sempre nella pagina Create (Crea) immetti i valori seguenti:

* In **Name** (Nome) immetti un nome appropriato per il servizio, ad esempio *MRTK-Tutorials-AzureSpeechServices*
* In **Prediction location** (Posizione di stima) scegli una posizione vicina alla posizione fisica degli utenti dell'app, ad esempio *(US) West US* (Stati Uniti occidentali)
* Ai fini di questa esercitazione, in **Prediction pricing tier** (Piano tariffario di stima) seleziona **F0 (5 Calls per second, 10K Calls per month)** (F0 - 5 chiamate al secondo, 10.000 chiamate al mese)

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

Passa quindi alla scheda **Review + create** (Verifica e crea), esamina i dettagli e quindi fai clic sul pulsante **Create** (Crea), disponibile nella parte inferiore della pagina, per creare la risorsa e il nuovo gruppo di risorse se ne hai configurato uno per la creazione:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> Dopo aver fatto clic sul pulsante Create (Crea), dovrai attendere alcuni minuti per la creazione del servizio.

Al termine del processo di creazione delle risorse, visualizzerai il messaggio **Your deployment is complete** (Distribuzione completata):

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>Creazione di un'app LUIS (Language Understanding Intelligent Service)

In questa sezione eseguirai la creazione di un'app LUIS, la configurazione e il training del modello di stima e la connessione alla risorsa di stima di Azure creata nel passaggio precedente.

In particolare, creerai una finalità in base alla quale se l'utente pronuncia un'azione da eseguire, l'app attiverà l'evento Interactable.OnClick() su uno dei tre pulsanti rossi della scena, a seconda del pulsante a cui fa riferimento l'utente.

Se ad esempio l'utente pronuncia **go ahead and launch the rocket** (vai avanti e lancia il missile), l'app stimerà che **vai avanti** indica un'**azione** da eseguire e che l'evento Interactable.OnClick() **target** sia il pulsante di **lancio**.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Creare un'app LUIS
2. Creare finalità
3. Creare espressioni di esempio
4. Creare entità
5. Assegnare entità alle espressioni di esempio
6. Eseguire il training, il test e la pubblicazione dell'app
7. Assegnare una risorsa di stima di Azure all'app

### <a name="1-create-a-luis-app"></a>1. Creare un'app LUIS

Con lo stesso account utente usato durante la creazione della risorsa di Azure nella sezione precedente, accedi a <a href="https://www.luis.ai" target="_blank">LUIS</a>, seleziona il tuo paese e accetta le condizioni per l'utilizzo. Nel passaggio successivo, quando viene visualizzata la richiesta **Link your Azure account** (Collega il tuo account Azure), scegli **Continue using your trial key** (Continua a usare la chiave di prova) per usare invece una risorsa di creazione di Azure.

> [!NOTE]
> Se hai già effettuato l'iscrizione a LUIS e la chiave di prova per la creazione è scaduta, puoi fare riferimento alla documentazione [Eseguire la migrazione a una chiave di creazione delle risorse di Azure](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) per passare ad Azure per la risorsa di creazione LUIS.

Dopo aver eseguito l'accesso, passa alla pagina **My apps** (App personali), quindi fai clic su **Create new app** (Crea nuova app) e immetti i valori seguenti nella finestra popup **Create new app** (Crea nuova app):

* In **Name** (Nome) immetti un nome appropriato, ad esempio *MRTK Tutorials - AzureSpeechServices*
* In **Culture** (Impostazioni cultura) seleziona **English** (Inglese)
* In **Description** (Descrizione) immetti facoltativamente una descrizione appropriata

Fai quindi clic sul pulsante **Done** (Fine) per creare la nuova app:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

Al termine della creazione della nuova app, visualizzerai la pagina **Dashboard** dell'app:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2. Creare finalità

Dalla pagina Dashboard passa alla pagina Build (Compila) > App Assets (Asset app) > **Intents** (Finalità), quindi fai clic su **Create new intent** (Crea nuova finalità) e immetti il valore seguente nella finestra popup **Create new intent** (Crea nuova finalità):

* In **Intent name** (Nome finalità) immetti **PressButton**

Fai quindi clic sul pulsante **Done** (Fine) per creare la nuova finalità:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> Ai fini di questa esercitazione, il progetto Unity farà riferimento a questa finalità in base al nome, ad esempio 'PressButton'. Di conseguenza, è estremamente importante assegnare alla finalità esattamente lo stesso nome.

Al termine della creazione della nuova finalità, visualizzerai la pagina corrispondente:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3. Creare espressioni di esempio

Aggiungi le espressioni di esempio seguenti all'elenco **Example utterance** (Espressioni di esempio) della finalità **PressButton**:

* activate launch sequence (attiva sequenza di lancio)
* show me a placement hint (mostra un suggerimento per il posizionamento)
* initiate the launch sequence (avvia la sequenza di lancio)
* press placement hints button (premi il pulsante dei suggerimenti per il posizionamento)
* give me a hint (fornisci un suggerimento)
* push the launch button (premi il pulsante di lancio)
* i need a hint (ho bisogno di un suggerimento)
* press the reset button (premi il pulsante di reimpostazione)
* time to reset the experience (tempo per reimpostare l'esperienza)
* go ahead and launch the rocket (vai avanti e lancia il missile)

Dopo aver aggiunto tutte le espressioni di esempio, la pagina della finalità PressButton dovrebbe essere simile alla seguente:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> Ai fini di questa esercitazione, il progetto Unity farà riferimento alle parole 'hint' (suggerimento), 'hints' (suggerimenti), 'reset' (reimpostazione) e 'launch' (lancia). Di conseguenza, è estremamente importante che le parole vengano scritte esattamente nello stesso modo.

### <a name="4-create-entities"></a>4. Creare entità

Dalla pagina della finalità PressButton passa alla pagina Build (Compila) > App Assets (Asset app) > **Entities** (Entità), quindi fai clic su **Create new entity** (Crea nuova entità) e immetti i valori seguenti nella finestra popup **Create new entity** (Crea nuova entità):

* In **Entity name** (Nome entità) immetti **Action** (Azione)
* In **Entity type** (Tipo entità) seleziona **Simple** (Semplice)

Fai quindi clic sul pulsante **Done** (Fine) per creare la nuova entità:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

**Ripeti** il passaggio precedente per creare un'altra entità denominata **Target**, in modo da avere due entità denominate Action (Azione) e Target:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> Ai fini di questa esercitazione, il progetto Unity farà riferimento a queste entità in base al nome, ad esempio 'Action' (Azione) e 'Target'. Di conseguenza, è estremamente importante assegnare alle entità esattamente lo stesso nome.

### <a name="5-assign-entities-to-the-example-utterances"></a>5. Assegnare entità alle espressioni di esempio

Dalla pagina Entities (Entità) torna alla pagina della finalità **PressButton**.

Dopo essere tornato alla pagina della finalità PressButton, fai clic sulla parola **go** (vai) e quindi sulla parola **ahead** (avanti) e infine scegli **Action (Simple)** (Azione - Semplice) dal menu popup contestuale per etichettare **go ahead** (vai avanti) come valore dell'entità **Action** (Azione):

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

La frase **go ahead** (vai avanti) è ora definita come valore dell'entità **Action** (Azione). Se passi il cursore del mouse sopra il nome dell'entità Action (Azione), puoi visualizzare il valore dell'entità Action (Azione) associato:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> La linea rossa visualizzata sotto l'etichetta nell'immagine precedente indica che il valore dell'entità non è stato stimato. Questa operazione verrà risolta quando esegui il training del modello nella sezione successiva.

Fai quindi clic sulla parola **launch** (lancia) e infine scegli **Target (Simple)** (Target - Semplice) dal menu popup contestuale per etichettare **launch** (lancia) come valore dell'entità **Target**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

La parola **launch** (lancia) è ora definita come valore dell'entità **Target**. Se passi il cursore del mouse sopra il nome dell'entità Target, puoi visualizzare il valore dell'entità Target associato:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

L'espressione di esempio della finalità PressButton 'go ahead and launch the rocket' (vai avanti e lancia il missile) è ora configurata per essere stimata come indicato di seguito:

* Finalità: PressButton
* Entità Action (Azione): go ahead (vai avanti)
* Entità Target: launch (lancia)

**Ripeti**  il processo in due passaggi sopra descritto per assegnare un'etichetta di entità Action (Azione) e Target a ogni espressione di esempio, tenendo presente che le parole seguenti devono essere etichettate come entità **Target**:

* **hint** (suggerimento) (il target è HintsButton nel progetto Unity)
* **hints** (suggerimenti) (il target è HintsButton nel progetto Unity)
* **reset** (reimpostazione) (il target è ResetButton nel progetto Unity)
* **launch** (lancia) (il target è LaunchButton nel progetto Unity)

Dopo aver etichettato tutte le espressioni di esempio, la pagina della finalità PressButton dovrebbe essere simile alla seguente:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

Come metodo alternativo per verificare che siano state assegnate le entità corrette, fai clic sul menu **View options** (Opzioni vista) e passa alla vista **Show entity values** (Mostra valori entità):

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

Ora, con la vista impostata in modo da mostrare i valori delle entità, puoi passare il cursore del mouse sulle parole e le frasi con etichetta per verificare rapidamente il nome dell'entità assegnata:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a>6. Eseguire il training, il test e la pubblicazione dell'app

Per eseguire il training dell'app, fai clic sul pulsante **Train** (Esegui training) e attendi il completamento del processo di training:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> Come puoi vedere nell'immagine precedente, le linee rosse sotto tutte le etichette sono state rimosse, a indicare che tutti i valori delle entità sono stati stimati. Osserva inoltre che l'icona di stato a sinistra del pulsante Train (Esegui training) ha cambiato colore da rosso a verde.

Al termine dell'elaborazione del training, fai clic sul pulsante **Test**, quindi digita **go ahead and launch the rocket** (vai avanti e lancia il missile) e premi INVIO:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

Dopo l'elaborazione dell'espressione di test, fai clic su **Inspect** (Ispeziona) per visualizzare il risultato del test:

* Finalità: PressButton (con un'attendibilità del 98,5%)
* Entità Action (Azione): go ahead (vai avanti)
* Entità Target: launch (lancia)

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

Per pubblicare l'app, fai clic sul pulsante **Publish** (Pubblica) in alto a destra, quindi nella finestra popup **Choose your publishing slot and settings** (Scegli lo slot e le impostazioni di pubblicazione) seleziona **Production** (Produzione) e fai clic sul pulsante **Publish** (Pubblica):

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

Attendi il completamento del processo di pubblicazione:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a>7. Assegnare una risorsa di stima di Azure all'app

Passa alla pagina Manage (Gestisci) > Application Settings (Impostazioni applicazione) > **Azure Resources** (Risorse di Azure):

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

Nella pagina Azure Resources (Risorse di Azure) fai clic sul pulsante **Add prediction resource** (Aggiungi risorsa di stima) e seleziona i valori seguenti nella finestra popup **Assign a resource to your app** (Assegna una risorsa all'app):

* In **Tenant name** (Nome tenant) seleziona il nome del tenant
* In **Subscription Name** (Nome sottoscrizione) seleziona la stessa sottoscrizione usata in precedenza nella sezione [Creazione della risorsa Azure Language Understanding](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)
* In **LUIS resource name** (Nome risorsa LUIS) seleziona la risorsa di stima creata in precedenza nella sezione [Creazione della risorsa Azure Language Understanding](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)

Fai quindi clic sul pulsante **Assign Resource** (Assegna risorsa) per assegnare la risorsa di stima di Azure all'app:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

Dopo l'assegnazione della risorsa, la pagina Azure Resources (Risorse di Azure) dovrebbe essere simile alla seguente:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>Connessione del progetto Unity all'app LUIS

Nella pagina Manage (Gestisci) > Application Settings (Impostazioni applicazione) **Azure Resources** (Risorse di Azure) fai clic sull'icona di **copia** per copiare il contenuto di **Example Query** (Query di esempio):

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

Tornato nel progetto Unity, nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Lunarcom**, quindi nella finestra Inspector (Controllo) individua il componente **Lunarcom Intent Recognizer (Script)** (Riconoscimento finalità Lunarcom - Script) e configuralo come indicato di seguito:

* Nel campo **LUIS Endpoint** (Endpoint LUIS) incolla il contenuto di **Example Query** (Query di esempio) copiato nel passaggio precedente:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>Test e miglioramento del riconoscimento delle finalità

Per usare il riconoscimento delle finalità direttamente nell'editor di Unity, devi consentire al computer di sviluppo di usare la dettatura. Per verificare questa impostazione, apri **Impostazioni** di Windows, quindi scegli **Privacy** > **Comandi vocali** e assicurati che sia attivato **Riconoscimento vocale online**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

Se ora attivi la modalità di gioco, puoi testare il riconoscimento delle finalità selezionando prima il pulsante relativo al missile. Supponendo quindi che il computer disponga di un microfono, quando pronunci la prima espressione di esempio, **go ahead and launch the rocket** (vai avanti e lancia il missile) potrai osservare il lancio del modulo lunare LunarModule nello spazio:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

Prova tutte le **espressioni di esempio**, quindi alcune **varianti delle espressioni di esempio**, nonché alcune **espressioni casuali**.

Torna quindi a <a href="https://www.luis.ai" target="_blank">LUIS</a> e passa alla pagina Build (Compila) > Improve app performance (Migliora prestazioni app) > **Review endpoint utterances** (Rivedi espressioni endpoint), usa il pulsante di **attivazione/disattivazione** per passare dalla vista predefinita Entities View (Vista entità) a **Tokens View** (Vista token) e quindi rivedi le espressioni:

* Nella colonna **Utterance** (Espressione) modifica e rimuovi in base alle esigenze le etichette assegnate in modo da allinearle alla finalità
* Nella colonna **Aligned intent** (Finalità allineata) verifica che la finalità sia corretta
* Nella colonna **Add/Delete** (Aggiungi/Elimina) fai clic sul pulsante con il segno di spunta verde per aggiungere l'espressione o il pulsante con la x rossa per eliminarla.

Dopo aver esaminato tutte le espressioni desiderate, fai clic sul pulsante **Train** (Esegui training) per ripetere il training del modello e quindi sul pulsante **Publish** (Pubblica) per ripubblicare l'app aggiornata:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> Se un'espressione dell'endpoint non è allineata alla finalità PressButton, ma vuoi indicare al modello che l'espressione non ha finalità, puoi modificare Aligned intent (Finalità allineata) impostando None (Nessuna).

**Ripeti** questo processo il numero di volte desiderato per migliorare il modello di app.

## <a name="congratulations"></a>Lezione completata

Il progetto ora dispone di comandi di riconoscimento vocale basati sull'intelligenza artificiale, consentendo all'applicazione di riconoscere le finalità degli utenti anche se non pronunciano comandi precisi. Esegui l'applicazione sul dispositivo per verificare che la funzionalità venga eseguita correttamente.
