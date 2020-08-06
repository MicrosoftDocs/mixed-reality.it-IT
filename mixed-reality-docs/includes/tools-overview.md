# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Scaricare la versione più recente

È consigliabile il flusso [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) come versione ottimale per iniziare nuovi progetti, eseguendo l'aggiornamento alla revisione più recente per usufruire delle ultime fix stabili. 
* Il suggerimento corrente è di usare **Unity 2019**, che è la build LTS necessaria per MRTK v2 indicato di seguito.
* Se per motivi specifici è necessario usare una versione diversa di Unity, è supportata l'installazione side-by-side di versioni diverse di Unity.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importare Mixed Reality Toolkit (MRTK)
![MRTK](../images/UX/MRTK_UX_Hero.png)

[Mixed Reality Toolkit](../mrtk-getting-started.md) (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali. Il toolkit permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, ai visori VR immersive di Windows Mixed Reality e alla piattaforma OpenVR.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se non si vuole usare MRTK per Unity, sarà necessario creare personalmente script per tutti i comportamenti e le interazioni.

#### <a name="other-tools-optional"></a>Altri strumenti [facoltativo]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: bit di codice e componenti che non possono essere eseguiti direttamente in HoloLens o nei visori VR immersive, ma che si aggiungono a questi strumenti per creare esperienze per Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a>: raccolta di script e componenti condivisi.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurare il PC per lo sviluppo di app di Realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti. 

> [!NOTE]
> È possibile sviluppare e distribuire le app per HoloLens, visori VR immersive o entrambi. Verificare che siano soddisfare i requisiti seguenti in base alle necessità.

#### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando configuri il computer di sviluppo per lo sviluppo per HoloLens, assicurati che soddisfi i requisiti di sistema sia di <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> che di <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se si prevede di usare l'[emulatore HoloLens](../using-the-hololens-emulator.md), sarà opportuno verificare che il PC soddisfi anche i [requisiti di sistema dell'emulatore HoloLens](../using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Per iniziare a usare l'emulatore di HoloLens, vedi [Uso dell'emulatore di HoloLens](../using-the-hololens-emulator.md).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

#### <a name="immersive-vr-headset-requirements"></a>Requisiti per visori VR immersive

>[!NOTE]
>Le linee guida seguenti rappresentano le specifiche minime correnti consigliate per il *computer di sviluppo* per visori VR immersive e possono essere aggiornate a intervalli regolari.

>[!WARNING]
>Non confonderle con le [linee guida per la compatibilità hardware minima del computer](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che descrivono le *specifiche del computer utente* a cui fare riferimento per le app o i giochi per visori VR immersive.

Se il PC di sviluppo per visori VR immersive non dispone di porte HDMI e/o USB 3.0 di grandi dimensioni, dovrai usare [adattatori](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) per collegare i visori.

Esistono attualmente [problemi noti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

<table>
<tr>
<th></th><th> Minimo</th><th> Implementazione consigliata</th>
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
<td> Risoluzione dello schermo</td><td colspan="2"> Risoluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel</td>
</tr><tr>
<td> Memory</td><td> Almeno 8 GB di RAM</td><td> Almeno 16 GB di RAM</td>
</tr><tr>
<td> Archiviazione:</td><td colspan="2"> &gt;10 GB di spazio disponibile aggiuntivo</td>
</tr><tr>
<td> Porte USB</td><td colspan="2"> Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) <b>Nota: USB deve fornire un minimo di 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (per la connettività degli accessori)</td>
</tr>
</table>

### <a name="whats-next"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Iniziare il percorso Unity](../unity-development-overview.md)

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. Scaricare la versione più recente

È consigliabile installare [Unreal Engine versione 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o versione successiva per sfruttare appieno il supporto di HoloLens incorporato.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importare Mixed Reality Toolkit (MRTK)
![MRTK](../images/UX/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista. MRTK offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali. Il toolkit permette di accelerare lo sviluppo di applicazioni destinate a Microsoft HoloLens, ai visori VR immersive di Windows Mixed Reality e alla piattaforma OpenVR.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Se non si vuole usare MRTK per Unreal, sarà necessario creare personalmente script per tutti i comportamenti e le interazioni.

#### <a name="other-tools-optional"></a>Altri strumenti [facoltativo]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: bit di codice e componenti che non possono essere eseguiti direttamente in HoloLens o nei visori VR immersive, ma che si aggiungono a questi strumenti per creare esperienze per Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a>: raccolta di script e componenti condivisi.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurare il PC per lo sviluppo di app di Realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti. 

> [!NOTE]
> È possibile sviluppare e distribuire le app per HoloLens, visori VR immersive o entrambi. Verificare che siano soddisfare i requisiti seguenti in base alle necessità.

#### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando si configura il PC per lo sviluppo per HoloLens, verificare che vengano soddisfatti i requisiti di sistema sia di [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) sia di <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se si prevede di usare l'[emulatore HoloLens](../using-the-hololens-emulator.md), sarà opportuno verificare che il PC soddisfi anche i [requisiti di sistema dell'emulatore HoloLens](../using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

#### <a name="immersive-vr-headset-requirements"></a>Requisiti per visori VR immersive

>[!NOTE]
>Le linee guida seguenti rappresentano le specifiche minime correnti consigliate per il *computer di sviluppo* per visori VR immersive e possono essere aggiornate a intervalli regolari.

>[!WARNING]
>Non confonderle con le [linee guida per la compatibilità hardware minima del computer](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che descrivono le *specifiche del computer utente* a cui fare riferimento per le app o i giochi per visori VR immersive.

Se il PC di sviluppo per visori VR immersive non dispone di porte HDMI e/o USB 3.0 di grandi dimensioni, dovrai usare [adattatori](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) per collegare i visori.

Esistono attualmente [problemi noti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

<table>
<tr>
<th></th><th> Minimo</th><th> Implementazione consigliata</th>
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
<td> Risoluzione dello schermo</td><td colspan="2"> Risoluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel</td>
</tr><tr>
<td> Memory</td><td> Almeno 8 GB di RAM</td><td> Almeno 16 GB di RAM</td>
</tr><tr>
<td> Archiviazione:</td><td colspan="2"> &gt;10 GB di spazio disponibile aggiuntivo</td>
</tr><tr>
<td> Porte USB</td><td colspan="2"> Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) <b>Nota: USB deve fornire un minimo di 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (per la connettività degli accessori)</td>
</tr>
</table>

### <a name="whats-next"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Iniziare il percorso Unreal](../unreal-development-overview.md)

# <a name="native-openxr"></a>[Nativo (OpenXR)](#tab/native)

 ![Sviluppo di app native](../images/native_logo_banner.png)

Per lo sviluppo di app OpenXR native non è disponibile un motore da scaricare. È possibile trovare tutti gli elementi necessari per iniziare lo sviluppo nel documento [Informazioni di base su OpenXR](../openxr-getting-started.md).

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. Configurare il PC per lo sviluppo di app di Realtà mista

Windows 10 SDK funziona in modo ottimale con il sistema operativo Windows 10. Questo SDK è supportato anche in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2. Non tutti gli strumenti sono supportati nei sistemi operativi meno recenti.

#### <a name="for-hololens-development"></a>Per lo sviluppo per HoloLens

Quando si configura il PC per lo sviluppo per HoloLens, verificare che vengano soddisfatti i requisiti di sistema di <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Se si prevede di usare l'[emulatore HoloLens](../using-the-hololens-emulator.md), sarà opportuno verificare che il PC soddisfi anche i [requisiti di sistema dell'emulatore HoloLens](../using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Se prevedi di eseguire attività di sviluppo sia per HoloLens che per visori VR immersive Windows Mixed Reality, usa i consigli e i requisiti di sistema riportati nella sezione seguente.

> [!NOTE]
> È possibile sviluppare e distribuire le app per HoloLens, visori VR immersive o entrambi. Verificare che siano soddisfare i requisiti seguenti in base alle necessità.

#### <a name="immersive-vr-headset-requirements"></a>Requisiti per visori VR immersive

>[!NOTE]
>Le linee guida seguenti rappresentano le specifiche minime correnti consigliate per il *computer di sviluppo* per visori VR immersive e possono essere aggiornate a intervalli regolari.

>[!WARNING]
>Non confonderle con le [linee guida per la compatibilità hardware minima del computer](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), che descrivono le *specifiche del computer utente* a cui fare riferimento per le app o i giochi per visori VR immersive.

Se il PC di sviluppo per visori VR immersive non dispone di porte HDMI e/o USB 3.0 di grandi dimensioni, dovrai usare [adattatori](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) per collegare i visori.

Esistono attualmente [problemi noti](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con alcune configurazioni hardware, in particolare con notebook contenenti schede video ibride.

<table>
<tr>
<th></th><th> Minimo</th><th> Implementazione consigliata</th>
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
<td> Risoluzione dello schermo</td><td colspan="2"> Risoluzione: SVGA (800 x 600) o superiore Intensità in bit: 32 bit di colore per pixel</td>
</tr><tr>
<td> Memory</td><td> Almeno 8 GB di RAM</td><td> Almeno 16 GB di RAM</td>
</tr><tr>
<td> Archiviazione:</td><td colspan="2"> &gt;10 GB di spazio disponibile aggiuntivo</td>
</tr><tr>
<td> Porte USB</td><td colspan="2"> Porta USB disponibile 1x per visore VR (USB 3.0 Tipo A) <b>Nota: USB deve fornire un minimo di 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (per la connettività degli accessori)</td>
</tr>
</table>

### <a name="whats-next"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Iniziare il percorso Nativo](../directx-development-overview.md)


