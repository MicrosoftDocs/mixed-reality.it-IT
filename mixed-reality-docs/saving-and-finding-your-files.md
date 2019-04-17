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
# <a name="saving-and-finding-your-files"></a>Salvataggio e trovare i file

I file possono essere salvati e gestiti in modo analogo ad altri Windows 10 Desktop e dispositivi mobili:
* Usa l'app Esplora File per accedere alle cartelle locali
* All'interno di una risorsa di archiviazione dell'app
* In una cartella speciale nota (ad esempio la libreria musica o video)
* Utilizzo di un servizio di archiviazione che include una selezione di app e file (ad esempio OneDrive)
* Usando un computer desktop connesso a di HoloLens tramite USB, tramite il supporto di MTP (Media Transfer Protocol)

## <a name="file-explorer"></a>Esplora file

È possibile usare l'app Esplora File per spostare ed eliminare file dall'interno di HoloLens.

>[!NOTE]
>Se non viene visualizzato di tutti i file in Esplora File, il filtro "Recenti" può essere attivo (icona dell'orologio viene evidenziato nel riquadro a sinistra). Per risolvere questo problema, selezionare la **questa periferica** icona nel riquadro a sinistra (sotto l'icona di orologio), di documento o aprire il menu e selezionare **This Device**.

## <a name="files-within-an-app"></a>File all'interno di un'app

Se un'applicazione consente di salvare file nel dispositivo, è possibile utilizzare tale applicazione per accedere a essi.

### <a name="where-are-my-photosvideos"></a>Dove si trovano le foto/video personali?

[Acquisizione di realtà mista](mixed-reality-capture.md) foto e video vengono salvati nella cartella di eseguire il rollback della fotocamera del dispositivo. È possibile accedervi tramite il [app foto](see-your-photos.md#photos-app). È possibile utilizzare l'app foto per sincronizzare le foto e video in OneDrive. È possibile accedere anche le tue foto e video tramite la pagina dell'acquisizione di realtà mista il [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).

### <a name="requesting-files-from-another-app"></a>Richieste di file da un'altra app

Un'applicazione può richiedere per salvare un file o aprire un file da un'altra app tramite [selettori file](app-model.md#file-pickers).

## <a name="known-folders"></a>Cartelle note

HoloLens supporta numerosi [noto cartelle](app-model.md#known-folders) che le app possono richiedere l'autorizzazione per accedere.

## <a name="files-in-a-service"></a>File in un servizio

Per salvare un file (o accedere ai file da) un servizio, l'app associata con il servizio deve essere installato. Per salvare i file e accedere ai file da OneDrive, è necessario installare il [app OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).

## <a name="mtp-media-transfer-protocol"></a>MTP (Media Transfer Protocol)

Analogamente ad altri dispositivi mobili, connettersi HoloLens sul PC desktop e aprire Esplora File nel PC per accedere a raccolte di HoloLens (foto, video, documenti) per trasferimento dati.

## <a name="clarifications"></a>Chiarimenti

* HoloLens non supporta la connessione a dischi rigidi esterni o schede SD.
* A partire il [Windows 10 April 2018 Update (RS4) per HoloLens](release-notes-april-2018.md), HoloLens include Esplora File per il salvataggio e gestione dei file sul dispositivo. L'aggiunta di Esplora File offre inoltre la possibilità di scegliere il selettore file (ad esempio per salvare un file nel dispositivo o a OneDrive).
