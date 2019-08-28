---
title: MR e Azure 310-rilevamento di oggetti
description: Completare questo corso per apprendere come eseguire il training di un modello di apprendimento automatico e quindi usare il modello sottoposto a training per riconoscere oggetti simili e la relativa posizione nel mondo reale dall'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, visione personalizzata, rilevamento di oggetti, realtà mista, Accademia, Unity, esercitazione, API, hololens
ms.openlocfilehash: 71370db84a9b90b017e8d5fac0799a862883d046
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047223"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

# <a name="mr-and-azure-310-object-detection"></a>Mr e Azure 310: Rilevamento oggetti

In questo corso si apprenderà come riconoscere il contenuto visivo personalizzato e la relativa posizione spaziale all'interno di un'immagine fornita, usando le funzionalità di Azure Visione personalizzata "rilevamento oggetti" in un'applicazione di realtà mista.

Questo servizio consentirà di eseguire il training di un modello di apprendimento automatico usando immagini oggetto. Si userà quindi il modello sottoposto a training per riconoscere oggetti simili e approssimarne la posizione nel mondo reale, come fornito dall'acquisizione della fotocamera di Microsoft HoloLens o da una fotocamera che si connette a un PC per auricolari immersivi (VR).

![risultato del corso](images/AzureLabs-Lab310-00.png)

**Azure visione personalizzata, rilevamento oggetti** è un servizio Microsoft che consente agli sviluppatori di creare classificatori di immagini personalizzate. Questi classificatori possono quindi essere utilizzati con nuove immagini per rilevare gli oggetti all'interno di tale nuova immagine, fornendo **limiti di box** all'interno dell'immagine stessa. Il servizio fornisce un portale online semplice e facile da usare per semplificare questo processo. Per ulteriori informazioni, visitare i collegamenti seguenti:

* [Pagina Visione personalizzata di Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Limiti e quote](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Al termine di questo corso, sarà disponibile un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1. L'utente sarà in grado di osservare un oggetto, di cui è stato eseguito il training tramite il servizio visione artificiale personalizzato di Azure e il rilevamento degli oggetti. 
2. L'utente userà il gesto *Tap* per acquisire un'immagine di ciò che sta esaminando.
3. L'app invierà l'immagine alla Servizio visione artificiale personalizzato di Azure.
4. Verrà restituita una risposta dal servizio che visualizzerà il risultato del riconoscimento come testo dello spazio globale. Questa operazione viene eseguita tramite l'uso del rilevamento spaziale di Microsoft HoloLens, per comprendere la posizione globale dell'oggetto riconosciuto e quindi usare il *tag* associato a quello rilevato nell'immagine, per fornire il testo dell'etichetta.

Il corso illustra anche il caricamento manuale delle immagini, la creazione di tag e il training del servizio per riconoscere oggetti diversi (nell'esempio specificato, una Coppa), impostando la *casella limite* all'interno dell'immagine inviata. 

> [!IMPORTANT]
> Dopo la creazione e l'uso dell'app, lo sviluppatore deve tornare al Servizio visione artificiale personalizzato di Azure e identificare le stime effettuate dal servizio e determinare se sono corrette o meno (tramite l'assegnazione di tag a qualsiasi elemento del servizio e regolazione dei *rettangoli*di delimitazione). Il servizio può quindi essere nuovamente sottoposto a training, che aumenterà la probabilità che riconosca gli oggetti reali.

Questo corso spiegherà come ottenere i risultati dal Servizio visione artificiale personalizzato di Azure, il rilevamento degli oggetti, in un'applicazione di esempio basata su Unity. Sarà necessario applicare questi concetti a un'applicazione personalizzata che è possibile creare.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 310: Rilevamento oggetti</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018). È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Windows 10 SDK più recente](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017,4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) con la modalità di sviluppo abilitata
- Accesso a Internet per il programma di installazione di Azure e il recupero Servizio visione artificiale personalizzato
-  È necessaria una serie di almeno quindici (15) immagini) per ogni oggetto che si desidera venga riconosciuto dal Visione personalizzata. Se lo si desidera, è possibile utilizzare le immagini già disponibili in questo corso, [una serie di CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip).

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente. 

Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Capitolo 1-portale di Visione personalizzata

