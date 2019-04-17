---
title: MR e 312 Azure - integrazione di Bot
description: Completare questo corso per informazioni su come creare e distribuire un bot, tramite Microsoft Bot Framework v4 e consentire la comunicazione in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realtà mista, Azure, academy, unity, esercitazione, api, visione artificiale, hololens, vr immersivi, microsoft bot framework v4, bot per app web, bot framework, bot di microsoft
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604980"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

# <a name="mr-and-azure-312-bot-integration"></a>MR e Azure 312: Integrazione di BOT

In questo corso, si apprenderà come creare e distribuire un bot tramite il Microsoft Bot Framework versione 4 e comunicare con esso tramite un'applicazione di realtà mista di Windows. 

![](images/AzureLabs-Lab312-00.png)

Il **Microsoft Bot Framework V4** è un set di API progettato per offrire agli sviluppatori gli strumenti necessari per compilare un bot estendibile e scalabile dell'applicazione. Per altre informazioni, visitare il [pagina Microsoft Bot Framework](https://dev.botframework.com/) o nella [Git Repository V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).

Dopo aver completato il corso, verrà generata un'applicazione di realtà mista di Windows, che sarà in grado di eseguire le operazioni seguenti:

1. Usare un **movimento toccare** per avviare il bot in ascolto per la voce degli utenti.
2. Quando l'utente ha detto qualcosa, il bot proverà a fornire una risposta.
3. Visualizzare la risposta del Bot come testo, posizionato in prossimità del bot, nella scena Unity.

Nell'applicazione, è responsabilità dell'utente per quanto riguarda la modalità si integrerà i risultati con la progettazione. Questo corso è pensato per scoprire come integrare un servizio di Azure con il progetto Unity. È il compito di utilizzare le competenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> MR e Azure 312: Integrazione di BOT</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Questo corso è incentrato principalmente sulla HoloLens, è inoltre possibile applicare informazioni in questo corso per auricolari (VR) coinvolgenti di realtà mista di Windows. Poiché immersive auricolari (VR) non è accessibile fotocamere, sarà necessario una fotocamera esterna connessa al PC. Seguendo gli argomenti del corso, si noterà note in tutte le modifiche potrebbe essere necessario impiegare per supportare immersive auricolari (VR).

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
- Accesso a Internet per Azure e per il recupero di Bot di Azure. Per altre informazioni, [, seguire questo collegamento](https://dev.botframework.com/).

### <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare l'insorgere di problemi di compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o in prossimità di primo livello (i percorsi delle cartelle lungo possono causare problemi in fase di compilazione).
2.  Configurare e testare l'HoloLens. Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  È una buona idea eseguire calibrazione e ottimizzazione sensore quando si inizia a sviluppare una nuova app per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente). 

Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).

Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Capitolo 1: creare l'applicazione di Bot

Il primo passaggio consiste nella creazione del bot come un'applicazione Web ASP.Net Core locale. Dopo avere completato e testato, si sarà pubblicarla nel portale di Azure.

1.  Aprire Visual Studio. Creare un nuovo progetto, seleziona **ASP NET Core Web Application** come tipo di progetto (risulterà sotto la sottosezione .NET Core) e chiamarlo **MyBot**. Fare clic su **OK**.

2.  Nella finestra che verrà visualizzato seleziona **vuoto**. Inoltre assicurarsi che la destinazione è impostata su **ASP NET Core 2.0** e l'autenticazione è impostata su **Nessuna autenticazione**. Fare clic su **OK**.  

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-01.png)

3.  A questo punto verrà aperta la soluzione. Pulsante destro del mouse sulla soluzione **Mybot** nel **Esplora soluzioni** e fare clic su **Gestisci pacchetti NuGet per la soluzione**. 

    ![Creare l'applicazione di Bot](images/AzureLabs-Lab312-02.png)

4.  Nel **esplorare** scheda, cercare **Microsoft.Bot.Builder.Integration.AspNet.Core** (assicurarsi di avere **includono versioni non definitive** selezionata). Selezionare la versione del pacchetto **4.0.1-Preview**e selezionare le caselle di progetto. Quindi fare clic su **installare**. Ora state installate le librerie necessarie per la **Bot Framework v4**. Chiudere la pagina di NuGet.

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-03.png)

