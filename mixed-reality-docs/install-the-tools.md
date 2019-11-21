---
title: Installare gli strumenti
description: Inizia da qui per prepararti allo sviluppo della realtà mista. Questo articolo deve sempre essere aggiornato con le versioni più recenti di Unity, Visual Studio e altri strumenti consigliati per lo sviluppo con visori VR immersivi Windows Mixed Reality e HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: informazioni aggiornate, strumenti, inizio, nozioni di base, unity, visual studio, toolkit
ms.openlocfilehash: f63cf094c5dffd29d2cb54cb56df588858785ae9
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064244"
---
# <a name="install-the-tools"></a>Installare gli strumenti

Acquisisci gli strumenti necessari per creare applicazioni per visori VR immersive di Windows Mixed Reality e Microsoft HoloLens. Non è disponibile un SDK separato per lo sviluppo Windows Mixed Reality. Userai Visual Studio con Windows 10 SDK.

Non disponi di un dispositivo di realtà mista? Puoi installare l'[emulatore di HoloLens](using-the-hololens-emulator.md) per testare alcune funzionalità delle app di realtà mista senza HoloLens. Puoi anche usare il [simulatore Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) per testare le tue app di realtà mista per visori VR immersive.

Il modo più semplice per iniziare a creare app di realtà mista consiste nell'installare il motore di gioco Unity. Se invece vuoi usare un motore personalizzato, puoi anche creare app in DirectX.

>[!TIP]
>Contrassegna questa pagina e controllala periodicamente per tenerti aggiornato sulla versione più recente di ogni strumento consigliato per lo sviluppo della realtà mista.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Elenco di controllo per l'installazione


