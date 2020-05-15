---
title: 3. Configurazione del progetto per la realtà mista
description: Parte 3 di un'esercitazione per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840620"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Configurazione del progetto per la realtà mista

Questa sezione illustra il processo di configurazione dell'app per lo sviluppo della realtà mista. 

## <a name="objectives"></a>Obiettivi

* Informazioni su come configurare un progetto di realtà mista con ARSessionConfig, Pawn e GameMode

## <a name="configure-the-session"></a>Configurare la sessione

1. Nel browser dei contenuti torna alla cartella **Content** (Contenuto). Fai clic su **Add New > Miscellaneous > Data Asset** (Aggiungi nuovo > Varie > Asset dati). 

2. Seleziona **ARSessionConfig** come classe e fai clic su **Select** (Seleziona). Assegna all'asset il nome "ARSessionConfig".

![Creazione di un'origine dati](images/unreal-uxt/3-createasset.PNG)

3. Fai doppio clic sulla classe ARSessionConfig per aprirla. Un asset di dati ARSessionConfig contiene una serie di utili impostazioni di realtà aumentata (AR), tra cui il mapping spaziale e l'occlusione. Per altri dettagli su ARSessionConfig, consulta la documentazione relativa a Unreal Engine in [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html). Per l'app di scacchi non è necessario modificare le impostazioni, quindi premi **Save** (Salva) e torna alla finestra principale. 

![ARSessionConfig](images/unreal-uxt/3-arsessionconfig.PNG)

4. Sulla barra degli strumenti sopra il viewport fai clic su **Blueprints > Open Level Blueprint** (Progetti > Progetto Level aperto). Level è un progetto speciale che svolge la funzione di grafico di evento globale e prende come riferimento il livello. Verrà ora avviata una sessione di realtà aumentata, in modo che la configurazione di questa sessione venga applicata all'inizio del livello.  

5. Trascina fuori e rilascia il nodo di esecuzione **Event BeginPlay** (Evento BeginPlay). Cerca il nodo **Start AR Session** (Avvia sessione AR). Fai clic su **Session Config** (Configurazione sessione) e seleziona l'asset **ARSessionConfig** appena creato. Seleziona **Compile** (Compila) e quindi **Save** (Salva). Torna alla finestra principale.

![Start AR Session (Avvia sessione AR)](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a>Creare un pedone

1.  Nella cartella dei contenuti crea un nuovo progetto basato su **DefaultPawn**. In Unreal, un pedone rappresenta l'utente del gioco o, in questo caso, l'esperienza HoloLens 2. Rinomina il nuovo pedone "MRPawn" e fai doppio clic su MRPawn per aprirlo. 

![Creare un nuovo pedone basato su DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

2.  Per impostazione predefinita, il pedone include un componente mesh e un componente di collisione, poiché nella maggior parte dei progetti Unreal, i pedoni controllati dall'utente sono oggetti solidi che si scontrano con altri componenti. In questa situazione, l'utente corrisponde al pedone e si vuole quindi passare attraverso gli ologrammi senza generare collisioni. Nel pannello dei componenti seleziona **CollisionComponent**. Nel pannello dei dettagli scorri verso il basso fino alla sezione Collision (Collisione) e fai clic sull'elenco a discesa accanto a Collision Presets (Set di impostazioni per la collisione). Modifica il valore da Pawn (Pedone) a **NoCollision**. Esegui la stessa operazione per **MeshComponent**. Fai clic su **Compile** (Compila) e quindi su **Save** (Salva) per salvare il progetto. Torna alla finestra principale. 

![Modifica dei set di impostazioni di collisione del pedone](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a>Crea una modalità di gioco

1.  Nella cartella Content (Contenuto) del browser dei contenuti crea un nuovo progetto il cui elemento padre è **Game Mode Base** (Base modalità gioco). Denominalo MRGameMode e fai doppio clic per aprirlo. In Unreal, la modalità di gioco determina una serie di impostazioni relative al gioco o all'esperienza, incluso il pedone predefinito da usare. 

![MRGameMode nel browser dei contenuti](images/unreal-uxt/3-gamemode.PNG)

2.  Nel pannello dei dettagli individua la sezione Classes (Classi). Modifica il parametro Default Pawn Class (Classe pedone predefinito) da DefaultPawn a **MRPawn**. Seleziona **Compile** (Compila) e quindi **Save** (Salva). Torna alla finestra principale. 

![Impostazione della classe di pedone predefinita](images/unreal-uxt/3-setpawn.PNG)

3.  L'ultimo passaggio di configurazione del progetto prevede di indicare a Unreal che l'impostazione predefinita è MRGameMode. Passa a **Edit > Projects Settings > Maps & modes** (Modifica > Impostazioni progetti > Mappe e modalità) nella sezione Projects (Progetti). Nella sezione Default Modes (Modalità predefinite) fai clic sull'elenco a discesa e scegli **MRGameMode**. Nella sezione Default Maps (Mappe predefinite) sottostante, modifica sia **EditorStartupMap** sia **GameDefaultMap** sostituendoli con **Main** (Principale). In questo modo, quando si chiude e si riapre l'editor, per impostazione predefinita viene selezionata la mappa principale. Analogamente, quando si riproduce il gioco, la mappa principale è il livello avviato. 

![Project Settings - Maps & Modes (Impostazioni progetto - Mappe e modalità)](images/unreal-uxt/3-mapsandmodes.PNG)

[Sezione successiva: 4. Rendere la scena interattiva](unreal-uxt-ch4.md)