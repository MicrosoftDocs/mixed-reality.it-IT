---
title: Senza mani
description: Ottimizzazione dell'app per la libertà di lavoro
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, Hand-Free, sguardo, targeting, interazione, progettazione
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414388"
---
# <a name="hands-free"></a>Senza mani



## <a name="scenarios"></a>Scenari

Come descritto nella [Panoramica del modello di interazione](interaction-fundamentals.md), una volta identificati gli utenti e i rispettivi obiettivi, è possibile chiedersi quali problemi ambientali o di situazione potrebbero affrontare quando lavorano per svolgere le proprie attività. Molti utenti, ad esempio, devono usare le proprie mani per realizzare gli obiettivi del mondo reale e avranno difficoltà a interagire con un'interfaccia basata su hands and controller. 

Alcuni scenari specifici potrebbero essere: 
* Guidate attraverso un'attività, mentre le mani sono occupate
* Riferimento ai materiali mentre le mani sono occupate
* Affaticamento della mano
* Guanti che non possono essere rilevati
* Portare qualcosa


## <a name="hands-free-modalities"></a>Modalità senza mani

### <a name="voice-commandingvoice-designmd"></a>[Esecuzione di comandi vocali](voice-design.md)

L'uso della voce per eseguire il comando e il controllo di un'interfaccia non consente solo all'utente di usare la modalità vivavoce, ma anche di ignorare più passaggi. L'utilizzo di questa modalità può variare da consentire all'utente di leggere semplicemente il nome di qualsiasi pulsante in modo da attivarlo, come in see-it-say-it, per conversare con un agente che può eseguire le attività.



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[Puntamento con la testa e attesa](gaze-and-dwell.md)

In alcune situazioni senza problemi, l'uso della tua voce non è ideale o addirittura possibile. Gli ambienti di produzione, la privacy o le norme di social networking possono essere tutti vincoli. Il modello Head con lo sguardo più attivo consente all'utente di spostarsi nell'app usando il vettore Head per puntare, mentre rimanente o soffermarsi su un pulsante che lo attiverà dopo un determinato periodo di tempo, in genere circa 1 secondo. 


## <a name="transitioning-in-and-out-of-hands-free"></a>Transizione all'interno e all'esterno di Hands-Free

Per questi scenari, liberare le mani dall'interazione con gli ologrammi per i comandi e la navigazione può variare da un requisito assoluto per il funzionamento dell'applicazione, end-to-end, a un ulteriore vantaggio che l'utente può eseguire la transizione da e verso qualsiasi tempo. 

Se il requisito dell'applicazione consiste nel fatto che verrà sempre usato senza intervento, sia che si tratti di un'operazione di digitazione, di comandi vocali o del comando per voce singola, "Select", assicurarsi di effettuare le sistemazioni appropriate nell'interfaccia utente. 

Se l'utente di destinazione deve essere in grado di passare da una mano all'altra a loro discrezione, è importante tenere conto dei principi seguenti.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Si supponga che l'utente sia già nella modalità a cui si desidera passare
Ad esempio, se l'utente si trova in fabbrica, guardando un riferimento video sulla sua Hololens e decide di prelevare una chiave per iniziare a lavorare, probabilmente inizierà a lavorare in vivavoce senza dover chiudere la chiave per premere un pulsante. Dovrebbe essere in grado di richiamare una sessione vocale con un comando Voice, soffermarsi su un'interfaccia utente già visibile per iniziare a soffermarsi o pronunciare la parola "Select".

L'utente deve avere la possibilità di: 
* Passa a vivavoce senza intervento
* Passa a mano
* Passare al controller usando un controller 

### <a name="create-redundant-ways-to-switch-modes"></a>Creare modi ridondanti per cambiare modalità
Mentre il primo principio riguarda l'accesso, il secondo riguarda la disponibilità. Non dovrebbe essere presente un solo modo per eseguire la transizione all'interno e all'esterno di una modalità. 

Di seguito sono riportati alcuni esempi: 
* Pulsante per l'inizio delle interazioni vocali
* Un comando vocale per la transizione a tramite lo sguardo + l'abitazione

### <a name="add-a-dash-of-drama"></a>Aggiungere un trattino di dramma
Un cambio di modalità è molto importante, quando queste transizioni si verificano come un cambio esplicito, anche drammatico, per informare l'utente di cosa è successo. 


## <a name="usability-checklist"></a>Elenco di controllo dell'usabilità

**L'utente può eseguire tutte le operazioni e tutto ciò che si può fare senza alcun intervento end-to-end?**
* Ogni interactible deve essere Hands-Free accessibile
* Assicurarsi che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, l'inserimento, il scorrimento, i rubinetti e così via.
* Assicurarsi che l'utente abbia il controllo della presenza, della posizione e del livello di dettaglio dell'interfaccia utente in qualsiasi momento
    * Recupero dell'interfaccia utente
    * Indirizzamento dell'interfaccia utente fuori campo di visualizzazione (FOV)
    * Quanto vedo, dove, quando

**La meccanica dell'interazione viene insegnata e rafforzata con la affordances corretta?**

Informazioni sull'utente...
* ... Modalità di funzionamento
* ... Cosa si può fare in questa modalità?
* ... Qual è lo stato corrente?
* ... In che modo è possibile eseguire la transizione?
    
**L'interfaccia utente è ottimizzata per l'Hand-Free?**   

* Esempio: I affordances di residenza non sono incorporati nei modelli 2D tipici
* Esempio: Il targeting vocale è migliore con l'evidenziazione degli oggetti
* Esempio: Le interazioni vocali sono migliori con le didascalie che devono essere attivate


## <a name="see-also"></a>Vedere anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
