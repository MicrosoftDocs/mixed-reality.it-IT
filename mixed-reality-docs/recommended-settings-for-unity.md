---
title: Impostazioni consigliate per Unity
description: Unity offre alcuni comportamenti specifici di realtà mista che può essere attivata/disattivata tramite le impostazioni del progetto.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Unity, impostazioni, realtà mista
ms.openlocfilehash: 8afcefb49a860d66a372ebd3d0c4bcdb43038813
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415455"
---
# <a name="recommended-settings-for-unity"></a>Impostazioni consigliate per Unity

Unity offre un set di opzioni predefinite che sono in genere la metà dei casi per tutte le piattaforme. Unity offre tuttavia alcuni comportamenti specifici di realtà mista che può essere attivata/disattivata tramite le impostazioni del progetto.

## <a name="performant-environment-set-up"></a>Configurare l'ambiente ad alte prestazioni

### <a name="low-quality-settings"></a>Impostazioni relative alla qualità bassa

È importante modificare il **le impostazioni di qualità di Unity** per l'ambiente per **molto bassa**. Questo contribuisce a garantire che l'applicazione viene eseguita con efficacia nella frequenza dei fotogrammi appropriato. Ciò è estremamente importante per lo sviluppo di Hololens. Per lo sviluppo in auricolari coinvolgenti, a seconda delle specifiche del desktop di potenziamento dell'esperienza di realtà virtuale, uno ancora possibile ottenere una frequenza senza i parametri di qualità più bassi. 

In Unity 2018 LTS +, è possibile impostare il livello di qualità del progetto:

Sotto **modifica** > **impostazioni del progetto** > **qualità** > impostare il **predefinito** facendo clic sul la freccia rivolta verso il basso per il **molto bassa** a livello di qualità

### <a name="lighting-settings"></a>Impostazioni di illuminazione

Come per le impostazioni di scena Quality, è importante impostare le impostazioni di illuminazione ottimali per l'applicazione di realtà mista. In Unity, è l'impostazione di illuminazione che in genere hanno il maggiore impatto sulle prestazioni su scena **illuminazione globale in tempo reale**. Ciò può essere disattivato selezionando **finestra** > **Rendering** > **impostazioni illuminazione** > **in tempo reale Illuminazione globale**. 

È un'altra impostazione di illuminazione **integrati globale illuminazione**. Questa impostazione può fornire risultati visivamente accattivanti e ad alte prestazioni su auricolari immersive ma in genere non è applicabile per lo sviluppo di HoloLens. **Compresa Illumniation globale** viene calcolata solo per Gameobject statici che non sono generalmente disponibili nelle scene HoloLens a causa della natura di un ambiente sconosciuto e modificabile.

Leggi [illuminazione globale da Unity](https://docs.unity3d.com/Manual/GIIntro.html) per altre informazioni. 

>[!NOTE]
> **Illuminazione globale in tempo reale** è impostata **per ogni scena** e pertanto gli sviluppatori devono salvare questa proprietà per ogni scena Unity nel progetto. 

### <a name="single-pass-instancing-rendering-path"></a>Percorso per il rendering delle istanze solo passaggio

Nelle applicazioni di realtà mista della scena viene eseguito il rendering due volte, una volta per ogni occhio all'utente. Rispetto al tradizionale sviluppo 3D, questo in modo efficace raddoppiare la quantità di lavoro che deve essere calcolata. Di conseguenza, è importante selezionare il percorso per il rendering più efficiente in Unity per salvare entrambi sul tempo di CPU e GPU. Il rendering singola istanza consente di ottimizzare la pipeline di rendering di Unity per le app di realtà mista e pertanto è consigliabile abilitare questa impostazione per impostazione predefinita per ogni progetto. 

Per abilitare questa funzionalità nel progetto Unity
1)  Open **le impostazioni del giocatore XR** (Vai al **modifica** > **impostazioni progetto** > **Player**  >  **XR impostazioni**)
2) Selezionare **singola istanza di passare** dal **Stereo metodo di Rendering** dal menu a discesa (**supportato di realtà virtuale** deve essere selezionata la casella di controllo)

