---
title: Il simulatore di realtà mista di Windows
description: Il simulatore di realtà mista di Windows consente di testare le app di realtà mista sul PC senza un visore VR immersivi di realtà mista di Windows.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows misti realtà, simulatore, test
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603636"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Il simulatore di realtà mista di Windows

Il simulatore di realtà mista di Windows consente di testare le app di realtà mista sul PC senza un visore VR immersivi di realtà mista di Windows. È disponibile a partire da Windows 10 Creators Update. Il simulatore è simile al [HoloLens emulatore](using-the-hololens-emulator.md), anche se il simulatore non usa una macchina virtuale. Le App in esecuzione nel simulatore vengono eseguite nella sessione utente desktop di Windows 10, come si farebbe se si usasse un visore VR immersivi. L'input umano e dell'ambiente che verrà in genere letti dai sensori in un visore VR immersivi sono invece simulate usando la tastiera, mouse o controller Xbox. Le app non devono essere modificati per l'esecuzione nel simulatore e sapere che non sono in esecuzione su un visore VR immersivi.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Abilitazione del simulatore di realtà mista di Windows

1. **Abilitare la modalità sviluppatore** da impostazioni -> aggiornamento e sicurezza -> per gli sviluppatori
2. Avviare il **portale di realtà mista** dal desktop
3. Se questa è la prima volta che l'avvio del portale, è necessario passare attraverso l'esperienza di installazione
   1. Fare clic su **iniziare**
   2. Fare clic su **accetto** di accettare il contratto
   3. Fare clic su **configurare per la simulazione (per gli sviluppatori)** per procedere con il programma di installazione senza un dispositivo fisico
   4. Fare clic su **configurare** per confermare la scelta
4. Scegliere il **per gli sviluppatori** pulsante sul lato sinistro del portale di realtà mista
5. Impostare l'opzione di attivazione/disattivazione di simulazione **su**
   * Questa operazione richiede le autorizzazioni di amministratore e la finestra di dialogo controllo dell'Account utente che viene visualizzato, è necessario accettare

Dovrebbe ora essere in esecuzione con simulazione!

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Distribuzione di App nel simulatore di realtà mista

Il simulatore viene eseguito sul proprio computer locale senza una macchina virtuale, è semplicemente possibile distribuire le app Windows universali per i **computer locale** durante il debug.

## <a name="basic-simulator-input"></a>Input di base simulatore

Controllare il simulatore è molto simile a molti comuni videogiochi 3D e la [HoloLens emulatore](using-the-hololens-emulator.md). Sono disponibili opzioni di input usando la tastiera, mouse o controller Xbox.

Per controllare il simulatore, indirizzando le operazioni eseguite da un utente simulato che portano un visore VR immersivi. Le azioni di spostare l'utente simulato e causano le interazioni con le app che rispondono come in un visore VR immersivi.
* **Scorrere in avanti, indietro, a sinistra e destra** -W, usare le chiavi A, S e D su tastiera, oppure la levetta sinistra in un controller Xbox.
* **Cercare, in basso a sinistra e con il pulsante destro** -fare clic e trascinare il mouse, usare i tasti freccia su tastiera, oppure la levetta destra in un controller Xbox.
* **Fare clic sul pulsante azione nel controller** : fare doppio clic del mouse, premere il tasto INVIO sulla tastiera o usare il pulsante in un controller Xbox.
* **Fare clic sul pulsante nel controller Home** : premere il tasto Windows o F2 sulla tastiera o fare clic sul pulsante B in un controller Xbox.
* **Lo spostamento di controller per lo scorrimento** : tenere premuto il tasto Alt, tenere premuto il pulsante destro del mouse e trascinare il puntatore del mouse su / giù, o in un controller Xbox premuto un pulsante e il trigger a destra e spostarsi su e giù sulla destra stick.

## <a name="tracked-controllers"></a>Controller di rilevamento

Il simulatore di realtà mista consente di simulare fino a due controller di movimento rilevati palmari. Abilitarle usando le opzioni di attivazione/disattivazione nel portale di realtà mista. Ogni controller simulato è:
* Posizione nello spazio
* Pulsante Home
* Pulsante Menu
* Pulsante di triangolo di ridimensionamento
* Touchpad

## <a name="see-also"></a>Vedere anche
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Advanced Input simulatore realtà mista](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Mapping spaziale in Unity](spatial-mapping-in-unity.md)
* [Mapping spaziale DirectX](spatial-mapping-in-directx.md)
