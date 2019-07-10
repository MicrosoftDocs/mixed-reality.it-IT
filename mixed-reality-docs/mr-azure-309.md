---
title: MR e Azure 309 - Application insights
description: Completare questo corso di informazioni su come raccogliere analitica relative a un comportamento utente all'interno di un'applicazione di realtà mista, l'utilizzo del servizio di Azure Application Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, insights dell'applicazione, hololens, coinvolgenti, vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694567"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR e Azure 309: Insights dell'applicazione

![versione finale del prodotto-avvio](images/AzureLabs-Lab309-00.png)

In questo corso, si apprenderà come aggiungere funzionalità di Application Insights a un'applicazione di realtà mista, usando l'API di Azure Application Insights per raccogliere analitica riguardanti il comportamento degli utenti.

Application Insights è un servizio Microsoft, consentendo agli sviluppatori di raccogliere analitica dalle rispettive applicazioni e gestire da un portale facile da usare. L'analitica può essere qualsiasi elemento, da prestazioni personalizzazione delle informazioni da raccogliere. Per altre informazioni, visitare il [pagina di Application Insights](https://azure.microsoft.com/services/application-insights/).

Dopo aver completato il corso, si avrà un'applicazione di realtà mista visore VR immersivi che sarà in grado di eseguire le operazioni seguenti:

1.  Consentire all'utente estasiati e spostarsi all'interno di una scena.
2.  Attivare l'invio di analitica per la *servizio di Application Insights*, tramite l'uso di sguardo e prossimità agli oggetti nella scena.
3.  L'app chiamerà anche al momento il servizio, il recupero di informazioni sull'oggetto che è stato affrontato il massimo dall'utente, nelle ultime 24 ore. Tale oggetto cambierà il colore verde.

Questo corso ti spiegherà come ottenere i risultati da del servizio Application Insights, in un'applicazione di esempio basate su Unity. Sarà quindi compito è possibile applicare questi concetti a un'applicazione personalizzata, che potrebbe voler costruire.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 309: Insights dell'applicazione</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla auricolari (VR) coinvolgenti di realtà mista di Windows, è inoltre possibile applicare informazioni in questo corso per Microsoft HoloLens. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare HoloLens. Quando si usa HoloLens, è possibile notare alcune echo durante l'acquisizione voce.

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
- Le cuffie con un microfono incorporato (se le cuffie non ha un mic incorporati e altri relatori)
- Accesso a Internet per la configurazione di Azure e il recupero dei dati di Application Insights

## <a name="before-you-start"></a>Prima di iniziare

Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).