| Strumento | Descrizione | Note |
|---------|---------|---------|
| ![Logo Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(collegamento per l'installazione manuale)</a> | Installa la versione di Windows 10 più recente in modo che il sistema operativo del PC corrisponda alla piattaforma per cui stai creando applicazioni di realtà mista. | **Installazione di Windows 10** <br> <ul><li>Puoi installare la versione di Windows 10 più recente tramite Windows Update in Impostazioni oppure creando supporti di installazione, usando il collegamento nella colonna sinistra.<li>Vedi le [note sulla versione aggiornate](release-notes-october-2018.md) per informazioni sulle funzionalità di realtà mista più recenti disponibili con ogni versione di Windows 10.</ul> **Abilita la modalità sviluppatore nel PC** in Impostazioni > Aggiornamento e sicurezza > Per sviluppatori. <br><br> **Nota per computer aziendali e gestiti dall'organizzazione:** se il computer è gestito dal reparto IT dell'organizzazione, potrebbe essere necessario contattarlo per l'aggiornamento. <br><br> **Versioni 'N' di Windows:** i visori VR immersive di Windows Mixed Reality non sono supportati nelle versioni "N" di Windows. |
| ![Logo di Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.1 o versione successiva)**<br>(collegamento per l'installazione)</a> | Ambiente di sviluppo integrato con funzionalità complete per Windows e altro ancora. Visual Studio verrà usato per scrivere il codice ed eseguire il debug, i test e la distribuzione. | **Carichi di lavoro da installare:** <ul><li>Sviluppo per desktop con C++</li><li>Sviluppo di app UWP (Universal Windows Platform)</li></ul>**Nota su Unity:** a meno che non stia intenzionalmente tentando di installare una versione più recente (non LTS) di Unity per uno scopo specifico, è consigliabile *non* installare il carico di lavoro Unity come parte dell'installazione di Visual Studio e installare invece il flusso 2018.4 LTS di Unity come indicato di seguito.<br> <br>**Nota:** esistono alcuni problemi noti relativi al debug di app di realtà mista in Visual Studio 2019 versione 16.0.  Assicurati di aggiornare Visual Studio 2019 alla versione 16.1 o successiva. |
| ![Logo Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>(collegamento per l'installazione manuale)</a> | Include le intestazioni, le librerie, i metadati e gli strumenti più recenti per la creazione di app di Windows 10 in HoloLens 2. | Per creare app di HoloLens 2, devi installare l'SDK di Windows, build 18362 o versione successiva.<br> <br> Se sviluppi solo applicazioni per visori VR di Windows Mixed Reality desktop o per HoloLens (prima generazione), puoi usare Windows SDK installato da Visual Studio 2017. |
| ![Logo di Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2110553" target="_blank">**Emulatore HoloLens 2 (aggiornamento di novembre 2019)**<br>(collegamento per l'installazione: 10.0.18362.1039)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulatore di HoloLens (prima generazione)**<br>(collegamento per l'installazione: 10.0.17763.134)</a> | L'emulatore permette di eseguire le applicazioni in un'immagine di macchina virtuale HoloLens senza un dispositivo HoloLens fisico.<br> <br> | Vedi [Uso dell'emulatore di HoloLens](using-the-hololens-emulator.md) per altre informazioni su come iniziare a usare l'emulatore.<br> <br> **Il sistema deve supportare Hyper-V** per garantire un'installazione corretta dell'emulatore. Vedi più avanti la sezione relativa ai requisiti di sistema per i dettagli. <br>|

## <a name="choose-your-engine"></a>Scegli il motore

:::row:::
    :::column:::
       [![Unity](images/unity_logo.png)](https://unity3d.com/unity/qa/lts-releases?version=2018.4)<br>
        **[Unity](https://unity3d.com/unity/qa/lts-releases?version=2018.4)**<br>
        È in genere consigliabile il flusso Unity LTS (Long Term Support) come versione ottimale per iniziare nuovi progetti, eseguendo l'aggiornamento alla revisione più recente per usufruire delle ultime fix stabili.<br> <br>Il suggerimento corrente è di usare **Unity 2018.4.x**, che è la build LTS necessaria per MRTK v2 indicato di seguito.<br> <br>Alcuni sviluppatori potrebbero scegliere di usare una versione diversa di Unity per motivi specifici. In questi casi, Unity supporta installazioni side-by-side di versioni diverse.<br><br>[![MRTK](images/MRTKIcon.jpg)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)<br>**[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)**<br>Mixed Reality Toolkit (MRTK) v2 per Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista.<br><br> Permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso alla creazione di applicazioni di realtà mista offrendo inoltre un contributo alla community quando si realizzano progressi.
    :::column-end:::
    :::column:::
        [Unreal![](images/Unreal_logo.png)](https://docs.unrealengine.com//GettingStarted/Installation/index.html)<br>
        **[Unreal](https://docs.unrealengine.com//GettingStarted/Installation/index.html)**<br>
        Unreal Engine 4 è un potente motore di creazione open source con supporto completo per la realtà mista sia in C++ che nei progetti.<br> <br>Il supporto di HoloLens per Unreal Engine 4.23 attualmente è in versione beta.
    :::column-end:::
    :::column:::
        [![Modelli DirectX](images/DirectX_logo.png)](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)<br>
        **[Modelli DirectX](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)**<br>
        Tutti gli elementi di base necessari per iniziare a scrivere un'app di realtà mista usando DirectX. Sono inclusi un loop di rendering (o "loop di gioco"), una classe helper DeviceResources per la gestione del contesto e del dispositivo Direct3D e un semplice renderer di esempio.
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK)

Mixed Reality Toolkit offre componenti e funzionalità utili per accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, visori per Windows Mixed Reality e piattaforma OpenVR. Il progetto mira a ridurre le barriere di accesso alla creazione di applicazioni di realtà mista, offrendo inoltre un contributo alla community quando si realizzano progressi.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit</a>: una raccolta di script e componenti realizzati allo scopo di accelerare lo sviluppo di applicazioni di realtà mista.
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit-Unity</a>: usa il codice del toolkit di base semplificandone l'utilizzo in Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit</a>: bit di codice e componenti che non possono essere eseguiti direttamente in HoloLens o nei visori VR immersive, ma che si aggiungono a essi per creare esperienze per Windows Mixed Reality.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Configurazione del computer per lo sviluppo della realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti. 

### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando configuri il computer di sviluppo per lo sviluppo per HoloLens, assicurati che soddisfi i requisiti di sistema sia di <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> che di <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se prevedi di usare l'emulatore di HoloLens (prima generazione), assicurati che il computer soddisfi anche i [requisiti di sistema dell'emulatore di HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Per iniziare a usare l'emulatore di HoloLens, vedi [Uso dell'emulatore di HoloLens](using-the-hololens-emulator.md).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

### <a name="for-immersive-vr-headset-development"></a>Per lo sviluppo per visori VR immersive

>[!NOTE]
>Le linee guida seguenti rappresentano le specifiche minime correnti consigliate per il *computer di sviluppo* per visori VR immersive e possono essere aggiornate a intervalli regolari.

>[!WARNING]
>Non confonderle con le [linee guida per la compatibilità hardware minima del computer](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che descrivono le *specifiche del computer utente* a cui fare riferimento per le app o i giochi per visori VR immersive.

Se il PC di sviluppo per visori VR immersive non dispone di porte HDMI e/o USB 3.0 di grandi dimensioni, dovrai usare [adattatori](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) per collegare i visori.

Esistono attualmente [problemi noti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

<table>
<tr>
<th></th><th> Minimo</th><th> Consigliato</th>
</tr><tr>
<td> Processore</td><td> <b>Notebook:</b> CPU Intel Mobile Core i5 settima generazione, dual-core con hyperthreading <b>Desktop:</b> CPU Intel Desktop i5 sesta generazione, dual-core con hyperthreading <b>OPPURE</b> equivalente quad-core 4,2 GHz AMD FX4350</td><td> <b>Desktop:</b> Intel Desktop i7 sesta generazione (6 core) <b>OPPURE</b> AMD Ryzen 5 1600 (6 core, 12 thread)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> GPU NVIDIA GTX 965M, AMD RX 460M (2 GB) equivalente o superiore con supporto DX12<b>Desktop:</b> GPU NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) equivalente o superiore con supporto DX12</td><td><b>Desktop:</b> GPU NVIDIA GTX 960/1060, AMD Radeon RX 480 (2 GB) equivalente o superiore con supporto DX12</td>
</tr><tr>
<td> Versione WDDM driver GPU</td><td colspan="2"> Driver WDDM 2.2</td>
</tr><tr>
<td> Potenza termica</td><td colspan="2"> Almeno 15 W</td>
</tr><tr>
<td> Porte per scheda video</td><td colspan="2"> Porta per scheda video disponibile 1x per&#160;visore VR (HDMI 1.4 o DisplayPort 1.2 per visori VR 60 Hz, HDMI 2.0 o DisplayPort 1.2 per visori VR 90 Hz)</td>
</tr><tr>
<td> Risoluzione dello schermo</td><td colspan="2"> Soluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel</td>
</tr><tr>
<td> Memoria</td><td> Almeno 8 GB di RAM</td><td> Almeno 16 GB di RAM</td>
</tr><tr>
<td> Archiviazione</td><td colspan="2"> &gt;10 GB di spazio disponibile aggiuntivo</td>
</tr><tr>
<td> Porte USB</td><td colspan="2"> Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) <b>Nota: USB deve fornire un minimo di 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (per la connettività degli accessori)</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche

* [Cenni preliminari sullo sviluppo](development.md)
* [Uso dell'emulatore HoloLens](using-the-hololens-emulator.md)
* [Uso del simulatore di Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Panoramica dello sviluppo per Unity](unity-development-overview.md)
* [Panoramica dello sviluppo con Unreal](unreal-development-overview.md)
* [Panoramica dello sviluppo DirectX](directx-development-overview.md)
* [Archivio dell'emulatore HoloLens](hololens-emulator-archive.md)
