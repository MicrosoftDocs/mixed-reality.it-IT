---
title: MR e Azure 304-riconoscimento facciale
description: Completa questo corso per apprendere come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, riconoscimento viso, hololens, immersive, VR
ms.openlocfilehash: ef75be5485f85538eb8b3db3eebec63b166f7aa3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438500"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR e Azure 304: riconoscimento viso

![risultato del completamento del corso](images/AzureLabs-Lab4-00.png)

In questo corso si apprenderà come aggiungere funzionalità di riconoscimento viso a un'applicazione di realtà mista usando servizi cognitivi di Azure con Microsoft API Viso.

*Azure API viso* è un servizio Microsoft, che fornisce agli sviluppatori gli algoritmi volti più avanzati, tutto nel cloud. Il *API viso* dispone di due funzioni principali: il rilevamento viso con attributi e il riconoscimento viso. In questo modo gli sviluppatori possono semplicemente impostare un set di gruppi per i visi e quindi inviare immagini di query al servizio in un secondo momento, per determinare a chi appartiene un viso. Per ulteriori informazioni, visitare la [pagina Azure Face Recognition](https://azure.microsoft.com/services/cognitive-services/face/).

Dopo aver completato questo corso, si disporrà di un'applicazione HoloLens in realtà mista, che sarà in grado di eseguire le operazioni seguenti:

1. Usare un **movimento Tap** per avviare l'acquisizione di un'immagine usando la fotocamera HoloLens a bordo. 
2. Inviare l'immagine acquisita al servizio *API viso di Azure* .
3. Ricevere i risultati dell'algoritmo di *API viso* .
4. Utilizzare un'interfaccia utente semplice per visualizzare il nome delle persone corrispondenti.

In questo modo verrà illustrato come ottenere i risultati dal servizio API Viso nell'applicazione di realtà mista basata su Unity.

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 304: riconoscimento viso</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente su HoloLens, è anche possibile applicare le informazioni apprese in questo corso agli auricolari per la realtà mista (VR) di Windows. Poiché le cuffie immersive (VR) non hanno fotocamere accessibili, sarà necessaria una fotocamera esterna connessa al PC. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare gli auricolari immersivi (VR).

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018). È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](install-the-tools.md)
- [Windows 10 SDK più recente](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Un [headset di Windows misto reality immersiv (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata
- Una fotocamera connessa al PC (per lo sviluppo di auricolari immersivi)
- Accesso a Internet per il programma di installazione di Azure e il recupero API Viso

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente. 

Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1-portale di Azure

Per usare il servizio *API viso* in Azure, sarà necessario configurare un'istanza del servizio da rendere disponibile per l'applicazione.

1.  Per prima cosa, accedere al [portale di Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *API viso*, quindi premere **invio**.

    ![Cerca API viso](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

3.  La nuova pagina fornirà una descrizione del servizio *API viso* . Nella parte inferiore sinistra di questo prompt selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![informazioni sull'API viso](images/AzureLabs-Lab4-02.png)

4.  Una volta fatto clic su **Crea**:

    1. Inserire il nome desiderato per l'istanza del servizio.

    2. Selezionare una sottoscrizione.

    3. Selezionare il piano tariffario appropriato. se è la prima volta che si crea un *servizio di API viso*, è necessario che sia disponibile un livello gratuito (denominato F0).

    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune). 

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. L'app UWP, **persona Maker**, che viene usata in un secondo momento, richiede l'uso di "Stati Uniti occidentali" per la località.

    6. Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.

    7. Selezionare **Crea *.**

        ![Crea servizio API viso](images/AzureLabs-Lab4-03.png)

5.  Una volta fatto clic su **Crea *,** sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![notifica di creazione del servizio](images/AzureLabs-Lab4-04.png)

7.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![passa a notifica risorse](images/AzureLabs-Lab4-05.png)

8.  Quando si è pronti, fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.

    ![chiavi API della faccia di accesso](images/AzureLabs-Lab4-06.png)

9.  All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione che viene eseguita tramite l'uso della sottoscrizione ' Key ' del servizio. Dalla pagina *avvio rapido* del servizio *API viso* , il primo punto è il numero 1, per recuperare *le chiavi.*

10. Nella pagina del *servizio* selezionare il collegamento ipertestuale **chiavi** blu (se nella pagina avvio rapido) o il collegamento **chiavi** nel menu di navigazione servizi (a sinistra, indicato dall'icona "chiave"), per rivelare le chiavi.

    > [!NOTE] 
    > Prendere nota di una delle chiavi e proteggerla, perché sarà necessaria in un secondo momento.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capitolo 2-uso dell'applicazione UWP ' person Maker '

Assicurarsi di scaricare l'applicazione UWP predefinita denominata [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Questa app non è il prodotto finale per questo corso, ma solo uno strumento che consente di creare le voci di Azure su cui si basa il progetto successivo.

**Persona Maker** consente di creare voci di Azure, associate a utenti e gruppi di utenti. L'applicazione inserisce tutte le informazioni necessarie in un formato che può essere usato in un secondo momento da FaceAPI, in modo da riconoscere i visi degli utenti che sono stati aggiunti. 

> IMPORTANTE La **persona Maker** usa alcune limitazioni di base per garantire che il numero di chiamate al servizio al minuto per il **livello di abbonamento gratuito**non venga superato. Il testo verde nella parte superiore verrà modificato in rosso e verrà aggiornato come ' ACTIVE ' quando si verifica la limitazione; in tal caso, è sufficiente attendere che l'applicazione continui ad accedere al servizio face, aggiornando come ' IN-ACTIVE ' quando è possibile riutilizzarla.

Questa applicazione usa le librerie *Microsoft. ProjectOxford. Face* che consentono di sfruttare al meglio le API viso. Questa libreria è disponibile gratuitamente come pacchetto NuGet. Per altre informazioni su questo e sulle API simili, vedere [l'articolo di riferimento sulle API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Questi sono solo i passaggi necessari. le istruzioni su come eseguire queste operazioni sono più avanti nel documento. L'app **Person Maker** consentirà di:
>
> - Creare un *gruppo*di persone, ovvero un gruppo composto da più persone a cui si desidera associarlo. Con l'account Azure è possibile ospitare più gruppi di persone.
>
> - Creare una *persona*, che è un membro di un gruppo di persone. Ogni persona ha un certo numero di immagini *facciali* associate.
>
> -  Assegnare le *Immagini facciali* a una *persona*per consentire al servizio API viso di Azure di riconoscere una *persona* con la *faccia*corrispondente.
>
> -  Eseguire il *Training* del *servizio API viso di Azure*.

Tenere presente che, per eseguire il training dell'app in modo che riconosca le persone, saranno necessarie dieci (10) foto di primo piano di ogni persona che si desidera aggiungere al gruppo di persone. L'app di Windows 10 CAM può aiutarti a eseguire queste app. È necessario assicurarsi che ogni foto sia chiara (evitare la sfocatura, l'oscuramento o la distanza dal soggetto), avere la foto in formato di file jpg o PNG, con le dimensioni del file di immagine non maggiori di **4 MB**e non inferiori a **1 KB**.

> [!NOTE]
> Se si segue questa esercitazione, non usare il proprio viso per il training, come quando si inserisce il HoloLens, non è possibile esaminare se stessi. Usare la faccia di un collega o di un altro studente.

**Autore della persona**che esegue:

1.  Aprire la cartella **PersonMaker** e fare doppio clic sulla *soluzione PersonMaker* per aprirla con *Visual Studio*.

2.  Dopo aver aperto la *soluzione PersonMaker* , verificare che:

    1. La *configurazione della soluzione* è impostata su **debug**.

    2. La *piattaforma della soluzione* è impostata su **x86**

    3. La *piattaforma di destinazione* è il **computer locale**.

    4.  Potrebbe anche essere necessario *ripristinare i pacchetti NuGet* facendo clic con il pulsante destro del mouse sulla *soluzione* e selezionando **Ripristina pacchetti NuGet**.

3.  Fare clic su *computer locale* e l'applicazione viene avviata. Tenere presente che, su schermi più piccoli, tutto il contenuto potrebbe non essere visibile, anche se è possibile scorrere ulteriormente verso il basso per visualizzarlo.

    ![interfaccia utente di PERSON Maker](images/AzureLabs-Lab4-07.png)

4.  Inserire la **chiave di autenticazione di Azure**, che dovrebbe essere disponibile, dal servizio *API viso* in Azure.

5.  Inserire

    1. *ID* da assegnare al *gruppo person*. L'ID deve essere minuscolo, senza spazi. Prendere nota di questo ID, perché sarà necessario in un secondo momento nel progetto Unity.
    2. *Nome* che si desidera assegnare al *gruppo person* (può contenere spazi).


6.  Premere il pulsante **Crea gruppo di persone** . Sotto il pulsante verrà visualizzato un messaggio di conferma.

> [!NOTE]
> Se si verifica un errore di accesso negato, controllare il percorso impostato per il servizio di Azure. Come indicato in precedenza, questa app è progettata per "Stati Uniti occidentali".

> [!IMPORTANT]
> Si noterà che è possibile anche fare clic sul pulsante **Recupera un gruppo noto** , ovvero se è già stato creato un gruppo di persone e si desidera utilizzarlo, anziché crearne uno nuovo. Tenere presente che, se si fa clic su *Crea un gruppo di persone* con un gruppo noto, viene recuperato anche un gruppo.

7.  Inserire il *nome* della *persona* che si desidera creare.

    1. Fare clic sul pulsante **Crea persona** .

    2. Sotto il pulsante verrà visualizzato un messaggio di conferma.

    3. Se si desidera eliminare una persona creata in precedenza, è possibile scrivere il nome nella casella di testo e premere **Canc person** .

8.  Assicurarsi di avere la posizione di dieci (10) foto della persona che si vuole aggiungere al gruppo.

9.  Premere **Crea e Apri cartella** per aprire Esplora risorse e la cartella associata alla persona. Aggiungere le dieci (10) immagini nella cartella. Il formato del file deve essere *jpg* o *png* .

10. Fare clic su **Invia ad Azure**. Un contatore indicherà lo stato dell'invio, seguito da un messaggio al termine dell'operazione.

11. Una volta completato il contatore e visualizzato un messaggio di conferma, fare clic su **Training** per eseguire il training del servizio.

Al termine del processo, si è pronti per passare a Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3: configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire *Unity* e fare clic su **New**. 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab4-08.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity. Inserire **MR_FaceRecognition**. Verificare che il tipo di progetto sia impostato su **3D**. Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab4-09.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **Modifica preferenze >** e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![Aggiornare la preferenza dell'editor di script.](images/AzureLabs-Lab4-10.png)

4.  Passare quindi a **File > impostazioni di compilazione** e impostare la piattaforma su **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .

    ![Finestra impostazioni di compilazione, passa alla piattaforma UWP.](images/AzureLabs-Lab4-11.png)

5.  Passare a **File > impostazioni di compilazione** e verificare che:

    1. Il **dispositivo di destinazione** è impostato su **HoloLens**

        > Per gli auricolari immersivi, impostare **dispositivo di destinazione** su *qualsiasi dispositivo*.

    2. Il **tipo di compilazione** è impostato su **D3D**
    3. **SDK** è impostato sull' **ultima versione installata**
    4. La **versione di Visual Studio** è impostata su **installazione più recente**
    5. **Compilazione ed esecuzione** è impostato su **computer locale**
    6. Salvare la scena e aggiungerla alla compilazione. 

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.

            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab4-12.png)

        2. Selezionare il pulsante **nuova cartella** per creare una nuova cartella, denominarla **Scenes**.

            ![Crea nuova cartella script](images/AzureLabs-Lab4-13.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo **nome file**: testo digitare **FaceRecScene**e quindi fare clic su **Salva**.

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab4-14.png)

    7. Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.

6. Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* . 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab4-15.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **altre impostazioni** :

        1. La **versione di runtime** di **Scripting** deve essere **sperimentale** (equivalente a .NET 4,6). Se si modifica questa impostazione, è necessario riavviare l'editor.
        2. Il **back-end di scripting** deve essere **.NET**
        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab4-16.png)
      
    2. Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        - **InternetClient**
        - **Webcam**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab4-17.png)

    3. Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![Aggiornare le impostazioni X R.](images/AzureLabs-Lab4-18.png)

8.  Nelle *impostazioni di compilazione*, **i C# progetti Unity** non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra impostazioni di compilazione.
10. Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).

## <a name="chapter-4---main-camera-setup"></a>Capitolo 4-configurazione della fotocamera principale

> [!IMPORTANT]
> Se si desidera ignorare il componente di *configurazione di Unity* di questo corso e continuare direttamente con il codice, è possibile [scaricare questo. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo nel progetto come [pacchetto personalizzato](https://docs.unity3d.com/Manual/AssetPackages.html). Tenere presente che questo pacchetto include anche l'importazione della *dll Newtonsoft*, illustrata nel [capitolo 5](#chapter-5--import-the-newtonsoftjson-library). Con questa importazione, è possibile continuare dal [capitolo 6](#chapter-6---create-the-faceanalysis-class).

1.  Nel pannello *gerarchia* selezionare la **fotocamera principale**.

2.  Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel *Pannello di controllo*.

    1. L' **oggetto fotocamera** deve essere denominato **Main camera** (nota l'ortografia).

    2. Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (si noti l'ortografia).

    3. Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**

    4. Imposta **Cancella flag** su **colore a tinta unita**

    5. Imposta il colore di **sfondo** del componente della fotocamera su **nero, alfa 0 (codice esadecimale: #00000000)**

        ![configurare i componenti della fotocamera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capitolo 5: importare la libreria Newtonsoft. JSON

> [!IMPORTANT]
> Se il ". file unitypackage Tools" è stato importato nell' [ultimo capitolo](#chapter-4---main-camera-setup), è possibile ignorare questo capitolo.

Per semplificare la deserializzazione e la serializzazione degli oggetti ricevuti e inviati al servizio bot, è necessario scaricare la libreria *Newtonsoft. JSON* . È presente una versione compatibile già organizzata con la struttura di cartelle Unity corretta in questo [file di pacchetto Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Per importare la libreria:

1.  Scaricare il pacchetto Unity.
2.  Fare clic su **Asset**, **Importa pacchetto**, **pacchetto personalizzato**.

    ![Importare la libreria Newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  Cercare il pacchetto Unity scaricato e fare clic su Apri.
4.  Verificare che tutti i componenti del pacchetto siano stati sottoselezionati e fare clic su **Importa**.

    ![Importare la libreria Newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capitolo 6: creare la classe FaceAnalysis

Lo scopo della classe FaceAnalysis è di ospitare i metodi necessari per comunicare con il servizio Azure Face Cognition. 

- Dopo aver inviato il servizio a un'immagine di acquisizione, lo analizzerà e identificherà i visi in e ne determinerà l'eventuale appartenenza a una persona nota. 
- Se viene trovata una persona nota, questa classe ne visualizzerà il nome come testo dell'interfaccia utente nella scena.

Per creare la classe *FaceAnalysis* :

 1. Fare clic con il pulsante destro del mouse sulla *cartella assets* nel pannello Project, quindi scegliere **Crea** > **cartella**. Chiamare gli **script**della cartella. 

    ![Creare la classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla. 
3.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi fare clic su **Crea** >  **C# script**. Chiamare lo script *FaceAnalysis*. 
4.  Fare doppio clic sul nuovo script *FaceAnalysis* per aprirlo con Visual Studio 2017.
5.  Immettere gli spazi dei nomi seguenti sopra la classe *FaceAnalysis* :

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  È ora necessario aggiungere tutti gli oggetti utilizzati per deserialising. Questi oggetti devono essere aggiunti **all'esterno** dello script *FaceAnalysis* (sotto la parentesi graffa inferiore). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. I metodi *Start ()* e *Update ()* non verranno usati, quindi eliminarli ora. 

8.  All'interno della classe *FaceAnalysis* aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Sostituire la **chiave** e il **PersonGroupId** con la chiave del servizio e l'ID del gruppo creato in precedenza.

9.  Aggiungere il metodo *sveglie ()* , che inizializza la classe, aggiungendo la classe *ImageCapture* alla fotocamera principale e chiama il metodo di creazione dell'etichetta:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Aggiungere il metodo *CreateLabel ()* , che crea l'oggetto *Label* per visualizzare il risultato dell'analisi:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Aggiungere il metodo *DetectFacesFromImage ()* e *GetImageAsByteArray ()* . Il primo richiederà al servizio di riconoscimento delle facce di rilevare qualsiasi possibile aspetto nell'immagine inviata, mentre quest'ultimo è necessario per convertire l'immagine acquisita in una matrice di byte:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Aggiungere il metodo *IdentifyFaces ()* che richiede al *servizio di riconoscimento delle facce* di identificare qualsiasi volto noto rilevato in precedenza nell'immagine inviata. La richiesta restituirà un ID della persona identificata, ma non il nome:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Aggiungere il metodo *GetPerson ()* . Se si specifica l'ID persona, questo metodo richiede al *servizio di riconoscimento delle facce* di restituire il nome della persona identificata:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Ricordarsi di **salvare** le modifiche prima di tornare all'editor di Unity.
15.  Nell'editor di Unity trascinare lo script FaceAnalysis dalla cartella Scripts nel pannello del progetto all'oggetto fotocamera principale nel *Pannello gerarchia*. Il nuovo componente script verrà aggiunto alla fotocamera principale. 

![Inserire FaceAnalysis nella fotocamera principale](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capitolo 7: creare la classe ImageCapture

Lo scopo della classe *ImageCapture* è di ospitare i metodi necessari per comunicare con il *servizio Azure Face Recognition* per analizzare l'immagine che verrà acquisita, identificando i visi al suo interno e determinando se appartiene a una persona nota. Se viene trovata una persona nota, questa classe ne visualizzerà il nome come testo dell'interfaccia utente nella scena.

Per creare la classe *ImageCapture* :
 
1.  Fare clic con il pulsante destro del mouse all'interno della cartella **script** creata in precedenza, quindi fare clic su **Crea**,  **C# script**. Chiamare lo script *ImageCapture*. 
2.  Fare doppio clic sul nuovo script *ImageCapture* per aprirlo con Visual Studio 2017.
3.  Immettere gli spazi dei nomi seguenti sopra la classe ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  All'interno della classe *ImageCapture* aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Aggiungere i metodi *svegli ()* e *Start ()* necessari per inizializzare la classe e consentire al HoloLens di acquisire i movimenti dell'utente:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Aggiungere *TapHandler ()* che viene chiamato quando l'utente esegue un gesto *Tap* :

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Aggiungere il metodo *ExecuteImageCaptureAndAnalysis ()* che inizierà il processo di acquisizione dell'immagine:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Aggiungere i gestori che vengono chiamati quando il processo di acquisizione foto è stato completato:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Ricordarsi di **salvare** le modifiche prima di tornare all'editor di Unity.

## <a name="chapter-8---building-the-solution"></a>Capitolo 8-compilazione della soluzione

Per eseguire un test completo dell'applicazione, è necessario sideload nel HoloLens.

Prima di procedere, verificare quanto segue:

-   Tutte le impostazioni indicate nel capitolo 3 sono impostate correttamente. 
-   Lo script *FaceAnalysis* è associato all'oggetto principale della fotocamera. 
-   All'interno dello script *FaceAnalysis* sono stati impostati sia la **chiave di autenticazione** che l' **ID gruppo** .

A questo punto si è pronti per compilare la soluzione. Una volta compilata la soluzione, si sarà pronti per distribuire l'applicazione.

Per avviare il processo di compilazione:

1.  Salvare la scena corrente facendo clic su file, Salva.
2.  Passare a file, impostazioni di compilazione, fare clic su Aggiungi scene aperte.
3.  Verificare di aver selezionato i C# progetti Unity.

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  Premere compila. Quando si esegue questa operazione, Unity avvierà una finestra di Esplora file, in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella adesso, all'interno del progetto Unity, e chiamarla app. Quindi, con la cartella dell'app selezionata, fare clic su Seleziona cartella. 
5.  Unity inizierà a compilare il progetto, fino alla cartella dell'app. 
6.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra Esplora file nel percorso della compilazione.

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  Aprire la cartella dell'app e quindi aprire la nuova soluzione del progetto (come illustrato in precedenza, MR_FaceRecognition. sln).


## <a name="chapter-9---deploying-your-application"></a>Capitolo 9-distribuzione dell'applicazione

Per eseguire la distribuzione in HoloLens:

1.  È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore**. A tale scopo, effettua le seguenti operazioni:

    1. Quando si indossa il HoloLens, aprire le **Impostazioni**.
    2. Passare a **rete & Internet > opzioni avanzate Wi-Fi >**
    3. Prendere nota dell'indirizzo **IPv4** .
    4. Quindi, tornare a **Settings (impostazioni**) e quindi **aggiornare & Security > per gli sviluppatori** 
    5. Impostare la modalità di sviluppo su.

2.  Passare alla nuova compilazione Unity (cartella *app* ) e aprire il file della soluzione con *Visual Studio*.
3.  Nella configurazione della soluzione selezionare **debug**.
4.  Nella piattaforma soluzione selezionare **x86**, **computer remoto**. 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione**per sideload l'applicazione in HoloLens.
6.  L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.

> [!NOTE]
> Per eseguire la distribuzione in un dispositivo headset immersivo, impostare la **piattaforma della soluzione** su *computer locale*e impostare la **configurazione** su *debug*, con *x86* come **piattaforma**. Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*. 


## <a name="chapter-10---using-the-application"></a>Capitolo 10-uso dell'applicazione

1.  Quando si usa il HoloLens, avviare l'app.
2.  Esaminare la persona registrata con il *API viso*. Verificare che:

    -  Il volto della persona non è troppo distante e chiaramente visibile
    -  L'illuminazione dell'ambiente non è troppo scura

3.  Usare il gesto Tap per acquisire l'immagine della persona.
4.  Attendere l'invio della richiesta di analisi da parte dell'app e la ricezione di una risposta.
5.  Se la persona è stata riconosciuta correttamente, il nome della persona verrà visualizzato come testo dell'interfaccia utente.
6.  È possibile ripetere il processo di acquisizione usando il gesto Tap a intervalli di pochi secondi.

## <a name="your-finished-azure-face-api-application"></a>Applicazione API Viso di Azure completa

Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio Azure Face Cognition per rilevare i visi in un'immagine e identificare eventuali visi noti.

![risultato del completamento del corso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Il **API viso di Azure** è sufficientemente potente da rilevare fino a 64 visi in un'unica immagine. Estendere l'applicazione in modo che riconosca due o tre visi, tra le molte altre persone.

### <a name="exercise-2"></a>Esercizio 2

Il **API viso di Azure** è inoltre in grado di fornire tutti i tipi di informazioni sugli attributi. Integrarlo nell'applicazione. Questo potrebbe essere ancora più interessante, se combinato con il [API emozioni](https://azure.microsoft.com/services/cognitive-services/emotion/).
