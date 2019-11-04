---
title: Simulazione della percezione
description: Guida all'uso della libreria di simulazione della percezione per automatizzare l'input simulato per le applicazioni immersive
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, simulazione, test
ms.openlocfilehash: 503533bc5a2e9307b7c5217632d42670285aac0a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437542"
---
# <a name="perception-simulation"></a>Simulazione della percezione

Si vuole compilare un test automatizzato per l'app? Si desidera che i test vadano oltre il testing unità a livello di componente e che l'app venga effettivamente eseguita end-to-end? La simulazione della percezione è ciò che si sta cercando. La libreria di simulazione della percezione invia dati di input umani e internazionali all'app in modo che sia possibile automatizzare i test. Ad esempio, è possibile simulare l'input di un utente cercando una posizione specifica e ripetibile, quindi eseguendo un movimento o utilizzando un controller di movimento.

La simulazione della percezione può inviare input simulati come questo a un HoloLens fisico, l'emulatore di HoloLens (1a generazione), l'emulatore HoloLens 2 o un PC con il portale di realtà mista installato. La simulazione della percezione ignora i sensori dinamici in un dispositivo di realtà mista e invia un input simulato alle applicazioni in esecuzione sul dispositivo. Le applicazioni ricevono questi eventi di input tramite le stesse API che usano sempre e non possono indicare la differenza tra l'esecuzione con sensori reali e l'esecuzione con la simulazione della percezione. La simulazione della percezione è la stessa tecnologia usata dagli emulatori di HoloLens per inviare input simulato alla macchina virtuale HoloLens.

