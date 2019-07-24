---
title: 'Case Study: creazione di prospettive impossibili per HoloTour'
description: L'esperienza di HoloTour per Microsoft HoloLens è stata indimenticata. Oltre alle interruzioni turistiche tradizionali, abbiamo pianificato alcune "prospettive impossibili".
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, realtà mista di Windows
ms.openlocfilehash: be00df73543aa295e1e0dbe1462a888d6bb24954
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523567"
---
# <a name="case-study---creating-impossible-perspectives-for-holotour"></a>Case Study: creazione di prospettive impossibili per HoloTour

L'esperienza di HoloTour per Microsoft HoloLens è stata indimenticata. Oltre alle interruzioni turistiche tradizionali, abbiamo pianificato alcune "prospettive impossibili", ovvero momenti che sarebbe impossibile sperimentare in qualsiasi tour, ma che, grazie alla tecnologia di HoloLens, avremmo potuto portare direttamente alla tua sala da visita. Per creare il contenuto di queste esperienze è necessario adottare alcune tecniche diverse da quelle del processo di acquisizione standard.

## <a name="the-content-challenge"></a>La richiesta di contenuto

Ci sono alcune scene nell'esperienza HoloTour, ad esempio il giro di mongolfiera a caldo di Roma e la lotta tra i gladiatori presso il Colosseo nell'antica Roma, che offrono visualizzazioni univoche che non verranno visualizzate altrove. Questi istanti hanno lo scopo di entusiasmare e stupire l'utente, rendendo il viaggio in HoloTour più di una semplice esperienza didattica. Sono i momenti in cui ci si vuole ricordare e si è entusiasti di informare altri utenti. Dal momento che non è stato possibile portare il rig della fotocamera verso l'alto e non è ancora stato eseguito il mastering, ognuna di queste "prospettive impossibili" ha chiamato un approccio speciale per la creazione di contenuti.

## <a name="behind-the-scenes"></a>Dietro le quinte

La creazione di questi momenti e prospettive univoci è stata necessaria oltre alla semplice creazione di filmati e modifiche. È stata impiegata una notevole quantità di tempo, persone con molte competenze diverse e un po' di magia di Hollywood.

### <a name="viewing-rome-from-a-hot-air-balloon"></a>Visualizzazione di Roma da un pallone ad aria calda

Dai primi giorni della pianificazione, sapevamo che volevamo eseguire le viste aeree in HoloTour. Vedendo Roma dal cielo ti offre una prospettiva che la maggior parte degli utenti non è mai in grado di vedere e in che modo i punti di riferimento più diffusi si trovano a livello spaziale. Il tentativo di acquisire questo comportamento con la fotocamera e il rig microfonici esistenti sarebbe stato estremamente complesso, ma fortunatamente non era necessario.

Prima di tutto, è importante spiegare che tutti i percorsi visitati in HoloTour sono in movimento. Il nostro obiettivo è quello di fare in modo che tu sia davvero in realtà e, dal momento che sei circondato da un movimento ovunque ti trovi in realtà, le nostre destinazioni virtuali necessarie per fornire anche lo spostamento ambientale. Ad esempio, quando si visita il Pantheon durante il viaggio, si vedranno le persone che vagano in tutto il piazzale e si uniscono i passaggi. Il movimento in background ti aiuta a farti sentire come se fossi in realtà nella posizione, anziché in un ambiente statico a fasi.

Per creare le visualizzazioni aeree per la corsa in mongolfiera, abbiamo collaborato con altri team di Microsoft per ottenere l'accesso alle immagini panoramiche aeree di Roma. La qualità di queste immagini è stata eccellente e la visualizzazione era sorprendente, ma quando le abbiamo usate in scena senza modifiche, si sono rilevati inevitabili rispetto alle altre parti del tour e la mancanza di movimento era distrazione. 


![Il basket del pallone ad aria calda, Mobile su Roma.](images/hotairballoon1-300px.png)<br>
*Basket ad aria calda, Mobile su Roma*

