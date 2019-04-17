---
title: MR e 310 Azure - rilevamento di oggetti
description: Completare questo corso per informazioni su come eseguire il training di un modello di machine learning e quindi usare il modello con training per riconoscere gli oggetti simili e la posizione nel mondo reale dall'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, servizio visione artificiale personalizzato, dell'oggetto rilevamento, mista realtà, academy, unity, esercitazione, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597652"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

# <a name="mr-and-azure-310-object-detection"></a>MR e Azure 310: Rilevamento di oggetti

In questo corso, si apprenderà come riconoscere contenuto visivo personalizzato e la sua posizione spaziale all'interno di un'immagine fornita, visione artificiale personalizzato di Azure usando le funzionalità di "Rilevamento di oggetti" in un'applicazione di realtà mista.

Questo servizio consentirà di eseguire il training di un modello di machine learning usando immagini di oggetto. Si utilizzerà quindi il modello con training per riconoscere gli oggetti simili e approssimare la relativa posizione nel mondo reale, come specificato dall'acquisizione della fotocamera del Microsoft HoloLens o una videocamera di connettersi a un PC per immersive auricolari (VR).

![risultato del corso](images/AzureLabs-Lab310-00.png)

**Visione artificiale personalizzato di Azure, rilevamento di oggetti** è un Service Microsoft che consente agli sviluppatori di compilare classificatori di immagini personalizzate. Questi due classificatori sono quindi utilizzabile con le immagini nuove per rilevare gli oggetti all'interno di tale immagine nuova, fornendo **limiti di finestra** all'interno dell'immagine stessa. Il servizio offre un portale semplice, facile da usare, in linea per semplificare questo processo. Per altre informazioni, visitare i collegamenti seguenti:

* [Pagina di visione artificiale personalizzato di Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Limiti e quote](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1. L'utente sarà in grado *estasiati* in un oggetto che si è sottoposti a training usando il servizio di visione artificiale personalizzato di Azure, rilevamento di oggetti. 
2. L'utente userà il *toccare* movimento per acquisire un'immagine di ciò che si sta esaminando.
3. L'app invia l'immagine per il servizio visione artificiale personalizzato di Azure.
4. Sarà presente una risposta dal servizio che verrà visualizzato il risultato del riconoscimento come testo spazio globale. A tale scopo tramite l'utilizzo spaziale di rilevamento degli Microsoft HoloLens, allo scopo di comprendere la posizione globale dell'oggetto riconosciuta e quindi usando il *Tag* associata a ciò che viene rilevato nell'immagine, a fornire il testo dell'etichetta.

Il corso si occuperà anche caricare manualmente le immagini, la creazione di tag, e il servizio, per riconoscere diversi training oggetti (nell'esempio fornito una tazza), da impostando il *limite casella* all'interno dell'immagine è inviare. 

> [!IMPORTANT]
> Dopo la creazione e uso dell'app, lo sviluppatore deve passare al servizio visione artificiale personalizzato, Azure e identificare le stime eseguite dal servizio e verificare se è corretti o non (tramite l'assegnazione di tag alcuna operazione del servizio mancante, e modificando la *riquadri*). Il servizio può quindi eseguire nuovamente il training, che aumenta il livello di probabilità di riconoscere gli oggetti reali.

Questo corso ti spiegherà come ottenere i risultati dal servizio visione artificiale personalizzato di Azure, il rilevamento di oggetti, in un'applicazione di esempio basate su Unity. Sarà quindi compito è possibile applicare questi concetti a un'applicazione personalizzata, che potrebbe voler costruire.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> MR e Azure 310: Rilevamento di oggetti</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quanto elencato di seguito.

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer di sviluppo
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [La versione più recente di Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Oggetto [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) con abilitata la modalità sviluppatore
- Accesso a Internet per la configurazione di Azure e il recupero servizio visione artificiale personalizzato
-  Una serie di immagini almeno quindici (15) sono necessarie) per ogni oggetto che si desidera la visione artificiale personalizzato per riconoscere. Se si desidera, è possibile usare le immagini già fornite con questo corso [una serie di criteri utente personalizzati](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
2.  Configurare e testare l'HoloLens. Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova App per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente). 

Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Capitolo 1 - portale di visione artificiale personalizzato

Usare la **servizio visione artificiale personalizzato di Azure**, sarà necessario configurare un'istanza di tale da rendere disponibili all'applicazione.

1.  Spostarsi [per il **servizio visione artificiale personalizzato** pagina principale](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Fare clic su **introduttiva**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Accedere al portale del servizio visione artificiale personalizzato.

    ![](images/AzureLabs-Lab310-02.png)

4.  Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

5.  Una volta che si sono connessi per la prima volta, verrà richiesto con la *Terms of Service* pannello. Selezionare la casella di controllo *accettare le condizioni*. Quindi fare clic su **accetto**.

    ![](images/AzureLabs-Lab310-03.png)

6.  Avere accettato le condizioni, ci si trova nel *progetti* sezione. Fare clic su **nuovo progetto**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Verrà visualizzata una scheda sul lato destro, che verrà richiesto di specificare alcuni campi per il progetto.

    1.  Inserire un nome per il progetto

    2.  Inserire una descrizione per il progetto (**facoltativo**)

    3.  Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Se si vuole [altre informazioni sui gruppi di risorse di Azure, passare alla documentazione associata](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  Impostare il **tipi di progetto** come **rilevamento di oggetti (anteprima)**.

8.  Dopo aver completato, fare clic su **Crea progetto**, e si verrà reindirizzati alla pagina progetto servizio visione artificiale personalizzato.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capitolo 2 - Training il progetto di Custom Vision

Una volta nel portale di visione artificiale personalizzato, l'obiettivo principale è eseguire il training di progetto per riconoscere gli oggetti specifici nelle immagini.

È necessario almeno quindici (15) le immagini per ogni oggetto che si desidera riconoscere l'applicazione. È possibile usare le immagini fornite con questo corso ([una serie di criteri utente personalizzati](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Per eseguire il training del progetto di visione artificiale personalizzato:

1.  Fare clic sui **+** accanto alla **tag**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Aggiungere un **nome** per il tag che verrà usato per associare le immagini con. In questo esempio le immagini dei criteri utente personalizzati per il riconoscimento, pertanto ha assegnato un nome al tag a tale scopo, utilizziamo **Cup**. Fare clic su **salvare** una volta terminato.

    ![](images/AzureLabs-Lab310-07.png)

3.  Si noterà il **Tag** è stato aggiunto (potrebbe essere necessario ricaricare la pagina affinché venga visualizzata). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Fare clic su **aggiungere immagini** al centro della pagina.

    ![](images/AzureLabs-Lab310-09.png)

5.  Fare clic su **Esplora file locali**e passare alle immagini di cui si vuole caricare un oggetto, con il minimo being quindici (15).

    > [!TIP]
    >  È possibile selezionare numerose immagini alla volta, da caricare.

    ![](images/AzureLabs-Lab310-10.png)

6.  Premere **caricare i file** dopo aver selezionato tutte le immagini che si desidera eseguire il training con il progetto. I file verranno avviato il caricamento. Dopo aver conferma del caricamento, fare clic su ****.

    ![](images/AzureLabs-Lab310-11.png)

7.  A questo punto le immagini vengono caricate, ma non contrassegnate.

    ![](images/AzureLabs-Lab310-12.png)

8.  Per applicare un tag delle immagini, utilizzare il mouse. Come passa il mouse sopra l'immagine, che risulteranno utili per un'evidenziazione della selezione creando automaticamente una selezione attorno all'oggetto. Se non è accurato, è possibile creare il proprio. Questa operazione viene eseguita contenente il pulsante sinistro del mouse, e trascinando l'area di selezione per includere l'oggetto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Dopo la selezione dell'oggetto all'interno dell'immagine, verrà richiesto un prompt dei comandi di piccole dimensioni per poter *aggiungere Tag Region*. Selezionare il tag creato in precedenza ('Cup', nell'esempio precedente) o se si desidera aggiungere altri tag, digitare in, fare clic sui **+ (segno più)** pulsante.

    ![](images/AzureLabs-Lab310-14.png) 

10. Per contrassegnare l'immagine successiva, è possibile fare clic sulla freccia a destra del pannello o chiudere il pannello tag (facendo il **X** nell'angolo in alto a destra del pannello) e quindi fare clic sull'immagine successiva. Dopo aver creato l'immagine successiva pronto, ripetere la stessa procedura. Eseguire questa operazione per tutte le immagini di che aver caricato, fino a quando non sono tutte contrassegnate. 

    > [!NOTE]
    >  È possibile selezionare diversi oggetti della stessa immagine, simile all'immagine seguente: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Dopo avere tutti i tag, fare clic sui **tagged** pulsante a sinistra della schermata per visualizzare le immagini con tag. 

    ![](images/AzureLabs-Lab310-16.png)

12. A questo punto si è pronti eseguire il training del servizio. Scegliere il **Train** pulsante e la prima iterazione training inizierà.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Una volta creato, sarà possibile visualizzare due pulsanti chiamati **predefinito** e **stima URL**. Fare clic su **predefinito** prima di tutto, quindi fare clic su **stima URL**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > L'endpoint che viene fornito da questo, è impostato su qualunque *iterazione* è stata contrassegnata come predefinita. Pertanto, se si apportata in un secondo momento una nuova *iterazione* e aggiornarlo come impostazione predefinita, non è necessario modificare il codice.

14. Dopo avere fatto clic su **URL di stima**, aprire *blocco note*e copiare e incollare il **URL** (chiamato anche il **stima-Endpoint**) e il **stima-chiave servizio**, in modo che è possibile recuperarlo quando ti serve in un secondo momento nel codice.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3 - configurare il progetto Unity

Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire **Unity** e fare clic su **New**.

    ![](images/AzureLabs-Lab310-21.png)

2.  A questo punto, è necessario specificare un nome di progetto Unity. Inserire **CustomVisionObjDetection**. Verificare che il tipo di progetto è impostato su **3D**e impostare le **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **modificare* > *preferenze** e quindi dalla nuova finestra, passare a **strumenti esterni**. Change **External Script Editor** al **Visual Studio**. Chiudi il **preferenze** finestra.

    ![](images/AzureLabs-Lab310-23.png)

4.  Passare quindi ad **File > Build Settings** e passare la **piattaforma** a *Universal Windows Platform*e fare clic su di **Switch Platform** pulsante.

    ![](images/AzureLabs-Lab310-24.png)

5.  Nella stessa **Build Settings** finestra, assicurarsi che siano impostate le operazioni seguenti:

    1.  **Dispositivo di destinazione** è impostata su **HoloLens**        
    2.  **Tipo di compilazione** è impostata su **D3D**
    3.  **SDK** è impostata su **installata più recente**
    4.  **Versione di Visual Studio** è impostata su **installata più recente**
    5.  **Compilare ed eseguire** è impostata su **computer locale**            
    6.  Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.

        ![](images/AzureLabs-Lab310-25.png)

6.  Nella stessa **Build Settings** finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il **Inspector** si trova.

7. In questo pannello, alcune impostazioni devono essere verificati:

    1.  Nel **altre impostazioni** scheda:

        1.  **Versione del Runtime di scripting** deve essere **sperimentale** (.NET 4.6 equivalente), che attiverà una necessità di riavviare l'Editor.

        2. **Back-end di scripting** deve essere **.NET**.

        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Ulteriormente verso il basso il pannello, in **impostazioni XR** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, quindi assicurarsi che il **Windows misti Realtà SDK** viene aggiunto.

        ![](images/AzureLabs-Lab310-29.png)

8.  Nuovamente in **Build Settings**, *Unity C\# progetti* non è non è più in grigio: selezionare la casella di controllo accanto a questo.

9.  Chiudi il **Build Settings** finestra.

10. Nel **Editor**, fare clic su **Edit** > **impostazioni progetto** > **grafica**.

    ![](images/AzureLabs-Lab310-30.png)

11. Nel **Pannello di controllo** le *grafica impostazioni* saranno aperte. Scorrere verso il basso finché non viene visualizzata una matrice denominata **includono sempre gli shader**. Aggiungere uno slot, aumentando la **dimensioni** variabile da uno (in questo esempio, era 8 in modo che l'abbiamo fatto 9). Un nuovo slot apparirà l'ultima posizione della matrice, come illustrato di seguito:

    ![](images/AzureLabs-Lab310-31.png)

12. Nello slot, fare clic sul cerchio accanto slot per aprire un elenco di shader di destinazione di dimensioni ridotte. Cercare il **Legacy shader o trasparente/diffuso** shader e fare doppio clic. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capitolo 4 - importazione del pacchetto CustomVisionObjDetection Unity

Per questo corso viene fornito un pacchetto di Asset Unity denominati **Azure-SIG-310.unitypackage**. 

> [SUGGERIMENTO] Qualsiasi oggetto supportato da Unity, incluse intere scene, può essere compresse in un **.unitypackage** file ed esportato o importato in altri progetti. È il modo più efficiente e sicuro per spostare risorse tra diverse **i progetti Unity**.

È possibile trovare il [pacchetto Azure-SIG-310 che è necessario scaricare qui](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  Con il dashboard di Unity fronte, fare clic su **Assets** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto > pacchetto personalizzato**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Usare il selettore file per selezionare i **Azure-SIG-310.unitypackage** del pacchetto e fare clic su **Open**. Verrà visualizzato un elenco di componenti per questo asset all'utente. Confermare l'importazione facendo il **importare** pulsante.

    ![](images/AzureLabs-Lab310-34.png)

3.  Una volta completato l'importazione, si noterà che le cartelle del pacchetto sono stato aggiunto per le **asset** cartella. Questo tipo di struttura di cartelle è tipico per i progetti Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  Il **materiali** cartella contiene il materiale usato dalle **estasiati cursore**. 

    2.  Il **Plugins** contiene la DLL Newtonsoft utilizzato dal codice per deserializzare la risposta del servizio web. Due (2) diverse versioni contenute nella cartella e sotto-cartella, sono necessari per consentire la libreria da utilizzare ed compilati da Editor di Unity e la compilazione della piattaforma UWP. 

    3.  Il **Prefabs** cartella contiene il prefabs contenute nella scena. Questi sono:

        1.  Il **GazeCursor**, il cursore utilizzato nell'applicazione. Funzionerà con il prefab SpatialMapping per poter essere inseriti nella scena in oggetti fisici.
        2.  Il **etichetta**, ovvero l'oggetto dell'interfaccia utente utilizzato per visualizzare il tag di oggetti nella scena quando necessario.
        3.  Il **SpatialMapping**, che è l'oggetto che consente di usare l'applicazione creare una mappa virtuale, usando il rilevamento spaziale degli Microsoft HoloLens.

    4.  Il **scene** cartella che contiene attualmente preesistente scena a questo corso.

4.  Aprire il **scene** cartella, nella **pannello progetto**e fare doppio clic sul **ObjDetectionScene**, caricare la scena che si utilizzerà questo corso di.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Non è incluso alcun codice**, si scriverà il codice seguendo questo corso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capitolo 5 - creare la classe CustomVisionAnalyser.

A questo punto si è pronti a scrivere codice. Inizierà con la **CustomVisionAnalyser** classe.

> [!NOTE]
> Le chiamate per il **servizio visione artificiale personalizzato**, apportate al codice illustrato di seguito, vengono effettuate tramite il **API REST di Custom Vision**. Tramite l'utilizzo, verrà visualizzato come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile per conto proprio). Tenere presente, che Microsoft mette a disposizione un **SDK di Custom Vision** che può essere utilizzato anche per effettuare chiamate al servizio. Per altre informazioni, vedere la [articolo SDK di Custom Vision](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Questa classe è responsabile per:

- Il caricamento dell'immagine più recente acquisito come una matrice di byte.

- Invia la matrice di byte per Azure **servizio visione artificiale personalizzato** istanza per l'analisi.

- Ricezione della risposta come stringa JSON.

- La deserializzazione della risposta e passando l'oggetto risultante **Prediction** per il **SceneOrganiser** classe, che si occuperà di modalità di visualizzazione nella risposta.

Per creare questa classe:

1.  Fare doppio clic nella **cartella Asset**che si trova nel **pannello progetto**, quindi fare clic su **Create** > **cartella**. Chiamare la cartella **script**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Fare doppio clic sulla cartella appena creata, per aprirlo.

3.  Fare doppio clic all'interno della cartella, quindi fare clic su **Create** > **C\# Script**. Denominare lo script **CustomVisionAnalyser.**

4.  Fare doppio clic su nuova **CustomVisionAnalyser** script per aprirlo con **Visual Studio.**

5.  Assicurarsi di avere i seguenti spazi dei nomi cui viene fatto riferimento nella parte superiore del file:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  Nel **CustomVisionAnalyser** classe, aggiungere le variabili seguenti:

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
    > Assicurarsi di inserire le **stima-chiave di servizio** nel **predictionKey** variabile e il **stima-Endpoint** nel **predictionEndpoint**  variabile. È stato copiato al [blocco note in precedenza, nel capitolo 2, passaggio 14](#chapter-2---training-your-custom-vision-project).

7.  Codice per un **Awake()** deve ora essere aggiunto per inizializzare la variabile di istanza:

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

8.  Aggiungere le coroutine (con il metodo statico **GetImageAsByteArray()** metodo sotto di essa), che otterranno i risultati dell'analisi dell'immagine, acquisito dalle **ImageCapture** classe.

    > [!NOTE]
    > Nel **AnalyseImageCapture** coroutine, viene eseguita una chiamata ai **SceneOrganiser** classe che è ancora da creare. Pertanto **lasciarli impostata come commento le righe per il momento**.

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

9. Eliminare il **Start ()** e **Update ()** metodi, poiché essi non verrà utilizzati. 

10.  Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.

> [!IMPORTANT]
> Come accennato in precedenza, non preoccuparsi di codice che può sembrare un errore, come si fornirà ulteriori classi presto, risolvere questi.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capitolo 6: creare la classe CustomVisionObjects

La classe si creerà ora è il **CustomVisionObjects** classe.

Questo script contiene un numero di oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate al servizio visione artificiale personalizzato.

Per creare questa classe:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**. Chiamare lo script **CustomVisionObjects.**

2.  Fare doppio clic su nuova **CustomVisionObjects** script per aprirlo con **Visual Studio.**

3.  Assicurarsi di avere i seguenti spazi dei nomi cui viene fatto riferimento nella parte superiore del file:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Eliminare il **Start ()** e **Update ()** metodi all'interno di **CustomVisionObjects** (classe), questa classe ora deve essere vuota.

    > [!WARNING]
    > È importante che seguire attentamente l'istruzione successiva. Se si inseriscono le nuove dichiarazioni di classe all'interno di **CustomVisionObjects** (classe), puoi accedere a errori di compilazione [capitolo 10](#chapter-10---create-the-imagecapture-class), che segnala che **AnalysisRootObject** e **BoundingBox** non sono stati trovati.

5.  Aggiungere le classi seguenti *fuori* le **CustomVisionObjects** classe. Questi oggetti vengono utilizzati per il **Newtonsoft** libreria per serializzare e deserializzare i dati di risposta:

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

6.  Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capitolo 7 - creare la classe SpatialMapping

Questa classe verrà impostato il **Collider Mapping spaziale** della scena in modo da essere in grado di rilevare le collisioni tra oggetti virtuali e oggetti reali.

Per creare questa classe:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**. Chiamare lo script **SpatialMapping.**

2.  Fare doppio clic su nuova **SpatialMapping** script per aprirlo con **Visual Studio.**

3.  Assicurarsi di avere i seguenti spazi dei nomi citati in precedenza il **SpatialMapping** classe:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Quindi, aggiungere le variabili seguenti all'interno di **SpatialMapping** classe, sopra il **Start ()** (metodo):

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

5.  Aggiungere il **Awake()** e **Start ()**:

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

6.  Eliminare il **Update ()** (metodo).

7.  Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Capitolo 8 - creare la classe GazeCursor

Questa classe è responsabile della configurazione del cursore nella posizione corretta nell'area reale, mediante l'utilizzo dei **SpatialMappingCollider**, creato nel capitolo precedente.

Per creare questa classe:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**. Chiamare lo script **GazeCursor**

2.  Fare doppio clic su nuova **GazeCursor** script per aprirlo con **Visual Studio.**

3.  Assicurarsi di avere il seguente spazio dei nomi citato in precedenza il **GazeCursor** classe:

    ```csharp
    using UnityEngine;
    ```

4.  Quindi aggiungere la variabile seguente all'interno di **GazeCursor** classe, sopra la **Start ()** (metodo). 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Aggiorna il **Start ()** metodo con il codice seguente:

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

6.  Aggiorna il **Update ()** metodo con il codice seguente:

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
    > Senza doversi preoccupare di errore per il **SceneOrganiser** classe non viene trovato, verrà creato nel capitolo successivo.

7. Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capitolo 9 - creare la classe SceneOrganiser

Questa classe sarà:

-   Configurare il *Main Camera* collegando i componenti appropriati a esso.

-   Quando viene rilevato un oggetto, sarà responsabile del calcolo relativa posizione nel mondo reale e sul posto un **Tag Label** vicino, con l'appropriato **nome del Tag**.    

Per creare questa classe:

1.  Pulsante destro del mouse all'interno di **gli script** cartella, quindi fare clic su **Create** > **C\# Script**. Denominare lo script **SceneOrganiser**.

2.  Fare doppio clic su nuova **SceneOrganiser** script per aprirlo con **Visual Studio.**

3.  Assicurarsi di avere i seguenti spazi dei nomi citati in precedenza il **SceneOrganiser** classe:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Quindi aggiungere le variabili seguenti all'interno di **SceneOrganiser** classe sopra il **Start ()** metodo:

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

5.  Eliminare il **Start ()** e **Update ()** metodi.

6.  Sotto le variabili, aggiungere il **Awake()** (metodo), che consente di inizializzare la classe e impostare la scena.

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

7.  Aggiungere il **PlaceAnalysisLabel()** metodo, che verrà *Instantiate* l'etichetta nella scena (che a questo punto è invisibile all'utente). Inserisce inoltre quad (anche invisibili) in cui viene inserito l'immagine e si sovrappone al mondo reale. Questo è importante perché le coordinate della finestra recuperati dal servizio dopo l'analisi vengono risalire in questa quad determinata la posizione approssimativa dell'oggetto nel mondo reale. 

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

8.  Aggiungere il **FinaliseLabel()** (metodo). È responsabile per:

    *   Impostando il *Label* testo con il *Tag* la stima con il livello di confidenza più elevato.
    *   Chiamare il calcolo del *rettangolo di selezione* sull'oggetto quad, posizionato in precedenza e posizionare l'etichetta nella scena.
    *   Regolare la profondità di etichetta usando un Raycast verso la *rettangolo di selezione*, quali dovrebbe entri in conflitto con l'oggetto nel mondo reale.
    * Reimpostare il processo di acquisizione per consentire all'utente di acquisire un'altra immagine.

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

9.  Aggiungere il **CalculateBoundingBoxPosition()** metodo, che ospita un numero di calcoli necessari per convertire le *rettangolo di selezione* coordinate recuperati dal servizio e crearli di nuovo in modo proporzionale su quad.

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

10. Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.

    > [!IMPORTANT]
    > Prima di continuare, aprire il **CustomVisionAnalyser** (classe) e all'interno di **AnalyseLastImageCaptured()** metodo *rimuovere il commento* le righe seguenti:
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
> Senza doversi preoccupare di **ImageCapture** classe messaggio 'non è stato possibile trovare', si creerà nel capitolo successivo.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capitolo 10 - creare la classe ImageCapture

La classe successiva si intende creare è il **ImageCapture** classe.

Questa classe è responsabile per:

*   Acquisizione di un'immagine usando la fotocamera di HoloLens e archiviandolo nel *App* cartella.
*   Gestisce *toccare* movimenti da parte dell'utente.

Per creare questa classe:

1.  Andare alla **script** cartella creata in precedenza.

2.  Fare doppio clic all'interno della cartella, quindi fare clic su **Create** > **C\# Script**. Denominare lo script **ImageCapture**.

3.  Fare doppio clic su nuova **ImageCapture** script per aprirlo con **Visual Studio.**

4.  Sostituire gli spazi dei nomi nella parte superiore del file con il codice seguente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Quindi aggiungere le variabili seguenti all'interno di **ImageCapture** classe sopra il **Start ()** metodo:

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

6.  Codice per un **Awake()** e **Start ()** metodi deve ora essere aggiunto:

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

7.  Implementare un gestore che verrà chiamato quando si verifica un gesto tocco:

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
    > Quando il cursore si trova **verde**, significa che la fotocamera è disponibile per acquisire l'immagine. Quando il cursore si trova **rosso**, significa che la fotocamera è occupata.

8.  Aggiungere il metodo che l'applicazione usa per avviare il processo di acquisizione di immagini e archiviare l'immagine:

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

9.  Aggiungere i gestori che verranno chiamati quando è stata acquisita la foto e quando è pronto per essere analizzati. Il risultato viene quindi passato per il **CustomVisionAnalyser** per l'analisi.

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

10. Assicurarsi di salvare le modifiche apportate **Visual Studio**, prima di restituire **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capitolo 11 - configurazione gli script nella scena

Ora che è necessario scrivere tutto il codice necessario per questo progetto, è ora possibile configurare gli script nella scena e su prefabs, per essi funzionino correttamente.

1.  All'interno di **Editor di Unity**, nel **pannello gerarchia**, selezionare il **Main Camera**.
2.  Nel **Pannello di controllo**, con la **Main Camera** selezionato, fare clic su **Add Component**, quindi cercare **SceneOrganiser** script e Fare doppio clic, per aggiungerlo.

    ![](images/AzureLabs-Lab310-38.png)

3.  Nel **pannello progetto**, aprire il **cartella Prefabs**, trascinare il **etichetta** prefab nel *etichetta* area di input destinazione del riferimento vuoto nel **SceneOrganiser** che appena aggiunti allo script il *Main Camera*, come illustrato nell'immagine seguente:

    ![](images/AzureLabs-Lab310-39.png)

4.  Nel **Pannello di gerarchia**, selezionare la **GazeCursor** figlio del **Main Camera**.
5.  Nel **Pannello di controllo**, con la **GazeCursor** selezionato, fare clic su **Add Component**, quindi cercare **GazeCursor** script e Fare doppio clic, per aggiungerlo.

    ![](images/AzureLabs-Lab310-40.png)

6.  Ripetere l'operazione, il **pannello gerarchia**, selezionare il **SpatialMapping** figlio del **Main Camera**.
7.  Nel **Pannello di controllo**, con la **SpatialMapping** selezionato, fare clic su **Add Component**, quindi cercare **SpatialMapping** script e fare doppio clic, per aggiungerlo.

    ![](images/AzureLabs-Lab310-41.png)

Gli script rimanenti che si hanno non verrà aggiunti dal codice nel set il **SceneOrganiser** script, in fase di esecuzione.

## <a name="chapter-12---before-building"></a>Capitolo 12 - prima della compilazione

Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload in di Microsoft HoloLens.

Prima di procedere, verificare quanto segue:

-  Tutte le impostazioni indicate nella [capitolo 3](#chapter-3---set-up-the-unity-project) siano impostate correttamente.
- Lo script **SceneOrganiser** è collegato il **Main Camera** oggetto.
- Lo script **GazeCursor** è collegato il **GazeCursor** oggetto.
- Lo script **SpatialMapping** è collegato il **SpatialMapping** oggetto.
- Nelle [capitolo 5](#chapter-5---create-the-customvisionanalyser-class), passaggio 6:

    - Assicurarsi di inserire le **chiave del servizio stima** nel **predictionKey** variabile.
    - Sono stati inseriti i **Endpoint di stima** nel **predictionEndpoint** classe.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capitolo 13 - compila la soluzione di piattaforma UWP e trasferire localmente l'applicazione

A questo punto si è pronti a compilare l'applicazione come una soluzione di piattaforma UWP potrai distribuire con il Microsoft HoloLens è. Per iniziare il processo di compilazione:

1.  Passare a **File > Impostazioni di compilazione**.

2.  Segni di graduazione **Unity C\# progetti**.

3.  Fare clic su **aggiungere scene Open**. Verrà aggiunta la scena attualmente aperta per la compilazione.

    ![](images/AzureLabs-Lab310-42.png)

4.  Fai clic su **Compila**. Unity avvierà una *Esplora File* finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in. Creare ora tale cartella e denominarlo **App**. Quindi con il **App** cartella selezionata, fare clic su **Seleziona cartella**.

5.  Unity verrà avviata la compilazione del progetto per la **App** cartella.

6.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).

7.  Per distribuire al Microsoft HoloLens, è necessario l'indirizzo IP del dispositivo (per la distribuzione remota), e per verificare che siano anche dispone **modalità sviluppatore** impostato. A tale scopo, effettuare le seguenti operazioni:

    1.  Durante l'uso di HoloLens, aprire il **impostazioni**.

    2.  Passare a **rete e Internet** > **Wi-Fi** > **opzioni avanzate**

    3.  Si noti il **IPv4** indirizzo.

    4.  Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza** > **per gli sviluppatori**

    5.  Impostare **modalità sviluppatore** *su*.

8.  Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.

9.  Selezione configurazione di soluzione **Debug**.

10. La piattaforma della soluzione, selezionare **x86, computer remoto**. Verrà richiesto di inserire le **indirizzo IP** di un dispositivo remoto (di Microsoft HoloLens, in questo caso, che si è preso nota).

    ![](images/AzureLabs-Lab310-43.png)

11. Andare alla **compilare** dal menu e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione di HoloLens.

12. L'app deve vengono ora visualizzati nell'elenco delle App installate in di Microsoft HoloLens, pronta per essere avviata.

### <a name="to-use-the-application"></a>Per usare l'applicazione:

* Esaminare un oggetto che aver eseguito il training con il **servizio visione artificiale personalizzato di Azure, rilevamento di oggetti**e utilizzare il **gesto tocco**.
* Se l'oggetto è stato rilevato, un spazio globale *testo dell'etichetta* verranno visualizzate con il nome del tag.

> [!IMPORTANT]
> Ogni volta che è acquisire una foto e inviarlo al servizio, è possibile tornare alla pagina del servizio e ripetere il training del servizio con le immagini appena acquisite. All'inizio, sarà probabilmente anche essere necessario correggere il *riquadri* per ottenere una maggiore precisione e ripetere il training del servizio.

> [!NOTE]
> Il testo dell'etichetta inseriti potrebbe non essere visualizzato in prossimità dell'oggetto quando i sensori Microsoft HoloLens e/o SpatialTrackingComponent in Unity non è possibile posizionare il colliders appropriato, rispetto all'oggetto reale. Provare a usare l'applicazione in un'area diversa, se in questo caso.

## <a name="your-custom-vision-object-detection-application"></a>La visione artificiale personalizzato, applicazione di rilevamento di oggetti

Complimenti, è stata compilata un'app per realtà mista che sfrutta la visione personalizzata di Azure, API di rilevamento di oggetti, che può riconoscere un oggetto da un'immagine e quindi specificare una posizione approssimativa per quell'oggetto nello spazio 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Aggiunta all'etichetta di testo, utilizzare un cubo semi-trasparente per eseguire il wrapping dell'oggetto reale in una 3D *rettangolo di selezione*.

### <a name="exercise-2"></a>Esercizio 2

Eseguire il training del servizio visione artificiale personalizzato per riconoscere più oggetti.

### <a name="exercise-3"></a>Esercizio 3

Riprodurre un suono quando un oggetto viene riconosciuto.

### <a name="exercise-4"></a>Esercizio 4

Usare l'API di eseguire nuovamente il training del servizio con le stesse immagini all'app è l'analisi, pertanto, per rendere il più accurati (eseguire stime e contemporaneamente di training).
