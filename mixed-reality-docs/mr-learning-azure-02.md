---
title: Esercitazioni sul cloud di Azure - 2. Integrazione di Archiviazione di Azure
description: Completa questo corso per apprendere come implementare Archiviazione tabelle di Azure e Archiviazione BLOB di Azure in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, archiviazione di azure
ms.localizationpriority: high
ms.openlocfilehash: a8d91bc55b3ce73d6e1fb46e5d696d853adcf871
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376473"
---
# <a name="2-integrating-azure-storage"></a>2. Integrazione di Archiviazione di Azure

In questa esercitazione apprenderai come salvare dati di entità in Archiviazione tabelle di Azure e immagini di anteprima in Archiviazione BLOB di Azure. Questa funzionalità consentirà di archiviare e recuperare *oggetti tracciati* con dati come ID, nome, immagine di anteprima e così via tra sessioni e dispositivi nel cloud.

## <a name="objectives"></a>Obiettivi

* Apprendere le nozioni di base relative ad Archiviazione di Azure
* Apprendere come archiviare, modificare e recuperare i dati dall'archiviazione tabelle
* Apprendere come archiviare ed eliminare immagini dall'archiviazione BLOB

## <a name="understanding-azure-storage"></a>Informazioni su Archiviazione di Azure

**Archiviazione di Azure** è una soluzione di archiviazione Microsoft sul cloud in grado di coprire numerosi scenari e requisiti. Si tratta di una soluzione con scalabilità elevata facilmente accessibile per gli sviluppatori. Tutti i servizi possono essere usati con un **account di archiviazione di Azure**. Per questo caso d'uso, verranno usati i servizi *archiviazione tabelle* e *archiviazione BLOB*.

Sono disponibili altre informazioni sui [servizi Archiviazione di Azure](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview).

### <a name="azure-table-storage"></a>Archiviazione tabelle di Azure

Questo servizio consente di archiviare i dati in modalità NoSQL e in questo progetto verrà usato per archiviare informazioni sull'*oggetto tracciato*, ad esempio nome, descrizione, ID ancoraggio nello spazio e altro ancora.

Nel contesto dell'applicazione demo sono necessarie due tabelle, una per archiviare i dati relativi al progetto con informazioni sullo stato dei modelli con training (altre informazioni sono disponibili nell'esercitazione [Integrazione di Visione personalizzata di Azure](mr-learning-azure-03.md)) e una seconda tabella per archiviare le informazioni sugli *oggetti tracciati*.

