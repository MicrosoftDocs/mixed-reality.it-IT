---
title: MR e Azure 306-video di streaming
description: Completare questo corso per apprendere come implementare servizi multimediali di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, servizi multimediali, streaming video, 360, immersiva, VR
ms.openlocfilehash: e27bda2a9309f335feb0056703da492555c39fde
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896579"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR e Azure 306: Video di streaming

![prodotto finale-](images/AzureLabs-Lab6-00.png)
![avvio prodotto finale](images/AzureLabs-Lab6-01.png)

In questo corso si apprenderà come connettere i servizi multimediali di Azure a un'esperienza di VR per la realtà mista di Windows per consentire la riproduzione video in streaming di 360 gradi su cuffie immersive. 

**Servizi multimediali di Azure** è una raccolta di servizi che offre servizi di streaming video di qualità broadcast per raggiungere un numero elevato di destinatari sui dispositivi mobili attualmente più diffusi. Per altre informazioni, visitare la [pagina servizi multimediali di Azure](https://azure.microsoft.com/services/media-services).

Dopo aver completato questo corso, si disporrà di un'applicazione per cuffie immersiva mista, che sarà in grado di eseguire le operazioni seguenti:

1. Recuperare un video di 360 Degree da un' **archiviazione di Azure**tramite il **servizio multimediale di Azure**.

2. Visualizza il video recuperato di 360 Degree in una scena Unity.

3. Spostarsi tra due scene, con due video diversi.

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 306: Video di streaming</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura del documento (maggio 2018). È possibile utilizzare il software più recente, come indicato nell' [articolo installare gli strumenti](install-the-tools.md), ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo, [compatibile con la realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di auricolari immersivi (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](install-the-tools.md#installation-checklist)
- [Windows 10 SDK più recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Cuffia A [realtà mista (VR) di Windows](immersive-headset-hardware-details.md)
- Accesso a Internet per l'installazione di Azure e il recupero dei dati
- Video di 2 360 gradi in formato MP4 (è possibile trovare alcuni video senza diritti d'autore [in questa pagina di download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare l'auricolare immersiva della realtà mista.

    > [!NOTE]
    > **Non** sarà necessario alcun controller di movimento per questo corso. Se è necessario supportare la configurazione dell'auricolare immersivo, fare clic [sul collegamento per configurare la realtà mista di Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Capitolo 1-portale di Azure: creazione dell'account di archiviazione di Azure

Per usare il **servizio di archiviazione di Azure**, è necessario creare e configurare un **account di archiviazione** nell'portale di Azure.

1.  Accedere al [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **account di archiviazione** nel menu a sinistra.

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab6-02.png)

3.  Nella scheda **account di archiviazione** fare clic su **Aggiungi**.

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab6-03.png)

4.  Nella scheda **Crea account di archiviazione** :

    1.  Inserire un **nome** per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.

    2.  Per **modello di distribuzione** selezionare **Resource Manager**.

    3.  Per **tipo di account**selezionare **archiviazione (utilizzo generico V1)** .

    4.  Per la **Performance**, selezionare **Standard*.**

    5.  Per la **replica** selezionare **archiviazione con ridondanza locale (con ridondanza locale)** .

    6.  Lasciare il **trasferimento sicuro necessario** come **disabilitato**.

    7.  Selezionare una **sottoscrizione**.

    8.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.

    9.  Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

5.  È necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab6-04.png)

6.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

7.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Configurazione dell'account di archiviazione di Azure](images/AzureLabs-Lab6-05.png)

8.  A questo punto non è necessario seguire la risorsa, ma è sufficiente passare al capitolo successivo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capitolo 2-portale di Azure: creazione del servizio multimediale

Per usare il servizio multimediale di Azure, è necessario configurare un'istanza del servizio da rendere disponibile all'applicazione (dove il titolare dell'account deve essere un amministratore).

1.  Nel portale di Azure fare clic su **Crea una risorsa** nell'angolo in alto a sinistra e cercare **servizio multimediale,** quindi premere **invio**. La risorsa desiderata dispone attualmente di un'icona rosa; fare clic su questo pulsante per visualizzare una nuova pagina.

    ![Portale di Azure](images/AzureLabs-Lab6-06.png)

2.  La nuova pagina fornirà una descrizione del **servizio multimediale**. Nella parte inferiore sinistra del prompt, fare clic sul pulsante **Crea** per creare un'associazione con il servizio.

    ![Portale di Azure](images/AzureLabs-Lab6-07.png)

3.  Una volta fatto clic su **Crea** , verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli sul nuovo servizio multimediale:

    1.  Inserire il **nome dell'account** desiderato per questa istanza del servizio.

    2.  Selezionare una **sottoscrizione**.

    3. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi Lab) in un gruppo di risorse comune). 
    
    > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire i gruppi di risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determinare il **percorso** del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

    5.  Per la sezione **account di archiviazione** , fare clic sulla sezione **selezionare...** , quindi fare clic sull'account di **archiviazione** creato nell'ultimo capitolo.

    6.  Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.

    7.  Fare clic su **Create**(Crea).

        ![Portale di Azure](images/AzureLabs-Lab6-08.png)

