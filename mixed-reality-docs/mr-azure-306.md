---
title: MR e 306 Azure - video in Streaming
description: Completare questo corso di informazioni su come implementare servizi multimediali di Azure all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, servizi multimediali, lo streaming di video, 360, coinvolgenti, vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599483"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR e Azure 306: Lo streaming di video

![versione finale del prodotto-avviare](images/AzureLabs-Lab6-00.png)
![prodotto finale-avvio](images/AzureLabs-Lab6-01.png)

In questo corso scoprirai come connettere i servizi multimediali di Azure a un'esperienza VR realtà mista di Windows per consentire la riproduzione di video a 360 gradi in auricolari coinvolgenti di streaming. 

**Servizi multimediali di Azure** sono una raccolta di servizi che ti offre servizi streaming video di alta qualità per raggiungere un pubblico più ampio sui dispositivi mobili più diffusi di oggi. Per altre informazioni, visitare il [pagina di servizi multimediali di Azure](https://azure.microsoft.com/services/media-services).

Dopo aver completato il corso, si avrà un'applicazione visore VR immersivi realtà mista, in grado di eseguire le operazioni seguenti:

1. Recuperare un video a 360 gradi da un' **archiviazione di Azure**, tramite il **servizi multimediali di Azure**.

2. Visualizzare il video a 360 gradi recuperato all'interno di una scena Unity.

3. Spostarsi tra le due scene, con due diversi video.

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> MR e Azure 306: Lo streaming di video</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare l'articolo strumenti](install-the-tools.md), anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri nel software più recente rispetto a quelle riportate di seguito sono disponibili .

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer, di sviluppo [compatibile con realtà mista di Windows](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visore VR immersive (VR)
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](install-the-tools.md#installation-checklist)
- [La versione più recente di Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Oggetto [visore VR (VR) coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md)
- Accesso a Internet per il recupero di dati e il programma di installazione di Azure
- Due video a 360 gradi in formato mp4 (è possibile trovare alcuni video gratuite [nella pagina di download](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
2.  Configurare e testare il visore VR Immersivi a realtà mista.

    > [!NOTE]
    > Verrà **non** richiedono controller di movimento a questo corso. Se è necessario il supporto di configurazione di visore VR Immersivi, fai clic [collegamento su come impostare la realtà mista di Windows](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Capitolo 1 - portale di Azure: creare l'Account di archiviazione di Azure

Usare la **servizio di archiviazione di Azure**, sarà necessario creare e configurare un **Account di archiviazione** nel portale di Azure.

1.  Accedi per il [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **gli account di archiviazione** nel menu a sinistra.

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab6-02.png)

3.  Nel **gli account di archiviazione** scheda, fare clic su **Add**.

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab6-03.png)

4.  Nel **creare account di archiviazione** scheda:

    1.  Inserire un **nome** per l'account, tenere presente questo campo accetta solo numeri e lettere minuscole.

    2.  Per la **modello di distribuzione** selezionate **Resource manager**.

    3.  Per la **tipologia Account**, selezionare **archiviazione (utilizzo generico v1)**.

    4.  Per la **Performance**, selezionare **Standard*.**

    5.  Per la **replica** selezionate **l'archiviazione con ridondanza locale (LRS)**.

    6.  Lasciare **trasferimento sicuro obbligatorio** come **disabilitato**.

    7.  Selezionare una **sottoscrizione**.

    8.  Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.

    9.  Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

5.  È necessario confermare di avere compreso le condizioni applicate a questo servizio.

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab6-04.png)

6.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

7.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Configurazione dell'Account di archiviazione di Azure](images/AzureLabs-Lab6-05.png)

8.  A questo punto non è necessario seguire la risorsa, è sufficiente spostare il capitolo successivo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capitolo 2 - portale di Azure: creazione del servizio multimediale

Per usare il servizio di supporto di Azure, è necessario configurare un'istanza del servizio venga reso disponibile per l'applicazione (in cui il titolare dell'account deve essere un amministratore).

1.  Nel portale di Azure, fare clic su **crea una risorsa** nell'angolo in alto a sinistra e cercare **servizio multimediale** premere **invio**. La risorsa desiderata attualmente dispone di un'icona di colore rosa; Fare clic sul collegamento, in modo da visualizzare una nuova pagina.

    ![Il portale di Azure](images/AzureLabs-Lab6-06.png)

2.  La nuova pagina fornirà una descrizione del **servizio multimediale**. AT nella parte inferiore sinistra di questo prompt, fare clic sui **Create** pulsante, per creare un'associazione con questo servizio.

    ![Il portale di Azure](images/AzureLabs-Lab6-07.png)

3.  Dopo avere fatto clic su **Create** verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli relativi al nuovo servizio di supporto:

    1.  Inserire la posizione desiderata **nome dell'Account** per questa istanza del servizio.

    2.  Selezionare una **sottoscrizione**.

    3. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, questi laboratori) in un gruppo di risorse comuni). 
    
    > Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire i gruppi di risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determinare il **posizione** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.

    5.  Per il **Account di archiviazione** fare clic su di **Seleziona...**  sezione e quindi scegliere il **Account di archiviazione** creato nel capitolo precedente.

    6.  È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.

    7.  Fare clic su **Crea**.

        ![Il portale di Azure](images/AzureLabs-Lab6-08.png)

4.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

5.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Il portale di Azure](images/AzureLabs-Lab6-09.png)

6.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Il portale di Azure](images/AzureLabs-Lab6-10.png)

7.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.

8.  Entro la nuova pagina di servizi multimediali, all'interno del pannello a sinistra, fare clic sui **asset** collegamento, che si riferisce a metà inferiore.

9.  Nella pagina successiva, nell'angolo superiore sinistro della pagina, fare clic su **caricare**.

    ![Il portale di Azure](images/AzureLabs-Lab6-11.png)

10. Fare clic sui **cartella** icona per esplorare i file e selezionare il Video 360 prima che si desidera eseguire lo streaming. 
    
    > È possibile seguire questo [collegamento per scaricare un video di esempio](https://vimeo.com/214401712).

    ![Il portale di Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Nomi file lunghi possono causare un problema con il codificatore: pertanto, per garantire i video non sono presenti problemi, è consigliabile ridurre la lunghezza dei nomi di file video.

11. L'indicatore di stato verrà diventi verde quando ha terminato il caricamento di video.

    ![Il portale di Azure](images/AzureLabs-Lab6-13.png)

12. Fare clic sul testo precedente (**yourservicename - asset**) per tornare alle **asset** pagina.

13. Si noterà che il video sia stato caricato correttamente. Fare clic su di esso.

    ![Il portale di Azure](images/AzureLabs-Lab6-14.png)

14. Si verrà reindirizzati alla pagina mostrerà che vengono fornite informazioni dettagliate relative al video. Per poter utilizzare il video è necessario codificarli, facendo i **Encode** pulsante in alto a sinistra della pagina.

    ![Il portale di Azure](images/AzureLabs-Lab6-15.png)

15. Un nuovo pannello verrà visualizzato a destra, in cui sarà in grado di impostare le opzioni per il file di codifica. Impostare le proprietà seguenti (alcuni sarà già impostato per impostazione predefinita):

    1.  **Nome del codificatore multimediale *Media Encoder Standard***

    2.  **Set di impostazioni di codifica *Content Adaptive Multiple Bitrate MP4***

    3.  **Nome del processo *elaborazione Media Encoder Standard di Video1.mp4***

    4.  **Nome dell'asset multimediali output *Video1.mp4 - Media Encoder Standard con codifica***

        ![Il portale di Azure](images/AzureLabs-Lab6-16.png)

16. Fare clic sul pulsante **Crea**.

17. Si noterà una barra con **processo di codifica aggiunta**, fare clic su tale barra e verrà visualizzato un pannello con lo stato di avanzamento di codifica in esso visualizzato.

    ![Il portale di Azure](images/AzureLabs-Lab6-17.png)

    ![Il portale di Azure](images/AzureLabs-Lab6-18.png)

18. Attendere il completamento del processo. Al termine, è possibile chiudere il pannello con la "X" in alto a destra del pannello.

    ![Il portale di Azure](images/AzureLabs-Lab6-19.png)

    ![Il portale di Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > Il tempo che richiesto, dipende dalla dimensione file del video. Questo processo può richiedere molto tempo.

19. Ora che la versione codificata del video è stata creata, è possibile pubblicare in modo che sia accessibile. A tale scopo, fare clic sul collegamento blu **asset** per tornare alla pagina di asset.

    ![Il portale di Azure](images/AzureLabs-Lab6-21.png)

20. Si noterà un video insieme a un altro, che è impostato su **Asset di tipo *a più Bitrate MP4***.

    ![Il portale di Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > È possibile notare che il nuovo asset, insieme ai video iniziale, è *sconosciuto*, e ha '0' byte, in quanto **dimensioni**, aggiornare semplicemente la finestra per consentirne l'aggiornamento.

21. Fare clic su questo nuovo asset.

    ![Il portale di Azure](images/AzureLabs-Lab6-23.png)

22. Verrà visualizzato un pannello simile a quello usato prima, proprio questa è una risorsa diversa. Scegliere il **pubblica** pulsante che si trova in centrale superiore della pagina.

    ![Il portale di Azure](images/AzureLabs-Lab6-24.png)

23. Verrà richiesto di impostare una **localizzatore**, ovvero il punto di ingresso, file/sec negli asset. Per lo scenario di imposta le proprietà seguenti:

    1.  **Tipo di localizzatore** > **progressivo**.

    2.  Il **data** e **ora** verrà automaticamente impostato per l'utente, la data corrente, un momento nel futuro (100 anni in questo caso). Lasciare invariata o modificandola in base alle proprie.

    > [!NOTE]
    > Per altre informazioni sui localizzatori e ciò che è possibile scegliere, visitare il [documentazione di servizi multimediali di Azure](https://docs.microsoft.com/azure/media-services/media-services-concepts).

24. Nella parte inferiore del pannello, fare clic sui **Add** pulsante.

    ![Il portale di Azure](images/AzureLabs-Lab6-25.png)

25. Il video viene pubblicato e può essere trasmessi tramite il relativo endpoint. Ulteriormente verso il basso la pagina è una **file** sezione. Si tratta in cui saranno le diverse versioni di codificate del video. Selezionare il più alto possibile risoluzione uno (nell'immagine seguente è il file di 1920 x 960), e quindi verrà visualizzato un pannello a destra. Qui troverai una **URL di Download**. Copiare questa **Endpoint** perché verrà usato successivamente nel codice.

    ![Il portale di Azure](images/AzureLabs-Lab6-26.png)    

    ![Il portale di Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > È anche possibile premere il **riprodurre** per riprodurre il video e testarlo.

26. È ora necessario caricare il secondo video che si userà in questo laboratorio. Seguire i passaggi precedenti, ripetere lo stesso processo per il secondo video. Assicurarsi copiare il secondo **Endpoint** anche. Usare il comando seguente [collegamento per scaricare un video secondo](https://vimeo.com/214402865).

27. Dopo che entrambi i video sono stati pubblicati, si è pronti per passare al capitolo successivo.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capitolo 3 - configurazione del progetto Unity

Di seguito è una tipica configurato per lo sviluppo con la realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire **Unity** e fare clic su **New**. 

    ![Il portale di Azure](images/AzureLabs-Lab6-28.png)

2.  A questo punto si dovrà fornire un nome di progetto Unity, inserire **MR\_360VideoStreaming.**. Verificare che il tipo di progetto è impostato su **3D**. Impostare il percorso a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![Il portale di Azure](images/AzureLabs-Lab6-29.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio.** Passare a ***modificare* *preferenze*** e quindi dalla nuova finestra, passare al **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![Il portale di Azure](images/AzureLabs-Lab6-30.png)

4.  Passare quindi ad ***File* *Build Settings*** e passare alla piattaforma di **Universal Windows Platform**, facendo clic su di **Commutatore piattaforma** pulsante.

5.  Assicurarsi anche che:

    1. **Dispositivo di destinazione** è impostata su **qualsiasi dispositivo.**
    
    2.  **Tipo di compilazione** è impostata su **D3D.**

    3.  **SDK** è impostata su **installata più recente.**

    4.  **Versione di Visual Studio** è impostata su **installata più recente.**

    5.  **Compilare ed eseguire** è impostata su **computer locale.**

    6.  Non è necessario configurare **scene** subito, perché questi valori verranno impostati in un secondo momento.

    7.  Le impostazioni rimanenti devono essere lasciate come impostazione predefinita per il momento.

        ![Impostazione del progetto Unity](images/AzureLabs-Lab6-31.png)

6.  Nel **Build Settings** finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il **Inspector** si trova. 

7. In questo pannello, alcune impostazioni devono essere verificati:

    1.  Nel **altre impostazioni** scheda:

        1.  **Scripting** **versione Runtime** deve essere **stabile** (.NET 3.5 equivalente).

        2. **Back-end di scripting** deve essere **.NET.**

        3. **Livello di compatibilità delle API** deve essere **.NET 4.6.**

            ![Impostazione del progetto Unity](images/AzureLabs-Lab6-32.png)

    2.  Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.

        ![Impostazione del progetto Unity](images/AzureLabs-Lab6-33.png)

    3.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        - **InternetClient**

            ![Impostazione del progetto Unity](images/AzureLabs-Lab6-34.png)

8.  Una volta apportate queste modifiche, chiudere la **Build Settings** finestra.

9.  Salvare il progetto **File* *Salva progetto**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capitolo 4 - importazione del pacchetto InsideOutSphere Unity

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importarlo nel progetto come un [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione **capitolo 5**. È comunque necessario creare un progetto Unity.

Per questo corso si sarà necessario scaricare un pacchetto di Asset Unity denominati [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).

Importazione sulle procedure di **file unitypackage**:

1.  Con il dashboard di Unity fronte, fare clic su **Assets** nel menu nella parte superiore della schermata, quindi fare clic su **Importa pacchetto > pacchetto personalizzato**.

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-35.png)

2.  Usare il selettore file per selezionare i **InsideOutSphere.unitypackage** del pacchetto e fare clic su **Open**. Verrà visualizzato un elenco di componenti per questo asset all'utente. Confermare l'importazione facendo **importare**.

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-36.png)

3.  Una volta completato l'importazione, si noteranno tre nuove cartelle, **materiali**, **modelli**, e **Prefabs**, sono state aggiunte ad il **asset**cartella. Questo tipo di struttura di cartelle è tipico per i progetti Unity.

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-37.png)

    1.  Aprire il **modelli** cartella e si noterà che il **InsideOutSphere** modello è stato importato.

    2.  All'interno di **materiali** cartella troveranno le **InsideOutSpheres** materiale *lambert1*, insieme a un materiale chiamato *ButtonMaterial*, che viene usato per il GazeButton, che viene visualizzata a breve.

    3.  Il **Prefabs** cartella contiene le **InsideOutSphere** prefab che contiene sia il **InsideOutSphere** *modello* e la  *GazeButton*.

    4.  **Non è incluso alcun codice**, si scriverà il codice seguendo questo corso.


4.  All'interno di **gerarchia**, selezionare la **Main Camera** dell'oggetto e aggiornare i componenti seguenti:

    1.  **Transform**

        1.  Posizione = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotazione = **X**: 0, **Y**: 0, **Z**: 0.

        3. Scala **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Fotocamera**

        1. **Cancellare i flag**: Colore a tinta unita.

        2.  **I piani di ritaglio**: In prossimità di: 0,1, a questo momento: 6.

            ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-38.png)

5.  Passare al **Prefab** cartella e quindi trascinare il **InsideOutSphere** prefab nel **gerarchia** pannello.

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-39.png)

6.  Espandere la **InsideOutSphere** dell'oggetto all'interno di **gerarchia** facendo clic sulla piccola freccia accanto a esso. Si noterà una **figlio** oggetto sotto il chiamato **GazeButton**. Questo verrà utilizzato per modificare le scene e pertanto i video.

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-40.png)

7.  Nella finestra di controllo fare clic sui **InsideOutSphere**del componente di trasformazione, assicurarsi che siano impostate le proprietà seguenti:

    |            |    TRASFORMAZIONE - POSIZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRASFORMAZIONE - ROTAZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORM - SCALE     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-41.png)

8.  Fare clic sui **GazeButton** oggetto figlio e set relativo **trasformare** come indicato di seguito:

    |            |    TRASFORMAZIONE - POSIZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    TRASFORMAZIONE - ROTAZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORM - SCALE     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importazione del pacchetto Unity InsideOutSphere](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capitolo 5 - creare la classe VideoController

Il **VideoController** classe ne ospita i due endpoint di video che verrà usato per trasmettere il contenuto dal servizio multimediale di Azure.

Per creare questa classe:

1.  Fare doppio clic nella **cartella Asset**che si trova nel **Project** pannello e fare clic su **Crea > cartella**. Denominare la cartella **script**.

    ![Creare la classe VideoController](images/AzureLabs-Lab6-43.png)

    ![Creare la classe VideoController](images/AzureLabs-Lab6-44.png)

2.  Fare doppio clic sui **script** cartella per aprirla.

3.  Fare doppio clic all'interno della cartella, quindi fare clic su **Crea > C\# Script**. Denominare lo script **VideoController**.

    ![Creare la classe VideoController](images/AzureLabs-Lab6-45.png)

4.  Fare doppio clic su nuova **VideoController** script per aprirlo con **Visual Studio 2017.**

    ![Creare la classe VideoController](images/AzureLabs-Lab6-46.png)

5.  Aggiornare gli spazi dei nomi nella parte superiore del file di codice come segue:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Immettere le seguenti variabili nel **VideoController** classe, insieme con la **Awake()** metodo:

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

7.  È arrivato il momento di immettere gli endpoint dai tuoi video di servizi multimediali di Azure:

    1.  Il primo nel *video1endpoint* variabile.
    
    2.  La seconda nel *video2endpoint* variabile.

    > [!WARNING]
    > Si verifica un problema noto con usando *https* in Unity, con versione 2017.4.1f1. Se i video di forniscono un errore in play, provare a utilizzare 'http'.

8.  Successivamente, il **Start ()** metodo deve essere modificato. Questo metodo verrà attivato ogni volta che l'utente passa scena (cambio, di conseguenza, il video) esaminando il pulsante estasiati.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Seguendo la **Start ()** metodo, inserire il **playVideo ()** *IEnumerator* metodo, che verrà usato per avviare i video facilmente (in modo che non si verifica alcuna segnalazione).

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

10. Quest'ultimo metodo è necessario per questa classe è il **ChangeScene()** metodo, che verrà usato per scambiare tra le scene.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > Il **ChangeScene()** metodo utilizza un comodo C\# funzionalità denominata di *operatore condizionale*. In questo modo le condizioni da controllare e quindi i valori restituiti in base il risultato della verifica, tutto all'interno di una singola istruzione. Seguire questo [collegamento per altre informazioni sull'operatore condizionale](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

11. Salvare le modifiche in Visual Studio prima di tornare a Unity.

12. Indietro nell'Editor di Unity, fare clic e trascinare il **VideoController** classe [da] {.underline} il **script** cartella per il **Main Camera** dell'oggetto nel  **Gerarchia** pannello.

13. Fare clic sui **Main Camera** ed esaminare le **Pannello di controllo**. Si noterà che all'interno del componente di Script appena aggiunto, vi è un campo con un valore vuoto. Si tratta di un campo di riferimento, fa riferimento a variabili pubbliche all'interno del codice.

14. Trascinare il **InsideOutSphere** dall'oggetto il **Pannello di gerarchia** per il **sfera** slot, come illustrato nell'immagine seguente.

    ![Creare la classe VideoController](images/AzureLabs-Lab6-47.png)
    ![creare la classe VideoController](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capitolo 6: creare la classe sguardo

Questa classe è responsabile per la creazione di un **Raycast** che beprojected inoltrerà dalle **Main Camera**, per rilevare l'oggetto sta guardando l'utente. In questo caso, il **Raycast** sarà necessario identificare se l'utente sta guardando il **GazeButton** oggetti nella scena e attivare un comportamento.

Per creare questa classe:

1.  Andare alla **script** cartella creata in precedenza.

2.  Fare doppio clic nella **Project** Pannello di **creare* *C\# Script**. Denominare lo script **estasiati**.

3.  Fare doppio clic su nuova ***estasiati*** script per aprirlo con **Visual Studio 2017.**

4.  Verificare che sia lo spazio dei nomi seguente all'inizio dello script e rimuovere tutte le altre:

    ```csharp
    using UnityEngine;
    ```

5.  Quindi aggiungere le variabili seguenti all'interno di **estasiati** classe:

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

6.  Il codice per il **Awake()** e **Start ()** metodi deve ora essere aggiunto.

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

7.  Aggiungere il codice seguente nel **Update ()** metodo per proiettare un Raycast e rilevare il calo di destinazione:

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

9.  Fare clic e trascinare il **estasiati** classe dalla cartella degli script per l'oggetto Main Camera nel **gerarchia** pannello.

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capitolo 7 - installazione le due scene di Unity

Lo scopo di questo capitolo è per configurare le due scene, ognuno dei quali ospita un video in stream. Verranno duplicati della scena è già stato creato, in modo che non devi reimpostarlo, anche se si modificherà quindi la nuova scena, in modo che il *GazeButton* oggetto è in una posizione diversa e ha un aspetto diverso. Ciò sta a indicare come cambiare tra le scene.

1.  Eseguire questa operazione passando a **File > Salva scena come...** . Verrà visualizzata una finestra di salvataggio. Scegliere il **nuova cartella** pulsante.

    ![Capitolo 7 - installazione le due scene di Unity](images/AzureLabs-Lab6-49.png)

2.  Denominare la cartella **scene**.

3.  Il **Salva scena** finestra saranno ancora aperta. Aprire l'appena creato **scene** cartella.

4.  Nel **nome File:** campo di testo, digitare **VideoScene1**, quindi premere **Salva**.

5.  In Unity, aprire il **scene** la cartella e quindi fare clic sui **VideoScene1** file. Utilizzare la tastiera, premere **Ctrl + D** verranno duplicati tale scena

    > [!TIP]
    > Il **duplicato** comandi possono essere eseguiti anche passando a **Modifica > duplicato**.

6.  Unity automaticamente incrementare il numero di nomi di scena, ma verificare, in modo che corrisponda il codice inserito in precedenza.

    >  È necessario disporre **VideoScene1** e **VideoScene2**.

7.  Con le due scene, andare al **File > Build Settings**. Con il **Build Settings** finestra aperta, trascinare gli in modo invisibile per il **scene nella compilazione** sezione.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > È possibile selezionare entrambe le scene le **scene** cartella tramite azienda il **Ctrl** pulsante, quindi mouse ogni scena e infine trascinare entrambi in.

8.  Chiudi il **Build Settings** finestra e fare doppio clic sul **VideoScene2**.

9.  Con il secondo scena aperta, fare clic sul **GazeButton** oggetto figlio del **InsideOutSphere**e impostare la trasformazione corrispondente come indicato di seguito:

    |            |    TRASFORMAZIONE - POSIZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    TRASFORMAZIONE - ROTAZIONE   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORM - SCALE     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Con il **GazeButton** figlio ancora selezionato, cercare nel **Inspector** e il **Mesh filtro**. Fare clic accanto alla destinazione little il **Mesh** campo di riferimento:

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-51.png)

11. Oggetto **Mesh selezionare** verrà visualizzata la finestra popup. Fare doppio clic il **cubo** mesh dall'elenco dei **asset**.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-52.png)

12. Il **filtro Mesh** consente di aggiornare e ora da un **cubo**. A questo punto, fare clic sui **a forma di ingranaggio** icona accanto a **sfera Collider** e fare clic su **Rimuovi componente**, eliminare l'oggetto collider da questo oggetto.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-53.png)

13. Con il **GazeButton** ancora selezionato, fare clic sul **Add Component** nella parte inferiore del **Inspector**. Nel campo di ricerca, digitare **finestra**, e **casella Collider** sarà un'opzione: fare clic per aggiungere un **casella Collider** per il **GazeButton** oggetto .

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-54.png)

14. Il **GazeButton** è ora aggiornata parzialmente, per un aspetto diverso, tuttavia, ora si creerà un nuovo **materiale**, in modo che il servizio ha un aspetto completamente diverso ed è più facile da riconoscere come un oggetto diverso, rispetto al oggetto in prima scena.

15. Passare alle **materiali** cartella, all'interno di **pannello progetto**. Duplica il **ButtonMaterial** materiale (premere **Ctrl** + **1!d** sulla tastiera o fare clic sul **materiale**, quindi dal **Edit** opzione di menu, selezionare file **duplicato**).

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-55.png)
    ![capitolo 7: configurare le due scene di Unity](images/AzureLabs-Lab6-56.png)

16. Selezionare la nuova **ButtonMaterial** materiale (qui denominata **1 ButtonMaterial**) e all'interno di **Inspector**, fare clic sul **Albedo** colore finestra. Verrà visualizzata una finestra popup, in cui è possibile selezionare un altro colore (scegliere a seconda di quale si desidera), quindi chiudere la finestra popup. Il materiale sarà una propria istanza e diversi con la versione originale.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-57.png)

17. Trascinare la nuova **materiale** nel **GazeButton** figlio, a questo punto aggiornare completamente aspetto, in modo che risulti facilmente distinguibile dal primo pulsante in background.

    ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-58.png)

18. A questo punto è possibile testare il progetto nell'Editor prima di compilare il progetto UWP.

    -  Premere il **riprodurre** pulsante il **Editor** e wear le cuffie.

        ![Capitolo 7: Configurare le due scene di Unity](images/AzureLabs-Lab6-59.png)

19. Esaminare i due **GazeButton** oggetti da passare tra il primo e il secondo video.

## <a name="chapter-8---build-the-uwp-solution"></a>Capitolo 8 - compilare la soluzione di piattaforma UWP

Dopo aver verificato che l'editor non dispone di alcun errore, sei pronto per la compilazione.

Per compilare:

1.  Salvare nella scena corrente facendo clic su **File > Salva**.

2.  Selezionare la casella denominata **C Unity\# progetti** (questo è importante poiché ciò permette di modificare le classi dopo la compilazione è stata completata).

3.  Passare a **File > Build Settings**, fare clic su **compilazione**.

4.  Viene chiesto di selezionare la cartella in cui si desidera buildthe soluzione.

5.  Creare un **COMPILAZIONI** cartella e all'interno della cartella creare un'altra cartella con un nome appropriato di propria scelta.

6.  Fare clic sulla nuova cartella e quindi fare clic su **selezionare la cartella**, pertanto, per scegliere quella cartella, per avviare la compilazione nel percorso specificato.

    ![Capitolo 8 - Compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab6-60.png)
    ![capitolo 8 - compilare la soluzione di piattaforma UWP](images/AzureLabs-Lab6-61.png)

7.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione.

## <a name="chapter-9---deploy-on-local-machine"></a>Capitolo 9 - distribuire nel computer locale

Dopo aver completata la compilazione, un **Esplora File** verrà visualizzata la finestra in corrispondenza della posizione della compilazione. Aprire la cartella è denominata e compilata per, quindi fare doppio clic sul file di soluzione (sln) da quella cartella, aprire la soluzione con Visual Studio 2017.

L'unico a sinistra è distribuire l'app nel computer (o *computer locale*).

Per distribuire nel computer locale:

1.  Nelle **Visual Studio 2017**, aprire il file di soluzione che è stato appena creato.

2.  Nel **piattaforma soluzione**, selezionare **x86, computer locale**.

3.  Nel **configurazione della soluzione** selezionate **Debug**.

    ![Capitolo 9 - Distribuire nel computer locale](images/AzureLabs-Lab6-62.png)

4.  A questo punto, è necessario ripristinare tutti i pacchetti della soluzione. Fare clic sui **soluzione**, fare clic su **Ripristina pacchetti NuGet per la soluzione...**

    > [!NOTE] 
    > Ciò avviene perché i pacchetti che Unity compilate necessarie da impostare come destinazione per l'uso con i riferimenti del computer locale.

5.  Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer. Visual Studio verrà innanzitutto compilare e distribuire l'applicazione.

6.  L'App deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.

    ![Capitolo 9 - Distribuire nel computer locale](images/AzureLabs-Lab6-63.png)

Quando si esegue l'applicazione di realtà mista, saranno è essere all'interno di **InsideOutSphere** modello che è stato utilizzato all'interno dell'app. Questo sfera saranno in cui il video verrà trasmesso, fornendo una visualizzazione a 360 gradi, di video in ingresso (che per questo tipo di punto di vista è stato filmato). Non sorprendere che se il video richiede un paio di secondi per caricare, l'app è soggetto alle velocità di Internet disponibile, come il video deve essere recuperate e quindi scaricati, pertanto per lo streaming nell'app.
Quando si è pronti, modificare le scene e aprire il secondo video, gazing alla sfera rossa! Quindi è possibile tornare indietro, mediante il cubo blu nella scena secondo!

## <a name="your-finished-azure-media-service-application"></a>L'applicazione di servizi multimediali di Azure completata
 
Complimenti, è stata compilata un'app per realtà mista che si avvale di servizi multimediali di Azure per trasmettere in streaming 360 video.

![risultato di Lab](images/AzureLabs-Lab6-00.png)

![risultato di Lab](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Esercizi bonus

**Esercizio 1**

È assolutamente possibile utilizzare solo un'unica scena per modificare i video all'interno di questa esercitazione. Provare a usare l'applicazione e trasformarlo in un'unica scena. Aggiungere anche un altro video alla combinazione.

**Esercizio 2**

Sperimentare con Unity e Azure e provare a implementare la possibilità per l'app selezionare automaticamente un video con una dimensione di file diverso, a seconda della complessità di una connessione a Internet.


