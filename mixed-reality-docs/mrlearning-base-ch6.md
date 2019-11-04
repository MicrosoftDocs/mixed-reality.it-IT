---
title: Esercitazioni introduttive-7. Creazione di un'applicazione di esempio del modulo Lunar
description: In questa lezione vengono combinati più concetti appresi dalle lezioni precedenti per creare un'esperienza di esempio univoca.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: a4f405b29ac87945a8585beeed83c1beb450eb0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437761"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. creazione di un'applicazione di esempio del modulo Lunar

In questa esercitazione vengono combinati più concetti rispetto alle lezioni precedenti per creare un'esperienza di esempio univoca. Si apprenderà come creare un'applicazione di assembly del modulo lunare, in base alla quale un utente deve usare le mani registrate per prelevare parti del modulo lunari e provare a assemblare un modulo lunare. Usiamo i pulsanti stampabili per impostare gli hint di posizionamento, per reimpostare l'esperienza e per avviare il modulo lunare nello spazio. Nelle esercitazioni future si continuerà a sviluppare questa esperienza, che include potenti casi d'uso multiutente che sfruttano gli ancoraggi spaziali di Azure per l'allineamento spaziale.

## <a name="objectives"></a>Obiettivi

- Combinare i vari concetti illustrati nelle lezioni precedenti per creare un'esperienza unica
- Apprendere come attivare o disattivare gli oggetti
- Attivare eventi complessi usando i pulsanti a pressione
- Usare la forza e la fisica dei corpi rigidi
- Esplorare l'uso delle descrizioni comandi

## <a name="instructions"></a>Istruzioni

### <a name="configuring-the-lunar-module"></a>Configurazione del modulo lunare

In questa sezione vengono introdotti i vari componenti necessari per creare l'esperienza di esempio.

1. Aggiungere il prefabbricato dell'assembly del modulo Lunar alla scena di base. A tale scopo, cercare il Launcher_Tutorial Rocket nella scheda Project (progetto). trovare il prefabbricato in assets-> BaseModuleAssets-> prefabbricates. Verranno anche visualizzate due prefabbricati di lanciarazzi. uno con il nome "tutorial" e l'altro con il nome "complete". Trascinare il prefabbricato Rocket Launcher_Tutorial nella scena di base e posizionare come desiderato.
Nota: la prefabbricazione Rocket Launcher_Complete è l'utilità di avvio completata, fornita come riferimento. 

![Immagine lezione 6 capitolo 1 passaggio 1](images/Lesson6_Chapter1_step1im.PNG)

Se si espande l'oggetto gioco Rocket Launcher_Tutorial nella gerarchia e si espande ulteriormente l'oggetto Lunar Module, si troveranno diversi oggetti figlio con un materiale denominato "x-ray". Il materiale "x-ray" consente un colore leggermente trasparente che verrà usato come hint di selezione host per l'utente. 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) sono presenti cinque parti del modulo Lunar con cui l'utente interagirà, come illustrato nell'immagine seguente:

1.  Scocca del rover
2.  Serbatoio del carburante
3.  Cella energetica
4.  Portale di ancoraggio 
5.  Sensore esterno

![Immagine lezione 6 capitolo 1 nota b](images/Lesson6_Chapter1_notebim.PNG)

> Nota: i nomi degli oggetti del gioco visualizzati nella gerarchia della scena di base non corrispondono ai nomi degli oggetti nella scena.

Passaggio 2: aggiungere un'origine audio al modulo lunare. Verificare che il modulo Lunar sia selezionato nella gerarchia della scena di base e fare clic su Add Component. Cercare l'origine audio e aggiungerla all'oggetto. Lasciarlo vuoto per il momento, ma fare clic sulla casella di controllo "Spatialize" per abilitare l'audio spaziale. Questa operazione verrà usata per riprodurre il suono di avvio in un secondo momento.

 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)  
Passaggio 3: aggiungere gli hint per la selezione host per lo script. Fare clic su Aggiungi componente e cercare gli hint di selezione host. Si tratta di uno script personalizzato che consente di attivare e disattivare gli hint traslucidi (oggetti con il materiale x-ray), come indicato in precedenza.  
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)  
Passaggio 4: poiché sono disponibili cinque oggetti, digitare "5" per la dimensione della matrice di oggetti del gioco. Verranno visualizzati cinque nuovi elementi.  


