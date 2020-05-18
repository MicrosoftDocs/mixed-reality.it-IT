---
title: Codici a matrice in Unreal
description: Guida all'uso dei codici a matrice in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, codici a matrice
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342659"
---
# <a name="qr-codes-in-unreal"></a>Codici a matrice in Unreal

HoloLens può individuare i codici a matrice in uno spazio del mondo reale per il rendering degli ologrammi in posizioni note del mondo reale.  Questi codici possono essere usati anche per eseguire il rendering degli ologrammi su più dispositivi nella stessa posizione, in modo da creare un'esperienza condivisa. 

Per abilitare il rilevamento a matrice in HoloLens, verifica che la funzionalità Webcam sia selezionata nell'editor di Unreal in Project Settings > Platform > HoloLens > Capabilities (Impostazioni progetto > Piattaforma > HoloLens > Funzionalità).  

Puoi acconsentire esplicitamente all'uso del rilevamento dei codici a matrice in Unreal avviando ARSession con la funzione StartARSession. 

I codici a matrice vengono esposti tramite il sistema di geometria rilevata AR di Unreal come immagine rilevata.  Per usare questo sistema, aggiungi un componente AR Trackable Notify a un attore del progetto: 

![Codice a matrice - AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

Passa quindi ai dettagli del componente e fai clic sul pulsante verde "+" per selezionare gli eventi da monitorare.  

![Eventi dei codici a matrice](images/unreal-spatialmapping-events.PNG)

In questo esempio, abbiamo effettuato la sottoscrizione a OnUpdateTrackedImage per eseguire il rendering di un punto al centro di un codice a matrice e stampare i dati codificati del codice a matrice. 

![Esempio di rendering dei codici a matrice](images/unreal-qr-render.PNG)

Esegui innanzitutto il cast dell'immagine rilevata in un codice ARTrackedQRCode, per verificare che l'immagine aggiornata corrente sia un codice a matrice.  I dati codificati possono quindi essere recuperati con la variabile QRCode.  La parte superiore sinistra del codice a matrice può essere recuperata dalla posizione di GetLocalToWorldTransform.  Le dimensioni possono essere recuperate con GetEstimateSize. 

Ogni codice a matrice ha anche un ID GUID univoco: 

![GUID dei codici a matrice](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>Vedere anche
* [Rilevamento di codici a matrice](qr-code-tracking.md)
