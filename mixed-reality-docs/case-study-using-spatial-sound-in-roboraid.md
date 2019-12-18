---
title: Case Study-uso di un suono spaziale in RoboRaid
description: Il suono spaziale è una delle funzionalità più interessanti di Microsoft HoloLens, che offre agli utenti un modo per capire cosa accade quando gli oggetti sono fuori linea.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, RoboRaid, suono spaziale
ms.openlocfilehash: 1482c914d261cae698a1460873b217b0683cd16b
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181941"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Case Study-uso di un suono spaziale in RoboRaid

In questo articolo vengono descritte le specifiche esigenze del team di Microsoft HoloLens Experience durante la creazione di audio per [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j), uno sparatutto in realtà mista.

## <a name="the-tech"></a>Il Tech

Il [suono spaziale](spatial-sound.md) è una delle funzionalità più interessanti di Microsoft HoloLens, che offre agli utenti un modo per capire cosa accade quando gli oggetti sono fuori linea.

In RoboRaid, l'uso più ovvio ed efficace del suono spaziale è quello di avvisare il lettore di qualcosa che si verifica all'esterno della visione periferica dell'utente. Ad esempio, l'utente malfunzionante può entrare da una qualsiasi delle pareti analizzate nella stanza, ma se non ci si trova nella posizione in cui si trova, è possibile che si perda. Per avvertire l'utente di questa invasione, si riceverà un po' di audio distinto proveniente dal punto in cui si sta immettendo il violatore, che informa che è necessario agire rapidamente per arrestarlo.

## <a name="behind-the-scenes"></a>Dietro le quinte

Il processo di creazione di un suono spaziale per le app HoloLens è così nuovo e univoco e la mancanza di progetti precedenti da usare per riferimento può comportare una notevole difficoltà quando si verifica un problema. Ci auguriamo che questi esempi di problemi audio che abbiamo affrontato durante l'esecuzione di RoboRaid ti aiuteranno a creare audio per le tue app.

### <a name="be-mindful-of-taxing-the-cpu"></a>Tenere conto della tassazione della CPU

Il suono spaziale può richiedere la CPU. Per un'esperienza frenetica come RoboRaid, era fondamentale evitare che le istanze del suono spaziale fossero in un dato momento inferiore a otto. Nella maggior parte dei casi, è facile impostare il limite di istanze di eventi audio diversi, in modo che vengano terminate tutte le istanze che si verificano dopo il raggiungimento del limite. Ad esempio, quando i droni generano, i loro Scream sono limitati a tre istanze in un determinato momento. Considerando che solo quattro droni possono generare una sola volta, tre Scream sono molto perché non è possibile tenere traccia di molti eventi audio simili. In questo modo sono state liberate risorse per altri eventi audio spaziali, ad esempio esplosioni nemiche o nemici che si preparano a sparare.

### <a name="rewarding-a-successful-dodge"></a>Soddisfazione di una Dodge riuscita

Il meccanico che si sta evitando è uno degli aspetti più importanti del gioco in RoboRaid e anche un elemento che abbiamo ritenuto realmente univoco per l'esperienza HoloLens. Di conseguenza, volevamo che le Dodge fossero molto gratificanti per il lettore. È stato ottenuto il "mago" di Doppler per sembrare piuttosto tempestivo in fase di sviluppo. Inizialmente, il mio piano consisteva nell'usare un ciclo e modificarlo in tempo reale usando volume, pitch e Filter. L'implementazione di questa operazione è stata molto elaborata, pertanto prima di eseguire il commit delle risorse per compilarlo, abbiamo creato un prototipo a basso costo usando un asset con l'effetto Doppler preparato in solo per scoprire come si riteneva *. Il nostro sviluppo di talento lo ha fatto in modo che questo asset venga riprodotto esattamente 0,7 secondi prima che il proiettile fosse passato dall'orecchio del giocatore e i risultati fossero davvero straordinari. Inutile dirlo, abbiamo abbandonato la soluzione più complessa e implementato il prototipo.

