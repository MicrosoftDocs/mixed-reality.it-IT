---
title: Input porting guide per Unity
description: Informazioni su come gestire gli input per realtà mista di Windows in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: input, unity, portabilità
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602792"
---
# <a name="input-porting-guide-for-unity"></a>Input porting guide per Unity

È possibile convertire l'input per la logica in Windows Mixed Reality usando uno dei due approcci, API Input.GetButton/GetAxis generale di Unity che si estendono su più piattaforme o i XR Windows specifiche. WSA. API di input che offrono dati più complessi in modo specifico per i controller di movimento e le mani HoloLens.

## <a name="general-inputgetbuttongetaxis-apis"></a>API Input.GetButton/GetAxis generale

Unity attualmente Usa le relative API Input.GetButton/Input.GetAxis generale di input per esporre [SDK Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) e [SDK OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se le app che già utilizzano queste API per l'input, si tratta del percorso più semplice per il supporto di controller di movimento in realtà mista di Windows: è necessario solo modificare il mapping dei pulsanti e assi nel gestore di Input.

Per altre informazioni, vedere la [tabella di mapping pulsante/asse Unity](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e il [panoramica delle API di Unity comuni](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR Windows specifiche. WSA. API di input

Se l'app viene compilata già la logica di input personalizzata per ogni piattaforma, è possibile scegliere di usare le API di input spaziali specifiche di Windows con il **UnityEngine.XR.WSA.Input** dello spazio dei nomi. Ciò consente di accedere a informazioni aggiuntive, ad esempio accuratezza posizione o il tipo di origine, consentendo di indicare le mani e controller distanti in HoloLens.

Per altre informazioni, vedere la [panoramica delle APIs UnityEngine.XR.WSA.Input](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Triangolo di ridimensionamento posa confronto posa puntamento

Realtà mista di Windows supporta controller di movimento in un'ampia gamma di fattori di forma, con la progettazione del ogni controller che differiscono per la relazione tra la posizione dell'utente mano e naturale "inoltro" direzione tale app deve usare per fare riferimento durante il rendering di controller.

Per rappresentare meglio questi controller, esistono due tipi di può causare che è possibile esaminare per ogni origine di interazione:

* Il **triangolo posa**, che rappresenta la posizione di palmo di una mano rilevata da un HoloLens o palmo che contiene un controller di movimento.
    * In coinvolgenti auricolari, questo posa è particolarmente utile per eseguire il rendering **manuale dell'utente** oppure **mantenuto un oggetto a disposizione dell'utente**, ad esempio un doppio taglio o gun.
    * Il **afferrare posizione**: Il centroide palm quando tenendo naturalmente, il controller è regolato sinistro o destro da allineare al centro la posizione all'interno del triangolo di ridimensionamento.
    * Il **afferrare asse a destra dell'orientamento**: Quando si apre completamente la mano per formare una posa flat con un dito di 5, il raggio è normale che palm (in avanti dal palmo a sinistra, con le versioni precedenti dal palmo a destra)
    * Il **afferrare asse diretta dell'orientamento**: Quando si chiude la mano parzialmente (come se che contiene il controller), il raggio che punta "forward" tramite il tubo costituita dalle dita non thumb.
    * Il **afferrare orientamento di asse**: L'asse verticale in cui è inclusa per le definizioni di destra e l'inoltro.
    * È possibile accedere posa il triangolo di ridimensionamento tramite l'API di input tra fornitori entrambi di Unity (**[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o tramite l'API di Windows specifico (**sourceState.sourcePose.TryGetPosition/Rotation**, che richiede la posa triangolo).
* Il **posa puntatore**, che rappresenta la punta del controller in avanti che punta.
    * Questo posa è particolarmente utile per raycast quando **che punta all'interfaccia utente** quando si esegue il rendering di modello controller stesso.
    * Posa il puntatore è attualmente disponibile solo tramite l'API di Windows specifico (**sourceState.sourcePose.TryGetPosition/Rotation**, che richiede la posa puntatore).

Questi posa le coordinate sono espresse in coordinate complessive di Unity.

## <a name="see-also"></a>Vedere anche
* [Controller di movimento](motion-controllers.md)
* [I movimenti e i controller di movimento in Unity](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Porting di guide](porting-guides.md)
