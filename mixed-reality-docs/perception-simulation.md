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
# <a name="perception-simulation"></a><span data-ttu-id="668fb-104">Simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="668fb-104">Perception simulation</span></span>

<span data-ttu-id="668fb-105">Si desidera creare un test automatizzato per l'app?</span><span class="sxs-lookup"><span data-stu-id="668fb-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="668fb-106">Eseguire i test per andare oltre a livello di componente di unit test e sperimentare effettivamente l'app end-to-end?</span><span class="sxs-lookup"><span data-stu-id="668fb-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="668fb-107">Simulazione di percezione è ciò che sta cercando.</span><span class="sxs-lookup"><span data-stu-id="668fb-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="668fb-108">La libreria di simulazione di percezione invia umana e world dati all'app di input in modo che è possibile automatizzare i test.</span><span class="sxs-lookup"><span data-stu-id="668fb-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="668fb-109">Ad esempio, è possibile simulare l'input di una risorse umane alla ricerca in una posizione specifica, ripetibile e quindi eseguendo un movimento o utilizzando un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="668fb-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="668fb-110">Simulazione di percezione può inviare l'input simulato simile al seguente a un HoloLens fisico, l'emulatore di HoloLens (dal 1 ° generazione), installato HoloLens 2 emulatore o un PC con il portale di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="668fb-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="668fb-111">Percezione simulazione ignora i sensori in tempo reale in un dispositivo di realtà mista e invia simulati input per le applicazioni in esecuzione nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="668fb-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="668fb-112">Le applicazioni ricevono questi eventi di input tramite le stesse API sempre utilizzano e non può indicare la differenza tra l'esecuzione con sensori reali e l'esecuzione con Perception simulazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="668fb-113">Simulazione di percezione è la stessa tecnologia usata per gli emulatori di HoloLens inviare input simulato alla macchina virtuale di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="668fb-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="668fb-114">Per iniziare a usare simulazione nel codice, iniziare creando un oggetto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="668fb-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="668fb-115">Da tale oggetto, è possibile eseguire comandi per controllare le proprietà di un simulato "umano", tra cui posizione head mano posizione e i movimenti, ed è possibile abilitare e modificare i controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="668fb-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="668fb-116">Configurazione di un progetto di Visual Studio per la simulazione di percezione</span><span class="sxs-lookup"><span data-stu-id="668fb-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="668fb-117">[Installare l'emulatore di HoloLens](install-the-tools.md) nel PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="668fb-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="668fb-118">L'emulatore include le librerie che si utilizzerà per la simulazione di percezione.</span><span class="sxs-lookup"><span data-stu-id="668fb-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="668fb-119">Creare un nuovo Visual Studio C# progetto desktop (un progetto Console è efficace per iniziare).</span><span class="sxs-lookup"><span data-stu-id="668fb-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="668fb-120">Aggiungere i file binari seguenti al progetto come riferimenti (progetto -> Aggiungi -> riferimento...). È possibile trovarli in % ProgramFiles (x86) %\Microsoft XDE\\(versione), ad esempio **% ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** per l'emulatore di 2 HoloLens.</span><span class="sxs-lookup"><span data-stu-id="668fb-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="668fb-121">(Nota: anche se i file binari fanno parte dell'emulatore 2 HoloLens, funzionano anche per realtà mista di Windows sul desktop.) a.</span><span class="sxs-lookup"><span data-stu-id="668fb-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="668fb-122">PerceptionSimulationManager.Interop.dll - gestito C# wrapper per la simulazione di percezione.</span><span class="sxs-lookup"><span data-stu-id="668fb-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="668fb-123">b.</span><span class="sxs-lookup"><span data-stu-id="668fb-123">b.</span></span> <span data-ttu-id="668fb-124">PerceptionSimulationRest.dll - libreria per la configurazione di un canale di comunicazione web socket nel HoloLens o nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="668fb-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="668fb-125">c.</span><span class="sxs-lookup"><span data-stu-id="668fb-125">c.</span></span> <span data-ttu-id="668fb-126">SimulationStream.Interop.dll - tipi condivisi per la simulazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="668fb-127">Aggiungere l'implementazione PerceptionSimulationManager.dll binari al progetto un.</span><span class="sxs-lookup"><span data-stu-id="668fb-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="668fb-128">Prima di tutto aggiunto come un file binario del progetto (progetto -> Aggiungi -> elemento esistente...). Salvarlo come un collegamento in modo da non copiarla alla cartella di origine del progetto.</span><span class="sxs-lookup"><span data-stu-id="668fb-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="668fb-129">![Aggiungere al progetto come collegamento PerceptionSimulationManager.dll](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="668fb-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="668fb-130">Assicurarsi quindi di ottenere di copiati nella cartella di output in fase di compilazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="668fb-131">Si tratta di una finestra delle proprietà per il file binario.</span><span class="sxs-lookup"><span data-stu-id="668fb-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="668fb-132">![Contrassegnare PerceptionSimulationManager.dll da copiare nella directory di output](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="668fb-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="668fb-133">Impostare la piattaforma soluzione attiva su x64.</span><span class="sxs-lookup"><span data-stu-id="668fb-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="668fb-134">(Uso di Configuration Manager per creare una voce di piattaforma per x64, se non esiste già).</span><span class="sxs-lookup"><span data-stu-id="668fb-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="668fb-135">Creazione di un oggetto di gestione IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="668fb-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="668fb-136">Per controllare la simulazione, si saranno rilasciare aggiornamenti agli oggetti recuperati da un oggetto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="668fb-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="668fb-137">Il primo passo è ottenere quell'oggetto e connetterla a un emulatore o il dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="668fb-138">È possibile ottenere l'indirizzo IP all'emulatore facendo clic sul pulsante nel portale del dispositivo di [sulla barra degli strumenti](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="668fb-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="668fb-139">![Icona dispositivo portale aperta](images/emulator-deviceportal.png) **aprire il portale di dispositivo**: apre il Portale di dispositivi di Windows per il sistema operativo di HoloLens nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="668fb-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="668fb-140">Per realtà mista di Windows, questo può essere recuperato nell'app impostazioni nel gruppo "Aggiornamento e sicurezza" e quindi "per gli sviluppatori" nel "Connetti tramite:" sezione "Enable Device Portal".</span><span class="sxs-lookup"><span data-stu-id="668fb-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="668fb-141">Assicurarsi di prendere nota sia l'indirizzo IP e porta.</span><span class="sxs-lookup"><span data-stu-id="668fb-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="668fb-142">In primo luogo, verrà chiamato per ottenere un oggetto RestSimulationStreamSink RestSimulationStreamSink.Create.</span><span class="sxs-lookup"><span data-stu-id="668fb-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="668fb-143">Questo è il dispositivo di destinazione o l'emulatore che consentono di controllare tramite una connessione http.</span><span class="sxs-lookup"><span data-stu-id="668fb-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="668fb-144">I comandi verranno passati a e gestiti dal [Windows Device Portal](using-the-windows-device-portal.md) in esecuzione nel dispositivo o emulatore.</span><span class="sxs-lookup"><span data-stu-id="668fb-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="668fb-145">I quattro parametri, devi creare un oggetto sono:</span><span class="sxs-lookup"><span data-stu-id="668fb-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="668fb-146">Uri di URI - indirizzo IP del dispositivo di destinazione (ad esempio, "http://123.123.123.123"o"http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="668fb-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="668fb-147">System.Net.NetworkCredential credenziali - nome utente/password per la connessione per il [Windows Device Portal](using-the-windows-device-portal.md) sul dispositivo di destinazione o un emulatore.</span><span class="sxs-lookup"><span data-stu-id="668fb-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="668fb-148">Se ci si connette all'emulatore tramite il relativo indirizzo locale (ad esempio, 168. *.* . \*) sullo stesso PC, verranno accettate le credenziali.</span><span class="sxs-lookup"><span data-stu-id="668fb-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="668fb-149">normale - bool True per priorità normale, false per priorità bassa.</span><span class="sxs-lookup"><span data-stu-id="668fb-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="668fb-150">In genere si desidera impostare l'opzione su *true* per scenari di test, che consente il test di assumere il controllo.</span><span class="sxs-lookup"><span data-stu-id="668fb-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="668fb-151">L'emulatore e la simulazione di realtà mista di Windows Usa le connessioni per priorità bassa.</span><span class="sxs-lookup"><span data-stu-id="668fb-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="668fb-152">Se il test Usa anche una connessione per priorità bassa, più recentemente stabilita connessione verrà nel controllo.</span><span class="sxs-lookup"><span data-stu-id="668fb-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="668fb-153">Token System.Threading.CancellationToken - Token per annullare l'operazione asincrona.</span><span class="sxs-lookup"><span data-stu-id="668fb-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="668fb-154">In secondo luogo si creerà il IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="668fb-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="668fb-155">Questo è l'oggetto da usare per controllare la simulazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="668fb-156">Si noti che questa operazione deve anche essere eseguita in un metodo asincrono.</span><span class="sxs-lookup"><span data-stu-id="668fb-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="668fb-157">Controllare l'umana simulata</span><span class="sxs-lookup"><span data-stu-id="668fb-157">Control the simulated Human</span></span>

