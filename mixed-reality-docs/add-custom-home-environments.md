---
title: Aggiungere ambienti Home personalizzati
description: Oltre agli ambienti domestici per la realtà mista di Windows, è possibile sperimentare la creazione e l'uso dei propri.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, Home, ambienti personalizzati, luoghi, Cliff House, Skyloft, utente, creazione
ms.openlocfilehash: d0cdb878f1994cb5f898f06b98d74dee3dd4fdf1
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024536"
---
# <a name="add-custom-home-environments"></a>Aggiungere ambienti Home personalizzati

>[!NOTE]
>Si tratta di una funzionalità sperimentale. È possibile provarlo e divertirlo, ma non stupirsi se tutto funziona come previsto. Microsoft sta valutando la redditività di questa funzionalità e ne è interessato l'uso. per informazioni sull'esperienza e sui bug trovati, vedere i [forum per sviluppatori](https://forums.hololens.com/categories/custom-home-environments).

A partire dall' [aggiornamento di Windows 10 aprile 2018](#release-notes-april-2018.md), è stata abilitata una funzionalità sperimentale che consente di aggiungere ambienti personalizzati alla selezione posizioni (dal menu Start) da usare come [Home realtà mista di Windows](#navigating-the-windows-mixed-reality-home.md). La realtà mista di Windows presenta due ambienti predefiniti, Cliff House e Skyloft, che è possibile scegliere come Home. La creazione di ambienti personalizzati consente di espandere l'elenco con le proprie creazioni. Questa funzionalità è disponibile in uno stato preliminare per valutare l'interesse degli autori e degli sviluppatori, vedere quali tipi di mondi creare e comprendere come usare diversi strumenti di creazione.

Quando si usa un ambiente personalizzato si noterà che il Teleporting, l'interazione con le app e il posizionamento degli ologrammi funzionano esattamente come avviene in Cliff House e Skyloft. È possibile esplorare il Web in un panorama Fantasy o riempire una città futuristica con ologrammi. le possibilità sono infinite.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Ambienti Home personalizzati</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Tentativo di un ambiente di esempio

È stato creato un ambiente di esempio che illustra alcune delle possibilità creative degli ambienti domestici personalizzati. Per provarlo, attenersi alla procedura seguente:
1. [Scarica l'ambiente Fantasy Island di esempio](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (punti di collegamento all'eseguibile autoestraente).

    ![Ambiente di esempio Fantasy Island](images/FantasyLand.jpg)<br>
    *Ambiente di esempio Fantasy Island*<br>

2. Eseguire il file **Fantasy_Island. exe** appena scaricato.

    > [!NOTE]
    > Quando si tenta di eseguire un file con estensione exe scaricato dal Web (come questo), è possibile che venga visualizzato un messaggio popup "Windows Protected your PC". Per eseguire Fantasy_Island. exe da questa finestra popup, selezionare **altre informazioni** e quindi **eseguire comunque**. Questa impostazione di sicurezza ha lo scopo di impedire il download dei file che potrebbero non essere attendibili. scegliere questa opzione solo quando si considera attendibile l'origine del file.

3. Aprire **Esplora file** e passare alla cartella ambienti incollando il codice seguente nella barra degli indirizzi: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.
4. Copiare l'ambiente di esempio scaricato in questa cartella.
5. Riavviare il **portale di realtà mista**. Verrà aggiornato l'elenco di ambienti nel selettore di posizioni.
6. Inserire l'auricolare. Quando ci si trova nella Home page, aprire il **menu Start** usando il pulsante Windows del controller.
7. Selezionare l'icona **posizioni** sopra l'elenco di app bloccate per scegliere un ambiente Home.
8. L'ambiente Fantasy Island è stato scaricato nell'elenco di posizioni. Selezionare **Fantasy Island** per accedere al nuovo ambiente Home personalizzato.

## <a name="creating-your-own-custom-environment"></a>Creazione di un ambiente personalizzato

Oltre a usare gli ambienti di esempio, è possibile esportare gli ambienti personalizzati usando il software di modifica 3D preferito. 

### <a name="modeling-guidelines"></a>Linee guida per la modellazione

Quando si modella l'ambiente, tenere presenti le indicazioni seguenti. In questo modo si garantisce che l'utente possa generare un orientamento corretto in un mondo di dimensioni credibili:

1. Gli utenti generano a 0, 0, 0, in modo da centrare la posizione di generazione desiderata intorno all'origine.
2. Le unità di lavoro devono essere impostate su contatori in modo che le risorse possano essere create a livello globale.
3. L'asse su deve essere impostato su "Y".
4. L'asset deve riguardare "Avanti" verso l'asse Z positivo.
5. Non è necessario combinare tutte le mesh, ma è consigliabile usare i dispositivi con vincoli di risorse.

### <a name="exporting-your-environment"></a>Esportazione dell'ambiente

La realtà mista di Windows si basa su Binary glTF (. glb) come formato di distribuzione degli asset per gli ambienti. glTF è uno standard gratuito aperto per la distribuzione di asset 3D gestito dal gruppo Khronos. Man mano che glTF si evolve come standard di settore per il contenuto 3D interoperativo, il supporto di Microsoft per il formato tra le app e le esperienze di Windows.

Il primo passaggio nell'esportazione degli asset da usare come ambienti Home personalizzati è la generazione di un modello glTF 2,0. Il gruppo di lavoro glTF gestisce un [elenco degli esportatori e dei convertitori supportati](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) per la creazione di un modello glTF 2,0. Per iniziare, usare uno dei programmi elencati in questa pagina per creare ed esportare un modello glTF 2,0 o convertire un modello esistente usando uno dei convertitori supportati.

Vedere anche [questo articolo utile](https://www.khronos.org/blog/art-pipeline-for-gltf) che offre una panoramica di un flusso di lavoro artistico per l'esportazione diretta di modelli GlTF da Blender e 3ds max. 

### <a name="environment-limits"></a>Limiti di ambiente

Tutti gli ambienti devono essere < 256 MB. Gli ambienti con dimensioni maggiori di 256 MB non vengono caricati e il fallback viene eseguito in un mondo vuoto con solo i SKYBOX predefiniti che circondano l'utente. Quando si creano i modelli, tenere presente questo limite di dimensioni del file. Inoltre, se si prevede di ottimizzare l'ambiente usando WindowsMRAssetConverter, come descritto di seguito, è necessario tenere presente che le dimensioni della trama aumenteranno, in quanto Query Optimizer crea trame con dimensioni di file maggiori, ma carica più velocemente. 

### <a name="optimizing-your-environment"></a>Ottimizzazione dell'ambiente

La realtà mista di Windows supporta una serie di ottimizzazioni facoltative che consentono di ridurre in modo significativo il tempo di caricamento degli ambienti. Questo può essere particolarmente importante per gli ambienti con molte trame, in quanto talvolta si timeout durante il caricamento. In generale, si consiglia di eseguire questo passaggio per tutti gli asset, tuttavia gli ambienti più piccoli con trame o a bassa risoluzione non saranno sempre necessari. 

Per semplificare questo processo, è stato creato il convertitore di asset per la [realtà mista di Windows (disponibile in GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) per eseguire le ottimizzazioni. Questo strumento usa un set di utilità disponibili in Microsoft glTF Toolkit per ottimizzare qualsiasi glTF standard 2,0 o glb eseguendo un'ulteriore compressione di trama, la compressione e la risoluzione del ridimensionamento. 

Il convertitore supporta attualmente diversi flag per ottimizzare il comportamento esatto delle ottimizzazioni. Per ottenere risultati ottimali, è consigliabile eseguire con i flag seguenti:

Flag|Valori consigliati|Descrizione
---|---|---
-Max-texture-size|1024 o 2048| Per ottimizzare la qualità delle trame, il valore predefinito è 512x512. Si noti che un valore più grande influirà in modo significativo sulle dimensioni del file dell'ambiente, in modo da tenere presente il limite di 256 MB
-min-Version|1803|Gli ambienti personalizzati sono supportati solo nelle versioni di Windows > = 1803. Questo flag rimuove le trame per le versioni precedenti e riduce le dimensioni del file dell'asset finale

Ad esempio:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Test dell'ambiente

Dopo aver creato l'ambiente finale con estensione GLB, è possibile eseguirne il test nell'auricolare. Iniziare dal passaggio 2 della sezione ["tentativo di un ambiente di esempio"](#trying-a-sample-environment) per usare l'ambiente personalizzato come Home realtà mista. 

## <a name="feedback"></a>Commenti e suggerimenti

Mentre stiamo valutando questa funzionalità sperimentale, siamo interessati a scoprire come stai usando gli ambienti personalizzati, eventuali bug che potresti incontrare e come preferisci la funzionalità. Condividere tutti i commenti e suggerimenti per la creazione e l'uso di ambienti Home personalizzati nei [forum per sviluppatori](https://forums.hololens.com/categories/custom-home-environments).

## <a name="troubleshooting-and-tips"></a>Risoluzione dei problemi e suggerimenti

### <a name="how-do-i-change-the-name-of-the-environment"></a>Ricerca per categorie modificare il nome dell'ambiente?

Il nome del file nella cartella ambienti verrà usato nella selezione posizioni. Per modificare il nome dell'ambiente, è sufficiente rinominare il nome del file dell'ambiente e quindi riavviare il portale di realtà mista.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Ricerca per categorie rimuovere gli ambienti personalizzati dalla selezione risorse personali?

Per rimuovere un ambiente personalizzato, aprire la cartella Environments nel PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) ed eliminare l'ambiente. Dopo aver riavviato il portale Mixed Reality, questo ambiente non verrà più visualizzato nella selezione dei punti. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Ricerca per categorie per impostazione predefinita l'ambiente personalizzato preferito?

Attualmente non è possibile modificare l'ambiente predefinito. Ogni volta che si riavvia il portale di realtà mista, si verrà restituiti all'ambiente Cliff House. 

### <a name="i-spawn-into-a-blank-space"></a>Viene generato uno spazio vuoto

La realtà mista [di Windows non supporta ambienti che superano 256 MB](#environment-limits). Quando un ambiente supera questo limite, verrà visualizzata la casella Sky vuota senza modello.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Il caricamento dell'ambiente richiede molto tempo

È possibile aggiungere ottimizzazioni facoltative all'ambiente in modo da renderle più veloci. Per informazioni dettagliate, vedere l'argomento relativo all' [ottimizzazione dell'ambiente](#optimizing-your-environment) .

### <a name="the-scale-of-my-environment-is-incorrect"></a>La scala dell'ambiente non è corretta

La realtà mista di Windows converte le unità glTF in 1 contatore durante il caricamento degli ambienti. Se l'ambiente carica una scala imprevista, controllare l'utilità di esportazione per assicurarsi di eseguire la modellazione a una scala da 1 misuratore. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>Il percorso di generazione nell'ambiente in uso non è corretto

Il percorso di generazione predefinito si trova a 0, 0, 0 nell'ambiente. Attualmente non è possibile personalizzare questo percorso, quindi è necessario modificare il punto di spawn esportando l'ambiente con l'origine posizionata in corrispondenza del punto di generazione desiderato.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>L'audio non viene emesso correttamente nell'ambiente

Quando si crea l'ambiente personalizzato, verrà usata una simulazione di rendering acustico che non corrisponde allo spazio fisico creato. Il suono può provenire dalle direzioni errate e può sembrare ovattato. 

## <a name="see-also"></a>Vedere anche
* [Microsoft Mixed Reality asset Converter (su GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)

