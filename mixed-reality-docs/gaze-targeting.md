---
title: Destinazione dello sguardo
description: Tutte le interazioni si basano sulla capacità di un utente di selezionare come destinazione l'elemento con cui vuole interagire, indipendentemente dalla modalità di input.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realtà mista, sguardo, targeting, interazione, progettazione
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829845"
---
# <a name="gaze-and-dwell"></a>Sguardo e dimora
Ci sono molti modi diversi per confermare un _commit_ , ad esempio la combinazione di sguardi con _movimenti_ _vocali_ o mano.
Tuttavia, esistono diversi scenari utente, in cui le mani degli utenti possono essere occupate o non possono essere rilevate (ad esempio, gli addetti alla produzione con guanti pesanti a dazio eccessivo). L'input vocale potrebbe non essere disponibile anche a causa di preferenze utente, contesto sociale o ambienti ad alta voce.
Come soluzione di fallback, un'altra opzione per eseguire un _commit_ consiste semplicemente nell'osservare un elemento dell'interfaccia utente a cui si fa riferimento come _abitazione_.
È possibile eseguire un' _abitazione_ con lo sguardo a capo o a occhio. L'idea è semplice e può essere suddivisa nelle fasi seguenti: 
1. L'utente inizia a guardare un pulsante olografico

2. Dopo un breve intervallo di tempo di inattività, ad esempio 150 ms, viene avviata un'animazione con commenti visivi. Il ritardo di inizio viene usato per evitare di sovraccaricare l'utente riprendendo immediatamente il feedback.
    - Per gli _occhi_, è consigliabile quanto segue per la progettazione dei commenti e suggerimenti sugli oggetti visivi:
      - **Blend it**: Combinare in modo uniforme i commenti e i suggerimenti da poco visibili inizialmente a completamente opachi. In questo modo i commenti e i suggerimenti risultano meno dispersivi e overwhleming e ben allineati con la certezza che il sistema abbia effettivamente la voglia di interagire con questo pulsante.
      - **Esegui il pull**: Consente di creare un feedback visivo che diminuisce di dimensioni e si sposta verso il centro della destinazione, astraendondo l'attenzione visiva dell'utente. 

3. Dopo una durata predefinita dell'abitazione (ad esempio, 800 MS), l'abitazione viene completata e viene attivato un evento associato.
    - Fornire alcuni commenti o suggerimenti visivi finalizzati per portare a casa che l'elemento è stato selezionato.

