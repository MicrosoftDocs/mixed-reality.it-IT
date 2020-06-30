---
title: Mapping spaziale in Unreal
description: Guida all'uso del mapping spaziale in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, mapping spaziale
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720407"
---
# <a name="spatial-mapping-in-unreal"></a>Mapping spaziale in Unreal

## <a name="overview"></a>Panoramica
Il mapping spaziale consente di posizionare oggetti sulle superfici reali visualizzando l'ambiente intorno a HoloLens, rendendo gli ologrammi più realistici per l'utente. Il mapping spaziale consente anche di ancorare gli oggetti nel mondo dell'utente sfruttando i segnali di profondità del mondo reale. In questo modo l'utente avrà l'impressione che questi ologrammi si trovino effettivamente nello spazio che lo circonda; gli ologrammi che fluttuano nello spazio o che si muovono insieme all'utente non vengono percepiti come reali. È consigliabile inserire elementi di comfort, quando possibile.

Per altre informazioni su qualità del mapping spaziale, posizionamento, occlusione, rendering e così via, consulta il documento [Mapping spaziale](spatial-mapping.md).

## <a name="enabling-spatial-mapping"></a>Abilitazione del mapping spaziale

Per abilitare il mapping spaziale in HoloLens:
- Apri **Edit > Project Settings** (Modifica > Impostazioni progetto) e scorri fino alla sezione **Platforms** (Piattaforme).    
    + Seleziona **HoloLens** e **Spatial Perception** (Percezione spaziale).

Per acconsentire esplicitamente al mapping spaziale ed eseguire il debug di **MRMesh** in un gioco HoloLens:
1. Apri **ARSessionConfig** ed espandi la sezione **ARSettings > World Mapping** (ARSettings > Mapping mondo). 

2. Seleziona **Generate Mesh Data from Tracked Geometry** (Genera dati mesh da geometria rilevata), che indica al plug-in di HoloLens di avviare l'acquisizione asincrona dei dati di mapping spaziale e presentarli ad Unreal tramite **MRMesh**. 
3. Seleziona **Render Mesh Data in Wireframe** (Esegui il rendering dei dati mesh in wireframe) per visualizzare un contorno wireframe bianco di ogni triangolo in **MRMesh**. 

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Mapping spaziale in fase di runtime
Puoi modificare i parametri seguenti per aggiornare il comportamento di runtime del mapping spaziale:

- Apri **Edit > Project Settings** (Modifica > Impostazioni progetto), scorri verso il basso fino alla sezione **Platforms** (Piattaforme) e seleziona **HoloLens > Spatial Mapping** (HoloLens > Mapping spaziale): 

![Impostazioni del progetto di ancoraggi nello spazio](images/unreal-spatialmapping-projectsettings.PNG)

- Il parametro **Max Triangles Per Cubic Meter** (Numero massimo di triangoli per metro cubo) aggiorna la densità dei triangoli nella mesh di mapping spaziale.  
- Il parametro **Spatial Meshing Volume Size** (Dimensioni del volume della mesh spaziale) indica le dimensioni del cubo intorno al giocatore per il rendering e l'aggiornamento dei dati di mapping spaziale.  
    + Se prevedi che l'ambiente di runtime dell'applicazione sia di grandi dimensioni, è possibile che questo valore debba essere elevato per poter corrispondere allo spazio reale.  Viceversa, questo valore può essere più piccolo se l'applicazione deve soltanto posizionare ologrammi sulle superfici immediatamente attorno all'utente. Il volume di mapping spaziale si sposterà quindi contestualmente all'utente. 

## <a name="working-with-mrmesh"></a>Uso di MRMesh
Per ottenere l'accesso a **MRMesh** in fase di runtime:
1. Aggiungi un componente **ARTrackableNotify** a un attore del progetto. 

![Ancoraggi nello spazio AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Seleziona il componente **ARTrackableNotify** ed spandi la sezione **Events** (Events) nel pannello **Details** (Dettagli). 
    - Fai clic sul pulsante **+** sugli eventi da monitorare. 

![Eventi sugli ancoraggi nello spazio](images/unreal-spatialmapping-events.PNG)

In questo caso viene monitorato l'evento **On Add Tracked Geometry** (All'aggiunta della geometria rilevata), che cerca mesh reali valide corrispondenti ai dati del mapping spaziale. L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Il materiale della mesh può essere modificato nel grafico eventi del progetto o in C++. Nello screenshot seguente è mostrato il percorso del progetto: 

![Esempi di ancoraggi nello spazio](images/unreal-spatialmapping-example.PNG)

In C++ è possibile sottoscrivere il delegato `OnTrackableAdded` per ottenere `ARTrackedGeometry` non appena è disponibile, come mostrato nel codice seguente. 

> [!IMPORTANT]
> Il file build.cs del progetto **DEVE** includere **AugmentedReality** nell'elenco **PublicDependencyModuleNames**.
> - Questo comprende **ARBlueprintLibrary.h** e **MRMeshComponent.h**, che consente di ispezionare il componente **MRMesh** di **UARTrackedGeometry**. 

![Esempio di ancoraggi nello spazio in codice C++](images/unreal-spatialmapping-examplecode.PNG)

Il mapping spaziale non è l'unico tipo di dati che viene esposto tramite **ARTrackedGeometries**. Puoi verificare che `EARObjectClassification` è `World`, che indica che si tratta di una geometria di mapping spaziale. 

Sono presenti delegati simili per gli eventi aggiornati e rimossi: 
- `AddOnTrackableUpdatedDelegate_Handle` 
- `AddOnTrackableRemovedDelegate_Handle`. 

L'elenco completo degli eventi è disponibile nell'API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>Vedere anche
* [Mapping spaziale](spatial-mapping.md)
