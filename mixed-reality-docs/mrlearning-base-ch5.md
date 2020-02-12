---
title: Esercitazioni introduttive-6. Esplorazione delle opzioni di input avanzate
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129662"
---
# <a name="6-exploring-advanced-input-options"></a>6. esplorazione delle opzioni di input avanzate

In questa esercitazione si esamineranno alcune opzioni di input avanzate per HoloLens 2, tra cui l'uso di comandi vocali, movimenti di panoramica e rilevamento degli occhi.

## <a name="objectives"></a>Obiettivi

* Attivare eventi usando comandi vocali e parole chiave
* Usare le mani tracciate per la panoramica delle trame e degli oggetti 3D con le mani rilevate
* Sfruttare le funzionalità di rilevamento degli occhi di HoloLens 2 per selezionare gli oggetti

## <a name="enabling-voice-commands"></a>Abilitazione dei comandi vocali
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

In questa sezione verrà implementato un comando vocale per consentire all'utente di riprodurre un suono nell'oggetto Octa. A tale scopo, si creerà un nuovo comando vocale e quindi si configurerà l'evento in modo da attivare l'azione desiderata quando la parola chiave del comando vocale viene pronunciata.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Clonare il profilo di sistema di input predefinito
2. Clonare il profilo dei comandi vocali predefiniti
3. Crea un nuovo comando vocale
4. Aggiungere e configurare il componente gestore di input vocale (script)
5. Implementare l'evento di risposta per il comando vocale

### <a name="1-clone-the-default-input-system-profile"></a>1. clonare il profilo di sistema di input predefinito

Nella finestra gerarchia selezionare l'oggetto **MixedRealityToolkit** , quindi nella finestra Inspector selezionare la scheda **input** e clonare il **DefaultHoloLens2InputSystemProfile** per sostituirlo con il proprio profilo di **sistema di input**personalizzabile:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> Per un promemoria su come clonare i profili MRTK, è possibile fare riferimento alle istruzioni [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .

### <a name="2-clone-the-default-speech-commands-profile"></a>2. clonare il profilo dei comandi vocali predefiniti

Espandere la sezione **sintesi vocale** e clonare il **DefaultMixedRealitySpeechCommandsProfile** per sostituirlo con un **profilo di comandi vocale**personalizzabile:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. creare un nuovo comando vocale

Nella sezione **comandi vocali** fare clic sul pulsante **+ Aggiungi un nuovo riconoscimento** vocale per aggiungere un nuovo comando vocale nella parte inferiore dell'elenco dei comandi di riconoscimento vocale esistenti, quindi nel campo **parola chiave** immettere una parola o una frase appropriata, ad esempio **Play Music**:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> Se il computer non dispone di un microfono e si vuole testare il comando vocale usando la simulazione in-Editor, è possibile assegnare un KeyCode al comando vocale che consente di attivarlo quando viene premuto il tasto corrispondente.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. aggiungere e configurare il componente gestore di input vocale (script)

Nella finestra gerarchia selezionare l'oggetto **Octa** e aggiungere il componente **gestore di input vocale (script)** all'oggetto Octa. Deselezionare quindi la casella di controllo **è stato attivo obbligatorio** in modo che l'utente non debba esaminare l'oggetto Octa per attivare il comando vocale:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. implementare l'evento di risposta per il comando vocale

Nel componente gestore di input vocale (script) fare clic sul pulsante **+** piccolo per aggiungere una parola chiave e quindi, dall'elenco a discesa **parola chiave** , scegliere la parola chiave **Play Music** creata in precedenza:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> Le parole chiave nell'elenco a discesa della parola chiave vengono popolate in base alle parole chiave definite nell'elenco dei comandi vocali nel profilo dei comandi vocali.

Creare un nuovo evento **Response ()** , configurare l'oggetto **Octa** per ricevere l'evento, definire **audiosource. PlayOneShot** come azione da attivare e assegnare una clip audio adatta al campo **clip** audio, ad esempio, il MRTK_Gem clip audio:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> Per un promemoria sulla modalità di implementazione degli eventi e sull'assegnazione di un clip audio, è possibile fare riferimento alle istruzioni per l'esecuzione di per l' [evento Touch started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) .

## <a name="the-pan-gesture"></a>Il movimento di panoramica

Il gesto Pan è utile per lo scorrimento usando il dito o la mano per scorrere il contenuto. In questo esempio si apprenderà innanzitutto come scorrere un'interfaccia utente 2D e quindi espanderla in modo da poter scorrere una raccolta di oggetti 3D.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Creare un oggetto Quad che può essere usato per la panoramica
2. Aggiungere il componente near Interaction touchable (script)
3. Aggiungere il componente zoom (script) per l'interazione della mano
4. Aggiungere contenuto 2D da scorrere
5. Aggiungi contenuto 3D da scorrere
6. Aggiungere il componente Move with Pan (script)

> [!NOTE]
> Il componente Move with Pan (script) non fa parte di MRTK. È stato fornito con le risorse dell'esercitazione.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. creare un oggetto Quad che può essere usato per la panoramica