Per altre informazioni con questo approccio per il rendering, vedere gli articoli seguenti da Unity.
- [Come ottimizzare le prestazioni di AR e VR con rendering stereo avanzate](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Creazione di istanze di passaggio singolo](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Si verifica un problema comune relativo all'unico passare istanze per il Rendering se sviluppatori dispongono già di shader personalizzati esistenti non scritti per la creazione di istanze. Dopo aver abilitato questa funzionalità, gli sviluppatori potrebbero notare alcuni Gameobject solo eseguire il rendering in un occhio. Infatti, gli shader personalizzati associati non hanno le proprietà appropriate per la creazione di istanze.
>
> Visualizzare [singolo passare Stereo Rendering per HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) da Unity per la procedura risolvere questo problema

### <a name="enable-depth-buffer-sharing"></a>Abilitare la condivisione del buffer di profondità

Per ottenere una migliore stabilità ologrammi dalla percezione dell'utente, è consigliabile abilitare il **condivisione Buffer profondità** proprietà in Unity. Attivando questo, Unity condivideranno la mappa di profondità generata dall'applicazione con la piattaforma di realtà mista di Windows. La piattaforma sarà quindi in grado di ottimizzare al meglio la stabilità di ologramma in modo specifico per la scena per qualsiasi intervallo specificata dall'applicazione sottoposta a rendering.

Per abilitare questa funzionalità nel progetto Unity
1) Open **le impostazioni del giocatore XR** (Vai al **modifica** > **impostazioni progetto** > **Player**  >  **XR impostazioni**)
2) Selezionare la casella di controllo **abilitare la condivisione di Buffer profondità** sotto **SDK di realtà virtuale** > **realtà mista di Windows** espansione (**virtuale Realtà supportata** deve essere selezionata la casella di controllo)

Inoltre, è consigliabile selezionare **profondità 16 bit** sotto il **profondità formato** impostazione di questo pannello, in particolare per lo sviluppo di Hololens. La selezione di 16 bit rispetto a 24 bit riduce significativamente i requisiti di larghezza di banda saranno necessario meno dati da spostare o elaborare.

Affinché la piattaforma di realtà mista di Windows ottimizzare la stabilità di ologramma, si affidano ai buffer di profondità per essere accurato e far corrispondere tutti vntana sottoposto a rendering sullo schermo. Pertanto, con la condivisione su un buffer di profondità, è importante quando il rendering di colori, anche il rendering di profondità. In Unity, la maggior parte dei materiali opaco o TransparentCutout verranno eseguito il rendering profondità per impostazione predefinita ma trasparenti e oggetti di testo a livello generale non eseguirà il rendering profondità anche se si tratta dello shader dipendente e così via. 

Se si usa lo shader Toolkit realtà mista Standard, eseguire il rendering di profondità per gli oggetti trasparenti:
1) Selezionare il materiale trasparente che utilizza lo shader MRTK Standard e aprire la finestra dell'editor Inspector
2) Impostare **modalità di Rendering** al **Custom** quindi impostare **modalità** per **Transparent** e infine impostare **profondità scrivere**a **su**

>[!NOTE]
> Gli sviluppatori devono prestare attenzione Z-fighting durante la modifica di questi valori, insieme alle impostazioni di piano quasi/lontano della camera. Z-Fighting si verifica quando due gameobject tenta di eseguire il rendering per lo stesso pixel e a causa delle limitazioni di fedeltà del buffer di profondità (ad es. profondità di z), Unity non è possibile discernere quale oggetto viene davanti a altro. Gli sviluppatori si noterà un sfarfallio tra due oggetti giochi man mano che vengono *combattere* per lo stesso valore z e approfondita. Ciò può essere risolto da passa al formato a 24 bit profondità saranno un intervallo più ampio di valori per ogni oggetto per il calcolo al momento la profondità z dalla fotocamera.
>
> Tuttavia, è consigliabile, in particolare per Hololens development, modificare la fotocamera di quasi molto piani e a un intervallo più piccolo invece e mantenendo la profondità di 16 bit formato. La profondità di z non lineare viene eseguito il mapping all'intervallo di valori lungo la fotocamera vicino e lontano piani. Questa può essere modificata selezionando la *Main Camera* nella scena e in **Inspector**, modificare il **piano di taglio più vicino e lontano** valori per ridurre l'intervallo (ad esempio da 1000 m per 100 milioni o altro valore x, ecc.)

### <a name="building-for-il2cpp"></a>Compilazione per IL2CPP

