---
title: MR e Azure 307-Machine Learning
description: Completare questo corso per apprendere come implementare Azure Machine Learning Studio all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, Machine Learning, ml, Machine Learning Studio, hololens, immersive, VR
ms.openlocfilehash: e302e287049cd746a436904c2af2bcc2b0835796
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926613"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR e Azure 307: Machine Learning

![prodotto finale-inizio](images/AzureLabs-Lab7-0.png)

In questo corso si apprenderà come aggiungere le funzionalità di Machine Learning (ML) a un'applicazione di realtà mista usando Azure Machine Learning Studio.

*Azure Machine Learning Studio* è un servizio Microsoft, che fornisce agli sviluppatori un numero elevato di algoritmi di Machine Learning, che possono essere utili per l'input, l'output, la preparazione e la visualizzazione dei dati. Da questi componenti è quindi possibile sviluppare un esperimento di analisi predittiva, eseguirne l'iterazione e usarlo per il training del modello. Seguendo il training, è possibile rendere operativo il modello all'interno del cloud di Azure, in modo da poter assegnare un punteggio ai nuovi dati. Per ulteriori informazioni, visitare la [pagina Azure Machine Learning Studio](https://azure.microsoft.com/services/machine-learning-studio/).

Dopo aver completato questo corso, si disporrà di un'applicazione con cuffie immersive di realtà mista e si avrà appreso come eseguire le operazioni seguenti:

1.  Fornire una tabella di dati di vendita al portale di *Azure Machine Learning Studio* e progettare un algoritmo per stimare le vendite future degli elementi più diffusi.
2.  Creare un **progetto Unity**, che può ricevere e interpretare i dati di stima dal servizio ml.
3.  Visualizza i dati di predicazione nel **progetto Unity**, fornendo gli elementi di vendita più diffusi, in uno scaffale.

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.

Questo corso è un'esercitazione autonoma, che non implica direttamente altri laboratori di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 307: Machine Learning</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018). È possibile utilizzare il software più recente, come indicato nell' [articolo installare gli strumenti](install-the-tools.md), ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](install-the-tools.md#installation-checklist)
- [Windows 10 SDK più recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata
- Accesso a Internet per l'installazione di Azure e il recupero dei dati ML

## <a name="before-you-start"></a>Prima di iniziare

Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capitolo 1-configurazione dell'account di archiviazione di Azure

Per usare l'API di Azure translator, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.
1.  Accedere al portale di [Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **account di archiviazione** nel menu a sinistra.

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

3.  Nella scheda **account di archiviazione** fare clic su **Aggiungi**.

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab7-2.png)

4.  Nel pannello **Crea account di archiviazione** :

    1.  Inserire un **nome** per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.
    2.  Per **modello di distribuzione** selezionare **Resource Manager**.
    3.  Per **tipo di account**selezionare **archiviazione (utilizzo generico V1)** .
    4.  Per **prestazioni**, selezionare **standard**.
    5.  Per la **replica** selezionare **l'archiviazione con ridondanza geografica e accesso in lettura (RA-GRS)** .
    6.  Lasciare il **trasferimento sicuro necessario** come **disabilitato**.
    7.  Selezionare una **sottoscrizione**.
    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
    
    5.  Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

5.  Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab7-3.png)

6.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

7.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>Capitolo 2: il Azure Machine Learning Studio

Per usare la *Azure Machine Learning*, è necessario configurare un'istanza del servizio Machine Learning da rendere disponibile per l'applicazione.

1.  Nel portale di Azure fare clic su **nuovo** nell'angolo in alto a sinistra e cercare **Machine Learning Studio area di lavoro**, quindi premere **invio**.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  La nuova pagina fornirà una descrizione del servizio **Machine Learning Studio area di lavoro** . Nella parte inferiore sinistra del prompt, fare clic sul pulsante **Crea** per creare un'associazione con il servizio.

3.  Una volta fatto clic su **Crea**, verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli sul nuovo **servizio Machine Learning Studio**:

    1.  Inserire il **nome dell'area di lavoro** desiderato per questa istanza del servizio.

    2.  Selezionare una **sottoscrizione**.

    3. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune). 

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche. È necessario usare lo stesso gruppo di risorse usato per la creazione di archiviazione di Azure nel capitolo precedente.

    5.  Per la sezione **account di archiviazione** , fare clic su **Usa esistente**, quindi fare clic sul menu a discesa e fare clic sull' **account di archiviazione** creato nell'ultimo capitolo.

    6.  Selezionare il piano **tariffario dell'area di lavoro** appropriato dal menu a discesa.

    7.  Nella sezione **piano di servizio Web** fare clic su **Crea** **nuovo e** quindi inserire un nome per il campo nel campo di testo.

    8.  Nella sezione **piano tariffario del piano di servizio Web** selezionare il piano tariffario scelto. Un livello di test di sviluppo denominato **DEVTEST standard** dovrebbe essere disponibile gratuitamente.

    9.  Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.

    10. Fai clic su **Crea**.

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