<span data-ttu-id="668fb-158">Un IPerceptionSimulationManager dispone di una proprietà di risorse umane che restituisce un oggetto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="668fb-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="668fb-159">Per controllare l'uomo simulato, eseguire operazioni su questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="668fb-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="668fb-160">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="668fb-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="668fb-161">Esempio di base C# applicazione console</span><span class="sxs-lookup"><span data-stu-id="668fb-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="668fb-162">Estendere l'esempio C# applicazione console</span><span class="sxs-lookup"><span data-stu-id="668fb-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="668fb-163">Si noti nei controller di 6-gradi di libertà</span><span class="sxs-lookup"><span data-stu-id="668fb-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="668fb-164">Prima di chiamare qualsiasi proprietà nei metodi in un controller simulato-i gradi di libertà 6, è necessario attivare il controller.</span><span class="sxs-lookup"><span data-stu-id="668fb-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="668fb-165">Non eseguire questa operazione comporterà un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="668fb-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="668fb-166">A partire da Windows 10 possono aggiornare 2019, possono essere installati e attivati impostando la proprietà Status dell'oggetto ISimulatedSixDofController su SimulatedSixDofControllerStatus.Active controller simulato 6-gradi di libertà.</span><span class="sxs-lookup"><span data-stu-id="668fb-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="668fb-167">In Windows 10 ottobre 2018 Update e versioni precedenti, è necessario installare un controller simulato 6-gradi di libertà prima di tutto, chiamare lo strumento PerceptionSimulationDevice che si trova nella cartella \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="668fb-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="668fb-168">L'utilizzo di questo strumento è come segue:</span><span class="sxs-lookup"><span data-stu-id="668fb-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="668fb-169">Per esempio</span><span class="sxs-lookup"><span data-stu-id="668fb-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="668fb-170">Azioni supportate sono:</span><span class="sxs-lookup"><span data-stu-id="668fb-170">Supported actions are:</span></span>
* <span data-ttu-id="668fb-171">Ho = install</span><span class="sxs-lookup"><span data-stu-id="668fb-171">i = install</span></span>
* <span data-ttu-id="668fb-172">q = query</span><span class="sxs-lookup"><span data-stu-id="668fb-172">q = query</span></span>
* <span data-ttu-id="668fb-173">r = Rimuovi</span><span class="sxs-lookup"><span data-stu-id="668fb-173">r = remove</span></span>

