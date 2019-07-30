---
title: Integrazione di MR e Azure 312-bot
description: Completare questo corso per apprendere come creare e distribuire un bot, usando Microsoft bot Framework V4 e comunicare con esso in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realtà mista, Accademia, Unity, esercitazione, API, visione artificiale, hololens, immersiva, VR, Microsoft bot Framework V4, bot per app Web, bot Framework, Microsoft bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63542859"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

# <a name="mr-and-azure-312-bot-integration"></a>MR e Azure 312: Integrazione bot

In questo corso si apprenderà come creare e distribuire un bot con Microsoft bot Framework V4 e come comunicare con esso tramite un'applicazione di realtà mista di Windows. 

![](images/AzureLabs-Lab312-00.png)

**Microsoft bot Framework V4** è un set di API progettate per fornire agli sviluppatori gli strumenti necessari per creare un'applicazione bot estensibile e scalabile. Per ulteriori informazioni, visitare la [pagina Microsoft bot Framework](https://dev.botframework.com/) o il [repository git V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).

Al termine di questo corso, sarà stata compilata un'applicazione di realtà mista di Windows, che sarà in grado di eseguire le operazioni seguenti:

1. Usare un **movimento Tap** per avviare il bot in ascolto per la voce degli utenti.
2. Quando l'utente ha detto qualcosa, il bot tenterà di fornire una risposta.
3. Visualizza la risposta dei bot come testo, posizionata vicino al bot, nella scena Unity.

Nell'applicazione, spetta all'utente come integrare i risultati con la progettazione. Questo corso è stato progettato per insegnare come integrare un servizio di Azure con il progetto Unity. Per migliorare l'applicazione di realtà mista, è compito dell'utente sfruttare le conoscenze acquisite in questo corso.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 312: Integrazione bot</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Sebbene questo corso sia incentrato principalmente su HoloLens, è anche possibile applicare le informazioni apprese in questo corso agli auricolari per la realtà mista (VR) di Windows. Poiché le cuffie immersive (VR) non hanno fotocamere accessibili, sarà necessaria una fotocamera esterna connessa al PC. Seguendo le istruzioni riportate in questo corso, vengono visualizzate le note sulle eventuali modifiche che potrebbero essere necessarie per supportare gli auricolari immersivi (VR).

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
- Accesso a Internet per Azure e per il recupero di bot di Azure. Per ulteriori informazioni, [seguire questo collegamento](https://dev.botframework.com/).

### <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare che si verifichino problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartella lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la taratura e l'ottimizzazione dei sensori, a volte può essere utile per eseguire queste attività per ogni utente. 

Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Capitolo 1-creare l'applicazione bot

Il primo passaggio consiste nel creare il bot come applicazione Web ASP.Net Core locale. Una volta completato e testato, sarà possibile pubblicarlo nel portale di Azure.

1.  Aprire Visual Studio. Creare un nuovo progetto, selezionare **applicazione Web ASP NET Core** come tipo di progetto (sarà presente nella sottosezione .NET Core) e denominarlo **MyBot**. Fare clic su **OK**.

2.  Nella finestra che verrà visualizzata selezionare **vuoto**. Assicurarsi anche che la destinazione sia impostata su **ASP NET Core 2,0** e che l'autenticazione sia impostata su **Nessuna autenticazione**. Fare clic su **OK**.  

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-01.png)

3.  La soluzione verrà aperta. Fare clic con il pulsante destro del mouse su soluzione **Mybot** nel **Esplora soluzioni** e fare clic su **Gestisci pacchetti NuGet per la soluzione**. 

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-02.png)

4.  Nella scheda **Sfoglia** cercare **Microsoft. bot. Builder. Integration. AspNet. Core** (assicurarsi di **includere la versione non definitiva** selezionata). Selezionare la versione del pacchetto **4.0.1-Preview**e selezionare le caselle di progetto. Quindi fare clic su **Installa**. Sono ora installate le librerie necessarie per **bot Framework V4**. Chiudere la pagina NuGet.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-03.png)

5.  Fare clic con il pulsante destro del mouse sul *progetto*, **MyBot**, nella **Esplora soluzioni** e fare clic su **Aggiungi** **|** **classe**.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-04.png)

6.  Assegnare alla classe il nome **MyBot** e fare clic su **Aggiungi**.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-05.png)

