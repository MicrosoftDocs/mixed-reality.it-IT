---
title: MR e Azure 308-notifiche tra dispositivi
description: Completare questo corso per apprendere come implementare Hub di notifica di Azure, funzioni di Azure e archiviazione di Azure e tabelle in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, notifiche, funzioni, tabelle, hub di notifica, hololens, immersive, VR
ms.openlocfilehash: d65750f37815efecae85e7bff85318a234079af8
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438755"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR e Azure 308: notifiche tra dispositivi

![prodotto finale-inizio](images/AzureLabs-Lab8-00.png)

In questo corso verrà illustrato come aggiungere funzionalità di hub di notifica a un'applicazione di realtà mista usando hub di notifica di Azure, tabelle di Azure e funzioni di Azure.

**Hub di notifica di Azure** è un servizio Microsoft che consente agli sviluppatori di inviare notifiche push mirate e personalizzate a qualsiasi piattaforma, tutto alimentato all'interno del cloud. Ciò consente agli sviluppatori di comunicare con gli utenti finali o persino di comunicare tra le varie applicazioni, a seconda dello scenario. Per altre informazioni, visitare la [pagina](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)Hub di notifica di Azure.

**Funzioni di Azure** è un servizio Microsoft che consente agli sviluppatori di eseguire piccole porzioni di codice, "funzioni", in Azure. Questo consente di delegare il lavoro al cloud, anziché l'applicazione locale, che può avere molti vantaggi. **Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, node. js, Java e php. Per altre informazioni, visitare la [pagina](https://docs.microsoft.com/azure/azure-functions/functions-overview)funzioni di Azure.

**Tabelle di Azure** è un servizio cloud Microsoft che consente agli sviluppatori di archiviare dati non SQL strutturati nel cloud, rendendoli facilmente accessibili ovunque. Il servizio è caratterizzato da una progettazione non schema, che consente l'evoluzione delle tabelle in base alle esigenze e pertanto è molto flessibile. Per altre informazioni, visita la [pagina](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) delle tabelle di Azure

Dopo aver completato questo corso, si disporrà di un'applicazione per le cuffie immersive a realtà mista e di un'applicazione per PC desktop, che sarà in grado di eseguire le operazioni seguenti:

1. L'app desktop PC consentirà all'utente di spostare un oggetto nello spazio 2D (X e Y), usando il mouse.

2. Lo spostamento di oggetti all'interno dell'app PC verrà inviato al cloud usando JSON, che avrà il formato di una stringa, contenente un ID oggetto, un tipo e le informazioni di trasformazione (coordinate X e Y). 

3. L'app per la realtà mista, che ha una scena identica per l'app desktop, riceverà le notifiche relative allo spostamento degli oggetti, dal servizio Hub di notifica, che è stato appena aggiornato dall'app per PC desktop. 

