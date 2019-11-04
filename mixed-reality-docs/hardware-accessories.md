---
title: Accessori hardware
description: Descrive i tipi di accessori disponibili per l'uso con HoloLens e la realtà mista di Windows e come configurarli.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: procedure, accessori, Bluetooth, BT, controller, gamepad, clicker, Xbox
ms.openlocfilehash: 566d4217fb674057e1dc3d9791b247185bf61d32
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435142"
---
# <a name="hardware-accessories"></a>Accessori hardware

I dispositivi per la realtà mista di Windows supportano accessori. Gli accessori supportati verranno abbinati a HoloLens tramite Bluetooth, mentre è possibile usare Bluetooth o USB per abbinare gli accessori supportati a un headset immersivo tramite il PC a cui è connesso.

Due scenari comuni per l'uso di accessori con HoloLens sono sostituiti dal gesto del rubinetto aereo e dalla tastiera virtuale. A questo proposito, i due accessori più comuni sono le **tastiere** **HoloLens** e Bluetooth. Microsoft HoloLens include una radio Bluetooth 4,1 e supporta i profili del [GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) Bluetooth [HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) e Bluetooth.

Gli auricolari a realtà mista di Windows richiedono accessori per l'input oltre lo [sguardo](gaze-and-commit.md) e la [voce](voice-input.md). Gli accessori supportati includono **tastiera e mouse**, **Gamepad**e **[controller di movimento](motion-controllers.md)** .

## <a name="pairing-bluetooth-accessories"></a>Associazione di accessori Bluetooth

L'associazione di una periferica Bluetooth con Microsoft HoloLens è simile all'associazione di una periferica Bluetooth con un dispositivo Windows 10 desktop o mobile:
1. Dal menu Start aprire l'app **Settings (impostazioni** )
2. Vai ai **dispositivi**
3. Accendere la radio Bluetooth se è spenta usando il dispositivo di scorrimento
4. Posizionare il dispositivo Bluetooth in modalità di associazione. Questa operazione varia da dispositivo a dispositivo. Nella maggior parte dei dispositivi Bluetooth questa operazione viene eseguita tenendo premuto uno o più pulsanti.
5. Attendere che il nome del dispositivo venga visualizzato nell'elenco dei dispositivi Bluetooth. In tal caso, selezionare il dispositivo e quindi fare clic sul pulsante **associa** . Se sono presenti molti dispositivi Bluetooth nelle vicinanze, potrebbe essere necessario scorrere fino alla fine dell'elenco dei dispositivi Bluetooth per visualizzare il dispositivo che si sta tentando di associare.
6. Quando si abbinano periferiche Bluetooth con funzionalità di input (ad esempio, tastiere Bluetooth), è possibile che venga visualizzato un pin di 6 o 8 cifre. Assicurarsi di digitare il pin sulla periferica e quindi premere INVIO per completare l'associazione con Microsoft HoloLens.

## <a name="motion-controllers"></a>Controller di movimento

I controller di [movimento](motion-controllers.md) di realtà mista di Windows sono supportati da auricolari immersivi, ma non da HoloLens. Questi controller offrono un tracking preciso e reattivo del movimento nel campo della visualizzazione usando i sensori nell'auricolare immersiva, ovvero non è necessario installare hardware nei muri dello spazio. Ogni controller presenta diversi metodi di input.

