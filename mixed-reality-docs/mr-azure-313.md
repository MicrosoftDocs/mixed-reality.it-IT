---
title: MR e 313 - servizio Hub IoT di Azure
description: Completare questo corso di informazioni su come implementare il servizio Hub IoT di Azure in una macchina virtuale che esegue Ubuntu 16.4 e quindi visualizzare i dati del messaggio usando Microsoft HoloLens o un auricolare (VR) coinvolgenti.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: realtà mista, Azure, academy, edge, iot edge, esercitazione, api, la notifica, funzioni, tabelle, hololens, coinvolgenti, vr, iot, macchina virtuale, ubuntu, python
ms.openlocfilehash: 93f7dc64426360d2e02b0ee0a9b1796fc8f2b469
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694593"
---
>[!NOTE]
><span data-ttu-id="f94af-104">Le esercitazioni Academy di realtà mista sono state progettate con HoloLens (dal 1 ° generazione) e mista auricolari Immersive realtà presente.</span><span class="sxs-lookup"><span data-stu-id="f94af-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f94af-105">Siamo di conseguenza, che è importante non cancellare le esercitazioni create per gli sviluppatori che stanno ancora cercando indicazioni per lo sviluppo per tali dispositivi.</span><span class="sxs-lookup"><span data-stu-id="f94af-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f94af-106">Queste esercitazioni verranno **_non_** verrà aggiornata con il set di strumenti o in uso per HoloLens 2 interazioni più recente.</span><span class="sxs-lookup"><span data-stu-id="f94af-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f94af-107">Essi verranno mantenute per continuare a utilizzare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="f94af-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f94af-108">Sarà presente una nuova serie di esercitazioni che verranno pubblicati in futuro che consentiranno di dimostrare come lo sviluppo per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f94af-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f94af-109">Questo avviso verrà aggiornato con un collegamento a tali esercitazioni quando vengono registrate.</span><span class="sxs-lookup"><span data-stu-id="f94af-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="f94af-110">MR e Azure 313: Servizio Hub IoT</span><span class="sxs-lookup"><span data-stu-id="f94af-110">MR and Azure 313: IoT Hub Service</span></span>

