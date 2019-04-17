---
title: Visualizzazione spectator
description: Visualizzare vntana da un dispositivo esterno come mezzo per illustrare un'esperienza di realtà mista su uno schermo esterno o la registrazione del video di un'esperienza di realtà mista.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Visualizzazione spectator, iPhone, iPad e iOS OpenCV, fotocamera, ARKit, HoloLens, realtà mista, MixedRealityToolkit, demo, record
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602272"
---
# <a name="spectator-view-for-hololens"></a>Visualizzazione spectator per HoloLens

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a>Effettuare il refactoring corrente

> [!NOTE]
>Visualizzazione spectator per HoloLens è sta attivamente eseguendo il refactoring. Questa operazione consente di consolidare l'anteprima e Pro codebase ed estende il supporto per HoloLens 2. 

Per visualizzare l'oggetto corrente dello stato di refactor la visualizzazione Spectator vedere ' funzionalità/spectatorView' rami nel repository MixedRealityToolkit sia MixedRealityToolkit Unity:

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

e

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a>Panoramica

Con i un HoloLens, abbiamo spesso dimenticare che una persona che non è presente è in grado di sperimentare le meraviglie che è possibile. Visualizzazione spectator consente ad altri utenti di vedere sullo schermo 2D ciò che un utente di HoloLens Visualizza nel proprio mondo.
Visualizzazione spectator (anteprima) è veloce e conveniente approccio alla registrazione vntana in HD, sebbene Spectator visualizzazione Pro è concepita per la registrazione di qualità professionale di vntana.

Nella tabella seguente mostra le opzioni e le relative funzionalità. Scegliere l'opzione più adatta alle proprie esigenze di registrazione video:

|                                      | Visualizzazione spectator (anteprima) |              Spectator visualizzare Pro              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Qualità di Hdinsight                         |         HD completo         |        Qualità professionale riprese (come stabilito da DSLR)      |
| Spostamento della videocamera semplice                      |            ✔            |                                             |
| Visualizzazione di terza persona                    |            ✔            |                      ✔                      |
| Possono essere trasmessi alle schermate           |            ✔            |                      ✔                      |
| Portabile                             |            ✔            |                                             |
| Wireless                             |            ✔            |                                             |
| Altri requisiti hardware         |     (iPhone o iPad)    | HoloLens Rig treppiede + DSLR + PC + Unity |
| Investimento hardware                  |           Bassa           |                     Alto                    |
| Multipiattaforma                       |           iOS           |                                             |
| Il visualizzatore può interagire                  |            ✔            |                                             |
| Funzionalità di rete necessaria (UNET scripting) |            ✔            |                      ✔                      |
| Durata dell'esecuzione il programma di installazione               |         Istante         |                     Lento                    |

## <a name="spectator-view-preview"></a>Visualizzazione spectator (anteprima)

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a>Casi di utilizzo

- Le riprese vntana in Hdinsight: Usa la visualizzazione Spectator (anteprima), è possibile registrare un'esperienza di realtà mista tramite un iPhone. Record full HD e applicare l'anti-aliasing ologrammi e persino ombreggiature. È un modo rapido ed economicamente conveniente per acquisire contenuti video di vntana.
- Demo in tempo reale: Esperienze di realtà mista live Stream a un Apple TV direttamente da iPhone o iPad, senza ritardi.
- Condividere l'esperienza con gli utenti Guest: Consentire agli utenti non HoloLens esperienza vntana direttamente dai propri telefoni o Tablet.

### <a name="current-features"></a>Funzionalità correnti

- Auto-discovery per l'aggiunta di telefoni alla sessione di rete.
- Gestione automatica della sessione, in modo che gli utenti vengono aggiunti alla sessione corretta.
- Sincronizzazione spaziale di Vntana, in modo che tutti visualizzino vntana nella stessa posizione esatta.
- supporto per iOS (dispositivi abilitati per ARKit).
- Più utenti guest di iOS.
- La registrazione del video vntana suono ambiente + suono ologramma.
- Condividere foglio in modo che è possibile salvare video, inviarla tramite posta elettronica o condivisione con altre applicazioni di supporti.


>[!NOTE] 
>Il codice di visualizzazione Spectator (anteprima) non può essere usato con il codice versione Spectator visualizzazione Pro. È consigliabile implementarlo in nuovi progetti in cui è necessaria la registrazione video di vntana.

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a>Licenze

