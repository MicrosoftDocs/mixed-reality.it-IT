---
title: MR e Azure 302B-visione personalizzata
description: Completare questo corso per apprendere come eseguire il training di un modello di apprendimento automatico e quindi usare il modello sottoposto a training per riconoscere oggetti simili in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, visione personalizzata, hololens, immersiva, VR
ms.openlocfilehash: 2c8bd31958cca3b0e27fb0e97839d75fcdebe8c5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438514"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR e Azure 302B: visione personalizzata

In questo corso si apprenderà come riconoscere contenuto visivo personalizzato in un'immagine fornita, usando le funzionalità di Visione personalizzata di Azure in un'applicazione di realtà mista.

Questo servizio consentirà di eseguire il training di un modello di apprendimento automatico usando immagini oggetto. Si userà quindi il modello sottoposto a training per riconoscere oggetti simili, come fornito dall'acquisizione della fotocamera di Microsoft HoloLens o da una fotocamera connessa al PC per auricolari immersivi (VR).

![risultato del corso](images/AzureLabs-Lab302b-00.png)

Azure Visione personalizzata è un servizio cognitivo Microsoft che consente agli sviluppatori di creare classificatori di immagini personalizzate. Questi classificatori possono quindi essere utilizzati con nuove immagini per riconoscere, o classificare, gli oggetti all'interno di tale nuova immagine. Il servizio fornisce un portale online semplice e facile da usare per semplificare il processo. Per ulteriori informazioni, visitare la [pagina servizio visione artificiale personalizzato di Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

Al termine di questo corso, sarà disponibile un'applicazione di realtà mista che sarà in grado di funzionare in due modalità:

-   **Modalità di analisi**: configurazione manuale del servizio visione artificiale personalizzato tramite il caricamento di immagini, creazione di tag e training del servizio per riconoscere oggetti diversi (in questo caso mouse e tastiera). Si creerà quindi un'app HoloLens che acquisisce immagini con la fotocamera e si tenterà di riconoscere tali oggetti nel mondo reale.

-   **Modalità di training**: viene implementato il codice che Abilita una "modalità di training" nell'app. La modalità di training consentirà di acquisire immagini usando la fotocamera HoloLens, caricare le immagini acquisite nel servizio ed eseguire il training del modello di visione artificiale personalizzato.

