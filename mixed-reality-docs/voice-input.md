---
title: Input vocale
description: L'input vocale è un input di base per HoloLens e per le cuffie immersive in realtà mista di Windows. La voce può essere usata per i comandi, la dettatura, il Cortana e altro ancora.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, input
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829956"
---
# <a name="voice-input"></a>Input vocale

Voice è una delle tre forme chiave di input per HoloLens. Consente di eseguire direttamente il comando di un ologramma senza dover usare i [movimenti](gestures.md). È sufficiente [guardare](gaze.md) un ologramma e pronunciare il comando. L'input vocale può essere un metodo naturale per comunicare lo scopo. La voce è particolarmente utile per attraversare interfacce complesse perché consente agli utenti di tagliare i menu nidificati con un unico comando.

L'input vocale è alimentato dallo [stesso motore](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) che supporta la sintesi vocale in tutte le altre app di Windows universale.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Input vocale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con microfono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Comando "Select"

Anche senza aggiungere esplicitamente il supporto vocale all'app, gli utenti possono attivare gli ologrammi semplicemente dicendo "Select". Questo comportamento è identico a quello di un [rubinetto d'aria](gestures.md#air-tap) su HoloLens, facendo clic sul pulsante Seleziona nel [HoloLens clic](hardware-accessories.md#hololens-clicker)oppure premendo il trigger in un [controller di movimento della realtà mista di Windows](motion-controllers.md). Verrà visualizzato un suono e verrà visualizzata una descrizione comando con "Select" come conferma. "Select" è abilitato da un algoritmo di rilevamento di parole chiave a basso consumo, in modo che sia sempre disponibile per l'utente in qualsiasi momento con un minimo di durata della batteria, anche con le tue mani.

> [!NOTE]
> Altre indicazioni specifiche per HoloLens 2 [saranno presto](index.md#news-and-notes)disponibili.

![Pronunciare "Select" per utilizzare il comando Voice per la selezione](images/kma-voice-select-00170-800px.png)<br>
*Pronunciare "Select" per utilizzare il comando Voice per la selezione*

## <a name="hey-cortana"></a>Ehi Cortana

È anche possibile pronunciare "Hey Cortana" per visualizzare Cortana in qualsiasi momento. Non è necessario attendere che venga visualizzata per continuare a porre una domanda o fornire un'istruzione, ad esempio, provare a pronunciare "Hey Cortana qual è il meteo?" come singola frase. Per ulteriori informazioni su Cortana e sulle operazioni che è possibile eseguire, è sufficiente chiederle! Pronunciare "Hey Cortana cosa posso dire?" verrà quindi eseguito il pull di un elenco di comandi funzionanti e consigliati. Se si è già nell'app Cortana, è anche possibile fare clic sul pulsante **?** icona sulla barra laterale per estrarre lo stesso menu.

**Comandi specifici di HoloLens**
* "Cosa posso dire?"
* "Vai a casa" o "Vai a avvio"-anziché [Bloom](gestures.md#bloom) per visualizzare il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Avvia <app>"
* "Sposta <app> qui"
* "Scattare un'immagine"
* "Avvia registrazione"
* "Arresta registrazione"
* "Aumentare la luminosità"
* "Riduzione della luminosità"
* "Aumento del volume"
* "Diminuisci volume"
* "Mute" o "unmute"
* "Arresta il dispositivo"
* "Riavvia il dispositivo"
* "Vai a sospensione"
* "Qual è il tempo?"
* "Quanta batteria è rimasta?"
* "Call <contact>" (richiede Skype per HoloLens)

## <a name="see-it-say-it"></a>"Vedere la voce"

HoloLens dispone di un modello "See it, Say it" per l'input vocale, in cui le etichette sui pulsanti indicano agli utenti i comandi vocali che possono dire. Ad esempio, quando si esamina un'app 2D, un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app nel mondo.

![Quando si esamina un'app 2D o un ologramma, un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app nel mondo](images/microphone-600px.png)

Quando le app seguono questa regola, gli utenti possono comprendere facilmente cosa dire per controllare il sistema. Per rinforzare questo problema, guardando un pulsante, viene visualizzata una descrizione comando "Voice Rest" che viene visualizzata dopo un secondo se il pulsante è abilitato per la voce e visualizza il comando per "premere".

![Vedere i comandi visualizzati sotto i pulsanti](images/voice-seeitsayit-600px.png)<br>
*I comandi "See it, Say it" appaiono sotto i pulsanti*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandi vocali per la manipolazione rapida degli ologrammi

Sono inoltre disponibili numerosi comandi vocali che è possibile osservare guardando un ologramma per eseguire rapidamente le attività di manipolazione. Questi comandi vocali funzionano in app 2D e in oggetti 3D che sono stati inseriti nel mondo.

**Comandi di manipolazione ologramma**
* Mi faccia
* Più grande | Migliorare
* Più piccoli

## <a name="dictation"></a>Dettatura

Invece di digitare con le [scelte aeree](gestures.md#air-tap), la dettatura vocale può essere più efficiente per inserire il testo in un'app. Questo può accelerare significativamente l'input con minore impegno per l'utente.

![La dettatura vocale inizia selezionando il pulsante del microfono](images/micbuttonfordictation.png)<br>
*La dettatura vocale inizia selezionando il pulsante del microfono sulla tastiera*

Ogni volta che la tastiera olografica è attiva, è possibile passare alla modalità di dettatura anziché alla digitazione. Per iniziare, selezionare il microfono sul lato della casella input di testo.

## <a name="communication"></a>Comunicazione

Per le applicazioni che vogliono sfruttare le opzioni di elaborazione dell'input audio personalizzato fornite da HoloLens, è importante comprendere le diverse categorie di [flussi audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) che l'app può utilizzare. Windows 10 supporta diverse categorie di flusso e HoloLens ne usa tre per consentire l'elaborazione personalizzata per ottimizzare la qualità audio del microfono personalizzata per la comunicazione vocale, la comunicazione e altro che può essere usata per l'audio dell'ambiente di ambiente scenari di acquisizione, ad esempio "videocamera".
* La categoria del flusso AudioCategory_Communications è personalizzata per gli scenari di qualità della chiamata e di narrazione e fornisce al client un flusso audio 16kHz 24bit mono della voce dell'utente
* La categoria del flusso AudioCategory_Speech è personalizzata per il motore vocale HoloLens (Windows) e fornisce un flusso 16kHz 24bit mono della voce dell'utente. Questa categoria può essere usata dai motori di sintesi vocale di terze parti, se necessario.
* La categoria del flusso AudioCategory_Other è personalizzata per la registrazione audio dell'ambiente di ambiente e fornisce al client un flusso audio stereo a 24 bit a 48 bit.

Questa elaborazione audio è accelerata dall'hardware, il che significa che le funzionalità svuotano molto meno energia rispetto a quando la stessa elaborazione è stata eseguita sulla CPU HoloLens. Evitare di eseguire altre elaborazioni di input audio sulla CPU per ottimizzare la durata della batteria del sistema e sfruttare i vantaggi dell'elaborazione dell'input audio con offload incorporato.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi con "Select" e "Hey Cortana", provare a passare a uno spazio più silenzioso, a disattivarsi dall'origine del rumore o a una voce più forte. A questo punto, tutto il riconoscimento vocale in HoloLens viene ottimizzato e ottimizzato in modo specifico per gli altoparlanti nativi di Stati Uniti inglese.

Per la versione 2017 di Windows Mixed Reality Developer Edition, la logica di gestione degli endpoint audio funzionerà correttamente (per sempre) dopo la disconnessione e l'accesso al desktop del PC dopo la connessione iniziale di HMD. Prima della prima disconnessione o dell'evento, dopo aver attraversato la configurazione guidata di WMR, l'utente poteva riscontrare diversi problemi di funzionalità audio, tra cui l'assenza di audio e nessun cambio audio, a seconda della configurazione del sistema prima di connettere il HMD per la prima volta.

## <a name="see-also"></a>Vedere anche
* [Input vocale in DirectX](voice-input-in-directx.md)
* [Input vocale in Unity](voice-input-in-unity.md)
* [Input MR 212: Voce](holograms-212.md)
