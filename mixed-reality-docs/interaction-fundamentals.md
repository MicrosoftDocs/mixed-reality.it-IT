---
title: Panoramica dell'interazione multimodale
description: Panoramica dell'interazione multimodale
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, sguardo fisso, selezione della destinazione con lo sguardo fisso, interazione, progettazione, HoloLens, MMR, multimodale
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516015"
---
# <a name="introducing-instinctual-interactions"></a>Introduzione alle interazioni istintive

La filosofia delle interazioni semplici e istintive è alla base di tutta la piattaforma Realtà mista di Microsoft.  Abbiamo adottato tre accorgimenti per consentire ai progettisti e agli sviluppatori di applicazioni di fornire ai clienti interazioni facili e intuitive. 

In primo luogo, ci siamo assicurati che i nostri straordinari sensori e la tecnologia di input, tra cui il tracciamento delle mani, il tracciamento oculare e il linguaggio naturale, si combinassero in perfetti modelli di interazione multimodale.  In base alle nostre ricerche, le attività di progettazione e sviluppo multimodali e non basate su input singoli sono la chiave di volta per creare esperienze istintive.

In secondo luogo, constatiamo che molti sviluppatori puntano a più dispositivi, indipendentemente dal fatto che si tratti di HoloLens 2 e HoloLens (prima generazione) oppure HoloLens e VR.  Abbiamo quindi progettato modelli di interazione in grado di funzionare in tutti i dispositivi, anche se la tecnologia di input varia da un dispositivo all'altro.  Ad esempio, per l'interazione da lontano con un visore VR immersive di Windows dotato di un controller 6DOF e per l'interazione da lontano con un dispositivo HoloLens 2 vengono usati gli stessi inviti e modelli, semplificando le applicazioni su più dispositivi. Questo accorgimento non solo è utile per gli sviluppatori e i progettisti, ma offre un'esperienza naturale anche agli utenti finali. 

Infine, anche se riconosciamo che possono esistere migliaia di interazioni efficaci, coinvolgenti e magiche in Realtà mista, abbiamo constatato che l'utilizzo intenzionale di un unico modello di interazione end-to-end in un'applicazione è il modo migliore per garantire agli utenti risultati ottimali e un'esperienza eccezionale.  A questo scopo, in queste indicazioni relative all'interazione abbiamo incluso tre aspetti:
* Il materiale è stato strutturato attorno ai tre principali modelli di interazione e ai componenti e agli schemi necessari per ciascun modello.
* Sono state incluse istruzioni supplementari su altri vantaggi forniti dalla piattaforma.
* Sono incluse indicazioni per consentire di selezionare il modello di interazione appropriato per lo scenario specifico.

## <a name="multimodal-interaction-models"></a>Modelli di interazione multimodale

In base alle nostre ricerche e al lavoro finora svolto con i clienti, abbiamo scoperto che la maggior parte delle esperienze di realtà mista viene soddisfatta da tre principali modelli di interazione.

Per molti versi, il modello di interazione è lo schema mentale seguito dall'utente per completare i flussi.  Ognuno di questi modelli di interazione è ottimizzato per una serie di esigenze dei clienti e ciascuno è comodo, efficiente e utilizzabile a pieno titolo. 

La classifica seguente offre una panoramica semplificata.  Informazioni dettagliate per l'utilizzo di ogni modello di interazione sono collegate a immagini ed esempi di codice nelle pagine seguenti. 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modello</strong></td>
        <td><strong>Scenari di esempio</strong></td>
        <td><strong>Destinatari</strong></td>
        <td><strong>Hardware</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Mani e controller del movimento</a></td>
        <td>Esperienze nello spazio 3D, ad esempio layout e progettazione dello spazio, manipolazione di contenuti o simulazione.</td>
        <td>Ideale per i nuovi utenti, in combinazione con comandi vocali, tracciamento oculare o puntamento con la testa. Curva di apprendimento bassa. Esperienza utente coerente con tracciamento delle mani e 6 controller DoF.</td>
        <td>HoloLens 2<br>Visori VR immersive</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mani libere</a></td>
        <td>Esperienze contestuali in cui le mani dell'utente sono occupate, ad esempio apprendimento sul posto e gestione.</td>
        <td>È necessario un certo livello di apprendimento. Se le mani non sono disponibili, questo modello si adatta bene a comandi vocali e linguaggio naturale.</td>
        <td>HoloLens 2<br>HoloLens (prima generazione)<br>Visori VR immersive</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Puntamento con la testa e commit</a></td>
        <td>Esperienze di tipo click-through, ad esempio presentazioni 3D e demo.</td>
        <td>È necessario eseguire il training in dispositivi HMD, non in dispositivi mobili. Ideale per controller accessibili. Ideale per HoloLens (prima generazione).</td>
        <td>HoloLens 2<br>HoloLens (prima generazione)<br>Visori VR immersive<br>AR per dispositivi mobili</td>
    </tr>
