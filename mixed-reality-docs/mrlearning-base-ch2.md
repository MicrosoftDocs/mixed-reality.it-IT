---
title: Esercitazioni introduttive - 3. Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376138"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Creazione dell'interfaccia utente e configurazione di Mixed Reality Toolkit
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

Nell'esercitazione precedente hai appreso alcune delle funzionalità offerte da Mixed Reality Toolkit (MRTK) avviando la tua prima applicazione per HoloLens 2. In questa esercitazione apprenderai come creare e organizzare i pulsanti con i pannelli di testo dell'interfaccia utente e come usare l'interazione predefinita (tocco) per interagire con ogni pulsante. Potrai inoltre esplorare alcuni effetti e azioni semplici, ad esempio la modifica delle dimensioni, del suono e del colore degli oggetti. Questo modulo presenterà i concetti di base relativi alla modifica dei profili di MRTK, a partire dalla disabilitazione della visibilità della mesh di [mapping spaziale](spatial-mapping.md).

## <a name="objectives"></a>Obiettivi

* Personalizzare e configurare i profili di Mixed Reality Toolkit
* Interagire con gli ologrammi usando pulsanti ed elementi dell'interfaccia utente
* Eseguire interazioni e input di tracciamento delle mani

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Come configurare i profili di Mixed Reality Toolkit (modifica dell'opzione di visualizzazione della mesh di consapevolezza spaziale)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

In questa sezione apprenderai come personalizzare e configurare i profili di MRTK predefiniti.

Questo particolare esempio mostrerà come nascondere la mesh di consapevolezza spaziale cambiando le impostazioni dell'osservatore della mesh spaziale. Puoi comunque adottare gli stessi principi per personalizzare le impostazioni o i valori nei profili di MRTK.

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

Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) imposta **Configuration Profile** (Profilo di configurazione) di Mixed Reality Toolkit su **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

Con l'oggetto **MixedRealityToolkit** ancora selezionato, nella finestra Inspector (Controllo) fai clic sul pulsante **Copy & Customize** (Copia e personalizza) per aprire la finestra Clone Profile (Clona profilo):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

Nella finestra Clone Profile (Clona profilo) fai clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultHololens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

Il profilo di configurazione appena creato viene ora assegnato come profilo di configurazione per la scena:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

Nel menu di Unity scegli **File** > **Save** (Salva) per salvare la scena.

> [!TIP]
> Ricorda di salvare il lavoro durante l'esercitazione.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Abilitare il sistema di consapevolezza spaziale

Con l'oggetto **MixedRealityToolkit** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) seleziona la scheda **Spatial Awareness** (Consapevolezza spaziale) e quindi seleziona la casella di controllo **Enable Spatial Awareness System** (Abilita sistema di consapevolezza spaziale):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonare il profilo predefinito del sistema di consapevolezza spaziale

Nella scheda **Spatial Awareness** (Consapevolezza spaziale) fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

Nella finestra Clone Profile (Clona profilo) fai clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

Il profilo del sistema di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo di configurazione:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonare il profilo predefinito dell'osservatore della mesh di consapevolezza spaziale

Con la scheda **Spatial Awareness** (Consapevolezza spaziale) ancora selezionata, espandi la sezione **Windows Mixed Reality Spatial Mesh Observer** (Osservatore mesh spaziale Windows Mixed Reality) e quindi fai clic sul pulsante **Clone** (Clona) per aprire la finestra Clone Profile (Clona profilo):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

Nella finestra Clone Profile (Clona profilo) fai clic sul pulsante **Clone** (Clona) per creare una copia modificabile di **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

Il profilo dell'osservatore della mesh di consapevolezza spaziale appena creato viene ora assegnato automaticamente al profilo del sistema di consapevolezza spaziale:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Modificare la visibilità della mesh di consapevolezza spaziale

In **Spatial Mesh Observer Settings** (Impostazioni osservatore della mesh spaziale) imposta **Display Option** (Opzione di visualizzazione) su **Occlusion** (Occlusione) per rendere invisibile la mesh di mapping spaziale mentre è ancora funzionante:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> Anche se non è visibile, la mesh di mapping spaziale è comunque presente e funzionante. Ad esempio, gli ologrammi dietro la mesh di mapping spaziale, come nel caso di un ologramma dietro a un muro fisico, non saranno visibili.

