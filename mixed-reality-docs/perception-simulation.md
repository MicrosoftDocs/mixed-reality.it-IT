---
title: Simulazione della percezione
description: Guida all'uso della libreria di simulazione della percezione per automatizzare l'input simulato per le applicazioni immersive
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulazione, test
ms.openlocfilehash: 701fd39490d87b70df9bd68cc99da6482d41b676
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228026"
---
# <a name="perception-simulation"></a><span data-ttu-id="f7812-104">Simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="f7812-104">Perception simulation</span></span>

<span data-ttu-id="f7812-105">Si vuole compilare un test automatizzato per l'app?</span><span class="sxs-lookup"><span data-stu-id="f7812-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="f7812-106">Si desidera che i test vadano oltre il testing unità a livello di componente e che l'app venga effettivamente eseguita end-to-end?</span><span class="sxs-lookup"><span data-stu-id="f7812-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="f7812-107">La simulazione della percezione è ciò che si sta cercando.</span><span class="sxs-lookup"><span data-stu-id="f7812-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="f7812-108">La libreria di simulazione della percezione invia dati di input umani e internazionali all'app in modo che sia possibile automatizzare i test.</span><span class="sxs-lookup"><span data-stu-id="f7812-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="f7812-109">Ad esempio, è possibile simulare l'input di un utente cercando una posizione specifica e ripetibile, quindi eseguendo un movimento o utilizzando un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="f7812-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="f7812-110">La simulazione della percezione può inviare input simulati come questo a un HoloLens fisico, l'emulatore di HoloLens (1a generazione), l'emulatore HoloLens 2 o un PC con il portale di realtà mista installato.</span><span class="sxs-lookup"><span data-stu-id="f7812-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="f7812-111">La simulazione della percezione ignora i sensori dinamici in un dispositivo di realtà mista e invia un input simulato alle applicazioni in esecuzione sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f7812-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="f7812-112">Le applicazioni ricevono questi eventi di input tramite le stesse API che usano sempre e non possono indicare la differenza tra l'esecuzione con sensori reali e l'esecuzione con la simulazione della percezione.</span><span class="sxs-lookup"><span data-stu-id="f7812-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="f7812-113">La simulazione della percezione è la stessa tecnologia usata dagli emulatori di HoloLens per inviare input simulato alla macchina virtuale HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f7812-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="f7812-114">Per iniziare a usare la simulazione nel codice, iniziare creando un oggetto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="f7812-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="f7812-115">Da tale oggetto, è possibile eseguire comandi per controllare le proprietà di un elemento "Human" simulato, inclusi posizione della testa, posizione della mano e movimenti, ed è possibile abilitare e modificare i controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="f7812-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="f7812-116">Configurazione di un progetto di Visual Studio per la simulazione della percezione</span><span class="sxs-lookup"><span data-stu-id="f7812-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="f7812-117">[Installare l'emulatore di HoloLens](install-the-tools.md) nel PC di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="f7812-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="f7812-118">L'emulatore include le librerie che si utilizzeranno per la simulazione della percezione.</span><span class="sxs-lookup"><span data-stu-id="f7812-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="f7812-119">Creare un nuovo progetto desktop di Visual Studio C# (un progetto console è molto interessante per iniziare).</span><span class="sxs-lookup"><span data-stu-id="f7812-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="f7812-120">Aggiungere i file binari seguenti al progetto come riferimenti (informazioni di riferimento sul >di aggiunta di Project->...). È possibile trovarli in% ProgramFiles (x86)% \ Microsoft XDE \\ (Version), ad esempio **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** per l'emulatore HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f7812-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="f7812-121">Nota: anche se i file binari fanno parte dell'emulatore HoloLens 2, funzionano anche per la realtà mista di Windows sul desktop. un.</span><span class="sxs-lookup"><span data-stu-id="f7812-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="f7812-122">PerceptionSimulationManager. Interop. dll: wrapper C# gestito per la simulazione della percezione.</span><span class="sxs-lookup"><span data-stu-id="f7812-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="f7812-123">b.</span><span class="sxs-lookup"><span data-stu-id="f7812-123">b.</span></span> <span data-ttu-id="f7812-124">PerceptionSimulationRest. dll-libreria per la configurazione di un canale di comunicazione del socket Web per HoloLens o emulatore.</span><span class="sxs-lookup"><span data-stu-id="f7812-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="f7812-125">c.</span><span class="sxs-lookup"><span data-stu-id="f7812-125">c.</span></span> <span data-ttu-id="f7812-126">SimulationStream. Interop. dll: tipi condivisi per la simulazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="f7812-127">Aggiungere il file binario di implementazione PerceptionSimulationManager. dll al progetto a.</span><span class="sxs-lookup"><span data-stu-id="f7812-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="f7812-128">Per prima cosa, aggiungere il file come binario al progetto (>elemento esistente del >di progetto...). Salvarlo come collegamento in modo che non venga copiato nella cartella di origine del progetto.</span><span class="sxs-lookup"><span data-stu-id="f7812-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="f7812-129">![Aggiungere PerceptionSimulationManager. dll al progetto come collegamento ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="f7812-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="f7812-130">Assicurarsi quindi che venga copiato nella cartella di output durante la compilazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="f7812-131">Si trova nella finestra delle proprietà per il file binario.</span><span class="sxs-lookup"><span data-stu-id="f7812-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="f7812-132">![Contrassegnare PerceptionSimulationManager. dll per la copia nella directory di output](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="f7812-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="f7812-133">Impostare la piattaforma della soluzione attiva su x64.</span><span class="sxs-lookup"><span data-stu-id="f7812-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="f7812-134">Usare il Configuration Manager per creare una voce della piattaforma per x64, se non ne esiste già una.</span><span class="sxs-lookup"><span data-stu-id="f7812-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="f7812-135">Creazione di un oggetto IPerceptionSimulation Manager</span><span class="sxs-lookup"><span data-stu-id="f7812-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="f7812-136">Per controllare la simulazione, è possibile eseguire aggiornamenti agli oggetti recuperati da un oggetto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="f7812-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="f7812-137">Il primo passaggio consiste nell'ottenere l'oggetto e connetterlo al dispositivo o all'emulatore di destinazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="f7812-138">È possibile ottenere l'indirizzo IP dell'emulatore facendo clic sul pulsante portale del dispositivo sulla [barra degli strumenti](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="f7812-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="f7812-139">![Aprire l'icona del portale del dispositivo ](images/emulator-deviceportal.png) **aprire il portale**del dispositivo: aprire il portale del dispositivo Windows per il sistema operativo HoloLens nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="f7812-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="f7812-140">Per la realtà mista di Windows, questo può essere recuperato nell'app impostazioni in "Aggiorna & sicurezza", quindi "per sviluppatori" nella sezione "Connetti tramite:" in "abilitare il portale del dispositivo".</span><span class="sxs-lookup"><span data-stu-id="f7812-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="f7812-141">Assicurarsi di annotare l'indirizzo IP e la porta.</span><span class="sxs-lookup"><span data-stu-id="f7812-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="f7812-142">In primo luogo, si chiamerà RestSimulationStreamSink. create per ottenere un oggetto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="f7812-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="f7812-143">Si tratta del dispositivo o dell'emulatore di destinazione che si controllerà su una connessione HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7812-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="f7812-144">I comandi verranno passati e gestiti dal [portale del dispositivo Windows](using-the-windows-device-portal.md) in esecuzione nel dispositivo o nell'emulatore.</span><span class="sxs-lookup"><span data-stu-id="f7812-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="f7812-145">I quattro parametri necessari per creare un oggetto sono:</span><span class="sxs-lookup"><span data-stu-id="f7812-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="f7812-146">Uri URI-indirizzo IP del dispositivo di destinazione (ad esempio, " https://123.123.123.123 " o " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="f7812-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="f7812-147">System .NET. NetworkCredential credentials: nome utente/password per la connessione al [portale per dispositivi Windows](using-the-windows-device-portal.md) sul dispositivo o sull'emulatore di destinazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="f7812-148">Se ci si connette all'emulatore tramite l'indirizzo locale (ad esempio,*168...* \*) nello stesso computer verranno accettate le credenziali.</span><span class="sxs-lookup"><span data-stu-id="f7812-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="f7812-149">bool Normal-true per la priorità normale, false per priorità bassa.</span><span class="sxs-lookup"><span data-stu-id="f7812-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="f7812-150">In genere è consigliabile impostare questo valore su *true* per gli scenari di test, che consente al test di assumere il controllo.</span><span class="sxs-lookup"><span data-stu-id="f7812-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="f7812-151">L'emulatore e la simulazione di realtà mista di Windows usano connessioni con priorità bassa.</span><span class="sxs-lookup"><span data-stu-id="f7812-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="f7812-152">Se il test USA anche una connessione con priorità bassa, la connessione stabilita più di recente sarà controllata.</span><span class="sxs-lookup"><span data-stu-id="f7812-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="f7812-153">System. Threading. CancellationToken token-token per annullare l'operazione asincrona.</span><span class="sxs-lookup"><span data-stu-id="f7812-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="f7812-154">In secondo luogo viene creato il IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="f7812-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="f7812-155">Si tratta dell'oggetto usato per controllare la simulazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="f7812-156">Si noti che questa operazione deve essere eseguita anche in un metodo asincrono.</span><span class="sxs-lookup"><span data-stu-id="f7812-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="f7812-157">Controllare la persona simulata</span><span class="sxs-lookup"><span data-stu-id="f7812-157">Control the simulated Human</span></span>

