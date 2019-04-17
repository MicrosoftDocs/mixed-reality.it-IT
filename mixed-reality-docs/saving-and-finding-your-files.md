---
title: Salvataggio e trovare i file
description: Come trovare, salvare e condividere file su HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: procedure, selezione dei file, file, foto, video, immagini, OneDrive, archiviazione, Esplora file
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602683"
---
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="7d785-104">Salvataggio e trovare i file</span><span class="sxs-lookup"><span data-stu-id="7d785-104">Saving and finding your files</span></span>

<span data-ttu-id="7d785-105">I file possono essere salvati e gestiti in modo analogo ad altri Windows 10 Desktop e dispositivi mobili:</span><span class="sxs-lookup"><span data-stu-id="7d785-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="7d785-106">Usa l'app Esplora File per accedere alle cartelle locali</span><span class="sxs-lookup"><span data-stu-id="7d785-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="7d785-107">All'interno di una risorsa di archiviazione dell'app</span><span class="sxs-lookup"><span data-stu-id="7d785-107">Within an app's own storage</span></span>
* <span data-ttu-id="7d785-108">In una cartella speciale nota (ad esempio la libreria musica o video)</span><span class="sxs-lookup"><span data-stu-id="7d785-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="7d785-109">Utilizzo di un servizio di archiviazione che include una selezione di app e file (ad esempio OneDrive)</span><span class="sxs-lookup"><span data-stu-id="7d785-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="7d785-110">Usando un computer desktop connesso a di HoloLens tramite USB, tramite il supporto di MTP (Media Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="7d785-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="7d785-111">Esplora file</span><span class="sxs-lookup"><span data-stu-id="7d785-111">File Explorer</span></span>

<span data-ttu-id="7d785-112">È possibile usare l'app Esplora File per spostare ed eliminare file dall'interno di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7d785-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="7d785-113">Se non viene visualizzato di tutti i file in Esplora File, il filtro "Recenti" può essere attivo (icona dell'orologio viene evidenziato nel riquadro a sinistra).</span><span class="sxs-lookup"><span data-stu-id="7d785-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="7d785-114">Per risolvere questo problema, selezionare la **questa periferica** icona nel riquadro a sinistra (sotto l'icona di orologio), di documento o aprire il menu e selezionare **This Device**.</span><span class="sxs-lookup"><span data-stu-id="7d785-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="7d785-115">File all'interno di un'app</span><span class="sxs-lookup"><span data-stu-id="7d785-115">Files within an app</span></span>

<span data-ttu-id="7d785-116">Se un'applicazione consente di salvare file nel dispositivo, è possibile utilizzare tale applicazione per accedere a essi.</span><span class="sxs-lookup"><span data-stu-id="7d785-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="7d785-117">Dove si trovano le foto/video personali?</span><span class="sxs-lookup"><span data-stu-id="7d785-117">Where are my photos/videos?</span></span>

<span data-ttu-id="7d785-118">[Acquisizione di realtà mista](mixed-reality-capture.md) foto e video vengono salvati nella cartella di eseguire il rollback della fotocamera del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d785-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="7d785-119">È possibile accedervi tramite il [app foto](see-your-photos.md#photos-app).</span><span class="sxs-lookup"><span data-stu-id="7d785-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="7d785-120">È possibile utilizzare l'app foto per sincronizzare le foto e video in OneDrive.</span><span class="sxs-lookup"><span data-stu-id="7d785-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="7d785-121">È possibile accedere anche le tue foto e video tramite la pagina dell'acquisizione di realtà mista il [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="7d785-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="7d785-122">Richieste di file da un'altra app</span><span class="sxs-lookup"><span data-stu-id="7d785-122">Requesting files from another app</span></span>

<span data-ttu-id="7d785-123">Un'applicazione può richiedere per salvare un file o aprire un file da un'altra app tramite [selettori file](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="7d785-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="7d785-124">Cartelle note</span><span class="sxs-lookup"><span data-stu-id="7d785-124">Known folders</span></span>

<span data-ttu-id="7d785-125">HoloLens supporta numerosi [noto cartelle](app-model.md#known-folders) che le app possono richiedere l'autorizzazione per accedere.</span><span class="sxs-lookup"><span data-stu-id="7d785-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="7d785-126">File in un servizio</span><span class="sxs-lookup"><span data-stu-id="7d785-126">Files in a service</span></span>

<span data-ttu-id="7d785-127">Per salvare un file (o accedere ai file da) un servizio, l'app associata con il servizio deve essere installato.</span><span class="sxs-lookup"><span data-stu-id="7d785-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="7d785-128">Per salvare i file e accedere ai file da OneDrive, è necessario installare il [app OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="7d785-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="7d785-129">MTP (Media Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="7d785-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="7d785-130">Analogamente ad altri dispositivi mobili, connettersi HoloLens sul PC desktop e aprire Esplora File nel PC per accedere a raccolte di HoloLens (foto, video, documenti) per trasferimento dati.</span><span class="sxs-lookup"><span data-stu-id="7d785-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="7d785-131">Chiarimenti</span><span class="sxs-lookup"><span data-stu-id="7d785-131">Clarifications</span></span>

* <span data-ttu-id="7d785-132">HoloLens non supporta la connessione a dischi rigidi esterni o schede SD.</span><span class="sxs-lookup"><span data-stu-id="7d785-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="7d785-133">A partire il [Windows 10 April 2018 Update (RS4) per HoloLens](release-notes-april-2018.md), HoloLens include Esplora File per il salvataggio e gestione dei file sul dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d785-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="7d785-134">L'aggiunta di Esplora File offre inoltre la possibilità di scegliere il selettore file (ad esempio per salvare un file nel dispositivo o a OneDrive).</span><span class="sxs-lookup"><span data-stu-id="7d785-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
