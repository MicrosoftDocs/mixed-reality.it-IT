---
title: Sguardo targeting
description: Tutte le interazioni vengono compilate al momento la possibilità di un utente di destinazione l'elemento a cui che si desidera interagire, indipendentemente dalla modalità di input.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mista realtà, sguardo, sguardo targeting, interazione, progettazione
ms.openlocfilehash: 1ac4f06208a7574fced0a7e27e93469ec93bf6e0
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873919"
---
# <a name="gaze-and-dwell"></a>Sguardo e permanenza
Esistono molti modi diversi per verificare un _commit_ quale la combinazione di sguardo con _vocali_ oppure _mano i movimenti_.
Esistono diversi scenari utente, tuttavia, in cui le mani degli utenti potrebbero essere occupate o non possono essere rilevate (ad esempio, factory gli utenti che svolgono guanti dimensioni eccessive pesante). Input vocale anche potrebbero non essere disponibili a causa delle preferenze utente, contesto basati su social network o ambienti alti.
Come soluzione di fallback un'altra opzione per eseguire una _commit_ consiste nel mantenere fissare lo un elemento dell'interfaccia utente che costituiscono _permanenza_.
Oggetto _permanenza_ può essere eseguita con sguardo head o rossi. L'idea è semplice e può essere suddivisa nelle fasi seguenti: 
1. Si inizia a un pulsante holographic gazing

2. Dopo un ritardo di onset breve (ad esempio, 150 ms) viene avviata l'animazione alcune indicazioni visive. Il ritardo del set viene utilizzato per evitare di sovraccaricare l'utente visualizzando immediatamente commenti e suggerimenti continuamente.
    - Per la _sguardo occhio_, si consiglia quanto segue per la progettazione dell'oggetto visivo permanenza commenti e suggerimenti:
      - **Blend**: Blend senza problemi i commenti e suggerimenti da poco visibile nella prima di tutto a completamente opaco. In questo modo i commenti e suggerimenti meno rappresentano una distrazione e overwhleming e perfettamente in linea con la certezza che il sistema è che l'utente desideri interagire con questo pulsante.
      - **Trascinarlo in**: Creare un feedback visivo che riduce le dimensioni e si sposta verso il centro della destinazione, chiama l'attenzione dell'utente visual. 

3. Dopo avere una durata di permanenza predefiniti (ad esempio, 800 ms), la permanenza completa e si verifica un evento associato.
    - Fornire alcuni finalizzazione acustica o feedback visivo davvero portare home che l'elemento è stato selezionato ora.

![Permanenza stati](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>Sguardo targeting

Tutte le interazioni vengono compilate al momento la possibilità di un utente di destinazione l'elemento a cui che si desidera interagire, indipendentemente dalla modalità di input. Realtà mista di Windows, questa operazione viene in genere eseguita usando sguardo dell'utente.

Per consentire agli utenti un'esperienza di corretto funzionamento, comprensione calcolata del sistema della finalità dell'utente e l'intenzione dell'utente effettivo, deve essere allineati quanto più vicina. Al grado che il sistema interpreta le azioni dell'utente desiderato correttamente, le prestazioni e aumenta la soddisfazione migliora.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (dal 1 ° generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Auricolari coinvolgenti</a></th>
</tr><tr>
<td> Sguardo targeting</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️ </td>
</tr><tr>
<td> Destinazione rossi</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md).

## <a name="target-sizing-and-feedback"></a>Commenti e suggerimenti e le dimensioni di destinazione

Il vettore sguardo è stato dimostrato ripetutamente per poter essere usato per specificare come destinazione bene, ma spesso è adatto per gross targeting (acquisizione leggermente maggiori destinazioni). Le dimensioni di destinazione minimo di 1 a 1.5 gradi devono consentire le azioni dell'utente ha esito positivo nella maggior parte degli scenari, anche se le destinazioni di gradi 3 spesso consentono maggiore velocità. Si noti che le dimensioni che le destinazioni degli utenti in modo efficace è un'area 2D anche per gli elementi 3D, qualunque proiezione è rivolta essi devono essere l'area definibili come destinazione. Fornendo alcune salienti della segnalazione che un elemento è "active" (che l'utente è destinato a si) è molto utile: può trattarsi di trattamenti come effetti visibili "mouse", evidenzia audio o fa clic su, o cancellare l'allineamento di un cursore con un elemento.

![Dimensioni di destinazione ottimale a distanza di 2 metri](images/gazetargeting-size-1000px.jpg)<br>
*Dimensioni di destinazione ottimale a distanza di 2 metri*

