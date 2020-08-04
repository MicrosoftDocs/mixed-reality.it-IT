---
title: Esercitazioni sul cloud di Azure - 4. Integrazione di Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come implementare Ancoraggi nello spazio di Azure in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, Ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: 468ba0d8e9fca85dc266b662f402f5c956dc94bb
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376443"
---
# <a name="4-integrating-azure-spatial-anchors"></a>4. Integrazione di Ancoraggi nello spazio di Azure

In questa esercitazione verrà spiegato come usare **Ancoraggi nello spazio di Azure**. Si archivierà la posizione di un **oggetto tracciato** come oggetto di Ancoraggi nello spazio di Azure. Quindi si eseguirà una query e si presenterà all'utente una freccia guida che punta alla posizione.

## <a name="objectives"></a>Obiettivi

* Acquisire le nozioni di base su Ancoraggi nello spazio di Azure.
* Imparare a impostare la scena per l'uso di Ancoraggi nello spazio di Azure in questo progetto.
* Scoprire come integrare le posizioni di archiviazione e query.

## <a name="understanding-azure-spatial-anchors"></a>Informazioni su Ancoraggi nello spazio di Azure

 **Ancoraggi nello spazio di Azure** fa parte della famiglia di Servizi cloud di Azure e viene utilizzato per salvare posizioni di ancoraggio. Le posizioni di ancoraggio salvate possono essere recuperate in base all'*ID di ancoraggio* dal cloud. Questa posizione di ancoraggio è condivisibile e accessibile da dispositivi multipiattaforma come i dispositivi HoloLens, iOS e Android.

Altre informazioni su [Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/overview).

## <a name="preparing-azure-spatial-anchors"></a>Preparazione di Ancoraggi nello spazio di Azure

Prima di iniziare, è necessario creare una risorsa di ancoraggio nello spazio nel portale di Azure.
Vedere come [creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).

## <a name="preparing-the-scene"></a>Preparazione della scena

In questa sezione verrà illustrato come configurare la scena e apportare le modifiche necessarie.

Nella finestra Project (Progetto) passa a **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

Dalla cartella **Manager** trascinare e rilasciare il prefab **Anchor Manager** (Gestione ancoraggi) nella gerarchia della scena.

Selezionare il GameObject **Anchor Manager** nella gerarchia e nella sezione Inspector (Controllo) si noterà **Spatial Anchor Manager** (Script). Trovare il campo ID account chiave e aggiungere le credenziali che create nel prerequisito nella fase precedente.

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

Ora trovare l'oggetto **Scene Controller** (Controllo scena) nella gerarchia della scena e selezionarlo. Verrà visualizzata la finestra Inspector (Controllo) di **Scene Controller** (Controllo scena).

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

Si osserverà che il campo **Anchor Manager** (Gestione ancoraggi) nel componente **Scene Controller** (Controllo scena) è vuoto. Trascinare **Anchor Manager** (Gestione ancoraggi) da Hierarchy (Gerarchia) nella scena, rilasciarlo nel campo e salvare la scena.

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a>Creare e distribuire l'app in un dispositivo HoloLens 2

Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity. Pertanto, per testare la funzionalità di questo servizio devi distribuire il progetto nel tuo dispositivo.

> [!TIP]
> Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilazione dell'applicazione nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>Eseguire l'app in HoloLens 2 e seguire le istruzioni in-app

### <a name="create-an-anchor-to-store-a-location"></a>Creare un ancoraggio per archiviare una posizione

In questa sezione verrà illustrato come salvare la posizione dell'oggetto.

Eseguire l'applicazione e fare clic su **Set Object** (Imposta oggetto) nel menu principale dell'esperienza.

Specificare il **nome** dell'oggetto da salvare e fare clic su **Set Object** (Imposta oggetto) per proseguire. Per aggiungere altre informazioni sull'oggetto, selezionare l'**immagine** e descrivere l'oggetto.

Per salvare la posizione, fare clic su **Save Location** (Salva posizione)

Viene visualizzato un **puntatore di ancoraggio** che è possibile spostare e posizionare nella posizione da salvare. Successivamente, viene visualizzata una finestra popup di conferma. Se si vuole confermare e salvare la posizione, fare clic su **Yes** (Sì); in caso contrario, è possibile modificare la posizione facendo clic su **No** e selezionando nuovamente la posizione.

Dopo avere confermato la posizione facendo clic su **Yes** (Sì), la posizione e l'ID di ancoraggio verranno salvati nell'archiviazione cloud di Azure. Eseguito il salvataggio, verrà visualizzato il **tag dell'oggetto** nell'ancoraggio con il nome dell'oggetto.

A questo punto, la posizione dell'oggetto è salvata correttamente.

### <a name="query-for-finding-an-anchor-location"></a>Query per trovare una posizione di ancoraggio

Dopo avere salvato la posizione di ancoraggio, è possibile trovarla selezionando **Search Object** (Cerca oggetto) nel menu principale.

Facendo clic su **Search Object** (Cerca oggetto), viene visualizzata una nuova finestra in cui occorre specificare il nome dell'oggetto da cercare.

Immettere il nome dell'oggetto e fare clic su **Search Object** (Cerca oggetto). Se l'oggetto è stato salvato in precedenza ed è presente nel database, si otterrà la scheda dell'oggetto con tutti i dettagli che lo riguardano.

A questo punto è possibile fare clic su **Show Location** (Mostra posizione) per trovare l'oggetto. Dopo avere fatto clic su **Show Location** (Mostra percorso), il sistema eseguirà una query nella risorsa di archiviazione cloud alla ricerca dell'indirizzo dell'oggetto.

Una volta recuperata a posizione, apparirà una **freccia** rivolta verso la posizione dell'oggetto. Seguire il segno della freccia fino a trovare la posizione dell'oggetto.

Una volta trovato l'oggetto, nella parte superiore verrà visualizzato il nome dell'oggetto, il segno della freccia scomparirà e sarà possibile fare clic sul **tag dell'oggetto** per visualizzare i dettagli dell'oggetto.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione è stato illustrato come salvare e recuperare la posizione di un oggetto in HoloLens 2 con Ancoraggi nello spazio di Azure.

Nell'esercitazione finale si imparerà a usare il **Servizio Azure Bot** per aggiungere il linguaggio naturale come nuovo metodo di interazione per l'applicazione.

[Esercitazione successiva: 5. Integrazione del servizio Azure Bot con LUIS](mr-learning-azure-05.md)
