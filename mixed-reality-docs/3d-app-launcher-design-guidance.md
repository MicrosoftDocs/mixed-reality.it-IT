---
title: Linee guida di progettazione di app 3D dell'utilità di avvio
description: Un'utilità di avvio app 3D è un oggetto "physical" in casa di realtà mista dell'utente che è possibile scegliere di avviare un'app.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, progettazione, utilità di avvio app 3D, visore VR immersivi, il cubo in tempo reale
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598552"
---
# <a name="3d-app-launcher-design-guidance"></a>Linee guida di progettazione di app 3D dell'utilità di avvio

Quando si inserisce in un auricolare (VR) coinvolgente di realtà mista di Windows, si immette la realtà mista di Windows home, visualizzato come una casa in un precipizio racchiuso tra le montagne e acqua (anche se è possibile [scegliere altri ambienti e persino crearne di propri](add-custom-home-environments.md)). Nello spazio di questo home, un utente è libero di gestire e organizzare gli oggetti 3D e le app che si preoccupi di qualsiasi modalità che preferiscono. Oggetto **utilità di avvio app 3D** è casa realtà che è possibile scegliere di avviare un'app mista di un oggetto "physical" dell'utente.

![Esempio: Utilità di avvio di Mobile Bird app 3D](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Esempio di utilità di avvio di Mobile Bird app 3D (fittizia app)*

## <a name="3d-app-launcher-creation-process"></a>Processo di creazione dell'utilità di avvio app 3D

Sono previsti 3 passaggi per la creazione di un'utilità di avvio app 3D:
1. Progettazione e concepting (questo articolo)
2. [Modellazione e l'esportazione](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. L'integrazione nell'applicazione:
    * [App UWP](implementing-3d-app-launchers.md)
    * [App Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Concetti relativi alla progettazione

### <a name="fantastic-yet-familiar"></a>Fantastico ancora familiare

L'ambiente di realtà mista di Windows in che si trova l'icona di avvio delle app è parte familiare, parte eroi sempre/sci-fi. L'utilità di avvio migliore seguono le regole di questo mondo. Pensare a come è possibile accettare un oggetto familiare e rappresentativo dall'app, ma piegare alcune delle regole di realtà effettivo. Magic verrà generato.

### <a name="intuitive"></a>intuitivo

Quando si esamina l'utilità di avvio di app, lo scopo - per avviare l'app - dovrebbe essere evidente e non dovrebbe causare confusione. Assicurarsi, ad esempio, che l'utilità di avvio è un ovvio sufficientemente rappresentativo dell'app che non verranno confusi per un dato decor in House di Cliff. L'utilità di avvio di app deve invitare persone a tocco/select si.

![Esempio: Nuova utilità di avvio nota app 3D](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Nuova nota 3D app dell'utilità di avvio di esempio (fittizio app)*

### <a name="home-scale"></a>Scalabilità home

Nelle schermate di avvio app 3D in tempo reale in House di Cliff e le dimensioni predefinite devono essere usati con gli altri oggetti "physical" nello spazio. Se si inseriscono le utilità di avvio-beside, ad esempio, un impianto di casa o alcuni mobili, dovrebbe risultare a casa, size-wise. Un buon punto di partenza consiste nel verificarne l'aspetto in centimetri cubiche 30, tenere presente che gli utenti possono scalare verso l'alto o verso il basso se desiderano.

### <a name="own-able"></a>Il proprietario da dispositivo

L'icona di avvio dovrebbe risultare simile a un oggetto persona sarebbe entusiasti di avere nel proprio spazio. Si sarà essere praticamente circostante autonomamente con queste cose, in modo che l'utilità di avvio dovrebbe risultare simile al pensiero di utente è stata abbastanza utile cercare e mantenere vicini.

![Esempio: Utilità di avvio app 3D atomi Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Esempio di utilità di avvio app 3D atomi Warp (fittizia app)*

### <a name="recognizable"></a>Riconoscibile

L'utilità di avvio app 3D debba esprimere istantaneamente "marchio dell'app" a chi visualizzarlo. Se si dispone di un carattere a stella o a un oggetto soprattutto personali nell'app, è consigliabile usarlo come gran parte della progettazione. In un mondo di realtà mista, un oggetto verrà suscitare l'interesse più utenti rispetto a semplicemente un logo da solo. Oggetti riconoscibili comunicano marchio semplice e rapido.

### <a name="volumetric"></a>Volumetrici

L'applicazione merita i più della semplice inserendo il logo personalizzato su un piano flat e la chiamata a tutto il giorno. L'utilità di avvio dovrebbe risultare, ad esempio un oggetto interessante, 3D, fisico nello spazio dell'utente. Un buon approccio è immaginare che l'app stava per avere una bolla nel giorno del ringraziamento YCbCr di Macy. Chiedersi che cosa sarebbe stupire persone come proviene strada? Aspetto eccezionale da tutti gli angoli di visualizzazione?


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>Suggerimenti per la buona modelli 3D

### <a name="best-practices"></a>Procedure consigliate
* Quando si pianificano le quote dell'utilità di avvio di app, riprese per circa un cubo 30cm. Pertanto, un valore 1: proporzioni 1:1.
* I modelli devono essere meno di 10.000 poligoni. [Altre informazioni sui livelli dei dettagli (LOD) e i conteggi di triangolo](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Test su un visore VR immersivi quando possibile.
* Dettagli di compilazione nella geometria del modello dove possibile, non si basano su trame per informazioni dettagliate.
* Compilare la geometria "acqua stretta" chiusa. Nessun buchi che non sono modellate in.
* Utilizzare materiali naturale nell'oggetto. Si supponga alla creazione nel mondo reale.
* Assicurarsi che il modello legge correttamente alle dimensioni e le distanze diverse.
* Quando il modello è pronto per iniziare, leggere il [esportazione di linee guida per gli asset](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modello con dettagli nella trama](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modello con dettagli nella trama*

### <a name="what-to-avoid"></a>Cosa evitare
* Non usare i dettagli a contrasto elevato o modelli di piccole dimensioni, occupati e trame.
* Non usare geometry thin: non funzionare bene a una distanza, alias in modo errato.
* Non lasciare che le parti del modello di estendere troppo oltre il 1: proporzioni 1:1. Problemi di scalabilità verrà creato.

![Evitare i modelli di occupato a contrasto elevato di piccole dimensioni](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evitare i modelli a contrasto elevato, piccoli, occupati*

## <a name="how-to-handle-type"></a>Come tipo di handle

### <a name="best-practices"></a>Procedure consigliate
* È consigliabile il tipo è costituito da circa 1/3 di utilità di avvio di app (o più). Il tipo è la cosa principale che offre agli utenti un'idea che è l'utilità di avvio, infatti, un'utilità di avvio in modo che se non si verificano se è piuttosto notevole.
* Evitare l'esecuzione di tipo wide super: provare per contenerlo entro i confini dell'utilità di avvio di app le quote di core (più o meno).
* Tipo flat può funzionare, ma tenere presente che può essere difficile da visualizzare da alcuni punti di vista e in alcuni ambienti. È possibile applicarlo a un oggetto solid o dello sfondo dietro di essa per facilitare questa operazione.
* Dimensione aggiunta al tipo ritiene interessante in 3D. Ombreggiatura i lati del tipo di un colore diverso e più scuro utili per migliorare la leggibilità.


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


**Colori di tipo che funzionano**
* Bianco
* Nero
* Brillante semi-saturazione colore

![Digitare i colori che funzionano.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Colori di tipo che funzionano*

### <a name="what-to-avoid"></a>Cosa evitare

**Colori di tipo che causano problemi**
* Tonalità medie
* Grigio
* Overcommit saturazione dei colori o colori desaturati

![Digitare i colori che causano problemi.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Colori di tipo che causano problemi*

## <a name="lighting"></a>Luce

L'illuminazione per l'utilità di avvio app provenienti dall'ambiente Cliff House. Assicurarsi di testare l'utilità di avvio in diverse posizioni in tutta la casa, in modo esito positivo in chiaro e ombreggiature. La buona notizia è, se sono stati eseguiti altri linee guida di progettazione in questo documento, l'utilità di avvio deve essere abbastanza corrette per la maggior parte delle illuminazione in House di Cliff.

Ottimo strumento per testare come l'utilità di avvio appare in varie luci nell'ambiente è di Studio, chat Room Media, in qualsiasi punto esterno e terrazzo indietro (l'area concreto con le Prato). Un altro, è possibile inserirlo nella metà e ombre metà e vedere l'effetto.

![Assicurarsi che l'utilità di avvio sono corrette in chiaro e ombreggiature.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Assicurarsi che l'utilità di avvio sono corrette in chiaro e ombreggiature*

## <a name="texturing"></a>La trama

### <a name="authoring-your-textures"></a>Le trame di creazione

Il formato finale dell'utilità di avvio app 3D sarà un file .glb, che viene eseguito tramite la pipeline PBR (Rendering fisicamente base). Può trattarsi di un processo difficile, ora è un buon momento per impiegare un artista tecnico se già stato fatto. Se si ha un coraggioso fai da te-UT, avere inviato [ricerche e informazioni sulla terminologia PBR](http://wiki.polycount.com/wiki/PBR) e ciò che accade dietro le quinte prima di iniziare per evitare gli errori più comuni. 

![Esempio: App nuova nota](images/pbr-freshnote1-640px-500px.png)<br>
*Nuova nota 3D app dell'utilità di avvio di esempio (fittizio app)*

**Strumento di creazione e modifica consigliato**

È consigliabile usare [sostanza pittore](https://www.allegorithmic.com/products/substance-painter) da Allegorithmic per creare il file finale. Se non si ha familiarità con la creazione di shader PBR in sostanza, del pittore una [esercitazione](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(In alternativa [3D Coat](https://3dcoat.com/home/), [Suite Quixel 2](https://quixel.se/suite2/), o [Marmoset Toolbag](https://www.marmoset.co/toolbag/) funzionerebbe anche se non ha maggiore familiarità con uno di questi.)

### <a name="best-practices"></a>Procedure consigliate

* Se l'oggetto dell'utilità di avvio di app è stata creata per PBR, dovrebbe essere piuttosto semplice per convertirlo per l'ambiente di Cliff House.
* Il shader si aspetta un flusso di lavoro Metal/asperità: The PBR Unreal shader è un facsimile chiude.
* Quando l'esportazione le trame di mantenere la [consiglia le dimensioni della trama](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) presente.
* Assicurarsi di compilare gli oggetti per l'illuminazione in tempo reale: ciò significa che:
    * Evitare virtuali create con bake shadows – o ombreggiature disegnate
    * Evitare di illuminazione virtuali create con bake nelle trame
    * Usare uno dei materiali PBR creazione di pacchetti per le mappe a destra generate per il shader

## <a name="see-also"></a>Vedere anche

* [Creare modelli 3D per l'utilizzo in realtà mista home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementare nelle schermate di avvio app 3D (app UWP)](implementing-3d-app-launchers.md)
* [Implementare nelle schermate di avvio app 3D (app Win32)](implementing-3d-app-launchers-win32.md)