> [!WARNING] 
> Tenere presente, i dati in transito per *Application Insights* richiede tempo, pertanto è necessario paziente. Se si vuole verificare se il servizio ha ricevuto i dati, consultare [capitolo 14](#chapter-14---the-application-insights-service-portal), che illustrerà come esplorare il portale.

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1 - portale di Azure

Per utilizzare *Application Insights*, sarà necessario creare e configurare un' *servizio Application Insights* nel portale di Azure.

1.  Accedi per il [portale di Azure](https://portal.azure.com).

    > [!NOTE]
    > Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **New** nell'angolo in alto a sinistra e cercare *Application Insights*, fare clic su **invio**.

    > [!NOTE]
    > La parola **New** potrebbe essere stata sostituita con **crea una risorsa**, nei portali più recente.

    ![Portale di Azure](images/AzureLabs-Lab309-01.png)

3.  La nuova pagina a destra fornirà una descrizione del *Azure Application Insights* servizio. AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![Portale di Azure](images/AzureLabs-Lab309-02.png)

4.  Dopo avere fatto clic su **Create**:

    1.  Inserire la posizione desiderata **nome** per questa istanza del servizio.

    2.  Come **tipo di applicazione**, selezionare **generali**.

    3.  Selezionare un'opzione appropriata **sottoscrizione**.

    4.  Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, please [passare all'articolo di gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Selezionare una **posizione**.

    6.  È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.

    7.  Selezionare **Create**.

        ![Portale di Azure](images/AzureLabs-Lab309-03.png)

5.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Portale di Azure](images/AzureLabs-Lab309-04.png)

7.  Fare clic su notifiche per esplorare la nuova istanza del servizio.

    ![Portale di Azure](images/AzureLabs-Lab309-05.png)

8.  Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Si verrà indirizzati alla nuova *servizio di Application Insights* istanza.

    ![Portale di Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Tenere aperta questa pagina web e facile accesso, verrà tornare qui frequenza con cui visualizzare i dati raccolti.

    > [!IMPORTANT]
    > Per implementare Application Insights, è necessario usare valori specifici di tre (3): **Chiave di strumentazione**, **ID applicazione**, e **chiave API**. Di seguito si vedrà come recuperare questi valori dal servizio. Assicurarsi di annotare questi valori in uno spazio vuoto *Notepad* pagina, perché verrà usato presto nel codice.

9.  Per trovare il **chiave di strumentazione**, sarà necessario scorrere verso il basso l'elenco di funzioni del servizio e fare clic su **proprietà**, verrà visualizzate nella scheda visualizzata il **chiave del servizio**.

    ![Portale di Azure](images/AzureLabs-Lab309-07.png)

10. Un po' di seguito **delle proprietà**, si noterà **l'accesso all'API**, che è necessario fare clic su. Il pannello a destra fornirà il **ID applicazione** dell'app.

    ![Portale di Azure](images/AzureLabs-Lab309-08.png)

11. Con il **ID applicazione** ancora aperto, fare clic su pannello **Crea chiave API**, che apre il *Crea chiave API* pannello.

    ![Portale di Azure](images/AzureLabs-Lab309-09.png)

12. Entro l'ora di apertura *Crea chiave API* panel, digitare una descrizione, e **selezionare le tre caselle**.

13. Fare clic su **Genera chiave**. I **chiave API** verranno creati e visualizzati. 

    ![Portale di Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Questa è l'unica volta le **chiave del servizio** verranno visualizzati, pertanto è necessario verificare ora eseguire una copia di esso.

## <a name="chapter-2---set-up-the-unity-project"></a>Capitolo 2 - configurare il progetto Unity

Di seguito è una tipica configurato per lo sviluppo con la realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **New**.

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-11.png)

2.  A questo punto si dovrà fornire un nome di progetto Unity, inserire **MR\_Azure\_Application\_Insights**. Assicurarsi che il *modello* è impostata su **3D**. Impostare il *posizione* a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-12.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **modifica \> Preferences** e quindi dalla nuova finestra, passare al **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-13.png)

4.  Passare quindi ad **File \> Build Settings** e passare alla piattaforma di **Universal Windows Platform**, facendo clic sui **commutatore piattaforma** pulsante.

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-14.png)

5.  Passare a **File \> Build Settings** e assicurarsi che:

    1.  **Dispositivo di destinazione** è impostata su **qualsiasi dispositivo**

        > Per il Microsoft HoloLens, impostare **dispositivo di destinazione** al *HoloLens*.

    2.  **Tipo di compilazione** è impostata su **D3D**

    3.  **SDK** è impostata su **installata più recente**

    4.  **Compilare ed eseguire** è impostata su **computer locale**

    5.  Salvare la scena e aggiungerlo alla compilazione.

        1.  Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-15.png)

        2. Creare una nuova cartella per questo e qualsiasi futura scena, quindi scegliere il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-16.png)

        3. Aprire appena creato **scene** cartella e quindi la *nome File:* campo di testo, digitare **ApplicationInsightsScene**, quindi fare clic su **salvare**.

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-17.png)

6.  Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.

7.  Nel **Build Settings** finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il **Inspector** si trova.

    ![Configurare il progetto Unity](images/AzureLabs-Lab309-18.png)

