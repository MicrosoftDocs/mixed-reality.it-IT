---
title: Esercitazioni introduttive - 3. Configurazione dei profili di Mixed Reality Toolkit
description: Questo corso illustra come usare Mixed Reality Toolkit (MRTK) per creare un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: d3381241bb1418fb0e1fb7e5d29d552a533faa32
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376643"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. Configurazione dei profili di Mixed Reality Toolkit

## <a name="overview"></a>Panoramica

In questa esercitazione si apprenderà come personalizzare e configurare i profili di MRTK.

Questo particolare esempio mostrerà come nascondere la mesh di consapevolezza spaziale cambiando le impostazioni dell'osservatore della mesh spaziale. Puoi comunque adottare gli stessi principi per personalizzare le impostazioni o i valori nei profili di MRTK.

## <a name="objectives"></a>Obiettivi

* Imparare a personalizzare e configurare i profili di MRTK
* Nascondere il mesh di consapevolezza spaziale

## <a name="changing-the-spatial-awareness-display-option"></a>Modifica delle opzioni di visualizzazione di consapevolezza spaziale

Di seguito sono elencati i passaggi principali da eseguire per nascondere la mesh di consapevolezza spaziale:

1. Clonare il profilo di configurazione predefinito
2. Abilitare il sistema di consapevolezza spaziale
3. Clonare il profilo predefinito del sistema di consapevolezza spaziale
4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale
5. Modificare la visibilità della mesh di consapevolezza spaziale

> [!NOTE]
> per impostazione predefinita, i profili di MRTK non sono modificabili. Si tratta di modelli di profilo predefiniti che devono essere clonati prima di poter essere modificati. Sono disponibili diversi livelli annidati di profili. È quindi normale clonare e modificare diversi profili quando una o più impostazioni vengono configurate.

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonare il profilo di configurazione predefinito

> [!NOTE]
> Il profilo di configurazione è il profilo di primo livello. Di conseguenza, prima di modificare altri profili, devi clonare il profilo di configurazione.

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) impostare **Configuration Profile** (Profilo di configurazione) di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_HoloLens2ConfigurationProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.

> [!TIP]
> Ricordarsi di salvare il lavoro durante l'esercitazione.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Abilitare il sistema di consapevolezza spaziale

Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) selezionare la scheda **Spatial Awareness** (Consapevolezza spaziale), infine la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonare il profilo predefinito del sistema di consapevolezza spaziale

Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale

Con la scheda **Spatial Awareness** (Consapevolezza spaziale) ancora selezionata, espandi la sezione **Windows Mixed Reality Spatial Mesh Observer** (Osservatore mesh spaziale Windows Mixed Reality) e quindi fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

Nella finestra Clone Profile (Clona profilo) immettere un **nome di profilo** appropriato, ad esempio _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e quindi fare clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Modificare la visibilità della mesh di consapevolezza spaziale

In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) impostare **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante. Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.

hai appreso come modificare un'impostazione nel profilo di MRTK. Come si può notare, per personalizzare le impostazioni di MRTK, è necessario prima creare copie dei profili predefiniti. Poiché i profili predefiniti non sono modificabili, saranno sempre presenti come riferimento in caso di ripristino delle impostazioni predefinite. Per altre informazioni sui profili di MRTK e sulla loro architettura, consultare la [guida alla configurazione dei profili di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come clonare, personalizzare e configurare i profili e le impostazioni di MRTK.

[Esercitazione successiva: 4. Posizionamento degli oggetti nella scena](mr-learning-base-04.md)
