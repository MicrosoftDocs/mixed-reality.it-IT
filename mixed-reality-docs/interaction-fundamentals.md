---
title: Panoramica di interazione multimodale
description: Panoramica dell'interazione multimodale
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Progettare sguardo, sguardo targeting, interazione, realtà mista
ms.openlocfilehash: 8c578d9a67f6809df69fb132f4c46a381726596e
ms.sourcegitcommit: d6d96d552ec10cd7e6502fbbc1905432e2878325
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524344"
---
# <a name="introducing-instinctual-interactions"></a>Introduzione a instinctual interazioni
La filosofia di interazioni semplice, instinctual sperimentare tutta la piattaforma Microsoft di realtà mista.  Sono state utilizzate tre passaggi per garantire che gli sviluppatori e progettisti di applicazioni possono offrire le interazioni semplice e intuitive per i clienti. 

In primo luogo, siamo quindi assicurati le straordinari sensori e tecnologie per l'input, tra cui mano rilevamento sotto controllo di rilevamento e linguaggio naturale, combinare in modelli di interazione multimodale invisibile.  Basato su ricerca, progettazione e lo sviluppo multimodally e non basati su singoli input, è essenziale per la creazione di esperienze instinctual.

In secondo luogo, è possibile riconoscere che molti sviluppatori di supportare più dispositivi, indipendentemente dal fatto che questa 2 HoloLens e HoloLens (dal 1 ° generazione) o HoloLens e VR.  In modo che è stato progettato i nostri modelli di interazione per funzionare in diversi dispositivi (anche se la tecnologia input varia in ogni dispositivo).  Ad esempio, interazione decisamente su un auricolare coinvolgenti di Windows con un controller 6DoF e interazione decisamente su un 2 HoloLens entrambi usare gli affordance identici e modelli, rendendo più semplice per applicazioni multidispositivo. È non solo questo utile per gli sviluppatori e progettisti, ma è scontata agli utenti finali. 

Infine, anche se è possibile riconoscere che sono presenti migliaia di validità, coinvolgenti e interazioni magiche presenti possibili in MR, si è constatato che utilizza intenzionalmente un modello di sola interazione end-to-end in un'applicazione è il modo migliore per assicurarsi che gli utenti hanno esito positivo e avere un'esperienza ottimale.  A tale scopo, sono state incluse tre operazioni in questo materiale sussidiario interazione:
* È stata strutturata questo materiale sussidiario i tre modelli di interazione principale e i componenti e i modelli necessari per ogni
* Sono state incluse istruzioni aggiuntive su altri vantaggi che la nostra piattaforma di fornisce
* Sono incluse indicazioni per consentire di selezionare il modello di interazione appropriato per lo scenario


## <a name="three-multimodal-interaction-models"></a>Tre modelli di interazione multimodale
A seconda della ricerca e il lavoro con i clienti a oggi, abbiamo scoperto che i tre modelli di interazione principale soddisfare la maggior parte delle esperienze di realtà mista.

In molti modi, il modello di interazione è modello mentale dell'utente per il completamento dei flussi.  Ognuno di questi modelli di interazione è ottimizzato per una serie di esigenze dei clienti e ognuno è conveniente, efficiente ed utilizzabile in sé. 

Il grafico seguente viene fornita una panoramica semplificata.  Informazioni dettagliate per l'utilizzo di ogni modello di interazione sono collegate nelle pagine seguenti con le immagini ed esempi di codice.  

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
        <td><strong>Fit</strong></td>
        <td><strong>Hardware</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Strumenti e le mani</a></td>
        <td>Esperienze spaziali 3D<br>ad esempio spaziale layout e progettazione, manipolazione del contenuto o simulazione</td>
        <td>Ottima soluzione per i nuovi utenti<br>Curva di apprendimento<br>Piedi affordance visual semplice<br>Esperienza utente coerente tra mano di rilevamento e 6DoF controller<br>Bene quando è associata vocali, estasiati occhio rilevamento o head</td>
        <td>HoloLens 2<br>Windows coinvolgenti con 6DoF controller</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mani libere</a></td>
        <td>Esperienze contestuale in cui le mani dell'utente sono occupate, ad esempio nel processo di apprendimento, manutenzione</td>
        <td>Alcuni di apprendimento obbligatorio<br>Se non sono disponibili le mani<br>coppie con vocali e il linguaggio naturale</td>
        <td>HoloLens 2<br>HoloLens (dal 1 ° generazione)<br> Coinvolgenti di Windows</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Puntamento con la testa e commit</a></td>
        <td>Drill-through esperienze, ad esempio 3D presentazioni, demo</td>
        <td>Richiede la formazione su HMDs ma non su dispositivi mobili<br>Ideale per i controller accessibili<br>Ideale per HoloLens (dal 1 ° generazione)</td>
        <td>HoloLens 2<br>HoloLens (dal 1 ° generazione)<br> Coinvolgenti di Windows<br> AR per dispositivi mobili</td>
    </tr>