- [OpenCV - (licenza BSD 3-clausola)](https://opencv.org/license.html)
- [Unity ARKit - (licenza MIT)](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a>Come impostare la visualizzazione Spectator (anteprima)

### <a name="requirements"></a>Requisiti

- [Plug-in visualizzazione spectator e i file binari necessari OpenCV](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) -informazioni dettagliate su come compilare visualizzazione Spectator Native plug-in sono disponibili sotto. Per i file binari generati sono necessari:

    - opencv_aruco343.dll
    - opencv_calib3d343.dll
    - opencv_core343.dll
    - opencv_features2d343.dll
    - opencv_flann343.dll
    - opencv_imgproc343.dll

    - zlib1.dll
    - SpectatorViewPlugin.dll
- Vista spectator utilizza Unity Networking (UNET) per la relativa individuazione di rete e la sincronizzazione spaziale. Ciò significa che tutte le funzionalità interattive durante l'applicazione deve essere sincronizzato tra i dispositivi.
- Unity 2017.2.1p2 o versione successiva
- Hardware
    - Un HoloLens
    - PC Windows che eseguono Windows 10
    - Dispositivo compatibile ARKit (iPhone 6s e versioni successive / iPad Pro 2016 e versioni successive / iPad 2017 o versione successiva)-che eseguono iOS 11 o versione successiva
    - Computer Mac con xcode 9.2 e versioni successive
- Account sviluppatore Apple gratuito o [a pagamento](https://developer.apple.com/)
- Microsoft Visual Studio 2017

### <a name="building-the-spectator-view-native-plugin"></a>Creazione del plug-in nativi di visualizzazione Spectator

Per generare i file necessari, seguire questa procedura: https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md

### <a name="project-setup"></a>Configurazione progetto

1. Preparare la scena, garantendo che tutti gameobject visibile all'interno della scena sono contenuti in un gameobject radice world.

    ![Radice World](images/SpecViewPhoneWorldRoot2.PNG)

2. Aggiungere il prefab SpectatorView ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) nella scena.
3. Aggiungere il prefab SpectatorViewNetworking ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) nella scena.
4. Selezionare gli elementi gameobject SpectatorViewNetworking e del componente SpectatorViewNetworkingManager, non esiste alcune cose che è possibile collegare i backup. Questo componente eseguirà la ricerca per gli script necessari in fase di esecuzione se sinistra invariati.
    - Marcatore rilevamento HoloLens -> SpectatorView/Hololens/MarkerDetection
    - Marcatore generazione 3D -> SpectatorView/IPhone/SyncMarker/3DMarker

    ![Individuazione di rete SpectatorView](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a>L'app di rete

- Visualizzazione spectator Usa UNET per la rete e gestisce tutte le connessioni client host automaticamente.
- Tutti i dati specifici di app deve essere sincronizzato e implementato dall'utente, usando ad esempio SyncVars, NetworkTransform, NetworkBehavior.
- Per altre informazioni sulle funzionalità di rete di Unity, visitare [Multiplayer e rete](https://docs.unity3d.com/Manual/UNet.html). (Nota: È stato deprecato UNet; il refactoring della codebase Spectator visualizzazione corrente risolverà il problema)

### <a name="building-for-each-platform-hololens-or-ios"></a>Compilazione per ogni piattaforma (HoloLens o iOS)

- Quando si compila per iOS, assicurarsi di che rimuovere il componente GLTF di MRTK poiché questo non è ancora compatibile con questa piattaforma.
- Al livello superiore del prefab SpectatorView è presente un componente denominato 'Strumento di selezione della piattaforma'. Selezionare la piattaforma da compilare per.
    - Se si seleziona 'Hololens' dovrebbe gameobject tutte sotto gli elementi gameobject iPhone nel prefab SpectatorView diventano inattivi e tutti i gameobject sotto 'Hololens' diventi attivo.
    - Questa operazione può richiedere un po' di tempo a seconda della piattaforma che vuoi l'HoloToolkit viene aggiunto o rimosso dal progetto.

    ![Cambio modalità per piattaforma](images/SpecViewPhoneSwitcher.PNG)

- Verificare che si compila tutte le versioni dell'applicazione che usa la stessa istanza di editor di Unity (Unity non Chiudi tra compilazioni non) a causa di un problema non risolto con Unity.

### <a name="running-your-app"></a>Esecuzione dell'app

Dopo aver compilato e distribuito una versione dell'applicazione su iPhone e in HoloLens, dovrebbe essere possibile connetterli.

1. Assicurarsi che entrambi i dispositivi siano nella stessa rete Wi-Fi.
2. Avviare l'applicazione nei dispositivi sia in alcun ordine specifico. Il processo di avvio dell'applicazione con l'iPhone deve attivare la fotocamera di HoloLens per attivare e iniziare lo scatto di foto.
3. Non appena viene avviata l'app iPhone, avrà un aspetto per superfici come pavimenti o tabelle. Quando vengono trovate le superfici, verrà visualizzato un marcatore simile a quello riportato di seguito. Mostra questo marcatore per il HoloLens.

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. Quando viene rilevato il marcatore da di HoloLens dovrebbe scomparire ed entrambi i dispositivi devono essere connesse e sincronizzati a livello spaziale.

### <a name="recording-video"></a>La registrazione di video

1. Per acquisire e salvare un video da iPhone, toccare e tenere premuto la schermata per 1 secondo. Si aprirà il menu di registrazione.
2. Toccare il pulsante rosso record, verrà avviato un conteggio alla rovescia prima di iniziare a registrare lo schermo.
3. Per completare la registrazione tap e tenere premuto la schermata per un altro 1 secondo, quindi toccare il pulsante di arresto.
4. Una volta caricato il video registrato, verrà visualizzato un pulsante Anteprima (pulsante blu), toccare per guardare il video registrato.
5. Aprire il foglio di condivisione e selezionare Salva al rullino della fotocamera.

### <a name="example-scene"></a>Scena di esempio

È disponibili una scena di esempio [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)

### <a name="troubleshooting"></a>Risoluzione dei problemi

**L'Editor di Unity non si connette a una sessione ospitata da un dispositivo HoloLens**

- Potrebbe trattarsi di Windows Firewall.
- Passare a opzioni di Windows Firewall.
- Consenti app o funzionalità attraverso Windows Firewall.
- Per tutte le istanze dell'Editor di Unity nei segni di graduazione di elenco, dominio, privato o pubblico.
- Quindi tornare alle opzioni di Windows Firewall.
- Fare clic su impostazioni avanzate.
- Fare clic su regole in ingresso.
- Tutte le istanze dell'Editor di Unity dovrebbero avere un segno di spunta verde.
- Per tutte le istanze dell'Editor di Unity che non hanno un segno di spunta verde:
    - Fare doppio clic.
    - Nella finestra di dialogo azione selezionare Consenti la connessione.
    - Fare clic su OK.
    - Riavviare l'Editor di Unity.

**In fase di esecuzione la schermata di iPhone afferma "Individuazione Floor..." ma non viene visualizzato un marcatore di AR.**

- L'iPhone è cercano una superficie orizzontale quindi è preferibile che punta alla fotocamera iPhone verso la parte intera o una tabella. Ciò risulta utile ARKit trovare superfici necessari per la sincronizzazione a livello spaziale con HoloLens.

**Fotocamera HoloLens non attiva quando iPhone tenta automaticamente di join.**

- Assicurarsi che sia HoloLens e iPhone sono in esecuzione nella stessa rete Wi-Fi.

**Quando si avvia un'applicazione Spectator visualizzazione in un dispositivo mobile, altri hololens che eseguono altre App Spectator visualizzazione attiva la fotocamera**

- Il componente NewDeviceDiscovery GoTo e impostare la porta di trasmissione sia la chiave di trasmissione su due valori univoci.
- Passare a SpectatorViewDiscovery e modificare il Broadcast chiave e la porta di trasmissione a un altro set di numeri univoci.

**Il HoloLens non si connette con il mac Editor di Unity.**

- Si tratta di un problema noto che potrebbe essere collegato alla versione di Unity. Compilazione per l'iPhone deve comunque di lavoro e connettersi come di consueto.

**La fotocamera di HoloLens attiva ma non è in grado di analizzare il marcatore.**

- Assicurarsi che si compila tutte le versioni dell'applicazione che usa la stessa istanza di Editor di Unity (Unity non Chiudi tra compilazioni non). Si è verificato un errore sconosciuto con Unity.

## <a name="spectator-view-pro"></a>Spectator visualizzare Pro

![Programma di installazione visualizza spectator](images/spectatorview-300px.png)

Usando Spectator visualizzazione Pro prevede quattro componenti:
1. Un'app compilata in modo specifico per attivare la visualizzazione spectator, basato sul [condividere esperienze in realtà mista](shared-experiences-in-mixed-reality.md).
2. Un utente di usura HoloLens usando l'app.
3. Spectator vista fotocamera rig fornendo un video di punto di vista della terza persona.
4. Un PC desktop che eseguono l'app di condividere esperienze e la composizione di vntana in un video di visualizzazione spectator.

![Programma di installazione visualizza Pro spectator](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a>Casi di utilizzo

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


*Visualizzazione spectator è utilizzabile per condividere le tue creazioni holographic, se si tratta di un'immagine fissa, un clip video o una dimostrazione in tempo reale.*


Esistono tre scenari principali che funzionano bene con questa tecnologia:

**1. Acquisizione di foto**<br>
Utilizza questa tecnologia, è possibile acquisire immagini ad alta risoluzione del vntana. Queste immagini possono essere utilizzate per presentare i contenuti degli eventi di marketing, inviare ai potenziali client o persino inviare l'applicazione a Store di Windows. È possibile ottenere decidere quale fotocamera foto da usare per acquisire queste immagini, di conseguenza potrebbe essere preferibile una videocamera DSLR qualità.


![Esempio di acquisizione foto visualizzazione Pro spectator](images/fall-350px.jpg)<br>
*Esempio di acquisizione di foto - facendola apparire il tetto minimo è costituito da lava.*


**2. Acquisizione video**<br>
I video sono la storia migliore indicante meccanismo per la condivisione di un'esperienza app holographic con molti utenti. Visualizzazione spectator consente di scegliere la fotocamera, obiettivo e sui frame che meglio semi come vuoi presenta la tua app. Si inserisce nel controllo della qualità video in base all'hardware video disponibili.

![Esempio di acquisizione video vista Pro spectator](images/spectatorviewvideo.gif)<br>
*Esempio di acquisizione video: la registrazione di un'esperienza di collaborazione di realtà mista.*


**3. Demo in tempo reale**<br>
Visualizzazione spectator è un approccio da preferire per dimostrazioni in tempo reale quando la posizione della camera rimane stabile o controllata. Poiché è possibile utilizzare una videocamera di qualità elevata, si possono inoltre generare immagini di alta qualità destinate a una schermata di big Data. Ciò è adatta le demo live su una schermata, possibilmente ai partecipanti eager in attesa nella riga del loro turno di streaming.

### <a name="comparing-video-capture-techniques"></a>Confronto tra le tecniche di acquisizione video

[Acquisizione di realtà mista](mixed-reality-capture.md) (MRC) fornisce un video composto di ciò che l'utente di HoloLens è visualizzare da una prima persona punto di vista. Visualizzazione spectator produce un video da una prospettiva terza persona, consentendo l'osservatore video verificare l'ambiente con ologrammi e l'utente che portano un dispositivo HoloLens. Poiché è possibile scegliere di fotocamera, viste spectator possono inoltre generare immagini di qualità migliore rispetto alla fotocamera HoloLens predefinita usato per le immagini MRC e una risoluzione superiore. Per questo motivo, visualizzazione spectator meglio è adatto per immagini di app Store di Windows, video, di marketing o per la progettazione di una visualizzazione in tempo reale per un gruppo di destinatari.

![Spectator vista Pro professionale della fotocamera usata nelle presentazioni di intervento di Microsoft](images/spectator-view-professional-red-camera-300px.jpg)<br>
*Spectator vista Pro professionale della fotocamera usata nelle presentazioni di intervento di Microsoft*


Visualizzazione spectator è stata una parte essenziale del modo in cui Microsoft HoloLens ha presentato esperienze al pubblico dall'inizio quando il prodotto è stato annunciato in gennaio 2015. L'installazione professionale utilizzato era impegnativi e un tag di prezzo costosa per ad esso associati. Ad esempio, la fotocamera Usa un segnale genlock per garantire tempistiche precise che coordina con il sistema di rilevamento di HoloLens. In questa configurazione, lo spostamento della fotocamera visualizzazione spectator era possibile mantenendo vntana stabile per la corrispondenza l'esperienza di un utente che sta visualizzando l'esperienza direttamente in HoloLens.

La versione open source di visualizzazione spectator controbilancia la possibilità di spostare il rig di fotocamera per ridurre significativamente il costo dell'impostazione globale. Questo progetto usa una fotocamera esterna rigidamente e a un HoloLens per rendere le immagini ad alta definizione e i video del progetto Unity holographic. **Durante le dimostrazioni in tempo reale, la fotocamera deve rimanere in una posizione fissa.** Lo spostamento della fotocamera può causare instabilità ologrammi o gli orientamenti. Questo avviene perché i tempi del frame video e il rendering di vntana su PC può non essere sincronizzate con precisione. Pertanto, mantenere costante la fotocamera o la limitazione di spostamento verrà generato un risultato più vicino di ciò che è possibile visualizzare la persona che portano un HoloLens.

Per rendere l'app è pronta per la visualizzazione spectator, è necessario creare un [condiviso esperienza](holograms-240.md) app e verificare che l'app può essere eseguita su HoloLens nonché a desktop nell'editor di Unity. La versione dell'app desktop sarà presenti componenti aggiuntivi compilati in tale composita video feed con il vntana sottoposto a rendering.

## <a name="how-to-set-up-spectator-view-pro"></a>Come configurare Pro visualizzazione Spectator 

### <a name="requirements"></a>Requisiti

![Rig Pro visualizzazione spectator](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a>Elenco degli acquisti di hardware

Di seguito è riportato un elenco consigliato dell'hardware, ma è possibile sperimentare troppo altre unità compatibile. 

|Componente hardware                                                                     |Consiglio               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|Una configurazione del PC che funziona per lo sviluppo holographic con l'emulatore di HoloLens  |                              | 
|Fotocamera con HDMI out o di acquisizione di foto SDK                                             | Foto e acquisizione video, è stato testato il [Canon EOS 5D Mark III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) fotocamera. Per la demo in tempo reale, è stato testato il [Blackmagic progettazione produzione fotocamera 4K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k).<br><br>Si noti che nessuna videocamera con HDMI out (ad esempio GoPro) dovrebbe funzionare correttamente. Molti dei nostri video utilizzano le [lente II USM Ultra-Wide angolo fisso, EF Canon 14mm f/2.8 L](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), ma è consigliabile scegliere un obiettivo della fotocamera che soddisfa le proprie esigenze. | 
|Acquisizione di carta del PC ottenere i frame di colore da una fotocamera per calibrare le rig e visualizzare in anteprima la scena composita |  È stato testato il [Blackmagic progettazione intensità Pro 4K scheda di acquisizione](https://www.amazon.com/dp/B00U3QNP7Q). | 
|Cavi                                                                                 |  [HDMI a HDMI Mini](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) per collegare la fotocamera per la scheda di acquisizione. Verificare che si acquista un fattore di forma HDMI adatto alla fotocamera. (GoPro, ad esempio, gli output tramite [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)<br><br>[Cavo HDMI](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) per la visualizzazione feed su un monitor di anteprima o la televisione composita | 
|Lavorare tra parentesi quadre aluminum per la connessione di HoloLens alla fotocamera. | [Tra parentesi quadre Aluminum](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|3D stampato adapter a cui connettersi il montaggio di HoloLens hotshoe la fotocamera.| [Scheda Stampa 3D](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|Fastener Hotshoe per montare l'adapter hotshoe                                       |  [Hotshoe Fastener](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|Strumenti, i BOLT e dadi vengono formattati diversi                                                |  [1/4-20" dadi](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[1/4-20 "x 3 o 4" BOLT](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[Driver di dado 7/16](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[T15 Torx](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[T7 Torx](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a>Componenti software

1. Software scaricato dal [progetto GitHub per la visualizzazione spectator](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView).
2. [Scheda di acquisizione Blackmagic SDK](https://www.blackmagicdesign.com/support). \
 Ricerca Desktop Video SDK per sviluppatori in "Download più recenti".
3. [Runtime Video Desktop Blackmagic](https://www.blackmagicdesign.com/support). \
 Ricerca di aggiornamento Software Video del Desktop in "Download più recenti". \
 Verificare la versione del SDK le corrispondenze di numeri di versione.
4. [3.1 OpenCV](https://opencv.org/releases.html) per calibrazione o acquisizione video senza la scheda di acquisizione Blackmagic.
5. [Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (Optional).\
 Se si usa una videocamera Canon e avere accesso al SDK Canon, è possibile collegamento la fotocamera sul proprio PC da eseguire immagini con risoluzione superiore.
6. Unity per lo sviluppo di app holographic. \
 Versione supportata è reperibile nel progetto software Open Source.
7. Visual Studio 2015 con gli aggiornamenti più recenti.

### <a name="building-your-own-spectator-view-pro-camera"></a>Compilazione di fotocamera Spectator visualizzazione Pro

**SI NOTI CHE &AMP; DICHIARAZIONE DI NON RESPONSABILITÀ:** Quando si apportano modifiche all'hardware di HoloLens (inclusi, senza limitazioni, impostazione di HoloLens per "visualizzazione spectator") base precauzioni di sicurezza dovrebbero sempre essere esaminate. Leggere tutte le istruzioni e i manuali prima di apportare alcuna modifica. È necessario seguire tutte le istruzioni e usare strumenti come indicato. Si potrebbe acquistati o concesso in licenza di HoloLens con una garanzia limitata o non rilascia alcuna garanzia. Leggere le applicabili [contratto di licenza di HoloLens o condizioni d'uso e la vendita](https://www.microsoft.com/hololens/support/warranty) per comprendere le opzioni di garanzia.

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a>Rig Assembly

![Rig Spectator visualizzazione Pro assemblato con HoloLens e DSLR fotocamera.](images/assembly.gif)<br>
*Assemblato rig Spectator visualizzazione Pro con HoloLens e DSLR fotocamera*


* Per rimuovere l'archetto di HoloLens, utilizzare un cacciavite T7. Quando le viti sono separate, scrivere tali moduli con un allegati da altro lato.
* Rimuovi il limite di vite all'interno parte anteriore dell'hypervisor di HoloLens con un piccolo cacciavite flat head.
* Utilizzare un cacciavite T15 per rimuovere i BOLT torx piccolo da parentesi HoloLens da rimuovere l'oggetto e gli allegati a forma di Hook.
* Posizionare il HoloLens in parentesi, incolli foro esposto all'interno di e le risorse con l'estrusione sul pannello anteriore della parentesi. Arms degli HoloLens deve essere mantenuto posto per i perni nella parte inferiore della parentesi.
* Ricollegare l'oggetto e gli allegati a forma di Hook per la protezione per la parentesi quadra di HoloLens.
* Collegare il fastener hotshoe a hotshoe della fotocamera.
* Collegare la scheda di montaggio per i fastener hotshoe.
* Ruota l'adapter in modo che il side ravvicinate è rivolta verso l'alto e parallelo per l'obiettivo.
* Proteggere l'adapter posto con un dado 1/4" con il driver di dado 7/16.
* Posizionare la parentesi quadra contro l'adapter in modo davanti 8informazioni degli HoloLens sono più vicino possibile all'inizio della sezione della camera.
* Associa la parentesi quadra 1/4 di 4" vera e propria usando il driver di dado 7/16.

#### <a name="pc-setup"></a>Programma di installazione di PC
* Installare il software nella sezione componenti software.
* Aggiungere la scheda di acquisizione in uno slot PCIe aperto sulla scheda madre.
* Collegare un cavo HDMI dalla fotocamera nello slot HDMI outer (HDMI aggiuntivo) della scheda di acquisizione.
* Collegare un cavo HDMI dallo slot HDMI center (HDMI-Out) della scheda di acquisizione per un monitoraggio di anteprima facoltativo.

#### <a name="camera-setup"></a>il programma di installazione della fotocamera
* Cambiare la fotocamera per la modalità Video restituisce come output la risoluzione di 1920 x 1080 completo piuttosto che un ritagliato risoluzione foto 3:4.
* Trovare le impostazioni della fotocamera HDMI e abilitare **Mirroring** oppure **doppio Monitor**.
* Impostare la risoluzione di output su 1080 P.
* Disattivare **Live visualizzazione su schermo** quindi sovrappone qualsiasi schermata non appare nella composita feed.
* Attivare la fotocamera **vista Live**.
* Se si usa la **SDK Canon** e si desidera utilizzare un'unità flash, disabilitare **girare LV invisibile all'utente**.
* Collegare un cavo HDMI dalla fotocamera nello slot HDMI outer (HDMI aggiuntivo) della scheda di acquisizione.

#### <a name="calibration"></a>Calibrazione

Dopo aver configurato il rig di visualizzazione spectator, è necessario calibrare per ottenere l'offset di posizione e della rotazione della fotocamera per la HoloLens.
* Aprire la soluzione di Visual Studio di calibrazione sotto Calibration\Calibration.sln.
* In questa soluzione, si noterà il dependencies.props file che consente di creare macro per i percorsi inc delle origini 3rd party.
* Aggiornare il file con il percorso di installazione OpenCV 3.1, il SDK Blackmagic e SDK Canon (se applicabile)

![Snapshot di percorsi delle dipendenze in Visual Studio](images/dependencies-600px.png)<br>
*Snapshot di percorsi delle dipendenze in Visual Studio*


* Stampare il modello di calibrazione Calibration\CalibrationPatterns\2_66_grid_FULL.png su una superficie piana e rigida.
* Collegare il HoloLens al computer tramite USB.
* Aggiornare le definizioni per il preprocessore **HOLOLENS_USER** e **HOLOLENS_PW** nelle **stdafx. h** con le credenziali del portale del dispositivo degli HoloLens.
* Collegare la fotocamera per la scheda di acquisizione su HDMI e attivarlo.
* Eseguire la soluzione di calibrazione.
* Spostare il motivo a scacchi attorno alla vista simile al seguente:

![Si calibrano il rig Spectator visualizzazione Pro](images/calibration.gif)<br>
*Si calibrano il rig Spectator visualizzazione Pro*


* Un'immagine vengono intraprese automaticamente quando viene visualizzato di una scacchiera. Cercare la luce bianca su 8informazioni degli HoloLens prima dell'avanzamento per la successiva posa.
* Al termine, premere **invio** con l'app di calibrazione lo stato attivo per creare un **CalibrationData.txt** file.
* Questo file verrà salvato **Documents\CalibrationFiles\CalibrationData.txt**
* Esaminare questo file per vedere se i dati di calibrazione sono accurati:
   * **RMS DSLR** dovrebbe essere vicino allo 0.
   * **HoloLens RMS** dovrebbe essere vicino allo 0.
   * **RMS stereo** potrebbero essere 20-50, questa situazione è accettabile perché il campo visivo tra le due telecamere potrebbe essere diverso.
   * **Traduzione** la distanza dalla fotocamera degli HoloLens collegati obiettivo. Si tratta in metri.
   * **Rotazione** dovrebbe essere vicino a identità.
   * **DSLR_fov** valore y deve essere vicino al campo di visualizzazione verticale previsto da focale dei filtri e qualsiasi fattore di taglio corpo della fotocamera.
* Se uno qualsiasi dei valori specificati sopra sembrano non avere senso, ricalibrare.
* Copiare questo file per il **asset** directory nel progetto Unity.

### <a name="compositor"></a>Compositor

Nel filtro compositor è un'estensione di Unity che viene eseguito come una finestra dell'editor di Unity. A tale scopo, la soluzione di Visual Studio Compositor deve prima essere compilato.
* Aprire la soluzione di Visual Studio Compositor sotto Compositor\Compositor.sln
* Aggiornare dependencies.props con gli stessi criteri usati dalla soluzione di calibrazione precedente. Se è stata seguita la procedura di calibrazione, questo file sarà già aggiornato.
* Compilare l'intera soluzione come versione e l'architettura corrispondente architettura della versione di Unity. In caso di dubbio, compilazione sia x86 sia x64.
* Se è stata compilata la soluzione per x64, anche compilare il progetto SpatialPerceptionHelper come x86 poiché verrà eseguito di HoloLens.
* Chiudi Unity è in esecuzione l'applicazione. Unity deve essere riavviati e se le DLL vengono modificate in fase di esecuzione.
* Eseguire Compositor\CopyDLL.cmd per copiare le DLL compilate da questa soluzione del progetto Unity. Questo script copierà i file DLL per il progetto di esempio inclusi. Dopo aver configurato il proprio progetto, è possibile eseguire CopyDLL con un argomento della riga di comando che punta alla directory Assets del progetto per copiare anche.
* Avviare l'app di esempio Unity.

### <a name="unity-app"></a>App Unity

Viene eseguito nel filtro compositor come una finestra nell'Editor di Unity. Il progetto di esempio incluso include tutto ciò è configurato per funzionare con la visualizzazione spectator una sola volta nel filtro compositor che DLL vengono copiate.

Visualizzazione spectator richiede che l'applicazione deve essere eseguito come un [condiviso esperienza](holograms-240.md). Ciò significa che è necessario essere collegati alla rete per aggiornare l'app in esecuzione in Unity troppo modifiche di stato dell'applicazione che si verificano nel HoloLens.

Se a partire da un nuovo progetto Unity, è necessario innanzitutto eseguire un programma di installazione:
* Copia **Assets/componenti aggiuntivi/HolographicCameraRig** dal progetto di esempio al progetto.
* Aggiungere il più recente MixedRealityToolkit al progetto, inclusi **Sharing**, **csc. rsp**, **gmcs.rsp**, e **smcs.rsp**.
* Aggiungere il **CalibrationData.txt** file alla directory di asset.

![Snapshot di directory di Unity gli asset](images/files-400px.png)

* Aggiungere il **HolographicCameraRig\Prefabs\SpectatorViewManager** prefab alla scena e compilare i campi:
   * **HolographicCameraManager** deve essere popolato con il prefab HolographicCameraManager dalla directory HolographicCameraRig prefab.
   * **Ancoraggio** deve essere popolato con il prefab ancoraggio dalla directory HolographicCameraRig prefab.
   * **Condivisione** deve essere popolato con il prefab condivisione dal MixedRealityToolkit.
   * Nota: Se uno qualsiasi di questi prefabs esiste già nella gerarchia del progetto, verrà utilizzato il prefabs esistente anziché quelli riportati.
   * **Spectator visualizzazione IP** deve essere l'indirizzo IP di HoloLens collegati a rig di visualizzazione spectator.
   * **IP del servizio di condivisione** deve essere l'indirizzo IP del computer che eseguono il MixedRealityToolkit SharingService.
   * Facoltativo: Se si dispone di più spectator visualizzare rig collegato al PC più del **IP di Computer locali** deve essere impostato con il PC il rig di visualizzazione spectator comunicherà con.

![Proprietà spectator visualizzazione Gestione in Unity](images/spectatorviewmanager-500px.png)

* Avviare il MixedRealityToolkit **servizio di condivisione**
* Compilare e distribuire l'app UWP D3D per il HoloLens collegata al rig di visualizzazione spectator.
* Distribuire l'app per tutti gli altri dispositivi HoloLens nell'esperienza.
* Controllare la **eseguito In Background** casella di controllo **Modifica/progetto impostazioni/player**.

![Eseguire nell'impostazione in background in Unity](images/run-in-bg-400px.png)
* Avviare la finestra del filtro compositor sotto **Spectator visualizzazione/filtro Compositor**

![Visualizzazione filtro Compositor per Vista spectator in Unity](images/compositor-500px.png)

* In questa finestra consente di:
   * Avviare la registrazione di video
   * Scatta una foto
   * Modificare l'opacità ologrammi
   * Modificare l'offset di frame (che consente di regolare il timestamp di colore per rappresentare la latenza di scheda di acquisizione)
   * Aprire la directory che vengono salvate le acquisizioni
   * Richiedere i dati di mapping spaziale tra la camera e visualizzazione spectator (se è presente un SpatialMappingManager nel progetto)
   * Visualizzare la scena visualizzazione composta così come colore, ologrammi e canale alfa singolarmente.
   * Abilitare la fotocamera.
   * Premere Riproduci in Unity.
   * Quando viene spostata la fotocamera, vntana in Unity dovrebbe essere dove si trovano nel mondo reale relativo al colore fotocamera del feed.

## <a name="see-also"></a>Vedere anche

* [Acquisizione di realtà mista](mixed-reality-capture.md) 
* [Mista acquisizione realtà per gli sviluppatori](mixed-reality-capture-for-developers.md)
* [Condividere esperienze in realtà mista](shared-experiences-in-mixed-reality.md)
* [Codice di visualizzazione (anteprima) spectator su GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [Codice nativo spectator di visualizzazione (anteprima) in GitHub](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [Codice di visualizzazione Pro spectator su GitHub](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
