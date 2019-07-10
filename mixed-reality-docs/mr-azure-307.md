---
title: MR e Azure Machine learning 307-
description: Completare questo corso di informazioni su come implementare Azure Machine Learning Studio all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, machine learning, Machine Learning, machine learning studio, hololens, coinvolgenti, vr
ms.openlocfilehash: 89d9758dedb6a2389644dda887bfadf5b28f6dd2
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694547"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR e Azure 307: Machine Learning

![versione finale del prodotto-avvio](images/AzureLabs-Lab7-0.png)

In questo corso, si apprenderà come aggiungere funzionalità di Machine Learning (ML) a un'applicazione di realtà mista tramite Azure Machine Learning Studio.

*Azure Machine Learning Studio* è un servizio Microsoft, che offre agli sviluppatori con un numero elevato di algoritmi di machine learning, che possono contribuire con dati di input, output, preparazione e visualizzazione. Questi componenti, è quindi possibile sviluppare un esperimento predittivo analitica, eseguire l'iterazione su di esso e utilizzarlo per il training del modello. Seguire corsi di formazione, è possibile rendere il modello operativa nell'ambito del cloud di Azure, in modo che è possibile quindi assegnare punteggi ai nuovi dati. Per altre informazioni, visitare il [pagina di Azure Machine Learning Studio](https://azure.microsoft.com/en-au/services/machine-learning-studio/).

Dopo aver completato il corso, si avrà un'applicazione immersive visore VR realtà mista e sarà appreso come eseguire le operazioni seguenti:

1.  Fornire una tabella di dati di vendita per il *Azure Machine Learning Studio* portale e la progettazione, un algoritmo per stimare le vendite future di elementi più diffusi.
2.  Creare un **progetto Unity**, che può ricevere e interpretare i dati di stima dal servizio di Machine Learning.
3.  Visualizzare i dati predication visivamente all'interno di **progetto Unity**, fornendo gli elementi di vendita più diffusi su uno scaffale tramite.

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

Questo corso è un'esercitazione completa, che non implicano direttamente eventuali altri laboratori di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 307: Machine Learning</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare l'articolo strumenti](install-the-tools.md), anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](install-the-tools.md#installation-checklist)
- [La versione più recente di Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore
- Accesso a Internet per la configurazione di Azure e il recupero dei dati di Machine Learning

## <a name="before-you-start"></a>Prima di iniziare

Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capitolo 1: configurazione dell'Account di archiviazione Azure

Per usare l'API di traduzione di Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.
1.  Accedi per il [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **gli account di archiviazione** nel menu a sinistra.

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

3.  Nel **gli account di archiviazione** scheda, fare clic su **Add**.

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab7-2.png)

4.  Nel **crea Account di archiviazione** pannello:

    1.  Inserire un **nome** per l'account, tenere presente questo campo accetta solo numeri e lettere minuscole.
    2.  Per la **modello di distribuzione** selezionate **Resource manager**.
    3.  Per la **tipologia Account**, selezionare **archiviazione (utilizzo generico v1)** .
    4.  Per la **Performance**, selezionare **Standard**.
    5.  Per la **replica** selezionate **Read-access-archiviazione geograficamente ridondante (RA-GRS)** .
    6.  Lasciare **trasferimento sicuro obbligatorio** come **disabilitato**.
    7.  Selezionare una **sottoscrizione**.
    4. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
    
    5.  Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

5.  È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab7-3.png)

6.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

7.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>Capitolo 2 - Azure Machine Learning Studio

Usare la *Azure Machine Learning*, è necessario configurare un'istanza del servizio Machine Learning da rendere disponibili all'applicazione.

1.  Nel portale di Azure, fare clic su **New** nell'angolo in alto a sinistra e cercare **dell'area di lavoro di Machine Learning Studio**, premere **invio**.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  La nuova pagina fornirà una descrizione del **dell'area di lavoro di Machine Learning Studio** servizio. AT nella parte inferiore sinistra di questo prompt, fare clic sui **Create** pulsante, per creare un'associazione con questo servizio.

3.  Dopo avere fatto clic su **Create**, verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli sulla nuova **servizio Machine Learning Studio**:

    1.  Inserire la posizione desiderata **nome area di lavoro** per questa istanza del servizio.

    2.  Selezionare una **sottoscrizione**.

    3. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni). 

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche. È consigliabile usare stesso gruppo di risorse usato per la creazione di archiviazione di Azure nel capitolo precedente.

    5.  Per il **account di archiviazione** fare clic su **Usa esistente**, quindi fare clic sul menu a discesa e da lì, fare clic sui **Account di archiviazione** creato nel capitolo precedente.

    6.  Selezionare un valore appropriato **piano tariffario dell'area di lavoro** alle proprie esigenze, nel menu a discesa.

    7.  All'interno di **piano di servizio Web** fare clic su **Create** **nuovi,** quindi inserire un nome digitandolo nel campo di testo.

    8.  Dal **piano di servizio Web tariffario** , selezionare il livello di prezzo di propria scelta. Un livello denominato di test di sviluppo **DEVTEST Standard** deve essere disponibile senza costi aggiuntivi.

    9.  È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.

    10. Fare clic su **Crea**.

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

