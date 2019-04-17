---
title: Accessori hardware
description: Descrive i tipi di accessori disponibili per l'uso con HoloLens e realtà mista di Windows e come impostarli.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: procedure, Accessori, bluetooth, bt, controller, gamepad, clicker, xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604739"
---
# <a name="hardware-accessories"></a>Accessori hardware

I dispositivi di realtà mista di Windows supportano accessori. Si saranno abbinare supportati accessori per HoloLens tramite Bluetooth, mentre è possibile usare Bluetooth o USB-to-pair supportati accessori per un visore VR immersivi tramite il PC a cui è connessa.

Due scenari comuni per l'uso di accessori con HoloLens sono come sostituti di aria toccare gesti e la tastiera virtuale. A tale scopo, i due accessori più comuni sono le **HoloLens Clicker** e **Bluetooth tastiere**. Microsoft HoloLens include un'opzione Bluetooth 4.1 e supporta [HID Bluetooth](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) e [Bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) profili.

Auricolari coinvolgenti di realtà mista di Windows richiedono accessori per l'input di là [estasiati](gaze.md) e [vocale](voice-input.md). Accessori supportati includono **tastiera e mouse**, **gamepad**, e  **[movimento controller](motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Abbinamento degli accessori Bluetooth

Associazione periferiche Bluetooth con Microsoft HoloLens è simile all'associazione Bluetooth periferiche con Windows 10 desktop o dispositivo mobile:
1. Dal Menu Start, aprire il **impostazioni** app
2. Passare a **dispositivi**
3. Attivare l'opzione Bluetooth se è disattivata tramite l'opzione dispositivo di scorrimento
4. Inserire il dispositivo Bluetooth in modalità di associazione. Il valore varia da un dispositivo a altro. Nella maggior parte delle periferiche Bluetooth questa operazione viene eseguita, tenere premuto uno o più pulsanti.
5. Attendere che il nome del dispositivo venga visualizzato nell'elenco di dispositivi Bluetooth. Quando, selezionare il dispositivo quindi il **coppia** pulsante. Se si dispone di molti dispositivi Bluetooth nelle vicinanze si potrebbero essere necessario scorrere verso il basso dell'elenco dei dispositivi Bluetooth per visualizzare il dispositivo che si sta tentando di associare.
6. Se l'associazione periferiche Bluetooth con input funzionalità (ad esempio: Bluetooth tastiere), potrebbe essere visualizzato una cifra di 6 o un pin a 8 cifre. Verificare di aver digitato pin nella periferica e quindi premere INVIO per associazione completa con Microsoft HoloLens.

## <a name="motion-controllers"></a>Controller di movimento

Realtà mista di Windows [controller di movimento](motion-controllers.md) sono supportati da auricolari coinvolgenti, ma non HoloLens. Questi controller offrono preciso e reattivo rilevamento del movimento nel campo visivo usando i sensori nel visore VR immersivi, ovvero non vi è alcuna necessità di installare hardware sulle pareti nello spazio di. Ogni controller offre diversi metodi di input.

