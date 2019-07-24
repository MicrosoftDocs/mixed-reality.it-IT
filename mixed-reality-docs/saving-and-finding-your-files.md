---
title: Salvataggio e ricerca dei file
description: Come trovare, salvare e condividere file in HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: procedura, selezione file, file, foto, video, immagini, OneDrive, archiviazione, Esplora file
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524609"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="e771a-104">Salvataggio e ricerca dei file</span><span class="sxs-lookup"><span data-stu-id="e771a-104">Saving and finding your files</span></span>

<span data-ttu-id="e771a-105">I file possono essere salvati e gestiti in modo analogo ad altri dispositivi Windows 10 desktop e mobile:</span><span class="sxs-lookup"><span data-stu-id="e771a-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="e771a-106">Uso dell'app Esplora file per accedere alle cartelle locali</span><span class="sxs-lookup"><span data-stu-id="e771a-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="e771a-107">All'interno dell'archiviazione di un'app</span><span class="sxs-lookup"><span data-stu-id="e771a-107">Within an app's own storage</span></span>
* <span data-ttu-id="e771a-108">In una cartella nota speciale (ad esempio, video o Music Library)</span><span class="sxs-lookup"><span data-stu-id="e771a-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="e771a-109">Uso di un servizio di archiviazione che include un'app e un selettore file (ad esempio OneDrive)</span><span class="sxs-lookup"><span data-stu-id="e771a-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="e771a-110">Uso di un PC desktop connesso a HoloLens tramite USB, tramite il supporto MTP (Media Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="e771a-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="e771a-111">Esplora file</span><span class="sxs-lookup"><span data-stu-id="e771a-111">File Explorer</span></span>

<span data-ttu-id="e771a-112">È possibile usare l'app Esplora file per spostare ed eliminare i file dall'interno di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e771a-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="e771a-113">Se non viene visualizzato alcun file in Esplora file, il filtro "recente" potrebbe essere attivo (l'icona di clock è evidenziata nel riquadro sinistro).</span><span class="sxs-lookup"><span data-stu-id="e771a-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="e771a-114">Per risolvere il problema, selezionare l'icona del documento del **dispositivo** nel riquadro sinistro (sotto l'icona di clock) oppure aprire il menu e selezionare il **dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="e771a-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="e771a-115">File all'interno di un'app</span><span class="sxs-lookup"><span data-stu-id="e771a-115">Files within an app</span></span>

<span data-ttu-id="e771a-116">Se un'applicazione salva i file nel dispositivo, è possibile usare tale applicazione per accedervi.</span><span class="sxs-lookup"><span data-stu-id="e771a-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="e771a-117">Dove sono le foto e i video?</span><span class="sxs-lookup"><span data-stu-id="e771a-117">Where are my photos/videos?</span></span>

<span data-ttu-id="e771a-118">Le foto e i video di [acquisizione della realtà mista](mixed-reality-capture.md) vengono salvati nella cartella del rullo della fotocamera del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e771a-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="e771a-119">È possibile accedervi tramite l' [app Photos](see-your-photos.md#photos-app).</span><span class="sxs-lookup"><span data-stu-id="e771a-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="e771a-120">È possibile usare l'app Photos per sincronizzare le foto e i video con OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e771a-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="e771a-121">Puoi anche accedere alle tue foto e ai tuoi video tramite la pagina di acquisizione di realtà mista del [portale per dispositivi Windows](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="e771a-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="e771a-122">Richiesta di file da un'altra app</span><span class="sxs-lookup"><span data-stu-id="e771a-122">Requesting files from another app</span></span>

<span data-ttu-id="e771a-123">Un'applicazione può richiedere il salvataggio di un file o l'apertura di un file da un'altra app tramite la [selezione di file](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="e771a-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="e771a-124">Cartelle note</span><span class="sxs-lookup"><span data-stu-id="e771a-124">Known folders</span></span>

<span data-ttu-id="e771a-125">HoloLens supporta una serie di [cartelle note](app-model.md#known-folders) che le app possono richiedere l'autorizzazione per l'accesso.</span><span class="sxs-lookup"><span data-stu-id="e771a-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="e771a-126">File in un servizio</span><span class="sxs-lookup"><span data-stu-id="e771a-126">Files in a service</span></span>

<span data-ttu-id="e771a-127">Per salvare un file o accedere a file da un servizio, è necessario installare l'app associata al servizio.</span><span class="sxs-lookup"><span data-stu-id="e771a-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="e771a-128">Per salvare i file e accedere ai file da OneDrive, è necessario installare l' [app OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="e771a-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="e771a-129">MTP (Media Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="e771a-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="e771a-130">Analogamente ad altri dispositivi mobili, connettere HoloLens al PC desktop e aprire Esplora file nel computer per accedere alle librerie HoloLens (foto, video, documenti) per un trasferimento semplice.</span><span class="sxs-lookup"><span data-stu-id="e771a-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="e771a-131">Chiarimenti</span><span class="sxs-lookup"><span data-stu-id="e771a-131">Clarifications</span></span>

* <span data-ttu-id="e771a-132">HoloLens non supporta la connessione a dischi rigidi esterni o schede SD.</span><span class="sxs-lookup"><span data-stu-id="e771a-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="e771a-133">A partire da [Windows 10 aprile 2018 Update (RS4) per HoloLens](release-notes-april-2018.md), HoloLens include Esplora file per il salvataggio e la gestione dei file sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e771a-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="e771a-134">L'aggiunta di Esplora file consente inoltre di scegliere la selezione file, ad esempio il salvataggio di un file nel dispositivo o in OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e771a-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
