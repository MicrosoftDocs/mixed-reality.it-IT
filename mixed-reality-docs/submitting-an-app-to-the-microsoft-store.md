---
title: Invio di un'app al Microsoft Store
description: Questo articolo offre suggerimenti per l'invio di app per realtà mista ai Microsoft Store, tra cui come creare un pacchetto e testare l'app e i suggerimenti per superare la certificazione e contribuire all'individuabilità dell'app nello Store.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: app, UWP, Submit, Submission, filters, Metadata, System Requirements, keywords, certificate, Package, appx, merchandising
ms.openlocfilehash: af8ee89b2cae42fc3abeec072acde20f437eb820
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387745"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Invio di un'app al Microsoft Store

Sia [HoloLens](hololens-hardware-details.md) che il PC Windows 10 che alimentano le [cuffie immersive](immersive-headset-hardware-details.md) eseguono piattaforma UWP (Universal Windows Platform) app. Che tu stia inviando un'app che supporta HoloLens o PC (o entrambi), l'app verrà inviata al Microsoft Store tramite il [centro](https://partner.microsoft.com/dashboard)per i partner.

Se non si dispone già di un account per sviluppatore del centro per i partner, è possibile [iscriversi oggi stesso](https://developer.microsoft.com/store/register).

## <a name="packaging-a-mixed-reality-app"></a>Creazione del pacchetto di un'app per realtà mista

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparare le risorse dell'immagine incluse nel appx

Gli strumenti di compilazione appx sono necessari per creare l'applicazione in un pacchetto appx da inviare allo Store. Sono disponibili altre informazioni sulle [linee guida per le risorse di Tile e icone](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) in MSDN.

| Asset obbligatorio | Scala consigliata | Formato immagine | Dove viene visualizzato questo? | 
|----------|----------|----------|------------------|
| Logo quadrato 71x71 | Any |  PNG | N/D | 
| Logo quadrato 150x150 | 150x150 (100% scala) o 225x225 (150% scala) | PNG | Start pin e tutte le app (se non è specificato 310x310), archiviare i suggerimenti di ricerca, la pagina di presentazione del negozio, l'esplorazione del negozio, la ricerca nel negozio | 
|  Logo 310x150 Wide |  Any  |  PNG  |  N/D | 
|  Logo dello Store |  75x75 (150% di scalabilità)  |  PNG  |  Centro per i partner, app report, Scrivi una recensione, raccolta personale | 
|  Schermata iniziale |  930x450 (150% di scalabilità)  |  PNG  |  utilità di avvio app 2D (Slate) | 

Sono inoltre disponibili alcune risorse consigliate che HoloLens può sfruttare.

| Asset consigliati | Scala consigliata | Dove viene visualizzato questo? | 
|----------|----------|----------|
|  Logo quadrato 310x310 |  310x310 (150% di scalabilità) |  Avvia pin e tutte le app | 

### <a name="live-tile-requirements"></a>Requisiti dei riquadri animati

Il menu Start in HoloLens utilizzerà l'immagine del riquadro quadrato più grande inclusa.

Si noterà che alcune app pubblicate da Microsoft hanno un programma di avvio 3D per la propria applicazione. Gli sviluppatori possono aggiungere un utilità di avvio 3D per la propria app usando [queste istruzioni](implementing-3d-app-launchers.md).

### <a name="specifying-target-and-minimum-version-of-windows"></a>Specifica della destinazione e della versione minima di Windows

Se l'app per la realtà mista include funzionalità specifiche di una determinata versione di Windows, è importante specificare le versioni di destinazione e minima della piattaforma supportate dall'applicazione Windows universale.

**Questa situazione è particolarmente valida per le app destinate agli auricolari immersivi con la [realtà mista di Windows](immersive-headset-hardware-details.md), che richiedono almeno Windows 10 Fall Creators Update (10,0; Compilazione 16299) per il corretto funzionamento.**

Quando si crea un nuovo progetto di Windows universale in Visual Studio, verrà richiesto di impostare la versione di destinazione e la versione minima di Windows. È anche possibile modificare questa impostazione per un progetto esistente nel menu "progetto", quindi "< le proprietà del > del nome dell'app" nella parte inferiore del menu a discesa.

![Impostare le versioni minime e di destinazione della piattaforma in Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
Impostare le versioni minime e di destinazione della piattaforma in Visual Studio

### <a name="specifying-target-device-families"></a>Specifica delle famiglie di dispositivi di destinazione

Le applicazioni di realtà mista di Windows (sia per [HoloLens](hololens-hardware-details.md) che per [auricolari immersivi](immersive-headset-hardware-details.md)) fanno parte del piattaforma UWP (Universal Windows Platform), quindi qualsiasi pacchetto dell'app con una famiglia di dispositivi di [destinazione](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) "Windows. Universal" può essere eseguito in HoloLens o PC Windows 10 con auricolari immersivi. Detto questo, se non si specifica una famiglia di dispositivi di destinazione nel manifesto dell'applicazione, è possibile aprire inavvertitamente l'app fino a dispositivi Windows 10 non intenzionali. Attenersi alla procedura seguente per specificare la famiglia di dispositivi Windows 10 desiderata, quindi [verificare che siano selezionate le famiglie di dispositivi corrette quando si carica il pacchetto dell'app nel centro per i partner da inviare allo Store.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Per impostare questo campo in Visual Studio, fare clic con il pulsante destro del mouse su Package. appxmanifest e selezionare "Visualizza codice" e quindi trovare il campo nome TargetDeviceFamily. Per impostazione predefinita, potrebbe essere simile al seguente:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Se l'app viene creata per **HoloLens**, è possibile assicurarsi che sia installata solo in HoloLens specificando un gruppo di dispositivi di destinazione "Windows. olografico". 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Se l'app viene creata per **auricolari immersivi di Windows**, è possibile verificare che sia installata solo nei PC Windows 10 con Windows 10 Fall Creators Update (necessario per la realtà mista di Windows) specificando un gruppo di dispositivi di destinazione " Windows. desktop "e MinVersion" 10.0.16299.0 ".

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

Infine, se l'app è progettata per l'esecuzione sia in **HoloLens che**in modalità mista di Windows, è possibile verificare che l'app sia resa disponibile solo per queste due famiglie di dispositivi e che ogni destinazione sia la versione minima corretta di Windows inclusa una riga per ogni famiglia di dispositivi di destinazione con la rispettiva MinVersion.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Per altre informazioni sulla destinazione delle famiglie di dispositivi, vedere la [documentazione di TARGETDEVICEFAMILY UWP](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Associare l'app allo Store

Dal menu progetto nella soluzione di Visual Studio scegliere "Archivia > associa app allo Store". In tal caso, è possibile testare gli scenari di acquisto e di notifica nell'app. Quando si associa l'app allo Store, questi valori vengono scaricati nel file manifesto dell'app per il progetto corrente nel computer locale:
* Nome visualizzato del pacchetto
* Nome pacchetto
* ID editore
* Nome visualizzato dell'editore
* Version

Se si sostituisce il file Package. appxmanifest predefinito creando un file con estensione XML personalizzato per il manifesto, non è possibile associare l'app allo Store. Se si tenta di associare un file manifesto personalizzato all'archivio, verrà visualizzato un messaggio di errore.

### <a name="creating-an-upload-package"></a>Creazione di un pacchetto di caricamento

Seguire le linee guida per la creazione [di pacchetti di app di Windows universale per Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

Il passaggio finale della creazione di un pacchetto di caricamento consiste nel convalidare il pacchetto con il [Kit di certificazione applicazioni Windows](#windows-app-certification-kit).

Se si aggiungerà un pacchetto specifico per HoloLens a un prodotto esistente disponibile in altre famiglie di dispositivi Windows 10, sarà anche possibile sapere in che [modo i numeri di versione possono avere un effetto sui pacchetti distribuiti a clienti specifici](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)e [modalità di distribuzione dei pacchetti a diversi sistemi operativi](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx).

Il materiale sussidiario generale è che il pacchetto con il numero di versione più alto applicabile a un dispositivo sarà quello distribuito dallo Store.

Se è presente un pacchetto Windows. Universal e un pacchetto Windows. olografico e il pacchetto Windows. Universal ha un numero di versione superiore, un utente di HoloLens scaricherà il numero di versione superiore del pacchetto Windows. Universal anziché Windows. Olografic pacchetto. Esistono diverse soluzioni a questo problema:
1. Assicurarsi che i pacchetti specifici della piattaforma, ad esempio Windows. olografico, abbiano sempre un numero di versione superiore rispetto ai pacchetti indipendenti dalla piattaforma, ad esempio Windows. Universal
2. Non creare pacchetti di app come Windows. universali se sono presenti pacchetti specifici della piattaforma, bensì creare il pacchetto Windows. Universal per le piattaforme specifiche in cui si vuole che sia disponibile

>[!NOTE]
> È possibile dichiarare un singolo pacchetto da applicare a più famiglie di dispositivi di destinazione

3. Creare un singolo pacchetto Windows. Universal che funziona in tutte le piattaforme. Il supporto per questa operazione non è attualmente eccezionale, quindi le soluzioni precedenti sono consigliate.

## <a name="testing-your-app"></a>Test dell'app

### <a name="windows-app-certification-kit"></a>Kit di certificazione app Windows

Quando si creano i pacchetti dell'app da inviare al centro per i partner tramite Visual Studio, la procedura guidata crea pacchetti dell'applicazione richiede di eseguire il kit di certificazione app Windows per i pacchetti che vengono creati. Per avere un processo di invio uniforme allo Store, è consigliabile verificare che i test del kit di [certificazione app Windows](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) vengano superati con l'app nel computer locale prima di inviarli allo Store. L'esecuzione del kit di certificazione app Windows in un HoloLens remoto non è attualmente supportata.

### <a name="run-on-all-targeted-device-families"></a>Esegui in tutte le famiglie di dispositivi di destinazione

La piattaforma universale di Windows consente di creare una singola applicazione che può essere eseguita in tutte le famiglie di dispositivi Windows 10. Tuttavia, non garantisce che le app di Windows universale funzioneranno solo su tutte le famiglie di dispositivi. Prima di scegliere di rendere disponibile l'app in HoloLens o in qualsiasi altra famiglia di dispositivi di destinazione Windows 10, è importante [testare l'app](testing-your-app-on-hololens.md) in ognuna di queste famiglie di dispositivi per garantire un'esperienza ottimale.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Invio dell'app per la realtà mista allo Store

Se si sta inviando un'app per realtà mista basata su un progetto Unity, vedere prima questo [video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) .

In generale, l'invio di un'app di realtà mista Windows che funziona su HoloLens e/o cuffie immersive è proprio come l'invio di qualsiasi app UWP al Microsoft Store. Dopo aver [creato l'app riservando il nome](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), è necessario seguire l'elenco di [controllo](https://docs.microsoft.com/windows/uwp/publish/app-submissions)per l'invio di UWP.

Una delle prime operazioni da eseguire è [selezionare una categoria e una sottocategoria](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) per l'esperienza di realtà mista. È importante **scegliere la categoria più accurata per l'app** in modo che sia possibile commercializzare l'applicazione nelle categorie di archiviazione corrette e assicurarsi che venga visualizzata usando le query di ricerca pertinenti. L' **inserimento del titolo di VR come gioco non comporterà una migliore esposizione per l'app** e potrebbe impedire che venga visualizzato in categorie più adatte e meno affollate.

Tuttavia, nel processo di invio sono presenti quattro aree principali in cui si desidera effettuare selezioni specifiche per la realtà mista:
1. Nella sezione delle **[dichiarazioni di prodotto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** in [Proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. Nella sezione **[requisiti di sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** in [Proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. Nella sezione relativa alla **[disponibilità della famiglia di dispositivi](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** in [pacchetti](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. In diversi campi della **[pagina di elenco dei negozi](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Dichiarazioni di prodotti di realtà mista

Nella pagina delle **[Proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** del processo di invio dell'app sono disponibili diverse opzioni correlate alla realtà mista nella sezione relativa alle **[dichiarazioni di prodotti](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** .

![Dichiarazioni di prodotti di realtà mista](images/product-declarations-900px.png)<br>
Dichiarazioni di prodotti di realtà mista

Prima di tutto, è opportuno identificare i tipi di dispositivi per cui l'app offre un'esperienza di realtà mista. Ciò garantisce che l'app sia inclusa nelle raccolte di realtà miste Windows nello Store e che sia rilevata per gli utenti che accedono allo Store dopo la connessione di un auricolare immersivo (o quando si Esplora lo Store in HoloLens).

Accanto a "questa esperienza è progettata per la realtà mista di Windows in:"
* Controllare la casella **PC** solo se l'app offre un'esperienza VR quando un headset immersivo è connesso al PC dell'utente. È consigliabile selezionare questa casella di controllo se l'app è progettata esclusivamente per l'esecuzione su un auricolare immersivo o se si tratta di un'app/gioco PC standard che offre una modalità di realtà mista e/o un contenuto bonus quando una cuffia è connessa.
* Controllare la casella **HoloLens** solo se l'app offre un'esperienza olografica quando viene eseguita in HoloLens.
* Controllare **entrambe** le caselle se l'app offre un'esperienza di realtà mista in entrambi i tipi di dispositivi, ad esempio l' [app "Project Island" mista di reality Academy](mixed-reality-250.md) della build 2017.

Se è stato selezionato "PC" in precedenza, è necessario impostare la "configurazione della realtà mista" (livello di attività). Questo vale solo per le esperienze di realtà miste eseguite su PC connessi a auricolari immersivi, in quanto le app di realtà mista in HoloLens sono a livello globale e l'utente non definisce un limite durante l'installazione.
* Scegliere **in** primo luogo se l'app è progettata con l'intenzione che l'utente rimanga in una posizione, ad esempio un gioco in cui ci si trova in un pozzetto di un aeromobile.
* Scegliere **tutte le esperienze** se l'app è progettata con l'intenzione di aggirare l'utente entro il limite definito durante l'installazione. ad esempio, è possibile che si tratta di un gioco in cui si affiancano gli attacchi Dodge.

### <a name="mixed-reality-system-requirements"></a>Requisiti di sistema per la realtà mista

Nella pagina delle **[Proprietà](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** del processo di invio dell'app sono disponibili diverse opzioni correlate alla realtà mista nella sezione **[requisiti di sistema](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** .

![Requisiti di sistema](images/system-reqs-800px.png)<br>
Requisiti di sistema

In questa sezione si identificherà l'hardware minimo (obbligatorio) e l'hardware consigliato (facoltativo) per l'app realtà mista.

**Hardware di input:**

Usare le caselle di controllo per indicare ai potenziali clienti se l'app supporta il **microfono** (per l' [input vocale](voice-input.md)), **[Xbox controller o gamepad](hardware-accessories.md#bluetooth-gamepads)** e/o i **[controller di movimento della realtà mista di Windows](motion-controllers.md)** . Queste informazioni verranno riportate nella pagina dei dettagli del prodotto dell'app nello Store e aiuteranno l'app a essere inclusa nelle raccolte di app/giochi appropriate. ad esempio, è possibile che esista una raccolta per tutti i giochi che supportano i controller di movimento.

Si consiglia di selezionare le caselle di controllo per "hardware minimo" o "hardware consigliato" per i tipi di input. 

Ad esempio: 
* Se il gioco richiede controller di movimento, ma accetta l'input vocale tramite microfono, selezionare la casella di controllo "hardware minimo" accanto a "controller di movimento per la realtà mista di Windows", ma la casella di controllo "hardware consigliato" accanto a "microfono". 
* Se è possibile riprodurre il gioco con un controller Xbox/gamepad o un controller di movimento, è possibile selezionare la casella di controllo "hardware minimo" accanto a "controller Xbox o gamepad" e selezionare la casella di controllo "hardware consigliato" accanto a "movimento realtà mista di Windows". i controller "come controller di movimento offriranno probabilmente un passo avanti nell'esperienza del gamepad.

**Cuffia mista a realtà mista di Windows:**

Che indica se è necessaria una cuffia immersiva per usare l'app o è facoltativa, è essenziale per la soddisfazione e la formazione dei clienti.

Se l'app può essere usata *solo* tramite un auricolare immersivo, selezionare la casella di controllo "hardware minimo" accanto a "Windows Mixed Reality Full-headset". Questa operazione verrà rilevata nella pagina dei dettagli del prodotto dell'app in Store come un avviso sopra il pulsante Purchase, in modo che i clienti non stiano acquistando un'app che funzionerà nel PC come un'app desktop tradizionale.

Se l'app viene eseguita sul desktop come un'app per PC tradizionale, ma offre un'esperienza VR quando è connesso un auricolare immersivo (se il contenuto completo dell'app è disponibile o solo una parte), selezionare la casella di controllo "hardware consigliato" accanto a "realtà mista di Windows auricolare immersivo ". Non verrà visualizzato alcun avviso sopra il pulsante Acquista nella pagina dei dettagli del prodotto dell'app se l'app funziona come un'app desktop tradizionale senza una cuffia a immersione connessa.

**Specifiche del PC:**

Se si vuole che l'app raggiunga il maggior numero possibile di utenti dell'auricolare immersiva di Windows mista, è opportuno definire come [destinazione](understanding-performance-for-mixed-reality.md) le specifiche del PC per i [PC con la realtà mista di Windows con grafica integrata](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Se l'app per la realtà mista è destinata ai requisiti minimi del PC Windows Mixed Reality o richiede una configurazione specifica del PC, ad esempio la GPU dedicata di un PC con una [realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), è necessario indicare con le specifiche del PC rilevanti in colonna "hardware minimo".

Se l'app per la realtà mista è progettata per migliorare le prestazioni o offre grafica a risoluzione superiore, in una particolare configurazione del PC o scheda grafica, è necessario indicare con le specifiche del PC rilevanti nella colonna "hardware consigliato".

Questa opzione si applica solo se l'app per la realtà mista Usa un headset immersivo connesso a un PC. Se l'app per la realtà mista viene eseguita solo su HoloLens, non è necessario indicare le specifiche del PC perché HoloLens ha una sola configurazione hardware.

### <a name="device-family-availability"></a>Disponibilità famiglia di dispositivi

Se [l'app](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) è stata assemblata correttamente in Visual Studio, caricarla nella pagina pacchetti del processo di invio dell'app dovrebbe produrre una tabella che identifichi le famiglie di dispositivi a cui l'app sarà disponibile.

![Tabella di disponibilità della famiglia di dispositivi](images/device-family-table-900px.png)<br>
Tabella di disponibilità della famiglia di dispositivi

Se l'app per la realtà mista funziona con auricolari immersivi, è necessario selezionare almeno "Windows 10 desktop" nella tabella. Se l'app per la realtà mista funziona in HoloLens, è necessario selezionare almeno "Windows 10 olografico". Se l'app è in esecuzione in entrambi i tipi di auricolari per la realtà mista di Windows, ad esempio l' [app "Project Island" di Mixed Reality Academy](mixed-reality-250.md), è necessario selezionare sia "Windows 10 desktop" sia "Windows 10 olografico".

>[!TIP]
>Molti sviluppatori si verificano errori durante il caricamento del pacchetto dell'app correlato a mancate corrispondenze tra il manifesto del pacchetto e le informazioni sull'account dell'editore o dell'app nel centro per i partner. Questi errori possono spesso essere evitati accedendo a Visual Studio con lo stesso account associato all'account per sviluppatore di Windows (quello usato per accedere al centro per i partner). Se si usa lo stesso account, sarà possibile associare l'app alla relativa identità nella Microsoft Store prima di eseguirne il pacchetto.

![Associare l'app al Microsoft Store](images/associate-your-app-700px.png)<br>
Associare l'app al Microsoft Store in Visual Studio

### <a name="store-listing-page"></a>Pagina di inserzione dello Store

Nella pagina di presentazione dello [Store](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) del processo di invio dell'app è possibile aggiungere informazioni utili sull'app per realtà mista.

>[!IMPORTANT]
>Per assicurarsi che l'app sia categorizzata correttamente dallo Store e resa individuabile per i clienti con realtà mista di Windows, è necessario aggiungere **"realtà mista di Windows"** come uno dei "termini di ricerca" per l'app (è possibile trovare i termini di ricerca espandendo i "campi condivisi" sezione).

![Aggiungere la realtà mista di Windows ai termini di ricerca](images/search-terms-800px.png)<br>
Aggiungere "realtà mista di Windows" ai termini di ricerca

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Offerta di una versione di valutazione gratuita per il gioco o l'app

Molti consumer non avranno alcuna esperienza con la realtà virtuale prima di acquistare una cuffia mista a realtà mista di Windows. È possibile che non sappiano cosa aspettarsi da giochi intensi e che non abbiano familiarità con la loro soglia di comfort in esperienze immersive. Molti clienti possono anche provare a usare un auricolare immersivo a realtà mista di Windows nei PC che non sono associati ai PC con la [realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). A causa di queste considerazioni, è consigliabile valutare la possibilità di offrire una [versione di valutazione gratuita](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) per l'app o il gioco in realtà mista a pagamento.

## <a name="see-also"></a>Vedere anche
* [Realtà mista](mixed-reality.md)
* [Cenni preliminari sullo sviluppo](development-overview.md)
* [Visualizzazioni delle app](app-views.md)
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Suggerimenti sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Test dell'app in HoloLens](testing-your-app-on-hololens.md)
* [Linee guida per la compatibilità hardware con la realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
