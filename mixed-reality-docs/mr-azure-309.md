---
title: MR e Azure 309-Application Insights
description: Completare questo corso per informazioni su come raccogliere i dati analitici sul comportamento dell'utente all'interno di un'applicazione di realtà mista usando il servizio applicazione Azure Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, Application Insights, hololens, immersive, VR
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694567"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR e Azure 309: Application Insights

![prodotto finale-inizio](images/AzureLabs-Lab309-00.png)

In questo corso si apprenderà come aggiungere Application Insights funzionalità a un'applicazione di realtà mista usando l'API applicazione Azure Insights per raccogliere le analisi relative al comportamento degli utenti.

Application Insights è un servizio Microsoft, che consente agli sviluppatori di raccogliere le analisi dalle applicazioni e di gestirle da un portale di facile utilizzo. L'analisi può essere di qualsiasi tipo, dalle prestazioni alle informazioni personalizzate da raccogliere. Per ulteriori informazioni, visitare la [pagina Application Insights](https://azure.microsoft.com/services/application-insights/).

Dopo aver completato questo corso, si disporrà di un'applicazione con un auricolare immersiva a realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  Consente all'utente di guardare e spostarsi in una scena.
2.  Attivare l'invio di analisi al *servizio Application Insights*, tramite l'uso di sguardi e prossimità di oggetti in scena.
3.  L'app chiamerà anche il servizio, recuperando le informazioni sull'oggetto che è stato più o meno affrontato dall'utente nelle ultime 24 ore. Tale oggetto cambierà il colore in verde.

Questo corso spiegherà come ottenere i risultati dal servizio Application Insights in un'applicazione di esempio basata su Unity. Sarà necessario applicare questi concetti a un'applicazione personalizzata che è possibile creare.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 309: Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente sugli auricolari per la realtà mista (VR) di Windows, è anche possibile applicare le informazioni apprese in questo corso a Microsoft HoloLens. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcuni echi durante l'acquisizione vocale.

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
- Un set di cuffie con un microfono incorporato (se la cuffia non dispone di un MIC e di altoparlanti predefiniti)
- Accesso a Internet per il programma di installazione di Azure e Application Insights il recupero dei dati

## <a name="before-you-start"></a>Prima di iniziare

Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).

