---
title: Input da tastiera in Unity
description: Unity offre la classe TouchScreenKeyboard per accettare input da tastiera quando non è disponibile alcuna tastiera fisica.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: unity input, dalla tastiera del computer, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604889"
---
# <a name="keyboard-input-in-unity"></a>Input da tastiera in Unity

**Namespace:** *UnityEngine*<br>
 **Tipo**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Mentre HoloLens supporta molti formati di input, tra cui Bluetooth tastiere, la maggior parte delle applicazioni non possono presupporre che tutti gli utenti avranno una tastiera fisica disponibile. Se l'applicazione richiede l'input di testo, è necessario specificare una forma di tastiera su schermo.

Unity offre il *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* classe per accettare input da tastiera quando non è disponibile alcuna tastiera fisica.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamento della tastiera sistema HoloLens in Unity

Su HoloLens, la *TouchScreenKeyboard* sfrutta la tastiera su schermo del sistema. Tastiera su schermo del sistema non riesce a sovrapporre all'inizio di una vista volumetrica in modo che dispone di Unity creare una visualizzazione XAML 2D secondaria per mostrare la tastiera quindi tornare alla visualizzazione volumetrica dopo che l'input è stato inviato. Il flusso utente è il seguente:
1. L'utente esegue un'azione che ha causato il codice di app di chiamare *TouchScreenKeyboard*
    * L'app è responsabile per lo stato di sospensione app prima di chiamare *TouchScreenKeyboard*
    * L'app può terminare prima del passaggio che mai tornare alla visualizzazione volumetrica
2. Unity passa a una visualizzazione XAML 2D disponibile posizionati automaticamente in tutto il mondo
3. L'utente immette testo mediante la tastiera del sistema e invia o Annulla
4. Unity passa nuovamente alla visualizzazione volumetrica
    * L'app è responsabile della ripresa dell'app stato quando la *TouchScreenKeyboard* avviene
5. È disponibile in testo inviati il *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>Viste da tastiera disponibili

Sono disponibili sei viste della tastiera a altro:
* Nella casella di testo a riga singola
* Nella casella di testo a riga singola con titolo
* Nella casella di testo multilinea
* Nella casella di testo multilinea con titolo
* Casella della password a riga singola
* Casella della password a riga singola con titolo

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Come abilitare la tastiera del sistema in Unity

I tasti di sistema HoloLens sono disponibili solo per le applicazioni di Unity che vengono esportate con il "UWP tipo Build" impostato su "XAML". Sussistono compromessi apportate quando si sceglie "XAML" come "UWP BuildType" su "D3D". Se non si ha familiarità con questi compromessi, è consigliabile consultare un [soluzione di input alternativi](#alternative-keyboard-options) alla tastiera di sistema.
1. Aprire il **File** dal menu **Build Settings...**
2. Verificare che il **piattaforma** è impostata su **Windows Store**, il **SDK** è impostata su **10 universale**e impostare il **tipo Build UWP**  al **XAML**.
3. Nel **Build Settings** finestra di dialogo, fare clic sui **le impostazioni del giocatore...**  pulsante
4. Selezionare il **le impostazioni per Windows Store** scheda
5. Espandere la **altre impostazioni** gruppo
6. Nel **Rendering** sezione, verificare il **realtà virtuale supportato** casella di controllo per aggiungere un nuovo **dispositivi per realtà virtuale** elenco
7. Assicurarsi **Windows Holographic** visualizzato nell'elenco degli SDK di realtà virtuale

>[!NOTE]
>Se non si contrassegna la compilazione come realtà virtuale supportata con il dispositivo HoloLens, il progetto verrà esportati come un'app XAML 2D.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Uso della tastiera di sistema nell'app Unity

### <a name="declare-the-keyboard"></a>Dichiarare la tastiera

Nella classe, dichiarare una variabile per archiviare le *TouchScreenKeyboard* e restituisce una variabile per contenere la stringa della tastiera.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Richiamare la tastiera

Quando si verifica un evento che richiede input da tastiera, chiamare una di queste funzioni in base al tipo di input desiderato. Si noti che il titolo è specificato nel parametro textPlaceholder.

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a>Recuperare contenuto tipizzato

Nel ciclo di aggiornamento, controllare se la tastiera ricevuto nuovo input e archiviarlo per l'uso in un' posizione.

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a>Opzioni della tastiera alternativo

Siamo consapevoli che il passaggio all'esterno di una vista in una visualizzazione 2D volumetrica non è il modo ideale per ottenere l'input di testo da parte dell'utente.

Le alternative corrente per l'uso della tastiera di sistema tramite Unity includono:
* Utilizzando la dettatura di riconoscimento vocale per l'input (<b>Nota:</b> ciò spesso è soggetta a errori per le parole non trovate nel dizionario e non è adatto per l'immissione della password)
* Creare una tastiera che funziona nella propria vista esclusivo di applicazioni
