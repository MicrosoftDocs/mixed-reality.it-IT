---
title: Guide alla conversione
description: Una procedura dettagliata passo a passo che spiegano come eseguire il porting di un'applicazione esistente coinvolgente per realtà mista di Windows.
author: ChimeraScorn
ms.author: cwhite
ms.date: 10/02/2018
ms.topic: article
keywords: la porta, portabilità, unity, middleware, motore, piattaforma UWP
ms.openlocfilehash: a4a8c78f1c45fd8e3b85a767d139bae9f67540e0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602182"
---
# <a name="porting-guides"></a>Guide alla conversione

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

Windows 10 include il supporto per le cuffie coinvolgenti e holographic direttamente. Coloro che hanno creato contenuto per un altro dispositivo, ad esempio del Oculus Rift o Vive HTC, hanno dipendenze dalle librerie che esistono di sopra di API della piattaforma del sistema operativo. Portare anche di contenuto esistente in Windows Mixed Reality implica l'utilizzo di questi altri SDK per le API di Windows di reindirizzamento. Il [API della piattaforma Windows per realtà mista](https://docs.microsoft.com/uwp/api/Windows.Perception) funzionano solo nel modello di app Universal Windows Platform (UWP). Pertanto, se l'app non è già incorporato per la piattaforma UWP, il porting alla piattaforma UWP farà parte dell'esperienza di porting.

## <a name="porting-overview"></a>Porting di panoramica

In generale, questi sono i passaggi necessari per il porting di contenuto esistente:
1. **Assicurarsi che il PC è in esecuzione di Windows 10 Fall Creators Update (16299).** Non è più consigliabile ricezione preview builds dall'anello Skip Insider-Ahead, come tali compilazioni non sarà più stabile per lo sviluppo della realtà mista.
2. **Eseguire l'aggiornamento alla versione più recente del motore di gioco o grafica.** Motori di gioco dovranno supportare Windows 10 SDK versione 10.0.15063.0 (rilasciata ad aprile 2017) o versione successiva.
3. **Eseguire l'aggiornamento di qualsiasi middleware, plug-in o componenti.** Se l'app contiene tutti i componenti, è consigliabile eseguire l'aggiornamento alla versione più recente. Le versioni più recenti dei plug-in genere dispongono di supporto per la piattaforma UWP.
4. **Rimuovere le dipendenze da SDK duplicati**. A seconda del dispositivo era destinata al contenuto, è necessario rimuovere o la compilazione condizionale out tale SDK (ad esempio SteamVR) in modo che è possibile fare riferimento invece le API di Windows.
5. **Risolvere i problemi di compilazione.** A questo punto, l'esercizio di porting è specifico per l'app, il motore e le dipendenze dei componenti che è necessario.

## <a name="common-porting-steps"></a>Passaggi comuni di porting

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>Passaggio 1 comune: Assicurarsi di avere l'hardware di sviluppo a destra

