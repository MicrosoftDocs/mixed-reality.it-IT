---
title: 'Case Study: progettazione di suoni spaziali per HoloTour'
description: Per creare una presentazione virtuale 3D realmente immersiva per Microsoft HoloLens, i video panoramici e i paesaggi olografici sono solo parte della formula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, HoloTour, audio spaziale, case study
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522433"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>Case Study: progettazione di suoni spaziali per HoloTour

Per creare una presentazione virtuale 3D realmente immersiva per Microsoft HoloLens, i video panoramici e i paesaggi olografici sono solo parte della formula. La finestra di progettazione audio Jason Syltebo spiega in che modo l'audio è stato acquisito ed elaborato per fare in modo che l'utente sia in realtà in ognuna delle posizioni di HoloTour.

## <a name="the-tech"></a>Il Tech

Le bellissime immagini e le scene olografiche visualizzate in HoloTour sono solo una parte della creazione di un'esperienza di realtà mista credibile. Mentre gli ologrammi possono essere visualizzati solo visivamente davanti a un utente, la funzionalità [audio spaziale](spatial-sound.md) di HoloLens consente all'audio di provenire da tutte le direzioni, che offre all'utente un'esperienza sensoriale più completa.

Il suono spaziale consente di fornire segnali audio per indicare la direzione in cui l'utente deve attivare o per consentire all'utente di sapere se sono presenti più ologrammi da visualizzare all'interno del proprio spazio. Possiamo anche alleghiamo un suono direttamente a un ologramma e aggiorniamo continuamente la direzione e la distanza che l'ologramma è da un utente per fare in modo che sembri che il suono provenga direttamente da tale oggetto.

Con HoloTour è stato voluto sfruttare le funzionalità audio spaziali di HoloLens per creare un ambiente di ambiente di 360 gradi, sincronizzato con il video per rivelare le evidenziazioni soniche di posizioni specifiche.

## <a name="behind-the-scenes"></a>Dietro le quinte

Sono state create esperienze HoloTour in due posizioni diverse: Roma e Machu Picchu. Per fare in modo che questi tour siano autentici e accattivanti, abbiamo voluto evitare di usare i suoni generici e di acquisire l'audio direttamente dalle posizioni in cui ci stavamo filmando.

### <a name="capturing-the-audio"></a>Acquisizione dell'audio

