---
title: Guida alla progettazione dell'utilità di avvio delle app 3D
description: Un avvio di app 3D è un oggetto "fisico" nella casa della realtà mista dell'utente che può selezionare per avviare un'app.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, avvio di app 3D, auricolare immersivo, cubo attivo
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437227"
---
# <a name="3d-app-launcher-design-guidance"></a>Guida alla progettazione dell'utilità di avvio delle app 3D

Quando si usa un headset di Windows misto Reality (VR), si immette la Home realtà mista di Windows, viene visualizzata come una casa in una rupe circondata da montagne e acqua (anche se è possibile [scegliere altri ambienti e persino crearne di personalizzati](add-custom-home-environments.md)). All'interno dello spazio di questa casa, un utente può organizzare e organizzare gli oggetti e le app 3D a cui si è interessati. Un **avvio di app 3D** è un oggetto "fisico" nella casa della realtà mista dell'utente che può selezionare per avviare un'app.

Esempio ![: utilità di avvio delle app 3D Floaty Bird](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Esempio di utilità di avvio di app 3D Floaty Bird (app fittizia)*

## <a name="3d-app-launcher-creation-process"></a>processo di creazione dell'utilità di avvio delle app 3D

Per la creazione di un avvio di app 3D sono necessari tre passaggi:
1. Progettazione e concezione (questo articolo)
2. [Modellazione ed esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Per integrarlo nell'applicazione:
    * [App UWP](implementing-3d-app-launchers.md)
    * [App Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Concetti di progettazione

### <a name="fantastic-yet-familiar"></a>Fantastico ma familiare

L'ambiente di realtà mista di Windows in cui si trova l'utilità di avvio delle app è familiare, parte fantastica/sci-fi. I migliori lanci seguono le regole di questo mondo. Si pensi a come sia possibile prendere un oggetto familiare, rappresentativo, dall'app, ma è necessario piegare alcune delle regole della realtà reale. Si otterrà un risultato magico.

### <a name="intuitive"></a>Intuitivo

Quando si esamina l'utilità di avvio delle app, il suo scopo è quello di avviare l'app, che dovrebbe essere ovvia e non dovrebbe causare confusione. Assicurarsi, ad esempio, che l'utilità di avvio sia un rappresentante abbastanza ovvio dell'app che non verrà confusa per un pezzo di arredamento in Cliff House. L'utilità di avvio delle app dovrebbe invitare gli utenti a toccarlo/selezionarlo.

Esempio di ![:](images/20171016-152145-mixedreality1-1200px-1000px.jpg) di avvio delle app 3D<br>
*Esempio di avvio dell'app 3D (app fittizia)*

### <a name="home-scale"></a>Scalabilità domestica

i lanci di app 3D risiedono nella casa di Cliff e le dimensioni predefinite dovrebbero avere senso con gli altri oggetti "fisici" nello spazio. Se l'utilità di avvio viene posizionata accanto a un impianto di casa o a una parte di mobili, si dovrebbe sentire a casa, ridimensionare. Un valido punto di partenza consiste nel vedere il modo in cui esamina 30 centimetri cubici, ma tenere presente che gli utenti possono aumentare o ridurre le prestazioni se lo desiderano.

### <a name="own-able"></a>Proprietario

L'utilità di avvio delle app dovrebbe essere simile a un oggetto che una persona sarebbe entusiasta di avere nello spazio. Si tratteranno praticamente di questi elementi, quindi l'utilità di avvio dovrebbe avere un aspetto simile a quello auspicabile dall'utente per cercarla e mantenerla vicina.

Esempio ![: avvio dell'app 3D di Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Esempio di avvio di app 3D di Astro Warp (app fittizia)*

### <a name="recognizable"></a>Riconoscibile

L'utilità di avvio delle app 3D dovrebbe immediatamente esprimere "il marchio dell'app" agli utenti che lo visualizzano. Se è presente un carattere a stella o un oggetto particolarmente identificabile nell'app, è consigliabile usarlo come parte importante della progettazione. In un mondo di realtà mista, un oggetto trarrà maggiore interesse dagli utenti rispetto solo a un logo. Gli oggetti riconoscibili comunicano il marchio in modo rapido e chiaro.

### <a name="volumetric"></a>Volumetrici

L'app merita di più di inserire il logo su un piano semplice e chiamarlo un giorno. L'utilità di avvio dovrebbe sembrare un oggetto fisico eccitante, 3D, nello spazio dell'utente. Un approccio efficace consiste nell'immaginare che l'app avrebbe avuto un pallone nella sfilata del giorno del ringraziamento del Macy. Se ci si chiede, cosa si può veramente stupire con la strada? Cosa può sembrare interessante da tutti gli angoli di visualizzazione?


:::row:::
    :::column:::
        solo logo di ![](images/20171016-140436-mixedreality-640px.jpg) *solo logo*
    :::column-end:::
    :::column:::
        ![più riconoscibili con un carattere](images/20171016-140557-mixedreality-640px.jpg) *più riconoscibile con un carattere*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![approccio Flat, non sorprendentemente, si sente un approccio Flat](images/20171016-155101-mixedreality-640px.jpg) flat *, non sorprendentemente, sembra piatto*
    :::column-end:::
    :::column:::
        ![approccio volumetrico presenta una migliore presentazione dell'app](images/20171016-161407-mixedreality-640px.jpg) *approccio volumetrico illustra meglio l'app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>Suggerimenti per modelli 3D efficaci

### <a name="best-practices"></a>Procedure consigliate
* Quando si pianificano le dimensioni per l'utilità di avvio delle app, si scatta approssimativamente un cubo di 30cm. Quindi, un rapporto di dimensioni 1:1:1.
* I modelli devono essere sotto 10.000 poligoni. [Altre informazioni sui conteggi dei triangoli e sui livelli di dettaglio (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Testare su un auricolare immersivo quando possibile.
* Consente di compilare i dettagli nella geometria del modello, laddove possibile, non basarsi sulle trame per i dettagli.
* Compila la geometria chiusa "acqua stretta". Non ci sono buchi che non sono modellati in.
* Usare materiali naturali nell'oggetto. Immagina di crearlo nel mondo reale.
* Verificare che il modello sia ben letto a distanza e dimensioni diverse.
* Quando il modello è pronto per l'uso, leggere le [linee guida](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)per l'esportazione degli asset.

![modello con dettagli sottili nella trama](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modello con dettagli sottili nella trama*

### <a name="what-to-avoid"></a>Cosa evitare
* Non usare dettagli a contrasto elevato o modelli e trame di dimensioni ridotte e occupate.
* Non usare la geometria sottile: non funziona bene a una distanza e l'alias non è corretto.
* Non lasciare che le parti del modello si estendano troppo oltre il rapporto dimensioni 1:1:1. Si creeranno problemi di scalabilità.

![evitare i modelli a contrasto elevato e a basso traffico](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evitare i modelli a contrasto elevato, piccoli e occupati*

## <a name="how-to-handle-type"></a>Come gestire il tipo

### <a name="best-practices"></a>Procedure consigliate
* È consigliabile che il tipo sia costituito da circa 1/3 dell'utilità di avvio dell'app (o più). Il tipo è l'elemento principale che offre agli utenti un'idea del fatto che l'utilità di avvio è, di fatto, un'utilità di avvio, quindi è interessante se è piuttosto sostanziale.
* Evitare di rendere il tipo Super Wide: provare a mantenerlo entro i limiti delle dimensioni di base dei lanci di app (più o meno).
* Il tipo flat può funzionare, ma tenere presente che può essere difficile da visualizzare da determinati angoli e da determinati ambienti. È possibile considerare di inserirlo in un oggetto solido o in uno sfondo per facilitare questa operazione.
* L'aggiunta di una dimensione al tipo è gradevole in 3D. L'ombreggiatura dei lati del tipo un colore più scuro può essere utile per migliorare la leggibilità.


:::row:::
    :::column:::
        ![tipo Flat senza uno sfondo può essere difficile da visualizzare da determinati angoli e in determinati ambienti](images/flattype-640px.png) *tipo Flat senza uno sfondo può essere difficile da visualizzare da determinati angoli e in determinati ambienti*
    :::column-end:::
    :::column:::
        ![tipo con uno sfondo incorporato può funzionare correttamente](images/flattypeandbkg-640px.png) *tipo con uno sfondo incorporato può funzionare correttamente*
    :::column-end:::
    :::column:::
        ![tipo estruso può funzionare correttamente se si ombreggiano i lati](images/20171016-160221-mixedreality-640px.jpg) *tipo estruso può funzionare correttamente se si ombreggiano i lati*
    :::column-end:::
:::row-end:::


**Colori del tipo che funzionano**
* Vuoto
* Nero
* Colore luminoso semi-saturato

![i colori del tipo che funzionano.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Colori del tipo che funzionano*

### <a name="what-to-avoid"></a>Cosa evitare

**Tipi di colori che provocano problemi**
* Frequenze medie
* Grigio
* Colori eccessivamente saturi o colori desaturi

![i colori di tipo che provocano problemi.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Tipi di colori che provocano problemi*

## <a name="lighting"></a>Luce

L'illuminazione per l'utilità di avvio dell'app deriva dall'ambiente Cliff House. Assicurarsi di testare l'utilità di avvio in diversi punti della casa, in modo da ottenere un aspetto positivo sia in chiaro che in ombreggiatura. La buona notizia è che, se sono state seguite le altre linee guida di progettazione di questo documento, l'utilità di avvio dovrebbe avere una forma abbastanza buona per la maggior parte dell'illuminazione della casa Cliff.

Un posto ideale per testare il modo in cui l'utilità di avvio Guarda le varie luci nell'ambiente è lo studio, la media room, in qualsiasi punto all'esterno e sul patio (l'area concreta con il prato). Un altro test efficace consiste nell'inserirlo a metà luce e metà ombreggiatura per vedere come appare.

![assicurarsi che l'utilità di avvio sia corretta sia in chiaro che in ombreggiatura.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Assicurarsi che l'utilità di avvio sia corretta in chiaro e in ombra*

## <a name="texturing"></a>Texturing

### <a name="authoring-your-textures"></a>Creazione di trame

Il formato finale dell'utilità di avvio delle app 3D sarà un file con estensione GLB, che viene creato usando la pipeline di PBR (rendering fisico). Questo può essere un processo complesso, ora è il momento giusto per impiegare un artista tecnico, se non è già stato fatto. Se si è bravi fai da te, il tempo necessario per la [ricerca e l'apprendimento della terminologia di PBR](https://wiki.polycount.com/wiki/PBR) e cosa accade dietro le quinte prima di iniziare ti aiuterà a evitare errori comuni. 

Esempio ![: Nota aggiornata](images/pbr-freshnote1-640px-500px.png) app<br>
*Esempio di avvio dell'app 3D (app fittizia)*

**Strumento di creazione consigliato**

Per creare il file finale, è consigliabile usare il [pittore di sostanze](https://www.allegorithmic.com/products/substance-painter) Allegorithmic. Se non si ha familiarità con la creazione di shader PBR in sostanza Painter, ecco un' [esercitazione](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(In alternativa [, il](https://3dcoat.com/home/) [Quixel Suite 2](https://quixel.se/suite2/)o [uistitì toolbag](https://www.marmoset.co/toolbag/) funziona anche se si ha familiarità con uno di questi).

### <a name="best-practices"></a>Procedure consigliate

* Se l'oggetto dell'utilità di avvio delle app è stato creato per PBR, dovrebbe essere piuttosto semplice convertirlo per l'ambiente Cliff House.
* Lo shader sta aspettando un flusso di lavoro di metallo/rugosità: lo shader Unreal PBR è un facsimile di chiusura.
* Quando si esportano le trame, tenere presenti le [dimensioni consigliate](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) .
* Assicurarsi di compilare gli oggetti per l'illuminazione in tempo reale, ovvero:
    * Evitare le ombre cotte o disegnare le ombre
    * Evitare l'illuminazione al forno nelle trame
    * Usare uno dei pacchetti di creazione materiali di PBR per ottenere le mappe corrette generate per lo shader

## <a name="see-also"></a>Vedi anche

* [Creare modelli 3D da usare nella Home realtà mista](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementare utilità di avvio per app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Implementare utilità di avvio per app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
