---
title: Ancoraggi nello spazio di Azure in Unreal
description: Panoramica della creazione di Ancoraggi nello spazio di Azure nel motore Unreal.
author: hferrone
services: azure-spatial-anchors
ms.author: v-haferr
ms.date: 07/01/2020
ms.topic: tutorial
ms.service: azure-spatial-anchors
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, sviluppo di azure, ancoraggi nello spazio, realtà mista, sviluppo, funzionalità, nuovo progetto, emulatore, documentazione, guide, ologrammi, sviluppo di giochi
ms.openlocfilehash: c7189407bea4b38e7305f0dda7637b82d3325704
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377346"
---
# <a name="azure-spatial-anchors-in-unreal"></a>Ancoraggi nello spazio di Azure in Unreal

## <a name="overview"></a>Panoramica

Ancoraggi nello spazio di Azure è un servizio di Realtà mista di Microsoft che consente ai dispositivi di realtà aumentata di individuare, condividere e salvare in modo permanente i punti di ancoraggio nel mondo fisico. La documentazione seguente fornisce istruzioni utili per l'integrazione del servizio Ancoraggi nello spazio di Azure in un progetto Unreal. Per altre informazioni, vedere il [servizio Ancoraggi nello spazio di Azure](https://azure.microsoft.com/services/spatial-anchors/).

> [!IMPORTANT]
> Gli ancoraggi locali vengono archiviati nel dispositivo, mentre i dati relativi ad Ancoraggi nello spazio di Azure vengono archiviati nel cloud. Se si vuole archiviare gli ancoraggi in locale in un dispositivo, è disponibile il documento [Ancoraggi nello spazio locali](unreal-spatial-anchors.md) che fornisce informazioni dettagliate per l'esecuzione del processo. Si noti che è possibile includere ancoraggi locali e ancoraggi di Azure nello stesso progetto senza che si verifichino conflitti.

## <a name="prerequisites"></a>Prerequisiti

Per completare le procedure contenute in questa guida, verificare che siano soddisfatti i requisti seguenti:

- Installato [Unreal versione 4.25](https://www.unrealengine.com/get-now) o successiva
- [Progetto HoloLens 2](unreal-uxt-ch1.md) configurato in Unreal 
- Leggere la sezione [Panoramica di Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/overview)
- Nozioni di base su C++ e Unreal

## <a name="getting-azure-spatial-anchors-account-info"></a>Recupero delle informazioni sull'account di Ancoraggi nello spazio di Azure

Prima di usare Ancoraggi nello spazio di Azure nel progetto, è necessario:
* [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) e copiare i campi dell'account elencati di seguito. Questi valori vengono usati per autenticare gli utenti con l'account dell'applicazione:
    * **ID account**
    * **Chiave dell'account**

Per altre informazioni, vedere la documentazione relativa all'[autenticazione di Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp).

> [!NOTE]
> Ancoraggi nello spazio di Azure in Unreal 4.25 non supporta i token di autenticazione di Azure AD. Il supporto per questa funzionalità, tuttavia, sarà disponibile in una versione successiva.

## <a name="adding-azure-spatial-anchors-plugins"></a>Aggiunta di plug-in di Ancoraggi nello spazio di Azure

Abilitare i plug-in di Ancoraggi nello spazio di Azure nell'editor Unreal nel modo seguente:
1. Fare clic su **Edit > Plugins** (Modifica > Plug-in) e cercare **AzureSpatialAnchors** e **AzureSpatialAnchorsForWMR**.
2. Selezionare la casella di controllo **Enabled** (Abilitato) di entrambi i plug-in per consentire l'accesso alle librerie del progetto di Ancoraggi nello spazio di Azure nell'applicazione.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-01.png)

Al termine, riavviare l'editor Unreal per rendere effettive le modifiche apportate ai plug-in. Il progetto è ora pronto per l'uso di Ancoraggi nello spazio di Azure.

