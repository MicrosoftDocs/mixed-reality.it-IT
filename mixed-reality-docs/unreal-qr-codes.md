---
title: Codici a matrice in Unreal
description: Guida all'uso dei codici a matrice in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, codici a matrice
ms.openlocfilehash: cf6c113f6bf4a13a96f46d6420a3093966455c3b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720387"
---
# <a name="qr-codes-in-unreal"></a>Codici a matrice in Unreal

## <a name="overview"></a>Panoramica

HoloLens 2 può individuare i codici a matrice in uno spazio del mondo reale usando la webcam, eseguendone il rendering come ologrammi mediante un sistema di coordinate nella posizione reale di ciascun nodo.  Oltre ai singoli codici a matrice, HoloLens 2 è in grado di eseguire il rendering degli ologrammi nella stessa posizione su più dispositivi per creare un'esperienza condivisa. Assicurati di seguire le procedure consigliate per l'aggiunta di codici a matrice alle tue applicazioni:

- Zone silenziose
- Illuminazione e sfondo
- Dimensione, distanza e posizione angolare

Presta particolare attenzione alle [considerazioni sull'ambiente](environment-considerations-for-hololens.md) quando vengono inseriti codici a matrice nell'app. Per altre informazioni su questi argomenti e per istruzioni su come scaricare il pacchetto NuGet necessario, vedi il documento principale [Rilevamento di codici a matrice](qr-code-tracking.md). 

## <a name="enabling-qr-detection"></a>Abilitazione del rilevamento di codici a matrice
Dato che HoloLens 2 deve usare la webcam per visualizzare i codici a matrice, è necessario abilitarla nelle impostazioni del progetto:
- Apri **Edit > Project Settings** (Modifica > Impostazioni progetto), scorri fino alla sezione **Platforms** (Piattaforme) e fai clic su **HoloLens**.
    + Espandi la sezione **Capabilities** (Funzionalità) e seleziona **Webcam**.  

Devi anche acconsentire esplicitamente al rilevamento dei codici a matrice [aggiungendo un asset ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

## <a name="setting-up-a-tracked-image"></a>Configurazione di un'immagine rilevata

I codici a matrice vengono esposti tramite il sistema di geometria rilevata AR di Unreal come immagine rilevata. Per procedere, è necessario:
1. Creare un progetto e aggiungere un componente **ARTrackableNotify**.

![Codice a matrice - AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Selezionare **ARTrackableNotify** ed espandere la sezione **Events** (Eventi) nel pannello **Details** (Dettagli). 

![Eventi dei codici a matrice](images/unreal-spatialmapping-events.PNG)

3. Fare clic su **+** accanto a **On Add Tracked Geometry** (All'aggiunta della geometria rilevata) per aggiungere il nodo in Event Graph (Grafico eventi).
    - L'elenco completo degli eventi è disponibile nell'API del componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

![Esempio di rendering dei codici a matrice](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a>Uso di un'immagine rilevata
Il grafico degli eventi nell'immagine seguente mostra l'evento **OnUpdateTrackedImage** usato per eseguire il rendering di un punto al centro di un codice a matrice e stamparne i dati. 

![Esempio di rendering dei codici a matrice](images/unreal-qr-render.PNG)

Ecco cosa accade:
1. Prima di tutto, viene eseguito il cast dell'immagine rilevata in un codice **ARTrackedQRCode** per verificare che l'immagine aggiornata corrente sia un codice a matrice.  
2. I dati codificati vengono recuperati dalla variabile **QRCode**. È possibile ottenere la parte superiore sinistra del codice a matrice dalla posizione di **GetLocalToWorldTransform** e le dimensioni con **GetEstimateSize**. 

È anche possibile [ottenere il sistema di coordinate per un codice a matrice](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) nel codice.

## <a name="finding-the-unique-id"></a>Ricerca dell'ID univoco
Ogni codice a matrice ha un ID GUID univoco. Per trovarlo:
- Trascina e rilascia il segnaposto **As ARTracked QRCode** e cerca **Get Unique ID** (Ottieni ID univoco).

![GUID dei codici a matrice](images/unreal-qr-guid.PNG)

Le operazioni sui codici a matrice sono piuttosto complesse, quindi ci sono diversi aspetti da approfondire. I collegamenti riportati di seguito consentono di accedere a informazioni più dettagliate a questo proposito.

## <a name="see-also"></a>Vedere anche
* [Mapping spaziale](spatial-mapping.md)
* [Ologrammi](hologram.md)
* [Sistemi di coordinate](coordinate-systems.md)