Nella finestra gerarchia, fare clic con il pulsante destro del mouse su un'area vuota e selezionare **oggetto 3d** > **Quad** per aggiungere un quad alla scena. Assegnare un nome appropriato, ad esempio **PanGesture**, e posizionarlo in una posizione appropriata, ad esempio X = 0, Y =-0,2, Z = 2.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Per un promemoria su come aggiungere alla scena le primitive Unity, ad esempio un Quad 3D, è possibile fare riferimento alle istruzioni [aggiungere un cubo alla scena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) .

Come per qualsiasi altra interazione, il movimento Pan richiede anche un Collider. Per impostazione predefinita, un quad ha un Collider mesh. Tuttavia, il mesh Collider non è ideale perché è estremamente sottile. Per semplificare l'interazione dell'utente con il Collider, il mesh Collider viene sostituito con un Collider di box.

Con l'oggetto PanGesture ancora selezionato, fare clic sull'icona **delle impostazioni** del componente **mesh Collider** e selezionare **Rimuovi componente** per rimuovere il mesh Collider:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

Nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere un **Collider di box**, quindi modificare le **dimensioni** di box Collider da Z a 0,15 per aumentare lo spessore della casella Collider:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. aggiungere il componente di prossimità interazione (script)

Se l'oggetto **PanGesture** è ancora selezionato, aggiungere il componente **near Interaction (script)** per l'oggetto PanGesture, quindi fare clic sui pulsanti **Correggi limiti** e **Correggi centro** per aggiornare le proprietà del centro locale e dei limiti di near Interaction touchable (script) in modo che corrispondano a BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. aggiungere il componente zoom (script) per l'interazione della mano

Con l'oggetto **PanGesture** ancora selezionato, aggiungere il componente **Zoom Pan (script)** per l'interazione con la mano all'oggetto PanGesture e quindi selezionare la casella di controllo **blocca orizzontalmente** per consentire solo lo scorrimento verticale:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. aggiungere contenuto 2D da scorrere

Nel pannello del progetto cercare il materiale **PanContent** , quindi fare clic su di esso e trascinarlo sulla proprietà elemento 0 del **materiale** renderer di mesh dell'oggetto **PanGesture** :

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

Nella finestra di controllo espandere il componente del materiale **PanContent** appena aggiunto e quindi modificare il valore di **affiancamento** Y in 0,5 in modo che corrisponda al valore X e i riquadri siano quadrati:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

Se si immette la modalità di gioco, è possibile eseguire il test dello scorrimento del contenuto 2D usando il gesto della panoramica nella simulazione dell'Editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. aggiungere il contenuto 3D da scorrere

Nella finestra gerarchia **creare quattro cubi** come oggetti figlio di **PanContent** e impostare la relativa **scala** di trasformazione su X = 0,15, Y = 0,15, Z = 0,15:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

Per spaziare i cubi in modo uniforme e risparmiare tempo, aggiungere il componente Grid Object Collection (script) all'oggetto padre Cubes, ad esempio l'oggetto PanGesture, e configurare la raccolta di oggetti Grid (script) come indicato di seguito:

* Modificare **num Rows** su 1 in modo che tutti i cubi siano allineati in una singola riga
* Modificare la **larghezza della cella** a 0,25 per spaziare i cubi all'interno della riga

Quindi fare clic sul pulsante **Aggiorna raccolta** per applicare la nuova configurazione:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. aggiungere il componente Move with Pan (script)

Nella finestra gerarchia selezionare tutti gli **oggetti figlio del cubo**, quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente **spostamento con panoramica (script)** a tutti i cubi:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> Per un promemoria sulla selezione di più oggetti nella finestra gerarchia, le condizioni possono fare riferimento al [componente Aggiungi il gestore di manipolazione (script) a tutte le istruzioni per gli oggetti](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) .

Con tutti i cubi ancora selezionati, fare clic e trascinare l'oggetto **PanGesture** nel campo **origine input Pan** :

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> Il componente spostamento con Pan (script) in ogni cubo è in ascolto dell'evento di aggiornamento della panoramica inviato dal componente HandInteractionPanZoom (script) nell'oggetto PanGesture, assegnato come origine di input Pan nel passaggio precedente, e aggiorna la posizione di ogni cubo. conseguenza.

Nella finestra gerarchia selezionare l'oggetto **PanGesture** , quindi nella casella di controllo **deseleziona** il **renderer mesh** per disabilitare il componente renderer mesh:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

Se si immette la modalità di gioco, è possibile eseguire il test dello scorrimento del contenuto 3D usando il gesto della panoramica nella simulazione dell'Editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>Tracciamento oculare

