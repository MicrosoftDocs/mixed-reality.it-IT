---
title: Senza mani
description: Ottimizzazione delle app per mani libere
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, mani libere, estasiati, estasiati targeting, interazione, progettazione
ms.openlocfilehash: 4d21fa10eabb446565bddebccdbde5e2e7bcc72a
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326147"
---
# <a name="hands-free"></a>Senza mani



## <a name="scenarios"></a>Scenari

Come descritto nel [Cenni preliminari sul modello di interazione](interaction-fundamentals.md), una volta identificati gli utenti e i propri obiettivi, è opportuno porsi le sfide ambientali o di consapevolezza che possono verificarsi mentre lavorano per portare a termine le attività. Ad esempio, molti utenti è necessario usare le mani per eseguire i propri obiettivi del mondo reale e sarà difficile l'interazione con un'interfaccia basata su mani e controller. 

Potrebbero essere alcuni scenari specifici: 
* Viene guidato attraverso un'attività, mentre sono occupati
* Materiali di riferimento mentre le mani sono occupate
* Ricordare di mano
* Guanti che non possono essere rilevate
* Esecuzione di un elemento


## <a name="hands-free-modalities"></a>Modalità invisibile all'utente

### <a name="voice-commandingvoice-designmd"></a>[Esecuzione di comandi vocali](voice-design.md)

Utilizzando la voce di comando e controllo di che un'interfaccia può non solo consentono all'utente di operare in viva voce, ma anche ignorare più passaggi. L'utilizzo di questa modalità può variare da consentire all'utente di leggere semplicemente il nome di un pulsante qualsiasi a voce alta per attivarlo, come vedere-it-say-it, alla conversazione con un agente che consentono di eseguire attività per l'utente.



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[Puntamento con la testa e attesa](gaze-and-dwell.md)

In alcune situazioni invisibile all'utente, utilizzando la voce non è ideale o persino possibile. Gli ambienti di factory l, sulla privacy o norme social possono essere tutti i vincoli. Head estasiati + permanenza modello consente all'utente di spostarsi tra l'app usando il vettore head in modo da puntare, mentre il tempo di ritardo, o rimanere su un pulsante verrà attivarlo dopo un determinato periodo di tempo, normalmente circa 1 secondo o in questo caso. 


## <a name="transitioning-in-and-out-of-hands-freey"></a>In fase di transizione da e verso le mani freey

Per questi scenari, liberando le mani di interagire con vntana per l'esecuzione di comandi e la navigazione può essere compreso tra da un requisito assoluto all'esecuzione dell'applicazione, end-to-end, per praticità che l'utente può eseguire la transizione in e out di in corrispondenza di qualsiasi ora. 

Se i requisiti dell'applicazione verrà sempre utilizzato invisibile all'utente, utilizzando sia permanenza, comandi vocali o l'unico comando vocale, "select", quindi assicurarsi di prendere il accomodations appropriata nell'interfaccia utente. 

Se l'utente di destinazione deve essere in grado di passare da mani a invisibile all'utente a propria discrezione, quindi è importante considerare i seguenti principi.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Si presuppone che l'utente è già in modalità che desiderano passare a
Ad esempio, se l'utente è nell'ambiente di produzione, guardare un video riferimento sul suo Hololens e decide di prelevare una chiave inglese per iniziare a lavorare, Anna molto probabilmente verrebbe iniziare a lavorare in viva voce senza la necessità di impostare la chiave inglese a premere un pulsante. Deve essere in grado di richiamare una sessione vocale con un comando vocale, il caso di soffermarsi su un'interfaccia utente già visibili per iniziare a permanenza, o ad esempio la parola "select".

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
Un interruttore è molto importante, è importante che quando si verificano queste transizioni che tuttavia un'opzione esplicita, anche un significativo, per consentire all'utente di sapere che cosa è successo. 


## <a name="usability-checklist"></a>Elenco di controllo di usabilità

**L'utente può fare tutto e qualsiasi valore mani libere, end-to-end?**
* Ogni interactible devono essere accessibili mani libere
* Verificare che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, inserendo, tessere magnetiche, tap e così via.
* Assicurarsi che l'utente abbia certo controllo della presenza dell'interfaccia utente, posizione e livello di dettaglio in qualsiasi momento
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

* Esempio: Permanenza affordance non sono incorporati ai tipici modelli 2D
* Esempio: Destinati Voice è migliore con l'evidenziazione di oggetto
* Esempio: Le interazioni vocali sono preferibili con sottotitoli in lingua originale che dovranno essere attivata


## <a name="see-also"></a>Vedere anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Manipolazione diretta](direct-manipulation.md)
* [Puntamento e commit](point-and-commit.md)