8. In questo pannello, alcune impostazioni devono essere verificati:

    1.  Nel **altre impostazioni** scheda:

        1.  **Scripting** **versione Runtime** deve essere **Experimental (.NET 4.6 equivalente)** , che attiverà una necessità di riavviare l'Editor.

        2.  **Back-end di scripting** deve essere **.NET**

        3.  **Livello di compatibilità delle API** deve essere **.NET 4.6**

        ![Configurare il progetto Unity](images/AzureLabs-Lab309-19.png)

    2.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        - **InternetClient**     

            ![Configurare il progetto Unity](images/AzureLabs-Lab309-20.png)

    3.  Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **le impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **realtà mista di Windows SDK** viene aggiunto.

        ![Configurare il progetto Unity](images/AzureLabs-Lab309-21.png)

9.  Nuovamente in **Build Settings**, **Unity C# progetti** non è più è disattivata; selezionare la casella di controllo accanto a questo.

10.  Chiudere la finestra Impostazioni di compilazione.

11.  Salvare la scena e il progetto (**FILE** > **SAVE SCENE /file** > **Salva progetto**).


## <a name="chapter-3---import-the-unity-package"></a>Capitolo 3 - Importa pacchetto Unity

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componenti di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [MR-Azure-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importarlo nel progetto come un [ **Pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html). Questa conterrà anche la DLL del capitolo successivo. Al termine dell'importazione, sono la prosecuzione [ **capitolo 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Per usare Application Insights in Unity, è necessario importare il file DLL, con la DLL Newtonsoft. È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.

Per importare Application Insights in un progetto, assicurarsi di avere [scaricato il '.unitypackage', che contiene i plug-in](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). Quindi, eseguire le operazioni seguenti:

1.  Aggiungere il **.unitypackage** a Unity tramite il **asset \> Importa pacchetto \> pacchetto personalizzato** l'opzione di menu.

2.  Nel **Importa pacchetto Unity** scatola viene, assicurarsi che tutto ciò che in (e tra cui) **plug-in** sia selezionata.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-22.png)

3.  Scegliere il **importazione** pulsante, per aggiungere elementi al progetto.

4.  Passare al **Insights** cartella sotto **Plugins** nel progetto consente di visualizzare e selezionare il plug-in seguenti *solo*:

    -   Microsoft.ApplicationInsights

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-23.png)

5.  Con questo *plug-in* selezionato, assicurarsi che **Any Platform** viene **deselezionata**, quindi verificare che **WSAPlayer** anche  **unchecked**, quindi fare clic su **applica**. Questa operazione consiste nel verificare che i file siano configurati correttamente.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Contrassegnare i plug-in simile al seguente, li configura per essere usato solo nell'Editor di Unity. Esistono un diverso set di DLL nella cartella WSA che verrà usato dopo che il progetto viene esportato da Unity.

6.  Successivamente, è necessario aprire la **WSA** cartella, all'interno di **Insights** cartella. Si noterà una copia dello stesso file che appena configurato. Selezionare questo file e quindi nella finestra di ispezione, assicurarsi che **piattaforma Any** viene **deselezionata**, quindi verificare che **solo** **WSAPlayer** è **controllato**. Fare clic su **Applica**.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25.png)

7. Ora devi seguire **i passaggi 4-6**, ma per il *Newtonsoft* plug-in invece. Vedere la seguente schermata per la quale il risultato deve essere simile.

    ![Importare il pacchetto Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Capitolo 4 - configurare fotocamera e all'utente di controlli

In questo capitolo si configurerà il la fotocamera e i controlli per consentire all'utente di visualizzare e spostarsi nella scena.

1.  Fare clic in un'area vuota nel Pannello di gerarchia, quindi su **Create** > **vuoto**.

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-26.png)

2.  Rinominare il nuovo GameObject vuoto al **fotocamera padre**.

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-27.png)

3.  Fare clic in un'area vuota nel Pannello di gerarchia, quindi su **oggetto 3D**, quindi su **sfera**.

4.  Rinominare la sfera **a destra**.

5.  Impostare il **trasformare Scale** della mano destra per **0.1, 0.1, 0.1**

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-28.png)

6.  Rimuovere il **sfera Collider** l'icona della mano destra, fare clic sul componente il **a forma di ingranaggio** nel *Collider sfera* componente e quindi **Rimuovi componente** .

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-29.png)