Per garantire che le località aeree soddisfino la stessa barra di qualità delle altre destinazioni, abbiamo deciso di trasformare le fotografie statiche in scene in continua evoluzione. Il primo passaggio consiste nel modificare l'immagine e il movimento composito al suo interno. L'autore di effetti visivi è stato contratto per aiutare Microsoft a eseguire questa operazione. La modifica è stata eseguita per mostrare lentamente i cloud, gli uccelli che volano da e un aereo o un elicottero occasionale attraversando l'orizzonte. A fondo, sono state effettuate numerose automobili per guidare le strade. Se si è passati al tour di Roma in HoloTour, è improbabile che si sia in grado di riconoscere in modo esplicito uno di questi spostamenti. Si tratta di un'ottima soluzione. Il lieve movimento non è concepito per attirare gli occhi, ma senza questi piccoli tocchi, le persone hanno notato immediatamente che era un'immagine statica nella scena.

La seconda cosa da fare è fornire un punto di vista da cui visualizzare la scena. Non ci si farà sentire come se fosse semplicemente a mezz'aria, quindi è stato creato un modello 3D di un fumetto e ci si trova all'interno. In questo modo è possibile aggirare il fumetto ed esaminare il bordo per ottenere un punto di vista migliore. Abbiamo scoperto che questo è un modo naturale e divertente per sperimentare le immagini aeree.

L'esperienza di mongolfiera a caldo presenta problematiche uniche per il nostro team audio, perché la logistica ha impedito ai microfoni di passare da migliaia di metri a Roma. Fortunatamente, abbiamo avuto una grande quantità di acquisizione audio di ambiente da tutte le città che potevamo usare durante la fase di post-produzione. Gli emettitori audio sono stati inseriti nelle rispettive posizioni da dove sono stati acquisiti da zero. L'audio è stato filtrato in modo da sembrare distante, come se fosse stato sentito dal punto di vista di un utente che si trovava nel pallone ad aria calda, offrendo un paesaggista autentico e direzionale per la scena.

### <a name="time-traveling-to-ancient-rome"></a>Tempo di viaggio verso la Roma antica

I rimanenti dei monumenti e delle costruzioni a Roma sono impressionanti anche 2000 anni dopo la loro costruzione, ma sapevamo che avevamo un'opportunità unica di dimostrare cosa sarebbe stato come tornare indietro nel tempo e osservare queste strutture come sono apparse nell'antica Roma.

Naturalmente, non è presente alcun video o immagine statica del Colosseo come appare al momento della compilazione, quindi è necessario crearne uno personalizzato. Era necessario eseguire molte ricerche per apprendere il maggior numero possibile della struttura. conoscere i materiali da cui è stato creato, esaminare i diagrammi dell'architettura e leggere le descrizioni storiche per ottenere informazioni sufficienti per poter creare una ricreazione virtuale. 

![Il giorno moderno rovine del Colosseo con una sovrapposizione che mostra il piano dell'Arena, come sarebbe stato osservato nell'antica Roma.](images/rome-colosseum-overlay-500px.png)<br>
*Il giorno moderno rovine del Colosseo con una sovrapposizione che mostra il piano dell'Arena come sarebbe stato osservato nell'antica Roma*

La prima cosa che volevamo fare era migliorare i tour tradizionali con sovrapposizioni didattiche. In HoloTour quando si visitano i ruderi del Colosseo così come si trova oggi, il piano dell'Arena viene trasformato per illustrare il modo in cui sarebbe stato osservato durante l'uso, incluse le aree di gestione temporanea elaborate. In una presentazione normale è possibile che queste informazioni siano state descritte ed è possibile provare a immaginarla, ma in HoloTour è possibile visualizzarla effettivamente.

Per una sovrapposizione come questa, abbiamo fatto in modo che i nostri artisti corrispondano al punto di vista del nostro metraggio di acquisizione e creiamo l'immagine sovrapposta manualmente. Il punto di vista deve corrispondere in modo che, quando si sostituisce il video con l'immagine, entrambi si allineano correttamente.

### <a name="staging-the-gladiator-fight"></a>Gestione temporanea del gladiatore