Per iniziare a usare la simulazione nel codice, iniziare creando un oggetto IPerceptionSimulationManager. Da tale oggetto, è possibile eseguire comandi per controllare le proprietà di un elemento "Human" simulato, inclusi posizione della testa, posizione della mano e movimenti, ed è possibile abilitare e modificare i controller di movimento.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Configurazione di un progetto di Visual Studio per la simulazione della percezione
1. [Installare l'emulatore di HoloLens](install-the-tools.md) nel PC di sviluppo. L'emulatore include le librerie che si utilizzeranno per la simulazione della percezione.
2. Creare un nuovo progetto desktop C# di Visual Studio (un progetto console è molto interessante per iniziare).
3. Aggiungere i file binari seguenti al progetto come riferimenti (informazioni di riferimento sul > di aggiunta di Project->...). È possibile trovarli in% ProgramFiles (x86)% \ Microsoft XDE\\(versione), ad esempio **% ProgramFiles (x86)% \ Microsoft XDE\\10.0.18362.0** per l'emulatore HoloLens 2.  Nota: anche se i file binari fanno parte dell'emulatore HoloLens 2, funzionano anche per la realtà mista di Windows sul desktop. un. Wrapper gestito C# da PerceptionSimulationManager. Interop. dll per la simulazione della percezione.
    b. PerceptionSimulationRest. dll-libreria per la configurazione di un canale di comunicazione del socket Web per HoloLens o emulatore.
    c. SimulationStream. Interop. dll: tipi condivisi per la simulazione.
4. Aggiungere il file binario di implementazione PerceptionSimulationManager. dll al progetto a. Per prima cosa, aggiungere il file come binario al progetto (> elemento esistente del > di progetto...). Salvarlo come collegamento in modo che non venga copiato nella cartella di origine del progetto. ![aggiungere PerceptionSimulationManager. dll al progetto come collegamento](images/saveaslink.png) b. Assicurarsi quindi che venga copiato nella cartella di output durante la compilazione. Si trova nella finestra delle proprietà per il file binario. ![contrassegnare PerceptionSimulationManager. dll per la copia nella directory di output](images/copyalways.png)
5. Impostare la piattaforma della soluzione attiva su x64.  Usare il Configuration Manager per creare una voce della piattaforma per x64, se non ne esiste già una.

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Creazione di un oggetto IPerceptionSimulation Manager

Per controllare la simulazione, è possibile eseguire aggiornamenti agli oggetti recuperati da un oggetto IPerceptionSimulationManager. Il primo passaggio consiste nell'ottenere l'oggetto e connetterlo al dispositivo o all'emulatore di destinazione. È possibile ottenere l'indirizzo IP dell'emulatore facendo clic sul pulsante portale del dispositivo sulla [barra degli strumenti](using-the-hololens-emulator.md) .

![icona Apri portale del dispositivo](images/emulator-deviceportal.png) **Apri portale**del dispositivo: aprire il portale del dispositivo Windows per il sistema operativo HoloLens nell'emulatore.  Per la realtà mista di Windows, questo può essere recuperato nell'app impostazioni in "Aggiorna & sicurezza", quindi "per sviluppatori" nella sezione "Connetti tramite:" in "abilitare il portale del dispositivo".  Assicurarsi di annotare l'indirizzo IP e la porta.

In primo luogo, si chiamerà RestSimulationStreamSink. create per ottenere un oggetto RestSimulationStreamSink. Si tratta del dispositivo o dell'emulatore di destinazione che si controllerà su una connessione HTTP. I comandi verranno passati e gestiti dal [portale del dispositivo Windows](using-the-windows-device-portal.md) in esecuzione nel dispositivo o nell'emulatore. I quattro parametri necessari per creare un oggetto sono:
* Uri URI-indirizzo IP del dispositivo di destinazione (ad esempio, "https://123.123.123.123" o "https://123.123.123.123:50080")
* System .NET. NetworkCredential credentials: nome utente/password per la connessione al [portale per dispositivi Windows](using-the-windows-device-portal.md) sul dispositivo o sull'emulatore di destinazione. Se ci si connette all'emulatore tramite l'indirizzo locale (ad esempio,*168...* *) nello stesso computer verranno accettate le credenziali.
* bool Normal-true per la priorità normale, false per priorità bassa. In genere è consigliabile impostare questo valore su *true* per gli scenari di test, che consente al test di assumere il controllo.  L'emulatore e la simulazione di realtà mista di Windows usano connessioni con priorità bassa.  Se il test USA anche una connessione con priorità bassa, la connessione stabilita più di recente sarà controllata.
* System. Threading. CancellationToken token-token per annullare l'operazione asincrona.

In secondo luogo viene creato il IPerceptionSimulationManager. Si tratta dell'oggetto usato per controllare la simulazione. Si noti che questa operazione deve essere eseguita anche in un metodo asincrono.

## <a name="control-the-simulated-human"></a>Controllare la persona simulata

Un IPerceptionSimulationManager ha una proprietà umana che restituisce un oggetto ISimulatedHuman. Per controllare l'uomo simulato, eseguire operazioni su questo oggetto. Ad esempio:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Applicazione console C# di esempio di base

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
                        new Uri("https://169.254.227.115"),
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

## <a name="extended-sample-c-console-application"></a>Applicazione console C# di esempio estesa

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
                        new Uri("https://169.254.227.115"),
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

## <a name="note-on-6-dof-controllers"></a>Nota sui controller da 6 a DOF

Prima di chiamare qualsiasi proprietà nei metodi in un controller 6-DOF simulato, è necessario attivare il controller.  In caso contrario, viene generata un'eccezione.  A partire dall'aggiornamento 2019 di Windows 10, è possibile installare e attivare i controller 6-DOF simulati impostando la proprietà Status dell'oggetto ISimulatedSixDofController su SimulatedSixDofControllerStatus. Active.
Nell'aggiornamento di Windows 10 ottobre 2018 e versioni precedenti, è necessario installare prima di tutto un controller 6-DOF simulato chiamando lo strumento PerceptionSimulationDevice disponibile nella cartella \Windows\System32.  L'utilizzo di questo strumento è il seguente:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Per esempio

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Le azioni supportate sono:
* i = install
* q = query
* r = Rimuovi

Le istanze supportate sono:
* 1 = il controller 6-DOF a sinistra
* 2 = il controller 6-DOF a destra

Il codice di uscita del processo indicherà l'esito positivo (un valore restituito pari a zero) o un errore (un valore restituito diverso da zero).  Quando si usa l'azione "q" per eseguire una query indipendentemente dal fatto che sia installato un controller, il valore restituito sarà zero (0) se il controller non è già installato o uno (1) se il controller è installato.

Quando si rimuove un controller nell'aggiornamento di Windows 10 ottobre 2018 o versioni precedenti, impostare lo stato su disattivato tramite l'API, quindi chiamare lo strumento PerceptionSimulationDevice.

Si noti che questo strumento deve essere eseguito come amministratore.




## <a name="api-reference"></a>Informazioni di riferimento sulle API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft. PerceptionSimulation. SimulatedDeviceType

Descrive un tipo di dispositivo simulato

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**

Un dispositivo di riferimento fittizio, il valore predefinito per PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft. PerceptionSimulation. HeadTrackerMode

Descrive la modalità Head Tracker

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft. PerceptionSimulation. HeadTrackerMode. default**

Rilevamento Head predefinito. Ciò significa che il sistema può selezionare la modalità di rilevamento Head migliore in base alle condizioni di Runtime.

**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**

Solo orientamento Head Tracking. Ciò significa che la posizione rilevata potrebbe non essere affidabile e che alcune funzionalità che dipendono dalla posizione Head potrebbero non essere disponibili.

**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**

Rilevamento Head posizionale. Ciò significa che la posizione e l'orientamento della testa rilevati sono entrambi affidabili

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft. PerceptionSimulation. SimulatedGesture

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

**Microsoft. PerceptionSimulation. SimulatedGesture. None**

Valore sentinella utilizzato per indicare nessun movimento.

**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**

Gesto premuto con un dito.

**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**

Gesto rilasciato da un dito.

**Microsoft. PerceptionSimulation. SimulatedGesture. Home**

Movimento Home/sistema.

**Microsoft. PerceptionSimulation. SimulatedGesture. max**

Il gesto massimo valido.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus

Gli stati possibili di un controller 6-DOF simulato.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. off**

Il controller 6-DOF è disattivato.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. Active**

Il controller 6-DOF è acceso e rilevato.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**

Il controller 6-DOF è acceso, ma non è possibile monitorarlo.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton

Pulsanti supportati in un controller 6-DOF simulato.

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

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**

Valore sentinella utilizzato per indicare l'assenza di pulsanti.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**

Viene premuto il pulsante Home.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. menu**

Viene premuto il pulsante di menu.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Grip**

Viene premuto il pulsante del grip.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**

Il TouchPad è premuto.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**

Viene premuto il pulsante Seleziona.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**

Il TouchPad viene toccato.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. levetta**

Viene premuto levetta.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. max**

Pulsante massimo valido.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState

Stato di calibrazione degli occhi simulati

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. non disponibile**

La calibrazione degli occhi non è disponibile.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**

Gli occhi sono stati calibrati.  Questo è il valore predefinito.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Configuring**

Gli occhi vengono calibrati.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**

È necessario calibrare gli occhi.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy

Accuratezza del rilevamento di una giunzione della mano.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. non disponibile**

Il giunto non viene rilevato.

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. approssimate**

La posizione congiunta viene dedotta.

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**

Il giunto è completamente monitorato.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft. PerceptionSimulation. SimulatedHandPose

Accuratezza del rilevamento di una giunzione della mano.

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

**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**

Le giunzioni del dito della mano sono configurate in modo da riflettere una posa chiusa.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**

Le giunzioni del dito della mano sono configurate in modo da riflettere una posa aperta.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**

Le giunzioni del dito della mano sono configurate in modo da riflettere una posa di puntamento.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Pinch**

Le giunzioni del dito della mano sono configurate in modo da riflettere una puntura.

**Microsoft. PerceptionSimulation. SimulatedHandPose. max**

Valore massimo valido per SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft. PerceptionSimulation. PlaybackState

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

**Microsoft. PerceptionSimulation. PlaybackState. Stopped**

La registrazione è attualmente arrestata e pronta per la riproduzione.

**Microsoft. PerceptionSimulation. PlaybackState. playing**

La registrazione è attualmente in riproduzione.

**Microsoft. PerceptionSimulation. PlaybackState. Paused**

La registrazione è attualmente sospesa.

**Microsoft. PerceptionSimulation. PlaybackState. end**

La registrazione ha raggiunto la fine.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft. PerceptionSimulation. Vector3

Descrive un vettore di 3 componenti, che può descrivere un punto o un vettore nello spazio 3D.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft. PerceptionSimulation. Vector3. X**

Componente X del vettore.

**Microsoft. PerceptionSimulation. Vector3. Y**

Componente Y del vettore.

**Microsoft. PerceptionSimulation. Vector3. Z**

Componente Z del vettore.

**Microsoft. PerceptionSimulation. Vector3. #ctor (System. Single, System. Single, System. Single)**

Costruire un nuovo Vector3.

Parametri
* x: componente x del vettore.
* y: componente y del vettore.
* z: componente z del vettore.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft. PerceptionSimulation. Rotation3

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

**Microsoft. PerceptionSimulation. Rotation3. Pitch**

Componente pitch della rotazione, verso il basso attorno all'asse X.

**Microsoft. PerceptionSimulation. Rotation3. imbardata**

Componente di imbardata della rotazione, immediatamente intorno all'asse Y.

**Microsoft. PerceptionSimulation. Rotation3. roll**

Componente di roll della rotazione, immediatamente intorno all'asse Z.

**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. Single, System. Single, System. Single)**

