---
title: Ottimizzazione delle app per mani libere
description: Ottimizzazione delle app per mani libere
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, mani libere, estasiati, estasiati targeting, interazione, progettazione
ms.openlocfilehash: b64dec802d8ed2886021a54f302ba4a948c4f5b9
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581031"
---
# <a name="optimizing-your-app-for-hands-free"></a>Ottimizzazione delle app per mani libere



## <a name="scenarios"></a>Scenari

Come descritto nel [Cenni preliminari sul modello di interazione](interaction-fundamentals.md), una volta identificati gli utenti e i propri obiettivi, è opportuno porsi le sfide ambientali o di consapevolezza che possono verificarsi mentre lavorano per portare a termine le attività. Ad esempio, necessario usare le mani realizzazione dei loro obiettivi reali che molti utenti con difficoltà l'interazione con un'interfaccia basata su mani e controller. 

Potrebbero essere alcuni scenari specifici: 
* Viene guidato attraverso un'attività, mentre sono occupati
* Materiali di riferimento mentre le mani sono occupate
* Ricordare di mano
* Guanti che non possono essere rilevate
* Esecuzione di un elemento


## <a name="hands-free-modalities"></a>Modalità invisibile all'utente

### <a name="voice-commanding"></a>L'esecuzione di comandi vocali

Utilizzando la voce di comando e controllo di che un'interfaccia può non solo consentono all'utente di operare in viva voce, ma anche ignorare più passaggi. L'utilizzo di questa modalità può variare da consentire all'utente di nome del pulsante, qualsiasi operazione di lettura a voce alta per attivarlo, come vedere-it-say-it, alla conversazione con un agente che consentono di eseguire attività per l'utente.

* [Progettazione delle interazioni vocali](voice-design.md)


### <a name="head-gaze-and-dwell"></a>Head sguardo e permanenza

In alcune situazioni invisibile all'utente, utilizzando la voce non è ideale o persino possibile. Gli ambienti di factory l, sulla privacy o norme social possono essere tutti i vincoli. Head estasiati + permanenza modello consente all'utente di spostarsi tra l'app usando il vettore head in modo da puntare, mentre il tempo di ritardo, o rimanere su un pulsante verrà attivarlo dopo un determinato periodo di tempo (in genere entro 1 secondo o operazione). 

* [Sguardo e permanenza](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a>In fase di transizione da e verso mani libere

Per questi scenari, liberando le mani di interagire con vntana per l'esecuzione di comandi e l'esplorazione può variare da in corso di un requisito assoluto all'esecuzione dell'app, end-to-end, per praticità che l'utente può eseguire la transizione in e out di in qualsiasi momento. 

Se i requisiti dell'app verrà sempre utilizzata invisibile all'utente, utilizzando sia permanenza, comandi vocali o l'unico comando vocale, "select", quindi assicurarsi di prendere il accomodations appropriata nell'interfaccia utente. 

Se l'utente di destinazione deve essere in grado di passare da mani a invisibile all'utente a propria discrezione, quindi è importante tenere conto di questi principi:

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Si presuppone che l'utente è già in modalità che desiderano passare a
Ad esempio, se l'utente è nell'ambiente di produzione, guardare un video riferimento sul suo Hololens e decide di prelevare una chiave inglese per iniziare a lavorare, Anna molto probabilmente desidera iniziare a lavorare in viva voce senza la necessità di impostare la chiave inglese a premere un pulsante. Deve essere in grado di richiamare una sessione vocale con un comando vocale, il caso di soffermarsi su già visibili dell'interfaccia utente per iniziare a permanenza, o ad esempio la parola "select".

L'utente deve avere la possibilità di: 
* Passare a in viva voce durante in viva voce
* Passare a mani con le mani
* Passare al controller usando un controller 

### <a name="create-redundant-ways-to-switch-modes"></a>Creare metodi ridondanti per cambiare la modalità di
Mentre il principio del primo accesso, il secondo è sulla disponibilità. Non vi non appena sarà un unico modo per eseguire la transizione da e verso una modalità. 

Alcuni esempi sono: 
* Un pulsante per avviare interazioni vocali
* Un comando vocali per la transizione all'utilizzo sguardo + permanenza

### <a name="add-a-dash-of-drama"></a>Aggiungere un trattino di drammatico
Un interruttore è senz'altro un traguardo, è importante che quando si verificano queste transizioni, che tuttavia un'opzione esplicita, anche un significativo, per consentire all'utente di sapere che cosa è successo. 


## <a name="usability-checklist"></a>Elenco di controllo di usabilità

**L'utente può fare tutto e qualsiasi valore mani libere, end-to-end?**
* Ogni interactible devono essere accessibili mani libere
* Verificare che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, inserendo, tessere magnetiche, tap e così via.
* Assicurarsi che l'utente abbia certo controllo della presenza dell'interfaccia utente, posizione, il livello di dettaglio in qualsiasi momento
    * Introduzione dell'interfaccia utente dall'area di lavoro
    * Interfaccia utente di indirizzamento fuori campo visualizzazione)
    * Quanto viene visualizzato, dove e quando

**Vengono tenuti e consolidati con i destro affordance i meccanismi dell'interazione?**

L'utente comprensione...
* ... Quali modalità si trovano in?
* ... Le operazioni consentite in questa modalità?
* ... Che cos'è lo stato corrente?
* ... Come è possibile eseguire la transizione?
    
**L'interfaccia utente ottimizzata per invisibile all'utente?**   

* Ad esempio: Permanenza affordance non sono incorporati ai tipici modelli 2D
* Ad esempio: Destinati Voice è migliore con l'evidenziazione di oggetto
* Ad esempio: Le interazioni vocali sono preferibili con sottotitoli in lingua originale che dovranno essere attivata


## <a name="see-also"></a>Vedere anche
* [Sguardo ed eseguire il commit](gaze-and-commit.md)
* [Manipolazione diretta](direct-manipulation.md)
* [Punto e commit](point-and-commit.md)
