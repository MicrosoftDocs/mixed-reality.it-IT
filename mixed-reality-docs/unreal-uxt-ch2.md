---
title: 2. Inizializzazione del progetto e prima applicazione
description: Parte 2 di un'esercitazione per la creazione di una semplice app di scacchi con Unreal Engine 4 e il plug-in UX Tools di Mixed Reality Toolkit
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, esercitazione, guida introduttiva, mrtk, uxt, UX Tools, documentazione
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851575"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inizializzazione del progetto e prima applicazione

Questa sezione è un'introduzione alla creazione di una nuova applicazione Unreal per HoloLens 2. 

## <a name="objectives"></a>Obiettivi

* Configurare Unreal per lo sviluppo di HoloLens
* Importare gli asset e configurare la scena

## <a name="create-a-new-unreal-project"></a>Creare un nuovo progetto Unreal

1. Avvia Unreal Engine

2. In **New Project Categories** (Categorie nuovo progetto) seleziona **Games** (Giochi) e fai clic su Next (Avanti). Seleziona un modello **vuoto** e fai clic su Next (Avanti). 

![Selezionare il modello vuoto](images/unreal-uxt/2-template.PNG)

3. In Project Settings (Impostazioni progetto) scegli **C++, Scalable 3D or 2D, Mobile/Tablet** (C++, 3D o 2D scalabile, Cellulare/Tablet) e **No Starter Content** (Nessun contenuto iniziale). Seleziona un percorso per il progetto da salvare e fai clic su **Create Project** (Crea progetto). I file C++ verranno visualizzati in un progetto di Visual Studio e nell'editor di Unreal. 

![Impostazioni iniziali del progetto](images/unreal-uxt/2-project-settings.PNG)

4. Nell'angolo superiore sinistro passa a **Edit > Plugins** (Modifica > Plug-in). In Augmented Reality (Realtà aumentata) seleziona la casella per abilitare il plug-in **HoloLens**. Scorri verso il basso fino alla sezione Virtual Reality (Realtà virtuale) e seleziona la casella per abilitare il plug-in **Microsoft Windows Mixed Reality**. Per lo sviluppo di HoloLens 2 sono necessari entrambi i plug-in. Riavvia l'editor. 

![Plug-in](images/unreal-uxt/2-plugins.PNG)

5. Nell'angolo superiore sinistro passa a **File > New Level** (File > Nuovo livello). Seleziona **Empty Level** (Livello vuoto). In questa fase, la scena predefinita nel riquadro di visualizzazione dovrebbe essere vuota.

6. Trascina e rilascia PlayerStart dal pannello Modes (Modalità) a sinistra, che si trova nella scheda Basic (Impostazioni generali). Nel pannello Details (Dettagli) a destra imposta la posizione su X = 0, Y = 0, Z = 0, in modo che l'utente inizi dal principio quando si avvia l'app.

![Riquadro di visualizzazione con PlayerStart](images/unreal-uxt/2-playerstart.PNG)

7. Trascina un **cubo** dalla scheda Basic (Impostazioni generali) del pannello Modes (Modalità) nel riquadro di visualizzazione. Nel pannello Details (Dettagli) imposta la posizione su X = 50, Y = 0, Z = 0, in modo da impostare il cubo a 50 cm dal giocatore all'inizio della partita. Poiché il cubo predefinito è abbastanza grande, imposta le dimensioni del cubo su (0,2, 0,2, 0,2). 

8. Non puoi visualizzare il cubo a meno che non aggiungi una luce alla scena. Passa alla scheda**Lights** (Luci) nel pannello Modes (Modalità) e trascina un oggetto **Directional Light** (Luce direzionale) nella scena, sopra PlayerStart.

![Riquadro di visualizzazione con aggiunta di luce](images/unreal-uxt/2-light.PNG)

9.  Premi il pulsante **Play** sulla barra degli strumenti per visualizzare il cubo nel riquadro di visualizzazione. Premi **ESC** per arrestare il livello. 

![Un cubo nel riquadro di visualizzazione](images/unreal-uxt/2-cube.PNG)

10. Salva il livello. Nell'angolo in alto a sinistra fai clic su **File > Save Current** (File > Salva corrente). Assegna il nome "Main" (Principale) al livello e fai clic su **Save** (Salva). 

## <a name="set-up-a-chess-scene"></a>Configurare la scena di una partita a scacchi