> [!WARNING] 
> Tenere presente che i dati che passano a *Application Insights* richiedono tempo, quindi possono essere pazienti. Se si vuole controllare se il servizio ha ricevuto i dati, vedere il [capitolo 14](#chapter-14---the-application-insights-service-portal), che illustra come spostarsi nel portale.

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1-portale di Azure

Per usare *Application Insights*, è necessario creare e configurare un servizio di *Application Insights* nel portale di Azure.

1.  Accedere al [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **nuovo** nell'angolo in alto a sinistra e cercare *Application Insights*e premere **invio**.

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **Crea una risorsa**, nei portali più recenti.

    ![Portale di Azure](images/AzureLabs-Lab309-01.png)

3.  La nuova pagina a destra fornirà una descrizione del servizio *applicazione Azure Insights* . Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![Portale di Azure](images/AzureLabs-Lab309-02.png)

4.  Una volta fatto clic su **Crea**:

    1.  Inserire il **nome** desiderato per l'istanza del servizio.

    2.  In **tipo di applicazione**selezionare **generale**.

    3.  Selezionare una **sottoscrizione**appropriata.

    4.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, [vedere l'articolo relativo al gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Selezionare un **percorso**.

    6.  Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.

    7.  Selezionare **Create**.

        ![Portale di Azure](images/AzureLabs-Lab309-03.png)

5.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Portale di Azure](images/AzureLabs-Lab309-04.png)

7.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![Portale di Azure](images/AzureLabs-Lab309-05.png)

8.  Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del *servizio Application Insights* .

    ![Portale di Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Questa pagina Web è aperta e facile da accedere. si tornerà spesso a visualizzare i dati raccolti.

    > [!IMPORTANT]
    > Per implementare Application Insights, sarà necessario usare tre (3) valori specifici: **Chiave di strumentazione**, **ID applicazione**e **chiave API**. Di seguito viene illustrato come recuperare questi valori dal servizio. Assicurarsi di prendere nota di questi valori in una pagina del *blocco note* vuota, perché saranno presto usati nel codice.

9.  Per trovare la **chiave di strumentazione**, è necessario scorrere verso il basso l'elenco di funzioni del servizio e fare clic su **Proprietà**. la scheda visualizzata mostrerà la **chiave del servizio**.

    ![Portale di Azure](images/AzureLabs-Lab309-07.png)

10. Di seguito sono riportate alcune **Proprietà**che consentono di **accedere all'API**, che è necessario fare clic su. Il pannello a destra fornirà l' **ID applicazione** dell'app.

    ![Portale di Azure](images/AzureLabs-Lab309-08.png)

11. Con il pannello **ID applicazione** ancora aperto, fare clic su **Crea chiave API**, che consente di aprire il pannello *Crea chiave API* .

    ![Portale di Azure](images/AzureLabs-Lab309-09.png)

12. All'interno del pannello Apri *chiave API crea* Digitare una descrizione e quindi **le tre caselle**.

13. Fare clic su **Genera chiave**. La **chiave API** verrà creata e visualizzata. 

    ![Portale di Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Questa è l'unica volta in cui verrà visualizzata la **chiave del servizio** , quindi assicurarsi di crearne una copia adesso.

## <a name="chapter-2---set-up-the-unity-project"></a>Capitolo 2: configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire *Unity* e fare clic su **New**.

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-11.png)

2.  A questo punto è necessario specificare un nome di progetto Unity **,\_inserire\_Azure\_Application Insights**. Verificare che il *modello* sia impostato su **3D**. Impostare il *percorso* su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-12.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **modifica \> preferenze** e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-13.png)

4.  Passare quindi a **impostazioni di \> compilazione file** e passare alla piattaforma **piattaforma UWP (Universal Windows Platform)** , facendo clic sul pulsante **Switch Platform** .

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-14.png)

5.  Passare a **impostazioni \> di compilazione file** e verificare che:

    1.  Il **dispositivo di destinazione** è impostato su **qualsiasi dispositivo**

        > Per Microsoft HoloLens, impostare **dispositivo di destinazione** su *HoloLens*.

    2.  Il **tipo di compilazione** è impostato su **D3D**

    3.  **SDK** è impostato sull' **ultima versione installata**

    4.  **Compilazione ed esecuzione** è impostato su **computer locale**

    5.  Salvare la scena e aggiungerla alla compilazione.

        1.  A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-15.png)

        2. Creare una nuova cartella per questo e qualsiasi scena futura, quindi fare clic sul pulsante **nuova cartella** per creare una nuova cartella, denominarla **Scenes**.

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-16.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file:* testo digitare **ApplicationInsightsScene**e quindi fare clic su **Salva**.

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-17.png)

6.  Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.

7.  Nella finestra **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il **controllo** .

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-18.png)

8. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **altre impostazioni** :

        1.  Creazione di **script** La **versione di runtime** deve essere sperimentale **(equivalente a .NET 4,6)** , che attiverà la necessità di riavviare l'editor.

        2.  Il **back-end** di scripting deve essere **.NET**

        3.  Il **livello di compatibilità API** deve essere **.NET 4,6**

        ![Configurare il progetto Unity](images/AzureLabs-Lab309-19.png)

    2.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        - **InternetClient**     

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-20.png)

    3.  Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![Configurare il progetto Unity](images/AzureLabs-Lab309-21.png)

9.  Nelle **impostazioni di compilazione**, **i C# progetti Unity** non sono più disattivati; Selezionare la casella di controllo accanto a questo.