5.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.

8.  Nella pagina visualizzata, sotto il **collegamenti aggiuntivi** fare clic su **avvia Machine Learning Studio**, che reindirizzerà il browser per il **Machine Learning Studio** portale.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  Usare la **Accedi** pulsante in alto a destra o al centro, per accedere a Machine Learning Studio.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>Capitolo 3 - Machine Learning Studio: Programma di installazione di set di dati

Analizzando i dati esistenti e quindi si prova a prevedere risultati futuri in una delle modalità di algoritmi di Machine Learning è basata sul set di dati esistente. Ciò in genere significa che i dati più esistenti che si dispone, migliore sarà l'algoritmo dovrà essere eseguita prevedere risultati futuri.

Una tabella di esempio viene fornita all'utente, a questo corso, chiamato [ProductsTableCSV e può essere scaricato da qui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> Il file con estensione zip contiene sia la **ProductsTableCSV** e il **.unitypackage**, che servirà nei [capitolo 6](#chapter-6---importing-the-mlproducts-unity-package). Questo pacchetto viene inoltre fornito all'interno di questo capitolo, anche se distinta nel file csv.

Questo set di dati di esempio contiene un record degli oggetti più venduti in ogni ora di ogni giorno dell'anno 2017.
        
![Machine Learning Studio: Programma di installazione di set di dati](images/AzureLabs-Lab7-11.png)

Ad esempio, il giorno 1 del 2017, Vediamoci (ora 13), l'elemento più venduto era salt e pepper.

Questa tabella di esempio contiene le 9998 voci.

1.  Tornando al **Machine Learning Studio** portale, e aggiunge questa tabella come una **Dataset** per il Machine Learning. Eseguire questa operazione facendo il **+ nuovo** pulsante nell'angolo inferiore sinistro della schermata.

    ![Machine Learning Studio: Programma di installazione di set di dati](images/AzureLabs-Lab7-12.png)

2.  Una sezione verrà visualizzata nella parte inferiore e all'interno che vi sia Pannello di navigazione a sinistra. Fare clic su **set di dati**, quindi a destra di quella **dal File locale**.

    ![Machine Learning Studio: Programma di installazione di set di dati](images/AzureLabs-Lab7-13.png)

3.  Caricare il nuovo **set di dati** seguendo questa procedura:

    1. Verrà visualizzata la finestra di caricamento, in cui è possibile **esplorare** sul disco rigido per il nuovo set di dati.

        ![Machine Learning Studio: Programma di installazione di set di dati](images/AzureLabs-Lab7-14.png)

    2.  Una volta selezionato e di nuovo la finestra di caricamento, lasciare la casella di controllo senza tick.

    3.  Nel campo di testo seguente, immettere **ProductsTableCSV.csv** come nome per il set di dati (anche se deve essere aggiunto automaticamente).

    4.  Usando il menu a discesa per **tipo**, selezionare **Generic CSV File con un'intestazione (con estensione csv)** .

    5.  Premere il segno di spunta nella parte inferiore destra della finestra di caricamento, in quello **set di dati** verrà caricato.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>Capitolo 4 - Machine Learning Studio: L'esperimento

Prima di poter compilare il sistema di machine learning, è necessario creare un esperimento, per convalidare la teoria sui dati. Con i risultati, sarà possibile sapere se sono necessari più dati o se è presente alcuna correlazione tra i dati e un risultato possibili.

Per iniziare a creare un esperimento:

