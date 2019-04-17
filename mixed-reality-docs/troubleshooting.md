---
title: Risoluzione dei problemi di HoloLens
description: Passaggi di risoluzione dei problemi per Microsoft HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: i problemi, bug, risolvere i problemi, correggere, consente di supportare, HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597573"
---
# <a name="hololens-troubleshooting"></a>Risoluzione dei problemi di HoloLens

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>My HoloLens non risponde o non consentirà l'avvio

Se non si avviano di HoloLens:
* Se non accende il LED per il pulsante di alimentazione rapidamente o solo 1 LED lampeggia brevemente, è necessario effettuare l'addebito di HoloLens.
* Se il LED illuminano quando si preme il pulsante di alimentazione, ma non è possibile visualizzare qualsiasi elemento sugli schermi, tenere premuto il pulsante di alimentazione fino a quando non disattivare tutte e 5 i LED per il pulsante di alimentazione.

Se il HoloLens diventa bloccata o non risponde:
* Disattivare il HoloLens premendo il pulsante di alimentazione fino a quando tutte e 5 i LED per il pulsante di alimentazione autonomamente, attiva o disattiva per 10 secondi se il LED non risponde. Premere il pulsante di alimentazione nuovamente per eseguire l'avvio.

Se questi passaggi non funzionano:
* È possibile provare [il ripristino del dispositivo](reset-or-recover-your-hololens.md).

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Ologrammi aspetto non è valida o sono gli spostamenti.

Se il vntana è instabile, intermittente o non è corretti, provare una di queste correzioni:
* Pulire e risorse del dispositivo e verificare che non stia ostruendo i sensori.
* Assicurarsi che la luce è sufficiente la chat.
* Try walking tutto ed esaminando l'ambiente circostante HoloLens così possibile analizzarli più completo.
* Provare a eseguire l'app di calibrazione. Ne eseguono la taratura di HoloLens a funzionare meglio saranno accessibili ad altri. Passare a **le impostazioni** > **System** > **utilità**. In calibrazione, selezionare **calibrazione Open**.
* Se si verificano ancora problemi dopo l'esecuzione dell'app di calibrazione, usare l'app di ottimizzazione del sensore per ottimizzare i sensori del dispositivo. Passare a **le impostazioni** > **System** > **utilità**. In ottimizzazione sensore, selezionare **ottimizzazione sensore Open**.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens non risponde al mio movimenti.

Per assicurarsi che HoloLens è possibile visualizzare i movimenti, mantenere la mano nel frame di movimento, che estende un paio di piedi su entrambi i lati di voi. Quando HoloLens vede la mano, il cursore cambierà da un punto in un anello. Altre informazioni sull'uso [movimenti](gestures.md).

Se l'ambiente è troppo scuro, HoloLens potrebbero non vedere mano, quindi assicurarsi che la luce è sufficiente.

Se l'hypervisor è impronte digitali o sfumatura, usare il microfibra tessuto in dotazione con HoloLens per pulire l'hypervisor delicatamente di pulizia.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens non risponde al mio comandi vocali.

Se Cortana non risponde ai comandi vocali, assicurarsi che Cortana è attivata. Nell'elenco di tutte le app, selezionare Cortana > Menu > Notebook > Impostazioni di apportare modifiche. Per altre informazioni su ciò che è possibile dire, vedere usare la voce per controllare HoloLens.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>Non è possibile posizionare vntana o vedere vntana che ho inserito in precedenza.

Se non è possibile eseguire il mapping o caricare lo spazio di HoloLens, verrà attivata la modalità Limited e non saranno in grado di inserire vntana o vedere vntana che è stato inserito. Ecco come procedere:
* Assicurarsi che la luce è sufficiente nell'ambiente in uso, in modo HoloLens può visualizzare ed eseguire il mapping dello spazio.
* Assicurarsi che si è connessi a una rete Wi-Fi. Se non si è connessi alla rete Wi-Fi, HoloLens non è possibile identificare e caricare uno spazio noto.
* Se è necessario creare un nuovo spazio, connettersi alla rete Wi-Fi, quindi riavviare il HoloLens.
* Per verificare se lo spazio corretto è attivo, o a caricare manualmente uno spazio, andare **le impostazioni** > **System** > **spazi**.
* Se lo spazio corretto viene caricato e si verificano ancora problemi, lo spazio potrebbe essere danneggiato. Per risolvere questo problema, selezionare lo spazio, quindi scegliere Rimuovi. Una volta che lo spazio viene rimosso, HoloLens avvierà mapping l'ambiente circostante e creare un nuovo spazio.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>My HoloLens entra in modalità Limited frequente o viene visualizzato un messaggio "Rilevamento persi".

Se il dispositivo viene visualizzato spesso una "modalità limited" o un messaggio "rilevamento perso", provare i suggerimenti da [Vntana My aspetto non è valida o si muove](#holograms-dont-look-good-or-are-moving-around).

## <a name="my-hololens-cant-tell-what-space-im-in"></a>My HoloLens non è possibile stabilire lo spazio di quello si appartiene.

Se di HoloLens automaticamente non è possibile identificare e caricare lo spazio è attiva, verificare che si è connessi alla rete Wi-Fi, vi è una notevole quantità di luce nella chat room e non sono stati pubblicati importanti modifiche all'ambiente circostante. È anche possibile caricare manualmente uno spazio o gestire gli spazi, passare a **le impostazioni** > **System** > **spazi**.

## <a name="im-getting-a-low-disk-space-error"></a>Viene visualizzato un errore "spazio su disco insufficiente".

È necessario liberare spazio di archiviazione eseguendo uno o più dei seguenti:
* Eliminare alcuni spazi inutilizzati. Passare a **le impostazioni** > **System** > **spazi**, selezionare un'area non sono più necessarie e quindi selezionare **rimuovere**.
* Rimuovere alcune delle vntana che è stato inserito.
* Eliminare alcune immagini e video nell'app foto.
* Disinstallare alcune app di HoloLens. Nell'elenco di tutte le app, toccare e tenere le app da disinstallare e quindi selezionare **Disinstalla**.

## <a name="my-hololens-cant-create-a-new-space"></a>My HoloLens non è possibile creare un nuovo spazio.

Il problema più probabile è che sta per esaurirsi in spazio di archiviazione. Provare una delle [suggerimenti precedente](#im-getting-a-low-disk-space-error) per liberare spazio su disco.
