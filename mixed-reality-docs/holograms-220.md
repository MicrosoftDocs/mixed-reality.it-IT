---
title: MR spaziale 220 - spaziale audio
description: Seguire questa procedura dettagliata codifica con Unity, Visual Studio e HoloLens informazioni dettagliate su concetti audio spaziali.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, esercitazione, spaziale audio
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599013"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR Spatial 220: Audio spaziale

[Suono spaziale](spatial-sound.md) armonioso suscita vita in ologrammi e fornisce a ognuna presenza nel mondo. Ologrammi sono costituiti sia chiaro e suono e se si perdono del vntana vista, spaziale audio consentono di trovarli. Suono spaziale non è ad esempio il suono tipico che senti sulla radio, è audio che viene posizionato nello spazio 3D. Spaziali audio, è possibile rendere vntana audio, ad esempio si trovano dietro, accanto a si o anche in mente. In questo corso, si apprenderà come:

* Configurare l'ambiente di sviluppo per usare Microsoft Spatial Sound.
* Usare un suono spaziale per migliorare le interazioni.
* Usare un suono spaziale in combinazione con Mapping spaziale.
* Comprendere la progettazione del suono e combinare le procedure consigliate.
* Usare un suono per migliorare gli effetti speciali e portare l'utente in tutto il mondo delle realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>MR Spatial 220: Audio spaziale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).
* Alcuni basic C# capacità di programmazione.
* È necessario avere completato [MR nozioni di base 101](holograms-101.md).
* Un dispositivo HoloLens [configurato per lo sviluppo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>File di progetto

* Scaricare il [file](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) necessarie per il progetto. Richiede Unity 2017.2 o versione successiva.
  * Se è comunque necessario il supporto di Unity 5.6, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Questa versione potrebbe non essere più aggiornata.
  * Se è comunque necessario il supporto di Unity 5.5, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Questa versione potrebbe non essere più aggiornata.
  * Se è ancora necessario supporto 5.4 di Unity, usare [questa versione](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Questa versione potrebbe non essere più aggiornata.
* Annullare la-archive i file sul desktop o altri facile da raggiungere percorso.

>[!NOTE]
>Se si desidera esaminare il codice sorgente prima di scaricare, ha [disponibile in GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Errori e note

* "Abilita Just My Code" deve essere disabilitato (*unchecked*) in Visual Studio in Strumenti -> Opzioni -> debug per poter raggiungere punti di interruzione nel codice.

## <a name="chapter-1---unity-setup"></a>Capitolo 1 - il programma di installazione di Unity

### <a name="objectives"></a>Obiettivi

* Modificare la configurazione di audio di Unity per usare Microsoft Spatial Sound.
* Aggiungere suoni 3D a un oggetto in Unity.

### <a name="instructions"></a>Istruzioni

* Avviare Unity.
* Selezionare **aperto**.
* Passare al Desktop e individuare la cartella è archiviato in precedenza di annullamento.
* Fare clic sui **Starting\Decibel** cartella e quindi premere il **Seleziona cartella** pulsante.
* Attendere che il progetto da caricare in Unity.
* Nel **Project** pannello aperto **Scenes\Decibel.unity**.
* Nel **gerarchia** panel, espandere **HologramCollection** e selezionare **P0LY**.
* Nella finestra di ispezione, espandere **AudioSource** e notare che non vi è alcun **Spatialize** casella di controllo.

Per impostazione predefinita, Unity non viene caricato un plug-in spaziale. La procedura seguente consentirà spaziali audio nel progetto.

* Nel menu in alto di Unity, passare a **Modifica > Impostazioni di progetto > Audio**.
* Trovare il **plug-in spaziale** dal menu a discesa e selezionare **MS HRTF Spatializer**.
* Nel **gerarchia** Pannello di selezione **HologramCollection > P0LY**.
* Nel **Inspector** panel, trovare il **origine Audio** componente.
* Verificare i **Spatialize** casella di controllo.
* Trascinare il **Blend spaziali** dispositivo di scorrimento fino alla **3D**, oppure immettere **1** nella casella di modifica.

È ora verrà compilare il progetto in Unity e configurare la soluzione in Visual Studio.

1. In Unity, selezionare **File > Build Settings**.
2. Fare clic su **aggiungere scene Open** per aggiungere la scena.
3. Selezionare **Universal Windows Platform** nel **Platform** elenco e fare clic su **commutatore piattaforma**.
4. Se si sta sviluppando in modo specifico per HoloLens, impostare **dispositivo di destinazione** al **HoloLens**. In caso contrario, ci si trova sulla **tutti i dispositivi**.
5. Assicurarsi **tipo di compilazione** è impostata su **D3D** e **SDK** è impostata su **installata più recente** (che deve essere SDK 16299 o versione successiva).
6. Fai clic su **Compila**.
7. Creare un **nuova cartella** denominato "App".
8. Solo clic i **App** cartella.
9. Premere **Seleziona cartella**.

Quando Unity viene eseguita, verrà visualizzata una finestra di Esplora File.

1. Aprire il **App** cartella.
2. Aprire il **soluzione di Visual Studio Decibel**.

Se la distribuzione in HoloLens:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x86**.
2. Fare clic sull'elenco a discesa sulla freccia accanto al pulsante computer locale e selezionare **computer remoto**.
3. Immettere **l'indirizzo IP del dispositivo HoloLens** e impostare la modalità di autenticazione **universale (protocollo non crittografato)**. Fare clic su **Seleziona**. Se non si conosce l'indirizzo IP del dispositivo, esaminare **Impostazioni > rete e Internet > Opzioni avanzate**.
4. Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**. Se questa è la prima volta che la distribuzione nel dispositivo, devi [abbinarlo a Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).

Se la distribuzione in un visore VR immersivi:

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione di debug per **Release** e da ARM a **x64**.
2. Verificare che la destinazione di distribuzione è impostata su **computer locale**.
3. Nella barra dei menu superiore, fare clic su **Debug -> Avvia senza eseguire debug** o premere **Ctrl + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capitolo 2 - spaziale e suono di interazione

### <a name="objectives"></a>Obiettivi

* Migliorare il realismo ologrammi utilizzando audio.
* Indirizzare sguardo dell'utente utilizzando audio.
* Commenti e suggerimenti di movimento tramite file audio.

### <a name="part-1---enhancing-realism"></a>Parte 1 - realismo miglioramento

#### <a name="key-concepts"></a>Concetti chiave

* Spatialize suoni ologramma.
* Origini audio devono essere posizionate in una posizione appropriata di ologramma.

Il percorso appropriato per l'audio verrà variano a seconda di ologramma. Ad esempio, se l'ologrammi sono di un essere umano, l'origine audio deve trovarsi quasi bocca e non dei piedi.

#### <a name="instructions"></a>Istruzioni

Le istruzioni seguenti collegherà un suono spatialized di ologramma.

* Nel **gerarchia** panel, espandere **HologramCollection** e selezionare **P0LY**.
* Nel **Inspector** Pannello di **AudioSource**, fare clic sul cerchio accanto a **AudioClip** e selezionare **PolyHover** dalla finestra a comparsa.
* Fare clic sul cerchio accanto alla **Output** e selezionare **SoundEffects** dalla finestra a comparsa.

Progetto Decibel Usa un'istanza di Unity **AudioMixer** componente per abilitare la modifica dei livelli audio per i gruppi di suoni. È possibile regolare il volume complessivo dal raggruppamento di suoni in questo modo, pur mantenendo il relativo volume di ciascun file audio.

* Nel **AudioSource**, espandere **3D impostazioni audio**.
* Impostare **livello Doppler** al **0**.

Impostazione livello Doppler a zero modifiche Disabilita nel passo causati da movimento (entrambi l'ologrammi e l'utente). Un esempio tipico di utilizzo Doppler è un'auto in rapida evoluzione. Come l'auto si avvicina a un listener stazionario, aumenta il tono del motore. Quando si passa il listener, il tono scende con distanza.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2 - indirizzamento sguardo dell'utente

#### <a name="key-concepts"></a>Concetti chiave

* Usare un suono per attirare l'attenzione su vntana importanti.
* Orecchie consentono di indirizzare in cui dovrebbe avere un aspetto dal punto di vista.
* Il cervello ha alcune aspettative appreso.

Un esempio delle aspettative acquisite è che sono in genere volatili sopra i capi di esseri umani. Se un utente ascolta un suono bird, la reazione iniziale consiste nel cercare. Inserimento di uccelli sotto l'utente può portare a essi rivolta nella direzione corretta del suono, ma non riesce a trovare l'ologrammi si prevede di dover cercare in base.

#### <a name="instructions"></a>Istruzioni

Le istruzioni seguenti abilitano P0LY nascondere sottostante è, in modo che è possibile usare suono per individuare l'ologramma.

* Nel **gerarchia** Pannello di selezione **responsabili**.
* Nel **Inspector** panel, trovare **gestore di Input vocale**.
* Nelle **gestore di Input vocale**, espandere **Vai nascondere**.
* Change **alcuna funzione** al **PolyActions.GoHide**.

![parola chiave: Nascondi passare](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3 - commenti e suggerimenti di movimento

#### <a name="key-concepts"></a>Concetti chiave

* Fornire all'utente conferma positivo movimento utilizzando audio
* Invece di travolgerci utente - get suoni troppo alti in modo
* Suoni sottili funzionano in modo ottimale - non stonino l'esperienza

#### <a name="instructions"></a>Istruzioni

* Nel **gerarchia** panel, espandere **HologramCollection**.
* Espandere **EnergyHub** e selezionare **Base**.
* Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **gestore movimenti suono**.
* Nella **gestore movimenti suono**, fare clic sul cerchio accanto a **spostamento avviato Clip** e **navigazione aggiornato Clip** e selezionare **RotateClick**dalla finestra a comparsa per entrambi.
* Fare doppio clic su "GestureSoundHandler" per il caricamento in Visual Studio.

Gestore di segnale acustico di movimento esegue le attività seguenti:

* Creare e configurare un' **AudioSource**.
* Sul posto di **AudioSource** in corrispondenza della posizione di appropriato **GameObject**.
* Riproduce il **AudioClip** associato al movimento.

#### <a name="build-and-deploy"></a>Compilare e distribuire

1. In Unity, selezionare **File > Build Settings**.
2. Fai clic su **Compila**.
3. Solo clic i **App** cartella.
4. Premere **Seleziona cartella**.

Verificare che la barra degli strumenti viene visualizzato "Rilascio", "x86" o "x64" e "Dispositivo remoto". In caso contrario, si tratta dell'istanza di scrittura del codice di Visual Studio. Potrebbe essere necessario aprire nuovamente la soluzione dalla cartella dell'App.

* Se richiesto, ricaricare i file di progetto.
* Come in precedenza, eseguire la distribuzione da Visual Studio.

Dopo aver distribuita l'applicazione:

* Osservare come il suono cambia mentre si sposta all'interno di P0LY.
* Pronunciare *"Vai Hide"* apportare P0LY spostare in un percorso sottostante è. Cercarla, l'audio.
* Fissare la base di Hub di energia. Toccare e trascinare destra o sinistra per ruotare l'ologrammi e notare come il suono facendo clic su Conferma il movimento.

Nota: È presente un pannello di testo che verrà tag-along con l'utente. Questa sezione contiene i comandi vocali disponibili che è possibile usare in questo corso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capitolo 3 - Mapping spaziale audio e quelli spaziali

### <a name="objectives"></a>Obiettivi

* Verificare l'interazione tra ologrammi e il mondo reale con file audio.
* Nasconde i colori audio mediante il mondo fisico.

### <a name="part-1---physical-world-interaction"></a>Part 1 - Physical World Interaction

#### <a name="key-concepts"></a>Concetti chiave

* Oggetti fisici generi un suono a livello generale in presenza di un'area o in un altro oggetto.
* Suoni dovrebbero essere appropriato all'interno di un contesto.

Ad esempio, l'impostazione di una tazza di una tabella deve generi un suono risulteranno meno intensi di eliminazione di un boulder su un foglio di metallo.

#### <a name="instructions"></a>Istruzioni

* Nel **gerarchia** panel, espandere **HologramCollection**.
* Espandere **EnergyHub**, selezionare **Base**.
* Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **toccare a sul posto con suono e azione**.
* Nelle **toccare a con azione e suono**:
  * Controllare **posizionare padre al tocco**.
  * Impostare **suono di posizionamento** al **luogo**.
  * Impostare **suono Pickup** al **Pickup**.
  * Premere + in basso a destra sotto entrambi **in azione Pickup** e **azione sul posizionamento**. Trascinare EnergyHub dalla scena nel **Nessuno (oggetto)** campi.
    * Sotto **in azione Pickup**, fare clic su **nessuna funzione** -> **EnergyHubBase** -> **ResetAnimation**.
    * Sotto **azione sul posizionamento**, fare clic su **nessuna funzione** -> **EnergyHubBase** -> **OnSelect**.

![Toccare a con azione e suono](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2 - occlusione audio

#### <a name="key-concepts"></a>Concetti chiave

* File audio, ad esempio chiaro, possa essere bloccato.

Un esempio classico è un concerti. Quando un listener è permanente di fuori ufficio e la porta è chiuso, i suoni di musica ovattati. È inoltre disponibile in genere una riduzione del volume. Quando si apre la porta, la gamma completa dell'audio viene ascoltata al volume effettivo. Suoni ad alta frequenza vengono in genere assorbiti più basse frequenze.

#### <a name="instructions"></a>Istruzioni

* Nel **gerarchia** panel, espandere **HologramCollection** e selezionare **P0LY**.
* Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **Audio emettitore**.

La classe Audio emettitore fornisce le funzionalità seguenti:

* Ripristina tutte le modifiche al volume dei **AudioSource**.
* Esegue una **Physics.RaycastNonAlloc** dalla posizione dell'utente nella direzione delle **GameObject** a cui il **AudioEmitter** è collegato.

Il metodo RaycastNonAlloc viene utilizzato come ottimizzare le prestazioni per limitare le allocazioni, nonché il numero di risultati restituiti.

* Per ognuno **IAudioInfluencer** rilevato, chiama il **ApplyEffect** (metodo).
* Per ogni precedente **IAudioInfluencer** vale a dire chiamata non è più rilevato, il **RemoveEffect** (metodo).

Si noti che AudioEmitter Aggiorna in tempi umanamente scale, in contrapposizione a pagamento in base al frame. Ciò avviene perché gli esseri umani in genere non si spostano sufficientemente rapido per l'effetto di dover essere aggiornata con frequenza maggiore rispetto a ogni trimestre o semestre di un secondo. Ologrammi tale teleport rapidamente da una posizione a un'altra può interrompere l'illusione.

* Nel **gerarchia** panel, espandere **HologramCollection**.
* Espandere **EnergyHub** e selezionare **BlobOutside**.
* Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **Audio Occluder**.
* Nelle **Occluder Audio**, impostare **frequenza di taglio** al **1500**.

Questa impostazione limita le frequenze AudioSource ad Hz 1500 e versioni precedenti.

* Impostare **Volume Pass-Through** al **0.9**.

Questa impostazione riduce il volume del AudioSource al 90% del relativo livello corrente.

Audio Occluder implementa IAudioInfluencer per:

* Applicare un effetto di occlusione usando un **AudioLowPassFilter** che viene associato ai **AudioSource** buy gestito il **AudioEmitter**.
* Si applica un'attenuazione volume per il AudioSource.
* Disabilita l'effetto impostando una frequenza di taglio neutra e la disabilitazione del filtro.

La frequenza utilizzata come neutro è kHz 22 (22000 Hz). Poiché i file sono di sopra la nominale frequenza massima che può essere ascoltata dai ascoltati dal umani, questa effettua alcun impatto percepibile per l'audio è stato scelto questa frequenza.

* Nel **gerarchia** Pannello di selezione **SpatialMapping**.
* Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **Audio Occluder**.
* Nelle **Occluder Audio**, impostare **frequenza di taglio** al **750**.

Quando più occluders si trovano nel percorso tra l'utente e la **AudioEmitter**, la frequenza minima viene applicata al filtro.

* Impostare **Volume Pass-Through** al **0,75**.

Quando più occluders si trovano nel percorso tra l'utente e la **AudioEmitter**, il volume pass-through viene applicato modo additivo.

* Nel **gerarchia** Pannello di selezione **responsabili**.
* Nel **Inspector** panel, espandere **gestore di Input vocale**.
* Nelle **gestore di Input vocale**, espandere **Vai addebito**.
* Change **alcuna funzione** al **PolyActions.GoCharge**.

![parola chiave: Passare l'addebito](images/gocharge.png)

* Espandere **qui**.
* Change **alcuna funzione** al **PolyActions.ComeBack**.

![parola chiave: In questa pagina](images/comehere.png)

#### <a name="build-and-deploy"></a>Compilare e distribuire

* Come in precedenza, compilare il progetto in Unity e distribuzione in Visual Studio.

Dopo aver distribuita l'applicazione:

* Pronunciare *"Addebito per passare"* per far P0LY entrare nell'Hub di energia.

Si noti la modifica dell'audio. Necessario un tono sordo e un po' più basse. Se si è in grado di posizionare manualmente con una parete o un altro oggetto tra l'utente e l'Hub di energia, si dovrebbe notare un'ulteriore muffling del suono a causa dell'occlusione dal mondo reale.

* Pronunciare *"Provengono qui"* affinché P0LY lasciare l'Hub di energia e posizionerà portata di mano.

Si noti che dell'occlusione audio viene rimossa una volta P0LY viene chiuso l'Hub di energia. Se sei ancora occlusione udito, P0LY potrebbero essere bloccati in situazioni reali. Provare a spostare avere a disposizione un chiaro comunichi P0LY.

### <a name="part-3---room-models"></a>Parte 3: modelli di chat Room

#### <a name="key-concepts"></a>Concetti chiave

* Le dimensioni dello spazio fornisce code subliminali che contribuiscono alla localizzazione audio.
* I modelli di chat vengono impostati per ogni-**AudioSource**.
* Il [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce codice per impostare il modello di chat room.
* Per le esperienze di realtà mista, selezionare il modello di chat che meglio si adatta lo spazio del mondo reale.

Se si sta creando uno scenario di realtà virtuale, selezionare il modello di chat che meglio si adatta l'ambiente virtuale.

## <a name="chapter-4---sound-design"></a>Capitolo 4 - progettazione

### <a name="objectives"></a>Obiettivi

* Considerazioni per la progettazione efficace.
* Altre linee guida e le tecniche di combinazione.

### <a name="part-1---sound-and-experience-design"></a>Parte 1: progettazione dell'esperienza e suono

Questa sezione illustra le linee guida e considerazioni sulla progettazione di esperienza e suono di chiave.

#### <a name="normalize-all-sounds"></a>Normalizza tutti i file audio

Questo evita la necessità di codice case speciale regolare i livelli di volume al suono, che può richiedere tempi lunghi e riduce la possibilità di aggiornare facilmente i file audio.

#### <a name="design-for-an-untethered-experience"></a>Progettazione per un'esperienza senza i limiti

HoloLens è un computer holographic completamente indipendente, senza i limiti. Gli utenti possono e userà le proprie esperienze durante lo spostamento. Assicurarsi di testare la combinazione di audio scorrendo intorno.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emette un suono da percorsi logici di vntana

Nel mondo reale, un cane non abbaiare dalla relativa coda e vocale di un essere umano non proviene dal proprio piedi. Evitare che i suoni di generano da parti impreviste del vntana.

Per piccole vntana, è ammissibile avere suono emit dal centro della geometria.

#### <a name="familiar-sounds-are-most-localizable"></a>Suoni familiari sono più localizzabili

La voce umana e musica sono molto semplici da localizzare. Se qualcuno chiama il proprio nome, si è in grado di molto accuratamente determinare da quale direzione proviene dalla voce e da come a portata di mano. Suoni familiarità e breve sono più difficili da localizzare.

#### <a name="be-cognizant-of-user-expectations"></a>Tenere conto del fatto delle aspettative dell'utente

Esperienza riveste un ruolo nella nostra capacità di identificare la posizione di un suono. Questo è il motivo per cui la voce umana è particolarmente semplice da localizzare. È importante essere a conoscenza delle aspettative appreso dell'utente quando si posiziona i suoni.

Ad esempio, quando un utente ascolta un brano musicale bird generalmente risultino verso l'alto, come quelle volatili tendono a essere sopra la linea di visuale sul (volanti o in una struttura ad albero). Non è insolito per un utente di attivare nella direzione corretta di un file audio, ma Cerca in direzione verticale errata e diventare confusi o frustrato quando non è possibile trovare l'ologramma.

#### <a name="avoid-hidden-emitters"></a>Evitare di istanze di emissione FixIt nascosti

Nel mondo reale, se abbiamo riprodotto un suono, in genere è possibile identificare l'oggetto che sta generando l'audio. Questo inoltre deve restituire true nelle proprie esperienze. Può costituire un problema molto agli utenti di ascoltare un suono, sapere da dove proviene l'audio e in grado di rilevare un oggetto.

Esistono alcune eccezioni a questa linea guida. Ad esempio, ambiente suoni, ad esempio crickets in un campo non è necessario visibile. Esperienza ci offre una certa familiarità con l'origine di queste suoni senza la necessità di visualizzarlo.

### <a name="part-2---sound-mixing"></a>Parte 2 - missaggio audio

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>La combinazione per il 70% di HoloLens volume di destinazione

Esperienze di realtà miste consentono vntana affinché sia disponibile nel mondo reale. Permettono inoltre suoni reali per far valere. Una destinazione di 70% del volume consente all'utente di sentire il mondo attorno a esse insieme al suono di tua esperienza.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens al 100% del volume deve finire travolti dai suoni esterni

Un livello di volume pari a 100% equivale a un'esperienza di realtà virtuale. In modo visivo, l'utente viene trasportato al mondo. Lo stesso debba valere anche acustico.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Utilizzare il AudioMixer Unity per regolare le categorie di suoni

Quando si progetta la combinazione, è spesso utile creare categorie di audio e hanno la possibilità di aumentare o diminuire il volume come unità. Ciò consente di mantenere i livelli relativi di ogni file audio durante l'abilitazione delle modifiche di facile e veloce per la combinazione globale. Categorie comuni sono rappresentati da: effetti sonori, atmosfera, passaggi vocali e musica.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Combinare i suoni basati sguardo dell'utente

Spesso può essere utile modificare la combinazione di audio durante l'utilizzo basato sulla posizione in cui un utente è (o non) alla ricerca. Uno degli usi comuni per questa tecnica sono per ridurre il livello di volume per vntana esterni al Frame Holographic per renderne più semplice per gli utenti possono concentrarsi sulle informazioni davanti a essi. Un altro utilizzo consiste nell'aumentare il volume di un suono per attirare l'attenzione dell'utente a un evento importante.

#### <a name="building-your-mix"></a>La combinazione di compilazione

Quando si compila la combinazione, è consigliabile iniziare con audio in background dell'esperienza e aggiungere i livelli basati importanza. Spesso, ciò comporta in ogni livello in quella precedente.

Immaginando i modi la combinazione come un grafico a imbuto invertito, con meno importante (e in genere silenziosi suoni) nella parte inferiore, è consigliabile per definire la struttura alla combinazione di simile al diagramma seguente.

![Struttura di combinazione di audio](images/soundlevels.png)

Voice over di valori sono uno scenario interessante. Basato sull'esperienza che si sta creando è possibile avere un suono (non localizzato) stereo o spatialize i passaggi di voice. Pubblicate da Microsoft due esperienze di illustrare ottimi esempi di ogni scenario.

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) utilizza una voce stereo sulla. Quando l'Assistente vocale è descrivere il percorso viene visualizzato, il suono è coerenza e non variare in base alla posizione dell'utente. In questo modo, l'Assistente vocale descrivere la scena senza l'utilizzo di lontano dai suoni spatialized dell'ambiente.

[Frammenti](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizza una voce spatialized su sotto forma di un'indagine. Voce del detective viene utilizzato per portare l'attenzione dell'utente a un indizio importante, come se fosse un uomo effettivo nella chat room. In questo modo un senso di full immersion nell'esperienza di risolvere il mistero ancora maggiore.

### <a name="part-3--performance"></a>Parte 3 - prestazioni

#### <a name="cpu-usage"></a>Utilizzo della CPU

Quando si usa spaziale suono, 10 al 12 istanze di emissione FixIt utilizzerà circa il 12% della CPU.

#### <a name="stream-long-audio-files"></a>File audio lungo Stream

Dati audio possono essere grandi, specialmente le frequenze di campionamento più comuni (48 e 44,1 kHz). In generale è che i file audio più di circa 5-10 secondi dovrebbero essere trasmessi per ridurre l'utilizzo della memoria dell'applicazione.

In Unity, è possibile contrassegnare un file audio per il flusso in impostazioni di importazione del file.

![Impostazioni di importazione audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capitolo 5 - effetti speciali

### <a name="objectives"></a>Obiettivi

* Aggiungere profondità "Magic Windows".
* Rendere l'utente del mondo virtuale.

### <a name="magic-windows"></a>Magic Windows

#### <a name="key-concepts"></a>Concetti chiave

* Creazione di visualizzazioni in un mondo caratterizzato dalla nascosto, è visivamente accattivanti.
* Migliorare il realismo aggiungendo effetti audio quando ologramma oppure l'utente si avvicina al mondo nascosto.

#### <a name="instructions"></a>Istruzioni

* Nel **gerarchia** panel, espandere **HologramCollection** e selezionare **Underworld**.
* Espandere **Underworld** e selezionare **VoiceSource**.
* Nel **Inspector** del pannello, fare clic su **Add Component** e aggiungere **utente vocale effetto**.

Un' **AudioSource** verrà aggiunto al componente **VoiceSource**.

* Nelle **AudioSource**, impostare **Output** al **UserVoice (Mixer)**.
* Verificare i **Spatialize** casella di controllo.
* Trascinare il **Blend spaziali** dispositivo di scorrimento fino alla **3D**, oppure immettere **1** nella casella di modifica.
* Espandere **le impostazioni audio 3D**.
* Impostare **livello Doppler** al **0**.
* Nelle **utente vocale effetto**, impostare **oggetto padre** per il **Underworld** dalla scena.
* Impostare **distanza massima** al **1**.

L'impostazione **distanza massima** indica **utente vocale effetto** Chiudi modo in cui l'utente deve essere all'oggetto padre prima che l'effetto è abilitato.

* Nelle **utente vocale effetto**, espandere **coro parametri**.
* Impostare **profondità** al **0,1**.
* Impostare **1 Volume toccare**, **toccare Volume 2** e **toccare Volume 3** al **0.8**.
* Impostare **Volume audio originali** al **0,5**.

Le impostazioni precedenti configurano i parametri di Unity **AudioChorusFilter** consente di aggiungere tutti i vantaggi per la voce dell'utente.

* Nelle **utente vocale effetto**, espandere **Echo parametri**.
* Impostare **ritardo** a **300**
* Impostare **Decay Ratio** al **0.2**.
* Impostare **Volume audio originali** al **0**.

Le impostazioni precedenti configurano i parametri di Unity **AudioEchoFilter** utilizzata per determinare la voce dell'utente da restituire.

Lo script utente vocale effetto è responsabile per:

* Misurazione della distanza tra l'utente e la **GameObject** al quale è associato lo script.
* Che determina se l'utente è rivolta la **GameObject**.

L'utente deve essere rivolto il GameObject, indipendentemente dalla distanza, per l'effetto deve essere abilitata.

* Applicazione e configurazione di un' **AudioChorusFilter** e un **AudioEchoFilter** per il **AudioSource**.
* Disabilitare l'effetto Disabilitando i filtri.

Effetto vocale utente utilizza il componente Mic Stream Selector, dal [MixedRealityToolkit per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), per selezionare il flusso di qualità elevata vocali e distribuirla nel sistema audio di Unity.

* Nel **gerarchia** Pannello di selezione **responsabili**.
* Nel **Inspector** panel, espandere **gestore di Input vocale**.
* Nelle **gestore di Input vocale**, espandere **Underworld Mostra**.
* Change **alcuna funzione** al **UnderworldBase.OnEnable**.

![parola chiave: Underworld Show](images/showunderworld.png)

* Espandere **nascondere Underworld**.
* Change **alcuna funzione** al **UnderworldBase.OnDisable**.

![parola chiave: Nascondi Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Compilare e distribuire

* Come in precedenza, compilare il progetto in Unity e distribuzione in Visual Studio.

Dopo aver distribuita l'applicazione:

* Devono affrontare una superficie (parete, floor, tabella) e scelgo *"Mostra Underworld"*.

Verrà visualizzato il underworld e verrà nascoste tutte le altre vntana. Se non viene visualizzato il underworld, assicurarsi che si verificano una superficie del mondo reale.

* Approccio interno 1 metro di ologramma underworld e avviare discussioni.

Sono ora disponibili effetti audio per la voce dell'utente.

* Abbandoneranno l'underworld e notare come l'effetto non è più applicata.
* Pronunciare *"Nascondi Underworld"* per nascondere il underworld.

Sarà nascosto il underworld e verrà visualizzato nuovamente il vntana nascoste in precedenza.

## <a name="the-end"></a>La fine

La procedura è stata completata. Sono stati completati **SIG spaziali 220: Suono spaziale**.

Rimanere in ascolto per il mondo e portare le proprie esperienze accattivanti con suono!
