---
title: Configurare un nuovo progetto Unity per la realtà mista di Windows
description: configurare il progetto Unity senza MRTK
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto
ms.openlocfilehash: 99c72f2d9d900c8a05fb7d8b9b8de10d657fdd13
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502652"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configurare un nuovo progetto Unity per la realtà mista di Windows 

(ignorare se MRTK V2 è già stato importato nel progetto Unity)

Se si vuole creare un nuovo progetto Unity senza importare il Toolkit di realtà mista, è necessario modificare manualmente le impostazioni di Unity per la realtà mista di Windows, suddivise in due categorie: per progetto e per scena.

## <a name="per-project-settings"></a>Impostazioni per progetto

Per fare riferimento alla realtà mista di Windows, è necessario prima di tutto impostare il progetto Unity per l'esportazione come app piattaforma UWP (Universal Windows Platform): 
1. Seleziona **File > impostazioni di compilazione...**
2. Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e fare clic su **Cambia piattaforma**
3. Impostare **SDK** su **Universal 10**
4. Impostare il **dispositivo di destinazione** su **qualsiasi dispositivo** per supportare auricolari immersivi o passare a **HoloLens**
5. Imposta **tipo di compilazione** su **D3D**
6. Impostare **UWP SDK** sull' **ultima versione installata**

È quindi necessario informare Unity che l'app che si sta tentando di esportare deve creare una [visualizzazione immersiva](app-views.md) anziché una visualizzazione 2D. A tale scopo, abilitare "Virtual Reality supported":
1. Dalla finestra **impostazioni di compilazione...** aprire **lettore impostazioni...**
2. Selezionare le **impostazioni per** la scheda piattaforma UWP (Universal Windows Platform)
3. Espandere il gruppo di **impostazioni di XR**
4. Nella sezione **impostazioni di XR** , selezionare la casella di controllo **realtà virtuale supportata** per aggiungere l'elenco **dispositivi della realtà virtuale** .
5. Nel gruppo **impostazioni di XR** verificare che **"realtà mista di Windows"** sia elencato come un dispositivo supportato. (questo può apparire come "Windows olografico" nelle versioni precedenti di Unity)

impostazioni della qualità di ![Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Impostazioni di Unity XR*

L'app ora può eseguire il rendering olografico di base e l'input spaziale. Per approfondire e sfruttare alcune funzionalità, l'app deve dichiarare le funzionalità appropriate nel manifesto. Le dichiarazioni di manifesto possono essere apportate in Unity, in modo che vengano incluse in ogni esportazione successiva del progetto. Le impostazioni sono disponibili in **Impostazioni lettore > impostazioni per piattaforma UWP (Universal Windows Platform) > impostazioni di pubblicazione > funzionalità**. Le funzionalità applicabili per l'abilitazione di API Unity utilizzate comunemente per la realtà mista sono:

|  Capability  |  API che richiedono funzionalità | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (accesso ai mesh di [mapping spaziale](spatial-mapping.md) in HoloLens)&mdash;*Nessuna funzionalità necessaria per il rilevamento spaziale generale dell'auricolare* | 
|  WebCam  |  Acquisizione e VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  Fotocapture o VideoCapture, rispettivamente (quando si archivia il contenuto acquisito) | 
|  Microfono  |  VideoCapture (durante l'acquisizione dell'audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e per usare Unity Profiler) | 

**Impostazioni qualità Unity**

impostazioni della qualità di ![Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Impostazioni qualità Unity*

HoloLens dispone di una GPU di classe mobile. Se l'app è destinata a HoloLens, è necessario ottimizzare le impostazioni di qualità per ottenere prestazioni più rapide, in modo da mantenere la frequenza di framerate completa:
1. Selezionare **modifica > impostazioni progetto > qualità**
2. Selezionare l' **elenco a discesa** sotto il logo di **Windows Store** e selezionare **molto basso**. Si saprà che l'impostazione viene applicata correttamente quando la casella nella colonna Windows Store e con **una riga molto bassa** è verde.

## <a name="per-scene-settings"></a>Impostazioni per scena

**Impostazioni della fotocamera Unity**

![impostazioni della fotocamera Unity](images/Unitycamerasettings.png)<br>
*Impostazioni della fotocamera Unity*

Una volta abilitata la casella di controllo "Virtual Reality supported", il componente della [fotocamera Unity](camera-in-unity.md) gestisce il [monitoraggio Head e il rendering stereoscopico](rendering.md). Per eseguire questa operazione, non è necessario sostituirlo con una fotocamera personalizzata.

Se l'app è destinata a HoloLens in modo specifico, è necessario modificare alcune impostazioni per ottimizzare le visualizzazioni trasparenti del dispositivo, in modo che l'app venga visualizzata nel mondo fisico:
1. Nella **gerarchia**selezionare la **fotocamera principale**
2. Nel pannello **Inspector** impostare la **posizione** di trasformazione su 0, 0 **, 0,** in modo che la posizione della testa dell'utente inizi in corrispondenza dell'origine mondiale di Unity.
3. Modificare i **flag cancellati** in **colore a tinta unita**.
4. Modificare il colore di **sfondo** in **RGBA 0**, 0, 0, 0. Il nero viene visualizzato come trasparente in HoloLens.
5. Modificare i **piani di ritaglio in prossimità** del [HoloLens consigliato](camera-in-unity.md#clip-planes) 0,85 (contatori).

Se si elimina e si crea una nuova fotocamera, assicurarsi che la fotocamera sia **contrassegnata** come **MainCamera**.


## <a name="see-also"></a>Vedi anche
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Panoramica sullo sviluppo Unity](unity-development-overview.md)
