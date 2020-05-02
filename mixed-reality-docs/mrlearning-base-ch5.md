---
title: Esercitazioni introduttive - 6. Esplorazione delle opzioni di input avanzate
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376088"
---
# <a name="6-exploring-advanced-input-options"></a>6. Esplorazione delle opzioni di input avanzate

In questa esercitazione esaminerai alcune opzioni di input avanzate per HoloLens 2, come l'uso di comandi vocali, il movimento di panoramica e il tracciamento oculare.

## <a name="objectives"></a>Obiettivi

* Attivare gli eventi usando comandi vocali e parole chiave
* Usare le mani tracciate per fare una panoramica di trame e oggetti 3D
* Sfruttare le funzionalità di tracciamento oculare di HoloLens 2 per selezionare gli oggetti

## <a name="enabling-voice-commands"></a>Abilitazione dei comandi vocali
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

In questa sezione implementerai un comando vocale per consentire all'utente di riprodurre un suono per l'oggetto Octa. A tale scopo, creerai un nuovo comando vocale e quindi configurerai l'evento in modo che attivi l'azione desiderata quando viene pronunciata la parola chiave del comando vocale.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Clonare il profilo di sistema di input predefinito
2. Clonare il profilo dei comandi vocali predefinito
3. Creare un nuovo comando vocale
4. Aggiungere e configurare il componente Speech Input Handler (Script) (Gestore input vocale - Script)
5. Implementare l'evento Response (Risposta) per il comando vocale

