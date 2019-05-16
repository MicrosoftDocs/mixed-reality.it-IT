---
title: Installare gli strumenti
description: Iniziare da qui per la preparazione per lo sviluppo della realtà mista. Questo articolo dovrebbe riflettono sempre le versioni più recenti di Unity, Visual Studio e altri strumenti consigliati per lo sviluppo di visore VR immersivi HoloLens e realtà mista di Windows.
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: sempre aggiornati, strumenti, iniziare a usare, nozioni di base, unity, visual studio, toolkit
ms.openlocfilehash: 03a310457bf5ef498a6369a158b697c7fa59d6d9
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730874"
---
# <a name="install-the-tools"></a>Installare gli strumenti

Ottenere gli strumenti che necessari per compilare App per Microsoft HoloLens e auricolari (VR) coinvolgenti di realtà mista di Windows. Non vi è alcun sviluppo separati di SDK per realtà mista di Windows; si userà Visual Studio con SDK per Windows 10.

Non hai un dispositivo di realtà mista? È possibile installare il [emulatore HoloLens](using-the-hololens-emulator.md) per testare alcune funzionalità delle app di realtà mista senza un HoloLens. È anche possibile usare la [simulatore di realtà mista di Windows](using-the-windows-mixed-reality-simulator.md) per testare le app di realtà mista per auricolari coinvolgente e concreto.

Si consiglia di installare il motore di gioco Unity come il modo più semplice per iniziare a creare mista le App per realtà, tuttavia, è anche possibile compilare su DirectX se si vuole usare un motore personalizzato.

>[!TIP]
>Segnalibro di questa pagina e la verificherà periodicamente per mantenere aggiornato alla versione più recente di ogni strumento consigliato per lo sviluppo della realtà mista.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Elenco di controllo installazione


