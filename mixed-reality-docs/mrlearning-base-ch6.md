---
title: Esercitazioni introduttive-7. Creazione di un'applicazione di esempio del modulo Lunar
description: In questa lezione vengono combinati più concetti appresi dalle lezioni precedenti per creare un'esperienza di esempio univoca.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 3a557be91bee9b98e750ae1546ea1c4b3103298e
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555280"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. creazione di un'applicazione di esempio del modulo Lunar
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

In questa esercitazione vengono combinati più concetti rispetto alle lezioni precedenti per creare un'esperienza di esempio univoca. Si apprenderà come creare un'applicazione di assembly di parti in base alla quale un utente deve usare le mani registrate per scegliere le parti e provare a assemblare un modulo lunare. Si utilizzeranno pulsanti stampabili per attivare e disattivare gli hint di posizionamento, per reimpostare l'esperienza e per avviare il modulo Lunar nello spazio.

Nelle esercitazioni future si continuerà a sviluppare questa esperienza, che include potenti casi d'uso multiutente che sfruttano gli ancoraggi spaziali di Azure per l'allineamento spaziale.

## <a name="objectives"></a>Obiettivi

* Combinare i vari concetti illustrati nelle lezioni precedenti per creare un'esperienza unica
* Apprendere come attivare o disattivare gli oggetti
* Attivare eventi complessi usando i pulsanti a pressione
* Usare la forza e la fisica dei corpi rigidi
* Esplorare l'uso delle descrizioni comandi

## <a name="lunar-module-parts-overview"></a>Cenni preliminari sulle parti del modulo Lunar
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

In questa sezione si creerà un semplice problema di assembly di parti in cui l'obiettivo dell'utente è inserire cinque parti distribuite nella tabella nella posizione corretta nel modulo Lunar.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Aggiungere la prefabbricazione di lanciarazzi alla scena
2. Abilitare la manipolazione degli oggetti per tutte le parti
3. Aggiungere e configurare il componente Demo assembly parti (script)

> [!NOTE]
> Il componente Demo assembly parti (script) non fa parte di MRTK. È stato fornito con le risorse dell'esercitazione.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. aggiungere la prefabbricazione di lanciarazzi alla scena

Nella finestra del progetto passare al **asset** > **MRTK. Esercitazioni. GettingStarted** > **prefabbricati** > cartella **RocketLauncher** , trascinare il prefabbricato **RocketLauncher** nella finestra gerarchia per aggiungerlo alla scena e quindi posizionarlo in una posizione appropriata, ad esempio:

* Posizione di trasformazione X = 1,5, Y =-0,4, Z = 0, in modo che venga posizionata a destra dell'utente all'altezza della vita
* Rotazione della trasformazione X = 0, Y = 180, Z = 0, quindi le funzionalità principali dell'esperienza sono relative all'utente

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. abilitare la manipolazione degli oggetti per tutte le parti

Nella finestra gerarchia individuare l'oggetto RocketLauncher > **LunarModuleParts** e selezionare tutti gli **oggetti figlio**, aggiungere il componente **gestione manipolazione (script)** e il componente **near Interaction (script** ), quindi configurare il gestore di manipolazione (script) come indicato di seguito:

* Deselezionare la casella di controllo **Consenti modifiche a distanza** per consentire solo l'interazione near
* Modificare il **tipo di manipolazione a due passi** per **spostare la rotazione** in modo che la scalabilità sia disabilitata

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> Per un promemoria, con le istruzioni dettagliate su come implementare la manipolazione degli oggetti, è possibile fare riferimento alle istruzioni di [manipolazione degli oggetti 3D](mrlearning-base-ch4.md#manipulating-3d-objects) .

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. aggiungere e configurare il componente Demo assembly parte (script)

Con tutti gli oggetti figlio LunarModuleParts ancora selezionati, aggiungere un componente di **origine audio** , quindi configurarlo come segue:

* Assegnare un clip audio adatto al campo **AudioClip** , ad esempio MRKT_Scale_Start
* Deselezionare la casella di controllo **Riproduci in** modo non attivo, quindi il clip audio non viene riprodotto automaticamente quando viene caricata la scena
* Modificare **Blend spaziale** su 1 per abilitare l'audio spaziale

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Con tutti gli oggetti figlio LunarModuleParts ancora selezionati, aggiungere il componente **demo assembly parti (script)** :

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

Nella finestra gerarchia selezionare l'oggetto **RoverEnclosure** e configurare il componente **demo assembly parte (script)** come indicato di seguito:

* All'oggetto **da inserire** nel campo, assegnare l'oggetto **stesso**, in questo caso l'oggetto RoverEnclosure
* Per il campo **percorso da inserire** , assegnare l'oggetto **PlacementHints** corrispondente, in questo caso l'oggetto RoverEnclosure_PlacementHint
* Nel campo dell' **oggetto** descrizione comando assegnare la **Descrizione comando**corrispondente, in questo caso l'oggetto RoverEnclosure_ToolTip
* Nel campo **origine audio** assegnare l'oggetto **stesso**, in questo caso l'oggetto RoverEnclosure

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Ripetere** per ognuno degli altri oggetti figlio LunarModuleParts, ad esempio serbatoio, EnergyCell, DockingPortal e ExternalSensor.

Se a questo punto si immette la modalità di gioco e si sposta un'oggetto per posizionarlo ' vicino alla posizione corrispondente, si noterà quanto segue:

* L'oggetto verrà inserito e associato all'oggetto LunarModule in modo che diventi parte del modulo Lunar
* L'origine audio nell'oggetto riprodurrà il clip audio assegnato in corrispondenza della posizione dell'oggetto
* L'oggetto descrizione comando corrispondente verrà nascosto

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Per un promemoria su come usare la simulazione di input nell'editor, è possibile fare riferimento a [usando la simulazione di input manuale in-Editor per testare una](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) Guida alla scena nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Configurazione del modulo lunare

In questa sezione si aggiungeranno altre funzionalità all'applicazione di avvio Rocket in modo che l'utente possa:

* Interagire con il modulo Lunar
* Avviare il modulo Lunar nello spazio e riprodurre un suono quando viene avviato
* Reimpostare l'applicazione in modo che il modulo Lunar e tutte le parti vengano nuovamente posizionate nella posizione originale
* Nascondere gli hint di selezione host per rendere più difficile la verifica dell'assembly della parte.

Di seguito sono riportati i passaggi principali da eseguire per ottenere questo risultato:

1. Abilita manipolazione oggetti
2. Abilita fisica
3. Aggiungere un componente di origine audio
4. Aggiungere e configurare il componente Launch Lunar Module (script)
5. Aggiungere e configurare il componente di attivazione/disinstallazione (script)

> [!NOTE]
> Il componente Launch Lunar Module (script) e il componente di attivazione/disinstallazione (script) non fanno parte di MRTK. Sono state fornite con le risorse dell'esercitazione.

### <a name="1-enable-object-manipulation"></a>1. abilitare la manipolazione degli oggetti

Nella finestra gerarchia selezionare l'oggetto RocketLauncher > **LunarModule** , aggiungere il componente **gestore di manipolazione (script)** e il componente **near Interaction (script)** , quindi configurare il gestore di manipolazione (script) come indicato di seguito:

* Deselezionare la casella di controllo **Consenti modifiche a distanza** per consentire solo l'interazione near
* Modificare il **tipo di manipolazione a due passi** per spostare la rotazione in modo che la scalabilità sia disabilitata

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. abilitare la fisica

Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungere un componente **Rigidbody** e quindi configurarlo come segue:

* Deselezionare la casella di controllo **USA gravità** per evitare che il modulo Lunar venga influenzato dalla gravità
* Controllare la casella di controllo **è cinematica** , in modo che il modulo Lunar inizialmente non sia influenzato dalle forze fisiche

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. aggiungere un componente di origine audio

Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungere un componente di **origine audio** e quindi configurarlo come segue:

* Modificare **Blend spaziale** su 1 per abilitare l'audio spaziale

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. aggiungere e configurare il componente Launch Lunar Module (script)

Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungere il componente **Launch Lunar Module (script)** , quindi configurarlo come segue:

* Modificare il valore di **Spinta** in modo che il modulo lunare si avvicini normalmente all'avvio, ad esempio, a 0,01

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. aggiungere e configurare il componente di attivazione/disinstallazione (script)

Con l'oggetto RocketLauncher > **LunarModule** ancora selezionato, aggiungere il componente **interruttore selezione host (script)** e quindi configurarlo come segue:

* Impostare la proprietà **dimensione** matrice oggetto gioco su 5
* Assegnare ognuno degli **oggetti figlio** dell'oggetto RocketLauncher > LunarModule > **PlacementHints** al campo di un **elemento** nella matrice di oggetti del gioco:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Configurazione del pulsante Launch

Nella finestra gerarchia selezionare i pulsanti RocketLauncher > > oggetto **LaunchButton** , quindi, nel componente **pulsante stampabile (script)** , creare un nuovo evento **premuto ()** , configurare l'oggetto **LunarModule** per ricevere l'evento e definire **LaunchLunarModule. StartThruster** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> Per un promemoria su come implementare gli eventi, è possibile fare riferimento alle istruzioni per i [movimenti di rilevamento della mano e i pulsanti interagiscono](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .

Con i pulsanti di > RocketLauncher > oggetto **LaunchButton** ancora selezionato, nel **componente pulsante stampabile (script)** , creare un nuovo **evento premuto ()** , configurare l'oggetto **LunarModule** per ricevere l'evento, definire **audiosource. PlayOneShot** come azione da attivare e assegnare una clip audio adatta al campo **clip** audio, ad esempio il clip audio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Con i pulsanti di > RocketLauncher > oggetto **LaunchButton** ancora selezionato, nel componente **pulsante stampabile (script)** , creare un nuovo evento **touch end ()** , configurare l'oggetto **LunarModule** per ricevere l'evento e definire **LaunchLunarModule. StopThruster** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Se si immette la modalità di gioco e si preme il pulsante Launch (Avvia), si noterà la riproduzione del clip audio. Se si tiene premuto il pulsante Launch (avvio) per circa un secondo o più, verrà visualizzato lo spazio del lancio del modulo Lunar:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Configurazione del pulsante Reimposta

Nella finestra gerarchia selezionare i pulsanti RocketLauncher > > oggetto **ResetButton** , quindi, nel componente **pulsante stampabile (script)** , creare un nuovo evento **premuto ()** , configurare l'oggetto **LunarModule** per ricevere l'evento e definire **LaunchLunarModule. ResetModule** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Con i pulsanti di > RocketLauncher > oggetto **ResetButton** ancora selezionato, nel **componente pulsante stampabile (script)** , creare un nuovo **evento premuto ()** , configurare l'oggetto **RocketLauncher** per ricevere l'evento, definire **GameObject. BroadcastMessage** come azione da attivare e immettere **ResetPlacement** nel campo messaggio:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> L'azione GameObject. BroadcastMessage invia il messaggio ResetPlacement dall'oggetto RocketLauncher a tutti i relativi oggetti figlio. Qualsiasi oggetto figlio con la funzione ResetPlacement, definito nel componente Demo assembly parti (script) aggiunto a tutti gli oggetti figlio LunarModuleParts, richiama la funzione ResetPlacement che reimposta la posizione dell'oggetto figlio.

Se si immette la modalità di gioco, spostare alcune parti e/o avviare il modulo lunare, quindi premere il pulsante Reimposta per visualizzare le parti e/o il modulo lunare da ripristinare nella posizione originale:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Configurazione del pulsante degli hint di selezione host
<!-- TODO: Rename to 'Configuring the Hints button'-->

Nella finestra gerarchia selezionare i pulsanti RocketLauncher > > oggetto **HintsButton** , quindi, nel componente **pulsante stampabile (script)** , creare un nuovo evento **premuto ()** , configurare l'oggetto **LunarModule** per ricevere l'evento e definire **TogglePlacementHints. ToggleGameObjects** come azione da attivare:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Se si immette la modalità di gioco, si noterà che gli hint di selezione host traslucidi sono disabilitati per impostazione predefinita, ma è possibile attivarli e disattivarli premendo il pulsante hint:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Complimenti

Questa applicazione è stata configurata completamente. A questo punto, l'applicazione consente agli utenti di assemblare completamente il modulo Lunar, avviare il modulo Lunar, attivare o disabilitare i suggerimenti e reimpostare l'applicazione in modo che venga riavviata.
