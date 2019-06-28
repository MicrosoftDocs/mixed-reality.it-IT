---
title: Simulazione di percezione
description: Una Guida all'utilizzo della libreria di simulazione di percezione automatizzare input simulati per le applicazioni coinvolgenti
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, simulazione, test
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414536"
---
# <a name="perception-simulation"></a>Simulazione di percezione

Si desidera creare un test automatizzato per l'app? Eseguire i test per andare oltre a livello di componente di unit test e sperimentare effettivamente l'app end-to-end? Simulazione di percezione è ciò che sta cercando. La libreria di simulazione di percezione invia umana e world dati all'app di input in modo che è possibile automatizzare i test. Ad esempio, è possibile simulare l'input di una risorse umane alla ricerca in una posizione specifica, ripetibile e quindi eseguendo un movimento o utilizzando un controller di movimento.

Simulazione di percezione può inviare l'input simulato simile al seguente a un HoloLens fisico, l'emulatore di HoloLens (dal 1 ° generazione), installato HoloLens 2 emulatore o un PC con il portale di realtà mista. Percezione simulazione ignora i sensori in tempo reale in un dispositivo di realtà mista e invia simulati input per le applicazioni in esecuzione nel dispositivo. Le applicazioni ricevono questi eventi di input tramite le stesse API sempre utilizzano e non può indicare la differenza tra l'esecuzione con sensori reali e l'esecuzione con Perception simulazione. Simulazione di percezione è la stessa tecnologia usata per gli emulatori di HoloLens inviare input simulato alla macchina virtuale di HoloLens.

Per iniziare a usare simulazione nel codice, iniziare creando un oggetto IPerceptionSimulationManager. Da tale oggetto, è possibile eseguire comandi per controllare le proprietà di un simulato "umano", tra cui posizione head mano posizione e i movimenti, ed è possibile abilitare e modificare i controller di movimento.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Configurazione di un progetto di Visual Studio per la simulazione di percezione
1. [Installare l'emulatore di HoloLens](install-the-tools.md) nel PC di sviluppo. L'emulatore include le librerie che si utilizzerà per la simulazione di percezione.
2. Creare un nuovo Visual Studio C# progetto desktop (un progetto Console è efficace per iniziare).
3. Aggiungere i file binari seguenti al progetto come riferimenti (progetto -> Aggiungi -> riferimento...). È possibile trovarli in % ProgramFiles (x86) %\Microsoft XDE\\(versione), ad esempio **% ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** per l'emulatore di 2 HoloLens.  (Nota: anche se i file binari fanno parte dell'emulatore 2 HoloLens, funzionano anche per realtà mista di Windows sul desktop.) a. PerceptionSimulationManager.Interop.dll - gestito C# wrapper per la simulazione di percezione.
    b. PerceptionSimulationRest.dll - libreria per la configurazione di un canale di comunicazione web socket nel HoloLens o nell'emulatore.
    c. SimulationStream.Interop.dll - tipi condivisi per la simulazione.
4. Aggiungere l'implementazione PerceptionSimulationManager.dll binari al progetto un. Prima di tutto aggiunto come un file binario del progetto (progetto -> Aggiungi -> elemento esistente...). Salvarlo come un collegamento in modo da non copiarla alla cartella di origine del progetto. ![Aggiungere al progetto come collegamento PerceptionSimulationManager.dll](images/saveaslink.png) b. Assicurarsi quindi di ottenere di copiati nella cartella di output in fase di compilazione. Si tratta di una finestra delle proprietà per il file binario. ![Contrassegnare PerceptionSimulationManager.dll da copiare nella directory di output](images/copyalways.png)
5. Impostare la piattaforma soluzione attiva su x64.  (Uso di Configuration Manager per creare una voce di piattaforma per x64, se non esiste già).

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Creazione di un oggetto di gestione IPerceptionSimulation

Per controllare la simulazione, si saranno rilasciare aggiornamenti agli oggetti recuperati da un oggetto IPerceptionSimulationManager. Il primo passo è ottenere quell'oggetto e connetterla a un emulatore o il dispositivo di destinazione. È possibile ottenere l'indirizzo IP all'emulatore facendo clic sul pulsante nel portale del dispositivo di [sulla barra degli strumenti](using-the-hololens-emulator.md)

![Icona dispositivo portale aperta](images/emulator-deviceportal.png) **aprire il portale di dispositivo**: apre il Portale di dispositivi di Windows per il sistema operativo di HoloLens nell'emulatore.  Per realtà mista di Windows, questo può essere recuperato nell'app impostazioni nel gruppo "Aggiornamento e sicurezza" e quindi "per gli sviluppatori" nel "Connetti tramite:" sezione "Enable Device Portal".  Assicurarsi di prendere nota sia l'indirizzo IP e porta.

