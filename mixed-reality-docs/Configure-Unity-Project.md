---
title: Configurare un nuovo progetto Unity per realtà mista di Windows
description: configurare il progetto Unity senza MRTK
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mista realtà, sviluppo, operazioni preliminari, nuovo progetto
ms.openlocfilehash: aad38474781fd78425d48034877122d36d9e3e93
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2019
ms.locfileid: "65940758"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configurare un nuovo progetto Unity per realtà mista di Windows 

(ignorare se sono già stati importati MRTK v2 nel progetto Unity)

Se si vuole creare un nuovo progetto Unity senza importare Toolkit di realtà mista, sono disponibili un piccolo set di impostazioni di Unity, è necessario modificare manualmente per realtà mista di Windows, suddivise in due categorie: al progetto e per ogni scena.

## <a name="per-project-settings"></a>Impostazioni per ogni progetto

Per impostare come destinazione la realtà mista di Windows, è necessario innanzitutto impostare il progetto di Unity per l'esportazione come app Universal Windows Platform:
1. Selezionare **File > Impostazioni di compilazione...**
2. Selezionare **Universal Windows Platform** nella piattaforma di elenco e fare clic su **commutatore piattaforma**
3. Impostare **SDK** a **10 universali**
4. Impostare **dispositivo di destinazione** al **qualsiasi dispositivo** supportano auricolari immersive o passare a **HoloLens**
5. Impostare **tipo di compilazione** a **D3D**
6. Impostare **UWP SDK** a **installata più recente**

È quindi necessario informare Unity che deve creare l'app è in corso per esportare un' [vista immersiva](app-views.md) invece di una visualizzazione 2D. Ciò è possibile abilitare "Supportata di realtà virtuale":
1. Dal **le impostazioni di compilazione...**  finestra, aprire **le impostazioni del giocatore...**
2. Selezionare il **le impostazioni per la Universal Windows Platform** scheda
3. Espandere la **XR impostazioni** gruppo
4. Nel **impostazioni XR** sezione, verificare il **realtà virtuale supportato** casella di controllo per aggiungere il **dispositivi per realtà virtuale** elenco.
5. Nel **impostazioni XR** gruppo, verificare che **"Windows Mixed Reality"** viene elencato come un dispositivo supportato. (questa verifica può sembrare come "Windows Holographic" nelle versioni precedenti di Unity)

![Impostazioni di qualità di Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Impostazioni di Unity xr*

L'app ora è possibile eseguire spaziali input e base per il rendering holographic. Per andare oltre e sfruttare alcune funzionalità, l'app deve dichiarare le funzionalità appropriate nel relativo manifesto. Le dichiarazioni del manifesto possono essere rese Unity in modo che vengono inclusi in ogni esportazione progetto successivo. L'impostazione si trovano **Player Settings > impostazioni per la Universal Windows Platform > Impostazioni di pubblicazione > funzionalità**. Le funzionalità applicabili per l'abilitazione di uso comune le API di Unity per realtà mista sono:

|  Capability  |  API che richiedono funzionalità | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (accedere al [mapping spaziale](spatial-mapping.md) trame in HoloLens)&mdash;*alcuna funzionalità necessarie per rilevamento spaziale generale delle cuffie* | 
|  WebCam  |  PhotoCapture e VideoCapture | 
|  PicturesLibrary o VideosLibrary  |  PhotoCapture o VideoCapture, rispettivamente (quando si archiviano il contenuto acquisito) | 
|  Microfono  |  VideoCapture (durante l'acquisizione audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e usare il Profiler di Unity) | 

**Impostazioni di qualità di Unity**

![Impostazioni di qualità di Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Impostazioni di qualità di Unity*

HoloLens ha una GPU di classi di dispositivi mobili. Se l'app è destinata a HoloLens, è opportuno le impostazioni di qualità ottimizzate per prestazioni più veloci per garantire che manteniamo framerate completo:
1. Selezionare **Modifica > impostazioni del progetto > qualità**
2. Selezionare il **elenco a discesa** sotto il **Windows Store** logo e selezionare **molto bassa**. È quindi possibile sapere l'impostazione viene applicata in modo corretto quando la casella nella colonna di Windows Store e **molto bassa** riga è di colore verde.

## <a name="per-scene-settings"></a>Impostazioni per ogni scena

**Impostazioni videocamera di Unity**

![Impostazioni videocamera di Unity](images/Unitycamerasettings.png)<br>
*Impostazioni videocamera di Unity*

Dopo aver abilitato la casella di controllo "Realtà virtuale supportati", il [fotocamera Unity](camera-in-unity.md) componente gestisce [head rilevamento e il rendering stereoscopico](rendering.md). Non è necessario sostituirlo con una fotocamera personalizzata per eseguire questa operazione.

Se l'app è destinata a HoloLens in particolare, esistono alcune impostazioni che devono essere modificati per ottimizzare le visualizzazioni trasparente del dispositivo, in modo che l'app sarà visibile attraverso al mondo fisico:
1. Nel **gerarchia**, selezionare il **Main Camera**
2. Nel **Inspector** panel, impostare la trasformazione **posizione** al **0, 0, 0** in modo che la posizione di inizio utenti inizia in corrispondenza dell'origine mondo di Unity.
3. Change **cancellare i flag** al **colore a tinta unita**.
4. Modifica il **sfondo** colore **RGBA 0,0,0,0**. Nero esegue il rendering come trasparente nell'HoloLens.
5. Change **ritaglio piani - quasi** per il [HoloLens consigliato](camera-in-unity.md#clip-planes) 0,85 (metri).

Se si elimina e crea una nuova fotocamera, assicurarsi che sia la fotocamera **tag** come **MainCamera**.


## <a name="see-also"></a>Vedere anche
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Panoramica sullo sviluppo per Unity](unity-development-overview.md)