<span data-ttu-id="668fb-174">Istanze supportate sono:</span><span class="sxs-lookup"><span data-stu-id="668fb-174">Supported instances are:</span></span>
* <span data-ttu-id="668fb-175">1 = il controller a sinistra-i gradi di libertà 6</span><span class="sxs-lookup"><span data-stu-id="668fb-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="668fb-176">2 = il controller a destra-i gradi di libertà 6</span><span class="sxs-lookup"><span data-stu-id="668fb-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="668fb-177">Il codice di uscita del processo indica esito positivo (valore restituito pari a zero) o negativo (un valore restituito diverso da zero).</span><span class="sxs-lookup"><span data-stu-id="668fb-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="668fb-178">Quando si usa l'azione 'q' per eseguire una query o meno in cui è installato un controller, il valore restituito sarà zero (0) se il controller non è già installato o uno (1) se l'installazione del controller.</span><span class="sxs-lookup"><span data-stu-id="668fb-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="668fb-179">Quando si rimuove un controller in Windows 10 ottobre 2018 Update o versioni precedenti, impostare il relativo stato disattivato tramite l'API in primo luogo, quindi chiamare lo strumento PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="668fb-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="668fb-180">Si noti che questo strumento deve essere eseguito come amministratore.</span><span class="sxs-lookup"><span data-stu-id="668fb-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="668fb-181">Informazioni di riferimento sulle API</span><span class="sxs-lookup"><span data-stu-id="668fb-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="668fb-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="668fb-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="668fb-183">Descrive un tipo di dispositivo simulato</span><span class="sxs-lookup"><span data-stu-id="668fb-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="668fb-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="668fb-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="668fb-185">Un dispositivo di riferimento fittizio, il valore predefinito per PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="668fb-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="668fb-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="668fb-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="668fb-187">Descrive una modalità di arresto head</span><span class="sxs-lookup"><span data-stu-id="668fb-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="668fb-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="668fb-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="668fb-189">Intestazione predefinita di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="668fb-189">Default Head Tracking.</span></span> <span data-ttu-id="668fb-190">Ciò significa che il sistema può selezionare l'intestazione della migliore modalità in base alle condizioni di runtime di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="668fb-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="668fb-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="668fb-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="668fb-192">Orientamento Head solo rilevamento.</span><span class="sxs-lookup"><span data-stu-id="668fb-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="668fb-193">Ciò significa che la posizione di rilevamento potrebbe non essere affidabile e alcune funzionalità dipende dalla posizione head potrebbero non essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="668fb-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="668fb-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="668fb-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="668fb-195">Rilevamento Head posizionale.</span><span class="sxs-lookup"><span data-stu-id="668fb-195">Positional Head Tracking.</span></span> <span data-ttu-id="668fb-196">Ciò significa che la posizione head rilevati e l'orientamento sono entrambi affidabile</span><span class="sxs-lookup"><span data-stu-id="668fb-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="668fb-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="668fb-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="668fb-198">Descrive un movimento simulato</span><span class="sxs-lookup"><span data-stu-id="668fb-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="668fb-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="668fb-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="668fb-200">Un valore di sentinel usato per non indicare nessun movimenti.</span><span class="sxs-lookup"><span data-stu-id="668fb-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="668fb-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="668fb-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="668fb-202">Un dito premuto movimento.</span><span class="sxs-lookup"><span data-stu-id="668fb-202">A finger pressed gesture.</span></span>

<span data-ttu-id="668fb-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="668fb-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="668fb-204">Un movimento del dito rilasciato.</span><span class="sxs-lookup"><span data-stu-id="668fb-204">A finger released gesture.</span></span>

<span data-ttu-id="668fb-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="668fb-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="668fb-206">Il movimento di sistema/home.</span><span class="sxs-lookup"><span data-stu-id="668fb-206">The home/system gesture.</span></span>

<span data-ttu-id="668fb-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="668fb-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="668fb-208">Il movimento valido massimo.</span><span class="sxs-lookup"><span data-stu-id="668fb-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="668fb-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="668fb-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="668fb-210">Gli stati possibili di un controller simulato 6-gradi di libertà.</span><span class="sxs-lookup"><span data-stu-id="668fb-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="668fb-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="668fb-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="668fb-212">Il controller i gradi di libertà 6 è stato disattivata.</span><span class="sxs-lookup"><span data-stu-id="668fb-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="668fb-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="668fb-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="668fb-214">Il controller i gradi di libertà 6 è attivato e tiene traccia.</span><span class="sxs-lookup"><span data-stu-id="668fb-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="668fb-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="668fb-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="668fb-216">Il controller di 6-gradi di libertà è attivato ma non può essere rilevato.</span><span class="sxs-lookup"><span data-stu-id="668fb-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="668fb-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="668fb-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="668fb-218">I pulsanti supportati in un controller simulato 6-gradi di libertà.</span><span class="sxs-lookup"><span data-stu-id="668fb-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="668fb-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="668fb-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="668fb-220">Un valore di sentinel usato per non indicare nessun pulsante.</span><span class="sxs-lookup"><span data-stu-id="668fb-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="668fb-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="668fb-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="668fb-222">Viene premuto il pulsante Home.</span><span class="sxs-lookup"><span data-stu-id="668fb-222">The Home button is pressed.</span></span>

<span data-ttu-id="668fb-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="668fb-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="668fb-224">Viene premuto il pulsante di Menu.</span><span class="sxs-lookup"><span data-stu-id="668fb-224">The Menu button is pressed.</span></span>

<span data-ttu-id="668fb-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="668fb-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="668fb-226">Viene premuto il pulsante di triangolo di ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="668fb-226">The Grip button is pressed.</span></span>

<span data-ttu-id="668fb-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="668fb-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="668fb-228">Il TouchPad è premuto.</span><span class="sxs-lookup"><span data-stu-id="668fb-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="668fb-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="668fb-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="668fb-230">Viene premuto il pulsante di selezione.</span><span class="sxs-lookup"><span data-stu-id="668fb-230">The Select button is pressed.</span></span>

<span data-ttu-id="668fb-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="668fb-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="668fb-232">Il TouchPad viene manipolato.</span><span class="sxs-lookup"><span data-stu-id="668fb-232">The TouchPad is touched.</span></span>