5.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.

8.  Nella sezione **collegamenti aggiuntivi** della pagina visualizzata fare clic su **Avvia Machine Learning Studio**, che consente di indirizzare il browser al portale di **Machine Learning Studio** .

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  Usare il pulsante **Sign in (accedi** ) in alto a destra o al centro per accedere al Machine Learning Studio.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>Capitolo 3-la Machine Learning Studio: impostazione del set di dati

Uno dei modi in cui Machine Learning gli algoritmi è l'analisi dei dati esistenti e quindi il tentativo di stimare i risultati futuri in base al set di dati esistente. Ciò significa in genere che i dati più esistenti si presentano, migliore sarà l'algoritmo per la stima dei risultati futuri.

Viene fornita una tabella di esempio per questo corso, denominata ProductsTableCSV, che [può essere scaricata qui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> Il file zip precedente contiene sia **ProductsTableCSV** che **file unitypackage Tools**, che sarà necessario nel [capitolo 6](#chapter-6---importing-the-mlproducts-unity-package). Questo pacchetto viene fornito anche in questo capitolo, anche se separato dal file CSV.

Questo set di dati di esempio contiene un record degli oggetti più venduti ogni ora di ogni giorno dell'anno 2017.
        
![Il Machine Learning Studio: impostazione del set di dati](images/AzureLabs-Lab7-11.png)

Ad esempio, il giorno 1 di 2017, alle 13.00 (ora 13), l'elemento più venduto era Salt e Pepper.

Questa tabella di esempio contiene 9998 voci.

1.  Tornare al portale di **Machine Learning Studio** e aggiungere questa tabella come **set di dati** per ml. A tale scopo, fare clic sul pulsante **+ nuovo** nell'angolo in basso a sinistra della schermata.

    ![Il Machine Learning Studio: impostazione del set di dati](images/AzureLabs-Lab7-12.png)

2.  Viene rilevata una sezione dalla parte inferiore e all'interno del pannello di navigazione a sinistra. Fare clic su **set di dati**, quindi a destra di tale, **da file locale**.

    ![Il Machine Learning Studio: impostazione del set di dati](images/AzureLabs-Lab7-13.png)

3.  Caricare il nuovo **set di dati** attenendosi alla procedura seguente:

    1. Verrà visualizzata la finestra carica, in cui è possibile **esplorare** il disco rigido per il nuovo set di dati.

        ![Il Machine Learning Studio: impostazione del set di dati](images/AzureLabs-Lab7-14.png)

    2.  Una volta selezionato e nuovamente nella finestra di caricamento, lasciare la casella di controllo non selezionata.

    3.  Nel campo di testo seguente immettere **ProductsTableCSV. csv** come nome per il set di dati, ma dovrebbe essere aggiunto automaticamente.

    4.  Utilizzando il menu a discesa per **tipo**, selezionare **file CSV generico con un'intestazione (CSV)** .

    5.  Premere il segno di selezione nella parte inferiore destra della finestra di caricamento e il **set di dati** verrà caricato.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>Capitolo 4-il Machine Learning Studio: esperimento

Prima di poter compilare il sistema di Machine Learning, è necessario creare un esperimento per convalidare la teoria sui dati. Con i risultati, sarà possibile sapere se sono necessari più dati o se non esiste alcuna correlazione tra i dati e un possibile risultato.

Per iniziare a creare un esperimento:

1.  Fare di nuovo clic sul pulsante **+ nuovo** nella parte inferiore sinistra della pagina, quindi fare clic su **esperimento** > **esperimento vuoto**.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-15.png)

2.  Verrà visualizzata una nuova pagina con un esperimento vuoto:

3.  Dal pannello a sinistra espandere set di **impostazioni salvati** > **My Datasets** e trascinare **ProductsTableCSV** sull'area di disegno dell' **esperimento**.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-16.png)

