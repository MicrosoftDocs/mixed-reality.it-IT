---
title: Guide alla conversione
description: Procedura dettagliata che spiega come trasferire un'applicazione immersiva esistente a una realtà mista di Windows.
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: Port, porting, Unity, middleware, Engine, UWP, Win32
ms.openlocfilehash: a1e3cd47096d728091d62d6c038bf6b2eb6bab16
ms.sourcegitcommit: 0eb99fae933d4374af2c032af4e9ceda1807e532
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2020
ms.locfileid: "86156772"
---
# <a name="porting-guides"></a>Guide alla conversione

## <a name="overview"></a>Panoramica

Windows 10 include il supporto diretto per auricolari immersivi e olografici. Se è stato creato contenuto per altri dispositivi, ad esempio Oculus Rift o HTC vive, questi hanno dipendenze da librerie esistenti sopra l'API della piattaforma del sistema operativo. Il riutilizzo del contenuto esistente in realtà mista di Windows implica il reindirizzamento dell'utilizzo di questi altri SDK alle API Windows. Le [API della piattaforma Windows per la realtà mista](https://docs.microsoft.com/uwp/api/Windows.Perception) funzionano con il modello di app Win32 e il piattaforma UWP (Universal Windows Platform) (UWP). Se l'app non è già stata compilata per UWP, il passaggio a UWP sarà parte integrante dell'esperienza di porting.

## <a name="porting-overview"></a>Panoramica del porting

A livello generale, sono necessari i passaggi seguenti per trasferire il contenuto esistente:
1. **Verificare che il PC esegua Windows 10 Fall Creators Update (16299).** Non è più consigliabile ricevere le build di anteprima dall'anello Insider Skip Ahead, perché tali Build non saranno le più stabili per lo sviluppo di realtà miste.
2. **Eseguire l'aggiornamento alla versione più recente della grafica o del motore di gioco.** I motori di gioco dovranno supportare Windows 10 SDK versione 10.0.15063.0 (rilasciato ad aprile 2017) o versione successiva.
3. **Aggiornare tutti i middleware, i plug-in o i componenti.** Se l'app contiene componenti, è consigliabile eseguire l'aggiornamento alla versione più recente. Le versioni più recenti dei plug-in più comuni includono il supporto per UWP.
4. **Rimuovere le dipendenze da SDK duplicati**. A seconda del dispositivo a cui è destinato il contenuto, è necessario rimuovere o compilarlo in modo condizionale (ad esempio, SteamVR) in modo da poter utilizzare le API di Windows.
5. **Risolvere i problemi di compilazione.** A questo punto, l'esercizio di porting è specifico per l'app, il motore e le dipendenze dei componenti.

## <a name="common-porting-steps"></a>Passaggi comuni di porting

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>Passaggio comune 1: assicurarsi di avere il giusto hardware di sviluppo

Nella pagina [installa strumenti](install-the-tools.md#for-immersive-vr-headset-development) è elencato l'hardware di sviluppo consigliato.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>Passaggio comune 2: eseguire l'aggiornamento all'ultimo volo di Windows 10

La piattaforma di realtà mista Windows è ancora in fase di sviluppo attivo. È consigliabile [partecipare al programma Windows Insider](https://insider.windows.com/) per accedere al volo "Windows Insider Fast".
1. Installare [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Partecipa](https://insider.windows.com/) al programma Windows Insider.
3. Abilita [modalità sviluppatore](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Passa alla sezione relativa ai [voli rapidi di Windows Insider](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) tramite **le impostazioni > sezione aggiornamento & sicurezza**

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio-uwp-only"></a>Passaggio comune 3: eseguire l'aggiornamento alla build più recente di Visual Studio (solo UWP)
* Vedere [Install the Tools](install-the-tools.md#installation-checklist) page in Visual Studio 2019

### <a name="common-step-4-be-ready-for-the-store-uwp-only"></a>Passaggio 4 comune: essere pronti per lo Store (solo UWP)
* Usa il [Kit di certificazione applicazioni Windows](https://developer.microsoft.com/windows/develop/app-certification-kit) (noto anche come pazzoide) presto e spesso.
* Usare [Portability Analyzer](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([download](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>Passaggio comune 5: scegliere la scheda corretta
* Nei sistemi come notebook con due GPU, fare [riferimento alla scheda corretta](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Questo vale per Unity e per le app DirectX native in cui viene creato un ID3D11Device, in modo esplicito o implicito (Media Foundation), per la funzionalità.

## <a name="unity-porting-guidance"></a>Guida al porting di Unity

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity Step 1: seguire la procedura di portabilità comune

Seguire tutti i passaggi comuni. Nel passaggio #3 Selezionare il carico di lavoro **sviluppo di giochi con Unity** . È possibile deselezionare il componente facoltativo editor Unity poiché verrà installata una versione più recente di Unity dalle istruzioni riportate di seguito.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity Step 2: eseguire l'aggiornamento alla build pubblica più recente di Unity con il supporto di Windows MR
1. Scarica l'ultima [Build pubblica consigliata di Unity](install-the-tools.md) con il supporto della realtà mista.
2. Salva una copia del progetto prima di iniziare
3. Esaminare la [documentazione](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponibile in Unity sulla portabilità.
4. Seguire le [istruzioni](https://docs.unity3d.com/Manual/APIUpdater.html) nel sito di Unity per usare il relativo aggiornamento automatico delle API
5. Controllare e verificare se sono presenti ulteriori modifiche che è necessario apportare per eseguire il progetto e risolvere gli eventuali errori e avvisi rimanenti. 

> [!Note] 
> Se è presente un middleware da cui si dipende, verificare che sia in uso la versione più recente. per altre informazioni, vedere il passaggio 3 riportato di seguito.

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity Step 3: aggiornare il middleware alle versioni più recenti

Con qualsiasi aggiornamento di Unity, è possibile che sia necessario aggiornare uno o più pacchetti middleware da cui dipende il gioco o l'applicazione. Inoltre, l'aggiornamento con il middleware più recente aumenta la probabilità di successo durante il resto del processo di porting. Molti pacchetti middleware hanno aggiunto di recente il supporto per piattaforma UWP (Universal Windows Platform) (UWP) e l'aggiornamento alle versioni più recenti consente di sfruttare il lavoro.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity Step 4: indirizzare l'applicazione per l'esecuzione in piattaforma UWP (Universal Windows Platform) (UWP)

Se la destinazione è Win32, è possibile ignorare questo passaggio e continuare con il passaggio 5.

Dopo aver installato gli strumenti, è necessario fare in modo che l'app venga eseguita come app di Windows universale.

* Seguire le istruzioni [dettagliate](https://unity3d.com/partners/microsoft/porting-guides) fornite da Unity. È consigliabile rimanere nella versione LTS più recente (qualsiasi versione 20XX. 4) per Windows MR.
* Per altre risorse di sviluppo UWP, vedere la [Guida allo sviluppo di giochi per Windows 10](https://docs.microsoft.com/windows/uwp/gaming/e2e).

> [!NOTE]
> Unity continua a migliorare il supporto per IL2CPP; IL2CPP rende più semplici le porte UWP. Se la destinazione è il back-end di scripting .NET, è consigliabile prendere in considerazione la conversione per sfruttare il back-end IL2CPP.

* È possibile ignorare "Unity Step 5" poiché la destinazione è UWP anziché Win32.

> [!NOTE] 
> Se l'applicazione dispone di dipendenze da servizi specifici del dispositivo, ad esempio la corrispondenza da Steam, sarà necessario disabilitarli in questo passaggio. È possibile associare i servizi equivalenti forniti da Windows in un secondo momento.

### <a name="unity-step-5-target-your-application-to-run-on-win32"></a>Unity Step 5: indirizzare l'applicazione per l'esecuzione in Win32

Dall'interno dell'applicazione Unity:

* Passare a file-> impostazioni di compilazione
* Selezionare "PC, Mac, Linux autonomo"
* Imposta la piattaforma di destinazione su "Windows"
* Imposta architettura su "x86" selezionare "Cambia piattaforma"


### <a name="unity-step-6-setup-your-windows-mixed-reality-hardware"></a>Unity Step 6: configurare l'hardware della realtà mista di Windows
1. Esaminare i passaggi nella [configurazione dell'auricolare immersiva](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Scopri come [usare il simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md) e passare [alla Home realtà mista di Windows](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity STEP 7: destinazione dell'applicazione per l'esecuzione in realtà mista di Windows
1. In primo luogo, è necessario rimuovere o compilare in modo condizionale qualsiasi altro supporto di libreria specifico di un determinato VR SDK. Tali asset cambiano spesso le impostazioni e le proprietà del progetto in modi non compatibili con altri SDK di VR, ad esempio la realtà mista di Windows.
    * Ad esempio, se il progetto fa riferimento a SteamVR SDK, sarà necessario aggiornare il progetto in modo da escludere i prefabbricati e le chiamate all'API script durante l'esportazione per la destinazione di compilazione di Windows Store.
    * I passaggi specifici per escludere gli altri SDK di VR saranno presto disponibili.
2. Nel progetto Unity, fare [riferimento a Windows 10 SDK](holograms-100.md#target-windows-10-sdk)
3. Per ogni scena, [configurare la fotocamera](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity Step 8: usare la fase per collocare il contenuto al piano

È possibile creare esperienze di realtà miste in un'ampia gamma di [scale di esperienza](coordinate-systems.md).

Se si esegue il porting di un' **esperienza con scalabilità verticale**, è necessario assicurarsi che Unity sia impostato sul tipo di spazio di rilevamento **stazionario** :

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Questo codice precedente imposta il sistema di Coordinate internazionali di Unity per tenere traccia del [frame di riferimento fisso](coordinate-systems.md#spatial-coordinate-systems). Nella modalità di rilevamento fisso, il contenuto inserito nell'editor immediatamente davanti alla posizione predefinita della fotocamera (avanti è-Z) viene visualizzato davanti all'utente all'avvio dell'app. Per ricentrare l'origine di seduta dell'utente, è possibile chiamare XR di Unity [. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) .

Se si sta effettuando il porting di un'esperienza di **scalabilità permanente** o di **scalabilità**in modalità locale, il contenuto verrà inserito in relazione al pavimento. Si ragiona sul pavimento dell'utente usando la **[fase spaziale](coordinate-systems.md#spatial-coordinate-systems)**, che rappresenta l'origine di livello del piano definita dall'utente e il limite di spazio facoltativo, configurato durante la prima esecuzione. Per queste esperienze è necessario assicurarsi che Unity sia impostato sul tipo di spazio di rilevamento **RoomScale** . Anche se RoomScale è il valore predefinito, è consigliabile impostarlo in modo esplicito e assicurarsi di tornare a true per individuare le situazioni in cui l'utente ha spostato il computer dalla stanza in cui è stato calibrato:

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

Quando l'app imposta correttamente il tipo di spazio di rilevamento RoomScale, il contenuto inserito sul piano y = 0 verrà visualizzato sul pavimento. L'origine in (0, 0, 0) sarà la posizione specifica del piano in cui l'utente si trovava durante l'installazione della chat room, con-Z che rappresenta la direzione in avanti durante l'installazione.

Nel codice di script è quindi possibile chiamare il metodo TryGetGeometry sul tipo UnityEngine. Experimental. XR. Boundary per ottenere un poligono di limiti, specificando un tipo di limite di TrackedArea. Se l'utente ha definito un limite (si ottiene un elenco di vertici), è possibile fornire all'utente un' **esperienza di scalabilità della stanza** , in cui è possibile aggirare la scena creata.

Il sistema eseguirà automaticamente il rendering del limite quando l'utente si avvicina. L'app non deve usare questo poligono per eseguire il rendering del limite.

Per altre informazioni, vedere la pagina [sistemi di coordinate in Unity](coordinate-systems-in-unity.md) .

Alcune applicazioni utilizzano un rettangolo per vincolare l'interazione. Il recupero del rettangolo inscritto più grande non è supportato direttamente nell'API UWP o Unity. Il codice di esempio collegato al seguente mostra come trovare un rettangolo all'interno dei limiti tracciati. Poiché è basato su euristico, potrebbe non trovare la soluzione ottimale, tuttavia, i risultati sono coerenti con le aspettative. I parametri nell'algoritmo possono essere ottimizzati per trovare risultati più precisi al costo del tempo di elaborazione. L'algoritmo si trova in una divisione del Toolkit di realtà mista che usa la versione MRTP di Unity di 5,6 Preview. Questa operazione non è disponibile pubblicamente. Il codice deve essere direttamente utilizzabile in 2017,2 e versioni successive di Unity. Il codice verrà trasferito al MRTK corrente nel prossimo futuro.

[file zip di codice in GitHub](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) File importanti:
* Assets/HoloToolkit/stage/scripts/StageManager. cs-esempio di utilizzo
* Assets/HoloToolkit/stage/scripts/LargestRectangle. cs-implementazione dell'algoritmo
* Assets/HoloToolkit-UnitTests/editor/stage/LargestRectangleTest. cs-test Trivial dell'algoritmo

Esempio di risultati:

![Esempio di risultati](images/largestrectangle-400px.jpg)

L'algoritmo si basa su un Blog di Daniel smilkov: [rettangolo più grande in un poligono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Unity Step 9: usare il modello di input

Ogni gioco o applicazione destinata a un HMD esistente avrà un set di input che gestisce, i tipi di input necessari per l'esperienza e le API specifiche che chiama per ottenere tali input. Abbiamo investito nel tentativo di renderlo il più semplice e semplice possibile per sfruttare i vantaggi degli input disponibili nella realtà mista di Windows.
1. Per informazioni dettagliate sul modo in cui la realtà mista di Windows espone l'input e sul modo in cui è possibile eseguire questa operazione, vedere la **[Guida al porting di input per Unity](input-porting-guide-for-unity.md)** .
2. Scegliere se utilizzare l'API di input cross-VR-SDK di Unity o l'API di input specifica del sig. Le API di input. GetButton/input. getaxis generale vengono usate attualmente dalle app di Unity VR per l'input [Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e l' [input OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se le app usano già queste API per i controller di movimento, questo è il percorso più semplice: è necessario solo modificare il mapping di pulsanti e assi nel gestore di input.
    * È possibile accedere ai dati di motion controller in Unity usando le API General Cross-VR-SDK input. GetButton/input. getaxis o le API UnityEngine. XR. WSA. input specifiche di MR. (in precedenza nello spazio dei nomi UnityEngine. XR. WSA. input in Unity 5,6)
    * Vedere l' [esempio nel Toolkit](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) che combina gamepad e controller di movimento.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity Step 10: test delle prestazioni e ottimizzazione

La realtà mista di Windows sarà disponibile in un'ampia gamma di dispositivi, a partire da PC con giochi di fascia alta, fino a PC mainstream di mercato più ampi. A seconda del mercato di destinazione, esiste una differenza significativa nei budget di calcolo e grafica disponibili per l'applicazione. Durante questo esercizio di porting, è probabile che si usi un PC Premium e che siano disponibili budget di calcolo e grafica significativi per l'app. Se si vuole rendere l'app disponibile a un pubblico più ampio, è consigliabile eseguire il test e la profilatura dell'app sull' [hardware rappresentativo a cui si vuole fare riferimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

[Unity](https://docs.unity3d.com/Manual/Profiler.html) e [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) includono i profiler delle prestazioni e le linee guida per la pubblicazione di [Microsoft](understanding-performance-for-mixed-reality.md) e [Intel](https://software.intel.com/articles/vr-content-developer-guide) per la profilatura e l'ottimizzazione delle prestazioni. È disponibile una descrizione approfondita delle prestazioni disponibili [per comprendere le prestazioni della realtà mista](understanding-performance-for-mixed-reality.md). Sono inoltre disponibili dettagli specifici per Unity in [raccomandazioni sulle prestazioni per Unity](performance-recommendations-for-unity.md).

## <a name="see-also"></a>Vedere anche
* [Guida alla conversione dell'input per Unity](input-porting-guide-for-unity.md)
* [Linee guida per la compatibilità hardware con la realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Informazioni sulle prestazioni per la realtà mista](understanding-performance-for-mixed-reality.md)
* [Suggerimenti sulle prestazioni per Unity](performance-recommendations-for-unity.md)
* [Aggiungere il supporto Xbox Live a Unity per UWP](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