![risultato del corso](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="f94af-112">In questo corso, si apprenderà come implementare un' **servizio Hub IoT di Azure** in una macchina virtuale in esecuzione il sistema operativo Ubuntu 16.4.</span><span class="sxs-lookup"><span data-stu-id="f94af-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="f94af-113">Un' **App per le funzioni** verrà usato per ricevere messaggi da una VM Ubuntu e archiviare il risultato all'interno di un' **servizio tabelle di Azure**.</span><span class="sxs-lookup"><span data-stu-id="f94af-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="f94af-114">Quindi sarà possibile visualizzare questo dati usando **Power BI** in Microsoft HoloLens o coinvolgenti visore VR (VR).</span><span class="sxs-lookup"><span data-stu-id="f94af-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="f94af-115">Il contenuto di questo corso *applicabile* nei dispositivi perimetrali IoT, ma ai fini di questo corso, lo stato attivo si sarà in un ambiente di macchina virtuale, in modo che l'accesso a un dispositivo fisico di Edge non è necessario.</span><span class="sxs-lookup"><span data-stu-id="f94af-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="f94af-116">Completando questo corso, apprenderà come:</span><span class="sxs-lookup"><span data-stu-id="f94af-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="f94af-117">Distribuire un' **modulo di IoT Edge** a una macchina virtuale (sistema operativo di Ubuntu 16), che rappresenterà un dispositivo IoT.</span><span class="sxs-lookup"><span data-stu-id="f94af-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="f94af-118">Aggiungere un **modello di Azure Custom Vision Tensorflow** per il modulo di Edge, con il codice che analizza le immagini archiviate nel contenitore.</span><span class="sxs-lookup"><span data-stu-id="f94af-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="f94af-119">Configurare il modulo per inviare il messaggio di risultato di analisi al **il servizio Hub IoT**.</span><span class="sxs-lookup"><span data-stu-id="f94af-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="f94af-120">Usa un' **App per le funzioni** per memorizzare il messaggio all'interno di un' **tabelle di Azure**.</span><span class="sxs-lookup"><span data-stu-id="f94af-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="f94af-121">Configurare **Power BI** per raccogliere il messaggio archiviato e creare un report.</span><span class="sxs-lookup"><span data-stu-id="f94af-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="f94af-122">Visualizzare i dati di messaggio IoT entro **Power BI**.</span><span class="sxs-lookup"><span data-stu-id="f94af-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="f94af-123">I servizi che si utilizzeranno includono:</span><span class="sxs-lookup"><span data-stu-id="f94af-123">The Services you will use include:</span></span>

- <span data-ttu-id="f94af-124">**IoT Hub di Azure** è un servizio di Microsoft Azure che consente agli sviluppatori di connettere, monitorare e gestire, gli asset IoT.</span><span class="sxs-lookup"><span data-stu-id="f94af-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="f94af-125">Per altre informazioni, visitare il [ **servizio Hub IoT di Azure** pagina](https://azure.microsoft.com/en-au/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="f94af-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="f94af-126">**Registro contenitori di Azure** è un servizio di Microsoft Azure che consente agli sviluppatori di archiviare immagini dei contenitori, per vari tipi di contenitori.</span><span class="sxs-lookup"><span data-stu-id="f94af-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="f94af-127">Per altre informazioni, visitare il [ **servizio Registro di sistema contenitore di Azure** pagina](https://azure.microsoft.com/en-au/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="f94af-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="f94af-128">**App per le funzioni Azure** è un servizio Microsoft Azure, che consente agli sviluppatori di eseguire piccole porzioni di codice, 'le funzioni', in Azure.</span><span class="sxs-lookup"><span data-stu-id="f94af-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="f94af-129">Ciò consente di delegare lavoro nel cloud, anziché l'applicazione locale, che può avere molti vantaggi.</span><span class="sxs-lookup"><span data-stu-id="f94af-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="f94af-130">**Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, Node. js, Java e PHP.</span><span class="sxs-lookup"><span data-stu-id="f94af-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="f94af-131">Per altre informazioni, visitare il [ **funzioni di Azure** pagina](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="f94af-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="f94af-132">**Archiviazione di Azure: Tabelle** è un servizio Microsoft Azure, che consente agli sviluppatori di archiviare strutturati, non SQL, i dati nel cloud, per renderla facilmente accessibile ovunque.</span><span class="sxs-lookup"><span data-stu-id="f94af-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="f94af-133">Il servizio vanta una struttura senza schema, che consente l'evoluzione delle tabelle in base alle esigenze ed è pertanto molto flessibile.</span><span class="sxs-lookup"><span data-stu-id="f94af-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="f94af-134">Per altre informazioni, visitare il [ **le tabelle di Azure** pagina](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="f94af-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="f94af-135">Questo corso ti spiegherà come impostare e usare il servizio Hub IoT e quindi visualizzare una risposta fornita da un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f94af-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="f94af-136">Sarà quindi compito è possibile applicare questi concetti per un'installazione personalizzata del servizio Hub IoT, che potrebbe voler costruire.</span><span class="sxs-lookup"><span data-stu-id="f94af-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="f94af-137">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="f94af-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f94af-138">Corso</span><span class="sxs-lookup"><span data-stu-id="f94af-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f94af-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f94af-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f94af-140"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="f94af-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f94af-141">MR e Azure 313: Servizio Hub IoT</span><span class="sxs-lookup"><span data-stu-id="f94af-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="f94af-142">✔️</span><span class="sxs-lookup"><span data-stu-id="f94af-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f94af-143">✔️</span><span class="sxs-lookup"><span data-stu-id="f94af-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="f94af-144">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="f94af-144">Prerequisites</span></span>

<span data-ttu-id="f94af-145">Per i prerequisiti per lo sviluppo con realtà mista, tra cui con il Microsoft HoloLens, più aggiornati, visitare il [installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) articolo.</span><span class="sxs-lookup"><span data-stu-id="f94af-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="f94af-146">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Python.</span><span class="sxs-lookup"><span data-stu-id="f94af-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="f94af-147">Inoltre tenere presente che i prerequisiti e istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="f94af-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="f94af-148">Si è liberi di utilizzare il software più recente, come indicato all'interno di [installare gli strumenti](install-the-tools.md) articolo, anche se non si deve essere presupposto che le informazioni contenute in questo corso perfettamente corrispondenti ai criteri troveranno nel software più recente rispetto a quelli elencati di seguito.</span><span class="sxs-lookup"><span data-stu-id="f94af-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="f94af-149">È necessario hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="f94af-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="f94af-150">Windows 10 Fall Creators Update (o versione successiva), **abilitata la modalità sviluppatore**</span><span class="sxs-lookup"><span data-stu-id="f94af-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="f94af-151">Non è possibile eseguire una macchina virtuale utilizzando Hyper-V in Windows 10 Home Edition.</span><span class="sxs-lookup"><span data-stu-id="f94af-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="f94af-152">Windows 10 SDK (versione più recente)</span><span class="sxs-lookup"><span data-stu-id="f94af-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="f94af-153">A HoloLens, **abilitata la modalità sviluppatore**</span><span class="sxs-lookup"><span data-stu-id="f94af-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="f94af-154">Visual Studio 2017.15.4 (usato solo per accedere a Esplora il Cloud Azure)</span><span class="sxs-lookup"><span data-stu-id="f94af-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="f94af-155">Accesso a Internet per Azure e per il servizio Hub IoT.</span><span class="sxs-lookup"><span data-stu-id="f94af-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="f94af-156">Per altre informazioni, seguire questa [collegamento alla pagina del servizio Hub IoT](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="f94af-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="f94af-157">Un modello di machine learning.</span><span class="sxs-lookup"><span data-stu-id="f94af-157">A machine learning model.</span></span> <span data-ttu-id="f94af-158">Se non è proprio pronti all'uso del modello, [è possibile usare il modello fornito con questo corso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="f94af-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="f94af-159">**Hyper-V** software abilitato nel computer di sviluppo di Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f94af-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="f94af-160">Una macchina virtuale che esegue Ubuntu 16.4 o 18.4, in esecuzione nel computer di sviluppo o in alternativa è possibile usare un computer separato che esegue Linux (Ubuntu 16.4 o 18.4).</span><span class="sxs-lookup"><span data-stu-id="f94af-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="f94af-161">È possibile trovare altre informazioni su come creare una macchina virtuale su Windows con Hyper-V nel [capitolo "Prima di iniziare"](#before-you-start). ( https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="f94af-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="f94af-162">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="f94af-162">Before you start</span></span>

1. <span data-ttu-id="f94af-163">Configurare e testare l'HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f94af-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="f94af-164">Se è necessario supportano l'impostazione di HoloLens [assicurarsi di passare all'articolo di programma di installazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="f94af-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="f94af-165">È una buona idea eseguire **calibrazione** e **sensore ottimizzazione** quando si inizia a sviluppare una nuova app per HoloLens (talvolta può essere utile eseguire tali attività per ogni utente).</span><span class="sxs-lookup"><span data-stu-id="f94af-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="f94af-166">Per informazioni su calibrazione, seguire questa [collegamento all'articolo di calibrazione HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="f94af-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="f94af-167">Per informazioni sull'ottimizzazione del sensore, seguire questa [collegamento all'articolo HoloLens sensore ottimizzazione](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="f94af-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="f94af-168">Configurare le **macchina virtuale Ubuntu** utilizzando **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="f94af-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="f94af-169">Le risorse seguenti consentono del processo.</span><span class="sxs-lookup"><span data-stu-id="f94af-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="f94af-170">In primo luogo, fare clic sul collegamento a [scaricare l'immagine ISO LTS (Xenial Xerus) Ubuntu 16.04.4](http://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="f94af-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="f94af-171">Selezionare il **immagine del desktop PC (AMD64) a 64 bit**.</span><span class="sxs-lookup"><span data-stu-id="f94af-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="f94af-172">Assicurarsi che **Hyper-V** è abilitato nel computer Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f94af-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="f94af-173">È possibile seguire questo collegamento per indicazioni [installazione e abilitazione di Hyper-V in Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="f94af-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="f94af-174">Avviare Hyper-V e creare una nuova VM di Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="f94af-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="f94af-175">È possibile seguire questo collegamento per una [Guida dettagliata su come creare una macchina virtuale con Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="f94af-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="f94af-176">Quando richiesto **"Installa un sistema operativo da un file di immagine di avvio"** , selezionare la **Ubuntu ISO** essere stati scaricati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="f94af-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f94af-177">Usando **creazione rapida di Hyper-V** non è consigliata.</span><span class="sxs-lookup"><span data-stu-id="f94af-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="f94af-178">Capitolo 1: recuperare il modello di visione artificiale personalizzato</span><span class="sxs-lookup"><span data-stu-id="f94af-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="f94af-179">Con questo corso si avrà accesso a un [modello di visione artificiale personalizzato preesistente](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) che rileva tastiere e mouse dalle immagini.</span><span class="sxs-lookup"><span data-stu-id="f94af-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="f94af-180">Se si usa questo, passare a [capitolo 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="f94af-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="f94af-181">Tuttavia, è possibile seguire questi passaggi se si vuole usare il proprio modello di visione artificiale personalizzato:</span><span class="sxs-lookup"><span data-stu-id="f94af-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="f94af-182">Nel **progetto di visione artificiale personalizzato** andare alla **prestazioni** scheda.</span><span class="sxs-lookup"><span data-stu-id="f94af-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="f94af-183">Il modello è necessario usare una *compact* dominio, per esportare il modello.</span><span class="sxs-lookup"><span data-stu-id="f94af-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="f94af-184">È possibile modificare il dominio di modelli nelle impostazioni per il progetto.</span><span class="sxs-lookup"><span data-stu-id="f94af-184">You can change your models domain in the settings for your project.</span></span>

    ![scheda prestazioni](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="f94af-186">Selezionare il **iterazione** si vuole esportare e fare clic su **esportare**.</span><span class="sxs-lookup"><span data-stu-id="f94af-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="f94af-187">Verrà visualizzato un pannello.</span><span class="sxs-lookup"><span data-stu-id="f94af-187">A blade will appear.</span></span>

    ![Pannello esportazione](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="f94af-189">Nel pannello fare clic su **File Docker**.</span><span class="sxs-lookup"><span data-stu-id="f94af-189">In the blade click **Docker File**.</span></span>

    ![Selezionare docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="f94af-191">Fare clic su **Linux** nel menu a tendina e quindi fare clic su **scaricare**.</span><span class="sxs-lookup"><span data-stu-id="f94af-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Fare clic su download](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="f94af-193">Decomprimere il contenuto.</span><span class="sxs-lookup"><span data-stu-id="f94af-193">Unzip the content.</span></span> <span data-ttu-id="f94af-194">Si userà, più avanti in questo corso.</span><span class="sxs-lookup"><span data-stu-id="f94af-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="f94af-195">Capitolo 2: il servizio contenitore di registro di sistema</span><span class="sxs-lookup"><span data-stu-id="f94af-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="f94af-196">Il **servizio contenitore di registro di sistema** è il repository usato per ospitare i contenitori.</span><span class="sxs-lookup"><span data-stu-id="f94af-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="f94af-197">Il **il servizio Hub IoT** che di compilazione e verrà utilizzato in questo corso, si intende **contenitore del Registro di sistema servizio** per ottenere i contenitori da distribuire nel dispositivo Edge.</span><span class="sxs-lookup"><span data-stu-id="f94af-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="f94af-198">Seguire prima di tutto ciò [collegamento al portale di Azure](https://portal.azure.com/)e accedere con le proprie credenziali.</span><span class="sxs-lookup"><span data-stu-id="f94af-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="f94af-199">Passare a **crea una risorsa** e cercare **registro contenitori di**.</span><span class="sxs-lookup"><span data-stu-id="f94af-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![Registro contenitori](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="f94af-201">Fare clic su **creare**.</span><span class="sxs-lookup"><span data-stu-id="f94af-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="f94af-202">Impostare il servizio di parametri di installazione:</span><span class="sxs-lookup"><span data-stu-id="f94af-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="f94af-203">Inserire un nome per il progetto, In questo esempio la chiamata **IoTCRegistry**.</span><span class="sxs-lookup"><span data-stu-id="f94af-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="f94af-204">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="f94af-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f94af-205">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, il provisioning e la gestione, la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="f94af-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="f94af-206">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="f94af-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="f94af-207">Impostare il percorso del servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="f94af-208">Impostare **l'utente amministratore** al **abilitare**.</span><span class="sxs-lookup"><span data-stu-id="f94af-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="f94af-209">Impostare **SKU** al **base**.</span><span class="sxs-lookup"><span data-stu-id="f94af-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="f94af-210">Fare clic su **Create** e attendere che i servizi da creare.</span><span class="sxs-lookup"><span data-stu-id="f94af-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="f94af-211">Una volta che viene visualizzata la notifica che informa della corretta creazione del *registro contenitori*, fare clic su **Vai alla risorsa** essere reindirizzati alla pagina del servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="f94af-212">Nel *registro contenitori* pagina del servizio, fare clic su **chiavi di accesso**.</span><span class="sxs-lookup"><span data-stu-id="f94af-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="f94af-213">Prendere nota (è possibile usare il blocco note) dei parametri seguenti:</span><span class="sxs-lookup"><span data-stu-id="f94af-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="f94af-214">**Login Server**</span><span class="sxs-lookup"><span data-stu-id="f94af-214">**Login Server**</span></span>
    2. <span data-ttu-id="f94af-215">**Nome utente**</span><span class="sxs-lookup"><span data-stu-id="f94af-215">**Username**</span></span>
    3. <span data-ttu-id="f94af-216">**Password**</span><span class="sxs-lookup"><span data-stu-id="f94af-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="f94af-217">Capitolo 3 - il servizio Hub IoT</span><span class="sxs-lookup"><span data-stu-id="f94af-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="f94af-218">A questo punto si verrà avviata la creazione e l'installazione delle **il servizio Hub IoT**.</span><span class="sxs-lookup"><span data-stu-id="f94af-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="f94af-219">Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="f94af-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="f94af-220">Una volta effettuato l'accesso, fare clic su **crea una risorsa** nell'angolo in alto a sinistra e cercare **dell'IoT Hub**, fare clic su **invio**.</span><span class="sxs-lookup"><span data-stu-id="f94af-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![eseguire la ricerca di account di archiviazione](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="f94af-222">La nuova pagina fornirà una descrizione del **account di archiviazione** servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="f94af-223">AT nella parte inferiore sinistra di questo prompt, fare clic sui **Create** pulsante, per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="f94af-225">Dopo avere fatto clic su **Create**, verrà visualizzato un pannello:</span><span class="sxs-lookup"><span data-stu-id="f94af-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="f94af-226">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="f94af-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f94af-227">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, eseguire il provisioning e gestire la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="f94af-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f94af-228">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="f94af-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="f94af-229">Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="f94af-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="f94af-230">Selezionare un'opzione appropriata **posizione** (usare la stessa località in tutti i servizi creati in questo corso).</span><span class="sxs-lookup"><span data-stu-id="f94af-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="f94af-231">Inserire la posizione desiderata **nome** per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="f94af-232">Nella parte inferiore della pagina fare clic su **successiva: Ridimensionamento e scalabilità**.</span><span class="sxs-lookup"><span data-stu-id="f94af-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="f94af-234">In questa pagina, selezionare i **piano tariffario e scalabilità livello** (se questa è la prima istanza di servizio dell'Hub IoT, un livello gratuito deve essere disponibile all'utente).</span><span class="sxs-lookup"><span data-stu-id="f94af-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="f94af-235">Fare clic su **Rivedi e crea**.</span><span class="sxs-lookup"><span data-stu-id="f94af-235">Click on **Review + Create**.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="f94af-237">Rivedere le impostazioni e fare clic su **Create**.</span><span class="sxs-lookup"><span data-stu-id="f94af-237">Review your settings and click on **Create**.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="f94af-239">Una volta che viene visualizzata la notifica che informa della corretta creazione del *IoT Hub* servizio, fare clic su **Vai alla risorsa** essere reindirizzati alla pagina del servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="f94af-241">Pannello laterale a sinistra scorrere per visualizzare *gestione dei dispositivi automatici*, di fare clic su **IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="f94af-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="f94af-243">Nella finestra che viene visualizzato a destra, fare clic su **Aggiungi dispositivo IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="f94af-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="f94af-244">Verrà visualizzato un pannello a destra.</span><span class="sxs-lookup"><span data-stu-id="f94af-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="f94af-245">Nel pannello del nuovo dispositivo forniscono un **ID dispositivo** (un nome di propria scelta).</span><span class="sxs-lookup"><span data-stu-id="f94af-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="f94af-246">Fare quindi clic **salvare**.</span><span class="sxs-lookup"><span data-stu-id="f94af-246">Then, click **Save**.</span></span> <span data-ttu-id="f94af-247">Il *primari* e *chiavi secondarie* auto genererà, se hai **genera automaticamente** selezionata.</span><span class="sxs-lookup"><span data-stu-id="f94af-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="f94af-249">Passerà nuovamente al *dispositivi perimetrali IoT* sezione, in cui verrà elencato il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f94af-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="f94af-250">Fare clic sul nuovo dispositivo (evidenziate in rosso nell'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="f94af-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="f94af-252">Nel *dettagli dispositivo* pagina visualizzata, eseguire una copia della **stringa di connessione** (chiave primaria).</span><span class="sxs-lookup"><span data-stu-id="f94af-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="f94af-254">Tornare al pannello a sinistra e fare clic su *criteri di accesso condiviso*per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="f94af-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="f94af-255">Nella pagina visualizzata, fare clic su **iothubowner**, e verrà visualizzato un pannello a destra della schermata.</span><span class="sxs-lookup"><span data-stu-id="f94af-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="f94af-256">Prendere nota (on il blocco note) del **stringa di connessione** (chiave primaria), per utilizzarli successivamente quando l'impostazione di *stringa di connessione* al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f94af-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="f94af-258">Capitolo 4 - impostazione dell'ambiente di sviluppo</span><span class="sxs-lookup"><span data-stu-id="f94af-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="f94af-259">Per creare e distribuire i moduli per *IoT Hub Edge*, saranno necessari i seguenti componenti installati nel computer di sviluppo che eseguono Windows 10:</span><span class="sxs-lookup"><span data-stu-id="f94af-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="f94af-260">[Docker per Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), verrà chiesto di creare un account per poter scaricare.</span><span class="sxs-lookup"><span data-stu-id="f94af-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="f94af-261">[![scaricare docker per windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="f94af-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f94af-262">Richiede docker *Windows 10 PRO*, *Enterprise 14393*, o *Windows Server 2016 RTM*in modo da eseguire.</span><span class="sxs-lookup"><span data-stu-id="f94af-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="f94af-263">Se si eseguono altre versioni di Windows 10, è possibile provare a installare Docker usando il [casella degli strumenti Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).</span><span class="sxs-lookup"><span data-stu-id="f94af-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="f94af-264">[Python 3.6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="f94af-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="f94af-265">[![scaricare python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="f94af-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="f94af-266">[Visual Studio Code (anche noto come VS Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="f94af-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="f94af-267">[![scaricare Visual Studio Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="f94af-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="f94af-268">Dopo aver installato il software indicato in precedenza, è necessario riavviare il computer.</span><span class="sxs-lookup"><span data-stu-id="f94af-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="f94af-269">Capitolo 5: configurazione dell'ambiente di Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f94af-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="f94af-270">A questo punto è possibile passare alla configurazione del dispositivo **che esegue OS Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="f94af-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="f94af-271">Seguire la procedura seguente per installare il software necessario, per distribuire i contenitori nella bacheca:</span><span class="sxs-lookup"><span data-stu-id="f94af-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f94af-272">È sempre necessario far precedere i comandi di terminali con **sudo** per l'esecuzione come utente amministratore.</span><span class="sxs-lookup"><span data-stu-id="f94af-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="f94af-273">ad esempio:</span><span class="sxs-lookup"><span data-stu-id="f94af-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="f94af-274">Aprire il **Ubuntu Terminal**e usare il comando seguente per installare **pip**:</span><span class="sxs-lookup"><span data-stu-id="f94af-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! HINT]<span data-ttu-id="f94af-275"> è possibile aprire *Terminal* molto facilmente tramite il tasto di scelta rapida: **Ctrl + Alt + T**.</span><span class="sxs-lookup"><span data-stu-id="f94af-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="f94af-276">In questo capitolo, è possibile che venga richiesto, da *Terminal*, l'autorizzazione per l'uso dell'archiviazione del dispositivo e sarà necessario immettere **s/n** (Sì o no), digitare **'y'** e quindi premere i **Invio** chiave, per accettare.</span><span class="sxs-lookup"><span data-stu-id="f94af-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="f94af-277">Al termine di tale comando, usare il comando seguente per installare **curl**:</span><span class="sxs-lookup"><span data-stu-id="f94af-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="f94af-278">Una volta **pip** e **curl** vengono installati, usare il comando seguente per installare il **runtime di IoT Edge**, questa operazione è necessaria per distribuire e controllare i moduli nella bacheca:</span><span class="sxs-lookup"><span data-stu-id="f94af-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="f94af-279">A questo punto verrà richiesto di aprire il *file di configurazione di runtime*, inserire il **Device Connection String**, che si è preso nota (nel blocco note), quando si crea il **servizio Hub IoT**  ([al passaggio 14, capitolo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="f94af-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="f94af-280">Eseguire la riga seguente nel terminale per aprire il file:</span><span class="sxs-lookup"><span data-stu-id="f94af-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="f94af-281">Il **config. yaml** file verranno visualizzati, è possibile modificare:</span><span class="sxs-lookup"><span data-stu-id="f94af-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="f94af-282">Quando si apre questo file, potrebbe essere una certa confusione.</span><span class="sxs-lookup"><span data-stu-id="f94af-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="f94af-283">Si modifica questo file, all'interno del testo di *Terminal* stesso.</span><span class="sxs-lookup"><span data-stu-id="f94af-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="f94af-284">Utilizzare i tasti di direzione sulla tastiera per scorrere verso il basso (è necessario scorrere verso il basso una piccola modo), per raggiungere la riga contenente ":</span><span class="sxs-lookup"><span data-stu-id="f94af-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="f94af-285">" **\<AGGIUNGERE QUI STRINGA DI CONNESSIONE DEL DISPOSITIVO >** ".</span><span class="sxs-lookup"><span data-stu-id="f94af-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="f94af-286">Riga, sostituire **incluse le parentesi**, con la **Device Connection String** annotato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="f94af-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="f94af-287">Con la stringa di connessione posto, sulla tastiera, premere il **Ctrl-X** le chiavi per salvare il file.</span><span class="sxs-lookup"><span data-stu-id="f94af-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="f94af-288">Verrà chiesto di confermare digitando **Y**. Premere quindi il **invio** chiave, per confermare.</span><span class="sxs-lookup"><span data-stu-id="f94af-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="f94af-289">Si passerà nuovamente alla tariffa *Terminal*.</span><span class="sxs-lookup"><span data-stu-id="f94af-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="f94af-290">Una volta che questi comandi hanno tutti eseguiti correttamente, verrà installato il **Runtime di IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="f94af-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="f94af-291">Una volta inizializzato, il runtime verranno avviati con il proprio ogni volta che il dispositivo è acceso e il componente verrà posizionato in background, in attesa per i moduli per la distribuzione dal **il servizio Hub IoT**.</span><span class="sxs-lookup"><span data-stu-id="f94af-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="f94af-292">Eseguire la seguente riga di comando per inizializzare il *Runtime di IoT Edge*:</span><span class="sxs-lookup"><span data-stu-id="f94af-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="f94af-293">Se si apportano modifiche per il file con estensione yaml o la configurazione descritta sopra, dovrai eseguire di nuovo, la riga precedente di riavvio entro *Terminal*.</span><span class="sxs-lookup"><span data-stu-id="f94af-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="f94af-294">Verificare i *Runtime di IoT Edge* lo stato eseguendo la seguente riga di comando.</span><span class="sxs-lookup"><span data-stu-id="f94af-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="f94af-295">Il runtime deve essere visualizzato con stato **attive in esecuzione** nel testo in verde.</span><span class="sxs-lookup"><span data-stu-id="f94af-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="f94af-296">Premere il **Ctrl + C** chiavi, per uscire dalla pagina relativa allo stato.</span><span class="sxs-lookup"><span data-stu-id="f94af-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="f94af-297">È possibile verificare che il *Runtime di IoT Edge* effettua il pull dei contenitori correttamente, digitando il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="f94af-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="f94af-298">Dovrebbe essere visualizzato un elenco con i contenitori di due (2).</span><span class="sxs-lookup"><span data-stu-id="f94af-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="f94af-299">Questi sono i moduli predefiniti vengono creati automaticamente dal servizio Hub IoT (edgeAgent ed edgeHub).</span><span class="sxs-lookup"><span data-stu-id="f94af-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="f94af-300">Quando si creano e distribuiscono i propri moduli, verranno visualizzati nell'elenco, di sotto di quelli predefiniti.</span><span class="sxs-lookup"><span data-stu-id="f94af-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="f94af-301">Capitolo 6: installare le estensioni</span><span class="sxs-lookup"><span data-stu-id="f94af-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f94af-302">I prossimi capitoli descrivono (da 6 a 9) devono essere eseguite nel computer Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f94af-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="f94af-303">Aprire **Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="f94af-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="f94af-304">Fare clic sui **Extensions** pulsante (quadrata) sul sinistro codice a barre di Visual Studio, aprire il **pannello estensioni**.</span><span class="sxs-lookup"><span data-stu-id="f94af-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="f94af-305">Cercare e installare, le estensioni seguenti (come illustrato nell'immagine seguente):</span><span class="sxs-lookup"><span data-stu-id="f94af-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="f94af-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="f94af-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="f94af-307">Azure IoT Toolkit</span><span class="sxs-lookup"><span data-stu-id="f94af-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="f94af-308">Docker</span><span class="sxs-lookup"><span data-stu-id="f94af-308">Docker</span></span>   

    ![Creare il contenitore](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="f94af-310">Una volta le estensioni vengono installate, chiudere e riaprire Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f94af-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="f94af-311">Con Visual Studio Code aprire ancora una volta, passare a **View** > **terminale integrato**.</span><span class="sxs-lookup"><span data-stu-id="f94af-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="f94af-312">A questo punto si installerà **Cookiecutter**.</span><span class="sxs-lookup"><span data-stu-id="f94af-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="f94af-313">Nel terminale eseguire il comando bash seguente:</span><span class="sxs-lookup"><span data-stu-id="f94af-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! HINT]<span data-ttu-id="f94af-314"> Se si riscontrano problemi con questo comando:</span><span class="sxs-lookup"><span data-stu-id="f94af-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="f94af-315">Riavviare Visual Studio Code, e / o nel computer.</span><span class="sxs-lookup"><span data-stu-id="f94af-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="f94af-316">Potrebbe essere necessario passare il **terminale di Visual Studio Code** a quella a cui è stato utilizzato per installare Python, vale a dire **Powershell** (particolarmente nel caso in cui l'ambiente di Python è già stato installato nel computer).</span><span class="sxs-lookup"><span data-stu-id="f94af-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="f94af-317">Aprire il terminale, sono disponibili nell'elenco a discesa dal menu sul lato destro della finestra del terminale.</span><span class="sxs-lookup"><span data-stu-id="f94af-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="f94af-318">![Creare il contenitore](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="f94af-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="f94af-319">Assicurarsi che il **Python** percorso di installazione viene aggiunto come **variabile di ambiente** nel computer.</span><span class="sxs-lookup"><span data-stu-id="f94af-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="f94af-320">Cookiecutter deve far parte di percorso stesso.</span><span class="sxs-lookup"><span data-stu-id="f94af-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="f94af-321">Seguire questa [collegamento per altre informazioni sulle variabili di ambiente](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span><span class="sxs-lookup"><span data-stu-id="f94af-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="f94af-322">Una volta **Cookiecutter** è stato installato, è necessario riavviare il computer, in modo che **Cookiecutter** viene riconosciuto come un comando, nell'ambiente del sistema.</span><span class="sxs-lookup"><span data-stu-id="f94af-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="f94af-323">Capitolo 7 - creare una soluzione contenitori</span><span class="sxs-lookup"><span data-stu-id="f94af-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="f94af-324">A questo punto, è necessario creare il contenitore, il modulo, eseguire il push nel *registro contenitori di*.</span><span class="sxs-lookup"><span data-stu-id="f94af-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="f94af-325">Una volta che si è eseguito il push del contenitore, si userà il *Hub di IoT Edge* servizio distribuirla sul dispositivo, che è in esecuzione il *runtime di IoT Edge*.</span><span class="sxs-lookup"><span data-stu-id="f94af-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="f94af-326">Da Visual Studio Code, fare clic su **View** > **comandi**.</span><span class="sxs-lookup"><span data-stu-id="f94af-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="f94af-327">Nel riquadro di ricerca ed eseguire **Azure IoT Edge: Nuova soluzione Iot Edge**.</span><span class="sxs-lookup"><span data-stu-id="f94af-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="f94af-328">Sfoglia in una posizione in cui si desidera creare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="f94af-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="f94af-329">Premere il **invio** chiave, per accettare il percorso.</span><span class="sxs-lookup"><span data-stu-id="f94af-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="f94af-330">Assegnare un nome per la soluzione.</span><span class="sxs-lookup"><span data-stu-id="f94af-330">Give a name to your solution.</span></span> <span data-ttu-id="f94af-331">Premere il **invio** chiave, per confermare il nome specificato.</span><span class="sxs-lookup"><span data-stu-id="f94af-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="f94af-332">A questo punto verrà chiesto di scegliere il framework di modello per la soluzione.</span><span class="sxs-lookup"><span data-stu-id="f94af-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="f94af-333">Fare clic su **modulo Python**.</span><span class="sxs-lookup"><span data-stu-id="f94af-333">Click **Python Module**.</span></span> <span data-ttu-id="f94af-334">Premere il **invio** chiave, per confermare la scelta.</span><span class="sxs-lookup"><span data-stu-id="f94af-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="f94af-335">Assegnare un nome per il modulo.</span><span class="sxs-lookup"><span data-stu-id="f94af-335">Give a name to your module.</span></span> <span data-ttu-id="f94af-336">Premere il **invio** chiave, per verificare il nome del modulo.</span><span class="sxs-lookup"><span data-stu-id="f94af-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="f94af-337">Assicurarsi di annotare (con il blocco note) il nome del modulo, perché è usato in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="f94af-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="f94af-338">Si noterà una preesistente *Repository di immagini Docker* indirizzo verrà visualizzato nella tavolozza.</span><span class="sxs-lookup"><span data-stu-id="f94af-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="f94af-339">Sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="f94af-339">It will look like:</span></span>

    <span data-ttu-id="f94af-340">**localhost:5000 /, il nome del modulo -** .</span><span class="sxs-lookup"><span data-stu-id="f94af-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="f94af-341">Eliminare **localhost:5000**e nel relativo inserimento sul posto di *registro contenitori* **Login Server** indirizzo, che si è preso nota quando si crea il **contenitore Servizio Registro di sistema** ([nel passaggio 8, capitolo 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="f94af-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="f94af-342">Premere il **invio** chiave, per confermare l'indirizzo.</span><span class="sxs-lookup"><span data-stu-id="f94af-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="f94af-343">A questo punto, verrà creata la soluzione che contiene il modello per il modulo Python e la relativa struttura verrà visualizzata nei **esplorare scheda**, di Visual Studio Code, sul lato sinistro della schermata.</span><span class="sxs-lookup"><span data-stu-id="f94af-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="f94af-344">Se il **esplorare scheda** è non è aperto, è possibile aprirlo facendo clic sul pulsante posizionata più in alto, nella barra a sinistra.</span><span class="sxs-lookup"><span data-stu-id="f94af-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Creare il contenitore](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="f94af-346">L'ultimo passaggio per questo capitolo, deve fare clic e aprire il **file con estensione env**, dall'interno la **scheda Esplora**e aggiungere il *registro contenitori* **username** e **password**.</span><span class="sxs-lookup"><span data-stu-id="f94af-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="f94af-347">Questo file viene ignorato da git, ma sulla compilazione imposterà le credenziali per accedere al contenitore e il **servizio contenitore di registro di sistema**.</span><span class="sxs-lookup"><span data-stu-id="f94af-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Creare il contenitore](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="f94af-349">Capitolo 8 - modifica la soluzione contenitori</span><span class="sxs-lookup"><span data-stu-id="f94af-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="f94af-350">A questo punto si completerà la soluzione contenitore, aggiornando i file seguenti:</span><span class="sxs-lookup"><span data-stu-id="f94af-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="f94af-351">*principali<span></span>py* script python.</span><span class="sxs-lookup"><span data-stu-id="f94af-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="f94af-352">*requirements.txt*.</span><span class="sxs-lookup"><span data-stu-id="f94af-352">*requirements.txt*.</span></span>
- <span data-ttu-id="f94af-353">*deployment.template.json*.</span><span class="sxs-lookup"><span data-stu-id="f94af-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="f94af-354">*Dockerfile.amd64*</span><span class="sxs-lookup"><span data-stu-id="f94af-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="f94af-355">Verrà quindi creato il *immagini* cartella usato dallo script di python per verificare la presenza di immagini in base alla quale confrontare i *modello di visione artificiale personalizzato*.</span><span class="sxs-lookup"><span data-stu-id="f94af-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="f94af-356">Infine, si aggiungerà il *labels.txt* file, per facilitare la lettura del modello e il *model.pb* file, ovvero il modello.</span><span class="sxs-lookup"><span data-stu-id="f94af-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="f94af-357">Con Visual Studio Code aprire, passare alla cartella del modulo e cercare lo script chiamato **principale<span></span>py**.</span><span class="sxs-lookup"><span data-stu-id="f94af-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="f94af-358">Fare doppio clic per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="f94af-358">Double-click to open it.</span></span>

2. <span data-ttu-id="f94af-359">Eliminare il contenuto del file e inserire il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="f94af-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="f94af-360">Aprire il file denominato **Requirements. txt**e sostituire il contenuto con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f94af-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="f94af-361">Aprire il file denominato **deployment.template.json**e sostituire il contenuto seguente le seguenti linee guida:</span><span class="sxs-lookup"><span data-stu-id="f94af-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="f94af-362">Poiché si avrà il proprio, univoca, struttura JSON, è necessario modificarlo manualmente (invece di copiare un esempio).</span><span class="sxs-lookup"><span data-stu-id="f94af-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="f94af-363">Per facilitare questa operazione, usare l'immagine come guida seguente.</span><span class="sxs-lookup"><span data-stu-id="f94af-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="f94af-364">Le aree che avrà un aspetto diverse rispetto a quelle in uso, ma che si **non deve cambiare viene evidenziato in giallo**.</span><span class="sxs-lookup"><span data-stu-id="f94af-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="f94af-365">**Le sezioni che è necessario eliminare, sono una linea rossa evidenziata.**</span><span class="sxs-lookup"><span data-stu-id="f94af-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="f94af-366">Prestare attenzione a eliminare la parentesi corrette e anche rimuovere le virgole.</span><span class="sxs-lookup"><span data-stu-id="f94af-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Creare il contenitore](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="f94af-368">Il codice JSON completato dovrebbe essere simile all'immagine seguente (tuttavia, con le differenze univoche: *riferimenti al nome utente/password/modulo nome/modulo*):</span><span class="sxs-lookup"><span data-stu-id="f94af-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Creare il contenitore](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="f94af-370">Aprire il file denominato **Dockerfile.amd64**e sostituire il contenuto con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f94af-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="f94af-371">Pulsante destro del mouse sulla cartella sotto **moduli** (avrà il nome specificato in precedenza; nell'esempio ulteriormente verso il basso, viene chiamato *pythonmodule*) e fare clic su **nuova cartella**.</span><span class="sxs-lookup"><span data-stu-id="f94af-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="f94af-372">Denominare la cartella **immagini**.</span><span class="sxs-lookup"><span data-stu-id="f94af-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="f94af-373">All'interno della cartella, aggiungere alcune immagini contenenti mouse o tastiera.</span><span class="sxs-lookup"><span data-stu-id="f94af-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="f94af-374">Che saranno le immagini che verranno analizzate dal modello Tensorflow.</span><span class="sxs-lookup"><span data-stu-id="f94af-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="f94af-375">Se si usa un modello personalizzato, è necessario modificare questa impostazione in modo da riflettere i propri dati di modelli.</span><span class="sxs-lookup"><span data-stu-id="f94af-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="f94af-376">A questo punto è necessario recuperare il **labels.txt** e **model.pb** file dalla cartella di modello precedente scaricato (o creato dal proprio **servizio visione artificiale personalizzato** ), in [capitolo 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="f94af-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="f94af-377">Dopo aver creato i file, inserirli all'interno della soluzione, insieme ad altri file.</span><span class="sxs-lookup"><span data-stu-id="f94af-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="f94af-378">Il risultato finale dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="f94af-378">The final result should look like the image below:</span></span>

    ![Creare il contenitore](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="f94af-380">Capitolo 9 - pacchetto della soluzione come un contenitore</span><span class="sxs-lookup"><span data-stu-id="f94af-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="f94af-381">A questo punto si è pronti per "pacchetto" i file come un contenitore ed eseguirne il push per le **registro contenitori di Azure**.</span><span class="sxs-lookup"><span data-stu-id="f94af-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="f94af-382">All'interno di Visual Studio Code, aprire il *terminale integrato* (**View** > **terminale integrato** oppure **Ctrl** + **\`** ) e utilizzare la seguente riga per l'accesso al **Docker** (sostituire i valori del comando con le credenziali del **registro contenitori di Azure (ACR)** ):</span><span class="sxs-lookup"><span data-stu-id="f94af-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="f94af-383">Fare doppio clic sul file **deployment.template.json**, fare clic su **Compila soluzione Edge IoT**.</span><span class="sxs-lookup"><span data-stu-id="f94af-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="f94af-384">Questo processo di compilazione richiede molto tempo (a seconda del dispositivo), quindi sarà necessario attendere.</span><span class="sxs-lookup"><span data-stu-id="f94af-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="f94af-385">Al termine del processo di compilazione, un **Deployment** file viene creato all'interno di una nuova cartella denominata **config**.</span><span class="sxs-lookup"><span data-stu-id="f94af-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![creare una distribuzione](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="f94af-387">Aprire il **riquadro comandi** anche in questo caso e cercare **Azure: Sign In**.</span><span class="sxs-lookup"><span data-stu-id="f94af-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="f94af-388">Seguire le istruzioni usando le credenziali dell'Account di Azure; Visual Studio Code fornirà all'utente un'opzione per *copiare e aprire*, che verrà copiato il codice del dispositivo verrà presto necessarie e quindi aprire il web browser predefinito.</span><span class="sxs-lookup"><span data-stu-id="f94af-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="f94af-389">Quando viene chiesto, incollare il codice del dispositivo, per eseguire l'autenticazione nel computer.</span><span class="sxs-lookup"><span data-stu-id="f94af-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![copia e Apri](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="f94af-391">Una volta firmati in si noterà, sul lato inferiore del *Explore* del pannello, una nuova sezione denominata **dispositivi dell'Hub IoT di Azure**.</span><span class="sxs-lookup"><span data-stu-id="f94af-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="f94af-392">Fare clic su questa sezione per espanderla.</span><span class="sxs-lookup"><span data-stu-id="f94af-392">Click this section to expand it.</span></span>

    ![dispositivo Edge](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="f94af-394">Se il dispositivo non è in questo caso, sarà necessario fare doppio clic su *dispositivi dell'Hub IoT di Azure*, quindi fare clic su **Set IoT Hub Connection String**.</span><span class="sxs-lookup"><span data-stu-id="f94af-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="f94af-395">Si noterà quindi che il **riquadro comandi** (nella parte superiore di Visual Studio Code), verrà richiesto di immettere il *stringa di connessione*.</span><span class="sxs-lookup"><span data-stu-id="f94af-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="f94af-396">Questo è il *stringa di connessione* si è preso nota alla fine del [capitolo 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="f94af-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="f94af-397">Premere il **invio** della chiave, dopo aver copiato la stringa.</span><span class="sxs-lookup"><span data-stu-id="f94af-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="f94af-398">Il dispositivo deve caricare e vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="f94af-398">Your device should load, and appear.</span></span> <span data-ttu-id="f94af-399">Fare doppio clic sul nome del dispositivo e quindi scegliere **creare la distribuzione per singolo dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="f94af-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![creare una distribuzione](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="f94af-401">Si otterrà un *Esplora File* prompt dei comandi, in cui è possibile passare alle **config** cartella e quindi selezionare il **Deployment** file.</span><span class="sxs-lookup"><span data-stu-id="f94af-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="f94af-402">Con tale file selezionato, scegliere il **selezionare manifesto della distribuzione Edge** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f94af-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![creare una distribuzione](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="f94af-404">A questo punto è stato specificato il **il servizio Hub IoT** con il manifesto per poter distribuire il contenitore, come un modulo, dalle **registro contenitori di Azure**, in modo efficace distribuirla nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f94af-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="f94af-405">Per visualizzare i messaggi inviati dal dispositivo all'IoT Hub, fare clic nuovamente sul nome del dispositivo nel **dispositivi dell'Hub IoT di Azure** nella sezione la **Explorer** pannello e fare clic su **inizia il monitoraggio Messaggi D2C**.</span><span class="sxs-lookup"><span data-stu-id="f94af-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="f94af-406">I messaggi inviati dal dispositivo verrà visualizzato nel terminale di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f94af-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="f94af-407">Essere paziente, in quanto l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="f94af-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="f94af-408">Vedere il capitolo successivo per il debug e verifica se la distribuzione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="f94af-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="f94af-409">Questo modulo verrà ora eseguire l'iterazione tra le immagini nel **immagini** cartelle e analizzarli, con ogni iterazione.</span><span class="sxs-lookup"><span data-stu-id="f94af-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="f94af-410">Questo è ovviamente solo una dimostrazione di come ottenere il modello di base di machine learning per lavorare in un ambiente del dispositivo IoT Edge.</span><span class="sxs-lookup"><span data-stu-id="f94af-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="f94af-411">Per espandere la funzionalità di questo esempio, è possibile procedere in diversi modi.</span><span class="sxs-lookup"><span data-stu-id="f94af-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="f94af-412">Uno dei modi potrebbe essere inclusi codice nel contenitore, che consente di acquisire foto da webcam che è connesso al dispositivo e Salva le immagini nella cartella delle immagini.</span><span class="sxs-lookup"><span data-stu-id="f94af-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="f94af-413">Un altro modo possibile copiare le immagini dal dispositivo IoT nel contenitore.</span><span class="sxs-lookup"><span data-stu-id="f94af-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="f94af-414">Un modo pratico per farlo consiste nell'eseguire il comando seguente nel dispositivo IoT terminale (forse una piccola app è stato possibile eseguire il processo, se si vuole automatizzare il processo).</span><span class="sxs-lookup"><span data-stu-id="f94af-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="f94af-415">È possibile testare questo comando, eseguire manualmente dal percorso di cartella in cui sono archiviati i file:</span><span class="sxs-lookup"><span data-stu-id="f94af-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="f94af-416">Capitolo 10 - debug Runtime di IoT Edge</span><span class="sxs-lookup"><span data-stu-id="f94af-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="f94af-417">Di seguito sono un elenco di righe di comando e suggerimenti, che consentono di monitorare ed eseguire il debug dell'attività di messaggistica la *Runtime di IoT Edge*, dalle **dispositivo Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="f94af-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="f94af-418">Verificare i *Runtime di IoT Edge* lo stato eseguendo la seguente riga di comando:</span><span class="sxs-lookup"><span data-stu-id="f94af-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="f94af-419">Tenere presente premere **Ctrl + C**per portare a termine visualizzando lo stato.</span><span class="sxs-lookup"><span data-stu-id="f94af-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="f94af-420">Elencare i contenitori che sono attualmente distribuiti.</span><span class="sxs-lookup"><span data-stu-id="f94af-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="f94af-421">Se il *il servizio Hub IoT* sia distribuito correttamente, i contenitori saranno visualizzati eseguendo la seguente riga di comando:</span><span class="sxs-lookup"><span data-stu-id="f94af-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="f94af-422">Oppure</span><span class="sxs-lookup"><span data-stu-id="f94af-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="f94af-423">Il codice precedente è un buon metodo per verificare se il modulo è stato distribuito correttamente, come verrà visualizzato nell'elenco. in caso contrario, verranno **soltanto** vedere la *edgeHub* e *edgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="f94af-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="f94af-424">Per visualizzare i log di codice di un contenitore, eseguire la seguente riga di comando:</span><span class="sxs-lookup"><span data-stu-id="f94af-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="f94af-425">**Comandi utili per gestire il Runtime di IoT Edge:**</span><span class="sxs-lookup"><span data-stu-id="f94af-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="f94af-426">Per eliminare tutti i contenitori nell'host:</span><span class="sxs-lookup"><span data-stu-id="f94af-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="f94af-427">Per arrestare il *Runtime di IoT Edge*:</span><span class="sxs-lookup"><span data-stu-id="f94af-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="f94af-428">Capitolo 11 - Creazione del servizio tabelle</span><span class="sxs-lookup"><span data-stu-id="f94af-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="f94af-429">Passare al portale di Azure, in cui verrà creato un servizio di tabelle di Azure, tramite la creazione di una risorsa di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="f94af-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="f94af-430">Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="f94af-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="f94af-431">Una volta effettuato l'accesso, fare clic su **crea una risorsa**in alto a sinistra angolo e cercare **account di archiviazione**, premere il **invio** chiave, per avviare la ricerca.</span><span class="sxs-lookup"><span data-stu-id="f94af-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="f94af-432">Dopo che è stato incluso, fare clic su **account di archiviazione: blob, file, tabella, coda** dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="f94af-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![eseguire la ricerca di account di archiviazione](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="f94af-434">La nuova pagina fornirà una descrizione del **account di archiviazione** servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="f94af-435">AT nella parte inferiore sinistra di questo prompt, fare clic sui **Create** pulsante, per creare un'istanza di questo servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![creare l'istanza di archiviazione](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="f94af-437">Dopo avere fatto clic su **Create**, verrà visualizzato un pannello:</span><span class="sxs-lookup"><span data-stu-id="f94af-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="f94af-438">Inserire la posizione desiderata **Name** per questa istanza del servizio (*deve contenere solo lettere minuscole*).</span><span class="sxs-lookup"><span data-stu-id="f94af-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="f94af-439">Per la **modello di distribuzione**, fare clic su **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="f94af-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="f94af-440">Per la **tipologia Account**, usando il menu a discesa, fare clic su **archiviazione (utilizzo generico v1)** .</span><span class="sxs-lookup"><span data-stu-id="f94af-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="f94af-441">Fare clic su un oggetto appropriato **posizione**.</span><span class="sxs-lookup"><span data-stu-id="f94af-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="f94af-442">Per il **replica** dal menu a discesa, fare clic su **Read-access-archiviazione geograficamente ridondante (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="f94af-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="f94af-443">Per la **Performance**, fare clic su **Standard**.</span><span class="sxs-lookup"><span data-stu-id="f94af-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="f94af-444">All'interno di **trasferimento sicuro obbligatorio** fare clic su **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="f94af-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="f94af-445">Dal **sottoscrizione** menu a discesa, fare clic su una sottoscrizione appropriata.</span><span class="sxs-lookup"><span data-stu-id="f94af-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="f94af-446">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="f94af-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f94af-447">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, il provisioning e la gestione, la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="f94af-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="f94af-448">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="f94af-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="f94af-449">Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="f94af-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="f94af-450">Lasciare **reti virtuali** come **disabilitato**, se si tratta di un'opzione per l'utente.</span><span class="sxs-lookup"><span data-stu-id="f94af-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="f94af-451">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="f94af-451">Click **Create**.</span></span>

        ![Compilandone i dettagli di archiviazione](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="f94af-453">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="f94af-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="f94af-454">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="f94af-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="f94af-455">Fare clic su notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-455">Click on the notifications to explore your new Service instance.</span></span>

    ![nuova notifica di archiviazione](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="f94af-457">Scegliere il **Vai alla risorsa** pulsante nella notifica e verrà visualizzato la nuova pagina di panoramica di istanza del servizio di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="f94af-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![Vai alla risorsa](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="f94af-459">Dalla pagina di panoramica, per il lato destro, fare clic su **tabelle**.</span><span class="sxs-lookup"><span data-stu-id="f94af-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![Tabelle](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="f94af-461">Il pannello sulla destra cambierà e indicherà il **servizio tabelle** informazioni, in cui è necessario aggiungere una nuova tabella.</span><span class="sxs-lookup"><span data-stu-id="f94af-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="f94af-462">Eseguire questa operazione facendo il **+ tabella** pulsante nell'angolo superiore sinistro.</span><span class="sxs-lookup"><span data-stu-id="f94af-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![Aprire le tabelle](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="f94af-464">Verrà visualizzata una nuova pagina, in cui è necessario immettere un **nome della tabella**.</span><span class="sxs-lookup"><span data-stu-id="f94af-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="f94af-465">Questo è il nome che verrà utilizzato per fare riferimento ai dati nell'applicazione nei capitoli successivi (creazione di App per le funzioni e Power BI).</span><span class="sxs-lookup"><span data-stu-id="f94af-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="f94af-466">Inserire **IoTMessages** come nome (è possibile scegliere il proprio, è importante ricordare che quando usato più avanti in questo documento) e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f94af-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="f94af-467">Dopo aver creata la nuova tabella, sarà possibile visualizzarlo all'interno di **servizio tabelle** (inferiore) della pagina.</span><span class="sxs-lookup"><span data-stu-id="f94af-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![nuova tabella creata](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="f94af-469">Fare clic su **chiavi di accesso** e richiedere una copia del **nome account di archiviazione** e **chiave** (usando il blocco note), si userà questi valori più avanti in questo corso, quando si crea il **App per le funzioni di azure**.</span><span class="sxs-lookup"><span data-stu-id="f94af-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![nuova tabella creata](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="f94af-471">Usando il pannello a sinistra, scorrere fino al *servizio tabelle* sezione e fare clic su **tabelle** (o **Sfoglia tabelle**, nei portali più recente) e richiedere una copia il  **URL di tabella** (usando il blocco note).</span><span class="sxs-lookup"><span data-stu-id="f94af-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="f94af-472">Si userà questo valore più avanti in questo corso, quando si collegano la tabella per il **Power BI** dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f94af-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![nuova tabella creata](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="f94af-474">Capitolo 12 - tabella di Azure di completamento</span><span class="sxs-lookup"><span data-stu-id="f94af-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="f94af-475">Ora che il **servizio tabelle** account di archiviazione è stata configurata, è possibile aggiungere dati a esso, che verrà usato per archiviare e recuperare informazioni.</span><span class="sxs-lookup"><span data-stu-id="f94af-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="f94af-476">La modifica delle tabelle può essere eseguita tramite **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f94af-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="f94af-477">Aprire **Visual Studio** (**non** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="f94af-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="f94af-478">Dal menu, fare clic su **View** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="f94af-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Aprire cloud explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="f94af-480">Il **Cloud Explorer** verranno aperte come un elemento ancoraggio (essere paziente, come il caricamento potrebbe richiedere tempo).</span><span class="sxs-lookup"><span data-stu-id="f94af-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="f94af-481">Se la sottoscrizione è stata usata per creare le *gli account di archiviazione* non è visibile, assicurarsi di avere:</span><span class="sxs-lookup"><span data-stu-id="f94af-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="f94af-482">Per lo stesso account come quello usato per il portale di Azure connesso.</span><span class="sxs-lookup"><span data-stu-id="f94af-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="f94af-483">Selezionare la sottoscrizione dalla pagina di gestione di Account (potrebbe essere necessario applicare un filtro da impostazioni dell'account):</span><span class="sxs-lookup"><span data-stu-id="f94af-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![trovare la sottoscrizione](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="f94af-485">Verranno visualizzati i servizi cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="f94af-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="f94af-486">Trovare **gli account di archiviazione** e fare clic sulla freccia a sinistra di tale per espandere l'account.</span><span class="sxs-lookup"><span data-stu-id="f94af-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Aprire l'account di archiviazione](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="f94af-488">Una volta espanso, appena creato **account di archiviazione** devono essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="f94af-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="f94af-489">Fare clic sulla freccia a sinistra della risorsa di archiviazione e quindi una volta che viene espanso, individuare **tabelle** e fare clic sulla freccia accanto a cui, per visualizzare i **tabella** creato nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="f94af-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="f94af-490">Fare doppio clic sui **tabella**.</span><span class="sxs-lookup"><span data-stu-id="f94af-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="f94af-491">La tabella verrà aperta al centro della finestra di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f94af-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="f94af-492">Fare clic sull'icona di tabella con il **+** (più) su di esso.</span><span class="sxs-lookup"><span data-stu-id="f94af-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![Aggiungi nuova tabella](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="f94af-494">Verrà visualizzata richiede una finestra per poter *Aggiungi entità*.</span><span class="sxs-lookup"><span data-stu-id="f94af-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="f94af-495">Verrà creata solo un'entità, anche se hanno tre proprietà.</span><span class="sxs-lookup"><span data-stu-id="f94af-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="f94af-496">Si noterà che *PartitionKey* e *RowKey* già disponibili, poiché verranno usati per trovare i dati dalla tabella.</span><span class="sxs-lookup"><span data-stu-id="f94af-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![chiave di partizione e di riga](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="f94af-498">Aggiornare i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="f94af-498">Update the following values:</span></span>

    - <span data-ttu-id="f94af-499">Nome: **PartitionKey**, Value: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="f94af-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="f94af-500">Nome: **RowKey**, valore: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="f94af-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="f94af-501">Quindi, fare clic su **Aggiungi proprietà** (in basso a sinistra del *Aggiungi entità* finestra) e aggiungere la proprietà seguente:</span><span class="sxs-lookup"><span data-stu-id="f94af-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="f94af-502">**L'elemento MessageContent**, come un *stringa*, lasciare vuoto il valore.</span><span class="sxs-lookup"><span data-stu-id="f94af-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="f94af-503">La tabella deve corrispondere a quello nell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="f94af-503">Your table should match the one in the image below:</span></span>

    ![aggiungere i valori corretti](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="f94af-505">Il motivo per cui l'entità contiene il numero 1 nella chiave di riga, è perché si potrebbe voler aggiungere altri messaggi, si necessita di sperimentare ulteriormente con questo corso.</span><span class="sxs-lookup"><span data-stu-id="f94af-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="f94af-506">Fare clic su **OK** al termine.</span><span class="sxs-lookup"><span data-stu-id="f94af-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="f94af-507">La tabella è ora pronta per essere usato.</span><span class="sxs-lookup"><span data-stu-id="f94af-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="f94af-508">Capitolo 13 - creare un'App per le funzioni di Azure</span><span class="sxs-lookup"><span data-stu-id="f94af-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="f94af-509">È ora possibile creare un *App per le funzioni*, che verrà chiamato dal *servizio Hub IoT* per archiviare il *IoT Edge* dispositivo i messaggi nel **tabella** Servizio che è stato creato nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="f94af-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="f94af-510">In primo luogo, è necessario creare un file che consentirà la funzione di Azure caricare le librerie che necessarie.</span><span class="sxs-lookup"><span data-stu-id="f94af-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="f94af-511">Open **Notepad** (premere il *chiave di Windows*e il tipo *blocco note*).</span><span class="sxs-lookup"><span data-stu-id="f94af-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![Aprire Blocco note](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="f94af-513">Aprire Blocco note, inserire la struttura JSON seguente al suo interno.</span><span class="sxs-lookup"><span data-stu-id="f94af-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="f94af-514">Una volta che è stato fatto che, salvarlo sul desktop come **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="f94af-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="f94af-515">Questo file definisce le librerie che userà la funzione.</span><span class="sxs-lookup"><span data-stu-id="f94af-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="f94af-516">Se si usa NuGet, avrà un aspetto familiare.</span><span class="sxs-lookup"><span data-stu-id="f94af-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="f94af-517">È importante che la denominazione sia corretta. Verificare che avviene **non è un file con estensione txt** estensione di file.</span><span class="sxs-lookup"><span data-stu-id="f94af-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="f94af-518">Per riferimento, vedere di seguito:</span><span class="sxs-lookup"><span data-stu-id="f94af-518">See below for reference:</span></span>
    >
    > ![Salvataggio JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="f94af-520">Accedi per il [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="f94af-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="f94af-521">Una volta connessi, fare clic su **crea una risorsa** nell'angolo in alto a sinistra e cercare **App per le funzioni**, premere il **invio** chiave, eseguire la ricerca.</span><span class="sxs-lookup"><span data-stu-id="f94af-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="f94af-522">Fare clic su *App per le funzioni* dai risultati, aprire un nuovo pannello.</span><span class="sxs-lookup"><span data-stu-id="f94af-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![cercare app per le funzioni](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="f94af-524">Nel nuovo pannello fornirà una descrizione del **App per le funzioni** servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="f94af-525">AT nella parte inferiore sinistra del pannello, fare clic sui **Create** pulsante, per creare un'associazione con questo servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![istanza dell'app (funzione)](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="f94af-527">Dopo avere fatto clic su **Create**, compilare i campi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f94af-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="f94af-528">Per la **nome App**, inserire il nome desiderato per questa istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="f94af-529">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="f94af-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="f94af-530">Selezionare il piano tariffario appropriato per l'utente, se questa è la prima volta che la creazione di un **servizio App di funzione**, un livello gratuito deve essere disponibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="f94af-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="f94af-531">Scegliere una **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="f94af-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f94af-532">Un gruppo di risorse offre un modo per monitorare, controllare l'accesso, il provisioning e la gestione, la fatturazione per una raccolta delle risorse di Azure.</span><span class="sxs-lookup"><span data-stu-id="f94af-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="f94af-533">È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, ad esempio, i corsi) in un gruppo di risorse comuni).</span><span class="sxs-lookup"><span data-stu-id="f94af-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="f94af-534">Per altre informazioni sui gruppi di risorse di Azure, seguire questa [collegamento su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="f94af-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="f94af-535">Per la **OS**, fare clic su Windows, che è la piattaforma desiderata.</span><span class="sxs-lookup"><span data-stu-id="f94af-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="f94af-536">Selezionare una **piano di Hosting** (questa esercitazione Usa un **piano a consumo**.</span><span class="sxs-lookup"><span data-stu-id="f94af-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="f94af-537">Selezionare una **posizione** (scegliere la stessa ubicazione come risorsa di archiviazione che hanno creato nel passaggio precedente)</span><span class="sxs-lookup"><span data-stu-id="f94af-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="f94af-538">Per il **memorizzazione** sezione **è necessario selezionare il servizio di archiviazione creato nel passaggio precedente**.</span><span class="sxs-lookup"><span data-stu-id="f94af-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="f94af-539">Non è necessario *Application Insights* in questa app, è possibile lasciarlo **Off**.</span><span class="sxs-lookup"><span data-stu-id="f94af-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="f94af-540">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="f94af-540">Click **Create**.</span></span>

        ![creare una nuova istanza](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="f94af-542">Dopo avere fatto clic su **Create**, sarà necessario attendere che il servizio deve essere creato, l'operazione potrebbe richiedere qualche minuto.</span><span class="sxs-lookup"><span data-stu-id="f94af-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="f94af-543">Dopo aver creata l'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="f94af-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![nuova notifica](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="f94af-545">Fare clic sulla notifica, dopo la distribuzione ha esito positivo (terminata).</span><span class="sxs-lookup"><span data-stu-id="f94af-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="f94af-546">Scegliere il **Vai alla risorsa** pulsante della notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="f94af-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Vai alla risorsa](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="f94af-548">Sul lato sinistro del pannello nuovo, fare clic sui **+** (più) icona accanto a *funzioni*, per creare una nuova funzione.</span><span class="sxs-lookup"><span data-stu-id="f94af-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Aggiungi nuova funzione](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="f94af-550">All'interno del pannello centrale, il **funzione** verrà visualizzata la finestra di creazione.</span><span class="sxs-lookup"><span data-stu-id="f94af-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="f94af-551">Scorrere ulteriormente verso il basso e fare clic su **funzione personalizzata**.</span><span class="sxs-lookup"><span data-stu-id="f94af-551">Scroll down further, and click on **Custom function**.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="f94af-553">Scorrere verso il basso la pagina successiva, fino a individuare **IoT Hub (Hub eventi)** , quindi fare clic su di esso.</span><span class="sxs-lookup"><span data-stu-id="f94af-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="f94af-555">Nel **IoT Hub (Hub eventi)** blade, impostare il **Language** a **C#** e quindi fare clic su **nuovo**.</span><span class="sxs-lookup"><span data-stu-id="f94af-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="f94af-557">Nella finestra che verrà visualizzato, verificare che **IoT Hub** sia selezionata e il nome del *dell'IoT Hub* campo corrisponde con il nome del *servizio Hub IoT* che è necessario creato in precedenza ([nel passaggio 8, capitolo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="f94af-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="f94af-558">Scegliere il **seleziona** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f94af-558">Then click the **Select** button.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="f94af-560">Nella **IoT Hub (Hub eventi)** pannello, fare clic su **crea**.</span><span class="sxs-lookup"><span data-stu-id="f94af-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="f94af-562">Si verrà reindirizzati all'editor di funzione.</span><span class="sxs-lookup"><span data-stu-id="f94af-562">You will be redirected to the function editor.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="f94af-564">Eliminare tutto il codice in esso e sostituirlo con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="f94af-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="f94af-565">Modificare le variabili seguenti, in modo che corrispondano ai valori appropriati (**tabella** e **archiviazione** valori, da [passaggio 11 e 13, rispettivamente, del capitolo 11](#chapter-11---create-table-service)), che si trovano nel **Account di archiviazione**:</span><span class="sxs-lookup"><span data-stu-id="f94af-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="f94af-566">**tableName**, con il nome del **tabella** che si trova nel **Account di archiviazione**.</span><span class="sxs-lookup"><span data-stu-id="f94af-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="f94af-567">**tableURL**, con l'URL del **tabella** che si trova nel **Account di archiviazione**.</span><span class="sxs-lookup"><span data-stu-id="f94af-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="f94af-568">**storageAccountName**, con il nome del corrispondente con il nome del valore di **Account di archiviazione** nome.</span><span class="sxs-lookup"><span data-stu-id="f94af-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="f94af-569">**storageAccountKey**, con la chiave ottenuta nel servizio di archiviazione creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="f94af-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="f94af-571">Con il codice, fare clic su **salvare**.</span><span class="sxs-lookup"><span data-stu-id="f94af-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="f94af-572">Successivamente, fare clic il **\<** icona (freccia), sul lato destro della pagina.</span><span class="sxs-lookup"><span data-stu-id="f94af-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="f94af-574">Un pannello verrà diapositiva da destra.</span><span class="sxs-lookup"><span data-stu-id="f94af-574">A panel will slide in from the right.</span></span> <span data-ttu-id="f94af-575">In questo pannello, fare clic su **caricare**e una *Browser File* verranno visualizzati.</span><span class="sxs-lookup"><span data-stu-id="f94af-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="f94af-576">Passare a e quindi, il **Project. JSON** file, che è stato creato in **blocco note** in precedenza e quindi fare clic sui **Open** pulsante.</span><span class="sxs-lookup"><span data-stu-id="f94af-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="f94af-577">Questo file definisce le librerie che userà la funzione.</span><span class="sxs-lookup"><span data-stu-id="f94af-577">This file defines the libraries that your function will use.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="f94af-579">Quando il file è stato caricato, verrà visualizzato nel pannello a destra.</span><span class="sxs-lookup"><span data-stu-id="f94af-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="f94af-580">Clic su di esso verrà aperta all'interno di **funzione** editor.</span><span class="sxs-lookup"><span data-stu-id="f94af-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="f94af-581">È necessario ottenere **esattamente** quello utilizzato per l'immagine successiva.</span><span class="sxs-lookup"><span data-stu-id="f94af-581">It must look **exactly** the same as the next image.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="f94af-583">A questo punto può essere opportuno testare la funzionalità della funzione per memorizzare il messaggio nel *tabella*.</span><span class="sxs-lookup"><span data-stu-id="f94af-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="f94af-584">In alto a destra della finestra, fare clic su **Test**.</span><span class="sxs-lookup"><span data-stu-id="f94af-584">On the top right side of the window, click on **Test**.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="f94af-586">Inserire un messaggio sul **corpo della richiesta**, come illustrato nell'immagine precedente e fare clic su **eseguire**.</span><span class="sxs-lookup"><span data-stu-id="f94af-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="f94af-587">Verrà eseguita la funzione, visualizzare lo stato dei risultati (si noterà verde **lo stato 202-accettato**sopra il *Output* finestra, il che significa è stata una chiamata riuscita):</span><span class="sxs-lookup"><span data-stu-id="f94af-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![risultato dell'output](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="f94af-589">Capitolo 14 - visualizzare i messaggi attivi</span><span class="sxs-lookup"><span data-stu-id="f94af-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="f94af-590">Se si apre ora Visual Studio (**non** Visual Studio Code), è possibile visualizzare il risultato messaggio di test, come verrà archiviato nel *l'elemento MessageContent* stringa area.</span><span class="sxs-lookup"><span data-stu-id="f94af-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![funzione personalizzata](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="f94af-592">Con il servizio tabelle e l'App per le funzioni posto, i messaggi da dispositivo Ubuntu saranno visualizzato nei *IoTMessages* tabella.</span><span class="sxs-lookup"><span data-stu-id="f94af-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="f94af-593">Se non è già in esecuzione, avviare nuovamente il dispositivo e sarà possibile visualizzare i messaggi risultati dal dispositivo e modulo, all'interno della tabella, usando Visual Studio *Cloud Explorer*.</span><span class="sxs-lookup"><span data-stu-id="f94af-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Visualizzare i dati](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="f94af-595">Capitolo 15 - il programma di installazione di Power BI</span><span class="sxs-lookup"><span data-stu-id="f94af-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="f94af-596">Per visualizzare i dati dal dispositivo IOT configurerà **Power BI** (versione desktop), per raccogliere i dati dalle *tabella* servizio, che appena creato.</span><span class="sxs-lookup"><span data-stu-id="f94af-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="f94af-597">Il *HoloLens* versione di Power BI userà quindi tali dati per visualizzare il risultato.</span><span class="sxs-lookup"><span data-stu-id="f94af-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="f94af-598">Aprire il Microsoft Store in Windows 10 e cercare **Power BI Desktop**.</span><span class="sxs-lookup"><span data-stu-id="f94af-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="f94af-600">Scaricare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f94af-600">Download the application.</span></span> <span data-ttu-id="f94af-601">Dopo aver terminato il download, è necessario aprirlo.</span><span class="sxs-lookup"><span data-stu-id="f94af-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="f94af-602">Accedere al *Power BI* con il **account di Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="f94af-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="f94af-603">Potrebbe essere reindirizzato a un browser, effettuare l'iscrizione.</span><span class="sxs-lookup"><span data-stu-id="f94af-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="f94af-604">Una volta che si sono iscritti, tornare all'app Power BI e accedere di nuovo.</span><span class="sxs-lookup"><span data-stu-id="f94af-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="f94af-605">Fare clic su **recupera dati** e quindi fare clic su **più...** .</span><span class="sxs-lookup"><span data-stu-id="f94af-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="f94af-607">Fare clic su **Azure**, **archiviazione tabelle di Azure**, quindi fare clic su **Connect**.</span><span class="sxs-lookup"><span data-stu-id="f94af-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="f94af-609">Verrà richiesto di inserire le **adresa URL Tabulky** che sono stati raccolti in precedenza ([nel passaggio 13 del capitolo 11](#chapter-11---create-table-service)), durante la creazione di un servizio tabelle.</span><span class="sxs-lookup"><span data-stu-id="f94af-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="f94af-610">Dopo aver inserito l'URL, eliminare la parte del percorso che fa riferimento alla tabella "sottocartella" (che era IoTMessages, in questo corso).</span><span class="sxs-lookup"><span data-stu-id="f94af-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="f94af-611">Il risultato finale dovrebbe essere visualizzato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="f94af-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="f94af-612">Quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f94af-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="f94af-614">Verrà richiesto di inserire le **chiave di archiviazione** annotato ([nel passaggio 11 di 11 capitolo](#chapter-11---create-table-service)) precedenti durante la creazione nell'archiviazione tabelle.</span><span class="sxs-lookup"><span data-stu-id="f94af-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="f94af-615">Quindi fare clic su **Connect**.</span><span class="sxs-lookup"><span data-stu-id="f94af-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="f94af-617">Oggetto **pannello Navigatore** verrà visualizzata, selezionare la casella accanto alla tabella e fare clic su **carico**.</span><span class="sxs-lookup"><span data-stu-id="f94af-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="f94af-619">La tabella è stata caricata in Power BI, ma richiede una query per visualizzare i valori in esso.</span><span class="sxs-lookup"><span data-stu-id="f94af-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="f94af-620">A tale scopo, fare doppio clic sul nome della tabella che si trova nel **pannello campi** sul lato destro dello schermo.</span><span class="sxs-lookup"><span data-stu-id="f94af-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="f94af-621">Quindi fare clic su **modifica Query**.</span><span class="sxs-lookup"><span data-stu-id="f94af-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="f94af-623">Oggetto **Editor di Power Query** , verrà visualizzato come una nuova finestra di visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="f94af-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="f94af-624">Fare clic sulla parola **Record** all'interno di *contenuto* colonna della tabella, per visualizzare il contenuto archiviato.</span><span class="sxs-lookup"><span data-stu-id="f94af-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="f94af-626">Fare clic su **Into Table**, in alto a sinistra della finestra.</span><span class="sxs-lookup"><span data-stu-id="f94af-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="f94af-628">Fare clic su **Chiudi e applica**.</span><span class="sxs-lookup"><span data-stu-id="f94af-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="f94af-630">Una volta completato il caricamento della query, all'interno di **pannello campi**, sul lato destro della schermata, selezionare le caselle corrispondenti ai parametri **Name** e **valore**, a visualizzare il **l'elemento MessageContent** il contenuto della colonna.</span><span class="sxs-lookup"><span data-stu-id="f94af-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="f94af-632">Fare clic sui **icona del disco blu** nella parte superiore sinistra della finestra per salvare il lavoro in una cartella di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="f94af-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="f94af-634">È ora possibile fare clic sul pulsante pubblica per caricare la tabella nell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="f94af-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="f94af-635">Quando richiesto, fare clic su **area di lavoro personale** e fare clic su *seleziona*.</span><span class="sxs-lookup"><span data-stu-id="f94af-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="f94af-636">Attendere che venga visualizzato il risultato positivo dell'invio.</span><span class="sxs-lookup"><span data-stu-id="f94af-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="f94af-639">Nel capitolo successivo è HoloLens specifico.</span><span class="sxs-lookup"><span data-stu-id="f94af-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="f94af-640">Power BI non è attualmente disponibile come applicazione coinvolgente, tuttavia, è possibile eseguire la versione desktop nel portale di realtà mista Windows (noto anche come Cliff House), tramite l'app Desktop.</span><span class="sxs-lookup"><span data-stu-id="f94af-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="f94af-641">Capitolo 16 - i dati di Power BI Visualizza su HoloLens</span><span class="sxs-lookup"><span data-stu-id="f94af-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="f94af-642">Nella finestra di HoloLens, accedere al **Microsoft Store**, toccando la relativa icona nell'elenco delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="f94af-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="f94af-644">Eseguire la ricerca e quindi scaricare il **Power BI** dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f94af-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="f94af-646">Avviare **Power BI** dall'elenco delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="f94af-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="f94af-647">**Power BI** potrebbe venire richiesto di eseguire l'accesso per il **account di Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="f94af-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="f94af-648">Una volta all'interno dell'app, l'area di lavoro dovrebbe essere visualizzata per impostazione predefinita come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="f94af-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="f94af-649">Se che ciò non accada, è sufficiente fare clic sull'icona dell'area di lavoro sul lato sinistro della finestra.</span><span class="sxs-lookup"><span data-stu-id="f94af-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="f94af-651">Il termine applicazione dell'IoT Hub</span><span class="sxs-lookup"><span data-stu-id="f94af-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="f94af-652">Complimenti, è stato creato un servizio di Hub IoT, con un dispositivo simulato Edge di macchina virtuale.</span><span class="sxs-lookup"><span data-stu-id="f94af-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="f94af-653">Il dispositivo può comunicare i risultati di un modello di machine learning per un servizio, tabelle di Azure fornita da un'App di funzione di Azure, che viene letto in Power BI e visualizzati all'interno di un Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f94af-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f94af-655">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="f94af-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f94af-656">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="f94af-656">Exercise 1</span></span>

<span data-ttu-id="f94af-657">Espandere la struttura di messaggistica archiviata nella tabella e la visualizza sotto forma di grafico.</span><span class="sxs-lookup"><span data-stu-id="f94af-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="f94af-658">È possibile raccogliere più dati e archiviarlo nella stessa tabella, deve essere visualizzato in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="f94af-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="f94af-659">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="f94af-659">Exercise 2</span></span>

<span data-ttu-id="f94af-660">Creare un altro modulo "acquisizione con fotocamera" da distribuire nella bacheca IoT, in modo che consente di acquisire immagini tramite la fotocamera da analizzare.</span><span class="sxs-lookup"><span data-stu-id="f94af-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
