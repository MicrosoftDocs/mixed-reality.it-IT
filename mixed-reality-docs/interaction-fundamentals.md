---
title: Panoramica di interazione multimodale
description: Panoramica dell'interazione multimodale
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mista realtà, sguardo, sguardo targeting, interazione, progettare, hololens, MMR, multimodali
ms.openlocfilehash: 771ebe44dc984c9d4550638bef405810d86b8d69
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730827"
---
# <a name="introducing-instinctual-interactions"></a>Introduzione a instinctual interazioni

La filosofia di interazioni semplice, instinctual sperimentare tutta la piattaforma di realtà mista Microsoft (MMR), dal software di hardware.

Tali interazioni instinctual usano tutte le tecnologie di input disponibili, tra cui rilevamento interno a esterno, mano di rilevamento, sotto controllo di rilevamento e il linguaggio naturale, nei modelli di interazione multimodale invisibile. Basato su ricerca, progettazione e sviluppo multimodals e non si basa sui singoli input, è fondamentale durante la creazione di esperienze instinctive.

I modelli di interazione Instinctual Allinea inoltre naturalmente a tipi di dispositivo.  Distante interazione in un visore VR immersivi con un 6 gradi di controller di libertà e interazione distante su 2 HoloLens, ad esempio, usare la stessa affordance, modelli e i comportamenti.  È non solo questo utile per gli sviluppatori e progettisti, ma è scontata agli utenti finali.


Infine, anche se è possibile riconoscere che sono presenti migliaia di validità, coinvolgenti e interazioni magiche presenti possibili in MR, si è constatato che utilizza intenzionalmente un modello di sola interazione end-to-end in un'applicazione è il modo migliore per assicurarsi che gli utenti hanno esito positivo e avere un'esperienza ottimale.  A tale scopo, sono state incluse tre operazioni in questo materiale sussidiario interazione:
* È stata strutturata questo materiale sussidiario i tre modelli di interazione principale e i componenti e i modelli necessari per ogni
* Sono state incluse istruzioni aggiuntive su altri vantaggi che la nostra piattaforma di fornisce
* Sono incluse indicazioni per consentire di selezionare il modello di interazione appropriato per lo scenario

## <a name="multimodal-interaction-models"></a>Modelli di interazione multimodale

A seconda della ricerca e il lavoro con i clienti a oggi, abbiamo scoperto tre modelli di interazione principale che soddisfare la maggior parte delle esperienze di realtà mista.  

Questi modelli di interazione può essere paragonato a modello mentale dell'utente per il completamento dei flussi.

Ognuno di questi modelli di interazione è conveniente, efficiente ed utilizzabile in sé e tutte sono ottimizzate per una serie di esigenze dei clienti. Visualizzare il grafico seguente, per gli scenari, esempi e i vantaggi di ogni modello di interazione.  

