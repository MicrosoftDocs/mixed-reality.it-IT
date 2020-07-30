---
title: Configurare un nuovo progetto Unity per la realtà mista di Windows
description: Istruzioni sulla configurazione di un progetto Unity per la realtà mista di Windows
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, realtà mista, sviluppo, Guida introduttiva, nuovo progetto
ms.openlocfilehash: 64f7006bf212f49ab1c478d5dbb1fc1f5ab15497
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390103"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configurare un nuovo progetto Unity per la realtà mista di Windows 

## <a name="overview"></a>Panoramica

La realtà mista di Windows (WMR) è una piattaforma Microsoft introdotta come parte del sistema operativo Windows 10. La piattaforma WMR consente di creare applicazioni che eseguono il rendering di contenuto digitale su dispositivi di visualizzazione olografici e VR.

Quando si configura per WMR, è possibile eseguire due percorsi. La prima opzione consiste nell'installare il [Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) (MRTK) V2, che configurerà automaticamente l'ambiente WMR. La seconda opzione consiste nel modificare manualmente alcune impostazioni di Unity in modo da ottenere il rollup con WMR. 

> [!NOTE]
> È sempre possibile importare MRTK in un secondo momento, quindi non è necessario prima di tutto procedere con la route manuale.

Se si sceglie l'installazione manuale di WMR, le impostazioni che è necessario modificare sono suddivise in due categorie: per progetto e per scena.

## <a name="per-project-settings"></a>Impostazioni per progetto

La prima impostazione che è necessario modificare per WMR è la piattaforma del progetto: 
1. Seleziona **File > impostazioni di compilazione...**
2. Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e fare clic su **Cambia piattaforma**
3. Impostare **SDK** su **Universal 10**
4. Impostare il **dispositivo di destinazione** su **qualsiasi dispositivo** per supportare auricolari immersivi o passare a **HoloLens**
5. Imposta **tipo di compilazione** su **D3D**
6. Impostare **UWP SDK** sull' **ultima versione installata**

![Impostazioni di Unity XR](images/unity-uwp-settings.png)<br>
*Impostazioni di Unity XR*

Quando la piattaforma è configurata correttamente, è necessario informare Unity che l'app deve creare una [visualizzazione immersiva](app-views.md) invece di una visualizzazione 2D quando viene esportata:
1. Dalla finestra **impostazioni di compilazione...** aprire **lettore impostazioni...**
2. Selezionare le **impostazioni per** la scheda piattaforma UWP (Universal Windows Platform) ed espandere il gruppo di **Impostazioni XR**
3. Nella sezione **impostazioni di XR** , selezionare la casella di controllo **realtà virtuale supportata** per aggiungere l'elenco **dispositivi della realtà virtuale** .
4. Nel gruppo **impostazioni di XR** verificare che **"realtà mista di Windows"** sia elencato come un dispositivo supportato. (questa opzione può apparire come **Windows olografico** nelle versioni precedenti di Unity)

![Impostazioni UWP Unity](images/xrsettings.png)<br>
*Impostazioni di Unity XR*

### <a name="updating-the-manifest"></a>Aggiornamento del manifesto

L'app ora può gestire il rendering olografico e l'input spaziale. Tuttavia, l'app deve dichiarare le funzionalità appropriate nel manifesto per sfruttare le funzionalità specifiche. È possibile trovare le funzionalità di progetto passando a **Impostazioni lettore > impostazioni per piattaforma UWP (Universal Windows Platform) > impostazioni di pubblicazione > funzionalità**. 

È consigliabile fare in modo che le dichiarazioni di manifesto in Unity vengano incluse in tutti i progetti futuri esportati. Le funzionalità applicabili per l'abilitazione di API Unity comunemente usate per la realtà mista sono:

|  Funzionalità  |  API che richiedono funzionalità | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (accesso ai mesh di [mapping spaziale](spatial-mapping.md) in HoloLens) &mdash; *Nessuna funzionalità necessaria per il rilevamento spaziale generale dell'auricolare* | 
|  WebCam  |  Acquisizione e VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  Fotocapture o VideoCapture, rispettivamente (quando si archivia il contenuto acquisito) | 
|  Microfono  |  VideoCapture (durante l'acquisizione dell'audio), DictationRecognizer, GrammarRecognizer e KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (e per usare Unity Profiler) | 

### <a name="quality-settings"></a>Impostazioni qualità

HoloLens dispone di una GPU di classe mobile. Se l'app è destinata a HoloLens, è possibile ottimizzare le impostazioni di qualità nell'app per ottenere prestazioni più rapide per garantire la massima frequenza dei fotogrammi:
1. Selezionare **modifica > impostazioni progetto > qualità**
2. Selezionare l' **elenco a discesa** sotto il logo di **Windows Store** e selezionare **molto basso**. Si saprà che l'impostazione è stata applicata in modo corretto quando la casella nella colonna Windows Store e la riga **Molto bassa** è di colore verde.

![Impostazioni qualità Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Impostazioni qualità Unity*

## <a name="per-scene-settings"></a>Impostazioni per scena

### <a name="unity-camera-settings"></a>Impostazioni della fotocamera Unity

Con la **realtà virtuale supportata** selezionata, il componente della [fotocamera Unity](camera-in-unity.md) gestisce il [rilevamento Head e il rendering stereoscopico](rendering.md). Ciò significa che non è necessario sostituire l'oggetto fotocamera principale con una fotocamera personalizzata.

Se l'app è destinata a HoloLens in modo specifico, è necessario modificare alcune impostazioni per ottimizzare la visualizzazione trasparente del dispositivo. Queste impostazioni consentono di visualizzare il contenuto olografico nel mondo fisico:
1. Nella **gerarchia**selezionare la **fotocamera principale**
2. Nel pannello **Inspector** impostare la **posizione** di trasformazione su 0, 0 **, 0,** in modo che la posizione della testa dell'utente inizi in corrispondenza dell'origine mondiale di Unity.
3. Modificare i **flag cancellati** in **colore a tinta unita**.
4. Modificare il colore di **sfondo** in **RGBA 0**, 0, 0, 0. Il nero viene visualizzato come trasparente in HoloLens.
5. Modificare i **piani di ritaglio in prossimità** del [HoloLens consigliato](camera-in-unity.md#clip-planes) 0,85 (contatori).

![Impostazioni della fotocamera Unity](images/Unitycamerasettings.png)<br>
*Impostazioni della fotocamera Unity*

> [!IMPORTANT]
> Se si elimina e si crea una nuova fotocamera, assicurarsi che la nuova fotocamera sia contrassegnata come **MainCamera**.

## <a name="see-also"></a>Vedere anche
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Panoramica sullo sviluppo Unity](unity-development-overview.md)
