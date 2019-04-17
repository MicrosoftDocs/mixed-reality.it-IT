---
title: MR e Azure 308 - notifiche a più dispositivi
description: Completa questo corso per imparare a implementare gli hub di notifica di Azure, funzioni di Azure e archiviazione di Azure e le tabelle all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, la notifica, funzioni, tabelle, hub di notifica, hololens, vr immersivi,
ms.openlocfilehash: ed56c936a0498b6e0ac804da15a2c6ec98239d0c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604780"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR e Azure 308: Notifiche di più dispositivi

![versione finale del prodotto-avvio](images/AzureLabs-Lab8-00.png)

In questo corso, si apprenderà come aggiungere funzionalità di hub di notifica a un'applicazione di realtà mista tramite hub di notifica di Azure, tabelle di Azure e funzioni di Azure.

**Hub di notifica di Azure** è un servizio Microsoft, che consente agli sviluppatori di inviare notifiche push mirate e personalizzate a qualsiasi piattaforma, tutto con tecnologia nell'ambito del cloud. Questo può consentire in modo efficace agli sviluppatori di comunicare con gli utenti finali o anche la comunicazione tra diverse applicazioni, a seconda dello scenario. Per altre informazioni, visitare il **hub di notifica** [pagina](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).

**Funzioni di Azure** è un servizio Microsoft, che consente agli sviluppatori di eseguire piccole porzioni di codice, 'le funzioni', in Azure. Ciò consente di delegare lavoro nel cloud, anziché l'applicazione locale, che può avere molti vantaggi. **Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, Node. js, Java e PHP. Per altre informazioni, visitare il **funzioni di Azure** [pagina](https://docs.microsoft.com/azure/azure-functions/functions-overview).

**Le tabelle di Azure** è un servizio cloud Microsoft, che consente agli sviluppatori di archiviare dati strutturati non-SQL nel cloud, per renderla facilmente accessibile ovunque. Il servizio vanta una struttura senza schema, che consente l'evoluzione delle tabelle in base alle esigenze e pertanto è molto flessibile. Per altre informazioni, visitare il **tabelle di Azure** [pagina](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Dopo aver completato il corso, si avrà un'applicazione immersive visore VR realtà mista e un'applicazione di PC Desktop, che sarà in grado di eseguire le operazioni seguenti:

1. L'app a PC Desktop consentirà all'utente di spostare un oggetto nello spazio 2D (X e Y), utilizzando il mouse.

2. Lo spostamento di oggetti all'interno dell'app PC verrà inviato al cloud usando JSON, che sarà sotto forma di stringa, contenente un ID di oggetto, tipo e trasforma le informazioni (coordinate X e Y). 