![Un esempio di evidenziazione di un oggetto di destinazione sguardo](images/gazetargeting-highlighting-640px.jpg)<br>
*Un esempio di evidenziazione di un oggetto di destinazione sguardo*

## <a name="target-placement"></a>Selezione host di destinazione

Gli utenti spesso riuscirà a trovare gli elementi dell'interfaccia utente che vengono posizionati in modo molto elevato o molto bassa nel loro campo visivo, concentrandosi la maggior parte dei loro attenzione sulle aree intorno a loro lo stato attivo principale (in genere circa livello rossi). Consente l'inserimento di quasi tutte le destinazioni in alcune fuori banda ragionevole intorno a livello di attenzione. Data la tendenza per gli utenti per concentrarsi su un'area visual relativamente piccola in qualsiasi momento (cono attentional della visione è all'incirca 10 gradi), raggruppare gli elementi dell'interfaccia utente per il livello che sono correlati a livello concettuale possono sfruttare i comportamenti di concatenamento dell'attenzione da elemento a un elemento con un account utente viene spostata loro sguardo all'interno di un'area. Durante la progettazione dell'interfaccia utente, tenere presenti le variazioni di grandi dimensioni potenziali nel campo visivo tra HoloLens e auricolari coinvolgente e concreto.

![Un esempio di elementi dell'interfaccia utente raggruppati per più semplice sguardo targeting in Esplora Galaxy](images/gazetargeting-grouping-1000px.jpg)<br>
*Un esempio di elementi dell'interfaccia utente raggruppati per più semplice sguardo targeting in Esplora Galaxy*

## <a name="improving-targeting-behaviors"></a>Miglioramento della destinazione dei comportamenti

Se l'intenzione dell'utente a un elemento di destinazione può essere determinato o approssimati a stretto contatto, può essere molto utile accettare "near miss" tentativi di interazione come se esse sono destinate in modo corretto. Esistono un numero limitato di metodi corretta che può essere incorporato nelle esperienze di realtà mista:

### <a name="gaze-stabilization-gravity-wells"></a>Stabilizzazione sguardo ("aree di gravità")

Questa deve essere attiva per la maggior parte/all del tempo. Questa tecnica consente di rimuovere l'instabilità head/collo naturale che gli utenti possono avere. Anche lo spostamento a causa dei comportamenti di ricerca/parlando.

### <a name="closest-link-algorithms"></a>Algoritmi di collegamento più vicino

Queste funzionano meglio in aree con sparse contenuti interattivi. Se è presente un'elevata probabilità che è possibile determinare quali un utente ha tentato di interagire con, è possibile integrare la capacità targeting semplicemente assumendo un certo livello di intent.

### <a name="backdatingpostdating-actions"></a>Azioni backdating/postdating

Questo meccanismo è utile per le attività che richiedono velocità. Quando un utente viene spostato attraverso una serie di targeting/attivazione evasive alla velocità, può essere utile per presuppone alcune finalità e consentire *saltate passaggi* su cui intervenire destinazioni che l'utente ha lo stato attivo leggermente prima o leggermente dopo il (tap 50 ms prima/dopo è rimasto in vigore nel test preliminare).

### <a name="smoothing"></a>Anti-aliasing

Questo meccanismo è utile per gli spostamenti di ricerca del percorso, riducendo l'instabilità/oscillazione leggero a causa di caratteristiche naturale movimento della testina. Quando l'anti-aliasing tramite i movimenti di ricerca del percorso, arrotondare di dimensioni/distanza di spostamenti di tipo invece che nel corso del tempo

### <a name="magnetism"></a>Campi magnetici

Questo meccanismo può essere considerato come una versione più generale degli algoritmi "Più vicino link" - Creazione di un cursore verso una destinazione o aumentare semplicemente hitboxes (se visibilmente o No) quando gli utenti si avvicinano probabilmente destinazioni, tramite una certa conoscenza del layout interattiva per intenzione dell'utente approccio migliore. Ciò risulta particolarmente utile per le destinazioni di piccole dimensioni.

### <a name="focus-stickiness"></a>Persistenza dello stato attivo

Quando si determina quale vicino agli elementi interattivi per attivare, fornire un valore di bias all'elemento che è attualmente attivo. Ciò consentirà di ridurre lo stato attivo imprevedibile cambio comportamenti quando mobile in un punto intermedio tra due elementi con rumore naturale.

## <a name="see-also"></a>Vedere anche
* [Movimenti](gestures.md)
* [Progettazione delle interazioni vocali](voice-design.md)
* [Cursori](cursors.md)
