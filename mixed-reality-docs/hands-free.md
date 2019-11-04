---
title: Senza mani
description: Ottimizzazione dell'app per la libertà di lavoro
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, Hand-Free, sguardo, targeting, interazione, progettazione
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435081"
---
# <a name="hands-free"></a>Senza mani

## <a name="scenarios"></a>Scenari

Come descritto nella [Panoramica del modello di interazione](interaction-fundamentals.md), dopo aver identificato gli utenti e i relativi obiettivi, è possibile chiedersi quali sono le questioni ambientali o di situazione che potrebbero affrontare quando lavorano per svolgere le proprie attività. Molti utenti, ad esempio, devono usare le proprie mani per realizzare gli obiettivi reali e avranno difficoltà a interagire con un'interfaccia basata su hands and controller. 

Di seguito sono riportati alcuni scenari specifici: 
* Guidate attraverso un'attività, mentre le mani dell'utente sono occupate
* Riferimento ai materiali mentre le mani dell'utente sono occupate
* Affaticamento della mano
* Guanti che non possono essere rilevati
* Portare un elemento in mano
* Imbarazzo sociale per eseguire movimenti a mano grande
* Spazi stretti


## <a name="hands-free-modalities"></a>Modalità senza mani

### <a name="voice-inputvoice-inputmd"></a>[Input vocale](voice-input.md)

L'uso della tua voce per il comando e il controllo di un'interfaccia ti offre un modo pratico per lavorare senza mani e per usare i tasti di scelta rapida per ignorare in modo flessibile più passaggi, se necessario. Con l'input vocale, l'utente può semplicemente leggere il nome di un pulsante per attivarlo _("visualizzarlo, pronunciarlo")_ e conversare con un agente digitale che può eseguire le attività.


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[Sguardo fisso e attesa](gaze-and-dwell.md)

In alcune situazioni senza problemi, l'uso della tua voce non è ideale o addirittura possibile. Gli ambienti di produzione, la privacy o le norme di social networking possono essere tutti vincoli. Il modello di tipo sguardo + sosta consente all'utente di spostarsi in un'app senza alcun input aggiuntivo, oltre che da un occhio o da uno sguardo: l'utente continua a guardare la destinazione e indugia per un istante per poterlo attivare. Per altre informazioni sulle singole considerazioni di progettazione per lo sguardo + l'abitazione, vedere [Eye-sguardi + soffermarsi](gaze-and-dwell-eyes.md) e [guardare a capo + soffermarsi](gaze-and-dwell-head.md).


## <a name="transitioning-in-and-out-of-hands-free"></a>Transizione all'interno e all'esterno di Hands-Free

Per questi scenari, liberare le mani dall'interazione con gli ologrammi per i comandi e la navigazione può variare da un requisito assoluto per il funzionamento dell'applicazione, end-to-end, a un ulteriore vantaggio che l'utente può eseguire la transizione da e verso qualsiasi tempo. 

Se il requisito dell'applicazione è che verrà sempre usato senza intervento, sia che si tratti di un'abitazione, di comandi vocali personalizzati o del singolo comando Voice, "Select", assicurarsi di creare le sistemazioni appropriate nell'interfaccia utente. 

Se l'utente di destinazione deve essere in grado di passare da una mano all'altra a loro discrezione, è importante tenere conto dei principi seguenti.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Si supponga che l'utente sia già nella modalità a cui si desidera passare
Ad esempio, se l'utente si trova in fabbrica, guardando un riferimento video sulla sua HoloLens e decide di prelevare una chiave per iniziare a lavorare, probabilmente inizierà a lavorare in modo pratico senza dover posizionare la chiave per premere un pulsante. Dovrebbe essere in grado di richiamare una sessione vocale con un comando Voice, soffermarsi su un'interfaccia utente già visibile per iniziare a soffermarsi o pronunciare la parola "Select".

L'utente deve avere la possibilità di: 
* Passa a vivavoce senza intervento
* Passa a mano
* Passare al controller usando un controller 

### <a name="create-redundant-ways-to-switch-modes"></a>Creare modi ridondanti per cambiare modalità
Mentre il primo principio riguarda l'accesso, il secondo riguarda la disponibilità. Non dovrebbe essere presente un solo modo per eseguire la transizione all'interno e all'esterno di una modalità. 

Di seguito sono riportati alcuni esempi: 
* Pulsante per l'inizio delle interazioni vocali
* Un comando vocale a cui passare, usando l'Head-sguardi e l'abitazione

### <a name="add-a-dash-of-drama"></a>Aggiungere un trattino di dramma
Un cambio di modalità è molto importante, quando queste transizioni si verificano come uno esplicito, anche un cambio drammatico, per consentire all'utente di sapere cosa è successo. 


## <a name="usability-checklist"></a>Elenco di controllo dell'usabilità

**L'utente può eseguire tutte le operazioni e tutto ciò che si può fare senza alcun intervento end-to-end?**
* Ogni interoperabilità deve essere Hands-Free accessibile
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

* Esempio: i affordances di abitazione non sono incorporati nei modelli 2D tipici
* Esempio: il targeting vocale è migliore con l'evidenziazione degli oggetti
* Esempio: le interazioni vocali sono migliori con le didascalie che devono essere attivate


## <a name="see-also"></a>Vedi anche
* [Rilevamento degli occhi su HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Manipolazione diretta](direct-manipulation.md)
* [Movimenti pratici](gaze-and-commit.md#composite-gestures)
* [Hand-point e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)
