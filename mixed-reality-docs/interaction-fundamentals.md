---
title: Interazioni istintive
description: Scopri la filosofia delle interazioni semplici e istintive alla base di tutta la piattaforma di realtà mista.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, sguardo fisso, selezione della destinazione con lo sguardo fisso, interazione, progettazione, HoloLens, MMR, multimodale
ms.openlocfilehash: 6b54d6e844c1b501a0835fc3a48deb4932ba551d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539725"
---
# <a name="introducing-instinctual-interactions"></a>Introduzione alle interazioni istintive

![Manipolazione da lontano con le mani](images/04_InteractionFundamentals.png)

La filosofia delle interazioni semplici e istintive è alla base di tutta la piattaforma di realtà mista. Abbiamo adottato tre accorgimenti per consentire ai progettisti e agli sviluppatori di applicazioni di fornire ai clienti interazioni facili e intuitive. 

In primo luogo, ci siamo assicurati che i sensori e le tecnologie di input, tra cui il tracciamento oculare e delle mani e l'input in linguaggio naturale, si combinino in perfetti modelli di interazione multimodale.  
In base alle nostre ricerche, le attività di progettazione e sviluppo all'interno di un framework multimodale (e non basate su singoli input) sono la chiave di volta per creare esperienze istintive.

In secondo luogo, constatiamo che molti sviluppatori destinano le loro applicazioni a più dispositivi HoloLens, come HoloLens 2 e HoloLens (prima generazione) oppure HoloLens e VR.  
Abbiamo quindi progettato modelli di interazione in grado di funzionare in tutti i dispositivi, anche se la tecnologia di input varia da uno all'altro.  
Ad esempio, per l'interazione da lontano con un visore VR immersive di Windows dotato di un controller 6DoF e per l'interazione da lontano con un dispositivo HoloLens 2 vengono usati gli stessi inviti e modelli, semplificando lo sviluppo di applicazioni per più dispositivi e assicurando interazioni più naturali con gli utenti. 

Anche se riconosciamo che possono esistere migliaia di interazioni efficaci, coinvolgenti e magiche nella realtà mista, abbiamo constatato che l'utilizzo intenzionale di un unico modello di interazione end-to-end in un'applicazione è il modo migliore per garantire agli utenti risultati ottimali e un'esperienza eccezionale. A questo scopo, in queste indicazioni relative all'interazione abbiamo incluso tre aspetti:
* Materiale specifico incentrato sui tre principali modelli di interazione e sui componenti e schemi necessari per ciascun modello.
* Istruzioni supplementari su altri vantaggi offerti dalla piattaforma.
* Indicazioni di carattere generale, utili per selezionare il modello di interazione appropriato per uno scenario di sviluppo specifico.

## <a name="multimodal-interaction-models"></a>Modelli di interazione multimodale

In base alle nostre ricerche e al feedback dei clienti, abbiamo scoperto che la maggior parte delle esperienze di realtà mista viene soddisfatta da tre principali modelli di interazione. Per molti versi, il modello di interazione è lo schema mentale seguito dall'utente per completare un flusso di lavoro. Ognuno di questi modelli di interazione è ottimizzato per una serie di esigenze dei clienti ed è comodo, efficiente e applicabile se usato in modo corretto. 

La classifica seguente offre una panoramica semplificata. Informazioni dettagliate per l'utilizzo di ogni modello di interazione sono collegate a immagini ed esempi di codice nelle pagine seguenti. 

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
        <td>Ideale per i nuovi utenti, in combinazione con comandi vocali, tracciamento oculare o puntamento con la testa. Curva di apprendimento bassa. Esperienza utente coerente con tracciamento delle mani e controller 6DoF.</td>
        <td>HoloLens 2<br>Visori VR immersive</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mani libere</a></td>
        <td>Esperienze contestuali in cui le mani dell'utente sono occupate, ad esempio apprendimento sul posto e manutenzione.</td>
        <td>È necessario un certo livello di apprendimento. Se le mani non sono disponibili, il dispositivo si adatta bene a comandi vocali e linguaggio naturale.</td>
        <td>HoloLens 2<br>HoloLens (prima generazione)<br>Visori VR immersive</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Sguardo e commit</a></td>
        <td>Esperienze di tipo click-through, ad esempio presentazioni 3D e demo.</td>
        <td>È necessario eseguire il training in dispositivi HMD, non in dispositivi mobili. Ideale per controller accessibili. Ideale per HoloLens (prima generazione).</td>
        <td>HoloLens 2<br>HoloLens (prima generazione)<br>Visori VR immersive<br>AR per dispositivi mobili</td>
    </tr>
