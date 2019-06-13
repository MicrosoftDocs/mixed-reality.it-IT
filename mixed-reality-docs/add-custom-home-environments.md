---
title: Aggiungere gli ambienti home personalizzati
description: Oltre a degli ambienti principali di realtà mista di Windows che viene fornito, è possibile provare con la creazione e usare il proprio.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, Home, ambienti personalizzati, posizioni, casa cliff, skyloft, utente, creazione
ms.openlocfilehash: d0cdb878f1994cb5f898f06b98d74dee3dd4fdf1
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024536"
---
# <a name="add-custom-home-environments"></a>Aggiungere gli ambienti home personalizzati

>[!NOTE]
>Questa è una funzionalità sperimentale. Fare una prova e divertente, ma non c'è da stupirsi se tutto ciò che ancora non funziona come previsto. Vengono valutati dell'affidabilità di questa funzionalità e l'interesse dimostrato in uso, quindi, fornisci sulla tua esperienza (e tutti i bug è stato individuato) nei [forum per sviluppatori](https://forums.hololens.com/categories/custom-home-environments).

Inizia con la [Windows 10 April 2018 update](#release-notes-april-2018.md), è stata abilitata una funzionalità sperimentale che consente di aggiungere gli ambienti personalizzati per il selettore di percorsi (nel menu Start) per l'uso come il [realtà mista di Windows home](#navigating-the-windows-mixed-reality-home.md). Realtà mista di Windows dispone di due ambienti predefiniti, Cliff House e Skyloft, che è possibile scegliere come la home page. Creazione di ambienti personalizzati consente di espandere tale elenco con proprie creazioni. Stiamo predisponendo questo in uno stato iniziali per valutare interesse da autori e degli sviluppatori, vedere quali tipi di scenari di creare e comprendere il funzionamento con diversi strumenti di creazione.

Quando si usa un ambiente personalizzato, si noterà che teleporting, l'interazione con le App e inserendoli vntana funziona come avviene in Cliff House e Skyloft. È possibile esplorare il web in uno scenario di fantacalcio oppure inserire una città più innovative con vntana: le possibilità sono infinite.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Auricolari coinvolgenti</strong></a></td>
    </tr>
     <tr>
        <td>Ambienti home personalizzati</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Il tentativo di un ambiente di esempio

Abbiamo creato un ambiente di esempio che dimostra alcune delle possibilità creative degli ambienti principali personalizzati. Seguire questi passaggi per provarlo:
1. [Scaricare l'ambiente di Fantacalcio isola esempio](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (collegamento al file eseguibile autoestraente).

    ![Ambiente di esempio fantacalcio isola](images/FantasyLand.jpg)<br>
    *Ambiente di esempio fantacalcio isola*<br>

2. Eseguire la **Fantasy_Island.exe** file appena scaricato.

    > [!NOTE]
    > Quando si tenta di eseguire un file .exe scaricati dal web (come questo), è possibile riscontrare un menu a comparsa "Windows protetto PC". Per eseguire Fantasy_Island.exe da questo menu a comparsa, selezionare **altre informazioni** e quindi **Esegui comunque**. Questa impostazione di sicurezza è progettata per proteggere gli utenti dai download di file potrebbe non voler considera attendibile, questa operazione, scegliere questa opzione solo quando si considera attendibile l'origine del file.

3. Aprire **Esplora File** e passare alla cartella di ambienti da incollare il codice seguente nella barra degli indirizzi: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.
4. Copiare l'ambiente di esempio che è stato scaricato in questa cartella.
5. Riavviare **portale di realtà mista**. Consente di aggiornare l'elenco degli ambienti nella casella di selezione delle posizioni.
6. Inserire le cuffie. Una volta nell'ambiente domestico, aprire il **dal menu Start** utilizzando il Windows pulsante del controller.
7. Selezionare il **posizioni** sull'icona sopra l'elenco delle App bloccate per scegliere un ambiente domestico.
8. Si noterà l'ambiente di Fantacalcio isola scaricato nel proprio elenco di posizioni. Selezionare **isola di Fantacalcio** immettere il nuovo ambiente home personalizzato.

## <a name="creating-your-own-custom-environment"></a>Creazione del proprio ambiente personalizzato

Oltre a usare ambienti nostro esempio, è possibile esportare i propri ambienti personalizzati usando i Preferiti 3D software di montaggio. 

### <a name="modeling-guidelines"></a>Linee guida per la modellazione delle minacce

L'ambiente di modellazione, tenere presente le raccomandazioni seguenti. Questo contribuisce a garantire l'utente genera l'orientamento corretto in un mondo believably dimensioni:

1. Gli utenti distribuirà fulcro 0, 0,0 in questo percorso di generazione desiderata intorno all'origine.
2. Unità di lavoro deve essere impostata su metri, in modo che gli asset possono essere creati su scala mondiale.
3. L'asse verticale deve essere impostato su "Y".
4. L'asset debba affrontare "forward" rispetto all'asse Z positivo.
5. Tutte le reti mesh non è necessario essere combinati, ma è consigliabile se si sviluppano App per dispositivi vincolati alle risorse.

### <a name="exporting-your-environment"></a>Esportazione ambiente

Realtà mista di Windows si basa su glTF binario (.glb) come il formato di recapito asset per gli ambienti. glTF è un diritto d'autore gratuita standard aperto per il recapito di asset 3D gestito dal gruppo di Khronos. Con glTF evoluzione come standard per il contenuto 3D interoperativo di settore, tra le app di Windows e le esperienze verrà così il supporto Microsoft per il formato.

Il primo passaggio nell'esportazione di risorse da usare come ambienti personalizzati home sta generando un modello glTF 2.0. Il gruppo di lavoro glTF gestisce un [elenco di utilità di esportazione supportati e i convertitori](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) per creare un modello glTF 2.0. Per iniziare, usare uno dei programmi elencati in questa pagina per creare ed esportare un modello glTF 2.0 o convertire un modello esistente utilizzando uno dei convertitori supportati.

Inoltre, consultare [questo articolo utile](https://www.khronos.org/blog/art-pipeline-for-gltf) che fornisce una panoramica del flusso di lavoro art per esportazione modelli glTF da Blender e 3DS Max direttamente. 

### <a name="environment-limits"></a>Limiti di ambiente

Tutti gli ambienti devono essere < 256 MB. Ambienti di dimensioni superiori a 256 MB non riuscirà a caricare ed eseguire il fallback a un mondo vuoto con solo la skybox predefinito che circonda l'utente. Tenere questo limite di dimensione file presente durante la creazione dei modelli. Inoltre, se si prevede di ottimizzare l'ambiente usando il WindowsMRAssetConverter come descritto di seguito, tenere conto del fatto che le dimensioni della trama comporta un aumento perché query optimizer crea le trame che hanno file di grandi dimensioni, ma caricare più velocemente. 

### <a name="optimizing-your-environment"></a>Ottimizzazione dell'ambiente

Realtà mista di Windows supporta una serie di ottimizzazioni facoltative che riduce significativamente i tempi di caricamento degli ambienti. Ciò risulta particolarmente importante per gli ambienti con molte trame, come vengono riprodotti in alcuni casi è previsto un timeout durante il caricamento. In generale, è consigliabile eseguire questa procedura per tutti gli asset, tuttavia, ambienti più piccoli con alcuni o a bassa risoluzione trame non saranno sempre lo richiedono. 

Per semplificare questo processo, abbiamo creato il [mista realtà Asset convertitore Windows (disponibile in GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) per eseguire le ottimizzazioni. Questo strumento utilizza un set di utilità disponibili in Microsoft glTF toolkit per ottimizzare qualsiasi glTF 2.0 standard o .glb eseguendo una compressione di trama aggiuntivi, la compressione e scalabilità verso il basso la risoluzione. 

Attualmente, il convertitore supporta un numero di flag per modificare il comportamento esatto delle ottimizzazioni. È consigliabile eseguire con i flag seguenti per ottenere risultati ottimali:

Flag|Valori consigliati|Descrizione
---|---|---
-max-texture-size|1024 o 2048| Modificare questa opzione per migliorare la qualità delle trame, valore predefinito è 512 x 512. Si noti che un valore maggiore influirà in modo significativo le dimensioni del file dell'ambiente bene tenere il limite di 256 mb presente
-min-version|1803|Gli ambienti personalizzati sono supportati solo nelle versioni di windows > = 1803. Questo flag rimuoverà le trame per le versioni precedenti e ridurre le dimensioni del file dell'asset finale

Ad esempio:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>L'ambiente di test

Dopo aver ottenuto l'ambiente .glb finale si è pronti per testarlo nelle cuffie. Iniziare dal passaggio 2 nel ["Cercando un ambiente di esempio"](#trying-a-sample-environment) sezione per usare un ambiente personalizzato come la realtà mista home. 

## <a name="feedback"></a>Feedback

Mentre si sta valutando questa funzionalità sperimentale, siamo interessati a come si usa ambienti personalizzati, gli eventuali problemi possono, e come si desidera che la funzionalità. Microsoft invita tutti i commenti e suggerimenti per la creazione e uso degli ambienti principali personalizzati nel [forum per sviluppatori](https://forums.hololens.com/categories/custom-home-environments).

## <a name="troubleshooting-and-tips"></a>Suggerimenti e risoluzione dei problemi

### <a name="how-do-i-change-the-name-of-the-environment"></a>Come si modifica il nome dell'ambiente?

Verrà utilizzato il nome del file nella cartella di ambienti nel selettore di percorsi. Per modificare il nome dell'ambiente in uso è sufficiente rinominare l'ambiente di nome file e quindi riavviare il portale di realtà mista.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Come si rimuove gli ambienti personalizzati dalla mia selezione posizioni?

Per rimuovere un ambiente personalizzato, aprire la cartella environments sul PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) ed eliminare l'ambiente. Dopo aver riavviato il portale di realtà mista, in questo ambiente non verrà più visualizzato nel selettore di percorsi. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Come eseguire operazioni predefinite per Preferiti ambiente personalizzato?

Non è attualmente possibile modificare l'ambiente predefinito. Ogni volta che viene riavviato portale realtà mista, verrà restituito all'ambiente di Cliff House. 

### <a name="i-spawn-into-a-blank-space"></a>È possibile distribuire in uno spazio vuoto

Realtà mista di Windows [non supporta gli ambienti che superare i 256 mb](#environment-limits). Quando un ambiente supera questo limite, verrà visualizzata la finestra di sky vuoto con alcun modello.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Richiede molto tempo per caricare l'ambiente

È possibile aggiungere le ottimizzazioni facoltative all'ambiente per renderlo di caricare più velocemente. Visualizzare ["Ottimizzazione dell'ambiente"](#optimizing-your-environment) per informazioni dettagliate.

### <a name="the-scale-of-my-environment-is-incorrect"></a>La scalabilità dell'ambiente in uso non è corretto

Realtà mista di Windows si traduce glTF unità da 1 metro durante il caricamento di ambienti. Se l'ambiente carica una proporzione imprevista, ricontrollare che l'utilità di esportazione per assicurarsi che stia creando un modello su scala 1 metro. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>Il percorso di generazione nel mio ambiente non è corretto

Il percorso di generazione predefinito si trova in 0, 0,0 nell'ambiente. Il non attualmente è possibile personalizzare questo percorso, è necessario modificare il punto di generazione esportando l'ambiente con l'origine posizionato in corrispondenza del punto di generazione desiderata.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>Non vi sembra corretta nell'ambiente di file audio

Quando si crea un ambiente personalizzato, userà una simulazione di rendering acustica che non corrisponde lo spazio fisico che è stato creato. Suono possono provenire dalle indicazioni di problemi e possa sembrare ovattato. 

## <a name="see-also"></a>Vedere anche
* [Windows misti realtà Asset convertitore (su GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)