<span data-ttu-id="f7812-158">Un IPerceptionSimulationManager ha una proprietà umana che restituisce un oggetto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="f7812-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="f7812-159">Per controllare l'uomo simulato, eseguire operazioni su questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="f7812-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="f7812-160">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f7812-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="f7812-161">Applicazione console C# di esempio di base</span><span class="sxs-lookup"><span data-stu-id="f7812-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="f7812-162">Applicazione console C# di esempio estesa</span><span class="sxs-lookup"><span data-stu-id="f7812-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="f7812-163">Nota sui controller da 6 a DOF</span><span class="sxs-lookup"><span data-stu-id="f7812-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="f7812-164">Prima di chiamare qualsiasi proprietà nei metodi in un controller 6-DOF simulato, è necessario attivare il controller.</span><span class="sxs-lookup"><span data-stu-id="f7812-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="f7812-165">In caso contrario, viene generata un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="f7812-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="f7812-166">A partire dall'aggiornamento 2019 di Windows 10, è possibile installare e attivare i controller 6-DOF simulati impostando la proprietà Status dell'oggetto ISimulatedSixDofController su SimulatedSixDofControllerStatus. Active.</span><span class="sxs-lookup"><span data-stu-id="f7812-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="f7812-167">Nell'aggiornamento di Windows 10 ottobre 2018 e versioni precedenti, è necessario installare prima di tutto un controller 6-DOF simulato chiamando lo strumento PerceptionSimulationDevice disponibile nella cartella \Windows\System32..</span><span class="sxs-lookup"><span data-stu-id="f7812-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="f7812-168">L'utilizzo di questo strumento è il seguente:</span><span class="sxs-lookup"><span data-stu-id="f7812-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="f7812-169">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f7812-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="f7812-170">Le azioni supportate sono:</span><span class="sxs-lookup"><span data-stu-id="f7812-170">Supported actions are:</span></span>
* <span data-ttu-id="f7812-171">i = install</span><span class="sxs-lookup"><span data-stu-id="f7812-171">i = install</span></span>
* <span data-ttu-id="f7812-172">q = query</span><span class="sxs-lookup"><span data-stu-id="f7812-172">q = query</span></span>
* <span data-ttu-id="f7812-173">r = Rimuovi</span><span class="sxs-lookup"><span data-stu-id="f7812-173">r = remove</span></span>

