---
title: Input vocale
description: Input vocale è un input di core per HoloLens e realtà mista di Windows auricolari coinvolgente e concreto. Vocale è utilizzabile per i comandi, dettatura, Cortana e altro ancora.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, voce, cortana, il riconoscimento vocale, di input
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829956"
---
# <a name="voice-input"></a>Input vocale

Vocale è uno dei tre formati principali di input su HoloLens. Consente al comando direttamente ologramma senza dover usare [movimenti](gestures.md). È semplicemente [estasiati](gaze.md) in ologramma e si parla del comando. Input vocale può essere un modo semplice per comunicare lo scopo previsto. Vocale è particolarmente efficaci per attraversare complesse interfacce perché consente agli utenti di Taglia tramite i menu annidati con un solo comando.

Input vocale è una tecnologia di [stesso motore](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) che supporta la sintesi vocale in tutte le altre app di Windows universale.

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (dal 1 ° generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Input vocale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con microfono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Il comando "select"

Anche senza specificamente aggiunta del supporto vocali all'App, gli utenti possono attivare vntana semplicemente specificando "select". Si comporta come un [puntato](gestures.md#air-tap) su HoloLens, premendo il pulsante di selezione per il [HoloLens clicker](hardware-accessories.md#hololens-clicker), o premendo il trigger per un [controller movimento di realtà mista di Windows](motion-controllers.md). Si verrà riprodotto un suono e una descrizione comando con l'istruzione "select" vengono visualizzati come conferma. "Select" è abilitata per un algoritmo di rilevamento di basso consumo (parola chiave) in modo che è sempre disponibile per poter affermare in qualsiasi momento con un impatto minimo batteria vita, anche con le mani al lato dell'utente.

> [!NOTE]
> Altre indicazioni specifiche su 2 HoloLens [presto](index.md#news-and-notes).

![Ad esempio "select" per usare i comandi vocali per la selezione](images/kma-voice-select-00170-800px.png)<br>
*Ad esempio "select" per usare i comandi vocali per la selezione*

## <a name="hey-cortana"></a>Ehi Cortana

È inoltre possibile pronunciare "Ehi Cortana" per visualizzare Cortana in qualsiasi momento. Non devi attendere di sembrano continuare chiede la domanda o relativa fornendo un'istruzione, ad esempio, provare ottimizzazioni "Ehi Cortana che cos'è il meteo?" come una singola frase. Per altre informazioni su Cortana e cosa può fare, è sufficiente richiedere copie! Pronunciare "Ehi Cortana in che modo è dico?" e Lei esegue pull un elenco di comandi funziona correttamente ed è consigliati. Se si ha già nell'app di Cortana è anche possibile scegliere di **?** icona sulla barra laterale per eseguire il pull questo stesso menu di scelta rapida.

**Comandi specifici HoloLens**
* "Cosa posso dire?"
* "Go home" o "andare a Start" - anziché [bloom](gestures.md#bloom) per ottenere [Menu Start](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Avvio <app>"
* "Sposta <app> qui"
* "Scattare una foto"
* "Avvia registrazione"
* "Arrestare la registrazione"
* "Increase luminosità"
* "Riduzione della luminosità"
* "Increase il volume"
* "Diminuire il volume"
* "Disattivare" o "Ripristinare"
* "Arrestare il dispositivo"
* "Riavvia il dispositivo"
* "Vai allo stato di sospensione"
* "Che ora è?"
* "Quanti batteria rimasti?"
* "Chiamare <contact>" (richiede Skype per HoloLens)

## <a name="see-it-say-it"></a>"Visualizzarlo, dice"

HoloLens dispone di un modello "visualizzarlo, dice" per l'input vocale, in cui le etichette nei pulsanti indicano agli utenti quali comandi vocali dice anche. Ad esempio, quando si esamina un'app 2D, un utente può pronunciare il comando "Regolare" che viene visualizzato nella barra dell'App per regolare la posizione dell'app nel mondo.

![Quando si esamina un'ologrammi o un'app 2D, un utente può pronunciare il comando "Regolare" che viene visualizzato nella barra dell'App per regolare la posizione dell'app nel mondo](images/microphone-600px.png)

Quando le app seguono questa regola, possono comprenderne facilmente agli utenti cosa significa controllare il sistema. Per ribadire, mentre gazing a un pulsante, si noterà una descrizione comando "permanenza della voce" che viene visualizzato dopo un secondo se il pulsante è abilitato per la voce e viene visualizzato il comando da leggere a voce per "premerlo".

![Visualizzarlo, ad esempio, i comandi vengono visualizzate sotto i pulsanti](images/voice-seeitsayit-600px.png)<br>
*"A vederla, dice" i comandi vengono visualizzate sotto i pulsanti*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandi vocali per la manipolazione di ologramma veloce

Esistono anche numerose vocale comandi è possibile dire durante gazing in ologramma per eseguire rapidamente attività di manipolazione. Questi comandi vocali si cimentano App 2D nonché oggetti 3D che è stato inserito nel mondo.

**Comandi di manipolazione ologrammi**
* Viso me
* Più grande | Migliorare
* Più piccolo

## <a name="dictation"></a>Dettatura

Invece di digitare con [aria scelte](gestures.md#air-tap), dettatura può essere più efficiente di immettere testo in un'app. Ciò consente di accelerare notevolmente input con meno sforzi per l'utente.

![Dettatura inizia selezionando il pulsante del microfono](images/micbuttonfordictation.png)<br>
*Dettatura inizia selezionando il pulsante del microfono sulla tastiera*

Ogni volta che la tastiera holographic è attiva, è possibile passare alla modalità di dettatura anziché digitare. Selezionare il microfono sul lato di casella di input di testo per iniziare.

## <a name="communication"></a>Comunicazione

Per le applicazioni che vogliono sfruttare i vantaggi dell'input audio personalizzato fornite da HoloLens opzioni di elaborazione, è importante comprendere i vari [categorie flusso audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) può usare l'app. Windows 10 supporta diverse categorie di flusso diverso e HoloLens rende l'utilizzo di tre di questi per consentire l'elaborazione personalizzata ottimizzare la qualità audio microfono su misura per la sintesi vocale, la comunicazione e altri che può essere usato per audio ambiente ambiente scenari di acquisizione (vale a dire "cineprese").
* La categoria di flusso AudioCategory_Communications personalizzata per la chiamata di qualità e un testo descrittivo scenari e fornisce al client con un flusso audio mono a 24 kHz 16 bit della voce dell'utente
* La categoria di flusso AudioCategory_Speech personalizzata per il motore di sintesi vocale HoloLens (Windows) e fornisce un flusso di mono a 24 kHz 16 bit della voce dell'utente. Questa categoria può essere utilizzata dai motori di sintesi vocale 3rd party se necessario.
* La categoria di flusso AudioCategory_Other personalizzata per la registrazione audio ambiente ambiente e fornisce al client con un flusso audio stereo a 48 bit 24 kHz.

Tutti i questa elaborazione audio è con accelerazione hardware che indica che le funzionalità di svuotare molto meno energia rispetto a se stessa elaborazione è stata eseguita sulla CPU HoloLens. Evitare di eseguire altri input audio di elaborazione sulla CPU per ottimizzare la durata della batteria del sistema e sfruttare i vantaggi di incorporato, l'offload l'elaborazione dell'input audio.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano eventuali problemi tramite "selezionare" e "Ehi Cortana", provare a spostare in uno spazio risulteranno meno intensi, l'attivazione verso la sorgente di disturbo o parlando più alto. A questo punto, tutti di riconoscimento vocale in HoloLens è ottimizzato e ottimizzato in modo specifico per madrelingua dell'inglese degli Stati Uniti.

Per la versione di Windows misti realtà Developer Edition 2017, la logica di gestione endpoint audio funziona correttamente (per sempre) dopo la registrazione e al desktop del computer dopo la connessione HMD iniziale. Prima di tale prima sign out/in eventi dopo il passaggio attraverso WMR OOBE, l'utente potrebbe subire vari problemi di funzionalità audio compreso senza audio e nessun audio di commutazione a seconda del modo in cui è stato configurato il sistema prima di connettere il HMD per la prima volta.

## <a name="see-also"></a>Vedere anche
* [Input vocale in DirectX](voice-input-in-directx.md)
* [Input vocale in Unity](voice-input-in-unity.md)
* [Input MR 212: Voce](holograms-212.md)