7.  Ripetere il punto precedente per creare un'altra classe denominata **ConversationContext**. 

8.  Fare clic con il pulsante destro del mouse su **wwwroot** nel **Esplora soluzioni** e fare clic su **Aggiungi** **|** **nuovo elemento**. Selezionare la **pagina HTML** (si troverà nella sottosezione Web). Denominare il file **default. html**. Fare clic su **Aggiungi**.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-06.png)

9.  L'elenco di classi/oggetti nel **Esplora soluzioni** dovrebbe essere simile all'immagine seguente.

    ![Creare l'applicazione bot](images/AzureLabs-Lab312-07.png)

10. Fare doppio clic sulla classe **ConversationContext** . Questa classe è responsabile della conservazione delle variabili usate dal bot per mantenere il contesto della conversazione. Questi valori del contesto di conversazione vengono mantenuti in un'istanza di questa classe, perché ogni istanza della classe **MyBot** verrà aggiornata ogni volta che viene ricevuta un'attività. Aggiungere il codice seguente alla classe:

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Fare doppio clic sulla classe **MyBot** . Questa classe ospiterà i gestori chiamati da qualsiasi attività in ingresso dal cliente. In questa classe verrà aggiunto il codice usato per compilare la conversazione tra il bot e il cliente. Come indicato in precedenza, un'istanza di questa classe viene inizializzata ogni volta che viene ricevuta un'attività. Aggiungere il codice seguente a questa classe:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Fare doppio clic sulla classe **Startup** . Questa classe inizializza il bot. Aggiungere il codice seguente alla classe:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Aprire il file della classe **Program** e verificare che il codice sia uguale a quello riportato di seguito:

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. Ricordarsi di salvare le modifiche. a tale scopo, passare a **file** > **Salva tutto**, dalla barra degli strumenti nella parte superiore di Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Capitolo 2: creare il servizio Azure bot

Ora che è stato compilato il codice per il bot, è necessario pubblicarlo in un'istanza del servizio *bot app Web* nel portale di Azure. In questo capitolo viene illustrato come creare e configurare il servizio bot in Azure e quindi come pubblicarvi il codice.

1.  Per prima cosa, accedere al portale di Azure https://portal.azure.com) (. 

    1. Se non si dispone già di un account Azure, sarà necessario crearne uno. Se si segue questa esercitazione in una classe o in una situazione di laboratorio, rivolgersi all'insegnante o a uno dei Proctor per ottenere assistenza nella configurazione del nuovo account.

2.  Una volta effettuato l'accesso, fare clic su **Crea una risorsa** nell'angolo in alto a sinistra e cercare *bot app Web*e premere **invio**.

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-08.png)
 
3.  La nuova pagina fornirà una descrizione del servizio *bot per app Web* . Nella parte inferiore sinistra della pagina selezionare il pulsante **Crea** per creare un'associazione con il servizio.

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-09.png)
 
4.  Una volta fatto clic su **Crea**:

    1. Inserire il **nome** desiderato per l'istanza del servizio.
    2. Selezionare una **sottoscrizione**.
    3. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [il collegamento](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) seguente.

    4. Determinare il percorso del gruppo di risorse (se si sta creando un nuovo gruppo di risorse). Il percorso dovrebbe trovarsi idealmente nell'area in cui verrà eseguita l'applicazione. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.
    5. Selezionare il piano tariffario appropriato. se è la prima volta che si crea un servizio *bot app Web* , è necessario che sia disponibile un livello gratuito (denominato F0)
    6. Il **nome dell'app** può essere semplicemente lasciato lo stesso *nome del bot*. 
    7. Lasciare il *modello bot* come **Basic (C#)** .
    8. Il *piano/percorso di servizio app* deve essere stato compilato automaticamente per l'account.
    9. Impostare l' **archiviazione di Azure** che si vuole usare per ospitare il bot. Se non ne è già disponibile uno, è possibile crearlo qui.
    10. Sarà inoltre necessario confermare di aver compreso i termini e le condizioni applicati a questo servizio.
    11. Fare clic su Crea.
 
        ![Creare il servizio Azure bot](images/AzureLabs-Lab312-10.png)

5.  Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.

6.  Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-11.png) 
 
7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-12.png)
 
8. Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio Azure. 

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-13.png)
 
