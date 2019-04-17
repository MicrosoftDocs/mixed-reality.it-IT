---
title: Panoramica sullo sviluppo per Unity
description: Recupero di iniziare a compilare mista le App per realtà in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mista realtà, sviluppo, Guida introduttiva, nuovo progetto, portabilità, funzionalità, fotocamera, simulazione, emulazione, documentazione
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604549"
---
# <a name="unity-development-overview"></a>Panoramica sullo sviluppo per Unity

Il percorso più veloce alla compilazione un' [app per realtà mista](app-views.md) riguarda [Unity](http://aka.ms/HoloLensUnity). È consigliabile eseguire il tempo necessario per esplorare le [esercitazioni di Unity](https://unity3d.com/learn/tutorials). Se è necessario asset, Unity ha una serie completa [Asset Store](https://www.assetstore.unity3d.com/). Dopo aver creato una conoscenza di base di Unity, è possibile visitare il [Academy di realtà mista](academy.md) conoscere le specifiche di sviluppo di applicazioni di realtà mista con Unity. Assicurarsi di visitare il [forum di realtà mista di Unity](http://forum.unity3d.com/forums/hololens.102/) di interagire con il resto della community di creazione di App di realtà mista in Unity e trovare soluzioni ai problemi si verificano.

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Porting di un'app esistente di Unity in Windows Mixed Reality

Se si dispone di un progetto Unity esistente che sta eseguendo il porting in Windows Mixed Reality, seguire le [Guida al porting di Unity](porting-guides.md) per iniziare.

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a>Configurazione di un nuovo progetto Unity per realtà mista di Windows

Per iniziare a compilare le App per realtà mista con Unity, innanzitutto [installare gli strumenti](install-the-tools.md). Se si sarà destinazione auricolari coinvolgenti di realtà mista di Windows anziché a HoloLens, è necessario una versione speciale di Unity per il momento.

Se appena stato creato un nuovo progetto Unity, sono disponibili un piccolo set di impostazioni di Unity, è necessario modificare per realtà mista di Windows, suddivise in due categorie: al progetto e per ogni scena.

### <a name="per-project-settings"></a>Impostazioni per ogni progetto

Per impostare come destinazione la realtà mista di Windows, è necessario innanzitutto impostare il progetto di Unity per l'esportazione come app Universal Windows Platform:
1. Selezionare **File > Impostazioni di compilazione...**
2. Selezionare **Universal Windows Platform** nella piattaforma di elenco e fare clic su **commutatore piattaforma**
3. Impostare **SDK** a **10 universali**
4. Impostare **dispositivo di destinazione** al **qualsiasi dispositivo** supportano auricolari immersive o passare a **HoloLens**
5. Impostare **tipo di compilazione** a **D3D**
6. Impostare **UWP SDK** a **installata più recente**

È quindi necessario informare Unity che deve creare l'app è in corso per esportare un' [vista immersiva](app-views.md) invece di una visualizzazione 2D. Ciò è possibile abilitare "Supportata di realtà virtuale":
1. Dal **le impostazioni di compilazione...**  finestra, aprire **le impostazioni del giocatore...**
2. Selezionare il **le impostazioni per la Universal Windows Platform** scheda
3. Espandere la **XR impostazioni** gruppo
4. Nel **impostazioni XR** sezione, verificare il **realtà virtuale supportato** casella di controllo per aggiungere il **dispositivi per realtà virtuale** elenco.
5. Nel **impostazioni XR** gruppo, verificare che **"Windows Mixed Reality"** viene elencato come un dispositivo supportato. (questa verifica può sembrare come "Windows Holographic" nelle versioni precedenti di Unity)

L'app ora è possibile eseguire spaziali input e base per il rendering holographic. Per andare oltre e sfruttare alcune funzionalità, l'app deve dichiarare le funzionalità appropriate nel relativo manifesto. Le dichiarazioni del manifesto possono essere rese Unity in modo che vengono inclusi in ogni esportazione progetto successivo. L'impostazione si trovano **Player Settings > impostazioni per la Universal Windows Platform > Impostazioni di pubblicazione > funzionalità**. Le funzionalità applicabili per l'abilitazione di uso comune le API di Unity per realtà mista sono:

|  Capability  |  API che richiedono funzionalità | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (accedere al [mapping spaziale](spatial-mapping.md) trame in HoloLens)&mdash;*alcuna funzionalità necessarie per rilevamento spaziale generale delle cuffie* | 
|  WebCam  |  PhotoCapture e VideoCapture | 
|  PicturesLibrary o VideosLibrary  |  PhotoCapture o VideoCapture, rispettivamente (quando si archiviano il contenuto acquisito) | 
|  Microfono  |  VideoCapture (durante l'acquisizione audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e usare il Profiler di Unity) | 

**Impostazioni di qualità di Unity**

![Impostazioni di qualità di Unity](images/unityqualitysettings-350px.png)<br>
*Impostazioni di qualità di Unity*

HoloLens ha una GPU di classi di dispositivi mobili. Se l'app è destinata a HoloLens, è opportuno le impostazioni di qualità ottimizzate per prestazioni più veloci per garantire che manteniamo framerate completo:
1. Selezionare **Modifica > impostazioni del progetto > qualità**
2. Selezionare il **elenco a discesa** sotto il **Windows Store** logo e selezionare **Fastest**. È quindi possibile sapere l'impostazione viene applicata in modo corretto quando la casella nella colonna di Windows Store e **Fastest** riga è di colore verde.

### <a name="per-scene-settings"></a>Impostazioni per ogni scena

**Impostazioni videocamera di Unity**

![Impostazioni videocamera di Unity](images/unitycamerasettings.png)<br>
*Impostazioni videocamera di Unity*

Dopo aver abilitato la casella di controllo "Realtà virtuale supportati", il [fotocamera Unity](camera-in-unity.md) componente gestisce [head rilevamento e il rendering stereoscopico](rendering.md). Non è necessario sostituirlo con una fotocamera personalizzata per eseguire questa operazione.

Se l'app è destinata a HoloLens in particolare, esistono alcune impostazioni che devono essere modificati per ottimizzare le visualizzazioni trasparente del dispositivo, in modo che l'app sarà visibile attraverso al mondo fisico:
1. Nel **gerarchia**, selezionare il **Main Camera**
2. Nel **Inspector** panel, impostare la trasformazione **posizione** al **0, 0, 0** in modo che la posizione di inizio utenti inizia in corrispondenza dell'origine mondo di Unity.
3. Change **cancellare i flag** al **colore a tinta unita**.
4. Modifica il **sfondo** colore **RGBA 0,0,0,0**. Nero esegue il rendering come trasparente nell'HoloLens.
5. Change **ritaglio piani - quasi** per il [HoloLens consigliato](camera-in-unity.md#clip-planes) 0,85 (metri).

Se si elimina e crea una nuova fotocamera, assicurarsi che sia la fotocamera **tag** come **MainCamera**.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Aggiunta di input e le funzionalità di realtà mista

Dopo aver configurato il progetto come descritto in precedenza, oggetti di gioco Unity standard (ad esempio la fotocamera) verranno visualizzati immediatamente per un **esperienza su scala seduto**, con la posizione della fotocamera viene aggiornata automaticamente come l'utente sposta propria testa attraverso il mondo.

Aggiunta del supporto per le funzionalità di realtà mista di Windows, ad esempio [fasi spaziali](coordinate-systems.md#spatial-coordinate-systems), [movimenti, i controller di movimento](gestures-and-motion-controllers-in-unity.md) oppure [input vocale](voice-input-in-unity.md) avviene tramite le API incorporate direttamente in Unity.

Il primo passaggio necessario per rivedere le [esperienza Scale](coordinate-systems.md) che può avere come destinazione l'app:
* Se si sta cercando di creare un **orientamento sola** o **scalabilità seduto esperienza**, è necessario impostare Unity del rilevamento tipo dello spazio a [fermo](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se si sta cercando di creare un **permanente-scale** o **esperienza su scala chat room**, è necessario assicurarsi di Unity spazio tipo di rilevamento è stata impostata su [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se si sta cercando di creare un **su scala mondiale** esperienza in HoloLens, consentire agli utenti di effettuare il roaming oltre i contatori di 5, è necessario utilizzare il [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) componente.

Tutti i componenti fondamentali per le app di realtà mista vengono esposte in modo coerente con altre API di Unity:
* [Fotocamera](camera-in-unity.md)
* [Sistemi di coordinate](coordinate-systems-in-unity.md)
* [Sguardo](gaze-in-unity.md)
* [I movimenti e controller di movimento](gestures-and-motion-controllers-in-unity.md)
* [Input vocale](voice-input-in-unity.md)
* [Persistenza](persistence-in-unity.md)
* [Spaziale audio](spatial-sound-in-unity.md)
* [Mapping spaziale](spatial-mapping-in-unity.md)

Sono disponibili altre funzionalità chiave che molte app di realtà mista desidera usare, che sono visualizzate anche per le app Unity:
* [Esperienze condivise](shared-experiences-in-unity.md)
* [Fotocamera individuabile](locatable-camera-in-unity.md)
* [Punto di stato attivo](focus-point-in-unity.md)
* [Perdita di rilevamento](tracking-loss-in-unity.md)
* [Tastiera](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Esecuzione del progetto Unity in un dispositivo reale o simulato

Una volta il progetto Unity holographic pronti per eseguire il test, il passaggio successivo consiste [esportare e compilare una soluzione di Visual Studio a Unity](exporting-and-building-a-unity-visual-studio-solution.md).

Con tale soluzione di Visual Studio a disposizione, è possibile quindi eseguire l'app in uno dei tre modi, usando un dispositivo reale o simulato:
* [Distribuire un auricolare immersiva reale, HoloLens o realtà mista di Windows](using-visual-studio.md)
* [Distribuire l'emulatore di HoloLens](using-the-hololens-emulator.md)
* [Distribuire il simulatore immersive visore VR realtà mista di Windows](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentazione di Unity

Oltre a questa documentazione disponibile in Windows Dev Center, Unity installa la documentazione per la funzionalità di realtà mista di Windows con l'Editor di Unity. Unity fornita documentazione include due sezioni separate:
1. **Riferimento di scripting di Unity**
    * In questa sezione della documentazione contiene i dettagli dell'API di scripting che consente di Unity.
    * Accessibile dall'Editor di Unity tramite **Guida > riferimento agli script**
2. **Manuale di Unity**
    * Questo manuale è progettato per scoprire come usare Unity, dalle tecniche di base fino ad avanzate.
    * Accessibile dall'Editor di Unity tramite **Guida > manuale**

## <a name="see-also"></a>Vedere anche
* [Nozioni fondamentali di MR 100: Introduzione a Unity](holograms-100.md)
* [Impostazioni consigliate per Unity](recommended-settings-for-unity.md)
* [Raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Esportazione e creazione di una soluzione di Visual Studio a Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Utilizzo dello spazio dei nomi Windows con le app Unity per HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Le procedure consigliate per l'uso di Unity e Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modalità di gioco Unity](unity-play-mode.md)
* [Porting di guide](porting-guides.md)