In questa sezione si esaminerà come abilitare il rilevamento degli occhi nel progetto. Per questo esempio, si implementerà la funzionalità per fare in modo che ogni oggetto nel 3DObjectCollection si avvii lentamente mentre viene esaminato dallo sguardo dell'utente, nonché attivare un effetto blip quando l'oggetto da esaminare è selezionato tramite il tocco di aria o il comando vocale.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere il componente della destinazione di rilevamento degli occhi (script) a tutti gli oggetti di destinazione
2. Aggiungere il componente Demo dell'esercitazione per la verifica degli occhi (script) a tutti gli oggetti di destinazione
3. Implementare l'oggetto durante la ricerca dell'evento di destinazione
4. Implementa l'evento selezionato
5. Abilitare la verifica degli occhi simulati per le simulazioni in-Editor
6. Abilitare l'input dello sguardo nelle funzionalità dell'app del progetto di Visual Studio

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. aggiungere il componente della destinazione di rilevamento degli occhi (script) a tutti gli oggetti di destinazione

Nella finestra gerarchia espandere l'oggetto **3DObjectCollection** e selezionare tutti gli **oggetti figlio**, quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere il componente di **destinazione di rilevamento degli occhi (script)** a tutti gli oggetti figlio:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

Con tutti gli **oggetti figlio** ancora selezionati, configurare il componente di **destinazione del rilevamento degli occhi (script)** come indicato di seguito:

* Modificare selezionare l' **azione** da **selezionare**per definire l'azione di tocco aereo per questo oggetto come SELECT
* Espandere **voce selezionare** e impostare le **dimensioni** dell'elenco dei comandi vocali su 1 e quindi, nell'elenco nuovo elemento visualizzato, modificare l' **elemento 0** in **Seleziona**per definire l'azione del comando vocale per questo oggetto come SELECT

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. aggiungere il componente Demo dell'esercitazione per la verifica degli occhi (script) a tutti gli oggetti di destinazione

Con tutti gli **oggetti figlio** ancora selezionati, usare il pulsante **Aggiungi componente** per aggiungere il componente Demo dell'esercitazione per la **Verifica degli occhi (script)** a tutti gli oggetti figlio:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> Il componente della destinazione di rilevamento degli occhi (script) non fa parte di MRTK. È stato fornito con le risorse dell'esercitazione.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. implementare durante la ricerca dell'evento di destinazione

Nella finestra gerarchia selezionare l'oggetto **Cheese** , quindi creare un nuovo oggetto durante la ricerca dell'evento **target ()** , configurare l'oggetto **Cheese** per ricevere l'evento e definire **EyeTrackingTutorialDemo. RotateTarget** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

**Ripetere** per ogni oggetto figlio in 3DObjectCollection.

> [!TIP]
> Per un promemoria su come implementare gli eventi, è possibile fare riferimento alle istruzioni per i [movimenti di rilevamento della mano e i pulsanti interagiscono](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .

### <a name="4-implement-the-on-selected-event"></a>4. implementare nell'evento selezionato

Nella finestra gerarchia selezionare l'oggetto **Cheese** , quindi creare un nuovo evento **on Selected ()** , configurare l'oggetto **Cheese** per ricevere l'evento e definire **EyeTrackingTutorialDemo. RotateTarget** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

**Ripetere** per ogni oggetto figlio in 3DObjectCollection.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. abilitare la verifica degli occhi simulati per le simulazioni in-Editor

Nella finestra gerarchia selezionare l'oggetto **MixedRealityToolkit** , quindi nella finestra di controllo selezionare la scheda **input** , espandere la sezione provider di **dati di input** e quindi la sezione del **servizio di simulazione input** e clonare il **DefaultMixedRealityInputSimulationProfile** per sostituirlo con il profilo di **simulazione di input**personalizzabile:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> Per un promemoria su come clonare i profili MRTK, è possibile fare riferimento alle istruzioni [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .

Nella sezione **simulazione degli** occhi, selezionare la casella di controllo **simula la posizione degli** occhi per abilitare la simulazione di rilevamento degli occhi:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

Se si immette la modalità di gioco, è possibile testare gli effetti di rotazione e di selezione implementati regolando la visualizzazione in modo che il cursore raggiunga uno degli oggetti e usando il comando interazione mano o riconoscimento vocale per selezionare l'oggetto:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> Se non è stato usato DefaultHoloLens2ConfigurationProfile per clonare il profilo di configurazione MRTK personalizzabile, come indicato nelle istruzioni [configurare il Toolkit per la realtà mista](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) , la verifica degli occhi potrebbe non essere abilitata nel progetto e sarà necessario abilitarla. A tale proposito, è possibile fare riferimento alla [Guida introduttiva a Eye Tracking nelle istruzioni di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) .

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. abilitare l'input dello sguardo nelle funzionalità dell'app del progetto di Visual Studio

Prima di compilare e distribuire l'app da Visual Studio al dispositivo, è necessario abilitare l'input dello sguardo nelle funzionalità dell'app del progetto. A tale proposito, è possibile seguire le istruzioni per [testare l'app Unity in un HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) .

## <a name="congratulations"></a>Complimenti

Sono state aggiunte le funzionalità di base per la verifica degli occhi all'applicazione. Queste azioni sono solo l'inizio del vasto mondo di possibilità offerte dal tracciamento oculare. In questa esercitazione sono state illustrate anche altre funzionalità di input avanzate, ad esempio i comandi vocali e i movimenti di panoramica.

[Lezione successiva: 7. creazione di un'applicazione di esempio del modulo Lunar](mrlearning-base-ch6.md)