1.  Fare clic nuovamente sul **+ nuovo** sulla sinistra nella parte inferiore della pagina e quindi fare clic su **esperimento** > **esperimento vuoto**.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-15.png)

2.  Verrà visualizzata una nuova pagina con un esperimento vuoto:

3.  Nel pannello a sinistra espandere **Saved Datasets** > **My Datasets** e trascinare il **ProductsTableCSV** al **area di disegno esperimento**.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-16.png)

4.  Nel pannello a sinistra, espandere **Data Transformation** > **Sample and Split**. Trascinare quindi il **Split Data** elemento per il **area di disegno esperimento**. L'elemento di suddivisione dei dati verrà suddiviso il set di dati in due parti. Una parte si userà per il training di algoritmi di machine learning. La seconda parte verrà utilizzata per valutare l'accuratezza dell'algoritmo generato.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-17.png)

5.  Nel Pannello di destra (durante la suddivisione dei dati nell'area di disegno viene selezionato), modificare il **frazione di righe nel primo set di dati di output** al **0,7**. Si suddivideranno i dati in due parti, la prima parte è 70% dei dati e la seconda parte sarà il restante 30%. Per garantire che i dati vengono suddivisi in modo casuale, verificare che il **suddivisione casuale** casella di controllo rimanga selezionata.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-18.png)

6.  Trascinare una connessione dalla base del **ProductsTableCSV** elemento nell'area di disegno nella parte superiore dell'elemento di dati di divisione. Ciò si connetterà gli elementi e inviare il **ProductsTableCSV** output di set di dati (dati) della suddivisione dei dati di input.  

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-19.png)

7.  Nel **esperimenti** pannello sul lato sinistro, espandere **Machine Learning** > **Train**. Trascinare il **Train Model** elemento indietro nell'area di disegno dell'esperimento. Area di disegno deve avere lo stesso aspetto come di seguito.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-20.png)

8.  Dal ***in basso a sinistra*** delle **Split Data** elemento trascinare una connessione al **in alto a destra** del **Train Model** elemento. La prima divisione 70% del set di dati userà il modello di training per eseguire il training dell'algoritmo.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-21.png)

9.  Selezionare il **Train Model** elemento nell'area di disegno e nel **proprietà** fare clic su pannello (sul lato destro della finestra del browser) il **Avvia selettore di colonna** pulsante.

10. Nella casella di testo digitare **prodotto** e quindi premere **invio**, *prodotto* verrà impostato come una colonna per il training di stime. In seguito, fare clic sui **segni di graduazione** nell'angolo in basso a destra per chiudere la finestra di dialogo di selezione.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-22.png)

11. Si intende eseguire il training di un **Multiclass Logistic Regression** algoritmo per stimare i più venduti **prodotto** in base all'ora del giorno e la data. È oltre l'ambito di questo documento illustrano in dettaglio i diversi algoritmi disponibili in Azure Machine Learning studio, tuttavia, è possibile trovare informazioni dal [foglio informativo di algoritmi di Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. Nel pannello elementi esperimento a sinistra, espandere **Machine Learning** > **modello di inizializzazione** > **classificazione**, trascinare il  **Regressione logistica multiclasse** elemento all'area di disegno dell'esperimento.

13. Connettere l'output, dal livello inferiore di **Multiclass Logistic Regression**, all'input dell'angolo superiore sinistro il **Train Model** elemento.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-23.png)

14. Nell'elenco di elementi di esperimento nel pannello a sinistra, espandere **Machine Learning** > **punteggio**, trascinare il **Score Model** elemento nell'area di lavoro.

15. Connettere l'output, dal livello inferiore di **Train Model**, all'input dell'angolo superiore sinistro il **Score Model**.

16. Connettere l'output in basso a destra **Split Data**, l'input superiore destro del **Score Model** elemento.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-24.png)

17. Nell'elenco degli **esperimento** gli elementi del pannello a sinistra, espandere **Machine Learning** > **Evaluate**e trascinare il **Evaluate Model** elemento nell'area di disegno.

18. Connettere l'output dal **Score Model** all'input dell'angolo superiore sinistro il **Evaluate Model**.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-25.png)

19. Aver creato il primo esperimento di Machine Learning. È ora possibile salvare ed eseguire l'esperimento. Nel menu nella parte inferiore della pagina, fare clic sui **salvare** per salvare l'esperimento e quindi fare clic su **eseguire** all'inizio dell'esperimento.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-26.png)

