---
title: Case study - spaziale progettazione per HoloTour
description: Per creare una presentazione virtuale 3D veramente coinvolgente per Microsoft HoloLens, i video panoramiche e holographic panorami rappresentano solo una parte della formula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, HoloTour, spaziale Studio case audio
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603643"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>Case study - spaziale progettazione per HoloTour

Per creare una presentazione virtuale 3D veramente coinvolgente per Microsoft HoloLens, i video panoramiche e holographic panorami rappresentano solo una parte della formula. Progettazione audio che Jason Syltebo parla del modo in cui audio è stato acquisito ed elaborati affinché si ritiene che non si ha effettivamente in ognuna delle posizioni in HoloTour.

## <a name="the-tech"></a>Le tecnologie innovative

Le immagini accattivanti e holographic scene che holotour presenti sono solo una parte della creazione di un'esperienza di realtà mista credibili. Mentre vntana può apparire solo visivamente davanti a un utente, il [spaziale audio](spatial-sound.md) funzionalità di HoloLens consente audio provenire da tutte le direzioni, che offre all'utente un'esperienza più completa dei sensori.

Suono spaziale consente di assegnare segnali acustici per indicare una direzione in cui l'utente dovrebbe diventare oppure per informare l'utente sono presenti altre vntana vengano visualizzati entro il relativo spazio. Possiamo anche collegare un suono direttamente a un ologrammi e aggiornare continuamente la direzione e la distanza che di ologramma proviene da un utente per far sembrare come se l'audio proviene direttamente da tale oggetto.

Con HoloTour, abbiamo voluto sfruttare i vantaggi delle funzionalità spaziali audio di HoloLens per creare un ambiente di ambiente a 360 gradi, sincronizzato con il video per ottenere le novità introdotte sonic posizioni specifiche.

## <a name="behind-the-scenes"></a>Dietro le quinte

Abbiamo creato HoloTour esperienze dei due percorsi diversi: Roma e Picchu Machu. Per rendere queste presentazioni sentirsi autentico e accattivanti volevamo evitare di utilizzare suoni generici e invece acquisire audio direttamente dai percorsi in cui abbiamo parlato riprese.

### <a name="capturing-the-audio"></a>Acquisizione dell'audio