## <a name="starting-a-spatial-anchors-session"></a>Avvio di una sessione di Ancoraggi nello spazio
Una sessione di Ancoraggi nello spazio di Azure consente alle applicazioni client di comunicare con il servizio Ancoraggi nello spazio di Azure. È necessario creare e avviare una sessione di Ancoraggi nello spazio di Azure per creare, salvare in modo permanente e condividere Ancoraggi nello spazio di Azure:

1. Aprire il progetto per il pedone che si sta usando nell'applicazione.
2. Aggiungere due variabili di stringa per **ID account** e **Chiave dell'account** e quindi assegnare i valori corrispondenti dell'account di Ancoraggi nello spazio di Azure per eseguire l'autenticazione della sessione.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-02.png)

Avviare una sessione di Ancoraggi nello spazio di Azure nel modo seguente:
1. Verificare che nell'applicazione HoloLens sia in esecuzione un'istanza di **AR Session** (Sessione AR) poiché la sessione di Ancoraggi nello spazio di Azure non può essere avviata fino a quando non è in esecuzione una sessione AR. [Creare un asset di sessione AR](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset) se non ne è stato configurato nessuno.
2. Aggiungere l'evento personalizzato **Start Azure Spatial Anchors Session** (Avvia sessione di Ancoraggi nello spazio di Azure) e configurarlo nel modo illustrato nello screenshot seguente.
    * La creazione di una sessione non determina l'avvio della sessione per impostazione predefinita, che consente allo sviluppatore di configurare la sessione per l'autenticazione con il servizio Ancoraggi nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. Configurare la sessione di Ancoraggi nello spazio di Azure per specificare **ID account** e **Chiave dell'account**.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. Avviare la sessione di Ancoraggi nello spazio di Azure, consentendo all'applicazione di creare e individuare Ancoraggi nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-05.png)

Quando non si usa più il servizio, è consigliabile pulire le risorse di Ancoraggi nello spazio di Azure presenti nel progetto Event Graph (Grafico eventi):

1. Arrestare la sessione di Ancoraggi nello spazio di Azure. La sessione non sarà più in esecuzione, ma le risorse associate saranno ancora presenti nel plug-in di Ancoraggi nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. Eliminare la sessione di Ancoraggi nello spazio di Azure per eseguire la pulizia di tutte le risorse della sessione ancora note al plug-in di Ancoraggi nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-07.png)

Il progetto Event Graph (Grafico eventi) dovrebbe avere un aspetto simile allo screenshot seguente:

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a>Creazione di un ancoraggio
Un ancoraggio nello spazio di Azure rappresenta una posa del mondo fisico nello spazio della applicazione di realtà aumentata, che blocca il contenuto della realtà aumentata nelle posizioni del mondo fisico. È anche possibile condividere Ancoraggi nello spazio di Azure tra diversi utenti. Questa condivisione consente al contenuto della realtà aumentata progettato su dispositivi diversi di essere posizionato come nel mondo fisico. 

Per creare un nuovo ancoraggio nello spazio di Azure:
1. Verificare che sia in esecuzione una sessione di Ancoraggi nello spazio di Azure. L'applicazione non può creare o salvare in modo permanente un ancoraggio nello spazio di Azure quando non è in esecuzione alcuna sessione di Ancoraggi nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. Creare oppure ottenere un **[componente scena](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** di Unreal di cui deve essere salvata la posizione in modo permanente. 
    * Nell'immagine seguente il componente **Scene Component Needing Anchor** (Componente scena con necessità di ancoraggio) viene usato come variabile. È necessario un componente scena Unreal per stabilire una trasformazione globale dell'applicazione per un [segnaposto AR](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) e un ancoraggio nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-10.png)