20. È possibile vedere le **stato** dell'esperimento in alto a destra dell'area di disegno. Attendere alcuni istanti per l'esperimento terminare.

    > Se si dispone di un set di dati di grandi dimensioni (reali) è probabile che l'esperimento può richiedere ore per l'esecuzione.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-27.png)

21. Fare clic con il pulsante destro sul **Evaluate Model** nell'area di disegno e gli articoli dal passaggio del mouse menu di scelta rapida del mouse su **i risultati della valutazione**, quindi selezionare **Visualize**.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-28.png)

22. Verrà visualizzati i risultati della valutazione che mostra i risultati stimati e i risultati effettivi. Questo metodo utilizza il 30% del set di dati originale, che è stata suddivisa in precedenza, per valutare il modello. È possibile visualizzare che i risultati non sono eccezionali, che idealmente sarebbe necessario il numero più alto in ogni riga di essere l'elemento evidenziato nelle colonne.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-29.png)

23. Chiudi il **risultati**.

24. Per usare il modello appena sottoposto a training di Machine Learning è necessario esporre come un **servizio Web**. A tale scopo, fare clic sui **Set Up Web Service** dal menu di elemento nel menu nella parte inferiore della pagina e fare clic su **servizio Web predittivo**.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-30.png)

25. Verrà creata una nuova scheda e il modello di training uniti per creare il nuovo servizio web. 

26. Nel menu nella parte inferiore della pagina fare clic su **salvare**, quindi fare clic su **eseguire**. Verrà visualizzato lo stato aggiornato nell'angolo superiore destro dell'area di disegno dell'esperimento.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-31.png)

27. Al termine dell'esecuzione, una **Distribuisci servizio Web** pulsante verrà visualizzato nella parte inferiore della pagina. Si è pronti per distribuire il servizio web. Fare clic su **Distribuisci servizio Web** (classico) nel menu nella parte inferiore della pagina.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-32.png)

    > Il browser può richiedere per consentire un messaggio popup, dovrebbe **consentire**, anche se potrebbe essere necessario premere **Distribuisci servizio Web** anche in questo caso, se non viene visualizzata la pagina di distribuzione. 

28. Dopo aver creato l'esperimento si verrà reindirizzati a un **Dashboard** pagina in cui si avrà la **chiave API** visualizzato. Copiarlo in un blocco note per il momento, sarà necessario nel codice molto presto. Una volta che si sia preso nota prima la chiave API, fare clic sul **REQUEST/RESPONSE** pulsante il **Endpoint predefinito** sezione sotto la chiave.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Se si fa clic sul Test in questa pagina, sarà possibile immettere i dati di input e visualizzare l'output. Immettere il **giorno** e **ora**. Lasciare il **prodotto** voce vuota. Scegliere il **Confirm** pulsante. L'output nella parte inferiore della pagina verrà visualizzato il codice JSON che rappresenta la probabilità di ogni prodotto in corso la scelta.

29. Una nuova pagina web verrà aperta, visualizzare le istruzioni e alcuni esempi sulla struttura richiesta richiesti da Machine Learning Studio. Copia il **URI della richiesta** visualizzato in questa pagina, nel blocco note.

    ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-34.png)

È stato compilato un sistema di machine learning che fornisce il prodotto più probabilmente verranno venduti basato sui dati cronologici di acquisti, in correlazione con l'ora del giorno e giorno dell'anno.

Per chiamare il servizio web, è necessario l'URL per l'endpoint di servizio e una chiave API per il servizio. Fare clic sui **Consume** scheda, dal menu in alto.

Il **consumo** informazioni pagina visualizzerà le informazioni necessarie chiamare il servizio web dal codice. Richiedere una copia di **chiave primaria** e il **richiesta-risposta** URL. Sono necessari questi elementi nel capitolo successivo.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capitolo 5 - configurazione del progetto Unity

Configurare e testare il visore VR Immersivi a realtà mista.

