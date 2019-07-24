---
title: Guida al porting di input per Unity
description: Informazioni su come gestire l'input per la realtà mista di Windows in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: input, Unity, porting
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515489"
---
# <a name="input-porting-guide-for-unity"></a>Guida al porting di input per Unity

È possibile trasferire la logica di input in una realtà mista di Windows usando uno dei due approcci, le API input. GetButton/getaxis di Unity che si estendono su più piattaforme o la XR specifica di Windows. WSA. API di input che offrono dati più ricchi in modo specifico per i controller di movimento e le HoloLens.

## <a name="general-inputgetbuttongetaxis-apis"></a>Input generale. GetButton/API getaxis

Unity usa attualmente le API input. GetButton/input. getasse generale per esporre l'input per [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) e [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html). Se le app usano già queste API per l'input, questo è il percorso più semplice per supportare i controller di movimento in realtà mista di Windows: è necessario solo modificare il mapping di pulsanti e assi nel gestore di input.

Per altre informazioni, vedere la [tabella di mapping degli assi](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) e dei pulsanti di Unity e la [Panoramica delle API comuni di Unity](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR specifico di Windows. WSA. API di input

Se l'app crea già una logica di input personalizzata per ogni piattaforma, è possibile scegliere di usare le API di input spaziali specifiche di Windows nello spazio dei nomi **UnityEngine. XR. WSA. input** . In questo modo è possibile accedere a informazioni aggiuntive, ad esempio l'accuratezza della posizione o il tipo di origine, consentendo di comunicare le mani e i controller a HoloLens.

Per altre informazioni, vedere la [Panoramica delle API UnityEngine. XR. WSA. input](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Posa del grip e puntamento

La realtà mista di Windows supporta i controller di movimento in diversi fattori di forma, con la progettazione di ogni controller diversa nella relazione tra la posizione della mano dell'utente e la direzione naturale "Avanti" che le app devono usare per puntare durante il rendering del controller.

Per rappresentare meglio questi controller, esistono due tipi di pose che è possibile esaminare per ogni origine interazione:

* La posizione del **grip**, che rappresenta la posizione della Palma di una mano rilevata da un HoloLens o della palma che contiene un controller di movimento.
    * Negli auricolari immersivi è consigliabile usare questa soluzione per eseguire **il rendering della mano dell'utente** o di **un oggetto contenuto nella mano**, ad esempio una spada o una pistola.
    * **Posizione del grip**: Centro della palma quando il controller viene tenuto in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del grip.
    * **Asse destro dell'orientamento del grip**: Quando si apre completamente la mano per formare una formula a 5 dita piatta, il raggio è normale per la Palma (in avanti dal palmo sinistro, indietro rispetto a destra)
    * **Asse di avanzamento dell'orientamento del grip**: Quando si chiude parzialmente la mano (come se si utilizzasse il controller), il raggio che punta "" in poi "attraverso il tubo formato dalle dita non Thumb.
    * **Asse verticale dell'orientamento del grip**: Asse verso l'alto implicito dalle definizioni di destra e di avanzamento.
    * È possibile accedere al grip con l'API di input tra fornitori di Unity ( **[XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o tramite l'API specifica di Windows (**SourceState. SourcePose. TryGetPosition/Rotation**, che richiede la richiesta della forma del grip).
* Il **puntatore**che rappresenta il suggerimento del controller che punta in poi.
    * Questa posizione è particolarmente utilizzata per Raycast quando si **punta all'interfaccia utente** quando si esegue il rendering del modello di controller.
    * Attualmente, la posa del puntatore è disponibile solo tramite l'API specifica di Windows (**sourceState. sourcePose. TryGetPosition/Rotation**, che richiede la posa del puntatore).

Queste coordinate di pose sono tutte espresse in coordinate internazionali di Unity.

## <a name="see-also"></a>Vedere anche
* [Controller del movimento](motion-controllers.md)
* [Movimenti e controller del movimento in Unity](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guide al porting](porting-guides.md)
