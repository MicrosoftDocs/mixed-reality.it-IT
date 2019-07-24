---
title: Modalità di ricerca HoloLens
description: Usando la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi dei sensori del dispositivo chiave (profondità, rilevamento dell'ambiente e riflettanza IR).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modalità di ricerca, CV, RS4, visione artificiale, ricerca, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829929"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="a539a-104">Modalità di ricerca HoloLens</span><span class="sxs-lookup"><span data-stu-id="a539a-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="a539a-105">Questa funzionalità è stata aggiunta come parte dell' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md) per HoloLens e non è disponibile nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="a539a-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="a539a-106">La modalità di ricerca è una nuova funzionalità di HoloLens che fornisce l'accesso alle applicazioni ai sensori chiave del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a539a-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="a539a-107">Sono inclusi:</span><span class="sxs-lookup"><span data-stu-id="a539a-107">These include:</span></span>
- <span data-ttu-id="a539a-108">Le quattro fotocamere di rilevamento dell'ambiente usate dal sistema per la creazione e il rilevamento della mappa.</span><span class="sxs-lookup"><span data-stu-id="a539a-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="a539a-109">Due versioni dei dati di profondità della fotocamera, una per il rilevamento ad alta frequenza (30 FPS), comunemente usata per il rilevamento manuale e l'altra per il rilevamento di più bassa frequenza (1 FPS), attualmente usata dal mapping spaziale,</span><span class="sxs-lookup"><span data-stu-id="a539a-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="a539a-110">Due versioni di un flusso IR-riflettività, usate dal HoloLens per calcolare la profondità, ma preziose nel proprio diritto, perché queste immagini sono illuminate dalla HoloLens e ragionevolmente non interessate dalla luce ambientale.</span><span class="sxs-lookup"><span data-stu-id="a539a-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="a539a-111">![Schermata dell'app modalità di ricerca](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="a539a-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="a539a-112">*Acquisizione di realtà mista di un'applicazione di test che visualizza gli otto flussi di sensori disponibili in modalità ricerca*</span><span class="sxs-lookup"><span data-stu-id="a539a-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="a539a-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="a539a-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a539a-114"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="a539a-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a539a-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a539a-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a539a-116"><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="a539a-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a539a-117">Modalità di ricerca</span><span class="sxs-lookup"><span data-stu-id="a539a-117">Research mode</span></span></td>
        <td><span data-ttu-id="a539a-118">✔️</span><span class="sxs-lookup"><span data-stu-id="a539a-118">✔️</span></span></td>
        <td><span data-ttu-id="a539a-119">❌</span><span class="sxs-lookup"><span data-stu-id="a539a-119">❌</span></span></td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="a539a-120">Prima di usare la modalità di ricerca</span><span class="sxs-lookup"><span data-stu-id="a539a-120">Before using Research mode</span></span>

<span data-ttu-id="a539a-121">La modalità di ricerca è ben denominata: è destinata ai ricercatori accademici e industriali che provano nuove idee nei campi di Visione artificiale e robotica.</span><span class="sxs-lookup"><span data-stu-id="a539a-121">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="a539a-122">La modalità di ricerca non è destinata alle applicazioni che verranno distribuite in un'organizzazione o rese disponibili nella Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="a539a-122">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="a539a-123">Il motivo è che la modalità di ricerca riduce la sicurezza del dispositivo e utilizza significativamente più energia della batteria rispetto al normale funzionamento.</span><span class="sxs-lookup"><span data-stu-id="a539a-123">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="a539a-124">Microsoft non sta eseguendo alcun commit per supportare questa modalità in tutti i dispositivi futuri.</span><span class="sxs-lookup"><span data-stu-id="a539a-124">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="a539a-125">Pertanto, è consigliabile utilizzarlo per sviluppare e testare nuove idee; Tuttavia, non sarà possibile distribuire ampiamente le applicazioni che usano la modalità di ricerca o avere garanzie che continueranno a funzionare su hardware futuro.</span><span class="sxs-lookup"><span data-stu-id="a539a-125">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="a539a-126">Abilitazione della modalità ricerca</span><span class="sxs-lookup"><span data-stu-id="a539a-126">Enabling Research mode</span></span>

<span data-ttu-id="a539a-127">La modalità di ricerca è una modalità secondaria della modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="a539a-127">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="a539a-128">Per prima cosa è necessario abilitare la modalità sviluppatore nell'app Impostazioni (**impostazioni > aggiornare & > di sicurezza per gli sviluppatori**):</span><span class="sxs-lookup"><span data-stu-id="a539a-128">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="a539a-129">Imposta "USA funzionalità per sviluppatori" **su on**</span><span class="sxs-lookup"><span data-stu-id="a539a-129">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="a539a-130">Imposta "Abilita il portale del dispositivo" **su on**</span><span class="sxs-lookup"><span data-stu-id="a539a-130">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="a539a-131">Usando un Web browser connesso alla stessa rete Wi-Fi della HoloLens, passare all'indirizzo IP della HoloLens (ottenuto tramite **le impostazioni > rete & Internet > Wi-fi > le proprietà hardware**).</span><span class="sxs-lookup"><span data-stu-id="a539a-131">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="a539a-132">Si tratta del [portale del dispositivo](using-the-windows-device-portal.md)ed è presente una pagina "modalità di ricerca" nella sezione "sistema" del portale:</span><span class="sxs-lookup"><span data-stu-id="a539a-132">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="a539a-133">![Scheda modalità ricerca del portale per dispositivi HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="a539a-133">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="a539a-134">*Modalità di ricerca nel portale per dispositivi HoloLens*</span><span class="sxs-lookup"><span data-stu-id="a539a-134">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="a539a-135">Dopo aver selezionato **Consenti accesso ai flussi di sensori**, sarà necessario riavviare HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a539a-135">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="a539a-136">Questa operazione può essere eseguita dal portale del dispositivo, sotto la voce di menu "Power" nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="a539a-136">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="a539a-137">Una volta riavviato il dispositivo, le applicazioni che sono state caricate tramite il portale per i dispositivi devono essere in grado di accedere ai flussi della modalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="a539a-137">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="a539a-138">Uso dei dati dei sensori nelle app</span><span class="sxs-lookup"><span data-stu-id="a539a-138">Using sensor data in your apps</span></span>

<span data-ttu-id="a539a-139">Le applicazioni possono accedere ai dati del flusso dei sensori aprendo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) flussi esattamente allo stesso modo in cui accedono al flusso della fotocamera Photo/video.</span><span class="sxs-lookup"><span data-stu-id="a539a-139">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="a539a-140">Tutte le API che funzionano per lo sviluppo HoloLens sono disponibili anche in modalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="a539a-140">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="a539a-141">In particolare, l'applicazione è in grado di individuare con esattezza il punto in cui HoloLens si trova nello spazio 6DoF a ogni tempo di acquisizione del frame del sensore</span><span class="sxs-lookup"><span data-stu-id="a539a-141">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="a539a-142">Applicazioni di esempio che illustrano come accedere ai vari flussi in modalità di ricerca, come usare le funzioni intrinseche ed estrinseche e come registrare i flussi sono disponibili nel [repository GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="a539a-142">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="a539a-143">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="a539a-143">Known issues</span></span>

<span data-ttu-id="a539a-144">Vedere la pagina relativa al [rilevamento dei problemi](https://github.com/Microsoft/HololensForCV/issues) nel repository HoloLensForCV.</span><span class="sxs-lookup"><span data-stu-id="a539a-144">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="a539a-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a539a-145">See also</span></span>

* [<span data-ttu-id="a539a-146">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="a539a-146">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="a539a-147">Repository GitHub HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="a539a-147">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="a539a-148">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="a539a-148">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