Sono disponibili altre informazioni su [Archiviazione tabelle di Azure](https://docs.microsoft.com/azure/storage/tables/table-storage-overview).

### <a name="azure-blob-storage"></a>Archiviazione BLOB di Azure

Questo servizio consente di archiviare file binari di grandi dimensioni e lo userai per archiviare le foto acquisite per *oggetti tracciati* come anteprima.
Per l'applicazione demo necessiti di un contenitore BLOB per archiviare le immagini.

Sono disponibili altre informazioni su [Archiviazione BLOB di Azure](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction).

## <a name="preparing-azure-storage"></a>Preparazione di Archiviazione di Azure

Per usare i servizi Archiviazione di Azure, necessiterai di un account di archiviazione di Azure. Per creare un account di archiviazione, vedi [Creare un account di archiviazione](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal). Per altre informazioni sugli account di archiviazione, vedi [Panoramica dell'account di archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview).

Dopo aver creato un account di archiviazione, puoi recuperare dal **portale di Azure** la stringa di connessione, che sarà necessaria nella sezione successiva di questa lezione.

### <a name="optional-azure-storage-explorer"></a>Azure Storage Explorer facoltativo

Sebbene sia possibile visualizzare e verificare tutte le modifiche dall'interfaccia utente all'interno dell'applicazione, è consigliabile installare [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/). Questo strumento consente di visualizzare i dati in Archiviazione di Azure ed è molto utile per il debug e l'apprendimento.

> [!TIP]
> Per i test dall'editor di Unity puoi usare un emulatore locale:

> * in Windows 10 puoi usare l'[emulatore di archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)
> * in MacOS/Linux puoi usare l'[immagine Azurite Docker](https://hub.docker.com/_/microsoft-azure-storage-azurite) per Docker

## <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Hierarchy (Gerarchia) individua l'oggetto **DataManager** e selezionalo.

![mr-learning-azure](images/mr-learning-azure/tutorial2-section4-step1-1.png)

Dalla finestra Inspector (Controllo) noterai che tutte le impostazioni relative ad **Archiviazione di Azure** sono contenute nel componente **DataManager (script)** . Tutte le impostazioni pertinenti sono già impostate, devi solo sostituire il campo della *stringa di connessione* con la stringa che puoi recuperare dal portale di Azure. Se usi una soluzione emulatore di archiviazione di Azure locale, puoi mantenere il valore della *stringa di connessione* già fornita.

Il componente **DataManager (script)** è responsabile della comunicazione con i servizi **archiviazione tabelle** e **archiviazione BLOB** usati da altri script di controllo nei componenti dell'interfaccia utente.

## <a name="writing-and-reading-data-from-azure-table-storage"></a>Scrittura e lettura di dati da Archiviazione tabelle di Azure

Con tutti gli elementi pronti, puoi ora creare un *oggetto tracciato*.

Apri l'applicazione in HoloLens e fai clic su **Set Object** (Imposta oggetto). Potrai osservare il modo in cui l'oggetto *EnterObjectName* diventa attivo nella gerarchia. In questo menu fai clic sulla *barra di ricerca* e digita il nome che desideri assegnare all'*oggetto tracciato*. Dopo aver fornito un nome, fai clic sul pulsante **Set Object** (Imposta oggetto). In Archiviazione tabelle di Azure verrà creato l'*oggetto tracciato* e sarà ora visibile **Object Card** (Scheda oggetto).

**Object Card** (Scheda oggetto) è una rappresentazione dell'interfaccia utente dell'*oggetto tracciato* e svolgerà un ruolo importante più volte in questa serie di esercitazioni.

A questo punto, fai clic sulla *casella di testo* della descrizione e digita "Car", quindi fai clic sul pulsante **Save** (Salva) per salvare le modifiche. Arresta l'applicazione ed eseguila di nuovo.

Fai clic ora su **Search Object** (Cerca oggetto) e digita nella *barra di ricerca* il nome usato in precedenza quando hai creato l'*oggetto tracciato*. Noterai che da **Archiviazione tabelle di Azure** viene recuperato **Object Card** (Scheda oggetto) con tutti i dati.

Sei libero di chiudere **Object Card** (Scheda oggetto) e di creare nuovi *oggetti tracciati* e modificare i relativi dati.

> [!TIP]
> Se hai installato [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/), esamina la tabella degli *oggetti* e vedrai l'*oggetto tracciato* creato.

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>Caricamento e download dell'immagine da Archiviazione BLOB di Azure

In questa sezione userai Archiviazione BLOB di Azure per caricare e scaricare immagini che verranno usate come anteprime per gli *oggetti tracciati*.

> [!NOTE]
> In questa esercitazione l'applicazione acquisirà foto per caricare immagini in archiviazione BLOB. Se esegui questa operazione localmente dall'editor di Unity, assicurati di disporre di una webcam connessa al computer.

Apri l'applicazione in HoloLens, fai clic su **Set Object** (Imposta oggetto) e digita nella *barra di ricerca* il nome "Car". A questo punto dovresti visualizzare **Object Card** (Scheda oggetto). Fai clic sul pulsante **Camera** (Fotocamera) e ti verrà richiesto di eseguire un'operazione AirTap per acquisire una foto. Dopo aver acquisito una foto, visualizzerai un messaggio che ti informa del caricamento attivo e dopo un periodo di tempo dovresti visualizzare l'immagine nel punto in cui precedentemente si trovava il segnaposto.

A questo punto, esegui di nuovo l'applicazione e cerca l'*oggetto tracciato*. L'immagine caricata in precedenza dovrebbe visualizzarsi come anteprima.

## <a name="deleting-image-from-azure-blob-storage"></a>Eliminazione di un'immagine da Archiviazione BLOB di Azure

Nella sezione precedente hai caricato nuove immagini in Archiviazione BLOB di Azure. In questa sezione eliminerai un'anteprima di immagine per gli *oggetti tracciati*.

Apri l'applicazione in HoloLens, fai clic su **Set Object** (Imposta oggetto) e digita nella *barra di ricerca* il nome "Car". A questo punto dovresti visualizzare **Object Card** (Scheda oggetto) con l'immagine di anteprima. Fai clic sul pulsante **Delete** (Elimina). L'immagine di anteprima verrà sostituita dall'immagine segnaposto.

A questo punto, esegui di nuovo l'applicazione e cerca l'*oggetto tracciato* dell'anteprima precedentemente eliminata. Dovresti visualizzare solo l'immagine segnaposto.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come usare i servizi Archiviazione di Azure per salvare in modo permanente dati non strutturati, come in questo caso gli **oggetti tracciati** e i file binari sotto forma di immagini di anteprima per l'applicazione demo **HoloLens 2** nel cloud.

Nell'esercitazione successiva apprenderai come usare Visione personalizzata di Azure per rilevare le immagini associate a un *oggetto tracciato*.

[Esercitazione successiva: 3. Integrazione di Visione personalizzata di Azure](mr-learning-azure-03.md)
