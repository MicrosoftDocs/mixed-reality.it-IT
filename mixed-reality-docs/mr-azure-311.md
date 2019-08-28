---
title: MR e Azure 311-Microsoft Graph
description: Completare questo corso per apprendere come sfruttare Microsoft Graph e connettersi ai dati che determinano la produttività, all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, Microsoft Graph, hololens, immersive, VR
ms.openlocfilehash: 775971c4e4289d2dc963dfa2bf033192d9f3489e
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047199"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

# <a name="mr-and-azure-311---microsoft-graph"></a>MR e Azure 311-Microsoft Graph

In questo corso si apprenderà come usare *Microsoft Graph* per accedere al account Microsoft usando l'autenticazione protetta all'interno di un'applicazione di realtà mista. Sarà quindi possibile recuperare e visualizzare le riunioni pianificate nell'interfaccia dell'applicazione.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* è un set di API progettate per consentire l'accesso a molti dei servizi Microsoft. Microsoft descrive Microsoft Graph come una matrice di risorse connesse da relazioni, il che significa che consente a un'applicazione di accedere a tutti i tipi di dati utente connessi. Per ulteriori informazioni, visitare la [pagina Microsoft Graph](https://developer.microsoft.com/graph).

Lo sviluppo includerà la creazione di un'app in cui l'utente verrà istruito a osservare e quindi toccare una sfera, che chiederà all'utente di accedere in modo sicuro a una account Microsoft. Una volta effettuato l'accesso al proprio account, l'utente sarà in grado di visualizzare un elenco di riunioni pianificate per la giornata.

Dopo aver completato questo corso, si disporrà di un'applicazione HoloLens in realtà mista, che sarà in grado di eseguire le operazioni seguenti:

1.  Usando il gesto Tap, toccare un oggetto per richiedere all'utente di accedere a un account Microsoft (uscendo dall'app per accedere e quindi nuovamente nell'app).
2.  Visualizza un elenco di riunioni pianificate per il giorno. 

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con C#Unity e. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018). È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.

Per questo corso è consigliabile usare i componenti hardware e software seguenti:

- Un computer di sviluppo
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità di sviluppo abilitata](install-the-tools.md#installation-checklist)
- [Windows 10 SDK più recente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- [Microsoft HoloLens](hololens-hardware-details.md) con la modalità di sviluppo abilitata
- Accesso a Internet per il programma di installazione di Azure e Microsoft Graph il recupero dei dati
- Un **account Microsoft** valido (personale o aziendale/dell'Istituto di istruzione)
- Alcune riunioni pianificate per il giorno corrente, usando lo stesso account Microsoft

### <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente. 

Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Capitolo 1-creare l'app nel portale di registrazione delle applicazioni

Per iniziare, sarà necessario creare e registrare l'applicazione nel **portale di registrazione dell'applicazione**.

In questo capitolo si troverà anche la chiave del servizio che consentirà di effettuare chiamate a *Microsoft Graph* per accedere al contenuto dell'account.

1.  Passare al [portale di registrazione delle applicazioni Microsoft](https://apps.dev.microsoft.com) e accedere con l'account Microsoft. Dopo aver eseguito l'accesso, si verrà reindirizzati al **portale di registrazione delle applicazioni**.

2.  Nella sezione **applicazioni personali** fare clic sul pulsante **Aggiungi un'app**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > Il **portale di registrazione delle applicazioni** può avere un aspetto diverso, a seconda che in precedenza sia stato usato *Microsoft Graph*. Le schermate seguenti visualizzano queste versioni diverse.

3.  Aggiungere un nome per l'applicazione e fare clic su **Crea**.

    ![](images/AzureLabs-Lab311-03.png)

4.  Una volta creata l'applicazione, si verrà reindirizzati alla pagina principale dell'applicazione. Copiare l' **ID applicazione** e assicurarsi di prendere nota di questo valore in un punto sicuro, che verrà usato a breve nel codice.

    ![](images/AzureLabs-Lab311-04.png)

5.  Nella sezione **piattaforme** verificare che sia visualizzata l' **applicazione nativa** . Se *non* si fa clic su **Aggiungi piattaforma** e selezionare **applicazione nativa**.

    ![](images/AzureLabs-Lab311-05.png)

6.  Scorrere verso il basso nella stessa pagina e nella sezione chiamata **autorizzazioni Microsoft Graph** sarà necessario aggiungere altre autorizzazioni per l'applicazione. Fare clic su **Aggiungi** accanto a **autorizzazioni delegate**.

    ![](images/AzureLabs-Lab311-06.png)

7.  Poiché si desidera che l'applicazione acceda al calendario dell'utente, selezionare la casella **calendari. Read** e fare clic su **OK**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Scorrere fino alla fine e fare clic sul pulsante **Salva** .

    ![](images/AzureLabs-Lab311-08.png)

9.  Il salvataggio verrà confermato ed è possibile disconnettersi dal **portale di registrazione delle applicazioni**.

## <a name="chapter-2---set-up-the-unity-project"></a>Capitolo 2: configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire *Unity* e fare clic su **New**.

    ![](images/AzureLabs-Lab311-09.png)

2.  È necessario specificare un nome di progetto Unity. Inserire **MSGraphMR**. Verificare che il modello di progetto sia impostato su **3D**. Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![](images/AzureLabs-Lab311-10.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **modifica** > **Preferenze** e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![](images/AzureLabs-Lab311-11.png)

4.  Passare a**impostazioni di compilazione** **file** > e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.

    ![](images/AzureLabs-Lab311-12.png)

5.  Sempre nelle**impostazioni di compilazione** **file** > , verificare che:

    1. Il **dispositivo di destinazione** è impostato su **HoloLens**
    2. Il **tipo di compilazione** è impostato su **D3D**
    3. **SDK** è impostato sull' **ultima versione installata**
    4. La **versione di Visual Studio** è impostata su **installazione più recente**
    5. **Compilazione ed esecuzione** è impostato su **computer locale**
    6. Salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.

            ![](images/AzureLabs-Lab311-13.png)

        2. Creare una nuova cartella per questo e qualsiasi scena futura. Selezionare il pulsante **nuova cartella** per creare una nuova cartella, denominarla **Scenes**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **MR_ComputerVisionScene**e quindi fare clic su **Salva**.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Tenere presente che è necessario salvare le scene Unity all' interno della cartella assets, in quanto devono essere associate al progetto Unity. La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.

    7.  Le impostazioni rimanenti, nelle *impostazioni di compilazione*, devono essere lasciate come predefinite per il momento.

6.  Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* . 

    ![](images/AzureLabs-Lab311-16.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **altre impostazioni** :

        1.  Creazione di **script** La **versione di runtime** deve essere **sperimentale** (equivalente a .NET 4,6), che attiverà la necessità di riavviare l'editor.

        2. Il **back-end** di scripting deve essere **.NET**

        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Nella parte inferiore del pannello, in **Impostazioni XR** (disponibili sotto **le impostazioni di pubblicazione**), controllare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![](images/AzureLabs-Lab311-19.png)

8.  Nelle *impostazioni di compilazione*, *i C# progetti Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo.

9.  Chiudere la finestra *impostazioni di compilazione* .

10.  Salva la scena e il progetto (**progetto**Salva**file** >  **/Salva file** > ).

## <a name="chapter-3---import-libraries-in-unity"></a>Capitolo 3-importare le librerie in Unity

> [!IMPORTANT]
> Se si vuole ignorare il componente di *configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricare questo [Azure-Mr-311. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare dal [capitolo 5 ](#chapter-5---create-meetingsui-class).

Per usare *Microsoft Graph* in Unity, è necessario usare la dll **Microsoft. Identity. client** . È possibile usare l'SDK Microsoft Graph, tuttavia, richiede l'aggiunta di un pacchetto NuGet dopo la compilazione del progetto Unity (ovvero la modifica del progetto post-compilazione). È considerato più semplice importare le DLL necessarie direttamente in Unity.

> [!NOTE]
> Attualmente esiste un problema noto in Unity che richiede che i plug-in vengano riconfigurati dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare *Microsoft Graph* nel progetto, [scaricare il file MSGraph_LabPlugins. zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Questo pacchetto è stato creato con le versioni delle librerie testate.

Per altre informazioni su come aggiungere DLL personalizzate al progetto Unity, vedere il [collegamento](https://docs.unity3d.com/Manual/UsingDLL.html)seguente.

Per importare il pacchetto:

1.  Aggiungere il pacchetto Unity a Unity usando l'opzione di menu **Asset** > **Import Package** > **Custom Package** . Selezionare il pacchetto appena scaricato.

2.  Nella casella **Importa pacchetto Unity** visualizzata verificare che siano selezionati tutti gli elementi in (e inclusi) **plug** -in.

    ![](images/AzureLabs-Lab311-20.png)

3.  Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.

4.  Passare alla cartella **MSGraph** in **plugins** nel *Pannello Project* e selezionare il plug-in denominato **Microsoft. Identity. client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  Con il *plug* -in selezionato, assicurarsi che **qualsiasi piattaforma** sia deselezionata, quindi assicurarsi che **WSAPlayer** sia deselezionata, quindi fare clic su **applica**. Questa operazione è sufficiente per verificare che i file siano configurati correttamente.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Contrassegnando questi plug-in, questi vengono configurati per essere usati solo nell'editor di Unity. Nella cartella WSA è presente un set di dll diverso che verrà usato dopo che il progetto viene esportato da Unity come applicazione Windows universale.

6.  Successivamente, è necessario aprire la cartella **WSA** , all'interno della cartella **MSGraph** . Viene visualizzata una copia dello stesso file appena configurato. Selezionare il file e quindi nell'Ispettore:

    -   Verificare che **qualsiasi piattaforma** siadeselezionata e che sia **selezionato** **solo** **WSAPlayer** .

    -   Verificare che l' **SDK** sia impostato su **UWP**e che **lo scripting back-end** sia impostato su **dot net**

    -   Assicurarsi che l'opzione **non elaborare** sia **selezionata**.

        ![](images/AzureLabs-Lab311-23.png)

7.  Fare clic su **Applica**.

## <a name="chapter-4---camera-setup"></a>Capitolo 4-configurazione della fotocamera

Durante questo capitolo verrà configurata la fotocamera principale della scena:

1.  Nel *Pannello gerarchia*selezionare la **fotocamera principale**.

2.  Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel pannello di *controllo* .

    1.  L' **oggetto fotocamera** deve essere denominato **Main camera** (nota l'ortografia).

    2.  Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (si noti l'ortografia).

    3.  Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**

    4.  Imposta **Cancella flag** su **colore a tinta unita**

    5.  Imposta il **colore di sfondo** del componente della fotocamera su **nero, alfa 0** **(codice esadecimale: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  La struttura dell'oggetto finale nel *Pannello gerarchia* deve essere simile a quella illustrata nell'immagine seguente:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Capitolo 5-creare la classe MeetingsUI

Il primo script che è necessario creare è **MeetingsUI**, che è responsabile dell'hosting e del popolamento dell'interfaccia utente dell'applicazione (messaggio di benvenuto, istruzioni e dettagli delle riunioni).

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse sulla cartella **Asset** nel *pannello progetto*, quindi scegliere **Crea** > **cartella**. Denominare gli **script**della cartella.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Aprire la cartella Scripts, quindi, in tale cartella, fare clic con il pulsante destro del mouse su **Crea**  >   **C# script**. Denominare lo script **MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Fare doppio clic sul nuovo script **MeetingsUI** per aprirlo con *Visual Studio*.

4.  Inserire gli spazi dei nomi seguenti:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  All'interno della classe inserire le variabili seguenti:

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  Sostituire quindi il metodo **Start ()** e aggiungere un metodo **svegli ()** . Questi verranno chiamati quando la classe inizializza:

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  Aggiungere i metodi responsabili della creazione dell' *interfaccia utente riunioni* e popolarla con le riunioni correnti quando richiesto:

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Eliminare** il metodo **Update ()** e **salvare le modifiche** in Visual Studio prima di tornare a Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Capitolo 6: creare la classe Graph

Lo script successivo da creare è lo script **Graph** . Questo script è responsabile dell'esecuzione delle chiamate per autenticare l'utente e recuperare le riunioni pianificate per il giorno corrente dal calendario dell'utente.

Per creare questa classe:

1.  Fare doppio clic sulla cartella **Scripts** per aprirla.

2.  Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**. Denominare lo script **Graph**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserire gli spazi dei nomi seguenti:

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > Si noterà che le parti del codice in questo script sono incapsulate intorno alle [direttive di precompilazione](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), in modo da evitare problemi con le librerie durante la compilazione della soluzione di Visual Studio.

5.  Eliminare i metodi **Start ()** e **Update ()** perché non verranno usati.

6.  All'esterno della classe **Graph** inserire gli oggetti seguenti, necessari per deserializzare l'oggetto JSON che rappresenta le riunioni pianificate giornaliere:

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  All'interno della classe **Graph** aggiungere le variabili seguenti:

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > Modificare il valore **AppID** in modo che sia l' **ID app** annotato nel  **[capitolo 1](#chapter-1---create-your-app-in-the-application-registration-portal), passaggio 4**. Questo valore deve corrispondere a quello visualizzato nel **portale di registrazione delle applicazioni,** nella pagina di registrazione dell'applicazione.

8.  All'interno della classe **Graph** aggiungere i metodi **SignInAsync ()** e **AquireTokenAsync ()** che richiederanno all'utente di inserire le credenziali di accesso.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  Aggiungere i due metodi seguenti:

    1.  **BuildTodayCalendarEndpoint ()** , che compila l'URI che specifica il giorno e l'intervallo di tempo in cui vengono recuperate le riunioni pianificate.

    2.  **ListMeetingsAsync ()** , che richiede le riunioni pianificate da *Microsoft Graph*.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. A questo punto è stato completato lo script **Graph** . **Salvare le modifiche** in Visual Studio prima di tornare a Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Capitolo 7: creare lo script GazeInput

A questo punto verrà creato il **GazeInput**. Questa classe gestisce e tiene traccia dello sguardo dell'utente, usando un **Raycast** proveniente dalla **fotocamera principale**, proiettando in futuro.

Per creare lo script:

1.  Fare doppio clic sulla cartella **Scripts** per aprirla.

2.  Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**. Denominare lo script **GazeInput**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Modificare il codice degli spazi dei nomi in modo che corrisponda a quello riportato di seguito, oltre ad aggiungere il tag ' **\[System. Serializable\]** ' sopra la classe **GazeInput** , in modo che possa essere serializzato:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  All'interno della classe **GazeInput** aggiungere le variabili seguenti:

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Aggiungere il metodo **CreateCursor ()** per creare il cursore HoloLens nella scena e chiamare il metodo dal metodo **Start ()** :

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  I metodi seguenti abilitano lo sguardo Raycast e tengono traccia degli oggetti specifici.

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **Salvare le modifiche** in Visual Studio prima di tornare a Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Capitolo 8: creare la classe di interazioni

A questo punto sarà necessario creare lo script delle **interazioni** , responsabile di:

-   Gestione dell'interazione **Tap** e dello **sguardo della fotocamera**, che consente all'utente di interagire con il pulsante di accesso nella scena.

-   Creazione dell'oggetto di accesso "button" nella scena per l'interazione dell'utente con.

Per creare lo script:

1.  Fare doppio clic sulla cartella **Scripts** per aprirla.

2.  Fare clic con il pulsante destro del mouse nella cartella **script** , quindi scegliere **Crea**  >   **C# script**. Denominare le **interazioni**dello script.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserire gli spazi dei nomi seguenti:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Modificare l'ereditarietà della classe di **interazione** da *monobehavior* a **GazeInput**.

    ~~Interazioni tra classi pubbliche: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  All'interno della classe di **interazione** inserire la variabile seguente:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Sostituire il metodo **Start** ; Si noti che si tratta di un metodo di override, che chiama il metodo della classe di sguardi "base". **Start ()** verrà chiamato quando la classe viene inizializzata, registrandosi per il riconoscimento dell'input e creando il *pulsante* di accesso nella scena:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  Aggiungere il metodo **CreateSignInButton ()** che creerà un'istanza del *pulsante* Accedi nella scena e ne imposterà le proprietà:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  Aggiungere il metodo **GestureRecognizer_Tapped ()** che risponde per l'evento *Tap* User.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Eliminare** il metodo **Update ()** e quindi **salvare le modifiche** in Visual Studio prima di tornare a Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Capitolo 9: impostare i riferimenti agli script

In questo capitolo è necessario inserire lo script delle **interazioni** sulla **fotocamera principale**. Tale script gestirà quindi l'inserimento degli altri script in cui devono essere.

-  Dalla cartella **script** nel pannello del *progetto*trascinare le **interazioni** degli script nell'oggetto della **fotocamera principale** , come illustrato di seguito.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Capitolo 10-configurazione del tag

Il codice che gestisce lo sguardo utilizzerà il tag **SignInButton** per identificare l'oggetto con cui l'utente interagirà per accedere *Microsoft Graph*.

Per creare il tag:

1.  Nell'editor di Unity fare clic sulla **fotocamera principale** nel *Pannello gerarchia*.

2.  Nel *Pannello di controllo* fare clic sul *tag* MainCamera per aprire un elenco a discesa. Fare clic su **Aggiungi tag...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Fare clic sul **+** pulsante.

    ![](images/AzureLabs-Lab311-31.png)

4.  Scrivere il nome del tag come **SignInButton** e fare clic su Save.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Capitolo 11: compilare il progetto Unity in UWP

Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.

1.  Passare a *impostazioni di compilazione* (**File*>*Impostazioni di compilazione**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Se non è già stato fatto, è necessario che i **progetti Unity C\#** .

3.  Fai clic su **Compila**. Unity avvierà una finestra di **Esplora file** , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella adesso e denominarla **app**. Quindi, con la cartella dell' **app** selezionata, fare clic su **Seleziona cartella**.

4.  Unity inizierà a compilare il progetto nella cartella dell' **app** .

5.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).

## <a name="chapter-12---deploy-to-hololens"></a>Capitolo 12: eseguire la distribuzione in HoloLens

Per eseguire la distribuzione in HoloLens:

1.  È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore.** A tale scopo, effettuare le seguenti operazioni:

    1.  Quando si indossa il HoloLens, aprire le **Impostazioni**.

    2.  Passa a **rete &**  > **Opzioni avanzate** **Wi-Fi** > Internet

    3.  Prendere nota dell'indirizzo **IPv4** .

    4.  Tornare quindi a Settings ( **Impostazioni**) e quindi **aggiornare & Security** > **per gli sviluppatori**

    5.  Impostare la **modalità di sviluppo su**.

2.  Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.

3.  Nella **configurazione della soluzione** selezionare **debug**.

4.  Nella **piattaforma soluzione**selezionare **x86, computer remoto**. Verrà richiesto di inserire l' **indirizzo IP** di un dispositivo remoto (HoloLens, in questo caso, annotato).

    ![](images/AzureLabs-Lab311-34.png)

5.  Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per sideload l'applicazione in HoloLens.

6.  L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.

## <a name="your-microsoft-graph-hololens-application"></a>Applicazione Microsoft Graph HoloLens

Congratulazioni, è stata creata un'app per realtà mista che sfrutta i Microsoft Graph per leggere e visualizzare i dati del calendario degli utenti.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Usare Microsoft Graph per visualizzare altre informazioni sull'utente

-   Indirizzo di posta elettronica utente/numero di telefono/profilo

### <a name="exercise-1"></a>Esercizio 1

Implementare il controllo vocale per spostarsi nell'interfaccia utente di Microsoft Graph.
