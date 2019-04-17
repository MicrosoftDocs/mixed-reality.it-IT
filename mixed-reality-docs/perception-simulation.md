---
title: Simulazione di percezione
description: Una Guida all'utilizzo della libreria di simulazione di percezione automatizzare input simulati per le applicazioni coinvolgenti
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, simulazione, test
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602203"
---
# <a name="perception-simulation"></a><span data-ttu-id="e4172-104">Simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="e4172-104">Perception simulation</span></span>

<span data-ttu-id="e4172-105">Si desidera creare un test automatizzato per l'app?</span><span class="sxs-lookup"><span data-stu-id="e4172-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="e4172-106">Eseguire i test per andare oltre a livello di componente di unit test e sperimentare effettivamente l'app end-to-end?</span><span class="sxs-lookup"><span data-stu-id="e4172-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="e4172-107">Simulazione di percezione è ciò che sta cercando.</span><span class="sxs-lookup"><span data-stu-id="e4172-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="e4172-108">La libreria di simulazione di percezione invia umane fittizio e dati di input world all'App in modo che è possibile automatizzare i test.</span><span class="sxs-lookup"><span data-stu-id="e4172-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="e4172-109">Ad esempio, è possibile simulare l'input di una ricerca umani a sinistra e destra e quindi eseguendo un movimento.</span><span class="sxs-lookup"><span data-stu-id="e4172-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="e4172-110">Simulazione di Perception può inviare l'input simulato simile al seguente a un HoloLens fisico, l'emulatore di HoloLens o un PC con il portale di realtà mista installato.</span><span class="sxs-lookup"><span data-stu-id="e4172-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="e4172-111">Percezione simulazione ignora i sensori in tempo reale in un dispositivo di realtà mista e invia simulati input per le applicazioni in esecuzione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e4172-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="e4172-112">Le applicazioni ricevono questi eventi di input fittizi tramite le stesse API sempre usate e non può indicare la differenza tra l'esecuzione con sensori reali e l'esecuzione con Perception simulazione.</span><span class="sxs-lookup"><span data-stu-id="e4172-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="e4172-113">Simulazione di percezione è la stessa tecnologia usata dall'emulatore di HoloLens inviare input simulato alla macchina virtuale di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e4172-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="e4172-114">Simulazione inizia creando un oggetto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e4172-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="e4172-115">Da tale oggetto, è possibile eseguire comandi per controllare le proprietà di un simulato "umano", tra cui posizione head mano posizione e i movimenti.</span><span class="sxs-lookup"><span data-stu-id="e4172-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="e4172-116">Configurazione di un progetto di Visual Studio per la simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="e4172-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="e4172-117">[Installare l'emulatore di HoloLens](install-the-tools.md) nel PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="e4172-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="e4172-118">L'emulatore include le librerie che si utilizzerà per la simulazione di percezione.</span><span class="sxs-lookup"><span data-stu-id="e4172-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="e4172-119">Creare un nuovo Visual Studio C# progetto desktop (un progetto Console è efficace per iniziare).</span><span class="sxs-lookup"><span data-stu-id="e4172-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="e4172-120">Aggiungere i file binari seguenti al progetto come riferimenti (progetto -> Aggiungi -> riferimento...). È possibile trovarli nella **% ProgramFiles (x86) %\Microsoft XDE\10.0.11082.0** una.</span><span class="sxs-lookup"><span data-stu-id="e4172-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="e4172-121">PerceptionSimulationManager.Interop.dll - gestito C# wrapper per la simulazione di percezione.</span><span class="sxs-lookup"><span data-stu-id="e4172-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="e4172-122">b.</span><span class="sxs-lookup"><span data-stu-id="e4172-122">b.</span></span> <span data-ttu-id="e4172-123">PerceptionSimulationRest.dll - libreria per la configurazione di un canale di comunicazione web socket nel HoloLens o nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="e4172-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="e4172-124">c.</span><span class="sxs-lookup"><span data-stu-id="e4172-124">c.</span></span> <span data-ttu-id="e4172-125">SimulationStream.Interop.dll - tipi condivisi per la simulazione.</span><span class="sxs-lookup"><span data-stu-id="e4172-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="e4172-126">Aggiungere l'implementazione PerceptionSimulationManager.dll binari al progetto un.</span><span class="sxs-lookup"><span data-stu-id="e4172-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="e4172-127">Prima di tutto aggiunto come un file binario del progetto (progetto -> Aggiungi -> elemento esistente...). Salvarlo come un collegamento in modo da non copiarla alla cartella di origine del progetto.</span><span class="sxs-lookup"><span data-stu-id="e4172-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="e4172-128">![Aggiungere al progetto come collegamento PerceptionSimulationManager.dll](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="e4172-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="e4172-129">Assicurarsi quindi di ottenere di copiati nella cartella di output in fase di compilazione.</span><span class="sxs-lookup"><span data-stu-id="e4172-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="e4172-130">Si tratta di una finestra delle proprietà per il file binario.</span><span class="sxs-lookup"><span data-stu-id="e4172-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="e4172-131">![Contrassegnare PerceptionSimulationManager.dll da copiare nella directory di output](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="e4172-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="e4172-132">Creazione di un oggetto di gestione IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="e4172-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="e4172-133">Per controllare la simulazione, si saranno rilasciare aggiornamenti agli oggetti recuperati da un oggetto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e4172-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="e4172-134">Il primo passo è ottenere quell'oggetto e connetterla a un emulatore o il dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="e4172-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="e4172-135">È possibile ottenere l'indirizzo IP all'emulatore facendo clic sul pulsante nel portale del dispositivo di [sulla barra degli strumenti](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="e4172-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="e4172-136">![Icona dispositivo portale aperta](images/emulator-deviceportal.png) **aprire il portale di dispositivo**: Aprire il Windows Device Portal per il sistema operativo HoloLens nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="e4172-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="e4172-137">In primo luogo, verrà chiamato per ottenere un oggetto RestSimulationStreamSink RestSimulationStreamSink.Create.</span><span class="sxs-lookup"><span data-stu-id="e4172-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="e4172-138">Questo è il dispositivo di destinazione o l'emulatore che consentono di controllare tramite una connessione http.</span><span class="sxs-lookup"><span data-stu-id="e4172-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="e4172-139">I comandi verranno passati a e gestiti dal [Windows Device Portal](using-the-windows-device-portal.md) in esecuzione nel dispositivo o emulatore.</span><span class="sxs-lookup"><span data-stu-id="e4172-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="e4172-140">I quattro parametri, devi creare un oggetto sono:</span><span class="sxs-lookup"><span data-stu-id="e4172-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="e4172-141">Uri di URI - indirizzo IP del dispositivo di destinazione (ad esempio, "http://123.123.123.123")</span><span class="sxs-lookup"><span data-stu-id="e4172-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="e4172-142">System.Net.NetworkCredential credenziali - nome utente/password per la connessione per il [Windows Device Portal](using-the-windows-device-portal.md) sul dispositivo di destinazione o un emulatore.</span><span class="sxs-lookup"><span data-stu-id="e4172-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="e4172-143">Se ci si connette all'emulatore tramite le 168 locale. *.* . \* indirizzo sullo stesso PC, verranno accettate le credenziali.</span><span class="sxs-lookup"><span data-stu-id="e4172-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="e4172-144">normale - bool True per priorità normale, false per priorità bassa.</span><span class="sxs-lookup"><span data-stu-id="e4172-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="e4172-145">In genere si desidera impostare l'opzione su *true* per scenari di test.</span><span class="sxs-lookup"><span data-stu-id="e4172-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="e4172-146">Token System.Threading.CancellationToken - Token per annullare l'operazione asincrona.</span><span class="sxs-lookup"><span data-stu-id="e4172-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="e4172-147">In secondo luogo si creerà il IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="e4172-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="e4172-148">Questo è l'oggetto da usare per controllare la simulazione.</span><span class="sxs-lookup"><span data-stu-id="e4172-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="e4172-149">Si noti che questa operazione deve anche essere eseguita in un metodo asincrono.</span><span class="sxs-lookup"><span data-stu-id="e4172-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="e4172-150">Controllare l'umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-150">Control the simulated Human</span></span>

<span data-ttu-id="e4172-151">Un IPerceptionSimulationManager dispone di una proprietà di risorse umane che restituisce un oggetto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="e4172-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="e4172-152">Per controllare l'uomo simulato, eseguire operazioni su questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="e4172-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="e4172-153">Ad esempio: </span><span class="sxs-lookup"><span data-stu-id="e4172-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="e4172-154">Esempio di base C# applicazione console</span><span class="sxs-lookup"><span data-stu-id="e4172-154">Basic Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="e4172-155">Estendere l'esempio C# applicazione console</span><span class="sxs-lookup"><span data-stu-id="e4172-155">Extended Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

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
        }
    }
}
```

## <a name="api-reference"></a><span data-ttu-id="e4172-156">Informazioni di riferimento sulle API</span><span class="sxs-lookup"><span data-stu-id="e4172-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="e4172-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="e4172-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="e4172-158">Descrive un tipo di dispositivo simulato</span><span class="sxs-lookup"><span data-stu-id="e4172-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="e4172-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="e4172-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="e4172-160">Un dispositivo di riferimento fittizio, il valore predefinito per PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e4172-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="e4172-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="e4172-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="e4172-162">Descrive una modalità di arresto head</span><span class="sxs-lookup"><span data-stu-id="e4172-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="e4172-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="e4172-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="e4172-164">Intestazione predefinita di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="e4172-164">Default Head Tracking.</span></span> <span data-ttu-id="e4172-165">Ciò significa che il sistema può selezionare l'intestazione della migliore modalità in base alle condizioni di runtime di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="e4172-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="e4172-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="e4172-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="e4172-167">Orientamento Head solo rilevamento.</span><span class="sxs-lookup"><span data-stu-id="e4172-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="e4172-168">Ciò significa che la posizione di rilevamento potrebbe non essere affidabile e alcune funzionalità dipende dalla posizione head potrebbero non essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="e4172-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="e4172-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="e4172-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="e4172-170">Rilevamento Head posizionale.</span><span class="sxs-lookup"><span data-stu-id="e4172-170">Positional Head Tracking.</span></span> <span data-ttu-id="e4172-171">Ciò significa che la posizione head rilevati e l'orientamento sono entrambi affidabile</span><span class="sxs-lookup"><span data-stu-id="e4172-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="e4172-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="e4172-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="e4172-173">Descrive un movimento simulato</span><span class="sxs-lookup"><span data-stu-id="e4172-173">Describes a simulated gesture</span></span>

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

<span data-ttu-id="e4172-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="e4172-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="e4172-175">Valore di sentinel usato per non indicare nessun movimenti</span><span class="sxs-lookup"><span data-stu-id="e4172-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="e4172-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="e4172-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="e4172-177">Un dito premuto movimento</span><span class="sxs-lookup"><span data-stu-id="e4172-177">A finger pressed gesture</span></span>

<span data-ttu-id="e4172-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="e4172-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="e4172-179">Un movimento del dito rilasciato</span><span class="sxs-lookup"><span data-stu-id="e4172-179">A finger released gesture</span></span>

<span data-ttu-id="e4172-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="e4172-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="e4172-181">Il movimento di casa</span><span class="sxs-lookup"><span data-stu-id="e4172-181">The home gesture</span></span>

<span data-ttu-id="e4172-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="e4172-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="e4172-183">Il movimento valido massimo</span><span class="sxs-lookup"><span data-stu-id="e4172-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="e4172-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="e4172-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="e4172-185">Descrive lo stato di una riproduzione</span><span class="sxs-lookup"><span data-stu-id="e4172-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="e4172-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="e4172-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="e4172-187">La registrazione è attualmente arrestato e pronto per la riproduzione</span><span class="sxs-lookup"><span data-stu-id="e4172-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="e4172-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="e4172-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="e4172-189">La registrazione in corso di riproduzione</span><span class="sxs-lookup"><span data-stu-id="e4172-189">The recording is currently playing</span></span>

<span data-ttu-id="e4172-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="e4172-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="e4172-191">La registrazione è attualmente in pausa</span><span class="sxs-lookup"><span data-stu-id="e4172-191">The recording is currently paused</span></span>

<span data-ttu-id="e4172-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="e4172-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="e4172-193">La registrazione ha raggiunto la fine</span><span class="sxs-lookup"><span data-stu-id="e4172-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="e4172-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="e4172-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="e4172-195">Viene descritto un vettore di 3 componenti, che potrebbe descrivere un punto o un vettore nello spazio 3D</span><span class="sxs-lookup"><span data-stu-id="e4172-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="e4172-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="e4172-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="e4172-197">Componente X del vettore</span><span class="sxs-lookup"><span data-stu-id="e4172-197">The X component of the vector</span></span>

<span data-ttu-id="e4172-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="e4172-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="e4172-199">Il componente Y del vettore</span><span class="sxs-lookup"><span data-stu-id="e4172-199">The Y component of the vector</span></span>

<span data-ttu-id="e4172-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="e4172-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="e4172-201">Componente Z del vettore</span><span class="sxs-lookup"><span data-stu-id="e4172-201">The Z component of the vector</span></span>

<span data-ttu-id="e4172-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="e4172-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="e4172-203">Creare un nuovo Vector3</span><span class="sxs-lookup"><span data-stu-id="e4172-203">Construct a new Vector3</span></span>

<span data-ttu-id="e4172-204">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-204">Parameters</span></span>
* <span data-ttu-id="e4172-205">x - componente x del vettore</span><span class="sxs-lookup"><span data-stu-id="e4172-205">x - The x component of the vector</span></span>
* <span data-ttu-id="e4172-206">y - componente y del vettore</span><span class="sxs-lookup"><span data-stu-id="e4172-206">y - The y component of the vector</span></span>
* <span data-ttu-id="e4172-207">z - componente z del vettore</span><span class="sxs-lookup"><span data-stu-id="e4172-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="e4172-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="e4172-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="e4172-209">Descrive una rotazione di 3 componenti</span><span class="sxs-lookup"><span data-stu-id="e4172-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="e4172-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="e4172-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="e4172-211">Il componente del passo di rotazione, in giù intorno all'asse X</span><span class="sxs-lookup"><span data-stu-id="e4172-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="e4172-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="e4172-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="e4172-213">Il componente di rotazione di rotazione, attorno all'asse Y</span><span class="sxs-lookup"><span data-stu-id="e4172-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="e4172-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="e4172-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="e4172-215">Il componente esegue il rollup di rotazione, attorno all'asse Z</span><span class="sxs-lookup"><span data-stu-id="e4172-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="e4172-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="e4172-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="e4172-217">Creare un nuovo Rotation3</span><span class="sxs-lookup"><span data-stu-id="e4172-217">Construct a new Rotation3</span></span>

<span data-ttu-id="e4172-218">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-218">Parameters</span></span>
* <span data-ttu-id="e4172-219">pitch: il componente del passo di rotazione</span><span class="sxs-lookup"><span data-stu-id="e4172-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="e4172-220">rotazione - il componente di rotazione della rotazione</span><span class="sxs-lookup"><span data-stu-id="e4172-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="e4172-221">eseguire il rollback, il componente esegue il rollup di rotazione</span><span class="sxs-lookup"><span data-stu-id="e4172-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="e4172-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="e4172-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="e4172-223">Vengono descritti di cono una visualizzazione, come viene generalmente utilizzato da una fotocamera</span><span class="sxs-lookup"><span data-stu-id="e4172-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="e4172-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="e4172-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="e4172-225">La distanza minima che è contenuta in del cono</span><span class="sxs-lookup"><span data-stu-id="e4172-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="e4172-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="e4172-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="e4172-227">La distanza massima che è contenuta in del cono</span><span class="sxs-lookup"><span data-stu-id="e4172-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="e4172-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="e4172-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="e4172-229">Campo visivo orizzontale del cono, espresso in radianti (inferiori a PI)</span><span class="sxs-lookup"><span data-stu-id="e4172-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="e4172-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="e4172-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="e4172-231">Il rapporto dei campo visivo orizzontale a campo di visualizzazione verticale</span><span class="sxs-lookup"><span data-stu-id="e4172-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="e4172-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e4172-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="e4172-233">Radice per la generazione di pacchetti usati per controllare un dispositivo</span><span class="sxs-lookup"><span data-stu-id="e4172-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="e4172-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="e4172-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="e4172-235">Recuperare l'oggetto dispositivo simulato che interpreta l'umana simulata e tutto il mondo simulato.</span><span class="sxs-lookup"><span data-stu-id="e4172-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="e4172-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="e4172-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="e4172-237">Recuperare l'oggetto che controlla l'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="e4172-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="e4172-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="e4172-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="e4172-239">Reimposta la simulazione allo stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="e4172-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="e4172-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="e4172-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="e4172-241">Interfaccia che descrive il dispositivo che interpreta tutto il mondo simulato e l'utente simulato</span><span class="sxs-lookup"><span data-stu-id="e4172-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="e4172-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="e4172-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="e4172-243">Recuperare la posizione di testa dal dispositivo simulato.</span><span class="sxs-lookup"><span data-stu-id="e4172-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="e4172-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="e4172-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="e4172-245">Recuperare la posizione di mano dal dispositivo simulato.</span><span class="sxs-lookup"><span data-stu-id="e4172-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="e4172-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="e4172-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="e4172-247">Impostare le proprietà del dispositivo simulato in modo che corrispondano il tipo di dispositivo specificato.</span><span class="sxs-lookup"><span data-stu-id="e4172-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="e4172-248">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-248">Parameters</span></span>
* <span data-ttu-id="e4172-249">Type - il nuovo tipo di dispositivo simulato</span><span class="sxs-lookup"><span data-stu-id="e4172-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="e4172-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="e4172-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="e4172-251">Interfaccia che descrive la parte del dispositivo simulato che tiene traccia di inizio della finestra di umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="e4172-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="e4172-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="e4172-253">Recupera e imposta la modalità di arresto head corrente.</span><span class="sxs-lookup"><span data-stu-id="e4172-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="e4172-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="e4172-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="e4172-255">Interfaccia che descrive la parte del dispositivo simulato che rileva il movimento delle lancette dell'umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="e4172-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e4172-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="e4172-257">Recuperare la posizione del nodo in relazione al mondo, in metri</span><span class="sxs-lookup"><span data-stu-id="e4172-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="e4172-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="e4172-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="e4172-259">Recuperare e impostare la posizione dello strumento di rilevamento mano simulato, rispetto al centro della testina.</span><span class="sxs-lookup"><span data-stu-id="e4172-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="e4172-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="e4172-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="e4172-261">Recuperare e impostare il passo verso il basso dello strumento di rilevamento mano simulato</span><span class="sxs-lookup"><span data-stu-id="e4172-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="e4172-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="e4172-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="e4172-263">Recuperare e impostare se cono dello strumento di rilevamento mano simulato viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="e4172-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="e4172-264">Se ignorato, entrambe le mani sono sempre visibili.</span><span class="sxs-lookup"><span data-stu-id="e4172-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="e4172-265">Quando non ignorare (impostazione predefinita) le mani sono visibili solo quando sono all'interno del cono dello strumento di rilevamento disponibili.</span><span class="sxs-lookup"><span data-stu-id="e4172-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="e4172-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="e4172-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="e4172-267">Recuperare e impostare le proprietà di cono utilizzate per determinare se sono visibili allo strumento di rilevamento mano simulato mani.</span><span class="sxs-lookup"><span data-stu-id="e4172-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="e4172-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="e4172-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="e4172-269">Interfaccia di livello superiore per controllare l'umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-269">Top level interface for controlling the simulated human</span></span>

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

<span data-ttu-id="e4172-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e4172-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="e4172-271">Recuperare e impostare la posizione del nodo in relazione al mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="e4172-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="e4172-272">La posizione corrisponde a un punto al centro di metri dell'uomo.</span><span class="sxs-lookup"><span data-stu-id="e4172-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="e4172-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="e4172-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="e4172-274">Recuperare e impostare la direzione i visi umani simulati in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="e4172-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="e4172-275">0 radianti sia rivolto verso il basso l'asse Z negativo.</span><span class="sxs-lookup"><span data-stu-id="e4172-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="e4172-276">Radianti positivi Ruota in senso orario intorno all'asse Y.</span><span class="sxs-lookup"><span data-stu-id="e4172-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="e4172-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="e4172-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="e4172-278">Recuperare e impostare l'altezza di umana simulata, in metri</span><span class="sxs-lookup"><span data-stu-id="e4172-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="e4172-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="e4172-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="e4172-280">Recuperare la parte sinistra dell'umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="e4172-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="e4172-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="e4172-282">Recuperare il a destra dell'umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="e4172-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="e4172-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="e4172-284">Recuperare l'intestazione dell'umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="e4172-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="e4172-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="e4172-286">Spostare l'umana simulata rispetto alla posizione corrente, in metri</span><span class="sxs-lookup"><span data-stu-id="e4172-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="e4172-287">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-287">Parameters</span></span>
* <span data-ttu-id="e4172-288">Translation - la traduzione da spostare, rispetto alla posizione corrente</span><span class="sxs-lookup"><span data-stu-id="e4172-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="e4172-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="e4172-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="e4172-290">Ruotare l'umana simulata rispetto alla relativa direzione correnti, in senso orario intorno all'asse Y</span><span class="sxs-lookup"><span data-stu-id="e4172-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="e4172-291">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-291">Parameters</span></span>
* <span data-ttu-id="e4172-292">RADIANS - la quantità di rotazione intorno all'asse Y</span><span class="sxs-lookup"><span data-stu-id="e4172-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="e4172-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="e4172-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="e4172-294">Interfaccia che descrive una mano dell'umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-294">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="e4172-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e4172-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="e4172-296">Recuperare la posizione del nodo in relazione al mondo, in metri</span><span class="sxs-lookup"><span data-stu-id="e4172-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="e4172-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="e4172-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="e4172-298">Recuperare e impostare la posizione della mano simulata relativo umane, in metri.</span><span class="sxs-lookup"><span data-stu-id="e4172-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="e4172-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="e4172-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="e4172-300">Recuperare e impostare se l'icona della mano è attualmente attivato.</span><span class="sxs-lookup"><span data-stu-id="e4172-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="e4172-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="e4172-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="e4172-302">Sapere se l'icona della mano è attualmente visibile per il SimulatedDevice (ad esempio, se è in grado di rilevare il HandTracker).</span><span class="sxs-lookup"><span data-stu-id="e4172-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="e4172-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="e4172-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="e4172-304">Spostare l'icona della mano, che risulta visibile per il SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="e4172-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="e4172-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="e4172-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="e4172-306">Spostare la posizione della mano simulata rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="e4172-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="e4172-307">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-307">Parameters</span></span>
* <span data-ttu-id="e4172-308">Translation - quantità per convertire l'icona della mano simulato</span><span class="sxs-lookup"><span data-stu-id="e4172-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="e4172-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="e4172-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="e4172-310">Eseguire un gesto usando l'icona della mano simulato (verrà rilevato dal sistema se è abilitata l'icona della mano).</span><span class="sxs-lookup"><span data-stu-id="e4172-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="e4172-311">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-311">Parameters</span></span>
* <span data-ttu-id="e4172-312">movimento - il movimento da eseguire</span><span class="sxs-lookup"><span data-stu-id="e4172-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="e4172-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="e4172-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="e4172-314">Interfaccia che descrive l'inizio dell'umana simulata</span><span class="sxs-lookup"><span data-stu-id="e4172-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="e4172-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="e4172-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="e4172-316">Recuperare la posizione del nodo in relazione al mondo, in metri</span><span class="sxs-lookup"><span data-stu-id="e4172-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="e4172-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="e4172-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="e4172-318">Recuperare la rotazione di testa simulata.</span><span class="sxs-lookup"><span data-stu-id="e4172-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="e4172-319">Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="e4172-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e4172-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="e4172-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="e4172-321">Recuperare il diametro del head simulato.</span><span class="sxs-lookup"><span data-stu-id="e4172-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="e4172-322">Questo valore viene utilizzato per determinare l'area dell'intestazione (punto di rotazione).</span><span class="sxs-lookup"><span data-stu-id="e4172-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="e4172-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="e4172-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="e4172-324">Ruotare la testa simulata rispetto alla rotazione corrente.</span><span class="sxs-lookup"><span data-stu-id="e4172-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="e4172-325">Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="e4172-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="e4172-326">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-326">Parameters</span></span>
* <span data-ttu-id="e4172-327">rotazione - la quantità per ruotare</span><span class="sxs-lookup"><span data-stu-id="e4172-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="e4172-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="e4172-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="e4172-329">Caricare l'interfaccia per l'interazione con una registrazione singola per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="e4172-329">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="e4172-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="e4172-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="e4172-331">Recupera l'elenco dei tipi di dati della registrazione.</span><span class="sxs-lookup"><span data-stu-id="e4172-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="e4172-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="e4172-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="e4172-333">Recupera lo stato corrente della registrazione.</span><span class="sxs-lookup"><span data-stu-id="e4172-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="e4172-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="e4172-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="e4172-335">Avviare la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="e4172-335">Start the playback.</span></span> <span data-ttu-id="e4172-336">Se è in pausa la registrazione, riproduzione verrà ripresa dal percorso in pausa; Se arrestato, la riproduzione inizierà all'inizio.</span><span class="sxs-lookup"><span data-stu-id="e4172-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="e4172-337">Se già riproducendo, questa chiamata viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="e4172-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="e4172-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="e4172-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="e4172-339">Sospende la riproduzione nel percorso corrente.</span><span class="sxs-lookup"><span data-stu-id="e4172-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="e4172-340">Se la registrazione viene arrestata, la chiamata viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="e4172-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="e4172-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="e4172-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="e4172-342">Cerca la registrazione per il tempo specificato (in 100 intervalli di nanosecondi dall'inizio) e del mouse viene posizionato nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="e4172-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="e4172-343">Se il tempo è oltre la fine della registrazione, è in pausa nell'ultimo fotogramma.</span><span class="sxs-lookup"><span data-stu-id="e4172-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="e4172-344">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-344">Parameters</span></span>
* <span data-ttu-id="e4172-345">segni di graduazione - il tempo per cui eseguire la ricerca</span><span class="sxs-lookup"><span data-stu-id="e4172-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="e4172-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="e4172-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="e4172-347">Arresta la riproduzione e reimposta la posizione di inizio</span><span class="sxs-lookup"><span data-stu-id="e4172-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="e4172-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="e4172-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="e4172-349">Interfaccia per la ricezione di modifiche di stato durante la riproduzione</span><span class="sxs-lookup"><span data-stu-id="e4172-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="e4172-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="e4172-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="e4172-351">Chiamato quando di un ISimulationRecording riproduzione è stato</span><span class="sxs-lookup"><span data-stu-id="e4172-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="e4172-352">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-352">Parameters</span></span>
* <span data-ttu-id="e4172-353">newState - il nuovo stato della registrazione</span><span class="sxs-lookup"><span data-stu-id="e4172-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="e4172-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="e4172-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="e4172-355">Oggetto radice per la creazione di oggetti di simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="e4172-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="e4172-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="e4172-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="e4172-357">Creare sull'oggetto per la generazione di pacchetti simulati e il recapito per il sink specificato.</span><span class="sxs-lookup"><span data-stu-id="e4172-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="e4172-358">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-358">Parameters</span></span>
* <span data-ttu-id="e4172-359">sink - sink che riceverà generati tutti i pacchetti</span><span class="sxs-lookup"><span data-stu-id="e4172-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="e4172-360">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e4172-360">Return value</span></span>

<span data-ttu-id="e4172-361">Il gestore creato</span><span class="sxs-lookup"><span data-stu-id="e4172-361">The created Manager</span></span>

<span data-ttu-id="e4172-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="e4172-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="e4172-363">Creare un sink di cui sono archiviati i pacchetti ricevuti tutti in un file nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="e4172-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="e4172-364">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-364">Parameters</span></span>
* <span data-ttu-id="e4172-365">percorso: il percorso del file da creare</span><span class="sxs-lookup"><span data-stu-id="e4172-365">path - The path of the file to create</span></span>

<span data-ttu-id="e4172-366">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e4172-366">Return value</span></span>

<span data-ttu-id="e4172-367">Il sink creato</span><span class="sxs-lookup"><span data-stu-id="e4172-367">The created sink</span></span>

<span data-ttu-id="e4172-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="e4172-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="e4172-369">Caricare una registrazione dal file specificato</span><span class="sxs-lookup"><span data-stu-id="e4172-369">Load a recording from the specified file</span></span>

<span data-ttu-id="e4172-370">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-370">Parameters</span></span>
* <span data-ttu-id="e4172-371">percorso: il percorso del file da caricare</span><span class="sxs-lookup"><span data-stu-id="e4172-371">path - The path of the file to load</span></span>
* <span data-ttu-id="e4172-372">factory - una factory utilizzata per la registrazione per la creazione di un ISimulationStreamSink quando necessario</span><span class="sxs-lookup"><span data-stu-id="e4172-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="e4172-373">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e4172-373">Return value</span></span>

<span data-ttu-id="e4172-374">La registrazione caricata</span><span class="sxs-lookup"><span data-stu-id="e4172-374">The loaded recording</span></span>

<span data-ttu-id="e4172-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="e4172-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="e4172-376">Caricare una registrazione dal file specificato</span><span class="sxs-lookup"><span data-stu-id="e4172-376">Load a recording from the specified file</span></span>

<span data-ttu-id="e4172-377">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-377">Parameters</span></span>
* <span data-ttu-id="e4172-378">percorso: il percorso del file da caricare</span><span class="sxs-lookup"><span data-stu-id="e4172-378">path - The path of the file to load</span></span>
* <span data-ttu-id="e4172-379">factory - una factory utilizzata per la registrazione per la creazione di un ISimulationStreamSink quando necessario</span><span class="sxs-lookup"><span data-stu-id="e4172-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="e4172-380">callback - un callback che riceve aggiornamenti il declassamento lo stato della registrazione</span><span class="sxs-lookup"><span data-stu-id="e4172-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="e4172-381">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e4172-381">Return value</span></span>

<span data-ttu-id="e4172-382">La registrazione caricata</span><span class="sxs-lookup"><span data-stu-id="e4172-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="e4172-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="e4172-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="e4172-384">Descrive i diversi tipi di dati di flusso</span><span class="sxs-lookup"><span data-stu-id="e4172-384">Describes the different types of stream data</span></span>

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

<span data-ttu-id="e4172-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="e4172-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="e4172-386">Valore di sentinel usato per non indicare nessun tipo di dati di flusso</span><span class="sxs-lookup"><span data-stu-id="e4172-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="e4172-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="e4172-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="e4172-388">Stream dei dati riguardanti la posizione e l'orientamento del capo</span><span class="sxs-lookup"><span data-stu-id="e4172-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="e4172-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="e4172-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="e4172-390">Stream dei dati riguardanti la posizione e i movimenti di mani</span><span class="sxs-lookup"><span data-stu-id="e4172-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="e4172-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="e4172-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="e4172-392">Stream dei dati relativi mapping spaziale dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="e4172-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="e4172-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="e4172-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="e4172-394">Stream dei dati relativi al calibrazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e4172-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="e4172-395">I pacchetti di calibrazione vengono accettati solo da un sistema in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="e4172-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="e4172-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="e4172-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="e4172-397">Stream dei dati relativi all'ambiente del dispositivo</span><span class="sxs-lookup"><span data-stu-id="e4172-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="e4172-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="e4172-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="e4172-399">Valore di sentinel usato per indicare tutti i tipi di dati registrati</span><span class="sxs-lookup"><span data-stu-id="e4172-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="e4172-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="e4172-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="e4172-401">Oggetto che riceve i pacchetti di dati da un flusso di simulazione</span><span class="sxs-lookup"><span data-stu-id="e4172-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="e4172-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="e4172-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="e4172-403">Riceve un singolo pacchetto, ovvero internamente tipizzata e con controllo delle versioni</span><span class="sxs-lookup"><span data-stu-id="e4172-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="e4172-404">Parametri</span><span class="sxs-lookup"><span data-stu-id="e4172-404">Parameters</span></span>
* <span data-ttu-id="e4172-405">Length - la lunghezza del pacchetto</span><span class="sxs-lookup"><span data-stu-id="e4172-405">length - The length of the packet</span></span>
* <span data-ttu-id="e4172-406">pacchetto - i dati del pacchetto</span><span class="sxs-lookup"><span data-stu-id="e4172-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="e4172-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="e4172-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="e4172-408">Oggetto che crea ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="e4172-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="e4172-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="e4172-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="e4172-410">Crea una singola istanza di ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="e4172-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="e4172-411">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="e4172-411">Return value</span></span>

<span data-ttu-id="e4172-412">Il sink creato</span><span class="sxs-lookup"><span data-stu-id="e4172-412">The created sink</span></span>