> [!NOTE]
>  Verrà **non** richiedono controller di movimento a questo corso. Se è necessario il supporto di configurazione di visore VR Immersivi, fai clic [qui](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Aprire **Unity** e creare un nuovo progetto Unity chiamato **MR\_MachineLearning.** Verificare che il tipo di progetto è impostato su **3D**.

2.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **Edit** > **preferenze** e quindi dalla nuova finestra, passare al **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

3.  Passare quindi ad **File** > **Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic su di ***commutatore piattaforma***  pulsante.

4.  Assicurarsi anche che:

    1.  **Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**.

        > Per il Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.

    2.  **Tipo di compilazione** è impostata su **D3D**.

    3.  **SDK** è impostata su **installata più recente**.

    4.  **Versione di Visual Studio** è impostata su **installata più recente**.

    5.  **Compilare ed eseguire** è impostata su **computer locale**.

    6.  Non è necessario configurare **scene** subito, come i Broker sono forniti in un secondo momento.

    7.  Le impostazioni rimanenti devono essere lasciate come impostazione predefinita per il momento.

        ![Impostazione del progetto Unity](images/AzureLabs-Lab7-35.png)

5.  Nel **Build Settings** finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il **Inspector** si trova. 

6. In questo pannello, alcune impostazioni devono essere verificati:

    1.  Nel **altre impostazioni** scheda:

        1.  **Scripting** **versione Runtime** deve essere **sperimentale** (.NET 4.6 equivalente)

        2. **Back-end di scripting** deve essere ***.NET***

        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![Impostazione del progetto Unity](images/AzureLabs-Lab7-36.png)

    2.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        - **InternetClient**

            ![Impostazione del progetto Unity](images/AzureLabs-Lab7-37.png)

    3.  Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto

        ![Impostazione del progetto Unity](images/AzureLabs-Lab7-38.png)

    

6.  Nuovamente in **Build Settings** *Unity C#*  progetti non sono più è disattivata; selezionare la casella di controllo accanto a questo. 

7.  Chiudere la finestra Impostazioni di compilazione.

8.  Salvare il progetto (**FILE > Salva progetto**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capitolo 6: importazione del pacchetto Unity MLProducts

A questo corso, è necessario scaricare un pacchetto di Asset Unity chiamato [ **Azure-SIG-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage). Questo pacchetto è dotato di una scena, con tutti gli oggetti che predefiniti, per consentirti di concentrarti su come ottenere tutto funzioni. Il **ShelfKeeper** viene fornito uno script, anche se contiene solo le variabili pubbliche, allo scopo di struttura di configurazione di scena. È necessario eseguire tutte le altre sezioni. 

Per importare il pacchetto:

1.  Con il dashboard di Unity fronte, fare clic su **Assets** nel menu nella parte superiore della schermata, quindi fare clic su **Import Package, pacchetto personalizzato**.

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-39.png)

2.  Usare il selettore file per selezionare i **Azure-SIG-307.unitypackage** del pacchetto e fare clic su **Open**.

3.  Verrà visualizzato un elenco di componenti per questo asset all'utente. Confermare l'importazione facendo **importare**.

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-40.png)

4.  Una volta completato l'importazione, si noterà che alcune nuove cartelle visualizzate nel tuo gioco **pannello progetto**. Questi sono i modelli 3D e i rispettivi materiali che fanno parte della scena già pronto che verranno usati. Si scriverà la maggior parte del codice in questo corso.

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-41.png)

5.  All'interno di **pannello progetto** cartella, fare clic sul **scene** cartella e fare doppio clic sulla scena all'interno di (denominata **MR_MachineLearningScene**). Verrà aperta la scena (vedere la figura seguente). Se mancano i rombi rosso, è sufficiente fare clic sul **Gizmo** pulsante, nella parte superiore destra del **Pannello di gioco**.

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capitolo 7 - controllare le DLL in Unity

Per sfruttare l'uso delle librerie JSON (utilizzato per serializzare e deserializzare), è stata implementata con il pacchetto in che è stata avviata una DLL Newtonsoft. La libreria deve avere la configurazione corretta, anche se è opportuno verificare (in particolare se si verificano problemi con il codice non funziona). 

A tale scopo:

-  Fare clic sul file Newtonsoft all'interno della cartella Plugins ed esaminare i **Pannello di controllo**. Assicurarsi che **piattaforma Any** sia selezionata. Andare alla **scheda UWP** e verificare inoltre **non elabora** sia selezionata.

    ![L'importazione di DLL in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capitolo 8 - creare la classe ShelfKeeper

Il **ShelfKeeper** classe ne ospita i metodi che consentono di controllare l'interfaccia utente e i prodotti generati nella scena.

Come parte del pacchetto importato, si verrà assegnato questa classe, anche se è incompleta. È giunto il momento per completare tale classe:

1.  Fare doppio clic sul **ShelfKeeper** uno script, all'interno di **script** cartella, aprirlo con **Visual Studio 2017**.

2.  Sostituire tutto il codice esistente nello script con il codice seguente, che imposta la data e ora e ha un metodo per la visualizzazione di un prodotto.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.

4.  Indietro nell'Editor di Unity, verificare che il **ShelfKeeper** classe simile di seguito:

    ![Creare la classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Se lo script non ha le destinazioni di riferimento (vale a dire *data (testo Mesh)* ), è sufficiente trascinare gli oggetti corrispondenti dalle **gerarchia pannello**, nei campi di destinazione. Vedere di seguito per una descrizione, se necessario:
    > 
    > 1.  Aprire il **punto Spawn** all'interno della matrice il **ShelfKeeper** per mouse lo script di componente. Una sottosezione apparirà chiamata **dimensioni**, che indica la dimensione della matrice. Tipo **3** nella casella di controllo accanto a **Size** , quindi premere **invio**, e verrà creato di sotto di tre slot.
    > 2. All'interno di **gerarchia** espandere il **visualizzazione cronologica** oggetto (di mouse sulla freccia accanto a esso). Successivamente fare clic sul ***Main Camera*** dall'interno la **gerarchia**, in modo che il **Inspector** Mostra le relative informazioni.
    > 3. Selezionare il **fotocamera principale** nel **gerarchia pannello**. Trascinare il **data** e **ora** oggetti dal **gerarchia pannello** per il **testo data** e **testo della fase di** slot all'interno di **Inspector** del **Main Camera** nel **ShelfKeeper** componente.
    > 4. Trascinare il **Spawn punti** dal **pannello gerarchia** (sotto la *dello scaffale dei* oggetto) per il **3** **elemento**fanno riferimento a destinazioni sotto il **Spawn punto** della matrice, come illustrato nell'immagine.
    > 
    >     ![Creare la classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capitolo 9 - creare la classe ProductPrediction

La classe successiva si intende creare è il **ProductPrediction** classe.

Questa classe è responsabile per:

-   L'esecuzione di query di **servizio di Machine Learning** istanza, che fornisce la data e ora correnti.

-   Durante la deserializzazione della risposta JSON in dati utilizzabili.

-   Interpretazione dei dati, il recupero di prodotti consigliati 3.

-   Chiama il **ShelfKeeper** metodi per visualizzare i dati nella scena della classe.

Per creare questa classe:

1.  Andare alla **gli script** cartella, nella **pannello progetto**.

2.  Pulsante destro del mouse all'interno della cartella **Create**  >   **C# Script**. Chiamare lo script **ProductPrediction**.

3.  Fare doppio clic su nuova **ProductPrediction** script per aprirlo con **Visual Studio 2017**.

4.  Se il **rilevate modifiche ai File** finestra di dialogo visualizzata, fare clic su ***Ricarica soluzione**.

5.  Aggiungere spazi dei nomi seguenti all'inizio della classe ProductPrediction:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  All'interno di **ProductPrediction** classe inserire i seguenti due oggetti che sono costituiti da un numero di classi annidate. Queste classi vengono usate per serializzare e deserializzare il codice JSON per il servizio Machine Learning.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  Aggiungere quindi le variabili seguenti sopra il codice precedente (in modo che il codice JSON correlato codice è riportato alla fine dello script, tutti gli altri codice riportato di seguito e all'esterno di quelle):

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Assicurarsi di inserire le **chiave primaria** e **endpoint di richiesta-risposta**, dal portale di Machine Learning, in questo caso le variabili. Di seguito le immagini mostrano in cui si avrebbe richiesto la chiave e l'endpoint da. 
    >  
    > ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: L'esperimento](images/AzureLabs-Lab7-53-2.png)

8.  Inserire il codice all'interno di **Start ()** (metodo). Il **Start ()** metodo viene chiamato quando inizializza la classe:

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  Di seguito è riportato il metodo che raccoglie la data e ora da Windows e lo converte in un formato che l'esperimento di Machine Learning è possibile usare per confrontare i dati archiviati nella tabella.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. È possibile **eliminare** le **Update ()** metodo poiché questa classe non verrà utilizzate.

11. Aggiungere il metodo seguente che consente di comunicare la data e ora correnti per l'endpoint di Machine Learning e di ricevere una risposta in formato JSON.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. Aggiungere il metodo seguente, che è responsabile della deserializzazione della risposta JSON e comunica il risultato della deserializzazione per il **ShelfKeeper** classe. Questo risultato sarà i nomi dei tre elementi stimati per la vendita al meglio alla data e ora correnti. Inserire il codice seguente nel **ProductPrediction** (classe), sotto il metodo precedente.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. Salvare **Visual Studio** e tornare alla **Unity**.

14. Trascinare il **ProductPrediction** classe script dalle **Script** cartella, nel **Main Camera** oggetto.

15. Salvare il progetto e la scena **File** > **salvare/File della scena** > **Salva progetto**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capitolo 10 - compilare la soluzione di piattaforma UWP

È ora possibile compilare il progetto come soluzione di piattaforma UWP, in modo che possa essere eseguita come applicazione autonoma.

Per compilare:

1.  Salvare nella scena corrente facendo clic su **File** > **salvare scene**.

2.  Passare a **File** > **le impostazioni di compilazione**

3.  Selezionare la casella denominata **Unity C# progetti** (questo è importante poiché ciò permette di modificare le classi dopo la compilazione è stata completata).

4.  Fare clic su **aggiungere scene Open**,

5.  Fai clic su **Compila**.

    ![Compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab7-54.png)

6.  Viene chiesto di selezionare la cartella in cui si desidera compilare la soluzione.

7.  Creare un **COMPILAZIONI** cartella e all'interno della cartella creare un'altra cartella con un nome appropriato di propria scelta.

8.  Fare clic sulla nuova cartella e quindi fare clic su **selezionare la cartella**da cui avviare la compilazione nel percorso specificato.

    ![Compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab7-55.png)

    ![Compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab7-56.png)

9.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).

## <a name="chapter-11---deploy-your-application"></a>Capitolo 11 - distribuire l'applicazione

Per distribuire l'applicazione:

1.  Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.

2.  Con Visual Studio aperto, è necessario ripristinare i pacchetti NuGet, che può essere eseguita tramite il pulsante destro del soluzione MachineLearningLab_Build, da Esplora soluzioni (disponibili a destra di Visual Studio) e quindi facendo clic su Ripristina pacchetti NuGet:

    ![Aggiungere i pacchetti NuGet](images/AzureLabs-Lab7-57.png)

3.  Selezione configurazione di soluzione **Debug**.

4.  La piattaforma della soluzione, selezionare **x86**, **computer locale**. 

    > Per il Microsoft HoloLens, può risultare più semplice impostare questa opzione su *computer remoto*, in modo che non Windows con tethering al computer in uso. Tuttavia, è necessario inoltre eseguire le operazioni seguenti:
    > - Conoscere il **indirizzo IP** di HoloLens, il che può trovarsi all'interno di *Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo è consigliabile usare. 
    > - Assicurarsi **modalità sviluppatore** viene **sul**; è stata trovata nel *Impostazioni > aggiornamento e sicurezza > per gli sviluppatori*.

    ![Aggiungere i pacchetti NuGet](images/AzureLabs-Lab7-58.png)

5.  Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione al computer.

6.  L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.

Quando si esegue l'applicazione di realtà mista, si noterà banco di cui è stata configurata nella scena Unity e dall'inizializzazione, verranno recuperati i dati impostati all'interno di Azure. Verranno deserializzati i dati all'interno dell'applicazione e verranno forniti in modo visivo, come i tre modelli sul banco di tre risultati principali per la data e ora correnti.


## <a name="your-finished-machine-learning-application"></a>L'applicazione di Machine Learning completata
 
Complimenti, è stata compilata un'app per realtà mista che si basa su Azure Machine Learning per eseguire stime dei dati e visualizzarlo nella scena.

![Aggiungere i pacchetti NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Esercizio

**Esercizio 1**

Sperimentare l'ordinamento dell'applicazione e visualizzare le stime di tre in basso sullo scaffale, come i dati potenzialmente sarebbe utili anche.

**Esercizio 2**

Usando **tabelle di Azure** popolare una nuova tabella con informazioni meteorologiche e creare un nuovo esperimento usando i dati.
