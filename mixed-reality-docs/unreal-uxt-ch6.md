---
title: 6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore
description: Parte 6 di un'esercitazione per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519968"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Creazione di pacchetti e distribuzione nel dispositivo o nell'emulatore

Questa sezione illustra i passaggi necessari per preparare l'app per l'esecuzione in un dispositivo o un emulatore HoloLens 2. Se usi un dispositivo, puoi eseguire il flusso dal computer al dispositivo oppure configurare l'app in modo da poter essere eseguita direttamente sul dispositivo. Se invece non usi un dispositivo, dovrai configurare l'app affinché venga eseguita nell'emulatore. 

## <a name="objectives"></a>Obiettivi

* [Solo dispositivo] Eseguire lo streaming dell'app in HoloLens 2 da remoto tramite un'app olografica
* Creare il pacchetto e distribuire l'app in un dispositivo o un emulatore HoloLens 2

## <a name="device-only-stream"></a>[Solo dispositivo] Eseguire lo streaming

1.  Installa **Holographic Remoting Player** dal Microsoft Store in HoloLens 2 ed esegui l'app

2.  Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto). Nella sezione Holographic Remoting seleziona la casella per abilitare la comunicazione remota e riavviare l'editor.

3.  Immetti l'indirizzo IP del dispositivo e fai clic su Connect (Connetti).

4.  Dopo esserti connesso, nell'editor di UE4 fai clic sulla freccia a discesa a destra del pulsante di riproduzione e seleziona VR Preview (Anteprima VR).

## <a name="package-and-deploy-your-app"></a>Creare il pacchetto e distribuire l'app 

>[!NOTE]
>Se è la prima volta esegui il packaging di un'app Unreal per HoloLens, dovrai scaricare i file di supporto dall'utilità di avvio Epic. A tale scopo, passa alla scheda **Library** (Libreria) nell'utilità di avvio Epic Games. Seleziona la freccia a discesa accanto a **Launch** (Avvia) quindi **Options** (Opzioni). In **Target Platforms** (Piattaforme di destinazione) seleziona **HoloLens 2** e fai clic su **Apply** (Applica). 
>![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-installationoptions.PNG)

1.  Passa a **Edit > Project Settings** (Modifica > Impostazioni progetto). In **Project > Description > About > Project Name** (Progetto > Descrizione > Informazioni -> Nome progetto) assegna un nome al progetto. In **Project > Description > Publisher > Company Distinguished Name** Progetto > Descrizione > Autore > Nome distinto società inserisci "CN={INSERISCI NOME SOCIETÀ}". Se lasci vuoto uno di questi campi, verrà generato un errore. 

![Impostazioni del progetto - Descrizione](images/unreal-uxt/6-cn.PNG)

2.  In **Platforms > HoloLens** (Piattaforma > HoloLens) scegli l'emulazione e/o il dispositivo, in base al tipo di destinazione desiderato.

3.  Nella sezione **Packaging** (Creazione del pacchetto), accanto a **Signing Certificate** (Certificato di firma), fai clic sul pulsante **Generate new** (Genera nuovo) per generare un nuovo certificato di firma. Torna alla finestra principale.

![Impostazioni di progetto - Piattaforme - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  Passa a **File > Package Project** (File > Crea pacchetto progetto) e seleziona **HoloLens**. Crea una nuova cartella in cui salvare il pacchetto e fare clic su **Select Folder** (Seleziona cartella). 

5.  Dopo aver creato il pacchetto dell'app, apri **Windows Device Portal**, passa a **Views > Apps** (Viste > App) e trova la sezione **Deploy apps** (Distribuzione delle app).

6.  Fai clic su **Browse...** (Sfoglia...) e passa al file **ChessApp.appxbundle**. Fare clic su **Apri**. 

    * Se è la prima volta che installi l'app sul dispositivo, seleziona la casella accanto a **Allow me to select framework packages** (Consenti di selezionare i pacchetti del framework). Nella finestra di dialogo successiva, includi il file VCLibs.appx appropriato (arm64 per il dispositivo, x64 per l'emulatore). 

7.  Fai clic su **Install** (Installa).

Congratulazioni per aver completato questa esercitazione.  