Costruire un nuovo Rotation3.

Parametri
* Pitch: componente pitch della rotazione.
* imbardata: componente imbardata della rotazione.
* Roll-il componente roll della rotazione.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration

Descrive la configurazione di un insieme in una mano simulata.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**

Posizione della giunzione.

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**

Rotazione della giunzione.

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**

Accuratezza del rilevamento della giunzione.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft. PerceptionSimulation. tronco

Descrive una vista tronco, usata in genere da una fotocamera.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft. PerceptionSimulation. tronco. near**

Distanza minima contenuta in tronco.

**Microsoft. PerceptionSimulation. tronco. lontano**

Distanza massima contenuta in tronco.

**Microsoft. PerceptionSimulation. tronco. FieldOfView**

Campo orizzontale della visualizzazione di tronco, in radianti (minore di PI).

**Microsoft. PerceptionSimulation. tronco. AspectRatio**

Rapporto tra il campo orizzontale e la visualizzazione e il campo verticale della visualizzazione.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft. PerceptionSimulation. IPerceptionSimulationManager

Radice per la generazione dei pacchetti usati per controllare un dispositivo.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**

Recuperare l'oggetto dispositivo simulato che interpreta l'uomo simulato e il mondo simulato.

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**

Recuperare l'oggetto che controlla l'uomo simulato.

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**