10.  Chiudere la finestra impostazioni di compilazione.

11.  Salva la scena e il progetto **(**  > **progetto**Salva**scena/Salva file** > ).


## <a name="chapter-3---import-the-unity-package"></a>Capitolo 3: importare il pacchetto Unity

> [!IMPORTANT]
> Se si vuole ignorare i componenti di *configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricare questo [Azure-Mr-309. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)e importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html). Questo conterrà anche le dll del capitolo successivo. Dopo l'importazione, continuare con il [**capitolo 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Per usare Application Insights in Unity, è necessario importare la DLL, insieme alla DLL Newtonsoft. Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare Application Insights nel progetto, assicurarsi di aver [scaricato il '. file unitypackage Tools ', contenente i plug](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)-in. Eseguire quindi le operazioni seguenti:

1.  Aggiungere il **file unitypackage Tools** a Unity usando l'opzione di menu  **\> asset \> Import Package Custom Package** .

2.  Nella casella **Importa pacchetto Unity** visualizzata verificare che siano selezionati tutti gli elementi in (e inclusi) **plug** -in.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-22.png)

3.  Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.

4.  Passare alla cartella **Insights** in **plug** -in nella visualizzazione del progetto e selezionare *solo*i plug-in seguenti:

    -   Microsoft. ApplicationInsights

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-23.png)

5.  Con questo *plug* -in selezionato, verificare che **qualsiasi piattaforma** sia deselezionata, quindi assicurarsi che  **WSAPlayer** sia deselezionata, quindi fare clic su **applica**. Questa operazione è sufficiente per confermare che i file sono configurati correttamente.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Contrassegnando i plug-in come questo, questi vengono configurati per essere usati solo nell'editor di Unity. Nella cartella WSA è presente un set di dll diverso che verrà usato dopo l'esportazione del progetto da Unity.

6.  Successivamente, è necessario aprire la cartella **WSA** , all'interno della  cartella Insights. Viene visualizzata una copia dello stesso file appena configurato. Selezionare questo file, quindi nel controllo verificare che **qualsiasi piattaforma** sia deselezionata , quindi assicurarsi che sia **selezionato** **solo** **WSAPlayer** . Fare clic su **Applica**.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25.png)

7. A questo punto, è necessario seguire i **passaggi 4-6**, ma per i plug-in *Newtonsoft* . Vedere lo screenshot seguente per il risultato dell'aspetto.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Capitolo 4: impostare la fotocamera e i controlli utente

In questo capitolo verrà illustrato come configurare la fotocamera e i controlli per consentire all'utente di visualizzare e spostare la scena.

1.  Fare clic con il pulsante destro del mouse in un'area vuota nel pannello gerarchia e quindi su **Crea** > **vuoto**.

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-26.png)

2.  Rinominare il nuovo GameObject vuoto nell' **elemento padre della fotocamera**.

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-27.png)

3.  Fare clic con il pulsante destro del mouse in un'area vuota nel pannello gerarchia, quindi su **oggetto 3D**, quindi su **sfera**.

4.  Rinominare la sfera nella **parte destra**.

5.  Imposta la **scala di trasformazione** della mano destra su **0,1, 0,1, 0,1**

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-28.png)

6.  Rimuovere il componente **Sphere Collider** dalla destra facendo clic sull'ingranaggio nel  componente *Sphere Collider* , quindi **rimuovere Component**.

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-29.png)

7.  Nel pannello gerarchia trascinare la **fotocamera principale** e gli oggetti **destro** nell'oggetto padre della **fotocamera** .

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-30.png)

8.  Impostare la **posizione di trasformazione** della **fotocamera principale** e dell'oggetto **destro** su **0, 0, 0**.

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-31.png)

    ![Configurare la fotocamera e i controlli utente](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Capitolo 5: configurare gli oggetti nella scena Unity

Verranno ora create alcune forme di base per la scena, con cui l'utente può interagire.

1.  Fare clic con il pulsante destro del mouse in un'area vuota nel *Pannello gerarchia*, quindi su **oggetto 3D**, quindi selezionare **piano**.

2.  Impostare la **posizione di trasformazione** del piano su **0,-1, 0**.

3.  Impostare **scala trasformazione** piano su **5, 1, 5**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-33.png)