5.  Fare clic sui *Project*, **MyBot**, nel **Esplora soluzioni** e fare clic su **Aggiungi** **|** **Classe**.

    ![Creare l'applicazione di Bot](images/AzureLabs-Lab312-04.png)

6.  Denominare la classe **MyBot** e fare clic su **Add**.

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-05.png)

7.  Ripetere il precedente punto, per creare un'altra classe denominata **ConversationContext**. 

8.  Fare clic su **wwwroot** nel **Esplora soluzioni** e fare clic su **Add** **|** **nuovo elemento**. Selezionare **pagina HTML** (risulterà sotto la sottosezione Web). Denominare il file **default. HTML**. Fai clic su **Aggiungi**.

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-06.png)

9.  L'elenco delle classi / gli oggetti di **Esplora soluzioni** dovrebbe essere simile all'immagine seguente.

    ![Creare l'applicazione di bot](images/AzureLabs-Lab312-07.png)

10. Fare doppio clic sulla **ConversationContext** classe. Questa classe è responsabilità delle variabili utilizzate dal bot per mantenere il contesto della conversazione. I valori di contesto conversazione sono gestiti in un'istanza di questa classe, poiché qualsiasi istanza del **MyBot** classe verrà aggiornata ogni volta che viene ricevuta un'attività. Aggiungere il codice seguente alla classe:

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

11. Fare doppio clic sulla **MyBot** classe. Questa classe ospiterà i gestori di chiamata da qualsiasi attività in ingresso dal cliente. In questa classe si aggiungerà il codice usato per compilare la conversazione tra il bot e il cliente. Come accennato in precedenza, un'istanza di questa classe viene inizializzata ogni volta che viene ricevuta un'attività. Aggiungere il codice seguente alla classe:

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

12. Fare doppio clic sulla **avvio** classe. Questa classe verrà inizializzato il bot. Aggiungere il codice seguente alla classe:

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

13. Aprire il **programma** file di classe e verificare il codice in esso è lo stesso come illustrato di seguito:

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

14. Ricordarsi di salvare le modifiche, a tale scopo, passare a **File** > **Salva tutto**, nella barra degli strumenti nella parte superiore di Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Capitolo 2: creare il servizio Azure Bot

Ora che è stata compilata nel codice per il bot, è necessario pubblicarlo in un'istanza di *Bot per App Web* Service, nel portale di Azure. In questo capitolo illustrerà come creare e configurare il servizio Bot in Azure e quindi pubblica il codice ad esso.

1.  In primo luogo, accedere al portale di Azure (https://portal.azure.com). 

    1. Se non hai già un account Azure, è necessario crearne uno. Se si segue questa esercitazione in una situazione di laboratorio o in aula, porre l'insegnante o uno dei dei supervisori per ulteriori informazioni sulla configurazione del nuovo account.

2.  Una volta connessi, fare clic su **crea una risorsa** nell'angolo in alto a sinistra e cercare *bot per App Web*, fare clic su **invio**.

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  La nuova pagina fornirà una descrizione del *Bot per App Web* servizio. AT nella parte inferiore sinistra della pagina, seleziona la **Create** pulsante, per creare un'associazione con questo servizio.

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  Dopo avere fatto clic su **Create**:

    1. Inserire la posizione desiderata **nome** per questa istanza del servizio.
    2. Selezionare una **sottoscrizione**.
    3. Scegliere una **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).

        > Per altre informazioni sui gruppi di risorse di Azure, [, seguire questo collegamento](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. Determinare il percorso per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione in una situazione ideale sarebbe nell'area in cui l'applicazione viene eseguita. Alcune risorse di Azure sono disponibili solo in determinate aree geografiche.
    5. Selezionare il **piano tariffario** appropriati per l'utente, se questo è il primo tempo nella creazione una *Bot per App Web* servizio, un livello gratuito (denominato F0) deve essere disponibile all'utente
    6. **Nome dell'app** possono solo essere lasciate quello utilizzato per il *nome Bot*. 
    7. Lasciare il *modello di Bot* come **base (C#)**.
    8. *Piano di servizio App/località* doveva essere compilati automaticamente per l'account.
    9. Impostare il **archiviazione di Azure** che si desidera usare per ospitare il tuo Bot. Se non è già, è possibile crearlo qui.
    10. È necessario anche confermare di avere compreso le condizioni applicate a questo servizio.
    11. Fare clic su Crea.
 
        ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-10.png)

5.  Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.

6.  Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio. Verrà visualizzata nella nuova istanza di servizio di Azure. 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  A questo punto è necessario configurare una funzionalità denominata **Direct Line** per consentire all'applicazione client comunicare con questo servizio Bot. Fare clic su **canali**, quindi nella **aggiungere un canale in primo piano** sezione, fare clic sul **canale Direct Line configurare**.

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-14.png)

10. In questa pagina sono disponibili i **chiavi private** che consentirà l'autenticazione con il bot dell'app client. Fare clic sui **mostrare** pulsante e richiedere una copia di una delle chiavi visualizzate, perché sarà necessaria in un secondo momento nel progetto. 

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Capitolo 3: pubblicare il Bot per il servizio Bot per App Web di Azure

Ora che il servizio è pronto, è necessario pubblicare il codice di Bot, creato in precedenza, per il servizio Bot di App Web appena creata.

> [!NOTE] 
> È necessario pubblicare il Bot per il servizio di Azure ogni volta che si apportano modifiche alla soluzione Bot / code.

1.  Tornare alla soluzione Visual Studio creato in precedenza. 
2.  Fare clic sui **MyBot** progetto le **Esplora soluzioni**, quindi fare clic su **Publish**.

    ![Pubblicare il Bot per il servizio Bot per App Web di Azure](images/AzureLabs-Lab312-16.png)

3.  Nel *selezionare una destinazione di pubblicazione* pagina, fare clic su **servizio App**, quindi **seleziona esistente**, infine fare clic su **Crea profilo** (potrebbe essere necessario Fare clic sulla freccia a discesa con i *pubblica* pulsante, se questo non è visibile).

    ![Pubblicare il Bot per il servizio Bot per App Web di Azure](images/AzureLabs-Lab312-17.png)

4. Se non ancora effettuato l'accesso all'account Microsoft, è necessario farlo qui.
5. Nel **Publish** pagina si noterà che è necessario impostare lo stesso **sottoscrizione** usato per il *Bot per App Web* creazione del servizio. Quindi impostare il **View** come **gruppo di risorse** e, nell'elenco a discesa di struttura di cartelle, selezionare il **gruppo di risorse** hanno creato in precedenza. Fare clic su **OK**. 

    ![Pubblicare il Bot per il servizio Bot per App Web di Azure](images/AzureLabs-Lab312-18.png)

6.  Fare clic sulla **pubblica** pulsante e attendere il Bot da pubblicare (potrebbe richiedere alcuni minuti).

    ![Pubblicare il Bot per il servizio Bot per App Web di Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Capitolo 4: configurare il progetto Unity

Di seguito è una tipica configurato per lo sviluppo con realtà mista e di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **New**. 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-20.png)

2.  A questo punto, è necessario specificare un nome di progetto Unity. Inserire **Hololens Bot**. Verificare che il modello di progetto è impostato su **3D**. Impostare il **posizione** a una destinazione appropriata (tenere presente che è preferibile più prossimo a directory radice). Fare quindi clic **Crea progetto**.

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-21.png)