9.  A questo punto è necessario configurare una funzionalità denominata **Direct Line** per consentire all'applicazione client di comunicare con questo servizio bot. Fare clic su **canali**, quindi nella sezione **Aggiungi un canale in primo piano** fare clic su **Configura canale linea diretta**.

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-14.png)

10. In questa pagina sono disponibili le **chiavi segrete** che consentiranno all'app client di eseguire l'autenticazione con il bot. Fare clic sul pulsante **Mostra** per eseguire una copia di una delle chiavi visualizzate, perché sarà necessario in un secondo momento nel progetto. 

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Capitolo 3: pubblicare il bot nel servizio bot app Web di Azure

Ora che il servizio è pronto, è necessario pubblicare il codice bot, che è stato compilato in precedenza, per il servizio bot app Web appena creato.

> [!NOTE] 
> Sarà necessario pubblicare il bot nel servizio di Azure ogni volta che si apportano modifiche al codice o alla soluzione bot.

1.  Tornare alla soluzione di Visual Studio creata in precedenza. 
2.  Fare clic con il pulsante destro del mouse sul progetto **MyBot** , nel **Esplora soluzioni**, quindi fare clic su **pubblica**.

    ![Pubblicare il bot nel servizio bot app Web di Azure](images/AzureLabs-Lab312-16.png)

3.  Nella pagina *selezionare una destinazione di pubblicazione* fare clic su **servizio app**, quindi **selezionare esistente**, infine fare clic su **Crea profilo** . se non è visibile, potrebbe essere necessario fare clic sulla freccia a discesa insieme al pulsante *pubblica* .

    ![Pubblicare il bot nel servizio bot app Web di Azure](images/AzureLabs-Lab312-17.png)

4. Se non si è ancora connessi all'account Microsoft, è necessario eseguire questa operazione qui.
5. Nella pagina **pubblica** si noterà che è necessario impostare la stessa **sottoscrizione** usata per la creazione del servizio *bot per app Web* . Impostare quindi la **vista** come **gruppo di risorse** e nella struttura di cartelle a discesa selezionare il **gruppo di risorse** creato in precedenza. Fare clic su **OK**. 

    ![Pubblicare il bot nel servizio bot app Web di Azure](images/AzureLabs-Lab312-18.png)

6.  A questo punto fare clic sul pulsante **pubblica** e attendere che il bot venga pubblicato. potrebbero essere necessari alcuni minuti.

    ![Pubblicare il bot nel servizio bot app Web di Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Capitolo 4: configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, un modello valido per altri progetti.

1.  Aprire *Unity* e fare clic su **New**. 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-20.png)

2.  A questo punto sarà necessario specificare un nome di progetto Unity. Inserire il **bot Hololens**. Verificare che il modello di progetto sia impostato su **3D**. Impostare il **percorso** su un punto appropriato (ricordare che più vicino alle directory radice è migliore). Fare quindi clic su **Crea progetto**.

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-21.png)

3.  Con Unity aperto, vale la pena controllare che l' **editor di script** predefinito sia impostato su **Visual Studio**. Passare a **Modifica preferenze >** e quindi dalla nuova finestra passare a **strumenti esterni**. Modificare l' **editor di script esterno** in **Visual Studio 2017**. Chiudere la finestra delle **Preferenze** .

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-22.png)

4.  Passare quindi a **File > impostazioni di compilazione** e selezionare **piattaforma UWP (Universal Windows Platform)** , quindi fare clic sul pulsante **Cambia piattaforma** per applicare la selezione.

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-23.png)

5.  Sempre in **File > impostazioni di compilazione** e verificare che:

    1.  Il **dispositivo di destinazione** è impostato su **Hololens**

        > Per gli auricolari immersivi, impostare **dispositivo di destinazione** su *qualsiasi dispositivo*.

    2.  Il **tipo di compilazione** è impostato su **D3D**

    3.  **SDK** è impostato sull' **ultima versione installata**

    4.  La **versione di Visual Studio** è impostata su **installazione più recente**

    5.  **Compilazione ed esecuzione** è impostato su **computer locale**

    6.  Salvare la scena e aggiungerla alla compilazione. 

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra Salva.
        
            ![Configurare il progetto Unity](images/AzureLabs-Lab312-24.png)

        2. Creare una nuova cartella per questo e per eventuali scenari futuri, quindi selezionare il pulsante **nuova cartella** per creare una nuova cartella **, assegnarle**un nome.

             ![Configurare il progetto Unity](images/AzureLabs-Lab312-25.png)

        3. Aprire la cartella **Scenes** appena creata e quindi nel campo *nome file*: testo digitare **BotScene**e quindi fare clic su **Salva**.

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-26.png)

    7. Le impostazioni rimanenti, nelle **impostazioni di compilazione**, devono essere lasciate come predefinite per il momento.