![Immagine lezione 6 capitolo 1 passaggio 4b](images/Lesson6_Chapter1_step4bim.PNG)

Trascinare ciascuno degli oggetti traslucidi in tutte le caselle nome (gioco le Esplora).
Trascina gli oggetti seguenti dal modulo lunare nella scena di base: 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Immagine lezione 6 capitolo 1 passaggio 4a](images/Lesson6_Chapter1_step4aim.PNG)

Lo script di attivazione/disattivazione del posizionamento è ora configurato, che consente di attivare e disattivare i suggerimenti.

Passaggio 5: aggiungere lo script Launch Lunar Module. Fare clic sul pulsante Aggiungi componente, cercare "Avvia modulo lunare" e selezionarlo. Questo script avvia il modulo Lunar. Quando si preme un pulsante configurato, viene aggiunta una forza ascendente al componente corpo rigido del modulo lunare e il modulo viene avviato verso l'alto. In luoghi chiusi, il modulo lunare potrebbe scontrarsi contro il soffitto. Se ci si trova in un'area con soffitti elevati o senza limiti, il modulo lunare si troverà nello spazio a tempo indefinito. 

![Immagine lezione 6 capitolo 1 passaggio 5](images/Lesson6_Chapter1_step5im.PNG)

Passaggio 6: regolare la spinta in modo che il modulo lunare si avvicini normalmente. Prova con un valore pari a 0.01. Lascia vuoto il campo "Rb" (Cr). RB sta per il corpo rigido e questo campo viene popolato automaticamente durante il Runtime.

