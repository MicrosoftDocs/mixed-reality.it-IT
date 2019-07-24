---
title: Input da tastiera in Unity
description: Unity fornisce la classe TouchScreenKeyboard per accettare l'input da tastiera quando non è disponibile una tastiera fisica.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: tastiera, input, Unity, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515735"
---
# <a name="keyboard-input-in-unity"></a>Input da tastiera in Unity

**Namespace** *UnityEngine*<br>
 **Tipo**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Sebbene HoloLens supporti molte forme di input, incluse le tastiere Bluetooth, la maggior parte delle applicazioni non può presupporre che tutti gli utenti dispongano di una tastiera fisica disponibile. Se l'applicazione richiede un input di testo, è necessario specificare una qualsiasi forma di tastiera sullo schermo.

Unity fornisce la classe *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* per accettare l'input da tastiera quando non è disponibile una tastiera fisica.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamento della tastiera di sistema HoloLens in Unity

In HoloLens, *TouchScreenKeyboard* sfrutta la tastiera sullo schermo del sistema. La tastiera sullo schermo del sistema non è in grado di sovrapporsi a una visualizzazione volumetrica, in modo che Unity debba creare una visualizzazione XAML 2D secondaria per mostrare la tastiera e tornare alla visualizzazione volumetrica una volta inviato l'input. Il flusso utente sarà simile al seguente:
1. L'utente esegue un'azione che causa il codice dell'app per chiamare *TouchScreenKeyboard*
    * L'app è responsabile della sospensione dello stato dell'app prima della chiamata a *TouchScreenKeyboard*
    * L'app può terminare prima di tornare alla visualizzazione volumetrica
2. Unity passa a una visualizzazione XAML 2D, che viene inserita automaticamente nel mondo
3. L'utente immette il testo usando la tastiera di sistema e invia o Annulla
4. Unity ritorna alla visualizzazione volumetrica
    * L'app è responsabile della ripresa dello stato dell'app al termine della *TouchScreenKeyboard*
5. Il testo inviato è disponibile in *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>Visualizzazioni tastiera disponibili

Sono disponibili sei diverse visualizzazioni tastiera:
* Casella di testo a riga singola
* Casella di testo a riga singola con titolo
* Casella di testo a più righe
* Casella di testo a più righe con titolo
* Casella password a riga singola
* Casella password a riga singola con titolo

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Come abilitare la tastiera di sistema in Unity

La tastiera di sistema HoloLens è disponibile solo per le applicazioni Unity esportate con il "tipo di compilazione UWP" impostato su "XAML". Quando si sceglie "XAML" come "tipo di compilazione UWP" su "D3D", si verificano compromessi. Se non si ha familiarità con questi compromessi, può essere utile esplorare una [soluzione di input alternativa](#alternative-keyboard-options) alla tastiera di sistema.
1. Aprire il menu **file** e selezionare **impostazioni di compilazione...**
2. Verificare che **la piattaforma** sia impostata su **Windows Store**, che l' **SDK** sia impostato su **Universal 10**e impostare il **tipo di compilazione UWP** su **XAML**.
3. Nella finestra di dialogo **impostazioni di compilazione** fare clic sul pulsante **Impostazioni lettore...**
4. Selezionare la scheda **impostazioni per Windows Store**
5. Espandi il gruppo **altre impostazioni**
6. Nella sezione **rendering** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco **dispositivi di realtà virtuale**
7. Assicurarsi che **Windows olografico** sia visualizzato nell'elenco degli SDK di realtà virtuale

>[!NOTE]
>Se la compilazione non viene contrassegnata come realtà virtuale supportata con il dispositivo HoloLens, il progetto viene esportato come app XAML 2D.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Uso della tastiera di sistema nell'app Unity

### <a name="declare-the-keyboard"></a>Dichiarare la tastiera

Nella classe dichiarare una variabile per archiviare *TouchScreenKeyboard* e una variabile per contenere la stringa restituita dalla tastiera.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Richiama la tastiera

Quando si verifica un evento che richiede l'input da tastiera, chiamare una di queste funzioni a seconda del tipo di input desiderato. Si noti che il titolo viene specificato nel parametro textPlaceholder.

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

### <a name="retrieve-typed-contents"></a>Recupera contenuto tipizzato

Nel ciclo di aggiornamento controllare se la tastiera ha ricevuto il nuovo input e archiviarlo per l'uso altrove.

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

## <a name="alternative-keyboard-options"></a>Opzioni di tastiera alternative

Si comprende che la disattivazione di una visualizzazione volumetrica in una visualizzazione 2D non è il modo ideale per ottenere l'input di testo dall'utente.

Le alternative attuali per sfruttare la tastiera di sistema tramite Unity includono:
* Uso della dettatura vocale per l'input (<b>Nota:</b> si tratta spesso di un errore soggetto a parole non trovate nel dizionario e non è adatto per l'immissione della password)
* Creare una tastiera che funzioni nella visualizzazione esclusiva delle applicazioni
