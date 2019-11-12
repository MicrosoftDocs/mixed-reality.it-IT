---
title: Nozioni fondamentali 100-Introduzione a Unity
description: Informazioni su come creare la prima applicazione "Hello World" di base per la realtà mista.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realtà mista, realtà mista di Windows, HoloLens, immersiva, VR, Mr, introduzione, ologramma, Accademia, esercitazione
ms.openlocfilehash: 0600383b3cca3f580f014597217afc6ae78836dd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926638"
---
>[!NOTE]
>Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.  Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Verranno mantenuti per continuare a usare i dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](mrlearning-base.md) .

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>Nozioni fondamentali 100: Introduzione a Unity

Questa esercitazione illustra come creare un'app di base per realtà mista compilata con Unity.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Nozioni fondamentali 100: Introduzione a Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurato con gli [strumenti corretti installati](install-the-tools.md).

## <a name="chapter-1---create-a-new-project"></a>Capitolo 1-creare un nuovo progetto

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Per compilare un'app con Unity, è prima di tutto necessario creare un progetto. Questo progetto è organizzato in alcune cartelle, il più importante dei quali è la cartella assets. Si tratta della cartella che include tutte le risorse importate da strumenti per la creazione di contenuti digitali, ad esempio Maya, max cinema 4D o Photoshop, tutto il codice creato con Visual Studio o l'editor di codice preferito e un numero qualsiasi di file di contenuto creati da Unity durante la composizione di scene , animazioni e altri tipi di asset Unity nell'editor.

Per compilare e distribuire app UWP, Unity può esportare il progetto come una soluzione di Visual Studio che conterrà tutti i file di asset e di codice necessari.

1. Avvia Unity
2. Seleziona **nuovo**
3. Immettere un nome di progetto (ad esempio "MixedRealityIntroduction")
4. Immettere un percorso per salvare il progetto
5. Verificare che sia selezionato l'interruttore **3D**
6. Selezionare **Crea progetto**

Il programma di installazione consente di iniziare subito a usare le personalizzazioni della realtà mista.

## <a name="chapter-2---setup-the-camera"></a>Capitolo 2: configurare la fotocamera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

La videocamera principale di Unity gestisce il rilevamento Head e il rendering stereoscopico. Ci sono alcune modifiche da apportare alla fotocamera principale per utilizzarlo con realtà mista.

1. Seleziona file > nuova scena

Per prima cosa, sarà più facile stendere l'app se si immagina la posizione iniziale dell'utente come (**X**: 0, **Y**: 0, **Z**: 0). Poiché la fotocamera principale tiene traccia del movimento della testa dell'utente, è possibile impostare la posizione iniziale dell'utente impostando la posizione iniziale della fotocamera principale.

1. Selezionare la **fotocamera principale** nel pannello **gerarchia**
2. Nel pannello **Inspector** trovare il componente **Transform** e modificare la **posizione** da (**x**: 0, **Y**: 1, **Z**:-10) a (**x**: 0, **Y**: 0, **Z**: 0)

In secondo luogo, lo sfondo predefinito della fotocamera richiede un certo pensiero.

**Per le applicazioni HoloLens**, il mondo reale dovrebbe comparire dietro tutto il rendering della fotocamera, non una trama skybox.

1. Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e modificare l'elenco a discesa **Clear Flags** da **SKYBOX** a **Solid Color**.
2. Selezionare la selezione dei colori di **sfondo** e modificare i valori di **RGBA** in (0, 0, 0, 0)

**Per le applicazioni di realtà miste destinate a auricolari immersivi**, è possibile usare la trama SKYBOX predefinita fornita da Unity.

1. Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e mantenere l'elenco a discesa **Clear Flags** su **SKYBOX**.

In terzo luogo, consideriamo il piano di ritaglio vicino in Unity, evitando che gli oggetti vengano visualizzati troppo vicino agli occhi degli utenti quando un utente si avvicina a un oggetto o a un oggetto che si avvicina a un utente.