6. Nella finestra *impostazioni di compilazione* fare clic sul pulsante **Impostazioni lettore** . verrà aperto il pannello correlato nello spazio in cui si trova il *controllo* . 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-27.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **altre impostazioni** :

        1. La **versione di runtime** di scripting deve essere **sperimentale (equivalente alla rete 4,6)** ; per modificare questa operazione, è necessario riavviare l'editor.
        2. Il **back-end** di scripting deve essere **.NET**
        3. Il **livello di compatibilità API** deve essere **.NET 4,6**

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-28.png)
      
    2. Nella scheda **impostazioni di pubblicazione** , in **funzionalità**, selezionare:

        - **InternetClient**
        - **Microfono**

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-29.png)

    3. Nella parte inferiore del pannello, **nelle impostazioni di XR** (disponibili sotto **le impostazioni di pubblicazione**), verificare la **realtà virtuale supportata**, verificare che sia stato aggiunto **Windows Mixed Reality SDK** .

        ![Configurare il progetto Unity](images/AzureLabs-Lab312-30.png)

8.  Nelle *impostazioni di compilazione* i progetti _Unity C#_  non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra impostazioni di compilazione.
10. Salvare la scena e il progetto (**file > Salva scena/file > Salva progetto**).


## <a name="chapter-5--camera-setup"></a>Capitolo 5-configurazione della fotocamera