7.  Trascinare la gerarchia pannello il **Main Camera** e il **a destra** gli oggetti il **fotocamera padre** oggetto.

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-30.png)

8.  Impostare il **posizione trasformare** di entrambi il **Main Camera** e il **a destra** oggetto **0, 0, 0**.

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-31.png)

    ![Configurare i controlli utente e la fotocamera](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Capitolo 5: configurare gli oggetti nella scena Unity

Ora si creerà alcune forme di base per la scena, con cui l'utente può interagire.

1.  Pulsante destro del mouse in un'area vuota nel *Pannello di gerarchia*, quindi nella **oggetto 3D**, quindi selezionare **piano**.

2.  Impostare il piano **trasformare posizione** al **0, -1, 0**.

3.  Impostare il piano **trasformare Scale** al **5, 1, 5**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-33.png)

4.  Creare un materiale base da usare con il **piano** dell'oggetto, in modo che le altre forme sono più facili da visualizzare. Passare al *pannello progetto*, destro del mouse e quindi **crea**, quindi su **cartella**, per creare una nuova cartella. Denominarlo **materiali**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-34.png) ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-35.png)

5.  Aprire il **materiali** cartella, quindi viene scelta, fare clic su **Create**, quindi **materiale**, per creare un nuovo materiale. Denominarlo **blu**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-36.png) ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-37.png)

6.  Con la nuova **blu** materiale selezionata, cercare nel *Inspector*e fare clic sulla finestra rettangolare insieme **Albedo**. Selezionare un colore blu (un'immagine seguente è **colore esadecimale: \#3592FFFF**). Dopo aver selezionato, fare clic sul pulsante Chiudi.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-38.png)

7.  Trascinare di nuovo materiale dal **materiali** cartella, nel appena creato **piano**, all'interno della scena (o rilasciarlo sul **piano** all'interno dell'oggetto di  *Gerarchia*).

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-39.png)

8.  Pulsante destro del mouse in un'area vuota nel *Pannello di gerarchia*, quindi nella **oggetto 3D, Capsule**.

    -  Con il **Capsule** selezionato, modificare relativo **trasformare** *posizione* da: **-10, 0 e 1**.

9.  Pulsante destro del mouse in un'area vuota nel *Pannello di gerarchia*, quindi nella **oggetto 3D, il cubo**.

    -  Con il **cubo** selezionato, modificare relativo **trasformare** *posizione* per: **0, 0, 10**.

10. Pulsante destro del mouse in un'area vuota nel *Pannello di gerarchia*, quindi nella **oggetto 3D, sfera**.

    -  Con il **sfera** selezionato, modificare relativo **trasformare** *posizione* per: **10, 0, 0**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Questi *posizione* i valori sono *suggerimenti*. Si è liberi di impostare le posizioni degli oggetti per qualsiasi elemento desiderato, ma è più semplice per l'utente dell'applicazione se le distanze di oggetti non troppo lontano dalla fotocamera.

11. Quando l'applicazione è in esecuzione, deve essere in grado di identificare gli oggetti all'interno della scena, per ottenere questo risultato, devono essere contrassegnati. Selezionare uno degli oggetti e nel *Inspector* del pannello, fare clic su **aggiungere Tag...** , che verrà scambiata il *Inspector* con il **tag & tutti i livelli di** pannello.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. Scegliere il **+ (segno più)** dei simboli, quindi digitare il nome del tag come **ObjectInScene**.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Se si usa un nome diverso per il tag, sarà necessario assicurarsi che questa modifica viene apportata anche il *DataFromAnalytics*, *ObjectTrigger*, e *estasiati*, gli script in un secondo momento, in modo che i gli oggetti vengono trovati e rilevati, all'interno della scena.

