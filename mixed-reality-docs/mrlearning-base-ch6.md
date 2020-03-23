---
title: Esercitazioni introduttive - 7 Creazione di un'applicazione di esempio Lunar Module
description: In questa lezione combinerai i vari concetti appresi nelle lezioni precedenti per creare un'esperienza di esempio unica.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031544"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Creazione di un'applicazione di esempio Lunar Module
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

In questa esercitazione verranno combinati i vari concetti appresi nelle lezioni precedenti per creare un'esperienza di esempio unica. Apprenderai come creare un'applicazione di assembly parti nella quale un utente dovrà usare le mani tracciate per prendere le parti di un modulo lunare e tentare di assemblarlo. Userai pulsanti a pressione per attivare e disattivare i suggerimenti di posizionamento, reimpostare l'esperienza e lanciare il modulo lunare nello spazio.

Nelle esercitazioni successive continuerai a sviluppare questa esperienza, che include efficaci casi d'uso multiutente che sfruttano gli ancoraggi nello spazio di Azure per l'allineamento spaziale.

## <a name="objectives"></a>Obiettivi

* Combinare i vari concetti illustrati nelle lezioni precedenti per creare un'esperienza unica
* Apprendere come attivare o disattivare gli oggetti
* Attivare eventi complessi usando i pulsanti a pressione
* Usare la forza e la fisica dei corpi rigidi
* Esplorare l'uso delle descrizioni comandi

## <a name="lunar-module-parts-overview"></a>Panoramica delle parti del modulo lunare
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

In questa sezione creerai una semplice prova di assembly di parti in cui l'obiettivo dell'utente è inserire nella posizione corretta sul modulo lunare cinque parti sparse sul tavolo.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere il prefab Rocket Launcher (Lanciamissili) alla scena
2. Abilitare la manipolazione degli oggetti per tutte le parti
3. Aggiungere e configurare il componente Part Assembly Demo (Script) (Demo assembly parti - Script)

> [!NOTE]
> Il componente Part Assembly Demo (Script) (Demo assembly parti - Script) non fa parte di MRTK. È stato fornito con gli asset dell'esercitazione.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. Aggiungere il prefab Rocket Launcher (Lanciamissili) alla scena

Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **RocketLauncher**, trascina il prefab **RocketLauncher** nella finestra Hierarchy (Gerarchia) per aggiungerlo alla scena e quindi posizionalo in un punto appropriato, ad esempio:

* Trasforma la posizione X = 1.5, Y = -0.4, Z = 0 in modo che venga posizionato a destra dell'utente all'altezza della vita
* Trasforma la rotazione X = 0, Y = 180, Z = 0 in modo che le funzionalità principali dell'esperienza siano di fronte all'utente

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. Abilitare la manipolazione degli oggetti per tutte le parti

Nella finestra Hierarchy (Gerarchia) individua l'oggetto RocketLauncher > **LunarModuleParts** e seleziona tutti gli **oggetti figlio**, aggiungi i componenti **Manipulation Handler (Script)** (Gestore di manipolazione - Script) e **Near Interaction Grabbable (Script)** (Afferrabile con interazione da vicino - Script) e quindi configura il componente Manipulation Handler (Script) (Gestore di manipolazione - Script) come illustrato di seguito:

* Deseleziona la casella di controllo **Allow Far Manipulation** (Consenti manipolazione da lontano) per consentire solo l'interazione da vicino
* Modifica il campo **Two Handed Manipulation Type** (Tipo di manipolazione a due mani) impostandolo su **Move Rotate** (Spostamento rotazione) in modo da disabilitare il ridimensionamento

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> Per rivedere la procedura di implementazione della manipolazione degli oggetti, con istruzioni dettagliate, puoi fare riferimento alle istruzioni [Manipolare gli oggetti 3D](mrlearning-base-ch4.md#manipulating-3d-objects).

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. Aggiungere e configurare il componente Part Assembly Demo (Script) (Demo assembly parti - Script)

Con tutti gli oggetti figlio di LunarModuleParts ancora selezionati, aggiungi un componente **Audio Source** (Origine audio) e quindi configuralo come indicato di seguito:

* Assegna al campo **AudioClip** un clip audio appropriato, ad esempio MRKT_Scale_Start
* Deseleziona la casella di controllo **Play On Awake** (Riproduci quando operativo) in modo che il clip audio non venga riprodotto automaticamente durante il caricamento della scena
* Modifica il campo **Spatial Blend** (Blend spaziale) impostandolo su 1 per abilitare l'audio spaziale

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Con tutti gli oggetti figlio di LunarModuleParts ancora selezionati, aggiungi il componente **Part Assembly Demo (Script)** (Demo assembly parti - Script):

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **RoverEnclosure** e configura il relativo componente **Part Assembly Demo (Script)** (Demo assembly parti - Script) come indicato di seguito:

* Assegna al campo **Object To Place** (Oggetto da posizionare) l'oggetto **stesso**, in questo caso l'oggetto RoverEnclosure
* Assegna al campo **Location To Place** (Punto di posizionamento) l'oggetto **PlacementHints** corrispondente, in questo caso l'oggetto RoverEnclosure_PlacementHint
* Assegna al campo **Tool Tip Object** (Oggetto descrizione comando) l'oggetto **ToolTip** corrispondente, in questo caso l'oggetto RoverEnclosure_ToolTip
* Assegna al campo **Audio Source** (Origine audio) l'oggetto **stesso**, in questo caso l'oggetto RoverEnclosure

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Ripeti** la procedura per ognuno degli altri oggetti figlio di LunarModuleParts, ad esempio FuelTank, EnergyCell, DockingPortal ed ExternalSensor.

Se a questo punto attivi la modalità di gioco e sposti un oggetto da posizionare vicino al punto di posizionamento corrispondente, noterai quanto segue:

* L'oggetto si bloccherà in posizione e gli verrà assegnato un elemento padre nell'oggetto LunarModule in modo che diventi parte del modulo lunare
* L'origine audio nell'oggetto riprodurrà il clip audio assegnato nella posizione dell'oggetto
* L'oggetto ToolTip corrispondente verrà nascosto

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Per rivedere la procedura di simulazione di input nell'editor, puoi fare riferimento alla guida [Uso della simulazione di input manuale nell'editor per testare una scena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Configurazione del modulo lunare

In questa sezione aggiungerai altre funzionalità all'applicazione Rocket Launcher (Lanciamissili) in modo che l'utente possa:

* Interagire con il modulo lunare
* Lanciare il modulo lunare nello spazio e riprodurre un suono quando viene lanciato
* Reimpostare l'applicazione in modo che il modulo lunare e tutte le parti vengano nuovamente riportati nella posizione originale
* Nascondere i suggerimenti di posizionamento per rendere più difficile la prova di assembly delle parti

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Abilitare la manipolazione degli oggetti
2. Abilitare la fisica
3. Aggiungere un componente Audio Source (Origine audio) all'oggetto
4. Aggiungere e configurare il componente Launch Lunar Module (Script) (Lancia modulo lunare - Script)
5. Aggiungere e configurare il componente Toggle Placement Hints (Script) (Attiva/Disattiva suggerimenti per il posizionamento - Script)

> [!NOTE]
> I componenti Launch Lunar Module (Script) (Lancia modulo lunare - Script) e Toggle Placement Hints (Script) (Attiva/Disattiva suggerimenti per il posizionamento - Script) non fanno parte di MRTK. Sono stati forniti con gli asset dell'esercitazione.

### <a name="1-enable-object-manipulation"></a>1. Abilitare la manipolazione degli oggetti

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RocketLauncher > **LunarModule**, aggiungi i componenti **Manipulation Handler (Script)** (Gestore di manipolazione - Script) e **Near Interaction Grabbable (Script)** (Afferrabile con interazione da vicino - Script) e configura il componente Manipulation Handler (Script) (Gestore di manipolazione - Script) come indicato di seguito:

* Deseleziona la casella di controllo **Allow Far Manipulation** (Consenti manipolazione da lontano) per consentire solo l'interazione da vicino
* Modifica il campo **Two Handed Manipulation Type** (Tipo di manipolazione a due mani) impostandolo su Move Rotate (Spostamento rotazione) in modo da disabilitare il ridimensionamento

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. Abilitare la fisica

Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungi un componente **Rigidbody** e quindi configuralo come indicato di seguito:

* Deseleziona la casella di controllo **Use Gravity** (Usa gravità) in modo che il modulo lunare non sia soggetto a gravità
* Seleziona la casella di controllo **Is Kinematic** (Cinematico) in modo che il modulo lunare non sia soggetto inizialmente alle forze della fisica

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. Aggiungere un componente Audio Source (Origine audio) all'oggetto

Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungi un componente **Audio Source** (Origine audio) e quindi configuralo come indicato di seguito:

* Modifica il campo **Spatial Blend** (Blend spaziale) impostandolo su 1 per abilitare l'audio spaziale

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. Aggiungere e configurare il componente Launch Lunar Module (Script) (Lancia modulo lunare - Script)

Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungi il componente **Launch Lunar Module (Script)** (Lancia modulo lunare - Script) e quindi configuralo come indicato di seguito:

* Modifica il valore di **Thrust** (Spinta) in modo che il modulo lunare possa sollevarsi delicatamente quando viene lanciato, impostandolo ad esempio su 0.01

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. Aggiungere e configurare il componente Toggle Placement Hints (Script) (Attiva/Disattiva suggerimenti per il posizionamento - Script)

Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungi il componente **Toggle Placement Hints (Script)** (Attiva/Disattiva suggerimenti per il posizionamento - Script) e quindi configuralo come indicato di seguito:

* Imposta la proprietà **Size** (Dimensione) della matrice degli oggetti gioco su 5
* Assegna ciascun **oggetto figlio** dell'oggetto RocketLauncher > LunarModule > **PlacementHints** al campo **Element** (Element) nella matrice degli oggetti gioco:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Configurazione del pulsante di lancio

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RocketLauncher > Buttons > **LaunchButton**, quindi nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) crea un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **LunarModule** in modo da ricevere l'evento e definisci **LaunchLunarModule.StartThruster** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> Per rivedere la procedura di implementazione degli eventi, puoi fare riferimento alle istruzioni [Movimenti di tracciamento delle mani e pulsanti con supporto per interazioni](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