hai appreso come modificare un'impostazione nel profilo di MRTK. Come puoi notare, per personalizzare le impostazioni di MRTK devi prima creare copie dei profili predefiniti. Poiché i profili predefiniti non sono modificabili, li avrai sempre come riferimento se vuoi ripristinare le impostazioni predefinite. Per altre informazioni sui profili di MRTK e sulla loro architettura, puoi consultare la [guida alla configurazione dei profili di Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Movimenti di tracciamento delle mani e pulsanti con supporto per interazioni

In questa sezione apprenderai come usare il tracciamento della mano per premere un pulsante e attivare eventi in modo da generare un'azione alla pressione del pulsante.

Questo particolare esempio mostrerà come cambiare il colore di un cubo quando il pulsante viene premuto e come ripristinare il colore originale quando il pulsante viene rilasciato. Puoi comunque adottare gli stessi principi per creare altri eventi.

Di seguito sono elencati i passaggi principali da eseguire per cambiare il colore del cubo:

1. Aggiungere alla scena il prefab di un pulsante a pressione
2. Aggiungere un cubo alla scena
3. Configurare il tipo di evento InteractableOnPressReceiver
4. Configurare il cubo per la ricezione dell'evento On Press
5. Definire l'azione che deve essere attivata dall'evento On Press
6. Configurare il cubo per la ricezione dell'evento On Release
7. Definire l'azione che deve essere attivata dall'evento On Release
8. Testare il pulsante usando la simulazione nell'editor

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. Aggiungere alla scena il prefab di un pulsante a pressione

> [!TIP]
> Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> è un GameObject preconfigurato che viene archiviato come asset Unity e può essere riutilizzato nel progetto.

Nella finestra **Project** (Progetto) cerca **PressableButtonHoloLens2** per individuare il prefab che verrà usato per questo esempio:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

Nel risultato visualizzato nell'area **Search** (Ricerca) seleziona il prefab **PressableButtonHoloLens2** e **trascinalo** nella finestra **Hierarchy** (Gerarchia) per aggiungerlo alla scena:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> Per visualizzare la scena come illustrato nell'immagine seguente, fai doppio clic sull'oggetto PressableButtonHoloLens2 nella finestra Hierarchy (Gerarchia) per attivarlo e quindi usa <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo della scena), nell'angolo superiore destro della finestra della scena, per impostare l'angolo di visualizzazione lungo l'asse Z in avanti.

Con l'oggetto **PressableButtonHoloLens2** ancora selezionato, nella finestra **Inspector** (Controllo):

* Modifica il valore di **Position** (Posizione) per Transform (Trasformazione) in modo da posizionare l'oggetto davanti alla fotocamera, che si trova in corrispondenza dell'origine, ad esempio x = 0, y = 0 e z = 0.5

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> In generale, 1 unità di posizione in Unity equivale quasi a 1 metro nel mondo fisico. Vi sono tuttavia eccezioni, ad esempio quando gli oggetti sono figli di oggetti ridimensionati.

### <a name="2-add-a-cube-to-the-scene"></a>2. Aggiungere un cubo alla scena

Fai clic con il pulsante destro del mouse in un punto vuoto all'interno della finestra Hierarchy (Gerarchia) e seleziona **3D Object** (Oggetto 3D)  >  **Cube** per aggiungere un cubo alla scena:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

Con l'oggetto **Cube** ancora selezionato, nella finestra **Inspector** (Controllo):

* Modifica il valore di **Position** (Posizione) per Transform (Trasformazione) in modo da posizionare il cubo vicino al pulsante a pressione, ma senza sovrapposizioni, ad esempio x = 0, y = 0.04 e z = 0.5
* Modifica il valore di **Scale** (Ridimensiona) per Transform (Trasformazione) impostando una dimensione appropriata, ad esempio x = 0.02, y = 0.02 e z = 0.02

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. Configurare il tipo di evento InteractableOnPressReceiver

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **PressableButtonHoloLens2** e quindi nel **menu hamburger** della finestra **Inspector** (Controllo) seleziona **Collapse All Components** (Comprimi tutti i componenti) per ottenere una panoramica di tutti i componenti dell'oggetto:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

Espandi il componente **Interactable (Script)** e quindi individua ed espandi la sezione **Events** (Eventi) > **Receivers** (Ricevitori):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

Fai clic sul pulsante **Add Event** (Aggiungi evento) per creare un nuovo ricevitore di eventi di tipo **InteractableOnPressReceiver**:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> Il tipo di ricevitore di eventi denominato InteractableOnPressReceiver consente al pulsante di rispondere a un evento di pressione quando una mano tracciata preme il pulsante.

