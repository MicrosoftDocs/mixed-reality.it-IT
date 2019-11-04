---
title: Controller di movimento e Hands
description: Panoramica dell'interazione tra controller di movimento e Hands
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realtà mista, mani, controller di movimento, interazione, progettazione
ms.openlocfilehash: 395862fe987244e2af70bb6794caa91e243cd076
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435168"
---
# <a name="hands-and-motion-controllers"></a>Controller di movimento e Hands
## <a name="scenarios"></a>Scenari
Se si sceglie di adottare questo modello di interazione dopo aver letto la [Panoramica sull'interazione](interaction-fundamentals.md), significa che si sta sviluppando un'applicazione che richiede agli utenti di usare due mani per interagire con il mondo olografico. L'applicazione è in grado di raggiungere l'obiettivo di rimuovere il limite tra virtuale e fisico.

Alcuni scenari specifici potrebbero essere:
* Fornire schermate virtuali 2D per gli Information Worker con interfaccia utente affordances per visualizzare e controllare il contenuto
* Esercitazione e guide per i ruoli di lavoro di prima linea per le linee di assemblaggio Factory
* Sviluppo di strumenti professionali per assistere e educare professionisti medici  
* Uso di oggetti virtuali 3D per decorare il mondo reale o creare un secondo mondo 
* Creazione di servizi e giochi location based usando il mondo reale come sfondo

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>Modalità di controllo delle mani e del movimento

:::row:::
    :::column:::
       [![manipolazione diretta con mani](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsdirect-manipulationmdbr"></a>[Manipolazione diretta con le mani](direct-manipulation.md)<br>
       Si tratta di una modalità sfruttando la potenza di Hands, con cui gli utenti sono in grado di toccare e modificare direttamente gli ologrammi. Sfruttando le esperienze quotidiane e fornendo affordances visivi appropriati, gli utenti possono usare lo stesso modo per modificare gli oggetti reali per interagire con quelli virtuali.
    :::column-end:::
    :::column:::
       [![punto e commit con hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handspoint-and-commitmdbr"></a>[Puntamento e commit con le mani](point-and-commit.md)<br>
        Questa modalità consente agli utenti di interagire con gli ologrammi a distanza. Consente agli utenti di sfruttare al meglio i dintorni. Gli utenti possono posizionare gli ologrammi ovunque e possono comunque accedervi da qualsiasi distanza. I modelli e i movimenti mentali per controllare e modificare gli ologrammi 2D e 3D sono sincronizzati con quelli di manipolazione diretta.
    :::column-end:::
    :::column:::
       [controller di movimento ![](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersmotion-controllersmdbr"></a>[Controller del movimento](motion-controllers.md)<br>
       I controller di movimento sono strumenti che estendono le funzionalità fisiche dell'utente fornendo interazioni precise in un'ampia gamma di distanze durante l'uso di una o entrambe le mani. Questi accessori hardware forniscono collegamenti a molte interazioni di uso comune e forniscono surefooted e commenti tattili per diverse azioni. Attualmente, i controller di movimento sono disponibili solo per gli scenari di realtà mista di Windows (WMR). 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Vedi anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Mani libere](hands-free.md)