</table>
<br>

Per evitare che siano presenti lacune nell'esperienza di interazione dell'utente, è preferibile seguire le indicazioni per un singolo modello dall'inizio alla fine.

Le sezioni seguenti illustrano la procedura di selezione e implementazione di uno di questi modelli di interazione.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>Al termine di questa pagina, avrai appreso a:
 
* Scegliere un modello di interazione per il cliente
* Implementare il modello di interazione
* Passare da un modello di interazione all'altro
* Progettare i passaggi successivi


## <a name="choose-an-interaction-model-for-your-customer"></a>Scegliere un modello di interazione per il cliente

In genere, gli sviluppatori e gli autori valutano tutti i tipi di interazione che i clienti possono avere. Per incoraggiare un approccio alla progettazione incentrato sul cliente, è consigliabile attenersi alle indicazioni seguenti per selezionare il modello di interazione ottimizzato per il cliente specifico.

### <a name="why-follow-this-guidance"></a>Perché seguire le indicazioni?

* I nostri modelli di interazione sono testati in base a criteri obiettivi e soggettivi, ad esempio lo sforzo fisico e cognitivo, l'intuitività e la capacità di apprendimento. 
* Poiché esistono diversi tipi di interazione, è possibile che anche gli inviti audio/video e il comportamento degli oggetti siano diversi da un modello di interazione all'altro.  
* Combinando parti di diversi modelli di interazione si rischia di ottenere inviti concorrenti, ad esempio raggi della mano simultanei e un cursore di puntamento con la testa. Tutto questo può inondare l'utente di troppe informazioni e confonderlo.

Ecco alcuni esempi di come sono ottimizzati gli inviti e i comportamenti per ogni modello di interazione. Notiamo spesso che le domande dei nuovi utenti sono simili, ad esempio: _"Come si può capire se il sistema funziona?"_ , _"Come si può sapere quali azioni si possono eseguire?"_ e _"Come si può sapere se il sistema ha capito quali azioni sono state eseguite?"_

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
        <td>Si vede una mesh mano, un invito punta del dito o raggi della mano/controller.</td>
        <td>Si vedono punti di controllo afferrabili o un riquadro delimitatore quando si avvicina la mano a un oggetto.</td>
        <td>Si sentono toni udibili e si vedono animazioni al momento di afferrare e rilasciare oggetti.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Puntamento con la testa e commit</a></td>
        <td>Si vede un cursore al centro del campo visivo.</td>
        <td>Il cursore cambia stato quando è posizionato su determinati oggetti.</td>
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
        <td>Si ricevono messaggi vocali e suggerimenti. Quando si dice: "Cosa posso dire?" viene visualizzato un messaggio di feedback.</td>
        <td>Si vedono o si sentono conferme visive o udibili quando si dà un comando o si ottiene una disambiguazione dell'esperienza utente, se necessario.</a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a>Di seguito sono riportate alcune domande che, in base ai nostri riscontri, possono aiutare i team a scegliere un modello di interazione:
 
1.  D:  Gli utenti vogliono toccare gli ologrammi ed eseguire manipolazioni olografiche precise?<br><br>
R:  Se la risposta è affermativa, scegli il modello di interazione mani e controller del movimento per la selezione della destinazione di precisione e la manipolazione.
 
