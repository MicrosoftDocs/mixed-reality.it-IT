---
title: Fotocamera in Unity
description: Come usare lo sviluppo di Unity Main Camera per realtà mista di Windows per eseguire il rendering holographic
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, rendering holographic, punto holographic, coinvolgenti, lo stato attivo, buffer di profondità, orientamento, posizionali, opachi e trasparente, clip
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597782"
---
# <a name="camera-in-unity"></a>Fotocamera in Unity

Quando si wear un visore VR realtà mista, diventa il centro del tuo mondo holographic. Unity [fotocamera](http://docs.unity3d.com/Manual/class-Camera.html) componente gestirà automaticamente il rendering stereoscopico e seguirà il movimento della testina e rotazione quando il progetto contiene "Virtuale realtà supportata" selezionata con "Windows Mixed Reality" del dispositivo (in la sezione altre impostazioni delle impostazioni di Windows Store Windows Media Player). Questo potrebbe essere elencato come "Windows Holographic" nelle versioni precedenti di Unity.

Tuttavia, per completare l'ottimizzazione di una qualità visiva e [stabilità ologrammi](hologram-stability.md), è necessario impostare le impostazioni di fotocamera descritte di seguito.

>[!NOTE]
>Queste impostazioni devono essere applicato alla fotocamera in ogni scena della tua app.
>
>Per impostazione predefinita, quando si crea una nuova scena in Unity, conterrà un GameObject fotocamera principale della gerarchia che include il componente della fotocamera, ma non ha le impostazioni di seguito applicato correttamente.

## <a name="holographic-vs-immersive-headsets"></a>Holographic e auricolari coinvolgenti

Le impostazioni predefinite del componente della fotocamera Unity sono per le applicazioni 3D tradizionali che necessitano di uno sfondo skybox simile perché non prevedono un mondo reale.
* Durante l'esecuzione in un  **[visore VR immersivi](immersive-headset-hardware-details.md)**, si esegue il rendering tutto ciò che l'utente vede e sarà probabilmente opportuno mantenere la skybox.
* Tuttavia, durante l'esecuzione in un **visore VR holographic** , ad esempio [HoloLens](hololens-hardware-details.md), del mondo reale deve essere visualizzato dietro a tutti gli elementi della fotocamera esegue il rendering. A tale scopo, impostare lo sfondo della fotocamera Transparent (in HoloLens, nero esegue il rendering come trasparente) invece di una trama Skybox:
    1. Seleziona la fotocamera principale nel Pannello di gerarchia
    2. Nel Pannello di controllo, trovare il componente della fotocamera e modificare l'elenco a discesa Cancella flag da Skybox colore a tinta unita
    3. Selezionare il selettore di colore di sfondo e modificare i valori RGBA (0, 0, 0, 0)

È possibile usare il codice di script per determinare in fase di esecuzione se le cuffie sono immersive o holographic controllando [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).


## <a name="positioning-the-camera"></a>Il posizionamento della fotocamera

Sarà più facile preparare l'app se si immagina la posizione iniziale dell'utente come (x: 0, Y: 0, Z: 0). Poiché la fotocamera principale è rilevamento movimento della testina dell'utente, è possibile impostare la posizione iniziale dell'utente, impostare la posizione iniziale della fotocamera principale.
1. Seleziona Main Camera nel Pannello di gerarchia
2. Nel Pannello di controllo, trovare il componente di trasformazione e modificare la posizione da (x: 0, Y: Z 1,: -10) a (x: 0, Y: 0, Z: 0)

   ![Fotocamera nel riquadro di controllo in Unity](images/maincamera-350px.png)<br>
   *Fotocamera nel riquadro di controllo in Unity*

## <a name="clip-planes"></a>Piani di ritaglio

Il rendering del contenuto troppo vicini l'utente può essere spiacevole nella realtà mista. È possibile modificare il [vicino e lontano piani di ritaglio](hologram-stability.md#hologram-render-distances) nel componente della fotocamera.
1. Seleziona la fotocamera principale nel Pannello di gerarchia
2. Nel Pannello di controllo, trovare i piani di ritaglio componente fotocamera e modificare la casella di testo quasi da 0,3 a.85. Il contenuto sottoposto a rendering ancora più vicino può causare disturbo utente dovrebbe essere evitata, il [eseguire il rendering di linee guida per la distanza](hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Più videocamere

Quando sono presenti più componenti di fotocamera nella scena, Unity conosce la fotocamera da usare per il rendering stereoscopico e rilevamento head controllando quali GameObject con il tag MainCamera.

## <a name="recentering-a-seated-experience"></a>Recentering un'esperienza seduta

Se si sta creando un [esperienza su scala seduto](coordinate-systems.md), è possibile origine mondo di Unity centrare di nuovo nella posizione head corrente dell'utente chiamando il **[XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** (metodo).

## <a name="reprojection-modes"></a>Modalità reprojection

HoloLens sia auricolari immersive verranno reproject ogni fotogramma l'app esegue il rendering in modo che qualsiasi soddisfare della posizione head effettivo dell'utente quando vengono generati fotoni.

Per impostazione predefinita:

* **Auricolari immersive** eseguirà reprojection posizionali, modificando il vntana per soddisfare in posizione e l'orientamento, se l'app fornisce un buffer di profondità per un determinato intervallo.  Se non viene fornito un buffer di profondità, il sistema si risolve solo mispredictions orientamento.
* **Auricolari holographic** come HoloLens eseguirà reprojection posizionali se l'app fornisce il buffer di profondità o No.  Come per il rendering è spesso di tipo sparsa con uno sfondo stabile fornito dal mondo reale, è possibile senza buffer di intensità su HoloLens reprojection posizionale.

Se si sa che si sta compilando un' [esperienza solo orientamento](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) con contenuto rigidamente bloccato corpo (contenuto video, ad esempio a 360 gradi), è possibile impostare in modo esplicito la modalità reprojection sia l'orientamento solo impostando [ HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) al [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Condividere i buffer di profondità con Windows

La condivisione di buffer di profondità dell'app da Windows ogni fotogramma fornirà l'app una delle due degli incrementi della stabilità ologrammi, in base al tipo di visore VR si esegue il rendering per:
* **Auricolari immersive** eseguibili reprojection posizionali quando viene fornito un buffer di profondità, la regolazione di vntana per soddisfare in posizione e l'orientamento.
* **Holographic auricolari** , ad esempio HoloLens selezionerà automaticamente un [concentrarsi punto](focus-point-in-unity.md) quando viene fornito un buffer di profondità, ottimizzazione della stabilità ologrammi lungo il piano che si interseca la maggior parte del contenuto.

Per specificare se l'app Unity fornirà un buffer di profondità per Windows:
1. Passare a **Edit** > **impostazioni del progetto** > **Player** > **scheda Universal Windows Platform**  >  **XR impostazioni**.
2. Espandere la **Windows SDK di realtà mista** elemento.
3. Selezionare o deselezionare i **abilitare la condivisione di Buffer profondità** casella di controllo.  Ciò verrà verificato per impostazione predefinita nei nuovi progetti creati dal momento che questa funzionalità è stata aggiunta a Unity e verrà deselezionata per impostazione predefinita per i progetti meno recenti che sono stati aggiornati.

Che fornisce un buffer di profondità per Windows può migliorare qualità visiva, purché Windows può in modo accurato il mapping i valori della profondità normalizzata per ogni pixel nel buffer di profondità a distanza in metri, usando i piani di vicini e lontano che sono impostati in Unity nella fotocamera principale.  Se il rendering passa l'handle di profondità valori in modi tipici, è consigliabile in genere eseguire qui, anche se rendering semitrasparente passa che scrivono nel buffer di profondità durante la visualizzazione esistente pixel dal colore possono confondere il reprojection.  Se si sa che i passaggi di rendering lascia molti del pixel finale profondità con valori imprecisi profondità, probabile che ottenere una qualità visiva superiore condividendo deselezionando"abilitare la profondità del Buffer".

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>Programma di installazione automatica scena del Toolkit di realtà mista
Quando si importano [MRTK rilasciare pacchetti Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonare il progetto dal [repository di GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), si desidera trovare un nuovo menu 'Toolkit realtà mista' in Unity. Nel menu 'Configura', verrà visualizzato il menu 'Applica misto realtà scena impostazioni'. Quando si fa clic si, rimuove la fotocamera predefinita e aggiunge i componenti fondamentali - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menu MRTK per l'installazione di scena](images/MRTK_Input_Menu.png)<br>
*Menu MRTK per l'installazione di scena*

![Programma di installazione automatica di scena in MRTK](images/MRTK_HowTo_Input1.png)<br>
*Programma di installazione automatica di scena in MRTK*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefab
È possibile aggiungere anche manualmente queste informazioni dal Pannello di progetto. È possibile trovare questi componenti come prefabs. Quando si cercano **MixedRealityCamera**, sarà possibile visualizzare due diversi fotocamera prefabs. È, la differenza **MixedRealityCamera** è la fotocamera solo prefab mentre **MixedRealityCameraParent** include i componenti aggiuntivi per le cuffie coinvolgente e concreto, ad esempio teletrasporto, movimento Controller e limiti.

![Fotocamera prefab nel MRTK](images/MRTK_HowTo_Input2.png)<br>
*Fotocamera prefab nel MRTK*

**MixedRealtyCamera** supporta visore VR immersivi e HoloLens. Rileva il tipo di dispositivo e consente di ottimizzare le proprietà, ad esempio cancella i flag e Skybox. Di seguito è possibile trovare alcune delle proprietà più utili è possibile personalizzare, ad esempio un cursore personalizzato, i modelli di Controller di movimento e Floor.

![Proprietà per il controller di movimento, cursore e Floor](images/MRTK_HowTo_Input3.png)<br>
*Proprietà per il controller di movimento, cursore e Floor*

## <a name="see-also"></a>Vedere anche
* [Stabilità ologrammi](hologram-stability.md)
* [MixedRealityToolkit Main Camera.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