In primo luogo, verrà chiamato per ottenere un oggetto RestSimulationStreamSink RestSimulationStreamSink.Create. Questo è il dispositivo di destinazione o l'emulatore che consentono di controllare tramite una connessione http. I comandi verranno passati a e gestiti dal [Windows Device Portal](using-the-windows-device-portal.md) in esecuzione nel dispositivo o emulatore. I quattro parametri, devi creare un oggetto sono:
* Uri di URI - indirizzo IP del dispositivo di destinazione (ad esempio, "http://123.123.123.123"o"http://123.123.123.123:50080")
* System.Net.NetworkCredential credenziali - nome utente/password per la connessione per il [Windows Device Portal](using-the-windows-device-portal.md) sul dispositivo di destinazione o un emulatore. Se ci si connette all'emulatore tramite il relativo indirizzo locale (ad esempio, 168. *.* . *) sullo stesso PC, verranno accettate le credenziali.
* normale - bool True per priorità normale, false per priorità bassa. In genere si desidera impostare l'opzione su *true* per scenari di test, che consente il test di assumere il controllo.  L'emulatore e la simulazione di realtà mista di Windows Usa le connessioni per priorità bassa.  Se il test Usa anche una connessione per priorità bassa, più recentemente stabilita connessione verrà nel controllo.
* Token System.Threading.CancellationToken - Token per annullare l'operazione asincrona.

In secondo luogo si creerà il IPerceptionSimulationManager. Questo è l'oggetto da usare per controllare la simulazione. Si noti che questa operazione deve anche essere eseguita in un metodo asincrono.

## <a name="control-the-simulated-human"></a>Controllare l'umana simulata

Un IPerceptionSimulationManager dispone di una proprietà di risorse umane che restituisce un oggetto ISimulatedHuman. Per controllare l'uomo simulato, eseguire operazioni su questo oggetto. Ad esempio:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Esempio di base C# applicazione console

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>Estendere l'esempio C# applicazione console

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>Si noti nei controller di 6-gradi di libertà

Prima di chiamare qualsiasi proprietà nei metodi in un controller simulato-i gradi di libertà 6, è necessario attivare il controller.  Non eseguire questa operazione comporterà un'eccezione.  A partire da Windows 10 possono aggiornare 2019, possono essere installati e attivati impostando la proprietà Status dell'oggetto ISimulatedSixDofController su SimulatedSixDofControllerStatus.Active controller simulato 6-gradi di libertà.
In Windows 10 ottobre 2018 Update e versioni precedenti, è necessario installare un controller simulato 6-gradi di libertà prima di tutto, chiamare lo strumento PerceptionSimulationDevice che si trova nella cartella \Windows\System32.  L'utilizzo di questo strumento è come segue:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Per esempio

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Azioni supportate sono:
* Ho = install
* q = query
* r = Rimuovi

Istanze supportate sono:
* 1 = il controller a sinistra-i gradi di libertà 6
* 2 = il controller a destra-i gradi di libertà 6

Il codice di uscita del processo indica esito positivo (valore restituito pari a zero) o negativo (un valore restituito diverso da zero).  Quando si usa l'azione 'q' per eseguire una query o meno in cui è installato un controller, il valore restituito sarà zero (0) se il controller non è già installato o uno (1) se l'installazione del controller.

Quando si rimuove un controller in Windows 10 ottobre 2018 Update o versioni precedenti, impostare il relativo stato disattivato tramite l'API in primo luogo, quindi chiamare lo strumento PerceptionSimulationDevice.

Si noti che questo strumento deve essere eseguito come amministratore.




## <a name="api-reference"></a>Informazioni di riferimento sulle API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

Descrive un tipo di dispositivo simulato

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

Un dispositivo di riferimento fittizio, il valore predefinito per PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

Descrive una modalità di arresto head

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

Intestazione predefinita di rilevamento. Ciò significa che il sistema può selezionare l'intestazione della migliore modalità in base alle condizioni di runtime di rilevamento.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

Orientamento Head solo rilevamento. Ciò significa che la posizione di rilevamento potrebbe non essere affidabile e alcune funzionalità dipende dalla posizione head potrebbero non essere disponibili.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

Rilevamento Head posizionale. Ciò significa che la posizione head rilevati e l'orientamento sono entrambi affidabile

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

Descrive un movimento simulato

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

Un valore di sentinel usato per non indicare nessun movimenti.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Un dito premuto movimento.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Un movimento del dito rilasciato.

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