> [!IMPORTANT]
> Se si vuole ignorare il componente di *configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricare questo [Azure-Mr-312-Package. file unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importarlo nel progetto come [**pacchetto personalizzato**](https://docs.unity3d.com/Manual/AssetPackages.html)e continuare da [ Capitolo 7](#chapter-7-–-create-the-botobjects-class).

1.  Nel *Pannello gerarchia*selezionare la **fotocamera principale**. 
2.  Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel *Pannello di controllo*.

    1. L' **oggetto fotocamera** deve essere denominato **Main camera** (nota l'ortografia)
    2. Il **tag** della fotocamera principale deve essere impostato su **MainCamera** (annotare l'ortografia)
    3. Assicurarsi che la **posizione di trasformazione** sia impostata su **0, 0, 0**
    4. Impostare **Cancella flag** su **colore a tinta unita**.
    5. Imposta il colore di **sfondo** del componente della fotocamera su **nero, alfa 0 (codice esadecimale: #00000000)**

    ![Configurazione della fotocamera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Capitolo 6: importare la libreria Newtonsoft

Per semplificare la deserializzazione e la serializzazione degli oggetti ricevuti e inviati al servizio bot, è necessario scaricare la libreria **Newtonsoft** . È disponibile una [versione compatibile già organizzata con la struttura di cartelle Unity corretta](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage). 

Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornito con questo corso.

1.  Aggiungere il *file unitypackage Tools* a Unity usando l'opzione di menu **Asset** > **Import Package** > **Custom Package** .

    ![Importare la libreria Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  Nella casella **Importa pacchetto Unity** visualizzata verificare che siano selezionati tutti gli elementi in (e inclusi) **plug** -in.

    ![Importare la libreria Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Fare clic sul pulsante **Importa** per aggiungere gli elementi al progetto.

4.  Passare alla cartella **Newtonsoft** in **plug** -in nella visualizzazione del progetto e selezionare il plug-in Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Con il plug-in Newtonsoft selezionato, verificare che **qualsiasi piattaforma** sia deselezionata, quindi verificare che **WSAPlayer** sia deselezionata, quindi fare clic su **applica**. Questa operazione è sufficiente per verificare che i file siano configurati correttamente.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Contrassegnando questi plug-in, questi vengono configurati per essere usati solo nell'editor di Unity. Nella cartella WSA è presente un set diverso che verrà usato dopo l'esportazione del progetto da Unity.

6.  Successivamente, è necessario aprire la cartella **WSA** , all'interno della cartella **Newtonsoft** . Viene visualizzata una copia dello stesso file appena configurato. Selezionare il file e quindi nel controllo verificare che
    -   **Qualsiasi piattaforma** è deselezionata 
    -   **solo** **WSAPlayer** è **selezionato**
    -   Il **processo** non è **selezionato**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Capitolo 7: creare il BotTag

1.  Creare un nuovo oggetto **tag** denominato **BotTag**. Selezionare la fotocamera principale nella scena. Fare clic sul menu a discesa Tag nel pannello Inspector. Fare clic su **Aggiungi tag**.

    ![Configurazione della fotocamera](images/AzureLabs-Lab312-32.png)
 
2.  Fare clic sul **+** simbolo. Denominare il nuovo **tag** come **BotTag**, *Save*.

    ![Configurazione della fotocamera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> Non applicare **BotTag** alla fotocamera principale. Se questa operazione è stata eseguita accidentalmente, assicurarsi di modificare di nuovo il tag della fotocamera principale in *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Capitolo 8: creare la classe BotObjects

Il primo script che è necessario creare è la classe **BotObjects** , che è una classe vuota creata in modo che una serie di altri oggetti classe possa essere archiviata nello stesso script e accessibile da altri script nella scena.

La creazione di questa classe è puramente una scelta di architettura. questi oggetti possono invece essere ospitati nello script bot che verrà creato più avanti in questo corso.

Per creare questa classe: 

1.  Fare clic con il pulsante destro del mouse nel *Pannello del progetto*, quindi **creare > cartella**. Denominare gli **script**della cartella. 

    ![Crea cartella script.](images/AzureLabs-Lab312-36.png)

2.  Fare doppio clic sulla cartella **script** per aprirla. Quindi, all'interno di tale cartella, fare clic con il pulsante destro del mouse e scegliere **crea > C# script**. Denominare lo script **BotObjects**. 

3.  Fare doppio clic sul nuovo script **BotObjects** per aprirlo con **Visual Studio**.

4.  Eliminare il contenuto dello script e sostituirlo con il codice seguente:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-9--create-the-gazeinput-class"></a>Capitolo 9: creare la classe GazeInput

La classe successiva che si intende creare è la classe **GazeInput** . Questa classe è responsabile di:

- Creazione di un cursore che rappresenterà lo *sguardo* del lettore.
- Rilevamento degli oggetti colpiti dallo sguardo del lettore e mantenimento di un riferimento agli oggetti rilevati.

Per creare questa classe: 

1.  Passare alla cartella **Scripts** creata in precedenza. 
2.  Fare clic con il pulsante destro del mouse all'interno della cartella, quindi **creare > C# script**. Chiamare lo script **GazeInput**. 
3.  Fare doppio clic sul nuovo script **GazeInput** per aprirlo con **Visual Studio**.
4.  Inserire la riga seguente direttamente sopra il nome della classe:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Aggiungere quindi le variabili seguenti all'interno della classe **GazeInput** , sopra il metodo **Start ()** :

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  È necessario aggiungere il codice per il metodo **Start ()** . Questa operazione verrà chiamata quando la classe inizializza:

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Implementare un metodo che creerà un'istanza e configurerà il cursore di sguardi: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Implementare i metodi per la configurazione di Raycast dalla fotocamera principale e per tenere traccia dell'oggetto attivo corrente.

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-10--create-the-bot-class"></a>Capitolo 10: creare la classe bot

Lo script che si intende creare è denominato **bot**. Questa è la classe principale dell'applicazione, che archivia: 

- Credenziali bot dell'app Web
- Metodo che raccoglie i comandi vocali dell'utente
- Metodo necessario per avviare conversazioni con il bot dell'app Web 
- Metodo necessario per inviare messaggi al bot dell'app Web 

Per inviare messaggi al servizio bot, la coroutine **SendMessageToBot ()** compilerà un'attività, ovvero un oggetto riconosciuto da bot Framework come dati inviati dall'utente. 
 
Per creare questa classe: 

1. Fare doppio clic sulla cartella **Scripts** per aprirla. 
2. Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**. Assegnare un nome al **bot**di script. 
3. Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4. Aggiornare gli spazi dei nomi in modo che siano uguali a quelli riportati di seguito, nella parte superiore della classe **bot** :

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. All'interno della classe **bot** aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Assicurarsi di inserire la **chiave privata bot** nella variabile **botSecret** . Si noterà che la **chiave privata del bot** è stata annotata all'inizio di questo corso, nel  **[capitolo 2](#chapter-2---create-the-azure-bot-service), passaggio 10**.

7. È necessario aggiungere il codice per **sveglie ()** e **Start ()** . 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Aggiungere i due gestori chiamati dalle librerie vocali quando l'acquisizione vocale inizia e termina. Il *DictationRecognizer* arresterà automaticamente l'acquisizione della voce utente quando l'utente smette di parlare.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. Il gestore seguente raccoglie il risultato dell'input vocale dell'utente e chiama la coroutine responsabile dell'invio del messaggio al servizio bot dell'app Web.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. La seguente coroutine viene chiamata per avviare una conversazione con il bot. Si noterà che, al termine della chiamata di conversazione, viene chiamato **SendMessageToCoroutine ()** passando una serie di parametri che imposteranno l'attività da inviare al servizio bot come messaggio vuoto. Questa operazione viene eseguita per richiedere al servizio bot di avviare il dialogo.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. La seguente coroutine viene chiamata per compilare l'attività da inviare al servizio bot. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. La seguente coroutine viene chiamata per richiedere una risposta dopo l'invio di un'attività al servizio bot. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. L'ultimo metodo da aggiungere a questa classe è necessario per visualizzare il messaggio nella scena:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > È possibile che venga visualizzato un errore nella console dell'editor di Unity, in cui manca la classe **SceneOrganiser** . Ignorare questo messaggio, in quanto la classe verrà creata più avanti nell'esercitazione.

14.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Capitolo 11: creare la classe di interazioni

La classe che si intende creare ora è chiamata **interazioni**. Questa classe viene usata per rilevare l'input di HoloLens Tap dall'utente. 

Se l'utente tocca osservando l'oggetto *bot* nella scena e il bot è pronto per l'ascolto degli input vocali, l'oggetto bot cambierà il colore in **rosso** e inizierà ad ascoltare gli input vocali. 

Questa classe eredita dalla classe **GazeInput** ed è quindi in grado di fare riferimento al metodo **Start ()** e alle variabili da tale classe, identificate dall'uso di **base**. 
 
Per creare questa classe:

1.  Fare doppio clic sulla cartella **Scripts** per aprirla. 
2.  Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**. Denominare le **interazioni**dello script. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi e l'ereditarietà della classe in modo che corrispondano a quanto riportato di seguito, nella parte superiore della classe Interactions:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  All'interno della classe Interactions aggiungere la variabile seguente:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Aggiungere quindi il metodo **Start ()** :

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  Aggiungere il gestore che verrà attivato quando l'utente esegue il gesto Tap davanti alla fotocamera HoloLens

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Capitolo 12: creare la classe SceneOrganiser

L'ultima classe richiesta in questo Lab è denominata **SceneOrganiser**. Questa classe imposta la scena a livello di codice, aggiungendo componenti e script alla fotocamera principale e creando gli oggetti appropriati nella scena.
 
Per creare questa classe:

1.  Fare doppio clic sulla cartella **Scripts** per aprirla. 
2.  Fare clic con il pulsante destro del mouse nella cartella Scripts, quindi scegliere **Crea > C# script**. Denominare lo script **SceneOrganiser**. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  All'interno della classe **SceneOrganiser** aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  Aggiungere quindi i metodi **svegli ()** e **Start ()** :

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Aggiungere il metodo seguente, responsabile della creazione dell'oggetto bot nella scena e della configurazione dei parametri e dei componenti:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Aggiungere il metodo seguente, responsabile della creazione dell'oggetto dell'interfaccia utente nella scena, che rappresenta le risposte dal bot:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity*.
9.  Nell'editor di Unity trascinare lo script **SceneOrganiser** dalla cartella Scripts alla fotocamera principale. Il componente dell'organizzatore della scena dovrebbe essere ora visualizzato nell'oggetto principale della fotocamera, come illustrato nell'immagine seguente.

    ![Creare il servizio Azure bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Capitolo 13: prima della compilazione

Per eseguire un test completo dell'applicazione, è necessario sideload nel HoloLens.
Prima di procedere, verificare quanto segue:

-   Tutte le impostazioni indicate nel [**capitolo 4**](#Chapter-4-–-Set-up-the-unity-project) sono impostate correttamente. 
-   Lo script **SceneOrganiser** è associato all'oggetto **principale della fotocamera** . 
-   Nella classe **bot** verificare di aver inserito la **chiave privata bot** nella variabile **botSecret** .

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Capitolo 14: compilare e sideload in HoloLens

Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è giunto il momento di compilarli da Unity.

1.  Passare a **impostazioni di compilazione**, **file > impostazioni di compilazione...** .
2.  Nella finestra **impostazioni di compilazione** fare clic su **Compila**.

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab312-38.png)

3.  Se non è già stato fatto, è necessario che i **progetti C# Unity**
4.  Fai clic su **Compila**. Unity avvierà una finestra di **Esplora file** , in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella adesso e denominarla **app**. Quindi, con la cartella dell' **app** selezionata, fare clic su **Seleziona cartella**. 
5.  Unity inizierà a compilare il progetto nella cartella dell' **app** . 
6.  Una volta completata la compilazione di Unity (potrebbe richiedere del tempo), verrà aperta una finestra **Esplora file** nella posizione della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà inviata una notifica sull'aggiunta di una nuova finestra).

## <a name="chapter-15--deploy-to-hololens"></a>Capitolo 15: distribuire in HoloLens

Per eseguire la distribuzione in HoloLens:

1.  È necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore**. A tale scopo, effettuare le seguenti operazioni:

    1. Quando si indossa il HoloLens, aprire le **Impostazioni**.
    2. Passare a **rete & Internet > opzioni avanzate Wi-Fi >**
    3. Prendere nota dell'indirizzo **IPv4** .
    4. Quindi, tornare a **Settings (impostazioni**) e quindi **aggiornare & Security > per gli sviluppatori** 
    5. Impostare la modalità di sviluppo su.

2.  Passare alla nuova compilazione Unity (cartella **app** ) e aprire il file della soluzione con **Visual Studio**.
3.  Nella **configurazione della soluzione** selezionare **debug**.
4.  Nella **piattaforma soluzione**selezionare **x86**, **computer remoto**. 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Passare al **menu Compila** e fare clic su **Distribuisci soluzione**per sideload l'applicazione in HoloLens.
6.  L'app verrà visualizzata nell'elenco delle app installate nella HoloLens, pronta per l'avvio.

    > [!NOTE]
    > Per eseguire la distribuzione in un dispositivo headset immersivo, impostare la **piattaforma della soluzione** su *computer locale*e impostare la **configurazione** su *debug*, con *x86* come **piattaforma**. Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Capitolo 16: uso dell'applicazione in HoloLens

- Una volta avviata l'applicazione, il bot viene visualizzato come una sfera blu davanti all'utente.

- Usare il **gesto Tap** mentre si sta guardando la sfera per avviare una conversazione. 
 
- Attendere l'avvio della conversazione (l'interfaccia utente visualizzerà un messaggio quando si verifica). Una volta ricevuto il messaggio introduttivo dal bot, toccare di nuovo sul bot in modo che diventi rosso e inizi ad ascoltare la voce. 

- Una volta terminata la conversazione, l'applicazione invierà il messaggio al bot e si riceverà immediatamente una risposta che verrà visualizzata nell'interfaccia utente. 

- Ripetere il processo per inviare altri messaggi al bot (è necessario toccare ogni volta che si desidera un messaggio).

In questa conversazione viene illustrato come il bot può conservare le informazioni (il nome), fornendo anche informazioni note, ad esempio gli elementi che sono disponibili.

#### <a name="some-questions-to-ask-the-bot"></a>Domande per chiedere al bot:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Applicazione bot (v4) per app Web completata

Congratulazioni, è stata creata un'app per realtà mista che sfrutta il bot app Web di Azure, Microsoft bot Framework V4.

![Prodotto finale](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

La struttura di conversazione in questo Lab è molto semplice. Usare Microsoft LUIS per offrire al bot funzionalità di comprensione del linguaggio naturale.

### <a name="exercise-2"></a>Esercizio 2

Questo esempio non include la terminazione di una conversazione e il riavvio di un nuovo. Per completare la funzionalità bot, provare a implementare la chiusura per la conversazione.