<span data-ttu-id="f7812-174">Le istanze supportate sono:</span><span class="sxs-lookup"><span data-stu-id="f7812-174">Supported instances are:</span></span>
* <span data-ttu-id="f7812-175">1 = il controller 6-DOF a sinistra</span><span class="sxs-lookup"><span data-stu-id="f7812-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="f7812-176">2 = il controller 6-DOF a destra</span><span class="sxs-lookup"><span data-stu-id="f7812-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="f7812-177">Il codice di uscita del processo indicherà l'esito positivo (un valore restituito pari a zero) o un errore (un valore restituito diverso da zero).</span><span class="sxs-lookup"><span data-stu-id="f7812-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="f7812-178">Quando si usa l'azione "q" per eseguire una query indipendentemente dal fatto che sia installato un controller, il valore restituito sarà zero (0) se il controller non è già installato o uno (1) se il controller è installato.</span><span class="sxs-lookup"><span data-stu-id="f7812-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="f7812-179">Quando si rimuove un controller nell'aggiornamento di Windows 10 ottobre 2018 o versioni precedenti, impostare lo stato su disattivato tramite l'API, quindi chiamare lo strumento PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="f7812-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="f7812-180">Si noti che questo strumento deve essere eseguito come amministratore.</span><span class="sxs-lookup"><span data-stu-id="f7812-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="f7812-181">Informazioni di riferimento sulle API</span><span class="sxs-lookup"><span data-stu-id="f7812-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="f7812-182">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="f7812-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="f7812-183">Descrive un tipo di dispositivo simulato</span><span class="sxs-lookup"><span data-stu-id="f7812-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="f7812-184">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="f7812-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="f7812-185">Un dispositivo di riferimento fittizio, il valore predefinito per PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f7812-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="f7812-186">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="f7812-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="f7812-187">Descrive la modalità Head Tracker</span><span class="sxs-lookup"><span data-stu-id="f7812-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="f7812-188">**Microsoft. PerceptionSimulation. HeadTrackerMode. default**</span><span class="sxs-lookup"><span data-stu-id="f7812-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="f7812-189">Rilevamento Head predefinito.</span><span class="sxs-lookup"><span data-stu-id="f7812-189">Default Head Tracking.</span></span> <span data-ttu-id="f7812-190">Ciò significa che il sistema può selezionare la modalità di rilevamento Head migliore in base alle condizioni di Runtime.</span><span class="sxs-lookup"><span data-stu-id="f7812-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="f7812-191">**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="f7812-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="f7812-192">Solo orientamento Head Tracking.</span><span class="sxs-lookup"><span data-stu-id="f7812-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="f7812-193">Ciò significa che la posizione rilevata potrebbe non essere affidabile e che alcune funzionalità che dipendono dalla posizione Head potrebbero non essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="f7812-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="f7812-194">**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="f7812-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="f7812-195">Rilevamento Head posizionale.</span><span class="sxs-lookup"><span data-stu-id="f7812-195">Positional Head Tracking.</span></span> <span data-ttu-id="f7812-196">Ciò significa che la posizione e l'orientamento della testa rilevati sono entrambi affidabili</span><span class="sxs-lookup"><span data-stu-id="f7812-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="f7812-197">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="f7812-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="f7812-198">Descrive un movimento simulato</span><span class="sxs-lookup"><span data-stu-id="f7812-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="f7812-199">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="f7812-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="f7812-200">Valore sentinella utilizzato per indicare nessun movimento.</span><span class="sxs-lookup"><span data-stu-id="f7812-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="f7812-201">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="f7812-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="f7812-202">Gesto premuto con un dito.</span><span class="sxs-lookup"><span data-stu-id="f7812-202">A finger pressed gesture.</span></span>

<span data-ttu-id="f7812-203">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="f7812-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="f7812-204">Gesto rilasciato da un dito.</span><span class="sxs-lookup"><span data-stu-id="f7812-204">A finger released gesture.</span></span>

<span data-ttu-id="f7812-205">**Microsoft. PerceptionSimulation. SimulatedGesture. Home**</span><span class="sxs-lookup"><span data-stu-id="f7812-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="f7812-206">Movimento Home/sistema.</span><span class="sxs-lookup"><span data-stu-id="f7812-206">The home/system gesture.</span></span>

<span data-ttu-id="f7812-207">**Microsoft. PerceptionSimulation. SimulatedGesture. max**</span><span class="sxs-lookup"><span data-stu-id="f7812-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="f7812-208">Il gesto massimo valido.</span><span class="sxs-lookup"><span data-stu-id="f7812-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="f7812-209">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="f7812-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="f7812-210">Gli stati possibili di un controller 6-DOF simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="f7812-211">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. off**</span><span class="sxs-lookup"><span data-stu-id="f7812-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="f7812-212">Il controller 6-DOF è disattivato.</span><span class="sxs-lookup"><span data-stu-id="f7812-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="f7812-213">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. Active**</span><span class="sxs-lookup"><span data-stu-id="f7812-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="f7812-214">Il controller 6-DOF è acceso e rilevato.</span><span class="sxs-lookup"><span data-stu-id="f7812-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="f7812-215">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="f7812-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="f7812-216">Il controller 6-DOF è acceso, ma non è possibile monitorarlo.</span><span class="sxs-lookup"><span data-stu-id="f7812-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="f7812-217">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="f7812-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="f7812-218">Pulsanti supportati in un controller 6-DOF simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="f7812-219">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="f7812-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="f7812-220">Valore sentinella utilizzato per indicare l'assenza di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="f7812-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="f7812-221">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**</span><span class="sxs-lookup"><span data-stu-id="f7812-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="f7812-222">Viene premuto il pulsante Home.</span><span class="sxs-lookup"><span data-stu-id="f7812-222">The Home button is pressed.</span></span>

<span data-ttu-id="f7812-223">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. menu**</span><span class="sxs-lookup"><span data-stu-id="f7812-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="f7812-224">Viene premuto il pulsante di menu.</span><span class="sxs-lookup"><span data-stu-id="f7812-224">The Menu button is pressed.</span></span>

<span data-ttu-id="f7812-225">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Grip**</span><span class="sxs-lookup"><span data-stu-id="f7812-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="f7812-226">Viene premuto il pulsante del grip.</span><span class="sxs-lookup"><span data-stu-id="f7812-226">The Grip button is pressed.</span></span>

<span data-ttu-id="f7812-227">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="f7812-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="f7812-228">Il TouchPad è premuto.</span><span class="sxs-lookup"><span data-stu-id="f7812-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="f7812-229">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="f7812-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="f7812-230">Viene premuto il pulsante Seleziona.</span><span class="sxs-lookup"><span data-stu-id="f7812-230">The Select button is pressed.</span></span>

<span data-ttu-id="f7812-231">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="f7812-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="f7812-232">Il TouchPad viene toccato.</span><span class="sxs-lookup"><span data-stu-id="f7812-232">The TouchPad is touched.</span></span>

<span data-ttu-id="f7812-233">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. levetta**</span><span class="sxs-lookup"><span data-stu-id="f7812-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="f7812-234">Viene premuto levetta.</span><span class="sxs-lookup"><span data-stu-id="f7812-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="f7812-235">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. max**</span><span class="sxs-lookup"><span data-stu-id="f7812-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="f7812-236">Pulsante massimo valido.</span><span class="sxs-lookup"><span data-stu-id="f7812-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="f7812-237">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="f7812-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="f7812-238">Stato di calibrazione degli occhi simulati</span><span class="sxs-lookup"><span data-stu-id="f7812-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="f7812-239">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. non disponibile**</span><span class="sxs-lookup"><span data-stu-id="f7812-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="f7812-240">La calibrazione degli occhi non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="f7812-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="f7812-241">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="f7812-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="f7812-242">Gli occhi sono stati calibrati.</span><span class="sxs-lookup"><span data-stu-id="f7812-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="f7812-243">Si tratta del valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="f7812-243">This is the default value.</span></span>

<span data-ttu-id="f7812-244">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Configuring**</span><span class="sxs-lookup"><span data-stu-id="f7812-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="f7812-245">Gli occhi vengono calibrati.</span><span class="sxs-lookup"><span data-stu-id="f7812-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="f7812-246">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="f7812-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="f7812-247">È necessario calibrare gli occhi.</span><span class="sxs-lookup"><span data-stu-id="f7812-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="f7812-248">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="f7812-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="f7812-249">Accuratezza del rilevamento di una giunzione della mano.</span><span class="sxs-lookup"><span data-stu-id="f7812-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="f7812-250">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. non disponibile**</span><span class="sxs-lookup"><span data-stu-id="f7812-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="f7812-251">Il giunto non viene rilevato.</span><span class="sxs-lookup"><span data-stu-id="f7812-251">The joint is not tracked.</span></span>

