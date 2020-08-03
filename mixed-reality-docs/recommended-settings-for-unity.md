---
title: Impostazioni consigliate per Unity
description: Unity offre alcuni comportamenti specifici per la realtà mista che possono essere alternate tramite le impostazioni del progetto.
author: troy-ferrell
ms.author: trferrel
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, impostazioni, realtà mista
ms.openlocfilehash: 414e18686926fd8105726fb3811f3eef1d365bd9
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476723"
---
# <a name="recommended-settings-for-unity"></a>Impostazioni consigliate per Unity

Unity offre un set di opzioni predefinite che in genere corrispondono al caso medio per tutte le piattaforme. Unity offre tuttavia alcuni comportamenti specifici per la realtà mista che possono essere alternate tramite le impostazioni del progetto.

## <a name="performant-environment-set-up"></a>Impostazione dell'ambiente di esecuzione

### <a name="low-quality-settings"></a>Impostazioni di bassa qualità

È importante modificare le impostazioni di **qualità di Unity** per l'ambiente in modo **molto basso**. Ciò consentirà di garantire che l'applicazione esegua performantly al framerate appropriato. Questa operazione è estremamente significativa per lo sviluppo di HoloLens. Per lo sviluppo di auricolari immersivi, a seconda delle specifiche del desktop che sfruttano l'esperienza VR, è comunque possibile ottenere un framerate senza i parametri di qualità più bassi.

In Unity 2019 LTS + è possibile impostare il livello di qualità del **progetto modificando**  >  la qualità**delle impostazioni del progetto**  >  **Quality** e impostando il **valore predefinito** facendo clic sulla freccia verso il basso fino al livello di qualità **molto basso** .

### <a name="lighting-settings"></a>Impostazioni di illuminazione

Analogamente alle impostazioni della scena di qualità, è importante impostare impostazioni di illuminazione ottimali per l'applicazione di realtà mista. In Unity, l'impostazione di illuminazione che in genere avrà un maggiore effetto sulle prestazioni sulla scena è l' **illuminazione globale in tempo reale**. Questa opzione può essere disattivata selezionando **Window**  >  **Rendering**  >  **Impostazioni illuminazione**  >  **globale in tempo reale**per il rendering della finestra.

È disponibile un'altra impostazione di illuminazione, un' **illuminazione globale al forno**. Questa impostazione consente di ottenere risultati accattivanti e visivi per gli auricolari immersivi, ma in genere non è applicabile per lo sviluppo di HoloLens. Il **Illumniation globale cotto** viene calcolato solo per GameObject statici che in genere non sono disponibili in scenari HoloLens a causa della natura di un ambiente sconosciuto e mutevole.

Per ulteriori informazioni, leggere l' [illuminazione globale da Unity](https://docs.unity3d.com/Manual/GIIntro.html) . 

>[!NOTE]
> L' **illuminazione globale in tempo reale** è impostata **per ogni scena** e pertanto gli sviluppatori devono salvare questa proprietà per ogni scena Unity nel progetto.

### <a name="single-pass-instancing-rendering-path"></a>Percorso di rendering per istanze Single Pass

Nelle applicazioni di realtà mista la scena viene visualizzata due volte, una per ogni occhio all'utente. Rispetto allo sviluppo 3D tradizionale, questo raddoppia effettivamente la quantità di lavoro che deve essere calcolata. Pertanto, è importante selezionare il percorso di rendering più efficiente in Unity per risparmiare sia sulla CPU che sul tempo GPU. Il rendering con istanza Single Pass ottimizza la pipeline di rendering Unity per le app di realtà miste ed è quindi consigliabile abilitare questa impostazione per impostazione predefinita per ogni progetto.

Per abilitare questa funzionalità nel tuo progetto Unity

1)  Apri **Player XR Settings** (Impostazioni XR riproduttore). A tale scopo, vai a **Edit** (Modifica) > **Project Settings** (Impostazioni progetto) > **Player** (Riproduttore) > **XR Settings** (Impostazioni XR)
2) Scegli **Single Pass Instanced** (Con istanze a singolo passaggio) dal menu a discesa **Stereo Rendering Method** (Metodo di rendering stereo). Deve essere selezionata la casella di controllo **Virtual Reality Supported** (Realtà virtuale supportata)

Per informazioni dettagliate su questo approccio di rendering, vedere gli articoli seguenti di Unity.