Unity è deprecato il supporto per .NET lo script back-end e quindi consiglia agli sviluppatori di usare **IL2CPP** per la piattaforma UWP visual studio viene compilato. Anche se ciò offre vari vantaggi, creare la tua soluzione di visual studio da Unity per **Il2CPP** può essere più lento rispetto al vecchio metodo .NET in modo significativo. In questo modo, si consiglia vivamente di seguire le procedure consigliate per la compilazione **IL2CPP** per risparmiare sui tempi di iterazione di sviluppo.

1) Compilazione incrementale sfrutta compilando il progetto nella stessa directory ogni volta, riutilizzando i file predefiniti non esiste
2) Disabilita le analisi software anti-malware per il progetto e le cartelle di compilazione
   - Aprire **protezione da Virus e minacce** sotto app delle impostazioni di Windows 10
   - Selezionare **gestire le impostazioni** sotto **le impostazioni di protezione da Virus e minacce**
   - Selezionare **aggiungere o rimuovere le esclusioni** sotto il **esclusioni** sezione
   - Fare clic su **aggiungere un'esclusione** e selezionare la cartella contiene il codice del progetto Unity e compilazione output
3) Usare un'unità SSD per la compilazione

Leggi [ottimizzazione tempi di compilazione per IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) per altre informazioni.

> [!NOTE]
> Inoltre, potrebbe essere utile configurare un [server di cache](https://docs.unity3d.com/Manual/CacheServer.html), soprattutto per i progetti Unity con una grande quantità di asset (esclusi i file di script) o con asset/scene in continua evoluzione. All'apertura di un progetto, Unity archivia gli asset validi in un formato della cache interna nel computer di sviluppo. Gli elementi devono essere reimportati e quindi rielaborati in caso di modifica. Questo processo può essere eseguito una volta, salvato in un server di cache e quindi condiviso con altri sviluppatori in modo da risparmiare tempo, evitando a ciascuno sviluppatore di elaborare la reimportazione di nuove modifiche in locale.

## <a name="publishing-properties"></a>Le opzioni di pubblicazione

### <a name="holographic-splash-screen"></a>Schermata iniziale holographic

HoloLens è una classe di dispositivi mobili CPU e GPU, ovvero l'App potrebbero richiedere un po' più tempo per caricare. Durante il caricamento dell'app, gli utenti visualizzeranno solo in bianco e pertanto, è lecito chiedersi cosa sta succedendo. Per rassicurare li durante il caricamento, che è possibile aggiungere una schermata iniziale holographic.

Per attivare o disattivare la schermata iniziale holographic:
1) Passare a **Edit** > **impostazioni del progetto** > **Player** pagina
2) Fare clic sui **Windows Store** scheda e aprire il **immagine iniziale** sezione
3) Applicare l'immagine desiderata sotto il **Windows Holographic > immagine iniziale Holographic** proprietà.
    - Attivare e disattivare la **Mostra la schermata iniziale Unity** opzione consentiranno di attivare o disabilitare la schermata iniziale personalizzata di Unity. Se non hai una licenza Pro di Unity, Unity con marchio di schermata iniziale verrà sempre visualizzata.
    - Se un **Holographic immagine iniziale** è applicata, verrà sempre visualizzata indipendentemente dal fatto che la casella di controllo Mostra la schermata iniziale Unity è abilitato o disabilitato. Specifica un'immagine iniziale holographic personalizzati è disponibile solo per gli sviluppatori con una licenza Pro di Unity.

|  Mostra la schermata iniziale di Unity  |  Immagine iniziale holographic  |  Comportamento |
|----------|----------|----------|
|  Attivato  |  Nessuno  |  Mostra la schermata iniziale Unity predefinito per 5 secondi o fino a quando non viene caricata l'app, a seconda del valore è più lungo. | 
|  Attivato  |  Personalizzato  |  Mostra la schermata iniziale personalizzata per 5 secondi o fino a quando non viene caricata l'app, a seconda del valore è più lungo. | 
|  Disattivato  |  Nessuno  |  Mostra nero trasparente (nothing) fino a quando non viene caricata l'app. | 
|  Disattivato  |  Personalizzato  |  Mostra la schermata iniziale personalizzata per 5 secondi o fino a quando non viene caricata l'app, a seconda del valore è più lungo. | 

Leggi [documentazione di Unity visualizzata la schermata iniziale](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) per altre informazioni.