Reimposta lo stato predefinito della simulazione.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft. PerceptionSimulation. ISimulatedDevice

Interfaccia che descrive il dispositivo che interpreta il mondo simulato e l'uomo simulato

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**

Recuperare l'Head Tracker dal dispositivo simulato.

**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**

Recuperare il Tracker mano dal dispositivo simulato.

**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**

Impostare le proprietà del dispositivo simulato in modo che corrispondano al tipo di dispositivo specificato.

Parametri
* Tipo: nuovo tipo di dispositivo simulato

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft. PerceptionSimulation. ISimulatedHeadTracker

Interfaccia che descrive la parte del dispositivo simulato che tiene traccia del titolo dell'uomo simulato.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**

Recupera e imposta la modalità di rilevamento Head corrente.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft. PerceptionSimulation. ISimulatedHandTracker

Interfaccia che descrive la parte del dispositivo simulato che tiene traccia delle mani dell'uomo simulato

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

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**

Recuperare la posizione del nodo con la relazione con il mondo, in metri.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**

Recuperare e impostare la posizione della traccia a mano simulata, relativa al centro della testa.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Pitch**

Recuperare e impostare il passo verso il basso della traccia a mano simulata.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**

Recuperare e impostare se il tronco della traccia a mano simulata viene ignorato. Quando viene ignorato, entrambe le mani sono sempre visibili. Quando non vengono ignorate (impostazione predefinita), le mani sono visibili solo quando si trovano all'interno del tronco della traccia a mano.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. tronco**