- [How to maximize AR and VR performance with advanced stereo rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) (Come ottimizzare le prestazioni di AR e VR con il rendering stereo avanzato)
- [Single Pass Instancing](https://docs.unity3d.com/Manual/SinglePassInstancing.html) (Creazione di istanze a singolo passaggio)

>[!NOTE]
> Un problema comune relativo al rendering con istanze a singolo passaggio si verifica se gli sviluppatori dispongono già di shader personalizzati non scritti per la creazione di istanze. Dopo l'abilitazione di questa funzionalità, gli sviluppatori possono notare che per alcuni GameObject viene eseguito il rendering in un solo occhio. Ciò è dovuto al fatto che gli shader personalizzati associati non hanno le proprietà appropriate per la creazione di istanze.
>
> Per informazioni su come risolvere questo problema, vedi l'articolo di Unity [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) (Rendering stereo a singolo passaggio per HoloLens)

### <a name="enable-depth-buffer-sharing"></a>Abilita condivisione buffer di profondità

Per ottenere una migliore stabilità dell'ologramma dalla percezione dell'utente, è consigliabile abilitare la proprietà **depth buffer sharing** in Unity. Se si attiva questa impostazione, Unity condividerà la mappa di profondità prodotta dall'applicazione con la piattaforma di realtà mista di Windows. La piattaforma sarà quindi in grado di ottimizzare la stabilità degli ologrammi in modo specifico per la scena in cui viene eseguito il rendering dell'applicazione da parte di un frame specifico.

Per abilitare questa funzionalità nel tuo progetto Unity

1) Apri **Player XR Settings** (Impostazioni XR riproduttore). A tale scopo, vai a **Edit** (Modifica) > **Project Settings** (Impostazioni progetto) > **Player** (Riproduttore) > **XR Settings** (Impostazioni XR)
2) Selezionare la casella di controllo **Abilita condivisione buffer di profondità** in **Virtual Reality SDK**  >  espansione di**realtà mista Windows** (casella di controllo**Virtual Reality supported** )

Si consiglia inoltre di selezionare la **profondità a 16 bit** nell'impostazione del **formato Depth** in questo pannello, specialmente per lo sviluppo HoloLens. La selezione di 16 bit rispetto a 24 bit ridurrà in modo significativo i requisiti di larghezza di banda, in quanto sarà necessario spostare o elaborare i dati.

Per ottimizzare la stabilità dell'ologramma, la piattaforma per la realtà mista di Windows si basa sul buffer di profondità, che corrisponde a tutti gli ologrammi sottoposti a rendering sullo schermo. Pertanto, con la condivisione del buffer di profondità in, è importante quando si esegue il rendering del colore, per eseguire anche il rendering della profondità. In Unity, la maggior parte dei materiali opachi o TransparentCutout eseguirà il rendering per impostazione predefinita, ma gli oggetti trasparenti e di testo non eseguiranno in genere il rendering della profondità anche se si tratta di uno shader dipendente

Se si usa il [Toolkit di realtà misto standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md), per eseguire il rendering della profondità per gli oggetti trasparenti:

1) Selezionare il materiale trasparente che usa lo shader standard MRTK e aprire la finestra Editor di controllo
2) Selezionare il pulsante **Correggi ora** nell'avviso di condivisione del buffer di profondità. Questa operazione può essere eseguita anche manualmente impostando la **modalità di rendering** su **personalizzata**; Impostare quindi **mode** su **Transparent** e infine impostare **Depth Write** **su on**

> [!IMPORTANT]
> Gli sviluppatori devono prestare attenzione alla lotta Z quando cambiano questi valori insieme alle impostazioni del piano vicino/lontano della fotocamera. Il combattimento Z si verifica quando due GameObject tentano di eseguire il rendering nello stesso pixel e a causa delle limitazioni della fedeltà del buffer di profondità (ovvero z depth), Unity non è in grado di distinguere l'oggetto che è davanti all'altro. Gli sviluppatori noteranno uno sfarfallio tra due oggetti del gioco mentre *combattono* per lo stesso valore di profondità z. Questo problema può essere risolto passando a un formato di profondità a 24 bit, perché sarà disponibile un intervallo più ampio di valori per ogni oggetto da calcolare per la profondità z dalla fotocamera.
>
> Tuttavia, è consigliabile, in particolare per lo sviluppo di HoloLens, modificare invece i piani vicini e lontani della fotocamera in un intervallo più piccolo e mantenere il formato di profondità a 16 bit. La profondità z è mappata in modo non lineare all'intervallo di valori lungo i piani della fotocamera vicini e lontani. Questo può essere modificato selezionando la *fotocamera principale* nella scena e sotto **controllo**, modificare i valori del **piano di ritaglio vicino & lontano** per ridurne l'intervallo (ad esempio da 1.000 a 100 milioni o altro valore x e così via)

