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
# <a name="saving-and-finding-your-files"></a>Salvataggio e ricerca dei file

I file possono essere salvati e gestiti in modo analogo ad altri dispositivi Windows 10 desktop e mobile:
* Uso dell'app Esplora file per accedere alle cartelle locali
* All'interno dell'archiviazione di un'app
* In una cartella nota speciale (ad esempio, video o Music Library)
* Uso di un servizio di archiviazione che include un'app e un selettore file (ad esempio OneDrive)
* Uso di un PC desktop connesso a HoloLens tramite USB, tramite il supporto MTP (Media Transfer Protocol)

## <a name="file-explorer"></a>Esplora file

È possibile usare l'app Esplora file per spostare ed eliminare i file dall'interno di HoloLens.

>[!NOTE]
>Se non viene visualizzato alcun file in Esplora file, il filtro "recente" potrebbe essere attivo (l'icona di clock è evidenziata nel riquadro sinistro). Per risolvere il problema, selezionare l'icona del documento del **dispositivo** nel riquadro sinistro (sotto l'icona di clock) oppure aprire il menu e selezionare il **dispositivo**.

## <a name="files-within-an-app"></a>File all'interno di un'app

Se un'applicazione salva i file nel dispositivo, è possibile usare tale applicazione per accedervi.

### <a name="where-are-my-photosvideos"></a>Dove sono le foto e i video?

Le foto e i video di [acquisizione della realtà mista](mixed-reality-capture.md) vengono salvati nella cartella del rullo della fotocamera del dispositivo. È possibile accedervi tramite l' [app Photos](see-your-photos.md#photos-app). È possibile usare l'app Photos per sincronizzare le foto e i video con OneDrive. Puoi anche accedere alle tue foto e ai tuoi video tramite la pagina di acquisizione di realtà mista del [portale per dispositivi Windows](using-the-windows-device-portal.md#mixed-reality-capture).

### <a name="requesting-files-from-another-app"></a>Richiesta di file da un'altra app

Un'applicazione può richiedere il salvataggio di un file o l'apertura di un file da un'altra app tramite la [selezione di file](app-model.md#file-pickers).

## <a name="known-folders"></a>Cartelle note

HoloLens supporta una serie di [cartelle note](app-model.md#known-folders) che le app possono richiedere l'autorizzazione per l'accesso.

## <a name="files-in-a-service"></a>File in un servizio

Per salvare un file o accedere a file da un servizio, è necessario installare l'app associata al servizio. Per salvare i file e accedere ai file da OneDrive, è necessario installare l' [app OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).

## <a name="mtp-media-transfer-protocol"></a>MTP (Media Transfer Protocol)

Analogamente ad altri dispositivi mobili, connettere HoloLens al PC desktop e aprire Esplora file nel computer per accedere alle librerie HoloLens (foto, video, documenti) per un trasferimento semplice.

## <a name="clarifications"></a>Chiarimenti

* HoloLens non supporta la connessione a dischi rigidi esterni o schede SD.
* A partire da [Windows 10 aprile 2018 Update (RS4) per HoloLens](release-notes-april-2018.md), HoloLens include Esplora file per il salvataggio e la gestione dei file sul dispositivo. L'aggiunta di Esplora file consente inoltre di scegliere la selezione file, ad esempio il salvataggio di un file nel dispositivo o in OneDrive.