### <a name="1-clone-the-default-input-system-profile"></a>1. Clonare il profilo di sistema di input predefinito

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **MixedRealityToolkit** e quindi nella finestra Inspector (Controllo) seleziona la scheda **Input** e clona **DefaultHoloLens2InputSystemProfile** per sostituirlo con il tuo **profilo di sistema di input** personalizzabile:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione dei profili MRTK, puoi fare riferimento alle istruzioni contenute in [Come configurare i profili di Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

### <a name="2-clone-the-default-speech-commands-profile"></a>2. Clonare il profilo dei comandi vocali predefinito

Espandi la sezione **Speech** (Voce) e clona **DefaultMixedRealitySpeechCommandsProfile** per sostituirlo con il tuo **profilo dei comandi vocali** personalizzabile:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. Creare un nuovo comando vocale

Nella sezione **Speech Commands** (Comandi vocali) fai clic sul pulsante **+ Add a New Speech Command** (+ Aggiungi un nuovo comando vocale) per aggiungere un nuovo comando vocale in fondo all'elenco dei comandi vocali esistenti e quindi nel campo **Keyword** (Parola chiave) immetti una parola o una frase appropriata, ad esempio **Play Music** (Riproduci musica):

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> Se il computer non dispone di un microfono e vuoi provare il comando vocale usando la simulazione nell'editor, puoi assegnare un codice tasto (KeyCode) al comando vocale in modo che tale comando venga attivato quando viene premuto il tasto corrispondente.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. Aggiungere e configurare il componente Speech Input Handler (Script) (Gestore input vocale - Script)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Octa** e aggiungigli il componente **Speech Input Handler (Script)** (Gestore input vocale - Script). Quindi deseleziona la casella di controllo **Is Focus Required** (È necessario lo stato attivo) in modo che l'utente non debba guardare l'oggetto Octa per attivare il comando vocale:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. Implementare l'evento Response (Risposta) per il comando vocale

Nel componente Speech Input Handler (Script) (Gestore input vocale - Script) fai clic sul piccolo pulsante **+** per aggiungere un elemento parola chiave all'elenco delle parole chiave:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

Fai clic sull'**Element 0** (Elemento 0) appena creato per espanderlo e quindi dall'elenco a discesa **Keyword** (Parola chiave) seleziona la parola chiave **Play Music** (Riproduci musica) creata in precedenza:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> L'elenco a discesa Keyword (Parola chiave) viene popolato con le parole chiave definite nell'elenco Speech Commands (Comandi vocali) nel profilo dei comandi vocali.

Crea un nuovo evento **Response ()** (Risposta), configura l'oggetto **Octa** in modo che riceva l'evento, definisci **AudioSource.PlayOneShot** come azione da attivare e assegna un clip audio appropriato al campo **Audio Clip** (Clip audio), ad esempio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> Per rivedere la procedura di implementazione degli eventi e di assegnazione di un clip audio, puoi fare riferimento alle istruzioni contenute in [Implementare l'evento On Touch Started (Avviato al tocco)](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event).

## <a name="the-pan-gesture"></a>Il movimento di panoramica

Il movimento di panoramica è utile per le operazioni di scorrimento del contenuto tramite il dito o la mano. In questo esempio apprenderai innanzitutto come scorrere un'interfaccia utente 2D e quindi come espanderla in modo da poter scorrere una raccolta di oggetti 3D.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Creare un oggetto Quad utilizzabile per la panoramica
2. Aggiungere il componente Near Interaction Touchable (Script) (Toccabile con interazione da vicino - Script)
3. Aggiungere il componente Hand Interaction Pan Zoom (Script) (Zoom panoramica con interazione manuale - Script)
4. Aggiungere il contenuto 2D da scorrere
5. Aggiungere il contenuto 3D da scorrere
6. Aggiungere il componente Move With Pan (Script) (Spostamento con panoramica - Script)

> [!NOTE]
> Il componente Move With Pan (Script) (Spostamento con panoramica - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. Creare un oggetto Quad utilizzabile per la panoramica

Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse su un'area vuota e scegli **3D Object** (Oggetto 3D) > **Quad** per aggiungere un quadrilatero alla scena. Assegnagli un nome appropriato, ad esempio **PanGesture**, e collocalo in una posizione adatta, ad esempio X = 0, Y = -0.2, Z = 2.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Per rivedere come aggiungere alla scena i primitivi di Unity, ad esempio un quadrilatero 3D, puoi fare riferimento alle istruzioni contenute in [Aggiungere un cubo alla scena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene).

Come qualsiasi altra interazione, anche il movimento di panoramica richiede un collisore. Per impostazione predefinita, un oggetto Quad ha un collisore mesh. Tuttavia, questo tipo di collisore non è ideale perché è estremamente sottile. Per facilitare l'interazione tra l'utente e il collisore, il collisore mesh verrà sostituito con un collisore cuboide.

Con l'oggetto PanGesture ancora selezionato, fai clic sull'icona delle **impostazioni** del componente **Mesh Collider** (Collisore mesh) e seleziona **Remove Component** (Rimuovi componente) per rimuovere il collisore mesh:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

Nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere un **Box Collider** (Collisore cuboide) e quindi imposta su 0.15 il valore Z di **Size** (Dimensioni) per rendere più spesso tale collisore:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. Aggiungere il componente Near Interaction Touchable (Script) (Toccabile con interazione da vicino - Script)

Con l'oggetto **PanGesture** ancora selezionato, aggiungigli il componente **Near Interaction Touchable (Script)** (Toccabile con interazione da vicino - Script) e quindi fai clic sui pulsanti **Fix Bounds** (Correggi limiti) e **Fix Center** (Correggi centro) per aggiornare le proprietà relative ai limiti e al centro in locale di tale componente in modo che corrispondano a BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. Aggiungere il componente Hand Interaction Pan Zoom (Script) (Zoom panoramica con interazione manuale - Script)

Con l'oggetto **PanGesture** ancora selezionato, aggiungigli il componente **Hand Interaction Pan Zoom (Script)** (Zoom panoramica con interazione manuale - Script) e quindi seleziona la casella di controllo **Lock Horizontal** (Blocca in orizzontale) per consentire solo lo scorrimento verticale:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. Aggiungere il contenuto 2D da scorrere

Nel pannello Project (Progetto) cerca il materiale **PanContent** e quindi fai clic e trascinalo sulla proprietà Element 0 (Elemento 0) in **Materials** (Materiali) nella sezione Mesh Renderer (Renderer mesh) dell'oggetto **PanGesture**:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

Nella finestra Inspector (Controllo) espandi il componente materiale **PanContent** appena aggiunto e quindi imposta su 0.5 il valore Y di **Tiling** (Affiancamento) in modo che corrisponda al valore X e i riquadri risultino quadrati:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

Se ora passi alla modalità di gioco, puoi provare lo scorrimento del contenuto 2D usando il movimento di panoramica nella simulazione nell'editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. Aggiungere il contenuto 3D da scorrere

Nella finestra Hierarchy (Gerarchia) **crea quattro cubi** come oggetti figlio dell'oggetto **PanGesture** e in Transform (Trasformazione) imposta **Scale** (Scala) su X = 0.15, Y = 0.15, Z = 0.15:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

Per spaziare i cubi in modo uniforme e risparmiare tempo, aggiungi il componente **Grid Object Collection (Script)** (Raccolta oggetti griglia - Script) all'oggetto padre dei cubi, ovvero all'oggetto **PanGesture**, e configura il componente come segue:

* Imposta **Num Rows** (Numero di righe) su 1 per avere tutti i cubi allineati in una sola riga
* Imposta **Cell Width** (Larghezza cella) su 0.25 per spaziare i cubi all'interno della riga

Fai quindi clic sul pulsante **Update Collection** (Aggiorna raccolta) per applicare la nuova configurazione:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. Aggiungere il componente Move With Pan (Script) (Spostamento con panoramica - Script)

Nella finestra Hierarchy (Gerarchia) seleziona tutti gli **oggetti figlio Cube** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Move With Pan (Script)** (Spostamento con panoramica - Script) a tutti i cubi:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> Per rivedere la procedura di selezione di più oggetti nella finestra Hierarchy (Gerarchia), puoi fare riferimento alle istruzioni contenute in [Aggiungere il componente Manipulation Handler (Script) (Gestore manipolazione - Script) a tutti gli oggetti](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects).

Con tutti i cubi selezionati, fai clic e trascina l'oggetto **PanGesture** sul campo **Pan Input Source** (Origine input panoramica):

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> Il component Move With Pan (Script) (Spostamento con panoramica - Script) di ogni cubo resta in ascolto dell'evento Pan Updated (Aggiornato con panoramica) inviato dal componente HandInteractionPanZoom (Script) nell'oggetto PanGesture, assegnato come origine input panoramica nel passaggio precedente, e aggiorna di conseguenza la posizione di ciascun cubo.

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **PanGesture** e quindi nella finestra Inspector (Controllo) **deseleziona** la casella di controllo **Mesh Renderer** (Renderer mesh) per disabilitare tale renderer:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

Se ora passi alla modalità di gioco, puoi provare lo scorrimento del contenuto 3D usando il movimento di panoramica nella simulazione nell'editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>Tracciamento oculare

In questa sezione esaminerai come abilitare il tracciamento oculare nel tuo progetto. Per questo esempio, implementerai la funzionalità in modo da far ruotare lentamente ogni oggetto incluso nella raccolta 3DObjectCollection mentre l'utente posa su di esso uno sguardo fisso e in modo che venga attivato un effetto sonoro quando l'oggetto guardato viene selezionato tramite simulazione del tocco o comando vocale.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere il componente Eye Tracking Target (Script) (Destinazione tracciamento oculare - Script) a tutti gli oggetti di destinazione
2. Aggiungere il componente Eye Tracking Tutorial Demo (Script) (Demo esercitazione tracciamento oculare - Script) a tutti gli oggetti di destinazione
3. Implementare l'evento While Looking At Target (Mentre viene guardata la destinazione)
4. Implementare l'evento On Selected (Alla selezione)
5. Abilitare il tracciamento oculare simulato per le simulazioni nell'editor
6. Abilitare l'input sguardo fisso nelle funzionalità dell'app del progetto di Visual Studio

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. Aggiungere il componente Eye Tracking Target (Script) (Destinazione tracciamento oculare - Script) a tutti gli oggetti di destinazione

Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **3DObjectCollection** e seleziona tutti gli **oggetti figlio**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Eye Tracking Target (Script)** (Destinazione tracciamento oculare - Script) a tutti gli oggetti figlio:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

Con tutti gli **oggetti figlio** ancora selezionati, configura il componente **Eye Tracking Target (Script)** (Destinazione tracciamento oculare - Script) come segue:

* Imposta **Select Action** (Seleziona azione) su **Select** (Seleziona) per definire la selezione come azione di simulazione del tocco per questo oggetto
* Espandi **Voice Select** (Selezione vocale) e imposta su 1 il valore **Size** (Dimensioni) dell'elenco dei comandi vocali e quindi nel nuovo elenco di elementi che viene visualizzato imposta **Element 0** (Elemento 0) su **Select** (Seleziona) per definire la selezione come azione del comando vocale per questo oggetto

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. Aggiungere il componente Eye Tracking Tutorial Demo (Script) (Demo esercitazione tracciamento oculare - Script) a tutti gli oggetti di destinazione

Con tutti gli **oggetti figlio** ancora selezionati, usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Eye Tracking Tutorial Demo (Script)** (Demo esercitazione tracciamento oculare - Script) a tutti gli oggetti figlio:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> Il componente Eye Tracking Target (Script) (Destinazione tracciamento oculare - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. Implementare l'evento While Looking At Target (Mentre viene guardata la destinazione)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cheese** e quindi crea un nuovo evento **While Looking At Target ()** (Mentre viene guardata la destinazione), configura l'oggetto **Cheese** in modo che riceva l'evento e definisci **EyeTrackingTutorialDemo.RotateTarget** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

**Ripeti** per ogni oggetto figlio incluso in 3DObjectCollection.

> [!TIP]
> Per rivedere la procedura di implementazione degli eventi, puoi fare riferimento alle istruzioni contenute in [Movimenti di tracciamento della mano e pulsanti con supporto per interazioni](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

### <a name="4-implement-the-on-selected-event"></a>4. Implementare l'evento On Selected (Alla selezione)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **Cheese** e quindi crea un nuovo evento **On Selected ()** (Alla selezione), configura l'oggetto **Cheese** in modo che riceva l'evento e definisci **EyeTrackingTutorialDemo.BlipTarget** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

**Ripeti** per ogni oggetto figlio incluso in 3DObjectCollection.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. Abilitare il tracciamento oculare simulato per le simulazioni nell'editor

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **MixedRealityToolkit**, quindi nella finestra Inspector (Controllo) seleziona la scheda **Input**, espandi la sezione **Input Data Providers** (Provider di dati di input) e poi la sezione **Input Simulation Service** (Servizio di simulazione input) e infine clona **DefaultMixedRealityInputSimulationProfile** per sostituirlo con il tuo **profilo di simulazione input** personalizzabile:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> Per rivedere la procedura di clonazione dei profili MRTK, puoi fare riferimento alle istruzioni contenute in [Come configurare i profili di Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

Nella sezione **Eye Simulation** (Simulazione oculare) seleziona la casella di controllo **Simulate Eye Position** (Simula posizione oculare) per abilitare la simulazione del tracciamento oculare:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

Se ora passi alla modalità di gioco, puoi provare l'effetto di rotazione e quello sonoro implementati adattando la vista in modo che il cursore tocchi uno degli oggetti e usando l'interazione con la mano o il comando vocale per selezionare l'oggetto:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> Se non hai usato DefaultHoloLens2ConfigurationProfile per clonare il tuo profilo di configurazione MRTK personalizzabile, come illustrato in [Configurare Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), il tracciamento oculare potrebbe non essere abilitato nel tuo progetto e dovrà essere abilitato. A tale scopo, puoi fare riferimento alle istruzioni contenute in [Introduzione al tracciamento oculare in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html).

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. Abilitare l'input sguardo fisso nelle funzionalità dell'app del progetto di Visual Studio

Prima di compilare e distribuire l'app da Visual Studio nel dispositivo, è necessario abilitare l'input sguardo fisso nelle funzionalità dell'app del progetto. A tale scopo, puoi seguire le istruzioni contenute in [Test dell'app Unity su un dispositivo HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2).

## <a name="congratulations"></a>Lezione completata

Hai ora aggiunto alla tua applicazione le funzionalità di base per il tracciamento oculare. Queste azioni sono solo l'inizio del vasto mondo di possibilità offerte dal tracciamento oculare. In questa esercitazione hai anche avuto informazioni su altre funzionalità di input avanzate, ad esempio i comandi vocali e i movimenti di panoramica.

[Lezione successiva: 7. Creazione dell'applicazione di esempio Lunar Module](mrlearning-base-ch6.md)
