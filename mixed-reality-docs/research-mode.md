---
title: Modalità HoloLens Research
description: Usa la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi di sensore chiave dispositivo (profondità, l'ambiente di rilevamento e runtime di integrazione-riflettività).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modalità di ricerca, convalida incrociata, rs4, visione artificiale, ricerca, HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597512"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="4f97a-104">Modalità HoloLens Research</span><span class="sxs-lookup"><span data-stu-id="4f97a-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="4f97a-105">Questa funzionalità è stato aggiunto durante la [Windows 10 April 2018 Update](release-notes-april-2018.md) per HoloLens e non è disponibile nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="4f97a-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="4f97a-106">Modalità di ricerca è una nuova funzionalità di HoloLens che fornisce accesso alle applicazioni per i sensori di chiave nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4f97a-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="4f97a-107">tra cui:</span><span class="sxs-lookup"><span data-stu-id="4f97a-107">These include:</span></span>
- <span data-ttu-id="4f97a-108">I quattro ambiente fotocamere utilizzate dal sistema per la creazione della mappa e rilevamento head di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="4f97a-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="4f97a-109">Due versioni dei dati della fotocamera profondità, una per quasi-depth rilevazione (30 FPS) ad alta frequenza, in genere utilizzato a disposizione di rilevamento e l'altro per frequenza inferiore (1 FPS) distante profondità sensibile, è attualmente usano da Mapping spaziale,</span><span class="sxs-lookup"><span data-stu-id="4f97a-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="4f97a-110">Due versioni di un flusso di runtime di integrazione-riflettività, usata di HoloLens per calcolare profondità, ma siano utili in sé come queste immagini vengono illuminati di HoloLens e ragionevolmente interessata da luce ambientale.</span><span class="sxs-lookup"><span data-stu-id="4f97a-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="4f97a-111">![Schermata di app in modalità di ricerca](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="4f97a-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="4f97a-112">*Un'acquisizione di realtà mista di un'applicazione di test che consente di visualizzare i flussi di otto sensore disponibili in modalità di ricerca*</span><span class="sxs-lookup"><span data-stu-id="4f97a-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="4f97a-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="4f97a-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4f97a-114">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="4f97a-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4f97a-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4f97a-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4f97a-116"><a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></span><span class="sxs-lookup"><span data-stu-id="4f97a-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4f97a-117">Modalità di ricerca</span><span class="sxs-lookup"><span data-stu-id="4f97a-117">Research mode</span></span></td><td style="text-align: center;"> <span data-ttu-id="4f97a-118">✔️</span><span class="sxs-lookup"><span data-stu-id="4f97a-118">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="4f97a-119">Prima di usare la modalità di ricerca</span><span class="sxs-lookup"><span data-stu-id="4f97a-119">Before using Research mode</span></span>

<span data-ttu-id="4f97a-120">Modalità di ricerca viene anche denominata: è destinata a ricercatori accademici e industriali provare nuove idee nei campi di visione artificiale e robotica.</span><span class="sxs-lookup"><span data-stu-id="4f97a-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="4f97a-121">Modalità di ricerca non è per le applicazioni che verranno distribuite in un'organizzazione o resa disponibile in di Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="4f97a-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="4f97a-122">Il motivo è che la modalità di ricerca consente di ridurre la sicurezza del dispositivo e consuma energia della batteria significativamente maggiore rispetto al normale funzionamento.</span><span class="sxs-lookup"><span data-stu-id="4f97a-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="4f97a-123">Microsoft non esegue il commit a questa modalità di supporto in qualsiasi dispositivo future.</span><span class="sxs-lookup"><span data-stu-id="4f97a-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="4f97a-124">Di conseguenza, è consigliabile che usarlo per sviluppare e testare nuove idee; Tuttavia, non sarà in grado di distribuire ampiamente le applicazioni che usano la modalità di ricerca o qualsiasi garanzia che continuerà a lavorare su hardware future.</span><span class="sxs-lookup"><span data-stu-id="4f97a-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="4f97a-125">Abilitazione della modalità di ricerca</span><span class="sxs-lookup"><span data-stu-id="4f97a-125">Enabling Research mode</span></span>

<span data-ttu-id="4f97a-126">Modalità di ricerca è una modalità secondaria della modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="4f97a-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="4f97a-127">È innanzitutto necessario abilitare la modalità sviluppatore nell'app impostazioni (**Impostazioni > aggiornamento e sicurezza > per gli sviluppatori**):</span><span class="sxs-lookup"><span data-stu-id="4f97a-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="4f97a-128">Impostare "Usa funzionalità per sviluppatori" su **su**</span><span class="sxs-lookup"><span data-stu-id="4f97a-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="4f97a-129">Impostare "Abilita il portale del dispositivo" su **su**</span><span class="sxs-lookup"><span data-stu-id="4f97a-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="4f97a-130">Quindi usando un web browser che è connesso alla stessa rete Wi-Fi di HoloLens, passare all'indirizzo IP di HoloLens (ottenuto tramite **Impostazioni > rete e Internet > Wi-Fi > proprietà Hardware**).</span><span class="sxs-lookup"><span data-stu-id="4f97a-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="4f97a-131">Questo è il [portale dispositivi](using-the-windows-device-portal.md), sarà presente una pagina di "Modalità di ricerca" nella sezione "Sistema" del portale:</span><span class="sxs-lookup"><span data-stu-id="4f97a-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="4f97a-132">![Scheda di modalità di ricerca del portale dei dispositivi HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="4f97a-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="4f97a-133">*Modalità di ricerca nel portale di dispositivo HoloLens*</span><span class="sxs-lookup"><span data-stu-id="4f97a-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="4f97a-134">Dopo aver selezionato **consentire l'accesso ai flussi di sensore**, dovrai riavviare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4f97a-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="4f97a-135">È possibile eseguire questa operazione dal portale di dispositivo, sotto la voce di menu "Power" nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="4f97a-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="4f97a-136">Dopo aver riavviato il dispositivo, le applicazioni che sono state caricate tramite il portale di dispositivo devono essere in grado di accedere ai flussi di modalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="4f97a-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="4f97a-137">Usando i dati dei sensori nelle tue App</span><span class="sxs-lookup"><span data-stu-id="4f97a-137">Using sensor data in your apps</span></span>

<span data-ttu-id="4f97a-138">Le applicazioni possono accedere i dati del sensore flusso aprendo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) flussi in esattamente allo stesso modo che accedono al flusso di fotocamera foto/video.</span><span class="sxs-lookup"><span data-stu-id="4f97a-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="4f97a-139">Tutte le API che funzionano per lo sviluppo di HoloLens sono anche disponibili in modalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="4f97a-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="4f97a-140">In particolare, l'applicazione può sapere con precisione dove HoloLens è nello spazio 6DoF al momento dell'acquisizione frame ogni sensore.</span><span class="sxs-lookup"><span data-stu-id="4f97a-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="4f97a-141">Sono disponibili in applicazioni di esempio che illustra come registrare i flussi, come usare le funzioni intrinseche ed extrinsics e modalità di accesso i vari flussi modalità Research la [repository HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="4f97a-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="4f97a-142">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="4f97a-142">Known issues</span></span>

<span data-ttu-id="4f97a-143">Vedere le [tracker problema](https://github.com/Microsoft/HololensForCV/issues) nel repository HoloLensForCV.</span><span class="sxs-lookup"><span data-stu-id="4f97a-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f97a-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4f97a-144">See also</span></span>

* [<span data-ttu-id="4f97a-145">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="4f97a-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="4f97a-146">Repository HoloLensForCV GitHub</span><span class="sxs-lookup"><span data-stu-id="4f97a-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="4f97a-147">Utilizzando il Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="4f97a-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
