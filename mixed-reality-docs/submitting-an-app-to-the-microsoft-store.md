---
title: Invio di un'app per i Microsoft Store
description: Questo articolo offre suggerimenti per l'invio alle app di realtà mista di Microsoft Store, incluse le procedure creare un pacchetto e prova le tue app e suggerimenti per la certificazione e facilitano l'individuabilità dell'app nella Store.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: App uwp, inviare, invio, i filtri, metadati, i requisiti di sistema, parole chiave, di questa procedura, certificazione, pacchetto, appx e merchandising
ms.openlocfilehash: 4eb69fbaa22f4864305f09d5e1bf1c1860a0d31f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600863"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Invio di un'app per i Microsoft Store

Entrambe [HoloLens](hololens-hardware-details.md) e il potenziamento di PC Windows 10 le [visore VR immersivi](immersive-headset-hardware-details.md) eseguire le app Universal Windows Platform. Se che si invia un'app che supporta HoloLens o PC (o entrambi), verrà inviare l'app per i Microsoft Store attraverso [Partner Center](https://partner.microsoft.com/dashboard).

Se non si ha già un account di developer Center Partner, è possibile [iscriversi subito](https://developer.microsoft.com/store/register).

## <a name="packaging-a-mixed-reality-app"></a>Creazione del pacchetto di un'app per realtà mista

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparare gli asset delle immagini inclusi di AppX

Esistono diversi asset delle immagini necessari per il pacchetto appx la generazione di strumenti per compilare l'applicazione in un pacchetto appx da inviare alla Store. Per ulteriori informazioni sulle [linee guida per gli asset riquadro e icona](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) su MSDN.

| Asset richiesto | Scale consigliate | Formato di immagine | In cui è visualizzato? | 
|----------|----------|----------|------------------|
| Logo quadrato 71x71 | Qualsiasi |  PNG | N/D | 
| Logo quadrato 150x150 | ovvero scala 100%, 150 x 150 o 225, 225 (150% scala) | PNG | Avviare tutte le App e i pin (se non viene fornito 310x310), esaminare i suggerimenti di ricerca Store, la pagina di inserzione Store, Store, ricerca Store | 
|  Ampia 310 x 150 Logo |  Qualsiasi  |  PNG  |  N/D | 
|  Logo Store |  75 x 75 (150% scala)  |  PNG  |  Centro per i partner, l'App di Report, scrivere una recensione, la libreria | 
|  Schermata iniziale |  930 x 450 (150% scala)  |  PNG  |  Utilità di avvio app 2D (slate) | 

Sono inoltre disponibili alcuni asset consigliato cui HoloLens possono sfruttare.

| Risorse consigliate | Scale consigliate | In cui è visualizzato? | 
|----------|----------|----------|
|  Logo quadrato 310x310 |  310x310 (150% scala) |  I pin di avvio e tutte le app | 

### <a name="live-tile-requirements"></a>Requisiti di riquadro in tempo reale

Nel menu Start in HoloLens userà l'immagine icona quadrata inclusi più grande.

È possibile riscontrare che alcune App pubblicate da Microsoft dispone di un pulsante di visualizzazione 3D per la propria applicazione. Gli sviluppatori possono aggiungere un pulsante di visualizzazione 3D per le app usando [queste istruzioni](implementing-3d-app-launchers.md).

### <a name="specifying-target-and-minimum-version-of-windows"></a>Specifica di destinazione e la versione minima di Windows

Se l'app di realtà mista include funzionalità specifiche di una determinata versione di Windows, è importante specificare le versioni minima della piattaforma supportate dall'applicazione di Windows universali e destinazione.

**Ciò vale soprattutto per le app destinate a [auricolari coinvolgenti di realtà mista di Windows](immersive-headset-hardware-details.md), che richiedono almeno di Windows 10 Fall Creators Update (10.0; Build 16299) per funzionare correttamente.**

Verrà richiesto di impostare la versione minima di Windows e di destinazione quando si crea un nuovo progetto Windows universale in Visual Studio. È anche possibile modificare questa impostazione per un progetto esistente nel menu "Progetto", quindi "del < nome dell'app > proprietà" nella parte inferiore del menu elenco a discesa.

![Set minimo e destinate a versioni di piattaforma in Visual Studio 2017](images/visual-studio-min-version-500px.png)<br>
Set minimo e destinate a versioni di piattaforma in Visual Studio

### <a name="specifying-target-device-families"></a>Specifica di famiglie di dispositivi di destinazione

Le applicazioni di realtà mista di Windows (per entrambi [HoloLens](hololens-hardware-details.md) e [auricolari coinvolgenti](immersive-headset-hardware-details.md)) sono parte della piattaforma Windows universale, pertanto qualsiasi pacchetto dell'app con un [famigliadidispositivididestinazione](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)"Universal" è in grado di eseguire su HoloLens o i PC Windows 10 con auricolari coinvolgente e concreto. Ciò premesso, se non si specifica una famiglia di dispositivi di destinazione nel manifesto dell'app si potrebbe inavvertitamente aprire l'app fino a dispositivi Windows 10 non intenzionali. Attenersi alla procedura seguente per specificare il gruppo di dispositivi Windows 10 desiderato e quindi [verificare che siano selezionate le famiglie di dispositivi corretto quando si carica il pacchetto dell'app nel centro per i Partner per l'invio alla Store.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Per impostare questo campo in Visual Studio, fare clic con il pulsante destro sul package. appxmanifest e scegliere "Visualizza codice", quindi individuare il campo nome TargetDeviceFamily. Per impostazione predefinita, potrebbe essere simile al seguente:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Se l'app viene creato **HoloLens**, quindi è possibile assicurarsi che viene installata solo su HoloLens specificando una famiglia di dispositivi di destinazione di "Windows.Holographic". 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Se l'app viene creato **auricolari coinvolgenti di realtà mista di Windows**, quindi è possibile assicurarsi che viene installata solo nei PC Windows 10 con il Windows 10 Fall Creators Update (necessaria per realtà mista di Windows), specificando una destinazione famiglia di dispositivi di MinVersion di "10.0.16299.0" e "Windows.Desktop".

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

Infine, se l'app è destinata a essere in esecuzione su **HoloLens e realtà mista di Windows auricolari immersive**, è possibile garantire l'app solo vengono resi disponibile per tali famiglie di due dispositivi e contemporaneamente verificare ognuno ha come destinazione i valori corretti versione minima di Windows mediante l'inclusione di una riga per ogni famiglia di dispositivi di destinazione con il rispettivo MinVersion.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Altre informazioni sulla destinazione famiglie di dispositivi, vedere la [documentazione della piattaforma UWP TargetDeviceFamily](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associare la app di Store

Dal menu progetto nella soluzione Visual Studio, scegliere "Store > associare App con il Store". In questo caso, è possibile testare scenari di acquisto e notifica nell'app. Quando si associa l'app di Store, questi valori vengono scaricati i file manifesto dell'app per il progetto corrente nel computer locale:
* Nome visualizzato del pacchetto
* Nome pacchetto
* ID dell'editore
* Nome visualizzato dell'editore
* Versione

Se si sostituisce il file package. appxmanifest predefinito creando un file con estensione XML personalizzato per il manifesto, è possibile associare l'app con il Store. Se si tenta di associare un file manifesto personalizzato con il Store, si verrà visualizzato un messaggio di errore.

### <a name="creating-an-upload-package"></a>Creazione di un pacchetto di caricamento

Attenersi alle linee guida in [creazione di pacchetti Windows Universal App per Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

Il passaggio finale della creazione di un pacchetto di caricamento convalida del pacchetto tramite il [Kit di certificazione App Windows](#windows-app-certification-kit).

Se si procede all'aggiunta un pacchetto in modo specifico per HoloLens a un prodotto esistente è disponibile in altre famiglie di dispositivi Windows 10, è anche consigliabile apprendere [come numeri di versione potrebbero influire sulle quali pacchetti vengano recapitati ai clienti specifici ](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx), e [come i pacchetti vengono distribuiti ai diversi sistemi operativi](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx).

La linea guida generale è che il pacchetto di numero versione più alto che è applicabile a un dispositivo sarà quello distribuito dalla Store.

Se è presente un pacchetto di Universal e un pacchetto Windows.Holographic e il pacchetto di Universal ha un numero di versione superiore, un utente di HoloLens verrà scaricato il pacchetto a Universal numero versione superiore anziché il Windows.Holographic pacchetto. Esistono diverse soluzioni a questo problema:
1. Verificare che i pacchetti specifici della piattaforma, ad esempio Windows.Holographic avere sempre un numero di versione superiore rispetto a pacchetti indipendente dalla piattaforma, ad esempio Universal
2. Non creare un pacchetto App come Universal se si dispone anche di pacchetti specifici della piattaforma - pacchetto invece del pacchetto di Universal per le piattaforme specifiche che si desidera che sia disponibile in

>[!NOTE]
> È possibile dichiarare un singolo pacchetto sia applicabile a più famiglie di dispositivi di destinazione

3. Creare un singolo pacchetto Universal che funziona in tutte le piattaforme. Supporto per l'oggetto non è ottimo momento in modo che le soluzioni precedenti sono consigliate.

## <a name="testing-your-app"></a>Test dell'app

### <a name="windows-app-certification-kit"></a>Kit di certificazione app Windows

Quando si crea pacchetti dell'app da inviare al Partner Center tramite Visual Studio, la procedura guidata Crea pacchetti dell'applicazione chiederà di eseguire i pacchetti che vengono creati il Kit di certificazione App Windows. Per un processo di invio smooth alla Store, è consigliabile verificare che il [Kit di certificazione App Windows verifica](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) passano con l'app nel computer locale prima di inviarle allo Store di. In esecuzione il Kit di certificazione App Windows in un HoloLens remoto non è attualmente supportato.

### <a name="run-on-all-targeted-device-families"></a>Eseguire su tutte le famiglie di dispositivi di destinazione

La piattaforma universale di Windows consente di creare una singola applicazione che viene eseguito in tutte le famiglie di dispositivi Windows 10. Tuttavia, ciò non garantisce che le app Windows universali funzioneranno su tutte le famiglie di dispositivi. Prima di scegliere di rendere disponibile su HoloLens o qualsiasi altro gruppo di dispositivi Windows 10 destinazione l'app, è importante che si [testare l'app](testing-your-app-on-hololens.md) in ognuna di queste famiglie di dispositivi per garantire un'esperienza ottimale.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Invio dell'app di realtà mista per la Store

Se si invia un'app per realtà mista che si basa su un progetto Unity, vedere questo [video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) prima.

In generale, l'invio di una realtà mista di Windows app che funzioni su HoloLens e/o auricolari coinvolgente e concreto è proprio come l'invio di qualsiasi app UWP di Microsoft Store. Dopo aver [creata l'app riservandone il nome](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), è consigliabile seguire il [elenco di controllo per l'invio UWP](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

È una delle prime cose verranno eseguite [selezionare una categoria e sottocategoria](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) per l'esperienza di realtà mista. È importante che si **scegliere la categoria più accurata per la tua app** in modo che possiamo commercializza su applicazione nelle categorie Store a destra e verificare che viene visualizzato utilizzando le query di ricerca rilevanti. **Elencare il titolo della realtà virtuale come un gioco non comporterà una migliore esposizione per l'app,** e può impedire che la visualizzazione in categorie sono adattamento più e meno affollato.

Tuttavia, esistono quattro aree principali nel processo di invio in cui è opportuno effettuare selezioni specifiche realtà miste:
1. Nel **[dichiarazioni prodotto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** sezione sotto [proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. Nel **[requisiti di sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** sezione sotto [proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. Nel **[disponibilità della famiglia di dispositivi](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** sezione sotto [pacchetti](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. In molti il **[pagina di presentazione Store](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** campi.

### <a name="mixed-reality-product-declarations"></a>Dichiarazioni di prodotto di realtà mista

Nel **[delle proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** pagina del processo di invio di app, troverai diverse opzioni relative alla realtà mista nel **[dichiarazioni prodotto](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** sezione.

![Dichiarazioni di prodotto di realtà mista](images/product-declarations-900px.png)<br>
Dichiarazioni di prodotto di realtà mista

In primo luogo, si identificano i tipi di dispositivo per cui l'app offre un'esperienza di realtà mista. Ciò garantisce che l'app sia incluso in raccolte di realtà mista di Windows nella finestra di Store e che viene esposto agli utenti di esplorazione di Store dopo la connessione a un visore VR immersivi (o quando si esplorano le Store su HoloLens).

Accanto a "questa esperienza è progettata per realtà mista di Windows su:"
* Verificare i **PC** casella solo se l'app offre un'esperienza di realtà virtuale quando un visore VR immersivi è connesso al PC dell'utente. È necessario selezionare questa casella se l'app è progettata esclusivamente per l'esecuzione su un visore VR immersivi o se si tratta di una PC gioco/app standard che offre un contenuto di modalità e/o premi di produttività di realtà mista quando è connesso un auricolare.
* Verificare i **HoloLens** casella solo se l'app offre un'esperienza olografica quando viene eseguito su HoloLens.
* Controllare **entrambe** caselle se l'app offre una realtà mista di esperienza in entrambi i tipi di dispositivo, ad esempio le [Academy realtà mista "progetto isola" app](mixed-reality-250.md) dall'evento Build 2017.

Se si seleziona "PC" precedente, è opportuno impostare la configurazione di realtà mista"" (livello di attività). Si applica solo alle esperienze di realtà mista eseguite in PC connesso a immersive auricolari, come le app di realtà mista su HoloLens sono su scala mondiale e l'utente non definisce un limite durante l'installazione.
* Scegli **Seated + permanente** se l'app è stata progettata con l'intenzione che l'utente resta in una posizione (ad esempio sarebbe un gioco in cui sta inserita in un pannello di controllo di un aereo).
* Scegli **tutte le esperienze** se l'app è stata progettata con l'intenzione che l'utente scorre attorno all'interno del limite che potrà definito durante l'installazione (un esempio potrebbe essere un oggetto in gioco si lato-passaggio e Duck Typing scherma attacchi).

### <a name="mixed-reality-system-requirements"></a>Requisiti di sistema di realtà mista

Nel **[delle proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** pagina del processo di invio di app, troverai diverse opzioni relative alla realtà mista nel **[requisiti di sistema](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** sezione.

![Requisiti di sistema](images/system-reqs-800px.png)<br>
Requisiti di sistema

In questa sezione si identificheranno hardware (obbligatorio) minimi e consigliati dell'hardware (facoltativo) per l'app di realtà mista.

**Input hardware:**

Usare le caselle di controllo per indicare i potenziali clienti se l'app supporta **microfono** (per [input vocale](voice-input.md)), **[Xbox controller o su gamepad](hardware-accessories.md#bluetooth-gamepads)**, e/o  **[controller movimento di realtà mista di Windows](motion-controllers.md)**. Queste informazioni verranno visualizzate nella pagina dei dettagli del prodotto dell'app nella finestra di Store e consentirà all'app di ottenere inclusi nelle raccolte di app/gioco appropriato (ad esempio, una raccolta può esistere per tutti i giochi che supportano i controller di movimento).

Essere precise sulla selezione di caselle di controllo "hardware minimo" o "hardware consigliato" per tipi di input. 

Ad esempio:  
* Se il tuo gioco richiede un controller di movimento, ma accetta l'input vocale tramite microfono, selezionare la casella di controllo "hardware minimi" accanto "Controller movimento di realtà mista di Windows", ma la casella di controllo "hardware consigliato" accanto "Microfono." 
* Se il tuo gioco potrà essere riprodotta con entrambi i controller di movimento o controller/gamepad una Xbox, è possibile selezionare la casella di controllo "hardware minimi" accanto "controller Xbox o gamepad" e selezionare la casella di controllo "hardware consigliato" accanto a "il movimento di realtà mista di Windows controller"come controller di movimento offrirà probabilmente un aggiornamento nell'esperienza dal gamepad.

**Visore VR immersivi realtà mista di Windows:**

Che indica se un visore VR immersivi deve usare l'app, oppure è facoltativo, è fondamentale per formazione e la soddisfazione dei clienti.

Se l'app può *solo* utilizzabile tramite un' visore VR immersivi, selezionare la casella di controllo "hardware minimi" accanto a "Windows immersive visore VR realtà mista." Questo verrà visualizzato nella pagina dei dettagli del prodotto dell'app di Store come avviso sopra il pulsante di acquisto in modo che i clienti non ritiene che si acquista un'app che potrà essere utilizzato nel proprio computer, ad esempio un'app desktop tradizionali.

Se l'app viene eseguita nel desktop, ad esempio un'app per PC tradizionali, ma offre un'esperienza di realtà virtuale quando è connesso un visore VR immersivi (se l'intero contenuto dell'app è disponibile o solo una parte), selezionare la casella di controllo "hardware consigliato" accanto "realtà mista di Windows visore VR immersivi." Nessun avviso verrà visualizzato sopra il pulsante di acquisto nella pagina dei dettagli del prodotto dell'app se funzioni dell'applicazione come un'app desktop tradizionali senza un visore VR immersivi connesso.

**Specifiche del PC:**

Se si vuole che l'app per raggiungere il numero di utenti immersive visore VR realtà mista di Windows possibili, è opportuno [destinazione](understanding-performance-for-mixed-reality.md) specifiche per PC [PC di realtà mista di Windows con grafica integrata](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Indica se l'app di realtà mista ha come destinazione i requisiti minimi di PC realtà mista di Windows oppure richiede una configurazione specifica di PC (ad esempio la GPU dedicata di una [PC Windows Mixed Reality Ultra](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), è necessario indicare che con il relativo Specifiche del PC nella colonna "hardware minimi".

Se l'app di realtà mista è progettata per offrire prestazioni migliori o un'offerta di grafica con risoluzione superiore, in una particolare configurazione di PC o una scheda grafica, è necessario indicare che le specifiche del PC pertinenti nella colonna "hardware consigliato".

Ciò vale solo se l'app di realtà mista Usa un visore VR immersivi connesso a un PC. Se l'app di realtà mista può essere eseguito solo su HoloLens, non dovrai indicano le specifiche di PC come HoloLens è solo una configurazione hardware.

### <a name="device-family-availability"></a>Disponibilità famiglia di dispositivi

Se hai [inserito correttamente l'app](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) in Visual Studio, caricarlo nella pagina dei pacchetti del processo di invio dell'app dovrebbe produrre una tabella che identifica le famiglie di dispositivi sarà disponibile per l'app.

![Tabella di disponibilità della famiglia di dispositivi](images/device-family-table-900px.png)<br>
Tabella di disponibilità della famiglia di dispositivi

Se l'app di realtà mista funziona su auricolari coinvolgenti, poi al livello minimo "Windows 10 Desktop" selezionata nella tabella. Se l'app di realtà mista funziona su HoloLens, poi al livello minimo "Windows 10 Holographic" deve essere selezionata. Se l'app viene eseguita su entrambi i tipi visore VR realtà mista di Windows, ad esempio la [Academy realtà mista "progetto isola" app](mixed-reality-250.md), selezionare "Windows 10 Desktop" e "Windows 10 Holographic".

>[!TIP]
>Molti sviluppatori si verificano errori durante il caricamento del pacchetto dell'app, i relativi a mancate corrispondenze tra il manifesto del pacchetto e le informazioni sull'account/autore dell'app nel centro per i Partner. Questi errori spesso possono essere evitati eseguendo l'accesso a Visual Studio con lo stesso account associato all'account per sviluppatori di Windows (quello usato per accedere al Partner Center). Se si usa lo stesso account, sarà possibile associare l'applicazione con la propria identità in di Microsoft Store prima di crearne un pacchetto.

![Associa l'app di Microsoft Store](images/associate-your-app-700px.png)<br>
Associa l'app di Microsoft Store in Visual Studio

### <a name="store-listing-page"></a>Pagina di presentazione di Store

Nel [listato Store](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) elaborare pagina degli invii di cui app, esistono diverse posizioni, è possibile aggiungere informazioni utili sull'app per la realtà mista.

>[!IMPORTANT]
>Per garantire l'app è stata correttamente classificati in base al Store e reso individuabile ai clienti di realtà mista di Windows, è necessario aggiungerli **"Di Windows Mixed Reality"** come uno dei "termini di ricerca" per l'app (è possibile trovare i termini di ricerca espandendo la "Condivisi i campi" sezione).

![Aggiungere la realtà mista di Windows per eseguire una ricerca termini](images/search-terms-800px.png)<br>
Aggiungere "Realtà mista di Windows" per eseguire una ricerca termini

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Offerta versione di valutazione gratuita di gioco o nell'app

Molti utenti saranno limitata a alcuna esperienza con realtà virtuale prima di acquistare un visore VR immersivi di realtà mista di Windows. Si potrebbe non sapere cosa aspettarsi da videogiochi e potrebbero non avere familiarità con i propri soglia comfort nelle esperienze coinvolgenti. Molti clienti è inoltre possono utilizzare un visore VR immersivi realtà mista di Windows nei computer che non sono con badge come [PC realtà mista Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). A causa di queste considerazioni, è fortemente consigliabile offerta un' [versione di valutazione gratuita](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) per l'app di realtà mista a pagamento o di un gioco.

## <a name="see-also"></a>Vedere anche
* [Realtà mista](mixed-reality.md)
* [Cenni preliminari sullo sviluppo](development-overview.md)
* [Viste di App](app-views.md)
* [Ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md)
* [Raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Test dell'app in HoloLens](testing-your-app-on-hololens.md)
* [Realtà mista di Windows minimo PC compatibilità alle linee guida hardware](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