</table>
<br>

Il modo migliore per assicurarsi che non sono presenti gap o difetti nell'interazione per l'esperienza consiste nel seguire le linee guida per un singolo modello dall'inizio alla fine. 

Per aumentare la velocità di progettazione e sviluppo, sono state incluse informazioni dettagliate e collegamenti a esempi di codice e le immagini entro il code coverage di ogni modello.

Ma prima di tutto le sezioni seguenti eseguire la procedura di selezione e implementazione di uno di questi modelli di interazione.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>Al termine di questa pagina, è possibile comprendere le linee guida su:
 
* Scelta di un modello di interazione per il cliente
* Seguendo le indicazioni fornite del modello di interazione
* In fase di transizione tra i modelli di interazione
* Passaggi successivi di progettazione

## <a name="choosing-an-interaction-model-for-your-customer"></a>Scelta di un modello di interazione per il cliente

È probabile che gli sviluppatori e autori già alcune idee mente i tipi di esperienza di interazione che per gli utenti desiderano.
Per favorire un approccio incentrato sul cliente alla progettazione, è consigliabile seguendo le indicazioni seguenti per selezionare il modello di interazione che è ottimizzato per il cliente.

### <a name="why-follow-this-guidance"></a>Il motivo per cui segue questo materiale sussidiario?

* I modelli di interazione vengono verificati i criteri soggettivi, ad esempio fisica e cognitiva sforzo e intuitiveness learnability e obiettivo. 
* Interazione è diverso, audio e video affordance e comportamento di tali oggetti possono anche differire tra i modelli di interazione.  
* Combinando le parti più modelli di interazione crea il rischio di affordance concorrenti, ad esempio rays mano simultanei e un cursore sguardo, che sovraccaricare e confondere gli utenti.

Di seguito sono riportati alcuni esempi del modo in cui affordance e i comportamenti sono ottimizzati per ogni modello di interazione.  È possibile notare spesso nuovi utenti come domande simili, ad esempio "come faccio a sapere il sistema funziona, come faccio a sapere che cosa può fare, e come si capisce se comprendere ciò che ho appena fatto?"

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
        <td><strong>Come si capisce funziona?</strong></td>
        <td><strong>Come sapere cosa posso fare?</strong></td>
        <td><strong>Come sapere ciò che ho appena fatto?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Strumenti e le mani</a></td>
        <td>Una mano mesh, vedere un intuitività punta del dito o manualmente / rays controller.</td>
        <td>Viene visualizzato un riquadro vengono visualizzate quando la mano si avvicina o handle grabbable.</td>
        <td>Posso sentire sonori e visualizzare animazioni in quadratini di ridimensionamento e il rilascio.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Puntamento con la testa e commit</a></td>
        <td>Viene visualizzato un cursore al centro del mio campo visivo.</td>
        <td>Il cursore sguardo Cambia stato quando su determinati oggetti.</td>
        <td>Posso vedere o ascolta le conferme e acustico quando intervenire.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Mani libere (sguardo e permanenza)</a></td>
        <td>Viene visualizzato un cursore al centro del mio campo visivo.</td>
        <td>Viene visualizzato un indicatore di stato quando il caso di soffermarsi su un oggetto si.</td>
        <td>Posso vedere o ascolta le conferme e acustico quando intervenire.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Mani libere (esecuzione di comandi vocali)</a></td>
        <td>Viene visualizzato un indicatore di attesa e sottotitoli in lingua originale che mostra ciò che il sistema sentito parlare.</td>
        <td>Ricevo messaggi vocali e suggerimenti.  Quando dico "frasi?" Vedere commenti e suggerimenti.</td>
        <td>Posso vedere o ascolta le conferme e acustico quando dà un comando o ottenere disambiguazione UX quando necessario.</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>Di seguito sono le domande che abbiamo scoperto help teams selezionare un modello di interazione:
 