4.  Nel pannello a sinistra espandere **Data Transformation** > **Sample e Split**. Trascinare quindi l'elemento **Split data** nell'area di **disegno dell'esperimento**. L'elemento Split data suddividerà il set di dati in due parti. Una parte che si userà per il training dell'algoritmo di machine learning. La seconda parte verrà utilizzata per valutare l'accuratezza dell'algoritmo generato.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-17.png)

5.  Nel pannello destro (mentre l'elemento Split data nell'area di disegno è selezionato) modificare la **frazione di righe nel primo set** di dati di output in **0,7**. I dati verranno suddivisi in due parti, la prima parte sarà pari al 70% dei dati e la seconda parte sarà il 30% rimanente. Per assicurarsi che i dati vengano suddivisi in modo casuale, verificare che la casella di controllo **suddivisione casuale** rimanga selezionata.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-18.png)

6.  Trascinare una connessione dalla base dell'elemento **ProductsTableCSV** nell'area di disegno all'inizio dell'elemento di dati divisi. In questo modo si connetteranno gli elementi e si invierà l'output del set di dati **ProductsTableCSV** (i dati) all'input dei dati suddivisi.  

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-19.png)

7.  Nel pannello **esperimenti** sul lato sinistro espandere **Machine Learning** > **Train**. Trascinare l'elemento **Train Model** nell'area di disegno dell'esperimento. L'area di disegno dovrebbe avere un aspetto analogo a quello riportato di seguito.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-20.png)

8.  Dalla parte ***inferiore sinistra*** dell'elemento **Split data** trascinare una connessione all' **angolo superiore destro** dell'elemento **Train Model** . La prima divisione del 70% dal set di dati verrà utilizzata dal modello Train per eseguire il training dell'algoritmo.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-21.png)

9.  Selezionare l'elemento **Train Model** nell'area di disegno e nel pannello **Proprietà** (sul lato destro della finestra del browser) fare clic sul pulsante **Launch Column Selector** .

10. Nella casella di testo digitare **Product** , quindi premere **invio**. il *prodotto* verrà impostato come colonna per eseguire il training delle stime. A questo punto, fare clic sul **segno** di selezione nell'angolo in basso a destra per chiudere la finestra di dialogo di selezione.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-22.png)

11. Si intende eseguire il training di un algoritmo di **regressione logistica multiclasse** per stimare il **prodotto** più venduto in base all'ora del giorno e alla data. Esula dall'ambito di questo documento per spiegare i dettagli dei diversi algoritmi forniti da Azure Machine Learning Studio, tuttavia, è possibile ottenere altre informazioni dal foglio informativo sugli [algoritmi di Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. Dal pannello degli elementi dell'esperimento a sinistra espandere **Machine Learning** > **inizializzare il modello** > **classificazione**e trascinare l'elemento **regressione logistica multiclasse** nell'area di disegno dell'esperimento.

13. Connettere l'output, dalla parte inferiore della **regressione logistica multiclasse**, all'input in alto a sinistra dell'elemento del **modello Train** .

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-23.png)

14. Nell'elenco degli elementi dell'esperimento nel pannello a sinistra espandere **Machine Learning** > **Score**e trascinare l'elemento **Score Model** nell'area di disegno.

15. Connettere l'output, dalla parte inferiore del **modello Train**, all'input superiore sinistro del **modello score**.

16. Connettere l'output inferiore destro da **Split data**all'input superiore destro dell'elemento **Score Model** .

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-24.png)

17. Nell'elenco degli elementi dell' **esperimento** nel pannello a sinistra espandere **Machine Learning** > **Evaluate**e trascinare l'elemento **Evaluate Model** nell'area di disegno.

18. Connettere l'output dal **modello di Punteggio** all'input superiore sinistro del **modello Evaluate**.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-25.png)

19. Il primo esperimento Machine Learning è stato creato. È ora possibile salvare ed eseguire l'esperimento. Nel menu nella parte inferiore della pagina fare clic sul pulsante Save ( **Salva** ) per salvare l'esperimento e quindi fare clic su **Run (Esegui** ) per avviare l'esperimento.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-26.png)

