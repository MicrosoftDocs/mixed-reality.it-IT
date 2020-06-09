---
title: Modalità di ricerca HoloLens
description: Usando la modalità di ricerca su HoloLens, un'applicazione può accedere ai flussi dei sensori del dispositivo chiave (profondità, rilevamento dell'ambiente e riflettanza IR).
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: modalità di ricerca, CV, RS4, visione artificiale, ricerca, HoloLens, HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533103"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="32c4c-104">Modalità ricerca HoloLens</span><span class="sxs-lookup"><span data-stu-id="32c4c-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="32c4c-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="32c4c-105">Overview</span></span>

<span data-ttu-id="32c4c-106">La modalità di ricerca è stata introdotta nella prima generazione HoloLens per consentire l'accesso ai sensori chiave sul dispositivo, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione.</span><span class="sxs-lookup"><span data-stu-id="32c4c-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="32c4c-107">È ora possibile raccogliere dati dagli input seguenti:</span><span class="sxs-lookup"><span data-stu-id="32c4c-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="32c4c-108">**Telecamere di rilevamento dell'ambiente chiaro visibili** : usate dal sistema per il rilevamento Head e la compilazione della mappa.</span><span class="sxs-lookup"><span data-stu-id="32c4c-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="32c4c-109">**Depth fotocamera** : funziona in due modalità:</span><span class="sxs-lookup"><span data-stu-id="32c4c-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="32c4c-110">Rilevamento a breve termine, ad alta frequenza (30 FPS) usato per il [rilevamento manuale](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="32c4c-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="32c4c-111">Rilevamento a lungo termine, a bassa frequenza (1-5 FPS) per un rilevamento approfondito usato dal [mapping spaziale](spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="32c4c-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="32c4c-112">**Due versioni del flusso IR-riflettività** , usate dal HoloLens per calcolare la profondità.</span><span class="sxs-lookup"><span data-stu-id="32c4c-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="32c4c-113">Queste immagini sono illuminate dall'infrarosso e non sono interessate dalla luce visibile dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="32c4c-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="32c4c-114">Se si usa un HoloLens 2, sarà anche possibile accedere agli input seguenti:</span><span class="sxs-lookup"><span data-stu-id="32c4c-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="32c4c-115">**Accelerometro** : usato dal sistema per determinare l'accelerazione lineare lungo gli assi X, Y e Z e la gravità.</span><span class="sxs-lookup"><span data-stu-id="32c4c-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="32c4c-116">**Gyro** : utilizzato dal sistema per determinare le rotazioni.</span><span class="sxs-lookup"><span data-stu-id="32c4c-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="32c4c-117">**Magnetometro** : utilizzato dal sistema per stimare l'orientamento assoluto.</span><span class="sxs-lookup"><span data-stu-id="32c4c-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="32c4c-118">![Schermata dell'app modalità di ricerca](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="32c4c-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="32c4c-119">*Acquisizione di realtà mista di un'applicazione di test che visualizza gli otto flussi di sensori disponibili in modalità ricerca*</span><span class="sxs-lookup"><span data-stu-id="32c4c-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="32c4c-120">La funzionalità modalità di ricerca è stata aggiunta come parte dell' [aggiornamento di Windows 10 aprile 2018](release-notes-april-2018.md) per HoloLens e non è disponibile nelle versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="32c4c-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="32c4c-121">Uso</span><span class="sxs-lookup"><span data-stu-id="32c4c-121">Usage</span></span>

<span data-ttu-id="32c4c-122">La modalità di ricerca è progettata per ricercatori accademici e industriali che esplorano nuove idee nei campi di Visione artificiale e robotica.</span><span class="sxs-lookup"><span data-stu-id="32c4c-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="32c4c-123">Non è destinata alle applicazioni distribuite in ambienti aziendali o disponibili tramite il Microsoft Store o altri canali di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="32c4c-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="32c4c-124">Inoltre, Microsoft non garantisce che la modalità di ricerca o la funzionalità equivalente verrà supportata negli aggiornamenti futuri dell'hardware o del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="32c4c-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="32c4c-125">Tuttavia, ciò non impedisce di usarlo per sviluppare e testare nuove idee.</span><span class="sxs-lookup"><span data-stu-id="32c4c-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="32c4c-126">Sicurezza e prestazioni</span><span class="sxs-lookup"><span data-stu-id="32c4c-126">Security and performance</span></span>

<span data-ttu-id="32c4c-127">Tenere presente che l'abilitazione della modalità di ricerca usa più potenza della batteria rispetto all'uso di HoloLens 2 in condizioni normali.</span><span class="sxs-lookup"><span data-stu-id="32c4c-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="32c4c-128">Questo vale anche se l'applicazione che usa le funzionalità della modalità di ricerca non è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="32c4c-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="32c4c-129">L'abilitazione di questa modalità può anche ridurre la sicurezza complessiva del dispositivo perché le applicazioni possono usare i dati del sensore in modo errato.</span><span class="sxs-lookup"><span data-stu-id="32c4c-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="32c4c-130">Altre informazioni sulla sicurezza del dispositivo sono disponibili nelle [domande frequenti sulla sicurezza di HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="32c4c-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="32c4c-131">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="32c4c-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="32c4c-132"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="32c4c-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="32c4c-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1 gen</strong></a></span><span class="sxs-lookup"><span data-stu-id="32c4c-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="32c4c-134">Fotocamere di rilevamento Head</span><span class="sxs-lookup"><span data-stu-id="32c4c-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="32c4c-135">✔️</span><span class="sxs-lookup"><span data-stu-id="32c4c-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="32c4c-136">Profondità & fotocamera IR</span><span class="sxs-lookup"><span data-stu-id="32c4c-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="32c4c-137">✔️</span><span class="sxs-lookup"><span data-stu-id="32c4c-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="32c4c-138">Accelerometro</span><span class="sxs-lookup"><span data-stu-id="32c4c-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="32c4c-139">Giroscopio</span><span class="sxs-lookup"><span data-stu-id="32c4c-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="32c4c-140">Magnetometro</span><span class="sxs-lookup"><span data-stu-id="32c4c-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="32c4c-141">Il supporto della modalità di ricerca per HoloLens 2 dovrebbe essere disponibile in versione di anteprima pubblica nel 2020 luglio e includerà tutte le funzionalità elencate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="32c4c-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="32c4c-142">Per ulteriori informazioni, consultare nuovamente.</span><span class="sxs-lookup"><span data-stu-id="32c4c-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="32c4c-143">Abilitazione della modalità ricerca</span><span class="sxs-lookup"><span data-stu-id="32c4c-143">Enabling Research mode</span></span>

<span data-ttu-id="32c4c-144">La modalità di ricerca è un'estensione della modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="32c4c-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="32c4c-145">Prima di iniziare, è necessario abilitare le funzionalità di sviluppo del dispositivo per accedere alle impostazioni della modalità di ricerca:</span><span class="sxs-lookup"><span data-stu-id="32c4c-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="32c4c-146">Aprire il **menu Start > impostazioni** e selezionare **aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="32c4c-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="32c4c-147">Selezionare **per gli sviluppatori** e abilitare la **modalità sviluppatore**.</span><span class="sxs-lookup"><span data-stu-id="32c4c-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="32c4c-148">Scorrere verso il basso e abilitare il **portale del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="32c4c-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="32c4c-149">Una volta abilitate le funzionalità per gli sviluppatori, [connettersi al portale del dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) per abilitare le funzionalità della modalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="32c4c-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="32c4c-150">In *HoloLens 1 gen*:</span><span class="sxs-lookup"><span data-stu-id="32c4c-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="32c4c-151">Passare alla **modalità di ricerca di System >** nel **portale del dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="32c4c-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="32c4c-152">Selezionare **Consenti accesso al flusso del sensore**.</span><span class="sxs-lookup"><span data-stu-id="32c4c-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="32c4c-153">Riavviare il dispositivo dalla voce del menu **Power** nella parte superiore della pagina.</span><span class="sxs-lookup"><span data-stu-id="32c4c-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="32c4c-154">Dopo aver riavviato il dispositivo, le applicazioni caricate tramite il **portale** per i dispositivi possono accedere ai flussi della modalità di ricerca.</span><span class="sxs-lookup"><span data-stu-id="32c4c-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="32c4c-155">![Scheda modalità ricerca del portale per dispositivi HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="32c4c-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="32c4c-156">*Finestra modalità di ricerca nel portale per dispositivi HoloLens*</span><span class="sxs-lookup"><span data-stu-id="32c4c-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="32c4c-157">Uso dei dati dei sensori nelle app</span><span class="sxs-lookup"><span data-stu-id="32c4c-157">Using sensor data in your apps</span></span>

<span data-ttu-id="32c4c-158">*HoloLens 1 gen*</span><span class="sxs-lookup"><span data-stu-id="32c4c-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="32c4c-159">Le applicazioni possono accedere ai dati del flusso dei sensori nello stesso modo in cui si accede ai flussi della fotocamera e della foto tramite [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="32c4c-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="32c4c-160">Tutte le API che funzionano per lo sviluppo di HoloLens sono disponibili anche in modalità ricerca.</span><span class="sxs-lookup"><span data-stu-id="32c4c-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="32c4c-161">In particolare, l'applicazione conosce esattamente dove HoloLens si trova nello spazio 6DoF a ogni tempo di acquisizione del fotogramma del sensore.</span><span class="sxs-lookup"><span data-stu-id="32c4c-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="32c4c-162">È possibile trovare applicazioni di esempio su come accedere ai vari flussi in modalità di ricerca, su come usare le [funzioni intrinseche e i dati estrinseci](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e su come registrare i flussi nel repository di [repository GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="32c4c-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="32c4c-163">A questo punto, l'esempio HoloLensForCV non funziona in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="32c4c-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="32c4c-164">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="32c4c-164">Known issues</span></span>

<span data-ttu-id="32c4c-165">È possibile usare lo strumento di [rilevamento](https://github.com/Microsoft/HololensForCV/issues) dei problemi nel repository HoloLensForCV per seguire i problemi noti.</span><span class="sxs-lookup"><span data-stu-id="32c4c-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="32c4c-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="32c4c-166">See also</span></span>

* [<span data-ttu-id="32c4c-167">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="32c4c-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="32c4c-168">Repository GitHub HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="32c4c-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="32c4c-169">Avviare il Portale di dispositivi di Windows</span><span class="sxs-lookup"><span data-stu-id="32c4c-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
