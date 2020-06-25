---
title: Coach mano
description: le mani 3D attivate quando il sistema non rileva le mani dell'utente per assisterle.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Realtà mista di Windows, progettazione, Coach mano, auricolare immersivo, MRTK, Hands, assistenza
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345666"
---
# <a name="hand-coach"></a>Coach mano
![Esempio: Hand Coach](images/HandCoach/MRTK_handCoach.jpg)<br>

Hand Coach è un modello 3D che viene attivato quando il sistema non rileva le mani dell'utente. Viene implementato come componente "didattico" che aiuta a guidare l'utente quando il movimento non è stato insegnato. Se gli utenti non hanno eseguito il movimento specificato per un periodo, il ciclo passa con un ritardo. Il coach della mano può essere usato per rappresentare la pressione di un pulsante o la selezione di un ologramma.  

## <a name="hand-coach-provided"></a>Hand Coach fornito

Il modello di interazione corrente rappresenta un'ampia gamma di controlli di movimento, ad esempio scorrimento, selezione e prossimità. Di seguito è riportato un elenco completo dei movimenti di mano esistenti disponibili in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:

:::row:::
    :::column:::
       ![Esempio di near Select](images/HandCoach/NearSelect.gif)<br>
       **Esempio di near Select-used Mostra come selezionare i pulsanti o chiudere gli oggetti interagibili**<br>
    :::column-end:::
    :::column:::
       ![Esempio di rubinetto aereo](images/HandCoach/AirTap.gif)<br>
        **Esempio di tocco aereo: usato per mostrare come selezionare gli oggetti che sono lontani**<br>
    :::column-end:::
    :::column:::
       ![Esempio di spostamento](images/HandCoach/Move.gif)<br>
       **Esempio di spostamento di un oggetto nello spazio: usato per mostrare come spostare un ologramma nello spazio**<br>
    :::column-end:::
    :::column:::
       ![Esempio di rotazione](images/HandCoach/Rotate.gif)<br>
       **Esempio di rotazione: usata per mostrare come ruotare gli ologrammi o gli oggetti**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Esempio di scala](images/HandCoach/Scale.gif)<br>
       **Esempio di scala: usato per illustrare come modificare gli ologrammi in modo che siano più grandi o più piccoli**<br>
    :::column-end:::
    :::column:::
       ![Esempio di Palm up](images/HandCoach/PalmUp.gif)<br>
        **Esempio di palmare: uso suggerito per visualizzare i menu a mano**<br>
    :::column-end:::
    :::column:::
       ![Esempio di HandFlip](images/HandCoach/HandFlip.gif)<br>
       **Esempio of hand Flip: un altro modo per visualizzare i menu a mano**<br>
    :::column-end:::
    :::column:::
       ![Esempio di scorrimento](images/HandCoach/Scoll.gif)<br>
       **Esempio di scorrimento: usato per scorrere un elenco o un documento lungo**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Concetti relativi alla progettazione

Per Hololens2, abbiamo progettato le interazioni Hand in base a movimenti di mano istintiva e naturale. Si ritiene che questi siano intuitivi per la maggior parte degli utenti e pertanto non hanno creato momenti dedicati per l'apprendimento dei movimenti. Al contrario, abbiamo creato il coach per aiutare gli utenti che potrebbero rimanere bloccati o che non hanno familiarità con l'interazione con gli ologrammi. Scopri questi movimenti. Senza un momento di apprendimento, abbiamo pensato che gli utenti che mostravano come eseguire un'azione dimostrando che sarebbe l'opzione migliore. Negli studi, abbiamo scoperto che gli utenti erano in grado di capire il gesto ma aveva bisogno di una piccola guida. Se si rileva che un utente non interagisce con un oggetto per un periodo di tempo, viene attivato un coach della mano che mostra la posizione corretta e la posizione del dito. 

### <a name="intuitive"></a>Intuitivo

