---
title: Modulo di Base Learning MR - modulo lunare Assembly esempio esperienza
description: In questa lezione si combinerà più i concetti appresi delle lezioni precedenti per creare un'esperienza di esempio univoco.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, hololens, esercitazione di unity,
ms.openlocfilehash: 303ed17724ba8799490aa7bca7a60600f6e5349b
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929608"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>Modulo di Base Learning MR - modulo lunare Assembly esempio esperienza

In questa lezione si combinerà più i concetti appresi delle lezioni precedenti per creare un'esperienza di esempio univoco. Si creerà un'applicazione di assembly lunare module in base al quale un utente dovrà usare mani rilevate per prelevare lunare modulo parti e tenta di assemblare un modulo lunare. Si userà pressable pulsanti per attivare o disattivare gli hint di posizionamento, reimpostare la nostra esperienza e per avviare il modulo lunare nello spazio. In futuro le esercitazioni, continueremo a si basano su questa esperienza, tra cui potente con più utenti-casi d'uso che sfrutta gli ancoraggi spaziale di Azure per l'allineamento spaziale.

## <a name="objectives"></a>Obiettivi

- Combinare i concetti più delle lezioni precedenti per creare un'esperienza unica
- Informazioni su come attivare o disattivare gli oggetti
- Attivare eventi complessi usando i pulsanti pressable
- Usare rigidbody fisica e forza
- Esplorare l'uso di descrizioni comandi

## <a name="instructions"></a>Istruzioni

### <a name="configuring-the-lunar-module"></a>Configurazione del modulo lunare

In questo capitolo verranno presentammo per i vari componenti necessari per creare la nostra esperienza di esempio.

1. Aggiungere il prefab assembly lunare modulo alla scena della Base. A tale scopo, nella scheda progetto, cercare "Rocket Launcher_Tutorial". È anche possibile trovare il prefab negli asset > BaseModuleAssets > Prefabs. È possibile visualizzare due rocket dell'utilità di avvio prefabs; uno con il nome "esercitazione di" e l'altro con il nome "completa". Trascinare il prefab "Rocket Launcher_Tutorial" alla scena della Base. È possibile posizionare il posizionamento del prefab nella scena.
   Nota: Il prefab "Rocket Launcher_Complete" è l'utilità di avvio completato, fornito per riferimento. 

