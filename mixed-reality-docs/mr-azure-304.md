---
title: MR e Azure 304 - riconoscimento facciale
description: Completare questo corso di informazioni su come implementare il riconoscimento di volti di Azure all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, misto realtà, academy, unity, esercitazione, api, riconoscimento, hololens, vr immersivi, facciale
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603811"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR e Azure 304: Rilevamento viso

![risultato del completamento di questo corso](images/AzureLabs-Lab4-00.png)

In questo corso si apprenderà come aggiungere funzionalità di riconoscimento del volto a un'applicazione di realtà mista, uso di servizi cognitivi di Azure, con l'API viso di Microsoft.

*API viso Azure* è un servizio Microsoft, che offre agli sviluppatori di algoritmi estremamente avanzati, faccia tutto nel cloud. Il *API viso* ha due funzioni principali: con gli attributi di rilevamento viso e riconoscimento facciale. Ciò consente agli sviluppatori di è sufficiente impostare un set di gruppi per i visi e quindi inviare query immagini al servizio in un secondo momento, per determinare a cui appartiene un viso. Per altre informazioni, visitare il [pagina di riconoscimento facciale Azure](https://azure.microsoft.com/services/cognitive-services/face/).

Dopo aver completato il corso, si avrà una realtà mista applicazione HoloLens, che sarà in grado di eseguire le operazioni seguenti:

1. Usare un **movimento toccare** per avviare l'acquisizione di un'immagine usando la fotocamera di HoloLens integrata. 
2. Inviare l'immagine acquisita per il *l'API viso Azure* servizio.
3. Ricevere i risultati del *API viso* algoritmo.
4. Usare una semplice interfaccia utente, per visualizzare il nome delle persone corrispondente.

Ciò viene illustrato come ottenere i risultati dal servizio API viso in un'applicazione basata su Unity realtà mista.

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> MR e Azure 304: Rilevamento viso</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla HoloLens, è inoltre possibile applicare informazioni in questo corso per auricolari (VR) coinvolgenti di realtà mista di Windows. Poiché immersive auricolari (VR) non è accessibile fotocamere, sarà necessario una fotocamera esterna connessa al PC. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare immersive auricolari (VR).

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](install-the-tools.md)
- [La versione più recente di Windows 10 SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md) oppure [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore
- Una fotocamera connessa al PC (per lo sviluppo visore VR immersivi)
- Accesso a Internet per la configurazione di Azure e il recupero di API viso

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
2.  Configurare e testare l'HoloLens. Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova App per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente). 

Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1 - portale di Azure

Usare la *API viso* servizio in Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione.

1.  Accedere prima di tutto per il [portale di Azure](https://portal.azure.com). 

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *API viso*, premere **invio**.

    ![eseguire la ricerca di api viso](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

3.  La nuova pagina fornirà una descrizione del *API viso* servizio. AT a sinistra nella parte inferiore di questo prompt, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![informazioni sull'api viso](images/AzureLabs-Lab4-02.png)

4.  Dopo avere fatto clic su **Create**:

    1. Inserire il nome desiderato per questa istanza del servizio.

    2. Selezionare una sottoscrizione.

    3. Selezionare il piano tariffario appropriato per l'utente, se questa è la prima volta che la creazione di un *Face API servizio*, un livello gratuito, denominato F0, debba essere disponibile.

    4. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni). 

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. L'app UWP **persona Maker**, che viene usato in seguito, richiede l'uso di 'Stati Uniti occidentali' per il percorso.

    6. È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.

    7. Selezionare **creare *.**

        ![Crea servizio api viso](images/AzureLabs-Lab4-03.png)

5.  Dopo avere fatto clic su **crea *,** si dovrà attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![notifica di creazione del servizio](images/AzureLabs-Lab4-04.png)

7.  Fare clic su notifiche per esplorare la nuova istanza del servizio.

    ![Passare alla notifica relativa alle risorse](images/AzureLabs-Lab4-05.png)

8.  Quando si è pronti, fare clic su **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.

    ![accesso affrontano le chiavi api](images/AzureLabs-Lab4-06.png)

9.  All'interno di questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, questa operazione viene eseguita tramite la sottoscrizione del servizio 'key'. Dal *avvio rapido* pagina, del *API viso* del servizio, il primo punto è numero 1, a *individuare le chiavi.*

10. Nel *Service* pagina selezionare entrambe di blue **chiavi** hyperlink (se nella pagina avvio rapido), o la **chiavi** collegamento nel menu di spostamento di servizi (a sinistra, identificata dal ' chiave ' icona), per visualizzare le chiavi.

    > [!NOTE] 
    > Prendere nota di uno delle chiavi e proteggerlo, perché sarà necessaria in un secondo momento.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capitolo 2 - uso dell'applicazione UWP 'Person Maker'

Assicurarsi di scaricare l'applicazione UWP predefiniti chiamati [persona Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Questa app non è il prodotto finale per questo corso, di un semplice strumento per creare le voci di Azure, il progetto più avanti si baseranno su.

**Persona Maker** consente di creare voci di Azure, che sono associate utenti e gruppi di utenti. L'applicazione inseriranno tutte le informazioni necessarie in un formato che è quindi in un secondo momento utilizzabile da FaceAPI, per poterlo riconoscere i visi di persone che sono stati aggiunti. 

> [IMPORTANTE] **Persona Maker** utilizza una base limitazione delle richieste, al fine di garantire di non superare il numero di chiamate al servizio al minuto per il **livello di sottoscrizione gratuita**. Il testo in verde nella parte superiore verrà cambia in rosso e aggiornare 'Attivo' quando viene applicata la limitazione; In questo caso, attendere semplicemente che l'applicazione (attenderà fino a quando non può continuare quindi l'accesso al servizio viso, l'aggiornamento come 'Attivo IN' quando è possibile utilizzare anche in questo caso).

Questa applicazione usa la *Microsoft.ProjectOxford.Face* usano librerie, quale sarà possibile apportare completa dell'API viso. Questa libreria è disponibile gratuitamente come pacchetto NuGet. Per altre informazioni su questo e così via, le API [assicurarsi di passare all'articolo di riferimento API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Questi sono solo i passaggi necessari, le istruzioni su come eseguire queste operazioni è più in basso il documento. Il **persona Maker** app consentirà di:
>
> - Creare un *gruppo di persone*, che è costituito da un gruppo di più persone che si desidera associare. Con l'account di Azure Puoi ospitare più gruppi di persone.
>
> - Creare un *persona*, che è un membro di un gruppo di persone. Ogni persona dispone di numerose *viso* immagini associate.
>
> -  Assegnare *affrontano le immagini* a un *persona*, per consentire al servizio di API viso di Azure di riconoscere un *persona* dal corrispondente *viso*.
>
> -  *Train* le *Azure affrontano servizio API*.

Si noti, pertanto per eseguire il training di questa app di riconoscere le persone, sarà necessario foto ravvicinate dieci (10) di ogni persona che si desidera aggiungere al gruppo di persone. L'App di Windows 10 Cam possono aiutare a sfruttare questi. È necessario assicurarsi che ogni foto è chiaro (evitare sfocatura, oscurare o in corso troppo lontano dal soggetto), avere la foto in formato di file jpg o png, con le dimensioni del file di immagine in corso non superiore **4MB**e non inferiore a **1KB**.

> [!NOTE]
> Se si segue questa esercitazione, non usare il proprio viso per il training, come quando si inserisce il HoloLens, è Impossibile esaminare manualmente. Usare la faccia di un collega o fellow studente.

In esecuzione **persona Maker**:

1.  Aprire il **PersonMaker** cartella e fare doppio clic sui *soluzione PersonMaker* aprirlo con *Visual Studio*.

2.  Una volta il *PersonMaker soluzione* è aperto, assicurarsi che:

    1. Il *configurazione della soluzione* è impostata su **Debug**.

    2. Il *piattaforma soluzione* è impostata su **x86**

    3. Il *piattaforma di destinazione* viene **computer locale**.

    4.  Inoltre potrebbe essere necessario *Ripristina pacchetti NuGet* (pulsante destro del mouse il *soluzione* e selezionare **Ripristina pacchetti NuGet**).

3.  Fare clic su *computer locale* e verrà avviata l'applicazione. Tenere presente, a su schermi più piccoli, tutto il contenuto potrebbe non essere visibile, anche se è possibile scorrere ulteriormente verso il basso per visualizzarlo.

    ![interfaccia utente di persona maker](images/AzureLabs-Lab4-07.png)

4.  Inserire le **chiave di autenticazione di Azure**, che è necessario, dalle *API viso* servizio all'interno di Azure.

5.  Inserire:

    1. Il *ID* da assegnare per il *gruppo di persone*. L'ID deve essere in lettere minuscole, senza spazi. Prendere nota di questo ID, sarà necessaria in un secondo momento nel progetto Unity.
    2. Il *Name* da assegnare al *gruppo di persone* (può avere spazi).


6.  Premere **Crea gruppo di persone** pulsante. Sotto il pulsante verrà visualizzato il messaggio di conferma.

> [!NOTE]
> Se si dispone di un errore "Accesso negato", controllare il percorso impostato per il servizio di Azure. Come indicato in precedenza, questa app è stata progettata per "Stati Uniti occidentali".

> [!IMPORTANT]
> Si noterà che è anche possibile scegliere il **recuperare un gruppo noto** pulsante: si tratta di per se è stato già creato un utente a gruppo e preferenze per usarlo, anziché crearne uno nuovo. Tenere presente, se si sceglie *creare un gruppo di persone* con un gruppo noto, verrà recuperata anche un gruppo.

7.  Inserire il *Name* del *persona* si desidera creare.

    1. Scegliere il **persona che crea** pulsante.

    2. Sotto il pulsante verrà visualizzato il messaggio di conferma.

    3. Se si desidera eliminare una persona hanno creato in precedenza, è possibile scrivere il nome nella casella di testo e premere **Elimina utente**

8.  Assicurarsi che si conosce il percorso di dieci (10) foto della persona che si desidera aggiungere al gruppo.

9.  Premere **crea e Apri cartella** per aprire l'Explorer di Windows per la cartella associata alla persona. Aggiungere le immagini di dieci (10) nella cartella. Tali dispositivi devono presentare *JPG* oppure *PNG* formato di file.

10. Fare clic su **inviare ad Azure**. Un contatore visualizzerà lo stato dell'inoltro, seguito da un messaggio quando è stata completata.

11. Dopo il contatore è stata completata ed è stato visualizzato un messaggio di conferma fare clic su **Train** per eseguire il training del servizio.

Una volta completato il processo, si è pronti a spostare in Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3 - configurare il progetto Unity

Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **New**. 

    ![Avvio nuovo progetto Unity.](images/AzureLabs-Lab4-08.png)

2.  A questo punto, è necessario specificare un nome di progetto Unity. Inserire **MR_FaceRecognition**. Verificare che il tipo di progetto è impostato su **3D**. Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![Fornire i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab4-09.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![Aggiornamento delle preferenze dell'editor di script.](images/AzureLabs-Lab4-10.png)

4.  Passare quindi ad **File > Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.

    ![Crea finestra delle impostazioni, la piattaforma del commutatore alla piattaforma UWP.](images/AzureLabs-Lab4-11.png)

5.  Passare a **File > Build Settings** e assicurarsi che:

    1. **Dispositivo di destinazione** è impostata su **HoloLens**

        > Per le cuffie coinvolgenti, impostare **dispositivo di destinazione** al *qualsiasi dispositivo*.

    2. **Tipo di compilazione** è impostata su **D3D**
    3. **SDK** è impostata su **installata più recente**
    4. **Versione di Visual Studio** è impostata su **installata più recente**
    5. **Compilare ed eseguire** è impostata su **computer locale**
    6. Salvare la scena e aggiungerlo alla compilazione. 

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.

            ![Fare clic su Aggiungi pulsante Apri scene](images/AzureLabs-Lab4-12.png)

        2. Selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![Crea nuova cartella scripts](images/AzureLabs-Lab4-13.png)

        3. Aprire appena creato **scene** cartella e quindi il **nome File**: campo di testo, digitare **FaceRecScene**, quindi premere **Salva**.

            ![Assegnare un nome nuova scena.](images/AzureLabs-Lab4-14.png)

    7. Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.

6. Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova. 

    ![Aprire le impostazioni del giocatore.](images/AzureLabs-Lab4-15.png)

7. In questo pannello, alcune impostazioni devono essere verificati:

    1. Nel **altre impostazioni** scheda:

        1. **Scripting** **versione Runtime** deve essere **sperimentale** (.NET 4.6 equivalente). Modificare questo elemento attiverà la necessità di riavviare l'Editor.
        2. **Back-end di scripting** deve essere **.NET**
        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![Aggiornare le altre impostazioni.](images/AzureLabs-Lab4-16.png)
      
    2. All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        - **InternetClient**
        - **Webcam**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab4-17.png)

    3. Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.

        ![Aggiornare le impostazioni di R X.](images/AzureLabs-Lab4-18.png)

8.  Nuovamente in *Build Settings*, **Unity C# progetti** non è più è disattivata; selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Impostazioni di compilazione.
10. Salvare la scena e il progetto (**FILE > SAVE SCENE / FILE > Salva progetto**).

## <a name="chapter-4---main-camera-setup"></a>Capitolo 4 - impostazione della fotocamera principale

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile [scaricare questo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo nel progetto come un [personalizzato Pacchetto](https://docs.unity3d.com/Manual/AssetPackages.html). Tenere presente che questo pacchetto include inoltre l'importazione del *DLL Newtonsoft*, descritta in [capitolo 5](#chapter-5--import-the-newtonsoft.json-library). A questo punto importato, è possibile continuare dal [capitolo 6](#chapter-6-create-the-faceanalysis-class).

1.  Nel *gerarchia* riquadro, selezionare la **Main Camera**.

2.  Una volta selezionata, sarà possibile visualizzare tutti i componenti del **Main Camera** nel *Pannello di controllo*.

    1. Il **oggetto della fotocamera** devono essere denominati **Main Camera** (si noti l'ortografici!)

    2. Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici!)

    3. Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**

    4. Impostare **cancellare i flag** a **colore a tinta unita**

    5. Impostare il **sfondo** colore del componente della fotocamera su **nero, Alpha 0 (Hex codice: #00000000)**

        ![configurare i componenti della fotocamera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capitolo 5: importazione della libreria newtonsoft. JSON

> [!IMPORTANT]
> Se è stata importata '.unitypackage' nella [ultimo capitolo](#chapter-4--main-camera-setup), è possibile ignorare questo capitolo.

Che consentono di deserializzano e serializzano oggetti ricevuti e inviati al servizio Bot è necessario scaricare il *newtonsoft. JSON* libreria. Si noterà una versione compatibile già organizzata con la struttura di cartelle di Unity corretta in questo [file di pacchetto Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Per importare la libreria:

1.  Scaricare il pacchetto Unity.
2.  Fare clic su **Assets**, **Importa pacchetto**, **pacchetto personalizzato**.

    ![Importazione della libreria newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  Cercare il pacchetto Unity è stato scaricato e fare clic su Apri.
4.  Assicurarsi che tutti i componenti del pacchetto sono selezionati e fare clic su **importazione**.

    ![Importazione della libreria newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capitolo 6: creare la classe FaceAnalysis

Lo scopo della classe FaceAnalysis deve ospitare i metodi necessari per comunicare con il servizio di riconoscimento di volti di Azure. 

- Dopo l'invio di un'immagine di acquisizione del servizio, verrà analizzare lo e identificare i volti all'interno e determinare se eventuali appartengono a un utente noto. 
- Se viene trovata una persona nota, questa classe relativo nome verrà visualizzato come testo dell'interfaccia utente nella scena.

Per creare il *FaceAnalysis* classe:

 1. Fare doppio clic nella *cartella Assets* si trova nel Pannello di progetto, quindi fare clic su **Create** > **cartella**. Chiamare la cartella **script**. 

    ![Creare la classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Fare doppio clic sulla cartella appena creata, per aprirlo. 
3.  Fare doppio clic all'interno della cartella, quindi fare clic su **Create**  >   **C# Script**. Chiamare lo script *FaceAnalysis*. 
4.  Fare doppio clic su nuova *FaceAnalysis* script per aprirlo con Visual Studio 2017.
5.  Immettere gli spazi dei nomi seguenti sopra la *FaceAnalysis* classe:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  È ora necessario aggiungere tutti gli oggetti che vengono usati per deserialising. Questi oggetti devono essere aggiunti **fuori** del *FaceAnalysis* script (sotto la parentesi graffa in basso). 

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
7. Il *Start ()* e *Update ()* metodi non verranno utilizzati, quindi eliminarli ora. 

8.  All'interno di *FaceAnalysis* classe, aggiungere le variabili seguenti:

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
    > Sostituire il **key** e il **personGroupId** con la chiave di servizio e l'Id del gruppo creato in precedenza.

9.  Aggiungere il *Awake()* metodo, che initialises la classe, aggiungendo il *ImageCapture* classe alla fotocamera principale e chiama il metodo di creazione di etichette:

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

10. Aggiungere il *CreateLabel()* metodo, che crea il *etichetta* oggetto per visualizzare il risultato dell'analisi:

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

11. Aggiungere il *DetectFacesFromImage()* e *GetImageAsByteArray()* (metodo). Il primo richiederà il servizio di riconoscimento del viso per rilevare eventuali possibili viso nell'immagine inviata, mentre nel secondo caso è necessario convertire l'immagine acquisita in una matrice di byte:

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

12. Aggiungere il *IdentifyFaces()* metodo, che richiede il *servizio di riconoscimento volto* per identificare eventuali noti volti rilevati in precedenza nell'immagine inviato. La richiesta restituisce un id dell'utente identificato ma non il nome:

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

13. Aggiungere il *GetPerson()* (metodo). Fornendo la persona id, questo metodo e le richieste per il *servizio di riconoscimento volto* per restituire il nome della persona identificato:

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

14.  Ricordarsi di **salvare** le modifiche prima di tornare all'Editor di Unity.
15.  Nell'Editor di Unity, trascinare lo script FaceAnalysis dalla cartella Scripts nel Pannello di progetto per l'oggetto Main Camera nel *pannello gerarchia*. Il nuovo componente script verrà quindi aggiunto alla fotocamera principale. 

![Posizionare FaceAnalysis nella fotocamera principale](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capitolo 7 - creare la classe ImageCapture

Lo scopo del *ImageCapture* classe consiste nell'ospitare i metodi necessari per comunicare con i *servizio di riconoscimento volto Azure* per analizzare l'immagine verrà acquisita, che identifica i visi in esso e determinare se appartiene a un utente noto. Se viene trovata una persona nota, questa classe relativo nome verrà visualizzato come testo dell'interfaccia utente nella scena.

Per creare il *ImageCapture* classe:
 
1.  Pulsante destro del mouse all'interno di **script** cartella hanno creato in precedenza e quindi fare clic su **Create**,  **C# Script**. Chiamare lo script *ImageCapture*. 
2.  Fare doppio clic su nuova *ImageCapture* script per aprirlo con Visual Studio 2017.
3.  Immettere gli spazi dei nomi seguenti sopra la classe ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  All'interno di *ImageCapture* classe, aggiungere le variabili seguenti:

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

5.  Aggiungere il *Awake()* e *Start ()* metodi necessari per inizializzare la classe e consentire di HoloLens acquisire i movimenti dell'utente:

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

6.  Aggiungere il *TapHandler()* che viene chiamato quando l'utente esegue un' *toccare* movimenti:

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

7.  Aggiungere il *ExecuteImageCaptureAndAnalysis()* metodo, che inizierà il processo di acquisizione immagine:

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

8.  Aggiungere i gestori eventi vengono chiamati quando il processo di acquisizione di foto è stato completato:

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

9. Ricordarsi di **salvare** le modifiche prima di tornare all'Editor di Unity.

## <a name="chapter-8---building-the-solution"></a>Capitolo 8 - la compilazione della soluzione

Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload di HoloLens.

Prima di procedere, verificare quanto segue:

-   Tutte le impostazioni indicate nel capitolo 3 siano impostate correttamente. 
-   Lo script *FaceAnalysis* è collegato all'oggetto Main Camera. 
-   Entrambi il **Authentication Key** e **Id gruppo** sono state impostate all'interno di *FaceAnalysis* script.

R questo punto si è pronti a compilare la soluzione. Dopo aver compilata la soluzione, sarà possibile distribuire l'applicazione.

Per iniziare il processo di compilazione:

1.  Facendo clic sul File, salvare, salvare nella scena corrente.
2.  Vai a File, impostazioni di compilazione, fare clic su Aggiungi scene Open.
3.  Assicurarsi di segni di graduazione Unity C# progetti.

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  Premere compilazione. In questo modo, Unity avvierà una finestra di Esplora File, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in. Creare a questo punto, tale cartella all'interno del progetto Unity e App. Premere quindi con la cartella dell'App selezionata, selezionare la cartella. 
5.  Unity verrà avviata la creazione del progetto, per la cartella dell'App. 
6.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà una finestra di Esplora File nel percorso della compilazione.

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  Aprire la cartella dell'App e quindi aprire la nuova soluzione di progetto (come nell'esempio precedente, MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>Capitolo 9 - distribuzione dell'applicazione

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

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  Andare alla **dal menu Compila** e fare clic su **Distribuisci soluzione**, trasferire localmente l'applicazione di HoloLens.
6.  L'App deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.

> [!NOTE]
> Per distribuire visore VR immersivi, impostare il **piattaforma soluzione** al *computer locale*e impostare il **configurazione** a *Debug*, con *x86* come la **piattaforma**. Quindi distribuire in locale del computer, utilizzando il **dal menu Compila**, selezionando *Distribuisci soluzione*. 


## <a name="chapter-10---using-the-application"></a>Capitolo 10 - uso dell'applicazione

1.  Uso di HoloLens, avviare l'app.
2.  Esaminare la persona che è registrati con il *API viso*. Verificare che:

    -  Viso della persona non è troppo distante e chiaramente visibili
    -  L'illuminazione di ambiente non è troppo scuro

3.  Usare i movimenti di tocco per acquisire l'immagine di una persona.
4.  Attendere che l'App per la richiesta di analisi di inviare e ricevere una risposta.
5.  Se la persona che è stata riconosciuta correttamente, verrà visualizzato il nome della persona come testo dell'interfaccia utente.
6.  È possibile ripetere il processo di acquisizione mediante i movimenti tocco di intervalli di pochi secondi.

## <a name="your-finished-azure-face-api-application"></a>Azure Face API dell'applicazione completata

Complimenti, è stata compilata un'app per realtà mista che usa il servizio di riconoscimento facciale di Azure per rilevare volti all'interno di un'immagine e identificare eventuali visi noti.

![risultato del completamento di questo corso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Il **l'API viso Azure** è sufficientemente potente per rilevare fino a 64 visi in un'unica immagine. Estendere l'applicazione, in modo che Impossibile riconoscere i visi due o tre, tra le molte altre persone.

### <a name="exercise-2"></a>Esercizio 2

Il **l'API viso Azure** è anche in grado di fornire nuovamente tutti i tipi di informazioni sugli attributi. Integrare l'applicazione. Ciò potrebbe essere ancora più interessante, in combinazione con il [API emozioni](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).