Per il ricevitore di eventi appena creato, modifica il valore di **Interaction Filter** (Filtro interazioni) impostandolo su **Near and Far** (Vicino e lontano):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. Configurare il cubo per la ricezione dell'evento On Press

Dalla finestra Hierarchy (Gerarchia) **fai clic e trascina** l'oggetto **Cube** nel campo dell'oggetto **Event Properties** (Proprietà evento) per l'evento **On Press ()** in modo da assegnare il cubo come ricevitore dell'evento On Press ():

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. Definire l'azione che deve essere attivata dall'evento On Press

Fai clic sull'elenco a discesa dell'azione, attualmente impostato su **No Function** (Nessuna funzione), e quindi seleziona **MeshRenderer** > **Material material** (Materiale fisico) per impostare la proprietà del materiale del cubo da modificare quando viene attivato l'evento On Press ():

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

Fai clic sulla piccola icona a forma di **cerchio** accanto al campo del materiale, attualmente impostata su **None (Material)** (Nessuno - Materiale), per aprire la finestra Select Material (Seleziona materiale):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

Nella finestra Select Material (Seleziona materiale) **cerca** **MRTK_Standard** e seleziona un materiale appropriato, ad esempio **MRTK_Standard_Cyan**, in modo che il colore del cubo venga modificato in ciano quando viene premuto il pulsante:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. Configurare il cubo per la ricezione dell'evento On Release

**Ripeti** il passaggio 4 per l'evento On Release per assegnare l'oggetto **Cube** come ricevitore dell'evento **On Release ()** .

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. Definire l'azione che deve essere attivata dall'evento On Release

**Ripeti** il passaggio 5 per l'evento On Release, ma scegli il materiale **MRTK_Standard_LightGray** in modo da ripristinare il colore grigio chiaro originale del cubo quando viene rilasciato il pulsante:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. Testare il pulsante usando la simulazione nell'editor

Premi il pulsante **Play** (Riproduci) per attivare la modalità di gioco e usa la simulazione di input nell'editor in modo da testare il pulsante appena configurato.