4. Quando riceve una notifica, che conterrà l'ID oggetto, il tipo e le informazioni di trasformazione, l'app realtà mista applica le informazioni ricevute alla propria scena.

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso. Questo corso è un'esercitazione autonoma, che non implica direttamente altri laboratori di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 308: notifiche tra dispositivi</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018). È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](install-the-tools.md#installation-checklist)
- [Windows 10 SDK più recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata
- Accesso a Internet per il programma di installazione di Azure e per accedere a hub di notifica

## <a name="before-you-start"></a>Prima di iniziare

- Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
- È necessario essere il proprietario del portale per sviluppatori Microsoft e il portale di registrazione delle applicazioni. in caso contrario, non si sarà autorizzati ad accedere all'app nel [capitolo 2](#chapter-2---retrieve-your-new-apps-credentials).

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capitolo 1-creare un'applicazione nel portale per sviluppatori Microsoft

Per usare il servizio **Hub di notifica di Azure** , è necessario creare un'applicazione nel portale per sviluppatori Microsoft, in quanto l'applicazione deve essere registrata, in modo che possa inviare e ricevere notifiche.

1.  Accedere al portale per [sviluppatori Microsoft](https://developer.microsoft.com/dashboard).

    > Sarà necessario accedere al proprio account Microsoft.

2.  Dal dashboard fare clic su **Crea una nuova app**.

    ![Creare un'app](images/AzureLabs-Lab8-01.png)

3.  Verrà visualizzata una finestra popup in cui è necessario riservare un nome per la nuova app. Nella casella di testo inserire un nome appropriato. Se il nome scelto è disponibile, verrà visualizzato un segno di spunta a destra della casella di testo. Una volta inserito un nome disponibile, fare clic sul pulsante **riserva nome prodotto** nella parte inferiore sinistra della finestra popup.

    ![invertire un nome](images/AzureLabs-Lab8-02.png)

4.  Ora che l'app è stata creata, è possibile passare al capitolo successivo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capitolo 2: recuperare le nuove credenziali per le app

Accedere al portale di registrazione delle applicazioni, in cui sarà elencata la nuova app e recuperare le credenziali che verranno usate per configurare il **servizio Hub di notifica** nel **portale di Azure**.

1.  Passare al [portale di registrazione delle applicazioni](https://apps.dev.microsoft.com).

    ![portale di registrazione delle applicazioni](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Per accedere è necessario usare il proprio account Microsoft.  
    > **Deve** corrispondere all'account Microsoft usato nel [capitolo](#chapter-1---create-an-application-on-the-microsoft-developer-portal)precedente, con il portale per sviluppatori di Windows Store.

2.  L'app sarà presente nella sezione **applicazioni personali** . Una volta individuato, fare clic su di esso e verrà eseguita una nuova pagina con il nome dell'app e la **registrazione**.

    ![app appena registrata](images/AzureLabs-Lab8-04.png)

3.  Scorrere la pagina di registrazione per trovare la sezione dei **segreti dell'applicazione** e il **SID del pacchetto** per l'app. Copiare entrambi per l'uso con la configurazione del **servizio Hub di notifica di Azure** nel capitolo successivo.

    ![segreti dell'applicazione](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capitolo 3: configurare il portale di Azure: creare il servizio Hub di notifica

Con le credenziali delle app recuperate, sarà necessario accedere al portale di Azure, in cui si creerà un servizio Hub di notifica di Azure.

1.  Accedere al [portale di Azure](https://portal.azure.com).

    > [!NOTE] 
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare **Hub di notifica**e quindi premere ***invio***.

    ![ricerca di hub di notifica](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > La parola ***New*** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

3.  La nuova pagina fornirà una descrizione del servizio *Hub di notifica* . Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![creare un'istanza di hub di notifica](images/AzureLabs-Lab8-07.png)

4.  Una volta fatto clic su ***Crea***:

    1.  Inserire il nome desiderato per l'istanza del servizio.

    2.  Fornire uno **spazio dei nomi** che sarà possibile associare a questa app.

    3.  Selezionare una **località.**

    4.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal). 

    5.  Selezionare una **sottoscrizione**appropriata.

    6.  Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.

    7. Seleziona **Crea**.

        ![dettagli del servizio di riempimento](images/AzureLabs-Lab8-08.png)

5.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![notifica](images/AzureLabs-Lab8-09.png)

7.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio **Hub di notifica** .

    ![Vai alla risorsa](images/AzureLabs-Lab8-10.png)
    
8.  Dalla pagina Panoramica, a metà della pagina, fare clic su **Windows (WNS).** Il pannello a destra cambierà in modo da visualizzare due campi di testo, che richiedono il **SID del pacchetto** e la **chiave di sicurezza**, dall'App configurata in precedenza.

    ![servizio Hub appena creato](images/AzureLabs-Lab8-11.png)

9. Dopo aver copiato i dettagli nei campi corretti, fare clic su **Salva**e si riceverà una notifica quando l'hub di notifica è stato aggiornato correttamente.

    ![Copia dettagli sicurezza](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capitolo 4: configurare il portale di Azure: creare il servizio tabelle

Dopo aver creato l'istanza del servizio Hub di notifica, tornare al portale di Azure, in cui si creerà un servizio tabelle di Azure creando una risorsa di archiviazione.

1.  Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).

2.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare **account di archiviazione**e premere **invio**.

    > [!NOTE] 
    > La parola ***New*** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

3.  Selezionare **account di archiviazione: BLOB, file, tabella e coda** dall'elenco.

    ![Cerca account di archiviazione](images/AzureLabs-Lab8-13.png)

4.  La nuova pagina fornirà una descrizione del servizio dell' **account di archiviazione** . Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'istanza di questo servizio.

    ![Crea istanza di archiviazione](images/AzureLabs-Lab8-14.png)

5.  Una volta fatto clic su **Crea**, verrà visualizzato un pannello:

    1. Inserire il **nome** desiderato per l'istanza del servizio (deve essere in lettere minuscole).

    2. Per **modello di distribuzione**, fare clic su **Resource Manager**.

    3.  Per **tipo di account**, usando il menu a discesa selezionare **archiviazione (utilizzo generico V1)** .

    4. Selezionare un **percorso**appropriato.
    
    5.  Per il menu a discesa **replica** , selezionare **lettura-accesso-archiviazione con ridondanza geografica (RA-GRS)** .

    6.  Per **prestazioni**, fare clic su **standard**.

    7.  Nella sezione **trasferimento sicuro obbligatorio** selezionare **disabilitato**.

    8.  Dal menu a discesa **sottoscrizione** selezionare una sottoscrizione appropriata.

    9.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Lasciare le **reti virtuali** **disabilitate** se si tratta di un'opzione.

    11. Fai clic su **Crea**.

        ![specificare i dettagli di archiviazione](images/AzureLabs-Lab8-15.png)

6.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

7.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale. Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![nuova notifica di archiviazione](images/AzureLabs-Lab8-16.png)

8.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova pagina Panoramica dell'istanza del servizio di archiviazione.

    ![Vai alla risorsa](images/AzureLabs-Lab8-17.PNG)

9. Nella pagina Panoramica fare clic su **tabelle**sul lato destro.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. Il pannello a destra cambierà in modo da visualizzare le informazioni sul **servizio tabelle** , in cui è necessario aggiungere una nuova tabella. A tale scopo, fare clic sul pulsante **+** **tabella** nell'angolo superiore sinistro.

    ![Apri tabelle](images/AzureLabs-Lab8-19.png)

11. Verrà visualizzata una nuova pagina, in cui è necessario immettere un nome di **tabella**. Si tratta del nome che verrà usato per fare riferimento ai dati nell'applicazione nei capitoli successivi. Inserire un nome appropriato e fare clic su **OK**.

    ![Crea nuova tabella](images/AzureLabs-Lab8-20.png)    

12. Una volta creata la nuova tabella, sarà possibile visualizzarla nella pagina del **servizio tabelle** (nella parte inferiore).

    ![nuova tabella creata](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capitolo 5-completamento della tabella di Azure in Visual Studio

Ora che l'account di archiviazione del **servizio tabelle** è stato configurato, è possibile aggiungervi dati, che verranno usati per archiviare e recuperare le informazioni. La modifica delle tabelle può essere eseguita tramite **Visual Studio**.

1.  Aprire **Visual Studio**.

2.  Dal menu fare clic su **visualizza** > **Cloud Explorer**.

    ![Aprire Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  Il **Cloud Explorer** verrà aperto come elemento ancorato (essere paziente, perché il caricamento potrebbe richiedere tempo).

    > [!NOTE] 
    > Se la sottoscrizione usata per creare gli *account di archiviazione* non è visibile, assicurarsi di disporre di: 
    > - Si è connessi allo stesso account usato per il portale di Azure.
    > - È stata selezionata la sottoscrizione dalla pagina di gestione degli account. potrebbe essere necessario applicare un filtro dalle impostazioni dell'account:  
    >
    >   ![trova sottoscrizione](images/AzureLabs-Lab8-22-5.png)

4.  Verranno visualizzati i servizi cloud di Azure. Trovare gli **account di archiviazione** e fare clic sulla freccia a sinistra di per espandere gli account.

    ![aprire gli account di archiviazione](images/AzureLabs-Lab8-23.png)

5.  Una volta espansa, l' **account di archiviazione** appena creato dovrebbe essere disponibile. Fare clic sulla freccia a sinistra della risorsa di archiviazione, quindi, una volta espansa, trovare le **tabelle** e fare clic sulla freccia accanto a questa, per visualizzare la **tabella** creata nell'ultimo capitolo. Fare doppio clic sulla **tabella**.

    ![Apri tabella oggetti scena](images/AzureLabs-Lab8-24.png)

6.  La tabella verrà aperta al centro della finestra di Visual Studio. Fare clic sull'icona della tabella con il **+** (Plus).

    ![Aggiungi nuova tabella](images/AzureLabs-Lab8-25.png)

7.  Verrà visualizzata una finestra con la richiesta di *aggiungere un'entità*. Si creeranno tre entità in totale, ognuna con diverse proprietà. Si noterà che *PartitionKey* e *RowKey* sono già disponibili, perché vengono usati dalla tabella per trovare i dati. 

    ![chiave di partizione e di riga](images/AzureLabs-Lab8-26.png)

8. Aggiornare il *valore* di **PartitionKey** e **RowKey** come indicato di seguito. a tale scopo, è necessario eseguire questa operazione per ogni proprietà di riga aggiunta, ma incrementare ogni volta il RowKey:

    ![Aggiungi valori corretti](images/AzureLabs-Lab8-26-5.png)

9.  Fare clic su **Aggiungi proprietà** per aggiungere righe di dati aggiuntive. Fare in modo che la prima tabella vuota corrisponda alla tabella seguente.

10. Al termine, fare clic su **OK** .

    ![al termine, fare clic su OK](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Assicurarsi di aver modificato il **tipo** delle voci **X**, **Y**e **Z**in **Double**. 

11. Si noterà che la tabella dispone ora di una riga di dati. Fare di nuovo clic sull'icona **+** (più) per aggiungere un'altra entità.

    ![prima riga](images/AzureLabs-Lab8-27-5.png)

12. Creare una proprietà aggiuntiva, quindi impostare i valori della nuova entità in modo che corrispondano a quelli mostrati di seguito.

    ![Aggiungi cubo](images/AzureLabs-Lab8-28.png)

13. Ripetere l'ultimo passaggio per aggiungere un'altra entità. Impostare i valori per questa entità su quelli mostrati di seguito.

    ![Aggiungi cilindro](images/AzureLabs-Lab8-29.png)

14. La tabella dovrebbe essere simile a quella riportata di seguito.

    ![tabella completata](images/AzureLabs-Lab8-30.png)

15. Il capitolo è stato completato. Assicurarsi di salvare.

## <a name="chapter-6---create-an-azure-function-app"></a>Capitolo 6: creare un app per le funzioni di Azure

Creare una app per le funzioni di Azure, che verrà chiamata dall'applicazione desktop per aggiornare il servizio **tabelle** e inviare una notifica tramite l' **Hub di notifica**.

In primo luogo, è necessario creare un file che consentirà alla funzione di Azure di caricare le librerie necessarie.

1.  Aprire **blocco note** (premere il tasto Windows e digitare blocco note).

    ![Apri blocco note](images/AzureLabs-Lab8-31.png)

2.  Con blocco note aperto, inserire la struttura JSON riportata di seguito. Una volta completata questa operazione, salvarla sul desktop come **Project. JSON**. È importante che la denominazione sia corretta: assicurarsi che non sia **presente un'estensione di file txt** . Questo file definisce le librerie che la funzione userà, se è stato usato NuGet, avrà un aspetto familiare.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Accedere al portale di [Azure](https://portal.azure.com).

4.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare **app per le funzioni**, quindi premere **invio**.

    ![Cerca app per le funzioni](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

5.  La nuova pagina fornirà una descrizione del servizio **app per le funzioni** . Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![istanza dell'app per le funzioni](images/AzureLabs-Lab8-33.png)

6.  Una volta fatto clic su **Crea**, compilare quanto segue:

    1. Per **nome app**, inserire il nome desiderato per l'istanza del servizio.

    2. Selezionare una **sottoscrizione**.

    3. Selezionare il piano tariffario appropriato, se è la prima volta che si crea un **servizio app per le funzioni**, sarà disponibile un livello gratuito.

    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Per **sistema operativo**, fare clic su Windows, che corrisponde alla piattaforma desiderata.

    6. Selezionare un **piano di hosting** . questa esercitazione usa un **piano a consumo**.

    7. Selezionare un **percorso** **(scegliere la stessa posizione della risorsa di archiviazione compilata nel passaggio precedente)**

    8. Per la sezione **archiviazione** **è necessario selezionare il servizio di archiviazione creato nel passaggio precedente**.

    9. Non sarà necessario *Application Insights* in questa app, quindi è possibile lasciarla **disattivata**.

    10. Fai clic su **Crea**.

        ![Crea nuova istanza](images/AzureLabs-Lab8-34.png)

7.  Una volta fatto clic su **Crea** , è necessario attendere che il servizio venga creato. l'operazione potrebbe richiedere un minuto.

8.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![nuova notifica](images/AzureLabs-Lab8-35.png)

9.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

10. Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. 

    ![Vai alla risorsa](images/AzureLabs-Lab8-36.png)

11. Fare clic sull'icona **+** (Plus) accanto a *funzioni*per *crearne una nuova*.

    ![Aggiungi nuova funzione](images/AzureLabs-Lab8-37.png)

12. All'interno del pannello centrale verrà visualizzata la finestra di creazione della **funzione** . Ignorare le informazioni nella metà superiore del pannello e fare clic su **funzione personalizzata**, posizionata nella parte inferiore dell'area blu, come indicato di seguito.

    ![funzione personalizzata](images/AzureLabs-Lab8-38.png)

13. La nuova pagina all'interno della finestra mostrerà vari tipi di funzione. Scorrere verso il basso per visualizzare i tipi viola, quindi fare clic su elemento **http put** .

    ![collegamento http put](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Potrebbe essere necessario scorrere verso il basso la pagina (e questa immagine potrebbe non essere esattamente identica, se si sono verificati aggiornamenti del portale di Azure), tuttavia, si cerca un elemento denominato *http put*.

14. Verrà visualizzata la finestra **PUT http** in cui è necessario configurare la funzione (vedere di seguito per l'immagine).

    1.  Per **lingua,** scegliere C\#dal menu a discesa.

    2.  Per **nome** immettere un nome appropriato.

    3.  Nel menu a discesa **livello di autenticazione** selezionare **funzione**.

    4.  Per la sezione **nome tabella** è necessario usare il nome esatto usato per creare il servizio **tabelle** in precedenza (incluso lo stesso caso della lettera).

    5.  Nella sezione **connessione dell'account di archiviazione** usare il menu a discesa e selezionare l'account di archiviazione da qui. In caso contrario, fare clic sul collegamento ipertestuale **nuovo** accanto al titolo della sezione per visualizzare un altro pannello in cui è necessario elencare l'account di archiviazione.

        ![nuova risorsa di archiviazione](images/AzureLabs-Lab8-40.png)

15. Fare clic su **Crea** . si riceverà una notifica che segnala che le impostazioni sono state aggiornate correttamente.

    ![Create (funzione)](images/AzureLabs-Lab8-41.png)

16. Dopo aver fatto clic su **Crea**, si verrà reindirizzati all'editor di funzioni.

    ![aggiornare il codice della funzione](images/AzureLabs-Lab8-42.png)

17. Inserire il codice seguente nell'editor di funzioni (sostituendo il codice nella funzione):

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > Usando le librerie incluse, la funzione riceve il nome e il percorso dell'oggetto che è stato spostato nella scena Unity (come C# oggetto, denominato **UnityGameObject**). Questo oggetto viene quindi utilizzato per aggiornare i parametri dell'oggetto all'interno della tabella creata. In seguito, la funzione effettua una chiamata al servizio Hub di notifica creato, che notifica tutte le applicazioni sottoscritte.

18. Con il codice sul posto, fare clic su **Salva**.

19. Fare quindi clic sull'icona **\<** (freccia), sul lato destro della pagina.

    ![Apri il pannello di caricamento](images/AzureLabs-Lab8-43.png)

20. Un pannello scorrerà verso destra. In tale pannello fare clic su **carica**e verrà visualizzato un browser file.

21. Passare a e fare clic sul file **Project. JSON** , creato in precedenza nel **blocco note** , quindi fare clic sul pulsante **Apri** . Questo file definisce le librerie che la funzione utilizzerà.

    ![carica JSON](images/AzureLabs-Lab8-44.png)

22. Quando il file è stato caricato, verrà visualizzato nel pannello a destra. Facendo clic su di esso verrà aperto nell'editor di **funzioni** . Deve essere **esattamente** uguale all'immagine successiva (al passaggio 23).

23. Quindi, nel pannello a sinistra, sotto **funzioni**, fare clic sul collegamento **integra** .

    ![integra funzione](images/AzureLabs-Lab8-45.png)

24. Nella pagina successiva, nell'angolo in alto a destra, fare clic su **Editor avanzato** (come indicato di seguito).

    ![editor avanzato aperto](images/AzureLabs-Lab8-46.png)

25. Un file **Function. JSON** verrà aperto nel pannello centrale, che deve essere sostituito con il frammento di codice seguente. Definisce la funzione che si sta compilando e i parametri passati alla funzione.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. L'editor dovrebbe ora apparire come l'immagine seguente:

    ![Torna all'editor standard](images/AzureLabs-Lab8-47.png)

27. È possibile notare che i parametri di input appena inseriti potrebbero non corrispondere ai dettagli della tabella e dell'archiviazione e pertanto dovranno essere aggiornati con le informazioni. **Questa operazione non**viene eseguita in questo argomento, come illustrato di seguito. È sufficiente fare clic sul collegamento dell' **editor standard** , nell'angolo in alto a destra della pagina, per tornare indietro.

28. Tornare all' **editor standard**, fare clic su **archiviazione tabelle di Azure (tabella)** in **input**. 
    
    ![Input tabella](images/AzureLabs-Lab8-47-5.png)

29. Assicurarsi che le informazioni seguenti corrispondano alle informazioni **, in quanto** potrebbero essere diverse (esiste un'immagine sotto la seguente procedura):

    1.  **Nome tabella**: il nome della tabella creata nel servizio tabelle di archiviazione di Azure.

    2.  **Connessione dell'account di archiviazione:** fare clic su **nuovo**, che viene visualizzato accanto al menu a discesa e un pannello verrà visualizzato a destra della finestra.

        ![nuova risorsa di archiviazione](images/AzureLabs-Lab8-48.png)

        1.  Selezionare l' **account di archiviazione**creato in precedenza per ospitare le app per le **funzioni.**

        2. Si noterà che il valore di connessione dell' **account di archiviazione** è stato creato.

        3. Assicurarsi di premere **Salva** al termine dell'operazione.

    3.  La pagina **input** dovrebbe ora corrispondere a quanto riportato di seguito, mostrando **le** informazioni.

        ![input completati](images/AzureLabs-Lab8-49.png)

30. Fare quindi clic su **Hub di notifica di Azure (notifica)** , in **output**. Verificare che le informazioni riportate di seguito corrispondano a quelle dell' **utente** , in quanto potrebbero essere diverse (esiste un'immagine sotto la seguente procedura):

    1.  **Nome Hub di notifica**: è il nome dell'istanza del servizio **Hub di notifica** creata in precedenza.

    2.  **Connessione spazio dei nomi di hub di notifica**: fare clic su **nuovo**, che viene visualizzato accanto al menu a discesa.

        ![Controlla output](images/AzureLabs-Lab8-50.png)

    3. Verrà visualizzato il popup della **connessione** (vedere l'immagine seguente), in cui è necessario selezionare lo **spazio dei nomi** dell' **Hub di notifica**, configurato in precedenza.

    4. Nel menu a discesa centrale selezionare il nome dell' **Hub di notifica** .

    5.  Impostare il menu a discesa **criterio** su **DefaultFullSharedAccessSignature**.

    6. Fare clic sul pulsante **Seleziona** per tornare indietro.

        ![aggiornamento dell'output](images/AzureLabs-Lab8-51.png)

31.  La pagina degli **output** dovrebbe ora corrispondere a quanto segue, ma con **le** informazioni. Assicurarsi di premere **Salva**.

> [!WARNING]
> Non *modificare direttamente il nome dell'hub di notifica* . questa operazione dovrebbe essere eseguita con il **Editor avanzato**, purché siano stati eseguiti correttamente i passaggi precedenti.

![output completati](images/AzureLabs-Lab8-50.png)

32. A questo punto, è necessario testare la funzione per verificare che funzioni. A tale scopo, effettua le seguenti operazioni: 

    1. Passare alla pagina della funzione ancora una volta:

        ![output completati](images/AzureLabs-Lab8-50-1.png)

    2. Tornare alla pagina funzione, fare clic sulla scheda **test** al lato destro della pagina per aprire il pannello *test* :

        ![output completati](images/AzureLabs-Lab8-50-2.png)

    3. Nella casella di testo **corpo della richiesta** del pannello incollare il codice seguente:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Con il codice di test, fare clic sul pulsante **Run (Esegui** ) in basso a destra e il test verrà eseguito. I log di output del test verranno visualizzati nell'area della console, sotto il codice della funzione.

        ![output completati](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Se il test precedente non riesce, è necessario verificare di aver seguito esattamente i passaggi precedenti, in particolare le impostazioni nel **Pannello integra**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capitolo 7: configurare il progetto di Unity desktop

> [!IMPORTANT]
> L'applicazione desktop attualmente creata **non** funzionerà nell'editor di Unity. Deve essere eseguito all'esterno dell'editor, dopo la compilazione dell'applicazione, usando Visual Studio (o l'applicazione distribuita). 

Di seguito è riportata una configurazione tipica per lo sviluppo con Unity e realtà mista e, di conseguenza, un modello valido per altri progetti.

Configurare e testare l'auricolare immersiva della realtà mista.

> [!NOTE] 
> **Non** sarà necessario alcun controller di movimento per questo corso. Se è necessario supportare la configurazione dell'auricolare immersivo, seguire questo [collegamento per configurare la realtà mista di Windows](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Aprire **Unity** e fare clic su **New**.

    ![nuovo progetto Unity](images/AzureLabs-Lab8-52.png)

2.  È necessario specificare un nome di progetto Unity, inserire **UnityDesktopNotifHub**. Verificare che il tipo di progetto sia impostato su **3D**. Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![Crea progetto](images/AzureLabs-Lab8-53.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **modifica** **Preferenze** > e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![imposta strumenti esterni di Visual Studio](images/AzureLabs-Lab8-54.png)

4.  Passare quindi a **File** > **impostazioni di compilazione** e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.

    ![piattaforme switch](images/AzureLabs-Lab8-55.png)

5.  Sempre in **File** > **impostazioni di compilazione**, verificare che:

    1.  Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**

        > Questa applicazione sarà per il desktop, quindi deve essere **qualsiasi dispositivo**

    2.  Il **tipo di compilazione** è impostato su **D3D**

    3.  **SDK** è impostato sull' **ultima versione installata**

    4.  La **versione di Visual Studio** è impostata su **installazione più recente**

    5.  **Compilazione ed esecuzione** è impostato su **computer locale**

    6.  Sebbene qui valga la pena salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.

            ![Aggiungi scene aperte](images/AzureLabs-Lab8-56.png)

        2. Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.

            ![nuova cartella scenes](images/AzureLabs-Lab8-57.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo **nome file:** testo digitare **NH\_desktop\_scena**, quindi fare clic su **Salva**.

            ![nuovo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.

6.  Nella stessa finestra fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .

7.  In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **altre impostazioni** :

        1.  La **versione di runtime di scripting** deve essere **sperimentale (equivalente a .NET 4,6)**

        2. Il **back-end di scripting** deve essere **.NET**

        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![4,6 versione NET](images/AzureLabs-Lab8-59.png)

    2.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        - **InternetClient**

            ![Seleziona client Internet](images/AzureLabs-Lab8-60.png)

8.  Nelle **impostazioni di compilazione** i *progetti di unity C\#* non sono più in grigio; Selezionare la casella di controllo accanto a questo.

9.  Chiudere la finestra **impostazioni di compilazione** .

10. Salvare la scena e il **file** di progetto > **Salva scena/file** > **Salva progetto**.

    > [!IMPORTANT]
    > Se si vuole ignorare il componente di *configurazione Unity* per questo progetto (app desktop) e continuare direttamente con il codice, è possibile [scaricare questo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  Sarà comunque necessario aggiungere i componenti di script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capitolo 8-importazione delle dll in Unity

Si utilizzerà archiviazione di Azure per Unity (che a sua volta USA .NET SDK per Azure). Per altre informazioni, seguire questo [collegamento su archiviazione di Azure per Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare l'SDK nel progetto, assicurarsi di aver scaricato la versione più recente di [**file unitypackage Tools**](https://aka.ms/azstorage-unitysdk) da GitHub. Eseguire quindi le operazioni seguenti:

1.  Aggiungere il **file unitypackage Tools** a Unity usando l'opzione di menu **Asset \> importa pacchetto \> pacchetto personalizzato** .

2.  Nella casella **Importa pacchetto Unity** visualizzata è possibile selezionare tutti gli elementi sotto * **plugin* \> * storage * * *.  Deselezionare tutti gli altri elementi, perché non sono necessari per questo corso.

    ![Importa nel pacchetto](images/AzureLabs-Lab8-61.png)

3.  Fare clic sul pulsante ***Importa*** per aggiungere gli elementi al progetto.

4.  Passare alla cartella **archiviazione** in **plug** -in nella visualizzazione del progetto e selezionare *solo*i plug-in seguenti:

    -   Microsoft. Data. Edm
    -   Microsoft. Data. OData
    -   Microsoft. WindowsAzure. storage
    -   Newtonsoft. JSON
    -   System. Spatial

![deseleziona qualsiasi piattaforma](images/AzureLabs-Lab8-62.png)

5.  Con *questi plug* -in specifici selezionati, **deselezionare** **qualsiasi piattaforma** e **deselezionare** **WSAPlayer** , quindi fare clic su **applica**.

    ![applica dll della piattaforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Questi specifici plug-in vengono contrassegnati per essere usati solo nell'editor di Unity. Questo è dovuto al fatto che esistono versioni diverse degli stessi plug-in nella cartella WSA che verranno usate dopo l'esportazione del progetto da Unity.

6.  Nella cartella plugin di **archiviazione** selezionare solo:

    -   Microsoft. Data. Services. client

        ![impostazione non elabora per le dll](images/AzureLabs-Lab8-64.png)

7.  Selezionare la casella **non elaborare** in **Impostazioni piattaforma** e fare clic su ***applica***.

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Si sta contrassegnando questo plug-in "non elaborare", perché il plug-in assembly Unity ha difficoltà nell'elaborare questo plug-in. Il plug-in continuerà a funzionare anche se non viene elaborato.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capitolo 9: creare la classe TableToScene nel progetto di Unity desktop

È ora necessario creare gli script contenenti il codice per eseguire questa applicazione.

Il primo script che è necessario creare è **TableToScene**, responsabile di:

-   Lettura di entità all'interno della tabella di Azure.
-   Utilizzando i dati della tabella, determinare gli oggetti da generare e in quale posizione.

Il secondo script che è necessario creare è **CloudScene**, responsabile di:

-   Registrazione dell'evento di clic per consentire all'utente di trascinare gli oggetti intorno alla scena.
-   Serializzare i dati dell'oggetto da questa scena Unity e inviarli al app per le funzioni di Azure.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella **Asset** che si trova nel pannello del progetto, quindi **creare** > **cartella**. Denominare gli **script**della cartella.

    ![Crea cartella script](images/AzureLabs-Lab8-66.png)

    ![Creazione cartella script 2](images/AzureLabs-Lab8-67.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla.

3.  Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **Crea** >  **C# script**. Denominare lo script **TableToScene**.

    ![nuovo script c#](images/AzureLabs-Lab8-68.png)
    ![ridenominazione TableToScene](images/AzureLabs-Lab8-69.png)

4.  Fare doppio clic sullo script per aprirlo in Visual Studio 2017.

5.  Aggiungere gli spazi dei nomi seguenti:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  All'interno della classe, inserire le variabili seguenti:

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Sostituire il valore **AccountName** con il nome del servizio di archiviazione di Azure e il valore **AccountKey** con il valore di chiave trovato nel servizio di archiviazione di Azure, nel portale di Azure (vedere l'immagine seguente). 
    >
    > ![Recupera chiave dell'account](images/AzureLabs-Lab8-70.png)

7.  A questo punto aggiungere i metodi **Start ()** e **svegli ()** per inizializzare la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  All'interno della classe **TableToScene** aggiungere il metodo che recupererà i valori dalla tabella di Azure e li userà per generare le primitive appropriate nella scena.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  Al di fuori della classe **TableToScene** , è necessario definire la classe usata dall'applicazione per serializzare e deserializzare le **entità di tabella**.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Assicurarsi di **salvare** prima di tornare all'editor di Unity.

11. Fare clic sulla **fotocamera principale** nel pannello **gerarchia** , in modo che le relative proprietà vengano visualizzate nel **controllo**.

12. Con la cartella degli **script** aperta, selezionare il **file TableToScene** dello script e trascinarlo sulla **fotocamera principale**. Il risultato dovrebbe essere il seguente:

    ![aggiungere lo script alla fotocamera principale](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capitolo 10: creare la classe CloudScene nel progetto di Unity desktop

Il secondo script che è necessario creare è **CloudScene**, responsabile di:

-   Registrazione dell'evento di clic per consentire all'utente di trascinare gli oggetti intorno alla scena.

-   Serializzare i dati dell'oggetto da questa scena Unity e inviarli al app per le funzioni di Azure.

Per creare il secondo script:

1.  Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **crea**, **C\# script**. Denominare lo script **CloudScene**
    
    ![nuovo script c#](images/AzureLabs-Lab8-72.png)
    ![rinominare CloudScene](images/AzureLabs-Lab8-73.png)

2.  Aggiungere gli spazi dei nomi seguenti:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Inserire le variabili seguenti:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Sostituire il valore di **azureFunctionEndpoint** con l'URL del app per le funzioni di Azure trovato nel servizio app per le funzioni di Azure, nel portale di Azure, come illustrato nell'immagine seguente:

    ![ottenere l'URL della funzione](images/AzureLabs-Lab8-74.png)

5.  A questo punto aggiungere i metodi **Start ()** e **svegli ()** per inizializzare la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  All'interno del metodo **Update ()** aggiungere il codice seguente che rileverà l'input e il trascinamento del mouse, che a sua volta sposta GameObject nella scena. Se l'utente ha trascinato e rilasciato un oggetto, passerà il nome e le coordinate dell'oggetto al metodo **UpdateCloudScene ()** , che chiamerà il servizio app per le funzioni di Azure, che aggiornerà la tabella di Azure e attiverà la notifica.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  A questo punto aggiungere il metodo **UpdateCloudScene ()** , come indicato di seguito:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Salvare il codice e tornare a Unity

9.  Trascinare lo script **CloudScene** sulla **fotocamera principale**. 

    1. Fare clic sulla **fotocamera principale** nel pannello **gerarchia** , in modo che le relative proprietà vengano visualizzate nel **controllo**. 

    2. Con la cartella degli **script** aperta, selezionare lo script **CloudScene** e trascinarlo sulla **fotocamera principale**. Il risultato dovrebbe essere il seguente:

        > ![Trascinare lo script cloud sulla fotocamera principale](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Capitolo 11: compilare il progetto desktop in UWP

Tutti gli elementi necessari per la sezione Unity di questo progetto sono ora completati.

1.  Passare a **impostazioni di compilazione** (**file** > **impostazioni di compilazione**).

2.  Nella finestra **impostazioni di compilazione** fare clic su **Compila**.

    ![Compila progetto](images/AzureLabs-Lab8-76.png)

3.  Verrà visualizzata una finestra **Esplora file** con la richiesta di un percorso da compilare. Creare una nuova cartella (facendo clic su **nuova cartella** nell'angolo superiore sinistro) e denominarla **compilata**.

    ![nuova cartella per la compilazione](images/AzureLabs-Lab8-77.png)

    1.  Aprire la nuova cartella **compilazioni** e creare un'altra cartella (usando una **nuova cartella** ancora una volta) e denominarla **NH\_desktop\_app**.

        ![nome cartella NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Con l' **App\_Desktop\_di NH** selezionata. fare clic su **Seleziona cartella**. La compilazione del progetto verrà eseguita per un minuto.

4.  Nella compilazione seguente verrà visualizzato **Esplora file** che indica il percorso del nuovo progetto. Tuttavia, non è necessario aprirlo, perché è necessario creare prima l'altro progetto Unity nei prossimi capitoli.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capitolo 12: configurare un progetto Unity per la realtà mista

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire **Unity** e fare clic su **New**.

    ![nuovo progetto Unity](images/AzureLabs-Lab8-79.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity, inserire **UnityMRNotifHub**. Verificare che il tipo di progetto sia impostato su **3D**. Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **modifica** **Preferenze** > e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![imposta editor esterno su Visual Studio](images/AzureLabs-Lab8-81.png)

4.  Passare quindi a **File** > **impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .

    ![passare da una piattaforma all'altra a UWP](images/AzureLabs-Lab8-82.png)

5.  Passare a **File** > **impostazioni di compilazione** e verificare che:

    1.  Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**

        > Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.

    2.  Il **tipo di compilazione** è impostato su **D3D**

    3.  **SDK** è impostato sull' **ultima versione installata**

    4.  La **versione di Visual Studio** è impostata su **installazione più recente**

    5.  **Compilazione ed esecuzione** è impostato su **computer locale**

    6.  Sebbene qui valga la pena salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.

            ![Aggiungi scene aperte](images/AzureLabs-Lab8-83.png)

        2. Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.

            ![nuova cartella scenes](images/AzureLabs-Lab8-84.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo **nome file:** testo digitare **NH\_\_scena**, quindi fare clic su **Salva**.

            ![nuova scena-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.

6.  Nella stessa finestra fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .    

    ![Apri Impostazioni lettore](images/AzureLabs-Lab8-86.png)

7.  In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **altre impostazioni** :

        1.  La **versione di runtime di scripting** deve essere **sperimentale** (equivalente a .NET 4,6)
        2.  Il **back-end di scripting** deve essere ***.NET***
        3.  Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![compatibilità API](images/AzureLabs-Lab8-87.png)

    2.  Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![aggiornare le impostazioni di XR](images/AzureLabs-Lab8-88.png)        

    3.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, Heck:

        - **InternetClient**           

            ![Seleziona client Internet](images/AzureLabs-Lab8-89.png)

8.  Nelle **impostazioni di compilazione**, **i C# progetti Unity** non sono più disattivati: selezionare la casella di controllo accanto a questo.

9.  Al termine di queste modifiche, chiudere la finestra impostazioni di compilazione.

10. Salvare la scena e il **file** di progetto > **Salva scena/file** > **Salva progetto**.

    > [!IMPORTANT]
    > Se si vuole ignorare il componente di *configurazione Unity* per questo progetto (app realtà mista) e continuare direttamente con il codice, è possibile [scaricare questo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare da [ Capitolo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Sarà comunque necessario aggiungere i componenti di script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capitolo 13-importazione delle dll nel progetto di Unity per la realtà mista

Verrà usata la libreria di archiviazione di Azure per Unity (che usa .NET SDK per Azure). Seguire questo collegamento per l' [uso di archiviazione di Azure con Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).
Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare l'SDK nel progetto, assicurarsi di aver scaricato la versione più recente di [. file unitypackage Tools](https://aka.ms/azstorage-unitysdk). Eseguire quindi le operazioni seguenti:

1.  Aggiungere il. file unitypackage Tools scaricato dal precedente a Unity usando l'opzione di menu **asset** > **Importa pacchetto** > **pacchetto personalizzato** .

2.  Nella casella **Importa pacchetto Unity** visualizzata è possibile selezionare tutti gli elementi in **plug** -in > **archiviazione**.

    ![Importa pacchetto](images/AzureLabs-Lab8-90.png)

3.  Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.

4.  Passare alla cartella **archiviazione** in **plug** -in nella visualizzazione del progetto e selezionare *solo*i plug-in seguenti:

    -   Microsoft. Data. Edm
    -   Microsoft. Data. OData
    -   Microsoft. WindowsAzure. storage
    -   Newtonsoft. JSON
    -   System. Spatial

    ![Selezionare i plug-in](images/AzureLabs-Lab8-91.png)

5.  Con *questi plug* -in specifici selezionati, **deselezionare** **qualsiasi piattaforma** e **deselezionare** **WSAPlayer** , quindi fare clic su **applica**.

    ![applicare le modifiche alla piattaforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Si sta contrassegnando questi plug-in particolari da usare solo nell'editor di Unity. Questo è dovuto al fatto che esistono versioni diverse degli stessi plug-in nella cartella WSA che verranno usate dopo l'esportazione del progetto da Unity.

6.  Nella cartella plugin di **archiviazione** selezionare solo:

    -   Microsoft. Data. Services. client

        ![Selezione client Servizi dati](images/AzureLabs-Lab8-93.png)

7.  Selezionare la casella **non elaborare** in **Impostazioni piattaforma** e fare clic su **applica**.

    ![non elaborare](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Si sta contrassegnando questo plug-in "non elaborare" perché il plug-in assembly Unity ha difficoltà nell'elaborare questo plug-in. Il plug-in continuerà a funzionare anche se non viene elaborato.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capitolo 14-creazione della classe TableToScene nel progetto Unity della realtà mista

La classe **TableToScene** è identica a quella illustrata nel [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project). Creare la stessa classe nel progetto Unity della realtà mista seguendo la stessa procedura descritta nel [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Una volta completato questo capitolo, per entrambi i **progetti Unity** questa classe verrà configurata nella fotocamera principale.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capitolo 15-creazione della classe NotificationReceiver nel progetto di Unity per la realtà mista

Il secondo script che è necessario creare è **NotificationReceiver**, responsabile di:

-   Registrazione dell'app con l'hub di notifica al momento dell'inizializzazione.
-   Ascolto delle notifiche provenienti dall'hub di notifica.
-   Deserializzazione dei dati dell'oggetto da notifiche ricevute.
-   Spostare GameObject nella scena in base ai dati deserializzati.

Per creare lo script **NotificationReceiver** :

1.  Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi scegliere **crea**, **C\# script**. Denominare lo script **NotificationReceiver**.

    ![creare un nuovo script c#](images/AzureLabs-Lab8-95.png)
    ![il nome NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Fare doppio clic sullo script per aprirlo.

3.  Aggiungere gli spazi dei nomi seguenti:

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Inserire le variabili seguenti:

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Sostituire il valore di **hubName** con il nome del servizio Hub di notifica e il valore **hubListenEndpoint** con il valore dell'endpoint disponibile nella scheda criteri di accesso, servizio Hub di notifica di Azure nel portale di Azure (vedere l'immagine seguente).

    ![Inserisci endpoint dei criteri di hub di notifica](images/AzureLabs-Lab8-97.png)

6.  A questo punto aggiungere i metodi **Start ()** e **svegli ()** per inizializzare la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Aggiungere il metodo **WaitForNotification** per consentire all'app di ricevere notifiche dalla libreria di hub di notifica senza conflitti con il thread principale:

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  Il metodo seguente, **InitNotificationAsync ()** , registrerà l'applicazione con il servizio Hub di notifica al momento dell'inizializzazione. Il codice è impostato come commento perché Unity non sarà in grado di compilare il progetto. I commenti vengono rimossi quando si importa il pacchetto NuGet di messaggistica di Azure in Visual Studio.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  Il seguente gestore, **Channel\_PushNotificationReceived ()** , verrà attivato ogni volta che viene ricevuta una notifica. La notifica verrà deserializzata, che sarà l'entità di tabella di Azure che è stata spostata nell'applicazione desktop, quindi spostare il GameObject corrispondente nella scena MR nella stessa posizione. 
    
    > [!IMPORTANT]
    > Il codice è impostato come commento perché il codice fa riferimento alla libreria di messaggistica di Azure, che verrà aggiunta dopo aver compilato il progetto Unity usando Gestione pacchetti NuGet, all'interno di Visual Studio. Di conseguenza, il progetto Unity non sarà in grado di eseguire la compilazione, a meno che non sia impostato come commento. Tenere presente che, quando si compila il progetto e quindi si vuole tornare a Unity, è necessario aggiungere di **nuovo il commento** a tale codice.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Ricordarsi di salvare le modifiche prima di tornare all'editor di Unity.

11. Fare clic sulla **fotocamera principale** nel pannello **gerarchia** , in modo che le relative proprietà vengano visualizzate nel **controllo**.

12. Con la cartella degli **script** aperta, selezionare lo script **NotificationReceiver** e trascinarlo sulla **fotocamera principale**. Il risultato dovrebbe essere il seguente:

    ![Trascinare lo script del ricevitore di notifiche nella fotocamera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Se si sta sviluppando questo per Microsoft HoloLens, sarà necessario aggiornare il componente della *fotocamera* della **fotocamera principale**, in modo che:
    > - Cancella flag: colore a tinta unita
    > - Sfondo: nero

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capitolo 16: compilare il progetto di realtà mista in UWP

Questo capitolo è identico al processo di compilazione per il progetto precedente. Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.

1.  Passare a **impostazioni di compilazione** ( **file** > **impostazioni di compilazione** ).

2.  Dal menu **Impostazioni compilazione** verificare che **Unity C# progetti*** sia selezionato (che consente di modificare gli script in questo progetto, dopo la compilazione).

3.  Al termine, fare clic su **Compila**.

    ![Compila progetto](images/AzureLabs-Lab8-99.png)

4.  Verrà visualizzata una finestra **Esplora file** con la richiesta di un percorso da compilare. Creare una nuova cartella (facendo clic su **nuova cartella** nell'angolo superiore sinistro) e denominarla **compilata**.

    ![Crea cartella compilazioni](images/AzureLabs-Lab8-100.png)

    1.  Aprire la nuova cartella **compilazioni** e creare un'altra cartella (usando una **nuova cartella** ancora una volta) e denominarla **NH\_\_app**.

        ![Crea cartella NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  Con l' **App\_di\_di NH** . fare clic su **Seleziona cartella**. La compilazione del progetto verrà eseguita per un minuto.

5.  Dopo la compilazione, viene aperta una finestra **Esplora file** nella posizione del nuovo progetto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Capitolo 17: aggiungere pacchetti NuGet alla soluzione UnityMRNotifHub

> [!WARNING] 
> Tenere presente che, una volta aggiunti i pacchetti NuGet seguenti (e rimuovere il commento dal codice nel [capitolo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)successivo), il codice, quando riaperto nel progetto Unity, presenta degli errori. Se si vuole tornare indietro e continuare la modifica nell'editor di Unity, è necessario aggiungere un commento al codice errosome, quindi rimuovere il commento più tardi, quando si torna in Visual Studio. 

Una volta completata la compilazione di realtà mista, passare al progetto di realtà mista compilato, quindi fare doppio clic sul file di soluzione (con estensione sln) all'interno della cartella per aprire la soluzione con Visual Studio 2017.
A questo punto sarà necessario aggiungere il pacchetto NuGet **WindowsAzure. Messaging. Managed** ; si tratta di una libreria usata per ricevere notifiche dall'hub di notifica.

Per importare il pacchetto NuGet:

1.  Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione

2.  Fare clic su **Gestisci pacchetti NuGet**.

    ![Apri Gestione NuGet](images/AzureLabs-Lab8-102.png)

3.  Selezionare la scheda ***Sfoglia*** e cercare **WindowsAzure. Messaging. Managed**.

    ![trovare il pacchetto di messaggistica di Windows Azure](images/AzureLabs-Lab8-103.png)

4.  Selezionare il risultato (come illustrato di seguito) e nella finestra a destra selezionare la casella di controllo accanto a **progetto**. Verrà inserito un segno di spunta nella casella di controllo accanto a **progetto**, insieme alla casella di controllo accanto al progetto **UnityMRNotifHub** e **CSharp assembly** .

    ![Seleziona tutti i progetti](images/AzureLabs-Lab8-104.png)

5.  La versione fornita inizialmente **potrebbe non** essere compatibile con il progetto. Quindi, fare clic sul menu a discesa accanto a **versione**, scegliere **versione 0.1.7.9**, quindi fare clic su **Installa**.

6.  A questo punto è stata completata l'installazione del pacchetto NuGet. Trovare il codice commentato immesso nella classe **NotificationReceiver** e rimuovere i commenti.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capitolo 18: modificare l'applicazione UnityMRNotifHub, classe NotificationReceiver

Dopo aver aggiunto i **pacchetti NuGet**, sarà necessario rimuovere il *Commento* da parte del codice all'interno della classe **NotificationReceiver** .

È possibile creare, ad esempio:

1. Lo spazio dei nomi nella parte superiore:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Tutto il codice all'interno del metodo **InitNotificationsAsync ()** :

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> Il codice precedente contiene un commento: assicurarsi che non sia stato accidentalmente annullato il *Commento* (poiché il codice non verrà compilato se si dispone di!).

3. Infine, l'evento **Channel_PushNotificationReceived** :

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Con questi commenti, assicurarsi di salvare e quindi passare al capitolo successivo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capitolo 19: associare il progetto di realtà mista all'app dello Store

È ora necessario associare il progetto di **realtà mista** all'app dello Store creata in all'inizio del Lab.

1.  Aprire la soluzione.

2.  Fare clic con il pulsante destro del mouse sul progetto di app UWP nel pannello Esplora soluzioni, passare all' **Archivio**e **associare l'app allo Store...** .

    ![Apri associazione di archiviazione](images/AzureLabs-Lab8-105.png)

3.  Verrà visualizzata una nuova finestra denominata **associare l'app a Windows Store**. Fai clic su **Next**.

    ![passa alla schermata successiva](images/AzureLabs-Lab8-106.png)

4.  Caricherà tutte le applicazioni associate all'account a cui è stato effettuato l'accesso. Se non è stato effettuato l'accesso al proprio account, è possibile **accedere** a questa pagina.

5.  Trovare il **nome dell'app dello Store** creato all'inizio di questa esercitazione e selezionarlo. Fai clic su **Avanti**.

    ![trovare e selezionare il nome dell'archivio](images/AzureLabs-Lab8-107.png)

6.  Fare clic su **associa**.

    ![associare l'app](images/AzureLabs-Lab8-108.png)

7.  L'app è ora **associata** all'app dello Store. Questa operazione è necessaria per abilitare le notifiche.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capitolo 20: distribuire applicazioni UnityMRNotifHub e UnityDesktopNotifHub

Questo capitolo può essere più semplice con due persone, in quanto il risultato includerà sia le app che eseguono, una in esecuzione sul desktop del computer che l'altra all'interno dell'auricolare immersiva.

L'app immersive per la cuffia è in attesa di ricevere le modifiche apportate alla scena (posizione delle modifiche della GameObject locale) e l'app desktop apporterà modifiche alla scena locale (modifiche alla posizione), che verranno condivise nell'app MR. È opportuno distribuire prima l'app MR, seguita dall'app desktop, in modo che il ricevitore possa iniziare l'ascolto.

Per distribuire l'app **UnityMRNotifHub** nel computer locale:

1.  Aprire il file di soluzione dell'app **UnityMRNotifHub** in **Visual Studio 2017**.

2.  Nella **piattaforma soluzione**selezionare **x86, computer locale**.

3.  Nella **configurazione della soluzione** selezionare **debug**.

    ![Imposta configurazione progetto](images/AzureLabs-Lab8-109.png)

4.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.

5.  L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.

Per distribuire l'app **UnityDesktopNotifHub** nel computer locale:

1.  Aprire il file di soluzione dell'app **UnityDesktopNotifHub** in **Visual Studio 2017**.

2.  Nella **piattaforma soluzione**selezionare **x86, computer locale**.

3.  Nella **configurazione della soluzione** selezionare **debug**.

    ![Imposta configurazione progetto](images/AzureLabs-Lab8-110.png)

4.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.

5.  L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.

6.  Avviare l'applicazione di realtà mista, seguita dall'applicazione desktop.

Con entrambe le applicazioni in esecuzione, spostare un oggetto nella scena del desktop (usando il pulsante sinistro del mouse). Queste modifiche posizionali verranno apportate localmente, serializzate e inviate al servizio app per le funzioni. Il servizio di app per le funzioni aggiornerà quindi la tabella insieme all'hub di notifica. Dopo aver ricevuto un aggiornamento, l'hub di notifica invierà i dati aggiornati direttamente a tutte le applicazioni registrate, in questo caso l'app immersiva per le cuffie, che deserializza i dati in arrivo e applica i nuovi dati posizionali agli oggetti locali. spostarli in scena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>L'applicazione Hub di notifica di Azure è stata completata
 
Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio Hub di notifica di Azure e consente la comunicazione tra le app.
 
![fine prodotto finale](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

È possibile capire come modificare il colore di GameObject e inviare la notifica ad altre app che visualizzano la scena?

### <a name="exercise-2"></a>Esercizio 2

È possibile aggiungere lo spostamento di GameObject all'app MR e visualizzare la scena aggiornata nell'app desktop?