>[!IMPORTANT]
> [Unity non crea un buffer di stencil](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) quando si usa il formato di profondità a 16 bit. Di conseguenza, alcuni effetti dell'interfaccia utente di Unity e altri effetti necessari per gli stencil non funzioneranno a meno che non sia selezionata l'opzione formato di profondità a 24 bit che creerà un [buffer di stencil a 8 bit](https://docs.unity3d.com/Manual/SL-Stencil.html).

### <a name="building-for-il2cpp"></a>Compilazione per IL2CPP

Unity ha deprecato il supporto per il back-end di scripting .NET e pertanto consiglia agli sviluppatori di usare **IL2CPP** per le compilazioni UWP di Visual Studio. Anche se questo offre diversi vantaggi, la creazione della soluzione di Visual Studio da Unity per **IL2CPP** può essere notevolmente più lenta rispetto al vecchio metodo .NET. Pertanto, è consigliabile seguire le procedure consigliate per la compilazione di **IL2CPP** per risparmiare sul tempo di iterazione dello sviluppo.

1) Utilizzare la compilazione incrementale compilando il progetto nella stessa directory ogni volta, riutilizzando i file predefiniti
2) Disabilitare le analisi del software anti-malware per il progetto & cartelle di compilazione
   - Aprire **Virus & Threat Protection** nell'app impostazioni di Windows 10
   - Selezionare **Gestisci impostazioni** in **virus & impostazioni di protezione dalle minacce**
   - Selezionare **Aggiungi o Rimuovi esclusioni** nella sezione **esclusioni**
   - Fare clic su **Aggiungi un'esclusione** e selezionare la cartella contenente il codice del progetto Unity e gli output di compilazione
3) Usare un'unità SSD per la compilazione

Per altre informazioni, vedere [ottimizzazione dei tempi di compilazione per IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) .

> [!NOTE]
> Inoltre, potrebbe essere utile configurare un [server di cache](https://docs.unity3d.com/Manual/CacheServer.html), soprattutto per i progetti Unity con una grande quantità di asset (esclusi i file di script) o con asset/scene in continua evoluzione. All'apertura di un progetto, Unity archivia gli asset validi in un formato della cache interna nel computer di sviluppo. Gli elementi devono essere reimportati e quindi rielaborati in caso di modifica. Questo processo può essere eseguito una volta, salvato in un server di cache e quindi condiviso con altri sviluppatori in modo da risparmiare tempo, evitando a ciascuno sviluppatore di elaborare la reimportazione di nuove modifiche in locale.

## <a name="publishing-properties"></a>Proprietà di pubblicazione

### <a name="holographic-splash-screen"></a>Schermata iniziale olografica

HoloLens dispone di una CPU e GPU di classe mobile, il che significa che le app potrebbero richiedere un po' più tempo per il caricamento. Durante il caricamento dell'app, gli utenti vedranno solo il nero, quindi possono chiedersi cosa sta accadendo. Per rassicurarli durante il caricamento, è possibile aggiungere una schermata iniziale olografica.

Per abilitare o disabilitare la schermata iniziale olografica:

1) Vai alla pagina **modifica**  >  **Impostazioni progetto**  >  **lettore**
2) Fare clic sulla scheda **Windows Store** e aprire la sezione **immagine iniziale** .
3) Applicare l'immagine desiderata sotto la proprietà **olografica >** olografica di Windows.
    - Impostando l'opzione **Mostra schermata iniziale di Unity** sarà abilitata o disabilitata la schermata iniziale di Unity personalizzata. Se non si ha una licenza Pro Unity, viene sempre visualizzata la schermata iniziale di Unity personalizzata.
    - Se viene applicata un' **immagine Splash olografica** , questa viene sempre visualizzata indipendentemente dal fatto che la casella di controllo Mostra schermata iniziale di Unity sia abilitata o disabilitata. Specificare un'immagine Splash olografica personalizzata è disponibile solo per gli sviluppatori che dispongono di una licenza Pro Unity.

|  Mostra schermata iniziale Unity  |  Immagine Splash olografica  |  Comportamento |
|----------|----------|----------|
|  On  |  Nessuno  |  Mostra la schermata iniziale di Unity predefinita per 5 secondi o fino a quando non viene caricata l'app, a seconda del valore più lungo |
|  On  |  Personalizzato  |  Mostra la schermata iniziale personalizzata per 5 secondi o fino al caricamento dell'app, a seconda di quale sia il più lungo. |
|  Off  |  Nessuno  |  Mostra il nero trasparente (Nothing) finché l'app non viene caricata. |
|  Off  |  Personalizzato  |  Mostra la schermata iniziale personalizzata per 5 secondi o fino al caricamento dell'app, a seconda di quale sia il più lungo. |

