---
title: Accessori hardware
description: Descrive i tipi di accessori disponibili per l'uso con la realtà mista di Windows e come configurarli.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: procedure, accessori, Bluetooth, BT, controller, gamepad, clicker, Xbox
ms.openlocfilehash: 556fc77ffb588c02ea17e8c97293f527469216f8
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866871"
---
# <a name="hardware-accessories"></a>Accessori hardware

I dispositivi per la realtà mista di Windows supportano accessori. È possibile usare Bluetooth o USB per abbinare gli accessori supportati a un headset immersivo usando il PC a cui è connesso.

Per informazioni sull'uso di accessori Bluetooth con HoloLens, vedere [connettersi ai dispositivi Bluetooth e USB-C](https://docs.microsoft.com/hololens/hololens-connect-devices).

Gli auricolari a realtà mista di Windows richiedono accessori per l'input oltre lo [sguardo](gaze-and-commit.md) e la [voce](voice-input.md). Gli accessori supportati includono **tastiera e mouse**, **Gamepad**e **[controller di movimento](motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Associazione di accessori Bluetooth

L'associazione di una periferica Bluetooth con un headset immersivo è simile all'associazione di una periferica Bluetooth con un dispositivo Windows 10 desktop o mobile:

1. Dal menu Start aprire l'app **Settings (impostazioni** )
2. Vai ai **dispositivi**
3. Accendere la radio Bluetooth se è spenta usando il dispositivo di scorrimento
4. Posizionare il dispositivo Bluetooth in modalità di associazione. Questa operazione varia da dispositivo a dispositivo. Nella maggior parte dei dispositivi Bluetooth questa operazione viene eseguita tenendo premuto uno o più pulsanti.
5. Attendere che il nome del dispositivo venga visualizzato nell'elenco dei dispositivi Bluetooth. In tal caso, selezionare il dispositivo e quindi fare clic sul pulsante **associa** . Se sono presenti molti dispositivi Bluetooth nelle vicinanze, potrebbe essere necessario scorrere fino alla fine dell'elenco dei dispositivi Bluetooth per visualizzare il dispositivo che si sta tentando di associare.
6. Quando si abbinano periferiche Bluetooth con funzionalità di input (ad esempio, tastiere Bluetooth), è possibile che venga visualizzato un pin di 6 o 8 cifre. Assicurarsi di digitare il pin sulla periferica e quindi premere INVIO per completare l'associazione con l'auricolare.

## <a name="motion-controllers"></a>Controller del movimento

I controller di [movimento](motion-controllers.md) di realtà mista di Windows sono supportati da auricolari immersivi, ma non da HoloLens. Questi controller offrono un tracking preciso e reattivo del movimento nel campo della visualizzazione usando i sensori nell'auricolare immersiva, ovvero non è necessario installare hardware nei muri dello spazio. Ogni controller presenta diversi metodi di input.

![Controller di movimento per la realtà mista di Windows](images/winmr-ck-1080x1080-350px.jpg)

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