Il [installare gli strumenti](install-the-tools.md#for-immersive-vr-headset-development) pagina elenca l'hardware consigliato di sviluppo.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>Passaggio 2 comune: Eseguire l'aggiornamento per il volo più recente di Windows 10

La piattaforma di realtà mista di Windows è ancora in fase di sviluppo attivo e per essere più efficace, è consigliabile acquisire durante il volo "Fast Windows Insider". Per accedere ai voli di windows, dovrai [desidero partecipare al programma di Windows Insider](https://insider.windows.com/).
1. Installare il [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Join](https://insider.windows.com/) programma Windows Insider.
3. Abilitare [modalità sviluppatore](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Passare al [voli Windows Insider Fast](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) tramite le impostazioni--> Aggiorna & sezione sicurezza

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>Passaggio 3 comune: Eseguire l'aggiornamento alla build più recente di Visual Studio
* Vedi [installare gli strumenti](install-the-tools.md#installation-checklist) pagina in Visual Studio 2017

### <a name="common-step-4-be-ready-for-the-store"></a>Passaggio 4 comune: La preparazione per la Store
* Uso [Kit di certificazione App Windows](https://developer.microsoft.com/windows/develop/app-certification-kit) (noto anche come WACK) tempestivi e frequenti.
* Uso [Portability Analyzer](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([scaricare](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>Passaggio 5 comune: Scegliere la scheda corretta
* Nei sistemi, ad esempio con due GPU, i notebook [come destinazione l'adattatore corretto](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Questo vale per le app Unity, inoltre alle App native di DirectX, in cui viene creato un ID3D11Device, in modo implicito o esplicito (Media Foundation), per la relativa funzionalità.

## <a name="unity-porting-guidance"></a>Indicazioni sulla portabilità di Unity

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity passaggio1: Seguire i passaggi comuni di porting

Seguire tutte le operazioni più comuni. Quando nel passaggio #3, selezionare la **lo sviluppo di giochi con Unity** carico di lavoro. È possibile deselezionare il componente facoltativo di Editor di Unity poiché si desidera installare una versione più recente di Unity da istruzioni riportate di seguito.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Passaggio di Unity 2: Eseguire l'aggiornamento all'ultima build pubbliche di Unity con il supporto Windows MR
1. Scaricare la versione più recente [consigliato build pubbliche di Unity](install-the-tools.md) con realtà mista di supportare.
2. Salvare una copia del progetto prima di iniziare.
3. Rivedere le [documentazione](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponibili da Unity sul porting.
4. Seguire le [istruzioni](https://docs.unity3d.com/Manual/APIUpdater.html) nel sito di Unity per l'uso di loro updater API automatica
5. Controllare se esistono altre modifiche che è necessario apportare ottenere il progetto in esecuzione ed esaminato rimanente gli eventuali errori e avvisi. Nota: Se si dispone di middleware di cui si dipende, si potrebbe essere necessario aggiornare tale middleware per iniziare a usare (ulteriori dettagli nel passaggio 3 riportato di seguito).

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Passaggio di Unity 3: Aggiornare il middleware per le versioni più recenti

Con qualsiasi aggiornamento di Unity, è probabile che è necessario aggiornare uno o più pacchetti middleware che dipende dal gioco o nell'applicazione. Inoltre, la versione più recente di tutti i middleware aumenteranno le probabilità di successo nella parte restante del processo di trasferimento. Numero di pacchetti middleware have recentemente aggiunto il supporto per la Universal Windows Platform (UWP) e l'aggiornamento alle versioni più recenti consentirà di sfruttare tale lavoro.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Passaggio di Unity 4: L'applicazione venga eseguita in Universal Windows Platform (UWP) di destinazione

Dopo aver installato gli strumenti, è necessario ottenere l'app in esecuzione come un'app di Windows universale.
* Seguire le [procedura dettagliata passo a passo](https://unity3d.com/partners/microsoft/porting-guides) fornito da Unity. Si noti che devono restare nella versione più recente LTS (qualsiasi versione 20xx.4) per Windows MR.
* Per altre risorse per lo sviluppo UWP, esaminiamo il [Guida per lo sviluppo di giochi Windows 10](https://docs.microsoft.com/windows/uwp/gaming/e2e).
* Si noti che Unity continua a migliorare il supporto IL2CPP. IL2CPP semplifica alcuni UWP porte in modo significativo. Se si usa attualmente .net scripting back-end, è necessario considerare la conversione di sfruttare i vantaggi di back-end IL2CPP invece.

Nota: Se l'applicazione include tutte le dipendenze in servizi specifici di dispositivi, ad esempio, corrispondenza rendendo dal flusso, è necessario disabilitarle, in questo passaggio. In un secondo momento, è possibile collegare per i servizi equivalenti Windows forniti.

### <a name="unity-step-5-deprecated"></a>Passaggio di Unity 5: (Deprecato)

Passaggio 5 non è più necessario. Si sta lasciandolo qui in modo che l'indicizzazione dei passaggi rimane invariato.

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Passaggio di Unity 6: Ottenere la configurazione di hardware realtà mista di Windows
1. Rivedere i passaggi [installazione visore VR Immersivi](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Scopri [mediante il simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md) e [passando la home page di realtà mista di Windows](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Passaggio di Unity 7: L'applicazione venga eseguita in realtà mista di Windows di destinazione
1. In primo luogo, è necessario rimuovere o qualsiasi altro supporto di libreria specifici di un particolare VR SDK la compilazione condizionale. Tali asset modificano frequentemente le impostazioni e proprietà del progetto in modo che non è compatibili con altri SDK di realtà virtuale, ad esempio la realtà mista di Windows.
    * Ad esempio, se il progetto fa riferimento al SDK SteamVR, dovrai aggiornare il progetto per escludere le prefabs e chiamate alle API di script durante l'esportazione per la destinazione build di Windows Store.
    * I passaggi specifici per escludere in modo condizionale le altri SDK VR sarà presto disponibile.
2. Nel progetto Unity, [destinazione Windows 10 SDK](holograms-100.md#target-windows-10-sdk)
3. Per ogni scena, [la fotocamera di installazione](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Passaggio di Unity 8: Usare la fase di collocare il contenuto sul pavimento

È possibile sviluppare esperienze di realtà mista in un'ampia gamma di [esperienza Scale](coordinate-systems.md).

Se si esegue il trasferimento una **esperienza su scala seduto**, è necessario assicurarsi di Unity è impostato sul **fermo** rilevamento tipo dello spazio:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Sistema di coordinate complessive di Unity per tenere traccia consente di impostare il [fotogramma di riferimento fisso](coordinate-systems.md#spatial-coordinate-systems). Nella modalità di rilevamento fisso, il contenuto inserito nell'editor subito prima di percorso predefinito della camera (in avanti è -Z) verrà visualizzato davanti all'utente quando l'app viene avviata. Per centrare di nuovo l'utente del seduto origine, è possibile chiamare di Unity [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) (metodo).

Se si esegue il trasferimento una **esperienza su scala permanente** o **esperienza su scala chat room**, verranno inseriti contenuto relativo al piano. Meglio il suo floor usando il  **[fase spaziali](coordinate-systems.md#spatial-coordinate-systems)**, che rappresenta l'utente definito a livello di parte intera origine e limiti di spazio facoltativo, configurato durante la prima esecuzione. Per queste esperienze, è necessario assicurarsi di Unity è impostato il **RoomScale** spazio tipo di rilevamento. Mentre RoomScale è quello predefinito, è necessario impostarlo in modo esplicito e assicurarsi di che ottenere nuovamente impostato su true, per rilevare situazioni in cui l'utente ha allontanate dal proprio computer la chat che vengono calibrati:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Una volta che l'app imposta correttamente i RoomScale rilevamento tipo dello spazio, contenuto inserito in y = 0 piano verrà visualizzati sul pavimento. L'origine in corrispondenza (0, 0, 0) sarà la posizione specifica nell'ambiente operativo in cui l'utente si durante l'installazione di chat, con -Z che rappresenta la direzione in avanti che riscontrato durante l'installazione.

Nel codice di script, è quindi possibile chiamare il metodo TryGetGeometry per l'utente è il tipo UnityEngine.Experimental.XR.Boundary per ottenere un poligono di confine, che specifica un tipo di limite di TrackedArea. Se l'utente ha definito un limite (verrà restituito un elenco di vertici), si saprà già sia sicuro offrire una **esperienza su scala chat room** all'utente, in cui sono inoltre informazioni dettagliate per la scena creare.

Si noti che il sistema esegue il rendering automatico il limite quando l'utente si avvicina. L'app non dovrà utilizzare questo poligono per il rendering del limite se stesso.

Per altre informazioni, vedere la [sistemi di Coordinate in Unity](coordinate-systems-in-unity.md) pagina.

Alcune applicazioni usano un rettangolo per vincolare l'interazione. Recuperare il rettangolo più grande inscritto non è direttamente supportata nella piattaforma UWP API o Unity. L'esempio di codice collegato a seguente viene illustrato come trovare un rettangolo all'interno dei limiti inseriti nella traccia. Approccio euristico basato in modo che potrebbe non trovare la soluzione ottimale, tuttavia, i risultati siano generalmente coerenti con le aspettative. I parametri dell'algoritmo possono essere ottimizzati per trovare i risultati più precisi aumentando tuttavia il tempo di elaborazione. L'algoritmo è in un fork del Toolkit di realtà mista che usa l'anteprima versione MRTP di Unity 5.6. Non è disponibile pubblicamente. Il codice dovrebbe essere utilizzabile direttamente nelle versioni 2017.2 e versioni successive di Unity. Il codice sarà essere trasferito al MRTK corrente in un prossimo futuro.

[file zip del codice su GitHub](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) file importanti:
* Assets/HoloToolkit/Stage/Scripts/StageManager.cs - esempio di utilizzo
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle.cs - implementazione dell'algoritmo
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest.cs - test semplice dell'algoritmo

Esempio dei risultati:

![Esempio dei risultati](images/largestrectangle-400px.jpg)

Algoritmo si basa su un blog da Daniel Smilkov: [Rettangolo più grande in un'istanza polygon](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Passaggio di Unity 9: Esaminare il modello di input

Ogni gioco o nell'applicazione destinata a un HMD esistente sarà presente un set di input in cui vengono gestite, tipi di input necessari per l'esperienza e API specifiche tramite cui viene chiamato per ottenere tali input. Sono stati fatti investimenti per riuscire a realizzare come semplice e lineare possibile sfruttare i vantaggi degli input disponibili in realtà mista di Windows.
1. Leggere con attenzione il **[Input di portabilità manuale per Unity](input-porting-guide-for-unity.md)** per informazioni dettagliate sul realtà mista di Windows espone input e il mapping alla quale l'applicazione può eseguire oggi stesso.
2. Scegliere se si intende sfruttare l'API di input di Unity cross-VR-SDK o API di input di specifiche di MR. Le API Input.GetButton/Input.GetAxis generale vengono usate dalle App Unity VR oggi per [input Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e [OpenVR input](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se le app che già utilizzano queste API per i controller di movimento, questo è il percorso più semplice: è necessario solo modificare il mapping dei pulsanti e assi nel gestore di Input.
    * È possibile accedere a dati di movimento controller in Unity utilizzando APIs UnityEngine.XR.WSA.Input SIG specifici o generali Input.GetButton/Input.GetAxis cross-VR-SDK le API. (in precedenza nello spazio dei nomi di UnityEngine.XR.WSA.Input in Unity 5.6)
    * Vedere le [esempio di Toolkit](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) che combina i controller su gamepad e movimento.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Passaggio di Unity 10: Test delle prestazioni e ottimizzazione

Realtà mista di Windows verrà sia disponibile in una classe ampia di dispositivi, che vanno da elevata terminare i PC di gioco, fino a ampio mercato mainstream PC. A seconda di quale tipo di applicazione di destinazione, è presente una differenza significativa nel budget di calcolo e di grafici disponibili per l'applicazione. Nel corso dell'esercizio porting, probabile sfruttando un premio di PC e hanno dovuto significativi budget di calcolo e la grafica disponibile l'app. Se si vuole rendere disponibile l'app a un pubblico più ampio, è necessario testare e profilare l'app nel [rappresentativo hardware che si desidera destinazione](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Entrambe [Unity](https://docs.unity3d.com/Manual/Profiler.html) e [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) includono i profiler delle prestazioni ed entrambe [Microsoft](understanding-performance-for-mixed-reality.md) e [Intel](https://software.intel.com/articles/vr-content-developer-guide) pubblicare le linee guida su profilatura delle prestazioni e ottimizzazione. Una discussione completa delle prestazioni è disponibile all'indirizzo [ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md). Inoltre, vi sono i dettagli specifici per Unity sotto [raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md).

## <a name="see-also"></a>Vedere anche
* [Input porting guide per Unity](input-porting-guide-for-unity.md)
* [Realtà mista di Windows minimo PC compatibilità alle linee guida hardware](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Ottenere informazioni sulle prestazioni per realtà mista](understanding-performance-for-mixed-reality.md)
* [Raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Aggiungere il supporto di Xbox Live per Unity per la piattaforma UWP](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
