---
title: MR e Azure 313-servizio hub Internet
description: Completare questo corso per apprendere come implementare il servizio Hub Azure Internet in una macchina virtuale che esegue Ubuntu 16,4 e quindi visualizzare i dati del messaggio usando Microsoft HoloLens o un auricolare immersivo (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, realtà mista, Academy, Edge, Internet delle cose, esercitazione, API, notifiche, funzioni, tabelle, hololens, immersive, VR, Internet delle cose, macchina virtuale, Ubuntu, Python
ms.openlocfilehash: bfb1518869892ed4899019d7b9c504a960e7db3f
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926840"
---
>[!NOTE]
><span data-ttu-id="79b13-104">Le esercitazioni miste di reality Academy sono state progettate con i HoloLens (1st Gen) e gli auricolari immersivi a realtà mista.</span><span class="sxs-lookup"><span data-stu-id="79b13-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="79b13-105">Di conseguenza, si ritiene che sia importante lasciare queste esercitazioni per gli sviluppatori che cercano ancora materiale sussidiario per lo sviluppo di questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="79b13-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="79b13-106">Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79b13-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="79b13-107">Verranno mantenuti per continuare a usare i dispositivi supportati.</span><span class="sxs-lookup"><span data-stu-id="79b13-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="79b13-108">In futuro sarà disponibile una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79b13-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="79b13-109">Questo avviso verrà aggiornato con un collegamento a queste esercitazioni quando vengono pubblicate.</span><span class="sxs-lookup"><span data-stu-id="79b13-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="79b13-110">MR e Azure 313: servizio hub Internet</span><span class="sxs-lookup"><span data-stu-id="79b13-110">MR and Azure 313: IoT Hub Service</span></span>

![risultato del corso](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="79b13-112">In questo corso si apprenderà come implementare un **servizio Hub** Internet degli Azure in una macchina virtuale che esegue il sistema operativo Ubuntu 16,4.</span><span class="sxs-lookup"><span data-stu-id="79b13-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="79b13-113">Un **app per le funzioni di Azure** verrà quindi usato per ricevere messaggi dalla macchina virtuale Ubuntu e archiviare il risultato in un **servizio tabelle di Azure**.</span><span class="sxs-lookup"><span data-stu-id="79b13-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="79b13-114">Sarà quindi possibile visualizzare questi dati usando **Power bi** su un auricolare Microsoft HoloLens o immersive (VR).</span><span class="sxs-lookup"><span data-stu-id="79b13-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="79b13-115">Il contenuto di questo corso *è applicabile* ai dispositivi IOT Edge, ma ai fini di questo corso, l'attenzione si troverà in un ambiente di macchina virtuale, in modo che l'accesso a un dispositivo perimetrale fisico non sia necessario.</span><span class="sxs-lookup"><span data-stu-id="79b13-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="79b13-116">Completando questo corso, si apprenderà come:</span><span class="sxs-lookup"><span data-stu-id="79b13-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="79b13-117">Distribuire un **modulo IOT Edge** in una macchina virtuale (Ubuntu 16 OS), che rappresenterà il dispositivo Internet delle cose.</span><span class="sxs-lookup"><span data-stu-id="79b13-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="79b13-118">Aggiungere un **modello Tensorflow di Azure visione personalizzata** al modulo perimetrale, con codice che analizzerà le immagini archiviate nel contenitore.</span><span class="sxs-lookup"><span data-stu-id="79b13-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="79b13-119">Configurare il modulo per inviare di nuovo il messaggio di risultato dell'analisi al **servizio Hub**Internet delle cose.</span><span class="sxs-lookup"><span data-stu-id="79b13-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="79b13-120">Usare un **app per le funzioni di Azure** per archiviare il messaggio all'interno di una **tabella di Azure**.</span><span class="sxs-lookup"><span data-stu-id="79b13-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="79b13-121">Configurare **Power bi** per la raccolta del messaggio archiviato e la creazione di un report.</span><span class="sxs-lookup"><span data-stu-id="79b13-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="79b13-122">Visualizza i dati del messaggio Internet all'interno **Power bi**.</span><span class="sxs-lookup"><span data-stu-id="79b13-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="79b13-123">I servizi che si utilizzeranno includono:</span><span class="sxs-lookup"><span data-stu-id="79b13-123">The Services you will use include:</span></span>

- <span data-ttu-id="79b13-124">**Hub di Azure** è un servizio di Microsoft Azure che consente agli sviluppatori di connettersi, monitorare e gestire le risorse del tutto.</span><span class="sxs-lookup"><span data-stu-id="79b13-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="79b13-125">Per altre informazioni, visita la [pagina del **servizio Hub Azure** ](https://azure.microsoft.com/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="79b13-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/services/iot-hub/).</span></span>

- <span data-ttu-id="79b13-126">**Azure container Registry** è un servizio di Microsoft Azure che consente agli sviluppatori di archiviare le immagini del contenitore per diversi tipi di contenitori.</span><span class="sxs-lookup"><span data-stu-id="79b13-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="79b13-127">Per altre informazioni, visitare la [pagina del **servizio container Registry di Azure** ](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="79b13-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/services/container-registry/).</span></span>

- <span data-ttu-id="79b13-128">**Azure app per le funzioni** è un servizio Microsoft Azure, che consente agli sviluppatori di eseguire piccole porzioni di codice, "funzioni", in Azure.</span><span class="sxs-lookup"><span data-stu-id="79b13-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="79b13-129">Questo consente di delegare il lavoro al cloud, anziché l'applicazione locale, che può avere molti vantaggi.</span><span class="sxs-lookup"><span data-stu-id="79b13-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="79b13-130">**Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui C\#, F\#, node. js, Java e php.</span><span class="sxs-lookup"><span data-stu-id="79b13-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="79b13-131">Per altre informazioni, visitare la [pagina **funzioni di Azure** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="79b13-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="79b13-132">**Archiviazione di Azure: tabelle** è un servizio Microsoft Azure, che consente agli sviluppatori di archiviare dati strutturati e non SQL nel cloud, rendendoli facilmente accessibili ovunque.</span><span class="sxs-lookup"><span data-stu-id="79b13-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="79b13-133">Il servizio presenta una progettazione senza schema, che consente l'evoluzione delle tabelle in base alle esigenze e pertanto è molto flessibile.</span><span class="sxs-lookup"><span data-stu-id="79b13-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="79b13-134">Per altre informazioni, visita la [pagina delle **tabelle di Azure**](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="79b13-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="79b13-135">Questo corso ti insegnerà come configurare e usare il servizio hub Internet delle cose e quindi visualizzare una risposta fornita da un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="79b13-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="79b13-136">Sarà quindi necessario applicare questi concetti a una configurazione del servizio Hub delle cose personalizzate, che può essere compilata.</span><span class="sxs-lookup"><span data-stu-id="79b13-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="79b13-137">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="79b13-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="79b13-138">Corso</span><span class="sxs-lookup"><span data-stu-id="79b13-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="79b13-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="79b13-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="79b13-140"><a href="immersive-headset-hardware-details.md">Visori VR immersive</a></span><span class="sxs-lookup"><span data-stu-id="79b13-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="79b13-141">MR e Azure 313: servizio hub Internet</span><span class="sxs-lookup"><span data-stu-id="79b13-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="79b13-142">✔️</span><span class="sxs-lookup"><span data-stu-id="79b13-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="79b13-143">✔️</span><span class="sxs-lookup"><span data-stu-id="79b13-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="79b13-144">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="79b13-144">Prerequisites</span></span>