![Controller del movimento di realtà mista di Windows](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

Il HoloLens Clicker è il primo dispositivo periferico creato appositamente per HoloLens e viene fornita con HoloLens Development Edition. Il HoloLens Clicker consente all'utente di fare clic e scorre con movimento manuale minimo come una sostituzione per il movimento indice puntato. Non è una sostituzione per tutti i [movimenti](gestures.md). Ad esempio, [bloom](gestures.md#bloom) e [ridimensionare o spostare](gestures.md#composite-gestures) i movimenti di usano i movimenti di mano. Il clicker HoloLens è un dispositivo sensore di orientamento con un semplice pulsante. Si connette a di HoloLens tramite Bluetooth Low Energy (BTLE).

![Il HoloLens Clicker](images/hololens-clicker-500px.jpg)

Per selezionare una [ologrammi](hologram.md)fissare lo e quindi fare clic su. Orientamento del clicker non è rilevante per questa operazione. Scorrere verso il o eseguire una panoramica, fare clic e tenere premuto, quindi ruotare il Clicker su/giù o sinistra/destra. Durante lo scorrimento, si otterrà la massima velocità con un po' di + /-15° di rotazione del polso. Lo spostamento di più non scorre uno più velocemente.

Esistono due LED all'interno di Clicker:
* Il LED bianco indica se il dispositivo è associazione (lampeggiare) e degli addebiti (continuo)
* Ambra LED indica che il dispositivo ha batteria in esaurimento (lampeggiare) o ha subito un errore (continuo)

È possibile prevedere almeno di 2 settimane di utilizzo standard basato su un addebito completo (ad esempio, 2 e 3 ore nel caricabatterie parete). Quando la batteria è ridotto, il giallo che LED sarà intermittente 10 volte in un periodo di 5 secondi se si preme il pulsante o la riattivazione da sospensione. Ambra che LED sarà intermittente più rapidamente in un periodo di 5 secondi se il Clicker è in modalità di batteria quasi scarica.

## <a name="bluetooth-keyboards"></a>Bluetooth tastiere

Tastiere Qwerty Bluetooth in lingua inglese possono essere associate e usata ovunque che è possibile usare la tastiera holographic. Recupera una tastiera di qualità esegue una differenza, pertanto, è consigliabile il [Microsoft Keyboard fold Universal](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) o il [Bluetooth Designer di Microsoft Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Gamepad Bluetooth

È possibile usare un controller con le App e giochi che specificamente attivare il supporto su gamepad. Gamepad non può essere utilizzato per controllare l'interfaccia utente di HoloLens.

Controller Wireless Xbox fornite con i dispositivi una Xbox o vendute di accessori per la funzionalità di Xbox S una connettività Bluetooth che consentono loro di essere utilizzato con HoloLens e auricolari coinvolgente e concreto. Il Controller Wireless Xbox [devono essere aggiornate](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) prima di poter essere utilizzato con HoloLens.

Gli altri marchi di Bluetooth gamepad potrebbero funzionare con i dispositivi di realtà mista di Windows, ma il supporto verrà variano a seconda dell'applicazione.

## <a name="other-bluetooth-accessories"></a>Altri accessori Bluetooth

Purché la periferica supporti profili Bluetooth HID o GATT, sarà in grado di effettuare l'associazione con HoloLens. Altri dispositivi Bluetooth HID e GATT oltre alla tastiera, mouse e il HoloLens Clicker richiedano un'applicazione complementare in Microsoft HoloLens completa operatività.

Periferiche non supportate includono:
* Periferiche Bluetooth audio dei profili non sono supportate.
* Dispositivi audio Bluetooth, ad esempio altoparlanti e cuffie appaia come disponibili nell'app impostazioni, ma non sono supportati per l'utilizzo con Microsoft HoloLens come endpoint audio.
* PC e telefoni non sono supportati per essere associato e usato per il trasferimento file.

## <a name="unpairing-a-bluetooth-peripheral"></a>Associazione annullamento periferiche Bluetooth
1. Dal Menu Start, aprire il **impostazioni** app
2. Passare a **dispositivi**
3. Attivare l'opzione Bluetooth se è off
4. Trovare il dispositivo nell'elenco dei dispositivi Bluetooth disponibili
5. Selezionare il dispositivo dall'elenco e quindi selezionare il **rimuovere** pulsante

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>La disabilitazione di Bluetooth nel Microsoft HoloLens

Verrà disattivare i componenti RF dell'opzione Bluetooth e disabilitare tutte le funzionalità di Bluetooth nel Microsoft HoloLens.
1. Dal Menu Start, aprire il **impostazioni** app
2. Passare a **dispositivi**
3. Spostare il commutatore di dispositivo di scorrimento per Bluetooth in posizione OFF
