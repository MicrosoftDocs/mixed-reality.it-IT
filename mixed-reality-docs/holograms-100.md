---
title: Nozioni di base di MR 100 - Guida introduttiva a Unity
description: Informazioni su come creare la prima applicazione "hello world" di base di realtà mista.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: mista realtà, realtà mista di Windows, HoloLens, vr immersivi, mr, iniziare a usare, ologrammi, academy, esercitazione
ms.openlocfilehash: 1f4a5490383671fba694b386015ff6742d37241b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597562"
---
>[!NOTE]
>Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.  Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.  Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.  Essi verranno mantenute per continuare a utilizzare i dispositivi supportati. Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.  Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>Nozioni fondamentali di MR 100: Introduzione a Unity

Questa esercitazione illustrerà di creazione di un'app di base di realtà mista creata con Unity.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td>Nozioni fondamentali di MR 100: Introduzione a Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

* Un PC Windows 10 configurate con i valori corretti [sono installati gli strumenti](install-the-tools.md).

## <a name="chapter-1---create-a-new-project"></a>Capitolo 1 - creare un nuovo progetto

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Per compilare un'app con Unity, è necessario innanzitutto creare un progetto. Questo progetto è organizzato in alcune cartelle, la più importante dei quali è la cartella Assets. Questa è la cartella che contiene tutti gli asset che si importa da strumenti di creazione di contenuti digitali come Maya, Cinema Max 4D o Photoshop, tutto il codice creare con Visual Studio o l'editor di codice preferito, e un numero qualsiasi di file di contenuto che consente di creare Unity durante la composizione in background , animazioni e altri tipi di asset Unity nell'editor.

Per compilare e distribuire le app UWP, Unity è possibile esportare il progetto come una soluzione di Visual Studio che conterrà tutte le risorse necessarie e i file di codice.

1. Avviare Unity
2. Selezionare **New**
3. Immettere un nome di progetto (ad esempio "MixedRealityIntroduction")
4. Immettere un percorso per salvare il progetto
5. Verificare che il **3D** attiva/disattiva è selezionata
6. Selezionare **Crea progetto**

Complimenti, sono tutte le impostazioni per iniziare subito con le personalizzazioni di realtà mista.

## <a name="chapter-2---setup-the-camera"></a>Capitolo 2: configurazione della fotocamera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

La fotocamera principale di Unity gestisce l'head di rilevamento e stereoscopico per il rendering. Esistono alcune modifiche apportare a Main Camera per usarlo con realtà mista.
1. Selezionare File > nuova scena

In primo luogo, sarà più facile preparare l'app se si immagina la posizione iniziale dell'utente come (**X**: 0, **Y**: 0, **Z**: 0). Poiché la fotocamera principale è rilevamento movimento della testina dell'utente, è possibile impostare la posizione iniziale dell'utente, impostare la posizione iniziale della fotocamera principale.
1. Selezionare **Main Camera** nel **gerarchia** pannello
2. Nel **Inspector** panel, trovare il **trasformare** componente e modifica i **posizione** da (**X**: 0, **Y**: 1, **Z**: da -10) a (**X**: 0, **Y**: 0, **Z**: 0)

In secondo luogo, lo sfondo di fotocamera predefinito richiede molta attenzione.

**Per le applicazioni di HoloLens**, del mondo reale deve essere visualizzato dietro a tutti gli elementi della fotocamera esegue il rendering, non una trama Skybox.
1. Con il **Main Camera** ancora selezionato nel **gerarchia** panel, trovare il **fotocamera** componente nel **Inspector** pannello e modificare il **Cancella flag** elenco a discesa dal **Skybox** al **colore a tinta unita**.
2. Selezionare il **sfondo** selezione dei colori e modifica il **RGBA** valori su (0, 0, 0, 0)

**Per le applicazioni di realtà mista destinate a auricolari immersive**, è possibile usare la trama Skybox predefinito che fornisce Unity.
1. Con il **Main Camera** ancora selezionato nel **gerarchia** panel, trovare il **fotocamera** componente nel **Inspector** pannello e mantenere il **Cancella flag** elenco a discesa per **Skybox**.

