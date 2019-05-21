---
title: MR e 305 Azure - funzioni e archiviazione
description: Completare questo corso di informazioni su come implementare l'archiviazione di Azure e le funzioni all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, funzioni, archiviazione, hololens, vr immersivi,
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598302"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR e Azure 305: Funzioni e archiviazione

![versione finale del prodotto-avvio](images/AzureLabs-Lab5-00.png)

In questo corso, si apprenderà come creare e usare funzioni di Azure e archiviare i dati con una risorsa di archiviazione di Azure, all'interno di un'applicazione di realtà mista.

*Funzioni di Azure* è un servizio Microsoft, che consente agli sviluppatori di eseguire piccole porzioni di codice, 'le funzioni', in Azure. Ciò consente di delegare lavoro nel cloud, anziché l'applicazione locale, che può avere molti vantaggi. *Funzioni di Azure* supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, Node. js, Java e PHP. Per altre informazioni, visitare il [articolo funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).

*Archiviazione di Azure* è un servizio cloud Microsoft, che consente agli sviluppatori di archiviare i dati, con l'assicurazione che sarà altamente disponibile, sicuro, durevole, scalabile e ridondante. Ciò significa che Microsoft gestirà tutti manutenzione e i problemi critici per l'utente. Per altre informazioni, visitare il [articolo di archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Dopo aver completato il corso, si avrà un'applicazione di realtà mista visore VR immersivi che sarà in grado di eseguire le operazioni seguenti:

1.  Consentire all'utente di estasiati intorno a una scena.
2.  Attivare la generazione di oggetti, quando l'utente gazes in un 'button' 3D.
3.  Gli oggetti generati verranno scelto da una funzione di Azure.
4.  Poiché ogni oggetto viene generato, l'applicazione archivierà il tipo di oggetto in un *File di Azure*che si trova in *archiviazione di Azure*.
5.  Durante il caricamento di una seconda volta, il *File di Azure* dati verranno recuperati e utilizzati per riprodurre le azioni di generazione dell'istanza precedente dell'applicazione.

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare le applicazioni di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>MR e Azure 305: Funzioni e archiviazione</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens.

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
- Una sottoscrizione a un account Azure per la creazione di risorse di Azure
- Accesso a Internet per il recupero di dati e il programma di installazione di Azure

## <a name="before-you-start"></a>Prima di iniziare

Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1 - portale di Azure

Usare la **servizio di archiviazione di Azure**, sarà necessario creare e configurare un **Account di archiviazione** nel portale di Azure.

1.  Accedi per il [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *account di archiviazione*, fare clic su **invio**.

    ![ricerca di archiviazione di Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

3.  La nuova pagina fornirà una descrizione del *account di archiviazione Azure* servizio. AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![Crea servizio](images/AzureLabs-Lab5-02.png)

4.  Dopo avere fatto clic su **Create**:

    1.  Inserire un *nome* per l'account, tenere presente questo campo accetta solo numeri e lettere minuscole.

    2.  Per la *modello di distribuzione*, selezionare **Resource manager**.

    3.  Per la *tipologia Account*, selezionare **archiviazione (utilizzo generico v1)**.

    4.  Determinare il *posizione* per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

    5.  Per la *replica* selezionate **Read-access-archiviazione geograficamente ridondante (RA-GRS)**.

    6.  Per la *Performance*, selezionare **Standard**.

    7.  Lasciare *trasferimento sicuro obbligatorio* come **disabilitato**.

    8.  Selezionare una *sottoscrizione*.

    9. Scegliere una *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni). 

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.

    11. Selezionare **Create**.

        ![informazioni di input del servizio](images/AzureLabs-Lab5-03.png)

5.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![nuova notifica nel portale di azure](images/AzureLabs-Lab5-04.png)

7.  Fare clic su notifiche per esplorare la nuova istanza del servizio.

    ![Vai alla risorsa](images/AzureLabs-Lab5-05.png)

8.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Si verrà indirizzati alla nuova *account di archiviazione* l'istanza del servizio.

    ![tasti di scelta](images/AzureLabs-Lab5-06.png)

9.  Fare clic su *chiavi di accesso*, per visualizzare gli endpoint per questo servizio cloud. Usare *Notepad* o simile, per copiare una delle chiavi per un uso successivo. Si noti anche il *stringa di connessione* valore, perché verrà usato nel *servizi di Azure* (classe), che verrà creato in un secondo momento.

    ![Copiare la stringa di connessione](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capitolo 2: configurazione di una funzione di Azure

Ora si scriverà un' **Azure** **funzione** nel servizio di Azure.

È possibile usare un **funzione di Azure** per eseguire praticamente qualsiasi operazione che si farebbe con una funzione classica nel codice, la differenza è che questa funzione è accessibile da qualsiasi applicazione che dispone delle credenziali per accedere all'Account Azure.

Per creare una funzione di Azure:

1.  Dalle *portale di Azure*, fare clic su **New** nell'angolo in alto a sinistra e cercare *App per le funzioni*, fare clic su **invio**.

    ![Creare app per le funzioni](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

2.  La nuova pagina fornirà una descrizione del *App per le funzioni* servizio. AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![informazioni sull'app (funzione)](images/AzureLabs-Lab5-09.png)

3.  Dopo avere fatto clic su **Create**:

    1.  Fornire un' *nome App*. Solo lettere e numeri possono essere usati di seguito (è consentito sia maiuscole o minuscole).

    2.  Selezionare la voce preferita *sottoscrizione*.

    3. Scegliere una *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni). 

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Per questo esercizio, selezionare *Windows* come la scelta **OS**.

    5.  Selezionare *piano a consumo* per il **piano di Hosting**.

    6.  Determinare il *posizione* per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche. Per ottenere prestazioni ottimali, selezionare la stessa area dell'account di archiviazione.

    7.  Per la *memorizzazione*, selezionare **Usa esistente**, e quindi utilizzando il menu a discesa, individuare lo spazio di archiviazione creato in precedenza.

    8.  Lasciare *Application Insights* disattivata per questo esercizio.

        ![dettagli dell'app input (funzione)](images/AzureLabs-Lab5-10.png)

4.  Fare clic sul pulsante **Crea**.

5.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![nuove notifiche del portale di azure](images/AzureLabs-Lab5-11.png)

7.  Fare clic su notifiche per esplorare la nuova istanza del servizio. 

    ![Passare alla risorsa app per le funzioni](images/AzureLabs-Lab5-12.png)

8.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Si verrà indirizzati alla nuova *App per le funzioni* l'istanza del servizio.

9.  Nel *App per le funzioni* dashboard, posizionare il mouse sopra *funzioni*trovato all'interno del pannello a sinistra e quindi fare clic sui **+ (segno più)** simbolo.

    ![Creare una nuova funzione](images/AzureLabs-Lab5-13.png)

10. Nella pagina successiva, assicurarsi **Webhook e API** è selezionata e per *scegliere una lingua* seleziona **CSharp**, come sarà la lingua utilizzata per questa esercitazione. Infine, fare clic il **consente di creare questa funzione** pulsante.

    ![Selezionare web hook csharp](images/AzureLabs-Lab5-14.png)

11. Si verrà reindirizzati al codice di pagina (Run. csx), in caso contrario, fare clic sulla funzione appena creata nell'elenco le funzioni all'interno del pannello a sinistra.

    ![Aprire una nuova funzione](images/AzureLabs-Lab5-15.png)

12. Copiare il codice seguente alla funzione. Questa funzione restituirà semplicemente un numero intero casuale compreso tra 0 e 2 quando viene chiamato. Non preoccuparti del codice esistente, è possibile incollare nella parte superiore di esso.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Selezionare **Salva**.

14. Il risultato dovrebbe essere simile all'immagine seguente.

15. Fare clic su **recupera URL della funzione** e prendere nota del *endpoint* visualizzato. È necessario inserirla nel *servizi di Azure* classe che verrà creato più avanti in questo corso.

    ![ottenere l'endpoint (funzione)](images/AzureLabs-Lab5-16.png)

    ![ottenere l'endpoint (funzione)](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capitolo 3 - configurazione del progetto Unity

Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.

Configurare e testare il visore VR immersivi di realtà mista.

> [!NOTE]
> Verrà **non** richiedono controller di movimento a questo corso. Se è necessario il supporto di configurazione di visore VR immersivi, please [visitare la realtà mista configurare articolo](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Aprire Unity e fare clic su **New**.

    ![creare nuovo progetto unity](images/AzureLabs-Lab5-17.png)

2.  A questo punto, è necessario specificare un nome di progetto Unity. Inserire **MR_Azure_Functions**. Verificare che il tipo di progetto è impostato su **3D**. Impostare il *posizione* a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![assegnare un nome nuovo progetto unity](images/AzureLabs-Lab5-18.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **modificare* > *preferenze** e quindi dalla nuova finestra, passare a **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![set di visual studio come editor di script](images/AzureLabs-Lab5-19.png)

4.  Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.

    ![piattaforma del commutatore alla piattaforma uwp](images/AzureLabs-Lab5-20.png)

5.  Passare a **File > Build Settings** e assicurarsi che:

    1. **Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**.

        > Per Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.

    2. **Tipo di compilazione** è impostata su **D3D**

    3. **SDK** è impostata su **installata più recente**

    4. **Versione di Visual Studio** è impostata su **installata più recente**

    5. **Compilare ed eseguire** è impostata su **computer locale**

    6. Salvare la scena e aggiungerlo alla compilazione.

        1.  Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.

            ![aggiungere scene open](images/AzureLabs-Lab5-21.png)

        2.  Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![creare la cartella in background](images/AzureLabs-Lab5-22.png)

        3.  Aprire appena creato **scene** cartella e quindi il **nome File:** campo di testo, digitare **FunctionsScene**, quindi premere **Salva**.

            ![Salva scena le funzioni](images/AzureLabs-Lab5-23.png)

6.  Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.

    ![Salva scena le funzioni](images/AzureLabs-Lab5-24.png)

7.  Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.

    ![impostazioni del lettore di controllo](images/AzureLabs-Lab5-25.png)

8.  In questo pannello, alcune impostazioni devono essere verificati:

    1.  Nel **altre impostazioni** scheda:

        1.  **Versione del Runtime di scripting** deve essere **sperimentale** (.NET 4.6 equivalente), che attiverà una necessità di riavviare l'Editor.
        2.  **Back-end di scripting** deve essere **.NET**
        3.  **Livello di compatibilità delle API** deve essere **.NET 4.6**

    2.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:
        
        -  **InternetClient**

            ![set di funzionalità](images/AzureLabs-Lab5-26.png)

    3.  Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **le impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **realtà mista di Windows SDK** viene aggiunto.

        ![XR le impostazioni](images/AzureLabs-Lab5-27.png)

9.  Nuovamente in *Build Settings* *Unity C# progetti* non è più è disattivata; selezionare la casella di controllo accanto a questo.

    ![progetti c# segni di graduazione](images/AzureLabs-Lab5-28.png)

10.  Chiudere la finestra Impostazioni di compilazione.

11. Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).

## <a name="chapter-4---setup-main-camera"></a>Capitolo 4 - la fotocamera principale di installazione

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componenti di questo corso e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo nel progetto come un [personalizzato Pacchetto](https://docs.unity3d.com/Manual/AssetPackages.html). Questa conterrà anche la DLL del capitolo successivo. Al termine dell'importazione, sono la prosecuzione [capitolo 7](#chapter-7---create-the-azureservices-class). 

1.  Nel *Pannello di gerarchia*, si noterà un oggetto denominato **Main Camera**, questo oggetto rappresenta il punto di vista della "head" quando si è "l'applicazione interni".

2.  Con il Dashboard di Unity fronte, selezionare la **Main Camera GameObject**. Si noterà che il *Pannello di controllo* (in genere trovato a destra, all'interno del Dashboard) mostrerà i vari componenti di tale *GameObject*, con *trasformare* nella parte superiore, seguita da *fotocamera*e alcuni altri componenti. È necessario reimpostare la trasformazione della fotocamera principale, in modo che sia posizionato correttamente.

3.  A questo scopo, selezionare la **a forma di ingranaggio** icona accanto della fotocamera *trasformare* componente e selezionare **Reimposta**.

    ![reimpostazione della trasformazione](images/AzureLabs-Lab5-29.png)

4.  Aggiornare quindi il **trasformare** componente come illustrato:

    |         |    TRASFORMAZIONE - POSIZIONE   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRASFORMAZIONE - ROTAZIONE |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORM - SCALE |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![trasformazione della fotocamera set](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capitolo 5 - configurare la scena Unity

1.  Pulsante destro del mouse in un'area vuota del *Pannello di gerarchia*, in **oggetto 3D**, aggiungere un **piano**.

    ![Crea nuovo piano](images/AzureLabs-Lab5-31.png)

2.  Con il **piano** dell'oggetto selezionato, modificare i parametri seguenti nel *Pannello di controllo*:

    |       | TRASFORMAZIONE - POSIZIONE |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORM - SCALE |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![Imposta piano posizione e scala](images/AzureLabs-Lab5-32.png)

    ![visualizzazione scena del piano](images/AzureLabs-Lab5-33.png)

3.  Pulsante destro del mouse in un'area vuota del *Pannello di gerarchia*, in **oggetto 3D**, aggiungere un **cubo**.

    1.  Rinominare il cubo **GazeButton** (con il cubo selezionato, premere 'F2').

    2.  Modificare i parametri seguenti nel *Pannello di controllo*:

        |       | TRASFORMAZIONE - POSIZIONE |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![set sguardo pulsante trasformazione](images/AzureLabs-Lab5-34.png)

        ![estasiati visualizzazione scena pulsante](images/AzureLabs-Lab5-35.png)

    3.  Fare clic sui **Tag** pulsante a discesa e fare clic su **aggiungere Tag** per aprire il *tag & riquadro livelli*.

        ![Aggiungi nuovo tag](images/AzureLabs-Lab5-36.png)

        ![Select plus](images/AzureLabs-Lab5-37.png)

    4.  Selezionare il **+ (segno più)** pulsante e il *nuovo nome del Tag* immettere **GazeButton**e premere **Salva**.

        ![nuovo tag di nome](images/AzureLabs-Lab5-38.png)

    5.  Fare clic sul **GazeButton** dell'oggetto nel *pannello gerarchia*e nel *Pannello di controllo*, assegnare l'oggetto appena creato **GazeButton** tag.

        ![pulsante di sguardo assegna il nuovo tag](images/AzureLabs-Lab5-39.png)

4.  Fare clic sul **GazeButton** dell'oggetto, nelle *pannello gerarchia*e aggiungere un **GameObject vuoto** (che verrà aggiunto come un *figlio* oggetto).

5.  Selezionare il nuovo oggetto e rinominarlo **ShapeSpawnPoint**.

    1.  Modificare i parametri seguenti nel *Pannello di controllo*:

        |       | TRASFORMAZIONE - POSIZIONE |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![trasformazione di punto di aggiornamento forma spawn](images/AzureLabs-Lab5-40.png)

        ![vista forma spawn punto della scena](images/AzureLabs-Lab5-41.png)

6.  Successivamente verrà creato un **testo 3D** oggetto da fornire commenti e suggerimenti sullo stato del servizio di Azure.

    Fare clic con il pulsante destro sul **GazeButton** nella gerarchia del pannello nuovo e aggiungere un **oggetto 3D > testo 3D** dell'oggetto come un *figlio*.

    ![creare nuovi oggetti di testo 3D](images/AzureLabs-Lab5-42.png)

7.  Rinominare il **testo 3D** obiettare **AzureStatusText**.

8.  Modifica il **AzureStatusText** trasformazione dell'oggetto come indicato di seguito:

    |       | TRASFORMAZIONE - POSIZIONE |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | TRANSFORM - SCALE |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > Non occorre preoccuparsi se sembrano essere disattivato centre, come questo problema verrà risolto quando il seguente testo Mesh componente viene aggiornato.

9.  Modifica il **Mesh testo** componente in modo che corrisponda di seguito:

    ![componente mesh testo set](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > Colore selezionato qui è di colore esadecimale: **000000FF**, tuttavia è possibile scegliere il proprio, assicurarsi sia leggibile.

10. La struttura di gerarchia pannello sarà simile al seguente:

    ![testo mesh nella visualizzazione scena](images/AzureLabs-Lab5-43b.png)

10. La scena a questo punto dovrebbe essere simile al seguente:

    ![testo mesh nella visualizzazione scena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capitolo 6: importare l'archiviazione di Azure per Unity

Si userà archiviazione di Azure per Unity (che a sua volta si basa su .net SDK per Azure). È possibile leggere altre informazioni, vedere la [archiviazione di Azure per l'articolo di Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.

Per importare il SDK in un progetto, assicurarsi di aver scaricato la versione più recente ['.unitypackage' da GitHub](https://aka.ms/azstorage-unitysdk). Quindi, eseguire le operazioni seguenti:

1.  Aggiungere il **.unitypackage** file da Unity tramite il **asset > Importa pacchetto > pacchetto personalizzato** l'opzione di menu.

2.  Nel **Importa pacchetto Unity** casella visualizzata, è possibile selezionare tutti gli elementi in **plug-in* > *archiviazione**. Deseleziona tutto il resto, perché non è necessaria per questo corso.

    ![Importa pacchetto](images/AzureLabs-Lab5-45.png)

3.  Scegliere il **importazione** pulsante per aggiungere elementi al progetto.

4.  Passare al *archiviazione* cartella sotto *Plugins*, nella visualizzazione del progetto e selezionare il plug-in seguenti *solo*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![Deselezionare qualsiasi piattaforma](images/AzureLabs-Lab5-46.png)

5.  Con *questi plug-in specifici* è selezionata, **deselezionare** *Any Platform* e **deselezionare** *WSAPlayer* quindi fare clic su **applica**.

    ![applicare le DLL di piattaforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Vengono contrassegnati questi plug-in particolare per essere usato solo nell'Editor di Unity. Questo avviene perché sono presenti versioni diverse dello stesso plug-nella cartella WSA che verrà utilizzata dopo che il progetto viene esportato da Unity.

6.  Nel *archiviazione* cartella plug-in, selezionare solo:

    -   Microsoft.Data.Services.Client

        ![non elabora set di DLL](images/AzureLabs-Lab5-48.png)

7.  Verificare i **processo non** nella casella *impostazioni piattaforma* e fare clic su **Apply**.

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Vengono contrassegnati questo plug-in "Non elabora" perché il patcher assembly di Unity ha difficoltà a questo plug-in di elaborazione. Il plug-in continuerà a funzionare anche se non è stato elaborato.

## <a name="chapter-7---create-the-azureservices-class"></a>Capitolo 7 - creare la classe di servizi di Azure

La prima classe si intende creare è il *servizi di Azure* classe.

Il *servizi di Azure* classe sarà responsabile per:

-   Archiviare le credenziali dell'Account di Azure.

-   Chiamare la funzione di App di Azure.

-   Il caricamento e il download del file di dati nell'archiviazione Cloud di Azure.

Per creare questa classe:

1.  Fare doppio clic nella *bene* cartella, che si trova nel pannello dei progetti **Crea > cartella**. Denominare la cartella **script**.

    ![Crea nuova cartella](images/AzureLabs-Lab5-50.png)

    ![cartella chiamata - script](images/AzureLabs-Lab5-51.png)

2.  Fare doppio clic sulla cartella appena creata, per aprirlo.

3.  Pulsante destro del mouse all'interno della cartella **Crea > C# Script**. Chiamare lo script *servizi di Azure*.

4.  Fare doppio clic su nuova *servizi di Azure* classe per aprirlo con *Visual Studio*.

5.  Aggiungere spazi dei nomi seguenti all'inizio del *servizi di Azure*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Aggiungere i seguenti campi di controllo all'interno di *servizi di Azure* classe:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  Quindi aggiungere le seguenti variabili membro all'interno di *servizi di Azure* classe:

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Assicurarsi di sostituire il *endpoint* e *stringa di connessione* valori con i valori da archiviazione di Azure, disponibile nel portale di Azure

8.  Codice per un *Awake()* e *Start ()* metodi deve ora essere aggiunto. Questi metodi verranno chiamati quando si inizializza la classe:

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > Si compilerà il codice per *CallAzureFunctionForNextShape()* in un [capitolo future](#chapter-10---completing-the-AzureServices-class).

9.  Eliminare il *Update ()* metodo poiché questa classe non verrà utilizzate.

10. Salvare le modifiche in Visual Studio e quindi tornare a Unity.

11. Fare clic e trascinare il *servizi di Azure* classe dalla cartella degli script per l'oggetto Main Camera nel *gerarchia pannello*.

12. Selezionare la fotocamera principale, quindi selezionare il **AzureStatusText** oggetto figlio da sotto il **GazeButton** dell'oggetto e inserirla all'interno di **AzureStatusText** target di riferimento nel campo la *Inspector*, per fornire il riferimento al *servizi di Azure* script.

    ![assegnare una destinazione del riferimento di testo dello stato di azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capitolo 8 - creare la classe ShapeFactory

Lo script successivo per la creazione, è il *ShapeFactory* classe. Il ruolo di questa classe consiste nel creare una nuova forma, quando richiesto e conservare una cronologia delle forme creato in una *elenco di cronologia forma*. Ogni volta che viene creata una forma, il *elenco cronologia forma* viene aggiornato nel *AzureService* classe e quindi archiviati nel *archiviazione di Azure*. Quando viene avviata l'applicazione, se viene trovato un file archiviato nel *archiviazione di Azure*, il *elenco cronologia forma* viene recuperato e riprodotti, con il **testo 3D** oggetto fornendo indica se il generato shape è dall'archiviazione o i nuovi.

Per creare questa classe:

1.  Andare alla **script** cartella creata in precedenza.

2.  Pulsante destro del mouse all'interno della cartella **Crea > C# Script**. Chiamare lo script *ShapeFactory*.

3.  Fare doppio clic su nuova *ShapeFactory* script per aprirlo con *Visual Studio*.

4.  Verificare che il *ShapeFactory* classe include spazi dei nomi seguenti:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Aggiungere le variabili mostrate di seguito per il *ShapeFactory* e sostituire il *Start ()* e *Awake()* funzioni con quelli seguenti:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  Il *createShape ()* metodo genera le forme di primitive, in base al fornito *integer* parametro. Il parametro booleano viene usato per specificare se la forma attualmente creata da un archivio o nuovo. Inserire il codice seguente nel *ShapeFactory* (classe), i metodi sopra riportati di seguito:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Assicurarsi di salvare le modifiche in Visual Studio prima di tornare a Unity.

8.  Indietro nell'Editor di Unity, fare clic e trascinare il *ShapeFactory* classe il **script** cartella per il **Main Camera** dell'oggetto nel *gerarchia pannello*.

9. Con la fotocamera principale selezionato si noterà il *ShapeFactory* componente script non è presente il *Spawn punto* riferimento. Per risolvere il problema, trascinare il **ShapeSpawnPoint** dall'oggetto il *pannello gerarchia* per il **Spawn punto** target di riferimento.

    ![destinazione del riferimento di set di forma factory](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capitolo 9 - creare la classe sguardo

È l'ultimo script è necessario creare il *estasiati* classe.

Questa classe è responsabile per la creazione di un **Raycast** che sarà proiettato in avanti dalla fotocamera principale, per rilevare l'oggetto sta guardando l'utente. In questo caso, sarà necessario il Raycast identificare se l'utente sta guardando il **GazeButton** oggetti nella scena e attivare un comportamento.

Per creare questa classe:

1.  Andare alla **script** cartella creata in precedenza.

2.  Pulsante destro del mouse nel pannello dei progetti **Crea > C# Script**. Chiamare lo script *estasiati*.

3.  Fare doppio clic su nuova *estasiati* script per aprirlo con *Visual Studio.*

4.  Assicurarsi che lo spazio dei nomi seguente è incluso nella parte superiore dello script:

    ```csharp
        using UnityEngine;
    ```

5.  Quindi aggiungere le variabili seguenti all'interno di *estasiati* classe:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Alcune di queste variabili potranno essere modificati nel *Editor*.

6.  Il codice per il *Awake()* e *Start ()* metodi deve ora essere aggiunto.

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Aggiungere il codice seguente, che verrà creato un oggetto cursore all'inizio, con la *Update ()* metodo, che verrà eseguito il metodo Raycast, oltre a essere in cui è attivato o disattivato il valore booleano GazeEnabled:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. Successivamente aggiungere il *UpdateRaycast()* metodo, che sarà un Raycast del progetto e rilevare la destinazione di hit.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Infine, aggiungere il *ResetFocusedObject()* metodo, che si attiva o disattiva il colore corrente oggetti GazeButton, che indica se che si sta creando una nuova forma o No.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Salvare le modifiche in Visual Studio prima di tornare a Unity.

11.  Fare clic e trascinare il *estasiati* classe dalla cartella degli script per il **Main Camera** dell'oggetto nel *gerarchia pannello*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Capitolo 10 - completamento della classe di servizi di Azure

Con gli altri script posto, è ora possibile *completa* le *servizi di Azure* classe. Questo verrà ottenuto tramite:

1.  Aggiunta di un nuovo metodo denominato *CreateCloudIdentityAsync()* per impostare le variabili di autenticazione necessarie per la comunicazione con Azure.

    > Questo metodo inoltre verifica l'esistenza di un File archiviato in precedenza che contiene l'elenco di forma.
    >
    > **Se il file si trova**, disabilita l'utente *estasiati*e attivare la creazione di forma, in base al modello di forme, archiviato nel **file di archiviazione di Azure**. L'utente può visualizzare, come le **Mesh testo** fornirà display 'Storage' o 'New', a seconda dell'origine di forme.
    >
    > **Se viene trovato alcun file**, abiliterà il *estasiati*, consentendo all'utente di creare forme quando si esaminano le **GazeButton** oggetti nella scena.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  Il frammento di codice successivo viene dall'interno di *Start ()* metodo; in cui verrà eseguita una chiamata per il *CreateCloudIdentityAsync()* (metodo). È possibile copiare correnti *Start ()* (metodo), con il seguito:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Compilare il codice per il metodo *CallAzureFunctionForNextShape()*. Si userà creato in precedenza *App per le funzioni* per richiedere un indice di forma. Dopo aver ricevuta la nuova forma, questo metodo invia la forma per il *ShapeFactory* classe per creare la nuova forma nella scena. Usare il codice seguente per completare il corpo della *CallAzureFunctionForNextShape()*.

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  Aggiungere un metodo per creare una stringa, concatenando i numeri interi archiviati nell'elenco della cronologia di forma e salvarli nel *File di archiviazione di Azure*.

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  Aggiungere un metodo per recuperare il testo archiviato nel file che si trova nel *File di archiviazione di Azure* e *deserializzare* in un elenco.

6.  Una volta completato questo processo, il metodo riabilita lo sguardo in modo che l'utente può aggiungere più forme nella scena.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Salvare le modifiche in Visual Studio prima di tornare a Unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Capitolo 11 - compilare la soluzione di piattaforma UWP

Per iniziare il processo di compilazione:

1.  Passare a **File > Impostazioni di compilazione**.

    ![Compilare l'app](images/AzureLabs-Lab5-54.png)

2.  Fai clic su **Compila**. Unity avvierà una *Esplora File* finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in. Creare ora tale cartella e denominarlo *App*. Quindi con il *App* cartella selezionata, premere **Seleziona cartella**.

3.  Unity verrà avviata la compilazione del progetto per la *App* cartella.

4.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un *Esplora File* finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).

## <a name="chapter-12---deploying-your-application"></a>Capitolo 12 - distribuzione dell'applicazione

Per distribuire l'applicazione:

1.  Passare al *App* cartella di cui è stata creata nel [ultimo capitolo](#chapter-11---build-the-uwp-solution). Verrà visualizzato un file con il nome dell'App con l'estensione '. sln', che è necessario fare doppio clic, pertanto, per aprirlo in *Visual Studio*.

2.  Nel **piattaforma soluzione**, selezionare **x86, computer locale**.

3.  Nel **configurazione della soluzione** selezionate **Debug**.

    > Per il Microsoft HoloLens, può risultare più semplice impostare questa opzione su *computer remoto*, in modo che non Windows con tethering al computer in uso. Tuttavia, è necessario inoltre eseguire le operazioni seguenti:
    > - Conoscere il **indirizzo IP** di HoloLens, il che può trovarsi all'interno di *Impostazioni > rete e Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo è consigliabile usare. 
    > - Assicurarsi **modalità sviluppatore** viene **sul**; è stata trovata nel *Impostazioni > aggiornamento e sicurezza > per gli sviluppatori*.

    ![distribuire soluzioni](images/AzureLabs-Lab5-55.png)

4.  Andare alla **compilare** dal menu e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.

5.  L'App deve ora visualizzato nell'elenco delle App installate, pronta essere avviato e testati!

## <a name="your-finished-azure-functions-and-storage-application"></a>Le funzioni di Azure e applicazione di archiviazione completata

Complimenti, è stata compilata un'app per realtà mista che si avvale di servizi di archiviazione di Azure sia funzioni di Azure. L'app sarà in grado di ricavare sui dati archiviati e fornire un'azione basata su tali dati.

![versione finale del prodotto-fine](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Creare una seconda generazione record il cui generare un oggetto è stato creato da punto e punto. Quando si carica il file di dati, riprodurre le forme a cui viene generate dal percorso di che sono state create in origine.

### <a name="exercise-2"></a>Esercizio 2

Creare un modo per riavviare l'app, anziché dover aprirlo nuovamente ogni volta. **Il caricamento in background** è il luogo ideale per iniziare. Dopo questa operazione, creare un modo per cancellare l'elenco archiviato in *archiviazione di Azure*, in modo che possono essere reimpostata facilmente dall'app. 
