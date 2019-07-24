---
title: MR e Azure 302-visione artificiale
description: Completare questo corso per apprendere come riconoscere il contenuto visivo in un'immagine fornita, usando Azure Visione artificiale in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, visione artificiale, hololens, immersiva, VR
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63552144"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR e Azure 302: Visione artificiale

In questo corso si apprenderà come riconoscere il contenuto visivo in un'immagine fornita, usando le funzionalità di Visione artificiale di Azure in un'applicazione di realtà mista.

I risultati del riconoscimento verranno visualizzati come tag descrittivi. È possibile usare questo servizio senza dover eseguire il training di un modello di machine learning. Se l'implementazione richiede il training di un modello di apprendimento automatico, vedere [Mr e Azure 302B](mr-azure-302b.md).

![risultato Lab](images/AzureLabs-Lab2-000.png)

Microsoft Visione artificiale è un set di API progettate per fornire agli sviluppatori l'elaborazione e l'analisi delle immagini (con informazioni di ritorno), usando algoritmi avanzati, dal cloud. Gli sviluppatori caricano un URL di immagine o immagine e gli algoritmi di Microsoft API Visione artificiale analizzano il contenuto visivo, in base agli input scelti dall'utente, che possono quindi restituire informazioni, tra cui l'identificazione del tipo e della qualità di un'immagine, il rilevamento dei visi umani ( la restituzione delle coordinate), l'assegnazione di tag o la categorizzazione di immagini. Per ulteriori informazioni, visitare la [pagina API visione artificiale di Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Dopo aver completato questo corso, si disporrà di un'applicazione HoloLens in realtà mista, che sarà in grado di eseguire le operazioni seguenti:

1.  Usando il gesto Tap, la fotocamera del HoloLens acquisirà un'immagine.
2.  L'immagine verrà inviata al servizio API Visione artificiale di Azure. 
3.  Gli oggetti riconosciuti saranno elencati in un gruppo di interfaccia utente semplice posizionato nella scena Unity.

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 302: Visione artificiale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente su HoloLens, è anche possibile applicare le informazioni apprese in questo corso agli auricolari per la realtà mista (VR) di Windows. Poiché le cuffie immersive (VR) non hanno fotocamere accessibili, sarà necessaria una fotocamera esterna connessa al PC. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare gli auricolari immersivi (VR).

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
- Una fotocamera connessa al PC (per lo sviluppo di auricolari immersivi)
- Accesso a Internet per il programma di installazione di Azure e il recupero API Visione artificiale

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente. 

Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Capitolo 1: portale di Azure

Per usare il servizio *API visione artificiale* in Azure, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.

1.  Per prima cosa, accedere al [portale di Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *API visione artificiale*e premere **invio**.

    ![Creare una nuova risorsa in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.
 
3.  La nuova pagina fornirà una descrizione del servizio *API visione artificiale* . Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![Informazioni sul servizio API visione artificiale](images/AzureLabs-Lab2-01.png)
 
4.  Una volta fatto clic su **Crea**:

    1. Inserire il **nome** desiderato per l'istanza del servizio.
    2. Selezionare una **sottoscrizione**.
    3. Selezionare il  piano tariffario appropriato. se è la prima volta che si crea un servizio di *API visione artificiale* , è necessario che sia disponibile un livello gratuito (denominato F0).
    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune). 

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinare il percorso del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

    6. Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.
    7. Fare clic su Crea.

        ![Informazioni sulla creazione del servizio](images/AzureLabs-Lab2-02.png)

5.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.
6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Visualizza la nuova notifica per il nuovo servizio](images/AzureLabs-Lab2-03.png) 
 
7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Selezionare il pulsante Vai alla risorsa.](images/AzureLabs-Lab2-04.png)
 
8. Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio API Visione artificiale. 

    ![Il nuovo servizio API Visione artificiale](images/AzureLabs-Lab2-05.png)
 
9.  All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita usando la chiave di sottoscrizione del servizio.
10. Dalla pagina *avvio rapido* del servizio *API visione artificiale* , passare al primo passaggio, selezionare le *chiavi*e fare clic su **chiavi** . a tale scopo, fare clic sui tasti di collegamento ipertestuale blu disponibili nel menu di navigazione servizi, indicato dall'icona della chiave). Le *chiavi*del servizio vengono rivelate.
11. Eseguire una copia di una delle chiavi visualizzate, perché sarà necessario in un secondo momento nel progetto. 