3.  Con Unity open, è opportuno verificare il valore predefinito **Editor di Script** è impostata su **Visual Studio**. Passare a **Modifica > Preferenze** e quindi dalla nuova finestra, passare alla **strumenti esterni**. Change **External Script Editor** al **Visual Studio 2017**. Chiudi il **preferenze** finestra.

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-22.png)

4.  Passare quindi ad **File > Build Settings** e selezionare **Universal Windows Platform**, quindi fare clic sui **commutatore piattaforma** pulsante per applicare la selezione.

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-23.png)

5.  Mentre si trovano ancora nella **File > Build Settings** e assicurarsi che:

    1.  **Dispositivo di destinazione** è impostata su **Hololens**

        > Per le cuffie coinvolgenti, impostare **dispositivo di destinazione** al *qualsiasi dispositivo*.

    2.  **Tipo di compilazione** è impostata su **D3D**

    3.  **SDK** è impostata su **installata più recente**

    4.  **Versione di Visual Studio** è impostata su **installata più recente**

    5.  **Compilare ed eseguire** è impostata su **computer locale**

    6.  Salvare la scena e aggiungerlo alla compilazione. 

        1. Eseguire questa operazione selezionando **aggiungere scene Open**. Verrà visualizzata una finestra di salvataggio.
        
            ![Configurare il progetto Unity](images/AzureLabs-Lab312-24.png)

        2. Creare una nuova cartella per questa operazione e qualsiasi futuro, scena, quindi selezionare il **nuova cartella** pulsante, per creare una nuova cartella, denominarla **scene**.

             ![Configurare il progetto Unity](images/AzureLabs-Lab312-25.png)

        3. Aprire appena creato **scene** cartella e quindi il *nome File*: campo di testo, digitare **BotScene**, quindi fare clic su **Salva**.

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-26.png)

    7. Le restanti impostazioni, nel **Build Settings**, deve essere lasciato come impostazione predefinita per il momento.