Quando si animano le mani, dovrebbe essere ovvio e shoudn ' t causare confusione. L'animazione delle mani è una rappresentazione del gesto che il tentativo di evocare all'utente per comprenderne lo scopo. 

Ad esempio, se si vuole che un utente prema un pulsante, viene attivata una mano che preme un pulsante.

![Esempio: coach della mano vicino al tocco](images/HandCoach/NearSelect_unity.gif)<br>
*Coach della mano che illustra quasi un gioiello*  

### <a name="hand-scale"></a>Scalabilità manuale

Sono state testate diverse dimensioni della mano con i menu dell'interfaccia utente e si ritiene che se le mani erano vere, ha dato una sensazione minacciosa, ma se fosse troppo piccola, era difficile vedere e comprendere il movimento. 

**Voice over e Hands**

Non aspettarsi che gli utenti possano restare in ascolto di un set di istruzioni tramite Voice over e guardare istruzioni diverse tramite il Coach mano. Sequenziare le istruzioni per aiutare gli utenti a concentrarsi sulla propria attenzione per ridurre il sovraccarico sensoriale.


## <a name="can-i-create-my-own"></a>È possibile crearne una personalizzata?

Sì. Si consiglia di creare un proprio gesto univoco per il gioco e contribuire alla community.
È stato fornito un file Maya di una mano truccata che può essere usata per l'app che può essere scaricata qui: <a href="files/HandCoach_MRTK.zip">scaricare HandCoach_MRTK.zip</a>