<span data-ttu-id="79b13-145">Per i prerequisiti più aggiornati per lo sviluppo con realtà mista, tra cui con Microsoft HoloLens, vedere l'articolo [installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .</span><span class="sxs-lookup"><span data-stu-id="79b13-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="79b13-146">Questa esercitazione è progettata per gli sviluppatori che hanno esperienza di base con Python.</span><span class="sxs-lookup"><span data-stu-id="79b13-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="79b13-147">Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano gli elementi testati e verificati al momento della stesura (luglio 2018).</span><span class="sxs-lookup"><span data-stu-id="79b13-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="79b13-148">È possibile utilizzare il software più recente, come indicato nell'articolo [installare gli strumenti](install-the-tools.md) , ma non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b13-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="79b13-149">Sono necessari i componenti hardware e software seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b13-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="79b13-150">Windows 10 Fall Creators Update (o versione successiva), **modalità sviluppatore abilitata**</span><span class="sxs-lookup"><span data-stu-id="79b13-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="79b13-151">Non è possibile eseguire una macchina virtuale con Hyper-V in Windows 10 Home Edition.</span><span class="sxs-lookup"><span data-stu-id="79b13-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="79b13-152">Windows 10 SDK (versione più recente)</span><span class="sxs-lookup"><span data-stu-id="79b13-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="79b13-153">HoloLens, **modalità sviluppatore abilitata**</span><span class="sxs-lookup"><span data-stu-id="79b13-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="79b13-154">Visual Studio 2017.15.4 (usato solo per accedere al Cloud Explorer di Azure)</span><span class="sxs-lookup"><span data-stu-id="79b13-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="79b13-155">Accesso a Internet per Azure e per il servizio hub Internet.</span><span class="sxs-lookup"><span data-stu-id="79b13-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="79b13-156">Per altre informazioni, seguire questo [collegamento alla pagina del servizio Hub](https://azure.microsoft.com/services/iot-hub/) Internet.</span><span class="sxs-lookup"><span data-stu-id="79b13-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/services/iot-hub/)</span></span>
- <span data-ttu-id="79b13-157">Un modello di machine learning.</span><span class="sxs-lookup"><span data-stu-id="79b13-157">A machine learning model.</span></span> <span data-ttu-id="79b13-158">Se non si dispone di un modello pronto per l'utilizzo, [è possibile utilizzare il modello fornito con questo corso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="79b13-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="79b13-159">Software **Hyper-V** abilitato nel computer di sviluppo Windows 10.</span><span class="sxs-lookup"><span data-stu-id="79b13-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="79b13-160">Una macchina virtuale che esegue Ubuntu (16,4 o 18,4), in esecuzione nel computer di sviluppo o in alternativa, è possibile usare un computer separato che esegue Linux (Ubuntu 16,4 o 18,4).</span><span class="sxs-lookup"><span data-stu-id="79b13-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="79b13-161">Per ulteriori informazioni su come creare una macchina virtuale in Windows utilizzando Hyper-V, vedere il [capitolo "prima di iniziare"](#before-you-start). (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="79b13-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="79b13-162">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="79b13-162">Before you start</span></span>

1. <span data-ttu-id="79b13-163">Configurare e testare il HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79b13-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="79b13-164">Se è necessario supporto per la configurazione di HoloLens, [vedere l'articolo relativo alla configurazione di HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="79b13-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="79b13-165">Quando si inizia a sviluppare una nuova app HoloLens, è consigliabile eseguire la **taratura** e l' **ottimizzazione dei sensori** , a volte può essere utile per eseguire queste attività per ogni utente.</span><span class="sxs-lookup"><span data-stu-id="79b13-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="79b13-166">Per informazioni sulla calibrazione, seguire questo [collegamento all'articolo relativo alla calibrazione di HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="79b13-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="79b13-167">Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo relativo all'ottimizzazione del sensore HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="79b13-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="79b13-168">Configurare la **macchina virtuale Ubuntu** con **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="79b13-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="79b13-169">Le risorse seguenti consentiranno di semplificare il processo.</span><span class="sxs-lookup"><span data-stu-id="79b13-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="79b13-170">Per prima cosa, seguire questo collegamento per [scaricare l'immagine ISO 16.04.4 LTS (xenial Xerus) di Ubuntu](https://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="79b13-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="79b13-171">Selezionare l' **immagine del desktop di 64 bit per PC (amd64)** .</span><span class="sxs-lookup"><span data-stu-id="79b13-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="79b13-172">Verificare che **Hyper-V** sia abilitato nel computer Windows 10.</span><span class="sxs-lookup"><span data-stu-id="79b13-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="79b13-173">È possibile seguire questo collegamento per istruzioni sull' [installazione e l'abilitazione di Hyper-V in Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="79b13-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="79b13-174">Avviare Hyper-V e creare una nuova macchina virtuale Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="79b13-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="79b13-175">È possibile seguire questo collegamento per una [Guida dettagliata su come creare una macchina virtuale con Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="79b13-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="79b13-176">Quando viene richiesto di **installare un sistema operativo da un file di immagine di avvio**, selezionare l'immagine ISO di **Ubuntu** scaricata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79b13-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="79b13-177">Non è consigliabile usare la **creazione rapida di Hyper-V** .</span><span class="sxs-lookup"><span data-stu-id="79b13-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="79b13-178">Capitolo 1-recuperare il modello di Visione personalizzata</span><span class="sxs-lookup"><span data-stu-id="79b13-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="79b13-179">Con questo corso potrai accedere a un [modello di visione personalizzata](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) predefinito che rileva tastiere e topi dalle immagini.</span><span class="sxs-lookup"><span data-stu-id="79b13-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="79b13-180">Se si usa questa operazione, procedere con il [capitolo 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="79b13-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="79b13-181">Tuttavia, se si vuole usare il proprio modello di Visione personalizzata, è possibile seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="79b13-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="79b13-182">Nel **progetto visione personalizzata** passare alla scheda **prestazioni** .</span><span class="sxs-lookup"><span data-stu-id="79b13-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="79b13-183">Per esportare il modello, il modello deve usare un dominio *compatto* .</span><span class="sxs-lookup"><span data-stu-id="79b13-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="79b13-184">È possibile modificare il dominio dei modelli nelle impostazioni per il progetto.</span><span class="sxs-lookup"><span data-stu-id="79b13-184">You can change your models domain in the settings for your project.</span></span>

    ![scheda prestazioni](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="79b13-186">Selezionare l' **iterazione** che si desidera esportare e fare clic su **Esporta**.</span><span class="sxs-lookup"><span data-stu-id="79b13-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="79b13-187">Verrà visualizzato un pannello.</span><span class="sxs-lookup"><span data-stu-id="79b13-187">A blade will appear.</span></span>

    ![pannello Esporta](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="79b13-189">Nel pannello fare clic su **file Docker**.</span><span class="sxs-lookup"><span data-stu-id="79b13-189">In the blade click **Docker File**.</span></span>

    ![Selezionare Docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="79b13-191">Scegliere **Linux** dal menu a discesa e quindi fare clic su **download**.</span><span class="sxs-lookup"><span data-stu-id="79b13-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Fare clic su download](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="79b13-193">Decomprimere il contenuto.</span><span class="sxs-lookup"><span data-stu-id="79b13-193">Unzip the content.</span></span> <span data-ttu-id="79b13-194">Che verrà usato più avanti in questo corso.</span><span class="sxs-lookup"><span data-stu-id="79b13-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="79b13-195">Capitolo 2-Servizio Container Registry</span><span class="sxs-lookup"><span data-stu-id="79b13-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="79b13-196">Il **servizio container Registry** è il repository usato per ospitare i contenitori.</span><span class="sxs-lookup"><span data-stu-id="79b13-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="79b13-197">Il **servizio Hub** Internet delle cose che verrà compilato e usato in questo corso fa riferimento al **servizio container Registry** per ottenere i contenitori da distribuire nel dispositivo perimetrale.</span><span class="sxs-lookup"><span data-stu-id="79b13-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="79b13-198">Per prima cosa, seguire questo [collegamento al portale di Azure](https://portal.azure.com/)e accedere con le proprie credenziali.</span><span class="sxs-lookup"><span data-stu-id="79b13-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="79b13-199">Passare a **Crea una risorsa** e cercare **container Registry**.</span><span class="sxs-lookup"><span data-stu-id="79b13-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![registro contenitori](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="79b13-201">Fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="79b13-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="79b13-202">Impostare i parametri di installazione del servizio:</span><span class="sxs-lookup"><span data-stu-id="79b13-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="79b13-203">Inserire un nome per il progetto, in questo esempio denominato **IoTCRegistry**.</span><span class="sxs-lookup"><span data-stu-id="79b13-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="79b13-204">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="79b13-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79b13-205">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b13-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="79b13-206">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="79b13-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="79b13-207">Imposta il percorso del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="79b13-208">Impostare **utente amministratore** su **Abilita**.</span><span class="sxs-lookup"><span data-stu-id="79b13-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="79b13-209">Impostare **SKU** su **Basic**.</span><span class="sxs-lookup"><span data-stu-id="79b13-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="79b13-210">Fare clic su **Crea** e attendere la creazione dei servizi.</span><span class="sxs-lookup"><span data-stu-id="79b13-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="79b13-211">Quando viene visualizzata la notifica che informa che la creazione del *container Registry*è riuscita, fare clic su **Vai alla risorsa** da reindirizzare alla pagina del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="79b13-212">Nella pagina servizio *container Registry* fare clic su **chiavi di accesso**.</span><span class="sxs-lookup"><span data-stu-id="79b13-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="79b13-213">Prendere nota (è possibile usare il blocco note) dei parametri seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b13-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="79b13-214">**Server di accesso**</span><span class="sxs-lookup"><span data-stu-id="79b13-214">**Login Server**</span></span>
    2. <span data-ttu-id="79b13-215">**Nome utente**</span><span class="sxs-lookup"><span data-stu-id="79b13-215">**Username**</span></span>
    3. <span data-ttu-id="79b13-216">**Password**</span><span class="sxs-lookup"><span data-stu-id="79b13-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="79b13-217">Capitolo 3-servizio hub Internet delle cose</span><span class="sxs-lookup"><span data-stu-id="79b13-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="79b13-218">A questo punto si inizierà la creazione e la configurazione del **servizio Hub**Internet delle cose.</span><span class="sxs-lookup"><span data-stu-id="79b13-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="79b13-219">Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="79b13-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="79b13-220">Una volta effettuato l'accesso, fare clic su **Crea una risorsa** nell'angolo in alto a sinistra e cercare l' **Hub**Internet e premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="79b13-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![Cerca account di archiviazione](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="79b13-222">La nuova pagina fornirà una descrizione del servizio dell' **account di archiviazione** .</span><span class="sxs-lookup"><span data-stu-id="79b13-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="79b13-223">Nella parte inferiore sinistra del prompt, fare clic sul pulsante **Crea** per creare un'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="79b13-225">Una volta fatto clic su **Crea**, verrà visualizzato un pannello:</span><span class="sxs-lookup"><span data-stu-id="79b13-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="79b13-226">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="79b13-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79b13-227">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b13-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="79b13-228">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="79b13-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="79b13-229">Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="79b13-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="79b13-230">Selezionare un **percorso** appropriato (usare la stessa posizione in tutti i servizi creati in questo corso).</span><span class="sxs-lookup"><span data-stu-id="79b13-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="79b13-231">Inserire il **nome** desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="79b13-232">Nella parte inferiore della pagina fare clic su **Next: size and scale**.</span><span class="sxs-lookup"><span data-stu-id="79b13-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="79b13-234">In questa pagina selezionare il piano **tariffario e il livello di scalabilità** (se si tratta della prima istanza del servizio hub Internet, sarà disponibile un livello gratuito).</span><span class="sxs-lookup"><span data-stu-id="79b13-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="79b13-235">Fare clic su **Verifica + crea**.</span><span class="sxs-lookup"><span data-stu-id="79b13-235">Click on **Review + Create**.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="79b13-237">Verificare le impostazioni e fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="79b13-237">Review your settings and click on **Create**.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="79b13-239">Quando viene visualizzata la notifica che informa che la creazione del servizio *Hub* Internet è stata completata, fare clic su **Vai alla risorsa** da reindirizzare alla pagina del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="79b13-241">Scorrere il pannello laterale a sinistra fino a quando non viene visualizzata la *gestione automatica dei dispositivi*, facendo clic su **IOT Edge**.</span><span class="sxs-lookup"><span data-stu-id="79b13-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="79b13-243">Nella finestra visualizzata a destra fare clic su **aggiungi IOT Edge dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="79b13-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="79b13-244">Verrà visualizzato un pannello a destra.</span><span class="sxs-lookup"><span data-stu-id="79b13-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="79b13-245">Nel pannello fornire al nuovo dispositivo un **ID dispositivo** , ovvero un nome di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="79b13-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="79b13-246">Quindi, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="79b13-246">Then, click **Save**.</span></span> <span data-ttu-id="79b13-247">Le chiavi *primarie* e *secondarie* vengono generate automaticamente se è stato **generato automaticamente** il segno di generazione.</span><span class="sxs-lookup"><span data-stu-id="79b13-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="79b13-249">Si tornerà alla sezione *dispositivi IOT Edge* , in cui verrà elencato il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="79b13-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="79b13-250">Fare clic sul nuovo dispositivo (descritto in rosso nell'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="79b13-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="79b13-252">Nella pagina *Dettagli dispositivo* visualizzata, eseguire una copia della **stringa di connessione** (chiave primaria).</span><span class="sxs-lookup"><span data-stu-id="79b13-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="79b13-254">Tornare al pannello a sinistra e fare clic su criteri di *accesso condiviso*per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="79b13-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="79b13-255">Nella pagina visualizzata fare clic su **iothubowner**. verrà visualizzato un pannello a destra della schermata.</span><span class="sxs-lookup"><span data-stu-id="79b13-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="79b13-256">Prendere nota (sul blocco note) della **stringa di connessione** (chiave primaria), da usare in un secondo momento quando si imposta la *stringa di connessione* sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="79b13-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="79b13-258">Capitolo 4-configurazione dell'ambiente di sviluppo</span><span class="sxs-lookup"><span data-stu-id="79b13-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="79b13-259">Per creare e distribuire i moduli per il *perimetro dell'hub*Internet delle cose, è necessario che i componenti seguenti siano installati nel computer di sviluppo che esegue Windows 10:</span><span class="sxs-lookup"><span data-stu-id="79b13-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="79b13-260">[Docker per Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), verrà richiesto di creare un account per poterlo scaricare.</span><span class="sxs-lookup"><span data-stu-id="79b13-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="79b13-261">[scaricare ![Docker per Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="79b13-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="79b13-262">Docker richiede *Windows 10 Pro*, *Enterprise 14393*o *Windows Server 2016 RTM*per l'esecuzione.</span><span class="sxs-lookup"><span data-stu-id="79b13-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="79b13-263">Se si eseguono altre versioni di Windows 10, è possibile provare a installare Docker usando la [casella degli strumenti di Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).</span><span class="sxs-lookup"><span data-stu-id="79b13-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="79b13-264">[Python 3,6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="79b13-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="79b13-265">[![scaricare Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="79b13-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="79b13-266">[Visual Studio Code (noto anche come vs code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="79b13-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="79b13-267">[Download ![VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="79b13-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="79b13-268">Dopo aver installato il software menzionato in precedenza, sarà necessario riavviare il computer.</span><span class="sxs-lookup"><span data-stu-id="79b13-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="79b13-269">Capitolo 5-configurazione dell'ambiente Ubuntu</span><span class="sxs-lookup"><span data-stu-id="79b13-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="79b13-270">A questo punto è possibile passare alla configurazione del dispositivo **che esegue Ubuntu OS**.</span><span class="sxs-lookup"><span data-stu-id="79b13-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="79b13-271">Attenersi alla procedura seguente per installare il software necessario per distribuire i contenitori nella lavagna:</span><span class="sxs-lookup"><span data-stu-id="79b13-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79b13-272">È sempre necessario precedere i comandi del terminale con **sudo** per l'esecuzione come utente amministratore.</span><span class="sxs-lookup"><span data-stu-id="79b13-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="79b13-273">cioè</span><span class="sxs-lookup"><span data-stu-id="79b13-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="79b13-274">Aprire il **terminale Ubuntu**e usare il comando seguente per installare **PIP**:</span><span class="sxs-lookup"><span data-stu-id="79b13-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! HINT]<span data-ttu-id="79b13-275"> è possibile aprire facilmente il *terminale* usando i tasti di scelta rapida: **CTRL + ALT + T**.</span><span class="sxs-lookup"><span data-stu-id="79b13-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="79b13-276">In questo capitolo, è possibile che venga richiesto, dal *terminale*, per l'autorizzazione all'uso dell'archiviazione del dispositivo e per l'input di **y/n** (Sì o no), digitare **"y"** , quindi premere il tasto **invio** per accettare.</span><span class="sxs-lookup"><span data-stu-id="79b13-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="79b13-277">Al termine del comando, usare il comando seguente per installare **curl**:</span><span class="sxs-lookup"><span data-stu-id="79b13-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="79b13-278">Dopo l'installazione di **PIP** e **curl** , usare il comando seguente per installare il **runtime di IOT Edge**, necessario per distribuire e controllare i moduli sulla lavagna:</span><span class="sxs-lookup"><span data-stu-id="79b13-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

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

5. <span data-ttu-id="79b13-279">A questo punto verrà chiesto di aprire il *file di configurazione di runtime*per inserire la stringa di **connessione del dispositivo**annotata (nel blocco note) quando si crea il **servizio Hub** Internet (nel[passaggio 14 del capitolo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="79b13-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="79b13-280">Eseguire la riga seguente nel terminale per aprire il file:</span><span class="sxs-lookup"><span data-stu-id="79b13-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="79b13-281">Verrà visualizzato il file **config. YAML** , pronto per la modifica:</span><span class="sxs-lookup"><span data-stu-id="79b13-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="79b13-282">Quando si apre questo file, è possibile che si verifichi una certa confusione.</span><span class="sxs-lookup"><span data-stu-id="79b13-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="79b13-283">Il file verrà modificato dal testo nel *terminale* stesso.</span><span class="sxs-lookup"><span data-stu-id="79b13-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="79b13-284">Usare i tasti di direzione sulla tastiera per scorrere verso il basso (sarà necessario scorrere verso il basso), per raggiungere la riga contenente ":</span><span class="sxs-lookup"><span data-stu-id="79b13-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="79b13-285">" **\<aggiungere la stringa di connessione del dispositivo qui >** ".</span><span class="sxs-lookup"><span data-stu-id="79b13-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="79b13-286">Sostituire la riga, **incluse le parentesi**, con la **stringa di connessione del dispositivo** annotata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79b13-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="79b13-287">Con la stringa di connessione sul posto, sulla tastiera premere i tasti **CTRL + X** per salvare il file.</span><span class="sxs-lookup"><span data-stu-id="79b13-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="79b13-288">Verrà richiesto di confermare digitando **Y**. Premere quindi il tasto **invio** per confermare.</span><span class="sxs-lookup"><span data-stu-id="79b13-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="79b13-289">Si tornerà al *terminale*normale.</span><span class="sxs-lookup"><span data-stu-id="79b13-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="79b13-290">Una volta che tutti i comandi sono stati eseguiti correttamente, il **runtime di IOT Edge**sarà installato.</span><span class="sxs-lookup"><span data-stu-id="79b13-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="79b13-291">Una volta inizializzato, il runtime si avvierà in modo autonomo ogni volta che il dispositivo viene acceso e si troverà in background, in attesa che i moduli vengano distribuiti dal **servizio Hub**Internet delle cose.</span><span class="sxs-lookup"><span data-stu-id="79b13-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="79b13-292">Eseguire la seguente riga di comando per inizializzare il *runtime di IOT Edge*:</span><span class="sxs-lookup"><span data-stu-id="79b13-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="79b13-293">Se si apportano modifiche al file con estensione YAML o al programma di installazione precedente, sarà necessario eseguire nuovamente la riga di riavvio precedente, all'interno del *terminale*.</span><span class="sxs-lookup"><span data-stu-id="79b13-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="79b13-294">Verificare lo stato di *Runtime IOT Edge* eseguendo la riga di comando seguente.</span><span class="sxs-lookup"><span data-stu-id="79b13-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="79b13-295">Il runtime verrà visualizzato con lo stato **attivo (in esecuzione)** in testo verde.</span><span class="sxs-lookup"><span data-stu-id="79b13-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="79b13-296">Premere i tasti **CTRL + C** per uscire dalla pagina stato.</span><span class="sxs-lookup"><span data-stu-id="79b13-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="79b13-297">È possibile verificare che il *runtime di IOT Edge* stia effettuando correttamente il pull dei contenitori digitando il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="79b13-298">Verrà visualizzato un elenco con due contenitori (2).</span><span class="sxs-lookup"><span data-stu-id="79b13-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="79b13-299">Si tratta dei moduli predefiniti che vengono creati automaticamente dal servizio hub Internet delle cose (edgeAgent e edgeHub).</span><span class="sxs-lookup"><span data-stu-id="79b13-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="79b13-300">Una volta creati e distribuiti i moduli, questi verranno visualizzati in questo elenco, sotto quelli predefiniti.</span><span class="sxs-lookup"><span data-stu-id="79b13-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="79b13-301">Capitolo 6: installare le estensioni</span><span class="sxs-lookup"><span data-stu-id="79b13-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79b13-302">I prossimi capitoli (6-9) devono essere eseguiti nel computer Windows 10.</span><span class="sxs-lookup"><span data-stu-id="79b13-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="79b13-303">Aprire **vs code**.</span><span class="sxs-lookup"><span data-stu-id="79b13-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="79b13-304">Fare clic sul pulsante **estensioni** (quadrato) nella barra di sinistra di vs code per aprire il **Pannello estensioni**.</span><span class="sxs-lookup"><span data-stu-id="79b13-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="79b13-305">Cercare e installare le estensioni seguenti (come illustrato nell'immagine seguente):</span><span class="sxs-lookup"><span data-stu-id="79b13-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="79b13-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="79b13-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="79b13-307">Toolkit di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b13-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="79b13-308">Docker</span><span class="sxs-lookup"><span data-stu-id="79b13-308">Docker</span></span>   

    ![Creare il contenitore](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="79b13-310">Una volta installate le estensioni, chiuderlo e riaprirlo VS Code.</span><span class="sxs-lookup"><span data-stu-id="79b13-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="79b13-311">Con VS Code Apri ancora una volta, passare a **visualizza** > **terminale integrato**.</span><span class="sxs-lookup"><span data-stu-id="79b13-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="79b13-312">Si installerà ora **tagliatore**.</span><span class="sxs-lookup"><span data-stu-id="79b13-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="79b13-313">Nel terminale eseguire il comando bash seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! HINT]<span data-ttu-id="79b13-314"> Se si riscontrano problemi con questo comando:</span><span class="sxs-lookup"><span data-stu-id="79b13-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="79b13-315">Riavviare VS Code e/o il computer.</span><span class="sxs-lookup"><span data-stu-id="79b13-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="79b13-316">Potrebbe essere necessario passare il **terminale vs code** a quello usato per installare Python, ad esempio **PowerShell** (soprattutto se l'ambiente Python è già installato nel computer).</span><span class="sxs-lookup"><span data-stu-id="79b13-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="79b13-317">Con il terminale aperto è possibile trovare il menu a discesa sul lato destro del terminale.</span><span class="sxs-lookup"><span data-stu-id="79b13-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="79b13-318">![creare il contenitore](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="79b13-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="79b13-319">Verificare che il percorso di installazione di **Python** venga aggiunto come **variabile di ambiente** nel computer.</span><span class="sxs-lookup"><span data-stu-id="79b13-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="79b13-320">Tagliatore deve far parte dello stesso percorso.</span><span class="sxs-lookup"><span data-stu-id="79b13-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="79b13-321">[Per ulteriori informazioni sulle variabili di ambiente](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), seguire questo collegamento.</span><span class="sxs-lookup"><span data-stu-id="79b13-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="79b13-322">Al termine dell'installazione di **tagliatore** , è necessario riavviare il computer, in modo che **tagliatore** venga riconosciuto come comando nell'ambiente del sistema.</span><span class="sxs-lookup"><span data-stu-id="79b13-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="79b13-323">Capitolo 7: creare una soluzione contenitore</span><span class="sxs-lookup"><span data-stu-id="79b13-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="79b13-324">A questo punto, è necessario creare il contenitore, con il modulo, per eseguire il push nel *container Registry*.</span><span class="sxs-lookup"><span data-stu-id="79b13-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="79b13-325">Dopo aver eseguito il push del contenitore, si userà il servizio *Edge Hub* Internet per distribuirlo nel dispositivo, che esegue il runtime di *IOT Edge*.</span><span class="sxs-lookup"><span data-stu-id="79b13-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="79b13-326">In VS Code fare clic su **visualizza** > **tavolozza comandi**.</span><span class="sxs-lookup"><span data-stu-id="79b13-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="79b13-327">Nella tavolozza, cercare ed eseguire **Azure IOT Edge: nuova soluzione Edge**.</span><span class="sxs-lookup"><span data-stu-id="79b13-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="79b13-328">Individuare un percorso in cui si desidera creare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="79b13-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="79b13-329">Premere il tasto **invio** per accettare il percorso.</span><span class="sxs-lookup"><span data-stu-id="79b13-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="79b13-330">Assegnare un nome alla soluzione.</span><span class="sxs-lookup"><span data-stu-id="79b13-330">Give a name to your solution.</span></span> <span data-ttu-id="79b13-331">Premere il tasto **invio** per confermare il nome fornito.</span><span class="sxs-lookup"><span data-stu-id="79b13-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="79b13-332">A questo punto verrà richiesto di scegliere il Framework modello per la soluzione.</span><span class="sxs-lookup"><span data-stu-id="79b13-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="79b13-333">Fare clic su **modulo Python**.</span><span class="sxs-lookup"><span data-stu-id="79b13-333">Click **Python Module**.</span></span> <span data-ttu-id="79b13-334">Premere il tasto **invio** per confermare la scelta.</span><span class="sxs-lookup"><span data-stu-id="79b13-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="79b13-335">Assegnare un nome al modulo.</span><span class="sxs-lookup"><span data-stu-id="79b13-335">Give a name to your module.</span></span> <span data-ttu-id="79b13-336">Premere il tasto **invio** per confermare il nome del modulo.</span><span class="sxs-lookup"><span data-stu-id="79b13-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="79b13-337">Assicurarsi di prendere nota del nome del modulo (con il blocco note), perché verrà usato in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="79b13-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="79b13-338">Si noterà che nella tavolozza verrà visualizzato un indirizzo predefinito del *repository di immagini Docker* .</span><span class="sxs-lookup"><span data-stu-id="79b13-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="79b13-339">L'aspetto sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-339">It will look like:</span></span>

    <span data-ttu-id="79b13-340">**localhost: 5000/-nome del modulo-** .</span><span class="sxs-lookup"><span data-stu-id="79b13-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="79b13-341">Elimina **localhost: 5000**e al suo posto inserire l'indirizzo del **Server di accesso** *container Registry* , annotato durante la creazione del servizio di **container Registry** ([nel passaggio 8 del capitolo 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="79b13-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="79b13-342">Premere il tasto **invio** per confermare l'indirizzo.</span><span class="sxs-lookup"><span data-stu-id="79b13-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="79b13-343">A questo punto, verrà creata la soluzione contenente il modello per il modulo Python e la relativa struttura verrà visualizzata nella **scheda Esplora**, di vs code, sul lato sinistro dello schermo.</span><span class="sxs-lookup"><span data-stu-id="79b13-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="79b13-344">Se la **scheda Esplora** non è aperta, è possibile aprirla facendo clic sul pulsante in primo piano nella barra a sinistra.</span><span class="sxs-lookup"><span data-stu-id="79b13-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Creare il contenitore](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="79b13-346">L'ultimo passaggio per questo capitolo consiste nel fare clic e aprire il **file con estensione ENV**, nella **scheda Esplora**e aggiungere il **nome utente** e la **password**del *container Registry* .</span><span class="sxs-lookup"><span data-stu-id="79b13-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="79b13-347">Questo file viene ignorato da git, ma quando si compila il contenitore, le credenziali verranno impostate per accedere al **servizio container Registry**.</span><span class="sxs-lookup"><span data-stu-id="79b13-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Creare il contenitore](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="79b13-349">Capitolo 8-modifica della soluzione contenitore</span><span class="sxs-lookup"><span data-stu-id="79b13-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="79b13-350">A questo punto è necessario completare la soluzione contenitore aggiornando i file seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b13-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="79b13-351">script Python *<span></span>Main. py* .</span><span class="sxs-lookup"><span data-stu-id="79b13-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="79b13-352">*requirements. txt*.</span><span class="sxs-lookup"><span data-stu-id="79b13-352">*requirements.txt*.</span></span>
- <span data-ttu-id="79b13-353">*Deployment. template. JSON*.</span><span class="sxs-lookup"><span data-stu-id="79b13-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="79b13-354">*Dockerfile. amd64*</span><span class="sxs-lookup"><span data-stu-id="79b13-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="79b13-355">Si creerà quindi la cartella *images* usata dallo script Python per verificare la presenza di immagini corrispondenti al modello di *visione personalizzata*.</span><span class="sxs-lookup"><span data-stu-id="79b13-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="79b13-356">Infine, si aggiungerà il file *labels. txt* , per facilitare la lettura del modello e il file *Model. PB* , che rappresenta il modello.</span><span class="sxs-lookup"><span data-stu-id="79b13-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="79b13-357">Con VS Code aperto, passare alla cartella del modulo e cercare lo script denominato **<span></span>Main. py**.</span><span class="sxs-lookup"><span data-stu-id="79b13-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="79b13-358">Fare doppio clic per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="79b13-358">Double-click to open it.</span></span>

2. <span data-ttu-id="79b13-359">Eliminare il contenuto del file e inserire il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-359">Delete the content of the file and insert the following code:</span></span>

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

3.  <span data-ttu-id="79b13-360">Aprire il file denominato **requirements. txt**e sostituirne il contenuto con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="79b13-361">Aprire il file denominato **Deployment. template. JSON**e sostituirne il contenuto seguendo le linee guida seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b13-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="79b13-362">Poiché la struttura JSON è personalizzata, sarà necessario modificarla manualmente, invece di copiare un esempio di.</span><span class="sxs-lookup"><span data-stu-id="79b13-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="79b13-363">Per semplificare questa operazione, usare l'immagine seguente come guida.</span><span class="sxs-lookup"><span data-stu-id="79b13-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="79b13-364">Le aree che hanno un aspetto diverso per l'utente, ma che **non devono essere modificate sono evidenziate in giallo**.</span><span class="sxs-lookup"><span data-stu-id="79b13-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="79b13-365">**Le sezioni che è necessario eliminare sono evidenziate in rosso.**</span><span class="sxs-lookup"><span data-stu-id="79b13-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="79b13-366">Prestare attenzione a eliminare le parentesi quadre corrette e rimuovere anche le virgole.</span><span class="sxs-lookup"><span data-stu-id="79b13-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Creare il contenitore](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="79b13-368">Il file JSON completato dovrebbe essere simile all'immagine seguente (Tuttavia, con le differenze univoche: *nome utente/password/nome modulo/riferimenti modulo*):</span><span class="sxs-lookup"><span data-stu-id="79b13-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Creare il contenitore](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="79b13-370">Aprire il file denominato **Dockerfile. amd64**e sostituirne il contenuto con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

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

6.  <span data-ttu-id="79b13-371">Fare clic con il pulsante destro del mouse sulla cartella sotto i **moduli** (il nome fornito in precedenza, nell'esempio più avanti, è denominato *pythonmodule*) e fare clic su **nuova cartella**.</span><span class="sxs-lookup"><span data-stu-id="79b13-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="79b13-372">Denominare le **Immagini**della cartella.</span><span class="sxs-lookup"><span data-stu-id="79b13-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="79b13-373">All'interno della cartella aggiungere alcune immagini che contengono il mouse o la tastiera.</span><span class="sxs-lookup"><span data-stu-id="79b13-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="79b13-374">Si tratta delle immagini che verranno analizzate dal modello Tensorflow.</span><span class="sxs-lookup"><span data-stu-id="79b13-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="79b13-375">Se si usa un modello personalizzato, è necessario modificarlo in modo da riflettere i dati dei modelli personalizzati.</span><span class="sxs-lookup"><span data-stu-id="79b13-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="79b13-376">A questo punto è necessario recuperare i file **labels. txt** e **Model. PB** dalla cartella del modello, che è stata precedentemente scaricata (o creata dal proprio **servizio visione artificiale personalizzato**), nel [capitolo 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="79b13-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="79b13-377">Dopo aver creato i file, posizionarli all'interno della soluzione, insieme ad altri file.</span><span class="sxs-lookup"><span data-stu-id="79b13-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="79b13-378">Il risultato finale dovrebbe essere simile all'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-378">The final result should look like the image below:</span></span>

    ![Creare il contenitore](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="79b13-380">Capitolo 9: creare un pacchetto della soluzione come contenitore</span><span class="sxs-lookup"><span data-stu-id="79b13-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="79b13-381">A questo punto è possibile creare il pacchetto dei file come contenitore ed eseguirne il push nel **container Registry di Azure**.</span><span class="sxs-lookup"><span data-stu-id="79b13-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="79b13-382">All'interno VS Code aprire il *terminale integrato* (**visualizzare** > **terminale integrato** o **CTRL**+ **\`** ) e usare la riga seguente per accedere a **Docker** (sostituire i valori del comando con le credenziali del **container Registry di Azure (ACR)** ):</span><span class="sxs-lookup"><span data-stu-id="79b13-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="79b13-383">Fare clic con il pulsante destro del mouse sul file **Deployment. template. JSON**e scegliere **Compila IOT Edge soluzione**.</span><span class="sxs-lookup"><span data-stu-id="79b13-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="79b13-384">Questo processo di compilazione richiede molto tempo (a seconda del dispositivo), quindi prepararsi ad attendere.</span><span class="sxs-lookup"><span data-stu-id="79b13-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="79b13-385">Al termine del processo di compilazione, un file **Deployment. JSON** sarà stato creato all'interno di una nuova cartella denominata **config**.</span><span class="sxs-lookup"><span data-stu-id="79b13-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![Crea distribuzione](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="79b13-387">Aprire di nuovo il **riquadro comandi** e cercare **Azure: Sign in (accedi**).</span><span class="sxs-lookup"><span data-stu-id="79b13-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="79b13-388">Seguire le istruzioni usando le credenziali dell'account Azure. VS Code fornirà un'opzione per la *copia e l'apertura*, che consente di copiare il codice del dispositivo che sarà presto necessario e di aprire il Web browser predefinito.</span><span class="sxs-lookup"><span data-stu-id="79b13-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="79b13-389">Quando viene richiesto, incollare il codice del dispositivo per autenticare il computer.</span><span class="sxs-lookup"><span data-stu-id="79b13-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![copia e Apri](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="79b13-391">Una volta effettuato l'accesso, si noterà che, nella parte inferiore del pannello di *esplorazione* , è presente una nuova sezione denominata **dispositivi dell'hub Azure**.</span><span class="sxs-lookup"><span data-stu-id="79b13-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="79b13-392">Fare clic su questa sezione per espanderla.</span><span class="sxs-lookup"><span data-stu-id="79b13-392">Click this section to expand it.</span></span>

    ![dispositivo perimetrale](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="79b13-394">Se il dispositivo non è disponibile, è necessario fare clic con il pulsante destro del mouse su *dispositivi dell'hub Azure*, quindi fare clic su **Imposta stringa di connessione dell'hub Internet**.</span><span class="sxs-lookup"><span data-stu-id="79b13-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="79b13-395">Si noterà che il **riquadro comandi** (nella parte superiore di vs code) richiederà di immettere la *stringa di connessione*.</span><span class="sxs-lookup"><span data-stu-id="79b13-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="79b13-396">Si tratta della *stringa di connessione* annotata alla fine del [capitolo 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="79b13-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="79b13-397">Premere il tasto **invio** dopo aver copiato la stringa in.</span><span class="sxs-lookup"><span data-stu-id="79b13-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="79b13-398">Il dispositivo deve essere caricato e visualizzato.</span><span class="sxs-lookup"><span data-stu-id="79b13-398">Your device should load, and appear.</span></span> <span data-ttu-id="79b13-399">Fare clic con il pulsante destro del mouse sul nome del dispositivo e quindi scegliere **Crea distribuzione per singolo dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="79b13-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![Crea distribuzione](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="79b13-401">Verrà visualizzato un prompt di *Esplora file* , in cui è possibile passare alla cartella **config** e quindi selezionare il file **Deployment. JSON** .</span><span class="sxs-lookup"><span data-stu-id="79b13-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="79b13-402">Con il file selezionato, fare clic sul pulsante **Seleziona manifesto di distribuzione Edge** .</span><span class="sxs-lookup"><span data-stu-id="79b13-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![Crea distribuzione](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="79b13-404">A questo punto è stato fornito il **servizio Hub** Internet con il manifesto per la distribuzione del contenitore, come modulo, dal **container Registry di Azure**, in modo da distribuirlo nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="79b13-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="79b13-405">Per visualizzare i messaggi inviati dal dispositivo all'hub Internet, fare di nuovo clic con il pulsante destro del mouse sul nome del dispositivo nella sezione **dispositivi dell'hub Azure** Internet Explorer, nel pannello di **esplorazione** e fare clic su Avvia il **monitoraggio del messaggio D2C**.</span><span class="sxs-lookup"><span data-stu-id="79b13-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="79b13-406">I messaggi inviati dal dispositivo verranno visualizzati nel terminale di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79b13-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="79b13-407">Essere paziente, perché questa operazione potrebbe richiedere del tempo.</span><span class="sxs-lookup"><span data-stu-id="79b13-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="79b13-408">Vedere il capitolo successivo per il debug e verificare se la distribuzione è stata completata correttamente.</span><span class="sxs-lookup"><span data-stu-id="79b13-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="79b13-409">Questo modulo consente ora di eseguire un'iterazione tra le immagini nella cartella **images** e di analizzarle, con ogni iterazione.</span><span class="sxs-lookup"><span data-stu-id="79b13-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="79b13-410">Questo è ovviamente solo una dimostrazione di come ottenere il modello di apprendimento automatico di base per il funzionamento in un ambiente IoT Edge dispositivo.</span><span class="sxs-lookup"><span data-stu-id="79b13-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="79b13-411">Per espandere la funzionalità di questo esempio, è possibile procedere in diversi modi.</span><span class="sxs-lookup"><span data-stu-id="79b13-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="79b13-412">Un modo potrebbe includere il codice nel contenitore, che acquisisce le foto da una webcam connessa al dispositivo e salva le immagini nella cartella immagini.</span><span class="sxs-lookup"><span data-stu-id="79b13-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="79b13-413">Un altro modo potrebbe copiare le immagini dal dispositivo Internet delle cose nel contenitore.</span><span class="sxs-lookup"><span data-stu-id="79b13-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="79b13-414">Un modo pratico per eseguire questa operazione consiste nell'eseguire il comando seguente nel terminale del dispositivo Internet delle cose, ad esempio se si desidera automatizzare il processo.</span><span class="sxs-lookup"><span data-stu-id="79b13-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="79b13-415">È possibile testare questo comando eseguendolo manualmente dal percorso della cartella in cui sono archiviati i file:</span><span class="sxs-lookup"><span data-stu-id="79b13-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="79b13-416">Capitolo 10-debug del runtime di IoT Edge</span><span class="sxs-lookup"><span data-stu-id="79b13-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="79b13-417">Di seguito è riportato un elenco di righe di comando e suggerimenti che consentono di monitorare ed eseguire il debug dell'attività di messaggistica del *runtime di IOT Edge*, dal **dispositivo Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="79b13-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="79b13-418">Verificare lo stato di *Runtime IOT Edge* eseguendo la riga di comando seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="79b13-419">Ricordarsi di premere **CTRL + C**per completare la visualizzazione dello stato.</span><span class="sxs-lookup"><span data-stu-id="79b13-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="79b13-420">Elenca i contenitori attualmente distribuiti.</span><span class="sxs-lookup"><span data-stu-id="79b13-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="79b13-421">Se il *servizio Hub* Internet delle cose ha distribuito correttamente i contenitori, verranno visualizzati eseguendo la riga di comando seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="79b13-422">Oppure</span><span class="sxs-lookup"><span data-stu-id="79b13-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="79b13-423">Questo è un buon metodo per verificare se il modulo è stato distribuito correttamente, perché verrà visualizzato nell'elenco; in caso contrario, si vedranno **solo** *edgeHub* e *edgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="79b13-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="79b13-424">Per visualizzare i log del codice di un contenitore, eseguire la riga di comando seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="79b13-425">**Comandi utili per gestire il runtime di IoT Edge:**</span><span class="sxs-lookup"><span data-stu-id="79b13-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="79b13-426">Per eliminare tutti i contenitori nell'host:</span><span class="sxs-lookup"><span data-stu-id="79b13-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="79b13-427">Per arrestare il *runtime di IOT Edge*:</span><span class="sxs-lookup"><span data-stu-id="79b13-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="79b13-428">Capitolo 11-creazione del servizio tabelle</span><span class="sxs-lookup"><span data-stu-id="79b13-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="79b13-429">Tornare al portale di Azure, in cui si creerà un servizio tabelle di Azure creando una risorsa di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="79b13-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="79b13-430">Se non è già stato effettuato l'accesso, accedere al [portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="79b13-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="79b13-431">Una volta effettuato l'accesso, fare clic su **Crea una risorsa**, nell'angolo in alto a sinistra e cercare **account di archiviazione**e premere **invio** per avviare la ricerca.</span><span class="sxs-lookup"><span data-stu-id="79b13-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="79b13-432">Una volta visualizzato, fare clic su **account di archiviazione: BLOB, file, tabelle, code** nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="79b13-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Cerca account di archiviazione](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="79b13-434">La nuova pagina fornirà una descrizione del servizio dell' **account di archiviazione** .</span><span class="sxs-lookup"><span data-stu-id="79b13-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="79b13-435">Nella parte inferiore sinistra del prompt, fare clic sul pulsante **Crea** per creare un'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Crea istanza di archiviazione](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="79b13-437">Una volta fatto clic su **Crea**, verrà visualizzato un pannello:</span><span class="sxs-lookup"><span data-stu-id="79b13-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="79b13-438">Inserire il **nome** desiderato per l'istanza del servizio (*deve essere in lettere minuscole*).</span><span class="sxs-lookup"><span data-stu-id="79b13-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="79b13-439">Per **modello di distribuzione**, fare clic su **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="79b13-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="79b13-440">Per **tipo di account**, usando il menu a discesa, fare clic su **archiviazione (utilizzo generico V1)** .</span><span class="sxs-lookup"><span data-stu-id="79b13-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="79b13-441">Fare clic su un **percorso**appropriato.</span><span class="sxs-lookup"><span data-stu-id="79b13-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="79b13-442">Per il menu a discesa **replica** , fare clic su **archiviazione con ridondanza geografica e accesso in lettura (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="79b13-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="79b13-443">Per **prestazioni**, fare clic su **standard**.</span><span class="sxs-lookup"><span data-stu-id="79b13-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="79b13-444">Nella sezione **trasferimento sicuro obbligatorio** fare clic su **disabilitato**.</span><span class="sxs-lookup"><span data-stu-id="79b13-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="79b13-445">Dal menu a discesa **sottoscrizione** fare clic su una sottoscrizione appropriata.</span><span class="sxs-lookup"><span data-stu-id="79b13-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="79b13-446">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="79b13-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79b13-447">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b13-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="79b13-448">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="79b13-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="79b13-449">Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="79b13-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="79b13-450">Lasciare le **reti virtuali** **disabilitate**, se questa è un'opzione.</span><span class="sxs-lookup"><span data-stu-id="79b13-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="79b13-451">Fai clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="79b13-451">Click **Create**.</span></span>

        ![specificare i dettagli di archiviazione](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="79b13-453">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="79b13-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="79b13-454">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="79b13-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="79b13-455">Fare clic sulle notifiche per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-455">Click on the notifications to explore your new Service instance.</span></span>

    ![nuova notifica di archiviazione](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="79b13-457">Fare clic sul pulsante **Vai alla risorsa** nella notifica. verrà quindi eseguita la nuova pagina Panoramica dell'istanza del servizio di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="79b13-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![Vai alla risorsa](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="79b13-459">Nella pagina Panoramica fare clic su **tabelle**sul lato destro.</span><span class="sxs-lookup"><span data-stu-id="79b13-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![tabelle](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="79b13-461">Il pannello a destra cambierà in modo da visualizzare le informazioni sul **servizio tabelle** , in cui è necessario aggiungere una nuova tabella.</span><span class="sxs-lookup"><span data-stu-id="79b13-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="79b13-462">A tale scopo, fare clic sul pulsante **+ tabella** nell'angolo superiore sinistro.</span><span class="sxs-lookup"><span data-stu-id="79b13-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![Apri tabelle](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="79b13-464">Verrà visualizzata una nuova pagina, in cui è necessario immettere un nome di **tabella**.</span><span class="sxs-lookup"><span data-stu-id="79b13-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="79b13-465">Si tratta del nome che verrà usato per fare riferimento ai dati nell'applicazione nei capitoli successivi (creazione di app per le funzioni e Power BI).</span><span class="sxs-lookup"><span data-stu-id="79b13-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="79b13-466">Inserire **IoTMessages** come nome (è possibile sceglierne un altro, ricordarlo se usato più avanti in questo documento) e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="79b13-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="79b13-467">Una volta creata la nuova tabella, sarà possibile visualizzarla nella pagina del **servizio tabelle** (nella parte inferiore).</span><span class="sxs-lookup"><span data-stu-id="79b13-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![nuova tabella creata](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="79b13-469">A questo punto, fare clic su **chiavi di accesso** e copiare il nome e la **chiave** dell' **account di archiviazione** (usando il blocco note). questi valori verranno usati più avanti in questo corso, quando si crea il app per le funzioni di **Azure**.</span><span class="sxs-lookup"><span data-stu-id="79b13-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![nuova tabella creata](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="79b13-471">Utilizzando di nuovo il pannello a sinistra, scorrere fino alla sezione *servizio* tabelle, fare clic su **tabelle** (o **esplorare le tabelle**, in portali più recenti) ed eseguire una copia dell'URL della **tabella** (usando il blocco note).</span><span class="sxs-lookup"><span data-stu-id="79b13-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="79b13-472">Questo valore verrà usato più avanti in questo corso, quando si collega la tabella all'applicazione **Power bi** .</span><span class="sxs-lookup"><span data-stu-id="79b13-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![nuova tabella creata](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="79b13-474">Capitolo 12-completamento della tabella di Azure</span><span class="sxs-lookup"><span data-stu-id="79b13-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="79b13-475">Ora che l'account di archiviazione del **servizio tabelle** è stato configurato, è possibile aggiungervi dati, che verranno usati per archiviare e recuperare le informazioni.</span><span class="sxs-lookup"><span data-stu-id="79b13-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="79b13-476">La modifica delle tabelle può essere eseguita tramite **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="79b13-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="79b13-477">Aprire **Visual Studio** (**non** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="79b13-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="79b13-478">Dal menu fare clic su **visualizza** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="79b13-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Aprire Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="79b13-480">Il **Cloud Explorer** verrà aperto come elemento ancorato (essere paziente, perché il caricamento potrebbe richiedere tempo).</span><span class="sxs-lookup"><span data-stu-id="79b13-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="79b13-481">Se la sottoscrizione usata per creare gli *account di archiviazione* non è visibile, assicurarsi di disporre di:</span><span class="sxs-lookup"><span data-stu-id="79b13-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="79b13-482">Si è connessi allo stesso account usato per il portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b13-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="79b13-483">È stata selezionata la sottoscrizione dalla pagina di gestione degli account. potrebbe essere necessario applicare un filtro dalle impostazioni dell'account:</span><span class="sxs-lookup"><span data-stu-id="79b13-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![trova sottoscrizione](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="79b13-485">Verranno visualizzati i servizi cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b13-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="79b13-486">Trovare gli **account di archiviazione** e fare clic sulla freccia a sinistra di per espandere gli account.</span><span class="sxs-lookup"><span data-stu-id="79b13-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![aprire gli account di archiviazione](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="79b13-488">Una volta espansa, l' **account di archiviazione** appena creato dovrebbe essere disponibile.</span><span class="sxs-lookup"><span data-stu-id="79b13-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="79b13-489">Fare clic sulla freccia a sinistra della risorsa di archiviazione, quindi, una volta espansa, trovare le **tabelle** e fare clic sulla freccia accanto a questa, per visualizzare la **tabella** creata nell'ultimo capitolo.</span><span class="sxs-lookup"><span data-stu-id="79b13-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="79b13-490">Fare doppio clic sulla **tabella**.</span><span class="sxs-lookup"><span data-stu-id="79b13-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="79b13-491">La tabella verrà aperta al centro della finestra di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79b13-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="79b13-492">Fare clic sull'icona della tabella con il **+** (Plus).</span><span class="sxs-lookup"><span data-stu-id="79b13-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![Aggiungi nuova tabella](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="79b13-494">Verrà visualizzata una finestra con la richiesta di *aggiungere un'entità*.</span><span class="sxs-lookup"><span data-stu-id="79b13-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="79b13-495">Si creerà solo un'entità, anche se avranno tre proprietà.</span><span class="sxs-lookup"><span data-stu-id="79b13-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="79b13-496">Si noterà che *PartitionKey* e *RowKey* sono già disponibili, perché vengono usati dalla tabella per trovare i dati.</span><span class="sxs-lookup"><span data-stu-id="79b13-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![chiave di partizione e di riga](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="79b13-498">Aggiornare i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="79b13-498">Update the following values:</span></span>

    - <span data-ttu-id="79b13-499">Nome: **PartitionKey**, valore: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="79b13-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="79b13-500">Nome: **RowKey**, valore: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="79b13-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="79b13-501">Quindi, fare clic su **Aggiungi proprietà** (in basso a sinistra della finestra *Aggiungi entità* ) e aggiungere la proprietà seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="79b13-502">**MessageContent**, sotto forma di *stringa*, lasciare vuoto il valore.</span><span class="sxs-lookup"><span data-stu-id="79b13-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="79b13-503">La tabella deve corrispondere a quella dell'immagine seguente:</span><span class="sxs-lookup"><span data-stu-id="79b13-503">Your table should match the one in the image below:</span></span>

    ![Aggiungi valori corretti](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="79b13-505">Il motivo per cui l'entità ha il numero 1 nella chiave di riga è perché potrebbe essere necessario aggiungere altri messaggi, qualora si desideri sperimentare ulteriormente questo corso.</span><span class="sxs-lookup"><span data-stu-id="79b13-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="79b13-506">Al termine, fare clic su **OK** .</span><span class="sxs-lookup"><span data-stu-id="79b13-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="79b13-507">La tabella è ora pronta per essere usata.</span><span class="sxs-lookup"><span data-stu-id="79b13-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="79b13-508">Capitolo 13: creare una app per le funzioni di Azure</span><span class="sxs-lookup"><span data-stu-id="79b13-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="79b13-509">A questo punto è necessario creare un *app per le funzioni di Azure*, che verrà chiamato dal *servizio Hub* Internet delle cose per archiviare i messaggi di *IOT Edge* dispositivo nel servizio **tabelle** , creato nel capitolo precedente.</span><span class="sxs-lookup"><span data-stu-id="79b13-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="79b13-510">In primo luogo, è necessario creare un file che consentirà alla funzione di Azure di caricare le librerie necessarie.</span><span class="sxs-lookup"><span data-stu-id="79b13-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="79b13-511">Aprire il **blocco note** (premere il *tasto Windows*e digitare *notepad*).</span><span class="sxs-lookup"><span data-stu-id="79b13-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![Apri blocco note](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="79b13-513">Con blocco note aperto, inserire la struttura JSON riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="79b13-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="79b13-514">Una volta completata questa operazione, salvarla sul desktop come **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="79b13-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="79b13-515">Questo file definisce le librerie che la funzione utilizzerà.</span><span class="sxs-lookup"><span data-stu-id="79b13-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="79b13-516">Se è stato usato NuGet, avrà un aspetto familiare.</span><span class="sxs-lookup"><span data-stu-id="79b13-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="79b13-517">È importante che la denominazione sia corretta; Assicurarsi che **non disponga di un'estensione di file txt** .</span><span class="sxs-lookup"><span data-stu-id="79b13-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="79b13-518">Per informazioni di riferimento, vedere di seguito:</span><span class="sxs-lookup"><span data-stu-id="79b13-518">See below for reference:</span></span>
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

3.  <span data-ttu-id="79b13-520">Accedere al portale di [Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="79b13-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="79b13-521">Una volta effettuato l'accesso, fare clic su **Crea una risorsa** nell'angolo in alto a sinistra e cercare **app per le funzioni**e premere il tasto **invio** per eseguire la ricerca.</span><span class="sxs-lookup"><span data-stu-id="79b13-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="79b13-522">Fare clic su *app per le funzioni* nei risultati per aprire un nuovo pannello.</span><span class="sxs-lookup"><span data-stu-id="79b13-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![Cerca app per le funzioni](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="79b13-524">Il nuovo pannello fornirà una descrizione del servizio **app per le funzioni** .</span><span class="sxs-lookup"><span data-stu-id="79b13-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="79b13-525">Nella parte inferiore sinistra di questo pannello fare clic sul pulsante **Crea** per creare un'associazione con il servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![istanza dell'app per le funzioni](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="79b13-527">Una volta fatto clic su **Crea**, compilare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="79b13-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="79b13-528">Per **nome app**, inserire il nome desiderato per l'istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="79b13-529">Selezionare una **sottoscrizione**.</span><span class="sxs-lookup"><span data-stu-id="79b13-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="79b13-530">Selezionare il piano tariffario appropriato, se è la prima volta che si crea un **servizio app per le funzioni**, sarà disponibile un livello gratuito.</span><span class="sxs-lookup"><span data-stu-id="79b13-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="79b13-531">Scegliere un **gruppo di risorse** o crearne uno nuovo.</span><span class="sxs-lookup"><span data-stu-id="79b13-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="79b13-532">Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure.</span><span class="sxs-lookup"><span data-stu-id="79b13-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="79b13-533">Si consiglia di lasciare tutti i servizi di Azure associati a un singolo progetto (ad esempio questi corsi) in un gruppo di risorse comune).</span><span class="sxs-lookup"><span data-stu-id="79b13-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="79b13-534">Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento per informazioni [su come gestire un gruppo di risorse](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="79b13-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="79b13-535">Per **sistema operativo**, fare clic su Windows, che corrisponde alla piattaforma desiderata.</span><span class="sxs-lookup"><span data-stu-id="79b13-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="79b13-536">Selezionare un **piano di hosting** . questa esercitazione usa un **piano a consumo**.</span><span class="sxs-lookup"><span data-stu-id="79b13-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="79b13-537">Selezionare un **percorso** (scegliere la stessa posizione della risorsa di archiviazione compilata nel passaggio precedente)</span><span class="sxs-lookup"><span data-stu-id="79b13-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="79b13-538">Per la sezione **archiviazione** **è necessario selezionare il servizio di archiviazione creato nel passaggio precedente**.</span><span class="sxs-lookup"><span data-stu-id="79b13-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="79b13-539">Non sarà necessario *Application Insights* in questa app, quindi è possibile lasciarla **disattivata**.</span><span class="sxs-lookup"><span data-stu-id="79b13-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="79b13-540">Fai clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="79b13-540">Click **Create**.</span></span>

        ![Crea nuova istanza](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="79b13-542">Una volta fatto clic su **Crea**, sarà necessario attendere il completamento della creazione del servizio. l'operazione potrebbe richiedere un minuto.</span><span class="sxs-lookup"><span data-stu-id="79b13-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="79b13-543">Dopo la creazione dell'istanza del servizio, verrà visualizzata una notifica nel portale.</span><span class="sxs-lookup"><span data-stu-id="79b13-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![nuova notifica](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="79b13-545">Fare clic sulla notifica, una volta completata la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="79b13-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="79b13-546">Fare clic sul pulsante **Vai alla risorsa** nella notifica per esplorare la nuova istanza del servizio.</span><span class="sxs-lookup"><span data-stu-id="79b13-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Vai alla risorsa](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="79b13-548">Sul lato sinistro del nuovo pannello fare clic sull'icona **+** (più) accanto a *funzioni*per creare una nuova funzione.</span><span class="sxs-lookup"><span data-stu-id="79b13-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Aggiungi nuova funzione](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="79b13-550">All'interno del pannello centrale verrà visualizzata la finestra di creazione della **funzione** .</span><span class="sxs-lookup"><span data-stu-id="79b13-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="79b13-551">Scorrere ulteriormente verso il basso e fare clic su **funzione personalizzata**.</span><span class="sxs-lookup"><span data-stu-id="79b13-551">Scroll down further, and click on **Custom function**.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="79b13-553">Scorrere verso il basso la pagina successiva finché non viene trovato l'hub delle cose **(hub eventi)** , quindi fare clic su di esso.</span><span class="sxs-lookup"><span data-stu-id="79b13-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="79b13-555">Nel **Pannello Hub eventi (hub eventi)** impostare la **lingua** su **C#** e quindi fare clic su **nuovo**.</span><span class="sxs-lookup"><span data-stu-id="79b13-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="79b13-557">Nella finestra che verrà visualizzata verificare che sia selezionata l'opzione **Hub** Internet e che il nome del campo dell' *Hub* Internet corrisponda al nome del *servizio Hub* Internet che è stato creato in precedenza ([nel passaggio 8 del capitolo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="79b13-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="79b13-558">Fare quindi clic sul pulsante **Seleziona** .</span><span class="sxs-lookup"><span data-stu-id="79b13-558">Then click the **Select** button.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="79b13-560">Tornare al **Pannello Hub eventi (hub eventi)** , fare clic su **Crea**.</span><span class="sxs-lookup"><span data-stu-id="79b13-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="79b13-562">Si verrà reindirizzati all'editor di funzioni.</span><span class="sxs-lookup"><span data-stu-id="79b13-562">You will be redirected to the function editor.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="79b13-564">Eliminare tutto il codice e sostituirlo con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="79b13-564">Delete all the code in it and replace it with the following:</span></span>

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

19. <span data-ttu-id="79b13-565">Modificare le variabili seguenti, in modo che corrispondano ai valori appropriati (valori di**tabella** e di **archiviazione** , [rispettivamente dal passaggio 11 e 13 del capitolo 11](#chapter-11---create-table-service)), che si troveranno nell'account di **archiviazione**:</span><span class="sxs-lookup"><span data-stu-id="79b13-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="79b13-566">**TableName**, con il nome della **tabella** che si trova nell' **account di archiviazione**.</span><span class="sxs-lookup"><span data-stu-id="79b13-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="79b13-567">**tableURL**, con l'URL della **tabella** che si trova nell' **account di archiviazione**.</span><span class="sxs-lookup"><span data-stu-id="79b13-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="79b13-568">**storageAccountName**, con il nome del valore corrispondente al nome del nome dell' **account di archiviazione** .</span><span class="sxs-lookup"><span data-stu-id="79b13-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="79b13-569">**storageAccountKey**, con la chiave ottenuta nel servizio di archiviazione creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="79b13-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="79b13-571">Con il codice sul posto, fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="79b13-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="79b13-572">Fare quindi clic sull'icona **\<** (freccia), sul lato destro della pagina.</span><span class="sxs-lookup"><span data-stu-id="79b13-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="79b13-574">Un pannello scorrerà verso destra.</span><span class="sxs-lookup"><span data-stu-id="79b13-574">A panel will slide in from the right.</span></span> <span data-ttu-id="79b13-575">In tale pannello fare clic su **carica**e verrà visualizzato un *browser file* .</span><span class="sxs-lookup"><span data-stu-id="79b13-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="79b13-576">Passare a e fare clic sul file **Project. JSON** , creato in precedenza nel **blocco note** , quindi fare clic sul pulsante **Apri** .</span><span class="sxs-lookup"><span data-stu-id="79b13-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="79b13-577">Questo file definisce le librerie che la funzione utilizzerà.</span><span class="sxs-lookup"><span data-stu-id="79b13-577">This file defines the libraries that your function will use.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="79b13-579">Quando il file è stato caricato, verrà visualizzato nel pannello a destra.</span><span class="sxs-lookup"><span data-stu-id="79b13-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="79b13-580">Facendo clic su di esso verrà aperto nell'editor di **funzioni** .</span><span class="sxs-lookup"><span data-stu-id="79b13-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="79b13-581">Deve essere **esattamente** uguale all'immagine successiva.</span><span class="sxs-lookup"><span data-stu-id="79b13-581">It must look **exactly** the same as the next image.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="79b13-583">A questo punto sarebbe opportuno testare la funzionalità della funzione per archiviare il messaggio nella *tabella*.</span><span class="sxs-lookup"><span data-stu-id="79b13-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="79b13-584">Sul lato superiore destro della finestra fare clic su **test**.</span><span class="sxs-lookup"><span data-stu-id="79b13-584">On the top right side of the window, click on **Test**.</span></span>

    ![funzione personalizzata](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="79b13-586">Inserire un messaggio sul **corpo della richiesta**, come illustrato nell'immagine precedente, e fare clic su **Run (Esegui**).</span><span class="sxs-lookup"><span data-stu-id="79b13-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="79b13-587">La funzione verrà eseguita, visualizzando lo stato del risultato (si noterà lo **stato verde 202 accettato**, sopra la finestra di *output* , il che significa che è stata effettuata una chiamata riuscita):</span><span class="sxs-lookup"><span data-stu-id="79b13-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![Risultato output](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="79b13-589">Capitolo 14-visualizzare i messaggi attivi</span><span class="sxs-lookup"><span data-stu-id="79b13-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="79b13-590">Se ora si apre Visual Studio (**non** Visual Studio Code), è possibile visualizzare il risultato del messaggio di test, in quanto verrà archiviato nell'area della stringa *MessageContent* .</span><span class="sxs-lookup"><span data-stu-id="79b13-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![funzione personalizzata](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="79b13-592">Con il servizio tabelle e app per le funzioni sul posto, i messaggi di Ubuntu Device verranno visualizzati nella tabella *IoTMessages* .</span><span class="sxs-lookup"><span data-stu-id="79b13-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="79b13-593">Se non è già in esecuzione, riavviare il dispositivo e sarà possibile visualizzare i messaggi di risultato dal dispositivo e il modulo nella tabella tramite l'uso di Visual Studio *Cloud Explorer*.</span><span class="sxs-lookup"><span data-stu-id="79b13-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Visualizza dati](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="79b13-595">Capitolo 15-installazione di Power BI</span><span class="sxs-lookup"><span data-stu-id="79b13-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="79b13-596">Per visualizzare i dati dal dispositivo Internet delle cose, configurare **Power bi** (versione desktop), per raccogliere i dati dal servizio *tabelle* appena creato.</span><span class="sxs-lookup"><span data-stu-id="79b13-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="79b13-597">La versione *HoloLens* di Power bi utilizzerà quindi i dati per visualizzare il risultato.</span><span class="sxs-lookup"><span data-stu-id="79b13-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="79b13-598">Aprire il Microsoft Store in Windows 10 e cercare **Power bi desktop**.</span><span class="sxs-lookup"><span data-stu-id="79b13-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="79b13-600">Scaricare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="79b13-600">Download the application.</span></span> <span data-ttu-id="79b13-601">Al termine del download, aprirlo.</span><span class="sxs-lookup"><span data-stu-id="79b13-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="79b13-602">Accedere a *Power bi* con l' **account di Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="79b13-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="79b13-603">Per iscriversi, è possibile essere reindirizzati a un browser.</span><span class="sxs-lookup"><span data-stu-id="79b13-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="79b13-604">Una volta effettuata l'iscrizione, tornare all'app Power BI ed eseguire di nuovo l'accesso.</span><span class="sxs-lookup"><span data-stu-id="79b13-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="79b13-605">Fare clic su **Ottieni dati** , quindi fare clic su **altro.**</span><span class="sxs-lookup"><span data-stu-id="79b13-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="79b13-607">Fare clic su **Azure**, **archiviazione tabelle di Azure**e quindi su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="79b13-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="79b13-609">Verrà richiesto di inserire l'URL della **tabella** raccolto in precedenza ([nel passaggio 13 del capitolo 11](#chapter-11---create-table-service)), durante la creazione del servizio tabelle.</span><span class="sxs-lookup"><span data-stu-id="79b13-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="79b13-610">Dopo aver inserito l'URL, eliminare la parte del percorso che fa riferimento alla tabella "subfolder" (che è stata IoTMessages, in questo corso).</span><span class="sxs-lookup"><span data-stu-id="79b13-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="79b13-611">Il risultato finale dovrebbe essere come visualizzato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="79b13-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="79b13-612">Fare quindi clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="79b13-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="79b13-614">Verrà richiesto di inserire la chiave di **archiviazione** annotata ([nel passaggio 11 del capitolo 11) in](#chapter-11---create-table-service)precedenza durante la creazione dell'archiviazione tabelle.</span><span class="sxs-lookup"><span data-stu-id="79b13-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="79b13-615">Fare quindi clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="79b13-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="79b13-617">Verrà visualizzato un **Pannello dello strumento di navigazione** , quindi selezionare la casella accanto alla tabella e fare clic su **carica**.</span><span class="sxs-lookup"><span data-stu-id="79b13-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="79b13-619">La tabella è stata caricata in Power BI, ma richiede una query per visualizzare i valori in esso contenuti.</span><span class="sxs-lookup"><span data-stu-id="79b13-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="79b13-620">A tale scopo, fare clic con il pulsante destro del mouse sul nome della tabella che si trova nel **Pannello campi** sul lato destro dello schermo.</span><span class="sxs-lookup"><span data-stu-id="79b13-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="79b13-621">Quindi fare clic su **modifica query**.</span><span class="sxs-lookup"><span data-stu-id="79b13-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="79b13-623">Un **Editor Power query** si aprirà come nuova finestra, visualizzando la tabella.</span><span class="sxs-lookup"><span data-stu-id="79b13-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="79b13-624">Fare clic sul **record** di parole nella colonna *contenuto* della tabella per visualizzare il contenuto archiviato.</span><span class="sxs-lookup"><span data-stu-id="79b13-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="79b13-626">Fare clic su **nella tabella**nella parte superiore sinistra della finestra.</span><span class="sxs-lookup"><span data-stu-id="79b13-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="79b13-628">Fare clic su **chiudi & applica**.</span><span class="sxs-lookup"><span data-stu-id="79b13-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="79b13-630">Al termine del caricamento della query, all'interno del **Pannello campi**, sul lato destro dello schermo, selezionare le caselle corrispondenti al **nome** e al **valore**dei parametri per visualizzare il contenuto della colonna **MessageContent** .</span><span class="sxs-lookup"><span data-stu-id="79b13-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="79b13-632">Fare clic sull' **icona del disco Blu** nella parte superiore sinistra della finestra per salvare il lavoro in una cartella di propria scelta.</span><span class="sxs-lookup"><span data-stu-id="79b13-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="79b13-634">È ora possibile fare clic sul pulsante pubblica per caricare la tabella nell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="79b13-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="79b13-635">Quando richiesto, fare clic su **area di lavoro personale** e fare clic su *Seleziona*.</span><span class="sxs-lookup"><span data-stu-id="79b13-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="79b13-636">Attendere che visualizzi il risultato corretto dell'invio.</span><span class="sxs-lookup"><span data-stu-id="79b13-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="79b13-639">Il capitolo seguente è specifico di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79b13-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="79b13-640">Power BI non è attualmente disponibile come applicazione immersiva, ma è possibile eseguire la versione desktop nel portale per la realtà mista di Windows (noto anche come Cliff House), tramite l'app desktop.</span><span class="sxs-lookup"><span data-stu-id="79b13-640">Power BI is not currently available as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="79b13-641">Capitolo 16: visualizzare i dati Power BI in HoloLens</span><span class="sxs-lookup"><span data-stu-id="79b13-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="79b13-642">Nella HoloLens accedere al **Microsoft Store**, toccando la relativa icona nell'elenco delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="79b13-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="79b13-644">Cercare e scaricare l'applicazione **Power bi** .</span><span class="sxs-lookup"><span data-stu-id="79b13-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="79b13-646">Avviare **Power bi** dall'elenco delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="79b13-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="79b13-647">**Power bi** possibile richiedere l'accesso all'account di **Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="79b13-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="79b13-648">Una volta all'interno dell'app, l'area di lavoro verrà visualizzata per impostazione predefinita, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="79b13-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="79b13-649">Se ciò non accade, è sufficiente fare clic sull'icona dell'area di lavoro sul lato sinistro della finestra.</span><span class="sxs-lookup"><span data-stu-id="79b13-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="79b13-651">L'applicazione dell'hub Internet è stata completata</span><span class="sxs-lookup"><span data-stu-id="79b13-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="79b13-652">Congratulazioni, è stato creato un servizio hub Internet delle cose con un dispositivo periferico della macchina virtuale simulato.</span><span class="sxs-lookup"><span data-stu-id="79b13-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="79b13-653">Il dispositivo può comunicare i risultati di un modello di apprendimento automatico a un servizio tabelle di Azure, semplificato da un app per le funzioni di Azure, che viene letto in Power BI e visualizzato all'interno di una HoloLens Microsoft.</span><span class="sxs-lookup"><span data-stu-id="79b13-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="79b13-655">Esercizi bonus</span><span class="sxs-lookup"><span data-stu-id="79b13-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="79b13-656">Esercizio 1</span><span class="sxs-lookup"><span data-stu-id="79b13-656">Exercise 1</span></span>

<span data-ttu-id="79b13-657">Espandere la struttura di messaggistica archiviata nella tabella e visualizzarla come grafico.</span><span class="sxs-lookup"><span data-stu-id="79b13-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="79b13-658">È possibile che si desideri raccogliere più dati e archiviarli nella stessa tabella per essere visualizzati in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="79b13-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="79b13-659">Esercizio 2</span><span class="sxs-lookup"><span data-stu-id="79b13-659">Exercise 2</span></span>

<span data-ttu-id="79b13-660">Creare un ulteriore modulo "acquisizione fotocamera" da distribuire nella bacheca degli utenti, in modo che possa acquisire immagini attraverso la fotocamera da analizzare.</span><span class="sxs-lookup"><span data-stu-id="79b13-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
