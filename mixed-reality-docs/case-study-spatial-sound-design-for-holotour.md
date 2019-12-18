---
title: 'Case Study: progettazione di suoni spaziali per HoloTour'
description: Per creare una presentazione virtuale 3D realmente immersiva per Microsoft HoloLens, i video panoramici e i paesaggi olografici sono solo parte della formula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, HoloLens, HoloTour, audio spaziale, case study
ms.openlocfilehash: f2dd704089d9c76b7ba175a4a1ad5cebf9ec6c68
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181926"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>Case Study: progettazione di suoni spaziali per HoloTour

I video panoramici e i paesaggi olografici sono solo parte della formula per una presentazione virtuale di Microsoft HoloLens realmente immersiva. Questo articolo descrive come è stato usato il suono per verificare che l'utente sia effettivamente in ogni località di HoloTour.

## <a name="the-tech"></a>Il Tech

Le bellissime immagini e le scene olografiche visualizzate in HoloTour sono solo una parte di un'esperienza di realtà mista credibile. Mentre gli ologrammi possono essere visualizzati solo visivamente davanti a un utente, il [suono spaziale](spatial-sound.md) fornito da HoloLens da tutte le direzioni fornisce un'esperienza sensoriale più completa.

Il suono spaziale fornisce indicazioni per indicare una direzione che l'utente deve attivare o per informare l'utente della presenza di più ologrammi da visualizzare all'interno del proprio spazio. Possiamo anche alleghi un suono direttamente a un ologramma e aggiorniamo continuamente la direzione e la distanza con cui l'ologramma è dall'utente. Questa tecnica fa sembrare che il suono provenga direttamente da tale oggetto.

Per HoloTour, è stato voluto sfruttare le funzionalità audio spaziali di HoloLens per creare un ambiente di ambiente di 360 gradi sincronizzato con il video per rivelare le evidenziazioni soniche di posizioni specifiche.

## <a name="behind-the-scenes"></a>Dietro le quinte

Sono state create esperienze HoloTour in due posizioni diverse: Roma e Machu Picchu. Per fare in modo che questi tour siano autentici e accattivanti, abbiamo voluto acquisire l'audio dalle posizioni in cui abbiamo girato invece di usare suoni generici.

### <a name="capture-the-audio"></a>Acquisisci audio