6. Nel *Build Settings* finestra, fare clic sul **Player Settings** pulsante, si aprirà il pannello correlato nello spazio in cui il *Inspector* si trova. 

    ![Configurare il progetto Unity](images/AzureLabs-Lab312-27.png)

7. In questo pannello, alcune impostazioni devono essere verificati:

    1. Nel **altre impostazioni** scheda:

        1. **Versione del Runtime di scripting** deve essere **sperimentale (equivalente NET 4.6)**; questa modifica richiede il riavvio dell'Editor.
        2. **Back-end di scripting** deve essere **.NET**
        3. **Livello di compatibilità delle API** deve essere **.NET 4.6**

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-28.png)
      
    2. All'interno di **impostazioni di pubblicazione** nella scheda **funzionalità**, controllare:

        - **InternetClient**
        - **Microfono**

            ![Configurare il progetto Unity](images/AzureLabs-Lab312-29.png)

    3. Più in basso il pannello, nello **XR impostazioni** (disponibile di seguito **impostazioni di pubblicazione**), segni di graduazione **supportato di realtà virtuale**, assicurarsi che il **SDK realtà mista di Windows**  viene aggiunto.

        ![Configurare il progetto Unity](images/AzureLabs-Lab312-30.png)

8.  Nuovamente in *Build Settings* _Unity C#_  progetti non sono più è disattivata; selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Impostazioni di compilazione.
10. Salvare la scena e il progetto (**FILE > Salva scena / FILE > Salva progetto**).


## <a name="chapter-5--camera-setup"></a>Capitolo 5: impostazione della fotocamera