1. In Content Browser (Browser contenuto) fai clic sull'icona Add New (Aggiungi nuovo) per visualizzare il pannello delle origini. Fai quindi clic su **Add New > New Folder** (Aggiungi nuovo > Nuova cartella) e assegna alla cartella il nome "ChessAssets". Fai doppio clic su questa cartella per esplorarla. Questo è il punto in cui importeremo le risorse 3D per la partita a scacchi.

![Visualizzare o nascondere il pannello delle origini](images/unreal-uxt/2-showhidesources.PNG)

2. Scarica il file con estensione zip degli asset da [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z). Questo file contiene i modelli 3D per una scacchiera e una partita a scacchi. Decomprimi il file.

3. Nella parte superiore di Content Browser (Browser contenuto) fai clic su **Import** (Importa). Passa alla cartella appena decompressa e seleziona tutti gli elementi all'interno. Questa cartella contiene i file FBX, che sono le mesh oggetto 3D per la scacchiera e i pezzi, nonché i file TGA, che rappresentano le mappe delle texture da usare per creare i materiali per la scacchiera e i pezzi. Fare clic su **Apri**. 

4. Visualizzerai la finestra FBX Import Options (Opzioni di importazione FBX). Nella sezione **Material** (Materiale) modifica l'opzione **Material Import Method** (Metodo importazione materiale) in **Do Not Create Material** (Non creare materiale). Quindi fai clic su **Import all** (Importa tutto).

![Opzioni importazione FBX](images/unreal-uxt/2-nocreatemat.PNG)

5. Torna alla cartella del contenuto e crea una nuova cartella denominata **Blueprints** (Progetti). Qui verranno archiviati tutti i progetti, ovvero asset speciali che forniscono un'interfaccia basata su nodi per creare nuovi tipi di attori ed eventi a livello di script. 

6. Fai doppio clic sulla cartella **Blueprints** (Progetti) per esplorarla e quindi fai clic con il pulsante destro del mouse su Content Browser (Browser contenuto) e seleziona **Blueprint Class** (Classe progetto). Fai clic su **Actor** (Attore) e assegna al nuovo progetto il nome "Board" (Tavola). Fai doppio clic sul progetto Board (Tavola) per aprirlo. 

![Selezionare una classe padre per il progetto](images/unreal-uxt/2-bpparent.PNG)

![Nuovo progetto Board (Tavola)](images/unreal-uxt/2-bpboard.PNG)

7. Nell'editor del progetto passa al pannello Components (Componenti) e fai clic su **Add Component > Scene** (Aggiungi componente > Scena). Assegna il nome "Root" (Radice) alla scena appena creata e quindi seleziona e trascina Root (Radice) su DefaultSceneRoot. Questa operazione sostituisce la radice della scena predefinita ed elimina la sfera nel riquadro di visualizzazione. 

![Sostituzione della radice](images/unreal-uxt/2-root.PNG)

8. Fai di nuovo clic su **Add Component** (Aggiungi componente) e questa volta scegli **Static Mesh** (Mesh statica). Assegna il nome "SM_Board" (MS_Tavola) alla nuova mesh statica. 

![Aggiunta di una mesh statica](images/unreal-uxt/2-sm-board.PNG)

9. Nel pannello **Details** (Dettagli) individua la sezione **Static Mesh** (Mesh statica) e fai clic sull'elenco a discesa. Seleziona **ChessBoard** (Scacchiera). 

![Mesh Tavola nel riquadro di visualizzazione](images/unreal-uxt/2-sm-board-view.PNG)

10. Sempre nel pannello **Details** (Dettagli) individua la sezione **Material** (Materiale) e fai clic sull'elenco a discesa. In **Create New Asset** (Crea nuovo asset) seleziona **Material** (Materiale). Assegna a questo asset il nome **M_ChessBoard** (M_Scacchiera) e salvalo nella cartella **ChessAssets**. 

![Creare un nuovo materiale](images/unreal-uxt/2-newmat.PNG)

11. Fai doppio clic sul quadrato accanto all'elenco a discesa M_ChessBoard (M_Scacchiera) per aprire il materiale M_ChessBoard (M_Scacchiera) appena creato. Nell'editor dei materiali fai clic con il pulsante destro del mouse e cerca il nodo **Texture Sample** (Esempio di texture). Nel pannello **Details** (Dettagli) nella sezione **Material Expression Texture Base** (Espressione materiale - Base texture) fai clic sull'elenco a discesa e seleziona **ChessBoard_Albedo** (Scacchiera_Albedo). Infine, trascina il segnaposto di output **RGB** sul segnaposto Base Color (Colore di base) di **M_ChessBoard** (M_Scacchiera). 