Il movimento di sistema/home.

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

Il movimento valido massimo.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

Gli stati possibili di un controller simulato 6-gradi di libertà.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

Il controller i gradi di libertà 6 è stato disattivata.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

Il controller i gradi di libertà 6 è attivato e tiene traccia.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

Il controller di 6-gradi di libertà è attivato ma non può essere rilevato.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

I pulsanti supportati in un controller simulato 6-gradi di libertà.

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

Un valore di sentinel usato per non indicare nessun pulsante.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

Viene premuto il pulsante Home.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

Viene premuto il pulsante di Menu.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

Viene premuto il pulsante di triangolo di ridimensionamento.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

Il TouchPad è premuto.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

Viene premuto il pulsante di selezione.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

Il TouchPad viene manipolato.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

La levetta viene premuta.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

Il pulsante massimo valido.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

Lo stato di calibrazione degli occhi simulati

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

Non è disponibile la calibrazione occhi.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

Sono stati calibrati gli occhi.  Rappresenta il valore predefinito.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

Gli occhi sono in corso calibrati.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

È necessario essere tarato gli occhi.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

L'accuratezza di rilevamento di un join della lancetta.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

Join non viene rilevato.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

Posizione comune viene dedotto.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

La giunzione è registrata completamente.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

L'accuratezza di rilevamento di un join della lancetta.

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

Giunzioni dito dell'icona della mano siano configurati per riflettere una posa chiusa.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

Giunzioni dito dell'icona della mano sono configurati in modo da riflettere un posa open.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

Giunzioni dito dell'icona della mano siano configurati per riflettere una posa puntamento.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

Giunzioni dito dell'icona della mano siano configurati per riflettere una posa pinching.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

Il valore massimo valido per SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Descrive lo stato di una riproduzione.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

La registrazione è attualmente arrestato e pronto per la riproduzione.

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

La registrazione è in corso di riproduzione.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

La registrazione è attualmente sospeso.

**Microsoft.PerceptionSimulation.PlaybackState.End**

La registrazione ha raggiunto la fine.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Descrive un vettore di 3 componenti, che potrebbe descrivere un punto o un vettore nello spazio 3D.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

Componente X del vettore.

**Microsoft.PerceptionSimulation.Vector3.Y**

Componente Y del vettore.

**Microsoft.PerceptionSimulation.Vector3.Z**

Componente Z del vettore.

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

Creare un nuovo Vector3.

Parametri
* x - componente x del vettore.
* y - componente y del vettore.
* z - componente z del vettore.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Descrive una rotazione di 3 componenti.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

Il componente del passo di rotazione, in giù intorno all'asse X.

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Il componente di rotazione di rotazione, attorno all'asse Y.

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Il componente esegue il rollup di rotazione, attorno all'asse Z.

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

Creare un nuovo Rotation3.

Parametri
* pitch: il componente del passo della rotazione.
* rotazione - il componente di rotazione della rotazione.
* esegue il rollup - il componente esegue il rollup della rotazione.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

Descrive la configurazione di un join in una mano simulata.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

La posizione del join.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

La rotazione del join.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

L'accuratezza di rilevamento del join.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Vengono descritti di cono una visualizzazione, come viene generalmente utilizzato da una fotocamera.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

La distanza minima che è contenuta in del cono.

**Microsoft.PerceptionSimulation.Frustum.Far**

La distanza massima che è contenuta in del cono.

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

Il campo di visualizzazione orizzontale di cono, espresso in radianti (inferiori a PI).

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

Il rapporto di campo visivo orizzontale a campo di visualizzazione verticale.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Per la generazione di pacchetti usati per controllare un dispositivo di primo livello.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

Recuperare l'oggetto dispositivo simulato che interpreta l'umana simulata e tutto il mondo simulato.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

Recuperare l'oggetto che controlla l'umana simulata.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

Reimposta la simulazione allo stato predefinito.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

Interfaccia che descrive il dispositivo che interpreta tutto il mondo simulato e l'utente simulato

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

Recuperare la posizione di testa dal dispositivo simulato.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

Recuperare la posizione di mano dal dispositivo simulato.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

Impostare le proprietà del dispositivo simulato in modo che corrispondano il tipo di dispositivo specificato.

Parametri
* Type - il nuovo tipo di dispositivo simulato

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

Interfaccia che descrive la parte del dispositivo simulato che tiene traccia di inizio della finestra di umana simulata.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

Recupera e imposta la modalità di arresto head corrente.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