Per costruire e salvare un ancoraggio nello spazio di Azure per un componente scena Unreal:
1. Chiamare [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) (Componente segnaposto) per il componente scena Unreal e specificare **World Transform** (Trasformazione globale) come trasformazione globale usata per il segnaposto AR.
    * Unreal tiene traccia dei punti AR nello spazio dell'applicazione con i segnaposto AR, usati per creare un ancoraggio nello spazio di Azure. In Unreal un segnaposto AR è analogo a un ancoraggio nello spazio di HoloLens.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. Chiamare **Create Cloud Anchor** (Crea ancoraggio cloud) usando il segnaposto AR appena creato.
    * La chiamata a Create Cloud Anchor (Crea ancoraggio cloud) consente di creare un ancoraggio nello spazio di Azure in locale, ma non nel servizio Ancoraggi nello spazio di Azure. È possibile impostare i parametri relativi all'ancoraggio nello spazio di Azure, ad esempio una data di scadenza, prima di creare l'ancoraggio nello spazio di Azure con il servizio.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. Impostare la scadenza dell'ancoraggio nello spazio di Azure. Il parametro Lifetime (Durata) di questa funzione consente allo sviluppatore di specificare l'intervallo di tempo in secondi durante il quale l'ancoraggio deve essere mantenuto dal servizio.
    * Ad esempio, per una durata di una settimana è richiesto un valore di 60 secondi x 60 minuti x 24 ore x sette giorni = 604.800 secondi.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-13.png)

Dopo aver impostato i parametri di ancoraggio, dichiarare l'ancoraggio come pronto per il salvataggio. Nell'esempio seguente, l'ancoraggio nello spazio di Azure appena creato viene aggiunto a un set di ancoraggi nello spazio di Azure per i quali è necessario eseguire il salvataggio. Questo set viene dichiarato come variabile per il progetto Pawn.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a>Salvataggio di un ancoraggio

Dopo aver configurato l'ancoraggio nello spazio di Azure con i parametri, chiamare **Save Cloud Anchor** (Salva ancoraggio cloud). La chiamata a Save Cloud Anchor (Salva ancoraggio cloud) dichiara l'ancoraggio al servizio Ancoraggi nello spazio di Azure. Se la chiamata a Save Cloud Anchor (Salva ancoraggio cloud) ha esito positivo, l'ancoraggio nello spazio di Azure sarà disponibile per altri utenti del servizio Ancoraggi nello spazio di Azure.  

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> Save Cloud Anchor (Salva ancoraggio cloud) è una funzione asincrona e può essere chiamata solo in un evento thread di gioco, ad esempio **EventTick**. È possibile che Save Cloud Anchor (Salva ancoraggio cloud) non venga visualizzata come funzione disponibile tra le funzioni di progetto personalizzate. Dovrebbe essere disponibile, tuttavia, nell'editor del progetto Pawn Event Graph (Grafico eventi Pawn).

Nell'esempio seguente l'ancoraggio nello spazio di Azure viene archiviato in un set durante un callback dell'evento di input. L'ancoraggio viene quindi salvato in EventTick. Per salvare un ancoraggio nello spazio di Azure, possono essere necessari più tentativi a seconda della quantità di dati spaziali creati dalla sessione di Ancoraggi nello spazio di Azure. Per questo motivo è consigliabile controllare se la chiamata di salvataggio ha avuto esito positivo.

Se l'ancoraggio non viene salvato, aggiungerlo nuovamente al set di ancoraggi ancora da salvare. EventTick futuri tenteranno di salvare l'ancoraggio fino a quando non viene archiviato nel servizio Ancoraggi nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-16.png)

Dopo il salvataggio dell'ancoraggio, è possibile usare la trasformazione dei segnaposto AR come trasformazione di riferimento per inserire contenuto nell'applicazione. Altri utenti possono rilevare questo ancoraggio e allineare il contenuto AR per dispositivi diversi nel mondo fisico.

## <a name="deleting-an-anchor"></a>Eliminazione di un ancoraggio

È possibile eliminare gli ancoraggi dal servizio Ancoraggi nello spazio di Azure chiamando **Delete Cloud Anchor** (Elimina ancoraggio cloud).

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> Delete Cloud Anchor (Elimina ancoraggio cloud) è una funzione latente e può essere chiamata solo nel caso di un evento thread di gioco, ad esempio EventTick. È possibile che Delete Cloud Anchor (Elimina ancoraggio cloud) non venga visualizzata come funzione disponibile tra le funzioni di progetto personalizzate. Dovrebbe essere disponibile, tuttavia, nell'editor del progetto Pawn Event Graph (Grafico eventi Pawn).