In terzo luogo, invia i tuoi commenti prendere in considerazione il piano di ritaglio quasi in Unity e impedire che gli oggetti venga eseguito il rendering troppo vicino agli utenti gli occhi quando un utente si avvicina a un oggetto o un oggetto sta per raggiungere un utente.

**Per le applicazioni di HoloLens**, il piano di ritaglio vicino può essere impostato sul [HoloLens consigliato](camera-in-unity.md#clip-planes) 0.85 metri.
1. Con il **Main Camera** ancora selezionato nel **gerarchia** panel, trovare il **fotocamera** componente nel **Inspector** pannello e modificare il **Quasi il piano di ritaglio** campo il valore predefinito **0.3** a di HoloLens consigliato **0,85**.

**Per le applicazioni di realtà mista destinate a auricolari immersive**, è possibile usare l'impostazione predefinita che consente di Unity.
1. Con il **Main Camera** ancora selezionato nel **gerarchia** panel, trovare il **fotocamera** componente nel **Inspector** pannello e mantenere il **Quasi il piano di ritaglio** campo sul valore predefinito **0.3**.

Infine, invia i tuoi commenti salvare lo stato di avanzamento fino ad ora. Per salvare le modifiche apportate alla scena, selezionare **File > Salva scena con nome**, denominare la scena **Main**e selezionare **Salva**.

## <a name="chapter-3---setup-the-project-settings"></a>Capitolo 3 - Configurazione impostazioni del progetto

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

In questo capitolo, si imposterà alcune impostazioni del progetto Unity aiutarci a Windows Holographic SDK per lo sviluppo di destinazione. Si imposterà inoltre alcune impostazioni di qualità per la nostra applicazione. Infine, si garantirà che la destinazioni di compilazione siano impostate su Windows Store.

### <a name="unity-performance-and-quality-settings"></a>Impostazioni di qualità e prestazioni di Unity

**Impostazioni di qualità di Unity per HoloLens**

![Impostazioni di qualità di Unity per HoloLens](images/qualitysettings.png) 

Poiché la gestione di ad alta frequenza dei fotogrammi in HoloLens è così importante, è opportuno le impostazioni di qualità ottimizzate per prestazioni ottimali. Per altre informazioni sulle prestazioni, [raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md).
1. Selezionare **Modifica > impostazioni del progetto > qualità**
2. Selezionare il **elenco a discesa** sotto il **Windows Store** logo e selezionare **molto bassa**. Si saprà che l'impostazione viene applicata in modo corretto quando la casella nella colonna di Windows Store e riga più veloce è verde.

**Per le applicazioni di realtà mista destinate agli schermi bloccati**, è possibile lasciare le impostazioni di qualità sui valori predefiniti.

### <a name="target-windows-10-sdk"></a>Target Windows 10 SDK

**Destinazione Windows Holographic SDK**

![Destinazione Windows Holographic SDK](images/xrsettings.png) 

Dobbiamo informare Unity che deve creare l'app è in corso per esportare un' [vista immersiva](app-views.md) invece di una visualizzazione 2D. Abbiamo tale scopo, abilitare il supporto di realtà virtuale su Unity destinate a Windows 10 SDK.
1. Passare a **Modifica > impostazioni del progetto > Player**.
2. Nel **Pannello di controllo** per le impostazioni del giocatore, selezionare la **Windows Store** icona.
3. Espandere la **XR impostazioni** gruppo.
4. Nel **Rendering** sezione controllo la **realtà virtuale supportato** casella di controllo per aggiungere un nuovo **gli SDK di realtà virtuale** elenco.
5. Verificare che **realtà mista di Windows** visualizzato nell'elenco. In caso contrario, selezionare la **+** pulsante nella parte inferiore dell'elenco e scegliere **realtà mista di Windows**.

>[!NOTE]
>Se non viene visualizzato il **Windows Store** icona, ricontrollare per verificare che sia selezionato il back-end per la creazione di script di Windows Store .NET prima dell'installazione. In caso contrario, potrebbe essere necessario reinstallare Unity con la corretta installazione di Windows.

**Verificare la configurazione di .NET**

![Verificare la configurazione di .NET](images/configoptions-375px.png)

1. Passare a **Modifica > Impostazioni di progetto > Player** (è ancora possibile avere questo nel passaggio precedente).
2. Nel **Pannello di controllo** per le impostazioni del giocatore, selezionare la **Windows Store** icona.
3. Nel **altre impostazioni** Configuration sezione, assicurarsi che **Scripting back-end** è impostato su **.NET**

Processo eccezionale su come ottenere tutte le impostazioni di progetto applicate. Aggiungere quindi invia i tuoi commenti ologramma!

## <a name="chapter-4---create-a-cube"></a>Capitolo 4 - creare un cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Creazione di un cubo nel progetto Unity è proprio come la creazione di qualsiasi altro oggetto in Unity. Inserimento di un cubo davanti all'utente è semplice perché viene eseguito il mapping di sistema di coordinate di Unity con il mondo reale, in cui un misuratore in Unity è circa un contatore nel mondo reale.
1. Nell'angolo superiore sinistro del **gerarchia** pannello, seleziona la **Create** elenco a discesa e scegliere **oggetto 3D > cubo**.
2. Selezionare quella appena creata **cubo** nel **gerarchia** pannello
3. Nel **Inspector** trovare il **trasformare** componente e modificare **posizione** a (**X**: 0, **Y**: 0, **Z**: 2). *Si posiziona il cubo 2 metri davanti a posizione iniziale dell'utente.*
4. Nel **trasformare** componente, change **rotazione** per (**X**: 45, **Y**: 45, **Z**: 45) e cambiare **scalabilità** a (**X**: 0.25, **Y**: 0.25, **Z**: 0.25). *Questa configurazione è possibile il cubo e visualizzare i contatori 0,25.*
5. Per salvare le modifiche apportate alla scena, selezionare **File > Salva scena**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capitolo 5: verificare sul dispositivo dall'editor di Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Ora che abbiamo creato il cubo, è possibile eseguire un rapido controllo nel dispositivo. È possibile eseguire questa operazione direttamente dall'editor di Unity.

### <a name="initial-setup"></a>Configurazione iniziale
1. Nel computer, di sviluppo in Unity, aprire **File > Build Settings** finestra.
2. Change **piattaforma** al **Universal Windows Platform** e fare clic su **commutatore piattaforma in uso**

### <a name="for-hololens-use-unity-remoting"></a>Per HoloLens usare la comunicazione remota di Unity
1. Nella finestra di HoloLens, installare ed eseguire la [Holographic Remoting Player](holographic-remoting-player.md), disponibile da Store di Windows. Per avviare l'applicazione nel dispositivo, entrare in uno stato di attesa ed mostrano l'indirizzo IP del dispositivo. Annotare l'indirizzo IP.
2. Aprire **finestra > XR > emulazione Holographic**.
3. Change **modalità di emulazione** da **None** al **remoto al dispositivo**.
4. Nelle **computer remoto**, immettere l'indirizzo IP di HoloLens indicato in precedenza.
5. Fare clic su **Connetti**.
6. Verificare che il **lo stato di connessione** assume il colore verde **connesso**.
7. A questo punto è possibile ora fare clic **riprodurre** nell'editor di Unity.

A questo punto sarà possibile visualizzare il cubo nel dispositivo e nell'editor. È possibile sospendere, controllare gli oggetti e il debug proprio come si esegue un'app nell'editor, perché si tratta essenzialmente ciò che accade, ma con video, audio e input dei dispositivi e viceversa trasmessi attraverso la rete tra il computer host e il dispositivo.

### <a name="for-other-mixed-reality-supported-headsets"></a>Per altri realtà mista supportati auricolari

1. Connettere le cuffie al PC usando il cavo USB e le HDMI di sviluppo o visualizzare il cavo di porta.
2. Avviare il **portale di realtà mista** e assicurarsi di aver completato la prima esperienza di esecuzione.
3. Da Unity, è ora possibile premere il pulsante di riproduzione.

A questo punto sarà possibile visualizzare il rendering di cubo nel visore VR realtà mista e nell'editor.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capitolo 6: creare e distribuire al dispositivo da Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

A questo punto siamo pronti compilare il progetto di Visual Studio e distribuire il dispositivo di destinazione.

### <a name="export-to-the-visual-studio-solution"></a>Esportare in soluzione di Visual Studio
1.  Aprire **File > Build Settings** finestra.
2.  Fare clic su **aggiungere scene Open** per aggiungere la scena.
3.  Change **piattaforma** al **Universal Windows Platform** e fare clic su **commutatore piattaforma**.
4.  Nelle **Windows Store** assicurarsi che le impostazioni, **SDK** viene **10 universale**.
5.  Per il dispositivo di destinazione, lasciare **qualsiasi dispositivo** bloccati consente di visualizzare o passa a **HoloLens**.
6.  **Tipo di compilazione UWP** deve essere **D3D**.
7.  **UWP SDK** potrebbe essere lasciati **installata più recente**.
8.  Controllare **Unity C# progetti** nella fase di debug.
9.  Fai clic su **Compila**.
10. In Esplora file, fare clic su **nuova cartella** e denominare la cartella **"App"**.
11. Con il **App** cartella selezionata, fare clic sui **Seleziona cartella** pulsante.
12. Quando l'operazione Unity viene eseguita la compilazione, verrà visualizzata una finestra di Esplora File di Windows.
13. Aprire il **App** cartella in Esplora file.
14. Aprire la soluzione di Visual Studio generata (MixedRealityIntroduction.sln in questo esempio)

### <a name="compile-the-visual-studio-solution"></a>Compilare la soluzione di Visual Studio

Infine, si verrà compilare la soluzione di Visual Studio esportata, distribuirlo e provarlo nel dispositivo.
1. Usando la barra degli strumenti superiore in Visual Studio, modificare la destinazione dal **Debug** a **Release** e da **ARM** a **X86**.

Le istruzioni sono diverse per la distribuzione in un dispositivo e l'emulatore. Seguire le istruzioni che soddisfano la configurazione.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Distribuire al dispositivo di realtà mista tramite Wi-Fi
1. Fare clic sulla freccia accanto al **computer locale** pulsante e modificare la destinazione di distribuzione per **computer remoto**.
2. Immettere l'indirizzo IP del dispositivo di realtà mista e cambiare **modalità di autenticazione** universale (protocollo non crittografato) per HoloLens e **Windows** per altri dispositivi.
3. Fare clic su **Debug > Avvia senza eseguire debug**.

**Per HoloLens**, se questa è la prima volta che si distribuisce nel dispositivo, sarà necessario coppia [con Visual Studio](using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Distribuire al dispositivo di realtà mista tramite USB

Assicurarsi che nel dispositivo sia connesso tramite il cavo USB.
1. **Per HoloLens**, fare clic sulla freccia accanto al **computer locale** pulsante e modificare la destinazione di distribuzione per **dispositivo**.
2. **Per i dispositivi bloccati collegati al computer di destinazione**, mantenere l'impostazione nel computer locale. Assicurarsi di aver la **portale di realtà mista** in esecuzione.
3. Fare clic su **Debug > Avvia senza eseguire debug**.

### <a name="deploy-to-emulator"></a>Distribuzione emulatore
1. Fare clic sulla freccia accanto al **periferica** pulsante e dall'elenco a discesa selezionare **emulatore HoloLens**.
2. Fare clic su **Debug > Avvia senza eseguire debug**.

### <a name="try-out-your-app"></a>Provare l'app

Ora che l'app viene distribuita, provare a spostare tutto il cubo e osservare che il messaggio rimane nel mondo sempre a disposizione.

## <a name="see-also"></a>Vedere anche
* [Panoramica sullo sviluppo per Unity](unity-development-overview.md)
* [Le procedure consigliate per l'uso di Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [MR Basics 101](holograms-101.md)
* [Nozioni di base di MR 101E](holograms-101e.md)
