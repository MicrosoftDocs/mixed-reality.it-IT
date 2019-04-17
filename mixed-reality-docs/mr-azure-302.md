---
title: MR e Azure 302 - visione artificiale
description: Completa questo corso per imparare a riconoscere contenuti visivi all'interno di un'immagine fornita, l'utilizzo di visione artificiale di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, visione artificiale, hololens, coinvolgenti, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597892"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR e Azure 302: Visione artificiale

In questo corso, si apprenderà come riconoscere contenuto visivo all'interno di un'immagine specificato, usando le funzionalità di visione artificiale di Azure in un'applicazione di realtà mista.

Risultati di riconoscimento verranno visualizzati come tag descrittivi. È possibile utilizzare questo servizio senza la necessità di eseguire il training di un modello di machine learning. Se l'implementazione richieda training modello di machine learning, vedere [MR e 302b Azure](mr-azure-302b.md).

![risultato di Lab](images/AzureLabs-Lab2-000.png)

La visione artificiale Microsoft è un set di API progettato per offrire agli sviluppatori con l'elaborazione di immagini e analisi (con restituiscono informazioni), utilizzando algoritmi avanzati, tutto dal cloud. Gli sviluppatori di caricare un'immagine o URL dell'immagine e gli algoritmi di API visione artificiale Microsoft analizzano il contenuto visivo, basato su input scelte utente, che quindi può restituire le informazioni, inclusi, che identifica il tipo e la qualità di un'immagine, rileva i visi umani ( Restituisce le coordinate) e l'assegnazione di tag, o classificazione di immagini. Per altre informazioni, visitare il [pagina API visione artificiale di Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Dopo aver completato il corso, si avrà una realtà mista applicazione HoloLens, che sarà in grado di eseguire le operazioni seguenti:

1.  Usa il gesto tocco, la camera e il HoloLens consente di acquisire un'immagine.
2.  L'immagine verrà inviato il Computer Vision API nel servizio di Azure. 
3.  Gli oggetti riconosciuti verranno elencati in un gruppo dell'interfaccia utente semplice posizionato nella scena Unity.

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> MR e Azure 302: Visione artificiale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla HoloLens, è inoltre possibile applicare informazioni in questo corso per auricolari (VR) coinvolgenti di realtà mista di Windows. Poiché immersive auricolari (VR) non è accessibile fotocamere, sarà necessario una fotocamera esterna connessa al PC. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare immersive auricolari (VR).

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
- Una fotocamera connessa al PC (per lo sviluppo visore VR immersivi)
- Accesso a Internet per la configurazione di Azure e il recupero delle API visione artificiale

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
2.  Configurare e testare l'HoloLens. Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova App per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente). 

Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Capitolo 1: il portale di Azure

Usare la *API visione artificiale* servizio in Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.

1.  Accedere prima di tutto per il [portale di Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *API visione artificiale*, fare clic su **invio**.

    ![Creare una nuova risorsa in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.
 
3.  La nuova pagina fornirà una descrizione del *API visione artificiale* servizio. AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![Informazioni sul servizio di computer vision api](images/AzureLabs-Lab2-01.png)
 
4.  Dopo avere fatto clic su **Create**:

    1. Inserire la posizione desiderata **nome** per questa istanza del servizio.
    2. Selezionare una **sottoscrizione**.
    3. Selezionare il **piano tariffario** appropriati per l'utente, se questo è il primo tempo nella creazione una *API visione artificiale* servizio, un livello gratuito (denominato F0) deve essere disponibile all'utente.
    4. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni). 

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinare il percorso per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

    6. È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.
    7. Fare clic su Crea.

        ![Informazioni sulla creazione del servizio](images/AzureLabs-Lab2-02.png)

5.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.
6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Vedere la nuova notifica per il nuovo servizio](images/AzureLabs-Lab2-03.png) 
 
7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Selezionare il pulsante di passare alla risorsa.](images/AzureLabs-Lab2-04.png)
 
8. Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Verrà visualizzata per la nuova istanza del servizio API visione artificiale. 

    ![Il nuovo servizio API visione artificiale](images/AzureLabs-Lab2-05.png)
 
