---
title: Fotocamera in Unity
description: Come usare la fotocamera principale di Unity per lo sviluppo di realtà mista di Windows per eseguire il rendering olografico
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, rendering olografico, olografico, immersivo, punto di messa a fuoco, buffer di profondità, solo orientamento, posizionale, opaco, trasparente, clip
ms.openlocfilehash: 1a2e66d5c028109a58ea8682668521f50158add9
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375588"
---
# <a name="camera-in-unity"></a>Fotocamera in Unity

Quando si usa una cuffia a realtà mista, diventa il centro del mondo olografico. Il componente della [fotocamera](https://docs.unity3d.com/Manual/class-Camera.html) Unity gestirà automaticamente il rendering stereoscopico e seguirà lo spostamento e la rotazione delle intestazioni quando il progetto ha selezionato "realtà virtuale supportata" con "realtà mista di Windows" come dispositivo (nella sezione altre impostazioni delle impostazioni di Windows Store Player). Questo può essere elencato come "Windows olografico" nelle versioni precedenti di Unity.

Tuttavia, per ottimizzare completamente la qualità visiva e la [stabilità dell'ologramma](hologram-stability.md), è necessario impostare le impostazioni della fotocamera descritte di seguito.

>[!NOTE]
>Queste impostazioni devono essere applicate alla fotocamera in ogni scena dell'app.
>
>Per impostazione predefinita, quando si crea una nuova scena in Unity, questa conterrà una fotocamera principale GameObject nella gerarchia che include il componente della fotocamera, ma le impostazioni non sono state applicate correttamente.

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a>Configurazione automatica della scena e della fotocamera con Mixed Reality toolkit V2

Seguire la Guida [dettagliata](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) per aggiungere Mixed Reality toolkit V2 al progetto Unity e il progetto verrà configurato automaticamente.

È anche possibile configurare manualmente il progetto senza MRTK con la guida nella sezione seguente.

## <a name="holographic-vs-immersive-headsets"></a>Cuffie olografiche rispetto a quelle immersive

Le impostazioni predefinite nel componente della fotocamera Unity sono per le applicazioni 3D tradizionali che necessitano di uno sfondo simile a skybox, perché non hanno un mondo reale.

* Quando si esegue un' **[auricolare immersiva](immersive-headset-hardware-details.md)** , si esegue il rendering di tutti gli elementi che l'utente vede, quindi è probabile che si desideri proteggere skybox.
* Tuttavia, quando si esegue un **auricolare olografico** come [HoloLens](hololens-hardware-details.md), il mondo reale dovrebbe apparire dietro tutto il rendering della fotocamera. A tale scopo, impostare lo sfondo della fotocamera come trasparente (in HoloLens, il nero viene visualizzato come trasparente) invece di una trama skybox:
    1. Selezionare la fotocamera principale nel pannello gerarchia
    2. Nel pannello Inspector trovare il componente della fotocamera e modificare l'elenco a discesa Clear Flags da skybox a Solid Color.
    3. Selezionare la selezione dei colori di sfondo e modificare i valori di RGBA in (0, 0, 0, 0)

È possibile usare il codice di script per determinare in fase di esecuzione se l'auricolare è immersiva o olografica controllando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).

## <a name="positioning-the-camera"></a>Posizionamento della fotocamera

Il layout dell'app sarà più semplice se si immagina la posizione iniziale dell'utente come (X: 0, Y: 0, Z: 0). Poiché la fotocamera principale tiene traccia del movimento della testa dell'utente, è possibile impostare la posizione iniziale dell'utente impostando la posizione iniziale della fotocamera principale.

1. Selezionare la fotocamera principale nel pannello gerarchia
2. Nel pannello Inspector trovare il componente Transform e modificare la posizione da (X: 0, Y: 1, Z:-10) a (X: 0, Y: 0, Z: 0)

   ![fotocamera nel riquadro Inspector in Unity](images/maincamera-350px.png)  
   *Fotocamera nel riquadro controllo in Unity*

## <a name="clip-planes"></a>Ritagliare i piani

Il rendering del contenuto troppo vicino all'utente può risultare scomodo in realtà mista. È possibile regolare i [piani di ritaglio vicini e lontani](hologram-stability.md#hologram-render-distances) sul componente della fotocamera.

1. Selezionare la fotocamera principale nel pannello gerarchia
2. Nel pannello Inspector trovare i piani di ritaglio dei componenti della fotocamera e modificare la casella di testo near da 0,3 a 85. Il rendering del contenuto ancora più vicino può causare disagi da parte dell'utente e deve essere evitato in base alle [linee guida di rendering](hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Più fotocamere

Quando nella scena sono presenti più componenti della fotocamera, Unity sa quale fotocamera usare per il rendering stereoscopico e il rilevamento Head controllando quale GameObject ha il tag MainCamera.

## <a name="recentering-a-seated-experience"></a>Ricentrare un'esperienza di seduta

Se si sta creando un' [esperienza a scalabilità verticale](coordinate-systems.md), è possibile ricentrare l'origine del mondo di Unity nella posizione Head corrente dell'utente chiamando **[XR. Metodo InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .

## <a name="reprojection-modes"></a>Modalità di riproiezione

Sia HoloLens che le cuffie immersive riproiettano ogni frame di cui l'app esegue il rendering per adattarsi a qualsiasi stima errata della posizione effettiva dell'utente quando vengono emessi i fotoni.

Per impostazione predefinita:

* Gli **auricolari immersivi** eseguiranno una riproiezione posizionale, modificando gli ologrammi per la stima errata nella posizione e nell'orientamento, se l'app fornisce un buffer di profondità per un determinato frame.  Se non viene fornito un buffer di profondità, il sistema correggerà solo le stime errate all'orientamento.
* Gli **auricolari olografici** come HoloLens eseguiranno la riproiezione posizionale se l'app fornisce o meno il buffer di profondità.  La riproiezione posizionale è possibile senza buffer di profondità su HoloLens perché il rendering è spesso di tipo sparse con uno sfondo stabile fornito dal mondo reale.

Se si è certi che si sta compilando un' [esperienza di solo orientamento](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) con contenuto con blocco del corpo rigido (ad esempio, il contenuto video di 360 gradi), è possibile impostare in modo esplicito la modalità di riprogettazione in modo che sia l'orientamento solo impostando [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) su [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Condivisione dei buffer di profondità con Windows

La condivisione del buffer di profondità dell'app in Windows ogni frame offrirà all'app uno dei due aumenti di stabilità dell'ologramma, in base al tipo di auricolare per cui si esegue il rendering:

* Gli **auricolari immersivi** possono eseguire la riproiezione posizionale quando viene fornito un buffer di profondità, regolando gli ologrammi per la stima errata nella posizione e nell'orientamento.
* Per gli **auricolari olografici** sono disponibili alcuni metodi diversi. HoloLens 1 seleziona automaticamente un [punto di interesse](focus-point-in-unity.md) quando viene fornito un buffer di profondità, ottimizzando la stabilità dell'ologramma lungo il piano che interseca la maggior parte del contenuto. HoloLens 2 stabilizza il contenuto usando [LSR di profondità (vedere la sezione Osservazioni)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

Per specificare se l'app Unity fornirà un buffer di profondità a Windows:

1. Passare a **modifica** > **Impostazioni progetto** > **lettore** > **scheda piattaforma UWP (Universal Windows Platform)**  > **XR impostazioni**.
2. Espandere l'elemento **SDK di realtà mista di Windows** .
3. Selezionare o deselezionare la casella di controllo **Abilita condivisione buffer di profondità** .  Questa opzione verrà controllata per impostazione predefinita nei nuovi progetti creati poiché questa funzionalità è stata aggiunta a Unity e verrà deselezionata per impostazione predefinita per i progetti precedenti aggiornati.

Fornire un buffer di profondità a Windows può migliorare la qualità visiva, purché Windows possa mappare accuratamente i valori di profondità per pixel normalizzati nel buffer di profondità a distanza in metri, usando i piani vicini e lontani impostati in Unity sulla fotocamera principale.  Se il rendering passa i valori di profondità di gestione in modi tipici, in genere è opportuno eseguire questa procedura, sebbene i passaggi di rendering traslucidi che scrivono nel buffer di profondità durante la visualizzazione dei pixel di colore esistenti possano confondere la riproiezione.  Se si è certi che i passaggi di rendering lasceranno molti dei pixel di profondità finali con valori di profondità non corretti, è probabile che si ottenga una qualità visiva migliore deselezionando "Abilita condivisione buffer di profondità".

## <a name="see-also"></a>Vedere anche

* [Stabilità degli ologrammi](hologram-stability.md)
* [MixedRealityToolkit fotocamera principale. prefabbricata](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