4.  Creare un materiale di base da usare con l'oggetto **piano** , in modo che le altre forme siano più semplici da vedere. Passare al *Pannello del progetto*, fare clic con il pulsante destro del mouse, quindi scegliere **Crea**, seguito da **cartella**, per creare una nuova cartella. Assegnare un nome ai **materiali**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-34.png) ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-35.png)

5.  Aprire la  cartella Materials, quindi fare clic con il pulsante destro del mouse, scegliere **Crea**, quindi **Material**, per creare un nuovo materiale. Denominarlo **blu**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-36.png) ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-37.png)

6.  Con il nuovo materiale **blu** selezionato, esaminare il *controllo*e fare clic sulla finestra rettangolare accanto a **albedo**. Selezionare un colore blu (l'immagine seguente è **il colore esadecimale: \#3592FFFF**). Una volta scelto, fare clic sul pulsante Chiudi.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-38.png)

7.  Trascinare il nuovo materiale dalla cartella **Materials** , nel **piano**appena creato, all'interno della scena o rilasciarlo sull'oggetto **piano** all'interno della *gerarchia*.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-39.png)

8.  Fare clic con il pulsante destro del mouse in un'area vuota nel *Pannello gerarchia*, quindi su **oggetto 3D, capsula**.

    -  Con la **capsula** selezionata, modificare la  *posizione* di trasformazione in: **-10, 1, 0**.

9.  Fare clic con il pulsante destro del mouse in un'area vuota nel *Pannello gerarchia*, quindi su **oggetto 3D, cubo**.

    -  Con il **cubo** selezionato, modificare la  *posizione* di trasformazione in: **0, 0, 10**.

10. Fare clic con il pulsante destro del mouse in un'area vuota nel *Pannello gerarchia*, quindi su **oggetto 3D, sfera**.

    -  Con la **sfera** selezionata, modificare la  *posizione* di trasformazione in: **10, 0, 0**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Questi valori di *posizione* sono *suggerimenti*. È possibile impostare le posizioni degli oggetti su quello che si desidera, sebbene sia più semplice per l'utente dell'applicazione se le distanze degli oggetti non sono troppo distanti dalla fotocamera.

11. Quando l'applicazione è in esecuzione, deve essere in grado di identificare gli oggetti all'interno della scena, a tale scopo è necessario contrassegnarli. Selezionare uno degli oggetti e nel pannello di *controllo* fare clic su **Aggiungi tag...** , che consente di scambiare il *controllo* con il pannello **tag & livelli** .

    ![Configurare gli oggetti nella scena](images/AzureLabs-Lab309-41.png) Unity![](images/AzureLabs-Lab309-42.png)

12. Fare clic sul simbolo **+ (segno più)** , quindi digitare il nome del tag come **ObjectInScene**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Se si usa un nome diverso per il tag, è necessario assicurarsi che questa modifica sia anche *DataFromAnalytics*, *ObjectTrigger*e *sguardi*, script in un secondo momento, in modo che gli oggetti vengano trovati e rilevati all'interno della scena.

13. Con il tag creato, è ora necessario applicarlo a tutti e tre gli oggetti. Dalla *gerarchia*tenere premuto il tasto **MAIUSC** , quindi fare clic su **capsula**, **cubo**e **sfera**, oggetti, quindi, nel *controllo*, fare clic sul menu a discesa insieme a **tag**, quindi fare clic su *ObjectInScene* Tag creato.

    ![Configurare gli oggetti nella scena](images/AzureLabs-Lab309-44.png) Unity![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Capitolo 6: creare la classe ApplicationInsightsTracker

Il primo script che è necessario creare è **ApplicationInsightsTracker**, responsabile di:

1.  Creazione di eventi in base alle interazioni dell'utente da inviare ad applicazione Azure Insights.

2. Creazione di nomi di evento appropriati, a seconda dell'interazione dell'utente.

3. Invio di eventi all'istanza del servizio Application Insights.

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse sul *Pannello del progetto*, quindi scegliere **Crea** > **cartella**. Denominare gli **script**della cartella.

    ![Creazione della classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Creazione della classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  Con la  cartella Scripts creata, fare doppio clic su di essa per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse su **Crea**  >   **C# script**. Denominare lo script **ApplicationInsightsTracker**.

3.  Fare doppio clic sul nuovo script **ApplicationInsightsTracker** per aprirlo con **Visual Studio**.

4.  Aggiornare gli spazi dei nomi nella parte superiore dello script come indicato di seguito:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  All'interno della classe inserire le variabili seguenti:

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > Impostare i valori **instrumentationKey, ApplicationId e API_Key** in modo appropriato, usando le *chiavi del servizio* del portale di Azure, come indicato nel [capitolo 1](#chapter-1---the-azure-portal), passaggio 9 e versioni successive.

6.  Aggiungere quindi i metodi **Start ()** e **svegli ()** , che verranno chiamati al momento dell'inizializzazione della classe:

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  Aggiungere i metodi responsabili dell'invio degli eventi e delle metriche registrati dall'applicazione:

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-7---create-the-gaze-script"></a>Capitolo 7: creare lo script di sguardi

Lo script successivo da creare è lo **sguardo** . Questo script è responsabile della creazione di un *Raycast* che verrà proiettato in futuro dalla *fotocamera principale*, per individuare l'oggetto analizzato dall'utente. In questo caso, *Raycast* deve identificare se l'utente sta esaminando un oggetto con il tag **ObjectInScene** , quindi contare il tempo che *l'utente guarda* a tale oggetto.

1.  Fare doppio clic sulla cartella **Scripts** per aprirla.

2.  Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**. Denominare **lo script.**

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Sostituire il codice esistente con quello seguente:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  È ora necessario aggiungere il codice per i metodi **svegli ()** e **Start ()** .

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  All'interno della classe **sguardi** aggiungere il codice seguente nel metodo **Update ()** per proiettare un *Raycast* e rilevare il raggiungimento della destinazione:

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  Aggiungere il metodo **ResetFocusedObject ()** per inviare dati a **Application Insights** quando l'utente ha esaminato un oggetto.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  Lo script di **sguardi** è stato completato. Salvare le modifiche in *Visual Studio* prima di tornare a Unity.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Capitolo 8: creare la classe ObjectTrigger

Lo script successivo che è necessario creare è **ObjectTrigger**, responsabile di:

- Aggiunta di componenti necessari per la collisione alla fotocamera principale.
- Rilevamento della presenza della fotocamera vicino a un oggetto contrassegnato come **ObjectInScene**.

Per creare lo script:

1.  Fare doppio clic sulla cartella **Scripts** per aprirla.

2.  Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**. Denominare lo script **ObjectTrigger**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio. Sostituire il codice esistente con quello seguente:

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Capitolo 9: creare la classe DataFromAnalytics

A questo punto sarà necessario creare lo script **DataFromAnalytics** , responsabile di:

- Recupero dei dati di analisi sull'oggetto che è stato più utilizzato dalla fotocamera.
- Usando le *chiavi del servizio*, che consentono la comunicazione con l'istanza del servizio applicazione Azure Insights.
- Ordinamento degli oggetti in scena, in base al quale ha il numero massimo di eventi.
- Modifica del colore del materiale, dell'oggetto più affrontato, in *verde*.

Per creare lo script:

1.  Fare doppio clic sulla cartella **Scripts** per aprirla.

2.  Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**. Denominare lo script **DataFromAnalytics**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserire gli spazi dei nomi seguenti:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  All'interno dello script, inserire quanto segue:

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  All'interno della classe **DataFromAnalytics** , subito dopo il metodo **Start ()** , aggiungere il metodo seguente denominato **FetchAnalytics ()** . Questo metodo è responsabile del popolamento dell'elenco di coppie chiave-valore, con *GameObject* e un numero di conteggio eventi segnaposto. Inizializza quindi la coroutine **GetWebRequest ()** . La struttura di query della chiamata a *Application Insights* è disponibile anche all'interno di questo metodo, come endpoint dell' *URL della query* .

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  Al di sotto del metodo **FetchAnalytics ()** aggiungere un metodo denominato **GetWebRequest ()** che restituisce un *IEnumerator*. Questo metodo è responsabile della richiesta del numero di volte in cui un evento, corrispondente a un *GameObject*specifico, è stato chiamato all'interno *Application Insights*. Quando tutte le query inviate sono state restituite, viene chiamato il metodo **DetermineWinner ()** .

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  Il metodo successivo è **DetermineWinner ()** , che ordina l'elenco di coppie *GameObject* e *int* , in base al numero massimo di eventi. Il colore del materiale di tale *GameObject* viene quindi modificato in *verde* (come feedback per il numero più alto). Viene visualizzato un messaggio con i risultati dell'analisi.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  Aggiungere la struttura della classe che verrà usata per deserializzare l'oggetto JSON, ricevuto da *Application Insights*. Aggiungere queste classi nella parte inferiore del file della classe **DataFromAnalytics** , al di **fuori** della definizione della classe.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-10---create-the-movement-class"></a>Capitolo 10: creare la classe Movement

Lo script di **spostamento** è lo script successivo che sarà necessario creare. È responsabile di:

- Lo sposti della fotocamera principale in base alla direzione che la fotocamera sta cercando.
- Aggiunta di tutti gli altri script agli oggetti scena.

Per creare lo script:

1.  Fare doppio clic sulla cartella **Scripts** per aprirla.

2.  Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**. Assegnare un nome allo **spostamento**dello script.

3.  Fare doppio clic sullo script per aprirlo con *Visual Studio*.

4.  Sostituire il codice esistente con quello seguente:

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  All'interno della classe **Movement** , *sotto* il metodo **Update ()** vuoto, inserire i metodi seguenti che consentono all'utente di usare il controller della mano per spostarsi nello spazio virtuale:

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  Aggiungere infine la chiamata al metodo all'interno del metodo **Update ()** .

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Capitolo 11-Configurazione dei riferimenti agli script

In questo capitolo è necessario inserire lo script di **spostamento** sull' **elemento padre della fotocamera** e impostare le relative destinazioni di riferimento. Tale script gestirà quindi l'inserimento degli altri script in cui devono essere.

1.  Dalla cartella **Scripts** nel *Pannello Project*trascinare lo script **Movement** nell'oggetto padre della **fotocamera** , che si trova nel *Pannello gerarchia*.

    ![Configurazione dei riferimenti agli script nella scena Unity](images/AzureLabs-Lab309-48.png)

2.  Fare clic sull' **elemento padre della fotocamera**. Nel *Pannello gerarchia*trascinare l'oggetto **destro** dal *Pannello gerarchia* alla destinazione di riferimento, **controller**, nel *Pannello di controllo*. Impostare la **velocità utente** su **5**, come illustrato nell'immagine seguente.

    ![Configurazione dei riferimenti agli script nella scena Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Capitolo 12: creare il progetto Unity

Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.

1.  Passare a **impostazioni di compilazione**(**impostazioni di compilazione** **file** > ).

2.  Nella finestra **impostazioni di compilazione** fare clic su **Compila**.

    ![Compilare il progetto Unity per la soluzione UWP](images/AzureLabs-Lab309-50.png)

3.  Verrà visualizzata una finestra di **Esplora file** con la richiesta di un percorso per la compilazione. Creare una nuova cartella (facendo clic su **nuova cartella** nell'angolo superiore sinistro) e denominarla compilata.

    ![Compilare il progetto Unity per la soluzione UWP](images/AzureLabs-Lab309-51.png)

    1.  Aprire la nuova  cartella compilazioni e creare un'altra cartella (usando una **nuova cartella** ancora una volta) e **\_denominarla Azure\_\_Application Insights**.

        ![Compilare il progetto Unity per la soluzione UWP](images/AzureLabs-Lab309-52.png)

    2.  Con la **\_cartella di\_Azure\_Application Insights** selezionata, fare clic su **Seleziona cartella**. La compilazione del progetto verrà eseguita per un minuto.

4.  Nella *compilazione*seguente verrà visualizzato **Esplora file** che indica il percorso del nuovo progetto.

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>Capitolo 13: distribuire l'app MR_Azure_Application_Insights nel computer

Per distribuire l' **\_app Application\_\_Insights di Azure** nel computer locale:

1.  Aprire il file di soluzione dell' **\_app Azure\_Application\_Insights** in **Visual Studio**.

2.  Nella **piattaforma soluzione**selezionare **x86, computer locale**.

3.  Nella **configurazione della soluzione** selezionare **debug**.

    ![Compilare il progetto Unity per la soluzione UWP](images/AzureLabs-Lab309-53.png)

4.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione al computer.

5.  L'app verrà visualizzata nell'elenco delle app installate, pronte per l'avvio.

6. Avviare l'applicazione di realtà mista.

7. Spostarsi nella scena, avvicinarsi agli oggetti e esaminarli, quando il *servizio Azure Insight* ha raccolto un numero sufficiente di dati degli eventi, imposta l'oggetto che è stato avvicinato al più verde.

> [!IMPORTANT] 
> Il tempo medio di attesa per la raccolta di *eventi e metriche* da parte del servizio richiede circa 15 minuti, in alcune occasioni potrebbe richiedere fino a 1 ora.

## <a name="chapter-14---the-application-insights-service-portal"></a>Capitolo 14-portale del servizio Application Insights

Dopo aver eseguito il roaming nella scena e aver guardato diversi oggetti, è possibile visualizzare i dati raccolti nel portale del *servizio Application Insights* .

1.  Tornare al portale del servizio Application Insights.

2.  Fare clic su *Esplora metriche*.

    ![Esaminare i dati raccolti](images/AzureLabs-Lab309-54.png)

3.  Verrà aperto in una scheda contenente il grafico che rappresenta gli *eventi e le metriche* correlate all'applicazione. Come indicato in precedenza, la visualizzazione dei dati nel grafico potrebbe richiedere del tempo (fino a un'ora)

    ![Esaminare i dati raccolti](images/AzureLabs-Lab309-55.png)

4.  Fare clic sulla *barra degli eventi* nel *totale degli eventi* in base alla versione dell'applicazione per visualizzare una suddivisione dettagliata degli eventi con i relativi nomi.

    ![Esaminare i dati raccolti](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>L'applicazione di servizio Application Insights completata

Congratulazioni, è stata creata un'app per realtà mista che sfrutta il servizio Application Insights per monitorare l'attività dell'utente all'interno dell'app.

![risultato del corso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

**Esercizio 1**

Provare a generare, anziché creare manualmente gli oggetti ObjectInScene e impostare le rispettive coordinate sul piano all'interno degli script. In questo modo, è possibile richiedere ad Azure l'oggetto più diffuso (da uno sguardo o risultati di prossimità) e *generare un altro* oggetto.

**Esercizio 2**

Ordinare i risultati del Application Insights in base all'ora, in modo da ottenere i dati più rilevanti e implementare tali dati sensibili all'ora nell'applicazione.

