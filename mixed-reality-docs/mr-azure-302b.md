---
title: MR e 302b Azure - visione artificiale personalizzato
description: Completare questo corso per informazioni su come eseguire il training di un modello di machine learning e quindi usare il modello con training per riconoscere gli oggetti simili all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, visione artificiale personalizzato, hololens, coinvolgenti, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600002"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR e 302b Azure: Servizio visione artificiale personalizzato

In questo corso, si apprenderà come riconoscere personalizzato contenuto visivo all'interno di un'immagine fornita, usando le funzionalità di visione artificiale personalizzato di Azure in un'applicazione di realtà mista.

Questo servizio consentirà di eseguire il training di un modello di machine learning usando immagini di oggetto. Si utilizzerà il modello con training per riconoscere gli oggetti simili, come specificato dall'acquisizione della fotocamera del Microsoft HoloLens o una fotocamera connesso al PC per immersive auricolari (VR).

![risultato del corso](images/AzureLabs-Lab302b-00.png)

Visione artificiale personalizzato di Azure è un servizio cognitivi di Microsoft che consente agli sviluppatori di compilare classificatori di immagini personalizzate. Questi due classificatori sono quindi utilizzabile con nuove immagini per riconoscere o classificare, gli oggetti all'interno che la nuova immagine. Il servizio offre un portale semplice, facile da usare, in linea per semplificare il processo. Per altre informazioni, visitare il [pagina servizio visione artificiale personalizzato di Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di funzionare in due modalità:

-   **Modalità analisi**: configurare il servizio visione artificiale personalizzato manualmente dal caricamento di immagini, la creazione di tag e il servizio di training per riconoscere i diversi oggetti (in questo caso mouse e tastiera). Quindi si creerà un'app di HoloLens che acquisire immagini di uso della fotocamera e tenta di riconoscere tali oggetti nel mondo reale.

-   **Training modello**: si implementerà codice che consentirà una modalità"Training" nell'app. La modalità di training consentirà di acquisire immagini di uso della fotocamera degli HoloLens, caricare le immagini acquisite nel servizio e il training del modello di visione artificiale personalizzato.

