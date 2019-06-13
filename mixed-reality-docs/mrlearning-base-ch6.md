---
title: Modulo di apprendimento di base sulla realtà mista - Esperienza di esempio di assemblaggio di un modulo lunare
description: In questa lezione combineremo i vari concetti appresi nelle lezioni precedenti per creare un'esperienza di esempio unica.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730852"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>Modulo di apprendimento di base sulla realtà mista - Esperienza di esempio di assemblaggio di un modulo lunare

In questa lezione combineremo i vari concetti appresi nelle lezioni precedenti per creare un'esperienza di esempio unica. Creeremo un'applicazione per l'assemblaggio di un modulo lunare nella quale un utente dovrà usare le mani tracciate per selezionare le parti di un modulo lunare e tentare di assemblarlo. Useremo pulsanti a pressione per attivare o disattivare i suggerimenti di posizionamento, reimpostare l'esperienza e lanciare il modulo lunare nello spazio. Nelle successive esercitazioni continueremo a sviluppare questa esperienza, includendo efficaci casi d'uso multiutente che sfruttano gli ancoraggi nello spazio di Azure per l'allineamento spaziale.

## <a name="objectives"></a>Obiettivi

- Combinare i vari concetti illustrati nelle lezioni precedenti per creare un'esperienza unica
- Apprendere come attivare o disattivare gli oggetti
- Attivare eventi complessi usando i pulsanti a pressione
- Usare la forza e la fisica dei corpi rigidi
- Esplorare l'uso delle descrizioni comandi

## <a name="instructions"></a>Istruzioni

### <a name="configuring-the-lunar-module"></a>Configurazione del modulo lunare

In questo capitolo presenteremo i vari componenti necessari per creare l'esperienza di esempio.

1. Aggiungi il prefab dell'assemblaggio del modulo lunare alla scena di base. A tale scopo, cerca "Rocket Launcher_Tutorial" nella scheda del progetto. Puoi trovare il prefab anche in Assets>BaseModuleAssets>Prefabs. Visualizzerai due prefab per un lanciarazzi: uno denominato "Tutorial" e l'altro denominato "Complete". Trascina il prefab "Rocket Launcher_Tutorial" nella scena di base. Posiziona liberamente il prefab nella scena.
   Nota: il prefab "Rocket Launcher_Complete" è il lanciarazzi completato, disponibile come riferimento. 

![Immagine lezione 6 capitolo 1 passaggio 1](images/Lesson6_Chapter1_step1im.PNG)

Se espandi l'oggetto gioco "Rocket Launcher_Tutorial" nella gerarchia ed espandi ulteriormente l'oggetto "LunarModule", noterai diversi oggetti figlio con un materiale denominato "x-ray". Il materiale "x-ray" attiva un colore semitrasparente che useremo per i suggerimenti di posizionamento per l'utente. 

![Immagine lezione 6 capitolo 1 nota a](images/Lesson6_Chapter1_noteaim.PNG) Il modulo lunare è costituito da cinque parti con cui l'utente può interagire, come illustrato nell'immagine seguente:

1.  Scocca del rover
2.  Serbatoio del carburante
3.  Cella energetica
4.  Portale di ancoraggio 
5.  Sensore esterno

![Immagine lezione 6 capitolo 1 nota b](images/Lesson6_Chapter1_notebim.PNG)

> Nota: i nomi degli oggetti gioco visualizzati nella gerarchia della scena di base non corrispondono ai nomi degli oggetti nella scena.

Passaggio 2: aggiungi un'origine audio al modulo lunare. Assicurati che il modulo lunare sia selezionato nella gerarchia della scena di base e fai clic su "Add Component" (Aggiungi componente). Cerca "Audio Source" (Origine audio) e aggiungi l'origine audio all'oggetto. Per il momento lasciala vuota, verrà usata in un secondo momento per riprodurre il suono del lancio.
 ![Immagine lezione 6 capitolo 1 passaggio 2](images/Lesson6_Chapter1_step2im.PNG) Passaggio 3: aggiungi lo script "Toggle Placement Hints" (Attiva/Disattiva suggerimenti per il posizionamento). Fai clic su "Add Component" (Aggiungi componente) e cerca "Toggle Placement Hints". Questo è uno script personalizzato che consente di attivare e disattivare i suggerimenti semitrasparenti (oggetti con materiale x-ray) indicati in precedenza. 
![Immagine lezione 6 capitolo 1 passaggio 3](images/Lesson6_Chapter1_step3im.PNG) Passaggio 4: poiché sono presenti cinque oggetti, digita "5" per la dimensione della matrice degli oggetti gioco. Vengono quindi visualizzati cinque nuovi elementi. 