12. Tornare alla pagina *avvio rapido* e, da qui, recuperare l'endpoint. Tenere presente che l'utente può essere diverso, a seconda dell'area geografica (in questo caso, sarà necessario apportare una modifica al codice in un secondo momento). Eseguire una copia di questo endpoint per usarlo in seguito:

    ![Il nuovo servizio API Visione artificiale](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > È possibile controllare quali sono i vari [endpoint.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) 

## <a name="chapter-2--set-up-the-unity-project"></a>Capitolo 2: configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire *Unity* e fare clic su **New**. 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab2-06.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity. Inserire **MR_ComputerVision**. Verificare che il tipo di progetto sia impostato su **3D**. Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab2-07.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **Modifica preferenze >** e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![Aggiornare la preferenza dell'editor di script.](images/AzureLabs-Lab2-08.png)

4.  Passare quindi a **File > impostazioni di compilazione** e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.

    ![Finestra impostazioni di compilazione, passa alla piattaforma UWP.](images/AzureLabs-Lab2-10.png)

5.  Sempre in **File > impostazioni di compilazione** e verificare che:

    1. Il **dispositivo di destinazione** è impostato su **HoloLens**

        > Per gli auricolari immersivi, impostare **dispositivo di destinazione** su *qualsiasi dispositivo*.

    2. Il **tipo di compilazione** è impostato su **D3D**
    3. **SDK** è impostato sull' **ultima versione installata**
    4. La **versione di Visual Studio** è impostata su **installazione più recente**
    5. **Compilazione ed esecuzione** è impostato su **computer locale**
    6. Salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.
        
            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab2-11.png)

        2. Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.

            ![Crea nuova cartella script](images/AzureLabs-Lab2-12.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **MR_ComputerVisionScene**e quindi fare clic su **Salva**.

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab2-13.png)

            > Tenere presente che è necessario salvare le scene Unity all'  interno della cartella assets, in quanto devono essere associate al progetto Unity. La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.

    7. Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.

6. Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* . 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab2-14.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **altre impostazioni** :

        1. La **versione di runtime** di scripting deve essere **stabile** (equivalente a .NET 3,5).
        2. Il **back-end** di scripting deve essere **.NET**
        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab2-15.png)
      
    2. Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        1. **InternetClient**
        2. **Webcam**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab2-16.png)

    3. Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![Aggiornare le impostazioni X R.](images/AzureLabs-Lab2-17.png)

8.  Nelle *impostazioni di compilazione* i progetti _Unity C#_  non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra impostazioni di compilazione.
10. Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).

## <a name="chapter-3--main-camera-setup"></a>Capitolo 3-configurazione della fotocamera principale

