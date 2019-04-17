---
title: Modulo lunare
description: LunarModule è un'app di esempio open source di laboratori di progettazione realtà mista di Microsoft. Con questo progetto, è possibile imparare ad ampliarne i movimenti di base degli Hololens due mani utilizza il rilevamento e controller Xbox di input, creare gli oggetti che sono reattivi per surface mapping e di ricerca di piano e implementare sistemi di menu semplice.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà, esempio le app, progettazione, HoloLens mista di Windows
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602483"
---
# <a name="lunar-module"></a>Modulo lunare

>[!NOTE]
>Questo articolo illustra un esempio di analisi esplorativo è stata creata nel [laboratori di progettazione di realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), una posizione in cui si condivide quanto appreso sulle e per suggerimenti su mista lo sviluppo di app di realtà. Nostri articoli correlati alla progettazione e il codice si evolverà come si ottengono nuove informazioni.

[Modulo lunare](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) è un'app di esempio open source di laboratori di progettazione realtà mista di Microsoft. Con questo progetto, è possibile imparare ad ampliarne i movimenti di base degli Hololens due mani utilizza il rilevamento e controller Xbox di input, creare gli oggetti che sono reattivi per surface mapping e di ricerca di piano e implementare sistemi di menu semplice. Tutti i componenti del progetto sono disponibili per l'uso nelle proprie esperienze di app di realtà mista.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Rethinking esperienza classica per realtà mista di Windows

Livello più alto nella atmosfera, un piccolo ship simile a quella del modulo Apollo sondaggi metodicamente matrice terreno riportato di seguito. La potenza senza pilota spot un'area di destinazione appropriato. La parte discendente è complicata, ma per fortuna, questo percorso è diventato più volte prima di...

![Interfaccia originale dal 1979 lunare Lander del Atari](images/640px-atari-lunar-lander.png)<br>
*Interfaccia originale dal 1979 lunare Lander del Atari*

[Lander lunare](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) è un modello di distribuzione classica per computer in cui i giocatori tentano di avviare un programma pilota un lander lunare in un punto di terreno lunare flat. Chiunque nasce la 1970s molto probabilmente trascorso ore in un arcade con ai loro stessi occhi associate a questa spedizione vettore plummeting dal cielo. Un lettore si sposta le spedizione verso un'area di destinazione desiderata aumenta il terreno per rivelare progressivamente maggiori dettagli. Esito positivo significa destinazione entro la soglia di velocità orizzontali e verticali-safe. Vengono assegnati punti per periodo di tempo trascorso di destinazione e il rimanente carburante, con un moltiplicatore in base alla dimensione dell'area di destinazione.