Questo corso spiegherà come ottenere i risultati dal Servizio visione artificiale personalizzato in un'applicazione di esempio basata su Unity. Sarà necessario applicare questi concetti a un'applicazione personalizzata che è possibile creare.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 302B: visione personalizzata</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente su HoloLens, è anche possibile applicare le informazioni apprese in questo corso agli auricolari per la realtà mista (VR) di Windows. Poiché le cuffie immersive (VR) non hanno fotocamere accessibili, sarà necessaria una fotocamera esterna connessa al PC. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare gli auricolari immersivi (VR).

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018). È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](install-the-tools.md#installation-checklist)
- [Windows 10 SDK più recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata
- Una fotocamera connessa al PC (per lo sviluppo di auricolari immersivi)
- Accesso a Internet per il programma di installazione di Azure e il recupero Visione personalizzata API
- Una serie di almeno cinque immagini (5) (dieci (10) consigliate) per ogni oggetto che si desidera venga riconosciuto dal Servizio visione artificiale personalizzato. Se si desidera, è possibile utilizzare [le immagini già disponibili in questo corso (un mouse del computer e una tastiera) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente. 

Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Capitolo 1-portale di Servizio visione artificiale personalizzato

Per usare il *servizio visione artificiale personalizzato* in Azure, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.

1.  Per prima cosa, [passare alla pagina principale *servizio visione artificiale personalizzato* ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Fare clic sul pulsante **Get Started** (attività iniziali).

    ![](images/AzureLabs-Lab302b-01.png)

3.  Accedere al portale di *servizio visione artificiale personalizzato* .

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

4.  Una volta effettuato l'accesso per la prima volta, verrà visualizzato il pannello *condizioni del servizio* . Fare clic sulla casella di controllo per accettare le condizioni. Quindi **, fare clic su Accetto.**

    ![](images/AzureLabs-Lab302b-03.png)

5.  Accettando le condizioni, si passerà alla sezione *Projects (progetti* ) del portale. Fare clic su **nuovo progetto**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  Verrà visualizzata una scheda sul lato destro, che richiederà di specificare alcuni campi per il progetto.

    1.  Inserire un *nome* per il progetto.

    2.  Inserire una *Descrizione* per il progetto (*facoltativo*).

    3.  Scegliere un *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).

    4. Impostare i *tipi di progetto* sulla **classificazione**
    
    5. Impostare i *domini* come **generali**.

        ![](images/AzureLabs-Lab302b-05.png)

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  Al termine, fare clic su **Crea progetto**. si verrà reindirizzati alla pagina servizio visione artificiale personalizzato, progetto.

## <a name="chapter-2---training-your-custom-vision-project"></a>Capitolo 2-training del progetto di Visione personalizzata

Una volta nel portale di Visione personalizzata, l'obiettivo principale è quello di eseguire il training del progetto per riconoscere oggetti specifici nelle immagini. Sono necessarie almeno cinque immagini (5), sebbene sia preferibile dieci (10), per ogni oggetto che si desidera che l'applicazione riconosca. [È possibile utilizzare le immagini fornite con questo corso (un mouse del computer e una tastiera)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Per eseguire il training del progetto Servizio visione artificiale personalizzato:

1.  Fare clic sul pulsante **+** accanto ai **tag.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Aggiungere il **nome** dell'oggetto che si desidera riconoscere. Fare clic su **Salva**.

    ![](images/AzureLabs-Lab302b-07.png)

3.  Si noterà che il **tag** è stato aggiunto. potrebbe essere necessario ricaricare la pagina affinché venga visualizzata. Fare clic sulla casella di controllo accanto al nuovo tag, se non è già selezionato.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Fare clic su **Aggiungi immagini** al centro della pagina.

    ![](images/AzureLabs-Lab302b-09.png)

5.  Fare clic su **Sfoglia file locali**e cercare, quindi selezionare le immagini che si desidera caricare, almeno cinque (5). Tenere presente che tutte le immagini devono contenere l'oggetto di cui si esegue il training.

    > [!NOTE]
    >  È possibile selezionare più immagini alla volta per caricare.

6.  Una volta visualizzate le immagini nella scheda, selezionare il tag appropriato nella casella **tag personali** .

    ![](images/AzureLabs-Lab302b-10.png)

7.  Fare clic su **Carica file**. Il caricamento dei file inizierà. Una volta confermata la richiesta di caricamento, fare clic su **fine**.

    ![](images/AzureLabs-Lab302b-11.png)

8.  Ripetere lo stesso processo per creare un nuovo **tag** denominato **Keyboard** e caricare le foto appropriate. Assicurarsi di **deselezionare** il *mouse* dopo aver creato i nuovi tag, in modo da visualizzare la finestra *Aggiungi immagini* .

9.  Una volta impostati entrambi i tag, fare clic su **Training**per avviare la creazione della prima iterazione di training.

    ![](images/AzureLabs-Lab302b-12.png)

10. Una volta compilato, sarà possibile visualizzare due pulsanti denominati **Make default** and **PREDICTION URL**. Fare clic su **Imposta come predefinito** per primo, quindi fare clic su **URL stima**.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > L'URL dell'endpoint fornito da questo oggetto è impostato su qualsiasi *iterazione* contrassegnata come predefinita. Di conseguenza, se in un secondo momento si crea una nuova *iterazione* e la si aggiorna come predefinita, non sarà necessario modificare il codice.

11. Una volta fatto clic su *URL stima*, aprire *blocco note*e copiare e incollare l' **URL** e la chiave di **stima**, in modo da poterlo recuperare quando necessario in un secondo momento nel codice.

    ![](images/AzureLabs-Lab302b-14.png)

12. Fare clic sull' **ingranaggio** nella parte superiore destra della schermata.

    ![](images/AzureLabs-Lab302b-15.png)

13. Copiare la **chiave di training** e incollarla in un *blocco note*, per un uso successivo.

    ![](images/AzureLabs-Lab302b-16.png)

14. Copiare anche l' **ID del progetto**e incollarlo nel file del *blocco note* , per usarlo in seguito.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3: configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire *Unity* e fare clic su **New**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity. Inserire **AzureCustomVision.** Verificare che il modello di progetto sia impostato su **3D**. Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a  **modifica* *Preferenze* > * e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![](images/AzureLabs-Lab302b-19.png)

4.  Passare quindi a **File > impostazioni di compilazione** e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.

    ![](images/AzureLabs-Lab302b-20.png)

5.  Sempre in **File > impostazioni di compilazione** e verificare che:

    1.  Il **dispositivo di destinazione** è impostato su **HoloLens**

        > Per gli auricolari immersivi, impostare **dispositivo di destinazione** su *qualsiasi dispositivo*.
        
    2.  Il **tipo di compilazione** è impostato su **D3D**
    3.  **SDK** è impostato sull' **ultima versione installata**
    4.  La **versione di Visual Studio** è impostata su **installazione più recente**
    5.  **Compilazione ed esecuzione** è impostato su **computer locale**
    6.  Salvare la scena e aggiungerla alla compilazione. 

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.

            ![](images/AzureLabs-Lab302b-22.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file:* testo digitare **CustomVisionScene**e quindi fare clic su **Salva**.

            ![](images/AzureLabs-Lab302b-23.png)

            > Tenere presente che è necessario salvare le scene Unity all'interno della cartella *assets* , in quanto devono essere associate al progetto Unity. La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.
            
    7.  Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.

        ![](images/AzureLabs-Lab302b-24.png)

6.  Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* .

7. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **altre impostazioni** :

        1.  La **versione di runtime di scripting** deve essere **sperimentale (equivalente a .NET 4,6)** , che attiverà la necessità di riavviare l'editor.

        2. Il **back-end di scripting** deve essere **.NET**

        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        1. **InternetClient**

        2.  **Webcam**

        3. **Microfono**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

    ![](images/AzureLabs-Lab302b-27.png)

8.  Nelle *impostazioni di compilazione* i *progetti di unity C\#* non sono più in grigio; Selezionare la casella di controllo accanto a questo.

9.  Chiudere la finestra impostazioni di compilazione.

10.  Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Capitolo 4-importazione della DLL di Newtonsoft in Unity

> [!IMPORTANT]
> Se si vuole ignorare il componente di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile scaricare questo [Azure-Mr-302B. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 6 ](#chapter-6---create-the-customvisionanalyser-class).

Questo corso richiede l'uso della libreria **Newtonsoft** , che è possibile aggiungere come dll agli asset. Il pacchetto contenente [questa libreria può essere scaricato da questo collegamento](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornito con questo corso.

1.  Aggiungere il *file unitypackage Tools* a Unity usando l'opzione di menu **asset* > *Importa* *pacchetto* > *pacchetto* *personalizzato** .

2.  Nella casella **Importa pacchetto Unity** visualizzata verificare che siano selezionati tutti gli elementi in (e inclusi) **plug** -in.

    ![](images/AzureLabs-Lab302b-28.png)

3.  Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.

4.  Passare alla cartella **Newtonsoft** in **plug** -in nella visualizzazione del progetto e selezionare il plug-in *Newtonsoft. JSON*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  Con il *plug-in Newtonsoft. JSON* selezionato, verificare che **qualsiasi piattaforma** sia **deselezionata**, quindi verificare che **WSAPlayer** sia **deselezionata**, quindi fare clic su **applica**. Questa operazione è sufficiente per verificare che i file siano configurati correttamente.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Contrassegnando questi plug-in, questi vengono configurati per essere usati solo nell'editor di Unity. Nella cartella WSA è presente un set diverso che verrà usato dopo l'esportazione del progetto da Unity.

6.  Successivamente, è necessario aprire la cartella **WSA** , all'interno della cartella **Newtonsoft** . Viene visualizzata una copia dello stesso file appena configurato. Selezionare il file e quindi nel controllo verificare che
    -   **Qualsiasi piattaforma** è **deselezionata** 
    -   **Verifica** **solo** **WSAPlayer**
    -   Il **processo** non è **selezionato**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Capitolo 5-configurazione della fotocamera

1.  Nel pannello gerarchia selezionare la *fotocamera principale*.

2.  Una volta selezionato, sarà possibile visualizzare tutti i componenti della *fotocamera principale* nel *Pannello di controllo*.

    1.  L'oggetto *fotocamera* deve essere denominato **Main camera** (nota l'ortografia).

    2.  Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (si noti l'ortografia).

    3.  Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**

    4.  Impostare **Cancella flag** su **colore a tinta unita** (ignorarlo per l'auricolare immersivo).

    5.  Imposta il colore di **sfondo** del componente della fotocamera su **nero, alfa 0 (codice esadecimale: #00000000)** (ignorarlo per l'auricolare immersivo).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Capitolo 6: creare la classe CustomVisionAnalyser.

A questo punto si è pronti per scrivere il codice.

Si inizierà con la classe *CustomVisionAnalyser* .

> [!NOTE]
> Le chiamate al **servizio visione artificiale personalizzato** effettuate nel codice riportato di seguito vengono effettuate usando l' **API REST di visione personalizzata**. Con l'uso di questa API, si vedrà come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile). Tenere presente che Microsoft offre un **servizio visione artificiale personalizzato SDK** che può essere usato anche per effettuare chiamate al servizio. Per altre informazioni, vedere l'articolo [servizio visione artificiale personalizzato SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) .

Questa classe è responsabile di:

-   Caricamento dell'immagine più recente acquisita come matrice di byte.

-   Invio della matrice di byte all'istanza di Azure *servizio visione artificiale personalizzato* per l'analisi.

-   Ricezione della risposta come stringa JSON.

-   Deserializzare la risposta e passare la *stima* risultante alla classe *SceneOrganiser* , che si occuperà della modalità di visualizzazione della risposta.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella *cartella Asset* che si trova nel *pannello progetto*, quindi fare clic su **Crea > cartella**. Chiamare gli **script**della cartella.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla.

3.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi fare clic su **crea** > **C\# script**. Denominare lo script *CustomVisionAnalyser*.

4.  Fare doppio clic sul nuovo script *CustomVisionAnalyser* per aprirlo con **Visual Studio**.

5.  Aggiornare gli spazi dei nomi all'inizio del file in modo che corrispondano a quanto segue:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  Nella classe *CustomVisionAnalyser* aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Assicurarsi di inserire la **chiave di stima** nella variabile **PredictionKey** e l'endpoint di **stima** nella variabile **predictionEndpoint** . Questi sono stati copiati nel *blocco note* in precedenza nel corso.

7.  Per inizializzare la variabile di istanza, è necessario aggiungere il codice per il punto di riattivazione **()** :

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Eliminare i metodi **Start ()** e **Update ()** .

9.  Aggiungere quindi la coroutine (con il metodo statico **GetImageAsByteArray ()** sottostante), che otterrà i risultati dell'analisi dell'immagine acquisita dalla classe *ImageCapture* .

    > [!NOTE]
    > Nella coroutine di **AnalyseImageCapture** è presente una chiamata alla classe *SceneOrganiser* che è ancora necessario creare. Lasciare quindi **le righe impostate come commento per il momento**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Capitolo 7: creare la classe CustomVisionObjects

La classe che verrà creata ora è la classe *CustomVisionObjects* .

Questo script contiene una serie di oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate all' *servizio visione artificiale personalizzato*.

> [!WARNING]
> È importante prendere nota dell'endpoint fornito dal Servizio visione artificiale personalizzato, perché la struttura JSON seguente è stata configurata per funzionare con [*visione personalizzata Prediction v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Se si dispone di una versione diversa, potrebbe essere necessario aggiornare la struttura seguente.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi fare clic su **crea** > **C\# script**. Chiamare lo script *CustomVisionObjects*.

2.  Fare doppio clic sul nuovo script **CustomVisionObjects** per aprirlo con **Visual Studio**.

3.  Aggiungere i seguenti spazi dei nomi all'inizio del file:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Eliminare i metodi **Start ()** e **Update ()** all'interno della classe *CustomVisionObjects* . Questa classe dovrebbe ora essere vuota.

5.  Aggiungere le classi seguenti al di **fuori** della classe *CustomVisionObjects* . Questi oggetti vengono usati dalla libreria *Newtonsoft* per serializzare e deserializzare i dati di risposta:

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Capitolo 8: creare la classe VoiceRecognizer

Questa classe riconoscerà l'input vocale dall'utente.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi fare clic su **crea** > **C\# script**. Chiamare lo script *VoiceRecognizer*.

2.  Fare doppio clic sul nuovo script **VoiceRecognizer** per aprirlo con **Visual Studio**.

3.  Aggiungere gli spazi dei nomi seguenti sopra la classe *VoiceRecognizer* :

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno della classe *VoiceRecognizer* , sopra il metodo *Start ()* :

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Aggiungere i metodi **svegli ()** e **Start ()** , il secondo dei quali configurerà le *parole chiave* utente da riconoscere quando si associa un tag a un'immagine:

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  Eliminare il metodo **Update ()** .

7.  Aggiungere il seguente gestore, che viene chiamato ogni volta che viene riconosciuto l'input vocale:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.

> [!NOTE]
> Non è necessario preoccuparsi del codice che potrebbe sembrare avere un errore, in quanto verranno presto fornite ulteriori classi, per risolvere il problema.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Capitolo 9: creare la classe CustomVisionTrainer

Questa classe condurrà una serie di chiamate web per il training del *servizio visione artificiale personalizzato*. Ogni chiamata verrà illustrata in dettaglio immediatamente sopra il codice.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi fare clic su **crea** > **C\# script**. Chiamare lo script *CustomVisionTrainer*.

2.  Fare doppio clic sul nuovo script *CustomVisionTrainer* per aprirlo con **Visual Studio**.

3.  Aggiungere gli spazi dei nomi seguenti sopra la classe *CustomVisionTrainer* :

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno della classe *CustomVisionTrainer* , sopra il metodo **Start ()** . 

    > [!NOTE]
    > L'URL di training usato in questo articolo è disponibile all'interno della documentazione di *visione personalizzata training 1,2* e presenta una struttura di: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Per ulteriori informazioni, visitare l' [*API di riferimento visione personalizzata Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > È importante prendere nota dell'endpoint che la Servizio visione artificiale personalizzato fornisce per la modalità di training, perché la struttura JSON usata (all'interno della classe **CustomVisionObjects** ) è stata configurata per funzionare con [*visione personalizzata Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). Se si dispone di una versione diversa, potrebbe essere necessario aggiornare la struttura *degli oggetti* .

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Assicurarsi di aggiungere il valore della **chiave del servizio** (chiave di training) e il valore dell' **ID progetto** , annotato in precedenza; Questi sono i valori [raccolti dal portale in precedenza nel corso (capitolo 2, passaggio 10 e versioni successive)](#chapter-2---training-your-custom-vision-project).

5.  Aggiungere i seguenti metodi **Start ()** e **sveglie ()** . Questi metodi vengono chiamati all'inizializzazione e contengono la chiamata per configurare l'interfaccia utente:

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  Eliminare il metodo **Update ()** . Questa classe non sarà necessaria.

7.  Aggiungere il metodo **RequestTagSelection ()** . Questo metodo è il primo a essere chiamato quando un'immagine viene acquisita e archiviata nel dispositivo ed è ora pronta per essere inviata alla *servizio visione artificiale personalizzato*per eseguirne il training. Questo metodo Visualizza, nell'interfaccia utente di training, un set di parole chiave che l'utente può usare per contrassegnare l'immagine che è stata acquisita. Avvisa inoltre la classe *VoiceRecognizer* per iniziare l'ascolto dell'input vocale da parte dell'utente.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Aggiungere il metodo **VerifyTag ()** . Questo metodo riceverà l'input vocale riconosciuto dalla classe **VoiceRecognizer** e ne verificherà la validità, quindi avvierà il processo di training.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Aggiungere il metodo **SubmitImageForTraining ()** . Questo metodo inizierà il processo di training Servizio visione artificiale personalizzato. Il primo passaggio consiste nel recuperare l' **ID del tag** dal servizio associato all'input vocale convalidato dall'utente. L' **ID Tag** verrà quindi caricato insieme all'immagine.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Aggiungere il metodo **TrainCustomVisionProject ()** . Una volta che l'immagine è stata inviata e contrassegnata, questo metodo verrà chiamato. Verrà creata una nuova iterazione che verrà sottoposta a training con tutte le immagini precedenti inviate al servizio più l'immagine appena caricata. Una volta completato il training, questo metodo chiamerà un metodo per impostare l' **iterazione** appena creata come **predefinita**, in modo che l'endpoint usato per l'analisi sia l'iterazione con training più recente.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Aggiungere il metodo **SetDefaultIteration ()** . Questo metodo imposterà l'iterazione precedentemente creata e sottoposta a training come *predefinita*. Al termine, questo metodo dovrà eliminare l'iterazione precedente esistente nel servizio. Al momento della stesura di questo corso, è previsto un limite di un massimo di dieci (10) iterazioni che possono esistere nello stesso momento nel servizio.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Aggiungere il metodo **DeletePreviousIteration ()** . Questo metodo troverà ed eliminerà l'iterazione non predefinita precedente:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. L'ultimo metodo da aggiungere in questa classe è il metodo **GetImageAsByteArray ()** usato nelle chiamate web per convertire l'immagine acquisita in una matrice di byte.

    ```csharp
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

14. Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Capitolo 10: creare la classe SceneOrganiser

Questa classe:

-   Creare un oggetto **cursore** per la connessione alla fotocamera principale.

-   Creare un oggetto **Label** che verrà visualizzato quando il servizio riconosce gli oggetti reali.

-   Configurare la fotocamera principale collegando i componenti appropriati.

-   In **modalità di analisi**, generare le etichette in fase di esecuzione, nello spazio globale appropriato rispetto alla posizione della fotocamera principale e visualizzare i dati ricevuti dal servizio visione artificiale personalizzato.

-   In **modalità di training**, generare l'interfaccia utente che visualizzerà le varie fasi del processo di training.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella cartella **Scripts** , quindi fare clic su **crea** > **C\# script**. Denominare lo script *SceneOrganiser*.

2.  Fare doppio clic sul nuovo script *SceneOrganiser* per aprirlo con **Visual Studio**.

3.  Sarà necessario solo uno spazio dei nomi, rimuovere gli altri dalla classe *SceneOrganiser* :

    ```csharp
    using UnityEngine;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno della classe *SceneOrganiser* , sopra il metodo **Start ()** :

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  Eliminare i metodi **Start ()** e **Update ()** .

6.  Direttamente sotto le variabili aggiungere il metodo **sveglie ()** che inizializza la classe e imposta la scena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  A questo punto aggiungere il metodo **CreateCameraCursor ()** che crea e posiziona il cursore della fotocamera principale e il metodo **CreateLabel ()** , che crea l'oggetto **Label di analisi** .

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Aggiungere il metodo **SetCameraStatus ()** , che gestirà i messaggi destinati alla rete di testo che forniscono lo stato della fotocamera.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Aggiungere i metodi **PlaceAnalysisLabel ()** e **SetTagsToLastLabel ()** , che generano e visualizzano i dati dal servizio visione artificiale personalizzato alla scena.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Infine, aggiungere il metodo **CreateTrainingUI ()** , che genera l'interfaccia utente che visualizza le varie fasi del processo di training quando l'applicazione è in modalità di training. Questo metodo verrà inoltre sfruttato per creare l'oggetto stato della fotocamera.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.

> [!IMPORTANT]
> Prima di continuare, aprire la classe **CustomVisionAnalyser** e, all'interno del metodo **AnalyseLastImageCaptured ()** , *rimuovere il commento* dalle righe seguenti:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Capitolo 11: creare la classe ImageCapture

La classe successiva che si intende creare è la classe *ImageCapture* .

Questa classe è responsabile di:

-   Acquisizione di un'immagine con la fotocamera HoloLens e relativa archiviazione nella cartella dell' *app* .

-   Gestione dei movimenti Tap dall'utente.

-   Gestione del valore *enum* che determina se l'applicazione viene eseguita in modalità di *analisi* o di *Training* .

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi fare clic su **crea > C\# script**. Denominare lo script *ImageCapture*.

3.  Fare doppio clic sul nuovo script **ImageCapture** per aprirlo con **Visual Studio**.

4.  Sostituire gli spazi dei nomi all'inizio del file con il codice seguente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe *ImageCapture* , sopra il metodo **Start ()** :

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implementare un gestore che verrà chiamato quando si verifica un movimento tap.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > In modalità *analisi* il metodo **TapHandler** funge da opzione per avviare o arrestare il ciclo di acquisizione foto.
    >
    > In modalità di *Training* , acquisisce un'immagine dalla fotocamera.
    >
    > Quando il cursore è verde, significa che la fotocamera è disponibile per l'immagine.
    >
    > Quando il cursore è rosso, significa che la fotocamera è occupata.

8.  Aggiungere il metodo usato dall'applicazione per avviare il processo di acquisizione dell'immagine e archiviare l'immagine.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  Aggiungere i gestori che verranno chiamati quando la foto è stata acquisita e quando è pronta per essere analizzata. Il risultato viene quindi passato a *CustomVisionAnalyser* o *CustomVisionTrainer* a seconda della modalità in cui è impostato il codice.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity**.

11. Ora che tutti gli script sono stati completati, tornare nell'editor di Unity, quindi fare clic e trascinare la classe **SceneOrganiser** dalla cartella **Scripts** all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.

## <a name="chapter-12---before-building"></a>Capitolo 12-prima della compilazione

Per eseguire un test completo dell'applicazione, è necessario sideload nel HoloLens.

Prima di procedere, verificare quanto segue:

- Tutte le impostazioni indicate nel [capitolo 2](#chapter-2---training-your-custom-vision-project) sono impostate correttamente.

- Tutti i campi della **fotocamera principale**, il pannello di controllo, sono assegnati correttamente.

- Lo script **SceneOrganiser** è associato all'oggetto **principale della fotocamera** .

- Assicurarsi di inserire la **chiave di stima** nella variabile **predictionKey** .

- L' **endpoint di stima** è stato inserito nella variabile **predictionEndpoint** .

- La **chiave di training** è stata inserita nella variabile **TrainingKey** della classe *CustomVisionTrainer* .

- L' **ID progetto** è stato inserito nella variabile **projectId** della classe *CustomVisionTrainer* .

## <a name="chapter-13---build-and-sideload-your-application"></a>Capitolo 13: creare e sideload l'applicazione

Per avviare il processo di *compilazione* :

1.  Passare a **File > impostazioni di compilazione**.

2.  Seleziona i **progetti di Unity C\#** .

3.  Fai clic su **Compila**. Unity avvierà una finestra di **Esplora file** , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella adesso e denominarla **app**. Quindi, con la cartella **app** selezionata, fare clic su **Seleziona cartella**.

4.  Unity inizierà a compilare il progetto nella cartella dell' **app** .

5.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).

Per eseguire la distribuzione in HoloLens:

1.  È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore**. A tale scopo, effettua le seguenti operazioni:

    1.  Quando si indossa il HoloLens, aprire le **Impostazioni**.

    2.  Passare a **rete & Internet** > **Opzioni avanzate** **Wi-Fi** > 

    3.  Prendere nota dell'indirizzo **IPv4** .

    4.  Quindi, tornare a **Settings (impostazioni**) e quindi **aggiornare & Security** > **per gli sviluppatori**

    5.  Impostare la **modalità di sviluppo su**.

2.  Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.

3.  Nella *configurazione della soluzione* selezionare **debug**.

4.  Nella *piattaforma soluzione*selezionare **x86, computer remoto**. Verrà richiesto di inserire l' **indirizzo IP** di un dispositivo remoto (HoloLens, in questo caso, annotato).

    ![](images/AzureLabs-Lab302b-34.png)

5. Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione in HoloLens.

6. L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.

> [!NOTE]
> Per eseguire la distribuzione in un dispositivo headset immersivo, impostare la **piattaforma della soluzione** su *computer locale*e impostare la **configurazione** su *debug*, con *x86* come **piattaforma**. Quindi eseguire la distribuzione nel computer locale, usando la voce di menu **Compila** , selezionando *Distribuisci soluzione*. 

## <a name="to-use-the-application"></a>Per utilizzare l'applicazione:

Per cambiare la funzionalità dell'app tra la modalità di *Training* e la modalità di *stima* è necessario aggiornare la variabile **AppMode** , che si trova nel metodo **sveglie ()** che si trova all'interno della classe *ImageCapture* .

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
o
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

In modalità di *Training* :

- Esaminare il **mouse** o la **tastiera** e usare il **gesto Tap**.

- Verrà quindi visualizzato un messaggio in cui viene chiesto di specificare un tag.

- Pronunciare il **mouse** o la **tastiera**.


In modalità di *stima* :

- Esaminare un oggetto e usare il **gesto Tap**.

- Verrà visualizzato il testo che fornisce l'oggetto rilevato, con la probabilità più elevata (normalizzata).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Capitolo 14: valutare e migliorare il modello di Visione personalizzata

Per rendere più accurato il servizio, sarà necessario continuare a eseguire il training del modello utilizzato per la stima. Questa operazione viene eseguita tramite l'uso della nuova applicazione, con le modalità di *Training* e di *previsione* , con la seconda richiesta di visitare il portale, che è il contenuto di questo capitolo. Prepararsi a rivisitare il portale più volte, per migliorare continuamente il modello.

1. Tornare al portale di Visione personalizzata di Azure e, una volta nel progetto, selezionare la scheda *stime* (dal centro superiore della pagina):

    ![](images/AzureLabs-Lab302b-35.png)

2. Vengono visualizzate tutte le immagini che sono state inviate al servizio mentre l'applicazione era in esecuzione. Se si passa il mouse sulle immagini, verranno fornite le stime effettuate per l'immagine:

    ![](images/AzureLabs-Lab302b-36.png)

3. Selezionare una delle immagini per aprirla. Una volta aperta, le stime effettuate per l'immagine vengono visualizzate a destra. Se le stime sono corrette e si desidera aggiungere questa immagine al modello di training del servizio, fare clic sulla casella di input *Tags* e selezionare il tag che si desidera associare. Al termine, fare clic sul pulsante *Salva e Chiudi* in basso a destra e continuare con l'immagine successiva.

    ![](images/AzureLabs-Lab302b-37.png)

4. Quando si torna alla griglia delle immagini, si noterà che le immagini a cui sono stati aggiunti i tag (e salvate) verranno rimosse. Se si rilevano immagini a cui non è associato alcun elemento con tag, è possibile eliminarle facendo clic sul segno di ingrandimento dell'immagine (può eseguire questa operazione per diverse immagini) e quindi facendo clic su *Elimina* nell'angolo superiore destro della pagina della griglia. Nella finestra popup riportata di seguito è possibile fare clic su *Sì, Elimina* o *No*per confermare l'eliminazione o annullarla, rispettivamente. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Quando si è pronti per continuare, fare clic sul pulsante di *Train* verde in alto a destra. Il modello di servizio verrà sottoposto a training con tutte le immagini fornite a questo punto (per renderlo più accurato). Al termine del training, assicurarsi di fare clic sul pulsante *Rendi predefinito* ancora una volta, in modo che l' *URL di stima* continui a usare l'iterazione più aggiornata del servizio.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Applicazione API Visione personalizzata completata

Congratulazioni, è stata creata un'app per realtà mista che sfrutta l'API Visione personalizzata di Azure per riconoscere oggetti reali, eseguire il training del modello del servizio e visualizzare la confidenza di ciò che è stato visto.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Eseguire il training del **servizio visione artificiale personalizzato** per riconoscere più oggetti.

### <a name="exercise-2"></a>Esercizio 2

Per ampliare i concetti appresi, completare gli esercizi seguenti:

Riprodurre un suono quando viene riconosciuto un oggetto.

### <a name="exercise-3"></a>Esercizio 3

Usare l'API per eseguire nuovamente il training del servizio con le stesse immagini analizzate dall'app, in modo da rendere più accurato il servizio (eseguire contemporaneamente la stima e la formazione).