![Impostare il colore di base](images/unreal-uxt/2-boardalbedomat.PNG)

12. Esegui la stessa operazione quattro volte, collegando l'esempio di texture **ChessBoard_AO** (Scacchiera_OA) al segnaposto **Ambient Occlusion** (Occlusione ambientale), l'esempio di texture **ChessBoard_Metal** (Scacchiera_Metallo) al segnaposto **Metallic** (Metallico), l'esempio di texture **ChessBoard_Normal** (Scacchiera_Normale) al segnaposto **Normal** (Normale) e l'esempio di texture **ChessBoard_Rough** (Scacchiera_Ruvido) al segnaposto **Roughness** (Ruvidezza). Fare clic su **Save**. 

![Associare le texture rimanenti](images/unreal-uxt/2-boardmat.PNG)

13. Torna al progetto **Board** (Tavola). Noterai che il materiale appena creato è stato applicato al progetto. Per assicurarti che la tavola sia di dimensioni e posizioni adeguate dopo averla posizionata nella scena, imposta le **dimensioni** della tavola su (0,05, 0,05, 0,05) e la **rotazione** su Z = 90. Nella barra degli strumenti in alto fai clic su **Compile** (Compila) e quindi **Save** (Salva). Torna alla finestra principale. 

![Scacchiera con materiale applicato](images/unreal-uxt/2-chessboard.PNG)

14. A questo punto, elimina il cubo e sostituiscilo con l'attore Board (Tavola) appena creato. In **World Outliner** (Delineatore mondo reale) fai clic con il pulsante destro del mouse su **Cube > Edit > Delete** (Cubo > Modifica > Elimina). Trascina la tavola dal browser del contenuto nel riquadro di visualizzazione. Imposta la posizione della tavola su X = 80, Y = 0, Z = -20. 

15. Fai clic sul pulsante **Play** per visualizzare la nuova tavola nel livello. Premi **ESC** per tornare all'editor. 

16. A questo punto, seguiamo la stessa procedura per creare un pezzo degli scacchi come abbiamo fatto con la tavola, questa volta selezionando la mesh e il materiale per questo elemento:

    a) Passa alla cartella Blueprints (Progetti) in Content Browser (Browser contenuto) e crea una nuova classe Blueprint (Progetto) di tipo Actor (Attore). Assegna a questo attore il nome "WhiteKing".

    b) Fai doppio clic su WhiteKing per aprirlo. Aggiungi un nuovo componente della scena denominato "Root" (Radice) e usalo per sostituire DefaultSceneRoot. 

    c) Aggiungi un nuovo componente Static Mesh (Mesh statica) denominato "SM_King" (MS_Re). Nel pannello Details (Dettagli) imposta **Static Mesh** (Mesh statica) su **Chess_King** (Schacchi_Re) e **Material** (Materiale) su un nuovo materiale denominato **M_ChessWhite** (M_ScacchiBianco). 

    d) Apri il nuovo materiale **M_ChessWhite** (M_ScacchiBianco) e associa le texture rilevanti agli input materiali corrispondenti. 

    ![Creare il materiale per il re degli scacchi](images/unreal-uxt/2-chesskingmat.PNG)

    e) Torna al progetto **WhiteKing**, imposta le **dimensioni** su (0,05, 0,05, 0,05) e la **rotazione** su Z = 90.

    f) Compila e salva il progetto e quindi torna alla finestra principale. 

17. Trascina WhiteKing nel riquadro di visualizzazione. In **World Outliner** (Delineatore mondo reale) trascina WhiteKing sulla tavola in modo che sia ora un elemento figlio della tavola. 

![Delineatore mondo reale](images/unreal-uxt/2-child.PNG)

18. Nel pannello **Details** (Dettagli) in **Transform** (Trasformazione) imposta **Location** (Posizione) di WhiteKing su X =-26, Y = 4, Z = 0

19. Fai clic su **Play** per visualizzare il livello. Premi **ESC** per uscire. 

[Sezione successiva: 3. Configurare il progetto per la realtà mista](unreal-uxt-ch3.md)