<span data-ttu-id="f7812-252">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. approssimate**</span><span class="sxs-lookup"><span data-stu-id="f7812-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="f7812-253">La posizione congiunta viene dedotta.</span><span class="sxs-lookup"><span data-stu-id="f7812-253">The joint position is inferred.</span></span>

<span data-ttu-id="f7812-254">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="f7812-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="f7812-255">Il giunto è completamente monitorato.</span><span class="sxs-lookup"><span data-stu-id="f7812-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="f7812-256">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="f7812-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="f7812-257">Accuratezza del rilevamento di una giunzione della mano.</span><span class="sxs-lookup"><span data-stu-id="f7812-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="f7812-258">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="f7812-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="f7812-259">Le giunzioni del dito della mano sono configurate in modo da riflettere una posa chiusa.</span><span class="sxs-lookup"><span data-stu-id="f7812-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="f7812-260">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="f7812-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="f7812-261">Le giunzioni del dito della mano sono configurate in modo da riflettere una posa aperta.</span><span class="sxs-lookup"><span data-stu-id="f7812-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="f7812-262">**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="f7812-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="f7812-263">Le giunzioni del dito della mano sono configurate in modo da riflettere una posa di puntamento.</span><span class="sxs-lookup"><span data-stu-id="f7812-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="f7812-264">**Microsoft. PerceptionSimulation. SimulatedHandPose. Pinch**</span><span class="sxs-lookup"><span data-stu-id="f7812-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="f7812-265">Le giunzioni del dito della mano sono configurate in modo da riflettere una puntura.</span><span class="sxs-lookup"><span data-stu-id="f7812-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="f7812-266">**Microsoft. PerceptionSimulation. SimulatedHandPose. max**</span><span class="sxs-lookup"><span data-stu-id="f7812-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="f7812-267">Valore massimo valido per SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="f7812-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="f7812-268">Microsoft. PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="f7812-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="f7812-269">Descrive lo stato di una riproduzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="f7812-270">**Microsoft. PerceptionSimulation. PlaybackState. Stopped**</span><span class="sxs-lookup"><span data-stu-id="f7812-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="f7812-271">La registrazione è attualmente arrestata e pronta per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="f7812-272">**Microsoft. PerceptionSimulation. PlaybackState. playing**</span><span class="sxs-lookup"><span data-stu-id="f7812-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="f7812-273">La registrazione è attualmente in riproduzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-273">The recording is currently playing.</span></span>

<span data-ttu-id="f7812-274">**Microsoft. PerceptionSimulation. PlaybackState. Paused**</span><span class="sxs-lookup"><span data-stu-id="f7812-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="f7812-275">La registrazione è attualmente sospesa.</span><span class="sxs-lookup"><span data-stu-id="f7812-275">The recording is currently paused.</span></span>

<span data-ttu-id="f7812-276">**Microsoft. PerceptionSimulation. PlaybackState. end**</span><span class="sxs-lookup"><span data-stu-id="f7812-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="f7812-277">La registrazione ha raggiunto la fine.</span><span class="sxs-lookup"><span data-stu-id="f7812-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="f7812-278">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="f7812-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="f7812-279">Descrive un vettore di 3 componenti, che può descrivere un punto o un vettore nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="f7812-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="f7812-280">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="f7812-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="f7812-281">Componente X del vettore.</span><span class="sxs-lookup"><span data-stu-id="f7812-281">The X component of the vector.</span></span>

<span data-ttu-id="f7812-282">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="f7812-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="f7812-283">Componente Y del vettore.</span><span class="sxs-lookup"><span data-stu-id="f7812-283">The Y component of the vector.</span></span>

<span data-ttu-id="f7812-284">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="f7812-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="f7812-285">Componente Z del vettore.</span><span class="sxs-lookup"><span data-stu-id="f7812-285">The Z component of the vector.</span></span>

<span data-ttu-id="f7812-286">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="f7812-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="f7812-287">Costruire un nuovo Vector3.</span><span class="sxs-lookup"><span data-stu-id="f7812-287">Construct a new Vector3.</span></span>

<span data-ttu-id="f7812-288">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-288">Parameters</span></span>
* <span data-ttu-id="f7812-289">x: componente x del vettore.</span><span class="sxs-lookup"><span data-stu-id="f7812-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="f7812-290">y: componente y del vettore.</span><span class="sxs-lookup"><span data-stu-id="f7812-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="f7812-291">z: componente z del vettore.</span><span class="sxs-lookup"><span data-stu-id="f7812-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="f7812-292">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="f7812-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="f7812-293">Descrive una rotazione di 3 componenti.</span><span class="sxs-lookup"><span data-stu-id="f7812-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="f7812-294">**Microsoft. PerceptionSimulation. Rotation3. Pitch**</span><span class="sxs-lookup"><span data-stu-id="f7812-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="f7812-295">Componente pitch della rotazione, verso il basso attorno all'asse X.</span><span class="sxs-lookup"><span data-stu-id="f7812-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="f7812-296">**Microsoft. PerceptionSimulation. Rotation3. imbardata**</span><span class="sxs-lookup"><span data-stu-id="f7812-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="f7812-297">Componente di imbardata della rotazione, immediatamente intorno all'asse Y.</span><span class="sxs-lookup"><span data-stu-id="f7812-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="f7812-298">**Microsoft. PerceptionSimulation. Rotation3. roll**</span><span class="sxs-lookup"><span data-stu-id="f7812-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="f7812-299">Componente di roll della rotazione, immediatamente intorno all'asse Z.</span><span class="sxs-lookup"><span data-stu-id="f7812-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="f7812-300">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="f7812-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="f7812-301">Costruire un nuovo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="f7812-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="f7812-302">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-302">Parameters</span></span>
* <span data-ttu-id="f7812-303">Pitch: componente pitch della rotazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="f7812-304">imbardata: componente imbardata della rotazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="f7812-305">Roll-il componente roll della rotazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="f7812-306">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7812-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="f7812-307">Descrive la configurazione di un insieme in una mano simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="f7812-308">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="f7812-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="f7812-309">Posizione della giunzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-309">The position of the joint.</span></span>

<span data-ttu-id="f7812-310">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="f7812-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="f7812-311">Rotazione della giunzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-311">The rotation of the joint.</span></span>