![Immagine lezione 6 capitolo 1 passaggio 4b](images/Lesson6_Chapter1_step4bim.PNG)

Trascina ciascuno degli oggetti semitrasparenti nelle caselle di testo denominate "None (Game Object)" (Nessuno - oggetto gioco). Trascina gli oggetti seguenti dal modulo lunare nella scena di base: 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Immagine lezione 6 capitolo 1 passaggio 4a](images/Lesson6_Chapter1_step4aim.PNG)

Ora lo script "Toggle Placement Hints" (Attiva/Disattiva suggerimenti per il posizionamento) è configurato. In questo modo possiamo attivare e disattivare i suggerimenti.

Passaggio 5: aggiungi lo script "Launch Lunar Module" (Lancia modulo lunare). Fai clic sul pulsante "Add Component" (Aggiungi componente), cerca "Launch Lunar Module" e seleziona il componente. Questo script sarà responsabile del lancio del modulo lunare. Quando premi un pulsante configurato, al componente del corpo rigido del modulo lunare verrà aggiunta una forza verso l'alto e il modulo verrà lanciato verso l'alto. In luoghi chiusi, il modulo lunare potrebbe scontrarsi contro il soffitto. In ambienti esterni, volerà all'infinito nello spazio. 

![Immagine lezione 6 capitolo 1 passaggio 5](images/Lesson6_Chapter1_step5im.PNG)

Passaggio 6: regola la spinta in modo che il modulo lunare possa sollevarsi delicatamente. Prova con un valore pari a 0.01. Lascia vuoto il campo "Rb" (Cr). Rb (Cr) è l'acronimo di corpo rigido e questo campo viene popolato automaticamente al runtime.