20. È possibile visualizzare lo **stato** dell'esperimento nella parte superiore destra dell'area di disegno. Attendere alcuni istanti per il completamento dell'esperimento.

    > Se si dispone di un set di dati di grandi dimensioni (reale), è probabile che l'esecuzione dell'esperimento possa richiedere alcune ore.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-27.png)

21. Fare clic con il pulsante destro del mouse sull'elemento **Evaluate Model** nell'area di disegno e dal menu di scelta rapida posizionare il mouse sui **Risultati della valutazione**, quindi selezionare **Visualize (Visualizza**).

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-28.png)

22. I risultati della valutazione verranno visualizzati mostrando i risultati stimati rispetto ai risultati effettivi. Viene utilizzato il 30% del set di dati originale, diviso in precedenza, per la valutazione del modello. È possibile osservare che i risultati non sono ottimali, idealmente il numero più alto in ogni riga è costituito dall'elemento evidenziato nelle colonne.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-29.png)

23. Chiudere i **risultati**.

24. Per usare il modello di Machine Learning appena sottoposto a training, è necessario esporlo come **servizio Web**. A tale scopo, fare clic sulla voce di menu **Configura servizio Web** nel menu nella parte inferiore della pagina e fare clic su **servizio Web predittivo**.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-30.png)

25. Viene creata una nuova scheda e il modello di training viene unito per creare il nuovo servizio Web. 

26. Nel menu nella parte inferiore della pagina fare clic su **Salva**, quindi su **Esegui**. Viene visualizzato lo stato aggiornato nell'angolo superiore destro dell'area di disegno dell'esperimento.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-31.png)

27. Al termine dell'esecuzione, verrà visualizzato un pulsante **Distribuisci servizio Web** nella parte inferiore della pagina. Si è pronti per distribuire il servizio Web. Fare clic su **Distribuisci servizio Web** (classico) nel menu nella parte inferiore della pagina.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-32.png)

    > Il browser potrebbe richiedere di consentire un popup, che dovrebbe essere **consentito**, ma potrebbe essere necessario premere di nuovo **Distribuisci servizio Web** , se la pagina Distribuisci non viene visualizzata. 

28. Una volta creato l'esperimento, si verrà reindirizzati a una pagina del **Dashboard** in cui verrà visualizzata la **chiave API** . Per il momento, copiarlo in un blocco note, sarà necessario nel codice molto presto. Dopo aver annotato la chiave API, fare clic sul pulsante **richiesta/risposta** nella sezione **endpoint predefinito** sotto la chiave.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Se si fa clic su test in questa pagina, sarà possibile immettere i dati di input e visualizzare l'output. Immettere il **giorno** e l' **ora**. Lasciare vuota la voce relativa al **prodotto** . Fare quindi clic sul pulsante **Confirm (conferma** ). L'output nella parte inferiore della pagina visualizzerà il codice JSON che rappresenta la probabilità che ogni prodotto sia la scelta.

29. Viene visualizzata una nuova pagina Web che mostra le istruzioni e alcuni esempi sulla struttura di richiesta richiesta dal Machine Learning Studio. Copiare l' **URI della richiesta** visualizzato in questa pagina nel blocco note.

    ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-34.png)

A questo punto è stato creato un sistema di Machine Learning che fornisce il prodotto più probabile da vendere in base ai dati di acquisto cronologici, correlati all'ora del giorno e al giorno dell'anno.

Per chiamare il servizio Web, è necessario l'URL per l'endpoint del servizio e una chiave API per il servizio. Fare clic sulla scheda **consume** nel menu in alto.

Nella pagina informazioni sul **consumo** vengono visualizzate le informazioni necessarie per chiamare il servizio Web dal codice. Eseguire una copia della **chiave primaria** e dell'URL di **richiesta-risposta** . Questi sono necessari nel capitolo successivo.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capitolo 5-configurazione del progetto Unity

Configurare e testare l'auricolare immersiva della realtà mista.

> [!NOTE]
>  **Non** sarà necessario alcun controller di movimento per questo corso. Per supportare la configurazione dell'auricolare immersiva, fare clic [qui](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Aprire **Unity** e creare un nuovo progetto Unity denominato **Mr\_MachineLearning.** Verificare che il tipo di progetto sia impostato su **3D**.