Nel [case study sull'acquisizione del contenuto visivo per HoloTour](case-study-capturing-and-creating-content-for-holotour.md), si parla della progettazione del rig della fotocamera. È costituito da 14 fotocamere GoPro in un'abitazione stampata in 3D progettata per adattarsi al treppiede. Per acquisire audio, è stato aggiunto un array a quattro microfoni sotto le fotocamere. Il suono è stato inserito in un'unità di registrazione compatta a quattro canali alla base del treppiede. Abbiamo scelto i microfoni che venivano eseguiti correttamente ma erano sufficientemente piccoli da evitare di interferire con le fotocamere.

![rig per fotocamere e microfoni personalizzati](images/camera-rig-microphones-300px.png)<br>
*Rig fotocamera e microfono personalizzati*

Questa configurazione acquisisce il suono in quattro direzioni. Sono state registrate informazioni sufficienti per ricreare un panorama uditivo 3D del suono spaziale, che è possibile sincronizzare successivamente con il video di 360 gradi.

Una sfida dell'audio dell'array della fotocamera è che si è alla mercé dei suoni fuori fotocamera, ad esempio sirene, aeroplani o venti elevati. Per assicurarsi di avere tutti gli elementi audio necessari, abbiamo usato anche i registratori stereo e mono mobile per acquisire il suono asincrono e dell'ambiente in punti specifici di interesse in ogni posizione. Queste registrazioni consentono al sound designer di pulire contenuto per aggiungere interesse e migliorare la direzionalità in fase di post-produzione.

Ogni giorno di acquisizione genera molti file. Quindi, è stato importante sviluppare un sistema per tenere traccia dei file corrispondenti a una posizione specifica o a una foto. L'unità di registrazione è stata configurata per il nome automatico dei file per data e il numero "Take". È stato eseguito il backup dei file in unità esterne alla fine di ogni giorno. È stato inoltre rilevato che è importante denominare verbalmente l'inizio delle registrazioni audio. Questa precauzione consente di identificare facilmente il contenuto nel caso in cui si verifichino problemi di nome file. È anche importante visualizzare visivamente l'acquisizione di rig della fotocamera, perché il video e l'audio sono stati registrati come supporti separati e devono essere sincronizzati durante la fase di post-produzione.

### <a name="edit-the-audio"></a>Modificare l'audio

Tornando a Studio dopo il viaggio di acquisizione, il primo passaggio per l'assemblaggio di un'esperienza direzionale e coinvolgente è la revisione di tutti i file audio acquisiti per una località. Si scelgono le procedure consigliate e si identificano le evidenziazioni che è possibile applicare durante l'integrazione. L'audio viene quindi modificato e pulito. Ad esempio, un Blast clacson che dura un secondo e si ripete alcune volte potrebbe essere sostituito con audio di ambiente più silenzioso dalla stessa sessione di acquisizione.

Dopo aver impostato la modifica video per un percorso, la finestra di progettazione audio può sincronizzare l'audio corrispondente. A questo punto, vengono valutate sia le acquisizioni del suono della fotocamera che dei dispositivi mobili per decidere quali elementi funzionerebbero per creare una scena audio immersiva. Si è rivelato utile inserire tutti gli elementi acustici in un editor audio e creare simulazioni lineari veloci per sperimentare idee combinate diverse. Questo passaggio ha fornito idee migliori in merito al momento in cui è giunto il momento di creare le scene HoloTour effettive.

### <a name="assemble-the-scene"></a>Assemblare la scena

Il primo passaggio per la creazione di una scena di ambiente 3D consiste nel creare un letto di suoni di ciclo di ambiente di background generale che supporteranno altre funzionalità e gli elementi audio interattivi in una scena. Viene adottato un approccio olistico all'implementazione come determinato dai criteri di progettazione per una particolare scena. Alcune scene possono essere indicizzate in base all'acquisizione della fotocamera sincronizzata. Più momenti "cinematografici" possono richiedere un approccio curato che si basa su suoni, elementi interattivi e musica disposti in modo discreta.

Quando è stato indicizzato nell'audio di acquisizione della fotocamera, abbiamo inserito gli emettitori audio spaziali abilitati per il suono che corrispondono all'orientamento direzionale delle fotocamere. La visualizzazione della fotocamera a nord riproduce l'audio dal microfono Nord e, allo stesso modo, per le altre direzioni cardinali. Questi emettitori sono bloccati a livello globale, il che significa che quando l'utente trasforma la loro testa in relazione a essi, il suono cambia. Questa tecnica consente di modellare efficacemente il suono che si trova in tale posizione. Ascoltare Piazza Navona o il Pantheon per esempi di scene che usano una combinazione di audio acquisita dalla fotocamera.

In un approccio diverso, talvolta si riproduce un ambiente stereo in loop insieme a emettitori di suoni spaziali posizionati intorno alla scena. Questi emettitori svolgono suoni monouso di volume casuale, pitch e frequenza del trigger. Questa tecnica crea un ambiente con un senso di direzionalità migliorato. In Aguas Aliens, ad esempio, è possibile scoprire in che modo ciascun quadrante del panorama dispone di emettitori specifici che evidenziano aree specifiche della geografia, ma che interagiscono per creare un ambiente immersivo generale.

## <a name="tips-and-tricks"></a>Suggerimenti

Esistono altri modi per evidenziare la direzionalità e migliorare l'immersione per sfruttare al meglio le funzionalità audio spaziali di HoloLens. Un elenco è disponibile qui. Attendere questi effetti la volta successiva che si prova a HoloTour.
* **Cerca destinazioni:** Questi suoni vengono attivati quando si esamina un oggetto specifico o un'area del frame olografico. Si osservi, ad esempio, il caffè sul lato strada a Roma, Piazza Navona, per attivare leggermente i suoni del ristorante occupato.
* **Visione locale:** Il percorso, sebbene HoloTour, contenga alcuni "ritmi", in cui la Guida introduttiva, aiutata dagli ologrammi, Esplora un argomento in modo approfondito. Ad esempio, poiché la facciata del Pantheon si risolve per rivelare l'Oculus, il riverbero audio che è stato inserito come emettitore 3D dall'interno del Pantheon invita l'utente a esplorare l'interno.
* **Direzionalità avanzata:** In molte scene, abbiamo inserito i suoni in diversi modi per aggiungere la direzionalità. Nella scena Pantheon, ad esempio, il suono della fontana è stato inserito come un emettitore separato abbastanza vicino all'utente che poteva ottenere un senso di "Sonic parallasse" mentre aggirano lo spazio di riproduzione. Nella scena Salinas de Mara del Perù, i suoni dei singoli flussi sono stati inseriti come emettitori distinti per creare un ambiente di ambiente più immersivo, che circonda l'utente con i suoni autentici di tale percorso.
* **Emettitore spline:** Questi emettitori si muovono nello spazio 3D rispetto alla posizione visiva dell'oggetto a cui sono collegati. Un esempio è il treno di Machu Picchu, in cui è stato usato un emettitore spline per fornire un senso di direzionalità e movimento distinti.
* **Musica e SFX:** Alcuni aspetti di HoloTour che rappresentano un approccio più stilizzato o cinematografico usano musica e effetti audio per aumentare l'impatto emotivo. Nella battaglia gladiatore alla fine della tournée di Roma, ad esempio, gli effetti speciali come whooshes e Stingers contribuiscono a rafforzare l'effetto delle etichette visualizzate in background.

## <a name="see-also"></a>Vedi anche
* [Audio spaziale](spatial-sound.md)
* [Progettazione dell'audio spaziale](spatial-sound-design.md)
* [Audio spaziale in Unity](spatial-sound-in-unity.md)
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
