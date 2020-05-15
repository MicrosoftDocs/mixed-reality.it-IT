---
title: Mapping spaziale in Unreal
description: Guida all'uso del mapping spaziale in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, mapping spaziale
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840080"
---
# <a name="spatial-mapping-in-unreal"></a>Mapping spaziale in Unreal

Per abilitare il mapping spaziale in HoloLens, verifica che la funzionalità "Percezione spaziale" sia selezionata nell'editor di Unreal in Impostazioni progetto > Piattaforma > HoloLens > Funzionalità.  

Per acconsentire esplicitamente all'uso del mapping spaziale in un gioco HoloLens, abilita "Generate Mesh Data from Tracked Geometry" (Genera dati mesh dalla geometria rilevata) in ARSessionConfig.  Il plug-in HoloLens otterrà quindi i dati di mapping spaziale in modo asincrono e li sottoporrà a Unreal attraverso MRMesh. 

![Archivio di ancoraggi nello spazio pronto](images/unreal-spatialmapping-arsettings.PNG)

Per aprire una visualizzazione di debug della mesh di mapping spaziale, abilita la casella di controllo "Render Mesh Data in Wireframe" (Rendering dei dati mesh in Wireframe) in ARSessionConfig, in modo da visualizzare una struttura di wireframe bianca di ogni triangolo in MRMesh. 

In Impostazioni progetto > Piattaforma > HoloLens > Mapping spaziale, è possibile modificare i parametri seguenti per aggiornare il comportamento di runtime del mapping spaziale: 

![Impostazioni del progetto di ancoraggi nello spazio](images/unreal-spatialmapping-projectsettings.PNG)

Il parametro Max Triangles Per Cubic Meter (Numero massimo di triangoli per metro cubo) aggiornerà la densità dei triangoli nella mesh di mapping spaziale.  Il parametro Spatial Meshing Volume Size (Dimensioni del volume della mesh spaziale) indica le dimensioni del cubo intorno al giocatore in cui poter eseguire il rendering e l'aggiornamento dei dati di mapping spaziale.  Se prevedi che l'ambiente di runtime dell'applicazione sia di grandi dimensioni, è possibile che questo valore debba essere elevato per poter corrispondere allo spazio reale.  Se invece l'applicazione deve soltanto posizionare ologrammi sulle superfici immediatamente attorno all'utente, questo campo può essere più piccolo.  Il volume di mapping spaziale si sposterà quindi contestualmente all'utente. 

Per ottenere l'accesso a MRMesh in fase di esecuzione, aggiungi un componente AR Trackable Notify a un attore del progetto: 

![Ancoraggi nello spazio AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

Passa quindi ai dettagli del componente e fai clic sul pulsante verde "+" per selezionare gli eventi da monitorare. 

![Eventi sugli ancoraggi nello spazio](images/unreal-spatialmapping-events.PNG)

In questo caso viene monitorato l'evento On Add Tracked Geometry, con sui si cercano le mesh globali valide corrispondenti ai dati di mapping spaziale, e viene modificato il materiale della mesh: 

![Esempi di ancoraggi nello spazio](images/unreal-spatialmapping-example.PNG)

In C++ è possibile sottoscrivere il delegato OnTrackableAdded per ottenere ARTrackedGeometry non appena risulta disponibile.  Sono presenti delegati simili per gli eventi aggiornati e rimossi: AddOnTrackableUpdatedDelegate_Handle e AddOnTrackableRemovedDelegate_Handle. 

![Esempio di ancoraggi nello spazio in codice C++](images/unreal-spatialmapping-examplecode.PNG)

Il file build.cs del progetto deve contenere "AugmentedReality" nell'elenco PublicDependencyModuleNames in modo da includere "ARBlueprintLibrary.h" e "MRMesh" per l'ispezione del componente MRMesh di UARTrackedGeometry. 

Il mapping spaziale non è l'unico tipo di dati presentato tramite ARTrackedGeometries ed è quindi necessario verificare in primo luogo che EARObjectClassification sia impostato su World, in modo da indicare che si tratta di geometria di mapping spaziale. 

## <a name="see-also"></a>Vedere anche
* [Mapping spaziale](spatial-mapping.md)