![Esempio di mani animate in Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Esempio di mano animata di una casella in Maya*


**Strumento di creazione consigliato**

Tra gli artisti 3D, molti scelgono di usare il [Maya di Autodesk, che a sua volta è in grado di usare HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) per trasformare il modo in cui vengono create le risorse. Il file hands fornito è un file binario Maya, quindi è consigliabile usare Maya per animare ed esportare le mani. Se si preferisce usare un altro programma 3D, di seguito è riportato un <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">scaricare HandCoachMRTK_FBX.zip</a> per creare la configurazione del controller. 

Se si usa il file della mano Maya scaricabile fornito, si consiglia di ridimensionare le mani in Unity a 0,6.

![Esempio: rig della mano del coach in Maya](images/HandCoach/MayaExample.png)<br>
*Mani truccate*

### <a name="technical-specs"></a>Specifiche tecniche

*   Il file a due passate è disponibile nel formato Maya ASCII
*    Il lato destro e sinistro è disponibile nel formato binario Maya
*   Impostare il file Maya su 24 FPS
*   All'interno del file è presente una mano sinistra e una destra che può essere usata per due movimenti gestiti o a mano singola. La mano destra sarà visibile solo per impostazione predefinita.
*   Si consiglia di lasciare un buffer di circa 10 frame all'inizio e di fine per Fades
*   Se si aggiunge un'animazione a un oggetto con una destinazione specificata, è consigliabile aggiungere un'animazione a una casella predefinita o a un valore null.
*   Se la mano sta aggiungendo un'animazione a un oggetto fisico, ad esempio una casella, è consigliabile non animare la traduzione in Maya, ma attendere per animarla in Unity o nel codice.
*   L'animazione visibile dovrebbe essere 1,5 secondi per la trasmissione di informazioni significative
*   Quando si ritiene soddisfacente l'animazione:
    *   Selezionare tutti i giunti e cuocere i fotogrammi chiave
    *   Eliminare i controller, selezionare le giunzioni e la mesh ed esportare come FBX
    *  Se sono presenti più animazioni, è possibile usare l'utilità di esportazione del gioco integrata di Maya:https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Esportazione da Maya

Una volta soddisfatta l'animazione
* Seleziona tutte le giunzioni: seleziona > gerarchia

     ![Esempio: posizione del menu](images/HandCoach/Hierarchy.png)<br>
* Cuocere l'animazione: passare a animazione > chiave > animazione Bake

     ![Esempio: posizione del menu](images/HandCoach/BakeAnimation.png)<br>
* Eliminare il rig del controller: DELINEATORE > MainR_Grp o MainL_Grp

     ![Esempio: posizione del menu](images/HandCoach/ControllerRig.png)<br>

* Esporta come FBX: selezionare JNT + mesh: file > Esporta selezione (casella di opzione) > selezione esportazione

     ![Esempio: posizione del menu](images/HandCoach/OptionBox.png)<br>

     ![Esempio: posizione del menu](images/HandCoach/SelectionExport.png)<br>

     ![Esempio: posizione del menu](images/HandCoach/FBXSelection.png)<br>


 Quando si esporta come FBX e si inserisce in Unity, ridimensionare le mani fino a 0,6. Abbiamo scoperto che questo era il giusto equilibrio per la visualizzazione delle mani. 

![Esempio: impostazioni Unity](images/HandCoach/HandHintScale.png)<br>
*Impostazioni Unity per HandCoach_R prefabbricate trovato in MRTK*


## <a name="implementing-hands-into-your-unity-project"></a>Implementazione di Hands nel progetto Unity

### <a name="best-practices"></a>Procedure consigliate
*    Si consiglia di ridimensionare le mani in Unity a 0,6
*   Le mani devono essere riprodotte due volte e se non sono state completate, il ciclo continua fino al completamento del movimento. Per assicurarsi che l'utente abbia il tempo necessario per eseguire la registrazione e visualizzare il movimento, è necessario eseguire due volte il ciclo delle mani. Le mani devono dissolversi tra i cicli. 
 *  Se le mani degli utenti sono visibili dalle fotocamere HL2, ma gli utenti non eseguono l'interazione necessaria, le mani verranno visualizzate dopo 10 secondi.
*   Se le mani dell'utente non sono visibili dalle fotocamere HL2, le mani verranno visualizzate dopo 5 secondi.  
*   Se le mani dell'utente vengono rilevate in maniera visibile dalle fotocamere HL2 al centro dell'animazione, l'animazione verrà completata e sfumata.
*   Se si include il Voice over, è consigliabile che corrisponda al gesto della mano.
*   Se è stato insegnato almeno una volta, ripetere il movimento solo se è stato rilevato che l'utente è bloccato.
*   Se sono critiche posizioni specifiche per Finger/Hand, assicurarsi che gli utenti possano vedere chiaramente queste sfumature nell'animazione. Provare a pescare le mani in modo che le parti più importanti siano chiaramente visibili. 
* Se si nota la distorsione delle mani, è necessario passare alle impostazioni di qualità di Unity per aumentare la quantità di ossa. 
 Passare alle impostazioni del progetto modifica > di Unity > qualità > altri pesi > Blend. Assicurarsi che siano selezionate "4 ossa" per visualizzare le giunzioni uniformi. 

   ![Esempio: posizione del menu](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a>Da evitare
* Ridimensionamento delle mani troppo grandi
* Posizionare le mani troppo vicino all'utente
* Le mani devono essere insegnate una sola volta. Il superamento dell'insegnamento può causare confusione e confusione
*   Per portarla in Unity, scaricare la versione più recente di MRTK qui:https://github.com/microsoft/MixedRealityToolkit-Unity
    *   Materiale: Teaching_Hand2
    *   Script: fare riferimento alle linee guida di MRTK per <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK Hand Coach</a>
    *   Impostazione per progetto
        *   Scenografia impostata su UWP: è possibile trovare l'istruzione nel [progetto di Unity](Configure-Unity-Project.md) per la realtà mista di Windows

## <a name="see-also"></a>Vedi anche
* [Interazione-nozioni fondamentali](interaction-fundamentals.md)
* [Processo di creazione dell'asset](asset-creation-process.md)
* [Movimenti](gestures.md)
* [Installare gli strumenti](install-the-tools.md)
* [Configurare il progetto Unity](Configure-Unity-Project.md)
* [Panoramica dello sviluppo per Unity](unity-development-overview.md)
* [MRTK 101](mrtk-101.md)