Per altre informazioni, vedere [la documentazione della schermata iniziale di Unity](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) .

### <a name="tracking-loss"></a>Perdita del tracciamento

Una cuffia a realtà mista dipende dall'ambiente in cui si trova l'ambiente per costruire [sistemi di coordinate con blocco globale](coordinate-systems-in-unity.md), che consentono di mantenere la posizione degli ologrammi. Quando l'auricolare non riesce a trovarsi nel mondo, si dice che l'auricolare ha *perso il rilevamento*. In questi casi, le funzionalità che dipendono da sistemi di coordinate con blocco globale, ad esempio fasi spaziali, ancoraggi spaziali e mapping spaziale, non funzionano.

Se si verifica una perdita di rilevamento, il comportamento predefinito di Unity prevede l'arresto del rendering degli ologrammi, la sospensione del [ciclo di gioco](https://docs.unity3d.com/Manual/ExecutionOrder.html)e la visualizzazione di una notifica di rilevamento perso che segue comodamente lo sguardo degli utenti. Le notifiche personalizzate possono essere fornite anche sotto forma di immagine di perdita del rilevamento. Per le app che dipendono dal rilevamento per l'intera esperienza, è sufficiente consentire a Unity di gestire completamente questa operazione fino a quando il rilevamento non viene recuperato. Gli sviluppatori possono fornire un'immagine personalizzata da visualizzare durante la perdita del rilevamento.

Per personalizzare l'immagine del rilevamento perso:

1) Vai alla pagina **modifica**  >  **Impostazioni progetto**  >  **lettore**
2) Fare clic sulla scheda **Windows Store** e aprire la sezione **immagine iniziale** .
3) Applicare l'immagine desiderata sotto la proprietà **olografica Windows > Tracking Loss** .

#### <a name="opt-out-of-automatic-pause"></a>Rifiutare esplicitamente la sospensione automatica

È possibile che alcune app non richiedano il rilevamento, ad esempio le [app solo](coordinate-systems-in-unity.md) per l'orientamento, ad esempio i visualizzatori video di 360 gradi, oppure che sia necessario continuare l'elaborazione senza interruzioni durante la perdita del rilevamento. In questi casi, le app possono rifiutare esplicitamente la perdita predefinita del comportamento del rilevamento. Gli sviluppatori che scelgono questa operazione sono responsabili di nascondere o disabilitare tutti gli oggetti che non vengono visualizzati correttamente in uno scenario di perdita del rilevamento. Nella maggior parte dei casi, l'unico contenuto che si consiglia di eseguire il rendering in questo caso è il contenuto con blocco del corpo, centrato attorno alla fotocamera principale.

Per rifiutare esplicitamente il comportamento di sospensione automatica:

1) Vai alla pagina **modifica**  >  **Impostazioni progetto**  >  **lettore**
2) Fare clic sulla scheda **Windows Store** e aprire la sezione **immagine iniziale** .
3) Modificare la casella **di controllo > Windows olografico nella casella di controllo Sospendi perdita e Mostra immagine** .

#### <a name="tracking-loss-events"></a>Eventi di perdita di rilevamento

Per definire un comportamento personalizzato quando il rilevamento viene perso, gestire gli [eventi di perdita del rilevamento](tracking-loss-in-unity.md)globale.

### <a name="capabilities"></a>Funzionalità

Per fare in modo che un'app sfrutti i vantaggi di determinate funzionalità, deve dichiarare le funzionalità appropriate nel manifesto. Le dichiarazioni di manifesto possono essere apportate in Unity, in modo che vengano incluse in ogni esportazione successiva del progetto.

È possibile abilitare le funzionalità per un'applicazione di realtà mista:

1) Vai alla pagina **modifica**  >  **Impostazioni progetto**  >  **lettore**
2) Fare clic sulla scheda **Windows Store** , aprire la sezione **impostazioni di pubblicazione** e cercare l'elenco delle **funzionalità**

Le funzionalità applicabili per l'abilitazione delle API di uso comune per le app olografiche sono:
<br>

|  Funzionalità  |  API che richiedono funzionalità |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  WebCam  |  Acquisizione e VideoCapture |
|  PicturesLibrary/VideosLibrary  |  Fotocapture o VideoCapture, rispettivamente (quando si archivia il contenuto acquisito) |
|  Microfono  |  VideoCapture (durante l'acquisizione dell'audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (e per usare Unity Profiler) |

## <a name="see-also"></a>Vedi anche

* [Panoramica dello sviluppo per Unity](unity-development-overview.md)
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
