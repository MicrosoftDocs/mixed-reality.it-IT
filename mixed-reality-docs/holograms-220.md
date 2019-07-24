---
title: MR Spatial 220-audio spaziale
description: Seguire questa procedura dettagliata di codifica usando Unity, Visual Studio e HoloLens per informazioni dettagliate sui concetti relativi ai suoni spaziali.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, esercitazione, spazio audio
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526959"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR Spatial 220: Audio spaziale

Il [suono spaziale](spatial-sound.md) respira la vita negli ologrammi e offre loro la presenza nel nostro mondo. Gli ologrammi sono costituiti da luci e suoni e, se si perde la visione degli ologrammi, il suono spaziale può aiutarti a trovarli. Il suono spaziale non è analogo a quello tipico che è possibile sentire sulla radio, è un suono posizionato nello spazio 3D. Con il suono spaziale è possibile far sembrare gli ologrammi come se fossero dietro di te, accanto a te o persino in testa! In questo corso verrà:

* Configurare l'ambiente di sviluppo per l'utilizzo di audio spaziale Microsoft.
* Usare il suono spaziale per migliorare le interazioni.
* Utilizzare il suono spaziale insieme al mapping spaziale.
* Comprendere le procedure consigliate per la progettazione e la combinazione di suoni.
* Usare il suono per migliorare gli effetti speciali e coinvolgere l'utente nel mondo della realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>MR Spatial 220: Audio spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).
* Alcune funzionalità C# di programmazione di base.
* Sono state completate le nozioni di [base 101](holograms-101.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare i [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) richiesti dal progetto. Richiede Unity 2017,2 o versione successiva.
  * Se è ancora necessario il supporto per Unity 5,6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Questa versione potrebbe non essere più aggiornata.
  * Se è ancora necessario il supporto per Unity 5,5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Questa versione potrebbe non essere più aggiornata.
  * Se è ancora necessario il supporto per Unity 5,4, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Questa versione potrebbe non essere più aggiornata.
* Annullare l'archiviazione dei file sul desktop o in un'altra posizione facile da raggiungere.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Errori e note

* "Enable Just My Code" deve essere disabilitato (deselezionato) in Visual Studio in strumenti-Opzioni >-> debug per raggiungere i punti di interruzione nel codice.

## <a name="chapter-1---unity-setup"></a>Capitolo 1-installazione di Unity

### <a name="objectives"></a>Obiettivi

* Modificare la configurazione audio di Unity per l'uso del suono Microsoft Spatial.
* Aggiungere un suono 3D a un oggetto in Unity.

### <a name="instructions"></a>Istruzioni

* Avvia Unity.
* Selezionare **Apri**.
* Passare al desktop e trovare la cartella precedentemente non archiviata.
* Fare clic sulla cartella **Starting\Decibel** , quindi premere il pulsante **Seleziona cartella** .
* Attendere che il progetto venga caricato in Unity.
* Nel pannello del **progetto** aprire **Scenes\Decibel.Unity**.
* Nel pannello **gerarchia** espandere ologrammcollection  e selezionare **P0LY**.
* Nel controllo espandere **audiosource** e notare che non è presente alcuna casella di controllo **Spatialize** .

Per impostazione predefinita, Unity non carica un plug-in Spatializer. Nei passaggi seguenti viene abilitato il suono spaziale nel progetto.

* Nel menu principale di Unity scegliere **modifica > impostazioni progetto > audio**.
* Individuare l'elenco a discesa plug-in **Spatializer** e selezionare **MS HRTF Spatializer**.
* Nel pannello **gerarchia** selezionare ologrammcollection **> P0LY**.
* Nel pannello **Inspector** trovare il componente di **origine audio** .
* Selezionare la casella di controllo **Spatialize** .
* Trascinare il dispositivo di scorrimento di **Blend spaziale** fino a **3D**oppure immettere **1** nella casella di modifica.

Il progetto verrà ora compilato in Unity e la soluzione verrà configurata in Visual Studio.

1. In Unity selezionare **File > impostazioni di compilazione**.
2. Fare clic su **Aggiungi scene aperte** per aggiungere la scena.
3. Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco **piattaforma** e fare clic su **Cambia piattaforma**.
4. Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** su **HoloLens**. In caso contrario, lasciarlo in **qualsiasi dispositivo**.
5. Verificare che **tipo di compilazione** sia impostato su **D3D** e che l' **SDK** sia impostato su **installato più recente** (che deve essere SDK 16299 o versione successiva).
6. Fai clic su **Compila**.
7. Creare una **nuova cartella** denominata "app".
8. Fare clic sulla cartella dell' **app** .
9. Premere **Seleziona cartella**.

Quando si esegue Unity, viene visualizzata una finestra Esplora file.

1. Aprire la cartella dell' **app** .
2. Aprire la **soluzione decibel di Visual Studio**.

Se si esegue la distribuzione in HoloLens:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x86**.
2. Fare clic sulla freccia a discesa accanto al pulsante computer locale e selezionare **computer remoto**.
3. Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione su **universale (protocollo non crittografato)** . Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, vedere **impostazioni > rete & Internet > opzioni avanzate**.
4. Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**. Se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario associarla a [Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).

Se si esegue la distribuzione in un auricolare immersivo:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da debug a **Release** e da ARM a **x64**.
2. Verificare che la destinazione di distribuzione sia impostata su **computer locale**.
3. Nella barra dei menu superiore fare clic su **debug-> avvia senza eseguire debug** o premere **CTRL + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capitolo 2-audio e interazione spaziali

### <a name="objectives"></a>Obiettivi

* Migliorare il Real ologramma usando il suono.
* Indirizzare lo sguardo dell'utente usando un suono.
* Fornire commenti e suggerimenti sui movimenti usando un suono.

### <a name="part-1---enhancing-realism"></a>Parte 1-miglioramento del realismo

#### <a name="key-concepts"></a>Concetti chiave

* Spatialize ologrammi.
* Le origini audio devono essere posizionate in una posizione appropriata nell'ologramma.

Il percorso appropriato per il suono dipende dall'ologramma. Se, ad esempio, l'ologramma è umano, l'origine del suono dovrebbe trovarsi vicino alla bocca e non ai piedi.

#### <a name="instructions"></a>Istruzioni

Le istruzioni seguenti allegheranno un suono spaziali a un ologramma.

* Nel pannello **gerarchia** espandere ologrammcollection  e selezionare **P0LY**.
* Nel pannello di **controllo** , in **audiosource**, fare clic sul cerchio accanto a **AudioClip** e selezionare **polihover** dal menu a comparsa.
* Fare clic sul cerchio accanto a **output** e selezionare **SoundEffects** dal menu a comparsa.

Il progetto decibel usa un componente **audiomixer** Unity per abilitare la regolazione dei livelli audio per gruppi di suoni. Raggruppando i suoni in questo modo, è possibile modificare il volume complessivo mantenendo il volume relativo di ogni suono.

* In **audiosource**espandere **impostazioni audio 3D**.
* Impostare il **livello di Doppler** su **0**.

L'impostazione del livello di Doppler su zero disabilita le modifiche apportate a un pitch causato da un movimento, ovvero l'ologramma o l'utente. Un esempio classico di Doppler è un'auto in rapida evoluzione. Quando l'auto si avvicina a un listener fisso, il pitch del motore aumenta. Quando passa il listener, il passo viene ridotto a distanza.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2-indirizzare lo sguardo dell'utente

#### <a name="key-concepts"></a>Concetti chiave

* Usare il suono per richiamare l'attenzione sugli ologrammi importanti.
* Gli orecchi consentono di indirizzare il punto di vista.
* Il cervello ha alcune aspettative acquisite.

Un esempio di aspettative apprese è che gli uccelli si trovano in genere sopra i capi degli uomini. Se un utente riceve un segnale acustico, la relativa reazione iniziale è la ricerca. L'inserimento di un uccello sotto l'utente può comportare la direzione corretta del suono, ma non è in grado di trovare l'ologramma in base alla necessità di cercare.

#### <a name="instructions"></a>Istruzioni

Le istruzioni seguenti consentono a P0LY di nascondersi dietro l'utente, in modo da poter usare il suono per individuare l'ologramma.

* Nel pannello **gerarchia** selezionare managers .
* Nel pannello **Inspector** trovare gestore di **input vocale**.
* In **gestore di input vocale**espandere **Vai a Nascondi**.
* Modificare **Nessuna funzione** in **poliactions. GoHide**.

![Parola chiave Nascondi](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3: commenti e suggerimenti sui movimenti

#### <a name="key-concepts"></a>Concetti chiave

* Fornire all'utente una conferma positiva del movimento usando un suono
* Non sovraccaricare i suoni eccessivamente rumorosi dell'utente
* I rumori sottili funzionano meglio: non offuscare l'esperienza

#### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** espandere ologrammcollection .
* Espandere **EnergyHub** e selezionare **base**.
* Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere il **gestore audio del movimento**.
* Nel **gestore del suono del movimento**fare clic sul cerchio accanto al clip avviato per la **navigazione** e selezionare il clip **aggiornato** e selezionare **RotateClick** dal menu a comparsa per entrambe.
* Fare doppio clic su "GestureSoundHandler" per caricare in Visual Studio.

Il gestore del suono del movimento esegue le attività seguenti:

* Creare e configurare un **audiosource**.
* Inserire **audiosource** nella posizione del **GameObject**appropriato.
* Riproduce il **AudioClip** associato al movimento.

#### <a name="build-and-deploy"></a>Compilazione e distribuzione

1. In Unity selezionare **File > impostazioni di compilazione**.
2. Fai clic su **Compila**.
3. Fare clic sulla cartella dell' **app** .
4. Premere **Seleziona cartella**.

Controllare che la barra degli strumenti indichi "versione", "x86" o "x64" e "dispositivo remoto". In caso contrario, si tratta dell'istanza di codifica di Visual Studio. Potrebbe essere necessario aprire nuovamente la soluzione dalla cartella dell'app.

* Se richiesto, ricaricare i file di progetto.
* Come in precedenza, eseguire la distribuzione da Visual Studio.

Dopo la distribuzione dell'applicazione:

* Osservare le modifiche apportate al suono quando ci si sposta intorno a P0LY.
* Pronunciare *"go Hide"* per fare in modo che P0LY si sposti in una posizione sottostante. Trovarlo in base al suono.
* Guardare la base dell'hub energia. Toccare e trascinare verso sinistra o destra per ruotare l'ologramma e notare come il suono di clic confermi il movimento.

Nota: È presente un pannello di testo che tag insieme all'utente. Questo conterrà i comandi vocali disponibili che è possibile usare in questo corso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capitolo 3-mapping spaziale e spaziale

### <a name="objectives"></a>Obiettivi

* Confermare l'interazione tra ologrammi e il mondo reale usando un suono.
* Occludere suono che usa il mondo fisico.

### <a name="part-1---physical-world-interaction"></a>Parte 1: interazione con il mondo fisico

#### <a name="key-concepts"></a>Concetti chiave

* In genere, gli oggetti fisici comportano un suono quando si verifica una superficie o un altro oggetto.
* I suoni devono essere appropriati per il contesto all'interno dell'esperienza.

Ad esempio, l'impostazione di un calice in una tabella dovrebbe rendere un suono più tranquillo rispetto alla rimozione di un masso in un pezzo di metallo.

#### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** espandere ologrammcollection .
* Espandere **EnergyHub**, selezionare **base**.
* Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **toccare per inserire il suono e l'azione**.
* In **Tap per inserire il suono e l'azione**:
  * Controllare la **posizione dell'elemento padre al tocco**.
  * Impostare il **suono del posizionamento** sul **posto**.
  * Imposta il **suono del pickup** su **pickup**.
  * Premere + in basso a destra sotto l' **azione di prelievo** e **sull'azione di selezione host**. Trascinare EnergyHub dalla scena ai campi **None (Object)** .
    * In **azione di prelievo**fare clic su **Nessuna funzione** -> **EnergyHubBase** -> **ResetAnimation**.
    * In **azione posizionamento**fare clic su **Nessuna funzione** -> **EnergyHubBase** -> **onselect**.

![Toccare per inserire il suono e l'azione](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2-occlusione del suono

#### <a name="key-concepts"></a>Concetti chiave

* Il suono, come Light, può essere nascosto.

Un esempio classico è una sala concerti. Quando un listener si trova al di fuori della hall e la porta viene chiusa, la musica emette un suono ovattato. In genere è presente anche una riduzione del volume. Quando lo sportello viene aperto, l'intero spettro del suono viene udito nel volume effettivo. I suoni ad alta frequenza vengono in genere assorbiti più di frequenze basse.

#### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** espandere ologrammcollection  e selezionare **P0LY**.
* Nel pannello di **controllo** fare clic su **Aggiungi componente** e Aggiungi **emettitore audio**.

La classe Emittor audio fornisce le funzionalità seguenti:

* Ripristina tutte le modifiche apportate al volume del **audiosource**.
* Esegue un oggetto **Physics. RaycastNonAlloc** dalla posizione dell'utente nella direzione del **GameObject** a cui è collegato il **AudioEmitter** .

Il metodo RaycastNonAlloc viene utilizzato come ottimizzazione delle prestazioni per limitare le allocazioni e il numero di risultati restituiti.

* Per ogni **IAudioInfluencer** rilevato, chiama il metodo **ApplyEffect** .
* Per ogni **IAudioInfluencer** precedente non più rilevata, chiamare il metodo **RemoveEffect** .

Si noti che AudioEmitter viene aggiornato in base alle scale temporali umane, anziché ai singoli frame. Questa operazione viene eseguita perché gli utenti in genere non si spostano abbastanza rapidamente affinché l'effetto debba essere aggiornato con una frequenza maggiore di ogni trimestre o metà di un secondo. Gli ologrammi che si teletrasportano rapidamente da una posizione a un'altra possono suddividere l'illusione.

* Nel pannello **gerarchia** espandere ologrammcollection .
* Espandere **EnergyHub** e selezionare **BlobOutside**.
* Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **occlusione audio**.
* In **occlusione audio**impostare **frequenza di taglio** su **1500**.

Questa impostazione limita le frequenze AudioSource a 1500 Hz e inferiori.

* Impostare **volume pass-through** su **0,9**.

Questa impostazione riduce il volume del AudioSource al 90% del livello corrente.

Occlusione audio implementa IAudioInfluencer per:

* Applicare un effetto occlusione usando un **AudioLowPassFilter** che viene collegato al **audiosource** gestito acquistare il **AudioEmitter**.
* Applica l'attenuazione del volume a AudioSource.
* Disabilita l'effetto impostando una frequenza di taglio neutra e disabilitando il filtro.

La frequenza utilizzata come neutra è 22 kHz (22000 Hz). Questa frequenza è stata scelta perché si trova al di sopra della frequenza massima nominale che può essere ascoltata dall'orecchio umano, che non ha alcun effetto discernente sul suono.

* Nel pannello **gerarchia** selezionare **SpatialMapping**.
* Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **occlusione audio**.
* In **occlusione audio**impostare **frequenza di taglio** su **750**.

Quando più occluders si trovano nel percorso tra l'utente e il **AudioEmitter**, viene applicata la frequenza più bassa al filtro.

* Impostare **volume pass-through** su **0,75**.

Quando più occluders si trovano nel percorso tra l'utente e il **AudioEmitter**, il pass-through del volume viene applicato in aggiunta.

* Nel pannello **gerarchia** selezionare managers .
* Nel pannello **Inspector** espandere gestore di **input vocale**.
* In **gestore di input vocale**espandere **Vai**a addebiti.
* Modificare **Nessuna funzione** in **poliactions. GoCharge**.

![Parola chiave Ricarica](images/gocharge.png)

* Espandi **.**
* **Non modificare alcuna funzione** in poliactions **. Comeback**.

![Parola chiave Vieni qui](images/comehere.png)

#### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Come in precedenza, compilare il progetto in Unity e distribuirlo in Visual Studio.

Dopo la distribuzione dell'applicazione:

* Pronunciare *"go charge"* per fare in modo che P0LY entri nell'hub di energia.

Si noti la modifica apportata al suono. Dovrebbe sembrare ovattato e leggermente più tranquillo. Se si è in grado di posizionarsi con un muro o un altro oggetto tra l'utente e l'hub energetico, è necessario notare un ulteriore silenziatore del suono a causa dell'occlusione del mondo reale.

* Pronunciare *"qui"* per fare in modo che P0LY lasci l'hub di energia e la posizione in primo piano.

Si noti che l'occlusione audio viene rimossa quando P0LY esce dall'hub di energia. Se si sta ancora sentendo l'occlusione, P0LY potrebbe essere bloccato dal mondo reale. Provare a eseguire il passaggio per assicurarsi di avere una chiara linea di visibilità per P0LY.

### <a name="part-3---room-models"></a>Parte 3-modelli di chat room

#### <a name="key-concepts"></a>Concetti chiave

* La dimensione dello spazio fornisce le code subliminali che contribuiscono alla localizzazione del suono.
* I modelli room sono impostati per ogni**audiosource**.
* [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce il codice per l'impostazione del modello room.
* Per esperienze di realtà mista, selezionare il modello room più adatto allo spazio reale.

Se si sta creando uno scenario di realtà virtuale, selezionare il modello room più adatto all'ambiente virtuale.

## <a name="chapter-4---sound-design"></a>Capitolo 4-progettazione audio

### <a name="objectives"></a>Obiettivi

* Comprendere le considerazioni relative alla progettazione di un suono efficace.
* Impara a combinare tecniche e linee guida.

### <a name="part-1---sound-and-experience-design"></a>Parte 1: progettazione di suoni e esperienza

In questa sezione vengono illustrate le linee guida e le considerazioni principali relative alla progettazione.

#### <a name="normalize-all-sounds"></a>Normalizza tutti i suoni

In questo modo si evita la necessità di codice del case speciale per modificare i livelli del volume per ogni suono, che può richiedere molto tempo e limita la possibilità di aggiornare facilmente i file audio.

#### <a name="design-for-an-untethered-experience"></a>Progettazione per un'esperienza non legata

HoloLens è un computer olografico completamente indipendente e non tethered. Gli utenti possono e utilizzeranno le proprie esperienze durante lo trasferimento. Assicurarsi di testare la combinazione di audio aggirando.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emettere un suono da posizioni logiche sugli ologrammi

Nel mondo reale, un cane non abbaia dalla coda e la voce umana non proviene dai suoi piedi. Evitare di creare suoni da parti impreviste degli ologrammi.

Per gli ologrammi di piccole dimensioni, è ragionevole avere suono emesso dal centro della geometria.

#### <a name="familiar-sounds-are-most-localizable"></a>I suoni noti sono più localizzabili

La voce e la musica umana sono molto facili da localizzare. Se un utente chiama il proprio nome, è possibile determinare in modo molto accurato dalla direzione della voce e dal punto in cui si è lontani. I suoni brevi e non noti sono più difficili da localizzare.

#### <a name="be-cognizant-of-user-expectations"></a>Tenere a conoscenza delle aspettative degli utenti

L'esperienza di vita gioca una parte della capacità di identificare la posizione di un suono. Questo è uno dei motivi per cui la voce umana è particolarmente facile da localizzare. È importante essere a conoscenza delle aspettative apprese dall'utente quando si posizionano i suoni.

Ad esempio, quando qualcuno ascolta un brano di Bird, in genere cerca, perché gli uccelli tendono a essere al di sopra della linea di vista (Flying o in un albero). Non è insolito che un utente accenda la direzione corretta di un suono, ma si trovi nella direzione verticale errata e si confonde o si frustra quando non è in grado di trovare l'ologramma.

#### <a name="avoid-hidden-emitters"></a>Evitare gli emettitori nascosti

Nel mondo reale, se viene emesso un segnale acustico, in genere è possibile identificare l'oggetto che emette il suono. Questa operazione dovrebbe essere valida anche per le proprie esperienze. Per gli utenti può essere molto sconcertante ascoltare un suono, sapere da dove ha origine il suono e non essere in grado di visualizzare un oggetto.

Esistono alcune eccezioni a questa linea guida. Ad esempio, i suoni di ambiente come i cricket in un campo non devono essere visibili. L'esperienza di vita offre familiarità con l'origine di questi suoni senza la necessità di visualizzarla.

### <a name="part-2---sound-mixing"></a>Parte 2-combinazione di suoni

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Specificare come destinazione la combinazione per il volume del 70% nel HoloLens

Le esperienze di realtà miste consentono di osservare gli ologrammi nel mondo reale. Devono inoltre consentire l'ascolto di suoni reali. Una destinazione del volume del 70% consente all'utente di sentire il mondo intorno al suono dell'esperienza.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>Il volume HoloLens al 100% dovrebbe escludere i suoni esterni

Un livello di volume pari al 100% è analogo a un'esperienza di realtà virtuale. Visivamente, l'utente viene trasportato in un altro mondo. Lo stesso vale per il vero udibile.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Usare Unity AudioMixer per modificare le categorie di suoni

Quando si progetta la combinazione, è spesso utile creare categorie audio e avere la possibilità di aumentare o diminuire il volume come unità. Questo consente di mantenere i livelli relativi di ogni suono, consentendo al tempo stesso di apportare modifiche rapide e semplici alla combinazione complessiva. Le categorie comuni includono; effetti audio, ambiente, Voice over e musica in background.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Combinare i suoni in base allo sguardo dell'utente

Spesso può essere utile modificare la combinazione di suoni nell'esperienza in base alla posizione dell'utente (o non). Un uso comune di questa tecnica consiste nel ridurre il livello di volume per gli ologrammi esterni al frame olografico, in modo da rendere più semplice per l'utente concentrarsi sulle informazioni in primo piano. Un altro utilizzo consiste nell'aumentare il volume di un suono per attirare l'attenzione dell'utente su un evento importante.

#### <a name="building-your-mix"></a>Creazione della combinazione

Quando si compila la combinazione, è consigliabile iniziare con l'audio in background dell'esperienza e aggiungere i livelli in base all'importanza. Spesso, il risultato è che ogni livello è più elevato rispetto a quello precedente.

Immaginando la combinazione di un imbuto invertito, con i suoni meno importanti (e generalmente più tranquilli) nella parte inferiore, si consiglia di strutturare la combinazione in modo analogo al diagramma seguente.

![Struttura del mix audio](images/soundlevels.png)

I Voice over sono uno scenario interessante. In base all'esperienza che si sta creando, potrebbe essere necessario disporre di un audio stereo (non localizzato) o di spatialize. Due esperienze pubblicate da Microsoft illustrano esempi eccellenti di ogni scenario.

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voce stereo. Quando l'Assistente vocale descrive la posizione visualizzata, il suono è coerente e non varia in base alla posizione dell'utente. Ciò consente all'Assistente vocale di descrivere la scena senza togliere i suoni spaziali dell'ambiente.

I [frammenti](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizzano una voce con spazialità sotto forma di detective. La voce del detective viene usata per aiutare a attirare l'attenzione dell'utente su un importante indizio come se fosse presente un uomo reale nella stanza. Questo consente un senso ancora più approfondito dell'esperienza di risoluzione del mistero.

### <a name="part-3--performance"></a>Parte 3: prestazioni

#### <a name="cpu-usage"></a>Utilizzo CPU

Quando si usa il suono spaziale, gli emettitori 10-12 utilizzeranno approssimativamente il 12% della CPU.

#### <a name="stream-long-audio-files"></a>Streaming di file audio lunghi

I dati audio possono essere di grandi dimensioni, soprattutto a tariffe di esempio comuni (44,1 e 48 kHz). Una regola generale è che i file audio più lunghi di 5-10 secondi devono essere trasmessi per ridurre l'utilizzo della memoria dell'applicazione.

In Unity è possibile contrassegnare un file audio per il flusso nelle impostazioni di importazione del file.

![Impostazioni di importazione audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capitolo 5-effetti speciali

### <a name="objectives"></a>Obiettivi

* Aggiungere Depth a "Magic Windows".
* Porta l'utente nel mondo virtuale.

### <a name="magic-windows"></a>Finestre magiche

#### <a name="key-concepts"></a>Concetti chiave

* La creazione di visualizzazioni in un ambiente nascosto è visivamente accattivante.
* Migliora il realismo aggiungendo effetti audio quando un ologramma o l'utente è vicino al mondo nascosto.

#### <a name="instructions"></a>Istruzioni

* Nel pannello **gerarchia** espandere ologrammcollection  e selezionare Sottomondo .
* Espandere **Underworld** e selezionare **VoiceSource**.
* Nel pannello di **controllo** fare clic su **Aggiungi componente** e aggiungere **effetto voce utente**.

Verrà aggiunto un componente **audiosource** a **VoiceSource**.

* In **audiosource**impostare **output** su **UserVoice (mixer)** .
* Selezionare la casella di controllo **Spatialize** .
* Trascinare il dispositivo di scorrimento di **Blend spaziale** fino a **3D**oppure immettere **1** nella casella di modifica.
* Espandere **impostazioni audio 3D**.
* Impostare il **livello di Doppler** su **0**.
* In **effetto voce utente**impostare **oggetto padre** sul Sottomondo  dalla scena.
* Impostare **distanza massima** su **1**.

L'impostazione della **distanza massima** indica all' **utente** il modo in cui la chiusura dell'utente deve essere l'oggetto padre prima che l'effetto venga attivato.

* In **effetto voce utente**espandere **parametri Chorus**.
* Impostare **Depth** su **0,1**.
* Impostare **toccare 1 volume**, **toccare 2 volume** e **toccare 3 volume** su **0,8**.
* Impostare **volume audio originale** su **0,5**.

Le impostazioni precedenti configurano i parametri del **AudioChorusFilter** Unity usato per aggiungere ricchezza alla voce dell'utente.

* In **effetto voce utente**espandere **parametri Echo**.
* Imposta **ritardo** su **300**
* Imposta il **rapporto** di decadimento su **0,2**.
* Impostare **volume audio originale** su **0**.

Le impostazioni precedenti configurano i parametri del **AudioEchoFilter** Unity usato per fare in modo che la voce dell'utente sia Echo.

Lo script dell'effetto vocale utente è responsabile di:

* Misurazione della distanza tra l'utente e la **GameObject** a cui è associato lo script.
* Determinare se l'utente si trova o meno a **GameObject**.

È necessario che l'utente si trovi a fronte del GameObject, indipendentemente dalla distanza, per abilitare l'effetto.

* Applicazione e configurazione di un **AudioChorusFilter** e di un **AudioEchoFilter** in **audiosource**.
* Disabilitare l'effetto disabilitando i filtri.

L'effetto voce utente usa il componente MIC Stream Selector, da [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), per selezionare il flusso di voce di qualità elevata e instradarlo nel sistema audio di Unity.

* Nel pannello **gerarchia** selezionare managers .
* Nel pannello **Inspector** espandere gestore di **input vocale**.
* In **gestore di input vocale**espandere **Mostra Sottomondo**.
* Modificare **Nessuna funzione** in **UnderworldBase. OnEnable**.

![Parola chiave Mostra Sottomondo](images/showunderworld.png)

* Espandi **Nascondi Sottomondo**.
* Modificare **Nessuna funzione** in **UnderworldBase. ondisable**.

![Parola chiave Nascondi Sottomondo](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Compilazione e distribuzione

* Come in precedenza, compilare il progetto in Unity e distribuirlo in Visual Studio.

Dopo la distribuzione dell'applicazione:

* Far fronte a una superficie (Wall, Floor, Table) e pronunciare *"Show Underworld"* .

Il Sottomondo verrà visualizzato e tutti gli altri ologrammi verranno nascosti. Se il Sottomondo non viene visualizzato, assicurarsi di essere connessi a una superficie reale.

* Approccio entro 1 metro dell'ologramma del Sottomondo e iniziare a comunicare.

Sono ora applicati effetti audio alla voce.

* Allontanarsi dal Sottomondo e notare il modo in cui l'effetto non viene più applicato.
* Pronunciare *"Hide Underworld"* per nascondere il Sottomondo.

Il Sottomondo verrà nascosto e verranno nuovamente visualizzati gli ologrammi nascosti in precedenza.

## <a name="the-end"></a>La fine

La procedura è stata completata. A questo punto è **stato completato lo spazio di 220: Audio**spaziale.

Ascolta il mondo e fai vivere le tue esperienze con i suoni.