![Immagine lezione 6 capitolo 1 passaggio 6](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Panoramica delle parti del modulo lunare
L'oggetto padre delle parti del modulo lunare è costituito dalla raccolta di oggetti con cui interagirà l'utente. I nomi degli oggetti gioco (con le etichette della scena tra parentesi) sono specificati nell'elenco seguente:

- Equipaggiamento (Serbatoio del carburante)
- GasTank (Cella energetica)
- TopLeftBody (Scocca del rover)
- Nose (Portale di ancoraggio)
- LeftTwirler (Sensore esterno)

Nota che per ognuno di questi oggetti è definito il gestore di manipolazione, come illustrato nella lezione 4. Con il gestore di manipolazione, gli utenti possono afferrare e manipolare l'oggetto. Tieni presente anche che l'opzione "Two Handed Manipulation Type" (Tipo di manipolazione a due mani) è impostata su "Move and rotate" (Sposta e ruota). Ciò consente all'utente solo di spostare l'oggetto, senza modificarne le dimensioni, che è la funzionalità richiesta per un'applicazione di assemblaggio.
Inoltre, la manipolazione da lontano è deselezionata per consentire solo l'interazione diretta con le parti del modulo.

![Immagine lezione 6 capitolo 2](images/Lesson6_Chapter2im.PNG)

Lo script dimostrativo dell'assemblaggio delle parti (illustrato in precedenza) gestisce gli oggetti che l'utente deve posizionare nel modulo lunare. 

Il campo "Object To Place" (Oggetto da posizionare) è la trasformazione selezionata (nel caso dell'immagine precedente, equipaggiamento/serbatoio del carburante) con l'oggetto a cui può connettersi. 

Le impostazioni "Near Distance" (Distanza ravvicinata) e "Far Distance" (Distanza remota) consentono di determinare la vicinanza alle parti che verranno ancorate o rilasciate. Ad esempio, l'oggetto equipaggiamento/serbatoio del carburante dovrà trovarsi a 0.1 unità dal modulo lunare per essere ancorato. "Far Distance" (Distanza remota) consente di impostare la posizione in cui deve trovarsi l'oggetto per scollegarsi dal modulo lunare. In questo caso, la mano dell'utente deve afferrare l'oggetto equipaggiamento/serbatoio del carburante e spostarlo a 0.2 unità dal modulo lunare per evitare che venga nuovamente ancorato.

"Tool Tip Object" (Oggetto descrizione comando) è l'etichetta della descrizione comando nella scena. Quando gli oggetti sono ancorati, l'etichetta viene disabilitata. 

L'origine audio viene acquisita automaticamente. 

### <a name="placement-hints-buttons"></a>Pulsanti dei suggerimenti per il posizionamento
Nella [lezione 2](mrlearning-base-ch2.md) hai appreso come posizionare e configurare i pulsanti per eseguire operazioni come modificare il colore di un elemento o riprodurre un suono quando il pulsante viene premuto. Useremo questi stessi principi per configurare i pulsanti in modo da attivare o disattivare i suggerimenti di posizionamento. 

L'obiettivo è configurare il pulsante in modo che, a ogni pressione da parte dell'utente, si attivi o disattivi la visibilità dei suggerimenti di posizionamento semitrasparenti. 

Passaggio 1: sposta il modulo lunare nello slot vuoto "Runtime Only" (Solo runtime) nel pannello di controllo, mentre l'oggetto dei suggerimenti per il posizionamento è selezionato nella gerarchia della scena di base. 
 ![Immagine lezione 6 capitolo 3 passaggio 1](images/Lesson6_Chapter3_step1im.PNG) Passaggio 2: fai ora clic sull'elenco a discesa denominato "No Function" (Nessuna funzione). Scorri fino all'opzione "TogglePlacementHints" e seleziona "ToggleGameObjects ()" dal menu. ToggleGameObjects () consente di attivare o disattivare i suggerimenti per il posizionamento, in modo che siano visibili o invisibili ogni volta che il pulsante viene premuto.
 ![Immagine lezione 6 capitolo 3 passaggio 2](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configurazione del pulsante reset

Ci sono casi in cui l'utente commette un errore o accidentalmente elimina l'oggetto o semplicemente vuole reimpostare l'esperienza. Il pulsante reset consentirà di riavviare l'esperienza. 

Passaggio 1: seleziona il pulsante reset. Nella scena di base è denominato "ResetRoundButton". 

Passaggio 2: trascina il modulo lunare dalla gerarchia della scena di base nello slot vuoto in "Button Pressed" (Pulsante premuto) nel pannello di controllo.
 ![Immagine lezione 6 capitolo 4 passaggio 2](images/Lesson6_Chapter4_step2im.PNG)

Passaggio 3: seleziona il menu a discesa denominato "No Function" (Nessuna funzione) e passa il puntatore su "LaunchLunarModule". A questo punto, seleziona "resetModule ()".

![Immagine lezione 6 capitolo 4 passaggio 3](images/Lesson6_Chapter4_step3im.PNG)

> Nota: come puoi notare, per impostazione predefinita, "GameObject.BroadcastMessage" è configurato su "ResetPlacement". Questa opzione consente di trasmettere un messaggio denominato "ResetPlacement" a tutti gli oggetti figlio di Rocket Launcher_Tutorial. Qualsiasi oggetto che dispone di un metodo per "ResetPlacement()" risponderà al messaggio reimpostando la relativa posizione. 

### <a name="launching-the-lunar-module"></a>Lancio del modulo lunare
In questo capitolo illustreremo come configurare il pulsante di lancio. Ciò consentirà all'utente di premere il pulsante e lanciare il modulo lunare nello spazio.

Passaggio 1: seleziona il pulsante di lancio, denominato "LaunchRoundButton" nella scena di base. Trascina il modulo lunare nello slot vuoto dell'area "Touch End" (Fine tocco) del pannello di controllo.
 ![Immagine lezione 6 capitolo 5 passaggio 1](images/Lesson6_Chapter5_step1im.PNG) Passaggio 2: seleziona il menu a discesa denominato "No Function" (Nessuna funzione). Passa il puntatore su "LaunchLunarModule" e seleziona "StopThruster ()". Ciò consente di controllare la spinta che l'utente vuole assegnare al modulo lunare. 
 ![Immagine lezione 6 capitolo 5 passaggio 2](images/Lesson6_Chapter5_step2im.PNG) Passaggio 3: in "ButtonPressed()" aggiungi il modulo lunare (seleziona, tieni premuto e trascina) nello slot vuoto. 

Passaggio 4: fai clic sul menu a discesa denominato "No Function" (Nessuna funzione), passa il puntatore su "LaunchLunarModule" e seleziona "StartThruster ()". 
 ![Immagine lezione 6 capitolo 5 passaggio 4](images/Lesson6_Chapter5_step4im.PNG) Passaggio 5: aggiungi musica al modulo lunare in modo che venga riprodotta al decollo del razzo. A tale scopo, trascina il modulo lunare nello slot vuoto successivo in "ButtonPressed()".

Passaggio 6: seleziona il menu a discesa denominato "No Function" (Nessuna funzione), passa il puntatore su "AudioSource" e seleziona "PlayOneShot (AudioClip)". Esplora la varietà di suoni inclusi in MRTK. Per questo esempio useremo "MRTK_Gem".
 ![Immagine lezione 6 capitolo 5 passaggio 6](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Lezione completata 
Hai configurato completamente questa applicazione. Quando premi il pulsante per la riproduzione, puoi ora assemblare completamente il modulo lunare, attivare o disattivare i suggerimenti, lanciare il modulo lunare e reimpostarlo per ripetere tutta la procedura.