Nell'esempio seguente l'ancoraggio viene contrassegnato per l'eliminazione in un evento di input personalizzato. L'eliminazione viene quindi tentata in EventTick. Se l'eliminazione dell'ancoraggio non riesce, aggiungere l'ancoraggio nello spazio di Azure al set di ancoraggi contrassegnati per l'eliminazione e riprovare in EventTick successivi.

Il progetto Event Graph (Grafico eventi) dovrebbe ora avere un aspetto simile allo screenshot seguente:

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a>Individuazione di ancoraggi preesistenti

Oltre a creare ancoraggi nello spazio di Azure, è possibile rilevare ancoraggi creati da peer con il servizio Ancoraggi nello spazio di Azure:

1. Ottenere un identificatore di ancoraggio nello spazio di Azure per l'ancoraggio da rilevare.
    * È possibile ottenere un identificatore per un ancoraggio creato dallo stesso dispositivo in una precedente sessione di Ancoraggi nello spazio di Azure. Può anche essere creato e condiviso da dispositivi peer che interagiscono con il servizio Ancoraggi nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. Aggiungere un componente **AzureSpatialAnchorsEvent** al progetto Pawn.
    * Questo componente consente di effettuare la sottoscrizione a diversi eventi di Ancoraggi nello spazio di Azure, ad esempio eventi chiamati quando vengono individuati gli ancoraggi nello spazio di Azure.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. Effettuare la sottoscrizione ad **ASAAnchor Located Delegate** per il componente **AzureSpatialAnchorsEvent**.
    * Il delegato consente all'applicazione di stabilire quando sono stati individuati nuovi ancoraggi associati all'account di Ancoraggi nello spazio di Azure.
    * Con il callback dell'evento, gli ancoraggi nello spazio di Azure creati dai peer con la sessione di Ancoraggi nello spazio di Azure non avranno segnaposto AR creati per impostazione predefinita. Per creare un segnaposto AR per l'ancoraggio nello spazio di Azure rilevato, gli sviluppatori possono chiamare la funzione **Create ARPin Around Azure Cloud Spatial Anchor** (Crea segnaposto AR attorno all'ancoraggio nello spazio cloud di Azure).

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-20.png)

Per individuare gli ancoraggi nello spazio di Azure creati dai peer con il servizio Ancoraggi nello spazio di Azure, l'applicazione dovrà creare un elemento **Azure Spatial Anchors Watcher** (Watcher ancoraggi nello spazio di Azure):
1. Verificare che sia in esecuzione una sessione di Ancoraggi nello spazio di Azure.
2. Creare **AzureSpatialAnchorsLocateCriteria**.
    * È possibile specificare diversi parametri di posizione, ad esempio la distanza dall'utente o la distanza da un altro ancoraggio.
3. Dichiarare in **AzureSpatialAnchorsLocateCritieria** l'identificatore di ancoraggio nello spazio di Azure desiderato.
4. Chiamare **Create Watcher** (Crea Watcher).

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-21.png)

L'applicazione ora inizia a cercare gli ancoraggi nello spazio di Azure noti al servizio Ancoraggi nello spazio di Azure. In altre parole, gli utenti possono individuare gli ancoraggi nello spazio di Azure creati dai relativi peer.

Dopo aver individuato l'ancoraggio nello spazio di Azure, chiamare **Stop Watcher** (Arresta Watcher) per arrestare Azure Spatial Anchors Watcher (Watcher ancoraggi nello spazio di Azure) e pulire le risorse Watcher.

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-22.png)

Il progetto Event Graph (Grafico eventi) finale dovrebbe ora avere un aspetto simile allo screenshot seguente:

![Plug-in di Ancoraggi nello spazio](images/asa-unreal/unreal-spatial-anchors-img-23.png)


## <a name="next-steps"></a>Passaggi successivi
* [Ancoraggi nello spazio locali](unreal-spatial-anchors.md)
* [Documentazione di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/)
* [Funzionalità di Ancoraggi nello spazio](https://azure.microsoft.com/services/spatial-anchors/#features)
* [Linee guida per un'esperienza efficace di gestione degli ancoraggi](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)