9.  All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, questa operazione viene eseguita tramite chiave di sottoscrizione del servizio.
10. Dal *avvio rapido* pagina, delle *API visione artificiale* del servizio, passare al primo passaggio *individuare le chiavi*e fare clic su **chiavi** ( è possibile anche ottenere ciò scegliendo il collegamento blu chiavi, che si trova nel menu di spostamento dei servizi, indicato dall'icona della chiave). Il servizio verrà visualizzata *chiavi*.
11. Richiedere una copia di una delle chiavi visualizzate, in quanto sarà necessaria in un secondo momento nel progetto. 

12. Tornare al *introduttiva* pagina e da lì, recuperare l'endpoint. Tenere presente quelle in uso potrebbe essere diverso, in base al paese (che se si tratta, sarà necessario apportare una modifica al codice in un secondo momento). Eseguire una copia di questo endpoint per l'uso in un secondo momento:

    ![Il nuovo servizio API visione artificiale](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > È possibile controllare quali sono i diversi endpoint [qui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). 

## <a name="chapter-2--set-up-the-unity-project"></a>Capitolo 2: configurare il progetto Unity

Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **New**. 

    ![Avvio nuovo progetto Unity.](images/AzureLabs-Lab2-06.png)

2.  A questo punto, è necessario specificare un nome di progetto Unity. Inserire **MR_ComputerVision**. Verificare che il tipo di progetto è impostato su **3D**. Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![Fornire i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab2-07.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![Aggiornamento delle preferenze dell'editor di script.](images/AzureLabs-Lab2-08.png)

4.  Passare quindi ad **File > Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sui **commutatore piattaforma** pulsante per applicare la selezione.

    ![Crea finestra delle impostazioni, la piattaforma del commutatore alla piattaforma UWP.](images/AzureLabs-Lab2-10.png)

5.  Mentre si trovano ancora nella **File > Build Settings** e assicurarsi che:

    1. **Dispositivo di destinazione** è impostata su **HoloLens**

        > Per le cuffie coinvolgenti, impostare **dispositivo di destinazione** al *qualsiasi dispositivo*.

    2. **Tipo di compilazione** è impostata su **D3D**
    3. **SDK** è impostata su **installata più recente**
    4. **Versione di Visual Studio** è impostata su **installata più recente**
    5. **Compilare ed eseguire** è impostata su **computer locale**
    6. Salvare la scena e aggiungerlo alla compilazione.

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.
        
            ![Fare clic su Aggiungi pulsante Apri scene](images/AzureLabs-Lab2-11.png)

        2. Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![Crea nuova cartella scripts](images/AzureLabs-Lab2-12.png)

        3. Aprire appena creato **scene** cartella e quindi la *nome File*: campo di testo, digitare **MR_ComputerVisionScene**, quindi fare clic su **Salva** .

            ![Assegnare un nome nuova scena.](images/AzureLabs-Lab2-13.png)

            > Tenere presente, è necessario salvare le scene di Unity all'interno di *asset* cartella, come devono essere associate al progetto di Unity. Creare la cartella scene (e altre simili) è un modo tipico strutturare un progetto Unity.

    7. Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.

6. Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova. 

    ![Aprire le impostazioni del giocatore.](images/AzureLabs-Lab2-14.png)

7. In questo pannello, alcune impostazioni devono essere verificati:

    1. Nel **altre impostazioni** scheda:

        1. **Versione del Runtime di scripting** deve essere **stabile** (.NET 3.5 equivalente).
        2. **Back-end di scripting** deve essere **.NET**
        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![Aggiornare le altre impostazioni.](images/AzureLabs-Lab2-15.png)
      
    2. All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        1. **InternetClient**
        2. **Webcam**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab2-16.png)

    3. Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.

        ![Aggiornare le impostazioni di R X.](images/AzureLabs-Lab2-17.png)

8.  Nuovamente in *Build Settings* _Unity C#_  progetti non sono più è disattivata; selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Impostazioni di compilazione.
10. Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).

## <a name="chapter-3--main-camera-setup"></a>Capitolo 3: impostazione della fotocamera principale

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importarlo nel progetto come un [pacchetto personalizzato ](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 5](#chapter-5--create-the-resultslabel-class).

1.  Nel *Pannello di gerarchia*, selezionare la **Main Camera**. 
2.  Una volta selezionata, sarà possibile visualizzare tutti i componenti del **Main Camera** nel *Pannello di controllo*.

    1. Il **oggetto della fotocamera** devono essere denominati **Main Camera** (si noti l'ortografici!)
    2. Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici!)
    3. Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**
    4. Impostare **Cancella flag** al **colore a tinta unita** (ignorare questo visore VR immersivi).
    5. Impostare il **sfondo** colore del componente della fotocamera **nero, Alpha 0 (codice esadecimale: #00000000)** (ignorare questo visore VR immersivi).

        ![Aggiornare i componenti della fotocamera.](images/AzureLabs-Lab2-18.png)
 
3.  Successivamente, sarà necessario creare un oggetto semplice "Cursor" collegato al **Main Camera**, che aiutano a posizionare l'analisi delle immagini restituirà quando l'applicazione è in esecuzione. Questo cursore determinerà il punto centrale dello stato attivo della fotocamera.

Per creare il cursore:

1.  Nel *Pannello di gerarchia*, fare clic sui **Main Camera**. Sotto **oggetto 3D**, fare clic su **sfera**.

    ![Selezionare l'oggetto cursore.](images/AzureLabs-Lab2-19.png)
 
2.  Rinominare il **sfera** al **cursore** fare doppio clic sull'oggetto cursore o premere il tasto 'F2' con l'oggetto selezionato e assicurarsi che sia disponibile come elemento figlio del **Main Camera**.

3.  Nel *pannello gerarchia*, fare clic sulla **cursore**. Con il cursore selezionato, modificare le variabili seguenti nel *Pannello di controllo*:

    1. Impostare il *trasformare posizione* a **0, 0, 5**
    2. Impostare il *scalabilità* a **0,02, 0,02, 0,02**

        ![Aggiornare la posizione di trasformazione e la scala.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capitolo 4 – programma di installazione il sistema di etichetta

Dopo aver acquisito un'immagine con fotocamera degli HoloLens, tale immagine verrà inviato per il *API visione artificiale di Azure* istanza del servizio per l'analisi. 

I risultati dell'analisi sarà un elenco di oggetti riconosciuti denominati **tag**. 

Si userà le etichette (come un testo 3D nello spazio globale) per visualizzare questi tag in corrispondenza della posizione che è stata eseguita la foto.

I passaggi seguenti illustrano come configurare il **etichetta** oggetto.

1.  Fare doppio clic in un punto qualsiasi nella gerarchia di sezione del pannello (il percorso non è rilevante a questo punto), **oggetto 3D**, aggiungere un **testo 3D**. Denominarlo **LabelText**.

    ![Creare l'oggetto testo 3D.](images/AzureLabs-Lab2-21.png)
 
2.  Nel *pannello gerarchia*, fare clic sulla **LabelText**. Con il **LabelText** selezionato, modificare le variabili seguenti nel *Pannello di controllo*:

    1. Impostare il **posizione** a **0, 0,0**
    2. Impostare il **scalabilità** a **0,01, 0,01, 0,01**
    3. Nel componente **testo Mesh**:
    4. Sostituire tutto il testo all'interno **testo**, con "..."        
    5. Impostare il **ancoraggio** a **in mezzo al centro**
    6. Impostare il **allineamento** a **Center**
    7. Impostare il **Dimensione tabulazione** a **4**
    8. Impostare il **Font Size** a **50**
    9. Impostare il **colore** a **#FFFFFFFF**

    ![Componente di testo](images/AzureLabs-Lab2-21-5.png)

3.  Trascinare il **LabelText** dal *pannello gerarchia*, nel *cartella Asset*all'interno nel *progetto pannello*. In questo modo il **LabelText** un Prefab, in modo che non è possibile creare istanze nel codice.

    ![Crea un prefab dell'oggetto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  È consigliabile eliminare il **LabelText** dalle *gerarchia pannello*, in modo che non verrà visualizzato nella scena apertura. Quanto è diventato un prefab, che si chiamerà per le singole istanze dalla cartella Assets, non è necessario per contenerlo entro la scena. 
5.  La struttura dell'oggetto finale nel *gerarchia pannello* dovrebbe essere simile a quello illustrato nell'immagine seguente:

    ![Struttura finale del Pannello di gerarchia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capitolo 5: creare la classe ResultsLabel

È il primo script è necessario creare il *ResultsLabel* (classe), che è responsabile per le operazioni seguenti: 

- Creazione di etichette nello spazio complessivo appropriato, rispetto alla posizione della Camera.
- Visualizzare i tag da onerosa l'immagine.

Per creare questa classe: 

1.  Fare doppio clic nella *Pannello di progetto*, quindi **Crea > cartella**. Denominare la cartella **script**. 

    ![Crea cartella scripts.](images/AzureLabs-Lab2-24.png)

2.  Con il **script** cartella creare, fare doppio clic sopra per avviarlo. Quindi all'interno di tale cartella, pulsante destro del mouse e scegliere **Crea >** quindi  **C# Script**. Denominare lo script *ResultsLabel*. 

3.  Fare doppio clic su nuova *ResultsLabel* script per aprirlo con **Visual Studio**.

4.  All'interno della classe inserire il codice seguente nel *ResultsLabel* classe:

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

6.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.
7.  Nel *Editor di Unity*, fare clic e trascinare il *ResultsLabel* classe la **script** cartella in cui la **Main Camera** oggetto nel  *Pannello gerarchia*.
8.  Fare clic sui **Main Camera** ed esaminare le *Pannello di controllo*.

Si noterà dallo script che è stato appena trascinato nella fotocamera, sono presenti due campi: **Cursore** e **etichettare Prefab**.

9.  Trascinare l'oggetto chiamato **cursore** dalle *Pannello di gerarchia* allo slot denominato **cursore**, come illustrato nell'immagine seguente.
10. Trascinare l'oggetto chiamato **LabelText** dal *cartella Assets* nel *pannello progetto* allo slot denominato **etichetta Prefab**, come illustrato di immagine riportata di seguito. 

    ![Impostare gli obiettivi di riferimento all'interno di Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capitolo 6: creare la classe ImageCapture

La classe successiva si intende creare è il *ImageCapture* classe. Questa classe è responsabile per:

-   Acquisizione di un'immagine usando la fotocamera di HoloLens e archiviarlo nella cartella dell'App.
-   Movimenti tocco di acquisizione da parte dell'utente.

Per creare questa classe: 

1.  Andare alla **script** cartella creata in precedenza. 
2.  Pulsante destro del mouse all'interno della cartella **Crea > C# Script**. Chiamare lo script *ImageCapture*. 
3.  Fare doppio clic su nuova *ImageCapture* script per aprirlo con **Visual Studio**.
4.  Aggiungere spazi dei nomi seguenti all'inizio del file:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Quindi aggiungere le variabili seguenti all'interno di *ImageCapture* classe sopra il *Start ()* metodo:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
Il **tapsCount** variabile archivieranno il numero di movimenti di tocco acquisiti da parte dell'utente. Questo numero viene usato nella denominazione delle immagini acquisite.

6.  Codice per un *Awake()* e *Start ()* metodi deve ora essere aggiunto. Questi verranno chiamati quando inizializza la classe:

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

7.  Implementare un gestore che verrà chiamato quando si verifica un gesto tocco. 

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
 
Il *TapHandler()* metodo incrementa il numero di elementi di ritardo acquisiti da parte dell'utente e utilizza la posizione del cursore corrente per determinare dove posizionare una nuova etichetta.

Questo metodo chiama quindi il *ExecuteImageCaptureAndAnalysis()* metodo per avviare le funzionalità principali di questa applicazione.

8.  Dopo aver acquisita un'immagine ed archiviata, i seguenti gestori verranno chiamati. Se il processo ha esito positivo, il risultato viene passato per il *VisionManager* (che sono ancora da creare) per l'analisi.

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
 
9.  Aggiungere quindi il metodo che l'applicazione usa per avviare il processo di acquisizione di immagini e archiviare l'immagine.

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
> A questo punto si noterà un errore dei *pannello della Console dell'Editor Unity*. Infatti, il codice fa riferimento il *VisionManager* classe che verrà creato nel capitolo successivo.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capitolo 7: chiamata ad Azure e analisi delle immagini

È l'ultimo script è necessario creare il *VisionManager* classe. 

Questa classe è responsabile per:

-   Il caricamento dell'immagine più recente acquisito come una matrice di byte.
-   Matrice di byte da inviare le *API visione artificiale di Azure* istanza del servizio per l'analisi.
-   Ricezione della risposta come stringa JSON.
-   La deserializzazione della risposta e passando il tag risultante per il *ResultsLabel* classe.
 
Per creare questa classe:

1.  Fare doppio clic sui **script** cartella per aprirla. 
2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**. Denominare lo script *VisionManager*. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi affinché corrisponda al seguente, in cima il *VisionManager* classe:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  Nella parte superiore dello script, *all'interno* le *VisionManager* classe (sopra il *Start ()* metodo), è ora necessario creare due *classi* che rappresenta la risposta JSON deserializzata da Azure:

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
    > Il *TagData* e *AnalysedObject* classi devono avere la *[System.Serializable]* attributo aggiunto prima della dichiarazione per poter essere deserializzati con Unity librerie.

6.  Nella classe VisionManager, è necessario aggiungere le variabili seguenti:

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
    > Assicurarsi di inserire le **Authentication Key** nel **authorizationKey** variabile. Verrà annotati i **Authentication Key** all'inizio di questo corso [capitolo 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > Il **visionAnalysisEndpoint** variabile potrebbe essere diverso da quello specificato in questo esempio. Il **west-us** rigorosamente fa riferimento alle istanze del servizio create per l'area Stati Uniti occidentali. Aggiornarlo con il [URL dell'endpoint](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); di seguito sono riportati alcuni esempi di come potrebbe essere simile:
    > - Europa occidentale: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Asia sud-orientale: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Australia orientale: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Codice per Awake deve ora essere aggiunto. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Successivamente, aggiungere le coroutine (con il metodo statico flusso sotto di essa), che otterrà i risultati dell'analisi dell'immagine acquisita dal *ImageCapture* classe. 

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

9.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.
10. Indietro nell'Editor di Unity, fare clic e trascinare il *VisionManager* e *ImageCapture* classi il **script** cartella in cui il **Main Camera**dell'oggetto nel *Pannello di gerarchia*. 

## <a name="chapter-8--before-building"></a>Capitolo 8 – prima della compilazione

Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload di HoloLens.
Prima di procedere, verificare quanto segue:

-   Tutte le impostazioni indicate nella [capitolo 2](#chapter-2--set-up-the-unity-project) siano impostate correttamente. 
-   Tutti gli script associati per il **Main Camera** oggetto. 
-   Tutti i campi di *Pannello controllo fotocamera principale* vengono assegnati in modo corretto.
-   Assicurarsi di inserire le **Authentication Key** nel **authorizationKey** variabile.
-   Assicurarsi di aver anche selezionato l'endpoint *VisionManager* script e che si allinei alla *il* area (questo documento usa *west-us* per impostazione predefinita).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capitolo 9: compilare la soluzione di piattaforma UWP e trasferire localmente l'applicazione
Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.

1.  Passare a *impostazioni di compilazione* - **File > Impostazioni di compilazione...**
2.  Dal *Build Settings* finestra, fare clic su **compilazione**.

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab2-26.png)

3.  Se non è già, graduazione **Unity C# progetti**.
4.  Fai clic su **Compila**. Unity avvierà una *Esplora File* finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in. Creare ora tale cartella e denominarlo *App*. Quindi con il *App* cartella selezionata, premere **Seleziona cartella**. 
5.  Unity verrà avviata la compilazione del progetto per la *App* cartella. 
6.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un *Esplora File* finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).

## <a name="chapter-10--deploy-to-hololens"></a>Il capitolo 10-distribuire a HoloLens

Per distribuire in HoloLens:

1.  È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore**. A tale scopo, effettuare le seguenti operazioni:

    1. Durante l'uso di HoloLens, aprire il **impostazioni**.
    2. Passare a **rete e Internet > Wi-Fi > Opzioni avanzate**
    3. Si noti il **IPv4** indirizzo.
    4. Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza > per gli sviluppatori** 
    5. Attivare la modalità sviluppatore.

2.  Passare alla nuova build Unity (le *App* cartella) e aprire il file di soluzione con *Visual Studio*.
3.  Selezione configurazione di soluzione **Debug**.
4.  La piattaforma della soluzione, selezionare **x86**, **computer remoto**. 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Andare alla **dal menu Compila** e fare clic su **Distribuisci soluzione**, trasferire localmente l'applicazione di HoloLens.
6.  L'App deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.

> [!NOTE]
> Per distribuire visore VR immersivi, impostare il **piattaforma soluzione** al *computer locale*e impostare il **configurazione** a *Debug*, con *x86* come la **piattaforma**. Quindi distribuire in locale del computer, utilizzando il **dal menu Compila**, selezionando *Distribuisci soluzione*. 

## <a name="your-finished-computer-vision-api-application"></a>L'applicazione API visione artificiale completata

Complimenti, è stata compilata un'app per realtà mista che sfrutta l'API visione artificiale di Azure per riconoscere gli oggetti reali e visualizzare la fiducia di ciò che è stato individuato.

![risultato di Lab](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Esattamente come è stato usato il *tag* parametro (come evidenziato all'interno del *endpoint* utilizzati all'interno di *VisionManager*), estendere l'app per rilevare altre informazioni, esaminare quali altri parametri che è possibile utilizzare [qui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).

### <a name="exercise-2"></a>Esercizio 2

Visualizzare i dati di Azure restituiti, in modo più colloquiale e leggibile, ad esempio nascondendo i numeri. Come se un bot potrebbe essere riprodotta la voce all'utente.