Recuperare e impostare le proprietà tronco usate per determinare se le mani sono visibili per la traccia a mano simulata.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft. PerceptionSimulation. ISimulatedHuman

Interfaccia di primo livello per il controllo dell'uomo simulato.

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

**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**

Recuperare e impostare la posizione del nodo con la relazione con il mondo, in metri. La posizione corrisponde a un punto al centro dei piedi dell'uomo.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**

Recuperare e impostare la direzione dei visi umani simulati nel mondo. 0 radianti si affacciano sull'asse Z negativo. Radianti positivi ruotano in senso orario sull'asse Y.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**

Recuperare e impostare l'altezza dell'oggetto umano simulato, in metri.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Mancini**

Recuperare il lato sinistro dell'oggetto umano simulato.

**Microsoft. PerceptionSimulation. ISimulatedHuman. destra**

Recuperare la mano giusta dell'uomo simulato.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**

Recuperare l'intestazione dell'uomo simulato.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**

Spostare l'oggetto umano simulato rispetto alla posizione corrente, in metri.

Parametri
* Translation: la traduzione da spostare rispetto alla posizione corrente.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**

Ruotare l'oggetto umano simulato rispetto alla direzione corrente, in senso orario sull'asse Y

Parametri
* radianti: la quantità da ruotare intorno all'asse Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft. PerceptionSimulation. ISimulatedHuman2

Sono disponibili proprietà aggiuntive eseguendo il cast di ISimulatedHuman a ISimulatedHuman2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**

Recuperare il controller 6-DOF a sinistra.

**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**

Recuperare il controller 6-DOF a destra.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft. PerceptionSimulation. ISimulatedHand

Interfaccia che descrive una mano dell'uomo simulato

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

**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**

Recuperare la posizione del nodo con la relazione con il mondo, in metri.

**Microsoft. PerceptionSimulation. ISimulatedHand. Position**

Recuperare e impostare la posizione della mano simulata rispetto all'oggetto umano, in metri.

**Microsoft. PerceptionSimulation. ISimulatedHand. Activated**

Recuperare e impostare se la mano è attualmente attivata.

**Microsoft. PerceptionSimulation. ISimulatedHand. Visible**

Recuperare se la mano è attualmente visibile a SimulatedDevice (ad esempio, se si trova in una posizione che deve essere rilevata da HandTracker).

**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**

Spostare la mano in modo che sia visibile a SimulatedDevice.

**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**

Spostare la posizione della mano simulata rispetto alla posizione corrente, in metri.

Parametri
* Translation: la quantità per tradurre la mano simulata.

**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**

Eseguire un movimento usando la mano simulata.  Verrà rilevato solo dal sistema se la mano è abilitata.

Parametri
* Gesture: movimento da eseguire.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft. PerceptionSimulation. ISimulatedHand2

Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHand a ISimulatedHand2.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**

Recuperare o impostare la rotazione della mano simulata.  Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft. PerceptionSimulation. ISimulatedHand3

Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHand in ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**

Ottiene la configurazione congiunta per il giunto specificato.

**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**

Imposta la configurazione congiunta per il giunto specificato.

**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**