![Controller di movimento per la realtà mista di Windows](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens clic

Il HoloLens clic è il primo dispositivo periferico creato in modo specifico per HoloLens ed è incluso in HoloLens Development Edition. Il clicker HoloLens consente a un utente di fare clic e scorrere con un movimento minimo come sostituzione per il movimento di tocco aereo. Non è un sostituto per tutti i [movimenti](gaze-and-commit.md#composite-gestures). Ad esempio, i movimenti [Bloom](system-gesture.md#bloom) e [Resize o Move](gaze-and-commit.md#composite-gestures) consentono di usare i movimenti di mano. Il HoloLens Clicker è un dispositivo sensore di orientamento con un pulsante semplice. Si connette a HoloLens usando Bluetooth Low Energy (BTLE).

![Clic del HoloLens](images/hololens-clicker-500px.jpg)

Per selezionare un [ologramma](hologram.md), guardarlo, quindi fare clic su. L'orientamento del clic non è rilevante per questa operazione. Per scorrere o eseguire il panning, fare clic e tenendo premuto il pulsante del mouse verso l'alto o verso il basso o verso sinistra o verso destra. Durante lo scorrimento si raggiunge la velocità più veloce con un minimo di +/-15 ° di rotazione del polso. Lo spostamento di altro non scorre più velocemente.

All'interno del clic sono presenti due LED:
* Il LED bianco indica se il dispositivo è associato (lampeggiante) o in ricarica (a tinta unita)
* Il LED ambra indica che il dispositivo ha una batteria insufficiente (lampeggiante) o ha subito un errore (Solid)

È possibile prevedere 2 settimane o più di un uso normale a costo intero (ad esempio, 2-3 ore su un caricabatterie da parete). Quando la batteria è bassa, il LED ambrato lampeggerà 10 volte in un periodo di 5 secondi se si preme il pulsante o lo si riattiva dalla sospensione. Il LED Amber lampeggerà più rapidamente in un periodo di 5 secondi se il Clicker è in modalità di batteria a basso livello di importanza critica.

## <a name="bluetooth-keyboards"></a>Tastiere Bluetooth

Le tastiere Bluetooth QWERTY della lingua inglese possono essere abbinate e usate ovunque sia possibile usare la tastiera olografica. Il recupero di una tastiera di qualità fa la differenza, quindi è consigliabile utilizzare la [tastiera Microsoft universale](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) o il [Desktop Bluetooth di Microsoft designer](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Gamepad Bluetooth

È possibile usare un controller con app e giochi che abilitano in modo specifico il supporto del gamepad. I gamepad non possono essere usati per controllare l'interfaccia utente di HoloLens.

I controller wireless Xbox disponibili con Xbox One o sono stati venduti come accessori per la funzionalità Xbox One S per la connettività Bluetooth che li consente di usare con HoloLens e auricolari immersivi. È [necessario aggiornare](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) il controller wireless Xbox prima di poterlo usare con HoloLens.

Altre marche di gamepad Bluetooth possono funzionare con i dispositivi di realtà mista di Windows, ma il supporto può variare in base all'applicazione.

## <a name="other-bluetooth-accessories"></a>Altri accessori Bluetooth

Fino a quando la periferica supporta i profili Bluetooth HID o GATT, sarà in grado di associarsi a HoloLens. Altri dispositivi Bluetooth HID e GATT oltre alla tastiera, ai topi e al Clicker HoloLens possono richiedere una completa operatività di un'applicazione complementare in Microsoft HoloLens.

Le periferiche non supportate includono:
* Le periferiche nei profili audio Bluetooth non sono supportate.
* I dispositivi audio Bluetooth quali altoparlanti e auricolari possono apparire come disponibili nell'app Impostazioni, ma non sono supportati per l'uso con Microsoft HoloLens come endpoint audio.
* I telefoni e i PC abilitati per Bluetooth non sono supportati per essere abbinati e usati per il trasferimento di file.

## <a name="unpairing-a-bluetooth-peripheral"></a>Annullamento dell'associazione di una periferica Bluetooth
1. Dal menu Start aprire l'app **Settings (impostazioni** )
2. Vai ai **dispositivi**
3. Accendere la radio Bluetooth se è disattivata
4. Trovare il dispositivo nell'elenco dei dispositivi Bluetooth disponibili
5. Selezionare il dispositivo dall'elenco e quindi fare clic sul pulsante **Rimuovi** .

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Disabilitazione di Bluetooth in Microsoft HoloLens

Questa operazione Disabilita i componenti RF della radio Bluetooth e disattiva tutte le funzionalità Bluetooth in Microsoft HoloLens.
1. Dal menu Start aprire l'app **Settings (impostazioni** )
2. Vai ai **dispositivi**
3. Spostare il dispositivo di scorrimento per Bluetooth nella posizione OFF