Interfaccia che descrive la parte del dispositivo simulato che rileva il movimento delle lancette dell'umana simulata

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Recuperare e impostare la posizione dello strumento di rilevamento mano simulato, rispetto al centro della testina.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Recuperare e impostare il passo verso il basso dello strumento di rilevamento mano simulato.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Recuperare e impostare se cono dello strumento di rilevamento mano simulato viene ignorato. Se ignorato, entrambe le mani sono sempre visibili. Quando non ignorare (impostazione predefinita) le mani sono visibili solo quando sono all'interno del cono dello strumento di rilevamento disponibili.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Recuperare e impostare le proprietà di cono utilizzate per determinare se sono visibili allo strumento di rilevamento mano simulato mani.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

Interfaccia di livello superiore per controllare l'umana simulata.

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

Recuperare e impostare la posizione del nodo in relazione al mondo, in metri. La posizione corrisponde a un punto al centro di metri dell'uomo.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

Recuperare e impostare la direzione i visi umani simulati in tutto il mondo. 0 radianti sia rivolto verso il basso l'asse Z negativo. Radianti positivi Ruota in senso orario intorno all'asse Y.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

Recuperare e impostare l'altezza di umana simulata, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

Recuperare la parte sinistra dell'umana simulata.

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

Recuperare il a destra dell'umana simulata.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

Recuperare l'intestazione dell'umana simulata.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

Spostare l'umana simulata rispetto alla posizione corrente, in metri.

Parametri
* Translation - la traduzione da spostare, rispetto alla posizione corrente.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Ruotare l'umana simulata rispetto alla relativa direzione correnti, in senso orario intorno all'asse Y

Parametri
* RADIANS - la quantità di rotazione intorno all'asse Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedHuman2

Proprietà aggiuntive sono disponibili eseguendo il cast di ISimulatedHuman a ISimulatedHuman2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**

Recuperare il controller a sinistra 6-gradi di libertà.

**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**

Recuperare il controller a destra i 6-gradi di libertà.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

Interfaccia che descrive una mano dell'umana simulata

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

Recuperare e impostare la posizione della mano simulata relativo umane, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

Recuperare e impostare se l'icona della mano è attualmente attivato.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

Sapere se l'icona della mano è attualmente visibile per il SimulatedDevice (ad esempio, se è in grado di rilevare il HandTracker).

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

Spostare l'icona della mano, che risulta visibile per il SimulatedDevice.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

Spostare la posizione della mano simulata rispetto alla posizione corrente, in metri.

Parametri
* Translation - quantità per convertire l'icona della mano simulato.

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Eseguire un gesto usando l'icona della mano simulato.  Verrà solo rilevata dal sistema se è abilitata l'icona della mano.

Parametri
* movimento - il movimento da eseguire.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

Proprietà aggiuntive sono disponibili eseguendo il cast di un ISimulatedHand a ISimulatedHand2.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

Recuperare o impostare la rotazione della mano simulata.  Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

Proprietà aggiuntive sono disponibili eseguendo il cast di un ISimulatedHand a ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

Ottenere la configurazione comune per la giunzione specificata.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

Impostare la configurazione comune per la giunzione specificata.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

Impostare l'icona della mano una posa nota con flag facoltativo per aggiungere un'animazione.  Nota: l'animazione non comportare giunzioni immediatamente che riflette le relative configurazioni joint finale.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Interfaccia che descrive l'inizio dell'umana simulata.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Recuperare la rotazione di testa simulata. Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Recuperare il diametro del head simulato. Questo valore viene utilizzato per determinare l'area dell'intestazione (punto di rotazione).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Ruotare la testa simulata rispetto alla rotazione corrente. Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.

Parametri
* rotazione - la quantità per ruotare.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

Proprietà aggiuntive sono disponibili eseguendo il cast di un ISimulatedHead a ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

Recuperare gli occhi dell'umana simulata.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

Interfaccia che descrivono un controller di 6-gradi di libertà associato l'umana simulata.

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

Recuperare o impostare lo stato corrente del controller.  Lo stato del controller deve essere impostato su un valore diverso da Off prima delle chiamate a spostare, ruotare e premere i pulsanti avranno esito positivo.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

Recuperare o impostare la posizione del controller simulato relativo umane, in metri.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

Recuperare o impostare l'orientamento del controller simulato.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

Spostare la posizione del controller simulato rispetto alla posizione corrente, in metri.

Parametri
* Translation - quantità per convertire il controller simulato.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

Premere un pulsante sul controller simulato.  Verrà solo rilevata dal sistema se il controller è abilitato.

Parametri
* pulsante - premere il pulsante.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

Rilascia un pulsante sul controller simulato.  Verrà solo rilevata dal sistema se il controller è abilitato.

Parametri
* pulsante - il rilascio.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition (out out float, float)**