*Per altre informazioni sulla creazione di un asset audio con l'effetto Doppler incorporato, vedere [100 Whooshes in 2 minuti](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).*  
<br>
![riuscito a schivare il proiettile di un nemico premia il lettore con un suono che soddisfi le proprie esigenze.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Ammaraggio di suoni inefficaci

Originariamente, avevamo voluto riprodurre un suono di esplosione dietro il lettore una volta che il proiettile nemico è stato schivato, ma abbiamo deciso di abbandonarlo per diversi motivi. In primo luogo, non si riteneva così efficace come il mago-by SFX usato per Dodge. Nel momento in cui il proiettile raggiunge un muro dietro di te, si sarebbe verificato un altro problema nel gioco che sarebbe stato molto simile alla maschera. In secondo luogo, non abbiamo avuto collisioni a livello di terra, quindi non riuscivamo a far giocare l'esplosione quando il proiettile raggiungeva il pavimento anziché i muri. Infine, c'era il costo della CPU del suono spaziale. L'Elite Scorpion Enemy (uno che può eseguire la ricerca per indicizzazione all'interno della parete) ha un attacco speciale che spara circa otto proiettili. Non solo questa situazione ha comportato una grande confusione nella combinazione, ma ha anche introdotto una terribile incrinatura perché la CPU era troppo complessa.

### <a name="communicating-a-hit"></a>Comunicazione di un riscontro

Si è verificato un problema interessante, che è stato ritenuto univoco per l'esperienza HoloLens, è stata la difficoltà di comunicare efficacemente con i giocatori che sono stati raggiunti. Ciò che rende un'esperienza di realtà mista riuscita è la sensazione che la storia si sta verificando. Ciò significa che è necessario ritenere che si stia combattendo un'invasione di robot alieni nel proprio salotto.