Sebbene le sovrapposizioni siano un modo accattivante per insegnare agli utenti la cronologia, ciò che era più entusiasta è stato quello di trasportarsi indietro nel tempo. La sovrimpressione è stata un'immagine ancora da un particolare punto di vista, ma il tempo di viaggio richiederebbe la modellazione dell'intero Colosseum e, come illustrato in precedenza, era necessario avere un movimento nella scena per far sentire la sua vita. Il raggiungimento di una notevole quantità di lavoro.

Questa impresa era troppo grande per il nostro team, quindi il nostro team artistico lavorava con Whiskytree, una società di effetti esterni che in genere funziona sugli effetti visivi per i film hollywoodiani. Whiskytree ci ha aiutato a ricreare il Colosseo nel suo apogeo, che ci ha permesso di insegnare alla struttura mentre si trovava sul pavimento dell'Arena e di creare una vista di una lotta gladiatore dalla scatola dell'imperatore. La folla allegra e i banner ondeggianti aggiungono il lieve movimento necessario per far sembrare che si tratta di luoghi reali e non solo immagini.

![Il Colosseo ricreato, come visto dal piano Arena. Quando vengono visualizzati in HoloTour, i banner sventolano al vento, offrendo una sensazione di movimento.](images/recreated-colosseum-holotour-500px.png)<br>
*Il Colosseo ricreato, come visto dal piano Arena. Quando vengono visualizzati in HoloTour, i banner sventolano al vento, offrendo una sensazione di movimento.*

La presentazione di Roma culmina con la lotta gladiatore. Whiskytree ci ha fornito le simulazioni Arena e 3D per la folla con rendering come video, ma è stato necessario aggiungere i gladiatori sul piano Arena. Questa parte del processo ha avuto un aspetto analogo a quello di una produzione di video Hollywood rispetto a un progetto di Game Studio Incubation. I membri del team hanno eseguito il mapping di una sequenza di lotte approssimativa e la loro raffinata con un coreografo. Abbiamo assunto gli attori per organizzare la nostra battaglia fittizia e abbiamo acquistato armature, in modo che possano sembrare la parte. Infine, abbiamo girato l'intera scena su una schermata verde.

![I nostri gladiatori, ricevendo istruzioni tra.](images/green-screen-gladiators-holotour-500px.jpg)<br>
*Il nostro gladiatiors, ottenendo istruzioni tra*

Questa scena si trova nella casella dell'imperatore, il che significava che tutto il metraggio era necessario da questa prospettiva. Se abbiamo girato da dove i gladiatori stavano combattendo nell'Arena, non saremmo riusciti a comporre correttamente la sequenza di lotte in un secondo momento, quindi mettiamo l'operatore della fotocamera in un ascensore a forbice molto alto, guardando la sequenza di lotte per il film.

![Ottenere la prospettiva giusta: il film da un lift a forbice.](images/scissor-lift-holotour-500px.jpg)<br>
*Ottenere la prospettiva giusta: film da un lift a forbice*

Nel corso della fase di post-produzione, i gladiatori sono stati compositi sul pavimento dell'Arena e la prospettiva era corretta, ma è rimasto un problema: le ombre dei gladiatori nella schermata verde sono state rimosse come parte del processo di composizione. Senza ombre, sembrava che i gladiatori fossero fluttuati in aria. Fortunatamente, Whiskytree è la soluzione ideale per risolvere questo tipo di problema e hanno usato una parte della procedura guidata tecnica per aggiungere ombre alla nostra scena. Il risultato è quello che viene visualizzato oggi nella presentazione.

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> è uno sviluppatore senior che ha appreso altre informazioni sui rig della fotocamera e la riproduzione video di quanto pensi possa essere usato in HoloTour.</td>

<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> è una finestra di progettazione audio che ha avuto la certezza di poter provare il paesaggio appropriato di ogni destinazione visitata, anche quando si torna indietro nel tempo.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny storta</b> è un artista video che ha avuto la certezza che il suo percorso attraverso Roma fosse il più perfetto possibile.</td>

<td style="border:0" width="60px"></td>
<td style="border:0" width="408"></td>
</tr>
</table>


## <a name="see-also"></a>Vedere anche
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
