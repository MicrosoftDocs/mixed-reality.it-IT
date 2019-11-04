---
title: Risoluzione dei problemi di HoloLens
description: Procedura per la risoluzione dei problemi di Microsoft HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: problemi, bug, risoluzione dei problemi, correzione, guida, supporto tecnico, HoloLens
ms.openlocfilehash: 855bb0cafb0d3fba0d8d97c93d9415b51bcc2fb3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438275"
---
# <a name="hololens-troubleshooting"></a>Risoluzione dei problemi di HoloLens

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>Il HoloLens non risponde o non viene avviato

Se il HoloLens non verrà avviato:
* Se i LED tramite il pulsante di alimentazione non si accendono o solo 1 LED lampeggia brevemente, potrebbe essere necessario addebitare il HoloLens.
* Se i LED si accendono quando si preme il pulsante di alimentazione, ma non viene visualizzato alcun elemento, tenere premuto il pulsante di alimentazione fino a quando tutti i 5 dei LED del pulsante di alimentazione non si spengono.

Se il HoloLens diventa bloccato o non risponde:
* Spegnere il HoloLens premendo il pulsante di alimentazione fino a quando tutti i 5 LED del pulsante di alimentazione si spengono o per 10 secondi se i LED non rispondono. Premere di nuovo il pulsante di alimentazione per avviare.

Se questi passaggi non funzionano:
* È possibile provare a [ripristinare il dispositivo](reset-or-recover-your-hololens.md).

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Gli ologrammi non hanno un aspetto positivo o sono in continua evoluzione.

Se gli ologrammi sono instabili, saltellanti o non sembrano corretti, provare una di queste correzioni:
* Pulire la visiera del dispositivo e verificare che non siano ostruiti i sensori.
* Assicurarsi che sia presente una quantità di luce sufficiente per la stanza.
* Provare a esaminare gli ambienti circostanti, in modo che HoloLens possa analizzarli più completamente.
* Provare a eseguire l'app Calibration. Consente di calibrare i HoloLens in modo che funzionino meglio per gli occhi. Passare a **impostazioni** > **utilità**di > di **sistema** . In calibrazione selezionare **Apri calibrazione**.
* Se si verificano ancora problemi dopo l'esecuzione dell'app di calibrazione, usare l'app per la regolazione dei sensori per ottimizzare i sensori del dispositivo. Passare a **impostazioni** > **utilità**di > di **sistema** . In ottimizzazione del sensore selezionare **Apri ottimizzazione del sensore**.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens non risponde ai movimenti personali.

Per assicurarsi che HoloLens possa visualizzare i movimenti, è possibile usare il frame di movimento, che estende un paio di metri su entrambi i lati. Quando HoloLens può visualizzare la mano, il cursore passa da un punto a un anello. Altre informazioni sull'uso dei [movimenti](gaze-and-commit.md#composite-gestures).

Se l'ambiente è troppo scuro, HoloLens potrebbe non visualizzare la mano, quindi assicurarsi che sia disponibile una quantità di luce sufficiente.

Se la visiera ha impronte digitali o sbavature, usare il panno di pulizia di microfibre fornito con il HoloLens per pulire delicatamente la visiera.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens non risponde ai comandi vocali.

Se Cortana non risponde ai comandi vocali, verificare che Cortana sia attivato. Nell'elenco tutte le app selezionare Cortana > Menu > notebook > impostazioni per apportare modifiche. Per altre informazioni su ciò che si può dire, vedere usare la voce per controllare HoloLens.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>Non è possibile inserire ologrammi o vedere ologrammi precedentemente posizionati.

Se HoloLens non è in grado di eseguire il mapping o caricare lo spazio, entrerà in modalità limitata e non sarà possibile inserire ologrammi o visualizzare ologrammi. Ecco come procedere:
* Assicurarsi che l'ambiente sia sufficientemente chiaro, in modo che HoloLens possa visualizzare ed eseguire il mapping dello spazio.
* Assicurarsi di essere connessi a una rete Wi-Fi. Se non si è connessi al Wi-Fi, HoloLens non è in grado di identificare e caricare uno spazio noto.
* Se è necessario creare un nuovo spazio, connettersi a Wi-Fi, quindi riavviare il HoloLens.
* Per verificare se lo spazio corretto è attivo o caricare manualmente uno spazio, passare a **impostazioni** > **sistema** > **spazi**.
* Se viene caricato lo spazio corretto e si verificano ancora problemi, lo spazio potrebbe essere danneggiato. Per risolvere il problema, selezionare lo spazio, quindi selezionare Rimuovi. Una volta rimosso lo spazio, HoloLens inizierà a eseguire il mapping dell'ambiente e creerà un nuovo spazio.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>Il HoloLens di frequente entra in modalità limitata o Visualizza un messaggio di "rilevamento perso".

Se il dispositivo visualizza spesso un messaggio "modalità limitata" o "rilevamento perso", provare i suggerimenti dei [miei ologrammi non hanno un aspetto positivo o sono in continua evoluzione](#holograms-dont-look-good-or-are-moving-around).

## <a name="my-hololens-cant-tell-what-space-im-in"></a>HoloLens non è in grado di indicare lo spazio disponibile.

Se il HoloLens non è in grado di identificare e caricare automaticamente lo spazio in cui ci si trova, assicurarsi di essere connessi al Wi-Fi, che ci sia molto chiaro nella stanza e che non siano state apportate modifiche sostanziali agli ambienti. È anche possibile caricare uno spazio manualmente o gestire gli spazi passando a **impostazioni** > **sistema** > **spazi**.

## <a name="im-getting-a-low-disk-space-error"></a>Si verifica un errore di spazio su disco insufficiente.

Per liberare spazio di archiviazione, è necessario eseguire una o più delle operazioni seguenti:
* Eliminare alcuni spazi inutilizzati. Passare a **impostazioni** > **sistema** > **spazi**, selezionare uno spazio non più necessario, quindi selezionare **Rimuovi**.
* Rimuovere alcuni degli ologrammi posizionati.
* Eliminare alcune immagini e video nell'app Photos.
* Disinstallare alcune app dal HoloLens. Nell'elenco tutte le app toccare e mantenere l'app che si vuole disinstallare e quindi selezionare **Disinstalla**.

## <a name="my-hololens-cant-create-a-new-space"></a>HoloLens non è in grado di creare un nuovo spazio.

Il problema più probabile è che si stia esaurendo lo spazio di archiviazione. Provare uno dei [suggerimenti precedenti](#im-getting-a-low-disk-space-error) per liberare spazio su disco.