![Lesson6 capitolo 1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

Se si espande l'oggetto gioco "Rocket Launcher_Tutorial" nella gerarchia ed espande ulteriormente l'oggetto "Lunare modulo", si noterà diversi oggetti figlio che hanno un materiale chiamato "a raggi x". Il materiale "x-ray" consente un colore semitrasparente leggermente che verrà usato come hint per la selezione host per l'utente. 

![Lesson6 capitolo 1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) costituito da cinque parti al modulo lunare che l'utente sta per interagire, come illustrato nell'immagine seguente:

1.  L'Enclosure spaziale
2.  Il serbatoio
3.  La cella di energia
4.  Il portale di ancoraggio 
5.  Il sensore esterno

![Lesson6 capitolo 1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> Nota: I nomi degli oggetti gioco visualizzato nella gerarchia della scena di base non corrispondono ai nomi degli oggetti nella scena.

Passaggio 2: Aggiungere un'origine audio per il modulo lunare. Assicurarsi che il modulo lunare sia selezionato nella gerarchia della scena di base e fare clic su "Aggiungi componente". Eseguire la ricerca di "Origine Audio" e aggiungerlo all'oggetto. Lasciare vuoto per il momento. Si userà questo riproduce l'audio che avvia l'operazione in un secondo momento.
 ![Lesson6 capitolo 1 Step2im](images/Lesson6_Chapter1_step2im.PNG) passaggio 3: Aggiungere lo script "Attiva/Disattiva hint per la selezione host". Fare clic su "Add Component" e cercare "Attiva/Disattiva hint per la selezione host". Si tratta di uno script personalizzato che consente di attivare e disattivare gli hint semitrasparenti (oggetti con il materiale di x-ray) indicati in precedenza. 
![Lesson6 capitolo 1 Step3im](images/Lesson6_Chapter1_step3im.PNG) passaggio 4: Poiché sono presenti 5 oggetti, digitare "5" per la dimensione della matrice oggetto gioco. È possibile vedere 5 nuovi elementi vengono visualizzati. 

![Lesson6 capitolo 1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

Trascinare ognuno degli oggetti traslucidi nelle caselle di testo "None (Game Object)". Trascinare gli oggetti seguenti dal modulo lunare nella scena base: 

• Zaino

•   GasTank

• Topleftbody

• Naso

•   LeftTwirler

 ![Lesson6 capitolo 1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

Ora è configurato lo script "Attiva/Disattiva hint per la selezione host". Ciò permetterà di attivare e disattivare la gli hint.

Passaggio 5: Aggiungere lo script "avvio modulo lunare". Fare clic sul pulsante "Add Component", cercare "avvio lunare modulo" e selezionarlo. Questo script sarà responsabile dell'avvio del modulo lunare. Quando si preme un pulsante configurato, aggiungerà una forza verso l'alto al componente rigida corpo del modulo lunare e causerà il modulo da avviare verso l'alto. Se si è chiuso, il modulo lunare potrebbe bloccarsi contro la mesh ceiling. Ma se siete in ambienti esterni, verrà entri in allo spazio per un periodo illimitato. 

![Lesson6 capitolo 1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

Passaggio 6: Regolare la spinta in modo che il modulo lunare verrà pilotare backup normalmente. Provare con un valore pari a 0,01. Lasciare vuoto il campo "Rb". È l'acronimo di corpo rigido RB e questo campo viene popolato automaticamente in fase di esecuzione.

![Lesson6 capitolo 1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Panoramica delle parti lunare modulo
L'oggetto padre di parti lunare modulo è la raccolta degli oggetti che interagirà con l'utente. Nell'elenco seguente vengono forniti i nomi di oggetto gioco (con scena con etichettata nomi in paretheses):

- Zaino (serbatoio)
- GasTank (cella Energy)
- TopLeftBody (spaziale Enclosure)
- Naso (ancoraggio portale)
- LeftTwirler (esterni del sensore)

Si noti che ognuno di questi oggetti dispone il gestore di modifica, come illustrato nella lezione 4. Con il gestore di modifica, gli utenti sono in grado di recuperare e manipolare l'oggetto. Si noti inoltre che il "tipo di modifica la mano due" è impostata su "spostare e ruotare". Ciò consente solo all'utente di spostare l'oggetto e non modificarne le dimensioni, ovvero le funzionalità richieste per un'applicazione di assembly.
Inoltre, manipolazione distante è deselezionata per consentire solo per l'interazione diretta delle parti di modulo.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

Lo script della demo parte assembly (illustrato in precedenza) è di scripting che gestisce gli oggetti da inserire al modulo lunare dall'utente. 

Il campo "Oggetto al posto" è la trasformazione che è selezionata (n caso della figura sopra, lo zaino/serbatoio) con l'oggetto che si possa connettere a. 

Le impostazioni "Accanto alla distanza" e "Molto Distance" sono tenute a determinare la vicinanza a cui verranno bloccata in posizione parti o venga rilasciate. Ad esempio, lo zaino/serbatoio dovrà essere 0,1 unità lontano da modulo lunare per bloccare in posizione. "Molto distanza" imposta il percorso in cui l'oggetto deve essere per scollegarsi dal modulo lunare. In questo caso, manuale dell'utente deve acquisire lo zaino/serbatoio e ne effettua il pull 0,2 unità lontano da modulo lunare per rimuoverlo dal blocco nuovamente nella posizione corretta.

il "oggetto suggerimento dello strumento" è l'etichetta suggerimento dello strumento nella scena. Quando gli oggetti vengono bloccati posto, l'etichetta verrà disabilitata. 

L'origine Audio verrà essere afferrato automaticamente. 

### <a name="placement-hints-buttons"></a>Pulsanti di hint per la selezione host
Nelle [lezione 2](mrlearning-base-ch2.md), si è appreso come inserire e configurare i pulsanti per eseguire operazioni come modificare il colore di un elemento o renderla di riprodurre un suono quando questo viene inserito. Si continuerà a usare tali principi come configuriamo nostri pulsanti per attivare e disattivare hint per la selezione host. 

L'obiettivo consiste nel configurare il nostro pulsante in modo che ogni volta che l'utente preme il pulsante di hint per la selezione host, si attiva o disattiva la visibilità dei suggerimenti di selezione host semitrasparente. 

Passaggio 1: Spostare il modulo lunare per lo slot vuoto "solo runtime" nel Pannello di controllo, mentre l'oggetto di hint per la selezione host viene selezionato nella gerarchia della scena di base. 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) passaggio 2: Ora fare clic sull'elenco a discesa in cui è non visualizzato, "Nessuna funzione". Passare alla "TogglePlacementHints" e nel menu selezionare "ToggleGameObjects ()". ToggleGameObjects() si attiva o disattiva l'hint per la selezione host per attivare e disattivare in modo che siano visibili o invisibili ogni volta che viene premuto il pulsante.
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configurare il pulsante di reimpostazione

Ci sono casi in cui l'utente effettua un errore o accidentalmente genera che l'oggetto da subito, o semplicemente desidera posizionare l'esperienza. Il pulsante di reimpostazione aggiungerà la possibilità di riavviare l'esperienza. 

Passaggio 1: Selezionare il pulsante di reimpostazione. Nella scena, base è denominata "ResetRoundButton." 

Passaggio 2: Trascinare il modulo lunare dalla gerarchia della scena di base nello slot vuoto in "pulsante premuto" Pannello di controllo.
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

Passaggio 3: Selezionare il menu a discesa con la dicitura "Nessuna funzione" e passare il mouse su "LaunchLunarModule." A questo punto selezionare "resetModule ()".

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> Nota: Si noterà che per impostazione predefinita "GameObject.BroadcastMessage" è configurato per "ResetPlacement." Questo verrà trasmettere un messaggio denominato "ResetPlacement" per tutti gli oggetti figlio di RocketLauncher_Tutorial. Qualsiasi oggetto che dispone di un metodo per "ResetPlacement()" risponderà al messaggio reimpostando la relativa posizione. 

### <a name="launching-the-lunar-module"></a>L'avvio del modulo lunare
In questo capitolo verrà configurato il pulsante di avvio. Ciò consentirà all'utente di premere il pulsante e avviare il modulo lunare nello spazio.

Passaggio 1: Selezionare il pulsante di avvio (in base scena è denominato "LaunchRoundButton"). Trascinare il modulo lunare lo slot vuoto in "End Touch" nel Pannello di controllo.
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) passaggio 2: Selezionare il menu a discesa con la dicitura "Nessuna funzione". Passare il mouse su "LaunchLunarModule" e selezionare "StopThruster ()". Ciò consente di controllare quanta spinta l'utente vuole assegnare al modulo lunare. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) passaggio 3: In "ButtonPressed()", aggiungere il modulo lunare (fare clic su, tenere premuto e trascinare) per lo slot vuoto. 

Passaggio 4: Fare clic sul menu a discesa con la dicitura "Nessuna funzione" e "LaunchLunarModule" del mouse e selezionare "StartThruster ()". 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) passaggio 5: Aggiungere il modulo lunare musica in modo che quando il rocket decolla, verrà riprodotta la musica. A tale scopo, trascinare il modulo lunare lo slot vuoto successivo in "Pulsante Pressed()".

Passaggio 6: Selezionare il menu a discesa con la dicitura "Nessuna funzione" e "AudioSource" del mouse e selezionare "PlayOneShot (AudioClip)". È possibile esplorare la varietà di suoni incluso con il MRTK. In questo esempio si intende mantenere "MRTK_Gem."
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>È stata completata 
Questa applicazione è stata configurata completamente. Ora quando si preme play, è possibile completamente assemblare il modulo lunare, attivare o disattivare gli hint, avviare il modulo lunare e reimpostarla ripeterla tutto il mondo.