<span data-ttu-id="f7812-312">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="f7812-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="f7812-313">Accuratezza del rilevamento della giunzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="f7812-314">Microsoft. PerceptionSimulation. tronco</span><span class="sxs-lookup"><span data-stu-id="f7812-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="f7812-315">Descrive una vista tronco, usata in genere da una fotocamera.</span><span class="sxs-lookup"><span data-stu-id="f7812-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="f7812-316">**Microsoft. PerceptionSimulation. tronco. near**</span><span class="sxs-lookup"><span data-stu-id="f7812-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="f7812-317">Distanza minima contenuta in tronco.</span><span class="sxs-lookup"><span data-stu-id="f7812-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="f7812-318">**Microsoft. PerceptionSimulation. tronco. lontano**</span><span class="sxs-lookup"><span data-stu-id="f7812-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="f7812-319">Distanza massima contenuta in tronco.</span><span class="sxs-lookup"><span data-stu-id="f7812-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="f7812-320">**Microsoft. PerceptionSimulation. tronco. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="f7812-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="f7812-321">Campo orizzontale della visualizzazione di tronco, in radianti (minore di PI).</span><span class="sxs-lookup"><span data-stu-id="f7812-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="f7812-322">**Microsoft. PerceptionSimulation. tronco. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="f7812-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="f7812-323">Rapporto tra il campo orizzontale e la visualizzazione e il campo verticale della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="f7812-324">Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7812-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="f7812-325">Descrive la configurazione del display simulato dell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="f7812-325">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="f7812-326">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="f7812-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="f7812-327">Trasformazione dal centro della parte centrale all'occhio sinistro per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="f7812-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="f7812-328">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="f7812-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="f7812-329">Rotazione dell'occhio sinistro a scopo di rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="f7812-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="f7812-330">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="f7812-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="f7812-331">Trasformazione dal centro dell'inizio all'occhio destro per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="f7812-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="f7812-332">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="f7812-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="f7812-333">Rotazione dell'occhio destro per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="f7812-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="f7812-334">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. dpi**</span><span class="sxs-lookup"><span data-stu-id="f7812-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="f7812-335">Valore di dpi segnalato dal sistema per il rendering stereo.</span><span class="sxs-lookup"><span data-stu-id="f7812-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="f7812-336">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="f7812-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="f7812-337">Indica se i valori specificati per le trasformazioni a sinistra e a destra devono essere considerati validi e applicati al sistema in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="f7812-338">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="f7812-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="f7812-339">Indica se il valore specificato per la funzione DPI deve essere considerato valido e applicato al sistema in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="f7812-340">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f7812-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="f7812-341">Radice per la generazione dei pacchetti usati per controllare un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f7812-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="f7812-342">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="f7812-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="f7812-343">Recuperare l'oggetto dispositivo simulato che interpreta l'uomo simulato e il mondo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="f7812-344">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="f7812-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="f7812-345">Recuperare l'oggetto che controlla l'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="f7812-346">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="f7812-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="f7812-347">Reimposta lo stato predefinito della simulazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="f7812-348">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="f7812-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="f7812-349">Interfaccia che descrive il dispositivo che interpreta il mondo simulato e l'uomo simulato</span><span class="sxs-lookup"><span data-stu-id="f7812-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="f7812-350">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="f7812-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="f7812-351">Recuperare l'Head Tracker dal dispositivo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="f7812-352">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="f7812-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="f7812-353">Recuperare il Tracker mano dal dispositivo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="f7812-354">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="f7812-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="f7812-355">Impostare le proprietà del dispositivo simulato in modo che corrispondano al tipo di dispositivo specificato.</span><span class="sxs-lookup"><span data-stu-id="f7812-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="f7812-356">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-356">Parameters</span></span>
* <span data-ttu-id="f7812-357">Tipo: nuovo tipo di dispositivo simulato</span><span class="sxs-lookup"><span data-stu-id="f7812-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="f7812-358">Microsoft. PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="f7812-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="f7812-359">Sono disponibili proprietà aggiuntive eseguendo il cast di ISimulatedDevice a ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="f7812-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="f7812-360">**Microsoft. PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="f7812-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="f7812-361">Recuperare o impostare un valore che indica se l'uomo simulato sta attivamente indossando l'auricolare.</span><span class="sxs-lookup"><span data-stu-id="f7812-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="f7812-362">**Microsoft. PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f7812-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="f7812-363">Recuperare o impostare le proprietà della visualizzazione simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="f7812-364">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="f7812-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="f7812-365">Interfaccia che descrive la parte del dispositivo simulato che tiene traccia del titolo dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="f7812-366">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="f7812-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="f7812-367">Recupera e imposta la modalità di rilevamento Head corrente.</span><span class="sxs-lookup"><span data-stu-id="f7812-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="f7812-368">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="f7812-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="f7812-369">Interfaccia che descrive la parte del dispositivo simulato che tiene traccia delle mani dell'uomo simulato</span><span class="sxs-lookup"><span data-stu-id="f7812-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="f7812-370">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f7812-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="f7812-371">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f7812-372">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="f7812-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="f7812-373">Recuperare e impostare la posizione della traccia a mano simulata, relativa al centro della testa.</span><span class="sxs-lookup"><span data-stu-id="f7812-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="f7812-374">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Pitch**</span><span class="sxs-lookup"><span data-stu-id="f7812-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="f7812-375">Recuperare e impostare il passo verso il basso della traccia a mano simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="f7812-376">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="f7812-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="f7812-377">Recuperare e impostare se il tronco della traccia a mano simulata viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="f7812-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="f7812-378">Quando viene ignorato, entrambe le mani sono sempre visibili.</span><span class="sxs-lookup"><span data-stu-id="f7812-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="f7812-379">Quando non vengono ignorate (impostazione predefinita), le mani sono visibili solo quando si trovano all'interno del tronco della traccia a mano.</span><span class="sxs-lookup"><span data-stu-id="f7812-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="f7812-380">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. tronco**</span><span class="sxs-lookup"><span data-stu-id="f7812-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="f7812-381">Recuperare e impostare le proprietà tronco usate per determinare se le mani sono visibili per la traccia a mano simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="f7812-382">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="f7812-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="f7812-383">Interfaccia di primo livello per il controllo dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-383">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="f7812-384">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f7812-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="f7812-385">Recuperare e impostare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="f7812-386">La posizione corrisponde a un punto al centro dei piedi dell'uomo.</span><span class="sxs-lookup"><span data-stu-id="f7812-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="f7812-387">**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="f7812-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="f7812-388">Recuperare e impostare la direzione dei visi umani simulati nel mondo.</span><span class="sxs-lookup"><span data-stu-id="f7812-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="f7812-389">0 radianti si affacciano sull'asse Z negativo.</span><span class="sxs-lookup"><span data-stu-id="f7812-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="f7812-390">Radianti positivi ruotano in senso orario sull'asse Y.</span><span class="sxs-lookup"><span data-stu-id="f7812-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="f7812-391">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="f7812-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="f7812-392">Recuperare e impostare l'altezza dell'oggetto umano simulato, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="f7812-393">**Microsoft. PerceptionSimulation. ISimulatedHuman. Mancini**</span><span class="sxs-lookup"><span data-stu-id="f7812-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="f7812-394">Recuperare il lato sinistro dell'oggetto umano simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="f7812-395">**Microsoft. PerceptionSimulation. ISimulatedHuman. destra**</span><span class="sxs-lookup"><span data-stu-id="f7812-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="f7812-396">Recuperare la mano giusta dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="f7812-397">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="f7812-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="f7812-398">Recuperare l'intestazione dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="f7812-399">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="f7812-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f7812-400">Spostare l'oggetto umano simulato rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="f7812-401">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-401">Parameters</span></span>
* <span data-ttu-id="f7812-402">Translation: la traduzione da spostare rispetto alla posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="f7812-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="f7812-403">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="f7812-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="f7812-404">Ruotare l'oggetto umano simulato rispetto alla direzione corrente, in senso orario sull'asse Y</span><span class="sxs-lookup"><span data-stu-id="f7812-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="f7812-405">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-405">Parameters</span></span>
* <span data-ttu-id="f7812-406">radianti: la quantità da ruotare intorno all'asse Y.</span><span class="sxs-lookup"><span data-stu-id="f7812-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="f7812-407">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="f7812-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="f7812-408">Sono disponibili proprietà aggiuntive eseguendo il cast di ISimulatedHuman a ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="f7812-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="f7812-409">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="f7812-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="f7812-410">Recuperare il controller 6-DOF a sinistra.</span><span class="sxs-lookup"><span data-stu-id="f7812-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="f7812-411">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="f7812-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="f7812-412">Recuperare il controller 6-DOF a destra.</span><span class="sxs-lookup"><span data-stu-id="f7812-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="f7812-413">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="f7812-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="f7812-414">Interfaccia che descrive una mano dell'uomo simulato</span><span class="sxs-lookup"><span data-stu-id="f7812-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="f7812-415">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f7812-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="f7812-416">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f7812-417">**Microsoft. PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="f7812-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="f7812-418">Recuperare e impostare la posizione della mano simulata rispetto all'oggetto umano, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="f7812-419">**Microsoft. PerceptionSimulation. ISimulatedHand. Activated**</span><span class="sxs-lookup"><span data-stu-id="f7812-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="f7812-420">Recuperare e impostare se la mano è attualmente attivata.</span><span class="sxs-lookup"><span data-stu-id="f7812-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="f7812-421">**Microsoft. PerceptionSimulation. ISimulatedHand. Visible**</span><span class="sxs-lookup"><span data-stu-id="f7812-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="f7812-422">Recuperare se la mano è attualmente visibile a SimulatedDevice (ad esempio, se si trova in una posizione che deve essere rilevata da HandTracker).</span><span class="sxs-lookup"><span data-stu-id="f7812-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="f7812-423">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="f7812-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="f7812-424">Spostare la mano in modo che sia visibile a SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="f7812-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="f7812-425">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="f7812-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f7812-426">Spostare la posizione della mano simulata rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="f7812-427">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-427">Parameters</span></span>
* <span data-ttu-id="f7812-428">Translation: la quantità per tradurre la mano simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="f7812-429">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="f7812-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="f7812-430">Eseguire un movimento usando la mano simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="f7812-431">Verrà rilevato solo dal sistema se la mano è abilitata.</span><span class="sxs-lookup"><span data-stu-id="f7812-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="f7812-432">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-432">Parameters</span></span>
* <span data-ttu-id="f7812-433">Gesture: movimento da eseguire.</span><span class="sxs-lookup"><span data-stu-id="f7812-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="f7812-434">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="f7812-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="f7812-435">Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHand a ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="f7812-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="f7812-436">**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="f7812-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="f7812-437">Recuperare o impostare la rotazione della mano simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="f7812-438">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="f7812-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="f7812-439">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="f7812-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="f7812-440">Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHand in ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="f7812-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="f7812-441">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f7812-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="f7812-442">Ottiene la configurazione congiunta per il giunto specificato.</span><span class="sxs-lookup"><span data-stu-id="f7812-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="f7812-443">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f7812-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="f7812-444">Imposta la configurazione congiunta per il giunto specificato.</span><span class="sxs-lookup"><span data-stu-id="f7812-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="f7812-445">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="f7812-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="f7812-446">Impostare la mano su una forma nota con un flag facoltativo a cui aggiungere un'animazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="f7812-447">Nota: l'animazione non comporterà l'aggiunta immediata di giunzioni che riflettono le configurazioni finali.</span><span class="sxs-lookup"><span data-stu-id="f7812-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="f7812-448">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="f7812-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="f7812-449">Interfaccia che descrive l'intestazione dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="f7812-450">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f7812-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="f7812-451">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f7812-452">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="f7812-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="f7812-453">Recuperare la rotazione della testa simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="f7812-454">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="f7812-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f7812-455">**Microsoft. PerceptionSimulation. ISimulatedHead. Diametr**</span><span class="sxs-lookup"><span data-stu-id="f7812-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="f7812-456">Recuperare il diametro della testa simulata.</span><span class="sxs-lookup"><span data-stu-id="f7812-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="f7812-457">Questo valore viene usato per determinare il centro della testa (punto di rotazione).</span><span class="sxs-lookup"><span data-stu-id="f7812-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="f7812-458">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="f7812-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="f7812-459">Ruota la testa simulata rispetto alla rotazione corrente.</span><span class="sxs-lookup"><span data-stu-id="f7812-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="f7812-460">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="f7812-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f7812-461">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-461">Parameters</span></span>
* <span data-ttu-id="f7812-462">Rotation: quantità da ruotare.</span><span class="sxs-lookup"><span data-stu-id="f7812-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="f7812-463">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="f7812-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="f7812-464">Sono disponibili proprietà aggiuntive eseguendo il cast di un ISimulatedHead in ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="f7812-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="f7812-465">**Microsoft. PerceptionSimulation. ISimulatedHead2. Eyes**</span><span class="sxs-lookup"><span data-stu-id="f7812-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="f7812-466">Recuperare gli occhi dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="f7812-467">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="f7812-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="f7812-468">Interfaccia che descrive un controller 6-DOF associato all'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="f7812-469">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f7812-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="f7812-470">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f7812-471">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**</span><span class="sxs-lookup"><span data-stu-id="f7812-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="f7812-472">Recuperare o impostare lo stato corrente del controller.</span><span class="sxs-lookup"><span data-stu-id="f7812-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="f7812-473">Lo stato del controller deve essere impostato su un valore diverso da off prima che tutte le chiamate per lo spostamento, la rotazione o la pressione dei pulsanti abbiano esito positivo.</span><span class="sxs-lookup"><span data-stu-id="f7812-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="f7812-474">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="f7812-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="f7812-475">Recuperare o impostare la posizione del controller simulato rispetto all'oggetto umano, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="f7812-476">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**</span><span class="sxs-lookup"><span data-stu-id="f7812-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="f7812-477">Recupera o imposta l'orientamento del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="f7812-478">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="f7812-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f7812-479">Spostare la posizione del controller simulato rispetto alla posizione corrente, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="f7812-480">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-480">Parameters</span></span>
* <span data-ttu-id="f7812-481">Translation: quantità di conversione del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="f7812-482">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="f7812-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="f7812-483">Premere un pulsante sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="f7812-484">Verrà rilevato solo dal sistema se il controller è abilitato.</span><span class="sxs-lookup"><span data-stu-id="f7812-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="f7812-485">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-485">Parameters</span></span>
* <span data-ttu-id="f7812-486">Button-pulsante da premere.</span><span class="sxs-lookup"><span data-stu-id="f7812-486">button - The button to press.</span></span>