3. L'app di realtà mista, che dispone di una scena identica all'app desktop, sarà inviate notifiche relative alle spostamento di un oggetto, dal servizio hub di notifica (che è stata appena aggiornato dall'app per PC Desktop). 

4. Dopo aver ricevuto una notifica, che conterrà l'ID di oggetto, tipo e le informazioni di trasformazione, l'app di realtà mista applicherà le informazioni ricevute per il proprio scena.

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista. Questo corso è un'esercitazione completa, che non implicano direttamente eventuali altri laboratori di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> MR e Azure 308: Notifiche di più dispositivi</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](install-the-tools.md#installation-checklist)
- [La versione più recente di Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore
- Accesso a Internet per la configurazione di Azure e di accedere agli hub di notifica

## <a name="before-you-start"></a>Prima di iniziare

- Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
- È necessario essere il proprietario del portale per sviluppatori Microsoft e il portale di registrazione dell'applicazione, in caso contrario, non si disporrà dell'autorizzazione per accedere all'app nel [capitolo 2](#chapter-2---retrieve-your-new-apps-credentials).

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capitolo 1 - creare un'applicazione nel portale per sviluppatori Microsoft

Usare la **hub di notifica** servizio, sarà necessario creare un'applicazione nel portale per sviluppatori Microsoft, come l'applicazione dovrà essere registrata, in modo che possa inviare e ricevere le notifiche.

1.  Accedi per il [portale per sviluppatori Microsoft](https://developer.microsoft.com/dashboard).

    > È necessario accedere al tuo Account Microsoft.

2.  Dal Dashboard, fare clic su **creare una nuova app**.

    ![Creare un'app](images/AzureLabs-Lab8-01.png)

3.  Verrà visualizzata una finestra popup, in cui è necessario riservare un nome per la nuova app. Nella casella di testo, inserire un nome appropriato. Se il nome scelto è disponibile, verrà visualizzato un segno di spunta a destra della casella di testo. Dopo aver creato un nome disponibile inserito, scegliere il **riserva nome prodotto** pulsante in basso a sinistra della finestra popup.

    ![un nome inverso](images/AzureLabs-Lab8-02.png)

4.  L'App creata a questo punto, sei pronto a passare al capitolo successivo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capitolo 2: recuperare le nuove credenziali di App

Accedere al portale di registrazione dell'applicazione, in cui la nuova app verrà elencato e recuperare le credenziali che verranno usato per il programma di installazione di **servizio hub di notifica** all'interno di **portale di Azure**.

1.  Passare il [portale di registrazione applicazione](http://apps.dev.microsoft.com).

    ![portale di registrazione dell'applicazione](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > È necessario usare l'Account Microsoft all'account di accesso.  
    > Ciò **devono** l'account di Microsoft che è stato utilizzato nella precedente [capitolo](#chapter-1---create-an-application-on-the-microsoft-developer-portal), con il portale per sviluppatori di Windows Store.

2.  Si noterà l'app con il **mie applicazioni** sezione. Una volta che si sia notato, fare clic su di esso e si accederà a una nuova pagina in cui è installata l'app nome seguito da **registrazione**.

    ![l'app appena registrata](images/AzureLabs-Lab8-04.png)

3.  Scorrere verso il basso la pagina di registrazione per trovare le **i segreti dell'applicazione** sezione e la **SID pacchetto** per l'app. Copiare entrambe per l'utilizzo con configurazione di **servizio di hub di notifica di Azure** nel capitolo successivo.

    ![Segreti dell'applicazione](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capitolo 3 - portale di Azure il programma di installazione: creare il servizio di hub di notifica

Con le credenziali dell'App recuperato, dovrai accedere al portale di Azure, in cui verrà creato un servizio di hub di notifica di Azure.

1.  Accedere al [portale di Azure](https://portal.azure.com).

    > [!NOTE] 
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare **Hub di notifica**, fare clic su ***invio***.

    ![ricerca per hub di notifica](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > La parola ***New*** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

3.  La nuova pagina fornirà una descrizione del *hub di notifica* servizio. AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![creare l'istanza di hub di notifica](images/AzureLabs-Lab8-07.png)

4.  Dopo avere fatto clic su ***Create***:

    1.  Inserire il nome desiderato per questa istanza del servizio.

    2.  Fornire una **dello spazio dei nomi** che sarà in grado di associare a questa app.

    3.  Selezionare un **posizione.**

    4.  Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal). 

    5.  Selezionare un'opzione appropriata **sottoscrizione**.

    6.  È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.

    7. Selezionare **Create**.

        ![Compilandone i dettagli del servizio](images/AzureLabs-Lab8-08.png)

5.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![notifica](images/AzureLabs-Lab8-09.png)

7.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Si verrà indirizzati alla nuova **Hub di notifica** l'istanza del servizio.

    ![Vai alla risorsa](images/AzureLabs-Lab8-10.png)
    
8.  Dalla pagina di panoramica, trova a metà della pagina, fare clic su **Windows (WNS).** Il pannello sulla destra verrà modificato in campi di testo Mostra due, che richiedono il **SID pacchetto** e **chiave di sicurezza**, dall'app è configurato in precedenza.

    ![nuovo servizio hub](images/AzureLabs-Lab8-11.png)

9. Dopo aver copiato i dettagli nei campi corretti, fare clic su **salvare**, e si riceverà una notifica quando l'Hub di notifica è stata aggiornata.

    ![copiare i dettagli di sicurezza](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capitolo 4 - portale di Azure il programma di installazione: creazione del servizio tabelle

Dopo aver creato l'istanza del servizio hub di notifica, passare al portale di Azure, in cui verrà creato un servizio di tabelle di Azure tramite la creazione di una risorsa di archiviazione.

1.  Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).

2.  Una volta effettuato l'accesso, fare clic su **New** nell'angolo in alto a sinistra e cercare **account di archiviazione**, fare clic su **invio**.

    > [!NOTE] 
    > La parola ***New*** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

3.  Selezionare **account di archiviazione: blob, file, tabella, coda** dall'elenco.

    ![eseguire la ricerca di account di archiviazione](images/AzureLabs-Lab8-13.png)

4.  La nuova pagina fornirà una descrizione del **account di archiviazione** servizio. AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'istanza di questo servizio.

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab8-14.png)

5.  Dopo avere fatto clic su **Create**, verrà visualizzato un pannello:

    1. Inserire la posizione desiderata **nome** per questa istanza del servizio (deve contenere solo lettere minuscole).

    2. Per la **modello di distribuzione**, fare clic su **Resource manager**.

    3.  Per la **tipologia Account**, usando il menu a discesa, selezionare **archiviazione (utilizzo generico v1)**.

    4. Selezionare un'opzione appropriata **posizione**.
    
    5.  Per il **replica** dal menu a discesa, seleziona **Read-access-archiviazione geograficamente ridondante (RA-GRS)**.

    6.  Per la **Performance**, fare clic su **Standard**.

    7.  All'interno di **trasferimento sicuro obbligatorio** sezione, selezionare **disabilitato**.

    8.  Dal **sottoscrizione** menu a discesa, selezionare una sottoscrizione appropriata.

    9.  Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Lasciare **reti virtuali** come **disabilitato** se si tratta di un'opzione per l'utente.

    11. Fare clic su **Crea**.

        ![Compilandone i dettagli di archiviazione](images/AzureLabs-Lab8-15.png)

6.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

7.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale. Fare clic su notifiche per esplorare la nuova istanza del servizio.

    ![nuova notifica di archiviazione](images/AzureLabs-Lab8-16.png)

8.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Si verrà indirizzati alla nuova pagina di panoramica di istanza del servizio di archiviazione.

    ![Vai alla risorsa](images/AzureLabs-Lab8-17.PNG)

9. Dalla pagina di panoramica, per il lato destro, fare clic su **tabelle**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. Il pannello sulla destra cambierà e indicherà il **servizio tabelle** informazioni, in cui è necessario aggiungere una nuova tabella. Eseguire questa operazione facendo il **+** **tabella** pulsante nell'angolo superiore sinistro.

    ![Aprire le tabelle](images/AzureLabs-Lab8-19.png)

11. Verrà visualizzata una nuova pagina, in cui è necessario immettere un **nome della tabella**. Questo è il nome che verrà utilizzato per fare riferimento ai dati nell'applicazione nei capitoli successivi. Inserire un nome appropriato e fare clic su **OK**.

    ![Creare una nuova tabella](images/AzureLabs-Lab8-20.png)    

12. Dopo aver creata la nuova tabella, sarà possibile visualizzarlo all'interno di **servizio tabelle** (inferiore) della pagina.

    ![nuova tabella creata](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capitolo 5: completare la tabella di Azure in Visual Studio

Ora che il **servizio tabelle** account di archiviazione è stata configurata, è possibile aggiungere dati a esso, che verrà usato per archiviare e recuperare informazioni. La modifica delle tabelle può essere eseguita tramite **Visual Studio**.

1.  Aprire **Visual Studio**.

2.  Dal menu, fare clic su **Visualizza > Cloud Explorer**.

    ![Aprire cloud explorer](images/AzureLabs-Lab8-22.png)

3.  Il **Cloud Explorer** verranno aperte come un elemento ancoraggio (essere paziente, come il caricamento potrebbe richiedere tempo).

    > [!NOTE] 
    > Se la sottoscrizione è stata usata per creare le *gli account di archiviazione* non è visibile, assicurarsi di avere: 
    > - Per lo stesso account come quello usato per il portale di Azure connesso.
    > - Selezionare la sottoscrizione dalla pagina di gestione di Account (potrebbe essere necessario applicare un filtro da impostazioni dell'account):  
    >
    >   ![trovare la sottoscrizione](images/AzureLabs-Lab8-22-5.png)

4.  Verranno visualizzati i servizi cloud di Azure. Trovare **gli account di archiviazione** e fare clic sulla freccia a sinistra di tale per espandere l'account.

    ![Aprire l'account di archiviazione](images/AzureLabs-Lab8-23.png)

5.  Una volta espanso, appena creato **account di archiviazione** devono essere disponibili. Fare clic sulla freccia a sinistra della risorsa di archiviazione e quindi una volta che viene espanso, individuare **tabelle** e fare clic sulla freccia accanto a cui, per visualizzare i **tabella** creato nel capitolo precedente. Fare doppio clic il **tabella**.

    ![Aprire la tabella oggetti di scena](images/AzureLabs-Lab8-24.png)

6.  La tabella verrà aperta al centro della finestra di Visual Studio. Fare clic sull'icona di tabella con il **+** (più) su di esso.

    ![Aggiungi nuova tabella](images/AzureLabs-Lab8-25.png)

7.  Verrà visualizzata richiede una finestra per poter *Aggiungi entità*. Si creerà tre entità in totale, ciascuno con diverse proprietà. Si noterà che *PartitionKey* e *RowKey* già disponibili, poiché verranno usati per trovare i dati dalla tabella. 

    ![chiave di partizione e di riga](images/AzureLabs-Lab8-26.png)

8. Aggiornamento di *valore* del **PartitionKey** e **RowKey** come indicato di seguito (ricordarsi di eseguire questa operazione per ogni proprietà di riga si aggiungono, tuttavia incrementare ogni volta che l'elemento RowKey):

    ![aggiungere i valori corretti](images/AzureLabs-Lab8-26-5.png)

9.  Fare clic su **aggiungere proprietà** per aggiungere ulteriori righe di dati. Creare la prima tabella vuota corrisponde la tabella seguente.

10. Fare clic su **OK** al termine.

    ![Fare clic su ok al termine](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Assicurarsi di aver modificato il **tipo** delle **X**, **Y**, e **Z**, le voci per **Double**. 

11. Si noterà che la tabella ora presenta una riga di dati. Scegliere il **+** (icona Nuovo per aggiungere un'altra entità più).

    ![prima riga](images/AzureLabs-Lab8-27-5.png)

12. Creare una proprietà aggiuntiva e quindi impostare i valori della nuova entità in modo che corrispondano a quelle riportate di seguito.

    ![aggiungere cubo](images/AzureLabs-Lab8-28.png)

13. Ripetere l'ultimo passaggio per aggiungere un'altra entità. Impostare i valori per questa entità su quelle riportate di seguito.

    ![aggiungere cilindro](images/AzureLabs-Lab8-29.png)

14. La tabella dovrebbe ora essere simile al seguente.

    ![tabella completa](images/AzureLabs-Lab8-30.png)

15. È stata completata in questo capitolo. Assicurarsi di salvare.

## <a name="chapter-6---create-an-azure-function-app"></a>Capitolo 6: creare un'App per le funzioni di Azure

Creare un'App di funzione di Azure, che verrà chiamato dall'applicazione Desktop per aggiornare il **tabella** del servizio e invia una notifica tramite il **Hub di notifica**.

In primo luogo, è necessario creare un file che consentirà la funzione di Azure caricare le librerie che necessarie.

1.  Aprire **Notepad** (premere tasto Windows e digitare notepad).

    ![Aprire Blocco note](images/AzureLabs-Lab8-31.png)

2.  Aprire Blocco note, inserire la struttura JSON seguente al suo interno. Una volta che è stato fatto che, salvarlo sul desktop come **Project. JSON**. È importante che il nome sia corretto: assicurarsi che avviene **non è un file con estensione txt** estensione di file. Questo file definisce le librerie che userà la funzione, se si usa NuGet avrà un aspetto familiare.

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

3.  Accedi per il [portale di Azure](https://portal.azure.com).

4.  Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare **App per le funzioni**, premere **invio**.

    ![cercare app per le funzioni](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

5.  La nuova pagina fornirà una descrizione del **App per le funzioni** servizio. AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![istanza dell'app (funzione)](images/AzureLabs-Lab8-33.png)

6.  Dopo avere fatto clic su **Create**, compilare i campi seguenti:

    1. Per la **nome App**, inserire il nome desiderato per questa istanza del servizio.

    2. Selezionare una **sottoscrizione**.

    3. Selezionare il piano tariffario appropriato per l'utente, se questa è la prima volta che la creazione di un **servizio App di funzione**, un livello gratuito deve essere disponibile all'utente.

    4. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Per la **OS**, fare clic su Windows, che è la piattaforma desiderata.

    6. Selezionare una **piano di Hosting** (questa esercitazione Usa un **piano a consumo**.

    7. Selezionare una **ubicazione** **(scegliere la stessa ubicazione come risorsa di archiviazione che hanno creato nel passaggio precedente)**

    8. Per il **memorizzazione** sezione **è necessario selezionare il servizio di archiviazione creato nel passaggio precedente**.

    9. Non è necessario *Application Insights* in questa app, è possibile lasciarlo **Off**.

    10. Fare clic su **Crea**.

        ![creare una nuova istanza](images/AzureLabs-Lab8-34.png)

7.  Dopo avere fatto clic su **Create** si dovrà attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

8.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![nuova notifica](images/AzureLabs-Lab8-35.png)

9.  Fare clic su notifiche per esplorare la nuova istanza del servizio.

10. Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. 

    ![Vai alla risorsa](images/AzureLabs-Lab8-36.png)

11. Scegliere il **+** (più) icona accanto a *funzioni*, a *Crea nuovo*.

    ![Aggiungi nuova funzione](images/AzureLabs-Lab8-37.png)

12. All'interno del pannello centrale, il **funzione** verrà visualizzata la finestra di creazione. Ignorare le informazioni nella parte superiore del pannello e fare clic su **funzione personalizzata**, che si trova nella parte inferiore (nell'area blu, come indicato di seguito).

    ![funzione personalizzata](images/AzureLabs-Lab8-38.png)

13. Nella pagina nuovo all'interno della finestra verranno visualizzati diversi tipi di funzione. Scorrere verso il basso per visualizzare i tipi di colore viola e fare clic su **PUT HTTP** elemento.

    ![collegamento put http](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Potrebbe essere necessario scorrere ulteriormente verso la freccia giù della pagina e questa immagine potrebbe non esattamente lo stesso aspetto, se siano stati eseguiti aggiornamenti del portale di Azure, tuttavia, si sta cercando un elemento denominato *PUT HTTP*.

14. Il **PUT HTTP** verrà visualizzata la finestra in cui è necessario configurare la funzione (vedere di seguito per l'immagine).

    1.  Per la **linguaggio** utilizzando il menu a discesa, selezionare C\#.

    2.  Per la **nome,** immettere un nome appropriato.

    3.  Nel **a livello di autenticazione** dal menu a discesa, seleziona **funzione**.

    4.  Per il **nome della tabella** sezione, è necessario usare il nome esatto usato per creare le **tabella** servizio precedentemente (tra cui le stesse maiuscole/minuscole).

    5.  All'interno di **connessione dell'account di archiviazione** sezione, usare il menu a discesa e selezionare l'account di archiviazione da tale posizione. Se non è presente, fare clic il **New** hyperlink insieme il titolo di sezione, per visualizzare un altro pannello, in cui dovrebbe essere elencato nell'account di archiviazione.

        ![nuova risorsa di archiviazione](images/AzureLabs-Lab8-40.png)

15. Fare clic su **Create** e si riceverà una notifica che le impostazioni sono state aggiornate correttamente.

    ![creare (funzione)](images/AzureLabs-Lab8-41.png)

16. Dopo aver fatto clic **Create**, si verrà reindirizzati all'editor di funzione.

    ![aggiornare il codice di funzione](images/AzureLabs-Lab8-42.png)

17. Inserire il codice seguente nell'editor di funzione (sostituendo il codice nella funzione di):

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
    > Usando le librerie incluse, la funzione riceve il nome e il percorso dell'oggetto che è stato spostato nella scena Unity (come un C# oggetto, definito **UnityGameObject**). Questo oggetto viene quindi usato per aggiornare i parametri dell'oggetto all'interno della tabella creata. In seguito, la funzione effettua una chiamata al servizio Hub di notifica creato, che notifica alle applicazioni tutti sottoscritte.

18. Con il codice, fare clic su **salvare**.

19. Successivamente, fare clic il **\<** icona (freccia), sul lato destro della pagina.

    ![Pannello Apri caricamento](images/AzureLabs-Lab8-43.png)

20. Un pannello verrà diapositiva da destra. In questo pannello, fare clic su **caricare**, e verrà visualizzato un Browser di File.

21. Passare a e quindi, il **Project. JSON** file, che è stato creato in **blocco note** in precedenza e quindi fare clic sui **Open** pulsante. Questo file definisce le librerie che userà la funzione.

    ![Carica json](images/AzureLabs-Lab8-44.png)

22. Quando il file è stato caricato, verrà visualizzato nel pannello a destra. Clic su di esso verrà aperta all'interno di **funzione** editor. È necessario ottenere **esattamente** quello utilizzato per l'immagine successiva (in basso passaggio 23).

23. Quindi, nel pannello a sinistra, sotto **funzioni**, fare clic sui **integra** collegamento.

    ![integrare (funzione)](images/AzureLabs-Lab8-45.png)

24. Nella pagina successiva, nell'angolo superiore destro, fare clic su **editor avanzato** (come indicato di seguito).

    ![editor avanzato aperto](images/AzureLabs-Lab8-46.png)

25. Oggetto **Function. JSON** file verrà aperto nel Pannello di center, che deve essere sostituito con il frammento di codice seguente. Questa impostazione definisce la funzione crei e i parametri passati alla funzione.

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

26. L'editor dovrebbe ora essere simile all'immagine seguente:

    ![tornare all'editor standard](images/AzureLabs-Lab8-47.png)

27. È possibile riscontrare i parametri di input che è stato inserito potrebbero non corrispondere i dettagli della tabella e archiviazione e pertanto dovrà essere aggiornata con le informazioni. **Non eseguire questa operazione qui**, perché è coperto successivamente. È sufficiente fare clic il **editor Standard** collegamento, nell'angolo superiore destro della pagina, tornare indietro.

28. Nel **editor Standard**, fare clic su **archiviazione tabelle di Azure (tabella)**, sotto **input**. 
    
    ![Input di tabelle](images/AzureLabs-Lab8-47-5.png)

29. Verificare che la corrispondenza seguente per **il** informazioni, queste potrebbero essere diversi (è disponibile un'immagine di seguito i passaggi seguenti):

    1.  **Nome della tabella**: il nome della tabella creata all'interno di archiviazione di Azure, servizio tabelle.

    2.  **Connessione dell'account di archiviazione:** fare clic su **nuovi**, che viene visualizzata accanto nel menu a discesa e verrà visualizzato un pannello a destra della finestra.

        ![nuova risorsa di archiviazione](images/AzureLabs-Lab8-48.png)

        1.  Selezionare i **Account di archiviazione**, creato in precedenza per ospitare il **App per le funzioni.**

        2. Si noterà che il **Account di archiviazione** valore di connessione è stato creato.

        3. Assicurarsi di premere **salvare** dopo aver terminato.

    3.  Il **input** pagina dovrebbe ora corrispondere il seguente, che mostra **il** informazioni.

        ![input completo](images/AzureLabs-Lab8-49.png)

30. Fare quindi clic **Hub di notifica di Azure (notifica)** : in **output**. Assicurarsi che corrispondono a quanto segue **il** informazioni, queste potrebbero essere diversi (è disponibile un'immagine di seguito la procedura seguente):

    1.  **Nome Hub di notifica**: si tratta del nome delle **dell'Hub di notifica** istanza del servizio creato in precedenza.

    2.  **Connessione dello spazio dei nomi hub di notifica**: fare clic su **nuovi**, che viene visualizzata accanto nel menu a discesa.

        ![controllare gli output](images/AzureLabs-Lab8-50.png)

    3. Il **Connection** popup verrà visualizzati (vedere la figura seguente), in cui è necessario selezionare la **Namespace** del **Hub di notifica**, che devono essere impostate in precedenza.

    4. Selezionare i **Hub di notifica** nome dal menu a discesa intermedio.

    5.  Impostare il **criterio** dal menu a discesa per **DefaultFullSharedAccessSignature**.

    6. Scegliere il **seleziona** pulsante per tornare indietro.

        ![aggiornamento di output](images/AzureLabs-Lab8-51.png)

31.  Il **output** pagina dovrebbe ora corrispondere il più avanti, ma con **il** informazioni invece. Assicurarsi di premere **salvare**.

> [!WARNING]
> *Non modificare direttamente il nome dell'Hub di notifica* (tutti eseguire questa operazione usando il **Editor avanzato**, a condizione che è stata seguita la procedura precedente in modo corretto.

![output completo](images/AzureLabs-Lab8-50.png)

32. A questo punto, è consigliabile testare la funzione, per assicurarsi che del corretto funzionamento. A tale scopo, effettuare le seguenti operazioni: 

    1. Passare alla pagina di funzione ancora una volta:

        ![output completo](images/AzureLabs-Lab8-50-1.png)

    2. Tornare alla pagina di funzione e fare clic sui **Test** scheda all'estrema destra di destra della pagina, aprire il *Test* pannello:

        ![output completo](images/AzureLabs-Lab8-50-2.png)

    3. All'interno di **corpo della richiesta** nella casella di testo del pannello, incollare il codice riportato di seguito:

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

    4. Con il test di codice, scegliere il **eseguire** pulsante in basso a destra e il test verrà eseguito. I log di output del test saranno visualizzati nell'area di console, sotto il codice della funzione.

        ![output completo](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Se il test precedente non riesce, è necessario per controllare di aver seguito i passaggi precedenti esattamente, in particolare le impostazioni all'interno di **integrare pannello**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capitolo 7 - configurazione di progetto Desktop di Unity

> [!IMPORTANT]
> L'applicazione Desktop che si sta ora creando, **non** funzionano nell'Editor di Unity. Deve essere eseguito all'esterno dell'Editor, dopo la compilazione dell'applicazione, usando Visual Studio (o l'applicazione distribuita). 

Di seguito è una tipica configurato per lo sviluppo con Unity e realtà mista e di conseguenza, è un buon modello per altri progetti.

Configurare e testare il visore VR immersivi di realtà mista.

> [!NOTE] 
> Verrà **non** richiedono controller di movimento a questo corso. Se è necessario il supporto di configurazione di visore VR immersivi, seguire questa [collegamento su come impostare la realtà mista di Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Aprire **Unity** e fare clic su **New**.

    ![nuovo progetto unity](images/AzureLabs-Lab8-52.png)

2.  È necessario specificare un nome di progetto Unity, inserire **UnityDesktopNotifHub**. Verificare che il tipo di progetto è impostato su **3D**. Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![Crea progetto](images/AzureLabs-Lab8-53.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![set di strumenti di Visual Studio esterni](images/AzureLabs-Lab8-54.png)

4.  Passare quindi ad **File > Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sui **commutatore piattaforma** pulsante per applicare la selezione.

    ![passare a piattaforme](images/AzureLabs-Lab8-55.png)

5.  Mentre si trovano ancora nella **File > Build Settings**, assicurarsi che:

    1.  **Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**

        > Questa applicazione sarà per il desktop, pertanto deve essere **qualsiasi dispositivo**

    2.  **Tipo di compilazione** è impostata su **D3D**

    3.  **SDK** è impostata su **installata più recente**

    4.  **Versione di Visual Studio** è impostata su **installata più recente**

    5.  **Compilare ed eseguire** è impostata su **computer locale**

    6.  A questo punto, vale la pena di salvataggio della scena e aggiungerlo alla compilazione.

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.

            ![aggiungere scene open](images/AzureLabs-Lab8-56.png)

        2. Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![nuova cartella scene](images/AzureLabs-Lab8-57.png)

        3. Aprire appena creato **scene** cartella e quindi il **nome File:** campo di testo, digitare **hub di notifica\_Desktop\_scena**, quindi premere **Salvare**.

            ![new NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.

6.  Nella stessa finestra fare clic sui **le impostazioni del giocatore** pulsante, si aprirà il pannello correlato nello spazio in cui le **Inspector** si trova.

7.  In questo pannello, alcune impostazioni devono essere verificati:

    1.  Nel **altre impostazioni** scheda:

        1.  **Versione del Runtime di scripting** deve essere **sperimentale (equivalente con .NET 4.6)**

        2. **Back-end di scripting** deve essere **.NET**

        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![versione di .NET 4.6](images/AzureLabs-Lab8-59.png)

    2.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        - **InternetClient**

            ![client internet di segni di graduazione](images/AzureLabs-Lab8-60.png)

8.  Nuovamente in **Build Settings** *Unity C\# progetti* non è non è più in grigio, selezionare la casella di controllo accanto a questo.

9.  Chiudi il **Build Settings** finestra.

10. Salvare il progetto e la scena **File > Salva scena* / * File > Salva progetto * *.

    > [!IMPORTANT]
    > Se si vuole ignorare la *configurare Unity* componente per il progetto (App Desktop) e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importarlo nel progetto come un [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  È comunque necessario aggiungere i componenti di script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capitolo 8 - importazione di DLL in Unity

Si userà archiviazione di Azure per Unity (che a sua volta si basa su .net SDK per Azure). Per altre informazioni, seguire questo [collegamento su archiviazione di Azure per Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.

Per importare il SDK in un progetto, assicurarsi di aver scaricato la versione più recente [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) da GitHub. Quindi, eseguire le operazioni seguenti:

1.  Aggiungere il **.unitypackage** a Unity tramite il **asset \> Importa pacchetto \> pacchetto personalizzato** l'opzione di menu.

2.  Nel **Importa pacchetto Unity** casella visualizzata, è possibile selezionare tutti gli elementi in * **plug-in* \> * archiviazione * * *.  Deseleziona tutto il resto, perché non è necessaria per questo corso.

    ![Importa pacchetto](images/AzureLabs-Lab8-61.png)

3.  Scegliere il ***importazione*** pulsante per aggiungere elementi al progetto.

4.  Andare alla **Storage** cartella sotto **plug-in** nel progetto consente di visualizzare e selezionare il plug-in seguenti *solo*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![Deselezionare qualsiasi piattaforma](images/AzureLabs-Lab8-62.png)

5.  Con *questi plug-in specifici* è selezionata, **deselezionare** **Any Platform** e **deselezionare** **WSAPlayer** quindi fare clic su **applica**.

    ![applicare le DLL di piattaforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Vengono contrassegnati questi plug-in particolare per essere usato solo nell'Editor di Unity. Questo avviene perché sono presenti versioni diverse dello stesso plug-nella cartella WSA che verrà utilizzata dopo che il progetto viene esportato da Unity.

6.  Nel **archiviazione** cartella plug-in, selezionare solo:

    -   Microsoft.Data.Services.Client

        ![non elabora set di DLL](images/AzureLabs-Lab8-64.png)

7.  Verificare i **processo non** nella casella **impostazioni piattaforma** e fare clic su ***Apply***.

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Vengono contrassegnati questo plug-in "Non elabora", perché il patcher assembly di Unity ha difficoltà a questo plug-in di elaborazione. Il plug-in continuerà a funzionare anche se non è stato elaborato.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capitolo 9 - creare la classe TableToScene nel progetto Unity Desktop

È ora necessario creare gli script che contiene il codice per eseguire questa applicazione.

È il primo script da creare **TableToScene**, che è responsabile per:

-   La lettura delle entità all'interno della tabella di Azure.
-   Usando i dati della tabella, determinare gli oggetti da generare e in quale posizione.

È il secondo script è necessario creare **CloudScene**, che è responsabile per:

-   Registrazione dell'evento, quindi fare clic su per consentire all'utente di trascinare gli oggetti per la scena.
-   Serializzare i dati dell'oggetto da questa scena Unity e inviarlo all'App per le funzioni di Azure.

Per creare questa classe:

1.  Fare doppio clic nella **bene** cartella si trova nel pannello dei progetti **Crea > cartella**. Denominare la cartella **script**.

    ![Crea cartella scripts](images/AzureLabs-Lab8-66.png)

    ![creare la cartella degli script 2](images/AzureLabs-Lab8-67.png)

2.  Fare doppio clic sulla cartella appena creata, per aprirlo.

3.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create** **C\# Script**. Denominare lo script **TableToScene**.

    ![nuovo script c#](images/AzureLabs-Lab8-68.png)
    ![TableToScene ridenominazione](images/AzureLabs-Lab8-69.png)

4.  Fare doppio clic sullo script per aprirlo in Visual Studio 2017.

5.  Aggiungere spazi dei nomi seguenti:

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
    > Sostituire il **NomeAccount** valore con il nome del servizio di archiviazione di Azure e **accountKey** valore con il valore della chiave trovato nel servizio di archiviazione di Azure, nel portale di Azure (vedere immagine seguente). 
    >
    > ![chiave dell'account di recupero](images/AzureLabs-Lab8-70.png)

7.  A questo punto aggiungere il **Start ()** e **Awake()** metodi per inizializzare la classe.

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

8.  All'interno di **TableToScene** classe, aggiungere il metodo che recupererà i valori della tabella di Azure e usarle per generare le primitive appropriate nella scena.

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

9.  Di fuori di **TableToScene** (classe), è necessario definire la classe utilizzata dall'applicazione per serializzare e deserializzare le **entità tabella**.

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

10. Assicurarsi di aver **salvare** prima di tornare all'Editor di Unity.

11. Fare clic sui **Main Camera** dalle **gerarchia** pannello, in modo che le proprietà visualizzate nella **Inspector**.

12. Con il **gli script** cartella aperta, selezionare lo script **file TableToScene** e trascinarla nel **Main Camera**. Il risultato dovrebbe essere come indicato di seguito:

    ![aggiungere script alla fotocamera principale](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capitolo 10 - creare la classe CloudScene nel progetto Unity Desktop

È il secondo script è necessario creare **CloudScene**, che è responsabile per:

-   Registrazione dell'evento, quindi fare clic su per consentire all'utente di trascinare gli oggetti per la scena.

-   Serializzare i dati dell'oggetto da questa scena Unity e inviarlo all'App per le funzioni di Azure.

Per creare il secondo script:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**, **C\# Script**. Denominare lo script **CloudScene**
    
    ![nuovo script c#](images/AzureLabs-Lab8-72.png)
    ![rinominare CloudScene](images/AzureLabs-Lab8-73.png)

2.  Aggiungere spazi dei nomi seguenti:

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

4.  Sostituire il **azureFunctionEndpoint** valore con l'URL dell'App funzione Azure trovare la funzione di servizio App di Azure, nel portale di Azure, come illustrato nell'immagine seguente:

    ![Recupera URL della funzione](images/AzureLabs-Lab8-74.png)

5.  A questo punto aggiungere il **Start ()** e **Awake()** metodi per inizializzare la classe.

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

6.  All'interno di **Update ()** metodo, aggiungere il codice seguente che rileva l'input del mouse e trascinare, che a sua volta sposterà Gameobject nella scena. Se l'utente ha trascinato e rilasciato un oggetto, passerà il nome e le coordinate dell'oggetto al metodo **UpdateCloudScene()**, che chiamerà il servizio App di funzioni di Azure, che aggiornerà le tabelle di Azure e i trigger di notifica.

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

7.  A questo punto aggiungere il **UpdateCloudScene()** (metodo), come indicato di seguito:

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

9.  Trascinare il **CloudScene** nello script le **Main Camera**. 

    1. Fare clic sui **Main Camera** dalle **gerarchia** pannello, in modo che le proprietà visualizzate nella **Inspector**. 

    2. Con il **gli script** aperto, selezionare cartella la **CloudScene** script e trascinarla nel **Main Camera**. Il risultato dovrebbe essere come indicato di seguito:

        > ![Trascinare uno script cloud fotocamera principale](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Capitolo 11 - compilare il progetto per Desktop alla piattaforma UWP

Tutti gli elementi necessari per la sezione di Unity di questo progetto a questo punto è stato completato.

1.  Passare a **impostazioni di compilazione** (**File > Impostazioni di compilazione**).

2.  Dal **Build Settings** finestra, fare clic su **compilazione**.

    ![Compila progetto](images/AzureLabs-Lab8-76.png)

3.  Oggetto **Esplora File** popup verrà finestra, di cui è possibile specificare un percorso di compilazione. Creare una nuova cartella (facendo **nuova cartella** nell'angolo superiore sinistro) e denominarla **COMPILA**.

    ![nuova cartella per la compilazione](images/AzureLabs-Lab8-77.png)

    1.  Aprire il nuovo **si basa** cartella e creare un'altra cartella (utilizzando **nuova cartella** ancora una volta) e denominarlo **hub di notifica\_Desktop\_App**.

        ![folder name NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Con il **hub di notifica\_Desktop\_App** selezionato. Fare clic su **Seleziona cartella**. Il progetto avrà un minuto alla compilazione.

4.  Compilazione, in seguito **Esplora File** apparirà mostrano la posizione del nuovo progetto. Nessuna necessità di aprire il file, tuttavia, che è necessario creare anche l'altro Unity project in primo luogo, entro i prossimi capitoli.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capitolo 12: configurare progetti di Unity di realtà mista

Di seguito è una tipica configurato per lo sviluppo con la realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire **Unity** e fare clic su **New**.

    ![nuovo progetto unity](images/AzureLabs-Lab8-79.png)

2.  A questo punto si dovrà fornire un nome di progetto Unity, inserire **UnityMRNotifHub**. Verificare che il tipo di progetto è impostato su **3D**. Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![set editor esterno a Visual Studio](images/AzureLabs-Lab8-81.png)

4.  Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.

    ![piattaforme commutatore alla piattaforma UWP](images/AzureLabs-Lab8-82.png)

5.  Passare a **File > Build Settings** e assicurarsi che:

    1.  **Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**

        > Per il Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.

    2.  **Tipo di compilazione** è impostata su **D3D**

    3.  **SDK** è impostata su **installata più recente**

    4.  **Versione di Visual Studio** è impostata su **installata più recente**

    5.  **Compilare ed eseguire** è impostata su **computer locale**

    6.  A questo punto, vale la pena di salvataggio della scena e aggiungerlo alla compilazione.

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.

            ![aggiungere scene open](images/AzureLabs-Lab8-83.png)

        2. Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![nuova cartella scene](images/AzureLabs-Lab8-84.png)

        3. Aprire appena creato **scene** cartella e quindi la **nome File:** campo di testo, digitare **hub di notifica\_MR\_scena**, quindi premere  **Salvare**.

            ![new scene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.

6.  Nella stessa finestra fare clic sui **le impostazioni del giocatore** pulsante, si aprirà il pannello correlato nello spazio in cui le **Inspector** si trova.    

    ![Aprire le impostazioni del giocatore](images/AzureLabs-Lab8-86.png)

7.  In questo pannello, alcune impostazioni devono essere verificati:

    1.  Nel **altre impostazioni** scheda:

        1.  **Versione del Runtime di scripting** deve essere **sperimentale** (.NET 4.6 equivalente)
        2.  **Back-end di scripting** deve essere ***.NET***
        3.  **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![compatibilità con le API](images/AzureLabs-Lab8-87.png)

    2.  Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto

        ![xr Aggiorna impostazioni](images/AzureLabs-Lab8-88.png)        

    3.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, archivia il:

        - **InternetClient**           

            ![client internet di segni di graduazione](images/AzureLabs-Lab8-89.png)

8.  Nuovamente in **Build Settings** *Unity C\# progetti* non è non è più in grigio: selezionare la casella di controllo accanto a questo.

9.  Con queste modifiche eseguite, chiudere la finestra Impostazioni di compilazione.

10. Salvare il progetto e la scena **File* *Salva scena*/ *File* * Salva progetto * *.

    > [!IMPORTANT]
    > Se si vuole ignorare la *configurare Unity* componente per questo progetto (App di realtà misto) e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importarlo nel progetto come una [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), quindi continuare dal [capitolo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). È comunque necessario aggiungere i componenti di script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capitolo 13 - importazione di DLL nel progetto Unity realtà mista

Si userà archiviazione di Azure per la libreria di Unity (che usa .net SDK per Azure). Seguire questa [collegamento su come usare archiviazione di Azure con Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).
È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.

Per importare il SDK in un progetto, assicurarsi di aver scaricato la versione più recente [.unitypackage](https://aka.ms/azstorage-unitysdk). Quindi, eseguire le operazioni seguenti:

1.  Aggiungere il .unitypackage scaricato da quanto sopra, Unity tramite il **asset > Importa pacchetto > pacchetto personalizzato** l'opzione di menu.

2.  Nel **Importa pacchetto Unity** casella visualizzata, è possibile selezionare tutti gli elementi sotto **plug-in > archiviazione**.

    ![Importa pacchetto](images/AzureLabs-Lab8-90.png)

3.  Scegliere il **importazione** pulsante per aggiungere elementi al progetto.

4.  Andare alla **Storage** cartella sotto **plug-in** nel progetto consente di visualizzare e selezionare il plug-in seguenti *solo*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![Selezionare i plug-in](images/AzureLabs-Lab8-91.png)

5.  Con *questi plug-in specifici* è selezionata, **deselezionare** **Any Platform** e **deselezionare** **WSAPlayer** quindi fare clic su **applica**.

    ![applicare le modifiche alla piattaforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Si contrassegna questi plug-in particolare per essere usato solo nell'Editor di Unity. Questo avviene perché sono presenti versioni diverse dello stesso plug-nella cartella WSA che verrà utilizzata dopo che il progetto viene esportato da Unity.

6.  Nel **archiviazione** cartella plug-in, selezionare solo:

    -   Microsoft.Data.Services.Client

        ![Selezionare il client di servizi dati](images/AzureLabs-Lab8-93.png)

7.  Verificare i **processo non** nella casella **impostazioni piattaforma** e fare clic su **Apply**.

    ![non elaborare](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Si contrassegna questo plug-in "Non elabora" perché il patcher assembly di Unity ha difficoltà a questo plug-in di elaborazione. Il plug-in continuerà a funzionare anche se questa non viene elaborata.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capitolo 14 - Creazione della classe TableToScene nel progetto Unity realtà mista

Il **TableToScene** classe è identico a quello illustrato in [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project). Creare la stessa classe nella realtà mista progetto Unity seguendo la stessa procedura illustrata nel [capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Dopo aver completato questo capitolo, entrambi i **i progetti Unity** avrà questa classe impostato su Main Camera.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capitolo 15 - creazione della classe NotificationReceiver nel progetto Unity realtà mista

È il secondo script è necessario creare **NotificationReceiver**, che è responsabile per:

-   La registrazione dell'app con l'Hub di notifica in fase di inizializzazione.
-   Ascoltare le notifiche provenienti dall'Hub di notifica.
-   Durante la deserializzazione di dati dell'oggetto dalle notifiche ricevute.
-   Spostare il Gameobject nella scena, in base i dati deserializzati.

Per creare il **NotificationReceiver** script:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**, **C\# Script**. Denominare lo script **NotificationReceiver**.

    ![creare il nuovo script c#](images/AzureLabs-Lab8-95.png)
    ![denominarlo NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Fare doppio clic sullo script per aprirlo.

3.  Aggiungere spazi dei nomi seguenti:

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

5.  Sostituire il **hubName** valore con il nome del servizio Hub di notifica e **hubListenEndpoint** valore con il valore di endpoint disponibile nella scheda Criteri di accesso, servizio di Hub di notifica di Azure, nel Portale di Azure (vedere la figura seguente).

    ![Inserisci endpoint criteri hub di notifica](images/AzureLabs-Lab8-97.png)

6.  A questo punto aggiungere il **Start ()** e **Awake()** metodi per inizializzare la classe.

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

7.  Aggiungere il **WaitForNotification** metodo per consentire all'app di ricevere le notifiche dalla libreria di Hub di notifica senza sovrapposizioni con il Thread principale:

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

8.  Il metodo seguente, **InitNotificationAsync()**, registrerà l'applicazione con il servizio Hub di notifica in fase di inizializzazione. Il codice viene commentato poiché Unity non saranno in grado di compilare il progetto. Quando si importa il pacchetto Nuget di messaggistica di Azure in Visual Studio verranno rimossi i commenti.

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

9.  Il seguente gestore **Channel\_PushNotificationReceived()**, verrà attivata ogni volta che viene ricevuta una notifica. Eseguirà la deserializzazione di notifica, che verrà entità della tabella di Azure che è stato spostato nell'applicazione Desktop e quindi spostare il GameObject corrispondente nella scena MR nella stessa posizione. 
    
    > [!IMPORTANT]
    > Il codice viene commentato perché il codice fa riferimento la libreria di messaggistica di Azure, che verranno aggiunti dopo la compilazione del progetto Unity usando Gestione pacchetti Nuget, Visual Studio. Di conseguenza, il progetto Unity non sarà possibile creare, a meno che questo non è commentato. Tenere presente, che dovrebbe si compila il progetto e quindi si vuole tornare a Unity, dovrai **nuovamente commento** tale codice.

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

10. Ricordarsi di salvare le modifiche prima di tornare all'Editor di Unity.

11. Fare clic sui **Main Camera** dalle **gerarchia** pannello, in modo che le proprietà visualizzate nella **Inspector**.

12. Con il **gli script** aperto, selezionare cartella la **NotificationReceiver** script e trascinarla nel **Main Camera**. Il risultato dovrebbe essere come indicato di seguito:

    ![Trascinare script del destinatario notifica alla fotocamera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Se si sta sviluppando ciò per i Microsoft HoloLens, dovrai aggiornare il **Main Camera**del *fotocamera* componente, in modo che:
    > - Cancellare i flag: Colore a tinta unita
    > - Background: Nero

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capitolo 16 - compilare il progetto di realtà mista alla piattaforma UWP

In questo capitolo è identico al processo per il progetto precedente di compilazione. Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.

1.  Passare a **impostazioni di compilazione** ( **File > Impostazioni di compilazione...**  ).

2.  Dal **Build Settings** menu, assicurarsi che **Unity C# progetti*** è selezionata (che consente di modificare gli script di questo progetto, dopo la compilazione).

3.  Dopo questa operazione, fare clic su **compilazione**.

    ![Compila progetto](images/AzureLabs-Lab8-99.png)

4.  Oggetto **Esplora File** popup verrà finestra, di cui è possibile specificare un percorso di compilazione. Creare una nuova cartella (facendo **nuova cartella** nell'angolo superiore sinistro) e denominarla **COMPILA**.

    ![creare una cartella delle build](images/AzureLabs-Lab8-100.png)

    1.  Aprire il nuovo **si basa** cartella e creare un'altra cartella (utilizzando **nuova cartella** ancora una volta) e denominarlo **hub di notifica\_MR\_App**.

        ![Crea cartella NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  Con il **hub di notifica\_MR\_App** selezionato. Fare clic su **Seleziona cartella**. Il progetto avrà un minuto alla compilazione.

5.  Dopo la compilazione, un **Esplora File** aprirà la finestra in corrispondenza della posizione del nuovo progetto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Capitolo 17 - aggiungere pacchetti NuGet alla soluzione UnityMRNotifHub

> [!WARNING] 
> Si ricordi che, dopo aver aggiunto i pacchetti NuGet seguenti (e rimuovere il commento il codice entro i prossimi [capitolo](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class)), il codice, quando all'interno del progetto Unity, riaperto presenterà errori. Se si vuole tornare indietro e continuare la modifica nell'Editor di Unity, sarà necessario commentare tale codice errosome e quindi rimuovere il commento nuovamente in un secondo momento, quando si è in Visual Studio. 

Dopo aver completata la compilazione di realtà mista, passare al progetto di realtà mista, è stata compilata, e fare doppio clic sul file di soluzione (sln) da quella cartella, aprire la soluzione con Visual Studio 2017.
È ora necessario aggiungere il **Windowsazure** pacchetto NuGet; si tratta di una libreria che consente di ricevere le notifiche dall'Hub di notifica.

Per importare il pacchetto NuGet:

1.  Nel **Esplora soluzioni**, fare clic con il pulsante destro sulla soluzione

2.  Fare clic su **Gestisci pacchetti NuGet**.

    ![Aprire Gestione nuget](images/AzureLabs-Lab8-102.png)

3.  Selezionare il ***esplorare*** scheda e cercare **Windowsazure**.

    ![trovare il pacchetto di messaggistica di windows azure](images/AzureLabs-Lab8-103.png)

4.  Selezionare il risultato (come illustrato di seguito) e nella finestra a destra, selezionare la casella di controllo accanto a **progetto**. Verrà inserito un segno di spunta nella casella di controllo accanto a **Project**, con la casella di controllo accanto al **Assembly-CSharp** e **UnityMRNotifHub** progetto.

    ![tutti i progetti di graduazione](images/AzureLabs-Lab8-104.png)

5.  La versione fornita inizialmente **potrebbe non** siano compatibili con questo progetto. Pertanto, fare clic sul menu a discesa accanto a **versione**, fare clic su **versione 0.1.7.9**, quindi fare clic su **installare**.

6.  È ora di installazione del pacchetto NuGet è stata completata. Trovare il codice con commento immessi nella **NotificationReceiver** classe e rimuovere i commenti...



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capitolo 18 - classe NotificationReceiver, UnityMRNotifHub Modifica applicazione

Dopo avere aggiunto il **i pacchetti NuGet**, sarà necessario *rimuovere il commento* parte del codice all'interno del **NotificationReceiver** classe.

È possibile creare, ad esempio:

1. Lo spazio dei nomi nella parte superiore:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Tutto il codice all'interno di **InitNotificationsAsync()** metodo:

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
> Il codice precedente contiene un commento: assicurarsi di aver accidentalmente *senza commenti* che come commento (come il codice non verrà compilato se hai!).

3. E, infine, il **Channel_PushNotificationReceived** evento:

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

Con questi senza commenti, assicurarsi di salvare e quindi procedere al capitolo successivo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capitolo 19 - associare il progetto di realtà mista per l'app Store

È ora necessario associare il **realtà mista** progetto nell'App Store creato all'inizio del lab.

1.  Aprire la soluzione.

2.  Fare clic con il pulsante destro sul progetto di app UWP nel Pannello di Esplora soluzioni, andare al **Store**, e **Associa applicazione a Store di...** .

    ![Aprire associazione archivio](images/AzureLabs-Lab8-105.png)

3.  Verrà visualizzata una nuova finestra chiamata **associa l'applicazione con il Windows Store**. Fare clic su **Avanti**.

    ![Passare alla schermata successiva](images/AzureLabs-Lab8-106.png)

4.  Verrà caricato tutte le applicazioni associate con l'Account che hanno effettuato l'accesso. Se non si è connessi al proprio account, è possibile **Log In** in questa pagina.

5.  Trovare il **nome dell'App Store** creato all'inizio di questa esercitazione e selezionarlo. Fare quindi clic su **Avanti**.

    ![Individuare e selezionare il nome dell'archivio](images/AzureLabs-Lab8-107.png)

6.  Fare clic su **associare**.

    ![associare l'app](images/AzureLabs-Lab8-108.png)

7.  L'App è ora **Associated** con l'App Store. Ciò è necessario per l'abilitazione di notifiche.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capitolo 20 - distribuire applicazioni UnityMRNotifHub e UnityDesktopNotifHub

In questo capitolo può essere più semplice con due persone, poiché il risultato includerà sia le App in esecuzione, una in esecuzione nel computer Desktop e l'altro all'interno di visore VR immersivi.

L'app visore VR immersivi è in attesa di ricevere le modifiche alla scena (modifiche della posizione del Gameobject locale) e l'app Desktop subirà modifiche alla loro scena locale (modifiche della posizione), che verrà condiviso con l'app MR. È opportuno distribuire l'app MR in primo luogo, seguita dall'app Desktop, in modo che il destinatario può iniziare in ascolto.

Per distribuire il **UnityMRNotifHub** app nel computer locale:

1.  Aprire il file della soluzione delle **UnityMRNotifHub** in app **Visual Studio 2017**.

2.  Nel **piattaforma soluzione**, selezionare **x86, computer locale**.

3.  Nel **configurazione della soluzione** selezionate **Debug**.

    ![set di configurazione del progetto](images/AzureLabs-Lab8-109.png)

4.  Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.

5.  L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.

Per distribuire il **UnityDesktopNotifHub** app nel computer locale:

1.  Aprire il file della soluzione delle **UnityDesktopNotifHub** in app **Visual Studio 2017**.

2.  Nel **piattaforma soluzione**, selezionare **x86, computer locale**.

3.  Nel **configurazione della soluzione** selezionate **Debug**.

    ![set di configurazione del progetto](images/AzureLabs-Lab8-110.png)

4.  Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.

5.  L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.

6.  Avviare l'applicazione di realtà mista, seguito dall'applicazione Desktop.

Con entrambe le applicazioni in esecuzione, spostare un oggetto nella scena desktop (con il pulsante del Mouse a sinistra). Queste modifiche posizionali verranno essere eseguite in locale, serializzate e inviate al servizio App per le funzioni. Il servizio App per le funzioni aggiornerà quindi la tabella con l'Hub di notifica. Aver ricevuto un aggiornamento, l'Hub di notifica invia i dati aggiornati direttamente a tutte le applicazioni registrate (in questo caso l'app visore VR immersivi), che verranno quindi deserializzare i dati in ingresso e applicare i nuovi dati posizionali agli oggetti locali, lo spostamento nella scena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Il termine applicazione hub di notifica di Azure
 
Complimenti, è stata compilata un'app per realtà mista che sfrutta il servizio hub di notifica di Azure e consentire la comunicazione tra app.
 
![versione finale del prodotto-fine](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

È possibile usare le istruzioni per modificare il colore del Gameobject e inviare notifica ad altre App visualizzazione scena?

### <a name="exercise-2"></a>Esercizio 2

È possibile aggiungere lo spostamento del Gameobject all'app di MR e visualizzato la scena aggiornata nell'app desktop?