Nel [case study sull'acquisizione del contenuto visivo per HoloTour](case-study-capturing-and-creating-content-for-holotour.md), abbiamo parlato della progettazione personalizzata del rig della fotocamera. È costituito da 14 fotocamere GoPro contenute in un'abitazione stampata in 3D, progettate per le dimensioni specifiche del treppiede. Per acquisire audio da questo rig, è stato aggiunto un array a quattro microfoni sotto le fotocamere, che è stato inserito in un'unità di registrazione compatta a 4 canali che si trovava alla base del treppiede. Abbiamo scelto i microfoni che non solo venivano eseguiti correttamente, ma con un footprint molto ridotto, in modo da non occludere la visualizzazione della fotocamera.

![Rig fotocamera e microfono personalizzati](images/camera-rig-microphones-300px.png)<br>
*Rig fotocamera e microfono personalizzati*

Questa configurazione ha acquisito un suono in quattro direzioni dalla posizione precisa della fotocamera, fornendo informazioni sufficienti per ricreare una panoramica 3D uditiva usando un suono spaziale, che è possibile sincronizzare successivamente con il video di 360 gradi.

Uno dei problemi relativi all'audio dell'array della fotocamera è che si è alla mercé di ciò che viene registrato al momento dell'acquisizione. Anche se l'acquisizione video è valida, l'acquisizione del suono può risultare problematica a causa di suoni fuori dalla fotocamera, ad esempio sirene, aeroplani o venti elevati. Per assicurarci che tutti gli elementi necessari siano stati usati, abbiamo usato una serie di unità di registrazione stereo e mono per ottenere elementi di ambiente asincroni in punti di interesse specifici in ogni posizione. Questa acquisizione è importante perché consente alla finestra di progettazione di suoni di cercare contenuti puliti e utilizzabili che possono essere usati in fase di produzione per creare interesse e aggiungere ulteriore direzionalità.

Un determinato giorno di acquisizione genera un numero elevato di file. È stato importante sviluppare un sistema per tenere traccia dei file corrispondenti a una posizione specifica o a una foto. L'unità di registrazione è stata configurata in modo da assegnare un nome automatico ai file in base alla data e assumere il numero ed è possibile eseguirne il backup alla fine del giorno per le unità esterne. Almeno, il fatto che l'inizio delle registrazioni audio sia stato annullato in modo verbale è importante, in quanto ciò consente di identificare facilmente i nomi di file. È stato inoltre importante visualizzare in modo visivo l'acquisizione di rig della fotocamera poiché il video e l'audio sono stati registrati come supporti distinti e devono essere sincronizzati durante il post.

### <a name="editing-the-audio"></a>Modifica dell'audio

Tornando a Studio dopo il viaggio di acquisizione, il primo passaggio per l'assemblaggio di un'esperienza fonetica direzionale e coinvolgente consiste nel rivedere tutta l'acquisizione audio per una posizione, scegliendo tra i migliori e identificando eventuali evidenziazioni che potrebbero essere applicate in modo creativo durante integrazione. L'audio viene quindi modificato e pulito. Ad esempio, un clacson automobilistico con una frequenza di un secondo e una ripetizione di alcune volte possono essere sostituiti e Uniti con sezioni di audio di ambiente non interattiva dalla stessa acquisizione.

Una volta stabilita la modifica del video per un percorso, la finestra di progettazione audio può sincronizzare l'audio corrispondente. A questo punto abbiamo lavorato con la funzionalità di acquisizione della fotocamera e l'acquisizione di dispositivi mobili per decidere quali elementi, o una combinazione di essi, funzioneranno per creare una scena audio immersiva. Una tecnica utile consiste nell'aggiungere tutti gli elementi acustici in un editor audio e creare simulazioni lineari veloci per sperimentare idee combinate diverse. In questo modo, abbiamo creato idee migliori quando si è giunto il momento di creare gli effettivi scenari di HoloTour.

### <a name="assembling-the-scene"></a>Assemblaggio della scena

Il primo passaggio per la creazione di una scena di ambiente 3D consiste nel creare un letto di suoni di ciclo di ambiente di background generale che supporteranno altre funzionalità e gli elementi audio interattivi in una scena. In questo modo, abbiamo adottato un approccio olistico a diverse tecniche di implementazione determinate dalle esigenze specifiche e dai criteri di progettazione di qualsiasi scena particolare. Alcune scene possono essere indicizzate in base all'uso della fotocamera sincronizzata, mentre altre potrebbero richiedere un approccio più curato che usa suoni più discretamente posizionati, elementi interattivi e musica e effetti audio per i momenti più cinematografici in HoloTour.

Quando si esegue l'indicizzazione sull'uso dell'audio di acquisizione della fotocamera, sono stati inseriti gli emettitori audio spaziali abilitati per il suono che corrispondono alle coordinate direzionali dell'orientamento della fotocamera, in modo che la visualizzazione della fotocamera Nord riproduca audio dal microfono Nord e allo stesso modo per le altre direzioni cardinali. Questi emettitori sono bloccati in tutto il mondo, ovvero è possibile che l'utente ritorni liberamente in relazione a questi emettitori e il suono cambierà di conseguenza, modellando in modo efficace il suono in quel percorso. Ascoltare Piazza Navona o il Pantheon per esempi di scene che usano una combinazione di audio acquisita con la fotocamera.

Un approccio diverso prevede la riproduzione di un ambiente stereo a ciclo in combinazione con i generatori di suoni spaziali posizionati in una scena che suona un suono casuale, in termini di volume, pitch e frequenza del trigger. In questo modo viene creato un ambiente con un senso di direzionalità migliorato. In Aguas Calientes, ad esempio, è possibile ascoltare il modo in cui ogni quadrante del panorama dispone di emettitori specifici che evidenziano intenzionalmente aree specifiche della geografia, ma interagiscono per creare un ambiente immersivo generale.

## <a name="tips-and-tricks"></a>Suggerimenti e trucchi

Quando si combinano audio per una scena, sono disponibili alcuni metodi aggiuntivi che consentono di evidenziare ulteriormente la direzionalità e l'immersione, sfruttando al meglio le funzionalità audio spaziali di HoloLens. È stato fornito un elenco di alcuni di seguito, in ascolto per la prossima volta che si prova a usare HoloTour.
* **Cerca destinazioni**: Si tratta di suoni che vengono attivati solo quando si esamina un oggetto specifico o un'area del frame olografico. Se, ad esempio, si esamina la direzione del caffè sul lato strada a Roma, Piazza Navona attiverà leggermente i suoni di un ristorante occupato.
* **Visione locale**: Il viaggio, tuttavia, HoloTour contiene alcuni ritmi in cui la Guida introduttiva, che aiuta gli ologrammi, esplorerà un argomento in modo approfondito. Ad esempio, poiché la facciata del Pantheon si risolve per rivelare l'Oculus, il riverbero di audio inserito come emettitore 3D dall'interno del Pantheon invita l'utente a esplorare il modello interno.
* **Direzionalità avanzata**: In molte scene, abbiamo inserito i suoni in diversi modi per aggiungere la direzionalità. Nella scena Pantheon, ad esempio, il suono della fontana è stato inserito come un emettitore separato sufficientemente vicino all'utente, in modo da ottenere un senso di "Sonic Parallax" Man mano che si aggira lo spazio di riproduzione. Nella scena Salinas de Mara del Perù, il singolo punto di vista di alcuni flussi è stato inserito come emettitori distinti per creare un ambiente di ambiente più immersivo, che circonda l'utente con i suoni autentici di tale percorso.
* **Emettitore spline**: Questo emettitore di suoni spaziali speciale si sposta nello spazio 3D rispetto alla posizione visiva dell'oggetto a cui è collegato. Un esempio di questo è stato il treno di Machu Picchu, in cui è stato usato un emettitore spline per fornire un senso di direzionalità e movimento distinti.
* **Musica e SFX**: Alcuni aspetti di HoloTour che rappresentano un approccio più stilizzato o cinematografico usano musica e effetti audio per aumentare l'impatto emotivo. Nel gladiatore Battle alla fine del tour di Roma sono stati usati effetti speciali come whooshes o Stingers per contribuire a rafforzare l'effetto delle etichette visualizzate in scene.

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>Finestra di progettazione audio@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche
* [Audio spaziale](spatial-sound.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Audio spaziale in Unity](spatial-sound-in-unity.md)
* [MR Spatial 220](holograms-220.md)
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