Ottenere la posizione di un dito simulato su touchpad del controller simulato.

Parametri
* x - la posizione orizzontale del dito.
* y - la posizione verticale del dito.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**

Impostare la posizione di un dito simulato su touchpad del controller simulato.

Parametri
* x - la posizione orizzontale del dito.
* y - la posizione verticale del dito.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

I metodi e proprietà aggiuntive sono disponibili eseguendo il cast di un ISimulatedSixDofController a ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition (out out float, float)**

Ottenere la posizione del thumbstick simulato sul controller simulato.

Parametri
* x - la posizione orizzontale del thumbstick.
* y - la posizione verticale del thumbstick.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**

Impostare la posizione del thumbstick simulato sul controller simulato.

Parametri
* x - la posizione orizzontale del thumbstick.
* y - la posizione verticale del thumbstick.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

Recuperare o impostare il livello della batteria del controller simulato.  Il valore deve essere maggiore di 0,0 e minore o uguale a 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

Interfaccia che descrive gli occhi dell'umana simulata.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

Recuperare la rotazione degli occhi simulati. Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Ruota gli occhi simulati rispetto alla rotazione corrente. Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.

Parametri
* rotazione - la quantità per ruotare.

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

Recupera o imposta lo stato di calibrazione degli occhi simulati.

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

Recuperare la posizione del nodo in relazione al mondo, in metri.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

Caricare l'interfaccia per l'interazione con una registrazione singola per la riproduzione.

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

Recupera l'elenco dei tipi di dati della registrazione.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

Recupera lo stato corrente della registrazione.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

Avviare la riproduzione. Se è in pausa la registrazione, riproduzione verrà ripresa dal percorso in pausa; Se arrestato, la riproduzione inizierà all'inizio. Se già riproducendo, questa chiamata viene ignorata.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

Sospende la riproduzione nel percorso corrente. Se la registrazione viene arrestata, la chiamata viene ignorata.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

Cerca la registrazione per il tempo specificato (in 100 intervalli di nanosecondi dall'inizio) e del mouse viene posizionato nel percorso specificato. Se il tempo è oltre la fine della registrazione, è in pausa nell'ultimo fotogramma.

Parametri
* segni di graduazione - il tempo per cui eseguire la ricerca.

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Arresta la riproduzione e reimposta la posizione di inizio.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Interfaccia per la ricezione di modifiche di stato durante la riproduzione.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Chiamato quando di un ISimulationRecording riproduzione è stato.

Parametri
* newState - il nuovo stato della registrazione.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Oggetto radice per la creazione di oggetti di simulazione di percezione.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

Creare sull'oggetto per la generazione di pacchetti simulati e il recapito per il sink specificato.

Parametri
* sink - sink che riceverà generati tutti i pacchetti.

Valore restituito

Il gestore creato.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Creare un sink di cui sono archiviati i pacchetti ricevuti tutti in un file nel percorso specificato.

Parametri
* percorso: il percorso del file da creare.

Valore restituito

Il sink creato.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Caricare una registrazione dal file specificato.

Parametri
* percorso: il percorso del file da caricare.
* factory - una factory utilizzata per la registrazione per la creazione di un ISimulationStreamSink quando necessario.

Valore restituito

La registrazione caricata.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Caricare una registrazione dal file specificato.

Parametri
* percorso: il percorso del file da caricare.
* factory - una factory utilizzata per la registrazione per la creazione di un ISimulationStreamSink quando necessario.
* callback - aggiorna un callback che riceve il declassamento lo stato della registrazione.

Valore restituito

La registrazione caricata.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Descrive i diversi tipi di dati di flusso.

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

Un valore di sentinel usato per non indicare nessun tipo di dati di flusso.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Stream dei dati riguardanti la posizione e l'orientamento della testina.

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Stream dei dati riguardanti la posizione e i movimenti di mani.

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Stream dei dati relativi mapping spaziale dell'ambiente.

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Stream dei dati relativi al calibrazione del dispositivo. I pacchetti di calibrazione vengono accettati solo da un sistema in modalità remota.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Stream dei dati relativi all'ambiente del dispositivo.

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Un valore di sentinel usato per indicare tutti i tipi di dati registrati.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Oggetto che riceve i pacchetti di dati da un flusso di simulazione.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

Riceve un singolo pacchetto, ovvero internamente tipizzata e con controllo delle versioni.

Parametri
* Length - la lunghezza del pacchetto.
* pacchetto - i dati del pacchetto.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Oggetto che crea ISimulationStreamSink.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Crea una singola istanza di ISimulationStreamSink.

Valore restituito

Il sink creato.
