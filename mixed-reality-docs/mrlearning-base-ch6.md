---
title: Esercitazioni introduttive-7. Creazione di un'applicazione di esempio del modulo Lunar
description: In questa lezione vengono combinati più concetti appresi dalle lezioni precedenti per creare un'esperienza di esempio univoca.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926514"
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

1. Aggiungere il prefabbricato dell'assembly del modulo Lunar alla scena di base. A tale scopo, nella scheda progetto passare a Asset > BaseModuleAssets > prefabbricates. Si vedranno due prefabbricati di lanciarazzi, trascinando il razzo Launcher_Tutorial prefabbricato nella scena e posizionando come desiderato.

    >[!NOTE]
    >Il Rocket Launcher_Complete prefabbricato è l'utilità di avvio completata, fornita come riferimento.

    ![Immagine lezione 6 capitolo 1 passaggio 1](images/Lesson6_Chapter1_step1im.PNG)

    Se si espande l'oggetto gioco Rocket Launcher_Tutorial nella gerarchia e si espande ulteriormente l'oggetto Lunar Module, si troveranno diversi oggetti figlio con un materiale denominato "x-ray". Il materiale "x-ray" consente un colore leggermente trasparente che verrà usato come hint di selezione host per l'utente. 

    ![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    Sono disponibili cinque parti per il modulo Lunar con cui l'utente interagirà, come illustrato nell'immagine seguente:

    1. Scocca del rover
    2. Serbatoio del carburante
    3. Cella energetica
    4. Portale di ancoraggio
    5. Sensore esterno

    ![Immagine lezione 6 capitolo 1 nota b](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    >i nomi degli oggetti gioco visualizzati nella gerarchia della scena di base non corrispondono ai nomi degli oggetti nella scena.

2. Aggiungere un'origine audio all'oggetto gioco LunarModule. Assicurarsi che LunarModule sia selezionato nella gerarchia della scena e fare clic su Aggiungi componente. Cercare l'origine audio e aggiungerla all'oggetto gioco. Lasciare vuoto il campo AudioClip per il momento, ma modificare l'impostazione speciale di Blend da 0 a 1 in modo da abilitare l'audio spaziale. Questa origine audio verrà usata per riprodurre il suono di avvio in un secondo momento.

    ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. Aggiungere gli hint per la selezione host per l'interruttore. Fare clic su Aggiungi componente e cercare gli hint di selezione host. Si tratta di uno script personalizzato che consente di attivare e disattivare gli hint traslucidi (oggetti con il materiale x-ray), come indicato in precedenza.

    ![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. Poiché sono presenti cinque oggetti, digitare "5" per la dimensione della matrice di oggetti del gioco. Verranno visualizzati cinque nuovi elementi.

    ![Immagine lezione 6 capitolo 1 passaggio 4b](images/Lesson6_Chapter1_step4bim.PNG)

    Trascinare ciascuno degli oggetti traslucidi in tutte le caselle nome (oggetto gioco). Trascinare gli oggetti seguenti dal modulo Lunar nella scena nei campi della matrice di oggetti, come illustrato nell'immagine precedente:

    ![Immagine lezione 6 capitolo 1 passaggio 4a](images/Lesson6_Chapter1_step4aim.PNG)

    Lo script di attivazione/disattivazione del posizionamento è ora configurato, che consente di attivare e disattivare i suggerimenti.

5. Aggiungere lo script Launch Lunar Module. Fare clic sul pulsante Aggiungi componente, cercare "Avvia modulo lunare" e selezionarlo. Questo script avvia il modulo Lunar. Quando si preme un pulsante configurato, viene aggiunta una forza ascendente al componente corpo rigido del modulo lunare e il modulo viene avviato verso l'alto. In luoghi chiusi, il modulo lunare potrebbe scontrarsi contro il soffitto. Se ci si trova in un'area con soffitti elevati o senza limiti, il modulo lunare si troverà nello spazio a tempo indefinito.

    ![Immagine lezione 6 capitolo 1 passaggio 5](images/Lesson6_Chapter1_step5im.PNG)

6. regola la spinta in modo che il modulo lunare possa sollevarsi delicatamente. Prova con un valore pari a 0.01. Lascia vuoto il campo "Rb" (Cr). RB sta per il corpo rigido e questo campo viene popolato automaticamente durante il Runtime.

    ![Immagine lezione 6 capitolo 1 passaggio 6](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Cenni preliminari sulle parti del modulo Lunar

L'oggetto padre Parts del modulo Lunar è la raccolta degli oggetti con cui l'utente interagisce. I nomi degli oggetti di gioco con la scena con etichetta nomi racchiusi tra parentesi sono disponibili nell'elenco seguente:

- Zaino (cella energia)
- GASTANK Sweden (serbatoio carburante)
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

### <a name="configuring-the-placement-hints-button"></a>Configurazione del pulsante degli hint di selezione host

Nella [lezione 2](mrlearning-base-ch2.md)si è appreso come posizionare e configurare i pulsanti per eseguire operazioni quali la modifica del colore di un elemento o la riproduzione di un suono quando viene effettuato il push. Useremo questi stessi principi per configurare i pulsanti in modo da attivare o disattivare i suggerimenti di posizionamento.

Lo scopo è quello di configurare il pulsante in modo che ogni volta che l'utente preme il pulsante dell'hint di selezione host, la visibilità degli hint di posizionamento translucidi.

1. Spostare il modulo Lunar nello slot di runtime vuoto solo nel pannello Inspector mentre l'oggetto hint di posizionamento è selezionato nella gerarchia di base della scena.

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. Fare clic sull'elenco a discesa nessuna funzione. Passare a TogglePlacementHints e selezionare ToggleGameObjects () in questo menu. ToggleGameObjects () consente di attivare e disattivare gli hint di selezione host in modo che siano visibili o invisibili ogni volta che viene premuto il pulsante.

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configurazione del pulsante Reimposta

Si verificheranno situazioni in cui l'utente commette un errore, genera accidentalmente l'oggetto o semplicemente vuole reimpostare l'esperienza. Il pulsante Reimposta consente di riavviare l'esperienza.

1. Selezionare il pulsante Reimposta. Nella scena di base è denominato ResetRoundButton.

2. Trascinare il modulo Lunar dalla gerarchia di base della scena nello slot vuoto sotto il pulsante premuto nel pannello Inspector.

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. Selezionare il menu a discesa nessuna funzione e passare il mouse su LaunchLunarModule, quindi selezionare resetModule ().

    ![Immagine lezione 6 capitolo 4 passaggio 3](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    >Si noti che per impostazione predefinita, GameObject. BroadcastMessage è configurato per ResetPlacement. Viene trasmesso un messaggio denominato ResetPlacement per ogni oggetto figlio della RocketLauncher_Tutorial. Qualsiasi oggetto con un metodo per ResetPlacement () risponde a tale messaggio reimpostando la relativa posizione.

### <a name="configuring-the-launch-button"></a>Configurazione del pulsante Launch

Questa sezione illustra come configurare il pulsante Launch (avvio), che consente all'utente di premere il pulsante e avviare il modulo Lunar nello spazio.

1. Selezionare il pulsante Launch (Avvia). Nella scena di base viene chiamato LaunchRoundButton. Trascinare il modulo Lunar nello slot vuoto sotto touch end nel pannello Inspector.

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. Selezionare il menu a discesa nessuna funzione e passare il puntatore del mouse su LaunchLunarModule e selezionare StopThruster (). Consente di controllare la quantità di spinta che l'utente desidera assegnare al modulo lunare.

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. Trascinare il modulo Lunar dalla gerarchia di base della scena nello slot vuoto in Button premuto nel pannello Inspector.

4. Fare clic sul menu a discesa nessuna funzione e quindi su LaunchLunarModule e selezionare StartThruster ().

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. Aggiungere musica al modulo Lunar in modo che la musica riproduca quando il razzo decolla. A tale scopo, trascinare il modulo Lunar sul successivo slot vuoto sotto il pulsante premuto ().

6. Selezionare il menu a discesa nessuna funzione, passare il mouse su AudioSource e selezionare PlayOneShot (AudioClip). Esplora la varietà di suoni inclusi in MRTK. In questo esempio si userà "MRTK_Gem".

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a>Lezione completata

Questa applicazione è stata configurata completamente. A questo punto, quando si preme Play, è possibile assemblare completamente il modulo Lunar, attivare o disabilitare i suggerimenti, avviare il modulo Lunar e reimpostarlo per riavviarlo.