2.  D:  Gli utenti devono avere le mani libere per poter eseguire attività reali?<br><br>
R:  In caso affermativo, prendi in considerazione il modello di interazione a mani libere, che offre un'eccezionale esperienza a mani libere attraverso interazioni basate sullo sguardo e sulla voce.
 
3.  D:  Gli utenti hanno tempo sufficiente per apprendere le interazioni per le applicazioni di realtà mista o hanno bisogno delle interazioni con la curva di apprendimento più bassa?<br><br>
R:  Per le interazioni più intuitive e con la curva di apprendimento più bassa, è consigliabile scegliere il modello mani e controller del movimento, purché gli utenti possano usare le mani per l'interazione.
 
4.  D:  Gli utenti usano i controller del movimento per le azioni di puntamento e manipolazione?<br><br>
R:  Il modello mani e controller del movimento include tutte le indicazioni per un'esperienza eccezionale con i controller del movimento.
 
5.  D:  Gli utenti usano un controller di accessibilità o un comune controller Bluetooth, ad esempio un dispositivo Clicker?<br><br>
R:  Per tutti i controller non tracciati è consigliabile usare il modello di puntamento con la testa e commit, studiato per consentire a un utente di vivere un'intera esperienza in base a un semplice meccanismo di "selezione della destinazione e commit". 
 
6.  D: Gli utenti attraversano un'esperienza in modalità "click-through", ad esempio in un ambiente simile a una presentazione 3D, invece di spostarsi all'interno di layout pieni di controlli di interfaccia?<br><br>
R:  Se non è necessario usare molti controlli di interfaccia, il modello di puntamento con la testa e commit è un'opzione praticabile che consente agli utenti di non doversi preoccupare della selezione della destinazione. 
 
7.  D:  Gli utenti usano sia i visori VR immersive di HoloLens (prima generazione) sia quelli di HoloLens 2/Windows Mixed Reality?<br><br>
R:  Poiché quello di puntamento con la testa e commit è il modello di interazione per HoloLens (prima generazione), è consigliabile che gli autori che supportano HoloLens (prima generazione) usino questo modello per qualsiasi funzionalità o modalità che gli utenti possono sperimentare con un visore VR HoloLens (prima generazione). Per informazioni dettagliate sull'eccezionale esperienza offerta da più generazioni di HoloLens, vedere la prossima sezione relativa al *passaggio da un modello di interazione all'altro*.
 
8.  D: Quali sono le indicazioni per gli utenti che in genere usano dispositivi mobili, muovendosi in uno spazio di grandi dimensioni o spostandosi da uno spazio all'altro, e per quelli che tendono a operare in un unico spazio?<br><br>
R:  Tutti i modelli di interazione sono adatti a questi utenti.  

> [!NOTE]
> Saranno [presto disponibili](news.md) altre istruzioni di progettazione specifiche per le app.


## <a name="transitioning-interaction-models"></a>Passaggio da un modello di interazione all'altro
Per alcuni casi d'uso può essere necessario impiegare più modelli di interazione. Ad esempio, per il flusso di creazione di un'applicazione viene usato il modello di interazione _"mani e controller del movimento"_ , ma per i tecnici sul campo è preferibile adottare una modalità a mani libere.
Se per un'esperienza sono necessari più modelli di interazione, tieni presente che molti utenti possono avere difficoltà a passare da un modello all'altro, in particolare quelli che hanno scarsa familiarità con la realtà mista.

> [!Note]
> Continueremo a fornire altre indicazioni che saranno rese disponibili per sviluppatori e progettisti per informarli su come, quando e perché usare più modelli di interazione di realtà mista.
 

## <a name="see-also"></a>Vedi anche
* [Comodità](comfort.md)
* [Interazione basata sullo sguardo](eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo e commit](gaze-and-commit.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Controller del movimento](motion-controllers.md)
* [Mapping spaziale](spatial-mapping.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Input vocale](voice-input.md)