Impostare la mano su una forma nota con un flag facoltativo a cui aggiungere un'animazione.  Nota: l'animazione non comporterà l'aggiunta immediata di giunzioni che riflettono le configurazioni finali.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft. PerceptionSimulation. ISimulatedHead

Interfaccia che descrive l'intestazione dell'uomo simulato.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**

Recuperare la posizione del nodo con la relazione con il mondo, in metri.

**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**

Recuperare la rotazione della testa simulata. Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.

**Microsoft. PerceptionSimulation. ISimulatedHead. Diametr**

Recuperare il diametro della testa simulata. Questo valore viene usato per determinare il centro della testa (punto di rotazione).

**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**

Ruota la testa simulata rispetto alla rotazione corrente. Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.

Parametri
* Rotation: quantità da ruotare.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft. PerceptionSimulation. ISimulatedHead2

Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHead in ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHead2. Eyes**

Recuperare gli occhi dell'uomo simulato.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft. PerceptionSimulation. ISimulatedSixDofController

Interfaccia che descrive un controller 6-DOF associato all'uomo simulato.

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

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**

Recuperare la posizione del nodo con la relazione con il mondo, in metri.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**

Recuperare o impostare lo stato corrente del controller.  Lo stato del controller deve essere impostato su un valore diverso da off prima che tutte le chiamate per lo spostamento, la rotazione o la pressione dei pulsanti abbiano esito positivo.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**

Recuperare o impostare la posizione del controller simulato rispetto all'oggetto umano, in metri.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**

Recupera o imposta l'orientamento del controller simulato.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**

Spostare la posizione del controller simulato rispetto alla posizione corrente, in metri.

Parametri
* Translation: quantità di conversione del controller simulato.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**

Premere un pulsante sul controller simulato.  Verrà rilevato solo dal sistema se il controller è abilitato.

Parametri
* Button-pulsante da premere.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**

Rilasciare un pulsante sul controller simulato.  Verrà rilevato solo dal sistema se il controller è abilitato.

Parametri
* Button-pulsante da rilasciare.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**

Ottiene la posizione di un dito simulato nel touchpad del controller simulato.

Parametri
* x: posizione orizzontale del dito.
* y: posizione verticale del dito.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**

Imposta la posizione di un dito simulato nel touchpad del controller simulato.

Parametri
* x: posizione orizzontale del dito.
* y: posizione verticale del dito.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft. PerceptionSimulation. ISimulatedSixDofController2

Sono disponibili proprietà e metodi aggiuntivi eseguendo il cast di un ISimulatedSixDofController in ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**

Ottiene la posizione della levetta simulata sul controller simulato.

Parametri
* x: posizione orizzontale di levetta.
* y: posizione verticale del levetta.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**

Impostare la posizione della levetta simulata sul controller simulato.

Parametri
* x: posizione orizzontale di levetta.
* y: posizione verticale del levetta.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**

Recuperare o impostare il livello di batteria del controller simulato.  Il valore deve essere maggiore di 0,0 e minore o uguale a 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft. PerceptionSimulation. ISimulatedEyes

Interfaccia che descrive gli occhi dell'uomo simulato.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**

Recuperare la rotazione degli occhi simulati. Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.

**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**

Ruotare gli occhi simulati rispetto alla rotazione corrente. Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.

Parametri
* Rotation: quantità da ruotare.

**Microsoft. PerceptionSimulation. ISimulatedEyes. CalibrationState**

Recupera o imposta lo stato di calibrazione degli occhi simulati.

**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**

Recuperare la posizione del nodo con la relazione con il mondo, in metri.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft. PerceptionSimulation. ISimulationRecording

Interfaccia per l'interazione con una singola registrazione caricata per la riproduzione.

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

**Microsoft. PerceptionSimulation. ISimulationRecording. DataTypes**

Recupera l'elenco dei tipi di dati nella registrazione.

**Microsoft. PerceptionSimulation. ISimulationRecording. state**