</table>
<br>

Il modo migliore per assicurarsi che non siano presenti gap o interruzioni dell'interazione per l'esperienza consiste nel seguire le indicazioni per un singolo modello dall'inizio alla fine. 

Per velocizzare le attività di progettazione e sviluppo, abbiamo incluso informazioni dettagliate e collegamenti a immagini ed esempi di codice all'interno della documentazione relativa a ciascun modello.

Prima, tuttavia, le sezioni seguenti illustrano la procedura di selezione e implementazione di uno di questi modelli di interazione.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>Al termine di questa pagina, avrai appreso a:
 
* Scegliere un modello di interazione per il cliente
* Usare le indicazioni relative al modello di interazione
* Passare da un modello di interazione all'altro
* Progettare i passaggi successivi


## <a name="choose-an-interaction-model-for-your-customer"></a>Scegliere un modello di interazione per il cliente


È probabile che autori e sviluppatori abbiano già in mente quali tipi di esperienza di interazione vogliono avere i loro utenti.
Per promuovere un approccio alla progettazione incentrato sul cliente, è consigliabile attenersi alle indicazioni seguenti per selezionare il modello di interazione ottimizzato per il cliente specifico.

### <a name="why-follow-this-guidance"></a>Perché seguire le indicazioni?

* I nostri modelli di interazione sono testati in base a criteri obiettivi e soggettivi, ad esempio lo sforzo fisico e cognitivo, l'intuitività e la capacità di apprendimento. 
* Poiché l'interazione differisce, è possibile che anche gli inviti audio e video e il comportamento degli oggetti siano diversi da un modello all'altro.  
* Combinando parti di diversi modelli di interazione si rischia di ottenere inviti concorrenti, ad esempio raggi mano simultanei e un cursore di puntamento con la testa e commit, che possono confondere gli utenti.

Ecco alcuni esempi di come sono ottimizzati gli inviti e i comportamenti per ogni modello di interazione.  Notiamo spesso che le domande dei nuovi utenti sono simili, ad esempio: "Come si può capire se il sistema funziona? Come si può sapere quali azioni si possono eseguire? Come si può sapere se il sistema ha capito quali azioni sono state eseguite?"

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modello</strong></td>
        <td><strong>Come si può capire se il sistema funziona?</strong></td>
        <td><strong>Come si può sapere quali azioni si possono eseguire?</strong></td>
        <td><strong>Come si può sapere quali azioni sono state eseguite?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Mani e controller del movimento</a></td>
        <td>Si vede una mesh mano, un invito punta del dito o raggi mano/controllore.</td>
        <td>Si vedono handle afferrabili o un riquadro di delimitazione quando si avvicina la mano.</td>
        <td>Si sentono toni udibili e si vedono animazioni al momento di afferrare e rilasciare oggetti.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Puntamento con la testa e commit</a></td>
        <td>Si vede un cursore al centro del campo visivo.</td>
        <td>Il cursore di puntamento con la testa cambia stato quando è posizionato su determinati oggetti.</td>
        <td>Si vedono conferme visive e/o si sentono conferme udibili quando si intraprendono azioni.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Mani libere (puntamento con la testa e attesa)</a></td>
        <td>Si vede un cursore al centro del campo visivo.</td>
        <td>Si vede un indicatore di stato quando ci si sofferma su un oggetto con supporto per interazioni.</td>
        <td>Si vedono conferme visive e/o si sentono conferme udibili quando si intraprendono azioni.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mani libere (esecuzione di comandi vocali)</a></td>
        <td>Si vedono un indicatore di ascolto e sottotitoli che mostrano quello che il sistema ha sentito.</td>
        <td>Si ricevono messaggi vocali e suggerimenti.  Se si pronuncia una frase del tipo: "Cosa posso dire?", viene visualizzato un messaggio di feedback.</td>
        <td>Si vedono o si sentono conferme visive o udibili quando si dà un comando o quando si ottiene una disambiguazione dell'esperienza utente, se necessario.</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>Di seguito sono riportate le domande che, in base ai nostri riscontri, possono aiutare i team a scegliere un modello di interazione:
 