<span data-ttu-id="f7812-487">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="f7812-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="f7812-488">Rilasciare un pulsante sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="f7812-489">Verrà rilevato solo dal sistema se il controller è abilitato.</span><span class="sxs-lookup"><span data-stu-id="f7812-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="f7812-490">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-490">Parameters</span></span>
* <span data-ttu-id="f7812-491">Button-pulsante da rilasciare.</span><span class="sxs-lookup"><span data-stu-id="f7812-491">button - The button to release.</span></span>

<span data-ttu-id="f7812-492">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="f7812-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="f7812-493">Ottiene la posizione di un dito simulato nel touchpad del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="f7812-494">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-494">Parameters</span></span>
* <span data-ttu-id="f7812-495">x: posizione orizzontale del dito.</span><span class="sxs-lookup"><span data-stu-id="f7812-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="f7812-496">y: posizione verticale del dito.</span><span class="sxs-lookup"><span data-stu-id="f7812-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="f7812-497">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="f7812-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="f7812-498">Imposta la posizione di un dito simulato nel touchpad del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="f7812-499">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-499">Parameters</span></span>
* <span data-ttu-id="f7812-500">x: posizione orizzontale del dito.</span><span class="sxs-lookup"><span data-stu-id="f7812-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="f7812-501">y: posizione verticale del dito.</span><span class="sxs-lookup"><span data-stu-id="f7812-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="f7812-502">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="f7812-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="f7812-503">Sono disponibili proprietà e metodi aggiuntivi eseguendo il cast di un ISimulatedSixDofController in ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="f7812-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="f7812-504">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="f7812-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="f7812-505">Ottiene la posizione della levetta simulata sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="f7812-506">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-506">Parameters</span></span>
* <span data-ttu-id="f7812-507">x: posizione orizzontale di levetta.</span><span class="sxs-lookup"><span data-stu-id="f7812-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="f7812-508">y: posizione verticale del levetta.</span><span class="sxs-lookup"><span data-stu-id="f7812-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="f7812-509">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="f7812-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="f7812-510">Impostare la posizione della levetta simulata sul controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="f7812-511">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-511">Parameters</span></span>
* <span data-ttu-id="f7812-512">x: posizione orizzontale di levetta.</span><span class="sxs-lookup"><span data-stu-id="f7812-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="f7812-513">y: posizione verticale del levetta.</span><span class="sxs-lookup"><span data-stu-id="f7812-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="f7812-514">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="f7812-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="f7812-515">Recuperare o impostare il livello di batteria del controller simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="f7812-516">Il valore deve essere maggiore di 0,0 e minore o uguale a 100,0.</span><span class="sxs-lookup"><span data-stu-id="f7812-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="f7812-517">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="f7812-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="f7812-518">Interfaccia che descrive gli occhi dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="f7812-519">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="f7812-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="f7812-520">Recuperare la rotazione degli occhi simulati.</span><span class="sxs-lookup"><span data-stu-id="f7812-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="f7812-521">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="f7812-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f7812-522">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="f7812-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="f7812-523">Ruotare gli occhi simulati rispetto alla rotazione corrente.</span><span class="sxs-lookup"><span data-stu-id="f7812-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="f7812-524">Radianti positivi ruotano in senso orario durante la ricerca lungo l'asse.</span><span class="sxs-lookup"><span data-stu-id="f7812-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f7812-525">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-525">Parameters</span></span>
* <span data-ttu-id="f7812-526">Rotation: quantità da ruotare.</span><span class="sxs-lookup"><span data-stu-id="f7812-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="f7812-527">**Microsoft. PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="f7812-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="f7812-528">Recupera o imposta lo stato di calibrazione degli occhi simulati.</span><span class="sxs-lookup"><span data-stu-id="f7812-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="f7812-529">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f7812-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="f7812-530">Recuperare la posizione del nodo con la relazione con il mondo, in metri.</span><span class="sxs-lookup"><span data-stu-id="f7812-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="f7812-531">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="f7812-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="f7812-532">Interfaccia per l'interazione con una singola registrazione caricata per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="f7812-533">**Microsoft. PerceptionSimulation. ISimulationRecording. DataTypes**</span><span class="sxs-lookup"><span data-stu-id="f7812-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="f7812-534">Recupera l'elenco dei tipi di dati nella registrazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="f7812-535">**Microsoft. PerceptionSimulation. ISimulationRecording. state**</span><span class="sxs-lookup"><span data-stu-id="f7812-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="f7812-536">Recupera lo stato corrente della registrazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="f7812-537">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="f7812-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="f7812-538">Avviare la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-538">Start the playback.</span></span> <span data-ttu-id="f7812-539">Se la registrazione viene sospesa, la riproduzione riprenderà dal percorso sospeso; Se arrestata, la riproduzione inizierà dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="f7812-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="f7812-540">Se è già in esecuzione, questa chiamata viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="f7812-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="f7812-541">**Microsoft. PerceptionSimulation. ISimulationRecording. pause**</span><span class="sxs-lookup"><span data-stu-id="f7812-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="f7812-542">Sospende la riproduzione nella posizione corrente.</span><span class="sxs-lookup"><span data-stu-id="f7812-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="f7812-543">Se la registrazione viene arrestata, la chiamata viene ignorata.</span><span class="sxs-lookup"><span data-stu-id="f7812-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="f7812-544">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="f7812-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="f7812-545">Cerca la registrazione per il tempo specificato (in intervalli di 100 nanosecondi dall'inizio) e si ferma in corrispondenza di tale posizione.</span><span class="sxs-lookup"><span data-stu-id="f7812-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="f7812-546">Se l'ora supera la fine della registrazione, viene sospesa in corrispondenza dell'ultimo frame.</span><span class="sxs-lookup"><span data-stu-id="f7812-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="f7812-547">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-547">Parameters</span></span>
* <span data-ttu-id="f7812-548">cicli: il tempo in cui eseguire la ricerca.</span><span class="sxs-lookup"><span data-stu-id="f7812-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="f7812-549">**Microsoft. PerceptionSimulation. ISimulationRecording. Stop**</span><span class="sxs-lookup"><span data-stu-id="f7812-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="f7812-550">Arresta la riproduzione e reimposta la posizione iniziale.</span><span class="sxs-lookup"><span data-stu-id="f7812-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="f7812-551">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="f7812-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="f7812-552">Interfaccia per la ricezione delle modifiche di stato durante la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="f7812-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="f7812-553">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="f7812-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="f7812-554">Chiamato quando viene modificato lo stato di riproduzione di un ISimulationRecording.</span><span class="sxs-lookup"><span data-stu-id="f7812-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="f7812-555">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-555">Parameters</span></span>
* <span data-ttu-id="f7812-556">newState: nuovo stato della registrazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="f7812-557">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f7812-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="f7812-558">Oggetto radice per la creazione di oggetti di simulazione della percezione.</span><span class="sxs-lookup"><span data-stu-id="f7812-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="f7812-559">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="f7812-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="f7812-560">Creare sull'oggetto per generare pacchetti simulati e distribuirli al sink fornito.</span><span class="sxs-lookup"><span data-stu-id="f7812-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="f7812-561">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-561">Parameters</span></span>
* <span data-ttu-id="f7812-562">sink: sink che riceverà tutti i pacchetti generati.</span><span class="sxs-lookup"><span data-stu-id="f7812-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="f7812-563">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f7812-563">Return value</span></span>

