---
title: MR e Azure 305-funzioni e archiviazione
description: Completare questo corso per apprendere come implementare archiviazione e funzioni di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, funzioni, archiviazione, hololens, immersiva, VR
ms.openlocfilehash: 79c276d45163465c9921d02343d41d52d5f094e7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437983"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR e Azure 305: funzioni e archiviazione

![prodotto finale-inizio](images/AzureLabs-Lab5-00.png)

In questo corso si apprenderà come creare e usare funzioni di Azure e come archiviare i dati con una risorsa di archiviazione di Azure, all'interno di un'applicazione di realtà mista.

*Funzioni di Azure* è un servizio Microsoft che consente agli sviluppatori di eseguire piccole porzioni di codice, "funzioni", in Azure. Questo consente di delegare il lavoro al cloud, anziché l'applicazione locale, che può avere molti vantaggi. *Funzioni di Azure* supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, node. js, Java e php. Per altre informazioni, vedere l' [articolo funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).

*Archiviazione di Azure* è un servizio cloud Microsoft che consente agli sviluppatori di archiviare i dati, con l'assicurazione che saranno a disponibilità elevata, protezione, durabilità, scalabilità e ridondanza. Ciò significa che Microsoft gestirà tutta la manutenzione e i problemi critici. Per altre informazioni, vedere l' [articolo archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Dopo aver completato questo corso, si disporrà di un'applicazione con un auricolare immersiva a realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  Consente all'utente di guardare una scena.
2.  Attiva la generazione di oggetti quando l'utente guarda un "pulsante" 3D.
3.  Gli oggetti generati verranno scelti da una funzione di Azure.
4.  Quando viene generato ogni oggetto, l'applicazione archivia il tipo di oggetto in un *file di Azure*, che si trova in *archiviazione di Azure*.
5.  Al caricamento di una seconda volta, i dati dei *file di Azure* verranno recuperati e usati per riprodurre le azioni di generazione dall'istanza precedente dell'applicazione.

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>MR e Azure 305: funzioni e archiviazione</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens.

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
- Una sottoscrizione di un account Azure per la creazione di risorse di Azure
- Accesso a Internet per l'installazione di Azure e il recupero dei dati

## <a name="before-you-start"></a>Prima di iniziare

Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1-portale di Azure

Per usare il **servizio di archiviazione di Azure**, è necessario creare e configurare un **account di archiviazione** nell'portale di Azure.

1.  Accedere al portale di [Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *account di archiviazione*e premere **invio**.

    ![ricerca di archiviazione di Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

3.  La nuova pagina fornirà una descrizione del servizio *account di archiviazione di Azure* . Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![Crea servizio](images/AzureLabs-Lab5-02.png)

4.  Una volta fatto clic su **Crea**:

    1.  Inserire un *nome* per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.

    2.  Per *modello di distribuzione*selezionare **Resource Manager**.

    3.  Per *tipo di account*selezionare **archiviazione (utilizzo generico V1)** .

    4.  Determinare il *percorso* del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

    5.  Per la *replica* selezionare **l'archiviazione con ridondanza geografica e accesso in lettura (RA-GRS)** .

    6.  Per *prestazioni*, selezionare **standard**.

    7.  Lasciare il *trasferimento sicuro necessario* come **disabilitato**.

    8.  Selezionare una *sottoscrizione*.

    9. Scegliere un *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune). 

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.

    11. Seleziona **Crea**.

        ![informazioni sul servizio di input](images/AzureLabs-Lab5-03.png)

5.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![nuova notifica nel portale di Azure](images/AzureLabs-Lab5-04.png)

7.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![Vai alla risorsa](images/AzureLabs-Lab5-05.png)

8.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio dell' *account di archiviazione* .

    ![tasti di scelta](images/AzureLabs-Lab5-06.png)

9.  Fare clic su *chiavi di accesso*per visualizzare gli endpoint per il servizio cloud. Usare *blocco note* o simile per copiare una delle chiavi da usare in un secondo momento. Prendere nota anche del valore della *stringa di connessione* , che verrà usato nella classe *Servizi* , che verrà creata in un secondo momento.

    ![copia stringa di connessione](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capitolo 2-configurazione di una funzione di Azure

Verrà ora scritta una **funzione** di **Azure** nel servizio di Azure.

È possibile usare una **funzione di Azure** per eseguire quasi tutte le operazioni eseguite con una funzione classica nel codice. la differenza è che questa funzione è accessibile da qualsiasi applicazione con credenziali per accedere all'account di Azure.

Per creare una funzione di Azure:

1.  Dal *portale di Azure*fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *app per le funzioni*e premere **invio**.

    ![Crea app per le funzioni](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

2.  La nuova pagina fornirà una descrizione del servizio *app per le funzioni di Azure* . Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![informazioni sull'app per le funzioni](images/AzureLabs-Lab5-09.png)

3.  Una volta fatto clic su **Crea**:

    1.  Specificare un *nome*per l'app. Qui è possibile usare solo lettere e numeri (maiuscole o minuscole).

    2.  Selezionare la *sottoscrizione*preferita.

    3. Scegliere un *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune). 

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Per questo esercizio, selezionare *Windows* come **sistema operativo**scelto.

    5.  Selezionare il *piano a consumo* per il piano di **hosting**.

    6.  Determinare il *percorso* del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche. Per prestazioni ottimali, selezionare la stessa area dell'account di archiviazione.

    7.  Per *archiviazione*, selezionare **Usa esistente**e quindi usare il menu a discesa per individuare l'archiviazione creata in precedenza.

    8.  Uscire da *Application Insights* per questo esercizio.

        ![dettagli dell'app per le funzioni di input](images/AzureLabs-Lab5-10.png)

4.  Fare clic sul pulsante **Crea**.

5.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![notifica del nuovo portale di Azure](images/AzureLabs-Lab5-11.png)

7.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio. 

    ![passa all'app per le funzioni delle risorse](images/AzureLabs-Lab5-12.png)

8.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio *app per le funzioni* .

9.  Nel dashboard *app per le funzioni* , posizionare il puntatore del mouse sulle *funzioni*, disponibili all'interno del pannello a sinistra, quindi fare clic sul simbolo **+ (segno più)** .

    ![Crea nuova funzione](images/AzureLabs-Lab5-13.png)

10. Nella pagina successiva assicurarsi che **webhook** e l'API siano selezionati e per *scegliere una lingua* Selezionare **CSharp**, in quanto si tratta della lingua usata per questa esercitazione. Infine, fare clic sul pulsante **Crea funzione** .

    ![Seleziona CSharp Web Hook](images/AzureLabs-Lab5-14.png)

11. È necessario passare alla tabella codici (Run. CSX), se non è possibile fare clic sulla funzione appena creata nell'elenco funzioni all'interno del pannello a sinistra.

    ![Apri nuova funzione](images/AzureLabs-Lab5-15.png)

12. Copiare il codice seguente nella funzione. Questa funzione restituirà semplicemente un intero casuale compreso tra 0 e 2 quando viene chiamato. Non preoccuparti del codice esistente, è possibile incollarlo nella parte superiore.

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

13. Seleziona **Salva**.

14. Il risultato dovrebbe essere simile all'immagine seguente.

15. Fare clic su **Ottieni URL funzione** e prendere nota dell' *endpoint* visualizzato. Sarà necessario inserirlo nella classe *Servizi* che verrà creata più avanti in questo corso.

    ![Ottieni endpoint funzione](images/AzureLabs-Lab5-16.png)

    ![Ottieni endpoint funzione](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capitolo 3-configurazione del progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.

Configurare e testare l'auricolare immersiva della realtà mista.

> [!NOTE]
> **Non** sarà necessario alcun controller di movimento per questo corso. Se è necessario supporto per la configurazione dell'auricolare immersivo, [vedere l'articolo relativo alla configurazione della realtà mista](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Aprire Unity e fare clic su **New**.

    ![Crea nuovo progetto Unity](images/AzureLabs-Lab5-17.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity. Inserire **MR_Azure_Functions**. Verificare che il tipo di progetto sia impostato su **3D**. Impostare il *percorso* su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![assegnare un nome al nuovo progetto Unity](images/AzureLabs-Lab5-18.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **modifica** **Preferenze** > e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![imposta Visual Studio come editor di script](images/AzureLabs-Lab5-19.png)

4.  Passare quindi a **File** > **impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .

    ![passa alla piattaforma UWP](images/AzureLabs-Lab5-20.png)

5.  Passare a **File** > **impostazioni di compilazione** e verificare che:

    1. Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**.

        > Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.

    2. Il **tipo di compilazione** è impostato su **D3D**

    3. **SDK** è impostato sull' **ultima versione installata**

    4. La **versione di Visual Studio** è impostata su **installazione più recente**

    5. **Compilazione ed esecuzione** è impostato su **computer locale**

    6. Salvare la scena e aggiungerla alla compilazione.

        1.  A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.

            ![Aggiungi scene aperte](images/AzureLabs-Lab5-21.png)

        2.  Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.

            ![cartella crea scene](images/AzureLabs-Lab5-22.png)

        3.  Aprire la cartella **Scenes** appena creata e quindi nel campo **nome file:** testo digitare **FunctionsScene**e quindi fare clic su **Salva**.

            ![scena Salva funzioni](images/AzureLabs-Lab5-23.png)

6.  Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.

    ![scena Salva funzioni](images/AzureLabs-Lab5-24.png)

7.  Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .

    ![impostazioni del lettore in Inspector](images/AzureLabs-Lab5-25.png)

8.  In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **altre impostazioni** :

        1.  La **versione di runtime di scripting** deve essere **sperimentale** (equivalente a .NET 4,6), che attiverà la necessità di riavviare l'editor.
        2.  Il **back-end di scripting** deve essere **.NET**
        3.  Il **livello di compatibilità API** deve essere **.NET 4,6**

    2.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:
        
        -  **InternetClient**

            ![impostare le funzionalità](images/AzureLabs-Lab5-26.png)

    3.  Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![impostare le impostazioni di XR](images/AzureLabs-Lab5-27.png)

9.  Nelle *impostazioni di compilazione* *i C# progetti Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo.

    ![Seleziona progetti c#](images/AzureLabs-Lab5-28.png)

10.  Chiudere la finestra impostazioni di compilazione.

11. Salvare la scena e il progetto (**file** > **Salva scena/file** > **Salva progetto**).

## <a name="chapter-4---setup-main-camera"></a>Capitolo 4-installazione della fotocamera principale

> [!IMPORTANT]
> Se si vuole ignorare i componenti di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile [scaricare questo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo nel progetto come [pacchetto personalizzato](https://docs.unity3d.com/Manual/AssetPackages.html). Questo conterrà anche le dll del capitolo successivo. Dopo l'importazione, continuare con il [capitolo 7](#chapter-7---create-the-azureservices-class). 

1.  Nel *Pannello gerarchia*è presente un oggetto denominato **Main camera**, che rappresenta il punto di visualizzazione "Head" dopo che l'applicazione è stata "interna".

2.  Con il dashboard Unity in primo piano, selezionare la **fotocamera principale GameObject**. Si noterà che il *pannello Inspector* , disponibile in genere a destra, all'interno del dashboard, visualizzerà i vari componenti di tale *GameObject*, con la *trasformazione* nella parte superiore, seguita dalla *fotocamera*e da altri componenti. Sarà necessario reimpostare la trasformazione della fotocamera principale, in modo che venga posizionata correttamente.

3.  A tale scopo, selezionare l'icona dell' **ingranaggio** accanto al componente *trasformazione* della fotocamera e selezionare **Reimposta**.

    ![Reimposta trasformazione](images/AzureLabs-Lab5-29.png)

4.  Aggiornare quindi il componente **Transform** in modo simile al seguente:

    |         |    TRASFORMAZIONE-POSIZIONE   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRASFORMAZIONE-ROTAZIONE |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRASFORMAZIONE-RIDIMENSIONA |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![imposta trasformazione fotocamera](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capitolo 5-configurazione della scena Unity

1.  Fare clic con il pulsante destro del mouse in un'area vuota del *Pannello gerarchia*, sotto **oggetto 3D**, Aggiungi un **piano**.

    ![Crea nuovo piano](images/AzureLabs-Lab5-31.png)

2.  Con l'oggetto **piano** selezionato, modificare i parametri seguenti nel *Pannello di controllo*:

    |       | TRASFORMAZIONE-POSIZIONE |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRASFORMAZIONE-RIDIMENSIONA |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![Imposta posizione e scala del piano](images/AzureLabs-Lab5-32.png)

    ![visualizzazione scena del piano](images/AzureLabs-Lab5-33.png)

3.  Fare clic con il pulsante destro del mouse in un'area vuota del *Pannello gerarchia*, sotto **oggetto 3D**, Aggiungi un **cubo**.

    1.  Rinominare il cubo in **GazeButton** (con il cubo selezionato, premere ' F2').

    2.  Modificare i parametri seguenti nel *Pannello di controllo*:

        |       | TRASFORMAZIONE-POSIZIONE |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![imposta la trasformazione del pulsante di sguardo](images/AzureLabs-Lab5-34.png)

        ![visualizzazione della scena del pulsante Guarda](images/AzureLabs-Lab5-35.png)

    3.  Fare clic sul pulsante a discesa **tag** e fare clic su **Aggiungi tag** per aprire il *riquadro Tag & livelli*.

        ![Aggiungi nuovo tag](images/AzureLabs-Lab5-36.png)

        ![Seleziona più](images/AzureLabs-Lab5-37.png)

    4.  Selezionare il pulsante **+ (segno più)** e nel campo *nuovo nome tag* immettere **GazeButton**e quindi fare clic su **Salva**.

        ![nome nuovo tag](images/AzureLabs-Lab5-38.png)

    5.  Fare clic sull'oggetto **GazeButton** nel *Pannello gerarchia*e nel *pannello Inspector*assegnare il tag **GazeButton** appena creato.

        ![pulsante assegna sguardo al nuovo tag](images/AzureLabs-Lab5-39.png)

4.  Fare clic con il pulsante destro del mouse sull'oggetto **GazeButton** , nel *Pannello gerarchia*e aggiungere un **GameObject vuoto** (che verrà aggiunto come oggetto *figlio* ).

5.  Selezionare il nuovo oggetto e rinominarlo **ShapeSpawnPoint**.

    1.  Modificare i parametri seguenti nel *Pannello di controllo*:

        |       | TRASFORMAZIONE-POSIZIONE |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![Aggiorna trasformazione punto di generazione forma](images/AzureLabs-Lab5-40.png)

        ![visualizzazione scena punto di generazione forma](images/AzureLabs-Lab5-41.png)

6.  Successivamente verrà creato un oggetto **testo 3D** per fornire commenti e suggerimenti sullo stato del servizio di Azure.

    Fare di nuovo clic con il pulsante destro del mouse su **GazeButton** nel pannello gerarchia e aggiungere un **oggetto 3D** > oggetto **testo 3D** come *elemento figlio*.

    ![Crea nuovo oggetto testo 3D](images/AzureLabs-Lab5-42.png)

7.  Rinominare l'oggetto **testo 3D** in **AzureStatusText**.

8.  Modificare la trasformazione dell'oggetto **AzureStatusText** nel modo seguente:

    |       | TRASFORMAZIONE-POSIZIONE |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0,6  |

    |       | TRASFORMAZIONE-RIDIMENSIONA |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0,1   | 0,1               | 0,1   |


    > [!NOTE]
    > Non preoccuparti se sembra essere fuori sede, perché verrà corretto quando il componente mesh del testo seguente viene aggiornato.

9.  Modificare il componente **mesh di testo** in modo che corrisponda a quanto segue:

    ![imposta componente mesh testo](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > Il colore selezionato è il colore esadecimale: **000000FF**, sebbene sia possibile sceglierne un altro, è sufficiente assicurarsi che sia leggibile.

10. La struttura del pannello della gerarchia dovrebbe ora essere simile alla seguente:

    ![mesh di testo in visualizzazione scena](images/AzureLabs-Lab5-43b.png)

10. La scena dovrebbe ora essere simile alla seguente:

    ![mesh di testo in visualizzazione scena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capitolo 6: importare archiviazione di Azure per Unity

Si utilizzerà archiviazione di Azure per Unity (che a sua volta USA .NET SDK per Azure). Per altre informazioni, vedere l' [articolo archiviazione di Azure per Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare l'SDK nel progetto, assicurarsi di aver scaricato la versione più recente [di ". file unitypackage Tools" da GitHub](https://aka.ms/azstorage-unitysdk). Eseguire quindi le operazioni seguenti:

1.  Aggiungere il file con **estensione file unitypackage Tools** a Unity usando l'opzione di menu **Asset** > **Importa pacchetto** > **pacchetto personalizzato** .

2.  Nella casella **Importa pacchetto Unity** visualizzata è possibile selezionare tutti gli elementi in **plug** -in > **archiviazione**. Deselezionare tutti gli altri elementi, perché non sono necessari per questo corso.

    ![Importa nel pacchetto](images/AzureLabs-Lab5-45.png)

3.  Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.

4.  Passare alla cartella *archiviazione* in *plug*-in, nella visualizzazione del progetto e selezionare *solo*i plug-in seguenti:

    -   Microsoft. Data. Edm
    -   Microsoft. Data. OData
    -   Microsoft. WindowsAzure. storage
    -   Newtonsoft. JSON
    -   System. Spatial

        ![deseleziona qualsiasi piattaforma](images/AzureLabs-Lab5-46.png)

5.  Con *questi plug* -in specifici selezionati, **deselezionare** *qualsiasi piattaforma* e **deselezionare** *WSAPlayer* , quindi fare clic su **applica**.

    ![applica dll della piattaforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Questi specifici plug-in vengono contrassegnati per essere usati solo nell'editor di Unity. Questo è dovuto al fatto che esistono versioni diverse degli stessi plug-in nella cartella WSA che verranno usate dopo l'esportazione del progetto da Unity.

6.  Nella cartella plugin di *archiviazione* selezionare solo:

    -   Microsoft. Data. Services. client

        ![impostazione non elabora per le dll](images/AzureLabs-Lab5-48.png)

7.  Selezionare la casella **non elaborare** in *Impostazioni piattaforma* e fare clic su **applica**.

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Si sta contrassegnando questo plug-in "non elaborare" perché il plug-in assembly Unity ha difficoltà nell'elaborare questo plug-in. Il plug-in continuerà a funzionare anche se non viene elaborato.

## <a name="chapter-7---create-the-azureservices-class"></a>Capitolo 7: creare la classe servizi

La prima classe che si intende creare è la classe *Servizi* .

La classe *Servizi* sarà responsabile di:

-   Archiviazione delle credenziali dell'account Azure.

-   Chiamata della funzione app Azure.

-   Caricare e scaricare il file di dati nella risorsa di archiviazione cloud di Azure.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella *Asset* , che si trova nel pannello del progetto, **creare** > **cartella**. Denominare gli **script**della cartella.

    ![Crea nuova cartella](images/AzureLabs-Lab5-50.png)

    ![cartella di chiamata-script](images/AzureLabs-Lab5-51.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla.

3.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi **creare** >  **C# script**. Chiamare lo script *Servizi*.

4.  Fare doppio clic sulla nuova classe *Servizi* per aprirla con *Visual Studio*.

5.  Aggiungere gli spazi dei nomi seguenti all'inizio di *Servizi*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Aggiungere i campi Inspector seguenti all'interno della classe *Servizi* :

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

7.  Aggiungere quindi le variabili membro seguenti all'interno della classe *Servizi* :

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
    > Assicurarsi di sostituire i valori della *stringa di connessione* e dell' *endpoint* con i valori di archiviazione di Azure, disponibili nel portale di Azure

8.  È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* . Questi metodi verranno chiamati quando la classe inizializza:

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
    > Il codice per *CallAzureFunctionForNextShape ()* viene compilato in un [capitolo futuro](#chapter-10---completing-the-azureservices-class).

9.  Eliminare il metodo *Update ()* perché non verrà utilizzato da questa classe.

10. Salvare le modifiche in Visual Studio e quindi tornare a Unity.

11. Fare clic e trascinare la classe *Servizi* dalla cartella Scripts all'oggetto principale della fotocamera nel *Pannello gerarchia*.

12. Selezionare la fotocamera principale, quindi estrarre l'oggetto figlio **AzureStatusText** dall'oggetto **GazeButton** e inserirlo nel campo destinazione riferimento **AzureStatusText** , nel *controllo*, per fornire il riferimento al  *Script Servizi* .

    ![assegnare la destinazione di riferimento del testo di stato di Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capitolo 8: creare la classe ShapeFactory

Lo script successivo da creare è la classe *ShapeFactory* . Il ruolo di questa classe è creare una nuova forma, quando richiesto, e conservarne una cronologia delle forme create in un *elenco della cronologia delle forme*. Ogni volta che viene creata una forma, l' *elenco della cronologia delle forme* viene aggiornato nella classe *AzureService* e quindi archiviato in *archiviazione di Azure*. All'avvio dell'applicazione, se viene trovato un file archiviato in *archiviazione di Azure*, l' *elenco della cronologia delle forme* viene recuperato e riprodotto, con l'oggetto **testo 3D** che indica se la forma generata è di archiviazione o una nuova.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi **creare** >  **C# script**. Chiamare lo script *ShapeFactory*.

3.  Fare doppio clic sul nuovo script *ShapeFactory* per aprirlo con *Visual Studio*.

4.  Verificare che la classe *ShapeFactory* includa gli spazi dei nomi seguenti:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Aggiungere le variabili illustrate di seguito alla classe *ShapeFactory* e sostituire le funzioni *Start ()* e *svegli ()* con quelle riportate di seguito:

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

6.  Il metodo *createShape ()* genera le forme primitive, in base al parametro *Integer* fornito. Il parametro booleano viene usato per specificare se la forma attualmente creata è di archiviazione o nuova. Inserire il codice seguente nella classe *ShapeFactory* , sotto i metodi precedenti:

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

8.  Nell'editor di Unity fare clic e trascinare la classe *ShapeFactory* dalla cartella **Scripts** all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.

9. Con la fotocamera principale selezionata, si noterà che nel componente di script *ShapeFactory* manca il riferimento al *punto di generazione* . Per risolvere il problema, trascinare l'oggetto **ShapeSpawnPoint** dal *Pannello gerarchia* alla destinazione di riferimento del **punto di generazione** .

    ![imposta la destinazione del riferimento alla Factory della forma](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capitolo 9: creare la classe sguardi

L'ultimo script che è necessario creare è la classe *sguardi* .

Questa classe è responsabile della creazione di un **Raycast** che verrà proiettato in futuro dalla fotocamera principale, per individuare l'oggetto analizzato dall'utente. In questo caso, Raycast dovrà identificare se l'utente sta esaminando l'oggetto **GazeButton** nella scena e attivare un comportamento.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro del mouse sul pannello del progetto, quindi **creare** >  **C# script**. Chiamare lo *sguardo*dello script.

3.  Fare doppio clic *sul nuovo script* per aprirlo con *Visual Studio.*

4.  Verificare che nella parte superiore dello script sia incluso lo spazio dei nomi seguente:

    ```csharp
        using UnityEngine;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe *sguardi* :

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
> Alcune di queste variabili possono essere modificate nell' *Editor*.

6.  È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* .

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

7.  Aggiungere il codice seguente, in cui verrà creato un oggetto cursore all'inizio, insieme al metodo *Update ()* , che eseguirà il metodo Raycast, insieme alla posizione in cui viene attivato il valore booleano GazeEnabled:

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

8. Aggiungere quindi il metodo *UpdateRaycast ()* che proietta un Raycast e rileva la destinazione dell'hit.

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

9. Infine, aggiungere il metodo *ResetFocusedObject ()* , che consente di impostare il colore corrente per gli oggetti GazeButton, che indica se sta creando una nuova forma.

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

11.  Fare clic e trascinare la classe *sguardi* dalla cartella Scripts all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Capitolo 10-completamento della classe servizi

Con gli altri script sul posto, è ora possibile *completare* la classe *Servizi* . Questa operazione verrà eseguita tramite:

1.  Aggiunta di un nuovo metodo denominato *CreateCloudIdentityAsync ()* per configurare le variabili di autenticazione necessarie per la comunicazione con Azure.

    > Questo metodo verificherà anche l'esistenza di un file archiviato in precedenza contenente l'elenco di forme.
    >
    > **Se il file viene trovato**, lo *sguardo*dell'utente viene disabilitato e viene attivata la creazione della forma, in base al modello di forme, come archiviato nel **file di archiviazione di Azure**. L'utente può visualizzarlo, perché la **mesh di testo** fornirà la visualizzazione ' storage ' o ' New ', a seconda delle forme Origin.
    >
    > **Se non viene trovato alcun file**, verrà abilitato lo *sguardo*, consentendo all'utente di creare forme quando si esamina l'oggetto **GazeButton** nella scena.

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

2.  Il frammento di codice successivo si trova all'interno del metodo *Start ()* ; dove verrà effettuata una chiamata al metodo *CreateCloudIdentityAsync ()* . È possibile copiare il metodo *Start ()* corrente con il seguente:

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

3.  Compilare il codice per il metodo *CallAzureFunctionForNextShape ()* . Si userà la *app per le funzioni di Azure* creata in precedenza per richiedere un indice delle forme. Una volta ricevuta la nuova forma, questo metodo invierà la forma alla classe *ShapeFactory* per creare la nuova forma nella scena. Usare il codice seguente per completare il corpo di *CallAzureFunctionForNextShape ()* .

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

4.  Aggiungere un metodo per creare una stringa concatenando gli Integer archiviati nell'elenco della cronologia delle forme e salvarli nel *file di archiviazione di Azure*.

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

5.  Aggiungere un metodo per recuperare il testo archiviato nel file che si trova nel *file di archiviazione di Azure* e *deserializzarlo* in un elenco.

6.  Una volta completato il processo, il metodo abilita nuovamente lo sguardo in modo che l'utente possa aggiungere altre forme alla scena.

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

## <a name="chapter-11---build-the-uwp-solution"></a>Capitolo 11: compilare la soluzione UWP

Per avviare il processo di compilazione:

1.  Passare a **File** > **impostazioni di compilazione**.

    ![compilare l'app](images/AzureLabs-Lab5-54.png)

2.  Fai clic su **Compila**. Unity avvierà una finestra di *Esplora file* , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella adesso e denominarla *app*. Quindi, con la cartella dell' *app* selezionata, fare clic su **Seleziona cartella**.

3.  Unity inizierà a compilare il progetto nella cartella dell' *app* .

4.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra *Esplora file* nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).

## <a name="chapter-12---deploying-your-application"></a>Capitolo 12-distribuzione dell'applicazione

Per distribuire l'applicazione:

1.  Passare alla cartella dell' *app* creata nell' [ultimo capitolo](#chapter-11---build-the-uwp-solution). Verrà visualizzato un file con il nome delle app, con l'estensione ' sln ', che è necessario fare doppio clic, per aprirlo in *Visual Studio*.

2.  Nella **piattaforma soluzione**selezionare **x86, computer locale**.

3.  Nella **configurazione della soluzione** selezionare **debug**.

    > Per Microsoft HoloLens, può risultare più semplice impostare questa impostazione su *computer remoto*, in modo da non essere collegati al computer. Tuttavia, sarà necessario eseguire anche le operazioni seguenti:
    > - Conosce l' **indirizzo IP** del HoloLens, disponibile all'interno delle **impostazioni** > **rete & Internet** > **Wi-Fi** > **Opzioni avanzate**; IPv4 è l'indirizzo da usare. 
    > - Verificare che la **modalità sviluppatore** sia **attiva**; disponibile in **impostazioni** > **Aggiorna &**  > **di sicurezza per gli sviluppatori**.

    ![Distribuisci soluzione](images/AzureLabs-Lab5-55.png)

4.  Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.

5.  L'app verrà visualizzata nell'elenco delle app installate, pronta per essere avviata e testata.

## <a name="your-finished-azure-functions-and-storage-application"></a>Le funzioni di Azure e l'applicazione di archiviazione completate

Congratulazioni, è stata creata un'app per realtà mista che sfrutta sia le funzioni di Azure che i servizi di archiviazione di Azure. L'app sarà in grado di creare dati archiviati e fornirà un'azione in base a tali dati.

![fine prodotto finale](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Creare un secondo punto di spawn e registrare il punto di generazione da cui è stato creato un oggetto. Quando si carica il file di dati, riprodurre le forme generate dalla posizione in cui sono state create originariamente.

### <a name="exercise-2"></a>Esercizio 2

Creare un modo per riavviare l'app, anziché riaprirla ogni volta. Il **caricamento di scene** è un punto di partenza valido. Al termine di questa operazione, creare un modo per cancellare l'elenco Archiviato in *archiviazione di Azure*, in modo che possa essere facilmente reimpostato dall'app. 