4.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

5.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Portale di Azure](images/AzureLabs-Lab6-09.png)

6.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Portale di Azure](images/AzureLabs-Lab6-10.png)

7.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.

8.  Nella pagina nuovo servizio multimediale, all'interno del pannello a sinistra, fare clic sul collegamento **Asset** , che è circa a metà.

9.  Nella pagina successiva, nell'angolo in alto a sinistra della pagina, fare clic su **carica**.

    ![Portale di Azure](images/AzureLabs-Lab6-11.png)

10. Fare clic sull'icona della **cartella** per sfogliare i file e selezionare il primo video 360 che si desidera trasmettere in streaming. 
    
    > È possibile seguire questo [collegamento per scaricare un video di esempio](https://vimeo.com/214401712).

    ![Portale di Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> I nomi di file lunghi possono causare un problema con il codificatore: pertanto, per assicurarsi che i video non richiedano problemi, è consigliabile abbreviare la lunghezza dei nomi dei file video.

11. L'indicatore di stato diventerà verde al termine del caricamento del video.

    ![Portale di Azure](images/AzureLabs-Lab6-13.png)

12. Fai clic sul testo precedente (**yourservicename-assets**) per tornare alla pagina **Asset** .

13. Si noterà che il video è stato caricato correttamente. Fare clic su di essa.

    ![Portale di Azure](images/AzureLabs-Lab6-14.png)

14. Nella pagina a cui si è reindirizzati verranno visualizzate informazioni dettagliate sul video. Per poter usare il video, è necessario codificarlo facendo clic sul pulsante Encode ( **codifica** ) nella parte superiore sinistra della pagina.

    ![Portale di Azure](images/AzureLabs-Lab6-15.png)

15. Verrà visualizzato un nuovo pannello a destra, in cui sarà possibile impostare le opzioni di codifica per il file. Impostare le proprietà seguenti (alcune saranno già impostate per impostazione predefinita):

    1.  **Nome codificatore multimediale *Media Encoder standard***

    2.  **Codifica del contenuto preimpostato *contenuto MP4 a più velocità in bit***

    3.  **Nome processo *Media Encoder standard l'elaborazione di video1. mp4***

    4.  **Nome asset del supporto *di output video1. MP4--Media Encoder standard codificato***

        ![Portale di Azure](images/AzureLabs-Lab6-16.png)

16. Fare clic sul pulsante **Crea**.

17. Si noterà una barra con il **processo di codifica aggiunto**, si fa clic su tale barra e viene visualizzato un pannello con lo stato di codifica visualizzato.

    ![Portale di Azure](images/AzureLabs-Lab6-17.png)

    ![Portale di Azure](images/AzureLabs-Lab6-18.png)

18. Attendere il completamento del processo. Al termine, è possibile chiudere il pannello con ' X ' nella parte superiore destra del pannello.

    ![Portale di Azure](images/AzureLabs-Lab6-19.png)

    ![Portale di Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > Il tempo necessario dipende dalla dimensione del file del video. Questo processo può richiedere molto tempo.

19. Ora che è stata creata la versione codificata del video, è possibile pubblicarla per renderla accessibile. A tale scopo, fare clic sulle **risorse** dei collegamenti blu per tornare alla pagina asset.

    ![Portale di Azure](images/AzureLabs-Lab6-21.png)

20. Il video verrà visualizzato insieme a un altro, che è di **tipo asset con _MP4 a bitrate multipli_** .

    ![Portale di Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > È possibile notare che il nuovo asset, insieme al video iniziale, è *sconosciuto*e contiene ' 0' byte per la **dimensione**, ma è sufficiente aggiornare la finestra affinché venga aggiornata.

21. Fare clic su questo nuovo asset.

    ![Portale di Azure](images/AzureLabs-Lab6-23.png)

22. Verrà visualizzato un pannello simile a quello usato in precedenza, ma si tratta di un asset diverso. Fare clic sul pulsante **pubblica** nella parte superiore del centro della pagina.

    ![Portale di Azure](images/AzureLabs-Lab6-24.png)

23. Verrà richiesto di impostare un localizzatore, ovvero il punto di ingresso, per file/s negli asset. Per lo scenario, impostare le proprietà seguenti:

    1.  **Tipo di localizzatore** **progressive.**  > 

    2.  La **Data** e l' **ora** verranno impostate per l'utente, dalla data corrente, a un'ora futura (100 anni in questo caso). Lasciarlo invariato o modificarlo in base alle esigenze.

    > [!NOTE]
    > Per altre informazioni sui localizzatori e sulle opzioni che è possibile scegliere, vedere la [documentazione di servizi multimediali di Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).

24. Nella parte inferiore del pannello fare clic sul pulsante **Aggiungi** .

    ![Portale di Azure](images/AzureLabs-Lab6-25.png)

25. Il video è ora pubblicato e può essere trasmesso tramite il relativo endpoint. La pagina è una sezione di **file** . Questo è il punto in cui saranno le diverse versioni codificate del video. Selezionare la risoluzione più alta possibile (nell'immagine seguente è il file 1920x960) e quindi verrà visualizzato un pannello a destra. Qui sarà disponibile un **URL di download**. Copiare questo **endpoint** come verrà usato in un secondo momento nel codice.

    ![Portale di Azure](images/AzureLabs-Lab6-26.png)    

    ![Portale di Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > È anche possibile premere il pulsante Riproduci per riprodurre il video e testarlo.

26. È ora necessario caricare il secondo video che verrà usato in questo Lab. Seguire i passaggi precedenti, ripetendo lo stesso processo per il secondo video. Assicurarsi di copiare anche il secondo **endpoint** . Usare il [collegamento seguente per scaricare un secondo video](https://vimeo.com/214402865).

27. Dopo la pubblicazione di entrambi i video, è possibile passare al capitolo successivo.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capitolo 3-configurazione del progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire **Unity** e fare clic su **New**. 

    ![Portale di Azure](images/AzureLabs-Lab6-28.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity, inserire **\_Mr 360VideoStreaming.** Verificare che il tipo di progetto sia impostato su **3D**. Impostare il percorso su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![Portale di Azure](images/AzureLabs-Lab6-29.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio.** Passare a ***modifica* *Preferenze*** e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![Portale di Azure](images/AzureLabs-Lab6-30.png)

4.  Passare quindi a  ***impostazioni di compilazione* File** e passare alla piattaforma **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .

5.  Assicurarsi inoltre che:

    1. Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo.**
    
    2.  Il **tipo di compilazione** è impostato su **D3D.**

    3.  **SDK** è impostato sull' **ultima versione installata.**

    4.  La **versione di Visual Studio** è impostata su **installazione più recente.**

    5.  **Compilazione ed esecuzione** è impostato su **computer locale.**

    6.  Non preoccuparti di configurare le **scene** in questo momento, perché verranno impostate in un secondo momento.

    7.  Per il momento le impostazioni rimanenti devono essere lasciate come predefinite.

        ![Configurazione del progetto Unity](images/AzureLabs-Lab6-31.png)

6.  Nella finestra **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** . 

7. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **altre impostazioni** :

        1.  Creazione di **script** La **versione di runtime** deve essere **stabile** (equivalente a .NET 3,5).

        2. Il **back-end** di scripting deve essere **.NET.**

        3. Il **livello di compatibilità API** deve essere **.NET 4,6.**

            ![Configurazione del progetto Unity](images/AzureLabs-Lab6-32.png)

    2.  Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![Configurazione del progetto Unity](images/AzureLabs-Lab6-33.png)

    3.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        - **InternetClient**

            ![Configurazione del progetto Unity](images/AzureLabs-Lab6-34.png)

8.  Dopo aver apportato queste modifiche, chiudere la finestra **impostazioni di compilazione** .

9.  Salvare il progetto **File* *Salva progetto**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capitolo 4-importazione del pacchetto InsideOutSphere Unity

> [!IMPORTANT]
> Se si desidera ignorare il componente *di configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricarlo [. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal **capitolo 5**. Sarà comunque necessario creare un progetto Unity.

Per questo corso sarà necessario scaricare un pacchetto di asset Unity denominato [**InsideOutSphere. file unitypackage Tools**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).

Procedura: importare il **file unitypackage Tools**:

1.  Con il dashboard Unity, fare clic su **Asset** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto > pacchetto personalizzato**.

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-35.png)

2.  Usare il selettore file per selezionare il pacchetto **InsideOutSphere. file unitypackage Tools** e fare clic su **Apri**. Verrà visualizzato un elenco di componenti per questo asset. Confermare l'importazione facendo clic su **Importa**.

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-36.png)

3.  Una volta completata l'importazione, si noterà che nella cartella **assets** sono state aggiunte tre nuove cartelle, **materiali**, **modelli**e prefabbricati. Questo tipo di struttura di cartelle è tipico per un progetto Unity.

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-37.png)

    1.  Aprire la cartella Models ( **modelli** ). si noterà che il modello **InsideOutSphere** è stato importato.

    2.  All'interno della cartella Materials ( **materiali** ) troverete il materiale **InsideOutSpheres** *lambert1*, insieme a un materiale denominato *ButtonMaterial*, che viene usato da GazeButton, che verrà visualizzato a breve.

    3.  La cartella prefabbricates contiene la prefabbricazione **InsideOutSphere** che contiene il *modello* **InsideOutSphere** e *GazeButton*.

    4.  **Non è incluso alcun codice**, il codice verrà scritto seguendo questo corso.


4.  All'interno della **gerarchia**selezionare l'oggetto **principale della fotocamera** e aggiornare i componenti seguenti:

    1.  **Trasformazione**

        1.  Posizione = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotazione = **X**: 0, **Y**: 0, **Z**: 0.

        3. Scala **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Fotocamera**

        1. **Cancella flag**: Colore a tinta unita.

        2.  **Piani**di ritaglio: Quasi 0,1, lontano: 6.

            ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-38.png)

5.  Passare alla cartella prefabbricata, quindi trascinare la prefabbricata **InsideOutSphere** nel pannello **gerarchia** .

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-39.png)

6.  Espandere l'oggetto **InsideOutSphere** all'interno della **gerarchia** facendo clic sulla piccola freccia accanto. Verrà visualizzato un oggetto **figlio** sotto il nome **GazeButton**. Questa operazione verrà usata per modificare le scene e quindi i video.

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-40.png)

7.  Nella finestra di controllo fare clic sul componente di trasformazione di **InsideOutSphere**, verificare che siano impostate le proprietà seguenti:

    |            |    TRASFORMAZIONE-POSIZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRASFORMAZIONE-ROTAZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRASFORMAZIONE-RIDIMENSIONA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-41.png)

8.  Fare clic sull'oggetto figlio **GazeButton** e impostare la relativa **trasformazione** come segue:

    |            |    TRASFORMAZIONE-POSIZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3,6|          **Y** 1,3        |  **Z** 0  |

    |            |    TRASFORMAZIONE-ROTAZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRASFORMAZIONE-RIDIMENSIONA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importazione del pacchetto InsideOutSphere Unity](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capitolo 5: creare la classe VideoController

La classe **VideoController** ospita i due endpoint video che verranno usati per lo streaming del contenuto da servizi multimediali di Azure.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse nella **cartella Asset**, che si trova nel pannello **progetto** , quindi fare clic su **Crea > cartella**. Denominare gli **script**della cartella.

    ![Creazione della classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Creazione della classe VideoController](images/AzureLabs-Lab6-44.png)

2.  Fare doppio clic sulla cartella **script** per aprirla.

3.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi fare clic su **Crea > script C\#** . Denominare lo script **VideoController**.

    ![Creazione della classe VideoController](images/AzureLabs-Lab6-45.png)

4.  Fare doppio clic sul nuovo script **VideoController** per aprirlo con **Visual Studio 2017.**

    ![Creazione della classe VideoController](images/AzureLabs-Lab6-46.png)

5.  Aggiornare gli spazi dei nomi all'inizio del file di codice nel modo seguente:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Immettere le variabili seguenti nella classe **VideoController** insieme al metodo **svegli ()** :

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  A questo punto è possibile immettere gli endpoint dai video di servizi multimediali di Azure:

    1.  Primo oggetto nella variabile *video1endpoint* .
    
    2.  Il secondo oggetto nella variabile *video2endpoint* .

    > [!WARNING]
    > Si è verificato un problema noto relativo all'uso di *https* in Unity, con la versione 2017.4.1 F1. Se i video forniscono un errore di riproduzione, provare a usare "http".

8.  Successivamente, è necessario modificare il metodo **Start ()** . Questo metodo verrà attivato ogni volta che l'utente passa dalla scena (quindi passa il video) esaminando il pulsante con lo sguardo.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Dopo il metodo **Start ()** , inserire il metodo **PlayVideo ()** *IEnumerator* , che verrà usato per avviare i video senza interruzioni (pertanto non viene visualizzata alcuna balbuzie).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. L'ultimo metodo necessario per questa classe è il metodo **ChangeScene ()** , che verrà usato per scambiare tra le scene.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > Il metodo **ChangeScene ()** usa una funzionalità C\# utile chiamata *operatore condizionale*. In questo modo è possibile controllare le condizioni e i valori restituiti in base al risultato del controllo, il tutto all'interno di un'unica istruzione. Seguire questo [collegamento per altre informazioni sull'operatore condizionale](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

11. Salvare le modifiche in Visual Studio prima di tornare a Unity.

12. Nell'editor di Unity fare clic e trascinare la classe **VideoController** [from] {. Underline} la cartella **Scripts** nell'oggetto principale della **fotocamera** nel pannello **gerarchia** .

13. Fare clic sulla **fotocamera principale** ed esaminare il **pannello Inspector**. Si noterà che all'interno del componente script appena aggiunto è presente un campo con un valore vuoto. Si tratta di un campo di riferimento, che ha come destinazione le variabili pubbliche all'interno del codice.

14. Trascinare l'oggetto **InsideOutSphere** dal **Pannello gerarchia** allo slot **Sphere** , come illustrato nell'immagine seguente.

    ![Creare la classe](images/AzureLabs-Lab6-47.png)
    ![VideoController creare la classe VideoController](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capitolo 6: creare la classe sguardi

Questa classe è responsabile della creazione di un **Raycast** che verrà proiettato in futuro dalla **fotocamera principale**, per individuare l'oggetto analizzato dall'utente. In questo caso, **Raycast** dovrà identificare se l'utente sta esaminando l'oggetto **GazeButton** nella scena e attivare un comportamento.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare doppio clic nella **Project** Pannello di **creare* *C\# Script**. Denominarelo script.

3.  Fare doppio clic sul nuovo script per aprirlo con **Visual Studio 2017.**

4.  Verificare che lo spazio dei nomi seguente si trovi nella parte superiore dello script e rimuovere gli altri:

    ```csharp
    using UnityEngine;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe **sguardi** :

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  È ora necessario aggiungere il codice per i metodi **svegli ()** e **Start ()** .

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Aggiungere il codice seguente nel metodo **Update ()** per proiettare un Raycast e rilevare il raggiungimento della destinazione:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Salvare le modifiche in Visual Studio prima di tornare a Unity.

9.  Fare clic e trascinare la classe **sguardi** dalla cartella Scripts all'oggetto principale della fotocamera nel pannello **gerarchia** .

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capitolo 7: configurare le due scene Unity

Lo scopo di questo capitolo è quello di configurare le due scene, ciascuna delle quali ospita un video da trasmettere. Si duplica la scena che è già stata creata, in modo che non sia necessario configurarla di nuovo, anche se si modifica la nuova scena, in modo che l'oggetto *GazeButton* si trovi in una posizione diversa e abbia un aspetto diverso. In questo modo viene illustrato come passare da una scena all'altra.

1.  A tale scopo, passare a **File > Salva scena con nome...** . Verrà visualizzata una finestra Salva. Fare clic sul pulsante **nuova cartella** .

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-49.png)

2.  Denominare la cartella **Scenes**.

3.  La finestra **Salva scena** sarà ancora aperta. Aprire la cartella **scene** appena create.

4.  Nel campo **nome file:** testo digitare **VideoScene1**e quindi fare clic su **Salva**.

5.  Tornare in Unity, aprire la cartella **Scenes** e fare clic sul file **VideoScene1** . Utilizzare la tastiera e premere **CTRL + D** per duplicare la scena

    > [!TIP]
    > Il comando duplicato può essere eseguito anche passando a **Modifica > duplicato**.

6.  Unity incrementerà automaticamente il numero di nomi di scena, ma ne verificherà comunque il numero per assicurarsi che corrisponda al codice inserito in precedenza.

    >  Sono presenti **VideoScene1** e **VideoScene2**.

7.  Con le due scene, passare a **File > impostazioni di compilazione**. Con la finestra **impostazioni di compilazione** aperta, trascinare le scene nella sezione **scene della compilazione** .

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > È possibile selezionare entrambe le scene dalla cartella **Scenes** tenendo premuto il pulsante **CTRL** , quindi fare clic su ciascuna scena e infine trascinare entrambe le scene.

8.  Chiudere la finestra **impostazioni di compilazione** e fare doppio clic su **VideoScene2**.

9.  Con la seconda scena aperta, fare clic sull'oggetto figlio **GazeButton** di **InsideOutSphere**e impostare la relativa trasformazione come segue:

    |            |    TRASFORMAZIONE-POSIZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1,3         | **Z** 3,6 |

    |            |    TRASFORMAZIONE-ROTAZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRASFORMAZIONE-RIDIMENSIONA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Con l'elemento figlio **GazeButton** ancora selezionato, esaminare il **controllo** e il **Filtro Mesh**. Fare clic sulla piccola destinazione accanto al campo riferimento **mesh** :

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-51.png)

11. Verrà visualizzata una finestra popup **Seleziona mesh** . Fare doppio clic sulla mesh del **cubo** dall'elenco degli **Asset**.

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-52.png)

12. Il **Filtro Mesh** verrà aggiornato ed è ora costituito da un **cubo**. A questo punto, fare clic sull'icona a forma di ingranaggio accanto a **Sphere Collider** , quindi fare clic su **Rimuovi componente**per eliminare il Collider da questo oggetto.

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-53.png)

13. Con il **GazeButton** ancora selezionato, fare clic sul pulsante **Aggiungi componente** nella parte inferiore del **controllo**. Nel campo di ricerca digitare **Box**e **Box Collider** sarà un'opzione: fare clic su di essa per aggiungere un **Collider di box** all'oggetto **GazeButton** .

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-54.png)

14. Il **GazeButton** è stato aggiornato parzialmente, per un aspetto diverso, tuttavia, verrà creato un nuovo **materiale**, in modo che appaia completamente diverso ed è più facile da riconoscere come oggetto diverso rispetto all'oggetto nella prima scena.

15. Passare alla cartella **Materials** , all'interno del **Pannello Project**. Duplicare il materiale **ButtonMaterial** (premere **CTRL** + **D** sulla tastiera o fare clic con il pulsante destro del mouse sul **materiale**, quindi scegliere duplicato dall'opzione di menu **modifica** file).

    ![Capitolo 7: configurare le due scene](images/AzureLabs-Lab6-55.png)
    ![Unity capitolo 7--configurare le due scene Unity](images/AzureLabs-Lab6-56.png)

16. Selezionare il nuovo materiale **ButtonMaterial** (qui denominato **ButtonMaterial 1**) e, all'interno del **controllo**, fare clic sulla finestra del colore **albedo** . Verrà visualizzata una finestra popup in cui è possibile selezionare un altro colore (scegliere il tipo desiderato), quindi chiudere il popup. Il materiale sarà una propria istanza e diverso dall'originale.

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-57.png)

17. Trascinare il nuovo **materiale** nell'elemento figlio **GazeButton** , per aggiornare completamente l'aspetto, in modo che sia facilmente distinguibile dal pulsante First Scenes.

    ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-58.png)

18. A questo punto è possibile testare il progetto nell'editor prima di compilare il progetto UWP.

    -  Premere il pulsante Riproduci nell' **Editor** e utilizzare l'auricolare.

        ![Capitolo 7: configurare le due scene Unity](images/AzureLabs-Lab6-59.png)

19. Esaminare i due oggetti **GazeButton** per passare tra il primo e il secondo video.

## <a name="chapter-8---build-the-uwp-solution"></a>Capitolo 8: compilare la soluzione UWP

Dopo aver verificato che l'editor non abbia errori, è possibile procedere alla compilazione.

Per compilare:

1.  Salvare la scena corrente facendo clic su **File > Salva**.

2.  Selezionare la casella denominata **progetti Unity C\#**  (questo aspetto è importante perché consente di modificare le classi al termine della compilazione).

3.  Passare a **File > impostazioni di compilazione**, fare clic su **Compila**.

4.  Verrà richiesto di selezionare la cartella in cui si vuole buildthe la soluzione.

5.  Creare una cartella compilazioni e all'interno di tale cartella creare un'altra cartella con un nome appropriato.

6.  Fare clic sulla nuova cartella e quindi fare clic su **Seleziona cartella**, quindi scegliere la cartella per iniziare la compilazione in quel percorso.

    ![Capitolo 8: compilare il capitolo 8 della](images/AzureLabs-Lab6-60.png)
    soluzione![UWP. compilare la soluzione UWP](images/AzureLabs-Lab6-61.png)

7.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nel percorso della compilazione.

## <a name="chapter-9---deploy-on-local-machine"></a>Capitolo 9: eseguire la distribuzione nel computer locale

Una volta completata la compilazione, nella posizione della compilazione verrà visualizzata una finestra **Esplora file** . Aprire la cartella denominata e compilata, quindi fare doppio clic sul file di soluzione (con estensione sln) all'interno della cartella per aprire la soluzione con Visual Studio 2017.

L'unica cosa che rimane da fare è distribuire l'app nel computer (o nel computer *locale*).

Per eseguire la distribuzione nel computer locale:

1.  In **Visual Studio 2017**aprire il file di soluzione appena creato.

2.  Nella **piattaforma soluzione**selezionare **x86, computer locale**.

3.  Nella **configurazione della soluzione** selezionare **debug**.

    ![Capitolo 9-distribuzione nel computer locale](images/AzureLabs-Lab6-62.png)

4.  A questo punto sarà necessario ripristinare tutti i pacchetti nella soluzione. Fare clic con il pulsante destro del mouse sulla **soluzione**e scegliere **Ripristina pacchetti NuGet per la soluzione...**

    > [!NOTE] 
    > Questa operazione viene eseguita perché i pacchetti compilati da Unity devono essere destinati a funzionare con i riferimenti dei computer locali.

5.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer. Visual Studio compilerà prima di tutto e distribuirà l'applicazione.

6.  L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.

    ![Capitolo 9-distribuzione nel computer locale](images/AzureLabs-Lab6-63.png)

Quando si esegue l'applicazione di realtà mista, si sarà all'interno del modello **InsideOutSphere** usato nell'app. Questa sfera è la posizione in cui verrà trasmesso il video, fornendo una visualizzazione di 360 gradi, del video in arrivo (filmato per questo tipo di prospettiva). Non sorprendere se il video richiede un paio di secondi per il caricamento, l'app è soggetta alla velocità Internet disponibile, perché il video deve essere recuperato e quindi scaricato, quindi per eseguire lo streaming nell'app.
Quando si è pronti, modificare le scene e aprire il secondo video, guardando la sfera rossa. Quindi, è possibile tornare indietro, usando il cubo blu nella seconda scena.

## <a name="your-finished-azure-media-service-application"></a>Applicazione di servizi multimediali di Azure completata
 
Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio multimediale di Azure per lo streaming di video di 360.

![risultato Lab](images/AzureLabs-Lab6-00.png)

![risultato Lab](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Esercizi bonus

**Esercizio 1**

Per modificare i video in questa esercitazione è possibile usare solo una singola scena. Prova la tua applicazione e creala in un'unica scena. Forse anche aggiungere un altro video alla combinazione.

**Esercizio 2**

Sperimentare Azure e Unity e provare a implementare la possibilità per l'app di selezionare automaticamente un video con dimensioni di file diverse, a seconda del livello di attendibilità di una connessione Internet.