<span data-ttu-id="668fb-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="668fb-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="668fb-234">La levetta viene premuta.</span><span class="sxs-lookup"><span data-stu-id="668fb-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="668fb-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="668fb-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="668fb-236">Il pulsante massimo valido.</span><span class="sxs-lookup"><span data-stu-id="668fb-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="668fb-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="668fb-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="668fb-238">Lo stato di calibrazione degli occhi simulati</span><span class="sxs-lookup"><span data-stu-id="668fb-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="668fb-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="668fb-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="668fb-240">Non è disponibile la calibrazione occhi.</span><span class="sxs-lookup"><span data-stu-id="668fb-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="668fb-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="668fb-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="668fb-242">Sono stati calibrati gli occhi.</span><span class="sxs-lookup"><span data-stu-id="668fb-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="668fb-243">Rappresenta il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="668fb-243">This is the default value.</span></span>

<span data-ttu-id="668fb-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="668fb-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="668fb-245">Gli occhi sono in corso calibrati.</span><span class="sxs-lookup"><span data-stu-id="668fb-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="668fb-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="668fb-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="668fb-247">È necessario essere tarato gli occhi.</span><span class="sxs-lookup"><span data-stu-id="668fb-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="668fb-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="668fb-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="668fb-249">L'accuratezza di rilevamento di un join della lancetta.</span><span class="sxs-lookup"><span data-stu-id="668fb-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="668fb-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="668fb-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="668fb-251">Join non viene rilevato.</span><span class="sxs-lookup"><span data-stu-id="668fb-251">The joint is not tracked.</span></span>

<span data-ttu-id="668fb-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="668fb-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="668fb-253">Posizione comune viene dedotto.</span><span class="sxs-lookup"><span data-stu-id="668fb-253">The joint position is inferred.</span></span>

<span data-ttu-id="668fb-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="668fb-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="668fb-255">La giunzione è registrata completamente.</span><span class="sxs-lookup"><span data-stu-id="668fb-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="668fb-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="668fb-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="668fb-257">L'accuratezza di rilevamento di un join della lancetta.</span><span class="sxs-lookup"><span data-stu-id="668fb-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="668fb-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="668fb-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="668fb-259">Giunzioni dito dell'icona della mano siano configurati per riflettere una posa chiusa.</span><span class="sxs-lookup"><span data-stu-id="668fb-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="668fb-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="668fb-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="668fb-261">Giunzioni dito dell'icona della mano sono configurati in modo da riflettere un posa open.</span><span class="sxs-lookup"><span data-stu-id="668fb-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="668fb-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="668fb-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="668fb-263">Giunzioni dito dell'icona della mano siano configurati per riflettere una posa puntamento.</span><span class="sxs-lookup"><span data-stu-id="668fb-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="668fb-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="668fb-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="668fb-265">Giunzioni dito dell'icona della mano siano configurati per riflettere una posa pinching.</span><span class="sxs-lookup"><span data-stu-id="668fb-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="668fb-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="668fb-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="668fb-267">Il valore massimo valido per SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="668fb-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="668fb-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="668fb-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="668fb-269">Descrive lo stato di una riproduzione.</span><span class="sxs-lookup"><span data-stu-id="668fb-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="668fb-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="668fb-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="668fb-271">La registrazione è attualmente arrestato e pronto per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="668fb-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="668fb-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="668fb-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="668fb-273">La registrazione è in corso di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="668fb-273">The recording is currently playing.</span></span>

<span data-ttu-id="668fb-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="668fb-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="668fb-275">La registrazione è attualmente sospeso.</span><span class="sxs-lookup"><span data-stu-id="668fb-275">The recording is currently paused.</span></span>

<span data-ttu-id="668fb-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="668fb-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="668fb-277">La registrazione ha raggiunto la fine.</span><span class="sxs-lookup"><span data-stu-id="668fb-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="668fb-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="668fb-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="668fb-279">Descrive un vettore di 3 componenti, che potrebbe descrivere un punto o un vettore nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="668fb-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="668fb-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="668fb-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="668fb-281">Componente X del vettore.</span><span class="sxs-lookup"><span data-stu-id="668fb-281">The X component of the vector.</span></span>

<span data-ttu-id="668fb-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="668fb-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="668fb-283">Componente Y del vettore.</span><span class="sxs-lookup"><span data-stu-id="668fb-283">The Y component of the vector.</span></span>

<span data-ttu-id="668fb-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="668fb-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="668fb-285">Componente Z del vettore.</span><span class="sxs-lookup"><span data-stu-id="668fb-285">The Z component of the vector.</span></span>

<span data-ttu-id="668fb-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="668fb-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="668fb-287">Creare un nuovo Vector3.</span><span class="sxs-lookup"><span data-stu-id="668fb-287">Construct a new Vector3.</span></span>

<span data-ttu-id="668fb-288">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-288">Parameters</span></span>
* <span data-ttu-id="668fb-289">x - componente x del vettore.</span><span class="sxs-lookup"><span data-stu-id="668fb-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="668fb-290">y - componente y del vettore.</span><span class="sxs-lookup"><span data-stu-id="668fb-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="668fb-291">z - componente z del vettore.</span><span class="sxs-lookup"><span data-stu-id="668fb-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="668fb-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="668fb-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="668fb-293">Descrive una rotazione di 3 componenti.</span><span class="sxs-lookup"><span data-stu-id="668fb-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="668fb-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="668fb-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="668fb-295">Il componente del passo di rotazione, in giù intorno all'asse X.</span><span class="sxs-lookup"><span data-stu-id="668fb-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="668fb-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="668fb-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="668fb-297">Il componente di rotazione di rotazione, attorno all'asse Y.</span><span class="sxs-lookup"><span data-stu-id="668fb-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="668fb-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="668fb-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="668fb-299">Il componente esegue il rollup di rotazione, attorno all'asse Z.</span><span class="sxs-lookup"><span data-stu-id="668fb-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="668fb-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="668fb-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="668fb-301">Creare un nuovo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="668fb-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="668fb-302">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-302">Parameters</span></span>
* <span data-ttu-id="668fb-303">pitch: il componente del passo della rotazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="668fb-304">rotazione - il componente di rotazione della rotazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="668fb-305">esegue il rollup - il componente esegue il rollup della rotazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="668fb-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="668fb-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="668fb-307">Descrive la configurazione di un join in una mano simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="668fb-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="668fb-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="668fb-309">La posizione del join.</span><span class="sxs-lookup"><span data-stu-id="668fb-309">The position of the joint.</span></span>

