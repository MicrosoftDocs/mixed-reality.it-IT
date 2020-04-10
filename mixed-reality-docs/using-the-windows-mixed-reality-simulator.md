---
title: Uso del simulatore di realtà mista di Windows
description: Il simulatore di realtà mista di Windows consente di testare app per realtà mista nel PC senza una cuffia mista a realtà mista di Windows.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Realtà mista di Windows, simulatore, test
ms.openlocfilehash: 686cac4e9ab4b3354767e22cd87d37ffbb508dea
ms.sourcegitcommit: 37816514b8fe20669c487774b86e80ec08edcadf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2020
ms.locfileid: "81003297"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Uso del simulatore di realtà mista di Windows

Il simulatore di realtà mista di Windows consente di testare app per realtà mista nel PC senza una cuffia mista a realtà mista di Windows. È disponibile a partire da Windows 10 Creators Update. Il simulatore è simile all' [emulatore di HoloLens](using-the-hololens-emulator.md), anche se il simulatore non usa una macchina virtuale. Le app in esecuzione nel simulatore vengono eseguite nella sessione utente desktop di Windows 10, proprio come se si stesse usando un auricolare immersivo. Gli input umani e ambientali che in genere vengono letti dai sensori su un auricolare immersivo vengono invece simulati con la tastiera, il mouse o il controller Xbox. Le app non devono essere modificate per l'esecuzione nel simulatore e non sanno che non sono in esecuzione su un auricolare immersivo.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Abilitazione del simulatore di realtà mista di Windows

1. **Abilitare la modalità sviluppatore** da impostazioni-> aggiornamento e > sicurezza per gli sviluppatori
2. Avviare il **portale di realtà mista** dal desktop
3. Se è la prima volta che si avvia il portale, è necessario eseguire l'installazione
   1. Fare **clic su inizia**
   2. Fare **clic su Accetto per** accettare il contratto
   3. Fare clic su **Configura per la simulazione (per gli sviluppatori)** per procedere con l'installazione senza un dispositivo fisico
   4. Fare clic su **Configura** per confermare la scelta
4. Fai clic sul pulsante **per sviluppatori** sul lato sinistro del portale per la realtà mista
5. Attivare l' **opzione di attivazione** della simulazione
   * L'abilitazione della simulazione installa e Abilita il controller 6-DOF a sinistra per impostazione predefinita.  Prima dell'aggiornamento di Windows 10 maggio 2019, l'installazione di un controller 6-DOF simulato richiede autorizzazioni di amministratore.  È necessario accettare la finestra di dialogo di controllo dell'account utente, se visualizzata.

A questo punto dovrebbe essere in esecuzione la simulazione.

Se si vuole disabilitare la modalità sviluppatore nelle impostazioni, è necessario prima **di tutto attivare** l'opzione di attivazione della simulazione nella sezione **per sviluppatori** del portale per la realtà mista.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Distribuzione di app al simulatore di realtà mista

Poiché il simulatore viene eseguito nel PC locale senza una macchina virtuale, è possibile distribuire semplicemente le app di Windows universali nel **computer locale** durante il debug.

## <a name="basic-simulator-input"></a>Input del simulatore Basic

Il controllo del simulatore è molto simile a molti giochi video 3D comuni e l' [emulatore di HoloLens](using-the-hololens-emulator.md). Usando la tastiera, il mouse o il controller Xbox, sono disponibili diverse opzioni di input.

Per controllare il simulatore, è possibile indirizzare le azioni di un utente simulato con un headset immersivo. Le azioni spostano l'utente simulato e provocano interazioni con le app che rispondono come in un auricolare immersivo.
* **Camminare avanti, indietro, verso sinistra e verso destra**: usa i tasti W, A, S e D della tastiera oppure il joystick sinistro di un controller Xbox.
* **Guardare in alto, in basso, a sinistra e a destra**: fai clic e trascina il mouse, usa i tasti di direzione della tastiera o il joystick destro di un controller Xbox.
* **Pulsante azione premere il controller** , fare clic con il pulsante destro del mouse, premere il tasto INVIO sulla tastiera oppure usare il pulsante a in un controller Xbox.
* **Pulsante Home premere il controller** : premere il tasto Windows o il tasto F2 sulla tastiera oppure premere il pulsante B in un controller Xbox.
* **Spostamento del controller per lo scorrimento** : tenendo premuto il tasto ALT, tenendo premuto il pulsante destro del mouse, trascinare il mouse verso l'alto o verso il basso oppure in un controller Xbox posizionare il trigger destro e un pulsante verso il basso e spostare la levetta destra verso l'alto e verso il basso.

## <a name="tracked-controllers"></a>Controller rilevati

Il simulatore di realtà mista può simulare fino a due controller di movimento rilevati e gestiti manualmente. Abilitarli usando le opzioni di attivazione/disattivazione nel portale per la realtà mista. Ogni controller simulato ha:
* Posizione e orientamento nello spazio
* Pulsante Home
* Pulsante Menu
* Pulsante grip
* Touchpad
* Levetta
* Livello batteria

## <a name="see-also"></a>Vedere anche
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Input avanzato del simulatore di realtà mista](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Mapping spaziale in DirectX](spatial-mapping-in-directx.md)