Pulsante non premuto (barra spaziatrice + rotellina del mouse all'indietro):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

Pulsante premuto (barra spaziatrice + rotellina del mouse in avanti):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> Per informazioni sulla procedura di simulazione di input nell'editor, puoi fare riferimento alla guida [Uso della simulazione di input manuale nell'editor per testare una scena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creazione di un pannello di pulsanti con il componente Grid Object Collection di MRTK

In questa sezione apprenderai come allineare automaticamente più pulsanti in un'interfaccia utente pulita usando il componente Grid Object Collection di MRTK.

Questo particolare esempio mostrerà come creare un pannello con cinque pulsanti allineati orizzontalmente. Puoi tuttavia seguire gli stessi principi per creare altri layout.

Di seguito sono elencati i passaggi principali da eseguire per ottenere questo risultato:

1. Associare gli oggetti pulsante a un oggetto padre
2. Aggiungere e configurare il componente Grid Object Collection (Script)
3. Testare i pulsanti usando la simulazione nell'editor

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. Associare gli oggetti pulsante a un oggetto padre

Fai clic con il pulsante destro del mouse in un punto vuoto all'interno della finestra Hierarchy (Gerarchia) e seleziona **Create Empty** (Crea vuoto):

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

Fai clic con il pulsante destro del mouse sull'oggetto appena creato, seleziona **Rename** (Rinomina) e assegnagli un nome appropriato, ad esempio **ButtonCollection**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

Seleziona l'oggetto **PressableButtonHoloLens2** e **trascinalo** sopra l'oggetto **ButtonCollection** per impostarlo come figlio dell'oggetto ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

Fai clic con il pulsante destro del mouse sull'oggetto **PressableButtonHoloLens2** e seleziona **Duplicate** (Duplica) per crearne una copia:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**Ripeti** questo passaggio altre quattro volte fino a ottenere un totale di cinque oggetti PressableButtonHoloLens2.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Aggiungere e configurare il componente Grid Object Collection (Script)

Con l'oggetto ButtonCollection selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) fai clic sul pulsante **Add Component** (Aggiungi componente) e quindi cerca e seleziona **Grid Object Collection** (Raccolta oggetti griglia) per aggiungere un componente Grid Object Collection (Script) all'oggetto ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

Configura il componente Grid Object Collection (Script) nel modo seguente:

* Imposta **Num Rows** (Numero righe) su 1 per avere tutti i pulsanti allineati su una sola riga
* Imposta **Cell Width** (Larghezza celle) su 0.05 per spaziare i cubi all'interno della riga

Fai quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per applicare la nuova configurazione:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> Le modifiche di configurazione appena applicate rappresentano le modifiche minime necessarie per raggiungere l'obiettivo di posizionare i pulsanti su una sola riga. Nei progetti futuri, tuttavia, a seconda di fattori come l'orientamento degli oggetti padre e figlio, potrebbe essere necessario modificare altre impostazioni, ad esempio il tipo di orientamento. Per altre informazioni sul componente Grid Object Collection di MRTK, puoi consultare la guida relativa agli [script per la raccolta di oggetti](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

Con l'oggetto ButtonCollection ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) modifica il valore di **Position** (Posizione) per Transform (Trasformazione) in modo che gli oggetti pulsante figlio siano posizionati davanti alla fotocamera, che si trova in corrispondenza dell'origine, ad esempio in x = 0, y = 0 e z = 0.5:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> Quando hai aggiunto per la prima volta il prefab PressableButtonHoloLens2 alla scena nella sezione precedente [Movimenti di tracciamento delle mani e pulsanti con supporto per interazioni](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons), lo hai posizionato davanti alla fotocamera. Tuttavia, poiché il componente Grid Object Collection controlla la posizione degli oggetti figlio immediati, la posizione Z degli oggetti figlio PressableButtonHoloLens2 è stata reimpostata su 0 in base alla distanza predefinita di Grid Object Collection dal valore padre 0. Questo è il motivo, insieme alla necessità di mantenere organizzata la relazione posizionale padre/figlio, per cui abbiamo spostato in avanti la posizione dell'oggetto ButtonCollection padre anziché configurare la distanza dal valore padre per spostare in avanti gli oggetti figlio PressableButtonHoloLens2.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. Testare i pulsanti usando la simulazione nell'editor

Fai clic sul pulsante Play (Riproduci) per attivare la modalità di gioco e usa la simulazione di input nell'editor per testare ogni pulsante nel pannello appena creato:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> Attualmente, quando premi uno dei cinque pulsanti, il colore del cubo diventa ciano. Per rendere più interessante l'esperienza, usa le informazioni appena apprese per configurare ogni pulsante in modo da assegnare un colore diverso al cubo.

## <a name="adding-text-into-your-scene"></a>Aggiunta di testo nella scena

In questa sezione apprenderai come aggiungere testo alle esperienze di realtà mista usando TextMesh Pro di Unity, che hai preparato nella sezione [Importare le risorse essenziali TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) dell'esercitazione precedente.

In questo particolare esempio aggiungerai un'etichetta semplice sotto la raccolta di pulsanti creata nella sezione precedente.

Fai clic con il pulsante destro del mouse sull'oggetto ButtonCollection e seleziona **3D Object** (Oggetto 3D) > **Text - TextMeshPro** per creare un oggetto di TextMeshPro come figlio dell'oggetto ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Con l'oggetto Text (TMP) di TextMeshPro appena creato ancora selezionato, nella finestra Inspector (Controllo) modifica la posizione e le dimensioni in modo che l'etichetta venga posizionata perfettamente sotto la raccolta di pulsanti, ad esempio:

* Modifica il valore di **Pos Y** per Rect Transform (Trasformazione rettangolo) impostando -0.0425
* Modifica il valore di **Width** (Larghezza) per Rect Transform (Trasformazione rettangolo) impostando 0.24
* Modifica il valore di **Height** (Altezza) per Rect Transform (Trasformazione rettangolo) impostando 0.024

Aggiorna quindi il testo in base a ciò che indica l'etichetta e scegli le proprietà del tipo di carattere, in modo da adattare il testo all'etichetta, ad esempio:

* Modifica il valore di **Text** (Testo) per Text Mesh Pro (Script) impostando Button Collection
* Modifica il valore di **Font Style** (Stile carattere) per Text Mesh Pro (Script) impostando Bold (Grassetto)
* Modifica il valore di **Font Size** (Dimensione carattere) per Text Mesh Pro (Script) impostando 0.2
* Modifica il valore di **Alignment** (Allineamento) impostando Center (Al centro) e Middle (In mezzo)

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come clonare, personalizzare e configurare un'impostazione di profilo MRTK. Hai inoltre appreso come interagire con i pulsanti per attivare gli eventi usando le mani tracciate sul dispositivo HoloLens 2 e, infine, come creare un'interfaccia utente semplice usando i componenti Grid Object Collection di MRTK e Text Mesh Pro di Unity.

[Esercitazione successiva: 4. Inserimento di contenuto dinamico e uso dei risolutori](mrlearning-base-ch3.md)