Ovviamente, i giocatori non hanno alcuna sensazione quando vengono colpiti, quindi è necessario trovare un modo per convincere il giocatore che ha avuto happed. Nei giochi convenzionali è possibile che venga visualizzata un'animazione che consente di conoscere il carattere che ha raggiunto un riscontro. in alternativa, è possibile che la schermata sia Flash rossa e che il carattere possa grugnire un po'. Poiché questi tipi di indicazioni non funzionano in un'esperienza di realtà mista, abbiamo deciso di combinare il segnale visivo con un suono effettivamente esagerato che indica che hai causato danni. Ho creato una grande sonorità e ho reso questo aspetto molto importante nella combinazione di tutti gli elementi. Quindi, per fare in modo che risulti ancora più, abbiamo aggiunto un breve messaggio di avviso come se fosse stato effettuato il sink di un sommergibile nucleare. 
<br>
![quando viene raggiunto un giocatore in RoboRaid, viene visualizzato un segnale visivo, ma viene anche visualizzato un segnale audio esagerato che indica che hanno causato danni.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Ottenere un grande suono da piccoli speaker

I relatori HoloLens sono piccoli e leggeri per soddisfare le esigenze del dispositivo, quindi non è possibile aspettarsi di ricevere troppo basso. Analogamente allo sviluppo per Smart Phone o dispositivi di gioco palmari, le finestre di progettazione e i compositori sono tenuti a tenere conto del contenuto della frequenza dei propri audio. È sempre necessario progettare suoni o scrivere musica con intervallo di frequenza completo, perché l'uso di cuffie è un'opzione per gli utenti. Tuttavia, per garantire la compatibilità con I relatori HoloLens, eseguo un test occasionalmente inserendo un EQ nel master di qualsiasi DAW che sto lavorando. L'impostazione EQ è costituita da un filtro High-Pass, da 600 a 700 Hz (non troppo ripida) e da un filtro low-pass a circa 10.000 (molto ripida). In questo modo si avrà un'idea Ballpark del modo in cui i suoni verranno rilasciati nel dispositivo.

Se si fa affidamento sui bassi per dare il senso della modifica dell'accordo nella musica, è possibile che la musica perda completamente il senso della radice quando si applica questa impostazione EQ. Per risolvere questo problema, ho aggiunto un altro livello alla spigola che è un'ottava più alta (con alcune armoniche avanzate) e la mescolo per ottenere il senso della radice. In alcuni casi, l'uso della distorsione per accelerare le armoniche consentirà un contenuto di frequenza sufficiente nell'intervallo superiore per fare in modo che il nostro cervello pensi che vi sia qualcosa sotto di esso. Questa operazione è valida per gli SFX come gli effetti, le esplosioni o i suoni per i momenti speciali, ad esempio i super attacchi del boss. In realtà non è possibile fare affidamento sul lato basso per dare al giocatore un senso di impatto o peso. Come per la musica, l'uso della distorsione per fornire un po' di crunch è stato decisamente utile.

### <a name="making-your-audio-cues-stand-out"></a>Emergenze dei segnali audio

Naturalmente, tutti gli utenti del team volevano musica Robo, pistole forti e esplosioni pazzesche; ma volevano anche essere in grado di ascoltare VoiceOver o qualsiasi altro spunto audio critico per i giochi.

In un gioco console con una gamma di frequenza completa sono disponibili più opzioni per dividere le frequenze a seconda dell'importanza del suono. Per RoboRaid, tuttavia, il numero di intervalli di frequenze che ho potuto rientrare tra i suoni era limitato. Se, ad esempio, si usa un filtro low-pass e si curva troppo a una parte superiore dello spettro, non si avrà nulla a che fare con il suono perché non c'è molto di basso livello.

Per fare in modo che RoboRaid sia il più grande possibile sul dispositivo, è stato necessario ridurre l'intervallo dinamico dell'intera esperienza e si è fatto ampio uso di ducking creando una gerarchia chiara di importanza per diversi tipi di suoni. Imposto il ducking da-2 a-6 dB a seconda dell'importanza. Personalmente non mi piace ovviare ai giochi, quindi ho impiegato molto tempo per ottimizzare l'intervallo di dissolvenza in entrata/uscita e la quantità di attenuazione del volume. Sono stati configurati bus distinti per un suono spaziale, un suono non spaziale, un VO e un bus secco senza Riverb per la musica, quindi sono stati creati bus di priorità molto alta, critici e non critici. Gli asset sono stati quindi impostati per accedere ai bus appropriati.

Spero che i professionisti audio siano in possesso di una grande quantità di divertimento e entusiasmo a lavorare sulle proprie app, come ho fatto per lavorare a RoboRaid. Non posso aspettare di vedere (e ascoltare) quali sono le persone di talento all'esterno di Microsoft per HoloLens.

## <a name="do-it-yourself"></a>Provare

Un trucco che ho scoperto per far sembrare "più grande" alcuni eventi, ad esempio le esplosioni, è quello di creare un asset mono per il suono spaziale e combinarlo con un asset stereo 2D, per riprodurlo in 3D. Questa operazione non comporta alcuna ottimizzazione, perché la presenza di una quantità eccessiva di informazioni nel contenuto stereo diminuisce la direzionalità degli asset mono. Tuttavia, l'ottenimento del giusto equilibrio comporterà la visualizzazione di grandi quantità di suoni che conterranno ai giocatori di trasformare le loro teste nella direzione giusta.

È possibile provare a usare le risorse audio seguenti:

**Scenario 1**
1. Scaricare [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) e impostare la riproduzione tramite un suono spaziale e assegnarlo a un evento.
2. Scaricare [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) e impostare la riproduzione in stereo 2D e assegnarla allo stesso evento indicato in precedenza. Poiché queste risorse vengono normalizzate in Unity, attenuare il volume di entrambi gli asset in modo da non ritagliare.
3. Riprodurre entrambi i suoni insieme. Spostare la testa per sentire la spazialità.

**Scenario 2**
1. Scaricare [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) e impostare la riproduzione tramite il suono spaziale e assegnarlo a un evento.
2. Riprodurre questo asset da solo e confrontarlo con l'evento dello scenario 1.
3. Provare a eseguire un saldo diverso di file mono e stereo.



## <a name="see-also"></a>Vedi anche
* [Audio spaziale](spatial-sound.md)
* [RoboRaid per Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