2.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **modifica** **Preferenze** > e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

3.  Passare quindi a **File** > **impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante ***Switch Platform*** .

4.  Assicurarsi inoltre che:

    1.  Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**.

        > Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.

    2.  Il **tipo di compilazione** è impostato su **D3D**.

    3.  **SDK** è impostato sull' **ultima versione installata**.

    4.  La **versione di Visual Studio** è impostata su **installazione più recente**.

    5.  **Compilazione ed esecuzione** è impostato su **computer locale**.

    6.  Non preoccuparti di configurare le **scene** in questo momento, perché verranno fornite in seguito.

    7.  Per il momento le impostazioni rimanenti devono essere lasciate come predefinite.

        ![Configurazione del progetto Unity](images/AzureLabs-Lab7-35.png)

5.  Nella finestra **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** . 

6. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **altre impostazioni** :

        1.  La **versione di runtime** di **Scripting** deve essere **sperimentale** (equivalente a .NET 4,6)

        2. Il **back-end di scripting** deve essere ***.NET***

        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![Configurazione del progetto Unity](images/AzureLabs-Lab7-36.png)

    2.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        - **InternetClient**

            ![Configurazione del progetto Unity](images/AzureLabs-Lab7-37.png)

    3.  Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![Configurazione del progetto Unity](images/AzureLabs-Lab7-38.png)

    

6.  Nelle **impostazioni di compilazione** i progetti *Unity C#*  non sono più disattivati; Selezionare la casella di controllo accanto a questo. 

7.  Chiudere la finestra impostazioni di compilazione.