Recupera lo stato corrente della registrazione.

**Microsoft. PerceptionSimulation. ISimulationRecording. Play**

Avviare la riproduzione. Se la registrazione viene sospesa, la riproduzione riprenderà dal percorso sospeso; Se arrestata, la riproduzione inizierà dall'inizio. Se è già in esecuzione, questa chiamata viene ignorata.

**Microsoft. PerceptionSimulation. ISimulationRecording. pause**

Sospende la riproduzione nella posizione corrente. Se la registrazione viene arrestata, la chiamata viene ignorata.

**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**

Cerca la registrazione per il tempo specificato (in intervalli di 100 nanosecondi dall'inizio) e si ferma in corrispondenza di tale posizione. Se l'ora supera la fine della registrazione, viene sospesa in corrispondenza dell'ultimo frame.

Parametri
* cicli: il tempo in cui eseguire la ricerca.

**Microsoft. PerceptionSimulation. ISimulationRecording. Stop**

Arresta la riproduzione e reimposta la posizione iniziale.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft. PerceptionSimulation. ISimulationRecordingCallback

Interfaccia per la ricezione delle modifiche di stato durante la riproduzione.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**

Chiamato quando viene modificato lo stato di riproduzione di un ISimulationRecording.

Parametri
* newState: nuovo stato della registrazione.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft. PerceptionSimulation. PerceptionSimulationManager

Oggetto radice per la creazione di oggetti di simulazione della percezione.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**

Creare sull'oggetto per generare pacchetti simulati e distribuirli al sink fornito.

Parametri
* sink: sink che riceverà tutti i pacchetti generati.

Valore restituito

Gestore creato.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**

Consente di creare un sink che archivia tutti i pacchetti ricevuti in un file nel percorso specificato.

Parametri
* Path: percorso del file da creare.

Valore restituito

Sink creato.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**

Carica una registrazione dal file specificato.

Parametri
* Path: percorso del file da caricare.
* Factory: Factory usata dalla registrazione per la creazione di un ISimulationStreamSink quando richiesto.

Valore restituito

Registrazione caricata.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**

Carica una registrazione dal file specificato.

Parametri
* Path: percorso del file da caricare.
* Factory: Factory usata dalla registrazione per la creazione di un ISimulationStreamSink quando richiesto.
* callback: callback che riceve aggiornamenti che rigradano lo stato della registrazione.

Valore restituito

Registrazione caricata.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft. PerceptionSimulation. StreamDataTypes

Vengono descritti i diversi tipi di dati di flusso.

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

**Microsoft. PerceptionSimulation. StreamDataTypes. None**

Valore sentinella utilizzato per indicare nessun tipo di dati di flusso.

**Microsoft. PerceptionSimulation. StreamDataTypes. Head**

Flusso di dati relativi alla posizione e all'orientamento della testa.

**Microsoft. PerceptionSimulation. StreamDataTypes. Hands**

Flusso di dati relativi alla posizione e ai movimenti delle mani.

**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**

Flusso di dati relativi al mapping spaziale dell'ambiente.

**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**

Flusso di dati relativi alla calibrazione del dispositivo. I pacchetti di calibrazione sono accettati solo da un sistema in modalità remota.

**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**

Flusso dei dati relativi all'ambiente del dispositivo.

**Microsoft. PerceptionSimulation. StreamDataTypes. All**

Valore sentinella utilizzato per indicare tutti i tipi di dati registrati.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft. PerceptionSimulation. ISimulationStreamSink

Oggetto che riceve pacchetti di dati da un flusso di simulazione.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint length, byte [] Packet)**

Riceve un singolo pacchetto, che è tipizzato internamente e con controllo delle versioni.

Parametri
* length: lunghezza del pacchetto.
* Packet: dati del pacchetto.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory

Oggetto che crea ISimulationStreamSink.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**

Crea una singola istanza di ISimulationStreamSink.

Valore restituito

Sink creato.