<span data-ttu-id="f7812-564">Gestore creato.</span><span class="sxs-lookup"><span data-stu-id="f7812-564">The created Manager.</span></span>

<span data-ttu-id="f7812-565">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="f7812-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="f7812-566">Consente di creare un sink che archivia tutti i pacchetti ricevuti in un file nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="f7812-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="f7812-567">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-567">Parameters</span></span>
* <span data-ttu-id="f7812-568">Path: percorso del file da creare.</span><span class="sxs-lookup"><span data-stu-id="f7812-568">path - The path of the file to create.</span></span>

<span data-ttu-id="f7812-569">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f7812-569">Return value</span></span>

<span data-ttu-id="f7812-570">Sink creato.</span><span class="sxs-lookup"><span data-stu-id="f7812-570">The created sink.</span></span>

<span data-ttu-id="f7812-571">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="f7812-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="f7812-572">Carica una registrazione dal file specificato.</span><span class="sxs-lookup"><span data-stu-id="f7812-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="f7812-573">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-573">Parameters</span></span>
* <span data-ttu-id="f7812-574">Path: percorso del file da caricare.</span><span class="sxs-lookup"><span data-stu-id="f7812-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="f7812-575">Factory: Factory usata dalla registrazione per la creazione di un ISimulationStreamSink quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="f7812-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="f7812-576">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f7812-576">Return value</span></span>