<span data-ttu-id="668fb-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="668fb-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="668fb-311">La rotazione del join.</span><span class="sxs-lookup"><span data-stu-id="668fb-311">The rotation of the joint.</span></span>

<span data-ttu-id="668fb-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="668fb-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="668fb-313">L'accuratezza di rilevamento del join.</span><span class="sxs-lookup"><span data-stu-id="668fb-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="668fb-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="668fb-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="668fb-315">Vengono descritti di cono una visualizzazione, come viene generalmente utilizzato da una fotocamera.</span><span class="sxs-lookup"><span data-stu-id="668fb-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="668fb-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="668fb-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="668fb-317">La distanza minima che è contenuta in del cono.</span><span class="sxs-lookup"><span data-stu-id="668fb-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="668fb-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="668fb-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="668fb-319">La distanza massima che è contenuta in del cono.</span><span class="sxs-lookup"><span data-stu-id="668fb-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="668fb-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="668fb-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="668fb-321">Il campo di visualizzazione orizzontale di cono, espresso in radianti (inferiori a PI).</span><span class="sxs-lookup"><span data-stu-id="668fb-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="668fb-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="668fb-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="668fb-323">Il rapporto di campo visivo orizzontale a campo di visualizzazione verticale.</span><span class="sxs-lookup"><span data-stu-id="668fb-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="668fb-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="668fb-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="668fb-325">Per la generazione di pacchetti usati per controllare un dispositivo di primo livello.</span><span class="sxs-lookup"><span data-stu-id="668fb-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="668fb-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="668fb-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="668fb-327">Recuperare l'oggetto dispositivo simulato che interpreta l'umana simulata e tutto il mondo simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="668fb-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="668fb-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="668fb-329">Recuperare l'oggetto che controlla l'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="668fb-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="668fb-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="668fb-331">Reimposta la simulazione allo stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="668fb-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="668fb-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="668fb-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="668fb-333">Interfaccia che descrive il dispositivo che interpreta tutto il mondo simulato e l'utente simulato</span><span class="sxs-lookup"><span data-stu-id="668fb-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="668fb-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="668fb-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="668fb-335">Recuperare la posizione di testa dal dispositivo simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="668fb-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="668fb-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="668fb-337">Recuperare la posizione di mano dal dispositivo simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="668fb-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="668fb-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="668fb-339">Impostare le proprietà del dispositivo simulato in modo che corrispondano il tipo di dispositivo specificato.</span><span class="sxs-lookup"><span data-stu-id="668fb-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="668fb-340">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-340">Parameters</span></span>
* <span data-ttu-id="668fb-341">Type - il nuovo tipo di dispositivo simulato</span><span class="sxs-lookup"><span data-stu-id="668fb-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="668fb-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="668fb-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="668fb-343">Interfaccia che descrive la parte del dispositivo simulato che tiene traccia di inizio della finestra di umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="668fb-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="668fb-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="668fb-345">Recupera e imposta la modalità di arresto head corrente.</span><span class="sxs-lookup"><span data-stu-id="668fb-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="668fb-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="668fb-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="668fb-347">Interfaccia che descrive la parte del dispositivo simulato che rileva il movimento delle lancette dell'umana simulata</span><span class="sxs-lookup"><span data-stu-id="668fb-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="668fb-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="668fb-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="668fb-349">Recuperare la posizione del nodo in relazione al mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="668fb-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="668fb-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="668fb-351">Recuperare e impostare la posizione dello strumento di rilevamento mano simulato, rispetto al centro della testina.</span><span class="sxs-lookup"><span data-stu-id="668fb-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="668fb-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="668fb-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="668fb-353">Recuperare e impostare il passo verso il basso dello strumento di rilevamento mano simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="668fb-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="668fb-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="668fb-355">Recuperare e impostare se cono dello strumento di rilevamento mano simulato viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="668fb-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="668fb-356">Se ignorato, entrambe le mani sono sempre visibili.</span><span class="sxs-lookup"><span data-stu-id="668fb-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="668fb-357">Quando non ignorare (impostazione predefinita) le mani sono visibili solo quando sono all'interno del cono dello strumento di rilevamento disponibili.</span><span class="sxs-lookup"><span data-stu-id="668fb-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="668fb-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="668fb-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="668fb-359">Recuperare e impostare le proprietà di cono utilizzate per determinare se sono visibili allo strumento di rilevamento mano simulato mani.</span><span class="sxs-lookup"><span data-stu-id="668fb-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="668fb-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="668fb-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="668fb-361">Interfaccia di livello superiore per controllare l'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="668fb-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="668fb-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="668fb-363">Recuperare e impostare la posizione del nodo in relazione al mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="668fb-364">La posizione corrisponde a un punto al centro di metri dell'uomo.</span><span class="sxs-lookup"><span data-stu-id="668fb-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="668fb-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="668fb-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="668fb-366">Recuperare e impostare la direzione i visi umani simulati in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="668fb-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="668fb-367">0 radianti sia rivolto verso il basso l'asse Z negativo.</span><span class="sxs-lookup"><span data-stu-id="668fb-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="668fb-368">Radianti positivi Ruota in senso orario intorno all'asse Y.</span><span class="sxs-lookup"><span data-stu-id="668fb-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="668fb-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="668fb-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="668fb-370">Recuperare e impostare l'altezza di umana simulata, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="668fb-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="668fb-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="668fb-372">Recuperare la parte sinistra dell'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="668fb-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="668fb-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="668fb-374">Recuperare il a destra dell'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="668fb-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="668fb-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="668fb-376">Recuperare l'intestazione dell'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="668fb-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="668fb-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="668fb-378">Spostare l'umana simulata rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="668fb-379">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-379">Parameters</span></span>
* <span data-ttu-id="668fb-380">Translation - la traduzione da spostare, rispetto alla posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="668fb-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="668fb-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="668fb-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="668fb-382">Ruotare l'umana simulata rispetto alla relativa direzione correnti, in senso orario intorno all'asse Y</span><span class="sxs-lookup"><span data-stu-id="668fb-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="668fb-383">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-383">Parameters</span></span>
* <span data-ttu-id="668fb-384">RADIANS - la quantità di rotazione intorno all'asse Y.</span><span class="sxs-lookup"><span data-stu-id="668fb-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="668fb-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="668fb-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="668fb-386">Proprietà aggiuntive sono disponibili eseguendo il cast di ISimulatedHuman a ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="668fb-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="668fb-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="668fb-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="668fb-388">Recuperare il controller a sinistra 6-gradi di libertà.</span><span class="sxs-lookup"><span data-stu-id="668fb-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="668fb-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="668fb-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="668fb-390">Recuperare il controller a destra i 6-gradi di libertà.</span><span class="sxs-lookup"><span data-stu-id="668fb-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="668fb-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="668fb-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="668fb-392">Interfaccia che descrive una mano dell'umana simulata</span><span class="sxs-lookup"><span data-stu-id="668fb-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="668fb-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="668fb-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="668fb-394">Recuperare la posizione del nodo in relazione al mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="668fb-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="668fb-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="668fb-396">Recuperare e impostare la posizione della mano simulata relativo umane, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="668fb-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="668fb-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="668fb-398">Recuperare e impostare se l'icona della mano è attualmente attivato.</span><span class="sxs-lookup"><span data-stu-id="668fb-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="668fb-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="668fb-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="668fb-400">Sapere se l'icona della mano è attualmente visibile per il SimulatedDevice (ad esempio, se è in grado di rilevare il HandTracker).</span><span class="sxs-lookup"><span data-stu-id="668fb-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="668fb-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="668fb-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="668fb-402">Spostare l'icona della mano, che risulta visibile per il SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="668fb-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="668fb-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="668fb-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="668fb-404">Spostare la posizione della mano simulata rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="668fb-405">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-405">Parameters</span></span>
* <span data-ttu-id="668fb-406">Translation - quantità per convertire l'icona della mano simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="668fb-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="668fb-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="668fb-408">Eseguire un gesto usando l'icona della mano simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="668fb-409">Verrà solo rilevata dal sistema se è abilitata l'icona della mano.</span><span class="sxs-lookup"><span data-stu-id="668fb-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="668fb-410">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-410">Parameters</span></span>
* <span data-ttu-id="668fb-411">movimento - il movimento da eseguire.</span><span class="sxs-lookup"><span data-stu-id="668fb-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="668fb-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="668fb-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="668fb-413">Proprietà aggiuntive sono disponibili eseguendo il cast di un ISimulatedHand a ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="668fb-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="668fb-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="668fb-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="668fb-415">Recuperare o impostare la rotazione della mano simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="668fb-416">Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="668fb-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="668fb-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="668fb-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="668fb-418">Proprietà aggiuntive sono disponibili eseguendo il cast di un ISimulatedHand a ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="668fb-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="668fb-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="668fb-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="668fb-420">Ottenere la configurazione comune per la giunzione specificata.</span><span class="sxs-lookup"><span data-stu-id="668fb-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="668fb-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="668fb-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="668fb-422">Impostare la configurazione comune per la giunzione specificata.</span><span class="sxs-lookup"><span data-stu-id="668fb-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="668fb-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="668fb-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="668fb-424">Impostare l'icona della mano una posa nota con flag facoltativo per aggiungere un'animazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="668fb-425">Nota: l'animazione non comportare giunzioni immediatamente che riflette le relative configurazioni joint finale.</span><span class="sxs-lookup"><span data-stu-id="668fb-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="668fb-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="668fb-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="668fb-427">Interfaccia che descrive l'inizio dell'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="668fb-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="668fb-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="668fb-429">Recuperare la posizione del nodo in relazione al mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="668fb-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="668fb-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="668fb-431">Recuperare la rotazione di testa simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="668fb-432">Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="668fb-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="668fb-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="668fb-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="668fb-434">Recuperare il diametro del head simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="668fb-435">Questo valore viene utilizzato per determinare l'area dell'intestazione (punto di rotazione).</span><span class="sxs-lookup"><span data-stu-id="668fb-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="668fb-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="668fb-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="668fb-437">Ruotare la testa simulata rispetto alla rotazione corrente.</span><span class="sxs-lookup"><span data-stu-id="668fb-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="668fb-438">Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="668fb-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="668fb-439">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-439">Parameters</span></span>
* <span data-ttu-id="668fb-440">rotazione - la quantità per ruotare.</span><span class="sxs-lookup"><span data-stu-id="668fb-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="668fb-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="668fb-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="668fb-442">Proprietà aggiuntive sono disponibili eseguendo il cast di un ISimulatedHead a ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="668fb-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="668fb-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="668fb-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="668fb-444">Recuperare gli occhi dell'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="668fb-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="668fb-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="668fb-446">Interfaccia che descrivono un controller di 6-gradi di libertà associato l'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="668fb-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="668fb-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="668fb-448">Recuperare la posizione del nodo in relazione al mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="668fb-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="668fb-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="668fb-450">Recuperare o impostare lo stato corrente del controller.</span><span class="sxs-lookup"><span data-stu-id="668fb-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="668fb-451">Lo stato del controller deve essere impostato su un valore diverso da Off prima delle chiamate a spostare, ruotare e premere i pulsanti avranno esito positivo.</span><span class="sxs-lookup"><span data-stu-id="668fb-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="668fb-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="668fb-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="668fb-453">Recuperare o impostare la posizione del controller simulato relativo umane, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="668fb-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="668fb-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="668fb-455">Recuperare o impostare l'orientamento del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="668fb-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="668fb-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="668fb-457">Spostare la posizione del controller simulato rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="668fb-458">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-458">Parameters</span></span>
* <span data-ttu-id="668fb-459">Translation - quantità per convertire il controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="668fb-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="668fb-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="668fb-461">Premere un pulsante sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="668fb-462">Verrà solo rilevata dal sistema se il controller è abilitato.</span><span class="sxs-lookup"><span data-stu-id="668fb-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="668fb-463">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-463">Parameters</span></span>
* <span data-ttu-id="668fb-464">pulsante - premere il pulsante.</span><span class="sxs-lookup"><span data-stu-id="668fb-464">button - The button to press.</span></span>