![Stati di abitazione](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>Destinazione dello sguardo

Tutte le interazioni si basano sulla capacità di un utente di selezionare come destinazione l'elemento con cui vuole interagire, indipendentemente dalla modalità di input. In Windows Mixed Reality questo avviene in genere mediante lo sguardo dell'utente.

Per consentire a un utente di usufruire con successo di un'esperienza, la comprensione dell'intenzione dell'utente calcolata dal sistema e l'effettiva intenzione dell'utente devono essere allineate il più possibile. Più il sistema interpreta correttamente le azioni che l'utente intende compiere, più aumenta la soddisfazione e migliorano le prestazioni.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Destinazione dello sguardo</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Targeting degli occhi</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Altre indicazioni specifiche per HoloLens 2 [saranno presto](index.md)disponibili.

## <a name="target-sizing-and-feedback"></a>Dimensioni della destinazione e feedback

In più occasioni è stato dimostrato come il vettore di sguardo fisso sia utilizzabile per selezionare con precisione la destinazione, ma spesso tale vettore funziona in modo ottimale per selezionare la destinazione con minore precisione, ovvero quando sia necessario acquisire destinazioni di dimensioni più grandi. Dimensioni minime della destinazione da 1 a 1,5 gradi dovrebbero garantire una corretta esecuzione delle azioni dell'utente nella maggior parte degli scenari, benché destinazioni di 3 gradi spesso consentano una velocità superiore. Le dimensioni che l'utente punta come destinazione corrispondono in effetti a un'area 2D persino per gli elementi 3D: qualunque proiezione vi sia di fronte deve essere l'area selezionabile come destinazione. È estremamente utile fornire un segnale che indichi quando un elemento è "attivo", ossia quando l'utente lo sta puntando come destinazione. A tale scopo, possono essere usati effetti visibili "al passaggio del puntatore", clic o evidenziazioni audio oppure il chiaro allineamento di un cursore a un elemento.

![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni ottimali della destinazione a una distanza di 2 metri*

![Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso](images/gazetargeting-highlighting-640px.jpg)<br>
*Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso*

## <a name="target-placement"></a>Posizionamento della destinazione

Gli utenti spesso non riescono a trovare gli elementi dell'interfaccia utente posizionati molto in alto o molto in basso nel loro campo visivo, in quanto tendono a concentrare l'attenzione sulle aree intorno al punto focale principale, che in genere si trova approssimativamente al livello degli occhi. Può pertanto rivelarsi utile posizionare la maggior parte delle destinazioni in una fascia ragionevole attorno al livello degli occhi. Data la tendenza degli utenti a concentrarsi su un'area visiva relativamente limitata in un determinato momento (il cono attenzionale della visione è all'incirca di 10 gradi), il fatto di raggruppare gli elementi dell'interfaccia utente in base a come sono correlati concettualmente può dare luogo a comportamenti di concatenamento dell'attenzione da un elemento all'altro man mano che l'utente sposta lo sguardo all'interno di un'area. Quando progetti l'interfaccia utente, tieni presente la grande differenza potenziale di campo visivo tra i visori HoloLens e i visori VR immersive.

![Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Miglioramento dei comportamenti di selezione della destinazione

Se è possibile determinare (o approssimare con una certa precisione) l'intenzione dell'utente di selezionare un elemento come destinazione, può essere molto utile accettare i tentativi di interazione "quasi riusciti" come se avessero avuto esito positivo. Sono disponibili alcuni metodi validi che possono essere incorporati nelle esperienze di realtà mista:

### <a name="gaze-stabilization-gravity-wells"></a>Stabilizzazione di sguardi ("pozzi di gravità")

Deve essere attivata per tutto o per la maggior parte del tempo. Questa tecnica consente di eliminare i tremolii naturali della testa o del collo che possono avere gli utenti, nonché il movimento che si produce guardando o parlando.

### <a name="closest-link-algorithms"></a>Algoritmi di collegamento più vicino

Funzionano al meglio nelle aree con contenuto interattivo sparso. Se vi è un'alta probabilità di determinare l'elemento con cui un utente stava tentando di interagire, puoi integrare le sue capacità di selezione della destinazione semplicemente presupponendo un certo livello di intenzione.

### <a name="backdatingpostdating-actions"></a>Retrodatazione o postdatazione delle azioni

Questo meccanismo è utile per le attività che richiedono velocità. Quando un utente si sposta in una serie di manovre di targeting/attivazione alla velocità, può essere utile presupporre un certo scopo e consentire ai *passaggi mancanti* di agire sulle destinazioni di cui l'utente si è concentrato leggermente prima o leggermente dopo il tocco (50 ms prima/dopo was efficace nei test iniziali).

### <a name="smoothing"></a>Definizione di movimenti uniformi

Questo meccanismo è utile per i movimenti che consentono di disegnare un percorso, in quanto riduce il leggero tremolio o la lieve oscillazione dovuta alle naturali caratteristiche del movimento della testa. Quando decidi di rendere uniformi i movimenti che disegnano un percorso, uniformali in base alla loro entità o distanza anziché in base al tempo.

### <a name="magnetism"></a>Magnetismo

Questo meccanismo può essere considerato come una versione più generale degli algoritmi di "collegamento più vicino"; è possibile disegnare un cursore verso una destinazione o semplicemente aumentare le hitbox (in modo visibile o meno) man mano che gli utenti si avvicinano a probabili destinazioni, avvalendosi di una certa conoscenza del layout interattivo per avvicinarsi con maggior accuratezza all'intenzione dell'utente. Questa soluzione può risultare particolarmente efficace per le destinazioni di piccole dimensioni.

### <a name="focus-stickiness"></a>Spostamento dello stato attivo in base all'elemento di interesse corrente

Quando determini gli elementi interattivi vicini su cui spostare lo stato attivo, prediligi l'elemento su cui è attualmente concentrata l'attenzione. Ciò consentirà di ridurre i passaggi imprevedibili da un'area di interesse all'altra quando ci si trova in un punto intermedio tra due elementi con disturbi naturali.

## <a name="see-also"></a>Vedere anche
* [Movimenti](gestures.md)
* [Esecuzione di comandi vocali](voice-design.md)
* [Cursori](cursors.md)
