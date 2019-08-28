---
title: Calibrazione
description: La calibratura del dpi (interpupillare distance) può migliorare la qualità degli oggetti visivi. Sia HoloLens che gli auricolari a realtà mista di Windows offrono modi per personalizzare il dispositivo.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: calibrazione, comodità, oggetti visivi, qualità, dpi
ms.openlocfilehash: 1fc3904f4b3e441a967616f20e4287dbc7f08835
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047050"
---
# <a name="improve-visual-quality-and-comfort"></a>Migliorare la qualità visiva e la comodità
HoloLens, HoloLens 2 e gli auricolari a realtà mista di Windows offrono diversi modi per migliorare la qualità dell'esperienza visiva. 

## <a name="hololens-2"></a>Hololens 2

### <a name="calibration"></a>Calibrazione

Hololens 2 è progettato per fornire le immagini visive più elevate e la comodità per i clienti. La tecnologia di rilevamento degli occhi viene usata per migliorare l'esperienza utente nella visualizzazione e nell'interazione con l'ambiente virtuale.  
In HoloLens 2 verrà richiesto di calibrare gli oggetti visivi durante la configurazione del dispositivo. Agli utenti viene richiesto di esaminare il set di destinazioni di fissaggio. In questo modo, il dispositivo può modificare il rendering degli ologrammi per consentire all'utente di garantire ologrammi posizionati in modo accurato, una comoda esperienza di visualizzazione 3D e una migliore qualità di visualizzazione Tutte le regolazioni si verificano in tempo reale senza dover eseguire l'ottimizzazione manuale. Usando gli occhi come punti di riferimento, il dispositivo viene regolato per ogni utente e gli oggetti visivi vengono ottimizzati quando l'auricolare si sposta leggermente in tutto il consumo. Il rilevamento delle posizioni oculari viene utilizzato internamente dal sistema e gli sviluppatori non devono eseguire alcuna operazione per sfruttare questa funzionalità. Queste informazioni non sono disponibili per gli sviluppatori. In Hololens 2, l'esecuzione della calibrazione garantisce anche un accurato rilevamento degli sguardi per ogni utente. Il tracciamento oculare consente alle applicazioni di tenere traccia di dove guarda l'utente in tempo reale. Questo è lo strumento principale che gli sviluppatori possono sfruttare per consentire un livello completamente nuovo di contesto, comprensione umana e interazioni nell'esperienza olografica.  
La calibrazione viene archiviata localmente nel dispositivo e non è associata ad alcuna informazione sull'account. Non è presente alcun record di chi ha usato il dispositivo senza calibrazione. Questo significa che i nuovi utenti riceveranno la richiesta di calibrare gli oggetti visivi quando useranno il dispositivo per la prima volta, oltre che per gli utenti che hanno rifiutato la taratura in precedenza o se la taratura non è riuscita. La taratura può sempre essere eliminata dal dispositivo in **Impostazioni** > **privacy** > **eye tracker**. 

### <a name="calibration-failures"></a>Errori di calibrazione

La calibrazione dovrebbe funzionare per la maggior parte degli utenti, ma in alcuni casi l'utente potrebbe non essere in grado di calibrare correttamente.  
Alcuni esempi di errori di calibrazione sono dovuti a:
- L'utente si distrae e non segue gli obiettivi di calibrazione durante l'esperienza di calibrazione
- Visiera del dispositivo Dirty o graffiato o visiera del dispositivo non posizionata correttamente 
- Occhiali sporchi o graffiati
- Determinati tipi di lenti e occhiali di contatto (lenti a contatto colorate, alcune lenti a contatto torica, occhiali di blocco IR, alcuni occhiali di prescrizione elevati, occhiali da sole e così via)
- Makeup più pronunciato, alcune estensioni delle ciglia
- Occlusioni di occhi e/o visiera del dispositivo (capelli, alcuni frame di occhiali di spessore)
- Fisiologia degli occhi, determinate condizioni degli occhi e/o chirurgia degli occhi (alcuni occhi stretti, ciglia lunghe, ambliopia, nistagmo, alcuni casi di LASIK o altri interventi chirurgici, ecc.)

Se la taratura ha esito negativo, provare una di queste correzioni: 
- Pulire la visiera del dispositivo
- Pulisci gli occhiali
- Eseguire il push della visiera del dispositivo fino a
- Assicurarsi che non ci siano ostacoli ai sensori o agli occhi (ad esempio, i capelli) 
- Assicurarsi che la stanza sia sufficiente e che l'utente non sia sotto la luce solare diretta
- Assicurarsi di seguire attentamente le destinazioni durante la taratura