8.  Salvare il progetto (**FILE > Salva progetto**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capitolo 6-importazione del pacchetto MLProducts Unity

Per questo corso, sarà necessario scaricare un pacchetto di asset Unity denominato [**Azure-Mr-307. file unitypackage Tools**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage). Questo pacchetto viene completato con una scena, con tutti gli oggetti in che vengono precompilati, in modo da potersi concentrare sul funzionamento. Viene fornito lo script **ShelfKeeper** , sebbene contenga solo le variabili pubbliche per lo scopo della struttura di configurazione della scena. Sarà necessario eseguire tutte le altre sezioni. 

Per importare il pacchetto:

1.  Con il dashboard Unity davanti all'utente, fare clic su **Asset** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto, pacchetto personalizzato**.

    ![Importazione del pacchetto MLProducts Unity](images/AzureLabs-Lab7-39.png)

2.  Usare il selettore file per selezionare il pacchetto **Azure-Mr-307. file unitypackage Tools** e fare clic su **Apri**.

3.  Verrà visualizzato un elenco di componenti per questo asset. Confermare l'importazione facendo clic su **Importa**.

    ![Importazione del pacchetto MLProducts Unity](images/AzureLabs-Lab7-40.png)

4.  Una volta completata l'importazione, si noterà che alcune nuove cartelle sono state visualizzate nel pannello del **progetto**Unity. Questi sono i modelli 3D e i rispettivi materiali che fanno parte della scena preimpostata che si utilizzerà. In questo corso verrà scritta la maggior parte del codice.

    ![Importazione del pacchetto MLProducts Unity](images/AzureLabs-Lab7-41.png)

5.  Nella cartella del **Pannello del progetto** fare clic sulla cartella **Scenes** e fare doppio clic sulla scena all'interno (denominata **MR_MachineLearningScene**). La scena si aprirà (vedere l'immagine seguente). Se i diamanti rossi sono mancanti, è sufficiente fare clic sul pulsante **gizmos (Gizmo** ) in alto a destra nel **Pannello del gioco**.

    ![Importazione del pacchetto MLProducts Unity](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capitolo 7-controllo delle dll in Unity

Per sfruttare l'uso delle librerie JSON (usate per la serializzazione e la deserializzazione), è stata implementata una DLL Newtonsoft con il pacchetto fornito. La libreria deve avere la configurazione corretta, sebbene valga la pena controllare (in particolare se si verificano problemi con il codice non funzionante). 

A tale scopo:

-  Fare clic con il pulsante destro del mouse sul file Newtonsoft all'interno della cartella plugins ed esaminare il **pannello Inspector**. Verificare che **qualsiasi piattaforma** sia selezionata. Passare alla **scheda UWP** e assicurarsi che il **processo non** sia stato selezionato.

    ![Importazione delle dll in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capitolo 8: creare la classe ShelfKeeper

La classe **ShelfKeeper** ospita metodi che controllano l'interfaccia utente e i prodotti generati nella scena.

Come parte del pacchetto importato, si riceverà questa classe, sebbene sia incompleta. A questo punto è necessario completare la classe:

1.  Fare doppio clic sullo script **ShelfKeeper** , all'interno della cartella **Scripts** , per aprirlo con **Visual Studio 2017**.

2.  Sostituire tutto il codice esistente nello script con il codice seguente, che imposta la data e l'ora e dispone di un metodo per visualizzare un prodotto.

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

3.  Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.

4.  Tornare all'editor di Unity per verificare che la classe **ShelfKeeper** sia simile alla seguente:

    ![Creazione della classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Se lo script non ha le destinazioni di riferimento (ad esempio *Data (rete di testo)* , trascinare semplicemente gli oggetti corrispondenti dal **Pannello gerarchia**nei campi di destinazione. Vedere di seguito per una spiegazione, se necessario:
    > 
    > 1.  Per aprire la matrice di **punti di spawn** nello script del componente **ShelfKeeper** , fare clic su di essa. Verrà visualizzata una sottosezione denominata **size**, che indica le dimensioni della matrice. Digitare **3** nella casella di testo accanto a **size** e premere **invio**. verranno creati tre slot sotto.
    > 2. All'interno della **gerarchia** espandere l'oggetto **visualizzazione dell'ora** (facendo clic con il pulsante sinistro del mouse sulla freccia accanto). Fare quindi clic sulla ***videocamera principale*** dalla **gerarchia**, in modo che il **controllo** visualizzi le informazioni.
    > 3. Selezionare la **fotocamera principale** nel **Pannello gerarchia**. Trascinare gli oggetti **Data** e **ora** dal **Pannello gerarchia** agli slot di testo **Data** e **ora** nel **controllo** della **fotocamera principale** del componente **ShelfKeeper** .
    > 4. Trascinare i **punti di spawn** dal **Pannello gerarchia** (sotto l'oggetto *scaffale* ) alle destinazioni di riferimento a **3** **elementi** sotto la matrice del **punto di spawn** , come illustrato nell'immagine.
    > 
    >     ![Creazione della classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capitolo 9: creare la classe ProductPrediction

La classe successiva che si intende creare è la classe **ProductPrediction** .

Questa classe è responsabile di:

-   Esecuzione di query sull'istanza del **servizio Machine Learning** , specificando la data e l'ora correnti.

-   Deserializzazione della risposta JSON in dati utilizzabili.

-   Interpretazione dei dati, recupero dei 3 prodotti consigliati.

-   Chiamare i metodi della classe **ShelfKeeper** per visualizzare i dati nella scena.

Per creare questa classe:

1.  Passare alla cartella **Scripts** nel **Pannello Project**.

2.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi **creare** >  **C# script**. Chiamare lo script **ProductPrediction**.

3.  Fare doppio clic sul nuovo script **ProductPrediction** per aprirlo con **Visual Studio 2017**.

4.  Se viene visualizzata la finestra di dialogo **rilevamento modifiche file** , fare clic su ***ricarica soluzione**.

5.  Aggiungere gli spazi dei nomi seguenti all'inizio della classe ProductPrediction:

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

6.  All'interno della classe **ProductPrediction** inserire i due oggetti seguenti che sono composti da un numero di classi annidate. Queste classi vengono usate per serializzare e deserializzare il codice JSON per il servizio Machine Learning.

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

7.  Aggiungere quindi le variabili seguenti sopra il codice precedente, in modo che il codice JSON correlato si trovi nella parte inferiore dello script, sotto tutto il codice e non in linea:

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
    > Assicurarsi di inserire la **chiave primaria** e l' **endpoint richiesta-risposta**dal portale di machine learning nelle variabili qui. Le immagini seguenti mostrano dove è stata eseguita la chiave e l'endpoint da. 
    >  
    > ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: esperimento](images/AzureLabs-Lab7-53-2.png)

8.  Inserire questo codice all'interno del metodo **Start ()** . Il metodo **Start ()** viene chiamato quando la classe inizializza:

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

9.  Di seguito è riportato il metodo che raccoglie la data e l'ora da Windows e la converte in un formato che l'esperimento Machine Learning può utilizzare per eseguire il confronto con i dati archiviati nella tabella.

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

10. È possibile **eliminare** il metodo **Update ()** perché non verrà utilizzato da questa classe.

11. Aggiungere il metodo seguente che comunicherà la data e l'ora correnti all'endpoint Machine Learning e riceverà una risposta in formato JSON.

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

            // Serialize the request
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

12. Aggiungere il metodo seguente, che è responsabile della deserializzazione della risposta JSON e della comunicazione del risultato della deserializzazione alla classe **ShelfKeeper** . Questo risultato sarà costituito dai nomi dei tre elementi stimati per la vendita del maggior numero alla data e all'ora correnti. Inserire il codice seguente nella classe **ProductPrediction** , al di sotto del metodo precedente.

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

13. Salva **Visual Studio** e torna a **Unity**.

14. Trascinare lo script della classe **ProductPrediction** dalla cartella **script** nell'oggetto della **fotocamera principale** .

15. Salvare la scena e il **file** di progetto > **Salva scena/file** > **Salva progetto**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capitolo 10: compilare la soluzione UWP

A questo punto è necessario compilare il progetto come soluzione UWP, in modo che possa essere eseguito come applicazione autonoma.

Per compilare:

1.  Salvare la scena corrente facendo clic su **File** > **Salva scene**.

2.  Vai a **File** > **impostazioni di compilazione**

3.  Selezionare la casella denominata **progetti C# Unity** (questo aspetto è importante perché consente di modificare le classi al termine della compilazione).

4.  Fare clic su **Aggiungi scene aperte**,

5.  Fai clic su **Compila**.

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-54.png)

6.  Verrà richiesto di selezionare la cartella in cui si vuole compilare la soluzione.

7.  Creare una cartella **compilazioni** e all'interno di tale cartella creare un'altra cartella con un nome appropriato.

8.  Fare clic sulla nuova cartella e quindi fare clic su **Seleziona cartella**per iniziare la compilazione in quel percorso.

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-55.png)

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-56.png)

9.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).

## <a name="chapter-11---deploy-your-application"></a>Capitolo 11-distribuire l'applicazione

Per distribuire l'applicazione:

1.  Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.

2.  Con Visual Studio aperto è necessario ripristinare i pacchetti NuGet. a tale scopo, è possibile fare clic con il pulsante destro del mouse sulla soluzione MachineLearningLab_Build, dall'Esplora soluzioni (disponibile a destra di Visual Studio) e quindi scegliere Ripristina pacchetti NuGet:

    ![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-57.png)

3.  Nella configurazione della soluzione selezionare **debug**.

4.  Nella piattaforma soluzione selezionare **x86**, **computer locale**. 

    > Per Microsoft HoloLens, può risultare più semplice impostare questa impostazione su *computer remoto*, in modo da non essere collegati al computer. Tuttavia, sarà necessario eseguire anche le operazioni seguenti:
    > - Conosce l' **indirizzo IP** del HoloLens, disponibile all'interno delle *impostazioni > rete & Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare. 
    > - Verificare che la **modalità sviluppatore** sia **attiva**; disponibile in *impostazioni > aggiorna & > di sicurezza per gli sviluppatori*.

    ![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-58.png)

5.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per SIDELOAD l'applicazione al PC.

6.  L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.

Quando si esegue l'applicazione di realtà mista, viene visualizzato il banco configurato nella scena Unity e, dall'inizializzazione, verranno recuperati i dati configurati in Azure. I dati verranno deserializzati all'interno dell'applicazione e i tre risultati principali per la data e l'ora correnti verranno forniti visivamente, come tre modelli sul banco.


## <a name="your-finished-machine-learning-application"></a>Applicazione Machine Learning completata
 
Congratulazioni, è stata creata un'app per realtà mista che sfrutta le Azure Machine Learning per eseguire stime dei dati e visualizzarle nella scena.

![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Esercizio

**Esercizio 1**

Provare a usare il tipo di ordinamento dell'applicazione e fare in modo che vengano visualizzate le tre stime in basso sullo scaffale, in quanto questi dati potrebbero essere utili anche.

**Esercizio 2**

Con le **tabelle di Azure** viene popolata una nuova tabella con le informazioni meteorologiche e viene creato un nuovo esperimento usando i dati.
