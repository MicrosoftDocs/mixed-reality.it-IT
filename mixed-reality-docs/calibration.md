---
title: Calibrazione
description: La calibratura del dpi (interpupillare distance) può migliorare la qualità degli oggetti visivi. Sia HoloLens che gli auricolari a realtà mista di Windows offrono modi per personalizzare il dispositivo.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: calibrazione, comodità, oggetti visivi, qualità, dpi
ms.openlocfilehash: 5f8e6aef1df0efe4c64c807e627f69c7949363f2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974809"
---
# <a name="improve-visual-quality-and-comfort"></a>Migliorare la qualità visiva e la comodità
Gli auricolari HoloLens, HoloLens 2 e Windows Mixed Reality immersive offrono diversi modi per migliorare la qualità dell'esperienza visiva. 

## <a name="hololens"></a>HoloLens

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

## <a name="hololens-2"></a>HoloLens 2

### <a name="calibration"></a>Calibrazione 

In HoloLens 2 verrà richiesto di calibrare gli oggetti visivi durante la configurazione del dispositivo. Agli utenti viene richiesto di esaminare il set di destinazioni di fissaggio. In questo modo, il dispositivo può modificare il rendering degli ologrammi per consentire all'utente di garantire ologrammi posizionati in modo accurato, un'esperienza di visualizzazione 3D più comoda e una migliore qualità di visualizzazione Tutte le regolazioni si verificano in tempo reale senza dover eseguire l'ottimizzazione manuale. 

### <a name="calibration-when-sharing-a-device"></a>Calibrazione durante la condivisione di un dispositivo 

Il dispositivo Hololens 2 può essere condiviso tra le persone, senza dover eseguire l'installazione del dispositivo. Hololens 2 chiederà all'utente di calibrare gli oggetti visivi quando il dispositivo viene messo in testa, se l'utente è nuovo del dispositivo. Se l'utente ha già calibrato gli oggetti visivi nel dispositivo, la visualizzazione verrà regolata facilmente per la qualità e la visualizzazione confortevole quando l'utente inserisce il dispositivo in testa.  

### <a name="launching-the-calibration-app-from-settings"></a>Avvio dell'app di calibrazione dalle impostazioni
1. Usare l'azione di avvio per ottenere il menu Start.
2. Selezionare **+** questa opzione per visualizzare tutte le app se **le impostazioni** non sono bloccate per l'avvio.
3. **Impostazioni**di avvio.
4. Passare a**utilità** di **sistema** > e selezionare **Open Calibration**.

## <a name="immersive-headsets"></a>Visori VR immersive

Per modificare il dispositivo dpi all'interno dell'auricolare, aprire l'app Impostazioni e passare a**visualizzazione** della cuffia a **realtà** > mista e spostare il controllo dispositivo di scorrimento. Le modifiche verranno visualizzate in tempo reale nell'auricolare. Se si conosce il valore di dpi, forse da una visita all'oculista, è possibile immetterlo direttamente.

È anche possibile modificare questa impostazione selezionando **Impostazioni** > **reality** > **Headset display** nel PC.

Se la cuffia non supporta la personalizzazione di dpi, questa impostazione verrà disabilitata.

## <a name="see-also"></a>Vedere anche
* [Considerazioni relative all'ambiente per HoloLens](environment-considerations-for-hololens.md)