Per usare il **servizio visione artificiale personalizzato di Azure**, è necessario configurare un'istanza di tale istanza per renderla disponibile per l'applicazione.

1.  Passare [alla pagina principale **servizio visione artificiale personalizzato** ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Fare clic su **Introduzione**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Accedere al portale di Visione personalizzata.

    ![](images/AzureLabs-Lab310-02.png)

4.  Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

5.  Una volta effettuato l'accesso per la prima volta, verrà visualizzato il pannello *condizioni del servizio* . Fare clic sulla casella di controllo per *accettare le condizioni*. Quindi fareclic su Accetto.

    ![](images/AzureLabs-Lab310-03.png)

6.  Accettando le condizioni, si è ora nella sezione *progetti personali* . Fare clic su **nuovo progetto**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Verrà visualizzata una scheda sul lato destro, che richiederà di specificare alcuni campi per il progetto.

    1.  Inserire un nome per il progetto

    2.  Inserire una descrizione per il progetto (**facoltativo**)

    3.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Per [altre informazioni sui gruppi di risorse di Azure, passare alla documentazione associata](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  Impostare i **tipi di progetto** come **rilevamento oggetti (anteprima)** .

8.  Al termine, fare clic su **Crea progetto**e si verrà reindirizzati alla pagina servizio visione artificiale personalizzato progetto.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capitolo 2-training del progetto di Visione personalizzata

Una volta nel portale di Visione personalizzata, l'obiettivo principale è quello di eseguire il training del progetto per riconoscere oggetti specifici nelle immagini.

Sono necessarie almeno 15 immagini per ogni oggetto che si desidera che l'applicazione riconosca. È possibile usare le immagini fornite con questo corso ([una serie di CUPS](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Per eseguire il training del progetto Visione personalizzata:

1.  Fare clic sul **+** pulsante accanto ai **tag**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Aggiungere un **nome** per il tag che verrà usato per associare le immagini a. In questo esempio vengono utilizzate immagini di CUPS per il riconoscimento, quindi è stato denominato il tag per questo, **Cup**. Al termine, fare clic su **Salva** .

    ![](images/AzureLabs-Lab310-07.png)

3.  Si noterà che il **tag** è stato aggiunto. potrebbe essere necessario ricaricare la pagina affinché venga visualizzata. 

    ![](images/AzureLabs-Lab310-08.png)

4.  Fare clic su **Aggiungi immagini** al centro della pagina.

    ![](images/AzureLabs-Lab310-09.png)

5.  Fare clic su **Sfoglia file locali**e selezionare le immagini che si desidera caricare per un oggetto, con un minimo di quindici (15).

    > [!TIP]
    >  È possibile selezionare più immagini alla volta per caricare.

    ![](images/AzureLabs-Lab310-10.png)

6.  Quando si selezionano tutte le immagini con cui si vuole eseguire il training del progetto, fare clic su **Carica file** . Il caricamento dei file inizierà. Dopo aver conferma del caricamento, fare **clic** su

    ![](images/AzureLabs-Lab310-11.png)

7.  A questo punto le immagini vengono caricate, ma non contrassegnate.

    ![](images/AzureLabs-Lab310-12.png)

8.  Per contrassegnare le immagini, usare il mouse. Quando si passa il mouse sull'immagine, un'evidenziazione della selezione consente di disegnare automaticamente una selezione intorno all'oggetto. Se non è accurato, è possibile creare un proprio. Questa operazione viene eseguita tenendo premuto il pulsante sinistro del mouse e trascinando l'area di selezione per includere l'oggetto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Dopo la selezione dell'oggetto all'interno dell'immagine, verrà richiesto di *aggiungere un tag Region*. Selezionare il tag creato in precedenza (' Cup ' nell'esempio precedente) oppure, se si aggiungono altri tag, digitarlo in e fare clic sul pulsante **+ (segno più)** .

    ![](images/AzureLabs-Lab310-14.png) 

10. Per contrassegnare l'immagine successiva, è possibile fare clic sulla freccia a destra del pannello oppure chiudere il pannello Tag facendo clic sulla **X** nell'angolo superiore destro del pannello, quindi fare clic sull'immagine successiva. Una volta preparata l'immagine successiva, ripetere la stessa procedura. Eseguire questa operazione per tutte le immagini caricate fino a quando non vengono contrassegnate tutte con tag. 

    > [!NOTE]
    >  È possibile selezionare più oggetti nella stessa immagine, come nell'immagine seguente: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Una volta contrassegnati tutti, fare clic sul pulsante **con tag** , a sinistra della schermata, per visualizzare le immagini con tag. 

    ![](images/AzureLabs-Lab310-16.png)

12. A questo punto è possibile eseguire il training del servizio. Fare clic sul pulsante **Train (Train** ) per avviare la prima iterazione di training.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Una volta compilato, sarà possibile visualizzare due pulsanti denominati **Make default** and prediction **URL**. Fare clic su **Imposta come predefinito** per primo, quindi fare clic su **URL stima**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > L'endpoint fornito da questo oggetto è impostato su qualsiasi iterazione contrassegnata come predefinita. Di conseguenza, se in un secondo momento si crea una nuova iterazione e la si aggiorna come predefinita, non sarà necessario modificare il codice.

14. Dopo aver fatto clic su **URL di stima**, aprire il *blocco note*e copiare e incollare l' **URL** (detto anche endpoint di **stima**) e la chiave di **stima del servizio**, in modo da poterlo recuperare quando necessario in un secondo momento nel codice.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3: configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire **Unity** e fare clic su **New**.

    ![](images/AzureLabs-Lab310-21.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity. Inserire **CustomVisionObjDetection**. Verificare che il tipo di progetto sia impostato su **3D**e impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **modifica* > *Preferenze** e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio**. Chiudere la finestra delle **Preferenze** .

    ![](images/AzureLabs-Lab310-23.png)

4.  Passare quindi a **File > impostazioni di compilazione** e impostare la **piattaforma** su *piattaforma UWP (Universal Windows Platform)* , quindi fare clic sul pulsante **Switch Platform** .

    ![](images/AzureLabs-Lab310-24.png)

5.  Nella stessa finestra **impostazioni di compilazione** verificare che siano impostati i seguenti elementi:

    1.  Il **dispositivo di destinazione** è impostato su **HoloLens**        
    2.  Il **tipo di compilazione** è impostato su **D3D**
    3.  **SDK** è impostato sull' **ultima versione installata**
    4.  La **versione di Visual Studio** è impostata su **installazione più recente**
    5.  **Compilazione ed esecuzione** è impostato su **computer locale**            
    6.  Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.

        ![](images/AzureLabs-Lab310-25.png)

6.  Nella stessa finestra **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .

7. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **altre impostazioni** :

        1.  La **versione di runtime** di scripting deve essere **sperimentale** (equivalente a .NET 4,6), che attiverà la necessità di riavviare l'editor.

        2. Il **back-end** di scripting deve essere **.NET**.

        3. Il **livello di compatibilità API** deve essere **.NET 4,6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, quindi assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![](images/AzureLabs-Lab310-29.png)

8.  Nelle **impostazioni di compilazione**, i *progetti\# Unity C* non sono più in grigio: selezionare la casella di controllo accanto a questo.

9.  Chiudere la finestra **impostazioni di compilazione** .

10. Nell' **Editor**fare clic su **modifica** > **Impostazioni** > progetto**grafica**.

    ![](images/AzureLabs-Lab310-30.png)

11. Nel **pannello Inspector** verranno aperte le *impostazioni grafiche* . Scorrere verso il basso fino a quando non viene visualizzata una matrice denominata **Includi sempre gli shader**. Aggiungere uno slot aumentando la variabile di **dimensione** di uno (in questo esempio, è stato 8, quindi è stato creato 9). Verrà visualizzato un nuovo slot nell'ultima posizione della matrice, come illustrato di seguito:

    ![](images/AzureLabs-Lab310-31.png)

12. Nello slot fare clic sul cerchio di destinazione piccolo accanto allo slot per aprire un elenco di shader. Cercare il Legacy shaders **/Transparent/Diffusion** shader e fare doppio clic su di esso. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capitolo 4-importazione del pacchetto CustomVisionObjDetection Unity

Per questo corso viene fornito un pacchetto di asset Unity denominato **Azure-Mr-310. file unitypackage Tools**. 

> Punta Tutti gli oggetti supportati da Unity, incluse le intere scene, possono essere inseriti in un file con **estensione file unitypackage Tools** e esportati o importati in altri progetti. Si tratta del modo più sicuro e più efficiente per spostare le risorse tra diversi **progetti Unity**.

È possibile trovare il [pacchetto Azure-Mr-310 che è necessario scaricare qui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  Con il dashboard Unity, fare clic su **Asset** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto > pacchetto personalizzato**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Usare il selettore file per selezionare il pacchetto **Azure-Mr-310. file unitypackage Tools** e fare clic su **Apri**. Verrà visualizzato un elenco di componenti per questo asset. Confermare l'importazione facendo clic sul pulsante **Importa** .

    ![](images/AzureLabs-Lab310-34.png)

3.  Una volta completata l'importazione, si noterà che le cartelle del pacchetto sono state aggiunte alla cartella assets . Questo tipo di struttura di cartelle è tipico per un progetto Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  La cartella Materials contiene il materiale utilizzato dal **cursore sguardo**. 

    2.  La cartella plugins contiene la dll Newtonsoft usata dal codice per deserializzare la risposta Web del servizio. Le due (2) versioni diverse contenute nella cartella e nella sottocartella sono necessarie per consentire l'uso e la compilazione della libreria sia dall'editor di Unity che dalla compilazione UWP. 

    3.  La cartella prefabbricates contiene le prefabbricati contenute nella scena. Sono:

        1.  **GazeCursor**, il cursore utilizzato nell'applicazione. Collaborerà con la prefabbricata SpatialMapping per poter essere posizionata nella scena sopra gli oggetti fisici.
        2.  **Etichetta**, ovvero l'oggetto dell'interfaccia utente usato per visualizzare il tag oggetto nella scena quando richiesto.
        3.  **SpatialMapping**, che è l'oggetto che consente all'applicazione di usare la creazione di una mappa virtuale usando il rilevamento spaziale di Microsoft HoloLens.

    4.  La cartella **Scenes** che attualmente contiene la scena predefinita per questo corso.

4.  Aprire la cartella **Scenes** , nel **Pannello Project**e fare doppio clic su **ObjDetectionScene**per caricare la scena che verrà usata per questo corso.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Non è incluso alcun codice**, il codice verrà scritto seguendo questo corso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capitolo 5: creare la classe CustomVisionAnalyser.

A questo punto si è pronti per scrivere il codice. Si inizierà con la classe **CustomVisionAnalyser** .

> [!NOTE]
> Le chiamate al **servizio visione artificiale personalizzato**, effettuate nel codice riportato di seguito, vengono effettuate usando l' **API REST di visione personalizzata**. Con l'uso di questa API, si vedrà come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile). Tenere presente che Microsoft offre un **visione personalizzata SDK** che può essere usato anche per effettuare chiamate al servizio. Per altre informazioni, vedere l' [articolo visione personalizzata SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Questa classe è responsabile di:

- Caricamento dell'immagine più recente acquisita come matrice di byte.

- Invio della matrice di byte all'istanza di Azure **servizio visione artificiale personalizzato** per l'analisi.

- Ricezione della risposta come stringa JSON.

- Deserializzare la risposta e passare la **stima** risultante alla classe **SceneOrganiser** , che si occuperà della modalità di visualizzazione della risposta.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella **cartella Asset**, che si trova nel **pannello progetto**, quindi fare clic su **Crea** > **cartella**. Chiamare gli **script**della cartella.

    ![](images/AzureLabs-Lab310-37.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla.

3.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi scegliere **Crea** > **script C\#** . Denominare lo script **CustomVisionAnalyser.**

4.  Fare doppio clic sul nuovo script **CustomVisionAnalyser** per aprirlo con **Visual Studio.**

5.  Verificare che siano presenti gli spazi dei nomi seguenti a cui si fa riferimento all'inizio del file:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  Nella classe **CustomVisionAnalyser** aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Assicurarsi di inserire la **chiave di stima del servizio** nella variabile **PredictionKey** e l'endpoint di **stima** nella variabile **predictionEndpoint** . Questi sono stati copiati [nel blocco note in precedenza, nel capitolo 2, passaggio 14](#chapter-2---training-your-custom-vision-project).

7.  Per inizializzare la variabile di istanza, è necessario aggiungere il codice per il punto di riattivazione **()** :

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Aggiungere la coroutine (con il metodo statico **GetImageAsByteArray ()** sottostante), che otterrà i risultati dell'analisi dell'immagine, acquisita dalla classe **ImageCapture** .

    > [!NOTE]
    > Nella coroutine di **AnalyseImageCapture** è presente una chiamata alla classe **SceneOrganiser** che è ancora necessario creare. Lasciare quindi **le righe impostate come commento per il momento**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. Eliminare i metodi **Start ()** e **Update ()** perché non verranno usati. 

10.  Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.

> [!IMPORTANT]
> Come indicato in precedenza, non è necessario preoccuparsi del codice che potrebbe sembrare un errore, in quanto le altre classi saranno presto disponibili, che verranno risolte.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capitolo 6: creare la classe CustomVisionObjects

La classe che verrà creata ora è la classe **CustomVisionObjects** .

Questo script contiene una serie di oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate all'Servizio visione artificiale personalizzato.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea** > **script C\#** . Chiamare lo script **CustomVisionObjects.**

2.  Fare doppio clic sul nuovo script **CustomVisionObjects** per aprirlo con **Visual Studio.**

3.  Verificare che siano presenti gli spazi dei nomi seguenti a cui si fa riferimento all'inizio del file:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Eliminare i metodi **Start ()** e **Update ()** all'interno della classe **CustomVisionObjects** . questa classe ora dovrebbe essere vuota.

    > [!WARNING]
    > È importante seguire con attenzione l'istruzione successiva. Se si inseriscono le nuove dichiarazioni di classe all'interno della classe **CustomVisionObjects** , si otterranno errori di compilazione nel [capitolo 10](#chapter-10---create-the-imagecapture-class), indicando che **AnalysisRootObject** e **BoundingBox** non sono stati trovati.

5.  Aggiungere le classi seguenti al di *fuori* della classe **CustomVisionObjects** . Questi oggetti vengono usati dalla libreria **Newtonsoft** per serializzare e deserializzare i dati di risposta:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capitolo 7: creare la classe SpatialMapping

Questa classe imposterà il **conflitto di mapping spaziale** nella scena in modo da essere in grado di rilevare conflitti tra oggetti virtuali e oggetti reali.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea** > **script C\#** . Chiamare lo script **SpatialMapping.**

2.  Fare doppio clic sul nuovo script **SpatialMapping** per aprirlo con **Visual Studio.**

3.  Verificare che siano presenti gli spazi dei nomi seguenti a cui si fa riferimento sopra la classe **SpatialMapping** :

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno della classe **SpatialMapping** , sopra il metodo **Start ()** :

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Aggiungere i **risvegli ()** e **Start ()** :

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  Eliminare il metodo **Update ()** .

7.  Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Capitolo 8: creare la classe GazeCursor

Questa classe è responsabile della configurazione del cursore nella posizione corretta nello spazio reale, mediante l'utilizzo di **SpatialMappingCollider**, creato nel capitolo precedente.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea** > **script C\#** . Chiamare lo script **GazeCursor**

2.  Fare doppio clic sul nuovo script **GazeCursor** per aprirlo con **Visual Studio.**

3.  Verificare che sia presente lo spazio dei nomi seguente a cui si fa riferimento sopra la classe **GazeCursor** :

    ```csharp
    using UnityEngine;
    ```

4.  Aggiungere quindi la variabile seguente all'interno della classe **GazeCursor** , sopra il metodo **Start ()** . 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Aggiornare il metodo **Start ()** con il codice seguente:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Aggiornare il metodo **Update ()** con il codice seguente:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > Non preoccuparsi dell'errore per la classe **SceneOrganiser** non trovata, che verrà creata nel capitolo successivo.

7. Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capitolo 9: creare la classe SceneOrganiser

Questa classe:

-   Configurare la *fotocamera principale* collegando i componenti appropriati.

-   Quando viene rilevato un oggetto, questo sarà responsabile per il calcolo della posizione nel mondo reale e per inserire un' **etichetta tag** accanto al **nome del tag**appropriato.    

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea** > **script C\#** . Denominare lo script **SceneOrganiser**.

2.  Fare doppio clic sul nuovo script **SceneOrganiser** per aprirlo con **Visual Studio.**

3.  Verificare che siano presenti gli spazi dei nomi seguenti a cui si fa riferimento sopra la classe **SceneOrganiser** :

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno della classe **SceneOrganiser** , sopra il metodo **Start ()** :

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  Eliminare i metodi **Start ()** e **Update ()** .

6.  Sotto le variabili aggiungere il metodo **sveglie ()** che inizializza la classe e imposta la scena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Aggiungere il metodo **PlaceAnalysisLabel ()** che creerà *un'istanza* dell'etichetta nella scena, che a questo punto non è visibile all'utente. Inserisce anche il quad (anche invisibile) in cui si trova l'immagine e si sovrappone al mondo reale. Questo è importante perché le coordinate della casella recuperate dal servizio dopo l'analisi vengono riportate in questo quad per determinare la posizione approssimativa dell'oggetto nel mondo reale. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Aggiungere il metodo **FinaliseLabel ()** . È responsabile di:

    *   Impostazione del testo dell' *etichetta* con il *tag* della stima con la massima confidenza.
    *   Chiamata del calcolo del rettangolo di delimitazione dell'oggetto Quad, posizionato in precedenza e posizionamento dell'etichetta nella scena.
    *   Regolazione della profondità dell'etichetta usando un Raycast verso ilrettangolo di delimitazione, che deve essere in conflitto con l'oggetto nel mondo reale.
    * Reimpostazione del processo di acquisizione per consentire all'utente di acquisire un'altra immagine.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Aggiungere il metodo **CalculateBoundingBoxPosition ()** che ospita una serie di calcoli necessari per tradurre le coordinate del rettangolo di delimitazione recuperate dal servizio e ricrearle proporzionalmente sul quad.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.

    > [!IMPORTANT]
    > Prima di continuare, aprire la classe **CustomVisionAnalyser** e, all'interno del metodo **AnalyseLastImageCaptured ()** , *rimuovere il commento* dalle righe seguenti:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> Non preoccuparsi del messaggio "Impossibile trovare la classe **ImageCapture** ", che verrà creata nel capitolo successivo.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capitolo 10: creare la classe ImageCapture

La classe successiva che si intende creare è la classe **ImageCapture** .

Questa classe è responsabile di:

*   Acquisizione di un'immagine con la fotocamera HoloLens e relativa archiviazione nella cartella dell' *app* .
*   Gestione dei movimenti *Tap* dall'utente.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi scegliere **Crea** > **script C\#** . Denominare lo script **ImageCapture**.

3.  Fare doppio clic sul nuovo script **ImageCapture** per aprirlo con **Visual Studio.**

4.  Sostituire gli spazi dei nomi all'inizio del file con il codice seguente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe **ImageCapture** , sopra il metodo **Start ()** :

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  È ora necessario aggiungere il codice per i metodi **svegli ()** e **Start ()** :

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementare un gestore che verrà chiamato quando si verifica un movimento TAP:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Quando il cursore è **verde**, significa che la fotocamera è disponibile per l'immagine. Quando il cursore è **rosso**, significa che la fotocamera è occupata.

8.  Aggiungere il metodo usato dall'applicazione per avviare il processo di acquisizione dell'immagine e archiviare l'immagine:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  Aggiungere i gestori che verranno chiamati quando la foto è stata acquisita e quando è pronta per essere analizzata. Il risultato viene quindi passato a **CustomVisionAnalyser** per l'analisi.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Assicurarsi di salvare le modifiche in **Visual Studio**prima di tornare a **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capitolo 11-Configurazione degli script nella scena

Ora che è stato scritto tutto il codice necessario per questo progetto, è il momento di configurare gli script nella scena e sui prefabbricati per comportarsi correttamente.

1.  Nell' **Editor**di Unity selezionare la **fotocamera principale**nel **Pannello gerarchia**.
2.  Nel **pannello Inspector**, con la **fotocamera principale** selezionata, fare clic su **Add Component**, quindi cercare lo script **SceneOrganiser** e fare doppio clic su per aggiungerlo.

    ![](images/AzureLabs-Lab310-38.png)

3.  Nel **Pannello del progetto**aprire la cartella prefabbricati, trascinare l' **etichetta** prefabbricato nell'area di input di destinazione di riferimento vuota dell' *etichetta* , nello script **SceneOrganiser** appena aggiunto alla *fotocamera principale*, come illustrato in l'immagine seguente:

    ![](images/AzureLabs-Lab310-39.png)

4.  Nel **Pannello gerarchia**selezionare l'elemento figlio **GazeCursor** della **fotocamera principale**.
5.  Nel **pannello Inspector**, con **GazeCursor** selezionato, fare clic su **Add Component**, quindi cercare **GazeCursor** script e fare doppio clic su per aggiungerlo.

    ![](images/AzureLabs-Lab310-40.png)

6.  Anche in questo caso, nel **Pannello gerarchia**selezionare l'elemento figlio **SpatialMapping** della **fotocamera principale**.
7.  Nel **pannello Inspector**, con **SpatialMapping** selezionato, fare clic su **Add Component**, quindi cercare **SpatialMapping** script e fare doppio clic su per aggiungerlo.

    ![](images/AzureLabs-Lab310-41.png)

Gli script rimanenti non impostati verranno aggiunti dal codice nello script **SceneOrganiser** , durante la fase di esecuzione.

## <a name="chapter-12---before-building"></a>Capitolo 12-prima della compilazione

Per eseguire un test completo dell'applicazione, è necessario sideload in Microsoft HoloLens.

Prima di procedere, verificare quanto segue:

-  Tutte le impostazioni indicate nel [capitolo 3](#chapter-3---set-up-the-unity-project) sono impostate correttamente.
- Lo script **SceneOrganiser** è associato all'oggetto **principale della fotocamera** .
- Lo script **GazeCursor** è associato all'oggetto **GazeCursor** .
- Lo script **SpatialMapping** è associato all'oggetto **SpatialMapping** .
- Nel [capitolo 5](#chapter-5---create-the-customvisionanalyser-class), passaggio 6:

    - Assicurarsi di inserire la **chiave di stima del servizio** nella variabile **predictionKey** .
    - L' **endpoint di stima** è stato inserito nella classe **predictionEndpoint** .

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capitolo 13: compilare la soluzione UWP e sideload l'applicazione

A questo punto si è pronti per compilare l'applicazione come soluzione UWP che sarà possibile distribuire in Microsoft HoloLens. Per avviare il processo di compilazione:

1.  Passare a **File > impostazioni di compilazione**.

2.  Seleziona i **progetti\# Unity C**.

3.  Fare clic su **Aggiungi scene aperte**. Verrà aggiunta la scena attualmente aperta alla compilazione.

    ![](images/AzureLabs-Lab310-42.png)

4.  Fai clic su **Compila**. Unity avvierà una finestra di *Esplora file* , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella adesso e denominarla **app**. Quindi, con la cartella dell' **app** selezionata, fare clic su **Seleziona cartella**.

5.  Unity inizierà a compilare il progetto nella cartella dell' **app** .

6.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).

7.  Per eseguire la distribuzione in Microsoft HoloLens, è necessario l'indirizzo IP del dispositivo (per la distribuzione remota) e per assicurarsi che abbia anche la **modalità di sviluppo** impostata. A tale scopo, effettuare le seguenti operazioni:

    1.  Quando si indossa il HoloLens, aprire le **Impostazioni**.

    2.  Passa a **rete &**  > **Opzioni avanzate** **Wi-Fi** > Internet

    3.  Prendere nota dell'indirizzo **IPv4** .

    4.  Tornare quindi a Settings ( **Impostazioni**) e quindi **aggiornare & Security** > **per gli sviluppatori**

    5.  Impostare la **modalità di sviluppo** *su*.

8.  Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.

9.  Nella configurazione della soluzione selezionare **debug**.

10. Nella piattaforma soluzione selezionare **x86, computer remoto**. Verrà richiesto di inserire l' **indirizzo IP** di un dispositivo remoto (Microsoft HoloLens, in questo caso, annotato).

    ![](images/AzureLabs-Lab310-43.png)

11. Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione in HoloLens.

12. L'app verrà ora visualizzata nell'elenco delle app installate in Microsoft HoloLens, pronto per l'avvio.

### <a name="to-use-the-application"></a>Per utilizzare l'applicazione:

* Esaminare un oggetto, che è stato sottoposto a training con la **servizio visione artificiale personalizzato di Azure, il rilevamento degli oggetti**e usare il **gesto Tap**.
* Se l'oggetto viene rilevato correttamente, verrà visualizzato un *testo dell'etichetta* con spazio globale con il nome del tag.

> [!IMPORTANT]
> Ogni volta che si acquisisce una foto e la si invia al servizio, è possibile tornare alla pagina del servizio e ripetere il training del servizio con le immagini appena acquisite. All'inizio, probabilmente sarà anche necessario correggere i *riquadri* delimitativi in modo da essere più accurati e ripetere il training del servizio.

> [!NOTE]
> Il testo dell'etichetta inserito potrebbe non essere visualizzato vicino all'oggetto quando i sensori Microsoft HoloLens e/o SpatialTrackingComponent in Unity non riescono a collocare i Collider appropriati, relativi agli oggetti reali. Se questo è il caso, provare a usare l'applicazione in un'area diversa.

## <a name="your-custom-vision-object-detection-application"></a>Applicazione di rilevamento oggetti Visione personalizzata

Congratulazioni, è stata creata un'app per realtà mista che sfrutta il Visione personalizzata di Azure, l'API di rilevamento oggetti, che può riconoscere un oggetto da un'immagine, quindi fornire una posizione approssimativa per tale oggetto nello spazio 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Aggiungendo all'etichetta di testo, utilizzare un cubo semi-trasparente per eseguire il wrapping dell'oggetto reale inun rettangolo di delimitazione 3D.

### <a name="exercise-2"></a>Esercizio 2

Eseguire il training del Servizio visione artificiale personalizzato per riconoscere più oggetti.

### <a name="exercise-3"></a>Esercizio 3

Riprodurre un suono quando viene riconosciuto un oggetto.

### <a name="exercise-4"></a>Esercizio 4

Usare l'API per eseguire nuovamente il training del servizio con le stesse immagini analizzate dall'app, in modo da rendere più accurato il servizio (eseguire contemporaneamente la stima e la formazione).