**Modello** | **[Strumenti e le mani](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)** | **[Mani libere](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)** | **[Estasiati ed eseguire il Commit](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**
|--------- | --------------| ------------| ---------|
**Scenari di esempio** | Del contenuto 3D esperienze spaziali, ad esempio spatial layout e progettazione, modifica o simulazione | Esperienze contestuale in cui sono occupate mani dell'utente, ad esempio, nella formazione, la manutenzione del processo| Esperienze drill-through interno, ad esempio 3D presentazioni e demo
**Fit** | Un'ottima soluzione per i nuovi utenti, wit accoppiata vocali, dell'occhio sguardo rilevamento o head. Curva di apprendimento. Esperienza utente coerente tra mano di rilevamento e 6 controller i gradi di libertà. | Alcuni di apprendimento obbligatorio. Se sono coppie non disponibile anche con vocali e il linguaggio naturale | Richiede la formazione su HMDs ma non su dispositivi mobili. Ideale per i controller accessibili migliore per HoloLens (dal 1 ° generazione) |
**Hardware** | HoloLens 2 Immersive auricolari | HoloLens 2 HoloLens (dal 1 ° generazione) auricolari coinvolgenti | HoloLens 2 Immersive auricolari | HoloLens 2 HoloLens (dal 1 ° generazione) coinvolgenti auricolari AR per dispositivi mobili |

Informazioni dettagliate per l'uso in perfetta sintonia, tutti gli input disponibili in ogni modello di interazione sono nelle pagine che seguono, nonché le illustrazioni e collegamenti a contenuto di esempio dal nostro MRTK di Unity.


## <a name="choose-an-interaction-model-for-your-customer"></a>Scegliere un modello di interazione per il cliente


È probabile che gli sviluppatori e autori anche già alcune idee mente i tipi di esperienza di interazione che desiderano agli utenti di avere.
Per favorire un approccio incentrato sul cliente alla progettazione, è consigliabile seguendo le indicazioni seguenti per selezionare il modello di interazione che è ottimizzato per il cliente.

### <a name="why-follow-this-guidance"></a>Il motivo per cui segue questo materiale sussidiario?

* I modelli di interazione vengono verificati i criteri soggettivi, ad esempio fisica e cognitiva sforzo e intuitiveness learnability e obiettivo. 
* Interazione è diverso, audio e video affordance e comportamento di tali oggetti possono anche differire tra i modelli di interazione.  
* Combinando le parti più modelli di interazione crea il rischio di affordance concorrenti, ad esempio rays mano simultanei e un cursore, head sguardo che sovraccaricare e confondere gli utenti.

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
        <td>Il cursore head sguardo Cambia stato quando su determinati oggetti.</td>
        <td>Posso vedere o ascolta le conferme e acustico quando intervenire.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Mani libere (Head-sguardo e permanenza)</a></td>
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
 
1.  D:  Gli utenti desiderano touch ologrammi ed eseguono manipolazioni holographic precisione?<br><br>
R:  In questo caso, consultare il modello di interazione mani e strumenti per la selezione della precisione e manipolazione con controller di movimento o mani.
 
2.  D:  Gli utenti devono mantenere le mani gratuite, per le attività del mondo reale?<br><br>
R:  In questo caso, esaminare il modello di interazione invisibile all'utente, che offre un'esperienza ottimale invisibile all'utente tramite le interazioni basate su sguardo e vocali.
 
3.  D:  Gli utenti devono imparare a utilizzare le interazioni per la mia applicazione di realtà mista, o devono le interazioni con la curva di apprendimento più bassa possibile?<br><br>
R:  È consigliabile il modello mani e strumenti per la curva di apprendimento più bassa e le interazioni più intuitive, purché siano in grado di usare le mani per l'interazione con gli utenti.
 
4.  D:  Gli utenti usano i controller di movimento per la modifica e che puntano?<br><br>
R:  Il modello di strumenti e le mani include tutte le linee guida per un'esperienza ottimale con i controller di movimento.
 
5.  D:  Gli utenti usano un controller di accessibilità o un controller Bluetooth comuni, ad esempio un clicker?<br><br>
R:  Si consiglia il modello Head sguardo ed eseguire il Commit per tutti i controller non rilevate.  È progettato per consentire a un utente attraversare un'intera esperienza con un semplice meccanico "target e commit". 
 
6.  D: Gli utenti solo l'avanzamento viene eseguito tramite un'esperienza facendo clic su"tramite" (ad esempio in un ambiente simile a presentazione 3d), anziché passare ad alta densità layout dei controlli dell'interfaccia utente?<br><br>
R:  Se gli utenti non sono necessario controllare molti dell'interfaccia utente, Head sguardo ed eseguire il commit offrono un'opzione learnable in cui gli utenti non sono necessario preoccuparsi di destinazione. 
 
7.  D:  Gli utenti usano entrambi HoloLens (dal 1 ° generazione) e HoloLens 2 / coinvolgenti di Windows (auricolari VR)<br><br>
R:  Poiché Head sguardo ed eseguire il commit è il modello di interazione per HoloLens (dal 1 ° generazione), è consigliabile che gli autori che supportano HoloLens (dal 1 ° generazione) usare Head sguardo ed eseguire il commit per qualsiasi funzionalità o le modalità che gli utenti potrebbero riscontrare in un HoloLens (dal 1 ° generazione) visore Vr.  Vedere la sezione seguente nel *modelli di interazione in fase di transizione* per informazioni dettagliate su come rendere una straordinaria esperienza più generazioni di HoloLens.
 
8.  D: Per quanto riguarda per gli utenti che sono in genere per dispositivi mobili relativi a uno spazio di grandi dimensioni o lo spostamento tra gli spazi, e gli utenti tendono a funzionare in uno spazio singolo?<br><br>
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