Se sono state seguite tutte le linee guida e la taratura è ancora in errore, è possibile disabilitare la richiesta di calibrazione in **Impostazioni** > **calibrazione**del**sistema** > . ' Quando un nuovo utente usa questa Hololens, è necessario che venga ottimizzata automaticamente la richiesta di eseguire la taratura degli occhi. Tenere presente che ciò potrebbe comportare la qualità e il disagio del rendering degli ologrammi.

### <a name="launching-the-calibration-app-from-settings"></a>Avvio dell'app di calibrazione dalle impostazioni
1. Usare l'azione di avvio per ottenere il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selezionare **tutte le app** per visualizzare tutte le app se **le impostazioni** non sono bloccate per l'avvio.
3. **Impostazioni**di avvio.
4. Passare alla calibrazione**degli occhi** di**calibrazione** > del **sistema** > e selezionare **Esegui calibrazione occhio**.

### <a name="calibration-when-sharing-a-devicesession"></a>Calibrazione durante la condivisione di un dispositivo/sessione

Hololens 2 può essere condiviso tra le persone, senza dover eseguire l'installazione del dispositivo. Hololens 2 richiede all'utente di calibrare gli oggetti visivi quando il dispositivo viene messo in testa se l'utente è nuovo del dispositivo. Se l'utente ha precedentemente calibrato gli oggetti visivi nel dispositivo, la visualizzazione verrà regolata facilmente per la qualità e un'esperienza di visualizzazione comoda quando l'utente inserisce il dispositivo in testa. 


## <a name="hololens-v1"></a>Hololens (V1)

La calibratura del dpi (interpupillare distance) può migliorare la qualità degli oggetti visivi.

### <a name="during-setup"></a>Durante l'installazione

![Schermata di allineamento del dito dpi al secondo passaggio](images/ipd-finger-alignment-300px.jpg)<br>

*Schermata di allineamento del dito dpi al secondo passaggio*

In HoloLens verrà richiesto di calibrare gli oggetti visivi durante l'installazione. Ciò consente al dispositivo di modificare la visualizzazione dell'ologramma in base alla [distanza interpupillare](https://en.wikipedia.org/wiki/Interpupillary_distance) (dpi) dell'utente. Con un valore DIP errato, gli ologrammi possono apparire instabili o a una distanza non corretta.

Quando Cortana introduce se stesso, il primo passaggio di configurazione è taratura. È consigliabile completare il passaggio di calibrazione durante questa fase di configurazione, ma è possibile ignorarlo attendendo che Cortana chieda di "ignorare" per continuare.

Agli utenti viene chiesto di allineare il dito con una serie di sei destinazioni per occhio. Tramite questo processo, HoloLens imposta il DPI corretto per l'utente. Se è necessario aggiornare o modificare la calibrazione per un nuovo utente, è possibile eseguirla al di fuori del programma di installazione usando l'app Calibration.

### <a name="calibration-app"></a>App di calibrazione

La calibrazione può essere eseguita in qualsiasi momento tramite l'app Calibration. L'app Calibration viene installata per impostazione predefinita ed è possibile accedervi dal menu Start o dall'app Settings. Per migliorare la qualità degli oggetti visivi o calibrare gli oggetti visivi per un nuovo utente, è consigliabile eseguire la calibrazione.

**Avvio dell'app dall'inizio**
1. Usare [Bloom](gestures.md#bloom) per aprire il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selezionare **+** per visualizzare tutte le app.
3. Avviare la **calibrazione**.

![Accesso all'app di calibrazione dalla shell](images/calibration-shell.png)

![App di calibrazione visualizzata come cubo attivo dopo l'avvio](images/calibration-livecube-200px.png)

**Avvio dell'app dalle impostazioni**
1. Usare [Bloom](gestures.md#bloom) per aprire il [menu Start](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Selezionare **+** questa opzione per visualizzare tutte le app se **le impostazioni** non sono bloccate per l'avvio.
3. **Impostazioni**di avvio.
4. Passare a**utilità** di **sistema** > e selezionare **Open Calibration**.

![Avvio dell'app di calibrazione dall'app impostazioni](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a>Visori VR immersive

Per modificare il dispositivo dpi all'interno dell'auricolare, aprire l'app Impostazioni e passare a**visualizzazione** della cuffia a **realtà** > mista e spostare il controllo dispositivo di scorrimento. Le modifiche verranno visualizzate in tempo reale nell'auricolare. Se si conosce il valore di dpi, forse da una visita all'oculista, è possibile immetterlo direttamente.

È anche possibile modificare questa impostazione selezionando **Impostazioni** > **reality** > **Headset display** nel PC.

Se la cuffia non supporta la personalizzazione di dpi, questa impostazione verrà disabilitata.

## <a name="see-also"></a>Vedere anche
* [Considerazioni relative all'ambiente per HoloLens](environment-considerations-for-hololens.md)
