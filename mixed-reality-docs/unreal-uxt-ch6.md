---
title: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore
description: Parte 6 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: 99c431920c72cf85fed5a0eec6fc72ddf9fb112c
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330238"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore

## <a name="overview"></a>Panoramica

Nell'esercitazione precedente hai aggiunto un semplice pulsante che riporta il pezzo degli scacchi nella posizione originale. In questa sezione finale preparerai l'app per l'esecuzione su HoloLens 2 o su un emulatore. Se usi HoloLens 2, puoi trasmettere il flusso dal computer oppure creare un pacchetto dell'app in modo che venga eseguita direttamente sul dispositivo. Se non hai un dispositivo, creerai un pacchetto dell'app per l'esecuzione nell'emulatore. Alla fine di questa sezione avrai un'app in realtà mista distribuita pronta per l'uso, completa di interazioni e interfaccia utente.

## <a name="objectives"></a>Obiettivi

* [Solo dispositivo] Streaming a HoloLens 2 con app remota olografica
* Creazione del pacchetto e distribuzione dell'app in un dispositivo HoloLens 2 o in un emulatore

## <a name="device-only-streaming"></a>[Solo dispositivo] Streaming
[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in questo caso indica lo streaming di dati da un PC o dispositivo UWP autonomo a HoloLens 2, non il cambio di canale. Funziona in questo modo: un'app host remota riceve un flusso di dati di input da HoloLens, esegue il rendering del contenuto in una visualizzazione Immersive virtuale e ritrasmette i frame di contenuto a HoloLens tramite Wi-Fi. Lo streaming consente di aggiungere visualizzazioni Immersive remote nel software per PC desktop esistente e di accedere a più risorse di sistema. 

Se usi questa strategia per l'app di scacchi, dovrai eseguire alcuni passaggi:

1.  Installa **Holographic Remoting Player** dal Microsoft Store in HoloLens 2 ed esegui l'app.

2.  Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto) e seleziona **enable remoting** (abilita comunicazione remota) nella sezione **Holographic Remoting**.

3.  Riavvia l'editor, [trova l'indirizzo IP del dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi) e immettilo, quindi fai clic su **Connect** (Connetti).

Dopo esserti connesso, fai clic sulla freccia a discesa a destra del pulsante **Play** (Riproduci) e seleziona **VR Preview** (Anteprima VR). L'app verrà eseguita nella finestra di anteprima VR, che viene trasmessa al visore VR HoloLens. 

## <a name="packaging-and-deploying-the-app"></a>Creazione del pacchetto e distribuzione dell'app 

>[!NOTE]
>Se è la prima volta esegui il packaging di un'app Unreal per HoloLens, dovrai scaricare i file di supporto dal laucher Epic. 
>- Passa alla scheda **Library** (Libreria) nel launcher di Epic Games, seleziona la freccia a discesa accanto a **Launch** (Avvia) e fai clic su **Options** (Opzioni). 
>- In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica). 
>![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-installationoptions.PNG)

1.  Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto). 
    * Aggiungi un nome progetto in **Project > Description > About > Project Name** (Progetto > Descrizione > Informazioni -> Nome progetto). 
    * Aggiungi **CN={INSERISCI NOME SOCIETÀ}** in **Project > Description > Publisher > Company Distinguished Name** (Progetto > Descrizione > Autore > Nome distinto società).

> [!IMPORTANT]
> Se lasci vuoto uno di questi campi, verrà generato un errore. 

![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-cn.PNG)

2.  Abilita **Build for HoloLens Emulation** (Build per emulazione HoloLens) e/o **Build for HoloLens Device** (Build per dispositivo HoloLens) in **Platforms > HoloLens** (Piattaforme > HoloLens).

3.  Fai clic su **Generate new** (Genera nuovo) nella sezione **Packaging** (Pacchetto), accanto a **Signing Certificate** (Certificato di firma), quindi torna alla finestra principale.

![Impostazioni di progetto - Piattaforme - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  Passa a **File > Package Project** (File > Crea pacchetto progetto) e seleziona **HoloLens**. 
    * Crea una nuova cartella in cui salvare il pacchetto e fai clic su **Select Folder** (Seleziona cartella). 

5.  Dopo avere creato il pacchetto dell'app, apri il [Portale di dispositivi di Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), passa a **Views > Apps** (Viste > App) e trova la sezione **Deploy apps** (Distribuzione app).

6.  Fai clic su **Sfoglia** (Sfoglia), passa al file **ChessApp.appxbundle** e fai clic su **Apri**. 

    * Se è la prima volta che installi l'app sul dispositivo, seleziona la casella accanto a **Allow me to select framework packages** (Consenti di selezionare i pacchetti del framework). 
    * Nella finestra di dialogo successiva includi i file **VCLibs** e **appx** appropriati (arm64 per il dispositivo e x64 per l'emulatore). Li trovi in **HoloLens** all'interno della cartella in cui hai salvato il pacchetto.

7.  Fai clic su **Install** (Installa).
    * Ora puoi passare a **All Apps** (Tutte le app) e toccare l'app appena installata per eseguirla oppure avviare l'app direttamente dal **Portale di dispositivi di Windows**. 

A questo punto, la tua applicazione in realtà mista HoloLens è completa e pronta per l'uso. Ci sono però molti altri aspetti da esplorare. MRTK include molte funzionalità autonome che puoi aggiungere ai progetti, ad esempio il mapping spaziale, lo sguardo e l'input vocale e persino codici a matrice. Per altre informazioni su queste funzionalità, consulta la [Panoramica sullo sviluppo con Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).