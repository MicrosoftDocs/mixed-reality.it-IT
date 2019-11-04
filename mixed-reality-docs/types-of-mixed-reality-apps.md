---
title: Tipi di app per realtà mista
description: Uno dei vantaggi dello sviluppo di app per la realtà mista di Windows è costituito dalla possibilità che la piattaforma possa supportare da ambienti virtuali completamente immersivi, fino a una chiara sovrapposizione di informazioni sull'ambiente corrente di un utente.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, modelli di app
ms.openlocfilehash: 62a0b76ba7853262a46b34466a6d3b0567bc137d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438267"
---
# <a name="types-of-mixed-reality-apps"></a>Tipi di app per realtà mista

Uno dei vantaggi dello sviluppo di app per Windows Mixed Reality è costituito dal fatto che la piattaforma può supportare un'ampia gamma di esperienze. Da ambienti virtuali completamente immersivi a una sovrapposizione poco invasiva di informazioni all'ambiente corrente di un utente, Windows Mixed Reality offre un set efficace di strumenti per creare qualsiasi tipo di esperienza. È importante che un creatore di app conosca tempestivamente il proprio processo di sviluppo, a seconda del punto in cui si trova in questo spettro. Questa decisione avrà un effetto sul trucco della progettazione dell'app e sul percorso tecnologico per lo sviluppo.

## <a name="enhanced-environment-apps-hololens-only"></a>App per ambienti avanzati (solo HoloLens)

Uno dei modi più potenti per la realtà mista può fornire valore agli utenti facilitando il posizionamento di informazioni o contenuti digitali nell'ambiente corrente di un utente. Si tratta di un'app per ambienti migliorata. Questo approccio è molto diffuso per le app in cui il posizionamento contestuale di contenuto digitale nel mondo reale è fondamentale e/o mantiene l'ambiente reale dell'utente "presente" durante la loro esperienza è fondamentale. Questo approccio consente anche agli utenti di passare facilmente da attività reali a attività digitali e di tornare in modo semplice, assicurando una maggiore credibilità per garantire che le app di realtà mista visualizzate dall'utente facciano effettivamente parte dell'ambiente.

![app per ambienti avanzati](images/enhancedenvironmentapps-640px.jpg)<br>
*App per ambienti avanzati*

**Usi di esempio**
* App in stile blocco note in realtà mista che consente agli utenti di creare e inserire note nell'ambiente
* Un'app per la televisione in realtà mista posizionata in una posizione comoda per la visualizzazione
* Un'app per la cottura di realtà mista posizionata sopra l'isola della cucina per semplificare l'attività di cottura
* Un'app per realtà mista che offre agli utenti la sensazione di "visione a raggi x", ad esempio un ologramma posizionata sopra e che simula un oggetto reale, consentendo all'utente di visualizzare il "interno" in modo olografico.
* Annotazioni della realtà mista posizionate in una factory per fornire le informazioni necessarie per il ruolo di lavoro
* Realtà mista wayfinding in uno spazio di Office
* Esperienze per il ripiano della realtà mista (esperienze di stile del gioco Board)
* App di comunicazione della realtà mista come Skype

## <a name="blended-environment-apps"></a>App ambiente blended

Data la possibilità di riconoscere e mappare l'ambiente dell'utente in realtà mista di Windows, è in grado di creare un livello digitale che può essere completamente sovrapposto allo spazio dell'utente. Il livello Thin rispetta la forma e i limiti dell'ambiente dell'utente, ma l'app può scegliere di trasformare determinati elementi più adatti per immergere l'utente nell'app. Si tratta di un'app ambiente con Blend. A differenza di un'app per ambienti migliorata, le app per ambienti blended possono solo preoccuparsi dell'ambiente per sfruttare al meglio il proprio trucco per favorire un comportamento specifico dell'utente (ad esempio, incoraggiare lo spostamento o l'esplorazione) o sostituendo elementi con modifiche (una cucina il contatore è praticamente scuoiato per mostrare un modello di riquadro diverso). Questo tipo di esperienza può persino trasformare un elemento in un oggetto completamente diverso, mantenendo tuttavia le dimensioni approssimative dell'oggetto come base (un'isola della cucina viene trasformata in un dumpster per un gioco di thriller del crimine).

App dell'ambiente ![blended](images/blendedenvironmentapps-640px.jpg)<br>
*App ambiente blended*

**Usi di esempio**
* App per la progettazione interna di realtà mista che può dipingere muri, piani o piani in colori e modelli diversi
* App per realtà mista che consente a un progettista di Automotive di sovrapporre nuove iterazioni di progettazione per un aggiornamento imminente dell'auto in un'auto esistente
* Un letto è "coperto" e sostituito da una frutta in realtà mista nel gioco di bambini
* Una scrivania è "coperta" e sostituita con un dumpster di realtà mista in un gioco di thriller del crimine
* Una lanterna sospesa è "coperta" e sostituita con il cartello che usa approssimativamente la stessa forma e la stessa dimensione
* App che consente agli utenti di saltare buchi nei propri muri del mondo reali o immersivi, che mostrano un mondo magico

## <a name="immersive-environment-apps"></a>App per ambienti immersivi

Le app per ambienti immersivi sono incentrate su un ambiente che cambia completamente il mondo dell'utente e può inserirlo in un'ora e in uno spazio diverso. Questi ambienti possono essere molto reali, creando esperienze coinvolgenti ed entusiasmanti, che sono limitate solo dalla fantasia dell'autore dell'app. Diversamente dalle app per ambienti con Blend, una volta che la realtà mista di Windows identifica lo spazio dell'utente, un'app per ambienti immersivi può ignorare completamente l'ambiente corrente dell'utente e sostituirla con una propria. Queste esperienze possono anche separare completamente tempo e spazio, vale a dire che un utente può esplorare le strade di Roma in un'esperienza immersiva, rimanendo relativamente ancora nello spazio reale. Il contesto dell'ambiente reale potrebbe non essere importante per un'app per ambienti immersivi.

![app per ambienti immersivi](images/windows-mixed-reality-640px.jpg)<br>
*App per ambienti immersivi*

**Usi di esempio**
* Un'app immersiva che consente a un utente di visitare uno spazio completamente separato (ad esempio, un famoso edificio, Museo, città popolare)
* App immersiva che orchestra un evento o uno scenario per l'utente (ad esempio, una battaglia o un miglioramento delle prestazioni)

## <a name="see-also"></a>Vedi anche
* [Cenni preliminari sullo sviluppo](development.md)
* [Modello di app](app-model.md)
* [Visualizzazioni delle app](app-views.md)