Con l'oggetto RocketLauncher > Buttons > **LaunchButton** ancora selezionato, crea nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **LunarModule** in modo da ricevere l'evento, definisci **AudioSource.PlayOneShot** come azione da attivare e assegna al campo **Audio Clip** (Clip audio) un clip audio appropriato, ad esempio il clip audio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Con l'oggetto RocketLauncher > Buttons > **LaunchButton** ancora selezionato, crea nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) un nuovo evento **Touch End ()** (Fine tocco), configura l'oggetto **LunarModule** in modo da ricevere l'evento e definisci **LaunchLunarModule.StopThruster** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Se attivi la modalità di gioco e premi il pulsante di lancio, verrà riprodotto il clip audio. Se tieni premuto il pulsante di lancio per almeno un secondo circa, potrai osservare il lancio del modulo lunare nello spazio:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Configurazione del pulsante di reimpostazione

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RocketLauncher > Buttons > **ResetButton**, quindi nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) crea un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **LunarModule** in modo da ricevere l'evento e definisci **LaunchLunarModule.ResetModule** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Con l'oggetto RocketLauncher > Buttons > **ResetButton** ancora selezionato, crea nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **RocketLauncher** in modo da ricevere l'evento, definisci **GameObject.BroadcastMessage** come azione da attivare e immetti **ResetPlacement** nel campo del messaggio:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> L'azione GameObject.BroadcastMessage invia il messaggio ResetPlacement dall'oggetto RocketLauncher a tutti i relativi oggetti figlio. Gli oggetti figlio con la funzione ResetPlacement, definita nel componente Part Assembly Demo (Script) (Demo assembly parti - Script) aggiunto a tutti gli oggetti figlio LunarModuleParts, richiameranno la funzione ResetPlacement che reimposta la posizione dell'oggetto figlio.

Se attivi ora la modalità di gioco, sposti alcune parti e/o avvii il modulo lunare e quindi premi il pulsante Reimposta, visualizzerai le parti e/o il modulo lunare da reimpostare nella posizione originale:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Configurazione del pulsante dei suggerimenti di posizionamento
<!-- TODO: Rename to 'Configuring the Hints button'-->

Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RocketLauncher > Buttons > **HintsButton**, quindi nel componente **Pressable Button (Script)** (Pulsante a pressione - Script) crea un nuovo evento **Button Pressed ()** (Pulsante premuto), configura l'oggetto **LunarModule** in modo da ricevere l'evento e definisci **TogglePlacementHints.ToggleGameObjects** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Se attivi ora la modalità di gioco, noterai che i suggerimenti di posizionamento traslucidi sono disabilitati per impostazione predefinita, ma puoi attivarli e disattivarli premendo il pulsante Hints (Suggerimenti):

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Lezione completata

Hai configurato completamente questa applicazione. A questo punto, l'applicazione consente agli utenti di assemblare completamente il modulo lunare, lanciarlo, attivare o disattivare i suggerimenti e reimpostare l'applicazione in modo che venga riavviata.