Questo corso ti spiegherà come ottenere i risultati dal servizio visione artificiale personalizzato in un'applicazione di esempio basate su Unity. Sarà quindi compito è possibile applicare questi concetti a un'applicazione personalizzata, che potrebbe voler costruire.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> MR e 302b Azure: Servizio visione artificiale personalizzato</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla HoloLens, è inoltre possibile applicare informazioni in questo corso per auricolari (VR) coinvolgenti di realtà mista di Windows. Poiché immersive auricolari (VR) non è accessibile fotocamere, sarà necessario una fotocamera esterna connessa al PC. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare immersive auricolari (VR).

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quanto elencato di seguito.

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](install-the-tools.md#installation-checklist)
- [La versione più recente di Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore
- Una fotocamera connessa al PC (per lo sviluppo visore VR immersivi)
- Accesso a Internet per la configurazione di Azure e il recupero delle API visione artificiale personalizzato
- Una serie di almeno cinque (5) immagini (dieci (10) consigliati) per ogni oggetto che si desidera venga riconosciuta dal servizio visione artificiale personalizzato. Se si desidera, è possibile usare [le immagini già fornite con questo corso (un mouse e tastiera) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
2.  Configurare e testare l'HoloLens. Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova app per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente). 

Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Capitolo 1 - portale del servizio visione artificiale personalizzato

Usare la *servizio visione artificiale personalizzato* in Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.

1.  Prima di tutto [passare al *servizio visione artificiale personalizzato* pagina principale](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Fare clic sui **iniziare a usare** pulsante.

    ![](images/AzureLabs-Lab302b-01.png)

3.  Accedi per il *servizio visione artificiale personalizzato* portale.

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

4.  Una volta che si sono connessi per la prima volta, verrà richiesto con la *Terms of Service* pannello. Fare clic sulla casella di controllo per accettare le condizioni. Quindi fare clic su **accetto**.

    ![](images/AzureLabs-Lab302b-03.png)

5.  Avere accettato le condizioni, verrà reindirizzato il *progetti* sezione del portale. Fare clic su **nuovo progetto**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  Verrà visualizzata una scheda sul lato destro, che verrà richiesto di specificare alcuni campi per il progetto.

    1.  Inserire un *nome* per il progetto.

    2.  Inserire un *Description* per il progetto (*facoltativo*).

    3.  Scegliere una *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).

    4. Impostare il *tipi di progetto* a **classificazione**
    
    5. Impostare il *domini* come **generali**.

        ![](images/AzureLabs-Lab302b-05.png)

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  Dopo aver completato, fare clic su **Crea progetto**, si verrà reindirizzati al servizio visione artificiale personalizzato, pagina del progetto.

## <a name="chapter-2---training-your-custom-vision-project"></a>Capitolo 2 - Training il progetto di Custom Vision

Una volta nel portale di visione artificiale personalizzato, l'obiettivo principale è eseguire il training di progetto per riconoscere gli oggetti specifici nelle immagini. È necessario almeno cinque (5) le immagini, anche se dieci (10) preferito, per ogni oggetto che si desidera riconoscere l'applicazione. [È possibile usare le immagini fornite con questo corso (un mouse e tastiera)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Per eseguire il training il progetto di servizio visione artificiale personalizzato:

1.  Fare clic sui **+** accanto alla **tag.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Aggiungere il **nome** dell'oggetto da riconoscere. Fare clic su **salvare**.

    ![](images/AzureLabs-Lab302b-07.png)

3.  Si noterà il **Tag** è stato aggiunto (potrebbe essere necessario ricaricare la pagina affinché venga visualizzata). Se non è già selezionata, fare clic con il nuovo tag, la casella di controllo.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Fare clic su **aggiungere immagini** al centro della pagina.

    ![](images/AzureLabs-Lab302b-09.png)

5.  Fare clic su **Esplora file locali**e di ricerca, quindi selezionare, le immagini da caricare, dove il minimo è cinque (5). Tenere presente che tutte queste immagini deve contenere l'oggetto che è set di training.

    > [!NOTE]
    >  È possibile selezionare numerose immagini alla volta, da caricare.

6.  Dopo che è possibile visualizzare le immagini nella scheda, selezionare i tag appropriati nel **contrassegni** casella.

    ![](images/AzureLabs-Lab302b-10.png)

7.  Fare clic su **caricare i file**. I file verranno avviato il caricamento. Dopo aver conferma del caricamento, fare clic su **fatto**

    ![](images/AzureLabs-Lab302b-11.png)

8.  Ripetere lo stesso processo per creare una nuova **Tag** denominate **tastiera** e caricare le foto appropriate per tale. Verificare di aver **deselezionare l'opzione** *Mouse* dopo aver creato i nuovi tag, pertanto, per visualizzare il *aggiungere immagini* finestra.

9.  Dopo aver creato entrambe tag configurato, fare clic su **Train**, e avvierà la compilazione della prima iterazione di training.

    ![](images/AzureLabs-Lab302b-12.png)

10. Una volta creato, sarà possibile visualizzare due pulsanti chiamati **predefinito** e **stima URL**. Fare clic su **predefinito** prima di tutto, quindi fare clic su **stima URL**.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > L'URL dell'endpoint che viene fornito da questo, è impostato su qualunque *iterazione* è stata contrassegnata come predefinita. Pertanto, se si apportata in un secondo momento una nuova *iterazione* e aggiornarlo come impostazione predefinita, non è necessario modificare il codice.

11. Dopo avere fatto clic su *URL di stima*, aprire *blocco note*e copiare e incollare il **URL** e il **stima-Key**, in modo che sia possibile recuperarlo quando ti serve in un secondo momento nel codice.

    ![](images/AzureLabs-Lab302b-14.png)

12. Fare clic sui **rappresenta dalla ruota dentata** nella parte superiore destra della schermata.

    ![](images/AzureLabs-Lab302b-15.png)

13. Copia il **chiave di formazione** e incollarlo in una *Notepad*, per un uso successivo.

    ![](images/AzureLabs-Lab302b-16.png)

14. Copiare anche il **Id progetto**e anche incollarlo nel *Notepad* file, per un uso successivo.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3 - configurare il progetto Unity

Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **New**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  A questo punto, è necessario specificare un nome di progetto Unity. Inserisci **AzureCustomVision.** Verificare che il modello di progetto è impostato su **3D**. Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **modificare* > *preferenze** e quindi dalla nuova finestra, passare a **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![](images/AzureLabs-Lab302b-19.png)

4.  Passare quindi ad **File > Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sui **commutatore piattaforma** pulsante per applicare la selezione.

    ![](images/AzureLabs-Lab302b-20.png)

5.  Mentre si trovano ancora nella **File > Build Settings** e assicurarsi che:

    1.  **Dispositivo di destinazione** è impostata su **Hololens**

        > Per le cuffie coinvolgenti, impostare **dispositivo di destinazione** al *qualsiasi dispositivo*.
        
    2.  **Tipo di compilazione** è impostata su **D3D**
    3.  **SDK** è impostata su **installata più recente**
    4.  **Versione di Visual Studio** è impostata su **installata più recente**
    5.  **Compilare ed eseguire** è impostata su **computer locale**
    6.  Salvare la scena e aggiungerlo alla compilazione. 

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![](images/AzureLabs-Lab302b-22.png)

        3. Aprire appena creato **scene** cartella e quindi il *nome File:* campo di testo, digitare **CustomVisionScene**, quindi fare clic su **Salva**.

            ![](images/AzureLabs-Lab302b-23.png)

            > Tenere presente, è necessario salvare le scene di Unity all'interno di *asset* cartella, come devono essere associate al progetto di Unity. Creare la cartella scene (e altre simili) è un modo tipico strutturare un progetto Unity.
            
    7.  Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.

        ![](images/AzureLabs-Lab302b-24.png)

6.  Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova.

7. In questo pannello, alcune impostazioni devono essere verificati:

    1.  Nel **altre impostazioni** scheda:

        1.  **Versione del Runtime di scripting** deve essere **Experimental (.NET 4.6 equivalente)**, che attiverà una necessità di riavviare l'Editor.

        2. **Back-end di scripting** deve essere **.NET**

        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        1. **InternetClient**

        2.  **Webcam**

        3. **Microfono**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.

    ![](images/AzureLabs-Lab302b-27.png)

8.  Nuovamente in *Build Settings* *Unity C\# progetti* non è non è più in grigio, selezionare la casella di controllo accanto a questo.

9.  Chiudere la finestra Impostazioni di compilazione.

10.  Salvare la scena e il progetto (**FILE > Salva scena / FILE > Salva progetto**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Capitolo 4 - importare la DLL Newtonsoft in Unity

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [MR-Azure-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importarlo nel progetto come un [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 6](#chapter-6---create-the-customvisionanalyser-class).

Questo corso è necessario utilizzare il **Newtonsoft** libreria, che è possibile aggiungere come una DLL agli asset. Il pacchetto che contiene [questa libreria può essere scaricata da questo collegamento](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornita con questo corso.

1.  Aggiungere il *.unitypackage* Unity tramite il **asset* > *importazione* *pacchetto*  >  *Custom* *pacchetto** l'opzione di menu.

2.  Nel **Importa pacchetto Unity** scatola viene, assicurarsi che tutto ciò che in (e tra cui) **plug-in** sia selezionata.

    ![](images/AzureLabs-Lab302b-28.png)

3.  Scegliere il **importazione** pulsante per aggiungere elementi al progetto.

4.  Andare alla **Newtonsoft** cartella sotto **plug-in** nella visualizzazione del progetto e selezionare il *plug-in di newtonsoft. JSON*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  Con il *plug-in di newtonsoft. JSON* selezionato, assicurarsi che **Any Platform** viene **unchecked**, quindi verificare che **WSAPlayer** è anche **unchecked**, quindi fare clic su **applica**. Si tratta semplicemente di confermare che i file siano configurati correttamente.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Contrassegnare questi plug-in Configura perché possano essere usati solo nell'Editor di Unity. Sono presenti un set diverso di esse nella cartella WSA che verrà usato dopo che il progetto viene esportato da Unity.

6.  Successivamente, è necessario aprire la **WSA** cartella, all'interno di **Newtonsoft** cartella. Si noterà una copia dello stesso file che appena configurato. Selezionare il file e quindi nella finestra di ispezione, assicurarsi che
    -   **Qualsiasi piattaforma** è **deselezionata** 
    -   **solo** **WSAPlayer** è **selezionata**
    -   **Non elaborare** è **selezionata**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Capitolo 5 - impostazione della fotocamera

1.  Nel Pannello di gerarchia, selezionare la *Main Camera*.

2.  Una volta selezionata, sarà possibile visualizzare tutti i componenti del *Main Camera* nel *Pannello di controllo*.

    1.  Il *fotocamera* nome oggetto deve essere **Main Camera** (si noti l'ortografici!)

    2.  Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici!)

    3.  Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**

    4.  Impostare **Cancella flag** al **colore a tinta unita** (ignorare questo visore VR immersivi).

    5.  Impostare il **sfondo** colore della fotocamera componente **nero, Alpha 0 (codice esadecimale: #00000000)** (ignorare questo visore VR immersivi).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Capitolo 6: creare la classe CustomVisionAnalyser.

A questo punto si è pronti a scrivere codice.

Inizierà con la *CustomVisionAnalyser* classe.

> [!NOTE]
> Le chiamate per il **servizio visione artificiale personalizzato** apportate al codice illustrato di seguito vengono effettuate tramite il **API REST di Custom Vision**. Tramite l'utilizzo, verrà visualizzato come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile per conto proprio). Tenere presente, che Microsoft mette a disposizione un **SDK del servizio visione artificiale personalizzato** che può essere utilizzato anche per effettuare chiamate al servizio. Per altre informazioni, vedere la [SDK del servizio visione artificiale personalizzato](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) articolo.

Questa classe è responsabile per:

-   Il caricamento dell'immagine più recente acquisito come una matrice di byte.

-   Invia la matrice di byte per Azure *servizio visione artificiale personalizzato* istanza per l'analisi.

-   Ricezione della risposta come stringa JSON.

-   La deserializzazione della risposta e passando l'oggetto risultante *Prediction* per il *SceneOrganiser* classe, che si occuperà di modalità di visualizzazione nella risposta.

Per creare questa classe:

1.  Fare doppio clic nella *cartella Asset* che si trova nel *pannello progetto*, quindi fare clic su **Crea > cartella**. Chiamare la cartella **script**.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Fare doppio clic sulla cartella appena creata, per aprirlo.

3.  Fare doppio clic all'interno della cartella, quindi fare clic su **Create** > **C\# Script**. Denominare lo script *CustomVisionAnalyser*.

4.  Fare doppio clic su nuova *CustomVisionAnalyser* script per aprirlo con **Visual Studio**.

5.  Aggiornare gli spazi dei nomi nella parte superiore del file per corrispondere a quanto segue:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  Nel *CustomVisionAnalyser* classe, aggiungere le variabili seguenti:

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
    > Assicurarsi di inserire le **chiave stima** nel **predictionKey** variabile e il **stima Endpoint** nel **predictionEndpoint** variabile. È stato copiato al *Notepad* più indietro in corso.

7.  Codice per un **Awake()** deve ora essere aggiunto per inizializzare la variabile di istanza:

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

8.  Eliminare i metodi **Start ()** e **Update ()**.

9.  Successivamente, aggiungere le coroutine (con il metodo statico **GetImageAsByteArray()** metodo sotto di essa), che otterranno i risultati dell'analisi dell'immagine acquisita dalle *ImageCapture* classe.

    > [!NOTE]
    > Nel **AnalyseImageCapture** coroutine, viene eseguita una chiamata ai *SceneOrganiser* classe che è ancora da creare. Pertanto **lasciarli impostata come commento le righe per il momento**.

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

10.  Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Capitolo 7 - creare la classe CustomVisionObjects

La classe si creerà ora è il *CustomVisionObjects* classe.

Questo script contiene un numero di oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate per la *servizio visione artificiale personalizzato*.

> [!WARNING]
> È importante che prendere nota dell'endpoint a cui il servizio visione artificiale personalizzato fornisce, come il codice JSON seguente struttura è stata configurata per lavorare con [ *v2.0 di Custom Vision stima*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Se si dispone di una versione diversa, si potrebbe essere necessario aggiornare la seguente struttura.

Per creare questa classe:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**. Chiamare lo script *CustomVisionObjects*.

2.  Fare doppio clic su nuova **CustomVisionObjects** script per aprirlo con **Visual Studio**.

3.  Aggiungere spazi dei nomi seguenti all'inizio del file:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Eliminare il **Start ()** e **Update ()** metodi all'interno di *CustomVisionObjects* classe; questa classe dovrebbe ora essere vuota.

5.  Aggiungere le classi seguenti **fuori** le *CustomVisionObjects* classe. Questi oggetti vengono utilizzati per il *Newtonsoft* libreria per serializzare e deserializzare i dati di risposta:

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Capitolo 8 - creare la classe VoiceRecognizer

Questa classe riconosceranno l'input vocale dell'utente.

Per creare questa classe:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**. Chiamare lo script *VoiceRecognizer*.

2.  Fare doppio clic su nuova **VoiceRecognizer** script per aprirlo con **Visual Studio**.

3.  Aggiungere gli spazi dei nomi seguenti sopra la *VoiceRecognizer* classe:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Quindi aggiungere le variabili seguenti all'interno di *VoiceRecognizer* classe sopra il *Start ()* metodo:

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

5.  Aggiungere il **Awake()** e **Start ()** metodi, l'utente verrà impostato il secondo dei quali *parole chiave* per essere riconosciuti durante l'associazione di un tag di un'immagine:

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

6.  Eliminare il **Update ()** (metodo).

7.  Aggiungere il gestore seguente, che viene chiamato ogni volta che viene riconosciuto input vocale:

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

8.  Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.

> [!NOTE]
> Non preoccuparsi di codice che può sembrare un errore, come si fornirà ulteriori classi presto, risolvere questi.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Capitolo 9 - creare la classe CustomVisionTrainer

Questa classe verrà concatenare una serie di chiamate web per eseguire il training di *servizio visione artificiale personalizzato*. Ogni chiamata verrà descritta in dettaglio immediatamente sopra il codice.

Per creare questa classe:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**. Chiamare lo script *CustomVisionTrainer*.

2.  Fare doppio clic su nuova *CustomVisionTrainer* script per aprirlo con **Visual Studio**.

3.  Aggiungere gli spazi dei nomi seguenti sopra la *CustomVisionTrainer* classe:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Quindi aggiungere le variabili seguenti all'interno di *CustomVisionTrainer* classe, sopra la **Start ()** (metodo). 

    > [!NOTE]
    > L'URL di training usata in questo esempio viene fornito all'interno di *1.2 di Custom Vision Training* documentazione, e ha una struttura di: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Per altre informazioni, visitare il [ *API di riferimento di Training di Custom Vision v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > È importante che prendere nota dell'endpoint a cui il servizio visione artificiale personalizzato offre la modalità di training, come la struttura JSON usata (all'interno di **CustomVisionObjects** classe) è stato configurato per lavorare con [  *Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). Se si dispone di una versione diversa, si potrebbe essere necessario aggiornare il *oggetti* struttura.

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
    > Assicurarsi di aggiungere il **chiave di servizio** valore (chiave di Training) e **Id progetto** valore, che si è preso nota precedente; questi sono i valori si [raccolti dal portale in precedenza nel corso ( Capitolo 2, vedere il passaggio 10 e versioni successive)](#chapter-2---training-your-custom-vision-oroject).

5.  Aggiungere il codice seguente **Start ()** e **Awake()** metodi. Questi metodi vengono chiamati durante l'inizializzazione e contengono la chiamata per impostare l'interfaccia utente:

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

6.  Eliminare il **Update ()** (metodo). Questa classe sarà non necessario.

7.  Aggiungere il **RequestTagSelection()** (metodo). Questo metodo è il primo a essere chiamato quando un'immagine acquisita e archiviata nel dispositivo ed è ora pronto per essere inviato per la *servizio visione artificiale personalizzato*per sottoporlo a training. Questo metodo visualizza i corsi di formazione dell'interfaccia utente, un set di parole chiave che l'utente può usare per contrassegnare l'immagine acquisita. Avvisa anche il *VoiceRecognizer* classe per iniziare l'ascolto per l'utente per l'input vocale.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Aggiungere il **VerifyTag()** (metodo). Questo metodo riceverà l'input vocale riconosciuto dal **VoiceRecognizer** classe e verificare la validità e quindi avviare il processo di training.

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

9.  Aggiungere il **SubmitImageForTraining()** (metodo). Questo metodo inizierà il processo di training del servizio visione artificiale personalizzato. Il primo passaggio consiste nel recuperare la **l'Id di Tag** dal servizio di cui è associato l'input vocale convalidato da parte dell'utente. Il **l'Id di Tag** verrà quindi caricato insieme all'immagine.

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

10. Aggiungere il **TrainCustomVisionProject()** (metodo). Una volta che l'immagine ha inviato e contrassegnata, questo metodo verrà chiamato. Verrà creata una nuova iterazione che verrà eseguito il training con tutte le immagini precedente inviate al servizio più l'immagine appena caricato. Dopo aver completato il training, questo metodo chiamerà un metodo per impostare l'oggetto appena creato **iterazione** come **predefinito**, in modo che l'endpoint si usa per l'analisi è l'ultima iterazione sottoposto a training.

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

11. Aggiungere il **SetDefaultIteration()** (metodo). Questo metodo verrà impostato l'iterazione precedentemente creato e sottoposto a training come *predefinito*. Al termine, questo metodo dovrà eliminare iterazione precedente esistente nel servizio. Al momento della stesura di questo corso, è previsto un limite di un numero massimo dieci (10) di iterazioni possono esistere contemporaneamente nel servizio.

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

12. Aggiungere il **DeletePreviousIteration()** (metodo). Questo metodo verrà trovare ed eliminare iterazione precedente non predefinita:

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

13. L'ultimo metodo da aggiungere in questa classe è il **GetImageAsByteArray()** metodo, utilizzata per il web le chiamate per convertire l'immagine acquisita in una matrice di byte.

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

14. Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Capitolo 10 - creare la classe SceneOrganiser

Questa classe sarà:

-   Creare un **cursore** oggetto da connettere alla fotocamera principale.

-   Creare un **etichetta** oggetto che verrà visualizzato quando il servizio riconosca gli oggetti reali.

-   Configurare la fotocamera principale collegando i componenti appropriati a esso.

-   Se si **modalità analisi**, le etichette in fase di esecuzione nello spazio complessivo appropriato rispetto alla posizione della fotocamera principale, generare e visualizzare i dati ricevuti dal servizio visione artificiale personalizzato.

-   Se si **modalità di Training**, generare l'interfaccia utente che visualizzerà le diverse fasi del processo di training.

Per creare questa classe:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**. Denominare lo script *SceneOrganiser*.

2.  Fare doppio clic su nuova *SceneOrganiser* script per aprirlo con **Visual Studio**.

3.  È sufficiente uno spazio dei nomi, rimuovere gli altri dall'esempio precedente il *SceneOrganiser* classe:

    ```csharp
    using UnityEngine;
    ```

4.  Quindi aggiungere le variabili seguenti all'interno di *SceneOrganiser* classe sopra il **Start ()** metodo:

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

5.  Eliminare il **Start ()** e **Update ()** metodi.

6.  A destra sotto le variabili, aggiungere il **Awake()** (metodo), che consente di inizializzare la classe e impostare la scena.

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

7.  A questo punto aggiungere il **CreateCameraCursor()** metodo che crea e posiziona il cursore Main Camera, e il **CreateLabel()** metodo, che consente di creare la **etichetta analisi** oggetto .

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

8. Aggiungere il **SetCameraStatus()** metodo che gestirà i messaggi destinati per la rete mesh di testo che fornisce lo stato della camera.

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

9. Aggiungere il **PlaceAnalysisLabel()** e **SetTagsToLastLabel()** metodi, che consente di generare e visualizzare i dati dal servizio visione artificiale personalizzato nella scena.

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

10. Infine, aggiungere il **CreateTrainingUI()** metodo, che distribuirà l'interfaccia utente di visualizzare le fasi del processo di training più quando l'applicazione è in modalità di Training. Questo metodo verrà inoltre essere sfruttato per creare l'oggetto di stato della fotocamera.

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

11. Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.

> [!IMPORTANT]
> Prima di continuare, aprire il **CustomVisionAnalyser** (classe) e all'interno di **AnalyseLastImageCaptured()** metodo *rimuovere il commento* le righe seguenti:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Capitolo 11 - creare la classe ImageCapture

La classe successiva si intende creare è il *ImageCapture* classe.

Questa classe è responsabile per:

-   Acquisizione di un'immagine usando la fotocamera di HoloLens e archiviandolo nel *App* cartella.

-   Gestione di movimenti di tocco da parte dell'utente.

-   Mantenendo il *Enum* valore che determina se l'applicazione verrà eseguita *Analysis* modalità oppure *Training* modalità.

Per creare questa classe:

1.  Andare alla **script** cartella creata in precedenza.

2.  Fare doppio clic all'interno della cartella, quindi fare clic su **Crea > C\# Script**. Denominare lo script *ImageCapture*.

3.  Fare doppio clic su nuova **ImageCapture** script per aprirlo con **Visual Studio**.

4.  Sostituire gli spazi dei nomi nella parte superiore del file con il codice seguente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Quindi aggiungere le variabili seguenti all'interno di *ImageCapture* classe sopra il **Start ()** metodo:

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

6.  Codice per un **Awake()** e **Start ()** metodi deve ora essere aggiunto:

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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implementare un gestore che verrà chiamato quando si verifica un gesto tocco.

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
    > Nelle *Analysis* modalità, il **TapHandler** metodo funge da opzione per avviare o interrompere il ciclo di acquisizione di foto.
    >
    > Nelle *Training* modalità, consente di acquisire un'immagine dalla fotocamera.
    >
    > Quando il cursore è verde, significa che la fotocamera è disponibile per acquisire l'immagine.
    >
    > Quando il cursore è rosso, significa che la fotocamera è occupata.

8.  Aggiungere il metodo che l'applicazione usa per avviare il processo di acquisizione di immagini e archiviare l'immagine.

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

9.  Aggiungere i gestori che verranno chiamati quando è stata acquisita la foto e quando è pronto per essere analizzati. Il risultato viene quindi passato per il *CustomVisionAnalyser* o il *CustomVisionTrainer* a seconda di quale modalità è nastavit il codice.

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

10. Assicurarsi di salvare le modifiche apportate **Visual Studio** prima di restituire **Unity**.

11. Ora che sono stati completati tutti gli script, tornare indietro nell'Editor di Unity, quindi fare clic e trascinare il **SceneOrganiser** classe la **script** cartella per il **Main Camera** oggetto di *gerarchia pannello*.

## <a name="chapter-12---before-building"></a>Capitolo 12 - prima della compilazione

Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload di HoloLens.

Prima di procedere, verificare quanto segue:

- Tutte le impostazioni indicate nella [capitolo 2](#chapter-2---training-your-custom-vision-project) siano impostate correttamente.

- Tutti i campi di **Main Camera**, pannello di controllo, vengono assegnate in modo corretto.

- Lo script **SceneOrganiser** è collegato il **Main Camera** oggetto.

- Assicurarsi di inserire le **chiave di stima** nel **predictionKey** variabile.

- Sono stati inseriti i **Endpoint di stima** nel **predictionEndpoint** variabile.

- Sono stati inseriti i **chiave di formazione** nel **trainingKey** variabile, del *CustomVisionTrainer* classe.

- Sono stati inseriti i **ID progetto** nel **projectId** variabile, del *CustomVisionTrainer* classe.

## <a name="chapter-13---build-and-sideload-your-application"></a>Capitolo 13 - compilazione e trasferire localmente l'applicazione

Per avviare il *compilazione* processo:

1.  Passare a **File > Impostazioni di compilazione**.

2.  Segni di graduazione **Unity C\# progetti**.

3.  Fai clic su **Compila**. Unity avvierà una **Esplora File** finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in. Creare ora tale cartella e denominarlo **App**. Quindi con il **App** cartella selezionata, fare clic su **Seleziona cartella**.

4.  Unity verrà avviata la compilazione del progetto per la **App** cartella.

5.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).

Per distribuire in HoloLens:

1.  È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore**. A tale scopo, effettuare le seguenti operazioni:

    1.  Durante l'uso di HoloLens, aprire il **impostazioni**.

    2.  Passare a **rete e Internet** > **Wi-Fi** > **opzioni avanzate**

    3.  Si noti il **IPv4** indirizzo.

    4.  Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza** > **per gli sviluppatori**

    5.  Impostare **modalità sviluppatore su**.

2.  Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.

3.  Nel *configurazione della soluzione* selezionate **Debug**.

4.  Nel *piattaforma soluzione*, selezionare **x86, computer remoto**. Verrà richiesto di inserire le **indirizzo IP** di un dispositivo remoto (il HoloLens, in questo caso, che si è preso nota).

    ![](images/AzureLabs-Lab302b-34.png)

5. Passare a **compilare** dal menu e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione di HoloLens.

6. L'app deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.

> [!NOTE]
> Per distribuire visore VR immersivi, impostare il **piattaforma soluzione** al *computer locale*e impostare il **configurazione** a *Debug*, con *x86* come la **piattaforma**. Quindi distribuire in locale del computer, utilizzando il **compilare** voce di menu, selezionando *Distribuisci soluzione*. 

## <a name="to-use-the-application"></a>Per usare l'applicazione:

Per cambiare le funzionalità di app tra *Training* modalità e *stima* modalità è necessario aggiornare il **AppMode** variabile, che si trova nel **Awake()** metodo all'interno di *ImageCapture* classe.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
oppure
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

Nelle *Training* modalità:

- Esaminare **Mouse** oppure **tastiera** e usare il **gesto tocco**.

- Successivamente, il testo verrà visualizzato che richiede di specificare un tag.

- Indicato **Mouse** oppure **tastiera**.


Nelle *stima* modalità:

- Esaminare un oggetto e usare la **gesto tocco**.

- Verrà visualizzato il testo che fornisce l'oggetto rilevato, con la probabilità più alta (ciò viene normalizzato).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Capitolo 14 - valutare e migliorare il modello di visione artificiale personalizzato

Per rendere il server più accurato, dovrai continuare per il training del modello utilizzato per la stima. Questa operazione viene eseguita tramite la nuova applicazione, sia con il *training* e *stima* modalità, richiedendo quest'ultimo è possibile visitare il portale, ovvero quelle illustrate in questo capitolo. Essere preparati a visitare di nuovo il portale del numero di volte, per migliorare costantemente il modello.

1. Passare al portale di visione artificiale personalizzato di Azure anche in questo caso e una volta nel progetto, selezionare la *stime* della scheda (dall'alto al centro della pagina):

    ![](images/AzureLabs-Lab302b-35.png)

2. Si noterà che tutte le immagini che sono state inviate al servizio mentre era in esecuzione l'applicazione. Se si posiziona le immagini, si fornirà all'utente le stime che sono state apportate per quell'immagine:

    ![](images/AzureLabs-Lab302b-36.png)

3. Selezionare una delle immagini per aprirlo. Una volta aperto, si visualizzeranno le stime eseguite per quell'immagine a destra. Se si delle stime corrette e si vuole aggiungere questa immagine modello di training del servizio, fare clic sui *contrassegni* casella di input e selezionare il tag che si desidera associare. Al termine, scegliere il *salvare e chiudere* pulsante nella parte inferiore destra e continuare con l'immagine successiva.

    ![](images/AzureLabs-Lab302b-37.png)

4. Dopo aver nuovamente alla griglia delle immagini, è possibile notare le immagini di che aver aggiunto i tag per (e salvato), verranno rimossi. Se si trova tutte le immagini che si ritiene che non è l'elemento con tag al loro interno, è possibile eliminarle, facendo clic sui segni di graduazione sull'immagine specificata (questa operazione può essere numerose immagini) e quindi scegliendo *eliminare* nell'angolo superiore destro della pagina della griglia. Nella finestra popup che segue, è possibile fare clic su *Sì, è possibile eliminare* oppure *No*, per confermare l'eliminazione o annullare l'operazione, rispettivamente. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Quando si è pronti per procedere, fare clic su verde *Train* pulsante in alto a destra. Il modello del servizio verrà eseguito il training con tutte le immagini sono ora fornite (che rendono più accurati). Una volta completato il training, assicurarsi di fare clic sui *predefinito* pulsante ancora una volta, in modo che le *stima URL* continua a usare l'iterazione aggiornata del servizio.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>L'applicazione API visione artificiale personalizzato completato

Complimenti, è stata compilata un'app per realtà mista che sfrutta l'API di visione artificiale personalizzato di Azure per riconoscere gli oggetti reali, il training del modello di servizio e visualizzare la fiducia di ciò che è stato individuato.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Eseguire il training del **servizio visione artificiale personalizzato** riconoscere più oggetti.

### <a name="exercise-2"></a>Esercizio 2

Che consente di espandere in quanto si è appreso, eseguire gli esercizi seguenti:

Riprodurre un suono quando un oggetto viene riconosciuto.

### <a name="exercise-3"></a>Esercizio 3

Usare l'API di eseguire nuovamente il training del servizio con le stesse immagini all'app è l'analisi, pertanto, per rendere il più accurati (eseguire stime e contemporaneamente di training).