> [!IMPORTANT]
> Se si desidera ignorare il componente *di configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricarlo [. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importarlo nel progetto come [pacchetto personalizzato](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 5](#chapter-5--create-the-resultslabel-class).

1.  Nel *Pannello gerarchia*selezionare la **fotocamera principale**. 
2.  Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel *Pannello di controllo*.

    1. L' **oggetto fotocamera** deve essere denominato **Main camera** (nota l'ortografia).
    2. Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (si noti l'ortografia).
    3. Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**
    4. Impostare **Cancella flag** su **colore a tinta unita** (ignorarlo per l'auricolare immersivo).
    5. Imposta il colore di **sfondo** del componente della fotocamera su **nero, alfa 0 (codice esadecimale: #00000000)** (ignorarlo per l'auricolare immersivo).

        ![Aggiornare i componenti della fotocamera.](images/AzureLabs-Lab2-18.png)
 
3.  Sarà quindi necessario creare un oggetto "Cursor" semplice collegato alla **fotocamera principale**, che consentirà di posizionare l'output dell'analisi dell'immagine quando l'applicazione è in esecuzione. Questo cursore determina il punto centrale dello stato attivo della fotocamera.

Per creare il cursore:

1.  Nel *Pannello gerarchia*, fare clic con il pulsante destro del mouse sulla **fotocamera principale**. In **oggetto 3D**fare clic su **sfera**.

    ![Selezionare l'oggetto cursore.](images/AzureLabs-Lab2-19.png)
 
2.  Rinominare la **sfera** in **cursore** (fare doppio clic sull'oggetto cursore o premere il pulsante della tastiera "F2" con l'oggetto selezionato) e verificare che sia posizionato come figlio della **fotocamera principale**.

3.  Nel *Pannello gerarchia*, fare clic sul **cursore**. Con il cursore selezionato, modificare le variabili seguenti nel *Pannello di controllo*:

    1. Impostare la *posizione di trasformazione* su **0, 0, 5**
    2. Impostare la *scala* su **0,02, 0,02, 0,02**

        ![Aggiornare la posizione e la scala della trasformazione.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capitolo 4: configurare il sistema di etichette

Una volta acquisita un'immagine con la fotocamera HoloLens, tale immagine verrà inviata all'istanza del servizio *API visione artificiale di Azure* per l'analisi. 

I risultati di tale analisi saranno un elenco di oggetti riconosciuti chiamati **tag**. 

Si useranno le etichette (come testo 3D nello spazio globale) per visualizzare questi tag nella posizione in cui è stata eseguita la foto.

Nei passaggi seguenti viene illustrato come configurare l'oggetto **Label** .

1.  Fare clic con il pulsante destro del mouse in un punto qualsiasi del pannello gerarchia (il percorso non è rilevante a questo punto), in **oggetto 3D**, aggiungere un **testo 3D**. Denominarlo **LabelText**.

    ![Crea oggetto testo 3D.](images/AzureLabs-Lab2-21.png)
 
2.  Nel *Pannello gerarchia*fare clic su **LabelText**. Con **LabelText** selezionato, modificare le variabili seguenti nel pannello di *controllo*:

    1. Imposta la **posizione** su **0, 0, 0**
    2. Impostare la **scala** su **0,01, 0,01, 0,01**
    3. Nella mesh del **testo**del componente:
    4. Sostituire tutto il testo all'interno del **testo**con "..."        
    5. Imposta l' **ancoraggio** sul **centro centrale**
    6. Impostare l' **allineamento** al **centro**
    7. Imposta la **dimensione** della tabulazione su **4**
    8. Imposta la **dimensione del carattere** su **50**
    9. Imposta il **colore** su **#FFFFFFFF**

    ![Componente testo](images/AzureLabs-Lab2-21-5.png)

3.  Trascinare **LabelText** dal *Pannello gerarchia*, nella *cartella Asset*, all'interno del *Pannello Project*. In questo modo, **LabelText** viene creato un prefabbricato, in modo che sia possibile crearne un'istanza nel codice.

    ![Creare una prefabbricata dell'oggetto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  È necessario eliminare il **LabelText** dal *Pannello gerarchia*, in modo che non venga visualizzato nella scena di apertura. Poiché è ora un prefabbricato, che verrà chiamato per le singole istanze dalla cartella assets, non è necessario mantenerlo all'interno della scena. 
5.  La struttura dell'oggetto finale nel *Pannello gerarchia* deve essere simile a quella illustrata nell'immagine seguente:

    ![Struttura finale del pannello gerarchia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capitolo 5: creare la classe ResultsLabel

Il primo script che è necessario creare è la classe *ResultsLabel* , responsabile delle operazioni seguenti: 

- Creazione delle etichette nello spazio globale appropriato rispetto alla posizione della camera.
- Visualizzazione dei tag dall'immagine onerosa.

Per creare questa classe: 

1.  Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare > cartella**. Denominare gli **script**della cartella. 

    ![Crea cartella script.](images/AzureLabs-Lab2-24.png)

2.  Con la  cartella Scripts create, fare doppio clic su di essa per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse e selezionare **Crea >** quindi  **C# script**. Denominare lo script *ResultsLabel*. 

3.  Fare doppio clic sul nuovo script *ResultsLabel* per aprirlo con **Visual Studio**.

4.  All'interno della classe, inserire il codice seguente nella classe *ResultsLabel* :

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.
7.  Nell'editor di *Unity*fare clic e trascinare la classe *ResultsLabel* dalla cartella **Scripts** all'oggetto **principale della fotocamera** nel *Pannello gerarchia*.
8.  Fare clic sulla **fotocamera principale** ed esaminare il *pannello Inspector*.

Si noterà che dallo script appena trascinato nella fotocamera sono presenti due campi: Prefabbricato **Cursor** e **Label**.

9.  Trascinare l'oggetto denominato **cursore** dal *Pannello gerarchia* nello slot denominato **Cursor**, come illustrato nell'immagine seguente.
10. Trascinare l'oggetto denominato **LabelText** dalla *cartella assets* nel *Pannello Project* allo slot denominato label prefabric, come illustrato nell'immagine seguente. 

    ![Impostare le destinazioni di riferimento all'interno di Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capitolo 6: creare la classe ImageCapture

La classe successiva che si intende creare è la classe *ImageCapture* . Questa classe è responsabile di:

-   Acquisizione di un'immagine con la fotocamera HoloLens e relativa archiviazione nella cartella dell'app.
-   Acquisizione dei movimenti Tap dall'utente.

Per creare questa classe: 

1.  Passare alla cartella **Scripts** creata in precedenza. 
2.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi **creare > C# script**. Chiamare lo script *ImageCapture*. 
3.  Fare doppio clic sul nuovo script *ImageCapture* per aprirlo con **Visual Studio**.
4.  Aggiungere i seguenti spazi dei nomi all'inizio del file:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe *ImageCapture* , sopra il metodo *Start ()* :

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
Nella variabile **tapsCount** viene archiviato il numero di movimenti Tap acquisiti dall'utente. Questo numero viene usato per la denominazione delle immagini acquisite.

6.  È ora necessario aggiungere il codice per i metodi *svegli ()* e *Start ()* . Questi verranno chiamati quando la classe inizializza:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementare un gestore che verrà chiamato quando si verifica un movimento tap. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
Il metodo *TapHandler ()* incrementa il numero di rubinetti acquisiti dall'utente e utilizza la posizione corrente del cursore per determinare la posizione in cui posizionare una nuova etichetta.

Questo metodo chiama quindi il metodo *ExecuteImageCaptureAndAnalysis ()* per avviare la funzionalità di base di questa applicazione.

8.  Una volta acquisita e archiviata un'immagine, verranno chiamati i gestori seguenti. Se il processo ha esito positivo, il risultato viene passato a *VisionManager* (che è ancora necessario creare) per l'analisi.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  Aggiungere quindi il metodo usato dall'applicazione per avviare il processo di acquisizione dell'immagine e archiviare l'immagine.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> A questo punto si noterà un errore nel *Pannello console dell'editor*di Unity. Questo perché il codice fa riferimento alla classe *VisionManager* che verrà creata nel capitolo successivo.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capitolo 7-chiamata ad Azure e analisi delle immagini

L'ultimo script che è necessario creare è la classe *VisionManager* . 

Questa classe è responsabile di:

-   Caricamento dell'immagine più recente acquisita come matrice di byte.
-   Invio della matrice di byte all'istanza del servizio *API visione artificiale di Azure* per l'analisi.
-   Ricezione della risposta come stringa JSON.
-   Deserializzazione della risposta e passaggio dei tag risultanti alla classe *ResultsLabel* .
 
Per creare questa classe:

1.  Fare doppio clic sulla  cartella Scripts per aprirla. 
2.  Fare clic con il pulsante  destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**. Denominare lo script *VisionManager*. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi in modo che corrispondano a quelli riportati di seguito, all'inizio della classe *VisionManager* :

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  All'inizio dello script, *all'interno* della classe *VisionManager* (sopra il metodo *Start ()* ), è ora necessario creare due *classi* che rappresenteranno la risposta JSON deserializzata da Azure:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > Le classi *TagData* e *AnalysedObject* devono avere l'attributo *[System. Serializable]* aggiunto prima della dichiarazione per poter essere deserializzato con le librerie di Unity.

6.  Nella classe VisionManager è necessario aggiungere le variabili seguenti:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Assicurarsi di inserire la **chiave di autenticazione** nella variabile **authorizationKey** . Si noterà che la **chiave di autenticazione** è stata annotata all'inizio di questo corso, [capitolo 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > La variabile **visionAnalysisEndpoint** potrebbe essere diversa da quella specificata in questo esempio. Gli **Stati Uniti occidentali** si riferiscono esclusivamente alle istanze del servizio create per l'area Stati Uniti occidentali. Aggiornarlo con l' [URL dell'endpoint](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). di seguito sono riportati alcuni esempi di ciò che potrebbe essere simile al seguente:
    > - Europa occidentale:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Asia sudorientale:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Australia orientale:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  È necessario aggiungere il codice per l'ora di riattivazione. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Aggiungere quindi la coroutine (con il metodo del flusso statico sotto di essa), che otterrà i risultati dell'analisi dell'immagine acquisita dalla classe *ImageCapture* . 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.
10. Nell'editor di Unity fare clic e trascinare le classi *VisionManager* e *ImageCapture* dalla cartella **Scripts** all'oggetto **principale della fotocamera** nel *Pannello gerarchia*. 

## <a name="chapter-8--before-building"></a>Capitolo 8-prima della compilazione

Per eseguire un test completo dell'applicazione, è necessario sideload nel HoloLens.
Prima di procedere, verificare quanto segue:

-   Tutte le impostazioni indicate nel [capitolo 2](#chapter-2--set-up-the-unity-project) sono impostate correttamente. 
-   Tutti gli script sono collegati all'oggetto **principale della fotocamera** . 
-   Tutti i campi nel *pannello principale di controllo della fotocamera* sono assegnati correttamente.
-   Assicurarsi di inserire la **chiave di autenticazione** nella variabile **authorizationKey** .
-   Assicurarsi di aver controllato anche l'endpoint nello script *VisionManager* e che sia allineato *all'area* geografica (in questo documento vengono usati *Stati Uniti occidentali* per impostazione predefinita).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capitolo 9: compilare la soluzione UWP e sideload l'applicazione
Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.

1.  Passare al file *delle impostazioni* - di compilazione **> impostazioni di compilazione...**
2.  Nella finestra *impostazioni di compilazione* fare clic su **Compila**.

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab2-26.png)

3.  Se non è già stato fatto, è necessario che i **progetti C# Unity**
4.  Fai clic su **Compila**. Unity avvierà una finestra di *Esplora file* , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella adesso e denominarla *app*. Quindi, con la cartella dell' *app* selezionata, fare clic su **Seleziona cartella**. 
5.  Unity inizierà a compilare il progetto nella cartella dell' *app* . 
6.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra *Esplora file* nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).

## <a name="chapter-10--deploy-to-hololens"></a>Capitolo 10: eseguire la distribuzione in HoloLens

Per eseguire la distribuzione in HoloLens:

1.  È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore**. A tale scopo, effettuare le seguenti operazioni:

    1. Quando si indossa il HoloLens, aprire le **Impostazioni**.
    2. Passare a **rete & Internet > opzioni avanzate Wi-Fi >**
    3. Prendere nota dell'indirizzo **IPv4** .
    4. Quindi, tornare a **Settings (impostazioni**) e quindi **aggiornare & Security > per gli sviluppatori** 
    5. Impostare la modalità di sviluppo su.

2.  Passare alla nuova compilazione Unity (cartella *app* ) e aprire il file della soluzione con *Visual Studio*.
3.  Nella configurazione della soluzione selezionare **debug**.
4.  Nella piattaforma soluzione selezionare **x86**, **computer remoto**. 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione**per sideload l'applicazione in HoloLens.
6.  L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.

> [!NOTE]
> Per eseguire la distribuzione in un dispositivo headset immersivo, impostare la **piattaforma della soluzione** su *computer locale*e impostare la **configurazione** su *debug*, con *x86* come **piattaforma**. Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*. 

## <a name="your-finished-computer-vision-api-application"></a>Applicazione API Visione artificiale completata

Congratulazioni, è stata creata un'app per realtà mista che sfrutta la API Visione artificiale di Azure per riconoscere gli oggetti reali e visualizzare la confidenza di ciò che è stato visto.

![risultato Lab](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Così come è stato usato il parametro *Tags* (come evidenziato all'interno dell' *endpoint* usato in *VisionManager*), estendere l'app per rilevare altre informazioni; esaminare gli altri parametri a cui si ha [accesso.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)

### <a name="exercise-2"></a>Esercizio 2

Visualizza i dati di Azure restituiti, in modo più colloquiale e leggibile, forse nascondendo i numeri. Come se un bot potesse parlare con l'utente.
