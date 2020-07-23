---
title: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore
description: Parte 6 di 6 in una serie di esercitazioni per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: c49e2a69cb97a996da4bf601a105c2176ccf267f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303542"
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

1.  Installa **Holographic Remoting Player** dal Microsoft Store in HoloLens 2 ed esegui l'app. Prendere nota dell'indirizzo IP visualizzato nell'app.

2.  Nell'editor di Unity passare a **Edit > Project Settings** (Modifica > Impostazioni progetto) e selezionare **Enable Remoting** (Abilita comunicazione remota) nella sezione **Holographic Remoting**.

3.  Riavviare l'editor e immettere l'indirizzo IP del dispositivo (come visualizzato nell'app del lettore Holographic Remoting) e quindi fare clic su **Connect** (Connetti).

Dopo esserti connesso, fai clic sulla freccia a discesa a destra del pulsante **Play** (Riproduci) e seleziona **VR Preview** (Anteprima VR). L'app verrà eseguita nella finestra di anteprima VR, che viene trasmessa al visore VR HoloLens. 

## <a name="packaging-and-deploying-the-app-via-device-portal"></a>Creazione del pacchetto e distribuzione dell'app tramite il portale del dispositivo

>[!NOTE]
>Se è la prima volta esegui il packaging di un'app Unreal per HoloLens, dovrai scaricare i file di supporto dall'utilità di avvio Epic. 
>- Passa alla scheda **Library** (Libreria) nel launcher di Epic Games, seleziona la freccia a discesa accanto a **Launch** (Avvia) e fai clic su **Options** (Opzioni). 
>- In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica). 
>![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-installationoptions.PNG)

1.  Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto). 
    * Aggiungi un nome progetto in **Project > Description > About > Project Name** (Progetto > Descrizione > Informazioni -> Nome progetto). 
    * Aggiungi **CN=NomeSocietà** in **Project > Description > Publisher > Company Distinguished Name** (Progetto > Descrizione > Autore > Nome distinto società).

> [!IMPORTANT]
> Se lasci vuoto uno di questi campi, viene generato un errore quando tenti di generare un nuovo certificato nel passaggio 3. 

> [!IMPORTANT]
> Il nome dell'autore deve essere nel [formato LADPv3 Distinguished Names](https://www.ietf.org/rfc/rfc2253.txt). Se il nome dell'autore non è valido, viene visualizzato un errore che indica che la chiave di firma non è stata trovata e che non è stato possibile firmare digitalmente l'app durante la creazione del pacchetto.

![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-cn.PNG)

2.  Abilita **Build for HoloLens Emulation** (Build per emulazione HoloLens) e/o **Build for HoloLens Device** (Build per dispositivo HoloLens) in **Platforms > HoloLens** (Piattaforme > HoloLens).

3.  Fai clic su **Generate new** (Genera nuovo) nella sezione **Packaging** (Pacchetto), accanto a **Signing Certificate** (Certificato di firma).

> [!IMPORTANT]
> Se usi un certificato già generato, il nome dell'autore del certificato deve corrispondere al nome dell'autore dell'applicazione. In caso contrario, viene visualizzato un errore che indica che la chiave di firma non è stata trovata e che non è stato possibile firmare digitalmente l'app errore.

![Impostazioni di progetto - Piattaforme - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. Fai clic su **None** (Nessuno) a scopo di test quando ti viene chiesto di creare una password di chiave privata.

![Generazione di un nuovo certificato](images/unreal-uxt/6-private-key-testing.png)

5. Passa a **File > Package Project** (File > Crea pacchetto progetto) e seleziona **HoloLens**. 
    * Crea una nuova cartella in cui salvare il pacchetto e fare clic su **Select Folder** (Seleziona cartella). 

6.  Dopo avere creato il pacchetto dell'app, apri il [Portale di dispositivi di Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), passa a **Views > Apps** (Viste > App) e trova la sezione **Deploy apps** (Distribuzione app).

7.  Fai clic su **Sfoglia** (Sfoglia), passa al file **ChessApp.appxbundle** e fai clic su **Apri**. 

    * Se è la prima volta che installi l'app sul dispositivo, seleziona la casella accanto a **Allow me to select framework packages** (Consenti di selezionare i pacchetti del framework). 
    * Nella finestra di dialogo successiva includi i file **VCLibs** e **appx** appropriati (arm64 per il dispositivo e x64 per l'emulatore). Li trovi in **HoloLens** all'interno della cartella in cui hai salvato il pacchetto.

8.  Fai clic su **Install** (Installa).
    * Ora puoi passare a **All Apps** (Tutte le app) e toccare l'app appena installata per eseguirla oppure avviare l'app direttamente dal **Portale di dispositivi di Windows**. 

A questo punto, la tua applicazione in realtà mista HoloLens è completa e pronta per l'uso. Ci sono però molti altri aspetti da esplorare. MRTK include molte funzionalità autonome che puoi aggiungere ai progetti, ad esempio il mapping spaziale, lo sguardo e l'input vocale e persino codici a matrice. Per altre informazioni su queste funzionalità, consulta la [Panoramica sullo sviluppo con Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).