### <a name="tracking-loss"></a>Perdita di rilevamento

Dipende visualizzato l'ambiente intorno a esso per costruire un visore VR realtà mista [sistemi di coordinate world-bloccato](coordinate-systems-in-unity.md), che consentono di vntana deve rimanere nella posizione. Quando le cuffie sono in grado di individuare se stessa nel mondo, le cuffie si dice che ha *perso rilevamento*. In questi casi, la funzionalità dipendente da bloccato world sistemi di coordinate, ad esempio spatial fasi, spaziali ancoraggi e mapping spaziale, non funzionano.

Se si verifica una perdita di rilevamento, il comportamento predefinito di Unity è vntana per il rendering di arrestare, sospendere il [ciclo del gioco](http://docs.unity3d.com/Manual/ExecutionOrder.html), e visualizzare un rilevamento perdito notifica che comodamente segue lo sguardo agli utenti. Notifiche personalizzate possono anche essere fornite sotto forma di un rilevamento immagine perdita. Per le app che dipendono dal rilevamento per l'intera esperienza, è sufficiente consentire a Unity gestiscono questa operazione fino a quando il rilevamento viene recuperato. Gli sviluppatori possono specificare un'immagine personalizzata da visualizzare durante la perdita di rilevamento. 

Per personalizzare l'immagine di rilevamento persi:
1) Passare a **Edit** > **impostazioni del progetto** > **Player** pagina
2) Fare clic sui **Windows Store** scheda e aprire il **immagine iniziale** sezione
3) Applicare l'immagine desiderata sotto il **Windows Holographic > rilevamento immagine perdita** proprietà.

#### <a name="opt-out-of-automatic-pause"></a>Rifiutare esplicitamente di pausa automatica

Alcune App potrebbero non richiedere rilevamento (ad esempio [orientamento sola app](coordinate-systems-in-unity.md) , ad esempio visualizzatori video a 360 gradi) o potrebbe essere necessario continuare l'elaborazione senza interruzioni durante la verifica viene perso. In questi casi, le app possono rifiutare esplicitamente la perdita di predefinito di comportamento di rilevamento. Gli sviluppatori che scelgono questo sono responsabili per nascondere/disabilitazione di tutti gli oggetti che non renda correttamente in uno scenario di perdita di rilevamento. Nella maggior parte dei casi, è consigliabile essere eseguire il rendering nel cui caso non sia bloccato al corpo del contenuto, solo il contenuto incentrate sulla fotocamera principale.

Per rifiutare esplicitamente il comportamento di sospensione automatica:
1) Passare a **Edit** > **impostazioni del progetto** > **Player** pagina
2) Fare clic sui **Windows Store** scheda e aprire il **immagine iniziale** sezione
3) Modificare il **Windows Holographic > in pausa la perdita di rilevamento e l'immagine mostra** casella di controllo.

#### <a name="tracking-loss-events"></a>Eventi di perdita di rilevamento

Per definire il comportamento personalizzato quando il rilevamento viene perso, la gestione globale [rilevamento di eventi di perdita](tracking-loss-in-unity.md).

### <a name="capabilities"></a>Funzionalità

Per un'app sfruttare i vantaggi di alcune funzionalità, è necessario dichiarare le funzionalità appropriate nel relativo manifesto. Le dichiarazioni del manifesto possono essere rese Unity in modo che vengono inclusi in ogni esportazione progetto successivo. 

Funzionalità possono essere abilitate per un'applicazione di realtà mista da:
1) Passare a **Edit** > **impostazioni del progetto** > **Player** pagina
2) Fare clic sui **Windows Store** scheda e aprire il **impostazioni di pubblicazione** sezione e cercare il **funzionalità** elenco

Le funzionalità applicabili per abilitare le API di usate comune per le app Holographic sono:
<br>

|  Capability  |  API che richiedono funzionalità |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver | 
|  WebCam  |  PhotoCapture e VideoCapture | 
|  PicturesLibrary o VideosLibrary  |  PhotoCapture o VideoCapture, rispettivamente (quando si archiviano il contenuto acquisito) | 
|  Microfono  |  VideoCapture (durante l'acquisizione audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e usare il Profiler di Unity) | 

## <a name="see-also"></a>Vedere anche
* [Panoramica dello sviluppo per Unity](unity-development-overview.md)
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md)