13. Con il tag creato, è necessario ora applicarlo a tutte e tre gli oggetti. Dal *gerarchia*, tenere premuto il **MAIUSC** chiave, quindi fare clic il **Capsule**, **cubo**, e **sfera**, gli oggetti, quindi nella *Inspector*, fare clic sul menu a discesa accanto **Tag**, quindi fare clic sui *ObjectInScene* tag creato.

    ![Configurare gli oggetti nella scena Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Capitolo 6: creare la classe ApplicationInsightsTracker

È il primo script da creare **ApplicationInsightsTracker**, che è responsabile per:

1.  Creazione di eventi in base alle interazioni dell'utente per inviare ad Azure Application Insights.

2. Creazione di nomi di eventi appropriati, a seconda di interazione dell'utente.

3. Invio di eventi all'istanza del servizio Application Insights.

Per creare questa classe:

1.  Fare doppio clic nella *Pannello di progetto*, quindi **creare** > **cartella**. Denominare la cartella **script**.

    ![Creare la classe ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Creare la classe ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  Con il **script** cartella creata, fare doppio clic sopra per avviarlo. Quindi, all'interno di tale cartella, pulsante destro del mouse, **Create**  >   **C# Script**. Denominare lo script **ApplicationInsightsTracker**.

3.  Fare doppio clic su nuova **ApplicationInsightsTracker** script per aprirlo con **Visual Studio**.

4.  Aggiornare gli spazi dei nomi nella parte superiore dello script sia come indicato di seguito:

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
    > Impostare il **instrumentationKey, applicationId e API_Key** i valori in modo appropriato, usando la *le chiavi del servizio* dal portale di Azure come indicato nella [capitolo 1](#chapter-1---the-azure-portal), passaggio 9 e versioni successive.

6.  Quindi aggiungere il **Start ()** e **Awake()** metodi, che verranno chiamati quando si inizializza la classe:

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

7.  Aggiungere i metodi responsabili per l'invio di eventi e metriche registrate dall'applicazione:

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

8.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-7---create-the-gaze-script"></a>Capitolo 7 - creare uno script di sguardo

Lo script successivo da creare è il **estasiati** script. Questo script è responsabile della creazione di un *Raycast* che sarà proiettato in avanti dalle *Main Camera*, per rilevare l'oggetto sta guardando l'utente. In questo caso, il *Raycast* sarà necessario identificare se l'utente è osservando un oggetto con il **ObjectInScene** tag e quindi contare quanto tempo l'utente *gazes* in quell'oggetto.

1.  Fare doppio clic sulla **script** cartella per aprirla.

2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**. Denominare lo script **estasiati**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Sostituire il codice esistente con il codice seguente:

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

5.  Il codice per il **Awake()** e **Start ()** metodi deve ora essere aggiunto.

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

6.  All'interno di **estasiati** classe, aggiungere il codice seguente nel **Update ()** metodo al progetto un *Raycast* e rilevare il calo di destinazione:

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

7.  Aggiungere il **ResetFocusedObject()** metodo, per inviare dati a **Application Insights** quando l'utente ha esaminato da un oggetto.

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

8.  È stata completata la **estasiati** script. Salvare le modifiche nel *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Capitolo 8 - creare la classe ObjectTrigger

Lo script successivo, è necessario creare sia **ObjectTrigger**, che è responsabile per:

- Aggiunta di componenti necessari per la collisione alla fotocamera principale.
- Rilevare se la fotocamera si avvicina un oggetto contrassegnato come **ObjectInScene**.

Per creare lo script:

1.  Fare doppio clic sulla **script** cartella per aprirla.

2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**. Denominare lo script **ObjectTrigger**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio. Sostituire il codice esistente con il codice seguente:

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

4.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Capitolo 9 - creare la classe DataFromAnalytics

È ora necessario creare il **DataFromAnalytics** script, che è responsabile per:

- Durante il recupero dei dati di analitica intorno al quale oggetto è stato affrontato dalla fotocamera più.
- Usando il *le chiavi del servizio*, che consentono la comunicazione con l'istanza del servizio di Azure Application Insights.
- Ordinare gli oggetti nella scena, in base ai quali ha il maggior numero di eventi.
- Modifica il colore del materiale, dell'oggetto più approached, a *verde*.

Per creare lo script:

1.  Fare doppio clic sulla **script** cartella per aprirla.

2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**. Denominare lo script **DataFromAnalytics**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserisci gli spazi dei nomi seguenti:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Nello script, inserire gli elementi seguenti:

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

6.  All'interno del **DataFromAnalytics** classi, pulsante destro del mouse dopo il **Start ()** metodo, aggiungere il seguente metodo chiamato **FetchAnalytics()** . Questo metodo è responsabile della compilazione dell'elenco di coppie chiave-valore, con un *GameObject* e un numero di conteggio di eventi di segnaposto. Vengono quindi inizializzate le **GetWebRequest()** coroutine. La struttura della query della chiamata a *Application Insights* sono disponibili all'interno di questo metodo, inoltre, come le *URL della Query* endpoint.

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

7.  Sotto il **FetchAnalytics()** metodo, aggiungere un metodo denominato **GetWebRequest()** , che restituisce un' *IEnumerator*. Questo metodo è responsabile che richiede il numero di volte in cui un evento, corrispondente a uno specifico *GameObject*, è stato chiamato all'interno *Application Insights*. Quando tutte le query inviate hanno restituito, il **DetermineWinner()** viene chiamato il metodo.

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

8.  Il metodo successivo viene **DetermineWinner()** , che consente di ordinare l'elenco dei *GameObject* e *Int* coppie, in base al maggior numero di eventi. Viene quindi modificato il colore del materiale di tale *GameObject* al *verde* (come commenti e suggerimenti per tale necessità il numero più alto). Ciò consente di visualizzare un messaggio con i risultati di analitica.

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

9.  Aggiungere la struttura della classe che verrà usata per deserializzare l'oggetto JSON, ricevuto dal *Application Insights*. Aggiungere queste classi nella parte inferiore dei **DataFromAnalytics** file di classe **di fuori** della definizione di classe.

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

10. Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-10---create-the-movement-class"></a>Capitolo 10 - creare la classe di movimento

Il **movimento** script è lo script successivo sarà necessario creare. È responsabile per:

- Spostamento della videocamera Main in base alla direzione della fotocamera esegue la ricerca nei confronti.
- Aggiunta di tutti gli altri script per gli oggetti di scena.

Per creare lo script:

1.  Fare doppio clic sulla **script** cartella per aprirla.

2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**. Denominare lo script **movimento**.

3.  Fare doppio clic su script per aprirlo con *Visual Studio*.

4.  Sostituire il codice esistente con il codice seguente:

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

5.  All'interno di **lo spostamento dei** (classe), *seguito* vuoto **Update ()** metodo, inserire i metodi seguenti che consentono di usare il controller manualmente per spostare in uno spazio virtuale:

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

6.  Aggiungere infine la chiamata di metodo all'interno di **Update ()** (metodo).

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Capitolo 11 - configurazione i riferimenti di script

In questo capitolo è necessario inserire il **lo spostamento dei** nello script il **fotocamera padre** e impostare le destinazioni di riferimento. Lo script gestirà quindi l'inserimento altri script in cui devono essere.

1.  Dal **gli script** cartella nel *pannello progetto*, trascinare il **lo spostamento dei** generare uno script per il **fotocamera padre** oggetto, che si trova nel  *Pannello gerarchia*.

    ![Impostare i riferimenti di script nella scena Unity](images/AzureLabs-Lab309-48.png)

2.  Fare clic sui **fotocamera padre**. Nel *pannello gerarchia*, trascinare il **a destra** dall'oggetto il *gerarchia pannello* alla destinazione di riferimento, **Controller**, nella *Pannello di controllo*. Impostare il **utente velocità** al **5**, come illustrato nell'immagine seguente.

    ![Impostare i riferimenti di script nella scena Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Capitolo 12 - compilare il progetto Unity

Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.

1.  Passare a **impostazioni di compilazione**, (**File** > **impostazioni di compilazione**).

2.  Dal **Build Settings** finestra, fare clic su **compilazione**.

    ![Compilare il progetto Unity alla soluzione di piattaforma UWP](images/AzureLabs-Lab309-50.png)

3.  Oggetto **Esplora File** finestra will popup, cui è possibile specificare un percorso per la compilazione. Creare una nuova cartella (facendo **nuova cartella** nell'angolo superiore sinistro) e denominarla **COMPILA**.

    ![Compilare il progetto Unity alla soluzione di piattaforma UWP](images/AzureLabs-Lab309-51.png)

    1.  Aprire il nuovo **si basa** cartella e creare un'altra cartella (utilizzando **nuova cartella** ancora una volta) e denominarlo **MR\_Azure\_applicazione\_ Insights**.

        ![Compilare il progetto Unity alla soluzione di piattaforma UWP](images/AzureLabs-Lab309-52.png)

    2.  Con il **MR\_Azure\_Application\_Insights** cartella selezionata, fare clic su **Seleziona cartella**. Il progetto avrà un minuto alla compilazione.

4.  Seguendo *compilare*, **Esplora File** apparirà mostrano la posizione del nuovo progetto.

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>Capitolo 13 - distribuire app MR_Azure_Application_Insights in un computer

Per distribuire il **MR\_Azure\_Application\_Insights** app nel computer locale:

1.  Aprire il file della soluzione delle **MR\_Azure\_Application\_Insights** in app **Visual Studio**.

2.  Nel **piattaforma soluzione**, selezionare **x86, computer locale**.

3.  Nel **configurazione della soluzione** selezionate **Debug**.

    ![Compilare il progetto Unity alla soluzione di piattaforma UWP](images/AzureLabs-Lab309-53.png)

4.  Passare a **dal menu Compila** e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione nel computer.

5.  L'app deve ora visualizzato nell'elenco delle App installate, pronta per essere avviata.

6. Avviare l'applicazione di realtà mista.

7. Spostare la scena, per raggiungere gli oggetti e analizzando, quando la *servizio di Azure Insights* abbia raccolto abbastanza dati evento, imposterà l'oggetto che è stato affrontato al meglio su verde.

> [!IMPORTANT] 
> Mentre il tempo medio di attesa per il *metriche ed eventi* a essere raccolte dal servizio richiede circa 15 minuti, in alcuni casi potrebbe richiedere fino a 1 ora.

## <a name="chapter-14---the-application-insights-service-portal"></a>Capitolo 14 - portale di Application Insights Service

Dopo che in roaming intorno scena e gazed in diversi oggetti è possibile visualizzare i dati raccolti nel *servizio di Application Insights* portale.

1.  Tornare al portale del servizio Application Insights.

2.  Fare clic su *Esplora metriche*.

    ![Esaminando i dati raccolti](images/AzureLabs-Lab309-54.png)

3.  Verrà aperto in una scheda che contiene il grafico che rappresenta il *metriche ed eventi* relative all'applicazione. Come indicato in precedenza, potrebbe richiedere tempo (fino a 1 ora) per i dati da visualizzare nel grafico

    ![Esaminando i dati raccolti](images/AzureLabs-Lab309-55.png)

4.  Fare clic sul *sulla barra degli eventi* nel *totale di eventi* dalla versione dell'applicazione, per visualizzare una suddivisione dettagliata degli eventi con i relativi nomi.

    ![Esaminando i dati raccolti](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Il termine l'applicazione di servizio di Application Insights

Complimenti, è stata compilata un'app per realtà mista che sfrutta il servizio Application Insights per monitorare l'attività dell'utente all'interno dell'app.

![risultato del corso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

**Esercizio 1**

Provare a generazione, anziché creare manualmente gli oggetti ObjectInScene e impostare le coordinate sul piano all'interno degli script. In questo modo, si può chiedere Azure quali l'oggetto più diffuso era (sia dai risultati sguardo o prossimità) e generare una *extra* uno di questi oggetti.

**Esercizio 2**

Per ordinare i risultati di Application Insights ora, in modo da ottenere i dati più rilevanti e implementare tali dati sensibili di tempo nell'applicazione.