| Strumento | Descrizione | Note |
|---------|---------|---------|
| ![Logo Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(Collegamento di installazione manuale)</a> | Installare la versione più recente di Windows 10 in modo da sistema operativo del computer corrisponde alla piattaforma per cui si sta creando app di realtà mista. | **Installazione di Windows 10** <br> <ul><li>Nelle impostazioni o mediante la creazione di supporti di installazione (usando il collegamento nella colonna sinistra), è possibile installare la versione più recente di Windows 10 tramite Windows Update.<li>Visualizzare [note sulla versione corrente](release-notes-october-2018.md) per informazioni sulla più recente mista funzionalità realtà disponibili con ogni versione di Windows 10.</ul> **Abilitare la modalità sviluppatore nel PC** in Impostazioni > aggiornamento e sicurezza > per gli sviluppatori. <br><br> **Nota per enterprise e computer aziendali gestiti da:** se il computer è gestito da un'organizzazione reparto IT, potrebbe essere necessario contattare per aggiornare. <br><br> **Versioni di "n" di Windows:** Auricolari (VR) coinvolgenti di realtà mista di Windows non sono supportati nelle versioni di "n" di Windows. |
| ![Logo di Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>(Collegamento di installazione)</a> | Ambiente di sviluppo integrato con funzionalità complete (IDE) per Windows e altro ancora. Si userà Visual Studio per scrivere il codice, eseguire il debug, testare e distribuire. | **Carichi di lavoro per l'installazione:** <ul><li>Sviluppo di applicazioni desktop con C++</li><li>Sviluppo della piattaforma Windows universale</li></ul>**Nota su Unity:** A meno che non si sta intenzionalmente installare una versione più recente (non-LTS) di Unity per uno scopo specifico, è consigliabile *non* installare il carico di lavoro di Unity come parte dell'installazione di Visual Studio e installando il 2018.3 LTS flusso di Unity come indicato di seguito.<br> <br>**Nota:** Esistono alcuni problemi noti con lo sviluppo della realtà mista in Visual Studio 2019 al momento.  Per il momento, è consigliabile continuare a usare Visual Studio 2017. |
| ![Logo Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>(Collegamento di installazione manuale)</a> | Offre la più recente intestazioni, librerie, metadati e gli strumenti per la creazione di App di Windows 10 in 2 HoloLens. | Per compilare App 2 HoloLens, è necessario installare il Windows SDK, build 18362 o versione successiva.<br> <br> Se si sta sviluppando solo App in HoloLens o auricolari realtà mista di Windows desktop (dal 1 ° generazione), è possibile usare il SDK di Windows installato da Visual Studio 2017. |
| ![Logo di Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**Emulatore HoloLens 2**<br>(Collegamento di installazione: 10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (dal 1 ° generazione) emulatore**<br>(Collegamento di installazione: 10.0.17763.253)</a> | L'emulatore consente di eseguire le app nell'immagine di macchina virtuale senza un HoloLens fisico HoloLens.<br> <br> Questo pacchetto include anche modelli di progetto DirectX holographic per Visual Studio. | Visualizzare [usando l'emulatore di HoloLens](using-the-hololens-emulator.md) per altre informazioni su come iniziare con l'emulatore.<br> <br> **Il sistema deve supportare Hyper-V** per l'installazione dell'emulatore abbia esito positivo. Vedi la sezione requisiti di sistema seguente per i dettagli. Se si desidera, è possibile scegliere di installare solo i modelli senza l'emulatore.<br>|
| ![Logo di Unity](images/unity_logo.png)<br><br><a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 2018.3**<br>(Collegamento di installazione)</a> | Unity game engine è il modo più semplice per creare esperienze di realtà mista, con supporto incorporato per le funzionalità di realtà mista di Windows. | È in genere consigliabile il flusso di Unity LTS (lungo termine di supporto) come la versione migliore con cui si desidera avviare nuovi progetti, l'aggiornamento per la revisione più recente per prelevare le correzioni stabile più recente.<br> <br> Corrente si consiglia di usare **Unity 2018.3.x**, che è necessario per la versione v2 MRTK riportato di seguito e che diventerà presto LTS 2018 di Unity di compilazione. <br> <br> Alcuni sviluppatori possibile usare una versione diversa di Unity per motivi specifici. In questi casi, Unity supporta installazioni side-by-side di versioni diverse. |
| ![Logo MRTK](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**Toolkit di realtà mista (MRTK v2) per Unity**</a> | MRTK v2 per Unity è un kit di sviluppo multipiattaforma open source per le applicazioni di realtà mista.<br><br> Consente di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, auricolari (VR) coinvolgenti di realtà mista di Windows e la piattaforma OpenVR MRTK v2. Il progetto mira a ridurre le barriere di ingresso per creare applicazioni di realtà mista e aggiunta come contributo alla community per noi aumento delle dimensioni. | Altre informazioni su v2 MRTK visitando il progetto <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">wiki GitHub</a>. |


## <a name="mixed-reality-toolkit"></a>Toolkit di realtà mista

Il Toolkit di realtà mista vengono forniti componenti e funzionalità sono utili per accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, piattaforma OpenVR e auricolari realtà mista di Windows. Il progetto mira a ridurre gli ostacoli alla voce per creare applicazioni di realtà mista e contribuire alla community di noi crescita.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit Unity</a> : Usa il codice dal toolkit di base e rende più semplici da utilizzare in Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> : componenti che non può essere eseguito direttamente su HoloLens o auricolari (VR) coinvolgenti e bit di codice, ma invece coppia con loro per creare esperienze di realtà mista di Windows di destinazione.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Configurazione del PC per lo sviluppo della realtà mista

Windows 10 SDK funziona meglio su sistema operativo Windows 10. Questo SDK è anche supportato in Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Si noti che non tutti gli strumenti sono supportati nei sistemi operativi precedenti. 

### <a name="for-hololens-development"></a>Per lo sviluppo di HoloLens

Quando si configura il computer di sviluppo per lo sviluppo di HoloLens, assicurarsi che soddisfi i requisiti di sistema per entrambi <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> e <a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>. Se si prevede di usare il HoloLens (dal 1 ° generazione) emulatore, è opportuno assicurarsi che il computer soddisfi i [requisiti di sistema dell'emulatore HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements) anche.

Per iniziare a usare l'emulatore di HoloLens, vedere [usando l'emulatore di HoloLens](using-the-hololens-emulator.md).

Se si prevede di sviluppare per HoloLens sia la realtà mista di Windows auricolari (VR) coinvolgenti, utilizzare i consigli del sistema e i requisiti nella sezione seguente.

### <a name="for-immersive-vr-headset-development"></a>Per lo sviluppo di visore VR immersive (VR)

>[!NOTE]
>Le linee guida seguenti sono le specifiche correnti minime e consigliate per le cuffie (VR) coinvolgenti *computer di sviluppo*e possono essere aggiornate regolarmente.

>[!WARNING]
>Non confondere con il [linee guida per la compatibilità di hardware PC minima](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che descrivono il *specifiche consumer PC* a cui si deve avere come destinazione gioco o dell'app di visore VR immersivi (VR).

Se il PC di sviluppo visore VR immersivi non dispone di porte HDMI e/o USB 3.0 ingrandita, dovrai [schede](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) connettersi le cuffie.

Esistono attualmente [problemi noti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con i notebook contenenti grafici ibridi.

<table>
<tr>
<th></th><th> Minimo</th><th> Consigliato</th>
</tr><tr>
<td> Processore</td><td> <b>taccuino:</b> Intel Core Mobile i5 generazione 7, CPU Dual-Core con hyperthreading <b>Desktop:</b> Intel Desktop i5 6 generazione della CPU, processori Dual-Core con hyperthreading <b>o</b> AMD FX4350 equivalente di 4,2 Ghz Quad-Core</td><td> <b>Desktop:</b> Desktop Intel i7 generazione 6 (6 Core) <b>o</b> AMD Ryzen 1600 5 (6 Core, 12 thread)</td>
</tr><tr>
<td> GPU</td><td> <b>taccuino:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) è equivalente o superiore con supporto GPU DX12 <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) è equivalente o superiore DX12 con supporto GPU</td><td><b>Desktop:</b> 1060/NVIDIA GTX 980, AMD Radeon RX 480 (2GB) è equivalente o superiore DX12 con supporto GPU</td>
</tr><tr>
<td> Versione GPU del driver WDDM</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potenza termica</td><td colspan="2"> 15W o versione successiva</td>
</tr><tr>
<td> Le porte vengono visualizzate le immagini</td><td colspan="2"> 1 x grafica disponibile Visualizza la porta per&#160;visore VR (1.4 HDMI o DisplayPort 1.2 per 60Hz auricolari, 2.0 HDMI o DisplayPort 1.2 per auricolari 90Hz)</td>
</tr><tr>
<td> Risoluzione dello schermo</td><td colspan="2"> Soluzione: SVGA (800 x 600) o maggiore è la profondità: 32 bit di colore per pixel</td>
</tr><tr>
<td> Memoria</td><td> 8&#160;GB di RAM o superiore</td><td> 16 GB di RAM o superiore</td>
</tr><tr>
<td> Archiviazione</td><td colspan="2"> &gt;10 GB di spazio libero aggiuntivo</td>
</tr><tr>
<td> Porte USB</td><td colspan="2"> 1 cavo USB disponibile la porta per le cuffie (USB 3.0 Type-A) <b>Nota: USB deve fornire un minimo di 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> 4.0 Bluetooth (per la connettività degli accessori)</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche

* [Cenni preliminari sullo sviluppo](development-overview.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Uso del simulatore di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Panoramica dello sviluppo per Unity](unity-development-overview.md)
* [Panoramica dello sviluppo DirectX](directx-development-overview.md)
* [Archivio dell'emulatore HoloLens](hololens-emulator-archive.md)