<span data-ttu-id="f7812-577">Registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="f7812-577">The loaded recording.</span></span>

<span data-ttu-id="f7812-578">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="f7812-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="f7812-579">Carica una registrazione dal file specificato.</span><span class="sxs-lookup"><span data-stu-id="f7812-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="f7812-580">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-580">Parameters</span></span>
* <span data-ttu-id="f7812-581">Path: percorso del file da caricare.</span><span class="sxs-lookup"><span data-stu-id="f7812-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="f7812-582">Factory: Factory usata dalla registrazione per la creazione di un ISimulationStreamSink quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="f7812-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="f7812-583">callback: callback che riceve aggiornamenti che rigradano lo stato della registrazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="f7812-584">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f7812-584">Return value</span></span>

<span data-ttu-id="f7812-585">Registrazione caricata.</span><span class="sxs-lookup"><span data-stu-id="f7812-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="f7812-586">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="f7812-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="f7812-587">Vengono descritti i diversi tipi di dati di flusso.</span><span class="sxs-lookup"><span data-stu-id="f7812-587">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="f7812-588">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="f7812-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="f7812-589">Valore sentinella utilizzato per indicare nessun tipo di dati di flusso.</span><span class="sxs-lookup"><span data-stu-id="f7812-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="f7812-590">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="f7812-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="f7812-591">Flusso di dati relativi alla posizione e all'orientamento della testa.</span><span class="sxs-lookup"><span data-stu-id="f7812-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="f7812-592">**Microsoft. PerceptionSimulation. StreamDataTypes. Hands**</span><span class="sxs-lookup"><span data-stu-id="f7812-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="f7812-593">Flusso di dati relativi alla posizione e ai movimenti delle mani.</span><span class="sxs-lookup"><span data-stu-id="f7812-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="f7812-594">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="f7812-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="f7812-595">Flusso di dati relativi al mapping spaziale dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="f7812-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="f7812-596">**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**</span><span class="sxs-lookup"><span data-stu-id="f7812-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="f7812-597">Flusso di dati relativi alla calibrazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f7812-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="f7812-598">I pacchetti di calibrazione sono accettati solo da un sistema in modalità remota.</span><span class="sxs-lookup"><span data-stu-id="f7812-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="f7812-599">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="f7812-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="f7812-600">Flusso dei dati relativi all'ambiente del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f7812-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="f7812-601">**Microsoft. PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="f7812-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="f7812-602">Flusso di dati relativi ai controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="f7812-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="f7812-603">**Microsoft. PerceptionSimulation. StreamDataTypes. Eyes**</span><span class="sxs-lookup"><span data-stu-id="f7812-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="f7812-604">Flusso di dati relativi agli occhi dell'uomo simulato.</span><span class="sxs-lookup"><span data-stu-id="f7812-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="f7812-605">**Microsoft. PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f7812-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="f7812-606">Flusso di dati relativi alla configurazione di visualizzazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f7812-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="f7812-607">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="f7812-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="f7812-608">Valore sentinella utilizzato per indicare tutti i tipi di dati registrati.</span><span class="sxs-lookup"><span data-stu-id="f7812-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="f7812-609">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="f7812-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="f7812-610">Oggetto che riceve pacchetti di dati da un flusso di simulazione.</span><span class="sxs-lookup"><span data-stu-id="f7812-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="f7812-611">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint length, byte [] Packet)**</span><span class="sxs-lookup"><span data-stu-id="f7812-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="f7812-612">Riceve un singolo pacchetto, che è tipizzato internamente e con controllo delle versioni.</span><span class="sxs-lookup"><span data-stu-id="f7812-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="f7812-613">Parametri</span><span class="sxs-lookup"><span data-stu-id="f7812-613">Parameters</span></span>
* <span data-ttu-id="f7812-614">length: lunghezza del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="f7812-614">length - The length of the packet.</span></span>
* <span data-ttu-id="f7812-615">Packet: dati del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="f7812-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="f7812-616">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="f7812-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="f7812-617">Oggetto che crea ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="f7812-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="f7812-618">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="f7812-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="f7812-619">Crea una singola istanza di ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="f7812-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="f7812-620">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="f7812-620">Return value</span></span>

<span data-ttu-id="f7812-621">Sink creato.</span><span class="sxs-lookup"><span data-stu-id="f7812-621">The created sink.</span></span>
