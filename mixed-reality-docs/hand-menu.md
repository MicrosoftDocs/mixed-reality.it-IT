---
title: Menu a mano
description: I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata manualmente per le funzioni usate di frequente. Queste sono le procedure consigliate e le raccomandazioni per i menu a mano.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menu, pulsante, accesso rapido, layout
ms.openlocfilehash: c53fdc4ea6f3243cf906ee1916a9c234d0fce6ca
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143184"
---
# <a name="hand-menu"></a>Menu a mano

![Posizione della mano del lato ulnare](images/UX/UX_Hero_HandMenu.jpg)

I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata manualmente per le funzioni usate di frequente. 

Di seguito sono riportate le procedure consigliate per i menu a mano. È anche possibile trovare una scena di esempio che illustra il menu a mano in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).

<br>

---

## <a name="behavior-best-practices"></a>Procedure consigliate per il comportamento
**A. tenere il numero di pulsanti piccoli:** a causa della distanza di chiusura tra un menu con blocco manuale e gli occhi e anche la tendenza dell'utente a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di attenzione è di circa 10 gradi), è consigliabile mantenendo il numero di pulsanti piccoli. In base all'esplorazione, una colonna con tre pulsanti funziona bene mantenendo tutto il contenuto all'interno del campo di visualizzazione (FOV) anche quando gli utenti spostano le mani al centro del FOV. 

**B. utilizzare il menu a mano per un'azione rapida:** la generazione di un ARM e la gestione della posizione possono causare un facile affaticamento dell'ARM. Usare un metodo con blocco manuale per il menu che richiede una breve interazione. Se il menu è complesso e richiede tempi di interazione estesi, prendere in considerazione l'uso di un blocco globale o del corpo. 

**C. angolo del pulsante o del pannello:** i menu devono essere posizionati verso la parte opposta e al centro della parte principale: ciò consente uno spostamento naturale per interagire con il menu con la mano opposta ed evitare eventuali posizioni scomode o scomode quando si tocca pulsanti. 

**D. provare a supportare il supporto di una sola mano o di un'operazione senza mani:** non presupporre che entrambe le mani dell'utente siano sempre disponibili. Prendere in considerazione una vasta gamma di contesti quando una o entrambe le mani non sono disponibili e assicurarsi che gli account di progettazione per tali situazioni. Per supportare un menu a mano singola, è possibile provare a eseguire la transizione della posizione del menu da Hand-locked a blocco globale quando viene eseguito il capovolgimento della mano (passa a una Palma). Per gli scenari pratici, provare a usare un comando vocale per richiamare i pulsanti del menu a forma di mano.

**E. chiamata in due passaggi:** se si usa solo il Palm-up come un evento per attivare il menu a mano, è possibile che venga visualizzato accidentalmente quando non è necessario (falso positivo), perché le persone spostano le mani molto intenzionalmente (per la manipolazione delle comunicazioni e degli oggetti) e non intenzionalmente. Se si verificano falsi positivi nell'app, è consigliabile aggiungere un passaggio aggiuntivo oltre all'evento di backup per richiamare il menu a mano, ad esempio le dita completamente aperte.

**F. evitare di aggiungere pulsanti vicino al polso (pulsante Home System):** se i pulsanti del menu a mano sono posizionati troppo vicino al pulsante Home, è possibile che venga accidentalmente attivato durante l'interazione con il menu a mano.

**G. test** , test, test: le persone hanno corpi diversi, con soglie diverse per comodità e disagio e così via. Assicurarsi di testare la progettazione e di ricevere commenti e suggerimenti da un'ampia gamma di persone.

<br>

---

## <a name="hand-menu-placement-best-practices"></a>Procedure consigliate per la selezione dei menu a mano

Nell'anatomia umana, il nervo ulnare è un nervo che viene eseguito in prossimità dell'osso ulna. L'ulna è un osso lungo trovato sull'avambraccio che si estende dal gomito al dito più piccolo.

Di seguito sono riportati 2 posizionamenti consigliati in base alle esplorazioni:


:::row:::
    :::column:::
        ![posizione della mano del lato ulnare](images/UlnarSideHandMenu.gif)<br>
        **A. ulnare all'interno di Palm**<br>
        Questa posizione è affidabile perché le mani non si sovrappongono. Si tratta di un fattore fondamentale per il rilevamento e il rilevamento delle carte accurate.
    :::column-end:::
    :::column:::
        ![posizione della mano del lato ulnare](images/UlnarAboveHandMenu.gif)<br>
        **B. oltre la mano del ulnare**<br>
        Questa posizione è comoda per gli utenti perché non è necessario aumentare il proprio ARM per interagire con il menu a mano. È consigliabile posizionare i menu **13cm** sopra la Palma e allineare i pulsanti all'interno della palma ulnar. [Altre informazioni sulle dimensioni dei pulsanti ottimali](interactable-object.md)<br>
        <br>
        Per motivi tecnici, è consigliabile usare questa località con un'implementazione richiesta: lo sviluppatore dovrà bloccare il menu una volta che la mano opposta dell'utente si avvicina all'interazione con l'utente. In questo modo si eviterà che nervosismo si sovrappongano e anche un targeting più rapido dei pulsanti.<br>
        <br>
        Le fotocamere HoloLens 2 identificano le mani accuratamente quando sono separate tra loro. Qualsiasi mano sovrapposta può causare la disattivazione dei menu a mano dalla posizione di ancoraggio.<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>Posizioni dei menu non consigliate
La ricerca degli utenti è stata eseguita con layout e percorsi di menu diversi. i percorsi dei menu seguenti **non sono consigliati**. trovare i svantaggi di ogni studio di seguito:


:::row:::
    :::column:::
        ![sopra](images/AboveArm.gif) ARM<br>
        **Sopra il ARM**<br>
        1-difficile mantenere il rilevamento della mano corretta<br>
        2-causa la fatica dell'utente a causa di una posizione non naturale
    :::column-end:::
    :::column:::
        ![sopra le dita](images/AboveFingers.gif)<br>
        **Sopra le dita**<br>
        affaticamento a una mano dovuta a un periodo di tempo prolungato<br>
        problemi di rilevamento a due mani sull'indice e sul dito medio
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![sopra il centro](images/handCenter.gif) Palm<br>
        **Sopra-centro Palm**<br>
        problemi di rilevamento a una mano dovuti a mani sovrapposte<br>
        affaticamento a due mani a causa del tempo di attesa lungo per interagire con i menu
    :::column-end:::
    :::column:::
        ![parte superiore](images/TopFingerTip.gif) a **portata di mano**<br>
        problemi di rilevamento a una mano<br>
        2-mano di mano che si tiene sotto la postura normale<br>
        3-problemi durante la pressione di pulsanti con altre dita per errore a causa dello spazio limitato tra le dita
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![back of the ARM](images/BackOfTheArm.gif)<br>
        **Back of the ARM**<br>
        1-è possibile attivare il pulsante Home per errore<br>
        2-posizione naturale o comoda per gli utenti
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtkmixed-reality-toolkit-for-unity"></a>Menu a mano in MRTK (Mixed Reality Toolkit) per Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce gli script e le scene di esempio per il menu a mano. Lo script del Risolutore HandConstraintPalmUp consente di associare facilmente tutti gli oggetti alle mani con diverse opzioni configurabili.

* [Menu a MRTK con HandConstraint e HandConstraintPalmUp](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a>Vedi anche

* [Cursori](cursors.md)
* [Raggio della mano](point-and-commit.md)
* [Button](button.md)
* [Oggetto che supporta interazioni](interactable-object.md)
* [Rettangolo di selezione e barra dell'app](app-bar-and-bounding-box.md)
* [Manipolazione](direct-manipulation.md)
* [Menu a mano](hand-menu.md)
* [Menu adiacente](near-menu.md)
* [Raccolta di oggetti](object-collection.md)
* [Comando vocale](voice-input.md)
* [Tastiera](keyboard.md)
* [Descrizione comando](tooltip.md)
* [Slate](slate.md)
* [Dispositivo di scorrimento](slider.md)
* [Shader](shader.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Visualizzazione dello stato](progress.md)
* [Magnetismo di superficie](surface-magnetism.md)