Nel nostro [case study di informazioni sull'acquisizione di contenuto visivo per HoloTour](case-study-capturing-and-creating-content-for-holotour.md), abbiamo parlato di progettazione personalizzata di rig la fotocamera. È costituito da 14 GoPro fotocamere digitali contenuti in un alloggiamento stampa 3D, progettato per le dimensioni specifiche della treppiede. Per acquisire audio da questo rig, abbiamo aggiunto una matrice/quad-microfono sotto le telecamere, che inseriti da un'unità di registrazione di tutti i canali di 4 compact che veniva aggiunto alla base della treppiede. Abbiamo scelto microfoni che non solo eseguita correttamente, ma che ha un footprint estremamente ridotto, in modo da non nasconde i colori di visualizzazione della camera.

![Rig personalizzato della fotocamera e microfono](images/camera-rig-microphones-300px.png)<br>
*Rig personalizzato della fotocamera e microfono*

Il programma di installazione acquisita suono in quattro direzioni dal percorso preciso la fotocamera, offrendo in tal modo le informazioni necessarie per ricreare un panorama acustico 3D utilizzando spaziale audio, che è stato possibile sincronizzarle successivamente al video a 360 gradi.

Una delle difficoltà con l'audio di matrice fotocamera è che si è alla mercé del ciò che viene registrato al momento dell'acquisizione. Anche se l'acquisizione video è valida, l'acquisizione audio può divenire problematica a causa di suoni off fotocamera, ad esempio sommergibile, aeroplani o venti elevate. Per garantire che avevamo tutti gli elementi che necessari, abbiamo utilizzato una serie di unità di registrazione per dispositivi mobili stereo e mono per ottenere elementi asincroni, l'ambiente in specifici punti di interesse in ogni posizione. Questa acquisizione è importante in quanto offre la finestra di progettazione audio consente di eseguire ricerche contenuto pulito e utilizzabile che è utilizzabile in fase di post-produzione per elaborare gli interessi e consente di aggiungere ulteriori direzionalità.

Qualsiasi giorno di acquisizione specifica genererebbero un numero elevato di file. Era importante sviluppare un sistema per rilevare i file che corrispondono a un percorso specifico o di una fotocamera cattura. L'unità di registrazione è stato impostato l'assegnazione automatica del nome file per data e numero di take e si potrebbe eseguire il backup alla fine del giorno per unità esterne. Minimo, lo Slate verbalmente l'inizio di registrazioni audio è stato importante in quanto in questo modo contestuali sarà possibile identificare facilmente il contenuto dovrebbe filenames diventare un problema. Era inoltre importante per noi a ardesia visivamente il rig di acquisizione della fotocamera come video e audio sono stati registrati come supporto separato e doveva essere sincronizzati durante il post.

### <a name="editing-the-audio"></a>Modifica file audio

Tornando al studio dopo l'acquisizione di andata e ritorno, è il primo passaggio nella creazione di un'esperienza acustico coinvolgente e direzionale per controllare tutti l'acquisizione audio per un percorso, il prelievo out il migliore accetta e identificare eventuali evidenziazioni che è stato possibile applicare modo creativo durante integrazione. L'audio viene quindi modificato e la pulizia. Ad esempio, horn un'automobile l per la durata o meno un secondo e ripetuti più volte, può essere sostituito e unire con sezioni di dati audio non interattiva e ambiente dalla stessa acquisizione.

Dopo aver stabilita la modifica di video per una posizione nella finestra di progettazione audio consente di sincronizzare audio corrispondente. A questo punto abbiamo collaborato con acquisizione con fotocamera rig e acquisizione per dispositivi mobili per decidere quali elementi o combinazione di questi, funzionerà per compilare una scena audio coinvolgente e concreto. Una tecnica che sono stati trovati utile è aggiungere tutti gli elementi di audio in un audio editor e compilazione rapide lineare fittizi preliminare per sperimentare con diversa combinazione idee. Questo ci ha offerto meglio le idee in formato giunse il momento di compilare le quinte HoloTour effettive.

### <a name="assembling-the-scene"></a>Assemblaggio della scena

Il primo passaggio per la creazione di una scena 3D ambiente consiste nel creare un ambiente di generale suoni in background ambiente ciclo che supporterà altri elementi audio interattivi e funzionalità in una scena. In questo modo, è stato scelto un approccio olistico verso le tecniche di implementazione diversa determinato dalle esigenze specifiche e i criteri di progettazione di qualsiasi particolare scena. Alcuni scene potrebbero indicizzare verso tramite l'acquisizione della fotocamera sincronizzato, mentre altri potrebbero richiedere un approccio più dettagliato che usa più discreto inserito suoni, elementi interattivi e musica e suono effetti per i momenti più cinematografico HoloTour.

Durante l'indicizzazione all'uso dell'acquisizione audio fotocamera, abbiamo inserito spaziale abilitata suono ambiente audio istanze di emissione FixIt corrispondente alle coordinate direzionale dell'orientamento della fotocamera in modo che la visualizzazione di fotocamera Nord riproduce audio dal microfono del Nord e allo stesso modo per le altre istruzioni cardinale. Queste istanze di emissione FixIt sono bloccati world, vale a dire l'utente può abilitare liberamente propria testa in relazione a tali istanze di emissione FixIt e cambierà di conseguenza, il suono di modellazione in modo efficace il suono di in esecuzione in tale posizione. Ascolta Navona Piazza o di Pantheon per alcuni esempi di scene di cui usano una combinazione ottima di audio fotocamera acquisita.

Un approccio diverso comportato la riproduzione di un ambiente stereo ciclo in combinazione con istanze di emissione FixIt audio spaziale è racchiuso tra la scena riproduzione di suoni occasionali che sono casuali in termini di frequenza di volume, il passo e trigger. Crea un ambiente con un senso avanzata di direzionalità. In Aguas Calientes, ad esempio, è possibile ascoltare come ogni quadrante del panorama ha specifiche istanze di emissione FixIt che intenzionalmente evidenziare aree specifiche della geografia, ma contribuiscono a creare un ambiente complessivo coinvolgente e concreto.

## <a name="tips-and-tricks"></a>Suggerimenti e consigli

Quando si inseriranno insieme audio per una scena, esistono altri metodi utilizzabili per evidenziare ulteriormente la direzionalità e full immersion, basate sull'utilizzo delle funzionalità spaziali audio di HoloLens. È stato fornito un elenco di alcune sotto, restare in ascolto il prossimo tentativo HoloTour per loro.
* **Cerca destinazioni**: Si tratta di suoni che attivano solo quando si sta esaminando un oggetto specifico o l'area del frame holographic. Ad esempio, la ricerca nella direzione di café il lato street in Navona Piazza di Roma leggermente attiverà i suoni di un ristorante occupato.
* **Visione artificiale locale**: Il percorso anche se HoloTour contiene determinati beats dove tour di Guida, supportato da vntana, verrà illustrati un argomento in modo approfondito. Ad esempio, non appena la facciata di Pantheon dissolvenze per rivelare il oculus, audio riverbero inserito come una funzione di emissione 3D dall'interno della finestra di Pantheon incoraggia l'utente per esplorare il modello interno.
* **Migliorata la direzionalità**: All'interno di numerose scene, abbiamo inserito suoni in vari modi per aggiungere la direzionalità. Nella scena Pantheon, ad esempio, riprodotto il suono di quest'opera è stato inserito come una funzione di emissione separato abbastanza ravvicinati per l'utente in modo da cui è stato possibile farsi un'idea di 'parallasse sonic' come essi esaminato tutto lo spazio di play. Nella scena Salinas de Maras del Perù, la singola prospettiva di alcuni dei flussi di poco sono stati inseriti come istanze di emissione FixIt separati per compilare un ambiente di ambiente più coinvolgente e concreto che circonda l'utente con i suoni autentici della località di.
* **Emissione spline**: L'emissione di audio spaziale speciale viene spostato nello spazio 3D rispetto alla posizione dell'oggetto a che è collegato visual. Un esempio di questo oggetto durante il training in Picchu Machu, in cui è stato usato un emettitore di spline di tipo per avere un'idea distinta di direzionalità e lo spostamento dei.
* **Musica e SFX**: Alcuni aspetti di HoloTour che rappresentano un approccio più stilizzato o cinematografico usano musica e suono effetti per elevare il livello di impatto emotivo. In battaglia gladiator alla fine del tour Roma, effetti speciali, ad esempio whooshes o stingers sono stati usati per rafforzare l'effetto delle etichette visualizzati nelle scene.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>Audio Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche
* [Spaziale audio](spatial-sound.md)
* [Progettazione spaziale](spatial-sound-design.md)
* [Audio spaziale in Unity](spatial-sound-in-unity.md)
* [MR Spatial 220](holograms-220.md)
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
