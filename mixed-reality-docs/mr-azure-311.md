---
title: MR e 311 - Microsoft Graph di Azure
description: Completa questo corso per imparare a usare Microsoft Graph e connettersi ai dati che contribuiscono alla produttività, all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, graph microsoft, hololens, coinvolgenti, vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694521"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

# <a name="mr-and-azure-311---microsoft-graph"></a>MR e 311 - Microsoft Graph di Azure

In questo corso, si apprenderà come usare *Microsoft Graph* per accedere all'account Microsoft usando l'autenticazione sicura all'interno di un'applicazione di realtà mista. È quindi e visualizzerà le riunioni pianificate nell'interfaccia dell'applicazione.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* è un set di API progettate per consentire l'accesso a molti dei servizi Microsoft. Microsoft descrive Microsoft Graph come una matrice di risorse connesse tramite relazioni, vale a dire che consente a un'applicazione accedere a tutti i tipi di dati dell'utente connesso. Per altre informazioni, visitare il [pagina di Microsoft Graph](https://developer.microsoft.com/graph).

Lo sviluppo include la creazione di un'app in cui l'utente verrà indicato per fissare e quindi toccare una sfera, verrà richiesto all'utente di accedere in modo sicuro a un account Microsoft. Una volta effettuato l'accesso al proprio account, l'utente sarà in grado di visualizzare un elenco delle riunioni pianificate per la giornata.

Dopo aver completato il corso, si avrà una realtà mista applicazione HoloLens, che sarà in grado di eseguire le operazioni seguenti:

1.  Uso di movimenti di tocco, toccare su un oggetto che richiederà all'utente di accedere a un Account Microsoft (lo spostamento all'esterno dell'app per accedere e quindi eseguire nuovamente il backup nell'app).
2.  Visualizzare un elenco delle riunioni pianificate per il giorno. 

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e 311 Azure: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Unity e C#. Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018). Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quanto elencato di seguito.

È consigliabile seguenti prodotti hardware e software per questo corso di:

- Un computer di sviluppo
- [Windows 10 Fall Creators Update (o versione successiva) con abilitata la modalità sviluppatore](install-the-tools.md#installation-checklist)
- [La versione più recente di Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Oggetto [Microsoft HoloLens](hololens-hardware-details.md) con abilitata la modalità sviluppatore
- Accesso a Internet per la configurazione di Azure e il recupero dei dati di Microsoft Graph
- Un valore valido **Account Microsoft** (personale o o dell'istituto)
- Alcune riunioni pianificate per il giorno corrente, usando lo stesso Account Microsoft

### <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
2.  Configurare e testare l'HoloLens. Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova App per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente). 

Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Capitolo 1 - creare l'app nel portale di registrazione dell'applicazione

Per iniziare, è necessario creare e registrare l'applicazione nel **portale di registrazione applicazione**.

In questo capitolo sono inoltre disponibili la chiave del servizio che ti permetterà di effettuare chiamate a *Microsoft Graph* di accedere ai contenuti di account.

1.  Passare al [portale di registrazione dell'applicazione Microsoft](https://apps.dev.microsoft.com) ed eseguire l'accesso con l'Account Microsoft. Dopo aver eseguito l'accesso, si verrà reindirizzati per il **portale di registrazione applicazione**.

2.  Nel **applicazioni personali** sezione, fare clic sul pulsante **Aggiungi un'app**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > Il **portale di registrazione dell'applicazione** può risultare diversa, a seconda se si è precedentemente utilizzato con *Microsoft Graph*. Di seguito le schermate visualizzate queste diverse versioni.

3.  Aggiungere un nome per l'applicazione e fare clic su **Create**.

    ![](images/AzureLabs-Lab311-03.png)

4.  Dopo aver creata l'applicazione, si verrà reindirizzati alla pagina principale dell'applicazione. Copia il **Id applicazione** e assicurarsi di prendere nota del valore in una posizione sicuro, verrà usato presto nel codice.

    ![](images/AzureLabs-Lab311-04.png)

5.  Nel **piattaforme** assicurarsi che **applicazione nativa** viene visualizzato. Se *non* fare clic su **Aggiungi piattaforma** e selezionare **applicazione nativa**.

    ![](images/AzureLabs-Lab311-05.png)

6.  Scorrere verso il basso nella stessa pagina e nella sezione denominata **autorizzazioni di Microsoft Graph** sarà necessario aggiungere altre autorizzazioni per l'applicazione. Fare clic su **Add** accanto a **autorizzazioni delegate**.

    ![](images/AzureLabs-Lab311-06.png)

7.  Poiché si desidera che l'applicazione per accedere al calendario dell'utente, selezionare la casella denominata **Calendars** e fare clic su **OK**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Scorrere verso il basso e scegliere il **salvare** pulsante.

    ![](images/AzureLabs-Lab311-08.png)

9.  Verrà confermata la salva, è possibile disconnettersi quindi dal **portale di registrazione applicazione**.

## <a name="chapter-2---set-up-the-unity-project"></a>Capitolo 2 - configurare il progetto Unity

Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **New**.

    ![](images/AzureLabs-Lab311-09.png)

2.  È necessario specificare un nome di progetto Unity. Insert **MSGraphMR**. Verificare che il modello di progetto è impostato su **3D**. Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![](images/AzureLabs-Lab311-10.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **Edit** > **preferenze** e quindi dalla nuova finestra, passare al **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![](images/AzureLabs-Lab311-11.png)

4.  Passare a **File** > **Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sul **commutatore piattaforma** pulsante per applicare la selezione.

    ![](images/AzureLabs-Lab311-12.png)

5.  Mentre si trovano ancora nella **File** > **Build Settings**, assicurarsi che:

    1. **Dispositivo di destinazione** è impostata su **HoloLens**
    2. **Tipo di compilazione** è impostata su **D3D**
    3. **SDK** è impostata su **installata più recente**
    4. **Versione di Visual Studio** è impostata su **installata più recente**
    5. **Compilare ed eseguire** è impostata su **computer locale**
    6. Salvare la scena e aggiungerlo alla compilazione.

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.

            ![](images/AzureLabs-Lab311-13.png)

        2. Creare una nuova cartella per questa operazione e qualsiasi futuro, la scena. Selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Aprire appena creato **scene** cartella e quindi la *nome File*: campo di testo, digitare **MR_ComputerVisionScene**, quindi fare clic su **Salva** .

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Tenere presente, è necessario salvare le scene di Unity all'interno di *asset* cartella, come devono essere associate al progetto di Unity. Creare la cartella scene (e altre simili) è un modo tipico strutturare un progetto Unity.

    7.  Le restanti impostazioni, nel *Build Settings*, deve essere lasciato come impostazione predefinita per il momento.

6.  Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova. 

    ![](images/AzureLabs-Lab311-16.png)

7. In questo pannello, alcune impostazioni devono essere verificati:

    1. Nel **altre impostazioni** scheda:

        1.  **Scripting** **versione Runtime** deve essere **sperimentale** (.NET 4.6 equivalente), che attiverà una necessità di riavviare l'Editor.

        2. **Back-end di scripting** deve essere **.NET**

        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), controllare **supportato di realtà virtuale**, assicurarsi che il **realtà mista di Windows SDK** viene aggiunto.

        ![](images/AzureLabs-Lab311-19.png)

8.  Nuovamente in *Build Settings*, *Unity C# progetti* non è più è disattivata; selezionare la casella di controllo accanto a questo.

9.  Chiudi il *Build Settings* finestra.

10.  Salvare la scena e il progetto (**FILE** > **salvare scene /file** > **Salva progetto**).

## <a name="chapter-3---import-libraries-in-unity"></a>Capitolo 3 - librerie di importazione in Unity

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [MR-Azure-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importarlo nel progetto come un [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html)e quindi sono la prosecuzione [capitolo 5](#chapter-5---create-meetingsui-class).

Per usare *Microsoft Graph* all'interno di Unity è necessario apportare utilizzare il **Microsoft.Identity.Client** DLL. È possibile usare il SDK di Microsoft Graph, tuttavia, sarà necessario l'aggiunta di un pacchetto NuGet dopo aver compilato il progetto di Unity (ovvero la post-compilazione del progetto di modifica). Viene considerato più semplice importare le librerie DLL richieste direttamente in Unity.

> [!NOTE]
> È attualmente non esiste un problema noto in Unity che richiede i plug-in per essere riconfigurato dopo l'importazione. Questi passaggi (4-7 in questa sezione) non saranno necessari dopo che è stato risolto il bug.

Per importare *Microsoft Graph* nel progetto, [scaricare il file MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Questo pacchetto è stato creato con le versioni delle librerie che sono state testate.

Se si vuole saperne di più su come aggiungere DLL personalizzata al progetto Unity [fare clic sul collegamento](https://docs.unity3d.com/Manual/UsingDLL.html).

Per importare il pacchetto:

1.  Aggiungere il pacchetto Unity per Unity usando il **Assets** > **Importa pacchetto** > **pacchetto personalizzato** l'opzione di menu. Selezionare il pacchetto che appena scaricato.

2.  Nel **Importa pacchetto Unity** scatola viene, assicurarsi che tutto ciò che in (e tra cui) **plug-in** sia selezionata.

    ![](images/AzureLabs-Lab311-20.png)

3.  Scegliere il **importazione** pulsante per aggiungere elementi al progetto.

4.  Andare alla **Microsoft Graph** cartella sotto **plug-in** nel *pannello progetto* e selezionare il plug-in denominato **Microsoft.Identity.Client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  Con il *plug-in* selezionato, assicurarsi che **Any Platform** non è selezionata, quindi verificare che **WSAPlayer** anche è deselezionata, quindi fare clic su **applica**. Si tratta semplicemente di confermare che i file siano configurati correttamente.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Contrassegnare questi plug-in Configura perché possano essere usati solo nell'Editor di Unity. Esistono un diverso set di DLL nella cartella WSA che verrà usato dopo che il progetto viene esportato da Unity come un'applicazione di Windows universale.

6.  Successivamente, è necessario aprire la **WSA** cartella, all'interno di **Microsoft Graph** cartella. Si noterà una copia dello stesso file che appena configurato. Selezionare il file, quindi nella finestra di ispezione:

    -   Assicurarsi che **piattaforma Any** viene **deselezionata**e che **solo** **WSAPlayer** è **selezionata**.

    -   Assicurarsi **SDK** è impostata su **UWP**, e **back-end di Scripting** è impostata su **Dot Net**

    -   Assicurarsi che **non elabora** viene **controllato**.

        ![](images/AzureLabs-Lab311-23.png)

7.  Fare clic su **Applica**.

## <a name="chapter-4---camera-setup"></a>Capitolo 4 - impostazione della fotocamera

Durante questo capitolo si configurerà la fotocamera principale della scena:

1.  Nel *Pannello di gerarchia*, selezionare la **Main Camera**.

2.  Una volta selezionata, sarà possibile visualizzare tutti i componenti del **Main Camera** nel *Inspector* pannello.

    1.  Il **oggetto della fotocamera** devono essere denominati **Main Camera** (si noti l'ortografici!)

    2.  Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici!)

    3.  Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**

    4.  Impostare **cancellare i flag** a **colore a tinta unita**

    5.  Impostare il **colore di sfondo** del componente della fotocamera **nero, Alpha 0** **(Hex codice: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  La struttura dell'oggetto finale nel *gerarchia pannello* dovrebbe essere simile a quello illustrato nell'immagine seguente:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Capitolo 5 - creare MeetingsUI classe

È il primo script da creare **MeetingsUI**, che è responsabile dell'hosting e popolando l'interfaccia utente dell'applicazione (messaggio di benvenuto, istruzioni e i dettagli di riunioni).

Per creare questa classe:

1.  Fare clic sul **asset** cartella la *pannello progetto*, quindi selezionare **crea** > **cartella**. Denominare la cartella **script**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Aprire il **gli script** cartella, quindi, all'interno di tale cartella, fare doppio clic su, **Create**  >   **C# Script**. Denominare lo script **MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Fare doppio clic su nuova **MeetingsUI** script per aprirlo con *Visual Studio*.

4.  Inserisci gli spazi dei nomi seguenti:

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

6.  Quindi sostituire il **Start ()** metodo e aggiungere un' **Awake()** (metodo). Questi verranno chiamati quando inizializza la classe:

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

7.  Aggiungere i metodi responsabili per la creazione di *riunioni UI* e popolarla con le riunioni corrente quando richiesto:

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

8. **Eliminare** il **Update ()** metodo, e **salvare le modifiche** in Visual Studio prima di tornare a Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Capitolo 6: creare la classe di Graph

Lo script successivo da creare è il **Graph** script. Questo script è responsabile di rendere le chiamate per autenticare l'utente e recuperare le riunioni pianificate per il giorno corrente dal calendario dell'utente.

Per creare questa classe:

1.  Fare doppio clic sulla **script** cartella per aprirla.

2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**. Denominare lo script **Graph**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserisci gli spazi dei nomi seguenti:

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
    > Si noterà che le parti del codice in questo script vengono eseguito il wrapping intorno [precompilare le direttive](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), questo serve a evitare problemi con le librerie quando si compila la soluzione Visual Studio.

5.  Eliminare il **Start ()** e **Update ()** metodi, poiché essi non verrà utilizzati.

6.  Di fuori di **Graph** classe, inserire gli oggetti seguenti, che sono necessari per deserializzare l'oggetto JSON che rappresenta le riunioni pianificate giornaliere:

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

7.  All'interno di **Graph** classe, aggiungere le variabili seguenti:

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
    > Modifica il **appId** valore sia il **App Id** annotato nella  **[capitolo 1](#chapter-1---create-your-app-in-the-application-registration-portal), passaggio 4**. Questo valore deve essere uguale a quello visualizzato nei **portale di registrazione delle applicazioni,** nella pagina di registrazione dell'applicazione.

8.  All'interno di **Graph** classe, aggiungere i metodi **SignInAsync()** e **AquireTokenAsync()** , che chiederà all'utente di inserire le credenziali di log.

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

    1.  **BuildTodayCalendarEndpoint()** , che si basa l'URI che specifica il giorno e intervallo di tempo, in cui vengono recuperate le riunioni pianificate.

    2.  **ListMeetingsAsync()** , che richiede le riunioni pianificate da *Microsoft Graph*.

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

10. È stata completata la **Graph** script. **Salvare le modifiche** in Visual Studio prima di tornare a Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Capitolo 7 - creare uno script di GazeInput

Ora si creerà il **GazeInput**. Questa classe gestisce e tiene traccia di sguardo dell'utente, utilizzando un **Raycast** provenienti dalle **Main Camera**, la proiezione in avanti.

Per creare lo script:

1.  Fare doppio clic sulla **script** cartella per aprirla.

2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**. Denominare lo script **GazeInput**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Modificare il codice degli spazi dei nomi in modo che corrisponda a quello riportato di seguito, con l'aggiunta di ' **\[System.Serializable\]** ' tag sopra il **GazeInput** classe, in modo che possa essere serializzato:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  All'interno di **GazeInput** classe, aggiungere le variabili seguenti:

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

6.  Aggiungere il **CreateCursor()** per creare il cursore di HoloLens nella scena e chiamare il metodo dalle **Start ()** metodo:

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

7.  I metodi seguenti abilitare sguardo Raycast e tenere traccia degli oggetti con lo stato attivo.

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

## <a name="chapter-8---create-the-interactions-class"></a>Capitolo 8 - creare la classe interazioni

È ora necessario creare il **interazioni** script, che è responsabile per:

-   La gestione di **toccare** interazione e il **fotocamera estasiati**, che consente all'utente di interagire con i log in "button" nella scena.

-   Creazione del log nell'oggetto "button" nella scena per l'utente può interagire.

Per creare lo script:

1.  Fare doppio clic sulla **script** cartella per aprirla.

2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Create**  >   **C# Script**. Denominare lo script **interazioni**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserisci gli spazi dei nomi seguenti:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Modificare l'ereditarietà del **interazione** classe *MonoBehaviour* al **GazeInput**.

    ~~classe pubblica le interazioni: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  All'interno di **interazione** classe inserire la variabile seguente:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Sostituire il **avviare** metodo; si noti che è un metodo di override, che chiama il metodo della classe sguardo 'base'. **Start ()** verrà chiamato quando si inizializza la classe, la registrazione per il riconoscimento di input e la creazione di accesso *pulsante* nella scena:

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

8.  Aggiungere il **CreateSignInButton()** metodo, che verrà creata un'istanza di accesso *pulsante* nella scena e impostarne le proprietà:

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

9.  Aggiungere il **GestureRecognizer_Tapped()** metodo, che è possibile rispondere per il *toccare* evento utente.

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

10. **Eliminare** il **Update ()** metodo e quindi **salvare le modifiche** in Visual Studio prima di tornare a Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Capitolo 9: configurare i riferimenti a script

In questo capitolo è necessario inserire il **interazioni** nello script le **Main Camera**. Lo script gestirà quindi l'inserimento altri script in cui devono essere.

-  Dal **script** cartella il *pannello progetto*, trascinare lo script **interazioni** per il **Main Camera** dell'oggetto, come illustrata di seguito.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Capitolo 10 - configurare i Tag

Il codice che gestisce lo sguardo useranno il Tag **SignInButton** per identificare l'oggetto con cui interagirà l'utente con effettuare l'accesso per *Microsoft Graph*.

Per creare il Tag:

1.  Nell'Editor di Unity fare clic sui **Main Camera** nel *gerarchia pannello*.

2.  Nel *Pannello di controllo* fare clic sulla **MainCamera** *Tag* per aprire un elenco a discesa. Fare clic su **aggiungere Tag...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Fare clic sui **+** pulsante.

    ![](images/AzureLabs-Lab311-31.png)

4.  Scrivere il nome del Tag come **SignInButton** e fare clic su Salva.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Capitolo 11 - compilare il progetto di Unity per UWP

Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.

1.  Passare a *impostazioni di compilazione* (**File* > *Impostazioni di compilazione**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Se non è già, graduazione **C Unity\# progetti**.

3.  Fai clic su **Compila**. Unity avvierà una **Esplora File** finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in. Creare ora tale cartella e denominarlo **App**. Quindi con il **App** cartella selezionata, fare clic su **Seleziona cartella**.

4.  Unity verrà avviata la compilazione del progetto per la **App** cartella.

5.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).

## <a name="chapter-12---deploy-to-hololens"></a>Capitolo 12 - distribuire a HoloLens

Per distribuire in HoloLens:

1.  È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore.** A tale scopo, effettuare le seguenti operazioni:

    1.  Durante l'uso di HoloLens, aprire il **impostazioni**.

    2.  Passare a **rete e Internet** > **Wi-Fi** > **opzioni avanzate**

    3.  Si noti il **IPv4** indirizzo.

    4.  Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza** > **per gli sviluppatori**

    5.  Impostare **modalità sviluppatore su**.

2.  Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.

3.  Nel **configurazione della soluzione** selezionate **Debug**.

4.  Nel **piattaforma soluzione**, selezionare **x86, computer remoto**. Verrà richiesto di inserire le **indirizzo IP** di un dispositivo remoto (il HoloLens, in questo caso, che si è preso nota).

    ![](images/AzureLabs-Lab311-34.png)

5.  Passare a **compilare** dal menu e fare clic su **Distribuisci soluzione** trasferire localmente l'applicazione di HoloLens.

6.  L'app deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.

## <a name="your-microsoft-graph-hololens-application"></a>L'applicazione di Microsoft Graph HoloLens

Complimenti, è stata compilata un'app per realtà mista che si basa su Microsoft Graph, per leggere e visualizzare i dati del calendario di utente.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

Usare Microsoft Graph per visualizzare altre informazioni sull'utente

-   Messaggio di posta elettronica utente / numero di telefono / immagine del profilo

### <a name="exercise-1"></a>Esercizio 1

Implementare il controllo di casella vocale per passare l'interfaccia utente di Microsoft Graph.