![Immagine lezione 6 capitolo 1 passaggio 6](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Cenni preliminari sulle parti del modulo Lunar
L'oggetto padre Parts del modulo Lunar è la raccolta degli oggetti con cui l'utente interagisce. I nomi degli oggetti di gioco con la scena con etichetta nomi in paretheses sono disponibili nell'elenco seguente:

- Equipaggiamento (Serbatoio del carburante)
- GasTank (Cella energetica)
- TopLeftBody (Scocca del rover)
- Nose (Portale di ancoraggio)
- LeftTwirler (Sensore esterno)

Si noti che ognuno di questi oggetti dispone di un gestore di manipolazione, come illustrato nella lezione 4. Questa funzionalità consente agli utenti di acquisire e manipolare l'oggetto. Si noti inoltre che l'impostazione, due tipi di manipolazione gestiti, viene impostata per spostare e ruotare. Questa opzione consente solo all'utente di spostare l'oggetto e non modificarne le dimensioni, ovvero la funzionalità desiderata per un'applicazione assembly.
Inoltre, la manipolazione a lungo è deselezionata per consentire solo l'interazione diretta delle parti del modulo.

![Immagine lezione 6 capitolo 2](images/Lesson6_Chapter2im.PNG)

Lo script demo dell'assembly della parte (illustrato in precedenza) è lo script che gestisce gli oggetti posizionati dall'utente sul modulo lunare dall'utente. 

Il campo oggetto da inserire è la trasformazione selezionata, come illustrato nell'immagine precedente, il serbatoio dello zaino o del carburante associato all'oggetto a cui si connette. 

Le impostazioni near distance e distance distance determinano la vicinanza a cui si bloccano le parti o che possono essere rilasciate. Ad esempio, lo zaino/serbatoio del carburante deve essere di 0,1 unità dal modulo lunare prima di eseguire lo snap-in. L'impostazione distance distance imposta la posizione in cui l'oggetto può essere prima che possa essere scollegato dal modulo lunare. In questo caso, la mano dell'utente deve afferrare l'oggetto equipaggiamento/serbatoio del carburante e spostarlo a 0.2 unità dal modulo lunare per evitare che venga nuovamente ancorato.

L'oggetto descrizione comando è l'etichetta descrizione comando nella scena. Quando gli oggetti vengono bloccati sul posto, l'etichetta è disabilitata. 

L'origine audio viene afferrata automaticamente. 

### <a name="placement-hints-buttons"></a>Pulsanti degli hint di selezione host
Nella [lezione 2](mrlearning-base-ch2.md)si è appreso come posizionare e configurare i pulsanti per eseguire operazioni quali la modifica del colore di un elemento o la riproduzione di un suono quando viene effettuato il push. Useremo questi stessi principi per configurare i pulsanti in modo da attivare o disattivare i suggerimenti di posizionamento. 

Lo scopo è quello di configurare il pulsante in modo che ogni volta che l'utente preme il pulsante dell'hint di selezione host, la visibilità degli hint di posizionamento translucidi. 

Passaggio 1: spostare il modulo Lunar nello slot di runtime vuoto nel pannello Inspector mentre l'oggetto hint di posizionamento è selezionato nella gerarchia di base della scena. 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) passaggio 2: fare clic sull'elenco a discesa nessuna funzione. Passare a TogglePlacementHints e selezionare ToggleGameObjects () in questo menu. ToggleGameObjects () consente di attivare e disattivare gli hint di selezione host in modo che siano visibili o invisibili ogni volta che viene premuto il pulsante.  
 ![Immagine lezione 6 capitolo 3 passaggio 2](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configurazione del pulsante Reimposta

Si verificheranno situazioni in cui l'utente commette un errore, genera accidentalmente l'oggetto o semplicemente vuole reimpostare l'esperienza. Il pulsante Reimposta consente di riavviare l'esperienza. 

Passaggio 1: selezionare il pulsante Reimposta. Nella scena di base è denominato ResetRoundButton. 

Passaggio 2: trascinare il modulo Lunar dalla gerarchia della scena di base nello slot vuoto sotto il pulsante premuto nel pannello Inspector.
 ![Immagine lezione 6 capitolo 4 passaggio 2](images/Lesson6_Chapter4_step2im.PNG)

Passaggio 3: selezionare il menu a discesa nessuna funzione e passare il mouse su LaunchLunarModule, quindi selezionare resetModule ().

![Immagine lezione 6 capitolo 4 passaggio 3](images/Lesson6_Chapter4_step3im.PNG)

> Nota: per impostazione predefinita, GameObject. BroadcastMessage è configurato per ResetPlacement. Viene trasmesso un messaggio denominato ResetPlacement per ogni oggetto figlio di RocketLauncher_Tutorial. Qualsiasi oggetto con un metodo per ResetPlacement () risponde a tale messaggio reimpostando la relativa posizione. 

### <a name="launching-the-lunar-module"></a>Avvio del modulo Lunar
Questa sezione illustra come configurare il pulsante Launch (avvio), che consente all'utente di premere il pulsante e avviare il modulo Lunar nello spazio.

Passaggio 1: selezionare il pulsante Launch (Avvia). Nella scena di base viene chiamato LaunchRoundButton. Trascinare il modulo Lunar nello slot vuoto sotto touch end nel pannello Inspector.
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) passaggio 2: selezionare il menu a discesa nessuna funzione e passare il mouse su LaunchLunarModule e selezionare StopThruster (). Consente di controllare la quantità di spinta che l'utente desidera assegnare al modulo lunare. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)  
Passaggio 3: in ButtonPressed () aggiungere il modulo Lunar (fare clic, mantenere e trascinare) allo slot vuoto. 

Passaggio 4: fare clic sul menu a discesa nessuna funzione, passare il mouse su LaunchLunarModule e selezionare StartThruster (). 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)  
Passaggio 5: aggiungere musica al modulo lunare, in modo che la musica riproduca quando il razzo viene disattivato. A tale scopo, trascinare il modulo Lunar sul successivo slot vuoto sotto il pulsante premuto ().

Passaggio 6: selezionare il menu a discesa nessuna funzione, passare il mouse su AudioSource e selezionare PlayOneShot (AudioClip). Esplora la varietà di suoni inclusi in MRTK. In questo esempio si userà "MRTK_Gem".
 ![Immagine lezione 6 capitolo 5 passaggio 6](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Lezione completata 
Questa applicazione è stata configurata completamente. A questo punto, quando si preme Play, è possibile assemblare completamente il modulo Lunar, attivare o disabilitare i suggerimenti, avviare il modulo Lunar e reimpostarlo per riavviarlo.
