---
title: Audio spaziale in Unreal
description: Panoramica del plug-in di audio spaziale per Unreal Engine.
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, streaming, comunicazione remota, realtà mista, sviluppo, guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, caratteristiche, ologrammi, sviluppo di giochi
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446812"
---
# <a name="spatial-audio-in-unreal"></a>Audio spaziale in Unreal

## <a name="overview"></a>Panoramica

Diversamente dalla vista, gli umani sentono un suono surround a 360 gradi. L'audio spaziale emula il funzionamento dell'udito umano, fornendo i segnali necessari per identificare le posizioni del suono nello spazio mondo. L'aggiunta dell'audio spaziale nelle applicazioni di realtà mista consente di migliorare il livello di immersione dell'esperienza degli utenti.  

Dato che l'elaborazione dell'audio spaziale di qualità elevata è un'attività complessa, HoloLens 2 è dotato di un hardware dedicato per l'elaborazione di tali oggetti audio.  Prima di poter accedere a questo supporto dell'elaborazione hardware, è necessario installare il plug-in **MicrosoftSpatialSound** nel progetto Unreal. Questo articolo illustra come installare e configurare quel plug-in e suggerisce alcune risorse di approfondimento per l'uso dell'audio spaziale nel motore Unreal. 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>Installazione del plug-in Microsoft Spatial Sound 

Per aggiungere l'audio spaziale a un progetto, prima di tutto è necessario installare il plug-in Microsoft Spatial Sound. Per trovarlo, procedi in questo modo: 

1. Fai clic su **Edit > Plugins** (Modifica > Plug-in) e immetti **MicrosoftSpatialSound** nella casella di ricerca. 
2. Seleziona la casella di controllo **Enabled** (Abilitato) nel plug-in **MicrosoftSpatialSound**. 
3. Riavvia Unreal Editor selezionando **Restart Now** (Riavvia ora) nella pagina dei plug-in. 

> [!NOTE]
> Se non l'hai già fatto, devi installare i plug-in **Microsoft Windows Mixed Reality** e **HoloLens** seguendo le istruzioni riportate nella sezione relativa all' **[inizializzazione del progetto](unreal-uxt-ch2.md)** della nostra serie di tutorial su Unreal.

![Plug-in audio spaziale di Unreal](images/unreal-spatial-audio-img-01.png)

Una volta riavviato l'editor, il progetto è impostato.


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>Impostazione del plug-in di spazializzazione per la piattaforma HoloLens 2
La configurazione del plug-in di spazializzazione è specifica delle singole piattaforme.  Per abilitare il plug-in Microsoft spatial audio per HoloLens 2:
1. Seleziona **Edit > Project Settings** (Modifica > Impostazioni progetto), scorri fino a **Platforms** (Piattaforme) e fai clic su **HoloLens**.
2. Espandi le proprietà **Audio** e imposta il campo **Spatialization Plugin** (Plug-in di spazializzazione) su **Microsoft Spatial Sound**.

![Plug-in di spazializzazione per la piattaforma HoloLens](images/unreal-spatial-audio-img-02.png)

Se prevedi di visualizzare in anteprima l'applicazione nell'editor Unreal su un PC desktop, dovrai ripetere i passaggi precedenti per la piattaforma **Windows**:

![Plug-in di spazializzazione per la piattaforma Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>Abilitazione dell'audio spaziale in una workstation
L'audio spaziale è disabilitato per impostazione predefinita nelle versioni desktop di Windows. Per abilitarlo, puoi:
* Fare clic con il pulsante destro del mouse sul **volume** sulla barra delle applicazioni. 
    + Scegli **Audio spaziale -> Windows Sonic per cuffie** per ottenere la migliore rappresentazione di ciò che sentirai su HoloLens 2.

![Plug-in di spazializzazione](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>Questa impostazione è necessaria solo se prevedi di testare il progetto nell'editor Unreal.

## <a name="creating-attenuation-objects"></a>Creazione di oggetti di attenuazione
Dopo avere installato e configurato i plug-in necessari:
1. Cerca un attore **Ambient Sound** (Suono ambientale) nella finestra **Place Actors** (Posiziona attori) e trascinalo nella finestra **Scene** (Scena).

![Aggiunta dell'attore del suono ambientale](images/unreal-spatial-audio-img-07.png)

2. Imposta l'attore **Ambient Sound** (Suono ambientale) come figlio di un elemento visivo nella scena. 
    * Per impostazione predefinita, un attore Ambient Sound (Suono ambientale) non ha alcuna rappresentazione visiva, quindi sentirai solo un suono dalla sua posizione nella scena. Se viene collegato a un elemento visivo, puoi vedere e spostare l'attore come qualsiasi altro asset.

3.  Fai clic con il pulsante destro del mouse su **Content Browser** (Browser contenuto) e seleziona **Create Advanced Asset -> Sounds -> Sound Attenuation** (Crea asset avanzato -> Suoni-> Attenuazione suono):

![Creazione di un asset di attenuazione del suono](images/unreal-spatial-audio-img-06.png)

4. Fai clic con il pulsante destro del mouse sull'asset **Sound Attenuation** (Attenuazione del suono) nella finestra **Content Browser** (Browser contenuto) e scegli l'opzione **Edit** (Modifica) per visualizzare la finestra delle proprietà.
    * Imposta **Spatialization Method** (Metodo di spazializzazione) su **Binaural** (Binaurale).

![Impostazione del metodo di spazializzazione](images/unreal-spatial-audio-img-03.png)

5. Seleziona l'attore **Ambient Sound** (Suono ambientale) e scorri fino alla sezione **Attenuation** (Attenuazione) nel pannello **Details** (Dettagli). 
    * Imposta la proprietà **Attenuation Settings** (Impostazioni attenuazione) sull'asset **Sound Attenuation** (Attenuazione del suono) che hai creato.

![Impostazione dell'attenuazione](images/unreal-spatial-audio-img-08.png)

6. Imposta l'oggetto **Sound Asset** (Asset audio) che vuoi associare all'attore Ambient Sound (Suono ambientale) aggiornando la proprietà **Sound** (Suono) dell'attore Ambient Sound (Suono ambientale) per specificare il file SoundAsset da usare.

![Impostazione dell'asset audio](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> Il file SoundAsset deve essere mono per la spazializzazione con il plug-in Microsoft Spatial Sound. È possibile trovare le proprietà del file audio posizionando il puntatore del mouse sull'asset nella finestra Content Browser (Browser contenuto), come illustrato nello screenshot seguente.

![Nuovo asset di attenuazione del suono](images/unreal-spatial-audio-img-10.png)

Terminata questa configurazione, il suono ambientale può essere spazializzato usando il supporto di offload hardware dedicato in HoloLens 2.

## <a name="configuring-objects-for-spatialization"></a>Configurazione degli oggetti per la spazializzazione
Quando usi l'audio spaziale, sei tu a gestire il comportamento del suono in un ambiente virtuale. L'obiettivo principale consiste nel creare oggetti audio che producono un suono più forte quando l'utente è vicino e un suono più debole quando è lontano. Grazie a questo effetto, detto attenuazione del suono, i suoni sembrano collocati in un punto fisso.

Tutti gli oggetti di attenuazione includono impostazioni modificabili per:
* Distanza
* Spazializzazione
* Assorbimento dell'aria
* Focus sull'ascoltatore
* Riverbero
* Occlusione

Nella pagina dedicata all'[attenuazione del suono in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) sono forniti dettagli e specifiche di implementazione su ognuno di questi argomenti.


## <a name="see-also"></a>Vedere anche
* [Audio spaziale](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [Progettazione dell'audio spaziale](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [Spaziale MR 220: Audio spaziale](https://docs.microsoft.com/windows/mixed-reality/holograms-220)