1.  D:  Gli utenti vogliono toccare gli ologrammi ed eseguire manipolazioni olografiche precise?<br><br>
R:  Se la risposta è affermativa, scegliere il modello di interazione mani e strumenti per la selezione della destinazione di precisione e la manipolazione con mani e controller del movimento.
 
2.  D:  Gli utenti devono avere le mani libere per poter eseguire attività reali?<br><br>
R:  In caso affermativo, prendere in considerazione il modello di interazione a mani libere, che offre un'eccezionale esperienza a mani libere attraverso interazioni basate sullo sguardo e sulla voce.
 
3.  D:  Gli utenti hanno tempo sufficiente per apprendere le interazioni per le applicazioni in realtà mista o hanno bisogno delle interazioni con la curva di apprendimento più bassa?<br><br>
R:  Per le interazioni più intuitive con curva di apprendimento minima è consigliabile scegliere il modello mani e strumenti, a condizione che gli utenti possano usare le mani per l'interazione.
 
4.  D:  Gli utenti usano i controller del movimento per le azioni di puntamento e manipolazione?<br><br>
R:  Il modello mani e strumenti include tutte le indicazioni per un'esperienza eccezionale con i controller del movimento.
 
5.  D:  Gli utenti usano un controller di accessibilità o un comune controller Bluetooth, ad esempio un dispositivo Clicker?<br><br>
R:  Per tutti i controller non tracciati è consigliabile usare il modello di puntamento con la testa e commit,  studiato per consentire a un utente di vivere un'intera esperienza in base a un semplice meccanismo di "selezione della destinazione e commit". 
 
6.  D: Gli utenti attraversano un'esperienza in modalità "click-through", ad esempio in un ambiente simile a una presentazione 3D, anziché spostarsi all'interno di layout pieni di controlli di interfaccia?<br><br>
R:  Se non è necessario usare molti controlli di interfaccia, il modello di puntamento con la testa e commit è un'opzione praticabile che consente agli utenti di non doversi preoccupare della selezione della destinazione. 
 
7.  D:  Gli utenti usano sia HoloLens (prima generazione) sia HoloLens 2/Windows Immersive (visore VR)?<br><br>
R:  Poiché quello di puntamento con la testa e commit è il modello di interazione per HoloLens (prima generazione), è consigliabile che gli autori che supportano HoloLens (prima generazione) usino questo modello per qualsiasi funzionalità o modalità che gli utenti possono sperimentare con un visore VR HoloLens (prima generazione).  Per informazioni dettagliate sull'eccezionale esperienza offerta da più generazioni di HoloLens, vedere la prossima sezione relativa al *passaggio da un modello di interazione all'altro*.
 
8.  D: Quali sono le indicazioni per gli utenti che in genere usano dispositivi mobili (muovendosi in uno spazio di grandi dimensioni o spostandosi da uno spazio all'altro) e per quelli che tendono a operare in un unico spazio?<br><br>
R:  Tutti i modelli di interazione sono adatti a questi utenti.  

> [!NOTE]
> Saranno [presto disponibili](index.md#news-and-notes) altre istruzioni di progettazione specifiche per le app.


## <a name="transition-interaction-models"></a>Passaggio da un modello di interazione all'altro
Per alcuni casi d'uso può essere necessario impiegare più modelli di interazione.  Ad esempio, per il "flusso di creazione" di un'app viene utilizzato il modello di interazione Mani e controller del movimento, ma per i tecnici sul campo si vuole impiegare una modalità a mani libere.  

Se per un'esperienza sono necessari più modelli di interazione, ci siamo accorti che molti utenti finali possono avere difficoltà a passare da un modello all'altro, in particolare gli utenti che hanno scarsa familiarità con la realtà mista.

> [!Note]
> Per aiutare i progettisti e gli sviluppatori a operare scelte che possono rivelarsi difficili nel campo della realtà mista, stiamo elaborando altre indicazioni per l'uso di più modelli di interazione.
 

## <a name="see-also"></a>Vedi anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Puntamento con la testa e attesa](gaze-and-dwell.md)
* [Manipolazione diretta con le mani](direct-manipulation.md)
* [Puntamento e commit con le mani](point-and-commit.md)
* [Movimenti](gestures.md)
* [Esecuzione di comandi vocali](voice-design.md)
* [Controller del movimento](motion-controllers.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Progettazione del mapping spaziale](spatial-mapping-design.md)
* [Comodità](comfort.md)