A parte la modalità di gioco, l'era arcade, giochi di portata un'innovazione costante degli schemi di controllo. Dalle configurazioni di joystick e pulsante 4-way più semplice (illustrato nell'originalissima [Pac Man](https://en.wikipedia.org/wiki/Pac-Man)) per gli schemi estremamente specifici e complessi visualizzati degli anni ' 90 e 00s (analoghe a quelle di combattimento slitte delle guide e i simulatori golf). Lo schema di input utilizzato nella macchina Lander lunare è particolarmente interessante per due motivi: inquadrano i punti di forza e partecipate.

![Console arcade del Lander lunare del Atari](images/atariconsole.png)<br>
*Console della Atari Lander lunare arcade*

Il motivo per cui è stata così tante altre società di giochi e Atari decide di reinventa l'input?

Un elemento kid illustrando un arcade verrà naturalmente incuriosito il più recente, flashiest macchina. Ma Lander lunare features un meccanico input novel che mi ha colpito distinguersi dalla massa.

Lander lunare usa due pulsanti per la rotazione di spedizione sinistro e destro e un **levetta spinta** per controllare la quantità di spinta produce la spedizione. La levetta assomigliasse offre agli utenti un certo livello di eleganza in grado di fornire un joystick regolare. È anche è un componente comune ai pannelli di controllo aviation moderne. Atari desiderava Lander lunare per l'utente nella sensazione che essi sono stati infatti distribuzione pilota di un modulo lunare. Questo concetto è noto come **tattili full immersion**.

Full immersion tattili è l'esperienza di feedback sensoriale di eseguire azioni ripetitive. In questo caso, l'azione ripetitiva regolare la levetta di limitazione e la rotazione che gli occhi vedere e ascolta orecchio, consente di collegare quest ' ultimo all'atto della raggiungono una nave superficie lunare. Questo concetto può essere associato alla psicologico concetto di "flusso". In cui un utente è completamente assorbito in un'attività che presenta la combinazione corretta di richiesta di verifica e reward o parole più semplici, risultano "nella"zona.

Senza dubbio, il tipo più importante di full immersion nella realtà mista è full immersion spaziale. Lo scopo di realtà mista è ingannare noi che questi oggetti digitali presenti nel mondo reale. Si sta la sintesi vntana nel nostro ambiente circostante, a livello spaziale si è immersi nel esperienze e interi ambienti. Ciò non significa che è ancora non è possibile utilizzare altri tipi di full immersion nelle nostre esperienze allo stesso Atari tattili full immersion in Lander lunare.

## <a name="designing-with-immersion"></a>Progettazione con full immersion

Come è potrebbe essere applichiamo tattili full immersion per un aggiungere volumetrici e aggiornato per il Atari classico? Prima di affrontare lo schema di input, deve essere affrontato il costrutto del gioco per spazio 3D.

![Visualizzazione mapping superficie in HoloLens](images/surfacemapping.png)<br>
*Visualizzazione mapping spaziale in HoloLens*

Sfruttando automobilista dell'utente, abbiamo in modo efficace le opzioni di terreno infinita per il modulo lunare di destinazione. Per rendere il gioco più simile a quella originale titolo, un utente potrebbe potenzialmente modificare e posizionare i riquadri di destinazione delle diverse difficoltà nel proprio ambiente.

![Il modulo lunare volo](images/640px-lm-hero.jpg)<br>
*Il modulo lunare volo*

Richiedere all'utente di conoscere lo schema di input, controllare la spedizione e hanno una destinazione di dimensioni ridotte a è tanto da porre. Una corretta esperienza di gioco di funzionalità garantirebbe il giusto di verifica e di reward. L'utente deve essere in grado di scegliere un livello di difficoltà, con la modalità più semplice semplicemente richiedere all'utente a terra correttamente in un'area definita dall'utente in un'area di analisi di HoloLens. Dopo che un utente ottiene il blocco del gioco, si può quindi attivando le difficoltà associate alle proprie esigenze.

### <a name="adding-input-for-hand-gestures"></a>Aggiunta di input per movimenti della mano

Input di base di HoloLens ha solo due movimenti - [Air toccare e Bloom](gestures.md). Gli utenti non debbano ricordare sfumature contestuali o un elenco di bucato di movimenti specifici che rende l'interfaccia della piattaforma versatile sia facile da imparare. Mentre il sistema può esporre solo queste due movimenti, HoloLens come un dispositivo è in grado di rilevare le due mani alla volta. Il codice per Lander lunare è un' [app immersive](app-model.md) che significa che abbiamo la possibilità di estendere il set di base dei movimenti di utilizzare due mani e aggiungere nostro squisitamente tattili mezzi per la navigazione modulo lunare.

Esaminando lo schema di controllo originale, tornare **dovevamo nel risolvere spinta e rotazione**. Il problema è rotazione nel nuovo contesto aggiunge un altro asse (tecnicamente due, ma l'asse Y è meno importante per la destinazione). I movimenti di spedizione distinti due prestano naturale per eseguire il mapping a ogni indicatore:

![Toccare e trascinare movimento per ruotare lander su tutti e tre gli assi](images/module-handdrag.gif)<br>
*Toccare e trascinare movimento per ruotare lander su tutti e tre gli assi*

**Thrust**

La levetta nella macchina arcade originale mappata a una scala di valori, maggiore sarà la levetta è stata spostata la spedizione è stata applicata tramite altre. Una sfumatura importante da sottolineare qui è l'utente può richiedere il trasferimento di controllo e mantenere un valore desiderato. È possibile usare in modo efficace il comportamento di tocco e trascinare per ottenere lo stesso risultato. Il valore di spinta inizia da zero. L'utente tocca e trascina per aumentare il valore. A questo punto è stato possibile lasciare che escono per conservare i dati. Qualsiasi modifica del valore di movimenti di tocco e trascinamento sarebbe il delta dal valore originale.

**Rotazione**

Questo è un po' più difficile. Con i pulsanti "Ruota" holographic a toccare rende per un'esperienza terribile. Non c'è un controllo fisico per sfruttare i vantaggi, in modo che il comportamento deve provenire da manipolazione di un oggetto che rappresenta il lander o con lander stesso. Abbiamo trovato un metodo tramite tocco e trascinare che consente a un utente in modo efficace "push e pull", nella direzione desiderata devono affrontare. Ogni volta che un utente tocca e include, il punto nello spazio in cui è stato avviato il movimento diventi l'origine per la rotazione. Il trascinamento dall'origine converte il delta di traduzione dell'icona della mano (X, Y, Z) e lo applica al delta di valori di rotazione del lander. O, più semplicemente *trascinando <> – sinistra a destra, backup <> – verso il basso per inoltrare <> – nuovamente in spazi ruota nave conseguenza*.

Poiché il HoloLens è possibile monitorare due mani, la rotazione può essere assegnata per l'icona della mano destra mentre spinta è controllato da sinistra. Eleganza è un fattore determinante per l'esito positivo in questo gioco. Il *ritiene* di queste interazioni è la priorità più alta assoluta. In particolare nel contesto di full immersion tattili. Una nave che reagisce troppo rapidamente sarebbe difficile inutilmente guidare, mentre uno troppo lenta richiede all'utente di "push e pull" nella spedizione per una lungo le quantità di tempo.

### <a name="adding-input-for-game-controllers"></a>Aggiunta dell'input di gioco.

Movimenti della mano nel HoloLens forniscono un metodo novel di un controllo granulare, è ancora presente determinata mancanza di feedback tattili 'true' che si ottengono da controlli analogici. La connessione di un controller di giochi Xbox consente di riportare online il senso di physicality, sfruttando al contempo le chiavi di controllo per mantenere il controllo granulare.

Esistono diversi modi per applicare lo schema di controllo relativamente semplice per il controller Xbox. Poiché stiamo cercando di più vicino di arcade originale impostata come possibile, rimanere **spinta** viene eseguito il mapping migliore per il pulsante di trigger. Questi pulsanti sono controlli analogici, ovvero devono avere più di una semplice *accensione e spegnimento* indicato, dipendono effettivamente il grado di pressione che imposti su di essi. Questo ci offre un costrutto simile come il **levetta spinta**. A differenza del gioco originale e il movimento di mano, questo controllo verrà tagliato spinta di spedizione dopo che un utente interrompe l'inserimento di pressione sul trigger. Offre comunque all'utente lo stesso livello di eleganza come il gioco arcade originale.

![Viene eseguito il mapping thumbstick sinistro per rotazione ed eseguire il rollback, viene eseguito il mapping a destra thumbstick per intonazione ed eseguire il rollback](images/thumbsticksidebyside.gif)<br>
*Viene eseguito il mapping thumbstick sinistro per rotazione ed eseguire il rollback; viene eseguito il mapping a destra thumbstick per intonazione ed eseguire il rollback*

La doppia levette naturalmente si prestano a rotazione ship controllo. Purtroppo, sono disponibili 3 assi in cui è possibile ruotare la spedizione e due levette che supportano due assi. Questa mancata corrispondenza indica che entrambi una levetta controlli un asse. o sovrapposizione degli assi per la levette. La prima soluzione finisce sente "interrotto" poiché levette blend intrinsecamente loro locale valori X e Y. La seconda soluzione necessari alcuni test per trovare gli assi ridondanti sono più semplice. Nell'esempio finale viene utilizzato *rotazione* e *roll* (assi X e Y) per il thumbstick sinistro, e *passo* e *roll* (assi X e Z) il diritto thumbstick. Si ritiene più naturali come *roll* sembra in modo indipendente da associare a bene *rotazione* e *passo*. Come nota a margine, utilizzando per entrambi levette *eseguire il rollback* avviene anche sul doppio del valore di rotazione; è divertente vera e propria per avere la lander cicli do.

Questa app di esempio viene illustrato il riconoscimento come spaziale e full immersion tattili può modificare considerevolmente un'esperienza grazie alla modalità di input estendibile di realtà mista Windows. Mentre potrebbe essere Lander lunare per raggiungere 40 anni di età, i concetti esposti con che little ottagono con legs risiederanno all'infinito. Quando possibile immaginare il futuro, esaminare il motivo per cui non passato?

## <a name="technical-details"></a>Dettagli tecnici

È possibile trovare prefabs e script per l'app di esempio di modulo lunare sul [mista realtà progettazione Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Linville Addison</b><br>UX Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche
* [Controller di movimento](motion-controllers.md)
* [Movimenti](gestures.md)
* [Tipi di App di realtà mista](types-of-mixed-reality-apps.md)