<span data-ttu-id="668fb-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="668fb-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="668fb-466">Rilascia un pulsante sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="668fb-467">Verrà solo rilevata dal sistema se il controller è abilitato.</span><span class="sxs-lookup"><span data-stu-id="668fb-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="668fb-468">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-468">Parameters</span></span>
* <span data-ttu-id="668fb-469">pulsante - il rilascio.</span><span class="sxs-lookup"><span data-stu-id="668fb-469">button - The button to release.</span></span>

<span data-ttu-id="668fb-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition (out out float, float)**</span><span class="sxs-lookup"><span data-stu-id="668fb-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="668fb-471">Ottenere la posizione di un dito simulato su touchpad del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="668fb-472">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-472">Parameters</span></span>
* <span data-ttu-id="668fb-473">x - la posizione orizzontale del dito.</span><span class="sxs-lookup"><span data-stu-id="668fb-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="668fb-474">y - la posizione verticale del dito.</span><span class="sxs-lookup"><span data-stu-id="668fb-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="668fb-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="668fb-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="668fb-476">Impostare la posizione di un dito simulato su touchpad del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="668fb-477">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-477">Parameters</span></span>
* <span data-ttu-id="668fb-478">x - la posizione orizzontale del dito.</span><span class="sxs-lookup"><span data-stu-id="668fb-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="668fb-479">y - la posizione verticale del dito.</span><span class="sxs-lookup"><span data-stu-id="668fb-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="668fb-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="668fb-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="668fb-481">I metodi e proprietà aggiuntive sono disponibili eseguendo il cast di un ISimulatedSixDofController a ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="668fb-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="668fb-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition (out out float, float)**</span><span class="sxs-lookup"><span data-stu-id="668fb-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="668fb-483">Ottenere la posizione del thumbstick simulato sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="668fb-484">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-484">Parameters</span></span>
* <span data-ttu-id="668fb-485">x - la posizione orizzontale del thumbstick.</span><span class="sxs-lookup"><span data-stu-id="668fb-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="668fb-486">y - la posizione verticale del thumbstick.</span><span class="sxs-lookup"><span data-stu-id="668fb-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="668fb-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="668fb-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="668fb-488">Impostare la posizione del thumbstick simulato sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="668fb-489">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-489">Parameters</span></span>
* <span data-ttu-id="668fb-490">x - la posizione orizzontale del thumbstick.</span><span class="sxs-lookup"><span data-stu-id="668fb-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="668fb-491">y - la posizione verticale del thumbstick.</span><span class="sxs-lookup"><span data-stu-id="668fb-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="668fb-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="668fb-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="668fb-493">Recuperare o impostare il livello della batteria del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="668fb-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="668fb-494">Il valore deve essere maggiore di 0,0 e minore o uguale a 100,0.</span><span class="sxs-lookup"><span data-stu-id="668fb-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="668fb-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="668fb-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="668fb-496">Interfaccia che descrive gli occhi dell'umana simulata.</span><span class="sxs-lookup"><span data-stu-id="668fb-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="668fb-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="668fb-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="668fb-498">Recuperare la rotazione degli occhi simulati.</span><span class="sxs-lookup"><span data-stu-id="668fb-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="668fb-499">Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="668fb-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="668fb-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="668fb-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="668fb-501">Ruota gli occhi simulati rispetto alla rotazione corrente.</span><span class="sxs-lookup"><span data-stu-id="668fb-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="668fb-502">Radianti positivi Ruota in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="668fb-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="668fb-503">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-503">Parameters</span></span>
* <span data-ttu-id="668fb-504">rotazione - la quantità per ruotare.</span><span class="sxs-lookup"><span data-stu-id="668fb-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="668fb-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="668fb-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="668fb-506">Recupera o imposta lo stato di calibrazione degli occhi simulati.</span><span class="sxs-lookup"><span data-stu-id="668fb-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="668fb-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="668fb-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="668fb-508">Recuperare la posizione del nodo in relazione al mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="668fb-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="668fb-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="668fb-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="668fb-510">Caricare l'interfaccia per l'interazione con una registrazione singola per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="668fb-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="668fb-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="668fb-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="668fb-512">Recupera l'elenco dei tipi di dati della registrazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="668fb-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="668fb-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="668fb-514">Recupera lo stato corrente della registrazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="668fb-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="668fb-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="668fb-516">Avviare la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="668fb-516">Start the playback.</span></span> <span data-ttu-id="668fb-517">Se è in pausa la registrazione, riproduzione verrà ripresa dal percorso in pausa; Se arrestato, la riproduzione inizierà all'inizio.</span><span class="sxs-lookup"><span data-stu-id="668fb-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="668fb-518">Se già riproducendo, questa chiamata viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="668fb-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="668fb-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="668fb-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="668fb-520">Sospende la riproduzione nel percorso corrente.</span><span class="sxs-lookup"><span data-stu-id="668fb-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="668fb-521">Se la registrazione viene arrestata, la chiamata viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="668fb-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="668fb-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="668fb-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="668fb-523">Cerca la registrazione per il tempo specificato (in 100 intervalli di nanosecondi dall'inizio) e del mouse viene posizionato nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="668fb-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="668fb-524">Se il tempo è oltre la fine della registrazione, è in pausa nell'ultimo fotogramma.</span><span class="sxs-lookup"><span data-stu-id="668fb-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="668fb-525">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-525">Parameters</span></span>
* <span data-ttu-id="668fb-526">segni di graduazione - il tempo per cui eseguire la ricerca.</span><span class="sxs-lookup"><span data-stu-id="668fb-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="668fb-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="668fb-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="668fb-528">Arresta la riproduzione e reimposta la posizione di inizio.</span><span class="sxs-lookup"><span data-stu-id="668fb-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="668fb-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="668fb-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="668fb-530">Interfaccia per la ricezione di modifiche di stato durante la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="668fb-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="668fb-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="668fb-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="668fb-532">Chiamato quando di un ISimulationRecording riproduzione è stato.</span><span class="sxs-lookup"><span data-stu-id="668fb-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="668fb-533">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-533">Parameters</span></span>
* <span data-ttu-id="668fb-534">newState - il nuovo stato della registrazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="668fb-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="668fb-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="668fb-536">Oggetto radice per la creazione di oggetti di simulazione di percezione.</span><span class="sxs-lookup"><span data-stu-id="668fb-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="668fb-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="668fb-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="668fb-538">Creare sull'oggetto per la generazione di pacchetti simulati e il recapito per il sink specificato.</span><span class="sxs-lookup"><span data-stu-id="668fb-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="668fb-539">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-539">Parameters</span></span>
* <span data-ttu-id="668fb-540">sink - sink che riceverà generati tutti i pacchetti.</span><span class="sxs-lookup"><span data-stu-id="668fb-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="668fb-541">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="668fb-541">Return value</span></span>

<span data-ttu-id="668fb-542">Il gestore creato.</span><span class="sxs-lookup"><span data-stu-id="668fb-542">The created Manager.</span></span>

<span data-ttu-id="668fb-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="668fb-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="668fb-544">Creare un sink di cui sono archiviati i pacchetti ricevuti tutti in un file nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="668fb-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="668fb-545">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-545">Parameters</span></span>
* <span data-ttu-id="668fb-546">percorso: il percorso del file da creare.</span><span class="sxs-lookup"><span data-stu-id="668fb-546">path - The path of the file to create.</span></span>

<span data-ttu-id="668fb-547">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="668fb-547">Return value</span></span>

<span data-ttu-id="668fb-548">Il sink creato.</span><span class="sxs-lookup"><span data-stu-id="668fb-548">The created sink.</span></span>

<span data-ttu-id="668fb-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="668fb-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="668fb-550">Caricare una registrazione dal file specificato.</span><span class="sxs-lookup"><span data-stu-id="668fb-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="668fb-551">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-551">Parameters</span></span>
* <span data-ttu-id="668fb-552">percorso: il percorso del file da caricare.</span><span class="sxs-lookup"><span data-stu-id="668fb-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="668fb-553">factory - una factory utilizzata per la registrazione per la creazione di un ISimulationStreamSink quando necessario.</span><span class="sxs-lookup"><span data-stu-id="668fb-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="668fb-554">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="668fb-554">Return value</span></span>

<span data-ttu-id="668fb-555">La registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="668fb-555">The loaded recording.</span></span>

<span data-ttu-id="668fb-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="668fb-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="668fb-557">Caricare una registrazione dal file specificato.</span><span class="sxs-lookup"><span data-stu-id="668fb-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="668fb-558">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-558">Parameters</span></span>
* <span data-ttu-id="668fb-559">percorso: il percorso del file da caricare.</span><span class="sxs-lookup"><span data-stu-id="668fb-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="668fb-560">factory - una factory utilizzata per la registrazione per la creazione di un ISimulationStreamSink quando necessario.</span><span class="sxs-lookup"><span data-stu-id="668fb-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="668fb-561">callback - aggiorna un callback che riceve il declassamento lo stato della registrazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="668fb-562">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="668fb-562">Return value</span></span>

<span data-ttu-id="668fb-563">La registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="668fb-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="668fb-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="668fb-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="668fb-565">Descrive i diversi tipi di dati di flusso.</span><span class="sxs-lookup"><span data-stu-id="668fb-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="668fb-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="668fb-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="668fb-567">Un valore di sentinel usato per non indicare nessun tipo di dati di flusso.</span><span class="sxs-lookup"><span data-stu-id="668fb-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="668fb-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="668fb-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="668fb-569">Stream dei dati riguardanti la posizione e l'orientamento della testina.</span><span class="sxs-lookup"><span data-stu-id="668fb-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="668fb-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="668fb-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="668fb-571">Stream dei dati riguardanti la posizione e i movimenti di mani.</span><span class="sxs-lookup"><span data-stu-id="668fb-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="668fb-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="668fb-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="668fb-573">Stream dei dati relativi mapping spaziale dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="668fb-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="668fb-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="668fb-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="668fb-575">Stream dei dati relativi al calibrazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="668fb-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="668fb-576">I pacchetti di calibrazione vengono accettati solo da un sistema in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="668fb-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="668fb-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="668fb-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="668fb-578">Stream dei dati relativi all'ambiente del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="668fb-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="668fb-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="668fb-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="668fb-580">Un valore di sentinel usato per indicare tutti i tipi di dati registrati.</span><span class="sxs-lookup"><span data-stu-id="668fb-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="668fb-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="668fb-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="668fb-582">Oggetto che riceve i pacchetti di dati da un flusso di simulazione.</span><span class="sxs-lookup"><span data-stu-id="668fb-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="668fb-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="668fb-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="668fb-584">Riceve un singolo pacchetto, ovvero internamente tipizzata e con controllo delle versioni.</span><span class="sxs-lookup"><span data-stu-id="668fb-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="668fb-585">Parametri</span><span class="sxs-lookup"><span data-stu-id="668fb-585">Parameters</span></span>
* <span data-ttu-id="668fb-586">Length - la lunghezza del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="668fb-586">length - The length of the packet.</span></span>
* <span data-ttu-id="668fb-587">pacchetto - i dati del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="668fb-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="668fb-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="668fb-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="668fb-589">Oggetto che crea ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="668fb-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="668fb-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="668fb-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="668fb-591">Crea una singola istanza di ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="668fb-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="668fb-592">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="668fb-592">Return value</span></span>

<span data-ttu-id="668fb-593">Il sink creato.</span><span class="sxs-lookup"><span data-stu-id="668fb-593">The created sink.</span></span>