**Per le applicazioni HoloLens**, il piano di ritaglio vicino può essere impostato su HoloLens 0,85 metri [consigliati](camera-in-unity.md#clip-planes) .

1. Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e modificare il campo **near clip Plane** dal valore predefinito **0,3** alla HoloLens consigliata **0,85** .

**Per le applicazioni di realtà miste destinate a auricolari immersivi**, è possibile usare l'impostazione predefinita fornita da Unity.

1. Con la **fotocamera principale** ancora selezionata nel pannello **gerarchia** , trovare il componente della **fotocamera** nel pannello **Inspector** e mantenere il campo del **piano di ritaglio vicino** al valore predefinito **0,3**.

Infine, dobbiamo salvare il nostro progresso fino a questo punto. Per salvare le modifiche apportate alla scena, selezionare **File > Salva scena come**, assegnare un nome alla scena **principale**e selezionare **Salva**.

## <a name="chapter-3---setup-the-project-settings"></a>Capitolo 3: configurare le impostazioni del progetto

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

In questo capitolo vengono impostate alcune impostazioni di progetto Unity che ci aiutano a usare Windows Olografic SDK per lo sviluppo. Vengono inoltre impostate alcune impostazioni di qualità per l'applicazione. Infine, si assicurerà che le destinazioni di compilazione siano impostate su Windows Store.

### <a name="unity-performance-and-quality-settings"></a>Impostazioni delle prestazioni e della qualità di Unity

**Impostazioni della qualità di Unity per HoloLens**

![Impostazioni della qualità di Unity per HoloLens](images/qualitysettings.png)

Poiché la gestione di un framerate elevato su HoloLens è così importante, è opportuno ottimizzare le impostazioni di qualità per ottenere prestazioni più rapide. Per informazioni più dettagliate sulle prestazioni, [consigli sulle prestazioni per Unity](performance-recommendations-for-unity.md).

1. Selezionare **modifica > impostazioni progetto > qualità**
2. Selezionare l' **elenco a discesa** sotto il logo di **Windows Store** e selezionare **molto basso**. Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna Windows Store e con **una riga molto bassa** è verde.

**Per le applicazioni di realtà miste destinate a schermi**bloccati, è possibile lasciare le impostazioni di qualità ai valori predefiniti.

### <a name="target-windows-10-sdk"></a>Windows 10 SDK di destinazione

**SDK Windows olografico di destinazione**

![SDK Windows olografico di destinazione](images/xrsettings.png)

È necessario informare Unity che l'app che si sta tentando di esportare deve creare una [visualizzazione immersiva](app-views.md) anziché una visualizzazione 2D. Questa operazione viene eseguita abilitando il supporto della realtà virtuale in Unity per Windows 10 SDK.

1. Passare a **Edit > Settings Project > Player**.
2. Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .
3. Espandere il gruppo di **Impostazioni XR** .
4. Nella sezione **rendering** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco **SDK di realtà virtuale** .
5. Verificare che l'opzione **realtà mista di Windows** sia presente nell'elenco. In caso contrario, selezionare il pulsante **+** nella parte inferiore dell'elenco e scegliere **realtà mista di Windows**.

>[!NOTE]
>Se l'icona di **Windows Store** non è visualizzata, verificare di aver selezionato il back-end di scripting .NET di Windows Store prima di procedere all'installazione. In caso contrario, potrebbe essere necessario reinstallare Unity con l'installazione di Windows corretta.

**Verificare la configurazione .NET**

![Verificare la configurazione .NET](images/configoptions-375px.png)

1. Passare a **Edit > Settings (Impostazioni progetto) > Player** (è possibile continuare a eseguire questa operazione dal passaggio precedente).
2. Nel **pannello Inspector** per le impostazioni del lettore selezionare l'icona di **Windows Store** .
3. Nella sezione **altre impostazioni** di configurazione, assicurarsi che **lo scripting backend** sia impostato su **.NET** .

Un processo straordinario per il recupero di tutte le impostazioni del progetto applicate. Quindi, aggiungiamo un ologramma!

## <a name="chapter-4---create-a-cube"></a>Capitolo 4-creazione di un cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

La creazione di un cubo nel progetto Unity è simile alla creazione di qualsiasi altro oggetto in Unity. Posizionare un cubo davanti all'utente è facile perché il sistema di coordinate di Unity è mappato al mondo reale, in cui un contatore in Unity è approssimativamente un contatore nel mondo reale.

1. Nell'angolo in alto a sinistra del pannello **gerarchia** selezionare l'elenco a discesa **Crea** e scegliere **oggetto 3D > cubo**.
2. Selezionare il **cubo** appena creato nel pannello **gerarchia**
3. Nel **controllo** trovare il componente **Transform** e modificare **position** in (**X**: 0, **Y**: 0, **Z**: 2). *Questa operazione posiziona il cubo 2 metri davanti alla posizione iniziale dell'utente.*
4. Nel componente **trasformazione** modificare la **rotazione** in (**x**: 45, **Y**: 45, **Z**: 45) e modificare la **scala** in (**X**: 0,25, **Y**: 0,25, **Z**: 0,25). *Questa operazione consente di ridimensionare il cubo a 0,25 metri.*
5. Per salvare le modifiche apportate alla scena, selezionare **File > Salva scena**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capitolo 5-verificare nel dispositivo dall'editor Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

A questo punto, dopo aver creato il cubo, è possibile eseguire un controllo rapido nel dispositivo. Questa operazione può essere eseguita direttamente dall'editor di Unity.

### <a name="initial-setup"></a>Configurazione iniziale

1. Nel computer di sviluppo, in Unity, aprire **File > finestra impostazioni di compilazione** .
2. Modificare la **piattaforma** in **piattaforma UWP (Universal Windows Platform)** e fare clic su Cambia **piattaforma**

### <a name="for-hololens-use-unity-remoting"></a>Per HoloLens usare la comunicazione remota di Unity

1. In HoloLens installare ed eseguire il lettore di [comunicazione remota olografico](holographic-remoting-player.md), disponibile in Windows Store. Avviare l'applicazione nel dispositivo, che entrerà in uno stato di attesa e visualizzerà l'indirizzo IP del dispositivo. Prendere nota dell'indirizzo IP.
2. Aprire la **finestra > XR > emulazione olografica**.
3. Modificare la **modalità di emulazione** da **Nessuna** a **remota a dispositivo**.
4. In **computer remoto**, immettere l'indirizzo IP della HoloLens annotata in precedenza.
5. Fai clic su **Connetti**.
6. Verificare che lo **stato della connessione** venga modificato in verde **connesso**.
7. A questo punto è possibile fare clic su **Play** nell'editor di Unity.

A questo punto sarà possibile visualizzare il cubo nel dispositivo e nell'editor. È possibile sospendere, ispezionare gli oggetti ed eseguire il debug in modo analogo all'esecuzione di un'app nell'editor, perché si tratta essenzialmente di ciò che accade, ma con video, audio e input del dispositivo trasmessi attraverso la rete tra il computer host e il dispositivo.

### <a name="for-other-mixed-reality-supported-headsets"></a>Per gli altri tipi di auricolari supportati dalla realtà mista

1. Connettere la cuffia al PC di sviluppo usando il cavo USB e il cavo porta HDMI o schermo.
2. Avviare il **portale di realtà mista** e assicurarsi di avere completato la prima esperienza di esecuzione.
3. Da Unity è ora possibile premere il pulsante Play.

A questo punto, sarà possibile visualizzare il rendering dei cubi nell'auricolare della realtà mista e nell'editor.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capitolo 6: creare e distribuire nel dispositivo da Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

A questo punto è possibile compilare il progetto in Visual Studio e distribuirlo nel dispositivo di destinazione.

### <a name="export-to-the-visual-studio-solution"></a>Esporta nella soluzione di Visual Studio

1.  Aprire **File > finestra impostazioni di compilazione** .
2.  Fare clic su **Aggiungi scene aperte** per aggiungere la scena.
3.  Modificare la **piattaforma** in **piattaforma UWP (Universal Windows Platform)** e fare clic su **Cambia piattaforma**.
4.  Nelle impostazioni di **Windows Store** assicurarsi che **SDK** sia **universale 10**.
5.  Per il dispositivo di destinazione, lasciare a **qualsiasi dispositivo** per visualizzare le schermate o passare a **HoloLens**.
6.  Il **tipo di compilazione UWP** deve essere **D3D**.
7.  L' **SDK di UWP** potrebbe essere rimasto **installato più di recente**.
8.  Controllare **i C# progetti Unity** in fase di debug.
9.  Fai clic su **Compila**.
10. In Esplora file fare clic su **nuova cartella** e denominare la cartella **"app"** .
11. Con la cartella **app** selezionata, fare clic sul pulsante **Seleziona cartella** .
12. Al termine della compilazione di Unity, viene visualizzata una finestra Esplora file di Windows.
13. Aprire la cartella dell' **app** in Esplora file.
14. Aprire la soluzione di Visual Studio generata (MixedRealityIntroduction. sln in questo esempio)

### <a name="compile-the-visual-studio-solution"></a>Compilare la soluzione di Visual Studio

Infine, la soluzione di Visual Studio esportata verrà compilata, distribuita e provata nel dispositivo.

1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione da **debug** a **Release** e da **ARM** a **x86**.

Le istruzioni sono diverse per la distribuzione in un dispositivo rispetto all'emulatore. Seguire le istruzioni corrispondenti alla configurazione.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Eseguire la distribuzione in un dispositivo a realtà mista tramite Wi-Fi

1. Fare clic sulla freccia accanto al pulsante **locale del computer** e modificare la destinazione di distribuzione in **computer remoto**.
2. Immettere l'indirizzo IP del dispositivo in realtà mista e modificare la **modalità di autenticazione** in Universal (protocollo non crittografato) per HoloLens e **Windows** per altri dispositivi.
3. Fare clic su **debug > avvia senza eseguire debug**.

**Per HoloLens**, se questa è la prima volta che si esegue la distribuzione nel dispositivo, sarà necessario eseguire l'associazione [con Visual Studio](using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Distribuisci in un dispositivo a realtà mista tramite USB

Verificare che il dispositivo sia collegato tramite il cavo USB.

1. **Per HoloLens**, fare clic sulla freccia accanto al pulsante **locale del computer** e modificare la destinazione di distribuzione nel **dispositivo**.
2. **Per individuare i dispositivi bloccati collegati al PC**, impostare il computer locale. Assicurarsi che sia in esecuzione il **portale di realtà mista** .
3. Fare clic su **debug > avvia senza eseguire debug**.

### <a name="deploy-to-emulator"></a>Distribuisci nell'emulatore

1. Fare clic sulla freccia accanto al pulsante **Device (dispositivo** ) e nell'elenco a discesa selezionare **HoloLens Emulator (emulatore**).
2. Fare clic su **debug > avvia senza eseguire debug**.

### <a name="try-out-your-app"></a>Provare l'app

Ora che l'app è stata distribuita, provare a spostarsi in tutto il cubo e osservare che rimane nel mondo davanti all'utente.

## <a name="see-also"></a>Vedi anche

* [Panoramica dello sviluppo per Unity](unity-development-overview.md)
* [Procedure consigliate per l'uso con Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Nozioni fondamentali 101](holograms-101.md)
* [Nozioni di base su 101E](holograms-101e.md)