1.  D:  Gli utenti desiderano touch ologrammi ed eseguono manipolazioni holographic precisione?
R:  In questo caso, consultare il modello di interazione mani e strumenti per la selezione della precisione e manipolazione con controller di movimento o mani.
 
2.  D:  Gli utenti devono mantenere le mani gratuite, per le attività del mondo reale?
R:  In questo caso, esaminare il modello di interazione invisibile all'utente, che offre un'esperienza ottimale invisibile all'utente tramite le interazioni basate su sguardo e vocali.
 
3.  D:  Gli utenti devono imparare a utilizzare le interazioni per la mia applicazione di realtà mista, o devono le interazioni con la curva di apprendimento più bassa possibile?
R:  È consigliabile il modello mani e strumenti per la curva di apprendimento più bassa e le interazioni più intuitive, purché siano in grado di usare le mani per l'interazione con gli utenti.
 
4.  D:  Gli utenti usano i controller di movimento per la modifica e che puntano?
R:  Il modello di strumenti e le mani include tutte le linee guida per un'esperienza ottimale con i controller di movimento.
 
5.  D:  Gli utenti usano un controller di accessibilità o un controller Bluetooth comuni, ad esempio un clicker?
R:  Si consiglia il modello Head sguardo ed eseguire il commit per tutti i controller non rilevate.  È progettato per consentire a un utente attraversare un'intera esperienza con un semplice meccanico "target e commit". 
 
6.  D: Gli utenti solo l'avanzamento viene eseguito tramite un'esperienza facendo clic su"tramite" (ad esempio in un ambiente simile a presentazione 3d), anziché passare ad alta densità layout dei controlli dell'interfaccia utente?
R:  Se gli utenti non sono necessario controllare molti dell'interfaccia utente, Head sguardo ed eseguire il commit offrono un'opzione learnable in cui gli utenti non sono necessario preoccuparsi di destinazione. 
 
7.  D:  Gli utenti usano entrambi HoloLens (dal 1 ° generazione) e HoloLens 2 / r coinvolgenti di Windows (auricolari VR):  Poiché Head sguardo ed eseguire il commit è il modello di interazione per HoloLens (dal 1 ° generazione), è consigliabile che gli autori che supportano HoloLens (dal 1 ° generazione) usare Head sguardo ed eseguire il commit per qualsiasi funzionalità o le modalità che gli utenti potrebbero riscontrare in un HoloLens (dal 1 ° generazione) visore Vr.  Vedere la sezione seguente nel *modelli di interazione in fase di transizione* per informazioni dettagliate su come rendere una straordinaria esperienza più generazioni di HoloLens.
 
8.  D: Per quanto riguarda per gli utenti che sono in genere per dispositivi mobili relativi a uno spazio di grandi dimensioni o lo spostamento tra gli spazi, e gli utenti tendono a funzionare in uno spazio singolo?  
R:  Uno dei modelli di interazione funzionerà per questi utenti.  

> [!NOTE]
> Informazioni aggiuntive specifiche per la progettazione di app [presto](index.md#news-and-notes).


## <a name="transition-interaction-models"></a>Modelli di interazione di transizione
Vi sono anche casi in cui i casi d'uso richieda che utilizzano più di un modello di interazione.  Ad esempio, il flusso di app"creazione" utilizza il modello di interazione mani e gli strumenti, ma si desidera utilizzare una modalità invisibile all'utente per i tecnici del campo.  

Se più modelli di interazione richiede l'esperienza, abbiamo scoperto che molti utenti finali potrebbero riscontrare difficoltà in fase di transizione da un modello a un'altra, in particolare gli utenti finali che hanno familiarità con MR.

> [!Note]
> Per consentire le finestre di progettazione di Guida e gli sviluppatori attraverso le scelte che possono essere difficile in MR, stiamo lavorando su altre indicazioni per l'uso di più modelli di interazione.
 

## <a name="see-also"></a>Vedere anche
* [Puntamento con la testa e commit](gaze-and-commit.md)
* [Manipolazione diretta](direct-manipulation.md)
* [Puntamento e commit](point-and-commit.md)
* [Selezione della destinazione con lo sguardo](gaze-targeting.md)
* [Movimenti](gestures.md)
* [Progettazione delle interazioni vocali](voice-design.md)
* [Controller del movimento](motion-controllers.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Progettazione del mapping spaziale](spatial-mapping-design.md)
* [Comodità](comfort.md)