> [!IMPORTANT]
> Se si vuole ignorare la *configurare Unity* componente di questo corso e continuare direttamente nel codice, è possibile scaricare questa app [Package.unitypackage-Azure-SIG-312](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importarlo nel progetto come una [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), quindi continuare dal [capitolo 7](#chapter-7-–-create-the-botobjects-class).

1.  Nel *Pannello di gerarchia*, selezionare la **Main Camera**. 
2.  Una volta selezionata, sarà possibile visualizzare tutti i componenti del **Main Camera** nel *Pannello di controllo*.

    1. Il **oggetto della fotocamera** devono essere denominati **Main Camera** (si noti l'ortografici)
    2. Main Camera **Tag** deve essere impostata su **MainCamera** (si noti l'ortografici)
    3. Assicurarsi che il **posizione trasformare** è impostata su **0, 0, 0**
    4. Impostare **cancellare i flag** al **colore a tinta unita**.
    5. Impostare il **sfondo** colore del componente della fotocamera su **nero, Alpha 0 (codice esadecimale: #00000000)**

    ![il programma di installazione della fotocamera](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Capitolo 6: importazione della libreria Newtonsoft

Che consentono di deserializzano e serializzano oggetti ricevuti e inviati al servizio Bot è necessario scaricare il **Newtonsoft** libreria. Si noterà una [versione compatibile già organizzati con la struttura cartella corretta Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage). 

Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornita con questo corso.

1.  Aggiungere il *.unitypackage* a Unity tramite il **asset** > **Importa pacchetto** > **pacchetto personalizzato** opzione di menu.

    ![Importazione della libreria Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  Nel **Importa pacchetto Unity** scatola viene, assicurarsi che tutto ciò che in (e tra cui) **plug-in** sia selezionata.

    ![Importazione della libreria Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Scegliere il **importazione** pulsante per aggiungere elementi al progetto.

4.  Andare alla **Newtonsoft** cartella sotto **plug-in** nella visualizzazione del progetto e selezionare il plug-in di Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Con il plug-in di Newtonsoft selezionato, assicurarsi che **Any Platform** viene **deselezionata**, quindi verificare che **WSAPlayer** anche **deselezionata**, quindi fare clic su **applica**. Si tratta semplicemente di confermare che i file siano configurati correttamente.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Contrassegnare questi plug-in Configura perché possano essere usati solo nell'Editor di Unity. Sono presenti un set diverso di esse nella cartella WSA che verrà usato dopo che il progetto viene esportato da Unity.

6.  Successivamente, è necessario aprire la **WSA** cartella, all'interno di **Newtonsoft** cartella. Si noterà una copia dello stesso file che appena configurato. Selezionare il file e quindi nella finestra di ispezione, assicurarsi che
    -   **Qualsiasi piattaforma** è **deselezionata** 
    -   **solo** **WSAPlayer** è **selezionata**
    -   **Non elaborare** è **selezionata**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Capitolo 7-creare il BotTag

1.  Creare una nuova **Tag** oggetto chiamato **BotTag**. Selezionare la fotocamera principale nella scena. Fare clic sul menu nel Pannello di controllo a discesa Tag. Fare clic su **aggiungere Tag**.

    ![il programma di installazione della fotocamera](images/AzureLabs-Lab312-32.png)
 
2.  Fare clic sui **+** simbolo. Denominare il nuovo **Tag** come **BotTag**, *Salva*.

    ![il programma di installazione della fotocamera](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **Non li** applicare le **BotTag** alla fotocamera principale. Se accidentalmente si hanno fatto, assicurarsi di modificare la fotocamera principale al tag *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Capitolo 8: creare la classe BotObjects

È il primo script è necessario creare il **BotObjects** (classe), che è una classe vuota creata in modo che una serie di altri oggetti di classe possono essere archiviata nello stesso alfabeto e accessibile da altri script nella scena.

La creazione di questa classe è esclusivamente una scelta dell'architettura, questi oggetti possono invece essere ospitati in script Bot che verrà creato più avanti in questo corso.

Per creare questa classe: 

1.  Fare doppio clic nella *pannello progetto*, quindi **Crea > cartella**. Denominare la cartella **script**. 

    ![Crea cartella scripts.](images/AzureLabs-Lab312-36.png)

2.  Fare doppio clic sulla **script** cartella per aprirla. Quindi all'interno di tale cartella, pulsante destro del mouse e scegliere **Crea > C# Script**. Denominare lo script **BotObjects**. 

3.  Fare doppio clic su nuova **BotObjects** script per aprirlo con **Visual Studio**.

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

6.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-9--create-the-gazeinput-class"></a>Capitolo 9: creare la classe GazeInput

La classe successiva si intende creare è il **GazeInput** classe. Questa classe è responsabile per:

- Creazione di un cursore che rappresenterà il *estasiati* del lettore.
- Rilevamento di oggetti colpiti sguardo del lettore e che contiene un riferimento agli oggetti rilevati.

Per creare questa classe: 

1.  Andare alla **script** cartella creata in precedenza. 
2.  Pulsante destro del mouse all'interno della cartella **Crea > C# Script**. Chiamare lo script **GazeInput**. 
3.  Fare doppio clic su nuova **GazeInput** script per aprirlo con **Visual Studio**.
4.  Inserire la riga seguente a destra in alto del nome della classe:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Quindi aggiungere le variabili seguenti all'interno di **GazeInput** classe sopra il **Start ()** metodo:

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

6.  Codice per un **Start ()** metodo deve essere aggiunti. Questo evento viene chiamato quando si inizializza la classe:

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

7.  Implementare un metodo che crea un'istanza e impostare il cursore sguardo: 

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

8.  Implementare i metodi che consentono di configurare il Raycast dalla fotocamera principale e terrà traccia dell'oggetto con lo stato attivo corrente.

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
 
9.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-10--create-the-bot-class"></a>Capitolo 10: creare la classe di Bot

Lo script si intende creare a questo punto viene chiamato **Bot**. Si tratta della classe di base dell'applicazione, archivia: 

- Le credenziali di Bot per App Web
- Il metodo che raccoglie i comandi vocali utente
- Il metodo necessario per avviare le conversazioni con il Bot per App Web 
- Il metodo necessario per inviare messaggi al tuo Bot di App Web 

Per inviare messaggi al servizio Bot, il **SendMessageToBot()** coroutine creerà un'attività, che è un oggetto riconosciuto dal Bot Framework, come i dati inviati dall'utente. 
 
Per creare questa classe: 

1. Fare doppio clic sulla **script** cartella per aprirla. 
2. Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**. Denominare lo script **Bot**. 
3. Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4. Aggiornare gli spazi dei nomi affinché corrisponda al seguente, in cima il **Bot** classe:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. All'interno di **Bot** classe aggiungere le variabili seguenti:

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
    > Assicurarsi di inserire le **Bot Secret Key** nel **botSecret** variabile. Verrà annotati i **Bot Secret Key** all'inizio di questo corso, in  **[capitolo 2](#chapter-2---create-the-azure-bot-service), passaggio 10**.

7. Codice per un **Awake()** e **Start ()** deve ora essere aggiunto. 

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

8. Aggiungere i due gestori che vengono chiamati dalle librerie di riconoscimento vocale quando inizia e finisce di acquisizione della voce. Il *DictationRecognizer* arresterà automaticamente i suggerimenti degli utenti per l'acquisizione quando l'utente interrompe il modo di parlare.

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

1. Il gestore seguente consente di raccogliere il risultato dell'input vocale dell'utente e chiama le coroutine responsabile dell'invio del messaggio al servizio Web App Bot.

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

10. Le coroutine seguente viene chiamato per iniziare una conversazione con il Bot. Si noterà che al termine della chiamata di conversazione, chiama il **SendMessageToCoroutine()** passando una serie di parametri che imposta l'attività da inviare al servizio Bot come un messaggio vuoto. Questa operazione viene eseguita per richiedere il servizio Bot per avviare la finestra di dialogo.

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

11. Le coroutine seguente viene chiamato per compilare l'attività da inviare al servizio Bot. 

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

12. Le coroutine seguente viene chiamato per richiedere una risposta dopo l'invio di un'attività per il servizio Bot. 

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

13. Quest'ultimo metodo da aggiungere a questa classe, è necessario per visualizzare il messaggio nella scena:

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
    > Si potrebbe comparire un errore interno della Console di Editor di Unity, assenza di **SceneOrganiser** classe. Ignorare questo messaggio, come verrà creata questa classe in un secondo momento nell'esercitazione.

14.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Capitolo 11: creare la classe interazioni

La classe a cui vuole creare a questo punto viene chiamata **interazioni**. Questa classe viene utilizzata per rilevare il HoloLens toccare Input dell'utente. 

Se l'utente tocca mentre si esaminano le *Bot* oggetti nella scena e Bot sono pronto per l'ascolto per gli input vocale, l'oggetto Bot cambierà colore **rosso** e iniziare l'ascolto per gli input vocale. 

Questa classe eredita dal **GazeInput** classe e quindi, è in grado di fare riferimento il **Start ()** metodo e variabili da tale classe, indicato mediante l'utilizzo di **base**. 
 
Per creare questa classe:

1.  Fare doppio clic sulla **script** cartella per aprirla. 
2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**. Denominare lo script **interazioni**. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi e l'ereditarietà delle classi sia lo stesso come illustrato di seguito, nella parte superiore del **interazioni** classe:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  All'interno di **interazioni** classe aggiungere la variabile seguente:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Quindi aggiungere il **Start ()** metodo:

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

7.  Aggiungere il gestore che verrà attivato quando l'utente esegue il gesto tocco davanti alla fotocamera HoloLens

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

8. Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Capitolo 12: creare la classe SceneOrganiser

Viene chiamato l'ultima classe necessaria in questo laboratorio **SceneOrganiser**. Questa classe configurerà la scena a livello di codice, aggiungendo componenti e gli script alla fotocamera principale, e creando gli oggetti appropriati nella scena.
 
Per creare questa classe:

1.  Fare doppio clic sulla **script** cartella per aprirla. 
2.  Pulsante destro del mouse all'interno di **gli script** cartella, fare clic su **Crea > C# Script**. Denominare lo script **SceneOrganiser**. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  All'interno di **SceneOrganiser** classe aggiungere le variabili seguenti:

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

6.  Quindi aggiungere il **Awake()** e **Start ()** metodi:

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

7.  Aggiungere il metodo seguente, responsabile della creazione dell'oggetto Bot nella scena e configurando i parametri e i componenti:

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

7.  Aggiungere il metodo seguente, responsabile della creazione dell'oggetto dell'interfaccia utente nella scena, che rappresenta le risposte provenienti dai Bot:

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

8.  Assicurarsi di salvare le modifiche apportate *Visual Studio* prima di restituire *Unity*.
9.  Nell'Editor di Unity trascinare la **SceneOrganiser** script dalla cartella degli script per la fotocamera principale. Il componente scena Organizer dovrebbe ora apparire sull'oggetto Main Camera, come illustrato nell'immagine seguente.

    ![Creare il servizio Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Capitolo 13-prima della compilazione

Per eseguire un test approfondito dell'applicazione sarà necessario per effettuare il sideload di HoloLens.
Prima di procedere, verificare quanto segue:

-   Tutte le impostazioni indicate nella [ **capitolo 4** ](#Chapter-4-–-Set-up-the-unity-project) siano impostate correttamente. 
-   Lo script **SceneOrganiser** è collegato il **Main Camera** oggetto. 
-   Nel **Bot** classe, assicurarsi di avere inserito il **Bot Secret Key** nel **botSecret** variabile.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Capitolo 14: compilazione e trasferirla in locale per il HoloLens

Tutti gli elementi necessari per la sezione di Unity di questo progetto è ora stato completato, è il momento per la compilazione da Unity.

1.  Passare a **impostazioni di compilazione**, **File > Impostazioni di compilazione...** .
2.  Dal **Build Settings** finestra, fare clic su **compilazione**.

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab312-38.png)

3.  Se non è già, graduazione **Unity C# progetti**.
4.  Fai clic su **Compila**. Unity avvierà una **Esplora File** finestra, in cui è necessario creare e quindi selezionare una cartella per compilare l'app in. Creare ora tale cartella e denominarlo **App**. Quindi con il **App** cartella selezionata, fare clic su **Seleziona cartella**. 
5.  Unity verrà avviata la compilazione del progetto per la **App** cartella. 
6.  Una volta Unity ha terminato predefiniti (potrebbe richiedere alcuni minuti), si aprirà un **Esplora File** finestra in corrispondenza della posizione della compilazione (controllare la barra delle applicazioni, essendo, ma potrebbe non venire visualizzato di sopra di notifica di aggiunta di un nuovo finestra).

## <a name="chapter-15--deploy-to-hololens"></a>Capitolo 15 – distribuire a HoloLens

Per distribuire in HoloLens:

1.  È necessario l'indirizzo IP di HoloLens (per la distribuzione remota), e per assicurarsi di HoloLens è nel **modalità sviluppatore**. A tale scopo, effettuare le seguenti operazioni:

    1. Durante l'uso di HoloLens, aprire il **impostazioni**.
    2. Passare a **rete e Internet > Wi-Fi > Opzioni avanzate**
    3. Si noti il **IPv4** indirizzo.
    4. Successivamente, tornare **le impostazioni**e quindi a **aggiornamento e sicurezza > per gli sviluppatori** 
    5. Attivare la modalità sviluppatore.

2.  Passare alla nuova build Unity (le **App** cartella) e aprire il file di soluzione con **Visual Studio**.
3.  Nel **configurazione della soluzione** selezionate **Debug**.
4.  Nel **piattaforma soluzione**, selezionare **x86**, **computer remoto**. 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Andare alla **dal menu Compila** e fare clic su **Distribuisci soluzione**, trasferire localmente l'applicazione di HoloLens.
6.  L'app deve vengono ora visualizzati nell'elenco delle App installate su di HoloLens, pronta per essere avviata.

    > [!NOTE]
    > Per distribuire visore VR immersivi, impostare il **piattaforma soluzione** al *computer locale*e impostare il **configurazione** a *Debug*, con *x86* come la **piattaforma**. Quindi distribuire in locale del computer, utilizzando il **dal menu Compila**, selezionando *Distribuisci soluzione*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Capitolo 16 utilizzando l'applicazione nella finestra di HoloLens

- Dopo aver avviato l'applicazione, il Bot verrà visualizzato come una sfera davanti è blu.

- Usare la **movimento toccare** mentre sono gazing alla sfera per avviare una conversazione. 
 
- Attesa della conversazione da avviare (l'interfaccia utente verrà visualizzato un messaggio se succede). Dopo aver ricevuto il messaggio introduttivo di Bot, toccare di nuovo su Bot in modo che verrà divengono rosso e iniziare ad ascoltare la voce dell'utente. 

- Dopo aver interrotto la conversazione, l'applicazione invierà il messaggio per il Bot e tempestivamente il cliente si riceverà una risposta che verrà visualizzata nell'interfaccia utente. 

- Ripetere il processo per inviare più messaggi al tuo Bot (è necessario toccare ogni volta che si desidera invia un messaggio).

La conversazione viene illustrato come il Bot di mantenere le informazioni (il nome), fornendo anche informazioni note (ad esempio, gli elementi che sono immagazzinati) allo stesso tempo.

#### <a name="some-questions-to-ask-the-bot"></a>Alcune domande da chiedere al Bot:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>L'applicazione finita Bot per App Web (v4)

Complimenti, è stata compilata un'app per realtà mista che sfrutta il Bot per App Web Azure, Microsoft Bot Framework v4.

![Versione finale del prodotto](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Esercizi bonus

### <a name="exercise-1"></a>Esercizio 1

La struttura di conversazione in questo laboratorio è molto semplice. Usare Microsoft LUIS per fornire il bot le funzionalità di comprensione del linguaggio naturale.

### <a name="exercise-2"></a>Esercizio 2

In questo esempio non include terminare una conversazione e il riavvio di una nuova. Per verificare la funzionalità di Bot completato, provare a implementare la chiusura per la conversazione.
